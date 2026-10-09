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
status: complete
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
next_topics: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
key_concepts: ["[[Biot-Savart Law and Helmholtz Theorems]]", "[[Downwash and Induced Drag]]", "[[Elliptic Lift Distribution]]", "[[Oswald Efficiency Factor]]", "[[Maximum Lift-to-Drag Ratio]]"]
tutorial_sheets: ["[[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Airfoils and Wings/FWT.txt"]
---

# SESA2022 T5 - Finite Wing Theory

> [!abstract] Summary
> On a finite wing, high pressure below and low pressure above spill round the tips as **trailing (tip) vortices**. These induce **downwash** $w$, which reduces the effective angle of attack by $\alpha_i$ and tilts the lift back, producing **induced drag** $D_i' = L'\alpha_i$. Prandtl's **lifting-line theory** models the wing as a bound vortex with a continuous trailing vortex sheet. Writing $\Gamma(\theta) = 2bV_\infty\sum B_n\sin n\theta$ gives
> $$C_L = \pi AR\,B_1,\qquad C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi e AR},\qquad a = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)}$$
> The **elliptic lift distribution** gives minimum induced drag ($\delta=0$) with constant downwash.

## Key Concepts
- [[Biot-Savart Law and Helmholtz Theorems]]
- [[Downwash and Induced Drag]]
- [[Elliptic Lift Distribution]]
- [[Oswald Efficiency Factor]] ($e$, $\delta$, $\tau$)
- [[Maximum Lift-to-Drag Ratio]]

---

## 5.1 Definitions and the horseshoe vortex

**Planform**:
- $b$: span
- $S = \int_{-b/2}^{b/2}c(y)\,dy$: reference area
- $\bar c = S/b$: standard mean chord
- MAC $= \frac1S\int c^2dy$
- $AR = b^2/S$
- The AC sits at $c/4$ of the MAC

**Why tip vortices form**: the lower surface is at high pressure and the upper at low pressure, so flow curls around the tips. The vortices induce **downwash**, a 3D effect that does not exist for 2D aerofoils.

**Helmholtz vortex theorems**:
1. A vortex filament **cannot end in a fluid**. It must form a closed loop or extend to a boundary (or infinity).
2. The circulation $\Gamma$ is **constant along a filament**.

**Biot–Savart law** (right-hand rule):

$$
d\mathbf V = \frac{\Gamma}{4\pi}\frac{d\mathbf l\times\mathbf r}{|\mathbf r|^3}
$$

For a straight filament of length from angle $\theta_1$ to $\theta_2$, at perpendicular distance $h$ from point P:

$$
V = -\frac{\Gamma}{4\pi h}\left(-\cos\theta_2+\cos\theta_1\right)
$$

- **Infinite** filament ($\theta_1\to0$, $\theta_2\to\pi$): $V = -\dfrac{\Gamma}{2\pi h}$, the 2D point vortex.
- **Semi-infinite** filament ($\theta_1 = \pi/2$): $V = -\dfrac{\Gamma}{4\pi h}$.

**Horseshoe vortex model**: a **bound vortex** along the span (which gives the lift) plus two **trailing vortices** to infinity. This satisfies Helmholtz. In reality the trailing vortices connect to the **starting vortex**.

## 5.2 Downwash, induced angle and induced drag

$$
\alpha_{eff} = \alpha-\alpha_i,\qquad \alpha_i(y_0) = -\frac{w(y_0)}{V_\infty}\quad(w<0\text{ is downwash})
$$

- 2D aerofoil: $c_l = 2\pi(\alpha-\alpha_{L=0})$
- 3D section: $c_l = 2\pi(\alpha_{eff}-\alpha_{L=0})$

The local lift is perpendicular to the *local* relative wind, so it tilts back by $\alpha_i$:

$$
D'_{wing} = D'\cos\alpha_i + L'\sin\alpha_i \approx D' + \underbrace{L'\alpha_i}_{D_i'}\qquad(w\ll V_\infty)
$$

**Superposition of horseshoe vortices**: $\Gamma(y_n) = \sum\gamma_k\Delta y$. In the continuous limit the trailing vortex sheet has strength $\gamma(y) = d\Gamma/dy$. An element $dy$ of the sheet (semi-infinite) induces

$$
dw(y_0) = -\frac{(d\Gamma/dy)\,dy}{4\pi(y_0-y)}
$$

$$
\boxed{w(y_0) = -\frac{1}{4\pi}\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y},\qquad \alpha_i(y_0) = \frac{1}{4\pi V_\infty}\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y}}
$$

## 5.3 Prandtl's lifting-line equation

Kutta–Joukowski for each section, $L'(y_0) = \rho V_\infty\Gamma(y_0) = \frac12\rho V_\infty^2c(y_0)c_l(y_0)$, gives:

$$
\boxed{\frac{2\Gamma(y_0)}{a_0V_\infty c(y_0)}+\frac{1}{4\pi V_\infty}\int_{-b/2}^{b/2}\frac{(d\Gamma/dy)\,dy}{y_0-y} = \alpha(y_0)-\alpha_{L=0}(y_0)}
$$

This is an integro-differential equation for $\Gamma(y)$. Transform with $y = -\frac b2\cos\theta$ and

$$
\Gamma(\theta) = 2bV_\infty\sum_{n=1}^\infty B_n\sin n\theta
$$

Using G1, $\alpha_i(\theta_0) = \sum nB_n\dfrac{\sin n\theta_0}{\sin\theta_0}$, and the general lifting-line equation is

$$
\sum_{n=1}^\infty B_n\sin n\theta_0\left[\frac{4b}{a_0c(\theta_0)}+\frac{n}{\sin\theta_0}\right] = \alpha(\theta_0)-\alpha_{L=0}(\theta_0)
$$

**Numerical solution**: truncate to $N$ terms, write the equation at $N$ spanwise stations $\theta_{0,j}$, and solve the $N\times N$ linear system for $B_1\dots B_N$. (Python in SESA2029.)

### Lift coefficient

$$
C_L = \frac{2}{V_\infty S}\int_{-b/2}^{b/2}\Gamma\,dy = \frac{2b^2}{S}\sum B_n\int_0^\pi\sin n\theta\sin\theta\,d\theta = \boxed{\pi AR\,B_1}
$$

Only $B_1$ contributes to lift.

### Induced drag

$$
C_{D_i} = \frac{2}{V_\infty S}\int\Gamma\alpha_i\,dy = \pi AR\sum nB_n^2 = \pi AR B_1^2\left[1+\sum_{n=2}^\infty n\left(\frac{B_n}{B_1}\right)^2\right]
$$

$$
\boxed{C_{D_i} = \frac{C_L^2}{\pi AR}(1+\delta) = \frac{C_L^2}{\pi eAR},\qquad \delta = \sum_{n=2}^\infty n\left(\frac{B_n}{B_1}\right)^2\ge0,\quad e = \frac{1}{1+\delta}\le1}
$$

- $\delta$ is the **span efficiency factor** (typically 0 to 0.3). $e$ is the **Oswald efficiency factor** (typically 0.75 to 1).
- The **minimum is at $\delta=0$**, where only $B_1$ is non-zero, which is the elliptic distribution.

> [!warning] Exam trap
> "Induced drag factor" is $\delta$ and "lift slope factor" is $\tau$. Many questions state $\delta = \tau$.

## 5.4 Elliptic lift distribution (ELD)

With only $B_1$:

$$
\Gamma(y) = \Gamma_0\sqrt{1-\left(\frac{2y}{b}\right)^2},\qquad \Gamma_0 = 2bV_\infty B_1
$$

$$
w = -\frac{\Gamma_0}{2b}\;(\text{constant}),\qquad \alpha_i = \frac{\Gamma_0}{2bV_\infty} = \frac{C_L}{\pi AR}\;(\text{constant}),\qquad C_L = \frac{\pi b\Gamma_0}{2V_\infty S},\qquad C_{D_i} = \frac{C_L^2}{\pi AR}
$$

- Lift: $L = \rho V_\infty\int\Gamma\,dy = \rho V_\infty\Gamma_0\dfrac{\pi b}{4}$.
- **Untwisted wing** with constant $\alpha$ and $\alpha_{L=0}$: $c_l$ is constant, so $c(y)\propto\Gamma(y)$. The chord must vary **elliptically**, giving an **elliptic planform** (Spitfire).
- **Rectangular wing with ELD**: the section $c_l$ varies ($c_l\propto\Gamma$), so the wing needs geometric twist (washout) or aerodynamic twist:

$$
\alpha(y_0)-\alpha_{L=0}(y_0) = \alpha_i+\frac{2\Gamma_0}{a_0cV_\infty}\sqrt{1-\left(\frac{2y_0}{b}\right)^2}
$$

  At the tip $c_l = 0$, so $\alpha_{tip} - \alpha_{L=0} = \alpha_i$.
- **Useful ratio** for a rectangular wing with ELD: $\dfrac{C_L}{c_l(0)} = \dfrac{\pi}{4} = 0.785$, since $\Gamma_{avg} = \frac\pi4\Gamma_0$.

See [[Elliptic Lift Distribution]].

![[fwt_circulation.png|560]]

**Typical planforms** (from Anderson): constant chord $e\approx0.96$ (only a 4% penalty), simple taper $\lambda = 0.6$ gives $e \approx 0.989$, double taper $e\approx0.997$. $\delta$ is minimised at taper ratio $\lambda\approx0.3$–$0.4$.

## 5.5 Lift slope of a finite wing

For an elliptic wing: $c_l = C_L = a_0\left(\alpha-\frac{C_L}{\pi AR}-\alpha_{L=0}\right)$, which gives

$$
a = \frac{a_0}{1+\frac{a_0}{\pi AR}}
$$

For a general wing:

$$
\boxed{a = \frac{dC_L}{d\alpha} = \frac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)}},\qquad C_L = a(\bar\alpha-\bar\alpha_{L=0})
$$

- $a < a_0$ always, and $a \to a_0$ as $AR\to\infty$.
- $\tau$ is between 0 and 0.3 (from the $B_n$).
- For twisted wings, use the area-weighted angles $\bar\alpha = \frac1S\int\alpha\,c\,dy$ and $\bar\alpha_{L=0} = \frac1S\int\alpha_{L=0}\,c\,dy$.

**Low AR**, Helmbold: $a = \dfrac{a_0}{\sqrt{1+(a_0/\pi AR)^2}+a_0/(\pi AR)}$. **Swept wings**: replace $a_0\to a_0\cos\Lambda$.

![[fwt_lift_slope.png|520]]

## 5.6 Total drag, drag polar, $(L/D)_{max}$

$$
C_D = C_{D_0}+C_{D_i} = C_{D_0}+\frac{C_L^2}{\pi eAR},\qquad C_{D_0} = C_F + C_{D_p}
$$

In steady level flight ($L=W$):

$$
D = \tfrac12\rho V^2SC_{D_0}+\frac{W^2}{\tfrac12\rho V^2S\pi eAR}
$$

Profile drag scales with $V^2$ and induced drag with $1/V^2$. From the second term, $D_i = \dfrac{2}{\pi e\rho V^2}\left(\dfrac{W}{b}\right)^2$, so induced drag depends on the **span loading** $W/b$. Increase the span to reduce it (gliders, albatross).

**Maximum $L/D$**: set $\dfrac{\partial}{\partial C_L}\left(\dfrac{C_L}{C_D}\right) = 0$. This happens when $C_{D_i} = C_{D_0}$:

$$
\boxed{C_L^* = \sqrt{\pi eAR\,C_{D_0}},\qquad \left(\frac{L}{D}\right)_{max} = \frac12\sqrt{\frac{\pi eAR}{C_{D_0}}}}
$$

Graphically, it is the tangent from the origin to the drag polar. Typical values: albatross ~20, glider ~20+, airliners ~15, UAVs 8–10, race car ~4, Shuttle ~1.

![[fwt_drag_polar.png]]

**Ways to reduce induced drag**: increase span/AR, winglets (when span is constrained), blended wing-body or lifting fuselage, and approaching elliptic loading.

**Control surfaces**: deploying a flap mid-span distorts the loading ($e\approx0.84$ in the slide example), which gives more induced drag and non-uniform downwash.

**Stall pattern**: a local section stalls when it reaches its stall angle. It is better for the **root to stall first** so the ailerons stay effective.

**Numerical methods**: vortex lattice (a horseshoe vortex per panel, Biot–Savart, tangency at control points) and 3D panel methods, both available in XFLR5.

---

## Worked examples (lecture)

> [!example] Quick example: elliptic, untwisted, $AR=10$, $C_L=0.3$, $a_0=5.8$
> 1. $C_{D_i} = \dfrac{0.3^2}{10\pi} = 0.00286$
> 2. $a = \dfrac{5.8}{1+5.8/(10\pi)} = 4.9$ rad$^{-1}$

> [!example] Twisted rectangular wing, $AR=10$, $C_L=0.3$, $a_0=5.8$, $\Gamma_{avg} = 0.785\Gamma_0$
> 1. With elliptic loading, $C_{D_i} = 0.00286$.
> 2. $C_L = 0.785\,c_{l,y=0}$, so $c_{l,y=0} = 0.38$.
> 3. $0.38 = 5.8[\alpha(0)-\alpha_i]$ with $\alpha_i = C_L/(\pi AR) = 0.00955$, so $\alpha(0) = 0.075$ rad $=4.3^\circ$.

> [!example] Untwisted, $AR=8$, taper 0.8, $\delta=\tau=0.055$, $\alpha=5^\circ$, $a_0=2\pi$
> $a = \dfrac{2\pi}{1+\frac{2\pi}{8\pi}(1.055)} = 4.97$ rad$^{-1}$, $C_L = 0.4335$, $C_{D_i} = \dfrac{0.4335^2(1.055)}{8\pi} = 0.00789$
>
> Section at $y_n$: $\alpha_i = C_L/(\pi AR) = 0.99^\circ$, so $c_l = 2\pi(5^\circ-0.99^\circ) = 0.44$.

> [!example] Scaling AR: $AR=6$ ($\delta=\tau=0.055$, $\alpha_{L=0}=-2^\circ$, $C_{D_i}=0.01$ at $3.4^\circ$) → $AR=10$ ($\delta=\tau=0.105$)
> - $AR=6$: $C_L = \sqrt{0.01\cdot6\pi/1.055} = 0.423$, $a = 0.423/5.4^\circ = 4.485$ rad$^{-1}$
> - Back out $a_0 = \dfrac{a}{1-a(1+\tau)/(\pi AR)} = 5.99$ rad$^{-1}$
> - $AR=10$: $a = 4.95$ rad$^{-1}$, $C_L=0.466$, $C_{D_i} = \mathbf{0.0076}$
>
> This appears in the 2013-14 and 2014-15 exams.

## Links
- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T4 - Thin Aerofoil Theory]] · Next: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Problems: [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]]
- Downwash at the tail ($\epsilon = C_L/\pi Ae$) is used in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]
- Year 3: [[SESA3043 Advanced Aeronautics]] (swept wings, VLM)

## Sources
- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf` (slides 1–67), transcript `FWT.txt`
- Anderson, *Fundamentals of Aerodynamics*, Ch. 5; MIT 16.01 lecture notes F5–F9
