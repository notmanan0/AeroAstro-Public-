---
title: "MATH2048 Problem Sheets 1-2 Solutions - ODEs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: tutorial
stream: "Block 1: Ordinary Differential Equations"
tags:
  - math2048
  - tutorial-solutions
  - odes
sheet: "Problem Sheet 1 (Second Order Equations) + Problem Sheet 2 Q1–3 (Boundary Value Problems)"
theory_notes: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]", "[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]", "[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
key_concepts: ["[[Auxiliary Equation]]", "[[Euler-Cauchy Equation]]", "[[Method of Undetermined Coefficients]]", "[[Boundary Value Problems]]", "[[ODE Eigenvalue Problems]]"]
status: complete
sources: ["02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 1.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 2.pdf"]
---

# MATH2048 Problem Sheets 1-2 Solutions - ODEs

> [!abstract] Sheet Info
> PS1 (all), plus PS2 Q1–3. PS2's Fourier-series page is solved in Block 2. The sheets have no printed answers, so every answer here was checked with SymPy `dsolve`. Every step is shown, as the exam requires ("show and explain your working").

## Theory Links
- [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]] · [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]

---

# Problem Sheet 1: Second-order equations

## Q1: Constant coefficients
### (a) $y''-3y'+2y=0$
The auxiliary equation $\lambda^2-3\lambda+2=(\lambda-1)(\lambda-2)=0$ gives $\lambda=1,2$ (real, distinct).
$$y=c_1e^{x}+c_2e^{2x}$$

### (b) $y''+4y'+13y=0$
$\lambda=\dfrac{-4\pm\sqrt{16-52}}{2}=\dfrac{-4\pm6j}{2}=-2\pm3j$ (complex; $\alpha=-2$, $\beta=3$).
$$y=e^{-2x}\big(c_1\cos3x+c_2\sin3x\big)$$

### (c) $y''-4y'+y=0$
$\lambda=\dfrac{4\pm\sqrt{16-4}}{2}=2\pm\sqrt3$ (real, distinct, irrational, which is fine).
$$y=c_1e^{(2+\sqrt3)x}+c_2e^{(2-\sqrt3)x}=e^{2x}\big(A\cosh\sqrt3x+B\sinh\sqrt3x\big)$$

### (d) $y''-3y'=0$
$\lambda(\lambda-3)=0$ gives $\lambda=0,3$. The root $\lambda=0$ gives the solution $e^{0x}=1$.
$$y=c_1+c_2e^{3x}$$

## Q2: Euler equations (ansatz $y=x^n$, so $n(n-1)$ from $x^2y''$ and $n$ from $xy'$)
### (a) $x^2y''-6y=0$
$n(n-1)-6=n^2-n-6=(n-3)(n+2)=0$ gives $n=3,-2$ (distinct).
$$y=c_1x^3+\frac{c_2}{x^2}$$
Check $x^3$: $x^2\cdot6x-6x^3=0$ ✔.

### (b) $x^2y''+3xy'+10y=0$
$n(n-1)+3n+10=n^2+2n+10=0$ gives $n=-1\pm3j$ (complex), so use $t=\ln x$.
With $a=1$, $b=3$, $c=10$, the transformed equation is $\ddot y+(b-a)\dot y+cy=\ddot y+2\dot y+10y=0$, with roots $-1\pm3j$:
$$y(t)=e^{-t}\big(c_1\cos3t+c_2\sin3t\big)\ \xrightarrow{\ t=\ln x\ }\ \boxed{y=\frac1x\Big[c_1\cos(3\ln x)+c_2\sin(3\ln x)\Big]}$$

### (c) $x^2y''+5xy'+4y=0$
$n(n-1)+5n+4=n^2+4n+4=(n+2)^2=0$ gives $n=-2$ (repeated), so use $t=\ln x$.
In $t$: $\ddot y+4\dot y+4y=0$, so $y=(c_1+c_2t)e^{-2t}$.
$$y=\frac{c_1+c_2\ln x}{x^2}$$

## Q3: Undetermined coefficients
### (a) $y''-2y'+y=4e^x$
- **CF**: $(\lambda-1)^2=0$, so $y_c=(c_1+c_2x)e^x$.
- **Trial**: $Ce^x$ and $Cxe^x$ both clash with the CF, so take $y_p=Cx^2e^x$.
- **Derivatives**: $y_p'=C(x^2+2x)e^x$ and $y_p''=C(x^2+4x+2)e^x$.
- **Substitute**: $C\big[(x^2+4x+2)-2(x^2+2x)+x^2\big]e^x=2Ce^x=4e^x$, so $C=2$.
$$y=(c_1+c_2x)e^x+2x^2e^x$$

### (b) $y''-2y'+2y=4e^x\sin x$
- **CF**: $\lambda^2-2\lambda+2=0$ gives $\lambda=1\pm j$, so $y_c=e^x(c_1\cos x+c_2\sin x)$.
- **Trial**: $e^x(A\cos x+B\sin x)$ *is* the CF (a clash), so multiply by $x$: $y_p=xe^x(A\cos x+B\sin x)$.
- **Neatest route**: substitute $y_p=u\,e^x$ ([[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs|ODE2 shortcut]]). With $k=1$, $b=-2$, $c=2$: $2k+b=0$ and $k^2+bk+c=1$. So the ODE for $u$ is
  $$u''+u=4\sin x.$$
- With $u=x(A\cos x+B\sin x)$: $u''=-2A\sin x+2B\cos x-x(A\cos x+B\sin x)$. So $u''+u=-2A\sin x+2B\cos x=4\sin x$, which gives $A=-2$, $B=0$.
$$y=e^x(c_1\cos x+c_2\sin x)-2x\,e^x\cos x$$

### (c) $y''-4y'+4y=xe^{2x}$
- **CF**: $(\lambda-2)^2=0$, so $y_c=(c_1+c_2x)e^{2x}$.
- **Trial**: the "natural" guess $(Ax+B)e^{2x}$ is *entirely* CF, so multiply by $x^2$: $y_p=(Ax^3+Bx^2)e^{2x}$.
- **With $y_p=ue^{2x}$**: $k=2$ is a double root, so both brackets vanish and $u''=x$. Hence $u=\tfrac{x^3}{6}$ (dropping the CF part), so $A=\tfrac16$ and $B=0$.
$$y=(c_1+c_2x)e^{2x}+\frac{x^3}{6}e^{2x}$$
- **Check**: with $u=x^3/6$, $u''=x$ ✔.

---

# Problem Sheet 2: Boundary value problems

## Q1: Initial value problems
### (a) $9y''-12y'+4y=0$, $y(0)=2$, $y'(0)=-1$
- $9\lambda^2-12\lambda+4=(3\lambda-2)^2=0$ gives $\lambda=\tfrac23$ (repeated), so $y=(c_1+c_2x)e^{2x/3}$.
- $y'=\big[c_2+\tfrac23(c_1+c_2x)\big]e^{2x/3}$.
- $y(0)=c_1=2$, and $y'(0)=c_2+\tfrac43=-1$, so $c_2=-\tfrac73$.
$$y=\Big(2-\frac{7x}{3}\Big)e^{2x/3}$$

### (b) $y''+4y'+3y=0$, $y(0)=2$, $y'(0)=-1$
- $(\lambda+1)(\lambda+3)=0$, so $y=c_1e^{-x}+c_2e^{-3x}$.
- $c_1+c_2=2$ and $-c_1-3c_2=-1$. Adding gives $-2c_2=1$, so $c_2=-\tfrac12$ and $c_1=\tfrac52$.
$$y=\tfrac52e^{-x}-\tfrac12e^{-3x}$$

### (c) $y''+4y'+5y=0$, $y(0)=1$, $y'(0)=0$
- $\lambda=-2\pm j$, so $y=e^{-2x}(c_1\cos x+c_2\sin x)$.
- $y'=e^{-2x}\big[(c_2-2c_1)\cos x-(c_1+2c_2)\sin x\big]$.
- $c_1=1$, and $c_2-2c_1=0$ gives $c_2=2$.
$$y=e^{-2x}(\cos x+2\sin x)$$

### (d) $y''+4y'+4y=0$, $y(-1)=2$, $y'(-1)=1$
**Trick**: when conditions are at $x_0\neq0$, write the solution in powers of $(x-x_0)$. Here $y=\big[A+B(x+1)\big]e^{-2(x+1)}$. This is still a valid general solution, because $e^{-2(x+1)}=e^{-2}e^{-2x}$.
- $y(-1)=A=2$.
- $y'=\big[B-2A-2B(x+1)\big]e^{-2(x+1)}$, so $y'(-1)=B-2A=1$ and $B=5$.
$$y=\big[2+5(x+1)\big]e^{-2(x+1)}=(5x+7)\,e^{-2x-2}$$

## Q2: $y''+\tfrac14y=1$. When do solutions exist?
**General solution.**
- **CF**: $\lambda^2+\tfrac14=0$ gives $\lambda=\pm\tfrac j2$, so $y_c=c_1\cos\frac x2+c_2\sin\frac x2$.
- **PI**: the source is a constant, so try $y_p=C$. Then $\tfrac14C=1$ and $C=4$.
$$y=c_1\cos\frac x2+c_2\sin\frac x2+4,\qquad y'=-\frac{c_1}2\sin\frac x2+\frac{c_2}2\cos\frac x2$$

Useful values: $\cos\frac\pi2=0$ and $\sin\frac\pi2=1$, so $y(\pi)=c_2+4$ and $y'(\pi)=-\tfrac{c_1}2$.

| | BCs | Equations | Result |
|---|---|---|---|
| (a) | $y(0)=0$, $y(\pi)=2$ | $c_1+4=0$, $c_2+4=2$ | **unique**: $y=4-4\cos\frac x2-2\sin\frac x2$ |
| (b) | $y'(0)=0$, $y'(\pi)=0$ | $\tfrac{c_2}2=0$, $-\tfrac{c_1}2=0$ | **unique**: $y=4$ |
| (c) | $y(0)=0$, $y'(\pi)=1$ | $c_1=-4$, $-\tfrac{c_1}2=1\Rightarrow c_1=-2$ | **no solution** (contradiction) |
| (d) | $y(0)+2y'(0)=0$, $y(\pi)-2y'(\pi)=0$ | $c_1+4+c_2=0$, $c_2+4+c_1=0$ | **infinitely many** (same equation twice) |

(d) in full: $c_2=-4-c_1$, so
$$y=4-4\sin\frac x2+c_1\Big(\cos\frac x2-\sin\frac x2\Big),\qquad c_1\in\mathbb R .$$

> [!note] Fredholm alternative check
> - In (c), the **homogeneous** problem $y''+\tfrac14y=0$, $y(0)=0$, $y'(\pi)=0$ has the non-trivial solution $\sin\frac x2$. Its derivative $\tfrac12\cos\frac\pi2=0$ vanishes at $\pi$. So a unique solution was impossible, and the inhomogeneous data happened to be inconsistent.
> - In (d), $\cos\frac x2-\sin\frac x2$ solves the homogeneous problem: $1+2(-\tfrac12)=0$ at $x=0$ and $-1-2(-\tfrac12)=0$ at $x=\pi$. Here the data were consistent, which gives the family.
> - In (a) and (b), the homogeneous problem has only $y\equiv0$, so the solution is unique.

## Q3: Eigenvalue problems
### (a) $y''+\lambda y=0$, $y(0)=0$, $y(\pi)=0$
- $\lambda=-k^2<0$: $y=A\cosh kx+B\sinh kx$. $y(0)=A=0$, and $y(\pi)=B\sinh k\pi=0$ with $\sinh k\pi\neq0$, so $B=0$. Trivial.
- $\lambda=0$: $y=c_1x+c_2$. $c_2=0$ and $c_1\pi=0$. Trivial.
- $\lambda=k^2>0$: $y=c_1\sin kx+c_2\cos kx$. $c_2=0$, and $c_1\sin k\pi=0$ with $c_1\neq0$, so $k=n$.
$$\lambda_n=n^2,\qquad y_n=\sin nx,\qquad n=1,2,3,\dots$$

### (b) $y''+\lambda y=0$, $y(0)=0$, $y'(\pi)=0$
- $\lambda<0$: $A=0$, then $y'(\pi)=Bk\cosh k\pi=0$, so $B=0$. Trivial.
- $\lambda=0$: $c_2=0$, then $y'=c_1=0$. Trivial.
- $\lambda=k^2$: $c_2=0$, then $y'(\pi)=c_1k\cos k\pi=0$, so $k\pi=\big(n-\tfrac12\big)\pi$ and $k=n-\tfrac12$.
$$\lambda_n=\Big(n-\tfrac12\Big)^2=\frac{(2n-1)^2}{4},\qquad y_n=\sin\frac{(2n-1)x}{2},\qquad n=1,2,\dots$$
The first few are $\lambda=\tfrac14,\tfrac94,\tfrac{25}4$. Note that $\lambda_1=\tfrac14$ is exactly why Q2(c) failed: $y''+\tfrac14y$ sits on an eigenvalue of this BC pair.

## Sources
- Problem Sheets 1 and 2 (MATH2048, 2024-25). Answers verified in SymPy (`dsolve` with `ics`).
