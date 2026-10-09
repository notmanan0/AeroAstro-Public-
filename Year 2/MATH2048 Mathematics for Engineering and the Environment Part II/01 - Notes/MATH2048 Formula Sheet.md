---
title: "MATH2048 Formula Sheet"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: formula
aliases: ["MATH2048 formulae"]
tags: [math2048, formula, exam-prep]
status: complete
sources: ["01 - Notes/Topics", "02 - Sources/Lectures & Problem Sheets"]
---

# MATH2048 Formula Sheet

Methods and results by block. Each section links to its topic note, which has the derivations.

## Block 1: ODEs

### Constant coefficients ([[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]])
$$
ay''+by'+cy=0\ \xrightarrow{\ y=e^{\lambda x}\ }\ a\lambda^2+b\lambda+c=0
$$

| Roots | $y$ |
|---|---|
| $\lambda_1\neq\lambda_2$ real | $c_1e^{\lambda_1x}+c_2e^{\lambda_2x}$ |
| $\lambda$ repeated | $(c_1+c_2x)e^{\lambda x}$ |
| $\alpha\pm j\beta$ | $e^{\alpha x}(c_1\cos\beta x+c_2\sin\beta x)$ |

### Euler equations ([[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]])
$$
ax^2y''+bxy'+cy=0\ \xrightarrow{\ y=x^n\ }\ an^2+(b-a)n+c=0;\qquad t=\ln x:\ a\ddot y+(b-a)\dot y+cy=0
$$

| Roots | $y$ |
|---|---|
| $n_1\neq n_2$ | $c_1x^{n_1}+c_2x^{n_2}$ |
| $n$ repeated | $x^n(c_1+c_2\ln x)$ |
| $\alpha\pm j\beta$ | $x^\alpha[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)]$ |

### Inhomogeneous: $y=\text{CF}+\text{PI}$
| $r(x)$ | trial $y_p$ |
|---|---|
| polynomial of degree $n$ | polynomial of degree $n$ |
| $e^{kx}$ | $Ce^{kx}$ |
| $\cos\omega x$ or $\sin\omega x$ | $C\cos\omega x+D\sin\omega x$ |
| products | products of trials |

**Clash rule**: multiply by $x^s$, where $s$ is the multiplicity of the root.
**Shortcut**: $y_p=ue^{kx}$ gives $u''+P'(k)u'+P(k)u=\tilde r$.
**Resonance**: $\ddot y+\omega_0^2y=\cos\omega_0t$ gives $y_p=\dfrac{t}{2\omega_0}\sin\omega_0t$.

### BVPs and eigenproblems ([[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]])
- A BVP has a unique solution iff the homogeneous BVP has only $y\equiv0$ (Fredholm). Otherwise it has none or a one-parameter family.
- For $y''+\lambda y=0$, check $\lambda=-k^2$ ($\cosh,\sinh$), $\lambda=0$ ($c_1x+c_2$) and $\lambda=k^2$ ($\sin,\cos$).

| BCs on $[0,L]$ | $\lambda_n$ | $y_n$ |
|---|---|---|
| D–D | $(n\pi/L)^2$, $n\geq1$ | $\sin\frac{n\pi x}L$ |
| N–N | $(n\pi/L)^2$, $n\geq0$ | $\cos\frac{n\pi x}L$ |
| D–N | $\big(\frac{(2n-1)\pi}{2L}\big)^2$ | $\sin\frac{(2n-1)\pi x}{2L}$ |
| N–D | $\big(\frac{(2n-1)\pi}{2L}\big)^2$ | $\cos\frac{(2n-1)\pi x}{2L}$ |

Orthogonality: $\int_0^Ly_my_n\,dx=0$ for $m\neq n$.

## Block 2: Fourier Series

### Series and Euler formulae ([[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]])
Period $2\ell$:
$$
f=\tfrac12a_0+\sum_{n\ge1}\Big[a_n\cos\tfrac{n\pi x}\ell+b_n\sin\tfrac{n\pi x}\ell\Big],\qquad a_n=\tfrac1\ell\int_{-\ell}^{\ell}f\cos\tfrac{n\pi x}\ell\,dx,\qquad b_n=\tfrac1\ell\int_{-\ell}^{\ell}f\sin\tfrac{n\pi x}\ell\,dx
$$

Orthogonality on $[-\ell,\ell]$, and the values at multiples of $\pi$:
$$
\int\cos\cos=\ell\delta_{mn},\qquad \int\sin\sin=\ell\delta_{mn},\qquad \int\cos\sin=0,\qquad \sin n\pi=0,\qquad \cos n\pi=(-1)^n
$$

### Symmetry and half-range ([[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]])
- Even $f$: $b_n=0$ and $a_n=\frac2\ell\int_0^\ell f\cos\frac{n\pi x}{\ell}\,dx$.
- Odd $f$: $a_n=0$ and $b_n=\frac2\ell\int_0^\ell f\sin\frac{n\pi x}{\ell}\,dx$.
- Half-range on $[0,L]$: the sine series uses $b_n=\frac2L\int_0^Lf\sin\frac{n\pi x}{L}\,dx$; the cosine series uses $a_n=\frac2L\int_0^Lf\cos\frac{n\pi x}{L}\,dx$.
- At a jump the series converges to $\frac12[f(x^-)+f(x^+)]$.

### Complex form and calculus ([[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]])
$$
f=\sum_{-\infty}^\infty c_ne^{jn\pi x/\ell},\qquad c_n=\frac1{2\ell}\int_{-\ell}^{\ell}fe^{-jn\pi x/\ell}dx,\qquad a_n=2\,\mathrm{Re}\,c_n,\qquad b_n=-2\,\mathrm{Im}\,c_n
$$
- Integrating term by term is always allowed.
- Differentiating term by term needs $f$ to be continuous (including across the period ends) with $f'$ piecewise smooth.

### Standard series on $(-\pi,\pi)$
| $f$ | series |
|---|---|
| $x$ | $\sum\frac{2(-1)^{n+1}}n\sin nx$ |
| $\lvert x\rvert$ | $\frac\pi2-\frac4\pi\sum_{\text{odd}}\frac{\cos nx}{n^2}$ |
| $x^2$ | $\frac{\pi^2}3+\sum\frac{4(-1)^n}{n^2}\cos nx$ |

Sums: $\sum\frac1{n^2}=\frac{\pi^2}6$ and $\sum_{\text{odd}}\frac1{n^2}=\frac{\pi^2}8$.

## Block 3: Fourier and Laplace Transforms

### Fourier transform ([[MATH2048 TR1 - Fourier Transforms]])
$$
F(\omega)=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^\infty fe^{-j\omega t}dt,\qquad f=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^\infty Fe^{j\omega t}d\omega,\qquad \mathcal F[f^{(n)}]=(j\omega)^nF,\qquad \mathcal F[f(t-t_0)]=e^{-j\omega t_0}F,\qquad \mathcal F[e^{j\omega_0t}f]=F(\omega-\omega_0)
$$

- Response function: $Y(\omega)=G(\omega)U(\omega)$.
- For $\ddot y+\gamma\dot y+\omega_0^2y=u$: $G=\dfrac1{\omega_0^2-\omega^2+j\gamma\omega}$, which peaks at $\omega^2=\omega_0^2-\gamma^2/2$.

### Laplace transform ([[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]], [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]])
$$
\tilde f=\int_0^\infty fe^{-sx}dx,\qquad \mathcal L[f']=s\tilde f-f(0),\qquad \mathcal L[f'']=s^2\tilde f-sf(0)-f'(0)\qquad\big(\text{needs }fe^{-sx}\to0\big)
$$

| $f$ | $\tilde f$ | | rule | result |
|---|---|---|---|---|
| $1$, $x^n$ | $\frac1s$, $\frac{n!}{s^{n+1}}$ | | first shift | $\mathcal L[e^{-ax}f]=\tilde f(s+a)$ |
| $e^{ax}$ | $\frac1{s-a}$ | | second shift | $\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f$ |
| $\sin ax$, $\cos ax$ | $\frac a{s^2+a^2}$, $\frac s{s^2+a^2}$ | | alternative form | $\mathcal L[f(x)H(x-a)]=e^{-as}\mathcal L[f(x+a)]$ |
| $\sinh ax$, $\cosh ax$ | $\frac a{s^2-a^2}$, $\frac s{s^2-a^2}$ | | multiply by $x$ | $\mathcal L[xf]=-\tilde f'(s)$ |
| $H(x-a)$ | $\frac{e^{-as}}s$ | | integral | $\mathcal L[\int_0^xf]=\tilde f/s$ |
| $\delta(x-a)$, $a>0$ | $e^{-as}$ | | products | $\mathcal L[fg]\neq\tilde f\tilde g$ |

**Partial fractions**:
- $\frac{A}{s-r}$ inverts to $Ae^{rx}$.
- $\frac{A}{(s-r)^k}$ inverts to $A\frac{x^{k-1}}{(k-1)!}e^{rx}$.
- $\frac{B(s+c)+Cb}{(s+c)^2+b^2}$ inverts to $e^{-cx}(B\cos bx+C\sin bx)$.

## Block 4: PDEs

### Classification ([[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]])
For $au_{xx}+2bu_{xy}+cu_{yy}+\dots=0$:
- $b^2-ac>0$: hyperbolic;
- $b^2-ac=0$: parabolic;
- $b^2-ac<0$: elliptic.

D'Alembert: $y=f(x+ct)+g(x-ct)$, with $c=\sqrt{T/\rho}$.

### Separated solutions on $[0,L]$ with $k_n=n\pi/L$ ([[MATH2048 PDE2 - Separation of Variables for the Wave Equation]], [[MATH2048 PDE3 - The Heat Equation]])
| PDE | Dirichlet ends | Neumann ends |
|---|---|---|
| $y_{tt}=c^2y_{xx}$ | $\sum[C_n\cos ck_nt+D_n\sin ck_nt]\sin k_nx$ | $Gt+H+\sum[\dots]\cos k_nx$ |
| $u_t=\kappa^2u_{xx}$ | $\sum C_ne^{-\kappa^2k_n^2t}\sin k_nx$ | $H+\sum C_ne^{-\kappa^2k_n^2t}\cos k_nx$ |
| $u_{tt}+2\kappa u_t=u_{xx}$ ($L=\pi$) | $\sum\sin nx\,e^{-\kappa t}[C_n\sin\omega_nt+D_n\cos\omega_nt]$, with $\omega_n=\sqrt{n^2-\kappa^2}$ | |

Coefficients:
- $C_n=\frac2L\int_0^Lf\sin k_nx\,dx$.
- For the wave equation, $D_n=\frac{2}{ck_nL}\int_0^Lg\sin k_nx\,dx$.

Standard integral: $2\int_0^1x(1-x)\sin n\pi x\,dx=\frac{4[1-(-1)^n]}{(n\pi)^3}$ and $2\int_0^1x(1-x)\cos n\pi x\,dx=-\frac{2[1+(-1)^n]}{(n\pi)^2}$.

### Inhomogeneous problems ([[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]])
- **Source term**: expand $u=\sum T_nX_n$ and $F=\sum F_nX_n$. Each mode then satisfies
$$\dot T_n+\kappa^2k_n^2T_n=F_n,\qquad T_n=e^{-\kappa^2k_n^2t}\Big[C_n+\int e^{\kappa^2k_n^2t}F_n\,dt\Big].$$
- **Inhomogeneous BCs**: subtract $y_P=f_0+(f_1-f_0)x$. The new unknown then satisfies $v_t=\kappa^2v_{xx}-\partial_ty_P$.

### Laplace's equation ([[MATH2048 PDE5 - Laplace's Equation]])
With $X_n=\sin n\pi x$, the other direction gives $Y_n=\sinh n\pi y$ (or $\cosh$). The maximum principle holds.

On a disk: $\phi=\frac12a_0+\sum r^n(a_n\cos n\theta+b_n\sin n\theta)$.

## Block 5: Vector Calculus

### Operators ([[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]], [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]])
$$
\nabla\phi=(\phi_x,\phi_y,\phi_z),\qquad \nabla_{\hat{\mathbf v}}\phi=\hat{\mathbf v}\cdot\nabla\phi,\qquad \nabla\cdot\mathbf F=\sum\partial_iF_i,\qquad \nabla\times\mathbf F=\big(\partial_yF_3-\partial_zF_2,\ \partial_zF_1-\partial_xF_3,\ \partial_xF_2-\partial_yF_1\big)
$$
- Maximum rate of change: $|\nabla\phi|$.
- $\nabla\phi$ is normal to the surfaces $\phi=c$.
- Always zero: $\nabla\times\nabla\phi=\mathbf 0$ and $\nabla\cdot\nabla\times\mathbf F=0$.
- Double curl: $\nabla\times\nabla\times\mathbf F=\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$.

### Integrals ([[MATH2048 VC3 - Line Integrals and Conservative Fields]], [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]])
$$
\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F(\mathbf r(t))\cdot\dot{\mathbf r}\,dt,\qquad \int_A^B\nabla\phi\cdot d\mathbf r=\phi(B)-\phi(A),\qquad d\mathbf S=(\mathbf r_s\times\mathbf r_t)\,ds\,dt,\qquad dA=|\mathbf r_s\times\mathbf r_t|\,ds\,dt
$$

In a simply connected region, $\mathbf F$ is conservative $\iff\nabla\times\mathbf F=\mathbf 0\iff\oint\mathbf F\cdot d\mathbf r=0\iff\mathbf F=\nabla\phi$.

| Surface | $d\mathbf S$ |
|---|---|
| Sphere of radius $a$ | $\hat{\mathbf r}\,a^2\sin\theta\,d\theta\,d\phi$ |
| Cylinder of radius $a$ | $\hat{\boldsymbol\rho}\,a\,d\phi\,dz$ |
| Graph $z=f(x,y)$ | $(-f_x,-f_y,1)\,dx\,dy$ |

### Volumes and theorems ([[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]])
$$
dV_{\text{cyl}}=\rho\,d\rho\,d\phi\,dz,\qquad dV_{\text{sph}}=r^2\sin\theta\,dr\,d\theta\,d\phi,\qquad dV=\Big|\frac{\partial(x,y,z)}{\partial(s,t,u)}\Big|\,ds\,dt\,du
$$
$$
\iiint_V\nabla\cdot\mathbf F\,dV=\mathop{∯}_{\partial V}\mathbf F\cdot d\mathbf S,\qquad \iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_{\partial S}\mathbf F\cdot d\mathbf r,\qquad \iint(F_{2,x}-F_{1,y})\,dA=\oint(F_1\,dx+F_2\,dy)
$$
- Gauss uses the outward normal. Stokes uses the right-hand rule: anticlockwise viewed from the tip of $\mathbf n$.
- $\mathop{∯}\mathbf r\cdot d\mathbf S=3V$.
