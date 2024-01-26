[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/x_MqueB0)
# lab1-power

    * Name: Jessi Jha
    * Description of hardware: Laptop,  

## Part A: Voltage Regulator

### 1 - Calculate the voltage at Node1. Show your work completely using Kirchhoff’s Law to derive the final voltage divider equation

V_out = V_in * (R_2 / (R_1 + R_2)) <br />
V_out = 5 V * (100 Ohms / (100 Ohms + 100 Ohms)) <br />
V_out = 2.5 V

### 2 - What if R2 was 850 ohm? What would the voltage at Node1 be? Show your work

V_out = V_in * (R_2 / (R_1 + R_2)) <br />
V_out = 5 V * (850 Ohms / (100 Ohms + 850 Ohms)) <br />
V_out =  4.47 V

### 3 - Attach an image of the plot generated (“Export Plot Images” in the upper right hand corner of the plot). Is this expected behavior? Why or why not?

![Alt text](image.png)

### 4 - List three scenarios where a voltage divider would be useful

1. You could use a voltage divider for a (cheap but pretty bad) voltage regulator.
2. You could also make a variable voltage regulator with a variable resistor (perhaps a potoentiometer that varies with light) if you want V_out to vary.
3. You also provide varying voltages from the same voltage supply (by connecting different circuit elements to the appropraite node in between resistors)

### 5 - When does the MOSFET (“switch”) become active - when the pulse of the clock (CLK1) is high or low? Why?

Because we used a P-MOSFET, the transistor allows current to pass when there is 0V applied to the gate. Thus the "switch" becomes active when 

### 6 - In order for Vout to be 3.3V, what duty cycle should be selected for the clock (CLK1)? What about for 2V? Do the values make sense? Why or why not?

Lorem ipsum

### 7 - Zoom into 2.8V to 5.0V. Explain the behavior you see - namely, why is there a spike at around 100us and why is the steady state output not a straight horizontal line? Attach an image of the generated plot

Lorem ipsum

### 8 - Explain the relationship between these three currents. (Hint: KCL) Is this expected? Why or why not? Attach an image of the generated plot

Lorem ipsum

### 9 - Attach an image of the generated plot

![Alt text](image-3.png) <br/>

![Alt text](image-4.png)

### 10 - Explain the relationship between these three currents. (Hint: KCL) Is this expected? Why or why not?

Lorem ipsum

## Part B: Arduino Power Management

### 11 - Manipulate the Barrel Jack voltage and USB voltage sources and fill out the following table. In the Power Source column, fill out whether the USB is used as a voltage source or the Barrel Jack

| **Jack**  | **USB**  | **Power Source?**  | **NODE1**  | **NODE2**  | **NODE3**  |
|---------- |--------- |------------------- |----------- |----------- |----------- |
| 0V        | 5V       |                    |            |            |            |
| 10V       | 0V       |                    |            |            |            |
| 10V       | 5V       |                    |            |            |            |
| 5V        | 5V       |                    |            |            |            |

### 12 - Is it possible to connect the barrel jack voltage directly to the non-inverting input of the op amp and still get the desired output? If not, what changes would need to be made to the circuit?

Lorem ipsum

### 13 - Why do you think that 3.3V is used as the reference voltage for the op-amp in this circuit and why is the voltage divider needed?

Lorem ipsum

## Part C: Boost Converter Implementation

### 14 - For a 10V input what is the output?

The output is about 20.77 V.

### 15 - Keeping the input voltage the same while changing the PWM to 20%, 35% and 50%. Measure the output voltage for each PWM. What is the relationship between input voltage, PWM and output voltage?

For PWM = 50%:
The output is about 20.77 V

For PWM = 35%:
The output is about 16.53 V

For PWM = 35%:
The output is about 12.70 V

It apears that the larger the duty cycle, the larger the output voltage is. This makes sense because was we decrease the duty cycle, the amount of time the transistor "switch" is on decreases. Thus, the inductor and capacitor have less time to charge, meaning Vout will be less.

### 16 - Keeping the input voltage, and PWM the same while changing the frequency to 20 KHz, 50 KHz and 100 KHz.  Record output voltage for each.  What conclusion can you draw from the readings?

For f = 100 kHz:
The output is about 18.39 V

For f = 50 kHz:
The output is about 18.64 V

For f = 20kHz:
The output is about  18.89 V

As the frequency decreases, I notice that Vout increases slighty. This is because the when we decrease the frequency of a wave, the wavelength (and thus, the time the wave is in the "on" position) is longer. This means the capacitor and inductor have more time to charge per cycle.

### 17 - Is the output different from the simulation output? If so, what’s the difference and why? How can you improve the performance of the physical circuit?

One way to improve the performance of the circuit is to reduce noise. You could do this by adding another capacitor into your cicruit. Essentially, capacitors take in a noisy voltage signal and then discharge a "smoother" (less noisy) signal. By adding multiple capacitors, you can obtain a signal that has less noise. 

## Part D: Linear Regulator

### 18 - Assuming an ideal linear regulator (i.e. the current that goes into the linear regulator is the same value for output current)  and knowing that the power equation is PWR = V * I, what would be the power efficiency of a 5.0V to 3.3V linear regulator? Why are linear regulators primarily used for low voltage drops from input to output?

PWR = (5 V - 3.3 V)*I_load = 2.7 V * I_load  <br/>

PWR_dissipated = (5 V - 3.3 V)*I_load + (5 V)*I_GND = 7.7 V * I_load <br/>

PWR_efficiency = 2.7 V * I_load / 7.7 V * I_load = 0.35

Linear regulators are primarily used for low voltage drops because the power efficiency decreases as you increase the voltage drop.

### 19 - Your task is to finish the table below. Plug in your ATmega Xplained board. Use the GND pin as reference, measure the voltages at pin A, B, C, D with a multimeter. Then, match the pins to their names on the schematic in Figure 14. Make sure that you understand what each pin does and write a short explanation for each pin

| **Fig 13 Label**  | **Voltage**  | **Pin Name in Schematic**  | **Explanation**                       |
|------------------ |------------- |--------------------------- |-------------------------------------- |
|         GND       |      0V      |             GND            | Connects to the ground on the board.  |
|          A        |     1.22V    |              EN            |   | <br/>       
|          B        |     3.31V    |           BYPASS           |   | <br/>
|          C        |     5.14V    |             VIN            |   | <br/>
|          D        |     5.14V    |             OUT            |   | <br/>

## Part E: Buck-Boost

### 20 - Attach an image of your schematic and the share link. (File > Link & Share)

Lorem ipsum

### 21 - For a given input voltage, attach a plot showing the schematic demonstrating buck (step down) capabilities

Lorem ipsum

### 22 - For the same input voltage as Question 21, attach a plot showing the schematic demonstrating boost (step up) capabilities

Lorem ipsum

## Github Repo Submission Resources

* [ESE5160 Example Repo Submission](https://github.com/ese5160/example-repository-submission)
* [Markdown Guide: Basic Syntax](https://www.markdownguide.org/basic-syntax/)
* [Adobe free video to gif converter](https://www.adobe.com/express/feature/video/convert/video-to-gif)
* [Curated list of example READMEs](https://github.com/matiassingers/awesome-readme)
* [VS Code](https://code.visualstudio.com/) is heavily recommended to develop code and handle Git commits
  * Code formatting and extension recommendation files come with this repository.
  * Ctrl+Shift+V will render the README.md (maybe not the images though)
