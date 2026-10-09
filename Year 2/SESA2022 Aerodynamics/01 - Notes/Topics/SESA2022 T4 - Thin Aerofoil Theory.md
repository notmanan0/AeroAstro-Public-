---
title: "SESA2022 T4 - Thin Aerofoil Theory"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 4: Thin Aerofoil Theory"
order: 4
tags:
  - sesa2022
  - thin-aerofoil-theory
  - aerofoils
aliases: ["Thin Aerofoil Theory", "TAT"]
date: 2026-09-23
status: complete
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[SESA2022 T3 - Potential Flow]]", "[[Kutta-Joukowski Theorem]]"]
next_topics: ["[[SESA2022 T5 - Finite Wing Theory]]"]
key_concepts: ["[[Vortex Sheet]]", "[[Kutta Condition]]", "[[Glauert Integrals]]", "[[Aerodynamic Centre and Centre of Pressure]]", "[[Kelvin's Circulation Theorem]]", "[[Aerofoil Stall]]", "[[Trailing-Edge Flap in Thin Aerofoil Theory]]"]
tutorial_sheets: ["[[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf", "02 - Sources/Airfoils and Wings/TAT.txt"]
---

# SESA2022 T4 - Thin Aerofoil Theory

> [!abstract] Summary
> Replace a thin, lightly cambered aerofoil at small $\alpha$ by a **vortex sheet** $\gamma(\xi)$ on its chord line. Enforce **flow tangency** to the camber line and the **Kutta condition** ($\gamma(TE)=0$). Transforming to $\theta$ and writing $\gamma$ as a Fourier series gives closed-form results:
>
> $$C_l = 2\pi(\alpha-\alpha_{L=0}) = \pi(2A_0+A_1),\qquad c_{m,c/4} = \frac\pi4(A_2-A_1)$$
>
> The lift slope is always $2\pi$, the **quarter chord is the aerodynamic centre**, and camber only shifts $\alpha_{L=0}$ and adds a constant nose-down moment.

## Key Concepts
- [[Vortex Sheet]] · [[Kutta Condition]] · [[Glauert Integrals]]
- [[Aerodynamic Centre and Centre of Pressure]]
- [[Kelvin's Circulation Theorem]] (starting vortex) · [[Aerofoil Stall]]
- [[Trailing-Edge Flap in Thin Aerofoil Theory]]

---

## 4.1 Aerofoil basics

**Nomenclature**:
- Leading and trailing edge; the **chord line** joins them, with length $c$.
- **Camber line**: the locus of points midway between the upper and lower surfaces. **Camber** is its maximum distance from the chord line.
- **Thickness**: measured normal to the chord line.
- **Angle of attack** $\alpha$: the angle between the relative wind and the chord line.

**NACA 4-digit (e.g. 2412)**:
- 2: max camber $m=0.02c$
- 4: at $p=0.4c$
- 12: thickness $0.12c$

**NACA 5-digit (e.g. 23012)**:
- 2: design $C_l = 2\times3/20 = 0.3$
- 30: max camber at $30/2 = 15\%c$
- 12: 12% thickness

**NACA 6-series (e.g. 65-218)**:
- 6: series
- 5: minimum pressure at $0.5c$ for the symmetric section
- 2: design $C_l=0.2$
- 18: 18% thickness

$$
c_l = \frac{L'}{q_\infty c},\quad q_\infty = \tfrac12\rho_\infty V_\infty^2,\quad Re = \frac{\rho V_\infty c}{\mu},\quad M=\frac{V_\infty}{a_\infty},\quad a_0 = \frac{dc_l}{d\alpha}
$$

Pressure plots usually show $-C_p$ to highlight the suction peak.

### Three key concepts

**1. Linearisation.** For small perturbation velocity $v \ll V_\infty$:

$$
C_p = \frac{p-p_\infty}{q_\infty} \approx -\frac{2v}{V_\infty}
$$

**2. Vortex sheet.** The flow over the top is faster than over the bottom. Model the aerofoil as a sheet of vortices with strength per unit length

$$
\gamma(s) = V_{upper}-V_{lower},\qquad \Gamma = \int_{LE}^{TE}\gamma\,ds,\qquad dV_\theta = -\frac{\gamma\,ds}{2\pi r}
$$

The loading is $\Delta C_p = C_{p,l}-C_{p,u} = \dfrac{2\gamma}{V_\infty}$, which gives

$$
c_l = \frac1c\int_0^c\Delta C_p\,dx = \frac{2}{cV_\infty}\int_0^c\gamma\,dx,\qquad c_{m,le} = -\frac{1}{c^2}\int_0^c x\Delta C_p\,dx = -\frac{2}{c^2V_\infty}\int_0^c x\gamma\,dx
$$

**3. Kutta condition.** The flow leaves a sharp trailing edge smoothly. Bernoulli across the TE ($p_a$ equal on both sides) gives $V_1=V_2$, so

$$
\boxed{\gamma(TE) = V_1-V_2 = 0}
$$

This is how viscosity is accounted for without modelling it: it **fixes the circulation** and hence the lift. See [[Kutta Condition]].

**Circulation theory of lift**: a lifting aerofoil induces a rotational flow (circulation). The Kutta condition picks the $\Gamma$, and Kutta–Joukowski gives $L' = \rho V_\infty\Gamma$.

> [!warning] Bogus explanations
> "Equal transit time" is completely wrong. Newton-only, Bernoulli-only and nozzle explanations are partly correct but incomplete.

## 4.2 The fundamental equation

**Linearised boundary condition**: the flow is tangent to the surface. For small angles

$$
\frac{dz}{dx} = \frac{w}{U}
$$

For a camber line $z_c$ at incidence $\alpha$, the surface slope relative to the freestream is $dz_c/dx - \alpha$. So the induced normal velocity must satisfy

$$
\frac{w}{V_\infty} = \frac{dz_c}{dx}-\alpha
$$

Move the sheet onto the chord ($\xi$ from $0$ to $c$). The induced velocity at $x$ from an element $d\xi$ is $dw(x) = -\dfrac{\gamma(\xi)d\xi}{2\pi(x-\xi)}$. Integrating and applying tangency:

$$
\boxed{\frac{1}{2\pi}\int_0^c\frac{\gamma(\xi)\,d\xi}{x-\xi} = V_\infty\left(\alpha-\frac{dz}{dx}\right)}
$$

**Transformation**:

$$
\xi = \frac c2(1-\cos\theta),\quad x = \frac c2(1-\cos\theta_0)
$$

The LE is at $\theta = 0$ and the TE at $\theta=\pi$. The equation becomes

$$
\frac{1}{2\pi}\int_0^\pi\frac{\gamma(\theta)\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = V_\infty\left(\alpha-\frac{dz}{dx}\right)
$$

$$
c_l = \frac{1}{V_\infty}\int_0^\pi\gamma\sin\theta\,d\theta,\qquad c_{m,le} = -\frac{1}{2V_\infty}\int_0^\pi\gamma\sin\theta(1-\cos\theta)\,d\theta
$$

**[[Glauert Integrals]]**. These are improper (singular at $\theta=\theta_0$) and evaluated in the principal-value sense:

$$
\text{(G1)}\;\int_0^\pi\frac{\cos n\theta\,d\theta}{\cos\theta-\cos\theta_0} = \frac{\pi\sin n\theta_0}{\sin\theta_0},\qquad \text{(G2)}\;\int_0^\pi\frac{\sin n\theta\sin\theta\,d\theta}{\cos\theta-\cos\theta_0} = -\pi\cos n\theta_0
$$

## 4.3 Symmetric aerofoil (flat plate)

With $dz/dx=0$, the solution is

$$
\boxed{\gamma(\theta) = 2V_\infty\alpha\frac{1+\cos\theta}{\sin\theta}}
$$

**Check with G1**:

$$
\frac{V_\infty\alpha}{\pi}\left[\int_0^\pi\frac{d\theta}{\cos\theta-\cos\theta_0}+\int_0^\pi\frac{\cos\theta\,d\theta}{\cos\theta-\cos\theta_0}\right] = \frac{V_\infty\alpha}{\pi}[0+\pi] = V_\infty\alpha \;✔
$$

**Kutta condition**: at $\theta=\pi$ the expression is $0/0$, and L'Hôpital gives $\gamma(\pi)=0$ ✔.

**Lift**:

$$
c_l = \frac{1}{V_\infty}\int_0^\pi 2V_\infty\alpha(1+\cos\theta)\,d\theta = 2\pi\alpha\qquad\boxed{\frac{dc_l}{d\alpha} = 2\pi}
$$

**Loading**: $\gamma(x) = 2V_\infty\alpha\sqrt{(c-x)/x}$. The **leading-edge suction peak** is infinite at the LE, and there is zero loading at the TE. The adverse pressure gradient behind the peak leads to [[Boundary Layer Separation]] and laminar separation bubbles.

## 4.4 General cambered aerofoil

Propose a flat-plate term plus a Fourier sine series. Each term vanishes at the TE:

$$
\boxed{\gamma(\theta) = 2V_\infty\left(A_0\frac{1+\cos\theta}{\sin\theta}+\sum_{n=1}^\infty A_n\sin n\theta\right)}
$$

Substitute into the fundamental equation and use G1 (n=0,1) and G2:

$$
A_0 - \sum_{n=1}^\infty A_n\cos n\theta_0 = \alpha - \frac{dz}{dx}
$$

Using orthogonality (multiply by $\cos m\theta_0$ and integrate from $0$ to $\pi$):

$$
\boxed{A_0 = \alpha-\frac1\pi\int_0^\pi\frac{dz}{dx}d\theta_0,\qquad A_n = \frac2\pi\int_0^\pi\frac{dz}{dx}\cos n\theta_0\,d\theta_0\;(n\ge1)}
$$

**Lift**. Only the $A_0$ term and the $n=1$ term survive:

$$
c_l = 2\int_0^\pi A_0(1+\cos\theta)d\theta + 2\int_0^\pi\sum A_n\sin n\theta\sin\theta\,d\theta = \pi(2A_0+A_1)
$$

$$
\boxed{c_l = 2\pi(\alpha-\alpha_{L=0}),\qquad \alpha_{L=0} = \frac1\pi\int_0^\pi\frac{dz}{dx}(1-\cos\theta_0)\,d\theta_0}
$$

The lift slope is **still $2\pi$**. Camber shifts the curve left (more negative $\alpha_{L=0}$).

![[tat_lift_curve.png|520]]

## 4.5 Moments, aerodynamic centre, centre of pressure

$$
c_{m,le} = -\frac\pi2\left(A_0+A_1-\frac{A_2}{2}\right) = -\left[\frac{c_l}{4}+\frac\pi4(A_1-A_2)\right]
$$

Transferring the moment to the quarter chord, $M'_{LE} = M'_{c/4} - \frac c4L'$:

$$
\boxed{c_{m,c/4} = c_{m,le}+\frac{c_l}{4} = \frac\pi4(A_2-A_1)}\quad\text{independent of }\alpha
$$

- The **aerodynamic centre** is where $dc_m/d\alpha = 0$. In thin-aerofoil theory it is the **quarter chord** for any aerofoil.
- For a symmetric aerofoil $c_{m,c/4}=0$. For positive camber it is **negative** (nose-down).

**Centre of pressure** (where the moment is zero):

$$
\frac{x_{cp}}{c} = -\frac{c_{m,le}}{c_l} = \frac14\left[1+\frac{\pi(A_1-A_2)}{c_l}\right]
$$

For a flat plate $x_{cp} = c/4$. For a cambered aerofoil it moves with $\alpha$ (towards $+\infty$ as $c_l\to0$), which is why the AC is the preferred reference point. See [[Aerodynamic Centre and Centre of Pressure]].

![[tat_loading.png|560]]

> [!example] NACA 6500: $z = 0.24x(1-x)$ (unit chord)
> - $\dfrac{dz}{dx} = 0.24(1-2x) = 0.24\cos\theta_0$, so $A_0=\alpha$, $A_1 = 0.24$, and all others are zero.
> - $c_l = \pi(2\alpha+0.24)$, $\alpha_{L=0} = -0.12$ rad $= -6.88^\circ$.
> - $c_{m,c/4} = \frac\pi4(0-0.24) = -0.06\pi = -0.188$.
> - $\dfrac{x_{cp}}{c} = \dfrac14\left(1+\dfrac{0.24}{2\alpha+0.24}\right)$. At $\alpha=0$: $x_{cp} = 0.5c$. As $\alpha\to\alpha_{L=0}$: $x_{cp}\to\infty$.
> - Loading: $\Delta C_p = 4\alpha\dfrac{1+\cos\theta}{\sin\theta}+0.96\sin\theta$. At $\alpha = 0$ the LE carries no load. This is the **ideal angle of attack**, where $A_0=0$.

> [!example] Parabolic camber $z/c = \epsilon\,\frac xc\left(1-\frac xc\right)$ (appears in about 8 past papers)
> - $dz/dx = \epsilon\cos\theta_0$, so $A_0=\alpha$, $A_1=\epsilon$, $A_{n\ge2}=0$.
> - $c_l = 2\pi\alpha+\pi\epsilon$, $\alpha_{L=0} = -\epsilon/2$, $c_{m,c/4} = -\pi\epsilon/4$.
> - Maximum camber is at $x=c/2$ with value $z_{max}/c = \epsilon/4$.

## 4.6 Trailing-edge flaps

Model a flap as a camber line (unit chord, hinge at $x_h$, deflection $\eta$ or $\phi$ downward):

$$
\frac{dz}{dx} = \begin{cases}0 & 0<\theta_0<\theta_h\\ -\phi & \theta_h<\theta_0<\pi\end{cases},\qquad \cos\theta_h = 1-2x_h
$$

For a **25% flap** ($x_h = 0.75$): $\theta_h = 2\pi/3$.

$$
A_0 = \alpha+\frac{\phi}{3},\quad A_1 = \frac{\sqrt3}{\pi}\phi,\quad A_2 = -\frac{\sqrt3}{2\pi}\phi
$$

$$
c_l = 2\pi\alpha + \left(\frac{2\pi}{3}+\sqrt3\right)\phi = 2\pi\alpha+3.826\,\phi,\qquad c_{m,c/4} = -\frac{3\sqrt3}{8}\phi = -0.6495\,\phi,\qquad \alpha_{L=0} = -0.609\,\phi
$$

Full derivation and general-hinge formulae: [[Trailing-Edge Flap in Thin Aerofoil Theory]].

**High-lift devices**: $V_{stall} = \sqrt{2W/(\rho_\infty S C_{L,max})}$.
- **TE flaps** make $\alpha_{L=0}$ more negative and raise $C_{L,max}$.
- **LE slats** increase the stall angle and $C_{L,max}$ but do not change $\alpha_{L=0}$.
- Multi-element flaps effectively add camber.

## 4.7 Real flow effects

**[[Kelvin's Circulation Theorem]]**: $D\Gamma/Dt = 0$. When an aerofoil starts moving, it sheds a **starting vortex**. The circulation around the aerofoil is **equal and opposite** to that of the starting vortex, so the total stays zero.

**[[Aerofoil Stall]]**:

| Type | Typical aerofoils | Behaviour |
|---|---|---|
| **Leading-edge stall** | $t/c \lesssim 15\%$ (e.g. NACA 4412) | Sudden separation from the LE over the whole upper surface, with a sharp drop in $c_l$ |
| **Trailing-edge stall** | Thick (e.g. NACA 4421) | Separation creeps forward from the TE and $c_l$ drops gradually |
| **Thin-aerofoil stall** | Flat plate | Separation bubble even at low $\alpha$ that grows with $\alpha$; lower $c_{l,max}$, gentle stall |

**Panel methods**: distribute sources and vortices over panels and solve $\mathbf{A}\mathbf{x} = \mathbf{B}$ for their strengths with tangency at the control points. XFOIL/XFLR5 add viscous BL coupling (more in [[SESA3043 Advanced Aeronautics]]).

## Thin-aerofoil theory: assumptions and summary
- Incompressible, irrotational, inviscid (drag $=0$), small $\alpha$, small thickness and camber.
- $L' = \rho V_\infty\Gamma$, $\Delta p = \rho V_\infty\gamma$, $\Gamma = \int\gamma\,ds$, $\gamma(TE)=0$.
- $C_l = 2\pi(\alpha-\alpha_{L=0}) = \pi(2A_0+A_1)$, $dC_l/d\alpha = 2\pi$.
- $c_{m,c/4} = \frac\pi4(A_2-A_1)$. The quarter chord is the aerodynamic centre, and the centre of pressure moves with $\alpha$.

## Links
- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T3 - Potential Flow]] · Next: [[SESA2022 T5 - Finite Wing Theory]]
- Problems: [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]
- Maths: Fourier series and orthogonality (MATH2048)
- Numerical TAT code: SESA2029 Digital Aerospace Methods
- Feeds: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] (tailplane $a_1, a_2$ and $c_{m,0}$), [[SESA3043 Advanced Aeronautics]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf` (slides 1–63), transcript `TAT.txt`
- Anderson, *Fundamentals of Aerodynamics*, Ch. 4
