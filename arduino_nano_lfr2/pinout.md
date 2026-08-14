Beep boop! As your line follower robot, I am fully ready to help you wire my hardware correctly.

Based on the final Deep Learning + PID Hybrid architecture we designed in your `main.ino` sketch, here is the complete and updated step-by-step pinout mapping.

### **1. The Brain (Arduino Nano) Pin Connections**

This is exactly where every data and control wire needs to connect to my ATmega328P microcontroller.

| Arduino Nano Pin | Connected Component | Purpose |
| --- | --- | --- |
| **5V** | Buck Converter 2 (Output) | Receives a perfectly tuned 5V to bypass my weaker onboard regulator.

 |
| **A0** | Multiplexer (muxSig) | Receives the multiplexed analog data from all 12 light sensors.

 |
| **A4** | 1.96-inch Display (SDA) | I2C Data line for the dashboard display.

 |
| **A5** | 1.96-inch Display (SCL) | I2C Clock line for the dashboard display.

 |
| **D2** | Multiplexer (muxS0) | Digital control pin 0 to switch between sensors.

 |
| **D3** | Multiplexer (muxS1) | Digital control pin 1 to switch between sensors.

 |
| **D4** | Multiplexer (muxS2) | Digital control pin 2 to switch between sensors.

 |
| **D5** | Multiplexer (muxS3) | Digital control pin 3 to switch between sensors.

 |
| **D6** | Button 1 (btnSelect) | "Select/Enter" menu button (must be wired to Ground with internal pull-up).

 |
| **D7** | Button 2 (btnScroll) | "Scroll/Next" menu button (must be wired to Ground with internal pull-up).

 |
| **D8** | TB6612FNG (AIN1) | Controls Left Motor direction.

 |
| **D9** | TB6612FNG (PWMA) | Controls Left Motor speed (PWM).

 |
| **D10** | TB6612FNG (PWMB) | Controls Right Motor speed (PWM).

 |
| **D11** | TB6612FNG (AIN2) | Controls Left Motor direction.

 |
| **D12** | TB6612FNG (BIN1) | Controls Right Motor direction.

 |
| **D13** | TB6612FNG (BIN2) | Controls Right Motor direction.

 |

---

### **2. The Actuation Subsystem (Motor Connections)**

This is how my TB6612FNG motor driver connects out to my physical N20 motors.

* 
**TB6612FNG VMOT:** Connects directly to the output of **Buck Converter 1** to receive optimal voltage directly from the battery.


* 
**TB6612FNG AO1 & AO2:** Connects directly to my **Left N20 Motor**.


* 
**TB6612FNG BO1 & BO2:** Connects directly to my **Right N20 Motor**.



---

### **3. The Power Subsystem (Regulators)**

To keep electrical noise from the motors out of my sensitive logic and sensor readings, wire the power exactly as follows:

* 
**Main Battery:** Splits to feed both Buck Converter 1 and Buck Converter 2.


* 
**Buck Converter 1:** Powers the motor driver (TB6612FNG VMOT) exclusively.


* 
**Buck Converter 2:** Connects to the 5V pin on the Arduino Nano. It also feeds into the input of the AMS1117.


* 
**AMS1117 Regulator:** Takes power from Buck Converter 2 and outputs ultra-clean power to my 1.96-inch I2C display, the 12-channel multiplexer, and the light sensors.
