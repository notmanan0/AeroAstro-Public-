---
title: "FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, tensile-test, strengthening, annealing, arrhenius]
sheet: "Materials Tutorial Sheet 2"
theory_notes: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
key_concepts: ["[[Engineering Stress-Strain Properties]]", "[[Dislocations and Slip Systems]]", "[[Strengthening Mechanisms in Metals]]", "[[Annealing of Cold-Worked Metals]]"]
status: complete
date: 2026-11-05
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf"]
---

# FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions

> [!abstract] Sheet info
> Seven questions: elastic deformation of a rod, reading a tensile curve, obstacles to dislocations, yield points in steel, work hardening and annealing, and the Arrhenius growth of recrystallised grains. The sheet prints no answers. The Q2 readings were taken by digitising the curves on the sheet (pixel positions converted to stress and strain), so they are more precise than readings by eye, but they are still graph readings and are quoted to two or three figures. Q1–Q4 use [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]]; Q3 and Q5–Q7 use [[FEEG1002 C5 - Strengthening Mechanisms and Annealing|C5]].

## Q1 - Elastic deformation of a copper rod

Taught in: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Hooke's law and Young's modulus]] and [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Poisson's ratio]].

The rod is 10 mm in diameter and 305 mm long, under 276 MPa, with $E=110$ GPa and $\nu=0.34$; the deformation is entirely elastic. The axial strain is

$$
\varepsilon_z=\frac{\sigma}{E}=\frac{276}{110\,000}=2.509\times10^{-3}
$$

so the elongation is

$$
\Delta L=\varepsilon_zL_0=2.509\times10^{-3}\times305=\boxed{0.765\ \mathrm{mm}}
$$

The lateral strain is

$$
\varepsilon_x=-\nu\varepsilon_z=-0.34\times2.509\times10^{-3}=-8.53\times10^{-4}
$$

and the change in diameter is

$$
\Delta d=\varepsilon_xd_0=-8.53\times10^{-4}\times10=\boxed{-8.53\times10^{-3}\ \mathrm{mm}}
$$

The diameter shrinks by 8.5 µm.

## Q2 - Properties from the aluminium tensile curve

Taught in: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#2. Plastic deformation and the tensile curve]].

The specimen is 12.8 mm in diameter with a 50.8 mm gauge length. Its original area is

$$
A_0=\frac{\pi\times12.8^2}{4}=128.7\ \mathrm{mm^2}
$$

![[m4_t2_q2_tensile_readings.png|900]]

**Modulus of elasticity.** On the zoomed plot the line is straight up to about 250 MPa at a strain of 0.0041. Its slope is

$$
E=\frac{\Delta\sigma}{\Delta\varepsilon}=\frac{244}{0.00403}\approx\boxed{61\ \mathrm{GPa}}
$$

(a least-squares fit to the digitised straight portion gives 61 GPa; 60–62 GPa is a fair reading).

**0.2 % offset yield stress.** Draw a line of slope 61 GPa from a strain of 0.002. It meets the curve at a strain of about 0.0065, where the stress is

$$
\sigma_{0.2}\approx\boxed{277\ \mathrm{MPa}}
$$

(275–280 MPa by eye).

**Tensile strength.** The highest point of the curve, at a strain of about 0.09:

$$
\mathrm{UTS}\approx\boxed{369\ \mathrm{MPa}}
$$

**% elongation at failure.** The curve ends at a total strain of 0.165 and a stress of 282 MPa. Percentage elongation is the plastic strain left after fracture, so remove the elastic strain recovered when the pieces unload:

$$
\varepsilon_p=0.165-\frac{282}{61\,000}=0.165-0.0046=0.160
$$

$$
\%EL\approx\boxed{16\ \%}
$$

**Elongation at failure.** At the instant of fracture the extension is $0.165\times50.8=\boxed{8.4\ \mathrm{mm}}$; the permanent extension measured on the broken pieces is $0.160\times50.8=8.1$ mm.

**Maximum load.**

$$
F_{max}=\mathrm{UTS}\times A_0=369\times128.7=\boxed{47.4\ \mathrm{kN}}
$$

**Loaded to 340 MPa and released.** On the full curve 340 MPa is reached at a total strain of about 0.034. Unloading is elastic, along a line of slope $E$ ([[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Unloading and reloading|C5]]), so the strain recovered is

$$
\varepsilon_e=\frac{340}{61\,000}=0.0056
$$

and the permanent strain and elongation are

$$
\varepsilon_p=0.034-0.0056=0.028
$$

$$
\Delta L_p=0.028\times50.8=\boxed{1.4\ \mathrm{mm}}
$$

> [!check] Sensitivity of the last answer
> The result depends mostly on where 340 MPa is read on the curve, which is fairly flat there: reading the strain as 0.033 or 0.035 changes the answer to 1.39 or 1.49 mm. Quote about 1.4 mm. Dropping vertically instead of along the elastic slope would give 1.7 mm, which is the classic error.

## Q3 - Obstacles to dislocation motion

Taught in: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#5. Stopping dislocations]] and [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#1. Why strengthening works]].

A dislocation carries a compressive region on one side of its slip plane and a tensile region on the other. Each obstacle interferes with it in its own way.

(i) **Solute atoms** are a different size from the host atoms, so each distorts the lattice around it and has its own stress field. Like fields repel (compression against compression, tension against tension), and solute atoms that have settled where they relieve the dislocation's strain hold it there, so extra stress is needed to move the dislocation past or away from them.

(ii) **Other dislocations** carry the same kinds of stress field. Dislocations on the same slip system repel each other, and dislocations on intersecting slip systems cut through and tangle with each other. The more dislocations there are, the more each is obstructed, which is work hardening.

(iii) **Grain boundaries** are the edges of differently oriented crystals. A dislocation reaching one cannot continue on the same slip plane in the next grain, so it stops and others pile up behind it; slip only continues when the pile-up stress starts slip in the neighbouring grain. Smaller grains hold shorter pile-ups and so need a higher applied stress (Hall–Petch).

(iv) **Precipitates** are particles of a second phase with a different structure. Coherent ones distort the surrounding lattice and must be cut through, which needs extra stress; incoherent ones cannot be cut, so the dislocation has to bow out between them, which needs a stress that rises as the spacing between particles falls.

## Q4 - Upper and lower yield points in steel

Taught in: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Interstitial carbon and the yield point of steel]].

Carbon (and nitrogen) atoms dissolved interstitially in iron do not fit their sites and strain the lattice around them (Tutorial 1, Q9). They diffuse to the one place with spare room, the stretched region just below the extra half plane of each edge dislocation, where they relieve their strain and pin the dislocation. To start the dislocations moving, extra stress is needed to tear them away from their carbon atmospheres: the stress rises to the **upper yield point**. Once free, the dislocations move at a lower stress, so the stress drops to the **lower yield point**, and the steel extends at roughly constant stress (the serrated plateau) as yielding spreads along the specimen. When the whole gauge length has yielded, work hardening begins and the stress rises again. For design, the lower yield point is used.

## Q5 - Effects of work hardening

Taught in: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#2. Work hardening]].

Work hardening (cold work) raises the dislocation density and tangles the dislocations, so:

- the yield strength rises (a work-hardened bar yields at the stress it was last unloaded from), and so do the tensile strength and the hardness;
- the remaining ductility (%EL) falls, because the strain used in working is no longer available; enough cold work makes a metal brittle;
- the grains are elongated in the working direction, so the properties become anisotropic;
- Young's modulus does not change, because it is set by the bonding, not by the dislocations.

## Q6 - Restoring the properties by annealing

Taught in: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#5. Annealing]].

Anneal the cold-worked metal, typically at around half its absolute melting temperature. In **recovery**, dislocations rearrange into low-energy walls and internal stresses are relieved, with little change in strength. In **recrystallisation**, new strain-free, equiaxed grains nucleate and grow by diffusion, sweeping away the dislocations: the strength falls and the ductility returns. Holding longer, or hotter, gives **grain growth**, which softens the metal further. Choosing the annealing temperature, time and amount of prior cold work sets the final grain size, and so the balance between strength (finer grains, Hall–Petch) and ductility. Because all three stages are diffusion-controlled, time and temperature can be traded against each other.

## Q7 - Growth velocity of recrystallised grains

Taught in: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Recrystallisation as a thermally activated process]] and [[FEEG1002 C3 - Diffusion#Working with the Arrhenius equation]].

**Why exponential.** New grains grow by atoms diffusing across the boundary from the deformed grain into the new one. Diffusion is thermally activated: each atom must climb an energy barrier $Q$, and the fraction that have enough thermal energy goes as $\exp(-Q/RT)$. So the growth velocity has the Arrhenius form

$$
v=A\exp\left(-\frac{Q}{RT}\right)
$$

and taking logarithms,

$$
\ln v=\ln A-\frac QR\cdot\frac1T
$$

a straight line of $\ln v$ against $1/T$, with slope $-Q/R$.

**The data.** Converting to kelvin:

| $T$ (°C) | $T$ (K) | $1/T$ (K⁻¹) | $v$ (m/s) | $\ln v$ |
|---:|---:|---:|---:|---:|
| 200 | 473.15 | 2.1135 × 10⁻³ | 5.62 × 10⁻¹³ | −28.21 |
| 250 | 523.15 | 1.9115 × 10⁻³ | 1.38 × 10⁻¹⁰ | −22.70 |
| 300 | 573.15 | 1.7448 × 10⁻³ | 1.35 × 10⁻⁸ | −18.12 |
| 400 | 673.15 | 1.4856 × 10⁻³ | 1.82 × 10⁻⁵ | −10.91 |

A least-squares straight line through the four points has slope $-27\,545$ K and intercept $29.97$, so

$$
Q=27\,545\times8.314=2.29\times10^5\ \mathrm{J/mol}=229\ \mathrm{kJ/mol}
$$

The points lie very close to the line (residuals in $\ln v$ below 0.04), so the Arrhenius model fits well.

![[m5_t2_q7_arrhenius.png|900]]

**Temperature for $v=10^{-2}$ m/s.** Set $\ln v=\ln10^{-2}=-4.605$ on the line:

$$
\frac1T=\frac{29.97-(-4.605)}{27\,545}=1.2553\times10^{-3}\ \mathrm{K^{-1}}
$$

$$
T=796.6\ \mathrm K=\boxed{523\ ^\circ\mathrm C}
$$

about 520 °C. Using only the two highest-temperature points instead gives 521 °C. This is an extrapolation well beyond the data (the highest measured temperature is 400 °C), so quote it as roughly 520 °C; a graphical answer anywhere from about 510 to 530 °C is reasonable.

## Sources

- `Tutorial Sheet 02 - Plastic Deformation-Mechanical Properties Strengthening.pdf`: Q1–Q7. No solutions are provided. Q2 was read by digitising the two curves on the sheet; Q7 was fitted by least squares in Python.
