---
title: "MATH1054 M14 Solutions - Vectors I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 4: Vectors and Matrices"
tags:
  - math1054
  - tutorial-solutions
  - vectors
sheet: "Specimen Test 14 (booklet) + Module 14 work scheme: Examples 4.1–4.29; Exercises 9, 11, 12, 19, 27, 28(a),(c), 31, 32, 41, 51, 52"
theory_notes: ["[[MATH1054 M14 - Vectors I]]"]
key_concepts: ["[[Vector Algebra and Components]]", "[[Scalar (Dot) Product]]", "[[Vector (Cross) Product]]"]
status: complete
sources: ["tmp/md/module_14_vectors_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§4.2–4.3)"]
---

# MATH1054 M14 Solutions - Vectors I

> [!abstract] Sheet Info
> The whole Module 14 work scheme. Every component, dot product and cross product was checked with SymPy `Matrix`. Vectors are written $(x,y,z)=x\mathbf i+y\mathbf j+z\mathbf k$.
>
> Two formulas are used throughout:
> - **Cross product** (determinant form): $\mathbf a\times\mathbf b=(a_2b_3-a_3b_2,\ a_3b_1-a_1b_3,\ a_1b_2-a_2b_1)$
> - **Angle between two vectors**: $\cos\theta=\dfrac{\mathbf a\cdot\mathbf b}{|\mathbf a||\mathbf b|}$

## Theory Links
- [[MATH1054 M14 - Vectors I]] · [[Vector Algebra and Components]] · [[Scalar (Dot) Product]] · [[Vector (Cross) Product]]

---

# Part A: Worked examples

## Example 4.1: $\mathrm P=(2,-1,3)$

$$|\mathrm{OP}|=\sqrt{4+1+9}=\boxed{\sqrt{14}\approx3.742}$$

The direction cosines are the components of the unit vector:

$$(l,m,n)=\Big(\tfrac2{\sqrt{14}},-\tfrac1{\sqrt{14}},\tfrac3{\sqrt{14}}\Big)\approx(0.535,-0.267,0.802)$$

**Check**: $l^2+m^2+n^2=1$ ✔.

## Example 4.4: Vectors around Fig. 4.14
Every side is "end minus start":
- $\mathbf g=\vec{\mathrm{AB}}=\boxed{\mathbf b-\mathbf a}$
- $\mathbf f=\vec{\mathrm{BC}}=\boxed{\mathbf c-\mathbf b}$
- $\mathbf e=\vec{\mathrm{CD}}=\boxed{\mathbf d-\mathbf c}$

Going round the closed loop A→B→C→D→A gives $\mathbf g+\mathbf f+\mathbf e+\mathbf h=\mathbf0$, so

$$\boxed{\mathbf e=-(\mathbf f+\mathbf g+\mathbf h)}$$

## Example 4.5: Quadrilateral OACB with $\vec{\mathrm{OC}}=\mathbf b+\tfrac12\mathbf a$

$$\vec{\mathrm{BC}}=\vec{\mathrm{OC}}-\vec{\mathrm{OB}}=\boxed{\tfrac12\mathbf a},\qquad\vec{\mathrm{CA}}=\vec{\mathrm{OA}}-\vec{\mathrm{OC}}=\boxed{\tfrac12\mathbf a-\mathbf b}$$

Since $\vec{\mathrm{BC}}\parallel\vec{\mathrm{OA}}$ and it is half as long, OACB is a **trapezium**.

## Example 4.6: Resultant of $|\mathbf F|=2$ N and $|\mathbf F'|=1$ N at $60°$
The cosine rule gives the magnitude. In the parallelogram, the angle between $\mathbf F$ and $\mathbf F'$ is $60°$, so

$$|\mathbf R|^2=2^2+1^2+2(2)(1)\cos60°=7\ \Rightarrow\ |\mathbf R|=\boxed{\sqrt7\approx2.646\ \text{N}}$$

The angle $\alpha$ to $\mathbf F$ comes from the components along and perpendicular to $\mathbf F$:

$$\tan\alpha=\frac{1\cdot\sin60°}{2+1\cdot\cos60°}=\frac{\sqrt3/2}{5/2}=\frac{\sqrt3}{5}\ \Rightarrow\ \alpha=\boxed{19.1°}$$

## Example 4.7: Aircraft in a north-west wind
Take $\mathbf i$ east and $\mathbf j$ north. A **NW wind** blows **from** the north-west, towards the south-east, so

$$\mathbf w=\frac{50}{\sqrt2}(\mathbf i-\mathbf j)=35.36\,\mathbf i-35.36\,\mathbf j.$$

The aircraft's air velocity is $\mathbf a$, with $|\mathbf a|=400$, and the ground velocity $\mathbf a+\mathbf w$ must point **due west**. So the northward component of $\mathbf a$ must cancel the wind's southward drift:

$$400\sin\theta=35.36\ \Rightarrow\ \theta=5.07°$$

**Heading**: $5.07°$ **north of west** (a bearing of about $275°$).

**Ground speed**: $400\cos\theta-35.36=398.43-35.36=\boxed{363.1\ \text{knots}}$.

![[m1054_relative_velocity.png|760]]

## Example 4.10: $\mathbf a=(1,1,1)$, $\mathbf b=(-1,2,3)$, $\mathbf c=(0,3,4)$
(a) $\mathbf a+\mathbf b=(0,3,4)$
(b) $2\mathbf a-\mathbf b=(3,0,-1)$
(c) $\mathbf a+\mathbf b-\mathbf c=\mathbf0$
(d) $|\mathbf c|=5$, so $\hat{\mathbf c}=\big(0,\tfrac35,\tfrac45\big)$

## Example 4.11
**(a)**

$$\mathbf d=\mathbf a-2\mathbf b+3\mathbf c=(2,-3,1)-(2,10,-4)+(9,-12,9)=\boxed{(9,-25,14)}$$

**(b)** $|\mathbf d|=\sqrt{81+625+196}=\sqrt{902}\approx30.03$, so $\hat{\mathbf d}=\frac1{\sqrt{902}}(9,-25,14)$.
**(c)** The direction cosines are $\big(\frac9{\sqrt{902}},\frac{-25}{\sqrt{902}},\frac{14}{\sqrt{902}}\big)\approx(0.300,-0.832,0.466)$.

## Example 4.12: The tetrahedral molecule XY₃
**(a) Bond lengths.** With X $=(2\sqrt3+\sqrt2,0,-2+\sqrt6)$:
- $\vec{\mathrm{XY}}=(-\sqrt3-\sqrt2,\,-2,\,1-\sqrt6)$
- $|\vec{\mathrm{XY}}|^2=(5+2\sqrt6)+4+(7-2\sqrt6)=16$, so $|\mathrm{XY}|=4$.
- The same working for Y′ and Y″ gives $|\mathrm{XY'}|=|\mathrm{XY''}|=4$ (SymPy confirms).

All three bonds are $\boxed4$ ✔.

**(b)** Going $\mathrm X\to\mathrm Y\to\mathrm Y'\to\mathrm Y''\to\mathrm X$ is a closed path. So $\vec{\mathrm{XY}}+\vec{\mathrm{YY'}}+\vec{\mathrm{Y'Y''}}+\vec{\mathrm{Y''X}}=\mathbf0$ ✔.

As the transcription notes, the closing vector must be $\vec{\mathrm{Y''X}}$. With $\vec{\mathrm{Y''Y}}$ as printed, the last three terms cancel on their own, leaving $\vec{\mathrm{XY}}\neq\mathbf0$.

## Example 4.13: Resultant of three forces
- $\mathbf F_2=6\cdot\frac{(1,2,-2)}{3}=(2,4,-4)$
- $\mathbf F_3=10\cdot\frac{(3,-4,0)}5=(6,-8,0)$

$$\mathbf R=(1,1,1)+(2,4,-4)+(6,-8,0)=\boxed{(9,-3,-3)\ \text{N}},\qquad|\mathbf R|=3\sqrt{11}\approx9.95\ \text{N}$$

The **equilibrant**, which makes the total zero, is $\boxed{(-9,3,3)\ \text{N}}$.

## Example 4.17: Dot products, with $\mathbf a=(1,-1,2)$, $\mathbf b=(-2,0,2)$, $\mathbf c=(3,2,1)$
(a) $\mathbf a\cdot\mathbf c=3-2+2=3$
(b) $\mathbf b\cdot\mathbf c=-6+0+2=-4$
(c) $(\mathbf a+\mathbf b)\cdot\mathbf c=3+(-4)=-1$ (distributive law ✔)
(d) $\mathbf a\cdot(2\mathbf b+3\mathbf c)=2(\mathbf a\cdot\mathbf b)+3(\mathbf a\cdot\mathbf c)=2(2)+9=13$, using $\mathbf a\cdot\mathbf b=-2+0+4=2$
(e) $(\mathbf a\cdot\mathbf b)\mathbf c=2(3,2,1)=(6,4,2)$. This is a **vector**.

## Example 4.18: The angle between $(1,2,3)$ and $(2,0,4)$

$$\cos\theta=\frac{2+0+12}{\sqrt{14}\sqrt{20}}=\frac{14}{\sqrt{280}}=0.8367\ \Rightarrow\ \boxed{\theta=33.2°}$$

## Example 4.19
$(1,0,1)\cdot(0,1,0)=0$, so the vectors are **perpendicular**. (Neither is the zero vector.)

## Example 4.20: $\mathbf a\cdot\mathbf b=\mathbf a\cdot\mathbf c$
$\mathbf a\cdot\mathbf b=3+2-3=2$ and $\mathbf a\cdot\mathbf c=-1+4-1=2$ ✔. Equal dot products do **not** mean $\mathbf b=\mathbf c$. They mean $\mathbf a\cdot(\mathbf b-\mathbf c)=0$: here $\mathbf a\perp(\mathbf b-\mathbf c)=(4,-2,-2)$. **You cannot "cancel" a vector from a dot product.**

## Example 4.22: Work done
$\vec{\mathrm{PQ}}=(-2,3,1)-(1,4,-1)=(-3,-1,2)$, so

$$W=\mathbf F\cdot\vec{\mathrm{PQ}}=-9+2+10=\boxed3$$

## Example 4.23: Components of $\mathbf F=(2,-1,3)$
The component of $\mathbf F$ along a direction is $\mathbf F\cdot\hat{\mathbf u}$:
(a) along $\mathbf i$: $\boxed2$
(b) along $\big(\frac13,\frac23,\frac23\big)$, already a unit vector: $\frac{2-2+6}3=\boxed2$
(c) along $(4,2,-1)$: $\hat{\mathbf u}=\frac{(4,2,-1)}{\sqrt{21}}$, so the component is $\frac{8-2-3}{\sqrt{21}}=\boxed{\frac3{\sqrt{21}}\approx0.655}$

## Example 4.24: Cross products and the triple-product identities
Given $\mathbf a=(2,1,0)$, $\mathbf b=(2,-1,1)$, $\mathbf c=(0,1,1)$:

| | Expression | Value |
|---|---|---|
| (a) | $\mathbf a\times\mathbf b$ | $(1\cdot1-0,\ 0-2\cdot1,\ -2-2)=(1,-2,-4)$ |
| (b) | $(\mathbf a\times\mathbf b)\times\mathbf c$ | $(1,-2,-4)\times(0,1,1)=(-2+4,\ 0-1,\ 1-0)=(2,-1,1)$ |
| (c) | $(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf b\cdot\mathbf c)\mathbf a$ | $1(2,-1,1)-0=(2,-1,1)$ ✔ equals (b) |
| (d) | $\mathbf b\times\mathbf c$ | $(-1-1,\ 0-2,\ 2-0)=(-2,-2,2)$ |
| (e) | $\mathbf a\times(\mathbf b\times\mathbf c)$ | $(2,1,0)\times(-2,-2,2)=(2,-4,-2)$ |
| (f) | $(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$ | $1(2,-1,1)-3(0,1,1)=(2,-4,-2)$ ✔ equals (e) |

Here $\mathbf a\cdot\mathbf c=1$, $\mathbf b\cdot\mathbf c=0$ and $\mathbf a\cdot\mathbf b=3$.

(b) and (e) differ, so **the cross product is not associative**.

## Example 4.25: Unit normal to the plane of $\mathbf a=(2,-3,1)$ and $\mathbf b=(1,2,-4)$

$$\mathbf a\times\mathbf b=\big((-3)(-4)-1\cdot2,\ 1\cdot1-2(-4),\ 2\cdot2-(-3)\cdot1\big)=(10,9,7),\qquad|\cdot|=\sqrt{230}$$

$$\boxed{\hat{\mathbf n}=\pm\frac{1}{\sqrt{230}}(10,9,7)}$$

## Example 4.26: Area of triangle PQR
- $\vec{\mathrm{PQ}}=(-3,-2,1)$ and $\vec{\mathrm{PR}}=(2,-5,-3)$.
- $\vec{\mathrm{PQ}}\times\vec{\mathrm{PR}}=\big(6+5,\ 2-9,\ 15+4\big)=(11,-7,19)$.

$$\text{Area}=\tfrac12|(11,-7,19)|=\tfrac12\sqrt{531}=\boxed{\tfrac{3\sqrt{59}}2\approx11.52}$$

## Example 4.28: Moment of a force about a point
- $\mathbf F=4\hat{\mathbf u}$ with $\hat{\mathbf u}=\frac{(4,5,-2)}{\sqrt{45}}$, so $\mathbf F=\frac{4}{3\sqrt5}(4,5,-2)$.
- $\mathbf r=\vec{\mathrm{AP}}=(1,1,-2)$.
- $\mathbf r\times(4,5,-2)=\big(1(-2)-(-2)5,\ (-2)4-1(-2),\ 5-4\big)=(8,-6,1)$.

$$\mathbf M_{\mathrm A}=\mathbf r\times\mathbf F=\frac{4}{3\sqrt5}(8,-6,1)\approx\boxed{(4.770,\,-3.578,\,0.596)},\qquad|\mathbf M|=\frac{4\sqrt{101}}{3\sqrt5}\approx5.99$$

The **moments about axes through A** parallel to $x$, $y$ and $z$ are the components: $4.770$, $-3.578$ and $0.596$.

## Example 4.29: Velocity of a point on a rotating body
Use $\mathbf v=\boldsymbol\omega\times\vec{\mathrm{AP}}$.
- $\boldsymbol\omega=\frac{5}{\sqrt{14}}(1,3,-2)$ and $\vec{\mathrm{AP}}=(-4,0,2)$.
- $(1,3,-2)\times(-4,0,2)=(6-0,\ 8-2,\ 0+12)=(6,6,12)$.

$$\mathbf v=\frac{5}{\sqrt{14}}(6,6,12)=\frac{30}{\sqrt{14}}(1,1,2)\approx\boxed{(8.02,\,8.02,\,16.04)}\ \text{units s}^{-1},\qquad|\mathbf v|\approx19.64$$

---

# Part B: Assigned exercises

## Exercise 9: The cyclist and the wind
Take $\mathbf i$ east and $\mathbf j$ north, and let the true wind be $\mathbf w=(p,q)$. The wind **felt** by the cyclist is $\mathbf w-\mathbf v_{\text{cyclist}}$.
- At $\mathbf v=(8,0)$, the felt wind $(p-8,q)$ comes **from the north**, so it points due south. Hence $p=8$ and $q<0$.
- At $\mathbf v=(16,0)$, the felt wind $(p-16,q)=(-8,q)$ comes **from the NE**, so it points towards the SW. Its components must be equal, so $q=-8$.

$$\boxed{\mathbf w=(8,-8)\ \text{km/h}:\ 8\sqrt2\approx11.3\ \text{km/h from the north-west}}$$

See the right panel of the relative-velocity figure above.

## Exercise 11: $\mathbf a=(1,1,0)$, $\mathbf b=(2,2,1)$, $\mathbf c=(0,1,1)$
| | Quantity | Value |
|---|---|---|
| (a) | $\mathbf a+\mathbf b$ | $(3,3,1)$ |
| (b) | $\mathbf a+\frac12\mathbf b+2\mathbf c$ | $(1,1,0)+(1,1,\frac12)+(0,2,2)=(2,4,\frac52)$ |
| (c) | $\mathbf b-2\mathbf a$ | $(0,0,1)$ |
| (d) | $\lvert\mathbf a\rvert$ | $\sqrt2$ |
| (e) | $\lvert\mathbf b\rvert$ | $3$ |
| (f) | $\lvert\mathbf a-\mathbf b\rvert$ | $\lvert(-1,-1,-1)\rvert=\sqrt3$ |
| (g) | $\hat{\mathbf a}$ | $\frac1{\sqrt2}(1,1,0)$ |
| (h) | $\hat{\mathbf b}$ | $\frac13(2,2,1)$ |

## Exercise 12: $\vec{\mathrm{PQ}}$

$$\vec{\mathrm{PQ}}=(5,-2,4)-(1,3,-7)=\boxed{(4,-5,11)},\qquad|\mathrm{PQ}|=\sqrt{16+25+121}=\sqrt{162}=\boxed{9\sqrt2\approx12.73}$$

The direction cosines are $\frac1{9\sqrt2}(4,-5,11)\approx(0.314,-0.393,0.864)$.

## Exercise 19: Collinearity
$\vec{\mathrm{PQ}}=(1,5,-3)$ and $\vec{\mathrm{QR}}=(1,5,-3)$. These are **equal**, so they are parallel and share the point Q. So P, Q and R lie on one line, and $\boxed{\mathrm{PQ}:\mathrm{QR}=1:1}$: Q is the midpoint.

## Exercise 27: $\mathbf u=(4,0,-2)$, $\mathbf v=(3,1,-1)$, $\mathbf w=(2,1,6)$, $\mathbf s=(1,4,1)$
(a) $\mathbf u\cdot\mathbf v=12+0+2=\boxed{14}$
(b) $\mathbf v\cdot\mathbf s=3+4-1=\boxed6$
(c) $\hat{\mathbf w}=\boxed{\frac1{\sqrt{41}}(2,1,6)}$
(d) $(\mathbf v\cdot\mathbf s)\hat{\mathbf u}=6\cdot\frac{(4,0,-2)}{2\sqrt5}=\boxed{\frac{3}{\sqrt5}(4,0,-2)}\approx(5.367,0,-2.683)$
(e) $\mathbf u\cdot\mathbf w=8-12=-4$, so $(\mathbf u\cdot\mathbf w)(\mathbf v\cdot\mathbf s)=\boxed{-24}$
(f) $\mathbf u\cdot\mathbf i=4$ and $\mathbf w\cdot\mathbf s=2+4+6=12$, so the result is $4(3,1,-1)+12(0,0,1)=\boxed{(12,4,8)}$

## Exercise 28
**(a)**

$$\cos\theta=\frac{\mathbf u\cdot\mathbf w}{|\mathbf u||\mathbf w|}=\frac{-4}{\sqrt{20}\sqrt{41}}=-0.1397\ \Rightarrow\ \boxed{\theta=98.0°}$$

**(c)** We need $(\mathbf u+\lambda\mathbf k)\cdot(\mathbf v-\lambda\mathbf i)=0$:

$$(4,0,-2+\lambda)\cdot(3-\lambda,1,-1)=12-4\lambda+2-\lambda=14-5\lambda=0\ \Rightarrow\ \boxed{\lambda=\tfrac{14}5}$$

## Exercise 31: Work done
$\vec{\mathrm{PQ}}=(1,-3,4)-(-1,2,3)=(2,-5,1)$, so

$$W=(-2,-1,3)\cdot(2,-5,1)=-4+5+3=\boxed4$$

## Exercise 32: The resolved part
$\mathbf F=5\dfrac{(2,-3,1)}{\sqrt{14}}$. Its resolved part along $(3,2,1)$ is

$$\mathbf F\cdot\frac{(3,2,1)}{\sqrt{14}}=\frac{5(6-6+1)}{14}=\boxed{\tfrac5{14}\approx0.357\ \text{units}}$$

## Exercise 41: $\mathbf p=(1,1,1)$, $\mathbf q=(0,-1,2)$, $\mathbf r=(2,2,1)$
(a) $\mathbf p\times\mathbf q=(2+1,\ 0-2,\ -1-0)=\boxed{(3,-2,-1)}$
(b) $\mathbf p\times\mathbf r=(1-2,\ 2-1,\ 2-2)=\boxed{(-1,1,0)}$
(c) $\mathbf r\times\mathbf q=(4+1,\ 0-4,\ -2-0)=\boxed{(5,-4,-2)}$
(d) $(\mathbf p\times\mathbf r)\cdot\mathbf q=(-1,1,0)\cdot(0,-1,2)=\boxed{-1}$
(e) $\mathbf q\cdot(\mathbf r\times\mathbf p)=-\mathbf q\cdot(\mathbf p\times\mathbf r)=\boxed{1}$ (swapping two vectors flips the sign)
(f) $(\mathbf p\times\mathbf r)\times\mathbf q=(-1,1,0)\times(0,-1,2)=(2-0,\ 0+2,\ 1-0)=\boxed{(2,2,1)}$

## Exercise 51: Linear velocity
Use $\mathbf v=\boldsymbol\omega\times\vec{\mathrm{AP}}$.
- $\boldsymbol\omega=\frac{6}{\sqrt{14}}(3,-2,1)$ and $\vec{\mathrm{AP}}=(0,0,-4)$.
- $(3,-2,1)\times(0,0,-4)=(8,12,0)$.

$$\mathbf v=\frac{6}{\sqrt{14}}(8,12,0)=\frac{24}{\sqrt{14}}(2,3,0)\approx\boxed{(12.83,\,19.24,\,0)},\qquad|\mathbf v|=\frac{24\sqrt{13}}{\sqrt{14}}\approx23.13$$

## Exercise 52: Moment about A
- $\vec{\mathrm{AP}}=(1,0,-2)$ and $\mathbf F=\frac{4}{\sqrt{21}}(2,-1,4)$.
- $(1,0,-2)\times(2,-1,4)=(0-2,\ -4-4,\ -1-0)=(-2,-8,-1)$.

$$\mathbf M_{\mathrm A}=\frac{4}{\sqrt{21}}(-2,-8,-1)\approx\boxed{(-1.746,\,-6.983,\,-0.873)},\qquad|\mathbf M|=\frac{4\sqrt{69}}{\sqrt{21}}\approx7.25$$

---

# Part C: Specimen Test 14

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 14), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Quadrilateral ABCD with $\vec{\mathrm{AB}}=\mathbf a$, $\vec{\mathrm{BC}}=\mathbf b$, $\vec{\mathrm{CD}}=\mathbf c$
**(i)**
- **(a)** $\vec{\mathrm{AC}}=\boxed{\mathbf a+\mathbf b}$
- **(b)** $\vec{\mathrm{AD}}=\boxed{\mathbf a+\mathbf b+\mathbf c}$
- **(c)** E is the midpoint of AB and G is the midpoint of CD, so

$$\vec{\mathrm{EG}}=\vec{\mathrm{EB}}+\vec{\mathrm{BC}}+\vec{\mathrm{CG}}=\boxed{\tfrac12\mathbf a+\mathbf b+\tfrac12\mathbf c}$$

**(ii)** $\mathbf b+\mathbf c=\vec{\mathrm{BD}}$. The angle $\theta$ at C lies between $\vec{\mathrm{CB}}=-\mathbf b$ and $\vec{\mathrm{CD}}=\mathbf c$, so $\mathbf b\cdot\mathbf c=-bc\cos\theta$. Then

$$|\mathbf b+\mathbf c|^2=b^2+c^2+2\mathbf b\cdot\mathbf c\ \Rightarrow\ \boxed{|\mathbf b+\mathbf c|=\sqrt{b^2+c^2-2bc\cos\theta}}$$

This is just the cosine rule in triangle BCD.

## Q2
**(i)** $\mathbf r=\boxed{\mathbf i-\mathbf j+4\mathbf k}$
**(ii)** $\vec{\mathrm{PA}}=\mathbf a-\mathbf r=\boxed{-\mathbf i+4\mathbf j-3\mathbf k}$

## Q3: $\mathbf a=(3,-4,5)$, $\mathbf b=(1,3,-1)$
(i) $|\mathbf a|=\sqrt{50}=\boxed{5\sqrt2}$
(ii) $\hat{\mathbf a}=\boxed{\tfrac1{5\sqrt2}(3\mathbf i-4\mathbf j+5\mathbf k)}$
(iii) $\mathbf a-2\mathbf b=\boxed{\mathbf i-10\mathbf j+7\mathbf k}$
(iv) The $z$-component of $\mathbf b$ is $\boxed{-1}$.

## Q4: $\mathbf b=(1,3,-1)$, $\mathbf c=(3,-2,-1)$
**(i)** $\mathbf b\cdot\mathbf c=3-6+1=\boxed{-2}$.

**(ii)**

$$\cos\theta=\frac{-2}{\sqrt{11}\sqrt{14}}=-0.1612\ \Rightarrow\ \boxed{\theta=99.3°}$$

## Q5: Work done
**(i)** $\mathbf F=6\,\dfrac{(1,2,1)}{\sqrt6}=\boxed{\sqrt6\,(\mathbf i+2\mathbf j+\mathbf k)}$ N

**(ii)** $\vec{\mathrm{AB}}=(1,1,2)$, so

$$W=\mathbf F\cdot\vec{\mathrm{AB}}=\sqrt6(1+2+2)=\boxed{5\sqrt6\approx12.25\ \text{J}}$$

## Q6: $\mathbf a=(2,0,1)$, $\mathbf b=(-2,4,3)$
**(i)**

$$\mathbf a\times\mathbf b=(0\cdot3-1\cdot4,\ 1(-2)-2\cdot3,\ 2\cdot4-0)=\boxed{(-4,-8,8)}$$

**(ii)** $|\mathbf a\times\mathbf b|=12$, so the unit perpendicular is $\boxed{\pm\tfrac13(-1,-2,2)}$.

## Q7: Moment about $(1,1,1)$
$\mathbf r=(2,6,1)-(1,1,1)=(1,5,0)$, so

$$\mathbf M=\mathbf r\times\mathbf F=(1,5,0)\times(5,0,2)=(10-0,\ 0-2,\ 0-25)=\boxed{(10,-2,-25)\ \text{N m}}$$

## Q8: Rotating body
**(i)** The axis direction is $(2,3,2)-(1,0,0)=(1,3,2)$, with $|\cdot|=\sqrt{14}$. So

$$\boldsymbol\omega=\boxed{\tfrac4{\sqrt{14}}(\mathbf i+3\mathbf j+2\mathbf k)}\ \text{rad/s}$$

**(ii)** Use the point A$(1,0,0)$ on the axis, so $\vec{\mathrm{AP}}=(1,1,1)$:

$$\mathbf v=\boldsymbol\omega\times\vec{\mathrm{AP}}=\tfrac4{\sqrt{14}}(1,3,2)\times(1,1,1)=\tfrac4{\sqrt{14}}(1,1,-2)\approx\boxed{(1.069,\,1.069,\,-2.138)}\ \text{m/s}$$

## Sources
- Transcribed problem statements: `tmp/md/module_14_vectors_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §4.2–4.3; MATH1054 Module Booklet, Module 14
