---
title: "Fourier Transform"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["FT", "Inverse Fourier transform", "Fourier integral", "Response function"]
tags: [math2048, concept, transforms]
status: complete
parent_lectures: ["[[MATH2048 TR1 - Fourier Transforms]]"]
related_concepts: ["[[Complex Fourier Series]]", "[[Laplace Transform]]", "[[Frequency Response Function]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture9_FourierTransforms1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture10_FourierTransforms2.pdf"]
---

# Fourier Transform

## Definition

> [!note] Definition (MATH2048 symmetric convention)
> $$F(\omega)=\frac1{\sqrt{2\pi}}\int_{-\infty}^\infty f(t)e^{-j\omega t}dt,\qquad f(t)=\frac1{\sqrt{2\pi}}\int_{-\infty}^\infty F(\omega)e^{j\omega t}d\omega$$

## Explanation
- It is the $T\to\infty$ limit of the [[Complex Fourier Series]]: the discrete coefficients $c_n$ become a continuous spectrum $F(\omega)$.
- **Exists if** $f$ is bounded, $\int|f|<\infty$, and $f$ has finitely many extrema and jumps on any finite interval.

**Properties** (each one is proved in [[MATH2048 TR1 - Fourier Transforms|TR1]]):

| Property | Result |
|---|---|
| Linearity | $\mathcal F[\alpha f+\beta g]=\alpha F+\beta G$ |
| Derivative | $\mathcal F[f^{(n)}]=(j\omega)^nF$ (needs $f\to0$ at $\pm\infty$) |
| Time shift | $\mathcal F[f(t-t_0)]=e^{-j\omega t_0}F$ |
| Frequency shift | $\mathcal F[e^{j\omega_0t}f]=F(\omega-\omega_0)$ |
| Symmetry | real even $f$ gives real even $F$; real odd $f$ gives imaginary odd $F$ |

**Solving ODEs**: an ODE $L_y[y]=L_u[u]$ becomes $Y=G(\omega)U$. The **response function** $|G(\omega)|$ is the gain at each frequency. For $\ddot y+\gamma\dot y+\omega_0^2y=u$, $G=1/(\omega_0^2-\omega^2+j\gamma\omega)$, which peaks at $\omega^2=\omega_0^2-\gamma^2/2$.

## Examples
| $f(t)$ | $F(\omega)$ |
|---|---|
| $1$ for $\lvert t\rvert<1$, else $0$ | $\sqrt{2/\pi}\,\sin\omega/\omega$ |
| $\sin t$ for $\lvert t\rvert<\pi$, else $0$ | $j\sqrt{2/\pi}\,\sin\omega\pi/(\omega^2-1)$ |
| $\cos t$ for $\lvert t\rvert<\pi$, else $0$ | $\sqrt{2/\pi}\,\omega\sin\omega\pi/(1-\omega^2)$ |
| $e^{-\omega_0\lvert t\rvert}$ | $\sqrt{2/\pi}\,\omega_0/(\omega_0^2+\omega^2)$ |
| $\sin at$ for $\lvert t\rvert\leq\pi/a$, else $0$ | $-j\sqrt{2/\pi}\,a\sin(\omega\pi/a)/(a^2-\omega^2)$ |

## Related
- [[Complex Fourier Series]] · [[Laplace Transform]] · [[Resonance]] · SESA2027 [[Frequency Response Function]]

## Sources
- Lectures 9–10; PS4
