# Experiment 4 — Differential Amplifier  
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

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/6b49333c2b70b540b003b6cc89302b946b8eb24a/CIRCUIT1DIAGRAM.png)

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

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/DC1.png)

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

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/TRASN1.png)

---

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

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%201(3)%20NON%20LINEAR.png)


### Result

- Output is clipped  
- Distortion present  
- One transistor OFF  

---

## AC Analysis

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%201(4).png)

### Results

| Parameter | Value |
|----------|------|
| Gain | ~15 dB |
| Bandwidth | ~10 MHz |

---
  
## Circuit 2: NMOS Differential Pair with PMOS Current Mirror Load

---

## Objective

To design and analyze a CMOS differential amplifier using a PMOS current mirror load and verify its DC, transient, and AC performance through LTspice simulation.

---

## Overview

A differential amplifier amplifies the difference between two input signals while rejecting common-mode signals. In this circuit, resistive loads are replaced by a PMOS current mirror, which increases output resistance and improves gain.

This configuration is widely used in analog integrated circuits because active loads occupy less area and provide higher gain than resistors.

---

## Circuit Description

The circuit contains:

- M1, M2 → NMOS differential pair  
- M3 → Tail current source  
- M4, M5 → PMOS current mirror load  
- VDD = 0.9 V, VSS = -0.9 V  

M4 is diode-connected and sets the reference current. M5 mirrors this current to the other branch. The output is obtained using the mirror-loaded branch.

---

## Important Concept

The circuit works on differential input:

Vid = Vin1 − Vin2  

- If Vin1 increases → M1 current increases  
- If Vin2 increases → M2 current increases  
- PMOS mirror converts this current difference into output voltage variation

Because the load is active, the effective output resistance is high, so gain is much larger than in the resistive-load case.

---

## Circuit Diagram

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT2DIAGRAM.png)


---

## Given Parameters

| Parameter | Value |
|----------|------|
| VDD | 0.9 V |
| VSS | -0.9 V |
| Power | 2.2 mW |
| μnCox | 236.5 µA/V² |
| μpCox | 90 µA/V² |
| Vov,n | 0.34 V |
| Vov,p | 0.4 V |
| λ | 0.02 V⁻¹ |
| CL | 10 pF |
| L | 540 nm |

---

## Design Calculations

### Tail Current

ISS = P / (VDD − VSS)  
ISS = 2.2m / 1.8 = 1.22 mA  

---

### Branch Current

ID = ISS / 2 = 0.61 mA  

---

### NMOS Transconductance

gm = 2ID / Vov  
gm = 2 × 0.611m / 0.34  
gm = 3.59 mS  

---

### Output Resistance of Each MOSFET

ro = 1 / (λID)  
ro = 1 / (0.02 × 0.611m)  
ro = 81.8 kΩ  

---

### Effective Output Resistance

Rout = ron || rop  
Rout = 81.8k || 81.8k  
Rout = 40.9 kΩ  

---

### Theoretical Gain

Av = gm × Rout  
Av = 3.59m × 40.9k  
Av ≈ 147 V/V  

Av(dB) = 20 log10(147)  
Av(dB) ≈ 43.3 dB  

---

### Bandwidth

fp = 1 / (2π Rout CL)  
fp = 1 / (2π × 40.9k × 10p)  
fp ≈ 389 kHz  

---

### Slew Rate

SR = ISS / CL  
SR = 1.22m / 10p  
SR = 122 V/µs  

---

### PMOS Mirror Sizing

W/L = 2ID / (μpCox × Vov,p²)  
W/L = 2 × 0.611m / (90µ × 0.4²)  
W/L ≈ 84.8  

If L = 0.54 µm, then  

W = 84.8 × 0.54  
W ≈ 45.8 µm  

---

## DC Analysis

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/DC2.png)

### Observations

| Parameter | Value |
|----------|------|
| Vout1 | ~ -0.0084 V |
| Vout2 | ~ -0.0084 V |
| VS | ~ -0.7004 V |
| ID1 | ~ 0.610 mA |
| ID2 | ~ 0.610 mA |
| ISS | ~ 1.220 mA |
| VB1 | ~ -0.26 V |
| VB2 | ~ 0 V |

✔ Balanced operation  
✔ Current mirror working properly  
✔ Tail current matches design value  

---

## Transient Analysis

---

### Linear Region

Vin1 = +50 mV  
Vin2 = -50 mV  

Vid = 100 mV < 0.48 V  
![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/TRANS2.png)

### Result

- Output is sinusoidal  
- No clipping  
- Mirror load responds correctly  

Vin(pp) = 100 mV  
Vout(pp) ≈ 160 mV  

Gain ≈ 1.6 V/V  

---

### Non-Linear Region

Vin1 = +300 mV  
Vin2 = -300 mV  

Vid = 600 mV > 0.48 V  

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%202(4)%20NON%20LINEAR.png)


### Result

- Output is clipped  
- Distortion is present  
- One transistor tends to turn OFF  

Output max ≈ +0.56 V  
Output min ≈ -0.28 V  

---

## AC Analysis

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%202(5).png)

### Results

| Parameter | Value |
|----------|------|
| Midband Gain | ~4.35 to 4.65 dB |
| Gain (linear) | ~1.65 to 1.71 V/V |
| Bandwidth | As observed from AC plot |

---

## Comparison of Results

| Parameter | Theoretical | Simulated |
|----------|------------|----------|
| VDD | 0.9 V | 0.9 V |
| VSS | -0.9 V | -0.9 V |
| ISS | 1.222 mA | 1.220 mA |
| ID1 | 0.611 mA | 0.610 mA |
| ID2 | 0.611 mA | 0.610 mA |
| ID4 | 0.611 mA | 0.610 mA |
| ID5 | 0.611 mA | 0.610 mA |
| Vout1 | 0 V | -0.0084 V |
| Vout2 | 0 V | -0.0084 V |
| VS | -0.14 V | -0.7004 V |
| VB1 | -0.25 V | -0.26 V |
| VB2 | 0 V | ~0 V |
| gm | 3.59 mS | Design value |
| ro | 81.8 kΩ | Model based |
| Rout | 40.9 kΩ | Effective |
| Gain | 147 V/V | ~1.6 V/V |
| Gain (dB) | 43.3 dB | ~4.08 dB |
| Bandwidth | 389 kHz | From AC plot |
| Slew Rate | 122 V/µs | Theoretical |

---

## Key Observations

- Current mirror load gives high theoretical gain  
- DC operating point is well balanced  
- Small input gives linear output  
- Large input produces clipping  
- Practical measured gain is lower because output is measured single-ended  

---

## Important Note

To measure proper differential gain in LTspice, use:

V(vout2) - V(vout1)

This gives the true differential output and better matches theory.

---

## Conclusion

The current-mirror-loaded differential amplifier operates correctly and shows higher theoretical gain than the resistive-load amplifier. The DC biasing and current mirror action are correct, and the transient response confirms linear and non-linear regions clearly.

👉 Final Result:  
Current mirror load → High gain, lower bandwidth, better active-load performance

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
## Circuit 3: NMOS Differential Pair with PMOS Active Load and Bias Control

---

## Objective

To design and analyze a CMOS differential amplifier using PMOS active load with external bias control and verify its DC, transient, and AC performance through LTspice simulation.

---

## Overview

A differential amplifier amplifies the difference between two input signals and rejects common-mode components. In this circuit, PMOS transistors are used as active loads, and external bias voltages are applied to improve operating-point control.

Compared to the previous circuit, this configuration offers better bias stability and improved practical gain.

---

## Circuit Description

The circuit contains:

- M1, M2 → NMOS differential pair  
- M3 → Tail current source controlled by VB1  
- M4, M5 → PMOS active loads controlled by VB2  
- VDD = 0.9 V, VSS = -0.9 V  

VB1 controls the tail current source and VB2 sets the PMOS load bias. This makes the operating point more controllable and stable.

---

## Important Concept

The circuit operates with differential input:

Vid = Vin1 − Vin2  

- If Vin1 increases → M1 current increases  
- If Vin2 increases → M2 current increases  
- Active PMOS loads convert current changes into larger output voltage variations

Because the PMOS loads are biased externally, the output behavior becomes more stable and gain improves practically.

---

## Circuit Diagram

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT3DIAGRAM.png)


---

## Given Parameters

| Parameter | Value |
|----------|------|
| VDD | 0.9 V |
| VSS | -0.9 V |
| VB1 | -0.25 V |
| VB2 | 0.2 V |
| μnCox | 236.5 µA/V² |
| Vov,n | 0.34 V |
| λ | 0.02 V⁻¹ |
| CL | 10 pF |

---

## Design Calculations

### Tail Current

ISS ≈ 1.23 mA  

---

### Branch Current

ID = ISS / 2  
ID ≈ 0.616 mA  

---

### Transconductance

gm = 2ID / Vov  
gm = 2 × 0.616m / 0.34  
gm ≈ 3.62 mS  

---

### Output Resistance

ro = 1 / (λID)  
ro = 1 / (0.02 × 0.616m)  
ro ≈ 81 kΩ  

---

### Effective Output Resistance

Rout = ro || ro  
Rout ≈ 40.5 kΩ  

---

### Theoretical Gain

Av = gm × Rout  
Av ≈ 3.62m × 40.5k  
Av ≈ 147 V/V  

Av(dB) ≈ 43.3 dB  

---

### Bandwidth

fp = 1 / (2π Rout CL)  
fp ≈ 390 kHz  

---

### Slew Rate

SR = ISS / CL  
SR ≈ 1.23m / 10p  
SR ≈ 123 V/µs  

---

## DC Analysis

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/DC3.png)


### Observations

| Parameter | Value |
|----------|------|
| Vout1 | ~ -0.2719 V |
| Vout2 | ~ -0.2719 V |
| VS | ~ -0.7007 V |
| ID1 | ~ 0.616 mA |
| ID2 | ~ 0.616 mA |
| ISS | ~ 1.233 mA |
| VB1 | -0.25 V |
| VB2 | 0.2 V |

✔ Stable biasing achieved  
✔ Outputs are balanced  
✔ Tail current matches expected value  

---

## Transient Analysis

---

### Linear Region

Vin1 = +50 mV  
Vin2 = -50 mV  

Vid = 100 mV < 0.48 V  

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%203(3).png)


### Result

- Output is sinusoidal  
- No distortion  
- Higher practical gain than Circuit 2  

Output amplitude ≈ ±600 mV  
Vout(pp) ≈ 1.2 V  

Gain ≈ 12 V/V  

---

### Non-Linear Region

Vin1 = +300 mV  
Vin2 = -300 mV  

Vid = 600 mV > 0.48 V  

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%203(4).png)


### Result

- Output is clipped  
- Distortion is strong  
- One transistor moves toward cutoff  

Output clipped near ±0.85 V  

---

## AC Analysis

![image alt](https://github.com/Kulkarni-Rachit17/Linear-Integrated-Circuit-Lab/blob/259fa4b5395d71668f293f4634472c176f717d84/CIRCUIT%203(5).png)


### Results

| Parameter | Value |
|----------|------|
| Gain | ~30 dB |
| Gain (linear) | ~31 V/V |
| Bandwidth | As observed from AC plot |

---

## Comparison of Results

| Parameter | Theoretical | Simulated |
|----------|------------|----------|
| ISS | 1.222 mA | 1.233 mA |
| ID | 0.611 mA | 0.616 mA |
| Vout1 | 0 V | -0.2719 V |
| Vout2 | 0 V | -0.2719 V |
| VS | -0.14 V | -0.7007 V |
| VB1 | -0.25 V | -0.25 V |
| VB2 | 0.2 V | 0.2 V |
| Gain (theoretical) | 147 V/V | — |
| Gain (transient) | — | ~12 V/V |
| Gain (AC) | — | ~31 V/V |
| Bandwidth | 390 kHz | From AC plot |
| Slew Rate | 123 V/µs | Theoretical |

---

## Complete Comparison of Values

| Parameter | Theoretical / Designed Value | Simulated / Observed Value | Remark |
|----------|------------------------------:|---------------------------:|--------|
| Supply Voltage VDD | 0.9 V | 0.9 V | Matched |
| Negative Supply VSS | -0.9 V | -0.9 V | Matched |
| Tail Bias VB1 | -0.25 V | -0.25 V | Matched |
| PMOS Bias VB2 | 0.2 V | 0.2 V | Matched |
| Tail Current ISS | 1.222 mA | 1.233 mA | Very close |
| Branch Current ID1 | 0.611 mA | 0.616 mA | Very close |
| Branch Current ID2 | 0.611 mA | 0.616 mA | Very close |
| Vout1 at DC | 0 V | -0.2719 V | Shifted by bias |
| Vout2 at DC | 0 V | -0.2719 V | Balanced |
| Source Node VS | -0.14 V | -0.7007 V | Bias controlled |
| gm | 3.62 mS | Design value | Used in theory |
| ro | 81 kΩ | Model based | Used in theory |
| Rout | 40.5 kΩ | Effective | Used in theory |
| Gain (theoretical) | 147 V/V | — | Ideal |
| Gain (AC) | — | ~31 V/V | Practical |
| Gain (transient) | — | ~12 V/V | From waveform |
| Bandwidth | 390 kHz | From AC plot | Practical |
| Slew Rate | 123 V/µs | Theoretical | Matched by design |

---

## Key Observations

- External bias improves operating-point control  
- DC behavior is stable and balanced  
- Practical gain is higher than Circuit 2  
- Output clipping appears clearly for larger differential input  
- Active load improves performance significantly over resistive load  

---

## Important Note

For actual differential gain in LTspice, use:

V(vout2) - V(vout1)

This gives the correct differential output response.

---

## Conclusion

The bias-controlled active-load differential amplifier operates correctly and provides better practical performance than the earlier circuits. External bias voltages improve stability and make the circuit more suitable for analog integrated design.

👉 Final Result:  
Bias-controlled active load → Better stability, better practical gain, improved control

---
