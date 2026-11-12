---
title: "Method of Joints and Method of Sections"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["method of joints", "method of sections", "truss analysis", "zero-force member"]
tags: [feeg1002, concept, statics, trusses]
status: complete
parent_lectures: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Static Determinacy]]", "[[Williot Displacement Diagram]]"]
sources: ["Statics 1 Lectures 3-4"]
---

# Method of Joints and Method of Sections

The method of joints and the method of sections are the two ways of finding the bar forces in a statically determinate pin-jointed truss. The **method of joints** isolates one pin at a time and applies $\sum F_x=\sum F_y=0$; the **method of sections** cuts the truss into two parts through at most three bars and applies all three equilibrium equations to one part.

Both rely on the bars being two-force members: with frictionless pins and loads applied only at the joints, each bar carries a single force along its own axis. Every cut bar force is drawn pointing away from the joint or the cut, which is the tension-positive convention, so a negative answer means compression without any change of drawing.

At a joint only two equations are available, so the method of joints starts at a joint with no more than two unknown bars and works through the truss from there. It suits small trusses, or cases where every bar force is wanted. The method of sections goes straight to a bar in the middle of a long truss. With three cut bars, taking moments about the point where two of them meet leaves an equation with only the third, so each force comes out of one equation.

Some bars carry no force under a given loading. At an unloaded joint with only two bars that are not in line, both are zero; at an unloaded joint with three bars, two of them in line, the third is zero. Such bars are still needed: they stabilise the truss and carry load when the loading changes. A quick physical check on any answer is to imagine removing the bar. If its two joints would then move apart, the bar was in tension; if they would move together, it was in compression.

![[s1_truss_method_of_sections.png|760]]

## Related

- Topic notes: [[FEEG1002 A2 - Pin-Jointed Trusses#3. The method of joints|A2, method of joints]] · [[FEEG1002 A2 - Pin-Jointed Trusses#4. The method of sections|A2, method of sections]] · [[FEEG1002 A2 - Pin-Jointed Trusses#Zero-force members|A2, zero-force members]] · [[FEEG1002 A2 - Pin-Jointed Trusses#5. Choosing a method|A2, choosing a method]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Static Determinacy]] · [[Williot Displacement Diagram]]
- Year 2: truss deflection by the [[Unit Load Method]] and redundant bars by [[Castigliano Second Theorem]] in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] · the stiffness method in [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]
