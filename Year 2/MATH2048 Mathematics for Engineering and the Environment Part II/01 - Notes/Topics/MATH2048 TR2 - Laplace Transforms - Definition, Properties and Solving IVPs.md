---
title: "MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 3: Fourier and Laplace Transforms"
order: 8
tags:
  - math2048
  - laplace-transform
  - initial-value-problems
aliases: ["MATH2048 Lecture 11", "MATH2048 Lecture 12", "Laplace transform"]
date: 2026-10-30
status: lectured
coverage: "Lecture 11 (22 Oct 2024): why Laplace rather than Fourier, the definition and existence, transforms of e^{at} and sin at, the first shift theorem, transforms of derivatives, and y'' + y = 0 solved by Laplace. Lecture 12 (23 Oct 2024): linearity, multiplication by x, powers of x, parameters and PDEs, the transform of an integral, an IVP with a polynomial source, partial fractions, and why the transform of a product is not the product. Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 TR1 - Fourier Transforms]]", "[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]"]
next_topics: ["[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
key_concepts: ["[[Laplace Transform Properties and Proofs]]", "[[Partial Fractions for Inverse Laplace]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 11.txt", "02 - Sources/Lectures/MATH2048 Lecture 12.txt", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture11_LaplaceTransform1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture12_LaplaceTransform2.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 4)"]
---

# MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs

> [!abstract] Summary
> The Laplace transform $\tilde f(s)=\int_0^\infty f(x)e^{-sx}\,dx$ is the Fourier transform adapted to initial value problems: it starts at $0$, uses a real decaying exponential and has no normalisation factor. It turns derivatives into algebra with the initial conditions built in, $\mathcal L[y']=s\tilde y-y(0)$ and $\mathcal L[y'']=s^2\tilde y-sy(0)-y'(0)$, so an IVP becomes an algebraic equation for $\tilde y$. Since there is no practical inversion formula, $\tilde y$ is split by partial fractions into terms recognisable from the formula-sheet table, using linearity and the first shift theorem $\mathcal L[e^{-ax}f]=\tilde f(s+a)$.

> [!summary]- Exam use: quick path
> - **Use it when:** an initial value problem has a source that undetermined coefficients can't handle, or the question says "use Laplace transforms" (exam A1(b)); A1(a) asks for a proof from the definition.
> - **Assumptions:** $f(x)e^{-sx}\to0$ as $x\to\infty$ for the $s$ in use (in practice $s>a$ for growth like $e^{ax}$); conditions given at $x=0$; linear constant-coefficient ODE.
> - **Method:** 1. Transform each term with linearity, $\mathcal L[y']$ and $\mathcal L[y'']$, and the table for the source. 2. Substitute the initial conditions immediately. 3. Solve for $\tilde y$. 4. Split by partial fractions; complete the square for irreducible quadratics. 5. Invert each term from the table, using the first shift theorem for $s+a$.
> - **Common mistakes:** writing $\mathcal L[y'']=s^2\tilde y$ and dropping the initial values; assuming $\mathcal L[fg]=\tilde f\tilde g$.
> - **Practise:** [[#An IVP with a polynomial source (L12)]] · [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms|PS5 Q3]]

The Laplace transform keeps the useful part of the Fourier transform and drops two inconveniences (L11, ll. 20–42). Fourier transforms carry $j$ everywhere, so every calculation is complex, and they run over all time, $-\infty$ to $\infty$, whereas an initial value problem starts at $x=0$ and has no meaningful past. So the Laplace transform starts its integral at zero, replaces $e^{-j\omega t}$ by the real $e^{-sx}$, and needs no normalisation factor. Both are integral transforms of the form $\int_a^bK(s,x)f(x)\,dx$ with different kernels $K$ (ll. 58–69).

The method is a detour through "frequency space" (ll. 7–15): transform the ODE and its initial conditions, solve the resulting algebra, and transform back. For a constant-coefficient ODE with a simple source, the ODE1–ODE2 methods are quicker. The detour pays when the source is awkward, above all when it switches on or off suddenly or acts in an instant, which is [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem|TR3]] (ll. 16–19).

One difference in the bookkeeping is worth noticing (ll. 403–418). Solving an ODE directly, you write the general solution with its arbitrary constants and fix them at the very end. With a Laplace transform the initial conditions go in at the start, the moment you transform a derivative, so there are never any arbitrary constants to fix. The other difference is the way back: there is an inversion integral, but it is a contour integral in the complex plane and not practical, so in practice you invert by recognising entries in a table (ll. 419–426).

---

## 1. Definition and existence (L11)

$$
\tilde f(s)=\mathcal L[f(x)]=\int_0^\infty f(x)\,e^{-sx}\,dx .
$$

The transformed function is written with a tilde, and $s$, like $\omega$, is called a frequency (ll. 13–14, 37–38). The course uses $\mathcal L$ both for the Laplace transform and for a general linear differential operator, so read it from context (ll. 71–74).

### The exponential, and when the transform exists

For $f=e^{ax}$ with $a$ real (ll. 70–148):

$$
\mathcal L[e^{ax}]=\int_0^\infty e^{(a-s)x}\,dx=\left[\frac{e^{-(s-a)x}}{-(s-a)}\right]_0^\infty .
$$

The lower limit gives $\frac1{s-a}$. At the upper limit, $e^{-(s-a)x}\to0$ only if $s>a$; if $s<a$ it blows up, and if $s=a$ the integrand is 1 and the integral is infinite. So

$$
\mathcal L[e^{ax}]=\frac1{s-a},\qquad s>a .
$$

In general the transform exists for a given $s$ when $f(x)e^{-sx}\to0$ as $x\to\infty$, that is, when $f$ grows no faster than some exponential that $e^{-sx}$ can beat (ll. 154–165). Unlike the Fourier transform, it only exists for some frequencies, so it is less general, but its real exponential kernel decays, so far more functions have one: constants, polynomials and growing exponentials all do.

### The sine, by parts twice

For $\mathcal L[\sin ax]=\int_0^\infty\sin ax\,e^{-sx}\,dx$ neither factor differentiates to zero, so integrate by parts twice and rearrange, integrating the exponential each time (ll. 166–226). First:

$$
\int_0^\infty\sin ax\,e^{-sx}\,dx=\left[-\frac{\sin ax\,e^{-sx}}{s}\right]_0^\infty+\frac as\int_0^\infty\cos ax\,e^{-sx}\,dx .
$$

The bracket is zero at both ends ($e^{-sx}\to0$ at infinity, $\sin0=0$ at zero). Second:

$$
\frac as\int_0^\infty\cos ax\,e^{-sx}\,dx=\frac as\left(\left[-\frac{\cos ax\,e^{-sx}}{s}\right]_0^\infty-\frac as\int_0^\infty\sin ax\,e^{-sx}\,dx\right)=\frac a{s^2}-\frac{a^2}{s^2}\mathcal L[\sin ax].
$$

The original integral has reappeared, so collect it:

$$
\Big(1+\frac{a^2}{s^2}\Big)\mathcal L[\sin ax]=\frac a{s^2}
$$

$$
\mathcal L[\sin ax]=\frac{a}{s^2+a^2},\qquad s>0 .
$$

The same steps give $\mathcal L[\cos ax]=\frac{s}{s^2+a^2}$, which the lecturer recommended doing as an exercise (ll. 226–229).

## 2. Properties (L11–L12)

The formula sheet on Blackboard lists the standard transforms and the theorems, and the lecturer was emphatic that it is "the first place that you should look", not something to memorise (L11, ll. 229–235; L12, ll. 14–29). The results below are the ones derived in the lectures.

### Linearity

$\mathcal L[\alpha f+\beta g]=\alpha\tilde f+\beta\tilde g$, by exactly the argument used for the Fourier transform in [[MATH2048 TR1 - Fourier Transforms#Linearity|TR1]]: the integral of a sum is the sum of the integrals, and constants pass through (L12, ll. 41–47). The transform of a product is **not** the product of the transforms (L12, ll. 420–436). The simplest counterexample is $1=1\times1$: $\mathcal L[1]=\frac1s$, but $\mathcal L[1]\,\mathcal L[1]=\frac1{s^2}$.

### The first shift theorem

Multiplying by an exponential shifts the frequency (L11, ll. 236–276):

$$
\mathcal L[e^{-ax}f(x)]=\int_0^\infty f(x)e^{-ax}e^{-sx}\,dx=\int_0^\infty f(x)e^{-(s+a)x}\,dx=\tilde f(s+a).
$$

So $\mathcal L[e^{-bx}\sin x]=\frac1{(s+b)^2+1}$ without any integration: take $\mathcal L[\sin x]=\frac1{s^2+1}$ and replace $s$ by $s+b$.

### Derivatives

From the definition, integrating $f'$ by parts (L11, ll. 278–302):

$$
\mathcal L[f']=\Big[f(x)e^{-sx}\Big]_0^\infty-\int_0^\infty f(x)(-s)e^{-sx}\,dx .
$$

The upper limit vanishes because the transform exists ($fe^{-sx}\to0$); the lower limit gives $-f(0)$:

$$
\mathcal L[f']=s\tilde f-f(0).
$$

The second derivative is the first derivative of $f'$, so apply the rule twice (ll. 319–330):

$$
\mathcal L[f'']=s\,\mathcal L[f']-f'(0)=s^2\tilde f-sf(0)-f'(0).
$$

Compared with the Fourier rule $\mathcal F[f']=j\omega F$, the frequency $j\omega$ has become $s$, and because the integral now starts at $0$, where $f$ needn't vanish, the initial value appears (ll. 304–317).

### Multiplication by x, and the powers of x

Differentiate the transform with respect to $s$ (L12, ll. 48–99). The limits don't depend on $s$, so the derivative passes inside the integral:

$$
\frac{d\tilde f}{ds}=\int_0^\infty f(x)\frac{\partial}{\partial s}e^{-sx}\,dx=\int_0^\infty f(x)(-x)e^{-sx}\,dx=-\mathcal L[xf(x)].
$$

So $\mathcal L[xf]=-\frac{d\tilde f}{ds}$, and more generally $\mathcal L[x^nf]=(-1)^n\frac{d^n\tilde f}{ds^n}$. The lecturer first wrote $-s\tilde f$ here before catching that the $x$ from differentiating the exponential can't come out of the integral (ll. 72–81). For example, $\mathcal L[xe^{ax}]=-\frac{d}{ds}\frac1{s-a}=\frac1{(s-a)^2}$.

Starting from $\mathcal L[1]=\int_0^\infty e^{-sx}\,dx=\frac1s$ (ll. 102–123) and applying the rule repeatedly:

$$
\mathcal L[x]=-\frac{d}{ds}\frac1s=\frac1{s^2},\qquad\mathcal L[x^2]=-\frac{d}{ds}\frac1{s^2}=\frac2{s^3},\qquad\mathcal L[x^n]=\frac{n!}{s^{n+1}} .
$$

Combined with the first shift theorem, $\mathcal L[x^ne^{-bx}]=\frac{n!}{(s+b)^{n+1}}$. The practical message for inverting is that anything written as a sum of $\frac1{s^n}$ or $\frac1{(s+b)^n}$ inverts to polynomials, possibly times an exponential (ll. 136–159).

### Parameters, and transforming a PDE

If $f$ depends on a parameter $a$ as well as $x$, then $\mathcal L\big[\frac{\partial f}{\partial a}\big]=\frac{\partial\tilde f}{\partial a}$, because the integral is over $x$ only (ll. 160–188). The parameter can be another coordinate, which is how a Laplace transform simplifies a PDE: transforming $\partial_xf+\partial_yf=g(x)$ in $x$ gives $s\tilde f-f(0,y,z)+\partial_y\tilde f=\tilde g$, an equation with derivatives in $y$ only, so a PDE in two variables becomes an ODE.

### Integrals

The transform of an integral (ll. 189–217), by parts with the integral differentiated:

$$
\mathcal L\Big[\int_0^xf(u)\,du\Big]=\frac1s\tilde f(s).
$$

The boundary term vanishes at both ends, at infinity because of $e^{-sx}$ and at zero because the integral from $0$ to $0$ is zero. The lecturer noted it is rarely used, since there are usually easier routes.

> [!check] SymPy
> `laplace_transform` gives $\frac1{s-a}$, $\frac a{s^2+a^2}$, $\frac s{s^2+a^2}$, $\frac6{s^4}$ for $x^3$, $\frac1{(s-a)^2}$ for $xe^{ax}$, and $\frac1{(s+2)^2+1}$ for $e^{-2x}\sin x$.

## 3. Solving initial value problems

### The harmonic oscillator (L11)

Solve $y''+y=0$ with $y(0)=0$, $y'(0)=1$, a pendulum kicked from rest (ll. 332–402). By ODE1 the answer is $y=\sin x$. With the Laplace transform, transform both sides:

$$
\big(s^2\tilde y-sy(0)-y'(0)\big)+\tilde y=0 .
$$

Substitute the initial conditions straight away:

$$
s^2\tilde y-1+\tilde y=0\quad\Longrightarrow\quad\tilde y=\frac1{s^2+1}.
$$

The table has $\mathcal L[\sin x]=\frac1{s^2+1}$, so $y=\sin x$, with no guess about the form of the solution.

### An IVP with a polynomial source (L12)

Solve $y''+2y'+5y=2+5x$ with $y(0)=0$, $y'(0)=3$ (ll. 219–294). Transform term by term:

$$
\big(s^2\tilde y-0-3\big)+2\big(s\tilde y-0\big)+5\tilde y=\frac2s+\frac5{s^2}.
$$

Collect:

$$
(s^2+2s+5)\tilde y=3+\frac2s+\frac5{s^2}.
$$

The lecturer's trick (ll. 235–247) is to write the right-hand side so that the quadratic appears in it:

$$
3+\frac2s+\frac5{s^2}=2+\frac{s^2+2s+5}{s^2},
$$

so that dividing through gives

$$
\tilde y=\frac{2}{s^2+2s+5}+\frac1{s^2}.
$$

The quadratic doesn't factor over the reals, so complete the square (ll. 253–271):

$$
s^2+2s+5=(s+1)^2+2^2 .
$$

The table gives $\mathcal L[\sin2x]=\frac{2}{s^2+2^2}$, and the first shift theorem with $e^{-x}$ turns $s$ into $s+1$, so $\frac{2}{(s+1)^2+2^2}$ inverts to $e^{-x}\sin2x$. The second term is $\mathcal L[x]$. Hence

$$
y=e^{-x}\sin2x+x .
$$

> [!check] Initial conditions
> $y(0)=0$, and $y'=-e^{-x}\sin2x+2e^{-x}\cos2x+1$ gives $y'(0)=2+1=3$. SymPy's `dsolve` returns $x+e^{-x}\sin2x$.

### Partial fractions, the systematic route (L12)

Spotting the right rearrangement is trial and error; partial fractions is the systematic version (ll. 305–334). Any $\tilde y$ that is a ratio of polynomials can be split into a sum of simple fractions, one for each factor of the denominator: $\frac{A}{s+a}$ for a linear factor, $\frac{A_1}{s+a}+\dots+\frac{A_n}{(s+a)^n}$ for a repeated one, and $\frac{Bs+C}{(s+a)^2+b^2}$ for an irreducible quadratic. Each then inverts from the table, to an exponential, to $x^{n-1}e^{-ax}$, or to $e^{-ax}\cos bx$ and $e^{-ax}\sin bx$.

The lecture's example (ll. 338–419) is $y''+3y'+2y=x+e^{-x}$ with $y(0)=y'(0)=0$. Transform, with zero initial data:

$$
(s^2+3s+2)\tilde y=\frac1{s^2}+\frac1{s+1}.
$$

Factorise the quadratic, as the lecturer advised doing whenever possible, and divide:

$$
\tilde y=\frac{1}{s^2(s+1)(s+2)}+\frac{1}{(s+1)^2(s+2)}=\frac{s^2+s+1}{s^2(s+1)^2(s+2)}.
$$

Write

$$
\tilde y=\frac A{s+2}+\frac B{s+1}+\frac C{(s+1)^2}+\frac Ds+\frac E{s^2},
$$

and multiply through by $s^2(s+1)^2(s+2)$:

$$
s^2+s+1=As^2(s+1)^2+Bs^2(s+1)(s+2)+Cs^2(s+2)+Ds(s+1)^2(s+2)+E(s+1)^2(s+2).
$$

This holds for every $s$, so choose values that kill most terms (ll. 387–402). At $s=0$: $1=2E$, so $E=\frac12$. At $s=-1$: $1=C\cdot1\cdot1$, so $C=1$. At $s=-2$: $3=4A$, so $A=\frac34$. The remaining two need two more equations, from two more values of $s$ or by comparing powers (ll. 403–410). Comparing the $s^4$ terms gives $A+B+D=0$, and $s=1$ gives $3=4A+6B+3C+12D+12E$, that is $6B+12D=-9$; together these give $B=0$ and $D=-\frac34$. So

$$
\tilde y=\frac{3/4}{s+2}+\frac{1}{(s+1)^2}-\frac{3/4}{s}+\frac{1/2}{s^2},
$$

and inverting term by term,

$$
y=\tfrac34e^{-2x}+xe^{-x}-\tfrac34+\tfrac12x .
$$

> [!check] SymPy
> `apart` gives exactly these five coefficients, and `dsolve` on the original ODE returns $\frac x2+xe^{-x}-\frac34+\frac34e^{-2x}$. The lecture stopped after $A$, $C$ and $E$, saying the rest follow the same way.

## Transcript slips

> [!warning] Lectures 11 and 12
> | Where | Transcript says | Correct |
> |---|---|---|
> | L11, l. 41 | the Fourier normalisation factors multiply to "1 over root 2 pi" | $\frac1{2\pi}$, as said correctly at l. 22 of L10 |
> | L11, l. 78 | "assuming that f is equal to e to the a s" | $f=e^{ax}$ |
> | L11, l. 144 | the transform of $e^{ax}$ exists if "S is strictly greater than 0" | $s>a$; l. 147 then says this correctly |
> | L11, l. 222 | "Laplace transform of sine of AT is equal to A on S squared" | that is the intermediate step $(1+a^2/s^2)\mathcal L[\sin at]=a/s^2$; the result is $a/(s^2+a^2)$ |
> | L11, ll. 422–424 | the slide says there is no inverse Laplace transform; the lecturer calls this "a lie" | an inverse exists (a complex contour integral) but isn't practical; invert from the table |
> | L12, ll. 62–80 | $\frac{d\tilde f}{ds}=-s\tilde f$, then corrected | $\frac{d\tilde f}{ds}=-\mathcal L[xf]$ |
> | L12, l. 233 | "this is 5 on x squared" | $5/s^2$ |
> | L12, l. 188 | "PDAs" | PDEs |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 TR1 - Fourier Transforms]] · Next: [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]
- SESA2027 uses the same transform for transfer functions: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · [[Laplace Transform]]
- Concepts: [[Laplace Transform Properties and Proofs]] · [[Partial Fractions for Inverse Laplace]]

## Sources

- Lecture 11 (22 Oct 2024) and Lecture 12 (23 Oct 2024) recordings, Ian Hawke: `MATH2048 Lecture 11.txt`, `MATH2048 Lecture 12.txt`
- Slides `Lecture11_LaplaceTransform1.pdf`, `Lecture12_LaplaceTransform2.pdf`; formula sheet FS/MATH2048; lecture notes Ch. 4
- Problem Sheet 5; worked solutions in [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]

## Self-study tasks

Lecture 11 suggested deriving $\mathcal L[\cos ax]$ the same way as the sine (ll. 226–229) and getting to know the formula sheet; Lecture 12 ended with "practice partial fractions. You are going to need them" (ll. 439–440) and pointed to the week-5 STACK partial-fractions question (l. 337).

### Core

- [ ] Lecturer-set (L11, ll. 226–229): derive $\mathcal L[\cos ax]=\frac s{s^2+a^2}$ by parts twice. → [[#The sine, by parts twice]]
- [ ] Prove $\mathcal L[f']=s\tilde f-f(0)$ and $\mathcal L[f'']=s^2\tilde f-sf(0)-f'(0)$ from the definition (an exam A1(a) type). → [[#Derivatives]]
- [ ] PS5 Q2: invert $\frac1{s(s-3)}$, $\frac6{(s+2)^2+9}$, $\frac{s+3}{s^2+2s+5}$ and $\frac1{s(s+1)(s+2)}$. Answers: $\frac13(e^{3x}-1)$; $2e^{-2x}\sin3x$; $e^{-x}(\cos2x+\sin2x)$; $\frac12-e^{-x}+\frac12e^{-2x}$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] Lecturer-set (L12, ll. 403–419): finish the partial fractions of the $y''+3y'+2y=x+e^{-x}$ example and check $B=0$, $D=-\frac34$. → [[#Partial fractions, the systematic route (L12)]]

### Further practice

- [ ] PS5 Q1: transforms of $\sinh ax$, $4\sin x\cos x$, $x\cos ax$ and $e^{-x}\sin2x$ from the definition. Answers: $\frac a{s^2-a^2}$; $\frac4{s^2+4}$; $\frac{s^2-a^2}{(s^2+a^2)^2}$; $\frac2{(s+1)^2+4}$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] PS5 Q3(a)–(d), four IVPs. Answers: $\frac15e^{3x}+\frac45e^{-2x}$; $e^x(2\cosh\sqrt3x-\frac2{\sqrt3}\sinh\sqrt3x)$; $\frac15(\cos x-2\sin x)+\frac25e^x(2\cos x-\sin x)$; $e^{-x}(2+x+2x^2)$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] Show $\mathcal L[x^n]=\frac{n!}{s^{n+1}}$ by induction from the multiplication-by-$x$ rule (suggested, not lecturer-set). → [[#Multiplication by x, and the powers of x]]
