---
title: "Magnetomotive Force and Reluctance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["mmf", "reluctance", "magnetic circuit", "F = Ni", "magnetic field intensity H"]
tags: [feeg1004, concept, magnetism, machines]
status: complete
parent_lectures: ["[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
related_concepts: ["[[Magnetic Flux and Flux Density]]", "[[Inductance]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf"]
---

# Magnetomotive Force and Reluctance

Magnetomotive force (mmf) $\mathcal F = Ni$ is the drive that a current-carrying coil applies to a magnetic circuit, and reluctance $\mathcal R$ is the circuit's opposition to flux. Together they give the magnetic-circuit equivalent of Ohm's law, $\mathcal F = \mathcal R\Phi$.

$$
\mathcal F = Ni = \oint H\,dl\approx\sum_kH_kl_k,\qquad \mathcal F = \mathcal R\Phi,\qquad \mathcal R = \frac{l}{\mu_0\mu_rA}
$$

In this analogy mmf, measured in ampere-turns, plays the part of voltage, flux the part of current, and reluctance the part of resistance. Reluctance depends on the path length, the cross-section and the permeability, just as resistance depends on length, area and resistivity. In a toroid, $4\ \mathrm A$ through 100 turns gives $400$ ampere-turns, and with $\mathcal R = 1.68\times10^6\ \mathrm{A/Wb}$ the flux is $\Phi = 400/(1.68\times10^6) = 0.238\ \mathrm{mWb}$.

Steel has $\mu_r$ of order $10^3$, so flux follows the core much as current follows a wire. An air gap has $\mu_r = 1$, so even a short gap usually dominates the total reluctance. The linear model also has a limit: steel saturates near $1.5\ \mathrm T$, after which its reluctance rises sharply.

Self-inductance follows from the same picture, $L = N\Phi/i = N^2/\mathcal R$. Changing the gap or moving a core changes $\mathcal R$ and therefore $L$, which is how inductive displacement sensors work.

## Related

- [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- [[Inductance]] · [[Magnetic Flux and Flux Density]] · [[Linear Variable Differential Transformer]]
- Sources: Sharkh machines notes §2; Machines 02 slides (toroid question)
