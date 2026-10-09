---
title: "SESA3029 Example Sheet 2 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Sections 3–4: method of characteristics and linearised supersonic/subsonic theory"
tags: [sesa3029, tutorial-solutions, example-sheet, method-of-characteristics, riemann-invariant, ackeret, prandtl-glauert]
sheet: "Example Sheet 2"
theory_notes: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
status: complete
sources: ["03 - Exams & Past Papers/ExamplesSheet2.pdf"]
---

# SESA3029 Example Sheet 2 - Solutions

> [!abstract] Sheet info
> Six questions from **Sections 3–4**, which have **not been lectured yet**:
> - Q1–Q3: the method of characteristics (MoC), in Weeks 4–5;
> - Q4–Q6: Ackeret and Prandtl–Glauert linear theory, in Weeks 7–8.
>
> So that the solutions stand alone, each section first derives the result it needs from Week 3 material (Mach waves and the Prandtl–Meyer relation). Revisit these solutions once the lectures arrive and add transcript references. All numbers are verified in Python. $\gamma=1.4$.

> [!warning] Not yet lectured
> Treat the derivations below as a preview. The lecturer's notation and sign conventions for $C^\pm$ and $K^\pm$ may differ. The conventions here follow Anderson §11.11–11.12 and §13.

---

## Q1. Eigenvalues and left eigenvectors

$$
A=\begin{pmatrix}2&1\\3&0\end{pmatrix}.
$$

**Eigenvalues.** Solve the characteristic equation:

$$
\det(A-\lambda I)=(2-\lambda)(0-\lambda)-3=\lambda^2-2\lambda-3=(\lambda-3)(\lambda+1)=0
\ \Rightarrow\
\boxed{\lambda_1=-1,\ \lambda_2=3}.
$$

**Left eigenvectors** are rows $\mathbf l$ with $\mathbf lA=\lambda\mathbf l$, i.e. $\mathbf l(A-\lambda I)=\mathbf 0$.

- $\lambda_1=-1$: $(l_1,l_2)\begin{pmatrix}3&1\\3&1\end{pmatrix}=(3l_1+3l_2,\ l_1+l_2)=\mathbf0$, so $l_2=-l_1$ and $\boxed{L_1=(1,\,-1)}$.
- $\lambda_2=3$: $(l_1,l_2)\begin{pmatrix}-1&1\\3&-3\end{pmatrix}=(-l_1+3l_2,\ l_1-3l_2)=\mathbf0$, so $l_1=3l_2$ and $\boxed{L_2=(3,\,1)}$.

**Left-eigenvector matrix** (rows $L_1$, $L_2$) and its inverse $S$ (the right-eigenvector matrix, $\det S^{-1}=1+3=4$):

$$
S^{-1}=\begin{pmatrix}1&-1\\3&1\end{pmatrix},
\qquad
S=\frac14\begin{pmatrix}1&1\\-3&1\end{pmatrix}.
$$

**Checks**, with $\Lambda=\mathrm{diag}(-1,3)$:

$$
S^{-1}A=\begin{pmatrix}1&-1\\3&1\end{pmatrix}\begin{pmatrix}2&1\\3&0\end{pmatrix}=\begin{pmatrix}-1&1\\9&3\end{pmatrix},
\qquad
\Lambda S^{-1}=\begin{pmatrix}-1\cdot1&-1\cdot(-1)\\3\cdot3&3\cdot1\end{pmatrix}=\begin{pmatrix}-1&1\\9&3\end{pmatrix}\ ✓
$$

$$
AS=\frac14\begin{pmatrix}2-3&2+1\\3&3\end{pmatrix}=\frac14\begin{pmatrix}-1&3\\3&3\end{pmatrix},
\qquad
S\Lambda=\frac14\begin{pmatrix}-1&3\\3&3\end{pmatrix}\ ✓
$$

> [!tip] Why this matters for MoC
> A hyperbolic system $\partial_t\mathbf q+A\,\partial_x\mathbf q=0$ multiplied by $S^{-1}$ decouples into $\partial_t w_i+\lambda_i\,\partial_xw_i=0$, with $\mathbf w=S^{-1}\mathbf q$. Each $w_i$ is constant along a curve of slope $\mathrm dx/\mathrm dt=\lambda_i$. Those curves are the **characteristics**, and the $w_i$ are the **Riemann invariants**. In steady supersonic flow, $x$ plays the role of time, the characteristic slopes are $\tan(\theta\pm\mu)$, and the invariants are $\theta\mp\nu$ (Q2). See also [[Eigenvalues and Eigenvectors]].

## Q2. Characteristics and Riemann invariants

**Theory needed** (derived from [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]). Through every point of a supersonic flow pass two Mach lines:

- $C^+$, "left-running", inclined at $\theta+\mu$;
- $C^-$, "right-running", inclined at $\theta-\mu$.

The flow changes only by crossing infinitesimal Mach waves, and across each one $\mathrm d\nu=\pm\mathrm d\theta$ (W03 §5).

A left-running wave originates on a **lower** wall. A lower wall turning **up** ($\mathrm d\theta>0$) is a compression ($\mathrm d\nu<0$), so across a $C^+$ wave $\mathrm d\theta=-\mathrm d\nu$, i.e. $\mathrm d(\theta+\nu)=0$. A point travelling along a $C^-$ line crosses only $C^+$ waves. Hence:

$$
\boxed{K^-=\theta+\nu=\text{const along }C^-},
\qquad
\boxed{K^+=\theta-\nu=\text{const along }C^+}.
$$

At a point R where a $C^-$ and a $C^+$ cross, both invariants are known, so

$$
\theta_R=\tfrac12(K^-+K^+),
\qquad
\nu_R=\tfrac12(K^--K^+).
$$

**(a)–(b) Sketch and labels.** P lies upstream of R on the $C^-$ through R, so the segment PR is a $C^-$ line carrying $K^-_P=\theta_P+\nu_P$. Q lies upstream of R on the $C^+$ through R, so QR is a $C^+$ line carrying $K^+_Q=\theta_Q-\nu_Q$. P lies **above** Q, because the $C^-$ runs downwards to R.

**(c) Zones.**

- **Domain of dependence** of R: the region **upstream**, between the $C^+$ and $C^-$ through R, i.e. the wedge containing P and Q. Only data there can affect R.
- **Zone (range) of influence** of R: the wedge **downstream** between the two characteristics leaving R. R can affect only points there.

**(d) Numbers.** IFT: $\nu(3)=49.757^\circ$ and $\nu(3.2)=53.470^\circ$.

$$
K^-=\theta_P+\nu_P=10+49.757=59.757^\circ,
\qquad
K^+=\theta_Q-\nu_Q=12-53.470=-41.470^\circ,
$$

$$
\theta_R=\tfrac12(59.757-41.470)=\boxed{9.14^\circ},
\qquad
\nu_R=\tfrac12(59.757+41.470)=50.614^\circ
\ \Rightarrow\
\boxed{M_R=3.045}.
$$

The sheet gives 3.04 and 9.15°; the difference is table rounding ✓.

## Q3. Flow in a symmetric 2D duct

![[at_es2_moc_net.png|900]]

Data: A at $(0,0.75)$ with $M_A=1.2$, $\theta_A=4.28^\circ$; B at $(0,0.25)$ with $M_B=1.2$, $\theta_B=1.43^\circ$. Wall $y=1+0.1x+0.5x^2$. Then $\nu(1.2)=3.558^\circ$ and $\mu(1.2)=56.44^\circ$.

**Point C (wall), on the $C^+$ through A.**

1. AC is straight with slope $\tan(\theta_A+\mu_A)=\tan60.72^\circ=1.7836$, so $y=0.75+1.7836x$.
2. Intersect with the wall: $1+0.1x+0.5x^2=0.75+1.7836x$, i.e. $0.5x^2-1.6836x+0.25=0$.
3. Smaller root: $x_C=1.6836-\sqrt{1.6836^2-0.5}=0.1557$, so $y_C=1.0277$.
4. Wall slope: $\theta_C=\tan^{-1}(\mathrm dy/\mathrm dx)=\tan^{-1}(0.1+x_C)=\boxed{14.34^\circ}$.
5. $K^+$ is constant along AC: $\theta_C-\nu_C=\theta_A-\nu_A$, so $\nu_C=14.342-4.28+3.558=13.621^\circ$ and $\boxed{M_C=1.558}$.

**Point D (interior)**: the $C^-$ from A meets the $C^+$ from B.

$$
K^-_A=4.28+3.558=7.838^\circ,
\qquad
K^+_B=1.43-3.558=-2.128^\circ,
$$

$$
\theta_D=2.855^\circ,
\qquad
\nu_D=4.983^\circ
\ \Rightarrow\
\boxed{M_D=1.256}.
$$

**Point F (interior)**: the $C^-$ from C meets the $C^+$ through B and D, which carries the same $K^+=-2.128^\circ$.

$$
K^-_C=\theta_C+\nu_C=27.963^\circ,
\qquad
\theta_F=12.92^\circ,
\qquad
\nu_F=15.046^\circ
\ \Rightarrow\
\boxed{M_F=1.606}.
$$

*(Point E on the axis, for completeness:* $\theta_E=0$, so $\nu_E=K^-_B=4.988^\circ$ and $M_E=1.256$.)

The sheet gives 14.34°, 1.558, 1.256 and 1.606 ✓.

## Q4. Flat plate by Ackeret theory

**Theory needed: the linearised pressure coefficient.** Across a weak wave turning the flow by a small $\theta$ (positive = into the flow):

- Prandtl–Meyer (W03 §5): $\mathrm d\theta=-\sqrt{M^2-1}\,\mathrm dV/V$, with the minus sign for compression.
- Euler: $\mathrm dp=-\rho V\,\mathrm dV$, so $\mathrm dp/p=-\gamma M^2\,\mathrm dV/V$.

Eliminate $\mathrm dV/V$:

$$
\frac{\mathrm dp}{p}=\frac{\gamma M^2}{\sqrt{M^2-1}}\,\theta
\quad\Longrightarrow\quad
C_p=\frac{p-p_\infty}{\frac12\gamma p_\infty M^2}=\boxed{\frac{2\theta}{\sqrt{M^2-1}}}.
$$

On the plate, the lower surface has $\theta=+\alpha$ and the upper surface $\theta=-\alpha$, so $C_{p,l}-C_{p,u}=4\alpha/\beta$ with $\beta=\sqrt{M^2-1}$. The force is normal to the plate. To first order in $\alpha$:

$$
C_l=\frac{4\alpha}{\beta},
\qquad
C_d=C_l\,\alpha=\frac{4\alpha^2}{\beta}.
$$

**Numbers:** $M=2.7$, $\beta=2.508$, $\alpha=0.17453$ rad, $q_\infty=\tfrac12\gamma pM^2=0.7\times20\,000\times7.29=102.06$ kPa, $c=0.06$ m.

$$
C_l=0.2784,
\qquad
C_d=0.04858,
$$

$$
L'=C_lq_\infty c=\boxed{1.70\ \text{kN/m}},
\qquad
D'=C_dq_\infty c=\boxed{0.298\ \text{kN/m}}.
$$

> [!note] Printed answer 1.67 kN/m
> 1.67 matches treating $4\alpha/\beta$ as the **normal**-force coefficient and multiplying by $\cos\alpha$ ($1.705\cos10^\circ=1.679$). To first order the two are the same thing. Either way, compare with the exact shock-expansion values of [[SESA3029 Example Sheet 1 - Solutions#Q4. Flat plate by shock-expansion theory|Example Sheet 1 Q4]]: $L'=1.74$ and $D'=0.307$ kN/m. **Ackeret underestimates by about 2–3% at $10^\circ$.**

## Q5. Diamond aerofoil by Ackeret theory

$M=1.8$ ($\beta=1.4967$, $2/\beta=1.3363$), $p_\infty=50$ kPa, $q_\infty=113.4$ kPa. Surface slope $\varepsilon=0.05$ rad, $\alpha=2^\circ=0.03491$ rad.

**(a) Pressures**, using $p=p_\infty+q_\infty C_p$ with each face's local inclination $\theta$:

| Face | $\theta$ | $C_p=2\theta/\beta$ | $p$ (kPa) |
|---|---:|---:|---:|
| 1u | $\varepsilon-\alpha=+0.01505$ | $+0.0201$ | **52.3** |
| 2u | $-\varepsilon-\alpha=-0.08487$ | $-0.1134$ | **37.1** |
| 1l | $\varepsilon+\alpha=+0.08487$ | $+0.1134$ | **62.9** |
| 2l | $-\varepsilon+\alpha=-0.01505$ | $-0.0201$ | **47.7** |

**(b) Forces.**

*Lift.* On both halves $C_{p,l}-C_{p,u}=\tfrac{2}{\beta}\big[(\varepsilon+\alpha)-(\varepsilon-\alpha)\big]=4\alpha/\beta$ (front), and the same on the rear. So

$$
C_l=\frac{4\alpha}{\beta}=0.0933
\ \Rightarrow\
L'=\boxed{10.58\ \text{kN/m}}.
$$

*Drag.* This is pressure × slope, integrated. Each surface contributes $\int C_p\,(\mathrm dy/\mathrm dx)$ relative to the free stream. The $\alpha$ and $\varepsilon$ parts separate because the cross terms cancel between front and rear:

$$
C_d=\frac{4}{\beta}\left(\alpha^2+\varepsilon^2\right)=\frac{4}{1.4967}(0.001218+0.0025)=0.00994
\ \Rightarrow\
D'=\boxed{1.13\ \text{kN/m}}.
$$

The thickness term $4\varepsilon^2/\beta=4(t/c)^2/\beta$ is supersonic **wave drag due to thickness**, present even at zero lift.

*Moment.* $\Delta C_p$ is uniform along the chord, so the load acts at mid-chord:

$$
C_{m,LE}=-\tfrac12C_l=-\frac{2\alpha}{\beta}=-0.0466
\ \Rightarrow\
M'_{LE}=C_mq_\infty c^2=\boxed{-5.29\ \text{kN}}.
$$

**(c)** $x_{cp}=-C_{m,LE}/C_l=\boxed{0.50}$.

The sheet gives 52.3, 37.1, 62.9 and 47.7 kPa; 10.5 kN/m; 1.13 kN/m; −5.29 kN; 0.50 ✓.

> [!tip] Linear versus exact (Example Sheet 1 Q6)
> Linear theory gets the lift (10.58 against 10.64 kN/m) and the drag (1.126 against 1.133 kN/m) within 1%. It misses the forward shift of the centre of pressure (0.47 exact against 0.50 linear), which comes from the nonlinear difference between the shock and the fan.

## Q6. Critical Mach number via Prandtl–Glauert

**Theory needed.**

*Prandtl–Glauert.* Subsonic compressibility scales the incompressible pressure coefficient:

$$
C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}.
$$

*Critical pressure coefficient.* The critical Mach number is the free-stream Mach number at which the local Mach number first reaches 1 at the suction peak. With $C_p=\tfrac{2}{\gamma M_\infty^2}\left(\tfrac{p}{p_\infty}-1\right)$ and, isentropically,

$$
\frac{p}{p_\infty}=\left[\frac{1+\frac{\gamma-1}{2}M_\infty^2}{1+\frac{\gamma-1}{2}M^2}\right]^{\gamma/(\gamma-1)},
$$

set $M=1$:

$$
C_{p,cr}=\frac{2}{\gamma M_\infty^2}\left[\left(\frac{2+(\gamma-1)M_\infty^2}{\gamma+1}\right)^{\gamma/(\gamma-1)}-1\right].
$$

**Solve** $\dfrac{-2.5}{\sqrt{1-M^2}}=C_{p,cr}(M)$ by tabulating:

| $M_\infty$ | 0.40 | 0.44 | 0.448 | 0.45 | 0.46 |
|---|---:|---:|---:|---:|---:|
| PG: $-2.5/\sqrt{1-M^2}$ | $-2.728$ | $-2.784$ | $-2.796$ | $-2.800$ | $-2.816$ |
| $C_{p,cr}$ | $-3.662$ | $-2.927$ | $-2.802$ | $-2.772$ | $-2.628$ |

The two cross at $\boxed{M_{cr}=0.448}$ (sheet: 0.45 ✓). Above it a supersonic pocket and a shock form on the aerofoil.

## Links

- Previous sheet: [[SESA3029 Example Sheet 1 - Solutions]] · Next: [[SESA3029 Example Sheet 3 - Solutions]]
- Theory: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]] · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]] · [[Eigenvalues and Eigenvectors]]
- Hub: [[SESA3029 Aerothermodynamics Hub]]
