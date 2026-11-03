---
title: "SESA3047 Chapter 5 Practice Problems - Solutions"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: tutorial
subtype: handout-practice-problems
lecturer_set: true
stream: "Chapter 5: State-Space Models"
tags: [sesa3047, tutorial-solutions, state-space, linearisation, transfer-function, block-diagram, stability]
sheet: "Chapter 5 §5.8 Practice problems (Dr Sean Symon)"
theory_notes: ["[[SESA3047 5.1 - State-Space Form and Linearisation]]", "[[SESA3047 5.2 - Longitudinal State-Space Model]]", "[[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]]", "[[SESA3047 5.4 - Time-Domain Solution and Stability]]"]
parent: ["[[SESA3047 Advanced Aerospace Mechanics & Control Hub]]"]
status: complete
coverage: "All five §5.8 problems; Problem 1 pointed to in L14 ll. 230–234; no answer key issued"
date: 2026-11-03
sources: ["02 - Sources/Lectures/Chapter_5.pdf", "02 - Sources/Lectures/02 November 2026 at 11_53_51.txt"]
---

# SESA3047 Chapter 5 Practice Problems - Solutions

> [!info] About this sheet
> The five problems are §5.8 of the Chapter 5 handout (pp. 9–10). No answer key has been issued, so these are my worked solutions, with every number and matrix checked in SymPy/SciPy (`generate_amc_ch5_figures.py --check`). L14 pointed at Problem 1: *"the first question is basically what we're doing right now … that used to be an exam question"* for SESA3030 (ll. 230–234). Problem 4's blocks $P_1,P_2,P_3$ are not given as transfer functions, so it is solved for general blocks first and then for first-order blocks.

## Problem 1. Equilibria and linearisation of a made-up system

> Find all equilibrium points of the system below, linearise it around $(x_0,y_0,z_0)=(-1,1,0)$ and express the linearised system in state-space form.
> $$\dot x=-x+z-x^2z-y^2,\qquad\dot y=z,\qquad\dot z=-4(x+1)^2-z+u.$$

### Equilibria

An equilibrium has every derivative zero. Take the input at its equilibrium value $u_0=0$ (the point given, with $z_0=0$, needs this, as shown below).

From $\dot y=0$:

$$
z_0=0.
$$

From $\dot z=0$ with $z_0=0$, $u_0=0$:

$$
-4(x_0+1)^2=0\quad\Rightarrow\quad x_0=-1.
$$

From $\dot x=0$ with $x_0=-1$, $z_0=0$:

$$
-(-1)+0-0-y_0^2=0\quad\Rightarrow\quad y_0^2=1\quad\Rightarrow\quad y_0=\pm1.
$$

So there are two equilibria, $(-1,1,0)$ and $(-1,-1,0)$, both with $u_0=0$. (With a constant input $u_0>0$ the equilibria move: $(x_0+1)^2=u_0/4$ and $y_0^2=-x_0$, giving up to four, all with $z_0=0$.)

### Linearisation, lecture method

Write $x=-1+\epsilon x_1$, $y=1+\epsilon y_1$, $z=\epsilon z_1$, $u=\epsilon u_1$.

The $\dot x$ equation. Substitute:

$$
\epsilon\dot x_1=-(-1+\epsilon x_1)+\epsilon z_1-(-1+\epsilon x_1)^2\epsilon z_1-(1+\epsilon y_1)^2.
$$

Expand the squares, $(-1+\epsilon x_1)^2=1-2\epsilon x_1+\epsilon^2x_1^2$ and $(1+\epsilon y_1)^2=1+2\epsilon y_1+\epsilon^2y_1^2$:

$$
\epsilon\dot x_1=1-\epsilon x_1+\epsilon z_1-\epsilon z_1+2\epsilon^2x_1z_1-\epsilon^3x_1^2z_1-1-2\epsilon y_1-\epsilon^2y_1^2.
$$

The $\epsilon^0$ terms, $1-1$, are the equilibrium and cancel. The two $\epsilon z_1$ terms cancel. Drop $\epsilon^2$ and $\epsilon^3$:

$$
\epsilon\dot x_1=-\epsilon x_1-2\epsilon y_1\quad\Rightarrow\quad\dot x_1=-x_1-2y_1.
$$

The $\dot y$ equation is already linear:

$$
\dot y_1=z_1.
$$

The $\dot z$ equation. Substitute:

$$
\epsilon\dot z_1=-4(\epsilon x_1)^2-\epsilon z_1+\epsilon u_1.
$$

The first term is $O(\epsilon^2)$. Drop it and divide by $\epsilon$:

$$
\dot z_1=-z_1+u_1.
$$

### The same by the Jacobian

$\mathbf A=\partial\mathbf f/\partial\mathbf x$ at the equilibrium:

| | $\partial/\partial x$ | $\partial/\partial y$ | $\partial/\partial z$ |
|---|---|---|---|
| $\dot x$ | $-1-2xz\to-1$ | $-2y\to-2$ | $1-x^2\to0$ |
| $\dot y$ | $0$ | $0$ | $1$ |
| $\dot z$ | $-8(x+1)\to0$ | $0$ | $-1$ |

and $\mathbf B=\partial\mathbf f/\partial u=[0,0,1]^T$. Both routes agree.

### State-space form

$$
\begin{bmatrix}\dot x_1\\\dot y_1\\\dot z_1\end{bmatrix}=\begin{bmatrix}-1&-2&0\\0&0&1\\0&0&-1\end{bmatrix}\begin{bmatrix}x_1\\y_1\\z_1\end{bmatrix}+\begin{bmatrix}0\\0\\1\end{bmatrix}u_1,
$$

with $\mathbf C=\mathbf I$ by the module's convention (L14 ll. 160–161).

The matrix is upper triangular, so its eigenvalues are the diagonal: $-1$, $0$, $-1$. With a zero eigenvalue the linear model is not asymptotically stable, and the linearisation alone cannot decide the stability of the nonlinear system at this point. (About $(-1,-1,0)$ only the $(1,2)$ entry changes, to $+2$, with the same eigenvalues.)

## Problem 2. Transfer functions to state space

> Determine a state-space representation of $\dfrac{Y}{U}=\dfrac{4s^2-5s+1}{s^3+3s^2-20s+14}$ and $\dfrac{\theta_o}{\theta_i}=\dfrac{3.5K}{s^3+51.4s^2+111s+3.5K}$.

Method of [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams#2. Transfer functions to state space (5.26–5.34)|5.3 §2]].

### (a)

Split with an intermediate $V$: $(s^3+3s^2-20s+14)V=U$ and $Y=(4s^2-5s+1)V$. In the time domain:

$$
\dddot v+3\ddot v-20\dot v+14v=u.
$$

States $x_1=v$, $x_2=\dot v$, $x_3=\ddot v$:

$$
\dot x_1=x_2,\qquad\dot x_2=x_3,\qquad\dot x_3=-14x_1+20x_2-3x_3+u.
$$

Output: $y=4\ddot v-5\dot v+v=x_1-5x_2+4x_3$.

$$
\dot{\mathbf x}=\begin{bmatrix}0&1&0\\0&0&1\\-14&20&-3\end{bmatrix}\mathbf x+\begin{bmatrix}0\\0\\1\end{bmatrix}u,\qquad y=\begin{bmatrix}1&-5&4\end{bmatrix}\mathbf x.
$$

Watch the signs: $-20s$ in the denominator becomes $+20$ in $\mathbf A$. A check with `ss2tf` returns the original transfer function. (Not asked: the poles are $2.609$, $0.833$ and $-6.442$, so this plant is unstable; the zeros are $s=1$ and $s=0.25$.)

### (b)

The numerator is a constant, so no intermediate signal is needed. Cross-multiply:

$$
\dddot\theta_o+51.4\ddot\theta_o+111\dot\theta_o+3.5K\theta_o=3.5K\theta_i.
$$

States $x_1=\theta_o$, $x_2=\dot\theta_o$, $x_3=\ddot\theta_o$, input $\theta_i$:

$$
\dot{\mathbf x}=\begin{bmatrix}0&1&0\\0&0&1\\-3.5K&-111&-51.4\end{bmatrix}\mathbf x+\begin{bmatrix}0\\0\\3.5K\end{bmatrix}\theta_i,\qquad\theta_o=\begin{bmatrix}1&0&0\end{bmatrix}\mathbf x.
$$

The §5.5 construction (unit input to $\dddot v$) gives instead $\mathbf B=[0,0,1]^T$ and $\mathbf C=[3.5K,0,0]$, with the same $\mathbf A$. Both are correct, an example of the non-uniqueness noted in 5.3. (Not asked: by Routh–Hurwitz on the cubic, the system is stable for $0<K<51.4\times111/3.5=1630$.)

## Problem 3. The lateral state-space model

> Derive the state-space model for the lateral dynamics if $\Delta Y_g=mg\phi$, $\Delta Y_a=\mathring Y_vv+\mathring Y_pp+\mathring Y_rr$, $\Delta L_a=\mathring L_vv+\mathring L_pp+\mathring L_rr$, $\Delta N_a=\mathring N_vv+\mathring N_pp+\mathring N_rr$.

The lateral counterpart of [[SESA3047 5.2 - Longitudinal State-Space Model|5.2]]. Subscripts 1 dropped: all variables are perturbations.

### Inertia sides

From Eqs. 5.7b and 5.8a, c:

$$
Y_1=m(\dot v+U_\infty r),\qquad L_1=J_{xx}\dot p-J_{xz}\dot r,\qquad N_1=-J_{xz}\dot p+J_{zz}\dot r.
$$

### Equate to the out-of-balance terms

Gravity gives a side force but no moment about the centre of mass:

$$
m\dot v+mU_\infty r=mg\phi+\mathring Y_vv+\mathring Y_pp+\mathring Y_rr,
$$

$$
J_{xx}\dot p-J_{xz}\dot r=\mathring L_vv+\mathring L_pp+\mathring L_rr,
$$

$$
-J_{xz}\dot p+J_{zz}\dot r=\mathring N_vv+\mathring N_pp+\mathring N_rr.
$$

Move $mU_\infty r$ to the right of the first:

$$
m\dot v=\mathring Y_vv+\mathring Y_pp+(\mathring Y_r-mU_\infty)r+mg\phi.
$$

### The fourth state

$\phi$ appears, so it is a state. From [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates|3.1]], $\dot\phi=p+(q\sin\phi+r\cos\phi)\tan\theta$. Linearised about level trim ($\theta_0=0$, $\phi_0=0$): $\dot\phi=p$. ($\psi$ could be a fifth state with $\dot\psi=r$, but no equation depends on $\psi$, so it is left out.)

### Matrix form

With $\mathbf x=[v,p,r,\phi]^T$:

$$
\underbrace{\begin{bmatrix}m&0&0&0\\0&J_{xx}&-J_{xz}&0\\0&-J_{xz}&J_{zz}&0\\0&0&0&1\end{bmatrix}}_{\mathbf E}\dot{\mathbf x}=\underbrace{\begin{bmatrix}\mathring Y_v&\mathring Y_p&\mathring Y_r-mU_\infty&mg\\\mathring L_v&\mathring L_p&\mathring L_r&0\\\mathring N_v&\mathring N_p&\mathring N_r&0\\0&1&0&0\end{bmatrix}}_{\mathbf A'}\mathbf x.
$$

### The state matrix

Rows 1 and 4 divide by $m$ and 1. Rows 2–3 couple $\dot p$ and $\dot r$ through $J_{xz}$; invert the $2\times2$ block with $\Gamma=J_{xx}J_{zz}-J_{xz}^2$:

$$
\begin{bmatrix}J_{xx}&-J_{xz}\\-J_{xz}&J_{zz}\end{bmatrix}^{-1}=\frac{1}{\Gamma}\begin{bmatrix}J_{zz}&J_{xz}\\J_{xz}&J_{xx}\end{bmatrix}.
$$

Then $\mathbf A=\mathbf E^{-1}\mathbf A'$ is

$$
\mathbf A=\begin{bmatrix}
\dfrac{\mathring Y_v}{m}&\dfrac{\mathring Y_p}{m}&\dfrac{\mathring Y_r}{m}-U_\infty&g\\[8pt]
\dfrac{J_{zz}\mathring L_v+J_{xz}\mathring N_v}{\Gamma}&\dfrac{J_{zz}\mathring L_p+J_{xz}\mathring N_p}{\Gamma}&\dfrac{J_{zz}\mathring L_r+J_{xz}\mathring N_r}{\Gamma}&0\\[8pt]
\dfrac{J_{xz}\mathring L_v+J_{xx}\mathring N_v}{\Gamma}&\dfrac{J_{xz}\mathring L_p+J_{xx}\mathring N_p}{\Gamma}&\dfrac{J_{xz}\mathring L_r+J_{xx}\mathring N_r}{\Gamma}&0\\[8pt]
0&1&0&0
\end{bmatrix}.
$$

(Checked with SymPy.) With $J_{xz}=0$ the roll and yaw rows reduce to $\mathring L/J_{xx}$ and $\mathring N/J_{zz}$. The given $\Delta Y_g=mg\phi$ is for level trim; in a climb at $\gamma_0$ it would be $mg\cos\gamma_0\,\phi$, and $\dot\phi=p+r\tan\gamma_0$.

## Problem 4. The MISO block diagram

> Find the correct state-space model for the MISO block diagram in Figure 5.4.

### Reading the diagram

- $u_1=K_1(r_1-y)$ and $u_2=K_2(r_2-y)$: both loops feed back the single output $y$ negatively.
- $P_1$ is driven by $u_1$ (output $x_1$), $P_3$ by $u_2$ (output $x_3$), and $P_2$ by the sum $u_1+u_2$ (output $x_2$).
- $y=K_3x_1+x_2+K_4x_3$.

Two inputs and one output: multi-input, single-output.

### General answer, for any blocks

The handout does not give $P_1,P_2,P_3$, so solve it for any strictly proper blocks first. Give each block its own state-space model (e.g. from [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams#2. Transfer functions to state space (5.26–5.34)|5.3 §2]]): block $i$ has state $\boldsymbol\xi_i$, input $e_i$ and output $x_i$,

$$
\dot{\boldsymbol\xi}_i=\mathbf A_i\boldsymbol\xi_i+\mathbf B_ie_i,\qquad x_i=\mathbf C_i\boldsymbol\xi_i .
$$

The block inputs, from the diagram:

$$
e_1=u_1=K_1(r_1-y),\qquad e_2=u_1+u_2=K_1r_1+K_2r_2-(K_1+K_2)y,\qquad e_3=u_2=K_2(r_2-y).
$$

The output, with $\boldsymbol\xi=[\boldsymbol\xi_1;\boldsymbol\xi_2;\boldsymbol\xi_3]$:

$$
y=K_3x_1+x_2+K_4x_3=\underbrace{\begin{bmatrix}K_3\mathbf C_1&\mathbf C_2&K_4\mathbf C_3\end{bmatrix}}_{\mathbf C}\boldsymbol\xi .
$$

Stack the three block equations and substitute $e_i$, then $y=\mathbf C\boldsymbol\xi$:

$$
\dot{\boldsymbol\xi}=\Big(\underbrace{\operatorname{diag}(\mathbf A_1,\mathbf A_2,\mathbf A_3)}_{\text{open loop}}-\underbrace{\begin{bmatrix}K_1\mathbf B_1\\(K_1+K_2)\mathbf B_2\\K_2\mathbf B_3\end{bmatrix}}_{\text{how }y\text{ feeds back}}\mathbf C\Big)\boldsymbol\xi+\underbrace{\begin{bmatrix}K_1\mathbf B_1&\mathbf 0\\K_1\mathbf B_2&K_2\mathbf B_2\\\mathbf 0&K_2\mathbf B_3\end{bmatrix}}_{\mathbf B}\begin{bmatrix}r_1\\r_2\end{bmatrix}.
$$

The size is $n_1+n_2+n_3$, the total order of the three blocks. (Checked numerically: with random second-, first- and third-order blocks and random gains, $\mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B$ equals the closed-loop transfer function found by block-diagram algebra, $[K_1(K_3P_1+P_2),\ K_2(P_2+K_4P_3)]/(1+K_1K_3P_1+(K_1+K_2)P_2+K_2K_4P_3)$.)

### First-order blocks

The diagram labels each block's output as a single state, $x_1,x_2,x_3$, as in Fig. 5.3, which suggests first-order blocks, $P_i=b_i/(s+a_i)$. Then $\mathbf A_i=-a_i$, $\mathbf B_i=b_i$, $\mathbf C_i=1$, $\boldsymbol\xi_i=x_i$, and the general answer reduces to three states. Row by row:

### Rows

Substitute $u_1$, $u_2$ and $y$ into each block's ODE.

$$
\dot x_1=-a_1x_1+b_1K_1(r_1-K_3x_1-x_2-K_4x_3),
$$

$$
\dot x_2=-a_2x_2+b_2\big[K_1(r_1-y)+K_2(r_2-y)\big]=-a_2x_2+b_2(K_1+K_2)(-K_3x_1-x_2-K_4x_3)+b_2K_1r_1+b_2K_2r_2,
$$

$$
\dot x_3=-a_3x_3+b_3K_2(r_2-K_3x_1-x_2-K_4x_3).
$$

### Matrices

$$
\mathbf A=\begin{bmatrix}
-a_1-b_1K_1K_3&-b_1K_1&-b_1K_1K_4\\
-b_2(K_1+K_2)K_3&-a_2-b_2(K_1+K_2)&-b_2(K_1+K_2)K_4\\
-b_3K_2K_3&-b_3K_2&-a_3-b_3K_2K_4
\end{bmatrix},
$$

$$
\mathbf B=\begin{bmatrix}b_1K_1&0\\b_2K_1&b_2K_2\\0&b_3K_2\end{bmatrix},\qquad\mathbf C=\begin{bmatrix}K_3&1&K_4\end{bmatrix}.
$$

(Checked as the Jacobian with SymPy.) Dimensions: $3\times3$, $3\times2$, $1\times3$. Because $y$ feeds back into both loops, every state appears in every row: the single output couples the whole system, unlike the two separate loops of Fig. 5.3.

## Problem 5. Stability of a 2 by 2 system

> Determine if $\dot{\mathbf x}=\begin{bmatrix}4&5\\-1&2\end{bmatrix}\mathbf x$ is stable.

$\lambda^2-6\lambda+13=0$ gives $\lambda=3\pm2j$. Positive real parts, so **unstable**: a growing oscillation, amplitude $\propto e^{3t}$, period $\pi$ s. Full working in [[SESA3047 5.4 - Time-Domain Solution and Stability#5. Worked example: Practice problem 5|5.4 §5]].

## Links

- [[SESA3047 5.1 - State-Space Form and Linearisation]] (Problem 1) · [[SESA3047 5.2 - Longitudinal State-Space Model]] (Problem 3) · [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]] (Problems 2, 4) · [[SESA3047 5.4 - Time-Domain Solution and Stability]] (Problem 5)
- Parent: [[SESA3047 Advanced Aerospace Mechanics & Control Hub]]
