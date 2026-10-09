---
title: "MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 3: Fourier and Laplace Transforms"
order: 8
tags:
  - math2048
  - laplace-transform
  - partial-fractions
aliases: ["MATH2048 Lecture 11", "MATH2048 Lecture 12", "Laplace transform properties"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 TR1 - Fourier Transforms]]", "[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]"]
next_topics: ["[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
key_concepts: ["[[Laplace Transform]]", "[[Laplace Transform Properties and Proofs]]", "[[Partial Fractions for Inverse Laplace]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture11_LaplaceTransform1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture12_LaplaceTransform2.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Appendix-Laplace Transform_additional slides.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 4)"]
---

# MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs

> [!abstract] Summary
> $\tilde f(s)=\mathcal L[f]=\int_0^\infty f(x)e^{-sx}dx$. This is the "one-sided" transform, and $s=\sigma+j\omega$ is complex. Derivatives become $s\tilde f-f(0)$ and $s^2\tilde f-sf(0)-f'(0)$, so **the initial conditions are built in**.
>
> The recipe for an IVP:
> 1. Transform the ODE.
> 2. Solve the algebra for $\tilde y(s)$.
> 3. Use **partial fractions** to split it into known forms.
> 4. Invert term by term with the table and the shift theorems.
>
> There is **no inversion formula** in this module, only table look-up. So fluency with partial fractions is what earns the marks.
>
> Every exam has asked for a **proof** of one property from the definition: the derivative rule (2023/24) or the second shift theorem (2025/26).

## Key Concepts
- [[Laplace Transform]] (SESA2027 note) · [[Laplace Transform Properties and Proofs]] · [[Partial Fractions for Inverse Laplace]]

---

## 1. Definition and existence (L11)
$$
\mathcal L[f(x)]=\tilde f(s)=\int_0^\infty f(x)\,e^{-sx}\,dx .
$$

Compare this with the Fourier transform: the Laplace integral runs over $[0,\infty)$, and $s$ replaces $j\omega$. On the line $\mathrm{Re}(s)=0$ it is essentially the Fourier transform of $fH$.

**Existence**: the transform may fail for some $s$, or for all $s$. Example:
$$
\mathcal L[e^{ax}]=\int_0^\infty e^{-(s-a)x}dx=\Big[\frac{e^{-(s-a)x}}{-(s-a)}\Big]_0^\infty=\frac{1}{s-a}\quad\text{only if }\mathrm{Re}(s)>a .
$$
For $s<a$ the integrand grows, and for $s=a$ the integral is $\int_0^\infty1\,dx=\infty$.

If $|f|\leq Ke^{ax}$ for large $x$, then $\tilde f$ exists for $\mathrm{Re}(s)>a$.

> [!important] Corollary used in every proof
> If $\tilde f(s)$ exists, then $\lim_{x\to\infty}f(x)e^{-sx}=0$. This is the condition the 2023/24 A1(a) question asks you to **state**.

## 2. Building the table from the definition (L11–12)
| $f(x)$ | $\tilde f(s)$ | Derivation |
|---|---|---|
| $1$ | $\dfrac1s$ ($s>0$) | $\big[-\frac{e^{-sx}}s\big]_0^\infty$ |
| $e^{ax}$ | $\dfrac1{s-a}$ ($s>a$) | above |
| $x^n$ | $\dfrac{n!}{s^{n+1}}$ | the $xf$ rule, applied $n$ times to $\mathcal L[1]$ |
| $\sin ax$ | $\dfrac{a}{s^2+a^2}$ | integrate by parts twice (below) |
| $\cos ax$ | $\dfrac{s}{s^2+a^2}$ | same, or $\frac{d}{dx}\sin ax=a\cos ax$ with the derivative rule |
| $\sinh ax$ | $\dfrac{a}{s^2-a^2}$ ($s>\lvert a\rvert$) | $\frac12(e^{ax}-e^{-ax})$ |
| $\cosh ax$ | $\dfrac{s}{s^2-a^2}$ | $\frac12(e^{ax}+e^{-ax})$ |
| $e^{-ax}f(x)$ | $\tilde f(s+a)$ | first shift theorem |
| $x\,f(x)$ | $-\tilde f'(s)$ | differentiate under the integral |

### $\mathcal L[\sin ax]$ by parts (L11)
With $u=\sin ax$ and $dv=e^{-sx}dx$:
$$
I=\Big[-\frac{\sin ax\,e^{-sx}}{s}\Big]_0^\infty+\frac as\int_0^\infty\cos ax\,e^{-sx}dx=\frac as\Big\{\Big[-\frac{\cos ax\,e^{-sx}}{s}\Big]_0^\infty-\frac as\int_0^\infty\sin ax\,e^{-sx}dx\Big\}=\frac a{s^2}-\frac{a^2}{s^2}I .
$$
So $I\big(1+\frac{a^2}{s^2}\big)=\frac{a}{s^2}$, which gives $I=\dfrac{a}{s^2+a^2}$ ✔.

**Complex shortcut** (Appendix): $\sin ax=\frac{e^{jax}-e^{-jax}}{2j}$, so
$$
\mathcal L[\sin ax]=\frac1{2j}\Big(\frac1{s-ja}-\frac1{s+ja}\Big)=\frac{1}{2j}\cdot\frac{2ja}{s^2+a^2}=\frac{a}{s^2+a^2} .
$$

## 3. Properties, with proofs
Full proofs are in [[Laplace Transform Properties and Proofs]]. In brief:

**Linearity**: $\mathcal L[\alpha f+\beta g]=\alpha\tilde f+\beta\tilde g$.

**Derivative** (prove it, and state the condition $f(x)e^{-sx}\to0$). Integrate by parts:
$$
\mathcal L[f']=\int_0^\infty f'e^{-sx}dx=\Big[fe^{-sx}\Big]_0^\infty+s\int_0^\infty fe^{-sx}dx=\underbrace{\lim_{x\to\infty}f e^{-sx}}_{=0}-f(0)+s\tilde f=s\tilde f(s)-f(0).
$$
Applying it to $f'$ gives
$$
\mathcal L[f'']=s\,\mathcal L[f']-f'(0)=s^2\tilde f-sf(0)-f'(0),
$$
and in general $\mathcal L[f^{(n)}]=s^n\tilde f-\sum_{k=0}^{n-1}s^{n-1-k}f^{(k)}(0)$.

**First shift theorem**:
$$
\mathcal L[e^{-ax}f]=\int_0^\infty fe^{-(s+a)x}dx=\tilde f(s+a).
$$

**Multiplication by $x$**:
$$
\frac{d\tilde f}{ds}=\int_0^\infty f\,\partial_s e^{-sx}dx=-\int_0^\infty xfe^{-sx}dx\ \Longrightarrow\ \mathcal L[xf]=-\frac{d\tilde f}{ds}.
$$
Example: $\mathcal L[x\cos ax]=-\frac{d}{ds}\frac{s}{s^2+a^2}=\frac{s^2-a^2}{(s^2+a^2)^2}$ (PS5 Q1c).

**Parameter derivative**: $\mathcal L[\partial_af]=\partial_a\tilde f$. For example, $\partial_a$ of $\mathcal L[\sin ax]$ gives $\mathcal L[x\cos ax]$ again.

**Integral**:
$$
\mathcal L\Big[\int_0^xf(z)dz\Big]=\frac1s\tilde f(s).
$$
*Proof*: let $g=\int_0^xf$. Then $g'=f$ and $g(0)=0$, so the derivative rule gives $\tilde f=s\tilde g-0$.

**Warning**: $\mathcal L[fg]\neq\mathcal L[f]\mathcal L[g]$. For example, $\mathcal L[x^2]=\frac2{s^3}$ but $\mathcal L[x]^2=\frac1{s^4}$.

## 4. Solving IVPs (L11–12)
> [!example] L11: $y''+y=0$, $y(0)=0$, $y'(0)=1$
> Transforming gives $s^2\tilde y-s\cdot0-1+\tilde y=0$, so $\tilde y=\frac1{s^2+1}$ and $y=\sin x$.

> [!example] L12: $y''+2y'+5y=2+5x$, $y(0)=0$, $y'(0)=3$
> 1. **Transform**: $(s^2\tilde y-3)+2s\tilde y+5\tilde y=\frac2s+\frac5{s^2}$.
> 2. **Solve for $\tilde y$**:
>    $$\tilde y=\frac{3+\frac2s+\frac5{s^2}}{s^2+2s+5}=\frac{3s^2+2s+5}{s^2(s^2+2s+5)} .$$
> 3. **Partial fractions**: write $\frac{3s^2+2s+5}{s^2(s^2+2s+5)}=\frac As+\frac B{s^2}+\frac{Cs+D}{s^2+2s+5}$.
>    Multiplying out, the numerator becomes $(A+C)s^3+(2A+B+D)s^2+(5A+2B)s+5B$. Match powers of $s$:
>    - $s^0$: $5B=5$, so $B=1$.
>    - $s^1$: $5A+2B=2$, so $A=0$.
>    - $s^2$: $2A+B+D=3$, so $D=2$.
>    - $s^3$: $A+C=0$, so $C=0$.
>
>    $$\tilde y=\frac1{s^2}+\frac{2}{(s+1)^2+4}$$
> 4. **Invert**: $\frac{2}{(s+1)^2+2^2}$ is $\mathcal L[\sin2x]$ shifted by $s\to s+1$, i.e. $\mathcal L[e^{-x}\sin2x]$ by the first shift theorem.
>
> $$y=x+e^{-x}\sin2x\ ✔\ \text{(SymPy)}$$

> [!example] L12: $y''+3y'+2y=x+e^{-x}$, $y(0)=y'(0)=0$
> 1. **Transform and solve**: $(s+1)(s+2)\tilde y=\frac1{s^2}+\frac1{s+1}$, so
>    $$\tilde y=\frac{1+s+s^2}{s^2(s+1)^2(s+2)} .$$
> 2. **Partial fractions**: $\tilde y=\frac{as+b}{s^2}+\frac{cs+d}{(s+1)^2}+\frac{f}{s+2}$.
>    - Cover-up: $s=-2$ gives $f=\frac34$; $s=0$ gives $b=\frac12$; $s=-1$ gives $d-c=1$.
>    - Two more values ($s=1,2$) give $a=-\frac34$ and $c=0$, so $d=1$.
>
>    $$\tilde y=-\frac{3}{4s}+\frac1{2s^2}+\frac1{(s+1)^2}+\frac{3}{4(s+2)}$$
> 3. **Invert**:
>    $$y=-\frac34+\frac x2+xe^{-x}+\frac34e^{-2x}$$
> 4. **Check**: $y(0)=-\frac34+\frac34=0$ ✔. SymPy's `apart` and `dsolve` both agree ✔.

## 5. Partial fractions toolkit
| Denominator factor | Term(s) | Inverse |
|---|---|---|
| $(s+a)$ | $\frac{A}{s+a}$ | $Ae^{-ax}$ |
| $(s+a)^n$ | $\frac{A_1}{s+a}+\dots+\frac{A_n}{(s+a)^n}$ | $A_k\frac{x^{k-1}}{(k-1)!}e^{-ax}$ |
| $(s+c)^2+b^2$ (irreducible) | $\frac{B(s+c)+Cb}{(s+c)^2+b^2}$ | $e^{-cx}(B\cos bx+C\sin bx)$ |

- **Complete the square**: $s^2+2s+5=(s+1)^2+4$.
- **Split the numerator to match**: $\frac{s+3}{(s+1)^2+4}=\frac{(s+1)}{(s+1)^2+4}+\frac{2}{(s+1)^2+4}$, which inverts to $e^{-x}(\cos2x+\sin2x)$ (PS5 Q2c).
- **Finding coefficients**: use cover-up at the roots, then either match powers of $s$ or substitute convenient values of $s$.

See [[Partial Fractions for Inverse Laplace]].

## 6. Extra results from the Lecture Notes (Ch. 4)
- **Existence theorem (4.2.1).** Suppose $f$ is piecewise continuous on every $[0,A]$ and $|f(x)|\leq Ke^{ax}$ for $x\geq M$. Then $\tilde f(s)$ exists for $s>a$, and $\lim_{x\to\infty}fe^{-sx}=0$.
- **Higher derivatives (4.15).** $\mathcal L[f^{(n)}]=s^n\tilde f-\sum_{k=0}^{n-1}s^{n-k-1}f^{(k)}(0)$. This needs $f^{(k)}e^{-sx}\to0$ for every $k\leq n$.
- **General second-order result (4.38).** For $ay''+by'+cy=f(x)$:
$$\tilde y=\frac{\tilde f+a\,y(0)\,s+\big(a\,y'(0)+b\,y(0)\big)}{as^2+bs+c}.$$
  The initial conditions enter only the numerator, and the denominator is the auxiliary polynomial.
- **Uniqueness (4.4).** If $\mathcal L[f_1]=\mathcal L[f_2]$, then $f_1=f_2$ (for continuous $f$). This one-to-one correspondence is why **table look-up is a valid way to invert**.
- *(Beyond the course)* The Bromwich contour-integral inversion formula, $f=\frac1{2\pi j}\int_{\gamma-j\infty}^{\gamma+j\infty}\tilde fe^{sx}ds$.
- *(Not examined)* **Convolution**: $\mathcal L\big[\int_0^xf(u)g(x-u)\,du\big]=\tilde f\tilde g$. The proof swaps the order of integration and substitutes $z=x-u$.
- *(Not examinable)* **Systems of ODEs**: $\mathbf y'-A\mathbf y=\mathbf f$ transforms to $(sI-A)\tilde{\mathbf y}=\tilde{\mathbf f}+\mathbf y(0)$. This can be solved whenever $s$ is not an eigenvalue of $A$, which connects to SESA2027 [[State-Space Representation]].

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 TR1 - Fourier Transforms]] · Next: [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]
- Practice: [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]] (PS5 Q1–3d) · [[MATH2048 Past Paper Solutions]] (A1 in every year)

## Sources
- Lectures 11–12; Laplace Appendix; Lecture Notes Ch. 4. Every example was re-derived and checked with SymPy `laplace_transform`, `apart` and `dsolve`.
