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
status: lectured
coverage: "Lectures 3–4 (2–3 Oct 2025, maths and governing equations) and 11–16 (16–24 Oct 2025)"
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[Streamfunction and Velocity Potential]]", "[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
next_topics: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
key_concepts: ["[[Elementary Potential Flows]]", "[[Flow Past a Cylinder]]", "[[Rankine Oval]]", "[[Kutta-Joukowski Theorem]]", "[[D'Alembert's Paradox]]", "[[Method of Images]]"]
tutorial_sheets: ["[[SESA2022 Tutorial 3 - Potential Flow Solutions]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/PF/Topic_3_Potential_Flow.ipynb", "02 - Sources/Lectures/SESA2022 Lecture 3.txt, 4.txt, 11.txt … 16.txt", "02 - Sources/PF/PFs.txt (earlier-year recording)"]
---

# SESA2022 T3 - Potential Flow

> [!abstract] Summary
> In steady, inviscid, irrotational, incompressible flow both $\psi$ and $\phi$ satisfy Laplace's equation, which is linear, so four elementary flows (uniform flow, source/sink, doublet and vortex) can be superposed and any streamline taken as a solid wall. Velocities come from derivatives of $\psi$ and pressures from Bernoulli. The main results are D'Alembert's paradox (zero drag), the Kutta–Joukowski theorem $L'=\rho V_\infty\Gamma$, and the method of images for walls.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a combination of uniform flow, sources, sinks, doublets or vortices (or asks you to choose one) and wants a body shape, stagnation points, velocities, $C_p$ or lift; or a wall must be modelled.
> - **Assumptions:** 2D in the $x$–$z$ plane, steady, inviscid, incompressible, irrotational; $\Gamma>0$ clockwise, $\theta$ anticlockwise from $+x$.
> - **Method:** 1. Superpose the bricks' $\psi$ (add images for walls). 2. Differentiate: $u = \partial\psi/\partial z$, $w=-\partial\psi/\partial x$ (or $V_r$, $V_\theta$). 3. Stagnation points from $u=w=0$. 4. Body streamline: $\psi_{body} = \psi(\text{stagnation point})$, or the streamline through a given point. 5. $C_p = 1-(u^2+w^2)/U_\infty^2$, then integrate for forces if needed.
> - **Common mistakes:** sign of the vortex term ($V_\theta = -\Gamma/2\pi r$ for clockwise $\Gamma>0$); forgetting that the image of a vortex has the opposite sign but the image of a source has the same sign.
> - **Exam format:** the stream functions are in the rubric; you must know which bricks to add, how to simplify, and where to set $x = 0$ or $z = 0$ (L15, ll. 536–561). Hard derivatives come with identities (L14, ll. 397–412, 1042–1050). Drag from potential flow is always zero: *"your answer should straight away be zero"* (L14, ll. 848–860).
> - Revision-lecture advice (Revision 1, ll. 368–455): $x = r\cos\theta$, $z = r\sin\theta$ and $u_r$, $u_\theta$ from $\psi$ are on the Topic 1 formula page; the velocity normal to a streamline is zero, a five-mark answer that needs a reason, not pages of derivation; answer the decision ("will erosion occur?") and the meaning of a negative $C_p$; use every value the question gives.
> - **Practise:** [[#Worked example: a spinning cylinder]] · [[SESA2022 Tutorial 3 - Potential Flow Solutions]] Q4 · [[SESA2022 Exam 2024-25 Solutions]] Q2

Take the boundary layer of [[SESA2022 T2 - Boundary Layers]] and shrink it to nothing. What is left is the outer flow: no friction, and fluid elements that slide without spinning. Such a flow has a "height map" $\phi$ whose slope is the velocity, and a family of streamlines $\psi = $ const. Both obey Laplace's equation, which is linear, so flows can simply be added.

That gives a construction kit (L13, ll. 7, 172–178). A uniform flow carries everything downstream. A source pushes fluid outwards and so bends the incoming streamlines round a blunt nose. A sink swallows it again and closes the shape. A doublet is a source and sink squeezed together, and with a uniform flow it makes a circle. A vortex adds swirl: faster on one side, slower on the other, and through Bernoulli a pressure difference, which is lift.

Because no fluid crosses a streamline, any closed streamline can be replaced by a solid body without changing the flow outside. So "what is the flow past this shape?" becomes "which bricks give a streamline of this shape?". The price of ignoring viscosity is that the pressure on a closed body always balances in the streamwise direction: zero drag (D'Alembert). Lift survives, and it depends only on the circulation: $L' = \rho V_\infty\Gamma$. What sets $\Gamma$ on a real aerofoil is the subject of [[SESA2022 T4 - Thin Aerofoil Theory]].

---

## 1. Coordinates and conventions (important for signs)

![[pf_sign_convention.png|600]]

The course uses the $x$–$z$ plane: $x$ is streamwise, $z$ is vertical, and $y$ points *into the page* (spanwise) to keep a right-handed system (L11, ll. 300–320). Velocity components are $u$ (along $x$) and $w$ (along $z$).

- The vorticity component that matters is along $y$: $\omega_y = \dfrac{\partial u}{\partial z} - \dfrac{\partial w}{\partial x}$.
- With $y$ into the page, positive $\omega_y$ is clockwise as drawn, so clockwise circulation is positive ($\Gamma > 0$ clockwise) (L11, ll. 319–320; L12, ll. 743–744; L13, ll. 16–17).
- The polar angle $\theta$, and positive $V_\theta$, still run anticlockwise from $+x$ (L13, ll. 531–532). That is why a positive (clockwise) vortex has $V_\theta = -\Gamma/(2\pi r)$ (L13, ll. 26–27).
- Irrotational: $\dfrac{\partial u}{\partial z} = \dfrac{\partial w}{\partial x}$.

> [!warning] Two conventions in the same module
> In the maths revision (L3, ll. 718–722) positive vorticity is anticlockwise: that is the $x$–$y$ plane with $z$ out of the page. From Lecture 11 onwards the aerodynamic $x$–$z$ plane flips it to clockwise. Older papers (pre-2020) use the $x$–$y$ plane with $u = \partial\psi/\partial y$, $v = -\partial\psi/\partial x$; the algebra is identical with $z\to y$. Always check which axes a question uses.

## 2. Governing equations

### Euler equations (steady, 2D, inviscid, incompressible)

$$
\frac{\partial u}{\partial x}+\frac{\partial w}{\partial z}=0
$$

$$
u\frac{\partial u}{\partial x}+w\frac{\partial u}{\partial z}=-\frac1\rho\frac{\partial p}{\partial x},\qquad u\frac{\partial w}{\partial x}+w\frac{\partial w}{\partial z}=-\frac1\rho\frac{\partial p}{\partial z}
$$

The viscous (Navier–Stokes) terms were shown but not derived (L4, ll. 466–480).

### Velocity potential and streamfunction

| | Cartesian | Polar |
|---|---|---|
| Potential | $u = \dfrac{\partial\phi}{\partial x},\; w=\dfrac{\partial\phi}{\partial z}$ | $V_r = \dfrac{\partial\phi}{\partial r},\; V_\theta = \dfrac1r\dfrac{\partial\phi}{\partial\theta}$ |
| Streamfunction | $u = \dfrac{\partial\psi}{\partial z},\; w=-\dfrac{\partial\psi}{\partial x}$ | $V_r=\dfrac1r\dfrac{\partial\psi}{\partial\theta},\; V_\theta=-\dfrac{\partial\psi}{\partial r}$ |

### Streamfunction from the flow between two streamlines

Label each streamline with a number $\psi$, constant along it (L4, ll. 56–142). Between neighbouring streamlines $\psi$ and $\psi+d\psi$ no fluid crosses either line, so $d\psi$ is the volume flow rate per unit depth passing between them. Across a short line element $(dx, dz)$ that flow rate is $u\,dz-w\,dx$:

$$
d\psi = u\,dz-w\,dx.
$$

Compare with the total differential $d\psi = \frac{\partial\psi}{\partial x}dx+\frac{\partial\psi}{\partial z}dz$:

$$
u = \frac{\partial\psi}{\partial z},\qquad w = -\frac{\partial\psi}{\partial x}.
$$

Only differences of $\psi$ mean anything; the value on one streamline can be chosen freely, which is why bodies are usually put on $\psi = 0$ (L14, ll. 111–117; L15, ll. 182–186).

> [!important] When each function exists
> $\psi$ exists for any 2D incompressible flow, rotational or not. $\phi$ exists only for irrotational flow, but works in 2D or 3D (L11, ll. 232–237). Streamlines and equipotentials are perpendicular: their slopes are $w/u$ and $-u/w$, whose product is $-1$. Use this as a check on numerical plots (L4, ll. 733–759).

### Why both satisfy Laplace's equation

**$\phi$ is irrotational automatically.** Substitute $u = \phi_x$, $w = \phi_z$ into $\omega_y$:

$$
\omega_y = \frac{\partial}{\partial z}\frac{\partial\phi}{\partial x}-\frac{\partial}{\partial x}\frac{\partial\phi}{\partial z} = 0
$$

(equal mixed derivatives). Continuity then gives Laplace:

$$
\frac{\partial u}{\partial x}+\frac{\partial w}{\partial z} = \frac{\partial^2\phi}{\partial x^2}+\frac{\partial^2\phi}{\partial z^2} = 0
$$

**$\psi$ satisfies continuity automatically.** Substitute $u = \psi_z$, $w = -\psi_x$:

$$
\frac{\partial u}{\partial x}+\frac{\partial w}{\partial z} = \frac{\partial^2\psi}{\partial x\,\partial z}-\frac{\partial^2\psi}{\partial z\,\partial x} = 0
$$

**Irrotationality then gives Laplace:**

$$
\omega_y = \frac{\partial u}{\partial z}-\frac{\partial w}{\partial x} = \frac{\partial^2\psi}{\partial z^2}+\frac{\partial^2\psi}{\partial x^2} = 0
$$

So for incompressible, irrotational flow (L4, ll. 640–726; L11, ll. 175–209):

$$
\nabla^2\phi = 0,\qquad \nabla^2\psi = 0\quad\Rightarrow\quad \psi = \psi_1+\psi_2+\dots+\psi_n
$$

The last step is superposition: if each $\psi_i$ satisfies the linear equation $\nabla^2\psi_i = 0$, so does their sum.

A streamline can be a wall because along a curve $\psi = $ const, $d\psi = \psi_x\,dx+\psi_z\,dz = -w\,dx+u\,dz = 0$, so $dz/dx = w/u$ and the velocity is tangent to the curve. No fluid crosses it, so a solid surface along it changes nothing outside.

## 3. Pressure from velocity

### Bernoulli between any two points

Assumptions: steady, inviscid, incompressible, irrotational, no body force.

Use the identity $(\mathbf V\cdot\nabla)\mathbf V = \nabla(\tfrac12V^2)-\mathbf V\times(\nabla\times\mathbf V)$ in the Euler momentum equation:

$$
\nabla\left(\tfrac12V^2\right)-\mathbf V\times\boldsymbol\omega = -\frac1\rho\nabla p.
$$

Irrotational, so $\boldsymbol\omega = 0$:

$$
\nabla\left(\frac p\rho+\tfrac12V^2\right) = 0.
$$

The gradient is zero in every direction, so $p+\tfrac12\rho V^2$ is the same constant everywhere, not just along a streamline (L11, ll. 518–548).

> [!note]- The lecture's route, without vector identities (L4, ll. 544–591)
> Irrotational means $\partial w/\partial x = \partial u/\partial z$. In the $x$-momentum equation $u\,u_x+w\,u_z = -p_x/\rho$, replace $u_z$ by $w_x$: the left side becomes $\frac{\partial}{\partial x}\tfrac12(u^2+w^2)$. Integrating in $x$ gives $p+\tfrac12\rho(u^2+w^2) = f(z)$. The $z$-momentum equation, with $w_x$ replaced by $u_z$, gives the same expression $= g(x)$. A function of $z$ alone can equal a function of $x$ alone only if both are the same constant.
>
> Without irrotationality, the same equations in streamline coordinates give Bernoulli along a streamline only, plus a normal balance $\partial p/\partial n = \rho V^2/R$ across curved streamlines: pressure rises away from the centre of curvature. That is the lecture's "centrifugal" picture of lift (L1, ll. 330–365; L4, ll. 330–400).

So between any two points:

$$
p + \tfrac12\rho(u^2+w^2) = p_\infty + \tfrac12\rho U_\infty^2
$$

Rearrange and divide by $\tfrac12\rho U_\infty^2$:

$$
\boxed{C_p = \frac{p-p_\infty}{\tfrac12\rho U_\infty^2} = 1-\frac{u^2+w^2}{U_\infty^2} = 1-\frac{V_r^2+V_\theta^2}{U_\infty^2}}
$$

If there is no freestream (for example a lone vortex or source), use a stated reference velocity $U_{ref}$ and pressure: $C_p = 1-(u^2+w^2)/U_{ref}^2$. If $U_{ref}=0$ you cannot form $C_p$, but you can still compute $p$.

## 4. The LEGO bricks

![[pf_lego_bricks.png|820]]

For an element at $(x_0,z_0)$: $r=\sqrt{(x-x_0)^2+(z-z_0)^2}$, $\theta=\tan^{-1}\!\frac{z-z_0}{x-x_0}$. Summary table in [[Elementary Potential Flows]].

| Brick | $\psi$ | $\phi$ | Velocity |
|---|---|---|---|
| Uniform flow at angle $\alpha$ | $U_\infty(z\cos\alpha - x\sin\alpha)$ | $U_\infty(x\cos\alpha + z\sin\alpha)$ | $(U_\infty\cos\alpha,\,U_\infty\sin\alpha)$ |
| Source ($\Lambda>0$) / sink ($\Lambda<0$) | $\dfrac{\Lambda}{2\pi}\theta$ | $\dfrac{\Lambda}{2\pi}\ln r$ | $V_r = \dfrac{\Lambda}{2\pi r}$ |
| Doublet ($\kappa=\Lambda l$) | $-\dfrac{\kappa}{2\pi}\dfrac{\sin\theta}{r}$ | $\dfrac{\kappa}{2\pi}\dfrac{\cos\theta}{r}$ | $V_r=-\dfrac{\kappa\cos\theta}{2\pi r^2},\ V_\theta=-\dfrac{\kappa\sin\theta}{2\pi r^2}$ |
| Vortex (clockwise $\Gamma>0$) | $\dfrac{\Gamma}{2\pi}\ln r$ | $-\dfrac{\Gamma}{2\pi}\theta$ | $V_\theta = -\dfrac{\Gamma}{2\pi r}$ |

### Uniform flow

Velocity $(U_\infty\cos\alpha, U_\infty\sin\alpha)$. Integrate $\psi_z = u$: $\psi = U_\infty z\cos\alpha+f(x)$. Then $-\psi_x = -f'(x) = w = U_\infty\sin\alpha$, so $f = -U_\infty x\sin\alpha$. For $\alpha = 0$: $\psi = U_\infty z = U_\infty r\sin\theta$.

### Source and sink: strength from the flow rate

A source is a point where fluid is created: divergence is non-zero only at that point, and mass is conserved everywhere else, so the same total flow crosses every circle round it (L12, ll. 118–147). It pushes out a volume flow rate $q$ through a cylinder of radius $r$ and depth $l$ (L12, ll. 149–260; the slide omits the $r$, l. 176):

$$
q = \int_0^{2\pi}V_r\,(l\,r\,d\theta) = 2\pi r\,l\,V_r.
$$

Define the strength as flow rate per unit depth, $\Lambda = q/l$:

$$
V_r = \frac{\Lambda}{2\pi r},\qquad V_\theta = 0.
$$

Streamfunction: $\frac1r\psi_\theta = V_r$ gives $\psi_\theta = \Lambda/2\pi$, so $\psi = \frac{\Lambda}{2\pi}\theta$ (and $-\psi_r = 0 = V_\theta$ ✔). Potential: $\phi_r = V_r$ gives $\phi = \frac{\Lambda}{2\pi}\ln r$. $\Lambda>0$ source, $\Lambda<0$ sink (L12, ll. 237–241). Some papers write $Q$ for $\Lambda$ (L12, l. 284).

### Doublet: the limit of a source–sink pair

The lecture shows the result without derivation (*"I don't need you to derive this"*, L12, l. 526). Here is the limit.

Place a source $+\Lambda$ at $(-l/2,0)$ and a sink $-\Lambda$ at $(+l/2,0)$. Their streamfunctions add:

$$
\psi = \frac{\Lambda}{2\pi}(\theta_1-\theta_2),
$$

where $\theta_1$, $\theta_2$ are the polar angles of $P$ seen from the source and from the sink. For $l\ll r$ the angle subtended at $P$ by the pair is small. Geometry gives $\theta_1-\theta_2 = -\Delta\theta$, with $\Delta\theta \approx l\sin\theta/r$ (the projection of the spacing perpendicular to the ray, divided by $r$):

$$
\psi \approx -\frac{\Lambda}{2\pi}\frac{l\sin\theta}{r}.
$$

Let $l\to0$ and $\Lambda\to\infty$ with $\kappa = \Lambda l$ fixed:

$$
\boxed{\psi = -\frac{\kappa}{2\pi}\frac{\sin\theta}{r}}
$$

Velocities: $V_r = \frac1r\psi_\theta = -\frac{\kappa\cos\theta}{2\pi r^2}$, $V_\theta = -\psi_r = -\frac{\kappa\sin\theta}{2\pi r^2}$. In Cartesian form $\psi = -\frac{\kappa}{2\pi}\frac{z}{x^2+z^2}$: the streamlines are circles through the origin, tangent to the $x$ axis. $\kappa>0$ means source on the left, sink on the right.

### Vortex and circulation

Circulation round a closed curve $C$, by Stokes' theorem:

$$
\Gamma = \oint_C \mathbf V\cdot d\mathbf s = \iint_S(\nabla\times\mathbf V)\cdot d\mathbf S.
$$

It is zero if the flow is irrotational everywhere inside $C$; a non-zero $\Gamma$ means vorticity is enclosed somewhere inside $C$ (the lecture words this the other way round, L12, ll. 745–747). A point vortex concentrates all the vorticity at one point, so $\Gamma$ is the same for every curve round it, and zero for curves that do not enclose it (L12, ll. 748–757).

Take a circle of radius $r$ traversed clockwise (the positive sense here). The flow speed on it is $|V_\theta|$, so $\Gamma = 2\pi r|V_\theta|$. A clockwise flow has negative $V_\theta$ (anticlockwise-positive), so

$$
V_\theta = -\frac{\Gamma}{2\pi r},\qquad V_r = 0.
$$

Then $-\psi_r = V_\theta$ gives $\psi = \frac{\Gamma}{2\pi}\ln r$, and $\frac1r\phi_\theta = V_\theta$ gives $\phi = -\frac{\Gamma}{2\pi}\theta$.

A point vortex is irrotational away from its centre even though the fluid goes round in circles. Elements orbit the centre without spinning about their own axes, because the outer side of each element moves more slowly ($V_\theta\propto1/r$) than the inner side, like a Ferris-wheel car that stays upright.

## 5. How to build a flow

1. Superpose bricks using physical intuition.
2. Find the streamline that represents the body using a boundary condition (L13, ll. 340–348, *"the main thing that you need to bring to the table in the exam"*):
   - Stagnation point ($\mathbf V = 0$), then $\psi_{body} = \psi(\text{stag. pt})$
   - No normal flow at a wall
   - A streamline through a given point
   - The streamline's shape matching the geometry
3. The remaining streamlines give the flow around the body. Differentiate to get velocities, then use Bernoulli for pressure.

Choose polar or Cartesian coordinates, whichever is easier, unless the question specifies (L13, ll. 325–336). In the exam, functions will be easy to differentiate and difficult identities will be supplied (L13, ll. 351–354; L14, ll. 1040–1050).

Numerically (Jupyter notebook, potential-flow computing lab): build a mesh with `np.meshgrid`, compute $\psi$, get velocities with `np.gradient(psi)` ($u = \partial\psi/\partial z$, $w=-\partial\psi/\partial x$), then compute $C_p$ (L11, ll. 455–504). Grid resolution matters: Tutorial 3 Q3 gives $C_p=-10.5$ on a coarse grid versus the true $0.872$.

> [!warning] Notebook pitfalls (from the lectures)
> - `np.gradient` on a meshgrid array returns the derivative along the rows ($z$) first, and returns differences, not derivatives, unless you divide by the spacing (L3, ll. 246–253; L11, ll. 495–508).
> - Elements not at the origin: use $x-x_0$, $z-z_0$ in $r$ and $\theta$ (`arctan2`) (L12, ll. 295–307).
> - Point singularities give garbage values nearby; mask them out (optional) (L12, ll. 385–457).
> - With no freestream, use a stated $U_{ref}$, never $U_\infty = 0$ (L11, ll. 529–553).
> - `fsolve` needs a sensible starting guess; values read off a discrete grid differ slightly from the analytical ones (L13, ll. 498–501; L15, ll. 389–394).

---

## 6. Example 1: uniform flow + source (Rankine half-body)

Lectured in L13, ll. 178–440.

$$
\psi = U_\infty r\sin\theta + \frac{\Lambda}{2\pi}\theta
$$

**Velocities:**

$$
V_r = \frac1r\frac{\partial\psi}{\partial\theta} = U_\infty\cos\theta+\frac{\Lambda}{2\pi r},\qquad V_\theta = -\frac{\partial\psi}{\partial r} = -U_\infty\sin\theta
$$

**Stagnation point.** $V_\theta = 0$ needs $\sin\theta = 0$, so $\theta = 0$ or $\pi$. On $\theta = 0$, $V_r = U_\infty+\Lambda/2\pi r>0$, never zero. On $\theta=\pi$:

$$
-U_\infty+\frac{\Lambda}{2\pi r} = 0\quad\Rightarrow\quad r_s = \frac{\Lambda}{2\pi U_\infty},\ \theta_s = \pi.
$$

**Body streamline.** At the stagnation point $\psi = U_\infty r_s\sin\pi+\frac{\Lambda}{2\pi}\pi = \Lambda/2$. So the body is $\psi = \Lambda/2$:

$$
U_\infty r\sin\theta+\frac{\Lambda}{2\pi}\theta = \frac\Lambda2\quad\Rightarrow\quad r = \frac{\Lambda(1-\theta/\pi)}{2U_\infty\sin\theta}.
$$

**Thickness far downstream.** As $\theta\to0$ on the body, $z = r\sin\theta\to\frac{\Lambda}{2U_\infty}$, so the half-thickness is $h = \Lambda/2U_\infty$ and the full width $2h = \Lambda/U_\infty$. Check: the source's whole output $\Lambda$ is carried downstream inside the body at speed $U_\infty$, so $U_\infty(2h) = \Lambda$ ✔.

Pressure on the body above the source ($\theta=\pi/2$, $r = \Lambda/4U_\infty$): $V_r = 0+\frac{\Lambda}{2\pi}\frac{4U_\infty}{\Lambda} = \frac{2U_\infty}{\pi}$, $V_\theta = -U_\infty$:

$$
C_p = 1-\left(\frac{4}{\pi^2}+1\right) = -\frac{4}{\pi^2} = -0.405.
$$

> [!example] Numbers
> $U_\infty = 10$ m/s, $\Lambda = 20$ m²/s: nose at $r_s = 20/(20\pi) = 0.318$ m upstream of the source, body width far downstream $2$ m, and $C_p = -0.405$ above the source whatever the numbers (Python ✔). The lecture notebook gets $-0.375$ at the nearest grid point and $-0.387$ after interpolation, against the analytical $-0.405$: a discretisation error you should be able to explain (L13, ll. 549–566).

The lecture rejects $\theta = 0$ as "flow inside a body" (L13, ll. 358–375). The direct reason is that on $\theta = 0$, $V_r = U_\infty+\Lambda/2\pi r>0$ for every $r$, so it never vanishes. Only the ratio $\Lambda/U_\infty$ matters for the shape (L13, ll. 257–267).

## 7. Example 2: flow past a circular cylinder (uniform flow + doublet)

Lectured in L14, ll. 69–830.

$$
\psi = V_\infty r\sin\theta-\frac{\kappa}{2\pi}\frac{\sin\theta}{r} = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right),\qquad R^2 \equiv \frac{\kappa}{2\pi V_\infty}
$$

**Velocities:**

$$
V_r = \frac1r\frac{\partial\psi}{\partial\theta} = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right)
$$

$$
V_\theta = -\frac{\partial\psi}{\partial r} = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)
$$

- $V_r = 0$ on $r=R$, so the circle is the streamline $\psi=0$: it can be a solid cylinder.
- On the surface $V_\theta = -2V_\infty\sin\theta$.
- Stagnation at $\theta = 0,\pi$. Maximum speed $2V_\infty$ at the top and bottom (L14, ll. 525, 652).

**Surface pressure:**

$$
C_p = 1-\frac{V_\theta^2}{V_\infty^2} = 1-\frac{4V_\infty^2\sin^2\theta}{V_\infty^2}
$$

$$
\boxed{C_p = 1-4\sin^2\theta}\qquad C_p(0)=1,\quad C_p(\pi/2)=-3,\quad C_p = 0\text{ at }\theta=30^\circ,150^\circ,\dots
$$

(L14, ll. 657–714.) The distribution is symmetric fore–aft and top–bottom, so there is zero lift and zero drag ([[D'Alembert's Paradox]]).

**Real flows**: viscosity causes separation and a wake ($Re=1.54$: attached; $Re=26$: twin vortices; $Re=140$: vortex street). Drag crisis at $Re\sim3\times10^5$, when the BL turns turbulent before separating ([[SESA2022 T2 - Boundary Layers#8. Pressure gradients and separation|T2 §8]]).

> [!warning] Low-$Re$ flow only *looks* like potential flow
> The lecture suggests that the attached, symmetric streamlines at $Re = 1.54$ are *"one of the reasons why we are still able to use potential flow modeling"* (L14, ll. 776–847). Creeping flow is the opposite limit: viscosity dominates and $C_D$ is very large, as the lecture's own drag curve shows. Potential flow is useful at high $Re$ on streamlined bodies, where viscous effects are confined to thin boundary layers ([[SESA2022 T2 - Boundary Layers|T2]]).

## 8. Example 3: Rankine oval (uniform flow + source at −b + sink at +b)

Lectured in L15, ll. 80–440.

$$
\psi = V_\infty z + \frac{\Lambda}{2\pi}(\theta_1-\theta_2),\quad \theta_1=\tan^{-1}\frac{z}{x+b},\ \theta_2=\tan^{-1}\frac{z}{x-b}
$$

### Stagnation points

By symmetry they lie on $z=0$, where $w = 0$ automatically. Differentiate: $u = \partial\psi/\partial z = V_\infty+\frac{\Lambda}{2\pi}\left[\frac{x+b}{(x+b)^2+z^2}-\frac{x-b}{(x-b)^2+z^2}\right]$. On $z=0$:

$$
V_\infty+\frac{\Lambda}{2\pi}\left[\frac{1}{x+b}-\frac{1}{x-b}\right]=0.
$$

Combine the fractions: $\frac{1}{x+b}-\frac{1}{x-b} = \frac{-2b}{x^2-b^2}$:

$$
V_\infty = \frac{\Lambda b}{\pi(x^2-b^2)}.
$$

Solve for $x$:

$$
x_{end} = \pm\sqrt{b^2+\frac{\Lambda b}{\pi V_\infty}} = \pm\frac L2
$$

### Body height

The body is $\psi = 0$ (both stagnation points have $\psi = 0$). At the top, $x=0$: $\theta_1 = \tan^{-1}(z/b)$ and $\theta_2 = \pi-\theta_1$, so $\theta_1-\theta_2 = 2\theta_1-\pi$:

$$
V_\infty z_{top} + \frac{\Lambda}{2\pi}\left(2\tan^{-1}\frac{z_{top}}{b}-\pi\right) = 0
$$

$$
V_\infty z_{top} + \frac{\Lambda}{\pi}\tan^{-1}\!\left(\frac{z_{top}}{b}\right) - \frac{\Lambda}{2} = 0
$$

This is transcendental: solve numerically (`fsolve` in the lab), or use the slender approximation in the exam, where it will be explicitly stated (L15, ll. 331–336).

Slender-oval approximation (L15, ll. 262–286). For a long, thin oval $z_{top}\ll b$, so $\theta_1$ is small and $\tan\theta_1\approx\theta_1$, i.e. $z_{top}\approx b\theta_1$:

$$
V_\infty b\theta_1-\frac{\Lambda}{2\pi}(\pi-2\theta_1) = 0.
$$

Collect $\theta_1$:

$$
\theta_1\left(V_\infty b+\frac{\Lambda}{\pi}\right) = \frac\Lambda2.
$$

So

$$
z_{top}\approx b\theta_1 = \frac{\Lambda b/2}{V_\infty b+\Lambda/\pi} = \frac{\pi b}{2+2\pi bV_\infty/\Lambda}.
$$

Aspect ratio: $L/H = x_{end}/z_{top}$.

### Top velocity and pressure

At $(0,z_{top})$ both $(x\pm b)$ terms in $u$ contribute $b/(b^2+z^2)$:

$$
u_{top} = V_\infty + \frac{\Lambda}{\pi}\frac{b}{b^2+z_{top}^2} = V_\infty\left[1+\Delta\right],\qquad \Delta \equiv \frac{\Lambda}{\pi V_\infty b(1+z_{top}^2/b^2)}
$$

and $w = 0$ there by symmetry. Then $C_p = 1-(1+\Delta)^2$:

$$
C_p = -2\Delta-\Delta^2 = -\frac{2\Lambda}{\pi V_\infty b(1+z_{top}^2/b^2)} - \frac{\Lambda^2}{\pi^2V_\infty^2b^2(1+z_{top}^2/b^2)^2}
$$

![[pf_rankine_oval.png|620]]

> [!example] Numbers: oval hangar
> $V_\infty = 10$ m/s, $b = 10$ m, $\Lambda = 100$ m²/s.
> 1. $x_{end} = \sqrt{100+100(10)/(10\pi)} = \sqrt{131.8} = 11.48$ m.
> 2. $z_{top}$: numerical root $3.83$ m; slender formula $\pi(10)/(2+2\pi(10)(10)/100) = 3.79$ m (1% low).
> 3. $L/H = 11.48/3.83 = 3.0$.
> 4. $\Delta = 100/[\pi(10)(10)(1+0.147)] = 0.278$, so $u_{top} = 12.8$ m/s and $C_p = -0.632$.
>
> Python (`brentq`) ✔. Tutorial 3 Q4 uses the semi-oval as a hangar: [[SESA2022 Tutorial 3 - Potential Flow Solutions]].

> [!warning] When the slender approximation fails (L15, ll. 338–365)
> Lecture notebook: for a long oval the aspect ratio is $13.698$ by `fsolve` and $13.699$ by the slender formula; for a fat oval $1.261$ against $1.667$, a 32% error. Use `fsolve` when you can, and say so when you approximate.

**Body or streamline coordinates.** Given $\psi$ (the body, $\psi = 0$, or the streamline through a chosen point, e.g. $\psi(0,2)$), fix $x$ and solve $\psi(x,z) = \psi_0$ for $z$ with `fsolve`, then mirror for the lower half (L15, ll. 367–395, 450–463).

Half an oval sitting on the ground is also a hill or sand dune: that was the previous year's exam question (L15, ll. 463–490). See [[Rankine Oval]].

## 9. Example 4: lifting flow over a cylinder (uniform flow + doublet + vortex)

Lectured in L15, ll. 595–680 and L16, ll. 1–295.

$$
\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right)+\frac{\Gamma}{2\pi}\ln\frac{r}{R}
$$

The constant $-\frac{\Gamma}{2\pi}\ln R$ is added so that $\psi=0$ on the cylinder, as in the non-lifting case (L15, ll. 626–632; L16, ll. 28–34).

$$
V_r = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right),\qquad V_\theta = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)-\frac{\Gamma}{2\pi r}
$$

### Stagnation points (L16, ll. 84–140)

**Case 1, on the cylinder.** On $r = R$, $V_r = 0$ always. Set $V_\theta = 0$:

$$
-2V_\infty\sin\theta-\frac{\Gamma}{2\pi R} = 0\quad\Rightarrow\quad \sin\theta = -\frac{\Gamma}{4\pi V_\infty R}.
$$

This has solutions only if $|\Gamma|\le4\pi V_\infty R$. For $\Gamma>0$ both points move into the lower half (third and fourth quadrants); they merge at the bottom when $\Gamma = 4\pi V_\infty R$.

Case 2, off the cylinder ($\Gamma > 4\pi V_\infty R$). For $r\neq R$, $V_r = 0$ needs $\cos\theta = 0$, so $\theta = \pm\pi/2$. For $\Gamma>0$ take $\theta = -\pi/2$ (below). Then $V_\theta = 0$ becomes

$$
V_\infty\left(1+\frac{R^2}{r^2}\right)-\frac{\Gamma}{2\pi r} = 0.
$$

Multiply by $r^2/V_\infty$:

$$
r^2-\frac{\Gamma}{2\pi V_\infty}r+R^2 = 0.
$$

Quadratic formula:

$$
r = \frac{\Gamma}{4\pi V_\infty}\pm\sqrt{\left(\frac{\Gamma}{4\pi V_\infty}\right)^2-R^2}.
$$

The two roots multiply to $R^2$, so one is outside the cylinder (the real stagnation point) and one inside (ignore it, L15, ll. 662–668).

![[pf_lifting_cylinder.png]]

### Surface pressure

On $r = R$, $V_\theta = -2V_\infty\sin\theta-\Gamma/(2\pi R)$:

$$
C_p = 1-\left(2\sin\theta+\frac{\Gamma}{2\pi RV_\infty}\right)^2
$$

$$
C_p = 1-4\sin^2\theta-\frac{2\Gamma\sin\theta}{\pi RV_\infty}-\left(\frac{\Gamma}{2\pi RV_\infty}\right)^2
$$

![[pf_cylinder_cp.png|620]]

### Forces from the pressure

On a surface element $dS = R\,d\theta$ with outward normal $(\cos\theta,\sin\theta)$, the pressure force is $-p\,\hat n\,dS$. Per unit span, with $\int p_\infty\hat n\,dS = 0$ round a closed body:

$$
D' = -\int_0^{2\pi}(p-p_\infty)\cos\theta\,R\,d\theta,\qquad L' = -\int_0^{2\pi}(p-p_\infty)\sin\theta\,R\,d\theta
$$

Subtracting $p_\infty$ changes nothing, because a uniform pressure integrates to zero net force round a closed body; it is done so that $C_p$ appears. (The lecture says $p_\infty$ is negligible compared with $p$, L16, ll. 234–252; it is not, both are about $10^5$ Pa.) Divide by $\tfrac12\rho V_\infty^2(2R)$, using the planform area $2R$ per unit span (L16, ll. 254–264):

$$
c_d = -\frac12\int_0^{2\pi}C_p\cos\theta\,d\theta,\qquad c_l = -\frac12\int_0^{2\pi}C_p\sin\theta\,d\theta
$$

**Drag.** Every term of $C_p$ is a function of $\sin\theta$ alone (a constant, $\sin\theta$, $\sin^2\theta$). Each, multiplied by $\cos\theta$, integrates to zero over a full period. So $c_d = 0$ (L16, ll. 285–295).

**Lift.** Multiply $C_p$ by $\sin\theta$ and integrate term by term:
- constant terms × $\sin\theta$: $\int_0^{2\pi}\sin\theta\,d\theta = 0$;
- $-4\sin^2\theta\times\sin\theta$: $\int_0^{2\pi}\sin^3\theta\,d\theta = 0$ (odd about $\theta=\pi$);
- $-\frac{2\Gamma}{\pi RV_\infty}\sin\theta\times\sin\theta$: $\int_0^{2\pi}\sin^2\theta\,d\theta = \pi$.

So

$$
c_l = -\frac12\left(-\frac{2\Gamma}{\pi RV_\infty}\pi\right) = \frac{\Gamma}{RV_\infty}.
$$

Hence

$$
L' = \tfrac12\rho V_\infty^2(2R)\frac{\Gamma}{RV_\infty}\quad\Rightarrow\quad\boxed{L' = \rho V_\infty\Gamma}\quad\text{(Kutta–Joukowski)}
$$

**Magnus effect**: a spinning cylinder or ball drags a circulation round with it and generates lift (L15, ll. 673–680; L16, ll. 423–431). See [[Kutta-Joukowski Theorem]].

### Worked example: a spinning cylinder

$V_\infty = 20$ m/s, $R = 0.5$ m, $\Gamma = 50$ m²/s (clockwise), $\rho = 1.225$ kg/m³.

1. $\Gamma/(4\pi V_\infty R) = 50/(4\pi\cdot20\cdot0.5) = 0.398<1$: stagnation points on the cylinder.
2. $\sin\theta = -0.398$: $\theta = -23.4^\circ$ and $203.4^\circ$ (both below the $x$ axis).
3. $c_l = \Gamma/(RV_\infty) = 50/10 = 5.0$; $L' = \rho V_\infty\Gamma = 1.225(20)(50) = 1225$ N/m.
4. $C_p$ top ($\theta = 90^\circ$): $1-(2+0.796)^2 = -6.82$; bottom: $1-(-2+0.796)^2 = -0.45$.
5. If $\Gamma$ rose to $150$ m²/s ($>4\pi V_\infty R = 125.7$), the stagnation point would leave the surface: $r = 0.597\pm\sqrt{0.597^2-0.25} = 0.923$ m at $\theta=-90^\circ$.

> [!check] Python check
> Numerical integration of $C_p$: $c_l = 5.000$, $c_d = 3\times10^{-16}$ ✔; $L' = 1225.0$ N/m ✔; stagnation angles $-23.45^\circ$, $203.45^\circ$ ✔.

## 10. D'Alembert's paradox and the Kutta–Joukowski theorem

**D'Alembert (1752):** in steady, inviscid, incompressible flow the drag on any closed 2D body is zero. (The lecture says *"in an incompressible, inviscid flow, drag is always zero"*, L16, l. 321: true in 2D, but a finite wing has induced drag even in inviscid flow, [[SESA2022 T5 - Finite Wing Theory|T5]].) Fore–aft symmetry kills drag; top–bottom asymmetry gives lift (L16, ll. 324–334). Experiments always show drag; the missing physics is viscosity (no-slip, boundary layers, separation), not identified until the Navier–Stokes equations decades later (L16, ll. 290–320). Even XFLR5 only adds skin friction through boundary-layer models (L16, ll. 313–319).

**Kutta–Joukowski:**

$$
L' = \rho_\infty V_\infty\Gamma
$$

It holds for any 2D body with net circulation $\Gamma$, independent of the integration path as long as the path encloses the body (Kutta, German; Joukowski, Russian; ≈1902–1906, via complex variables and conformal mapping; L16, ll. 370–380). The cylinder above is one confirmation. Lift needs circulation; potential flow cannot say how much: that is fixed by the Kutta condition in [[SESA2022 T4 - Thin Aerofoil Theory]].

## 11. Method of images

To enforce $\mathbf V\cdot\hat n = 0$ at a plane wall, place an image element of equal magnitude mirrored across the wall (L16, ll. 485–540):
- **Sources and sinks**: image has the same sign (their normal velocities cancel on the wall).
- Vortices (and doublets with axis normal to the wall): image has the opposite sign.

The image sign can be checked by drawing velocity arrows (L16, ll. 540–543). At a wall point midway between a vortex and its image, a clockwise vortex above pushes fluid one way along the wall, and the anticlockwise image below pushes it the same way along the wall but the opposite way normal to it. The normal components cancel and the tangential ones add. The same check works for sources.

### Vortex near a wall (lecture Example 5: multirotor near a wall)

Freestream $U_\infty$ plus vortex $\Gamma$ at $(0,a)$ plus image $-\Gamma$ at $(0,-a)$ (L16, ll. 544–600):

$$
\psi = U_\infty z + \frac{\Gamma}{2\pi}\ln\sqrt{x^2+(z-a)^2} - \frac{\Gamma}{2\pi}\ln\sqrt{x^2+(z+a)^2}
$$

**Wall condition.** $w = -\partial\psi/\partial x$:

$$
w = -\frac{\Gamma}{2\pi}\left[\frac{x}{x^2+(z-a)^2}-\frac{x}{x^2+(z+a)^2}\right],
$$

which is zero on $z=0$ because the two denominators are equal there ✔.

**Wall velocity.** $u = \partial\psi/\partial z$:

$$
u = U_\infty+\frac{\Gamma}{2\pi}\left[\frac{z-a}{x^2+(z-a)^2}-\frac{z+a}{x^2+(z+a)^2}\right].
$$

On $z=0$ both brackets give $-a/(x^2+a^2)$:

$$
u(x,0) = U_\infty - \frac{\Gamma a}{\pi(x^2+a^2)}.
$$

**Wall pressure.** With $\Delta = \Gamma a/[\pi U_\infty(x^2+a^2)]$, $C_p = 1-(1-\Delta)^2 = 2\Delta-\Delta^2$:

$$
C_p(x,0) = \frac{2\Gamma a}{\pi U_\infty(x^2+a^2)}-\frac{\Gamma^2a^2}{\pi^2U_\infty^2(x^2+a^2)^2}
$$

![[pf_vortex_wall_image.png|900]]

> [!example] Numbers
> $U_\infty = 5$ m/s, $\Gamma = 10$ m²/s, $a = 1$ m: under the vortex $\Delta = 10/(5\pi) = 0.637$, so $C_p(0,0) = 1.273-0.405 = 0.868$. The clockwise vortex opposes the freestream at the wall, slowing it and raising the pressure.

See [[Method of Images]]. Applications: ground effect of a starting vortex (Tutorial 3 Q2), rotorcraft near walls, fans near walls (2022-23 exam), vortex in a corner (2020-21 exam, which needs three images).

---

## Transcript slips (Lectures 3–16)

> [!warning] Slips in `SESA2022 Lecture 3.txt` to `Lecture 16.txt` (Whisper transcripts)
> Recurring transcriptions: *"string function"* = stream function, *"Lego bricks"* = elementary flows (deliberate), *"Jakowsky"* = Joukowski, *"D.I. Lambert"*/*"D. Allen-Burtz"*/*"d allenberg"* = D'Alembert, *"XFLRFI"* = XFLR5, *"F-solve"* = `fsolve`, *"Xn"* = $x_{end}$.
>
> | Line | Said | Correct |
> |---|---|---|
> | L3, ll. 718–722 | positive vorticity *"is always counterclockwise"* | true in the $x$–$y$ plane; in the course's $x$–$z$ plane (L11 onwards) positive is clockwise ([[#1. Coordinates and conventions (important for signs)]]) |
> | L12, l. 526 | *"string function minus kappa over 2 pi times sine theta over r"* | stream function $\psi = -\frac{\kappa}{2\pi}\frac{\sin\theta}{r}$ |
> | L15, l. 657 | the stagnation points meet at the bottom *"when gamma is equal to 4 pi v infinity r"* | correct; at L15, l. 651 *"gamma less than"* should read less than or equal to for points on the surface |
> | L16, ll. 20–24 | with negative $\Gamma$ the stagnation points move to *"the first and the second quarter or the first and the fourth quarters"* | first and second quadrants (upper half); lift then points down |
> | L16, l. 112 | *"minus v infinity sine 1 plus r square over r square"* | $-V_\infty\sin\theta\,(1+R^2/r^2)$ ("theta" and the capital $R$ lost) |
> | L4, l. 227 | $x$-momentum *"u du dx plus v dv dy = minus 1 over rho dp dx"* | $u\,\partial u/\partial x+v\,\partial u/\partial y = -\frac1\rho\partial p/\partial x$: the second term carries $\partial u/\partial y$ |
> | L4, l. 386 | *"the radius is basically inversely proportional to the pressure"* | the normal pressure gradient is inversely proportional to the radius of curvature, $\partial p/\partial n = \rho V^2/R$ |
> | L4, ll. 642–645 | *"a scalar function psi"*; *"if you take the curl of a scalar function it ends up being zero"* | $\phi$; the curl of the gradient of a scalar is zero |
> | L11, l. 160 | the stream function was covered in *"lecture 6, I believe"* | Lecture 4 (3 Oct) |
> | L11, l. 232 | *"the velocity potential is only for a rotational flows"* | only for irrotational flows |
> | L12, ll. 745–747 | *"the circulation is zero if the flow is rotational over the surface bounded by C"* | zero if the flow is irrotational everywhere inside $C$ ([[#Vortex and circulation]]) |
> | L13, ll. 192–193 | the leading edge of a streamlined body *"can be represented as a source plus sink"* | uniform flow plus a source (the half-body); a sink is added for a closed oval |
> | L14, ll. 776–847 | low-$Re$ attached flow is a reason potential flow works | creeping flow is viscosity-dominated with large drag; potential flow works at high $Re$ ([[#7. Example 2: flow past a circular cylinder (uniform flow + doublet)]]) |
> | L15, l. 234 | *"Rankine lived in the 17th or 18th century"* | W. J. M. Rankine, 1820–1872 |
> | L16, ll. 237–252 | $p_\infty$ is *"very very very very small in comparison to the actual pressure"* | it is not small; a uniform pressure simply integrates to zero force round a closed body ([[#Forces from the pressure]]) |
> | L16, l. 321 | *"in an incompressible, inviscid flow, drag is always zero"* | true for steady 2D flow; finite wings have induced drag ([[#10. D'Alembert's paradox and the Kutta–Joukowski theorem]]) |
> | L16, ll. 309–311 | viscosity not found *"for another 75 years at least"* after D'Alembert | roughly right: Navier (1822) and Stokes (1845) came 70–90 years after 1752 |

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| LEGO bricks | elementary flows, singularities, fundamental solutions | L13, ll. 7, 172; L16, l. 3 | |
| source/sink strength $\Lambda$ | $Q$, $m$, volume flow per unit depth | L12, ll. 227–241, 284 | 2024-25 exam writes $Q$ |
| doublet strength $\kappa$ | dipole, $\mu$ | L12, ll. 462–526 | |
| circulation $\Gamma$, positive clockwise | vortex strength | L12, ll. 743–772; L13, ll. 16–27 | Many textbooks take anticlockwise positive |
| stream function $\psi$ | streamfunction, Lagrange stream function | throughout | |
| uniform flow + source | Rankine half-body, Rankine nose | L13, ll. 178–440 | |
| uniform flow + source + sink | Rankine oval, Rankine body | L15 | |
| lifting flow over a cylinder | spinning cylinder, Magnus flow | L15–L16 | |
| method of images | mirror-image method | L16, ll. 485–534 | |
| D'Alembert's paradox | | L16, ll. 290–320 | |

## Links

- Parent: [[SESA2022 Aerodynamics Hub]] · Previous: [[SESA2022 T2 - Boundary Layers]] · Next: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Concepts: [[Streamfunction and Velocity Potential]] · [[Elementary Potential Flows]] · [[Flow Past a Cylinder]] · [[Rankine Oval]] · [[Kutta-Joukowski Theorem]] · [[D'Alembert's Paradox]] · [[Method of Images]]
- Tutorial: [[SESA2022 Tutorial 3 - Potential Flow Solutions]] · Formulae: [[SESA2022 Formula Sheet]]
- Maths: vector calculus and Laplace's equation (MATH2048)
- Feeds into (Year 3):
  - [[SESA3043 1.2b - Potential-Flow Review]] and [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]: the same bricks written as complex potentials $W = \phi+i\psi$.
  - [[SESA3043 2.3 - Panel Methods]]: sources and vortices distributed over panels, solved numerically, the generalisation of building a body from bricks.

## Sources

- `02 - Sources/PF/Topic 3 Potential Flow.pdf` (slides 1–65) and notebook `Topic_3_Potential_Flow.ipynb`.
- 2025-26 transcripts in `02 - Sources/Lectures/`: L3, L4 = `SESA2022 Lecture 3.txt`, `Lecture 4.txt` (maths revision, Euler equations, irrotational flow); L11–L16 = `SESA2022 Lecture 11.txt` to `Lecture 16.txt` (16–24 Oct 2025). Line numbers in this note refer to these files.
- All eight 2025-26 transcripts above (L3, L4, L11–L16) were read in full (second pass, 28 Oct 2026); every set task, exam remark and slip found is cited in this note.
- Revision lecture 1 (`SESA2022 Lecture 1 - Revision.txt`, Part A, Jan 2026), read in full and cited as "Revision 1": it works through [[SESA2022 Exam 2024-25 Solutions|2024-25]] Q2.
- Earlier-year recording `02 - Sources/PF/PFs.txt` (same slides).
- Anderson, *Fundamentals of Aerodynamics*, Ch. 3.10–3.16.
- Figures: `generate_aero_t3_figures.py` (`pf_sign_convention`, `pf_lego_bricks`, `pf_vortex_wall_image`); older figures (`pf_rankine_oval`, `pf_lifting_cylinder`, `pf_cylinder_cp`) predate the script. Worked-example numbers recomputed in Python (NumPy, SciPy `quad`, `brentq`).

## Self-study tasks

No tutorial sessions are run; do the tutorial sheet yourself and check against the written solutions (L1, ll. 441–452). The potential-flow computing lab (5%) is two hours, open book, individual: an analytical part of 30–35 minutes (treat it as exam practice) and a numerical part; upload the GenAI form or get no mark (L1, ll. 453–470; L15, ll. 4–35, 505–524). Attempt each task closed-book first.

### Core

- [ ] Show $\nabla^2\phi = 0$ and $\nabla^2\psi = 0$ from continuity and irrotationality (lectured, L4, ll. 640–726). → [[#Why both satisfy Laplace's equation]]
- [ ] Half-body: stagnation point, body streamline, downstream width (lectured, L13). → [[#6. Example 1: uniform flow + source (Rankine half-body)]]
- [ ] Cylinder $C_p = 1-4\sin^2\theta$ and the zero-drag integral (lectured, L14). → [[#7. Example 2: flow past a circular cylinder (uniform flow + doublet)]]
- [ ] Rankine oval: stagnation points, $z_{top}$ equation and the slender approximation — *"approximate it as a long and a slender body"* will be stated in an exam (L15, ll. 331–336). → [[#8. Example 3: Rankine oval (uniform flow + source at −b + sink at +b)]]
- [ ] Off-cylinder stagnation point for $\Gamma>4\pi V_\infty R$ — *"simple rearranging, squaring… I'm pretty sure you can work this out"* (L16, ll. 133–138). → [[#Stagnation points (L16, ll. 84–140)]]
- [ ] Lift and drag integrals for the lifting cylinder, giving $L' = \rho V_\infty\Gamma$. → [[#Forces from the pressure]]
- [ ] Tutorial 3, all questions. → [[SESA2022 Tutorial 3 - Potential Flow Solutions]]
- [ ] Laplace for $\psi$ from irrotationality — *"I'm going to leave that part to you"* (L4, ll. 725–728). → [[#Why both satisfy Laplace's equation]]
- [ ] Which streamline is the body? Given a streamline plot, identify the solid surface — a likely quiz and exam question (L4, ll. 44–48). → [[#5. How to build a flow]]
- [ ] Show a given velocity field is incompressible ($\nabla\cdot\mathbf V = 0$) and irrotational (L3, ll. 459–473). → [[#2. Governing equations]]

### Further practice

- [ ] *(Optional)* The doublet limit $\psi = -\frac{\kappa}{2\pi}\frac{\sin\theta}{r}$ — *"go over this yourself… I don't need you to derive this"* (L12, ll. 520–528). → [[#Doublet: the limit of a source–sink pair]]
- [ ] Image signs: draw velocity arrows for a source and a vortex near a wall — *"you can work it out"* (L16, ll. 540–543). → [[#11. Method of images]]
- [ ] Run the lecture notebook and vary grid resolution until $C_p$ converges — *"As always, check your grid resolution"* (L16, l. 630). → [[#5. How to build a flow]]
- [ ] Past papers: sand dune (previous year, L15, ll. 470–475), [[SESA2022 Exam 2024-25 Solutions]] Q2 (slope), and the image problems listed in [[SESA2022 Past Paper Map]].
- [ ] *(Suggested, not lecturer-set)* For the wall example ($U_\infty = 5$ m/s, $\Gamma = 10$ m²/s, $a = 1$ m), find $u$ and $C_p$ on the wall at $x = a$. Target: $u = 3.41$ m/s, $C_p = 0.535$. → [[#Vortex near a wall (lecture Example 5: multirotor near a wall)]]
