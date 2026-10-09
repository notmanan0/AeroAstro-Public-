---
title: "MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 1: Ordinary Differential Equations"
order: 1
tags:
  - math2048
  - odes
  - constant-coefficients
  - auxiliary-equation
aliases: ["MATH2048 Lecture 1", "Constant coefficient ODEs"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: []
next_topics: ["[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
key_concepts: ["[[Auxiliary Equation]]", "[[Damping Ratio and Natural Frequency]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture1_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix-solution ODE with repeated roots.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.1.1)"]
---

# MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients

> [!abstract] Summary
> Any linear second-order ODE can be written as $y''+p(x)y'+q(x)y=r(x)$. When $r\equiv0$ it is **homogeneous**, and the general solution is $y=c_1y_1+c_2y_2$ for two linearly independent solutions. With **constant coefficients** $ay''+by'+cy=0$, the ansatz $y=e^{\lambda x}$ reduces the ODE to the quadratic **auxiliary equation** $a\lambda^2+b\lambda+c=0$. The sign of $b^2-4ac$ then picks one of three solution forms. This is the engine behind every later PDE separation-of-variables question.

## Key Concepts
- [[Auxiliary Equation]] · [[Damping Ratio and Natural Frequency]] (SESA2027) · [[Characteristic Equation and Eigenvalues]] (SESA2027)

---

## 1. Standard form and linearity (Notes §1.1.1)
The general linear second-order ODE is $A(x)y''+B(x)y'+C(x)y+D(x)=0$. Dividing by $A$ gives the **standard form**

$$
y''+p(x)\,y'+q(x)\,y=r(x),\qquad p=\frac BA,\ q=\frac CA,\ r=-\frac DA .
$$

- $r\equiv0$: **homogeneous**. $r\not\equiv0$: **inhomogeneous**, and $r$ is the **source** or forcing term.
- For a homogeneous ODE, $y=c_1y_1(x)+c_2y_2(x)$, where $y_1,y_2$ are **linearly independent**: $c_1y_1+c_2y_2\equiv0\iff c_1=c_2=0$.
- *(Not examinable)* Independence can be tested with the Wronskian $W=y_1y_2'-y_1'y_2\neq0$. It satisfies $W'+pW=0$, so $W=Ke^{-\int p\,dx}$ is either zero everywhere or zero nowhere.

## 2. Constant coefficients: the auxiliary equation
For $ay''+by'+cy=0$, try $y=e^{\lambda x}$. Then $y'=\lambda y$ and $y''=\lambda^2y$, so

$$
(a\lambda^2+b\lambda+c)\,e^{\lambda x}=0\quad\Longrightarrow\quad a\lambda^2+b\lambda+c=0,\qquad \lambda=\frac{-b\pm\sqrt{b^2-4ac}}{2a}.
$$

| Discriminant | Roots | Independent solutions | General solution |
|---|---|---|---|
| $b^2-4ac>0$ | real, distinct $\lambda_1\neq\lambda_2$ | $e^{\lambda_1x},\ e^{\lambda_2x}$ | $y=c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $b^2-4ac=0$ | real, repeated $\lambda=-\tfrac{b}{2a}$ | $e^{\lambda x},\ x\,e^{\lambda x}$ | $y=(c_1+c_2x)e^{\lambda x}$ |
| $b^2-4ac<0$ | complex $\alpha\pm j\beta$ | $e^{\alpha x}\cos\beta x,\ e^{\alpha x}\sin\beta x$ | $y=e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |

> [!tip] Useful special cases
> - $y''+k^2y=0$ gives $\lambda=\pm jk$, so $y=c_1\cos kx+c_2\sin kx$ (simple harmonic motion).
> - $y''-k^2y=0$ gives $\lambda=\pm k$, so $y=c_1e^{kx}+c_2e^{-kx}$, or equivalently $y=A\cosh kx+B\sinh kx$. The cosh/sinh form is often easier for boundary conditions at $x=0$.
> - $y''=0$ gives $y=c_1x+c_2$.
> - If $c=0$, one root is $\lambda=0$, which gives a **constant** solution. For example, $y''-3y'=0$ gives $y=c_1+c_2e^{3x}$.

### Why $xe^{\lambda x}$ for a repeated root? (Appendix)
Try $y=v(x)e^{\lambda x}$ in $y''-2\lambda y'+\lambda^2y=0$, whose auxiliary equation is $(m-\lambda)^2=0$. Everything cancels except $v''e^{\lambda x}=0$, so $v=c_1+c_2x$. This is **reduction of order**. The general version, $y_2=y_1\int e^{-\int p\,dx}/y_1^2\,dx$, is not examinable.

**Direct check** (a quicker way to show it in an exam): the repeated root means $b^2=4ac$ and $\lambda=-b/2a$, i.e. $2a\lambda+b=0$. With $y=xe^{\lambda x}$:
- $y'=(1+\lambda x)e^{\lambda x}$
- $y''=(2\lambda+\lambda^2x)e^{\lambda x}$

$$
ay''+by'+cy=e^{\lambda x}\Big[x\underbrace{(a\lambda^2+b\lambda+c)}_{=0}+\underbrace{(2a\lambda+b)}_{=0}\Big]=0\ ✔
$$

Both brackets vanish **only** for a repeated root. For distinct roots $2a\lambda+b\neq0$, which is why $xe^{\lambda x}$ is then *not* a solution.

**Linear independence**: $c_1e^{\lambda x}+c_2xe^{\lambda x}\equiv0$ means $c_1+c_2x\equiv0$ for all $x$, which forces $c_1=c_2=0$. Equivalently, $W=y_1y_2'-y_1'y_2=e^{2\lambda x}\neq0$.

### Why cos/sin for complex roots? (Lecture 1 homework)
Start from $y=Ae^{(\alpha+j\beta)x}+Be^{(\alpha-j\beta)x}$ and apply Euler's formula $e^{\pm j\theta}=\cos\theta\pm j\sin\theta$:

$$
y=e^{\alpha x}\big[(A+B)\cos\beta x+j(A-B)\sin\beta x\big]=e^{\alpha x}\big[c_1\cos\beta x+c_2\sin\beta x\big].
$$

For a real solution, $B=\bar A$, so $c_1=A+B$ and $c_2=j(A-B)$ are both real.

## 3. Worked example: mass–spring–damper (L1 slides 10–12)
Newton's second law with friction gives $m\ddot y+2c\dot y+ky=0$, or $\ddot y+\dfrac{2c}{m}\dot y+\omega_0^2y=0$ with $\omega_0=\sqrt{k/m}$ the **natural frequency**. The roots are

$$
\lambda_{1,2}=-\frac cm\pm\sqrt{\frac{c^2}{m^2}-\omega_0^2}.
$$

- $c<m\omega_0$ (**under-damped**): complex roots, so $y=e^{-ct/m}\big[c_1\cos\omega t+c_2\sin\omega t\big]$ with $\omega=\sqrt{\omega_0^2-c^2/m^2}$. The oscillation decays inside the envelope $e^{-ct/m}$.
- $c=m\omega_0$ (**critical**): repeated root, so $y=(c_1+c_2t)e^{-ct/m}$. This is the fastest return with no oscillation.
- $c>m\omega_0$ (**over-damped**): two real negative roots, giving a sluggish return with no oscillation.

![[m2048_ode_damping_regimes.png|640]]

> [!note] Link to SESA2027
> Writing $c/m=\zeta\omega_0$ recovers the control-course form $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y=0$. The auxiliary equation here *is* the characteristic equation there, and its roots are the poles, $\sigma\pm j\omega_d$. See [[Damping Ratio and Natural Frequency]].

## 4. Method checklist
1. Put the ODE in the form $ay''+by'+cy=0$ and write down the auxiliary equation.
2. Solve the quadratic and classify the roots by the sign of $b^2-4ac$.
3. Write the matching general solution from the table.
4. Only then apply initial or boundary conditions to find $c_1,c_2$ (see [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]).

> [!example] One of each case
> | ODE | Auxiliary equation | Roots | $y$ |
> |---|---|---|---|
> | $y''-3y'+2y=0$ | $(\lambda-1)(\lambda-2)=0$ | $1,2$ | $c_1e^x+c_2e^{2x}$ |
> | $y''-6y'+9y=0$ | $(\lambda-3)^2=0$ | $3,3$ | $(c_1+c_2x)e^{3x}$ |
> | $y''+4y'+13y=0$ | $\lambda=\frac{-4\pm\sqrt{16-52}}2$ | $-2\pm3j$ | $e^{-2x}(c_1\cos3x+c_2\sin3x)$ |

> [!example] Full IVP: $y''+2y'+5y=0$, $y(0)=1$, $y'(0)=3$
> 1. **Auxiliary equation**: $\lambda^2+2\lambda+5=0$, so $\lambda=-1\pm2j$ ($\alpha=-1$, $\beta=2$).
> 2. **General solution**: $y=e^{-x}(c_1\cos2x+c_2\sin2x)$.
> 3. **Differentiate** (product rule): $y'=e^{-x}\big[(-c_1+2c_2)\cos2x+(-c_2-2c_1)\sin2x\big]$.
> 4. **Apply the conditions**: $y(0)=c_1=1$ and $y'(0)=-c_1+2c_2=3$, so $c_2=2$.
> 5. **Answer**: $y=e^{-x}(\cos2x+2\sin2x)$.
> 6. **Check**: $y(0)=1$ ✔ and $y'(0)=-1+4=3$ ✔.
>
> A common slip is to forget the $-e^{-x}$ part of the product rule in step 3.

More in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]].

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Next: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]
- Used in: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] and every separation-of-variables PDE (wave, heat, Laplace).

## Sources
- Lecture 1 (Dias / Richardson / Gan); Appendix L1–2; Appendix on repeated roots (K. Ashari); Lecture Notes §1.1.1
