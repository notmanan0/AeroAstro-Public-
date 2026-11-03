---
title: "Divergence Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Gauss's theorem", "Gauss divergence theorem"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
related_concepts: ["[[Flux Integrals]]", "[[Jacobian and Volume Elements]]", "[[Stokes' Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture29_vector09.pdf", "02 - Sources/Lectures/MATH2048 Lecture 29.txt"]
---

# Divergence Theorem

The **divergence theorem** (Gauss's theorem) states that for a region $V$ bounded by a closed surface $S$ with outward normal, $\oiint_S\mathbf F\cdot d\mathbf S=\iiint_V\nabla\cdot\mathbf F\,dV$.

The divergence is the outflow per unit volume, and when the region is cut into small boxes the fluxes through shared internal faces cancel, leaving only the outer surface. The normal must point outward, and $\nabla\cdot\mathbf F$ must exist everywhere inside. It turns a flux through a complicated closed surface, which may need splitting into smooth pieces, into a single volume integral: for $\mathbf F=\mathbf r$ through a closed cylinder, $\nabla\cdot\mathbf r=3$ gives $3\pi a^2h$ at once. An open surface can be closed with a simple flat piece whose flux is then subtracted.

Applied to a fixed control volume, the theorem converts the integral (weak) form of a conservation law into the differential (strong) form, such as the continuity equation $\partial_t\rho+\nabla\cdot(\rho\mathbf v)=0$. At a shock the divergence doesn't exist, so only the weak form survives, which is why shock-capturing schemes are built on it.

## Related

- Derivation and examples: [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem#2. The divergence theorem (L29)|VC5 §2]]
- [[Flux Integrals]] · [[Divergence, Curl and the Laplacian]] · [[Stokes' Theorem]] · [[Jacobian and Volume Elements]]
