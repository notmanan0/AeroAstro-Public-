---
title: "SESA2028 M4 - Polymer Matrix Composites"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 4
tags: [sesa2028, materials, composites, lightweighting, rule-of-mixtures, manufacturing]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
next_topics: ["[[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]"]
key_concepts: ["[[Specific Stiffness and Strength]]", "[[Rule of Mixtures]]", "[[Critical Fibre Length]]", "[[Composite Manufacturing Routes]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Lightweighting 2025.pdf (lectures 5-6)", "mini lectures ML5a, ML5b, ML5c, ML6a, ML6b, ML10b"]
---

# SESA2028 M4 - Polymer Matrix Composites

> [!abstract] Summary
> Lightweighting means maximising **structural efficiency**: getting the stiffness or strength you need for the least mass, through geometry *and* material choice. Composites win on **specific** properties ($E/\rho$, $\sigma/\rho$), but only along the fibres. The **rule of mixtures** gives the longitudinal (isostrain) and transverse (isostress) stiffness, and the lecturer calls it an "EXAM TOP TIP". The rest of the topic is about why composites are not used everywhere: manufacturing cost and quality, anisotropy, and damage that is not a single crack, so it cannot be lifed with $K$ and Paris.

## 1. Why lightweight, and with what?

**Transport** is the theme: aircraft, cars, boats. Structural efficiency comes from geometry (sections, sandwich panels) *and* material.

- **Marine**: composites cannot corrode like metals (though they absorb moisture). A composite hull is non-magnetic and hard to detect by radar or magnetic mine (the Vosper mine-hunter). Racing yachts and dinghies too (WUMTIA at Southampton, America's Cup).
- **Automotive**: 1980s predictions of all-composite cars never came true. Markets, aesthetics (SUVs) and economics matter, not just engineering. HSLA and advanced high-strength steels stayed competitive because they are strong in thin sections and cheap at huge scale. The Reliant Robin had a composite body; the Aston Martin DB9 carbon bonnet is marketing (non-structural).
- **Aerospace**: A380 CFRP in the outer wing, nacelle cowlings, tail and stabilisers, tail cone, central torsion box, radome and fairings. The 787 has all-composite wings. Hybrid metal-composite joints are a key challenge.

### Specific properties

$$
\text{specific stiffness}=\frac E\rho,\qquad \text{specific strength}=\frac{\sigma_{UTS}}\rho.
$$

The best material depends on the **loading mode** (Ashby performance indices, derived by minimising mass at fixed length and required stiffness or strength):

| Component | Maximise (stiffness-limited) | Maximise (strength-limited) |
|---|---|---|
| Tie in tension | $E/\rho$ | $\sigma/\rho$ |
| Strut in buckling / beam in bending | $E^{1/2}/\rho$ | $\sigma^{2/3}/\rho$ |
| Plate or panel in bending or buckling | $E^{1/3}/\rho$ | $\sigma^{1/2}/\rho$ |

![[Figures/materials_specific_property_map.png]]

> [!example] Table QB2 (MT3 Q5 / 2014-15 B2)
> | | $\sigma/\rho$ | $E/\rho$ | $E^{1/2}/\rho$ (strut) |
> |---|---:|---:|---:|
> | CFRP | **882** | **129** | **8.72** |
> | GFRP | 450 | 20.5 | 3.05 |
> | Steel | 128 | 26.5 | 1.84 |
> | Al alloy | 196 | 25.4 | 3.01 |
> | Ti alloy | 244 | 26.7 | 2.43 |
> CFRP wins in tension *and* as a buckling strut. The catch is that its **compressive** strength (fibre microbuckling, delamination) is much lower than its tensile strength. For compressive loading dominated by strength rather than buckling, choose Ti or Al, or accept a larger CFRP section. Note that steel, Al and Ti have almost identical $E/\rho$: metals only differ in lightweighting through strength, toughness and temperature capability.

See [[Specific Stiffness and Strength]].

## 2. What a composite is

A **composite** is a system of two or more constituents that differ in **form and chemistry**, are essentially **insoluble** in each other, and are physically combined. A precipitation-hardened alloy is *not* a composite, because its precipitates formed from solid solution.

- **Reinforcement**: the expensive, high-quality, low-defect element.
- **Matrix**: holds the reinforcement.

| Reinforcement form | Properties | Notes |
|---|---|---|
| Continuous aligned fibre | best, highly directional | lay-up controls the directions |
| Discontinuous (chopped) fibre | intermediate | cheap and mouldable; little control of alignment |
| Particulate | modest gain, isotropic | cheapest |

### Fibres

| Fibre | Since | Character |
|---|---|---|
| Glass | 1920s | drawn or spun from melt; cheap; moderate $E$ |
| Carbon | ~1970 | largest-growing tonnage (A380, 787); properties tunable by processing |
| Aramid (Kevlar) | ~1970 | "ductile" fibre that necks; body armour; poor in compression |
| Boron | | CVD onto a tungsten wire core |
| Natural (jute, hemp, flax) | | "green" composites; variability, quality and moisture problems |
| Whiskers | | nearly defect-free single crystals; highest properties but short |
| Metal wire | | strong but poor *specific* strength |

"Don't memorise the property tables": interrogate the data intelligently. What matters is the properties **of the composite**.

### The matrix does more than glue

It holds the shape, transfers load, protects the fibres, **sets the maximum service temperature**, controls fire behaviour and moisture absorption (absorbed water lowers $T_g$), controls how the part is made, affects mechanical properties, and adds cost.

| | Epoxy | Polyester |
|---|---|---|
| Cost | ~10× higher | cheap |
| Properties | better | inferior |
| Cure shrinkage | lower | higher |
| Moisture uptake | lower | higher |
| Typical use | aerospace (with carbon) | marine chopped-strand glass |

## 3. Anisotropy and the rule of mixtures

Unidirectional composites are extremely anisotropic. At 50 % $V_f$: glass/polyester 700 MPa longitudinal vs 20 MPa transverse; HM carbon/epoxy 1000 vs 35; Kevlar/epoxy 1200 vs 20. Steel is 300-1000 MPa but about 3× denser, so the composite's *specific* longitudinal strength is far higher.

### Longitudinal: isostrain (Voigt)

Fibres and matrix stretch together, $\varepsilon_f=\varepsilon_m=\varepsilon_c$, and the loads add:

$$
\boxed{E_L=V_fE_f+V_mE_m},\qquad \sigma_L\approx V_f\sigma_f+V_m\sigma_m.
$$

Most of the load goes to the stiff fibres: $P_f/P_m=V_fE_f/(V_mE_m)$.

### Transverse: isostress (Reuss)

The load passes through fibres and matrix in series, $\sigma_f=\sigma_m=\sigma_c$, and the strains add:

$$
\boxed{\frac1{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m}}
$$

$E_T$ is dominated by the soft matrix, so the improvement is **very poor**.

![[Figures/materials_rule_of_mixtures.png]]

The rule of mixtures works for **density**, electrical properties and longitudinal stiffness. It does **not** work for **toughness**, which depends on interfaces, pull-out and delamination.

> [!example] Worked answers
> **2013-14 B2(v)**, 60 % glass ($E_f=72.5$ GPa) in resin ($E_m=4$ GPa):
> $$E_L=0.6(72.5)+0.4(4)=45.1\ \text{GPa},\qquad E_T=\left(\tfrac{0.6}{72.5}+\tfrac{0.4}{4}\right)^{-1}=9.24\ \text{GPa}.$$
> **2014-15 B2(iii)**, 55 % carbon (325 GPa) in epoxy (3.1 GPa): $E_L=180$ GPa, $E_T=6.81$ GPa, an anisotropy ratio of 26.
> **Less anisotropic:** use a cross-ply 0/90 or quasi-isotropic 0/±45/90 lay-up, woven fabric, or chopped-strand mat. This gives up peak $E_L$ for balanced in-plane properties.

### Designing to a requirement: required $V_f$

Solve the rule of mixtures for the fibre fraction that just meets each requirement, and take the **larger** of the stiffness and strength values:

$$
V_f=\frac{P_{req}-P_m}{P_f-P_m}.
$$

> [!example] 2015-16 B2(iv) dinghy keel ($E\ge63$ GPa, $\sigma\ge1.45$ GPa, epoxy 3.1 GPa / 0.07 GPa)
> | Fibre | $V_f$ for $E$ | $V_f$ for $\sigma$ | Governs |
> |---|---:|---:|---:|
> | Aramid (124, 3.5) | 0.495 | 0.402 | **0.50** |
> | Glass (72, 3.5) | 0.869 | 0.402 | **0.87**: impractical (>~0.65 is hard to make) |
> | Carbon (325, 3.8) | 0.186 | 0.370 | **0.37**: strength governs |
> Choose **carbon**: the lowest $V_f$, lightest and stiffest. Aramid is feasible but weak in compression, which matters for a keel in bending.

![[Figures/materials_required_fibre_fractions.png]]

See [[Rule of Mixtures]].

### Laminates and fabrics

- A **0/90** lay-up is good along both axes but **weak at 45°** (in-plane shear), so add ±45° plies.
- Lay-ups should be **symmetric** about the mid-plane. Otherwise uneven thermal contraction on cooling from cure causes warping and residual stress.
- **Woven fabrics** (including carbon/Kevlar hybrids) give directional properties by weave and are much easier to handle. 3D knitting and weaving robots exist.
- **Hybrids** (mixed fibres) follow the rule of mixtures with an extra fibre term: $E=V_{f1}E_{f1}+V_{f2}E_{f2}+V_mE_m$.

## 4. Discontinuous fibres and the critical length

![[Figures/materials_short_fibre_stress.png]]

When a fibre ends (or breaks), load has to be fed back into it by **interfacial shear** through the matrix (the **shear-lag** model). The fibre stress is zero at its ends and builds up over a **transfer (ineffective) length**.

- **Critical length $l_c$**: the shortest fibre that reaches its breaking stress $\sigma_f^*$ at mid-length. For interfacial shear strength $\tau$ and fibre diameter $d$, a force balance on half the fibre gives $l_c=\sigma_f^*d/(2\tau)$.
- At $l=l_c$ the stress profile is a triangle, so the **average stress is only 50 %** of the peak.
- For $l<l_c$ the fibre **can never be broken**: it pulls out instead.
- For $l\gtrsim15\,l_c$ the end effects are negligible, and the fibre behaves like a continuous one (rule of mixtures).
- But short fibres cannot be well aligned, so in practice the properties are lower.

See [[Critical Fibre Length]].

## 5. Manufacturing routes

The objective is **high quality and low defects at minimum cost**. Composites are unusual because **you make the material and the component shape at the same time**. The UK south-coast craft industry is "a strength and a weakness": flexible, but skill-dependent and hard to automate.

| Route | Wet/dry | Mould | Quality | Cost and volume | Typical part |
|---|---|---|---|---|---|
| **Hand lay-up** | wet | open, 1-part | poor: high voids, resin-rich areas, skill dependent | cheapest tooling; slow | boat hulls, one-offs |
| **Pultrusion** | wet | heated die | good, automated, fast | constant cross-section only | rods, tubes, I-beams |
| **Resin transfer moulding (RTM)** | dry preform + injected resin | closed, 2-part | high; good infiltration | high mould cost, needs volume | dinghy hull, fairly large parts |
| **Vacuum bag / autoclave** | dry (prepreg) | open, 1-part + bag | **best: voids < 1 %** | expensive (prepreg stored frozen; autoclave) | aerospace primary structure |
| **Compression moulding** | dry | heated closed, 2-part | good consolidation, low voids | dearer tooling than a vacuum bag | helicopter and wind-turbine blades |
| **Filament winding** | wet or dry | rotating mandrel | high $V_f$, low voids, fast | limited to bodies of revolution; mandrel removal; wind direction fixed within a pass | pressure vessels (CNG, $\mathrm H_2$, scuba) over an Al liner; tubes |

Hand lay-up sequence: gel coat (surface finish, hides stray fibres), then dry fabric, then pour and roll resin (the roller squeezes out trapped air), then scrape off the excess. Vacuum bag stack: prepreg, **peel ply** (soaks up excess resin), breather, and sealed bagging film. Vacuum and autoclave pressure squeeze out gas and resin.

Quality problems common to all routes: **voids**, **resin-rich regions** (locally low $V_f$), and the **fibre-matrix interface** (sizing chemistry is proprietary). Overall the process is slow and expensive. See [[Composite Manufacturing Routes]].

> [!example] 2013-14 B2(iv): why is vacuum impregnation better than hand lay-up?
> Vacuum pressure (plus autoclave pressure and heat) removes trapped air and excess resin. That gives voids below 1 %, higher and more uniform $V_f$, better fibre wet-out and consistent properties, all independent of operator skill. It is restricted by the cost of prepreg, frozen storage, autoclave capital and the size of the autoclave (the A380 rear bulkhead was too big, so resin film infusion was used), and by slow cycle times.

## 6. Choosing composites, and why aerospace is cautious

**The hockey stick example** (ML6b): wood (a natural cellulose + lignin composite; CNC milled; recyclable), cast Al (then heat treated), or a composite (strips rolled in a mould and heat-cured). The choice depends on performance, cost, volume and end of life.

**Cost = raw materials + processing (equipment, time, skill) + end-of-life disposal or recycling** (life-cycle cost).

**Barriers in aerospace:**

- The industry is conservative, safety-critical and highly regulated.
- **Lack of trust in damage tolerance.** Composite damage is delamination, transverse ply cracks, fibre breakage and pull-out, not a single sharp crack. So **$K$ and Paris lifing cannot be applied**. Designers respond with big safety factors, over-engineered thick parts, and a composite's full performance envelope is not used.
- Coupon tests do not represent large structures. The **testing pyramid** runs coupon, element (stiffener), stiffened panel, sub-component, whole wing. You cannot jump from coupon to wing, and each level costs more.
- **Political** decisions about what an aircraft is made of and where (Airbus wings are made in the UK).
- Manufacturing reliability and consistency; cost.

**Barely visible impact damage (BVID).** The surface looks fine but there is internal ply cracking and delamination. It controls compression-after-impact strength, and also matters for lightning and bird strikes. It is found by **X-ray CT** (the µ-VIS centre at Southampton): rotating radiographs reconstructed into 3D, with contrast from density and chemistry, "4D" in-situ loading, and synchrotron resolution down to tens of nm.

**CT case studies (ML10b):**

- A notched coupon: ply cracks at about 30 % UTS, then 0° splits, then delamination, reaching up to 110 % UTS. Fibre breaks cascade (Weibull fibre-strength statistics).
- **Composite overwrapped pressure vessels** (COPV: Al liner, CFRP hoop and helical wraps, cosmetic GFRP outer wrap). BVID leaves a **dent in the liner**, which flexes with every pressure cycle, causing local liner fatigue.
- Wind-turbine GFRP: highly defective with large voids. Cracks start at surface voids and free edges, and a 45° ply crack turns into a delamination.

**New manufacturing:** the A380 rear pressure bulkhead is a single CFRP piece. It is too big for an autoclave and prepreg is too expensive, so it was made by **resin film infusion (RFI)**.

**Sandwich panels.** Laminates have poor through-thickness properties. Separating two thin skins with a light **core** (Al or Nomex honeycomb, foam) gives large bending stiffness for little mass. The core resists compression and shear, and its behaviour is set by cell density and geometry. The idea is biomimetic (shells, insect wings).

## 7. Exam checklist

- [ ] Use the rule of mixtures for $E_L$ and the inverse rule for $E_T$. Always say "isostrain" and "isostress".
- [ ] For required $V_f$, check **both** stiffness and strength, take the larger, and flag $V_f>0.6$-0.7 as impractical.
- [ ] Quote specific properties with units; choose the right index ($E/\rho$ vs $E^{1/2}/\rho$).
- [ ] For "make it less anisotropic": 0/90, ±45 or quasi-isotropic lay-ups, woven fabric, chopped mat.
- [ ] For "cheaper": glass or glass/carbon hybrid, a cheaper matrix (polyester), a cheaper route (RTM, filament winding, pultrusion instead of autoclave), less carbon where it is not needed.
- [ ] Compare composites with metals on damage tolerance, compressive strength, temperature limit (matrix), manufacturing and joining.

## Related

- [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]].
- [[SESA2028 Materials Tutorial MT3 - Lightweighting Solutions]].
- [[Bypass Ratio and Fan Pressure Ratio]] (SESA2023): why fan blades got bigger, and Ti vs CFRP fan blades (2020-21 MQ1).
- [[Euler Buckling]]: where the $E^{1/2}/\rho$ strut index comes from.
