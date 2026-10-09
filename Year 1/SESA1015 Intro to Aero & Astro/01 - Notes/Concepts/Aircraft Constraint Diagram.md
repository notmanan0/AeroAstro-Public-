---
title: "Aircraft Constraint Diagram"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, constraint-analysis, aircraft-design]
aliases: ["T/W versus W/S Diagram", "Constraint Map"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# Aircraft Constraint Diagram

An aircraft constraint diagram overlays performance boundaries on

$$x=\frac WS,\qquad y=\frac TW.$$

Common boundaries:

$$\text{stall: }\frac WS\le\frac12\rho V_s^2C_{L,max},$$

$$\text{level speed: }\frac TW\ge\frac{qC_{D0}}{W/S}+\frac{k(W/S)}q,$$

$$\text{climb: }\frac TW\ge\frac DW+\sin\gamma.$$

The feasible region is the intersection of the acceptable side of every constraint. Before overlaying, convert all curves to the same reference weight and thrust rating.

> [!warning] Design point
> A boundary intersection has no automatic claim to be optimal. Margin, technology, structure, stability, cost and mission closure still matter.

Recover dimensions with $S=W/(W/S)$ and $T=W(T/W)$.

