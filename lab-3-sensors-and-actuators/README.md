# Sensors & Actuators

In the exercise 3, students were asked to create a pneumatic system consisting of two air pumps, an air valve, and an inflatable pillow and integrating a sensor interaction according to their own design.

---

## Basic Setup

The Arduino Uno's digital pins run at 5V and support a maximum of 40mA. The two diaphragm air pumps along with the air air valve provided to us draw a much higher current load than supported. To safely connect these components to the microcontroller,  we first connected three IRF520 MOSFET driver modules.

---

### Hardware Setup
* Arduino Uno is powered via laptop USB port.
* MOSFETs load side connects to the external lab power supply.
* Arduino Uno's GND and the external power supply's GND must be tied together to establish a shared ground reference across the circuit.

---

### Code to Test Actuators
To verify the actuators, we started with a simple, hardcoded timer loop to test inflation, hold, and deflation states.

```cpp
.
.
.
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
.
.
.
```

---

### Observations
* **Insulation may cause issues:** During initial testing, the MOSFET status LEDs lit up correctly, but the pumps did not work. After troubleshooting the connections, we realized that the screw terminals were clamped down onto the plastic wire insulation instead of the bare copper core. Stripping the insulation a little and clamping the wires correctly fixed it.
* **Issues with the code:** During the  the initial attempt, inflation mechanism did not perform as expected due to issues with code logic and pin assignment. After updating the code logic and assigning the correct output pins, the system worked as expected.
* **Air tubes incorrectly connected:** Initially, we connected both the air tubes to the  DC motors in the inward airflow direction. Consequently, both the pumps where inflating the pillow in a round robin fashion, despite being assigned correct roles via code. Neither of the pumps was performing deflation and the pillow grew larger and larger in size. After spending some time inspecting the airflow direction, we fixed the air tube connections and the pneumatic system started functioning properly.
* **Connecting VCC is Optional:** MOSFET's VCC pin isn't necessarily needed for switching. Connecting the SIG line `HIGH` to 5V provides enough gate voltage to complete the circuit and light the status LED.

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

We designed the system such that the Arduino only reacts when the PIR motion sensor detects a movement in the room, and deflates when there is no movement detected.

```cpp
.
.
.
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
}
.
.
.
```

---

### Observations
* **PIR Motion Sensor in Action:** Movement around the system was continuously observed by the motion sensor. The microcontroller turned on the Inflation Pump (Pump 2) and closed the valve when motion was detected, causing the air pillow to expand. The system entered the deflation phase when no motion was detected, Deflation Pump (Pump 1) was turned on to expel the air from the system, Pump 2 was switched off, and the valve was opened.
* **Hardcoded delays no longer required:** In our initial implementation, we hardcoded delay(5000) or delay(3000) miliseconds, which was limited in functionality and suspended the microcontroller during execution. By using a motion sensing method,`(currentMotionState != lastMotionState)`, the loop runs independently and remains responsive to new inputs from the sensor.
* **Logging Detected Motion:** The motion detection logs generated by the system were sent to the Serial Monitor as output, which displayed messages such as “Motion Detected” and “Area Clear” suggesting that the sensor is working as we expected.

<video src= "https://github.com/user-attachments/assets/f174891c-22fe-42f2-a246-e06e9d0b989a" controls autoplay muted loop style="max-width: 100%;"> </video>

<video src= "https://github.com/user-attachments/assets/02c74f94-cea7-4d33-b036-2cc6e2099f1b" controls autoplay muted loop style="max-width: 100%;"> </video>

---

<br>

[← Back to Table of Contents](../README.md)
