# Experiment 2

## Design and Simulation of Various Amplifier Configurations Using 180 nm Technology Library in LTspice.

## Objective

A)To design and analyze a Common Source (CS) amplifier using 180nm CMOS technology with PMOS active load.

# Circuit 1

**This is CKT 1**

<img width="230" height="155" alt="image" src="https://github.com/user-attachments/assets/2cff4cf0-36b7-486a-bad4-192afe289c26" />

## NMOS Design Calculations (180 nm Technology)

### Given / Assumptions
- Technology : 180 nm
- For NMOS
- Supply Voltage, VDD = 1.5 V
- Overdrive Voltage, Vov = 0.25 V
- Threshold Voltage, Vth = 0.36 V
- Mobility factor, μnCox = 230 µA/V²
- Channel Length, L = 180 nm

### Gate-to-Source Voltage

Vov = VGS − Vth  

0.25 = VGS − 0.36  

VGS = 0.61 V  

### Output Voltage

Vout = VDD / 2 + 0.2  

Vout = 2 / 2 + 0.2  

Vout = 1.2 V  

### Drain Current

P = V × I  

0.5 mW = 1.5 × ID  

ID = 0.334 mA  

### Source Resistance

VRS = ID × RS  

0.2 = 0.334 × 10⁻³ × RS  

RS = 598.8 Ω  

### Gate Voltage

VG = VGS + VRS  

VG = 0.61 + 0.2  

VG = 0.81 V  

### Saturation Condition

VDS ≥ VGS − Vth  

VDS ≥ 0.61 − 0.36  

VDS ≥ 0.25 V  

Condition satisfied  

### Drain Current Equation

ID = ½ μnCox × W/L × Vov²  

0.334 × 10⁻³ = ½ × 230 × 10⁻⁶ × W / 180 × 10⁻⁹ × 0.25²  

### Transistor Width

W = 8.364 µm  

### Final NMOS Dimensions
- L = 180 nm  
- W = 8.364 µm

## PMOS Design Calculations (180 nm Technology)

### Given / Assumptions
- Technology : 180 nm
- For PMOS
- Supply Voltage, VDD = 1.5 V
- Overdrive Voltage, Vov = 0.25 V
- Threshold Voltage, |Vtp| = 0.39 V
- Drain Current, ID = 0.334 mA
- Mobility factor, μpCox = 115.689 µA/V²
- Channel Length, L = 180 nm

### Source-to-Gate Voltage

Vov = VSG − |Vtp|  

0.25 = VSG − 0.39  

VSG = 0.64 V  

### Gate Voltage

VSG = VS − VG  

VS = VDD  

0.64 = 1.5 − VG  

VG = 1.5 − 0.64  

VG = 0.86 V  

### Drain Current Equation

ID = ½ μpCox × W/L × Vov²  

0.334 × 10⁻³ = ½ × 115.689 × 10⁻⁶ × W / 180 × 10⁻⁹ × 0.25²  

### PMOS Width

W = 19.75 µm  

### Final PMOS Dimensions
- L = 180 nm  
- W = 19.75 µm

  <img width="827" height="450" alt="image" src="https://github.com/user-attachments/assets/13f31c43-2893-4008-b134-4fe1270e8306" />

## Operating Point (.op)

NMOS and PMOS are verified to operate in saturation at the DC operating point.

<img width="853" height="427" alt="image" src="https://github.com/user-attachments/assets/43c9f553-b1e0-44c7-8082-9c0c94afa11e" />


## DC Analysis

<img width="959" height="420" alt="image" src="https://github.com/user-attachments/assets/7fc695ea-6313-4ed9-b1a8-bb12dcbaeb0d" />


PMOS width varied:  
W = 6.286 × 10⁻⁵ m  

NMOS width varied:  
W = 4.832 × 10⁻⁵ m


## Transient Analysis

<img width="944" height="430" alt="image" src="https://github.com/user-attachments/assets/ccc33e28-e761-46c6-90a0-a0553a3dcdcf" />


Gain(practical) = Vout / Vin  
= (1.0373 − 0.84293) / (819.99m − 800m)  
= 9.72  

Voltage Gain (dB) = 20 log₁₀(9.72) = 19.75 dB

Gain(theoretical)=






## AC Analysis

<img width="958" height="415" alt="image" src="https://github.com/user-attachments/assets/30804fc7-fff3-43d4-a030-0112bba590fb" />


Gain = 19.779 − 3 dB = 16.75 dB  
Bandwidth = 215.120 MHz  
Cut-off Frequency = 219.120 MHz


## Circuit 2
B)To design and analyze a Common Source amplifier using 180nm CMOS technology with current source load.

**This is CKT 2**
<img width="524" height="314" alt="image" src="https://github.com/user-attachments/assets/60eab218-4112-491e-9f4a-7a39671b952b" />

## Calculations

Assume Vov = 0.25 V
From datasheet Vth=0.366V  &| Vin|= 0.38V

VGS = Vov + Vth  
VGS = 0.25 + 0.36  
VGS3 = 0.61 V  (M3)
VB2= VGS3= 0.61V

### For PMOS(M3)

VSG = VS − VG  

VS = VDD  

0.64 = 1.5 − VG  

VG = VB1= 1.5 − 0.64  

VG = 0.86 V  
Take VDS3= 0.25V

Vov = VSG − |VT|  

0.25 = VSG − 0.39  

VSG = 0.64 V  
VGS2=Vin-VS2
0.61=Vin-0.25
Vin= 0.86V

### Saturation Conditions

For M3:  
VDS3 ≥ Vov  
VDS3 ≥ 0.25 V  

Take VDS3 = 0.25 V  

For M2:  
VDS2 ≥ Vov  
VDS2 ≥ 0.25  

VO ≥ 0.5 V  

For M1:  
VSD1 ≥ Vov  
VSD1 = VDD − VO  
1.5 − VO ≥ 0.25  

VO ≤ 1.25 V  

With calculations we assume as previous one:

NMOS (M2, M3):  
W = 8.34 µm  L=180nm

PMOS (M1):  
W = 19.7 µm  L=180nm

## Operating Point

<img width="716" height="356" alt="image" src="https://github.com/user-attachments/assets/8126971c-3258-484c-a0e5-caa6bd47b6c7" />


---
## DC Analysis


Varied W = 28.773 µm (NMOS)  

Varied W = 63.264 µm (PMOS)  
OP after varing the width is shown below
<img width="953" height="388" alt="image" src="https://github.com/user-attachments/assets/65d17027-b772-4d9b-8676-ea30ac31b968" />


For these values of width we get:  

ID = 333 µA  

VO = 1.08 V  

It shows Vin
<img width="950" height="413" alt="image" src="https://github.com/user-attachments/assets/e3d85f08-2eaf-45e0-870c-a4dcd649b804" />


It shows Vout
<img width="952" height="385" alt="image" src="https://github.com/user-attachments/assets/e8c4746f-9940-44fc-9c78-7e701e0e247b" />


<img width="955" height="419" alt="image" src="https://github.com/user-attachments/assets/27014fea-1c55-4f43-88c8-a5d0877ef6bc" />
This shows 180 degree phase shift between input and output.




## Transient Analysis


<img width="952" height="408" alt="image" src="https://github.com/user-attachments/assets/a64001f9-9455-4591-9f3f-d26ae884410f" />


Gain = Vout / Vin  

Gain = (1.031 − 0.985) / (870m − 850.43m)  

Gain = 2.269 V/V = 7.12 dB

To maximise swing:

Midpt = 0.5 + 1.25 /2

Midpt = 0.83 V  

---

## AC Analysis


<img width="943" height="430" alt="image" src="https://github.com/user-attachments/assets/d2c81a42-e53c-42ee-a681-03219146da12" />
This after -3dB


Gain = 7.25 (practical)  

7.25 − 3 dB = 4.21  

fH = 245.54 MHz  

Bandwidth = 245.5 MHz  

GBP = 2.269 × 245.5 MHz  

GBP = 557.13 MHz

Theoretical Gain:


## Circuit 3
C)To design and analyze a Common Source (CS) amplifier using 180nm CMOS technology with diode configuration.


**This is CKT 3**

<img width="518" height="299" alt="image" src="https://github.com/user-attachments/assets/5827b01a-afab-43d4-a579-d05912196486" />


## Calculations

P = Vout × ID  

ID = 0.333 mA  

---

Since M3 is diode-connected:

VGS3 = VDS3  

Assume Vov = 0.25 V  

VGS3 = Vov + Vtn  

VGS3 = 0.25 + 0.366  

VGS3 = 0.61 V  

---

### For M1

VGS1 = Vin − VS1  

VGS1 = 0.25 + 0.366  

VS1 = 0.61 V  

Thus,

Vin = 0.61 + 0.61  

Vin = 1.22 V  

---

### For PMOS

VSG2 = Vov + |VTp|  

VSG2 = 0.25 + 0.39  

VSG2 = 0.64 V  

VB1 = VDD − VSG2  

VB1 = 1.5 − 0.64  

VB = 0.86 V  

---

## Saturation Conditions

### For M1 Saturation

VDS1 ≥ Vov  

VDS1 = VO − VS1  

VO − 0.61 ≥ 0.25  

VO ≥ 0.86 V  

---

### For PMOS(M3)Saturation

VSD2 ≥ Vov  

1.5 − VO ≥ 0.25  

VO ≤ 1.25 V  

---

Output range:

0.86 V ≤ VO ≤ 1.25 V  

Chosen:

VO = 1.055 V  
Also Vout= VDD/2 + VGS3 

---
The Ltspice circuit is shown below
<img width="439" height="317" alt="image" src="https://github.com/user-attachments/assets/bd10a0f0-accc-4cc1-917c-89481bcc350f" />


## Width Calculations

Same ID & Vov, so:

M1 = 8.3 µm (NMOS)  

M3 = 8.3 µm (NMOS)  

M2 = 19.7 µm (PMOS)  

---
## Operating Point ( before width is varied)

<img width="895" height="427" alt="image" src="https://github.com/user-attachments/assets/33a3ba06-a263-40bf-bce5-49bb59f933eb" />




## DC Analysis

After tuning & rounding:

W = 62.55 µm (NMOS)  

W = 79.08.08 µm (PMOS)  

For these values of width, we get:

ID = 329 µA  

VO = 1.36 V  

<img width="909" height="437" alt="image" src="https://github.com/user-attachments/assets/d878e4e3-a504-44a5-af75-2ff36df2e65e" />


## Transient Analysis

<img width="948" height="385" alt="image" src="https://github.com/user-attachments/assets/441f7bb9-1b82-4e27-b20e-d7aeeeafa5f1" />


<img width="948" height="374" alt="image" src="https://github.com/user-attachments/assets/c86ef653-a28a-4163-827a-cf38b11efc4b" />


<img width="953" height="407" alt="image" src="https://github.com/user-attachments/assets/f65200de-0ad6-4dd8-968c-8cfbdc71a2ae" />



Gain = Vout / Vin  

Gain = (1.390 − 1.313) / (1.229 − 1.210)  

Gain = 4.052 V/V  

Gain = 12.15 dB  

---

## AC Analysis

<img width="952" height="485" alt="image" src="https://github.com/user-attachments/assets/f744d764-6a9a-4437-8d04-3e9b9fc9fe89" />



Gain = 11.23 (max)  

11.23 − 3 dB  

= 8.23 dB  

fH = 1.1789 GHz  

Bandwidth = 1.1789 GHz  

GBP = 4.052 × 1.1789  

GBP = 4.7739 GHz  

Theoretical gain:








  
