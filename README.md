# Differential Amplifier Analysis (LTspice)

## Objective
To design and simulate three MOSFET-based differential amplifier configurations using LTspice and evaluate their performance through DC, transient, and AC analysis.

# Differential Amplifier – Overview
<img width="268" height="272" alt="image" src="https://github.com/user-attachments/assets/96e37499-ab6f-4dfc-8873-87f344d23e71" />


## Introduction
A differential amplifier is an analog circuit that amplifies the voltage difference between two input signals while suppressing any component that is common to both inputs. This property makes it highly useful in practical electronic systems where noise reduction is important.

It is commonly used in:
- Operational amplifiers (op-amps)
- Analog signal processing circuits
- Communication systems

---
## Working Principle
The circuit operates with two input voltages:
- V1 (input 1)
- V2 (input 2)
- 

The output is proportional to the difference between these inputs:
- When V1 = V2, the output is ideally zero
- When V1 ≠ V2, the difference is amplified at the output

---
## Output Relation
The output voltage can be expressed as:

Vout = Ad (V1 - V2)

Where:
- Ad is the differential gain
- V1 and V2 are the input voltages

---
## Key Parameters

### 1. Differential Gain (Ad)
Ad = Vout / (V1 - V2)

This represents the amplification factor for the difference between the input signals.

---
### 2. Common Mode Voltage (Vcm)
Vcm = (V1 + V2) / 2

It represents the average value of the two input signals.
---
### 3. Common Mode Gain (Ac)
Ac = Vout / Vcm

Ideally, this value should be very small to ensure proper operation.
---
### 4. Common Mode Rejection Ratio (CMRR)
CMRR = Ad / Ac

CMRR indicates how effectively the amplifier rejects common signals (noise). A higher value implies better performance.
---
## Characteristics
- High gain for differential signals  
- Very low gain for common-mode signals  
- High input impedance  
- Effective noise rejection

  A differential amplifier is designed to amplify the voltage difference between two input signals while suppressing any component that is common to both. This characteristic, known as common-mode rejection, is essential for minimizing noise in analog circuits.

In a basic MOS differential amplifier, two identical MOSFETs share a common source terminal, which is biased using a constant current source. The drain terminals are connected to load elements such as resistors or active loads.

The differential input is defined as:
vid = vin1 − vin2

The operation depends on this input difference:
- When vin1 is greater than vin2, transistor M1 conducts more current  
- When vin2 is greater than vin1, transistor M2 conducts more current  

For small values of vid:
- Both transistors remain in saturation  
- The circuit operates in a linear region  
- Voltage gain is given by: Av = gm × Rout  

Where:
- gm is the transconductance of the MOSFET  
- Rout is the effective output resistance  

The transconductance is expressed as:
gm = 2ID / Vov  

When the input difference becomes large (vid > 2Vov):
- One MOSFET turns OFF  
- The other carries the entire current  
- The amplifier enters a non-linear region  

The overall performance of the differential amplifier is influenced by the load type:
- Resistive load: provides moderate gain  
- Active load: increases output resistance and gain  
- Current mirror load: offers highest gain and improved performance  

Hence, selecting an appropriate load configuration plays a key role in determining the gain, bandwidth, and efficiency of the amplifier.

### Circuit Description
- Consists of two matched MOSFETs (M1 and M2)  
- Sources are connected together and biased using a constant current source  
- Drains are connected to load elements (resistors or active loads)  

---

### Input Relation
The differential input is defined as:
vid = vin1 − vin2  

---
### Working
- vin1 > vin2 → M1 conducts more current  
- vin2 > vin1 → M2 conducts more current  
- Current is steered between the two transistors based on input difference  

---

### Operation Regions

**For small input (vid is small):**
- Both MOSFETs operate in saturation  
- Circuit behaves linearly  
- Voltage gain:  
  Av = gm × Rout  

**For large input (vid > 2Vov):**
- One MOSFET turns OFF  
- Other MOSFET carries full current  
- Circuit becomes non-linear  

---
### Important Parameter
Transconductance:
gm = 2ID / Vov  
Where:
- ID = drain current  
- Vov = overdrive voltage  

---
### Effect of Load Type
- **Resistive Load:** Simple design, moderate gain  
- **Active Load:** Higher output resistance → higher gain  
- **Current Mirror Load:** Maximum gain and improved output performance


## Circuit 1: Differential Amplifier with Resistive Load
<img width="238" height="274" alt="image" src="https://github.com/user-attachments/assets/fecedb33-870b-480a-ac1b-b2711a96f2ee" />

### 1.1 Working Principle

A differential amplifier with a resistive load operates by converting a difference in input voltages into a proportional difference in output voltages. The circuit consists of two matched MOSFETs (M1 and M2) whose sources are connected together and biased using a constant current source. The drains are connected to resistors (RD1 and RD2), which act as loads.

When a differential input is applied:
vid = vin1 − vin2

- If vin1 > vin2 → M1 conducts more current → voltage drop across RD1 increases → output at OUT1 decreases  
- If vin2 > vin1 → M2 conducts more current → voltage drop across RD2 increases → output at OUT2 decreases

- <img width="494" height="417" alt="image" src="https://github.com/user-attachments/assets/e92515d1-09a8-449a-86f0-de816c268763" />
### Given Specifications

The differential amplifier is designed based on the following parameters:

## 1.2 Design Specifications

| Parameter                     | Symbol      | Value            |
|------------------------------|-------------|------------------|
| Technology                   | —           | TSMC 180 nm CMOS |
| Supply Voltage               | VDD         | +0.9 V           |
| Negative Supply              | VSS         | −0.9 V           |
| Maximum Power                | P           | ≤ 1.8 mW         |
| Channel Length (NMOS)        | Ln          | 480 nm           |
| Input Common-Mode Voltage    | Vin,CM      | 0 V              |
| Output Common-Mode Voltage   | Vo,CM       | 0 V              |
| Tail Node Voltage            | Vp          | −0.7 V           |
| Load Capacitance             | CL          | 10 pF            |
| Threshold Voltage            | VT          | ≈ 0.36 V         |


## Power and Current Constraints

The total power consumed by the differential amplifier is determined by the supply voltage and the tail current:

P = (VDD − VSS) × ISS  

### Total Supply Voltage

VDD − VSS = 0.9 − (−0.9) = 1.8 V  

### Power Constraint

Given maximum power:
P ≤ 1.8 mW = 1.8 × 10⁻³ W  

Substituting:
( VDD − VSS ) × ISS ≤ 1.8 × 10⁻³  

1.8 × ISS ≤ 1.8 × 10⁻³  

ISS ≤ 1 mA  

### Selected Tail Current

To fully utilize the available power budget:
ISS = 1 mA  

### Power Verification

P = (VDD − VSS) × ISS  
P = 1.8 × 1 mA = 1.8 mW  

Since:
1.8 mW ≤ 1.8 mW  

✔ Power constraint is satisfied  

### Current Distribution

For a balanced differential pair:
ID1 = ID2 = ISS / 2  

ID1 = ID2 = 0.5 mA  

### Summary

- Maximum allowable tail current: **1 mA**  
- Selected tail current: **1 mA**  
- Each transistor current: **0.5 mA**  
- Power consumption meets the design constraint  

This ensures optimal utilization of power while maintaining proper biasing of the differential amplifier.

## Drain Current Calculation

Under balanced input conditions:
vin1 = vin2  

The differential pair operates symmetrically, and the tail current divides equally between both transistors.

ID1 = ID2 = ISS / 2  

Substituting ISS = 1 mA:

ID1 = ID2 = 1 mA / 2  
ID1 = ID2 = 0.5 mA  

Thus, each MOSFET carries equal current when there is no differential input.

---

## Load Resistance Calculation

### Given
Output common-mode voltage:
VOCM = 0 V  

Hence:
Vout1 = Vout2 = 0 V  

### Output Voltage Relation

Vout = VDD − ID × RD  

Substituting values:

0 = 0.9 − ID × RD  

Rearranging:

ID × RD = 0.9  

### Solving for RD

RD = 0.9 / ID  

Substituting ID = 0.5 mA:

RD = 0.9 / (0.5 × 10⁻³)  

RD = 1.8 kΩ  

### Summary

- Drain current (each transistor): **0.5 mA**  
- Load resistance: **1.8 kΩ**  

These values ensure proper biasing and allow the output to be centered at 0 V under balanced conditions.

## 1.2.d Bias Point Analysis

### Given Conditions
- Input common-mode voltage: Vin,CM = 0 V  
- Tail node voltage: Vp = −0.7 V  

---

### Node Voltages

Since the inputs are equal:
VG1 = VG2 = 0 V  

Assuming the source node follows the tail node:
VS = Vp = −0.7 V  

---

### Gate-Source Voltage

VGS = VG − VS  
VGS = 0 − (−0.7) = 0.7 V  

---

### Overdrive Voltage

Given threshold voltage:
VT ≈ 0.36 V  

VOV = VGS − VT  
VOV = 0.7 − 0.36 = 0.34 V  

---

### Drain Voltage

From previous design:
Vout1 = Vout2 = 0 V  

So,
VD = 0 V  

---

### Drain-Source Voltage

VDS = VD − VS  
VDS = 0 − (−0.7) = 0.7 V  

---

### Region of Operation Check

Condition for saturation:
VDS > VOV  

0.7 > 0.34 ✔  

Hence, both MOSFETs operate in the saturation region.

---

### Final Bias Values

- VG = 0 V  
- VS = −0.7 V  
- VD = 0 V  
- VGS = 0.7 V  
- VDS = 0.7 V  

---

## 1.2.e Transistor Width Calculation

### Drain Current Equation (Saturation)

ID = (1/2) μnCox (W/L) (VOV)²  

---

### Rearranging for Width

W = (2 ID L) / [μnCox (VOV)²]  

---

### Substituting Values

- ID = 0.5 mA = 0.5 × 10⁻³ A  
- L = 480 nm = 480 × 10⁻⁹ m  
- μnCox = 236.5 μA/V² = 2.365 × 10⁻⁴  
- VOV = 0.34 V  

---

### Calculation

W = (2 × 0.5 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × 0.34²)  

W ≈ 17.57 μm  

---

### Practical Adjustment

The above value is based on ideal first-order assumptions. In real scenarios, effects such as:
- Channel length modulation  
- Mobility degradation  
- Process variations  

cause deviations from theoretical results.

To ensure the required condition:
VS = −0.7 V  

the width was fine-tuned using simulation until the desired bias point was achieved.

---

### Final Width

W ≈ 28.475 μm  

---

### Conclusion

The difference between calculated and final width highlights the impact of non-ideal effects in MOSFET operation. Simulation-based tuning ensures accurate biasing and reliable circuit performance.

## DC Analysis

### Objective
To determine the operating point (bias point) of the differential amplifier and verify that all transistors are operating in the saturation region.

<img width="733" height="482" alt="image" src="https://github.com/user-attachments/assets/8c021194-a39a-4377-b560-8631210294fa" />

## 1.2.f Input Common Mode Range (ICMR)

The input common-mode range defines the limits of input voltage within which all MOSFETs remain in saturation and the amplifier operates correctly.

---

### Minimum Input Voltage

To keep the NMOS transistors ON:
VGS ≥ VT  

Since:
VGS = VICM − VS  

Minimum input:
VICM(min) = VS + VT  

Substituting:
- VS = −0.7 V  
- VT = 0.36 V  

VICM(min) = −0.7 + 0.36 = **−0.34 V**

---

### Maximum Input Voltage

To maintain saturation:
VDS ≥ VOV  

Given:
VDS = VD − VS = 0 − (−0.7) = 0.7 V  

Maximum input is approximated by:
VICM(max) = VD + VT  

Substituting:
VICM(max) = 0 + 0.36 = **0.36 V**

---

### Final ICMR

| Parameter        | Value     |
|-----------------|-----------|
| VICM(min)        | −0.34 V   |
| VICM(max)        | 0.36 V    |

**ICMR Range:**  
−0.34 V ≤ VICM ≤ 0.36 V  

---

## 1.2.g Output Common Mode Range (OCMR)

The output common-mode range ensures that the transistors remain in saturation while allowing proper voltage swing at the output.

---

### Maximum Output Voltage

The upper limit is restricted by the supply voltage:
VOCM(max) ≈ VDD  

VOCM(max) = **0.9 V**

---

### Minimum Output Voltage

At the edge of saturation:
VDS = VOV  

So,
VD = VS + VOV  

Substituting:
- VS = −0.7 V  
- VOV = 0.34 V  

VOCM(min) = −0.7 + 0.34 = **−0.36 V**

---

### Final OCMR

| Parameter        | Value     |
|-----------------|-----------|
| VOCM(min)        | −0.36 V   |
| VOCM(max)        | 0.9 V     |

**OCMR Range:**  
−0.36 V ≤ VOCM ≤ 0.9 V  

---

## 1.2.h Differential Input Voltage Range (Linear Operation)

The differential amplifier behaves linearly only when both transistors share current and operate in saturation.

---

### Condition for Linear Region

|Vid| ≤ 2VOV  

---

### Calculation

Given:
VOV = 0.34 V  

|Vid| ≤ 2 × 0.34 = **0.68 V**

---

### Final Range

| Parameter | Value     |
|----------|-----------|
| Vid(min) | −0.68 V   |
| Vid(max) | 0.68 V    |

**Linear Operating Range:**  
−0.68 V ≤ Vid ≤ 0.68 V  

---

## Summary Table

| Parameter                     | Range                     |
|------------------------------|---------------------------|
| Input Common Mode (ICMR)     | −0.34 V to 0.36 V         |
| Output Common Mode (OCMR)    | −0.36 V to 0.9 V          |
| Differential Input (Linear)  | −0.68 V to 0.68 V         |

---

## Conclusion

The calculated ranges ensure that the differential amplifier operates in the saturation region with proper biasing. These limits define the safe operating region for accurate and linear signal amplification.

## Transient Analysis and Verification of Linear Behavior

The time-domain response of the differential amplifier is analyzed using transient simulation to evaluate its linear operating characteristics.

---
### Linearity Requirement

For the amplifier to function in the linear region, the applied differential input must remain within a specific limit:

|Vid| < 2VOV  

---
### Calculation

Given:
VOV = 0.34 V  

Therefore:
2VOV ≈ 1.414 × 0.34 ≈ 0.48 V  

---
### Interpretation

The differential input signal must be less than **0.48 V** to ensure that both transistors remain in saturation and the amplifier maintains linear operation.

<img width="882" height="188" alt="image" src="https://github.com/user-attachments/assets/25ba46bc-2622-4f2e-ba23-0d4b8c618c9c" />

## Case 1: Verification of Linear Operation

### Input Conditions

| Parameter                | Value                     |
|-------------------------|--------------------------|
| Input Signal 1          | SINE(0.1, 50m, 1k)       |
| Input Signal 2          | SINE(0.1, 50m, 1k, 180°) |
| Common-Mode Voltage     | 0.1 V                    |
| Differential Input (Vid)| 100 mV                   |

---

### Linearity Criterion

For a MOS differential amplifier to operate in the linear region:

|Vid| ≤ 2VOV  

Given:
2VOV = 0.68 V  

Comparison:
100 mV < 680 mV  

✔ Condition satisfied → **Linear operation confirmed**

---

### Output Characteristics

- **Waveform Quality:** Outputs are clean sinusoidal signals without any distortion  
- **Phase Relation:** The two outputs are equal in amplitude and exhibit a 180° phase difference  
- **Current Behavior:** Tail current is continuously shared between the two transistors  
- **Region of Operation:** Both MOSFETs remain in saturation throughout  

---

### Conclusion

The circuit operates in the linear region under the given input conditions. The output accurately represents the amplified difference of the inputs with stable gain and no signal distortion.

## Case 2: Non-Linear Mode of Operation

### Input Conditions (Modified)

| Parameter                | Value                      |
|-------------------------|----------------------------|
| Input Signal 1          | SINE(0.1, 400m, 1k)        |
| Input Signal 2          | SINE(0.1, 400m, 1k, 180°)  |
| Common-Mode Voltage     | 0.1 V                      |
| Differential Input (Vid)| 800 mV                     |

---
### Linearity Verification

For linear operation of a MOS differential pair:

|Vid| ≤ 2VOV  

Given:
2VOV ≈ 0.68 V  

Comparison:
800 mV > 680 mV  

✖ Condition violated → **Non-linear region**

---

<img width="887" height="191" alt="image" src="https://github.com/user-attachments/assets/69ab2e46-4701-471b-b985-89a9c6e08861" />

### Observations and Analysis

- **Waveform Distortion:** Output signals are highly distorted with noticeable clipping at the peaks  
- **Current Steering Effect:** The entire tail current shifts to one transistor (ID ≈ ISS), while the other approaches cutoff  
- **Loss of Symmetry:** Output waveforms are no longer symmetrical or purely sinusoidal  
- **Operating Behavior:** The circuit no longer behaves as a linear amplifier  

---
### Conclusion

At large differential input levels, the amplifier exceeds its linear operating limit. As a result, it behaves more like a switching circuit, with gain becoming non-linear and dependent on the input amplitude.Transient analysis shows that with a differential input of 100 mV, the amplifier functions in the linear region and produces a clean, undistorted output. When the input is increased to 800 mV, the circuit moves beyond its linear limits, clearly illustrating the onset of non-linear behavior in the TSMC 180 nm NMOS differential amplifier.

## Insight

The linear operating region of a differential amplifier is inherently limited and depends on the chosen overdrive voltage (VOV). The maximum differential input that preserves linearity can be expressed as:

|Vid|max = 2VOV  

If this limit is exceeded, the amplifier no longer maintains a linear relationship between input and output. Instead, it begins to act like a switching circuit, where the output is no longer proportional to the input. Hence, careful selection of VOV is essential to ensure the amplifier can accommodate the expected signal range without distortion.

---

## Gain Evaluation: Analytical vs Simulation

The performance of the differential amplifier is assessed by comparing the expected (theoretical) gain with the gain obtained from transient simulation.

---
### 1. Simulation-Based Gain Extraction

#### Input Signal Details

| Parameter        | Value        |
|-----------------|-------------|
| Signal Type      | Sinusoidal  |
| Frequency        | 1 kHz       |
| Amplitude        | 50 mV       |
| DC Offset        | 0.1 V       |
| Differential Input (Vid) | 100 mV |

---
#### Measured Values (From Transient Plot)

| Quantity                     | Calculation                          | Value       |
|-----------------------------|--------------------------------------|-------------|
| Input Peak-to-Peak Voltage  | 50 mV − (−50 mV)                     | 100 mV      |
| Output Peak-to-Peak Voltage | 287.165 mV − (−287.165 mV)           | 574.33 mV   |

---
#### Voltage Gain Calculation

Voltage gain is obtained using:

Av = Vout(pp) / Vin(pp)  

Av = 574.33 mV / 100 mV = **5.74**

---
#### Gain in Decibels

Av(dB) = 20 log10(Av)  

Av(dB) ≈ 20 log10(5.74) ≈ **15.18 dB**

---
### 2. Theoretical Gain

From small-signal analysis:

Ad ≈ gm × RD  

This value was previously estimated during the design stage.

---
### 3. Performance Comparison

| Parameter            | Theoretical | Simulated |
|---------------------|-------------|-----------|
| Gain (V/V)          | 4.5         | 5.74      |
| Gain (dB)           | 13.06 dB    | 15.18 dB  |

---
### 4. Interpretation

- The simulated gain is slightly higher than the theoretical value  
- This variation is due to non-ideal effects and more accurate device modeling in simulation  
- Overall, the results are reasonably close, validating the design approach  

---
### Conclusion

The comparison confirms that the designed differential amplifier achieves the expected gain performance, with simulation results closely matching theoretical predictions.

## WHY IS THE STIMULATED GAIN HIGHER?

The simulated gain (~5.74 V/V) is higher than the theoretical estimate (~4.5 V/V) due to practical device effects not captured in first-order calculations.

- **Channel Length Modulation:** λ varies with bias → alters output resistance (ro) and increases gain  
- **Advanced Device Modeling:** LTspice uses BSIM models accounting for velocity saturation, mobility degradation, and DIBL → more accurate gm  
- **Overdrive Variation:** Small shifts in VOV affect gm (gm ∝ 1/VOV) → impacts gain  
- **Non-ideal Output Resistance:** Interaction of transistor ro and tail current source modifies effective gain  
- **Width Optimization:** Increased W (≈ 28.475 μm vs theoretical 17.57 μm) boosts gm → higher gain  

---
### Conclusion
The deviation highlights the impact of non-ideal effects and validates the need for simulation-based refinement in analog design.

## AC Analysis: Frequency Response & Bandwidth Evaluation

AC analysis is carried out to study the frequency-dependent behavior of the differential amplifier, including gain, bandwidth, and high-frequency limitations.

<img width="860" height="407" alt="image" src="https://github.com/user-attachments/assets/1ddd10c4-424d-46ef-9574-6767760cb2fd" />


### 1. Simulation Configuration

| Parameter              | Setting                  |
|-----------------------|--------------------------|
| AC Sweep Command      | .ac dec 100 1 10G        |
| Input Excitation      | Vin1 = AC 1, Vin2 = AC -1|
| Output Measurement    | V(out1) − V(out2)        |

---
### 2. Key Results from Simulation

#### Midband Gain

| Scale        | Value        |
|--------------|-------------|
| Gain (dB)    | 15.6 dB      |
| Gain (Linear)| ≈ 6.02 V/V   |

✔ Matches closely with transient gain (~5.74 V/V), ensuring consistency  
---

#### Bandwidth Calculation

| Parameter                  | Value          |
|---------------------------|---------------|
| -3 dB Gain Level          | 12.6 dB        |
| Upper Cutoff (fH)         | 5.128 GHz      |
| Lower Cutoff (fL)         | ≈ 0 Hz(DC coupled)        |
| Bandwidth (BW)            | 5.128 GHz      |


#### Unity Gain Bandwidth

UGB ≈ Av × BW  

UGB ≈ 6.02 × 5.128 GHz ≈ **30.9 GHz**

### 3. Frequency Response (Bode Plot Insights)

| Parameter                          | Value       | Frequency Range        |
|-----------------------------------|------------|------------------------|
| Differential Gain (Adiff)          | 21.78 dB    | ~DC to 1 GHz           |
| Single-Ended Gain (Ase)            | 15.76 dB    | ~DC to 1 GHz           |
| -3 dB Cutoff Frequency (fH)        | 18.78 dB    | High-frequency limit   |
| Unity Gain Frequency (fT)          |0            | Gain = 0 dB            |
| Phase (Midband)                    | ~180°       | Low-frequency region   |

### 4. Performance Interpretation

- **Flat Gain Region:** Stable gain at low frequencies confirms proper biasing and absence of coupling losses  
- **High-Frequency Roll-off:** Gain drops at higher frequencies due to parasitic capacitances (Cgs, Cgd) and load capacitance (CL)  
- **High-Speed Capability:** GHz-level bandwidth indicates suitability for high-speed analog applications  
- **Gain-Bandwidth Trade-off:** High UGB (~30.9 GHz) reflects efficient design under given power constraints  

###  AC Performance Summary

| Metric                     | Value        |
|---------------------------|-------------|
| Midband Gain              | 15.6 dB      |
| Bandwidth (−3 dB)         | 5.128 GHz    |
| Unity Gain Bandwidth      | ≈ 30.9 GHz   |

### Conclusion

The AC analysis demonstrates that the designed differential amplifier achieves moderate gain with a very wide bandwidth. The results confirm stable operation and highlight the high-speed performance capability of the TSMC 180 nm MOSFET design.

## Frequency Response Analysis
### Gain Characteristics
The Bode plot shows that the differential gain (~21.78 dB) exceeds the single-ended gain (~15.76 dB) by nearly **6 dB**.  
This matches the expected behavior of differential circuits, where the output is effectively doubled:

20log₁₀(2) ≈ 6 dB  

### Bandwidth Behavior
- The gain remains **uniform across a wide frequency range** (from very low frequencies up to ~1 GHz)  
- This confirms **DC-coupled operation**, with no noticeable lower cutoff frequency  
- The gain starts to decrease beyond ~1 GHz due to the influence of **device parasitics (Cgs, Cgd)** and the load capacitance
  
### Phase Behavior
- The phase begins close to **180°**, indicating the inverting nature of the circuit  
- A smooth phase transition occurs near higher frequencies, reflecting **stable operation with good phase margin**

### Summary
The results indicate consistent gain, wide bandwidth, and stable phase response, demonstrating reliable high-frequency performance of the differential amplifier.



## 2.1 Operation of Differential Amplifier with PMOS Active Load

### Circuit Description
This configuration uses:
- Two matched NMOS transistors (M1, M2) forming the differential pair  
- An NMOS transistor (M5) acting as a constant current source  
- A PMOS current mirror (M3, M4) serving as the active load  

---
### Principle of Operation

The amplifier processes the difference between the two input signals:

vid = vin1 − vin2  

Based on the input difference:
- If vin1 > vin2 → M1 draws more current, M2 draws less  
- If vin2 > vin1 → M2 draws more current, M1 draws less  

The tail current (ISS), controlled by M5, is redistributed between M1 and M2 depending on this input difference.

---
### Role of Active Load

- M3 is diode-connected and establishes a reference current  
- M4 mirrors this current to the other branch  
- This arrangement provides **high output resistance**, resulting in **higher gain** compared to resistive loads  

---
### Output Formation

Variations in drain currents of M1 and M2 are converted into voltage changes at the output nodes (OUT1, OUT2), producing a differential output.

---
### Effect of Current Source (M5)

- M5 operates in saturation to supply a constant tail current  
- Its finite output resistance introduces slight source degeneration  
- This effect slightly reduces gain but improves stability  

---
### Operating Regions
**For small input signals:**
- All transistors remain in saturation  
- Current is shared smoothly  
- Output is linear and proportional to input  

**For large input signals:**
- One transistor turns OFF  
- The other carries most of the current  
- Output becomes non-linear  

---
### Key Advantage

The use of a PMOS current mirror as an active load significantly enhances the gain by increasing output resistance, making this configuration more efficient than a resistive load differential amplifier.

# 2.2 Design Calculations – Differential Amplifier with PMOS Active Load

<img width="460" height="325" alt="image" src="https://github.com/user-attachments/assets/5acc7e2e-0ecc-41b5-8012-af1684afd7f4" />


---
##  Given Specifications

| Parameter                  | Symbol     | Value            |
|---------------------------|------------|------------------|
| Technology                | —          | TSMC 180 nm      |
| Supply Voltage            | VDD        | +0.9 V           |
| Negative Supply           | VSS        | −0.9 V           |
| Power Constraint          | P          | ≤ 1.8 mW         |
| Channel Length            | L          | 480 nm           |
| Input CM Voltage          | Vin,CM     | 0 V              |
| Output CM Voltage         | Vo,CM      | 0 V              |
| Tail Node Voltage         | Vp         | −0.7 V           |
| Load Capacitance          | CL         | 10 pF            |
| Threshold Voltage         | VT         | ≈ 0.36 V         |

---

## Power Constraint

Total supply voltage:
VDD − VSS = 0.9 − (−0.9) = 1.8 V  

Power relation:
P = (VDD − VSS) × ISS  

1.8 × ISS ≤ 1.8 × 10⁻³  

ISS ≤ 1 mA  

✔ Choose:
ISS = 1 mA  

Power check:
P = 1.8 × 1 mA = 1.8 mW ✔  

---

##  Drain Current

For balanced inputs:
vin1 = vin2  

ID1 = ID2 = ISS / 2  

ID1 = ID2 = 1 mA / 2 = **0.5 mA**

---

## Bias Point Analysis

### NMOS Pair (M1, M2)

| Quantity | Expression        | Value |
|----------|------------------|-------|
| VG       | Given            | 0 V   |
| VS       | = Vp             | −0.7 V|
| VGS      | VG − VS          | 0.7 V |
| VOV      | VGS − VT         | 0.34 V|
| VD       | Given            | 0 V   |
| VDS      | VD − VS          | 0.7 V |

✔ Check:  
0.7 > 0.34 → Saturation ✔  

---
### NMOS Current Source (M5)

| Quantity | Value |
|----------|-------|
| VS       | −0.9 V |
| VD       | −0.7 V |
| VDS      | 0.2 V  |

Condition:
VDS ≥ VOV  

Choose:
VOV ≈ 0.2 V  

Then:
VGS = VT + VOV = 0.36 + 0.2 = 0.56 V  

Gate voltage:
VG = VS + VGS = −0.9 + 0.56 = **−0.34 V**

✔ Check:
0.2 ≥ 0.2 → Saturation edge ✔  

---
###  PMOS Load (M3, M4)

| Quantity | Value |
|----------|-------|
| VS       | 0.9 V |
| VD       | 0 V   |
| VSD      | 0.9 V |

✔ Since VSD ≫ VOV → Saturation ✔  

---
##  Width Calculation

### Formula

ID = (1/2) μnCox (W/L) (VOV)²  

Rearranged:
W = (2ID L) / [μnCox (VOV)²]  

---
###  M1, M2 Calculation

Given:

| Parameter | Value |
|----------|-------|
| ID       | 0.5 × 10⁻³ A |
| L        | 480 × 10⁻⁹ m |
| μnCox    | 2.365 × 10⁻⁴ |
| VOV      | 0.34 V |

Substitute:

W = (2 × 0.5 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × 0.34²)  

W = (480 × 10⁻¹²) / (2.365 × 10⁻⁴ × 0.1156)  

W = (480 × 10⁻¹²) / (2.733 × 10⁻⁵)  

W ≈ **17.56 μm**

---
###  M5 Calculation

Given:

| Parameter | Value |
|----------|-------|
| ID       | 1 × 10⁻³ A |
| VOV      | 0.2 V      |

Substitute:

W = (2 × 1 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × 0.2²)  

W = (960 × 10⁻¹²) / (2.365 × 10⁻⁴ × 0.04)  

W = (960 × 10⁻¹²) / (9.46 × 10⁻⁶)  

W ≈ **101.5 μm**

---

##  Width Optimization (Simulation)

| Transistor | Calculated (μm) | Final (μm) |
|------------|----------------|------------|
| M1, M2     | 17.56          | 29.85      |
| M5         | 101.5          | 195.85     |

---
## Observation

- Theoretical calculations provide initial sizing  
- Simulation tuning ensures:
  - Accurate biasing (Vp ≈ −0.7 V)  
  - Correct current levels  
- Practical effects (mobility, λ variation) require width adjustment  

✔ Final design satisfies both **power and bias conditions**

## DC Analysis

<img width="677" height="286" alt="image" src="https://github.com/user-attachments/assets/0e5dc9a1-5611-44e3-ae25-261c158b0f4e" />



# Input & Output Range Analysis + Linearity Check


##  Input Common-Mode Range (ICMR)

The ICMR defines the allowable input voltage range for which all transistors remain in saturation.

###  Lower Limit

To keep NMOS transistors (M1, M2) ON:

Condition:
VGS ≥ VT  

Using:
VGS = VICM − VS  

⇒ VICM(min) = VS + VT  

Substituting:
VS = −0.7 V,  VT = 0.36 V  

VICM(min) = −0.7 + 0.36 = **−0.34 V**

---

###  Upper Limit

To ensure PMOS load (M3, M4) stays in saturation:

Condition:
VSD ≥ VOVp  

Using relations and simplifying:

VICM(max) ≈ VD + |VTP|  

Substituting:
VD ≈ 0 V,  |VTP| ≈ 0.39 V  

VICM(max) = **0.39 V**

---
###  Final ICMR

| Range |
|------|
| **−0.34 V ≤ VICM ≤ 0.39 V** |

---

## Output Common-Mode Range (OCMR)

Defines allowable output swing while maintaining saturation.

###  Minimum Output Voltage

Condition:
VDS ≥ VOV  

Vout(min) ≥ VS + VOV  

Substituting:
VS = −0.7 V, VOV = 0.34 V  

Vout(min) = **−0.36 V**

---
### Maximum Output Voltage

Condition:
VSD ≥ VOVp  

Vout(max) ≤ VDD − VOVp  

Substituting:
VDD = 0.9 V, VOVp ≈ 0.25 V  

Vout(max) = **0.65 V**

---

### Final OCMR

| Range |
|------|
| **−0.36 V ≤ Vout ≤ 0.65 V** |

---
## Differential Input Range (Linear Region)

For proper linear amplification:

- Both transistors must remain in saturation  
- Tail current must be shared  

### Maximum Differential Input

vid(max) = 2VOV  

Substituting:
VOV = 0.25 V  

vid(max) = **0.5 V**

---

###  Linear Operating Range

| Range |
|------|
| **−0.5 V ≤ vid ≤ 0.5 V** |

---
##  Transient Analysis – Linearity Check

Transient simulation is used to verify linear behavior.
###  Linearity Condition

|Vid| < 2VOV  

Given:
VOV = 0.24 V  

√2VOV ≈ 1.414 × 0.24 ≈ **0.34 V**

---

### Insight

- If |Vid| < 0.34 V → Linear operation  
- If |Vid| exceeds this → Non-linear behavior begins  

✔ Confirms practical limits of the amplifier’s linear region under dynamic conditions

 ## LINEAR REGION OPERATION
<img width="674" height="142" alt="image" src="https://github.com/user-attachments/assets/a072603b-a9a0-40aa-9a01-06c9e592e4b9" />

INTERPRETATION:
✔ Output is clean and sinusoidal and that both the branches conduct equally and the amplifier behaves linearly.

## NON LINEAR REGION OPERATION
<img width="676" height="139" alt="image" src="https://github.com/user-attachments/assets/0e178754-6b35-42bd-87ff-d17c125bae76" />



**Input:**  
Vid = 400 mV  

**Check:**  
400 mV > 340 mV (VOV) →  Exceeds linear limit  

**Effect:**  
- One transistor OFF, other dominates current  
- Loss of symmetry and linear gain  

**Conclusion:**  
Circuit operates in **non-linear region** with distorted output.

## Interpretation of Operation

For low differential input levels, both NMOS devices remain active and divide the tail current nearly equally, producing a well-balanced and linear output response.
As the input difference grows, this balance is disturbed. Current gradually shifts toward one branch while the other weakens toward cutoff, introducing noticeable non-linearity and distortion in the output.

## 📊 Gain Analysis: Practical vs Ideal Behavior

### 🔹 Results from Transient Simulation

| Parameter     | Observed Value |
|---------------|---------------|
| Input (p-p)   | 100 mV        |
| Output (p-p)  | ≈ 180 mV      |

**Voltage Gain:**

Av = Vout / Vin = 180 / 100 = **1.8 V/V**

**Gain in dB:**

Av(dB) = 20 log(1.8) ≈ **5.1 dB**

---

### 🔹 Analytical (Ideal) Estimation

#### Output Resistance

ro = 1 / (λ · Id)

| Parameter | Value     |
|----------|----------|
| λ        | 0.1 V⁻¹  |
| Id       | 0.5 mA   |

ro ≈ **20 kΩ**

Effective load:

Rout ≈ ro || ro ≈ **10 kΩ**

---

#### Transconductance

gm = 2Id / Vov

| Parameter | Value     |
|----------|----------|
| Id       | 0.5 mA   |
| Vov      | ≈ 0.25 V |

gm ≈ **4 mS**

---

#### Expected Gain

Av = gm × Rout  

Av ≈ 4 mS × 10 kΩ = **40 V/V**

Av(dB) ≈ **32 dB**

---

## Practical Behavior & Deviation Analysis

The large gap between theoretical (~40) and simulated (~1.8) gain arises due to real-device effects that are ignored in first-order calculations.

---
### 1. Channel Length Modulation (λ Variation)

- In theory, λ is assumed constant  
- In practice, λ varies with VDS and device geometry  
- This reduces output resistance (ro ↓)  
- Lower ro → lower Rout → reduced gain  

---
### 2. Non-Ideal Tail Current Source

- Ideal assumption: constant current source  
- Real NMOS (M5) has finite output resistance  
- Current varies with voltage → imperfect current steering  
- This reduces differential gain and symmetry  

---

### 3. Limited Output Resistance

- Theoretical model simplifies Rout = ro || ro  
- In reality, multiple devices contribute to output impedance  
- Interaction between NMOS pair + PMOS load + current source lowers effective Rout  

---
### 4. Mobility Degradation

- Carrier mobility decreases at high electric fields  
- This reduces effective transconductance (gm ↓)  
- Lower gm directly reduces gain  

---
### 5. Parasitic Capacitances

- Internal capacitances: Cgs, Cgd, Cdb  
- External load: CL = 10 pF  
- These introduce frequency-dependent effects  
- Signal attenuation occurs even at moderate frequencies  

---
### 6. Bias Point Variations

- Small shifts in node voltages affect VOV  
- Since gm ∝ 1/VOV, even slight changes impact gain  
- Leads to mismatch between ideal and simulated results  

---
## Final Insight

- Analytical gain represents an **upper bound**
- Simulation reflects **realistic device behavior**
- Performance is governed by trade-offs between:
  - Gain  
  - Linearity  
  - Stability  

✔ The observed result highlights the importance of **simulation-based refinement** in analog design.


##  AC Analysis – Frequency Response

### 🔹 Excitation Setup

| Parameter        | Value              |
|------------------|--------------------|
| Vin1             | +0.5 AC            |
| Vin2             | −0.5 AC            |
| Sweep Range      | 1 Hz → 1 GHz       |

**Measured Output:**

Vout = V(out1) − V(out2)

---

<img width="925" height="188" alt="image" src="https://github.com/user-attachments/assets/11975378-74d6-4216-8a09-0125f0a27742" />


### Key Results

- Midband Gain ≈ **5.4 dB**  
- Bandwidth extends up to **hundreds of MHz**  
- Gain reduces progressively at higher frequencies  

---

### Response Characteristics

- Flat gain region observed at low–mid frequencies  
- High-frequency attenuation due to parasitic effects  
- Overall response resembles a **low-pass filter**

---

### Interpretation

- Circuit exhibits stable **differential amplification**  
- Biasing ensures proper small-signal operation  
- Gain remains linear within operating range  
- Reduced gain compared to theory confirms **real-world non-idealities**



# Circuit 3: CMOS Differential Amplifier with Bias-Controlled PMOS Load

<img width="185" height="247" alt="image" src="https://github.com/user-attachments/assets/494860a6-1fc0-4fe2-a897-4c738e1482d4" />

## Working Principle

This configuration employs a matched NMOS differential pair (M1, M2) whose common source node is biased by a constant tail current source (M5). The drains are connected to PMOS transistors (M3, M4), which act as active loads.

Unlike a current mirror load, the gates of M3 and M4 are driven by a fixed bias voltage (Vb2). This ensures that the PMOS devices operate as controlled current sources, offering high output resistance without enforcing strict current mirroring.

---
## Operation Mechanism

For a differential input:

vid = vin1 − vin2  

- When vin1 > vin2 → M1 draws a larger portion of ISS, reducing current through M2  
- When vin2 > vin1 → M2 conducts more, while M1 current decreases  

Thus, the constant tail current is dynamically steered between the two branches based on the input difference.

---
## Role of Bias-Controlled PMOS Load

- PMOS transistors (M3, M4) convert current variations into voltage variations at the output  
- Biasing via Vb2 ensures stable operation in saturation  
- High output resistance enhances voltage gain significantly  

---
## Output Characteristics

- Output is typically taken from one drain (single-ended output)  
- Produces an amplified version of the differential input signal  

---
## Operating Regions

**Small-Signal Operation:**
- M1 and M2 remain in saturation  
- Current is shared smoothly  
- Output is linear and proportional to input  

**Large-Signal Operation:**
- One transistor approaches cutoff  
- Other carries most of ISS  
- Output exhibits non-linearity  

---
## Key Advantage

This topology achieves **high gain and improved output swing** by combining a differential pair with bias-controlled PMOS active loads, offering better performance compared to resistive and current-mirror-based designs.






# Design Calculations – CMOS Differential Amplifier (Bias-Controlled Load)

<img width="448" height="329" alt="image" src="https://github.com/user-attachments/assets/eb55d01d-2765-4763-b10e-1928c09efb56" />

##  Given Parameters

| Parameter                  | Symbol     | Value            |
|---------------------------|------------|------------------|
| Technology                | —          | TSMC 180 nm      |
| Supply Voltages           | VDD / VSS  | +0.9 V / −0.9 V  |
| Power Limit               | P          | ≤ 1.8 mW         |
| Channel Length            | L          | 480 nm           |
| Input CM Voltage          | Vin,CM     | 0 V              |
| Output CM Voltage         | Vo,CM      | 0 V              |
| Tail Node Voltage         | Vp         | −0.7 V           |
| Load Capacitance          | CL         | 10 pF            |
| Threshold Voltage         | VT         | ≈ 0.36 V         |

---
##  Power Constraint

Total supply voltage:

VDD − VSS = 0.9 − (−0.9) = **1.8 V**

Power equation:

P = (VDD − VSS) × ISS  

Substitute maximum allowed power:

1.8 × ISS ≤ 1.8 × 10⁻³  

Solve:

ISS ≤ (1.8 × 10⁻³) / 1.8  
ISS ≤ **1 × 10⁻³ A = 1 mA**

✔ Choose:
ISS = **1 mA**

Verification:

P = 1.8 × 1 × 10⁻³ = **1.8 mW** ✔

---
## Drain Current Calculation

At zero differential input:

Vin1 = Vin2  

Tail current splits equally:

ID1 = ID2 = ISS / 2  

Substitute:

ID1 = ID2 = (1 × 10⁻³) / 2  
ID1 = ID2 = **0.5 × 10⁻³ A = 0.5 mA**

---

## Bias Point Calculations

###  NMOS Differential Pair (M1, M2)

Gate voltage:

VG = Vin,CM = **0 V**

Source voltage:

VS = Vp = **−0.7 V**

####  Gate-Source Voltage

VGS = VG − VS  
VGS = 0 − (−0.7)  
VGS = **0.7 V**

####  Overdrive Voltage

VOV = VGS − VT  
VOV = 0.7 − 0.36  
VOV = **0.34 V**

#### Drain Voltage

Given:

VD = Vo,CM = **0 V**

####  Drain-Source Voltage

VDS = VD − VS  
VDS = 0 − (−0.7)  
VDS = **0.7 V**

---

####  Saturation Check

Condition:

VDS > VOV  

0.7 > 0.34 ✔  

→ M1 and M2 operate in **saturation**

---

### NMOS Current Source (M5)

Source:

VS = VSS = **−0.9 V**

Drain:

VD = Vp = **−0.7 V**

#### Drain-Source Voltage

VDS = VD − VS  
VDS = −0.7 − (−0.9)  
VDS = **0.2 V**

#### Choose Overdrive

To keep M5 in saturation:

VDS ≥ VOV  

Choose:

VOV ≈ **0.2 V**

####  Gate-Source Voltage
VGS = VT + VOV  
VGS = 0.36 + 0.2  
VGS = **0.56 V**

---
#### Gate Voltage

VG = VS + VGS  
VG = −0.9 + 0.56  
VG = **−0.34 V**

---
#### Saturation Check

0.2 ≥ 0.2 ✔  

→ M5 operates at **edge of saturation**

###  PMOS Load (M3, M4)

Source:

VS = VDD = **0.9 V**

Drain:

VD = **0 V**

---
####  Source-Drain Voltage

VSD = VS − VD  
VSD = 0.9 − 0  
VSD = **0.9 V**

#### Saturation Check

Condition:

VSD > VOV  

0.9 ≫ 0.25 ✔  

→ PMOS devices are in **deep saturation**

## Width Calculations

###  Formula

ID = (1/2) μnCox (W/L) (VOV)²  

Rearranged:

W = (2ID L) / [μnCox (VOV)²]

---
###  NMOS Differential Pair (M1, M2)

Substitute values:

W = (2 × 0.5 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × (0.34)²)

Numerator:

= 2 × 0.5 × 10⁻³ × 480 × 10⁻⁹  
= 480 × 10⁻¹²  

Denominator:

(0.34)² = 0.1156  

= 2.365 × 10⁻⁴ × 0.1156  
= 2.733 × 10⁻⁵  
#### Final:

W = (480 × 10⁻¹²) / (2.733 × 10⁻⁵)  
W ≈ **17.56 μm**

###  NMOS Current Source (M5)

Substitute:

W = (2 × 1 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × (0.2)²)

---

Numerator:

= 960 × 10⁻¹²  

Denominator:

(0.2)² = 0.04  

= 2.365 × 10⁻⁴ × 0.04  
= 9.46 × 10⁻⁶  

#### Final:

W = (960 × 10⁻¹²) / (9.46 × 10⁻⁶)  
W ≈ **101.5 μm**

## Width Refinement (Simulation)

| Transistor | Calculated (μm) | Final (μm) |
|------------|----------------|------------|
| M1, M2     | 17.56          | 29.85      |
| M5         | 101.5          | 195.85     |

---
## Insight

- Step-by-step calculations establish correct operating region  
- Practical simulation accounts for non-idealities  
- Increased width → higher gm → improved gain  

✔ Final design achieves:
- Accurate biasing  
- Stable current operation  
- Desired amplifier performance  

#  Design Analysis – CMOS Differential Amplifier (Bias-Controlled PMOS Load)

---


##  Design Specifications

| Parameter                  | Symbol     | Value            |
|---------------------------|------------|------------------|
| Technology                | —          | TSMC 180 nm      |
| Supply Voltages           | VDD / VSS  | +0.9 V / −0.9 V  |
| Power Budget              | P          | ≤ 1.8 mW         |
| Channel Length            | L          | 480 nm           |
| Input Common Mode         | Vin,CM     | 0 V              |
| Output Common Mode        | Vo,CM      | 0 V              |
| Tail Node Voltage         | Vp         | −0.7 V           |
| Load Capacitance          | CL         | 10 pF            |
| Threshold Voltage         | VT         | ≈ 0.36 V         |

---

## Power Budget & Tail Current

Total supply span:

VDD − VSS = 0.9 − (−0.9) = **1.8 V**

Power relation:

P = (VDD − VSS) · ISS  

Constraint:

1.8 · ISS ≤ 1.8 × 10⁻³  

⇒ ISS ≤ **1 mA**

✔ Selected:

ISS = **1 mA**

Power check:

P = 1.8 × 1 mA = **1.8 mW** ✔

---

## Current Distribution

At zero differential input:

Vin1 = Vin2  

Current splits evenly:

ID1 = ID2 = ISS / 2 = **0.5 mA**

---

## Bias Conditions

###  NMOS Pair (M1, M2)

| Quantity | Expression | Value |
|----------|------------|-------|
| VG       | Vin,CM     | 0 V   |
| VS       | Vp         | −0.7 V |



VGS = VG − VS = 0 − (−0.7) = **0.7 V**

VOV = VGS − VT = 0.7 − 0.36 = **0.34 V**

VD = 0 V  

VDS = VD − VS = 0 − (−0.7) = **0.7 V**

✔ Saturation:

0.7 > 0.34 → **Valid**

---

### Tail Current Source (M5)

| Node | Value |
|------|-------|
| VS   | −0.9 V |
| VD   | −0.7 V |

VDS = 0.2 V  

**Step 2: Choose:**

VOV ≈ 0.2 V  

VGS = VT + VOV = 0.36 + 0.2 = **0.56 V**

VG = VS + VGS = −0.9 + 0.56 = **−0.34 V**

✔ Edge saturation ensured:

VDS ≈ VOV

---
### PMOS Active Load (M3, M4)

| Node | Value |
|------|-------|
| VS   | 0.9 V |
| VD   | 0 V   |
| VG   | Vb2   |

**Saturation condition:**

VSD ≥ VSG − |VTp|

Deriving:

Vb2 ≥ **−0.39 V**

✔ Selected:

Vb2 ≈ **−0.36 V**

---

**Verification:**

VSG = 0.9 − (−0.36) = **1.26 V**  

VOV(p) = 1.26 − 0.39 = **0.87 V**

Check:

0.9 > 0.87 ✔ → Saturation confirmed

---

## Device Sizing

### General Expression

W = (2 ID L) / [μ Cox (VOV)²]

---

### NMOS Pair (M1, M2)

Given:

- ID = 0.5 mA  
- μnCox = 2.365 × 10⁻⁴  
- VOV = 0.34 V  

**Calculation:**

W = (2 × 0.5 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × 0.1156)

W ≈ **17.56 μm**

✔ Final:

W1 = W2 ≈ **17.6 μm**

---

### Tail Transistor (M5)

Given:

- ID = 1 mA  
- VOV = 0.2 V  

**Calculation:**

W5 = (2 × 1 × 10⁻³ × 480 × 10⁻⁹) / (2.365 × 10⁻⁴ × 0.04)

W5 ≈ **101.5 μm**

---
### PMOS Load (M3, M4)

Given:

- μpCox = 9.98 × 10⁻⁵  
- ID = 0.5 mA  
- VOV(p) = 0.87 V  

**Calculation:**

Wp = (2 × 0.5 × 10⁻³ × 480 × 10⁻⁹) / (9.98 × 10⁻⁵ × 0.7569)

Wp ≈ **6.35 μm**

✔ Final:

W3 = W4 ≈ **6.35 μm**

---

## Post-Simulation Optimization

| Device | Theoretical (μm) | Optimized (μm) |
|--------|-----------------|----------------|
| M1, M2 | 17.56           | 32             |
| M5     | 101.5           | 209.15         |
| M3, M4 | 6.35            | 13.88          |

---

## Insights

- Analytical sizing gives **first-order estimates**
- Simulation tuning compensates for:
  - Short-channel effects  
  - Mobility degradation  
  - Bias shifts  
- Increased widths → higher **gm → improved gain & stability**

✔ Final design ensures:
- All devices in saturation  
- Accurate bias control  
- High-gain differential operation

DC Analysis – CMOS Differential Amplifier
DC analysis is performed to verify the **biasing conditions** of the circuit and ensure that all transistors operate in the **saturation region**, which is essential for proper differential amplification.

<img width="725" height="325" alt="image" src="https://github.com/user-attachments/assets/0ea55ba3-6201-4994-a3b3-3f60a677b1ea" />




