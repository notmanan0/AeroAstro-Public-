---
title: "Panel Method"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 2: Exact Solutions and Methods for Potential Flow"
aliases: ["panel methods", "source panel method", "doublet panel method", "Hess-Smith method", "boundary element method", "surface singularity method", "influence coefficient", "collocation point", "self-induced velocity"]
tags: [sesa3043, concept, potential-flow, panel-method, cfd]
status: complete
parent_lectures: ["[[SESA3043 2.3 - Panel Methods]]"]
related_concepts: ["[[Lumped Vortex Method]]", "[[General Doublet]]", "[[Kutta Condition]]"]
sources: ["02 - Sources/Lectures/Ch2 Exact Solution and methods for potential flow.pdf", "02 - Sources/Lectures/Ch2_Panel_Method_Explainer.pdf"]
---

# Panel Method

A panel method represents a body surface by $N$ straight panels, each carrying a constant-strength singularity. Flow tangency is imposed at a control point on each panel, a Kutta condition closes the system, and the resulting linear system is solved for the strengths.

For a panel lying on $x_1\le x_0\le x_2$, the elementary singularities are:

| Panel | Far field | On the panel |
|---|---|---|
| source $\sigma$ | $u=\frac{\sigma}{2\pi}\ln\frac{r_1}{r_2}$, $w=\frac{\sigma}{2\pi}(\theta_2-\theta_1)$ | $w_\pm=\pm\sigma/2$ |
| vortex $\gamma$ | $u=\frac{\gamma}{2\pi}(\theta_2-\theta_1)$, $w=\frac{\gamma}{2\pi}\ln\frac{r_2}{r_1}$ | $u_\pm=\pm\gamma/2$ |
| doublet $\mu$ | $\phi=\frac{\mu}{2\pi}(\theta_1-\theta_2)$ | $\phi_\pm=\mp\mu/2$ |

The course builds two complete methods from these. The source + vortex method is a Neumann method: the unknowns are $\sigma_1\ldots\sigma_N$ and one vortex strength $\gamma$, tangency reads $\sum a_{ij}\sigma_j+\hat a_i\gamma=U_\infty\sin(\beta_i-\alpha)$, and the Kutta condition comes either from an extra control point on the trailing-edge bisector or from requiring equal speeds on the two trailing-edge panels, $q_{t,1}=-q_{t,N}$. The minus sign matters: the signed components are opposite, and writing $q_{t,1}=q_{t,N}$ makes the system singular. The doublet method is a Dirichlet method: the unknowns are $\mu_1\ldots\mu_N$ and a wake doublet $\mu_w$, the condition is zero total potential inside the body, the Kutta condition is $\mu_1-\mu_N-\mu_w=0$, and then $C_L=2\mu_w/(U_\infty c)$ and $q_t=-\mathrm d\mu/\mathrm ds$.

![[aa_panel_method_validation.png|700]]

## Related

- [[SESA3043 2.3 - Panel Methods]] · [[Lumped Vortex Method]] · [[Kármán–Trefftz Transformation]] · [[Vortex Sheet]]
