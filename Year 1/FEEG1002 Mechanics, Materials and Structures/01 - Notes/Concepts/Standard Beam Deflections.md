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
sources: []
---

# Standard Beam Deflections

## Definition

> [!note] Definition
> | Case | $v_{max}$ | $\theta_{max}$ | $M_{max}$ |
> |---|---|---|---|
> | Cantilever, end load $F$ | $FL^3/3EI$ | $FL^2/2EI$ | $FL$ |
> | Cantilever, UDL $w$ | $wL^4/8EI$ | $wL^3/6EI$ | $wL^2/2$ |
> | Simply supported, central $F$ | $FL^3/48EI$ | $FL^2/16EI$ | $FL/4$ |
> | Simply supported, UDL | $5wL^4/384EI$ | $wL^3/24EI$ | $wL^2/8$ |
> | Propped cantilever, UDL | $wL^4/185EI$ | – | $wL^2/8$ (wall) |
> | Fixed–fixed, UDL | $wL^4/384EI$ | 0 | $wL^2/12$ (ends) |

## Explanation

- Deflection scales as $L^3$ (point load) or $L^4$ (UDL). Doubling a span multiplies the deflection by 8–16.
- **Superposition**: for linear elastic beams, add the deflections of standard cases. This is the fast route for indeterminate beams ([[Superposition for Indeterminate Beams]]).
- **Slope trick**: past the last load, a cantilever is straight, so $v_{tip} = v(a) + \theta(a)(L-a)$.

## Examples

![[s1_standard_beam_cases.png|860]]

## Related

- Topic notes: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Concepts: [[Macaulay's Method]] · [[Superposition for Indeterminate Beams]] · [[Elastic Curve]]
- Year 2: Deflection limits in [[SESA2028 S2 - Beam Deflection and Bending Design]] · the same numbers from the [[Unit Load Method]]

## Sources

- Statics 1 Lectures 9b–c, 11c
