---
title: "SESA3047 Formula Sheet"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: formula
aliases: ["SESA3047 formulae", "Advanced Mechanics and Control formula sheet"]
tags: [sesa3047, formula, exam-prep]
status: in-progress
coverage: "Chapters 1–5 lectured in full (L2–L16); Chapter 6 §§6.1–6.5 from L17 (Mon 9 Nov); §6.6 phugoid approximations from L18 (Mon 16 Nov)"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter-3.pdf", "02 - Sources/Lectures/Chapter_4.pdf", "02 - Sources/Lectures/Chapter_5.pdf", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/L11 - SESA3047.txt", "02 - Sources/Lectures/L12 - SESA3047.txt", "02 - Sources/Lectures/L13 - SESA3047.txt", "02 - Sources/Lectures/02 November 2026 at 11_53_51.txt", "02 - Sources/Lectures/09 November 2026 at 11_54_07.txt", "02 - Sources/Lectures/16 November 2026 at 11_51_48.txt"]
---

# SESA3047 Formula Sheet

Current coverage: **Chapters 1–5 and Chapter 6 §§6.1–6.6**. Chapter 4 was lectured in full (L11–L13, 19 and 22 Oct), Chapter 5 in L14–L16 (2 and 5 Nov), Chapter 6 §§6.1–6.4 in L17; §6.5 was set as reading; §6.6 was lectured in L18 (Mon 16 Nov). Handout-only pieces are marked where they appear. The official exam formula sheet goes on Blackboard in mid-November 2026.

## Control-system notation

For negative feedback,

$$
e=r-y_m.
$$

| Symbol | Meaning |
|---|---|
| $r$ | reference input |
| $e$ | error signal |
| $u_c$ | controller output / control signal |
| $y$ | plant output |
| $y_m$ | measured output / feedback signal |
| $d$ | external disturbance |

## Oscillator model examples

Nonlinear:

$$
m\ddot x+c\dot x+kx+\mu x^3=0.
$$

Linear local approximation:

$$
m\ddot x+c\dot x+kx=0.
$$

Linear time varying:

$$
m\ddot x+c\dot x+k(t)x=0,
\qquad k(t)=k_0+\Delta k(t).
$$

## Local linearisation

For $\dot{\mathbf x}=\mathbf f(\mathbf x,\mathbf u)$ around a **trim (equilibrium) point** $(\mathbf x_0,\mathbf u_0)$ with $\mathbf f(\mathbf x_0,\mathbf u_0)=\mathbf 0$, $\delta\mathbf x=\mathbf x-\mathbf x_0$, $\delta\mathbf u=\mathbf u-\mathbf u_0$. (About a time-varying reference, require $\dot{\mathbf x}_0(t)=\mathbf f(\mathbf x_0,\mathbf u_0)$ instead; otherwise a constant residual $\mathbf f(\mathbf x_0,\mathbf u_0)$ is left over.)

$$
\delta\dot{\mathbf x}
\approx
\mathbf A\,\delta\mathbf x+
\mathbf B\,\delta\mathbf u,
$$

$$
\mathbf A=\left.\frac{\partial\mathbf f}{\partial\mathbf x}\right|_0,
\qquad
\mathbf B=\left.\frac{\partial\mathbf f}{\partial\mathbf u}\right|_0.
$$

## Vector and frame notation

$$
\mathbf p_{A/B}=\text{position of point }A\text{ relative to }B,
$$

$$
\mathbf v_{A/i}=\text{velocity of point }A\text{ relative to frame }F_i,
$$

$$
\mathbf v^c=\text{components of }\mathbf v\text{ in coordinates }c,\qquad {}^b\dot{\mathbf v}=\text{derivative observed from }F_b.
$$

## Flat-Earth assumptions

$$
\boldsymbol\omega_{e/i}=\mathbf 0,
\qquad
\text{Earth curvature neglected},
\qquad
g=\text{constant}.
$$

In local NED coordinates,

$$
\mathbf g^{NED}=\begin{bmatrix}0\\0\\g\end{bmatrix}.
$$

## Coordinate axes

| Coordinates | $x$ | $y$ | $z$ | Typical use |
|---|---|---|---|---|
| NED | north | east | down | local position, ground velocity, gravity |
| FRD | forward | right | down | body forces, body velocity, angular velocity |

## Vector operations

$$
\mathbf u\cdot\mathbf v=|\mathbf u||\mathbf v|\cos\alpha=\mathbf u^T\mathbf v,
\qquad
\mathbf u\times\mathbf v=|\mathbf u||\mathbf v|\sin\alpha\,\mathbf n=\begin{bmatrix}u_yv_z-u_zv_y\\u_zv_x-u_xv_z\\u_xv_y-u_yv_x\end{bmatrix}.
$$

Cross-product matrix (skew matrix, the tilde notation):

$$
\mathbf u\times\mathbf v=\tilde{\mathbf u}\mathbf v,\qquad
\tilde{\mathbf u}=\begin{bmatrix}0&-u_z&u_y\\u_z&0&-u_x\\-u_y&u_x&0\end{bmatrix},\qquad
\tilde{\mathbf u}^T=-\tilde{\mathbf u},\qquad
\tilde{\boldsymbol\omega}^2=\boldsymbol\omega\boldsymbol\omega^T-\omega^2\mathbf I.
$$

Triple products:

$$
\mathbf u\cdot(\mathbf v\times\mathbf w)=\mathbf v\cdot(\mathbf w\times\mathbf u)=\mathbf w\cdot(\mathbf u\times\mathbf v),
\qquad
\mathbf u\times(\mathbf v\times\mathbf w)=\mathbf v(\mathbf u\cdot\mathbf w)-\mathbf w(\mathbf u\cdot\mathbf v).
$$

Circular motion: $\mathbf v=\boldsymbol\omega\times\mathbf r$, $\mathbf a_c=\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)=-\omega^2\mathbf r$ for $\boldsymbol\omega\perp\mathbf r$.

## Angular velocity and the transport theorem

$$
\boldsymbol\omega_{b/a}=-\boldsymbol\omega_{a/b},\qquad
\boldsymbol\omega_{c/a}=\boldsymbol\omega_{c/b}+\boldsymbol\omega_{b/a},\qquad
{}^a\dot{\boldsymbol\omega}_{b/a}={}^b\dot{\boldsymbol\omega}_{b/a}.
$$

$$
\boxed{{}^a\dot{\mathbf p}={}^b\dot{\mathbf p}+\boldsymbol\omega_{b/a}\times\mathbf p}
\qquad\text{(fixed in }F_b\text{: }{}^a\dot{\mathbf p}=\boldsymbol\omega_{b/a}\times\mathbf p\text{)}
$$

Rigid body: $\mathbf v_P=\mathbf v_Q+\boldsymbol\omega\times\mathbf p$.

## Direction cosine matrices

$$
\mathbf u^b=\mathbf C_{b/a}\mathbf u^a,\qquad C_{ij}=\mathbf b_i\cdot\mathbf a_j,\qquad
\mathbf C^{-1}=\mathbf C^T,\qquad \det\mathbf C=1,\qquad
\mathbf C_{d/a}=\mathbf C_{d/c}\mathbf C_{c/b}\mathbf C_{b/a}.
$$

$$
\mathbf C_x(\phi)=\begin{bmatrix}1&0&0\\0&c_\phi&s_\phi\\0&-s_\phi&c_\phi\end{bmatrix},\quad
\mathbf C_y(\theta)=\begin{bmatrix}c_\theta&0&-s_\theta\\0&1&0\\s_\theta&0&c_\theta\end{bmatrix},\quad
\mathbf C_z(\psi)=\begin{bmatrix}c_\psi&s_\psi&0\\-s_\psi&c_\psi&0\\0&0&1\end{bmatrix}.
$$

## Aerospace 3-2-1 Euler angles

$$
\mathbf C_{FRD/NED}=\mathbf C_x(\phi)\mathbf C_y(\theta)\mathbf C_z(\psi)=
\begin{bmatrix}
c_\theta c_\psi & c_\theta s_\psi & -s_\theta\\
-c_\phi s_\psi+s_\phi s_\theta c_\psi & c_\phi c_\psi+s_\phi s_\theta s_\psi & s_\phi c_\theta\\
s_\phi s_\psi+c_\phi s_\theta c_\psi & -s_\phi c_\psi+c_\phi s_\theta s_\psi & c_\phi c_\theta
\end{bmatrix}.
$$

$$
\mathbf u^{FRD}=\mathbf C_{FRD/NED}\mathbf u^{NED},\qquad
\mathbf u^{NED}=\mathbf C_{FRD/NED}^T\mathbf u^{FRD},\qquad
\mathbf g^{FRD}=g\begin{bmatrix}-s_\theta\\s_\phi c_\theta\\c_\phi c_\theta\end{bmatrix}.
$$

Extraction (singular at $\theta=\pm90^\circ$):

$$
\phi=\mathrm{atan2}(C_{23},C_{33}),\qquad \theta=-\arcsin C_{13},\qquad \psi=\mathrm{atan2}(C_{12},C_{11}).
$$

$\mathrm{atan2}(y,x)\in(-\pi,\pi]$ uses the signs of both arguments; $\arctan(y/x)\in(-\pi/2,\pi/2)$ cannot tell $(y,x)$ from $(-y,-x)$. At $\theta=\pm90^\circ$ both atan2 calls become $\mathrm{atan2}(0,0)$ ([[Gimbal Lock]]); libraries return 0 silently.

Notation: $\mathbf p_{A/B}$ (of $A$ relative to $B$), $(\cdot)^c$ (components in coordinates $c$), ${}^b\dot{(\cdot)}$ (derivative observed from $F_b$).

## Rotational kinematics

Body rates $\boldsymbol\omega^{FRD}_{b/r}=[p,q,r]^T$; Euler angles $\boldsymbol\Phi=[\phi,\theta,\psi]^T$.

$$
\boldsymbol\omega^{FRD}_{b/r}=\begin{bmatrix}\dot\phi\\0\\0\end{bmatrix}+\mathbf C_x(\phi)\left(\begin{bmatrix}0\\\dot\theta\\0\end{bmatrix}+\mathbf C_y(\theta)\begin{bmatrix}0\\0\\\dot\psi\end{bmatrix}\right)=\mathbf E(\boldsymbol\Phi)\dot{\boldsymbol\Phi}\ \ (\text{kinematic transformation matrix}),\qquad
\mathbf E=\begin{bmatrix}1&0&-s_\theta\\0&c_\phi&s_\phi c_\theta\\0&-s_\phi&c_\phi c_\theta\end{bmatrix}.
$$

$$
\dot{\boldsymbol\Phi}=\mathbf H(\boldsymbol\Phi)\,\boldsymbol\omega^{FRD}_{b/r}\ \ (\text{transform matrix}),\qquad
\mathbf H=\begin{bmatrix}1&s_\phi\tan\theta&c_\phi\tan\theta\\0&c_\phi&-s_\phi\\0&s_\phi/c_\theta&c_\phi/c_\theta\end{bmatrix},\qquad\det\mathbf E=\cos\theta.
$$

$$
\dot\phi=p+(q s_\phi+r c_\phi)\tan\theta,\qquad\dot\theta=qc_\phi-rs_\phi,\qquad\dot\psi=\frac{qs_\phi+rc_\phi}{c_\theta}.
$$

Small angles: $\dot\phi\approx p$, $\dot\theta\approx q$, $\dot\psi\approx r$. Flat Earth: $\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/e}=\boldsymbol\omega_{b/i}$; rotating Earth: $\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/i}-\boldsymbol\omega_{r/i}$. Coupling check: $r=0$, $\theta=0$ gives $\dot\theta=q\cos\phi$, $\dot\psi=q\sin\phi$. Level turn: $\dot\psi=g\tan\phi/V$, $q=\dot\psi\sin\phi$, $r=\dot\psi\cos\phi$.

Structure and singularity ([[SESA3047 Deep Dive - Euler-Angle Rates and Gimbal Lock|deep dive]]): $\mathbf E=\big[\mathbf e_1\ \big|\ \mathbf C_x\mathbf e_2\ \big|\ \mathbf C_x\mathbf C_y\mathbf e_3\big]=\mathbf C_x(\phi)\,\mathbf E_\theta$ with $\mathbf E_\theta=\begin{bmatrix}1&0&-s_\theta\\0&1&0\\0&0&c_\theta\end{bmatrix}$, so $\mathbf H=\mathbf E_\theta^{-1}\mathbf C_x^T$ and $\mathbf H=\operatorname{adj}\mathbf E/\cos\theta$. At $\theta=\pm90^\circ$: rank 2, null space $[1,0,\pm1]^T$ (equal or opposite $\dot\phi$, $\dot\psi$ give no rotation), missing axis $\mathbf x_1=[0,s_\phi,c_\phi]^T$ in FRD, body-rate component about it $q\sin\phi+r\cos\phi$.

$$
\dot\phi-\dot\psi=p-(q\sin\phi+r\cos\phi)\frac{\cos\theta}{1+\sin\theta}\ \ (\text{finite at }\theta=90^\circ),\qquad\sigma_{max}(\mathbf H)=\frac{1}{\sqrt{1-|\sin\theta|}}\approx\frac{\sqrt2}{\delta},\ \ \delta=90^\circ-|\theta|\ \text{in rad}.
$$

## Velocity and acceleration in moving frames

$$
\mathbf v_{P/a}=\mathbf v_{P/b}+\mathbf v_{Q/a}+\boldsymbol\omega_{b/a}\times\mathbf p_{P/Q},
$$

$$
\mathbf a_{P/a}=\mathbf a_{P/b}+\mathbf a_{Q/a}+\boldsymbol\alpha_{b/a}\times\mathbf p_{P/Q}+\boldsymbol\omega_{b/a}\times(\boldsymbol\omega_{b/a}\times\mathbf p_{P/Q})+2\boldsymbol\omega_{b/a}\times\mathbf v_{P/b}.
$$

Rotating Earth: $m\mathbf a_{P/e}=\sum\mathbf F_{real}-m\boldsymbol\omega_{e/i}\times(\boldsymbol\omega_{e/i}\times\mathbf p)-2m\boldsymbol\omega_{e/i}\times\mathbf v_{P/e}$, $\Omega=7.292\times10^{-5}$ rad/s. Flat Earth: $\mathbf a_{P/i}=\mathbf a_{P/e}$.

Body-axis acceleration:

$$
\mathbf a^{FRD}_{cm/e}={}^b\dot{\mathbf v}+\boldsymbol\omega\times\mathbf v=\begin{bmatrix}\dot u+qw-rv\\\dot v+ru-pw\\\dot w+pv-qu\end{bmatrix}.
$$

Translational kinematic equation:

$$
\dot{\mathbf p}^{NED}_{cm/Q}=\begin{bmatrix}\dot x\\\dot y\\\dot z\end{bmatrix}=\mathbf C^T_{FRD/NED}\begin{bmatrix}u\\v\\w\end{bmatrix}.
$$

## Rigid-body dynamics

$$
\mathbf Q=m\mathbf v_{cm/i},\qquad\sum\mathbf F_{ext}=m\,\mathbf a_{cm/i}.
$$

$$
\mathbf h^{FRD}_{cm/i}=\mathbf J^{FRD}\boldsymbol\omega^{FRD}_{b/i},\qquad
\mathbf J=-\int_B\tilde{\mathbf r}^{\,2}\mathrm dm=\begin{bmatrix}J_{xx}&-J_{xy}&-J_{xz}\\-J_{xy}&J_{yy}&-J_{yz}\\-J_{xz}&-J_{yz}&J_{zz}\end{bmatrix},
$$

with $J_{xx}=\int(y^2+z^2)\mathrm dm$ (and cyclic) and $J_{xy}=\int xy\,\mathrm dm$ (and cyclic).

Rotational dynamic equation (lectured form 3.70, then solved, 3.71):

$$
\sum\mathbf M_{cm}=\mathbf J\,{}^b\dot{\boldsymbol\omega}+\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega,
\qquad
{}^b\dot{\boldsymbol\omega}=\mathbf J^{-1}\left(\sum\mathbf M_{cm}-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega\right).
$$

Conditions: moments about the **cm** ($\int_B\mathbf r\,\mathrm dm=\mathbf 0$ by definition there); $\mathbf J$ in **body** axes and the body **rigid**, so $\dot{\mathbf J}=\mathbf 0$.

Principal axes (Euler's equations; $J_x\equiv J_{xx}$ etc., the Lab 1 and Coursework 1 notation): $J_x\dot p=L+(J_y-J_z)qr$, $J_y\dot q=M+(J_z-J_x)rp$, $J_z\dot r=N+(J_x-J_y)pq$.

Aircraft ($J_{xy}=J_{yz}=0$):

$$
L=J_x\dot p-J_{xz}\dot r+(J_z-J_y)qr-J_{xz}pq,\quad
M=J_y\dot q+(J_x-J_z)pr+J_{xz}(p^2-r^2),\quad
N=J_z\dot r-J_{xz}\dot p+(J_y-J_x)pq+J_{xz}qr.
$$

These Chapter 3 equations supply nine of the twelve state derivatives; the velocity dynamics supply the rest (assembled below).

## Principal axes, aircraft inverse and rotors

Sources: L11 (full-inertia expansion, principal axes), L12 (inertia coupling, aircraft symmetry, rotors), L13 (aircraft rotor terms).

$$
\mathbf J\mathbf e_i=\lambda_i\mathbf e_i,\quad
\mathbf Q=[\mathbf e_1\ \mathbf e_2\ \mathbf e_3],\quad
\mathbf J_P=\mathbf Q^T\mathbf J_B\mathbf Q=\operatorname{diag}(\lambda_i).
$$

Inertia coupling, principal axes, no external moment:

$$
\dot p=\frac{(J_{yy}-J_{zz})qr}{J_{xx}},\qquad
\dot q=\frac{(J_{zz}-J_{xx})pr}{J_{yy}},\qquad
\dot r=\frac{(J_{xx}-J_{yy})pq}{J_{zz}}.
$$

Each rate's derivative needs **both other rates** non-zero **and** its inertia difference non-zero. With two non-zero rates, initially only the third rate changes (unless its inertia difference is zero, e.g. $J_{xx}=J_{zz}$ kills $\dot q$); the others can change later, once the third rate has grown. A single-axis spin stays steady.

For aircraft symmetry $J_{xy}=J_{yz}=0$:

$$
\Gamma=J_{xx}J_{zz}-J_{xz}^2,\qquad
\mathbf J^{-1}=\frac1\Gamma
\begin{bmatrix}J_{zz}&0&J_{xz}\\0&\Gamma/J_{yy}&0\\J_{xz}&0&J_{xx}\end{bmatrix}.
$$

$$
R_L=L-(J_{zz}-J_{yy})qr+J_{xz}pq,\qquad
R_N=N-(J_{yy}-J_{xx})pq-J_{xz}qr.
$$

$$
\dot p=(J_{zz}R_L+J_{xz}R_N)/\Gamma,\qquad
\dot r=(J_{xz}R_L+J_{xx}R_N)/\Gamma,
$$

$$
\dot q=[M+(J_{zz}-J_{xx})pr-J_{xz}(p^2-r^2)]/J_{yy}.
$$

Internal rotor momentum, with locked assembly inertia included in $\mathbf J$:

$$
\mathbf h=\mathbf J\boldsymbol\omega+\mathbf h_R,\qquad
\dot{\boldsymbol\omega}
=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega
-\tilde{\boldsymbol\omega}\mathbf h_R-{}^b\dot{\mathbf h}_R).
$$

Constant body-frame rotor momentum removes only its body derivative (the lectured case). The last term is handout-only (Eq. 4.25). With ${}^b\dot{\mathbf h}_R=\mathbf 0$:

$$
\dot{\boldsymbol\omega}=\dot{\boldsymbol\omega}_{base}+\dot{\boldsymbol\omega}_{add},\qquad
\dot{\boldsymbol\omega}_{base}=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega),\qquad
\dot{\boldsymbol\omega}_{add}=-\mathbf J^{-1}\tilde{\boldsymbol\omega}\mathbf h_R.
$$

Aircraft $\mathbf J$ (Eq. 4.23):

$$
\begin{aligned}
\dot p_{add}&=\frac{J_{zz}(rh_y-qh_z)+J_{xz}(qh_x-ph_y)}{\Gamma},\\
\dot q_{add}&=\frac{ph_z-rh_x}{J_{yy}},\\
\dot r_{add}&=\frac{J_{xz}(rh_y-qh_z)+J_{xx}(qh_x-ph_y)}{\Gamma}.
\end{aligned}
$$

Principal axes ($J_{xz}=0$): $\dot p_{add}=(rh_y-qh_z)/J_{xx}$, $\dot q_{add}=(ph_z-rh_x)/J_{yy}$, $\dot r_{add}=(qh_x-ph_y)/J_{zz}$.

## Translational dynamics

Lectured in L13 (Thu 22 Oct), except effective gravity and the scalar/$X,Y,Z$ forms. $\mathbf F$ excludes gravity. Rotating Earth (Eq. 4.30, lectured):

$$
\mathbf a_{cm/e}=\mathbf F/m+\mathbf G-\boldsymbol\omega_{e/i}\times(\boldsymbol\omega_{e/i}\times\mathbf p)-2\boldsymbol\omega_{e/i}\times\mathbf v_{cm/e}.
$$

Effective gravity (Eq. 4.31, handout only):

$$
\mathbf g=\mathbf G-\boldsymbol\omega_{e/i}\times(\boldsymbol\omega_{e/i}\times\mathbf p),\qquad
\mathbf a_{cm/e}=\mathbf F/m+\mathbf g-2\boldsymbol\omega_{e/i}\times\mathbf v_{cm/e}.
$$

Flat Earth: $\boldsymbol\omega_{e/i}=\mathbf 0$, local NED inertial, $\mathbf g^{NED}=[0,0,g]^T$, $g=9.81$ m/s².

$$
\boxed{\dot{\mathbf v}
=\mathbf F^{FRD}/m+\mathbf C_{FRD/NED}\mathbf g^{NED}
-\tilde{\boldsymbol\omega}\mathbf v.}
$$

$$
\begin{aligned}
\dot u&=F_x/m-g\sin\theta+rv-qw,\\
\dot v&=F_y/m+g\sin\phi\cos\theta+pw-ru,\\
\dot w&=F_z/m+g\cos\phi\cos\theta+qu-pv.
\end{aligned}
$$

If $[X,Y,Z]^T$ includes weight instead (handout only, Eqs. 4.38–4.40):

$$
X=m(\dot u+qw-rv),\quad
Y=m(\dot v+ru-pw),\quad
Z=m(\dot w+pv-qu).
$$

Do not add explicit gravity to that second convention.

## Complete flat-Earth model

$$
\mathbf x=[x,y,z,\phi,\theta,\psi,u,v,w,p,q,r]^T,
$$

$$
\boxed{\begin{aligned}
\dot{\mathbf p}^{NED}&=\mathbf C^T\mathbf v,\\
\dot{\boldsymbol\Phi}&=\mathbf H(\boldsymbol\Phi)\boldsymbol\omega,\\
\dot{\mathbf v}&=\mathbf F/m+\mathbf C\mathbf g^{NED}-\tilde{\boldsymbol\omega}\mathbf v,\\
\dot{\boldsymbol\omega}&=\mathbf J^{-1}(\mathbf M-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega).
\end{aligned}}
$$

Four groups, twelve states (six for the dynamics and six for the kinematics); evaluate together using current-state force and moment models. The baseline last row excludes internal rotors. Assumptions: constant mass/inertia, rigid-body approximation, flat Earth, and $\cos\theta\ne0$. Height relative to the NED origin is $h=-z$.

## State-space form and linearisation

Lectured in L14 (Mon 2 Nov).

$$
\dot{\mathbf x}=\mathbf A\mathbf x+\mathbf B\mathbf u,\qquad\mathbf y=\mathbf C\mathbf x+\mathbf D\mathbf u,
$$

with $\mathbf x$: $n\times1$, $\mathbf u$: $m\times1$, $\mathbf y$: $p\times1$; state matrix $\mathbf A$: $n\times n$, control matrix $\mathbf B$: $n\times m$, output matrix $\mathbf C$: $p\times n$, feedforward matrix $\mathbf D$: $p\times m$. In this module $\mathbf C=\mathbf I$ unless stated and $\mathbf D$ is not used.

Linearising: $x=x_0+\epsilon x_1$ about an equilibrium; keep $\epsilon^1$, drop $\epsilon^2$; the $\epsilon^0$ terms must be the equilibrium and cancel. Example: $\sin(x_0+\epsilon x_1)\approx\epsilon x_1\cos x_0$ when $\sin x_0=0$ ($y=x$ about 0, $y=-(x-\pi)$ about $\pi$).

About $(U,V,W)=(U_\infty,0,0)$, $(p,q,r)=(0,0,0)$, constant $m$, rigid symmetric aircraft ($J_{xy}=J_{yz}=0$), no internal rotors:

$$
X_1=m\dot u_1,\qquad Y_1=m(\dot v_1+r_1U_\infty),\qquad Z_1=m(\dot w_1-q_1U_\infty),\qquad(5.7)
$$

$$
L_1=J_{xx}\dot p_1-J_{xz}\dot r_1,\qquad M_1=J_{yy}\dot q_1,\qquad N_1=-J_{xz}\dot p_1+J_{zz}\dot r_1.\qquad(5.8)
$$

A product survives at first order only if one factor has a non-zero equilibrium value. An internal rotor $\mathbf h_r$ adds first-order $\boldsymbol\omega_1\times\mathbf h_r$ terms to Eq. 5.8.

## Longitudinal state-space model

Gravity (lectured L14), trim climb angle $\gamma_0$, pitch perturbation $\theta_1$, $x$ along $U_\infty$ at trim, radians:

$$
X_{g1}=-mg\,\theta_1\cos\gamma_0,\qquad Z_{g1}=-mg\,\theta_1\sin\gamma_0.\qquad(5.15)
$$

Aerodynamics (lectured L15), ring = dimensional constants, so linear; $\mathring X_q=\mathring X_{\dot w}=0$, no control terms:

$$
\Delta X_a=\mathring X_uu+\mathring X_ww,\quad\Delta Z_a=\mathring Z_uu+\mathring Z_ww+\mathring Z_qq+\mathring Z_{\dot w}\dot w,\quad\Delta M_a=\mathring M_uu+\mathring M_ww+\mathring M_qq+\mathring M_{\dot w}\dot w.\qquad(5.16)
$$

With $\dot\theta=q$ and $\mathbf x=[u,w,q,\theta]^T$:

$$
\begin{bmatrix}m&0&0&0\\0&m-\mathring Z_{\dot w}&0&0\\0&-\mathring M_{\dot w}&J_{yy}&0\\0&0&0&1\end{bmatrix}\dot{\mathbf x}
=\begin{bmatrix}\mathring X_u&\mathring X_w&0&-mg\cos\gamma_0\\\mathring Z_u&\mathring Z_w&\mathring Z_q+mU_\infty&-mg\sin\gamma_0\\\mathring M_u&\mathring M_w&\mathring M_q&0\\0&0&1&0\end{bmatrix}\mathbf x,\qquad(5.18)
$$

i.e. $\mathbf M\dot{\mathbf x}=\mathbf A^\dagger\mathbf x$, so $\mathbf A=\mathbf M^{-1}\mathbf A^\dagger$ (course names). Row 4 of $\mathbf M$ must be $[0,0,0,1]$, otherwise $\det\mathbf M=0$. Gravity gives no pitching moment (it acts at the cm).

Dimensional derivatives (appendix; handout only, not lectured): force $\times\tfrac12\rho U_\infty^2S$, moment $\times\tfrac12\rho U_\infty^2Sc$, then divide by $U_\infty$ ($u,w$), $U_\infty/c$ ($q$) or $U_\infty^2/c$ ($\dot w$):

$$
\mathring Z_u=Z_u\tfrac12\rho U_\infty S,\quad\mathring Z_q=Z_q\tfrac12\rho U_\infty Sc,\quad\mathring Z_{\dot w}=Z_{\dot w}\tfrac12\rho Sc,
$$

$$
\mathring M_u=M_u\tfrac12\rho U_\infty Sc,\quad\mathring M_q=M_q\tfrac12\rho U_\infty Sc^2,\quad\mathring M_{\dot w}=M_{\dot w}\tfrac12\rho Sc^2.\qquad(5.51\text{–}5.56)
$$

Lateral (Practice problem 3, level trim): $\mathbf x=[v,p,r,\phi]^T$, $m\dot v=\mathring Y_vv+\mathring Y_pp+(\mathring Y_r-mU_\infty)r+mg\phi$, $\dot\phi=p$, and the $L$, $N$ rows of Eq. 5.8 equal to $\mathring L_vv+\mathring L_pp+\mathring L_rr$ and $\mathring N_vv+\mathring N_pp+\mathring N_rr$.

## Building state-space models

Lectured L15–L16 (Thu 5 Nov), except the block diagram (§5.6: not lectured, not examinable). Number of states = sum of the highest derivative orders; $\mathbf x$ is always $n\times1$. Inputs go in $\mathbf B\mathbf u$, never in $\mathbf A\mathbf x$. Dimension check: inner sizes of every product agree, $(n\times n)(n\times1)$, $(n\times m)(m\times1)$, $(p\times n)(n\times1)$.

- **Simple lag:** $G=1/(s-T_1)$ $\Rightarrow$ $\dot w=T_1w+r$, $\mathbf A=T_1$, $\mathbf B=1$, $\mathbf C=1$; pole $s=T_1$; free response $w=w_0e^{T_1t}$, unstable for $T_1>0$.
- **Laplace ↔ time (zero initial conditions):** $sW\leftrightarrow\dot w$, $W/s\leftrightarrow\int w\,dt$.
- **Second-order ODEs:** each variable and its rate are states. Satellite (Lab 2), $\mathbf x=[\theta_2,\dot\theta_2,\theta_1,\dot\theta_1]^T$, $u=T_c$, $y=\theta_2$:

$$
\mathbf A=\begin{bmatrix}0&1&0&0\\-k/J_2&-b/J_2&k/J_2&b/J_2\\0&0&0&1\\k/J_1&b/J_1&-k/J_1&-b/J_1\end{bmatrix},\quad\mathbf B=\begin{bmatrix}0\\0\\0\\1/J_1\end{bmatrix},\quad\mathbf C=\begin{bmatrix}1&0&0&0\end{bmatrix},
$$

$$
\frac{\Theta_2}{T_c}=\frac{bs+k}{s^2\big[J_1J_2s^2+(J_1+J_2)(bs+k)\big]}.
$$

- **Transfer function** $N(s)/D(s)$, strictly proper, $D=s^n+a_{n-1}s^{n-1}+\dots+a_0$, $N=b_{n-1}s^{n-1}+\dots+b_0$: states $v,\dot v,\dots$ with $D(s)V=U$;

$$
\mathbf A=\begin{bmatrix}0&1&\cdots&0\\\vdots&&\ddots&\vdots\\0&0&\cdots&1\\-a_0&-a_1&\cdots&-a_{n-1}\end{bmatrix},\quad\mathbf B=\begin{bmatrix}0\\\vdots\\0\\1\end{bmatrix},\quad\mathbf C=\begin{bmatrix}b_0&b_1&\cdots&b_{n-1}\end{bmatrix}.
$$

Only the denominator reaches $\mathbf A$: poles = eigenvalues of $\mathbf A$; zeros sit in $\mathbf C$ (the observation matrix) for this construction. Eq. 5.30: poles $-0.468,-1.653,-3.879$ (Routh column $1,6,8.5,3$), zeros $-0.2\pm0.6j$.

- **Block diagram:** one state per first-order block, $b/(s+a)\Rightarrow\dot x=-ax+b\,(\text{block input})$; replace internal signals ($u_1=K_1(r_1-y_1)$, $y_1=x_1+x_2$) by states and references.

## Time-domain solution and stability

Lectured L16 (Thu 5 Nov). Free system ($\mathbf u=\mathbf 0$), constant $\mathbf A$; matrix first in $e^{\mathbf At}\mathbf x_0$.

$$
\mathbf x(t)=e^{\mathbf At}\mathbf x_0,\qquad e^{\mathbf At}=\mathbf I+\mathbf At+\frac{(\mathbf At)^2}{2!}+\cdots\quad(\text{not element-wise}).
$$

If $\mathbf A=\mathbf V\boldsymbol\Lambda\mathbf V^{-1}$ (diagonalisable, e.g. distinct eigenvalues):

$$
\mathbf x(t)=\mathbf Ve^{\boldsymbol\Lambda t}\mathbf V^{-1}\mathbf x_0=\sum_ic_ie^{\lambda_it}\mathbf v_i.\qquad(5.47)
$$

Asymptotically stable $\iff$ all $\operatorname{Re}\lambda_i<0$; unstable if any $\operatorname{Re}\lambda_i>0$; simple eigenvalues on the imaginary axis are marginal, repeated defective ones (e.g. the satellite's double zero) unstable. For $2\times2$: $\lambda^2-(\operatorname{tr}\mathbf A)\lambda+\det\mathbf A=0$; stable $\iff\operatorname{tr}\mathbf A<0$ and $\det\mathbf A>0$. Poles of $\mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B$ are eigenvalues of $\mathbf A$. $\operatorname{Im}\lambda$ sets the oscillation frequency, $\operatorname{Re}\lambda$ growth or decay.

Eigenvectors: solve $(\mathbf A-\lambda_i\mathbf I)\mathbf v_i=\mathbf 0$, fix one free component (scale and sign arbitrary; MATLAB/Python normalise to unit length); $\mathbf V=[\mathbf v_1\ \cdots\ \mathbf v_n]$ in the same order as $\boldsymbol\Lambda$. Triangular $\mathbf A$ (upper or lower): eigenvalues are the main-diagonal entries. $2\times2$ inverse: $[a\ b;\ c\ d]^{-1}=\frac{1}{ad-bc}[d\ {-b};\ {-c}\ a]$. L16 example: $[3\ 2;\ 0\ {-1}]$, $\lambda=3,-1$, $\mathbf v_1=[1,0]^T$, $\mathbf v_2=[1,-2]^T$, $\mathbf V^{-1}=[1\ \tfrac12;\ 0\ {-\tfrac12}]$, unstable.

## Longitudinal modes and eigenvectors

Lectured L17 (Mon 9 Nov); §6.5 set as reading. States $[u,w,q,\theta]$ (m/s, m/s, rad/s, rad), FRD body axes, trim climb angle $\gamma_0$. Details: [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation|6.1]].

$$
\mathbf M\dot{\mathbf x}=\mathbf A'\mathbf x\ \Rightarrow\ \dot{\mathbf x}=\mathbf A\mathbf x,\qquad\mathbf A=\mathbf M^{-1}\mathbf A'.\qquad(6.3)
$$

The characteristic equation of the longitudinal $\mathbf A$ is the longitudinal stability quartic; it factors approximately into an SPO quadratic and a phugoid quadratic. A real $\mathbf A$ gives real eigenvalues or conjugate pairs, with conjugate eigenvectors. By hand: $2\times2$ only.

For a complex pair $\lambda=\sigma\pm j\omega$ (any $\zeta$ in $0\le\zeta<1$):

$$
\lambda^2+2\zeta\omega_n\lambda+\omega_n^2=0,\qquad\omega_n=|\lambda|=\sqrt{\sigma^2+\omega^2},\qquad\zeta=-\frac{\sigma}{\omega_n},\qquad\omega=\omega_n\sqrt{1-\zeta^2}.\qquad(6.16)
$$

Mass–spring–damper: $\omega_n=\sqrt{k/m}$, $\zeta=c/(2m\omega_n)$. Half-life (only for $\sigma<0$; natural log) and period:

$$
t_{1/2}=\frac{\ln0.5}{\sigma},\qquad T=\frac{2\pi}{\omega}.
$$

$\zeta>1$ over-damped, $\zeta=1$ critical, $0<\zeta<1$ under-damped (overshoots a step), $\zeta=0$ undamped, $\zeta<0$ growing.

Eigenvectors: $(\mathbf A-\lambda\mathbf I)\mathbf v=\mathbf 0$; MATLAB `[V,D] = eig(A)`, unit length $\sqrt{\sum|v_i|^2}=1$, overall phase arbitrary. Start on an eigenvector and only its mode appears:

$$
\mathbf x_0=\mathbf v_k\ \Rightarrow\ \mathbf x(t)=e^{\mathbf At}\mathbf v_k=e^{\lambda_kt}\mathbf v_k;\qquad\mathbf x_0=\mathcal R(\mathbf v_k)\ \Rightarrow\ \mathbf x(t)=\mathcal R\left(e^{\lambda_kt}\mathbf v_k\right).\qquad(6.21)
$$

$|v_i|$ = relative amplitude (compare like units; $\alpha\approx w/U_\infty$), $\arg v_i$ = phase. From $\dot\theta=q$: $\theta=q/\lambda$, so $\theta$ lags $q$ by $90^\circ+\arcsin\zeta$ (decaying oscillation). Level trim: $\dot h=U_\infty\theta-w$. Long-term response is set by the least stable mode.

Eq. 6.4 example: SPO $-0.4988\pm1.3237j$ ($\omega_n=1.414$, $\zeta=0.353$, $t_{1/2}=1.39$ s, $T=4.75$ s); phugoid $-0.00125\pm0.0709j$ ($\omega_n=0.0709$, $\zeta=0.018$, $t_{1/2}\approx555$ s, $T\approx89$ s).

SPO approximation (§6.5): $u,\theta$ frozen (slow), $\mathring Z_{\dot w}\ll m$, $\mathring Z_q\ll mU_\infty$:

$$
\begin{bmatrix}m&0\\-\mathring M_{\dot w}&J_{yy}\end{bmatrix}\begin{bmatrix}\dot w\\\dot q\end{bmatrix}=\begin{bmatrix}\mathring Z_w&mU_\infty\\\mathring M_w&\mathring M_q\end{bmatrix}\begin{bmatrix}w\\q\end{bmatrix},\qquad(6.23)
$$

$$
\omega_n^2=\frac{\mathring M_q\mathring Z_w-mU_\infty\mathring M_w}{mJ_{yy}},\qquad\zeta=\frac{-\left[m(\mathring M_q+U_\infty\mathring M_{\dot w})+\mathring Z_wJ_{yy}\right]}{2\omega_nmJ_{yy}}.\qquad(6.27)
$$

F-4C (178 m/s, level): full model SPO $-0.3690\pm1.3558j$ ($\omega_n=1.405$, $\zeta=0.2626$), phugoid $-0.0065\pm0.0779j$ ($\omega_n=0.0781$, $\zeta=0.0825$); SPO approximation $\omega_n=1.41$, $\zeta=0.264$.

Linearising the 6-DOF model ([[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes|deep dive]]): trim balance $X_{a0}=mg\sin\gamma_0$, $Z_{a0}=-mg\cos\gamma_0$, $M_{a0}=0$ ($x$ along $U_\infty$, $\theta_0=\gamma_0$); body gravity $mg[-s_\theta,\ s_\phi c_\theta,\ c_\phi c_\theta]^T$ gives $Y_{g1}=mg\cos\gamma_0\,\phi_1$ and no $\phi$ in $X_{g1}$, $Z_{g1}$; $\dot h=U_\infty\sin\gamma_0+U_\infty\cos\gamma_0\,\theta+\sin\gamma_0\,u-\cos\gamma_0\,w$. Inverse of the lower-triangular $\mathbf M$: diagonal $1/m$, $1/(m-\mathring Z_{\dot w})$, $1/J_{yy}$, 1 plus $(\mathbf M^{-1})_{32}=\mathring M_{\dot w}/[J_{yy}(m-\mathring Z_{\dot w})]$.

Quartic $\lambda^4+a_3\lambda^3+a_2\lambda^2+a_1\lambda+a_0$ with well-separated modes: fast $\approx\lambda^2+a_3\lambda+a_2$, slow $\approx\lambda^2+\dfrac{a_1a_2-a_0a_3}{a_2^2}\lambda+\dfrac{a_0}{a_2}$. Eigenvector by hand: set $\theta=1$, then $q=\lambda$, solve rows 1–2 for $u,w$; row 3 is the check. Compare in angle units $u/U_\infty$, $\alpha=w/U_\infty$, $\theta$, $\gamma=\theta-\alpha$. F-4C: SPO $\alpha\approx\theta$, $|\gamma|=0.22|\theta|$, $|u|/U_\infty=0.04|\theta|$; phugoid $\gamma\approx\theta$, $|\alpha|=0.10|\theta|$, $|\theta|=1.414\,|u|/U_\infty$.

Unity feedback, gain $K$, plant $1/(s^2+2\zeta\omega_ns+\omega_n^2)$: $\omega_{cl}=\sqrt{\omega_n^2+K}$, $\zeta_{cl}=\zeta\omega_n/\omega_{cl}$, step final value $K/(\omega_n^2+K)$ (stable loop).

## Phugoid approximations

Lectured L18 (Mon 16 Nov), Chapter 6 §6.6; Eq. 6.38 is handout only. Details: [[SESA3047 6.2 - Phugoid Approximation|6.2]].

Lanchester (Eqs. 6.28–6.33): total energy constant (thrust balances drag), $\alpha$ and $C_L$ fixed at trim, lift vertical (shallow path), $h$ up from the trim height where $U=U_\infty$:

$$
U_\infty^2=U^2+2gh,\qquad C_L=\frac{mg}{\tfrac12\rho U_\infty^2S},\qquad m\ddot h=L-mg=-\rho SC_Lgh,
$$

$$
\ddot h+\frac{2g^2}{U_\infty^2}h=0,\qquad\omega_n=\frac{\sqrt2\,g}{U_\infty},\qquad\zeta=0,\qquad T=\frac{\sqrt2\,\pi U_\infty}{g}.\qquad(6.33)
$$

Mode shape (small $u$): $u=-gh/U_\infty$ (antiphase with height), $h_0=U_\infty u_0/g$, $|\theta|\approx|\gamma|=\sqrt2\,|u|/U_\infty$, $\theta$ a quarter cycle ahead of $h$ and behind $u$.

Improved approximation (Eqs. 6.34–6.38): level trim $\gamma_0=0$, $\dot q=0$, $\mathring Z_q=\mathring Z_{\dot w}=\mathring M_q=\mathring M_{\dot w}=0$. The moment row becomes $0=\mathring M_uu+\mathring M_ww$; $q=\dot\theta$ removes the kinematic row; $mU_\infty\dot\theta$ moves left:

$$
\begin{bmatrix}m&0&0\\0&m&-mU_\infty\\0&0&0\end{bmatrix}\begin{bmatrix}\dot u\\\dot w\\\dot\theta\end{bmatrix}=\begin{bmatrix}\mathring X_u&\mathring X_w&-mg\\\mathring Z_u&\mathring Z_w&0\\\mathring M_u&\mathring M_w&0\end{bmatrix}\begin{bmatrix}u\\w\\\theta\end{bmatrix},\qquad
\begin{bmatrix}m\lambda-\mathring X_u&-\mathring X_w&mg\\-\mathring Z_u&m\lambda-\mathring Z_w&-mU_\infty\lambda\\-\mathring M_u&-\mathring M_w&0\end{bmatrix}\begin{bmatrix}u_0\\w_0\\\theta_0\end{bmatrix}=\mathbf 0.\qquad(6.36,\ 6.37)
$$

$\mathbf M$ is singular (rank 2): two eigenvalues, from $\det(\lambda\mathbf M-\mathbf A')=0$. Dimensional derivatives, level trim:

$$
\omega_n^2=\frac{g}{mU_\infty}\left(\frac{\mathring M_u\mathring Z_w}{\mathring M_w}-\mathring Z_u\right),\qquad\zeta=\frac{1}{2\omega_nm}\left[\frac{\mathring M_u}{\mathring M_w}\left(\mathring X_w-\frac{mg}{U_\infty}\right)-\mathring X_u\right].\qquad(6.38)
$$

At fixed $C_L$, $\mathring Z_u=-2mg/U_\infty$; with $\mathring M_u=0$ as well, Eq. 6.38 reduces to Lanchester's $\omega_n$ and $2\zeta\omega_n=-\mathring X_u/m$.

| F-4C, 178 m/s, level | $\omega_n$ (rad/s) | $\zeta$ | $T$ (s) |
|---|---|---|---|
| full model | 0.0781 | 0.0825 | 80.7 |
| Lanchester | 0.0779 | 0 | 80.6 |
| improved (Eq. 6.38) | 0.0797 | 0.0949 | 79.2 |

## Related

- [[SESA3047 1.1 - Dynamic Systems and Control Architectures]]
- [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]
- [[SESA3047 2.1 - Vector Operations and the Transport Theorem]]
- [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]
- [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]]
- [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]]
- [[SESA3047 3.3 - Rigid-Body Rotational Dynamics]]

- [[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]
- [[SESA3047 4.2 - Translational Dynamics]]
- [[SESA3047 4.3 - Complete Flat-Earth 6-DOF Model]]

- [[SESA3047 5.1 - State-Space Form and Linearisation]]
- [[SESA3047 5.2 - Longitudinal State-Space Model]]
- [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]]
- [[SESA3047 5.4 - Time-Domain Solution and Stability]]

- [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]] · [[Eigenvectors as Mode Shapes]]
- [[SESA3047 6.2 - Phugoid Approximation]] · [[Lanchester's Phugoid Approximation]] · [[Separation of Time Scales]] · [[State Coupling]]
- Deep dives: [[SESA3047 Deep Dive - Euler-Angle Rates and Gimbal Lock]] · [[SESA3047 Deep Dive - From the 6-DOF Equations to the Longitudinal Modes]]
