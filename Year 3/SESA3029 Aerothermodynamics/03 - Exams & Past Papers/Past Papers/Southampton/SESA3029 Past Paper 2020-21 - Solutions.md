---
title: "SESA3029 Past Paper 2020-21 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, shock-expansion, ackeret, wind-tunnel, oblique-shock, newton-raphson, boundary-layer, finite-difference]
paper: "2020-21"
theory_notes: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-202021-01-SESA3029.pdf"]
---

# SESA3029 Past Paper 2020-21 - Solutions

> [!abstract] Paper info
> 2020-21 Semester 1 Assessment: a 24-hour open-book paper (suggested 3–4 hours, handwritten solutions, no formula sheet attached), three questions worth 50, 20 and 30 marks. The front page gives $R=287\ \text{J/(kg K)}$, $c_p=1004.5\ \text{J/(kg K)}$, $\gamma=1.4$, $\rho=1.225\ \text{kg/m}^3$ and $\mu=1.8\times 10^{-5}\ \text{N s/m}^2$, and allows a spreadsheet shock calculator. Q1 takes $t/c\in[0.04,0.085]$ and $M_1\in[1.4,2.4]$ from a per-student parameter file (`SESA3029_individual_parameters.pdf`) that is not in the archive, so Q1 is set out for general values and worked in full for $M_1=2.0$, $t/c=0.06$. Every number was recomputed in Python. Question 3 is heat transfer (Weeks 9–12, not yet lectured).

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 50 | Kite aerofoil ($p_0=180\ \text{kPa}$, $\alpha=t/c$): shock-expansion, pressure along an off-body line A–B, Ackeret, 1/10-scale tunnel test | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 20 | Rearranging θ–β–M and a Newton–Raphson solver for β | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]] |
| 3 | 30 | Splitter-plate design: laminar and turbulent convection plus a 2D Laplace finite-difference solve. Heat transfer (Weeks 9–12, not yet lectured) | Not yet lectured |

---

## Q1. Kite-shaped supersonic aerofoil and off-body pressure (50 marks)

> A kite-shaped aerofoil of chord $c=1\ \text{m}$ has thickness $t$ at $c/3$ and incidence $\alpha = t/c$ (rad) to an oncoming flow at Mach number $M_1 \in [1.4, 2.4]$ and stagnation pressure $p_0 = 180\ \text{kPa}$ ($t/c \in [0.04, 0.085]$). Leading edge is at $(0,0)$ and line A–B runs parallel to the oncoming flow from $A=(0, 0.5\ \text{m})$ to $B=(3\ \text{m}, 0.5\ \text{m})$.
> (i) Sketch wave patterns and compute Mach numbers on all 4 surfaces by shock-expansion. [14]
> (ii) Plot $p(x)$ along A–B for shock-expansion (solid) and Ackeret (dashed), labelling key features. [26]
> (iii) Discuss experimental differences expected when testing a 1/10-scale model in a $50\ \text{cm} \times 10\ \text{cm} \times 10\ \text{cm}$ supersonic wind tunnel. [10]

> [!warning] Parameter file missing, and one corner of the range fails
> The per-student values are not available, so the method below is general and the numbers are for $M_1=2.0$, $t/c=0.06$. At the corner $M_1=1.4$, $t/c=0.085$ of the allowed range the lower forward surface turns the flow by $12.14^\circ$, more than $\theta_{\max}(1.4)=9.43^\circ$, so the leading-edge shock on that side detaches and the shock-expansion method does not apply.

![[at_pp_202021_q1_kite_aerofoil.png|900]]

### (i) Wave pattern and surface Mach numbers [14 marks]

#### Geometry and flow deflections

The thickness $t$ sits at $c/3$, half above and half below the chord, so the forward and rear facets make angles with the chord of

$$
\phi_f=\arctan\frac{t/2}{c/3}=\arctan\left(1.5\,\frac{t}{c}\right),
\qquad
\phi_r=\arctan\frac{t/2}{2c/3}=\arctan\left(0.75\,\frac{t}{c}\right).
$$

The chord is pitched nose-up by $\alpha=t/c$ rad. Measured from the oncoming flow, the upper forward facet therefore turns the flow by $\delta_{UF}=\phi_f-\alpha$ into itself and the lower forward facet by $\delta_{LF}=\phi_f+\alpha$. Over the whole range, $\arctan(1.5\,t/c)>t/c$, so $\delta_{UF}>0$ and both forward facets carry attached weak oblique shocks from the leading edge. At the shoulders ($c/3$) both surfaces turn away from the flow by $\phi_f+\phi_r$, which produces a centred Prandtl–Meyer fan on each side. The rear facets then run at $-(\phi_r+\alpha)$ (upper) and $+(\phi_r-\alpha)$ (lower) to the free stream. At the trailing edge the two streams meet at different angles and pressures, so a trailing-edge shock forms on the upper side and a weak wave, an expansion here, on the lower side, with a slip line between them along which pressure and flow direction match.

For $t/c=0.06$ the angles are

$$
\alpha=0.06\ \text{rad}=3.438^\circ,
\qquad
\phi_f=\arctan0.09=5.143^\circ,
\qquad
\phi_r=\arctan0.045=2.577^\circ,
$$

$$
\delta_{UF}=5.143^\circ-3.438^\circ=1.705^\circ,
\qquad
\delta_{LF}=5.143^\circ+3.438^\circ=8.581^\circ,
\qquad
\phi_f+\phi_r=5.143^\circ+2.577^\circ=7.719^\circ .
$$

The free-stream static pressure is

$$
p_1=p_0\left(1+0.2M_1^2\right)^{-3.5}=180\times1.8^{-3.5}=\frac{180}{7.8244}=23.00\ \text{kPa}.
$$

#### Upper forward facet: oblique shock

Trial values of $\beta$ in the θ–β–M relation at $M_1=2.0$ bracket $\theta=1.705^\circ$.

| $\beta$ (°) | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ (°) |
|---:|---:|---:|---:|---:|---:|
| 31 | 0.06106 | 9.47789 | 3.32856 | 0.02144 | 1.228 |
| 32 | 0.12326 | 9.35348 | 3.20067 | 0.04218 | 2.415 |

Interpolating,

$$
\beta_{UF}\approx31+\frac{1.705-1.228}{2.415-1.228}=31+0.402=31.40^\circ,
$$

and the exact root is $31.398^\circ$. Then

$$
M_{n1}=2.0\sin31.40^\circ=2.0\times0.52097=1.0419 .
$$

The NST rows $M_{n1}=1.04$ ($M_{n2}=0.9620$, $p_2/p_1=1.0952$) and $1.06$ ($0.9444$, $1.1442$) give, with fraction $(1.0419-1.04)/0.02=0.097$,

$$
\frac{p_{UF}}{p_1}=1.0952+0.097\times0.0490=1.0999,
\qquad
M_{n2}=0.9620-0.097\times0.0176=0.9603 .
$$

So

$$
p_{UF}=23.00\times1.0999=25.30\ \text{kPa},
\qquad
M_{UF}=\frac{M_{n2}}{\sin(\beta_{UF}-\delta_{UF})}=\frac{0.9603}{\sin29.693^\circ}=\frac{0.9603}{0.49536}=\boxed{1.94} .
$$

The unrounded value is $M_{UF}=1.9386$.

#### Upper aft facet: expansion at the shoulder

The IFT rows $M=1.92$ ($\nu=24.1506^\circ$) and $1.94$ ($24.7123^\circ$) give, with fraction $(1.9386-1.92)/0.02=0.930$,

$$
\nu(M_{UF})=24.1506+0.930\times0.5617=24.673^\circ .
$$

Adding the turn,

$$
\nu(M_{UA})=24.673^\circ+7.719^\circ=32.392^\circ .
$$

The rows $M=2.22$ ($\nu=32.2494^\circ$) and $2.24$ ($32.7629^\circ$) bracket this. The fraction is $(32.3924-32.2494)/0.5135=0.279$, so

$$
M_{UA}=2.22+0.02\times0.279=\boxed{2.23}\quad(2.2256) .
$$

The fan is isentropic, so

$$
p_{UA}=p_{UF}\left(\frac{1+0.2M_{UF}^2}{1+0.2M_{UA}^2}\right)^{3.5}=25.30\times\left(\frac{1.75163}{1.99062}\right)^{3.5}=25.30\times0.63914=16.17\ \text{kPa}.
$$

#### Lower forward facet: oblique shock

At $\theta=8.581^\circ$ the trial values are

| $\beta$ (°) | $M_1^2\sin^2\beta-1$ | $M_1^2(\gamma+\cos2\beta)+2$ | $2\cot\beta$ | $\tan\theta$ | $\theta$ (°) |
|---:|---:|---:|---:|---:|---:|
| 37 | 0.44873 | 8.70255 | 2.65409 | 0.13685 | 7.793 |
| 38 | 0.51616 | 8.56769 | 2.55988 | 0.15422 | 8.767 |

$$
\beta_{LF}\approx37+\frac{8.581-7.793}{8.767-7.793}=37+0.809=37.81^\circ,
$$

with exact root $37.806^\circ$. Then

$$
M_{n1}=2.0\sin37.81^\circ=1.2260 .
$$

The NST rows $1.22$ ($M_{n2}=0.8300$, $p_2/p_1=1.5698$) and $1.24$ ($0.8183$, $1.6272$) give, with fraction $0.299$,

$$
\frac{p_{LF}}{p_1}=1.5698+0.299\times0.0574=1.5870,
\qquad
M_{n2}=0.8300-0.299\times0.0117=0.8265 .
$$

So

$$
p_{LF}=23.00\times1.5869=36.51\ \text{kPa},
\qquad
M_{LF}=\frac{0.8264}{\sin(37.806^\circ-8.581^\circ)}=\frac{0.8264}{0.48823}=\boxed{1.69}\quad(1.6927) .
$$

#### Lower aft facet: expansion at the shoulder

The IFT rows $1.68$ ($17.2220^\circ$) and $1.70$ ($17.8099^\circ$) give, with fraction $0.633$,

$$
\nu(M_{LF})=17.2220+0.633\times0.5879=17.594^\circ,
$$

$$
\nu(M_{LA})=17.594^\circ+7.719^\circ=25.314^\circ .
$$

The rows $1.96$ ($25.2711^\circ$) and $1.98$ ($25.8269^\circ$) bracket this with fraction $(25.3137-25.2711)/0.5558=0.077$.

$$
M_{LA}=1.96+0.02\times0.077=\boxed{1.96}\quad(1.9615),
$$

$$
p_{LA}=36.51\times\left(\frac{1.57302}{1.76952}\right)^{3.5}=36.51\times0.66233=24.18\ \text{kPa}.
$$

| Surface | Wave | $M$ | $p$ (kPa) |
|---|---|---:|---:|
| upper forward | shock, $\beta=31.40^\circ$ | 1.94 | 25.30 |
| upper aft | fan, $7.72^\circ$ | 2.23 | 16.17 |
| lower forward | shock, $\beta=37.81^\circ$ | 1.69 | 36.51 |
| lower aft | fan, $7.72^\circ$ | 1.96 | 24.18 |

### (ii) Pressure distribution along line A–B [26 marks]

A–B lies above the aerofoil, so it sees only the upper-surface waves: the leading-edge shock, the shoulder fan and the trailing-edge shock. The working assumes inviscid flow of a perfect gas with no wave interactions below $y=0.5$ m, which is checked at the end of this part.

#### Shoulder and trailing-edge coordinates

The chord is rotated nose-up by $\alpha$, so a point at distance $c/3$ along it sits at $\left(\tfrac{c}{3}\cos\alpha,\,-\tfrac{c}{3}\sin\alpha\right)$, and the upper shoulder is a further $t/2$ along the chord normal $(\sin\alpha,\cos\alpha)$.

$$
x_U=\frac{c}{3}\cos\alpha+\frac{t}{2}\sin\alpha=0.33273+0.00180=0.3345\ \text{m},
$$

$$
y_U=-\frac{c}{3}\sin\alpha+\frac{t}{2}\cos\alpha=-0.01999+0.02995=0.0100\ \text{m}.
$$

The trailing edge is at

$$
x_{TE}=c\cos\alpha=0.9982\ \text{m},
\qquad
y_{TE}=-c\sin\alpha=-0.0600\ \text{m}.
$$

#### Leading-edge shock

The shock leaves $(0,0)$ at $\beta_{UF}=31.40^\circ$ to the free stream and crosses $y=0.5$ m at

$$
x_s=\frac{0.5}{\tan31.40^\circ}=\frac{0.5}{0.61034}=\boxed{0.82\ \text{m}},
$$

where the pressure jumps from $23.00$ to $25.30$ kPa.

#### Shoulder expansion fan

The upper forward facet is inclined at $+\delta_{UF}=1.705^\circ$, and the first Mach line of the fan makes $\mu_{UF}=\arcsin(1/1.9386)=31.053^\circ$ with it, so its inclination to the free stream is

$$
\mu_{UF}+\delta_{UF}=31.053^\circ+1.705^\circ=32.758^\circ,
$$

$$
x_{\text{fan},1}=x_U+\frac{0.5-y_U}{\tan32.758^\circ}=0.3345+\frac{0.4900}{0.64343}=\boxed{1.10\ \text{m}} .
$$

The upper aft facet is inclined at $-(\phi_r+\alpha)=-6.014^\circ$, and the last Mach line makes $\mu_{UA}=\arcsin(1/2.2256)=26.700^\circ$ with it.

$$
\mu_{UA}-(\phi_r+\alpha)=26.700^\circ-6.014^\circ=20.686^\circ,
$$

$$
x_{\text{fan},2}=0.3345+\frac{0.4900}{\tan20.686^\circ}=0.3345+\frac{0.4900}{0.37759}=\boxed{1.63\ \text{m}} .
$$

Between these two points the pressure falls smoothly from $25.30$ to $16.17$ kPa.

#### Trailing-edge shock and wake pressure

The upper stream arrives at the trailing edge at $M_{UA}=2.2256$, $p_{UA}=16.17$ kPa, inclined at $-6.014^\circ$. The lower stream arrives at $M_{LA}=1.9615$, $p_{LA}=24.18$ kPa, inclined at $\phi_r-\alpha=-0.861^\circ$. Both must leave along a common slip-line angle $\phi_w$ (positive upwards) at a common pressure. The upper stream is turned into itself by $\phi_w+6.014^\circ$ through a shock; the lower stream is turned away from itself by $\phi_w+0.861^\circ$ through an expansion. Two trial values of $\phi_w$ give

| $\phi_w$ (°) | upper turn (°) | $\beta$ (°) | $p_{\text{upper}}$ (kPa) | lower turn (°) | $p_{\text{lower}}$ (kPa) | difference (kPa) |
|---:|---:|---:|---:|---:|---:|---:|
| 0.00 | 6.014 | 31.629 | 23.006 | 0.861 | 23.041 | $-0.034$ |
| 0.05 | 6.064 | 31.674 | 23.071 | 0.911 | 22.976 | $+0.095$ |

and interpolating for zero difference,

$$
\phi_w=0.05\times\frac{0.034}{0.034+0.095}=0.013^\circ .
$$

The wake is parallel to the free stream to within $0.013^\circ$. The upper turn is then $6.028^\circ$ at $M_{UA}=2.2256$, and the θ–β–M trials

| $\beta$ (°) | $\tan\theta$ | $\theta$ (°) |
|---:|---:|---:|
| 31 | 0.09279 | 5.301 |
| 32 | 0.11266 | 6.428 |

give $\beta\approx31+(6.028-5.301)/(6.428-5.301)=31.645^\circ$ (exact $31.641^\circ$). With $M_{n1}=2.2256\sin31.641^\circ=1.1675$, the NST rows $1.16$ ($p_2/p_1=1.4032$) and $1.18$ ($1.4578$) give $p_2/p_1=1.4032+0.376\times0.0546=1.4237$, so

$$
p_{\text{wake}}=16.17\times1.4236=23.02\ \text{kPa},
$$

$0.02$ kPa above $p_1$. The shock lies at $\beta$ to the upper stream, so its inclination to the free stream is $31.641^\circ-6.014^\circ=25.627^\circ$, and it crosses A–B at

$$
x_{TE,s}=x_{TE}+\frac{0.5-y_{TE}}{\tan25.627^\circ}=0.9982+\frac{0.5600}{0.47969}=\boxed{2.17\ \text{m}},
$$

where the pressure jumps from $16.17$ to $23.02$ kPa and stays there to B.

#### Linearised (Ackeret) distribution

In linear theory every wave runs along a free-stream Mach line, at $\mu_1=\arcsin(1/2)=30^\circ$, and every pressure is $p=p_1+q_1C_p$ with $C_p=2\theta/\lambda$. Here

$$
\lambda=\sqrt{2.0^2-1}=1.7321,
\qquad
q_1=\tfrac12\gamma p_1M_1^2=0.7\times23.00\times4=64.41\ \text{kPa}.
$$

On the upper forward facet $\theta=+1.705^\circ=0.02976$ rad.

$$
p_{UF}=23.00+64.41\times\frac{2\times0.02976}{1.7321}=23.00+64.41\times0.03436=\boxed{25.22\ \text{kPa}},
$$

and on the upper aft facet $\theta=-6.014^\circ=-0.10497$ rad.

$$
p_{UA}=23.00+64.41\times\frac{2\times(-0.10497)}{1.7321}=23.00-64.41\times0.12121=\boxed{15.20\ \text{kPa}} .
$$

Downstream of the trailing edge the flow returns to the free-stream direction and $p=p_1=23.00$ kPa. The three waves reach A–B at

$$
x=\frac{0.5}{\tan30^\circ}=\boxed{0.87\ \text{m}},
\qquad
x=0.3345+\frac{0.4900}{0.57735}=\boxed{1.18\ \text{m}},
\qquad
x=0.9982+\frac{0.5600}{0.57735}=\boxed{1.97\ \text{m}} .
$$

The fan becomes a single step, every step is moved to the free-stream Mach line, and the wake pressure returns to $p_1$. If the thin-aerofoil approximation is carried further and the waves are started from $y=0$ at $x=c/3$ and $x=c$, the last two steps move to $1/3+0.5\sqrt3=1.20$ m and $1+0.5\sqrt3=1.87$ m.

| Feature on A–B | Shock-expansion | Ackeret |
|---|---|---|
| leading-edge wave | $x=0.82$ m, $23.00\to25.30$ kPa | $x=0.87$ m, $23.00\to25.22$ kPa |
| expansion | fan from $1.10$ to $1.63$ m, $25.30\to16.17$ kPa | step at $1.18$ m, $25.22\to15.20$ kPa |
| trailing-edge wave | $x=2.17$ m, $16.17\to23.02$ kPa | $x=1.97$ m, $15.20\to23.00$ kPa |

> [!check] No wave interactions below A–B
> The first fan line ($32.76^\circ$) is steeper than the leading-edge shock ($31.40^\circ$) and starts behind it, so the two converge. Intersecting the lines $y=0.61034\,x$ and $y=0.0100+0.64343\,(x-0.3345)$ gives $x=6.20$ m, $y=3.79$ m, well above A–B. The trailing-edge shock meets the last fan line at $x=4.14$ m, $y=1.45$ m, also above A–B. So along A–B the shock strength and the fan are those at the surface, and the straight-line wave positions above are valid.

### (iii) Differences in a 1/10-scale tunnel test [10 marks]

The model has a 10 cm chord in a 10 cm × 10 cm section, so with the model on the tunnel axis the walls are 5 cm above and below it. That is $0.5c$, the height of line A–B, so a row of pressure taps on the top wall sits where A–B was. It does not record the free-air distribution of part (ii). The leading-edge shock reaches the top wall at $x=0.05/0.61034=8.2$ cm and reflects, and a tap at the wall sees the incident and reflected shocks together: for this weak shock the pressure rise at the wall is about $2.1$ times the free-air jump ($23.0$ to $27.8$ kPa instead of $23.0$ to $25.3$ kPa). The lower shock ($\beta=37.8^\circ$) reaches the bottom wall at $6.4$ cm, and its reflection climbs back to the trailing-edge height at roughly $12$ cm, only about 2 cm behind the model. At lower $M_1$ or larger $t/c$ the shocks are steeper and the reflections land on the model itself, which changes its surface pressures.

The tunnel walls carry boundary layers. Where the reflected shocks meet them, the subsonic part of the boundary layer spreads the pressure rise upstream, and the boundary layer may separate, so the wall taps show a smeared ramp instead of a step. The wall boundary layers also reduce the effective cross-section, which lowers the core Mach number below its nominal value.

The model itself has a Reynolds number ten times smaller than the full-size aerofoil at the same flow conditions. Its boundary layer is relatively thicker and is more likely to stay laminar. The displacement thickness makes the effective facets slightly steeper, which strengthens the leading-edge shocks, smooths the expansion at the shoulder, and thickens the wake, so the trailing-edge shock is weaker and the pressure does not recover cleanly to $p_1$. The trailing-edge shock may also interact with the separated wake.

Smaller effects come from leading-edge bluntness (a small detached bow shock where the inviscid theory assumes a sharp edge), Mach-number non-uniformity from the nozzle, the support sting, and the side walls of a 10 cm span. Starting a supersonic tunnel with a model inside also needs enough diffuser capacity; at the low end of the Mach range ($M_1=1.4$) the blockage of the model and its wall boundary layers can prevent the tunnel from starting.

---

## Q2. Oblique shock rearrangement and Newton–Raphson solver (20 marks)

> (i) Starting from $\tan\theta = 2\cot\beta\left[\dfrac{M_1^2\sin^2\beta - 1}{M_1^2(\gamma + \cos 2\beta) + 2}\right]$, derive $\tan\theta\tan\beta\left(1 + \frac{\gamma+1}{2}M_1^2 - M_1^2\sin^2\beta\right) + 1 - M_1^2\sin^2\beta = 0$. [5]
> (ii) Deduce a Newton–Raphson scheme for $\beta$ given $M_1, \theta$ and demonstrate convergence for a chosen $(M_1, \theta)$. [15]

### (i) Algebraic rearrangement [5 marks]

Start from the θ–β–M relation ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]).

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}.
$$

Multiply both sides by $M_1^2(\gamma+\cos2\beta)+2$.

$$
\tan\theta\left[M_1^2(\gamma+\cos2\beta)+2\right]=2\cot\beta\left(M_1^2\sin^2\beta-1\right).
$$

Multiply both sides by $\tfrac12\tan\beta$, using $\tan\beta\cot\beta=1$.

$$
\tan\theta\tan\beta\left[\frac{M_1^2(\gamma+\cos2\beta)}{2}+1\right]=M_1^2\sin^2\beta-1 .
$$

Replace $\cos2\beta$ by $1-2\sin^2\beta$ inside the bracket.

$$
\frac{M_1^2(\gamma+1-2\sin^2\beta)}{2}+1=1+\frac{\gamma+1}{2}M_1^2-M_1^2\sin^2\beta .
$$

So

$$
\tan\theta\tan\beta\left(1+\frac{\gamma+1}{2}M_1^2-M_1^2\sin^2\beta\right)=M_1^2\sin^2\beta-1 .
$$

Subtract the right-hand side from both sides.

$$
\tan\theta\tan\beta\left(1+\frac{\gamma+1}{2}M_1^2-M_1^2\sin^2\beta\right)+1-M_1^2\sin^2\beta=0 . \qquad\blacksquare
$$

### (ii) Newton–Raphson formulation and convergence [15 marks]

For given $M_1$ and $\theta$, write $C=1+\tfrac{\gamma+1}{2}M_1^2$, which is constant, and take the left-hand side of (i) as the residual.

$$
f(\beta)=\tan\theta\tan\beta\left(C-M_1^2\sin^2\beta\right)+1-M_1^2\sin^2\beta .
$$

Differentiate with $\beta$ in radians. The first term is a product, $\tan\beta$ times $(C-M_1^2\sin^2\beta)$, with

$$
\frac{\mathrm d}{\mathrm d\beta}\tan\beta=\sec^2\beta,
\qquad
\frac{\mathrm d}{\mathrm d\beta}\left(C-M_1^2\sin^2\beta\right)=-2M_1^2\sin\beta\cos\beta=-M_1^2\sin2\beta .
$$

The product rule gives

$$
f'(\beta)=\tan\theta\left[\sec^2\beta\left(C-M_1^2\sin^2\beta\right)-\tan\beta\,M_1^2\sin2\beta\right]-M_1^2\sin2\beta .
$$

Simplify $\tan\beta\sin2\beta=\dfrac{\sin\beta}{\cos\beta}\cdot2\sin\beta\cos\beta=2\sin^2\beta$.

$$
f'(\beta)=\tan\theta\left[\sec^2\beta\left(C-M_1^2\sin^2\beta\right)-2M_1^2\sin^2\beta\right]-M_1^2\sin2\beta .
$$

The Newton–Raphson update is

$$
\beta_{k+1}=\beta_k-\frac{f(\beta_k)}{f'(\beta_k)} .
$$

$f$ has two roots between $\mu$ and $90^\circ$, the weak and the strong shock. Starting a little above the Mach angle $\mu=\arcsin(1/M_1)$ picks the weak root.

#### Demonstration at M₁ = 2.0, θ = 15°

Here $C=1+1.2\times4=5.8$, $\tan15^\circ=0.267949$, $\mu=30^\circ$, and the start is $\beta_0=35^\circ$. The first iterate in full is

$$
\sin^2\beta_0=0.328990,
\qquad
C-M_1^2\sin^2\beta_0=5.8-4\times0.328990=4.484040,
$$

$$
f(\beta_0)=0.267949\times0.700208\times4.484040+1-1.315961=0.841297-0.315961=0.525336,
$$

$$
f'(\beta_0)=0.267949\left[1.490291\times4.484040-8\times0.328990\right]-4\times0.939693=0.267949\times4.050604-3.758772=-2.673415,
$$

$$
\beta_1=35^\circ-\frac{0.525336}{-2.673415}\ \text{rad}=35^\circ+0.196504\ \text{rad}=35^\circ+11.259^\circ=46.259^\circ .
$$

Repeating the step gives

| $k$ | $\beta_k$ (°) | $f(\beta_k)$ | $f'(\beta_k)$ | $\lvert\beta_k-\beta^*\rvert$ (°) |
|---:|---:|---:|---:|---:|
| 0 | 35.000000 | $+5.253\times10^{-1}$ | $-2.6734$ | $1.03\times10^{1}$ |
| 1 | 46.258839 | $-4.849\times10^{-2}$ | $-3.0343$ | $9.15\times10^{-1}$ |
| 2 | 45.343165 | $+2.393\times10^{-5}$ | $-3.0362$ | $4.52\times10^{-4}$ |
| 3 | 45.343617 | $-2.219\times10^{-12}$ | $-3.0362$ | $4.19\times10^{-11}$ |

The weak-shock root is $\beta^*=45.3436^\circ$, the value a bracketing solver also returns.

> [!check] Quadratic convergence
> The error goes $10.3^\circ$, $0.92^\circ$, $4.5\times10^{-4}$°, $4.2\times10^{-11}$°: each error is roughly a constant times the square of the one before, so the number of correct digits doubles at every step once the iterate is close. The secant method used in the coursework converges with order about 1.618 and needs more steps for the same accuracy.

---

## Q3. High-temperature splitter plate thermal design and 2D FD (30 marks)

> [!warning] Heat transfer (Weeks 9–12)
> This question uses material from Weeks 9–12, which have not yet been lectured. Check the notation, the correlations and the node numbering against those lectures when they are written up.

> A steel splitter plate ($\rho_s = 7850\ \text{kg/m}^3$, thickness $d=6\ \text{cm}$, tapered underneath to $x=L/2$, right boundary adiabatic, underside kept at $300\ \text{K}$) carries air flow ($\text{Pr}=0.71$, $u_\infty=45\ \text{m/s}$, $T_\infty=800\ \text{K}$, $p_\infty=180\ \text{kPa}$) with $\dot{Q}=1200\ \text{W}$ uniform heat flux into the top face, $\text{Re}_{\text{crit}}=3\times 10^5$, and $\mu/\mu_{\text{ref}}=(T/T_{\text{ref}})^{0.75}$. Design constraints: $0.45 \le L \le 0.6\ \text{m}$, $0.15 \le w \le 0.3\ \text{m}$, $30 \le m \le 40\ \text{kg}$, and centreline nodes $T_5, T_8, T_{11} < 500\ \text{K}$.
> (i) Choose $L, w$, plot upper-surface $T_s(x)$, comment on internal temperatures, and find total mass. [15]
> (ii) Evaluate boundary nodes $T_1, T_2, T_4, T_7, T_{10}$, construct FD stencils for $T_5, T_8, T_{11}$, solve the linear system, and critique reliability/improvements. [15]

![[at_pp_202021_q3_plate_temp.png|900]]

### (i) Air properties, design choice, surface temperature and mass [15 marks]

#### Air properties at the free-stream state

The properties are taken at $T_\infty=800$ K and $p_\infty=180$ kPa, with $c_p=1004.5$ J/(kg K) from the front page.

$$
\rho=\frac{p_\infty}{RT_\infty}=\frac{180\times10^3}{287\times800}=0.7840\ \text{kg/m}^3,
$$

$$
\mu=\mu_{\text{ref}}\left(\frac{T_\infty}{T_{\text{ref}}}\right)^{0.75}=1.8\times10^{-5}\left(\frac{800}{288}\right)^{0.75}=1.8\times10^{-5}\times2.1517=3.873\times10^{-5}\ \text{N s/m}^2,
$$

$$
\nu=\frac{\mu}{\rho}=\frac{3.873\times10^{-5}}{0.7840}=4.940\times10^{-5}\ \text{m}^2/\text{s},
$$

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{3.873\times10^{-5}\times1004.5}{0.71}=0.05479\ \text{W/(m K)}.
$$

The boundary layer turns turbulent where $\text{Re}_x=3\times10^5$.

$$
x_{\text{crit}}=\frac{\text{Re}_{\text{crit}}\,\nu}{u_\infty}=\frac{3\times10^5\times4.940\times10^{-5}}{45}=0.329\ \text{m}.
$$

Every allowed length ($L\ge0.45$ m) is longer than this, so the rear of the plate is always turbulent.

#### Mass

The side profile is a rectangle $L\times d$ with a triangle of base $L/2$ and height $d$ cut from underneath, leaving an area of $Ld-\tfrac12\cdot\tfrac{L}{2}\cdot d=\tfrac34Ld$. The mass is therefore

$$
m=\tfrac34\rho_sLwd=0.75\times7850\times0.06\,Lw=353.25\,Lw\ \text{kg},
$$

and $30\le m\le40$ kg requires $0.0849\le Lw\le0.1132\ \text{m}^2$.

#### Surface temperature for a uniform heat flux

Heat flows from the hot air into the plate at the uniform flux $q''=\dot Q/(Lw)$, so at each point

$$
q''=h_x\left(T_\infty-T_s\right),
\qquad
T_s(x)=T_\infty-\frac{q''}{h_x}.
$$

The local coefficient comes from the uniform-heat-flux correlations on the 2019-20 and 2021-22 formula sheets.

$$
\text{laminar: }\ \text{Nu}_x=0.453\,\text{Re}_x^{1/2}\text{Pr}^{1/3},
\qquad
\text{turbulent: }\ \text{Nu}_x=0.029\,\text{Re}_x^{0.8}\text{Pr}^{0.6},
\qquad
h_x=\frac{\text{Nu}_x\,k}{x}.
$$

A larger plate area spreads the same 1200 W more thinly, which lowers $q''$ and raises $T_s$ towards 800 K. The interior limit of 500 K is therefore hardest to meet at the heavy end of the mass range. Solving part (ii) for several designs inside the mass limits gives

| $L$ (m) | $w$ (m) | $m$ (kg) | $T_5$ (K) | $T_8$ (K) | $T_{11}$ (K) |
|---:|---:|---:|---:|---:|---:|
| 0.50 | 0.17 | 30.0 | 383.1 | 470.8 | 469.0 |
| 0.50 | 0.20 | 35.3 | 407.1 | 482.7 | 481.1 |
| 0.50 | 0.226 | 39.9 | 422.8 | 490.4 | 489.1 |
| 0.45 | 0.25 | 39.7 | 428.0 | 491.1 | 490.1 |

All of these pass, with the margin shrinking as the mass rises. The chosen design is $L=0.50$ m, $w=0.20$ m, in the middle of the mass range with about 17 K of margin.

$$
m=353.25\times0.50\times0.20=\boxed{35.3\ \text{kg}},
\qquad
q''=\frac{1200}{0.50\times0.20}=12\,000\ \text{W/m}^2 .
$$

#### Surface temperatures at the grid columns

The grid columns are at $x=0,\ 0.125,\ 0.250,\ 0.375,\ 0.500$ m, with $\text{Pr}^{1/3}=0.89211$ and $\text{Pr}^{0.6}=0.81424$. At each column, $\text{Re}_x=u_\infty x/\nu=45x/4.940\times10^{-5}$.

At $x=0.125$ m (node 2, laminar),

$$
\text{Re}_x=113\,862,
\qquad
\text{Nu}_x=0.453\times113\,862^{1/2}\times0.89211=0.453\times337.43\times0.89211=136.37,
$$

$$
h_x=\frac{136.37\times0.05479}{0.125}=59.78\ \text{W/(m}^2\text{ K)},
\qquad
T_2=800-\frac{12\,000}{59.78}=800-200.7=\boxed{599.3\ \text{K}} .
$$

At $x=0.250$ m (node 4, laminar),

$$
\text{Re}_x=227\,723,
\qquad
\text{Nu}_x=0.453\times477.20\times0.89211=192.85,
$$

$$
h_x=\frac{192.85\times0.05479}{0.250}=42.27\ \text{W/(m}^2\text{ K)},
\qquad
T_4=800-\frac{12\,000}{42.27}=800-283.9=\boxed{516.1\ \text{K}} .
$$

At $x=0.375$ m (node 7, turbulent),

$$
\text{Re}_x=341\,585,
\qquad
\text{Nu}_x=0.029\times341\,585^{0.8}\times0.81424=0.029\times26\,718\times0.81424=630.89,
$$

$$
h_x=\frac{630.89\times0.05479}{0.375}=92.18\ \text{W/(m}^2\text{ K)},
\qquad
T_7=800-\frac{12\,000}{92.18}=800-130.2=\boxed{669.8\ \text{K}} .
$$

At $x=0.500$ m (node 10, turbulent),

$$
\text{Re}_x=455\,447,
\qquad
\text{Nu}_x=0.029\times33\,632\times0.81424=794.15,
$$

$$
h_x=\frac{794.15\times0.05479}{0.500}=87.03\ \text{W/(m}^2\text{ K)},
\qquad
T_{10}=800-\frac{12\,000}{87.03}=800-137.9=\boxed{662.1\ \text{K}} .
$$

At the leading edge the boundary layer has zero thickness and $h_x\to\infty$, so $T_1=\boxed{800\ \text{K}}$ in this model. In reality conduction in the sharp edge rounds this off.

Panel (b) above plots $T_s(x)$. In the laminar part $h_x\propto x^{-1/2}$, so the drop below the free-stream temperature, $q''/h_x$, grows like $x^{1/2}$ and $T_s$ falls from 800 K to about 474 K just ahead of transition. At $x_{\text{crit}}$ the coefficient rises about 2.6-fold (from 36.8 to 94.7 W/(m² K)), so $T_s$ jumps back up to about 673 K, and it then falls slowly as $h_x\propto x^{-0.2}$.

#### Expected internal temperatures

The plate is 6 cm deep and 50 cm long, with the top at 500–700 K and the underside held at 300 K, so conduction runs mainly across the thickness. The mid-plane temperature at each column is then close to the mean of the top and bottom values.

$$
T_5\approx\tfrac12(516.1+300)=408\ \text{K},
\qquad
T_8\approx\tfrac12(669.8+300)=485\ \text{K},
\qquad
T_{11}\approx\tfrac12(662.1+300)=481\ \text{K}.
$$

All are below 500 K, and the hottest region is the turbulent rear half, not the leading edge, because the leading edge is thin and close to the 300 K underside.

### (ii) 2D finite-difference solve [15 marks]

#### Grid and stencil

The $5\times3$ grid has

$$
\Delta x=\frac{L}{4}=0.125\ \text{m},
\qquad
\Delta y=\frac{d}{2}=0.030\ \text{m}.
$$

The spacings differ, so the stencil keeps both. Central differences in $\nabla^2T=0$ at an interior node P with neighbours W, E, S, N give

$$
\frac{T_W-2T_P+T_E}{\Delta x^2}+\frac{T_S-2T_P+T_N}{\Delta y^2}=0 .
$$

Multiply by $\Delta y^2$ and write $s=(\Delta y/\Delta x)^2$.

$$
s\left(T_W-2T_P+T_E\right)+T_S-2T_P+T_N=0 .
$$

Collect the $T_P$ terms.

$$
2(1+s)\,T_P=s\left(T_W+T_E\right)+T_N+T_S,
$$

$$
T_P=\frac{s\left(T_W+T_E\right)+T_N+T_S}{2(1+s)} .
$$

Here

$$
s=\left(\frac{0.030}{0.125}\right)^2=0.0576,
\qquad
2(1+s)=2.1152 .
$$

#### Boundary values and node equations

The nodes on the underside and on the tapered face are at 300 K: $T_3=T_6=T_9=T_{12}=300$ K. The top values are those of part (i): $T_4=516.10$ K, $T_7=669.83$ K, $T_{10}=662.12$ K. The right face is adiabatic, $\partial T/\partial x=0$, which a mirror node outside the plate represents with the value $T_8$.

Node 5 has W $=T_3$, E $=T_8$, N $=T_4$, S $=T_6$.

$$
T_5=\frac{0.0576\,(300+T_8)+516.10+300}{2.1152}=\frac{833.38+0.0576\,T_8}{2.1152}=393.997+0.027231\,T_8 .
$$

Node 11 has W $=T_8$, the mirror E $=T_8$, N $=T_{10}$, S $=T_{12}$.

$$
T_{11}=\frac{0.0576\times2T_8+662.12+300}{2.1152}=\frac{962.12+0.1152\,T_8}{2.1152}=454.859+0.054463\,T_8 .
$$

Node 8 has W $=T_5$, E $=T_{11}$, N $=T_7$, S $=T_9$.

$$
T_8=\frac{0.0576\,(T_5+T_{11})+669.83+300}{2.1152} .
$$

#### Solving the system

Substitute the node 5 and node 11 expressions into the node 8 equation.

$$
T_5+T_{11}=848.856+0.081694\,T_8,
$$

$$
2.1152\,T_8=0.0576\,(848.856+0.081694\,T_8)+969.83,
$$

$$
2.1152\,T_8=48.894+0.004706\,T_8+969.83,
$$

$$
2.110494\,T_8=1018.72,
$$

$$
T_8=\boxed{482.7\ \text{K}} .
$$

Back-substituting,

$$
T_5=393.997+0.027231\times482.69=\boxed{407.1\ \text{K}},
\qquad
T_{11}=454.859+0.054463\times482.69=\boxed{481.1\ \text{K}} .
$$

All three mid-plane temperatures are below 500 K, so the design passes on this model, and the values sit within 2 K of the simple averages of part (i).

The 2022–23 and later formula sheets give the turbulent correlation as $\text{Nu}_x=0.0308\,\text{Re}_x^{0.8}\text{Pr}^{1/3}$. With that, $h$ at the turbulent nodes rises to $107.3$ and $101.3$ W/(m² K), $T_7=688.1$ K and $T_{10}=681.5$ K, and the solve gives $T_5=407.4$ K, $T_8=491.6$ K and $T_{11}=490.8$ K, which also pass, with less margin.

#### Reliability and improvements

Three interior nodes cannot resolve the jump in $T_s$ at transition, the sharp leading edge, or the corner where the taper meets the underside, so the solution is a rough estimate. The bigger weakness is the model of the top boundary. Prescribing a uniform $q''$ and the resulting $T_s(x)$ as fixed temperatures decouples the air-side convection from the conduction in the steel, and the two are not consistent. For steel with $k$ of order 15–50 W/(m K), carrying $12$ kW/m² across 6 cm would need a temperature difference of only $q''d/k\approx14$–$48$ K, nowhere near the 200–370 K between $T_s$ and the underside. The convective flux would in fact be far from uniform.

A better analysis would use a convective (Robin) condition on the top face, $-k_s\,\partial T/\partial y=h_x\left(T_\infty-T_s\right)$, solved together with the conduction, evaluate the air properties at the film temperature $\tfrac12(T_\infty+T_s)$ rather than at $T_\infty$, and refine the grid, especially near the leading edge and near $x_{\text{crit}}$.

---

## Paper slips and ambiguities

- The parameter file `SESA3029_individual_parameters.pdf` is not archived with the paper, so Q1 is worked for $M_1=2.0$, $t/c=0.06$. At the corner $M_1=1.4$, $t/c=0.085$ of the stated range, $\delta_{LF}=12.14^\circ$ exceeds $\theta_{\max}(1.4)=9.43^\circ$ and the lower leading-edge shock detaches.
- No formula sheet was attached in 2020-21. The heat-transfer correlations used are those of the 2019-20 and 2021-22 sheets ($\text{Nu}_x=0.453\,\text{Re}_x^{1/2}\text{Pr}^{1/3}$ laminar, $\text{Nu}_x=0.029\,\text{Re}_x^{0.8}\text{Pr}^{0.6}$ turbulent, both for a uniform flux). The 2022–23 and later sheets print $0.0308\,\text{Re}_x^{0.8}\text{Pr}^{1/3}$; both satisfy the 500 K limit for the chosen design.
- Q3 combines a uniform heat flux into the top face with an underside held at 300 K and a temperature-prescribed top boundary in the FD solve. These are not consistent with the conduction in the steel (see the reliability discussion in Q3(ii)).
- Corrections to the earlier draft of these solutions. The draft computed the air conductivity with $c_p=1005$ J/(kg K) instead of the front-page $1004.5$. With $1004.5$, $k=0.05479$ W/(m K) and every heat-transfer value moves in the last figure: $T_2=599.3$ K (was 599.4), $T_4=516.1$ K (516.2), $T_7=669.8$ K (669.9), $T_{10}=662.1$ K (662.2), $T_5=407.1$ K (407.2), $T_8=482.7$ K (unchanged) and $T_{11}=481.1$ K (481.2). The draft also stated that increasing $w$ to 0.226 m "gives extra margin below 500 K". The opposite holds: a larger area lowers $q''$, which raises $T_s$, and at $w=0.226$ m the solve gives $T_8=490.4$ K, less margin than at $w=0.20$ m.
