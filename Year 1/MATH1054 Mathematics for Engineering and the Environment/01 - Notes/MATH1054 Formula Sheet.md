---
title: "MATH1054 Formula Sheet"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: formula
aliases: ["MATH1054 formulae"]
tags: [math1054, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources/Formulae & Reference"]
---

# MATH1054 Formula Sheet

Methods and results by block. Each section links to its topic note, which has the derivations and worked examples. Also see [[Integration Formulae]] and [[Useful Trigonometry Identities and stuff]] in `02 - Sources/Formulae & Reference`.

## Block 1: Calculus

### Differentiation ([[MATH1054 M03 - Differentiation I|M03]], [[MATH1054 M07 - Functions|M07]], [[MATH1054 M08 - Differentiation II|M08]])

$$
f'(x)=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x},\qquad(uv)'=u'v+uv',\qquad\Big(\frac uv\Big)'=\frac{u'v-uv'}{v^2},\qquad\frac{\mathrm dy}{\mathrm dx}=\frac{\mathrm dy}{\mathrm du}\frac{\mathrm du}{\mathrm dx}
$$

| $f$ | $f'$ | $f$ | $f'$ | $f$ | $f'$ |
|---|---|---|---|---|---|
| $x^n$ | $nx^{n-1}$ | $\sin^{-1}x$ | $\frac1{\sqrt{1-x^2}}$ | $\sinh x$ | $\cosh x$ |
| $e^{ax}$ | $ae^{ax}$ | $\cos^{-1}x$ | $-\frac1{\sqrt{1-x^2}}$ | $\cosh x$ | $\sinh x$ |
| $\ln x$ | $\frac1x$ | $\tan^{-1}x$ | $\frac1{1+x^2}$ | $\tanh x$ | $\mathrm{sech}^2x$ |
| $\tan x$ | $\sec^2x$ | $\sec x$ | $\sec x\tan x$ | $\sinh^{-1}x$ | $\frac1{\sqrt{1+x^2}}$ |
| $a^x$ | $a^x\ln a$ | $\cot x$ | $-\csc^2x$ | $\cosh^{-1}x$ | $\frac1{\sqrt{x^2-1}}$ |

- **Parametric**: $y'=\dot y/\dot x$ and $y''=\frac{\mathrm d}{\mathrm dt}(y')/\dot x$.
- **Implicit**: $y'=-F_x/F_y$.
- **Log differentiation**: $y'=y\,(\ln y)'$.
- **Newton–Raphson**: $x_{n+1}=x_n-\dfrac{f(x_n)}{f'(x_n)}$.
- **Stationary points**: $f'=0$; $f''<0$ gives a max, $f''>0$ a min. An inflection is where $f''$ changes sign.

### Functions ([[MATH1054 M07 - Functions|M07]])
- Hyperbolic definitions: $\cosh x=\frac{e^x+e^{-x}}2$ and $\sinh x=\frac{e^x-e^{-x}}2$, with $\cosh^2-\sinh^2=1$.
- Inverse hyperbolics:

$$
\sinh^{-1}x=\ln(x+\sqrt{x^2+1}),\qquad\cosh^{-1}x=\ln(x+\sqrt{x^2-1}),\qquad\tanh^{-1}x=\tfrac12\ln\frac{1+x}{1-x}
$$

- Principal ranges: $\sin^{-1}\in[-\frac\pi2,\frac\pi2]$, $\cos^{-1}\in[0,\pi]$, $\tan^{-1}\in(-\frac\pi2,\frac\pi2)$.
- Log laws: $\log_ax=\frac{\log_bx}{\log_ba}$.

### Integration ([[MATH1054 M04 - Integration I|M04]], [[MATH1054 M09 - Integration II|M09]], [[MATH1054 M10 - Integration III|M10]])
| $f$ | $\int f$ | $f$ | $\int f$ |
|---|---|---|---|
| $x^n$ | $\frac{x^{n+1}}{n+1}$ | $\frac1{a^2+x^2}$ | $\frac1a\tan^{-1}\frac xa$ |
| $\frac1x$ | $\ln\lvert x\rvert$ | $\frac1{\sqrt{a^2-x^2}}$ | $\sin^{-1}\frac xa$ |
| $e^{ax}$ | $\frac1ae^{ax}$ | $\frac1{\sqrt{x^2+a^2}}$ | $\sinh^{-1}\frac xa$ |
| $\frac{f'}{f}$ | $\ln\lvert f\rvert$ | $\frac1{\sqrt{x^2-a^2}}$ | $\cosh^{-1}\frac xa$ |

- **Parts**: $\int uv'=uv-\int u'v$ (LIATE). Also:

$$\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2}$$

- **Trig**: $\cos^2x=\frac12(1+\cos2x)$ and $2\sin A\cos B=\sin(A+B)+\sin(A-B)$.
- **Partial fractions**: $\frac A{x-a}$; $\frac A{x-a}+\frac B{(x-a)^2}$; $\frac{Bx+C}{x^2+bx+c}$. Divide first if the fraction is improper.
- **Improper integrals**: $\int_1^\infty x^{-p}$ converges iff $p>1$; $\int_0^1x^{-p}$ converges iff $p<1$.
- **Applications**:

$$
\bar x=\tfrac1A\int xy,\quad\bar y=\tfrac1{2A}\int y^2,\quad V=\pi\int y^2,\quad L=\int\sqrt{1+y'^2},\quad S=2\pi\int y\sqrt{1+y'^2},\quad f_{\text{rms}}^2=\tfrac1{b-a}\int f^2
$$

- **Numerical integration**:

$$
T=h\big[\tfrac12(f_0+f_n)+\textstyle\sum f_r\big],\quad S=\tfrac h3\big[f_0+f_n+4\textstyle\sum f_{\text{odd}}+2\sum f_{\text{even}}\big],\quad\tfrac13[4T(h)-T(2h)]=S
$$

### Multiple integrals ([[MATH1054 M11 - Integration IV|M11]])
- Always sketch the region. Inner limits may depend on the outer variable.
- **Polar**: $\mathrm dA=r\,\mathrm dr\,\mathrm d\theta$, so the area of $r=f(\theta)$ is $\frac12\int f^2\,\mathrm d\theta$.

## Block 2: Complex numbers ([[MATH1054 M05 - Complex Numbers I|M05]], [[MATH1054 M22 - Complex Numbers II|M22]])

$$
z=x+\mathrm jy=re^{\mathrm j\theta},\quad\frac{z_1}{z_2}=\frac{z_1z_2^*}{|z_2|^2},\quad e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta,\quad z^{1/n}=r^{1/n}e^{\mathrm j(\theta+2k\pi)/n}
$$

- **Argument by quadrant**: $\alpha$, $\pi-\alpha$, $-(\pi-\alpha)$, $-\alpha$ for Q1–Q4.
- **Complex functions**:
  - $\sin z=\sin x\cosh y+\mathrm j\cos x\sinh y$
  - $\cos z=\cos x\cosh y-\mathrm j\sin x\sinh y$
  - $\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi)$
- **Loci**: $|z-a|=r$ is a circle; $|z-a|=|z-b|$ is a bisector; $|z-a|=k|z-b|$ is a circle of Apollonius.

## Block 3: Differential equations ([[MATH1054 M06 - Differential Equations I|M06]], [[MATH1054 M12 - Differential Equations II|M12]], [[MATH1054 M13 - Differential Equations III|M13]])
| Type | Method |
|---|---|
| $\dot x=f(t)g(x)$ | separate: $\int\frac{\mathrm dx}g=\int f\,\mathrm dt$ |
| $\dot x=F(x/t)$ | $x=vt$, then $t\dot v=F(v)-v$ |
| $f\dot x+g=0$ with $f_t=g_x$ | exact: $F_x=f$, $F_t=g$, $F=C$ |
| $\dot x+Px=Q$ | integrating factor $\mu=e^{\int P}$, then $(\mu x)'=\mu Q$ |
| $a\ddot x+b\dot x+cx=f$ | CF from $am^2+bm+c=0$, PI by undetermined coefficients |

| Roots | CF |
|---|---|
| $m_1\neq m_2$ real | $Ae^{m_1t}+Be^{m_2t}$ |
| $m$ repeated | $(A+Bt)e^{mt}$ |
| $\alpha\pm\mathrm j\beta$ | $e^{\alpha t}(A\cos\beta t+B\sin\beta t)$ |

- **PI trials**: a polynomial gives a full polynomial; $e^{kt}$ gives $\frac{e^{kt}}{P(k)}$; $\cos\omega t$ gives $a\cos\omega t+b\sin\omega t$.
- **Clash**: multiply by $t^s$. Shortcuts: $\frac{te^{kt}}{P'(k)}$ and $\frac{t^2e^{kt}}{P''(k)}$.
- **Damping**: $\ddot x+2\zeta\omega\dot x+\omega^2x=0$. $\zeta<1$ is under-damped, $\zeta=1$ critical, $\zeta>1$ over-damped.

## Block 4: Vectors and matrices ([[MATH1054 M14 - Vectors I|M14]]–[[MATH1054 M18 - Matrices III|M18]])

$$
\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta,\quad|\mathbf a\times\mathbf b|=|\mathbf a||\mathbf b|\sin\theta,\quad[\mathbf a,\mathbf b,\mathbf c]=\det,\quad\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c
$$

- **Moment**: $\mathbf M_{\mathrm A}=\vec{\mathrm{AP}}\times\mathbf F$. **Rigid-body velocity**: $\mathbf v=\boldsymbol\omega\times\vec{\mathrm{AP}}$. **Work**: $W=\mathbf F\cdot\mathbf d$.
- **Line**: $\mathbf r=\mathbf a+t\mathbf d$. **Plane**: $\mathbf r\cdot\mathbf n=d$. **Point–plane distance**: $\frac{|\mathbf n\cdot\mathbf p-d|}{|\mathbf n|}$.
- **Skew-line distance**:

$$d=\frac{|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|}{|\mathbf d_1\times\mathbf d_2|}$$

- **Polar acceleration**: $\ddot{\mathbf r}=(\ddot r-r\dot\theta^2)\hat{\mathbf r}+(2\dot r\dot\theta+r\ddot\theta)\hat{\boldsymbol\theta}$.
- **Matrices**: $(\mathbf{AB})^{\mathrm T}=\mathbf B^{\mathrm T}\mathbf A^{\mathrm T}$, $(\mathbf{AB})^{-1}=\mathbf B^{-1}\mathbf A^{-1}$, $\mathbf A^{-1}=\frac{\operatorname{adj}\mathbf A}{|\mathbf A|}$, $|\mathbf{AB}|=|\mathbf A||\mathbf B|$.
- **Consistency**: $\operatorname{rank}\mathbf A=\operatorname{rank}[\mathbf A|\mathbf b]$. If both equal $n$, the solution is unique; if both are $r<n$, there are $n-r$ free parameters.
- **Eigenvalues**: $|\mathbf A-\lambda\mathbf I|=0$, with $\sum\lambda=\operatorname{tr}\mathbf A$ and $\prod\lambda=|\mathbf A|$.

## Block 5: Series and statistics ([[MATH1054 M20 - Further Calculus II|M20]], [[MATH1054 M24 - Statistics I|M24]], [[MATH1054 M25 - Statistics II|M25]])
- **AP**: $S_n=\frac n2[2a+(n-1)d]$. **GP**: $S_n=\frac{a(1-r^n)}{1-r}$, and $S_\infty=\frac a{1-r}$ for $|r|<1$.
- **Ratio test**: $\lim|a_{k+1}/a_k|<1$ converges. **Radius of convergence**: $R=\lim|c_n/c_{n+1}|$.
- **Maclaurin with remainder**: $f=\sum_{k\le n}\frac{f^{(k)}(0)}{k!}x^k+\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1}$.
- **L'Hôpital**: for $\frac00$, $\lim\frac fg=\lim\frac{f'}{g'}$.
- **Probability**:
  - $P(A\cup B)=P(A)+P(B)-P(A\cap B)$
  - $P(B\mid A)=\frac{P(A\cap B)}{P(A)}$
  - $P(B)=\sum P(B\mid A_i)P(A_i)$
  - $\binom nr=\frac{n!}{r!(n-r)!}$
- **Random variables**: $\mu=\sum xp$ or $\int xf$, and $\sigma^2=E[X^2]-\mu^2$. Median: $F(m)=\frac12$.
- **Exponential**: $F=1-e^{-\lambda x}$, $\mu=\sigma=\frac1\lambda$.
- **Sample statistics**: $\bar x=\frac1n\sum x_i$ and $s^2=\frac1{n-1}\sum(x_i-\bar x)^2$.
- **Binomial**: $P(X=r)=\binom nrp^r(1-p)^{n-r}$, with $\mu=np$ and $\sigma^2=np(1-p)$.
- **Normal**: $Z=\frac{X-\mu}{\sigma}$. $\bar X\sim N(\mu,\sigma^2/n)$, exactly for a normal parent and approximately for $n\ge30$ (CLT).
- **CI**: $\bar x\pm z\frac{\sigma}{\sqrt n}$, with $z=1.645$ (90%), $1.96$ (95%) or $2.58$ (99%).
- **Test**: $Z=\frac{\bar x-\mu_0}{\sigma/\sqrt n}$. At 5%, the critical value is $1.645$ one-tailed and $1.96$ two-tailed.
