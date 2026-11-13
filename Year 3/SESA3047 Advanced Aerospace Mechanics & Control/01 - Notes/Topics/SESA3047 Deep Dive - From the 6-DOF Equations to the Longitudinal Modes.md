---
title: "SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: topic
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
order: 15.5
tags: [sesa3047, deep-dive, derivation, 6dof, linearisation, state-space, eigenvalues, eigenvectors, longitudinal-modes, spo, phugoid]
aliases: ["6-DOF to longitudinal modes", "Longitudinal modes deep dive", "F-4C longitudinal modes", "Linearising the 6-DOF model"]
date: 2026-11-12
status: written-ahead
coverage: "One chain from the flat-Earth 6-DOF model (Ch. 4 §4.3) through the trim point, the term-by-term linearisation (Ch. 5 §§5.2–5.3), M ẋ = A′x and A = M⁻¹A′, to the eigenvalues, eigenvectors and SPO approximation of the F-4C (Ch. 6 §§6.1–6.5, lectured L13–L17 and §6.5 set as reading); §9 covers the phugoid approximations of Ch. 6 §6.6, written ahead of the Mon 16 Nov lecture"
parent: ["[[SESA3047 Advanced Aerospace Mechanics & Control Hub]]"]
prerequisites: ["[[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]", "[[SESA3047 5.1 - State-Space Form and Linearisation]]", "[[SESA3047 5.2 - Longitudinal State-Space Model]]", "[[SESA3047 5.4 - Time-Domain Solution and Stability]]", "[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]"]
next_topics: []
key_concepts: ["[[Six-Degree-of-Freedom State Model]]", "[[Linearisation about an Equilibrium Point]]", "[[Longitudinal and Lateral Dynamics]]", "[[Aerodynamic Stability Derivatives]]", "[[Eigenvectors as Mode Shapes]]", "[[Short Period Oscillation]]", "[[Phugoid Mode]]"]
tutorial_sheets: ["[[SESA3047 Chapter 5 Practice Problems - Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/Chapter_5.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/L13 - SESA3047.txt", "02 - Sources/Lectures/02 November 2026 at 11_53_51.txt", "02 - Sources/Lectures/05 November 2026 at 14_53_19.txt", "02 - Sources/Lectures/05 November 2026 at 15_56_57.txt", "02 - Sources/Lectures/09 November 2026 at 11_54_07.txt"]
---

# SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes

> [!abstract] Summary
> Linearising the twelve nonlinear 6-DOF equations about steady straight flight splits them into a longitudinal and a lateral set; the longitudinal set, with gravity linearised about the trim climb angle and the aerodynamics written as derivatives, is $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$ in $[u,w,q,\theta]$, and $\mathbf A=\mathbf M^{-1}\mathbf A'$. For the F-4C of Table 6.1 the eigenvalues are a short-period pair $-0.3690\pm1.3558j$ ($\omega_n=1.405$ rad/s, $\zeta=0.263$) and a phugoid pair $-0.00645\pm0.0779j$ ($\omega_n=0.0781$ rad/s, $\zeta=0.083$). The eigenvectors show the SPO as a rotation of the aircraft about an almost unchanged flight path at constant speed, and the phugoid as a slow swing of flight-path angle and speed at almost constant angle of attack, with $|\theta|\approx\sqrt2\,|u|/U_\infty$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the longitudinal model from the nonlinear equations, for $\mathbf A$ from $\mathbf M$ and $\mathbf A'$, for the modes of a given $\mathbf A$, or for the SPO approximation of a $2\times2$ by hand.
> - **Assumptions:** trim in steady straight flight, $x$ along $U_\infty$ (so $\theta_0=\gamma_0$); symmetric rigid aircraft, constant $m$, $\rho$, $g$; perturbations small, angles in radians; aerodynamics linear in $u,w,q,\dot w$ with $\mathring X_q=\mathring X_{\dot w}=0$.
> - **Method:** 1. Write the 6-DOF rows for $u,w,q,\theta$ with gravity $mg[-s_\theta,\ s_\phi c_\theta,\ c_\phi c_\theta]^T$. 2. Substitute trim $+\,\epsilon\times$perturbation; the $\epsilon^0$ terms are the trim balance and cancel; drop $\epsilon^2$. 3. Add Eq. 5.16 and move every $\dot{(\ )}$ to the left: $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$. 4. $\mathbf A=\mathbf M^{-1}\mathbf A'$ ($\mathbf M$ is lower triangular). 5. Eigenvalues by `eig` (or by trace and determinant for a $2\times2$); for each pair $\omega_n=|\lambda|$, $\zeta=-\sigma/\omega_n$; read the eigenvector in angle units ($u/U_\infty$, $w/U_\infty$, $\theta$).
> - **Common mistakes:** dropping $mU_\infty q$ along with the genuine $\epsilon^2$ products; ranking eigenvector entries in mixed units, which makes $w$ look dominant in every mode.
> - **Practise:** [[#7. Eigenvectors by hand and the mode shapes (6.17–6.21)|the F-4C eigenvectors by hand]] · [[SESA3047 Chapter 5 Practice Problems - Solutions#Problem 3. The lateral state-space model|Practice problem 3]]

The 6-DOF model of [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model|4.3]] is exact for a rigid aircraft on a flat Earth, but it is twelve coupled nonlinear ODEs and says nothing directly about stability. Steady straight flight is an equilibrium of those equations, and close to it every product of two small departures is negligible. What is left is linear, and it falls into two blocks that do not talk to each other: a longitudinal block in the plane of symmetry and a lateral block out of it. The longitudinal block has four states, and its $4\times4$ state matrix contains the whole of the aircraft's free longitudinal motion.

That motion is two oscillations with very different time scales. The aircraft first pitches about its centre of gravity and settles within a few seconds, with speed and flight path hardly moving: the short-period oscillation (SPO). Then, over a minute or more, it exchanges speed for height along a gentle wave at almost constant angle of attack: the phugoid. Both are eigenvalue pairs of the same matrix, and both eigenvectors are readable once the states are put into comparable units.

The aircraft throughout is the McDonnell Douglas F-4C Phantom II of Chapter 6 Table 6.1, in level flight at $U_\infty=178$ m/s, and every number is computed for it. The separate steps are lectured in [[SESA3047 5.1 - State-Space Form and Linearisation|5.1]], [[SESA3047 5.2 - Longitudinal State-Space Model|5.2]], [[SESA3047 5.4 - Time-Domain Solution and Stability|5.4]] and [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]]. The phugoid approximations of Chapter 6 §6.6 (§9) are written ahead of their lecture on Mon 16 Nov.

## 1. The complete 6-DOF model and the trim point (4.3, 5.1)

The flat-Earth model of Chapter 4 (Eq. 4.42), with states $[x,y,z,\ \phi,\theta,\psi,\ u,v,w,\ p,q,r]^T$, is

$$
\dot{\mathbf p}^{NED}=\mathbf C^T\mathbf v,\qquad
\dot{\boldsymbol\Phi}=\mathbf H(\boldsymbol\Phi)\boldsymbol\omega,\qquad
\dot{\mathbf v}=\frac{\mathbf F}{m}+\mathbf C\mathbf g^{NED}-\boldsymbol\omega\times\mathbf v,\qquad
\dot{\boldsymbol\omega}=\mathbf J^{-1}\left(\mathbf M-\boldsymbol\omega\times\mathbf J\boldsymbol\omega\right),
$$

with $\mathbf F$ the aerodynamic and thrust force (gravity excluded) and $\mathbf C=\mathbf C_{FRD/NED}$. In Chapter 5 the body velocity components are written $U,V,W$ for the total and $u,v,w$ for the perturbation, and that convention is used throughout. The assumptions are those of the flat-Earth model ([[Six-Degree-of-Freedom State Model]]): rigid body with constant $m$ and $\mathbf J$, NED treated as inertial, constant $g$. Two more are needed for the linearisation: the aircraft is symmetric about its $x$–$z$ plane, so $J_{xy}=J_{yz}=0$, and the air density is the same at every height the motion visits, so the aerodynamic forces do not depend on position.

Gravity in body axes is $\mathbf C$ times $[0,0,g]^T$, which is $g$ times the third column of $\mathbf C$ ([[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles#Gravity in body axes (derivation)|2.2]]):

$$
\mathbf C\mathbf g^{NED}=g\begin{bmatrix}-\sin\theta\\ \sin\phi\cos\theta\\ \cos\phi\cos\theta\end{bmatrix}.
$$

Multiply the translational row by $m$ and write it in components, with $\mathbf F=[X_a,Y_a,Z_a]^T$ and $\boldsymbol\omega\times\mathbf v=[qW-rV,\ rU-pW,\ pV-qU]^T$:

$$
m\left(\dot U+qW-rV\right)=X_a-mg\sin\theta,
$$

$$
m\left(\dot V+rU-pW\right)=Y_a+mg\sin\phi\cos\theta,
$$

$$
m\left(\dot W+pV-qU\right)=Z_a+mg\cos\phi\cos\theta.
$$

These are Eqs. 5.3 with the weight written out. The pitch row of the rotational dynamics, with the symmetric inertia matrix, is ([[SESA3047 5.1 - State-Space Form and Linearisation#4. Linearising the moment equations (5.8)|5.1 §4]])

$$
J_{yy}\dot q+(J_{xx}-J_{zz})pr+J_{xz}\left(p^2-r^2\right)=M_a,
$$

and the pitch row of the rotational kinematics is $\dot\theta=q\cos\phi-r\sin\phi$ ([[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#6. Inverting: the rotational kinematic equation|3.1 §6]]). The height rate is the third row of $\mathbf C^T\mathbf v$ with the sign changed, since $h=-z$:

$$
\dot h=U\sin\theta-V\sin\phi\cos\theta-W\cos\phi\cos\theta.
$$

### The trim point

The equilibrium is steady straight flight at climb angle $\gamma_0$ with no rotation and no sideslip:

$$
(U,V,W)=(U_\infty,0,0),\qquad(p,q,r)=(0,0,0),\qquad\phi_0=0,\qquad\theta_0=\gamma_0 .
$$

The body $x$ axis is chosen along the trim velocity, so the trim angle of attack is zero and the pitch attitude equals the climb angle. Every time derivative is zero there, so the three force rows and the pitch-moment row at trim reduce to

$$
0=X_{a0}-mg\sin\gamma_0,\qquad0=Z_{a0}+mg\cos\gamma_0,\qquad0=M_{a0}.
$$

The first says thrust minus drag balances the weight component along the flight path, the second that lift ($-Z_{a0}$) balances $mg\cos\gamma_0$, and the third that the aircraft is trimmed in pitch. For the F-4C in level flight, $\gamma_0=0$, so $X_{a0}=0$ and $-Z_{a0}=mg=17642\times9.81=173068$ N. The lift coefficient follows from Eq. 6.30:

$$
C_L=\frac{mg}{\tfrac12\rho U_\infty^2S}=\frac{173068}{\tfrac12(0.3809)(178)^2(49.239)}=\frac{173068}{297119}=0.5825 .
$$

## 2. Small perturbations and what survives (5.4–5.15)

Every variable is written as its trim value plus $\epsilon$ times a perturbation, with $\epsilon\ll1$ and all angles in radians ([[Linearisation about an Equilibrium Point]]):

$$
U=U_\infty+\epsilon u,\quad V=\epsilon v,\quad W=\epsilon w,\quad p=\epsilon p_1,\quad q=\epsilon q_1,\quad r=\epsilon r_1,\quad\phi=\epsilon\phi_1,\quad\theta=\gamma_0+\epsilon\theta_1 .
$$

The forces and moment are perturbed the same way, $X_a=X_{a0}+\epsilon\,\Delta X_a$ and so on. Three bookkeeping rules then do all the work: the $\epsilon^0$ terms must reproduce the trim balance of §1 and cancel; the $\epsilon^2$ terms are dropped; what is left is divided by $\epsilon$.

### Inertial and moment terms

In the $U$ row, $qW$ and $rV$ are both products of two perturbations:

$$
m\left(\epsilon\dot u+\epsilon^2q_1w-\epsilon^2r_1v\right),
$$

so only $m\epsilon\dot u$ survives. In the $W$ row, $pV$ is a product of two perturbations, but $qU$ is not, because $U$ has a non-zero trim value:

$$
qU=\epsilon q_1\left(U_\infty+\epsilon u\right)=\epsilon U_\infty q_1+\epsilon^2q_1u .
$$

So the $W$ row keeps $m\left(\epsilon\dot w-\epsilon U_\infty q_1\right)$. This is the term that turns the velocity vector when the aircraft pitches: a pitch rate $q_1$ at speed $U_\infty$ needs a normal force $-mU_\infty q_1$ ([[SESA3047 5.1 - State-Space Form and Linearisation#3. Linearising the force equations (5.3–5.7)|5.1 §3]]).

In the pitch-moment row, $pr$, $p^2$ and $r^2$ are all products of two perturbed rates, each $O(\epsilon^2)$, so

$$
J_{yy}\,\epsilon\dot q_1=\epsilon\,\Delta M_a .
$$

### Gravity

Expand the $X$ component with the compound-angle formula and the small-angle forms $\cos\epsilon\theta_1=1+O(\epsilon^2)$, $\sin\epsilon\theta_1=\epsilon\theta_1+O(\epsilon^3)$:

$$
-mg\sin(\gamma_0+\epsilon\theta_1)=-mg\sin\gamma_0\cos\epsilon\theta_1-mg\cos\gamma_0\sin\epsilon\theta_1 ,
$$

$$
-mg\sin(\gamma_0+\epsilon\theta_1)=-mg\sin\gamma_0-mg\cos\gamma_0\,\epsilon\theta_1+O(\epsilon^2).
$$

The $Z$ component carries an extra factor $\cos\phi=\cos\epsilon\phi_1=1-\tfrac12\epsilon^2\phi_1^2+\dots$, which is 1 to first order:

$$
mg\cos\epsilon\phi_1\cos(\gamma_0+\epsilon\theta_1)=mg\left(\cos\gamma_0-\sin\gamma_0\,\epsilon\theta_1\right)+O(\epsilon^2).
$$

The $Y$ component has $\sin\phi=\epsilon\phi_1$ as a factor, so only the zeroth-order part of $\cos\theta$ multiplies it:

$$
mg\sin\epsilon\phi_1\cos(\gamma_0+\epsilon\theta_1)=mg\cos\gamma_0\,\epsilon\phi_1+O(\epsilon^2).
$$

The $\epsilon^0$ parts, $-mg\sin\gamma_0$ and $mg\cos\gamma_0$, cancel against $X_{a0}$ and $Z_{a0}$ by the trim balance. The first-order parts are Eq. 5.15, $X_{g1}=-mg\cos\gamma_0\,\theta_1$ and $Z_{g1}=-mg\sin\gamma_0\,\theta_1$ ([[SESA3047 5.2 - Longitudinal State-Space Model#2. Gravitational contribution (5.9–5.15)|5.2 §2]]), together with $Y_{g1}=mg\cos\gamma_0\,\phi_1$. Pitching changes only the $X$ and $Z$ components and rolling changes only the $Y$ component, to first order: gravity already respects the longitudinal–lateral split.

### Kinematics and position

The pitch kinematics expand as

$$
\epsilon\dot\theta_1=\epsilon q_1\cos\epsilon\phi_1-\epsilon r_1\sin\epsilon\phi_1=\epsilon q_1-\epsilon^2r_1\phi_1+O(\epsilon^3),
$$

so $\dot\theta_1=q_1$: the small-angle form of [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#7. Physical interpretation and the small-angle form|3.1 §7]] is exact to first order about this trim. The height rate expands to

$$
\dot h=U_\infty\sin\gamma_0+\epsilon\left(U_\infty\cos\gamma_0\,\theta_1+\sin\gamma_0\,u-\cos\gamma_0\,w\right)+O(\epsilon^2),
$$

where the $V$ term is $O(\epsilon^2)$ because both $V$ and $\sin\phi$ are perturbations. The steady climb rate $U_\infty\sin\gamma_0$ is the trim part. At level trim the perturbation is $\dot h=U_\infty\theta-w$, the relation used for the phugoid height in [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#6. Phase relationships in a mode|6.1 §6]].

Neither $h$ nor the horizontal position appears on the right-hand side of any force or moment row: on a flat Earth with constant $g$ and constant $\rho$ the aircraft cannot tell where it is. Position therefore drops out of the stability problem. Adding $h$ as a fifth state only appends a row $\dot h=U_\infty\theta-w$ and a column of zeros, which adds an eigenvalue $\lambda=0$ (checked numerically for the F-4C) and leaves the other four unchanged. The heading $\psi$ drops out of the lateral set for the same reason.

> [!tip] Which products survive
> A product of two variables survives at first order only if one factor has a non-zero trim value. About this trim the only non-zero values are $U_\infty$ and $\gamma_0$, so the surviving coupling terms are exactly $mU_\infty q_1$, $mU_\infty r_1$ and the gravity terms with $\cos\gamma_0$ and $\sin\gamma_0$. Every term that would mix the $u,w,q,\theta$ group with the $v,p,r,\phi$ group is a product of one variable from each, both with zero trim value, and so vanishes.

After cancelling the trim terms and dividing by $\epsilon$, the longitudinal rows are (perturbation subscripts dropped, $q$ and $\theta$ now meaning $q_1$ and $\theta_1$)

$$
m\dot u=\Delta X_a-mg\cos\gamma_0\,\theta,
$$

$$
m\left(\dot w-U_\infty q\right)=\Delta Z_a-mg\sin\gamma_0\,\theta,
$$

$$
J_{yy}\dot q=\Delta M_a,
$$

$$
\dot\theta=q .
$$

None of $v,p,r,\phi$ appears, and the lateral rows contain none of $u,w,q,\theta$ as long as the aerodynamic forces respect the symmetry too ([[SESA3047 5.2 - Longitudinal State-Space Model#1. The longitudinal–lateral split|5.2 §1]]).

## 3. Aerodynamic forces as derivatives (5.16)

The aerodynamic increments are first-order Taylor expansions in the perturbations about trim. Each coefficient is a partial derivative evaluated at trim, for example $\mathring Z_w=\partial Z_a/\partial W|_0$, so each is a constant and the expansions are linear (Eq. 5.16):

$$
\Delta X_a=\mathring X_uu+\mathring X_ww,
$$

$$
\Delta Z_a=\mathring Z_uu+\mathring Z_ww+\mathring Z_qq+\mathring Z_{\dot w}\dot w,
$$

$$
\Delta M_a=\mathring M_uu+\mathring M_ww+\mathring M_qq+\mathring M_{\dot w}\dot w .
$$

$\mathring X_q$ and $\mathring X_{\dot w}$ are taken as zero, the expansions contain no control deflections (the free motion is what decides stability), and there is no $h$ term, which is the constant-density assumption of §1. The $\dot w$ terms come from the lag of the wing's downwash at the tail ([[Aerodynamic Stability Derivatives]]). For the F-4C, Table 6.1 gives dimensionless derivatives; the conversion of [[SESA3047 5.2 - Longitudinal State-Space Model#6. Dimensional and dimensionless derivatives (appendix, 5.51–5.56)|5.2 §6]] gives

| Derivative | Value | Derivative | Value |
|---|---|---|---|
| $\mathring X_u$ | $-126.86$ kg/s | $\mathring Z_q$ | $-9881.9$ kg m/s |
| $\mathring X_w$ | $80.62$ kg/s | $\mathring M_u$ | $277.47$ kg m/s |
| $\mathring Z_u$ | $-1214.0$ kg/s | $\mathring M_w$ | $-1770.07$ kg m/s |
| $\mathring Z_w$ | $-5215.4$ kg/s | $\mathring M_{\dot w}$ | $-132.47$ kg m |
| $\mathring Z_{\dot w}$ | $-18.33$ kg | $\mathring M_q$ | $-50798$ kg m²/s |

Eq. 6.22 quotes these rounded to integers; the unrounded values are carried below.

## 4. Assembling M ẋ = A′x (5.17–5.18)

Substitute Eq. 5.16 into the four rows of §2. The axial row is

$$
m\dot u=\mathring X_uu+\mathring X_ww-mg\cos\gamma_0\,\theta .
$$

The normal row, with the $\Delta Z_a$ terms written out, is

$$
m\dot w-mU_\infty q=\mathring Z_uu+\mathring Z_ww+\mathring Z_qq+\mathring Z_{\dot w}\dot w-mg\sin\gamma_0\,\theta .
$$

Move $\mathring Z_{\dot w}\dot w$ to the left and $mU_\infty q$ to the right:

$$
\left(m-\mathring Z_{\dot w}\right)\dot w=\mathring Z_uu+\mathring Z_ww+\left(\mathring Z_q+mU_\infty\right)q-mg\sin\gamma_0\,\theta .
$$

The pitching row, with $\mathring M_{\dot w}\dot w$ moved to the left, is

$$
-\mathring M_{\dot w}\dot w+J_{yy}\dot q=\mathring M_uu+\mathring M_ww+\mathring M_qq,
$$

and the fourth row is $\dot\theta=q$. Collected with $\mathbf x=[u,w,q,\theta]^T$, this is Eq. 5.18 (Eq. 6.1):

$$
\underbrace{\begin{bmatrix}m&0&0&0\\0&m-\mathring Z_{\dot w}&0&0\\0&-\mathring M_{\dot w}&J_{yy}&0\\0&0&0&1\end{bmatrix}}_{\mathbf M}\dot{\mathbf x}
=\underbrace{\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\cos\gamma_0\\\mathring Z_u&\mathring Z_w&\mathring Z_q+mU_\infty&-mg\sin\gamma_0\\\mathring M_u&\mathring M_w&\mathring M_q&0\\0&0&1&0\end{bmatrix}}_{\mathbf A'}\mathbf x .
$$

$\mathbf M$ is not the identity because $\dot w$ appears in two rows: the downwash lag adds an apparent mass $-\mathring Z_{\dot w}$ to the $w$ row and couples $\dot w$ into the pitching row. That is why the form $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$ comes first and $\dot{\mathbf x}=\mathbf A\mathbf x$ second. For the F-4C in level flight ($\cos\gamma_0=1$, $\sin\gamma_0=0$) the numbers are those of Eq. 6.22:

$$
\mathbf M=\begin{bmatrix}17642&0&0&0\\0&17660&0&0\\0&132.47&165669&0\\0&0&0&1\end{bmatrix},\qquad
\mathbf A'=\begin{bmatrix}-126.86&80.62&0&-173068\\-1214.0&-5215.4&3130394&0\\277.47&-1770.07&-50798&0\\0&0&1&0\end{bmatrix}.
$$

The $q$ entry of row 2 is $\mathring Z_q+mU_\infty=-9882+3140276=3130394$ kg m/s: the kinematic term $mU_\infty$ outweighs the aerodynamic $\mathring Z_q$ by a factor of 318.

## 5. From A′ to A for the F-4C (6.3)

$\mathbf M$ is lower triangular, so its inverse is too, and it can be found row by row. Write $a=m-\mathring Z_{\dot w}$ and $b=\mathring M_{\dot w}$. Rows 1, 2 and 4 of $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$ give $\dot u$, $\dot w$ and $\dot\theta$ by division by $m$, $a$ and 1. Row 3 is

$$
-b\,\dot w+J_{yy}\dot q=(\text{row 3 of }\mathbf A')\,\mathbf x .
$$

Substitute $\dot w=(\text{row 2 of }\mathbf A')\mathbf x/a$:

$$
J_{yy}\dot q=(\text{row 3 of }\mathbf A')\,\mathbf x+\frac{b}{a}(\text{row 2 of }\mathbf A')\,\mathbf x .
$$

Divide by $J_{yy}$:

$$
\dot q=\left[\frac{1}{J_{yy}}(\text{row 3})+\frac{b}{aJ_{yy}}(\text{row 2})\right]\mathbf x .
$$

So $\mathbf M^{-1}$ is diagonal with entries $1/m$, $1/a$, $1/J_{yy}$, 1, plus one off-diagonal entry in position (3,2):

$$
\left(\mathbf M^{-1}\right)_{32}=\frac{\mathring M_{\dot w}}{J_{yy}\left(m-\mathring Z_{\dot w}\right)}=\frac{-132.47}{165669\times17660.3}=-4.5277\times10^{-8}.
$$

Check it: row 3 of $\mathbf M$ times column 2 of $\mathbf M^{-1}$ is $(-b)(1/a)+J_{yy}\,b/(aJ_{yy})=0$. One entry of $\mathbf A$ as an example, the (3,1) entry, which is how a speed change pitches the aircraft:

$$
A_{31}=\frac{\mathring M_u}{J_{yy}}+\left(\mathbf M^{-1}\right)_{32}\mathring Z_u=\frac{277.47}{165669}+(-4.5277\times10^{-8})(-1214.0)
$$

$$
A_{31}=1.6748\times10^{-3}+0.0550\times10^{-3}=1.7298\times10^{-3}\ \text{rad s}^{-2}\text{ per m/s}.
$$

The full matrix (computed in NumPy, symbolic form in [[SESA3047 5.2 - Longitudinal State-Space Model#5. The complete model and the state matrix (5.18)|5.2 §5]]) is

$$
\mathbf A=\mathbf M^{-1}\mathbf A'=\begin{bmatrix}-0.0071908&0.0045699&0&-9.81\\-0.068742&-0.29532&177.26&0\\0.0017298&-0.010448&-0.44836&0\\0&0&1&0\end{bmatrix}.
$$

The $\mathring M_{\dot w}$ coupling is not negligible everywhere. In the (3,3) entry it adds $(\mathbf M^{-1})_{32}(\mathring Z_q+mU_\infty)=-0.1417$ to $\mathring M_q/J_{yy}=-0.3066$: the downwash lag supplies almost a third of the pitch damping in $\mathbf A$.

> [!check] The linearisation, checked numerically
> The longitudinal 6-DOF rows of §1 (with $V=p=r=\phi=0$, which is consistent for a symmetric aircraft) and the linear aerodynamics of Eq. 5.16 were coded as a nonlinear right-hand side with the $\dot W$ terms solved implicitly. At trim it returns zero, and its central-difference Jacobian with respect to $[U,W,q,\theta]$ matches $\mathbf A$ to $6\times10^{-10}$ (relative $3\times10^{-12}$). Integrated from $w(0)=1$, 5 and 20 m/s (an initial $\alpha$ of $0.32^\circ$, $1.61^\circ$ and $6.44^\circ$), the nonlinear $w(t)$ stays within 0.05 %, 0.28 % and 1.3 % of $w_0$ of the linear response over 120 s: the error grows as the square of the disturbance, as a dropped $\epsilon^2$ term should.

## 6. The characteristic equation and its two quadratics (6.5–6.12)

The eigenvalues solve $\det(\mathbf A-\lambda\mathbf I)=0$. For a $4\times4$ this is not expected by hand in the exam; NumPy's `poly` gives the longitudinal stability quartic of the F-4C,

$$
\lambda^4+0.750869\lambda^3+1.990078\lambda^2+0.029978\lambda+0.012057=0,
$$

and `eig` gives its roots:

$$
\lambda_{1,2}=-0.36898\pm1.35584j,\qquad\lambda_{3,4}=-0.0064504\pm0.077878j .
$$

These agree with §6.5 of Chapter 6. The real parts are all negative, so the trimmed F-4C is stable ([[SESA3047 5.4 - Time-Domain Solution and Stability#4. Stability from the eigenvalues|5.4 §4]]). For each pair $\sigma\pm j\omega$, $\omega_n=|\lambda|$, $\zeta=-\sigma/\omega_n$, $t_{1/2}=\ln0.5/\sigma$ and $T=2\pi/\omega$ ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#3. Damping ratio and natural frequency (6.13–6.16)|6.1 §3]]):

| Mode | $\lambda$ | $\omega_n$ (rad/s) | $\zeta$ | $t_{1/2}$ (s) | $T$ (s) |
|---|---|---|---|---|---|
| SPO | $-0.36898\pm1.35584j$ | 1.4052 | 0.2626 | 1.88 | 4.63 |
| Phugoid | $-0.0064504\pm0.077878j$ | 0.078145 | 0.0825 | 107.5 | 80.7 |

The SPO is 18 times faster and three times better damped than the phugoid. In half-lives the gap is 57 to 1.

![[amc_dd_long_eigenvalue_map.png|900]]

### Why the quartic splits into two quadratics

The exact quadratic factors, formed from the conjugate pairs, are

$$
\left(\lambda^2+0.737968\lambda+1.974451\right)\left(\lambda^2+0.012901\lambda+0.006107\right).
$$

Chapter 6 quotes factors like these for the Eq. 6.4 example (Eq. 6.10) without saying where they come from. They follow from the separation of time scales. Write the quartic as $\lambda^4+a_3\lambda^3+a_2\lambda^2+a_1\lambda+a_0$ and the factors as a fast quadratic $\lambda^2+b_1\lambda+b_0$ and a slow one $\lambda^2+c_1\lambda+c_0$. Multiply out:

$$
\left(\lambda^2+b_1\lambda+b_0\right)\left(\lambda^2+c_1\lambda+c_0\right)=\lambda^4+(b_1+c_1)\lambda^3+(b_0+b_1c_1+c_0)\lambda^2+(b_1c_0+b_0c_1)\lambda+b_0c_0 .
$$

Match coefficients:

$$
a_3=b_1+c_1,\qquad a_2=b_0+b_1c_1+c_0,\qquad a_1=b_1c_0+b_0c_1,\qquad a_0=b_0c_0 .
$$

If the slow mode's coefficients are small compared with the fast mode's ($c_1\ll b_1$, $c_0\ll b_0$), the first two become

$$
b_1\approx a_3,\qquad b_0\approx a_2 .
$$

The last one then gives

$$
c_0=\frac{a_0}{b_0}\approx\frac{a_0}{a_2},
$$

and the third, solved for $c_1$, gives

$$
c_1=\frac{a_1-b_1c_0}{b_0}\approx\frac{a_1-a_3a_0/a_2}{a_2}=\frac{a_1a_2-a_0a_3}{a_2^2}.
$$

For the F-4C this gives $\lambda^2+0.75087\lambda+1.99008$ and $\lambda^2+0.012778\lambda+0.006059$, with roots $-0.3754\pm1.3598j$ and $-0.00639\pm0.07757j$, within 2 % of the exact values. For the Eq. 6.4 example ($a_3=1$, $a_2=2.0084$, $a_1=0.01$, $a_0=0.0100553$) it gives $\lambda^2+\lambda+2.0084$ and $\lambda^2+0.002486\lambda+0.005007$: Eq. 6.10's $(\lambda^2+\lambda+2)(\lambda^2+0.0025\lambda+0.005)$ to the handout's rounding.

## 7. Eigenvectors by hand and the mode shapes (6.17–6.21)

Once $\lambda$ is known, the eigenvector of a $4\times4$ needs only a $2\times2$ solve, because two rows of $\mathbf A$ are almost empty. Scale the eigenvector so that $\theta=1$. Row 4 of $(\mathbf A-\lambda\mathbf I)\mathbf v=\mathbf 0$ reads $q-\lambda\theta=0$, so

$$
q=\lambda .
$$

Rows 1 and 2, with $\theta=1$ and $q=\lambda$ substituted and the knowns moved to the right, are

$$
(\lambda-A_{11})\,u-A_{12}\,w=A_{14},
$$

$$
-A_{21}\,u+(\lambda-A_{22})\,w=A_{23}\,\lambda .
$$

Row 3 is not needed: it holds automatically because $\lambda$ is an eigenvalue, and evaluating it is the check. With $A_{13}=A_{24}=0$ at level trim these two rows are complete.

For the SPO, $\lambda=-0.36898+1.35584j$:

$$
\begin{bmatrix}-0.36179+1.35584j&-0.0045699\\0.068742&-0.07366+1.35584j\end{bmatrix}\begin{bmatrix}u\\w\end{bmatrix}=\begin{bmatrix}-9.81\\-65.405+240.330j\end{bmatrix}.
$$

The determinant of the $2\times2$ is $-1.81134-0.59041j$, and Cramer's rule gives

$$
u=1.7735+6.1587j\ \text{m/s},\qquad w=179.04+38.60j\ \text{m/s}\qquad(\text{per rad of }\theta).
$$

For the phugoid, $\lambda=-0.0064504+0.077878j$:

$$
\begin{bmatrix}0.00074+0.07788j&-0.0045699\\0.068742&0.28887+0.07788j\end{bmatrix}\begin{bmatrix}u\\w\end{bmatrix}=\begin{bmatrix}-9.81\\-1.1434+13.8044j\end{bmatrix},
$$

$$
u=-0.164+125.916j\ \text{m/s},\qquad w=0.826+17.601j\ \text{m/s}\qquad(\text{per rad of }\theta).
$$

In both cases row 3 is satisfied to $10^{-15}$, and the vectors are `eig`'s eigenvectors rescaled.

The raw entries are in m/s, rad/s and rad, so $w$ looks dominant in both modes. The fair comparison is in angles ([[Eigenvectors as Mode Shapes]]): $u/U_\infty$ is the fractional speed change, $\alpha=w/U_\infty$ the angle-of-attack change, $\theta$ the attitude change, and $q/|\lambda|$ has the same modulus as $\theta$ because $\theta=q/\lambda$. The flight-path angle follows as $\gamma=\theta-\alpha$ ([[SESA3047 5.2 - Longitudinal State-Space Model#2. Gravitational contribution (5.9–5.15)|5.2 §2]]).

| Entry (per rad of $\theta$) | SPO: modulus | SPO: phase | Phugoid: modulus | Phugoid: phase |
|---|---|---|---|---|
| $u/U_\infty$ | 0.036 | $73.9^\circ$ | 0.707 | $90.1^\circ$ |
| $\alpha=w/U_\infty$ | 1.029 | $12.2^\circ$ | 0.099 | $87.3^\circ$ |
| $q/\lvert\lambda\rvert$ | 1 | $105.2^\circ$ | 1 | $94.7^\circ$ |
| $\theta$ | 1 | $0^\circ$ | 1 | $0^\circ$ |
| $\gamma=\theta-\alpha$ | 0.217 | $-91.5^\circ$ | 1.000 | $-5.7^\circ$ |

![[amc_dd_long_mode_phasors.png|900]]

### The short-period mode

In the SPO, $\alpha$ and $\theta$ have almost the same size and almost the same phase, so their difference $\gamma$ is only a fifth of either. The aircraft rotates about its velocity vector: the nose pitches up, the angle of attack rises with it, and the flight path barely turns in the four or five seconds the mode lasts. The speed change is 3.6 % of the angle change, which is why $u$ (and $\theta$'s slow influence through gravity) can be frozen in the SPO approximation of §8. The pitch rate leads $\theta$ by $105.2^\circ=90^\circ+\arcsin0.2626$, the integrator lag of [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#6. Phase relationships in a mode|6.1 §6]].

### The phugoid mode

In the phugoid the roles reverse. $\alpha$ is a tenth of $\theta$ and nearly in quadrature with it, so $\gamma\approx\theta$: the aircraft's nose follows the flight path, and the motion is a change of flight direction and speed at almost constant angle of attack. The speed leads the attitude by a quarter cycle. The ratio of the two amplitudes is

$$
\frac{|\theta|}{|u|/U_\infty}=\frac{1}{0.7074}=1.414\approx\sqrt2,
$$

which is the amplitude ratio of Lanchester's constant-energy phugoid (§9). The height follows from $\dot h=U_\infty\theta-w$ and $\dot h=\lambda h$:

$$
h=\frac{U_\infty\theta-w}{\lambda}=\frac{178-(0.826+17.601j)}{-0.0064504+0.077878j},
$$

which has modulus 2278 m per rad of $\theta$, or 18.1 m per 1 m/s of $u$, at $169.5^\circ$ from $u$: the aircraft is slowest near the top of the wave and fastest near the bottom.

> [!check] Energy exchange in the F-4C phugoid
> Per unit mass, the kinetic-energy amplitude is $U_\infty|u|=178\times125.92=22413$ m²/s² per rad of $\theta$ and the potential-energy amplitude is $g|h|=9.81\times2278.4=22351$ m²/s², equal to 0.3 %. They are $169.5^\circ$ apart rather than $180^\circ$, so the sum oscillates with an amplitude of 18 % of either term: that residual is the net work done by the aerodynamic forces over the cycle, through $\mathring X_u$ and the $\mathring M_u$ coupling (§9), and it is what gives this phugoid its $\zeta=0.083$. For the more lightly damped Eq. 6.4 example the offset is only $3^\circ$ ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#6. Phase relationships in a mode|6.1 §6]]).

The response started on the real part of each eigenvector shows the same shapes in time. Started on the SPO shape with $\theta(0)=1^\circ$, $\theta$ and $\alpha$ ring down together in about 8 s, $\gamma$ never exceeds $0.15^\circ$, and the speed moves by at most 0.07 m/s. Started on the phugoid shape, $\gamma$ tracks $\theta$, $\alpha$ stays below $0.1^\circ$, and $u$ swings by about 2 m/s with an 81 s period ([[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#5. Starting the system on an eigenvector (6.19–6.21)|6.1 §5]] shows why each start excites one mode only).

![[amc_dd_long_modal_responses.png|900]]

In the F-4C phugoid $\alpha$ is in phase with $u$, whereas in the Eq. 6.4 example it is in antiphase. The difference is $\mathring M_u$: the F-4C has $\mathring M_u=277$ kg m/s, so extra speed pitches the nose up, while Eq. 6.4 has $A_{31}=0$. Over a phugoid cycle $\dot q$ is tiny, so the pitching moment stays almost balanced, $\mathring M_uu+\mathring M_ww\approx0$, which gives $\alpha/(u/U_\infty)\approx-\mathring M_u/\mathring M_w=0.157$ against the eigenvector's 0.140. This quasi-static moment balance is the starting point of the improved phugoid approximation (§9).

## 8. The SPO approximation and what sets it (6.22–6.27)

The SPO eigenvector justifies the first assumption of §6.5 directly: over an SPO cycle $u/U_\infty$ is 3.6 % of $\alpha$, so $u$ is frozen, and $\theta$ enters the $w$ and $q$ rows only through gravity, which is $-mg\sin\gamma_0\,\theta=0$ at level trim. Deleting the $u$ and $\theta$ columns and rows leaves the $w$–$q$ block. The second assumption, $\mathring Z_{\dot w}\ll m$ and $\mathring Z_q\ll mU_\infty$ (0.10 % and 0.31 % for the F-4C), removes the small terms of that block. The derivation of Eqs. 6.23–6.27 is in [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#Derivation|6.1 §7]]; the reduced state matrix is

$$
\mathbf A_{\text{SPO}}=\begin{bmatrix}\dfrac{\mathring Z_w}{m}&U_\infty\\[2mm]\dfrac{\mathring M_w}{J_{yy}}+\dfrac{\mathring M_{\dot w}\mathring Z_w}{mJ_{yy}}&\dfrac{\mathring M_q+U_\infty\mathring M_{\dot w}}{J_{yy}}\end{bmatrix}=\begin{bmatrix}-0.29563&178\\-0.010448&-0.44895\end{bmatrix}.
$$

By hand, the characteristic equation of a $2\times2$ is $\lambda^2-(\operatorname{tr})\lambda+\det=0$:

$$
\operatorname{tr}\mathbf A_{\text{SPO}}=-0.29563-0.44895=-0.74458=-2\zeta\omega_n,
$$

$$
\det\mathbf A_{\text{SPO}}=(-0.29563)(-0.44895)-(178)(-0.010448)=0.13272+1.85974=1.99246=\omega_n^2 .
$$

So $\omega_n=1.4115$ rad/s, $\zeta=0.74458/(2\times1.4115)=0.2637$ and $\lambda=-0.3723\pm1.3616j$, against $1.4052$, $0.2626$ and $-0.3690\pm1.3558j$ for the full model.

The approximation's error has two sources, and they can be separated. The $w$–$q$ block of the full $\mathbf A$ (rows and columns 2–3, which keeps $\mathring Z_{\dot w}$ and $\mathring Z_q$ but freezes $u$ and $\theta$) has eigenvalues $-0.3718\pm1.3587j$. Freezing $u$ and $\theta$ moves the root by 0.0041; dropping $\mathring Z_{\dot w}$ and $\mathring Z_q$ then moves it by a further 0.0029. Both are under 0.3 % of $\omega_n$.

The terms of the trace and determinant show what sets the mode:

$$
\omega_n^2=\underbrace{-\frac{U_\infty\mathring M_w}{J_{yy}}}_{1.902}+\underbrace{\frac{\mathring M_q\mathring Z_w}{mJ_{yy}}}_{0.091},\qquad
2\zeta\omega_n=\underbrace{-\frac{\mathring M_q}{J_{yy}}}_{0.307}\ \underbrace{-\frac{\mathring Z_w}{m}}_{0.296}\ \underbrace{-\frac{U_\infty\mathring M_{\dot w}}{J_{yy}}}_{0.142}.
$$

The SPO frequency is set almost entirely (95 %) by the static pitch stiffness $\mathring M_w<0$, which is the static margin; the damping comes in nearly equal parts from the tail's pitch damping, the lift-curve slope and the downwash lag ([[Short Period Oscillation]]).

## 9. The phugoid approximations (written ahead)

*Written ahead from Chapter 6 §6.6, due to be lectured on Mon 16 Nov; to be checked against the lecture.*

The phugoid evolves slowly, on the time scale where $u$ and $\theta$ (or $h$) are the important variables and $w$ and $q$ have long since settled. Chapter 6 gives two approximations.

### Lanchester's energy argument (6.28–6.33)

Lanchester's approximation assumes the total energy is constant, with $h$ measured from the trim height, where the speed is $U_\infty$ (Eq. 6.28):

$$
\tfrac12mU_\infty^2=\tfrac12mU^2+mgh .
$$

Divide by $\tfrac12m$ (Eq. 6.29):

$$
U_\infty^2=U^2+2gh .
$$

The angle of attack, and with it $C_L$, are assumed fixed, at the trim value of Eq. 6.30, $C_L=mg/(\tfrac12\rho U_\infty^2S)$. Multiply Eq. 6.29 by $\tfrac12\rho SC_L$:

$$
\tfrac12\rho U^2SC_L=\tfrac12\rho U_\infty^2SC_L-\rho SC_Lgh .
$$

The left side is the lift $L$ at speed $U$, and the first term on the right is $mg$ by Eq. 6.30 (Eq. 6.31):

$$
L=mg-\rho SC_Lgh .
$$

With the flight path close to horizontal, the lift acts almost vertically, and Newton's law for the height is (Eq. 6.32)

$$
m\ddot h=L-mg=-\rho SC_Lgh .
$$

Substitute $C_L$ from Eq. 6.30:

$$
\rho SC_Lg=\rho Sg\,\frac{mg}{\tfrac12\rho U_\infty^2S}=\frac{2mg^2}{U_\infty^2}.
$$

Divide by $m$ (Eq. 6.33):

$$
\ddot h+\frac{2g^2}{U_\infty^2}h=0,\qquad\omega_n=\frac{\sqrt2\,g}{U_\infty},\qquad\zeta=0 .
$$

For the F-4C, $\omega_n=\sqrt2\times9.81/178=0.0779$ rad/s and $T=80.6$ s, against $0.0781$ rad/s and $80.7$ s from the full model. The frequency is almost exact; the damping is lost, because constant energy means nothing is dissipated, so this approximation cannot say whether the phugoid is stable.

The same argument reproduces the phugoid eigenvector of §7. To first order Eq. 6.29 gives $U_\infty^2=(U_\infty+u)^2+2gh\approx U_\infty^2+2U_\infty u+2gh$, so $u=-gh/U_\infty$: speed is in antiphase with height. With $h=h_0\cos\omega_nt$, the flight-path angle is $\gamma=\dot h/U_\infty=-\omega_nh_0\sin\omega_nt/U_\infty$, so

$$
\frac{|\gamma|}{|u|/U_\infty}=\frac{\omega_nh_0/U_\infty}{gh_0/U_\infty^2}=\frac{\omega_nU_\infty}{g}=\sqrt2,
$$

with $u$ leading $\gamma$ by $90^\circ$. The full F-4C eigenvector gives 1.414 and $95.7^\circ$.

### The improved approximation (6.34–6.38)

The improved approximation simplifies the linearised equations instead. It assumes level trim ($\gamma_0=0$), $\dot q=0$ (the pitching moment is in quasi-static balance, as found at the end of §7), and $\mathring Z_q=\mathring Z_{\dot w}=\mathring M_q=\mathring M_{\dot w}=0$. Eq. 6.1 becomes (Eq. 6.34)

$$
\begin{bmatrix}m&0&0&0\\0&m&0&0\\0&0&J_{yy}&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\dot u\\\dot w\\0\\\dot\theta\end{bmatrix}=\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\\\mathring Z_u&\mathring Z_w&mU_\infty&0\\\mathring M_u&\mathring M_w&0&0\\0&0&1&0\end{bmatrix}\begin{bmatrix}u\\w\\q\\\theta\end{bmatrix}.
$$

$J_{yy}$ multiplies $\dot q=0$ and drops out. Row 4 says $q=\dot\theta$, so $q$ is replaced by $\dot\theta$ in row 2 and row 4 is removed (Eq. 6.35). Moving $mU_\infty\dot\theta$ to the left puts the system in the form $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$ in $[u,w,\theta]$ (Eq. 6.36):

$$
\begin{bmatrix}m&0&0\\0&m&-mU_\infty\\0&0&0\end{bmatrix}\begin{bmatrix}\dot u\\\dot w\\\dot\theta\end{bmatrix}=\begin{bmatrix}\mathring X_u&\mathring X_w&-mg\\\mathring Z_u&\mathring Z_w&0\\\mathring M_u&\mathring M_w&0\end{bmatrix}\begin{bmatrix}u\\w\\\theta\end{bmatrix}.
$$

Row 3 is the moment balance $0=\mathring M_uu+\mathring M_ww$. Set $u=u_0e^{\lambda t}$, $w=w_0e^{\lambda t}$, $\theta=\theta_0e^{\lambda t}$ and collect on the left (Eq. 6.37):

$$
\begin{bmatrix}m\lambda-\mathring X_u&-\mathring X_w&mg\\-\mathring Z_u&m\lambda-\mathring Z_w&-mU_\infty\lambda\\-\mathring M_u&-\mathring M_w&0\end{bmatrix}\begin{bmatrix}u_0\\w_0\\\theta_0\end{bmatrix}=\mathbf 0 .
$$

Expanding along row 3, which has a zero in the last place, keeps the algebra short. The cofactor signs for (3,1) and (3,2) are $+$ and $-$:

$$
\det=(-\mathring M_u)\begin{vmatrix}-\mathring X_w&mg\\m\lambda-\mathring Z_w&-mU_\infty\lambda\end{vmatrix}-(-\mathring M_w)\begin{vmatrix}m\lambda-\mathring X_u&mg\\-\mathring Z_u&-mU_\infty\lambda\end{vmatrix}.
$$

The first $2\times2$ is

$$
(-\mathring X_w)(-mU_\infty\lambda)-mg\left(m\lambda-\mathring Z_w\right)=mU_\infty\mathring X_w\lambda-m^2g\lambda+mg\mathring Z_w .
$$

The second is

$$
\left(m\lambda-\mathring X_u\right)(-mU_\infty\lambda)-mg(-\mathring Z_u)=-m^2U_\infty\lambda^2+mU_\infty\mathring X_u\lambda+mg\mathring Z_u .
$$

Substitute both:

$$
\det=-\mathring M_u\left(mU_\infty\mathring X_w\lambda-m^2g\lambda+mg\mathring Z_w\right)+\mathring M_w\left(-m^2U_\infty\lambda^2+mU_\infty\mathring X_u\lambda+mg\mathring Z_u\right).
$$

Group by powers of $\lambda$:

$$
\det=-m^2U_\infty\mathring M_w\lambda^2+m\left(-U_\infty\mathring M_u\mathring X_w+mg\mathring M_u+U_\infty\mathring M_w\mathring X_u\right)\lambda-mg\left(\mathring M_u\mathring Z_w-\mathring M_w\mathring Z_u\right).
$$

Set it to zero and divide by $-m^2U_\infty\mathring M_w$:

$$
\lambda^2+\frac{U_\infty\mathring M_u\mathring X_w-mg\mathring M_u-U_\infty\mathring M_w\mathring X_u}{mU_\infty\mathring M_w}\lambda+\frac{g\left(\mathring M_u\mathring Z_w-\mathring M_w\mathring Z_u\right)}{mU_\infty\mathring M_w}=0 .
$$

Split the $\lambda$ coefficient term by term:

$$
\frac{U_\infty\mathring M_u\mathring X_w-mg\mathring M_u-U_\infty\mathring M_w\mathring X_u}{mU_\infty\mathring M_w}=\frac1m\left[\frac{\mathring M_u}{\mathring M_w}\left(\mathring X_w-\frac{mg}{U_\infty}\right)-\mathring X_u\right].
$$

Matching with $\lambda^2+2\zeta\omega_n\lambda+\omega_n^2=0$ gives Eq. 6.38:

$$
\boxed{\omega_n^2=\frac{g}{mU_\infty}\left(\frac{\mathring M_u\mathring Z_w}{\mathring M_w}-\mathring Z_u\right),\qquad
\zeta=\frac{1}{2\omega_n}\,\frac1m\left[\frac{\mathring M_u}{\mathring M_w}\left(\mathring X_w-\frac{mg}{U_\infty}\right)-\mathring X_u\right].}
$$

For the F-4C the bracket in $\omega_n^2$ is $817.5+1214.0=2031.6$ kg/s, so

$$
\omega_n^2=\frac{9.81}{17642\times178}\times2031.6=6.346\times10^{-3}\ \text{s}^{-2},\qquad\omega_n=0.0797\ \text{rad/s}.
$$

The $\lambda$ coefficient is $2\zeta\omega_n=-0.00072+0.00864+0.00719=0.01511$ s⁻¹, so $\zeta=0.01511/(2\times0.0797)=0.0949$. These are the handout's $\omega_n=0.0796$ and $\zeta=0.0949$, against $0.0781$ and $0.0825$ for the full model (roots $-0.00756\pm0.0793j$ against $-0.00645\pm0.0779j$). The same roots come from a numerical $3\times3$ determinant, and Eq. 6.38 was confirmed symbolically.

> [!tip] How the two approximations connect
> With $\mathring M_u=0$ and a lift that changes with speed at fixed $C_L$, Eq. 6.38 reduces to Lanchester's result. At fixed $C_L$, $Z_a\approx-\tfrac12\rho U^2SC_L$, so $\mathring Z_u=-\rho U_\infty SC_L=-2mg/U_\infty$, and then $\omega_n^2=(g/mU_\infty)(2mg/U_\infty)=2g^2/U_\infty^2$. For the F-4C $2mg/U_\infty=1944.6$ kg/s, while $-\mathring Z_u$ is only 1214.0; the speed-stability term $\mathring M_u\mathring Z_w/\mathring M_w=817.5$ makes up the difference, which is why Lanchester's frequency still lands within 0.3 %. The damping, $-\mathring X_u/m$ plus the $\mathring M_u$ terms, is exactly what the constant-energy argument leaves out.

## 10. Common mistakes

Most errors in this chain are bookkeeping rather than physics:

- dropping $mU_\infty q$ as if it were a product of two perturbations; $U$ has a trim value, so $qU$ is first order;
- leaving $\mathring Z_{\dot w}\dot w$ or $\mathring M_{\dot w}\dot w$ on the right, so a derivative sits inside the "state matrix"; both go into $\mathbf M$;
- writing $\mathbf A=\mathbf A'\mathbf M^{-1}$, or forgetting the (3,2) entry of $\mathbf M^{-1}$, which carries almost a third of the F-4C's pitch damping in $\mathbf A$;
- using $\gamma$ and $\theta$ interchangeably after the disturbance: $\gamma=\theta-\alpha$, equal to $\theta$ only at trim and, nearly, in the phugoid;
- reading the imaginary part of $\lambda$ as $\omega_n$ (it is $\omega_n\sqrt{1-\zeta^2}$);
- comparing eigenvector entries in mixed units, which makes $w$ look dominant in both modes; convert to $u/U_\infty$, $w/U_\infty$ and $\theta$ first;
- expecting the phugoid half-life from Lanchester's approximation, which has $\zeta=0$ by construction.

## Links

- Parent: [[SESA3047 Advanced Aerospace Mechanics & Control Hub]]
- Lecture notes: [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]] (the starting model) · [[SESA3047 5.1 - State-Space Form and Linearisation]] (the $\epsilon$ method and Eqs. 5.7–5.8) · [[SESA3047 5.2 - Longitudinal State-Space Model]] (gravity, derivatives, Eq. 5.18) · [[SESA3047 5.4 - Time-Domain Solution and Stability]] (eigenvalues and stability) · [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]] (the Eq. 6.4 example, Eqs. 6.13–6.27)
- Companion deep dive: [[SESA3047 Deep Dive - Euler-Angle Rates and Gimbal Lock]] (the $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ row of the 6-DOF model)
- Concepts: [[Six-Degree-of-Freedom State Model]] · [[Linearisation about an Equilibrium Point]] · [[Longitudinal and Lateral Dynamics]] · [[Aerodynamic Stability Derivatives]] · [[Eigenvectors as Mode Shapes]] · [[Matrix Exponential and Modal Solution]] · [[Damping Ratio and Natural Frequency]] · [[Short Period Oscillation]] · [[Phugoid Mode]]
- Earlier years: [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]] · [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]
- Formulae: [[SESA3047 Formula Sheet#Longitudinal modes and eigenvectors]]

## Sources

- `Chapter_4.pdf` (Dr Cristiano Martinelli), §4.3, Eqs. 4.41–4.42: the 6-DOF model. Shown at the end of L13 (Thu 22 Oct), `L13 - SESA3047.txt` ll. 310–344.
- `Chapter_5.pdf` (Dr Sean Symon), §§5.2–5.3, Eqs. 5.2–5.18, and the appendix Eqs. 5.51–5.56. Lectured in L14 (Mon 2 Nov, `02 November 2026 at 11_53_51.txt`: force linearisation ll. 236–317, gravity ll. 373–509) and L15 (Thu 5 Nov, `05 November 2026 at 14_53_19.txt`: derivatives and assembly ll. 1–308).
- `05 November 2026 at 15_56_57.txt` (L16): the matrix exponential and stability from the eigenvalues, ll. 148–311.
- `Lecture Notes - Chapter 6.pdf` (Dr Sean Symon), §§6.1–6.6, Eqs. 6.1–6.38 and Table 6.1. §§6.1–6.4 lectured in L17 (Mon 9 Nov, `09 November 2026 at 11_54_07.txt`, ll. 62–392); §6.5 set as reading (ll. 395–400); §6.6 due on Mon 16 Nov (ll. 401–403) and covered here from the handout.
- Computation: `generate_amc_deepdive_figures.py` in `01 - Notes/Figures/` (`--check` prints and asserts every number in this note: dimensional derivatives, $\mathbf M^{-1}$, $\mathbf A$, the quartic and its exact and approximate factors, the by-hand eigenvectors, phases, heights and energies, the SPO and phugoid approximations, Eq. 6.38 symbolically, the Jacobian of the nonlinear model and the nonlinear-versus-linear runs).

## Self-study tasks

Tasks citing a line were worked or flagged in the lectures; the longitudinal derivation is flagged as likely exam material (L15 l. 307). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L14 ll. 236–317, 373–509)** Linearise the $U$ and $W$ force rows and the gravity components about steady straight flight at $\gamma_0$, showing the trim balance cancel and which products survive, including the $\phi$ factor in the $Z$ gravity term. → [[#2. Small perturbations and what survives (5.4–5.15)|§2]]
- [ ] **(L15 ll. 85–255; exam flag l. 307)** Add Eq. 5.16 and assemble $\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x$; then invert the lower-triangular $\mathbf M$ and find $A_{31}$ for the F-4C. → [[#4. Assembling M ẋ = A′x (5.17–5.18)|§4]] and [[#5. From A′ to A for the F-4C (6.3)|§5]]
- [ ] **(L17 ll. 73–96)** From the F-4C eigenvalues find $\omega_n$, $\zeta$, $t_{1/2}$ and $T$ for each mode and say which is which. → [[#6. The characteristic equation and its two quadratics (6.5–6.12)|§6]]
- [ ] **(L17 ll. 298–321; handout pp. 3–4)** Read the F-4C eigenvectors in angle units and describe each mode in words, including $\gamma=\theta-\alpha$. → [[#7. Eigenvectors by hand and the mode shapes (6.17–6.21)|§7]]
- [ ] **(L17 ll. 132–142, 397–400)** Find the SPO roots of $\mathbf A_{\text{SPO}}$ by trace and determinant, and name the derivative behind each term. → [[#8. The SPO approximation and what sets it (6.22–6.27)|§8]]

### Further practice

- [ ] **(L17 ll. 401–403; due Mon 16 Nov)** Derive Lanchester's $\omega_n=\sqrt2g/U_\infty$ and Eq. 6.38, and evaluate both for the F-4C. → [[#9. The phugoid approximations (written ahead)|§9]]
- [ ] (suggested, not lecturer-set) Find the SPO eigenvector of the F-4C by hand from rows 1, 2 and 4 with $\theta=1$, and check row 3. → [[#7. Eigenvectors by hand and the mode shapes (6.17–6.21)|§7]]
- [ ] (suggested, not lecturer-set) Derive the approximate quadratic factors $b_1\approx a_3$, $b_0\approx a_2$, $c_0\approx a_0/a_2$, $c_1\approx(a_1a_2-a_0a_3)/a_2^2$ and recover Eq. 6.10. → [[#Why the quartic splits into two quadratics]]
- [ ] (suggested, not lecturer-set) Code the nonlinear longitudinal rows of §1 and confirm that their Jacobian at trim is $\mathbf A$. → [[#5. From A′ to A for the F-4C (6.3)|§5]]

## Transcript and slide slips

> [!warning] Handout slips in §6.6 (`Lecture Notes - Chapter 6.pdf`, p. 7)
> Where: [[#9. The phugoid approximations (written ahead)]].
>
> - *"It should be noted that $U\le U_\infty$ as kinetic energy is being transferred to potential energy during the instability."* With $h$ measured from the trim height, $h$ is negative for half of each cycle and then $U>U_\infty$. The phugoid is also not an instability in general: the F-4C's has $\zeta=0.083$ and Lanchester's has $\zeta=0$.
> - *"At some point the aircraft does not have enough airspeed to maintain lift which results in the aircraft stalling."* The approximation holds $\alpha$ and $C_L$ fixed, and the full eigenvector confirms $\alpha$ changes by only 0.1 rad per rad of $\theta$. Lift falls below weight because the speed falls at constant $C_L$; nothing stalls.
> - Eq. 6.32 treats the lift as vertical, which needs the flight-path angle to stay small; the handout does not state it.
>
> None of these changes Eqs. 6.33 or 6.38.

### Rounding in Eq. 6.22

Where: [[#4. Assembling M ẋ = A′x (5.17–5.18)]].

Eq. 6.22 prints the dimensional derivatives rounded to integers ($\mathring Z_{\dot w}$ appears only through $m-\mathring Z_{\dot w}=17660$, and $\mathring M_{\dot w}$ as 132). The eigenvalues quoted in §6.5 come from the unrounded values; the rounded matrix gives $-0.3687\pm1.3559j$ and $-0.00645\pm0.07785j$, a change in the fourth significant figure.
