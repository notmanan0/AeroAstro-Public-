---
title: "SESA2028 M1 - Fracture, Toughness and Fracture Mechanics"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 1
tags: [sesa2028, materials, fracture, toughness, fracture-mechanics, lefm]
status: lectured
coverage: "Mini-lectures ML0a, ML0b, ML1a and ML1b (structural performance block, weeks 1-3 of semester 2)"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[Stress Concentration Factor and Factor of Safety]]", "[[Plane Stress and Plane Strain]]"]
next_topics: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
key_concepts: ["[[Stress Intensity Factor]]", "[[Fracture Toughness and LEFM Validity]]", "[[Griffith Energy Balance]]", "[[Ductile-Brittle Transition]]", "[[Plane Strain Constraint]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT2 - Fatigue Lifing Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Structural Performance 2025.pdf (slides 1-20)", "02 - Sources/Materials Lectures/mini lecture videos/ML0a Structural performance intro and ductile_brittle recap_default_60214d95.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML0b Measuring toughness recap_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML1a Fracture mechanics concepts_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML1b Loading modes_default.txt"]
---

# SESA2028 M1 - Fracture, Toughness and Fracture Mechanics

> [!abstract] Summary
> Toughness is a material's resistance to fracture when a notch or defect is present. A Charpy test ranks materials by the energy a notched bar absorbs, but that energy cannot be turned into a safe load. Fracture mechanics can: the stress intensity factor $K=Q\sigma\sqrt{\pi a}$ describes the whole elastic crack-tip field with one number, the Griffith energy balance shows that its critical value $K_c=\sqrt{EG_c}$ is a material property, and fast fracture occurs when $K$ reaches the plane-strain fracture toughness $K_{Ic}$. Rearranged, that gives the critical crack size that ends every Paris-law calculation in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]].

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks whether a crack will cause fast fracture, what the critical defect size is, why a part failed in a ductile or brittle way, or why thick sections and low temperatures are dangerous.
> - **Assumptions:** linear elastic fracture mechanics, with the plastic zone at most about 1/50 of the crack length, the uncracked ligament and the thickness; mode I loading; geometry factor $Q$ given (usually 1.2 in this module's papers).
> - **Method:** 1. Take the peak tensile stress the part can see, $\sigma_{max}$ (an accident load if one is specified). 2. Use the lowest credible $K_{Ic}$. 3. $a_c=\frac1\pi\left(K_{Ic}/Q\sigma_{max}\right)^2$, in metres. 4. Compare $a_c$ with the defect sizes inspection can find. 5. Comment on temperature, loading rate, thickness and microstructure.
> - **Common mistakes:** putting $a$ in millimetres inside $\sqrt{\pi a}$; using the stress range instead of the peak stress for fast fracture.
> - **Example:** [[#A wing skin and a reactor vessel]]. **Exercise:** [[FEEG2005 Exam 2021-22 Solutions#(a) HSLA reactor pressure vessel|2021-22 MQ2(a)(i)]].

The materials half of the module opens with a block on structural performance, which runs through the first three weeks of semester 2 and is taught by Prof. Philippa Reed. Its aim is to design a component for a defined life: knowing how long it will last, when to inspect it and whether it is safe to keep using (ML0a, ll. 17–22). That needs every way a part can stop working, and those ways interact. A notch concentrates stress, cyclic loading grows a defect from it, a corrosion pit or a worn patch can supply the defect in the first place, and at high temperature creep and oxidation join in (ML0a, ll. 38–73). Fracture, fatigue, corrosion and wear are covered in this block; creep and oxidation come back at the end of the course in [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]].

In a loaded plate with a crack, lines of force cannot pass through the crack, so they crowd round its tip, and the material there carries far more than the nominal stress. In an elastic calculation the stress at a sharp tip is infinite; in a real metal the tip yields, spreads the load over a small plastic zone, and the question becomes whether the material inside that zone can survive. Whether it can depends on the microstructure in that small volume, on temperature and loading rate, and on how constrained the zone is by the material around it. Fracture mechanics wraps all of the loading side into one number, $K$, so that the material side can be measured once as a toughness and used for any geometry.

## 1. Ductile and brittle fracture

A smooth tensile bar of a ductile metal yields, reaches its ultimate tensile strength and then necks (ML0a, ll. 78–86). The neck is a very shallow notch, so the material at its centre sits in a triaxial stress state (ll. 94–98). Most engineering alloys contain hard second-phase particles, carbides in steel or silicon-rich particles in the aluminium alloy shown, which do not deform. As the matrix flows round them it pulls away and opens microvoids, "a bit like a ball bearing in plasticine" (ll. 99–108). The voids grow and join, so by the time the test reaches its maximum load the centre of the bar already holds an internal crack, and only an outer ring is still carrying the load (ll. 112–122). That ring is effectively thin sheet, so it fails by shear on planes at about 45° to the load, leaving the shear lips of the cup-and-cone fracture (ll. 122–126). Under the scanning electron microscope the flat centre is covered in dimples, each half a void with the particle that started it sitting in the bottom. The whole process involves a lot of plastic work and takes time: the crack advances slowly and you can watch it happen during the test (ll. 136–138, 178–180).

Brittle fracture is the opposite. The steel bars broken at low temperature in the Part 1 lab showed no neck and no change of section, and the fracture surface glinted when tilted in the light because it is made of small flat facets (ll. 139–147). A brittle crack takes whichever path through the microstructure is weaker. If the grain boundaries are weaker it runs along them, an **intergranular** fracture, and the surface shows the three-dimensional shapes of the grains; if not, it splits the grains along crystal planes, a **transgranular** or cleavage fracture (ll. 151–159, 172). Because the crack runs unstably, at close to the speed of sound in the material, its front wanders onto slightly different planes, and the steps between them grow as it runs. These steps are **river lines**: like tributaries they join in the direction the crack travelled, so following them back upstream leads to the initiation site (ll. 160–164, 174–175). Reading fracture surfaces like this is a learning outcome of the module, the subject of the first two materials tutorials and the basis of the fatigue-lab consultancy report (ll. 166–168).

| | Ductile | Brittle |
|---|---|---|
| Fracture surface | dimpled, dull and fibrous | flat and faceted, glints in light |
| Plastic deformation | extensive, with necking | little or none |
| Crack propagation | slow, needs continued work | rapid, self-sustaining |
| Character of failure | gradual, gives warning | catastrophic |

The table is slide 5 of the structural-performance deck (ML0a, ll. 176–180).

## 2. Measuring toughness

The smooth tensile test gives stiffness ($E$), strength (the yield stress) and ductility (the elongation to failure; below about 5 % is conventionally called brittle) (ML0b, ll. 3–11). It says nothing about how the material behaves at a notch. **Toughness** is defined as the resistance of a material to fracture in the presence of a notch or defect, which might be a crack, a corrosion pit, a handling mark or simply a change of cross-section (ll. 10–15, 24–25). So a toughness test must use a notched specimen.

The **Charpy impact test** breaks a notched bar in three-point bending with a swinging pendulum (ll. 16–23). The hammer is released from a height, converts its potential energy to kinetic energy, breaks the specimen at the bottom of its swing and rises on the other side. With nothing in the way it would rise to its starting height. Whatever energy the specimen absorbed is missing from the follow-through, and a dial records it as the impact energy (ll. 29–42). If the pendulum of mass $m$ falls from height $h_0$ and rises to $h_1$,

$$
\text{IE}=mg\left(h_0-h_1\right).
$$

A ductile failure absorbs a lot of energy and gives a high impact energy; a brittle one gives a low value (l. 42).

The test is quick and cheap, so it is good for ranking materials and for quality control, checking that each batch of steel or aluminium has a consistent toughness (ll. 43–45). It cannot be used in design. An energy in joules for one standard bar does not say what load a cracked oil-rig node can carry, because it has no link to stress or defect size (ll. 45–50). That link is what $K$ supplies in Section 5.

## 3. The ductile-brittle transition

The Part 1 Charpy lab showed steel to be the toughest material at room temperature and brittle enough to shatter after a dip in liquid nitrogen, while the aluminium alloy barely changed (ML0b, ll. 51–58). Plotting impact energy against temperature for a steel gives an **upper shelf** of high, ductile energies, a **lower shelf** of brittle ones and a fairly sharp step between them, the ductile-brittle transition. Adding carbon strengthens the steel, but it lowers the upper-shelf energy and raises the transition temperature, so the steel is brittle at higher temperatures (ll. 59–69). Higher strength here means lower toughness.

![[materials_dbt_yield_vs_cleavage.png|900]]

The transition is a competition between two ways of failing (ll. 69–108). Plastic flow needs the yield stress $\sigma_y$; brittle cleavage needs the fracture stress $\sigma_f$; whichever is reached first wins. The fracture stress hardly depends on temperature. How the yield stress depends on temperature is set by the crystal structure:

- Face-centred cubic metals (aluminium alloys, austenitic stainless steels, copper, nickel) have many close-packed slip planes, so dislocations move easily without thermal activation. The yield stress is low and roughly constant, it is always reached before $\sigma_f$, and the material is ductile at every temperature (ll. 73–83).
- Body-centred cubic metals (ferritic steels) have close-packed directions but no close-packed planes, so slip needs larger atomic movements and is thermally activated. As the temperature falls the yield stress rises steeply. Above the crossing with $\sigma_f$ the metal yields first and is ductile; below it, cleavage comes first and it is brittle (ll. 84–101).
- Hexagonal close-packed metals (magnesium, titanium, zinc) do have a close-packed basal plane, but not enough slip systems on it, so non-basal slip, which is thermally activated, must also operate. They can show a transition too (ll. 105–108).

The figure's right panel shows the consequence on a Charpy plot. The same competition explains why carbon raises the transition: it raises $\sigma_y$ at every temperature, which moves the crossing with $\sigma_f$ to a higher temperature.

## 4. Stress concentrations and the crack tip

Few components are plain cylinders or plates; they have holes, notches and changes of section, and the force lines have to bend round each of them (ML1a, ll. 18–26). For a circular hole in a wide plate the peak stress at the edge of the hole is three times the nominal stress, and it falls back to the nominal value a short distance away. The **stress concentration factor** $K_t$ is just that ratio of peak to nominal stress at one point (ll. 24–31). Deeper and sharper notches raise it: the lecture describes this through the ratio of notch depth $b$ to root radius $r$ (ll. 31–36). The elastic result for an elliptical notch (Inglis, covered in Part 1 and in [[Stress Concentration Factor and Factor of Safety]]) is usually written with semi-axis $a$ along the cross-section and $c$ along the load:

$$
K_t=1+\frac{2a}{c}.
$$

The root radius of an ellipse at the end of its long axis is

$$
\rho=\frac{c^2}{a},
$$

so

$$
\frac{a}{c}=\sqrt{\frac{a^2}{c^2}}=\sqrt{\frac{a}{\rho}},
$$

and

$$
K_t=1+2\sqrt{\frac{a}{\rho}} .
$$

In the lecture's notation that is $1+2\sqrt{b/r}$. A circle has $b=r$ and gives $K_t=3$; a notch nine times deeper than its root radius gives $K_t=7$. A crack has $r\to0$, so $K_t\to\infty$ and stops being useful. The tearing paper of ll. 37–41 makes the same point: a sharp crease tears easily, a curve round a mug does not.

Two conventions from Part 1 are used throughout (ll. 47–55). An internal crack in a plate is $2a$ long; a surface crack, which is half of that problem by symmetry, has depth $a$.

All of this is elastic. Ahead of a sharp crack the opening stress $\sigma_{11}$ (perpendicular to the crack plane) falls off as $1/\sqrt r$ with distance $r$ from the tip (ll. 72–80), and close enough to the tip it exceeds the yield stress. The material there cannot carry that stress; it yields instead, and the load it should have carried is redistributed over a wider region at roughly the yield stress, rejoining the elastic curve a little further out (ll. 80–91). The yielded region is the **plastic zone**, or process zone, and it is where the ductile or brittle mechanisms of Section 1 actually happen. Because it is small, failure is controlled by the weakest microstructural feature inside it, a brittle particle, an embrittled grain boundary or a large grain (ll. 92–99).

![[materials_crack_tip_plastic_zone.png|800]]

## 5. Two routes to a fracture criterion

### Griffith's energy balance

Griffith ignored the complicated tip stresses and asked a global question: if a pre-existing crack grows, is there enough energy to pay for it (ML1a, ll. 100–123)? Growth costs energy because two new surfaces are created, at $\gamma_e$ per unit area of surface for an ideally brittle solid such as the mica and glass he studied. In a metal the plastic zone must also be dragged along with the tip, which costs plastic work $\gamma_p$ per unit area, and $\gamma_p\gg\gamma_e$ (ll. 108–118). The energy comes from the elastic strain energy stored around the crack, which is released as the crack opens. The lecture gave only the result, since the derivation was done in Part 1 (ll. 123–127); here it is in full.

Take a large plate of unit thickness under remote stress $\sigma$, containing a through crack of length $2a$, in plane stress. Griffith's result, from the Inglis stress field, is that the crack lowers the stored strain energy by

$$
U_e=\frac{\pi a^2\sigma^2}{E}.
$$

The two crack faces each have area $2a\times1$, so the surface energy is

$$
U_s=2\times2a\times\gamma=4a\gamma,
$$

with $\gamma=\gamma_e+\gamma_p$. The crack can grow when the energy released by a small extension at least pays for the new surface:

$$
\frac{dU_e}{da}\ge\frac{dU_s}{da}.
$$

Differentiate each side:

$$
\frac{2\pi a\sigma^2}{E}\ge4\gamma .
$$

Fracture starts when the two are equal, at $\sigma=\sigma_f$:

$$
\sigma_f^2=\frac{2E\gamma}{\pi a},
$$

$$
\sigma_f=\sqrt{\frac{2E\gamma}{\pi a}} .
$$

The energy released per unit increase of crack area is the **strain energy release rate** $G$. Both tips advance, so the area grows by $d(2a)$ and

$$
G=\frac{dU_e}{d(2a)}=\frac{\pi a\sigma^2}{E}.
$$

Its critical value, the material's resistance, is $G_c=2\gamma=2(\gamma_e+\gamma_p)$, and the fracture condition $G=G_c$ gives the form on slide 11:

$$
\sigma_f=\sqrt{\frac{EG_c}{\pi a}} .
$$

Two things follow. The fracture stress falls as $1/\sqrt a$, so doubling the crack length lowers the fracture stress by about 30 %. And because $\gamma_p$ is so much larger than $\gamma_e$, a metal with a working plastic zone is far tougher than its bond strength alone would suggest (ll. 112–118).

### The stress intensity factor

Linear elastic theory gives the stress field near any sharp crack tip in polar coordinates $(r,\theta)$ centred on the tip (ll. 132–141):

$$
\sigma_{ij}=\frac{K}{\sqrt{2\pi r}}f_{ij}(\theta)+\text{higher-order terms}.
$$

The angular functions $f_{ij}$ are the same for every crack loaded the same way, so the single factor $K$, the **stress intensity factor**, sets the size of the whole near-tip field. Where $K_t$ described one point, $K$ describes the stress distribution over a distance, which is what the material in the process zone responds to (ll. 132–136).

Rearranging Griffith's result links the two views (ll. 142–156). Multiply both sides of $\sigma_f=\sqrt{2E\gamma/\pi a}$ by $\sqrt{\pi a}$:

$$
\sigma_f\sqrt{\pi a}=\sqrt{2E\gamma}=\sqrt{EG_c}.
$$

The left side is $K$ evaluated at the fracture stress; the right side contains only $E$ and $\gamma$, which are properties of the material. So the critical stress intensity factor

$$
K_c=\sqrt{EG_c}
$$

is a material constant, the **fracture toughness**. For a general geometry a dimensionless shape factor $Q$ (some texts write $Y$) allows for the shape and size of the crack and component, with $Q=1$ for the centre crack in a large plate derived above:

$$
K=Q\sigma\sqrt{\pi a},
\qquad
K_c=Q\sigma_f\sqrt{\pi a}.
$$

The lecture lists three reasons $K$ is useful: it describes the local crack-tip stresses and strains, it links to the energy balance, and it can be calculated from the specimen's external dimensions and the external loads alone (ll. 157–160).

Cracks can be loaded in three ways (ML1b, ll. 1–7): mode I opens the faces, mode II slides them over each other in their plane, and mode III tears them, an anti-plane shear. $K_c$ measured in mode I is written $K_{Ic}$. Most brittle failures follow the path of maximum opening stress, so mode I is the worst case and $K_{Ic}$ is the design value (ML1a, ll. 162–166).

### Critical crack size

Setting $K=K_{Ic}$ at the peak service stress and solving for $a$:

$$
Q\sigma_{max}\sqrt{\pi a_c}=K_{Ic},
$$

$$
\sqrt{\pi a_c}=\frac{K_{Ic}}{Q\sigma_{max}},
$$

$$
a_c=\frac1\pi\left(\frac{K_{Ic}}{Q\sigma_{max}}\right)^2 .
$$

This is the structural-design answer the Charpy test could not give: for a known toughness and stress, the largest defect that can be tolerated, or for a known defect, the largest stress (ll. 152–155).

## 6. When K is valid, and why thickness matters

$K$ comes from linear elasticity, but almost every structural metal has a plastic zone (ML1a, ll. 168–174). Outside the plastic zone and a transition region around it, the stress field is still the $K$ field. So as long as those regions are small, the $K$-dominated field is still what loads the process zone and $K$ remains a good descriptor of failure there (ll. 174–181). The rule of thumb given is that linear elastic fracture mechanics is valid when the plastic zone is about 1/50 of the crack length, of the uncracked ligament ahead of the crack, and of the specimen thickness (ll. 181–186, slide 13).

Testing one material at different thicknesses shows why the thickness appears (ll. 186–198). The measured critical value $K_{crit}$ is high in thin specimens and falls as the thickness grows, until it levels off. Only the plateau is a true material constant, and it is the lowest value: this is $K_{Ic}$, measured under **plane strain**. Thin sheet looks tougher only because of its geometry.

![[materials_thickness_effect_kcrit.png|900]]

The difference is constraint (ll. 199–216). In thin sheet nothing can carry stress through the thickness, so $\sigma_{33}\approx0$: a plane-stress state. The largest resolved shear stress is then on planes at 45° to the tensile load, yielding is easy, and the fracture is slanted, like the shear lips of the cup-and-cone. In the middle of a thick section the material is pulled in the loading direction and wants to contract sideways by the Poisson effect, but the surrounding material does not contract with it, so the through-thickness strain is prevented. With Hooke's law for the through-thickness direction,

$$
\varepsilon_{33}=\frac{1}{E}\left[\sigma_{33}-\nu\left(\sigma_{11}+\sigma_{22}\right)\right],
$$

setting $\varepsilon_{33}=0$ gives

$$
\sigma_{33}=\nu\left(\sigma_{11}+\sigma_{22}\right),
$$

a tensile reaction stress. The stress state is now triaxial: all three principal stresses are tensile, the differences between them (which drive shear and yield) are smaller, so the plastic zone is suppressed while the opening stress stays high. This is the most severe condition, which is why the plane-strain value is the one to design with (ll. 213–216). The fracture surface of a thick part records it: a flat, square centre with small shear lips at the free surfaces where plane stress returns. See [[Plane Strain Constraint]].

## 7. Loading modes and torsion failures

The general stress state is the stress tensor $\sigma_{ij}$, with three normal components ($\sigma_{11}$, $\sigma_{22}$, $\sigma_{33}$) and shears on each face of a cube (ML1b, ll. 7–23). Two rules let you read a fracture surface back to the loading (ll. 23–29). Brittle cracks follow the path of maximum opening stress. Yield needs shear, because dislocations move under shear stress. Real parts mix loads: a ruler bent one way has tension on one face and compression on the other, reversed bending swaps them every cycle, and a shaft that is slightly off-axis sees rotating bending and torsion together (ll. 29–38).

Torsion shows the two rules most clearly. On the surface of a shaft under torque the material is in pure shear $\tau$ on planes along and across the axis. Rotating the element by an angle $\theta$ from the axis, the normal stress on the rotated plane is

$$
\sigma_n(\theta)=\tau\sin2\theta,
$$

which is largest, $\sigma_n=\tau$, at $\theta=45^\circ$ and most negative, $-\tau$, at $\theta=-45^\circ$; the shear on those planes is

$$
\tau_n(\theta)=\tau\cos2\theta=0 .
$$

So the maximum shear acts along and across the axis, and the maximum opening stress acts on planes at 45° to it. The research demonstration in ML1b (ll. 39–47) shows both with a rubber tube: a slit cut along the tube shears when the tube is twisted, while a slit cut at 45° opens "like a little mouth".

![[materials_torsion_failure_planes.png|900]]

A ductile shaft therefore fails on a flat plane perpendicular to its axis, after visible twisting and sometimes a little necking, because that is a plane of maximum shear (ll. 48–56). A brittle shaft, like a piece of chalk or a pen twisted until it snaps, fails on a 45° helix, the surface of maximum opening stress, with very little deformation (ll. 50–58). These patterns come back in the fatigue fracture surfaces of [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]].

## 8. What controls toughness

Materials are often compared on two properties at once. An Ashby map of fracture toughness against density, on log–log axes, puts engineering alloys at high toughness and high density, composites at similar toughness but much lower density, and polymers, ceramics, woods and foams lower down; this kind of map is why composites matter for lightweighting ([[SESA2028 M4 - Polymer Matrix Composites|M4]]), and CES EduPack, met in Part 1, draws them (ML1b, ll. 59–73).

The factors that control toughness all come back to the competition between ductile and brittle failure (ll. 74–105). Toughness can fall as the temperature falls, in BCC and HCP metals, because yield becomes harder (Section 3). Ductile materials are generally much tougher, because yielding at the tip redistributes the stress and the moving plastic zone absorbs work. High-strength materials generally have low toughness, because a high yield stress means less redistribution at the tip; ceramics are the extreme case. Toughness falls as the loading rate rises, because some plastic deformation processes need time and at very high rates the material behaves as if it were stronger and more brittle. And since the events that matter happen in the small process zone, microstructure is the key variable:

- against intergranular brittle failure, minimise brittle species segregated to the grain boundaries;
- against transgranular failure, remove defects and large brittle particles inside the grains;
- avoid large grains, which allow long slip-band pile-ups that can start cleavage as well as lowering the yield stress;
- in a ductile alloy, control the size and spacing of the second-phase particles, which sets when microvoids nucleate and join.

## Worked examples

All numbers recomputed in Python.

### A wing skin and a reactor vessel

2013-14 B1(ii): a lower-wing skin in a 7xxx aluminium alloy has $K_{Ic}=45$ MPa√m, a peak stress of 200 MPa and $Q=1.2$. Then

$$
a_c=\frac1\pi\left(\frac{45}{1.2\times200}\right)^2=\frac1\pi\left(0.1875\right)^2=0.01119\text{ m}=11.2\text{ mm}.
$$

The peak stress, not the stress range, belongs here: fast fracture happens at the top of the load cycle.

2021-22 MQ2(a)(i): a reactor pressure vessel in HSLA steel has $K_{Ic}=73\pm3$ MPa√m and must survive a loss-of-coolant accident that raises the stress to 550 MPa, with $Q=1.2$. The vessel must survive the accident at any time, so use the accident stress and the lowest toughness:

$$
a_c=\frac1\pi\left(\frac{70}{1.2\times550}\right)^2=3.58\text{ mm},
$$

against 3.89 mm with the nominal 73 MPa√m. The full lifing calculation that follows is in [[FEEG2005 Exam 2021-22 Solutions#(a) HSLA reactor pressure vessel|the 2021-22 solutions]].

### Griffith in glass, and why metals are tough

These numbers are illustrative, not lecturer-set. For a glass with $E=70$ GPa and $\gamma_e=1$ J/m², a surface flaw of $a=1$ μm gives

$$
\sigma_f=\sqrt{\frac{2\times70\times10^9\times1}{\pi\times10^{-6}}}=211\text{ MPa},
$$

and a 1 mm scratch lowers this to 6.7 MPa: the $1/\sqrt a$ law at work.

Going the other way, $G_c=K_{Ic}^2/E$. A steel with $K_{Ic}=50$ MPa√m and $E=210$ GPa has

$$
G_c=\frac{\left(50\times10^6\right)^2}{210\times10^9}=1.19\times10^4\text{ J/m}^2,
$$

about ten thousand times the 1–2 J/m² that surface energy alone could supply. Almost all of it is $\gamma_p$, the plastic work of the moving process zone. Alumina, with $K_{Ic}\approx4$ MPa√m and $E\approx380$ GPa, has $G_c\approx42$ J/m².

> [!check] Units
> With $\sigma$ in MPa and $a$ in metres, $K$ comes out in MPa√m. The wing example with $a$ in millimetres would give $K$ larger by $\sqrt{1000}\approx31.6$, so a critical crack size that looks a thousand times too large is the usual sign of this slip.

## Transcript slips

> [!warning] Mini-lectures ML0a–ML1b
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML0a, l. 2 | "FIGE 205 … FIGE 1002" | FEEG2005 (the mechanical and maritime twin of this module) and FEEG1002 |
> | ML0a, l. 118 | "stress strain 10-cell test" | tensile test |
> | ML0a, l. 134; slide 3(d) | remaining ligaments "fail under the maximum tensile stress" | they fail in shear on 45° planes, as ll. 123–124 say; that is what forms the shear lips |
> | ML0b, ll. 19, 22, 26, 54 | "sharpie" | Charpy |
> | ML1a, l. 15 | "consistency failure report" | consultancy failure report |
> | ML1a, l. 66 | "creek processes" | creep |
> | ML1a, ll. 98–99 | "mic structure" | microstructure |
> | ML1a, l. 138 | "k to the one over k divided by square root of 2 pi r" | $K/\sqrt{2\pi r}$ |
> | ML1a, ll. 195, 197 | "plain strain" | plane strain |
> | ML1a, l. 209 | "cup comb failure" | cup-and-cone |
> | ML1b, l. 84 | high strength and high toughness are incompatible "by definition" | only generally; slide 20 says "generally", and some alloys (Ti, maraging steels) manage both |
> | ML1b, ll. 16–17 | "sigma 3 1 … sigma 3 2 sorry" | the lecturer corrects herself: the component shown is $\sigma_{32}$ |
> | ML1b, l. 36 | "if it was a tall off axis" | if it was a little off axis |
> | ML1b, l. 105 | "microfiroid coalescence" | microvoid coalescence |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Next: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]], where $a_c$ is the upper limit of every Paris-law integral
- Concepts: [[Stress Intensity Factor]] · [[Griffith Energy Balance]] · [[Fracture Toughness and LEFM Validity]] · [[Plane Strain Constraint]] · [[Ductile-Brittle Transition]]
- Elsewhere: [[Stress Concentration Factor and Factor of Safety]] · [[Stress Singularities]] · [[Plane Stress and Plane Strain]] · [[Von Mises and Tresca Yield Criteria]] · [[Strain Energy]]
- Year 1: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[FEEG1002 B6 - Yield Criteria]]

## Sources

- Structural Performance 2025 slides 1–20
- Mini-lecture transcripts ML0a (structural performance intro and ductile/brittle recap), ML0b (measuring toughness), ML1a (fracture mechanics concepts), ML1b (loading modes)
- Past-paper data from [[FEEG2005 Exam 2013-14 Solutions]] and [[FEEG2005 Exam 2021-22 Solutions]]; all numbers recomputed in Python

## Self-study tasks

No problems were set in these mini-lectures. ML0a (ll. 166–168) points ahead to the fracture-surface work in materials tutorials 1 and 2 and the fatigue-lab report; ML0b (ll. 109–111) asks you to re-watch the Part 1 lectures if the recap feels shaky.

### Core

- [ ] Explain ductile and brittle fracture from their micromechanisms and fracture surfaces (ML0a, ll. 75–180). → [[#1. Ductile and brittle fracture]]
- [ ] Explain the ductile-brittle transition from the competition between yield and cleavage, for FCC, BCC and HCP (ML0b, ll. 69–112). → [[#3. The ductile-brittle transition]]
- [ ] Derive the Griffith fracture stress and show that $K_c=\sqrt{EG_c}$ (ML1a, ll. 100–156; the derivation was left to Part 1). → [[#Griffith's energy balance]]
- [ ] Critical crack size for 2021-22 MQ2(a)(i) (suggested, not lecturer-set). → [[#A wing skin and a reactor vessel]]

### Further practice

- [ ] Explain why $K_{crit}$ depends on thickness and derive $\sigma_{33}=\nu(\sigma_{11}+\sigma_{22})$ (ML1a, ll. 186–216). → [[#6. When K is valid, and why thickness matters]]
- [ ] Sketch the torsion fracture of a ductile and a brittle shaft and justify the planes (ML1b, ll. 39–58; suggested, not lecturer-set). → [[#7. Loading modes and torsion failures]]
