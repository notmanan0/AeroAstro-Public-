---
title: "MATH1054 M07 - Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 7
tags:
  - math1054
  - functions
  - inverse-functions
  - hyperbolic-functions
aliases: ["MATH1054 Module 7", "Functions"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M08 - Differentiation II]]"]
key_concepts: ["[[Inverse Functions]]", "[[Even, Odd and Periodic Functions]]", "[[Inverse Trigonometric Functions]]", "[[Hyperbolic Functions]]"]
tutorial_sheets: ["[[MATH1054 M07 Solutions - Functions]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 7)", "02 - Sources/Modern Engineering Mathematics.pdf (§2.2, §2.6–2.7, §8.3.9–8.3.12)"]
---

# MATH1054 M07 - Functions

> [!abstract] Summary
> A function is a rule together with a domain. This module covers:
> - the vocabulary: domain, codomain, range, inverse, composite, even, odd, periodic;
> - two families built on that vocabulary: the **inverse trigonometric** functions (made invertible by restricting the domain) and the **exponential/log/hyperbolic** family;
> - the derivatives of all of these.
>
> Hyperbolic functions reappear everywhere later: catenaries, $\cosh/\sinh$ solutions of $y''=k^2y$, and $\int\frac{\mathrm dx}{\sqrt{x^2\pm a^2}}$.

## Key Concepts
- [[Inverse Functions]] · [[Even, Odd and Periodic Functions]] · [[Inverse Trigonometric Functions]] · [[Hyperbolic Functions]]

---

## 1. Vocabulary (James §2.2)
| Term | Meaning | Example |
|---|---|---|
| Domain | the allowed inputs | $\sqrt{(x+4)(3-x)}$: $[-4,3]$ |
| Codomain | the declared output set | usually $\mathbb R$ |
| Range (image set) | the outputs actually attained | $3x^2+1$: $[1,\infty)$ |
| Composite | $f(g(x))$: apply $g$ first | $f\circ g\neq g\circ f$ in general |
| Inverse $f^{-1}$ | undoes $f$; exists iff $f$ is **one-to-one** | $x^2$ needs $x\ge0$ |

**Finding an inverse**:
1. Write $y=f(x)$.
2. Solve for $x$ in terms of $y$.
3. Swap the letters.
4. Its domain is the range of $f$.

Graphically, $f^{-1}$ is the reflection of $f$ in $y=x$. A function is one-to-one iff every horizontal line meets its graph at most once.

![[m1054_inverse_reflections.png|760]]

## 2. Symmetry and periodicity (James §2.2.6)
- **Even**: $f(-x)=f(x)$, mirror symmetry in the $y$-axis. Examples: $x^2$, $\cos x$, $\cosh x$.
- **Odd**: $f(-x)=-f(x)$, $180°$ rotational symmetry about O, with $f(0)=0$ if defined. Examples: $x^3$, $\sin x$, $\sinh x$, $\tanh x$.
- **Periodic, period $T$**: $f(x+T)=f(x)$.
- A function given on $[0,L]$ can be extended to be even or odd with period $2L$ (Ex 2.12). This is the half-range idea used in Fourier series.

![[m1054_periodic_extensions.png|760]]

## 3. Inverse trigonometric functions (James §2.6.7)
The trig functions are periodic, so they are not one-to-one. Restrict each one to a principal branch first:

| Function | Restricted domain of the trig function | $f^{-1}$ domain | $f^{-1}$ range | Derivative |
|---|---|---|---|---|
| $\sin^{-1}x$ | $[-\frac\pi2,\frac\pi2]$ | $[-1,1]$ | $[-\frac\pi2,\frac\pi2]$ | $\dfrac{1}{\sqrt{1-x^2}}$ |
| $\cos^{-1}x$ | $[0,\pi]$ | $[-1,1]$ | $[0,\pi]$ | $-\dfrac{1}{\sqrt{1-x^2}}$ |
| $\tan^{-1}x$ | $(-\frac\pi2,\frac\pi2)$ | $\mathbb R$ | $(-\frac\pi2,\frac\pi2)$ | $\dfrac1{1+x^2}$ |

Useful identity: $\sin^{-1}x+\cos^{-1}x=\frac\pi2$.

> [!warning] $\sin^{-1}(\sin x)\neq x$ in general
> It equals $x$ only on $[-\frac\pi2,\frac\pi2]$. Elsewhere it is a **triangular wave**. The same goes for $\cos^{-1}(\cos x)=|x|$ on $[-\pi,\pi]$, repeated with period $2\pi$.

![[m1054_inverse_trig_compositions.png|800]]

## 4. Exponentials and logarithms (James §2.7.1–2.7.3)

$$
\log_a(xy)=\log_ax+\log_ay,\quad\log_a\frac xy=\log_ax-\log_ay,\quad\log_ax^n=n\log_ax,\quad\log_ax=\frac{\log_bx}{\log_ba}
$$

$e^{\ln x}=x$ for $x>0$, and $\ln e^x=x$. So $e^{2\ln x}=x^2$, and $\exp\{\tfrac12\ln u\}=\sqrt u$.

## 5. Hyperbolic functions (James §2.7.4–2.7.5)

$$
\cosh x=\frac{e^x+e^{-x}}2,\qquad\sinh x=\frac{e^x-e^{-x}}2,\qquad\tanh x=\frac{\sinh x}{\cosh x}
$$

- $\cosh^2x-\sinh^2x=1$, which follows by multiplying out the definitions.
- $\cosh x\pm\sinh x=e^{\pm x}$.
- **Osborn's rule**: a trig identity becomes a hyperbolic one if you swap each function for its hyperbolic version **and** flip the sign of every product of two sines. For example, $\cos^2+\sin^2=1$ becomes $\cosh^2-\sinh^2=1$.
- To **solve** $a\cosh x+b\sinh x=c$, substitute the exponentials and solve the quadratic in $e^x$ (Ex 2.59).

**Inverse hyperbolics in log form.** These are derived by solving a quadratic in $e^y$ (Specimen Q5):

$$
\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big),\quad\cosh^{-1}x=\ln\big(x+\sqrt{x^2-1}\big)\ (x\ge1),\quad\tanh^{-1}x=\tfrac12\ln\frac{1+x}{1-x}\ (|x|<1)
$$

## 6. Derivatives (James §8.3.9–8.3.12)
| $f$ | $f'$ | $f$ | $f'$ |
|---|---|---|---|
| $\sinh x$ | $\cosh x$ | $\sinh^{-1}x$ | $\dfrac1{\sqrt{1+x^2}}$ |
| $\cosh x$ | $\sinh x$ (no minus sign) | $\cosh^{-1}x$ | $\dfrac1{\sqrt{x^2-1}}$ |
| $\tanh x$ | $\mathrm{sech}^2x$ | $\tanh^{-1}x$ | $\dfrac1{1-x^2}$ |

**Derivation trick**: to differentiate an inverse function, write $x=f(y)$, differentiate implicitly, then use an identity. For $y=\sin^{-1}x$: $x=\sin y$, so $1=\cos y\,y'$, and $y'=\frac1{\cos y}=\frac1{\sqrt{1-x^2}}$.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M07 Solutions - Functions]]
- Prev: [[MATH1054 M03 - Differentiation I]] · Next: [[MATH1054 M08 - Differentiation II]]
- Complex extension: $\cosh\mathrm jx=\cos x$ and $\sinh\mathrm jx=\mathrm j\sin x$ ([[MATH1054 M22 - Complex Numbers II]])

## Sources
- MATH1054 Module Booklet, Module 7; James §2.2, §2.6–2.7, §8.3.9–8.3.12
