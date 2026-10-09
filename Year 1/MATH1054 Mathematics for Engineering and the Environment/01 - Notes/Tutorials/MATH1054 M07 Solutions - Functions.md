---
title: "MATH1054 M07 Solutions - Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 1: Calculus"
tags:
  - math1054
  - tutorial-solutions
  - functions
  - hyperbolic-functions
sheet: "Module 07 work scheme: Examples 2.1–2.61, 8.17(f–h), 8.18(b), 8.20; Exercises 10, 14, 35, 40, 41, 68, 75–77, 81; Specimen Test 7"
theory_notes: ["[[MATH1054 M07 - Functions]]"]
key_concepts: ["[[Inverse Functions]]", "[[Even, Odd and Periodic Functions]]", "[[Inverse Trigonometric Functions]]", "[[Hyperbolic Functions]]"]
status: complete
sources: ["tmp/md/module_07_functions.md", "02 - Sources/Modern Engineering Mathematics.pdf (§2.2, §2.6–2.7, §8.3.9–8.3.12)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 7)"]
---

# MATH1054 M07 Solutions - Functions

> [!abstract] Sheet Info
> The whole Module 07 work scheme plus Specimen Test 7. Numerical values were checked in Python, and derivatives with SymPy. Sketches are drawn with matplotlib from the exact formulae.
>
> Conventions:
> - $\sin^{-1}$ has range $[-\frac\pi2,\frac\pi2]$.
> - $\cos^{-1}$ has range $[0,\pi]$.
> - $\tan^{-1}$ has range $(-\frac\pi2,\frac\pi2)$.

## Theory Links
- [[MATH1054 M07 - Functions]] · [[Inverse Functions]] · [[Even, Odd and Periodic Functions]] · [[Inverse Trigonometric Functions]] · [[Hyperbolic Functions]]

---

# Part A: Worked examples

## Example 2.1: Domain, codomain, range and values
**(a)** $f(x)=3x^2+1$
- Domain $\mathbb R$, codomain $\mathbb R$.
- Range $[1,\infty)$, because $x^2\ge0$.
- $f(2)=13$, $f(-3)=28$, and $f(-x)=3x^2+1=f(x)$, so $f$ is **even**.

**(b)** $f(x)=\sqrt{(x+4)(3-x)}$
- We need $(x+4)(3-x)\ge0$, so the domain is $\boxed{-4\le x\le3}$. The codomain is $\mathbb R$.
- The quadratic under the root peaks at the midpoint $x=-\tfrac12$, where it equals $\tfrac72\cdot\tfrac72$. So the range is $\boxed{[0,\tfrac72]}$.
- $f(2)=\sqrt{6\cdot1}=\sqrt6$.
- $f(-3)=\sqrt{1\cdot6}=\sqrt6$.
- $f(-x)=\sqrt{(4-x)(3+x)}$, which is defined for $-3\le x\le4$.

## Example 2.3: Celsius to Fahrenheit, $T_2=\frac95T_1+32$
**(a)** Physically the domain is $T_1\ge-273.15\,°\mathrm C$ (absolute zero), and the codomain is $\mathbb R$.
**(b)** The rule is $T_1\mapsto\frac95T_1+32$.
**(c)** The graph is a straight line with gradient $\frac95$ and intercept 32 (see the left panel of the Ex 2.8 figure).
**(d)** The range is $T_2\ge\frac95(-273.15)+32=-459.67\,°\mathrm F$.
**(e)** (i) $60°\mathrm C\to108+32=\boxed{140°\mathrm F}$ (ii) $0°\mathrm C\to\boxed{32°\mathrm F}$ (iii) $-50°\mathrm C\to-90+32=\boxed{-58°\mathrm F}$.

## Example 2.6: Inverse of $y=\frac15(4x-3)$
Swap the roles by solving for $x$: $5y=4x-3$, so $x=\frac{5y+3}4$. Hence
$$\boxed{f^{-1}(x)=\frac{5x+3}4}$$
**Check**: $f(f^{-1}(x))=\frac15\big(5x+3-3\big)=x$ ✔

## Example 2.7: Inverse of $y=\frac{x+2}{x+1}$, $x\neq-1$
$$y(x+1)=x+2\ \Rightarrow\ x(y-1)=2-y\ \Rightarrow\ x=\frac{2-y}{y-1}$$
$$\boxed{f^{-1}(x)=\frac{2-x}{x-1},\quad x\neq1}$$
The excluded value $x=1$ is the horizontal asymptote $y=1$ of $f$: its range omits 1.

## Example 2.8: Graphs of $f^{-1}$
The graph of $f^{-1}$ is the **reflection of the graph of $f$ in the line $y=x$**.

![[m1054_inverse_reflections.png|760]]

- **(a)** $f^{-1}(x)=\frac59(x-32)$: another straight line.
- **(b)** $f^{-1}(x)=\frac{2-x}{x-1}$: the asymptotes $x=-1$ and $y=1$ of $f$ swap to become $y=-1$ and $x=1$.
- **(c)** $f(x)=x^2$ is **not one-to-one** on $\mathbb R$ (e.g. $f(2)=f(-2)$), so it has no inverse there. Its reflection fails the vertical-line test. Restricting to $x\ge0$ gives $f^{-1}(x)=\sqrt x$.

## Example 2.9: Composite functions, $f=x^2+2x$, $g=x-1$
$$f(g(x))=(x-1)^2+2(x-1)=\boxed{x^2-1},\qquad g(f(x))=\boxed{x^2+2x-1}$$
Note that $f\circ g\neq g\circ f$ in general.

## Example 2.11: Odd, even or neither (Fig. 2.20)
- Even means $f(-x)=f(x)$: symmetric about the $y$-axis.
- Odd means $f(-x)=-f(x)$: rotational symmetry of $180°$ about O.

| Graph | Symmetry | Verdict |
|---|---|---|
| (a) peak $(0,4)$, cusps at $\pm1$ | mirror in the $y$-axis | **even** |
| (b) roots at $0,\pm1,\pm2$ | $180°$ rotation about O | **odd** |
| (c) through $(0,1)$, rising, asymptotic to the negative $x$-axis (like $e^x$) | neither | **neither** |
| (d) flat top at $y=1$ on $[-1,1]$, zero at $\pm2$ | mirror in the $y$-axis | **even** |

## Example 2.12: Periodic, even and odd extensions of the triangle on $[0,1]$
The given piece is $f(x)=3x$ on $[0,\tfrac13]$ and $f(x)=\tfrac32(1-x)$ on $[\tfrac13,1]$.
- **(a)** Period 1: repeat the triangle on every unit interval.
- **(b)** Period 2, even: reflect it into $[-1,0]$ as $f(-x)$, then repeat every 2.
- **(c)** Period 2, odd: rotate it into $[-1,0]$ as $-f(-x)$ (an inverted triangle), then repeat every 2.

![[m1054_periodic_extensions.png|760]]

These are exactly the half-range extensions of MATH2048 Fourier series ([[Half-Range Expansions]]).

## Example 2.50: Inverse trig values (radians, 4 d.p.)
| $x$ | $\sin^{-1}x$ | $\cos^{-1}x$ | $\tan^{-1}x$ |
|---|---|---|---|
| (a) $0.35$ | $0.3576$ | $1.2132$ | $0.3367$ |
| (b) $-0.7$ | $-0.7754$ | $2.3462$ | $-0.6107$ |

**Check**: $\sin^{-1}x+\cos^{-1}x=\frac\pi2=1.5708$ in both rows ✔. Also, $\cos^{-1}$ of a negative number lies in $(\frac\pi2,\pi)$.

## Example 2.51: $y=\sin^{-1}(\sin x)$
$\sin^{-1}$ returns the angle in $[-\frac\pi2,\frac\pi2]$ that has the same sine as $x$:
- $y=x$ on $[-\frac\pi2,\frac\pi2]$;
- $y=\pi-x$ on $[\frac\pi2,\frac{3\pi}2]$, since $\sin(\pi-x)=\sin x$;
- then repeat with period $2\pi$.

The result is a **triangular wave** of amplitude $\frac\pi2$. It is *not* $y=x$. See the left panel below, and Exercise 68 below.

![[m1054_inverse_trig_compositions.png|800]]

## Example 2.57: Logarithms
**(a)** $\log_232=\log_22^5=\boxed5$.

**(b)** $\frac13\log_28=\frac13\cdot3=1$, and $\log_2\frac27=1-\log_27$. So
$$\tfrac13\log_28-\log_2\tfrac27=1-(1-\log_27)=\boxed{\log_27\approx2.807}$$

**(c)**
$$\ln\frac{\sqrt{10x}}{y^2}=\boxed{\tfrac12\ln10+\tfrac12\ln x-2\ln y}$$

**(d)** By the change of base formula, $\dfrac{\log_{10}32}{\log_{10}2}=\log_232=\boxed5$.

**(e)**
$$\frac{\log_3x}{\log_9x}=\frac{\ln x/\ln3}{\ln x/\ln9}=\frac{\ln9}{\ln3}=\frac{2\ln3}{\ln3}=\boxed2$$

## Example 2.58: $f=A\cosh2x+B\sinh2x$, $f(0)=5$, $f(1)=0$
- $f(0)=A=5$, since $\cosh0=1$ and $\sinh0=0$.
- $f(1)=5\cosh2+B\sinh2=0$, so $B=-5\coth2$.

Then
$$f=\frac{5}{\sinh2}\big(\sinh2\cosh2x-\cosh2\sinh2x\big)=\boxed{\frac{5\sinh(2-2x)}{\sinh2}}$$
This uses the addition formula $\sinh(a-b)=\sinh a\cosh b-\cosh a\sinh b$.

## Example 2.59: $5\cosh x+3\sinh x=4$
Substitute the exponential definitions:
$$\tfrac52(e^x+e^{-x})+\tfrac32(e^x-e^{-x})=4e^x+e^{-x}=4$$
Multiply by $e^x$: $4e^{2x}-4e^x+1=(2e^x-1)^2=0$. So $e^x=\tfrac12$, giving
$$\boxed{x=-\ln2\approx-0.6931}$$
This is a repeated root: the curve just touches the line $y=4$.

## Example 2.60: $\tanh2x=\dfrac{2\tanh x}{1+\tanh^2x}$
Let $t=\tanh x=\dfrac{e^x-e^{-x}}{e^x+e^{-x}}$. Then
$$\frac{2t}{1+t^2}=\frac{2(e^x-e^{-x})(e^x+e^{-x})}{(e^x+e^{-x})^2+(e^x-e^{-x})^2}=\frac{2(e^{2x}-e^{-2x})}{2e^{2x}+2e^{-2x}}=\tanh2x\ ✔$$
**Osborn's rule**: start from $\tan2x=\dfrac{2\tan x}{1-\tan^2x}$. Replace each trig function by its hyperbolic counterpart, and change the sign of any term containing a product of two sines. Now $\tan^2x=\sin^2x/\cos^2x$ contains $\sin^2$, so $-\tan^2x$ becomes $+\tanh^2x$. This gives exactly the identity above ✔.

## Example 2.61: Inverse hyperbolics via logs (4 s.f.)
$$\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big),\quad\cosh^{-1}x=\ln\big(x+\sqrt{x^2-1}\big)\ (x\ge1),\quad\tanh^{-1}x=\tfrac12\ln\frac{1+x}{1-x}\ (|x|<1)$$
**(a)** $\sinh^{-1}0.5=\ln(0.5+\sqrt{1.25})=\ln1.61803=\boxed{0.4812}$.
**(b)** $\cosh^{-1}3=\ln(3+\sqrt8)=\ln5.82843=\boxed{1.763}$.
**(c)** $\tanh^{-1}(-0.4)=\tfrac12\ln\dfrac{0.6}{1.4}=\boxed{-0.4236}$.

The calculator agrees for all three.

## Example 8.17(f)–(h) and 8.18(b): Inverse-trig derivatives
Parts (a)–(e) and 8.18(a) are worked in [[MATH1054 M03 Solutions - Differentiation I|M03 Solutions]].
- **(f)** $\dfrac{\mathrm d}{\mathrm dx}\sin^{-1}6x=\dfrac{6}{\sqrt{1-36x^2}}$.
- **(g)** $\dfrac{\mathrm d}{\mathrm dx}x^2\cos^{-1}x=2x\cos^{-1}x-\dfrac{x^2}{\sqrt{1-x^2}}$.
- **(h)** $\dfrac{\mathrm d}{\mathrm dx}\tan^{-1}\dfrac{2x}{1+x^2}=\dfrac{2(1-x^2)}{x^4+6x^2+1}$.
- **8.18(b)** $\dfrac{\mathrm d}{\mathrm dx}\cos^{-1}\sqrt{1-x^2}=\dfrac{x}{|x|\sqrt{1-x^2}}$, which is $+\dfrac1{\sqrt{1-x^2}}$ for $0<x<1$.

## Example 8.20: Hyperbolic derivatives
**(a)** $\dfrac{\mathrm d}{\mathrm dx}\tanh2x=\boxed{2\,\mathrm{sech}^22x}$.

**(b)** $\dfrac{\mathrm d}{\mathrm dx}\cosh^2x=2\cosh x\sinh x=\boxed{\sinh2x}$.

**(c)** By the product rule:
$$\frac{\mathrm d}{\mathrm dx}e^{-3x}\sinh3x=-3e^{-3x}\sinh3x+3e^{-3x}\cosh3x=3e^{-3x}(\cosh3x-\sinh3x)=3e^{-3x}e^{-3x}=\boxed{3e^{-6x}}$$
This uses $\cosh u-\sinh u=e^{-u}$. Equivalently, $e^{-3x}\sinh3x=\tfrac12(1-e^{-6x})$.

**(d)** With $\frac{\mathrm d}{\mathrm du}\sinh^{-1}u=\frac1{\sqrt{1+u^2}}$ and $u=\frac{3x}4$:
$$\frac{3/4}{\sqrt{1+9x^2/16}}=\boxed{\frac{3}{\sqrt{16+9x^2}}}$$

---

# Part B: Assigned exercises

## Exercise 10(a),(c) (pp.81–82): Inverses
**(a)** $y=2x-3$ gives $x=\frac{y+3}2$, so $\boxed{f^{-1}(x)=\tfrac12(x+3)}$, defined on all of $\mathbb R$.

**(c)** $f(x)=x^2+1$ is **not one-to-one** on $\mathbb R$, because $f(-x)=f(x)$. So there is no inverse.
- **Restrict** to $x\ge0$. Then $y=x^2+1$ gives $x=\sqrt{y-1}$, so $\boxed{f^{-1}(x)=\sqrt{x-1},\ x\ge1}$.
- Restricting to $x\le0$ instead gives $f^{-1}(x)=-\sqrt{x-1}$.

## Exercise 14 (p.87): Odd or even (Fig. 2.27)
| Graph | Verdict | Reason |
|---|---|---|
| (a) cubic-like through O, point-symmetric | **odd** | $180°$ rotation about O maps it onto itself |
| (b) W-shape, maximum at $(0,0)$, symmetric | **even** | mirror in the $y$-axis |
| (c) line, positive slope, positive intercept | **neither** | $f(0)\neq0$ rules out odd, and a sloping line is not even |
| (d) through O, a maximum for $x<0$, increasing for $x>0$ | **neither** | no mirror symmetry and no point symmetry |

## Exercise 68 (p.149) (harder): Sketches
**(a)** $y=\sin^{-1}(\cos x)$. Since $\cos x=\sin(\frac\pi2-x)$, and $\frac\pi2-x\in[-\frac\pi2,\frac\pi2]$ when $x\in[0,\pi]$:
- $y=\frac\pi2-x$ on $[0,\pi]$.
- The function is **even** (because $\cos$ is), so $y=\frac\pi2-|x|$ on $[-\pi,\pi]$.
- It has period $2\pi$.

The result is a triangular wave between $-\frac\pi2$ and $\frac\pi2$, peaking at $x=0,\pm2\pi,\dots$

**(c)** $y=\cos^{-1}(\cos x)$. On $[0,\pi]$ this is simply $y=x$. It is even and has period $2\pi$, so $y=|x|$ on $[-\pi,\pi]$. The result is a triangular wave between $0$ and $\pi$.

Both are shown in the figure under Example 2.51.

## Exercise 75: Log expansions
(a) $\ln(x^2y)=2\ln x+\ln y$
(b) $\ln\sqrt{xy}=\tfrac12\ln x+\tfrac12\ln y$
(c) $\ln(x^5/y^2)=5\ln x-2\ln y$

## Exercise 76: Single logarithm
**(a)** $\ln14-\ln21+\ln6=\ln\dfrac{14\cdot6}{21}=\boxed{\ln4}$.
**(b)** $4\ln2-\tfrac12\ln25=\ln16-\ln5=\boxed{\ln\tfrac{16}5}$.

## Exercise 77: Simplify
**(a)** $\exp\Big\{\tfrac12\ln\dfrac{1-x}{1+x}\Big\}=\exp\Big\{\ln\Big(\dfrac{1-x}{1+x}\Big)^{1/2}\Big\}=\boxed{\sqrt{\dfrac{1-x}{1+x}}}$, for $-1<x<1$.
**(b)** $e^{2\ln x}=e^{\ln x^2}=\boxed{x^2}$, for $x>0$.

## Exercise 81(a),(e): Find the other five hyperbolic functions
Use $\cosh^2x-\sinh^2x=1$.

**(a)** $\cosh x=\tfrac54$.
- $\sinh^2x=\tfrac{25}{16}-1=\tfrac9{16}$, so $\sinh x=\pm\tfrac34$. The sign is that of $x$: $\cosh$ is even, so both $\pm x$ give $\cosh x=\tfrac54$.

| $\sinh x$ | $\tanh x$ | $\mathrm{sech}\,x$ | $\mathrm{cosech}\,x$ | $\coth x$ |
|---|---|---|---|---|
| $\pm\frac34$ | $\pm\frac35$ | $\frac45$ | $\pm\frac43$ | $\pm\frac53$ |

**(e)** $\mathrm{cosech}\,x=-\tfrac34$, so $\sinh x=-\tfrac43$ and $x<0$.
- $\cosh x=\sqrt{1+\tfrac{16}9}=\tfrac53$, always positive.

| $\sinh x$ | $\cosh x$ | $\tanh x$ | $\mathrm{sech}\,x$ | $\coth x$ |
|---|---|---|---|---|
| $-\frac43$ | $\frac53$ | $-\frac45$ | $\frac35$ | $-\frac54$ |

## Exercise 35(a),(c),(f) (p.586): Inverse-trig derivatives
**(a)**
$$\frac{\mathrm d}{\mathrm dx}\sin^{-1}\frac x2=\frac{1/2}{\sqrt{1-x^2/4}}=\boxed{\frac1{\sqrt{4-x^2}}}$$

**(c)** By the product rule:
$$\frac{\mathrm d}{\mathrm dx}\Big[\sqrt{1+x^2}\tan^{-1}x\Big]=\frac{x}{\sqrt{1+x^2}}\tan^{-1}x+\frac{\sqrt{1+x^2}}{1+x^2}=\boxed{\frac{1+x\tan^{-1}x}{\sqrt{1+x^2}}}$$

**(f)** By the product rule:
$$\frac{\mathrm d}{\mathrm dx}\Big[\sqrt{1-x^2}\sin^{-1}x\Big]=-\frac{x\sin^{-1}x}{\sqrt{1-x^2}}+\frac{\sqrt{1-x^2}}{\sqrt{1-x^2}}=\boxed{1-\frac{x\sin^{-1}x}{\sqrt{1-x^2}}}$$

## Exercise 40(c),(d) (p.591)
**(c)** $\dfrac{\mathrm d}{\mathrm dx}x^3\cosh2x=\boxed{3x^2\cosh2x+2x^3\sinh2x}$.

**(d)**
$$\frac{\mathrm d}{\mathrm dx}\ln\big(\cosh\tfrac12x\big)=\frac{\tfrac12\sinh\tfrac12x}{\cosh\tfrac12x}=\boxed{\tfrac12\tanh\tfrac12x}$$

## Exercise 41(a),(b) (p.591)
**(a)**
$$\frac{\mathrm d}{\mathrm dx}\sinh^{-1}2x=\boxed{\frac{2}{\sqrt{1+4x^2}}}$$

**(b)** $\cosh^{-1}(2x^2-1)$. The argument must be $\ge1$, so we need $|x|\ge1$. Using $\frac{\mathrm d}{\mathrm du}\cosh^{-1}u=\frac1{\sqrt{u^2-1}}$:
$$\frac{4x}{\sqrt{(2x^2-1)^2-1}}=\frac{4x}{\sqrt{4x^4-4x^2}}=\frac{4x}{2|x|\sqrt{x^2-1}}=\boxed{\frac{2}{\sqrt{x^2-1}}\ (x>1)}$$
For $x<-1$, the derivative is $-\dfrac{2}{\sqrt{x^2-1}}$.

---

# Part C: Specimen Test 7

## Q1: $f(x)=\dfrac{x^2+1}{\sqrt{x^2-1}}$
**(i)** We need $x^2-1>0$ (strictly, because it is in the denominator). So the domain is $\boxed{|x|>1}$, i.e. $(-\infty,-1)\cup(1,\infty)$.
**(ii)** $f(-x)=f(x)$, since only $x^2$ appears. So $f$ is **even**.

## Q2: The graph of $\cos^{-1}x$
**(i)** The domain is $[-1,1]$ and the range is $[0,\pi]$. The graph is decreasing, running from $(-1,\pi)$ through $(0,\frac\pi2)$ to $(1,0)$.
**(ii)** $\cos\frac{2\pi}3=-\frac12$, and $\frac{2\pi}3\in[0,\pi]$, so $\cos^{-1}\big(-\tfrac12\big)=\boxed{\tfrac{2\pi}3}$.

![[m1054_arccos_specimen.png|520]]

## Q3: Simplify $y=\exp\{\ln x-\tfrac12\ln(x-3)\}$ for $x>3$
$$y=\exp\Big\{\ln\frac{x}{\sqrt{x-3}}\Big\}=\boxed{\frac{x}{\sqrt{x-3}}}$$

## Q4: $\sinh x=-\tfrac5{12}$
(i) $\cosh x=\sqrt{1+\tfrac{25}{144}}=\boxed{\tfrac{13}{12}}$ ($\cosh>0$ always)
(ii) $\tanh x=\dfrac{-5/12}{13/12}=\boxed{-\tfrac5{13}}$
(iii) $\mathrm{sech}\,x=\boxed{\tfrac{12}{13}}$

## Q5: Proving $\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big)$
**(i)** $\sinh y=\dfrac{e^y-e^{-y}}2$.

**(ii)** $x=\dfrac{e^y-e^{-y}}2$. Multiply by $2e^y$: $2xe^y=e^{2y}-1$, which rearranges to
$$\boxed{(e^y)^2-2x\,e^y-1=0}$$

**(iii)** Solve this quadratic in $e^y$:
$$e^y=\frac{2x\pm\sqrt{4x^2+4}}2=x\pm\sqrt{x^2+1}$$
Since $\sqrt{x^2+1}>|x|$, the minus sign gives a **negative** value. That is impossible, because $e^y>0$. So $e^y=x+\sqrt{x^2+1}$, and
$$\boxed{\sinh^{-1}x=y=\ln\big(x+\sqrt{x^2+1}\big)}$$

## Q6: Differentiate
**(i)**
$$\frac{\mathrm d}{\mathrm dx}\tan^{-1}4x=\frac{4}{1+(4x)^2}=\boxed{\frac{4}{1+16x^2}}$$

**(ii)** $\dfrac{\mathrm d}{\mathrm dx}x^3\sinh x=\boxed{3x^2\sinh x+x^3\cosh x}$.

## Sources
- Transcribed problem statements: `tmp/md/module_07_functions.md`
- James, *Modern Engineering Mathematics* (6th ed.) §2.2, §2.6–2.7, §8.3.9–8.3.12; MATH1054 Module Booklet, Module 7
