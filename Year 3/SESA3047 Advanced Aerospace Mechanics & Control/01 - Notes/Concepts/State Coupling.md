---
title: "State Coupling"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["coupling between states", "coupled states", "cross-coupling", "decoupled system", "off-diagonal coupling", "coupling"]
tags: [sesa3047, concept, state-space, coupling, modes]
status: complete
coverage: "Introduced through the Euler-angle and inertia coupling of Chapters 3–4 and Lab 1; stated as a central idea of the module in L18 ll. 421–436 (Mon 16 Nov)"
parent_lectures: ["[[SESA3047 6.2 - Phugoid Approximation]]", "[[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates]]", "[[SESA3047 4.1 - Inertia Models and Rotor Dynamics]]"]
related_concepts: ["[[Eigenvalue Decomposition]]", "[[Eigenvectors as Mode Shapes]]", "[[Separation of Time Scales]]", "[[Longitudinal and Lateral Dynamics]]"]
sources: ["02 - Sources/Lectures/16 November 2026 at 11_51_48.txt", "02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf"]
---

# State Coupling

Two states are coupled when the rate of change of one depends on the value of the other; in $\dot{\mathbf x}=\mathbf A\mathbf x$ that is a non-zero off-diagonal entry $a_{ij}$, $i\neq j$.

A diagonal state matrix has no coupling. Each equation is then $\dot x_i=a_{ii}x_i$ and can be solved alone, a disturbance to one state never reaches another, and the unit vectors are eigenvectors, each a single state with eigenvalue $a_{ii}$ (when two diagonal entries are equal, mixtures of those two states are eigenvectors too). As soon as off-diagonal terms appear, a disturbance spreads, and the natural motions are combinations of states: the eigenvectors. Diagonalising, $\mathbf A=\mathbf V\boldsymbol\Lambda\mathbf V^{-1}$, finds the coordinates (the modal coordinates) in which the coupling disappears ([[Eigenvalue Decomposition]]).

The idea appears throughout SESA3047. The Euler-angle rates couple the attitude angles geometrically through $\mathbf H(\boldsymbol\Phi)$, and $\boldsymbol\omega\times\mathbf J\boldsymbol\omega$ couples the body rates inertially (Chapters 3–4, Lab 1 Exercise 3). Linearising about steady straight flight decouples the longitudinal from the lateral states, but within the longitudinal set the matrix is nearly full. The short-period oscillation is mainly a coupling of $w$ and $q$, the phugoid mainly of $u$ and $\theta$, which is what the SPO and phugoid approximations exploit when they keep only the dominant pair of each mode.

Coupling can also be a structural zero that vanishes for special parameter values: with $J_{xx}=J_{zz}$ the inertial coupling into $\dot q$ disappears, and with $\mathring M_u=0$ a speed change no longer produces a pitching moment directly. "Coupled" is a statement about the matrix entries, so it should be checked against them rather than assumed.

## Related

- In the longitudinal modes: [[SESA3047 6.2 - Phugoid Approximation#3. Which states matter: time scales and coupling|6.2 §3]]; in the Euler-angle rates: [[SESA3047 3.1 - Rotational Kinematics and Euler-Angle Rates#Exposing the coupling: switch off two variables|3.1, exposing the coupling]]; inertia coupling: [[SESA3047 4.1 - Inertia Models and Rotor Dynamics#Inertia coupling with no external moment|4.1]]
- [[Eigenvalue Decomposition]] · [[Eigenvectors as Mode Shapes]] · [[Separation of Time Scales]] · [[Longitudinal and Lateral Dynamics]]
