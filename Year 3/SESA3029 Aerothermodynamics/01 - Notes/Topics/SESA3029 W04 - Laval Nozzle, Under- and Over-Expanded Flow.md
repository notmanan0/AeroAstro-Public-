---
title: "SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 3: Nozzles and the Method of Characteristics"
order: 4
tags: [sesa3029, compressible-flow, nozzle, laval, choked-flow, back-pressure, over-expanded, under-expanded, wind-tunnel]
aliases: ["SESA3029 Week 4", "SESA3029 Lecture 2.6", "SESA3029 Lecture 2.7", "Laval Nozzle (SESA3029)"]
date: 2026-10-01
status: complete
coverage: "Lectures 2.6 and 2.7 (from the slides; no transcripts)"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[Isentropic Nozzle Flow]]"]
next_topics: []
key_concepts: ["[[Isentropic Nozzle Flow]]", "[[Critical Conditions and Choked Flow]]", "[[Converging-Diverging Nozzle Operating Regimes]]", "[[Over- and Under-Expanded Jets]]", "[[Supersonic Wind Tunnel]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 1 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture2-6.pdf", "02 - Sources/Lectures/Lecture2-7.pdf"]
---

# SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow

> [!abstract] Summary
> **Quasi-one-dimensional isentropic duct flow obeys**
>
> $$\frac{\mathrm dA}{A}=(M^2-1)\frac{\mathrm dU}{U}.$$
>
> Subsonic flow speeds up in a converging duct, supersonic flow in a diverging one, and $M=1$ can only occur at a throat.
>
> **Laval nozzle.** Integrating mass flow against the sonic state gives the area–Mach relation $A/A^*(M)$. For each area ratio it has one subsonic and one supersonic root. Once the throat is sonic the nozzle is **choked**: $\dot m\propto p_0A_t/\sqrt{T_0}$, whatever happens downstream.
>
> **Lowering the back pressure** $p_b$ takes the nozzle through these regimes in turn:
>
> 1. subsonic venturi flow;
> 2. choked with a subsonic exit ($p_{b3}$);
> 3. a normal shock in the diverging part, moving downstream as $p_b$ falls;
> 4. the shock at the exit ($p_{b5}$);
> 5. **over-expanded** ($p_e<p_\infty$): oblique lip shocks;
> 6. the design point ($p_{b6}$);
> 7. **under-expanded** ($p_e>p_\infty$): lip expansion fans.
>
> **Free jets.** The W03 tools (shocks, fans, reflection from a constant-pressure slip line) explain the shock-diamond pattern.
>
> **Supersonic wind tunnel.** A second throat recovers pressure, but it must be at least $p_{01}/p_{02}$ times the first throat to swallow the starting shock: 3.05 at $M=3$.

## Key concepts

- New: [[Over- and Under-Expanded Jets]] · [[Supersonic Wind Tunnel]]
- Year 2 foundations, extended here: [[Isentropic Nozzle Flow]] (SESA2022) · [[Critical Conditions and Choked Flow]] · [[Converging-Diverging Nozzle Operating Regimes]] (SESA2023) · [[Rocket Nozzle Geometry]]
- From W03: [[Expansion Fan]] · [[Slip Line]] · [[Regular Shock Reflection]] · [[Mach Reflection]]

> [!info] Scope note
> These notes are written from the slides `Lecture2-6.pdf` and `Lecture2-7.pdf`; no transcripts exist yet. Every result is derived in full, including the A/A* relation that slide 2.6-5 sets as homework.

---

## The whole topic in one physical picture

Think of the nozzle as a **mass-flow funnel** with a speed limit at its narrowest point.

1. Squeeze subsonic gas through a narrowing duct and it speeds up, like a garden hose.
2. At the throat it reaches the speed of sound. From then on the throat passes the **maximum** mass flow the reservoir can push, so the nozzle is choked.
3. Past the throat, supersonic gas does the opposite of intuition: it **accelerates as the duct widens**. Each extra unit of area is filled more by the falling density than by a rise in speed.
4. The exit pressure the nozzle "wants" is fixed by its area ratio. The surroundings set a different pressure $p_b$. The mismatch is fixed by **waves**: a normal shock inside the nozzle if $p_b$ is high, oblique shocks or fans at the lip if $p_b$ is only slightly high or low. Those lip waves then bounce along the jet edge as shock diamonds.

---

## 1. The area–velocity relation (Lecture 2.6, slides 2–4)

![[at_area_mach_derivation.png|900]]

**Assumptions** (quasi-one-dimensional): the area varies slowly, properties are uniform across each section, and the flow is steady, adiabatic and inviscid, hence isentropic.

**(a) Mass.** $\rho UA=\text{const}$. Take logarithms and differentiate:

$$
\ln\rho+\ln U+\ln A=\text{const}
\quad\Longrightarrow\quad
\frac{\mathrm d\rho}{\rho}+\frac{\mathrm dU}{U}+\frac{\mathrm dA}{A}=0.
$$

**(b) Momentum.** Euler's equation for steady inviscid flow along the duct:

$$
\mathrm dp=-\rho U\,\mathrm dU.
$$

**(c) Isentropic link.** The speed of sound is defined by $a^2=(\partial p/\partial\rho)_s$, so $\mathrm dp=a^2\,\mathrm d\rho$. Combine with (b):

$$
\frac{\mathrm d\rho}{\rho}=\frac{\mathrm dp}{a^2\rho}=-\frac{U\,\mathrm dU}{a^2}=-M^2\,\frac{\mathrm dU}{U}.
$$

**(d) Substitute into (a).**

$$
-M^2\frac{\mathrm dU}{U}+\frac{\mathrm dU}{U}+\frac{\mathrm dA}{A}=0
\quad\Longrightarrow\quad
\boxed{\frac{\mathrm dA}{A}=\left(M^2-1\right)\frac{\mathrm dU}{U}}
$$

**What it says**:

| | $M<1$ ($M^2-1<0$) | $M>1$ ($M^2-1>0$) |
|---|---|---|
| converging ($\mathrm dA<0$) | $\mathrm dU>0$: **nozzle** | $\mathrm dU<0$: **diffuser** |
| diverging ($\mathrm dA>0$) | $\mathrm dU<0$: **diffuser** | $\mathrm dU>0$: **nozzle** |

At $M=1$ the equation forces $\mathrm dA=0$, so **sonic flow can only occur where the area is stationary**. In a converging–diverging duct that is the throat. To accelerate continuously from rest to supersonic speed you need a converging–diverging (**de Laval**) nozzle with $M=1$ exactly at the throat.

> [!tip] Why supersonic flow "behaves backwards"
> From (c), the fractional density change is $M^2$ times the fractional velocity change. Below $M=1$ the density barely changes, so a wider duct means slower flow, as in incompressible flow. Above $M=1$ the density falls faster than the speed rises, so the gas needs **more** area to carry the same $\dot m$ as it speeds up.

---

## 2. The area–Mach relation (homework, slide 5; Anderson §10.3)

Mass flow is the same at any section and at the sonic section $A^*$, which may be real (a sonic throat) or fictitious:

$$
\rho UA=\rho^*a^*A^*
\quad\Longrightarrow\quad
\frac{A}{A^*}=\frac{\rho^*}{\rho}\,\frac{a^*}{U}.
$$

Insert the stagnation state and use $U=Ma$:

$$
\frac{A}{A^*}=\frac{\rho^*}{\rho_0}\cdot\frac{\rho_0}{\rho}\cdot\frac{a^*}{a}\cdot\frac{1}{M}.
$$

Each ratio comes from the stagnation relations, with $X=1+\tfrac{\gamma-1}{2}M^2$ ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#4. Stagnation properties|W01 §4]]):

$$
\frac{\rho_0}{\rho}=X^{1/(\gamma-1)},
\qquad
\frac{\rho^*}{\rho_0}=\left(\frac{2}{\gamma+1}\right)^{1/(\gamma-1)},
$$

$$
\frac{a^*}{a}=\sqrt{\frac{T^*}{T_0}\frac{T_0}{T}}=\left(\frac{2}{\gamma+1}X\right)^{1/2}.
$$

The first two combine into $\left(\dfrac{2X}{\gamma+1}\right)^{1/(\gamma-1)}$. Multiply by the third and add the exponents:

$$
\frac{1}{\gamma-1}+\frac12=\frac{\gamma+1}{2(\gamma-1)}.
$$

$$
\boxed{\frac{A}{A^*}=\frac{1}{M}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{\frac{\gamma+1}{2(\gamma-1)}}}
$$

For air the exponent is 3. The function has a minimum of 1 at $M=1$, so **each $A/A^*>1$ has two Mach numbers**, one subsonic and one supersonic. Which one occurs is set by the back pressure (§4).

> [!check] Values ($\gamma=1.4$)
> - $A/A^*(2.2)=2.005$, $A/A^*(3)=4.2346$ and $A/A^*(2.5)=2.637$, all matching the IFT.
> - The subsonic root of 2.005 is $M=0.3051$.

---

## 3. Mass flow and choking

Evaluate $\dot m=\rho^*a^*A^*$ with $\rho^*=\rho_0\left(\tfrac{2}{\gamma+1}\right)^{1/(\gamma-1)}$, $a^*=a_0\sqrt{\tfrac{2}{\gamma+1}}$, $\rho_0=p_0/(RT_0)$ and $a_0=\sqrt{\gamma RT_0}$:

$$
\dot m=\frac{p_0}{RT_0}\sqrt{\gamma RT_0}\left(\frac{2}{\gamma+1}\right)^{\frac{1}{\gamma-1}+\frac12}A^*
$$

$$
\boxed{\dot m=\frac{p_0A^*}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}=0.0404\,\frac{p_0A^*}{\sqrt{T_0}}\ \ \text{(air, SI)}}
$$

- **Choked flow.** For given reservoir conditions, $\dot m$ is greatest when the throat is sonic ($A_t=A^*$). Once that happens, lowering $p_b$ further **cannot** raise $\dot m$: the information cannot travel upstream through the sonic throat. See [[Critical Conditions and Choked Flow]].
- **Across a shock** $T_0$ is unchanged but $p_0$ falls. Since $\dot m$ is the same, $p_{01}A^*_1=p_{02}A^*_2$, so the effective sonic area **grows** by $p_{01}/p_{02}$:

$$
\boxed{\frac{A^*_2}{A^*_1}=\frac{p_{01}}{p_{02}}}
$$

This one identity locates shocks in nozzles (§4) and sizes the second throat of a wind tunnel (§7).

---

## 4. Flow regimes as the back pressure falls (2.6 slides 6–13; 2.7 slide 2)

![[at_laval_regimes.png|900]]

Worked throughout for the lecture nozzle, designed for $M_e=2.2$, so $A_e/A_t=A/A^*(2.2)=2.005$.

| Back pressure | What happens |
|---|---|
| $p_{b1}$, $p_{b2}$ (just below $p_0$) | Subsonic throughout, a venturi. The throat is not sonic, so $\dot m$ rises as $p_b$ falls. |
| $p_{b3}=0.9375\,p_0$ | Throat just sonic, so the nozzle is **choked**, but the diverging part decelerates the flow subsonically: the subsonic root of $A/A^*=2.005$, $M_e=0.3051$. |
| $p_{b5}<p_b<p_{b3}$ | Supersonic after the throat, then a **normal shock** in the diverging part, then subsonic diffusion to $p_e=p_b$. |
| $p_{b5}=0.5125\,p_0$ | The shock sits **at the exit plane**. |
| $p_{b6}<p_b<p_{b5}$ | Shock-free inside and supersonic at the exit, but $p_e<p_b$: **over-expanded**. Oblique shocks at the lip (§5). |
| $p_{b6}=0.0935\,p_0$ | **Design**: $p_e=p_b$, a clean parallel jet. |
| $p_b<p_{b6}$ | $p_e>p_b$: **under-expanded**. Expansion fans at the lip (§6). |

### Computing the three critical back pressures

**$p_{b6}$ (design).**

$$
p_{b6}/p_0=(p/p_0)_{2.2}=0.0935.
$$

**$p_{b3}$ (subsonic choked).** Solve $A/A^*=2.005$ on the subsonic branch. IFT rows 0.30 (2.0351, 0.9395) and 0.32 (1.9219, 0.9315):

$$
\sigma=\frac{2.005-2.0351}{1.9219-2.0351}=0.266,
\qquad
M_e=0.3053,
\qquad
\frac{p_{b3}}{p_0}=0.9374.
$$

The exact values are 0.3051 and 0.9375.

**$p_{b5}$ (normal shock at the exit).** Normal shock at $M=2.2$: $p_2/p_1=1+\tfrac{2.8}{2.4}(4.84-1)=5.480$. So

$$
\frac{p_{b5}}{p_0}=5.480\times0.0935=0.5125.
$$

Behind the shock, $M=0.5471$.

### Where is the shock for a given back pressure?

The trick is to work **backwards from the exit**, where $p_e=p_b$ is known (panel e):

1. $\dot m$ is the same at the throat and at the exit: $p_{01}A_t=p_{0e}A_e^*$, using §3 with $T_0$ unchanged.
2. Hence

$$
\frac{p_e}{p_{0e}}\cdot\frac{A_e}{A_e^*}=\frac{p_bA_e}{p_{01}A_t}.
$$

   The right-hand side is **known**. The left-hand side is a function of $M_e$ alone, so solve for $M_e$ (subsonic).

3. Then $p_{0e}=p_b/(p/p_0)_{M_e}$. This equals $p_{02}$, so $p_{02}/p_{01}$ is known.
4. Find the shock Mach number $M_s$ from the normal-shock table's $p_{02}/p_{01}$ column.
5. The shock sits where $A/A_t=A/A^*(M_s)$ on the supersonic branch.

**Worked: $p_b/p_0=0.7$.**

1. $\dfrac{p_bA_e}{p_{01}A_t}=0.7\times2.005=1.4035$.
2. Solve $(p/p_0)(A/A^*)=1.4035$ on the subsonic branch: $M_e=0.406$.
3. $p_{0e}/p_{01}=0.7/(p/p_0)_{0.406}=0.784$.
4. Normal-shock table: $M_s=1.864$.
5. $A_s/A_t=A/A^*(1.864)=1.511$.

| $p_b/p_0$ | 0.6 | 0.7 | 0.8 | 0.9 |
|---|---:|---:|---:|---:|
| $M_s$ | 2.048 | 1.864 | 1.657 | 1.371 |
| $A_s/A_t$ | 1.757 | 1.511 | 1.298 | 1.100 |

Lower back pressure pushes the shock downstream, where it is stronger. As $p_b\to p_{b3}$ the shock shrinks to zero strength at the throat.

---

## 5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)

![[at_nozzle_jets.png|900]]

For $p_{b6}<p_b<p_{b5}$ the exit flow is supersonic with $p_e<p_\infty$. It has to be **recompressed**, so:

1. **Oblique shocks form at the lips**, with just the turning angle needed to raise the pressure to $p_\infty$. The jet boundary (a [[Slip Line]], whose pressure must equal $p_\infty$) turns inward.
2. **The two lip shocks cross** on the axis. Behind the crossing, the flow has been compressed twice, so its pressure is now **above** $p_\infty$.
3. **The shocks reach the jet boundary.** A constant-pressure boundary cannot hold a pressure jump, so each shock **reflects as an expansion fan**. This is the opposite of a solid wall, where a shock reflects as a shock (W03 §1).
4. **The fans cross**, overshooting: the pressure is now **below** $p_\infty$.
5. **The fans reflect from the boundary as compression waves.** These coalesce into shocks, and the pattern repeats. These are the **shock diamonds** in an afterburner plume (the SR-71 photograph on slides 1 and 7).

**Sizing the lip shock from the pressure ratio.** Invert the oblique-shock pressure jump:

$$
\frac{p_\infty}{p_e}=1+\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right)
\quad\Longrightarrow\quad
M_{n1}=\sqrt{1+\frac{\gamma+1}{2\gamma}\left(\frac{p_\infty}{p_e}-1\right)}.
$$

Then $\beta=\sin^{-1}(M_{n1}/M_e)$, and $\theta$ follows from the $\theta$–$\beta$–$M$ relation.

**Worked: $M_e=2.2$, $p_b/p_0=0.20$.**

$$
\frac{p_\infty}{p_e}=\frac{0.20}{0.0935}=2.139
\ \Rightarrow\
M_{n1}=1.406,
\quad
\beta=39.71^\circ,
\quad
\theta=13.67^\circ,
\quad
M_2=1.679.
$$

At the crossing each stream must be turned back by $13.67^\circ$, and $\theta_{max}(1.679)=16.5^\circ$. So this is a **regular** crossing.

**Mach disc (slide 7).** At $p_b/p_0=0.30$, the lip shock gives $\theta=21.6^\circ$ but $\theta_{max}(M_2=1.32)=7.2^\circ$. A regular crossing is impossible, so a **Mach disc** forms: the axisymmetric version of the W03 Mach reflection. Panel (c) puts the switch at $p_b/p_0\approx0.216$ for this nozzle. That is a planar estimate; real axisymmetric jets differ in detail.

---

## 6. Under-expanded jets (slides 5–7)

For $p_b<p_{b6}$ the exit pressure is **above** ambient, so the flow must expand further:

1. **Prandtl–Meyer fans at the lips** expand the flow to $p_\infty$ and turn the jet boundary **outward**.
2. **The fans cross** and over-expand: the pressure falls below $p_\infty$.
3. **The fans reflect from the boundary as compression waves**, which coalesce into shocks.
4. **The shocks cross** and raise the pressure to about the exit value: *"back where we started"*, and the pattern continues.

**Worked: $p_b/p_0=0.05$.** The jet must reach $p/p_0=0.05$, i.e. $M_j=2.602$. The lip turn is

$$
\nu(2.602)-\nu(2.2)=41.45^\circ-31.73^\circ=9.72^\circ.
$$

> [!note] Slide 7 summary
> - After the first cell, over- and under-expanded jets follow the **same** mechanism.
> - The slip line follows a **barrel** shape.
> - The shocks form a **diamond** pattern.
> - If the turning angle is too large for a regular crossing, a **Mach disc** appears.

---

## 7. The supersonic wind tunnel (slides 8–11)

![[at_wind_tunnel_starting.png|900]]

**Ideal configuration** (slide 8): reservoir → nozzle with first throat $A_{t1}$ → supersonic test section → diffuser with second throat $A_{t2}$ → subsonic exit. The diffuser recovers pressure far better than dumping the test-section flow as an open jet, so the tunnel needs a lower reservoir pressure.

**Why $A_{t2}>A_{t1}$.** If $A_{t2}<A_{t1}$, the second throat would choke first and fix $\dot m$ at a value too small for the first throat ever to go sonic, so there would be **no supersonic flow**. Even $A_{t2}=A_{t1}$ fails during start-up, because a shock with $p_0$ loss is then in the circuit.

**Starting** (slide 9). When the tunnel is switched on, a normal shock forms in the diverging nozzle and moves into the test section. With the shock standing in the test section at the test Mach number $M$, the flow reaching the second throat has stagnation pressure $p_{02}<p_{01}$. To pass the same $\dot m$ at its lower $p_0$, the second throat needs, from §3,

$$
\boxed{\frac{A_{t2}}{A_{t1}}\ \ge\ \frac{A^*_2}{A^*_1}=\frac{p_{01}}{p_{02}}\Big|_{\text{normal shock at }M}}
$$

If that holds, the shock is pushed through the test section and **swallowed** by the diffuser. $A_{t2}$ can then be reduced towards the ideal running size.

**Worked: $M=3$ (slides 10–11, the slide's route).**

1. IFT at $M=3$: $A_{test}/A_{t1}=A/A^*(3)=4.2346$.
2. Normal-shock table at $M=3$: $M_2=0.4752$ and $p_{02}/p_{01}=0.3283$.
3. Behind the shock, the second throat must choke the $M_2=0.4752$ flow. IFT rows 0.46 (1.4246) and 0.48 (1.3801): $\sigma=0.76$, so $A_{test}/A_{t2}=1.3908$ (exact: 1.3904).
4. $\dfrac{A_{t2}}{A_{t1}}=\dfrac{A_{test}/A_{t1}}{A_{test}/A_{t2}}=\dfrac{4.2346}{1.3908}=3.045.$

> [!check] The same answer in one line
> $1/(p_{02}/p_{01})=1/0.3283=3.046$. Both routes agree, because $A/A^*(M)\big/A/A^*(M_2)$ equals $p_{01}/p_{02}$ for a normal shock. It is the §3 identity in disguise.

| Test Mach number | 1.5 | 2 | 2.5 | 3 | 4 | 5 |
|---|---:|---:|---:|---:|---:|---:|
| minimum $A_{t2}/A_{t1}$ | 1.076 | 1.387 | 2.004 | 3.046 | 7.21 | 16.2 |

At high $M$ a fixed-geometry second throat becomes impractical. That motivates variable-geometry diffusers and the short-duration facilities below.

### Ludwieg tube (slides 12–13)

A long tube of high-pressure gas is separated from a low-pressure dump tank by a diaphragm or fast valve. Bursting it sends a shock and contact discontinuity downstream and an **expansion wave upstream** into the storage tube (the shock-tube CFD on slide 12). A Laval nozzle behind the valve accelerates the gas in the expanded region to supersonic or hypersonic speed. The test lasts until the expansion wave reflects off the closed end and returns, of order **0.1 s**. That is enough for force and pressure measurements, at a fraction of the cost of a continuous tunnel. Slide 13 shows TU Braunschweig's 17 m storage tube and the Mach-number field developing over 30 ms.

### Next (slide 14)

1D theory gives uniform properties at each section. The **method of characteristics** resolves both $x$ and $y$ and is the basis for designing shock-free supersonic nozzles (Anderson §13.3). It is also the subject of the **MoC coursework, due 15 Nov**. [[SESA3029 Example Sheet 2 - Solutions]] gives a first look.

---

## 8. Problem-solving workflow

1. Find the **design** point: $A_e/A_t\to M_e$ (supersonic root) $\to p_{b6}$.
2. Find $p_{b3}$ (subsonic root) and $p_{b5}$ ($p_{b6}\times$ the normal-shock $p_2/p_1$ at $M_e$).
3. Place the given $p_b$ in the table of §4 to identify the regime.
4. **Shock inside:** use the exit-backwards method of §4.
5. **Lip waves:** $p_\infty/p_e$ gives $M_{n1}$ and $\beta$, then $\theta$ (shock); or $\nu(M_j)-\nu(M_e)$ (fan). Then check $\theta_{max}$ for a regular crossing.
6. **Wind tunnel:** the second-throat ratio is $p_{01}/p_{02}$ at the test Mach number.

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]
- Year 2: [[Isentropic Nozzle Flow]] · [[Critical Conditions and Choked Flow]] · [[Converging-Diverging Nozzle Operating Regimes]] · [[Rocket Nozzle Geometry]] · [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]
- New concepts: [[Over- and Under-Expanded Jets]] · [[Supersonic Wind Tunnel]]
- Worked sheet: [[SESA3029 Example Sheet 1 - Solutions#Q8. Supersonic wind-tunnel nozzle|Example Sheet 1 Q8]]
- Formulae: [[SESA3029 Formula Sheet]]

## Sources

- `Lecture2-6.pdf`: 2.6 Laval Nozzle (14 slides)
- `Lecture2-7.pdf`: 2.7 Under/Over-expanded Nozzles (14 slides; the SR-71 photographs, schlieren image DOI 10.1177/1475472X19834521, and the TU Braunschweig Ludwieg tube)
- No transcripts yet.
- Anderson, *Fundamentals of Aerodynamics*, §§10.1–10.6 (nozzles and diffusers) and §13.3 (preview of MoC)
- Figures: `generate_aerothermo_w04_figures.py`

## Self-study tasks

> [!todo] How to use this list
> No transcripts exist for Lectures 2.6–2.7. Tasks printed on the slides are **slide-set**; the rest are *suggested, not lecturer-set*.

### Derivations

- [ ] **Slide-set (2.6, slide 5, "homework"):** derive $A/A^*(M)$ (Anderson §10.3). → [[#2. The area–Mach relation (homework, slide 5; Anderson §10.3)|§2]]
- [ ] *(Suggested)* Derive $\mathrm dA/A=(M^2-1)\,\mathrm dU/U$ from mass, Euler and $\mathrm dp=a^2\mathrm d\rho$. → [[#1. The area–velocity relation (Lecture 2.6, slides 2–4)|§1]]
- [ ] *(Suggested)* Derive the choked mass flow and the constant 0.0404 for air. → [[#3. Mass flow and choking|§3]]
- [ ] *(Suggested)* Show $A^*_2/A^*_1=p_{01}/p_{02}$ across a shock. → [[#3. Mass flow and choking|§3]]

### Calculations

- [ ] $M_e=2.2$ nozzle: $p_{b3}=0.9375$, $p_{b5}=0.5125$, $p_{b6}=0.0935$ (times $p_0$). → [[#Computing the three critical back pressures|§4]]
- [ ] Shock position for $p_b/p_0=0.7$: $A_s/A_t=1.511$. → [[#Where is the shock for a given back pressure?|§4]]
- [ ] Lip-shock angle for $p_b/p_0=0.2$, and whether the crossing is regular. → [[#5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)|§5]]
- [ ] **Slide-set example (2.7, slides 10–11):** $A_{t2}/A_{t1}=3.045$ at $M=3$. → [[#7. The supersonic wind tunnel (slides 8–11)|§7]]
- [ ] Example Sheet 1 Q8 (wind-tunnel nozzle). → [[SESA3029 Example Sheet 1 - Solutions#Q8. Supersonic wind-tunnel nozzle|ES1 Q8]]

### Concepts

- [ ] Sketch $p(x)$ for $p_{b1}$ to $p_{b6}$ and explain each regime. → [[#4. Flow regimes as the back pressure falls (2.6 slides 6–13; 2.7 slide 2)|§4]]
- [ ] Explain why a shock reflects from a free (constant-pressure) boundary as a fan, and from a wall as a shock. → [[#5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)|§5]]
- [ ] Explain why $A_{t2}<A_{t1}$ can never give supersonic flow. → [[#7. The supersonic wind tunnel (slides 8–11)|§7]]
- [ ] Read Anderson §13.3 before the MoC lectures; MoC coursework due **15 Nov**.
