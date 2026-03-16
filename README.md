## Experiment-no--02
Experiment no -02
## Design the amplifier configurations using tsmc is LTSPICE 


---
##  AIM :

To design a Common Source (CS) amplifier-configurations using NMOSFET in tsmc 180nm tech.lib in LTspice and to perform DC, Transient and AC analysis as per the given specifications.
1. Common source Amplifier with source degeneration
2. Cascode amplifier
3. Current mirror loaded common source amplifier

## Introduction :

Analog amplifier circuits are fundamental building blocks in electronic systems. They are used to increase the amplitude of weak electrical signals so that they can be processed by other stages in an electronic system. Amplifiers are widely used in communication systems, signal processing, and integrated circuit (IC) design.

In this project, different amplifier configurations are designed and simulated using **LTspice**, a SPICE-based circuit simulation software developed by Analog Devices. LTspice allows engineers and students to model MOSFET devices and evaluate important parameters such as voltage gain, frequency response, input impedance, output impedance, and power consumption.These circuits are designed using TSMC MOSFET models and analyzed through simulation. The results help in understanding the behavior of CMOS amplifiers and provide practical experience in analog IC design using simulation tools.


## MOSFET Amplifier Fundamentals:

MOSFET amplifiers are used to increase the amplitude of small input signals.  
For proper amplification, the MOSFET must operate in the **saturation region**, where it behaves like a controlled current source.

### Important Parameters

- **Drain Current (ID)**  
  ID = (1/2) μCox (W/L) (VGS − VTH)²

- **Overdrive Voltage (Vov)**  
  Vov = VGS − VTH

- **Transconductance (gm)**  
  gm = 2ID / Vov

- **Output Resistance (ro)**  
  ro = 1 / (λID)

- **Voltage Gain (Av)**  
  Av = −gm × Rout

---

## Amplifier Configurations Overview

### 1. Source Degenerated Common Source
- Uses a **source resistor** to introduce negative feedback.
- **Advantage:** Improves bias stability and linearity.
- **Limitation:** Reduces voltage gain.

### 2. Cascode Amplifier
- Combination of **Common Source + Common Gate** stages.
- **Advantage:** Provides high output resistance and higher gain.
- **Limitation:** More complex circuit design.

### 3. Active Load Common Source
- Uses a **current mirror or active transistor load** instead of a resistor.
- **Advantage:** Achieves higher gain.
- **Limitation:** Sensitive to biasing conditions.

## CONFIGURATION - 1

## CIRCUIT DIAGRAM :

![Image description] 
## CMOS Common Source Amplifier with Active Load


## Circuit description :

This circuit represents a **CMOS common-source amplifier** that uses an **NMOS transistor as the amplifying device** and a **PMOS transistor as an active load**. The design is commonly used in analog integrated circuits for **small-signal voltage amplification**.

## Components :
- **M1 (PMOS)** – Acts as an active load connected to the supply voltage.
- **M2 (NMOS)** – Functions as the main amplifying transistor.
- **V1 (2V)** – Power supply (VDD).
- **V3 (1.36V)** – Bias voltage applied to the PMOS gate.
- **V2** – Input signal source.
- **1kΩ Resistor** – Source degeneration resistor for the NMOS transistor.
- **Vout** – Output node taken at the drain connection of M1 and M2.

## Input Signal
The input voltage is defined as:

SINE(0.8 10m 1000)

Where:
- **0.8 V** = DC offset  
- **10 mV** = Amplitude of the input signal  
- **1000 Hz** = Frequency of the signal

## Circuit Operation
1. The input signal is applied to the **gate of the NMOS transistor (M2)**.
2. Variations in the input voltage change the **gate-to-source voltage (VGS)** of M2.
3. This variation controls the **drain current** flowing through M2.
4. The **PMOS transistor (M1)** acts as an active load, providing a nearly constant current and improving voltage gain.
5. The **output voltage (Vout)** is measured at the node between M1 and M2.

## Output Behavior
- When **Vin increases**, the NMOS conducts more current, causing **Vout to decrease**.
- When **Vin decreases**, the NMOS conducts less current, causing **Vout to increase**.

This results in an **inverted amplified output signal**.

## Source Degeneration
The **1kΩ resistor** connected to the source of M2 provides:
- Improved linearity
- Bias stability
- Reduced distortion

## THEORY :

### Circuit Components

The circuit consists of the following main components:

- **NMOS transistor** acting as the amplifying device  
- **PMOS transistor** acting as the active load  
- **Source degeneration resistor (Rs)**  
- **Bias voltage (VB)** for proper transistor operation  
- **Output node** taken from the drain terminal

---

### PMOS Active Load

Instead of using a passive resistor as the load, a **PMOS transistor** is used as an active load.  
The PMOS transistor provides a **higher output resistance** compared to a conventional resistor, which helps in increasing the **voltage gain** of the amplifier.

Using a PMOS transistor as a load also makes the circuit **more suitable for integrated circuit (IC) implementation**, since large resistors consume significant chip area.

---

### Source Degeneration

A **source resistor (Rs)** is connected to the source of the NMOS transistor.  
This configuration is known as **source degeneration**.

The resistor introduces **negative feedback** into the circuit. When the current through the NMOS increases, the voltage drop across Rs also increases, which reduces the effective gate-to-source voltage (Vgs). This helps control the current flowing through the transistor.

---

### Effects of Source Degeneration

The source degeneration resistor provides several advantages:

- Improves the **linearity** of the amplifier  
- Helps **stabilize the operating (bias) point**  
- Reduces signal **distortion**  
- Slightly **reduces the overall voltage gain**


## Design Calculations :

### 1. Drain Current (ID)

For the NMOS transistor operating in saturation region:

ID = (1/2) * μn * Cox * (W/L)n * (VGS − VTN)^2

Where:

- μn = Electron mobility
- Cox = Oxide capacitance per unit area
- (W/L)n = Aspect ratio of NMOS transistor
- VGS = Gate to source voltage
- VTN = Threshold voltage of NMOS

---

### 2. Transconductance (gm)

The transconductance of the NMOS transistor is given by:

gm = 2ID / (VGS − VTN)

### 4. Voltage Gain (Av)

For a common source amplifier with source degeneration:

Av = - gm (ron || rop) / (1 + gmRs)

Where:

- gm = Transconductance of NMOS
- Rs = Source degeneration resistor
- ron = Output resistance of NMOS
- rop = Output resistance of PMOS

The negative sign indicates **phase inversion**.

---

### 5. PMOS Active Load Current

For the PMOS transistor operating in saturation:

ID = (1/2) * μp * Cox * (W/L)p * (VSG − |VTP|)^2

Where:

- μp = Hole mobility
- (W/L)p = Aspect ratio of PMOS
- VSG = Source to gate voltage
- VTP = Threshold voltage of PMOS

The PMOS current must match the NMOS drain current for proper biasing.


### 8. Output Voltage

The output voltage is taken at the drain node:

Vout = VDD − ID * Rp (effective load)

Where Rp represents the effective resistance of the PMOS active load.


## Design Calculation:

### DC Analysis:

Given Specifications:

* VDD = 2 V

* ID = 200 µA

* VOV = 0.25 V

* CL = 1 pF

* Ln = Lp = 180 nm

* P<= 1.5mW

* εr = 3.9

* ε0 = 8.854 × 10⁻¹² F/m

* tox = 4.1 × 10⁻⁹ m

* μn = 273.809 cm²/Vs

* μp = 115.689 cm²/Vs

Power constraint:Assuming ID =200µA which satisfy P<=1.5mW (P=V*I ; 2×200×10^−6 ; 400µW<=1.5mW)

###  Output Voltage Selection
For symmetrical output swing:

Vout = VDD/2 + VRS

Vout = 1 + 0.2

Vout = 1.2 V

###  Overdrive Voltage
Assume:

VOV = 0.25 V
VTH = 0.36 V

VOV = VGS - VTH

VGS = VOV + VTH

VGS = 0.25 + 0.36

VGS = 0.61 V

###  Gate Voltage
VG = VGS + ID RS

Assume:

VRS = 0.2 V

VG = 0.61 + 0.2

VG = 0.81 V

### Source Resistor
RS = VRS / ID

RS = 0.2 /200µ 

RS = 1k Ω

### NMOS Width Calculation
Drain current equation:

ID = (1/2) kn' (W/L) (VOV)^2

Where

kn' = μn Cox

μn = 273.81 cm²/Vs

Cox = εox / tox

εox = 8.854 × 10⁻¹² × 3.9

tox = 4.1 × 10⁻⁹

kn' = 2.306 × 10⁻⁴

Now solving for W:

W = 5 µm

Thus

Wn = 5 µm

### PMOS Gate Bias
For PMOS: VOV = VSG − |VTP|
Assume |VTP| = 0.39 V

VSG = VOV + |VTP|

VSG = 0.25 + 0.39

VSG = 0.64 V

Since: VSG = VS − VG
VS = VDD = 2 V

VG = 2 − 0.64
VG = 1.36 V

### PMOS Width Calculation
Wp = (2 ID L) / (μp Cox (VOV)²)

Wp = 11.82 µm
By varying width:
* Wp = 2.9 µm → Id = 200 µA
* Wn =4.9  µm → Id = 200 µA

## Simulated Results:
Voltage Gain: Av = ΔVout / ΔVin Av = (1.379-1.136) / (819.64-800) = 12.39 V/V

Gain in decibels: Gain(dB) = 20 log10(Av) = 20 log10(12.39) = 21.86 dB

## Theoritical Results:
Small-signal Voltage Gain: Av = gm × RD = (1.6 × 10⁻³) × (5 × 10³) = 3.70

Gain in decibels: Gain(dB) = 20 log10(Av) = 20log(3.70) = 11.36 dB

gm = 2ID / VOV

gm = (2 × 200 × 10⁻⁶) / 0.25

gm = 1.6 × 10⁻³ S


ro = 1 / (λ ID)

ro = 1 / (0.1 × 200 × 10⁻⁶)

ro = 50 kΩ


(ro1 || ro2) = 25 kΩ


Av = - gm (ro1 || ro2) / (1 + gm RS) Av = - (1.6 × 10⁻³ × 25 × 10³) / (1 + 1.6 × 10⁻³ × 1 × 10³) Av = -40 / 2.6

Av = -15.38 V/V

Av(dB) = 20 log(15.38)

Av(dB) = 23.74 dB

The **simulated gain (21.86  dB)** is smaller than the **theoretical gain (23.74 dB)** because theoretical calculations usually assume ideal conditions with very large output resistance. In practical simulation, effects like **channel length modulation** reduce the output resistance of the transistors. Additionally, **parasitic capacitances** and accurate device model parameters lower the effective gain. The presence of the **source degeneration resistor (Rs)** also decreases the overall voltage gain of the amplifier.

 Voltage Gain: The measured voltage gain of the amplifier is found to be

  Av = 21.76-3 ≈ 18.76 dB

* Cutoff Frequency: The frequency at which the gain drops to the −3 dB level is observed as

Upper cutoff frequency:

  fH = 191.095 MHz

Lower cutoff frequency:

  fL ≈ 0

* Bandwidth:

  BW = FH − FL

  BW = 191.095 MHz

  ## Comparision of Results:

 | Parameter | Theoretical | Simulated |
|-----------|-------------|-----------|
| Voltage Gain (A_v) | 15.38 V/V | 12.39 V/V |
| Gain (dB) | 23.74 dB | 21.86 dB |

## Inference

- The difference between theoretical and simulated results occurs due to practical MOSFET non-idealities such as channel length modulation, mobility degradation, and parasitic capacitances.  
- These non-ideal effects introduce a dominant pole that limits the high-frequency response of the amplifier.  
- Source degeneration slightly reduces the gain but improves the stability and linearity of the circuit.  
- Overall, the amplifier performance remains close to the expected theoretical results.











































































