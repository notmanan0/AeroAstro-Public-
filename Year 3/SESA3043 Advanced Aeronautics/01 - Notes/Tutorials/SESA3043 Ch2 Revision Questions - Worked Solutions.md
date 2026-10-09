---
title: "SESA3043 Ch2 Revision Questions - Worked Solutions"
module: "SESA3043 Advanced Aeronautics"
type: tutorial
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
tags: [sesa3043, tutorial-solutions, revision-questions, conformal-mapping, lumped-vortex, panel-method]
sheet: "Chapter 2 Revision Questions"
theory_notes: ["[[SESA3043 2.1 - Complex Functions and Conformal Mapping]]", "[[SESA3043 2.2 - Lumped Vortex Method]]", "[[SESA3043 2.3 - Panel Methods]]"]
status: complete
sources: ["03 - Exams & Past Papers/Ch2_Revision_Questions.pdf"]
---

# SESA3043 Ch2 Revision Questions - Worked Solutions

> [!abstract] Sheet info
> Blackboard revision questions for Chapter 2 (updated 10 Sep 2026). Answers, all verified symbolically or numerically:
> - §2.1: Q1 doublet $\phi=\mu\cos\theta/2\pi r$; Q4 $b/c=(1+2\varepsilon)/4(1+\varepsilon)^2$.
> - §2.2: Q3 $L_1/L_2=(2\varepsilon+3)/(2\varepsilon+1)$; Q4 $7/5$; Q5 $2(\varepsilon+3)/(4\varepsilon+3)$; Q6 $\Gamma=\tfrac23\Gamma_\infty$ per wing, $\tfrac43$ total.
> - §2.3: descriptive and code questions, answered in the topic note.

## 2.1 Exact solution for potential flow

### Q1. Doublet from a source and a sink (real plane)

Put a sink $-m$ at the origin and a source $+m$ at $(-l,0)$, so the source is upstream (the table's doublet, $\nu=\pi$). By superposition,

$$
\phi=\frac{m}{2\pi}\ln r_s-\frac{m}{2\pi}\ln r=\frac{m}{2\pi}\ln\frac{r_s}{r},\qquad r_s^2=(x+l)^2+y^2=r^2+2rl\cos\theta+l^2.
$$

**Expand for small $l/r$:**

$$
\ln\frac{r_s}{r}=\frac12\ln\left(1+\frac{2l\cos\theta}{r}+\frac{l^2}{r^2}\right)\approx\frac12\cdot\frac{2l\cos\theta}{r}=\frac{l\cos\theta}{r}
$$

(using $\ln(1+\epsilon)\approx\epsilon$ and dropping $O(l^2/r^2)$).

**Doublet limit** $l\to0$, $m\to\infty$, $\mu=ml$ fixed:

$$
\boxed{\phi=\frac{\mu\cos\theta}{2\pi r}}.
$$

**Velocity:**

$$
q_r=\frac{\partial\phi}{\partial r}=-\frac{\mu\cos\theta}{2\pi r^2},\qquad q_\theta=\frac1r\frac{\partial\phi}{\partial\theta}=-\frac{\mu\sin\theta}{2\pi r^2}.
$$

**Cartesian components:**

$$
u=q_r\cos\theta-q_\theta\sin\theta=-\frac{\mu}{2\pi r^2}(\cos^2\theta-\sin^2\theta)=-\frac{\mu\cos2\theta}{2\pi r^2},
$$

$$
v=q_r\sin\theta+q_\theta\cos\theta=-\frac{\mu}{2\pi r^2}(2\sin\theta\cos\theta)=-\frac{\mu\sin2\theta}{2\pi r^2}.
$$

The streamfunction follows the same way from $\psi=\frac{m}{2\pi}(\theta_s-\theta)$: $\psi=-\dfrac{\mu\sin\theta}{2\pi r}$.

### Q2. General doublet by complex potential, compared with Q1

$\Phi=-\dfrac{\mu}{2\pi}\dfrac{e^{i\nu}}{z}$, $u=\dfrac{\mu}{2\pi r^2}\cos(2\theta-\nu)$, $v=\dfrac{\mu}{2\pi r^2}\sin(2\theta-\nu)$. At $\nu=\pi$ these are exactly Q1's results ✓, in one derivative instead of a Taylor expansion of two logarithms. → [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#5. The general doublet (derivation)]]

### Q3. Flow impinging on a plate

$\Phi=\pm U_\infty\sqrt{z^2+4a^2}$, $C_p=1-\dfrac{y^2}{4a^2-y^2}$. → [[SESA3043 2.1 - Complex Functions and Conformal Mapping#3. Flow impinging on a finite plate (slides 9–12; revision 2.1 Q3)]]

### Q4. Joukowski chord

$c=2b+b\left(1+2\varepsilon+\dfrac{1}{1+2\varepsilon}\right)=\dfrac{4b(1+\varepsilon)^2}{1+2\varepsilon}$. → [[SESA3043 2.1 - Complex Functions and Conformal Mapping#Chord length (derivation; revision 2.1 Q4)]]

## 2.2 Lumped vortex method

| Q | Configuration | Answer | Full solution |
|---|---|---|---|
| 1 | Thin-aerofoil review | a.c. at $c/4$, slope $2\pi$, $\bar x_{cp}=-C_{M,LE}/C_L$ | [[SESA3043 2.2 - Lumped Vortex Method#1. Thin-aerofoil review (slides 25–27; revision 2.2 Q1)]] |
| 2 | LV steps | 5 steps; why $c/4$ and $3c/4$ | [[SESA3043 2.2 - Lumped Vortex Method#2. The flat plate with one lumped vortex (slides 28–30)]] |
| 3 | Tandem, gap $\varepsilon c$ | $\dfrac{L_1}{L_2}=\dfrac{2\varepsilon+3}{2\varepsilon+1}$ | [[SESA3043 2.2 - Lumped Vortex Method#General gap s = εc (revision 2.2 Q3)]] |
| 4 | Tandem, gap $c/2$, ground at $h=c/2$ | $\Gamma_1=\tfrac{140}{87}\Gamma_\infty$, $\Gamma_2=\tfrac{100}{87}\Gamma_\infty$, $L_1/L_2=7/5$ | [[SESA3043 2.2 - Lumped Vortex Method#Q4. Tandem in ground effect (s = c/2, h = c/2)]] |
| 5 | Rear plate at $(1+\varepsilon)\alpha$ | $\dfrac{L_1}{L_2}=\dfrac{2(\varepsilon+3)}{4\varepsilon+3}$ | [[SESA3043 2.2 - Lumped Vortex Method#Q5. Rear aerofoil at extra incidence β = εα (s = c/2)]] |
| 6 | Biplane, gap $c/2$ | each $\tfrac23\Gamma_\infty$; total $\tfrac43$ of one aerofoil | [[SESA3043 2.2 - Lumped Vortex Method#Q6. Biplane, vertical gap c/2]] |

## 2.3 Panel method

All six questions are answered in [[SESA3043 2.3 - Panel Methods#9. Revision questions §2.3]], with the full derivations in §§2–5 of that note.

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]]
- Chapter 1 sheet: [[SESA3043 Ch1 Revision Questions - Worked Solutions]]
