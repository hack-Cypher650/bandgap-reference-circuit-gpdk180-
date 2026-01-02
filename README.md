# CMOS Bandgap Reference (BGR) Circuit Design

## Table of Contents
1. [Overview](#overview)
2. [Key Specifications](#key-specifications)
3. [Architecture](#architecture)
4. [Design Methodology](#design-methodology)
5. [Analysis and Verification](#analysis-and-verification)
6. [Layout Considerations](#layout-considerations)
7. [Design Trade-offs](#design-trade-offs)
8. [Simulation Environment](#simulation-environment)
9. [Results Summary](#results-summary)
10. [Future Improvements](#future-improvements)
11. [References](#references)

---

## Overview

This project presents the design and verification of a **CMOS Bandgap Reference (BGR)** circuit implemented using **parasitic vertical PNP BJTs** and **MOS current mirrors**.  
The objective is to generate a **temperature-stable reference voltage** suitable for on-chip biasing in analog and mixed-signal ICs.

The design emphasizes:
- First-order temperature compensation using **PTAT–CTAT summation**
- Robust biasing and startup behavior
- Layout-aware architectural decisions
- Thorough simulation-based validation

This is a **student-driven analog IC design project**, documented with industry-style rigor.

---

## Key Specifications

| Parameter | Value |
|---------|------|
| Technology | CMOS with parasitic PNP BJTs |
| Supply Voltage | 3.3 V |
| Target VREF | ~1.1–1.2 V |
| Temperature Range | −40°C to 125°C |
| Reference Type | Current-mode bandgap |
| Compensation | First-order PTAT–CTAT |

---

## Architecture

The bandgap reference follows a **current-mode topology**:

- **CTAT generation** using diode-connected parasitic PNP BJTs
- **PTAT generation** via ΔV_BE across resistor networks
- **MOS current mirrors** for current replication and summation
- **Cascode mirrors** employed to improve PSR and bias stability
- Dedicated **startup circuit** to guarantee correct operating point

Architectural decisions were made with layout and headroom constraints in mind.

Detailed architectural diagrams and explanations are provided in:

[Architecture.md](Design/Architecture.md)

---

## Design Methodology

1. Analytical derivation of PTAT and CTAT components
2. Selection of resistor ratios to achieve first-order temperature cancellation
3. Manual trimming and fine-tuning of resistor values
4. Verification through DC, transient, and temperature simulations
5. Iterative refinement based on simulation results

Design equations and derivations are documented in:

[Design_equations.md](Design/Design_equations.md)

---

## Analysis and Verification

The design was validated using multiple simulation analyses:

- **DC Operating Point Analysis**  
  Ensures all MOSFETs operate in saturation and BJTs in forward-active region.

- **Temperature Sweep Analysis**  
  Confirms temperature stability of VREF across the specified range.

- **Startup Verification**  
  Demonstrates correct convergence with and without startup circuitry.

- **Headroom Analysis**  
  Determines minimum supply voltage for regulation.

- **PSR Analysis**  
  Evaluates sensitivity of VREF to supply variations.

All plots and observations are documented under:

[Analysis/](Analysis/)

---

## Layout Considerations

Although the project is primarily schematic-focused, layout-aware decisions were incorporated:

- Physical layout implemented for the bandgap core
- Emphasis on symmetry and device grouping for matched elements
- No post-layout extraction or parasitic-aware re-simulation performed

Layout-related documentation is available in:

[Layout/Layout_Considerations.md](Layout/layout_considerations.md)

---

## Design Trade-offs

Several trade-offs were evaluated during the design process:

- **PSR vs headroom trade-off** arising from the use of cascode current mirrors, where improved supply rejection is achieved at the cost of reduced low-voltage operability

- **Cascode current mirrors vs simple mirrors**, evaluated in terms of bias stability, output resistance, and implementation complexity

- **Layout complexity vs matching accuracy**, where improved device matching and symmetry in the bandgap core layout increase layout effort and area, but enhance robustness against mismatch

- **Startup circuit robustness vs steady-state simplicity**, where additional circuitry is introduced to guarantee correct startup at the cost of increased schematic complexity and potential leakage paths under steady-state operation


These trade-offs, along with supporting simulation evidence, are documented in:

[Design/design_tradeoffs.md](Design/design_tradeoffs.md)

---

## Simulation Environment

- Tool: **Cadence Virtuoso (IC 6.1.5)**
- Simulator: **Spectre**
- Operating System: Linux (RHEL/CentOS based)

All simulations were performed using schematic-level testbenches.

---

## Results Summary

- Stable VREF around **1.1–1.2 V**
- Low temperature variation after manual trimming
- Correct startup behavior
- All core devices biased in intended operating regions
- Acceptable PSR and headroom performance for the chosen topology

---

## Future Improvements

- Curvature compensation
- Post-layout extraction and re-verification
- Trimming strategy for process variation
- Monte Carlo mismatch analysis
- Fully custom layout with guard rings

---

## References

- Gray, Meyer et al., *Analysis and Design of Analog Integrated Circuits*
- Razavi, *Design of Analog CMOS Integrated Circuits*
- Baker, *CMOS Circuit Design, Layout, and Simulation*



