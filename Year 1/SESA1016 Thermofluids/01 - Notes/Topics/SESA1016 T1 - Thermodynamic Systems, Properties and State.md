---
title: "SESA1016 T1 - Thermodynamic Systems, Properties and State"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 1
tags: [sesa1016, thermodynamics, ideal-gas, state]
aliases: ["Thermodynamic Systems and State"]
date: 2026-09-25
status: lectured
coverage: "Lecture 1 (27 Jan 2025, L1 ll. 319–636: systems, properties, continuum, equilibrium); Chapter 1 §§1.4–1.6 (state postulate, ideal-gas law, processes) from the notes only, as the following lecture was not recorded"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: []
next_topics: ["[[SESA1016 T2 - Work, Heat and the First Law]]"]
key_concepts: ["[[Closed System vs Control Volume]]", "[[Thermodynamic State and Process]]", "[[Ideal-gas Law]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/SESA1016 Lecture 1.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 01 - Basic Concepts.pdf"]
---

# SESA1016 T1 - Thermodynamic Systems, Properties and State

> [!abstract] Summary
> Every thermodynamic analysis starts by drawing a boundary round the thing being studied: a closed system holds a fixed mass, a control volume is a fixed region that mass flows through. Inside the boundary the gas has properties (intensive, extensive or specific), and once the gas is in equilibrium two independent intensive properties fix its state. For a gas the link between them is the ideal-gas law $pV=mRT$, which must be used with absolute pressure and kelvin.

> [!summary]- Exam use: quick path
> - **Use it when:** a fixed mass of gas changes from one equilibrium state to another (heated in a rigid tank, compressed by a piston, connected to a second tank) and you need $p$, $V$, $T$ or $m$ at the end.
> - **Assumptions:** ideal gas (moderate pressure, well above the boiling point), continuum, both end states in equilibrium, fixed mass unless gas is added.
> - **Method:** 1. Draw the boundary and decide what stays constant ($m$, $V$, $T$ or $p$). 2. Convert to SI with absolute pressure and kelvin. 3. Write $pV=mRT$ for each state (or each tank). 4. Cancel the constants (often $mR$, or $RT$) and solve. 5. Check the result against intuition (heated rigid tank: $p$ rises in proportion to $T$).
> - **Common mistakes:** using °C or gauge pressure in $pV=mRT$; using the universal constant $R_u=8.3145$ J mol⁻¹ K⁻¹ where the specific constant $R$ in J kg⁻¹ K⁻¹ is needed.
> - **Practise:** [[#Worked example - two connected tanks]] · [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]] Q1.2–Q1.5

Thermodynamics is about energy: how it is stored, how it moves from one form to another and how much useful work can be extracted when it does. That applies to everything, so the analysis starts with the simplest substance that shows all the effects, a gas in a box. The air in a room is already too complicated (it is warmer in some places than others, and people open doors), so the first step is to put an imaginary boundary round a definite piece of gas and agree what is allowed to cross it.

If gas flows in and out, as through the nozzle of a jet engine, the boundary encloses a control volume. If nothing crosses, as with gas trapped under a piston, it encloses a closed system. The closed system has the simpler energy accounting and is treated first; the control volume is used in the fluids half ([[SESA1016 T11 - Conservation of Mass|T11]]–[[SESA1016 T13 - Conservation of Energy and Propulsion|T13]]).

Once the boundary is drawn, the gas inside is described by properties such as pressure, temperature, volume and mass. Those properties only mean something if there are enough molecules to average over (the continuum assumption) and if the gas has settled down to uniform values (equilibrium). With both in place, two numbers are enough to fix the state, and an equation of state such as the ideal-gas law gives every other property from those two.

---

## 1. Closed systems and control volumes

A **control volume** has a boundary fixed in space, and mass may cross it. A nozzle is the standard example: gas enters on one side and leaves on the other, and the analysis tracks what is carried across the boundary. A **closed system** has a boundary that mass cannot cross, so the amount of gas inside is constant. The boundary of a closed system is not necessarily fixed: the gas in a cylinder closed by a piston is a closed system even while the piston moves and the volume changes. In practice a closed system is often just called a system.

Energy can still cross the boundary of a closed system, either as heat through the cylinder wall or as work done on or by the piston. If energy cannot cross either, the system is an **isolated system**.

![[tf_system_types.png|900]]

| Model | Boundary | Mass crosses? | Energy crosses? | Example |
|---|---|---|---|---|
| Control volume | usually fixed in space | yes | yes | nozzle, turbine, pipe junction |
| Closed system | may move or deform | no | yes, as heat or work | gas under a piston |
| Isolated system | closed | no | no | an ideal insulated rigid vessel |

The choice decides which energy terms appear. For a closed system, energy crosses only as heat or work. For a control volume, each kilogram of gas crossing the boundary also carries its own internal, kinetic and potential energy, and pushing it across takes work; that is why the control-volume energy equation in [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]] contains enthalpy rather than internal energy. See [[Closed System vs Control Volume]].

## 2. Intensive, extensive and specific properties

Any characteristic of a system is a **property**: pressure $p$, temperature $T$, volume $V$, mass $m$, density $\rho$, and later internal energy $U$, enthalpy $H$ and entropy $S$. Properties come in two kinds.

An **intensive** property does not depend on the amount of material: one kilogram of air at 20 °C and two kilograms of the same air are both at 20 °C. Pressure, temperature and density are intensive. An **extensive** property does depend on the amount: double the gas and the mass and volume double. Mass, volume and energy are extensive.

When it is not obvious which kind a property is, a partition through the middle of a uniform system settles it. Each half keeps the original $p$, $T$ and $\rho$, but has half the original $V$, $m$ and energy. Whatever is unchanged is intensive; whatever halves is extensive.

A **specific** property is an extensive property divided by the mass. The first example is specific volume,

$$
v=\frac{V}{m}
$$

which is the reciprocal of density, $v=1/\rho$. Applied to the partition test, each half has volume $V/2$ and mass $m/2$, so

$$
v_{half}=\frac{V/2}{m/2}=\frac{V}{m}=v
$$

and a specific property is therefore intensive. The same works for energy: 10 J in 1 kg is 10 J/kg, and after partitioning, 5 J in 0.5 kg is still 10 J/kg. Specific properties are useful when the mass is not known, and they let one equation serve any amount of gas.

The notation follows a convention: capitals for extensive properties ($V$, $U$, $H$, $S$), lower case for the specific versions ($v$, $u$, $h$, $s$). Temperature $T$ and mass $m$ are the two exceptions.

## 3. The continuum assumption

Gas is made of molecules, so a property such as density is only meaningful as an average over a volume containing many of them. Shrinking a sampling box shows this. When it is large, adding or losing one molecule as the box changes size makes no visible difference, and the computed density settles at a single value. When it is so small that it holds only a few molecules, the count jumps between zero, one and two as the box grows, and the computed density jumps with it.

![[tf_continuum_density.png|900]]

The **continuum assumption** treats the material as continuous, with no holes, so that $p$, $T$ and $\rho$ can be defined at every point as smooth fields. It holds when the system is much larger than the **mean free path**, the distance a molecule travels between collisions. For air at 1 atm and 20 °C the mean free path is about $0.7\times10^{-7}$ m, so the continuum model works for anything much bigger than about a micrometre.

> [!check] How many molecules does a small sample hold?
> The number density of an ideal gas is $n=p/(k_BT)$ with $k_B=1.381\times10^{-23}$ J/K. For air at $10^5$ Pa and 293 K, $n=2.47\times10^{25}$ m⁻³. A cube of side 1 µm then holds about $2.5\times10^7$ molecules, plenty to average over; a cube of side 10 nm holds about 25, and the density computed from it would jump by several per cent each time one molecule entered or left.

The assumption fails in two places that matter later: micro-scale devices, where the system size approaches the mean free path, and the upper atmosphere, where the mean free path grows as the density falls. A spacecraft in orbit flies through gas so thin that standard continuum aerodynamics cannot be used to compute its drag. Everything in this module assumes a continuum.

## 4. State, equilibrium and the state postulate

The **state** of a system is defined when a set of properties fully describes its condition. That needs **equilibrium**. If one part of a container is at 20 °C and another at 30 °C, there is no single temperature to quote, so the state is undefined. Left alone, heat flows from the warm region to the cool one until the whole container is at one temperature, and once every property has stopped changing the system is in equilibrium.

Equilibrium has several parts. Thermal equilibrium means no temperature differences to drive heat transfer; mechanical equilibrium means no unbalanced pressure forces; phase and chemical equilibrium mean no spontaneous change of phase or composition. A system in all of them is in **thermodynamic equilibrium**.

Temperature alone does not fix the state: gas at 25 °C can be at any pressure. The number of properties needed is given by the **state postulate**:

> The state of a simple compressible system is completely specified by two independent, intensive properties.

Both conditions matter. The properties must be intensive: knowing $p$ and $V$ does not give $T$ unless the mass is also known, since it is the specific volume $v=V/m$ that enters the equation of state. They must also be independent: $v$ and $\rho$ are not, because $\rho=1/v$, so knowing both is really knowing one.

## 5. The ideal-gas law

### Three forms of the law

The ideal-gas law is the simplest equation of state that describes a gas accurately over a practical range. It grew out of two experimental observations: at fixed temperature the pressure is inversely proportional to the volume, and at fixed volume the pressure is proportional to the absolute temperature. Combined, for a mass $m$,

$$
\boxed{pV=mRT}
$$

where $R$ is the **specific gas constant**, different for each gas. Divide both sides by $m$ and use $v=V/m$:

$$
p\frac{V}{m}=RT
$$

$$
pv=RT
$$

Alternatively divide $pV=mRT$ by $V$ and use $\rho=m/V$:

$$
p=\frac{m}{V}RT
$$

$$
p=\rho RT
$$

All three forms are the same law. Use whichever matches the data: $pV=mRT$ when a mass and a volume are given, $p=\rho RT$ for the atmosphere.

### Specific and universal gas constants

Chemistry writes the law per mole, $pV=nR_uT$, with the **universal gas constant** $R_u=8.3145$ J mol⁻¹ K⁻¹ and $n$ the number of moles. The amount of gas in moles and in kilograms are linked by the molar mass $M$, so $m=nM$. Substitute $n=m/M$:

$$
pV=\frac{m}{M}R_uT
$$

and compare with $pV=mRT$:

$$
R=\frac{R_u}{M}
$$

| Gas | $M$ (kg/mol) | $R=R_u/M$ (J kg⁻¹ K⁻¹) |
|---|---|---|
| Air | 0.02897 | 287 |
| N₂ | 0.02801 | 297 |
| O₂ | 0.03200 | 260 |
| H₂ | 0.002016 | 4124 (Table 1.1 rounds to 4120) |
| CO₂ | 0.04401 | 188.9 |

The mass form with $R$ is used throughout. The two constants are easy to confuse when looking values up, because the names and symbols vary between sources; the units settle it, since the universal constant is per mole or per kilomole and the specific constant is per kilogram.

### Units, absolute temperature and absolute pressure

The ideal-gas law needs consistent SI units: $T$ in kelvin, $m$ in kg, $p$ in Pa, $V$ in m³ and $R$ in J kg⁻¹ K⁻¹. Two conversions cause most of the errors.

Temperature must be absolute. Zero degrees Celsius is just the freezing point of water and has no special meaning for a gas, whereas 0 K is the temperature at which the molecules have no kinetic energy left. The conversion is

$$
T\,[\mathrm K]=T\,[^\circ\mathrm C]+273.15
$$

and temperature differences are the same on both scales. Write kelvin as K, not °K.

Pressure is the average force per unit area that the molecules exert on a surface, measured in pascals (1 Pa = 1 N m⁻²). The other common units are

$$
1\ \mathrm{bar}=100\ \mathrm{kPa}=10^5\ \mathrm{Pa},\qquad 1\ \mathrm{atm}=101\,325\ \mathrm{Pa}
$$

One atmosphere is a fixed standard value; the atmospheric pressure on a given day is whatever the local air pressure is, and 1 bar is often used as a round approximation to it. The ideal-gas law needs **absolute pressure**, measured from a perfect vacuum. Many gauges, such as a tyre gauge or the Pitot-static system on an aircraft, read **gauge pressure**, the difference from the local atmosphere:

$$
p_g=p_{abs}-p_{atm}
$$

A flat tyre reads 0 bar gauge, which means its absolute pressure equals the atmospheric pressure, not that it is a vacuum.

### Fixed mass between two states

For a closed system the mass is constant, so write the law for state 1 and state 2 and rearrange each for $mR$:

$$
mR=\frac{p_1V_1}{T_1}
$$

$$
mR=\frac{p_2V_2}{T_2}
$$

Equate them:

$$
\boxed{\frac{p_1V_1}{T_1}=\frac{p_2V_2}{T_2}}
$$

The ratio form removes the need to know $m$ or $R$, but not the need for absolute $p$ and $T$: the ratio $p_2/p_1$ is different in gauge and absolute pressure, and $T_2/T_1$ is different in °C and K. In a rigid container $V_1=V_2$, and the result reduces to $p_2/p_1=T_2/T_1$.

### Pressure set by a free piston

When gas is held under a frictionless piston of area $A$, with the atmosphere above and a load $F_L$ (including the piston's own weight) pressing down, the piston is in equilibrium when the forces on it balance. Taking upward as positive:

$$
p_{gas}A-p_{atm}A-F_L=0
$$

$$
p_{gas}=p_{atm}+\frac{F_L}{A}
$$

The gas pressure is fixed by the load, whatever the volume. Heating gas under a free piston with a constant load is therefore a constant-pressure process. If the piston reaches a stop, the volume becomes fixed instead and further heating raises the pressure.

### Why it is called ideal, and when it fails

The law can also be derived from a model gas of tiny particles that are point masses with no volume, collide perfectly elastically with each other and with the walls, carry only translational kinetic energy and exert no forces on each other apart from collisions. A short version of that derivation shows where the assumptions enter. A cube of side $L$ holds $N$ particles of mass $m_p$. A particle with $x$-velocity $c_x$ that bounces elastically off the wall at $x=L$ reverses its $x$-momentum, so each impact transfers

$$
\Delta(\text{momentum})=2m_pc_x
$$

It returns to the same wall after travelling $2L$, a time $2L/c_x$, so the average force it exerts on the wall is

$$
F_1=\frac{2m_pc_x}{2L/c_x}=\frac{m_pc_x^2}{L}
$$

Sum over all $N$ particles and divide by the wall area $L^2$:

$$
p=\frac{\sum m_pc_x^2}{L^3}=\frac{Nm_p\overline{c_x^2}}{V}
$$

The motion is random, so $\overline{c_x^2}=\overline{c_y^2}=\overline{c_z^2}=\overline{c^2}/3$:

$$
pV=\tfrac13Nm_p\overline{c^2}
$$

Temperature measures the mean translational kinetic energy, $\tfrac12m_p\overline{c^2}=\tfrac32k_BT$, so $m_p\overline{c^2}=3k_BT$ and

$$
pV=Nk_BT
$$

With $N=m/m_p$ and $k_B/m_p=R$ this is $pV=mRT$. The assumptions show where the law fails: when molecules are packed closely (high pressure or density) their own volume and their mutual attraction matter, and near condensation the attraction dominates.

The law is nevertheless very accurate for gases at ordinary conditions. For air at 300 K and 1 bar it gives $\rho=10^5/(287\times300)=1.1614$ kg/m³ against a measured 1.1616 kg/m³, a 0.01 % difference. For 1 kg of air at 1 bar the error stays below 1 % down to about 150 K, becomes noticeable near 100 K and fails completely at the boiling point of air (about 80 K), where the real volume drops by a factor of several hundred as the air liquefies. In this module every gas is treated as ideal.

## 6. Processes and state diagrams

A **process** takes the system from one equilibrium state to another. Air in a cylinder at 1 bar and 25 °C (state 1), compressed by pushing the piston down while the temperature stays at 25 °C, ends at 2 bar with half the volume (state 2), because at fixed $m$ and $T$ the ratio form gives $p_1V_1=p_2V_2$. Plotting $p$ against $V$ marks each state as a point, and the process as a line between them. This is a **state diagram**, here a $p$–$V$ diagram.

![[tf_state_paths.png|900]]

The line drawn between two states is the **process path**, and it is only one of infinitely many paths between the same end points. Drawing it at all assumes that every point along it is a well-defined state, that is, that the system is in equilibrium at every instant. A process that satisfies this is a **quasi-equilibrium process**: the change happens slowly enough (the piston is pushed down slowly) that the gas always stays close to equilibrium. Real processes never quite manage this, but it is usually a good approximation, and the module assumes it throughout. A sudden expansion into a vacuum is the clearest counter-example, because the gas is far from uniform while it rushes into the empty space (Problem Sheet 1, Q1.4b).

Properties and the quantities exchanged during a process are different kinds of quantity ([[SESA1016 T2 - Work, Heat and the First Law|T2]]). $p$, $V$, $T$, $U$, $H$ and $S$ are properties and depend only on the state. Heat $Q$ and work $W$ are transfers across the boundary during a process; a system does not contain heat or work, and how much of each crosses depends on the path.

---

## Worked examples

### Worked example - mass of air in a container

Air is kept in a 10.0 litre container at 1.00 bar and 20.0 °C. Find the mass of air (Chapter 1, §1.5).

Convert to SI:

$$
p=1.00\ \mathrm{bar}=1.00\times10^5\ \mathrm{Pa},\qquad V=10.0\ \mathrm L=1.00\times10^{-2}\ \mathrm{m^3},\qquad T=293.15\ \mathrm K
$$

Rearrange $pV=mRT$ for $m$:

$$
m=\frac{pV}{RT}
$$

$$
m=\frac{1.00\times10^5\times1.00\times10^{-2}}{287\times293.15}
$$

$$
m=0.0119\ \mathrm{kg}
$$

> [!check] Order of magnitude
> Air at room conditions has a density of about 1.2 kg/m³, so 10 litres should hold about 0.012 kg, as found.

### Worked example - two connected tanks

A 5 L tank at 1.5 bar (absolute) is joined by a thin tube and a closed valve to a tank of unknown volume $V_B$ at 1.0 bar. Both are at the surrounding temperature of 20 °C. The valve is opened and the system returns to 20 °C, when the pressure is 1.2 bar. Find $V_B$ (Problem Sheet 1, Q1.1, the tutorial problem).

Take both tanks together as one closed system. No gas leaves, so the total mass is conserved:

$$
m_A+m_B=m_f
$$

Write each mass with the ideal-gas law, $m=pV/(RT)$. All three states are at the same $T$ and contain the same gas, so $RT$ is common:

$$
\frac{p_AV_A}{RT}+\frac{p_BV_B}{RT}=\frac{p_f(V_A+V_B)}{RT}
$$

Multiply through by $RT$:

$$
p_AV_A+p_BV_B=p_f(V_A+V_B)
$$

Collect the $V_B$ terms:

$$
V_B(p_B-p_f)=V_A(p_f-p_A)
$$

$$
V_B=V_A\frac{p_A-p_f}{p_f-p_B}
$$

Substitute; the units of pressure and volume cancel, so bar and litres can be kept:

$$
V_B=5\times\frac{1.5-1.2}{1.2-1.0}=5\times\frac{0.3}{0.2}=7.5\ \mathrm L
$$

The tube volume is neglected. In this particular problem gauge pressures happen to give the same answer: replacing every $p$ by $p_g+p_{atm}$ adds $p_{atm}V_A+p_{atm}V_B$ to the left-hand side and $p_{atm}(V_A+V_B)$ to the right, which cancel because the total volume does not change. That cancellation is special to a mass balance at fixed total volume and fixed temperature. A ratio such as $p_2/p_1=T_2/T_1$ is not invariant under the shift, so the safe habit is to convert to absolute pressure every time.

### Worked example - heated rigid container with added gas

A sealed rigid 2.5 L container holds 4.4 g of CO₂ at 300 K. It is heated to 450 K, then a further 2.2 g of CO₂ is added at 450 K. Find the three pressures (Problem Sheet 1, Q1.2, the sheet's worked solution). For CO₂, $R=R_u/M=8.3145/0.04401=188.9$ J kg⁻¹ K⁻¹.

Initial pressure:

$$
p_1=\frac{m_1RT_1}{V}=\frac{4.4\times10^{-3}\times188.9\times300}{2.5\times10^{-3}}=99.74\ \mathrm{kPa}
$$

After heating at fixed $m$ and $V$, the ratio form gives $p_2/p_1=T_2/T_1$:

$$
p_2=99.74\times\frac{450}{300}=149.6\ \mathrm{kPa}
$$

After adding gas at fixed $V$ and $T$, $p\propto m$, and the mass rises from 4.4 g to 6.6 g:

$$
p_3=149.6\times\frac{6.6}{4.4}=224.4\ \mathrm{kPa}
$$

The sheet prints 99.75 kPa for the first pressure; the product $4.4\times10^{-3}\times188.9\times300/2.5\times10^{-3}$ is 99 739 Pa, so 99.74 kPa is the correctly rounded value. The other two answers agree.

### Worked example - gauge pressure in a heated tyre

A tyre is inflated to 2.2 bar gauge at 15 °C, where the atmosphere is 1.013 bar. After driving, the air inside reaches 45 °C. Treating the tyre as rigid, what does the gauge read? (Suggested example built on §1.5.1.)

Convert to absolute: $p_1=2.2+1.013=3.213$ bar, $T_1=288.15$ K, $T_2=318.15$ K. At fixed $m$ and $V$:

$$
p_2=p_1\frac{T_2}{T_1}=3.213\times\frac{318.15}{288.15}=3.548\ \mathrm{bar\ (absolute)}
$$

$$
p_{g,2}=3.548-1.013=2.53\ \mathrm{bar\ (gauge)}
$$

Using gauge pressure directly in the ratio would give $2.2\times318.15/288.15=2.43$ bar, an error of 0.1 bar, and using °C would give $2.2\times45/15=6.6$ bar, which is absurd.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Next: [[SESA1016 T2 - Work, Heat and the First Law]]
- Concepts: [[Closed System vs Control Volume]] · [[Thermodynamic State and Process]] · [[Ideal-gas Law]]
- Worked sheet: [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T8 - Hydrostatics|T8]] (gauge and absolute pressure, $p=\rho RT$ in the atmosphere) · [[SESA1016 T11 - Conservation of Mass|T11]] (control volumes) · [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] (state postulate and perfect gas in Propulsion)

## Sources

- `Chapter 1.pdf`: lecture notes Chapter 1, Introduction and basic concepts, §§1.1–1.6, Table 1.1, Figs 1.1–1.7.
- `SESA1016 Lecture 1.txt` (27 Jan 2025, cited as L1): module introduction (ll. 1–318), then systems, properties, the continuum and equilibrium (ll. 319–636). The lecture stops at equilibrium; the state postulate, ideal-gas law and processes were scheduled for the next day's lecture, which has no recording.
- `Problem Sheet 01 - Basic Concepts.pdf`: Q1.1–Q1.5 with printed answers and the worked solution to Q1.2.

## Self-study tasks

The weekly problem sheet is the set work, with one problem taken in the tutorial and one given a full worked solution (L1, ll. 204–230). Attempt each closed-book, then check against the linked section.

### Core

- [ ] Q1.1, unknown tank volume (Problem Sheet 1, the tutorial problem). Target 7.5 L. → [[#Worked example - two connected tanks]]
- [ ] Q1.2, rigid CO₂ container (Problem Sheet 1, worked solution). Targets 99.74, 149.6, 224.4 kPa. → [[#Worked example - heated rigid container with added gas]]
- [ ] Q1.3, density of air at sea level and 5000 m, and a balloon's volume change. Targets 1.225 kg/m³, 0.735 kg/m³, 1.67 m³. → [[#Three forms of the law]] · [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]]
- [ ] Q1.4, gas expanding into a vacuum behind a free piston, then reheated; was it quasi-equilibrium? Target 3519 K, no. → [[#6. Processes and state diagrams]] · [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]]
- [ ] Q1.5, two isothermal gases separated by a free piston. Targets 1.67 bar, 0.0024 and 0.0006 m³. → [[#Pressure set by a free piston]] · [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]]

### Further practice

- [ ] Use the partition test to classify $p$, $T$, $\rho$, $V$, $m$, $U$, $u$ and $v$ (L1, ll. 478–492). → [[#2. Intensive, extensive and specific properties]]
- [ ] Estimate how many molecules a 1 µm and a 10 nm cube of room air contain, and say which supports a continuum (suggested, not lecturer-set). → [[#3. The continuum assumption]]
- [ ] Derive $R=R_u/M$ and compute $R$ for CO₂ and H₂ from their molar masses (suggested, not lecturer-set). → [[#Specific and universal gas constants]]

## Transcript and slide slips

> [!warning] Lecture-notes slip (Chapter 1, eq. 1.10)
> Where: [[#Worked example - mass of air in a container]].
>
> The volume is converted correctly to $1\cdot10^{-2}$ m³ in eq. 1.8, but eq. 1.10 substitutes $1\cdot10^{-3}$ m³. With $10^{-3}$ the mass would be 0.00119 kg; the printed answer 0.0119 kg is the value for $10^{-2}$ m³, so only the substituted number is wrong.

> [!warning] Problem-sheet rounding (Problem Sheet 1, Q1.2a)
> Where: [[#Worked example - heated rigid container with added gas]].
>
> The printed initial pressure is 99.75 kPa; the arithmetic gives 99 739 Pa, which rounds to 99.74 kPa. Parts (b) and (c) are unaffected at four significant figures.
