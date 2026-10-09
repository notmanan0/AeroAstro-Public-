---
title: "MATH2048 TR1 - Fourier Transforms"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 3: Fourier and Laplace Transforms"
order: 7
tags:
  - math2048
  - fourier-transform
  - response-function
aliases: ["MATH2048 Lecture 9", "MATH2048 Lecture 10", "Fourier integral"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
next_topics: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]"]
key_concepts: ["[[Fourier Transform]]", "[[Resonance]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture9_FourierTransforms1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture10_FourierTransforms2.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Appendix-Fourier Transform_Additional Slides.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 3)"]
---

# MATH2048 TR1 - Fourier Transforms

> [!abstract] Summary
> Let the period of a complex Fourier series go to infinity. The discrete frequencies $n\pi/\ell$ merge into a continuum $\omega$, and the sum becomes an integral. The result is the **Fourier transform** (MATH2048's symmetric convention):
>
> $$F(\omega)=\mathcal F[f]=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{-j\omega t}dt,\qquad f(t)=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}F(\omega)e^{j\omega t}d\omega .$$
>
> Its key property is that **differentiation becomes multiplication by $j\omega$**. So a linear ODE becomes algebra, $Y(\omega)=G(\omega)U(\omega)$, and $|G(\omega)|$ is the system's frequency response.

## Key Concepts
- [[Fourier Transform]] · [[Complex Fourier Series]] · [[Resonance]] · SESA2027: [[Frequency Response Function]]

---

## 1. From Fourier series to Fourier transform (L9)
Take the complex series for period $T$: $f(t)=\sum_nc_ne^{j2\pi nt/T}$, with $c_n=\frac1T\int_{-T/2}^{T/2}fe^{-j2\pi nt/T}dt$.

1. Define $k_n=\frac{2\pi n}{T}$. Consecutive values are separated by $\Delta k=\frac{2\pi}T$, so $\frac1T=\frac{\Delta k}{2\pi}$.
2. Define $F(k_n)=\frac{T}{\sqrt{2\pi}}c_n=\frac{1}{\sqrt{2\pi}}\int_{-T/2}^{T/2}f(t)e^{-jk_nt}dt$.
3. Then $f(t)=\sum_nc_ne^{jk_nt}=\frac{1}{\sqrt{2\pi}}\sum_nF(k_n)e^{jk_nt}\,\Delta k$.
4. As $T\to\infty$, $\Delta k\to dk$ and the Riemann sum becomes an integral, which gives the pair above (with $k$ renamed $\omega$).

> [!warning] Conventions differ between modules
> MATH2048 uses $\frac1{\sqrt{2\pi}}$ on **both** transforms (the "unitary" form). MATH2047 and many textbooks put $1$ on $\mathcal F$ and $\frac1{2\pi}$ on $\mathcal F^{-1}$. Only the product of the two factors, $\frac1{2\pi}$, is fixed.
>
> Use the MATH2048 form in the exam, and check the factor in any formula you look up.

**Existence** (sufficient conditions): $f$ is bounded, $\int_{-\infty}^\infty|f|\,dt<\infty$, and $f$ has finitely many extrema and discontinuities in any finite interval. At a jump, the inverse transform returns the average $\frac12[f(t^-)+f(t^+)]$, just as for a Fourier series.

## 2. Worked examples
### Box: $f=1$ for $|t|<1$, else $0$ (L9)

$$
F(\omega)=\frac1{\sqrt{2\pi}}\int_{-1}^{1}e^{-j\omega t}dt=\frac1{\sqrt{2\pi}}\Big[\frac{e^{-j\omega t}}{-j\omega}\Big]_{-1}^{1}=\frac1{\sqrt{2\pi}}\cdot\frac{e^{j\omega}-e^{-j\omega}}{j\omega}=\sqrt{\frac2\pi}\,\frac{\sin\omega}{\omega}.
$$

The last step uses $e^{j\omega}-e^{-j\omega}=2j\sin\omega$. At $\omega=0$ the limit is $\sqrt{2/\pi}$.

### $f=\sin t$ for $|t|<\pi$, else $0$ (L9)
Write $\sin t=\frac{e^{jt}-e^{-jt}}{2j}$. Then

$$
F=\frac1{2j\sqrt{2\pi}}\int_{-\pi}^{\pi}\big[e^{j(1-\omega)t}-e^{-j(1+\omega)t}\big]dt=\frac1{2j\sqrt{2\pi}}\Big[\frac{2\sin(1-\omega)\pi}{1-\omega}-\frac{2\sin(1+\omega)\pi}{1+\omega}\Big].
$$

Use $\sin(\pi\mp\omega\pi)=\pm\sin\omega\pi$, i.e. $\sin(1-\omega)\pi=\sin\omega\pi$ and $\sin(1+\omega)\pi=-\sin\omega\pi$:

$$
F(\omega)=\frac{\sin\omega\pi}{j\sqrt{2\pi}}\Big[\frac1{1-\omega}+\frac1{1+\omega}\Big]=\frac{2\sin\omega\pi}{j\sqrt{2\pi}(1-\omega^2)}=j\sqrt{\frac2\pi}\,\frac{\sin\omega\pi}{\omega^2-1}.
$$

$F$ is purely imaginary and odd, because $f$ is real and odd.

### Symmetry rules
| $f$ real and... | $F(\omega)$ |
|---|---|
| even | real and even: $F=\sqrt{\frac2\pi}\int_0^\infty f\cos\omega t\,dt$ |
| odd | imaginary and odd: $F=-j\sqrt{\frac2\pi}\int_0^\infty f\sin\omega t\,dt$ |

![[m2048_tr_fourier_pairs.png|700]]

**Uncertainty trade-off**: a narrow pulse in $t$ has a wide spectrum in $\omega$, and vice versa. Compare $\omega_0=3$ with $\omega_0=0.5$ in the lower panels.

## 3. Properties (L10, Notes §3.3). Prove these, they are examinable
### Derivative
Assume $f\to0$ as $|t|\to\infty$. Integrate by parts with $u=e^{-j\omega t}$ and $dv=f'dt$:

$$
\mathcal F[f']=\frac1{\sqrt{2\pi}}\int_{-\infty}^\infty f'e^{-j\omega t}dt=\frac1{\sqrt{2\pi}}\Big[fe^{-j\omega t}\Big]_{-\infty}^{\infty}+\frac{j\omega}{\sqrt{2\pi}}\int_{-\infty}^\infty fe^{-j\omega t}dt=j\omega F(\omega).
$$

The boundary term vanishes because $f\to0$. Applying this $n$ times gives

$$
\mathcal F\big[f^{(n)}\big]=(j\omega)^nF(\omega).
$$

### First shift (time shift)
Substitute $\tau=t-t_0$:

$$
\mathcal F[f(t-t_0)]=\frac1{\sqrt{2\pi}}\int f(\tau)e^{-j\omega(\tau+t_0)}d\tau=e^{-j\omega t_0}F(\omega).
$$

A delay only changes the phase.

### Second shift (frequency shift)

$$
\mathcal F[e^{j\omega_0t}f(t)]=\frac1{\sqrt{2\pi}}\int fe^{-j(\omega-\omega_0)t}dt=F(\omega-\omega_0).
$$

This is the basis of modulation.

### Other properties
- **Linearity**: $\mathcal F[\alpha f+\beta g]=\alpha F+\beta G$.
- *(Not examinable)*: convolution, $\mathcal F[f*g]=\sqrt{2\pi}FG$; Parseval, $\int|f|^2dt=\int|F|^2d\omega$.

> [!example] L10: derivative trick
> $g(t)=\cos t$ on $|t|<\pi$ is $f'$ for $f=\sin t$ on $|t|<\pi$. Since $f(\pm\pi)=0$, $f$ is continuous everywhere, so the derivative rule applies:
>
> $$\mathcal F[g]=j\omega\cdot j\sqrt{\tfrac2\pi}\frac{\sin\omega\pi}{\omega^2-1}=-\sqrt{\tfrac2\pi}\frac{\omega\sin\omega\pi}{\omega^2-1}=\sqrt{\tfrac2\pi}\frac{\omega\sin\omega\pi}{1-\omega^2}.$$
>
> SymPy agrees ✔.

## 4. Response function and resonance (L10, Notes §3.4)
For a linear ODE $L_y[y]=L_u[u]$, transform both sides using $\frac{d}{dt}\to j\omega$:

$$
Y(\omega)=G(\omega)U(\omega),\qquad y(t)=\frac1{\sqrt{2\pi}}\int G(\omega)U(\omega)e^{j\omega t}d\omega .
$$

The output amplitude at frequency $\omega$ is $|G(\omega)|$ times the input amplitude.

**Damped oscillator** $\ddot y+\gamma\dot y+\omega_0^2y=u$. Transforming gives $\big[(j\omega)^2+\gamma j\omega+\omega_0^2\big]Y=U$, so

$$
G(\omega)=\frac{1}{\omega_0^2-\omega^2+j\gamma\omega},\qquad |G|^2=\frac1{(\omega_0^2-\omega^2)^2+\gamma^2\omega^2}.
$$

Maximise $|G|^2$ by minimising the denominator $D(v)=(\omega_0^2-v)^2+\gamma^2v$ with $v=\omega^2$:

$$
D'(v)=-2(\omega_0^2-v)+\gamma^2=0\ \Longrightarrow\ \omega_{\max}^2=\omega_0^2-\tfrac12\gamma^2 .
$$

For small damping, $\omega_{\max}\approx\omega_0$ and the peak $|G|_{\max}\approx\frac1{\gamma\omega_0}$ becomes huge. That is resonance.

> [!example] Notes eq. (3.30): $\ddot y+3\dot y+7y=3\dot u+2u$
> $G(\omega)=\dfrac{2+3j\omega}{7-\omega^2+3j\omega}$, so $|G|^2=\dfrac{4+9\omega^2}{(7-\omega^2)^2+9\omega^2}$.
> Setting $\frac{d}{d(\omega^2)}|G|^2=0$ gives $9v^2+8v-461=0$, so $v=\frac{-4+7\sqrt{85}}{9}$ and
>
> $$\omega_{\max}=\tfrac13\sqrt{-4+7\sqrt{85}}\approx2.594 .$$
>
> Numerically the peak is at $2.5935$ ✔. The system is a band-pass filter.

![[m2048_tr_response_function.png|680]]

## 5. Bonus: FT solves PDEs too (Appendix)
For Laplace's equation on the strip $-\infty<x<\infty$, $0<y<1$, transform in $x$: $\partial_x^2\to-k^2$. The PDE becomes the ODE $\hat u_{yy}-k^2\hat u=0$. With $\hat u(k,0)=0$ and $\hat u(k,1)=\hat f(k)$,

$$
\hat u(k,y)=\hat f(k)\frac{\sinh ky}{\sinh k},\qquad u=\mathcal F^{-1}[\hat u].
$$

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]] · Next: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]
- Practice: [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]] (PS4 FT Q1–2)

## Sources
- Lectures 9–10; FT Appendix (Gan Khong Wui); Lecture Notes Ch. 3. All transforms verified in SymPy. The response peak was checked numerically.
