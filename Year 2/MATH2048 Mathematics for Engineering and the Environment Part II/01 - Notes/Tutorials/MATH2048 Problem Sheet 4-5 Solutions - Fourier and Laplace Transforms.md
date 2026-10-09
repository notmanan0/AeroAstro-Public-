---
title: "MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: tutorial
stream: "Block 3: Fourier and Laplace Transforms"
tags:
  - math2048
  - tutorial-solutions
  - fourier-transform
  - laplace-transform
sheet: "PS4 (Fourier Transforms page) + PS5 (Laplace Transforms)"
theory_notes: ["[[MATH2048 TR1 - Fourier Transforms]]", "[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]", "[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
key_concepts: ["[[Fourier Transform]]", "[[Laplace Transform Properties and Proofs]]", "[[Partial Fractions for Inverse Laplace]]", "[[Heaviside Step Function]]", "[[Dirac Delta Function]]"]
status: complete
sources: ["02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 4.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 5.pdf"]
---

# MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms

> [!abstract] Sheet Info
> Every answer was checked with SymPy (`integrate`, `laplace_transform`, `inverse_laplace_transform`, `apart`, `dsolve`). The integral identity in PS4 and the peaks in PS5 Q4 were also checked numerically with SciPy and NumPy.

## Theory Links
- [[MATH2048 TR1 - Fourier Transforms]] · [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]] · [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]

---

# PS4: Fourier transforms

## Q1: $f(t)=e^{-\omega_0|t|}$, $\omega_0>0$
Split the integral at $t=0$, since $|t|=-t$ for $t<0$:
$$
F(\omega)=\frac1{\sqrt{2\pi}}\Big[\int_{-\infty}^0e^{(\omega_0-j\omega)t}dt+\int_0^\infty e^{-(\omega_0+j\omega)t}dt\Big]=\frac1{\sqrt{2\pi}}\Big[\frac1{\omega_0-j\omega}+\frac1{\omega_0+j\omega}\Big].
$$
Both limits at infinity vanish because $\omega_0>0$. Adding the fractions over the common denominator $\omega_0^2+\omega^2$:
$$
\boxed{F(\omega)=\sqrt{\frac2\pi}\;\frac{\omega_0}{\omega_0^2+\omega^2}}
$$
The result is real and even, because $f$ is real and even. It is a Lorentzian, with width $\sim\omega_0$ (see [[MATH2048 TR1 - Fourier Transforms|TR1]] figure).

## Q2: $f(t)=\sin(at)$ for $|t|\leq\pi/a$, otherwise $0$
**Transform.** $f$ is odd, so only the $-j\sin\omega t$ part of $e^{-j\omega t}$ survives:
$$
F=\frac{-2j}{\sqrt{2\pi}}\int_0^{\pi/a}\sin at\,\sin\omega t\,dt=\frac{-j}{\sqrt{2\pi}}\int_0^{\pi/a}\big[\cos(a-\omega)t-\cos(a+\omega)t\big]dt .
$$
Integrating each term, and using $\sin(\pi-\theta)=\sin\theta$ and $\sin(\pi+\theta)=-\sin\theta$:
$$
\int_0^{\pi/a}\cos(a-\omega)t\,dt=\frac{\sin\big(\pi-\frac{\omega\pi}{a}\big)}{a-\omega}=\frac{\sin(\omega\pi/a)}{a-\omega},\qquad
\int_0^{\pi/a}\cos(a+\omega)t\,dt=\frac{\sin\big(\pi+\frac{\omega\pi}{a}\big)}{a+\omega}=-\frac{\sin(\omega\pi/a)}{a+\omega}.
$$
Subtracting the second from the first gives
$$
F=\frac{-j}{\sqrt{2\pi}}\sin\frac{\omega\pi}a\Big[\frac1{a-\omega}+\frac1{a+\omega}\Big]=\boxed{-j\sqrt{\frac2\pi}\;\frac{a\sin(\omega\pi/a)}{a^2-\omega^2}}
$$
With $a=1$ this reproduces the Lecture 9 result ✔.

**Fourier integral representation.** $F$ is odd in $\omega$ and purely imaginary. So in $e^{j\omega t}=\cos\omega t+j\sin\omega t$, only the $j\sin\omega t$ part survives the integral, and it contributes twice the integral over $(0,\infty)$:
$$
f(t)=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}F e^{j\omega t}d\omega=\frac{2j}{\sqrt{2\pi}}\int_0^\infty F(\omega)\sin\omega t\,d\omega .
$$
Substituting $F$:
$$
f(t)=\frac{2j}{\sqrt{2\pi}}\cdot(-j)\sqrt{\frac2\pi}\int_0^\infty\frac{a\sin(\omega\pi/a)\sin\omega t}{a^2-\omega^2}d\omega=\boxed{\frac{2a}{\pi}\int_0^\infty\frac{\sin(\omega\pi/a)\sin(\omega t)}{a^2-\omega^2}d\omega}\ ✔
$$

**The integral.** Take $a=1$ and $t=\pi/2$. Since $|t|\leq\pi$ and $f$ is continuous there, $f(\pi/2)=\sin\frac\pi2=1$. So
$$
1=\frac2\pi\int_0^\infty\frac{\sin\omega\pi\,\sin(\omega\pi/2)}{1-\omega^2}d\omega\quad\Longrightarrow\quad\int_0^\infty\frac{\sin(\omega\pi)\sin(\omega\pi/2)}{1-\omega^2}d\omega=\frac\pi2\ ✔
$$
Numerical quadrature gives $1.5707963$ ✔. The apparent singularity at $\omega=1$ is removable, because $\sin\omega\pi\to0$ there.

---

# PS5: Laplace transforms

## Q1: Transforms from the definition
**(a) $\sinh ax$.** Write it as $\frac12(e^{ax}-e^{-ax})$:
$$
\frac12\Big[\int_0^\infty e^{-(s-a)x}dx-\int_0^\infty e^{-(s+a)x}dx\Big]=\frac12\Big[\frac1{s-a}-\frac1{s+a}\Big]=\frac{a}{s^2-a^2},\qquad s>|a| .
$$

**(b) $4\sin x\cos x=2\sin2x$.** Using $\sin2x=\frac{e^{2jx}-e^{-2jx}}{2j}$:
$$
2\cdot\frac1{2j}\Big[\frac1{s-2j}-\frac1{s+2j}\Big]=\frac1j\cdot\frac{4j}{s^2+4}=\frac{4}{s^2+4}.
$$

**(c) $x\cos ax$.** Use $\cos ax=\mathrm{Re}\,e^{jax}$ (valid for real $s$), then integrate by parts:
$$
\int_0^\infty xe^{-(s-ja)x}dx=\frac{1}{(s-ja)^2}=\frac{(s+ja)^2}{(s^2+a^2)^2} .
$$
Taking the real part:
$$
\mathcal L[x\cos ax]=\frac{s^2-a^2}{(s^2+a^2)^2}.
$$
Check with the $x f$ rule: $-\frac{d}{ds}\frac{s}{s^2+a^2}=\frac{s^2-a^2}{(s^2+a^2)^2}$ ✔.

**(d) $e^{-x}\sin2x$.** $\int_0^\infty e^{-(s+1)x}\sin2x\,dx$ is $\mathcal L[\sin2x]$ evaluated at $s+1$:
$$
\frac{2}{(s+1)^2+4}.
$$

## Q2: Inversions
| | $\tilde f(s)$ | Partial fractions / rearrangement | $f(x)$ |
|---|---|---|---|
| (a) | $\dfrac1{s(s-3)}$ | $-\dfrac1{3s}+\dfrac1{3(s-3)}$ | $\tfrac13(e^{3x}-1)$ |
| (b) | $\dfrac6{(s+2)^2+9}$ | $2\cdot\dfrac{3}{(s+2)^2+3^2}$ | $2e^{-2x}\sin3x$ |
| (c) | $\dfrac{s+3}{s^2+2s+5}$ | $\dfrac{(s+1)}{(s+1)^2+2^2}+\dfrac{2}{(s+1)^2+2^2}$ | $e^{-x}(\cos2x+\sin2x)$ |
| (d) | $\dfrac1{s(s+1)(s+2)}$ | $\dfrac1{2s}-\dfrac1{s+1}+\dfrac1{2(s+2)}$ (cover-up) | $\tfrac12-e^{-x}+\tfrac12e^{-2x}$ |

The cover-up method for (d): to find the coefficient of $\frac1{s-r}$, delete that factor from the denominator and evaluate what is left at $s=r$.
- At $s=0$: $\frac{1}{1\cdot2}=\frac12$.
- At $s=-1$: $\frac{1}{(-1)(1)}=-1$.
- At $s=-2$: $\frac{1}{(-2)(-1)}=\frac12$.

## Q3: IVPs
Throughout, $\mathcal L[y']=s\tilde y-y(0)$ and $\mathcal L[y'']=s^2\tilde y-sy(0)-y'(0)$.

### (a) $y''-y'-6y=0$, $y(0)=1$, $y'(0)=-1$
$$(s^2\tilde y-s+1)-(s\tilde y-1)-6\tilde y=0\ \Longrightarrow\ \tilde y=\frac{s-2}{(s-3)(s+2)}=\frac{1/5}{s-3}+\frac{4/5}{s+2}$$
$$y=\tfrac15e^{3x}+\tfrac45e^{-2x}$$

### (b) $y''-2y'-2y=0$, $y(0)=2$, $y'(0)=0$
$$(s^2\tilde y-2s)-2(s\tilde y-2)-2\tilde y=0\ \Longrightarrow\ \tilde y=\frac{2s-4}{(s-1)^2-3}=\frac{2(s-1)}{(s-1)^2-3}-\frac{2}{(s-1)^2-3}$$
Using $\mathcal L[\cosh bx]=\frac{s}{s^2-b^2}$ and $\mathcal L[\sinh bx]=\frac{b}{s^2-b^2}$ with $b=\sqrt3$, plus the first shift theorem:
$$y=e^{x}\Big(2\cosh\sqrt3x-\frac2{\sqrt3}\sinh\sqrt3x\Big)=\Big(1-\tfrac1{\sqrt3}\Big)e^{(1+\sqrt3)x}+\Big(1+\tfrac1{\sqrt3}\Big)e^{(1-\sqrt3)x}$$

### (c) $y''-2y'+2y=\cos x$, $y(0)=1$, $y'(0)=0$
$$(s^2-2s+2)\tilde y=s-2+\frac{s}{s^2+1}\ \Longrightarrow\ \tilde y=\frac{s-2}{(s-1)^2+1}+\frac{s}{(s^2+1)\big((s-1)^2+1\big)}$$
Combining everything and applying partial fractions (SymPy `apart`):
$$\tilde y=\frac{1}{5}\cdot\frac{s-2}{s^2+1}+\frac25\cdot\frac{2s-3}{(s-1)^2+1}=\frac15\Big[\frac{s}{s^2+1}-\frac{2}{s^2+1}\Big]+\frac25\Big[\frac{2(s-1)}{(s-1)^2+1}-\frac{1}{(s-1)^2+1}\Big]$$
$$y=\tfrac15(\cos x-2\sin x)+\tfrac25e^{x}(2\cos x-\sin x)$$
**Check**: $y(0)=\frac15+\frac45=1$ ✔.

### (d) $y''+2y'+y=4e^{-x}$, $y(0)=2$, $y'(0)=-1$
$$(s+1)^2\tilde y=2s+3+\frac4{s+1}\ \Longrightarrow\ \tilde y=\frac{2(s+1)+1}{(s+1)^2}+\frac{4}{(s+1)^3}=\frac2{s+1}+\frac1{(s+1)^2}+\frac4{(s+1)^3}$$
Using $\mathcal L[x^ne^{-x}]=\frac{n!}{(s+1)^{n+1}}$:
$$y=e^{-x}\big(2+x+2x^2\big)$$

### (e) $y''+4y=\sin x-H(x-2\pi)\sin(x-2\pi)$, $y(0)=y'(0)=0$
The forcing is already in second-shift form, so
$$(s^2+4)\tilde y=\frac{1-e^{-2\pi s}}{s^2+1}\ \Longrightarrow\ \tilde y=\big(1-e^{-2\pi s}\big)\underbrace{\frac1{(s^2+1)(s^2+4)}}_{=\frac13\left[\frac1{s^2+1}-\frac1{s^2+4}\right]}$$
Let $g(x)=\frac13\sin x-\frac16\sin2x$. Then
$$y=g(x)-H(x-2\pi)g(x-2\pi) .$$
Since $g$ is $2\pi$-periodic, this is
$$\boxed{y=\Big(\tfrac13\sin x-\tfrac16\sin2x\Big)\big[1-H(x-2\pi)\big]}$$
The forcing is exactly one period of $\sin x$, and at $x=2\pi$ both $y$ and $y'$ are zero. So the system is left **completely at rest** for $x>2\pi$.

### (f) $y''+3y'+2y=f(x)$, with $f=1$ on $[0,10]$ and $0$ after, $y(0)=y'(0)=0$
Write $f=1-H(x-10)$, so
$$(s+1)(s+2)\tilde y=\frac{1-e^{-10s}}{s},\qquad \frac1{s(s+1)(s+2)}\ \to\ g(x)=\tfrac12-e^{-x}+\tfrac12e^{-2x}\ \text{(Q2d)}.$$
$$y=g(x)-H(x-10)\,g(x-10)=\Big[\tfrac12-e^{-x}+\tfrac12e^{-2x}\Big]-H(x-10)\Big[\tfrac12-e^{-(x-10)}+\tfrac12e^{-2(x-10)}\Big]$$

### (g) $2y''+y'+2y=\delta(x-5)$, $y(0)=y'(0)=0$
Divide by 2 and complete the square:
$$\tilde y=\frac{e^{-5s}}{2s^2+s+2}=\frac{e^{-5s}}{2}\cdot\frac{1}{(s+\frac14)^2+\frac{15}{16}}$$
With $b=\frac{\sqrt{15}}4$, $\mathcal L^{-1}\big[\frac{1}{(s+1/4)^2+b^2}\big]=\frac1be^{-x/4}\sin bx$. So
$$y=H(x-5)\,\frac{2}{\sqrt{15}}\,e^{-(x-5)/4}\sin\Big(\frac{\sqrt{15}}{4}(x-5)\Big)$$

### (h) $y''+y=\delta(x-2\pi)\cos x$, $y(0)=0$, $y'(0)=1$
Use the sifting identity: $\delta(x-2\pi)\cos x=\cos2\pi\,\delta(x-2\pi)=\delta(x-2\pi)$. Then
$$(s^2+1)\tilde y-1=e^{-2\pi s}\ \Longrightarrow\ \tilde y=\frac{1+e^{-2\pi s}}{s^2+1}$$
$$y=\sin x+H(x-2\pi)\sin(x-2\pi)=\sin x\,\big[1+H(x-2\pi)\big]$$
The kick arrives in phase with the motion, since $y'(2\pi)=1$, so it **doubles** the amplitude.

## Q4: $y''+\gamma y'+y=k\delta(x-1)$, $y(0)=y'(0)=0$
**General solution.** $\tilde y=\dfrac{ke^{-s}}{(s+\gamma/2)^2+\omega_d^2}$ with $\omega_d=\sqrt{1-\gamma^2/4}$. So
$$y=\frac{k}{\omega_d}H(x-1)\,e^{-\gamma(x-1)/2}\sin\big(\omega_d(x-1)\big).$$

**Peak.** Let $\tau=x-1$ and $r(\tau)=e^{-\gamma\tau/2}\sin(\omega_d\tau)/\omega_d$. Setting $r'=0$:
$$-\tfrac\gamma2\sin\omega_d\tau+\omega_d\cos\omega_d\tau=0\ \Longrightarrow\ \tan(\omega_d\tau^*)=\frac{2\omega_d}{\gamma} .$$
At that point $\sin\omega_d\tau^*=\dfrac{2\omega_d}{\sqrt{\gamma^2+4\omega_d^2}}=\omega_d$, because $\gamma^2+4\omega_d^2=4$. So the peak is simply
$$r_{\max}=e^{-\gamma\tau^*/2},\qquad k_1=\frac{2}{r_{\max}}=2\exp\!\Big(\frac{\gamma\tau^*}{2}\Big),\qquad \tau^*=\frac{1}{\omega_d}\arctan\frac{2\omega_d}{\gamma}.$$

| $\gamma$ | $\omega_d$ | $\tau^*$ | $k_1$ |
|---|---|---|---|
| (a) $\tfrac12$ | $\sqrt{15}/4=0.96825$ | $1.36134$ | **2.8108** |
| (b) $\tfrac14$ | $\sqrt{63}/8=0.99216$ | $1.45690$ | **2.3995** |
| (c) $0$ | $1$ | $\pi/2$ | **2** (since $y=k\sin(x-1)$, the peak is $k$) |

A brute-force maximisation of $r(\tau)$ on a fine grid gives the same $k_1$ values to 5 s.f. ✔. More damping needs a bigger kick to reach the same peak.

![[m2048_tr_ps5_q4_impulse.png|640]]

## Sources
- PS4 (FT page) and PS5. All answers verified in SymPy and NumPy (`tr_check.py` in the session scratchpad).
