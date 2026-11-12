---
title: "Current Divider"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["current divider rule"]
tags: [feeg1004, concept, dc-circuits, ac-circuits]
status: complete
parent_lectures: ["[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]", "[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Potential Divider]]", "[[Series and Parallel Resistors]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf"]
---

# Current Divider

The current divider rule gives how a current $I$ splits between two parallel branches. Each branch takes a share proportional to the other branch's resistance:

$$
I_1=I\frac{R_2}{R_1+R_2},\qquad I_2=I\frac{R_1}{R_1+R_2}.
$$

It follows from the shared voltage. Both branches carry the same voltage $V=I(R_1\parallel R_2)=IR_1R_2/(R_1+R_2)$, and dividing by $R_1$ gives $I_1$. The resistance in the numerator is therefore the other branch's, and more current takes the lower-resistance path. In AC the rule holds with impedances $Z$ in place of $R$.

In the W6 superposition example, $I_2=4\times13.33/(13.33+20)=1.6\ \mathrm A$. Tutorial 7 Q5 applies the rule twice with complex impedances, giving $I_1=20\angle45^\circ\times2/(2+4.24\angle28.2^\circ)=6.59\angle25.7^\circ\ \mathrm A$.

## Related

- [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]] · [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- [[Potential Divider]] · [[Complex Impedance]]
- Sources: Week 6 interactive session; Tutorial Sheet 7
