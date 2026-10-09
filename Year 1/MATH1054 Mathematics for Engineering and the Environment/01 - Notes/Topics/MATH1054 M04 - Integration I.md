---
title: "MATH1054 M04 - Integration I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 4
tags:
  - math1054
  - calculus
  - integration
  - numerical-integration
aliases: ["MATH1054 Module 4", "Integration I"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M09 - Integration II]]"]
key_concepts: ["[[Integration by Parts]]", "[[Trigonometric Integrals and Power Reduction]]", "[[Trapezium and Simpson's Rules]]"]
tutorial_sheets: ["[[MATH1054 M04 Solutions - Integration I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 4)", "02 - Sources/Modern Engineering Mathematics.pdf (§8.6–8.10)", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# MATH1054 M04 - Integration I

> [!abstract] Summary
> Integration reverses differentiation, and a definite integral is a **signed area**. This module covers:
> - the standard integrals, and linear substitution $\int f(ax+b)\,\mathrm dx$;
> - trigonometric identities that turn products and powers into sums;
> - **integration by parts**, including the "cyclic" case $\int e^{ax}\sin bx$;
> - the **trapezium** and **Simpson** rules for integrals you cannot do exactly.

## Key Concepts
- [[Integration by Parts]] · [[Trigonometric Integrals and Power Reduction]] · [[Trapezium and Simpson's Rules]] · Reference: [[Integration Formulae]]

---

## 1. Definite integral = signed area (James §8.6)
$$
\int_a^bf(x)\,\mathrm dx=F(b)-F(a),\qquad F'=f
$$
Area **below** the axis counts negative. For Ex 8.38, $\int_{-5}^5(x+3)\,\mathrm dx=32-2=30$. To find the *geometric* area, split the range at the zeros of $f$ and add the absolute values.

## 2. Standard integrals (James Fig. 8.56)
| $f(x)$ | $\int f\,\mathrm dx$ | $f(x)$ | $\int f\,\mathrm dx$ |
|---|---|---|---|
| $x^n$ ($n\neq-1$) | $\dfrac{x^{n+1}}{n+1}$ | $\sec^2x$ | $\tan x$ |
| $\dfrac1x$ | $\ln\lvert x\rvert$ | $\dfrac{1}{\sqrt{a^2-x^2}}$ | $\sin^{-1}\dfrac xa$ |
| $e^{ax}$ | $\dfrac1ae^{ax}$ | $\dfrac1{a^2+x^2}$ | $\dfrac1a\tan^{-1}\dfrac xa$ |
| $\sin ax$ | $-\dfrac1a\cos ax$ | $\dfrac{1}{\sqrt{x^2+a^2}}$ | $\sinh^{-1}\dfrac xa$ |
| $\cos ax$ | $\dfrac1a\sin ax$ | $\dfrac{1}{\sqrt{x^2-a^2}}$ | $\cosh^{-1}\dfrac xa$ |

**Linear substitution**: if $\int f(x)\,\mathrm dx=F(x)$, then $\int f(ax+b)\,\mathrm dx=\tfrac1aF(ax+b)$. For example, $\int\sqrt{5x+2}\,\mathrm dx=\tfrac2{15}(5x+2)^{3/2}$.

## 3. Trigonometric integrals (James §8.8.5)
The idea is to turn **powers** and **products** into **sums** of single sines and cosines, which integrate directly.

| Identity | Use |
|---|---|
| $\cos^2x=\tfrac12(1+\cos2x)$, $\sin^2x=\tfrac12(1-\cos2x)$ | even powers (apply repeatedly for $\cos^4x$) |
| $2\sin A\cos B=\sin(A+B)+\sin(A-B)$ | $\sin\cdot\cos$ products |
| $2\cos A\cos B=\cos(A+B)+\cos(A-B)$ | $\cos\cdot\cos$ |
| $2\sin A\sin B=\cos(A-B)-\cos(A+B)$ | $\sin\cdot\sin$ |

$$
\cos^4x=\tfrac38+\tfrac12\cos2x+\tfrac18\cos4x\quad\Longrightarrow\quad\int\cos^4x\,\mathrm dx=\tfrac38x+\tfrac14\sin2x+\tfrac1{32}\sin4x+C
$$

> [!note] Orthogonality preview
> $\int_0^\pi\sin5x\sin6x\,\mathrm dx=0$, while $\int_0^\pi\sin^25x\,\mathrm dx=\frac\pi2$. Different frequencies integrate to zero over a full half-period. This is the whole basis of Fourier series ([[Orthogonality of Trigonometric Functions]], MATH2048).

## 4. Integration by parts (James §8.8.4)
$$
\int u\frac{\mathrm dv}{\mathrm dx}\,\mathrm dx=uv-\int v\frac{\mathrm du}{\mathrm dx}\,\mathrm dx\qquad\text{(from the product rule)}
$$
**Choosing $u$ (LIATE)**: take $u$ from whichever comes first in **L**ogs, **I**nverse trig, **A**lgebraic, **T**rig, **E**xponential. The aim is to make $u$ simpler when differentiated.
- $\int x^3\ln x$: take $u=\ln x$, because the log disappears on differentiation.
- $\int x^2\cos x$: take $u=x^2$, and apply parts twice to reduce the power to zero.
- $\int e^{ax}\sin bx$: apply parts twice until the **original integral returns**, then solve the equation for $I$. This is the Fourier-coefficient workhorse.

$$
\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2},\qquad\int e^{ax}\sin bx\,\mathrm dx=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}
$$

## 5. Numerical integration (James §8.10)
With $n$ strips of width $h=(b-a)/n$ and ordinates $f_r=f(a+rh)$:

**Trapezium rule** (straight-line tops, error $\propto h^2$):
$$
T(h)=h\Big[\tfrac12(f_0+f_n)+f_1+f_2+\dots+f_{n-1}\Big]
$$
**Simpson's rule** ($n$ **even**, parabolic tops, error $\propto h^4$):
$$
S=\frac h3\Big[f_0+f_n+4(f_1+f_3+\dots+f_{n-1})+2(f_2+f_4+\dots+f_{n-2})\Big]
$$

![[m1054_trapezium_vs_simpson.png|640]]

- **Interval halving**: $T(h)=h\sum f_{\text{new odd}}+\tfrac12T(2h)$, which reuses every old point.
- **Error estimate**: $T(h)-I\approx\tfrac13\big[T(2h)-T(h)\big]$.
- **Richardson extrapolation**: $\tfrac13\big[4T(h)-T(2h)\big]$ removes the $h^2$ term, and **equals Simpson's rule**. This is the neat result behind Ex 142 and Exercise C.
- **Tabulated data** (Ex 8.74, the road cutting) can *only* be integrated numerically. Simpson's rule with 10 strips gives $7.3\times10^4$ m³.

## Method checklist
1. Can it be simplified first? Expand, divide out, or use a log law.
2. Is it standard, or standard after a linear substitution?
3. Is it a trig power or product? Use the identities in §3.
4. Is it a product of two unlike function types? Use parts (LIATE).
5. Is there no closed form, or only data? Use trapezium or Simpson, and estimate the error.
6. **Always check** an indefinite integral by differentiating it back.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M04 Solutions - Integration I]]
- Next: [[MATH1054 M09 - Integration II]] (substitution, applications) → [[MATH1054 M10 - Integration III]] (partial fractions, improper integrals) → [[MATH1054 M11 - Integration IV]] (multiple integrals)

## Sources
- MATH1054 Module Booklet, Module 4; James §8.6–8.10; [[Integration Formulae]]
