---
title: "MATH1054 M10 Solutions - Integration III"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - integration
  - partial-fractions
  - improper-integrals
sheet: "Specimen Test 10 (booklet) + Module 10 work scheme: Examples 8.53, 9.1, 9.2, 9.4; Exercises 105(e), 106(f),(l), 117(a),(d),(f),(i), 1(e),(g) (§9.2.3)"
theory_notes: ["[[MATH1054 M10 - Integration III]]"]
key_concepts: ["[[Partial Fractions]]", "[[Completing the Square]]", "[[Improper Integrals]]"]
status: complete
sources: ["tmp/md/module_10_integration_iii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§2.3.x partial fractions, §8.8, §9.2)"]
---

# MATH1054 M10 Solutions - Integration III

> [!abstract] Sheet Info
> The whole Module 10 work scheme. Checks:
> - partial fractions: SymPy `apart`;
> - antiderivatives: `integrate`;
> - improper integrals: SymPy with infinite limits.
>
> Logs of possibly negative quantities are written $\ln|\cdot|$.

## Theory Links
- [[MATH1054 M10 - Integration III]] · [[Partial Fractions]] · [[Completing the Square]] · [[Improper Integrals]]

---

# Part A: Worked examples

## Example 8.53: Partial fractions
**(a)** $\displaystyle\int\frac{6}{x^2-2x-8}\,\mathrm dx$. The denominator factorises as $(x-4)(x+2)$. Write
$$\frac{6}{(x-4)(x+2)}=\frac{A}{x-4}+\frac{B}{x+2}.$$
**Cover-up rule**: to find $A$, cover the $(x-4)$ factor and set $x=4$, giving $A=\frac6{6}=1$. Likewise $x=-2$ gives $B=\frac6{-6}=-1$.
$$\int\Big(\frac1{x-4}-\frac1{x+2}\Big)\mathrm dx=\boxed{\ln\Big|\frac{x-4}{x+2}\Big|+C}$$

**(b)** $\displaystyle\int\frac{9}{(x-1)(x+2)^2}\,\mathrm dx$. A **repeated** factor needs one term for each power:
$$\frac9{(x-1)(x+2)^2}=\frac A{x-1}+\frac B{x+2}+\frac C{(x+2)^2}$$
- $x=1$: $A=\frac9{9}=1$.
- $x=-2$: $C=\frac{9}{-3}=-3$.
- Compare the $x^2$ coefficients in $9=A(x+2)^2+B(x-1)(x+2)+C(x-1)$: $0=A+B$, so $B=-1$.
$$\int\Big(\frac1{x-1}-\frac1{x+2}-\frac3{(x+2)^2}\Big)\mathrm dx=\boxed{\ln\Big|\frac{x-1}{x+2}\Big|+\frac{3}{x+2}+C}$$

**(c)** $\displaystyle\int_0^6\frac{\mathrm dx}{x^2+5x+6}$. Here $\frac{1}{(x+2)(x+3)}=\frac1{x+2}-\frac1{x+3}$, so
$$\Big[\ln\frac{x+2}{x+3}\Big]_0^6=\ln\frac89-\ln\frac23=\ln\frac{8}{9}\cdot\frac32=\boxed{\ln\tfrac43\approx0.2877}$$

## Example 9.1: Improper integrals where the integrand is unbounded at an endpoint
Define $\displaystyle\int_0^1f\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_\varepsilon^1f\,\mathrm dx$.

**(a)**
$$\int_\varepsilon^1x^{-2/3}\,\mathrm dx=\big[3x^{1/3}\big]_\varepsilon^1=3-3\varepsilon^{1/3}\to\boxed3$$
It converges because the power $\frac23<1$.

**(b)** The integrand is unbounded at $x=1$:
$$\int_0^{1-\varepsilon}\frac{\mathrm dx}{\sqrt{1-x^2}}=\sin^{-1}(1-\varepsilon)\to\boxed{\frac\pi2}$$

**(c)** By parts, $\int\ln x\,\mathrm dx=x\ln x-x$. Then
$$\int_\varepsilon^1\ln x\,\mathrm dx=(0-1)-(\varepsilon\ln\varepsilon-\varepsilon)\to\boxed{-1}$$
This uses the standard limit $\varepsilon\ln\varepsilon\to0$, because $\varepsilon$ beats the log.

**(d)**
$$\int_\varepsilon^1x^{-2}\,\mathrm dx=\Big[-\frac1x\Big]_\varepsilon^1=-1+\frac1\varepsilon\to\infty$$
So it is **not defined** (divergent), because the power $2\ge1$.

## Example 9.2: $\int_{-1}^1x^{-2}\,\mathrm dx$ is not defined
The integrand is unbounded at the **interior** point $x=0$, so split the range there:
$$\int_{-1}^1=\int_{-1}^0+\int_0^1$$
Each piece diverges (Ex 9.1(d)), so the integral is not defined.

> [!warning] The trap
> Ignoring the singularity gives $\big[-\frac1x\big]_{-1}^{1}=-1-1=-2$. That is a **negative** answer for a **positive** integrand, so it is obviously wrong. Always check the integrand for singularities inside the range.

## Example 9.4: Infinite ranges
$\displaystyle\int_a^\infty f\,\mathrm dx=\lim_{R\to\infty}\int_a^Rf\,\mathrm dx$.

**(a)**
$$\int_1^Rx^{-3/2}\,\mathrm dx=\Big[-2x^{-1/2}\Big]_1^R=2-\frac2{\sqrt R}\to\boxed2$$
It converges because the power $\frac32>1$.

**(b)**
$$\int_0^R\frac{\mathrm dx}{1+x^2}=\tan^{-1}R\to\boxed{\frac\pi2}$$

**(c)** Use the cyclic by-parts result from [[MATH1054 M04 Solutions - Integration I|M04]]:
$$\int e^{-x}\sin x\,\mathrm dx=-\tfrac12e^{-x}(\sin x+\cos x)$$
$$\int_0^Re^{-x}\sin x\,\mathrm dx=\Big[-\tfrac12e^{-x}(\sin x+\cos x)\Big]_0^R\to0+\tfrac12=\boxed{\tfrac12}$$

**(d)** $\displaystyle\int_{-\infty}^\infty e^{3x}\exp(-e^x)\,\mathrm dx$. Let $u=e^x$, so $\mathrm du=e^x\,\mathrm dx$. The range $x\in(-\infty,\infty)$ becomes $u\in(0,\infty)$:
$$\int_0^\infty u^2e^{-u}\,\mathrm du$$
Integrate by parts twice:
$$\Big[-e^{-u}(u^2+2u+2)\Big]_0^\infty=0-(-2)=\boxed2$$
(This is $\Gamma(3)=2!$.)

---

# Part B: Assigned exercises

## Exercise 105(e): $\displaystyle\int_0^2\frac{\mathrm dx}{\sqrt{3+2x-x^2}}$
**Complete the square**: $3+2x-x^2=4-(x-1)^2$. This has the form $a^2-u^2$, which gives $\sin^{-1}$:
$$\int_0^2\frac{\mathrm dx}{\sqrt{4-(x-1)^2}}=\Big[\sin^{-1}\frac{x-1}{2}\Big]_0^2=\sin^{-1}\tfrac12-\sin^{-1}\big(-\tfrac12\big)=\frac\pi6+\frac\pi6=\boxed{\frac\pi3}$$

## Exercise 106(f): $\displaystyle\int\frac{\mathrm dx}{\sqrt{2x-x^2}}$
$2x-x^2=1-(x-1)^2$, so
$$\int\frac{\mathrm dx}{\sqrt{1-(x-1)^2}}=\boxed{\sin^{-1}(x-1)+C}$$

## Exercise 106(l): $\displaystyle\int\frac{\mathrm dx}{x^2+6x+13}$
$x^2+6x+13=(x+3)^2+4$, and $\int\frac{\mathrm du}{u^2+a^2}=\frac1a\tan^{-1}\frac ua$. So
$$\boxed{\tfrac12\tan^{-1}\frac{x+3}{2}+C}$$

## Exercise 117: Partial fractions
**(a)** $\dfrac{x}{x^2-3x-4}=\dfrac{x}{(x-4)(x+1)}$. Cover-up: at $x=4$, $A=\frac45$; at $x=-1$, $B=\frac{-1}{-5}=\frac15$.
$$\int=\boxed{\tfrac45\ln|x-4|+\tfrac15\ln|x+1|+C}$$

**(d)** $\dfrac{x}{(x+1)^2}$ has a repeated factor. Write $x=(x+1)-1$:
$$\frac{x}{(x+1)^2}=\frac1{x+1}-\frac1{(x+1)^2}$$
$$\int=\boxed{\ln|x+1|+\frac1{x+1}+C}$$

**(f)** $\dfrac1{x^2(x-1)}=\dfrac Ax+\dfrac B{x^2}+\dfrac C{x-1}$.
- $x=0$: $B=-1$.
- $x=1$: $C=1$.
- Compare the $x^2$ coefficients in $1=Ax(x-1)+B(x-1)+Cx^2$: $0=A+C$, so $A=-1$.
$$\int\Big(-\frac1x-\frac1{x^2}+\frac1{x-1}\Big)\mathrm dx=\boxed{\ln\Big|\frac{x-1}{x}\Big|+\frac1x+C}$$

**(i) (harder)** $\dfrac{2x^3}{x^3-1}$ is **improper** (degree of top = degree of bottom), so divide first:
$$\frac{2x^3}{x^3-1}=2+\frac{2}{x^3-1}$$
Factorise $x^3-1=(x-1)(x^2+x+1)$. The quadratic is irreducible, so it needs a **linear numerator**:
$$\frac2{(x-1)(x^2+x+1)}=\frac A{x-1}+\frac{Bx+C}{x^2+x+1}$$
- $x=1$: $A=\frac23$.
- Compare the $x^2$ coefficients in $2=A(x^2+x+1)+(Bx+C)(x-1)$: $0=A+B$, so $B=-\frac23$.
- Compare the constants: $2=A-C$, so $C=-\frac43$.

This gives $-\dfrac23\cdot\dfrac{x+2}{x^2+x+1}$. To integrate it, split the numerator into a multiple of the derivative of the denominator plus a constant: $x+2=\tfrac12(2x+1)+\tfrac32$. Then
$$\int\frac{x+2}{x^2+x+1}\,\mathrm dx=\tfrac12\ln(x^2+x+1)+\tfrac32\int\frac{\mathrm dx}{(x+\frac12)^2+\frac34}=\tfrac12\ln(x^2+x+1)+\sqrt3\tan^{-1}\frac{2x+1}{\sqrt3}$$
Putting it all together:
$$\boxed{\int\frac{2x^3}{x^3-1}\,\mathrm dx=2x+\tfrac23\ln|x-1|-\tfrac13\ln(x^2+x+1)-\tfrac{2}{\sqrt3}\tan^{-1}\frac{2x+1}{\sqrt3}+C}$$

## Exercise 1 (§9.2.3): Improper integrals
**(e)** $\displaystyle\int_0^1x^2(1-x^3)^{-1/2}\,\mathrm dx$. The integrand is unbounded at $x=1$. Let $u=1-x^3$, so $\mathrm du=-3x^2\,\mathrm dx$:
$$\frac13\int_0^1u^{-1/2}\,\mathrm du=\frac13\big[2u^{1/2}\big]_0^1=\boxed{\tfrac23}$$
This converges, since $u^{-1/2}$ is integrable at 0.

**(g)** $\displaystyle\int_0^{\pi/2}\frac{\sin x}{\sqrt{\cos x}}\,\mathrm dx$. The integrand is unbounded at $x=\frac\pi2$. Let $u=\cos x$, so $\mathrm du=-\sin x\,\mathrm dx$:
$$\int_0^1u^{-1/2}\,\mathrm du=\boxed2$$

---

# Part C: Specimen Test 10

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 10), then solved and checked with SymPy, NumPy or SciPy.

## Q1: $\int\frac{\mathrm dx}{4x^2+4x+2}$
Complete the square: $4x^2+4x+2=(2x+1)^2+1$. With $u=2x+1$ and $\mathrm du=2\,\mathrm dx$:
$$\int\frac{\mathrm dx}{(2x+1)^2+1}=\boxed{\tfrac12\tan^{-1}(2x+1)+C}$$

## Q2: Partial fractions
**(i)** $\dfrac{2x+1}{(x+2)(x+1)}=\dfrac{A}{x+2}+\dfrac{B}{x+1}$. Cover-up gives $A=\frac{-3}{-1}=3$ and $B=\frac{-1}{1}=-1$:
$$\int=\boxed{3\ln|x+2|-\ln|x+1|+C}$$

**(ii)** Write $x+3=(x+2)+1$, so $\dfrac{x+3}{(x+2)^2}=\dfrac1{x+2}+\dfrac1{(x+2)^2}$:
$$\int=\boxed{\ln|x+2|-\frac1{x+2}+C}$$

## Q3: $\int\frac{x^2}{x^2+1}\,\mathrm dx$
The fraction is improper, so divide: $\frac{x^2}{x^2+1}=1-\frac1{x^2+1}$.
$$\int=\boxed{x-\tan^{-1}x+C}$$

## Q4: $\int_1^\infty\frac{\mathrm dx}{\sqrt x}$
$$\int_1^Rx^{-1/2}\,\mathrm dx=2\sqrt R-2\to\infty$$
The integral **diverges**, so it is not defined. This agrees with the $p$-test: $p=\frac12\le1$ on an infinite range.

## Sources
- Transcribed problem statements: `tmp/md/module_10_integration_iii.md`
- James, *Modern Engineering Mathematics* (6th ed.) partial fractions §2.3; §8.8; §9.2; MATH1054 Module Booklet, Module 10
