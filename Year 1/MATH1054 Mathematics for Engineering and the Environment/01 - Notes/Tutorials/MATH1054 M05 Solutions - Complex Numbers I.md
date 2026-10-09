---
title: "MATH1054 M05 Solutions - Complex Numbers I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 2: Complex Numbers"
tags:
  - math1054
  - tutorial-solutions
  - complex-numbers
sheet: "Module 05 work scheme: Examples 3.1–3.16, 4.15; Exercises 1, 6, 8, 10, 12, 17, 24, 26, 27; Specimen Test 5"
theory_notes: ["[[MATH1054 M05 - Complex Numbers I]]"]
key_concepts: ["[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Euler's Formula]]", "[[Argand Diagram]]"]
status: complete
sources: ["tmp/md/module_05_complex_numbers_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§3.2)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 5)"]
---

# MATH1054 M05 Solutions - Complex Numbers I

> [!abstract] Sheet Info
> Every worked example, assigned exercise and Specimen Test 5 question for Module 05. James (and engineering generally) writes $\mathrm j^2=-1$.
>
> - **Principal argument**: $-\pi<\theta\le\pi$.
> - **Quadrant rule**: $\theta=\tan^{-1}(y/x)$ is only correct in quadrants 1 and 4. Add $\pi$ in Q2, and subtract $\pi$ in Q3.
> - Every value was checked with SymPy.

## Theory Links
- [[MATH1054 M05 - Complex Numbers I]] · [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Euler's Formula]] · [[Argand Diagram]]

---

# Part A: Worked examples

## Example 3.1 and Exercise 1: Argand diagrams
Plot $x+\mathrm jy$ as the point $(x,y)$.

![[m1054_argand_points.png|720]]

| Ex 3.1 | point | quadrant | Ex 1 | point | quadrant |
|---|---|---|---|---|---|
| (a) $3+\mathrm j2$ | $(3,2)$ | 1 | (a) $1+\mathrm j$ | $(1,1)$ | 1 |
| (b) $-5+\mathrm j3$ | $(-5,3)$ | 2 | (b) $\sqrt3-\mathrm j$ | $(1.73,-1)$ | 4 |
| (c) $8-\mathrm j5$ | $(8,-5)$ | 4 | (c) $-3+\mathrm j4$ | $(-3,4)$ | 2 |
| (d) $-2-\mathrm j3$ | $(-2,-3)$ | 3 | (d) $1-\mathrm j\sqrt3$ | $(1,-1.73)$ | 4 |
| | | | (e) $-1+\mathrm j\sqrt3$ | $(-1,1.73)$ | 2 |
| | | | (f) $-1-\mathrm j\sqrt3$ | $(-1,-1.73)$ | 3 |

Points (d), (e) and (f) of Exercise 1 all have modulus 2. They lie on the circle $|z|=2$ at angles $-60°$, $120°$ and $-120°$.

## Example 3.2: Equal complex numbers
Two complex numbers are equal **iff** their real parts are equal **and** their imaginary parts are equal.

$$z_1=(3a+2)+\mathrm j(3b-1),\qquad z_2=(b+1)-\mathrm j(a+2-b)$$

- Real parts: $3a+2=b+1$, so $b=3a+1$.
- Imaginary parts: $3b-1=-(a+2-b)$, so $2b=-a-1$.

Substituting the first into the second: $6a+2=-a-1$, so $a=-\tfrac37$ and $b=-\tfrac27$.

**(a)** $\boxed{a=-\tfrac37,\ b=-\tfrac27}$.
**(b)** $\operatorname{Re}z_1=\operatorname{Re}z_2=3a+2=\tfrac57$ and $\operatorname{Im}z_1=\operatorname{Im}z_2=3b-1=-\tfrac{13}7$, so $z_1=z_2=\tfrac57-\mathrm j\tfrac{13}7$.

## Example 3.3
**(a)** $z_1+z_2=(3+5)+\mathrm j(2-3)=\boxed{8-\mathrm j}$.
**(b)** $z_1-z_2=(3-5)+\mathrm j(2+3)=\boxed{-2+\mathrm j5}$.

## Example 3.4

$$z_1z_2=(3+\mathrm j2)(5+\mathrm j3)=15+\mathrm j9+\mathrm j10+\mathrm j^2\,6=\boxed{9+\mathrm j19}$$

## Example 3.5
To divide, multiply the top and bottom by the conjugate of the denominator:

$$\frac{3+\mathrm j2}{5+\mathrm j3}\cdot\frac{5-\mathrm j3}{5-\mathrm j3}=\frac{15-\mathrm j9+\mathrm j10+6}{25+9}=\frac{21+\mathrm j}{34}=\boxed{\tfrac{21}{34}+\mathrm j\tfrac1{34}}$$

## Example 3.6: $z+1/z$ for $z=\dfrac{2+\mathrm j}{1-\mathrm j}$
First simplify $z$:

$$z=\frac{(2+\mathrm j)(1+\mathrm j)}{(1-\mathrm j)(1+\mathrm j)}=\frac{2+3\mathrm j-1}{2}=\tfrac12+\tfrac32\mathrm j$$

Then find $1/z$:

$$\frac1z=\frac{1-\mathrm j}{2+\mathrm j}=\frac{(1-\mathrm j)(2-\mathrm j)}{5}=\frac{1-3\mathrm j}{5}=\tfrac15-\tfrac35\mathrm j$$

Add:

$$z+\frac1z=\Big(\tfrac12+\tfrac15\Big)+\mathrm j\Big(\tfrac32-\tfrac35\Big)=\tfrac7{10}+\mathrm j\tfrac9{10}$$

So $\boxed{\operatorname{Re}=\tfrac7{10},\ \operatorname{Im}=\tfrac9{10}}$.

## Example 3.10: Modulus and argument
Use $|z|=\sqrt{x^2+y^2}$. Find the reference angle $\alpha=\tan^{-1}|y/x|$, then place it in the correct quadrant.

| $z$ | quadrant | $\lvert z\rvert$ | $\alpha$ | $\arg z$ |
|---|---|---|---|---|
| (a) $3+\mathrm j2$ | 1 | $\sqrt{13}=3.606$ | $33.69°$ | $0.588$ rad ($33.69°$) |
| (b) $1-\mathrm j$ | 4 | $\sqrt2$ | $45°$ | $-\pi/4$ |
| (c) $-1+\mathrm j$ | 2 | $\sqrt2$ | $45°$ | $\pi-\pi/4=3\pi/4$ |
| (d) $-\sqrt6-\mathrm j\sqrt2$ | 3 | $\sqrt{6+2}=2\sqrt2$ | $\tan^{-1}\frac{1}{\sqrt3}=30°$ | $-(\pi-\pi/6)=-5\pi/6$ |

> [!warning] The classic slip
> For (c), $\tan^{-1}\!\big(\tfrac{1}{-1}\big)=-\pi/4$ on a calculator. But $-1+\mathrm j$ is in the **second** quadrant, so the argument is $3\pi/4$. Always sketch the point first.

## Example 3.11: Polar form $r(\cos\theta+\mathrm j\sin\theta)$
| $z$ | $r$ | $\theta$ | polar form |
|---|---|---|---|
| (a) $12+\mathrm j5$ | 13 | $\tan^{-1}\frac5{12}=0.3948$ rad ($22.62°$) | $13(\cos0.3948+\mathrm j\sin0.3948)$ |
| (b) $-3+\mathrm j4$ | 5 | $\pi-\tan^{-1}\frac43=2.2143$ rad ($126.87°$) | $5(\cos2.2143+\mathrm j\sin2.2143)$ |
| (c) $-4-\mathrm j3$ | 5 | $-(\pi-\tan^{-1}\frac34)=-2.4981$ rad ($-143.13°$) | $5(\cos(-2.4981)+\mathrm j\sin(-2.4981))$ |

## Example 3.12: $|z_1z_2|$ and $\arg(z_1z_2)$ for $z_1=-12+\mathrm j5$, $z_2=-4+\mathrm j3$
Use (3.5a) and (3.5b): $|z_1z_2|=|z_1||z_2|$ and $\arg(z_1z_2)=\arg z_1+\arg z_2$.
- $|z_1|=13$ and $|z_2|=5$, so $|z_1z_2|=\boxed{65}$.
- $\arg z_1=\pi-\tan^{-1}\frac5{12}=2.7468$ and $\arg z_2=\pi-\tan^{-1}\frac34=2.4981$. Their sum is $5.2449$ rad.
- This exceeds $\pi$, so subtract $2\pi$: $\arg(z_1z_2)=\boxed{-1.0383\ \text{rad}\ (-59.49°)}$.

**Check**: $z_1z_2=48-15\mathrm j-20\mathrm j+15\mathrm j^2=33-56\mathrm j$. Then $|33-56\mathrm j|=\sqrt{1089+3136}=65$ ✔, and $\tan^{-1}(-56/33)=-59.49°$ ✔ (fourth quadrant).

## Example 3.13: Division in polar form
$\dfrac{r_1\angle\theta_1}{r_2\angle\theta_2}=\dfrac{r_1}{r_2}\angle(\theta_1-\theta_2)$.

**(a)** $z_1=4\angle\frac\pi2$ and $z_2=9\angle\frac\pi3$:

$$\frac{z_1}{z_2}=\tfrac49\Big(\cos\tfrac\pi6+\mathrm j\sin\tfrac\pi6\Big)=\tfrac{2\sqrt3}9+\mathrm j\tfrac29,\qquad\frac{z_2}{z_1}=\tfrac94\Big(\cos\tfrac\pi6-\mathrm j\sin\tfrac\pi6\Big)=\tfrac{9\sqrt3}8-\mathrm j\tfrac98$$

**(b)** $z_1=1\angle\frac{3\pi}4$ and $z_2=2\angle\frac\pi8$:

$$\frac{z_1}{z_2}=\tfrac12\Big(\cos\tfrac{5\pi}8+\mathrm j\sin\tfrac{5\pi}8\Big)\approx-0.191+0.462\mathrm j,\qquad\frac{z_2}{z_1}=2\Big(\cos\tfrac{5\pi}8-\mathrm j\sin\tfrac{5\pi}8\Big)\approx-0.765-1.848\mathrm j$$

## Example 3.14: Modulus and argument of a product and quotient

$$z=\frac{(1+\mathrm j2)^2(4-\mathrm j3)^3}{(3+\mathrm j4)^4(2-\mathrm j)^3}$$

Moduli multiply and divide; arguments add and subtract.
- $|1+2\mathrm j|=\sqrt5$, $|4-3\mathrm j|=5$, $|3+4\mathrm j|=5$, $|2-\mathrm j|=\sqrt5$.

$$|z|=\frac{5\cdot125}{625\cdot5\sqrt5}=\frac1{5\sqrt5}=\boxed{\frac{\sqrt5}{25}\approx0.0894}$$

- $\arg(1+2\mathrm j)=1.1071$, $\arg(4-3\mathrm j)=-0.6435$, $\arg(3+4\mathrm j)=0.9273$, $\arg(2-\mathrm j)=-0.4636$.

$$\arg z=2(1.1071)+3(-0.6435)-4(0.9273)-3(-0.4636)=\boxed{-2.0344\ \text{rad}\ (-116.57°)}$$

This already lies in $(-\pi,\pi]$. So $z=\frac{\sqrt5}{25}\angle(-116.57°)=-\tfrac1{25}-\tfrac2{25}\mathrm j$ ✔ (SymPy).

## Example 3.15: Exponential form $re^{\mathrm j\theta}$
**(a)** $2+\mathrm j3$: $r=\sqrt{13}$ and $\theta=\tan^{-1}\frac32=0.9828$, so $\boxed{\sqrt{13}\,e^{\mathrm j0.983}}$.
**(b)** $-2+\mathrm j$ (second quadrant): $r=\sqrt5$ and $\theta=\pi-\tan^{-1}\frac12=2.6779$, so $\boxed{\sqrt5\,e^{\mathrm j2.678}}$.

## Example 3.16: $e^{2+\mathrm j\pi/3}$ in cartesian form

$$e^{2}e^{\mathrm j\pi/3}=e^2\Big(\cos\tfrac\pi3+\mathrm j\sin\tfrac\pi3\Big)=\tfrac12e^2+\mathrm j\tfrac{\sqrt3}2e^2=\boxed{3.695+\mathrm j6.399}$$

## Example 4.15: Square on OP, with $\vec{\mathrm{OP}}=(1,2)$, in quadrants 1 and 2
Treat $\vec{\mathrm{OP}}$ as $p=1+2\mathrm j$. Multiplying by $\mathrm j$ rotates a vector by $+90°$ without changing its length.
- The adjacent side from O is $\mathrm jp=\mathrm j-2=-2+\mathrm j$, so R is $(-2,1)$.
- The fourth vertex is $p+\mathrm jp=-1+3\mathrm j$, so Q is $(-1,3)$.

$$\boxed{\text{vertices }(-2,1)\text{ and }(-1,3)}$$

Rotating by $-90°$ instead ($-\mathrm jp=2-\mathrm j$) would put a vertex at $(2,-1)$, in the fourth quadrant, which is not allowed.

**Check**: $|\mathrm{OR}|=\sqrt5=|\mathrm{OP}|$, and $\vec{\mathrm{OP}}\cdot\vec{\mathrm{OR}}=-2+2=0$ ✔

---

# Part B: Assigned exercises

## Exercise 6: Cartesian form
**(a)** $(5+3\mathrm j)(2-\mathrm j)=10-5\mathrm j+6\mathrm j+3=13+\mathrm j$. Subtracting $(3+\mathrm j)$ gives $\boxed{10}$.

**(b)** $(1-2\mathrm j)^2=1-4\mathrm j+4\mathrm j^2=\boxed{-3-4\mathrm j}$.

**(d)**

$$\frac{1-\mathrm j}{1+\mathrm j}=\frac{(1-\mathrm j)^2}{2}=\frac{1-2\mathrm j-1}{2}=\boxed{-\mathrm j}$$

**(f)** $(3-2\mathrm j)^2=9-12\mathrm j-4=\boxed{5-12\mathrm j}$.

**(g)**

$$\frac1{5-3\mathrm j}-\frac1{5+3\mathrm j}=\frac{(5+3\mathrm j)-(5-3\mathrm j)}{25+9}=\boxed{\tfrac{3}{17}\mathrm j}$$

## Exercise 8: Roots of polynomials
**(a)** $x^2+2x+2=0$:

$$x=\frac{-2\pm\sqrt{4-8}}{2}=\frac{-2\pm2\mathrm j}{2}=\boxed{-1\pm\mathrm j}$$

**(b)** $x^3+8=0$. One root is $x=-2$. Factor it out: $(x+2)(x^2-2x+4)=0$. Then

$$x=\frac{2\pm\sqrt{4-16}}{2}=1\pm\mathrm j\sqrt3.$$

$$\boxed{x=-2,\ 1+\mathrm j\sqrt3,\ 1-\mathrm j\sqrt3}$$

All three have modulus 2 and are spaced $120°$ apart. They are the three cube roots of $-8$ ([[MATH1054 M22 - Complex Numbers II|M22]]).

## Exercise 10: $z=2-3\mathrm j$
**(a)** $\mathrm jz=2\mathrm j-3\mathrm j^2=\boxed{3+2\mathrm j}$. Multiplying by $\mathrm j$ is a $90°$ rotation.

**(b)** $z^*=\boxed{2+3\mathrm j}$.

**(c)**

$$\frac1z=\frac{z^*}{|z|^2}=\boxed{\frac{2+3\mathrm j}{13}}$$

## Exercise 12: Simultaneous equations

$$4z+3w=23,\qquad z+\mathrm jw=6+8\mathrm j$$

From the second equation, $z=6+8\mathrm j-\mathrm jw$. Substitute into the first:

$$24+32\mathrm j-4\mathrm jw+3w=23\ \Rightarrow\ w(3-4\mathrm j)=-1-32\mathrm j$$

$$w=\frac{(-1-32\mathrm j)(3+4\mathrm j)}{25}=\frac{-3-4\mathrm j-96\mathrm j+128}{25}=\frac{125-100\mathrm j}{25}=5-4\mathrm j$$

Back-substitute: $z=6+8\mathrm j-\mathrm j(5-4\mathrm j)=6+8\mathrm j-5\mathrm j-4=2+3\mathrm j$.

$$\boxed{z=2+3\mathrm j,\quad w=5-4\mathrm j}$$

**Check**: $4z+3w=8+12\mathrm j+15-12\mathrm j=23$ ✔

## Exercise 17: Find the real $x$ and $y$
Cross-multiply:

$$2+x-\mathrm jy=(1+2\mathrm j)(3x+\mathrm jy)=(3x-2y)+\mathrm j(6x+y)$$

- Real parts: $2+x=3x-2y$, so $x-y=1$.
- Imaginary parts: $-y=6x+y$, so $y=-3x$.

Hence $4x=1$:

$$\boxed{x=\tfrac14,\quad y=-\tfrac34}$$

## Exercise 24: Polar form
| | $z$ | $r$ | $\theta$ | polar form |
|---|---|---|---|---|
| (a) | $\mathrm j$ | 1 | $\pi/2$ | $\cos\frac\pi2+\mathrm j\sin\frac\pi2$ |
| (c) | $-1$ | 1 | $\pi$ | $\cos\pi+\mathrm j\sin\pi$ |
| (e) | $\sqrt3-\mathrm j\sqrt3$ | $\sqrt6$ | $-\pi/4$ | $\sqrt6\big[\cos(-\frac\pi4)+\mathrm j\sin(-\frac\pi4)\big]$ |
| (g) | $-3-2\mathrm j$ (Q3) | $\sqrt{13}$ | $-(\pi-\tan^{-1}\frac23)=-2.554$ | $\sqrt{13}\big[\cos(-2.554)+\mathrm j\sin(-2.554)\big]$ |
| (i) | $(2-\mathrm j)(2+\mathrm j)=4+1=5$ | 5 | 0 | $5(\cos0+\mathrm j\sin0)$ |

## Exercise 26: $z_1=e^{\mathrm j\pi/4}$, $z_2=e^{-\mathrm j\pi/3}$
**(a)** Exponents add:
- $\arg(z_1z_2^2)=\frac\pi4-\frac{2\pi}3=\boxed{-\tfrac{5\pi}{12}}$.
- $\arg(z_1^3/z_2)=\frac{3\pi}4+\frac\pi3=\frac{13\pi}{12}$. Subtract $2\pi$ to get the principal value, $\boxed{-\tfrac{11\pi}{12}}$.

**(b)** $z_1^2=e^{\mathrm j\pi/2}=\mathrm j$, and $\mathrm jz_2=e^{\mathrm j\pi/2}e^{-\mathrm j\pi/3}=e^{\mathrm j\pi/6}=\frac{\sqrt3}2+\frac12\mathrm j$. So

$$z_1^2+\mathrm jz_2=\frac{\sqrt3}2+\mathrm j\Big(1+\frac12\Big),$$

giving $\boxed{\operatorname{Re}=\tfrac{\sqrt3}2,\ \operatorname{Im}=\tfrac32}$.

## Exercise 27: $z_1=2e^{\mathrm j\pi/3}$, $z_2=4e^{-2\mathrm j\pi/3}$
| | modulus | argument (raw) | principal argument |
|---|---|---|---|
| (a) $z_1^3z_2^2$ | $8\cdot16=128$ | $\pi-\frac{4\pi}3=-\frac\pi3$ | $-\frac\pi3$ |
| (b) $z_1^2z_2^4$ | $4\cdot256=1024$ | $\frac{2\pi}3-\frac{8\pi}3=-2\pi$ | $0$, so $z=1024$ |
| (c) $z_1^2/z_2^3$ | $4/64=\frac1{16}$ | $\frac{2\pi}3+2\pi=\frac{8\pi}3$ | $\frac{2\pi}3$ |

---

# Part C: Specimen Test 5

## Q1: $z=2+\mathrm j$, $w=-3+\mathrm j$
(i) $\operatorname{Re}(z)=2$
(ii) $\operatorname{Im}(w)=1$ (the imaginary part is the *real number* 1, not $\mathrm j$)
(iii) $w^*=-3-\mathrm j$
(iv) $\mathrm jz-2w=(2\mathrm j-1)-(-6+2\mathrm j)=\boxed{5}$
(v)

$$\frac zw=\frac{(2+\mathrm j)(-3-\mathrm j)}{(-3)^2+1^2}=\frac{-6-2\mathrm j-3\mathrm j+1}{10}=\boxed{-\tfrac12-\tfrac12\mathrm j}$$

## Q2: Sum and difference on the Argand diagram
- $z_1+z_2$ is the **diagonal of the parallelogram** with sides $\vec{Oz_1}$ and $\vec{Oz_2}$ (the parallelogram law).
- $z_1-z_2=z_1+(-z_2)$. Either reflect $z_2$ through O and complete that parallelogram, or draw the vector **from $z_2$ to $z_1$** and translate it to start at O.
- $|z_1-z_2|$ is the distance between the two points.

![[m1054_specimen5_argand.png|720]]

## Q3: $z=-\sqrt3-\mathrm j$
**(i)(a)** $|z|=\sqrt{3+1}=\boxed2$. The point is in Q3 with reference angle $\tan^{-1}\frac1{\sqrt3}=\frac\pi6$, so $\operatorname{Arg}z=-\pi+\frac\pi6=\boxed{-\tfrac{5\pi}6}$.

**(i)(b)** All values: $\arg z=-\dfrac{5\pi}6+2k\pi$, for $k\in\mathbb Z$.

**(i)(c)** See the right panel of the figure above.

**(ii)** $z=2e^{-\mathrm j5\pi/6}$.
- **(a)** $z^6=64e^{-\mathrm j5\pi}=64e^{-\mathrm j5\pi+\mathrm j6\pi}=\boxed{64e^{\mathrm j\pi}}$ $(=-64)$.
- **(b)** $z^{-2}=\tfrac14e^{\mathrm j5\pi/3}=\boxed{\tfrac14e^{-\mathrm j\pi/3}}$, using $\frac{5\pi}3-2\pi=-\frac\pi3$.

## Q4: Modulus rules
**(i)** (a) $|z_1z_2|=|z_1||z_2|$ (b) $\left|\dfrac{z_1}{z_2}\right|=\dfrac{|z_1|}{|z_2|}$ (c) $|z_1^n|=|z_1|^n$

**(ii)** $|2+\mathrm j|=|-1-2\mathrm j|=\sqrt5$, so

$$\left|\frac{(2+\mathrm j)^{11}}{(-1-2\mathrm j)^9}\right|=\frac{(\sqrt5)^{11}}{(\sqrt5)^9}=(\sqrt5)^2=\boxed5$$

## Q5: Euler's formula
**(i)** $e^{\mathrm j\alpha}=\cos\alpha+\mathrm j\sin\alpha$.

**(ii)** Replace $\alpha$ by $-\alpha$, using $\cos$ even and $\sin$ odd: $e^{-\mathrm j\alpha}=\cos\alpha-\mathrm j\sin\alpha$. Adding and subtracting the two:

$$\boxed{\cos\alpha=\frac{e^{\mathrm j\alpha}+e^{-\mathrm j\alpha}}2,\qquad\sin\alpha=\frac{e^{\mathrm j\alpha}-e^{-\mathrm j\alpha}}{2\mathrm j}}$$

## Sources
- Transcribed problem statements: `tmp/md/module_05_complex_numbers_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §3.2, §4.2; MATH1054 Module Booklet, Module 5
