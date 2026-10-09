---
title: "FEEG1002 A5 - Beam Deflection and Macaulay's Method"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 5
tags: [feeg1002, statics, beams, deflection, macaulay, double-integration]
aliases: ["Statics 1 Lecture 9", "Statics 1 Lecture 10", "Beam deflection", "Double integration method"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
key_concepts: ["[[Macaulay's Method]]", "[[Standard Beam Deflections]]", "[[Moment Curvature Relation]]", "[[Elastic Curve]]", "[[Heaviside Step Function]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 09 - Beams, Deflection.pdf", "02 - Sources/Statics 1/Lectures/Lecture 10 - Macaulay's Method.pdf"]
---

# FEEG1002 A5 - Beam Deflection and Macaulay's Method

> [!abstract] Summary
> Engineer's bending theory gives the local curvature $1/R = M/EI$. For small slopes $1/R\approx\pm d^2v/dx^2$. With deflection $v$ measured **downwards** and sagging $M$ positive, the result is
> $$EI\frac{d^2v}{dx^2} = -M(x)$$
> Integrating twice gives the slope and then the deflection, with two constants fixed by the support conditions.
> **Macaulay's method** writes $M(x)$ as **one** expression valid along the whole beam by using switch-on brackets $[x-a]^n$. However many point loads there are, there are only two constants to find.

## Key Concepts
- [[Macaulay's Method]] · [[Standard Beam Deflections]] · [[Moment Curvature Relation]] · [[Elastic Curve]] · [[Heaviside Step Function]]

---

## 1. From moment to curvature to deflection (L9a)
- Plane sections remaining plane means the beam is locally a circular arc: $\dfrac{1}{R} = \dfrac{M}{EI}$.
- Geometry: $ds = R\,d\theta$. For large $R$, $ds\approx dx$ and $\theta\approx\tan\theta = dv/dx$, so $\dfrac1R = \pm\dfrac{d^2v}{dx^2}$.
- **Sign convention**: $y$ and $v$ point downwards. A sagging (positive) $M$ makes the slope $dv/dx$ decrease, i.e. **negative** curvature.

$$
\boxed{EI\frac{d^2v}{dx^2} = -M}\qquad EI\frac{dv}{dx} = \int -M\,dx + C_0,\qquad EIv = \iint -M\,dx\,dx + C_0x + C_1
$$

$EI$ is the **flexural rigidity**.

| Support | Boundary conditions |
|---|---|
| Pinned or roller | $v = 0$ |
| Built-in | $v = 0$ **and** $dv/dx = 0$ |
| Free end | (none on $v$; $M = 0$ and $Q = 0$ are already in $M(x)$) |

## 2. Example 1: simply supported beam with a UDL (L9b)
$R_A = R_B = wL/2$, so $M = \dfrac{wL}{2}x - \dfrac{w x^2}{2}$ over the whole span.

$$
EIv = -\frac{wL}{12}x^3 + \frac{w}{24}x^4 + C_0x + C_1,\qquad v(0) = 0\Rightarrow C_1 = 0,\quad v(L) = 0\Rightarrow C_0 = \frac{wL^3}{24}
$$

$$
v = \frac{w}{24EI}\left(L^3x - 2Lx^3 + x^4\right),\qquad v_{max} = v(L/2) = \frac{5wL^4}{384EI}
$$

## 3. Example 2: point load off-centre, done the long way (L9c)
Load $F$ at $x = a$, with $R_A = F(L-a)/L$ and $R_B = Fa/L$.
- $M$ has **two** expressions, one on each side of the load.
- Two double integrations give **four** constants.
- Four conditions fix them: $v(0) = v(L) = 0$, plus continuity of $v$ and $dv/dx$ at $x = a$.

Result: $v(a) = \dfrac{Fa^2(L-a)^2}{3EIL}$, which at midspan is $v_{max} = \dfrac{FL^3}{48EI}$.

With $n$ load changes this becomes $2n$ constants, so a better method is needed.

## 4. Macaulay's method (L10a–b)

$$
[x-a]^n = \begin{cases}0 & x<a\\ (x-a)^n & x\ge a\end{cases},\qquad [x-a]^0 = 1\ \text{for}\ x > a
$$

Rules:
1. **Never expand** a bracket.
2. Integrate brackets as a whole: $\displaystyle\int[x-a]^n dx = \frac{[x-a]^{n+1}}{n+1}$.
3. When evaluating, any bracket with $x < a$ is **zero**, including inside the boundary conditions.

![[s1_macaulay_brackets.png|620]]

**Procedure:**
1. Find the reactions.
2. Take **one** cut, after the last change in loading but before the end of the beam, and write $M$ for the left part using brackets.
3. Integrate $EIv'' = -M$ twice.
4. Apply the two boundary conditions.

> [!example] L10: point load at $a$ with Macaulay
> $$M = \frac{F(L-a)}{L}x - F[x-a]$$
> $$EIv = -\frac{F(L-a)}{6L}x^3 + \frac{F}{6}[x-a]^3 + C_0x + C_1$$
> With $v(0) = v(L) = 0$:
> $$v = \frac1{EI}\left[\frac{F(L-a)x}{6L}(2La - a^2 - x^2) + \frac{F}{6}[x-a]^3\right]$$

### Writing $M$ with brackets (L10c)

| Loading | Contribution to $M$ at a cut beyond it |
|---|---|
| Upward reaction $R$ at $a$ | $+R[x-a]$ |
| Downward point load $F$ at $a$ | $-F[x-a]$ |
| UDL $w$ starting at $a$, running to the cut | $-w[x-a]^2/2$ |
| UDL $w$ from $a$ to $b$ **stopping before** the cut | $-w[x-a]^2/2 + w[x-b]^2/2$ (add a cancelling upward UDL from $b$) |
| Anticlockwise couple $M_0$ at $a$ | $-M_0[x-a]^0$ |

> [!tip] Why a stopped UDL needs a negative term
> A bracket, once switched on, cannot be switched off. To end a UDL at $x = b$, superpose an equal **upward** UDL starting at $b$. Tutorial 5 Q2 uses this: $M = 12[x-3] - 3[x-2]^2 + 3[x-4]^2$ kN m.

![[s1_t5_q2.png|720]]

## 5. Standard cases worth memorising

| Case | Max deflection | Max slope | Max moment |
|---|---|---|---|
| Cantilever, end load $F$ | $\dfrac{FL^3}{3EI}$ (tip) | $\dfrac{FL^2}{2EI}$ | $FL$ (root) |
| Cantilever, UDL $w$ | $\dfrac{wL^4}{8EI}$ (tip) | $\dfrac{wL^3}{6EI}$ | $\dfrac{wL^2}{2}$ (root) |
| Simply supported, central $F$ | $\dfrac{FL^3}{48EI}$ | $\dfrac{FL^2}{16EI}$ | $\dfrac{FL}{4}$ |
| Simply supported, UDL $w$ | $\dfrac{5wL^4}{384EI}$ | $\dfrac{wL^3}{24EI}$ | $\dfrac{wL^2}{8}$ |
| Cantilever, $F$ at $L/2$ (Tutorial 5 Q1) | $\dfrac{5FL^3}{48EI}$ (tip) | – | $\dfrac{FL}{2}$ |

In the last case the outer half carries no moment, so it is **straight**. The tip deflection is the midspan deflection plus the slope there times $L/2$:

$$
\frac{F(L/2)^3}{3EI} + \frac{F(L/2)^2}{2EI}\cdot\frac L2 = \frac{5FL^3}{48EI}
$$

![[s1_t5_q1.png|640]]

## Year 2 bridge
- **Same physics, different sign bookkeeping.** [[SESA2028 S2 - Beam Deflection and Bending Design]] writes $EI\,v'' = M$ and stresses consistency over any one convention. Translating FEEG1002 results means flipping the sign of $v$ (or of $M$).
- **Macaulay brackets are Heaviside functions.** $[x-a]^0 = H(x-a)$, and the brackets are repeated integrals of it ([[Heaviside Step Function]], MATH2048). The same idea appears in [[Laplace Transform]] time shifts, $\mathcal L\{g(t-a)H(t-a)\} = e^{-as}G(s)$.
- **Energy methods compute single deflections faster.** The [[Unit Load Method]] in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] gives $\delta = \int Mm/EI\,dx$ without finding the whole elastic curve.
- **FEA.** The cubic shape functions of the [[Euler-Bernoulli Beam Element]] ([[SESA2029 B5 - Euler-Bernoulli Beam Element]]) are exactly the deflected shapes above, which is why one beam element per span reproduces them exactly.

## Links
- Previous: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] · Next: [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]

## Sources
- Statics 1 Lectures 9a–c (deflection; UDL example; point-load example) and 10a–c (Macaulay's method; point load revisited; further examples)
