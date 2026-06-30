# Sensors & Actuators

In the exercise 3, students were asked to create a pneumatic system consisting of two air pumps, an air valve, and an inflatable pillow and integrating a sensor interaction according to our own design.

---

## Basic Setup

The Arduino Uno's digital pins run at 5V and support a maximum of 40mA. The two diaphragm air pumps along with the air air valve provided to us draw a much higher current load than supported. To safely connect these components to the microcontroller,  we first connected hree IRF520 MOSFET driver modules.

---

### Hardware Setup
* Arduino Uno is powered via laptop USB port.
* MOSFETs load side connects to the external lab power supply.
* Arduino Uno's GND and the external power supply's GND must be tied together to establish a shared ground reference across the circuit.

---

### Code to Test Actuators
To verify the actuators, I started with a simple, hardcoded timer loop to test inflation, hold, and deflation states.

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

---

### Observations
* **Insulation may cause issues:** During initial testing, the MOSFET status LEDs lit up correctly, but the pumps did not work. After troubleshooting the connections, we realized the tiny screw terminals were clamped down onto the plastic wire insulation instead of the bare copper core. Stripping the insulation a little and clamping the wires correctly fixed it.
* **Optional VCC:** The VCC pin on the MOSFET isn't necessarily needed for switching. Connecting the SIG line HIGH to 5V provides enough gate voltage to complete the circuit and light the status LED.

<div align="center">

| <img src="media/exercise-1-1.jpg">  | 
| :---: |

</div>

<video src= "https://github.com/user-attachments/assets/bfd1980d-d4f0-4c22-9d02-15f351451455" controls autoplay muted loop style="max-width: 100%;"> </video>

---

## Integrating PIR Motion Sensor for Interaction
In order to make the system interactive, we integrated an HC-SR501 Passive Infrared (PIR) motion sensor. The Arduino only reacts when the motion sensor detects a movement in the room and deflates when there is no detected movement.

---

### Code to Integrate Motion Sensor

We designed the system such that the Arduino only reacts when the motion sensor detects a movement in the room and deflates when there is no detected movement.

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

---

### Observations
* **Hardcoded delays no longer required:** In our initial implementation, we hardcoded delay(5000) or delay(3000) miliseconds, which was limited in functionality and froze the microcontroller during execution. By using a motion sensing method,(currentMotionState != lastMotionState), the loop runs independently and remains responsive to new inputs from the sensor.
* **Intentional 100ms delay:** At the end of the loop, we added a delay(100). Continuously reading a digital pin thousands of times in a second without a break may cause Serial Monitor to overflow and the processor to run at 100% capacity. A 100 milisecond pause is unnoticeable to a human interacting with the system, but it gives the processor a massive and power-saving break.

<video src= "https://github.com/user-attachments/assets/f174891c-22fe-42f2-a246-e06e9d0b989a" controls autoplay muted loop style="max-width: 100%;"> </video>

<video src= "https://github.com/user-attachments/assets/02c74f94-cea7-4d33-b036-2cc6e2099f1b" controls autoplay muted loop style="max-width: 100%;"> </video>

---

<br>

[← Back to Table of Contents](../README.md)
