---
title: "SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 2
tags: [sesa2028, materials, fatigue, paris-law, miners-rule, fractography, lifing]
status: lectured
coverage: "Mini-lectures ML1c, ML2a, ML2b, ML2c and the dinghy-mast video; worked numbers from materials tutorial MT2"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
next_topics: ["[[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]"]
key_concepts: ["[[Fatigue Fracture Surface Features]]", "[[S-N Curve and Basquin Law]]", "[[Goodman Relation]]", "[[Miner's Rule]]", "[[Paris Law]]", "[[Total Life vs Damage Tolerance]]", "[[Shot Peening]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Structural Performance 2025.pdf (slides 21-40)", "02 - Sources/Materials Lectures/mini lecture videos/ML1c Fatigue failure fracture surfaces_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML2a Micromechanisms and definitions in fatigue_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML2b Total life and damage tolerant lifing approaches_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML2c Reducing fatigue_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/dinghy mast_default.txt"]
---

# SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing

> [!abstract] Summary
> Fatigue is failure under repeated loading at stresses well below the static strength: a crack initiates, grows a little each cycle and finally reaches the critical size of [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]], when the part breaks in one go. Each stage leaves its own marks, so a fracture surface can be read backwards from the final fracture to the origin and tells you the type of loading, the stress level and how severe the stress concentration was. Lives are predicted two ways: the total-life approach uses S-N curves and Miner's rule and in effect designs against initiation, while the damage-tolerant approach integrates the Paris law from an inspected defect size to $a_c$. The Paris-law calculation has appeared on every past paper.

> [!summary]- Exam use: quick path
> - **Use it when:** a part sees cyclic load and you are asked to read its fracture surface, choose a lifing approach, combine blocks of cycles, or find how long a known crack can be left in service.
> - **Assumptions:** Miner: damage adds linearly and the order of the blocks does not matter. Paris: a long crack growing in stage II, constant $Q$, LEFM, only the tensile part of the cycle counts.
> - **Method (Paris):** 1. $\Delta\sigma=\sigma_{max}-\max(\sigma_{min},0)$. 2. $a_c=\frac1\pi(K_{Ic}/Q\sigma_{max})^2$. 3. $N_f=\dfrac{a_c^{1-m/2}-a_i^{1-m/2}}{(1-m/2)A(Q\Delta\sigma\sqrt\pi)^m}$ with lengths in metres. 4. Convert cycles to flights, days or years. 5. Halve the life (safety factor 2) or set an inspection interval, and list the assumptions.
> - **Common mistakes:** putting the compressive part of the cycle into $\Delta\sigma$; leaving out the safety factor or inspection advice, which costs marks every year.
> - **Example:** [[#A tutorial plate grown from 1 mm]]. **Exercise:** MT2 Q3 in [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]].

Fatigue is the reason the structural-performance block exists. Very few things are loaded at one steady value: wings flex in gusts, engines start and stop, shafts rotate under bending, and an offshore platform takes whatever the weather sends (ML2a, ll. 158–164). Under that cycling a crack can start at a stress concentration, grow slowly for years, and then fail without warning once it is long enough. The lecturer's examples range from the Hatfield rail crash of 2000, where rolling-contact fatigue cracks in the rail head were helped along by water freezing in them, to an engine on a 2014 flight at Melbourne that shed a fatigued turbine blade, to a pair of spectacles whose bridge snapped one morning (ML1c, ll. 1–40).

The picture to hold is of a crack tip that opens and closes every cycle. Each opening blunts the tip in a small plastic zone; each closing re-sharpens it a little further on. Nothing at the scale of the whole part looks plastic, so a fatigue fracture appears brittle to the eye, yet every increment of growth is a local plastic event (ML1c, ll. 107–111). The rate of growth depends on how hard the tip is being worked, which rises with both the stress range and the crack length; that is why a fatigue crack starts slowly and accelerates, and why the life is decided mainly while the crack is small.

## 1. Reading a fatigue fracture surface

Learning to read failure surfaces is one of the module's learning outcomes, and the first two materials tutorials and the consultancy-report coursework depend on it (ML1c, ll. 111–113, 199–208). Real service failures are hard to read: in the Melbourne engine, debris from the released blade had damaged almost every other blade and even the fan, so the small crack that started it was buried under evidence of the final event (ll. 30–42). The method is therefore to work backwards from the end.

Start with the shear lips, usually the easiest feature to spot. They are the last ligament of material, which tore under plane stress on planes at about 45° to the load, exactly as in the cup-and-cone of M1, and they mark where fast fracture finished the job (ll. 67–76). Next to the rough final-fracture region there should be a smooth, flat area: the fatigue crack, which grew perpendicular to the maximum opening stress (ll. 76–78, 107–108). Within it you may see **beach marks**, concentric lines visible by eye that record where the crack front was at some moment. They form because loading is rarely steady: a machine runs and vibrates, stops, sits, then runs again, and each pause or change of amplitude leaves a band of different roughness or a layer of oxide on the surface. They curve round the origin, so following them back leads to where the crack started (ll. 78–87). If a part shows several origins at slightly different heights, the cracks from each grow on slightly different levels, and where they meet they leave small steps called **ratchet marks**. Many ratchet marks mean many initiation sites, which signals a severe stress concentration (ll. 54–60).

![[materials_fatigue_surface_features.png|900]]

At high magnification in a scanning electron microscope there may also be **striations**: fine ripples, one per cycle, left as the tip blunts on loading and pinches back on unloading. Their spacing is the local crack growth rate $da/dN$, which makes them valuable in an investigation (ll. 87–97). The crack grew perpendicular to both striations and beach marks (ll. 99–100). Striations show up well in aluminium alloys and stainless steels and poorly in mild steel, and corrosion products can hide them, so their absence does not rule fatigue out; their presence is strong evidence for it (ll. 101–106).

The dinghy-mast video puts all of this on one real part (dinghy mast, ll. 1–35). The aluminium-alloy mast has two separate fatigue regions growing in from opposite sides. Each began as a row of small thumbnail cracks, each with its own beach marks, which joined into one main front with ratchet marks between them. The rough region in the middle, bounded by distinct shear lips, is the final fracture. The surface is dotted with small black corrosion pits, which is where the thumbnails started. Two opposed fatigue regions mean reversed bending: the mast was rocking from side to side on the boat.

### What the surface says about the loading

A chart from the Metals Handbook, used in the coursework, sets out how the surface changes with the type of loading, the nominal stress and the stress concentration (ML1c, ll. 111–198).

![[materials_fatigue_surface_chart.png|900]]

The size of the final-fracture region measures the peak nominal stress. The crack grows until, at the maximum load, either $K$ reaches $K_{Ic}$ or the remaining ligament reaches general yield (ll. 122–130). A high peak stress ends the growth while the crack is still small; a low one lets it run most of the way across. As a first approximation, the fraction of the section taken by final fracture is the fraction of the ultimate tensile strength that the peak nominal stress represented (ll. 133–143): a section that failed entirely by overload was loaded at the UTS, one that failed when the crack was halfway across was at about 50 % of the UTS, and a 20 % final-fracture area suggests a peak of about 20 % of the UTS. The appearance of ratchet marks, separately, measures the stress concentration: one origin for a mild one, many for a severe one, and with a very severe one under low stress the cracks can grow in from all round and surround a central final fracture (ll. 146–163).

The rows distinguish the loading (ll. 164–198). Tension gives a crack growing across the section from one side. Unidirectional bending looks almost the same, with origins on the tension face, so you need the load path to tell the two apart. Reversed bending is distinctive: two fatigue regions on opposite faces, one grown in each half of the cycle, with the final fracture as a band between them. Rotating bending, common in service where a shaft is slightly off-axis or carries an unbalanced load, gives a surface perpendicular to the axis, with a lopsided, swirled fatigue region and, under a severe concentration, origins all round and the final fracture near the centre. Torsion is different again: the crack follows the 45° helix of maximum opening stress, and with many origins gives a web of stepped spiral cracks like a little spiral staircase (ll. 191–198; the planes are derived in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics#7. Loading modes and torsion failures|M1]]).

## 2. How fatigue cracks start and grow

Fatigue has three phases: initiation, growth and final failure (ML2a, ll. 17–70). Initiation does not need a defect. Under cyclic load, dislocations shuttle back and forth along slip planes, and bands of slip move by different amounts, pushing out small extrusions and intrusions at the surface that act as micro-notches. Even an electropolished single crystal of copper will eventually crack this way (ll. 18–30). In most engineering materials, though, there is already a microscopic defect, a cracked inclusion or a pore. A weld is "a microcosm" of them: inclusions from the flux, small cracks from residual stresses after rapid heating and cooling, and hydrogen cracks (ll. 30–40). On top of that come mesoscopic flaws: a scratch or a dent from handling, which is why Rolls-Royce worries about a dropped hammer in a maintenance shop anywhere in the world, or the shape of a weld bead itself (ll. 41–50).

Once a crack is large enough to be called one (materials scientists and engineers argue about the size), it grows slowly, and eventually reaches the size at which loads that were once harmless cause fast fracture (ll. 54–66). How much of the life each phase takes decides how to inspect and how to life the part (ll. 66–70).

Growth itself has stages (ML2b, ll. 117–156). In **stage I**, the earliest growth, the crack follows slip bands at about 45° to the opening stress, giving a faceted, semi-brittle look. The lecturer's research examples include early growth from a gas pore in a powder-metallurgy turbine-disc alloy, single-crystal blade alloys that grow in stage I right across the part at low temperature because there are no grain boundaries to interrupt the slip bands, a crack in a thin aluminium-tin bearing layer that deflects as it nears the stiffer steel backing, and a "tunnelling teardrop" crack in a disc alloy. In **stage II** the crack grows perpendicular to the maximum opening stress, leaves striations and follows the Paris law, so its path and rate can be predicted. Stage I is not described by the Paris law, so lifing calculations assume stage II.

## 3. Cyclic stress and S-N curves

For a cycle between $\sigma_{max}$ and $\sigma_{min}$ (ML2a, ll. 70–75),

$$
\Delta\sigma=\sigma_{max}-\sigma_{min},
\qquad
\sigma_a=\frac{\Delta\sigma}{2},
\qquad
\sigma_m=\frac{\sigma_{max}+\sigma_{min}}{2}.
$$

Testing samples at different stress amplitudes and counting the cycles to failure gives the S-N curve, plotted against log cycles (ll. 76–85). Lower amplitudes mean longer lives, because both initiation and growth take longer. Steels show a **fatigue limit**, an amplitude below which no crack successfully initiates and the life is in effect infinite (ll. 85–89). Aluminium alloys do not; their curve keeps falling, so an **endurance limit** is defined instead as the fatigue strength at a stated large number of cycles, usually $10^7$ or $10^8$ (ll. 89–97).

![[materials_sn_curves.png|800]]

About $10^5$ cycles divides two regimes (ll. 102–118). Above it is **high-cycle fatigue**: low, nominally elastic stresses, with most of the life spent in initiation; vibration-loaded structures such as fuselages and wings work here. Below it is **low-cycle fatigue**: high stresses with cyclic plasticity, early initiation and a life controlled by crack growth; turbine discs and blades, which see a big cycle at every start and stop, work here. In low-cycle fatigue strain is the better measure, because once the material yields a small change in stress produces a large change in strain.

Each regime has a fitted power law (ll. 121–136, slide 27). In high-cycle fatigue Basquin's law relates the stress amplitude to the number of reversals $2N_f$,

$$
\frac{\Delta\sigma}{2}=\sigma_f'\left(2N_f\right)^{b},
$$

with the fatigue strength coefficient $\sigma_f'$ and the fatigue strength exponent $b$ (negative, typically about $-0.05$ to $-0.12$). In low-cycle fatigue the Coffin–Manson law uses the plastic strain amplitude,

$$
\frac{\Delta\varepsilon_p}{2}=\varepsilon_f'\left(2N_f\right)^{c},
$$

with the fatigue ductility coefficient $\varepsilon_f'$ and exponent $c$. To find the life at a given amplitude, invert Basquin's law. Divide by $\sigma_f'$:

$$
\left(2N_f\right)^{b}=\frac{\sigma_a}{\sigma_f'},
$$

raise both sides to the power $1/b$:

$$
2N_f=\left(\frac{\sigma_a}{\sigma_f'}\right)^{1/b},
$$

and halve:

$$
N_f=\frac12\left(\frac{\sigma_a}{\sigma_f'}\right)^{1/b}.
$$

Because $b$ is small and negative, $1/b$ is large and negative, so a small drop in amplitude buys a large gain in life: with $\sigma_f'=1000$ MPa and $b=-0.1$, an amplitude of 400 MPa gives $N_f=\tfrac12(0.4)^{-10}\approx4800$ cycles, and 300 MPa gives about 85,000. The tutorials fit such laws to data (ll. 134–136).

## 4. Mean stress and the Goodman relation

Amplitude alone does not fix the life. At the same amplitude, a higher mean stress gives a shorter life, so the S-N data form a family of curves, one per mean stress (ML2a, ll. 137–146). The Goodman equation collapses that family with a straight line between two anchor points (ll. 146–154, slide 28): when $\sigma_m=0$ the allowable amplitude is the fully reversed fatigue strength $\sigma_{a0}$ for the chosen life, and when $\sigma_a=0$ the mean stress can rise to the tensile strength $\sigma_{ts}$. A straight line through $(0,\sigma_{a0})$ and $(\sigma_{ts},0)$ has slope $-\sigma_{a0}/\sigma_{ts}$, so

$$
\sigma_a=\sigma_{a0}-\frac{\sigma_{a0}}{\sigma_{ts}}\sigma_m,
$$

$$
\sigma_a=\sigma_{a0}\left(1-\frac{\sigma_m}{\sigma_{ts}}\right).
$$

![[materials_goodman_mean_stress.png|900]]

This is why compressive residual stress helps (Section 8): it lowers the mean stress while leaving the range unchanged. With $\sigma_{a0}=300$ MPa and $\sigma_{ts}=600$ MPa, a mean of 150 MPa cuts the allowable amplitude to $300(1-0.25)=225$ MPa; a residual stress of $-150$ MPa would restore it.

## 5. Total life: Miner's rule

Laboratory S-N curves are measured at one amplitude and one mean stress, but a real structure sees a mixed schedule (ML2a, ll. 155–164). The load history is broken into blocks by counting how many cycles occur at each amplitude and mean stress, a procedure called rainflow counting (ll. 165–170). **Miner's rule** then says that $n_i$ cycles at a level whose life is $N_i$ use up the fraction $n_i/N_i$ of the life, and that failure occurs when the fractions add up to one (ll. 165–188, slide 29):

$$
\sum_i\frac{n_i}{N_i}=1 .
$$

The rule assumes damage accumulates linearly and that the order of the blocks makes no difference. Neither is strictly true, which is worth saying in an answer.

## 6. Total life against damage tolerance

The S-N approach is a **total-life** approach: the predicted life is the number of cycles to initiate a crack, $N_i$, plus the number to grow it to the critical size, $N_g$ (ML2b, ll. 1–15, slide 30). S-N curves depend strongly on how the specimens were finished: electropolished samples last much longer than ground or machined ones, because a scratch is already a defect and shortens initiation (ll. 15–23). S-N data are normally measured on highly finished samples, where initiation dominates, so a total-life calculation in effect designs against initiation (ll. 23–27). It suits parts that are smooth, or whose notch can be handled by evaluating the stress at the notch root (ll. 27–30).

If a defect is already present, the **damage-tolerant** approach asks instead how fast that defect grows and how many cycles remain before it becomes critical (ll. 30–35). It accepts the "almost inevitable" presence of defects (slide 30) and gives safe inspection intervals and how long a cracked part can keep flying (ll. 116–118). It needs four things (ll. 54–78, slide 31):

- the initial defect size $a_i$, and its position, from non-destructive testing: dye penetrant, optical inspection, X-ray or ultrasound;
- the final crack size, normally $a_c$ from the fracture toughness at the maximum stress, though it could instead be a crack length that makes the structure deflect unacceptably, or the length at which the remaining ligament reaches net-section yield;
- the stress range the part actually sees;
- the crack growth law, the Paris constants $A$ and $m$, measured in a fatigue test like the class's own fatigue lab.

| | Total life | Damage tolerant |
|---|---|---|
| Assumes | no significant defect; counts $N_i+N_g$ | a crack of known size is present |
| Data | S-N or strain-life curves for the right surface finish, Goodman, the load spectrum | $a_i$ from NDT, $K_{Ic}$, $\Delta\sigma$, $A$, $m$, $Q$ |
| In effect designs against | initiation | growth |
| Suits | parts that must not crack or cannot be inspected | inspectable structures that tolerate defects: airframes, vessels, welds |

## 7. Damage tolerance: integrating the Paris law

Plotting $da/dN$ against the stress intensity factor range $\Delta K$ on log–log axes gives a straight central region (ML2b, ll. 36–46). That straight line is the **Paris law**:

$$
\frac{da}{dN}=A\left(\Delta K\right)^m .
$$

Taking logarithms, $\log(da/dN)=\log A+m\log\Delta K$, so $m$ is the slope and $\log A$ the intercept. Only the tensile part of the cycle counts; while the crack is closed in compression nothing happens at the tip (ll. 51–54).

![[materials_paris_regimes_and_growth.png|900]]

The driving force is (ll. 75–78, 86–90)

$$
\Delta K=Q\Delta\sigma\sqrt{\pi a}.
$$

Substituting into the Paris law,

$$
\frac{da}{dN}=A\left(Q\Delta\sigma\sqrt{\pi a}\right)^m,
$$

and pulling the crack length out of the bracket,

$$
\frac{da}{dN}=A\left(Q\Delta\sigma\sqrt{\pi}\right)^m a^{m/2}.
$$

So the growth rate is not a constant: at a fixed stress range it rises as the crack grows. Taking the rate at one crack length and assuming it holds throughout would be wrong, which is why the life must be found by integration (ll. 90–100). Separate the variables, putting everything with $a$ on the left:

$$
\frac{da}{a^{m/2}}=A\left(Q\Delta\sigma\sqrt{\pi}\right)^m dN,
$$

and integrate from the initial crack $a_i$ at $N=0$ to the critical crack $a_c$ at $N=N_f$ (ll. 101–115):

$$
\int_{a_i}^{a_c}a^{-m/2}\,da=A\left(Q\Delta\sigma\sqrt{\pi}\right)^m\int_0^{N_f}dN .
$$

For $m\neq2$ the left side is

$$
\left[\frac{a^{1-m/2}}{1-m/2}\right]_{a_i}^{a_c}=\frac{a_c^{1-m/2}-a_i^{1-m/2}}{1-m/2},
$$

and the right side is $A(Q\Delta\sigma\sqrt\pi)^mN_f$. Solving for the life:

$$
N_f=\frac{a_c^{\,1-m/2}-a_i^{\,1-m/2}}{\left(1-\frac m2\right)A\left(Q\Delta\sigma\sqrt{\pi}\right)^m}.
$$

For the usual $m>2$ the exponent $1-m/2$ is negative, so both numerator and denominator are negative and $N_f$ comes out positive; keeping the signs explicit catches slips. If $m=2$ exactly, the integral is a logarithm instead: $N_f=\ln(a_c/a_i)/[A(Q\Delta\sigma\sqrt\pi)^2]$.

Before integrating you need $a_c$ from M1, using the peak stress:

$$
a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\sigma_{max}}\right)^2 .
$$

The numerator shows where the life is spent. With $m=3$, $a^{-1/2}$ is dominated by its value at the smallest crack, so when $a_c\gg a_i$ the life hardly depends on $a_c$ (and so on $K_{Ic}$) but depends strongly on $a_i$. Inspection resolution matters more than toughness.

> [!tip] Where the cycles go
> In the tutorial plate below, growing from 1 mm to 2 mm takes 34 % of the whole life to a 44.8 mm critical crack. A crack found early is worth far more than a slightly tougher alloy.

The lab class measures $a_i$, the growth rate and the applied stress range on a real specimen, generating the Paris curve that the integration then uses (ML2b, ll. 79–85). This mini-lecture was recorded in 2020–21, when the lab ran online (ll. 79–80).

## 8. Reducing fatigue

The lecturer frames prevention round a large steam-turbine blade (ML2c, ll. 6–49). Fatigue strength is controlled by stress concentrations at three scales, by residual stress, and by environment.

The macroscopic scale is the shape of the part. The fir-tree root where the blade slots into the disc has designed-in notches, and the first step in design is a hot-spot analysis: find the peak local stress by finite elements and read a life off the S-N curve (ll. 10–22). Generous fillets instead of sharp corners lower it (ll. 35–38). The next scale down is the surface roughness inside those notches; a profile of $R_a$ across a machined notch showed the roughest region exactly where the stress was highest (ll. 23–29). At the smallest scale is the microstructure: a crack in the blade steel had grown from an aluminium oxide stringer, an inclusion from steel-making (ll. 29–34). Each can be reduced: better notch geometry, a specified surface finish, cleaner material (ll. 35–38).

Residual stress can help or harm (ll. 39–46). A tensile residual stress, as left by a weld, pre-loads the part, so every service load adds to it. A compressive one must be overcome before the surface sees any tension at all.

### Shot peening

Shot peening fires small shot, sometimes glass beads, at the surface (ll. 50–59). Each impact makes a dimple and plastically stretches the material right under it, while the surrounding material is only loaded elastically. When the shot bounces off, the surroundings spring back towards their original shape and squeeze the stretched surface layer into compression. On a shot-peened low-pressure steam-turbine blade in tempered martensitic steel, X-ray diffraction measured about $-600$ MPa at the surface and nearly $-800$ MPa at about 100 µm depth, close to the yield strength, balanced by a tensile residual stress at about 400 µm, as equilibrium requires (ll. 60–73).

![[materials_shot_peening_residual_stress.png|800]]

The compressive layer sits exactly where fatigue cracks start. It changes the mean stress rather than the range (Section 4), which raises the fatigue limit and the high-cycle fatigue strength considerably, and the peening also work-hardens the surface, so it takes a higher stress to yield it further (ll. 73–84). The drawback is a rougher, dimpled surface, which on its own would be bad for fatigue (ll. 62–66). Peening is applied at stress concentrations such as the blade-root notches.

### Environment

S-N curves for an aluminium alloy fall from air to water to salt water (ll. 84–94). Corrosion pits form and act as ready-made initiation sites, and the environment may also attack grain boundaries or particular phases preferentially. In effect the initiation stage is removed and the part goes straight into crack growth, which is why the fatigue limit drops so far. The dinghy mast is a real case. At high temperature the environment can also speed up growth itself: in a NASA turbine-disc alloy tested hotter than discs normally run, cracks grew much faster in air than in vacuum, with an intergranular fracture surface, because oxygen attacks the grain boundaries and the Paris constants change (ll. 95–103; see [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]).

### Welds

A weld brings together almost everything bad for fatigue (ll. 104–125). Its shape and any lack of fusion or undercut are macroscopic and mesoscopic stress raisers; slag, porosity and small cracks are microscopic ones; the rapid heating and cooling varies the microstructure and the hardness across the weld, the heat-affected zone and the parent plate; and contraction on cooling leaves a tensile residual stress. The aluminium weld research in [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]] shows these effects measured.

## Worked examples

All numbers recomputed in Python.

### A tutorial plate grown from 1 mm

MT2 Q4, the lecturer's example: a large plate cycles between +120 and −30 MPa, with $a_i=1$ mm, $K_{Ic}=45$ MPa√m, $A=2\times10^{-12}$, $m=3$ and $Q=1$. The compressive part of the cycle closes the crack, so

$$
\Delta\sigma=120-0=120\text{ MPa}.
$$

The peak stress is also 120 MPa, so

$$
a_c=\frac1\pi\left(\frac{45}{1\times120}\right)^2=0.04476\text{ m}.
$$

With $1-m/2=-\tfrac12$,

$$
N_f=\frac{0.04476^{-1/2}-0.001^{-1/2}}{\left(-\tfrac12\right)\left(2\times10^{-12}\right)\left(120\sqrt\pi\right)^3}.
$$

The numerator is $4.727-31.623=-26.896$. The bracket is $120\sqrt\pi=212.7$, cubed $9.622\times10^6$, so the denominator is $-9.622\times10^{-6}$ and

$$
N_f=\frac{-26.896}{-9.622\times10^{-6}}=2.80\times10^6\text{ cycles}.
$$

Full precision gives 2,795,265 cycles; the tutorial's 2,801,904 comes from rounding the denominator to $9.6\times10^{-6}$. With a safety factor of 2, inspect again after about $1.4\times10^6$ cycles. Including the compressive part ($\Delta\sigma=150$ MPa) would have cut the predicted life by a factor $(150/120)^3\approx1.95$.

### Combined low- and high-cycle fatigue on a blade

MT2 Q2 (also 2018-19 A2(i)): a turbine blade has $N_{LCF}=150\,\Delta\varepsilon^{-1.5}$ for start-stop cycles and $N_{HCF}=7.5\times10^9\,\Delta\sigma^{-1.2}$ for vibration. It has seen 550 start-stops at $\Delta\varepsilon=0.23$ and $2.53\times10^6$ vibration cycles at 320 MPa. The lives are

$$
N_{LCF}=150\times0.23^{-1.5}=1360,
\qquad
N_{HCF}=7.5\times10^9\times320^{-1.2}=7.39\times10^6,
$$

so the damage so far is

$$
\frac{550}{1360}+\frac{2.53\times10^6}{7.39\times10^6}=0.404+0.342=0.747 .
$$

Future start-stops at $\Delta\varepsilon=0.18$ have $N=150\times0.18^{-1.5}=1964$, so the remaining life is

$$
n=\left(1-0.747\right)\times1964=498\text{ start-stops},
$$

or about 250 with a safety factor of 2. The full answer is Q2 of [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]].

### Every past-paper Paris calculation

The same recipe, with $Q=1.2$ throughout, all recomputed:

| Question | $a_i$ (mm) | $\sigma_{min}$/$\sigma_{max}$ (MPa) | $K_{Ic}$ | $A$, $m$ | $a_c$ (mm) | $N_f$ | Service life |
|---|---:|---|---:|---|---:|---:|---|
| 2013-14 B1 wing | 3 | 20/200 | 45 | 2.67e-10, 3 | 11.2 | 1,175 | 1,175 flights (SF 2: 588) |
| 2014-15 B1 = MT2 Q3 vessel | 4 | 10/150 | 65 | 1.58e-10, 3.5 | 41.5 | 963 | 963 cycles (SF 2: 482) |
| 2015-16 B1 offshore weld | 5 | 10/200 | 38 | 2.05e-11, 3.5 | 7.98 | 771 | 25.7 yr (SF 2: 12.9 yr) |
| 2016-17 A2 mixer shaft | 1.5 | 5/300 | 55 | 2.67e-10, 2.5 | 7.43 | 2,545 | 2,545 rev (SF 2: 1,272) |
| MT2 Q5 (Green Book $A$) | 1.5 | 5/300 | 55 | 2.67e-11, 2.5 | 7.43 | 25,449 | 25,449 rev (SF 2: 12,725) |
| 2017-18 A2 brewery weld | 1.35 | 15/225 | 38 | 2.2e-11, 4.5 | 6.31 | 143 | 143 days (SF 2: 71) |
| 2018-19 A2 IGT blade root | 3.3 | 34/195 | 75 | 4.5e-11, 3.8 | 32.7 | 862 | 431 days (SF 2: 216) |
| 2020-21 MQ2 water pipe | 1.8 | 30/350 | 47 | 2.45e-11, 3 | 3.99 | 2,002 | 143 weeks (SF 2: 71) |
| 2021-22 MQ2 reactor vessel | 1.4 ± 10 % | $\Delta\sigma$ 350; accident 550 | 70–76 | 2.45e-11, 3.2 | 3.58 (worst) | 850 (worst) | 8.1 yr worst (SF 2: about 4 yr) |
| 2022-23 MQ1 turbine disc | 1.5 | 25/550 | 125 | 7.35e-11, 2.5 | 11.4 | 2,641 | 2,641 flights (SF 2: 1,321) |
| 2023-24 MQ1 hip implant | 0.5 | 25/160 | 55 | 7.45e-12, 2.5 | 26.1 | 1.61e6 | 6.8 yr (SF 2: 3.4 yr) |
| 2024-25 MQ2 turbine disc | 1.5 | 30/450 | 95 | 2.45e-12, 3 | 9.85 | 18,030 | 18,030 flights (SF 2: 9,015) |

![[materials_paris_crack_growth_all_exams.png|900]]

In the 2021-22 vessel the ±10 % uncertainty in $a_i$ moves the life by about ±15 %, while ±3 MPa√m in $K_{Ic}$ moves it by about ±6 %, which is the sensitivity argument of Section 7 in numbers. Every answer should end with a safety factor or inspection interval and a list of limitations: no stage I or short-crack growth, constant $Q$, Paris constants measured in laboratory air rather than the service environment, no overload effects, and scatter in $K_{Ic}$ and $a_i$.

## Transcript slips

> [!warning] Mini-lectures ML1c–ML2c and the dinghy-mast video
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML1c, l. 74 | "microfiber coalescence" | microvoid coalescence |
> | ML1c, l. 75 | "plain stress" | plane stress |
> | ML1c, l. 76 | "fighting you fast catastrophic failure" | "where it broke, giving you fast catastrophic failure" |
> | ML1c, l. 97 | "the dabdn value" | $da/dN$ |
> | ML1c, l. 161 | "low normal stress" | low nominal stress |
> | ML2a, l. 5 | "recognitiates" | initiates |
> | ML2a, l. 40 | "poor" | pore |
> | ML2a, l. 125 | "2n to the nf, which is where nf is our number of sarcophilia" | $(2N_f)^b$, where $N_f$ is the number of cycles to failure |
> | ML2a, l. 144 | high-cycle fatigue "in terms of strain range" | in terms of stress amplitude; strain is the low-cycle measure (ll. 129–134) |
> | ML2a, l. 152 | "when the mean stress is zero and the stress amplitude is equal zero, the mean stress equals the tensile strength" | $\sigma_a=\sigma_{a0}$ when $\sigma_m=0$, and $\sigma_m=\sigma_{ts}$ when $\sigma_a=0$ (slide 28) |
> | ML2b, l. 6 | "minus rule" | Miner's rule |
> | ML2b, l. 52 | "stress density factor" | stress intensity factor |
> | ML2b, l. 61 | "die penetrant" | dye penetrant |
> | ML2b, ll. 65–66 | "lowering the fracture toughness … a quit calculation" | knowing the fracture toughness … an $a_{crit}$ calculation |
> | ML2b, l. 69 | "next section yield stress" | net-section yield |
> | ML2b, l. 102 | "a to the m minus two" | $a^{m/2}$ |
> | ML2b, l. 104 | "q delta sigma root pi a to the m" | $A(Q\Delta\sigma\sqrt\pi)^m$, with $a$ already moved to the left |
> | ML2b, l. 131 | "making the pores" | making the powders |
> | ML2b, l. 137 | "highly fasted" | highly faceted |
> | ML2b, l. 153 | "turbine discard" | turbine disc |
> | ML2c, l. 4 | "Paris-Lord type integrations for downward-tolerant lifing" | Paris-law integrations for damage-tolerant lifing |
> | ML2c, ll. 10–11 | "blade route", "fir tree route" | root |
> | ML2c, l. 69 | "martensitic temperate steel" | tempered martensitic steel |
> | ML2c, l. 71 | "10 cell residual stress" | tensile residual stress |
> | ML2c, l. 74 | "placidly deformed" | plastically deformed |
> | ML2c, l. 85 | an aluminium alloy "in air with a fatigue limit" | aluminium alloys have no true fatigue limit (ML2a, ll. 89–91); read it as the endurance limit |
> | ML2c, l. 102 | "your cnn value" | the Paris constants $A$ and $m$ |
> | ML2c, ll. 107, 123, 125 | "this world", "across the world", "wells" | weld, welds |
> | Dinghy mast, l. 21 | "dengue mast" | dinghy mast |
> | Dinghy mast, l. 24 | "little back dots" | little black dots |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]] · Next: [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]
- Concepts: [[Fatigue Fracture Surface Features]] · [[S-N Curve and Basquin Law]] · [[Goodman Relation]] · [[Miner's Rule]] · [[Paris Law]] · [[Total Life vs Damage Tolerance]] · [[Shot Peening]] · [[Stress Intensity Factor]]
- Tutorial: [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]] · past papers: [[SESA2028 Past Paper Map]]
- Elsewhere: [[Spinning Disc Stress]] (why the disc bore is the critical site) · [[Lame Thick-Cylinder Solution]] (stresses in the pressure vessels of the lifing questions)

## Sources

- Structural Performance 2025 slides 21–40
- Mini-lecture transcripts ML1c (fatigue fracture surfaces), ML2a (micromechanisms and definitions), ML2b (total life and damage tolerance), ML2c (reducing fatigue), and the dinghy-mast video
- Worked numbers from [[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]] and the exam solutions in `03 - Exams & Past Papers/Solutions`, recomputed in Python

## Self-study tasks

The mini-lectures set two pause-and-think exercises: list what you need to calculate a fatigue life from an existing defect (ML2b, ll. 54–58) and judge whether a pictured weld will resist fatigue (ML2c, ll. 104–109). They also point to the fracture-surface tutorials and the consultancy report (ML1c, ll. 199–208) and to Paris-law lifing in the tutorials (ML2b, ll. 48–51, 116).

### Core

- [ ] List the data needed for a damage-tolerant life (ML2b, ll. 54–78). → [[#6. Total life against damage tolerance]]
- [ ] Derive the Paris-law life formula, then do the tutorial plate (ML2b, ll. 86–116; MT2 Q4). → [[#7. Damage tolerance: integrating the Paris law]] · [[#A tutorial plate grown from 1 mm]]
- [ ] Read the dinghy-mast surface: origins, ratchets, beach marks, final fracture and the loading (dinghy mast, ll. 1–35). → [[#1. Reading a fatigue fracture surface]]
- [ ] Judge the weld for fatigue resistance (ML2c, ll. 104–125). → [[#Welds]]
- [ ] Miner's rule for the turbine blade (MT2 Q2). → [[#Combined low- and high-cycle fatigue on a blade]]

### Further practice

- [ ] Use the loading chart to say what a fracture surface tells you about loading, stress level and stress concentration (ML1c, ll. 111–198). → [[#What the surface says about the loading]]
- [ ] Explain how shot peening works and why it helps high-cycle fatigue (ML2c, ll. 50–84). → [[#Shot peening]]
- [ ] Work through the past-paper Paris calculations in the table, starting with MT2 Q3. → [[#Every past-paper Paris calculation]] · [[SESA2028 Past Paper Map]]
