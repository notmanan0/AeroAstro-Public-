---
title: "SESA3043 Mock Questions - Chapters 1-3"
module: "SESA3043 Advanced Aeronautics"
type: tutorial
stream: "Chapters 1–3: Conservation Laws, Potential-Flow Methods, Boundary Layers"
tags: [sesa3043, tutorial-solutions, mock-questions, exam-prep, conservation-laws, potential-flow, conformal-mapping, lumped-vortex, panel-method, boundary-layer, blasius, falkner-skan]
sheet: "Self-written mock questions (not lecturer-set)"
theory_notes: ["[[SESA3043 1.1 - Mathematical Tools and Flow Description]]", "[[SESA3043 1.2 - Conservation Laws and Governing Equations]]", "[[SESA3043 1.2b - Potential-Flow Review]]", "[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]", "[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]", "[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]", "[[SESA3043 2.2 - Lumped Vortex Method]]", "[[SESA3043 2.3 - Panel Methods]]", "[[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]", "[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]"]
status: complete
sources: ["01 - Notes/Topics", "03 - Exams & Past Papers/Ch1_Revision_Questions.pdf", "03 - Exams & Past Papers/Ch2_Revision_Questions.pdf", "03 - Exams & Past Papers/Ch3_Revision_Questions.pdf"]
---

# SESA3043 Mock Questions - Chapters 1-3

> [!warning] Self-written mock questions, not lecturer-set; written from lectured content up to 23 Oct 2026.
> These eight questions were written for revision. No past paper or specimen paper has been released, so neither the format nor the mark scheme is the lecturers'. They avoid repeating the Blackboard revision questions, whose solutions are in [[SESA3043 Ch1 Revision Questions - Worked Solutions|Ch1]], [[SESA3043 Ch2 Revision Questions - Worked Solutions|Ch2]] and [[SESA3043 Ch3 Revision Questions - Worked Solutions|Ch3]].

> [!info] How to use this sheet
> - **Timing.** Each question carries 20 marks. The target time assumes **≈1.5 min per mark**, i.e. 30 min per question, or four questions in a two-hour paper. The real paper is a two-hour, closed-book exam worth 80 % of the module (Week 1 lecture; see the [[SESA3043 Advanced Aeronautics Hub|hub]]). Its number of questions has not been announced.
> - **Attempt first.** Cover the solution, do the question closed-book against the clock, then mark yourself against the bracketed marks.
> - **Numbers.** Every number in the solutions was computed in Python (the `[!check]` callouts). The Blasius and Falkner–Skan constants given as data were recomputed by shooting.
> - **Each solution links** to the topic-note section where the method is derived.

> [!abstract] Scope: what is in and what is left out
> **In:** everything lectured up to Fri 23 Oct. That is all of Chapter 1 (1.1–1.4) and Chapter 2 (2.1–2.3), plus CH3-1 (3.1) and CH3-2 up to slide 99 (3.2).
>
> **Left out:** CH3-2 slides 100–106 (the cylinder stagnation-point problem) and CH3-3 to CH3-6: Pohlhausen, transition and the $e^n$ method, the full momentum integral equation, and SDM/STM viscous–inviscid interaction. These are only written ahead from the slides, and lectures resume after reading week. The momentum-integral, transition and viscous–inviscid topics appear here only in the parts already lectured:
> - $\mathrm d\theta/\mathrm dx=C_f/2$ for a flat plate (Q8);
> - laminar against turbulent profiles (Q8);
> - $\delta^*$ and the effective body (Q7).

| Q | Topic | Chapter | Marks | Target time |
|---|---|---|---:|---:|
| 1 | Reynolds transport theorem and Navier–Stokes terms in a channel | 1.1–1.2 | 20 | 30 min |
| 2 | A 120° wedge flow that is being spun up | 1.3 | 20 | 30 min |
| 3 | Boundary-layer scaling on a water-tunnel hydrofoil | 1.4 | 20 | 30 min |
| 4 | Ellipse and flat plate by the Joukowski map | 2.1 | 20 | 30 min |
| 5 | A plain flap by the lumped vortex method | 2.2 | 20 | 30 min |
| 6 | Panel-method logic and a four-panel cylinder | 2.3 | 20 | 30 min |
| 7 | Blasius plate, displacement effect and an adverse-gradient wedge flow | 3.1–3.2 | 20 | 30 min |
| 8 | Integral estimate with a sine profile; laminar against turbulent | 3.1 | 20 | 30 min |

---

## Q1. Conservation laws and a viscous channel flow

**[20 marks; target 30 min]**

(a) State the Reynolds transport theorem (the textbook name; the lectures apply the same balance to a fixed CV without naming it) for a fixed control volume and explain the physical meaning of each term. Use it, with the divergence theorem, to derive the differential continuity equation, and show where the incompressibility assumption enters. **[6]**

(b) Water ($\rho=1000$ kg/m³, $\mu=1.0\times10^{-3}$ Pa s) flows steadily between two horizontal parallel plates at $y=0$ and $y=h=2$ mm. The velocity field is

$$
u=\frac{G}{2\mu}\,y\,(h-y),\qquad v=0,\qquad G=-\frac{\mathrm dp}{\mathrm dx}=\text{constant}.
$$

- (i) Show that the field satisfies continuity. **[1]**
- (ii) Write the two-dimensional incompressible Navier–Stokes equations. Give the physical meaning of every term and say which terms vanish here, and why. **[5]**
- (iii) Show that the $x$-momentum equation reduces to $\mathrm dp/\mathrm dx=\mu\,\mathrm d^2u/\mathrm dy^2$ and that the profile satisfies it. **[1]**

(c) The centreline speed is $0.15$ m/s. Find $G$, the wall shear stress $\tau_w$, the mean velocity and the Reynolds number $\rho\bar uh/\mu$. **[4]**

(d) Apply the momentum form of the Reynolds transport theorem to a control volume of length $L=0.5$ m that spans the gap. Show that the momentum fluxes cancel, and that the pressure force balances the wall shear. Check this against (c). **[3]**

### Solution

**(a) Reynolds transport theorem** ([[SESA3043 1.1 - Mathematical Tools and Flow Description#8. Reynolds transport theorem|1.1 §8]]). For an extensive property $B$ with specific value $b=B/m$,

$$
\frac{\mathrm dB_{sys}}{\mathrm dt}=\frac{\partial}{\partial t}\int_{CV}\rho b\,\mathrm dV+\oint_{CS}\rho b\,(\mathbf u\cdot\mathbf n)\,\mathrm dA.
$$

- Left: the rate of change of $B$ for the material system that occupies the CV at that instant (Lagrangian).
- First term on the right: accumulation of $B$ inside the fixed CV (Eulerian, local).
- Second term: net **outward** flow rate of $B$ across the control surface ($\mathbf n$ is the outward normal).

**Mass** ([[SESA3043 1.2 - Conservation Laws and Governing Equations#2. Conservation of mass|1.2 §2]]): put $b=1$. A system's mass is fixed, so

$$
0=\frac{\partial}{\partial t}\int_{CV}\rho\,\mathrm dV+\oint_{CS}\rho\,\mathbf u\cdot\mathbf n\,\mathrm dA.
$$

The CV is fixed, so the time derivative goes inside the integral:

$$
0=\int_{CV}\frac{\partial\rho}{\partial t}\,\mathrm dV+\oint_{CS}\rho\,\mathbf u\cdot\mathbf n\,\mathrm dA.
$$

Divergence theorem on the surface integral:

$$
\oint_{CS}\rho\,\mathbf u\cdot\mathbf n\,\mathrm dA=\int_{CV}\nabla\cdot(\rho\mathbf u)\,\mathrm dV.
$$

Combine:

$$
\int_{CV}\left[\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)\right]\mathrm dV=0.
$$

This holds for **every** CV, so the integrand itself vanishes:

$$
\boxed{\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf u)=0.}
$$

Expand the divergence with the product rule:

$$
\frac{\partial\rho}{\partial t}+\mathbf u\cdot\nabla\rho+\rho\,\nabla\cdot\mathbf u=0.
$$

Group the first two terms into the material derivative:

$$
\frac{\mathrm D\rho}{\mathrm Dt}+\rho\,\nabla\cdot\mathbf u=0.
$$

**Incompressible** ($\mathrm D\rho/\mathrm Dt=0$, the density of each particle is fixed), so $\nabla\cdot\mathbf u=0$.

**(b)(i)** $u$ depends on $y$ only and $v=0$:

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0+0=0\ \checkmark
$$

**(b)(ii)** The 2-D incompressible Navier–Stokes equations ([[SESA3043 1.2 - Conservation Laws and Governing Equations#Explicit two-dimensional incompressible equations|1.2 §7]]):

$$
\underbrace{\frac{\partial u}{\partial t}}_{①}+\underbrace{u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}}_{②}=\underbrace{f_x}_{③}\underbrace{-\frac1\rho\frac{\partial p}{\partial x}}_{④}+\underbrace{\nu\left(\frac{\partial^2u}{\partial x^2}+\frac{\partial^2u}{\partial y^2}\right)}_{⑤},
$$

$$
\frac{\partial v}{\partial t}+u\frac{\partial v}{\partial x}+v\frac{\partial v}{\partial y}=f_y-\frac1\rho\frac{\partial p}{\partial y}+\nu\left(\frac{\partial^2v}{\partial x^2}+\frac{\partial^2v}{\partial y^2}\right).
$$

| Term | Meaning (per unit mass) | Here |
|---|---|---|
| ① $\partial u/\partial t$ | local (unsteady) acceleration at a fixed point | 0: steady |
| ② $u\,\partial u/\partial x$ | convective acceleration from moving along $x$ | 0: $u$ does not change with $x$ (fully developed) |
| ② $v\,\partial u/\partial y$ | convective acceleration from moving across the flow | 0: $v=0$ |
| ③ $f_x$ | body force | 0: gravity acts in $-y$ |
| ④ $-\frac1\rho\,\partial p/\partial x$ | net pressure force | $G/\rho$, the driving force |
| ⑤ $\nu\,\partial^2u/\partial x^2$ | viscous diffusion of $x$-momentum along $x$ | 0: no $x$-dependence |
| ⑤ $\nu\,\partial^2u/\partial y^2$ | viscous diffusion of $x$-momentum across the flow | non-zero, the resisting force |

In the $y$-equation every velocity term contains $v$, so it is zero. What is left is $0=-g-\frac1\rho\,\partial p/\partial y$, which is hydrostatic. Because the convective (nonlinear) terms vanish identically, this is one of the few **exact** solutions of the Navier–Stokes equations.

**(b)(iii)** What survives of $x$-momentum is

$$
0=-\frac1\rho\frac{\mathrm dp}{\mathrm dx}+\nu\frac{\mathrm d^2u}{\mathrm dy^2}.
$$

Multiply by $\rho$ ($\mu=\rho\nu$):

$$
\frac{\mathrm dp}{\mathrm dx}=\mu\frac{\mathrm d^2u}{\mathrm dy^2}.
$$

Differentiate the profile once:

$$
\frac{\mathrm du}{\mathrm dy}=\frac{G}{2\mu}(h-2y).
$$

And again:

$$
\frac{\mathrm d^2u}{\mathrm dy^2}=-\frac{G}{\mu}.
$$

So $\mu\,\mathrm d^2u/\mathrm dy^2=-G=\mathrm dp/\mathrm dx$ ✓.

**(c)** The maximum is at $y=h/2$:

$$
u_{max}=\frac{G}{2\mu}\cdot\frac h2\cdot\frac h2=\frac{Gh^2}{8\mu}.
$$

Solve for $G$:

$$
G=\frac{8\mu u_{max}}{h^2}=\frac{8(1.0\times10^{-3})(0.15)}{(2\times10^{-3})^2}=\boxed{300\ \text{Pa/m}.}
$$

Wall shear, from the first derivative at $y=0$:

$$
\tau_w=\mu\frac{\mathrm du}{\mathrm dy}\Big|_0=\mu\cdot\frac{G}{2\mu}h=\frac{Gh}{2}=\frac{300\times0.002}{2}=\boxed{0.30\ \text{Pa}.}
$$

Mean velocity:

$$
\bar u=\frac1h\int_0^h\frac{G}{2\mu}(hy-y^2)\,\mathrm dy=\frac{G}{2\mu h}\left[\frac{hy^2}{2}-\frac{y^3}{3}\right]_0^h=\frac{G}{2\mu h}\cdot\frac{h^3}{6}=\frac{Gh^2}{12\mu}.
$$

$$
\bar u=\frac23u_{max}=\boxed{0.100\ \text{m/s}},\qquad Re=\frac{\rho\bar uh}{\mu}=\frac{1000(0.1)(0.002)}{1.0\times10^{-3}}=\boxed{200.}
$$

This is low, consistent with a steady laminar solution.

**(d)** Steady flow, $b=\mathbf u$, $x$-component:

$$
\sum F_x=\oint_{CS}\rho u\,(\mathbf u\cdot\mathbf n)\,\mathrm dA=\int_0^h\rho u^2\,\mathrm dy\Big|_{out}-\int_0^h\rho u^2\,\mathrm dy\Big|_{in}.
$$

The profile is the same at inlet and outlet, so the two fluxes cancel and $\sum F_x=0$. The forces per unit span are the pressure difference on the end faces and the shear on both walls, which acts against the flow:

$$
(p_1-p_2)\,h-2\tau_wL=0.
$$

$p_1-p_2=GL$, so

$$
GLh=2\tau_wL\quad\Longrightarrow\quad\tau_w=\frac{Gh}{2}\ \checkmark
$$

> [!check] Python
> $G=300.0$ Pa/m, $\tau_w=0.300$ Pa, $\bar u=0.1000$ m/s, $Re=200.0$. Over $L=0.5$ m: $\Delta p=150.0$ Pa, pressure force $GLh=0.300$ N/m, wall force $2\tau_wL=0.300$ N/m ✓.

> [!tip] What the question is really testing
> The same five-term table appears in every Navier–Stokes question. Here the viscous term survives and the convective term dies; in [[#Q2. A 120° wedge flow that is being spun up|Q2]] it is the other way round. Saying **why** each term vanishes (steady, fully developed, $v=0$) is where the marks are ([[SESA3043 1.2 - Conservation Laws and Governing Equations#8. Model hierarchy by assumptions|1.2 §8]]: *"every simplification needs an explicit physical justification"*).

---

## Q2. A 120° wedge flow that is being spun up

**[20 marks; target 30 min]**

The complex potential

$$
\Phi=-k\,z^{3/2}\qquad(k>0)
$$

describes potential flow of air ($\rho=1.225$ kg/m³) towards the apex of a wedge.

(a) Find $\phi$ and $\psi$. Use $\psi=0$ to find the walls, and show that the included wedge angle is $120^\circ$. What is $\beta$ in $\beta\pi$? **[5]**

(b) Show that the speed along a wall, at distance $s$ from the apex, is $U_e=\tfrac32ks^{1/2}$. If $U_e=12$ m/s at $s=0.25$ m, find $k$ and the wall pressure gradient there. Is it favourable or adverse? **[4]**

(c) Starting from the incompressible Navier–Stokes equations without body force, derive the unsteady Bernoulli equation for potential flow. State each assumption where it is used. **[6]**

(d) The flow is being started: at the instant when $k=16$ m$^{1/2}$/s, $\mathrm dk/\mathrm dt=40$ m$^{1/2}$/s². Find $p_{apex}-p(s{=}0.25\ \text{m})$ and $p(0.05\ \text{m})-p(0.25\ \text{m})$ along the wall at that instant, and the percentage the unsteady term adds to each. **[5]**

### Solution

**(a)** With $z=re^{i\theta}$, $z^{3/2}=r^{3/2}e^{i3\theta/2}$ ([[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#7. A mystery flow: wedges and corners|1.3 §7]], here $m=\tfrac12$):

$$
\Phi=-kr^{3/2}\left[\cos\tfrac{3\theta}{2}+i\sin\tfrac{3\theta}{2}\right].
$$

$$
\phi=-kr^{3/2}\cos\tfrac{3\theta}{2},\qquad\psi=-kr^{3/2}\sin\tfrac{3\theta}{2}.
$$

$\psi=0$ for $r>0$ when $\sin(3\theta/2)=0$:

$$
\frac{3\theta}{2}=0,\ \pm\pi\quad\Longrightarrow\quad\theta=0,\ \pm\frac{2\pi}{3}.
$$

$\theta=0$ is the dividing streamline into the apex; the walls are at $\theta=\pm120^\circ$. The fluid fills the $240^\circ$ between them (through $\theta=0$), so the body occupies

$$
360^\circ-240^\circ=\boxed{120^\circ}=\beta\pi\quad\Longrightarrow\quad\beta=\frac23.
$$

Check with $\beta=2m/(m+1)=1/(3/2)=2/3$ ✓.

**(b)** Velocity:

$$
\frac{\mathrm d\Phi}{\mathrm dz}=-\frac32kz^{1/2}=-\frac32kr^{1/2}e^{i\theta/2}=u-iv.
$$

The speed is the modulus. On a wall $r=s$:

$$
\boxed{U_e=\frac32ks^{1/2}.}
$$

With $U_e=12$ m/s at $s=0.25$ m:

$$
k=\frac{12}{1.5\times0.5}=\boxed{16\ \text{m}^{1/2}/\text{s}.}
$$

Gradient:

$$
\frac{\mathrm dU_e}{\mathrm ds}=\frac34ks^{-1/2}=\frac{U_e}{2s}=\frac{12}{0.5}=24\ \text{s}^{-1}.
$$

Steady Bernoulli along the wall ([[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Step 4: Bernoulli at the edge (slides 33–37; revision §1.4 Q4)|1.4, Step 4]]):

$$
\frac{\mathrm dp}{\mathrm ds}=-\rho U_e\frac{\mathrm dU_e}{\mathrm ds}=-1.225\times12\times24=\boxed{-352.8\ \text{Pa/m}.}
$$

Negative: pressure falls along the wall, a **favourable** gradient. (In fact $U_e\,\mathrm dU_e/\mathrm ds=\tfrac98k^2$ is the same at every $s$ for $m=\tfrac12$.)

**(c) Unsteady Bernoulli** ([[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#Vector-form derivation, one step per line|1.3 §8]]). Start from

$$
\frac{\partial\mathbf u}{\partial t}+(\mathbf u\cdot\nabla)\mathbf u=-\frac1\rho\nabla p+\nu\nabla^2\mathbf u.
$$

1. **Convective term.** Use the identity:

$$
(\mathbf u\cdot\nabla)\mathbf u=\nabla\left(\frac{q^2}{2}\right)+(\nabla\times\mathbf u)\times\mathbf u.
$$

   **Irrotational** ($\nabla\times\mathbf u=0$), so only $\nabla(q^2/2)$ remains.

2. **Viscous term.** Use the identity:

$$
\nabla^2\mathbf u=\nabla(\nabla\cdot\mathbf u)-\nabla\times(\nabla\times\mathbf u).
$$

   The first part is zero because the flow is **incompressible**, and the second because it is **irrotational**. So the viscous force on each element is zero, even though $\mu\neq0$.

3. **Unsteady term.** Use $\mathbf u=\nabla\phi$, with smooth $\phi$ so the derivatives commute:

$$
\frac{\partial}{\partial t}\nabla\phi=\nabla\frac{\partial\phi}{\partial t}.
$$

4. **Constant density.** This lets $\rho$ go inside the gradient: $\frac1\rho\nabla p=\nabla(p/\rho)$. Collect the terms:

$$
\nabla\left(\frac{\partial\phi}{\partial t}+\frac{q^2}{2}+\frac p\rho\right)=\mathbf 0.
$$

5. **Integrate in space.** A zero gradient means no variation in space, but the bracket may still vary in time:

$$
\boxed{\frac{\partial\phi}{\partial t}+\frac{q^2}{2}+\frac p\rho=C(t).}
$$

Because the flow is irrotational, $C(t)$ is the **same everywhere** at a given instant, not just along one streamline.

**(d)** On the upper wall $\theta=2\pi/3$, $\cos(3\theta/2)=\cos\pi=-1$:

$$
\phi_{wall}=-ks^{3/2}(-1)=ks^{3/2}.
$$

Differentiate in time at fixed $s$:

$$
\frac{\partial\phi}{\partial t}\Big|_{wall}=\dot k\,s^{3/2}.
$$

At the apex $s=0$: $\phi=0$ for all $t$, so $\partial\phi/\partial t=0$, and $q=0$ (stagnation point). Apply the boxed equation at the apex and at $s$. $C(t)$ is common to both, so it cancels:

$$
\frac{p_{apex}}{\rho}=\dot ks^{3/2}+\frac{U_e^2}{2}+\frac{p_s}{\rho}.
$$

$$
p_{apex}-p_s=\rho\left(\dot ks^{3/2}+\frac{U_e^2}{2}\right).
$$

At $s=0.25$ m, $s^{3/2}=0.125$:

$$
p_{apex}-p(0.25)=1.225\left(40\times0.125+\frac{144}{2}\right)=1.225\,(5+72)=\boxed{94.3\ \text{Pa}}\quad(\text{steady part }88.2,\ \text{unsteady }6.1\ \text{Pa},\ +6.9\%).
$$

Between the two wall points, with $U_e(0.05)=24\sqrt{0.05}=5.367$ m/s and $0.05^{3/2}=0.01118$:

$$
p(0.05)-p(0.25)=\rho\left[\dot k\left(0.25^{3/2}-0.05^{3/2}\right)+\tfrac12\left(U_e(0.25)^2-U_e(0.05)^2\right)\right].
$$

$$
=1.225\left[40(0.11382)+\tfrac12(144-28.80)\right]=1.225\,(4.553+57.60)=\boxed{76.1\ \text{Pa}}\quad(\text{steady }70.6,\ +7.9\%).
$$

> [!check] Python
> $\beta=0.6667$; walls at $120.0^\circ$; $k=16.000$; on the wall at $s=0.25$: $|\mathrm d\Phi/\mathrm dz|=12.000$ and the flow direction is $120.0^\circ$ (along the wall ✓); $\phi=2.000=ks^{3/2}$ ✓. $\mathrm dp/\mathrm ds=-352.80$ Pa/m at both $s=0.05$ and $0.25$. $p_{apex}-p(0.25)=88.200+6.125=94.325$ Pa; $p(0.05)-p(0.25)=70.560+5.577=76.137$ Pa.

> [!tip] Link forward
> The wall speed $U_e\propto s^{1/2}$ is a Falkner–Skan edge velocity with $m=\tfrac12$, $\beta=\tfrac23$: an accelerating, favourable-gradient layer, thinner and fuller than Blasius ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Special cases and the wedge angle (slide 77)|3.2]]).

> [!warning] Common slip
> Do not drop $\partial\phi/\partial t$ just because the apex is a stagnation point. It is zero **at the apex** because $\phi(0)=0$ there for every $k$, but it is not zero along the wall.

---

## Q3. Boundary-layer scaling on a water-tunnel hydrofoil

**[20 marks; target 30 min]**

A hydrofoil of chord $L=0.15$ m is tested in a water tunnel at $U_e\approx3$ m/s ($\nu=1.0\times10^{-6}$ m²/s, $\rho=1000$ kg/m³).

(a) Find the chord Reynolds number. Use order-of-magnitude scaling to estimate the boundary-layer thickness $\delta$ and the wall-normal velocity scale $v$ near the trailing edge. Compare $\delta$ with the laminar flat-plate value $\delta_{99}=4.91L/\sqrt{Re_L}$. **[3]**

(b) Estimate the size, in m/s², of every term in the $x$-momentum equation. Use the estimates to justify dropping $\nu\,\partial^2u/\partial x^2$, and show which balance sets $\delta/L\sim Re^{-1/2}$. Over the first 30 % of chord the outer flow accelerates from 3.0 to 3.6 m/s: estimate the pressure-gradient term and decide whether it can be dropped. **[7]**

(c) From the $y$-momentum equation, estimate the largest pressure difference that can exist across the layer. Compare it with the dynamic pressure, and state the consequence for the boundary-layer equations. **[5]**

(d) Near the leading edge the thin-layer assumption fails. Taking "thin" to mean $\delta/x<0.1$, estimate the distance from the leading edge inside which it fails. **[3]**

(e) The tunnel speed is doubled. By what factor do $\delta$ and the neglected-term ratio change? **[2]**

### Solution

Scales ([[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#3. Order-of-magnitude analysis, step by step|1.4 §3]]): $x\sim L$, $y\sim\delta$, $u\sim U_e$, $p\sim\rho U_e^2$.

**(a)**

$$
Re_L=\frac{U_eL}{\nu}=\frac{3\times0.15}{1.0\times10^{-6}}=\boxed{4.5\times10^5.}
$$

$$
\delta\sim LRe_L^{-1/2}=\frac{0.15}{\sqrt{4.5\times10^5}}=0.22\ \text{mm}.
$$

Continuity, $\partial u/\partial x+\partial v/\partial y=0$, needs the two terms to be the same size:

$$
\frac{v}{\delta}\sim\frac{U_e}{L}.
$$

$$
v\sim\frac{U_e\delta}{L}=\frac{3\times0.224\times10^{-3}}{0.15}=4.5\ \text{mm/s}\ll U_e.
$$

Blasius gives $\delta_{99}=4.91\times0.15/670.8=1.10$ mm. The order-of-magnitude estimate is right in its **scaling** but not its constant (a factor of about 5 here), which is all $\mathcal O(\cdot)$ claims (L5, ll. 219–222).

**(b)** With $\delta=0.224$ mm:

| Term | Estimate | Size |
|---|---|---|
| $u\,\partial u/\partial x$ | $U_e^2/L$ | 60 m/s² |
| $v\,\partial u/\partial y$ | $(U_e\delta/L)(U_e/\delta)=U_e^2/L$ | 60 m/s² |
| $\nu\,\partial^2u/\partial y^2$ | $\nu U_e/\delta^2$ | 60 m/s² |
| $\nu\,\partial^2u/\partial x^2$ | $\nu U_e/L^2$ | $1.3\times10^{-4}$ m/s² |

Ratio of the two viscous terms:

$$
\frac{\nu U_e/L^2}{\nu U_e/\delta^2}=\left(\frac{\delta}{L}\right)^2=\frac{1}{Re_L}=2.2\times10^{-6}.
$$

So $\nu\,\partial^2u/\partial x^2$ is negligible. The remaining viscous term **cannot** be dropped, or no-slip could not be met. It must therefore balance inertia ([[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Step 2: x-momentum, term by term (slides 17–24)|1.4, Step 2]]):

$$
\frac{U_e^2}{L}\sim\frac{\nu U_e}{\delta^2}.
$$

$$
\frac{\delta^2}{L^2}\sim\frac{\nu}{U_eL}.
$$

$$
\frac{\delta}{L}\sim Re_L^{-1/2}.
$$

(That is why the third row equals the first: $\delta$ was **defined** by this balance.)

**Pressure gradient.** Inside the layer $-\frac1\rho\,\mathrm dp/\mathrm dx=U_e\,\mathrm dU_e/\mathrm dx$. Take $\bar U_e\approx3.3$ m/s and

$$
\frac{\mathrm dU_e}{\mathrm dx}\approx\frac{3.6-3.0}{0.3\times0.15}=13.3\ \text{s}^{-1}.
$$

$$
U_e\frac{\mathrm dU_e}{\mathrm dx}\approx3.3\times13.3=44\ \text{m/s}^2.
$$

That is the same order as the 60 m/s² of inertia, so it **must be kept**. It is $\mathcal O(U_e^2/L)$, as the scaling $p\sim\rho U_e^2$ predicts. (Check with Bernoulli: $\tfrac12\rho(3.6^2-3.0^2)=1980$ Pa over 45 mm.)

**(c)** Every term in $y$-momentum is at most $\mathcal O(U_e^2\delta/L^2)$ ([[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Step 3: y-momentum (slides 25–31)|1.4, Step 3]]), so the pressure gradient across the layer can be no larger:

$$
\frac1\rho\frac{\partial p}{\partial y}\sim\frac{U_e^2\delta}{L^2}.
$$

Multiply by $\delta$:

$$
\Delta p_{across}\sim\rho U_e^2\left(\frac{\delta}{L}\right)^2=\frac{\rho U_e^2}{Re_L}=\frac{1000\times9}{4.5\times10^5}=\boxed{0.02\ \text{Pa},}
$$

against $\tfrac12\rho U_e^2=4500$ Pa: a ratio of $4\times10^{-6}$. So, to leading order,

$$
\frac{\partial p}{\partial y}=0,\qquad p=p_e(x).
$$

**Consequence:** the outer potential flow imposes the pressure. $p$ stops being an unknown, which leaves two equations (continuity and $x$-momentum) for $u$ and $v$. Without $\partial^2/\partial x^2$ terms they are **parabolic**, so they can be marched downstream from an inflow profile ([[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers#Why parabolic matters (revision §1.4 Q6)|1.4 §4]]).

**(d)** Apply the scaling locally, $\delta/x\sim Re_x^{-1/2}$:

$$
Re_x^{-1/2}=0.1\quad\Longrightarrow\quad Re_x=100.
$$

$$
x=\frac{100\,\nu}{U_e}=\frac{100\times10^{-6}}{3}=\boxed{33\ \mu\text{m}.}
$$

That is 0.02 % of the chord: the boundary-layer equations are valid almost everywhere on the foil.

**(e)** $\delta\propto U_e^{-1/2}$, so $\delta$ falls by $1/\sqrt2$, to $0.16$ mm. The neglected ratio $1/Re_L$ halves, to $1.1\times10^{-6}$: the approximation improves as speed rises.

> [!check] Python
> $Re_L=4.500\times10^5$; $\delta\sim0.2236$ mm; $v\sim4.472$ mm/s; inertia and viscous terms 60.00 m/s²; $\nu U_e/L^2=1.333\times10^{-4}$ m/s²; ratio $2.222\times10^{-6}$; $\Delta p_{across}\sim0.0200$ Pa; Blasius $\delta_{99}=1.098$ mm; $x(Re_x=100)=33.3\ \mu$m; doubled speed $\delta\sim0.1581$ mm.

---

## Q4. Ellipse and flat plate by the Joukowski map

**[20 marks; target 30 min]**

The map $z=\bar z+b^2/\bar z$ is applied to the flow past a circle of radius $a$ ($a\geq b$) centred at the origin of the $\bar z$-plane, in a uniform stream $U_\infty$ along the real axis:

$$
\Phi=U_\infty\left(\bar z+\frac{a^2}{\bar z}\right).
$$

(a) Show that the circle maps to an ellipse with semi-axes $A=a+b^2/a$ and $B=a-b^2/a$. An elliptical strut has $A=0.5$ m and $B=0.1$ m: find $a$ and $b$. **[4]**

(b) For $U_\infty=30$ m/s, use the chain rule to find the surface speed and $C_p$ at the top of the strut. Show that in general $q_{max}=U_\infty(1+B/A)$. Find the speed, $C_p$ and the physical position of the surface point that comes from $\theta=45^\circ$ on the circle. **[6]**

(c) Check your result in the two limits $B\to0$ and $B=A$. **[2]**

(d) Now take $a=b$ (a flat plate of chord $c=1.2$ m) at incidence $\alpha=4^\circ$ in a 30 m/s air stream ($\rho=1.225$ kg/m³). Apply the Kutta condition at the trailing edge to find the circulation, the lift per unit span and $C_L$. **[5]**

(e) Without calculation, explain how the circle must be moved to produce a symmetric aerofoil and then a cambered one, and why the trailing edge stays sharp. **[3]**

### Solution

**(a)** On the circle, $\bar z=ae^{i\theta}$ ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#Flow over a finite plate, and an ellipse (slides 13–14)|2.1 §3]]):

$$
z=ae^{i\theta}+\frac{b^2}{a}e^{-i\theta}.
$$

Expand both exponentials:

$$
z=a(\cos\theta+i\sin\theta)+\frac{b^2}{a}(\cos\theta-i\sin\theta).
$$

Collect real and imaginary parts:

$$
x=\left(a+\frac{b^2}{a}\right)\cos\theta=A\cos\theta,\qquad y=\left(a-\frac{b^2}{a}\right)\sin\theta=B\sin\theta.
$$

So $x^2/A^2+y^2/B^2=1$: an ellipse. Add and subtract the semi-axes:

$$
a=\frac{A+B}{2}=\boxed{0.30\ \text{m}},\qquad\frac{b^2}{a}=\frac{A-B}{2}=0.20\ \text{m}.
$$

$$
b^2=0.30\times0.20=0.060\ \text{m}^2,\qquad\boxed{b=0.245\ \text{m}.}
$$

**(b)** Chain rule ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#What happens to streamlines and velocities|2.1 §2]]):

$$
u-iv=\frac{\mathrm d\Phi/\mathrm d\bar z}{\mathrm dz/\mathrm d\bar z}=\frac{U_\infty\left(1-a^2/\bar z^2\right)}{1-b^2/\bar z^2}.
$$

At the top, $\theta=90^\circ$, $\bar z=ia$ and $\bar z^2=-a^2$:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=U_\infty(1+1)=2U_\infty,\qquad\frac{\mathrm dz}{\mathrm d\bar z}=1+\frac{b^2}{a^2}.
$$

$$
q_{top}=\frac{2U_\infty}{1+b^2/a^2}.
$$

Here $b^2/a^2=0.06/0.09=2/3$:

$$
q_{top}=\frac{60}{5/3}=\boxed{36.0\ \text{m/s}},\qquad C_p=1-\left(\frac{36}{30}\right)^2=\boxed{-0.44.}
$$

**General form.** Use $A+B=2a$ and $A=a(1+b^2/a^2)$:

$$
1+\frac BA=\frac{A+B}{A}=\frac{2a}{a\left(1+b^2/a^2\right)}=\frac{2}{1+b^2/a^2}.
$$

So $q_{max}=U_\infty(1+B/A)$ ✓: the classic thickness effect on peak suction.

**At $\theta=45^\circ$:** $\bar z^2=a^2e^{i\pi/2}=ia^2$, and $1/i=-i$:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=U_\infty(1+i),\qquad\left|\frac{\mathrm d\Phi}{\mathrm d\bar z}\right|=\sqrt2\,U_\infty.
$$

$$
\frac{\mathrm dz}{\mathrm d\bar z}=1+\frac23i,\qquad\left|\frac{\mathrm dz}{\mathrm d\bar z}\right|=\sqrt{1+\tfrac49}=1.2019.
$$

$$
q=\frac{\sqrt2\times30}{1.2019}=\boxed{35.3\ \text{m/s}},\qquad C_p=1-\left(\frac{35.30}{30}\right)^2=\boxed{-0.385.}
$$

The point is $z=A\cos45^\circ+iB\sin45^\circ=0.354+0.071i$ m: still at 71 % of the half-length, the speed is within 2 % of its maximum.

**(c)**
- $B\to0$ means $b=a$, so $q_{top}=2U_\infty/2=U_\infty$ and $C_p=0$: the flat plate **along** the stream, which the lecture showed has $\Phi=U_\infty z$ and $C_p=0$ (L-b, ll. 45–62) ✓.
- $B=A$ means $b=0$, so $q_{top}=2U_\infty$ and $C_p=-3$: the cylinder ✓.

**(d)** With incidence and circulation (clockwise positive), the circle-plane potential is ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#The flow and the Kutta condition (slide 17)|2.1 §4]]):

$$
\Phi=U_\infty\bar ze^{-i\alpha}+\frac{U_\infty a^2e^{i\alpha}}{\bar z}+\frac{i\Gamma}{2\pi}\ln\bar z.
$$

Differentiate:

$$
\frac{\mathrm d\Phi}{\mathrm d\bar z}=U_\infty e^{-i\alpha}-\frac{U_\infty a^2e^{i\alpha}}{\bar z^2}+\frac{i\Gamma}{2\pi\bar z}.
$$

The TE is $\bar z=b=a$, where $\mathrm dz/\mathrm d\bar z=1-b^2/a^2=0$. A finite TE speed (the Kutta condition) needs $\mathrm d\Phi/\mathrm d\bar z=0$ there:

$$
U_\infty e^{-i\alpha}-U_\infty e^{i\alpha}+\frac{i\Gamma}{2\pi a}=0.
$$

Use $e^{-i\alpha}-e^{i\alpha}=-2i\sin\alpha$:

$$
-2iU_\infty\sin\alpha+\frac{i\Gamma}{2\pi a}=0.
$$

$$
\boxed{\Gamma=4\pi aU_\infty\sin\alpha.}
$$

Chord $c=4a$, so $a=0.30$ m:

$$
\Gamma=4\pi(0.30)(30)\sin4^\circ=7.889\ \text{m}^2/\text{s}.
$$

$$
L'=\rho U_\infty\Gamma=1.225\times30\times7.889=\boxed{290\ \text{N/m}}.
$$

$$
C_L=\frac{2\Gamma}{U_\infty c}=\frac{8\pi a\sin\alpha}{4a}=2\pi\sin\alpha=\boxed{0.438.}
$$

**(e)** The Joukowski map has critical points at $\bar z=\pm b$, where $\mathrm dz/\mathrm d\bar z=0$ and angles are not preserved ([[SESA3043 2.1 - Complex Functions and Conformal Mapping#Building the shape|2.1 §4]]; the exam asks for this logic, not the calculation: L-b, ll. 486–495).
- **Symmetric aerofoil.** Shift the centre **left** to $-\varepsilon b$ and enlarge the circle so that it still passes through $\bar z=+b$ but encloses $\bar z=-b$. The point through $+b$ maps to a sharp (cusped) TE. The LE is now away from a critical point, so it is round. $\varepsilon$ sets the thickness.
- **Cambered aerofoil.** Also shift the centre **up**, by $a\sin\beta$, still through $\bar z=b$ ($a\cos\beta=b(1+\varepsilon)$). The upper and lower arcs now differ, which gives camber, and $\alpha_{L=0}=-\beta$.
- **Why sharp.** Only a circle that passes through a critical point gets a corner there. The Kutta condition then fixes $\Gamma=4\pi aU_\infty\sin(\alpha+\beta)$.

> [!check] Python
> $a=0.3$, $b=0.24495$ m; $q_{top}=36.000$ m/s, $C_p=-0.4400$; a numerical sweep of the whole surface gives $q_{max}=36.0000$ at $\theta=90.000^\circ$. At $\theta=45^\circ$: $z=0.3536+0.0707i$, $q=35.3009$ m/s, $C_p=-0.3846$. Plate: $\Gamma=7.8893$ m²/s, $L'=289.93$ N/m, $C_L=0.4383=2\pi\sin4^\circ$ ✓.

---

## Q5. A plain flap by the lumped vortex method

**[20 marks; target 30 min]**

A thin aerofoil of chord $c$ is modelled by its camber line: a straight main element of length $0.75c$ and a plain flap of length $0.25c$, deflected **down** by a small angle $\delta$. The free stream $U_\infty$ meets the main element at a small incidence $\alpha$. Use one lumped vortex per segment.

![[aa_mock_flap_lvm.png|900]]

(a) Give the positions of the two vortices and the two control points, and explain why they are placed there. **[3]**

(b) Write the flow-tangency equation at each control point, with every induced velocity written as a downwash. **[5]**

(c) Solve for $\Gamma_1$ and $\Gamma_2$, and show that $C_L=2\pi\left(\alpha+\tfrac12\delta\right)$. Check the result for $\delta=0$. **[6]**

(d) For $c=0.8$ m, $U_\infty=50$ m/s, $\alpha=3^\circ$, $\delta=10^\circ$ and $\rho=1.225$ kg/m³, find $\Gamma_1$, $\Gamma_2$, $C_L$, the lift per unit span and the zero-lift angle. **[3]**

(e) Thin-aerofoil theory gives $C_L=2\pi(\alpha+0.609\,\delta)$ for this flap. Comment on the difference and on how the model could be improved. **[3]**

### Solution

**(a)** Each segment is a flat plate with its vortex at its own **quarter**-length point and its control point at its own **three-quarter**-length point. The quarter point puts the lift at the aerodynamic centre. The three-quarter point is the spacing ($c/2$ apart) that gives the flat-plate lift slope $2\pi$ ([[SESA3043 2.2 - Lumped Vortex Method#2. The flat plate with one lumped vortex (slides 28–30)|2.2 §2]]). Segments need not be equal, as long as the distances are worked out carefully (GE, ll. 224–228). Distances are taken along the chord, since $\cos\delta\approx1$ ([[SESA3043 2.2 - Lumped Vortex Method#5. Camber with N lumped vortices (slides 34–35 and notes)|2.2 §5]]).

$$
x_{\Gamma_1}=\tfrac14(0.75c)=\tfrac{3c}{16},\qquad x_{T_1}=\tfrac34(0.75c)=\tfrac{9c}{16},
$$

$$
x_{\Gamma_2}=0.75c+\tfrac14(0.25c)=\tfrac{13c}{16},\qquad x_{T_2}=0.75c+\tfrac34(0.25c)=\tfrac{15c}{16}.
$$

**(b) Free-stream upwash** normal to each segment (small angles): $U_\infty\alpha$ on the main element. The flap slopes at $-\delta$, so the stream meets it at $\alpha+\delta$, giving $U_\infty(\alpha+\delta)$.

**Induced velocities** from a clockwise vortex: a downwash at points **downstream** of it and an upwash at points **upstream** (a negative downwash).

| At | from $\Gamma_1$ | from $\Gamma_2$ |
|---|---|---|
| $T_1$ ($9c/16$) | $\Gamma_1$ is $\tfrac{3c}{8}$ upstream: $+\dfrac{\Gamma_1}{2\pi(3c/8)}=\dfrac{4\Gamma_1}{3\pi c}$ | $\Gamma_2$ is $\tfrac c4$ **downstream**: $-\dfrac{\Gamma_2}{2\pi(c/4)}=-\dfrac{2\Gamma_2}{\pi c}$ |
| $T_2$ ($15c/16$) | $\tfrac{3c}{4}$ upstream: $+\dfrac{\Gamma_1}{2\pi(3c/4)}=\dfrac{2\Gamma_1}{3\pi c}$ | $\tfrac c8$ upstream: $+\dfrac{\Gamma_2}{2\pi(c/8)}=\dfrac{4\Gamma_2}{\pi c}$ |

Tangency (free-stream upwash = total induced downwash):

$$
T_1:\quad U_\infty\alpha=\frac{4\Gamma_1}{3\pi c}-\frac{2\Gamma_2}{\pi c},
$$

$$
T_2:\quad U_\infty(\alpha+\delta)=\frac{2\Gamma_1}{3\pi c}+\frac{4\Gamma_2}{\pi c}.
$$

**(c)** Multiply both by $\pi c$:

$$
\pi cU_\infty\alpha=\tfrac43\Gamma_1-2\Gamma_2\qquad(1)
$$

$$
\pi cU_\infty(\alpha+\delta)=\tfrac23\Gamma_1+4\Gamma_2\qquad(2)
$$

Eliminate $\Gamma_2$ with $2\times(1)+(2)$:

$$
\pi cU_\infty(3\alpha+\delta)=\tfrac{10}{3}\Gamma_1.
$$

$$
\boxed{\Gamma_1=\tfrac{3}{10}\pi cU_\infty(3\alpha+\delta).}
$$

Back into (2):

$$
4\Gamma_2=\pi cU_\infty(\alpha+\delta)-\tfrac23\cdot\tfrac{3}{10}\pi cU_\infty(3\alpha+\delta).
$$

$$
4\Gamma_2=\pi cU_\infty\left[\alpha+\delta-\tfrac35\alpha-\tfrac15\delta\right]=\pi cU_\infty\left[\tfrac25\alpha+\tfrac45\delta\right].
$$

$$
\boxed{\Gamma_2=\tfrac{1}{10}\pi cU_\infty(\alpha+2\delta).}
$$

Total:

$$
\Gamma_1+\Gamma_2=\tfrac{1}{10}\pi cU_\infty\left[9\alpha+3\delta+\alpha+2\delta\right]=\pi cU_\infty\left(\alpha+\tfrac12\delta\right).
$$

Kutta–Joukowski, $L'=\rho U_\infty(\Gamma_1+\Gamma_2)$:

$$
C_L=\frac{2(\Gamma_1+\Gamma_2)}{U_\infty c}=\boxed{2\pi\left(\alpha+\tfrac12\delta\right).}
$$

**Check $\delta=0$:** $\Gamma_1=0.9\,\pi cU_\infty\alpha$ and $\Gamma_2=0.1\,\pi cU_\infty\alpha$. They sum to $\Gamma_\infty=\pi cU_\infty\alpha$ and $C_L=2\pi\alpha$: a flat plate cut into two lumped segments still gives the exact flat-plate lift ✓.

**(d)** With $\alpha=0.05236$ rad and $\delta=0.17453$ rad (radians for the small-angle forms):

$$
\Gamma_1=0.3\pi(0.8)(50)(3\times0.05236+0.17453)=0.3\pi(40)(0.33161)=\boxed{12.50\ \text{m}^2/\text{s}},
$$

$$
\Gamma_2=0.1\pi(40)(0.05236+2\times0.17453)=0.1\pi(40)(0.40143)=\boxed{5.04\ \text{m}^2/\text{s}},
$$

$$
C_L=2\pi(0.05236+0.08727)=\boxed{0.877},\qquad L'=1.225(50)(17.55)=\boxed{1075\ \text{N/m}}.
$$

Zero lift when $\alpha=-\delta/2=\boxed{-5^\circ}$. The flap carries 29 % of the circulation on 25 % of the chord.

**(e)** Thin-aerofoil theory gives $C_L=2\pi(0.05236+0.609\times0.17453)=0.997$. The two-vortex model is 12 % low in $C_L$, and its flap effectiveness, 0.50, is 18 % below 0.609.
- **Why.** For the parabolic camber line in the lectures, the lumped-vortex lift is exact at any $N$ (2.2 §5). A flap is a camber line with a **kink** at the hinge, and the true loading has a sharp peak there. One vortex per segment cannot represent it.
- **Improve.** Use more, shorter segments, concentrated near the hinge, as the lecture suggests where the camber curves most (GE, ll. 224–228). With 3, 6, 12 and 96 main segments and 1, 2, 4 and 32 flap segments, the flap effectiveness is 0.547, 0.576, 0.592 and 0.607, converging to 0.609.
- **Limits.** The model cannot capture thickness (it is a camber-line method) or viscous flap stall, which in reality lowers the effectiveness at large $\delta$.

> [!check] Python (sympy and numpy)
> Solving the two tangency equations symbolically gives $\Gamma_1=\tfrac{3\pi}{10}U c(3\alpha+\delta)$, $\Gamma_2=\tfrac{\pi}{10}Uc(\alpha+2\delta)$ and $C_L=2\pi\alpha+\pi\delta$. Numbers: $\Gamma_1=12.5015$, $\Gamma_2=5.0445$ m²/s, $C_L=0.8773$, $L'=1074.7$ N/m. Thin-aerofoil $\alpha_{L=0}/\delta=-0.6090$ (also by quadrature); $C_L^{TAT}=0.9968$. $N$-vortex flap model: effectiveness 0.5469 (3+1 segments), 0.5760, 0.5921, 0.6005, 0.6068, 0.6085 (96+32 segments).

> [!warning] Exam traps the lecturer named (PM1, ll. 77–84)
> - Resolve the free stream **normal to each segment**, not to the chord.
> - Use small angles throughout ($\sin\approx\tan\approx$ angle, $\cos\approx1$). Carrying exact trigonometry leaves equations you cannot solve in the time.

---

## Q6. Panel-method logic and a four-panel cylinder

**[20 marks; target 30 min]**

(a) Explain why a panel method that uses source panels only cannot predict lift. For the source-plus-vortex method with $N$ panels, state the unknowns and the equations, give two ways of applying the Kutta condition, and explain how $C_p$ and $C_L$ are obtained. **[6]**

(b) A lumped-vortex model with many vortices becomes badly conditioned, but a panel method does not. Explain why, with reference to the self-induced velocity of a source panel. **[3]**

(c) A circular cylinder of diameter $l$, in a uniform stream $U_\infty$ along $+x$, is crudely modelled by four constant-strength source panels forming the circumscribed square (figure). By symmetry the top and bottom panels have zero strength and the back panel has $\sigma_B=-\sigma_F$. Using the source-panel results ($w=\frac{\sigma}{2\pi}(\theta_2-\theta_1)$ normal to the panel, $u=\frac{\sigma}{2\pi}\ln\frac{r_1}{r_2}$ along it, and $\pm\sigma/2$ on the panel itself):
- (i) find $\sigma_F$ from tangency at the front control point; **[4]**
- (ii) show that the top/bottom tangency conditions are satisfied with zero strength, and check that the body has no net source strength; **[2]**
- (iii) find the speed and $C_p$ at the top and front control points, and compare with the exact cylinder. **[2]**

(d) The result in (c)(iii) looks perfect. Explain why it should not be trusted, and what refining the panels would show. **[3]**

![[aa_mock_square_panels.png|900]]

### Solution

**(a)** ([[SESA3043 2.3 - Panel Methods#4. Method 1: source + vortex panels (slides 51–53; explainer pp. 8–31)|2.3 §4]])
- **No lift from sources.** A source distribution carries no circulation: the velocity goes *through* it (PM2, ll. 100–109). By Kutta–Joukowski $L'=\rho U_\infty\Gamma$, so zero circulation means zero lift. The explainer's source-panel cylinder gives the symmetric $C_p=1-4\sin^2\theta$ and no lift.
- **Unknowns.** A source strength $\sigma_j$ on each panel plus **one** vortex strength $\gamma$ shared by all panels: $N+1$.
- **Equations.** Tangency (zero total normal velocity) at the $N$ panel control points gives $N$ equations. One more is needed.
- **Kutta condition**, either discrete form (they agree only as $N\to\infty$):
  1. equal tangential **speeds** on the two TE panels. With panels numbered TE → LE → TE, the two panel tangents point in opposite directions, so in signed components $q_{t,1}=-q_{t,N}$ (state the tangent convention). By Bernoulli $p_1=p_N$ and the TE carries no load;
  2. an extra control point just behind the TE, on the bisector of the TE angle, with zero velocity normal to the bisector, so the flow leaves along it.
- **Solve** the $(N+1)\times(N+1)$ linear system once.
- **Outputs.**
  - $q_{t,i}=\sum_j q_{t,ij}+U_\infty\cos(\beta_i-\alpha)$ and $C_{p,i}=1-(q_{t,i}/U_\infty)^2$;
  - $\Gamma=\gamma\sum_jl_j$ and $C_L=2\Gamma/(U_\infty c)$ (Kutta–Joukowski, since only the vortex panels carry circulation).

The exam asks for this process and logic, not panel-by-panel arithmetic (16 Oct, ll. 376–394; see the hub).

**(b)** With many lumped vortices, each control point sits ever closer to a point vortex. The self-term $\Gamma/(2\pi d)$ grows without bound and swamps the rest of the matrix (PM1, ll. 98–109). A panel spreads the same loading over a finite length. As a point on a source panel is approached, the subtended angle $\theta_2-\theta_1\to\pm\pi$ and $r_1=r_2$, so the self-induced velocity is

$$
u_\pm=0,\qquad w_\pm=\pm\frac{\sigma}{2\pi}\pi=\pm\frac\sigma2:
$$

finite, a clean half-strength outflow on each side ([[SESA3043 2.3 - Panel Methods#Self-induced values (slide 48)|2.3 §2]]). The diagonal is $\tfrac12$, the matrix is diagonally dominant and well conditioned, with no singularity.

**(c)(i)** Front control point $F=(-l/2,0)$, outward normal $-x$. Contributions to the **outward normal** velocity:
- free stream: $U_\infty\cdot(-1)=-U_\infty$ (into the body);
- the front panel itself: $+\sigma_F/2$ (outflow);
- top and bottom panels: zero strength;
- back panel, at distance $l$: it subtends

$$
\theta_2-\theta_1=2\tan^{-1}\frac{l/2}{l}=2\tan^{-1}\tfrac12=0.9273\ \text{rad}\ (53.1^\circ).
$$

  Its normal velocity is $\frac{\sigma_B}{2\pi}(0.9273)$, directed away from the back panel, i.e. along $-x$, which is outward at $F$.

Tangency:

$$
\frac{\sigma_F}{2}+\frac{\sigma_B}{2\pi}(0.9273)-U_\infty=0.
$$

Put $\sigma_B=-\sigma_F$:

$$
\sigma_F\left(\frac12-\frac{0.9273}{2\pi}\right)=U_\infty.
$$

$$
\sigma_F\,(0.5-0.14758)=U_\infty\quad\Longrightarrow\quad\boxed{\sigma_F=2.838\,U_\infty,\qquad\sigma_B=-2.838\,U_\infty.}
$$

**(ii)** At the top control point $T=(0,l/2)$ the free stream is tangential. The front source's component **along** its panel (vertical at $T$) is

$$
\frac{\sigma_F}{2\pi}\ln\frac{r_{far}}{r_{near}}=\frac{\sigma_F}{2\pi}\ln\frac{\sqrt5\,l/2}{l/2}=\frac{\sigma_F}{2\pi}(0.8047),
$$

upwards. The back sink gives the same magnitude downwards, so the normal velocity at $T$ vanishes with $\sigma_T=0$ ✓ (the same for the bottom panel). Net source strength $\sum\sigma_jl_j=\sigma_Fl+\sigma_Bl=0$ ✓: a closed body cannot have net outflow.

**(iii)** Horizontal velocity at $T$. The front panel subtends $\tan^{-1}2=1.1071$ rad ($63.4^\circ$) at $T$. Its velocity normal to itself is $+x$, away from it. The back sink pulls towards itself, also $+x$, with the same magnitude:

$$
u_T=U_\infty+2\cdot\frac{\sigma_F}{2\pi}(1.1071)=U_\infty+\frac{2.838\times1.1071}{\pi}U_\infty.
$$

$$
u_T=U_\infty+1.000\,U_\infty=\boxed{2.000\,U_\infty},\qquad C_p=1-2^2=\boxed{-3.00.}
$$

At $F$ the tangential (vertical) velocity is zero by symmetry, and the normal velocity is zero by tangency, so $q=0$ and $C_p=+1$. These are exactly the cylinder's values, $q=2U_\infty$ at the top and a stagnation point at the front ($C_p=1-4\sin^2\theta$).

**(d)** The match is a coincidence of this geometry, not accuracy.
- **Algebra.** Since $\tan^{-1}2=\tfrac\pi2-\tan^{-1}\tfrac12$, the extra speed is $\frac{\sigma_F}{\pi}\left(\frac\pi2-\tan^{-1}\frac12\right)=U_\infty$ **exactly**.
- **What the panels model.** Four panels represent a square, not a cylinder. The code knows only the panel corners, and tangency holds only at four points.
- **Refinement.** With more panels on the **same square** (3, 9 and 27 per side), the speed at the middle of the top face falls to 1.55, 1.45 and $1.43\,U_\infty$. It converges to the square's own potential flow, which has singular corners. To model a cylinder, put the panel nodes **on the circle** and refine; [[SESA3043 2.3 - Panel Methods#7. Validation against exact solutions|2.3 §7]] shows 32 source panels on the curve $1-4\sin^2\theta$.
- **Moral.** A plausible answer from a coarse model is not validation. Refine until the answer stops changing.

> [!check] Python (a general constant-strength source-panel solver)
> Four panels: $\sigma/U_\infty=(2.83755,\ 0,\ -2.83755,\ 0)$ for (front, top, back, bottom); $\sum\sigma_jl_j=-6\times10^{-17}$. Velocities: top $(2.000, 0)$, $C_p=-3.00000$; front $(0,0)$, $C_p=1.00000$. Angles: $2\tan^{-1}\tfrac12=0.92730$, $\tan^{-1}2=1.10715$ rad. Refined square, top-mid speed: 2.0000, 1.5490, 1.4541, 1.4267 $U_\infty$ for 1, 3, 9, 27 panels per side.

---

## Q7. Blasius plate, displacement effect and an adverse-gradient wedge flow

**[20 marks; target 30 min]**

Data, for $f'''+ff''+\beta(1-f'^2)=0$ with $\xi=\sqrt{2\nu x/((m+1)U_e)}$, $\eta=y/\xi$:

| $\beta$ | $f''(0)$ | $\eta^*=\int_0^\infty(1-f')\,\mathrm d\eta$ | $\theta^*=\int_0^\infty f'(1-f')\,\mathrm d\eta$ | $\eta_{99}$ |
|---:|---:|---:|---:|---:|
| 0 (Blasius) | 0.4696 | 1.2168 | 0.4696 | 3.47 |
| −0.18 | 0.1286 | 1.8716 | 0.5677 | — |

A smooth flat plate of length $L=0.4$ m is in a uniform stream of lab air at $U=8$ m/s ($\rho=1.2$ kg/m³, $\nu=1.5\times10^{-5}$ m²/s). The layer is laminar throughout.

(a) At the trailing edge find $Re_L$, $\xi$, $\delta_{99}$, $\delta^*$, $\theta$, $H$, $C_f$ and $\tau_w$. **[6]**

(b) Find the drag per unit span of one side of the plate in two ways: from $D=\rho U^2\theta(L)$, and by integrating $\tau_w$. Hence find $C_D$. **[4]**

(c) Show from continuity that the vertical velocity at the edge of a flat-plate layer is $v_e=U\,\mathrm d\delta^*/\mathrm dx$. Evaluate it at the trailing edge, and explain what the outer potential flow "sees". **[3]**

(d) In a diffuser, a laminar layer develops on a wall where $U_e=cx^m$ with $\beta=-0.18$. At $x=0.3$ m, $U_e=8$ m/s (same air). Find $m$ and the angle through which a single wall must turn away from the flow to give this $\beta$. Find $\delta^*$, $\theta$, $H$ and $C_f$ at that station, compare them with a Blasius layer at the same $Re_x$, and comment. **[7]**

### Solution

**(a)** ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#5. Blasius boundary-layer properties (slides 39–74; Notes §3)|3.2 §5]])

$$
Re_L=\frac{UL}{\nu}=\frac{8\times0.4}{1.5\times10^{-5}}=\boxed{2.133\times10^5},
$$

$$
\xi=\sqrt{\frac{2\nu L}{U}}=\sqrt{\frac{2(1.5\times10^{-5})(0.4)}{8}}=\sqrt{1.5\times10^{-6}}=1.2247\ \text{mm}.
$$

All thicknesses follow from $\mathrm dy=\xi\,\mathrm d\eta$:

$$
\delta_{99}=\eta_{99}\xi=3.47\times1.2247=\boxed{4.25\ \text{mm}},
$$

$$
\delta^*=\eta^*\xi=1.2168\times1.2247=\boxed{1.490\ \text{mm}},
$$

$$
\theta=\theta^*\xi=0.4696\times1.2247=\boxed{0.575\ \text{mm}},
$$

$$
H=\frac{\delta^*}{\theta}=\frac{\eta^*}{\theta^*}=\boxed{2.59}\quad(\xi\ \text{cancels: the same at every }x).
$$

Skin friction:

$$
C_f=\frac{2\nu}{U\xi}f''(0)=\frac{\sqrt2\,f''(0)}{\sqrt{Re_L}}=\frac{0.6641}{461.9}=\boxed{1.438\times10^{-3}},
$$

$$
\tau_w=C_f\cdot\tfrac12\rho U^2=1.438\times10^{-3}\times38.4=\boxed{0.0552\ \text{Pa}.}
$$

**(b)** Control volume ([[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#4. Momentum thickness θ: the control-volume derivation (slides 19–29)|3.1 §4]]):

$$
D=\rho U^2\theta(L)=1.2\times64\times0.5751\times10^{-3}=\boxed{0.0442\ \text{N/m}.}
$$

Integrating the wall shear. $\tau_w\propto x^{-1/2}$, so $\tau_w(x)=\tau_w(L)\sqrt{L/x}$:

$$
D=\int_0^L\tau_w(L)\sqrt{\frac Lx}\,\mathrm dx=\tau_w(L)\sqrt L\left[2\sqrt x\right]_0^L=2\tau_w(L)\,L.
$$

$$
D=2\times0.05521\times0.4=0.0442\ \text{N/m}\ \checkmark
$$

$$
C_D=\frac{D}{\tfrac12\rho U^2L}=\frac{0.04417}{38.4\times0.4}=\boxed{2.88\times10^{-3}}=\frac{1.328}{\sqrt{Re_L}}=2C_f(L).
$$

The two routes agree because $\theta^*=f''(0)$: on a flat plate, $\mathrm d\theta/\mathrm dx=C_f/2$ ([[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#5. Wall shear, skin friction and the drag link (slide 32)|3.1 §5]]).

**(c)** Integrate continuity up from the wall ($v=0$ at $y=0$) to a height $Y$ above the layer:

$$
v(Y)=-\int_0^Y\frac{\partial u}{\partial x}\,\mathrm dy.
$$

$U$ is constant, so $-\partial u/\partial x=\partial(U-u)/\partial x$:

$$
v(Y)=\int_0^Y\frac{\partial(U-u)}{\partial x}\,\mathrm dy.
$$

The limits do not depend on $x$, so the derivative comes outside:

$$
v(Y)=\frac{\mathrm d}{\mathrm dx}\int_0^Y(U-u)\,\mathrm dy.
$$

Let $Y\to\infty$ and use $\delta^*=\int_0^\infty(1-u/U)\,\mathrm dy$:

$$
\boxed{v_e=U\frac{\mathrm d\delta^*}{\mathrm dx}.}
$$

For Blasius $\delta^*\propto x^{1/2}$, so $\mathrm d\delta^*/\mathrm dx=\delta^*/(2x)$:

$$
v_e=8\times\frac{1.490\times10^{-3}}{2\times0.4}=\boxed{14.9\ \text{mm/s}}=\frac{0.860\,U}{\sqrt{Re_L}}.
$$

The streamlines leave the plate at only $0.11^\circ$. The outer flow does not see a zero-thickness plate. It sees the **effective (displaced) body**: the plate thickened by $\delta^*$ on each side, here 2.98 mm in total at the TE ([[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#Physical meaning: the effective body (slide 17)|3.1 §3]]). This is the lecture's answer to "where does the potential flow start?": outside the displaced surface (BL1, ll. 126–145; [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#The effective body (slides 98–99)|3.2, the effective body]]).

**(d)** Exponent:

$$
m=\frac{\beta}{2-\beta}=\frac{-0.18}{2.18}=\boxed{-0.0826}\quad(U_e\ \text{falls with }x:\ \text{adverse gradient}).
$$

Wall turning angle. $\beta\pi$ is the included angle of a **symmetric** wedge, so a single wall turns by half of it ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Special cases and the wedge angle (slide 77)|3.2 §6]]):

$$
\delta_w=-\frac{\beta\pi}{2}=0.09\pi=\boxed{16.2^\circ}\ \text{away from the flow}.
$$

Station values, using $Re_x=8\times0.3/1.5\times10^{-5}=1.6\times10^5$ ($\sqrt{Re_x}=400$):

$$
\sqrt{\frac{2}{m+1}}=\sqrt{\frac{2}{0.91743}}=1.4765.
$$

$$
\frac{\delta^*}{x}=\frac{\eta^*\sqrt{2/(m+1)}}{\sqrt{Re_x}}=\frac{1.8716\times1.4765}{400}=6.908\times10^{-3}\quad\Longrightarrow\quad\boxed{\delta^*=2.07\ \text{mm}},
$$

$$
\frac{\theta}{x}=\frac{0.5677\times1.4765}{400}=2.095\times10^{-3}\quad\Longrightarrow\quad\boxed{\theta=0.629\ \text{mm}},\qquad H=\frac{1.8716}{0.5677}=\boxed{3.30},
$$

$$
C_f=\frac{2f''(0)\sqrt{(m+1)/2}}{\sqrt{Re_x}}=\frac{2(0.1286)(0.6773)}{400}=\boxed{4.36\times10^{-4}.}
$$

(Formulae from [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Step 6: thicknesses and friction for any β|3.2 §6, Step 6]]. Note that $\theta^*\neq f''(0)$ when $\beta\neq0$.)

Blasius at the same $Re_x$: $\delta^*=1.291$ mm, $\theta=0.498$ mm, $H=2.59$, $C_f=1.66\times10^{-3}$.

| | $\delta^*$ | $\theta$ | $H$ | $C_f$ |
|---|---:|---:|---:|---:|
| $\beta=-0.18$ | 2.07 mm | 0.629 mm | 3.30 | $4.36\times10^{-4}$ |
| Blasius | 1.29 mm | 0.498 mm | 2.59 | $1.66\times10^{-3}$ |
| ratio | 1.61 | 1.26 | 1.27 | 0.26 |

**Comment.** The adverse gradient decelerates the slow near-wall fluid. The profile empties ($H$ rises from 2.59 towards 4.03, the separation value), the displacement thickness grows by 60 %, and the wall shear falls by three quarters. A wall turned away by only $16^\circ$ already does this; at about $18^\circ$ ($\beta=-0.1988$) the wall shear vanishes and the layer separates. A laminar layer tolerates only a very mild adverse gradient (BL2, ll. 636–655).

> [!check] Python (shooting, RK45, tolerance $10^{-11}$)
> Recomputed data: Blasius $f''(0)=0.46960$, $\eta^*=1.21678$, $\theta^*=0.46960$, $\eta_{99}=3.4719$, $H=2.5911$. $\beta=-0.18$: $f''(0)=0.12864$, $\eta^*=1.87158$, $\theta^*=0.56771$, $H=3.2967$.
>
> Plate: $Re_L=2.1333\times10^5$; $\xi=1.2247$ mm; $\delta_{99}=4.250$, $\delta^*=1.490$, $\theta=0.5751$ mm; $C_f=1.4379\times10^{-3}$; $\tau_w=0.05521$ Pa. $D=0.04417$ N/m by both routes (and by numerical quadrature of $\tau_w$); $C_D=2.876\times10^{-3}$. $v_e=14.903$ mm/s $=0.8604U/\sqrt{Re_L}$ ✓ (from the Blasius solution, $(\eta f'-f)/\sqrt2\to0.8604$).
>
> Diffuser: $m=-0.08257$; $\delta_w=16.200^\circ$; $\delta^*=2.0725$ mm, $\theta=0.6286$ mm, $H=3.2968$, $C_f=4.355\times10^{-4}$; Blasius $1.2908$ mm, $0.4980$ mm, $1.660\times10^{-3}$; ratios 1.6057, 1.2623, 0.2623.

---

## Q8. Integral estimate with a sine profile; laminar against turbulent

**[20 marks; target 30 min]**

A laminar flat-plate boundary layer is approximated by

$$
\frac{u}{U_e}=\sin\left(\frac{\pi}{2}\frac y\delta\right)\quad(y\leq\delta),\qquad\frac{u}{U_e}=1\quad(y>\delta).
$$

(a) Find $\delta^*/\delta$, $\theta/\delta$, $H$, and $C_f$ in terms of $Re_\delta=U_e\delta/\nu$. **[6]**

(b) State where the relation $\mathrm d\theta/\mathrm dx=C_f/2$ comes from and when it holds. Use it to find $\delta/x$, $\theta/x$, $\delta^*/x$ and $C_f$ as functions of $Re_x$, and compare them with Blasius ($\delta^*/x=1.721$, $\theta/x=C_f=0.664$, $H=2.59$, all $/\sqrt{Re_x}$ except $H$). **[6]**

(c) Evaluate $\delta$, $\theta$, $\delta^*$ and $C_f$ at $x=0.5$ m for $U_e=10$ m/s, $\nu=1.5\times10^{-5}$ m²/s. **[3]**

(d) A turbulent layer is often represented by $u/U_e=(y/\delta)^{1/7}$. Find its $H$, and compare $u/U_e$ for the two profiles at $y/\delta=0.1$. Explain which layer has the higher skin friction and why. Explain why $H$ is a useful diagnostic, and why $\mathrm d\theta/\mathrm dx=C_f/2$ cannot be applied as it stands on an aerofoil. **[5]**

### Solution

Let $\eta=y/\delta$, so $\mathrm dy=\delta\,\mathrm d\eta$; the integrands vanish for $\eta>1$ ([[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#7. Worked example: the linear profile (revision 3.1 Q4)|3.1 §7]] does the same for a straight line).

**(a) Displacement thickness:**

$$
\frac{\delta^*}{\delta}=\int_0^1\left(1-\sin\frac{\pi\eta}{2}\right)\mathrm d\eta=\left[\eta+\frac2\pi\cos\frac{\pi\eta}{2}\right]_0^1.
$$

$$
\frac{\delta^*}{\delta}=\left(1+0\right)-\left(0+\frac2\pi\right)=1-\frac2\pi=\boxed{0.3634.}
$$

**Momentum thickness.** Two standard integrals:

$$
\int_0^1\sin\frac{\pi\eta}{2}\,\mathrm d\eta=\frac2\pi,\qquad\int_0^1\sin^2\frac{\pi\eta}{2}\,\mathrm d\eta=\int_0^1\frac{1-\cos\pi\eta}{2}\,\mathrm d\eta=\frac12.
$$

$$
\frac\theta\delta=\int_0^1\left(\sin\frac{\pi\eta}{2}-\sin^2\frac{\pi\eta}{2}\right)\mathrm d\eta=\frac2\pi-\frac12=\frac{4-\pi}{2\pi}=\boxed{0.1366.}
$$

**Shape factor:**

$$
H=\frac{1-2/\pi}{(4-\pi)/(2\pi)}=\frac{2(\pi-2)}{4-\pi}=\boxed{2.66.}
$$

**Skin friction.** The wall slope is $\mathrm d(u/U_e)/\mathrm d\eta|_0=\tfrac\pi2$, so

$$
\tau_w=\mu\frac{U_e}{\delta}\cdot\frac\pi2.
$$

$$
C_f=\frac{\tau_w}{\tfrac12\rho U_e^2}=\frac{\pi\nu}{U_e\delta}=\boxed{\frac{\pi}{Re_\delta}.}
$$

**(b) Origin.** For a flat plate (zero pressure gradient) a control volume gives $D=\rho U_e^2\theta$ ([[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#4. Momentum thickness θ: the control-volume derivation (slides 19–29)|3.1 §4]]). The drag is also $\int_0^x\tau_w\,\mathrm dx$. Differentiating both in $x$ gives $\rho U_e^2\,\mathrm d\theta/\mathrm dx=\tau_w$, i.e. $\mathrm d\theta/\mathrm dx=C_f/2$. It holds **for a flat plate only** (BL1, ll. 284–288).

Substitute the profile results:

$$
0.1366\,\frac{\mathrm d\delta}{\mathrm dx}=\frac12\cdot\frac{\pi\nu}{U_e\delta}.
$$

Separate variables:

$$
\delta\,\mathrm d\delta=\frac{\pi}{2(0.1366)}\frac{\nu}{U_e}\,\mathrm dx.
$$

Integrate from $\delta(0)=0$:

$$
\frac{\delta^2}{2}=\frac{\pi}{2(0.1366)}\frac{\nu x}{U_e}.
$$

$$
\delta^2=\frac{2\pi^2}{4-\pi}\frac{\nu x}{U_e}=22.995\,\frac{\nu x}{U_e}.
$$

$$
\boxed{\frac{\delta}{x}=\frac{4.795}{\sqrt{Re_x}}.}
$$

Then

$$
\frac{\theta}{x}=0.1366\times\frac{4.795}{\sqrt{Re_x}}=\frac{0.655}{\sqrt{Re_x}},\qquad\frac{\delta^*}{x}=0.3634\times\frac{4.795}{\sqrt{Re_x}}=\frac{1.743}{\sqrt{Re_x}},
$$

$$
C_f=\frac{\pi}{Re_\delta}=\frac{\pi}{4.795\sqrt{Re_x}}=\frac{0.655}{\sqrt{Re_x}}.
$$

$\theta/x$ and $C_f$ come out equal, as for Blasius. Since $\theta\propto\sqrt x$, $\mathrm d\theta/\mathrm dx=\theta/(2x)$, and equating that to $C_f/2$ forces $\theta/x=C_f$.

| | $\delta^*\sqrt{Re_x}/x$ | $\theta\sqrt{Re_x}/x$ | $C_f\sqrt{Re_x}$ | $H$ |
|---|---:|---:|---:|---:|
| sine profile | 1.743 | 0.655 | 0.655 | 2.66 |
| Blasius | 1.721 | 0.664 | 0.664 | 2.59 |
| error | +1.3 % | −1.3 % | −1.3 % | +2.7 % |

A good guess of the profile shape gives integral quantities within about 1 % (the straight line of revision 3.1 Q4 is 13 % low in $C_f$). $\theta$ is an integral, so it averages out the local errors in the profile.

**(c)** $Re_x=10\times0.5/1.5\times10^{-5}=3.333\times10^5$, so $\sqrt{Re_x}=577.4$:

$$
\delta=\frac{4.795\times0.5}{577.4}=\boxed{4.15\ \text{mm}}\quad(\text{Blasius }\delta_{99}=4.25\ \text{mm}),
$$

$$
\theta=\frac{0.655\times0.5}{577.4}=\boxed{0.567\ \text{mm}},\qquad\delta^*=\frac{1.743\times0.5}{577.4}=\boxed{1.51\ \text{mm}},
$$

$$
C_f=\frac{0.655}{577.4}=\boxed{1.135\times10^{-3}}\quad(\text{Blasius }1.150\times10^{-3}).
$$

**(d)** **1/7 power law:**

$$
\frac{\delta^*}{\delta}=\int_0^1\left(1-\eta^{1/7}\right)\mathrm d\eta=1-\frac78=\frac18,\qquad\frac\theta\delta=\int_0^1\left(\eta^{1/7}-\eta^{2/7}\right)\mathrm d\eta=\frac78-\frac79=\frac{7}{72},
$$

$$
H=\frac{1/8}{7/72}=\frac97=\boxed{1.29.}
$$

At $y/\delta=0.1$: sine profile $u/U_e=0.156$; power law $0.720$.
- **Friction.** The turbulent profile is much **fuller**: it reaches most of $U_e$ very close to the wall, so its wall gradient, and hence $\tau_w=\mu\,\partial u/\partial y|_0$, is much larger. A turbulent layer has more skin-friction drag (BL1, ll. 82–88; [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#2. Boundary-layer thickness δ99 (slides 8–9)|3.1 §2]]). The power law itself has an infinite slope at $y=0$. It describes the outer turbulent layer, not the viscous sublayer, so $\tau_w$ cannot be taken from its slope.
- **$H$ as a diagnostic.** It is a single number for the profile shape ([[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#6. Shape factor H (slide 31)|3.1 §6]]): about 2.6 for a laminar flat plate, about 1.3 for a turbulent one, and rising above about 3.5–4 towards laminar separation. A measured fall in $H$ along a plate signals transition. The lecture: $H$ tells you whether the layer is laminar or turbulent and whether there is a pressure gradient (BL1, ll. 234–250).
- **Aerofoils.** The flat-plate relation assumes uniform pressure on the control volume ($U_e$ constant). On an aerofoil $U_e(x)$ varies, so the pressure forces on the control volume do not cancel and $\theta$ changes for a second reason. The general momentum integral equation adds that pressure-gradient term. Its derivation is CH3-5, which has not yet been lectured ([[SESA3043 3.5 - Momentum Integral Equation|3.5]], written ahead).

> [!check] Python (sympy and numpy)
> Sine profile: $\delta^*/\delta=(\pi-2)/\pi=0.36338$, $\theta/\delta=(4-\pi)/(2\pi)=0.13662$, $H=2.65979$, wall slope $\pi/2$. $\delta^2=22.9952\,\nu x/U_e$, so $\delta/x=4.7953/\sqrt{Re_x}$; $\theta/x=0.6551$, $\delta^*/x=1.7425$, $C_f\sqrt{Re_x}=0.6551$; errors against Blasius $-1.33\,\%$ ($C_f$), $+1.25\,\%$ ($\delta^*$), $+2.66\,\%$ ($H$). At $x=0.5$ m: $\delta=4.1529$ mm, $\theta=0.5674$ mm, $\delta^*=1.5091$ mm, $C_f=1.1347\times10^{-3}$ (Blasius $\delta_{99}=4.2522$ mm, $C_f=1.1501\times10^{-3}$). Power law: $1/8$, $7/72$, $H=9/7=1.2857$. At $y/\delta=0.1$: 0.1564 and 0.7197.

---

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]] · [[SESA3043 Formula Sheet]]
- Revision-question solutions: [[SESA3043 Ch1 Revision Questions - Worked Solutions]] · [[SESA3043 Ch2 Revision Questions - Worked Solutions]] · [[SESA3043 Ch3 Revision Questions - Worked Solutions]]
- Theory: [[SESA3043 1.1 - Mathematical Tools and Flow Description|1.1]] · [[SESA3043 1.2 - Conservation Laws and Governing Equations|1.2]] · [[SESA3043 1.2b - Potential-Flow Review|1.2b]] · [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli|1.3]] · [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers|1.4]] · [[SESA3043 2.1 - Complex Functions and Conformal Mapping|2.1]] · [[SESA3043 2.2 - Lumped Vortex Method|2.2]] · [[SESA3043 2.3 - Panel Methods|2.3]] · [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures|3.1]] · [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions|3.2]]
- Concepts: [[Reynolds Transport Theorem]] · [[Unsteady Bernoulli Equation]] · [[Wedge and Corner Flows]] · [[Order-of-Magnitude Analysis]] · [[Joukowski Transformation]] · [[Lumped Vortex Method]] · [[Panel Method]] · [[Blasius and Falkner-Skan Similarity Solutions]] · [[Viscous-Inviscid Interaction]]

## Sources

- Written from the lectured topic notes listed in the frontmatter; transcript line references are those cited in the topic notes (L5 = `02 October 2026 at 14_53_48.txt`; L-b = `09 October 2026 at 14_57_18.txt`; GE = `15 October 2026 at 13_48_35.txt`; PM1, PM2 = `16 October 2026 at 14_54_40.txt`, `16 October 2026 at 15_53_48.txt`; BL1 = `22 October 2026 at 13_51_55.txt`; BL2 = `23 October 2026 at 14_53_16.txt`).
- `03 - Exams & Past Papers/Ch1_Revision_Questions.pdf`, `Ch2_Revision_Questions.pdf`, `Ch3_Revision_Questions.pdf` (checked so as not to duplicate them).
- Figures: `01 - Notes/Figures/generate_aero_mock_figures.py` (`aa_mock_flap_lvm.png`, `aa_mock_square_panels.png`).
- Numerical checks: Python (numpy, scipy, sympy), run 24 Oct 2026.
