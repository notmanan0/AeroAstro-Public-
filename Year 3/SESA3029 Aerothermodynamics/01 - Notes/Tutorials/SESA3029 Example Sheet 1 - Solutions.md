---
title: "SESA3029 Example Sheet 1 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Blocks 1–3: normal and oblique shocks, expansions, nozzles"
tags: [sesa3029, tutorial-solutions, example-sheet, normal-shock, oblique-shock, shock-expansion, nozzle]
sheet: "Example Sheet 1"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
status: complete
sources: ["03 - Exams & Past Papers/ExamplesSheet1.pdf"]
---

# SESA3029 Example Sheet 1 - Solutions

> [!abstract] Sheet info
> Eight questions covering Weeks 1–4: normal shocks, the low-Mach limit, shock reflection, shock-expansion theory, the Mach cone, a diamond aerofoil and a wind-tunnel nozzle. All answers use $\gamma=1.4$ and $R=287$ J/kg K, and every number has been verified in Python. Where the sheet quotes both exact and "nearest value" answers, both are reproduced. Discrepancies with the printed answers are flagged.

| Q | Topic | Theory |
|---|---|---|
| 1, 2 | normal shock, low-Mach expansion | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]] |
| 3, 5 | reflection, Mach cone | [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03 §1–2]], [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02 §7]] |
| 4, 6, 7 | shock-expansion theory | [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]] |
| 8 | Laval nozzle | [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]] |

---

## Q1. Normal-shock pressure ratio from a control volume

**Show** $\dfrac{p_2}{p_1}=\dfrac{1+\gamma M_1^2}{1+\gamma M_2^2}$.

A thin control volume of area $A$ surrounds the stationary shock. With no friction and no area change, the net force is pressure alone (W01 §5):

$$
\dot m\,(U_2-U_1)=(p_1-p_2)A,
\qquad
\dot m=\rho_1U_1A=\rho_2U_2A.
$$

Divide by $A$ and use $\dot m/A=\rho_1U_1=\rho_2U_2$ to split the momentum flux between stations:

$$
p_1+\rho_1U_1^2=p_2+\rho_2U_2^2.
$$

Rewrite $\rho U^2$ in terms of $p$ and $M$ using $a^2=\gamma p/\rho$:

$$
\rho U^2=\rho a^2\,\frac{U^2}{a^2}=\rho\,\frac{\gamma p}{\rho}\,M^2=\gamma pM^2.
$$

So

$$
p_1\left(1+\gamma M_1^2\right)=p_2\left(1+\gamma M_2^2\right)
\quad\Longrightarrow\quad
\boxed{\frac{p_2}{p_1}=\frac{1+\gamma M_1^2}{1+\gamma M_2^2}}.
$$

> [!check] Check
> At $M_1=2$, $M_2=0.5774$: $(1+5.6)/(1+0.4667)=4.500$, the normal-shock table value ✓. The result is pure momentum: it holds for any gas whose sound speed obeys $a^2=\gamma p/\rho$.

## Q2. Low-Mach expansion of p₀/p and Bernoulli

$$
\frac{p_0}{p}=(1+x)^n,
\qquad
x=\frac{\gamma-1}{2}M^2,
\qquad
n=\frac{\gamma}{\gamma-1}.
$$

**Binomial series:** $(1+x)^n=1+nx+\dfrac{n(n-1)}{2}x^2+\dfrac{n(n-1)(n-2)}{6}x^3+\dots$ Evaluate each term:

$$
nx=\frac{\gamma}{\gamma-1}\cdot\frac{\gamma-1}{2}M^2=\frac{\gamma}{2}M^2,
$$

$$
\frac{n(n-1)}{2}x^2=\frac12\cdot\frac{\gamma}{\gamma-1}\cdot\frac{1}{\gamma-1}\cdot\frac{(\gamma-1)^2}{4}M^4=\frac{\gamma}{8}M^4,
$$

where $n-1=\dfrac{1}{\gamma-1}$, and

$$
\frac{n(n-1)(n-2)}{6}x^3=\frac{\gamma(2-\gamma)}{48}M^6,
$$

where $n-2=\dfrac{2-\gamma}{\gamma-1}$.

**Subtract 1 and factor out $\tfrac{\gamma}{2}M^2$:**

$$
\frac{p_0-p}{p}=\frac{\gamma}{2}M^2\left[1+\frac{M^2}{4}+\frac{2-\gamma}{24}M^4+\dots\right].
$$

**Divide by the dynamic pressure,** $\tfrac12\rho V^2=\tfrac12\gamma pM^2$ (from Q1's $\rho V^2=\gamma pM^2$):

$$
\boxed{\frac{p_0-p}{\frac12\rho V^2}=1+\frac{M^2}{4}+O(M^4)}
\qquad\left(\text{next term }\tfrac{2-\gamma}{24}M^4\right).
$$

**Comparison.** Incompressible Bernoulli gives $p_0-p=\tfrac12\rho V^2$ exactly, i.e. 1. The compressible "pressure coefficient at stagnation" exceeds 1 by $M^2/4$:

| $M$ | 0.1 | 0.3 | 0.5 | 0.7 |
|---|---:|---:|---:|---:|
| exact | 1.0025 | 1.0227 | 1.0641 | 1.1286 |
| $1+M^2/4$ | 1.0025 | 1.0225 | 1.0625 | 1.1225 |

Bernoulli is within 2% only below about $M=0.3$, which is the usual incompressibility limit. A Pitot probe read with Bernoulli **overestimates** $V$ by about $M^2/8$ (W01 §7).

## Q3. Ramp shock reflected from a wall

$M_1=2.3$, ramp $\theta=8^\circ$, $p_1=0.2$ atm $=20.265$ kPa, upper wall parallel to the free stream.

**Incident shock A.**

1. $\theta$–$\beta$–$M$ (weak) gives $\beta_A=32.42^\circ$.
2. $M_{n1}=2.3\sin32.42^\circ=1.2329$.
3. Normal-shock relations: $M_{n2}=0.8224$ and $p_2/p_1=1.6068$.

$$
p_2=1.6068\times20.265=32.56\ \text{kPa},
\qquad
M_2=\frac{0.8224}{\sin24.42^\circ}=1.990.
$$

**Reflected shock B.** The wall turns zone 2 back by $8^\circ$ (W03 §1).

1. $\theta=8^\circ$ at $M_2=1.990$ gives $\beta_B=37.41^\circ$, measured from $\mathbf V_2$.
2. $M_{n}=1.990\sin37.41^\circ=1.2087$.
3. $M_{n3}=0.8368$ and $p_3/p_2=1.5379$.

$$
p_3=1.5379\times32.56=50.08\ \text{kPa},
\qquad
M_3=\frac{0.8368}{\sin29.41^\circ}=1.704.
$$

The reflected shock makes $\phi=\beta_B-\theta=29.4^\circ$ with the upper wall ($\beta_A=32.4^\circ$).

**Answers:** $p_2=32.6$ kPa, $M_2=1.99$, $p_3=50.1$ kPa, $M_3=1.70$ ✓ (sheet: 32.6, 1.99, 50.1, 1.70).

> [!note] "Nearest value" route (sheet: 33.0, 1.97, 51.8, 1.66)
> Reading the chart to $0.5^\circ$ gives $\beta_A\approx32.5^\circ$ and nearest table rows. The errors compound through two shocks, so expect about 3% scatter.

**Maximum ramp angle for regular reflection.** We need $\theta\le\theta_{max}(M_2(\theta))$. As $\theta$ grows, $M_2$ falls and so does $\theta_{max}(M_2)$. Bisecting on $\theta_{max}(M_2)-\theta$:

$$
\boxed{\theta_{RR}=16.1^\circ}\quad(\text{at which }M_2=1.662,\ \theta_{max}(1.662)=16.1^\circ).
$$

Sheet: 16° ✓. Above this a Mach reflection forms (W03 §2).

## Q4. Flat plate by shock-expansion theory

$c=6$ cm, $\alpha=10^\circ$, $M_1=2.7$, $T_1=150$ K, $p_1=20$ kN/m².

**Upper surface: expansion through $10^\circ$.**

$$
\nu(2.7)=43.62^\circ
\ \Rightarrow\
\nu_U=53.62^\circ
\ \Rightarrow\
M_U=3.208,
$$

$$
\frac{p_U}{p_1}=\left(\frac{1+0.2\times2.7^2}{1+0.2\times3.208^2}\right)^{3.5}=0.4651
\ \Rightarrow\
p_U=9.30\ \text{kN/m}^2.
$$

**Lower surface: shock with $\theta=10^\circ$.**

$$
\beta=29.82^\circ,
\qquad
M_{n1}=1.3428,
\qquad
\frac{p_L}{p_1}=1.9369
\ \Rightarrow\
p_L=38.74\ \text{kN/m}^2,
$$

$$
M_L=\frac{0.7651}{\sin19.82^\circ}=2.256.
$$

**Forces per unit span.** The pressures are uniform, so the force is normal to the plate (W03 §6):

$$
N'=(p_L-p_U)\,c=(38.74-9.30)\times0.06=1.766\ \text{kN/m},
$$

$$
L'=N'\cos10^\circ=1.739\ \text{kN/m},
\qquad
D'=N'\sin10^\circ=0.307\ \text{kN/m}.
$$

> [!note] Comparison with the printed answers (9.4, 39.2, 1.76, 0.31)
> The printed answers are "nearest value" chart and table readings, about 1% high. The printed 1.76 kN/m equals the **normal** force $N'$. Strictly, the lift is $N'\cos\alpha=1.74$ kN/m. The temperature (150 K) is not needed for forces. It only gives speeds: for example $U_1=Ma=2.7\sqrt{1.4\times287\times150}=663$ m/s, and the surface temperatures are $T_U=120.5$ K and $T_L=182.7$ K.

## Q5. When is a supersonic jet heard?

$M=2$ at $h=2$ km, $T=18^\circ$C $=291.15$ K, uniform.

You hear nothing until the **Mach cone** (W02 §7) sweeps over you. Overhead, at $t=0$, the aircraft is directly above. It must travel a further horizontal distance $x$ such that the cone's edge, inclined at $\mu$ to the flight path, reaches the ground below it:

$$
\tan\mu=\frac{h}{x}
\quad\Longrightarrow\quad
x=\frac{h}{\tan\mu}.
$$

With $\mu=\sin^{-1}(1/2)=30^\circ$ and $a=\sqrt{1.4\times287\times291.15}=342.0$ m/s:

$$
t=\frac{x}{Ma}=\frac{h}{Ma\tan\mu}=\frac{2000}{2\times342.0\times\tan30^\circ}=\boxed{5.06\ \text{s}}
$$

The sheet gives 5.06 s ✓. (By then the aircraft is 3.46 km past overhead.)

## Q6. Diamond aerofoil by shock-expansion theory

$t/c=0.05$, $\alpha=2^\circ$, $M_1=1.8$, $p_1=50$ kPa, $c=1$ m. Half-angle $\varepsilon=\tan^{-1}(0.05)=2.862^\circ$.

**Turning angle at each face** (W03 §6). The chord is pitched nose-up by $\alpha$:

| Face | Turn | Wave |
|---|---|---|
| 1u (upper front) | $\varepsilon-\alpha=0.862^\circ$ into the flow | weak shock |
| 2u (upper rear) | $2\varepsilon=5.725^\circ$ away | fan |
| 1l (lower front) | $\varepsilon+\alpha=4.862^\circ$ into the flow | shock |
| 2l (lower rear) | $2\varepsilon=5.725^\circ$ away | fan |

**(a) Surface pressures.**

| Face | Working | $M$ | $p$ (kPa) |
|---|---|---:|---:|
| 1u | $\beta=34.51^\circ$, $M_{n1}=1.0197$, $p/p_1=1.0465$ | 1.770 | **52.3** |
| 2u | $\nu=19.86^\circ+5.725^\circ=25.59^\circ$, $p/p_{1u}=0.7337$ | 1.971 | **38.4** |
| 1l | $\beta=38.30^\circ$, $M_{n1}=1.1157$, $p/p_1=1.2856$ | 1.633 | **64.3** |
| 2l | $\nu=15.83^\circ+5.725^\circ=21.55^\circ$, $p/p_{1l}=0.7432$ | 1.829 | **47.8** |

The sheet gives 52.3, 38.4, 64.3 and 47.8 kPa ✓.

**(b) Forces.** Each face has length $s=(c/2)/\cos\varepsilon$, so its projections are $s\cos\varepsilon=c/2$ and $s\sin\varepsilon=t/2$. Summing $-p\,\mathbf n\,s$ over the four faces in **body axes** ($x$ along the chord, $y$ normal to it):

$$
F_y=\frac c2\Big[(p_{1l}+p_{2l})-(p_{1u}+p_{2u})\Big]=\frac12\big[112.05-90.71\big]=10.671\ \text{kN/m},
$$

$$
F_x=\frac t2\Big[(p_{1u}+p_{1l})-(p_{2u}+p_{2l})\Big]=0.025\,\big[116.60-86.16\big]=0.761\ \text{kN/m}.
$$

$F_x$ is pressure drag from thickness: the front faces push back and the rear faces pull back. Now rotate into wind axes:

$$
L'=F_y\cos\alpha-F_x\sin\alpha=10.665-0.027=\boxed{10.64\ \text{kN/m}},
$$

$$
D'=F_y\sin\alpha+F_x\cos\alpha=0.372+0.761=\boxed{1.13\ \text{kN/m}}.
$$

**Moment about the leading edge**, nose-up positive. Each face force acts at its midpoint, $(c/4,\pm t/4)$ or $(3c/4,\pm t/4)$. Working face by face:

- upper front contributes $+p_{1u}(c^2+t^2)/8$ (pressure on top, ahead of the TE, pushes down, so nose-up);
- upper rear contributes $+p_{2u}(3c^2-t^2)/8$;
- lower faces give the same with negative signs.

$$
M'_{LE}=\frac18\Big[(p_{1u}-p_{1l})(c^2+t^2)+(p_{2u}-p_{2l})(3c^2-t^2)\Big]
$$

$$
=\frac18\big[(-11.957)(1.0025)+(-9.385)(2.9975)\big]=\boxed{-5.02\ \text{kN}}\quad(\text{nose-down}).
$$

**(c) Centre of pressure.**

$$
x_{cp}=-\frac{M'_{LE}}{L'}=\frac{5.015}{10.638}=\boxed{0.47\ \text{m}}.
$$

Equivalently, along the chord, $-M'_{LE}/F_y=0.470$.

The sheet gives $L=10.6$ kN/m, $D=1.1$ kN/m, $M=-5.02$ kN and $x_{cp}=0.47$ ✓.

> [!tip] Why ahead of mid-chord?
> The front faces carry the larger pressure difference (12.0 kPa against 9.4 kPa on the rear), so the resultant moves forward of $c/2$. Linear theory, with uniform $\Delta p$ on a flat plate, puts it at exactly $c/2$; compare [[SESA3029 Example Sheet 2 - Solutions#Q5. Diamond aerofoil by Ackeret theory|Example Sheet 2 Q5]]. As coefficients, with $q_\infty=113.4$ kPa: $C_l=0.0938$, $C_d=0.0100$ and $C_{m,LE}=-0.0442$.

## Q7. Wave patterns at α = 5°, 2.86° and −2.86°

(The sheet says "the airfoil from Q7". It means **Q6**.)

![[at_es1_diamond_waves.png|900]]

- **(a) $\alpha=5^\circ>\varepsilon$.** The upper front face is inclined *away* from the flow by $\alpha-\varepsilon=2.14^\circ$, so the upper leading edge carries an **expansion fan**. The lower leading edge has a shock, turning by $\varepsilon+\alpha=7.86^\circ$. Both shoulders carry fans. At the trailing edge the streams meet at a slip line, with a shock above and a fan below for this case.
- **(b) $\alpha=2.86^\circ=\varepsilon$.** The upper front face is **parallel** to the free stream. There is no wave there (only a Mach line), and $p_{1u}=p_\infty=50$ kPa. The lower leading-edge shock turns by $2\varepsilon=5.72^\circ$.
- **(c) $\alpha=-2.86^\circ$.** This is the mirror image of (b): no wave on the lower front face, and a shock on top.

These are computed patterns, with the thickness drawn ×4 for visibility. The general rule is: **$\alpha<\varepsilon$, both leading edges shocks; $\alpha=\varepsilon$, one face wave-free; $\alpha>\varepsilon$, a fan on top.**

## Q8. Supersonic wind-tunnel nozzle

Test section: $M=2.5$, $p=0.1$ bar, $T=-23^\circ$C $=250.15$ K.

**Area ratio.** The test section is the nozzle exit and the throat is sonic, so $A_e/A_t=A/A^*(2.5)$ (W04 §2):

$$
\frac{A_e}{A_t}=\frac{1}{2.5}\left[\frac{2}{2.4}\left(1+0.2\times6.25\right)\right]^{3}=\frac{(1.875)^3}{2.5}=\boxed{2.64}.
$$

**Reservoir conditions.** These are isentropic stagnation relations with $1+0.2M^2=2.25$:

$$
T_0=250.15\times2.25=\boxed{562.8\ \text{K}},
\qquad
p_0=0.1\times2.25^{3.5}=0.1\times17.09=\boxed{1.71\ \text{bar}}.
$$

The sheet gives 2.64, 562.5 K and 1.71 bar ✓. The sheet's 562.5 K uses $T=250$ K.

## Links

- Theory: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] · [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]] · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- Next sheet: [[SESA3029 Example Sheet 2 - Solutions]]
- Hub: [[SESA3029 Aerothermodynamics Hub]] · Formulae: [[SESA3029 Formula Sheet]]
