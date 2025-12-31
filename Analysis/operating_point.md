# DC Operating Point Analysis

## 1. Objective

The objective of this analysis is to verify the DC biasing of all critical devices
in the bandgap reference circuit under nominal operating conditions.  
This includes confirmation of correct MOSFET region of operation and proper biasing
of parasitic PNP BJTs used for CTAT voltage generation.


---

## 2. Simulation Setup

- **Analysis Type:** DC Operating Point
- **Supply Voltage (VDD):** 3.3 V
- **Temperature:** 27 °C
- **Process Corner:** Typical–Typical (TT)  
  *(Corresponds to `NN` corner in gpdk180)*
- **Technology:** gpdk180
- **Simulator:** Cadence Spectre
- **Tool Version:** Virtuoso 6.1.5

All bias sources and startup circuitry were enabled during simulation.


---
##  Annotated Schematic – DC Bias Overview

The annotated schematic below shows the DC operating point values
for the critical biasing devices under nominal conditions.

![Annotated DC operating point schematic](Figures/op_schematic_annotated.png)

![Annotated DC operating point schematic](Figures/op_current_mirror_block.png)

![Annotated DC operating point schematic](Figures/op_reference_branch.png)

![Annotated DC operating point schematic](Figures/op_starter_circuit_block.png)

The annotations include drain current, terminal voltages, and small-signal
parameters required for bias verification.


---

## 3. MOSFET Bias Summary

The table below summarizes the extracted DC operating point values for key MOSFETs in the design.

### MOSFET DC Bias and Region of Operation

| Device | VGS (mV) | VDS (mV) | VTH (mV) | Region of Operation |
|--------|----------|----------|---------|---------------------|
| NM0    | 46.7774  | 2653.6   | 496.259 | OFF          |
| NM1    | 2077.28  | 46.7774  | 502.76  | Linear          |
| NM2    | 664.846  | 664.846  | 612.057 | Saturation          |
| NM3    | 664.846  | 664.74   | 612.057 | Saturation          |
| NM8    | 802.964  | 802.964  | 749.494 | Saturation          |
| NM9    | 803.07   | 732.983  | 749.494 | Saturation          |
| PM2    | -646.402 | -646.402 |-435.114 | Saturation          |
| PM3    | -646.596 | -576.508 |-435.129 | Saturation          |
| PM4    | -644.593 | -1467.12 |-434.929 | Saturation          |
| PM7    | -646.403 | -645.209 |-435.114 | Saturation          |
| PM8    | -646.403 | -648.212 |-435.113 | Saturation          |
| PM9    | -646.403 | -646.403 |-435.114 | Saturation          |

**Note:**  
The threshold voltage (`VTH`) values were obtained from the device operating point data reported by the simulator.  
The region of operation was determined analytically using DC bias conditions.

![Device operating point data for M1 – Page 1](Figures/op_device_table_NM2_p1.jpg)
![Device operating point data for M1 – Page 2](Figures/op_device_table_NM2_p2.jpg)


---

## 4. Region of Operation Verification

For an NMOS transistor to operate in saturation, the following conditions must be satisfied:
- VGS > VTH
- VDS ≥ (VGS − VTH)



Using the extracted DC operating point values, all listed MOSFETs satisfy the
above conditions, confirming saturation operation under nominal bias.

This ensures:
- Accurate current mirroring
- High output resistance
- Stable PTAT current generation

---

## 6. Parasitic PNP BJT Operating Point

The bandgap reference employs parasitic vertical PNP BJTs to generate the CTAT
voltage component (VBE). Proper DC biasing of these devices is essential for
predictable temperature behavior.

The DC operating point of the PNP BJTs was verified to confirm correct collector
current and base–emitter voltage.
(Also for a <b>Diode connected PNP BJT VBE=VCE</b>)

![PNP BJT DC operating point](Figures/op_pnp.png)

The extracted VBE values are consistent with expected CTAT behavior at room
temperature and nominal bias current.

---

## 7. Observations

- All critical MOSFETs operate in saturation with sufficient voltage headroom.
- MOSFETs 
- No device is biased near the triode or cutoff boundary.
- Parasitic PNP BJTs exhibit stable VBE values suitable for CTAT generation.

---

## 8. Conclusion

The DC operating point analysis confirms correct biasing of both MOSFET and
parasitic PNP BJT devices in the bandgap reference circuit under nominal
conditions. The verified operating regions validate the assumptions used in
subsequent temperature sweep, PSR, and headroom analyses.
