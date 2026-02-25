# Linear Integrated Circuits Laboratory

## Experiment: Design and Analysis of PMOS Common Source Amplifier  
**Technology:** TSMC 180 nm CMOS  
**Course:** Linear Integrated Circuits Laboratory (VTU – 4th Sem ECE)

**Name:** Kulkarni Rachit Ravinandan  
**USN:** 4NI24EC060  

---

## 1. Aim

To design and analyze a **PMOS Common Source (CS) amplifier** using **TSMC 180 nm CMOS technology** under given power and load constraints, and to study:

- DC operating point  
- Transient response  
- AC frequency response  
- Effect of load capacitance on gain and bandwidth  

---

## 2. Introduction to PMOS Transistor

A PMOS transistor is a MOSFET in which **holes are the majority charge carriers**. It turns ON when the **gate voltage is lower than the source voltage** by more than the threshold voltage.

For amplification, the PMOS transistor must operate in the **saturation region**, defined by:

- VSG > |VTP|  
- VSD ≥ (VSG − |VTP|)

Operating the device in saturation ensures linear amplification.

---

## 3. PMOS Common Source Amplifier

In a PMOS Common Source amplifier:
- Input signal is applied at the **gate**
- Output is taken from the **drain**
- Source is connected to **VDD**

A small variation in gate voltage controls the drain current, producing an amplified and inverted output signal with a **180° phase shift**.

---

## 4. Given Specifications

| Parameter | Value |
|--------|------|
| Supply Voltage (VDD) | 1.8 V |
| Power Constraint | ≤ 1 mW |
| Load Capacitance (CL) | 10 pF |
| Channel Length (L) | 180 nm |
| Technology | TSMC 180 nm |

---

## 5. Device Parameters

| Parameter | Value |
|--------|------|
| Threshold Voltage | |VTP| = 0.39 V |
| Oxide Thickness | tox = 4.1 nm |
| Oxide Capacitance | Cox = 8.418 × 10⁻³ F/m² |

---

## 6. Design Calculations

Maximum drain current from power constraint:

ID ≤ 1 mW / 1.8 V  
ID ≤ 555.5 µA  

Chosen drain current:

ID = **500 µA**

Power dissipation:

P = 1.8 × 500 µA = **0.9 mW**, which satisfies the constraint.

---

## 7. DC Analysis

DC analysis was performed to verify proper biasing of the PMOS transistor.

### DC Analysis Result

![DC Analysis](images/dc_analysis.jpeg)

Observations:
- Drain current ≈ 500 µA  
- Output voltage ≈ 0.9 V  
- PMOS operates in saturation region  

This confirms correct DC operating point for amplification.

---

## 8. Transient Analysis

Transient analysis was carried out using a small sinusoidal input signal applied at the gate.

### Transient Analysis – Input and Output Waveforms

![Transient Analysis 1](images/transient_1.jpeg)

### Transient Analysis – Combined Waveforms

![Transient Analysis 2](images/transient_2.jpeg)

Observations:
- Output amplitude is higher than input  
- Output signal is inverted (180° phase shift)  
- DC shift observed due to biasing  

Measured voltage gain:

Av ≈ **4.19 V/V**  
Av(dB) ≈ **12.44 dB**

---

## 9. AC Analysis

AC frequency response analysis was performed to study gain and bandwidth.

### AC Frequency Response

![AC Analysis](images/ac_analysis.jpeg)

Observations:
- −3 dB cutoff frequency ≈ **9.52 MHz**  
- Bandwidth reduces due to load capacitance  
- Gain–bandwidth trade-off verified  

Unity Gain Bandwidth:

UGB ≈ **39.9 MHz**

---

## 10. Effect of Capacitances

- MOSFET parasitic capacitances reduce high-frequency gain  
- External load capacitance introduces a dominant pole  
- Increase in load capacitance significantly reduces bandwidth  

---

## 11. Results Summary

| Parameter | Value |
|--------|------|
| Drain Current | 500 µA |
| Voltage Gain | 4.19 V/V |
| Gain (dB) | 12.44 dB |
| Bandwidth | 9.52 MHz |
| Unity Gain Bandwidth | 39.9 MHz |

---

## 12. Conclusion

A PMOS Common Source amplifier was successfully designed and analyzed using TSMC 180 nm CMOS technology under given constraints. DC, transient, and AC analyses confirmed correct operation in saturation region. The effect of load capacitance on bandwidth and gain–bandwidth trade-off was clearly observed, validating the design.

---

## 13. Inference

- PMOS operated in saturation region  
- Power constraint was satisfied  
- Practical gain reduced due to non-ideal effects  
- Load capacitance significantly reduced bandwidth  
- Gain–bandwidth trade-off verified successfully  
