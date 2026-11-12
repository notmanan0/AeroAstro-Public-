---
title: "Standard Beam Deflections"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["beam deflection table", "FL^3/3EI", "5wL^4/384EI", "standard cases"]
tags: [feeg1002, concept, statics, beams, deflection]
status: complete
parent_lectures: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]", "[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
related_concepts: ["[[Macaulay's Method]]", "[[Superposition for Indeterminate Beams]]", "[[Elastic Curve]]"]
sources: ["Statics 1 Lectures 9-11"]
---

# Standard Beam Deflections

The standard beam deflections are the closed-form results for the simplest loadings of cantilevers and simply supported beams, each found once by double integration of $EI\,d^2v/dx^2=-M$ and then reused, alone or added together, instead of integrating again.

| Case | Maximum deflection | Maximum slope | Maximum moment |
|---|---|---|---|
| Cantilever, end load $F$ | $FL^3/3EI$ at the tip | $FL^2/2EI$ at the tip | $FL$ at the root |
| Cantilever, UDL $w$ | $wL^4/8EI$ at the tip | $wL^3/6EI$ at the tip | $wL^2/2$ at the root |
| Simply supported, central $F$ | $FL^3/48EI$ at midspan | $FL^2/16EI$ at the ends | $FL/4$ at midspan |
| Simply supported, UDL $w$ | $5wL^4/384EI$ at midspan | $wL^3/24EI$ at the ends | $wL^2/8$ at midspan |

All four assume a linear elastic beam of uniform $EI$ with small deflections and slopes, and $v$ positive downwards.

The powers of $L$ are worth reading. A point load gives a deflection proportional to $L^3$ and a distributed load (whose total grows with $L$) to $L^4$, so doubling a span multiplies the deflection by 8 or 16, while the stress only goes up by 2 or 4. Long beams tend to be designed for stiffness rather than strength.

Because the governing equation is linear, deflections from separate loads add. A beam with an end load and a uniform load has a tip deflection equal to the sum of the two table entries, and the same idea, with an unknown reaction treated as one of the loads, solves indeterminate beams. Beyond the last load a cantilever carries no moment and stays straight, so its tip deflection is the deflection at the load plus the slope there times the remaining length.

![[s1_standard_beam_cases.png|860]]

## Related

- Topic notes: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Standard results|A5, standard results]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#2. Simply supported beam with a uniform load|A5, uniform load]] · [[FEEG1002 A6 - Statically Indeterminate Beams#3. The superposition method|A6, cantilever cases and superposition]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]
- Concepts: [[Macaulay's Method]] · [[Superposition for Indeterminate Beams]] · [[Elastic Curve]]
- Year 2: deflection limits in [[SESA2028 S2 - Beam Deflection and Bending Design]] · the same results from the [[Unit Load Method]]
