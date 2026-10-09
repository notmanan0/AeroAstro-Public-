---
title: "MATH1054 M03 Solutions - Differentiation I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - differentiation
sheet: "Specimen Test 3 (booklet) + Module 03 work scheme: Examples 8.1–8.27, 9.17–9.25; Exercises 1(c), 25–39, 60, 62, 26 (p.731), 39 (p.747); Booklet Example A"
theory_notes: ["[[MATH1054 M03 - Differentiation I]]"]
key_concepts: ["[[Derivative from First Principles]]", "[[Product, Quotient and Chain Rules]]", "[[Direct Substitution and Newton-Raphson]]", "[[Partial Derivatives]]"]
status: complete
sources: ["tmp/md/module_03_differentiation_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§8.2–8.4, §9.4.8, §9.6)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 3)"]
---

# MATH1054 M03 Solutions - Differentiation I

> [!abstract] Sheet Info
> This note covers every worked example and assigned exercise in the Module 03 work scheme (James, *Modern Engineering Mathematics* 6th ed.). Every derivative was checked with SymPy `diff`, and every Newton–Raphson root was checked against the exact roots.
>
> **Notation**: $f'(x)=\dfrac{\mathrm dy}{\mathrm dx}$, and $\ln$ is the natural log.

## Theory Links
- [[MATH1054 M03 - Differentiation I]] · [[Derivative from First Principles]] · [[Product, Quotient and Chain Rules]] · [[Direct Substitution and Newton-Raphson]] · [[Partial Derivatives]]

---

# Part A: Worked examples

## Example 8.1: Derivatives from the definition

$$f'(x)=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}$$

### (a) $f(x)=x^2$

$$\frac{(x+\Delta x)^2-x^2}{\Delta x}=\frac{2x\,\Delta x+(\Delta x)^2}{\Delta x}=2x+\Delta x\ \xrightarrow{\Delta x\to0}\ \boxed{f'(x)=2x}$$

### (b) $f(x)=\dfrac1x$

$$\frac{\frac1{x+\Delta x}-\frac1x}{\Delta x}=\frac{x-(x+\Delta x)}{x(x+\Delta x)\,\Delta x}=\frac{-1}{x(x+\Delta x)}\ \xrightarrow{\Delta x\to0}\ \boxed{f'(x)=-\frac1{x^2}}\quad(x\neq0)$$

### (c) $f(x)=mx+c$

$$\frac{m(x+\Delta x)+c-(mx+c)}{\Delta x}=\frac{m\,\Delta x}{\Delta x}=m\ \Rightarrow\ \boxed{f'(x)=m}$$

A straight line has constant slope, as expected.

## Example 8.2: $f(x)=25x-5x^2$
**(a) First principles**:

$$f(x+\Delta x)-f(x)=25\Delta x-5\big[(x+\Delta x)^2-x^2\big]=25\Delta x-10x\,\Delta x-5(\Delta x)^2$$

Dividing by $\Delta x$ gives $25-10x-5\Delta x$, so as $\Delta x\to 0$, $\boxed{f'(x)=25-10x}$.

**(b) Rate of change at $x=1$**: $f'(1)=25-10=\boxed{15}$.

**(c) Tangent at $(1,20)$**: the gradient is $m=15$. So $y-20=15(x-1)$, which gives $\boxed{y=15x+5}$.

**(d) Normal at $(1,20)$**: the gradient is $-1/m=-\tfrac1{15}$. So $y-20=-\tfrac1{15}(x-1)$, which gives $\boxed{15y+x=301}$ (or $y=\tfrac{301-x}{15}$).

## Example 8.9: Power rule $\frac{\mathrm d}{\mathrm dx}x^r=rx^{r-1}$
| $f(x)$ | rewrite | $f'(x)$ |
|---|---|---|
| (a) $\sqrt x$ | $x^{1/2}$ | $\tfrac12x^{-1/2}=\dfrac1{2\sqrt x}$ |
| (b) $\dfrac1{x^5}$ | $x^{-5}$ | $-5x^{-6}=-\dfrac5{x^6}$ |
| (c) $\dfrac1{\sqrt[3]x}$ | $x^{-1/3}$ | $-\tfrac13x^{-4/3}=-\dfrac1{3x\sqrt[3]x}$ |

## Example 8.10: Sum, product and quotient rules
**(a)** $\dfrac{\mathrm d}{\mathrm dx}(8x^4-4x^2)=\boxed{32x^3-8x}$.

**(b)** Product rule $(uv)'=u'v+uv'$, with $u=2x^2+5$ and $v=x^2+3x+1$:

$$f'=4x(x^2+3x+1)+(2x^2+5)(2x+3)=4x^3+12x^2+4x+4x^3+6x^2+10x+15=\boxed{8x^3+18x^2+14x+15}$$

**(c)** Expand first: $4x^7(x^2-3x)=4x^9-12x^8$, so $f'=36x^8-96x^7=\boxed{12x^7(3x-8)}$.

**(d)** $(x+1)x^{1/2}=x^{3/2}+x^{1/2}$, so

$$f'=\tfrac32x^{1/2}+\tfrac12x^{-1/2}=\boxed{\frac{3x+1}{2\sqrt x}}$$

**(e)** Quotient rule $\left(\frac uv\right)'=\dfrac{u'v-uv'}{v^2}$, with $u=\sqrt x$ and $v=x+1$:

$$f'=\frac{\frac1{2\sqrt x}(x+1)-\sqrt x}{(x+1)^2}=\frac{(x+1)-2x}{2\sqrt x(x+1)^2}=\boxed{\frac{1-x}{2\sqrt x\,(x+1)^2}}$$

**(f)** $u=x^3+2x+1$, $u'=3x^2+2$; $v=x^2+1$, $v'=2x$:

$$f'=\frac{(3x^2+2)(x^2+1)-2x(x^3+2x+1)}{(x^2+1)^2}=\frac{3x^4+5x^2+2-2x^4-4x^2-2x}{(x^2+1)^2}=\boxed{\frac{x^4+x^2-2x+2}{(x^2+1)^2}}$$

## Example 8.11
$y=2x^4-2x^3-x^2+3x-2$, so $\boxed{\dfrac{\mathrm dy}{\mathrm dx}=8x^3-6x^2-2x+3}$.

## Example 8.12: Velocity and acceleration
$s=2t^3-1.5t^2-6t+12$.
- $v=\dfrac{\mathrm ds}{\mathrm dt}=6t^2-3t-6$, so $v(2)=24-6-6=\boxed{12\ \text{m s}^{-1}}$.
- $a=\dfrac{\mathrm dv}{\mathrm dt}=12t-3$, so $a(2)=\boxed{21\ \text{m s}^{-2}}$.

## Example 8.14: Rational functions
**(a)** $\dfrac{3x+2}{2x^2+1}$:

$$f'=\frac{3(2x^2+1)-(3x+2)(4x)}{(2x^2+1)^2}=\frac{6x^2+3-12x^2-8x}{(2x^2+1)^2}=\boxed{\frac{3-8x-6x^2}{(2x^2+1)^2}}$$

**(b)** $\dfrac{2x+3}{x^2+x+1}$:

$$f'=\frac{2(x^2+x+1)-(2x+3)(2x+1)}{(x^2+x+1)^2}=\frac{2x^2+2x+2-4x^2-8x-3}{(\cdots)^2}=\boxed{-\frac{2x^2+6x+1}{(x^2+x+1)^2}}$$

**(c)** Write the function as $x^3+2x^2-x^{-1}+x^{-2}+3$ and differentiate term by term:

$$f'=\boxed{3x^2+4x+\frac1{x^2}-\frac2{x^3}}\quad\left(=\frac{3x^5+4x^4+x-2}{x^3}\right)$$

## Example 8.15: Chain rule $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{\mathrm dy}{\mathrm du}\dfrac{\mathrm du}{\mathrm dx}$
**(a)** Let $u=5x^2+11$, so $y=u^9$. Then $y'=9u^8\cdot10x=\boxed{90x(5x^2+11)^8}$.

**(b)** Let $u=3x^2+1$, so $y=u^{1/2}$. Then $y'=\tfrac12u^{-1/2}\cdot6x=\boxed{\dfrac{3x}{\sqrt{3x^2+1}}}$.

## Example 8.16
**(a)** $y'=5(3x^3-2x^2+1)^4(9x^2-4x)=\boxed{5x(9x-4)(3x^3-2x^2+1)^4}$.

**(b)** $y=(5x^2-2)^{-7}$, so $y'=-7(5x^2-2)^{-8}(10x)=\boxed{-\dfrac{70x}{(5x^2-2)^8}}$.

**(c)** Product of $(x^2+1)^3$ and $(x-1)^{1/2}$:

$$y'=3(x^2+1)^2(2x)\sqrt{x-1}+\frac{(x^2+1)^3}{2\sqrt{x-1}}=\frac{(x^2+1)^2\big[12x(x-1)+(x^2+1)\big]}{2\sqrt{x-1}}=\boxed{\frac{(x^2+1)^2(13x^2-12x+1)}{2\sqrt{x-1}}}$$

**(d)** Quotient with $u=(2x+1)^{1/2}$, $u'=(2x+1)^{-1/2}$; $v=(x^2+1)^3$, $v'=6x(x^2+1)^2$:

$$y'=\frac{(2x+1)^{-1/2}(x^2+1)^3-(2x+1)^{1/2}\,6x(x^2+1)^2}{(x^2+1)^6}$$

Multiply the top and bottom by $(2x+1)^{1/2}$ and cancel $(x^2+1)^2$:

$$y'=\frac{(x^2+1)-6x(2x+1)}{\sqrt{2x+1}\,(x^2+1)^4}=\boxed{\frac{1-6x-11x^2}{\sqrt{2x+1}\,(x^2+1)^4}}$$

## Example 8.17: Trig and inverse-trig functions
| | $y$ | working | $\dfrac{\mathrm dy}{\mathrm dx}$ |
|---|---|---|---|
| (a) | $\sin(2x+3)$ | chain rule | $2\cos(2x+3)$ |
| (b) | $x^2\cos x$ | product rule | $2x\cos x-x^2\sin x$ |
| (c) | $\dfrac{\sin2x}{x^2+2}$ | quotient rule | $\dfrac{2(x^2+2)\cos2x-2x\sin2x}{(x^2+2)^2}$ |
| (d) | $\sec6x=(\cos6x)^{-1}$ | chain rule | $6\sin6x/\cos^26x=6\sec6x\tan6x$ |
| (e) | $x\tan2x$ | product rule | $\tan2x+2x\sec^22x$ |
| (f) | $\sin^{-1}6x$ | $\frac{\mathrm d}{\mathrm du}\sin^{-1}u=\frac1{\sqrt{1-u^2}}$ | $\dfrac{6}{\sqrt{1-36x^2}}$ |
| (g) | $x^2\cos^{-1}x$ | product rule, $(\cos^{-1}x)'=-\frac1{\sqrt{1-x^2}}$ | $2x\cos^{-1}x-\dfrac{x^2}{\sqrt{1-x^2}}$ |

**(h)** $y=\tan^{-1}u$ with $u=\dfrac{2x}{1+x^2}$, so $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{u'}{1+u^2}$.
- $u'=\dfrac{2(1+x^2)-2x\cdot2x}{(1+x^2)^2}=\dfrac{2(1-x^2)}{(1+x^2)^2}$.
- $1+u^2=\dfrac{(1+x^2)^2+4x^2}{(1+x^2)^2}=\dfrac{x^4+6x^2+1}{(1+x^2)^2}$.

$$\frac{\mathrm dy}{\mathrm dx}=\boxed{\frac{2(1-x^2)}{x^4+6x^2+1}}$$

## Example 8.18
**(a)** $y=\sin^2(x^2+1)=[\sin u]^2$ with $u=x^2+1$. Differentiate the outer square, then $\sin$, then $u$:

$$y'=2\sin(x^2+1)\cos(x^2+1)\cdot2x=\boxed{2x\sin\big(2(x^2+1)\big)}$$

**(b)** $y=\cos^{-1}u$ with $u=\sqrt{1-x^2}$. Then $u'=\dfrac{-x}{\sqrt{1-x^2}}$ and $\sqrt{1-u^2}=\sqrt{x^2}=|x|$:

$$y'=-\frac{u'}{\sqrt{1-u^2}}=\frac{x}{|x|\sqrt{1-x^2}}=\begin{cases}\dfrac1{\sqrt{1-x^2}}&0<x<1\\[2mm]-\dfrac1{\sqrt{1-x^2}}&-1<x<0\end{cases}$$

The $|x|$ matters. For $x>0$, $y=\sin^{-1}x$, which is why the derivative matches.

## Example 8.19: Exponentials and logs
| | $y$ | $\dfrac{\mathrm dy}{\mathrm dx}$ |
|---|---|---|
| (a) | $x^2e^x$ | $2xe^x+x^2e^x=x(x+2)e^x$ |
| (b) | $3e^{-2x}$ | $-6e^{-2x}$ |
| (c) | $\dfrac{\ln x}{x^2}$ | $\dfrac{\frac1x\cdot x^2-2x\ln x}{x^4}=\dfrac{1-2\ln x}{x^3}$ |
| (d) | $\ln(x^2+1)$ | $\dfrac{2x}{x^2+1}$ |
| (e) | $e^{-x}(\sin x+\cos x)$ | $-e^{-x}(\sin x+\cos x)+e^{-x}(\cos x-\sin x)=-2e^{-x}\sin x$ |

## Example 8.27: Second derivatives
**(a)** $y'=12x^3-4x+1$, so $\boxed{y''=36x^2-4}$.

**(b)** $y=\dfrac{x}{x^2+1}$, so $y'=\dfrac{(x^2+1)-2x^2}{(x^2+1)^2}=\dfrac{1-x^2}{(x^2+1)^2}$. Differentiating again:

$$y''=\frac{-2x(x^2+1)^2-(1-x^2)\cdot2(x^2+1)\cdot2x}{(x^2+1)^4}=\frac{-2x(x^2+1)-4x(1-x^2)}{(x^2+1)^3}=\boxed{\frac{2x(x^2-3)}{(x^2+1)^3}}$$

**(c)** $y=e^{-x}\sin2x$:
- $y'=e^{-x}(2\cos2x-\sin2x)$
- $y''=-e^{-x}(2\cos2x-\sin2x)+e^{-x}(-4\sin2x-2\cos2x)=\boxed{-e^{-x}(4\cos2x+3\sin2x)}$

**(d)** $y=\dfrac{\ln x}{x}$:
- $y'=\dfrac{1-\ln x}{x^2}$
- $y''=\dfrac{-\frac1x\cdot x^2-(1-\ln x)2x}{x^4}=\dfrac{-x-2x+2x\ln x}{x^4}=\boxed{\dfrac{2\ln x-3}{x^3}}$

## Example 9.17: Newton–Raphson for $x\tan x=4$ near $x=1$
Let $f(x)=x\tan x-4$, so $f'(x)=\tan x+x\sec^2x$ and

$$x_{n+1}=x_n-\frac{x_n\tan x_n-4}{\tan x_n+x_n\sec^2x_n}.$$

| $n$ | $x_n$ | $f(x_n)$ | $f'(x_n)$ |
|---|---|---|---|
| 0 | 1.000000 | −2.4426 | 4.9829 |
| 1 | 1.490192 | 14.4478 | 242.24 |
| 2 | 1.430551 | 6.1334 | 80.294 |
| 3 | 1.354164 | 2.1529 | 33.855 |
| 4 | 1.290572 | 0.4843 | 20.347 |
| 5 | 1.266769 | 0.0375 | 17.322 |
| 6 | 1.264607 | 0.00026 | 17.082 |
| 7 | 1.264592 | ≈0 | |

**Root**: $x\approx\boxed{1.2646}$.
- The first step **overshoots**, because $f'(1)$ is small compared with the steepness of $\tan x$ near $\pi/2$. The iteration then creeps back from the high side.
- Starting at $x_0=1.2$ would converge in about 3 steps.
- The roots are all in $(n\pi,n\pi+\tfrac\pi2)$, which is a good way to choose $x_0$.

## Example 9.18: $8x^4+0.45x^3-4.544x-0.1136=0$ near $0.8$
$f'(x)=32x^3+1.35x^2-4.544$.

| $n$ | $x_n$ | $f(x_n)$ | $f'(x_n)$ |
|---|---|---|---|
| 0 | 0.8 | −0.2416 | 12.704 |
| 1 | 0.819018 | 0.011681 | 13.942 |
| 2 | 0.818180 | 0.000023 | 13.886 |
| 3 | 0.818178 | | |

$x_2$ and $x_3$ agree to 4 s.f., so $x=\boxed{0.8182}$ (4 s.f.). Convergence is quadratic: the error roughly squares at each step.

## Example 9.24: Partial derivatives
To find $\partial f/\partial x$, differentiate with respect to $x$ while holding $y$ constant, and vice versa.

**(a)** $f=3x^2+2xy+y^3$:

$$\frac{\partial f}{\partial x}=6x+2y,\qquad\frac{\partial f}{\partial y}=2x+3y^2$$

**(b)** $f=(y^2+x)e^{-xy}$. Use the product rule, remembering $\partial_x(e^{-xy})=-ye^{-xy}$ and $\partial_y(e^{-xy})=-xe^{-xy}$:

$$\frac{\partial f}{\partial x}=e^{-xy}-y(y^2+x)e^{-xy}=\boxed{(1-xy-y^3)e^{-xy}}$$

$$\frac{\partial f}{\partial y}=2ye^{-xy}-x(y^2+x)e^{-xy}=\boxed{(2y-xy^2-x^2)e^{-xy}}$$

## Example 9.25
**(a)** $f=xy^2+3xy-x+2$:

$$\frac{\partial f}{\partial x}=y^2+3y-1,\qquad\frac{\partial f}{\partial y}=2xy+3x$$

**(b)** $f=\sin(x^2-3y)$, using the chain rule on the inner function:

$$\frac{\partial f}{\partial x}=2x\cos(x^2-3y),\qquad\frac{\partial f}{\partial y}=-3\cos(x^2-3y)$$

---

# Part B: Assigned exercises

## Exercise 1(c) (p.552): $f(x)=x^2-2$ from first principles

$$\frac{f(x+\Delta x)-f(x)}{\Delta x}=\frac{(x+\Delta x)^2-2-x^2+2}{\Delta x}=\frac{2x\,\Delta x+(\Delta x)^2}{\Delta x}=2x+\Delta x\to\boxed{2x}$$

The constant $-2$ cancels in the difference, which is why constants differentiate to zero.

## Exercise 25 (p.572)
**(e)** $(x^4-3x+1)(6x^2+5)$, by the product rule:

$$f'=(4x^3-3)(6x^2+5)+(x^4-3x+1)(12x)=24x^5+20x^3-18x^2-15+12x^5-36x^2+12x$$

$$\boxed{f'=36x^5+20x^3-54x^2+12x-15}$$

**(f)** $\dfrac{x-3}{x-2}$:

$$f'=\frac{(x-2)-(x-3)}{(x-2)^2}=\boxed{\frac{1}{(x-2)^2}}$$

## Exercises 26, 27, 32, 33 (p.579): Chain rule
**26(a)** $(5x+3)^9$, so $f'=9(5x+3)^8\cdot5=\boxed{45(5x+3)^8}$.

**26(e)** $(4x^3-2x+1)^6$, so $f'=6(4x^3-2x+1)^5(12x^2-2)=\boxed{12(6x^2-1)(4x^3-2x+1)^5}$.

**27(d)** $(x^2+x+1)^2(x^3+2x^2+1)^4$. Let $P=x^2+x+1$ and $Q=x^3+2x^2+1$. Then

$$f'=2P(2x+1)Q^4+4P^2Q^3(3x^2+4x)=2PQ^3\big[(2x+1)Q+2P(3x^2+4x)\big].$$

Expand the bracket:
- $(2x+1)(x^3+2x^2+1)=2x^4+5x^3+2x^2+2x+1$
- $2(x^2+x+1)(3x^2+4x)=6x^4+14x^3+14x^2+8x$

Adding these gives $8x^4+19x^3+16x^2+10x+1$, so

$$\boxed{f'=2(x^2+x+1)(x^3+2x^2+1)^3(8x^4+19x^3+16x^2+10x+1)}$$

**32(a)** $x\sqrt{4+x^2}$:

$$f'=\sqrt{4+x^2}+\frac{x\cdot x}{\sqrt{4+x^2}}=\frac{4+x^2+x^2}{\sqrt{4+x^2}}=\boxed{\frac{2(x^2+2)}{\sqrt{x^2+4}}}$$

**32(e)** $\sqrt[3]{x^2+1}=(x^2+1)^{1/3}$, so

$$f'=\tfrac13(x^2+1)^{-2/3}\cdot2x=\boxed{\frac{2x}{3(x^2+1)^{2/3}}}$$

**33(b)** Expand first: $\left(\sqrt x+\frac1{\sqrt x}\right)^2=x+2+\frac1x$, so

$$f'=\boxed{1-\frac1{x^2}}=\frac{x^2-1}{x^2}$$

**33(d)** $\dfrac{(2x+1)^2}{(3x^2+1)^3}$, with $u'=4(2x+1)$ and $v'=3(3x^2+1)^2\cdot6x=18x(3x^2+1)^2$:

$$f'=\frac{4(2x+1)(3x^2+1)^3-(2x+1)^2\cdot18x(3x^2+1)^2}{(3x^2+1)^6}=\frac{2(2x+1)\big[2(3x^2+1)-9x(2x+1)\big]}{(3x^2+1)^4}$$

$$\boxed{f'=-\frac{2(2x+1)(12x^2+9x-2)}{(3x^2+1)^4}}$$

## Exercise 34 (p.586)
**(c)** $\cos^23x$:

$$f'=2\cos3x\cdot(-\sin3x)\cdot3=-6\sin3x\cos3x=\boxed{-3\sin6x}$$

**(f)** $\sqrt{2+\cos2x}$:

$$f'=\frac{-2\sin2x}{2\sqrt{2+\cos2x}}=\boxed{-\frac{\sin2x}{\sqrt{2+\cos2x}}}$$

## Exercises 38, 39 (p.591)
**38(b)** $e^{-x/2}$, so $f'=\boxed{-\tfrac12e^{-x/2}}$.

**38(e)** $(3x+2)e^{-x}$:

$$f'=3e^{-x}-(3x+2)e^{-x}=\boxed{(1-3x)e^{-x}}$$

**39(b)** $\ln(x^2+2x+3)$, so $f'=\dfrac{2x+2}{x^2+2x+3}=\boxed{\dfrac{2(x+1)}{x^2+2x+3}}$.

**39(c)** Split the log first: $\ln\frac{x-2}{x-3}=\ln(x-2)-\ln(x-3)$. Then

$$f'=\frac1{x-2}-\frac1{x-3}=\frac{(x-3)-(x-2)}{(x-2)(x-3)}=\boxed{-\frac{1}{(x-2)(x-3)}}$$

## Exercises 60(a), 62 (p.601)
**60(a)** $y=x^3(1+x^2)^{1/2}$.
- $y'=3x^2(1+x^2)^{1/2}+x^4(1+x^2)^{-1/2}=\dfrac{3x^2(1+x^2)+x^4}{\sqrt{1+x^2}}=\dfrac{4x^4+3x^2}{\sqrt{1+x^2}}$.
- Now apply the quotient rule to $u=4x^4+3x^2$ and $v=(1+x^2)^{1/2}$:

$$y''=\frac{(16x^3+6x)(1+x^2)-(4x^4+3x^2)x}{(1+x^2)^{3/2}}=\frac{16x^3+6x+16x^5+6x^3-4x^5-3x^3}{(1+x^2)^{3/2}}$$

$$\boxed{y''=\frac{x(12x^4+19x^2+6)}{(1+x^2)^{3/2}}}$$

**62** $y=3e^{2x}\cos(2x-3)$. Write $c=\cos(2x-3)$ and $s=\sin(2x-3)$.
- $y'=6e^{2x}c-6e^{2x}s=6e^{2x}(c-s)$
- $y''=12e^{2x}(c-s)+6e^{2x}(-2s-2c)=e^{2x}(12c-12s-12s-12c)=-24e^{2x}s$

Then

$$y''-4y'+8y=e^{2x}\big[-24s-24c+24s+24c\big]=0\ ✔$$

## Booklet Example A: $x^3=7$ from $x_0=2$
Let $f(x)=x^3-7$ and $f'(x)=3x^2$. Then $x_{n+1}=x_n-\dfrac{x_n^3-7}{3x_n^2}=\dfrac{2x_n^3+7}{3x_n^2}$.

| $n$ | $x_n$ | $x_{n+1}$ (4 d.p.) |
|---|---|---|
| 0 | 2 | $\frac{16+7}{12}=1.9167$ |
| 1 | 1.916667 | 1.9129 |
| 2 | 1.912938 | 1.9129 |

So $x_1=1.9167$, $x_2=1.9129$ and $x_3=1.9129$. Check: $\sqrt[3]7=1.912931\ldots$ ✔

## Exercise 26 (p.731): Positive roots of $x^4-4x^3-12x^2+32x+28=0$
**Locate the roots.** Tabulate $f(x)$:

| $x$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|
| $f(x)$ | 28 | 45 | 28 | **−11** | −36 | **13** | 220 |

The sign changes put the roots in $(2,3)$ and $(4,5)$. Here $f'(x)=4x^3-12x^2-24x+32$.

| Root in $(2,3)$, $x_0=3$ | | Root in $(4,5)$, $x_0=5$ | |
|---|---|---|---|
| $x_1=3-\frac{-11}{-40}$ | 2.725000 | $x_1=5-\frac{13}{112}$ | 4.883929 |
| $x_2$ | 2.732051 | $x_2$ | 4.873075 |
| $x_3$ | 2.732051 | $x_3$ | 4.872983 |

$$\boxed{x\approx2.7321\quad\text{and}\quad x\approx4.8730}$$

> [!tip] Exact check
> The quartic factorises as $(x^2-2x-2)(x^2-2x-14)$, so the roots are $1\pm\sqrt3$ and $1\pm\sqrt{15}$. The positive ones are $1+\sqrt3=2.73205$ and $1+\sqrt{15}=4.87298$ ✔. The other two, $-0.732$ and $-2.873$, are negative.

## Exercise 39 (p.747): Partial derivatives
**(a)** $f=x^3y+2x^2+9y^2+xy+10$:

$$f_x=3x^2y+4x+y,\qquad f_y=x^3+18y+x$$

**(b)** $f=(x+y^2)^3$:

$$f_x=3(x+y^2)^2,\qquad f_y=3(x+y^2)^2\cdot2y=6y(x+y^2)^2$$

**(c)** $f=(3x^2+y^2+2xy)^{1/2}$:

$$f_x=\frac{6x+2y}{2\sqrt{3x^2+y^2+2xy}}=\frac{3x+y}{\sqrt{3x^2+y^2+2xy}},\qquad f_y=\frac{2y+2x}{2\sqrt{\cdots}}=\frac{x+y}{\sqrt{3x^2+y^2+2xy}}$$

---

# Part C: Specimen Test 3

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 3), then solved and checked with SymPy, NumPy or SciPy.

## Q1: The derivative from first principles
**(i)**

$$\frac{\mathrm df}{\mathrm dx}=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}$$

**(ii)** For $f=2x^2$:

$$\frac{2(x+\Delta x)^2-2x^2}{\Delta x}=\frac{4x\,\Delta x+2(\Delta x)^2}{\Delta x}=4x+2\Delta x\to\boxed{4x}$$

## Q2: Differentiate
| | $f(x)$ | $f'(x)$ |
|---|---|---|
| (i) | $6x^{1/4}$ | $\tfrac32x^{-3/4}$ |
| (ii) | $2x^{-3}$ | $-6x^{-4}=-\dfrac6{x^4}$ |
| (iii) | $(x^2+x+1)^3$ | $3(2x+1)(x^2+x+1)^2$ |
| (iv) | $5+\cos(x^4)$ | $-4x^3\sin(x^4)$ |
| (v) | $e^{-2x}\sin2x$ | $-2e^{-2x}\sin2x+2e^{-2x}\cos2x=2e^{-2x}(\cos2x-\sin2x)$ |
| (vi) | $\dfrac{x}{\sqrt{x^2+1}}$ | $\dfrac{\sqrt{x^2+1}-\frac{x^2}{\sqrt{x^2+1}}}{x^2+1}=\dfrac{1}{(x^2+1)^{3/2}}$ |
| (vii) | $\ln(2+\sin x)$ | $\dfrac{\cos x}{2+\sin x}$ |
| (viii) | $\sin^2(x^3+1)$ | $2\sin(x^3+1)\cos(x^3+1)\cdot3x^2=3x^2\sin\big(2(x^3+1)\big)$ |

## Q3: Newton–Raphson for $x^2=5$ from $x_0=2$
Here $f=x^2-5$ and $f'=2x$, so $x_{n+1}=x_n-\dfrac{x_n^2-5}{2x_n}=\dfrac12\Big(x_n+\dfrac5{x_n}\Big)$.
- $x_1=\tfrac12(2+2.5)=\boxed{2.25}$
- $x_2=\tfrac12\big(2.25+\tfrac5{2.25}\big)=\boxed{2.2361}$

This is already correct to 4 d.p.: $\sqrt5=2.23607$.

## Q4: Partial derivatives
**(i)** $f=x^2y^2+xy-x^2+y^2-5x$:

$$f_x=2xy^2+y-2x-5,\qquad f_y=2x^2y+x+2y$$

**(ii)** $f=\ln(xy)=\ln x+\ln y$:

$$f_x=\frac1x,\qquad f_y=\frac1y$$

## Sources
- Transcribed problem statements: `tmp/md/module_03_differentiation_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §8.2–8.4, §9.4.8, §9.6; MATH1054 Module Booklet, Module 3
