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
