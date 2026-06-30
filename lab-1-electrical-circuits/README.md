# Electrical Circuits
In the exercise 1, we are tasked with building and testing five different electrical circuits.

---

### Task 1.1: LED Control Circuit
Upon connecting the circuit components with different resistances, we made the following measurements and observations:

---

#### Measurements
| R<sub>1</sub> [$\Omega$]  | Measured V<sub>1</sub> [V] | Measured V<sub>LED</sub> [V] |
|-|-|-|
| 220   | 2.0  |2.8  |
| 1000  | 2.5  |2.49 |
| 4700  | 2.7  |2.31 |

---

#### Observations 
* As the resistance _R<sub>1</sub>_ increased from 220 $\Omega$ to 4.7k $\Omega$, the voltage drop _V<sub>1</sub>_ across the resistor increases while the voltage drop _V<sub>LED</sub>_ across the LED decreases. 
* As the resistance increases, the resistor absorbs more current and dims the intensity with which the LED glows.
* The voltages _V<sub>1</sub>_ and _V<sub>LED</sub>_ add up to roughly _V<sub>cc</sub>_ (=5 V).
* The LED heats up to a point of malfunction in the absence of a resistor in the circuit.

<div align="left">

---

| Setup | 
| :---: |
| <img src="media/task 1.1 a.jpg" width="300"> | 

</div>

---

### Task 1.2: Switchable LED Circuit
In this task we connected a switch to turn the LED `ON` or `OFF`.

---

### Observations
* The LED glows only when the switch is in `ON` position and does not glow when the switch is turned `OFF`.
* The switch is non-directional (unlike the LED). If the LED is reversed, it does not light up but the switch works as expected in both the directions.

---

<div align="left">

| Setup | 
| :---: |
| <img src="media/task 1.2 a.jpg" width="300"> | 

</div>

---

## Task 1.3: Dimmable LED Circuit
In this task, we attached a potentiometer to control the flow of current to the LED. W made the following measurements and observations:

---

### Measurements
| Position |   V<sub>LED</sub> [V] | V<sub>2</sub> [V] |
|-|-|-|
| Full brightness          | 3    |3    |
| Dimmed                   | 2.29 |2.29 |
| OFF<sub>Threshold</sub>  | 1.9  |1.97 |
| OFF<sub>Full</sub>       | 0.3  |0.4  |

---

### Observations 
* Rotating the potentiometer gives us a smooth, continuous control over the intensity of light emited by LED.
* The data establishes a direct relationship between the LED voltage output _V<sub>LED</sub>_ and the potentiometer voltage output _V<sub>2</sub>_. The potentiometer acts as a variable voltage divider.
* There is a threshold voltage (approximately 1.9V) below which the LED does not emit any visible light.

---

<div align="center">

| Setup | Circuit Connections (1) | Circuit Connections (2) |
| :---: | :---: |:---: |
| <img src="media/task 1.3 b.jpg" height="600"> | <img src="media/task 1.3 a.gif" height="600"> | <img src="media/task 1.3 c.gif" height="600"> |

</div>

---

### Task 2.1: Switchable LED Strip
In this task, we were requried to use an IRLZ44N NPN MOSFET to control a high-power 12V LED strip using a 5V logic signal.

---

### Mechanism
The MOSFET acts as an electronic switch which controls the Gate Voltage _V<sub>GS</sub>_. When the switch is closed, _V<sub>GS</sub>_ goes high, allowing current to flow from Drain to Source _V<sub>DS</sub>_, turning on the 12V LED strip. 

---

### Observations
1. **Gate Control _V<sub>GS</sub>_**: MOSFET has three terminals: **Gate (G)**, **Drain (D)**, and **Source (S)**. When the mechanical switch S<sub>1</sub> is open, the Gate is connected to the ground through a pull-down resistor (R<sub>pull</sub> = 10k $\Omega$). This ensures the Gate voltage is 0V, keeping the transistor in the `OFF` state.
2. **Switching States:**
 * **OFF State:** When _V<sub>GS</sub>_ is below the threshold voltage, the internal channel between the Drain and Source is non-conductive (high resistance). No current flows through the 12V LED strip.
 * **ON State:** When S<sub>1</sub> is closed, 5V is applied to the Gate. This creates an electric field that opens a conductive channel between the Drain and Source. The resistance _V<sub>DS</sub>_ drops significantly, allowing current to flow from the 12V supply through the LED strip to the common ground.
3. **PWM and Perceived Brightness:** By using a PWM Signal Generator instead of a simple toggle switch, the Gate is turned `ON` and `OFF` thousands of times per second.
 * **Duty Cycle:** A higher duty cycle results in higher LED brightness.
 * **Frequency:** At lower frequencies (e.g., 5 Hz), the eye perceives individual blinks. As the frequency increases beyond the 60 Hz threshold, the flickering becomes invisible to the eye, resulting in a steady, dimmed light.

---

<div align="center">

| Setup | Circuit in Action |
| :---: | :---: |
| <img src="media/task 2.1 a.jpg" height="500"> | <img src="media/task 2.1 b.gif" height="500"> |

</div>

---

## Task 2.2: Dimmable LED Strip
In this task, we used the PWM generator to observe how diferent values of Duty Cycle and Frequency affect the perceived light from the LED strip.

---

### Measurements 
Behavour of the LED strip for 5 different settings of Duty Cycle with Frequency _(f)_=90 Hz.
| Duty Cycle (%)|LED Strip  |
|-|-|
| D = 2%   | Very low brightness                                    |
| D = 15%  | Brighter, perceived a single blink during adjustment   |
| D = 40%  | Significantly brighter                                |
| D = 75%  | Brightness remains consistent                         |
| D = 100% | Maximum brightness; the strip is "always on"          |

Behavour of the LED strip for 4 different settings of Frequency _(f)_ with Duty Cycle _(D)_=0.5.
| Frequency (Hz)  | Behaviour of the LED Strip |
|-|-|
| 5     | Distinct blinks                      |
| 25    | Rapid flickering                     |
| 45    | Almost stable, very slight flicker   |
| 100   | Stable Light                         |

---

### Observations 
* **Duty Cycle Variations (f=90 Hz):** We can control the `ON-TIME` fo the LED by keeping the frequency constant and varying the Duty Cycle.
* **Frequency Variation (D=0.5):** We observed the transition from visible blinking to a steady glow, known as Flicker Fusion Threshold.

---

| Setup | D=15; f=90 | D=100; f=90 | Circuit |
| :---: | :---: | :---: | :---: |
| <img src="media/task 2.2 d.jpg" height="800"> | <img src="media/task 2.2 b.jpg" height="800"> | <img src="media/task 2.2 a.jpg" height="800"> | <img src="media/task 2.2 c.gif" height="800"> |

---

<br>

[← Back to Table of Contents](../README.md)
