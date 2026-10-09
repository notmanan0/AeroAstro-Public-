---
title: "MATH2048 PDE3 - The Heat Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 12
tags:
  - math2048
  - pdes
  - heat-equation
  - diffusion
aliases: ["MATH2048 Lecture 17", "Diffusion equation", "Random walk derivation"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]"]
next_topics: ["[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
key_concepts: ["[[Heat Equation]]", "[[Separation of Variables]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture17_Parabolic1.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 6)"]
---

# MATH2048 PDE3 - The Heat Equation

> [!abstract] Summary
> $u_t=\kappa^2u_{xx}$ (the lectures write the diffusivity as $\kappa^2$) has only a **first** time derivative. So:
> - only **one** initial condition, $u(x,0)$, is needed;
> - the time behaviour is **exponential decay**, $e^{-\kappa^2(n\pi/L)^2t}$, not oscillation.
>
> The spatial eigenproblem is identical to the wave equation's. Higher modes die out fastest, so solutions smooth out towards their steady state:
> - $0$ for Dirichlet (cold) ends;
> - the **mean value** for Neumann (insulated) ends.

## Key Concepts
- [[Heat Equation]] · [[Separation of Variables]] · [[ODE Eigenvalue Problems]]

---

## 1. Derivation by random walk (L17)
Suppose walkers on a grid with spacing $\Delta x$ each flip two coins every time step $\Delta t$:
- two heads: move right;
- two tails: move left;
- one of each: stay put.

Counting who arrives at $x$ gives
$$
y(x,t+\Delta t)=\tfrac14\big[y(x+\Delta x,t)+y(x-\Delta x,t)+2y(x,t)\big].
$$

Taylor-expand both sides: the left side is $y+y_t\Delta t$, and on the right $y(x\pm\Delta x)=y\pm y_x\Delta x+\frac12y_{xx}\Delta x^2$. The $y$ terms and the $y_x$ terms cancel, leaving
$$
y_t\,\Delta t=\tfrac14y_{xx}\,\Delta x^2\quad\Longrightarrow\quad y_t=\kappa^2y_{xx},\qquad \kappa^2=\lim\frac{(\Delta x)^2}{4\Delta t}.
$$

*Physical version (Notes Ch. 6)*: combine conservation of energy with Fourier's law, flux $=-k\,u_x$. This also gives diffusivity $=\dfrac{k}{\rho c_p}$.

### Physical derivation (Lecture Notes §6.1)
Model a rod with conductivity $\kappa$, cross-sectional area $A$ and specific-heat-type constant $s$, insulated along its sides.
1. **Fourier's law.** The heat flow rate through a cross-section is $H(x,t)=-\kappa A\,T_x$. Heat flows from hot to cold.
2. **Net inflow.** The net flow into the slice $[x_0,x_0+\delta x]$ is $Q=H(x_0)-H(x_0+\delta x)\approx\kappa A\,T_{xx}\,\delta x$.
3. **Heat balance.** The temperature change is $\delta T=\dfrac{Q\,\delta t}{sA\,\delta x}$.
4. **Limit.** Letting $\delta x,\delta t\to0$ gives $T_t=\frac{\kappa}{s}T_{xx}$, which is the heat equation with diffusivity $\alpha^2=\kappa/s$.

### Generalised heat equation (§6.3, sets up Sturm–Liouville)
If the properties vary along the rod, and there is heat loss $-qy$ and a source $F$:
$$r(x)\,y_t=\big(p(x)\,y_x\big)_x-q(x)\,y+F(x,t).$$
Separating $y=XT$ in the homogeneous case gives $\dot T+\lambda T=0$ and $(pX')'-qX+\lambda rX=0$. The second equation is exactly a **Sturm–Liouville problem**. The general theory then guarantees real eigenvalues and orthogonal eigenfunctions (with weight $r$), and says which BCs are allowed.

### Allowed boundary conditions (§6.4)
Any combination of the following at each end works:
- Dirichlet: $y=0$;
- Neumann: $y'=0$;
- radiation (Robin): $y+ky'=0$;
- periodic;
- a singular point, where $p=0$.

For the general condition $\alpha_1y(0)+\beta_1y'(0)=0$, the $\lambda>0$ case gives only $X\equiv0$. Writing $X=A\sinh\mu x+B\cosh\mu x$ makes this quick to check.

The $\lambda=0$ case can give $X=\text{const}$, and then $T=Ct+D$. Boundedness usually forces $C=0$. The radiation condition is an exception where $X=Ax$ can survive.

## 2. Separation of variables: insulated rod (L17)
Solve $u_t=\kappa^2u_{xx}$ on $[0,1]$ with $u_x(0,t)=u_x(1,t)=0$ and $u(x,0)=x(1-x)$.

**Step 1.** With $u=XT$: $\dfrac{\dot T}{\kappa^2T}=\dfrac{X''}{X}=\lambda$.

**Steps 2–3.** $X'(0)=X'(1)=0$. This is the Neumann eigenproblem from [[MATH2048 PDE2 - Separation of Variables for the Wave Equation|PDE2]]:
- $\lambda_0=0$ with $X_0=1$;
- $\lambda_n=-(n\pi)^2$ with $X_n=\cos n\pi x$.

**Step 4.** The $T$ equation is now **first order**: $\dot T_n=-\kappa^2(n\pi)^2T_n$. Separating variables,
$$
\int\frac{dT_n}{T_n}=-\kappa^2(n\pi)^2\int dt\ \Longrightarrow\ T_n=C_ne^{-\kappa^2(n\pi)^2t},\qquad T_0=\text{const}.
$$

**Step 5.**
$$
u=H+\sum_{n\geq1}C_ne^{-\kappa^2(n\pi)^2t}\cos n\pi x .
$$

**Step 6.** Only $u(x,0)$ is given. It is the same cosine series as the open pipe, so $H=\frac16$ and $C_n=-\frac{2[1+(-1)^n]}{(n\pi)^2}$:
$$
\boxed{u(x,t)=\frac16-\sum_{n\ \mathrm{even}}\frac{4}{(n\pi)^2}e^{-\kappa^2(n\pi)^2t}\cos n\pi x}
$$
The slides set $\kappa=1$.

![[m2048_pde_heat_dirichlet_vs_neumann.png|760]]

> [!note] Physical reading
> **Insulated ends**: no heat leaves the rod, so the total heat $\int u\,dx$ is conserved and $u$ tends to its mean value, $\frac16$. That mean is exactly the $\lambda=0$ mode.
>
> **Dirichlet ends**, $u=0$ (held cold): heat leaks out through the ends and $u\to0$. The slowest mode, $n=1$, decays like $e^{-\kappa^2\pi^2t}$, so the time scale is $\sim\frac{L^2}{\pi^2\kappa^2}$.

## 3. Wave vs heat: what changes
| | Wave $y_{tt}=c^2y_{xx}$ | Heat $u_t=\kappa^2u_{xx}$ |
|---|---|---|
| Initial data | $y$ and $y_t$ | $u$ only |
| $T_n$ ODE | $\ddot T_n+\omega_n^2T_n=0$ | $\dot T_n+\kappa^2k_n^2T_n=0$ |
| $T_n$ | $C_n\cos\omega_nt+D_n\sin\omega_nt$ | $C_ne^{-\kappa^2k_n^2t}$ |
| $\lambda=0$ mode (Neumann) | $Gt+H$ | $H$ |
| Long-time behaviour | oscillates forever | decays to steady state |
| Physics | finite speed $c$ | "infinite speed", smoothing |

> [!example] Exam 2023/24 A2: $u_t=\frac14u_{xx}$ on $[0,\pi]$, insulated ends, $u(x,0)=\cos^3x$
> - The eigenfunctions are $\cos nx$, with $T_n=e^{-n^2t/4}$.
> - Use the identity $\cos^3x=\frac34\cos x+\frac14\cos3x$. Match terms by orthogonality: no integrals are needed.
>
> $$u=\tfrac34e^{-t/4}\cos x+\tfrac14e^{-9t/4}\cos3x .$$
>
> Full solution in [[MATH2048 Past Paper Solutions]].

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]] · Next: [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]
- Practice: [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] (PS7 Q1–2)

## Sources
- Lecture 17; Lecture Notes Ch. 6. Coefficients verified in SymPy.
