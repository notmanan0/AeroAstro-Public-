---
title: "SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
order: 7
tags:
  - sesa2023
  - turbofan
  - bypass-ratio
  - fan-pressure-ratio
  - engine-architecture
aliases: ["Turbofan design", "Fan pressure ratio", "SESA2023 Week 7"]
date: 2026-09-24
status: lectured
coverage: "Week 7 (Lectures 20–21)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
next_topics: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
key_concepts: ["[[Bypass Ratio and Fan Pressure Ratio]]", "[[Propulsive Efficiency]]", "[[Turbojet]]", "[[Actuator Disk Theory]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 8 Turbofans Solutions]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf", "02 - Sources/Lectures/SESA2023 Lecture 20.txt", "02 - Sources/Lectures/SESA2023 Lecture 21.txt"]
---

# SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection

> [!abstract] Summary
> Propulsive efficiency needs a large mass flow with a small velocity increase, and the turbofan gets it by using the core's surplus energy, through a low-pressure turbine, to drive a fan that pushes a large bypass stream. The fan pressure ratio is the fundamental design variable: for a given flight condition it alone sets the bypass jet velocity, and so $\eta_P$ and the specific thrust, and for a fixed core it also sets the bypass ratio. Lowering it improves the bare-engine sfc but grows the fan, its nacelle drag and its weight, so the installed sfc has a minimum near fpr ≈ 1.5, where current engines sit (bpr ≈ 10–12); noise pushes the same way.

> [!summary]- Exam use: quick path
> - **Use it when:** a turbofan question gives the fpr (or bpr), the core pressure ratios and TET, and asks for jet velocities, bpr, specific thrust, sfc or $\eta_P$; or asks you to argue for a choice of fpr.
> - **Assumptions:** two-spool engine, steady; zero net work on each spool; isentropic intake; fully expanded separate nozzles; cold-air properties unless product values are given; $V_{jc}=V_{jb}$ (matched jets) unless stated.
> - **Method:** 1. Intake: $T_{02}$, $p_{02}$ from flight $M$. 2. Fan: $T_{013}$ from fpr and $\eta_f$; $V_{jb}$ from expanding $fpr\,p_{02}$ to $p_a$. 3. Core: booster, HPC, burner, HPT (HP spool balance) to station 45. 4. LPT pressure ratio chosen so $V_{jc}=V_{jb}$; then the LP spool balance gives bpr. 5. $X=F_N/\dot m_a$, sfc, $\eta_P$; installed sfc with $F_{N,eff}=F_N(1-kV/X)$.
> - **Common mistakes:** forgetting that the LP turbine also drives the booster (core part of the LP spool); using bpr instead of specific thrust to compare engines.
> - **Practise:** [[#Worked example – the PS8 fan-pressure-ratio sweep]] · [[SESA2023 Problem Sheet 8 Turbofans Solutions]] Q8.1–Q8.4

A turbojet puts all its surplus energy into a small, very fast jet, which leaves a lot of kinetic energy behind in the air (W01). A turbofan spreads the same energy over more air. A second turbine takes power out of the core gas and gives it to a big fan, which pushes a much larger flow much more slowly, giving more thrust and less waste from the same energy. The fan pressure ratio decides how fast the bypass air leaves. A low fpr means a slow, efficient jet but a huge fan, a high fpr a compact engine but a faster, noisier, less efficient jet.

A big fan needs a big nacelle, which adds drag, and weighs more, which adds lift and so more drag, and at some point it no longer fits under the wing. The best fpr is where those penalties balance the propulsive gain. A less obvious constraint is the turbine's speed: a big fan has to turn slowly to keep its tips below about Mach 1.5, which forces a slow LP turbine with many stages, and a gearbox breaks that link.

---

## 1. Architectures (Lecture 20)

![[prop_w07_turbofan_stations.png|860]]

| Architecture | Example | Features |
|---|---|---|
| Turbojet (single spool) | RR Viper (target drones, trainers) | light and cheap; high $V_j$; suits supersonic flight |
| Twin-spool turbojet | RR Olympus 593 (Concorde, M 2) | the HP spool spins faster; better off-design operation and starting |
| Low-bpr turbofan | P&W JT8D (727/737/DC-9; bpr 0.3, later 1.5) | first step to higher $\eta_P$ (L20, ll. 131–138) |
| High-bpr, two-spool + booster | GE GEnx (bpr ≈ 9.5) | fan × booster ≈ 2.5, HPC ≈ 20, OPR ≈ 45; two-stage HPT, seven-stage LPT |
| High-bpr, three-spool | RR Trent 1000 (bpr ≈ 9.5) | fan ≈ 1.5, IPC ≈ 7, HPC ≈ 4; more flexible off-design and at start-up, but more complex |
| Geared turbofan | P&W GTF / GT1524 (bpr 12) | a 2.5 : 1 gearbox lets a small, fast LPT drive a slow, large fan |
| Turboprop | A400M | very high effective bpr; propeller-tip Mach number limits flight speed |
| Open rotor | CFM RISE | rotor plus stator to remove swirl; no nacelle, but blade containment and noise are the challenges |
| Turbo-electric / distributed fans | NASA STARC-ABL, E-Thrust | free choice of fan number and position; boundary-layer ingestion cuts wasted jet KE; heavy electrical machines |

**Bypass ratio:**

$$
BPR = \frac{\dot m_b}{\dot m_c}
$$

In a GEnx-class engine about 85–92 % of the air goes down the bypass duct, so "the core is really just a generator to drive the fan" (L20, ll. 148–151; L21, ll. 115–117).

Station numbering (two-spool turbofan, handout §7.3.3): 2 fan face; 13 bypass after the fan; 19 bypass nozzle exit; 23 core after the fan root and booster; 3 HPC exit; 4 HPT entry; 45 LPT entry; 5 LPT exit; 9 core nozzle exit.

The station numbers follow the industry convention (L21, ll. 26–79). Station 1 is upstream of the intake and 2 the compressor or fan inlet, which is why the course always starts at 2; then 3 is the combustor inlet, 4 the turbine inlet and 5 the turbine exit. Stations 6, 7 and 8 are reserved for an afterburner, so a dry engine jumps straight to 9, the nozzle. An intermediate station gets a two-digit number halfway between its neighbours (23 between 2 and 3, 45 between 4 and 5), and the bypass, the "first additional stream", has its stations prefixed with 1: 13 after the fan and 19 at its nozzle. The W02 and W06 turbojet examples follow the handout instead and call the nozzle exit 6.

### One core, several engines (L20, ll. 27–49)

A simple gas turbine's turbine only needs to drive its compressor, so there is pressure left over after it. That surplus can go:

- through a propulsive nozzle: a turbojet;
- through a free power turbine driving a generator, a ship's propeller or an aircraft propeller: a turboshaft or turboprop;
- through a low-pressure turbine driving a fan: a turbofan.

The core can be thermodynamically, even physically, the same; Rolls-Royce sells its Trent cores for power generation and ship propulsion too.

### The examples in detail (L20, ll. 50–180)

- Viper (single spool): 17 compressor stages driven by 3 turbine stages, more than five times as many, because the compressor works against an adverse pressure gradient (W08). One moving part, cheap, very fast jet; used on missiles, trainers and target drones.
- Olympus (two spool, Vulcan and Victor bombers at M 0.9): compression split into two blocks of 7 stages, each driven by a single turbine stage. The large, low-density LP stages must turn slowly to keep tip speeds (and noise, and shock losses) down; the smaller HP spool can turn faster, and since work per stage rises with blade speed squared, it needs fewer stages. Two spools also help starting and part-load running, though at the design point the thermodynamics is identical.
- JT8D (early turbofan): a two-stage fan and booster on the LP spool, driven by three LP turbine stages; one HP turbine stage driving the HPC. Bypass ratio 0.3 at launch, later reworked to 1.5.
- Trent (three spool): separate HP, IP and LP spools, each at its own best speed. The prize is a shorter, smaller core, which shortens the heavy LP "barbell" (huge fan, long stiff shaft, huge turbine) where most of the weight is.

### Why the fan cannot just get bigger (L20, ll. 152–201)

The fan tip speed is limited to a relative Mach number of about 1.5 ("it is supersonic, but we don't want it to be Mach 2"). Since tip speed is $\Omega r$, a larger fan must turn more slowly. The LP turbine on the same shaft then turns slowly too, and for the same power it needs more stages or a larger diameter.

**The geared fan.** With a gear ratio $G$ the LP turbine turns $G$ times faster than the fan. For a fixed blade loading the work per stage scales with blade speed squared (W08, $\Delta h_0=\psi U^2$), so each turbine stage delivers about $G^2$ times more work:

$$
G = 2.5\qquad\Longrightarrow\qquad G^2 = 6.25
$$

"About six times more power per stage" (L20, l. 200): fewer, smaller stages and a much lighter turbine. The drawback is a gearbox that has to transmit nearly the whole engine power. At 50 MW, even 1 % loss is 500 kW of heat to reject through the oil system (L20, ll. 203–213).

### Open rotors and containment (L20, ll. 225–262)

An open rotor removes the nacelle's weight and drag and can reach a very high effective bypass ratio. Stator blades behind the rotor remove the swirl, which would otherwise be kinetic energy that produces no thrust (the same job the outlet guide vanes do behind a turbofan's fan). But a released fan blade cannot be contained by a Kevlar band in the casing, as it is in a turbofan: "if one of these blades becomes detached it's game over". And noise is harder: a turbofan's intake liners absorb the noise of the fan blades chopping the air, and an open rotor has no nacelle to put them in (L20, ll. 265–273).

> [!warning] Bypass fraction in the GTF video (L21, ll. 115–117)
> "About 85 % of the flow is going down the bypass duct… a 12 to 1 bypass ratio, which actually means it's probably 92 %." The lecturer's correction is right: $12/13=92$ %.

---

## 2. Spool power balances

In steady operation the net shaft work on each spool is zero (L21, ll. 175–212).

HP spool (HPC driven by HPT):

$$
\dot m_c\left(h_{03}-h_{023}\right) = (\dot m_c+\dot m_f)\left(h_{04}-h_{045}\right)
$$

LP spool (fan, booster and LPT). Split the fan into its bypass part (2→13) and its core part plus booster (2→23):

$$
\dot m_b\left(h_{013}-h_{02}\right)+\dot m_c\left(h_{023}-h_{02}\right) = (\dot m_c+\dot m_f)\left(h_{045}-h_{05}\right)
$$

**Bypass ratio.** Divide the LP balance by $\dot m_c$ and use $f=\dot m_f/\dot m_c$:

$$
BPR\left(h_{013}-h_{02}\right)+\left(h_{023}-h_{02}\right) = (1+f)\left(h_{045}-h_{05}\right)
$$

$$
\boxed{BPR = \frac{(1+f)\left(h_{045}-h_{05}\right)-\left(h_{023}-h_{02}\right)}{h_{013}-h_{02}}}
$$

> [!warning] Sign errors on the Lecture 21 slide (ll. 192–206)
> The lecturer corrects two signs while presenting the spool balances: the HPT term should be $h_{045}-h_{04}$ when written as "work in = 0" ("I'll fix it in the online version"), and the LPT term needs a minus sign. The forms above are written as "work absorbed = work delivered", which avoids the sign issue.

---

## 3. The fan pressure ratio sets the bypass jet (Lecture 21)

### Bypass jet velocity

"People often talk in terms of bypass ratio, but… it's the fan pressure ratio that's a more meaningful indication of how suitable an engine is for a particular application" (L21, ll. 134–137).

Intake (isentropic):

$$
T_{02} = T_a\left(1+\frac{\gamma-1}{2}M^2\right),\qquad \frac{p_{02}}{p_a} = \left(\frac{T_{02}}{T_a}\right)^{\gamma/(\gamma-1)}
$$

Fan (bypass part, efficiency $\eta_f$), with $fpr=p_{013}/p_{02}$:

$$
T_{013} = T_{02}\left(1+\frac{fpr^{(\gamma-1)/\gamma}-1}{\eta_f}\right)
$$

Bypass nozzle (isentropic, fully expanded from $p_{019}=p_{013}$ to $p_a$). From $h_0=h+\tfrac12V^2$ with $T_{019}=T_{013}$:

$$
\tfrac12V_{jb}^2 = c_p\left(T_{013}-T_{19}\right) = c_pT_{013}\left[1-\left(\frac{p_a}{p_{013}}\right)^{(\gamma-1)/\gamma}\right]
$$

and $p_{013}=fpr\cdot p_{02}$, so

$$
\boxed{V_{jb} = \sqrt{2c_pT_{013}\left[1-\left(\frac{p_a}{fpr\,p_{02}}\right)^{(\gamma-1)/\gamma}\right]}}
$$

The pressure ratio across the bypass nozzle is the product of the ram ratio $p_{02}/p_a$ (set by the flight Mach number) and the fan ratio (L21, ll. 145–149). For a given flight condition and fan efficiency, $V_{jb}$, and so $\eta_P$, depends only on fpr.

### Why matched jets

For fixed total air flow $\dot m$ and fixed thrust $F=\sum\dot m_i(V_i-V)$, the kinetic energy that must be supplied to the jets is $\sum\tfrac12\dot m_i(V_i^2-V^2)$. Write $V_i=\bar V+\epsilon_i$ with $\bar V$ the mass-averaged jet velocity, so $\sum\dot m_i\epsilon_i=0$ (fixed thrust):

$$
\sum\tfrac12\dot m_iV_i^2 = \tfrac12\dot m\bar V^2+\sum\tfrac12\dot m_i\epsilon_i^2
$$

The extra term is never negative and is zero only if every $\epsilon_i=0$. So for a given thrust the least energy is spent, and $\eta_P$ is highest, when the core and bypass jets have the same velocity. Matched jets also minimise noise.

### Design procedure (core fixed by OPR and TET)

1. Choose the fpr; this gives $V_{jb}$.
2. Choose the core jet velocity; $V_{jc}=V_{jb}$ maximises $\eta_P$.
3. Iterate the LPT pressure ratio $p_{045}/p_{05}$ until $V_{jc}$ matches.
4. The LP spool balance then gives the bpr.

### Specific thrust

With matched jets and $f\ll1$, specific thrust per kilogram of total air is just the velocity increase:

$$
X = \frac{F_N}{\dot m_{air}} = V_j-V
$$

It is "a better single descriptor" than bpr: the RB211 kept the same bypass ratio while its thrust and propulsive efficiency changed a lot (L21, ll. 152–174).

The RB211 shows the trade in practice (L21, ll. 152–171). Launched in 1971 at bpr 5 and fpr 1.5, it was asked for more thrust as its airframes were stretched, from 44,000 to about 60,000 lbf, with no more room under the wing, so Rolls-Royce raised the fpr and accepted a lower $\eta_P$. Its sfc still improved over the period, because a higher core pressure ratio and turbine temperature raised $\eta_{th}$ by more than $\eta_P$ fell.

### Worked example – the PS8 fan-pressure-ratio sweep

From [[SESA2023 Problem Sheet 8 Turbofans Solutions]] Q8.3, the like-for-like comparison of L21 (ll. 213–276): M 0.78 at 35,000 ft, OPR 45, TET 1500 K, all component efficiencies 0.9, the same core in every case, matched jets.

| fpr | $V_j$ (m/s) | $\eta_P$ | bpr | $X=F_N/\dot m_a$ (m/s) | sfc bare (g s⁻¹ kN⁻¹) | sfc with nacelle drag |
|---|---|---|---|---|---|---|
| 1.4 | 323 | 0.834 | 13.8 | 91.9 | 12.16 | 13.52 |
| 1.5 | 340 | 0.810 | 11.2 | 108.7 | 12.47 | 13.63 |
| 1.6 | 355 | 0.789 | 9.4 | 124.0 | 12.75 | 13.78 |

A pure turbojet with the same core (PS8 Q8.2) has $V_j=975$ m/s, $\eta_P=0.38$ and sfc 22.2 g s⁻¹ kN⁻¹: the fan almost halves the fuel burn.

![[prop_turbofan_fpr.png|760]]

Trends (L21, ll. 223–276):

- Lower fpr gives a higher bpr for the same core: with a given turbine power the fan can move more air if it accelerates it less. The LPT then does proportionally more of the work.
- Net thrust rises only modestly as fpr falls, because the larger fan swallows more air and so pays more ram drag $\dot m_aV$ (L21, ll. 240–248).
- Gross thrust rises strongly as fpr falls (more air), which matters at take-off: with one engine failed at M 0.25, gross thrust is what lets a twin complete the take-off (L21, ll. 249–264).
- Thermal efficiency is unchanged (same core), so the bare sfc improves through $\eta_P$ alone.

> [!check] The handout's headline numbers
> - Reducing fpr from 1.8 to 1.5 cuts the bare sfc by about 6 % (handout §7.3, from Fig. 19). The same model gives 13.24 → 12.47 g s⁻¹ kN⁻¹, −5.8 % ✔.
> - Specific thrust falls from 151 to 109 m/s, so for the same thrust the air mass flow must rise by $151/109=1.39$, i.e. 39 % in this model. The handout quotes 36 %, read from its figure.

---

## 4. The installed engine: nacelle drag and weight (Lecture 21)

### Nacelle drag

The "bare engine" thrust counts only the momentum fluxes in and out. The nacelle's outer surface and the bypass-duct walls add drag (L21, ll. 277–316). Drag scales with density, wetted area $A_w$ and velocity squared:

$$
D_{nac}\propto\rho A_wV^2 = (\rho A_wV)\,V
$$

$\rho A_wV$ has the form of a mass flow and scales with the engine air flow, $\dot m\propto\rho A_wV$. The air flow is $\dot m=F_N/X$, so

$$
D_{nac} = k\,\dot mV = kV\,\frac{F_N}{X}
$$

and the effective thrust is

$$
\boxed{F_{N,eff} = F_{N,bare}\left(1-\frac{kV}{X}\right)\approx F_{N,bare}\left(1-\frac{9.25}{X}\right)}
$$

with $kV\approx9$ m/s from typical data. At $X\approx100$ m/s this is about a 10 % loss (L21, ll. 313–316). Low fpr (low $X$) is hit hardest, because a lot of air is moved for little velocity increase.

### Engine weight

A bigger engine is heavier. Pure geometric scaling would give mass ∝ length³ (ll. 335–338); real engine families are lighter than that because big engines get the best technology, so empirically the mass scales between the square and the cube of the fan diameter (ll. 347–352). The handout uses

$$
W_{eng} = 12\left(\frac{d}{3\ \mathrm m}\right)^{2.4}\ \mathrm{tonne}
$$

including nacelle and pylon. Extra weight needs extra lift, and with $L/D=21.6$ every tonne of engine costs $1/21.6$ of a tonne-force of extra drag:

$$
F_{N,corr} = F_{N,eff}-\frac{W_{eng}}{L/D}
$$

### The result

- Drag and weight turn the steady improvement in bare sfc into a real optimum: a large penalty below fpr ≈ 1.5, and a flat plateau above it (L21, ll. 362–369). The corrected sfc is about 40 % above the bare value.
- Rolls-Royce sits at the low-fpr end of the plateau, so something else must favour low fpr: noise.
- Very large fans also bring problems with blade stresses, ground and wing clearance, and air-freighting the engine (ll. 373–378).
- fpr ≈ 1.5 matches current industry practice.

### Noise

The most restrictive airport sets the design: London Heathrow for noise, probably Zurich for NOₓ (L21, ll. 381–391). Because jet noise rises so steeply with jet velocity, a high fpr is "an absolutely massive penalty"; on modern engines jet noise has been cut so far that turbomachinery noise now competes with it (ll. 393–400).

> [!warning] Seventh or eighth power?
> Both lecturers say jet noise scales with "jet velocity to the power of seven" (L1, l. 439; L21, l. 397, speaking of sound pressure level). The handout (§7.2.3) says "jet noise scales with jet velocity to the power of eight", which is Lighthill's law for the radiated acoustic power. Either way the message is the same; quote the course's form and say which quantity you mean.

The exam angle is the trade-off itself: "explain how a greater bypass ratio affects fpr and fuel consumption" ([[SESA2023 Exam 2021-22 Solutions]] Q3(iii)), or in the lecture's framing, "like all good engineering choices it's a trade-off… write a few bullet points on either side" (L21, ll. 406–411). A high fpr gives a smaller, lighter engine that is easier to manufacture and has less nacelle drag. A low fpr gives a higher $\eta_P$, a lower bare sfc, much less noise and more gross thrust at take-off. At a fixed overall pressure ratio and core, a higher bypass ratio needs a lower fpr and more LPT work, so more stages or a gearbox.

> [!warning] The JT8D was not a 707 engine (L20, ll. 116–117; L21, l. 375)
> Both lectures place "the JT8 engine" on the Boeing 707. The JT8D powered the 727, 737 and DC-9; the 707 used the JT3D. The point being made, slim early engines against today's large fans, is unaffected.

---

## 5. Problem-solving workflow

1. Sketch the two-spool layout with stations 2, 13, 19, 23, 3, 4, 45, 5, 9.
2. Intake → $T_{02}$, $p_{02}$; fan → $T_{013}$; bypass nozzle → $V_{jb}$.
3. Core: booster (2→23), HPC (23→3), burner (3→4), HPT from the HP spool balance (4→45).
4. LPT: find $p_{045}/p_{05}$ so that $V_{jc}=V_{jb}$ (or as specified), then $T_{05}$.
5. LP spool balance → bpr; thrust, $X$, sfc, $\eta_P$.
6. Installed: $F_{N,eff}=F_N(1-kV/X)$, then subtract $W_{eng}/(L/D)$ if weight is included.
7. Argue the trade-off: efficiency and noise versus size, weight, drag and turbine speed.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| fan pressure ratio (fpr) | FPR, $\pi_f$ | handout §7.3.2, L21 | $p_{013}/p_{02}$. |
| bypass ratio (bpr) | BPR, $\beta$ | handout §7.3.2 | $\dot m_b/\dot m_c$. |
| specific thrust $X$ | — | L21, l. 298 | $F_N/\dot m_{air}$, in m/s. |
| bare engine | uninstalled engine | handout §7.3.6 | thrust from momentum fluxes only. |
| effective / corrected net thrust | installed thrust | handout §§7.3.6–7.3.7 | after nacelle drag / weight. |
| booster | low-pressure compressor (LPC) | handout §7.2.3 | |
| intermediate-pressure compressor (IPC) | — | L20 (Trent) | three-spool engines only. |
| geared turbofan (GTF) | — | L20, ll. 191–215 | |
| boundary-layer ingestion (BLI) | — | handout §7.2.5 | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · Next: [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]
- Propulsive efficiency and the "large mass, small $\Delta V$" argument: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA#Why not make the jet as slow as the aircraft|W01]]
- Worked sheet: [[SESA2023 Problem Sheet 8 Turbofans Solutions]] · Formula list: [[SESA2023 Formula Sheet]]
- Exams: [[SESA2023 Exam 2013-14 Solutions]] Q3 (M 2 turbofan), [[SESA2023 Exam 2020-21 Solutions]] Q4 (geared LPT stage count), [[SESA2023 Exam 2021-22 Solutions]] Q3, [[SESA2023 Exam 2023-24 Solutions]] Q3 (electric ducted fan, BLI)
- Fan tip speed and stage work: [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]] · [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]

## Sources

- `Week 06-07 - Jet Engines.pdf`: Weeks 6–7 handout (E. Richardson) §7 (architectures, fpr and bpr, station numbering, bare engine, nacelle and weight, Fig. 19) and the Lecture 20–21 slides.
- Transcripts (line numbers refer to these files): L20 `SESA2023 Lecture 20.txt` (10 Mar: architectures, geared fans, open rotors); L21 `SESA2023 Lecture 21.txt` (13 Mar: fpr, bpr, installation, noise). L1 is `SESA2023 Lecture 1.txt`.

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 7 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Calculate a bypass ratio from the LP spool balance: "one of the examples set this week asks you to do that" (L21, ll. 208–212). → [[#2. Spool power balances]] · [[SESA2023 Problem Sheet 8 Turbofans Solutions]] Q8.1
- [ ] *(set)* Work [[SESA2023 Problem Sheet 8 Turbofans Solutions|Problem Sheet 8 (turbofans)]]: core temperatures, the pure turbojet, the matched-jet turbofan and installed sfc.
- [ ] *(set)* Write "a few bullet points on either side" of the fpr trade-off (L21, ll. 406–411). → [[#The result]]
- [ ] Derive $V_{jb}$ in terms of fpr and flight Mach number. → [[#Bypass jet velocity]]

### Further practice

- [ ] Derive the bpr formula from the LP spool balance. → [[#2. Spool power balances]]
- [ ] Show that matched jets minimise the kinetic energy needed for a given thrust. → [[#Why matched jets]]
- [ ] Derive $F_{N,eff}=F_N(1-kV/X)$ from the drag scaling. → [[#Nacelle drag]]
- [ ] Explain why a 2.5 : 1 gearbox gives about six times the work per LPT stage. → [[#Why the fan cannot just get bigger (L20, ll. 152–201)]]
- [ ] Explain the RB211's growth from 44,000 to 60,000 lbf at constant bpr. → [[#Specific thrust]]
- [ ] Number the stations of a two-spool turbofan from memory and explain the convention (why 9, 23, 45, 13, 19). → [[#1. Architectures (Lecture 20)]]
- [ ] Explain why the Viper needs 17 compressor stages but only 3 turbine stages, and what a second spool buys. → [[#The examples in detail (L20, ll. 50–180)]]
- [ ] Check the 6 % sfc gain from fpr 1.8 → 1.5 and the extra air flow needed. Targets −5.8 %, +39 %. → [[#Worked example – the PS8 fan-pressure-ratio sweep]]
