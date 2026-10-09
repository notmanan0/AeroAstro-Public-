---
title: "MATH2048 Problem Sheets 2-4 Solutions - Fourier Series"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: tutorial
stream: "Block 2: Fourier Series"
tags:
  - math2048
  - tutorial-solutions
  - fourier-series
sheet: "PS2 (Fourier Series page), PS3 (Fourier Series), PS4 Q1–2 (Complex Fourier Series)"
theory_notes: ["[[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]]", "[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]", "[[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]"]
key_concepts: ["[[Fourier Series]]", "[[Orthogonality of Trigonometric Functions]]", "[[Half-Range Expansions]]", "[[Fourier's Theorem]]", "[[Complex Fourier Series]]"]
status: complete
sources: ["02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 2.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 3.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 4.pdf"]
---

# MATH2048 Problem Sheets 2-4 Solutions - Fourier Series

> [!abstract] Sheet Info
> Every coefficient and every sum was checked in SymPy (`integrate`, `summation`) or numerically in NumPy. The Fourier-transform half of PS4 is solved in [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]].

## Theory Links
- [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]] · [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]] · [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]

**Integrals used repeatedly** (each is one or two integrations by parts):

$$
\int x\cos kx\,dx=\frac{x\sin kx}{k}+\frac{\cos kx}{k^2},\qquad \int x\sin kx\,dx=-\frac{x\cos kx}{k}+\frac{\sin kx}{k^2},
$$

$$
\int e^{x}\cos nx\,dx=\frac{e^x(\cos nx+n\sin nx)}{1+n^2},\qquad \int e^{x}\sin nx\,dx=\frac{e^x(\sin nx-n\cos nx)}{1+n^2}.
$$

---

# PS2 (Fourier Series page)

## Q1: Orthogonality relations on $[-L,L]$
This is proved in full in [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae#2. Orthogonality (L4–5, PS2 FS Q1)|FS1 §2]]. In outline, with $k=\pi/L$:

**$m\neq n$.**

$$\int_{-L}^L\cos mkx\cos nkx\,dx=\frac12\int_{-L}^L\big[\cos(m-n)kx+\cos(m+n)kx\big]dx=\frac12\Big[\frac{\sin(m-n)kx}{(m-n)k}+\frac{\sin(m+n)kx}{(m+n)k}\Big]_{-L}^{L}=0,$$

because $\sin(p\pi)=0$ for integer $p$. The same works for $\sin\sin$ using $\cos(A-B)-\cos(A+B)$.

**$m=n$.**

$$\int_{-L}^L\cos^2nkx\,dx=\frac12\int_{-L}^L(1+\cos2nkx)\,dx=\frac12\Big[x+\frac{\sin2nkx}{2nk}\Big]_{-L}^{L}=L .$$

The same for $\sin^2$ using $\frac12(1-\cos2A)$.

**Mixed.** $\cos mkx\sin nkx$ is odd, so its integral over $[-L,L]$ is $0$ for all $m,n$. Or use $2\sin A\cos B=\sin(A-B)+\sin(A+B)$, where every term integrates to a cosine difference that is $0$.

Result: $\int\cos\cos=L\delta_{mn}$, $\int\sin\sin=L\delta_{mn}$ and $\int\cos\sin=0$ ✔.

## Q2: $f(x)=1+x$ on $-2\leq x<2$
**(a) Period.** The interval has length $4$, so the period is $2\ell=4$ and $\ell=2$.

**(b) Sketch.** A line rising from $-1$ at $x=-2^+$ to $3$ at $x=2^-$, repeated every 4 units. At $x=\pm2,\pm6$ the series takes the jump average $\frac{3+(-1)}2=1$.

**(c) Series and Euler formulae.**

$$
f(x)=\frac12a_0+\sum_{n=1}^\infty\Big[a_n\cos\frac{n\pi x}2+b_n\sin\frac{n\pi x}2\Big],\qquad a_n=\frac12\int_{-2}^2f\cos\frac{n\pi x}2dx,\quad b_n=\frac12\int_{-2}^2f\sin\frac{n\pi x}2dx .
$$

**(d) Coefficients.** Split $f$ into $1$ (even) plus $x$ (odd).
- $a_0=\frac12\int_{-2}^2(1+x)\,dx=\frac12\cdot4=2$.
- $a_n$ ($n\geq1$): the $1$-part gives $\frac12\big[\frac{2}{n\pi}\sin\frac{n\pi x}2\big]_{-2}^2=0$, and the $x$-part is odd × even, so it vanishes. Hence $a_n=0$.
- $b_n$: the $1$-part is even × odd, so it vanishes. The $x$-part is even, so

$$b_n=\int_0^2x\sin\frac{n\pi x}2dx=\Big[-\frac{2x}{n\pi}\cos\frac{n\pi x}2\Big]_0^2+\frac{2}{n\pi}\int_0^2\cos\frac{n\pi x}{2}dx=-\frac{4(-1)^n}{n\pi}+0=\frac{4(-1)^{n+1}}{n\pi}.$$

$$
1+x=1+\frac4\pi\sum_{n=1}^\infty\frac{(-1)^{n+1}}{n}\sin\frac{n\pi x}{2},\qquad -2<x<2 .
$$

---

# PS3: Fourier Series

## Q1: $f(x)=e^x$ on $-\pi<x<\pi$
### (a) Coefficients
- $a_0=\frac1\pi\int_{-\pi}^{\pi}e^xdx=\frac{e^\pi-e^{-\pi}}{\pi}=\frac{2\sinh\pi}{\pi}$.
- $a_n=\frac1\pi\Big[\frac{e^x(\cos nx+n\sin nx)}{1+n^2}\Big]_{-\pi}^{\pi}=\frac1\pi\cdot\frac{(-1)^n(e^\pi-e^{-\pi})}{1+n^2}=\frac{2(-1)^n\sinh\pi}{\pi(1+n^2)}$.
- $b_n=\frac1\pi\Big[\frac{e^x(\sin nx-n\cos nx)}{1+n^2}\Big]_{-\pi}^{\pi}=\frac1\pi\cdot\frac{-n(-1)^n(e^\pi-e^{-\pi})}{1+n^2}=-\frac{2n(-1)^n\sinh\pi}{\pi(1+n^2)}$.

$$
e^x=\frac{\sinh\pi}{\pi}\Big[1+2\sum_{n=1}^\infty\frac{(-1)^n}{1+n^2}\big(\cos nx-n\sin nx\big)\Big],\qquad -\pi<x<\pi .
$$

> [!tip] Where does the integral $\int e^x\cos nx\,dx$ come from?
> Integrate by parts twice and you get back the original integral $I$: $I=e^x\cos nx+ne^x\sin nx-n^2I$, so $I=\frac{e^x(\cos nx+n\sin nx)}{1+n^2}$.
> Faster: $\int e^{(1+jn)x}dx=\frac{e^{(1+jn)x}}{1+jn}$, then take real and imaginary parts.

### (b) Sketch on $[-3\pi,3\pi]$
![[m2048_fs_ps3_q1_exp.png|640]]

### (c) Values of the series
The periodic extension is continuous inside $(-\pi,\pi)$ and jumps at odd multiples of $\pi$.

| $x$ | series value | why |
|---|---|---|
| $0$ | $e^0=1$ | continuous |
| $-\pi/2$ | $e^{-\pi/2}\approx0.208$ | continuous |
| $\pi/2$ | $e^{\pi/2}\approx4.810$ | continuous |
| $-\pi$ | $\frac12(e^{\pi}+e^{-\pi})=\cosh\pi\approx11.592$ | jump: the average of the left limit $e^\pi$ (from the previous period) and the right limit $e^{-\pi}$ |
| $\pi$ | $\cosh\pi$ | same jump |

### (d) $\displaystyle\sum_{n=0}^\infty\frac{(-1)^n}{1+n^2}$
Set $x=0$, where the series equals $1$:

$$
1=\frac{\sinh\pi}{\pi}\Big[1+2\sum_{n=1}^\infty\frac{(-1)^n}{1+n^2}\Big]\quad\Longrightarrow\quad\sum_{n=1}^\infty\frac{(-1)^n}{1+n^2}=\frac12\Big(\frac{\pi}{\sinh\pi}-1\Big).
$$

Adding the $n=0$ term, which is $1$:

$$
\boxed{\sum_{n=0}^\infty\frac{(-1)^n}{1+n^2}=\frac12\Big(1+\frac{\pi}{\sinh\pi}\Big)\approx0.63601}
$$

A numerical sum of $2\times10^5$ terms gives $0.6360145$ ✔.

*(Bonus: $x=\pi$ gives $\cosh\pi$ from the series, which leads to $\sum_{n\geq0}\frac1{1+n^2}=\frac12(1+\pi\coth\pi)$.)*

## Q2: Cosine series of $f(x)=x$ on $0\leq x\leq1$
### (a)
Use the even extension, which has period $2$, so $\ell=1$.
- $a_0=2\int_0^1x\,dx=1$.
- $a_n=2\int_0^1x\cos n\pi x\,dx=2\Big[\frac{x\sin n\pi x}{n\pi}+\frac{\cos n\pi x}{n^2\pi^2}\Big]_0^1=\frac{2\big[(-1)^n-1\big]}{n^2\pi^2}$. This is $-\frac4{n^2\pi^2}$ for odd $n$ and $0$ for even $n$.

$$
x=\frac12-\frac{4}{\pi^2}\sum_{n=0}^\infty\frac{\cos(2n+1)\pi x}{(2n+1)^2},\qquad 0\leq x\leq1 .
$$

### (b) Sketch: a triangle wave between 0 and 1 with period 2
![[m2048_fs_ps3_q2_cosine.png|620]]

### (c) $\sum\frac1{(2n+1)^2}=\frac{\pi^2}8$
The even extension is continuous, so the series equals $f$ everywhere. At $x=0$:

$$0=\frac12-\frac4{\pi^2}\sum_{n=0}^\infty\frac{1}{(2n+1)^2}\quad\Longrightarrow\quad\sum_{n=0}^\infty\frac1{(2n+1)^2}=\frac{\pi^2}{8}\ ✔$$

SymPy's `summation` confirms this.

## Q3: Half-wave rectified sine
$f(t)=0$ on $-\pi\leq t<0$ and $f(t)=\sin t$ on $0\leq t<\pi$, period $2\pi$.
- $a_0=\frac1\pi\int_0^\pi\sin t\,dt=\frac2\pi$, so $\frac12a_0=\frac1\pi$.
- $a_n$ for $n\neq1$: use $\sin t\cos nt=\frac12[\sin(1+n)t+\sin(1-n)t]$:

$$
a_n=\frac1{2\pi}\Big[-\frac{\cos(1+n)t}{1+n}-\frac{\cos(1-n)t}{1-n}\Big]_0^\pi .
$$

  Since $\cos(1\pm n)\pi=-(-1)^n$,

$$
a_n=\frac{1+(-1)^n}{2\pi}\Big[\frac1{1+n}+\frac1{1-n}\Big]=\frac{1+(-1)^n}{\pi(1-n^2)} .
$$

  This is $0$ for odd $n$. For $n=2k$ it is $-\dfrac{2}{\pi(4k^2-1)}$.
- $a_1=\frac1\pi\int_0^\pi\sin t\cos t\,dt=\frac1{2\pi}\int_0^\pi\sin2t\,dt=0$.
- $b_n$ for $n\neq1$: $\frac1{2\pi}\int_0^\pi[\cos(1-n)t-\cos(1+n)t]\,dt=0$, because each term integrates to a sine of an integer multiple of $\pi$.
- $b_1=\frac1\pi\int_0^\pi\sin^2t\,dt=\frac1\pi\cdot\frac\pi2=\frac12$.

$$
\boxed{f(t)=\frac1\pi+\frac12\sin t-\frac2\pi\sum_{n=1}^\infty\frac{\cos2nt}{4n^2-1}}\ ✔
$$

![[m2048_fs_ps3_q3_rectifier.png|620]]

> [!warning] Always treat $n=1$ separately
> The general formula has $1-n^2$ in the denominator, so it is undefined at $n=1$. Here $a_1=0$ and $b_1=\frac12$ come only from the separate calculation. Forgetting them loses the $\tfrac12\sin t$ term.

---

# PS4: Complex Fourier Series

## Q1: $f(x)=x$ on $(-\pi,\pi)$, then $g(x)=x^2$
### Complex series for $x$
- $c_0=\frac1{2\pi}\int_{-\pi}^{\pi}x\,dx=0$.
- For $n\neq0$, integrate by parts with $u=x$ and $dv=e^{-jnx}dx$, so $v=\frac{e^{-jnx}}{-jn}$:

$$
c_n=\frac1{2\pi}\Big\{\Big[\frac{xe^{-jnx}}{-jn}\Big]_{-\pi}^{\pi}+\frac1{jn}\underbrace{\int_{-\pi}^{\pi}e^{-jnx}dx}_{=0}\Big\}=\frac1{2\pi}\cdot\frac{\pi(-1)^n+\pi(-1)^n}{-jn}=\frac{(-1)^n}{-jn}=\frac{j(-1)^n}{n}.
$$

  This uses $e^{\mp jn\pi}=(-1)^n$.

$$
x=\sum_{n\neq0}\frac{j(-1)^n}{n}e^{jnx}.
$$

**Real form.** $a_n=2\,\mathrm{Re}\,c_n=0$ and $b_n=-2\,\mathrm{Im}\,c_n=\frac{2(-1)^{n+1}}{n}$, so $x=\sum\frac{2(-1)^{n+1}}n\sin nx$ ✔ (the sawtooth).

### Integrate to get $x^2$
Integrate from $0$ to $x$ term by term, which is always allowed:

$$
\frac{x^2}{2}=\sum_{n\neq0}\frac{j(-1)^n}{n}\cdot\frac{e^{jnx}-1}{jn}=\sum_{n\neq0}\frac{(-1)^n}{n^2}e^{jnx}+C,\qquad C=-\sum_{n\neq0}\frac{(-1)^n}{n^2}.
$$

The constant is the mean value of $\frac{x^2}2$, i.e. its $c_0$: $C=\frac1{2\pi}\int_{-\pi}^{\pi}\frac{x^2}2dx=\frac{\pi^2}{6}$. This is consistent with $\sum_{n\geq1}\frac{(-1)^{n+1}}{n^2}=\frac{\pi^2}{12}$. So

$$
x^2=\frac{\pi^2}{3}+\sum_{n\neq0}\frac{2(-1)^n}{n^2}e^{jnx}.
$$

**Real form.** $c_n=c_{-n}=\frac{2(-1)^n}{n^2}$ is real, so $a_n=2c_n=\frac{4(-1)^n}{n^2}$ and $b_n=0$:

$$
x^2=\frac{\pi^2}{3}+\sum_{n=1}^\infty\frac{4(-1)^n}{n^2}\cos nx\ ✔
$$

This matches [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series|FS3]], and direct SymPy integration gives the same $c_n$.

## Q2: Square wave, $f=0$ on $(-2,0)$ and $f=1$ on $(0,2)$, period 4
Here $\ell=2$, so the basis is $e^{jn\pi t/2}$.
- $c_0=\frac14\int_0^2dt=\frac12$.
- For $n\neq0$:

$$
c_n=\frac14\int_0^2e^{-jn\pi t/2}dt=\frac14\Big[\frac{e^{-jn\pi t/2}}{-jn\pi/2}\Big]_0^2=\frac{1-e^{-jn\pi}}{2jn\pi}=\frac{1-(-1)^n}{2jn\pi}.
$$

  This is $\dfrac{1}{jn\pi}=-\dfrac{j}{n\pi}$ for odd $n$ and $0$ for even $n\neq0$.

$$
f(t)=\frac12+\sum_{n\ \mathrm{odd}}\frac{1}{jn\pi}e^{jn\pi t/2}.
$$

**Real form.** $a_n=2\,\mathrm{Re}\,c_n=0$, and $b_n=-2\,\mathrm{Im}\,c_n=\frac{2}{n\pi}$ for odd $n$. Writing $n=2k-1$:

$$
\boxed{f(t)=\frac12+\frac2\pi\sum_{k=1}^\infty\frac{1}{2k-1}\sin\frac{(2k-1)\pi t}{2}}\ ✔
$$

Check: $f-\frac12$ is odd, so the real form should be a pure sine series, and it is ✔.

## Sources
- Problem Sheets 2–4. Every coefficient was checked in SymPy, and the sums were checked numerically (see `fs_check.py` in the session scratchpad).
