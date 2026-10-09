---
title: "SESA2022 T3 - Potential Flow"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 3: Potential Flow"
order: 3
tags:
  - sesa2022
  - potential-flow
  - inviscid-flow
aliases: ["Potential Flow"]
date: 2026-09-23
status: complete
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[Streamfunction and Velocity Potential]]"]
next_topics: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
key_concepts: ["[[Elementary Potential Flows]]", "[[Flow Past a Cylinder]]", "[[Rankine Oval]]", "[[Kutta-Joukowski Theorem]]", "[[D'Alembert's Paradox]]", "[[Method of Images]]"]
tutorial_sheets: ["[[SESA2022 Tutorial 3 - Potential Flow Solutions]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/PF/Topic_3_Potential_Flow.ipynb", "02 - Sources/PF/PFs.txt"]
---

# SESA2022 T3 - Potential Flow

> [!abstract] Summary
> For **steady, inviscid, irrotational, incompressible** flow, both $\psi$ and $\phi$ satisfy **Laplace's equation**, which is linear, so solutions **superpose** like LEGO bricks. There are four bricks (uniform flow, source/sink, doublet, vortex). Any streamline can be a solid wall ($\mathbf V\cdot\hat n=0$), so we build flows past bodies by adding bricks and picking the body streamline from a boundary condition. Velocities come from derivatives of $\psi$, and pressure comes from **Bernoulli**. The key results are **D'Alembert's paradox** (zero drag), the **Kutta–Joukowski theorem** $L'=\rho V_\infty\Gamma$, and the **method of images** for walls.

## Key Concepts
- [[Streamfunction and Velocity Potential]]
- [[Elementary Potential Flows]]: uniform flow, source/sink, doublet, vortex
- [[Flow Past a Cylinder]] (non-lifting and lifting)
- [[Rankine Oval]] (and Rankine half-body)
- [[Kutta-Joukowski Theorem]] and [[D'Alembert's Paradox]]
- [[Method of Images]]

---

## 1. Coordinates and conventions (important for signs)

The course uses the **$x$–$z$ plane**: $x$ is streamwise, $z$ is vertical, and $y$ points *into the page* (spanwise) to keep a right-handed system. Velocity components are $u$ (along $x$) and $w$ (along $z$).

- The vorticity component that matters is along $y$: $\omega_y = \dfrac{\partial u}{\partial z} - \dfrac{\partial w}{\partial x}$.
- **Clockwise circulation is positive** ($\Gamma > 0$ clockwise).
- Irrotational: $\dfrac{\partial u}{\partial z} = \dfrac{\partial w}{\partial x}$.

> [!warning] Older papers (pre-2020) use the $x$–$y$ plane with $u = \partial\psi/\partial y$, $v = -\partial\psi/\partial x$. The algebra is identical.

## 2. Governing equations

Euler (steady, 2D):

$$
\frac{\partial u}{\partial x}+\frac{\partial w}{\partial z}=0,\quad u\frac{\partial u}{\partial x}+w\frac{\partial u}{\partial z}=-\frac1\rho\frac{\partial p}{\partial x},\quad u\frac{\partial w}{\partial x}+w\frac{\partial w}{\partial z}=-\frac1\rho\frac{\partial p}{\partial z}
$$

| | Cartesian | Polar |
|---|---|---|
| Potential | $u = \dfrac{\partial\phi}{\partial x},\; w=\dfrac{\partial\phi}{\partial z}$ | $V_r = \dfrac{\partial\phi}{\partial r},\; V_\theta = \dfrac1r\dfrac{\partial\phi}{\partial\theta}$ |
| Streamfunction | $u = \dfrac{\partial\psi}{\partial z},\; w=-\dfrac{\partial\psi}{\partial x}$ | $V_r=\dfrac1r\dfrac{\partial\psi}{\partial\theta},\; V_\theta=-\dfrac{\partial\psi}{\partial r}$ |

- **Incompressible** means $\nabla^2\phi = 0$, and $\psi$ satisfies continuity automatically.
- **Irrotational** means $\nabla^2\psi = 0$, and $\phi$ is irrotational automatically.

$$
\nabla^2\phi = \frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial z^2}=0,\qquad \nabla^2\psi = 0\quad\Rightarrow\quad \psi = \psi_1+\psi_2+\dots+\psi_n
$$

## 3. Pressure from velocity

Bernoulli holds between **any two points** in potential flow:

$$
p + \tfrac12\rho(u^2+w^2) = p_\infty + \tfrac12\rho U_\infty^2\quad\Rightarrow\quad \boxed{C_p = \frac{p-p_\infty}{\tfrac12\rho U_\infty^2} = 1-\frac{V_r^2+V_\theta^2}{U_\infty^2} = 1-\frac{u^2+w^2}{U_\infty^2}}
$$

If there is **no freestream** (for example a lone vortex or source), use a stated reference velocity $U_{ref}$ and pressure: $C_p = 1-(u^2+w^2)/U_{ref}^2$. If $U_{ref}=0$ you cannot form $C_p$, but you can still compute $p$.

## 4. The LEGO bricks

The full table is in [[Elementary Potential Flows]]. For an element at $(x_0,z_0)$: $r=\sqrt{(x-x_0)^2+(z-z_0)^2}$, $\theta=\tan^{-1}\!\frac{z-z_0}{x-x_0}$.

| Brick | $\psi$ | $\phi$ | Velocity |
|---|---|---|---|
| Uniform flow at angle $\alpha$ | $U_\infty(z\cos\alpha - x\sin\alpha)$ | $U_\infty(x\cos\alpha + z\sin\alpha)$ | $(U_\infty\cos\alpha,\,U_\infty\sin\alpha)$ |
| Source ($\Lambda>0$) / sink ($\Lambda<0$) | $\dfrac{\Lambda}{2\pi}\theta$ | $\dfrac{\Lambda}{2\pi}\ln r$ | $V_r = \dfrac{\Lambda}{2\pi r}$ |
| Doublet ($\kappa=\Lambda l$) | $-\dfrac{\kappa}{2\pi}\dfrac{\sin\theta}{r}$ | $\dfrac{\kappa}{2\pi}\dfrac{\cos\theta}{r}$ | $V_r=-\dfrac{\kappa\cos\theta}{2\pi r^2},\ V_\theta=-\dfrac{\kappa\sin\theta}{2\pi r^2}$ |
| Vortex (clockwise $\Gamma>0$) | $\dfrac{\Gamma}{2\pi}\ln r$ | $-\dfrac{\Gamma}{2\pi}\theta$ | $V_\theta = -\dfrac{\Gamma}{2\pi r}$ |

- **Source strength**: $\Lambda = q/l$, the volume flow rate per unit depth, from $q=\int_0^{2\pi}V_r\,l\,r\,d\theta = 2\pi r V_r l$.
- **Doublet**: a source–sink pair at spacing $l\to0$ with $\Lambda l=\kappa$ held constant. $\kappa>0$ means source on the left, sink on the right.
- **Circulation**: $\Gamma = \oint_C \mathbf V\cdot d\mathbf s = \iint_S(\nabla\times\mathbf V)\cdot d\mathbf S$. It is zero if the flow inside $C$ is irrotational. A potential vortex concentrates all the vorticity at a point.

## 5. How to build a flow

1. Superpose bricks using physical intuition.
2. Find the streamline that represents the body using a boundary condition:
   - **Stagnation point** ($\mathbf V = 0$), then $\psi_{body} = \psi(\text{stag. pt})$
   - **No normal flow** at a wall
   - A streamline **through a given point**
   - The streamline's **shape** matching the geometry
3. The remaining streamlines give the flow around the body. Differentiate to get velocities, then use Bernoulli for pressure.

Numerically (Jupyter notebook): build a mesh with `np.meshgrid`, compute $\psi$, get velocities with `np.gradient(psi)` ($u = \partial\psi/\partial z$, $w=-\partial\psi/\partial x$), then compute $C_p$. **Grid resolution matters**: Tutorial 3 Q3 gives $C_p=-10.5$ on a coarse grid versus the true $0.872$.

---

## 6. Example 1: uniform flow + source (Rankine half-body)

$$
\psi = U_\infty r\sin\theta + \frac{\Lambda}{2\pi}\theta
$$

- **Stagnation point**: $V_r = U_\infty\cos\theta + \frac{\Lambda}{2\pi r}=0$ and $V_\theta = -U_\infty\sin\theta = 0$, so $\theta=\pi$ and $r = \dfrac{\Lambda}{2\pi U_\infty}$.
- **Body streamline**: $\psi_0 = \Lambda/2$, so the body surface is $r = \dfrac{\Lambda(1-\theta/\pi)}{2U_\infty\sin\theta}$.
- **Thickness far downstream**: $U_\infty h = \Lambda/2$, so $2h = \Lambda/U_\infty$ (all the source fluid is contained within the body).
- On the body at $x=0$ ($\theta=\pi/2$, $r=\Lambda/4U_\infty$): $V_r = 2U_\infty/\pi$, $V_\theta = -U_\infty$, so $C_p = -4/\pi^2 = -0.405$.

## 7. Example 2: flow past a circular cylinder (uniform flow + doublet)

$$
\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right),\qquad R^2 = \frac{\kappa}{2\pi V_\infty}
$$

- $V_r = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right)$, which is zero on $r=R$, so the circle is the streamline $\psi=0$.
- $V_\theta = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)$. On the surface $V_\theta = -2V_\infty\sin\theta$.
- Stagnation at $\theta = 0,\pi$. Maximum speed is $2V_\infty$ at the top and bottom.

$$
\boxed{C_p = 1-4\sin^2\theta}\qquad C_p(0)=1,\quad C_p(\pi/2)=-3,\quad C_p = 0\text{ at }\theta=30^\circ,150^\circ,\dots
$$

The distribution is symmetric, so there is **zero lift and zero drag** ([[D'Alembert's Paradox]]).

**Real flows**: viscosity causes separation and a wake ($Re=1.54$: attached; $Re=26$: twin vortices; $Re=140$: vortex street). Drag crisis at $Re\sim3\times10^5$.

## 8. Example 3: Rankine oval (uniform flow + source at $-b$ + sink at $+b$)

$$
\psi = V_\infty z + \frac{\Lambda}{2\pi}(\theta_1-\theta_2),\quad \theta_1=\tan^{-1}\frac{z}{x+b},\ \theta_2=\tan^{-1}\frac{z}{x-b}
$$

- Stagnation points on $z=0$ where $u=0$:

$$
V_\infty+\frac{\Lambda}{2\pi}\left[\frac{1}{x+b}-\frac{1}{x-b}\right]=0\;\Rightarrow\; x_{end} = \pm\sqrt{b^2+\frac{\Lambda b}{\pi V_\infty}} = \pm L/2
$$

- Body: $\psi = 0$. The top $z_{top}$ (at $x=0$) needs a **numerical** solution of

$$
V_\infty z_{top} + \frac{\Lambda}{\pi}\tan^{-1}\!\left(\frac{z_{top}}{b}\right) - \frac{\Lambda}{2} = 0
$$

  For a **slender oval** ($\theta_1\ll1$): $z_{top}\approx \dfrac{\pi b}{2+2\pi bV_\infty/\Lambda}$.
- Aspect ratio: $L/H = x_{end}/z_{top}$.
- Top velocity and pressure:

$$
u_{top} = V_\infty + \frac{\Lambda b}{\pi b^2}\frac{1}{1+z_{top}^2/b^2},\qquad C_p = -\frac{2\Lambda}{\pi V_\infty b(1+z_{top}^2/b^2)} - \frac{\Lambda^2}{\pi^2V_\infty^2b^2(1+z_{top}^2/b^2)^2}
$$

![[pf_rankine_oval.png|620]]

See [[Rankine Oval]]. Tutorial 3 Q4 uses the semi-oval as a hangar.

## 9. Example 4: lifting flow over a cylinder (uniform flow + doublet + vortex)

$$
\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right)+\frac{\Gamma}{2\pi}\ln\frac{r}{R}
$$

The constant $-\frac{\Gamma}{2\pi}\ln R$ makes $\psi=0$ on the cylinder.

$$
V_r = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right),\qquad V_\theta = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)-\frac{\Gamma}{2\pi r}
$$

**Stagnation points:**
- **On the cylinder** if $\Gamma \le 4\pi V_\infty R$: $\sin\theta = -\dfrac{\Gamma}{4\pi V_\infty R}$. For $\Gamma > 0$ both points move to the lower half.
- **Off the cylinder** if $\Gamma > 4\pi V_\infty R$: $\theta = -\pi/2$ and $r = \dfrac{\Gamma}{4\pi V_\infty}\pm\sqrt{\left(\dfrac{\Gamma}{4\pi V_\infty}\right)^2-R^2}$. Take the root with $r>R$.

![[pf_lifting_cylinder.png]]

**Surface pressure**:

$$
C_p = 1-\left(2\sin\theta+\frac{\Gamma}{2\pi RV_\infty}\right)^2 = 1-\left[4\sin^2\theta+\frac{2\Gamma\sin\theta}{\pi RV_\infty}+\left(\frac{\Gamma}{2\pi RV_\infty}\right)^2\right]
$$

![[pf_cylinder_cp.png|620]]

**Forces**:
- Integrating $dF = -p\,dS$ around the cylinder: $c_d = -\frac12\int_0^{2\pi}C_p\cos\theta\,d\theta = 0$ (D'Alembert).
- $c_l = -\frac12\int_0^{2\pi}C_p\sin\theta\,d\theta = \dfrac{\Gamma}{RV_\infty}$.
- Hence

$$
\boxed{L' = \tfrac12\rho V_\infty^2(2R)\,c_l = \rho V_\infty\Gamma}\quad\text{(Kutta–Joukowski)}
$$

Using $\int_0^{2\pi}\sin^2\theta\,d\theta = \pi$, and noting that the odd powers ($\sin\theta$, $\sin^3\theta$) and $\cos\theta\times$anything-in-$\sin\theta$ integrate to zero.

**Magnus effect**: a spinning cylinder or ball generates lift. See [[Kutta-Joukowski Theorem]].

## 10. Kutta–Joukowski theorem

$$
L' = \rho_\infty V_\infty\Gamma
$$

This holds for **any** 2D body shape with net circulation $\Gamma$, independent of the integration path as long as the path encloses the body. It was derived by Kutta and Joukowski (≈1902–1906) using complex variables and conformal mapping.

## 11. Method of images

To enforce $\mathbf V\cdot\hat n = 0$ at a wall, place an **image** element of equal magnitude mirrored across the wall:
- **Sources and sinks**: image has the **same sign**
- **Vortices and doublets** (axis normal to the wall): image has the **opposite sign**

> [!example] Vortex near a wall (lecture Example 5)
> Freestream plus vortex $\Gamma$ at $(0,a)$ plus image $-\Gamma$ at $(0,-a)$:
>
> $$\psi = U_\infty z + \frac{\Gamma}{2\pi}\ln\sqrt{x^2+(z-a)^2} - \frac{\Gamma}{2\pi}\ln\sqrt{x^2+(z+a)^2}$$
>
> On $z=0$: $w = 0$ ✔ and $u = U_\infty - \dfrac{\Gamma a}{\pi(x^2+a^2)}$, so
>
> $$C_p(x,0) = -\frac{\Gamma^2a^2}{\pi^2U_\infty^2(x^2+a^2)^2}+\frac{2\Gamma a}{\pi U_\infty(x^2+a^2)}$$

See [[Method of Images]]. Applications: ground effect of a take-off (starting) vortex, rotorcraft near walls, fans near walls (2022-23 exam), vortex in a corner (2020-21 exam, which needs three images).

---

## Summary
- Superpose the bricks and apply the boundary condition ("no normal flow", "stagnation point", "streamline through a point") to identify the body streamline.
- The other streamlines give the inviscid flow. Bernoulli is valid everywhere.
- Analytical solutions exist for special cases. Otherwise use the numerical notebook.
- The method of images handles walls.

## Links
- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T2 - Boundary Layers]] · Next: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Tutorial: [[SESA2022 Tutorial 3 - Potential Flow Solutions]]
- Maths: [[Streamfunction and Velocity Potential]] (MATH2048 vector calculus)
- Year 3: panel methods in [[SESA3043 Advanced Aeronautics]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf` (slides 1–65), notebook `Topic_3_Potential_Flow.ipynb`, transcript `PFs.txt`
- Anderson, *Fundamentals of Aerodynamics*, Ch. 3.10–3.16
