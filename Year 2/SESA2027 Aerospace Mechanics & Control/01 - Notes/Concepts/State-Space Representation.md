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

A linear time-invariant system in state-space form is a set of first-order matrix ODEs,

$$
\dot{\mathbf x} = \mathbf A\mathbf x+\mathbf B\mathbf u,\qquad \mathbf y = \mathbf C\mathbf x+\mathbf D\mathbf u,
$$

where $\mathbf x$ is the state (the smallest set of variables that describes the system), $\mathbf u$ the input and $\mathbf y$ the output. $\mathbf A$ is the system matrix, $\mathbf B$ the input matrix, $\mathbf C$ the output matrix and $\mathbf D$ the feedthrough matrix.

For the longitudinal aircraft, $\mathbf x = [u, w, q, \theta]^T$ and $\mathbf u = [\eta, \Delta T, u_g, w_g]^T$. The equations first come out as $\mathbf M\dot{\mathbf x} = \mathbf A'\mathbf x+\mathbf B'\mathbf u$, where $\mathbf M$ holds $m$, $I_{yy}$ and the $\dot w$ derivatives, so $\mathbf A = \mathbf M^{-1}\mathbf A'$ and $\mathbf B = \mathbf M^{-1}\mathbf B'$. $\mathbf A$ then holds the derivatives with respect to the states and $\mathbf B$ those with respect to the controls and gusts. The SPO approximation cuts this down to $\mathbf x = [w,q]^T$ with a 2×2 $\mathbf A$ ([[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]).

The free response is $\mathbf x = \mathbf x_0e^{\lambda t}$ with $\lambda$ the eigenvalues of $\mathbf A$ ([[Characteristic Equation and Eigenvalues]]), and the transfer function is $G(s) = \mathbf C(s\mathbf I-\mathbf A)^{-1}\mathbf B+\mathbf D$ ([[Transfer Function]]). $\mathbf C$ picks out what the sensor measures, for example $\mathbf C = [0,0,1,0]$ for pitch rate, and $\mathbf D = 0$ because sensors don't respond directly to control inputs. In PS2 Q3, the 2×2 $\mathbf A$ and $\mathbf B$ with $\mathbf C = [0\ 1]$ give $G(s) = -4.888(s+0.1609)/(s^2+0.7446s+18.73)$ ([[SESA2027 Practice Problems 2 Solutions]]). Sensors have their own state space in principle (diaphragm displacement, voltages and so on), but those matrices are hard to identify, so they are usually treated as black-box transfer functions ([[Sensor Dynamic Models]]).

## Related

- [[Transfer Function]] · [[Characteristic Equation and Eigenvalues]] · [[Aerodynamic Stability Derivatives]] · [[Small Perturbation Linearisation]]
- Year 3: [[SESA3047 5.1 - State-Space Form and Linearisation]] · [[SESA3047 5.3 - Building State-Space Models from ODEs, Transfer Functions and Block Diagrams]] · [[Transfer Function to State-Space Conversion]]
