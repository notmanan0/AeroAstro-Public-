---
title: "SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions"
module: "SESA2022 Aerodynamics"
type: tutorial
stream: "Topic 4: Thin Aerofoil Theory"
tags:
  - sesa2022
  - tutorial-solutions
  - thin-aerofoil-theory
sheet: "Examples Sheet 4"
theory_notes: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
key_concepts: ["[[Glauert Integrals]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Trailing-Edge Flap in Thin Aerofoil Theory]]"]
status: complete
sources: ["02 - Sources/Airfoils and Wings/Examples4(1).pdf"]
---

# SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions

> [!abstract] Sheet Info
> All given answers are reproduced ✔: Q1 (0.471, −0.181, 0.384, −2.29°, −0.063); Q3 (0°, 0.754, −0.189); Q4 (5°, −0.0567); Q5 (−2.08°, −0.053).

## Theory Links
- [[SESA2022 T4 - Thin Aerofoil Theory]]
- Toolkit: $x = \frac c2(1-\cos\theta_0)$, $A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0$, $A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0$
- $c_l = \pi(2A_0+A_1)$, $c_{m,le} = -\frac\pi2(A_0+A_1-\frac{A_2}{2})$, $c_{m,c/4} = \frac\pi4(A_2-A_1)$, $\frac{x_{cp}}{c} = \frac14\left[1+\frac{\pi(A_1-A_2)}{c_l}\right]$

## Q1: $z/c = 0.08\,(x/c)(1-x/c)$

### Solution
With unit chord, $\dfrac{dz}{dx} = 0.08(1-2x)$. Substituting $1-2x = \cos\theta_0$:

$$
\frac{dz}{dx} = 0.08\cos\theta_0
$$

$$
A_0 = \alpha-\frac{0.08}{\pi}\int_0^\pi\cos\theta_0\,d\theta_0 = \alpha,\qquad A_1 = \frac{2(0.08)}{\pi}\int_0^\pi\cos^2\theta_0\,d\theta_0 = 0.08,\qquad A_{n\ge2}=0
$$

**(a)** $\alpha = 2^\circ = 0.03491$ rad:

(i) $c_l = \pi(2\alpha+0.08) = \pi(0.06981+0.08) = \boxed{0.471}$

(ii) $c_{m,le} = -\frac\pi2(A_0+A_1) = -\frac\pi2(0.03491+0.08) = \boxed{-0.181}$

(iii) $\dfrac{x_{cp}}{c} = -\dfrac{c_{m,le}}{c_l} = \dfrac{0.1805}{0.4706} = \boxed{0.384}$

**(b)**

(i) $c_l = 0$ gives $2\alpha+0.08 = 0$, so $\alpha_{L=0} = -0.04$ rad $= \boxed{-2.29^\circ}$

(ii) $c_{m,ac} = c_{m,c/4} = \frac\pi4(0-0.08) = \boxed{-0.0628}$

## Q2: Ideal angle of attack

### Solution
The LE term of $\gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum A_n\sin n\theta\right)$ is **singular at $\theta = 0$** because $\sin\theta\to0$ while $1+\cos\theta\to2$. The sine terms all vanish there. So $\gamma(0)$ is finite (in fact zero, with no LE suction peak) **only if $A_0 = 0$**:

$$
A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0 = 0\quad\Rightarrow\quad\boxed{\alpha_{ideal} = \frac1\pi\int_0^\pi\frac{dz}{dx}\,d\theta_0}
$$

At the ideal angle the flow attaches smoothly at the LE. This is the design condition for low drag.

## Q3: NACA 6500, $z = 0.24x(1-x)$

### Solution
$dz/dx = 0.24\cos\theta_0$, so $A_0 = \alpha$, $A_1 = 0.24$, and the rest are zero.

(a) $\alpha_{ideal} = \frac{0.24}{\pi}\int_0^\pi\cos\theta_0\,d\theta_0 = \boxed{0^\circ}$

(b) $c_l = \pi(0+0.24) = \boxed{0.754}$

(c) $c_{m,c/4} = \frac\pi4(0-0.24) = \boxed{-0.189}$

## Q4: Symmetric aerofoil with a TE flap (hinge at $x/c = 3/4$)

### (a) Camber-line slope
Taking $c = 1$ and a downward deflection $\phi$:

$$
\frac{dz}{dx} = \begin{cases}0 & 0\le x<0.75\\ -\phi & 0.75<x\le1\end{cases}\qquad\Longleftrightarrow\qquad\frac{dz}{dx} = \begin{cases}0 & 0\le\theta_0<\frac{2\pi}{3}\\ -\phi & \frac{2\pi}{3}<\theta_0\le\pi\end{cases}
$$

The hinge is at $\cos\theta_h = 1-2(0.75) = -\frac12$, so $\theta_h = 2\pi/3$ ($120^\circ$). Both sketches are step functions: zero, then $-\phi$ from the hinge to the TE.

### (b) Flap setting for $c_l = 1$ at $\alpha = 6.074^\circ$

$$
A_0 = \alpha-\frac1\pi\int_{2\pi/3}^{\pi}(-\phi)\,d\theta_0 = \alpha+\frac\phi3
$$

$$
A_1 = \frac2\pi\int_{2\pi/3}^\pi(-\phi)\cos\theta_0\,d\theta_0 = -\frac{2\phi}{\pi}\left[\sin\theta_0\right]_{2\pi/3}^{\pi} = \frac{2\phi}{\pi}\cdot\frac{\sqrt3}{2} = \frac{\sqrt3}{\pi}\phi
$$

$$
A_2 = \frac2\pi\int_{2\pi/3}^\pi(-\phi)\cos2\theta_0\,d\theta_0 = -\frac\phi\pi\left[\sin2\theta_0\right]_{2\pi/3}^{\pi} = -\frac{\sqrt3}{2\pi}\phi
$$

$$
c_l = \pi(2A_0+A_1) = 2\pi\alpha+\left(\frac{2\pi}{3}+\sqrt3\right)\phi = 2\pi\alpha+3.8265\phi
$$

$$
1 = 2\pi(0.10601)+3.8265\phi\;\Rightarrow\;\phi = \frac{1-0.6661}{3.8265} = 0.0873\text{ rad} = \boxed{5.0^\circ}
$$

### (c) Quarter-chord moment

$$
c_{m,c/4} = \frac\pi4(A_2-A_1) = \frac\pi4\left(-\frac{\sqrt3}{2\pi}-\frac{\sqrt3}{\pi}\right)\phi = -\frac{3\sqrt3}{8}\phi = -0.6495(0.0873) = \boxed{-0.0567}
$$

## Q5: NACA 2400 ($m = 0.02$, $p = 0.4$)

### Solution
Camber slope with $c = 1$:

$$
\frac{dz}{dx} = \frac{2m}{p^2}(p-x)\;(x<p),\qquad \frac{dz}{dx} = \frac{2m}{(1-p)^2}(p-x)\;(x>p)
$$

With $p - x = -0.1+0.5\cos\theta_0$ and the break at $\cos\theta_p = 1-2p = 0.2$, so $\theta_p = 1.3694$ rad ($78.46^\circ$):

$$
\frac{dz}{dx} = \begin{cases}-0.025+0.125\cos\theta_0 & 0<\theta_0<\theta_p\\ -0.01111+0.05556\cos\theta_0 & \theta_p<\theta_0<\pi\end{cases}
$$

Integrate each piece. By hand, use $\int\cos\theta = \sin\theta$, $\int\cos^2\theta = \frac\theta2+\frac{\sin2\theta}{4}$, etc.; or use `scipy.integrate.quad` with a break point at $\theta_p$.

$$
\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0 = 0.00449,\qquad A_1 = 0.08150,\qquad A_2 = 0.01386
$$

(a) Zero-lift angle:

$$
\alpha_{L=0} = \frac1\pi\int_0^\pi\frac{dz}{dx}(1-\cos\theta_0)\,d\theta_0 = -0.03625\text{ rad} = \boxed{-2.08^\circ}
$$

Check: $\alpha_{L=0} = -(2A_0|_{\alpha=0}+A_1)/2 = -(2(-0.00449)+0.0815)/2 = -0.0363$ ✔

(b) Moment about the AC:

$$
c_{m,ac} = \frac\pi4(A_2-A_1) = \frac\pi4(0.01386-0.08150) = \boxed{-0.053}
$$

```python
import numpy as np; from scipy.integrate import quad
m,p=.02,.4; tp=np.arccos(1-2*p)
dz=lambda t:(2*m/p**2 if .5*(1-np.cos(t))<p else 2*m/(1-p)**2)*(p-.5*(1-np.cos(t)))
aL0=quad(lambda t:dz(t)*(1-np.cos(t)),0,np.pi,points=[tp])[0]/np.pi   # -0.03625 rad
A1=2/np.pi*quad(lambda t:dz(t)*np.cos(t),0,np.pi,points=[tp])[0]      # 0.0815
A2=2/np.pi*quad(lambda t:dz(t)*np.cos(2*t),0,np.pi,points=[tp])[0]    # 0.01386
```

## Sources
- `02 - Sources/Airfoils and Wings/Examples4(1).pdf`
