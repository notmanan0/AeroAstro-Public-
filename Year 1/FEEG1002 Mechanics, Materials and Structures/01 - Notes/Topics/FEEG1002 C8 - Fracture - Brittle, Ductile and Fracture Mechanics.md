---
title: "FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 23
tags: [feeg1002, materials, fracture, griffith, fracture-toughness, stress-intensity, dbtt]
aliases: ["Materials Lectures 11 and 12", "Failure of Materials 1 and 2", "Fracture mechanics"]
date: 2026-11-05
status: lectured
coverage: "Materials L11 (12 Nov 2024, ll. 1–1006): ductile and brittle failure, cup-cone fracture by void coalescence, intergranular and transgranular fracture surfaces, stress concentrations and the notched-rod demonstration, flaw length a and 2a, the Griffith energy balance and its limits. Materials L12 (18 Nov 2024, ll. 1–695): the crack-tip stress field, the stress intensity factor K = Yσ√(πa), fracture toughness K_IC, the link to Griffith, a design example, temperature and failure, the ductile-to-brittle transition and the effect of strengthening mechanisms, toughness and Charpy testing. Slide decks 12 and 13 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
next_topics: ["[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
key_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Ductile-to-Brittle Transition]]", "[[Engineering Stress-Strain Properties]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 12 - Failure of Materials 1 - Brittle vs Ductile and Griffiths.pdf", "02 - Sources/Materials/Lectures/Lecture 13 - Failure of Materials 2 - Fracture Mechanics.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 11 - Materials Failure of Materials 1.txt", "02 - Sources/Lectures/FEEG1002 Lecture 12 - Materials K fracture Mechanics.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 04 - Failure of Materials.pdf"]
---

# FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics

> [!abstract] Summary
> A ductile metal fails slowly after much plastic deformation, by voids forming round hard particles and joining up, leaving a dimpled cup-and-cone surface; a brittle material fails suddenly with almost no deformation, leaving flat cleavage or intergranular facets. Flaws concentrate stress at their tips, by $2\sqrt{a/\rho_t}$ for a crack of length $a$ and tip radius $\rho_t$. Griffith's energy balance gives the fracture stress of a brittle plate, $\sigma_c=\sqrt{2E\gamma_s/\pi a}$, and the stress intensity approach gives the design equation $K_{IC}=Y\sigma_f\sqrt{\pi a_c}$, where the fracture toughness $K_{IC}$ is a material property. BCC and HCP metals turn brittle in the cold because their yield stress rises above their (temperature-independent) fracture stress; FCC metals do not.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a flaw size and asks for the fracture stress, gives a stress and asks for the largest tolerable flaw, compares yield with fast fracture, or asks how temperature, crystal structure or a strengthening process affects ductile or brittle behaviour.
> - **Assumptions:** linear elastic fracture mechanics (no significant plasticity at the crack tip); $K_{IC}$ in plane strain; infinite plate ($Y=1$) unless a $Y$ is given; a surface flaw has length $a$, an internal flaw has length $2a$.
> - **Method:** 1. Halve the length of an internal crack to get $a$; a surface crack's length is $a$. 2. Fracture stress $\sigma_f=K_{IC}/(Y\sqrt{\pi a})$, or Griffith $\sigma_c=\sqrt{2E\gamma_s/(\pi a)}$. 3. Critical crack $a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma}\right)^2$. 4. Compare $\sigma_f$ with $\sigma_y$: whichever is lower happens first. 5. Apply a safety factor to the result.
> - **Common mistakes:** using the full length of an internal crack as $a$; mixing mm with MPa√m (convert $a$ to metres).
> - **Practise:** [[#Worked example - the pressure vessel question]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]] Q1–Q4

The point of studying failure is to stop it happening. Statics gives the average stress in a member, and a designer keeps it below the yield strength with a safety factor ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Using the properties in design|C4]]). Yet parts still break below their yield strength, and the reason is almost always a flaw: a hole, a sharp corner, a pore from casting, a quench crack. Around such a flaw the local stress can be many times the average. Whether the part then deforms and survives or cracks and fails depends on whether the material can yield at the crack tip, and that depends on the material, its microstructure and its temperature.

Fracture combines two ideas. The first is energy: a loaded component stores elastic strain energy like a spring, and a crack can grow only if growing releases enough of that energy to pay for the new surfaces it creates. That is Griffith's argument, and it gives a fracture stress that depends on the flaw size and two material constants. The second is the competition between yielding and fracture. If the yield stress is reached first, the material flows and blunts the crack; if the fracture stress is reached first, it cleaves. Because the yield stress of BCC iron climbs steeply as it gets colder ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Temperature and the yield stress|C4]]), steel that is ductile in summer can be brittle in winter.

A fracture surface also records how a part failed, which is why failure investigators protect them: the surfaces should never be pushed back together, because that destroys the evidence.

---

## 1. Ductile and brittle failure

### What the tensile test shows

A **ductile** material shows a large elongation to failure and absorbs a lot of energy, the area under its stress–strain curve; a **brittle** one fails at low elongation (below 5 %) with little energy absorbed, and a truly brittle ceramic is linear elastic right up to fracture. In a brittle failure the stored elastic energy is released suddenly, as noise, heat and the recoil of the broken ends; in a ductile failure it is dissipated in moving dislocations. Ductile failure is slow and gradual, with a crack that grows only as the load increases; brittle failure is rapid and catastrophic. Toughness, the total energy absorbed, is measured directly in an impact test ([[#Toughness and the Charpy test]]).

### Cup-and-cone fracture

A ductile tensile specimen necks down before it breaks, and usually breaks with a **cup-and-cone** appearance: one half has a rough, cratered centre and a raised rim, the other a matching cone. The sequence is:

1. Necking starts, and the stress concentrates in the neck, where the area is smallest.
2. Small voids form around hard second-phase particles, such as carbides in steel or θ particles in an aluminium–copper alloy.
3. The voids grow and coalesce into an internal crack across the centre of the neck.
4. The remaining outer ring of material shears, at about 45° to the load, as the internal crack grows by further void coalescence.
5. The specimen fails.

The voids form because the matrix is ductile and flows under stress while the hard particles keep their shape, so the matrix pulls away from them, like stretching putty with ball bearings in it. Under the scanning electron microscope a ductile fracture surface is covered in **dimples**, each the half of a void, often with the particle that started it still sitting at the bottom. The dimples were not there before the test; they are made by the fracture.

### Brittle fracture surfaces

A brittle specimen shows little or no necking, and the two halves fit back together. There are two kinds of brittle surface:

- **Intergranular** fracture runs along the grain boundaries, giving a rugged, three-dimensional surface in which the grain shapes can be seen. It happens when the boundaries are weak or carry a brittle phase, such as grain-boundary cementite in a hypereutectoid steel ([[FEEG1002 C7 - Steels and Precipitation Hardening#4. Carbon content and properties|C7]]).
- **Transgranular** fracture, or **cleavage**, passes through the grains by the successive breaking of atomic bonds along particular crystallographic planes, the cleavage planes: $\{100\}$ in steels. Each grain gives a flat facet at its own angle. Mica, which cleaves into atomically smooth sheets, is the extreme case.

| | Ductile | Brittle |
|---|---|---|
| Fracture surface | dimpled | flat |
| Deformation | lots of plastic | not appreciable (below 5 %) |
| Crack propagation | slow | rapid |
| Type of failure | gradual | catastrophic |

## 2. Stress concentrations

### Flaws raise the local stress

In a plain bar under tension, the lines along which force is carried run straight and evenly spaced. Put a hole or a crack in the bar and the lines cannot pass through it; they crowd round its edges, so the stress there is much higher than the average. Every hole, corner, groove, pore, inclusion or crack in a real part is such a **stress concentration**. A copper rod can be bent back and forth repeatedly, but the same rod with a small notch filed in it cracks at the notch on the first bend: at the root of the notch the local stress exceeds the yield and tensile strengths, although the average stress is the same.

![[m8_stress_concentration.png|900]]

### Flaw length: a and 2a

A flaw at the surface has one tip, and its length is $a$. A flaw inside the material has two tips, and its length is $2a$. The same formulas use $a$ in both cases, so the length of an internal crack must be halved. This halving is an exam question in its own right.

### How much the stress is raised

For an elliptical crack, the maximum stress at the tip is

$$
\boxed{\sigma_m=2\sigma_0\left(\frac{a}{\rho_t}\right)^{1/2}}
$$

where $\sigma_0$ is the applied (nominal) stress, $a$ the length of a surface crack (half the length of an internal one) and $\rho_t$ the radius of curvature of the crack tip. The ratio $\sigma_m/\sigma_0=2\sqrt{a/\rho_t}$ is the stress concentration factor. A long crack and a sharp tip both raise the stress: a crack 0.5 mm deep with a tip radius of 5 µm concentrates the stress 20 times. The formula is the sharp-crack limit ($a\gg\rho_t$) of the elliptical-hole result $\sigma_m=\sigma_0\left(1+2\sqrt{a/\rho_t}\right)$, and the full form is needed for a blunt notch: one of the same depth with a 1 mm radius concentrates the stress only about 2.4 times. Hence the design rule: avoid sharp 90° internal corners wherever possible, round them off, and keep surface flaws to a minimum.

## 3. The Griffith energy balance

### Two energies

Griffith's approach applies to brittle materials, with no plastic deformation, and considers energy rather than stress. Two energies matter:

- The **elastic strain energy** $U_E$ stored in the loaded material, like the energy in a stretched spring. When a crack forms, the material next to its faces is unloaded and this energy is released. It drives crack growth.
- The **surface energy** $U_S$ needed to create the two new crack faces. Atoms at a surface have lost some of their bonded neighbours, so a solid–gas interface has a higher energy than the bulk, by $\gamma_s$ per unit area (J/m²). It resists crack growth.

The crack propagates when the elastic strain energy released is just sufficient to provide the surface energy for the new surfaces.

### Setting up the balance

Take a thin plate of unit thickness, loaded by a remote tensile stress $\sigma$, containing an internal crack of length $2a$ perpendicular to the load.

The elastic strain energy per unit volume in a linear elastic material under stress $\sigma$ is the area under the stress–strain line ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Resilience and toughness|C4]]), $\tfrac12\sigma\varepsilon$. Introducing the crack unloads a region of material around it. Treating this region as a volume of $2\pi a^2$ per unit thickness (the "fudge" factor of 2 on a circle of radius $a$ comes from the full elasticity solution), the strain energy released is

$$
U_E=\tfrac12\sigma\varepsilon\times2\pi a^2
$$

Substitute $\varepsilon=\sigma/E$:

$$
U_E=\tfrac12\sigma\frac{\sigma}{E}\times2\pi a^2
$$

$$
U_E=\frac{\pi a^2\sigma^2}{E}
$$

The surface energy is the area of new surface times $\gamma_s$. The crack has two faces, each of length $2a$ per unit thickness:

$$
U_S=2\times2a\times\gamma_s=4a\gamma_s
$$

The total energy change on introducing the crack is the surface energy gained minus the strain energy released:

$$
U=4a\gamma_s-\frac{\pi a^2\sigma^2}{E}
$$

.

![[m8_griffith_energy.png|900]]

### The critical condition

$U_S$ grows in proportion to $a$, but $U_E$ grows with $a^2$, so for small cracks the surface term wins and $U$ rises with $a$, while for large cracks the strain-energy term wins and $U$ falls. $U$ has a maximum at a critical crack length $a_c$. A crack shorter than this would have to absorb energy to grow; a crack longer than this releases more energy than it uses, so it grows on its own, faster and faster. The crack therefore grows when the strain energy release rate is greater than or equal to the rate of increase of surface energy with crack length. At the maximum,

$$
\frac{dU}{da}=\frac{dU_S}{da}-\frac{dU_E}{da}=0
$$

Differentiate each term:

$$
\frac{dU_S}{da}=4\gamma_s,\qquad\frac{dU_E}{da}=\frac{2\pi a\sigma^2}{E}
$$

$$
4\gamma_s-\frac{2\pi a\sigma^2}{E}=0
$$

Solve for the stress at which a crack of half-length $a$ becomes critical, the fracture stress $\sigma_c$:

$$
\sigma_c^2=\frac{4\gamma_sE}{2\pi a}=\frac{2E\gamma_s}{\pi a}
$$

$$
\boxed{\sigma_c=\sqrt{\frac{2E\gamma_s}{\pi a}}}
$$

The fracture stress depends on the modulus, the surface energy and the size of the flaw. As $a$ increases, $\sigma_c$ falls, so as a crack grows the stress needed to drive it falls and the crack accelerates. For a brittle component this replaces the UTS in design: measure the largest flaw present (by X-ray computed tomography, or surface profilometry for surface flaws), and keep the stress below $\sigma_c$ for that flaw.

### Limits of the Griffith result

The result holds for thin plates in plane stress with no plastic deformation at the crack tip: it is part of **linear elastic fracture mechanics** (LEFM). Ceramics and glasses, and concrete, satisfy this well. Metals do not: plastic flow at the tip blunts it and absorbs far more energy than the surface energy, which is why Griffith's formula with the true surface energy greatly underestimates their fracture stress. Within the model, $E$ and $\gamma_s$ are material constants that hardly change with temperature, so the brittle fracture stress is taken to be independent of temperature; that assumption is used in [[#5. The ductile-to-brittle transition]].

## 4. The stress intensity factor

### The crack-tip stress field

The second approach, more widely used in engineering, looks at the stress just ahead of the crack tip. For an infinite plate, whose edges are too far away to matter, at a distance $r$ ahead of the tip of a sharp crack, linear elasticity gives a local stress

$$
\sigma_{local}=\frac{K}{\sqrt{2\pi r}}
$$

The stress is very high near the tip and falls away with distance, and the whole field scales with a single number $K$, the **stress intensity factor**, which describes the magnitude of the local crack-tip stress field. (As $r\to0$ the expression gives an infinite stress; real materials yield or cleave first, and the formula is used a little way from the tip.) $K$ is found from the applied stress and the crack length,

$$
K=\sigma\sqrt{\pi a}
$$

a separate result from the field expression, not derived from it. Doubling the applied stress doubles $K$ and with it the whole tip field.

### Fracture toughness

As the applied stress rises, $K$ rises, and at some point the local stress reaches the value needed for fracture. The value of $K$ at that point is the critical stress intensity factor $K_c$, the **fracture toughness**:

$$
K_c=\sigma_f\sqrt{\pi a_c}
$$

where $\sigma_f$ is the applied stress at fracture and $a_c$ the critical crack length. For a given material, a larger crack means a lower fracture stress, and the other way round. For a real specimen of finite size and a crack of any shape, a dimensionless geometry factor $Y$ is added:

$$
\boxed{K_c=Y\sigma_f\sqrt{\pi a_c}}
$$

$Y$ depends on the crack and specimen sizes and geometries and on how the load is applied, and is looked up in engineering data books; the infinite plate has $Y=1$.

### KIC as a material property

$K_c$ measured on a thin plate depends on the thickness. If the specimen is thick enough to be in **plane strain**, constrained so that it cannot strain through its thickness at the crack tip, $K_c$ falls to a minimum value that does not depend on the specimen: the **plane strain fracture toughness** $K_{IC}$, a material property as long as the linear elastic assumptions hold. The subscript I refers to **Mode I**, crack opening, with the load pulling the crack faces apart; this is the mode most commonly reported and easiest to test. Modes II and III load the crack in shear in different ways. Units are MPa√m.

### The link to Griffith

The two approaches agree. From Griffith,

$$
\sigma_f=\sqrt{\frac{2E\gamma_s}{\pi a}}
$$

Multiply both sides by $\sqrt{\pi a}$:

$$
\sigma_f\sqrt{\pi a}=\sqrt{2E\gamma_s}
$$

The left-hand side is $K_c$ for an infinite plate, so

$$
\boxed{K_c=\sqrt{2E\gamma_s}}
$$

Since $E$ and $\gamma_s$ are material constants, so is $K_c$, for an ideally brittle material. A low fracture toughness means the material tolerates very little stress intensification before it breaks; a high one means it resists crack growth.

### Using fracture mechanics in design

The equation $K_{IC}=Y\sigma\sqrt{\pi a}$ is used in two directions. If the flaws left by manufacture are known, the stress that must not be approached in service is

$$
\sigma_f=\frac{K_{IC}}{Y\sqrt{\pi a}}
$$

If the service stresses are known, the largest flaw that can be allowed to remain after manufacture is found by squaring and rearranging:

$$
a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma}\right)^2
$$

The service stresses must include one-off shocks, not just the routine load: stumbling on a kerb puts many times body weight through a hip replacement, and aircraft meet turbulence and ships freak waves. A safety factor is then applied to the calculated fracture stress; for something like a nuclear pressure vessel, more than the usual factor of 2.

## 5. The ductile-to-brittle transition

### Two competing stresses

Whether a metal fails in a ductile or a brittle way depends on which happens first as the load rises: yielding at the crack tip, which blunts it, or fracture.

The brittle fracture stress depends on $E$, $\gamma_s$ and the flaw size, all treated as independent of temperature, so $\sigma_f$ is roughly constant with temperature.

The yield stress depends on how easily dislocations move. In FCC metals, with many close-packed slip planes always well oriented to the load, the yield stress is almost independent of temperature. In BCC metals, which have no close-packed planes, and HCP metals, where most dislocation motion is on non-close-packed planes, moving a dislocation needs thermal help, so the yield stress rises as the temperature falls. In the Hall–Petch relation it is the friction term $\sigma_0$ that carries this temperature dependence.

For an FCC metal the yield stress is below the fracture stress at every temperature, so it always yields first and fails in a ductile way. For a BCC metal, cooling raises the yield stress until it crosses the fracture stress. Below that crossing the material reaches its fracture stress before it can yield, so it fractures with no plastic deformation: it is brittle. The temperature of the crossing is the **ductile-to-brittle transition temperature** (DBTT). Steels, which are BCC ferrite at room temperature, show a transition; aluminium, copper and austenitic stainless steel do not.

![[m8_dbtt_mechanism.png|900]]

### Strengthening moves the transition

Anything that changes $\sigma_y$ or $\sigma_f$ moves the crossing.

Work hardening, precipitation hardening and solid-solution strengthening all raise the yield stress but leave the fracture stress unchanged. The yield curve moves up, the crossing moves to a higher temperature, and the DBTT rises: the metal becomes more brittle.

Grain refinement is the exception. It raises the yield stress (Hall–Petch), but it also raises the fracture stress, because a cleavage crack has to change direction onto a new cleavage plane at every grain boundary, and smaller grains mean more changes. The fracture stress rises more than the yield stress, the crossing moves to a lower temperature, and the DBTT drops: the metal is both stronger and tougher. Grain refinement is the only common strengthening mechanism that improves both.

### Toughness and the Charpy test

**Toughness**, the ability of a material to absorb energy up to fracture, is the area under the whole stress–strain curve; it is not the same as fracture toughness, $K_{IC}$. Ductile failures absorb more energy, so ductile materials are tougher. Toughness is measured at high strain rate in the **Charpy impact test**: a weighted pendulum is released from a height $h$, strikes and breaks a notched specimen, and swings on to a lower height $h'$; the energy absorbed is the difference in potential energy, $mg(h-h')$. Plotted against temperature, the impact energy of a BCC steel drops sharply from a high upper shelf to a low lower shelf across the transition, while an FCC metal stays high at all temperatures.

![[m8_impact_energy.png|900]]

The *Titanic* is the classic case. Its hull steel was near or below its transition temperature in the near-freezing North Atlantic, so where the iceberg struck, the plates fractured with little plastic deformation and opened the hull in many places; warmer water would have let the plates deform instead. Modern ship steels are made with much lower transition temperatures.

---

## Worked examples

### Worked example - the pressure vessel question

A nuclear pressure vessel has $K_{IC}=40$ MPa√m and $Y=1.2$, and the manufacturing process has left internal quench cracks about 3 mm long. What stress would cause fracture, and what is a sensible allowable stress?

The cracks are internal, so $2a=3$ mm and $a=1.5$ mm $=1.5\times10^{-3}$ m. Then

$$
\sigma_f=\frac{K_{IC}}{Y\sqrt{\pi a}}=\frac{40\times10^6}{1.2\times\sqrt{\pi\times1.5\times10^{-3}}}
$$

$$
\sigma_f=\frac{40\times10^6}{1.2\times0.06865}=4.86\times10^8\ \mathrm{Pa}=486\ \mathrm{MPa}
$$

which is option 4. Using the full 3 mm as $a$ would give 343 MPa, option 1, which is exactly the trap the question sets. 486 MPa is the stress at which the vessel breaks, not the stress it should see. With a factor of 2 the allowable stress is 243 MPa, and for a nuclear vessel a larger factor would be used.

> [!check] Critical crack at a working stress
> At a service stress of 200 MPa, the largest tolerable crack is $a_c=\frac1\pi\left(\frac{40}{1.2\times200}\right)^2=8.8\times10^{-3}$ m, an internal crack 17.7 mm long. The 3 mm quench cracks are well inside that, consistent with $\sigma_f=486$ MPa being well above 200 MPa.

### Worked example - Griffith strength of glass

A glass has $E=69$ GPa and surface energy $\gamma_s=0.3$ J/m². Find the fracture stress of a plate containing an internal crack 2 µm long, and the largest internal crack that can be tolerated at a stress of 40 MPa.

Here $a=1\times10^{-6}$ m:

$$
\sigma_c=\sqrt{\frac{2E\gamma_s}{\pi a}}=\sqrt{\frac{2\times69\times10^9\times0.3}{\pi\times1\times10^{-6}}}=\sqrt{1.318\times10^{16}}=1.15\times10^8\ \mathrm{Pa}
$$

115 MPa. Rearranging for the crack at 40 MPa:

$$
a=\frac{2E\gamma_s}{\pi\sigma^2}=\frac{2\times69\times10^9\times0.3}{\pi\times(40\times10^6)^2}=8.2\times10^{-6}\ \mathrm m
$$

so an internal crack of $2a=16$ µm. Cracks of a few micrometres, invisible to the eye, are enough to bring glass down to the strengths of 50–100 MPa that are measured in practice, far below the theoretical strength of its bonds. The corresponding $K_c=\sqrt{2E\gamma_s}=0.20$ MPa√m; the measured fracture toughness of glass, about 0.7 MPa√m, is higher because even glass dissipates some energy at a running crack beyond the bare surface energy.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C7 - Steels and Precipitation Hardening]] · Next: [[FEEG1002 C9 - Fatigue, Creep and Corrosion]]
- Concepts: [[Griffith Criterion and Fracture Toughness]] · [[Ductile-to-Brittle Transition]] · [[Engineering Stress-Strain Properties]]
- Worked sheet: [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]] (Q1–Q4) · Formula list: [[FEEG1002 Formula Sheet]]
- Statics: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] (nominal stress and stress concentrations) · [[FEEG1002 B6 - Yield Criteria]] (ductile yield under combined stress)
- Year 2: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]] · [[Griffith Energy Balance]] · [[Stress Intensity Factor]] · [[Fracture Toughness and LEFM Validity]] · [[Ductile-Brittle Transition]]

## Sources

- `FEEG1002 Lecture 11 - Materials Failure of Materials 1.txt` (L11, 12 Nov 2024): why study failure (ll. 69–132), ductile and brittle in the tensile test (ll. 133–243), cup-and-cone fracture (ll. 244–371), brittle fracture surfaces (ll. 372–488), stress concentrations and the notched rod (ll. 489–609), a and 2a (ll. 610–645), tip radius (ll. 646–671), the Griffith approach (ll. 672–940), its limits (ll. 941–980).
- `FEEG1002 Lecture 12 - Materials K fracture Mechanics.txt` (L12, 18 Nov 2024): the crack-tip field and K (ll. 66–176), K_c and Y (ll. 177–255), K_IC and loading modes (ll. 255–283), the link to Griffith (ll. 284–319), design use (ll. 320–351), the pressure-vessel example (ll. 352–484), temperature and the DBTT (ll. 485–601), strengthening and the DBTT (ll. 602–648), toughness, Charpy and the *Titanic* (ll. 649–688).
- `Lecture 12 - Failure of Materials 1 - Brittle vs Ductile and Griffiths.pdf` (slide deck 12) and `Lecture 13 - Failure of Materials 2 - Fracture Mechanics.pdf` (slide deck 13), including the Vevox pressure-vessel question with solution. Figures after Callister and Anderson.
- `Tutorial Sheet 04 - Failure of Materials.pdf`: Q1–Q4 on this note (Q5–Q7 belong to [[FEEG1002 C9 - Fatigue, Creep and Corrosion|C9]]).

## Self-study tasks

### Core

- [ ] Tutorial 4, Q1: sketch toughness against temperature for Mg (HCP), stainless steel (FCC) and iron (BCC) and explain. → [[#5. The ductile-to-brittle transition]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q1 - Toughness against temperature]]
- [ ] Tutorial 4, Q2: largest tolerable flaw in fused silica at 35 MPa. Target $a=0.157$ mm. → [[#The critical condition]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q2 - Griffith flaw size in fused silica]]
- [ ] Tutorial 4, Q3: fast-fracture stress of a pressure-vessel plate with 1.6 mm internal cracks, and yield or fracture first. Target 1.30 GPa, so it yields first. → [[#Using fracture mechanics in design]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q3 - Fast fracture or general yield in a pressure-vessel plate]]
- [ ] Tutorial 4, Q4b: what safety factor for the pressure vessel. → [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q4 - Safety factor for the pressure vessel]]
- [ ] The Vevox pressure-vessel question, with the a and 2a trap flagged for the exam (L12, ll. 352–484; L11, ll. 639–644). Target 486 MPa. → [[#Worked example - the pressure vessel question]]

### Further practice

- [ ] Derive the Griffith fracture stress from $U=4a\gamma_s-\pi a^2\sigma^2/E$, filling in the differentiation skipped in the lecture (L11, ll. 896–898). → [[#The critical condition]]
- [ ] Explain why grain refinement lowers the DBTT while work hardening raises it (L12, ll. 602–648). → [[#Strengthening moves the transition]]

## Transcript and slide slips

> [!warning] Transcript slips (L11, ll. 865 and 974–979)
> Where: [[#The critical condition]] · [[#Limits of the Griffith result]].
>
> The growth criterion is garbled as "the release rate is greater or equal to the rate of change in the crack length of energy"; the slide's wording is right: the crack grows when the strain energy release rate, $dU_E/da$, is at least the rate of increase of surface energy, $dU_S/da$. The fracture stress is called "independent of temperature" because $E$ and $\gamma_s$ are; that is a modelling assumption (the modulus does fall slightly with temperature), used to explain the DBTT.

> [!warning] Transcript slips (L12, ll. 291, 466, 525–528 and 533)
> Where: [[#The link to Griffith]] · [[#Two competing stresses]].
>
> $K_c$ is read out as "equal to 2 modulus times surface energy"; it is the square root, $\sqrt{2E\gamma_s}$. At l. 466 a flaw gives a bigger stress "because you have a higher cross-sectional area"; it is a smaller one. At ll. 525–528 FCC is said not to show "temperature independence"; it shows temperature independence (no dependence). The thermally activated slip of BCC metals is described as a "slight diffusional component"; it is thermal activation over the lattice resistance, not diffusion.

> [!warning] Transcript slip (L12, ll. 670–676)
> Where: [[#Toughness and the Charpy test]].
>
> The *Titanic*'s hull steel is said to have had a transition temperature "just below zero". Charpy tests on steel recovered from the wreck put its transition well above that, at roughly +30 to +55 °C depending on orientation, against a sea temperature of about −2 °C. The plates were far below their transition temperature, which strengthens the point being made.

> [!warning] Griffith in plane stress, K_IC in plane strain (slides, decks 12 and 13)
> Where: [[#The link to Griffith]].
>
> Griffith's result is stated for thin plates in plane stress, while $K_{IC}$ is a property only in plane strain, and $K_c=\sqrt{2E\gamma_s}$ links the two without comment. In plane strain $E$ would strictly be replaced by $E/(1-\nu^2)$, a change of about 10 % for $\nu=0.3$. The course uses the simple form, which is enough for the trend.
