---
title: "SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 2
tags: [sesa2028, materials, fatigue, paris-law, miners-rule, fractography, lifing]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
next_topics: ["[[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]"]
key_concepts: ["[[Fatigue Fracture Surface Features]]", "[[S-N Curve and Basquin Law]]", "[[Goodman Relation]]", "[[Miner's Rule]]", "[[Paris Law]]", "[[Total Life vs Damage Tolerance]]", "[[Shot Peening]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Structural Performance 2025.pdf (lectures 1-2)", "mini lectures ML1c, ML2a, ML2b, ML2c"]
---

# SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing

> [!abstract] Summary
> Fatigue is failure under cyclic stress well below the static strength. It has three stages: **initiation**, **stable growth**, and **final fast fracture**, and each leaves its own marks on the fracture surface. There are two ways to life a component. The **total-life** approach uses S-N curves and Miner's rule, and mostly designs against initiation. The **damage-tolerant** approach uses the Paris law integrated from a measured defect $a_i$ to the critical size $a_c$. The Paris-law calculation appears on **every** past paper. It is worth about 8-10 marks, and marks are lost if you give no safety factor or inspection recommendation.

## 1. Examples the lecturer uses

- **Hatfield rail crash (2000)**: rolling-contact fatigue cracks in the rail head. Water in the surface cracks froze, and the ice ratcheted them open.
- **Glasses bridge**: beach marks in a polymer.
- **2014 A330 at Melbourne**: an uncontained turbine-blade fatigue failure. Secondary damage hid the origin, which is why the order in which you read a surface matters.
- **Petrochemical mixer shaft**: a smooth, dull fatigue region, a rough ductile overload region, and ratchet marks.
- **Aluminium dinghy mast**: two opposed fatigue regions show **reversed bending** (the mast rocking side to side). Several thumbnail origins sit at corrosion pits (black dots on the surface), with ratchet marks between them, beach marks, and a rough central final fracture with distinct shear lips.

## 2. Reading a fatigue fracture surface

Work **from the end back to the start**:

1. Find the **shear lips**. They are the easiest feature to see: a rough $45^\circ$ plane-stress rim that marks the **final overload** region.
2. Track back into the **smooth, flat fatigue region**. Fatigue cracks grow at $90^\circ$ to the opening load. By eye they look brittle, but they are produced by **localised** crack-tip plasticity.
3. Follow the **beach marks** (visible by eye or at low magnification). They are concentric crack-front positions left by changes in the loading: stop-start, a change of amplitude, or oxidation during a pause. They are convex away from the origin and point back to it.
4. Locate the **origin(s)**. **Ratchet marks** are steps between neighbouring origins that started on slightly different levels. Many ratchets mean multiple initiation, which indicates **high local stress or a severe stress concentration**.
5. **Striations** are visible only at high magnification (SEM). There is one per cycle, formed by repeated blunting and re-sharpening of the crack tip, so their local spacing is $da/dN$. They are clear in Al alloys and stainless steels and often absent in mild steel. Corrosion products can hide them, **so their absence does not disprove fatigue**.

The crack grew perpendicular to both beach marks and striations.

> [!tip] First-order load estimate (ML1c)
> The fraction of the cross-section taken up by final fast fracture is roughly $\sigma_{max,nominal}/\sigma_{UTS}$. A final zone covering 20 % of the area means the nominal peak stress was about 20 % of UTS. That is low stress and a long life, so the crack had time to grow almost all the way across.

### Metals Handbook chart: loading type from the surface

The chart's columns are **high vs low nominal stress** combined with **mild vs severe stress concentration**. Its rows are:

| Loading | Pattern |
|---|---|
| Tension | single origin (or several with a severe notch); crack front grows across the section |
| Unidirectional bending | origins on the tension side only; looks like tension, so you need the load path to tell them apart |
| Reversed bending | **two** crack systems from opposite sides; final fracture as a band in the middle |
| Rotating bending | origins all round the surface. The final fracture is **offset** (rotated against the direction of rotation) and lopsided or swirly. Under severe stress concentration, cracks grow in from all round and the final fracture is central |
| Torsion | $45^\circ$ helical growth; with multiple origins a stepped "spiral staircase" or star pattern |

Higher nominal stress gives a **larger** final-fracture zone. Severe stress concentration gives **more origins** and more ratchet marks.

> [!example] Lecture exam question: shaft with a keyway under asymmetric reversed bending
> Sketch: origins at the keyway corners (the stress concentration), with ratchet marks between them. Beach marks spread concentrically from the origins. The larger fatigue zone is on the more heavily loaded side, with a smaller zone growing from the opposite side. The final-fracture zone is surrounded by shear lips.
> What each feature tells you: shear lips mean final overload; smooth regions mean fatigue; beach marks point back to the origin; ratchets mean several initiation sites; the keyway is the stress concentration that caused it.
> *Striations (3 marks):* microscopic markings, one per cycle, showing the successive crack-front positions. They cannot be seen without a high-magnification (electron) microscope.

See [[Fatigue Fracture Surface Features]].

## 3. How fatigue cracks start and grow

### Initiation

- Even on a perfectly smooth, electropolished single crystal, cyclic slip builds **persistent slip bands**. These form **extrusions and intrusions**, which act as micro-notches.
- Usually a **microscopic** defect already exists: a cracked inclusion, a pore, or weld defects (inclusions, flux, hydrogen cracks, residual-stress cracks).
- Often a **mesoscopic** flaw is present too: a scratch, a dent (Rolls-Royce's concern about a dropped tool during outsourced MRO), or weld-toe geometry.

### Growth stages

- **Stage I**: shear-driven growth along slip planes at about $45^\circ$, giving a faceted surface. It happens in the first grains or so. **The Paris law does not apply here.** Lecture examples: early growth from a gas pore in a powder-metallurgy disc alloy; single-crystal blades that stay faceted throughout at low temperature; crack deflection at an Al-Sn bearing layer on a steel backing; tunnelling "teardrop" cracks in a disc.
- **Stage II**: growth normal to the maximum opening stress. This is the **Paris regime**, which gives striations.
- **Stage III**: $K_{max}\to K_c$, the crack accelerates, and then **final fast fracture**.

![[Figures/materials_paris_regimes_schematic.png]]

## 4. Cyclic-stress definitions and S-N curves

$$
\Delta\sigma=\sigma_{max}-\sigma_{min},\qquad
\sigma_a=\frac{\Delta\sigma}{2},\qquad
\sigma_m=\frac{\sigma_{max}+\sigma_{min}}2,\qquad
R=\frac{\sigma_{min}}{\sigma_{max}}.
$$

![[Figures/materials_sn_curves.png]]

- **Steels** have a **fatigue limit**: below it, life is effectively infinite.
- **Al alloys** have no limit, so an **endurance limit** is defined at a stated life of $10^7$-$10^8$ cycles.
- $10^5$ cycles is the conventional boundary between regimes:

| | HCF ($N_f\gtrsim10^5$) | LCF ($N_f\lesssim10^5$) |
|---|---|---|
| Stress level | low, nominally elastic | high, cyclic plasticity |
| Life dominated by | initiation | growth (early initiation) |
| Law | **Basquin** $\dfrac{\Delta\sigma}{2}=\sigma_f'(2N_f)^b$ | **Coffin-Manson** $\dfrac{\Delta\varepsilon_p}{2}=\varepsilon_f'(2N_f)^c$ |
| Examples | fuselage and wing vibration | turbine discs and blades (start-stop cycles) |

LCF is written in **strain**, because once the material yields a small change in stress produces a large change in strain. See [[S-N Curve and Basquin Law]].

## 5. Mean-stress correction: Goodman

A higher mean stress lowers the amplitude that can be tolerated for the same life. Goodman assumes a straight line between the fully reversed fatigue strength $\sigma_{a0}$ (at $\sigma_m=0$) and the tensile strength $\sigma_{TS}$ (at $\sigma_a=0$):

$$
\sigma_a=\sigma_{a0}\left(1-\frac{\sigma_m}{\sigma_{TS}}\right).
$$

![[Figures/materials_goodman_diagram.png]]

This is why compressive residual stress ([[Shot Peening]]) helps even though it does not change the stress range: it lowers $\sigma_m$. See [[Goodman Relation]].

## 6. Total-life approach: Miner's rule

In service a component sees blocks of different amplitudes, found by **rainflow counting** a load history (the lecture example is weather loading on an offshore platform). If block $i$ applies $n_i$ cycles at a level whose life is $N_i$, it uses up a fraction $n_i/N_i$ of the life. Failure is predicted when

$$
\boxed{\sum_i\frac{n_i}{N_i}=1.}
$$

Assumptions: damage accumulates linearly and **the order of the blocks does not matter**. In reality a high-low sequence is usually worse than a low-high one. See [[Miner's Rule]].

> [!example] MT2 Q2 / 2018-19 A2(i): combined LCF and HCF on a gas-turbine blade
> $N_{LCF}=150\,\Delta\varepsilon^{-1.5}$, $N_{HCF}=7.5\times10^9\,\Delta\sigma^{-1.2}$.
> - 550 LCF cycles at $\Delta\varepsilon=0.23$: $N=150(0.23)^{-1.5}=1360$, so the fraction used is $0.404$.
> - $2.53\times10^6$ HCF cycles at 320 MPa: $N=7.5\times10^9(320)^{-1.2}=7.39\times10^6$, so the fraction used is $0.342$.
> - Life used $=0.747$. At $\Delta\varepsilon=0.18$: $N=1964$, remaining $=(1-0.747)(1964)\approx\boxed{498}$ stop-starts. Recommend about 250 with a safety factor of 2.
> Full working: [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]].

![[Figures/materials_fatigue_miner_budget.png]]

## 7. Total life vs damage tolerance

| | Total life | Damage tolerant |
|---|---|---|
| Assumes | defect-free material; counts cycles to initiate *and* grow, $N_i+N_g$ | a crack is already present (found by NDT, or the largest that could be missed) |
| Tools | S-N (HCF) or $\varepsilon$-N (LCF) curves, Goodman, Miner | $K=Q\sigma\sqrt{\pi a}$, Paris law, $K_{Ic}$ |
| Sensitive to | **surface finish** (electropolished $\gg$ machined), because scratches remove the initiation stage | the measured crack size $a_i$ and the constants $A$, $m$ |
| Effectively designs against | **initiation** | **growth** |
| Data needed | S-N curves for the material and surface condition, the load spectrum (rainflow), mean stress | $a_i$ from NDT (size **and** position: dye penetrant, optical, X-ray, ultrasound), $a_c$, $\Delta\sigma$, $A$, $m$, $Q$ |
| Typical use | components that must never crack, or where cracks cannot be inspected: rotating shafts, springs, some engine parts | inspectable structures that tolerate defects: airframes, pressure vessels, offshore welds, discs under retirement-for-cause |

The damage-tolerant approach allows for the "almost inevitable" presence of defects and sets inspection intervals. See [[Total Life vs Damage Tolerance]].

## 8. Damage-tolerant lifing: integrating the Paris law

![[Figures/materials_paris_crack_growth_all_exams.png]]

### The recipe (every exam since 2013)

**Step 1: stress range.** Only the tensile part of the cycle opens the crack:

$$
\Delta\sigma=\sigma_{max}-\max(\sigma_{min},0).
$$

(In the lecturer's worked example, +120/-30 MPa gives $\Delta\sigma=120$ MPa.)

**Step 2: critical crack length** from fast fracture at $\sigma_{max}$:

$$
a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\sigma_{max}}\right)^2.
$$

**Step 3: separate the variables in the Paris law** $\dfrac{da}{dN}=A(\Delta K)^m$ with $\Delta K=Q\Delta\sigma\sqrt{\pi a}$:

$$
\frac{da}{dN}=A\left(Q\Delta\sigma\sqrt\pi\right)^m a^{m/2}
\;\Rightarrow\;
\int_{a_i}^{a_c}a^{-m/2}\,da=A\left(Q\Delta\sigma\sqrt\pi\right)^m\int_0^{N_f}dN.
$$

**Step 4: integrate** (for $m\neq2$):

$$
\boxed{N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{\left(1-\tfrac m2\right)A\left(Q\Delta\sigma\sqrt\pi\right)^m}}
$$

For $m>2$ the exponent $1-m/2$ is negative, so the numerator and denominator are both negative and $N_f$ comes out positive. Keep the signs explicit so you can catch slips.

**Step 5: convert to service units** (flights, days, rotations, years) and **apply a safety factor**. The lecturer's convention is a factor of 2 on life, or equivalently re-inspecting at half the predicted life. Marks are lost without it.

**Step 6: comment on the assumptions.** $Q$ is assumed constant as the crack grows; there is no Stage I or short-crack regime; $A$ and $m$ were measured in lab air, not the service environment; there is no overload retardation; $K_{Ic}$ may depend on temperature; the crack shape may change.

> [!example] Lecturer's worked example (MT2 Q4)
> Large plate, +120/-30 MPa, $a_i=1$ mm, $K_{Ic}=45\ \mathrm{MPa\sqrt m}$, $A=2\times10^{-12}$, $m=3$, $Q=1$.
>
> $$\Delta\sigma=120\ \text{MPa},\qquad a_c=\frac1\pi\left(\frac{45}{120}\right)^2=0.0448\ \text m.$$
>
> $$N_f=\frac{0.0448^{-1/2}-0.001^{-1/2}}{(-\tfrac12)(2\times10^{-12})(120\sqrt\pi)^3}=\frac{-26.90}{-9.62\times10^{-6}}\approx\boxed{2.80\times10^6\ \text{cycles}}.$$
>
> The lecturer's slide gives 2,801,904; carrying more figures in $a_c$ gives 2,795,265.

### Why the integral is dominated by the early crack

$da/dN\propto a^{m/2}$, so the crack grows slowest when it is small. For $m=3$ and $a_c\gg a_i$, the numerator is almost exactly $a_i^{-1/2}$. The life is therefore **very sensitive to $a_i$** (NDT resolution) and fairly insensitive to $a_c$ (and hence to $K_{Ic}$). The 2021-22 reactor-vessel question tests exactly this with a $\pm10\,\%$ uncertainty on $a_i$.

### Every Paris-law exam answer at a glance

| Question | $a_i$ (mm) | $\sigma_{min}$/$\sigma_{max}$ (MPa) | $K_{Ic}$ | $A$, $m$ | $a_c$ (mm) | $N_f$ | Service life |
|---|---:|---|---:|---|---:|---:|---|
| 2013-14 B1 wing | 3 | 20/200 | 45 | 2.67e-10, 3 | 11.2 | 1,175 | 1,175 flights (SF2: 588) |
| 2014-15 B1 = MT2 Q3 vessel | 4 | 10/150 | 65 | 1.58e-10, 3.5 | 41.5 | 963 | 963 cycles (SF2: 482) |
| 2015-16 B1 offshore weld | 5 | 10/200 | 38 | 2.05e-11, 3.5 | 7.98 | 771 | 25.7 yr (SF2: 12.9 yr) |
| 2016-17 A2 mixer shaft | 1.5 | 5/300 | 55 | 2.67e-10, 2.5 | 7.43 | 2,545 | 2,545 rev (SF2: 1,272) |
| MT2 Q5 (Green Book $A$) | 1.5 | 5/300 | 55 | 2.67e-11, 2.5 | 7.43 | 25,449 | 25,449 rev (SF2: 12,725) |
| 2017-18 A2 brewery weld | 1.35 | 15/225 | 38 | 2.2e-11, 4.5 | 6.31 | 143 | 143 days (SF2: 71) |
| 2018-19 A2 IGT blade root | 3.3 | 34/195 | 75 | 4.5e-11, 3.8 | 32.7 | 862 | 431 days (SF2: 216) |
| 2020-21 MQ2 water pipe | 1.8 | 30/350 | 47 | 2.45e-11, 3 | 3.99 | 2,002 | 143 weeks (SF2: 71) |
| 2021-22 MQ2 reactor vessel | 1.4±10 % | $\Delta\sigma$ 350; LOCA 550 | 70-76 | 2.45e-11, 3.2 | 3.58 (worst) | 850 (worst) | 8.1 yr worst (SF2: ~4 yr) |
| 2022-23 MQ1 turbine disc | 1.5 | 25/550 | 125 | 7.35e-11, 2.5 | 11.4 | 2,641 | 2,641 flights (SF2: 1,321) |
| 2023-24 MQ1 hip implant | 0.5 | 25/160 | 55 | 7.45e-12, 2.5 | 26.1 | 1.61e6 | 6.8 yr (SF2: 3.4 yr) |
| 2024-25 MQ2 turbine disc | 1.5 | 30/450 | 95 | 2.45e-12, 3 | 9.85 | 18,030 | 18,030 flights (SF2: 9,015) |

($Q=1.2$ throughout. Full working is in each [[SESA2028 Past Paper Map|exam solution note]].)

See [[Paris Law]].

## 9. Reducing fatigue

The lecturer's list of **five factors** (plus environment):

1. **Macroscopic stress concentrations** ("hot spots"): use generous fillets. Example: a steam-turbine blade fir-tree root, where FEA hot-spot stress feeds an S-N life.
2. **Microscopic stress concentrations**: for example $\mathrm{Al_2O_3}$ stringers in blade steel. Fix with cleaner steel-making.
3. **Surface roughness**: the peaks and valleys of $R_a$ act as micro-notches. Polish critical surfaces.
4. **Defects**: pores and inclusions. Use better processing (HIP, vacuum melting).
5. **Residual stress**: compressive is beneficial (shot peening), tensile is harmful (welds).
6. **Environment**: see below.

### Shot peening

![[Figures/materials_shot_peening_residual_stress.png]]

Each shot makes a small dimple that is plastically stretched. On unloading, the surrounding elastic material pushes back, which leaves the surface in **compression**. X-ray diffraction on a peened martensitic blade steel measured about $-600$ MPa at the surface and $-800$ MPa at about 100 µm depth (near yield), balanced by tension at about 400 µm.

- Benefit: it lowers the **mean** stress, not the range, so there is a big gain in HCF strength and fatigue limit (Goodman). It also work-hardens the surface.
- Side effect: the **surface gets rougher**, which is harmful.
- Apply it at stress-concentration features (fillets, fir-tree roots, spline roots).

See [[Shot Peening]].

### Environment

- The fatigue strength of Al alloys falls from air to water to salt water. **Corrosion pits** remove the initiation stage and act as stress concentrations. Preferential attack of grain boundaries or particular phases also helps initiation.
- At high temperature, oxidation along grain boundaries increases $da/dN$. A NASA disc alloy at 725 °C cracked much faster in air than in vacuum, with intergranular fracture. This is time-dependent, so it is worse at low frequency and with dwell ([[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]).

### Welds are bad news for fatigue

- Macro and meso stress raisers: weld-toe geometry, lack of fusion (a built-in notch), and undercut.
- Micro defects: slag, porosity, hot cracks.
- Rapid heating and cooling **changes the microstructure**, so properties vary across the heat-affected zone (HAZ). It also leaves **tensile residual stress** from contraction.
- The 2024 Al-weld research lecture (ML10a) showed that MIG welds cracked from fusion-zone porosity while VPPA welds cracked in the HAZ at residual-stress peaks. Life to a 1 mm crack was about 50 % of the total life. See [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]].

## 10. Exam checklist

- [ ] $\Delta\sigma$ uses the **tensile** part only.
- [ ] $a_c$ uses $\sigma_{max}$ **and** the same $Q$.
- [ ] Convert mm to m before integrating ($A$ is quoted for $a$ in m).
- [ ] Watch the sign of $1-m/2$.
- [ ] Convert cycles to flights/days/years, **then apply SF 2 or an inspection interval**.
- [ ] State at least three limitations (Stage I and short cracks, environment and temperature of the $A$, $m$ data, constant $Q$, overloads, $K_{Ic}$ scatter).
- [ ] For "other service problems", think corrosion fatigue, pitting, SCC ([[SESA2028 M3 - Corrosion, Wear and Surface Engineering|M3]]), and creep-fatigue or oxidation-fatigue at high temperature ([[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]).

## Related

- [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]] for $K$, $K_{Ic}$ and $a_c$.
- [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]].
- [[Spinning Disc Stress]]: why the turbine-disc bore sees the highest stress (2022-23 MQ1).
- [[Lame Thick-Cylinder Solution]]: stresses in the pressure vessels used in the lifing questions.

## Year 1 foundation
- Vibration as a source of stress cycles: [[FEEG1002 D6 - Single Degree of Freedom Vibration]]. Stress concentrations: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]].
