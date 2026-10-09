---
title: "MATH2048 Problem Sheets 6-7 Solutions - PDEs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: tutorial
stream: "Block 4: Partial Differential Equations"
tags:
  - math2048
  - tutorial-solutions
  - pdes
sheet: "PS6 (The wave equation) + PS7 (More separation of variables)"
theory_notes: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]", "[[MATH2048 PDE3 - The Heat Equation]]", "[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]"]
key_concepts: ["[[Separation of Variables]]", "[[Wave Equation]]", "[[Heat Equation]]", "[[Eigenfunction Expansion Method]]"]
status: complete
sources: ["02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 6.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 7.pdf"]
---

# MATH2048 Problem Sheets 6-7 Solutions - PDEs

> [!abstract] Sheet Info
> Every result shown on the sheets is reproduced. Coefficients were checked by SymPy integration, the time ODEs with `dsolve`, and the substitution in PS7 Q2 symbolically.

## Theory Links
- [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]] · [[MATH2048 PDE3 - The Heat Equation]] · [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]

---

# PS6: The wave equation

The shared set-up for both questions is $y_{tt}=c^2y_{xx}$ with $y(0,t)=y(L,t)=0$. Steps 1–5 are as in [[MATH2048 PDE2 - Separation of Variables for the Wave Equation|PDE2]] and give

$$
y=\sum_{n\geq1}\Big[C_n\cos\frac{n\pi ct}L+D_n\sin\frac{n\pi ct}L\Big]\sin\frac{n\pi x}{L}.
$$

The initial velocity is zero, so every $D_n=0$ and $C_n=\frac2L\int_0^Lf\sin\frac{n\pi x}{L}dx$.

## Q1: Plucked string (triangle of height $h$ at $L/2$), $c=1$
**Symmetry shortcut.** $f$ is symmetric about $x=L/2$, i.e. $f(L-x)=f(x)$. Also $\sin\frac{n\pi(L-x)}{L}=\sin\big(n\pi-\frac{n\pi x}L\big)=-(-1)^n\sin\frac{n\pi x}{L}$. So:
- for **even** $n$ the integrand is antisymmetric about $L/2$, and $C_n=0$;
- for **odd** $n$ the integrand is symmetric, so the integral is twice the first half.

**Odd $n$.** Let $k=n\pi/L$. Then

$$
C_n=2\cdot\frac2L\cdot\frac{2h}{L}\int_0^{L/2}x\sin kx\,dx=\frac{8h}{L^2}\Big[-\frac{x\cos kx}{k}+\frac{\sin kx}{k^2}\Big]_0^{L/2}=\frac{8h}{L^2}\Big[-\frac{L}{2k}\cos\frac{n\pi}{2}+\frac{L^2}{n^2\pi^2}\sin\frac{n\pi}{2}\Big].
$$

For odd $n$, $\cos\frac{n\pi}2=0$, which leaves

$$
C_n=\frac{8h}{n^2\pi^2}\sin\frac{n\pi}{2}=\frac{8h(-1)^{(n-1)/2}}{n^2\pi^2}.
$$

SymPy gives $\frac{8h\sin(n\pi/2)}{\pi^2n^2}$ for all $n$, which already vanishes for even $n$ ✔.

$$
\boxed{y(x,t)=\frac{8h}{\pi^2}\sum_{n\ \mathrm{odd}}\frac{(-1)^{(n-1)/2}}{n^2}\sin\frac{n\pi x}{L}\cos\frac{n\pi t}{L}}
$$

See the figure in [[MATH2048 PDE2 - Separation of Variables for the Wave Equation|PDE2]].

## Q2: Antisymmetric "Z" displacement
$f=\frac{2\alpha}{L}x$ on $(0,\frac L2)$ and $f=-\frac{2\alpha}{L}(L-x)$ on $(\frac L2,L)$. Here $c^2=T/\rho$, and the sheet's $l$ is $L$.

**Symmetry.** Now $f(L-x)=-f(x)$, which is antisymmetric about $L/2$. By the same argument as Q1:
- **odd** $n$ give $C_n=0$;
- **even** $n=2k$ give twice the first-half integral.

**Even $n=2k$.** Let $\kappa=2k\pi/L$. Then

$$
C_{2k}=2\cdot\frac2L\cdot\frac{2\alpha}L\int_0^{L/2}x\sin\kappa x\,dx=\frac{8\alpha}{L^2}\Big[-\frac{x\cos\kappa x}{\kappa}+\frac{\sin\kappa x}{\kappa^2}\Big]_0^{L/2}=\frac{8\alpha}{L^2}\Big[-\frac{L}{2}\cdot\frac{L\cos k\pi}{2k\pi}\Big]=\frac{2\alpha(-1)^{k+1}}{k\pi}.
$$

The $\sin\kappa x$ term vanishes because $\sin k\pi=0$.

$$
\boxed{y=\sum_{k=1}^\infty\frac{2\alpha}{k\pi}(-1)^{k+1}\sin\frac{2k\pi x}{L}\cos\frac{2k\pi ct}{L}}\ ✔
$$

SymPy gives $b_n=-\frac{4\alpha\cos(n\pi/2)}{n\pi}$, so $b_2=\frac{2\alpha}\pi$ and $b_4=-\frac\alpha\pi$, as expected. The midpoint of the string never moves: it is a node of every even mode.

---

# PS7: More separation of variables

## Q1: $u_t=\frac14u_{xx}$ on $[0,\pi]$, insulated ends, $u(x,0)=7+5\cos2x$
**(a) Separated equations.** Substitute $u=X(x)T(t)$:

$$X\dot T=\tfrac14X''T\ \Longrightarrow\ \frac{4\dot T}{T}=\frac{X''}{X}=\lambda .$$

So $X''-\lambda X=0$ and $\dot T-\frac\lambda4T=0$.

**(b) Eigenproblem.** The BCs are $X'(0)=X'(\pi)=0$.
- $\lambda=k^2>0$: $X'=k(Ae^{kx}-Be^{-kx})$. Then $A=B$ and $A(e^{k\pi}-e^{-k\pi})=0$, so the solution is trivial.
- $\lambda=0$: $X=A+Bx$ with $B=0$, so $X_0=1$ with $\lambda_0=0$.
- $\lambda=-k^2$: $X=A\cos kx+B\sin kx$. $X'(0)=kB=0$, then $X'(\pi)=-kA\sin k\pi=0$, so $k=n$.

$$X_n=\cos nx,\qquad \lambda_n=-n^2,\qquad n=0,1,2,\dots$$

**(c) Time equation.** $\dot T_n=-\frac{n^2}{4}T_n$, so $T_n=e^{-n^2t/4}$ (and $T_0=1$).

**(d) Fit the initial data.** $u=\sum_{n\geq0}A_ne^{-n^2t/4}\cos nx$. At $t=0$ this must equal $7+5\cos2x$. By orthogonality, compare coefficients directly: $A_0=7$, $A_2=5$, and all other $A_n=0$.

$$\boxed{u=7+5e^{-t}\cos2x}$$

Check: $u_t=-5e^{-t}\cos2x$ and $\frac14u_{xx}=\frac14(-20e^{-t}\cos2x)$, which are equal ✔.

## Q2: Heat equation with decay term, $u_t=h^2u_{xx}-ku$
**(a) Substitution.** Put $u=e^{-kt}v$. Then $u_t=e^{-kt}(v_t-kv)$ and $u_{xx}=e^{-kt}v_{xx}$. Substituting:

$$e^{-kt}(v_t-kv)=h^2e^{-kt}v_{xx}-ke^{-kt}v\ \Longrightarrow\ v_t=h^2v_{xx}\ ✔$$

SymPy confirms the residual reduces to exactly $v_t-h^2v_{xx}$.

**(b) New conditions.** $e^{-kt}\neq0$, so $v(0,t)=v(1,t)=0$. At $t=0$, $e^0=1$, so $v(x,0)=u(x,0)=x(1-x)$.

**(c) Solve for $v$, then $u$.** The eigenfunctions are $\sin n\pi x$ and $T_n=e^{-h^2n^2\pi^2t}$. The coefficients are the $x(1-x)$ sine coefficients $\frac{4[1-(-1)^n]}{(n\pi)^3}$, so

$$v=\sum_{n\ \mathrm{odd}}\frac{8}{(n\pi)^3}e^{-h^2n^2\pi^2t}\sin n\pi x,\qquad \boxed{u=\sum_{n\ \mathrm{odd}}\frac{8}{(n\pi)^3}e^{-(k+h^2n^2\pi^2)t}\sin n\pi x}$$

## Q3: Switched source, $u_t=u_{xx}+f(\tau-t)\sin^2\pi x$
The ends are insulated, $u(x,0)=0$, and $f=1$ for $0\leq t\leq\tau$ and $0$ afterwards.

**Eigenfunctions.** Neumann BCs on $[0,1]$ give $\cos n\pi x$, $n\geq0$. Write $u=T_0(t)+\sum_{n\geq1}T_n(t)\cos n\pi x$.

**Expand the source.** $\sin^2\pi x=\frac12-\frac12\cos2\pi x$, which uses only the $n=0$ and $n=2$ modes. So $F=\frac f2-\frac f2\cos2\pi x$.

**Mode ODEs.** Orthogonality gives one ODE per mode:

$$\dot T_0=\tfrac12f,\qquad \dot T_2+4\pi^2T_2=-\tfrac12f,\qquad \dot T_n+n^2\pi^2T_n=0\ (n\neq0,2).$$

All $T_n(0)=0$, so $T_n\equiv0$ for $n\neq0,2$.

**While the source is on** ($0\leq t\leq\tau$, $f=1$):

$$T_0=\frac t2,\qquad T_2=-\frac{1-e^{-4\pi^2t}}{8\pi^2}\ \ (\text{SymPy ✔}).$$

**After it switches off** ($t>\tau$, $f=0$): $T_0$ stays at $\frac\tau2$, and $T_2$ decays freely from its value at $t=\tau$:

$$T_2=-\frac{1-e^{-4\pi^2\tau}}{8\pi^2}e^{-4\pi^2(t-\tau)}.$$

$$
\boxed{u=\begin{cases}\dfrac t2-\dfrac{1-e^{-4\pi^2t}}{8\pi^2}\cos2\pi x,&0\leq t\leq\tau,\\[8pt]\dfrac\tau2-\dfrac{\left(e^{4\pi^2\tau}-1\right)e^{-4\pi^2t}}{8\pi^2}\cos2\pi x,&t>\tau.\end{cases}}
$$

**Physical check.** The rod is insulated, so no heat escapes. The heat put in is $\int_0^\tau\!\int_0^1\sin^2\pi x\,dx\,dt=\frac\tau2$, which is exactly the final uniform temperature $\frac\tau2$ ✔. Also, $u$ is continuous at $t=\tau$ ✔.

## Q4: Mixed BCs, $u(0,t)=0$ and $u_x(1,t)=C$, with $u(x,0)=0$
**Remove the inhomogeneous BC.** $y_P=Cx$ satisfies both BCs and the PDE (it is a steady state). Set $v=u-Cx$. Then

$$v_t=\kappa^2v_{xx},\qquad v(0,t)=0,\qquad v_x(1,t)=0,\qquad v(x,0)=-Cx .$$

**Eigenproblem (Dirichlet–Neumann).** $X_n=\sin k_nx$ with $k_n=\big(n-\tfrac12\big)\pi$, from $\cos k=0$. So $T_n=e^{-\kappa^2k_n^2t}$.

**Coefficients.** $b_n=2\int_0^1(-Cx)\sin k_nx\,dx$. The antiderivative is $\int x\sin kx\,dx=\frac{\sin kx}{k^2}-\frac{x\cos kx}{k}$. At $x=1$ we have $\cos k_n=0$ and $\sin k_n=(-1)^{n+1}$, so

$$b_n=-2C\frac{(-1)^{n+1}}{k_n^2}=\frac{2C(-1)^n}{(n-\frac12)^2\pi^2}\ ✔\ \text{(SymPy)}.$$

$$\boxed{u=C\Big\{x+\frac{2}{\pi^2}\sum_{n=1}^\infty\frac{(-1)^n}{(n-\frac12)^2}\sin\Big[\big(n-\tfrac12\big)\pi x\Big]e^{-(n-\frac12)^2\pi^2\kappa^2t}\Big\}}$$

As $t\to\infty$, $u\to Cx$: a steady linear profile carrying constant heat flux.

## Sources
- PS6 and PS7. Verified in SymPy (`pde_check.py` in the session scratchpad).
