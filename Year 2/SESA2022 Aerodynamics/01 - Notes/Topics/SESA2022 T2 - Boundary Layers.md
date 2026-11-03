---
title: "SESA2022 T2 - Boundary Layers"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 2: Incompressible Viscous Flow"
order: 2
tags:
  - sesa2022
  - boundary-layers
  - viscous-flow
aliases: ["Boundary Layers", "Incompressible Viscous Flow"]
date: 2026-09-23
status: lectured
coverage: "Lectures 1, 5–10 (30 Sep – 15 Oct 2025)"
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
next_topics: ["[[SESA2022 T3 - Potential Flow]]"]
key_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]", "[[Law of the Wall]]", "[[Virtual Origin Method]]", "[[Boundary Layer Separation]]"]
tutorial_sheets: ["[[SESA2022 Tutorial 2 - Viscous Flow Solutions]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf", "02 - Sources/Lectures/SESA2022 Lecture 5.txt … Lecture 10.txt", "02 - Sources/BL/BLs.txt (earlier-year recording)"]
---

# SESA2022 T2 - Boundary Layers

> [!abstract] Summary
> The no-slip condition brings the fluid to rest at a wall, creating a thin boundary layer in which viscosity matters. Its integral thicknesses ($\delta^*$, $\theta$, $H$) and the momentum integral equation link its growth to skin-friction drag, $c_f = 2\,d\theta/dx$ and $D' = \rho U_\infty^2\theta$. The topic then covers approximate laminar and turbulent profiles, the law of the wall, transition by the virtual origin method, and separation under adverse pressure gradients, all for a flat plate at zero pressure gradient unless stated.

> [!summary]- Exam use: quick path
> - **Use it when:** you are given a velocity profile (formula or data), a plate or "flat-plate-like" body and asked for $\delta^*$, $\theta$, $H$, $c_f$, $C_F$, drag, $y^+$ or a transition/virtual-origin drag estimate.
> - **Assumptions:** incompressible, steady, 2D, zero pressure gradient ($U_e = U_\infty$), self-similar profile; correlations are per side and per unit span.
> - **Method:** 1. Compute $Re_x$ and decide laminar ($<3\times10^5$), transitional ($3\times10^5$–$10^6$) or turbulent. 2. Get $\delta^*/\delta$, $\theta/\delta$, $H$ by integrating the profile in $\eta = y/\delta$. 3. Apply the MIE, $\tau_w/\rho U_\infty^2 = d\theta/dx$, to get $\theta(x)$ and $c_f$ (or use the correlation table). 4. Drag: $D' = \rho U_\infty^2\theta(L)$ per side, then multiply by span and by 2 sides. 5. Transitional plate: virtual origin $x_0$, then $\theta$ at the trailing edge measured from $x_0$.
> - **Common mistakes:** forgetting the two sides of the plate (L7, ll. 658–663); mixing $c_f$ (local) with $C_F$ (whole plate) (L9, ll. 109–113).
> - **Exam format:** closed book with all formulae given. You must know which formula applies, the starting point of each derivation and its assumptions; derivations may appear with hints and variations (L1, ll. 499–511; L7, ll. 519–525; L8, ll. 13–19).
> - Revision-lecture advice (Revision 1, ll. 162–363): take $\delta^*/\delta$ and $\theta/\delta$ from the formula sheet and show the substitution $\eta = y/\delta$; for an MIE "show that", equate $c_f = 2\,d\theta/dx$ with $c_f$ from the wall gradient of the profile; a transition point means the virtual origin (the formula sheet gives the method as text, not a formula); *"Unless and until specified, find the drag for both sides of the plate"*; a power-law $n$ must be an integer.
> - **Practise:** [[#Worked example 3: thin foil with transition at mid-chord]] · [[SESA2022 Tutorial 2 - Viscous Flow Solutions]] Q4 · [[SESA2022 Exam 2024-25 Solutions]] Q1

Stand on a flat plate in a wind. The air touching the plate does not move (no slip), and the air far above moves at $U_\infty$. In between is a thin layer where the speed climbs from zero to $U_\infty$: the boundary layer. The plate drags on this layer through the wall shear stress $\tau_w = \mu\,\partial u/\partial y|_0$, and the layer drags on the plate equally and oppositely: that is skin-friction drag.

The slowed air is evidence of the drag. Momentum that the plate removed is "missing" from the profile, and the momentum thickness $\theta$ measures exactly how much is missing. So you can weigh the drag by looking at the profile at the trailing edge, without ever measuring $\tau_w$: $D' = \rho U_\infty^2\theta$ (L6, ll. 310–321). As the air travels downstream, more of it is slowed, so $\theta$ and $\delta$ grow; the rate of growth is the local shear, $c_f = 2\,d\theta/dx$.

A turbulent layer mixes fast air down towards the wall. Its profile is fuller, its wall gradient steeper, so $\tau_w$ and drag are larger (bad for drag), but the fast near-wall air can push further against rising pressure before stopping (good against separation). That trade-off — friction drag versus pressure drag — is why golf balls are dimpled and why we care where transition happens (L10, ll. 615–700).

---

## 1. No-slip condition and the boundary layer

- Molecules hitting a surface leave with (on average) the surface velocity, so the fluid velocity at the wall equals the wall velocity (L5, ll. 146–162).
- Any "slip" velocity is of order mean free path ($\sim10^{-8}$ m in air) × velocity gradient, which is negligible; and the no-slip condition is supported by repeated measurement rather than calculation (L5, ll. 163–168).
- **Exceptions**: rarefied flows where the Knudsen number (mean free path / body length) exceeds $0.01$, e.g. hypersonic and micro-fluidic flows (L5, ll. 169–175).

The BL develops from the leading edge as laminar, becomes unstable, transitions, and becomes fully turbulent. In a turbulent BL the velocity must be *time-averaged* at each point; a Pitot probe does this automatically because its frequency response is low.

![[bl_profiles.png|560]]

**Laminar vs turbulent profiles:**
- The turbulent BL is *fuller*: it recovers $U_\infty$ closer to the wall but is *thicker* overall.
- The turbulent BL has a larger wall velocity gradient, which gives a larger wall shear stress $\tau_w$ and so more skin-friction drag.

$$
\tau_w = \mu\left.\frac{\partial u}{\partial y}\right|_{y=0}, \qquad c_f = \frac{\tau_w}{\tfrac12\rho U_\infty^2} = \frac{2\nu}{U_\infty^2}\left.\frac{\partial u}{\partial y}\right|_{y=0}
$$

Laminar, transitional, turbulent (L5, ll. 189–212): a laminar BL is steady, so a probe at one point always reads the same velocity; a turbulent BL is unsteady and unpredictable in both time and space; transition is the region where both appear intermittently. Higher $Re$ (inertia dominating viscosity) favours turbulence (L7, ll. 285–292).

> [!note] Measuring the profile (BL lab)
> The lab uses a Pitot probe traversed away from a flat plate. It is intrusive, has a finite diameter (which limits how close to the wall you can resolve) and a low frequency response, so in a turbulent BL it reads a time average. A hot-wire anemometer resolves the fluctuations; PIV gives the whole field (L5, ll. 221–304; L8, ll. 224–236). Discuss these limits, and the accuracy of your measurements, in the report (L8, ll. 209–223).

The layer is thin because viscous diffusion spreads momentum a distance of order $\sqrt{\nu t}$ in time $t$. A particle reaches station $x$ after $t\approx x/U_\infty$, so $\delta\sim\sqrt{\nu x/U_\infty}$, or $\delta/x\sim Re_x^{-1/2}$. At $Re_x = 10^6$ that is about $10^{-3}$, which is why the outer flow can be treated as inviscid ([[SESA2022 T3 - Potential Flow]]). The Blasius constant 4.91 in §4 is the exact coefficient of this scaling.

## 2. Measures of boundary-layer thickness

See [[Displacement and Momentum Thickness]] for a short summary.

### Boundary-layer thickness

$\delta = \delta_{99}$ is the height where $u = 0.99\,U_\infty$ (L5, ll. 412–447). In data the 99% point usually falls between two measurement heights, so linearly interpolate (L6, ll. 143–146). Because the profile approaches $U_\infty$ asymptotically, $\delta_{99}$ is sensitive to noise; the integral thicknesses below are robust. $\delta$ is also the length used to non-dimensionalise the wall-normal position, and to judge how far a wind-tunnel wall or a CFD boundary must be from a body (L5, ll. 462–480).

### Displacement thickness: derivation

Assumptions: incompressible ($\rho$ constant), unit span, station $x$ fixed.

The real mass flow per unit span through a height $Y$ well outside the BL is

$$
\dot m_{real} = \int_0^Y\rho u\,dy.
$$

With no BL (inviscid flow, slip at the wall) it would be

$$
\dot m_{ideal} = \int_0^Y\rho U_\infty\,dy.
$$

The deficit is

$$
\dot m_{ideal}-\dot m_{real} = \int_0^Y\rho\,(U_\infty-u)\,dy.
$$

Define $\delta^*$ as the height of a strip of inviscid flow carrying the same deficit:

$$
\rho U_\infty\delta^* = \int_0^Y\rho\,(U_\infty-u)\,dy.
$$

Divide by $\rho U_\infty$ and let $Y\to\infty$ (the integrand is zero outside the BL):

$$
\boxed{\delta^* = \int_0^\infty\left(1-\frac{u}{U_\infty}\right)dy}
$$

So $\delta^*$ is how far the wall must be displaced outwards in an inviscid calculation to pass the same mass flow (L5, ll. 683–770). Adding $\delta^*$ to a body is how a potential-flow calculation "sees" the BL.

### Momentum thickness: derivation

The fluid that does pass through the profile, mass flow $\rho u\,dy$ per strip, would carry momentum $\rho u\,U_\infty\,dy$ with no BL, but actually carries $\rho u\,u\,dy$. The momentum deficit is

$$
\int_0^\infty\rho u\,(U_\infty-u)\,dy.
$$

Define $\theta$ as the height of a strip of inviscid flow with the same momentum flux $\rho U_\infty^2\theta$:

$$
\rho U_\infty^2\theta = \int_0^\infty\rho u\,(U_\infty-u)\,dy.
$$

Divide by $\rho U_\infty^2$:

$$
\boxed{\theta = \int_0^\infty\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dy}
$$

> [!important] The two integrands differ by the factor $u/U_\infty$
> $\delta^*$ counts the mass deficit of every strip. $\theta$ counts the momentum deficit of the fluid that actually flows. Since $0\le u/U_\infty\le1$, the $\theta$ integrand is always smaller, so $\theta<\delta^*$ and $H>1$ for every profile.

![[bl_thickness_meanings.png|900]]

### Shape factor and non-dimensional form

$$
H = \frac{\delta^*}{\theta}
$$

Laminar $H>2$ (Blasius $2.59$); turbulent $H<2$ (power law $1.29$). This is how you identify the state of a measured BL (L6, ll. 114–123; "definitely" a quiz question, l. 121).

With $\eta = y/\delta$ so $dy = \delta\,d\eta$, and $u/U_\infty = f(\eta)$ with $f = 1$ for $\eta\ge1$:

$$
\frac{\delta^*}{\delta} = \int_0^1\left(1-f\right)d\eta,\qquad \frac{\theta}{\delta} = \int_0^1 f\left(1-f\right)d\eta
$$

The upper limit is 1 because both integrands vanish above the BL edge.

| Quantity | Definition | Meaning |
|---|---|---|
| $\delta = \delta_{99}$ | $u(\delta_{99}) = 0.99\,U_\infty$ | Edge of the BL (interpolate in data) |
| $\delta^*$ | $\displaystyle\int_0^\infty\left(1-\frac{u}{U_\infty}\right)dy$ | Wall displacement giving the same mass-flow deficit |
| $\theta$ | $\displaystyle\int_0^\infty\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dy$ | Momentum deficit, directly proportional to the drag |
| $H$ | $\delta^*/\theta$ | Laminar $H>2$, turbulent $H<2$ |

The lecture evaluates these quantities from measured data with a function `bl_prop(U, y)` (L6, ll. 139–198), which you may reuse in the lab report (L9, ll. 306–315). It works in five steps:

1. read the `.csv` with `pandas` and convert mm to m (L5, ll. 491–529);
2. take $U_\infty$ as the largest measured velocity;
3. find $\delta_{99}$ with `np.interp` between the two points either side of $0.99U_\infty$ (L5, ll. 582–591);
4. estimate $\tau_w = \mu(u_1-u_0)/(y_1-y_0)$ from the wall point and the first measured point;
5. integrate $\delta^*$ and $\theta$ by the trapezoidal rule (`np.trapz`) up to $\delta$, then form $H$.

Step 4 is a secant through a curved profile, so it underestimates $\tau_w$, badly if the first point is far from the wall (L5, ll. 619–642; L8, ll. 568–580); the integral quantities are much less sensitive. Your measured data will be noisier than the lecture `.csv`, so explain the errors rather than hiding them (L5, ll. 554–570).

## 3. Momentum integral equation and drag

Assumptions (L6, ll. 254–272): flat plate of unit depth, steady, incompressible, no pressure gradient (so $p = p_\infty$ on all faces and the only $x$-force on the fluid is the wall shear), 2D.

![[bl_mie_control_volume.png|900]]

Take a control volume bounded by the plate ($0\le x\le L$), the inlet face at the leading edge (height $h$), the outlet face at $x = L$ (height $\delta$) and the streamline that leaves the inlet at height $h$ and reaches the outlet at $\delta$. No mass crosses a streamline.

### Step 1: mass conservation fixes h

Mass in through the inlet equals mass out through the outlet:

$$
\rho U_\infty h = \int_0^\delta\rho u\,dy.
$$

Cancel $\rho$:

$$
h = \int_0^\delta\frac{u}{U_\infty}\,dy.
$$

### Step 2: x-momentum balance

Net $x$-force on the fluid = momentum flux out − momentum flux in. The plate exerts $-D'$ on the fluid (upstream), where $D' = \int_0^L\tau_w\,dx$:

$$
-D' = \int_0^\delta\rho u^2\,dy-\rho U_\infty^2h.
$$

Rearrange:

$$
D' = \rho U_\infty^2h-\int_0^\delta\rho u^2\,dy.
$$

### Step 3: eliminate h

Substitute Step 1:

$$
D' = \rho U_\infty^2\int_0^\delta\frac{u}{U_\infty}\,dy-\int_0^\delta\rho u^2\,dy.
$$

Take $\rho U_\infty^2$ outside both integrals:

$$
D' = \rho U_\infty^2\int_0^\delta\left[\frac{u}{U_\infty}-\frac{u^2}{U_\infty^2}\right]dy.
$$

Factor the integrand:

$$
D' = \rho U_\infty^2\int_0^\delta\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dy.
$$

Recognise $\theta(L)$:

$$
\boxed{D'(L) = \rho U_\infty^2\,\theta(L)}\qquad\text{(drag per unit span, one side, from the leading edge to }L\text{)}
$$

### Step 4: local form

$L$ was arbitrary, so write $x$. Differentiate with $dD'/dx = \tau_w$:

$$
\tau_w = \rho U_\infty^2\frac{d\theta}{dx}.
$$

Divide by $\tfrac12\rho U_\infty^2$:

$$
\boxed{c_f = 2\frac{d\theta}{dx}}
$$

The whole-plate coefficient, using $D'(L)$:

$$
C_F = \frac{D'}{\tfrac12\rho U_\infty^2 L} = \frac{\rho U_\infty^2\theta(L)}{\tfrac12\rho U_\infty^2L}
$$

$$
\boxed{C_F = \frac{2\,\theta(L)}{L} = \frac1L\int_0^L c_f\,dx}
$$

- A plate or wing has two sides: double the drag (L7, ll. 658–663), unless the question asks for one side.
- Real bodies have span $b$: $D = bD'$ and $S = bL$, so $b$ cancels in $C_F$ (L7, ll. 619–625; L9, ll. 141–151). State your assumption for the third dimension (L9, ll. 122–132).
- The doubling and the simple $C_F = 2\theta/L$ hold for a flat plate; with curvature or a pressure gradient the equation changes (L6, ll. 384–414).
- The same $\theta$–drag relation gives the drag of a body from its wake: integrate $\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)$ across the wake, from $-w$ to $w$ (the wake width, beyond which the flow is undisturbed), far enough downstream that $p = p_\infty$. It works in 3D too: race-car teams measure drag this way when a balance is impractical (L6, ll. 424–463; Tutorial 2 Q5).
- With a pressure gradient the MIE gains a term, $\dfrac{d\theta}{dx}+(2+H)\dfrac{\theta}{U_e}\dfrac{dU_e}{dx} = \dfrac{c_f}{2}$. That is not lectured in SESA2022; it is derived in [[SESA3043 3.5 - Momentum Integral Equation]].

> [!check] Physical check
> $D'(L)$ depends only on $\theta$ at $L$, not on what happened upstream. Two plates with the same trailing-edge $\theta$ have the same drag, whatever their transition history. The virtual-origin method in §7 uses exactly this.

## 4. Approximate laminar profiles

Self-similarity (Blasius, 1908): profiles $u/U_\infty$ vs $y/\delta(x)$ collapse at every $x$ (L6, ll. 567–612; L7, ll. 480–493). So a single function $f(\eta)$ describes the whole laminar layer, and similarly for a turbulent layer, but you cannot mix laminar and turbulent scalings.

### General recipe for any assumed profile

Assumptions: zero pressure gradient, profile $u/U_\infty = f(\eta)$ with $f(0)=0$, $f(1)=1$.

Write $\theta = \hat\theta\,\delta$ with $\hat\theta = \int_0^1f(1-f)\,d\eta$.

Wall shear, using $\partial u/\partial y = (U_\infty/\delta)\,f'(\eta)$:

$$
\tau_w = \frac{\mu U_\infty}{\delta}f'(0).
$$

MIE, $\tau_w = \rho U_\infty^2\,d\theta/dx$:

$$
\rho U_\infty^2\frac{d\theta}{dx} = \frac{\mu U_\infty}{\delta}f'(0).
$$

Divide by $\rho U_\infty^2$ and use $\delta = \theta/\hat\theta$:

$$
\frac{d\theta}{dx} = \frac{\nu f'(0)\hat\theta}{U_\infty\theta}.
$$

Separate variables:

$$
\theta\,d\theta = \frac{\nu f'(0)\hat\theta}{U_\infty}dx.
$$

Integrate from the leading edge, $\theta(0) = 0$:

$$
\frac{\theta^2}{2} = \frac{\nu f'(0)\hat\theta}{U_\infty}x.
$$

Solve and divide by $x$:

$$
\boxed{\frac{\theta}{x} = \frac{\sqrt{2f'(0)\hat\theta}}{\sqrt{Re_x}}},\qquad Re_x = \frac{U_\infty x}{\nu}
$$

Then $c_f = 2\,d\theta/dx$. Since $\theta\propto\sqrt x$, $d\theta/dx = \theta/(2x)$, so

$$
c_f = \frac{\theta}{x}\qquad(\text{same coefficient as }\theta/x\text{ for every laminar profile}).
$$

And $\delta/x = (\theta/x)/\hat\theta$, $\delta^*/x = H\,\theta/x$.

### Linear profile (lectured)

Profile $u/U_\infty = \eta$ (L7, ll. 294–448).

$$
\frac{\delta^*}{\delta}=\int_0^1(1-\eta)\,d\eta=\tfrac12
$$

$$
\frac{\theta}{\delta}=\int_0^1\eta(1-\eta)\,d\eta = \tfrac12-\tfrac13=\tfrac16
$$

$$
H = \frac{1/2}{1/6} = 3
$$

With $f'(0) = 1$, $\hat\theta = 1/6$: $\sqrt{2\cdot1\cdot\tfrac16} = \sqrt{1/3} = 0.577$.

$$
\frac{\theta}{x}=\frac{0.577}{\sqrt{Re_x}},\qquad \frac{\delta}{x} = \frac{3.46}{\sqrt{Re_x}},\qquad \frac{\delta^*}{x}=\frac{1.732}{\sqrt{Re_x}},\qquad c_f=\frac{0.577}{\sqrt{Re_x}}
$$

### Parabolic profile (lecture homework)

Profile $u/U_\infty = 2\eta-\eta^2$; Tutorial 2 Q3 and 2024-25 Q1.

Set as homework: *"take a parabolic profile and try to derive this"* (L7, ll. 506–513).

$$
1-f = 1-2\eta+\eta^2 = (1-\eta)^2
$$

$$
\frac{\delta^*}{\delta} = \int_0^1(1-\eta)^2d\eta = \tfrac13
$$

$$
f(1-f) = (2\eta-\eta^2)(1-\eta)^2
$$

Expand: $(2\eta-\eta^2)(1-2\eta+\eta^2) = 2\eta-5\eta^2+4\eta^3-\eta^4$.

$$
\frac{\theta}{\delta} = 1-\tfrac53+1-\tfrac15 = \tfrac{2}{15}
$$

$$
H = \frac{1/3}{2/15} = \frac{5}{2} = 2.5
$$

With $f'(0) = 2$, $\hat\theta = 2/15$: $\sqrt{2\cdot2\cdot\tfrac{2}{15}} = \sqrt{8/15} = 0.730$.

$$
\frac{\theta}{x} = \frac{0.730}{\sqrt{Re_x}},\qquad \frac{\delta}{x} = \frac{5.48}{\sqrt{Re_x}},\qquad \frac{\delta^*}{x} = \frac{1.83}{\sqrt{Re_x}},\qquad c_f = \frac{0.730}{\sqrt{Re_x}}
$$

### Blasius (exact) solution

Solving the boundary-layer equations exactly (not derived in the module) gives

$$
\frac{\delta}{x}=\frac{4.91}{\sqrt{Re_x}},\quad \frac{\delta^*}{x}=\frac{1.721}{\sqrt{Re_x}},\quad \frac{\theta}{x}=\frac{0.664}{\sqrt{Re_x}},\quad H=2.59,\quad c_f=\frac{0.664}{\sqrt{Re_x}},\quad C_F = \frac{1.328}{\sqrt{Re_L}}
$$

$C_F$ follows from $C_F = 2\theta(L)/L = 2(0.664)/\sqrt{Re_L}$.

![[bl_profile_family.png|640]]

> [!warning] Which laminar constants to use
> If a question says only "laminar", use Blasius ($0.664$, $1.328$, $4.91$) (L7, ll. 646–653). Use the linear or parabolic results only when the question gives that profile. The lecture calls $0.664$ *"the one that Blasius gave us for the parabolic profile"* (L7, ll. 646–648); that is a slip: the parabola gives $0.730$, Blasius is the exact solution. The same confusion recurs (L8, ll. 8–10; L10, ll. 69–71). See [[#Transcript slips (Lectures 5–10)]].

> [!check] Accuracy of the approximate profiles (Python, SymPy)
> $\theta/x\cdot\sqrt{Re_x}$: linear $0.577$ ($-13\%$ vs Blasius), parabolic $0.730$ ($+10\%$). $H$: $3.00$ and $2.50$ vs $2.59$. Even a crude profile gives the right $Re_x^{-1/2}$ law and the right order of magnitude: the MIE is forgiving because it only needs integrals of the profile.

## 5. Turbulent boundary layers

Properties of turbulence (L8, ll. 50–159):
- Chaotic and unsteady, but with structure: a wide range of interacting eddies, energy passing from large to small scales. The ratio of largest to smallest scales grows with $Re$.
- Real flows (aerofoils, fuselages) are almost always turbulent, so predicting turbulent drag matters.

Tools (a trade-off between accuracy and cost):

| Tool | What it does | Cost |
|---|---|---|
| Force/pressure measurements, Pitot | Mean quantities | Low |
| Hot-wire, PIV | Fluctuations, full field | Medium to high |
| RANS | Solve the mean flow and *model* all turbulence (closure: $k$–$\omega$, $k$–$\epsilon$, SA) | Low |
| LES | Resolve large eddies and model small ones | High |
| DNS | Resolve all scales; limited to low $Re$ | Very high |

### Power-law profile: integrals for general n

$$
\frac{u}{U_\infty} = \eta^{1/n}\quad(n \approx 7\text{, found by fitting data, L8, ll. 329–421})
$$

Displacement thickness:

$$
\frac{\delta^*}{\delta} = \int_0^1\left(1-\eta^{1/n}\right)d\eta = 1-\frac{1}{1+1/n} = 1-\frac{n}{n+1}
$$

$$
\frac{\delta^*}{\delta} = \frac{1}{n+1}
$$

Momentum thickness:

$$
\frac{\theta}{\delta} = \int_0^1\left(\eta^{1/n}-\eta^{2/n}\right)d\eta = \frac{n}{n+1}-\frac{n}{n+2}
$$

$$
\frac{\theta}{\delta} = \frac{n}{(n+1)(n+2)}
$$

Shape factor:

$$
H = \frac{1/(n+1)}{n/[(n+1)(n+2)]} = \frac{n+2}{n}
$$

With $n=7$: $\delta^*/\delta = 1/8$, $\theta/\delta = 7/72$, $H = 9/7 \approx 1.29$.

> [!warning] The power law cannot give the wall shear
> $\dfrac{\partial u}{\partial y} = \dfrac{U_\infty}{n\delta}\eta^{1/n-1}\to\infty$ as $\eta\to0$ for $n>1$. So the power law predicts infinite $\tau_w$ (*"You can try it out at home"*, L8, ll. 541–560). It describes the outer part of the layer, not the wall. Use an empirical $c_f$ correlation, or the [[Law of the Wall]].

Once $n$ is known at one station, the same $n$ applies at other stations of the same flow (self-similarity) (L8, ll. 524–526).

### Finding n from data (lecture method)

1. Normalise: $\eta = y/\delta$, $f = u/U_\infty$.
2. Keep only the points inside the BL: find the first index with $y/\delta>1$ (`np.where`) and fit up to the point before it. The traverse usually runs to 2–4$\delta$; fitting all of it gives a poor fit, the commonest error in the tutorials and quizzes (L8, ll. 394–483).
3. Fit $f = \eta^{1/n}$ with `scipy.optimize.curve_fit`; the lecture data give $n = 7.12$, rounded to $7$ (L8, ll. 386–424).
4. Use your $n$. *"If you have no data ... you can assume 7"*, but assuming 7 when data are given loses marks (L8, ll. 514–522, 642–657).

### Where the turbulent correlations come from (suggested, not lectured)

The course states the turbulent correlations as "$n = 7$ plus data". The textbook route shows where the $Re_x^{-1/5}$ comes from. Assumptions: $1/7$ law for $\theta$, plus the empirical Blasius pipe-flow wall-shear law $\tau_w = 0.0225\rho U_\infty^2(\nu/U_\infty\delta)^{1/4}$ (borrowed because the power law cannot supply $\tau_w$).

MIE with $\theta = \tfrac{7}{72}\delta$:

$$
\frac{7}{72}\frac{d\delta}{dx} = 0.0225\left(\frac{\nu}{U_\infty\delta}\right)^{1/4}.
$$

Separate:

$$
\delta^{1/4}d\delta = 0.2314\left(\frac{\nu}{U_\infty}\right)^{1/4}dx.
$$

Integrate from $\delta(0) = 0$ (fully turbulent from the leading edge):

$$
\frac45\delta^{5/4} = 0.2314\left(\frac{\nu}{U_\infty}\right)^{1/4}x.
$$

Raise to the power $4/5$ and divide by $x$:

$$
\frac{\delta}{x} = (0.2893)^{4/5}\left(\frac{\nu}{U_\infty x}\right)^{1/5} = \frac{0.37}{Re_x^{1/5}}.
$$

Then $\theta/x = \tfrac{7}{72}(0.37)Re_x^{-1/5} = 0.036\,Re_x^{-1/5}$, $c_f = 2\,d\theta/dx = 2\cdot\tfrac45\,\theta/x = 0.058\,Re_x^{-1/5}$, and $C_F = 2\theta(L)/L = 0.072\,Re_L^{-1/5}$.

The course table below uses slightly larger coefficients fitted to data ($0.38$, $0.037$, $0.059$, $0.074$). Use the course values unless the paper gives others (some past papers use $0.036$).

### Summary of flat-plate correlations

Use these only if you cannot get the values directly from the data.

| Property | Laminar (Blasius) | Turbulent ($n=7$ + data) |
|---|---|---|
| $\delta/x$ | $4.91/\sqrt{Re_x}$ | $0.38/Re_x^{1/5}$ |
| $\delta^*/x$ | $1.72/\sqrt{Re_x}$ | $0.048/Re_x^{1/5}$ |
| $\theta/x$ | $0.664/\sqrt{Re_x}$ | $0.037/Re_x^{1/5}$ |
| $c_{f}$ | $0.664/\sqrt{Re_x}$ | $0.059/Re_x^{1/5}$ |
| $C_F$ (one side) | $1.328/\sqrt{Re_L}$ | $0.074/Re_L^{1/5}$ |
| $H$ | $2.59$ | $1.29$ |

![[bl_cf_transition.png|560]]

A turbulent layer grows faster but its $c_f$ falls more slowly. Laminar $\delta\propto x^{1/2}$ against turbulent $\delta\propto x^{4/5}$, because mixing thickens the layer quickly; laminar $c_f\propto Re_x^{-1/2}$ against turbulent $c_f\propto Re_x^{-1/5}$, so on the log–log plot above the turbulent line is flatter and higher, and at $Re_x = 10^6$ the turbulent $c_f$ is about five times the laminar one.

**Fitting correlations to data**: assume $C_F = A\,Re^{b}$ and fit with `curve_fit`. The argument order matters: `curve_fit(f, Re, CF)` with `f(Re, A, b)` (L9, ll. 251–261). The lecture data gave $A = 0.0729$, $b = -0.197$, close to $0.074$ and $-1/5$ (L9, ll. 237–266). In the report, compare your fit with the $n = 7$ correlations and explain the difference (L9, ll. 273–279).

Tools for turbulent flows (L8, ll. 242–322): DNS resolves everything (low $Re$ only), LES resolves the large eddies and models the small, RANS averages and models all fluctuations (used in SESA2029). Lifting-line theory, panel methods, XFOIL and XFLR5 sit at the cheap end. Always ask *"what can I get away with and what am I giving up?"*

## 6. Law of the wall

The outer scaling ($U_\infty$, $\delta$) hides the near-wall physics. Instead, use inner (wall, "plus") units (L9, ll. 378–407):

$$
U_\tau = \sqrt{\frac{\tau_w}{\rho}},\qquad l = \frac{\nu}{U_\tau},\qquad U^+ = \frac{U}{U_\tau},\qquad y^+ = \frac{y}{l} = \frac{yU_\tau}{\nu}
$$

The lecture calls $U_\tau$ the skin friction velocity (L9, ll. 384, 407).

$U_\tau$ from $c_f$: since $\tau_w = \tfrac12\rho U_\infty^2c_f$,

$$
U_\tau = \sqrt{\tfrac12U_\infty^2c_f} = U_\infty\sqrt{\frac{c_f}{2}}.
$$

$$
U^+ = \begin{cases} y^+ & y^+ < 5 \quad\text{(viscous sub-layer)}\\[4pt] \dfrac{1}{\kappa}\ln y^+ + B & y^+ > 50 \text{ and } y/\delta < 0.2\quad\text{(log layer)}\end{cases}
$$

**Viscous sub-layer derivation.** Very close to the wall the shear stress is approximately constant and equal to $\tau_w$, and turbulence is suppressed, so $\tau_w = \mu\,du/dy$. Integrate from $u(0) = 0$:

$$
U = \frac{\tau_w}{\mu}y.
$$

Divide by $U_\tau$ and use $\tau_w = \rho U_\tau^2$:

$$
\frac{U}{U_\tau} = \frac{\rho U_\tau^2y}{\mu U_\tau} = \frac{yU_\tau}{\nu}\quad\Rightarrow\quad U^+ = y^+.
$$

- Slides: $\kappa = 0.4$, $B = 5.0$ (L9, l. 427). 2024-25 exam rubric: $\kappa = 0.39$, $B = 4.3$. The constants are empirical, so use whatever the paper gives.
- $5 < y^+ < 50$ is the buffer layer, where neither law fits. In data the log law often fits from $y^+\approx30$ (L9, ll. 450–465).
- **CFD**: put at least one grid point in the viscous sub-layer, $y^+ < 5$ (often $y^+\approx1$). Estimate $U_\tau$ from the flat-plate $c_f$ correlation, run the simulation, then check (L9, ll. 469–480, 492–493).
- **Lab**: compute $y^+$ for your measured points. If none lie in the sub-layer, say so, and describe your curve-fitting choices (a sensitivity check) (L9, ll. 479–491).

![[bl_law_of_wall.png|600]]

> [!example] Example (lecture, L9, ll. 492–531)
> Turbulent profile: estimate $c_f$ from the correlation, then $U_\tau = U_\infty\sqrt{c_f/2}$. At $y = 1$ mm: $y^+ = 55$ and $y/\delta = 0.2$ (0.21 from the data). Both conditions are only just met, so the point is borderline buffer/log. If you accept the log law, $U = U_\tau\left(\tfrac{1}{\kappa}\ln 55 + B\right) = U_\tau(10.0+5.0) = 15.0\,U_\tau$.

## 7. Transition and the virtual origin method

On a log–log plot, laminar $c_f$ has slope $-1/2$ and turbulent $c_f$ has slope $-1/5$. No real flow follows either line all the way: it leaves the laminar line at transition and joins the turbulent one (L10, ll. 105–125). Transitional Reynolds number for a smooth plate: $Re_{x_T} \approx 3\times10^5$ to $10^6$. *"This number may not be given in your formula sheet"* (L10, ll. 306–318).

Why bother: assuming the whole plate laminar underestimates the drag, assuming it all turbulent overestimates it (L10, ll. 124–134).

### The model (see [[Virtual Origin Method]])

1. **Assumption**: $\theta$ is continuous at transition, $\theta_{lam}(x_T) = \theta_{turb}(x_T)$ (L10, ll. 227–229, 290).
2. The turbulent layer grows as if it had started, fully turbulent, at a virtual origin $x_0 < x_T$; turbulent formulas use $x-x_0$ in place of $x$ (L10, ll. 203–266).
3. The drag of the whole plate comes from the trailing-edge turbulent $\theta$ measured from $x_0$ (§3: drag depends only on the trailing-edge $\theta$).

![[bl_virtual_origin.png|560]]

### Matching condition

Laminar side at $x_T$ (Blasius):

$$
\theta_{lam}(x_T) = \frac{0.664\,x_T}{\sqrt{U_\infty x_T/\nu}}.
$$

Turbulent side, from $x_0$:

$$
\theta_{turb}(x_T) = \frac{0.037\,(x_T-x_0)}{\left[U_\infty(x_T-x_0)/\nu\right]^{1/5}}.
$$

Equate them. Simplify each side using $Re_{x_T} = U_\infty x_T/\nu$ and write $\xi = (x_T-x_0)/x_T$:

$$
0.664\,x_T\,Re_{x_T}^{-1/2} = 0.037\,\xi x_T\,(\xi Re_{x_T})^{-1/5}.
$$

Cancel $x_T$ and collect powers of $\xi$:

$$
\xi^{4/5} = \frac{0.664}{0.037}Re_{x_T}^{-1/2+1/5} = 17.95\,Re_{x_T}^{-3/10}.
$$

Raise to the power $5/4$:

$$
\xi = 17.95^{5/4}Re_{x_T}^{-3/8} = 36.9\,Re_{x_T}^{-3/8}.
$$

So

$$
\boxed{x_0 = x_T\left(1-36.9\,Re_{x_T}^{-3/8}\right)}\qquad(\text{or }38.2\text{ with the }0.036\text{ coefficient})
$$

The slides' "last resort" $x_0 \approx x_T\left(1-38\,Re_{x_T}^{-3/8}\right)$ is this result with $0.036$ (L10, ll. 319–326).

Given $x_T$, the formula above is explicit for $x_0$. The lecture example runs the other way: $x_0$ comes from fitting turbulent data, and $x_T$ is the unknown, appearing as $x_T^{1/2}$ and $(x_T-x_0)^{4/5}$, so the lecture uses `fsolve` (L10, ll. 375–447). In an exam you will be given the relation and won't be expected to solve the high-order equation by hand (L10, ll. 334–336, where the transcript's "want" should read "won't").

### Drag of the transitional plate

$$
D' = \rho U_\infty^2\,\theta(c-x_0),\qquad \frac{\theta(c)}{c-x_0} = \frac{0.037}{Re_{c-x_0}^{1/5}}
$$

$$
C_F = \frac{2\theta(c)}{c} = 0.074\left(1-\frac{x_0}{c}\right)Re_{c-x_0}^{-1/5}\quad\text{(one side)}
$$

> [!example] Lecture example (L10, ll. 375–452)
> $L = 0.3$ m. From the turbulent data, $x_0 \approx 0.18$ m, and matching with the laminar $\theta$ gives $x_T \approx 0.28$ m, i.e. transition near the end of the plate. Check: $Re_{x_T}$ lies in $3\times10^5$–$10^6$ ✔ (L10, ll. 452–459).

`fsolve`'s answer depends on the starting guess (L10, ll. 399–451), so try several and accept the value they all converge to. Then sanity-check it: $x_0$ must lie between 0 and $x_T$ (0.187 m on the 0.3 m lecture plate), $x_T$ must lie on the plate (0.28 m), and $Re_{x_T}$ must fall in $3\times10^5$–$10^6$. Compare with the explicit approximation, as Tutorial 2 Q5 does (L10, ll. 461–477).

Delaying transition reduces friction drag (L10, ll. 517–560). Passive methods: distributed roughness and bio-inspired surfaces (riblets or shark skin, whale-flipper tubercles). Active methods: e.g. plasma actuators, which the lecture describes as ionising the near-wall layer; more precisely, a DBD actuator adds momentum near the wall through an ionic-wind body force. Harder in high-speed flows because of shocks; transition can be delayed but not eliminated (ll. 560–564).

## 8. Pressure gradients and separation

- Favourable pressure gradient (FPG): $dp/dx < 0$, which accelerates the flow (L10, l. 572).
- Adverse pressure gradient (APG): $dp/dx > 0$, which decelerates the flow everywhere, including near the wall where there is least momentum. Eventually $\partial u/\partial y|_{y=0} = 0$, so $\tau_w = 0$, and the flow separates (L10, ll. 569–601). On aerofoils this is stall, and once the flow separates the aerofoil loses circulation (L10, ll. 605, 633).
- A laminar BL separates earlier because it has less near-wall momentum, giving a bigger separated region (L10, l. 619).
- Tripping to turbulent increases mixing and delays separation, giving a smaller wake and lower pressure drag, at the cost of higher friction (L10, ll. 637–656). Examples: golf-ball dimples, trips on wind-tunnel models.
- **Bluff bodies**: early separation leads to vortex shedding and unsteady forces. Sharp corners separate immediately, so bodies are streamlined (L10, l. 700).

> [!warning] Separation needs viscosity
> The lecture puts it as the APG leading to *"zero viscous forces ... if there's no viscosity, if there's no shear stress, your flow will just go off the rails"* (L10, ll. 593–600). The cause is the opposite: friction has already drained the near-wall fluid of momentum, so the APG can stop and reverse it. Separation is where the wall shear passes through zero, $\partial u/\partial y|_0 = 0$. A truly inviscid flow has no boundary layer and does not separate ([[D'Alembert's Paradox]]).

> [!warning] "Turbulence always increases drag" is false
> Turbulence always increases skin-friction drag at a given $Re$ on an attached flow. On a bluff body, where pressure drag dominates, tripping can reduce the total drag by delaying separation. State which drag component you mean.

See [[Boundary Layer Separation]] and [[D'Alembert's Paradox]].

---

## 9. Worked examples

### Worked example 1: laminar UAV wing (lecture, L7, ll. 570–710)

Wing chord $c = 0.2$ m, span $b = 1.2$ m, speeds 6–15 m/s, fully laminar, flat-plate model, two sides. $\rho = 1.225$ kg/m³, $\nu = 1.5\times10^{-5}$ m²/s.

1. Range: $Re_c = Uc/\nu$ from $6(0.2)/1.5\times10^{-5} = 8\times10^4$ to $2\times10^5$, laminar ✔.
2. At 12 m/s: $Re_c = 12(0.2)/1.5\times10^{-5} = 1.6\times10^5$.
3. $C_F = 1.328/\sqrt{1.6\times10^5} = 1.328/400 = 0.00332$ per side.
4. $D = 2\times\tfrac12\rho U^2(bc)\,C_F = 2(0.5)(1.225)(144)(0.24)(0.00332) = 0.141$ N.

$C_F$ falls as $Re$ rises (as $Re^{-1/2}$), but drag still rises with speed (as $U^{3/2}$): *"a physical insight that you must be able to reproduce"* (L7, ll. 699–710).

### Worked example 2: AUV, fully turbulent (lecture, L9, ll. 104–160)

$c = 3$ m, $U = 2$ m/s in water ($\nu = 10^{-6}$ m²/s), flat-plate model.

1. $Re_c = 2(3)/10^{-6} = 6\times10^6$, turbulent.
2. $C_F = 0.074/Re_c^{1/5} = 0.074/(6\times10^6)^{0.2} = 0.074/22.7 = 0.0033$ per side.

### Worked example 3: thin foil with transition at mid-chord

Tutorial 2 Q4: symmetric thin foil at $\alpha = 0$, $Re_c = 6\times10^5$, transition at $x_T = 0.5c$, unit chord.

1. $Re_{x_T} = 0.5(6\times10^5) = 3\times10^5$.
2. $\xi = 36.9\,(3\times10^5)^{-3/8} = 36.9/113.2 = 0.326$.
3. $x_0 = 0.5c(1-0.326) = 0.337c$.
4. $Re_{c-x_0} = 6\times10^5(0.663) = 3.98\times10^5$.
5. $\theta_{TE} = 0.037(0.663c)(3.98\times10^5)^{-0.2} = 1.86\times10^{-3}c$.
6. Both sides: $C_F = 2\times2\theta_{TE}/c = 0.0074$. With the $0.036$ coefficient used in the tutorial, $0.0073$ (the given answer).

> [!check] Bracketing check
> Fully laminar both sides: $2(1.328)/\sqrt{6\times10^5} = 0.0034$. Fully turbulent: $2(0.074)/(6\times10^5)^{0.2} = 0.0105$. The transitional value $0.0074$ sits between them ✔. Python: $x_0 = 0.3369c$, $\theta_{TE} = 1.861\times10^{-3}c$, $C_F = 0.00745$.

### Worked example 4: riblet sizing (2023-24 Part A Q1v)

Riblets 10 wall units high on a plate: $U_0 = 15$ m/s, $X = 3$ m, $\nu = 1.5\times10^{-5}$ m²/s, turbulent.

1. $Re = 15(3)/1.5\times10^{-5} = 3\times10^6$.
2. $c_f = 0.059(3\times10^6)^{-0.2} = 0.002988$.
3. $U_\tau = 15\sqrt{0.002988/2} = 0.580$ m/s.
4. $h = 10\nu/U_\tau = 10(1.5\times10^{-5})/0.580 = 258.7\ \mu$m.

### Worked example 5: Remus-100 AUV control surfaces (Tutorial 2 Q2)

$L = 1.6$ m, $U = 2$ m/s, $\nu = 10^{-6}$: $Re_L = 3.2\times10^6$ (turbulent). Laminar would give $\delta = 4.91L/\sqrt{Re_L} = 4.4$ mm; turbulent gives $\delta = 0.38L/Re_L^{1/5} = 30.4$ mm. Use a safety factor because the correlation is empirical.

> [!check] Python check
> All five examples recomputed in Python (NumPy): $0.1406$ N; $0.00326$; $0.00745$; $258.7\ \mu$m; $4.39$ mm and $30.4$ mm ✔.

More in [[SESA2022 Tutorial 2 - Viscous Flow Solutions]] and the exam solutions linked from [[SESA2022 Past Paper Map]].

## Transcript slips (Lectures 5–10)

> [!warning] Slips in `SESA2022 Lecture 5.txt` to `Lecture 10.txt` (Whisper transcripts)
> Recurring transcriptions: *"CESA"* = SESA, *"lens scale"* = length scale, *"XNert"*/*"X naught"* = $x_0$, *"copper"* = kappa ($\kappa$), *"cord"* = chord.
>
> | Line | Said | Correct |
> |---|---|---|
> | L6, l. 288 | momentum at the inlet *"is rho u infinity, the free stream velocity, times h"* | $\rho U_\infty^{2}h$ (momentum flux) ([[#Step 2: x-momentum balance]]) |
> | L7, ll. 496–502 | the parabolic profile gives a shape factor of *"2.59 or 2.6"* | the parabola gives $H = 2.5$; $2.59$ is Blasius ([[#Parabolic profile (lecture homework)]]) |
> | L7, ll. 646–648 | $0.664/\sqrt{Re}$ is *"the one that Blasius gave us for the parabolic profile"* | Blasius is the exact similarity solution; the parabola gives $0.730$ |
> | L8, l. 330 | *"u over u infinity is … y over delta times 1 over n"* | $(y/\delta)^{1/n}$, a power, as corrected at l. 358 |
> | L9, l. 403 | *"y plus is nothing but y over L … y u tau"* over *u* (l. 433) | $y^+ = yU_\tau/\nu$ (kinematic viscosity, not velocity) |
> | L9, l. 419 | the log region is *"a linear log format"* | linear in $\ln y^+$: $U^+ = \frac1\kappa\ln y^++B$ |
> | L10, l. 336 | *"I want to expect you to do the fifth order equation in your exam"* | won't expect it; the relation for $x_0$ and $x_T$ will be given (ll. 334–335, 461–462) |
> | L10, l. 215 | *"take this whole plate as per view of the short one"* | garbled; the equivalent turbulent plate runs from $x_0$ to $c$ (ll. 219, 360–361) |
> | L5, l. 782 | *"your displacement or your boundary layer is 1 millimeter, then your effective body will be 11 millimeters"* | the effective body adds $\delta^*$, not $\delta$; they differ by a factor of about 3 (laminar) to 8 (turbulent) |
> | L6, ll. 519–525 | the general pressure-gradient case *"is basically the Faulkner-Skan equations"* | Falkner–Skan are similarity solutions for wedge flows, $U_e = cx^m$; the general momentum integral is von Kármán's, $\frac{d\theta}{dx}+(2+H)\frac{\theta}{U_e}\frac{dU_e}{dx} = \frac{c_f}{2}$ ([[SESA3043 3.5 - Momentum Integral Equation]]) |
> | L6, ll. 588–593 | *"once the boundary layer is all grown, the velocity will be decreasing"* | it is the growth rate $d\delta/dx$ that falls ($\delta\propto\sqrt x$), not the velocity |
> | L6, ll. 632–634; L7, l. 415 | *"The 0.99 times the U infinity is sometimes called the UE"* | $U_e$ is the velocity at the BL edge (the outer inviscid flow), equal to $U_\infty$ on a flat plate; $0.99U_\infty$ is only the $\delta_{99}$ criterion |
> | L7, l. 383 | *"dy over du I can easily replace with u infinity over delta"* | $du/dy = U_\infty/\delta$ |
> | L7, l. 402 | *"theta is nothing but square root of x divided by 3u infinity divided by nu"* | $\theta = \sqrt{\nu x/(3U_\infty)}$ |
> | L8, ll. 8–10 | *"We came up with some exact solutions for a parabolic profile"* | the parabola is an approximation; the exact laminar solution is Blasius |
> | L8, l. 553 | *"your shear stress is still zero"* | infinite for the power law, as said at l. 548 |
> | L9, l. 481 | *"see if it's matching within 0.2% or 20%"* | $y/\delta<0.2$, i.e. within 20% of $\delta$ |
> | L9, l. 504 | *"u tau is nothing but u infinity times CF over 2"* | $U_\tau = U_\infty\sqrt{c_f/2}$ (square root missing) ([[#6. Law of the wall]]) |
> | L10, ll. 69–71 | Q: *"what profile is Blasius' exact solution ... applicable for?"* A (student): *"Parabola"*, unchallenged | Blasius is the exact solution for the laminar flat plate at zero pressure gradient; it is not a parabola |
> | L10, ll. 593–600 | APG leads to *"zero viscous forces ... if there's no viscosity ... your flow will just go off the rails"* | separation is caused by viscosity plus the APG, at the point of zero wall shear ([[#8. Pressure gradients and separation]]) |

## Terminology and alternative names

This note uses the course's own words and symbols. Use the course term in the coursework and the exam, and treat the others as search terms.

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| boundary-layer thickness $\delta$ ($\delta_{99}$) | 99% thickness, BL edge | L5, ll. 412–447 | |
| local skin friction coefficient $c_f$ (small $f$) | local friction coefficient $C_f$, $c_{f,x}$ | L7, ll. 476–479; L9, ll. 109–113 | Some past papers write $C_f$ |
| total skin friction / viscous drag coefficient $C_F$ (capital $F$) | average friction coefficient $\bar C_f$, $C_{D,f}$ | L7, ll. 591–599; L9, ll. 109–113 | Based on one side unless doubled |
| momentum integral equation (MIE) | von Kármán momentum integral | slides; L6, ll. 254–360 | |
| shape factor $H$ | form factor $H_{12}$ | L6, ll. 114–123 | |
| skin friction velocity $U_\tau$ | friction velocity, shear velocity $u_*$ | L9, ll. 378–407 | |
| inner units, plus units $U^+$, $y^+$ | wall units | L9, ll. 401–410 | |
| log layer ("linear log region") | log-law region, overlap layer | L9, ll. 417–443 | |
| virtual origin $x_0$ | effective origin of the turbulent layer | L10, ll. 246–248 | |
| tripping | forced transition, boundary-layer trip | L10, ll. 637–641 | |

## Links

- Parent dashboard: [[SESA2022 Aerodynamics Hub]]
- Thermofluids foundation: [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]
- Next topic: [[SESA2022 T3 - Potential Flow]] (the inviscid outer flow; adding $\delta^*$ couples the two)
- Concepts: [[Displacement and Momentum Thickness]] · [[Momentum Integral Equation]] · [[Law of the Wall]] · [[Virtual Origin Method]] · [[Boundary Layer Separation]]
- Formulae: [[SESA2022 Formula Sheet]] · Problems: [[SESA2022 Tutorial 2 - Viscous Flow Solutions]]
- Feeds into (Year 3):
  - [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]] and [[SESA3043 3.5 - Momentum Integral Equation]]: the same thicknesses and MIE, now with a pressure gradient and the full boundary-layer equations.
  - [[SESA3043 3.4 - Transition to Turbulence]]: what this note models with the virtual origin, explained physically.

## Sources

- `02 - Sources/BL/Topic 2 Boundary layers.pdf` (slides 1–63), with the lecture notebooks and `laminar_profile.csv`, `turbulent_profile.csv`.
- 2025-26 transcripts in `02 - Sources/Lectures/`: L1 = `SESA2022 Lecture 1 - 1700.txt` (module introduction), L5–L10 = `SESA2022 Lecture 5.txt` to `SESA2022 Lecture 10.txt` (7–15 Oct 2025). Line numbers in this note refer to these files. `SESA2022 Lecture 2.txt` (non-dimensionalisation, Taylor series) is background and *"not going to show up in your exams"* (L1, l. 376).
- All seven 2025-26 transcripts above were read in full (second pass, 28 Oct 2026); every set task, exam remark and slip found is cited in this note.
- Revision lecture 1 (`SESA2022 Lecture 1 - Revision.txt`, Part A, Jan 2026), read in full and cited as "Revision 1": it works through [[SESA2022 Exam 2024-25 Solutions|2024-25]] Q1.
- Earlier-year recording `02 - Sources/BL/BLs.txt` (same slides).
- Anderson, *Fundamentals of Aerodynamics*, Ch. 17–19.
- Figures: `generate_aero_t2_figures.py` (`bl_mie_control_volume`, `bl_thickness_meanings`, `bl_profile_family`, `bl_profiles`); older figures (`bl_cf_transition`, `bl_law_of_wall`, `bl_virtual_origin`) predate the script. Worked-example numbers recomputed in Python (NumPy, SymPy, SciPy).

## Self-study tasks

The lecturer runs no tutorial sessions: you are expected to do the tutorial sheets yourself, using the written solutions (L1, ll. 441–452, 608–612), and the marked Blackboard quiz for Topic 2 counts towards the module (L1, ll. 423–437). Attempt each task closed-book first, then check.

### Core

- [ ] Derive $\delta^*$ and $\theta$ from the mass and momentum deficits (lectured, L5, ll. 683–770; L6, ll. 58–100). → [[#Displacement thickness: derivation]] · [[#Momentum thickness: derivation]]
- [ ] Derive $D' = \rho U_\infty^2\theta$ and $c_f = 2\,d\theta/dx$ from the control volume (lectured, L6, ll. 230–360; a past-paper derivation in 2016-17 Q3 and 2017-18 Q4). → [[#3. Momentum integral equation and drag]]
- [ ] Parabolic profile $u/U = 2\eta-\eta^2$: find $\delta^*/\delta$, $\theta/\delta$, $H$, $\theta/x$, $c_f$ — *"take a parabolic profile and try to derive this"*, Tutorial 2 Q3 hint (L7, ll. 506–513). → [[#Parabolic profile (lecture homework)]]
- [ ] Power law wall gradient: show $du/dy|_0\to\infty$ for $u/U = \eta^{1/n}$ — *"You can try it out at home"* (L8, l. 547). → [[#Power-law profile: integrals for general n]]
- [ ] Tutorial 2, all questions, especially Q4–Q5 (virtual origin and wake drag), flagged for the exam (L10, ll. 461–470, 487–510). → [[SESA2022 Tutorial 2 - Viscous Flow Solutions]]

### Further practice

- [ ] Run the lecture notebook on `laminar_profile.csv` and `turbulent_profile.csv`: $\delta$ by interpolation, $\delta^*$, $\theta$, $H$ by `np.trapz` — *"play with it at your own time"* (L5, ll. 481–508, 543, 660). → [[#2. Measures of boundary-layer thickness]]
- [ ] *(Suggested, not lecturer-set)* Derive $x_0 = x_T(1-36.9Re_{x_T}^{-3/8})$ from the matching condition and show the constant becomes $38.2$ with $0.036$. → [[#Matching condition]]
- [ ] *(Suggested, not lecturer-set)* Derive the turbulent $\delta/x = 0.37Re_x^{-1/5}$ from the $1/7$ law and the Blasius wall-shear law. → [[#Where the turbulent correlations come from (suggested, not lectured)]]
- [ ] *(Suggested, not lecturer-set)* For a cubic profile $u/U = \tfrac32\eta-\tfrac12\eta^3$, show $H = 35/13 = 2.69$ and $\theta/x = 0.646/\sqrt{Re_x}$, closest of the three to Blasius. → [[#General recipe for any assumed profile]]
- [ ] Past papers: [[SESA2022 Exam 2024-25 Solutions]] Q1 (parabolic profile, transition) and the BL questions listed in [[SESA2022 Past Paper Map]].
- [ ] Answer the "bare minimum" pop quiz without notes: which BL grows faster, which has the larger $\tau_w$, what $\delta^*$, $\theta$, $c_f$ and $C_F$ each measure, the three wall regions and why the law of the wall is needed — *"if you don't know this you're in trouble"* (L10, ll. 44–81).

### Lab report checklist (boundary-layer part, from the lectures)

- [ ] Attend, share your data with the other groups before you leave, keep a logbook (L1, ll. 471–531; L7, ll. 114–141). One combined report: BL, aerofoil and finite-wing labs plus an XFLR5 comparison; due Thursday of week 11 (11 Dec, 3 pm) (L7, ll. 189–256).
- [ ] $\delta$, $\delta^*$, $\theta$, $H$ for each profile with the lecture code, and classify each profile by $H$ (L6, ll. 129–204, 716–717). → [[#2. Measures of boundary-layer thickness]]
- [ ] Fit $n$ from your turbulent profile, fitting only inside the BL (L8, ll. 375–458). → [[#Finding n from data (lecture method)]]
- [ ] Pool the groups' $C_F$ against $Re$, fit $C_F = A\,Re^b$ and compare with the correlations (L7, ll. 710–714; L9, ll. 234–279).
- [ ] Check $y^+$ of your near-wall points and $y/\delta<0.2$ before using the log law (L9, ll. 479–531). → [[#6. Law of the wall]]
- [ ] Virtual origin and transition point with `fsolve` (several starting guesses) and sanity checks (L10, ll. 375–460).
- [ ] For the finite-wing lab, read off $C_F$ at the wing's $Re$, assuming the same surface (L7, ll. 715–719; L9, ll. 283–291).
- [ ] Discuss measurement accuracy and Pitot limitations; the marks are for explaining the data, not for clean curves (L5, ll. 554–570; L8, ll. 209–232). Declare any GenAI use (L1, ll. 553–586).
