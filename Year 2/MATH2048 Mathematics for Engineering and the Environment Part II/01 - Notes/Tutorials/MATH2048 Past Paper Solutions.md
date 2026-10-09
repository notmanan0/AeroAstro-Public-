---
title: "MATH2048 Past Paper Solutions"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: tutorial
stream: "Exam preparation"
tags:
  - math2048
  - tutorial-solutions
  - past-papers
  - exam-prep
sheet: "Semester 1 exams 2023/24, 2024/25, 2025/26 (Sections A and B)"
theory_notes: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]", "[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]", "[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]", "[[MATH2048 PDE3 - The Heat Equation]]", "[[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]", "[[MATH2048 VC3 - Line Integrals and Conservative Fields]]", "[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]", "[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
key_concepts: ["[[Laplace Transform Properties and Proofs]]", "[[Separation of Variables]]", "[[Conservative Vector Fields]]", "[[Divergence Theorem]]", "[[Jacobian and Volume Elements]]"]
status: complete
sources: ["03 - Exams & Past Papers/MATH2048-202324-01-MATH2048W1.pdf", "03 - Exams & Past Papers/MATH2048-202425-01-MATH2048W1.pdf", "03 - Exams & Past Papers/MATH2048-202526-01-MATH2048W1.pdf"]
---

# MATH2048 Past Paper Solutions

> [!abstract] Overview
> All three papers include official solutions. Every answer below was also **re-derived independently and checked in SymPy** (`pp_check.py`). It agrees with the official answers throughout.
>
> The Section C statistics questions (Civil Engineering only) are skipped.
>
> **Format**: 100 minutes, open book, formula sheet FS/MATH2048. You answer **A1, A2, B1 and B2**, worth 20, 25, 15 and 20 marks.

> [!tip] What gets examined, year after year
> | | 2023/24 | 2024/25 | 2025/26 |
> |---|---|---|---|
> | **A1(a)** proof from the definition | $\mathcal L[f']=s\tilde f-f(0)$ | $\mathcal L[\delta(x-a)]=e^{-as}$ | second shift theorem |
> | **A1(b)** Laplace IVP | $y''-y'-2y=e^tH(t-1)$ | $y'+2=2\sum\delta(t-n)$ | $y''+2y'+2y=\delta(x-13)$ |
> | **A2** PDE by separation | heat, Neumann, $\cos^3x$ | forced wave, Neumann | **damped** wave, Dirichlet |
> | **B1** fields and line integrals | grad, max rate, Laplacian, conservative line integral | div/curl, potential, line integral | not conservative + line integral |
> | **B2** surfaces and volumes | hemisphere $d\mathbf A$, flux, Gauss → volume | Jacobian, volume of a spherical wedge | Gauss + Jacobian + shifted domain |
>
> **Every year**: prove one Laplace property, solve an IVP with $H$ or $\delta$ using both shift theorems, solve an eigenproblem with the three cases, and fit initial conditions by orthogonality.

---

# 2023/24

## A1 (20 marks)
### (a) Prove $\mathcal L[f']=s\tilde f(s)-f(0)$ [5]
From the definition, integrate by parts with $u=e^{-sx}$ and $dv=f'\,dx$:
$$
\mathcal L[f']=\int_0^\infty f'(x)e^{-sx}dx=\Big[f(x)e^{-sx}\Big]_0^\infty+s\int_0^\infty f(x)e^{-sx}dx=\lim_{x\to\infty}f(x)e^{-sx}-f(0)+s\tilde f(s).
$$
**Condition**: $\lim_{x\to\infty}f(x)e^{-sx}=0$. This holds whenever $\mathcal L[f]$ exists, e.g. if $|f|\leq Ke^{ax}$ and $\mathrm{Re}\,s>a$. Then $\mathcal L[f']=s\tilde f-f(0)$ ∎.

### (b)(i) Show $\tilde y=-\frac e2\frac{e^{-s}}{s-1}+\frac e6\frac{e^{-s}}{s+1}+\frac e3\frac{e^{-s}}{s-2}$ [10]
**Rewrite the source.** $e^tH(t-1)=e\cdot e^{t-1}H(t-1)$. Now use:
- the second shift theorem, $\mathcal L[f(t-a)H(t-a)]=e^{-as}\tilde f(s)$, with $f=e^t$ and $\tilde f=\frac1{s-1}$ (both from the formula sheet);
- the derivative rules with $y(0)=y'(0)=0$.

**Transform.**
$$
(s^2-s-2)\tilde y=\frac{e\,e^{-s}}{s-1}\quad\Longrightarrow\quad\tilde y=\frac{e\,e^{-s}}{(s-1)(s+1)(s-2)} .
$$

**Partial fractions** (cover-up at $s=1,-1,2$):
$$
\frac{1}{(s-1)(s+1)(s-2)}=\frac{1/[(2)(-1)]}{s-1}+\frac{1/[(-2)(-3)]}{s+1}+\frac{1/[(1)(3)]}{s-2}=-\frac{1}{2(s-1)}+\frac1{6(s+1)}+\frac1{3(s-2)} .
$$
Multiplying through by $e\,e^{-s}$ gives the stated result ✔.

### (b)(ii) Invert [5]
Use $\mathcal L^{-1}\big[e^{-s}\tfrac1{s-\alpha}\big]=e^{\alpha(t-1)}H(t-1)$:
$$
y=H(t-1)\Big[-\tfrac e2e^{t-1}+\tfrac e6e^{-(t-1)}+\tfrac e3e^{2(t-1)}\Big]=H(t-1)\Big[-\tfrac12e^{t}+\tfrac16e^{2-t}+\tfrac13e^{2t-1}\Big].
$$
**Check**: at $t=1^+$ the bracket is $e\big(-\frac12+\frac16+\frac13\big)=0$, so $y$ is continuous ✔. SymPy ✔.

## A2 (25 marks): $u_t=\frac14u_{xx}$ on $[0,\pi]$, $u_x(0,t)=u_x(\pi,t)=0$, $u(x,0)=\cos^3x$
**(a) Separate [5].** Substitute $u=XT$:
$$XT'=\tfrac14X''T\ \Longrightarrow\ \frac{4T'}{T}=\frac{X''}{X}=\lambda .$$
So $X''-\lambda X=0$ and $T'-\frac\lambda4T=0$.

**(b) Eigenproblem [10].** The BCs become $X'(0)=X'(\pi)=0$.
- $\lambda=k^2>0$: $X=ae^{kx}+be^{-kx}$. $X'(0)=0$ gives $a=b$, then $X'(\pi)=ka(e^{k\pi}-e^{-k\pi})=0$ gives $a=0$. Trivial.
- $\lambda=0$: $X=A_0+B_0x$ and $X'=B_0=0$, so $X_0=A_0$ is non-trivial.
- $\lambda=-k^2<0$: $X=A\cos kx+B\sin kx$. $X'(0)=kB=0$, then $X'(\pi)=-kA\sin k\pi=0$, so $k=n$.

$$X_n=\cos nx,\qquad\lambda_n=-n^2,\qquad n=0,1,2,\dots$$

**(c) Time equation [5].** $T_n'=-\frac{n^2}{4}T_n$, so $\int\frac{dT_n}{T_n}=-\frac{n^2}4\int dt$ and
$$T_n=C_ne^{-n^2t/4}.$$

**(d) Fit the initial condition [5].** $u=\sum_{n\geq0}A_ne^{-n^2t/4}\cos nx$. Using the hint's identities,
$$\cos^3x=\cos x\cdot\tfrac12(1+\cos2x)=\tfrac12\cos x+\tfrac14(\cos3x+\cos x)=\tfrac34\cos x+\tfrac14\cos3x .$$
By orthogonality $A_1=\frac34$, $A_3=\frac14$, and all other $A_n=0$:
$$\boxed{u=\tfrac34e^{-t/4}\cos x+\tfrac14e^{-9t/4}\cos3x}\ ✔$$
SymPy confirms the PDE residual is $0$ and both BCs hold.

## B1 (15 marks)
### (a) $\phi=\sin(yz)+x^2y^2+z$ at $P(1,2,0)$
**(i) Gradient.** $\nabla\phi=\big(2xy^2,\ z\cos yz+2x^2y,\ y\cos yz+1\big)$. At $P$ this is $(8,4,3)$.

**(ii) Maximum rate of change.** $|\nabla\phi|=\sqrt{64+16+9}=\sqrt{89}\approx9.43$.

**(iii) Laplacian.**
$$\nabla^2\phi=2y^2+\big(2x^2-z^2\sin yz\big)+\big(-y^2\sin yz\big)=2(x^2+y^2)-(y^2+z^2)\sin yz .$$

### (b) $\mathbf G=z^2\,\mathbf i+2y\,\mathbf j+2xz\,\mathbf k$ along $\mathbf r=(t^2,e^t,t)$
**(i) Line integral.** On the curve $\mathbf G=(t^2,\ 2e^t,\ 2t^3)$ and $\dot{\mathbf r}=(2t,\ e^t,\ 1)$. So
$$\int_0^1\big(2t^3+2e^{2t}+2t^3\big)dt=\Big[t^4+e^{2t}\Big]_0^1=\boxed{e^2}.$$

**(ii) Curl.** $\nabla\times\mathbf G=(0-0,\ 2z-2z,\ 0-0)=\mathbf 0$, and $\mathbb R^3$ is simply connected. So $\mathbf G$ is conservative, and the integral depends only on the endpoints.

Indeed $\mathbf G=\nabla(xz^2+y^2)$, and $\phi(1,e,1)-\phi(0,1,0)=(1+e^2)-1=e^2$ ✔.

## B2 (20 marks): hemisphere $\mathbf r=(\sin s\cos t,\ \sin s\sin t,\ \cos s)$, $0\leq s\leq\pi/2$
**(a) Tangent vectors.**
- $\mathbf r_s=(\cos s\cos t,\ \cos s\sin t,\ -\sin s)$
- $\mathbf r_t=(-\sin s\sin t,\ \sin s\cos t,\ 0)$

**(b) Vector area element.** Expanding $\mathbf r_s\times\mathbf r_t$:
- $\mathbf i$: $0+\sin^2s\cos t$
- $\mathbf j$: $\sin^2s\sin t$
- $\mathbf k$: $\cos s\sin s(\cos^2t+\sin^2t)=\sin s\cos s$

So $d\mathbf A=\big(\sin^2s\cos t,\ \sin^2s\sin t,\ \sin s\cos s\big)\,ds\,dt$ ✔. This points outward.

**(c) Flux of $\mathbf F=3z\,\mathbf k$.** $\mathbf F\cdot d\mathbf A=3\cos s\cdot\sin s\cos s$, so
$$\int_0^{2\pi}\!\!\int_0^{\pi/2}3\cos^2s\sin s\,ds\,dt=2\pi\Big[-\cos^3s\Big]_0^{\pi/2}=2\pi\ ✔$$

**(d) Base disc.** On $z=0$, $\mathbf F=\mathbf 0$, so the flux is $0$.

**(e) Enclosed volume.** $\nabla\cdot\mathbf F=3$. Gauss on the closed surface (hemisphere plus disc) gives $3V=2\pi+0$, so $V=\frac{2\pi}3$. This is half of $\frac43\pi$ ✔.

---

# 2024/25

## A1 (20 marks)
### (a) $\mathcal L[\delta(x-a)]=e^{-as}$ for $a>0$ [4]
$$\mathcal L[\delta(x-a)]=\int_0^\infty\delta(x-a)e^{-sx}dx=e^{-sa}$$
This uses the sifting property $\int\delta(x-a)f\,dx=f(a)$, which **requires $a$ to lie inside the integration range** $(0,\infty)$. If $a<0$, the spike is outside $[0,\infty)$ and the integral is $0$. That is why $a>0$ is needed.

### (b) $y'+2=2\sum_{n\geq1}\delta(t-n)$, $y(0)=2$
**(i) [7]** Use $\mathcal L[y']=s\tilde y-2$, $\mathcal L[1]=\frac1s$ and $\mathcal L[\delta(t-n)]=e^{-ns}$:
$$s\tilde y-2+\frac2s=2\sum e^{-ns}\ \Longrightarrow\ \tilde y=2\Big[\frac1s-\frac1{s^2}+\sum_{n\geq1}\frac{e^{-ns}}{s}\Big].$$

**(ii) [5]** Invert term by term: $\frac1s\to1$, $\frac1{s^2}\to t$ and $\frac{e^{-ns}}s\to H(t-n)$. So
$$\boxed{y=2(1-t)+2\sum_{n\geq1}H(t-n)}$$

**(iii) Sketch [4].** On $n<t<n+1$ the solution is $y=2(n+1)-2t$: a line of slope $-2$ from $(n,2)$ down to $(n+1,0)$. Each kick adds $+2$, which produces a **sawtooth**.

![[m2048_pp_2425_a1_sawtooth.png|600]]

## A2 (25 marks): $u_{tt}=u_{xx}+\cos x$ on $[0,\pi]$, Neumann ends, $u(x,0)=\cos x+\cos3x$, $u_t(x,0)=0$
**(a) Homogeneous case [7].** Separating gives $\frac{T''}T=\frac{X''}X=\lambda$. With $X'(0)=X'(\pi)=0$, the three cases (exactly as in 2023/24 A2) give
$$X_0=A_0,\qquad X_n=A_n\cos nx .$$

**(b) Forced problem [13].**
- **Expand the source.** $F=\cos x$ is already an eigenfunction, so $F_1=1$ and all other $F_k=0$. No integrals are needed.
- **Expand the solution.** Substitute $u=\sum X_nT_n$. Using $X_n''=-n^2X_n$ and orthogonality:

| Mode | ODE | Solution |
|---|---|---|
| $n=0$ | $T_0''=0$ | $T_0=A_0+B_0t$ |
| $n=1$ | $T_1''+T_1=1$ | $T_1=A_1\cos t+B_1\sin t+1$ (the PI $1$ comes from undetermined coefficients) |
| $n\geq2$ | $T_n''+n^2T_n=0$ | $T_n=A_n\cos nt+B_n\sin nt$ |

**(c) Fit the initial data [5].**
- $u_t(x,0)=B_0+\sum nB_n\cos nx=0$, so every $B_n=0$.
- $u(x,0)=A_0+(A_1+1)\cos x+\sum_{n\geq2}A_n\cos nx=\cos x+\cos3x$. So $A_1=0$, $A_3=1$, and all others vanish.

$$\boxed{u=\cos x+\cos3x\cos3t}\ ✔$$

**Check**: $u_{tt}=-9\cos3x\cos3t$ and $u_{xx}+\cos x=-\cos x-9\cos3x\cos3t+\cos x$. These are equal ✔.

Note that the $\cos x$ mode sits at its **static equilibrium**, because the forcing exactly balances the stiffness: $-1\cdot\cos x+\cos x=0$.

## B1 (15 marks)
### (a) $\mathbf F=\sin(y^2)\,\mathbf i+(1+e^{2z})\,\mathbf j+x^2\,\mathbf k$ at the origin
**(i)** The gradient of a vector field is **not defined** in this course (grad acts on scalars).

**(ii)** $\nabla\cdot\mathbf F=0+0+0=0$.

**(iii)**
$$\nabla\times\mathbf F=\big(0-2e^{2z}\big)\,\mathbf i+\big(0-2x\big)\,\mathbf j+\big(0-2y\cos y^2\big)\,\mathbf k,$$
which at the origin is $(-2,\,0,\,0)$.

### (b) A potential with $\nabla\phi=-\mathbf G$
$\mathbf G=(y\cos xy+ze^{xz},\ x\cos xy,\ xe^{xz})$. Start with the simplest component:
1. $\phi_z=-xe^{xz}$ gives $\phi=-e^{xz}+f(x,y)$.
2. $\phi_y=f_y=-x\cos xy$ gives $f=-\sin xy+g(x)$.
3. $\phi_x=-ze^{xz}-y\cos xy+g'(x)=-G_1$, so $g'=0$.

$$\phi=-e^{xz}-\sin xy\ (+\text{const})$$

### (c) Line integral from $(0,0,0)$ to $(1,0,1)$
Along $\mathbf r=(t,0,t)$, $\mathbf G\cdot\dot{\mathbf r}=G_1+G_3=te^{t^2}+te^{t^2}=2te^{t^2}$. So
$$\int_0^1 2te^{t^2}\,dt=e-1 .$$
Check with the potential: $\phi(\mathbf 0)-\phi(1,0,1)=-1-(-e)=e-1$ ✔.

### (d) Is $\mathbf H=\mathbf G+\sin(xyz)\,\mathbf k$ path independent?
$\nabla\times\mathbf H=\nabla\times\big(\sin(xyz)\mathbf k\big)=(xz\cos xyz,\ -yz\cos xyz,\ 0)\neq\mathbf 0$. So $\mathbf H$ is **not** conservative, and its line integral depends on the path.

## B2 (20 marks): spherical wedge $0\leq r\leq R$, $0\leq\theta\leq\Theta$, $0\leq\phi\leq\Phi$
**(a) Jacobian [7].** $J=r^2\sin\theta$. The full cofactor expansion is in [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem|VC5]], and SymPy `det` ✔.

**(b) Volume [7].**
$$V=\int_0^\Phi\!\!\int_0^\Theta\!\!\int_0^Rr^2\sin\theta\,dr\,d\theta\,d\phi=\Phi\,[1-\cos\Theta]\,\frac{R^3}{3}=\boxed{\frac{\Phi R^3}{3}(1-\cos\Theta)}$$

**(c) Sketch of $V(\Theta,2\pi)=\frac{2\pi R^3}{3}(1-\cos\Theta)$ [6].** Features to show:
- $V(0)=0$, and the curve starts **flat** because $V'\propto\sin\Theta$ is $0$ there.
- The steepest point is at $\Theta=\pi/2$, where the curve passes through the hemisphere value $\frac{2\pi R^3}3$.
- It rises to the full sphere, $\frac{4\pi R^3}{3}$, at $\Theta=\pi$, and is flat again there.

![[m2048_pp_2425_b2_volume.png|560]]

---

# 2025/26

## A1 (20 marks)
### (a) Prove the second shift theorem [5]
See the boxed proof in [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem|TR3]]:
$$\int_a^\infty f(x-a)e^{-sx}dx\ \xrightarrow{\ \tau=x-a\ }\ e^{-as}\int_0^\infty f(\tau)e^{-s\tau}d\tau=e^{-as}\tilde f(s).$$

### (b) $y''+2y'+2y=\delta(x-13)$, $y(0)=y'(0)=0$
**(i) [7]** $(s^2+2s+2)\tilde y=e^{-13s}$, so
$$\tilde y=\frac{e^{-13s}}{(s+1)^2+1}.$$

**(ii) [8]**
- Formula sheet: $\mathcal L[\sin x]=\frac{1}{s^2+1}$.
- First shift theorem: $\mathcal L[e^{-x}\sin x]=\frac1{(s+1)^2+1}$.
- Second shift theorem with $c=13$:

$$\boxed{y=H(x-13)\,e^{-(x-13)}\sin(x-13)}$$

## A2 (25 marks): damped string $u_{tt}+2\kappa u_t=u_{xx}$, $0<\kappa<1$, $u(t,0)=u(t,\pi)=0$, $u_t(0,x)=0$
**(a) Separate [5].** Substitute $u=XT$ and divide by $XT$:
$$\frac{\ddot T+2\kappa\dot T}{T}=\frac{X''}{X}=\lambda .$$
So $X''-\lambda X=0$ and $\ddot T+2\kappa\dot T-\lambda T=0$ ✔.

**(b) Eigenproblem [9].** Dirichlet BCs, $X(0)=X(\pi)=0$:
- $\lambda=\mu^2>0$: $X=Ae^{\mu x}+Be^{-\mu x}$. The BCs force $A=B=0$.
- $\lambda=0$: $X=Ax+B$. The BCs force $A=B=0$.
- $\lambda=-\mu^2<0$: $X=A\sin\mu x+B\cos\mu x$. $B=0$, then $\sin\mu\pi=0$, so $\mu=n$.

$$X_n=\sin nx,\qquad\lambda_n=-n^2,\qquad n\geq1 .$$

**(c) Time equation and general solution [7].** The time ODE is $\ddot T_n+2\kappa\dot T_n+n^2T_n=0$.
- The auxiliary equation $m^2+2\kappa m+n^2=0$ gives $m=-\kappa\pm j\sqrt{n^2-\kappa^2}$. These are complex because $n\geq1>\kappa$: every mode is **under-damped**.
- So $T_n=e^{-\kappa t}\big[C_n\sin\omega_nt+D_n\cos\omega_nt\big]$ with $\omega_n=\sqrt{n^2-\kappa^2}$.
- Apply $u_t(0,x)=0$: $\dot T_n(0)=\omega_nC_n-\kappa D_n=0$, so $D_n=C_n\frac{\omega_n}{\kappa}=C_n\sqrt{(n/\kappa)^2-1}$.

$$u=\sum_{n\geq1}C_n\sin(nx)\,e^{-\kappa t}\Big[\sin\omega_nt+\sqrt{(n/\kappa)^2-1}\,\cos\omega_nt\Big]\ ✔$$
SymPy confirms that the residual is $0$ for general $n$ and $\kappa$, and that $u_t(0)=0$.

**(d) Second initial condition [4].** $u(0,x)=\sum C_n\sqrt{(n/\kappa)^2-1}\,\sin nx=\sin x$. By orthogonality, only $n=1$ survives:
$$C_1=\frac1{\sqrt{1/\kappa^2-1}}=\frac{\kappa}{\sqrt{1-\kappa^2}},\qquad C_n=0\ (n\geq2).$$
$$\boxed{u=\sin x\;e^{-\kappa t}\Big[\cos\sqrt{1-\kappa^2}\,t+\frac{\kappa}{\sqrt{1-\kappa^2}}\sin\sqrt{1-\kappa^2}\,t\Big]}$$

![[m2048_pp_2526_a2_damped_string.png|640]]

> [!note] Connection to SESA2027
> Each mode is exactly a damped oscillator with $\zeta_n=\kappa/n$. The higher modes are *less* damped relative to their frequency. See [[Damping Ratio and Natural Frequency]].

## B1 (15 marks): $\mathbf F=xyz\,\mathbf i+z^2\mathbf j+y^2\mathbf k$
**(a) Not conservative [6].**
$$\nabla\times\mathbf F=\big(2y-2z\big)\,\mathbf i+\big(xy-0\big)\,\mathbf j+\big(0-xz\big)\,\mathbf k=(2y-2z,\ xy,\ -xz).$$
This is not identically zero; for example, at $(1,1,0)$ it is $(2,1,0)$. So $\mathbf F$ is not conservative.

**(b) Line integral along $\mathbf r=\big(3(t+1),\,t,\,t^2\big)$, $0\leq t\leq1$ [9].**
- $\dot{\mathbf r}=(3,1,2t)$.
- On the curve, $\mathbf F=\big(3(t+1)\cdot t\cdot t^2,\ t^4,\ t^2\big)=\big(3t^3(t+1),\ t^4,\ t^2\big)$.
- $\mathbf F\cdot\dot{\mathbf r}=9t^4+9t^3+t^4+2t^3=10t^4+11t^3$.

$$\int_0^1(10t^4+11t^3)\,dt=2+\frac{11}{4}=\boxed{\frac{19}{4}}\ ✔$$

## B2 (20 marks): unit upper hemisphere, $\phi=x^2+y^2+z^3$
**(a)** $\mathbf F=\nabla\phi=(2x,\ 2y,\ 3z^2)$.

**(b)** $\nabla\cdot\mathbf F=4+6z$. By Gauss, $\oiint\mathbf F\cdot d\mathbf S=\iiint_V(4+6z)\,dV$.

**(c)** $dV=r^2\sin\theta\,dr\,d\theta\,d\phi$ (Jacobian, as in 2024/25 B2a).

**(d) Evaluate.**
$$I=\int_0^{2\pi}\!\!\int_0^{\pi/2}\!\!\int_0^1(4+6r\cos\theta)\,r^2\sin\theta\,dr\,d\theta\,d\phi=2\pi\Big[4\cdot\tfrac13\cdot1+6\cdot\tfrac14\cdot\tfrac12\Big]=2\pi\Big(\tfrac43+\tfrac34\Big)=\boxed{\frac{25\pi}{6}}$$
The two pieces use $\int_0^{\pi/2}\sin\theta\,d\theta=1$ and $\int_0^{\pi/2}\cos\theta\sin\theta\,d\theta=\tfrac12$.

*Cross-check*: the flux through the curved surface alone, computed by explicit parametrisation, is also $\frac{25\pi}6$. The base disc contributes $\mathbf F\cdot(-\mathbf k)=-3z^2=0$ at $z=0$ ✔.

**(e) Hemisphere centred at $(0,0,1)$ [4].** Shift $z=z'+1$; the Jacobian of this shift is $1$. Then $4+6z=(4+6z')+6$, so
$$I'=I+6\,\mathrm{Vol}=\frac{25\pi}{6}+6\cdot\frac{2\pi}{3}=\boxed{\frac{49\pi}{6}}\ ✔$$

---

## Exam technique (from the mark schemes)
- **"Identify results explicitly"**: write *"by the second shift theorem, $\mathcal L[f(t-a)H(t-a)]=e^{-as}\tilde f(s)$, with $f=\dots$"*. The mark schemes award marks for naming the result.
- **Eigenproblems** are marked as 1 mark for the separated ODEs, 1 for the BCs, 1 for the trivial cases, and 2 for each non-trivial case. **Always** show all three cases, including $\lambda=0$.
- **Use orthogonality** to match initial data. You do not need Euler integrals when the data is already a finite sum of eigenfunctions ($\cos^3x$, $\sin x$, $\cos x+\cos3x$).
- **B questions** reward a physical check: half the volume of a ball, a conservative potential giving the same line integral, and so on.

## Sources
- MATH2048 W1 papers and official solutions, 2023/24–2025/26. Independent verification in SymPy (`pp_check.py`, session scratchpad).
