---
title: "Magnetic Flux and Flux Density"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["magnetic flux", "flux density", "Phi = BA", "flux linkage", "tesla", "weber"]
tags: [feeg1004, concept, magnetism]
status: complete
parent_lectures: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
related_concepts: ["[[Faraday's Law and Lenz's Law]]", "[[Magnetomotive Force and Reluctance]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W03-2ab Magnetism and Induction - Recorded.pdf", "02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Magnetic Flux and Flux Density

Magnetic flux density $B$, measured in tesla, describes how densely the field lines are packed. Magnetic flux $\Phi$, measured in webers, counts the field lines passing normally through a given area, and flux linkage $\lambda = N\Phi$ is that flux multiplied by the number of turns of a coil.

$$
\Phi = \int\mathbf B\cdot d\mathbf A\ \ [\mathrm{Wb} = \mathrm{T\,m^2} = \mathrm{V\,s}],\qquad \Phi = BA\cos\theta\ \text{(uniform)},\qquad \lambda = N\Phi\ \text{(flux linkage)}
$$

Only the component of $\mathbf B$ normal to the area contributes, which gives the $\cos\theta$ factor for a uniform field. A $0.1\ \mathrm{m^2}$ coil in $2\ \mathrm T$ at angle $\theta$ links $\Phi = 0.2\cos\theta\ \mathrm{Wb}$. As a magnet passes a coil, counting field lines gives a flux sequence of $+1$, $0$, $-1$, $-2$ as it moves (lecture 2a).

Field lines always form closed loops, because there are no magnetic monopoles: they run from N to S outside a magnet and from S to N inside it. In diagrams, ⊗ marks a field into the page and ⊙ a field out of it.

Machine steel is kept below about $1.5\ \mathrm T$, because above that it saturates and extra current produces little extra flux ([[Transformer EMF Equation]]).

## Related

- [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]
- [[Faraday's Law and Lenz's Law]] · [[Magnetomotive Force and Reluctance]] · [[Inductance]]
- Maths: [[Flux Integrals]]
- Sources: Recorded lecture 2a; Sharkh machines notes §2
