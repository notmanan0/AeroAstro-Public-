---
title: "SESA1016 T14 - Boundary Layers and the Origin of Drag"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part E: Viscous Losses"
order: 14
tags: [sesa1016, boundary-layer, drag, separation, transition]
aliases: ["Origin of Drag"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
next_topics: ["[[SESA1016 T15 - Flow in Conduits]]"]
key_concepts: ["[[Boundary-layer Thickness Measures]]", "[[Skin-friction and Pressure Drag]]", "[[Reynolds Number]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 10 - Drag and External Flows Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 14.pdf"]
---

# SESA1016 T14 - Boundary Layers and the Origin of Drag

> [!abstract] Summary
> Viscosity matters most near a solid surface, where no slip creates a boundary layer. Wall shear produces skin-friction drag; adverse pressure gradients can make the low-momentum near-wall fluid reverse and separate, producing a wake and pressure drag. Turbulence raises wall shear but can delay separation, so it may reduce the total drag of a bluff body.

## 1. Boundary-layer picture

Over a flat plate, $u=0$ at the wall and approaches $U_\infty$ outside a thin region. The boundary layer grows downstream because viscous momentum diffusion has had longer to act.

$$
Re_x=\frac{U_\infty x}{\nu}
$$

helps determine whether the layer is laminar, transitional or turbulent.

## 2. Thickness measures

Geometric thickness $\delta$ is usually defined by $u(\delta)=0.99U_e$. Two integral measures have stronger conservation meaning:

$$
\boxed{\delta^*=\int_0^\infty\left(1-\frac u{U_e}\right)dy}
$$

$$
\boxed{\theta=\int_0^\infty\frac u{U_e}\left(1-\frac u{U_e}\right)dy}
$$

- $\delta^*$: equivalent outward displacement of the inviscid stream;
- $\theta$: momentum-deficit thickness;
- shape factor $H=\delta^*/\theta$ characterises profile fullness.

See [[Boundary-layer Thickness Measures]].

![[tf_boundary_layers.png|720]]

## 3. Wall shear and friction coefficient

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_0,qquad
c_f=\frac{\tau_w}{\tfrac12\rho U_e^2}.
$$

For zero pressure gradient, the momentum integral equation reduces to

$$
c_f=2\frac{d\theta}{dx}.
$$

The momentum lost from the outer stream appears as wall drag.

## 4. Laminar versus turbulent

| | Laminar | Turbulent |
|---|---|---|
| mixing | molecular | strong eddy mixing |
| profile | less full | fuller |
| wall gradient | lower | higher |
| skin friction | lower | higher |
| resistance to separation | lower | higher |

Flat-plate estimates are collected in [[SESA1016 Formula Sheet#12. Boundary layers and drag]]. They assume smooth surface and zero pressure gradient.

## 5. Pressure gradients and separation

- favourable gradient: $dp/dx<0$, outer flow accelerates;
- adverse gradient: $dp/dx>0$, outer flow decelerates.

An adverse gradient acts against the already slow near-wall fluid. At separation:

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_w=0,
$$

followed by local reverse flow. The wake has low pressure and creates pressure drag.

![[tf_drag_separation.png|700]]

## 6. Drag decomposition

$$
D=D_f+D_p,qquad C_D=\frac{D}{\tfrac12\rho U_\infty^2A_{ref}}.
$$

- skin-friction drag: tangential wall shear;
- pressure/form drag: streamwise component of normal pressure forces.

A streamlined body delays separation and reduces pressure drag. A bluff body creates a broad wake.

## 7. Transition can reduce total drag

Turbulence increases skin friction, but its fuller profile has more near-wall momentum and can remain attached longer. Golf-ball dimples exploit this: earlier transition can shrink the wake enough that the reduction in pressure drag exceeds the friction penalty.

## 8. Computing force from surface data

Resolve both pressure and shear contributions over the surface:

$$
\mathbf F=\int_S(-p\mathbf n+\boldsymbol\tau_w)\,dS.
$$

For discrete pressure taps, integrate numerically with a consistent surface orientation and reference pressure.

## Links

- Concepts: [[Boundary-layer Thickness Measures]] · [[Skin-friction and Pressure Drag]]
- Tutorial: [[SESA1016 Problem Sheet 10 - Drag and External Flows Solutions]]
- Continues in Aerodynamics/CFD: [[SESA2022 T2 - Boundary Layers]] · [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]] · [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- Next: [[SESA1016 T15 - Flow in Conduits]]

## Sources

- `02 - Sources/Lectures/Chapter 14.pdf`, §§14.1-14.11.
