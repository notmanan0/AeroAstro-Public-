---
title: "SESA2028 M1 - Fracture, Toughness and Fracture Mechanics"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 1
tags: [sesa2028, materials, fracture, toughness, fracture-mechanics, lefm]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[Stress Concentration Factor and Factor of Safety]]", "[[Plane Stress and Plane Strain]]"]
next_topics: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
key_concepts: ["[[Stress Intensity Factor]]", "[[Fracture Toughness and LEFM Validity]]", "[[Griffith Energy Balance]]", "[[Ductile-Brittle Transition]]", "[[Plane Strain Constraint]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Structural Performance 2025.pdf (lectures 0-1)", "mini lectures ML0a, ML0b, ML1a, ML1b"]
---

# SESA2028 M1 - Fracture, Toughness and Fracture Mechanics

> [!abstract] Summary
> Toughness is a material's resistance to fracture **when a notch or defect is present**. Charpy tests rank materials, but they cannot be used for design. Fracture mechanics can: the stress intensity factor $K=Q\sigma\sqrt{\pi a}$ combines applied stress and defect size into one crack-tip parameter. Fast fracture occurs when $K$ reaches the material's fracture toughness $K_{Ic}$. That one idea gives the critical crack size used in every Paris-law lifing question in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]].

## 1. Where this fits: the five failure modes

The structural-performance block covers the ways a component stops doing its job:

| Mode | Driver | Where it is treated |
|---|---|---|
| Fracture | stress in the presence of a stress concentration | this note |
| Fatigue | cyclic loading: initiation and growth of a defect | [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing\|M2]] |
| Corrosion | wet (electrochemical) or dry (oxidation) attack | [[SESA2028 M3 - Corrosion, Wear and Surface Engineering\|M3]], [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys\|M8]] |
| Wear | surface degradation, so local surface properties matter | [[SESA2028 M3 - Corrosion, Wear and Surface Engineering\|M3]] |
| Creep | time-dependent deformation above about $0.4T_m$ | [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys\|M8]] |

Most exam questions describe a real component (wing, disc, pipe, implant). You are expected to decide which of these modes limits its life before you calculate anything.

## 2. Ductile versus brittle fracture

### Ductile: the cup-and-cone

1. A neck forms. It acts as a shallow notch, so the centre of the neck becomes **triaxially** stressed.
2. Microvoids nucleate around hard second-phase particles. The lecturer's analogy is "ball bearings in plasticine".
3. The voids grow and coalesce into an internal crack in the centre of the neck.
4. The remaining thin outer ring is effectively a thin sheet (plane stress). It fails by shear on planes at about $45^\circ$ to the load, which forms the **shear lip**, the "cup".

Under the SEM the surface is **dimpled**: each dimple is half of a coalesced microvoid.

### Brittle: cleavage and intergranular

- There is little prior plastic deformation, and the crack runs fast. It is catastrophic.
- **Transgranular** (cleavage) cracks go straight across grains and leave flat, glinting facets.
- **Intergranular** cracks follow grain boundaries, so the surface shows the 3D outlines of the grains. The crack takes whichever path is weaker, for example grain boundaries embrittled by segregated S or P.
- **River lines** are left because the unstable crack front runs on slightly different planes. The "tributaries" join in the direction the crack travelled, so tracing them backwards leads to the initiation site.

| | Ductile | Brittle |
|---|---|---|
| Fracture surface | dimpled, dull, fibrous | flat, faceted, shiny |
| Plastic deformation | extensive (necking) | little or none |
| Crack propagation | slow, needs continued work | rapid, self-sustaining |
| Failure | gradual, with warning | catastrophic |

## 3. Measuring toughness

A smooth tensile test gives $E$, $\sigma_y$ and elongation (below about 5 % elongation is conventionally called brittle). It says nothing about behaviour at a notch. Toughness needs a **notched** test.

**Charpy impact test.** A notched bar is broken in three-point bending by a swinging pendulum, and the absorbed energy is read off a dial.

- A ductile failure gives high impact energy (IE); a brittle failure gives low IE.
- It is excellent for **ranking and quality control** (batch-to-batch consistency, finding the transition temperature).
- It is **not usable for structural design**, because it gives an energy with no link to stress or defect size. That link is what $K$ provides (Section 6).

## 4. The ductile-brittle transition (DBT)

![[Figures/materials_ductile_brittle_transition.png]]

Whether a material fails by yielding or by fracture is a competition between two stresses:

- the **fracture (cleavage) stress** $\sigma_f$, which is roughly independent of temperature;
- the **yield stress** $\sigma_y(T)$, which depends on crystal structure.

| Crystal structure | Slip behaviour | Consequence |
|---|---|---|
| FCC (Al, Cu, Ni, austenite) | many close-packed slip systems, no thermal activation needed | $\sigma_y$ roughly flat, so always ductile, no DBT |
| BCC (ferrite, mild steel) | no close-packed planes; slip is thermally activated | $\sigma_y$ rises steeply at low $T$; below the crossover $\sigma_f$ is reached first, so brittle |
| HCP (Mg, Ti, Zn) | close-packed basal plane but too few slip systems | non-basal slip is thermally activated, so a DBT is possible |

On a Charpy plot this appears as an upper shelf (ductile), a transition region and a lower shelf (brittle). **Increasing the carbon content** of steel raises strength, lowers the upper-shelf energy and pushes the DBT temperature up.

> [!example] Ship steels (ML11a)
> The Charpy 27 J transition temperature of the Titanic's hull plate was about $42^\circ$C longitudinally and $61^\circ$C transversely. Modern A36 ship steel is about $-18^\circ$C. Liberty-ship steels averaged about $23^\circ$C, so they were brittle in the cold North Atlantic. Ship steels have improved through grain-size control, low S and P (both segregate to grain boundaries), and higher Mn (which ties S up as MnS).

See [[Ductile-Brittle Transition]].

## 5. Stress concentrations and the crack tip

An elastic notch raises the local stress by the stress concentration factor $K_t$. For an elliptical hole of half-axes $a$ (perpendicular to the load) and $b$,

$$
K_t = 1+\frac{2a}{b},
$$

which gives $K_t=3$ for a circular hole. Deeper or sharper notches (larger $a/b$, smaller root radius) raise $K_t$. A crack is the limiting case: $b\to0$ and $K_t\to\infty$. At that point $K_t$ stops being useful and the **stress intensity factor** takes over. See [[Stress Concentration Factor and Factor of Safety]] (SESA2029).

Ahead of a sharp crack, linear elasticity gives a singular field:

$$
\sigma_{ij}=\frac{K}{\sqrt{2\pi r}}\,f_{ij}(\theta)+\text{higher-order terms}.
$$

Real materials cannot sustain an infinite stress. Where $\sigma_{11}>\sigma_y$ the material yields and the stress is **redistributed**, producing a **plastic (process) zone** at the tip. Fracture is controlled by the weakest microstructural feature inside this small zone, such as a brittle particle, a weak grain boundary or a large grain.

![[Figures/materials_crack_tip_plastic_zone.png]]

The $1/\sqrt r$ singularity is the same one that a mesh-refinement study fails to converge on in FEA; see [[Stress Singularities]].

## 6. Two routes to the same fracture criterion

### Griffith energy balance (global)

If a crack grows, two new surfaces are created. That costs energy $2\gamma$ per unit area, where $\gamma=\gamma_e$ (surface energy) for a brittle solid or $\gamma_e+\gamma_p$ if a plastic zone must be dragged along. The energy is supplied by release of stored elastic strain energy. Balancing the two gives

$$
\sigma_f=\sqrt{\frac{E\,G_c}{\pi a}},\qquad G_c=2(\gamma_e+\gamma_p).
$$

Because $\gamma_p\gg\gamma_e$ in metals, **ductile materials are much tougher**: most of the resistance is plastic work, not surface energy. See [[Griffith Energy Balance]] and the strain-energy ideas in [[Strain Energy]].

### Stress intensity factor (local)

The local route describes the crack-tip field by the single parameter

$$
K = Q\,\sigma\sqrt{\pi a},
$$

where $Q$ (also written $Y$) is a geometry/shape factor. Take $a$ as the depth of a surface crack or **half** the length of an internal crack. Fast fracture occurs when

$$
K = K_c=Q\sigma_f\sqrt{\pi a}=\sqrt{E\,G_c}.
$$

The two routes are therefore equivalent. $K$ is useful because it:

- describes the local crack-tip stresses and strains;
- links directly to the energy-balance picture;
- can be calculated from specimen dimensions and external loads alone.

See [[Stress Intensity Factor]].

### Critical crack size

Rearranging for the defect size that causes fast fracture at the peak service stress:

$$
\boxed{a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\,\sigma_{max}}\right)^2}
$$

> [!example] 2013-14 B1(ii): lower-wing 7xxx alloy
> $K_{Ic}=45\ \mathrm{MPa\sqrt m}$, $\sigma_{max}=200$ MPa, $Q=1.2$:
> $$a_c=\frac1\pi\left(\frac{45}{1.2\times200}\right)^2=0.01119\ \mathrm m=11.2\ \mathrm{mm}.$$
> Always use $\sigma_{max}$ here, not the stress range: fast fracture happens at the peak of the cycle.

## 7. Fracture toughness $K_{Ic}$ and when LEFM is valid

**Mode I** (opening) is the most damaging mode, and most brittle failures follow the path of maximum opening stress. So the design property is $K_{Ic}$, the plane-strain mode-I fracture toughness.

**Validity rule of thumb.** Linear elastic fracture mechanics (LEFM) still works when the plastic zone is small compared with the crack length, the uncracked ligament and the thickness: about **1/50 of each**. Then the $K$-dominated field still controls failure events at the tip.

### Thickness effect

$K_{crit}$ measured on thin specimens is higher than on thick ones, and it falls to a plateau as thickness increases. **Only the plateau value is a material constant**: that is $K_{Ic}$.

| | Thin section (plane stress) | Thick section centre (plane strain) |
|---|---|---|
| Through-thickness stress | $\sigma_{33}\approx0$ | $\varepsilon_{33}\approx0$, so $\sigma_{33}\neq0$ |
| Stress state | biaxial | **triaxial**: high constraint |
| Max. resolved shear | at $45^\circ$ to load, so easy yielding | yielding suppressed |
| Fracture profile | slant ($45^\circ$ shear lips) | flat, square |
| Toughness | higher | lowest, so most critical for design |

This is why a thick fracture surface has a flat centre with shear lips at the free surfaces. See [[Plane Strain Constraint]] and [[Plane Stress and Plane Strain]].

## 8. Loading modes and torsion failures

| Mode | Crack-face motion |
|---|---|
| I - opening | faces pulled apart normal to the crack plane |
| II - sliding | in-plane shear |
| III - tearing | anti-plane shear (twisting) |

- **Brittle** failure follows the plane of **maximum opening (principal) stress**.
- **Yield** needs **shear stress** so that dislocations can move.

Under torsion, the maximum shear acts on planes along and perpendicular to the shaft axis, and the maximum opening stress acts at $45^\circ$ (the lecture rubber-tube demonstration). So:

- a **ductile** shaft fails in torsion on a **flat plane perpendicular to the axis**, after some twisting;
- a **brittle** shaft (the chalk demonstration) fails on a **$45^\circ$ helix**, the maximum opening-stress surface.

Bending can be unidirectional, reversed, or rotating (off-axis rotation). Each leaves a different fatigue fracture pattern ([[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]).

## 9. Factors that control toughness

- **Temperature**: toughness falls at low $T$ in BCC and HCP metals (DBT).
- **Ductility**: plastic flow redistributes crack-tip stress and absorbs work, so ductile materials are much tougher.
- **Strength**: high-strength materials generally have low toughness (ceramics are the extreme case). Improving toughness at high strength is difficult ([[Titanium Alloy Classes]] shows this trade-off).
- **Strain rate**: faster loading lowers toughness because there is no time for crack-tip plasticity.
- **Microstructure**:
  - for brittle intergranular failure, minimise brittle species on grain boundaries;
  - for transgranular failure, remove large brittle particles and defects inside grains;
  - large grains allow long slip-band pile-ups, which can initiate cleavage;
  - for ductile failure, optimise the second-phase particle distribution to delay microvoid coalescence.

**Ashby maps** (for example $K_{Ic}$ against density on log-log axes) compare materials on more than one property. Composites reach alloy-like toughness at much lower density.

## 10. Exam checklist

1. Say whether the failure is ductile or brittle **and give the evidence** (dimples or facets, shear lips, river lines).
2. For numerical fracture problems, write $K=Q\sigma\sqrt{\pi a}$ with $a$ in **metres** so that $K$ comes out in $\mathrm{MPa\sqrt m}$.
3. Use $\sigma_{max}$ (not $\Delta\sigma$) in $a_c$.
4. State that $K_{Ic}$ is a plane-strain value, which is conservative for thin sections.
5. Charpy gives ranking, not design data.

## Related

- [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]: $a_c$ is the upper limit of every Paris integral.
- [[Stress Concentration Factor and Factor of Safety]], [[Stress Singularities]], [[Plane Stress and Plane Strain]], [[Von Mises and Tresca Yield Criteria]] (SESA2029).
- [[Strain Energy]] (SESA2028 structures): the energy released in Griffith's balance.

## Year 1 foundation
- Principal stresses and yield criteria in [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] and [[FEEG1002 B6 - Yield Criteria]]. Impact energy and restitution in [[FEEG1002 D4 - Linear Impulse and Momentum]].
