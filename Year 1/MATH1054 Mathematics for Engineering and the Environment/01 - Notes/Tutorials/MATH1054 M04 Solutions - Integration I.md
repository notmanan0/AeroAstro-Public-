---
title: "MATH1054 M04 Solutions - Integration I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - integration
sheet: "Specimen Test 4 (booklet) + Module 04 work scheme: Examples 8.38–8.74; Exercises 104–106, 110–111, 119–120, 142; Booklet Exercises A–C"
theory_notes: ["[[MATH1054 M04 - Integration I]]"]
key_concepts: ["[[Integration by Parts]]", "[[Trigonometric Integrals and Power Reduction]]", "[[Trapezium and Simpson's Rules]]"]
status: complete
sources: ["tmp/md/module_04_integration_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§8.6–8.10)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 4)"]
---

# MATH1054 M04 Solutions - Integration I

> [!abstract] Sheet Info
> Every worked example and assigned exercise in Module 04. Every antiderivative was checked by differentiating back, or with SymPy `integrate`. The numerical answers were checked against `scipy.integrate.quad`.
>
> Indefinite integrals carry an arbitrary constant $+C$ throughout.

## Theory Links
- [[MATH1054 M04 - Integration I]] · [[Integration by Parts]] · [[Trigonometric Integrals and Power Reduction]] · [[Trapezium and Simpson's Rules]]

---

# Part A: Worked examples

## Example 8.38: $\int_{-5}^5(x+3)\,\mathrm dx$ as an area
The line $y=x+3$ crosses the axis at $x=-3$.
- On $[-5,-3]$ it lies **below** the axis. The triangle has base 2 and height 2, so its area is $2$, and it counts as $-2$.
- On $[-3,5]$ it lies **above** the axis. The triangle has base 8 and height 8, so it contributes $+32$.

$$\int_{-5}^5(x+3)\,\mathrm dx=32-2=\boxed{30}$$

Check: $\left[\tfrac12x^2+3x\right]_{-5}^5=(12.5+15)-(12.5-15)=30$ ✔.

## Example 8.43: Indefinite integrals
**(a)** Term by term:

$$\int\Big(6x^4+4x-\frac3x\Big)\mathrm dx=\boxed{\tfrac65x^5+2x^2-3\ln|x|+C}$$

**(b)** Expand first: $(2-x)\sqrt x=2x^{1/2}-x^{3/2}$, so

$$\int\big(2x^{1/2}-x^{3/2}\big)\mathrm dx=\boxed{\tfrac43x^{3/2}-\tfrac25x^{5/2}+C}$$

**(c)** For a linear inner function, $\int(ax+b)^n\,\mathrm dx=\dfrac{(ax+b)^{n+1}}{a(n+1)}$. Here $a=5$ and $n=\tfrac12$:

$$\int(5x+2)^{1/2}\,\mathrm dx=\frac{(5x+2)^{3/2}}{5\cdot\frac32}=\boxed{\tfrac2{15}(5x+2)^{3/2}+C}$$

**(d)** $\dfrac{x+1}x=1+\dfrac1x$, so the integral is $\boxed{x+\ln|x|+C}$.

## Example 8.44: Definite integrals
**(a)**

$$\int_1^2(x^4+6x^2-4)\,\mathrm dx=\Big[\tfrac{x^5}5+2x^3-4x\Big]_1^2=\big(\tfrac{32}5+16-8\big)-\big(\tfrac15+2-4\big)=\tfrac{72}5+\tfrac95=\boxed{\tfrac{81}5}$$

**(b)** Expand $\dfrac{(x^2-1)^2}{x^2}=x^2-2+x^{-2}$:

$$\Big[\tfrac{x^3}3-2x-\tfrac1x\Big]_1^2=\big(\tfrac83-4-\tfrac12\big)-\big(\tfrac13-2-1\big)=-\tfrac{11}6+\tfrac83=\boxed{\tfrac56}$$

**(c)**

$$\int_{-2}^44e^x\,\mathrm dx=4\big[e^x\big]_{-2}^4=4(e^4-e^{-2})=\boxed{217.85}\ \text{(2 d.p.)}$$

**(d)**

$$\int_0^{\pi/6}(\cos3x+2\sin3x)\,\mathrm dx=\Big[\tfrac13\sin3x-\tfrac23\cos3x\Big]_0^{\pi/6}=\big(\tfrac13-0\big)-\big(0-\tfrac23\big)=\boxed{1}$$

## Example 8.51: Integration by parts, $\int u\,\mathrm dv=uv-\int v\,\mathrm du$
**(a)** $\int x\ln x\,\mathrm dx$. Take $u=\ln x$ (the log is hard to integrate, easy to differentiate) and $\mathrm dv=x\,\mathrm dx$, so $v=\tfrac12x^2$:

$$=\tfrac12x^2\ln x-\int\tfrac12x^2\cdot\tfrac1x\,\mathrm dx=\boxed{\tfrac12x^2\ln x-\tfrac14x^2+C}$$

**(b)** $\int x^2\cos x\,\mathrm dx$. Integrate by parts twice, each time with the polynomial as $u$:

$$=x^2\sin x-\int2x\sin x\,\mathrm dx=x^2\sin x-\Big[-2x\cos x+\int2\cos x\,\mathrm dx\Big]$$

$$=\boxed{x^2\sin x+2x\cos x-2\sin x+C}$$

**(c)** $I=\int e^x\sin2x\,\mathrm dx$. Integrate by parts twice and the original integral **returns**:

$$I=e^x\sin2x-2\int e^x\cos2x\,\mathrm dx=e^x\sin2x-2\Big[e^x\cos2x+2\int e^x\sin2x\,\mathrm dx\Big]=e^x\sin2x-2e^x\cos2x-4I$$

$$5I=e^x(\sin2x-2\cos2x)\ \Rightarrow\ \boxed{I=\tfrac15e^x(\sin2x-2\cos2x)+C}$$

## Example 8.56: Trigonometric integrals
**(a)** Use the double-angle identity $\cos^2x=\tfrac12(1+\cos2x)$:

$$\int\cos^2x\,\mathrm dx=\boxed{\tfrac12x+\tfrac14\sin2x+C}$$

**(b)** Use the product-to-sum identity $\sin A\cos B=\tfrac12[\sin(A+B)+\sin(A-B)]$ with $A=5x+1$ and $B=x+2$:

$$\sin(5x+1)\cos(x+2)=\tfrac12\big[\sin(6x+3)+\sin(4x-1)\big]$$

$$\int=\boxed{-\tfrac1{12}\cos(6x+3)-\tfrac18\cos(4x-1)+C}$$

## Example 8.72: $\int_1^2\frac{\mathrm dx}x$ by the trapezium rule, to 5 d.p.
The trapezium rule with $n$ strips of width $h$ is

$$T(h)=h\big[\tfrac12(f_0+f_n)+f_1+\dots+f_{n-1}\big].$$

Interval halving reuses the old points: $T(h)=h(f_1+f_3+\dots+f_{n-1})+\tfrac12T(2h)$.

| $n$ | $h$ | $T(h)$ | error $T-\ln2$ | error estimate $\tfrac13[T(2h)-T(h)]$ |
|---|---|---|---|---|
| 1 | 1 | 0.750000 | 0.05685 | |
| 2 | 0.5 | 0.708333 | 0.01519 | 0.01389 |
| 4 | 0.25 | 0.697024 | 0.00388 | 0.00377 |
| 8 | 0.125 | 0.694122 | 0.00098 | 0.00097 |
| 16 | 0.0625 | 0.693391 | 0.00024 | 0.00024 |
| 32 | 0.03125 | 0.693208 | 0.00006 | |
| 64 | | 0.693162 | 0.000015 | |
| 128 | | 0.693151 | 0.000004 | |

Halving $h$ cuts the error by about 4, so the error is $\propto h^2$. The plain trapezium rule needs about $n=128$ strips before the error drops below $5\times10^{-6}$. That gives $0.69315$ to 5 d.p.

**Richardson extrapolation** removes the $h^2$ error term directly: $R=\tfrac13\big[4T(h)-T(2h)\big]$.
- From $T(0.125)$ and $T(0.0625)$: $R=0.6931477$.
- Applying the same idea again, $\tfrac1{15}(16R_h-R_{2h})$, gives $0.6931472$.

$$\int_1^2\frac{\mathrm dx}{x}=\boxed{0.69315}\ \text{(5 d.p.)}=\ln2\ ✔$$

## Example 8.74: Earth removed for a road cutting
**Data** (Fig. 8.77/8.80): heights $h$ of the ground above the datum PQ every 200 m over 2 km.

**Cross-section.** The cutting is 10 m wide at road level. Its sides slope at 2 horizontal to 1 vertical, so the top width is $10+4h$. The trapezium area is

$$A=\tfrac12\big[10+(10+4h)\big]h=(2h+10)h.$$

For an embankment ($h<0$), the same shape is filled in, so it counts negative: $A=-(2|h|+10)|h|$.

| $x$ (m) | 0 | 200 | 400 | 600 | 800 | 1000 | 1200 | 1400 | 1600 | 1800 | 2000 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $h$ (m) | 0 | 3.0 | 7.0 | 6.3 | 1.3 | −2.6 | −1.3 | 1.7 | 2.8 | −0.5 | 0 |
| $A$ (m²) | 0 | 48.0 | 168.0 | 142.4 | 16.4 | −39.5 | −16.4 | 22.8 | 43.7 | −5.5 | 0 |

**Volume** $V=\int_0^{2000}A(x)\,\mathrm dx$. Use Simpson's rule with 10 strips and $h=200$:
- odd ordinates: $48+142.4-39.5+22.8-5.5=168.2$
- even ordinates: $168+16.4-16.4+43.7=211.7$

$$V\approx\frac{200}{3}\big[0+0+4(168.2)+2(211.7)\big]=\frac{200}3(1096.2)=73\,080\ \text{m}^3\approx\boxed{7.3\times10^4\ \text{m}^3}$$

For comparison, the trapezium rule gives $200\sum A_{\text{interior}}=75\,980\ \text{m}^3$. The data are only good to about 2 s.f., so quote $7\times10^4$ to $7.3\times10^4$ m³.

---

# Part B: Assigned exercises

## Exercise 104 (p.645)
| | $f(x)$ | $\int f\,\mathrm dx$ |
|---|---|---|
| (a) | $3x^{2/3}$ | $3\cdot\frac{x^{5/3}}{5/3}=\tfrac95x^{5/3}+C$ |
| (b) | $\sqrt{2x}=\sqrt2\,x^{1/2}$ | $\tfrac{2\sqrt2}{3}x^{3/2}+C$ |
| (c) | $2x^3-2x^2+\tfrac1x-2$ | $\tfrac12x^4-\tfrac23x^3+\ln\lvert x\rvert-2x+C$ |
| (d) | $2e^x+3\cos2x$ | $2e^x+\tfrac32\sin2x+C$ |
| (f) | $(2x+1)^3$ | $\dfrac{(2x+1)^4}{2\cdot4}=\tfrac18(2x+1)^4+C$ |

## Exercise 105(c), 106(b) (p.645)
**105(c)**

$$\int_1^2\Big(x^{3/2}-\frac1{x^2}\Big)\mathrm dx=\Big[\tfrac25x^{5/2}+\tfrac1x\Big]_1^2=\Big(\tfrac25\cdot4\sqrt2+\tfrac12\Big)-\Big(\tfrac25+1\Big)=\boxed{\tfrac{8\sqrt2}5-\tfrac9{10}\approx1.3627}$$

**106(b)**

$$\int(x+1)^{-1/3}\,\mathrm dx=\frac{(x+1)^{2/3}}{2/3}=\boxed{\tfrac32(x+1)^{2/3}+C}$$

## Exercises 119(b), 120 (p.656): Product-to-sum
**119(b)** $\cos A\cos B=\tfrac12[\cos(A+B)+\cos(A-B)]$, so $\cos7x\cos5x=\tfrac12(\cos12x+\cos2x)$:

$$\int\cos7x\cos5x\,\mathrm dx=\boxed{\tfrac1{24}\sin12x+\tfrac14\sin2x+C}$$

**120(a)** $\sin A\sin B=\tfrac12[\cos(A-B)-\cos(A+B)]$, so $\sin5x\sin6x=\tfrac12(\cos x-\cos11x)$:

$$\int_0^\pi=\tfrac12\Big[\sin x-\tfrac1{11}\sin11x\Big]_0^\pi=\boxed{0}$$

This is an instance of **orthogonality**: $\int_0^\pi\sin mx\sin nx\,\mathrm dx=0$ for $m\neq n$. It is the foundation of Fourier series in MATH2048 ([[Orthogonality of Trigonometric Functions]]).

**120(b)** $\sin^25x=\tfrac12(1-\cos10x)$, so

$$\int_0^\pi\sin^25x\,\mathrm dx=\tfrac12\Big[x-\tfrac1{10}\sin10x\Big]_0^\pi=\boxed{\tfrac\pi2}$$

## Booklet Exercise A: $\int\cos^4x\,\mathrm dx$
Reduce the power twice:

$$\cos^4x=\Big(\frac{1+\cos2x}2\Big)^2=\tfrac14\big(1+2\cos2x+\cos^22x\big)=\tfrac14\Big(1+2\cos2x+\tfrac{1+\cos4x}2\Big)=\tfrac38+\tfrac12\cos2x+\tfrac18\cos4x$$

$$\int\cos^4x\,\mathrm dx=\boxed{\tfrac38x+\tfrac14\sin2x+\tfrac1{32}\sin4x+C}$$

## Exercises 110, 111(a) (p.649): Integration by parts
**110(a)** $u=x$, $\mathrm dv=\sin x\,\mathrm dx$, so $v=-\cos x$:

$$\int x\sin x\,\mathrm dx=-x\cos x+\int\cos x\,\mathrm dx=\boxed{\sin x-x\cos x+C}$$

**110(b)** $u=x$, $v=\tfrac13e^{3x}$:

$$\int xe^{3x}\,\mathrm dx=\tfrac13xe^{3x}-\tfrac13\int e^{3x}\,\mathrm dx=\boxed{\tfrac19e^{3x}(3x-1)+C}$$

**110(c)** $u=\ln x$, $v=\tfrac14x^4$:

$$\int x^3\ln x\,\mathrm dx=\tfrac14x^4\ln x-\int\tfrac14x^3\,\mathrm dx=\boxed{\tfrac1{16}x^4(4\ln x-1)+C}$$

**110(d) (harder)** $I=\int e^{-2x}\sin3x\,\mathrm dx$. Take $u=\sin3x$ and $\mathrm dv=e^{-2x}\,\mathrm dx$, so $v=-\tfrac12e^{-2x}$:

$$I=-\tfrac12e^{-2x}\sin3x+\tfrac32\int e^{-2x}\cos3x\,\mathrm dx$$

Integrate by parts again with $u=\cos3x$:

$$\int e^{-2x}\cos3x\,\mathrm dx=-\tfrac12e^{-2x}\cos3x-\tfrac32I$$

Substitute back:

$$I=-\tfrac12e^{-2x}\sin3x-\tfrac34e^{-2x}\cos3x-\tfrac94I\ \Rightarrow\ \tfrac{13}4I=-\tfrac14e^{-2x}(2\sin3x+3\cos3x)$$

$$\boxed{I=-\tfrac1{13}e^{-2x}(2\sin3x+3\cos3x)+C}$$

**111(a)**

$$\int_0^{\pi/2}x^2\sin x\,\mathrm dx=\big[-x^2\cos x\big]_0^{\pi/2}+2\int_0^{\pi/2}x\cos x\,\mathrm dx=0+2\big[x\sin x+\cos x\big]_0^{\pi/2}=2\big(\tfrac\pi2-1\big)=\boxed{\pi-2\approx1.1416}$$

## Booklet Exercise B (harder): $I=\int e^{2x}\cos x\,\mathrm dx$
Take $u=\cos x$ and $v=\tfrac12e^{2x}$:

$$I=\tfrac12e^{2x}\cos x+\tfrac12\int e^{2x}\sin x\,\mathrm dx$$

Integrate by parts again with $u=\sin x$:

$$\int e^{2x}\sin x\,\mathrm dx=\tfrac12e^{2x}\sin x-\tfrac12I$$

Substitute back:

$$I=\tfrac12e^{2x}\cos x+\tfrac14e^{2x}\sin x-\tfrac14I\ \Rightarrow\ \tfrac54I=\tfrac14e^{2x}(2\cos x+\sin x)$$

$$\boxed{I=\tfrac15e^{2x}(2\cos x+\sin x)+C}$$

**Check**: $\frac{\mathrm d}{\mathrm dx}\big[\tfrac15e^{2x}(2\cos x+\sin x)\big]=\tfrac15e^{2x}\big[4\cos x+2\sin x-2\sin x+\cos x\big]=e^{2x}\cos x$ ✔

> [!tip] Shortcut for $\int e^{ax}\cos bx$ and $\int e^{ax}\sin bx$
>
> $$\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2},\qquad \int e^{ax}\sin bx\,\mathrm dx=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2}$$
>
> The quickest derivation takes the real or imaginary part of $\int e^{(a+jb)x}\,\mathrm dx$.

## Exercise 142 (p.688): Simpson's rule, $\int_0^1\sqrt{1+x^3}\,\mathrm dx$ with $h=0.1$
| $x$ | 0 | 0.1 | 0.2 | 0.3 | 0.4 | 0.5 | 0.6 | 0.7 | 0.8 | 0.9 | 1.0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $f$ | 1.000000 | 1.000500 | 1.003992 | 1.013410 | 1.031504 | 1.060660 | 1.102724 | 1.158879 | 1.229634 | 1.314914 | 1.414214 |

- ends: $f_0+f_{10}=2.414214$
- odd ordinates: $f_1+f_3+f_5+f_7+f_9=5.548363$
- even ordinates: $f_2+f_4+f_6+f_8=4.367854$

$$S=\frac{h}{3}\big[(f_0+f_{10})+4\sum f_{\text{odd}}+2\sum f_{\text{even}}\big]=\frac{0.1}3\big[2.414214+22.193453+8.735708\big]=\boxed{1.111446}$$

## Booklet Exercise C: The same integral by the trapezium rule, $h=0.1$

$$T(0.1)=0.1\Big[\tfrac12(2.414214)+5.548363+4.367854\Big]=0.1\times11.123324=\boxed{1.112332}$$

> [!note] How accurate are these? (answering the textbook's remark)
> A single Simpson value gives no error estimate. But a *second* trapezium value does.
> - Using only the even points, $T(0.2)=0.2\big[1.207107+4.367854\big]=1.114992$.
> - The error estimate is $\tfrac13\big[T(0.2)-T(0.1)\big]=0.000887$. So the trapezium value is too big by about $9\times10^{-4}$.
> - Richardson gives $\tfrac13\big[4T(0.1)-T(0.2)\big]=1.111446$. This is **exactly the Simpson value**: Simpson's rule *is* extrapolated trapezium.
> - The true value is $1.1114480$ (numerical quadrature), so Simpson is good to about $2\times10^{-6}$.

---

# Part C: Specimen Test 4

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 4), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Indefinite integrals
| | $\int f\,\mathrm dx$ | Result |
|---|---|---|
| (i) | $\int x^{-2}\,\mathrm dx$ | $-\dfrac1x+C$ |
| (ii) | $\int\frac{\mathrm dx}{x+4}$ | $\ln\lvert x+4\rvert+C$ |
| (iii) | $\int e^{2x+1}\,\mathrm dx$ | $\tfrac12e^{2x+1}+C$ |
| (iv) | $\int\sin(1+4x)\,\mathrm dx$ | $-\tfrac14\cos(1+4x)+C$ |
| (v) | $\int\cos2x\cos4x\,\mathrm dx=\tfrac12\int(\cos6x+\cos2x)\,\mathrm dx$ | $\tfrac1{12}\sin6x+\tfrac14\sin2x+C$ |
| (vi) | $\int\frac{\mathrm dx}{9+x^2}$ | $\tfrac13\tan^{-1}\tfrac x3+C$ |

## Q2: Definite integrals
**(i)**

$$\int_0^1(x^4+2x^2+1)\,\mathrm dx=\tfrac15+\tfrac23+1=\boxed{\tfrac{28}{15}}$$

**(ii)**

$$\int_0^\pi\tfrac12(1-\cos2x)\,\mathrm dx=\boxed{\tfrac\pi2}$$

## Q3: $\int_1^2x\ln x\,\mathrm dx$
By parts, with $u=\ln x$ and $v=\tfrac12x^2$:

$$\Big[\tfrac12x^2\ln x-\tfrac14x^2\Big]_1^2=(2\ln2-1)-\big(0-\tfrac14\big)=\boxed{2\ln2-\tfrac34\approx0.6363}$$

## Q4: Simpson's rule for $\int_1^2\frac{\mathrm dx}x$ with $h=0.25$
| $x$ | 1.00 | 1.25 | 1.50 | 1.75 | 2.00 |
|---|---|---|---|---|---|
| $1/x$ | 1.000000 | 0.800000 | 0.666667 | 0.571429 | 0.500000 |

$$S=\frac{0.25}3\Big[1+0.5+4(0.8+0.571429)+2(0.666667)\Big]=\frac{0.25}{3}(8.319048)=\boxed{0.693254}$$

The exact value is $\ln2=0.693147$, so the error is only $1.1\times10^{-4}$ with just four strips.

## Sources
- Transcribed problem statements: `tmp/md/module_04_integration_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §8.6–8.10; MATH1054 Module Booklet, Module 4
