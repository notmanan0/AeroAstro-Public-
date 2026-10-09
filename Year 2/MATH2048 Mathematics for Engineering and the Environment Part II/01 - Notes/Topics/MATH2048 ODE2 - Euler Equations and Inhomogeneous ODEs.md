---
title: "MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 1: Ordinary Differential Equations"
order: 2
tags:
  - math2048
  - odes
  - euler-equation
  - undetermined-coefficients
aliases: ["MATH2048 Lecture 2", "Cauchy-Euler equations", "Particular integral"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]"]
next_topics: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
key_concepts: ["[[Euler-Cauchy Equation]]", "[[Method of Undetermined Coefficients]]", "[[Resonance]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.1.1–1.1.2)"]
---

# MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs

> [!abstract] Summary
> This lecture covers two extensions of ODE1.
> - **Euler equations** $ax^2y''+bxy'+cy=0$ have variable coefficients, but each derivative carries a matching power of $x$. The ansatz $y=x^n$ gives a quadratic in $n$. For repeated or complex roots, the substitution $t=\ln x$ converts the equation into a constant-coefficient ODE.
> - **Inhomogeneous** ODEs have general solution $y=\underbrace{c_1y_1+c_2y_2}_{\text{complementary function}}+\underbrace{y_p}_{\text{particular integral}}$, where $y_p$ is found by the **method of undetermined coefficients**. If the guess clashes with the complementary function, multiply it by $x$ (and by $x$ again if it still clashes).

## Key Concepts
- [[Euler-Cauchy Equation]] · [[Method of Undetermined Coefficients]] · [[Resonance]] · [[Auxiliary Equation]]

---

## 1. Euler equations

$$
ax^2y''+bxy'+cy=0\qquad(x>0,\ a,b,c\text{ constant})
$$

**Ansatz** $y=x^n$: then $y'=nx^{n-1}=\tfrac nx y$ and $y''=n(n-1)x^{n-2}=\tfrac{n(n-1)}{x^2}y$. Each derivative brings a factor $1/x$, and the $x$, $x^2$ in the ODE cancel it. So

$$
\boxed{an(n-1)+bn+c=0\iff an^2+(b-a)n+c=0}
$$

> [!warning] The classic slip
> The coefficient of $n$ is $(b-a)$, not $b$. It is safest to always write $n(n-1)$ explicitly first.

| Roots of $an^2+(b-a)n+c=0$ | General solution |
|---|---|
| real distinct $n_1,n_2$ | $y=c_1x^{n_1}+c_2x^{n_2}$ |
| real repeated $n$ | $y=x^n(c_1+c_2\ln x)$ |
| complex $\alpha\pm j\beta$ | $y=x^\alpha\big[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\big]$ |

### Derivation: why $t=\ln x$ works
Let $t=\ln x$, so $x=e^t$ and $\dfrac{dt}{dx}=\dfrac1x$. Write $\dot y=dy/dt$.

**First derivative** (chain rule):

$$
y'=\frac{dy}{dx}=\frac{dy}{dt}\frac{dt}{dx}=\frac1x\,\dot y\quad\Longrightarrow\quad xy'=\dot y .
$$

**Second derivative**: apply the product rule to $\tfrac1x\cdot\dot y$, remembering that $\dot y$ depends on $x$ through $t$:

$$
y''=\frac{d}{dx}\Big(\frac1x\dot y\Big)=-\frac1{x^2}\dot y+\frac1x\frac{d\dot y}{dt}\frac{dt}{dx}=-\frac1{x^2}\dot y+\frac1{x^2}\ddot y\quad\Longrightarrow\quad x^2y''=\ddot y-\dot y .
$$

**Substitute** into $ax^2y''+bxy'+cy=0$:

$$
a(\ddot y-\dot y)+b\dot y+cy=0\quad\Longrightarrow\quad \boxed{a\ddot y+(b-a)\dot y+cy=0}
$$

This is a constant-coefficient ODE in $t$. Its auxiliary equation $a\lambda^2+(b-a)\lambda+c=0$ is **exactly** the Euler indicial equation with $\lambda=n$. That is why the table above works: $e^{nt}=(e^t)^n=x^n$, $te^{nt}=x^n\ln x$ and $e^{\alpha t}\cos\beta t=x^\alpha\cos(\beta\ln x)$. Solve it in $t$ using [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]], then substitute back $e^{nt}=x^n$ and $t=\ln x$.

> [!warning] Don't stop at $y(t)$
> The question wants $y(x)$, so always convert back.

> [!example] Pulsating star (L2): $r^2X''+2rX'-\ell(\ell+1)X=0$
> Here $a=1$, $b=2$, $c=-\ell(\ell+1)$, so $n^2+n-\ell(\ell+1)=0$, which factorises as $(n-\ell)(n+\ell+1)=0$. The roots are distinct:
>
> $$X(r)=c_1r^\ell+\frac{c_2}{r^{\ell+1}}.$$
>
> The same pair of powers returns for Laplace's equation in polar coordinates (Block 4, PDEs).

> [!example] Complex roots, full working: $x^2y''+xy'+4y=0$
> **Indicial**: $n(n-1)+n+4=n^2+4=0$, so $n=\pm2j$ ($\alpha=0$, $\beta=2$).
> **In $t$**: $a=1$ and $b-a=0$, so $\ddot y+4y=0$ and $y=c_1\cos2t+c_2\sin2t$.
> **Back to $x$**: $y=c_1\cos(2\ln x)+c_2\sin(2\ln x)$.
> **Check** $y_1=\cos(2\ln x)$: $y_1'=-\tfrac2x\sin(2\ln x)$ and $y_1''=\tfrac2{x^2}\sin(2\ln x)-\tfrac4{x^2}\cos(2\ln x)$. Then $x^2y_1''+xy_1'+4y_1=2\sin-4\cos-2\sin+4\cos=0$ ✔.

> [!example] Repeated root (L2): $x^2y''+3xy'+y=0$
> $n(n-1)+3n+1=(n+1)^2=0$, so $n=-1$ is repeated. In $t$: $\ddot y+2\dot y+y=0$, so $y=(c_1+c_2t)e^{-t}$. Converting back,
>
> $$y=\frac{c_1+c_2\ln x}{x}.$$

## 2. Inhomogeneous ODEs: CF + PI
For $y''+p y'+q y=r(x)$ (the coefficient of $y''$ must be 1 in standard form):
1. Solve the **homogeneous** problem to get the complementary function (CF) $c_1y_1+c_2y_2$.
2. Find **any** particular integral (PI) $y_p$ that satisfies the full equation.
3. The general solution is $y=c_1y_1+c_2y_2+y_p$. **Only now** apply initial or boundary conditions.

**Proof that CF + PI is the *general* solution.** Let $L[y]=y''+py'+qy$. $L$ is linear: $L[\alpha u+\beta v]=\alpha L[u]+\beta L[v]$. Take any solution $y$ of $L[y]=r$ and let $\tilde y=y-y_p$. Then

$$
L[\tilde y]=L[y]-L[y_p]=r-r=0,
$$

so $\tilde y$ solves the homogeneous equation and must equal $c_1y_1+c_2y_2$. Hence **every** solution has the form $y=c_1y_1+c_2y_2+y_p$, and no solution is missed. It also follows that *which* PI you find doesn't matter: two PIs differ by a CF, which is absorbed into $c_1,c_2$.

### Method of undetermined coefficients (constant coefficients only)
| Source $r(x)$ | Trial $y_p$ |
|---|---|
| polynomial of degree $n$ | general polynomial of degree $n$: $A_nx^n+\dots+A_0$ |
| $e^{kx}$ | $Ce^{kx}$ |
| $\sin\omega x$ or $\cos\omega x$ | $C\sin\omega x+D\cos\omega x$ (always **both**) |
| $e^{kx}\sin\omega x$ or $e^{kx}\cos\omega x$ | $e^{kx}(C\sin\omega x+D\cos\omega x)$ |
| $x^ne^{kx}$ | $(A_nx^n+\dots+A_0)e^{kx}$ |
| sum of the above | sum of the trials |

> [!important] Clash rule
> If any term of the trial already appears in the CF, multiply the trial by $x^s$. Here $s$ is the **smallest** positive integer that removes every overlap. For a repeated root this is usually $s=2$.

> [!example] L2: $y''+4y'+4y=4x+25e^{3x}$
> - **CF**: $(\lambda+2)^2=0$, so $y_c=(c_1+c_2x)e^{-2x}$.
> - **Trial**: $y_p=Ax+B+Ce^{3x}$. There is no clash with the CF.
> - **Substitute**: $y_p''+4y_p'+4y_p=4Ax+(4A+4B)+(9+12+4)Ce^{3x}$.
> - **Match coefficients**: $4A=4$, $4A+4B=0$, $25C=25$, so $A=1$, $B=-1$, $C=1$.
>
> $$y=(c_1+c_2x)e^{-2x}+x-1+e^{3x}$$

> [!tip] Shortcut for exponential trials: $y_p=u(x)e^{kx}$
> If $y_p=u\,e^{kx}$, then $y_p'=(u'+ku)e^{kx}$ and $y_p''=(u''+2ku'+k^2u)e^{kx}$. Substituting into $y''+by'+cy$ gives
>
> $$\big[u''+(2k+b)u'+(k^2+bk+c)u\big]e^{kx}.$$
>
> - $k^2+bk+c$ is the auxiliary polynomial at $k$. It **vanishes** when $k$ is a CF root, which is exactly why a plain $Ce^{kx}$ fails.
> - $2k+b$ is its derivative at $k$. It also vanishes when $k$ is a **repeated** root, which is why you then need $x^2$.

> [!example] Full working: $y''+4y'+4y=e^{-2x}$
> Here $k=-2$ is a double root, so both brackets vanish and the equation reduces to $u''=1$. That gives $u=\tfrac12x^2$ (drop $c_1+c_2x$, which is the CF), so $y_p=\tfrac12x^2e^{-2x}$.
> **Direct check**: with $y_p=Cx^2e^{-2x}$,
> - $y_p'=C(2x-2x^2)e^{-2x}$
> - $y_p''=C(2-8x+4x^2)e^{-2x}$
>
> $$y_p''+4y_p'+4y_p=C\big[(2-8x+4x^2)+(8x-8x^2)+4x^2\big]e^{-2x}=2Ce^{-2x}$$
>
> So $2C=1$ and $C=\tfrac12$ ✔.

> [!example] Clashes with $y_c=(c_1+c_2x)e^{-2x}$ (L2 slide 14)
> - $r=e^{-2x}$: both $e^{-2x}$ and $xe^{-2x}$ are in the CF, so try $y_p=Cx^2e^{-2x}$. This gives $C=\tfrac12$ (worked above).
> - $r=xe^{-2x}$: the full trial would be $(Ax+B)e^{-2x}$, and multiplying by $x^2$ removes the clash. So try $y_p=(Ax^3+Bx^2)e^{-2x}$. This gives $A=\tfrac16$, $B=0$, i.e. $y_p=\tfrac16x^3e^{-2x}$. The slides simply try $Cx^3e^{-2x}$ directly.
> - $r=\log(\sin x^{3/4})$: there is no sensible guess, and undetermined coefficients fails. *Variation of parameters* would be needed (not examinable).

### Resonance (L3 last slide, Tacoma Narrows)
For $\ddot y+\omega_0^2y=\cos\omega_st$, the CF is $c_1\cos\omega_0t+c_2\sin\omega_0t$.
- If $\omega_s\neq\omega_0$, the trial $A\cos\omega_st+B\sin\omega_st$ works and the response stays **bounded**: $y_p=\dfrac{\cos\omega_st}{\omega_0^2-\omega_s^2}$.
  *Derivation*: with $y_p=A\cos\omega_st$ (no $\sin$ is needed because there is no $\dot y$ term), $\ddot y_p+\omega_0^2y_p=A(\omega_0^2-\omega_s^2)\cos\omega_st$. So $A=1/(\omega_0^2-\omega_s^2)$, which blows up as $\omega_s\to\omega_0$.
- If $\omega_s=\omega_0$, the trial clashes with the CF, so multiply by $t$: $y_p=t(A\cos\omega_0t+B\sin\omega_0t)$.
  - $\dot y_p=(A\cos+B\sin)+t\omega_0(-A\sin+B\cos)$
  - $\ddot y_p=2\omega_0(-A\sin+B\cos)-t\omega_0^2(A\cos+B\sin)$

  The $t$-terms cancel against $\omega_0^2y_p$, leaving $2\omega_0(-A\sin\omega_0t+B\cos\omega_0t)=\cos\omega_0t$. Hence $A=0$ and $B=1/(2\omega_0)$:

$$
y_p=\frac{t}{2\omega_0}\sin\omega_0t\qquad\text{(the amplitude grows linearly in time)}.
$$

![[m2048_ode_resonance.png|640]]

See [[Resonance]].

## 3. Not examinable (for reference)
Variation of parameters: $y_p=v_1y_1+v_2y_2$ with $v_1'=-ry_2/W$ and $v_2'=ry_1/W$. It works for any $r(x)$ but is slower.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · Next: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]
- Practice: [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] (PS1 Q2–Q3)

## Sources
- Lecture 2; Lecture 3 slide 18 (resonance); Appendix L1–2; Lecture Notes §1.1.1–1.1.2
