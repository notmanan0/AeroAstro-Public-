---
title: "MATH1054 M09 - Integration II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 9
tags:
  - math1054
  - integration
  - substitution
  - applications-of-integration
aliases: ["MATH1054 Module 9", "Integration II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M07 - Functions]]"]
next_topics: ["[[MATH1054 M10 - Integration III]]"]
key_concepts: ["[[Integration by Substitution]]", "[[Centroids and Solids of Revolution]]", "[[RMS Value]]"]
tutorial_sheets: ["[[MATH1054 M09 Solutions - Integration II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 9)", "02 - Sources/Modern Engineering Mathematics.pdf (§8.8–8.9)", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# MATH1054 M09 - Integration II

> [!abstract] Summary
> **Substitution** is the chain rule run backwards. It is the most versatile integration technique:
> - spot $f'(x)\,g(f(x))$;
> - rationalise a root with $u=\sqrt{\cdots}$;
> - or use a trig or hyperbolic substitution to kill $\sqrt{a^2\pm x^2}$.
>
> The second half turns integrals into **engineering quantities**: area, centroid, volume of revolution, centre of gravity, mean and RMS values, arc length and surface area.

## Key Concepts
- [[Integration by Substitution]] · [[Centroids and Solids of Revolution]] · [[RMS Value]] · Reference sheet: [[Integration Formulae]]

---

## 1. Substitution (James §8.8.2–8.8.3)
If $u=g(x)$, then $\mathrm du=g'(x)\,\mathrm dx$, and
$$
\int f(g(x))g'(x)\,\mathrm dx=\int f(u)\,\mathrm du,\qquad\int_a^bf(g(x))g'(x)\,\mathrm dx=\int_{g(a)}^{g(b)}f(u)\,\mathrm du
$$
**Change the limits** in definite integrals (Ex 8.62, 115). Then there is no need to back-substitute.

| Pattern | Substitution | Example |
|---|---|---|
| $f'(x)\,[f(x)]^n$ | $u=f(x)$ | $\int x^2(1+x^3)^4\,\mathrm dx=\frac1{15}(1+x^3)^5$ |
| $\dfrac{f'(x)}{f(x)}$ | gives $\ln\lvert f\rvert$ directly | $\int\frac{\cos x-\sin x}{\sin x+\cos x}\,\mathrm dx=\ln\lvert\sin x+\cos x\rvert$ |
| $\sqrt{ax+b}$ in the integrand | $u=\sqrt{ax+b}$ | Ex 8.59, 8.62 |
| $\sqrt{a^2-x^2}$ | $x=a\sin\theta$ | $\int\sqrt{1-x^2}=\frac12\sin^{-1}x+\frac12x\sqrt{1-x^2}$ |
| $\sqrt{x^2-a^2}$ | $x=a\cosh u$ | $\int\frac{\mathrm dx}{\sqrt{x^2-1}}=\cosh^{-1}x$ |
| $\sqrt{x^2+a^2}$ or $a^2+x^2$ | $x=a\sinh u$ or $x=a\tan\theta$ | $\int\frac{\mathrm dx}{1+x^2}=\tan^{-1}x$ |
| $\sin^mx\cos^nx$ with $n$ odd | $u=\sin x$, keeping one $\cos x$ | Ex 122(b) |

## 2. Applications (James §8.9)
For the region under $y=f(x)\ge0$ on $[a,b]$:

| Quantity | Formula |
|---|---|
| Area | $A=\int_a^by\,\mathrm dx$ |
| Centroid of the area | $\bar x=\dfrac1A\int xy\,\mathrm dx$, $\bar y=\dfrac1{2A}\int y^2\,\mathrm dx$ |
| Volume about the $x$-axis | $V=\pi\int y^2\,\mathrm dx$ (discs) |
| Centre of gravity of the solid | $\bar x=\dfrac{\pi}{V}\int xy^2\,\mathrm dx$, $\bar y=\bar z=0$ |
| Mean value | $\bar f=\dfrac1{b-a}\int_a^bf\,\mathrm dx$ |
| RMS value | $f_{\text{rms}}=\sqrt{\dfrac1{b-a}\int_a^bf^2\,\mathrm dx}$ |
| Arc length | $L=\int_a^b\sqrt{1+y'^2}\,\mathrm dx$ |
| Surface of revolution | $S=2\pi\int_a^by\sqrt{1+y'^2}\,\mathrm dx$ |

- **Between two curves** $y_l\le y\le y_u$: the area strip has height $y_u-y_l$; the centroid uses $\tfrac12(y_u^2-y_l^2)$; the volume is a *washer*, $\pi(y_u^2-y_l^2)$ (Ex 135).
- **Why $\bar y=\frac1{2A}\int y^2$**: a vertical strip of height $y$ has its own centroid at height $y/2$, so its moment is $(y\,\mathrm dx)(y/2)$.
- **RMS of a sinusoid**: $I/\sqrt2$, which is the reason AC power uses RMS values (FEEG1004).

![[m1054_centroid_regions.png|800]]

## 3. Arc length and surface area
These usually produce $\int\sqrt{1+k^2u^2}\,\mathrm du$. Use the substitution $ku=\sinh t$, which gives
$$
\int\sqrt{1+k^2u^2}\,\mathrm du=\frac u2\sqrt{1+k^2u^2}+\frac1{2k}\sinh^{-1}(ku).
$$
This is where the hyperbolic functions of [[MATH1054 M07 - Functions|M07]] earn their keep (the suspension-bridge cable, Ex 8.69).

## Method checklist
1. Look for a function together with its derivative. If you find one, set $u$ to that function.
2. Roots of linear expressions: set $u$ to the root.
3. $\sqrt{a^2\pm x^2}$: use a trig or hyperbolic substitution.
4. For applications: sketch the region, identify the strip, write the integral, and **check the dimensions** (area in $L^2$, volume in $L^3$).
5. **Symmetry** often gives centroids for free (e.g. $\bar y=0$ for a solid of revolution).

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M09 Solutions - Integration II]]
- Prev: [[MATH1054 M04 - Integration I]] · Next: [[MATH1054 M10 - Integration III]]
- Related: FEEG1002 [[First Moment of Area]], [[Mass Moment of Inertia and Radius of Gyration]]

## Sources
- MATH1054 Module Booklet, Module 9; James §8.8–8.9; [[Integration Formulae]]
