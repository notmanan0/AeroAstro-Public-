---
title: "SESA3043 Ch3 Revision Questions - Worked Solutions"
module: "SESA3043 Advanced Aeronautics"
type: tutorial
stream: "Chapter 3: Methods for Boundary Layers"
tags: [sesa3043, tutorial-solutions, revision-questions, boundary-layer, blasius, pohlhausen, transition, momentum-integral, vii]
sheet: "Chapter 3 Revision Questions"
theory_notes: ["[[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures]]", "[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]", "[[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]", "[[SESA3043 3.4 - Transition to Turbulence]]", "[[SESA3043 3.5 - Momentum Integral Equation]]", "[[SESA3043 3.6 - Viscous-Inviscid Interaction]]"]
status: complete
sources: ["03 - Exams & Past Papers/Ch3_Revision_Questions.pdf"]
---

# SESA3043 Ch3 Revision Questions - Worked Solutions

> [!abstract] Sheet info
> Blackboard revision questions for Chapter 3 (updated 10 Sep 2026), 26 questions over six sections. Most are "understand / explain / derive" prompts whose full answers are in the topic notes; numerical answers are given here in full and were checked in Python. Chapter 3 has not been lectured yet, and the tutorial for it will be the second Friday lecture at the end of the chapter (`02 October 2026 at 14_53_48.txt`, ll. 507–510).

## 3.1 Introduction

**Q1. Prandtl's thin-BL theory.** High $Re$, so $\delta\ll x$; inviscid, irrotational flow outside and at the edge; viscous flow inside, governed by the reduced BL equations; pressure imposed by the outer flow ($\partial p/\partial y=0$). → [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#1. Prandtl's thin boundary-layer theory, revisited (slides 6–7)|3.1 §1]]

**Q2. Definitions.**

| Quantity | Definition | Physical meaning |
|---|---|---|
| $\delta_{99}$ | $u=0.99U_e$ | where the profile has (almost) reached the edge |
| $\delta^*$ | $\int_0^\infty(1-u/U_e)\,\mathrm dy$ | wall shift for equal **mass** flow; the effective body |
| $\theta$ | $\int_0^\infty\frac{u}{U_e}(1-\frac{u}{U_e})\,\mathrm dy$ | **momentum** deficit; $D=\rho U_e^2\theta$ on a flat plate |
| $H$ | $\delta^*/\theta$ | profile shape: 2.59 laminar, ~1.3 turbulent, rising towards separation |

→ [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures|3.1 §§2–6]]

**Q3.** $\tau_w=\mu\,\partial u/\partial y|_0$, $C_f=\tau_w/\frac12\rho U_e^2$. On a flat plate $D=\rho U_e^2\theta=\int_0^x\tau_w\,\mathrm dx$, so $\mathrm d\theta/\mathrm dx=C_f/2$. → [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#5. Wall shear, skin friction and the drag link (slide 32)|3.1 §5]]

**Q4. Linear profile.** $\delta^*=\delta/2$, $\theta=\delta/6$, $H=3$, $C_f=2\nu/(U_e\delta)=2/Re_\delta$. So $\delta^*$ and $\theta$ grow in proportion to $\delta$ and $C_f$ falls as $1/\delta$. (With the flat-plate MIE: $\delta/x=3.46/\sqrt{Re_x}$, $C_f=0.577/\sqrt{Re_x}$.) → [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures#7. Worked example: the linear profile (revision 3.1 Q4)|3.1 §7]]

## 3.2 Blasius and Falkner–Skan

**Q1.** $\xi=\sqrt{2\nu x/((m+1)U_e)}$ ($m=0$ for Blasius), $\eta=y/\xi$, $f=\psi/(U_e\xi)$, with $\partial\eta/\partial x=\frac{\eta}{2x}(m-1)$, $\partial\eta/\partial y=1/\xi$. → [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#2. The Blasius similarity variables (slides 12–27; Notes §1)|3.2 §2]]

**Q2. Integrals A and B (flat plate).**

$$
\eta^*=\int_0^\infty(1-f')\,\mathrm d\eta=1.217,\qquad\theta^*=\int_0^\infty f'(1-f')\,\mathrm d\eta=f''(0)=0.4696.
$$

A from the asymptote $f\to\eta-1.217$; B by parts plus the Blasius equation. → [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Integral type B (slides 46–68; Notes Eqs. 10–11)|3.2 §5]]

**Q3.** $\delta^*=\xi\eta^*$, $\theta=\xi\theta^*$, giving $\delta^*/x=1.721/\sqrt{Re_x}$, $\theta/x=0.664/\sqrt{Re_x}$, $H=2.59$.

**Q4. Wedge, $\beta=0.3$.** $m=0.1765$; table $\eta^*=0.9110$, $\theta^*=0.3857$:

$$
\frac{\delta^*}{x}=\frac{1.188}{\sqrt{Re_x}},\qquad\frac{\theta}{x}=\frac{0.503}{\sqrt{Re_x}},\qquad\delta^*,\theta\propto x^{0.412}.
$$

→ [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#7.2 Revision 3.2 Q4: the wedge with β = 0.3|3.2 §7.2]]

## 3.3 Pohlhausen and pressure gradient

**Q1.** At separation $\partial u/\partial y|_0=0$, so $\tau_w=0$ and $C_f=0$; downstream the near-wall flow reverses and $C_f<0$.

**Q2.** At the wall $u=v=0$, so $0=U_eU_e'+\nu\,\partial^2u/\partial y^2|_0=U_eU_e'+\frac{\nu U_e}{\delta^2}\frac{\mathrm d^2(u/U_e)}{\mathrm d\eta^2}|_0$; divide by $U_e$. → [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#Step 3: the wall compatibility condition (slide 18)|3.3 §2]]

**Q3.** $\lambda=\frac{\delta^2}{\nu}U_e'=Re_\delta\frac{\delta}{U_e}U_e'=-Re_\delta\frac{\delta}{\rho U_e^2}\frac{\mathrm dp_e}{\mathrm dx}$: dimensionless, and the ratio of pressure-gradient force to viscous shear. → [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#4. What λ means (revision Q3; slides 28–31)|3.3 §4]]

**Q4.** $u/U_e=F(\eta)+\lambda G(\eta)$: $\lambda>0$ fuller (thinner, higher shear, lower $H$); $\lambda<0$ emptier, with an inflection point. → [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#3. Integral properties as functions of λ|3.3 §3]]

**Q5.** $\tau_w\propto a_1=2+\lambda/6=0$ gives $\boxed{\lambda=-12}$, where $H=3.5$.

**Q6.** APG decelerates the slow wall fluid; separation is likelier at high $Re$, with thick layers, slow edge flow and strong APG. Delay it by gentler pressure recovery, tripping to turbulence, vortex generators, suction, blowing and slots. → [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#Ways to delay separation (revision Q6)|3.3 §5]]

## 3.4 Transition

**Q1–Q2.** Receptivity → TS waves → Λ-vortices → breakdown → turbulent spots → turbulence (natural); or bypass via large disturbances. → [[SESA3043 3.4 - Transition to Turbulence#2. The roadmap to transition (slides 9–16)|3.4 §2]]

**Q3.** Base flow plus small wave, products neglected, normal modes: Orr–Sommerfeld. → [[SESA3043 3.4 - Transition to Turbulence#4. Linear stability: deriving the Orr–Sommerfeld equation (slides 20–24)|3.4 §4]]

**Q4.** Contours of $\alpha_i$ in $(\log Re_{\delta^*},F)$; inside the neutral curve $\alpha_i<0$; the tip is $Re_{crit}$. → 3.4 §6

**Q5.** $n=-\int_{x_0}^x\alpha_i\,\mathrm dx$ for each $F$; envelope; transition at $n_{crit}=9$. → [[SESA3043 3.4 - Transition to Turbulence#7. The n factor and the eⁿ method (slides 37–44)|3.4 §7]]

**Q6.** APG destabilises (larger region, lower $Re_{crit}$, inflectional instability); FPG stabilises.

## 3.5 Momentum integral equation

**Q1–Q3.** $\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{C_f}{2}$, derived in six steps. → [[SESA3043 3.5 - Momentum Integral Equation#1. The derivation, step by step (slides 5–38)|3.5 §1]]

## 3.6 Viscous–inviscid interaction

**Q1.** SDM re-panels each iteration (direct but costly); STM keeps the panels and blows through them (cheap, used by XFOIL). → [[SESA3043 3.6 - Viscous-Inviscid Interaction#SDM against STM (revision Q1)|3.6 §4]]

**Q2.** Mass balance on the tunnel between $x$ and $x+\Delta x$: $v_s=\mathrm d(U_e\delta^*)/\mathrm dx$. → [[SESA3043 3.6 - Viscous-Inviscid Interaction#Deriving v_s (slide 21; revision Q2)|3.6 §4]]

**Q3. Wind tunnel.** $U_e=U_0a^2/(a-2\delta^*)^2$, $\delta^*=\frac97\theta$, $\theta=0.036L\,Re_L^{-1/5}$:

| Iteration | $U_e$ used (m/s) | $Re_L$ | $\theta$ (mm) | $\delta^*$ (mm) | new $U_e$ (m/s) |
|---|---:|---:|---:|---:|---:|
| 1 | 15.000 | $2.055\times10^6$ | 3.934 | 5.057 | **17.248** |
| 2 | 17.248 | $2.363\times10^6$ | 3.825 | 4.918 | **17.179** |

Converged: 17.181 m/s. → [[SESA3043 3.6 - Viscous-Inviscid Interaction#5. Worked example: revision 3.6 Q3, a wind-tunnel test section|3.6 §5]]

## Links

- [[SESA3043 Advanced Aeronautics Hub]] · [[SESA3043 Formula Sheet]]
- Earlier sheets: [[SESA3043 Ch1 Revision Questions - Worked Solutions]] · [[SESA3043 Ch2 Revision Questions - Worked Solutions]]
