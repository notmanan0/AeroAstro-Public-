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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture9_FourierTransforms1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture10_FourierTransforms2.pdf", "02 - Sources/Lectures/MATH2048 Lecture 9.txt", "02 - Sources/Lectures/MATH2048 Lecture 10.txt"]
---

# Fourier Transform

The **Fourier transform** represents a non-periodic function as a continuous spread of frequencies. MATH2048 uses the symmetric convention

$$
F(\omega)=\frac1{\sqrt{2\pi}}\int_{-\infty}^\infty f(t)e^{-j\omega t}\,dt,\qquad f(t)=\frac1{\sqrt{2\pi}}\int_{-\infty}^\infty F(\omega)e^{j\omega t}\,d\omega .
$$

It is the [[Complex Fourier Series]] with the period sent to infinity. As the period grows, the spacing between harmonics shrinks, the sum over $n$ becomes an integral over $\omega$, and the coefficients $c_n$ become a continuous spectrum $F(\omega)$. The two factors of $\frac1{\sqrt{2\pi}}$ split the $\frac1{2\pi}$ that the limit produces; other books put it all on one side, so check the convention before using someone else's table. The transform exists when $f$ is bounded, absolutely integrable and has finitely many extrema and jumps on any finite interval, which rules out constants, polynomials and growing exponentials.

Its use for ODEs comes from the derivative rule $\mathcal F[f^{(n)}]=(j\omega)^nF$, valid when $f$ and its derivatives vanish at $\pm\infty$. An ODE $L_y[y]=L_u[u]$ with constant coefficients becomes $Y(\omega)=G(\omega)U(\omega)$, and $|G|$, the response function, is the gain at each input frequency. For the damped oscillator $\ddot y+\gamma\dot y+\omega_0^2y=u$, $G=1/(\omega_0^2-\omega^2+j\gamma\omega)$, whose magnitude peaks at $\omega^2=\omega_0^2-\gamma^2/2$ and has no peak once $\gamma^2\geq2\omega_0^2$. This is the same object that SESA2027 calls the frequency response.

A real even $f$ gives a real even $F$, and a real odd $f$ gives an imaginary odd $F$, the same pattern as the complex series. Shifting in time multiplies by a phase, $\mathcal F[f(t-t_0)]=e^{-j\omega t_0}F$, and multiplying by $e^{j\omega_0t}$ shifts the spectrum, $\mathcal F[e^{j\omega_0t}f]=F(\omega-\omega_0)$.

| $f(t)$ | $F(\omega)$ |
|---|---|
| $1$ for $\lvert t\rvert<1$, else $0$ | $\sqrt{2/\pi}\,\sin\omega/\omega$ |
| $\sin t$ for $\lvert t\rvert<\pi$, else $0$ | $j\sqrt{2/\pi}\,\sin\omega\pi/(\omega^2-1)$ |
| $\cos t$ for $\lvert t\rvert<\pi$, else $0$ | $\sqrt{2/\pi}\,\omega\sin\omega\pi/(1-\omega^2)$ |
| $e^{-\omega_0\lvert t\rvert}$ | $\sqrt{2/\pi}\,\omega_0/(\omega_0^2+\omega^2)$ |

## Related

- Derivations: [[MATH2048 TR1 - Fourier Transforms]]
- [[Complex Fourier Series]] · [[Laplace Transform Properties and Proofs]] · [[Resonance]] · SESA2027 [[Frequency Response Function]]
