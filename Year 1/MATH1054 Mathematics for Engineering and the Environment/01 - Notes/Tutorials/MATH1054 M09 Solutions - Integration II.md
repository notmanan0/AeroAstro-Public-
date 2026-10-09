---
title: "MATH1054 M09 Solutions - Integration II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - integration
  - substitution
  - centroids
sheet: "Specimen Test 9 (booklet) + Module 09 work scheme: Examples 8.52–8.69; Exercises 112(h), 115(b),(d), 122(b), 131, 132, 135; Booklet Exercises A, B"
theory_notes: ["[[MATH1054 M09 - Integration II]]"]
key_concepts: ["[[Integration by Substitution]]", "[[Centroids and Solids of Revolution]]", "[[RMS Value]]"]
status: complete
sources: ["tmp/md/module_09_integration_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§8.8, §8.9)", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# MATH1054 M09 Solutions - Integration II

> [!abstract] Sheet Info
> The whole Module 09 work scheme: substitution, then geometric and physical applications. Every integral was checked with SymPy.
>
> Formulae used for a region under $y=f(x)$ on $[a,b]$ ([[Integration Formulae]]):
> $$A=\int y\,\mathrm dx,\quad\bar x=\frac1A\int xy\,\mathrm dx,\quad\bar y=\frac1{2A}\int y^2\,\mathrm dx,\quad V=\pi\int y^2\,\mathrm dx,\quad\bar x_V=\frac{\pi}{V}\int xy^2\,\mathrm dx$$

## Theory Links
- [[MATH1054 M09 - Integration II]] · [[Integration by Substitution]] · [[Centroids and Solids of Revolution]] · [[RMS Value]]

---

# Part A: Worked examples

## Example 8.52: Recognising $\int f'(x)g(f(x))\,\mathrm dx$
**(a)** $\int2x\sqrt{x^2+3}\,\mathrm dx$. Let $u=x^2+3$, so $\mathrm du=2x\,\mathrm dx$:
$$\int u^{1/2}\,\mathrm du=\tfrac23u^{3/2}=\boxed{\tfrac23(x^2+3)^{3/2}+C}$$

**(b)** $\int\dfrac{x+1}{x^2+2x+2}\,\mathrm dx$. The numerator is exactly half the derivative of the denominator, and $\int\frac{f'}{f}=\ln|f|$:
$$\int\frac{x+1}{x^2+2x+2}\,\mathrm dx=\boxed{\tfrac12\ln(x^2+2x+2)+C}$$
No modulus is needed, because $x^2+2x+2=(x+1)^2+1>0$.

## Example 8.59: $\int\dfrac{\mathrm dx}{2+\sqrt{1-x}}$
Let $u=\sqrt{1-x}$. Then $x=1-u^2$ and $\mathrm dx=-2u\,\mathrm du$:
$$\int\frac{-2u}{2+u}\,\mathrm du=-2\int\Big(1-\frac2{2+u}\Big)\mathrm du=-2u+4\ln(2+u)$$
$$\boxed{=-2\sqrt{1-x}+4\ln\big(2+\sqrt{1-x}\big)+C}$$

## Example 8.60: $\int\sqrt{1-x^2}\,\mathrm dx$, $0\le x\le1$
Let $x=\sin\theta$. Then $\mathrm dx=\cos\theta\,\mathrm d\theta$ and $\sqrt{1-x^2}=\cos\theta$ (since $\cos\theta\ge0$ here):
$$\int\cos^2\theta\,\mathrm d\theta=\tfrac12\theta+\tfrac14\sin2\theta=\tfrac12\theta+\tfrac12\sin\theta\cos\theta$$
$$\boxed{=\tfrac12\sin^{-1}x+\tfrac12x\sqrt{1-x^2}+C}$$
As a check, $\int_0^1\sqrt{1-x^2}\,\mathrm dx=\frac\pi4$, the area of a quarter of the unit circle ✔.

## Example 8.62: $\int_{-2}^2\dfrac{\sqrt{x+2}}{x+6}\,\mathrm dx$ with $u=\sqrt{x+2}$
- $x=u^2-2$, so $\mathrm dx=2u\,\mathrm du$ and $x+6=u^2+4$.
- The limits change: $x=-2\to u=0$ and $x=2\to u=2$.
$$\int_0^2\frac{2u^2}{u^2+4}\,\mathrm du=2\int_0^2\Big(1-\frac{4}{u^2+4}\Big)\mathrm du=2\Big[u-2\tan^{-1}\frac u2\Big]_0^2=2\Big(2-\frac\pi2\Big)=\boxed{4-\pi\approx0.8584}$$
**Change the limits** along with the variable. Then there is no need to substitute back.

## Example 8.65: The region under $y=\sqrt{x-2}$ on $[2,5]$, rotated about the $x$-axis
**(a) The plane area and its centroid**:
- $A=\displaystyle\int_2^5(x-2)^{1/2}\,\mathrm dx=\tfrac23\big[(x-2)^{3/2}\big]_2^5=\tfrac23\cdot3\sqrt3=\boxed{2\sqrt3\approx3.464}$
- $\displaystyle\int_2^5x\sqrt{x-2}\,\mathrm dx$: let $u=x-2$, giving $\int_0^3(u+2)u^{1/2}\,\mathrm du=\Big[\tfrac25u^{5/2}+\tfrac43u^{3/2}\Big]_0^3=\tfrac{18\sqrt3}5+4\sqrt3=\tfrac{38\sqrt3}{5}$. So $\bar x=\dfrac{38\sqrt3/5}{2\sqrt3}=\boxed{3.8}$.
- $\bar y=\dfrac{1}{2A}\displaystyle\int_2^5(x-2)\,\mathrm dx=\frac{9/2}{4\sqrt3}=\boxed{\tfrac{3\sqrt3}8\approx0.650}$

**(b) The solid of revolution and its centre of gravity**:
- $V=\pi\displaystyle\int_2^5(x-2)\,\mathrm dx=\boxed{\tfrac{9\pi}2\approx14.14}$
- $\bar x_V=\dfrac\pi V\displaystyle\int_2^5x(x-2)\,\mathrm dx=\frac{2}{9}\Big[\tfrac{x^3}3-x^2\Big]_2^5=\frac29\Big(\tfrac{50}3+\tfrac43\Big)=\boxed4$
- By symmetry, the centre of gravity is at $(4,0,0)$.

![[m1054_centroid_regions.png|800]]

## Example 8.67: RMS of $i=I\sin\theta$ over $[0,2\pi]$
$$i_{\text{rms}}^2=\frac1{2\pi}\int_0^{2\pi}I^2\sin^2\theta\,\mathrm d\theta=\frac{I^2}{2\pi}\int_0^{2\pi}\tfrac12(1-\cos2\theta)\,\mathrm d\theta=\frac{I^2}{2\pi}\cdot\pi=\frac{I^2}2$$
$$\boxed{i_{\text{rms}}=\frac{I}{\sqrt2}\approx0.707I}$$
This is why the peak of the 230 V mains is $230\sqrt2\approx325$ V ([[RMS Value]]).

## Example 8.68: Surface area of the paraboloid, $y=\sqrt x$ on $[0,1]$
$S=2\pi\int y\sqrt{1+y'^2}\,\mathrm dx$, with $y'=\frac1{2\sqrt x}$, so $1+y'^2=1+\frac1{4x}$:
$$S=2\pi\int_0^1\sqrt x\sqrt{1+\frac1{4x}}\,\mathrm dx=2\pi\int_0^1\sqrt{x+\tfrac14}\,\mathrm dx=\frac{4\pi}3\Big[(x+\tfrac14)^{3/2}\Big]_0^1$$
$$=\frac{4\pi}3\cdot\frac{5\sqrt5-1}{8}=\boxed{\frac\pi6\big(5\sqrt5-1\big)\approx5.330}$$

## Example 8.69: Length of the suspension-bridge cable
$y=\dfrac{hx^2}{l^2}-\dfrac{2hx}{l}+h=\dfrac{h}{l^2}(x-l)^2$, so $y'=\dfrac{2h}{l^2}(x-l)$. The arc length is $L=\int_0^{2l}\sqrt{1+y'^2}\,\mathrm dx$.

Let $u=x-l$ and $k=\frac{2h}{l^2}$. The integrand is even in $u$, so
$$L=2\int_0^l\sqrt{1+k^2u^2}\,\mathrm du.$$
Use the standard integral $\int\sqrt{1+k^2u^2}\,\mathrm du=\tfrac u2\sqrt{1+k^2u^2}+\tfrac1{2k}\sinh^{-1}(ku)$, which you get from the substitution $ku=\sinh t$. With $kl=\frac{2h}{l}$:
$$L=l\sqrt{1+\frac{4h^2}{l^2}}+\frac1k\sinh^{-1}\frac{2h}{l}=\boxed{\sqrt{l^2+4h^2}+\frac{l^2}{2h}\sinh^{-1}\frac{2h}{l}}$$
**Sanity check**: as $h\to0$, $\sinh^{-1}(2h/l)\approx2h/l$, so $L\to l+l=2l$, which is the span ✔.

---

# Part B: Assigned exercises

## Booklet Exercise A: Recognise the inner function
| | Integral | Substitution / pattern | Result |
|---|---|---|---|
| (a) | $\int x^2(1+x^3)^4\,\mathrm dx$ | $u=1+x^3$, $\mathrm du=3x^2\,\mathrm dx$ | $\tfrac1{15}(1+x^3)^5+C$ |
| (b) | $\int\cos x\sin^3x\,\mathrm dx$ | $u=\sin x$ | $\tfrac14\sin^4x+C$ |
| (c) | $\int x\cos(x^2)\,\mathrm dx$ | $u=x^2$, $\mathrm du=2x\,\mathrm dx$ | $\tfrac12\sin(x^2)+C$ |
| (d) | $\int\frac{\cosh x}{\sinh x}\,\mathrm dx$ | $f'/f$ | $\ln\lvert\sinh x\rvert+C$ |
| (e) | $\int\frac{2x}{1+x^2}\,\mathrm dx$ | $f'/f$ | $\ln(1+x^2)+C$ |
| (f) | $\int\frac{\cos x-\sin x}{\sin x+\cos x}\,\mathrm dx$ | $f'/f$, since $(\sin x+\cos x)'=\cos x-\sin x$ | $\ln\lvert\sin x+\cos x\rvert+C$ |
| (g) | $\int\frac{\ln x}{x}\,\mathrm dx$ | $u=\ln x$, $\mathrm du=\mathrm dx/x$ | $\tfrac12(\ln x)^2+C$ |

Worked line for (a): $\int x^2u^4\frac{\mathrm du}{3x^2}=\frac13\cdot\frac{u^5}5$.

## Booklet Exercise B: From first principles with the given substitution
**(a)** $\int\dfrac{\mathrm dx}{\sqrt{x^2-1}}$ with $x=\cosh u$, $u\ge0$.
- $\mathrm dx=\sinh u\,\mathrm du$, and $\sqrt{\cosh^2u-1}=\sinh u$ (positive for $u\ge0$).
$$\int\frac{\sinh u}{\sinh u}\,\mathrm du=u+C=\boxed{\cosh^{-1}x+C=\ln\big(x+\sqrt{x^2-1}\big)+C}$$

**(b)** $\int\dfrac{\mathrm dx}{1+x^2}$ with $x=\tan\theta$.
- $\mathrm dx=\sec^2\theta\,\mathrm d\theta$, and $1+\tan^2\theta=\sec^2\theta$.
$$\int\frac{\sec^2\theta}{\sec^2\theta}\,\mathrm d\theta=\theta+C=\boxed{\tan^{-1}x+C}$$

## Exercise 112(h): $\int\dfrac{x}{\sqrt{4-x^2}}\,\mathrm dx$
Let $u=4-x^2$, so $\mathrm du=-2x\,\mathrm dx$:
$$-\tfrac12\int u^{-1/2}\,\mathrm du=-u^{1/2}=\boxed{-\sqrt{4-x^2}+C}$$

## Exercise 115
**(b)** $\int_0^{\sqrt3}\dfrac{\tan^{-1}x}{1+x^2}\,\mathrm dx$ with $u=\tan^{-1}x$. Then $\mathrm du=\frac{\mathrm dx}{1+x^2}$, and the limits become $0\to0$, $\sqrt3\to\frac\pi3$:
$$\int_0^{\pi/3}u\,\mathrm du=\tfrac12\Big(\frac\pi3\Big)^2=\boxed{\frac{\pi^2}{18}\approx0.5483}$$

**(d)** $\int_1^4\dfrac{e^{\sqrt x}}{\sqrt x}\,\mathrm dx$ with $u=\sqrt x$. Then $\mathrm du=\frac{\mathrm dx}{2\sqrt x}$, and the limits become $1\to1$, $4\to2$:
$$2\int_1^2e^u\,\mathrm du=\boxed{2(e^2-e)\approx9.342}$$

## Exercise 122(b): $\int\sin^2x\cos^3x\,\mathrm dx$
With an odd power of cosine, save one $\cos x$ and convert the rest using $\cos^2x=1-\sin^2x$:
$$\int\sin^2x(1-\sin^2x)\cos x\,\mathrm dx\ \xrightarrow{u=\sin x}\ \int(u^2-u^4)\,\mathrm du=\boxed{\tfrac13\sin^3x-\tfrac15\sin^5x+C}$$

## Exercise 131: Average resistance
The mean value of $R$ over $10\le\theta\le40$ is
$$\bar R=\frac1{30}\int_{10}^{40}38(1+0.004\theta)\,\mathrm d\theta=\frac{38}{30}\Big[\theta+0.002\theta^2\Big]_{10}^{40}=\frac{38}{30}(30+3)=\boxed{41.8\ \Omega}$$
$R$ is linear in $\theta$, so its mean is simply $R$ at the midpoint, $\theta=25\,°$C: $38(1.1)=41.8$ ✔.

## Exercise 132: The region under $y=x(2-x)$ on $[1,2]$
**(a) Area and centroid**:
- $A=\displaystyle\int_1^2(2x-x^2)\,\mathrm dx=\Big[x^2-\tfrac{x^3}3\Big]_1^2=\tfrac43-\tfrac23=\boxed{\tfrac23}$
- $\displaystyle\int_1^2x\,y\,\mathrm dx=\Big[\tfrac23x^3-\tfrac14x^4\Big]_1^2=\tfrac43-\tfrac5{12}=\tfrac{11}{12}$, so $\bar x=\dfrac{11/12}{2/3}=\boxed{\tfrac{11}8}$.
- $\displaystyle\int_1^2y^2\,\mathrm dx=\Big[\tfrac43x^3-x^4+\tfrac15x^5\Big]_1^2=\tfrac8{15}$, so $\bar y=\dfrac{8/15}{2\cdot\frac23}=\boxed{\tfrac25}$.

**(b) Volume and centre of gravity**:
- $V=\pi\cdot\tfrac8{15}=\boxed{\tfrac{8\pi}{15}\approx1.676}$
- $\displaystyle\int_1^2xy^2\,\mathrm dx=\Big[x^4-\tfrac45x^5+\tfrac16x^6\Big]_1^2=\tfrac7{10}$, so $\bar x_V=\dfrac{7/10}{8/15}=\boxed{\tfrac{21}{16}}$.
- The centre of gravity is at $(\frac{21}{16},0,0)$.

## Exercise 135: The region between $y^2=4x$ and $y=2x$
The curves meet where $4x=4x^2$, i.e. at $x=0$ and $x=1$. On $[0,1]$ the upper curve is $y_u=2\sqrt x$ and the lower is $y_l=2x$.

**Area and centroid**. Use strips of height $y_u-y_l$:
- $A=\displaystyle\int_0^1(2\sqrt x-2x)\,\mathrm dx=\tfrac43-1=\tfrac13$
- $\bar x=\dfrac1A\displaystyle\int_0^1x(2\sqrt x-2x)\,\mathrm dx=3\Big(\tfrac45-\tfrac23\Big)=\tfrac25$
- $\bar y=\dfrac1{2A}\displaystyle\int_0^1(y_u^2-y_l^2)\,\mathrm dx=\tfrac32\int_0^1(4x-4x^2)\,\mathrm dx=\tfrac32\cdot\tfrac23=1$

$$\boxed{\text{centroid of the area}=\big(\tfrac25,\,1\big)}$$

**Solid of revolution** (a washer, outer radius $y_u$, inner radius $y_l$):
- $V=\pi\displaystyle\int_0^1(4x-4x^2)\,\mathrm dx=\tfrac{2\pi}3$
- $\bar x_V=\dfrac\pi V\displaystyle\int_0^1x(4x-4x^2)\,\mathrm dx=\frac32\Big(\tfrac43-1\Big)=\tfrac12$

$$\boxed{\text{centroid of the volume}=\big(\tfrac12,0,0\big)}$$

---

# Part C: Specimen Test 9

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 9), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Indefinite integrals
**(a)** $\int\frac{x}{1+x^2}\,\mathrm dx=\tfrac12\int\frac{2x}{1+x^2}\,\mathrm dx=\boxed{\tfrac12\ln(1+x^2)+C}$

**(b)** With $u=\cos x$ and $\mathrm du=-\sin x\,\mathrm dx$:
$$\int\cos^4x\sin x\,\mathrm dx=-\int u^4\,\mathrm du=\boxed{-\tfrac15\cos^5x+C}$$

## Q2: $\int_0^1\frac{x^2}{(1+x^3)^2}\,\mathrm dx$
Let $u=1+x^3$, so $\mathrm du=3x^2\,\mathrm dx$. The limits become $u=1\to2$:
$$\frac13\int_1^2u^{-2}\,\mathrm du=\frac13\Big[-\frac1u\Big]_1^2=\frac13\cdot\frac12=\boxed{\tfrac16}$$

## Q3: $\int_0^1\frac{x^3}{\sqrt{x^2+1}}\,\mathrm dx$ with $u^2=1+x^2$
Differentiating gives $u\,\mathrm du=x\,\mathrm dx$, and $x^2=u^2-1$. The limits become $u=1\to\sqrt2$:
$$\int_1^{\sqrt2}\frac{(u^2-1)\,u\,\mathrm du}{u}=\Big[\frac{u^3}3-u\Big]_1^{\sqrt2}=\Big(\frac{2\sqrt2}3-\sqrt2\Big)-\Big(\frac13-1\Big)=\boxed{\frac{2-\sqrt2}3\approx0.1953}$$

## Q4: Volume under $y=x^2+\frac1x$ on $[1,2]$, rotated about the $x$-axis
$$V=\pi\int_1^2\Big(x^4+2x+\frac1{x^2}\Big)\mathrm dx=\pi\Big[\frac{x^5}5+x^2-\frac1x\Big]_1^2=\pi\Big[\Big(\frac{32}5+4-\frac12\Big)-\Big(\frac15+1-1\Big)\Big]=\boxed{\frac{97\pi}{10}\approx30.47}$$

## Q5: The area under $y=\sin x$ on $[0,\pi]$
**(i)** $A=\int_0^\pi\sin x\,\mathrm dx=\big[-\cos x\big]_0^\pi=\boxed2$.

**(ii)**
- $\bar x=\frac1A\int_0^\pi x\sin x\,\mathrm dx=\frac12\big[\sin x-x\cos x\big]_0^\pi=\frac\pi2$. This is expected by symmetry.
- $\bar y=\frac1{2A}\int_0^\pi\sin^2x\,\mathrm dx=\frac14\cdot\frac\pi2=\frac\pi8$.

$$\boxed{(\bar x,\bar y)=\big(\tfrac\pi2,\tfrac\pi8\big)\approx(1.571,\,0.393)}$$

## Sources
- Transcribed problem statements: `tmp/md/module_09_integration_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §8.8–8.9; MATH1054 Module Booklet, Module 9; [[Integration Formulae]]
