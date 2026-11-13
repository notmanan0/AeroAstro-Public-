---
title: "MATH2048 Formula Sheet"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: formula
aliases: ["MATH2048 formulae"]
tags: [math2048, formula, exam-prep]
status: complete
coverage: "All 19 topic notes (ODE1–3, FS1–3, TR1–3, PDE1–5, VC1–5), 2024-25 lecture series, checked against the notes on 10 Nov 2026"
sources: ["01 - Notes/Topics", "01 - Notes/Tutorials", "02 - Sources/Lectures", "02 - Sources/Lectures & Problem Sheets"]
---

# MATH2048 Formula Sheet

Methods and results by block, in the order of the topic notes; each section links the note that derives them. The official sheet FS/MATH2048 is allowed in the exam, so this one is for revision and for the results the official sheet leaves out.

> [!warning] Conventions used throughout MATH2048
> - $j=\sqrt{-1}$ (STACK uses $i$).
> - ODE3 writes eigenproblems as $y''+\lambda y=0$, so the eigenvalues are positive. The PDE block and the exam write the separated spatial ODE as $X''-\lambda X=0$, so the same eigenvalues come out **negative**, $\lambda_n=-(n\pi/L)^2$. Read the form given before choosing signs.
> - Fourier transform normalisation $\frac1{\sqrt{2\pi}}$ on both the forward and inverse transforms.
> - Conservative fields are written $\mathbf F=-\nabla\phi$ ($\phi$ a potential energy); some questions use $\mathbf F=+\nabla\phi$, which flips every potential difference.
> - Spherical angles: polar angle measured down from the north pole ($t$ in VC4, $\theta$ in VC5), azimuth round the $z$-axis ($s$ in VC4, $\phi$ in VC5).

## Block 1: ODEs

### Constant coefficients ([[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]])

$$
ay''+by'+cy=0\ \xrightarrow{\ y=e^{\lambda x}\ }\ a\lambda^2+b\lambda+c=0\qquad(a,b,c\ \text{constant},\ a\neq0)
$$

| Discriminant | Roots | $y$ |
|---|---|---|
| $b^2-4ac>0$ | $\lambda_1\neq\lambda_2$ real | $c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $b^2-4ac=0$ | $\lambda=-\frac{b}{2a}$ repeated | $(c_1+c_2x)e^{\lambda x}$ |
| $b^2-4ac<0$ | $\alpha\pm j\beta$ | $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |

- Special cases: $y''+k^2y=0$ gives $c_1\cos kx+c_2\sin kx$; $y''-k^2y=0$ gives $c_1e^{kx}+c_2e^{-kx}=A\cosh kx+B\sinh kx$ (hyperbolic form easier with a condition at $x=0$); $c=0$ gives a root $\lambda=0$, a constant solution.
- Repeated root: $xe^{\lambda x}$ works because $2a\lambda+b=0$; reduction of order $y=v(x)e^{\lambda x}$ gives $v''=0$.
- Envelope: $c_1\cos\beta x+c_2\sin\beta x=R\cos(\beta x-\phi)$, $R=\sqrt{c_1^2+c_2^2}$, $\tan\phi=c_2/c_1$, so $|y|\leq Re^{\alpha x}$.
- General solution of the inhomogeneous equation: $y=c_1y_1+c_2y_2+y_P$ for any particular integral $y_P$; apply conditions last.
- Wronskian (background): $W=y_1y_2'-y_1'y_2$ obeys $W'=-pW$ for $y''+py'+qy=0$, so $W=W(x_0)e^{-\int p\,dx}$, zero everywhere or nowhere.
- Mass–spring–damper (background for SESA2027): $m\ddot y+2c\dot y+ky=0$, $\omega_0=\sqrt{k/m}$, roots $-\frac cm\pm\sqrt{\frac{c^2}{m^2}-\omega_0^2}$.
  - Under-damped $c<m\omega_0$: $y=e^{-ct/m}(c_1\cos\omega t+c_2\sin\omega t)$, $\omega=\sqrt{\omega_0^2-c^2/m^2}$.
  - Critical $c=m\omega_0$: $y=(c_1+c_2t)e^{-ct/m}$, fastest return without oscillation.
  - Over-damped $c>m\omega_0$: two negative real roots; the root nearer zero sets the return time.
  - SESA2027 form: $c/m=\zeta\omega_0$, $\ddot y+2\zeta\omega_n\dot y+\omega_n^2y=0$.

### Euler equations and inhomogeneous ODEs ([[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]])

$$
ax^2y''+bxy'+cy=0\ \ (x>0)\ \xrightarrow{\ y=x^n\ }\ an^2+(b-a)n+c=0
$$

$$
t=\ln x:\qquad xy'=\dot y,\qquad x^2y''=\ddot y-\dot y,\qquad a\ddot y+(b-a)\dot y+cy=0
$$

| Roots of $an^2+(b-a)n+c=0$ | $y$ |
|---|---|
| $n_1\neq n_2$ real | $c_1x^{n_1}+c_2x^{n_2}$ |
| $n$ repeated | $x^n(c_1+c_2\ln x)$ |
| $\alpha\pm j\beta$ | $x^\alpha\big[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\big]$ |

Undetermined coefficients ($y=\text{CF}+\text{PI}$, constant coefficients only):

| Source $r(x)$ | Trial $y_P$ |
|---|---|
| polynomial of degree $n$ | $A_nx^n+\dots+A_0$ |
| $e^{kx}$ | $Ce^{kx}$ |
| $\sin\omega x$ or $\cos\omega x$ | $C\sin\omega x+D\cos\omega x$ (always both) |
| $e^{kx}\sin\omega x$ or $e^{kx}\cos\omega x$ | $e^{kx}(C\sin\omega x+D\cos\omega x)$ |
| $x^ne^{kx}$ | $(A_nx^n+\dots+A_0)e^{kx}$ |
| a sum of the above | the sum of the trials |

- Clash rule: if any term of the trial is in the CF, multiply by $x^s$, $s$ the multiplicity of the root ($s\leq2$ for second order).
- Shift substitution: $y=u(x)e^{kx}$ gives $y''+by'+cy=\big[u''+(2k+b)u'+(k^2+bk+c)u\big]e^{kx}$; at a repeated root $k$ both brackets vanish and $u''=re^{-kx}$.
- No sensible trial (logarithms, fractional powers): variation of parameters, $y_P=v_1y_1+v_2y_2$ with $v_1'=-ry_2/W$, $v_2'=ry_1/W$ (not examinable).
- Resonance, undamped, forced at $\omega_s$: $\ddot y+\omega_0^2y=\cos\omega_st$.
  - $\omega_s\neq\omega_0$: $y_P=\dfrac{\cos\omega_st}{\omega_0^2-\omega_s^2}$; from rest, $y=\dfrac{\cos\omega_st-\cos\omega_0t}{\omega_0^2-\omega_s^2}$, beats with envelope period $4\pi/|\omega_0-\omega_s|$ and peak $2/|\omega_0^2-\omega_s^2|$.
  - $\omega_s=\omega_0$: $y_P=\dfrac{t}{2\omega_0}\sin\omega_0t$, the $\omega_s\to\omega_0$ limit of the beat solution.

### BVPs and eigenproblems ([[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]])

| Name | Condition | Heat in a bar |
|---|---|---|
| Dirichlet | $y=f$ | fixed temperature |
| Neumann | $y'=g$ | fixed flux; $y'=0$ insulated |
| Robin (mixed) | $y+cy'=h$ | heat loss set by end temperature |

- Fredholm alternative: a linear BVP has a unique solution iff the homogeneous BVP has only $y\equiv0$; otherwise it has no solution or a one-parameter family.
- For $y''+\lambda y=0$ (with $k>0$) work all three cases every time:

| Case | Roots | General solution |
|---|---|---|
| $\lambda=0$ | $0$ repeated | $c_1+c_2x$ |
| $\lambda=-k^2<0$ | $\pm k$ | $c_1e^{kx}+c_2e^{-kx}$ or $A\cosh kx+B\sinh kx$ |
| $\lambda=k^2>0$ | $\pm jk$ | $c_1\cos kx+c_2\sin kx$ |

Standard eigenproblems for $y''+\lambda y=0$ on $[0,L]$:

| BCs | $\lambda_n$ | $y_n$ | $n$ |
|---|---|---|---|
| $y(0)=y(L)=0$ | $(n\pi/L)^2$ | $\sin\frac{n\pi x}L$ | $1,2,\dots$ |
| $y'(0)=y'(L)=0$ | $(n\pi/L)^2$ | $\cos\frac{n\pi x}L$ (constant at $n=0$) | $0,1,2,\dots$ |
| $y(0)=0$, $y'(L)=0$ | $\big(\frac{(2n-1)\pi}{2L}\big)^2$ | $\sin\frac{(2n-1)\pi x}{2L}$ | $1,2,\dots$ |
| $y'(0)=0$, $y(L)=0$ | $\big(\frac{(2n-1)\pi}{2L}\big)^2$ | $\cos\frac{(2n-1)\pi x}{2L}$ | $1,2,\dots$ |

- Robin example $y(0)=0$, $y'(1)+y(1)=0$: $\lambda_n=k_n^2$, $y_n=\sin k_nx$ with $k_n=-\tan k_n$; $k_1=2.0288$, $k_2=4.9132$, $k_3=7.9787$, one root in each $\big((n-\frac12)\pi,n\pi\big)$. Newton on $g=\sin k+k\cos k$, $g'=2\cos k-k\sin k$.
- Properties (Dirichlet, Neumann or Robin ends): eigenvalues real and increasing to $\infty$; $y_n$ has $n-1$ interior zeros; $\int_0^Ly_my_n\,dx=0$ for $\lambda_m\neq\lambda_n$. The norm $\int_0^Ly_n^2\,dx$ is $L/2$ only for the sine and cosine cases (the Robin $y_1$ gives $0.5977$ on $[0,1]$).

## Block 2: Fourier Series

### Series and Euler formulae ([[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]])

Period $2\pi$, $f$ extended periodically:

$$
f(x)\sim\tfrac12a_0+\sum_{n=1}^\infty\big(a_n\cos nx+b_n\sin nx\big),\qquad a_n=\frac1\pi\int_{-\pi}^{\pi}f\cos nx\,dx,\qquad b_n=\frac1\pi\int_{-\pi}^{\pi}f\sin nx\,dx
$$

- Compute $a_0=\frac1\pi\int_{-\pi}^{\pi}f\,dx$ separately when the general $a_n$ divides by $n$; the series uses $\frac12a_0$, the mean of $f$.
- Orthogonality, integers $m,n\geq1$:

$$
\int_{-\pi}^{\pi}\sin mx\sin nx\,dx=\pi\delta_{mn},\qquad\int_{-\pi}^{\pi}\cos mx\cos nx\,dx=\pi\delta_{mn},\qquad\int_{-\pi}^{\pi}\sin mx\cos nx\,dx=0
$$

| Integer $n$ | Value |
|---|---|
| $\sin n\pi$ | $0$ |
| $\cos n\pi$ | $(-1)^n$ |
| $\sin(n+\frac12)\pi$ | $(-1)^n$ |
| $\cos(n+\frac12)\pi$ | $0$ |
| $1-(-1)^n$ | $0$ ($n$ even), $2$ ($n$ odd) |

### Symmetry, half-range series and convergence ([[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]])

On $(-L,L)$, period $2L$:

$$
f\sim\tfrac12a_0+\sum_{n=1}^\infty\Big(a_n\cos\frac{n\pi x}L+b_n\sin\frac{n\pi x}L\Big),\qquad a_n=\frac1L\int_{-L}^{L}f\cos\frac{n\pi x}L\,dx,\qquad b_n=\frac1L\int_{-L}^{L}f\sin\frac{n\pi x}L\,dx
$$

- Even $f$: $b_n=0$, $a_n=\frac2L\int_0^Lf\cos\frac{n\pi x}L\,dx$. Odd $f$: $a_n=0$ (including $a_0$), $b_n=\frac2L\int_0^Lf\sin\frac{n\pi x}L\,dx$. Products: odd × even is odd; even × even and odd × odd are even.
- Half-range, $f$ given on $[0,L]$:

| Extension | Series | Coefficients |
|---|---|---|
| periodic, period $L$ | all terms in $\cos\frac{2n\pi x}L$, $\sin\frac{2n\pi x}L$ | $a_n=\frac2L\int_0^Lf\cos\frac{2n\pi x}L\,dx$, $b_n=\frac2L\int_0^Lf\sin\frac{2n\pi x}L\,dx$ |
| even, period $2L$ | cosine series, $\frac12a_0+\sum a_n\cos\frac{n\pi x}L$ | $a_n=\frac2L\int_0^Lf\cos\frac{n\pi x}L\,dx$ |
| odd, period $2L$ | sine series, $\sum b_n\sin\frac{n\pi x}L$ | $b_n=\frac2L\int_0^Lf\sin\frac{n\pi x}L\,dx$ |

- Pairing with a PDE: zero value at both ends (Dirichlet) → odd extension, sine series; zero slope at both ends (Neumann) → even extension, cosine series.
- Dirichlet conditions: $f$ bounded and periodic with finitely many maxima, minima and discontinuities per period. Then the series converges to $f(x)$ where $f$ is continuous and to $\frac12\big[f(x^-)+f(x^+)\big]$ at a jump, including jumps hidden at the joins of the periodic extension.

### Calculus with series and the complex form ([[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]])

- Differentiating term by term needs $f$ continuous over its whole periodic extension and piecewise smooth; each derivative multiplies the $n$th coefficient by $n$.
- Integrating term by term needs only the Dirichlet conditions. On $(-\pi,\pi)$:

$$
\int f\,dx\sim C+\tfrac12a_0x+\sum_{n=1}^\infty\Big(\frac{a_n}{n}\sin nx-\frac{b_n}{n}\cos nx\Big)
$$

Then replace $x$ by its sine series and fix $C$ at a point where the extension is continuous (usually $x=0$, not $\pm\pi$).
- Complex series on $(-L,L)$:

$$
f(x)\sim\sum_{n=-\infty}^{\infty}c_ne^{jn\pi x/L},\qquad c_n=\frac1{2L}\int_{-L}^{L}f(x)\,e^{-jn\pi x/L}\,dx,\qquad n=0,\pm1,\pm2,\dots
$$

- $c_0=\frac12a_0$, $c_n=\frac12(a_n-jb_n)$ and $c_{-n}=\frac12(a_n+jb_n)$ for $n>0$; for real $f$, $c_{-n}=\overline{c_n}$, $a_n=2\,\mathrm{Re}\,c_n$, $b_n=-2\,\mathrm{Im}\,c_n$. Even $f$ gives real $c_n$, odd $f$ purely imaginary.
- If $f$ is or contains a basis function, the general $c_n$ formula divides by zero at that $n$: compute that case separately ($e^{jx}$ has $c_1=1$ and nothing else).

### Standard series, sums and convergence rates

| $f$ | Interval | Series |
|---|---|---|
| $x$ | $(-\pi,\pi)$ | $\sum\frac{2(-1)^{n+1}}n\sin nx$; $c_n=\frac{j(-1)^n}{n}$, $c_0=0$ |
| $\lvert x\rvert$ | $(-\pi,\pi)$ | $\frac\pi2-\frac4\pi\sum_{n\ \text{odd}}\frac{\cos nx}{n^2}$ |
| $x^2$ | $[-\pi,\pi]$ | $\frac{\pi^2}3+\sum\frac{4(-1)^n}{n^2}\cos nx$ |
| $x^3$ | $(-\pi,\pi)$ | $\sum\frac{2(-1)^n(6-\pi^2n^2)}{n^3}\sin nx$ |
| $e^x$ | $(-\pi,\pi)$ | $\frac{\sinh\pi}{\pi}\big[1+2\sum\frac{(-1)^n}{1+n^2}(\cos nx-n\sin nx)\big]$; $c_n=\frac{(-1)^n\sinh\pi}{\pi(1-jn)}$ |
| $x$, periodic extension | $(0,\pi)$ | $\frac\pi2-\sum\frac{\sin2nx}{n}$ |
| $x$, cosine series | $[0,1]$ | $\frac12-\frac4{\pi^2}\sum_{n\ \text{odd}}\frac{\cos n\pi x}{n^2}$ |
| $1+x$ | $(-2,2)$ | $1+\frac4\pi\sum\frac{(-1)^{n+1}}n\sin\frac{n\pi x}2$ |
| $0$ on $(-2,0)$, $1$ on $(0,2)$ | period 4 | $\frac12+\frac2\pi\sum_{n\ \text{odd}}\frac1n\sin\frac{n\pi t}2$; $c_n=\frac{j((-1)^n-1)}{2n\pi}$ |

- Sums (evaluate a series where it converges to $f$): $\sum_{n\geq1}\frac1{n^2}=\frac{\pi^2}6$, $\sum_{n\ \text{odd}}\frac1{n^2}=\frac{\pi^2}8$, $1-\frac13+\frac15-\dots=\frac\pi4$, $\sum_{n\geq1}\frac{(-1)^n}{1+n^2}=\frac12\big(\frac{\pi}{\sinh\pi}-1\big)$.
- Decay: a jump in the periodic extension gives coefficients $\sim1/n$, with a Gibbs overshoot tending to $8.95\%$ of the jump; continuous with corners gives $\sim1/n^2$. Integration moves one step faster, differentiation one step slower.

## Block 3: Fourier and Laplace Transforms

### Fourier transform ([[MATH2048 TR1 - Fourier Transforms]])

$$
F(\omega)=\mathcal F[f]=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}f(t)e^{-j\omega t}\,dt,\qquad f(t)=\mathcal F^{-1}[F]=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}F(\omega)e^{j\omega t}\,d\omega
$$

- Exists when $\int_{-\infty}^\infty|f|\,dt<\infty$ (a constant has no transform). The two normalising factors must multiply to $\frac1{2\pi}$ in any convention.
- Limit of the complex series of period $T$: $F(k)=\lim_{T\to\infty}Tc_k/\sqrt{2\pi}$ at $k=2\pi n/T$.
- Linearity; derivative rule $\mathcal F[f']=j\omega F$, $\mathcal F[f^{(n)}]=(j\omega)^nF$ (needs $f\to0$ as $t\to\pm\infty$).
- Shift theorems (not lectured): $\mathcal F[f(t-t_0)]=e^{-j\omega t_0}F(\omega)$, $\mathcal F[e^{j\omega_0t}f]=F(\omega-\omega_0)$.
- Real even $f$ gives real $F$; real odd $f$ gives purely imaginary $F$. Check separately any $\omega$ where the general answer is $0/0$.

| $f(t)$ | $F(\omega)$ |
|---|---|
| $1$ on $\lvert t\rvert<1$, else $0$ | $\sqrt{\frac2\pi}\,\frac{\sin\omega}{\omega}$ ($\sqrt{2/\pi}$ at $\omega=0$) |
| $e^{-\omega_0\lvert t\rvert}$, $\omega_0>0$ | $\sqrt{\frac2\pi}\,\frac{\omega_0}{\omega^2+\omega_0^2}$ |
| $\sin t$ on $\lvert t\rvert<\pi$ | $j\sqrt{\frac2\pi}\,\frac{\sin\pi\omega}{\omega^2-1}$ ($\mp j\sqrt{\pi/2}$ at $\omega=\pm1$) |
| $\cos t$ on $\lvert t\rvert<\pi$ | $-\sqrt{\frac2\pi}\,\frac{\omega\sin\pi\omega}{\omega^2-1}$ |

Response function, $Y(\omega)=G(\omega)U(\omega)$. For $\ddot y+\gamma\dot y+\omega_0^2y=u$:

$$
G=\frac1{\omega_0^2-\omega^2+j\gamma\omega},\qquad|G|^2=\frac1{(\omega_0^2-\omega^2)^2+\gamma^2\omega^2},\qquad\omega_{\text{peak}}^2=\omega_0^2-\tfrac12\gamma^2,\qquad|G|_{\max}=\frac{1}{\gamma\sqrt{\omega_0^2-\frac14\gamma^2}}
$$

- A peak exists only for $\gamma^2<2\omega_0^2$; otherwise $|G|$ falls monotonically from $|G(0)|=1/\omega_0^2$. $|G|_{\max}\approx1/(\gamma\omega_0)$ for $\gamma\ll\omega_0$; $|G|\sim1/\omega^2$ at high frequency.
- SESA2027 form: $\gamma=2\zeta\omega_0$, $\omega_r=\omega_0\sqrt{1-2\zeta^2}$.

### Laplace transform ([[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]])

$$
\tilde f(s)=\mathcal L[f]=\int_0^\infty f(x)e^{-sx}\,dx\qquad\big(\text{exists for the }s\text{ with }f(x)e^{-sx}\to0\text{ as }x\to\infty\big)
$$

| $f(x)$ | $\tilde f(s)$ | Condition |
|---|---|---|
| $1$ | $\frac1s$ | $s>0$ |
| $x^n$ | $\frac{n!}{s^{n+1}}$ | $s>0$ |
| $e^{ax}$ | $\frac1{s-a}$ | $s>a$ |
| $x^ne^{-bx}$ | $\frac{n!}{(s+b)^{n+1}}$ | $s>-b$ |
| $\sin ax$, $\cos ax$ | $\frac a{s^2+a^2}$, $\frac s{s^2+a^2}$ | $s>0$ |
| $\sinh ax$, $\cosh ax$ | $\frac a{s^2-a^2}$, $\frac s{s^2-a^2}$ | $s>\lvert a\rvert$ |
| $H(x-a)$, $a\geq0$ | $\frac{e^{-as}}s$ | $s>0$ |
| $\delta(x-a)$, $a>0$ | $e^{-as}$ | |
| $\delta(x-a)f(x)$, $a>0$ | $f(a)e^{-as}$ | |

| Rule | Result |
|---|---|
| linearity | $\mathcal L[\alpha f+\beta g]=\alpha\tilde f+\beta\tilde g$; but $\mathcal L[fg]\neq\tilde f\tilde g$ |
| first shift | $\mathcal L[e^{-ax}f]=\tilde f(s+a)$ |
| first derivative | $\mathcal L[f']=s\tilde f-f(0)$ |
| second derivative | $\mathcal L[f'']=s^2\tilde f-sf(0)-f'(0)$ |
| multiply by $x$ | $\mathcal L[xf]=-\frac{d\tilde f}{ds}$; $\mathcal L[x^nf]=(-1)^n\frac{d^n\tilde f}{ds^n}$ |
| integral | $\mathcal L\big[\int_0^xf(u)\,du\big]=\frac1s\tilde f$ |
| parameter | $\mathcal L[\partial_af]=\partial_a\tilde f$; transforming a PDE in one variable leaves an ODE |

Partial fractions for inversion (linear constant-coefficient IVP: transform, insert the initial values at once, solve for $\tilde y$, split, invert):

| Factor in the denominator | Terms | Inverse |
|---|---|---|
| $s-r$ | $\frac{A}{s-r}$ | $Ae^{rx}$ |
| $(s-r)^k$ | $\frac{A_1}{s-r}+\dots+\frac{A_k}{(s-r)^k}$ | $\frac{A}{(s-r)^m}\to A\frac{x^{m-1}}{(m-1)!}e^{rx}$, $m=1,\dots,k$ |
| $(s+c)^2+b^2$ | $\frac{B(s+c)+Cb}{(s+c)^2+b^2}$ | $e^{-cx}(B\cos bx+C\sin bx)$ |

- Complete the square, then write the numerator in powers of the same $s+c$; divide by the leading coefficient first ($2s^2+s+2=2\big[(s+\frac14)^2+\frac{15}{16}\big]$).
- Coefficients: cover-up values of $s$ at each root, then compare the highest power or substitute further values.

### Heaviside, delta and the second shift theorem ([[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]])

$$
H(x-a)=\begin{cases}0,&x<a\\1,&x>a\end{cases}\qquad\qquad\int_a^b\delta(x-c)f(x)\,dx=\begin{cases}f(c),&a<c<b\\0,&c\notin[a,b]\end{cases}
$$

| Construction | Effect |
|---|---|
| $f(x)H(x-a)$ | $f$ switched on at $a$ |
| $f(x)[1-H(x-a)]$ | $f$ switched off at $a$ |
| $f(x)[H(x-a)-H(x-b)]$ | $f$ on only for $a<x<b$ |

$$
\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s),\qquad\mathcal L^{-1}\big[e^{-as}\tilde f(s)\big]=f(x-a)H(x-a)\qquad(a>0)
$$

- Unshifted source: $\mathcal L[f(x)H(x-a)]=e^{-as}\mathcal L[f(x+a)]$; e.g. $e^xH(x-1)=e\,e^{x-1}H(x-1)$, $\sin x\,H(x-\pi)=-\sin(x-\pi)H(x-\pi)$.
- Sifting before transforming: $g(x)\delta(x-a)=g(a)\delta(x-a)$. A delta at $a<0$ transforms to $0$; the official sheet's $\mathcal L[\delta(x)]=1$ is the $a=0$ convention.
- Inversion: group the terms of $\tilde y$ by their $e^{-as}$ factor, invert each group without the exponential, then replace $x$ by $x-a$ and multiply by $H(x-a)$. Name the first and second shift theorems as they are used.
- Impulse response of $y''+\gamma y'+y=k\delta(x-a)$ from rest, $\tau=x-a$, $\omega=\sqrt{1-\gamma^2/4}$: $y=\frac k\omega H(\tau)e^{-\gamma\tau/2}\sin\omega\tau$, peak at $\tan\omega\tau^*=2\omega/\gamma$, peak value $ke^{-\gamma\tau^*/2}$; a peak of 2 needs $k_1=2e^{\gamma\tau^*/2}$.
- Across a step source $y$ and $y'$ stay continuous and $y''$ jumps; across a delta source $y'$ jumps by the impulse divided by the leading coefficient.

## Block 4: PDEs

### Classification and the wave equation ([[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]])

$$
au_{xx}+2bu_{xy}+cu_{yy}+du_x+eu_y+fu=0:\qquad b^2-ac\ \begin{cases}>0&\text{hyperbolic}\\=0&\text{parabolic}\\<0&\text{elliptic}\end{cases}
$$

- Halve the mixed coefficient: for $Bu_{xy}$, $b=B/2$. If $a$, $b$, $c$ vary, classify region by region (Tricomi $yu_{xx}=u_{yy}$: $b^2-ac=y$, hyperbolic for $y>0$, elliptic for $y<0$).
- Prototypes: wave $u_{tt}=c^2u_{xx}$ (hyperbolic, finite speed $c$); heat $u_t=ku_{xx}$, $k=\kappa^2>0$ (parabolic, smoothing); Laplace $u_{xx}+u_{yy}=0$ (elliptic, static).
- Conditions, one per derivative in each variable: hyperbolic needs $u$ and $u_t$ at $t=0$ plus one condition per end; parabolic needs $u$ at $t=0$ plus one per end; elliptic needs one on every part of the boundary, not all Neumann.
- String, small slopes, vertical motion only: $y_{tt}=c^2y_{xx}$, $c=\sqrt{T/\rho}$. Any $f(x-ct)+g(x+ct)$ solves it (d'Alembert, lecture notes only).

### Separated solutions on the interval from 0 to L

Notes and exam write the unknown as $y$ (or $u$), separate $y=X(x)T(t)$, divide by $XT$, and set both sides to $\lambda$ with $X''-\lambda X=0$. With $k_n=n\pi/L$ the eigenvalues are $\lambda_n=-k_n^2$.

| PDE | Separated $T$ equation | Dirichlet ends $y(0)=y(L)=0$ | Neumann ends $y_x(0)=y_x(L)=0$ |
|---|---|---|---|
| $y_{tt}=c^2y_{xx}$ | $\ddot T-\lambda c^2T=0$ | $\sum\big[C_n\cos ck_nt+D_n\sin ck_nt\big]\sin k_nx$ | $Gt+H+\sum\big[C_n\cos ck_nt+D_n\sin ck_nt\big]\cos k_nx$ |
| $y_t=\kappa^2y_{xx}$ | $\dot T-\lambda\kappa^2T=0$ | $\sum C_ne^{-\kappa^2k_n^2t}\sin k_nx$ | $\frac12a_0+\sum a_ne^{-\kappa^2k_n^2t}\cos k_nx$ |
| $u_{tt}+2\gamma u_t=u_{xx}$, $L=\pi$, $0<\gamma<1$ | $\ddot T+2\gamma\dot T-\lambda T=0$ | $\sum\sin nx\,e^{-\gamma t}\big[P_n\sin\omega_nt+Q_n\cos\omega_nt\big]$, $\omega_n=\sqrt{n^2-\gamma^2}$ | |

- Coefficients from the initial data (half-range series): $C_n=\frac2L\int_0^Ly(x,0)\sin k_nx\,dx$; for the wave equation $ck_nD_n=\frac2L\int_0^Ly_t(x,0)\sin k_nx\,dx$. Neumann: $\frac12a_0$ (or $H$) is the mean of the initial data.
- Data that is already a finite sum of eigenfunctions is matched by inspection (uniqueness of coefficients); $\cos^3x=\frac34\cos x+\frac14\cos3x$, $\sin^2\pi x=\frac12-\frac12\cos2\pi x$.
- Standard integrals: $2\int_0^1x(1-x)\sin n\pi x\,dx=\frac{4[1-(-1)^n]}{(n\pi)^3}$, $2\int_0^1x(1-x)\cos n\pi x\,dx=-\frac{2[1+(-1)^n]}{(n\pi)^2}$, $2\int_0^1(1-x)\cos n\pi x\,dx=\frac{2[1-(-1)^n]}{(n\pi)^2}$.

### Wave equation ([[MATH2048 PDE2 - Separation of Variables for the Wave Equation]])

- Mode $n$ oscillates at $\omega_n=n\pi c/L$; fundamental $f_1=c/(2L)$. Neumann ends add the $\lambda=0$ mode $T_0=Gt+H$ (rigid drift $Gt$, zero for zero initial velocity).
- Standing waves are travelling waves: $\sin n\pi x\cos n\pi ct=\frac12\big[\sin n\pi(x-ct)+\sin n\pi(x+ct)\big]$.
- Plucked string, height $h$ at $L/2$, from rest: $C_n=\frac{8h}{n^2\pi^2}\sin\frac{n\pi}2$, $D_n=0$.
- Damped string (2025/26 A2, which writes $\kappa$ for $\gamma$), $u(0,x)=\sin x$, from rest: $u=e^{-\gamma t}\big[\cos\omega_1t+\frac{\gamma}{\omega_1}\sin\omega_1t\big]\sin x$, $\omega_1=\sqrt{1-\gamma^2}$; zero initial velocity gives $Q_n=P_n\omega_n/\gamma$.

### Heat equation ([[MATH2048 PDE3 - The Heat Equation]])

- Random walk (stay $\frac12$, step $\frac14$ each way): $y_t=\kappa^2y_{xx}$ with $\kappa^2=\lim\frac{\Delta x^2}{4\Delta t}$; spread variance $2\kappa^2t$; diffusion over a length $\ell$ takes a time of order $\ell^2/\kappa^2$.
- Mode $n$ decays as $e^{-(n\pi\kappa/L)^2t}$; the slowest surviving mode sets the settling time.
- Insulated ends conserve $\int_0^Ly\,dx$ (since $\frac{d}{dt}\int y\,dx=\kappa^2[y_x]_0^L=0$), so $y\to$ the initial mean. Dirichlet ends at zero drive $y\to0$.
- Loss term $u_t=h^2u_{xx}-ku$: put $u=e^{-kt}v$, then $v_t=h^2v_{xx}$ with the same data; every decay rate rises by $k$.

### Inhomogeneous problems ([[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]])

- Source, $y_t=\kappa^2y_{xx}+F(x,t)$ with homogeneous BCs: expand $y=\sum T_n(t)X_n(x)$ and $F=\sum F_n(t)X_n(x)$ in the eigenfunctions of the homogeneous problem, with $F_n=\frac2L\int_0^LF\,X_n\,dx$ (or by inspection; the $n=0$ Neumann term is the mean). Each mode obeys

$$
\dot T_n+\kappa^2k_n^2T_n=F_n(t),\qquad T_n=e^{-\kappa^2k_n^2t}\Big[C_n+\int^te^{\kappa^2k_n^2s}F_n(s)\,ds\Big],
$$

with $C_n$ from the initial data. For a constant $F_n$, $T_n=C_ne^{-\kappa^2k_n^2t}+F_n/(\kappa^2k_n^2)$. For a sinusoidal $F_n$ use undetermined coefficients.
- Wave equation with a source: $\ddot T_n+c^2k_n^2T_n=F_n$, second order, two constants per mode (2024/25 A2: $u=\cos x+\cos3x\cos3t$).
- Inhomogeneous Dirichlet BCs $y(0,t)=f_0(t)$, $y(L,t)=f_1(t)$: subtract $y_p=f_0+(f_1-f_0)\frac xL$. Then $v=y-y_p$ has zero boundary values, initial data $y(x,0)-y_p(x,0)$, and $v_t=\kappa^2v_{xx}-\partial_ty_p$. Constant $f_0$, $f_1$: $y_p$ is the steady state and no source appears. Neumann data: choose a $y_p$ with the given slopes.

### Laplace's equation ([[MATH2048 PDE5 - Laplace's Equation]])

- $\nabla^2u=0$ is the static limit of the wave and heat equations; $\nabla^2u=f$ is Poisson's equation; in one dimension the solutions are straight lines.
- Separate $u=X(x)Y(y)$: $\frac{X''}X=-\frac{Y''}Y=\lambda$, so $X''-\lambda X=0$ and $Y''+\lambda Y=0$. Solve the eigenproblem in the direction whose two sides are homogeneous; the other direction is then hyperbolic, $Y_n=\tilde C_n\cosh k_ny+\tilde D_n\sinh k_ny$.
- Unit square, $u=g(x)$ on $y=1$ and zero on the other sides:

$$
u=\sum_{n=1}^\infty\frac{\hat D_n}{\sinh n\pi}\sin n\pi x\,\sinh n\pi y,\qquad\hat D_n=2\int_0^1g(x)\sin n\pi x\,dx
$$

- Data on $x=1$ instead: swap $x$ and $y$ ($\sinh n\pi x\,\sin n\pi y$). Data on several sides: add the one-side solutions.
- Mode $n$ decays like $e^{-n\pi d}$ at distance $d$ from its data side.
- All-Neumann data needs $\oint\partial_nu\,ds=0$ and fixes $u$ only up to a constant.
- Maximum principle (no source): the maximum and minimum of $u$ are on the boundary, which gives uniqueness of the Dirichlet problem.

## Block 5: Vector Calculus

### Fields, gradient and directional derivative ([[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]])

$$
\mathbf a\cdot\mathbf b=a_1b_1+a_2b_2+a_3b_3=|\mathbf a||\mathbf b|\cos\theta,\qquad\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix},\quad|\mathbf a\times\mathbf b|=|\mathbf a||\mathbf b|\sin\theta
$$

$$
\nabla f=f_x\,\mathbf i+f_y\,\mathbf j+f_z\,\mathbf k,\qquad\frac{\partial f}{\partial n}=\hat{\mathbf n}\cdot\nabla f,\qquad\frac{d\mathbf r}{dt}=\dot x\,\mathbf i+\dot y\,\mathbf j+\dot z\,\mathbf k
$$

- $\hat{\mathbf n}$ must be a unit vector: divide $\mathbf v$ by $|\mathbf v|$ first.
- $\big|\frac{\partial f}{\partial n}\big|\leq|\nabla f|$: the maximum rate of change is $|\nabla f|$, along $\nabla f$.
- $\nabla f$ is normal to the level surface $f=c$ and points towards larger $f$.
- Linearity $\nabla(\alpha f+\beta g)=\alpha\nabla f+\beta\nabla g$; product $\nabla(fg)=f\nabla g+g\nabla f$; radial $\nabla r=\hat{\mathbf r}$, $\nabla f(r)=f'(r)\hat{\mathbf r}$.
- $\mathbf b\times\mathbf a=-\mathbf a\times\mathbf b$; the tangent $d\mathbf r/dt$ has a direction independent of the parametrisation.

### Divergence, curl and the identities ([[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]])

$$
\nabla\cdot\mathbf F=\frac{\partial F_1}{\partial x}+\frac{\partial F_2}{\partial y}+\frac{\partial F_3}{\partial z},\qquad\nabla\times\mathbf F=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\\partial_x&\partial_y&\partial_z\\F_1&F_2&F_3\end{vmatrix}=\big(\partial_yF_3-\partial_zF_2,\ \partial_zF_1-\partial_xF_3,\ \partial_xF_2-\partial_yF_1\big)
$$

$$
\nabla^2f=\nabla\cdot\nabla f=f_{xx}+f_{yy}+f_{zz},\qquad\nabla^2\mathbf F=\big(\nabla^2F_1,\nabla^2F_2,\nabla^2F_3\big)\ \ \text{(Cartesian)}
$$

| # | Identity (fields twice continuously differentiable) |
|---|---|
| 1 | $\nabla(fg)=f\nabla g+g\nabla f$ |
| 2 | $\nabla\times(\nabla f)=\mathbf 0$ |
| 3 | $\nabla\times(g\mathbf F)=g\,\nabla\times\mathbf F+\nabla g\times\mathbf F$ |
| 4 | $\nabla\cdot(g\mathbf F)=\nabla g\cdot\mathbf F+g\,\nabla\cdot\mathbf F$ |
| 5 | $\nabla\cdot(\nabla\times\mathbf F)=0$ |
| 6 | $\nabla\times(\nabla\times\mathbf F)=\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$ |
| 7 | $\nabla(\mathbf F\cdot\mathbf G)=\mathbf F\times(\nabla\times\mathbf G)+\mathbf G\times(\nabla\times\mathbf F)+(\mathbf F\cdot\nabla)\mathbf G+(\mathbf G\cdot\nabla)\mathbf F$ |
| 8 | $\nabla\times(\mathbf F\times\mathbf G)=\mathbf F(\nabla\cdot\mathbf G)-\mathbf G(\nabla\cdot\mathbf F)+(\mathbf G\cdot\nabla)\mathbf F-(\mathbf F\cdot\nabla)\mathbf G$ |

- $(\mathbf F\cdot\nabla)=F_1\partial_x+F_2\partial_y+F_3\partial_z$ acts on each component. The gradient of a vector field is not defined in this course.
- $\nabla\cdot\mathbf r=3$, $\nabla\times\mathbf r=\mathbf 0$; rigid rotation $\mathbf v=-\Omega y\,\mathbf i+\Omega x\,\mathbf j$ has $\nabla\cdot\mathbf v=0$ and vorticity $\nabla\times\mathbf v=2\Omega\,\mathbf k$.
- Solenoidal: $\nabla\cdot\mathbf F=0$. Continuity $\partial_t\rho+\nabla\cdot(\rho\mathbf v)=0$, i.e. $\frac{D\rho}{Dt}=-\rho\nabla\cdot\mathbf v$; incompressible $\nabla\cdot\mathbf v=0$.

### Line integrals and conservative fields ([[MATH2048 VC3 - Line Integrals and Conservative Fields]])

$$
\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F\big(\mathbf r(t)\big)\cdot\frac{d\mathbf r}{dt}\,dt,\qquad\mathbf F=-\nabla\phi\ \Longrightarrow\ \int_A^B\mathbf F\cdot d\mathbf r=\phi(A)-\phi(B),\qquad\oint\mathbf F\cdot d\mathbf r=0
$$

- Independent of the parametrisation; reversing the direction flips the sign; in general it depends on the path.
- Straight line from $P$ to $Q$: $\mathbf r=P+(Q-P)t$, $0\leq t\leq1$.
- On a region without holes where $\mathbf F$ is smooth: $\mathbf F$ conservative $\iff\nabla\times\mathbf F=\mathbf 0\iff\oint\mathbf F\cdot d\mathbf r=0$ for every loop.
- Finding $\phi$ ($F_i=-\partial_i\phi$): integrate the easiest component, leaving an arbitrary function of the other variables, then differentiate and match the rest. $\phi$ is fixed only up to a constant.
- Potential flow: irrotational $\mathbf u=\nabla\phi$ and incompressible give $\nabla^2\phi=0$.

### Surfaces and flux ([[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]])

$$
\mathbf N=\frac{\partial\mathbf r}{\partial s}\times\frac{\partial\mathbf r}{\partial t},\qquad dA=|\mathbf N|\,ds\,dt,\qquad d\mathbf S=\hat{\mathbf n}\,dA=\mathbf N\,ds\,dt,\qquad\text{flux}=\iint_S\mathbf F\cdot d\mathbf S
$$

- Swapping the order of the cross product reverses $\mathbf N$ and the sign of the flux: check its direction at one point. Areas use $|\mathbf N|$, so the order does not matter there.

| Surface | Parametrisation | Normal (direction) | Area |
|---|---|---|---|
| Cylinder, radius $a$, height $h$ | $(a\cos s,\ a\sin s,\ t)$, $-\pi\leq s\leq\pi$, $0\leq t\leq h$ | $\mathbf r_s\times\mathbf r_t=a(\cos s,\sin s,0)$ (outward) | $2\pi ah$ |
| Sphere, radius $a$ | $(a\cos s\sin t,\ a\sin s\sin t,\ a\cos t)$, $0\leq s\leq2\pi$, $0\leq t\leq\pi$ | $\mathbf r_t\times\mathbf r_s=a^2\sin t\,\hat{\mathbf r}$ (outward; $\mathbf r_s\times\mathbf r_t$ is inward) | $4\pi a^2$ |
| Cone, vertex at origin, base radius $a$ at height $h$ | $\big(\frac ahz\cos\theta,\ \frac ahz\sin\theta,\ z\big)$ | $\mathbf r_\theta\times\mathbf r_z=\big(\frac ahz\cos\theta,\frac ahz\sin\theta,-\frac{a^2}{h^2}z\big)$ (outward, downward) | $\pi a\sqrt{a^2+h^2}$ |
| Graph $z=f(x,y)$ | $(x,\ y,\ f(x,y))$ | $(-f_x,-f_y,1)$ (upward) | $\iint\sqrt{1+f_x^2+f_y^2}\,dx\,dy$ |

- Scalar over a surface: $\iint_S\phi\,dA=\iint\phi\big(\mathbf r(s,t)\big)|\mathbf N|\,ds\,dt$.
- With no direction given, take the upward normal (or outward for a closed surface).

### Volumes and the integral theorems ([[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]])

$$
dV=|\det J|\,ds\,dt\,du,\quad J=\frac{\partial(x,y,z)}{\partial(s,t,u)},\qquad dV_{\text{cyl}}=\rho\,d\rho\,d\phi\,dz,\qquad dV_{\text{sph}}=r^2\sin\theta\,dr\,d\theta\,d\phi
$$

- Cylindrical $x=\rho\cos\phi$, $y=\rho\sin\phi$, $z=z$. Spherical $x=r\sin\theta\cos\phi$, $y=r\sin\theta\sin\phi$, $z=r\cos\theta$, $0\leq\theta\leq\pi$ from the north pole.
- Ball of radius $R$: $\frac43\pi R^3$; the region $0\leq r\leq R$, $0\leq\theta\leq\alpha$, $0\leq\phi\leq\beta$ has $V=\frac{R^3\beta}{3}(1-\cos\alpha)$.

$$
\mathop{∯}_{\partial V}\mathbf F\cdot d\mathbf S=\iiint_V\nabla\cdot\mathbf F\,dV,\qquad\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_{\partial S}\mathbf F\cdot d\mathbf r,\qquad\iint_A\Big(\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y}\Big)dx\,dy=\oint(F_1\,dx+F_2\,dy)
$$

- Divergence (Gauss) theorem: closed surface, outward normal, $\nabla\cdot\mathbf F$ defined everywhere inside. To use it on an open surface, close it with a flat piece and subtract that piece's flux.
- Stokes' theorem: open surface; with the thumb along the normal, the fingers give the direction round the edge (upward normal → anticlockwise seen from above). Every surface with the same edge gives the same curl flux, so swap to the flattest one. Over a closed surface the curl flux is $0$.
- Green's theorem is Stokes in the plane (third equation).
- $\mathop{∯}\mathbf r\cdot d\mathbf S=3V$, since $\nabla\cdot\mathbf r=3$.
- Weak form $\frac{d}{dt}\iiint_V\rho\,dV=-\mathop{∯}_S\rho\mathbf v\cdot d\mathbf S$ and the divergence theorem give the strong form $\partial_t\rho+\nabla\cdot(\rho\mathbf v)=0$ wherever the divergence exists (not across a shock).
