---
title: "State-Space Representation"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["state space", "state equation", "A B C D matrices", "LTI system"]
tags: [sesa2027, concept, state-space]
status: complete
parent_lectures: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]", "[[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]]"]
related_concepts: ["[[Transfer Function]]", "[[Characteristic Equation and Eigenvalues]]", "[[Aerodynamic Stability Derivatives]]"]
sources: ["02 - Sources/Lectures/Lecture 1.04.pdf", "02 - Sources/Lectures/Lecture 1.11.pdf", "02 - Sources/Lectures/Lecture 3.05.pdf"]
---

# State-Space Representation

## Definition

> [!note] Definition
> A linear time-invariant (LTI) system written as first-order matrix ODEs:
> $$\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u,\qquad \mathbf y = \mathbf C\mathbf x+\mathbf D\mathbf u$$
> - $\mathbf x$ is the state (the minimum set of variables describing the system);
> - $\mathbf u$ is the input and $\mathbf y$ the output;
> - $\mathbf A$ is the system (dynamics) matrix, $\mathbf B$ the input matrix, $\mathbf C$ the output matrix and $\mathbf D$ the feedthrough matrix.

## Explanation
- **Aircraft longitudinal model**: $\mathbf x = [u, w, q, \theta]^T$ and $\mathbf u = [\eta, \Delta T, u_g, w_g]^T$.
  - It comes from $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u$, so $\mathbf A = \mathbf M^{-1}\mathbf A'$ and $\mathbf B = \mathbf M^{-1}\mathbf B'$.
  - $\mathbf M$ contains $m$, $I_{yy}$ and the $\dot w$ derivatives.
- $\mathbf A$ holds the derivatives with respect to the **states**. $\mathbf B$ holds the derivatives with respect to the **controls and gusts**.
- **Free response**: $\mathbf x = \mathbf x_0e^{\lambda t}$, where the $\lambda$ are the eigenvalues of $\mathbf A$ ([[Characteristic Equation and Eigenvalues]]).
- **To a transfer function**: $G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D$ ([[Transfer Function]]).
- **Choosing $\mathbf C$**: it selects what the sensor measures, e.g. $\mathbf C = [0,0,1,0]$ for pitch rate. $\mathbf D = 0$ because sensors do not respond directly to control inputs.
- **Sensors**: in principle they have their own state space (diaphragm displacement, voltages, ...). In practice these matrices are hard to identify, so sensors are usually treated as black-box transfer functions ([[Sensor Dynamic Models]]).

## Examples
- SPO approximation: $\mathbf x = [w,q]^T$, a 2×2 $\mathbf A$ ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]).
- PS2 Q3: from the 2×2 $\mathbf A$, $\mathbf B$ and $\mathbf C = [0\ 1]$, $G(s) = -4.888(s+0.1609)/(s^2+0.7446s+18.73)$ ([[SESA2027 Practice Problems 2 Solutions]]).

## Related
- [[Transfer Function]] · [[Characteristic Equation and Eigenvalues]] · [[Aerodynamic Stability Derivatives]] · [[Small Perturbation Linearisation]]

## Sources
- Lectures 1.04, 1.11, 3.05
