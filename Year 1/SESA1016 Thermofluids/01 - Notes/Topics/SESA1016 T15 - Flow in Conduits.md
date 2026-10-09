---
title: "SESA1016 T15 - Flow in Conduits"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part E: Viscous Losses"
order: 15
tags: [sesa1016, pipe-flow, head-loss, friction-factor, pumps]
aliases: ["Flow in Conduits", "Internal Flow"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
next_topics: []
key_concepts: ["[[Darcy Friction Factor]]", "[[Major and Minor Head Losses]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 15.pdf"]
---

# SESA1016 T15 - Flow in Conduits

> [!abstract] Summary
> Pipe flow begins with developing boundary layers and becomes fully developed after they merge. Reynolds number determines the regime. Laminar flow admits an exact parabolic solution; turbulent flow requires empirical friction correlations. Distributed wall friction and local fittings consume mechanical-energy head, while pumps add it.

## 1. Developing and fully developed flow

At a pipe entrance the profile changes with $x$. Once fully developed,

$$
\frac{\partial u}{\partial x}=0
$$

for the profile shape, although pressure continues falling to overcome wall shear.

Approximate entrance lengths:

$$
\frac{L_e}{D}\approx0.06Re_D\quad\text{(laminar)},qquad
\frac{L_e}{D}\approx4.4Re_D^{1/6}\quad\text{(turbulent)}.
$$

![[tf_pipe_profiles.png|720]]

## 2. Flow regime

$$
Re_D=\frac{\rho\bar VD}{\mu}=\frac{\bar VD}{\nu}.
$$

For a circular pipe:

- $Re_D\lesssim2300$: laminar;
- $2300\lesssim Re_D\lesssim4000$: transitional;
- $Re_D\gtrsim4000$: usually turbulent.

Thresholds depend on disturbance and roughness.

## 3. Laminar circular-pipe flow

Balancing pressure force and viscous shear gives the Hagen-Poiseuille profile:

$$
u(r)=\frac{-dp/dx}{4\mu}(R^2-r^2)
=2\bar V\left(1-\frac{r^2}{R^2}\right).
$$

Thus

$$
u_{max}=2\bar V,qquad
\dot V=\frac{\pi R^4}{8\mu}\left(-\frac{dp}{dx}\right),qquad
f=\frac{64}{Re_D}.
$$

## 4. Turbulent profiles

Turbulent mixing creates a fuller mean profile and a steep wall gradient. A simple power-law approximation is

$$
\frac{u}{u_{max}}=\left(1-\frac rR\right)^{1/n},\qquad n\approx7,
$$

but friction is normally obtained from a Moody chart or correlation rather than differentiating this profile at the wall.

## 5. Darcy-Weisbach equation

$$
\boxed{h_f=f\frac LD\frac{\bar V^2}{2g}},qquad
\Delta p_f=\rho gh_f=f\frac LD\frac{\rho\bar V^2}{2}.
$$

The course uses the **Darcy** friction factor. It is four times the Fanning factor.

For turbulent flow, $f$ depends on $Re_D$ and relative roughness $\varepsilon/D$ through Colebrook:

$$
\frac1{\sqrt f}=-2\log_{10}\left(\frac{\varepsilon/D}{3.7}+\frac{2.51}{Re_D\sqrt f}\right).
$$

![[tf_moody_chart.png|700]]

## 6. Minor losses

Fittings, entrances, exits, valves and area changes give

$$
h_m=K\frac{\bar V^2}{2g}.
$$

Despite the name, their total can dominate in a short system. Use the velocity specified for each $K$, typically the local mean pipe velocity.

$$
h_L=\left(f\frac LD+\sum K\right)\frac{\bar V^2}{2g}.
$$

See [[Major and Minor Head Losses]].

## 7. Extended Bernoulli and pumps

$$
\frac{p_1}{\rho g}+\frac{V_1^2}{2g}+z_1+h_p-h_t-h_L
=\frac{p_2}{\rho g}+\frac{V_2^2}{2g}+z_2.
$$

$$
P_{fluid}=\rho g\dot Vh_p,qquad P_{shaft}=\frac{P_{fluid}}{\eta_p}.
$$

![[tf_conduit_head_loss.png|720]]

## 8. Two nonlinear problem types

1. **Flow rate known**: calculate $Re_D$, obtain $f$, then find $h_L$ or required pump power.
2. **Pressure/head known**: velocity is unknown, so $Re_D$ and $f$ are also unknown. Iterate:
   - guess $f$;
   - solve energy equation for $V$;
   - update $Re_D$ and $f$;
   - repeat to convergence.

## Links

- Concepts: [[Darcy Friction Factor]] · [[Major and Minor Head Losses]]
- Tutorial: [[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]]
- Formulae: [[SESA1016 Formula Sheet#13. Flow in conduits]]
- Continues in Propulsion/CFD: [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]] · [[Friction and Heat Addition in Constant-Area Ducts]] · [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]

## Sources

- `02 - Sources/Lectures/Chapter 15.pdf`, §§15.1-15.8.
