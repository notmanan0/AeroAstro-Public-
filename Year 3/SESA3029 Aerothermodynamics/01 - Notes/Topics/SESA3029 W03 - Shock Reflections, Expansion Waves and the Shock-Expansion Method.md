---
title: "SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 2: Oblique Shocks and Expansions"
order: 3
tags: [sesa3029, compressible-flow, shock-reflection, mach-reflection, slip-line, entropy, prandtl-meyer, expansion-fan, shock-expansion]
aliases: ["SESA3029 Week 3", "SESA3029 Lecture 2.3", "SESA3029 Lecture 2.4", "SESA3029 Lecture 2.5"]
date: 2026-10-01
status: lectured
coverage: "Lectures 2.3, 2.4 and 2.5 (lectured 2, 5 and 8 Oct; transcripts L2-3, L2-4 and last year's L2-5 recording)"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[Theta-Beta-Mach Relation]]", "[[Mach Waves and Mach Angle]]"]
next_topics: ["[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
key_concepts: ["[[Regular Shock Reflection]]", "[[Mach Reflection]]", "[[Slip Line]]", "[[Entropy Change Across a Shock]]", "[[Prandtl-Meyer Function]]", "[[Expansion Fan]]", "[[Shock-Expansion Theory]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 1 - Solutions]]", "[[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing]]"]
sources: ["02 - Sources/Lectures/Lecture2-3.pdf", "02 - Sources/Lectures/Lecture 2-3.txt", "02 - Sources/Lectures/Lecture2-4.pdf", "02 - Sources/Lectures/Lecture 2-4.txt", "02 - Sources/Lectures/Lecture2-5.pdf", "02 - Sources/Lectures/Lecture 2-5 (2025-26 version).txt"]
---

# SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method

> [!abstract] Summary
> Lecture 2.3 reflects oblique shocks off walls (regular reflection, and Mach reflection when that fails) and crosses them into each other, which brings in the slip line; it also shows that the entropy jump grows like $(M_{n1}^2-1)^3$, so expansion shocks are impossible and weak shocks are nearly isentropic. Lecture 2.4 handles convex corners with the Prandtl–Meyer fan, $\nu(M_2)=\nu(M_1)+\theta$. Lecture 2.5 combines shocks and fans into the shock-expansion method for lift, wave drag and moment on flat-faced aerofoils.

> [!summary]- Exam use: quick path
> - **Use it when:** a shock meets a wall or another shock, a flow turns round a convex corner, or a flat-faced aerofoil sits in a supersonic stream.
> - **Assumptions:** steady, inviscid, 2-D, $\gamma=1.4$ (IFT); fans are isentropic ($p_0$ constant); shock-expansion needs sharp edges, attached shocks and flat faces (uniform pressure on each).
> - **Method:** 1. At each corner: turned into the flow → oblique shock; away → fan, $\nu_2=\nu_1+\theta$. 2. Wall reflection: the same $\theta$ again from $M_2$; if $\theta>\theta_{max}(M_2)$ it is a Mach reflection. 3. Shock crossings and trailing edges: match $p$ and flow direction across the slip line. 4. Aerofoil: face pressures → chord-normal $N'$ and chordwise $A'$ → $L'$, $D'$. 5. Moment about the LE; centre of pressure along the chord with $C_n$.
> - **Common mistakes:** $D'=N'\sin\alpha$ on a thick section (misses $A'$); moving the moment with $C_l$ instead of $C_n$ at large $\alpha$.
> - **Practise:** [[#Flat plate at incidence, step by step (slides 7–13): M₁ = 2, α = 10°, p₁ = 30 kPa, c = 1 m|§6 flat plate]] · [[SESA3029 Mock Questions - Weeks 1-5#Q4. Diamond aerofoil by shock-expansion theory|Mock Q4]]

> [!info] Scope note
> - **Lecture 2.3** was given on Fri 2 Oct (`Lecture 2-3.txt`, 447 lines). It covered the whole deck: the regular-reflection example (ll. 15–176), Mach reflection (ll. 205–293), the double shock interaction set as homework (ll. 312–390) and the entropy argument (ll. 394–447).
> - **Lecture 2.4** was given on Mon 5 Oct (`Lecture 2-4.txt`, 463 lines). It covered the physical picture, the Prandtl–Meyer derivation and the $M_1=3$, $\theta=13^\circ$ example (ll. 4–449), and stopped there.
> - **Lecture 2.5** (shock-expansion method) was given on Thu 8 Oct. The recording on Blackboard is **last year's**, `Lecture 2-5 (2025-26 version).txt` (263 lines): it refers to "Tuesday" (l. 4) and "next week" (l. 262), last year's timetable. Friday's tutorial confirms that this year's lecture happened: *"yesterday we learned that the aerodynamic center and center pressure are at the half code"* (Tutorial 1, l. 148). §6 now carries `L2-5` line references to that recording. It covered the flat plate only; the diamond was left for the example sheets.
> - **Tutorial Lecture 1** (Fri 9 Oct): ES1 Q3 and a triangular wing, written up in [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing]].
>
> References like `L2-3, l. 166` point to transcript lines. Transcript slips are flagged in [[#Transcript slips (Lectures 2.3 and 2.4)]] and [[#Transcript slips (Lecture 2.5)]].

---

At a corner, a supersonic stream can only be turned into itself or away from itself. Turned into itself, at a concave corner or a wall in the way, it gets no warning upstream and has to turn abruptly through an oblique shock, which compresses and slows it and costs stagnation pressure. Turned away from itself, at a convex corner, the Mach waves from successive parts of the turn spread apart instead of piling up, so the turn happens smoothly through a fan that expands and speeds up the flow at no cost in stagnation pressure.

Two matching conditions do the rest. At a wall the flow has to end up parallel to the wall, which is where reflections come from. Across a slip line the pressure and flow direction have to match, which settles shock interactions and trailing edges. The shock-expansion method then just walks round a body corner by corner.

---

## 1. Regular shock reflection from a wall

### Why a reflected shock must exist

A ramp of angle $\theta$ makes an oblique shock A (slides 2–3). Behind A, zone 2 flows parallel to the ramp, tilted up by $\theta$. When A meets the upper wall, the zone-2 flow is aimed into that wall. That can't happen, because the wall allows no normal velocity, so something has to turn the flow back down by $\theta$. To the zone-2 flow the upper wall looks like a compression ramp of angle $\theta$, and an oblique shock is what turns a flow at a compression ramp, so a **reflected shock** B leaves the wall. Step B is the same problem as step A with $M_1$ replaced by $M_2$, and the same deflection measured from $\mathbf V_2$ ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#1. Where oblique shocks come from|W02 §1]]).

### Worked example (slides 2–4): M₁ = 3.6, θ = 10°, p₁ = 40 kPa

![[at_regular_reflection.png|900]]

**Step A, incident shock (zones 1 → 2).**

$$
\theta=10^\circ,\ M_1=3.6\ \ \xrightarrow{\ \theta\text{–}\beta\text{–}M,\ \text{weak}\ }\ \ \beta_A=23.90^\circ,
$$

$$
M_{n1}=3.6\sin23.90^\circ=1.4584,
\qquad
M_{n2}=0.7163,
\qquad
\frac{p_2}{p_1}=2.3149,
$$

$$
M_2=\frac{0.7163}{\sin(23.90^\circ-10^\circ)}=2.982.
$$

**Step B, reflected shock (zones 2 → 3).** It has the same $\theta=10^\circ$, now from $M_2=2.982$:

$$
\beta_B=27.51^\circ\ \ (\text{measured from }\mathbf V_2),
\qquad
M_{n2B}=2.982\sin27.51^\circ=1.3775,
$$

$$
M_{n3}=0.7494,
\qquad
\frac{p_3}{p_2}=2.0472,
\qquad
M_3=\frac{0.7494}{\sin17.51^\circ}=2.490.
$$

**Result.** Chain the static-pressure ratios:

$$
p_3=\frac{p_3}{p_2}\,\frac{p_2}{p_1}\,p_1=2.0472\times2.3149\times40=189.6\ \text{kPa}.
$$

The reflected shock makes an angle with the upper wall of

$$
\phi=\beta_B-\theta=17.51^\circ\neq\beta_A=23.90^\circ.
$$

> [!check] Checks
> - $T_0$ is constant throughout.
> - $M_3<M_2<M_1$, and $p_3/p_1=4.74$.
> - Check A through the density: $\tan\beta_A/\tan(\beta_A-\theta)=0.4431/0.2475=1.790=\rho_2/\rho_1$ at $M_{n1}=1.4584$ ✓.
> - The slide's intermediate value uses the rounded $M_2=2.98$, giving $M_{n2B}=1.376$; the unrounded $M_2$ gives 1.3775.

The lecturer's choice of tool at each step is worth copying (L2-3, ll. 61–160). Step A can't use the chart, which stops at $M_1=3$, so $\beta$ has to come from the θ–β–M equation with a root finder (ll. 65–75); he asks you to *"confirm that this is the correct answer"* (l. 76). The normal-shock table is entered with $M_n$, not $M$ (*"What does n mean? Normal."*, ll. 81–91), interpolating between rows for $M_{n1}=1.459$ (ll. 99–108). Step B can use the chart, because $M_2=2.98$ is just below 3 (ll. 126–135). And the pressure ratios multiply along the chain (l. 156).

> [!warning] Reflection is not mirror-like
> The angle of reflection $\phi$ is smaller than the angle of incidence $\beta_A$, so the reflected shock leans closer to the wall. The cause is that $M_2<M_1$, and on the chart (panel e of the figure) a lower Mach number needs a larger $\beta$ for the same $\theta$. So $\beta_B>\beta_A$, but $\beta_B$ is measured from the tilted $\mathbf V_2$, and $\phi=\beta_B-\theta$ comes out smaller.
>
> In the lecture: *"shock reflection is not like optical reflection. It's not specular"* (L2-3, ll. 172–175). Note that he quotes $\phi=7.5^\circ$ there (ll. 166, 171); the correct value is $27.5^\circ-10^\circ=17.5^\circ$. See [[#Transcript slips (Lectures 2.3 and 2.4)]].

The reflection can be cancelled: if the lower wall turns back by $\theta$ exactly where B lands, B is absorbed and zone 3 stays uniform. This is how wind-tunnel and intake designers stop shocks bouncing down a duct (see the W02 intake, [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.2 Example 2: a supersonic intake at M₁ = 3|W02 §10.2]]).

---

## 2. Mach reflection

### When regular reflection fails (slides 5–6)

Step B needs $\theta\le\theta_{max}(M_2)$. But $M_2<M_1$, so $\theta_{max}(M_2)<\theta_{max}(M_1)$. There is therefore a band of wall angles where the incident shock is attached, $\theta<\theta_{max}(M_1)$, but no attached reflected shock can turn zone 2 back, $\theta>\theta_{max}(M_2)$.

> [!check] The lecturer's chart readings (L2-3, ll. 210–228), checked
> - $\theta_{max}(3)\approx34^\circ$ (l. 215): exact $34.07^\circ$ ✓.
> - $\theta_{max}(3.6)$ is *"larger than 35 degrees"* (l. 217): exact $37.31^\circ$ ✓. So a $35^\circ$ ramp still gives an attached incident shock.
> - *"If M2 is 1.5, the maximum turning angle is going to be about 12 degrees"* (l. 225): exact $12.11^\circ$ ✓.
> - His $M_2=1.5$ was illustrative. The real numbers for $M_1=3.6$, $\theta=35^\circ$ are even more decisive: $\beta_A=56.2^\circ$ and $M_2=1.314$, so $\theta_{max}(M_2)=7.05^\circ$. The zone-2 flow would need a $35^\circ$ turn but can manage only $7^\circ$, so it *"is going to collide with the upper body"* (l. 231). Nature avoids this with a Mach reflection.

![[at_mach_reflection.png|900]]

What forms instead is shown in panel b. The incident shock stops short of the wall at a **triple point** T, and from T a nearly normal **Mach stem** runs down to the wall. The stem is normal where it meets the wall, so it turns the flow by zero and keeps it parallel to the wall. A curved reflected shock also leaves T, and a [[Slip Line]] trails downstream from it. Gas on the wall side of the slip line has been through the strong, near-normal stem and is subsonic with high entropy; gas on the other side has been through two weaker shocks and is still supersonic with less entropy loss. The two streams share pressure and direction but differ in velocity, temperature, density and entropy.

A normal shock *"doesn't deflect the flow. Only slow down the flow"* (L2-3, l. 248), which is why nature uses one here: near the wall the flow can carry on horizontally and the collision never happens, at the cost of going subsonic (l. 255). The reflected branch behaves like part of a bow shock, with a deflection that varies along its length, small near the stem and larger further out (ll. 263–291, *"just like the bow shock case that we looked at yesterday"*). That variation is what lets the two streams match direction along the slip line.

> [!question] Lecture Q&A: must the pressure be equal across a slip line? (L2-3, ll. 299–309)
> *"Yes, it has to be the same. Otherwise, there will be momentum generated normal to the slip line."* A pressure difference would push fluid across the line, which contradicts the line being a streamline. Density and temperature, however, can differ (l. 307).

### The regular-reflection limit, derived

Define $\theta_{RR}(M_1)$ as the largest wall angle for which step B is still possible:

$$
\theta_{RR}:\qquad \theta=\theta_{max}\big(M_2(M_1,\theta)\big).
$$

This is one equation in one unknown. Solve it numerically by scanning $\theta$ and bisecting on the sign of $\theta_{max}(M_2)-\theta$:

| $M_1$ | 1.6 | 2.0 | 2.3 | 3.0 | 3.6 | 5.0 | 10 |
|---|---:|---:|---:|---:|---:|---:|---:|
| $\theta_{RR}$ | $7.6^\circ$ | $12.9^\circ$ | $16.1^\circ$ | $21.5^\circ$ | $24.3^\circ$ | $27.8^\circ$ | $30.9^\circ$ |
| $\theta_{max}(M_1)$ | $14.7^\circ$ | $23.0^\circ$ | $27.4^\circ$ | $34.1^\circ$ | $37.3^\circ$ | $41.1^\circ$ | $44.4^\circ$ |

The lecture example ($M_1=3.6$, $\theta=10^\circ$) is well inside the regular region. [[SESA3029 Example Sheet 1 - Solutions#Q3. Ramp shock reflected from a wall|Example Sheet 1 Q3]] asks for this limit at $M_1=2.3$. The answer is $16.1^\circ$ (sheet: 16°).

This detachment criterion is the classical von Neumann limit for the transition from regular to Mach reflection. Experiments show hysteresis between it and the slightly lower mechanical-equilibrium criterion, which is beyond the module but explains why measured values scatter.

---

## 3. Shock–shock interaction and slip lines

### Set-up (slide 7)

The lower wall turns up by $\theta_A=18^\circ$ and the upper wall turns down by $\theta_B=12^\circ$, with $M_1=3$. The two incident shocks cross. After the crossing, each stream has to be turned again so that both end up parallel to each other at the same pressure. The final direction is not known in advance; call it $\Delta\theta$, measured from the free stream. Turning the two streams by different amounts leaves different entropy on each side, so a slip line separates zones 3A and 3B.

![[at_shock_interaction.png|900]]

### Matching conditions

Across a [[Slip Line]]:

$$
\boxed{p_{3A}=p_{3B}},\qquad\boxed{\text{flow direction}_{3A}=\text{flow direction}_{3B}=\Delta\theta}.
$$

Velocity, temperature, density and entropy may all jump. No mass crosses, so the only force balance across it is the pressure balance.

### Solving it, one step at a time

1. Incident shocks, one per wall:
   - zone 2A: $\theta_A=18^\circ$ gives $M_{2A}=2.100$, $p_{2A}/p_1=3.368$, flow at $+18^\circ$;
   - zone 2B: $\theta_B=12^\circ$ gives $M_{2B}=2.406$, $p_{2B}/p_1=2.340$, flow at $-12^\circ$.
2. Guess $\Delta\theta$. Zone 2A must turn down by $\theta_A-\Delta\theta$ and zone 2B up by $\theta_B+\Delta\theta$. Each is a compression, so each is an oblique shock.
3. Compute $p_{3A}/p_1=(p_{2A}/p_1)(p_{3A}/p_{2A})$ and $p_{3B}/p_1$ in the same way.
4. Adjust $\Delta\theta$ until the two agree (panel b). Raising $\Delta\theta$ weakens 3A and strengthens 3B, so the curves cross exactly once:

| $\Delta\theta$ | $0^\circ$ | $2^\circ$ | $4^\circ$ | $5.83^\circ$ | $8^\circ$ |
|---|---:|---:|---:|---:|---:|
| $p_{3A}/p_1-p_{3B}/p_1$ | $+3.98$ | $+2.59$ | $+1.23$ | $0$ | $-1.46$ |

$$
\boxed{\Delta\theta=5.83^\circ,\qquad p_3/p_1=6.535}
$$

The slide gives $\approx5.85^\circ$. The difference is chart-reading precision.

> [!important] This was last year's exam question (L2-3, ll. 317–390)
> *"If you have the chance to have a look at past exam papers, … this was exactly one of the questions last year. So this is basically your homework."* (ll. 317–319).
> - In the exam it was simplified: zones 2A and 2B were given, and so was the result of the first guess of $\Delta\theta$. You had to make the second guess, compute $p_{3A}$ and $p_{3B}$, then interpolate or extrapolate linearly to equal pressure (ll. 379–382).
> - He calls it *"the best example question to work on, to sum up everything that you have learned last week and this week"* (ll. 389–390).
>
> The two-guess method in numbers: with guesses $\Delta\theta=4^\circ$ (difference $+1.23$) and $8^\circ$ (difference $-1.46$), linear interpolation gives $\Delta\theta=4+4\times1.23/2.69=5.83^\circ$, the same as the full iteration, because the difference is nearly linear in $\Delta\theta$.

On either side of the slip line the flow differs:

| | zone 3A | zone 3B |
|---|---:|---:|
| $M_3$ | 1.650 | 1.674 |
| $T_3/T_1$ | 1.813 | 1.794 |
| $p_{03}/p_{01}$ | 0.814 | 0.844 |

So the slip line is real. It tilts upwards, towards A's original turning, because the stronger incident shock A leaves zone 2A at the higher pressure; to equalise, zone 2A has to be compressed less and zone 2B more.

---

## 4. Entropy across a shock and why shocks compress

Slides 8–10 set a "show it": the entropy change across a normal shock depends only on $M_{n1}$, and its slope vanishes at $M_{n1}=1$. Here is the full derivation.

![[at_entropy_jump.png|900]]

**Step 1. Gibbs relation for a perfect gas** ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Isentropic relations: derivation|W01 §3]]):

$$
s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}.
$$

Divide by $c_v$, using $c_p/c_v=\gamma$ and $R/c_v=\gamma-1$:

$$
\frac{s_2-s_1}{c_v}=\gamma\ln\frac{T_2}{T_1}-(\gamma-1)\ln\frac{p_2}{p_1}.
$$

**Step 2. Eliminate temperature** with the gas law, $T_2/T_1=(p_2/p_1)/(\rho_2/\rho_1)$:

$$
\frac{s_2-s_1}{c_v}=\gamma\ln\frac{p_2}{p_1}-\gamma\ln\frac{\rho_2}{\rho_1}-(\gamma-1)\ln\frac{p_2}{p_1}
=\ln\frac{p_2}{p_1}-\gamma\ln\frac{\rho_2}{\rho_1}.
$$

**Step 3. One variable.** Let $m=M_{n1}^2-1$ (the shock strength), $a=2\gamma/(\gamma+1)$ and $b=(\gamma-1)/(\gamma+1)$. The pressure jump is

$$
\frac{p_2}{p_1}=1+am.
$$

For the density jump, write $(\gamma+1)M^2=(\gamma+1)(1+m)$ and $2+(\gamma-1)M^2=(\gamma+1)+(\gamma-1)m=(\gamma+1)(1+bm)$. Then

$$
\frac{\rho_2}{\rho_1}=\frac{1+m}{1+bm}.
$$

**Step 4.**

$$
f(m)\equiv\frac{s_2-s_1}{c_v}=\ln(1+am)-\gamma\ln(1+m)+\gamma\ln(1+bm).
$$

This depends on $M_{n1}$ only ✓, and $f(0)=0$.

**Step 5. Differentiate.**

$$
f'(m)=\frac{a}{1+am}-\frac{\gamma}{1+m}+\frac{\gamma b}{1+bm}.
$$

At $m=0$: $a-\gamma+\gamma b=\dfrac{2\gamma-\gamma(\gamma+1)+\gamma(\gamma-1)}{\gamma+1}=0$, so the first derivative vanishes at $M_{n1}=1$.

**Step 6. Common denominator.** Write $1+am=P/(\gamma+1)$ with $P=\gamma+1+2\gamma m$, and $1+bm=Q/(\gamma+1)$ with $Q=\gamma+1+(\gamma-1)m$. Then

$$
f'(m)=\gamma\,\frac{2(1+m)Q+(\gamma-1)(1+m)P-PQ}{(1+m)PQ}.
$$

Expand the numerator term by term:

$$
2(1+m)Q=2(\gamma-1)m^2+4\gamma m+2(\gamma+1),
$$

$$
(\gamma-1)(1+m)P=2\gamma(\gamma-1)m^2+(3\gamma^2-2\gamma-1)m+(\gamma^2-1),
$$

$$
PQ=2\gamma(\gamma-1)m^2+(3\gamma^2+2\gamma-1)m+(\gamma+1)^2.
$$

Add the first two lines and subtract the third:

- the $m$ terms give $4\gamma+3\gamma^2-2\gamma-1-3\gamma^2-2\gamma+1=0$;
- the constants give $2\gamma+2+\gamma^2-1-\gamma^2-2\gamma-1=0$;
- only $2(\gamma-1)m^2$ survives.

$$
\boxed{f'(m)=\frac{2\gamma(\gamma-1)\,m^2}{(1+m)\,[\gamma+1+2\gamma m]\,[\gamma+1+(\gamma-1)m]}\ \ge0}
$$

**Step 7. Consequences.**

- $\mathrm ds/\mathrm dM_{n1}=f'(m)\cdot2M_{n1}=0$ at $M_{n1}=1$. This is the slide's "show it" ✓.
- $f'>0$ for every $m\ne0$, so $f$ is increasing. With $f(0)=0$ this gives $f>0$ for $M_{n1}>1$ and $f<0$ for $M_{n1}<1$. A shock with $M_{n1}<1$ would be an expansion shock that destroys entropy in an adiabatic process, which the second law forbids, so shocks are always compressive.
- Near $m=0$, $f'\approx2\gamma(\gamma-1)m^2/(\gamma+1)^2$. Integrate from 0:

$$
\boxed{\frac{s_2-s_1}{c_v}\approx\frac{2\gamma(\gamma-1)}{3(\gamma+1)^2}\left(M_{n1}^2-1\right)^3}.
$$

So weak shocks are nearly isentropic: halve the strength and the loss falls eightfold.

> [!check] Numbers ($\gamma=1.4$, $c_v=717.5$ J/kg K)
>
> | $M_{n1}$ | exact $(s_2-s_1)/c_v$ | cubic estimate | $s_2-s_1$ |
> |---:|---:|---:|---:|
> | 1.05 | $5.9\times10^{-5}$ | $7.0\times10^{-5}$ | 0.04 J/kg K |
> | 1.2 | 0.00289 | 0.00552 | 2.1 J/kg K |
> | 2 | 0.1309 | (cubic invalid) | 94 J/kg K |
>
> Cross-check with $p_{02}/p_{01}=e^{-\Delta s/R}$ at $M=2$: $e^{-93.9/287}=0.7209$, the table value ✓.

> [!important] The lecture's three "fake news" tests (L2-3, ll. 416–447)
> 1. A "shock" with upstream normal Mach number below 1: *"that's a fake news, that doesn't happen"* (ll. 419–421), because $s_2<s_1$.
> 2. A "shock" after which the pressure has dropped (his example: 90 Pa after, 100 Pa before) is fake too. A shock is always a compression wave (ll. 432–435).
> 3. Near $M_{n1}=1$ the entropy rise is almost zero, so Mach-wave processes may be treated as isentropic even in supersonic flow (ll. 424–442). This is what makes the expansion fan of §5 isentropic. The "$M<0.3$" rule for isentropic flow from earlier modules is not the relevant test here.
>
> Because a shock is irreversible, $p_0$ falls across it, and relations derived for isentropic flow (such as $p_0/p$ from Bernoulli-type arguments) cannot be applied across it (ll. 443–447).

This result gets used a lot. It is why intakes split their compression into several weak shocks ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.2 Example 2: a supersonic intake at M₁ = 3|W02 §10.2]]), why an expansion has to be a fan rather than a shock, and why Mach waves can be treated as isentropic, which §5 and the method of characteristics depend on.

---

## 5. Expansion waves and the Prandtl–Meyer function

### Physical picture (Lecture 2.4, slides 1–2)

At a convex corner of angle $\theta$ the wall turns away from the flow. The first Mach wave sits at $\mu_1$ to the incoming flow. Each further bit of turning accelerates the flow, so $M$ rises and $\mu$ falls, and each wave is also measured from a flow direction that has already turned down. The waves therefore fan out from the corner and never coalesce, the opposite of a concave corner where they converge into a shock. The result is a centred [[Expansion Fan]]: continuous and isentropic, with $p_0$ and $T_0$ constant.

![[at_expansion_fan.png|900]]

In panel (a) the rays and streamlines are computed, not sketched. Along each ray $M$ is constant. Each streamline bends smoothly through the fan and leaves parallel to the downstream wall.

The lecturer explains the same thing with a duct (L2-4, ll. 16–34). Draw a streamline well above the wall; it stays roughly horizontal while the streamline on the wall turns away, so the two form a diverging duct. A supersonic flow in a diverging duct accelerates and its pressure falls (SESA2023 propulsion), and that is the expansion fan. At a concave corner the streamlines form a converging duct instead, the supersonic flow has to slow down and its pressure rise, and the oblique shock is how it does that. See [[Converging-Diverging Nozzle Operating Regimes]].

### Deriving the Prandtl–Meyer function (slides 3–6)

![[at_prandtl_meyer_function.png|900]]

**Kinematics across one Mach wave.** Turn the flow by an infinitesimal $\mathrm d\nu$ across a Mach wave inclined at $\mu$ to the upstream velocity $U$. Pressure acts normal to the wave, so the tangential velocity is unchanged, as for an oblique shock. Downstream, the speed is $U+\mathrm dU$ and the angle to the wave is $\mu+\mathrm d\nu$:

$$
U\cos\mu=(U+\mathrm dU)\cos(\mu+\mathrm d\nu).
$$

Expand the cosine:

$$
U\cos\mu=(U+\mathrm dU)\left(\cos\mu\cos\mathrm d\nu-\sin\mu\sin\mathrm d\nu\right).
$$

For infinitesimal $\mathrm d\nu$, use $\cos\mathrm d\nu\to1$ and $\sin\mathrm d\nu\to\mathrm d\nu$:

$$
U\cos\mu=U\cos\mu+\mathrm dU\cos\mu-U\,\mathrm d\nu\sin\mu-\mathrm dU\,\mathrm d\nu\sin\mu.
$$

> [!question] Lecture Q&A: why say $\mathrm d\nu\to0$ but not set it to zero? (L2-4, ll. 144–175)
> We look at one of infinitely many Mach waves, across which the change is infinitesimal. So $\mathrm d\nu$ is small enough to use $\cos\mathrm d\nu\to1$, $\sin\mathrm d\nu\to\mathrm d\nu$ and to drop products of differentials, but it is not zero: *"if you set it to 0, then there's no progress at all"* (l. 153). Integrating $\mathrm d\nu$ across the whole fan gives the finite turn, *"like a calculus"* (ll. 172–174).

Cancel $U\cos\mu$ and drop the second-order product $\mathrm dU\,\mathrm d\nu$:

$$
0=\mathrm dU\cos\mu-U\,\mathrm d\nu\sin\mu
\quad\Longrightarrow\quad
\mathrm d\nu=\frac{1}{\tan\mu}\,\frac{\mathrm dU}{U}.
$$

From $\sin\mu=1/M$, a right triangle with hypotenuse $M$, opposite side 1 and adjacent side $\sqrt{M^2-1}$ gives $\tan\mu=1/\sqrt{M^2-1}$. So

$$
\boxed{\mathrm d\nu=\sqrt{M^2-1}\,\frac{\mathrm dU}{U}}.
$$

**Thermodynamics: change variable from $U$ to $M$.** Take logarithms of $U=Ma$ and differentiate:

$$
\frac{\mathrm dU}{U}=\frac{\mathrm dM}{M}+\frac{\mathrm da}{a}.
$$

The flow is adiabatic, so $T_0$ is constant and $a=a_0X^{-1/2}$ with $X=1+\tfrac{\gamma-1}{2}M^2$. Then

$$
\frac{\mathrm da}{a}=-\frac12\frac{\mathrm dX}{X}=-\frac{\frac{\gamma-1}{2}M\,\mathrm dM}{X}.
$$

Substitute:

$$
\frac{\mathrm dU}{U}=\frac{\mathrm dM}{M}\left[1-\frac{\frac{\gamma-1}{2}M^2}{X}\right]=\frac{1}{X}\,\frac{\mathrm dM}{M}.
$$

Hence

$$
\mathrm d\nu=\frac{\sqrt{M^2-1}}{1+\frac{\gamma-1}{2}M^2}\,\frac{\mathrm dM}{M}.
$$

**Integrate from $M=1$, where $\nu=0$ by definition.**

1. Substitute $t=\sqrt{M^2-1}$. Then $M^2=1+t^2$ and $M\,\mathrm dM=t\,\mathrm dt$, so $\mathrm dM/M=t\,\mathrm dt/(1+t^2)$.
2. The denominator becomes $1+\tfrac{\gamma-1}{2}(1+t^2)=\tfrac{\gamma+1}{2}\left(1+kt^2\right)$ with $k=\dfrac{\gamma-1}{\gamma+1}$.
3. The integrand is now $\dfrac{2}{\gamma+1}\,\dfrac{t^2}{(1+t^2)(1+kt^2)}\,\mathrm dt$.
4. Partial fractions: $\dfrac{t^2}{(1+t^2)(1+kt^2)}=\dfrac{1}{1-k}\left[\dfrac{1}{1+kt^2}-\dfrac{1}{1+t^2}\right]$. Check by recombining: the numerator is $(1+t^2)-(1+kt^2)=(1-k)t^2$ ✓.
5. The prefactor collapses: $1-k=\dfrac{2}{\gamma+1}$, so $\dfrac{2}{\gamma+1}\cdot\dfrac{1}{1-k}=1$.
6. Standard integrals: $\int\dfrac{\mathrm dt}{1+kt^2}=\dfrac{1}{\sqrt k}\tan^{-1}(\sqrt k\,t)$ and $\int\dfrac{\mathrm dt}{1+t^2}=\tan^{-1}t$. Both vanish at $t=0$.

$$
\boxed{\nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\,\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}\left(M^2-1\right)}-\tan^{-1}\sqrt{M^2-1}}
$$

This is the $\nu$ column of the isentropic-flow table (IFT). Check: $\nu(2)=26.38^\circ$ and $\nu(3)=49.76^\circ$; a numerical quadrature of the integral gives the same to four decimals ✓.

**Maximum turning.** As $M\to\infty$ both inverse tangents tend to $\pi/2$:

$$
\nu_{max}=\frac{\pi}{2}\left(\sqrt{\frac{\gamma+1}{\gamma-1}}-1\right)=130.45^\circ\quad(\gamma=1.4).
$$

A sonic stream can be turned at most $130.45^\circ$ before it expands to vacuum ($p\to0$). Beyond that, a void forms between the flow and the wall.

### Using it (slides 7–8)

$\nu(M)$ is the angle a sonic stream would have to be turned to reach $M$. A further turn of $\theta$ simply adds:

$$
\boxed{\nu(M_2)=\nu(M_1)+\theta}
$$

The recipe:

1. Read $\nu(M_1)$ from the IFT.
2. Add $\theta$.
3. Find $M_2$ by interpolation or by inverting numerically.
4. Get $p$, $T$ and $\rho$ from the isentropic ratios, since $p_0$ and $T_0$ are constant.

The forward Mach line of the fan sits at $\mu_1$ to the incoming flow, and the rearward one at $\mu_2$ to the turned flow, which is $\mu_2-\theta$ to the original direction. So the fan angle is

$$
\phi=\mu_1-(\mu_2-\theta)=\mu_1-\mu_2+\theta.
$$

### Worked example (slides 9–11): M₁ = 3, θ = 13°

1. IFT: $\nu(3)=49.757^\circ$, so $\nu_2=49.757^\circ+13^\circ=62.757^\circ$.
2. IFT rows: $\nu(3.76)=62.471^\circ$ and $\nu(3.78)=62.758^\circ$. So $M_2=3.78$ (exact: 3.7799).
3. Pressure, through the isentropic ratios:

$$
\frac{p_2}{p_1}=\frac{(p/p_0)_{3.78}}{(p/p_0)_{3}}=\frac{0.0089}{0.0272}=0.327\quad(\text{exact }0.3258).
$$

The pressure drops by 67.4%.

4. Temperature and density: $T_2/T_1=\dfrac{1+0.2\times9}{1+0.2\times3.78^2}=0.7258$ and $\rho_2/\rho_1=0.7258^{2.5}=0.4489$.
5. Fan: $\mu_1=19.47^\circ$ and $\mu_2=15.34^\circ$, so $\phi=19.47^\circ-15.34^\circ+13^\circ=17.13^\circ$.

> [!warning] Table precision
> Four-figure $p/p_0$ entries near 0.009 carry only two significant figures. That is why the table route gives 67.3% and the exact result 67.4%. If the question allows it, use the formula for $p/p_0$.

In the lecture Jae uses the nearest table row, $M_2=3.78$, and gets a 67.3% drop (l. 442), noting that interpolation or the exact equation would be more precise (l. 435). His point is how much a small turn does at high Mach number: *"The flow turned only 13 degrees … and the pressure dropped by 67.3%"* (ll. 444–445), so 1 bar becomes about 0.33 bar. He also stresses that the fan angle, $17.2^\circ$, is not the deflection angle (ll. 448–449, and earlier ll. 67–68), and that the IFT's $\nu$ column is blank below $M=1$ and starts at $\nu=0$ at $M=1$ (ll. 328–348).

Run the same construction on a smooth concave wall and the Mach waves converge instead, coalescing into a shock some distance from the wall. Close to the wall the compression is isentropic and follows the same $\nu$ relation with the sign of $\theta$ reversed. This is the Concorde intake idea from [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.2 Example 2: a supersonic intake at M₁ = 3|W02 §10.2]].

---

## 6. The shock-expansion method

> [!info] Lecture 2.5 (`L2-5`, last year's recording of the same deck)
> Recap of Prandtl–Meyer (ll. 1–14); which surface gets which wave (ll. 15–28); the upper surface (ll. 31–61); the lower surface (ll. 61–86); forces and moment (ll. 87–117); coefficients (ll. 118–137); discussion of the nose-down moment, drag, leading-edge suction and wave drag (ll. 138–213, 258–261); centre of pressure and aerodynamic centre (ll. 215–257). Trailing-edge waves were sketched but not solved: *"today's lecture is just focusing on the airfoil forces"* (l. 28).

### The rule (Lecture 2.5, slides 2–6)

For a two-dimensional body made of flat faces in supersonic flow:

1. At each compression corner (flow turned into itself) put an oblique shock, using the $\theta$–$\beta$–$M$ relation and the jump relations.
2. At each expansion corner put a Prandtl–Meyer fan, using $\nu$ and the isentropic relations.
3. Between corners the flow is uniform, so each face carries one constant pressure.
4. Integrate the pressures for the force and moment.

To see which side gets which wave (L2-5, ll. 15–27), draw a straight streamline far above the plate and one far below. Above, the channel between the far streamline and the surface widens downstream; a supersonic flow in a widening channel accelerates and its pressure drops, so an expansion fan sits at the upper leading edge. Below, the channel narrows, so the flow is compressed through an oblique shock. At the trailing edge the roles swap: the low-pressure upper stream must be compressed back towards $p_1$ (a shock) and the high-pressure lower stream expanded (a fan). The final direction is fixed by the slip line (ll. 24–27). This is the duct analogy of Lecture 2.4 (L2-4, ll. 16–34) applied to a body.

As long as no wave reflected from elsewhere lands back on the body, this is exact within inviscid theory, not linearised. It gives the wave drag that subsonic inviscid flow (d'Alembert) cannot.

### Flat plate at incidence, step by step (slides 7–13): M₁ = 2, α = 10°, p₁ = 30 kPa, c = 1 m

![[at_shock_expansion_plate.png|900]]

**Upper surface: expansion through α.**

$$
\nu(2)=26.38^\circ
\ \Rightarrow\
\nu(M_{2U})=36.38^\circ
\ \Rightarrow\
M_{2U}=2.385
$$

The IFT rows 2.38 ($\nu=36.26^\circ$) and 2.40 ($\nu=36.75^\circ$) bracket this $\nu$. The lecture interpolates (L2-5, ll. 40–53) by setting the two ratios equal:

$$
\frac{M_{2U}-M_A}{M_B-M_A}=\frac{\nu_{target}-\nu_A}{\nu_B-\nu_A}=\frac{36.38-36.26}{36.75-36.26}=0.245,
$$

$$
M_{2U}=2.38+0.245\times0.02=2.385.
$$

The same fraction applied to the $p/p_0$ column gives $0.07004$ (lecture: 0.07006, l. 54).

$$
\frac{p_{2U}}{p_1}=\frac{(p/p_0)_{2.385}}{(p/p_0)_2}=\frac{0.0700}{0.1278}=0.548
\ \Rightarrow\
p_{2U}=16.44\ \text{kPa}\quad(\text{slide and L2-5 l. 57: }16.45).
$$

*"Very strong expansion has occurred"*: the upper pressure is about half the free stream (ll. 59–61). *"I strongly recommend you to do these calculation[s] yourself"* (l. 57).

**Lower surface: compression through α.** The chart gives *"around 39 degrees but not precisely"* (L2-5, ll. 63–67). The lecture then brackets the root with two trial angles in the exact $\theta$–$\beta$–$M$ relation (ll. 68–74):

$$
\theta(\beta=39^\circ)=9.710^\circ,\qquad\theta(\beta=40^\circ)=10.623^\circ,
$$

$$
\beta=39^\circ+1^\circ\times\frac{10-9.710}{10.623-9.710}=39.318^\circ\quad(\text{exact root }39.314^\circ).
$$

Then the normal-shock unit (ll. 75–86):

$$
\beta=39.31^\circ,
\qquad
M_{n1}=2\sin39.31^\circ=1.267,
\qquad
M_{n2}=0.8032,
\qquad
M_{2L}=1.640,
$$

$$
\frac{p_{2L}}{p_1}=1.7066\ \Rightarrow\ p_{2L}=51.20\ \text{kPa}.
$$

**Forces (L2-5, ll. 87–117).** The plate is frictionless, so there is no tangential force; the net force per unit span is normal to the plate, of size $\Delta p\,c$ with $\Delta p=p_{2L}-p_{2U}$, and acts at **mid-chord** (ll. 94–102).

$$
F_n'=(p_{2L}-p_{2U})\,c=34.76\ \text{kN/m}.
$$

Resolve perpendicular and parallel to the free stream:

$$
L'=F_n'\cos\alpha=34.23\ \text{kN/m},
\qquad
D'=F_n'\sin\alpha=6.04\ \text{kN/m}.
$$

**Moment about the leading edge (ll. 106–117).** Nose-up is positive. A strip $\mathrm dx$ at distance $x$ from the LE carries a net upward force $\Delta p\,\mathrm dx$, which pitches the nose down. So its moment is $-\Delta p\,x\,\mathrm dx$ (*"the force component here has to be $p_{2U}-p_{2L}$, which is negative of $\Delta p$"*, l. 114):

$$
M'_{LE}=-\int_0^c\Delta p\,x\,\mathrm dx=-\Delta p\,\frac{c^2}{2}.
$$

**Coefficients.** The dynamic pressure is rewritten in terms of $p$ and $M$, which the problem gives (ll. 118–125):

$$
\rho U^2=\rho M^2a^2,
$$

$$
\rho U^2=\rho M^2\gamma RT\quad(a^2=\gamma RT),
$$

$$
\rho U^2=\gamma pM^2\quad(p=\rho RT),
$$

$$
q_\infty=\tfrac12\gamma p_1M_1^2=\tfrac12\times1.4\times30\times2^2=84\ \text{kPa}.
$$

$$
C_l=\frac{\Delta p\cos\alpha}{q_\infty}=0.4075,
\qquad
C_d=\frac{\Delta p\sin\alpha}{q_\infty}=0.0719,
$$

$$
C_{m,LE}=-\frac{F_n'\,(c/2)}{q_\infty c^2}=-\frac{\Delta p}{2q_\infty}=-0.2069
\quad(\text{nose-down}).
$$

$L/D=\cot\alpha=5.67$ exactly: an inviscid flat plate's force is normal to it. The lecture rounds these to $C_l\approx0.4$, $C_d\approx0.07$, $C_{m,LE}\approx-0.2$ (l. 137).

> [!warning] "Nose-down, so it's stable"? (L2-5, ll. 138–148)
> The lecture reads $C_{m,LE}<0$ as *"a kind of stable one… a favourable situation"*. Be careful with this in an exam. The sign of the moment about the leading edge only says that a free plate pitches nose-down, so a tail is needed to trim it (the lecture's next point, ll. 146–149). Static stability is about the slope, $\mathrm dC_{m,cg}/\mathrm d\alpha<0$, which holds when the centre of gravity is ahead of the aerodynamic centre. That is the margin that the ac shift below threatens.

> [!question] Lecture Q&A: why is there drag here but none in subsonic thin-aerofoil theory? (L2-5, ll. 149–213)
> The force on an inviscid flat plate is normal to it, so it always has a downstream component $N\sin\alpha$. In subsonic theory that component is cancelled by leading-edge suction. The stagnation point sits on the lower surface, and the flow wraps $180^\circ$ round the sharp edge (ll. 186–192). There $\Delta p\to\infty$ (the $1/\sqrt{x}$ singularity), and *"infinite multiply by zero"* thickness leaves a finite forward suction force (ll. 194–206). The result is pure lift, zero drag: d'Alembert's paradox. In supersonic flow the leading edge is where the flow splits cleanly into a shock below and a fan above. Nothing wraps round, so there is no suction and the full $N\sin\alpha$ survives as drag (ll. 208–213). This is wave drag (ll. 258–261).

**Centre of pressure and aerodynamic centre (L2-5, ll. 215–242).** Move the moment reference from the LE to a point $x$ on the chord.

*The lecture's version.* The lift acts upward, so its moment about $x$ changes by $+x\,L'$ (l. 222):

$$
C_{m,x}=C_{m,LE}+\frac{x}{c}\,C_l\quad(\text{lecture}).
$$

The centre of pressure is where $C_{m,x}=0$, so $x_{cp}/c=-C_{m,LE}/C_l$. The aerodynamic centre is where $C_{m,x}$ doesn't change with $C_l$; setting $\mathrm dC_{m,x}/\mathrm dC_l=0$ gives $x_{ac}/c=-\mathrm dC_{m,LE}/\mathrm dC_l$.

For the plate, $C_l=\Delta p\cos\alpha/q_\infty$ gives $\Delta p/q_\infty=C_l/\cos\alpha$ (l. 233). Then:

$$
C_{m,LE}=-\frac{\Delta p}{2q_\infty}=-\frac{C_l}{2\cos\alpha},
$$

$$
\frac{x_{cp}}{c}=-\frac{C_{m,LE}}{C_l}=\frac{1}{2\cos\alpha}=0.5077\quad(\alpha=10^\circ,\ \text{lecture}).
$$

The slide also sets $x_{ac}/c=1/(2\cos\alpha)$, by treating $C_{m,LE}$ as proportional to $C_l$. It is not quite: the factor $1/(2\cos\alpha)$ itself changes with $\alpha$.

*The exact version.* Moving the reference along the chord is a shift parallel to the chordwise force, so only the chord-normal force $F_n'$ changes the moment ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#2. Aerodynamic review and the low-speed baseline|W01 §2]]):

$$
C_{m,x}=C_{m,LE}+\frac{x}{c}\,C_n.
$$

For the plate, the uniform pressures give $C_n=\Delta p/q_\infty$, so

$$
C_{m,LE}=-\frac{\Delta p}{2q_\infty}=-\frac{C_n}{2}\quad\text{exactly, at every }\alpha.
$$

Hence

$$
\frac{x_{cp}}{c}=-\frac{C_{m,LE}}{C_n}=\frac12,
\qquad
\frac{x_{ac}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_n}=\frac12.
$$

They coincide because $C_{m,LE}$ is exactly proportional to $C_n$, with a constant factor: a flat plate has no zero-lift moment.

> [!check] Lift-based vs chord-based, computed (shock-expansion, $M_1=2$)
> | | $9^\circ$ | $10^\circ$ | $11^\circ$ |
> |---|---|---|---|
> | $C_n$ | 0.3705 | 0.4138 | 0.4578 |
> | $C_l$ | 0.3660 | 0.4075 | 0.4494 |
> | $C_{m,LE}$ | −0.1853 | −0.2069 | −0.2289 |
>
> Chord-based: $-C_{m,LE}/C_n=0.5000$ at every angle, and $-\Delta C_m/\Delta C_n=0.5000$. Lift-based: $-C_{m,LE}/C_l=0.5077$ at $10^\circ$, but the central difference $-\Delta C_m/\Delta C_l$ over $9^\circ\to11^\circ$ is 0.523, not 0.5077. So the lecture's "$x_{ac}=1/(2\cos\alpha)$" is off by a further 3% beyond the $\cos\alpha$ factor. Exam advice: quote the lecture's numbers if asked for them, then add "measured along the chord, both are exactly $c/2$".

> [!important] The ac jumps from c/4 to c/2 (L2-5, ll. 243–257)
> Subsonic aerofoils have their aerodynamic centre near the quarter chord, supersonic ones near half chord. A supersonic aircraft is designed with a positive static margin about the half-chord ac. It must still take off and land subsonically, and then the ac moves forward to the quarter chord. *"Can you guarantee that the cg margin is still positive? Maybe not"* (ll. 256–257). The aircraft can be stable in cruise and unstable at landing, or the reverse. This is a key design issue for any transonic or supersonic aircraft. (Extension: Concorde pumped fuel aft for supersonic cruise and forward again for landing, to move the cg with the ac.)

> [!warning] Centre of pressure on slide 16
> The slide writes $x_{cp}/c=-C_{m,LE}/C_l=1/(2\cos\alpha)=0.5077$. That formula attributes the whole moment to the lift, ignoring the drag's moment arm, so it gives where $L'$ alone would have to act along the free-stream direction. Measured along the chord, the centre of pressure is exactly mid-chord, $x_{cp}/c=-C_{m,LE}/C_n=0.5$ (derived above), because both surface pressures are uniform (see [[Aerodynamic Centre and Centre of Pressure]]). Quote 0.5 with "along the chord".

**Trailing edge.** The two streams leave at $-\alpha$ with different pressures (16.4 and 51.2 kPa) and have to end up parallel at a common pressure across a [[Slip Line]], as in §3. The upper flow turns up through a shock and the lower flow through a fan. Solving for the slip-line angle gives $\delta=0.03^\circ$ and $p_3=30.03$ kPa, essentially the free stream; what's left over is the small entropy difference. None of this changes the surface pressures, because nothing travels upstream in supersonic flow.

![[at_flat_plate_coefficients.png|900]]

> [!check] Against linear (Ackeret) theory, Weeks 7–8
> Ackeret gives $C_l=4\alpha/\sqrt{M^2-1}=0.4031$ and $C_d=4\alpha^2/\sqrt{M^2-1}=0.0703$ at $10^\circ$, 1–2% below shock-expansion. At $2^\circ$ the two agree to four figures. The linear theory is the small-angle limit of this exact method; compare [[SESA3029 Example Sheet 2 - Solutions#Q4. Flat plate by Ackeret theory|Example Sheet 2 Q4]] with [[SESA3029 Example Sheet 1 - Solutions#Q4. Flat plate by shock-expansion theory|Example Sheet 1 Q4]].

### Diamond aerofoil

A symmetric diamond of thickness ratio $t/c$ has half-angle $\varepsilon=\tan^{-1}(t/c)$. At incidence $\alpha$:

| Face | Turn at its leading corner |
|---|---|
| upper front | $\varepsilon-\alpha$ (a shock if $>0$, nothing if $=0$, a fan if $<0$) |
| upper rear | expansion by $2\varepsilon$ at the shoulder |
| lower front | compression by $\varepsilon+\alpha$ |
| lower rear | expansion by $2\varepsilon$ |

Each face's pressure acts normal to that face, so thickness gives drag even at zero lift. The full worked case ($M=1.8$, $t/c=0.05$, $\alpha=2^\circ$) and the wave sketches for $\alpha=5^\circ$ and $\pm2.86^\circ$ are in [[SESA3029 Example Sheet 1 - Solutions#Q6. Diamond aerofoil by shock-expansion theory|Example Sheet 1 Q6–Q7]].

---

## Transcript slips (Lectures 2.3 and 2.4)

> [!warning] Slips in the recordings
> The slides and the method are right in every case; these are spoken or transcription slips.
>
> | Where | Said | Correct |
> |---|---|---|
> | L2-3, ll. 115, 120, 125 | "$M_{n2}$ is 2.98" | $M_2=2.98$. The normal component is $M_{n2}=0.716$; 2.98 is the full Mach number. |
> | L2-3, ll. 133–135 | "about 27.08 ish … so $\beta_B$ is 27.5" | $\beta_B=27.51^\circ$ (exact); the 27.08 was a misread. |
> | L2-3, l. 152 | "$M_{n3}$ is $M_{n3}$ divided by $\sin(\beta_B-\theta)$" | $M_3=M_{n3}/\sin(\beta_B-\theta)$ |
> | L2-3, l. 154 | "Beta is 10" | $\theta=10^\circ$ |
> | L2-3, l. 160 | $p_3=189$ kPa | 189.6 kPa (rounding only) |
> | L2-3, ll. 166, 171 | reflected-shock angle "7.5 degrees" | $\phi=27.5^\circ-10^\circ=$ **17.5°**. The point he makes (that $\phi\neq\beta_A=23.9^\circ$) still holds. |
> | L2-3, ll. 404, 412 | "$T_2$ divided by $P_1$", "$p_2$ over $t_1$" | $T_2/T_1$ in both places |
> | L2-3, l. 445 | "the funerally equation" | an automatic-transcription error; he means the isentropic (Bernoulli-type) relations |
> | L2-4, l. 1 | "the fourth quiz has been released" | **Test 1** (l. 2) |
> | L2-4, l. 64 | fan angle "$\mu_1$ minus $\mu_2$ minus $\theta$" | $\phi=\mu_1-(\mu_2-\theta)=\mu_1-\mu_2+\theta$, as he says correctly at l. 448 |
> | L2-4, l. 116 | "cos mu is going to be replaced by 1" | $\cos\mathrm d\nu\to1$ (not $\cos\mu$) |
> | L2-4, ll. 216–217 | (self-corrected) a missing $\tfrac12$ in the $\mathrm da$ step | $\mathrm da=-\tfrac12a_0X^{-3/2}(\gamma-1)M\,\mathrm dM$; see §5 |
> | L2-4, l. 431 | $p_2/p_0=$ "0.089" | 0.0089 (he uses 0.0089 at l. 442) |
> | L2-4, l. 446 | "0.34 bar … 3.3 bar" | 0.33 bar |

## Transcript slips (Lecture 2.5)

> [!warning] Slips in `Lecture 2-5 (2025-26 version).txt`
> The method and the final numbers are right; these are spoken or transcription slips.
>
> | Where | Said | Correct |
> |---|---|---|
> | L2-5, ll. 3–4 | "the plantar mayor expansion fan we did on Tuesday" | Prandtl–Meyer; "Tuesday" is last year's timetable (this year Lecture 2.4 was Mon 5 Oct) |
> | L2-5, l. 13 | "mu3 is the Mach angle of the last Mach wave" | $\mu_2$ |
> | L2-5, l. 29 | "M1 is M2" | $M_1=2$ |
> | L2-5, l. 35 | $\nu(2)$ = "24.3798 degrees" | **26.3798°**; he uses 26.38 at l. 37 |
> | L2-5, l. 83 | "I think it's a wrong figure that is added here" | a slide figure; the jump he then uses, $p_2/p_1$ at $M_{n1}$, is correct |
> | L2-5, l. 116 | "integrating from 0 to 3 code length" | from 0 to $c$ |
> | L2-5, l. 122 | "a squared is gamma r t squared" | $a^2=\gamma RT$ |
> | L2-5, l. 130 | $C_{m,LE}$ = "minus delta p over half q infinity" | $-\Delta p/(2q_\infty)$; "over half $q$" would be $-2\Delta p/q_\infty$, four times too big |
> | L2-5, l. 184 | "dallangbel dilemma" | d'Alembert's paradox |
> | L2-5, l. 190 | "turn around 360 degrees" | 180° (self-corrected) |
> | L2-5, ll. 225, 238 | "x cp over c is cmle over cl" | $-C_{m,LE}/C_l$; he adds the minus at l. 234 |
> | L2-5, l. 240 | "minus dcm by dcm by dcl" | $-\mathrm dC_{m,LE}/\mathrm dC_l$ |

## 7. Problem-solving workflow

1. Sketch every corner and mark whether the flow turns into itself (shock) or away (fan), measuring each turn from the local upstream flow direction.
2. At a shock, check $\theta<\theta_{max}(M)$, find the weak $\beta$, take the jumps at $M_n=M\sin\beta$, then $M_{down}=M_{n,down}/\sin(\beta-\theta)$.
3. At a fan, $\nu_{down}=\nu_{up}+\theta$ gives $M_{down}$, and the isentropic ratios with $p_0$ unchanged give the rest.
4. At a wall reflection, apply the same $\theta$ again from the new $M$. If $\theta>\theta_{max}$, expect a Mach reflection.
5. At an interaction or a trailing edge, guess the slip-line angle and iterate until the pressures match. Expect $T$ and $M$ to jump across it.
6. For forces, take $p\times$ face length normal to each face, then resolve into $L$ and $D$, with moments about the leading edge using each face's midpoint. $D=N\sin\alpha$ only holds for a flat plate; on a thick section the faces also push along the chord (see [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Forces: the chordwise term the shortcut misses|Tutorial 1]]).

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] · Next: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- Concepts: [[Regular Shock Reflection]] · [[Mach Reflection]] · [[Slip Line]] · [[Entropy Change Across a Shock]] · [[Prandtl-Meyer Function]] · [[Expansion Fan]] · [[Shock-Expansion Theory]]
- Worked sheet: [[SESA3029 Example Sheet 1 - Solutions]] (Q3, Q4, Q6, Q7)
- Tutorial: [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing]] (ES1 Q3 and a triangular wing, Fri 9 Oct)
- Formulae: [[SESA3029 Formula Sheet]]
- Other modules: [[SESA3043 2.1 - Complex Functions and Conformal Mapping|SESA3043 2.1]] and [[SESA3043 2.2 - Lumped Vortex Method|2.2]] compute the low-speed loads that the shock-expansion method replaces at $M>1$. The subsonic flat plate in [[SESA3043 2.2 - Lumped Vortex Method#1. Thin-aerofoil review (slides 25–27; revision 2.2 Q1)|SESA3043 2.2 §1]] has $C_l=2\pi\alpha=1.097$ at $\alpha=10^\circ$, no drag and its aerodynamic centre at $c/4$; the supersonic plate of §6 at $M_1=2$ gives $C_l=0.4075$, wave drag $C_d=0.0719$ and a centre of pressure near $c/2$.

## Sources

- `Lecture2-3.pdf`: 2.3 Shock Reflections & Interactions (10 slides); transcript `Lecture 2-3.txt` (Fri 2 Oct, 447 lines)
- `Lecture2-4.pdf`: 2.4 Expansion Waves (12 slides); transcript `Lecture 2-4.txt` (Mon 5 Oct, 463 lines)
- `Lecture2-5.pdf`: 2.5 Shock-Expansion Method (17 slides); lectured Thu 8 Oct. Transcript: last year's recording, `Lecture 2-5 (2025-26 version).txt` (263 lines)
- Exam data sheets used in lectures: `IFT.pdf` (isentropic-flow table with $\nu$), `NST.pdf` (normal-shock table), `OSC.pdf` (oblique-shock chart, $M_1\le3$), `Aerothermodynamics Formula Sheet.pdf`. See [[SESA3029 Formula Sheet#What the exam formula sheet gives you]].
- Anderson, *Fundamentals of Aerodynamics*, §§9.3–9.7 (reflections, Prandtl–Meyer expansion, shock-expansion theory)
- Figures: `generate_aerothermo_w03_figures.py`

## Self-study tasks

Each task cites where it was set: a transcript line, or the slide for slide-set tasks. Anything else is marked as suggested, not lecturer-set. Lecture 2.5 line references are to last year's recording (`L2-5`). Try each one closed-book, then check against the linked section.

### Core

- [ ] Solve the θ–β–M equation numerically for $M_1=3.6$, $\theta=10^\circ$ and *"confirm that"* $\beta_A=23.9^\circ$ (L2-3, ll. 74–76). → [[#Worked example (slides 2–4): M₁ = 3.6, θ = 10°, p₁ = 40 kPa|§1]]
- [ ] Last year's exam question (L2-3, ll. 317–319, 388–390): the double shock interaction at $M_1=3$ with $18^\circ$ and $12^\circ$ walls. Find the slip-line angle by two guesses and interpolation: $\Delta\theta=5.83^\circ$ (lecture: 5.85°). → [[#3. Shock–shock interaction and slip lines|§3]]
- [ ] *"I strongly recommend you to do these calculation[s] yourself"* (L2-5, l. 57): the flat plate at $M_1=2$, $\alpha=10^\circ$, both surfaces, by table interpolation. Target $C_l=0.4075$, $C_d=0.0719$, $C_{m,LE}=-0.2069$. → [[#Flat plate at incidence, step by step (slides 7–13): M₁ = 2, α = 10°, p₁ = 30 kPa, c = 1 m|§6]]
- [ ] Slide 9 of 2.3, "show it": $s_2-s_1$ depends only on $M_{n1}$, and $\mathrm ds/\mathrm dM_{n1}=0$ at $M_{n1}=1$ (L2-3, ll. 396–435). → [[#4. Entropy across a shock and why shocks compress|§4]]
- [ ] Derive $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dU/U$ from tangential momentum across a Mach wave and convert it to $\mathrm dM$ (derived in full in L2-4, ll. 71–232). → [[#Deriving the Prandtl–Meyer function (slides 3–6)|§5]]

### Further practice

- [ ] *"If you haven't done proper revision, then probably it's a good time to do that, to catch up"* (L2-3, ll. 182–184): work back through [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]] and [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]].
- [ ] *"If you go through a few example questions then you will be familiar with this process"* (L2-4, ll. 307–310): practise $\nu(M_2)=\nu(M_1)+\theta$ with the IFT, including the $M_1=3$, $\theta=13^\circ$ fan ($M_2=3.78$, 67.4% drop, $\phi=17.1^\circ$). → [[#Using it (slides 7–8)|§5]] · [[#Worked example (slides 9–11): M₁ = 3, θ = 13°|§5 example]]
- [ ] Tutorial 1 weekend homework (ll. 232–235): the triangular wing at a second $\alpha$, and $x_{ac}\approx c/2$. → [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing#Weekend homework: the aerodynamic centre (ll. 228–235)|Tutorial 1]]
- [ ] Example Sheet 1 Q3 (reflection), Q4 (flat plate) and Q6–Q7 (diamond). → [[SESA3029 Example Sheet 1 - Solutions]]
- [ ] Show $C_{m,LE}=-\Delta p/(2q_\infty)$ with the nose-up sign convention and derive the lecture's $x_{cp}/c=1/(2\cos\alpha)$ (L2-5, ll. 106–117, 215–242). Then show that along the chord $x_{cp}=x_{ac}=c/2$ exactly. → [[#Flat plate at incidence, step by step (slides 7–13): M₁ = 2, α = 10°, p₁ = 30 kPa, c = 1 m|§6]]
- [ ] Explain why a supersonic inviscid flat plate has wave drag when a subsonic one has none (L2-5, ll. 149–213), why the ac moves from $c/4$ to $c/2$ and why that matters for static margin (ll. 243–257), and the difference between the sign of $C_{m,LE}$ and the slope $\mathrm dC_m/\mathrm d\alpha$ (ll. 138–148). → [[#6. The shock-expansion method|§6]]
- [ ] Explain why a "shock" with $M_{n1}<1$ or with a pressure drop is impossible (L2-3, ll. 416–435), and why convex corners give fans and concave corners shocks (L2-4, ll. 16–34). → [[#4. Entropy across a shock and why shocks compress|§4]] · [[#Physical picture (Lecture 2.4, slides 1–2)|§5]]
- [ ] Suggested, not lecturer-set: derive the cubic entropy estimate and the closed-form $\nu(M)$, including $\nu_{max}=130.45^\circ$. → [[#4. Entropy across a shock and why shocks compress|§4]] · [[#Deriving the Prandtl–Meyer function (slides 3–6)|§5]]
- [ ] Blackboard Test 1, due Sunday 11 October, 23:59 (L2-4, ll. 1–3). It covers Week 1; expansion waves are not in it (*"the test is always looking backwards a bit"*, ll. 457–459). → [[SESA3029 Test 1 - Solutions]]
