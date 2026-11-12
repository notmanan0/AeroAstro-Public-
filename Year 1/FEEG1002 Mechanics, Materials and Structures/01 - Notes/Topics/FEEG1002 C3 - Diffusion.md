---
title: "FEEG1002 C3 - Diffusion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 18
tags: [feeg1002, materials, diffusion, ficks-law, arrhenius, activation-energy]
aliases: ["Materials Lecture 3", "Diffusion in solids", "Fick's first law"]
date: 2026-11-05
status: lectured
coverage: "Materials L3 (15 Oct 2024, ll. 1–726): diffusion mechanisms (vacancy, interstitial, atom exchange, grain boundary), the Cu–Ni diffusion couple, flux and steady-state diffusion, Fick's first law, palladium-membrane hydrogen purification, effects of structure and temperature, the Arrhenius equation and the time–temperature trade-off in heat treatment; slide deck 04 in full. Only steady-state diffusion was covered; Fick's second law was not."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]"]
next_topics: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
key_concepts: ["[[Fick's Laws and Arrhenius Diffusion]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 04 - Diffusion.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 3 - Materials Diffusion version 1.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf"]
---

# FEEG1002 C3 - Diffusion

> [!abstract] Summary
> Diffusion is material transport by atomic motion. In solids atoms move by jumping into vacancies, by squeezing through the interstitial gaps between larger atoms, or along grain boundaries, and each route has its own activation energy. At steady state the flux of atoms through a plate is proportional to the concentration gradient, $J=-D\,dC/dx$ (Fick's first law). The diffusion coefficient rises exponentially with absolute temperature, $D=D_0\exp(-Q/RT)$ (the Arrhenius equation), so a modest rise in temperature can speed diffusion by orders of magnitude.

> [!summary]- Exam use: quick path
> - **Use it when:** you are asked which mechanism is faster, to compute a steady-state flux or mass transferred through a wall, to find $D$ at a new temperature, or to extract $Q$ from two values of $D$.
> - **Assumptions:** steady state (concentrations on both faces held fixed, so the profile through the wall is linear); $T$ in kelvin; $R=8.314$ J mol⁻¹ K⁻¹ with $Q$ in J/mol.
> - **Method:** 1. Gradient: $dC/dx=(C_A-C_B)/(x_A-x_B)$. 2. Flux: $J=-D\,dC/dx$ (positive towards low concentration). 3. Mass through area $A$ in time $t$: $M=JAt$. 4. For a new temperature: $D_2=D_1\exp[-(Q/R)(1/T_2-1/T_1)]$. 5. For $Q$: $Q=R\ln(D_2/D_1)/(1/T_1-1/T_2)$.
> - **Common mistakes:** using °C in the Arrhenius exponent; treating the diffusion coefficient as negative (the minus sign in Fick's law says the flow is down the gradient, and $D$ itself is always positive).
> - **Practise:** [[#Worked example - hydrogen through a palladium membrane]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]] Q8–Q9

The pin-and-ball pictures of [[FEEG1002 C2 - Crystal Structures and Crystallography|C2]] make atoms look fixed, but above absolute zero every atom vibrates about its lattice site, and now and then one gathers enough energy to jump to a neighbouring site. Each jump is random, but where there is a difference in concentration more atoms jump from the crowded side to the sparse side than the other way, and the net result is a steady drift of material down the concentration gradient (L3, ll. 47–73).

That drift is how much of materials processing works. Carburising a steel gear pushes carbon into its surface to harden it. Annealing a cold-worked metal lets atoms rearrange into new, soft grains ([[FEEG1002 C5 - Strengthening Mechanisms and Annealing|C5]]). Precipitation hardening relies on solute atoms gathering into tiny particles ([[FEEG1002 C7 - Steels and Precipitation Hardening|C7]]), and creep of a hot turbine blade is partly atoms diffusing under stress ([[FEEG1002 C9 - Fatigue, Creep and Corrosion|C9]]). The process going on in a material is very often either dislocation motion or diffusion (L3, ll. 84–91).

Two things control the rate. The structure decides how easy each jump is: a small atom slipping between large ones moves far more easily than a large atom waiting for a vacancy. The temperature decides how often an atom has the energy to make the jump, and because that depends exponentially on temperature, so does the rate of diffusion.

---

## 1. Diffusion mechanisms

**Diffusion** is material transport by atomic motion (slide "Diffusion"; L3, l. 93). In a solid it happens in three main ways (L3, ll. 112–211).

In **vacancy diffusion** an atom jumps into a neighbouring lattice site that happens to be empty. Real crystals are never perfect: solidification leaves some sites unoccupied, and these **vacancies** give atoms a route to move. The atom and the vacancy swap places, so atoms flow one way and vacancies the other. Vacancy diffusion covers **self-diffusion** (atoms of the host moving through their own lattice) and **substitutional** solute diffusion (solute atoms of similar size that sit on lattice sites). Its rate depends on how many vacancies there are (L3, ll. 158–176).

In **interstitial diffusion** a small solute atom, such as carbon, nitrogen or hydrogen in iron, moves from one interstitial site to the next through the gaps between the much larger host atoms. There are always plenty of interstitial sites, so an interstitial atom never has to wait for a vacancy to appear next to it, and interstitial diffusion is much faster than vacancy diffusion (slide "Diffusion Mechanisms"; L3, ll. 177–202). Hydrogen's ability to diffuse into steel this way is a nuisance, because it embrittles it.

In **atom exchange** two neighbouring atoms swap places directly (L3, ll. 437–492). Direct exchange needs a much higher activation energy than a vacancy jump, so vacancy diffusion dominates.

![[m3_diffusion_mechanisms.png|900]]

### Interdiffusion: the diffusion couple

In a block of pure copper pressed hard against a block of pure nickel and held hot, copper atoms move into the nickel and nickel atoms into the copper over time, until there is pure copper at one end, pure nickel at the other and a band of copper–nickel alloy between (slide "Interdiffusion or Impurity Diffusion"; L3, ll. 212–241). Atoms migrate from regions of high concentration to regions of low concentration. This **interdiffusion** (or impurity diffusion) takes time; it is not instantaneous, and it is the concentration gradient that drives it.

### Activation energy and the structure of the path

An atom sitting at its equilibrium spacing is in an energy minimum ([[FEEG1002 C1 - Atoms and Bonding|C1]]). To jump to the next site it must squeeze past its neighbours, which means climbing over an energy barrier, the **activation energy** $Q$ (L3, ll. 424–430). The lower the barrier, the easier the path and the faster the diffusion. The structure decides the barrier (slide "Effects of Structure on Diffusion"). **Volume diffusion**, through the bulk of the crystal by vacancy jumps or exchange, has a high activation energy and a low rate, limited by the number of vacancies. **Grain-boundary diffusion** is faster. A metal is polycrystalline, made of many crystals (grains) joined at grain boundaries where the atoms are disordered, so a grain boundary behaves like a large set of vacancies with a much lower activation energy (L3, ll. 493–545). **Interstitial diffusion** is much faster than vacancy diffusion, because the interstices are numerous, although they are small.

Diffusion is promoted by open crystal structures with low packing density, by low melting points (weaker bonds, so lower barriers) and by small diffusing atoms. BCC iron, with a packing factor of 0.68 against 0.74 for FCC, lets carbon diffuse faster than FCC iron at the same temperature (L3, ll. 557–576).

## 2. Flux and steady-state diffusion

### Flux

To put a number on the rate of diffusion, consider a thin metal plate, such as part of a vessel wall, with gas at high pressure on one side and low pressure on the other (L3, ll. 242–299). Gas atoms dissolve into the high-pressure face and diffuse through to the low-pressure face. The quantity of interest is the **flux** $J$, the mass (or number of atoms) $M$ diffusing through a unit area of the plate per unit time:

$$
J=\frac{M}{At}
$$

or, in differential form,

$$
J=\frac{1}{A}\frac{dM}{dt}
$$

where $A$ is the area and $t$ the time. Dividing by area and time is natural: a larger plate passes more gas, and so does a longer time. Units are kg m⁻² s⁻¹ or atoms m⁻² s⁻¹. The flux can be counted in diffusing atoms or, equally, in vacancies moving the opposite way.

### Steady state

If the pressures (and so the concentrations of gas just inside each face) are held fixed and the plate does not change, the profile settles and the flux no longer changes with time. This is **steady-state diffusion** (L3, ll. 300–326):

$$
\frac{dJ}{dt}=0
$$

At steady state, the same amount of gas must cross every slice of the plate per second, otherwise gas would pile up somewhere and the concentrations would change. So $J$ is also the same at every depth $x$, and (with $D$ constant) the concentration gradient is the same everywhere: the concentration profile through the plate is a straight line from $C_A$ on the high-concentration face at $x_A$ to $C_B$ on the low face at $x_B$. Its gradient is

$$
\frac{dC}{dx}=\frac{\Delta C}{\Delta x}=\frac{C_A-C_B}{x_A-x_B}
$$

![[m3_steady_state_profile.png|900]]

### Fick's first law

Experiments show that the flux is proportional to the concentration gradient (slide "Steady state diffusion: Fick's First law"; L3, ll. 327–350):

$$
\boxed{J=-D\frac{dC}{dx}}
$$

This is **Fick's first law**. $D$ is the **diffusion coefficient** (m²/s), a positive property of the diffusing species, the host and the temperature. The minus sign appears because atoms flow down the concentration gradient: where $C$ falls with increasing $x$, $dC/dx$ is negative and the flux is positive, in the $+x$ direction. With $J$ in atoms m⁻² s⁻¹ the concentration is in atoms/m³; with $J$ in kg m⁻² s⁻¹ it is in kg/m³.

For a plate at steady state, combining the linear gradient with Fick's law, the mass passing through area $A$ in time $t$ is

$$
M=JAt=D\frac{C_A-C_B}{x_B-x_A}At
$$

Doubling the concentration difference or halving the thickness doubles the flow; doubling $D$ also doubles it.

### Application: purifying hydrogen

Hydrogen made industrially is contaminated with CO₂, H₂O and CH₄. A thin palladium membrane separates them (slide "Steady-state Diffusion and Sustainable Energy"; L3, ll. 351–400). The impure gas is held at high pressure on one side and pure hydrogen at low pressure on the other. Hydrogen molecules are adsorbed on the palladium surface, dissociate into atoms, dissolve and diffuse through the metal, then recombine into H₂ and desorb on the far side. The larger molecules cannot pass. Because both pressures are maintained, this is steady-state diffusion and Fick's first law gives the production rate directly.

## 3. What controls the diffusion coefficient

Diffusion coefficients (Callister's data, m²/s) show the effects of mechanism, temperature and crystal structure separately (slide "Factors that Influence Diffusion"; L3, ll. 598–647):

| Effect | Diffusing species and host | Temperature | $D$ (m²/s) |
|---|---|---:|---:|
| mechanism | Fe in α-Fe (vacancy) | 500 °C | 3.0 × 10⁻²¹ |
| mechanism | C in α-Fe (interstitial) | 500 °C | 2.4 × 10⁻¹² |
| temperature | Fe in α-Fe (vacancy) | 500 °C | 3.0 × 10⁻²¹ |
| temperature | Fe in α-Fe (vacancy) | 900 °C | 1.8 × 10⁻¹⁵ |
| packing | C in α-Fe (BCC) | 900 °C | 1.7 × 10⁻¹⁰ |
| packing | C in γ-Fe (FCC) | 900 °C | 5.9 × 10⁻¹² |

At 500 °C interstitial carbon diffuses $8\times10^8$ times faster than iron diffusing through its own lattice by vacancies. Raising the temperature of iron self-diffusion from 500 °C to 900 °C increases $D$ by a factor of $6\times10^5$. At 900 °C carbon diffuses 29 times faster in the open BCC structure than in close-packed FCC. (α-Fe is BCC ferrite and γ-Fe is FCC austenite, [[FEEG1002 C2 - Crystal Structures and Crystallography#4. Polymorphism|C2]].)

### The Arrhenius equation

The temperature dependence of the diffusion coefficient follows an **Arrhenius equation** (slide "Effect of Temperature on Diffusion"; L3, ll. 648–688):

$$
\boxed{D=D_0\exp\left(-\frac{Q}{RT}\right)}
$$

where $D_0$ is a constant for a given material state (m²/s), $Q$ is the activation energy (J/mol), $R=8.314$ J mol⁻¹ K⁻¹ is the gas constant and $T$ is the absolute temperature in kelvin. The form is the same as for the rate of a chemical reaction, and it applies wherever a process is thermally activated: recrystallisation ([[FEEG1002 C5 - Strengthening Mechanisms and Annealing|C5]]), ageing ([[FEEG1002 C7 - Steels and Precipitation Hardening|C7]]) and creep ([[FEEG1002 C9 - Fatigue, Creep and Corrosion|C9]]). It need not be memorised, but it must be recognised and used whenever diffusion and temperature appear together (L3, ll. 649–655).

The exponential has a physical meaning. $Q/(RT)$ compares the height of the energy barrier with the thermal energy available, and $\exp(-Q/RT)$ is the fraction of attempts at a jump that succeed. Raise $T$ and a much larger fraction of atoms have enough energy to jump the barrier.

### Working with the Arrhenius equation

Taking natural logarithms turns it into a straight line:

$$
\ln D=\ln D_0-\frac{Q}{R}\cdot\frac1T
$$

A plot of $\ln D$ against $1/T$ is a straight line of slope $-Q/R$ and intercept $\ln D_0$. Write this at two temperatures $T_1$ and $T_2$:

$$
\ln D_1=\ln D_0-\frac{Q}{RT_1}
$$

$$
\ln D_2=\ln D_0-\frac{Q}{RT_2}
$$

Subtract the first from the second; $\ln D_0$ cancels:

$$
\ln D_2-\ln D_1=-\frac QR\left(\frac1{T_2}-\frac1{T_1}\right)
$$

$$
\ln\frac{D_2}{D_1}=\frac QR\left(\frac1{T_1}-\frac1{T_2}\right)
$$

Rearranged, this gives the activation energy from two measurements,

$$
\boxed{Q=\frac{R\ln(D_2/D_1)}{1/T_1-1/T_2}}
$$

or $D$ at a new temperature from one measurement and $Q$,

$$
\boxed{D_2=D_1\exp\left[-\frac QR\left(\frac1{T_2}-\frac1{T_1}\right)\right]}
$$

![[m3_arrhenius_plot.png|900]]

A large activation energy gives a steep line: iron self-diffusion ($Q\approx251$ kJ/mol) speeds up far more with temperature than interstitial carbon ($Q\approx80$ kJ/mol), although at every temperature shown carbon is still much faster.

> [!warning] Kelvin, and the factor of two that is not
> The exponent uses absolute temperature. Doubling a temperature in °C does not double $T$: going from 450 °C to 900 °C raises $T$ from 723 K to 1173 K, a factor of 1.62, but it raises the diffusion coefficient of carbon in α-iron by a factor of about 165. Nothing about diffusion scales linearly with temperature (Tutorial Sheet 1, Q8b).

### Time against temperature in heat treatment

Heat treatments depend on diffusion, and heating is expensive. The same amount of atomic movement can be had by holding at a high temperature for a short time or at a lower temperature for longer, for example five minutes against an hour or two, and the choice is an economic one (L3, ll. 689–702). A rough guide to the trade-off: $D$ has units of m²/s, so the only length that can be built from $D$ and the time $t$ is $\sqrt{Dt}$, and the distance atoms spread scales with it. To get the same spread at a new temperature the product $Dt$ must stay the same,

$$
D_1t_1=D_2t_2
$$

$$
t_2=t_1\frac{D_1}{D_2}
$$

so the time needed falls in proportion as $D$ rises.

---

## Worked examples

### Worked example - hydrogen through a palladium membrane

A palladium sheet 5 mm thick with an area of 0.20 m² is used to purify hydrogen at 600 °C. The hydrogen concentrations just inside the high- and low-pressure faces are held at 2.4 and 0.6 kg/m³, and the diffusion coefficient of hydrogen in palladium at 600 °C is $1.7\times10^{-8}$ m²/s. How much hydrogen passes through per hour?

Steady state is assumed, because both concentrations are held fixed, so the profile is linear. Take $x$ from the high-pressure face. The gradient is

$$
\frac{dC}{dx}=\frac{0.6-2.4}{0.005-0}=-360\ \mathrm{kg/m^4}
$$

Fick's first law gives the flux:

$$
J=-D\frac{dC}{dx}=-1.7\times10^{-8}\times(-360)=6.12\times10^{-6}\ \mathrm{kg\,m^{-2}\,s^{-1}}
$$

positive, so the flow is from the high- to the low-pressure side. In one hour through the whole sheet:

$$
M=JAt=6.12\times10^{-6}\times0.20\times3600=4.4\times10^{-3}\ \mathrm{kg}
$$

about 4.4 g of pure hydrogen per hour.

### Worked example - activation energy from two diffusion coefficients

For iron diffusing in α-iron, $D=3.0\times10^{-21}$ m²/s at 500 °C and $1.8\times10^{-15}$ m²/s at 900 °C (slide data). Find the activation energy, then estimate $D$ at 700 °C.

Convert to kelvin: $T_1=773$ K and $T_2=1173$ K. Then

$$
\ln\frac{D_2}{D_1}=\ln\frac{1.8\times10^{-15}}{3.0\times10^{-21}}=\ln(6.0\times10^5)=13.30
$$

$$
\frac1{T_1}-\frac1{T_2}=\frac1{773}-\frac1{1173}=4.41\times10^{-4}\ \mathrm{K^{-1}}
$$

$$
Q=\frac{8.314\times13.30}{4.41\times10^{-4}}=2.51\times10^5\ \mathrm{J/mol}=251\ \mathrm{kJ/mol}
$$

At 700 °C ($T=973$ K), working from the 500 °C value:

$$
D=3.0\times10^{-21}\exp\left[-\frac{251\,000}{8.314}\left(\frac1{973}-\frac1{773}\right)\right]
$$

$$
D=3.0\times10^{-21}\exp(8.03)=9.1\times10^{-18}\ \mathrm{m^2/s}
$$

> [!check] Against the table
> Callister tabulates $Q=251$ kJ/mol and $D_0=2.8\times10^{-4}$ m²/s for iron in α-iron, and $2.8\times10^{-4}\exp(-251\,000/(8.314\times973))=9.4\times10^{-18}$ m²/s at 700 °C. The 3 % difference comes from the two-figure rounding of the slide values.

### Worked example - shortening a carburising treatment

Carbon diffuses in FCC iron with $Q=148$ kJ/mol. A carburising treatment takes 10 hours at 900 °C. Roughly how long would the same case depth take at 1000 °C?

The ratio of diffusion coefficients is

$$
\frac{D_{1000}}{D_{900}}=\exp\left[-\frac{148\,000}{8.314}\left(\frac1{1273}-\frac1{1173}\right)\right]=\exp(1.192)=3.29
$$

and keeping $Dt$ constant,

$$
t_{1000}=10\times\frac{1}{3.29}=3.0\ \mathrm{h}
$$

A 100 °C rise cuts the time by more than two thirds, at the cost of a hotter furnace.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C2 - Crystal Structures and Crystallography]] · Next: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]
- Concept: [[Fick's Laws and Arrhenius Diffusion]]
- Worked sheet: [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]] (Q8–Q9) · Formula list: [[FEEG1002 Formula Sheet]]
- The Arrhenius form again: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Recrystallisation as a thermally activated process|C5]] (recrystallisation) · [[FEEG1002 C7 - Steels and Precipitation Hardening#Ageing temperature and time|C7]] (ageing) · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Steady-state creep rate|C9]] (creep)
- Year 2: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]] (diffusion-controlled creep and oxidation)

## Sources

- `FEEG1002 Lecture 3 - Materials Diffusion version 1.txt` (L3, 15 Oct 2024): introduction and exam framing (ll. 36–91), mechanisms (ll. 92–211), the diffusion couple (ll. 212–241), flux and steady state (ll. 242–326), Fick's first law (ll. 327–350), the palladium membrane (ll. 351–406), structure effects and the student demonstrations (ll. 407–576), Callister's diffusion data (ll. 598–647), the Arrhenius equation (ll. 648–688), heat-treatment trade-off (ll. 689–702), learning outcomes (ll. 703–726).
- `Lecture 04 - Diffusion.pdf` (slide deck 04): mechanisms, interdiffusion, flux, steady state, Fick's first law, hydrogen purification, effects of structure, the table of diffusion coefficients, the Arrhenius equation. Data and figures after Callister.
- `Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf`: Q8–Q9.
- The palladium example uses Callister's data for hydrogen in palladium; the two-temperature form of the Arrhenius equation and the $Dt$ scaling are not on the slides and are derived here.

## Self-study tasks

### Core

- [ ] Tutorial 1, Q8a: which is faster, hydrogen through steel or silicon through aluminium? → [[#1. Diffusion mechanisms]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q8 - Diffusion]]
- [ ] Tutorial 1, Q8b: does doubling the carburising temperature double the carbon concentration at depth? → [[#Working with the Arrhenius equation]] · [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q8 - Diffusion]]
- [ ] Tutorial 1, Q9: size of the octahedral interstitial site in BCC iron and whether carbon fits. Target $2r_i=0.037$ nm. → [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q9 - Carbon in a BCC interstitial site]]
- [ ] Calculate a steady-state flux and the mass transferred, the calculation promised for the tutorial and quizzes (L3, ll. 405–406, 722–724). → [[#Worked example - hydrogen through a palladium membrane]]
- [ ] Use the Arrhenius equation to find $D$ at a new temperature and $Q$ from two values (learning outcome 4, L3, ll. 720–721). → [[#Worked example - activation energy from two diffusion coefficients]]

### Further practice

- [ ] Rank vacancy, interstitial, grain-boundary and atom-exchange diffusion by rate and explain each in terms of activation energy (learning outcome 1, L3, ll. 707–712). → [[#Activation energy and the structure of the path]]
- [ ] Plot $\ln D$ against $1/T$ for the three systems in the table and read off $Q$ from the slopes (suggested, not lecturer-set). → [[#Working with the Arrhenius equation]]

## Transcript and slide slips

> [!warning] Transcript and slide slip: the sign of D (L3, l. 341; slide "Fick's First law")
> Where: [[#Fick's first law]].
>
> The diffusion coefficient is said to be negative ("our diffusion coefficient, that's negative"), and the slide has "−ve D as direction of diffusion is down the gradient". $D$ is always positive. The minus sign belongs to the equation $J=-D\,dC/dx$ and makes the flux point down the concentration gradient, which is the explanation given straight afterwards (ll. 342–343).

> [!warning] Transcript slips (L3, ll. 554–555 and 630–637)
> Where: [[#Activation energy and the structure of the path]] · [[#3. What controls the diffusion coefficient]].
>
> Interstitial diffusion is said to be faster "because those vacancies are always readily available"; it is the interstitial sites that are always available. The 900 °C values 1.7 × 10⁻¹⁰ and 5.9 × 10⁻¹² m²/s are read out as "body-centred cubic iron" and "gamma iron"; they are for carbon diffusing in BCC and FCC iron, as the slide says. The 500 °C values at ll. 600–606 are given without their temperature, which is on the slide.
