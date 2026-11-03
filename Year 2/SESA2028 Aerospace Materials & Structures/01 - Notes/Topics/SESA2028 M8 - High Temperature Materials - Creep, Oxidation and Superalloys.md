---
title: "SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 8
tags: [sesa2028, materials, creep, oxidation, superalloys, ceramics, coatings, turbine-blade]
status: lectured
coverage: "Mini-lectures ML14a, ML14b, ML14c, ML15a, ML15b, ML16a, ML16b, ML16c and ML16d; creep calculations from tutorial MT5 and past papers"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]", "[[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]"]
next_topics: []
key_concepts: ["[[Creep Curve and Mechanisms]]", "[[Larson-Miller Parameter]]", "[[Creep Miner's Rule]]", "[[Oxidation Rate Laws]]", "[[Gamma Prime Strengthening]]", "[[Single Crystal Casting]]", "[[Thermal Barrier Coatings]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]]"]
sources: ["02 - Sources/Materials Lectures/High temperature materials 2025.pdf", "02 - Sources/Materials Lectures/mini lecture videos/ML14a Creep Fundamentals_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML14b Creep Mechanisms_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML14c Creep Lifing Approaches_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML15a Oxidation Processes_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML15b engineering high temperature alloys_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML16a intermetallics_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML16b Ceramics and their uses_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML16c High temperature coatings_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML16d turbine blade case study_default.txt"]
---

# SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys

> [!abstract] Summary
> Above about 40 % of its absolute melting temperature a material creeps: it keeps deforming at constant load, through dislocation climb, diffusion through the grains and sliding along grain boundaries, until cavities link up and it ruptures. The steady-state creep rate follows a power law in stress and an Arrhenius law in temperature, which is why small changes in either change the life a great deal, and the Larson–Miller parameter and Miner's rule turn limited test data into lives. At the same temperatures oxidation speeds up, controlled by diffusion through the growing oxide, so the alloy must form a dense, adherent chromia or alumina scale. Nickel superalloys, grown out of austenitic stainless steel, meet both needs with a coherent $\gamma'$ precipitate that resists coarsening and even strengthens with temperature; intermetallics and ceramics go hotter but are brittle; and the modern turbine blade combines a single-crystal superalloy, internal cooling and a ceramic thermal barrier coating.

> [!summary]- Exam use: quick path
> - **Use it when:** a part runs above about $0.4T_m$ (blades, discs, exhausts, pressure plant), or a question asks for creep mechanisms, a creep life, oxidation behaviour, superalloy design, ceramics or coatings.
> - **Assumptions:** life governed by secondary creep; Arrhenius temperature dependence; Larson–Miller at constant stress with $C\approx20$, $T$ in kelvin, $t$ in hours; Miner's rule with linear damage.
> - **Method (life):** 1. Larson–Miller: read the LMP at the service stress, then $\log_{10}t_r=\mathrm{LMP}/T-C$. 2. Varying conditions: interpolate each $t_{r,i}$ in $\log t_r$, sum $t_i/t_{r,i}$, remaining life $=(1-\sum)\,t_{r,\text{new}}$. 3. Apply a safety factor and state the read-off uncertainty.
> - **Method (design):** stable microstructure, high melting point, slow self-diffusion, few or aligned grain boundaries, pinned dislocations, a protective oxide, lower metal temperature.
> - **Common mistakes:** temperature in °C in the LMP; interpolating creep lives linearly in $t_r$ rather than $\log t_r$.
> - **Example:** [[#Larson–Miller lives]]. **Exercise:** [[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]].

High-temperature service brings every structural-performance problem met so far, strength, toughness, fatigue, corrosion, and adds new ones (ML14a, ll. 9–62). The first requirement is obvious, a high melting point, but not enough: the material must keep its strength, so the microstructure that gives it strength must survive, which is why precipitate-strengthened light alloys, whose precipitates dissolve or coarsen when hot, fail here. Diffusion speeds up, so creep appears, and oxidation accelerates, so a protective oxide is needed. And there is a catch in manufacture: the qualities wanted in service, not softening and not melting, make the material hard to shape, so cost matters, and only applications such as space missions can pay for the most exotic materials.

The physical picture for this note is atoms that have started to move. At room temperature a metal's atoms sit still and only dislocations carry deformation. Heated to a good fraction of its melting point, atoms and vacancies diffuse readily, especially along grain boundaries, so a loaded part slowly changes shape even at stresses far below yield, grain boundaries slide and open up, precipitates coarsen, and oxygen ions and metal ions migrate through any surface oxide. High-temperature alloy design is the business of making all those movements slow.

## 1. Creep

Hang a weight from a bar in a hot room and watch it (ML14a, ll. 63–97). It stretches elastically at once, then keeps extending: quickly at first, the **primary** stage, then at a steady rate, the **secondary** stage, then faster again as damage accumulates in the **tertiary** stage, until it ruptures. The steady rate is what designers use, for instance to predict when a turbine blade, slowly lengthening, will reach the engine casing. The sigmoid shape resembles the Paris-law plot of [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]] but is a different thing, strain against time.

![[materials_creep_curve.png|800]]

**Creep** is time-dependent permanent deformation under load, and it depends on temperature relative to the melting point (ll. 82–92). It becomes significant above about 40 % of the absolute melting temperature, the homologous temperature $T/T_m\approx0.4$: 200 °C does nothing much to a nickel superalloy but is a high temperature for lead.

The secondary creep rate is a power law in stress times an Arrhenius term (ll. 98–107):

$$
\dot\varepsilon_{ss}=A\sigma^n\exp\left(-\frac{Q}{RT}\right),
$$

where $A$ is a material constant, $n$ the stress exponent, $R$ the gas constant, $T$ the absolute temperature and $Q$ an activation energy. Measured values of $Q$ match the activation energy for self-diffusion, the energy for an atom to hop through a lattice of its own kind, which is good evidence that diffusion controls creep; above about $0.4T_m$ there is enough thermal energy to overcome it (ML14c, ll. 28–40). Since a faster creep rate means a shorter life, the rupture time is inversely proportional to the rate (ll. 41–47):

$$
t_r=A'\sigma^{-n}\exp\left(+\frac{Q}{RT}\right).
$$

Both dependences are steep. At 1034 MPa the same alloy creeps very differently at 630, 640 and 650 °C, and at 650 °C very differently at 984, 1010 and 1034 MPa (ll. 3–24); the worked example puts numbers on it.

### Stress relaxation

Fix the strain instead of the load, by stretching a bar between ceiling and floor, and the initial stress decays over time by the same creep process, faster at higher temperature and higher initial stress (ML14a, ll. 108–129). The rate of relaxation is proportional to the stress that drives it:

$$
\frac{d\sigma}{dt}=-\frac{\sigma}{\tau},
$$

with $\tau$ the relaxation time. Separating variables,

$$
\frac{d\sigma}{\sigma}=-\frac{dt}{\tau},
$$

and integrating from $\sigma_0$ at $t=0$,

$$
\ln\frac{\sigma}{\sigma_0}=-\frac{t}{\tau},
\qquad
\sigma=\sigma_0e^{-t/\tau}.
$$

A bolted flange loses its preload this way.

## 2. Creep mechanisms

A deformation-mechanism map for nickel, of normalised shear stress $\tau/\mu$ against homologous temperature, shows which process dominates where, with contours of strain rate from $10^{-10}$ to 1 per second (ML14a, ll. 130–166). At high stress and low temperature, ordinary dislocation plasticity; at high temperature and low stress, diffusional flow; between them, low- and high-temperature creep, where dislocation motion and diffusion act together.

![[materials_creep_mechanisms.png|950]]

Three mechanisms matter (ML14a, ll. 166–185; ML14b). An edge dislocation is confined to one slip plane, and stops at an obstacle such as a precipitate. If vacancies can diffuse to the edge of its extra half-plane, the half-plane shortens by one atom at a time, so the dislocation **climbs** off the obstacle and glides on (ML14b, ll. 6–23). In BCC and HCP metals slip is thermally activated anyway (ll. 33–45). In primary creep this enhanced mobility competes with work hardening, so the rate falls; the steady secondary rate is reached when the rate of work hardening equals the rate of recovery (ll. 49–76).

At high temperature and low stress, deformation can happen by diffusion alone (ll. 85–124). Under tension, atoms migrate through a grain towards the faces that are being pulled apart, and vacancies go the other way, so the grain lengthens; this is bulk, or Nabarro–Herring, diffusion creep.

At somewhat lower temperatures and higher stresses, diffusion along grain boundaries, much faster than through the grains because the boundaries are disordered, lets boundaries that carry a resolved shear stress slide past each other (ll. 125–165). This **grain-boundary sliding** gives far more deformation than bulk diffusion. Where boundaries meet at triple points, sliding opens cavities, which grow and coalesce into intergranular creep rupture, the tertiary stage (ll. 166–184). Meanwhile the microstructure degrades: dislocations recover into cells, the metal may recrystallise, and precipitates coarsen or dissolve (ll. 198–230).

## 3. Creep data and lifing

Creep data come in several forms (ML14c, ll. 48–110). Plots of stress against time at a fixed temperature, with contours of equal strain, answer "how long until the blade has stretched enough to touch the casing?". Plots of stress against rupture time on log–log axes, one line per temperature, give lives. Long-term data are scarce: $10^5$ hours is 11.4 years, so few laboratories outside government and nuclear programmes run tests that long, and design lives are found by extrapolation (ll. 79–96).

### The Larson–Miller parameter

The Larson–Miller parameter collapses time and temperature into one number for each stress (ll. 111–249). It assumes life is controlled by secondary creep and applies at constant stress. Start from the rupture time at fixed stress, where the stress term is a constant absorbed into $A'$:

$$
t_r=A'\exp\left(\frac{Q}{RT}\right).
$$

Take natural logarithms:

$$
\ln t_r=\ln A'+\frac{Q}{RT}.
$$

Subtract $\ln A'$ and multiply by $T$:

$$
T\left(\ln t_r-\ln A'\right)=\frac{Q}{R}=\text{constant}.
$$

Converting to base-10 logarithms and writing $-\ln A'$ in base 10 as a constant $C$ gives the empirical form

$$
\mathrm{LMP}=T\left(C+\log_{10}t_r\right),
$$

with $T$ in kelvin, $t_r$ in hours and $C$ usually about 20. The time can be the rupture time or the time to a set strain such as 1 % (ll. 198–207). For each alloy a single curve of stress against LMP then holds for all temperatures; for titanium, carbon, chromium–molybdenum and stainless steels the values lie roughly between 20 and 28 thousand (ll. 208–249). To find a life, read the LMP at the service stress and rearrange:

$$
\log_{10}t_r=\frac{\mathrm{LMP}}{T}-C .
$$

See [[Larson-Miller Parameter]].

### Miner's rule for creep

Creep, like fatigue, accumulates damage, so the same rule applies (ll. 250–355). Under each condition of stress and temperature a fraction of the creep life is used, and failure is expected when

$$
\sum_i\frac{t_i}{t_{r,i}}=1 .
$$

Miner's rule is an assumption about adding damage fractions, not a rule special to fatigue or to creep (ll. 340–351). Because rupture life is exponential in temperature and a power law in stress, read or interpolate each $t_{r,i}$ on logarithmic axes. See [[Creep Miner's Rule]].

![[materials_creep_miner_budgets.png|900]]

## 4. Designing against creep

The design list follows from the mechanisms (ML14c, ll. 363–557):

- a microstructure that stays as designed at the service temperature: precipitates that neither coarsen nor dissolve, so the alloy stays in its two-phase field, and grain growth stopped by pinning carbides;
- a high melting point, which lowers $T/T_m$, perhaps below the 40 % threshold;
- solutes that slow self-diffusion;
- few grain boundaries, or boundaries aligned with the load so they carry no resolved shear: columnar grains, or no boundaries at all;
- dislocations pinned by precipitates or dispersoids so recovery is slow.

Creep is useful once, as **superplasticity** (ll. 558–722). A nanometre-grained microstructure, made by extreme deformation such as high-pressure torsion or equal-channel angular pressing with only slight recovery, has so many grain boundaries that, at slow strain rates, grain-boundary sliding gives elongations of 335–604 %, far beyond any Part 1 tensile test. Gas pressure can then blow a sheet into a complex shape in one step, the superplastic forming used for hollow titanium fan blades in [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]].

## 5. Oxidation

Oxidation is measured by weighing a sample in a furnace with a precision balance (ML15a, ll. 17–31). Oxidation adds oxygen to the solid, so the mass rises; a fall in mass means the oxide is volatile and is carrying metal away.

The key idea is that the oxide separates the reactants (ll. 32–62). Metal and oxygen react to form oxide between them, so further reaction needs metal or oxygen to cross that layer. The metal's reactivity sets the thermodynamics, the driving force; temperature and oxygen supply set the kinetics, through solid-state diffusion in the oxide. Ranking metals by the time to grow 100 μm of oxide at 70 % of their melting temperatures gives an order similar to the electrochemical series but not the same: gold never gets there, silver, aluminium, silicon nitride, silicon carbide and tin take very long, and tantalum, niobium, uranium, molybdenum and tungsten very little time (ll. 63–87). Where the order differs, kinetics dominates, so the oxide's structure is what matters.

The half-reactions are those of corrosion (ll. 88–137). At the metal–oxide interface the metal forms cations, $\mathrm{M\rightarrow M^{n+}+ne^-}$; at the oxide–gas interface oxygen takes up electrons, $\mathrm{O_2+4e^-\rightarrow2O^{2-}}$. If the oxide has vacancies on its cation sites, metal ions diffuse out and new oxide forms at the outer surface, burying a marker placed there at the start. If it has anion vacancies, oxygen ions diffuse in and new oxide forms at the metal, pushing the marker outwards. How defective the oxide is decides how fast it grows.

![[materials_oxide_growth.png|900]]

The weight gain follows one of three laws (ll. 138–170). It is linear,

$$
w=k_Lt,
$$

when the oxide is porous or cracked and does not protect, so the rate is set by the chemical reaction at an effectively bare surface: potassium and tantalum, the worst case. It is parabolic,

$$
w^2=k_pt+C,
$$

for a thick, coherent, adherent oxide, because the ions must diffuse through a layer that keeps thickening: copper and iron. The parabolic law follows from that picture. If growth is limited by diffusion across a scale of thickness $x$, the flux, and so the growth rate, is inversely proportional to the thickness:

$$
\frac{dx}{dt}=\frac{k}{x}.
$$

Separating variables,

$$
x\,dx=k\,dt,
$$

and integrating from $x_0$ at $t=0$,

$$
x^2=2kt+x_0^2,
$$

which, with weight gain proportional to thickness, is the parabolic law. Logarithmic growth,

$$
w=k_e\log\left(Ct+A\right),
$$

is fast at first and then almost stops, the signature of a very protective film, as on aluminium and chromium. Oxides are ceramics, and a mismatch in thermal expansion or lattice spacing with the metal makes them crack or spall, exposing fresh metal.

![[materials_oxidation_rate_laws.png|800]]

Chromium and aluminium protect because their oxides, chromia and alumina, are coherent, adherent and almost free of defects, so neither cations nor anions can get through (ll. 171–186). A little chromium is worse than none: it gives a mixed iron–chromium oxide that is defective and poorly adherent and can oxidise faster. Above about 12 % chromium a continuous chromia layer forms, the stainless-steel threshold of [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying#9. Stainless steels|M7]]. See [[Oxidation Rate Laws]].

### Oxidation of a turbine blade

The lecturer works a past-paper question with the examiner's marking notes (ll. 187–213): why does oxidation matter for a turbine blade, and how would you reduce it? It eats load-bearing metal, replacing it with oxide; it roughens the aerofoil and costs aerodynamic performance; spalled oxide is hard and brittle and erodes parts downstream when ingested. To reduce it, add chromium (and aluminium) for a coherent protective scale, lower the metal temperature with cooling and thermal barrier coatings, and apply protective coatings or deliberately thicken the oxide, as anodising does.

## 6. Oxidation, creep and fatigue together

At high temperature these processes combine (ML15b, ll. 126–165). Oxygen attacks grain boundaries ahead of a fatigue crack and forms brittle oxide there, which cracks, so it both starts fatigue cracks and raises $da/dN$. Because oxidation takes time, the effect is worse at low frequency: a few long cycles can grow a crack further per cycle than many fast ones, which give no time for oxygen to act. Creep-fatigue is time-dependent in the same way. Creep can relax the stress at a crack tip, but overall it accelerates fatigue by adding grain-boundary sliding. Slip-trace and orientation mapping of a disc alloy show cracks following grains oriented for easy slip (ll. 145–157). Paris constants measured quickly in air may therefore be unconservative at service temperature and frequency.

## 7. Alloys for high temperature

### Stainless steels

High-chromium austenitic stainless steels resist oxidation, but long exposure at temperature sensitises them, as welding does, by precipitating chromium carbides on the grain boundaries and leaving the boundaries short of chromium (ML15b, ll. 9–44). The cures are those of [[SESA2028 M3 - Corrosion, Wear and Surface Engineering#Intergranular corrosion and weld decay|M3]]: low-carbon grades such as 316L, or a stronger carbide former. Grain boundaries are the weak point at temperature, for creep and for oxidation alike, so alloy design turns to grain-boundary engineering: fewer boundaries, boundaries parallel to the load by directional solidification or none at all in single crystals, or boundaries pinned and serrated by fine carbides (ll. 45–59). Stainless steels serve to about 500 °C; beyond that they struggle (ll. 59–61).

### Nickel superalloys

Nickel superalloys grew out of austenitic stainless steel: metallurgists kept adding nickel and removing iron until there was no iron left (ML15b, ll. 62–68). The matrix, $\gamma$, is FCC nickel. Chromium gives corrosion and oxidation resistance; cobalt, molybdenum and tungsten give solid-solution strengthening, and tungsten also raises the melting point and slows self-diffusion, which helps creep (ll. 81–101). The main strengthener is $\gamma'$, the ordered intermetallic $\mathrm{Ni_3(Al,Ti)}$, whose amount is set by the aluminium and titanium content (ll. 86–90). Etched away from the matrix, it appears as a dense array of cubes, like the Giant's Causeway, at a very high volume fraction, with finer $\gamma'$ between them (ll. 69–81).

Three features suit $\gamma'$ to high temperature (ll. 90–97, 121–126). Its solvus, the temperature at which it dissolves, is close to the alloy's melting point. It is coherent with the matrix, so its interface energy is low and there is little drive to coarsen, the drive that ruins ordinary precipitates. And it gets stronger as the temperature rises. Dislocations therefore stay in the softer $\gamma$ channels between the cubes. Over long times under stress the cubes can join into plates, **rafting**, leaving continuous soft channels along which creep and cracks proceed, a form of degradation (ll. 106–126). See [[Gamma Prime Strengthening]].

## 8. Intermetallics, ceramics and coatings

### Intermetallics

If $\gamma'$ is so good at temperature, why not use intermetallics on their own (ML16a, ll. 1–13)? An intermetallic is an ordered compound of dissimilar elements; cementite is one (ll. 14–21). The ordering makes slip very difficult, so they are hard and strong; strong bonding gives melting points of 1000–2000 °C; open packing gives low density; and they are generally unreactive, so they resist oxidation and corrosion, with excellent high-temperature strength, creep resistance and stiffness (ll. 21–34). But they are brittle at low temperature: with no plastic flow there is no stress redistribution at a defect, so they are notch sensitive (ll. 34–48). Some conduct heat poorly, which creates hot spots that can overheat neighbouring parts, and they suffer thermal stresses when temperatures cycle (ll. 48–59). They are used where temperatures are high and steady: $\mathrm{Ni_3Al}$ for glass-making moulds, hot-forging dies and furnace parts, $\mathrm{Fe_3Al}$ for exhausts, heating elements and hot-corrosion applications (ll. 59–69). The one aerospace candidate is titanium aluminide, a mixture of TiAl and $\mathrm{Ti_3Al}$ whose lamellar form is tougher and more creep resistant and whose equiaxed form is more formable (ll. 69–76).

### Ceramics

Compared with metals, ceramics such as silicon nitride, silicon carbide and alumina are lighter, melt at much higher temperatures, are two or three times as stiff as steel, have very high yield stress and yield strain, but much lower fracture toughness and thermal expansion (ML16b, ll. 1–34). Their ionic and covalent bonds in low-symmetry crystals leave very few slip systems, so dislocations need very high temperatures to move: they are hard, brittle, chemically stable, and insulating, so they develop hot spots and are prone to thermal shock, like hot ovenware plunged into cold water (ll. 34–49).

They cannot be cast or rolled, so they are made from powder (ll. 50–96). A powder, held together by a binder of water or polymer that gives the green compact its strength, is pressed and sintered at high temperature and pressure. Atoms diffuse to the contacts, forming necks that become grain boundaries; larger grains grow at the expense of smaller ones; and continuous pores pinch off into isolated ones, often leaving some residual porosity. A liquid phase speeds sintering but can leave a glassy film on the grain boundaries with a low melting point, which lets even a ceramic creep. Strength is controlled by flaws (ll. 96–126): porosity, where 10 % porosity can halve the fracture strength and one large pore is far worse than the same volume of fine ones; inclusions; grains cracked by anisotropic thermal contraction; and surface damage. To strengthen a ceramic, reduce porosity and grain size: if pores are smaller than the grains, grain size governs, and if larger, porosity does. The crack path also matters, which is why fibres toughen [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|ceramic matrix composites]] (ll. 125–132). In practice ceramics carry structural loads mostly as coatings (ll. 133–138).

### Coatings

A **diffusion coating** interdiffuses with the substrate, for example aluminium into nickel to form a nickel aluminide with a composition gradient; an **overlay coating** is a separate layer deposited on top (ML16c, ll. 1–7). Chemical and physical vapour deposition build thin, exotic layers in vacuum, but only in small batches, at high cost and with imperfect composition control, because elements with different vapour pressures deposit at different rates (ll. 8–31). Plasma spraying and high-velocity oxy-fuel spraying partly melt a powder and fire it at the surface, where the droplets splat and pile up like mud thrown at a wall (ll. 31–54). They are quick, cheap and work for almost any composition, but need a line of sight, often robot handling, and give a porous, rough coating that can matter for fatigue; the substrate is first roughened by light peening with glass beads so the coating keys in.

See [[Thermal Barrier Coatings]].

## 9. Case study: the turbine blade

A turbine blade fits into the disc by a fir-tree root, whose notches make fatigue the concern there, at moderate temperature; along the aerofoil towards the tip the temperature, and the creep problem, increase (ML16d, ll. 1–13). Whittle's first engine needed a material to survive 650 °C at about 200 MPa; stainless steels could not, and the nickel–chromium alloy Nichrome, about 80 % nickel and 20 % chromium, became the ancestor of the superalloys (ll. 14–21).

Gas temperatures have since risen to above 1200 °C, beyond the melting point of the blade alloy, because three developments worked together (ll. 22–47). Cooling went from solid blades to convection-cooling holes and then film-cooling passages. Alloys improved in melting point and creep resistance. And the grain structure went from equiaxed to directionally solidified and then single crystal, which gives the best creep resistance. Higher gas temperature means a more efficient engine.

The blades are made by investment, or lost-wax, casting (ll. 48–84). A wax pattern of the blade, with silica cores where the cooling channels will be, is assembled with others on a tree with a runner system; repeated dipping in ceramic slurry and drying builds a shell; the wax is melted out in a furnace; and the molten alloy is poured in. The mould is then withdrawn slowly from the furnace so that solidification starts at the bottom and proceeds upwards. Without anything more this gives columnar grains aligned with the blade, a directionally solidified blade whose grain boundaries run parallel to the centrifugal stress. With a pigtail, a helical constriction, in the way, only one grain orientation survives to grow into the blade, which becomes a single crystal. The cores are dissolved out at the end. See [[Single Crystal Casting]].

Finally the blade is coated (ll. 85–126). On the single-crystal superalloy goes an intermetallic bond coat that eases the step from the metal's thermal expansion to the ceramic's through repeated heating and cooling; an oxide is deliberately grown on the bond coat, the thermally grown oxide; and on top goes a zirconia ceramic layer 100–400 μm thick, deposited by electron-beam physical vapour deposition or by spraying. The ceramic is an insulator, so the temperature falls steeply across it, and with internal cooling air the metal stays far cooler than the gas.

![[materials_tbc_temperature_profile.png|900]]

## Worked examples

All numbers recomputed in Python. ML14c promises worked creep problems in a later mini-lecture that is not among the recordings (ML14c, ll. 735–739); the calculations below are from tutorial MT5 and the past papers.

### How sensitive is creep?

Illustrative values: with $Q=280$ kJ/mol, typical of nickel self-diffusion, raising the temperature from 1000 K to 1010 K multiplies the creep rate by

$$
\exp\left[\frac{Q}{R}\left(\frac{1}{1000}-\frac{1}{1010}\right)\right]=\exp\left(33\,680\times9.90\times10^{-6}\right)=1.40,
$$

so 10 K costs 40 % of the life. With $n=5$, a 10 % rise in stress multiplies the rate by $1.1^5=1.61$. For stress relaxation with a relaxation time of 1000 h, after 500 h the stress has fallen to $e^{-0.5}=0.61$ of its initial value.

### Larson–Miller lives

Each life uses $\log_{10}t_r=\mathrm{LMP}/T-20$ with the LMP read from the alloy's master curve at the service stress:

| Question | Stress, temperature | LMP read | $t_r$ |
|---|---|---:|---:|
| Lecture example, S-590 alloy | 140 MPa, 800 °C (1073 K) | 24.0 × 10³ | 233 h |
| 2014-15 B1(iv), Ni superalloy | 500 MPa, 700 °C (973 K) | 26.4 × 10³ | 1.36 × 10⁷ h |
| 2015-16 B3(iv), Alloy 738 | 300 MPa, 785 °C (1058 K) | 25.0 × 10³ | 4,261 h |
| 2023-24 MQ2(ii)(d), steel bar | 500 MPa, 700 °C (973 K) | 22.2 × 10³ | 655 h |
| 2023-24 MQ2(ii)(d), steel bar | 250 MPa, 600 °C (873 K) | 24.3 × 10³ | 6.8 × 10⁷ h |

For the S-590 alloy, for instance,

$$
\log_{10}t_r=\frac{24\,000}{1073}-20=2.367,
\qquad
t_r=10^{2.367}=233\text{ h}.
$$

The life is exponential in the LMP: a read-off error of ±200 at 973 K changes it by a factor $10^{200/973}=1.6$. Always state the uncertainty and apply a safety factor; the 2015-16 marking scheme deducted a mark for leaving it out. The 2020-21 G92 question combines the LMP with Miner's rule over a flight cycle; see [[FEEG2005 Exam 2020-21 Solutions]].

The same equivalence underlies accelerated testing (illustrative): 1000 h at 900 K has $\mathrm{LMP}=900\times(20+3)=20\,700$, so it is matched by a 10-hour test at $20\,700/21=986$ K (713 °C), or would be by $10^5$ h of service at $20\,700/25=828$ K (555 °C).

### Creep life under changing conditions

The past papers apply Miner's rule to creep, interpolating rupture lives on logarithmic axes. The results, from the solution notes:

| Question | Conditions so far | Life used | Remaining life at final condition |
|---|---|---:|---:|
| 2013-14 B3(iv), SRR99 at 400 MPa | 500 h at 850 °C, 2100 h at 750 °C | 0.22 | 155 h at 1000 °C |
| 2016-17 A1(iv), Ti at 600 °C | 500 h at 325 MPa, 1100 h at 250 MPa | 0.86 | 1.9 h at 650 MPa (extrapolated) |
| 2017-18 A1(v), Ti at 550 °C | 750 h at 425 MPa, 21,100 h at 150 MPa | 0.53 | 68 h at 825 MPa (extrapolated) |
| 2021-22 MQ1(d), CM247LC, 1 % strain | 500 h at 250 MPa, 5000 h at 210 MPa | 0.41 | 70 h at 475 MPa |
| 2022-23 MQ2(v), martensitic stainless at 450 MPa | 85,000 h at 625 °C | 0.54 | 39,900 h at 680 °C |
| 2024-25 MQ2(c), CMSX-4 at 600 MPa | 1500 h at 1100 °C, 2000 h at 700 °C | 0.53 | 5,470 h at 800 °C |

The 2024-25 question also asks whether the data follow Arrhenius behaviour; fitting $\ln t_r$ against $1/T$ gives an apparent activation energy far below nickel self-diffusion, a sign that the mechanism changes over 600–1100 °C, so interpolate locally rather than trusting one global fit ([[FEEG2005 Exam 2024-25 Solutions]]).

## Transcript slips

> [!warning] Mini-lectures ML14a–ML16d
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML14a, l. 4 | "in lecture content block 4" | lecture content block 14 |
> | ML14a, ll. 104, 106 | "arhenius" | Arrhenius |
> | ML14a, ll. 124–125 | "my stress is a constant sort of threshold stress … times an exponential of minus t over tor" | $\sigma=\sigma_0e^{-t/\tau}$, with $\sigma_0$ the initial stress and $\tau$ the relaxation time (l. 128) |
> | ML14b, l. 9 | "the Burgess vector and the Lyon vector" | the Burgers vector and the line vector |
> | ML14b, l. 21 | "climb past the article" | climb past the particle |
> | ML14b, l. 149 | "grain boundaries that experience shit" | that experience shear (corrected at l. 150) |
> | ML14c, l. 46 | rupture time "A sigma to the N" | $t_r\propto\sigma^{-n}$: a higher stress shortens the life |
> | ML14c, l. 235 | "chromolydium steel" | chromium–molybdenum steel |
> | ML14c, l. 342 | "minus rule" | Miner's rule |
> | ML14c, l. 367 | "trying to desire something" | trying to design something |
> | ML14c, ll. 735–739 | the problem calculations "will be mini block 14D" | no ML14d recording exists; the worked creep problems are in tutorial MT5 |
> | ML15a, l. 14 | "corrosion isn't essentially an oxidation process" | corrosion is essentially an oxidation process in an aqueous environment |
> | ML15a, l. 52 | "the amount of thermology around" | the amount of thermal energy |
> | ML15a, l. 131 | "the anide reaction" | the cathodic reaction |
> | ML15a, l. 152 | "a non-productive oxide layer" | a non-protective oxide layer |
> | ML15a, l. 185 | "because you can put enough in" | because you have not put enough in |
> | ML15a, l. 201 | "spools off" | spalls off |
> | ML15b, l. 35 | "into granular attack" | intergranular attack |
> | ML15b, ll. 41–42 | stabilise with "molybdenum or vanadium" | the usual stabilising additions are titanium or niobium (ML4a, l. 79) |
> | ML15b, l. 89 | "ni3 ti al" | $\mathrm{Ni_3(Al,Ti)}$ |
> | ML15b, l. 92 | "it's solvers" | its solvus |
> | ML15b, l. 152 | "field beach and gun sem" | field-emission-gun SEM |
> | ML16a, l. 44 | "very not sensitive" | very notch sensitive |
> | ML16a, l. 61 | "NO3AL" | $\mathrm{Ni_3Al}$ |
> | ML16a, l. 62 | "superhalos", "hot forging dyes" | superalloys, hot-forging dies |
> | ML16c, l. 4 | nickel aluminide "onto an aluminium substrate" | onto a nickel substrate (aluminium diffused into nickel) |
> | ML16c, ll. 9, 17, 23 | "plasma vapor deposition" | physical vapour deposition (sputtering) |
> | ML16c, l. 41 | HVOF gives "plasma and shock waves" | HVOF uses a combustion flame; plasma spraying is the separate process of l. 42 |
> | ML16c, l. 59 | "fiji 205" | FEEG2005 |
> | ML16d, ll. 40, 45, 79 | "crepe resistance" | creep resistance |
> | ML16d, l. 48 | lost wax "which the Incare Empire first developed" | lost-wax casting is far older than the Inca, going back thousands of years in the Near East |
> | ML16d, ll. 70, 81 | "multiple tone constriction" | multiple-turn constriction (the pigtail grain selector) |
> | ML16d, l. 75 | "the blades are all parallel to the stress" | the grains are all parallel to the stress |
> | ML16d, l. 114 | "EPPVD" | EB-PVD |
> | ML16d, l. 124 | "the substrate says coal" | the substrate stays cool |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]
- Concepts: [[Creep Curve and Mechanisms]] · [[Larson-Miller Parameter]] · [[Creep Miner's Rule]] · [[Oxidation Rate Laws]] · [[Gamma Prime Strengthening]] · [[Single Crystal Casting]] · [[Thermal Barrier Coatings]]
- Related: [[Miner's Rule]] · [[Paris Law]] · [[MMC vs CMC]] · [[Stainless Steel Classes]] · [[Hall-Petch Relation]] · [[Spinning Disc Stress]] (disc stresses)
- Elsewhere: [[Turbine Entry Temperature and Blade Cooling]] · [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat|Brayton cycle]]
- Tutorial: [[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]] · past papers: [[SESA2028 Past Paper Map]]

## Sources

- High temperature materials 2025 slides
- Mini-lecture transcripts ML14a (creep fundamentals), ML14b (creep mechanisms), ML14c (creep lifing approaches), ML15a (oxidation processes), ML15b (engineering high-temperature alloys), ML16a (intermetallics), ML16b (ceramics), ML16c (high-temperature coatings), ML16d (turbine blade case study)
- Creep calculations from tutorial MT5 and the exam solution notes; Larson–Miller lives and illustrative numbers recomputed in Python

## Self-study tasks

ML14a (ll. 9–16) opens with a pause-and-think exercise: list the properties a high-temperature material needs. ML15a (ll. 187–213) sets a past-paper question on oxidation of a turbine blade and gives the marking notes. ML15b (ll. 102–105) says you may be asked to explain a creep-resistant alloy strategy element by element. ML14c points to worked creep problems, which are in tutorial MT5.

### Core

- [ ] List the properties a high-temperature material needs (ML14a, ll. 9–62). → [[#1. Creep]]
- [ ] Explain the three creep mechanisms and the shape of the creep curve (ML14a, ll. 130–185; ML14b). → [[#2. Creep mechanisms]]
- [ ] Derive the Larson–Miller parameter and use it for a life (ML14c, ll. 111–249). → [[#The Larson–Miller parameter]] · [[#Larson–Miller lives]]
- [ ] Explain why oxidation matters for a turbine blade and how to reduce it (ML15a, ll. 187–213). → [[#Oxidation of a turbine blade]]
- [ ] Explain a creep-resistant superalloy strategy, element by element (ML15b, ll. 62–126). → [[#Nickel superalloys]]
- [ ] Tutorial MT5 Q1 and Q2. → [[SESA2028 Materials Tutorial MT5 - High Temperature Materials Solutions]]

### Further practice

- [ ] Derive the parabolic oxidation law and explain where new oxide grows for cation- and anion-defective scales (ML15a, ll. 88–170). → [[#5. Oxidation]]
- [ ] Describe how a single-crystal, cooled, coated turbine blade is made and why each step helps (ML16d). → [[#9. Case study: the turbine blade]]
- [ ] Work the creep Miner's-rule past papers in the table, starting with 2013-14 B3(iv). → [[#Creep life under changing conditions]]
