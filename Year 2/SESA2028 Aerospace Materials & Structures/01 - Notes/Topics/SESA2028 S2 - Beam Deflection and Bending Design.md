---
title: "SESA2028 S2 - Beam Deflection and Bending Design"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 2
tags: [sesa2028, structures, deflection, beam]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
next_topics: ["[[SESA2028 S3 - Shear Flow and Shear Centre]]"]
key_concepts: ["[[Moment Curvature Relation]]", "[[Elastic Curve]]", "[[Section Modulus]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 2 - Bending Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL2 Bending stress and deflection.pdf"]
---

# SESA2028 S2 - Beam Deflection and Bending Design

> [!abstract] Summary
> Beam design has two independent checks: stress and stiffness. A beam may remain elastic yet deflect too far, or be acceptably stiff while exceeding an allowable stress near a support or load introduction point.

## 1. Euler-Bernoulli model

The lecture model assumes a slender, initially straight beam, linear elasticity, small deflection, and plane cross-sections remaining plane and normal to the neutral axis. Shear deformation is neglected.

For bending about a principal axis,

$$
EI\frac{d^2v}{dx^2}=M(x),\qquad
\theta=\frac{dv}{dx}.
$$

The sign on the right-hand side depends on the selected moment and deflection convention; consistency matters more than memorising one diagram.

## 2. Four useful integrations

The relationships

$$
\frac{dV}{dx}=-w(x),\qquad
\frac{dM}{dx}=V(x),\qquad
EI\frac{d\theta}{dx}=M(x),\qquad
\frac{dv}{dx}=\theta(x)
$$

form one chain. Concentrated loads cause jumps in shear; concentrated moments cause jumps in bending moment. Deflection and slope remain continuous unless the structure contains an internal release.

## 3. Boundary and continuity conditions

| Location | Kinematic conditions |
|---|---|
| fixed end | $v=0$, $\theta=0$ |
| simple support | $v=0$ |
| free end with no applied tip actions | $M=0$, $V=0$ |
| internal point with no hinge | $v$ and $\theta$ continuous |
| internal hinge | $v$ continuous, $M=0$ |

Write these before integrating. Most lost marks in piecewise-beam questions come from trying to remember a canned deflection formula that does not match the actual support or load arrangement.

## 4. Stress check

For principal-axis bending,

$$
\sigma_{xx}=-\frac{M_z}{I_{zz}}y+\frac{M_y}{I_{yy}}z,
$$

and for one-axis bending the maximum magnitude is

$$
|\sigma_{\max}|=\frac{|M|c}{I}=\frac{|M|}{Z},\qquad Z=\frac{I}{c}.
$$

Use the maximum moment along the beam and the appropriate extreme-fibre distance on the tension and compression sides. Unsymmetric sections require the coupled treatment from [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]].

## 5. Stiffness check

Common reference results are

$$
v_{tip}=\frac{FL^3}{3EI}\quad\text{(cantilever, tip force)},
$$

$$
v_{max}=\frac{5wL^4}{384EI}\quad\text{(simply supported, full-span UDL)},
$$

$$
v_{tip}=\frac{ML^2}{2EI},\qquad \theta_{tip}=\frac{ML}{EI}\quad\text{(cantilever, tip moment)}.
$$

These are checks, not substitutes for a derivation. If an overhang, eccentric action or axial load is present, use integration, virtual work or the beam-column equation instead.

## 6. Design interpretation

- Increasing depth is usually far more effective than adding the same material near the neutral axis because $I$ weights area by distance squared.
- A local stress maximum and a global deflection maximum need not occur at the same point.
- Thin-walled open sections can have excellent bending stiffness but poor torsional stiffness.
- A force applied away from the [[Shear Centre]] causes twist even when its line of action passes through the centroid.

## 7. Verification checks

- Units: $EI$ in $\mathrm{N\,mm^2}$ with $x$ in mm gives deflection in mm.
- At a free end, an unloaded beam must have zero internal $M$ and $V$.
- Reactions must satisfy overall force and moment equilibrium.
- A doubled span produces an eightfold cantilever tip deflection under the same tip force.

## Year 1 foundation
- [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] (SFD/BMD, $dM/dx = Q$), [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] (Macaulay, standard cases) and [[FEEG1002 A6 - Statically Indeterminate Beams]] (propped and fixed beams). **Sign convention change**: FEEG1002 takes $v$ positive downwards with $EI\,v'' = -M$ (sagging $M$ positive).
