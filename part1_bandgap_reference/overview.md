This section documents the design and analysis of a BJT-based bandgap reference (BGR) implemented in the gpdk180 CMOS process. The bandgap serves as a stable on-chip voltage and current reference intended for biasing analog circuit blocks rather than achieving production-grade precision.

The core of the bandgap reference utilizes parasitic vertical BJTs available in the CMOS process to generate complementary temperature-dependent voltages. A CTAT component derived from the base–emitter voltage ​is VD combined with a PTAT component generated from the difference in base–emitter voltages​ V2 of BJTs operating at different current densities. Proper scaling of these components results in a temperature-compensated reference voltage.

Bias currents within the bandgap are generated using MOS current mirrors. A startup circuit is included to eliminate the undesired zero-current operating point and ensure reliable turn-on during power-up. Once normal bias conditions are established, the startup path becomes inactive and does not affect steady-state operation.

The design prioritizes bias stability, robustness, and clarity of operation over aggressive optimization. Key analyses performed include DC operating point verification, temperature sweep, power supply rejection ratio (PSRR) evaluation, and supply headroom analysis. The resulting bandgap reference is subsequently reused as the bias source for a MOS differential amplifier in the second part of the project.

This implementation is intended as a learning-focused exploration of bandgap fundamentals, startup behavior, and system-level reuse in a mature CMOS technology.
