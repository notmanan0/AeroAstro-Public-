---
title: "SESA3029 Test 2 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Block 2: normal and oblique shocks, expansions and shock interactions"
tags: [sesa3029, tutorial-solutions, blackboard-test, normal-shock, pitot, oblique-shock, prandtl-meyer, slip-line]
sheet: "Blackboard Test 2"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
status: complete
due: 2026-10-25
sources: ["03 - Exams & Past Papers/aerothermo test 2 questions.txt"]
---

# SESA3029 Test 2 - Solutions

> [!abstract] Test info
> Blackboard Test 2 (2.5 % of the module, best of two attempts). It opened on **Mon 19 Oct** and closes **Sun 25 Oct, midnight** (L3-1, ll. 3–5; L3-2, ll. 2–8; reminder in L3-4, l. 6). There are five questions on Weeks 1–3: the normal-shock stagnation-pressure loss, the Pitot test, the oblique-shock chart, a Prandtl–Meyer expansion, and the shock–shock interaction of Lecture 2.3. These are worked solutions for revision, written after the test had been done by hand. Every number was checked in Python with $\gamma=1.4$, and the table values were regenerated from the exact relations (they match `IFT.pdf` and `NST.pdf` to 4 d.p.).

| Q | Answer | Tool | Theory |
|---|---|---|---|
| 1 | $M_1=2.22$ | NST $p_{02}/p_{01}$ column, read backwards | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#4. It is a normal shock in the normal component\|W02 §4]] |
| 2 | supersonic, $M_1=2.65$ | test against 1.893, then Rayleigh ($p_{02}/p_1$ column) | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#7. Pitot probe: three regimes\|W01 §7]] |
| 3 | $M_1=1.85$ (exact 1.8635) | OSC, between the 1.8 and 1.9 curves | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#6. The oblique-shock chart\|W02 §6]] |
| 4 | $p_U=22.9$ kPa (exact 22.8) | Prandtl–Meyer, nearest IFT row | [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method\|W03 §6]] |
| 5 | $\Delta\theta=5.815^\circ$ | two θ–β–M solves per side, iterate to $p_{3A}=p_{3B}$ | [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#3. Shock–shock interaction and slip lines\|W03 §3]] |

> [!warning] The method changes the last digit
> Q3 and Q4 name the method: "use OSC, nearest 0.05" and "use IFT, reading to nearest value". The exact answers (1.86 and 22.8 kPa) differ in the last quoted digit from the method-specified ones (1.85 and 22.9 kPa). Use the stated method, as the lecturer insists exam questions will specify one (L2-2, ll. 74–80).

---

## Q1. Mach number from the stagnation-pressure loss

> Across a normal shock the stagnation pressure drops by 38.1 %. Find $M_1$ to two decimal places.

![[at_test2_shock_ratios.png|900]]

**Step 1: turn the percentage into a ratio.** A drop of 38.1 % leaves 61.9 % of the upstream value:

$$
\frac{p_{02}}{p_{01}}=1-0.381=0.619.
$$

**Step 2: the relation to invert.** Chain three ratios across the shock:

$$
\frac{p_{02}}{p_{01}}=\frac{p_{02}}{p_2}\cdot\frac{p_2}{p_1}\cdot\frac{p_1}{p_{01}}.
$$

Write $D=2\gamma M_1^2-(\gamma-1)$. From [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Deriving the Rayleigh Pitot formula|W01]], the first factor is

$$
\frac{p_{02}}{p_2}=\left[\frac{(\gamma+1)^2M_1^2}{2D}\right]^{\gamma/(\gamma-1)}.
$$

The third factor is the isentropic relation at station 1:

$$
\frac{p_1}{p_{01}}=\left[\frac{2+(\gamma-1)M_1^2}{2}\right]^{-\gamma/(\gamma-1)}.
$$

Multiply these two (same exponent):

$$
\frac{p_{02}}{p_2}\cdot\frac{p_1}{p_{01}}=\left[\frac{(\gamma+1)^2M_1^2}{D\left(2+(\gamma-1)M_1^2\right)}\right]^{\gamma/(\gamma-1)}.
$$

Split the bracket into two factors:

$$
=\left[\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\right]^{\gamma/(\gamma-1)}\left[\frac{\gamma+1}{D}\right]^{\gamma/(\gamma-1)}.
$$

Multiply by the pressure jump $p_2/p_1=D/(\gamma+1)=[(\gamma+1)/D]^{-1}$. The exponent on $(\gamma+1)/D$ drops by one, to $\gamma/(\gamma-1)-1=1/(\gamma-1)$:

$$
\boxed{\frac{p_{02}}{p_{01}}=\left[\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}\right]^{\gamma/(\gamma-1)}\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}}
$$

With $\gamma=1.4$ the exponents are 3.5 and 2.5.

**Step 3: read the NST backwards.**

| $M_1$ | $p_{02}/p_{01}$ |
|---:|---:|
| 2.20 | 0.6281 |
| 2.22 | 0.6191 |

The target 0.619 is almost exactly on the 2.22 row. Interpolating:

$$
M_1=2.20+0.02\times\frac{0.6281-0.619}{0.6281-0.6191}=2.20+0.02\times\frac{0.0091}{0.0090}=2.2202.
$$

$$
M_1=\boxed{2.22}
$$

> [!check] Exact root and an entropy check
> - Solving the boxed formula with a root finder gives $M_1=2.2201$ ✓. At $M_1=2.22$: $[2.4\times4.9284/3.9714]^{3.5}=45.60$ and $[2.4/13.3995]^{2.5}=0.013576$. The product is $0.6191$ ✓.
> - The entropy rise is $\Delta s=-R\ln(p_{02}/p_{01})=-287\ln0.619=137.7$ J/(kg K) ([[Entropy Change Across a Shock]]).

> [!warning] Two traps
> - Entering the table with $0.381$ (the **loss**) instead of $0.619$ (what is **left**) gives $M_1=2.83$.
> - The $p_{02}/p_1$ column (Rayleigh) is a different quantity. It is the one for Q2, not Q1.

---

## Q2. Pitot probe: subsonic or supersonic?

> A Pitot probe reads a total pressure of 103 kPa and the static pressure is 10.8 kPa. Decide whether the flow is subsonic or supersonic, then find $M_1$ to two decimal places.

**Step 1: the test.** A Pitot probe in subsonic flow reads $p_0$ isentropically, and $p_0/p$ reaches its largest subsonic value at $M=1$:

$$
\left.\frac{p_0}{p}\right|_{M=1}=\left(1+\frac{\gamma-1}{2}\right)^{\gamma/(\gamma-1)}=1.2^{3.5}=1.893.
$$

The measured ratio is

$$
\frac{103}{10.8}=9.537>1.893,
$$

so the flow is **supersonic**. Equivalently, $p/p_0=0.1049$ is below $p^*/p_0=0.5283$. A bow shock stands ahead of the probe, and the probe reads $p_{02}$, the stagnation pressure **behind** the shock ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Case 3: compressible supersonic|W01 §7, Case 3]]).

**Step 2: the [[Rayleigh Pitot Formula]].** The static tapping sees the free stream, so the ratio is $p_{02}/p_1$:

$$
\frac{p_{02}}{p_1}=\left[\frac{(\gamma+1)M_1^2}{2}\right]^{\gamma/(\gamma-1)}\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}=9.537.
$$

**Step 3: read the NST's last column ($p_{02}/p_1$) backwards.**

| $M_1$ | $p_{02}/p_1$ |
|---:|---:|
| 2.64 | 9.4506 |
| 2.66 | 9.5869 |

$$
M_1=2.64+0.02\times\frac{9.5370-9.4506}{9.5869-9.4506}=2.64+0.02\times0.634=2.6527.
$$

$$
M_1=\boxed{2.65}\quad(\text{supersonic})
$$

> [!check] Exact root and consistency
> - The root finder gives $M_1=2.6527$ ✓.
> - The free-stream stagnation pressure is $p_{01}=p_1/(p/p_0)_{2.6527}=10.8/0.04620=233.8$ kPa. The probe reads 103 kPa, i.e. $103/233.8=0.4406$, which equals the NST $p_{02}/p_{01}$ at $M_1=2.6527$ ✓. The shock destroys 56 % of the total pressure before the probe sees it.

> [!warning] The isentropic trap
> Using the subsonic formula $p_0/p=(1+0.2M^2)^{3.5}$ on 9.537 gives $M=2.13$, which is wrong by 0.5. It ignores the bow shock (dotted curve in the figure above). The test against 1.893 comes first.

---

## Q3. Mach number from the oblique-shock chart

> A trailing-edge flap deflected by 5° generates a shock at 37°. Find $M_1$ ahead of the shock using the OSC, to the nearest 0.05.

![[at_test2_osc_reading.png|900]]

**Step 1: what is known.** The flap turns the flow by $\theta=5^\circ$, and the shock angle is $\beta=37^\circ$. Normally $M_1$ and $\theta$ give $\beta$. Here the chart is read the other way: find the curve through the point $(\theta,\beta)=(5^\circ,37^\circ)$.

**Step 2: read the chart.** The OSC has one curve every 0.1 in $M_1$. At $\theta=5^\circ$ (weak branch):

- the $M_1=1.8$ curve is at $\beta=38.44^\circ$;
- the $M_1=1.9$ curve is at $\beta=36.23^\circ$.

$37^\circ$ lies between them, slightly nearer the 1.9 curve. A linear estimate is

$$
M_1\approx1.8+0.1\times\frac{38.44-37}{38.44-36.23}=1.8+0.1\times0.652=1.865,
$$

and to the nearest 0.05:

$$
M_1=\boxed{1.85}
$$

**Step 3 (check): invert θ–β–M exactly.** The relation ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#5. The θ–β–M relation, step by step|W02 §5]]) is

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}.
$$

Given $\theta$ and $\beta$ it is linear in $M_1^2$, so it can be solved in closed form. Multiply out the denominator:

$$
\tan\theta\left[M_1^2(\gamma+\cos2\beta)+2\right]=2\cot\beta\left(M_1^2\sin^2\beta-1\right).
$$

Expand both sides:

$$
M_1^2\tan\theta\,(\gamma+\cos2\beta)+2\tan\theta=2M_1^2\cot\beta\sin^2\beta-2\cot\beta.
$$

Collect the $M_1^2$ terms on one side:

$$
M_1^2\left[2\cot\beta\sin^2\beta-\tan\theta\,(\gamma+\cos2\beta)\right]=2\left(\cot\beta+\tan\theta\right).
$$

Use $2\cot\beta\sin^2\beta=2\sin\beta\cos\beta=\sin2\beta$:

$$
\boxed{M_1^2=\frac{2\left(\cot\beta+\tan\theta\right)}{\sin2\beta-\tan\theta\,(\gamma+\cos2\beta)}}
$$

Substitute $\cot37^\circ=1.32704$, $\tan5^\circ=0.087489$, $\sin74^\circ=0.961262$ and $\cos74^\circ=0.275637$:

$$
M_1^2=\frac{2\times1.414534}{0.961262-0.087489\times1.675637}=\frac{2.829068}{0.814662}=3.4727.
$$

$$
M_1=1.8635.
$$

To the nearest 0.05 this is still **1.85** ✓.

> [!check] Is it a sensible shock?
> $M_{n1}=1.8635\sin37^\circ=1.121$, a weak shock. The Mach angle is $\mu=\sin^{-1}(1/1.8635)=32.45^\circ$, so the shock is only $4.5^\circ$ steeper than a Mach wave, as expected for a $5^\circ$ turn. Downstream, $M_2=1.690$ and $p_2/p_1=1.301$.

> [!tip] A useful by-product
> The closed form makes "given $\theta$ and $\beta$, find $M_1$" an easy direction, just like "given $\beta$ and $M_1$, find $\theta$" ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#8.3 The easy direction: given β, find θ|W02 §8.3]]). Only "given $M_1$ and $\theta$, find $\beta$" needs iteration.

---

## Q4. Upper-surface pressure on a flat plate

> A flat plate at $\alpha=10^\circ$ in a stream at $M_1=1.8$, $p_1=40$ kPa. Find the upper-surface pressure using the IFT, reading to the nearest value. One decimal place.

**Step 1: which wave.** At the leading edge the upper surface turns **away** from the oncoming flow by $\alpha$, so the upper flow passes through a Prandtl–Meyer **expansion** of $10^\circ$. The lower surface gets a shock ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]; picture: `at_shock_expansion_plate.png`).

**Step 2: Prandtl–Meyer.** Across the fan the turning angle adds to $\nu$:

$$
\nu(M_U)=\nu(M_1)+\alpha.
$$

From the IFT row $M=1.80$, $\nu=20.7251^\circ$:

$$
\nu(M_U)=20.7251^\circ+10^\circ=30.7251^\circ.
$$

**Step 3: nearest IFT row.**

| $M$ | $\nu$ (deg) | $p/p_0$ |
|---:|---:|---:|
| 1.80 | 20.7251 | 0.1740 |
| 2.16 | **30.6884** | **0.0996** |
| 2.18 | 31.2121 | 0.0965 |

$30.7251^\circ$ is $0.037^\circ$ from the 2.16 row and $0.487^\circ$ from the 2.18 row, so $M_U=2.16$.

**Step 4: pressure ratio.** The fan is isentropic, so $p_0$ is the same on both sides and

$$
\frac{p_U}{p_1}=\frac{(p/p_0)_{M_U}}{(p/p_0)_{M_1}}.
$$

Substitute the two table values:

$$
\frac{p_U}{p_1}=\frac{0.0996}{0.1740}=0.5724.
$$

$$
p_U=40\times0.5724=22.897\ \text{kPa}.
$$

$$
p_U=\boxed{22.9\ \text{kPa}}
$$

> [!check] Exact route
> Interpolating instead gives $M_U=2.16+0.02\times0.0367/0.5237=2.1614$. The exact relations then give $p_U=22.83$ kPa, i.e. **22.8** to one decimal place. The question's "nearest value" instruction is what makes 22.9 the expected answer.

> [!example] The lower surface, for completeness (not asked)
> A $10^\circ$ compression at $M_1=1.8$ gives $\beta=44.06^\circ$ and $M_{n1}=1.252$, so $p_L/p_1=1.661$ and $p_L=66.4$ kPa, with $M_L=1.449$. With $q_1=\tfrac12\gamma p_1M_1^2=90.72$ kPa, the normal-force coefficient is $c_n=(66.44-22.90)/90.72=0.480$. So $c_l=c_n\cos\alpha=0.473$ and $c_d=c_n\sin\alpha=0.083$ (wave drag).

---

## Q5. Shock–shock interaction at M₁ = 3.1

> Revisit the Lecture 2.3 slide 7 interaction (lower wall up by $\theta_A=18^\circ$, upper wall down by $\theta_B=12^\circ$) with $M_1=3.1$ instead of 3. Find the slip-line angle $\Delta\theta$ to three decimal places.

![[at_test2_slip_line.png|900]]

The procedure is exactly that of [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#Solving it, one step at a time|W03 §3]]. Only the numbers change.

**Step 1: incident shocks (zones 2A and 2B).**

| | zone 2A ($\theta_A=18^\circ$) | zone 2B ($\theta_B=12^\circ$) |
|---|---:|---:|
| $\beta$ | $34.739^\circ$ | $28.554^\circ$ |
| $M_{n1}=3.1\sin\beta$ | 1.7665 | 1.4818 |
| $p_2/p_1$ | 3.4739 | 2.3949 |
| $M_2$ | 2.1672 | 2.4837 |
| flow direction | $+18^\circ$ | $-12^\circ$ |

**Step 2: the matching conditions.** After the transmitted shocks both streams must have the same direction $\Delta\theta$ and the same pressure ([[Slip Line]]):

- zone 2A is turned **down** by $\theta_A-\Delta\theta$;
- zone 2B is turned **up** by $\theta_B+\Delta\theta$;
- require $p_{3A}/p_1=p_{3B}/p_1$, where $p_{3A}/p_1=(p_{2A}/p_1)(p_{3A}/p_{2A})$ and likewise for B.

**Step 3: two guesses.** The $M_1=3$ answer (5.85° on the slide) is a good starting point, so try $5^\circ$ and $6^\circ$:

| $\Delta\theta$ | turn A | $\beta_{3A}$ | $p_{3A}/p_{2A}$ | $p_{3A}/p_1$ | turn B | $\beta_{3B}$ | $p_{3B}/p_{2B}$ | $p_{3B}/p_1$ | difference |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| $5^\circ$ | $13^\circ$ | $39.516^\circ$ | 2.0518 | 7.1278 | $17^\circ$ | $39.409^\circ$ | 2.7339 | 6.5474 | $+0.5805$ |
| $6^\circ$ | $12^\circ$ | $38.409^\circ$ | 1.9483 | 6.7683 | $18^\circ$ | $40.599^\circ$ | 2.8812 | 6.9000 | $-0.1317$ |

Each $\beta_3$ is measured from the zone-2 flow direction, with $M_{2A}=2.1672$ or $M_{2B}=2.4837$ as the upstream Mach number.

**Step 4: interpolate to zero difference.**

$$
\Delta\theta=5^\circ+1^\circ\times\frac{0.5805}{0.5805-(-0.1317)}
$$

$$
=5^\circ+1^\circ\times\frac{0.5805}{0.7122}
$$

$$
=5^\circ+0.8151^\circ=5.8151^\circ.
$$

$$
\Delta\theta=\boxed{5.815^\circ}\ \text{(upwards, towards the stronger turn)}
$$

> [!check] Exact root and the state behind the crossing
> - A root finder on the full relations gives $\Delta\theta=5.81497^\circ$, i.e. $5.815^\circ$ ✓. The two-guess interpolation is already exact to 3 d.p., because the difference is nearly linear in $\Delta\theta$ (panel a).
> - At the solution $p_3/p_1=6.834$ on both sides, but $M_{3A}=1.709$ vs $M_{3B}=1.735$, $T_{3A}/T_1=1.844$ vs $T_{3B}/T_1=1.824$, and $p_{03}/p_{01}=0.802$ vs $0.834$. The slip line is real.
> - The same code gives $5.827^\circ$ at $M_1=3$, against the slide's chart-read $5.85^\circ$. Blackboard may accept a tolerance band; the value above is the exact one.

> [!tip] Why $\Delta\theta$ hardly moves
> Raising $M_1$ from 3.0 to 3.1 raises **both** pressure curves by about 5 % (panel a), so their crossing barely shifts: $5.827^\circ\to5.815^\circ$. At high Mach number the θ–β–M curves crowd towards the $M_1\to\infty$ limit ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#The M₁ → ∞ curve|W02 §6]]). The way the turning is shared between the two sides is then set mainly by the wall angles. The pressure level is what changes: $p_3/p_1=6.535\to6.834$.

> [!important] Exam link
> This interaction was last year's exam question (L2-3, ll. 317–319). In the exam, zones 2A and 2B and the first guess were given; you made the second guess and interpolated (ll. 379–382). Steps 3–4 above are exactly that procedure.

---

## Links

- Theory: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] · [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]
- Concepts: [[Normal-Shock Jump Relations]] · [[Rayleigh Pitot Formula]] · [[Compressible Pitot Probe]] · [[Theta-Beta-Mach Relation]] · [[Prandtl-Meyer Function]] · [[Shock-Expansion Theory]] · [[Slip Line]] · [[Entropy Change Across a Shock]] · [[Shock-Table Interpolation]]
- Module: [[SESA3029 Aerothermodynamics Hub]] · [[SESA3029 Formula Sheet]]
- Previous test: [[SESA3029 Test 1 - Solutions]]

## Sources

- `03 - Exams & Past Papers/aerothermo test 2 questions.txt` (the five Test 2 questions, copied from Blackboard)
- Dates: `Lecture 3-1.txt`, ll. 3–5; `Lecture 3-2.txt`, ll. 2–8; `Lecture 3-4.txt`, l. 6 (*"quiz closes on Sunday"*).
- Q5 geometry: `02 - Sources/Lectures/Lecture2-3.pdf`, slide 7; exam context `Lecture 2-3.txt`, ll. 317–390.
- Tables and chart: `IFT.pdf`, `NST.pdf`, `OSC.pdf`.
- Figures: `generate_aerothermo_test2_figures.py` (`at_test2_shock_ratios.png`, `at_test2_osc_reading.png`, `at_test2_slip_line.png`).

## Self-study tasks

> [!todo] Not lecturer-set beyond the test itself
> The test was set on Blackboard (L3-1, ll. 3–5; L3-2, ll. 2–8). Q5 also answers the L2-3 *"basically your homework"* (ll. 317–319) at a new Mach number. The other tasks are *suggested, not lecturer-set*.

- [ ] **Submit Test 2 by Sun 25 Oct, midnight** (L3-2, ll. 2–8; L3-4, l. 6); two attempts, highest mark counts.
- [ ] **(L2-3, ll. 317–319, 379–382)** Redo Q5 the exam way: take zones 2A and 2B as given, make a second guess from $5^\circ$, and interpolate. → [[#Q5. Shock–shock interaction at M₁ = 3.1]]
- [ ] Derive the boxed $p_{02}/p_{01}$ formula from the three-ratio chain. → [[#Q1. Mach number from the stagnation-pressure loss]]
- [ ] Derive the closed-form $M_1^2(\theta,\beta)$ and use it to check a chart reading. → [[#Q3. Mach number from the oblique-shock chart]]
- [ ] Finish Q4: find $p_L$, $c_l$ and $c_d$ for the plate. → [[#Q4. Upper-surface pressure on a flat plate]]
- [ ] Explain why the Pitot ratio must be tested against 1.893 before choosing a formula. → [[#Q2. Pitot probe: subsonic or supersonic?]]
- [ ] Explain why the slip-line angle barely changes between $M_1=3.0$ and 3.1. → [[#Q5. Shock–shock interaction at M₁ = 3.1]]
