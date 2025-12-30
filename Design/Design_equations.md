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

<p align="center"><img width="181" height="87" alt="image" src="https://github.com/user-attachments/assets/c16e9ffa-0256-4549-9e81-ef80a96f4848" />
</p>

For one diode in the parallel branch:

<p align="center"><img width="187" height="89" alt="image" src="https://github.com/user-attachments/assets/32091511-dcff-416e-9e0d-d71c7e128ddb" /></p>

### Difference of Diode Voltages (ΔV)
Subtracting the two branch voltages,
<p align="center"><img width="245" height="129" alt="image" src="https://github.com/user-attachments/assets/83f86ada-241d-4895-8894-477659c76068" />
</p>

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

### Extraction of PTAT component

<img width="1216" height="880" alt="current mirror block" src="https://github.com/user-attachments/assets/3aecb96b-684d-4c5c-a719-2889511c7fbc" />

Assuming NMOS transistors (M1) and (M2) are matched (same (W/L), same process) and operate in saturation. Ignoring channel-length modulation, the drain current for both is

<p align="center"><img width="389" height="134" alt="image" src="https://github.com/user-attachments/assets/a9d24237-73b9-4e3b-9a4b-8e5c70204b92" /></p>

This gives us,

<p align="center"><img width="137" height="43" alt="image" src="https://github.com/user-attachments/assets/aad84219-7925-4148-916d-30e798c28ab3" /></p>

Now, M1 is diode-connected, hence

<p align="center"><img width="137" height="50" alt="image" src="https://github.com/user-attachments/assets/0fdb7a5e-c306-4015-bc3d-5552b13bd186" /></p>

It is biased with a reference current I<sub>o</sub>:

<p align="center"><img width="331" height="61" alt="image" src="https://github.com/user-attachments/assets/3e45187b-aca5-4798-8bd5-2ac2b9f18b5a" /></p>

Also, the gates of M1 and M2 are connected so this equation uniquely fixes V<sub>GS1</sub> and V<sub>GS2</sub>.
Since both MOSFETs carry the same current and have identical VGS, their drain voltages adjust such that saturation is maintained. As a result,

<p align="center"><img width="94" height="37" alt="image" src="https://github.com/user-attachments/assets/717c2917-f7c3-4042-89e8-64c4f1ade959" /></p>

Now from circuit,

<p align="center"><img width="470" height="156" alt="image" src="https://github.com/user-attachments/assets/71f011b5-093f-4ca9-b1cb-ef0d5d4d28ed" /></p>

Now to use this PTAT current we need to isolate it which is done by mirroring Io using PMOS and pushing it through a resistor R<sub>2</sub> (For convenience we replace R by R<sub>1</sub>),

<p align="center"><img width="1536" height="1024" alt="PTAT extraction" src="https://github.com/user-attachments/assets/c24e0067-f6ee-44ba-aa0c-f72534fbfedc" /></p>

<p align="center"><img width="391" height="78" alt="image" src="https://github.com/user-attachments/assets/19ee9fed-09cb-432c-8640-f713ce59f368" /></p>

Here, V<sub>T</sub> is PTAT and let <img width="137" height="51" alt="image" src="https://github.com/user-attachments/assets/b3a9241f-6e66-40d5-926a-21fcad7e06ac" /> such that <img width="167" height="47" alt="image" src="https://github.com/user-attachments/assets/be217cee-af6d-46a3-8d35-900c4ef56dbb" />

And, <img width="238" height="66" alt="image" src="https://github.com/user-attachments/assets/e03d5e41-2a2c-4678-8a4a-60fd25277737" />

### Issues Left
#### Supply Variation
Supply variation is rejected by the current mirror used which in our case is cascode current mirror.

#### Current Through Diode (CTAT)
Earlier CTAT slope was given by,

<p align="center"><img width="339" height="71" alt="image" src="https://github.com/user-attachments/assets/a6c81ac2-be2f-4748-a85f-d4eac79e82dc" /></p>

was calculated by assuming that the current from the current mirror Io was constant but as we can see from equation (a) I<sub>o</sub> is not constant so calculating CTAT slope using I<sub>o</sub> from equation (a),

<p align="center"><img width="162" height="74" alt="image" src="https://github.com/user-attachments/assets/d7947bd6-ddf2-4909-b3eb-2c47165f0a90" /></p>

We know,

<p align="center"><img width="288" height="114" alt="image" src="https://github.com/user-attachments/assets/56945bef-971a-489a-8d32-1883e2d81a0d" /></p>

Differentiating V<sub>D</sub> partially w.r.t T,

<p align="center"><img width="527" height="79" alt="image" src="https://github.com/user-attachments/assets/6c5920af-a568-4802-ad67-245b8b7370bc" /></p>

Now, 

<p align="center"><img width="477" height="156" alt="image" src="https://github.com/user-attachments/assets/92bb0769-cade-4812-b4c7-9af0f8a1bddd" /></p>

Combining eq (d) and (e) into (c),

<p align="center"><img width="330" height="69" alt="image" src="https://github.com/user-attachments/assets/c2221e61-7d5d-4f25-9b3f-4bca73bad22f" /></p>

Plugging all the standard values used for CTAT calculation before,

<p align="center"><img width="224" height="67" alt="image" src="https://github.com/user-attachments/assets/efed4042-77b7-4d6c-a644-15ef21d7518e" /></p>

Which is also CTAT in nature hence I<sub>o</sub> being PTAT didn’t alter the nature of V<sub>D</sub>.

#### Scaling of CTAT and PTAT
Uptil now we extracted PTAT. To get VREF we have to scale both CTAT and PTAT and then add them. The reason for scaling is that CTAT and PTAT are not exactly equal in fact they differ vastly in magnitude so for constructing a stable VREF such that <img width="115" height="51" alt="image" src="https://github.com/user-attachments/assets/75378b46-501e-47aa-a778-ce1523550252" />, we must scale CTAT and PTAT such that,

<p align="center"><img width="373" height="43" alt="image" src="https://github.com/user-attachments/assets/901c4277-9eff-4fa8-bd6d-38f0ac212fab" /></p>

For this project we put <img width="69" height="36" alt="image" src="https://github.com/user-attachments/assets/8f312532-a53e-409a-aeee-a79e3909fccf" /> and from equation (b) <img width="131" height="53" alt="image" src="https://github.com/user-attachments/assets/85e109c6-7585-48bf-a65d-6b576b1db8fa" />,

<p align="center"><img width="332" height="110" alt="image" src="https://github.com/user-attachments/assets/fe9f597b-135d-4c33-b7ff-2ff681f4f7bd" /></p>

Putting <img width="200" height="68" alt="image" src="https://github.com/user-attachments/assets/fa9bd455-81e1-40ac-b169-befc781b6987" /> and <img width="222" height="49" alt="image" src="https://github.com/user-attachments/assets/63e9a2c4-a37b-49b3-845e-97883862f696" /> we get,

<p align="center"><img width="126" height="31" alt="image" src="https://github.com/user-attachments/assets/8950a6e0-58e1-4bf4-91cd-840ee0f9afbe" /></p>

For this project, <img width="99" height="30" alt="image" src="https://github.com/user-attachments/assets/986997e2-7f5d-4c4d-be0f-e870df1ab886" />, number of pnp bjt for PTAT block (n) = 5 at STP,

<p align="center"><img width="457" height="192" alt="image" src="https://github.com/user-attachments/assets/ec475b6e-4d0c-4058-8794-061356192de5" /></p>

### Practical Considerations
The resistor values derived in this section are based on first-order bandgap theory assuming ideal device behavior. In practice, second-order effects such as finite transistor output resistance, parasitic BJT behavior, and resistor mismatch introduce residual temperature dependence. Therefore, these theoretical values were used only as an initial reference, and the final resistor values were refined through iterative manual adjustment guided by temperature sweep simulations to reduce the overall variation of VREF.
























 






















