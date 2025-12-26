# BANDGAP REFERENCE (BGR) CIRCUIT - OVERVIEW
## 1. What is Bandgap Reference Circuit?
A Bandgap Reference (BGR) is a self-biased analog reference circuit that exploits the well-characterized temperature dependencies of bipolar junction transistor (BJT) junction voltages to generate a process- and temperature-stable reference quantity, most commonly a voltage near 1.2 V. The reference is obtained by summing a CTAT component (the base–emitter voltage VBE) with a scaled PTAT component derived from the differential base–emitter voltage ΔVBE of matched BJTs operated at unequal current densities.

From a circuit standpoint, the BGR establishes a PTAT current using device matching and resistor ratios, converts this current into a voltage, and combines it with VBE through negative feedback to enforce a well-defined operating point. Proper loop design ensures that the generated reference exhibits low temperature coefficient, high power-supply rejection, and robust bias stability across PVT corners. In CMOS implementations, the required BJTs are typically realized as parasitic vertical or lateral devices, allowing full on-chip integration without additional process steps.

## Block Diagram
<img width="313" height="161" alt="image" src="https://github.com/user-attachments/assets/0c2024d0-57ab-4981-a1c6-8905c7b2524d" />

Inputs: VDD (supply with variations), VSS (ground)
Output: VOUT (reference voltage)


## Why BGR 
- A battery is not suitable to use as a reference voltage source as it's voltage reduces with time
  
- A typical power supply gives noisy output or ripple superimposed in dc so it is also not suitable 
  
- Use of voltage reference IC with buried Zener diode, requires additional components and high frequency filtering circuits
  
- Unavailability of low voltage zener diode

**Solution**
- Ease of integration of Bandgap reference wthn bulk CMOS, Bi-CMOS or Bipolar technologies without the use of external components makes it suitable to use it as reference voltage generator.

## 2. Operating Principle
The bandgap reference relies on combining two voltages with opposite temperature coefficients (TC):
- #### 1. CTAT Voltage (Complementary To Absolute Temperature)
  - Derived from the base–emitter voltage (V_BE) of a BJT.
  - V_BE decreases with temperature at approximately −1.6 mV/K.
- #### 2. PTAT Voltage (Proportional to Absolute Temperature)
  - Generated from the difference between the V_BE values of two BJTs operating at different current densities.
  - This difference, ΔV_BE, increases linearly with temperature.
By properly scaling and summing the PTAT and CTAT voltages, the temperature dependencies cancel out:
VREF​=VBE​+k⋅ΔVBE
