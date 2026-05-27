# 🚀 Breathing Life into Hardware: Building an Interactive Pneumatic Installation

Welcome back to my hardware engineering series! After conquering I2C buses and state machines in Lab 2, Lab 3 plunges into the world of physical computing and soft robotics. The goal? Build an automated pneumatic system consisting of two air pumps, a solenoid valve, and an inflatable pillow, and bring it to life with sensor-driven interactions.

---

## 📝 Post 1: Isolating the Power (Enter the MOSFET)

The Arduino Uno's digital pins run at 5V and max out at around 40mA. The two ZR370-02PM diaphragm air pumps I used draw around 500mA each under load , and the FA0520E air valve draws ~400mA. To safely switch these heavy-duty inductive loads without frying the microcontroller, I wired up three IRF520 MOSFET driver modules.

### The Hardware Setup

The system isolates the low-power logic from the high-power physical loads.

* The Arduino logic processing is powered entirely via USB.


* The load side of the MOSFETs connects to an external lab power supply.


* Crucially, the Arduino's GND and the external power supply's GND must be tied together to establish a shared, unified ground reference across the entire circuit.



### The Open-Loop Code: A Basic Breath

To verify my actuators, I started with a simple, hardcoded timer loop to test inflation, hold, and deflation states.

```cpp
const int PUMP1_PIN = 3;      // (Deflation pump)
const int PUMP2_PIN = 4;      // (Inflation pump)
const int VALVE_PIN = 5;      // (Air Valve)

void setup() {
  pinMode(PUMP1_PIN, OUTPUT);
  pinMode(PUMP2_PIN, OUTPUT);
  pinMode(VALVE_PIN, OUTPUT);
}

void loop() {
  // --- INFLATION PHASE ---
  digitalWrite(VALVE_PIN, LOW);   // Close valve to seal the system
  digitalWrite(PUMP1_PIN, LOW);   // Turn OFF Pump 1 (Deflation pump)
  digitalWrite(PUMP2_PIN, HIGH);  // Turn ON Pump 2 (Inflation pump)
  delay(5000);                    // Inflate for 5 seconds

  // --- HOLD PHASE ---
  digitalWrite(PUMP1_PIN, LOW);   // Turn OFF both pumps
  digitalWrite(PUMP2_PIN, LOW);
  digitalWrite(VALVE_PIN, LOW);
  delay(3000);                    // Hold pressure for 3 seconds

  // --- DEFLATION PHASE ---
  digitalWrite(PUMP1_PIN, HIGH);  // Turn ON Pump 1 (Deflation pump)
  digitalWrite (PUMP2_PIN,LOW);   // Turn OFF Pump 2 (Inflation pump)
  digitalWrite(VALVE_PIN, HIGH);  // Open valve to vent air to atmosphere
  delay(5000);                    // Wait for deflation
}

```

### Engineering Insights

* **The "Insulation Trap":** During initial testing, my MOSFET status LEDs lit up correctly, but the pumps sat completely dead. After some frantic debugging, I realized the tiny screw terminals were clamped down onto the plastic wire insulation instead of the bare copper core. Stripping back the wire a few millimeters fixed it instantly.
* **VCC is Optional:** Interestingly, the VCC pin on the IRF520 control header isn't strictly needed for switching. Pulling the SIG line HIGH to 5V provides plenty of gate voltage to complete the circuit and light the onboard status LED simultaneously.

### The Circuit says "Cheese"

---

## 📝 Post 2: Making it Interactive with a PIR Sensor

A static timer is boring. To elevate the project, I brought in an HC-SR501 Passive Infrared (PIR) motion sensor. The goal: The cushion should inflate dynamically when it detects human presence and flatten out when the room is empty.

### The Closed-Loop Code: Edge-Triggered Automation**

Rather than spamming the MOSFETs with constant `digitalWrite()` commands, I implemented an edge-triggered state machine. The Arduino only acts at the exact moment a motion transition occurs.

```cpp
// Hardware Pin Definitions
#define PIR_PIN 2         // PIR Sensor Output Pin
#define PUMP1_PIN 3       // MOSFET 1 (Deflation Pump)
#define PUMP2_PIN 4       // MOSFET 2 (Inflation Pump)
#define VALVE_PIN 5       // MOSFET 3 (Air Valve)

int currentMotionState = LOW;
int lastMotionState = LOW;

void setup() {
  Serial.begin(9600);
  
  pinMode(PIR_PIN, INPUT);
  pinMode(PUMP1_PIN, OUTPUT);
  pinMode(PUMP2_PIN, OUTPUT);
  pinMode(VALVE_PIN, OUTPUT);

  // Initial Safety State: Turn off all pumps, open the valve
  digitalWrite(PUMP1_PIN, LOW);
  digitalWrite(PUMP2_PIN, LOW);
  digitalWrite(VALVE_PIN, HIGH); 

  Serial.println(F("PIR Warm-up Phase... Calibrating sensor..."));
  delay(20000); 
  Serial.println(F("System Active. Monitoring for motion..."));
}

void loop() {
  currentMotionState = digitalRead(PIR_PIN);

  if (currentMotionState != lastMotionState) {
    
    if (currentMotionState == HIGH) {
      // --- AUTOMATED INFLATION PHASE ---
      // Motion detected: Use Pump 2 to fill, isolate Pump 1
      Serial.println(F("» [MOTION DETECTED] Activating Pump 2 for Inflation..."));
      
      digitalWrite(VALVE_PIN, LOW);       // CLOSE the valve to seal the line
      digitalWrite(PUMP1_PIN, LOW);       // Ensure Deflation Pump 1 is OFF
      digitalWrite(PUMP2_PIN, HIGH);      // Turn ON Inflation Pump 2
      
    } else {
      // --- AUTOMATED DEFLATION PHASE ---
      // Motion stopped: Turn off Pump 2, open valve, run Pump 1 to pull air out
      Serial.println(F("» [AREA CLEAR] Activating Pump 1 for Assisted Deflation..."));
      
      digitalWrite(PUMP2_PIN, LOW);       // Turn OFF Inflation Pump 2
      digitalWrite(VALVE_PIN, HIGH);      // OPEN the valve to let air flow through
      digitalWrite(PUMP1_PIN, HIGH);      // Turn ON Deflation Pump 1 to clear lines
    }
    
    lastMotionState = currentMotionState;
  }

  delay(100); 
}

```

### Engineering Insights

* **Eliminating Blocking Delays:** My early experiments relied heavily on `delay()`, which literally freezes the microcontroller blind during execution. By using an edge-detection method (`currentMotionState != lastMotionState`), the loop runs freely and remains hyper-responsive to new sensor inputs without locking up.
* **The 100ms CPU Breather:** At the bottom of the loop, there is a tiny `delay(100)`. Reading a digital pin thousands of times a second without pause forces the processor to run at 100% capacity continuously. A tenth-of-a-second pause is unnoticeable to a human interacting with the cushion, but it gives the silicon a massive, power-saving break and prevents the Serial Monitor from overflowing.

### The Circuit says "Cheese"

---

## 🏁 Wrap-Up

Lab 3 demonstrated how low-level microcontroller logic translates into high-current physical action. What started as a messy tangle of silicone tubing and basic timers evolved into a fully closed-loop architectural prototype that dynamically breathes in response to human presence.

---

<br>

[← Back to Table of Contents](../README.md)