---
title: "FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, fracture, dbtt, fatigue, creep, corrosion]
sheet: "Materials Tutorial Sheet 4"
theory_notes: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]", "[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
key_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Ductile-to-Brittle Transition]]", "[[S-N Curves and Paris Law]]", "[[Creep]]", "[[Galvanic Corrosion and Passivation]]"]
status: complete
date: 2026-11-05
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 04 - Failure of Materials.pdf"]
---

# FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions

> [!abstract] Sheet info
> Seven questions on the ductile-to-brittle transition, Griffith and stress-intensity calculations, an S–N curve, steady-state creep and corrosion. The sheet prints no answers; all calculations were checked in Python and the S–N readings were taken by digitising the curve on the sheet. The sheet labels the safety-factor question "Q4 b", although it follows on from Q3. Q1–Q4 use [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics|C8]]; Q5–Q7 use [[FEEG1002 C9 - Fatigue, Creep and Corrosion|C9]].

## Q1 - Toughness against temperature

Taught in: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#5. The ductile-to-brittle transition]] and [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Temperature and the yield stress]].

**(a) Sketch.** Between −100 °C and 400 °C:

- **Stainless steel (FCC)**: high toughness at every temperature, roughly flat, with no transition.
- **Pure iron (BCC)**: a low lower shelf in the cold, a steep rise through the ductile-to-brittle transition (for a pure, coarse-grained iron, around or a little below room temperature), then a high upper shelf.
- **Magnesium (HCP)**: low toughness at low temperature, rising gradually with temperature as more slip systems become active, but staying well below the FCC metal; the transition is broad rather than sharp.

![[m8_impact_energy.png|900]]

The exact transition temperatures depend on purity, grain size and test; the sketch is qualitative.

**(b) Explanation.** A metal fails in a ductile way if its yield stress is reached before its fracture stress, so that the crack tip yields and blunts; otherwise it cleaves. The brittle fracture stress depends on $E$, $\gamma_s$ and the flaw size and hardly changes with temperature. FCC stainless steel has twelve close-packed slip systems in every orientation, so its yield stress is low and almost independent of temperature: it always yields first and stays tough. BCC iron has no close-packed planes, so slip needs thermal activation and its yield stress climbs steeply as the temperature falls; below the transition it exceeds the fracture stress, and the iron cleaves with little energy absorbed. HCP magnesium has only one set of close-packed (basal) planes, too few independent slip systems, and must use non-close-packed systems that need thermal activation, so it is brittle in the cold and becomes tougher only gradually as the temperature rises.

## Q2 - Griffith flaw size in fused silica

Taught in: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#The critical condition]].

Fused silica is ideally brittle, so the Griffith criterion applies:

$$
\sigma_c=\sqrt{\frac{2E\gamma_s}{\pi a}}
$$

Square and rearrange for the critical crack length at the working stress:

$$
a=\frac{2E\gamma_s}{\pi\sigma^2}
$$

With $E=70\,000$ MPa $=70\times10^9$ Pa, $\gamma_s=4.32$ J/m² and $\sigma=35$ MPa:

$$
a=\frac{2\times70\times10^9\times4.32}{\pi\times(35\times10^6)^2}=\frac{6.048\times10^{11}}{3.848\times10^{15}}=1.57\times10^{-4}\ \mathrm m
$$

The largest tolerable flaw has $a=\boxed{0.157\ \mathrm{mm}}$. If it is a surface flaw, that is its depth; if it is an internal flaw, its total length is $2a=0.314$ mm. Any larger flaw would propagate at 35 MPa.

## Q3 - Fast fracture or general yield in a pressure-vessel plate

Taught in: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Using fracture mechanics in design]].

The detector finds internal cracks of length 1.6 mm or more, so a crack just below the limit has $2a=1.6$ mm and $a=0.8$ mm $=8\times10^{-4}$ m. The sheet gives $K_c=\sigma_f\sqrt{\pi a_c}$, i.e. $Y=1$ for a large plate:

$$
\sigma_f=\frac{K_c}{\sqrt{\pi a}}=\frac{65}{\sqrt{\pi\times8\times10^{-4}}}=\frac{65}{0.05013}=\boxed{1300\ \mathrm{MPa}}
$$

This is far above the yield strength of 375 MPa. So as the load rises the plate reaches 375 MPa first and yields generally, long before the cracks could cause fast fracture: it fails by **general yielding**, not by fast fracture. Equivalently, at the yield stress the critical crack is

$$
a_c=\frac1\pi\left(\frac{65}{375}\right)^2=9.6\times10^{-3}\ \mathrm m
$$

an internal crack 19 mm long, twelve times the detection limit.

Assumptions: linear elastic fracture mechanics, with plane-strain conditions in the thick plate so that $K_c$ is the material's $K_{IC}$; a through-thickness, mode I crack perpendicular to the stress in an effectively infinite plate ($Y=1$); "length 1.6 mm" meaning the full length $2a$ of an internal crack; no residual stresses; and $K_c$ and the yield strength measured at the service temperature. If the 1.6 mm were taken as $a$ (or the crack were at the surface), $\sigma_f=917$ MPa, still well above yield, so the conclusion does not change. Once general yielding starts, LEFM no longer applies, but the plate has already failed by yielding by then.

![[m8_t4_q3_fracture_vs_yield.png|900]]

## Q4 - Safety factor for the pressure vessel

Taught in: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Using the properties in design]] and [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Using fracture mechanics in design]].

The governing failure mode is yielding, so the safety factor goes on the yield strength. The ordinary rule in the course is a working stress of at most half the yield strength; for a nuclear pressure vessel, where failure would be catastrophic, the lecture recommends a larger margin, a third of the yield strength or less. A factor of about 3 gives

$$
\sigma_{allow}=\frac{375}{3}=125\ \mathrm{MPa}
$$

Against fast fracture this leaves a factor of $1300/125\approx10$ for cracks at the detection limit. A larger factor still (3–4) is defensible given the consequences, and in practice the design would also follow the pressure-vessel code and allow for fatigue crack growth between inspections, residual stresses at welds, and loss of toughness with temperature or irradiation. This is a judgement question, and any answer between about 3 and 4 on yield, with that reasoning, is reasonable.

## Q5 - Reading the S–N curve

Taught in: [[FEEG1002 C9 - Fatigue, Creep and Corrosion#S–N curves]].

![[m9_t4_q5_sn_readings.png|900]]

The curve was digitised from the sheet. It falls almost linearly with $\log N$ from 400 MPa at $10^4$ cycles, about 90 MPa per decade, then bends over to a horizontal line from about $3\times10^6$ cycles.

- **Fatigue limit**: the horizontal part of the curve, $\boxed{200\ \mathrm{MPa}}$. Below this amplitude the material should survive indefinitely.
- **Fatigue life at 280 MPa**: read across at 280 MPa to the curve and down: about $\boxed{2\times10^5\ \text{cycles}}$ (digitised $2.1\times10^5$).
- **Fatigue life at 400 MPa**: the start of the curve, $\boxed{1\times10^4\ \text{cycles}}$.
- **Fatigue strength at 30 000 cycles**: read up at $3\times10^4$ to the curve and across: about $\boxed{355\ \mathrm{MPa}}$.
- **Fatigue strength at 200 000 cycles**: about $\boxed{283\ \mathrm{MPa}}$.

The last two are consistent with the lives above: 283 MPa at $2\times10^5$ cycles goes with 280 MPa at about $2.1\times10^5$ cycles.

## Q6 - Steady-state creep

Taught in: [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Steady-state creep rate]].

**(a) Why the equation has this form.**

$$
\dot\varepsilon=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right)
$$

Creep in the steady state is controlled by diffusion: vacancies diffusing through the grains, atoms diffusing along grain boundaries so that the grains can slide, and diffusion helping dislocations climb past obstacles. Diffusion is thermally activated, so its rate carries the Arrhenius factor $\exp(-Q_c/RT)$, with $Q_c$ the activation energy and $T$ in kelvin. The applied stress is the driving force, and the rate rises as a power of it, $\sigma^n$, with $n$ between about 1 and 9 depending on which mechanism dominates. $K_2$ is a material constant found by experiment.

**(b) Rate at 1123 K and 25 MPa.** At 1273 K the two data points give $n$. Divide one rate equation by the other; $K_2$ and the exponential cancel because the temperature is the same:

$$
\frac{10^{-4}}{10^{-6}}=\left(\frac{15}{4.5}\right)^n
$$

$$
n=\frac{\ln100}{\ln3.333}=\frac{4.605}{1.204}=3.82
$$

Now compare the new condition with the 15 MPa point, so that $K_2$ cancels again:

$$
\frac{\dot\varepsilon_2}{10^{-4}}=\left(\frac{25}{15}\right)^n\exp\left[-\frac{Q_c}{R}\left(\frac1{1123}-\frac1{1273}\right)\right]
$$

The stress factor is $(1.667)^{3.82}=7.06$. The temperature factor is

$$
\exp\left[-\frac{272\,000}{8.31}\times(8.905\times10^{-4}-7.855\times10^{-4})\right]=\exp(-3.434)=0.0322
$$

so

$$
\dot\varepsilon_2=10^{-4}\times7.06\times0.0322=\boxed{2.3\times10^{-5}\ \mathrm s^{-1}}
$$

The higher stress alone would multiply the rate by seven, but the 150 K drop in temperature cuts it by a factor of 31, so the creep rate ends up about four times lower than at 1273 K and 15 MPa.

> [!check] Recovering both data points
> With $n=3.825$, $K_2=10^{-4}/[15^n\exp(-272\,000/(8.31\times1273))]=466$ (in units for MPa and s⁻¹). The rate equation with this $K_2$ returns $1.0\times10^{-6}$ s⁻¹ at 4.5 MPa and 1273 K, and $2.28\times10^{-5}$ s⁻¹ at 25 MPa and 1123 K.

## Q7 - Corrosion of titanium and protecting buried steel

Taught in: [[FEEG1002 C9 - Fatigue, Creep and Corrosion#The galvanic series]], [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Passivation]] and [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Protecting against corrosion]].

**Titanium.** The standard electrode potential, $-1.63$ V for Ti²⁺/Ti, describes bare titanium metal in a standard solution of its own ions, and on that basis titanium is very reactive. But titanium reacts instantly with oxygen to form a thin, dense, adherent, coherent film of TiO₂. The oxide is a ceramic: it does not conduct electrons and is a barrier to the diffusion of titanium ions out and oxygen in, so once it has formed, further corrosion is stifled, and if it is scratched it re-forms at once. Titanium is **passivated**. The galvanic series ranks real alloys in seawater as they actually behave, with their surface films, so titanium appears near the noble, inert end, while the emf series ranks the bare, active metal.

**Protecting a buried steel pipe and tank.** The options are:

- a protective coating or wrapping (paint, bitumen, polymer tape) to keep the soil water off the steel and block electron flow, inspected for holidays (gaps);
- a sacrificial anode: a more reactive metal, normally magnesium ($-2.38$ V) or zinc ($-0.763$ V), against $-0.440$ V for iron, buried in backfill near the pipe and tank and connected to them, so that it is the anode and corrodes instead, and is replaced when used up; galvanising (zinc coating) works the same way;
- impressed current: a rectifier drives current from an inert or scrap-metal anode through the soil to the structure, forcing the steel to be the cathode; it needs power and maintenance;
- breaking the circuit: insulating washers and joints where the steel meets any other metal, and avoiding dissimilar metals in contact;
- good design: welded rather than bolted joints, no crevices or water traps, good drainage around the tank, and no small anodes next to large cathodes.

In practice a coating and cathodic protection (sacrificial or impressed current) are used together: the coating does most of the work, and the cathodic protection deals with any gaps in it.

## Sources

- `Tutorial Sheet 04 - Failure of Materials.pdf`: Q1–Q7, the S–N curve and the creep data. No solutions are provided. The S–N readings were digitised from the sheet; the creep and fracture calculations were done in Python. The least certain parts are qualitative: the exact positions of the curves in the Q1 sketch, and the choice of safety factor in Q4, which is a judgement.
