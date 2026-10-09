---
title: "SESA2022 Tutorial 3 - Potential Flow Solutions"
module: "SESA2022 Aerodynamics"
type: tutorial
stream: "Topic 3: Potential Flow"
tags:
  - sesa2022
  - tutorial-solutions
  - potential-flow
sheet: "Tutorial 3"
theory_notes: ["[[SESA2022 T3 - Potential Flow]]"]
key_concepts: ["[[Flow Past a Cylinder]]", "[[Method of Images]]", "[[Elementary Potential Flows]]", "[[Rankine Oval]]"]
status: complete
sources: ["02 - Sources/PF/Tutorial3.pdf", "02 - Sources/PF/Tutorial_3_Solutions.pdf"]
---

# SESA2022 Tutorial 3 - Potential Flow Solutions

> [!abstract] Sheet Info
> Sheet: Tutorial 3 (Potential flow). Lecturer's key results reproduced: Q3 $C_p(2,2) = 0.872$ (the coarse notebook grid wrongly gives $-10.5$).

## Theory Links
- [[SESA2022 T3 - Potential Flow]] · [[Flow Past a Cylinder]] · [[Method of Images]] · [[Rankine Oval]]

## Q1: Do the streamlines change if $V_\infty$ doubles?

### Solution
**Non-lifting cylinder** ($\Gamma=0$):

$$
\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right)\quad\Rightarrow\quad \frac{\psi}{V_\infty} = r\sin\theta\left(1-\frac{R^2}{r^2}\right)
$$

Doubling $V_\infty$ just doubles every $\psi$ value. The **shape** of each streamline $\psi/V_\infty = $ const is unchanged, so the **pattern does not change**; only the speed along it scales.

**Spinning cylinder** ($\Gamma\ne0$):

$$
\frac{\psi}{V_\infty} = r\sin\theta\left(1-\frac{R^2}{r^2}\right)+\frac{\Gamma}{2\pi V_\infty}\ln\frac rR
$$

The pattern depends on the ratio $\Gamma/(V_\infty R)$. The stagnation points sit at $\sin\theta = -\Gamma/(4\pi V_\infty R)$. Doubling $V_\infty$ halves this ratio, so the stagnation points move back toward $\theta = 0,\pi$ and **the streamlines change**. (If the spin rate is also fixed, $\Gamma$ is fixed.)

## Q2: Starting vortex above the ground

A starting vortex of strength $\Gamma = 20$ m²/s sits at height $a = 2$ m above the ground.

### Solution
**Method of images**: put an image vortex of **opposite sign** at $(0,-a)$ so that $z=0$ is a streamline.

$$
\boxed{\psi = \frac{\Gamma}{2\pi}\ln\sqrt{x^2+(z-a)^2}-\frac{\Gamma}{2\pi}\ln\sqrt{x^2+(z+a)^2}}
$$

Velocities:

$$
u = \frac{\partial\psi}{\partial z} = \frac{\Gamma}{2\pi}\left[\frac{z-a}{x^2+(z-a)^2}-\frac{z+a}{x^2+(z+a)^2}\right],\qquad w = -\frac{\partial\psi}{\partial x} = -\frac{\Gamma}{2\pi}\left[\frac{x}{x^2+(z-a)^2}-\frac{x}{x^2+(z+a)^2}\right]
$$

On $z = 1$ m with $a = 2$ m:

$$
u = \frac{\Gamma}{2\pi}\left[-\frac{1}{x^2+1}-\frac{3}{x^2+9}\right],\qquad w = \frac{\Gamma}{2\pi}\left[-\frac{x}{x^2+1}+\frac{x}{x^2+9}\right]
$$

$$
C_p = 1-\frac{u^2+w^2}{U_{ref}^2},\qquad U_{ref} = \frac\Gamma a = 10\text{ m/s}
$$

At $x = 0$: $u = \frac{20}{2\pi}\left(-1-\frac13\right) = -4.244$ m/s, so $C_{p,min} = 1-0.180 = \mathbf{0.820}$. As $|x|\to\infty$, $C_p\to1$.

![[t3_q2_cp_line.png|560]]

The analytic curve and the notebook (vortex function + `findvelocities` + `findpressure`, then pick the $z=1$ row with `np.where`) agree.

## Q3: Source + vortex at the origin

$\Lambda = 1$ m²/s, $\Gamma = 2\pi$ m²/s.

### Solution

$$
\psi = \frac{\Lambda}{2\pi}\theta+\frac{\Gamma}{2\pi}\ln r = \frac{\theta}{2\pi}+\ln r
$$

This is a **spiral vortex**: fluid spirals outward, because $V_r = \Lambda/(2\pi r)$ and $V_\theta = -\Gamma/(2\pi r)$ (clockwise). The streamlines are **logarithmic spirals**:

$$
\psi = 0:\; r = e^{-\theta/2\pi},\qquad \psi = \frac\pi2:\; r = e^{\pi/2-\theta/2\pi}
$$

Plot these by computing $r$ over a range of $\theta$ and converting to $x = r\cos\theta$, $z = r\sin\theta$:

![[t3_q3_spirals.png|480]]

**Pressure at $(2,2)$**: $r = 2\sqrt2$.

$$
C_p = 1-\frac{V_r^2+V_\theta^2}{U_{ref}^2} = 1-\frac{\Lambda^2+\Gamma^2}{4\pi^2r^2U_{ref}^2} = 1-\frac{1+4\pi^2}{4\pi^2(8)} = \boxed{0.872}
$$

> [!warning] Grid resolution
> A coarse notebook grid gives $C_p=-10.5$, which is badly wrong because of the singularity at the origin and interpolation errors. Refining the domain and grid gives $0.872$. Always sanity-check numerical results against the analytic ones.

## Q4: Aircraft hangar as a Rankine semi-oval

A semicircular hangar has $C_{p,min} = -3$ at the top. Find the aspect ratio of a semi-oval that gives $C_{p,min} = -1$.

### Solution
Model the hangar as the upper half of a **Rankine oval** (source at $-b$, sink at $+b$, uniform $V_\infty$), with the body being $\psi = 0$:

$$
\psi = V_\infty z+\frac{Q}{2\pi}\left[\tan^{-1}\frac{z}{x+b}-\tan^{-1}\frac{z}{x-b}\right] = 0
$$

**Half-length** (stagnation point on $z=0$):

$$
V_\infty+\frac{Q}{2\pi}\frac{-2b}{x^2-b^2} = 0\;\Rightarrow\;L = x_{end} = \sqrt{b^2+\frac{Qb}{\pi V_\infty}}
$$

**Height** $H = z_{top}$ at $x = 0$. Using $\theta_1 = \tan^{-1}(z/b)$ and $\theta_2 = \pi-\theta_1$, solve numerically (`fsolve`):

$$
V_\infty H+\frac{Q}{\pi}\tan^{-1}\frac Hb-\frac Q2 = 0
$$

**Minimum $C_p$** is at the top (slides):

$$
C_{p,min} = -\frac{2Q}{\pi V_\infty b(1+H^2/b^2)}-\frac{Q^2}{\pi^2V_\infty^2b^2(1+H^2/b^2)^2}
$$

Fix $V_\infty = b = 1$ and sweep $Q$. Each $Q$ gives one $AR = L/H$ and one $C_{p,min}$:
- As $Q\to\infty$ the oval tends to a circle, so $AR\to1$ and $C_{p,min}\to-3$ (the semicircular hangar ✔).
- As $Q\to0$ the oval becomes slender, so $AR\to\infty$ and $C_{p,min}\to0$.

![[t3_q4_hangar.png|560]]

$$
\boxed{C_{p,min} = -1\text{ requires }L/H\approx2.15}
$$

The hangar should be about twice as long as it is tall (a long, low profile). Flattening the hangar greatly reduces the peak suction and hence the roof uplift.

## Sources
- `02 - Sources/PF/Tutorial3.pdf`, lecturer solutions `Tutorial_3_Solutions.pdf`
- Figures generated in Python/matplotlib (see scripts in the note methods)
