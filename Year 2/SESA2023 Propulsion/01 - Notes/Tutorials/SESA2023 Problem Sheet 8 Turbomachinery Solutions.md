---
title: "SESA2023 Problem Sheet 8 Turbomachinery Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 4: Turbomachinery and Propellers"
tags:
  - sesa2023
  - tutorial-solutions
  - turbomachinery
  - velocity-triangles
sheet: "Exercises Week 8 (turbomachinery)"
theory_notes: ["[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
key_concepts: ["[[Velocity Triangles]]", "[[Degree of Reaction]]", "[[Euler Work Equation]]", "[[Stagnation Properties]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 08 - Turbomachinery.pdf"]
---

# SESA2023 Problem Sheet 8 Turbomachinery Solutions

> [!abstract] Sheet Info
> Three questions: a compressor cascade (flow functions), velocity-triangle identities, and a 50 % reaction HPC stage. All the printed answers are reproduced ✔.

## Theory Links
- [[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]
- [[Velocity Triangles]] · [[Degree of Reaction]] · [[Euler Work Equation]]

---

## Q8.1: 2-D compressor cascade, $M_1 = 0.78$, $\alpha_1 = 45^\circ$, $\alpha_2 = 5^\circ$, $p_{01} = 1$ bar, $T_{01} = 300$ K
**Mass flow per unit frontal (axial-normal) area.** The data-book flow function applies normal to the velocity:

$$
\frac{\dot m\sqrt{c_pT_0}}{A_np_0} = \frac{\gamma}{\sqrt{\gamma-1}}M\Big(1+\tfrac{\gamma-1}{2}M^2\Big)^{-3} = 2.2136(0.78)(1.1217)^{-3} = 1.2235
$$

$$
\frac{\dot m}{A_n} = \frac{1.2235\times10^5}{\sqrt{1005\times300}} = 222.8\text{ kg s}^{-1}\text{m}^{-2},\qquad\frac{\dot m}{A_{frontal}} = 222.8\cos45^\circ = \boxed{157.5\text{ kg s}^{-1}\text{m}^{-2}}\;✔
$$

**Exit Mach number (isentropic).** $p_0$, $T_0$ and the axial area are unchanged, so continuity gives $F(M_2)\cos\alpha_2 = F(M_1)\cos\alpha_1$:

$$
F(M_2) = \frac{1.2235(0.7071)}{0.9962} = 0.8685\;\Rightarrow\;M_{2s} = \boxed{0.440}\;✔
$$

**Static pressure ratio**:

$$
\frac{p_2}{p_1} = \frac{(1+0.2\times0.78^2)^{3.5}}{(1+0.2\times0.44^2)^{3.5}} = \boxed{1.31}\;✔
$$

Turning towards axial increases the flow area by $\cos5^\circ/\cos45^\circ = 1.41$. The flow diffuses from M 0.78 to M 0.44, and the pressure rises 31 %.

## Q8.2: Identities for a constant-$V_x$ compressor stage
With $V_{\theta,rel} = V_\theta-U$ and $V_\theta = V_x\tan\alpha$: $U = V_x(\tan\alpha_1-\tan\alpha_{1,rel})$. So

$$
\frac{V_x}{U} = \frac{1}{\tan\alpha_1-\tan\alpha_{1,rel}} = \frac{1}{\tan\alpha_2-\tan\alpha_{2,rel}}
$$

Euler: $\Delta h_0 = U(V_{\theta2}-V_{\theta1}) = UV_x(\tan\alpha_2-\tan\alpha_1)$. Using $\tan\alpha_2 = \tan\alpha_{2,rel}+U/V_x$:

$$
\frac{\Delta h_0}{U^2} = \frac{V_x}{U}(\tan\alpha_2-\tan\alpha_1) = 1+\frac{V_x}{U}(\tan\alpha_{2,rel}-\tan\alpha_1)
$$

**Static enthalpy rise per row**:
- The rotor conserves **relative** stagnation enthalpy (rothalpy at constant $r$), so $\Delta h_{rotor} = \tfrac12(V_{1,rel}^2-V_{2,rel}^2) = \tfrac12V_{1,rel}^2\big[1-(\cos\alpha_{1,rel}/\cos\alpha_{2,rel})^2\big]$, since $V_{rel} = V_x/\cos\alpha_{rel}$.
- The stator conserves $h_0$, so $\Delta h_{stator} = \tfrac12(V_2^2-V_3^2) = \tfrac12V_2^2\big[1-(\cos\alpha_2/\cos\alpha_3)^2\big]$.

For a compressor, $\alpha$ and $\alpha_{rel}$ have opposite signs. The tangents *add* in $V_x/U$ and *subtract* in $\Delta h_0/U^2$. For incompressible, loss-free flow, $\Delta p/(\rho U^2) = \Delta h/U^2$.

## Q8.3: 50 % reaction HPC stage, $V_x = 171$ m/s $= 0.55U$, $\psi = 0.439$
$U = 171/0.55 = 310.9$ m/s. **Mirror symmetry** gives $\alpha_1 = -\alpha_{2,rel}$ and $\alpha_2 = -\alpha_{1,rel}$. Then

$$
\tan\alpha_1+\tan\alpha_2 = \frac{1}{\phi} = 1.818,\qquad\tan\alpha_2-\tan\alpha_1 = \frac{\psi}{\phi} = 0.798
$$

$$
\tan\alpha_2 = 1.308\;\Rightarrow\;\boxed{\alpha_2 = 52.6^\circ},\qquad\tan\alpha_1 = 0.510\;\Rightarrow\;\boxed{\alpha_1 = 27.0^\circ}
$$

$$
\boxed{\alpha_{1,rel} = -52.6^\circ},\qquad\boxed{\alpha_{2,rel} = -27.0^\circ}\;✔
$$

Check the degree of reaction: $R = 1-\tfrac{\phi}{2}(\tan\alpha_1+\tan\alpha_2) = 1-0.275(1.818) = 0.500$ ✔.

**Sketch**:
- The **rotor** blade is cambered from about −52.6° (inlet) to −27.0° (exit), turning the relative flow towards axial.
- The **stator** is its mirror image, from +52.6° to +27.0°.
- The first rotor needs **inlet guide vanes** to supply the +27° swirl.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 08 - Turbomachinery.pdf`. All values checked in Python.
