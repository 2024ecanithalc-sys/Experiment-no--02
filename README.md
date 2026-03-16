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


### 6. Output Voltage

The output voltage is taken at the drain node:

Vout = VDD − ID * Rp (effective load)

Where Rp represents the effective resistance of the PMOS active load.

For symmetrical output swing:

Vout = VDD/2 + VRS

Vout = 1 + 0.2

Vout = 1.2 V

### 7. Overdrive Voltage
Assume:

VOV = 0.25 V
VTH = 0.36 V

VOV = VGS - VTH

VGS = VOV + VTH

VGS = 0.25 + 0.36

VGS = 0.61 V

### 8. Gate Voltage
VG = VGS + ID RS

Assume:

VRS = 0.2 V

VG = 0.61 + 0.2

VG = 0.81 V

### 9.Source Resistor
RS = VRS / ID

RS = 0.2 /200µ 

RS = 1k Ω

### 10. NMOS Width Calculation
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

### 11.PMOS Gate Bias
For PMOS: VOV = VSG − |VTP|
Assume |VTP| = 0.39 V

VSG = VOV + |VTP|

VSG = 0.25 + 0.39

VSG = 0.64 V

Since: VSG = VS − VG
VS = VDD = 2 V

VG = 2 − 0.64
VG = 1.36 V

### Over all conclusion :
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



## CONFIGURATION - 2
### Circuit :

The circuit represents a **common source amplifier with active load** implemented using CMOS transistors in **TSMC 0.18 µm technology**.

- **M1 (NMOS)** acts as the main amplifying transistor. The input signal `Vin` is applied to its gate through the voltage source **V4**, which is defined as `SINE(0.91 10m 1k)`.
- **M2 (PMOS)** works as an **active load transistor** and is connected to the supply voltage **V1 = 2 V**. Its gate is biased using **V3 = 2 V** to maintain proper operating conditions.
- **M3 (NMOS)** functions as a **current source / bias transistor**. The gate of M3 is biased with **V5 = 0.61 V** to set a constant current through the amplifier branch.
- The **output voltage (Vout)** is taken at the drain node of M1 and M2.
- **V2 = 1.36 V** is used to provide an additional biasing condition for proper transistor operation.
- The circuit includes different analyses:
  - `.op` for operating point analysis
  - `.dc V4 0 2` for DC sweep of the input
  - `.tran 5m` for transient response
  - `.ac dec 10 0.1 100G` for frequency response analysis

### Calculations :

Given Specifications:

VDD = 2 V
ID = 200 µA
VOV = 0.25 V
CL = 1 pF
Ln = Lp = 180 nm
P<= 1.5mW
εr = 3.9
ε0 = 8.854 × 10⁻¹² F/m
tox = 4.1 × 10⁻⁹ m
μn = 273.809 cm²/Vs
μp = 115.689 cm²/Vs

#### Power constraint:
Assuming ID =200µA which satisfy P<=1.5mW (P=V*I ; 2×200×10^−6 ; 400µW<=1.5mW)
#### Output Voltage Selection
For symmetrical output swing:

Vout = VDD/2 
Vout = 2/2
Vout = 1 V

#### For M1 (NMOS) transistor :

VOV = 0.25V and VTH = 0.36V
 VS1 = VD3
We know that, VDS3 >= VOV
Hence, VD3 = VS1 = 0.3 V
Vin = VG1 = VS1 + VGS1 = 0.3 + 0.61 = 0.91 V
* For M1 to be SATURATION, 
VGS1 >= VTH
0.61 V >= 0.36 V
also VDS1 >= VOV
VDS1 = VD1 - VS1 = Vout - VS1 = 1 - 0.3 = 0.7 V
Hence, 0.7 V >= 0.25 V
Both the conditions are satisfied, M1 is operating in saturation region.

#### For M3 (NMOS) transistor:

 VOV = 0.25V, VTH = 0.36V

 VGS3 = VOV + VTH 
      = 0.25 + 0.36 
 VGS3 = 0.61V
so VB2 = 0.61V
* For M3 to be SATURATION,
VGS3 >= VTH
0.61 V >= 0.36 V
also VDS3 >= VOV
VDS = 0.33 V from the simulation
Hence, 0.33 >= 0.25
Both the conditions are satisfied. M3 is operating in SATURATION region.

#### For M2 (PMOS) transistor:

VOV = 0.25V, VTH = 0.39V
VSG2 = VOV + |VTH| 
VSG2 = 0.25 + 0.39
VSG2 = 0.64 V
 VG2 = VS2 - VSG2
 VG2 = 2 - 0.64    
 VG2 = 1.36 V
 so VB1 = 1.36 V
* For M2 to be SATURATION,
VSG2 >= |VTH|
0.64 V >= 0.36 V
also VSD2 >= VOV
VSD2 = VDD - Vout  
VSD2 = 2 - 1
VSD2 = 1 V
Hence, 1 V >= 0.25 V

Both the conditions are satisfied.  M2 is operating in SATURATION region.

#### Drain current equation for M1 and M3 transistor:
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
W1 = 5 µm
similarly, W3 = 5 µm

#### Drain current equation for M2 transistor:
ID = (1/2) kn' (W/L) (VOV)^2

W2 = 11.82 µm 

By varying width:
* W1 = 25 µm → Id = 200 µA
* W2 = 34.605 µm → Id = 200 µA
* W3 = 15.79 µm → Id = 200 µA


### Simulated Results:

Vin(p-p) = Vin (max) − Vin (min)
         = 919.61 mV - 900.39 mV

Vin(p-p) =  19.22 mV

Vout(p-p) = Vout (max) − Vout (min)
          = 1.03 V - 967.25 mV

Vout(p-p) = 62.75 mV
Voltage Gain: 

Av = ΔVout / ΔVin
Av =  62.75/ 19.22
Av = 3.26 V/V

Gain in decibels:

Gain(dB) = 20 log10(Av) 
         = 20log(3.26)
  Av(dB) = 10.26 dB

### Theoritical Results:

gm1 = 2ID / VOV
gm1= (2 × 200 × 10⁻⁶) / 0.25
gm1 = 1.6 × 10⁻³ S
ro = 1 / (λ ID)
ro = 1 / (0.1 × 200 × 10⁻⁶)
ro1 = 50 kΩ

similarly, ro2 = 50 kΩ ,  ro3 = 50 kΩ

(ro1 || ro2) = 25 kΩ
Av = -gm1 (ro1 || ro2) / (1 + gm1 · ro3)
AV = - 0.5 V/V
Av(dB) = 20 log(Av)
       = 20 log(0.5)
       = 6.020 dB

Voltage Gain: The measured voltage gain of the amplifier is found to be
  
    Av = 10.87 - 3 = 7.87 dB
* Cutoff Frequency: The frequency at which the gain drops to the −3 dB level is observed as

  * Upper cutoff frequency:

    fH = 110.529 MHz

  * Lower cutoff frequency:

    fL ≈ 0

  * Bandwidth:

      BW = FH − FL

      BW = 110.529 MHz

#### Gain Bandwidth Product:

   GBP = Av × BW
   GBP = 3.49 × 110.529  MHz

   GBP = 385.71 MHz
   
   GBP = 0.385 GHz

#### Comparision of Results:

| Parameter | Theoretical | Simulated |
|-----------|-------------|-----------|
| Voltage Gain (A_v) | 0.5 V/V | 3.26 V/V |
| Gain (dB) | 6.020 dB | 10.26 dB |

### Result:

The Common Source (CS) amplifier that uses a resistive load along with source degeneration shows a lower voltage gain compared to a conventional CS amplifier. Simulation results indicate that although the peak-to-peak output amplitude is slightly reduced, the circuit produces a more linear output signal and maintains a more stable operating point even when MOSFET parameters vary.

### Validation

The simulation confirms the theoretical gain equation:

Av = -(gm × RD) / (1 + gm RS)

The simulated gain is close to the calculated value. The output waveform is inverted by 180° relative to the input, which is a characteristic property of a common-source amplifier. A small AC component at the source node indicates the presence of negative feedback in the circuit.

### Inference

The inclusion of M3 introduces negative feedback in the circuit, which enhances the stability of the amplifier operation. This feedback mechanism allows the amplifier to handle larger input signals with reduced distortion. Even though source degeneration decreases the voltage gain, it improves bias stability and linear behavior. Therefore, a balanced design must consider both feedback and output impedance to maintain adequate gain and bandwidth.


## CONFIGURATION - 3

## Circuit Description

The circuit represents a **common source (CS) amplifier with source degeneration and active load** implemented using CMOS transistors with **TSMC 0.18 µm technology**.

- **M1 (NMOS)** acts as the main amplifying transistor. The input signal **Vin** is applied to its gate through the voltage source **V4**, which is defined as `SINE(1.22 10m 1k)` for transient analysis and `AC 1` for AC analysis.
  
- **M2 (PMOS)** functions as the **active load** for the amplifier. It is connected to the supply voltage **V1 = 2 V**, and its gate is biased using **V2 = 2 V** to maintain proper operation.

- **M3 (NMOS)** acts as a **current source / bias transistor**. Its gate is biased using **V3 = 1.36 V**, which helps establish a constant current through the amplifier branch.

- The **output voltage (Vout)** is taken at the drain node of **M1** and **M2**.

- The circuit includes different analyses:
  - `.op` – Determines the DC operating point of the circuit.
  - `.dc V4 0 2` – Performs DC sweep analysis of the input voltage.
  - `.tran 5m` – Performs transient analysis to observe the time-domain response.
  - `.ac dec 10 10 100G` – Performs AC analysis to study the frequency response of the amplifier.
 
    ### Calculations :
Given Specifications:
VDD = 2 V
ID = 200 µA
VOV = 0.25 V
CL = 1 pF
Ln = Lp = 180 nm
P<= 1.5mW
εr = 3.9
ε0 = 8.854 × 10⁻¹² F/m
tox = 4.1 × 10⁻⁹ m
μn = 273.809 cm²/Vs
μp = 115.689 cm²/Vs

#### Power constraint:

Assuming ID =200µA which satisfy P<=1.5mW (P=V*I ; 2×200×10^−6 ; 400µW<=1.5mW)

#### Output Voltage Selection
For symmetrical output swing:
Vout = VDD/2
Vout = 2/2
Vout = 1 V

#### For M1 (NMOS) transistor :
VOV = 0.25V and VTH = 0.36V
VGS1 = VOV + VTH 
     = 0.25 + 0.36  
VGS1 = 0.61V
VS1 = 0.61 V
Vin =  VS1 + VGS1 
Vin = 0.61 + 0.61 
Vin = 1.22 V
so, VG1 = 1.22 V
* For M1 to be SATURATION,
VGS1 >= VTH
0.61 V >= 0.36 V
also VDS1 >= VOV

VDS1 = VD1 - VS1
     = Vout - VS1 
     = 1 - 0.61
     
VDS1 = 0.39 V
Hence, 0.39 V >= 0.25 V
Both the conditions are satisfied, M1 is operating in saturation region.

#### For M3 (NMOS) transistor:

VOV = 0.25V, VTH = 0.36V

VG3 = VS1
VGS3 = VOV + VTH
     = 0.25 + 0.36 
VGS3 = 0.61V
so, VG3 = 0.61V
For M3 to be SATURATION,
VGS3 >= VTH
0.61 V >= 0.36 V
also VDS3 >= VOV
VDS = 0.606 V from the simulation
Hence, 0.606 >= 0.25
Both the conditions are satisfied. M3 is operating in SATURATION region

#### For M2 (PMOS) transistor:

VOV = 0.25V, VTH = 0.39V
VSG2 = VOV + |VTH| = 0.25 + 0.39 VSG2 = 0.64 V
VG2 = VS2 - VSG2 = 2 - 0.64
VG2 = 1.36 V 
so VB1 = 1.36 V
For M2 to be SATURATION,
VSG2 >= |VTH|
0.64 V >= 0.36 V
also VSD2 >= VOV
VSD2 = VDD - Vout
VSD2 = 2 - 1 
VSD2 = 1 V
Hence, 1 V >= 0.25 V
Both the conditions are satisfied. M2 is operating in SATURATION region.

#### Drain current equation for M1 and M3 transistor:
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
W1 = 5 µm
similarly, W3 = 5 µm

#### Drain current equation for M2 transistor:
ID = (1/2) kn' (W/L) (VOV)^2
W2 = 11.82 µm
By varying width:
* W1 = 14.8  µm → Id = 200 µA
* W2 = 35 µm → Id = 200 µA
* W3 = 14.9  µm → Id = 200 µA

## Simulated Results:

Vin(p-p) = Vin (max) − Vin (min) = 1.22 V - 1.21 V
Vin(p-p) = 0.01 V
Vout(p-p) = Vout (max) − Vout (min) = 1.21 V - 0.869 V
Vout(p-p) = 0.341 V

Voltage Gain:
Av = ΔVout / ΔVin Av = 0.341/ 0.01 Av = 34.1 V/V
Gain in decibels:
Gain(dB) = 20 log10(Av) = 20log(34.1) 
Av(dB) = 30.65 dB

#### Theoritical Results:

gm1 = 2ID / VOV
gm1= (2 × 200 × 10⁻⁶) / 0.25
gm1 = 1.6 × 10⁻³ S
ro = 1 / (λ ID)
ro = 1 / (0.1 × 200 × 10⁻⁶)
ro1 = 50 kΩ
similarly, ro2 = 50 kΩ 
ro3 = 1/gm 
(ro1 || ro2) = 25 kΩ
Av = -gm1 (ro1 || ro2) / (1 + gm1 . 1/gm)
AV = -20 V/V
Av(dB) = 20 log(20) = 20 log(0.5) = 26.02 dB

* Voltage Gain: The measured voltage gain of the amplifier is found to be
   Av = 25.195 - 3 = 22.195 dB
* Cutoff Frequency: The frequency at which the gain drops to the −3 dB level is observed as
    * Upper cutoff frequency:
      fH = 345.989 MHz
    * Lower cutoff frequency:
      fL ≈ 0

* Bandwidth:

BW = FH − FL
BW =345.989 MHz

#### Gain Bandwidth Product:
GBP = Av × BW GBP = 18.182 × 345.989 MHz
GBP = 6363.49 MHz

### Comparision of Results:

| Parameter | Theoretical | Simulated |
|-----------|-------------|-----------|
| Voltage Gain (A_v) | 20 V/V |34.1  V/V |
| Gain (dB) |26.02 dB |30.65 dB |

## Result

The experimental results of the Common Source (CS) amplifier demonstrate the practical balance between voltage gain, circuit stability, and available voltage headroom. With a supply voltage of 1 V and a threshold voltage of 0.25 V, the transistors achieve an adequate overdrive voltage. This ensures that the MOSFETs operate in the saturation region during operation. As a result, the amplifier exhibits stable performance with good linearity, while minimizing distortion and preventing clipping of the output signal.

## 11. Inference

From the experimental observations, it can be concluded that the Common Source (CS) amplifier achieves effective voltage amplification while maintaining linearity and stability. The proper selection of supply voltage and transistor threshold ensures that the MOSFETs remain in saturation, preventing distortion or clipping. Overall, the amplifier design demonstrates a successful balance between gain, stability, and voltage headroom, confirming that the theoretical design principles translate well into practical performance.

The diode-connected load configuration reduces the overall voltage gain but improves the bandwidth and linearity of the amplifier. This approach is often used in integrated circuit design because large resistors are difficult to implement on a chip. By using an active load, the gain becomes dependent mainly on the transistor dimensions (W/L ratios) rather than precise resistance values, making the circuit performance more predictable.


## Comparison of Experiment 2 Configurations (A, B, C)

| Parameter | Experiment A | Experiment B | Experiment C |
|-----------|--------------|--------------|--------------|
| Source Element | Source Resistor (Rs) | NMOS Current Source | Diode-Connected NMOS |
| Active Load | PMOS | PMOS | PMOS |
| Drain Current (ID) | 200 µA | 200 µA | 200 µA |
| Power Dissipation | 1.5 mW | 1.5 mW | 1.5 mW |
| Theoretical Gain (V/V) | 15.38 | 0.5 | 20 |
| Simulated Gain (V/V) | 12.39 | 3.26 | 34.1 |
| Simulated Gain (dB) | 21.86 dB | 10.26 dB | 30.65 dB |
| Bandwidth | 191.095 MHz | 110.529 MHz | 345.989 MHz |









