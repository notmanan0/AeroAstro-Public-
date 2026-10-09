---
title: "Panel Method"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["panel methods", "source panel method", "doublet panel method", "Hess-Smith method"]
tags: [sesa3043, concept, potential-flow, panel-method, cfd]
status: complete
parent_lectures: ["[[SESA3043 2.3 - Panel Methods]]"]
related_concepts: ["[[Lumped Vortex Method]]", "[[General Doublet]]", "[[Kutta Condition]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf", "02 - Sources/Lectures/Ch2_Panel_Method_Explainer.pdf"]
---

# Panel Method

## Definition

> [!note] Definition
> Represent a body surface by $N$ straight panels carrying constant-strength singularities, impose flow tangency at a control point on each, close the system with a Kutta condition, and solve the linear system for the strengths.

## Elementary panels (panel on $x_1\le x_0\le x_2$)

| Panel | Far field | On the panel |
|---|---|---|
| source $\sigma$ | $u=\frac{\sigma}{2\pi}\ln\frac{r_1}{r_2}$, $w=\frac{\sigma}{2\pi}(\theta_2-\theta_1)$ | $w_\pm=\pm\sigma/2$ |
| vortex $\gamma$ | $u=\frac{\gamma}{2\pi}(\theta_2-\theta_1)$, $w=\frac{\gamma}{2\pi}\ln\frac{r_2}{r_1}$ | $u_\pm=\pm\gamma/2$ |
| doublet $\mu$ | $\phi=\frac{\mu}{2\pi}(\theta_1-\theta_2)$ | $\phi_\pm=\mp\mu/2$ |

## Two complete methods

- **Source + vortex (Neumann):** unknowns $\sigma_1\ldots\sigma_N,\gamma$; tangency $\sum a_{ij}\sigma_j+\hat a_i\gamma=U_\infty\sin(\beta_i-\alpha)$; Kutta by an extra control point on the TE bisector, or $q_{t,1}=q_{t,N}$.
- **Doublet (Dirichlet):** unknowns $\mu_1\ldots\mu_N,\mu_w$; total potential zero inside the body; Kutta $\mu_1-\mu_N-\mu_w=0$; $C_L=2\mu_w/(U_\infty c)$; $q_t=-\mathrm d\mu/\mathrm ds$.

![[aa_panel_method_validation.png|700]]

## Related

- [[SESA3043 2.3 - Panel Methods]] · [[Lumped Vortex Method]] · [[Kármán–Trefftz Transformation]] · [[Vortex Sheet]]
