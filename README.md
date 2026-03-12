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
