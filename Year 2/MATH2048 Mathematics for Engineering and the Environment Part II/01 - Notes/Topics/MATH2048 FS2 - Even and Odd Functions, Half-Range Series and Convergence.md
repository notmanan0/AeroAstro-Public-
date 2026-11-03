---
title: "MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 2: Fourier Series"
order: 5
tags:
  - math2048
  - fourier-series
  - half-range
  - convergence
aliases: ["MATH2048 Lecture 6", "Half-range series", "Fourier sine series", "Fourier cosine series"]
date: 2026-10-30
status: lectured
coverage: "Lecture 6 (9 Oct 2024, Ian Hawke): the general period 2L, even and odd functions and their integrals, the three half-range extensions with f = x on [0, π] done each way, and the Dirichlet conditions for convergence, including hidden discontinuities and the average at a jump."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]"]
next_topics: ["[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
key_concepts: ["[[Half-Range Expansions]]", "[[Fourier's Theorem]]", "[[Fourier Series]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 6.txt", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture6_FourierSeries3.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§2.2–2.4)"]
---

# MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence

> [!abstract] Summary
> On an interval $[-L,L]$ the Fourier series uses $\cos\frac{n\pi x}{L}$ and $\sin\frac{n\pi x}{L}$ with the factor $\frac1L$ in the Euler formulae. Symmetry halves the work: an even function has only cosine terms and an odd one only sine terms, with the surviving coefficients computed over $[0,L]$ and doubled. A function given only on $[0,L]$ can be extended periodically, evenly (a cosine series) or oddly (a sine series), and the choice is set by the boundary conditions in a PDE. A Fourier series converges wherever the Dirichlet conditions hold, to $f$ where it is continuous and to the average of the two one-sided limits at a jump.

> [!summary]- Exam use: quick path
> - **Use it when:** a function is given on $[0,L]$ and has to be expanded in sines only or cosines only (the initial-data fit in a PDE), or a function has an obvious symmetry.
> - **Assumptions:** $f$ satisfies the Dirichlet conditions (bounded, finitely many extrema and jumps per period); integrals over a symmetric interval $[-L,L]$.
> - **Method:** 1. Decide the extension (from the question or the boundary conditions: zero value at the ends gives a sine series, zero slope a cosine series). 2. Sketch the extension, including any hidden jumps. 3. Write only the surviving coefficients, $\frac2L\int_0^L f\sin\frac{n\pi x}L\,dx$ or $\frac2L\int_0^L f\cos\frac{n\pi x}L\,dx$ (and $a_0$). 4. Integrate by parts. 5. At a jump, the series gives the average of the two sides.
> - **Common mistakes:** using $\frac1L$ instead of $\frac2L$ for a half-range series; evaluating a series at a hidden discontinuity and quoting $f$ instead of the average.
> - **Practise:** [[#Example: f = x on the interval from 0 to π, three ways]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|PS3 Q2]]

Lecture 5 calculated every coefficient by brute force and found that many of them came out zero. That wasn't luck: it happened because the functions were even or odd, and noticing the symmetry first saves half the work (L6, ll. 1–4). The sine is odd and the cosine even, so an even function has nothing in common with the sines and an odd function nothing in common with the cosines.

The same idea answers a practical question. In a physical problem the function usually lives on a bar from $0$ to $L$, not on a symmetric interval, so we are free to invent what it does between $-L$ and $0$ before extending it periodically. Inventing it as a mirror image makes it even and gives a cosine series; inventing it upside-down makes it odd and gives a sine series. Which invention is right depends on what happens at the ends of the bar, which is how half-range series connect to boundary conditions in the PDE block.

The last question is whether the series actually equals the function. The answer is almost always yes, with one catch: at a jump the series can't pick one side, so it takes the average. Jumps also hide in places that aren't obvious, at the joins between periodic copies.

---

## 1. Fourier series on a general interval (L6)

To move from $(-\pi,\pi)$ to a domain $(-L,L)$, change variable (ll. 6–45). Let

$$
x=\frac{\pi}{L}x',\qquad dx=\frac\pi L\,dx',
$$

so that $x\in(-\pi,\pi)$ becomes $x'\in(-L,L)$. Substituting into the series:

$$
f(x')\sim\frac12a_0+\sum_{n=1}^{\infty}\Big(a_n\cos\frac{n\pi x'}{L}+b_n\sin\frac{n\pi x'}{L}\Big).
$$

In the Euler formula the $\frac1\pi$ outside combines with the $\frac\pi L$ from $dx$:

$$
a_n=\frac1\pi\int_{-L}^{L}f(x')\cos\frac{n\pi x'}{L}\,\frac\pi L\,dx'=\frac1L\int_{-L}^{L}f(x')\cos\frac{n\pi x'}{L}\,dx',
$$

and likewise $b_n=\frac1L\int_{-L}^{L}f\sin\frac{n\pi x}{L}\,dx$, dropping the prime. Two checks keep the formulae straight (ll. 25–40): at the ends $x=\pm L$ the argument $n\pi x/L$ is an integer multiple of $\pi$, so a whole number of half-waves fits the domain; and the factor in front is one over half the length of the domain. Setting $L=\pi$ recovers FS1.

## 2. Even and odd functions (L6)

A function is **even** if $g(-x)=g(x)$, symmetric about $x=0$ like the tent $|x|$ or $\cos x$, and **odd** if $h(-x)=-h(x)$, like the sawtooth $x$ or $\sin x$ (ll. 50–63). Most functions are neither.

### The integral of an even or odd function over a symmetric interval

Split any integral at zero (ll. 64–121):

$$
\int_{-L}^{L}g(x)\,dx=\int_{-L}^{0}g(x)\,dx+\int_0^{L}g(x)\,dx.
$$

In the first piece substitute $z=-x$, so $dz=-dx$ and the limits $-L,0$ become $L,0$:

$$
\int_{-L}^{0}g(x)\,dx=\int_{L}^{0}g(-z)(-dz).
$$

Reversing the limits flips the sign, cancelling the minus from $dz$:

$$
=\int_0^{L}g(-z)\,dz.
$$

For an even function $g(-z)=g(z)$, and the name of the dummy variable doesn't matter, so

$$
\int_{-L}^{L}g\,dx=\int_0^Lg\,dz+\int_0^Lg\,dx=2\int_0^{L}g(x)\,dx .
$$

For an odd function $h(-z)=-h(z)$ instead, and the two halves cancel:

$$
\int_{-L}^{L}h\,dx=-\int_0^Lh\,dz+\int_0^Lh\,dx=0 .
$$

This holds for any $L$: an integrable odd function always integrates to zero over a symmetric interval.

### Products

Products follow the sign rules for multiplying $\pm1$: odd times even is odd, and even times even and odd times odd are even (ll. 128–142). For $g$ even and $h$ odd, put $z(x)=g(x)h(x)$:

$$
z(-x)=g(-x)h(-x)=g(x)\cdot\big(-h(x)\big)=-z(x),
$$

so $z$ is odd; the other two cases go the same way.

### What this does to the coefficients

The three Euler integrals have $f$, $f\cos$ and $f\sin$ under them, with $\cos$ even and $\sin$ odd (ll. 143–163).

If $f$ is even, $f\cos\frac{n\pi x}L$ is even and $f\sin\frac{n\pi x}L$ is odd, so

$$
b_n=0,\qquad a_n=\frac2L\int_0^Lf(x)\cos\frac{n\pi x}{L}\,dx .
$$

If $f$ is odd, the reverse:

$$
a_n=0\ (\text{including }a_0),\qquad b_n=\frac2L\int_0^Lf(x)\sin\frac{n\pi x}{L}\,dx .
$$

Spot the symmetry, quote the vanishing coefficients, and compute only the other half over the right-hand half of the interval, doubled. That explains FS1: the sawtooth $x$ is odd and had only sine terms, and the tent $|x|$ is even and had only cosine terms.

## 3. Half-range series (L6)

A **half-range series** expands a function given only on half the expected range, $0\leq x\leq L$ (ll. 165–224). There are three ways to fill in the rest.

The periodic extension simply repeats the given piece with period $L$. Nothing is symmetric, so all the coefficients are generally non-zero, but the formulae change because the period is now $L$ rather than $2L$: with half-length $\frac L2$,

$$
a_n=\frac2L\int_0^Lf(x)\cos\frac{2n\pi x}{L}\,dx,\qquad b_n=\frac2L\int_0^Lf(x)\sin\frac{2n\pi x}{L}\,dx .
$$

The even extension mirrors $f$ about $x=0$, giving an even function of period $2L$, and then repeats it. Only cosines survive, a **Fourier cosine series**:

$$
f\sim\frac12a_0+\sum_{n=1}^\infty a_n\cos\frac{n\pi x}{L},\qquad a_n=\frac2L\int_0^Lf(x)\cos\frac{n\pi x}{L}\,dx .
$$

The odd extension mirrors $f$ about both axes, giving an odd function, and only sines survive, a **Fourier sine series**:

$$
f\sim\sum_{n=1}^\infty b_n\sin\frac{n\pi x}{L},\qquad b_n=\frac2L\int_0^Lf(x)\sin\frac{n\pi x}{L}\,dx .
$$

### Which extension goes with which boundary condition

These choices look artificial, but they are dictated by the boundary conditions of a PDE on $[0,L]$ (ll. 186–205). A sine series is zero at $x=0$ and $x=L$, because every $\sin\frac{n\pi x}{L}$ is; it suits a Dirichlet condition with the solution held at zero at the ends, such as a string fixed at both ends. A cosine series has zero slope at $x=0$ and $x=L$, because every derivative $-\frac{n\pi}L\sin\frac{n\pi x}{L}$ vanishes there; it suits a Neumann condition, such as an insulated end with no heat flux. These are exactly the eigenfunctions of the Dirichlet and Neumann eigenproblems in [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems#4. The standard eigenproblems (PS2 Q3, preview of the PDE block)|ODE3 §4]].

> [!warning] The lecture pairs these the wrong way round (L6, ll. 197–202)
> The transcript says "Dirichlet boundary conditions typically match up with even extensions" and links Neumann or reflection conditions with odd ones. It is the other way round: a zero value at the boundary (Dirichlet) means an odd extension and a sine series, and a zero slope (Neumann) means an even extension and a cosine series. The lecture's own no-penetration example, where the normal velocity vanishes at a wall and the mirror-image flow is odd (ll. 199–204), is really a Dirichlet condition on the velocity, so it agrees with the corrected pairing.

### Example: f = x on the interval from 0 to π, three ways

Take $f(x)=x$ on $0\leq x<\pi$ (ll. 225–361), so $L=\pi$.

**Periodic extension, period $\pi$.** The constant:

$$
a_0=\frac2\pi\int_0^\pi x\,dx=\frac2\pi\cdot\frac{\pi^2}2=\pi .
$$

For $b_m$, integrate by parts with $u=x$ and $v'=\sin2mx$, keeping each term over its own power of $2m$ as the lecturer recommends (ll. 255–263):

$$
b_m=\frac2\pi\left[-\frac{x\cos2mx}{2m}+\frac{\sin2mx}{(2m)^2}\right]_0^\pi .
$$

The sine vanishes at both ends and the cosine term vanishes at $x=0$, leaving

$$
b_m=\frac2\pi\left(-\frac{\pi\cos2m\pi}{2m}\right)=-\frac{1}{m},
$$

since $\cos2m\pi=1$ for every $m$: the argument is always an even multiple of $\pi$, so the alternating $(-1)^m$ of FS1 disappears (ll. 264–283). The $a_m$ vanish in the same way, so

$$
x\sim\frac\pi2-\sum_{n=1}^\infty\frac{\sin2nx}{n}\qquad(0<x<\pi).
$$

**Even extension.** Mirroring $x$ about zero gives $|x|$ on $(-\pi,\pi)$, so the periodic even extension is exactly FS1's tent (ll. 285–301). The cosine coefficients repeat that calculation over $[0,\pi]$:

$$
a_0=\frac2\pi\int_0^\pi x\,dx=\pi,\qquad a_n=\frac2\pi\int_0^\pi x\cos nx\,dx=\frac2\pi\left[\frac{\cos nx}{n^2}\right]_0^\pi=\frac{2}{\pi n^2}\big((-1)^n-1\big),
$$

so $x\sim\frac\pi2+\sum_n\frac{2}{\pi n^2}((-1)^n-1)\cos nx$ on $(0,\pi)$. The lecturer admitted this is hardly faster than the brute-force version; the real saving is not having to write the $b_n$ at all (ll. 333–341).

**Odd extension.** Mirroring about both axes gives $x$ on $(-\pi,\pi)$, so the periodic odd extension is FS1's sawtooth, and

$$
x\sim\sum_{n=1}^\infty\frac{2(-1)^{n+1}}{n}\sin nx\qquad(0<x<\pi).
$$

Here the symmetry saves the most, since $a_0$ and $a_n$ need no work at all (ll. 352–361).

![[m2048_fs_half_range_extensions.png|720]]

The three series agree with $x$ on $(0,\pi)$ and differ outside it. They also converge at different rates: the even extension is continuous and its coefficients fall as $1/n^2$, while the other two jump and fall only as $1/n$, with Gibbs overshoots at the jumps.

> [!check] SymPy
> Integrating directly over $[0,\pi]$: periodic extension $a_0=\pi$, $a_n=0$, $b_n=-1/n$; cosine series $a_n=2((-1)^n-1)/(\pi n^2)$; sine series $b_n=-2(-1)^n/n$.

## 4. When does a Fourier series converge? (L6)

The lecture stated the result without proof, as theory "you only need to know the result and the implications" (ll. 362–398). The **Dirichlet conditions** are that $f$ is bounded, periodic with some period, and has a finite number of maxima, minima and discontinuities in each period. A function like $1/x$ or $\ln x$ with a singularity inside the domain has no Fourier series, though the same function on a domain that excludes the singularity is fine (ll. 368–374).

If the conditions hold, the series converges at every point: to $f(x)$ where $f$ is continuous, and to the average of the left and right limits where it jumps,

$$
\frac12\big[f(x^-)+f(x^+)\big].
$$

Jumps can be hidden. The function $x$ is continuous on $(-\pi,\pi)$, but its periodic extension jumps from $\pi$ to $-\pi$ at every odd multiple of $\pi$. One jump per period is still a finite number, so the sawtooth series converges, and at $x=\pm\pi$ it gives $\frac12(\pi+(-\pi))=0$, which is visible directly because every $\sin n\pi=0$ (ll. 380–393). The lecturer added that this is why a step function is sometimes said to take the value $\frac12$ at its jump: the function itself needn't be defined there, but its Fourier series is, and it takes the average (ll. 394–398).

## Transcript slips

> [!warning] Lecture 6
> | Where | Transcript says | Correct |
> |---|---|---|
> | ll. 197–202 | Dirichlet conditions match even extensions; Neumann (reflection) conditions match odd ones | Dirichlet (zero value) means odd extension and sine series; Neumann (zero slope) means even extension and cosine series (see the warning in §3) |
> | ll. 58, 301 | "the tenth function" | the tent function |
> | l. 98 | "that should have been up to L" | the limits $0$ to $L$ after reversing |
> | l. 255 | "cos 2mx on 2m plus sine 2mx on 2m squared" | $-\frac{x\cos2mx}{2m}+\frac{\sin2mx}{(2m)^2}$; the $x$ and the minus sign were dropped in speech, and the result $b_m=-1/m$ is right |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]] · Next: [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]
- Sine and cosine series as eigenfunction expansions in the PDE block: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]], [[MATH2048 PDE3 - The Heat Equation]]
- Concepts: [[Half-Range Expansions]] · [[Fourier's Theorem]] · [[Fourier Series]]

## Sources

- Lecture 6 recording, 9 Oct 2024 (Ian Hawke): `MATH2048 Lecture 6.txt`
- Slides `Lecture6_FourierSeries3.pdf`; lecture notes §2.2–2.4
- Problem Sheet 3; worked solutions in [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

## Self-study tasks

Lecture 6 left the two remaining product rules (even times even, odd times odd) as an exercise (l. 142) and pointed to the problem sheets.

### Core

- [ ] Lecturer-set (l. 142): prove that the product of two even functions, and of two odd functions, is even. → [[#Products]]
- [ ] Prove that an odd function integrates to zero over $[-L,L]$, with the substitution $z=-x$. → [[#The integral of an even or odd function over a symmetric interval]]
- [ ] PS3 Q2: the cosine series of $f=x$ on $[0,1]$, its sketch on $[-3,3]$, and $\sum_{n\geq0}\frac1{(2n+1)^2}=\frac{\pi^2}8$. Answer: $x\sim\frac12-\frac4{\pi^2}\sum_{n\ \mathrm{odd}}\frac{\cos n\pi x}{n^2}$. → [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

### Further practice

- [ ] PS3 Q3: the half-wave rectified sine, $0$ on $(-\pi,0)$ and $\sin t$ on $(0,\pi)$; show $f=\frac1\pi+\frac12\sin t-\frac2\pi\sum\frac{\cos2nt}{4n^2-1}$. → [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]
- [ ] Find the value of the periodic-extension series of $x$ (period $\pi$) at $x=0$ and explain it from the jump (suggested, not lecturer-set). → [[#4. When does a Fourier series converge? (L6)]]
- [ ] Write down, without integrating, which coefficients vanish for $x^3$, $x\cos x$ and $e^{|x|}$ on $(-\pi,\pi)$ (suggested, not lecturer-set). → [[#What this does to the coefficients]]
