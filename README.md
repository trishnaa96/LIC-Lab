# Experiment 1

## DC, AC and Transient Analysis of Common Source Amplifier

---

### Aim
To perform DC analysis, AC analysis and Transient analysis of a Common Source (CS) amplifier using LTspice.

### Theory
A Common Source (CS) amplifier is a fundamental MOSFET configuration where the input is applied to the gate and the output is taken from the drain. It provides high voltage gain and a 180° phase shift. For effective amplification, the MOSFET must be biased in the **Saturation Region**.

**Saturation Condition:**
$$V_{DS} \geq (V_{GS} - V_T)$$

**Drain Current Equation:**
$$ID = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_T)^2$$

**Voltage Gain ($A_v$):**
$$A_v = -g_m R_D$$

---

### Circuit Diagram
<img width="955" height="413" alt="image" src="https://github.com/user-attachments/assets/f869f85a-a484-4426-b6b0-9fcb8d5a46b6" />



---

## Procedure
1. Open the **LTspice** software.
2. Draw the circuit using an **NMOS** transistor.
3. Set the supply voltage **Vdd = 1.5V**.
4. Apply a sine wave input to the gate terminal.
5. Use **DC analysis** to check the operating point.
6. Use **Transient analysis** to see the input and output waves.
7. Use **AC analysis** to find the gain and bandwidth.

## Operating Point Analysis (.op)

<img width="538" height="341" alt="image" src="https://github.com/user-attachments/assets/97a5ab33-d31e-4eac-b865-057da50cf7d8" />


Operating point analysis (.op) is carried out to determine the DC biasing
conditions of the Common Source amplifier circuit. In this analysis,
LTspice computes the steady-state values of the gate voltage (Vg),
source voltage (Vs), drain current (Id), and output voltage (Vout).

For the given circuit, the NMOS source terminal is connected to ground,
the gate is biased using a DC voltage source, and the drain is connected
to the supply through the drain resistor (RD). The operating point
analysis verifies that the gate-to-source voltage (VGS) is greater than
the threshold voltage (VT), ensuring that the transistor is turned ON.

It also confirms that the condition VDS ≥ (VGS − VT) is satisfied,
indicating that the MOSFET operates in the saturation region. Operation
in the saturation region is essential for proper amplification in a
Common Source configuration. Thus, the operating point analysis ensures
correct biasing of the transistor before performing transient and AC
analyses.

### Transistor Width Adjustment

To achieve the required drain current (Id), the width (W) of the NMOS
transistor was modified during the design process.

Initially:
W = 1.833 µm  

After tuning to meet the desired Id:
W = 2.7528 µm  

By increasing the transistor width, the effective channel area
increased, which in turn increased the drain current according to
the MOSFET current equation. This adjustment ensured that the
target operating point and power constraints were satisfied while
maintaining proper saturation region operation.





## Design Calculations

### Given Parameters

- Supply Voltage, VDD = 1.5 V  
- Power Constraint, P ≤ 0.5 mW  
- Load Capacitance, CL = 1 pF  
- Channel Length, L = 180 nm  
- Assumed Drain Current, Id = 0.334 mA  

---

### Power Verification

The power consumed by the circuit is:

P = VDD × Id  
  = 1.5 × 0.334 mA  
  = 0.501 mW  

The calculated power is approximately equal to 0.5 mW, which satisfies
the specified power constraint.

---

### Drain Resistor Calculation

For maximum symmetrical output swing, the quiescent output voltage is selected as:

Vout ≈ VDD / 2  
Vout ≈ 1.5 / 2 = 0.75 V  

Using the relation:

Vout = VDD − Id × RD  

0.75 = 1.5 − (0.334 × 10⁻³ × RD)

Solving for RD:

RD ≈ 2245 Ω  
RD ≈ 2.245 kΩ  

---

### MOSFET Sizing

In the saturation region, the drain current is given by:

Id = (μnCox / 2) × (W/L) × (VGS − VT)²  

Using 180 nm CMOS technology parameters and solving for W,
the transistor width was determined and refined through simulation.

Final NMOS Dimensions:

W = 1.833 µm  
L = 180 nm  

These values ensure the required drain current,
satisfy the power limitation,
and provide proper biasing for maximum output swing.

## DC Analysis

<img width="708" height="308" alt="image" src="https://github.com/user-attachments/assets/b3139f9e-d505-4dd5-a884-436d78f3a2c4" />


DC analysis is carried out by sweeping the gate voltage (VG) from 0 V to 2 V
while keeping the supply voltage fixed at VDD = 1.5 V. This analysis shows
the variation of output voltage (Vout) with respect to the gate voltage.

At low values of VG, the NMOS transistor remains in the cutoff region and
Vout stays close to VDD. As VG increases beyond the threshold voltage, the
transistor turns ON, the drain current increases, and Vout decreases due to
the voltage drop across the drain resistor.

The sloped region of the Vout–VG curve corresponds to the saturation region,
which is suitable for amplification. DC analysis therefore helps in selecting
the proper gate bias for linear operation of the Common Source amplifier.



## Transient Analysis

<img width="947" height="411" alt="image" src="https://github.com/user-attachments/assets/61d1666d-fc00-489b-a533-4f112f1f2b3c" />



## Gain Calculation

### Theoretical Voltage Gain

The small-signal voltage gain of a Common Source amplifier is given by:

Av = gm × RD

The transconductance (gm) is calculated as:

gm = 2Id / Vov

where the overdrive voltage is:

Vov = VGS − VT  
Vov = 0.9 − 0.366 = 0.534 V

Substituting values:

gm = (2 × 0.334 mA) / 0.534  
gm ≈ 1.25 mS

The theoretical voltage gain is therefore:

Av = 1.25 mS × 2.245 kΩ  
Av ≈ 2.81

Gain in decibels:

Av(dB) = 20 log10(Av)  
Av(dB) ≈ 8.97 dB

---

### Practical Gain from Transient Analysis

From the transient response:

Vout(p-p) = 40.44 mV  
Vin(p-p) = 19.373 mV  

The practical voltage gain is:

Av = Vout / Vin  
Av ≈ 2.09

Gain in decibels:

Av(dB) = 20 log10(Av)  
Av(dB) ≈ 6.39 dB

### AC Analysis

AC analysis is performed to determine gain and bandwidth of the amplifier.

Observations
The amplifier shows constant gain in the midband region.
At higher frequencies, gain decreases due to parasitic capacitances.

<img width="955" height="409" alt="image" src="https://github.com/user-attachments/assets/ac1d732f-9119-45c9-9553-c0775428ddef" />


<img width="953" height="416" alt="image" src="https://github.com/user-attachments/assets/e74f1b70-fce3-4531-8657-0b28a5913b37" />


<img width="956" height="421" alt="image" src="https://github.com/user-attachments/assets/74e9c1cf-81a9-46ab-8156-f9be57ee441d" />


## Bandwidth Calculation

The bandwidth of the Common Source amplifier is determined from the
frequency response obtained using AC analysis. Bandwidth is defined as
the frequency range over which the gain remains within 3 dB of its
midband value.

Bandwidth is expressed as:

BW = fH − fL

In this circuit, the lower cutoff frequency (fL) is approximately zero,
since no coupling or bypass capacitors are used at low frequencies.
Hence, the bandwidth is mainly limited by the upper cutoff frequency.

BW ≈ fH

From the AC response plot, the −3 dB frequency occurs at:

fH ≈ 89.58 MHz

Therefore, the bandwidth of the Common Source amplifier is approximately:

BW ≈ 89.58 MHz


## Result

A Common Source (CS) amplifier employing an NMOS transistor in 
180 nm CMOS technology was designed and simulated using LTspice. 
DC analysis was performed to determine the biasing conditions of 
the circuit. The obtained operating point confirmed that the 
MOSFET operates in the saturation region, which is essential 
for proper small-signal amplification.

### Transient Analysis

From the time-domain simulation:

Vin(p-p) ≈ 19.373 mV  
Vout(p-p) ≈ 40.44 mV  

The corresponding voltage gain is:

Av ≈ 2.808  

Expressed in decibels:

Av(dB) ≈ 8.94 dB  

The output waveform exhibited a 180° phase shift relative to the 
input signal, validating the expected behavior of a Common Source 
configuration.

### AC Analysis

The frequency response of the amplifier was evaluated using AC 
analysis. The −3 dB upper cutoff frequency was observed at 
approximately 89.52 MHz.

Since the lower cutoff frequency is close to zero, the bandwidth 
of the amplifier is approximately:

BW ≈ 89.52 MHz

Overall, the designed CS amplifier demonstrates stable voltage 
amplification, proper phase inversion, and satisfactory 
high-frequency performance within the specified design constraints.

## Conclusion

In this work, a Common Source (CS) amplifier was designed and evaluated using an NMOS transistor in 180 nm CMOS technology with LTspice simulation. The transistor sizing was carefully chosen to meet the specified drain current and power limitations while maintaining reliable operation.

DC operating point analysis confirmed that the MOSFET is biased in the saturation region, which is essential for achieving stable small-signal amplification. Transient analysis demonstrated proper voltage amplification with an inherent 180° phase inversion between the input and output waveforms.

The simulated voltage gain was approximately 6.395 dB, which closely aligns with the theoretical gain calculated during the design phase, thereby validating the accuracy of the design approach. Frequency-domain (AC) analysis was performed to evaluate the amplifier’s response, and the resulting bandwidth indicated satisfactory performance at higher frequencies.

Overall, the designed Common Source amplifier delivers effective voltage gain with controlled power dissipation and acceptable bandwidth, making it well-suited for analog integrated circuit applications in CMOS technology.









