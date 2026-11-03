---
title: "SESA2023 W11 - Solid Propellants and Rocket Nozzle Design"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 5: Rockets"
order: 11
tags:
  - sesa2023
  - rockets
  - solid-propellant
  - burning-rate
  - nozzle-design
aliases: ["Rockets II", "Solid rocket motors", "SESA2023 Week 11"]
date: 2026-09-24
status: lectured
coverage: "Week 11 (solids introduced 1 May; 8 May lecture on solids and real nozzles, no recording) and the 12 May review"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
next_topics: []
key_concepts: ["[[Solid Propellant Burning Rate]]", "[[Rocket Nozzle Geometry]]", "[[Rocket Performance Parameters]]", "[[Converging-Diverging Nozzle Operating Regimes]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Week 11 - Rockets.pdf", "02 - Sources/Lectures/Week 11 - Rockets - Lecture Slides.pdf", "02 - Sources/Lectures/SESA2023 Lecture 31.txt", "02 - Sources/Lectures/SESA2023 Lecture 34.txt"]
---

# SESA2023 W11 - Solid Propellants and Rocket Nozzle Design

> [!abstract] Summary
> Solid rocket motors are simple, reliable and storable for 5–20 years, but they can't be stopped or relit. Their thrust follows the burning rate $r=aP_c^n$ (Saint-Robert's law), whose burning index $n$ controls stability ($0.2<n<0.8$ in practice, no stable operating point for $n\ge1$), and $r$ also rises with the propellant's initial temperature, cross-flow (erosive burning) and acceleration. In a real nozzle the convergent shape barely matters, the throat curvature sets the effective $A_t$, and the divergent section is either conical (12–18°, divergence factor $\lambda=(1+\cos\alpha)/2$) or a shorter, lower-loss bell; aerospikes and dual-bells adapt to altitude.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to explain solid-motor behaviour (thrust–time shape, stability, temperature sensitivity, erosive burning), compare propellant types, or describe and compare nozzle contours and losses. Mostly descriptive.
> - **Assumptions:** quasi-steady chamber (gas generated = gas discharged through a choked throat); $r=aP_c^n$ over the operating range; uniform grain temperature; conical exit with a spherical wavefront for $\lambda$.
> - **Method:** 1. Write the mass balance $\rho_pA_br=P_cA_t/C^*$. 2. Insert $r=aP_c^n$ and solve for $P_c$. 3. Use $P_c\propto(A_b/A_t)^{1/(1-n)}$ to discuss sensitivity and stability. 4. Thrust $F=C_FP_cA_t$, with $C_F$ reduced by $\lambda$ for a cone. 5. List the real-nozzle losses.
> - **Common mistakes:** saying a higher propellant temperature raises the total impulse (it mainly shortens the burn); forgetting that $n\ge1$ is unstable, not just "more sensitive".
> - **Practise:** [[#Worked example – chamber pressure and its sensitivity]] · [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles#Worked example – the Saturn V F-1 engine|W10 F-1 nozzle]]

> [!note] Scope
> Solid motors were introduced on 1 May (Lecture 30, ll. 33–182: surface combustion, grain shapes, the Shuttle and Ares boosters), which is recorded; see §1. Lecture 31 (5 May, ll. 400–407) then says the Friday lecture would "study a little bit more the solid propellant and also the nozzle… remove a couple of assumptions about the nozzle, and with that we will complete the course". That 8 May lecture has no recording, so the propellant chemistry, burning-rate law and nozzle-contour material here follow the Week 11 notes and slides.

A solid motor is its own fuel tank and combustion chamber. The grain burns from its exposed surface inwards, and the gas it releases fills the case and leaves through the nozzle. The chamber pressure finds a balance: more pressure means faster burning and more gas made, but also more gas pushed out through the choked throat, and the pressure settles where generation equals discharge. That balance is stable only if burning responds gently to pressure. If the burning rate rose as fast as the discharge does ($n\ge1$), a small pressure rise would feed itself; with $n<1$ the discharge grows faster than the generation and disturbances die out.

A solid can't be throttled, so the thrust curve is set by the shape of the grain's burning surface: a star that burns out to a circle, a tube that grows, an end-burner that stays the same. A real nozzle also loses performance that the one-dimensional area-ratio model misses. The exit flow diverges, so some of its momentum points sideways and is wasted, and boundary layers, particles and chemistry cost more; nozzle shaping is about recovering that last few per cent.

---

## 1. Solid rocket motors

- **Components:** a case (cylindrical or spherical, thermally insulated), the propellant grain, an igniter (pyrotechnic charge) and the nozzle.
- **Uses:** from about 2 N to 11 MN. Large boosters (Space Shuttle, Ares, L30), upper stages, tactical missiles (air-to-air, surface-to-air, anti-tank) and gas generators to start turbopumps.
- **Pros:** few or no moving parts, low cost, very high reliability, minimal maintenance, ready for immediate use (important militarily).
- **Con:** no restart, no throttling once lit. "Once it's started, there's pretty much no way to stop it… unless you could cool it extremely quickly" (L30, ll. 72–77); for a crew, "there's no way for them to stop this once they've pressed go" (ll. 137–138).

### How a solid burns (L30, ll. 44–103)

The combustion chamber is the propellant store, as in a firework. Like a lump of coal in a fire, heat from the hot products conducts into the surface, which decomposes into gas that reacts just above it. The fuel and oxidiser are already premixed in the grain (for example aluminium powder with an oxygen-rich compound such as nitrocellulose in a binder), so there is no waiting for mixing and it burns fast.

The gas production is proportional to the burning surface area, and that area changes as the grain burns back. The nozzle stays choked, but a choked nozzle fixes only the *non-dimensional* flow: more gas raises the chamber pressure and so the mass flow and thrust (ll. 99–103).

Grain shapes ("think about this as the lettering in a stick of rock", l. 109):

| Grain (cross-section) | Burning area with time | Thrust profile |
|---|---|---|
| tube burning outwards | grows with the radius | progressive (rising); usually not wanted, since peak thrust is needed early to cut gravity losses |
| star | high at first; the points round off into a bigger circle | roughly neutral |
| "anchor" shape | high at first, then falling | regressive |
| two-step profiles | designed | e.g. the Space Shuttle boosters: a first thrust peak to cut gravity losses, a lower phase through the dense air, a second peak once drag matters less (ll. 135–142) |

The Ares I first-stage five-segment motor in the test film burned for about two minutes and then stopped quite suddenly; its nozzle can be seen gimballing for thrust-vector control (L30, ll. 143–182).

## 2. Propellants

The requirements conflict, so every grain is a compromise (Week 11 notes):

- high energy (high $T_c$ and $I_{sp}$) and a low product molar mass;
- high density;
- a low burning index for stable combustion;
- low sensitivity to temperature and to erosive burning;
- easy ignition;
- good mechanical properties, bonding and thermal-expansion match to the case;
- long storage life and safe manufacture;
- opacity to radiation; smokeless exhaust (stealth);
- low cost.

| Type | Make-up | Pros | Cons |
|---|---|---|---|
| Homogeneous / double-base (colloidal) | nitrocellulose (NC) dissolved in nitroglycerine (NG), plus additives (carbon black for opacity; AP or Al for performance; a third component gives *triple-base*) | cheap, smokeless, non-toxic exhaust, good mechanical properties, low $n$, good control of $r$ | low $I_{sp}$ (≈ 220 s at sea level), low density (1.6 g/cm³), hazardous; the energetically optimal NG/NC ≈ 8.6 cannot be used, and mechanical limits keep NG/NC ≤ 1 |
| Heterogeneous / composite | oxidiser crystals (AP, AN, KP, KN, NP) in a rubbery binder (HTPB, PBAN, asphalt), plus up to about 20 % metal powder (Al, B; Be is toxic) | safer, higher performance; the optimum is slightly fuel-rich, which also protects the nozzle | oxidiser loading ≤ 80–85 % for processability; the volume ratio is what matters, so dense oxidisers and light fuels are preferred; $r$ depends strongly on AP particle size |

## 3. Burning rate

The burning rate $r$ is the regression speed of the burning surface, normal to itself, in mm/s. It is measured in strand (Crawford) burners, ballistic evaluation motors or full-scale motors.

$$
\boxed{r = aP_c^{\,n}}\qquad\text{(Saint-Robert's, or Vieille's, law)}
$$

- The data lie on straight lines on a $\ln r$–$\ln P_c$ plot over wide ranges, sometimes piecewise (the "plateau" of double-base propellants).
- $a$ is the temperature coefficient: it depends on composition and on the initial grain temperature.
- $n$ is the burning index (the slope on the log–log plot): it depends mainly on composition.

![[prop_burning_rate.png|600]]

### Equilibrium chamber pressure

The step from the notes' statement that "the mass generated must balance the nozzle discharge" to a working formula (an extension, not printed in the notes).

Gas generated by a burning surface of area $A_b$ receding at $r$ into propellant of density $\rho_p$:

$$
\dot m_{gen} = \rho_pA_br = \rho_pA_baP_c^{\,n}
$$

Gas discharged through the choked throat (W10):

$$
\dot m_{noz} = \frac{P_cA_t}{C^*}
$$

**Quasi-steady chamber**: set them equal.

$$
\rho_pA_baP_c^{\,n} = \frac{P_cA_t}{C^*}
$$

Divide by $P_c^{\,n}$ and collect:

$$
P_c^{\,1-n} = \rho_paC^*\frac{A_b}{A_t}
$$

$$
\boxed{P_c = \left(\rho_paC^*\frac{A_b}{A_t}\right)^{\frac{1}{1-n}}}
$$

The area ratio $A_b/A_t$ (often written $K_n$) is the designer's main lever, and the thrust follows from $F=C_FP_cA_t$.

### Why n is less than one

Suppose $P_c$ rises slightly above equilibrium. Generation grows like $P_c^{\,n}$, discharge like $P_c^{\,1}$.

- If $n<1$, discharge grows faster, so the chamber empties and the pressure falls back: stable.
- If $n>1$, generation grows faster, so the pressure keeps rising: no stable operating point (in the limit, an explosion).
- Even below 1, sensitivity grows as $n\to1$: from the boxed result, $dP_c/P_c=\frac{1}{1-n}\,d(A_b/A_t)/(A_b/A_t)$.

**Interpretation of $n$:**

- $n=0$: flat burning, $r$ independent of $P_c$.
- $n<0$: rare, but interesting for reignition and extinction control.
- $n\to1$: small disturbances cause large changes in gas generation.
- $n>1$: unstable.
- Very low $n$ risks extinction at low pressure.
- In practice $0.2\lesssim n\lesssim0.8$.

**Grain shape → thrust curve.** $P_c$ follows $A_b(t)$, so the burning-area history shapes the thrust: progressive (rising, e.g. an internal tube), neutral (flat, e.g. a star or an end-burner) or regressive (falling).

### Worked example – chamber pressure and its sensitivity

Suggested example (not from the lecture). A composite propellant with $\rho_p=1750$ kg/m³ burns at $r=7$ mm/s at 7 MPa, with $n=0.35$, and $C^*=1500$ m/s. Write the law as $r=r_{ref}(P_c/P_{ref})^n$.

**Area ratio for $P_c=7$ MPa.** The balance becomes $(P_c/P_{ref})^{1-n}=\rho_pr_{ref}C^*K_n/P_{ref}$; set the left side to 1:

$$
K_n = \frac{P_{ref}}{\rho_pr_{ref}C^*} = \frac{7\times10^6}{1750\times0.007\times1500} = 381
$$

**Sensitivity.** If the burning area grows by 10 % (say a crack opens):

$$
\frac{P_c'}{P_c} = 1.1^{1/(1-n)} = 1.1^{1.54} = 1.16
$$

a 16 % pressure rise. With $n=0.8$ the same 10 % gives $1.1^{5}=1.61$, a 61 % rise: a high burning index turns small defects into dangerous overpressures.

### Other influences on the burning rate

**Initial propellant temperature $T_p$:**

- higher $T_p$ → hotter products → more heat flux into the grain → higher $r$;
- so higher thrust and a shorter burn;
- the total impulse is roughly unchanged (slightly higher through the pressure term);
- the case must survive the hot-day overpressure;
- non-uniform $T_p$ (sun on one side) causes thrust misalignment in large motors.

**Erosive burning:**

- gas flowing *along* the surface raises the heat transfer and so $r$;
- occurs in tubular grains, not in end-burners;
- strongest near the aft end (most accumulated mass flow) and early in the burn (smallest port area);
- significant for a port-to-throat area ratio $A_p/A_t<4$.

Vehicle acceleration normal to the burning surface (spin, anti-missile manoeuvres) causes micro-cracks, raising the burning area and $r$: noticeable around 5–10 g, and it can double $r$ above 30 g. For example, about 25 g at 2 rev/s and 1.5 m radius ($\omega^2r=(4\pi)^2\times1.5=237$ m/s² = 24 g).

---

## 4. Nozzle geometry

Quasi-1D theory (W03) only needs $A(x)$; a real nozzle needs the whole axisymmetric profile.

### Convergent section

The flow is subsonic with a favourable pressure gradient, so there is no separation and any smooth shape works.

- Contraction ratio 1.5–4: a higher ratio gives a lower chamber velocity and less stagnation-pressure loss during heat release (W04, heat addition in a duct).
- Convergence half-angle 30–45°, for a short, light nozzle.

### Throat

Two circular arcs (radius up to 2–3 × $r_t$) meet tangentially. Too tight an upstream curvature gives a vena contracta: the flow separates slightly and the effective $A_t$, and so the mass flow, is smaller than the geometric one.

### Divergent section

The critical part: the flow is supersonic, and a poor contour creates shocks.

**Conical.** Defined by its half-angle $\alpha$; simple and cheap; the wall (lateral) area scales as $1/\sin\alpha$. The exit flow is radial from the cone's apex, so only part of its momentum is axial.

*Derivation of the divergence factor.* Take the exit wavefront as a spherical cap of radius $R$ centred on the apex, with uniform mass flux crossing it radially. An annulus at polar angle $\theta$ has area $dA=2\pi R^2\sin\theta\,d\theta$ and its momentum has an axial fraction $\cos\theta$. The axial fraction of the total:

$$
\lambda = \frac{\int_0^\alpha\cos\theta\sin\theta\,d\theta}{\int_0^\alpha\sin\theta\,d\theta} = \frac{\tfrac12\sin^2\alpha}{1-\cos\alpha}
$$

Use $\sin^2\alpha=(1-\cos\alpha)(1+\cos\alpha)$:

$$
\boxed{\lambda = \frac{1+\cos\alpha}{2}}
$$

The momentum thrust is multiplied by $\lambda$ (notes eq. 11.3). $\alpha=15^\circ$ gives $\lambda=0.983$, a 1.7 % loss; 12° gives 0.989 and 18° gives 0.976. Use 12–18°: smaller angles make the nozzle too long, heavy and frictional; larger ones lose too much, and very large ones risk jet separation.

**Bell (contoured).** A large initial angle (30–60°) turning gradually to 2–8° at the exit, designed with 2-D (method-of-characteristics) models to cancel the expansion waves from the throat without creating compression waves. It is shorter and has lower divergence loss than a 15° cone of the same area ratio. It is not used on solid motors: two-phase Al₂O₃ particles in the exhaust erode the concave wall.

Unconventional designs, to cut launch cost and escape the single-design-altitude problem:

- *altitude-adaptive*: plug nozzle / aerospike, expansion–deflection;
- *multi-mode*: dual-bell, dual-mode;
- separation control and extendible cones (variable geometry).

### Real-nozzle losses

- exit flow divergence ($1-\lambda$);
- the contraction ratio and the chamber $p_0$ loss;
- the boundary layer (0.5–1.5 %);
- two-phase flow (particles lag the gas; up to 5 %);
- combustion instability, chemical effects (frozen versus shifting equilibrium, W05), transients and cooling.

---

## 5. The final review (12 May)

The last Grenga lecture reviewed combustion and compressible flow and set out the exam (L34, ll. 25–67):

- four questions, 25 marks each, all compulsory ("No, you have to do all four", l. 38), each split into marked sub-parts;
- expect roughly one each on rockets, turbomachinery, gas-turbine thermodynamics or shocks, and combustion;
- the data book is provided: "learn how to use the [equations], don't try to memorise" them (ll. 48–52);
- the course was restructured in 2021: papers from 2021 onwards are fully answerable; older papers contain topics no longer taught (ll. 62–67).

See [[SESA2023 Past Paper Map]].

---

## 6. Problem-solving workflow

1. For a solid motor: write the mass balance, then $P_c=(\rho_paC^*A_b/A_t)^{1/(1-n)}$.
2. Discuss sensitivity with the exponent $1/(1-n)$; state the stability condition $n<1$.
3. Relate $A_b(t)$ to the thrust curve (progressive, neutral, regressive).
4. For a nozzle: thrust $F=\lambda\dot mV_e+A_e(P_e-P_A)$ for a cone; compare with a bell.
5. List losses quantitatively where possible (divergence 1–2 %, boundary layer 0.5–1.5 %, two-phase up to 5 %).

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| burning rate $r$ | regression rate | Week 11 notes | |
| Saint-Robert's law | Vieille's law, burn-rate law | Week 11 notes | |
| burning index $n$ | pressure exponent | Week 11 notes | |
| temperature coefficient $a$ | burn-rate coefficient | Week 11 notes | Strictly $a$ is a coefficient; its temperature sensitivity is often quoted separately as $\sigma_p$. |
| $A_b/A_t$ | $K_n$, Klemmung | this note | Not named in the notes. |
| homogeneous / double-base propellant | colloidal propellant | Week 11 notes | |
| heterogeneous / composite propellant | — | Week 11 notes | |
| divergence factor $\lambda$ | divergence correction | notes eq. 11.3 | Not the payload ratio $\lambda$ of W10. |
| bell nozzle | contoured nozzle, Rao nozzle | Week 11 notes | |
| plug nozzle | aerospike | Week 11 notes | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Nozzle regimes (over- and under-expanded): [[Converging-Diverging Nozzle Operating Regimes]] · $C^*$, $C_F$: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles#2. Performance parameters|W10]]
- Formula list: [[SESA2023 Formula Sheet]] · exam strategy: [[SESA2023 Past Paper Map]]
- Not yet examined on the current syllabus (no Week 11 questions in the 2021-25 papers); still likely descriptive exam material.
- Method of characteristics for bell contours, taken further in Year 3: [[SESA3029 W05a - Method of Characteristics]] · [[SESA3029 W05b - Minimum-Length Nozzle Design]]
- **Related (SESA2028 materials):** [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|SESA2028 M5 CMCs]] (C/C nozzles) · [[Thermal Barrier Coatings]]

## Sources

- `Week 11 - Rockets.pdf` (notes: Grenga, Richardson) and `Week 11 - Rockets - Lecture Slides.pdf` (the notes call it Lecture 33).
- Transcripts: `SESA2023 Lecture 30.txt` (L30, 1 May, E. Richardson: solid motors, grain shapes, ll. 33–182); `SESA2023 Lecture 31.txt` (5 May, ll. 400–407: the plan for the Friday lecture); `SESA2023 Lecture 34.txt` (L34, 12 May: final review and exam structure). The 8 May lecture itself was not recorded.

## Self-study tasks

No tasks were recorded as set for Week 11 (the lecture has no transcript), so all of these except the last are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] Derive the equilibrium chamber pressure of a solid motor and explain why $n<1$ is required. → [[#Equilibrium chamber pressure]] · [[#Why n is less than one]]
- [ ] Explain how the propellant temperature changes the thrust, burn time and total impulse. → [[#Other influences on the burning rate]]
- [ ] Compare double-base and composite propellants in a table from memory. → [[#2. Propellants]]
- [ ] Sketch tube, star and anchor grains and their thrust–time curves; explain the Shuttle booster's two-peak profile. → [[#How a solid burns (L30, ll. 44–103)]]
- [ ] Derive $\lambda=(1+\cos\alpha)/2$ and evaluate it for 12°, 15° and 18°. → [[#Divergent section]]

### Further practice

- [ ] Chamber-pressure sensitivity for $n=0.35$ and $n=0.8$. Targets +16 %, +61 %. → [[#Worked example – chamber pressure and its sensitivity]]
- [ ] List the real-nozzle losses with typical magnitudes. → [[#Real-nozzle losses]]
- [ ] Explain why bell nozzles are not used on solid motors, and what altitude-adaptive nozzles try to fix. → [[#Divergent section]]
- [ ] *(set, 12 May)* Work the 2021–2025 papers under exam conditions with the data book (L34, ll. 42–67). → [[SESA2023 Past Paper Map]]
