# DESIGN EQUATIONS USED
## CTAT DESIGN
<img width="167" height="249" alt="image" src="https://github.com/user-attachments/assets/21b640d1-acad-4698-be02-89ea59acf7ed" />



I<sub>o</sub> = constant

![Io_1](https://github.com/user-attachments/assets/d5debeb3-165f-4e74-b02f-41c3b33eecf3)


### Fabrication of Ground-Referenced Diodes in a CMOS Process
In standard CMOS technologies, explicit discrete diodes are not available. Instead, diodes are realized using parasitic PN junctions formed between doped regions and wells or the substrate. A common requirement in analog circuits is a diode whose n-side is tied to ground and whose p-side is connected to a signal node, for example in biasing or reference-generation circuits.

#### Basic CMOS Substrate Context
- The substrate is typically p-type and is tied to ground (VSS).
- n-wells are used to host PMOS devices and p+ diffusions.
- p+ and n+ diffusions form junctions with the surrounding well or substrate.

<img width="949" height="614" alt="image" src="https://github.com/user-attachments/assets/eb781ab2-efdd-4871-8291-2035a8031fd6" />


#### Problem with Simple p+ and n+ in an n-Well
If we simply place both p+ and n+ diffusions inside an n-well, with the p-substrate grounded, the structure unintentionally behaves like a <b>parasitic vertical PNP BJT</b>:
- <b>Emitter</b>: p+ diffusion
- <b>Base</b>: n-well
- <b>Collector</b>: p-substrate

When current is injected through the p+ region:
- The p+–n-well junction forward-biases.
- Minority carriers are injected into the n-well.
- These carriers are collected by the grounded p-substrate.

As a result:
- A significant portion of current flows into the substrate rather than through the intended diode path.
- This substrate current is essentially <b>BJT action</b>, not diode conduction.
- The structure exhibits poor control, leakage, and unintended gain effects.

This is <b>undesirable</b> when the goal is to realize a clean diode behavior.









