# Introduction

## Exercise 1: Electrical Circuits
### Task 1.1: LED Control Circuit
**Objective:** 
<br> Observe how resistance affects current flow and LED brightness.

**Observations:** 
* As the resistance _R<sub>1</sub>_ increased from 220 Ω to 4.7k Ω, the voltage drop _V<sub>1</sub>_ across the resistor increases while the voltage drop _V<sub>LED</sub>_ across the LED decreases. 
* As the resistance increases, the resistor absorbs more current and dims the intensity with which the LED glows.
* The voltages _V<sub>1</sub>_ and _V<sub>LED</sub>_ add up to roughly _V<sub>cc</sub>_ (=5 V).
* The LED heats up to a point of malfunction in the absence of a resistor in the circuit.

**Measurements:**
| R<sub>1</sub> [Ω]  | Measured V<sub>1</sub> [V] | Measured V<sub>LED</sub> [V] |
|-|-|-|
| 220   | 2.0  |2.8  |
| 1000  | 2.5  |2.49 |
| 4700  | 2.7  |2.31 |

### Task 1.2: Switchable LED Circuit
**Objective:** 
<br> Observe the behaviour of the LED with a switch. Also, what happens if the switch is connected in the opposite direction?

**Observations:** 
* The LED glows only when the switch is in ON position and does not glow when the switch is turned off.
* The switch is non-directional (unlike the LED). If the LED is reversed, it does not light up but the switch works as expected in both the directions.

### Task 1.3: Dimmable LED Circuit
**Objective:** 
Operate the potentiometer and observe the behaviour of the LED.

**Observations:** 
* The rotatation of potentiometer through various positions provides a smooth, continuous control over the intensity of light emited by LED.
* The data establishes a direct relationship between the LED voltage output _V<sub>LED</sub>_ and the potentiometer  voltage output _V<sub>2</sub>_. The potentiometer acts as a variable voltage divider.

* There is a threshold voltage (approximately 1.9V). Below this point, the LED does not emit any visible light.

**Measurements:**
| Position |   V<sub>LED</sub> [V] | V<sub>2</sub> [V] |
|-|-|-|
| Full brightness          | 3    |3    |
| Dimmed                   | 2.29 |2.29 |
| OFF<sub>Threshold</sub>  | 1.9  |1.97 |
| OFF<sub>Full</sub>       | 0.3  |0.4  |

## Exercise 2: Transistor Switch Circuit
### Task 2.1: Switchable LED Strip
**Objective:** Use an IRLZ44N NPN MOSFET to control a high-power 12V LED strip using a 5V logic signal.

**Mechanism:** 
<br> The MOSFET acts as an electronic switch which controls the Gate Voltage _V<sub>GS</sub>_. When the switch is closed, _V<sub>GS</sub>_ goes high, allowing current to flow from Drain to Source _V<sub>DS</sub>_, turning on the 12V LED strip. 


**Principle of Operation:**
<br>
1. The Gate Control _V<sub>GS</sub>_: The MOSFET has three terminals: **Gate (G)**, **Drain (D)**, and **Source (S)**. When the mechanical switch S<sub>1</sub> is open, the Gate is connected to the ground through a pull-down resistor (R<sub>pull</sub> = 10k Ω). This ensures the Gate voltage is 0V, keeping the transistor in the "OFF" state.
2. Switching States:
 - OFF State: When _V<sub>GS</sub>_ is below the threshold voltage, the internal channel between the Drain and Source is non-conductive (high resistance). No current flows through the 12V LED strip.
 - ON State: When S<sub>1</sub> is closed, 5V is applied to the Gate. This creates an electric field that opens a conductive channel between the Drain and Source. The resistance _V<sub>DS</sub>_ drops significantly, allowing current to flow from the 12V supply through the LED strip to the common ground.
3. PWM and Perceived Brightness: By using a PWM Signal Generator instead of a simple toggle switch, the Gate is turned ON and OFF thousands of times per second.
 - Duty Cycle: The ratio of "ON" time to "OFF" time determines the average power delivered to the LEDs. A higher duty cycle results in higher perceived brightness.
 - Frequency: At lower frequencies (e.g., 5 Hz), the eye perceives individual blinks. As the frequency increases beyond the 60 Hz threshold, the flickering becomes invisible to the human eye, resulting in a steady, dimmed light.


### Task 2.2: Dimmable LED Strip
**Objective:** 
<br> Use the PWM generator and observe how the Duty Cycle and Frequency affect the perceived light from the LED strip.

**Observations:** 
<br> Behavour of the LED strip for 5 different settings of Duty Cycle with Frequency _(f)_=90 Hz.
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

**Reflections:** 
* _Duty Cycle Variations (f=90 Hz):_ By keeping the frequency constant and varying the Duty Cycle (D), we control the "on-time" of the LED.
* _Frequency Varioation (D=0.5):_ We observed the transition from visible blinking to a steady glow, known as Flicker Fusion Threshold.


## Learning Outcomes

**Relationship Between Voltage and Resistance:** We learned that increasing resistance in a series circuit directly increases the voltage drop across the resistor (V<sub>1</sub>), which reduces the voltage available to the LED V<sub>LED</sub>, causing brightness to decrease.

**The Concept of Threshold Voltage:** We observed that LEDs have a specific threshold voltage (approximately 1.9V in this lab). If the supplied voltage falls below this point, the LED will turn off completely rather than continuing to dim linearly.

**Component Directionality:** We confirmed that LEDs are directional (polar) components that only light up when the anode and cathode are correctly oriented, whereas mechanical switches are non-directional and function regardless of orientation.

**Active Switching with MOSFETs:** We practiced using a low-voltage logic signal (5V) at the Gate of a MOSFET to switch a separate, higher-voltage load (12V). This demonstrated how transistors act as electronically controlled switches to protect sensitive logic circuits from high-power loads.

**Human Perception and PWM:** We discovered the Flicker Fusion Threshold. By increasing the PWM frequency to 60Hz or higher, the human eye can no longer perceive individual pulses, resulting in the appearance of a stable, dimmed light.

**Comparison of Dimming Methods:**
 - Resistive Dimming (Analog): Simple to implement but inefficient, as excess energy is dissipated as heat through the resistor. It is also limited by the LED's threshold voltage.
 - PWM Dimming (Digital): Highly efficient because the transistor is either fully ON or fully OFF, minimizing heat loss. It allows for much finer control of perceived brightness across a wide range (2% to 100% duty cycle) without affecting the voltage supplied to the load.
