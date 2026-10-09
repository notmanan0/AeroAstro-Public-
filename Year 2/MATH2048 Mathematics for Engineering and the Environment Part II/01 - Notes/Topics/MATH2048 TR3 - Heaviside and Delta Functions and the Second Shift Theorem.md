---
title: "MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 3: Fourier and Laplace Transforms"
order: 9
tags:
  - math2048
  - laplace-transform
  - heaviside
  - dirac-delta
aliases: ["MATH2048 Lecture 13", "Second shift theorem", "Impulse response"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]"]
next_topics: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]"]
key_concepts: ["[[Heaviside Step Function]]", "[[Dirac Delta Function]]", "[[Laplace Transform Properties and Proofs]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Appendix-Laplace Transform_additional slides.pdf"]
---

# MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem

> [!abstract] Summary
> **Switches** and **impulses** are where Laplace transforms really outperform the undetermined-coefficients method. The key results are
>
> $$\mathcal L[H(x-a)]=\frac{e^{-as}}{s},\qquad\mathcal L[\delta(x-a)]=e^{-as},\qquad \mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s)\quad\text{(second shift theorem)}.$$
>
> An $e^{-as}$ in $\tilde y(s)$ always means **"delay by $a$ and switch on at $a$"**. Every past paper's A1 is exactly this, with an $H$ or $\delta$ source.

## Key Concepts
- [[Heaviside Step Function]] · [[Dirac Delta Function]] · [[Laplace Transform Properties and Proofs]]

---

## 1. Heaviside step function

$$
H(x-a)=\begin{cases}0&x<a\\1&x>a\end{cases}
$$

| Construction | Meaning |
|---|---|
| $H(x+1)-H(x-1)$ | top-hat on $(-1,1)$ |
| $f(x)H(x-a)$ | $f$ switched **on** at $a$ |
| $f(x)[1-H(x-a)]$ | $f$ switched **off** at $a$ |
| $f(x)[H(x-a)-H(x-b)]$ | $f$ on only for $a<x<b$ |

**Transform** (for $a\geq0$, $\mathrm{Re}\,s>0$):

$$
\mathcal L[H(x-a)]=\int_0^a0\,dx+\int_a^\infty e^{-sx}dx=\Big[-\frac{e^{-sx}}{s}\Big]_a^\infty=\frac{e^{-as}}{s}.
$$

## 2. Second shift theorem. **Prove it** (2025/26 A1(a), 5 marks)

$$
\boxed{\mathcal L[H(x-a)f(x-a)]=e^{-as}\tilde f(s)}\qquad(a\geq0)
$$

**Proof.**

$$
\mathcal L[H(x-a)f(x-a)]=\int_0^\infty H(x-a)f(x-a)e^{-sx}dx=\int_a^\infty f(x-a)e^{-sx}dx .
$$

- The first step uses the definition of $\mathcal L$. $H(x-a)=0$ for $x<a$ and $1$ for $x>a$, so the integral starts at $x=a$.
- Substitute $\tau=x-a$, so $x=\tau+a$ and $dx=d\tau$. When $x=a$, $\tau=0$; when $x\to\infty$, $\tau\to\infty$.

$$
=\int_0^\infty f(\tau)e^{-s(\tau+a)}d\tau=e^{-as}\int_0^\infty f(\tau)e^{-s\tau}d\tau=e^{-as}\tilde f(s).\qquad\blacksquare
$$

**Alternative form**: $\mathcal L[f(x)H(x-a)]=e^{-as}\mathcal L[f(x+a)]$. This is proved the same way: after the substitution the integrand is $f(\tau+a)$.

![[m2048_tr_second_shift.png|620]]

> [!warning] Which form do you have?
> - $f(x-a)H(x-a)$: the **whole graph is delayed**. Use $e^{-as}\tilde f(s)$.
> - $f(x)H(x-a)$: the graph is **switched on unshifted**. Rewrite it as $f\big((x-a)+a\big)H(x-a)$, then use $e^{-as}\mathcal L[f(x+a)]$.
>
> Example (2023/24 A1): $e^xH(x-1)=e\cdot e^{x-1}H(x-1)$, so its transform is $e\cdot\dfrac{e^{-s}}{s-1}$. This is where the $e\,e^{-s}$ in the given answer comes from.

**Inversion rule**: $\mathcal L^{-1}[e^{-as}\tilde f(s)]=f(x-a)H(x-a)$.
1. Strip off the $e^{-as}$.
2. Invert the rest to get $f(x)$.
3. Replace $x$ by $x-a$ and multiply by $H(x-a)$.

## 3. Dirac delta
$\delta$ is a **generalised function** (a distribution), defined by what it does under an integral:

$$
\int_{-\infty}^{\infty}\delta(x-c)f(x)\,dx=f(c),\qquad \int_a^b\delta(x-c)f(x)\,dx=\begin{cases}f(c)&c\in(a,b)\\0&c\notin(a,b)\end{cases}
$$

Picture it as a rectangle of fixed area $1$ that gets narrower and taller. It models an impulse: a hammer blow that delivers finite momentum in zero time. Also $\delta=H'$.

**Transform** (for $a>0$):

$$
\mathcal L[\delta(x-a)]=\int_0^\infty\delta(x-a)e^{-sx}dx=e^{-as}.
$$

This needs $a$ to lie inside the integration range $(0,\infty)$, which is why $a>0$. The formula sheet takes $\mathcal L[\delta(x)]=1$ by convention.

**Useful identity**: $g(x)\delta(x-a)=g(a)\delta(x-a)$. For example, $\delta(x-2\pi)\cos x=\cos2\pi\,\delta(x-2\pi)=\delta(x-2\pi)$ (PS5 Q3h).

## 4. Worked examples (L13)
> [!example] Step input: $y''+y=H(x-1)$, $y(0)=0$, $y'(0)=1$
> 1. **Transform and solve**: $(s^2+1)\tilde y-1=\frac{e^{-s}}{s}$, so
>
>    $$\tilde y=\frac1{s^2+1}+\frac{e^{-s}}{s(s^2+1)} .$$
>
> 2. **Partial fractions**: $\frac1{s(s^2+1)}=\frac1s-\frac{s}{s^2+1}$, which is $\mathcal L[1-\cos x]$.
> 3. **Invert with the second shift theorem**:
>
>    $$y=\sin x+H(x-1)\big[1-\cos(x-1)\big]$$
>
> SymPy agrees ✔.

> [!example] Repeated hammer blows: $\ddot y+y=\sum_{n\geq0}\delta(t-n\pi)$, $y(0)=\dot y(0)=0$
> Transforming gives $(s^2+1)\tilde y=\sum_ne^{-n\pi s}$, so
>
> $$y=\sum_nH(t-n\pi)\sin(t-n\pi) .$$
>
> Since $\sin(t-n\pi)=(-1)^n\sin t$, the blows alternately add and cancel:
> - $y=\sin t$ on $(0,\pi)$;
> - $y=0$ on $(\pi,2\pi)$;
> - $y=\sin t$ on $(2\pi,3\pi)$, and so on.
>
> The blow at $t=\pi$ arrives exactly when the mass passes $y=0$ moving with velocity $-1$, and brings it to rest.

> [!example] Exam 2025/26 A1(b): $y''+2y'+2y=\delta(x-13)$, $y(0)=y'(0)=0$
> 1. **Transform and solve**: $(s^2+2s+2)\tilde y=e^{-13s}$, so
>
>    $$\tilde y=\frac{e^{-13s}}{(s+1)^2+1} .$$
>
> 2. **Invert the part without $e^{-13s}$**: $\mathcal L^{-1}\Big[\frac{1}{(s+1)^2+1}\Big]=e^{-x}\sin x$ (first shift theorem, from $\mathcal L[\sin x]=\frac1{s^2+1}$).
> 3. **Apply the second shift theorem** with $a=13$:
>
>    $$y=H(x-13)\,e^{-(x-13)}\sin(x-13)$$
>
> This is the **impulse response**: nothing happens until $x=13$, then a decaying oscillation. SymPy agrees ✔.

## 5. Extra results from the Lecture Notes (§4.5.2, §4.7.3)
- **$\delta$ as a limit.** $\delta(x)=\lim_{\epsilon\to0}D(x,\epsilon)$, where $D=1/\epsilon$ on $|x|\leq\epsilon/2$ and $0$ elsewhere. Every $D$ has $\int D\,dx=1$. The limit only makes sense **inside an integral**. $\delta$ can be thought of as $H'$ (made rigorous for suitable arguments).
- **Inverse forms of the shift theorems (4.23).**

$$\mathcal L^{-1}[\tilde f(s+a)]=e^{-ax}f(x),\qquad \mathcal L^{-1}[e^{-sa}\tilde f(s)]=H(x-a)f(x-a).$$

- **Laplace transforms turn PDEs into ODEs.** A transform acts on one variable only.
  - *Example*: the spherical wave equation $c^2y_{tt}=\frac1r(ry)_{rr}$, with $y=y_t=0$ at $t=0$. Transforming in $t$ gives $(r\tilde y)''-(s/c)^2(r\tilde y)=0$.
  - Solving: $r\tilde y=De^{sr/c}+Ee^{-sr/c}$. Regularity as $r\to\infty$ forces $D=0$.
  - The "constant" $E=E(s)$ is then fixed by transforming the boundary condition too. For $y_r(a,t)=g(t)$:

$$\tilde y=-\frac{a^2c\,\tilde g(s)}{r\,(as+c)}e^{s(a-r)/c} .$$

  SymPy ✔. The Lecture Notes text shows $a^2s+c$ in the denominator, but differentiating $E\,e^{-sr/c}/r$ at $r=a$ gives $-E\,e^{-sa/c}\frac{as+c}{ca^2}$, so the correct denominator is $as+c$.
  - The factor $e^{-s(r-a)/c}$ is a pure **delay** of $(r-a)/c$: the signal travels outward at speed $c$ (second shift theorem).

## Method summary for Heaviside and delta IVPs
1. Rewrite each source term in the form $g(x-a)H(x-a)$ **before** transforming. Use trig or exponential identities if needed.
2. Transform with the table and the shift theorems. Name each one you use (the exam asks you to "identify them explicitly").
3. Solve for $\tilde y$. Group the terms by their $e^{-as}$ factor.
4. Use partial fractions on each group, **ignoring** the $e^{-as}$.
5. Invert each group, then apply the delay $x\to x-a$ and the factor $H(x-a)$.
6. Check: $y(0)$ and $y'(0)$, and continuity at $x=a$. The solution is continuous at an $H$ source; at a $\delta$ source, $y'$ jumps.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]] · Next: [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]
- Practice: [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]] (PS5 Q3e–h, Q4) · [[MATH2048 Past Paper Solutions]]

## Sources
- Lecture 13; Laplace Appendix. All examples verified with SymPy `inverse_laplace_transform`.
