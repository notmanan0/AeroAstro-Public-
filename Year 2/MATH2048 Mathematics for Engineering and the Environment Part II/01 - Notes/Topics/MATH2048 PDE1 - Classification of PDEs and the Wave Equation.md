---
title: "MATH2048 PDE1 - Classification of PDEs and the Wave Equation"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 4: Partial Differential Equations"
order: 10
tags:
  - math2048
  - pdes
  - wave-equation
  - classification
aliases: ["MATH2048 Lecture 14", "Hyperbolic parabolic elliptic", "D'Alembert solution"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
next_topics: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]"]
key_concepts: ["[[PDE Classification]]", "[[Wave Equation]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 6-7 Solutions - PDEs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture14_Hyperbolic1.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§5.1–5.3)"]
---

# MATH2048 PDE1 - Classification of PDEs and the Wave Equation

> [!abstract] Summary
> A second-order linear PDE $au_{xx}+2bu_{xy}+cu_{yy}+\dots=0$ falls into one of three types, decided by the sign of $b^2-ac$:
>
> | Type | Condition | Prototype | Behaviour |
> |---|---|---|---|
> | **hyperbolic** | $b^2-ac>0$ | wave equation | waves travelling at finite speed |
> | **parabolic** | $b^2-ac=0$ | heat equation | diffusion; information spreads at "infinite speed" |
> | **elliptic** | $b^2-ac<0$ | Laplace's equation | steady states; boundary-value problems |
>
> The wave equation $y_{tt}=c^2y_{xx}$ comes straight from Newton's second law applied to a short piece of taut string, with $c=\sqrt{T/\rho}$. On an infinite string its general solution is d'Alembert's $f(x+ct)+g(x-ct)$.

## Key Concepts
- [[PDE Classification]] · [[Wave Equation]] · [[Separation of Variables]]

---

## 1. Classification (L14)
$$
a\,u_{xx}+2b\,u_{xy}+c\,u_{yy}+d\,u_x+e\,u_y+f\,u=0 .
$$

> [!warning] The factor of 2
> The mixed-derivative coefficient is written as $2b$, so the discriminant is $b^2-ac$, not $B^2-4AC$. If the PDE is given as $Au_{xx}+Bu_{xy}+Cu_{yy}$, then $b=B/2$.

**The prototypes, written with $(x,y)\to(x,t)$:**
- **Wave**: $u_{tt}-c^2u_{xx}=0$. Here $a=-c^2$, $b=0$, $c_{\text{coef}}=1$, so $b^2-ac=c^2>0$: **hyperbolic**.
- **Heat**: $u_t-\kappa u_{xx}=0$. There is no $u_{tt}$, so $c_{\text{coef}}=0$. With $a=-\kappa$ and $b=0$, $b^2-ac=0$: **parabolic**.
- **Laplace**: $u_{xx}+u_{yy}=0$. Here $a=c=1$ and $b=0$, so $b^2-ac=-1<0$: **elliptic**.

**The type can change from region to region.** The **Tricomi equation** $yu_{xx}+u_{yy}=0$ (a model for transonic flow) has $b^2-ac=-y$:
- hyperbolic for $y<0$;
- elliptic for $y>0$;
- degenerate on the line $y=0$.

> [!note] The Tricomi sign convention
> The slides write it as $y\,u_{xx}=u_{yy}$, i.e. $a=y$ and $c=-1$. That gives $b^2-ac=y$: hyperbolic for $y>0$. Always compute the discriminant from the form actually given.

**Well-posedness: each type needs different data.**
- Hyperbolic equations need initial data $u$ **and** $u_t$ (second order in $t$).
- Parabolic equations need only $u$ at $t=0$ (first order in $t$).
- Elliptic equations need exactly one condition on **every** boundary.

## 2. Deriving the wave equation (L14)
Take a string with tension $T$ and mass per unit length $\rho$. Look at a small element $(x,x+\Delta x)$, whose ends make angles $\theta$ and $\theta'$ with the horizontal.

1. **Horizontal balance** (the string moves only vertically): $T_1\cos\theta=T_2\cos\theta'=T$.
2. **Vertical: Newton's second law**:
$$
\underbrace{\rho\,\Delta x}_{\text{mass}}\,\frac{\partial^2y}{\partial t^2}=T_2\sin\theta'-T_1\sin\theta=T(\tan\theta'-\tan\theta).
$$
   The second step divides each term by the matching horizontal balance.
3. **Small slopes**: $\tan\theta=\partial_xy\big|_x$ and $\tan\theta'=\partial_xy\big|_{x+\Delta x}$.
4. Divide by $\rho\,\Delta x$ and let $\Delta x\to0$:
$$
\frac{\partial^2y}{\partial t^2}=\frac T\rho\lim_{\Delta x\to0}\frac{y_x(x+\Delta x)-y_x(x)}{\Delta x}=\frac{T}{\rho}\frac{\partial^2y}{\partial x^2}\qquad\Longrightarrow\qquad \boxed{y_{tt}=c^2y_{xx},\quad c=\sqrt{T/\rho}}
$$

## 3. D'Alembert's solution (Notes §5.3)
Change to **characteristic coordinates** $\xi=x+ct$ and $\eta=x-ct$. By the chain rule,
$$
\partial_x=\partial_\xi+\partial_\eta,\qquad \partial_t=c(\partial_\xi-\partial_\eta).
$$
Substituting, $y_{tt}-c^2y_{xx}=c^2\big[(\partial_\xi-\partial_\eta)^2-(\partial_\xi+\partial_\eta)^2\big]y=-4c^2y_{\xi\eta}$. So the wave equation becomes
$$
\frac{\partial^2y}{\partial\xi\,\partial\eta}=0\quad\Longrightarrow\quad y=f(\xi)+g(\eta)=\boxed{f(x+ct)+g(x-ct)} .
$$

- $g(x-ct)$ keeps its shape and moves **right** at speed $c$: it is constant along the characteristic lines $x-ct=\text{const}$.
- $f(x+ct)$ moves **left** at speed $c$.

**Link to the separated solutions (PDE2)**: $\sin\frac{n\pi x}{L}\cos\frac{n\pi ct}{L}=\frac12\Big[\sin\frac{n\pi(x-ct)}{L}+\sin\frac{n\pi(x+ct)}{L}\Big]$. A standing wave is two travelling waves moving in opposite directions.

## 4. Extra results from the Lecture Notes (Ch. 5)
### Where the $b^2-ac$ test comes from (§5.1)
Change variables to $\xi=x+\beta y$ and $\eta=x+\delta y$, choosing $\beta$ and $\delta$ as the roots of
$$c\lambda^2+2b\lambda+a=0 .$$
The $u_{\xi\xi}$ and $u_{\eta\eta}$ terms then vanish, leaving the **canonical form** $\frac{4}{c}(ac-b^2)\,u_{\xi\eta}=G$. The type of the roots decides the type of the PDE:

| Roots $\beta,\delta$ | Type |
|---|---|
| real and distinct | hyperbolic |
| repeated | parabolic |
| complex conjugate | elliptic |

For the wave equation this is exactly d'Alembert's $\xi=x\pm ct$.

### Energy of a vibrating string (§5.2.2)
- Kinetic energy: $\mathrm{KE}=\int_0^L\tfrac12\rho\,y_t^2\,dx$.
- Potential energy: $\mathrm{PE}=T\int_0^L\big(\sqrt{1+y_x^2}-1\big)dx\approx\int_0^L\tfrac12T\,y_x^2\,dx$ for small slopes.
- Total:
$$E=\int_0^L\frac\rho2\big(y_t^2+c^2y_x^2\big)\,dx .$$

$E$ is conservative. **Proof**: $\dot E=\rho\int(y_ty_{tt}+c^2y_xy_{xt})\,dx$. Substitute $y_{tt}=c^2y_{xx}$ and integrate the second term by parts. What remains is $\rho c^2\big[y_xy_t\big]_0^L=0$, because $y_t=0$ at fixed ends.

### Harmonic travelling waves (§5.3.1)
$y=\mathrm{Re}\,Ae^{j\omega(t-x/c)}=|A|\cos\big(\omega(t-x/c)+\phi\big)$, with amplitude $|A|$, frequency $\omega$, phase $\phi$ and wavelength $2\pi c/\omega$.

### Reflection and transmission at a density jump (§5.3.2)
A string has $\rho_-$ for $x<0$ and $\rho_+$ for $x>0$, so the wave speeds are $c_\pm=\sqrt{T/\rho_\pm}$. Send in the wave $Ae^{j\omega(t-x/c_-)}$.

At $x=0$ two conditions hold:
- $y$ is continuous (the string does not break): $A+B=D$;
- $Ty_x$ is continuous (force balance): $\frac{-A+B}{c_-}=-\frac{D}{c_+}$.

Solving:
$$B=\frac{c_+-c_-}{c_++c_-}A\ \ (\text{reflected}),\qquad D=\frac{2c_+}{c_++c_-}A\ \ (\text{transmitted})\qquad\text{(SymPy ✔)}.$$

| Limit | Result | Meaning |
|---|---|---|
| $c_+=c_-$ | $B=0$, $D=A$ | no reflection |
| $\rho_+\to\infty$ ($c_+\to0$) | $B=-A$, $D=0$ | a rigid wall: inverted reflection |
| $\rho_+\to0$ | $B=A$, $D=2A$ | a massless (free) end |

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]] · Next: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]

## Sources
- Lecture 14; Lecture Notes §5.1–5.3
