# Experiment 2 — Differential Amplifier  
## Circuit 1: NMOS Differential Pair with Resistive Load

---

## Objective

To design and analyze a CMOS differential amplifier using resistive loads and verify its behavior through DC, transient, and AC simulations in LTspice.

---

## Overview

A differential amplifier amplifies the difference between two input signals while rejecting common-mode signals. It is widely used in analog circuits due to its high stability and noise immunity.

In this circuit, two NMOS transistors share a constant current source, and the output is taken across resistive loads.

---

## Circuit Description

The circuit contains:

- M1, M2 → NMOS differential pair  
- RD, RD2 → Load resistors  
- I1 → Tail current source  
- VDD = 0.9 V, VSS = -0.9 V  

When both inputs are equal, current splits equally. When a difference is applied, current shifts between the two branches, producing amplified outputs.

---

## Important Concept

The circuit works on differential input:

Vid = Vin1 − Vin2  

- If Vin1 increases → Vout1 decreases  
- If Vin2 increases → Vout2 decreases  

Thus outputs are equal in magnitude but opposite in phase.

---

## Circuit Diagram

<img src="YOUR_SCHEMATIC_IMAGE" width="800">

---

## Given Parameters

| Parameter | Value |
|----------|------|
| VDD | 0.9 V |
| VSS | -0.9 V |
| Power | 2.2 mW |
| μnCox | 236.5 µA/V² |
| Vov | 0.34 V |
| λ | 0.02 V⁻¹ |
| CL | 10 pF |

---

## Design Calculations

### Tail Current

ISS = P / (VDD − VSS)  
ISS = 2.2m / 1.8 = 1.22 mA  

---

### Branch Current

ID = ISS / 2 = 0.61 mA  

---

### Drain Resistance

RD = VDD / ID  
RD = 0.9 / 0.61m ≈ 1.47 kΩ  

---

### Transconductance

gm = 2ID / Vov  
gm = 3.59 mS  

---

### Gain

Av = gm × RD  
Av ≈ 5.28 V/V  

---

### Bandwidth

f = 1 / (2π RD CL)  
f ≈ 10.8 MHz  

---

### Slew Rate

SR = ISS / CL  
SR ≈ 122 V/µs  

---

## DC Analysis

<img src="YOUR_DC_IMAGE" width="800">

### Observations

| Parameter | Value |
|----------|------|
| Vout1 | ~0 V |
| Vout2 | ~0 V |
| ID | ~0.61 mA |
| ISS | ~1.22 mA |

✔ Balanced current  
✔ Stable operating point  

---

## Transient Analysis

---

### Linear Region

Vin1 = +50 mV  
Vin2 = -50 mV  

Vid = 100 mV < 0.48 V  

<img src="YOUR_LINEAR_WAVEFORM" width="800">

### Result

- Output is sinusoidal  
- No distortion  
- Phase difference = 180°  

Gain ≈ 7 V/V  

---

### Non-Linear Region

Vin1 = +300 mV  
Vin2 = -300 mV  

Vid = 600 mV > 0.48 V  

<img src="YOUR_NONLINEAR_WAVEFORM" width="800">

### Result

- Output is clipped  
- Distortion present  
- One transistor OFF  

---

## AC Analysis

<img src="YOUR_AC_PLOT" width="800">

### Results

| Parameter | Value |
|----------|------|
| Gain | ~15 dB |
| Bandwidth | ~10 MHz |

---

## Comparison of Results

| Parameter | Theoretical | Simulated |
|----------|------------|----------|
| ISS | 1.22 mA | 1.22 mA |
| ID | 0.61 mA | 0.61 mA |
| Gain | 5.28 V/V | ~7 V/V |
| Output Voltage | 0 V | ~0 V |

---

## Key Observations

- Gain is limited due to resistive load  
- Bandwidth is high due to low output resistance  
- Circuit is symmetric and stable  

---

## Conclusion

The resistive-load differential amplifier operates correctly and produces expected results. It provides good bandwidth but limited gain.

👉 Final Result:  
Resistive load → Low gain, High bandwidth

---
