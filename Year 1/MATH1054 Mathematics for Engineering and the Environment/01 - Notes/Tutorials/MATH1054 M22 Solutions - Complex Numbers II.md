---
title: "MATH1054 M22 Solutions - Complex Numbers II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 2: Complex Numbers"
tags:
  - math1054
  - tutorial-solutions
  - complex-numbers
  - de-moivre
  - loci
sheet: "Specimen Test 22 (booklet) + Module 22 work scheme: Examples 3.17–3.28; Exercises 29(a),(b), 30(a), 37, 38(a),(d), 40, 45(a),(c), 47(b); Booklet Exercise A"
theory_notes: ["[[MATH1054 M22 - Complex Numbers II]]"]
key_concepts: ["[[De Moivre's Theorem and Roots of Complex Numbers]]", "[[Complex Functions - Trig, Hyperbolic and Logarithm]]", "[[Loci in the Complex Plane]]"]
status: complete
sources: ["tmp/md/module_22_complex_numbers_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§3.2.9–3.2.12)"]
---

# MATH1054 M22 Solutions - Complex Numbers II

> [!abstract] Sheet Info
> The whole Module 22 work scheme. Numerical values were checked with Python `cmath`; quadratics and loci with SymPy.
>
> **Key identities**, for $z=x+\mathrm jy$:
> - $\sin z=\sin x\cosh y+\mathrm j\cos x\sinh y$
> - $\cos z=\cos x\cosh y-\mathrm j\sin x\sinh y$
> - $\sinh z=\sinh x\cos y+\mathrm j\cosh x\sin y$
> - $\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi)$

## Theory Links
- [[MATH1054 M22 - Complex Numbers II]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Complex Functions - Trig, Hyperbolic and Logarithm]] · [[Loci in the Complex Plane]]

---

# Part A: Worked examples

## Example 3.17: Complex trig and hyperbolic functions
**(a)**

$$\sin\big[\tfrac\pi4(1+\mathrm j)\big]=\sin\tfrac\pi4\cosh\tfrac\pi4+\mathrm j\cos\tfrac\pi4\sinh\tfrac\pi4=\tfrac1{\sqrt2}\big(1.3246+\mathrm j\,0.8687\big)=\boxed{0.9366+0.6142\mathrm j}$$

**(b)**

$$\sinh(3+4\mathrm j)=\sinh3\cos4+\mathrm j\cosh3\sin4=10.018(-0.6536)+\mathrm j\,10.068(-0.7568)=\boxed{-6.548-7.619\mathrm j}$$

**(c)** Use $\tan(x+\mathrm jy)=\dfrac{\sin2x+\mathrm j\sinh2y}{\cos2x+\cosh2y}$ with $x=\frac\pi4$ and $y=-3$:

$$\tan\big(\tfrac\pi4-3\mathrm j\big)=\frac{1-\mathrm j\,201.713}{0+201.716}=\boxed{0.00496-0.99999\mathrm j}$$

**(d)** $\cos z=2$. Write $\cos x\cosh y-\mathrm j\sin x\sinh y=2$ and equate parts:
- Imaginary: $\sin x\sinh y=0$. If $y=0$, then $\cos x=2$, which is impossible. So $\sin x=0$, and $x=n\pi$.
- Real: $\cos x\cosh y=2>0$, so we need $\cos x=+1$, i.e. $x=2k\pi$, and then $\cosh y=2$.

This gives $y=\pm\cosh^{-1}2=\pm\ln(2+\sqrt3)=\pm1.317$:

$$\boxed{z=2k\pi\pm1.317\,\mathrm j}$$

**(e)** $\tanh z=2$:

$$z=\tanh^{-1}2=\tfrac12\ln\frac{1+2}{1-2}=\tfrac12\ln(-3)=\tfrac12\big[\ln3+\mathrm j(\pi+2k\pi)\big]$$

$$\boxed{z=0.5493+\mathrm j\big(\tfrac\pi2+k\pi\big)}$$

## Example 3.18: $\ln(-3+4\mathrm j)$
$|z|=5$, and the argument is in Q2: $\pi-\tan^{-1}\frac43=2.2143$. So

$$\ln(-3+4\mathrm j)=\ln5+\mathrm j(2.2143+2k\pi)$$

The principal value is $\boxed{1.6094+2.2143\mathrm j}$.

## Example 3.19: $(1-\mathrm j)^{12}$
$1-\mathrm j=\sqrt2\big[\cos(-\tfrac\pi4)+\mathrm j\sin(-\tfrac\pi4)\big]$. By De Moivre:

$$(1-\mathrm j)^{12}=(\sqrt2)^{12}\big[\cos(-3\pi)+\mathrm j\sin(-3\pi)\big]=64(-1)=\boxed{-64}$$

## Example 3.20: Roots of $z=-\frac12+\frac12\mathrm j$
In polar form, $z=\frac1{\sqrt2}\angle\frac{3\pi}4$. The $n$ $n$th roots have modulus $r^{1/n}$ and arguments $\frac{\theta+2k\pi}{n}$ for $k=0,\dots,n-1$.

**(a)** $z^{1/2}$: modulus $2^{-1/4}=0.8409$, arguments $\frac{3\pi}8$ and $\frac{3\pi}8+\pi$:

$$\boxed{\pm(0.3218+0.7769\mathrm j)}$$

These are $67.5°$ and $247.5°$.

**(b)** $z^{1/3}$: modulus $2^{-1/6}=0.8909$, arguments $\frac\pi4,\ \frac{11\pi}{12},\ \frac{19\pi}{12}$ ($45°,165°,285°$):

$$\boxed{0.6300+0.6300\mathrm j,\quad-0.8605+0.2306\mathrm j,\quad0.2306-0.8605\mathrm j}$$

On the Argand diagram, the roots are equally spaced on the circle of radius $r^{1/n}$.

![[m1054_complex_roots.png|800]]

## Example 3.21: $(-\frac12+\frac12\mathrm j)^{-2/3}$
Take the modulus to the power $-\frac23$: $(2^{-1/2})^{-2/3}=2^{1/3}=1.2599$. The arguments are $-\frac23\big(\frac{3\pi}4+2k\pi\big)=-\frac\pi2-\frac{4k\pi}3$. Reduced mod $2\pi$, these are $-90°$, $30°$ and $150°$:

$$\boxed{-1.2599\mathrm j,\quad1.0911+0.6300\mathrm j,\quad-1.0911+0.6300\mathrm j}$$

There are three distinct values, because the denominator of $\frac23$ is 3.

## Example 3.22: $z^2+(2\mathrm j-3)z+(5-\mathrm j)=0$
The discriminant is $\Delta=(2\mathrm j-3)^2-4(5-\mathrm j)=(5-12\mathrm j)-(20-4\mathrm j)=-15-8\mathrm j$.

**Square root of $\Delta$**: write $(a+b\mathrm j)^2=-15-8\mathrm j$. Then:
- $a^2-b^2=-15$
- $2ab=-8$
- $a^2+b^2=|\Delta|=17$

So $a^2=1$ and $b^2=16$. With $ab<0$, $\sqrt\Delta=\pm(1-4\mathrm j)$. Then

$$z=\frac{(3-2\mathrm j)\pm(1-4\mathrm j)}2=\boxed{2-3\mathrm j\ \text{ or }\ 1+\mathrm j}$$

**Check** with Vieta: the sum is $3-2\mathrm j=-(2\mathrm j-3)$ ✔, and the product is $(2-3\mathrm j)(1+\mathrm j)=5-\mathrm j$ ✔.

## Example 3.25: Loci
Put $z=x+\mathrm jy$.

| | Locus | Cartesian form | Description |
|---|---|---|---|
| (a) | $\operatorname{Re}z=4$ | $x=4$ | vertical line |
| (b) | $\arg(z-1-\mathrm j)=\frac\pi4$ | $y-1=x-1$ with $x>1$ | **half-line** from $(1,1)$ at $45°$, with the endpoint excluded |
| (c) | $\lvert z-2\mathrm j\rvert=\lvert z-1\rvert$ | $x^2+(y-2)^2=(x-1)^2+y^2$, i.e. $2x-4y+3=0$ | perpendicular bisector of $2\mathrm j$ and $1$ |
| (d) | $\operatorname{Im}\big((1-2\mathrm j)z\big)=3$ | $(1-2\mathrm j)(x+\mathrm jy)$ has imaginary part $y-2x$, so $y=2x+3$ | straight line |

## Example 3.26: $|z-(2+3\mathrm j)|=2$
This is a circle with centre $(2,3)$ and radius 2:

$$\boxed{(x-2)^2+(y-3)^2=4}\quad\Longleftrightarrow\quad x^2+y^2-4x-6y+9=0$$

## Example 3.27: $\left|\dfrac{z-\mathrm j}{z-1-2\mathrm j}\right|=\sqrt2$ (a circle of Apollonius)
Square both sides:

$$x^2+(y-1)^2=2\big[(x-1)^2+(y-2)^2\big]\ \Rightarrow\ x^2+y^2-4x-6y+9=0$$

So $\boxed{(x-2)^2+(y-3)^2=4}$. Remarkably, this is the **same circle as Example 3.26**.

## Example 3.28: $\operatorname{Re}\dfrac{z-\mathrm j}{z+1}=0$
Multiply the top and bottom by $\overline{z+1}$. The real part of the numerator must vanish:

$$\operatorname{Re}\big[(x+\mathrm j(y-1))(x+1-\mathrm jy)\big]=x(x+1)+y(y-1)=0$$

$$\boxed{\big(x+\tfrac12\big)^2+\big(y-\tfrac12\big)^2=\tfrac12}$$

This is a circle with centre $(-\frac12,\frac12)$ and radius $\frac1{\sqrt2}$, **excluding** $z=-1$, where the expression is undefined.

![[m1054_complex_loci.png|800]]

---

# Part B: Assigned exercises

## Exercise 29
**(a)**

$$\sin\big(\tfrac56\pi+\mathrm j\big)=\sin\tfrac{5\pi}6\cosh1+\mathrm j\cos\tfrac{5\pi}6\sinh1=\tfrac12(1.5431)-\mathrm j\tfrac{\sqrt3}2(1.1752)=\boxed{0.7715-1.0178\mathrm j}$$

**(b)** $\cos(\mathrm j\tfrac34)=\cosh\tfrac34=\boxed{1.2947}$. It is real, because $\cos\mathrm jy=\cosh y$.

## Exercise 30(a) (harder): Solve $\sin z=2$
Write $\sin x\cosh y+\mathrm j\cos x\sinh y=2$ and equate parts:
- Imaginary: $\cos x\sinh y=0$. If $y=0$, then $\sin x=2$, which is impossible. So $\cos x=0$, and $x=\frac\pi2+n\pi$.
- Real: $\sin x\cosh y=2>0$, so we need $\sin x=+1$, i.e. $x=\frac\pi2+2k\pi$, and then $\cosh y=2$.

$$\boxed{z=\tfrac\pi2+2k\pi\pm\mathrm j\ln(2+\sqrt3)=\tfrac\pi2+2k\pi\pm1.317\,\mathrm j}$$

## Booklet Exercise A: All values of the logarithms
**(a)** $|5+12\mathrm j|=13$ and $\operatorname{Arg}=\tan^{-1}\frac{12}5=1.1760$. So

$$\ln(5+12\mathrm j)=\ln13+\mathrm j(1.1760+2k\pi)=\boxed{2.5649+\mathrm j(1.1760+2k\pi)},\quad k\in\mathbb Z$$

**(b)** $-\frac12-\frac{\sqrt3}2\mathrm j$ has modulus 1 and argument $-\frac{2\pi}3$ (Q3). So

$$\ln\big(-\tfrac12-\tfrac{\sqrt3}2\mathrm j\big)=0+\mathrm j\Big(-\frac{2\pi}3+2k\pi\Big)=\boxed{\mathrm j\Big(2k\pi-\frac{2\pi}{3}\Big)}$$

All the values are purely imaginary, because the modulus is 1.

## Exercise 37: The three values of $(8+8\mathrm j)^{1/3}$
$8+8\mathrm j=8\sqrt2\angle\frac\pi4$. The cube roots have modulus $(8\sqrt2)^{1/3}=2^{7/6}=2.2449$ and arguments $\frac\pi{12},\ \frac{3\pi}4,\ \frac{17\pi}{12}$ ($15°,135°,255°$):

$$\boxed{2.1684+0.5810\mathrm j,\quad-1.5874+1.5874\mathrm j,\quad-0.5810-2.1684\mathrm j}$$

These form an equilateral triangle on the circle of radius 2.245 (see the figure above).

## Exercise 38: Polar forms
**(a)** $\sqrt3-\mathrm j=2\angle(-\frac\pi6)$. The fourth roots have modulus $2^{1/4}=1.1892$ and arguments $-\frac\pi{24}+\frac{k\pi}2$:

$$\boxed{2^{1/4}\angle\Big(-\tfrac{\pi}{24}\Big),\ 2^{1/4}\angle\tfrac{11\pi}{24},\ 2^{1/4}\angle\tfrac{23\pi}{24},\ 2^{1/4}\angle\Big(-\tfrac{13\pi}{24}\Big)}$$

**(d)** $-1=1\angle\pi$. The fourth roots are $1\angle\frac{\pi+2k\pi}4$:

$$\boxed{\angle\tfrac\pi4,\ \angle\tfrac{3\pi}4,\ \angle\Big(-\tfrac{3\pi}4\Big),\ \angle\Big(-\tfrac\pi4\Big)}=\frac{\pm1\pm\mathrm j}{\sqrt2}$$

## Exercise 40: $z^2-(3+5\mathrm j)z+8\mathrm j-5=0$
The discriminant is $\Delta=(3+5\mathrm j)^2-4(8\mathrm j-5)=(-16+30\mathrm j)+(20-32\mathrm j)=4-2\mathrm j$.

**Square root of $\Delta$**: write $(a+b\mathrm j)^2=4-2\mathrm j$. Then:
- $a^2-b^2=4$
- $ab=-1$
- $a^2+b^2=|\Delta|=2\sqrt5$

So $a^2=2+\sqrt5$ and $b^2=\sqrt5-2$, giving $\sqrt\Delta=\pm\big(2.0582-0.4859\mathrm j\big)$. Then

$$z=\frac{(3+5\mathrm j)\pm(2.0582-0.4859\mathrm j)}{2}=\boxed{2.529+2.257\mathrm j\ \text{ or }\ 0.471+2.743\mathrm j}$$

In exact form: $z=\dfrac{3\pm\sqrt{2+\sqrt5}}2+\mathrm j\,\dfrac{5\mp\sqrt{\sqrt5-2}}2$.

**Check** with Vieta: the sum is $3+5\mathrm j$ ✔, and the product is $(2.529+2.257\mathrm j)(0.471+2.743\mathrm j)=-5.00+8.00\mathrm j$ ✔.

## Exercise 45: Identify and sketch the loci
**(a)** $\operatorname{Re}\dfrac{z+\mathrm j}{z-\mathrm j}=1$. Multiply the top and bottom by $\overline{z-\mathrm j}$:

$$\frac{\operatorname{Re}\big[(z+\mathrm j)(\bar z+\mathrm j)\big]}{|z-\mathrm j|^2}=\frac{x^2+y^2-1}{x^2+(y-1)^2}=1$$

This gives $x^2+y^2-1=x^2+y^2-2y+1$, so $\boxed{y=1}$: the horizontal line through $\mathrm j$, **with the point $z=\mathrm j$ removed**. Check: on $y=1$, $\frac{x+2\mathrm j}{x}=1+\frac{2\mathrm j}{x}$, which has real part 1 ✔.

**(c)** $\left|\dfrac{z+\mathrm j}{z-\mathrm j}\right|=3$. Square both sides:

$$x^2+(y+1)^2=9\big[x^2+(y-1)^2\big]\ \Rightarrow\ 8x^2+8y^2-20y+8=0\ \Rightarrow\ \boxed{x^2+\big(y-\tfrac54\big)^2=\big(\tfrac34\big)^2}$$

This is a circle (of Apollonius) with centre $(0,\frac54)$ and radius $\frac34$. It encloses $\mathrm j$ but not $-\mathrm j$.

## Exercise 47(b): $|2z-1|=3$
$|2z-1|=2\,|z-\tfrac12|=3$, so $|z-\tfrac12|=\tfrac32$:

$$\boxed{\big(x-\tfrac12\big)^2+y^2=\tfrac94}$$

This is a circle with centre $(\frac12,0)$ and radius $\frac32$.

---

# Part C: Specimen Test 22

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 22), then solved and checked with SymPy, NumPy or SciPy.

## Q1: $\sin\big(\frac\pi2+\mathrm j\big)$
Use the addition formula, with $\cos\mathrm j=\cosh1$ and $\sin\mathrm j=\mathrm j\sinh1$:

$$\sin\tfrac\pi2\cos\mathrm j+\cos\tfrac\pi2\sin\mathrm j=\cosh1+0$$

So $\boxed{\operatorname{Re}=\cosh1\approx1.5431,\ \operatorname{Im}=0}$.

## Q2: $\ln(-3)$
$-3=3e^{\mathrm j\pi}$, so $\ln(-3)=\ln3+\mathrm j(\pi+2k\pi)$. The principal value has

$$\boxed{\operatorname{Re}=\ln3\approx1.0986,\quad\operatorname{Im}=\pi}$$

## Q3: The cube roots of $z=4\sqrt2(1-\mathrm j)$
**(i)** $|z|=4\sqrt2\cdot\sqrt2=8$ and $\arg z=-\frac\pi4$, so $z=8e^{-\mathrm j\pi/4}$. The cube roots are

$$z^{1/3}=2e^{\mathrm j(-\pi/4+2k\pi)/3}=\boxed{2e^{-\mathrm j\pi/12},\ 2e^{\mathrm j7\pi/12},\ 2e^{-\mathrm j3\pi/4}}$$

**(ii)**
- $2e^{-\mathrm j\pi/12}=1.932-0.518\mathrm j$
- $2e^{\mathrm j7\pi/12}=-0.518+1.932\mathrm j$
- $2e^{-\mathrm j3\pi/4}=-\sqrt2-\mathrm j\sqrt2$

**(iii)** The roots are equally spaced ($120°$ apart) on the circle $|z|=2$:

![[m1054_spec22_roots.png|480]]

## Q4: $2\cos n\theta=z^n+z^{-n}$ and $2\mathrm j\sin n\theta=z^n-z^{-n}$
By De Moivre:
- $z^n=\cos n\theta+\mathrm j\sin n\theta$
- $z^{-n}=\cos(-n\theta)+\mathrm j\sin(-n\theta)=\cos n\theta-\mathrm j\sin n\theta$

Adding gives $z^n+z^{-n}=2\cos n\theta$. Subtracting gives $z^n-z^{-n}=2\mathrm j\sin n\theta$ ✔.

## Q5: $\left|\frac{z+2\mathrm j}{z-\mathrm j}\right|=2$
Square both sides:

$$x^2+(y+2)^2=4\big[x^2+(y-1)^2\big]\ \Rightarrow\ 3x^2+3y^2-12y=0\ \Rightarrow\ \boxed{x^2+(y-2)^2=4}$$

This is a circle with centre $2\mathrm j$ and radius 2 (a circle of Apollonius).

## Sources
- Transcribed problem statements: `tmp/md/module_22_complex_numbers_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §3.2.9–3.2.12; MATH1054 Module Booklet, Module 22
