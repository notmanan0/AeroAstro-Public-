---
title: "FEEG1002 C5 - Strengthening Mechanisms and Annealing"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 20
tags: [feeg1002, materials, work-hardening, hall-petch, precipitation-hardening, annealing, recrystallisation]
aliases: ["Materials Lecture 6", "Strengthening mechanisms", "Annealing"]
date: 2026-11-05
status: lectured
coverage: "Materials L6 (28 Oct 2024, ll. 1–862): the tin-cry twinning demonstration, work hardening and elastic unloading, the copper-rod demonstration and loss of ductility, grain-boundary strengthening and the Hall–Petch relation, coherent and incoherent precipitates (cutting against bowing), annealing in three stages (recovery, recrystallisation, grain growth) and its dependence on time and temperature; slide deck 07 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]", "[[FEEG1002 C3 - Diffusion]]"]
next_topics: ["[[FEEG1002 C6 - Phase Diagrams]]"]
key_concepts: ["[[Strengthening Mechanisms in Metals]]", "[[Annealing of Cold-Worked Metals]]", "[[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 07 - Strengthening Mechanisms and Annealing.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 6 - Materials Strengthening and Annealing.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf"]
---

# FEEG1002 C5 - Strengthening Mechanisms and Annealing

> [!abstract] Summary
> Because yielding is the motion of dislocations, a metal is strengthened by obstructing them. Alloying puts solute stress fields in their way ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]]); work hardening multiplies and tangles the dislocations themselves; grain-boundary strengthening uses the boundaries between grains as barriers, giving the Hall–Petch relation $\sigma_y=\sigma_0+k_yd^{-1/2}$; and precipitation hardening grows small particles of a second phase that dislocations must cut through or bow round. Every gain in strength costs ductility. Annealing at about half the absolute melting temperature reverses work hardening by recovery, recrystallisation and grain growth, all diffusion-controlled and so strongly dependent on temperature.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks how a process changes yield strength, ductility or grain size, asks you to apply Hall–Petch, to find the permanent strain after unloading a work-hardened bar, or to describe what happens in each stage of annealing.
> - **Assumptions:** Hall–Petch holds for ordinary grain sizes (not nanocrystalline); Young's modulus is unchanged by any of these treatments; annealing rates follow an Arrhenius law in absolute temperature.
> - **Method:** 1. Name the obstacle: solute, dislocations, grain boundaries or precipitates. 2. Hall–Petch with two data points: $k_y=(\sigma_2-\sigma_1)/(d_2^{-1/2}-d_1^{-1/2})$, then $\sigma_0=\sigma_1-k_yd_1^{-1/2}$. 3. Unloading a work-hardened bar: down a line of slope $E$, permanent strain $\varepsilon_{total}-\sigma/E$; on reloading it yields at the stress it was unloaded from. 4. Annealing: recovery (dislocations rearrange, properties barely change), recrystallisation (new grains, strength falls, ductility returns), grain growth (strength falls further). 5. Rate at a new temperature from $\ln(r_2/r_1)=(Q/R)(1/T_1-1/T_2)$.
> - **Common mistakes:** unloading vertically instead of parallel to the elastic line; thinking work hardening changes $E$ (it changes yield and ductility, not stiffness).
> - **Practise:** [[#Worked example - Hall–Petch from two grain sizes]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]] Q3, Q5–Q7

A blacksmith hammering a bar finds it gets harder to shape the more it is worked, and has to put it back in the fire to soften it before carrying on. The hammering is work hardening and the fire is annealing, and between them they show the two levers a metallurgist pulls: making dislocations harder to move, and letting the crystal rebuild itself by diffusion.

Raising the yield strength means stopping the dislocations moving ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]]). There are four ways to do it, and each uses a different obstacle with a stress field or an interface that a dislocation cannot easily cross: dissolved solute atoms, other dislocations, the boundaries between grains, and particles of a second phase. The engineer chooses among them by what else they do. Grain refinement raises strength without much loss of toughness, but fine grains are a drawback at high temperature, where their boundaries speed up diffusion and creep. Work hardening is free during forming but uses up ductility. Precipitation hardening lets an aluminium alloy be machined soft and hardened afterwards.

Strength is not always what is wanted. A sheet that has been rolled until it is hard and brittle cannot be formed any further, so the process has to be reset, which is what annealing does.

---

## 1. Why strengthening works

The yield point is where dislocation motion starts, and a dislocation carries a compressive region on one side of its slip plane and a tensile region on the other ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#The stress field of an edge dislocation|C4]]). Those regions exist because the atoms around the dislocation are pushed together or pulled apart from the equilibrium spacing $r_0$ at which their net bond force is zero. Any feature of the crystal that has its own stress field, or that a dislocation cannot pass through, interacts with these regions: compression against compression, or tension against tension, repels, and more applied stress is needed to push the dislocation on. Each strengthening mechanism is a way of putting such features in the dislocations' path.

The first mechanism, solid-solution strengthening by alloying, is in [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Solid-solution strengthening|C4]]. The other three are covered in the sections below.

## 2. Work hardening

### Dislocations get in each other's way

Once a metal has yielded, more stress is needed to deform it further, up to the UTS. In a perfect crystal containing a single dislocation the stress–strain curve after yield would be flat: the dislocation would glide on at constant stress, a **perfectly plastic** response. Real metals give a rising curve. Plastic deformation does not just move the existing dislocations; it generates many new ones, so the **dislocation density** (the total length of dislocation line per unit volume) climbs steeply. Dislocations on the same slip system repel one another, compression against compression, and dislocations on intersecting systems cut across and tangle with each other. Some meet opposite partners and annihilate, but most stay, and the tangle makes every further dislocation movement harder. This rise in resistance to plastic deformation is **work hardening**, also called strain hardening or cold working. A heavily worked metal, polished and etched, shows intense slip lines crossing its grains.

Cold work also changes the grain shape. The grains are stretched in the direction of working into elongated, deformed grains with a high dislocation density, so the properties are no longer the same in every direction: the worked metal is **anisotropic**.

### Unloading and reloading

Load a metal past yield, work-harden it, and unload before it breaks. The elastic part of the strain is still stored in the stretched bonds and is recovered on unloading. Young's modulus is set by the bonding ([[FEEG1002 C1 - Atoms and Bonding#Why the curve sets melting point and stiffness|C1]]), not by the dislocations, so work hardening leaves it unchanged, and the unloading line is straight with exactly the same slope $E$ as the original loading line. If the bar is unloaded from stress $\sigma_1$ at total strain $\varepsilon_1$, the elastic strain recovered is $\sigma_1/E$ and the permanent strain left is

$$
\varepsilon_p=\varepsilon_1-\frac{\sigma_1}{E}
$$

Reload it and it climbs back up the same line, elastically, until it reaches $\sigma_1$: the work-hardened bar has a new, higher yield strength. Nanoindentation uses the same fact to measure the modulus from the unloading curve of an indent. Unloading must follow the elastic slope, not drop vertically; questions on work hardening test exactly this, and a vertical line gives the wrong strain.

![[m5_work_hardening_unloading.png|900]]

### What it costs in ductility

The total strain a metal can take before it fails does not change when it is worked, so every bit of plastic strain spent in work hardening is strain no longer available afterwards. Cold work raises the yield strength and the tensile strength but reduces the remaining ductility (%EL), and enough of it makes a metal brittle. A paper clip bent back and forth snaps.

A copper rod shows the effect clearly. Bending it once work-hardens the bend. Trying to straighten it does not remove the original bend; instead the rod bends either side of it, because the hardened region now has a higher yield strength than the copper next to it, which has only ever been loaded elastically and yields first.

The amount of cold work is usually given as the **percentage cold work**, the reduction in cross-sectional area from $A_0$ to $A_d$:

$$
\%CW=\frac{A_0-A_d}{A_0}\times100
$$

The brass in the annealing example below is 33 % cold worked.

## 3. Grain-boundary strengthening

### Pile-ups at grain boundaries

A metal is polycrystalline, and each grain is the same crystal structure rotated to a different orientation. A grain boundary is the edge of a crystal. A dislocation gliding on a slip plane reaches the boundary and cannot carry straight on, because in the next grain the slip planes point in a different direction. It stops, and the dislocations following it on the same slip system pile up behind it, each pushing on the one in front. The **pile-up** concentrates stress at the boundary. When that stress is large enough it starts slip on a suitably oriented plane in the neighbouring grain, and the deformation spreads.

The size of the grain decides how easy this is. In a large grain a long pile-up builds up, giving a large stress concentration at its head, and slip starts in the next grain at a low applied stress. In a small grain only a few dislocations fit in the pile-up, so the applied stress must be higher before slip can cross into the next grain. Finer grains therefore give a higher yield strength. Grain refinement is unusual among strengthening mechanisms because it raises toughness as well as strength.

### The Hall–Petch relation

The dependence of yield strength on the average grain diameter $d$ is the **Hall–Petch relation**:

$$
\boxed{\sigma_y=\sigma_0+k_yd^{-1/2}}
$$

$k_y$ is a material-specific constant, and $\sigma_0$ is a material-specific constant related to the friction stress resisting dislocation motion within the grains, which is raised by work hardening, solution hardening and precipitation hardening. A plot of $\sigma_y$ against $d^{-1/2}$ is a straight line of slope $k_y$ and intercept $\sigma_0$.

![[m5_hall_petch.png|900]]

The relation fails at both extremes. At very fine, nanometre grain sizes the grains are too small to hold dislocations at all; deformation switches to grain-boundary sliding and grain rotation, and the metal softens as the grains get smaller still, the **inverse Hall–Petch effect**. At high temperature the grain boundaries are fast paths for diffusion ([[FEEG1002 C3 - Diffusion#Activation energy and the structure of the path|C3]]), so fine grains speed up creep; components that run hot need coarse grains, and the best turbine blades are single crystals with no grain boundaries at all ([[FEEG1002 C9 - Fatigue, Creep and Corrosion#Designing against creep|C9]]).

## 4. Precipitation hardening

### A second phase inside the grains

If more of an alloying element is added than the host crystal can dissolve, the excess can come out of solution as small regions of a different phase with its own crystal structure: **precipitates**. In steel these are particles of iron carbide (cementite) in the iron; in aluminium–copper alloys they are particles of a copper-rich intermetallic compound. The solute atoms scattered through the host are under strain, because their bond lengths do not match; given the chance by heating, they diffuse together into a cluster where they are less strained, a new phase. The cluster's different atomic spacing in turn distorts the crystal around it and surrounds it with a large stress field, which obstructs dislocations.

How much precipitate forms, and when, depends on solubility, which needs the phase diagrams of [[FEEG1002 C6 - Phase Diagrams|C6]]; the heat-treatment route is in [[FEEG1002 C7 - Steels and Precipitation Hardening#5. Precipitation hardening|C7]]. The processing sequence is that an aluminium alloy can be shaped and machined while it is soft, then heat-treated so that copper diffuses into precipitates and the yield strength rises.

### Coherent and incoherent precipitates

As a precipitate grows under heat treatment its relationship with the surrounding crystal changes.

A small **coherent** precipitate has lattice planes that run continuously into those of the matrix, strained to fit. It strengthens through its stress field, but a dislocation that is pushed hard enough can cut straight through it, shearing it.

As it grows, the strain of fitting becomes too great and the precipitate becomes **incoherent**, with a lattice structure unlike the matrix and a proper interface round it: in effect a little grain boundary, or a new crystal, inside the grain. A dislocation cannot cut through it. Instead it is pinned at the particles and bows out between them, until the bowed loops meet behind each particle, reconnect, and let the dislocation carry on, leaving a ring of dislocation round each particle. The stress to bow a dislocation between particles depends on how far apart they are: closely spaced particles need a high stress. Controlling the type, size and spacing of the precipitates is therefore the whole art of precipitation hardening.

![[m5_precipitate_cut_bow.png|900]]

## 5. Annealing

### Resetting a cold-worked metal

A heavily worked metal has a high yield strength but little ductility left. **Annealing** reduces or removes the effects of cold working: the metal is heated, typically to around half its absolute melting temperature, $T\approx0.5T_m$, and held. A blacksmith working steel does the same thing by reheating the bar in the fire. (Working steel hot also helps for another reason: BCC iron deforms much more easily when hot, [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Temperature and the yield stress|C4]].) Annealing happens in three stages, all of which depend on diffusion.

### Recovery

In a cold-worked metal the dislocations are tangled in highly stressed, local arrangements. On heating, atoms can diffuse, and the dislocations rearrange to minimise their local stress fields: they line up in walls with the compressive region of each dislocation next to the tensile region of its neighbour, forming low-angle boundaries. Between the walls the crystal is left almost free of dislocations and stress. The grain structure does not change, and neither do the mechanical properties much, but internal stresses are relieved.
### Recrystallisation

In the dislocation-free regions left by recovery, new crystals nucleate and grow by atomic diffusion. They are free of strain and roughly equal in size in every direction (equiaxed), and as they grow they sweep away the old dislocations and ignore the old grain boundaries, until the whole of the worked structure has been replaced by a new set of fine grains. Brass, 33 % cold worked and held at 580 °C, shows new crystals after 3 s, growing crystals after 4 s, and is fully recrystallised after 8 s.

The size of the recrystallised grains can be controlled. More cold work stores more energy and gives more sites for new grains to start, so the recrystallised grains are finer. A higher annealing temperature speeds up diffusion and gives larger grains. Because the new grains are fine, the recrystallised metal keeps a fair part of its strength through grain-boundary strengthening, while most of its ductility returns.

### Grain growth

If the metal is held at temperature after recrystallisation, the grains keep growing, larger grains consuming smaller ones. Grain boundaries are regions of high energy, so the total energy falls as the boundary area falls, the same reason that small bubbles in a foam disappear while large ones grow. The brass that was fully recrystallised after 8 s at 580 °C has coarser grains after 15 min at 580 °C, and much coarser grains after 7 min at 700 °C.

### Properties against annealing temperature

As the annealing temperature (for a fixed time) rises through the three stages, the properties change in a characteristic way. In the recovery range the strength and ductility barely change. Through recrystallisation the tensile strength falls steeply and the ductility rises steeply. During grain growth the strength continues to fall slowly and the ductility to rise, as the Hall–Petch contribution shrinks with the growing grains.

![[m5_annealing_properties.png|900]]

### Recrystallisation as a thermally activated process

Every stage of annealing proceeds by diffusion, so its rate $r$ follows the same Arrhenius form as the diffusion coefficient ([[FEEG1002 C3 - Diffusion#The Arrhenius equation|C3]]):

$$
r=A\exp\left(-\frac{Q}{RT}\right)
$$

The time to reach a given state is inversely proportional to the rate, so a modest rise in temperature shortens the anneal enormously, as the brass series shows (seconds at 580 °C for recrystallisation, against hours at lower temperatures). Annealing is a time-and-temperature process: both have to be specified.

---

## Worked examples

### Worked example - Hall–Petch from two grain sizes

The lower yield point of an iron is 135 MPa at an average grain diameter of 0.050 mm, and 260 MPa at 0.008 mm. Find $\sigma_0$ and $k_y$, and the grain size that would give a yield point of 205 MPa.

Write the Hall–Petch relation for both grain sizes. With $d$ in mm, $d_1^{-1/2}=0.050^{-1/2}=4.472$ mm$^{-1/2}$ and $d_2^{-1/2}=0.008^{-1/2}=11.180$ mm$^{-1/2}$:

$$
135=\sigma_0+4.472k_y
$$

$$
260=\sigma_0+11.180k_y
$$

Subtract the first equation from the second:

$$
125=6.708k_y
$$

$$
k_y=18.63\ \mathrm{MPa\,mm^{1/2}}
$$

Back into the first equation:

$$
\sigma_0=135-4.472\times18.63=51.7\ \mathrm{MPa}
$$

For $\sigma_y=205$ MPa:

$$
d^{-1/2}=\frac{205-51.7}{18.63}=8.229\ \mathrm{mm^{-1/2}}
$$

$$
d=\frac{1}{8.229^2}=0.0148\ \mathrm{mm}
$$

A grain size of about 15 µm.

> [!check] Units of $k_y$
> $k_y$ carries units of stress × length$^{1/2}$, so its value depends on the length unit. In SI, $18.63\ \mathrm{MPa\,mm^{1/2}}=18.63\times(10^{-3})^{1/2}=0.589\ \mathrm{MPa\,m^{1/2}}$. Mixing millimetres in $d$ with a $k_y$ quoted per metre is a common error.

### Worked example - unloading a work-hardened copper bar

A copper bar ($E=110$ GPa) is stretched until the stress is 300 MPa at a total engineering strain of 0.100, then unloaded. Find the permanent strain and the yield strength on reloading.

The unloading line has slope $E$, so the elastic strain recovered is

$$
\varepsilon_e=\frac{\sigma_1}{E}=\frac{300}{110\,000}=0.0027
$$

and the permanent strain is

$$
\varepsilon_p=0.100-0.0027=0.0973
$$

On reloading, the bar is elastic up to 300 MPa and yields there. Unloading vertically would have given a permanent strain of 0.100, an error equal to the whole elastic strain; with a stiff material and a high stress the error is small here (3 %), but on a short gauge length or a low-modulus alloy it is not.

### Worked example - activation energy for recrystallisation

The growth velocity of new crystals in cold-worked aluminium is $5.62\times10^{-13}$ m/s at 200 °C and $1.82\times10^{-5}$ m/s at 400 °C (Tutorial Sheet 2, Q7). Find the activation energy and predict the velocity at 300 °C.

With $T_1=473$ K and $T_2=673$ K,

$$
\ln\frac{v_2}{v_1}=\ln\frac{1.82\times10^{-5}}{5.62\times10^{-13}}=\ln(3.24\times10^7)=17.29
$$

$$
\frac1{T_1}-\frac1{T_2}=\frac1{473.15}-\frac1{673.15}=6.28\times10^{-4}\ \mathrm{K^{-1}}
$$

$$
Q=\frac{8.314\times17.29}{6.28\times10^{-4}}=2.29\times10^5\ \mathrm{J/mol}=229\ \mathrm{kJ/mol}
$$

At 300 °C ($T=573$ K):

$$
v=1.82\times10^{-5}\exp\left[-\frac{229\,000}{8.314}\left(\frac1{573.15}-\frac1{673.15}\right)\right]=1.82\times10^{-5}e^{-7.14}=1.44\times10^{-8}\ \mathrm{m/s}
$$

The sheet gives $1.35\times10^{-8}$ m/s at 300 °C, within 7 %, so the data follow an Arrhenius law closely. A 100 °C rise from 200 °C to 300 °C speeds the growth by a factor of about 24 000.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]] · Next: [[FEEG1002 C6 - Phase Diagrams]]
- Concepts: [[Strengthening Mechanisms in Metals]] · [[Annealing of Cold-Worked Metals]] · [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]] · [[Dislocations and Slip Systems]]
- Worked sheet: [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]] (Q3, Q5–Q7) · Formula list: [[FEEG1002 Formula Sheet]]
- Year 2: [[Hall-Petch Relation]] · [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]] (precipitation-hardened aluminium alloys) · [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]] (single-crystal blades)

## Sources

- `FEEG1002 Lecture 6 - Materials Strengthening and Annealing.txt` (L6, 28 Oct 2024): tin cry (ll. 1–43), aims and recap (ll. 44–95), work hardening (ll. 96–185), unloading and reloading (ll. 186–242), the copper rod and ductility (ll. 243–348), grain-boundary strengthening (ll. 349–451), Hall–Petch and its limits (ll. 452–526), precipitation hardening (ll. 527–678), annealing, recovery, recrystallisation and grain growth (ll. 679–844), summary (ll. 845–862).
- `Lecture 07 - Strengthening Mechanisms and Annealing.pdf` (slide deck 07): work hardening, grain-boundary strengthening, the Hall–Petch equation, precipitation hardening, the three stages of annealing, the brass recrystallisation series, controlling grain size. Figures after Callister.
- `Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf`: Q3 and Q5–Q7.
- The Hall–Petch example uses Callister's data for iron; the percentage cold work definition and the copper unloading example are added to make the slide statements quantitative.

## Self-study tasks

### Core

- [ ] Tutorial 2, Q3: why solute atoms, other dislocations, grain boundaries and precipitates hinder dislocation motion. → [[#1. Why strengthening works]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q3 - Obstacles to dislocation motion]]
- [ ] Tutorial 2, Q5: which properties change when a metal is work-hardened. → [[#2. Work hardening]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q5 - Effects of work hardening]]
- [ ] Tutorial 2, Q6: how a subsequent heat treatment improves them. → [[#5. Annealing]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q6 - Restoring the properties by annealing]]
- [ ] Tutorial 2, Q7: why the crystal growth velocity is exponential in temperature, and the temperature for $10^{-2}$ m/s. Target about 520 °C. → [[#Worked example - activation energy for recrystallisation]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q7 - Growth velocity of recrystallised grains]]
- [ ] Unload a work-hardened curve along the elastic slope and find the permanent strain, flagged for exam questions (L6, ll. 232–242). → [[#Unloading and reloading]] · [[#Worked example - unloading a work-hardened copper bar]]

### Further practice

- [ ] Explain the copper-rod demonstration: why the rod bends either side of the first bend when straightened (L6, ll. 259–299). → [[#What it costs in ductility]]
- [ ] Use Hall–Petch to find the grain size for a target yield strength (suggested, not lecturer-set). → [[#Worked example - Hall–Petch from two grain sizes]]

## Transcript and slide slips

> [!warning] Transcript slip (L6, ll. 178–180)
> Where: [[#Dislocations get in each other's way]].
>
> The lines in the optical micrograph of a heavily worked metal are described as "the linear defects, the dislocations". At that magnification they are slip lines, surface steps produced by many dislocations; individual dislocations are only visible in the TEM.

> [!warning] Slide slips (slide deck 07, "Hall-Petch Equation" and "Further grain growth")
> Where: [[#The Hall–Petch relation]] · [[#Grain growth]].
>
> The grain size appears as capital $D$ on the slide; it is the lower-case $d$ of the equation (corrected at L6, ll. 460–466). The brass grain-growth series is labelled "8 seconds, 15 mins, 7 mins at 700 °C"; Callister's original figure gives 10 min at 700 °C. The comparison it illustrates, much faster growth at the higher temperature, is unaffected.
