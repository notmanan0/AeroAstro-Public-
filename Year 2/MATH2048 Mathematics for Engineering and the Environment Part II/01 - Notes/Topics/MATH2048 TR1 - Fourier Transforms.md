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
aliases: ["MATH2048 Lecture 9", "MATH2048 Lecture 10", "Fourier transform"]
date: 2026-10-30
status: lectured
coverage: "Lecture 9 (16 Oct 2024): why integral transforms, the Fourier transform as the limit of the complex Fourier series, normalisation conventions, existence, and the box and sine-pulse examples. Lecture 10 (21 Oct 2024): the transform of a derivative, linearity, solving ODEs, and the response function of a damped oscillator with its resonance peak. Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
next_topics: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]"]
key_concepts: ["[[Fourier Transform]]", "[[Complex Fourier Series]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 9.txt", "02 - Sources/Lectures/MATH2048 Lecture 10.txt", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture9_FourierTransforms1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture10_FourierTransforms2.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 3)"]
---

# MATH2048 TR1 - Fourier Transforms

> [!abstract] Summary
> The Fourier transform $F(\omega)=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{-j\omega t}\,dt$ is the limit of the complex Fourier series as the period goes to infinity: the discrete frequencies $n$ become a continuous $\omega$ and the sum becomes the inverse transform $f(t)=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}F(\omega)e^{j\omega t}\,d\omega$. It exists when $\int|f|\,dt$ is finite, it is linear, and it turns a derivative into multiplication by $j\omega$, so a linear ODE becomes algebra and its solution is the response function $G(\omega)$ times the transformed input. For a damped oscillator the response peaks at $\omega^2=\omega_0^2-\gamma^2/2$.

> [!summary]- Exam use: quick path
> - **Use it when:** a signal on the whole real line has to be described by frequency, or the frequency response of a linear system is asked for. Fourier transforms are not examined on their own; they appear in the coursework and as the route to Laplace transforms.
> - **Assumptions:** $\int_{-\infty}^\infty|f|\,dt<\infty$ (in practice $f$ is zero outside a window or decays); the course normalisation $\frac1{\sqrt{2\pi}}$ on both transforms; $f\to0$ as $t\to\pm\infty$ for the derivative rule.
> - **Method:** 1. Restrict the integral to where $f\neq0$. 2. Write sines and cosines as exponentials and combine with $e^{-j\omega t}$. 3. Integrate the exponentials and evaluate at the limits. 4. Tidy to $\sin$ or $\cos$ if possible. 5. Check separately any $\omega$ where the general answer divides by zero.
> - **Common mistakes:** mixing normalisation conventions between sources (the product of the two factors must be $\frac1{2\pi}$); forgetting the $\omega=0$ check when the answer has $\omega$ in a denominator.
> - **Practise:** [[#The box function]] · [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms|PS4 (Fourier transforms) Q1]]

The lecture gave three reasons for moving from Fourier series to integral transforms (L9, ll. 7–43). A Fourier series only describes periodic functions on a bounded domain, so letting the period grow without limit should capture every function. A series only contains the discrete frequencies that fit the period, while real signals contain a continuous range, and a signal that looks complicated in time can be simple in frequency. And transforming a differential equation replaces derivatives with algebra, turning an ODE into an algebraic equation and a PDE into an ODE. The catch is the transform there and back, which is only worth it for certain classes of problem, but for those it is often the only practical method.

The transform is built as a limit of the Fourier series. A Fourier series has frequencies spaced $2\pi/T$ apart; as the period $T$ grows, they crowd together, the sum over them looks more and more like the Riemann sum of an integral, and in the limit it becomes one. The coefficient formula, which was already an integral over one period, becomes an integral over all time.

What makes the transform useful for ODEs is that differentiating $e^{j\omega t}$ just multiplies it by $j\omega$. Writing a function as a superposition of $e^{j\omega t}$ therefore turns every derivative into a factor $j\omega$, so $\ddot y+\gamma\dot y+\omega_0^2y=u$ becomes $(-\omega^2+j\gamma\omega+\omega_0^2)Y=U$. The ratio $Y/U$, the response function, says how much the system amplifies each input frequency, and its peak is resonance.

---

## 1. From Fourier series to Fourier transform (L9)

Start from the complex Fourier series of FS3, with two changes of notation: the independent variable is time $t$, and the period is the whole period $T=2L$ (ll. 98–116):

$$
f(t)=\sum_{n=-\infty}^{\infty}c_ne^{j2\pi nt/T},\qquad c_n=\frac1T\int_{-T/2}^{T/2}f(t)e^{-j2\pi nt/T}\,dt .
$$

Letting $T\to\infty$ directly would blow up, because of the $\frac1T$, so first count with a real-valued label (ll. 122–135):

$$
k=\frac{2\pi n}{T},\qquad\Delta k=\frac{2\pi}{T},\qquad\text{so}\qquad\frac{T\Delta k}{2\pi}=1 .
$$

Multiply every term of the series by that factor of 1 (ll. 151–157):

$$
f(t)=\sum_nc_ne^{jkt}\,\frac{T\Delta k}{2\pi}.
$$

Group the terms so that each looks like "a function of $k$ times $\Delta k$" (ll. 158–184):

$$
f(t)=\frac1{\sqrt{2\pi}}\sum_k\left[\frac{Tc_k}{\sqrt{2\pi}}\right]e^{jkt}\,\Delta k .
$$

This is a Riemann sum, the definition of an integral as a sum of strips of width $\Delta k$ (ll. 141–149). As $T\to\infty$, $\Delta k\to0$ and the sum becomes

$$
f(t)=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}F(k)e^{jkt}\,dk,\qquad F(k)=\lim_{T\to\infty}\frac{Tc_k}{\sqrt{2\pi}} .
$$

From the coefficient formula, $Tc_k=\int_{-T/2}^{T/2}f(t)e^{-jkt}\,dt$, which tends to the integral over all $t$ (ll. 192–211). Renaming $k$ as $\omega$, to stress that it is now a continuous frequency (ll. 212–223), gives the transform pair:

$$
F(\omega)=\mathcal F[f(t)]=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{-j\omega t}\,dt,\qquad f(t)=\mathcal F^{-1}[F(\omega)]=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}F(\omega)e^{j\omega t}\,d\omega .
$$

The notation is a capital letter for the transform, $G(\omega)$ for $g(t)$, or $\mathcal F[g]$ (ll. 225–233).

### Normalisation conventions

Splitting the factor $\frac1{2\pi}$ as $\frac1{\sqrt{2\pi}}$ on each side makes the pair symmetric, and this course uses it throughout. Other sources put $1$ on the forward transform and $\frac1{2\pi}$ on the inverse, or move the $2\pi$ into the exponent; numerical libraries such as FFTPACK and FFTW, and sites such as Wolfram MathWorld, disagree with each other. The only fixed requirement is that the two factors multiply to $\frac1{2\pi}$, so check the convention of any tool or reference before using its numbers (ll. 235–255).

### When does it exist?

The Dirichlet conditions still apply (bounded, finitely many extrema and jumps), but on an infinite domain one more matters most: $\int_{-\infty}^\infty|f(t)|\,dt$ must be finite (ll. 255–283). The kernel $e^{-j\omega t}$ has magnitude 1 everywhere, oscillating like $\cos\omega t$ without decaying, so it does nothing to help convergence; $f$ itself has to fall off. A constant, $f=1$, has no Fourier transform for this reason. In signal analysis, functions are made transformable by windowing, multiplying by something that vanishes outside a finite interval (ll. 277–283).

## 2. Examples (L9)

### The box function

Take $f(t)=1$ for $|t|<1$ and $0$ otherwise (ll. 283–353). Restrict the integral to where $f\neq0$:

$$
F(\omega)=\frac1{\sqrt{2\pi}}\int_{-1}^{1}e^{-j\omega t}\,dt=\frac1{\sqrt{2\pi}}\Big[\frac{e^{-j\omega t}}{-j\omega}\Big]_{-1}^{1}.
$$

Swap the limits to absorb the minus sign:

$$
F(\omega)=\frac1{\sqrt{2\pi}}\cdot\frac{e^{j\omega}-e^{-j\omega}}{j\omega}=\frac1{\sqrt{2\pi}}\cdot\frac2\omega\cdot\frac{e^{j\omega}-e^{-j\omega}}{2j}=\sqrt{\frac2\pi}\,\frac{\sin\omega}{\omega}.
$$

The transform of a real function is in general complex, but this one happens to be real (ll. 320–323). The general formula divides by $\omega$, so $\omega=0$ should strictly be checked on its own (ll. 324–351): there the kernel is 1 and $F(0)=\frac1{\sqrt{2\pi}}\int_{-1}^{1}dt=\frac{2}{\sqrt{2\pi}}=\sqrt{\frac2\pi}$, which agrees with the limit $\sin\omega/\omega\to1$.

![[m2048_tr_fourier_pairs.png|760]]

The figure also shows PS4 Q1's $e^{-\omega_0|t|}$ and the general pattern: a function narrow in time is wide in frequency, and vice versa.

### One period of sine

Take $f(t)=\sin t$ for $|t|<\pi$ and $0$ otherwise (ll. 354–436). Writing the sine as exponentials makes every integral an exponential one (ll. 363–366):

$$
F(\omega)=\frac1{\sqrt{2\pi}}\int_{-\pi}^{\pi}\frac{e^{jt}-e^{-jt}}{2j}e^{-j\omega t}\,dt=\frac1{2j\sqrt{2\pi}}\int_{-\pi}^{\pi}\Big(e^{j(1-\omega)t}-e^{-j(1+\omega)t}\Big)\,dt .
$$

Integrate:

$$
=\frac1{2j\sqrt{2\pi}}\left[\frac{e^{j(1-\omega)t}}{j(1-\omega)}+\frac{e^{-j(1+\omega)t}}{j(1+\omega)}\right]_{-\pi}^{\pi}.
$$

At the limits $e^{\pm j\pi}=-1$, so each bracket reduces to $-(e^{-j\omega\pi}-e^{j\omega\pi})=2j\sin\omega\pi$:

$$
=\frac{\sin\omega\pi}{j\sqrt{2\pi}}\left(\frac1{1-\omega}+\frac1{1+\omega}\right)=\frac{\sin\omega\pi}{j\sqrt{2\pi}}\cdot\frac{2}{1-\omega^2}.
$$

Multiply top and bottom by $j$:

$$
F(\omega)=j\sqrt{\frac2\pi}\,\frac{\sin\omega\pi}{\omega^2-1}.
$$

This one is purely imaginary, which FS3's rule predicts for an odd function (ll. 428–430). The points $\omega=\pm1$ need checking separately; the limit is finite there, $F(\pm1)=\mp j\sqrt{\pi/2}$.

> [!check] SymPy
> Direct integration gives $\sqrt{2/\pi}\,\sin\omega/\omega$ for the box (with $\sqrt{2/\pi}$ at $\omega=0$) and $j\sqrt{2/\pi}\,\sin\pi\omega/(\omega^2-1)$ for the sine pulse, with the finite values $\mp j\sqrt{\pi/2}$ at $\omega=\pm1$.

## 3. Properties (L10)

### The transform of a derivative

By definition (ll. 65–94),

$$
\mathcal F\Big[\frac{df}{dt}\Big]=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}\frac{df}{dt}e^{-j\omega t}\,dt .
$$

Integrate by parts, integrating $df/dt$:

$$
=\frac1{\sqrt{2\pi}}\Big[f(t)e^{-j\omega t}\Big]_{-\infty}^{\infty}-\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)\,(-j\omega)e^{-j\omega t}\,dt .
$$

The boundary term vanishes because $f\to0$ as $t\to\pm\infty$, which is required anyway for $\int|f|\,dt$ to be finite, and $|e^{-j\omega t}|=1$ (ll. 97–134). Taking the constant $j\omega$ outside:

$$
\mathcal F\Big[\frac{df}{dt}\Big]=j\omega\,\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{-j\omega t}\,dt=j\omega F(\omega).
$$

Applying it twice gives $\mathcal F[\ddot f]=(j\omega)^2F=-\omega^2F$.

The lecture's first use (ll. 137–148) was a shortcut: $\cos t$ on $|t|<\pi$ is the derivative of the sine pulse, which is continuous because it is zero at $\pm\pi$, so

$$
\mathcal F[\cos t\ \text{on}\ |t|<\pi]=j\omega\cdot j\sqrt{\frac2\pi}\frac{\sin\omega\pi}{\omega^2-1}=-\sqrt{\frac2\pi}\,\frac{\omega\sin\omega\pi}{\omega^2-1},
$$

with no new integral.

### Linearity

Using the derivative rule on an ODE term by term needs linearity, which has to be proved for each operation rather than assumed; powers, for instance, are not linear (ll. 150–170). From the definition:

$$
\mathcal F[\alpha f+\beta g]=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}(\alpha f+\beta g)e^{-j\omega t}\,dt
$$

$$
=\frac1{\sqrt{2\pi}}\Big(\alpha\int_{-\infty}^{\infty}fe^{-j\omega t}\,dt+\beta\int_{-\infty}^{\infty}ge^{-j\omega t}\,dt\Big)
$$

$$
=\alpha F(\omega)+\beta G(\omega),
$$

using that the integral of a sum is the sum of the integrals and that constants pass through (ll. 171–183).

## 4. Solving ODEs and the response function (L10)

A system with input $u(t)$ and output $y(t)$ is modelled by a linear ODE, written with linear differential operators as $\mathcal L_y[y]=\mathcal L_u[u]$ (ll. 195–236). Transforming turns each operator into a function of $\omega$, so $Y(\omega)=G(\omega)U(\omega)$, where the **response function** $G$ is the ratio of the two. The output can then be found as $\mathcal F^{-1}[GU]$ for a particular input, or $G$ can be studied on its own to see which frequencies any input will have amplified or damped, without solving again for each new input (ll. 247–265).

For the damped oscillator,

$$
\ddot y+\gamma\dot y+\omega_0^2y=u(t),
$$

transform term by term, using linearity and the derivative rule (ll. 266–274):

$$
(j\omega)^2Y+\gamma(j\omega)Y+\omega_0^2Y=U
$$

$$
\big(\omega_0^2-\omega^2+j\gamma\omega\big)Y=U,
$$

so

$$
G(\omega)=\frac{1}{\omega_0^2-\omega^2+j\gamma\omega}.
$$

At high frequency $|G|\sim1/\omega^2\to0$, so the system damps fast inputs (ll. 299–306). To find where $|G|$ is largest, which is resonance, work with $|G|^2$, which peaks at the same place and avoids square roots (ll. 308–336):

$$
|G|^2=\frac{1}{(\omega_0^2-\omega^2)^2+\gamma^2\omega^2}.
$$

The peak is where the denominator $D(\omega)$ is smallest. Differentiate:

$$
\frac{dD}{d\omega}=2(\omega_0^2-\omega^2)(-2\omega)+2\gamma^2\omega=-4\omega\Big(\omega_0^2-\omega^2-\tfrac12\gamma^2\Big).
$$

Setting this to zero for $\omega\neq0$:

$$
\omega^2=\omega_0^2-\tfrac12\gamma^2 .
$$

For light damping the peak sits at the natural frequency, as expected; the response function shows how far damping shifts it (ll. 377–384). There is a peak only while $\gamma^2<2\omega_0^2$; beyond that $|G|$ falls steadily from $\omega=0$. A large $G$ at some frequency only matters if the input has content there: an input designed to be nearly zero near $\omega_0$ won't excite the resonance (ll. 385–396).

![[m2048_tr_response_lecture.png|720]]

> [!check] SymPy
> Solving $d|G|^{-2}/d\omega=0$ gives $\omega=0$ and $\omega=\pm\sqrt{\omega_0^2-\gamma^2/2}$.

This is the same frequency response as SESA2027's [[Frequency Response Function]], with $\gamma=2\zeta\omega_0$; there the peak is written $\omega_r=\omega_0\sqrt{1-2\zeta^2}$.

## Transcript slips

> [!warning] Lectures 9 and 10
> | Where | Transcript says | Correct |
> |---|---|---|
> | L9, l. 188 | "the integral… of f of k exponential j k t dt" | $dk$; the integration variable is the frequency |
> | L9, ll. 202–205 | writes $f$ of $k$ inside the coefficient integral, then corrects himself | $f(t)$ |
> | L9, l. 278 | "nearly all cases where the Fourier series can be computed are going to be bounded" | where the Fourier transform can be computed, the functions are windowed (zero outside a finite interval) |
> | L9, l. 322 | "the Fourier transform of the constant turns out to be a real function" | of the box function; a constant has no Fourier transform (ll. 265–266) |
> | L10, l. 229 | admits the slide's operator equation is written incorrectly | $\mathcal L_y[y]=\mathcal L_u[u]$ with $\mathcal L_y=\frac{d^2}{dt^2}+\gamma\frac{d}{dt}+\omega_0^2$ and $\mathcal L_u=1$ |
> | L10, ll. 341–375 | sign and factor slips while differentiating $\lvert G\rvert^2$, corrected on the fly | $\omega^2=\omega_0^2-\frac12\gamma^2$ |
> | L10, l. 305 | high-frequency input is damped "unless… going like omega cubed" | $G\sim1/\omega^2$, so only an input growing at least like $\omega^2$ escapes the damping |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]] · Next: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]
- SESA2027: [[Frequency Response Function]] · [[Bode Plot]]
- Concepts: [[Fourier Transform]] · [[Complex Fourier Series]]

## Sources

- Lecture 9 (16 Oct 2024) and Lecture 10 (21 Oct 2024) recordings, Ian Hawke: `MATH2048 Lecture 9.txt`, `MATH2048 Lecture 10.txt`
- Slides `Lecture9_FourierTransforms1.pdf`, `Lecture10_FourierTransforms2.pdf`; lecture notes Ch. 3
- Problem Sheet 4 (Fourier transforms); worked solutions in [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]

## Self-study tasks

Lecture 10 mentioned "some important exercises that can be done there" on response functions (ll. 397–398) without setting a specific one. Problem Sheet 4 has two Fourier-transform questions.

### Core

- [ ] Derive the transform pair from the complex Fourier series by letting $T\to\infty$. → [[#1. From Fourier series to Fourier transform (L9)]]
- [ ] PS4 (Fourier transforms) Q1: show $\mathcal F[e^{-\omega_0|t|}]=\sqrt{\frac2\pi}\,\frac{\omega_0}{\omega^2+\omega_0^2}$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] Prove $\mathcal F[\dot f]=j\omega F$, saying where $f\to0$ at $\pm\infty$ is used. → [[#The transform of a derivative]]

### Further practice

- [ ] PS4 (Fourier transforms) Q2: transform $\sin at$ on $|t|\leq\pi/a$, use the inverse transform to get its Fourier-integral representation, and deduce $\int_0^\infty\frac{\sin\omega\pi\,\sin(\omega\pi/2)}{1-\omega^2}\,d\omega=\frac\pi2$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] Find the response function of $\ddot y+3\dot y+2y=u$ and the frequency, if any, at which $|G|$ peaks (suggested, not lecturer-set). → [[#4. Solving ODEs and the response function (L10)]]
- [ ] Check the sine-pulse transform at $\omega=1$ directly from the integral (suggested, not lecturer-set). → [[#One period of sine]]
