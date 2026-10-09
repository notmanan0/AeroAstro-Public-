---
title: "SESA2028 M3 - Corrosion, Wear and Surface Engineering"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 3
tags: [sesa2028, materials, corrosion, electrochemistry, wear, coatings]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
next_topics: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
key_concepts: ["[[Nernst Equation and Galvanic Series]]", "[[Evans Diagram and Passivation]]", "[[Localised Corrosion]]", "[[Sensitisation and Weld Decay]]", "[[Stress Corrosion Cracking]]", "[[Corrosion Protection]]"]
sources: ["02 - Sources/Materials Lectures/Structural Performance 2025.pdf (lectures 3-4)", "mini lectures ML3a, ML3b, ML3c, ML4a, ML4b, ML4c", "Green Book corrosion notes (theory only)"]
---

# SESA2028 M3 - Corrosion, Wear and Surface Engineering

> [!abstract] Summary
> Wet corrosion is an electrochemical cell: **the anode dissolves**. The cell needs five things: an anode, a cathode, electrical contact between them, an ionic electrolyte, and a cathode reactant (usually dissolved $\mathrm O_2$ or $\mathrm H^+$). Electrode potentials say *which* metal is the anode. Polarisation and passivation (Evans diagrams) say *how fast* it corrodes. Localised attack (galvanic, pitting, crevice, intergranular, SCC) can be up to $10^5$ times faster than uniform corrosion, because a **small anode** is driven by a **large cathode**. In exams, corrosion usually appears as the "other service problem" that shortens a fatigue life, or as weld decay in stainless steel.

## 1. The corrosion cell

![[Figures/materials_electrode_potentials.png]]

**Anode (oxidation, metal lost):**

$$
\mathrm{M\rightarrow M^{n+}+ne^-},\qquad\text{e.g. } \mathrm{Fe\rightarrow Fe^{2+}+2e^-}.
$$

**Cathode (reduction).** The reaction depends on the environment:

$$
\text{acid: } \mathrm{2H^++2e^-\rightarrow H_2},\qquad
\text{neutral/basic: } \mathrm{O_2+2H_2O+4e^-\rightarrow 4OH^-}.
$$

In neutral water, the $\mathrm{OH^-}$ from the cathode meets the $\mathrm{Fe^{2+}}$ from the anode *between* them, and rust precipitates there, not on top of the anode.

> [!tip] Always identify the anode first
> Every corrosion question reduces to "where is the anode, what makes it the anode, and how big is it compared with the cathode?"

## 2. Driving force: electrode potentials and the galvanic series

The standard electrode potential $E^0$ is measured against the standard hydrogen electrode (SHE $=0$ V, Pt electrode, 1 M, 25 °C). It ranks reactivity: **the more negative metal of a couple is the anode**.

$$
\mathrm{Zn^{2+}+2e^-\rightarrow Zn}\ \ (-0.76\ \mathrm V),\qquad
\mathrm{Cu^{2+}+2e^-\rightarrow Cu}\ \ (+0.34\ \mathrm V).
$$

The lecture's rule is "most negative minus least negative": $-0.76-(+0.34)=-1.10$ V. The magnitude of the Zn-Cu cell EMF is **1.10 V**, and Zn corrodes.

Whether a reaction is spontaneous follows from $\Delta G=-nFE$ ($F=96\,485\ \mathrm{C\,mol^{-1}}$):

- $\mathrm{Fe+2H^+}$: $E=+0.44$ V, so $\Delta G=-84.9$ kJ/mol. Iron dissolves in acid.
- $\mathrm{Cu+2H^+}$: $E=-0.34$ V, so $\Delta G=+65.6$ kJ/mol. Copper does not.

The **galvanic series** is the practical version: potentials measured in a real environment such as seawater, including alloys and passivated states. Standard potentials are for pure metals in 1 M solutions of their own ions.

### Concentration effects: the Nernst equation

$$
E=E^0+\frac{0.0592}{n}\log_{10}\left[\mathrm{M^{n+}}\right]\quad(25^\circ\mathrm C,\ \text{reduction potential}).
$$

The slide writes it as $E=E^0-(0.592/n)\log C_{ion}$. The coefficient should be **0.0592 V**; the sign depends on convention. The physics is what matters: **the same metal becomes more anodic where its ion concentration (or the local $\mathrm O_2$ concentration) is lower.** That gives **concentration cells** with no second metal involved, and it drives crevice corrosion and differential aeration (Section 5). See [[Nernst Equation and Galvanic Series]].

## 3. Rate: Faraday's law

The mass dissolved is proportional to the charge passed:

$$
w=kIt=\frac{M\,I\,t}{nF},\qquad
\text{rate per unit area}=\frac{kI}{A}\propto i\ (\text{current density}).
$$

Converting to penetration rate, with $M$ in g/mol, $I$ in mA, $A$ in cm² and $\rho$ in g/cm³:

$$
\mathrm{CR\,[mm/yr]}=3.27\,\frac{M\,I}{n\,\rho\,A},\qquad
\mathrm{CR\,[g\,m^{-2}\,day^{-1}]}=8.95\,\frac{M\,I}{n\,A}.
$$

(The constants are just unit conversions of $M/(nF)$. For example, $3.27=10^{-3}\times10\times3.156\times10^7/96\,485$.)

**Consequence.** For a fixed corrosion current, penetration rate $\propto 1/A_{anode}$. The current is usually limited by the **cathode** reaction (supply of $\mathrm O_2$), so $I\propto A_{cathode}$. Therefore

$$
\text{penetration rate}\propto\frac{A_{cathode}}{A_{anode}}.
$$

A small anode coupled to a large cathode is the worst case: a zinc-plated fastener in a steel sheet, a pit, or the bottom of a crevice.

Faraday gives a *general* rate. The real current is set by **polarisation**.

## 4. Polarisation and passivation

### Evans diagrams

![[Figures/materials_evans_diagram.png]]

When current flows, ions build up or deplete in a **depletion zone** next to each electrode, which shifts its potential:

- the anodic curve moves **more positive** as current increases;
- the cathodic curve moves **more negative**.

Plotting $E$ against $\log i$ (an Evans diagram), the anodic and cathodic lines **cross at $E_{corr}$, $i_{corr}$**. A high $i_{corr}$ means fast corrosion.

- **Polarisation is good.** Steep curves give a low $i_{corr}$, because more potential is needed to keep the cell running.
- The rate is often limited by **availability of the cathodic species** (for example $\mathrm O_2$ diffusion).
- Low temperature can *reduce* polarisation, so corrosion can be faster in the cold. The lecturer's example is a tin of baked beans in the fridge.
- An Al-Fe couple in 3 % NaCl shows the current density decaying with time as polarisation develops.

### Passivation

![[Figures/materials_passivation_curve.png]]

Some metals (stainless steel, Al, Ti, Cr) form a thin protective oxide once the potential rises past a critical value. The anodic curve then shows three regions: an **active nose**, a **passive region** (very low current), and a **transpassive** region. What happens depends on where the cathodic line crosses it:

| Cathodic curve crosses | Result |
|---|---|
| 1: active region | fast corrosion, no film |
| 2: passive region | stable passive film; a scratch **re-passivates** immediately (a safe, oxidising environment) |
| 3: transpassive region | film breaks down; a scratch is **not** repaired (unsafe) |

In reducing conditions the oxide is not repaired and the surface goes active. That is why stainless steel can fail in stagnant, oxygen-starved crevices. See [[Evans Diagram and Passivation]].

## 5. Types of corrosion

**Uniform (general) corrosion** is measurable, predictable and preventable. Structural analysis of offshore monopiles tracks wall thinning in the tidal zone, for example. Every other type below is **localised**. It is driven by potential differences (between materials, or between concentrations), and it is fast because a small anode is concentrated against a large cathode.

### Galvanic

Galvanic corrosion needs dissimilar metals **plus** electrical contact **plus** an electrolyte.

- **Bad**: a Zn fastener on steel corrodes away, because Zn is anodic to steel.
- **Good**: galvanised steel. The Zn coating is the anode, so the steel stays protected **even where the coating is scratched**, as the Zn keeps corroding sacrificially.
- The relative anode and cathode areas control the damage (Section 3).

### Pitting

A locally active spot (anode) is surrounded by a large cathode, giving very fast local dissolution. In Al alloys, pits form at second-phase particles: an **anodic** particle dissolves, or a **cathodic** particle makes the surrounding matrix anodic. Pits can be narrow and deep, wide and shallow, elliptical, undercut, subsurface, or run horizontally along grain boundaries. **Every pit is a stress concentration, so a fatigue origin.**

### Crevice

Crevices form under bolt heads, washers, lap joints and debris.

1. At first the $\mathrm O_2$ is uniform and the corrosion is general.
2. The stagnant crevice uses up its $\mathrm O_2$ and cannot replace it.
3. The crevice becomes the **anode**; the freely aerated surface becomes a **large cathode**.
4. Corrosion products plug the gap, and hydrolysis acidifies the crevice. The process is **autocatalytic**, hidden and dangerous.

The **water droplet on steel** is the same physics (**differential aeration**). The droplet edge is well aerated and becomes the cathode. The centre is starved of $\mathrm O_2$ and becomes the anode. Rust forms as a ring between them.

### Intergranular: weld decay in stainless steel

Slow cooling through, or holding at, about 500-800 °C lets $\mathrm{Cr_{23}C_6}$ precipitate on grain boundaries. The Cr comes from next to the boundary, leaving a zone with **less than 12 % Cr**, which cannot passivate. That active grain-boundary anode sits next to large passive grain cathodes: a tiny cell with rapid attack. Prevention:

1. **Cool quickly** through the sensitisation range (no time for carbides to form).
2. **Low carbon** (304L, 316L): too little C to form much carbide.
3. **Stabilise** with Ti or Nb, which are stronger carbide formers than Cr and leave the Cr in solution.

See [[Sensitisation and Weld Decay]].

### Cavitation

Pressure fluctuations (propellers, pumps) form vapour bubbles that implode, firing liquid jets at the surface. The pressure pulses destroy protective films, giving combined corrosion, fatigue and erosion.

### Erosion

Particles carried in a liquid or gas wear the surface. The damage depends on the medium, velocity and impact angle:

- near $90^\circ$: plastic deformation (a peening effect) or brittle chipping;
- low angle: cutting and abrasion.

Pipe design matters (bends, slurries). Erosion and corrosion act together: erosion strips the film, and corrosion attacks the fresh metal.

### Stress corrosion cracking (SCC)

SCC needs three things together: a **susceptible material**, a **specific environment**, and a **sustained tensile stress** (it is not cyclic). Cracks are often intergranular and branching ("tree roots"). They can grow at $K$ as low as about 1 % of $K_{Ic}$, so there is little warning. There is a threshold $K_{ISCC}$ below which SCC does not occur. Growth depends on the crack-tip film rupturing and re-forming under the combined local stress and chemistry. See [[Stress Corrosion Cracking]].

## 6. Protection and prevention

| Method | How it works | Example |
|---|---|---|
| **Sacrificial anode** (the slide calls this "anodic protection") | couple the structure to a more active metal that corrodes instead | Mg anode on a buried pipeline; Zn anodes on hulls; galvanising |
| **Impressed current** (cathodic protection) | a DC supply drives the structure to be the **cathode**; a scrap-metal anode is consumed | offshore structures, pipelines |
| **Seal the system** | trapped $\mathrm O_2$ is used up after a little initial corrosion, then the cathode reaction stops | central-heating circuits, sealed bolted joints |
| **Coatings** | paints act mainly as **ionic/electrical resistors**, not perfect $\mathrm O_2$ barriers; metallic (Zn, Cr), inorganic (anodised oxide) or organic | paint systems, anodising |
| **Coherent oxides** | choose an alloy whose own oxide protects it | Cr > 12 % (stainless), Al, Ti |

**Design rules (good detailing):**

- Know where the anode is; **avoid small anode / large cathode**.
- Avoid crevices, sharp edges and water traps. Provide drainage holes.
- Welded joints are preferable to bolted ones (fewer crevices), but watch for weld decay.
- Avoid dissimilar-metal contact, or insulate it.
- Control the environment: temperature, velocity, $\mathrm O_2$, ion concentration, inhibitors, cleaning.

The lecture's summary tree: **materials selection | coatings | design | cathodic/anodic protection | environmental control**. See [[Corrosion Protection]].

## 7. Wear

Wear is failure governed by surface properties under complex contact loading. It leads to **loss of fit, fatigue, or seizure**.

| Mechanism | What happens | Controlled by |
|---|---|---|
| Abrasive (2-body) | a hard asperity ploughs the softer surface | relative hardness |
| Abrasive (3-body) | loose hard particles (often oxidised debris) roll and cut: "inadvertent machining" | hardness, debris removal |
| Adhesive | asperity micro-welds shear, and material transfers between surfaces | low chemical affinity between the pair, lubrication |
| Sliding | combined adhesive and abrasive under sliding | tribofilms, lubrication |
| Contact (rolling) fatigue | subsurface cyclic shear under rolling contact; fragments spall out | subsurface cleanliness, case hardness (e.g. Hatfield rails) |

Tribology happens at many length scales. Southampton's national tribology centre, nCATS, is cited.

## 8. Surface engineering

**Surface treatments** (the surface reacts to make the layer):

- **Anodising** (Al, Ti) thickens the natural oxide by deliberately driving corrosion. On Ti the colour is set by oxide thickness.
- **Carburising** diffuses C into the surface, giving a high-C martensitic case over a tough core.
- **Nitriding** forms hard nitrides (golden colour) and distorts the lattice.
- Induction or flame hardening gives a martensitic case without changing the composition.

The idea behind all of these: **a hard case for wear and fatigue, a tough core to arrest cracks** ([[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying|M7]]).

**Coatings** (a separate layer is added):

| Process | Use |
|---|---|
| Hot-dip galvanising (Zn) | corrosion (sacrificial) |
| Electroplating (e.g. Cr on Cu alloy) | wear and appearance |
| CVD diamond / diamond-like carbon | wear |
| HVOF ceramic "splats" on a grit-blasted surface | wear |
| Weld overlay | thick wear or corrosion layers (similar to additive manufacturing) |
| TBC stack (aluminide bond coat by CVD, then a thermally grown oxide, then a PVD columnar YSZ top coat) | turbine-blade thermal protection ([[Thermal Barrier Coatings]]) |

## 9. Exam checklist

- [ ] Name the anode and the cathode reaction for the environment (acid or neutral/aerated).
- [ ] Explain *why* one region is anodic: a different metal, a different concentration or $\mathrm O_2$ level, Cr depletion, or a broken film.
- [ ] Comment on the anode/cathode area ratio.
- [ ] For a fatigue-lifing follow-up ("humid/salt environment?"): pitting removes initiation, corrosion fatigue raises $da/dN$ (larger effective $A$), SCC under sustained stress, and hydrogen embrittlement. The consequence is a shorter life and more frequent inspection.
- [ ] Give prevention at three levels: material, coating, design or detailing.

## Related

- [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]: stainless classes and why Cr > 12 %.
- [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]: **dry** oxidation uses the same anode and cathode reactions, but through a growing oxide.
- [[Fatigue Fracture Surface Features]]: corrosion pits as fatigue origins.
