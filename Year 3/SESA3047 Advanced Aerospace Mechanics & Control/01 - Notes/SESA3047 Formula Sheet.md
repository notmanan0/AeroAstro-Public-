---
title: "SESA3047 Formula Sheet"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: formula
aliases: ["SESA3047 formulae", "Advanced Mechanics and Control formula sheet"]
tags: [sesa3047, formula, exam-prep]
status: in-progress
coverage: "Chapters 1–3"
sources: ["01 - Notes/Topics", "02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/Chapter 2.pdf"]
---

# SESA3047 Formula Sheet

Current coverage: **Chapter 1 (fundamental concepts) and Chapter 2 (introduction to kinematics)**.

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

For $\dot{\mathbf x}=\mathbf f(\mathbf x,\mathbf u)$ around $(\mathbf x_0,\mathbf u_0)$,

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
[\mathbf v]^c=\text{components of }\mathbf v\text{ in coordinates }c.
$$

## Flat-Earth assumptions

$$
\boldsymbol\Omega_E\approx\mathbf 0,
\qquad
\text{Earth curvature neglected},
\qquad
g=\text{constant}.
$$

In local NED coordinates,

$$
[\mathbf g]^{NED}=\begin{bmatrix}0\\0\\g\end{bmatrix}.
$$

## Coordinate axes

| Coordinates | $x$ | $y$ | $z$ | Typical use |
|---|---|---|---|---|
| NED | north | east | down | local position, ground velocity, gravity |
| FRD | forward | right | down | body forces, body velocity, angular velocity |

## Vector operations (Chapter 2)

$$
\mathbf u\cdot\mathbf v=|\mathbf u||\mathbf v|\cos\alpha=\mathbf u^T\mathbf v,
\qquad
\mathbf u\times\mathbf v=|\mathbf u||\mathbf v|\sin\alpha\,\mathbf n=\begin{bmatrix}u_yv_z-u_zv_y\\u_zv_x-u_xv_z\\u_xv_y-u_yv_x\end{bmatrix}.
$$

Cross-product matrix:

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
[\mathbf g]^{FRD}=g\begin{bmatrix}-s_\theta\\s_\phi c_\theta\\c_\phi c_\theta\end{bmatrix}.
$$

Extraction (singular at $\theta=\pm90^\circ$):

$$
\phi=\mathrm{atan2}(C_{23},C_{33}),\qquad \theta=-\arcsin C_{13},\qquad \psi=\mathrm{atan2}(C_{12},C_{11}).
$$

$\mathrm{atan2}(y,x)\in(-\pi,\pi]$ uses the signs of both arguments; $\arctan(y/x)\in(-\pi/2,\pi/2)$ cannot tell $(y,x)$ from $(-y,-x)$. At $\theta=\pm90^\circ$ both atan2 calls become $\mathrm{atan2}(0,0)$ ([[Gimbal Lock]]); libraries return 0 silently.

Notation: $\mathbf p_{A/B}$ (of $A$ relative to $B$), $[\,\cdot\,]^c$ (components in coordinates $c$), ${}^b\dot{(\cdot)}$ (derivative observed from $F_b$).

## Rotational kinematics (Chapter 3, §3.1)

Body rates $\boldsymbol\omega^{FRD}_{b/r}=[p,q,r]^T$; Euler angles $\boldsymbol\Phi=[\phi,\theta,\psi]^T$.

$$
\boldsymbol\omega^{FRD}_{b/r}=\begin{bmatrix}\dot\phi\\0\\0\end{bmatrix}+\mathbf C_x(\phi)\left(\begin{bmatrix}0\\\dot\theta\\0\end{bmatrix}+\mathbf C_y(\theta)\begin{bmatrix}0\\0\\\dot\psi\end{bmatrix}\right)=\mathbf E(\boldsymbol\Phi)\dot{\boldsymbol\Phi},\qquad
\mathbf E=\begin{bmatrix}1&0&-s_\theta\\0&c_\phi&s_\phi c_\theta\\0&-s_\phi&c_\phi c_\theta\end{bmatrix}.
$$

$$
\dot{\boldsymbol\Phi}=\mathbf H(\boldsymbol\Phi)\,\boldsymbol\omega^{FRD}_{b/r},\qquad
\mathbf H=\begin{bmatrix}1&s_\phi\tan\theta&c_\phi\tan\theta\\0&c_\phi&-s_\phi\\0&s_\phi/c_\theta&c_\phi/c_\theta\end{bmatrix},\qquad\det\mathbf E=\cos\theta.
$$

$$
\dot\phi=p+(q s_\phi+r c_\phi)\tan\theta,\qquad\dot\theta=qc_\phi-rs_\phi,\qquad\dot\psi=\frac{qs_\phi+rc_\phi}{c_\theta}.
$$

Small angles: $\dot\phi\approx p$, $\dot\theta\approx q$, $\dot\psi\approx r$. Flat Earth: $\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/e}=\boldsymbol\omega_{b/i}$; rotating Earth: $\boldsymbol\omega_{b/r}=\boldsymbol\omega_{b/i}-\boldsymbol\omega_{r/i}$ (L8). Coupling check (L8): $r=0$, $\theta=0$ gives $\dot\theta=q\cos\phi$, $\dot\psi=q\sin\phi$. Level turn: $\dot\psi=g\tan\phi/V$, $q=\dot\psi\sin\phi$, $r=\dot\psi\cos\phi$.

## Velocity and acceleration in moving frames (§3.2)

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

## Rigid-body dynamics (§§3.3–3.4)

$$
\mathbf Q=m\mathbf v_{cm/i},\qquad\sum\mathbf F_{ext}=m\,\mathbf a_{cm/i}.
$$

$$
\mathbf h^{FRD}_{cm/i}=\mathbf J^{FRD}\boldsymbol\omega^{FRD}_{b/i},\qquad
\mathbf J=-\int_B\tilde{\mathbf r}^{\,2}\mathrm dm=\begin{bmatrix}J_{xx}&-J_{xy}&-J_{xz}\\-J_{xy}&J_{yy}&-J_{yz}\\-J_{xz}&-J_{yz}&J_{zz}\end{bmatrix},
$$

with $J_{xx}=\int(y^2+z^2)\mathrm dm$ (and cyclic) and $J_{xy}=\int xy\,\mathrm dm$ (and cyclic).

Rotational dynamic equation:

$$
{}^b\dot{\boldsymbol\omega}=\mathbf J^{-1}\left(\sum\mathbf M_{cm}-\tilde{\boldsymbol\omega}\mathbf J\boldsymbol\omega\right).
$$

Principal axes (Euler's equations): $J_x\dot p=L+(J_y-J_z)qr$, $J_y\dot q=M+(J_z-J_x)rp$, $J_z\dot r=N+(J_x-J_y)pq$.

Aircraft ($J_{xy}=J_{yz}=0$):

$$
L=J_x\dot p-J_{xz}\dot r+(J_z-J_y)qr-J_{xz}pq,\quad
M=J_y\dot q+(J_x-J_z)pr+J_{xz}(p^2-r^2),\quad
N=J_z\dot r-J_{xz}\dot p+(J_y-J_x)pq+J_{xz}qr.
$$

6-DOF so far: $\dot{\boldsymbol\omega}$ (dynamics), $\dot{\boldsymbol\Phi}=\mathbf H\boldsymbol\omega$ and $\dot{\mathbf p}=\mathbf C^T\mathbf v$ (kinematics); $\dot{\mathbf v}$ in Chapter 4.

## Related

- [[SESA3047 1.1 - Dynamic Systems and Control Architectures]]
- [[SESA3047 1.2 - Dynamic Models, Frames and Earth Models]]
- [[SESA3047 2.1 - Vector Operations and the Transport Theorem]]
- [[SESA3047 2.2 - Direction Cosine Matrices and Euler Angles]]
- [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]]
- [[SESA3047 3.2 - Translational Kinematics and Accelerations in Moving Frames]]
- [[SESA3047 3.3 - Rigid-Body Rotational Dynamics]]

