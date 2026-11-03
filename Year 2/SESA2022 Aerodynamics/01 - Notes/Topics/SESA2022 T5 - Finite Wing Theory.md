---
title: "SESA2022 T5 - Finite Wing Theory"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 5: Finite Wing Theory"
order: 5
tags:
  - sesa2022
  - finite-wing-theory
  - lifting-line
  - induced-drag
aliases: ["Finite Wing Theory", "Lifting Line Theory", "Prandtl Lifting-Line Theory"]
date: 2026-09-23
status: lectured
coverage: "Lectures 6–13 Nov 2025 (five lectures)"
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
next_topics: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
key_concepts: ["[[Biot-Savart Law and Helmholtz Theorems]]", "[[Downwash and Induced Drag]]", "[[Elliptic Lift Distribution]]", "[[Oswald Efficiency Factor]]", "[[Maximum Lift-to-Drag Ratio]]"]
tutorial_sheets: ["[[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-06.txt … 2025-11-13.txt", "02 - Sources/Airfoils and Wings/FWT.txt (earlier-year recording)"]
---

# SESA2022 T5 - Finite Wing Theory

> [!abstract] Summary
> On a finite wing, air spills round the tips from the high-pressure lower surface to the low-pressure upper one and trails behind as tip vortices, which induce a downwash that reduces the effective angle of attack by $\alpha_i$ and tilts the lift back into induced drag, $D_i' = L'\alpha_i$. Prandtl's lifting-line theory models the wing as a bound vortex shedding a continuous trailing sheet; writing $\Gamma(\theta) = 2bV_\infty\sum B_n\sin n\theta$ gives $C_L = \pi AR\,B_1$, $C_{D_i} = C_L^2(1+\delta)/(\pi AR)$ and $a = a_0/[1+\frac{a_0}{\pi AR}(1+\tau)]$. The elliptic lift distribution, reached with an elliptic planform or with twist, gives constant downwash and the minimum induced drag ($\delta=0$).

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a wing's $AR$ (or $b$ and $S$), a section lift slope $a_0$, $\delta$ and $\tau$ (or "elliptic"), and asks for $C_L$, $C_{D_i}$, the wing lift slope $a$, a section $c_l$, a twist distribution, or $(L/D)_{max}$.
> - **Assumptions:** high aspect ratio, unswept, incompressible, attached flow; angles in radians; $\delta$, $\tau$ read from a chart or given; for a twisted wing use area-weighted $\bar\alpha$, $\bar\alpha_{L=0}$.
> - **Method:** 1. $AR = b^2/S$. 2. $a = a_0/[1+a_0(1+\tau)/(\pi AR)]$. 3. $C_L = a(\alpha-\alpha_{L=0})$. 4. $C_{D_i} = C_L^2(1+\delta)/(\pi AR)$. 5. If something is given the other way round (e.g. $C_{D_i}$), run the same three equations backwards (12 Nov, ll. 336–410).
> - **Common mistakes:** mixing up $\delta$ (induced-drag factor) and $\tau$ (lift-slope factor); using $a_0$ in place of the finite-wing slope $a$ when finding $C_L$.
> - In the exam you get a formula sheet: *"you'll need to work your way through that formula sheet so you know where everything is and what the terms mean"* (13 Nov, ll. 679–680). For finite wings the course works with the correction factors $\delta$ and $\tau$, not individual Fourier coefficients (13 Nov, ll. 660–673).
> - Revision-lecture advice (7 Jan revision, ll. 351–450): a short derivation such as $C_L = \pi AR\,B_1$ can appear (*"a rare example"*); given $B_n$, find $\delta = \sum n(B_n/B_1)^2$ and invert the lift-slope formula for $a_0$. Setting $\tau = \delta$ is *"not strictly a very good approximation"*. Keep $a_0$ (section) and $a$ (wing) apart. Worked example: [[SESA2022 Exam 2024-25 Solutions|2024-25]] Q4.
> - **Practise:** [[#Worked example 3: scaling the aspect ratio (lecture, 12 Nov)]] · [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]]

A 2D aerofoil is a slice of an infinitely long wing: nothing can leak round its ends. A real wing has finite span, so the high pressure below it and the low pressure above it can meet at the tips: air curls round each tip from bottom to top and is left behind as two trailing vortices, the tip vortices you see as contrails or in wet air (6 Nov lecture).

Those vortices spin downwards between them, so the whole wing sits in a gentle downwash. Each wing section therefore meets air that is already moving slightly downwards: its local relative wind is tilted, its effective angle of attack is smaller than the geometric one, and its lift — perpendicular to that tilted wind — leans backwards. The backward component is induced drag (7 Nov, l. 97). It is the price of lift on a finite wing, and it exists even in inviscid flow.

Making the wing longer moves the tip vortices apart and weakens the downwash for the same lift: that is why gliders and albatrosses have long, thin wings. For a given span, the least induced drag comes when the downwash is the same everywhere along the span, which happens for an elliptic spanwise lift distribution (Spitfire, 11 Nov, ll. 505–513).

The 6 Nov photo shows the vortices leaving the outboard flap edges of a landing aircraft, where the circulation changes most sharply; their waviness is the Crow instability (6 Nov, ll. 103–149). Outboard of the tips the air moves *up* (upwash), which is why birds flying in formation sit just outboard of the bird ahead. A race-car wing makes downforce, so its vortices turn the other way, and the upwash behind it hurts the following car (6 Nov, ll. 205–212).

---

## 1. Definitions and vortex theorems (6 Nov lecture)

Planform quantities:
- $b$: span ($= 2s$, $s$ the semispan); $S = \int_{-b/2}^{b/2}c(y)\,dy$: reference area of the main wing ($S_T$ for the tailplane, used in T6); $\bar c = S/b$: standard mean chord; MAC $= \frac1S\int c^2dy$. Industry uses the MAC for the wing pitching moment; this course does not distinguish the two (6 Nov, ll. 66–92).
- Net area excludes the part inside the fuselage. Wetted area (the whole skin, upper and lower) is larger than the projected planform area and is what matters for skin-friction drag (6 Nov, ll. 40–65).
- Aspect ratio $AR = b^2/S$ ($= b/c$ for a rectangular wing). *"You should be able to do these little calculations of aspect ratio"* (13 Nov, ll. 197–199).
- The wing AC sits at $c/4$ of the MAC in incompressible flow only: it moves aft as the flow goes through Mach 1, a stability and control issue for supersonic aircraft (6 Nov, ll. 92–101; Year 3).

**Why tip vortices form**: the lower surface is at high pressure and the upper at low pressure, so flow curls round the tips. The vortices induce downwash, a 3D effect that does not exist for 2D aerofoils. *"You should understand the physical origin of trailing vortices"* (6 Nov, l. 619).

Helmholtz vortex theorems (see [[Biot-Savart Law and Helmholtz Theorems]]):
1. A vortex filament cannot end in a fluid. It must form a closed loop or extend to a boundary (or infinity).
2. The circulation $\Gamma$ is constant along a filament.

### Biot–Savart law and a straight segment

$$
d\mathbf V = \frac{\Gamma}{4\pi}\frac{d\mathbf l\times\mathbf r}{|\mathbf r|^3}
$$

The course takes this as a physical law, the same one as for the magnetic field of a current-carrying wire; deriving it needs the vector calculus taught later in the year (6 Nov, ll. 265–300).

![[fwt_biot_savart_segment.png|560]]

Derivation for a straight segment (6 Nov, ll. 560–600: *"just check if you can follow each step"*). Let P be at perpendicular distance $h$ from the filament, and let $\theta$ be the angle between $d\mathbf l$ and $\mathbf r$ (from the element to P). Every element gives a contribution in the same direction (normal to the plane), so only magnitudes need adding.

Magnitude of the cross product:

$$
|d\mathbf l\times\mathbf r| = dl\,r\sin\theta\quad\Rightarrow\quad dV = \frac{\Gamma}{4\pi}\frac{\sin\theta\,dl}{r^2}.
$$

Geometry: $r = h/\sin\theta$, and the element's position along the filament is $l = -h\cot\theta$ (measured from the foot of the perpendicular). Differentiate:

$$
dl = \frac{h}{\sin^2\theta}\,d\theta.
$$

Substitute both:

$$
dV = \frac{\Gamma}{4\pi}\sin\theta\cdot\frac{h}{\sin^2\theta}\cdot\frac{\sin^2\theta}{h^2}\,d\theta = \frac{\Gamma}{4\pi h}\sin\theta\,d\theta.
$$

Integrate from $\theta_1$ (at A) to $\theta_2$ (at B):

$$
\boxed{V = \frac{\Gamma}{4\pi h}\left(\cos\theta_1-\cos\theta_2\right)}
$$

You don't need the whole derivation for the exam: *"you don't need to know the whole proof"*, but you should understand how the Biot–Savart law leads to the final result (6 Nov, ll. 640–643). The segment formula, written with $\cos\theta_{1,2}$ expressed through the end distances $l_1$, $l_2$ and $h$, is *"the one that you're given that you can then use"* (6 Nov, ll. 542–569).

The direction comes from the right-hand rule. In the course's sign convention (downwash negative) the slides write $V = -\frac{\Gamma}{4\pi h}(\cos\theta_1-\cos\theta_2)$ for the downward case.

- Infinite filament ($\theta_1\to0$, $\theta_2\to\pi$): $V = \dfrac{\Gamma}{2\pi h}$, the 2D point vortex of T3 (6 Nov, l. 611).
- Semi-infinite filament starting opposite P ($\theta_1 = \pi/2$, $\theta_2\to\pi$): $V = \dfrac{\Gamma}{4\pi h}$, half the infinite value.

### Horseshoe vortex

A bound vortex along the span (which carries the lift, by Kutta–Joukowski) plus two trailing vortices to infinity. This satisfies Helmholtz (the filament does not end). In reality the trailing vortices connect to the starting vortex shed at the start of flight, closing the loop into a ring ([[Kelvin's Circulation Theorem]]; 6 Nov, ll. 345–412). A grid of such rings over the wing is the vortex lattice method (6 Nov, ll. 413–423).

Downwash on the lifting line from the two trailing legs (13 Nov, ll. 626–639: *"probably some previous past exam question"*). Put the trailing vortices at $y = \pm s$ and take a point $y_0$ between them, at distances $h_1 = s+y_0$ and $h_2 = s-y_0$. The bound vortex induces nothing on itself. Each trailing leg is semi-infinite and starts opposite the point, so each gives $\Gamma/(4\pi h)$ downwards:

$$
w(y_0) = -\frac{\Gamma}{4\pi h_1}-\frac{\Gamma}{4\pi h_2}
$$

Put over a common denominator:

$$
\boxed{w(y_0) = -\frac{\Gamma}{4\pi}\,\frac{h_1+h_2}{h_1h_2}}
$$

- Near either vortex ($h_1$ or $h_2\to0$) the downwash goes to infinity: the reason a single horseshoe is not good enough.
- At the centre $h_1 = h_2 = s$: $w = -\Gamma/(2\pi s) = -\Gamma/(\pi b)$.
- The same formula gives the downwash at the tailplane from the wing horseshoe (6 Nov, ll. 629–630), with the tail's longitudinal distance included through $\theta_1$.

## 2. Downwash, induced angle and induced drag (7 Nov lecture)

![[fwt_induced_drag_tilt.png|720]]

$$
\alpha_{eff} = \alpha-\alpha_i,\qquad \alpha_i(y_0) = -\frac{w(y_0)}{V_\infty}\quad(w<0\text{ is downwash})
$$

The last step uses the small-angle approximation $\tan^{-1}(|w|/V_\infty)\approx|w|/V_\infty$.

- 2D aerofoil: $c_l = a_0(\alpha-\alpha_{L=0})$. TAT gives $a_0 = 2\pi$; a real section at finite Reynolds number *"might be 6.1 or 5.9"*, hence the symbol $a_0$ (7 Nov, ll. 343–347).
- 3D section: $c_l = a_0(\alpha_{eff}-\alpha_{L=0}) = a_0(\alpha-\alpha_i-\alpha_{L=0})$.

**Induced drag.** The local lift $L'$ is perpendicular to the *local* relative wind, which is tilted down by $\alpha_i$. Resolving it parallel and perpendicular to the freestream:

$$
D'_{wing} = D'\cos\alpha_i + L'\sin\alpha_i \approx D' + \underbrace{L'\alpha_i}_{D_i'}\qquad(w\ll V_\infty,\ \cos\alpha_i\approx1)
$$

### From horseshoes to a vortex sheet

A single horseshoe gives infinite downwash at the tips. Superpose many horseshoes of different spans (7 Nov; 11 Nov, ll. 13–35): where the bound circulation steps down from $\Gamma_1+\Gamma_2$ to $\Gamma_1$, a trailing vortex of strength $\Gamma_2$ leaves the wing. In the continuous limit the bound circulation is $\Gamma(y)$ and a trailing vortex sheet of strength $d\Gamma/dy$ per unit span leaves the trailing edge.

![[fwt_lifting_line_sheet.png|760]]

> [!warning] Flat sheet, not rolled-up vortices
> The model keeps the sheet flat and straight behind the wing. Further downstream the real sheet rolls up into two tip vortices, but the downwash that matters is the one at the wing, and near the wing the flat sheet is accurate (11 Nov, ll. 64–77).

**Downwash at $y_0$.** The sheet element between $y$ and $y+dy$ is a semi-infinite vortex of strength $(d\Gamma/dy)\,dy$, starting on the lifting line at perpendicular distance $y_0-y$ from the point $y_0$. By the semi-infinite result:

$$
dw(y_0) = -\frac{(d\Gamma/dy)\,dy}{4\pi(y_0-y)}
$$

Integrate across the span, then use $\alpha_i = -w/V_\infty$:

$$
\boxed{w(y_0) = -\frac{1}{4\pi}\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y},\qquad \alpha_i(y_0) = \frac{1}{4\pi V_\infty}\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y}}
$$

## 3. Prandtl's lifting-line equation (11 Nov lecture)

### The equation

Section lift by Kutta–Joukowski and by definition:

$$
L'(y_0) = \rho V_\infty\Gamma(y_0) = \tfrac12\rho V_\infty^2c(y_0)\,c_l(y_0)\quad\Rightarrow\quad c_l(y_0) = \frac{2\Gamma(y_0)}{V_\infty c(y_0)}.
$$

Section lift curve: $c_l = a_0(\alpha-\alpha_i-\alpha_{L=0})$. Equate and rearrange:

$$
\frac{2\Gamma(y_0)}{a_0V_\infty c(y_0)} = \alpha(y_0)-\alpha_{L=0}(y_0)-\alpha_i(y_0).
$$

Substitute $\alpha_i$:

$$
\boxed{\frac{2\Gamma(y_0)}{a_0V_\infty c(y_0)}+\frac{1}{4\pi V_\infty}\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y} = \alpha(y_0)-\alpha_{L=0}(y_0)}
$$

An integro-differential equation for $\Gamma(y)$, with $\Gamma = 0$ at both tips. The right-hand side is the twist distribution (12 Nov, l. 490): geometry the designer controls.

### Fourier solution

Transform the span as in TAT: $y = -\frac b2\cos\theta$ (left tip $\theta = 0$, right tip $\theta = \pi$), $dy = \frac b2\sin\theta\,d\theta$. Propose

$$
\Gamma(\theta) = 2bV_\infty\sum_{n=1}^\infty B_n\sin n\theta,
$$

which is zero at both tips automatically.

**Induced angle.** By the chain rule, $\frac{d\Gamma}{dy} = \frac{d\Gamma/d\theta}{dy/d\theta} = \frac{2bV_\infty\sum nB_n\cos n\theta}{(b/2)\sin\theta}$. Also $y_0-y = \frac b2(\cos\theta-\cos\theta_0)$. Substitute into $\alpha_i$; the $\sin\theta$ and the $b/2$ factors cancel:

$$
\alpha_i(\theta_0) = \frac{1}{4\pi V_\infty}\cdot2bV_\infty\cdot\frac2b\sum_{n=1}^\infty nB_n\int_0^\pi\frac{\cos n\theta\,d\theta}{\cos\theta-\cos\theta_0} = \frac1\pi\sum nB_n\frac{\pi\sin n\theta_0}{\sin\theta_0}
$$

using Glauert integral G1 ([[SESA2022 T4 - Thin Aerofoil Theory#Glauert integrals|T4]]). So

$$
\alpha_i(\theta_0) = \sum_{n=1}^\infty nB_n\frac{\sin n\theta_0}{\sin\theta_0}.
$$

**First term.** $\frac{2\Gamma}{a_0V_\infty c} = \frac{4b}{a_0c}\sum B_n\sin n\theta_0$. Together:

$$
\sum_{n=1}^\infty B_n\sin n\theta_0\left[\frac{4b}{a_0c(\theta_0)}+\frac{n}{\sin\theta_0}\right] = \alpha(\theta_0)-\alpha_{L=0}(\theta_0)
$$

**Numerical solution**: truncate to $N$ terms, write the equation at $N$ spanwise stations $\theta_{0,j}$, and solve the $N\times N$ linear system for $B_1\dots B_N$. The lecture code uses 64 stations; check the answer does not change if you change that number (12 Nov, ll. 80–160). For a symmetric wing only odd $n$ are non-zero.

### Lift coefficient

$$
C_L = \frac{L}{\tfrac12\rho V_\infty^2S} = \frac{\rho V_\infty\int\Gamma\,dy}{\tfrac12\rho V_\infty^2S} = \frac{2}{V_\infty S}\int_{-b/2}^{b/2}\Gamma\,dy
$$

Substitute $\Gamma$ and $dy$:

$$
C_L = \frac{2}{V_\infty S}\cdot2bV_\infty\cdot\frac b2\sum B_n\int_0^\pi\sin n\theta\sin\theta\,d\theta = \frac{2b^2}{S}\sum B_n\int_0^\pi\sin n\theta\sin\theta\,d\theta
$$

Only $n = 1$ survives, with integral $\pi/2$ (11 Nov, l. 341):

$$
C_L = \frac{2b^2}{S}\cdot\frac\pi2B_1 = \boxed{\pi AR\,B_1}
$$

### Induced drag

$$
C_{D_i} = \frac{\int\rho V_\infty\Gamma\alpha_i\,dy}{\tfrac12\rho V_\infty^2S} = \frac{2}{V_\infty S}\int_{-b/2}^{b/2}\Gamma\alpha_i\,dy
$$

Substitute $\Gamma$, $\alpha_i$ and $dy$; the $\sin\theta$ in $dy$ cancels the one in the denominator of $\alpha_i$:

$$
C_{D_i} = \frac{2b^2}{S}\sum_n\sum_m mB_nB_m\int_0^\pi\sin n\theta\sin m\theta\,d\theta
$$

Orthogonality leaves only $m = n$, each with integral $\pi/2$:

$$
C_{D_i} = \pi AR\sum_{n=1}^\infty nB_n^2 = \pi AR\,B_1^2\left[1+\sum_{n=2}^\infty n\left(\frac{B_n}{B_1}\right)^2\right]
$$

Use $\pi AR\,B_1^2 = C_L^2/(\pi AR)$ (11 Nov, ll. 388–410):

$$
\boxed{C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi eAR},\qquad \delta = \sum_{n=2}^\infty n\left(\frac{B_n}{B_1}\right)^2\ge0,\quad e = \frac{1}{1+\delta}\le1}
$$

- $\delta$ is a sum of squares, so it can never be negative (11 Nov, ll. 403–404): any departure from a pure $\sin\theta$ loading adds induced drag.
- The minimum is $\delta=0$: only $B_1$ non-zero, the elliptic distribution (11 Nov, ll. 419–421).
- Typical values: $\delta \approx 0.05$, $e\approx0.95$ (11 Nov, l. 429). The lecture calls both $\delta$ and $e$ the "span efficiency factor" (11 Nov, ll. 425–427); [[Oswald Efficiency Factor|Oswald]] $e$ in the drag polar also lumps in profile-drag variation with $C_L$.

> [!warning] Exam trap
> "Induced drag factor" is $\delta$ and "lift slope factor" is $\tau$. Many questions state $\delta = \tau$. That is *"not a very good assumption"* (12 Nov, ll. 280–283): see the check in §5.

## 4. Elliptic lift distribution (ELD)

With only $B_1$:

$$
\Gamma(\theta) = 2bV_\infty B_1\sin\theta,\qquad \sin\theta = \sqrt{1-\cos^2\theta} = \sqrt{1-\left(\frac{2y}{b}\right)^2}
$$

$$
\Gamma(y) = \Gamma_0\sqrt{1-\left(\frac{2y}{b}\right)^2},\qquad \Gamma_0 = 2bV_\infty B_1
$$

**Downwash.** $\alpha_i = \sum nB_n\sin n\theta_0/\sin\theta_0 = B_1$: constant along the span (11 Nov, ll. 436–451). Then

$$
\alpha_i = B_1 = \frac{\Gamma_0}{2bV_\infty} = \frac{C_L}{\pi AR},\qquad w = -V_\infty\alpha_i = -\frac{\Gamma_0}{2b}
$$

**Lift.** $L = \rho V_\infty\int\Gamma\,dy = \rho V_\infty\Gamma_0\int_{-b/2}^{b/2}\sqrt{1-(2y/b)^2}\,dy = \rho V_\infty\Gamma_0\frac{\pi b}{4}$ (area of a half-ellipse). So $C_L = \dfrac{\pi b\Gamma_0}{2V_\infty S}$ and $C_{D_i} = \dfrac{C_L^2}{\pi AR}$.

See [[Elliptic Lift Distribution]].

![[fwt_circulation.png|560]]

### Way 1: elliptic planform

Untwisted ($\alpha$ and $\alpha_{L=0}$ constant), so $\alpha-\alpha_i-\alpha_{L=0}$ is constant and every section has the same $c_l$. Since $c_l = 2\Gamma/(V_\infty c)$, the chord must vary like $\Gamma$: $c(y)\propto\sqrt{1-(2y/b)^2}$, an elliptic planform (Spitfire; 11 Nov, ll. 500–513).

### Way 2: rectangular wing with twist (12 Nov lecture)

Constant chord, so $c_l\propto\Gamma$ must vary elliptically: the twist distribution must do the work. From the lifting-line equation with constant $\alpha_i$:

$$
\alpha(y_0)-\alpha_{L=0}(y_0) = \alpha_i+\frac{2\Gamma_0}{a_0cV_\infty}\sqrt{1-\left(\frac{2y_0}{b}\right)^2}
$$

The lecture goes one step beyond the slides (12 Nov, ll. 520–545). Substitute $\Gamma_0 = 2bV_\infty\alpha_i$:

$$
\frac{2\Gamma_0}{a_0cV_\infty} = \frac{4b\,\alpha_i}{a_0c}.
$$

For a rectangular wing $b/c = AR$. Factor out $\alpha_i = C_L/(\pi AR)$:

$$
\boxed{\alpha(y_0)-\alpha_{L=0}(y_0) = \frac{C_L}{\pi AR}\left[1+\frac{4AR}{a_0}\sqrt{1-\left(\frac{2y_0}{b}\right)^2}\right]}
$$

- At the tip $c_l = 0$, so $\alpha_{tip}-\alpha_{L=0} = \alpha_i$: the tip is twisted nose-down (washout).
- **Geometric twist**: vary $\alpha(y)$ with the same section everywhere. Aerodynamic twist: vary $\alpha_{L=0}(y)$ by changing the section (12 Nov, ll. 476–486, 560–575).
- **Useful ratio**: $C_L/c_l(0) = \pi/4 = 0.785$, since the average of an ellipse is $\pi/4$ of its peak.
- A twist is exact for one $C_L$ only; at other $C_L$ the loading is no longer elliptic.

![[fwt_twist_distribution.png|640]]

### Tapered wings

$\delta$ is minimised at taper ratio $\lambda\approx0.3$–$0.4$ ($\delta\approx0.01$). Lecture values: rectangular $e\approx0.96$ (a 4% penalty), $\lambda = 0.6$ about 1% off, double taper $e = 0.997$. An elliptic planform buys the last 1% at a large manufacturing cost; increasing the span is the bigger lever, and *"other forms of drag are going to be more critical than this"* (12 Nov, ll. 214–273). Typical ranges: $e = 0.75$ to $1$, $\delta = 0$ to $0.3$ (12 Nov, ll. 229–238).

## 5. Lift slope of a finite wing

Elliptic wing (11 Nov, ll. 515–530). Every section has $c_l = C_L$ and the same $\alpha_i = C_L/(\pi AR)$:

$$
C_L = a_0\left(\alpha-\frac{C_L}{\pi AR}-\alpha_{L=0}\right).
$$

Collect $C_L$:

$$
C_L\left(1+\frac{a_0}{\pi AR}\right) = a_0(\alpha-\alpha_{L=0})\quad\Rightarrow\quad a = \frac{dC_L}{d\alpha} = \frac{a_0}{1+\frac{a_0}{\pi AR}}.
$$

**General wing.** The non-elliptic terms change $\alpha_i$ slightly; the result from the general (numerical) solution is written with a lift-slope factor $\tau$ (12 Nov, ll. 170–193):

$$
\boxed{a = \frac{dC_L}{d\alpha} = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)}},\qquad C_L = a(\bar\alpha-\bar\alpha_{L=0})
$$

- $a < a_0$ always, and $a \to a_0$ as $AR\to\infty$. *"High aspect ratios gives you lower induced drag and it gives you a larger lift slope"* (11 Nov, l. 535).
- $\tau$ is typically 0 to 0.3. Lecture chart readings: $AR = 6$ rectangular $\tau\approx0.16$, $\lambda = 0.3$ about $0.03$ (12 Nov, ll. 170–200). The textbook charts *"have been copied from previous textbooks, and they've made errors in copying these curves"*: the course Python code is more accurate (12 Nov, ll. 205–213).
- *"There is no explicit formula for the lift slope for any planform"* except the elliptic one: the code finds $a$ by a finite difference between two angles (12 Nov, ll. 104–146).
- For twisted wings, use the area-weighted angles $\bar\alpha = \frac1S\int\alpha\,c\,dy$ and $\bar\alpha_{L=0} = \frac1S\int\alpha_{L=0}\,c\,dy$ (12 Nov, ll. 585–600).

Numerical solution (12 Nov, ll. 53–163). Truncate the series at $N$ terms and enforce the lifting-line equation at $N$ stations, giving an $N\times N$ linear system $\mathbf E\mathbf B = \mathbf F$. Equal steps in $\theta$ automatically cluster the stations near the tips, where $\Gamma$ changes fastest (like the wall-clustered grid of a BL code). The course code normalises chord by the mean chord, so $4b/(a_0c)$ becomes $4AR/(a_0c/\bar c)$; it assumes a symmetric wing (odd $n$ only) and uses $N = 64$ by default. Check the sensitivity by trying a much smaller $N$, e.g. 8 (12 Nov, ll. 149–163).

**Low AR**: lifting-line theory is a high-aspect-ratio theory, since all the lift sits on the $c/4$ line; a slender wing needs chordwise loading (slender-wing theory). That is why slender deltas such as Concorde land at very high $\alpha$ (12 Nov, ll. 40–52, 409–430). Helmbold's equation blends the two limits: $a = \dfrac{a_0}{\sqrt{1+(a_0/\pi AR)^2}+a_0/(\pi AR)}$ (12 Nov, ll. 421–444). Swept wings (not lectured in detail): the extension of Helmbold's equation to sweep uses the half-chord sweep angle $\Lambda_{c/2}$ (12 Nov, ll. 459–463).

> [!warning] Viscous XFLR5 vs inviscid theory
> XFLR5's "LLT" is a *viscous* lifting-line method: it uses XFOIL section polars. The course LLT (and the inviscid Fluent run in the coursework) is inviscid, so close agreement between them may be partly coincidence (12 Nov, ll. 431–457; 13 Nov, ll. 594–597).

![[fwt_lift_slope.png|520]]

> [!check] δ and τ are not equal (Python, 40-term lifting line, $AR = 8$, $a_0 = 2\pi$)
>
> | Taper $\lambda$ | 1.0 | 0.8 | 0.6 | 0.4 | 0.3 |
> |---|---|---|---|---|---|
> | $\delta$ | 0.068 | 0.044 | 0.025 | 0.013 | 0.014 |
> | $\tau$ | 0.195 | 0.138 | 0.085 | 0.047 | 0.042 |
>
> $\delta$ has its minimum near $\lambda\approx0.35$, and $\tau$ is roughly three times $\delta$. Setting $\delta=\tau$ (as in the worked example below) is a back-of-envelope simplification.

## 6. Total drag, drag polar, maximum L/D (13 Nov lecture)

$$
C_D = C_{D_0}+C_{D_i} = C_{D_0}+\frac{C_L^2}{\pi eAR},\qquad C_{D_0} = C_F + C_{D_p}
$$

$C_{D_0}$ is the friction drag plus the pressure (form) drag from boundary-layer growth. Flat-plate friction from T2 is only a first estimate; the full value comes from XFOIL or CFD of the section across the span (13 Nov, ll. 8–29). Fit $C_{D_0}$ and $K = 1/(\pi eAR)$ to measured polars: *"you can find them out by fitting them to a parabola"*, which is what the wind-tunnel lab does (13 Nov, ll. 91–103, 118–121).

### Span loading

In steady level flight $L = W$. Write $D_i = qS\,C_{D_i}$ with $C_L = W/(qS)$:

$$
D_i = qS\frac{W^2}{q^2S^2\pi eAR} = \frac{W^2}{q\,\pi e\,(S\,AR)} = \frac{W^2}{q\,\pi e\,b^2}
$$

using $S\cdot AR = b^2$. With $q = \tfrac12\rho V^2$:

$$
D_i = \frac{2}{\pi e\rho V^2}\left(\frac{W}{b}\right)^2
$$

So induced drag depends on the span loading $W/b$, not on aspect ratio as such; it falls as $1/V^2$ while profile drag rises as $V^2$. Increase the span to reduce it (gliders, albatross).

### Maximum lift-to-drag ratio

Maximise $C_L/C_D = C_L/(C_{D_0}+KC_L^2)$ (13 Nov, ll. 122–138). Differentiate with respect to $C_L$ (quotient rule):

$$
\frac{d}{dC_L}\left(\frac{C_L}{C_D}\right) = \frac{(C_{D_0}+KC_L^2)-C_L(2KC_L)}{C_D^2} = \frac{C_{D_0}-KC_L^2}{C_D^2}.
$$

Set to zero:

$$
KC_L^{*2} = C_{D_0}\quad\Rightarrow\quad C_{D_i} = C_{D_0}\ \text{at the optimum}.
$$

So

$$
C_L^* = \sqrt{\frac{C_{D_0}}{K}} = \sqrt{\pi eAR\,C_{D_0}}.
$$

At the optimum $C_D = 2C_{D_0}$:

$$
\boxed{\left(\frac{L}{D}\right)_{max} = \frac{C_L^*}{2C_{D_0}} = \frac12\sqrt{\frac{\pi eAR}{C_{D_0}}}}
$$

The derivative is positive below $C_L^*$ and negative above it, so this is a maximum. Graphically, it is the tangent from the origin to the drag polar. It sets the best range of a jet aircraft (13 Nov, ll. 104–114). Typical values: seabird ~20, glider 20+, airliners ~15, UAVs lower (8–10), race car ~4, Shuttle ~1, which sets the glide angle (13 Nov, ll. 170–180).

At best range the induced drag equals the parasitic drag, so half the drag is always induced. A device that cuts induced drag below 50 % isn't used that way in practice; the aircraft is re-trimmed to fly back at the 50 % condition (13 Nov, ll. 144–164).

![[fwt_drag_polar.png]]

> [!example] Numbers
> $C_{D_0} = 0.02$, $e = 0.85$, $AR = 8$: $C_L^* = \sqrt{\pi(0.85)(8)(0.02)} = 0.654$ and $(L/D)_{max} = \tfrac12\sqrt{\pi(0.85)(8)/0.02} = 16.3$ (Python ✔).

Ways to reduce induced drag (13 Nov, ll. 182–361):
- **Increase the span**: *"the number one way that you can improve the performance of your aircraft"* (ll. 200–202): high-performance gliders, the Helios solar aircraft, seabirds.
- Winglets and other tip devices, when the span is fixed (airliners must fit a gate box about 60-something metres wide). They alter the spanwise loading to mimic a larger span and also make some lift of their own; cant and toe angle, extra tip weight and root bending moment all enter the optimisation, and the net effect is small (ll. 214–262).
- **Lifting fuselage / blended wing body**: lift carried across the whole span gives a more elliptic loading; often combined with a laminar upper surface. Engines on top shield noise but are harder to maintain; passengers outboard feel larger accelerations in a roll and there are no windows in the middle (ll. 263–361). A highly swept leading edge also gives vortex lift at high $\alpha$ (ll. 318–326, 360–361).
- Approach elliptic loading (taper, twist).

**Control surfaces**: deploying a flap over part of the span distorts the loading ($e\approx0.84$ in the slide example): $\Gamma$ is high over the flap and low outboard of it, a strong trailing vortex leaves the flap tip (Helmholtz), and the induced drag rises, so retract flaps for efficient cruise (13 Nov, ll. 402–419).

**Stall pattern**: a section stalls when its local $c_l$ reaches the section maximum. A rectangular wing stalls first at the root; moderate taper moves first stall to mid-span; strong taper (small $\lambda$) moves it to the tip. With outboard ailerons a tip stall removes roll control, so root stall is preferred; washout helps (13 Nov, ll. 362–401).

Numerical methods (13 Nov, ll. 429–474): the vortex lattice method ignores thickness and covers the camber surface with ring vortices, or with horseshoes whose bound vortex sits at the panel quarter-chord and whose control point (tangency condition) sits at the three-quarter chord. A 3D panel method panels both surfaces, so it handles thickness and fuselages. Both are superpositions of the Biot–Savart segment formula; the hard part is the geometry.

XFLR5 (13 Nov demo, ll. 475–600) offers viscous LLT, horseshoe VLM, ring VLM (viscous or inviscid; inviscid gives zero drag at zero lift) and a 3D panel method. The default mesh is only 13 chordwise × 19 spanwise panels: *"If you want to verify your results, you ought to be changing these numbers"* (ll. 517–524). Check the Reynolds number too (*"50,000 is a pigeon"*, l. 537).

---

## 7. Worked examples

### Worked example 1: elliptic, untwisted wing (lecture, 11 Nov)

$AR=10$, $C_L=0.3$, $a_0=5.8$ rad⁻¹ (*"the kind of examples that you would need to do"*, 11 Nov, ll. 537–553).

1. $C_{D_i} = \dfrac{0.3^2}{10\pi} = 0.00286$.
2. $a = \dfrac{5.8}{1+5.8/(10\pi)} = \dfrac{5.8}{1.185} = 4.90$ rad⁻¹.

### Worked example 2: twisted rectangular wing with elliptic loading

$AR=10$, $C_L=0.3$, $a_0=5.8$.

1. Elliptic loading, so $C_{D_i} = 0.00286$ again.
2. $\alpha_i = C_L/(\pi AR) = 0.00955$ rad $= 0.547^\circ$.
3. Root: $\alpha(0)-\alpha_{L=0} = 0.00955\left[1+\tfrac{4(10)}{5.8}\right] = 0.00955(7.897) = 0.0754$ rad $= 4.32^\circ$.
4. Equivalently $c_l(0) = C_L/0.785 = 0.382 = 5.8[\alpha(0)-\alpha_{L=0}-\alpha_i]$ gives the same $4.32^\circ$.
5. Tip: $\alpha_{tip}-\alpha_{L=0} = 0.547^\circ$, so the washout is $3.77^\circ$.

### Worked example 3: scaling the aspect ratio (lecture, 12 Nov)

Rectangular wing, $AR=6$, $\delta=\tau=0.055$, $\alpha_{L=0}=-2^\circ$, $C_{D_i}=0.01$ at $\alpha = 3.4^\circ$. Same section and $\alpha$ at $AR=10$, where $\delta=\tau=0.105$. Find $C_{D_i}$ (12 Nov, ll. 336–405; also 2013-14 and 2014-15 exams).

1. $AR=6$: $C_L = \sqrt{\pi AR\,C_{D_i}/(1+\delta)} = \sqrt{0.01(6\pi)/1.055} = 0.423$.
2. $a = C_L/(\alpha-\alpha_{L=0}) = 0.423/(5.4^\circ\text{ in rad}) = 0.423/0.0942 = 4.485$ rad⁻¹.
3. Back out the section slope: $a_0 = \dfrac{a}{1-a(1+\tau)/(\pi AR)} = \dfrac{4.485}{1-4.485(1.055)/(6\pi)} = 5.99$ rad⁻¹ (not $2\pi$).
4. $AR=10$: $a = \dfrac{5.99}{1+5.99(1.105)/(10\pi)} = 4.95$ rad⁻¹.
5. $C_L = 4.95(0.0942) = 0.466$; $C_{D_i} = \dfrac{0.466^2(1.105)}{10\pi} = \mathbf{0.0076}$.

> [!check] Python check
> $C_L(AR{=}6) = 0.4227$, $a = 4.485$, $a_0 = 5.988$, $a(AR{=}10) = 4.946$, $C_L = 0.4662$, $C_{D_i} = 0.00764$ ✔. The lecture slide quotes $C_L = 0.464$ (12 Nov, l. 397); the difference is intermediate rounding, and $C_{D_i}$ rounds to $0.0076$ either way.

### Worked example 4: tapered wing (lecture, 12 Nov)

Untwisted, $AR=8$, $\lambda = 0.8$, thin symmetric section ($\alpha_{L=0} = 0$, $a_0 = 2\pi$), $\alpha=5^\circ$, $\delta=\tau=0.055$ read from the chart (12 Nov, ll. 274–300).

1. $a = \dfrac{2\pi}{1+\frac{2\pi}{8\pi}(1.055)} = 4.97$ rad⁻¹.
2. $C_L = 4.97(0.0873) = 0.434$.
3. $C_{D_i} = \dfrac{0.434^2(1.055)}{8\pi} = 0.0079$.
4. Mean induced angle $\approx C_L(1+\tau)/(\pi AR) = 1.04^\circ$, so a typical section works at $\alpha_{eff}\approx4.0^\circ$, $c_l\approx2\pi(0.0697) = 0.44$.

## Transcript slips (6–13 Nov)

> [!warning] Slips in `SESA2022 Lecture 2025-11-06.txt` to `2025-11-13.txt` (Whisper transcripts)
> Recurring transcriptions: *"Biot-Savar"* = Biot–Savart, *"Kuttev-Jakowsky"* = Kutta–Joukowski, *"cord"* = chord, *"air force section"*/*"aerofol"* = aerofoil section, *"minimum-reduced drag"* = minimum induced drag.
>
> | Line | Said | Correct |
> |---|---|---|
> | 12 Nov, l. 397 | *"So CL is 0.464"* | $0.466$ from unrounded intermediates ([[#Worked example 3: scaling the aspect ratio (lecture, 12 Nov)]]) |
> | 12 Nov, l. 486 | *"that will reduce the load at the wing tip and that will get you closer towards the minimum reduced drag"* | minimum induced drag |
> | 12 Nov, ll. 528–530 | *"4 times b divided by a 0 c times alpha i times the square root of 1 minus 2y0 over b. All squared."* | $\frac{4b}{a_0c}\alpha_i\sqrt{1-(2y_0/b)^2}$: only $2y_0/b$ is squared ([[#Way 2: rectangular wing with twist (12 Nov lecture)]]) |
> | 11 Nov, l. 523 | *"Cl is equal to A0 divided by 1 plus A0 over pi times the aspect ratio times alpha minus alpha 0 lift"* | $C_L = \frac{a_0}{1+a_0/(\pi AR)}(\alpha-\alpha_{L=0})$: the bracket closes before $(\alpha-\alpha_{L=0})$ |
> | 6 Nov, l. 99 | *"your pitching moment aerodynamic sensor changes"* | aerodynamic centre |
> | 6 Nov, ll. 516–517 | *"1 over tan is 6 … is cosec squared"* | $\dfrac{d}{d\theta}\cot\theta = -\operatorname{cosec}^2\theta$ ("6" is "cosec"; the sign matters for $dl$) |
> | 12 Nov, l. 649 | *"0.75 is just the average of the elliptic distribution"* | $\pi/4 = 0.785$, the value used at l. 623 |
> | 13 Nov, ll. 376–377 | *"as we go to high taper ratios, then we can get stall in the outboard part"* | tip stall comes with strong taper, i.e. a small taper ratio $\lambda$ |
> | 12 Nov, ll. 367–370 | *"So we're using A0 equals 2 pi … No, we're not. We're deducing A0 equals 5.989"* | corrected in the lecture: $a_0 = 5.99$ is deduced, not assumed |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| lifting-line theory | Prandtl lifting-line theory, LLT | 11 Nov | |
| induced angle of attack $\alpha_i$ | downwash angle at the wing | 7 Nov; 11 Nov | T6's $\epsilon$ is the downwash angle at the tail |
| $\delta$ (induced drag factor) | span efficiency factor (as in the lecture) | 11 Nov, ll. 403–432 | |
| $e = 1/(1+\delta)$ | span efficiency factor, Oswald efficiency factor | 11 Nov, ll. 423–429 | Oswald $e$ in a drag polar also includes profile-drag effects |
| $\tau$ (lift slope factor) | slope correction factor | 12 Nov, ll. 170–193 | |
| $B_n$ | Fourier coefficients of the circulation, $A_n$ in Anderson | 11 Nov | Not the same as the TAT $A_n$ |
| elliptic lift distribution (ELD) | elliptic loading | 11 Nov | |
| geometric twist / aerodynamic twist | washout (tip nose-down) | 12 Nov, ll. 476–486 | |
| vortex lattice method | VLM | 13 Nov; XFLR5 | |

## Links

- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T4 - Thin Aerofoil Theory]] · Next: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Concepts: [[Biot-Savart Law and Helmholtz Theorems]] · [[Downwash and Induced Drag]] · [[Elliptic Lift Distribution]] · [[Oswald Efficiency Factor]] · [[Maximum Lift-to-Drag Ratio]]
- Problems: [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]] · Formulae: [[SESA2022 Formula Sheet]]
- Downwash at the tail ($\epsilon = C_L/\pi Ae$) is used in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]].
- Feeds into (Year 3): [[SESA3043 Advanced Aeronautics Hub|SESA3043 Advanced Aeronautics]] (swept wings, vortex lattice); [[SESA3047 Advanced Aerospace Mechanics & Control Hub|SESA3047 Advanced Aerospace Mechanics & Control]] (roll damping and other lateral derivatives from spanwise loading).

## Sources

- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf` (slides 1–67), `Examples5.pdf`.
- 2025-26 transcripts in `02 - Sources/Lectures/`, cited by date: `SESA2022 Lecture 2025-11-06.txt` (Biot–Savart, Helmholtz, horseshoe), `2025-11-07.txt` (downwash, induced drag), `2025-11-11.txt` (lifting-line equation, Fourier solution, ELD, lift slope), `2025-11-12.txt` (numerical solution, taper, twist, examples), `2025-11-13.txt` (drag polar, $L/D$, winglets, XFLR5). Line numbers refer to these files. XFLR5 videos: `SESA2022 Lecture 2020-09-08 - XFLR5 *.txt`.
- All five 2025-26 lectures above were read in full (second pass, 28 Oct 2026); every set task, exam remark and slip found is cited in this note.
- Revision lecture 2 (`SESA2022 Lecture 2026-01-07.txt`, Part B), read in full and cited as "7 Jan revision".
- Earlier-year recording `02 - Sources/Airfoils and Wings/FWT.txt`.
- Anderson, *Fundamentals of Aerodynamics*, Ch. 5; MIT 16.01 lecture notes F5–F9.
- Figures: `generate_aero_t5_figures.py` (`fwt_biot_savart_segment`, `fwt_lifting_line_sheet`, `fwt_induced_drag_tilt`, `fwt_twist_distribution`); older figures (`fwt_circulation`, `fwt_lift_slope`, `fwt_drag_polar`) predate the script. Numbers and the $\delta$, $\tau$ table recomputed in Python (NumPy, 40-term lifting line).

## Self-study tasks

The exam uses the results more than the derivations: *"you're just using these formulae for particular wing designs"* (11 Nov, ll. 549–553). But you should be able to follow each step of the theory. Attempt each task closed-book first.

### Core

- [ ] Biot–Savart for a segment, then the infinite and semi-infinite limits — *"just check if you can follow each step"* (6 Nov, l. 585); *"You don't need to know the whole proof"* but follow how the result is reached (6 Nov, ll. 640–643). → [[#Biot–Savart law and a straight segment]]
- [ ] Physical origin of trailing vortices — *"you should understand the physical origin of trailing vortices"* (6 Nov, l. 619). → [[#SESA2022 T5 - Finite Wing Theory|opening section]]
- [ ] Downwash between two trailing vortices, $w = -\frac{\Gamma}{4\pi}\frac{h_1+h_2}{h_1h_2}$ — *"probably some previous past exam question"* (13 Nov, ll. 629–636). → [[#Horseshoe vortex]]
- [ ] Induced drag from the tilt of lift, $D_i' = L'\alpha_i$ — *"conceptually you should be able to understand where downwash comes from"* (7 Nov, l. 97). → [[#2. Downwash, induced angle and induced drag (7 Nov lecture)]]
- [ ] $C_L = \pi AR B_1$ and $C_{D_i} = C_L^2(1+\delta)/\pi AR$ from the Fourier series (lectured, 11 Nov, ll. 330–432). → [[#Lift coefficient]] · [[#Induced drag]]
- [ ] Elliptic wing: constant downwash and the lift slope $a_0/(1+a_0/\pi AR)$ (11 Nov, ll. 436–534). → [[#4. Elliptic lift distribution (ELD)]] · [[#5. Lift slope of a finite wing]]
- [ ] Worked examples 3 and 4 from the lecture. → [[#Worked example 3: scaling the aspect ratio (lecture, 12 Nov)]] · [[#Worked example 4: tapered wing (lecture, 12 Nov)]]
- [ ] $(L/D)_{max}$ and $C_{D_i} = C_{D_0}$ at the optimum — *"If you stick that value of lift coefficient back into the original formula, what do you get for the induced drag coefficient?"* (13 Nov, ll. 139–145). → [[#Maximum lift-to-drag ratio]]
- [ ] Aspect-ratio manipulations ($AR = b^2/S = b/\bar c$) — *"You should be able to do these little calculations of aspect ratio"* (13 Nov, ll. 197–199). → [[#1. Definitions and vortex theorems (6 Nov lecture)]]
- [ ] Know the exam formula sheet: find each finite-wing result on it and say what every symbol means (13 Nov, ll. 679–680). → [[SESA2022 Formula Sheet]]
- [ ] Examples Sheet 5, including the twisted-wing question flagged in lecture (12 Nov, l. 599). → [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]]

### Further practice

- [ ] Derive the twist distribution for elliptic loading on a rectangular wing, the step the lecture adds beyond the slides (12 Nov, ll. 520–545). → [[#Way 2: rectangular wing with twist (12 Nov lecture)]]
- [ ] Run the lifting-line Python code: vary taper and check that $\delta\ne\tau$, and that the answer is insensitive to the number of stations (try $N = 8$ against 64) (12 Nov, ll. 154–163, 283). → [[#5. Lift slope of a finite wing]]
- [ ] In XFLR5, compare a rectangular and an elliptic wing of the same $AR$, and refine the default 13 × 19 panel mesh until the answer stops changing (13 Nov, ll. 517–524; XFLR5 videos). → [[#6. Total drag, drag polar, maximum L/D (13 Nov lecture)]]
- [ ] For the lab: fit $C_{D_0}$ and $K$ to a measured polar and deduce $e$ (13 Nov, ll. 95–103, 118–121). → [[#6. Total drag, drag polar, maximum L/D (13 Nov lecture)]]
- [ ] *(Suggested, not lecturer-set)* Show that $D_i = \frac{2}{\pi e\rho V^2}(W/b)^2$ and use it to explain why a glider's span matters more than its chord. → [[#Span loading]]
- [ ] Past papers: the finite-wing questions listed in [[SESA2022 Past Paper Map]] (13 Nov, l. 629 flags the two-vortex downwash question).
