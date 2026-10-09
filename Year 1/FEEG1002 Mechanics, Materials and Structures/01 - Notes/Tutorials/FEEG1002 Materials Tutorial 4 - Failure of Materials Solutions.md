---
title: "FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, fracture, fatigue, creep, corrosion]
sheet: "Materials Tutorial Sheet 4"
theory_notes: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]", "[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
key_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Ductile-to-Brittle Transition]]", "[[S-N Curves and Paris Law]]", "[[Creep]]", "[[Galvanic Corrosion and Passivation]]"]
status: complete
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 04 - Failure of Materials.pdf"]
---

# FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions

> [!abstract] Sheet Info
> Seven questions on DBTT, Griffith/LEFM, fatigue graph reading, creep-rate extrapolation and corrosion protection. Q3's “1.6 mm internal crack” is treated as total length $2a$, consistent with the lecture convention.

## Theory Links
- [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion]]

---

## Q1: Toughness versus temperature
### (a) Sketch
- **Stainless steel (FCC)**: relatively high toughness across -100 to 400°C; no sharp transition.
- **Pure iron (BCC)**: low lower-shelf toughness at low temperature, a steep ductile-to-brittle transition, then a high upper shelf.
- **Magnesium (HCP)**: limited easy slip at low temperature gives low toughness; additional thermally activated slip raises toughness with temperature, qualitatively transition-like.

### (b) Mechanism
FCC has many close-packed slip systems, so yielding/plastic crack-tip blunting remains easier at low temperature. BCC has no close-packed plane and HCP has too few independent easy systems; their slip stress rises as temperature falls. When yield stress exceeds cleavage/fracture stress, brittle failure precedes plasticity.

## Q2: Griffith flaw in fused silica
Given $\gamma=4.32$ J/m², $E=70000$ MPa $=70\times10^9$ Pa, $\sigma=35$ MPa:
$$\sigma_f=\sqrt{\frac{2E\gamma}{\pi a}}\quad\Rightarrow\quad a=\frac{2E\gamma}{\pi\sigma_f^2}$$
$$a=\frac{2(70\times10^9)(4.32)}{\pi(35\times10^6)^2}=\boxed{1.57\times10^{-4}\ \text m=0.157\ \text{mm}}$$

Here $a$ is the half-length of a central crack, so the corresponding total crack length is $2a=\boxed{0.314\ \text{mm}}$.

## Q3: Nuclear pressure-vessel steel
Detection threshold: internal total crack length $2a=1.6$ mm, so $a=0.8$ mm. With $Y=1$ as stated/implicit:
$$\sigma_f=\frac{K_C}{\sqrt{\pi a}}=\frac{65}{\sqrt{\pi(0.8\times10^{-3})}}=\boxed{1.30\ \text{GPa}}$$

This exceeds the yield strength 375 MPa. The plate therefore reaches **general yielding first**, not LEFM fast fracture at 1.30 GPa. Assumptions: Mode I, central/infinite-plate idealisation, $Y=1$, crack length means $2a$, no residual stress, room-temperature $K_C$, and linear elasticity up to the comparison. Once widespread yielding occurs, the $K$ result is outside strict validity.

> [!note] If 1.6 mm were defined as $a$ rather than $2a$, the LEFM value would be 917 MPa; the conclusion (yield first) is unchanged.

## Q4: Safety factor for the pressure vessel
A nuclear pressure vessel must be designed to the applicable pressure-vessel/fracture-control code; one should not choose a single ad-hoc number. For the classroom comparison, a conservative yield-based factor of about **3–4** is defensible for high consequence and uncertainty:
$$\sigma_{allow}=\frac{375}{3\text{ to }4}=125\text{ to }93.8\ \text{MPa}$$
and the design also needs a separate fracture margin, proof testing, NDE probability-of-detection basis, fatigue growth allowance, residual-stress assessment and inspection interval.

## Q5: S-N curve
From the supplied graph:

| Requested quantity | Approximate reading |
|---|---:|
| fatigue limit | $\boxed{200\ \text{MPa}}$ |
| life at 280 MPa | $\boxed{\sim1.5\times10^5\ \text{cycles}}$ |
| life at 400 MPa | $\boxed{1.0\times10^4\ \text{cycles}}$ |
| fatigue strength at 30,000 cycles | $\boxed{\sim350\ \text{MPa}}$ |
| fatigue strength at 200,000 cycles | $\boxed{\sim270\ \text{MPa}}$ |

These are graph readings, not exact analytic values.

## Q6: Steady-state creep
### (a) Form of the rate law
$$\dot\varepsilon=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right)$$
- $\sigma^n$ captures mechanism-dependent sensitivity to driving stress;
- the Arrhenius exponential describes thermally activated diffusion/dislocation processes;
- $K_2$ contains material and unit-dependent constants.

### (b) Rate at 1123 K and 25 MPa
At the same $T_1=1273$ K, divide the two data equations:
$$\frac{10^{-4}}{10^{-6}}=\left(\frac{15}{4.5}\right)^n\Rightarrow n=\frac{\ln100}{\ln(15/4.5)}=3.825$$

Avoid finding $K_2$ by forming a ratio to the 15 MPa datum:
$$\frac{\dot\varepsilon_2}{10^{-4}}=\left(\frac{25}{15}\right)^n\exp\left[-\frac{Q_c}{R}\left(\frac1{1123}-\frac1{1273}\right)\right]$$

$$\boxed{\dot\varepsilon_2=2.28\times10^{-5}\ \text{s}^{-1}}$$
Higher stress accelerates creep, but the 150 K temperature reduction dominates and makes the result lower than $10^{-4}$ s$^{-1}$.

## Q7: Corrosion
### Titanium: active standard potential but inert in seawater
Titanium rapidly forms a dense, adherent TiO$_2$ passive film. The standard electrode potential describes ideal bare active metal; the seawater galvanic series reflects the actual passive surface, which behaves much more noble/inert.

### Buried steel pipe/tank protection
- continuous compatible coating/wrapping; inspect holidays;
- cathodic protection using Mg/Zn sacrificial anodes or impressed current;
- electrically isolate dissimilar metals and joints where practical;
- good drainage/backfill, avoid crevices and water traps;
- corrosion allowance, inhibitors where feasible, test points and potential monitoring;
- periodic inspection and anode replacement.

## Sources
- Materials Tutorial Sheet 4. Numerical results independently recalculated; graph values read from the rendered source.

