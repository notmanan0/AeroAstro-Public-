---
title: "MATH2048 PDE2 - Separation of Variables for the Wave Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 11
tags:
  - math2048
  - pdes
  - wave-equation
  - separation-of-variables
aliases: ["MATH2048 Lecture 15", "MATH2048 Lecture 16", "Normal modes", "Six-step method"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]", "[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]", "[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
next_topics: ["[[MATH2048 PDE3 - The Heat Equation]]"]
key_concepts: ["[[Separation of Variables]]", "[[Wave Equation]]", "[[ODE Eigenvalue Problems]]", "[[Half-Range Expansions]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture15_Hyperbolic2.pdf", "02 - Sources/Lectures & Problem Sheets/PDEs/Lecture16_Hyperbolic3.pdf"]
---

# MATH2048 PDE2 - Separation of Variables for the Wave Equation

> [!abstract] Summary
> **The six-step method** is examined every year, worth 25 marks. It combines all three earlier blocks:
> 1. Separate $y=X(x)T(t)$ into two ODEs.
> 2. Turn the BCs on $y$ into BCs on $X$.
> 3. Solve the **eigenvalue problem** for $X$ (Block 1).
> 4. Solve the $T$ ODE, which is a constant-coefficient ODE (Block 1).
> 5. Superpose the normal modes.
> 6. Fit the initial data with a **half-range Fourier series** (Block 2).
>
> Dirichlet ends give a sine series. Neumann ends give a cosine series and include an $n=0$ mode.

## Key Concepts
- [[Separation of Variables]] · [[Wave Equation]] · [[ODE Eigenvalue Problems]] · [[Half-Range Expansions]]

---

## Step 1: Separate (L15)
Substitute $y=X(x)T(t)$ into $y_{tt}=c^2y_{xx}$ to get $X\ddot T=c^2X''T$, then divide by $c^2XT$:
$$
\underbrace{\frac{\ddot T}{c^2T}}_{\text{function of }t\text{ only}}=\underbrace{\frac{X''}{X}}_{\text{function of }x\text{ only}}=\lambda\ (\text{constant}).
$$

> [!important] Why the separation constant exists
> Fix $x$ and vary $t$: the right-hand side does not change, so the left-hand side is constant. The same argument works the other way round, so both sides equal one constant $\lambda$.

This gives two ODEs:
$$
X''-\lambda X=0,\qquad \ddot T-\lambda c^2T=0 .
$$

## Step 2: BCs for $X$
$y(0,t)=X(0)T(t)=0$ for all $t$. We need $T\not\equiv0$ (otherwise $y\equiv0$), so $X(0)=0$. Likewise, $y(L,t)=0$ gives $X(L)=0$.

There are **no BCs on $T$**. Its constants are fixed by the initial data in step 6.

## Step 3: The eigenvalue problem
Solve $X''-\lambda X=0$ with $X(0)=X(L)=0$. **Note the sign**: with this convention the oscillatory case is $\lambda<0$.

| Case | $X$ | BCs give |
|---|---|---|
| $\lambda=k^2>0$ | $Ae^{kx}+Be^{-kx}$ | $A+B=0$, then $A(e^{kL}-e^{-kL})=0$, so $A=0$: trivial |
| $\lambda=0$ | $A+Bx$ | $A=0$, then $BL=0$: trivial |
| $\lambda=-k^2<0$ | $A\sin kx+B\cos kx$ | $B=0$, then $A\sin kL=0$, so $kL=n\pi$ |

$$
X_n=\sin\frac{n\pi x}{L},\qquad \lambda_n=-\Big(\frac{n\pi}{L}\Big)^2,\qquad n=1,2,\dots
$$

## Step 4: Solve for $T$
$\ddot T+\big(\tfrac{n\pi c}{L}\big)^2T=0$ is simple harmonic motion, so
$$
T_n=\tilde C_n\cos\omega_nt+\tilde D_n\sin\omega_nt,\qquad \omega_n=\frac{n\pi c}{L}.
$$
$\omega_n$ is the natural frequency of mode $n$. The fundamental is $\omega_1=\pi c/L$, and the higher modes are its **harmonics**, $\omega_n=n\omega_1$.

## Step 5: Superpose
The PDE is linear, so any sum of solutions is a solution:
$$
y(x,t)=\sum_{n=1}^\infty\Big[C_n\cos\frac{n\pi ct}{L}+D_n\sin\frac{n\pi ct}{L}\Big]\sin\frac{n\pi x}{L}.
$$

## Step 6: Initial data
Given $y(x,0)=f(x)$ and $y_t(x,0)=g(x)$, set $t=0$ in $y$ and in $y_t$:
$$
f(x)=\sum C_n\sin\frac{n\pi x}L,\qquad g(x)=\sum D_n\frac{n\pi c}{L}\sin\frac{n\pi x}L .
$$
These are **half-range sine series** on $[0,L]$, so
$$
C_n=\frac2L\int_0^Lf\sin\frac{n\pi x}{L}dx,\qquad D_n=\frac{2}{n\pi c}\int_0^Lg\sin\frac{n\pi x}{L}dx .
$$

> [!tip] Shortcut: match terms by inspection
> If $f$ is already a finite sum of the eigenfunctions, compare coefficients directly with no integrals. Examples: $f=\sin x$ gives $C_1=1$ and all other $C_n=0$. For a cosine basis, $\cos^3x=\frac34\cos x+\frac14\cos3x$. This is how the 2023/24 and 2025/26 part (d)s are meant to be done, and **orthogonality** justifies it.

---

## Example 1 (L16): guitar string, Dirichlet ends
$y_{tt}=c^2y_{xx}$ on $[0,1]$, with $y(0,t)=y(1,t)=0$, $y(x,0)=x(1-x)$ and $y_t(x,0)=0$.

The initial velocity is zero, so every $D_n=0$. Then
$$
C_n=2\int_0^1x(1-x)\sin n\pi x\,dx .
$$

Integrate by parts twice, with $u=x-x^2$ (so $u'=1-2x$ and $u''=-2$):
$$
C_n=2\Big[-\frac{(x-x^2)\cos n\pi x}{n\pi}+\frac{(1-2x)\sin n\pi x}{(n\pi)^2}-\frac{2\cos n\pi x}{(n\pi)^3}\Big]_0^1=2\cdot\frac{-2(-1)^n+2}{(n\pi)^3}=\frac{4\,[1-(-1)^n]}{(n\pi)^3}.
$$
The first two terms vanish at both limits, since $x-x^2=0$ at $0$ and $1$, and $\sin0=\sin n\pi=0$.

$$
\boxed{y=\sum_{n\ \mathrm{odd}}\frac{8}{(n\pi)^3}\cos(n\pi ct)\sin(n\pi x)}\ ✔\ \text{(SymPy)}
$$

Only odd modes appear, because $x(1-x)$ is symmetric about $x=\tfrac12$ and the even modes are antisymmetric about that point.

## Example 2 (L16): open pipe, Neumann ends
Same PDE and initial data, but now $y_x(0,t)=y_x(1,t)=0$.

**Step 3 again.**
- $\lambda=0$: $X=A+Bx$ and $X'=B=0$, so $X_0=1$ is a **non-trivial** solution.
- $\lambda=-k^2$: $X'=k(A\cos kx-B\sin kx)$. $X'(0)=0$ gives $A=0$, then $X'(1)=0$ gives $\sin k=0$, so $X_n=\cos n\pi x$.
- $\lambda>0$: trivial.

**Step 4.**
- $n=0$: $\ddot T=0$, so $T_0=Gt+H$. This mode is a rigid drift of the whole column.
- $n\geq1$: $T_n=C_n\cos n\pi ct+D_n\sin n\pi ct$.

**Step 5.**
$$
y=Gt+H+\sum_{n\geq1}\big[C_n\cos n\pi ct+D_n\sin n\pi ct\big]\cos n\pi x .
$$

**Step 6.** $y_t(x,0)=G+\sum n\pi cD_n\cos n\pi x=0$ gives $G=D_n=0$. Then $x(1-x)=H+\sum C_n\cos n\pi x$ is a **cosine** half-range series:
$$
H=\frac12a_0=\int_0^1x(1-x)dx=\frac16,\qquad C_n=2\int_0^1x(1-x)\cos n\pi x\,dx=-\frac{2\,[1+(-1)^n]}{(n\pi)^2}.
$$

$$
\boxed{y=\frac16-\sum_{n\ \mathrm{even}}\frac{4}{(n\pi)^2}\cos(n\pi ct)\cos(n\pi x)}\ ✔
$$

> [!warning] The $\lambda=0$ mode
> Neumann problems always have a $\lambda=0$ mode. Forgetting it loses the $\frac16$, the mean displacement. In the wave equation it also brings a $Gt$ term, which vanishes here only because the initial velocity has zero mean.

## Example 3 (PS6 Q1): plucked string
$f$ is a triangle of height $h$ at $x=L/2$, with $c=1$ and zero initial velocity:
$$
C_n=\frac{2}{L}\Big[\int_0^{L/2}\frac{2h}{L}x\sin\frac{n\pi x}Ldx+\int_{L/2}^L\frac{2h}{L}(L-x)\sin\frac{n\pi x}Ldx\Big]=\frac{8h}{n^2\pi^2}\sin\frac{n\pi}{2}.
$$
The full working is in [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]].

![[m2048_pde_plucked_string.png|640]]

The corners of the triangle travel outwards at speed $c$, which is d'Alembert's picture. The shape inverts at $t=L/c$ and returns at $t=2L/c$.

## Extra results from the Lecture Notes (§5.4.6)
### The standing-wave solution is d'Alembert in disguise
With zero initial velocity ($D_n=0$), use $\sin A\cos B=\frac12[\sin(A+B)+\sin(A-B)]$:
$$y=\sum C_n\cos\frac{n\pi ct}{L}\sin\frac{n\pi x}{L}=\frac12\big[p(x+ct)+p(x-ct)\big],$$
where $p$ is the **odd, $2L$-periodic extension** of the initial shape. The initial shape splits into two half-amplitude copies moving left and right at speed $c$. This is exactly what the plucked-string figure shows.

### Energy per normal mode
Substitute one mode into $E=\int_0^L\frac\rho2(y_t^2+c^2y_x^2)\,dx$. All the cross terms vanish by orthogonality, leaving
$$E_n=\frac{\rho L}{4}\Big(\frac{n\pi c}{L}\Big)^2\big(C_n^2+D_n^2\big)\qquad\text{(SymPy ✔)}.$$

This is **independent of $t$**, and the total energy is the sum of the $E_n$. So the normal modes **never exchange energy**.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]] · Next: [[MATH2048 PDE3 - The Heat Equation]]
- Practice: [[MATH2048 Problem Sheets 6-7 Solutions - PDEs]] · [[MATH2048 Past Paper Solutions]] (2025/26 A2: damped wave)

## Sources
- Lectures 15–16; Lecture Notes §5.4. Coefficients verified in SymPy; the series were reconstructed numerically.
