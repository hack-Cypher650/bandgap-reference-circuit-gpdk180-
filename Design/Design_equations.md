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

<img width="930" height="532" alt="image" src="https://github.com/user-attachments/assets/9d805689-e1de-45cc-9618-c17b918b28ec" />

This is <b>undesirable</b> when the goal is to realize a clean diode behavior.

#### Correct CMOS-Compatible Diode Implementation
To avoid substrate current leakage and suppress unintended BJT action, a well-isolated structure is used:
1. A p-well is first formed inside the p-substrate
   - The p-well is tied to ground (VSS).
   - This creates a controlled p-type region isolated from the substrate.
2. An n-well is then placed inside this p-well
   - The n-well is also tied to ground to avoid floating base effects.
3. p+ and n+ diffusions are added inside the n-well
   - The p+ diffusion is connected to the required signal node.
   -The n+ diffusion is tied to ground along with the n-well.

<img width="1066" height="601" alt="image" src="https://github.com/user-attachments/assets/291e2d49-eda0-40d5-813c-e7f3d50cb7a6" />


#### Resulting Electrical Behavior
This structure achieves:
- A well-defined p+–n-well PN junction, acting as the intended diode.
- Suppression of substrate current due to well isolation.
- A controlled parasitic diode-connected PNP BJT, where:
  - The base (n-well) and collector (p-well/substrate) are both grounded.
  - BJT gain is minimized.
  - The device behaves predominantly as a diode.
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b939ef13-2a75-40e0-87ab-3d1783e1c5f2" />
This approach is widely used in bandgap references, bias generators, and protection structures, where predictable diode behavior is required within a pure CMOS process.

---

## PTAT DESIGN
### Diode / BJT Current Voltage Relation
For a diode‑connected BJT (or PN junction diode) operating in forward active region, the collector (or diode) current is

<p align="center"><img width="182" height="67" alt="image" src="https://github.com/user-attachments/assets/28540a87-3e53-4486-8654-7d435274b34c" /></p>

where: - I<sub>S</sub> = saturation current; V<sub>D</sub> = diode voltage; V<sub>T</sub> =  kT/q = thermal voltage
Rearranging,

<p align="center"><img width="200" height="73" alt="image" src="https://github.com/user-attachments/assets/c762b2a3-94c1-46f7-9860-ffbd7d5c7478" /></p>

This voltage exhibits CTAT behavior due to the temperature dependence of (I<sub>S</sub>).

### One Diode vs n Identical Diodes in Parallel
Consider two branches biased with the same total current (I):
- <b>Branch 1:</b> a single diode
- <b>Branch 2:</b> (n) identical diodes connected in parallel
All diodes are assumed to be perfectly matched, each having the same saturation current (I<sub>S</sub>).

<p align="center"><img width="505" height="337" alt="image" src="https://github.com/user-attachments/assets/d9243867-d8eb-4d3b-bbac-62f54eb6b7a9" /></p>

### Current Distribution in Parallel Diodes
In the parallel branch, the total current divides equally among the diodes:

<p align="center"><img width="86" height="72" alt="image" src="https://github.com/user-attachments/assets/69dabaf2-5476-43ec-b690-f29c5c1211aa" /></p>

All parallel diodes share the same voltage, denoted V<sub>2</sub>.

### Diode Voltages
For the single-diode branch:

<p align="center"><img width="186" height="91" alt="image" src="https://github.com/user-attachments/assets/89c319c7-5059-4445-9ccb-8138320ea017" /></p>

For one diode in the parallel branch:

<p align="center"><img width="187" height="89" alt="image" src="https://github.com/user-attachments/assets/32091511-dcff-416e-9e0d-d71c7e128ddb" /></p>

### Difference of Diode Voltages (ΔV)
Subtracting the two branch voltages,
<p align="center"><img width="250" height="139" alt="image" src="https://github.com/user-attachments/assets/6ca4f6e1-cb4c-4a03-96cd-2595c32f3b80" /></p>

Using logarithmic identities,

<p align="center"><img width="211" height="55" alt="image" src="https://github.com/user-attachments/assets/af0a413e-2391-4989-999b-fa444048468b" /></p>

### PTAT Nature of ΔV
Since

<p align="center"><img width="140" height="89" alt="image" src="https://github.com/user-attachments/assets/f11842bc-3d26-4e24-bdbd-ef6eeed5142f" /></p>

we obtain,

<p align="center"><img width="233" height="93" alt="image" src="https://github.com/user-attachments/assets/79e63dcf-1bfa-4845-b0e3-7e569614025c" /></p>

This voltage is <b>directly proportional to absolute temperature (PTAT)</b>.

### Generating PTAT Current
In a practical bandgap reference, (V<sub>D</sub>) is forced across a resistor (R):

<p align="center"><img width="326" height="92" alt="image" src="https://github.com/user-attachments/assets/eaddc85f-7cff-4437-9155-01de18519321" /></p>

<p align="center"><img width="575" height="383" alt="image" src="https://github.com/user-attachments/assets/41bf3aef-7e3a-4234-a6b5-8a4374e31bd6" /></p>

This PTAT current is mirrored and combined with a CTAT voltage (V<sub>D</sub>≈V<sub>BE</sub>) to generate a temperature‑independent bandgap reference voltage.

---

## Current Mirror Implementation


















 






















