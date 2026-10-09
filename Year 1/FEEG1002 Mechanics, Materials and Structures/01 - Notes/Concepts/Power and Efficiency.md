---
title: "Power and Efficiency"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["power", "P = Fv", "mechanical efficiency", "horsepower"]
tags: [feeg1002, concept, dynamics, energy, power]
status: complete
parent_lectures: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
related_concepts: ["[[Work-Energy Principle]]", "[[Newton's Laws of Motion]]"]
sources: []
---

# Power and Efficiency

## Definition

> [!note] Definition
>
> $$P = \frac{dU}{dt} = \mathbf F\cdot\mathbf v = Fv\cos\theta\ \ [\text{W}],\qquad P = M\omega\ \text{for a couple},\qquad \eta = \frac{P_{out}}{P_{in}} < 1$$

## Explanation

- Power is **instantaneous**. For a constant force it rises with speed, so an accelerating vehicle needs its peak power at the end of the run.
- 1 hp = 746 W.
- Friction in any machine dissipates energy, so $\eta < 1$ and the input power must exceed the output.
- For hoists, find the cable tension from $\sum F = ma$ **first**, then $P = Tv_{cable}$.

## Examples

- **Motor hoist** (Lecture 3): $T = 320$ N and $P_o = 3844$ W, so $P_i = 4.8$ kW at $\eta = 0.8$.
- **Tutorial 3 Q10**: 19.07 kW while accelerating, 6.54 kW cruising.

![[d_t3_q10_car_power.png|620]]

## Related

- Topic notes: [[FEEG1002 D3 - Work, Energy and Power]]
- Concepts: [[Work-Energy Principle]] · [[Newton's Laws of Motion]]
- Year 2: Thrust power and propulsive efficiency, [[SESA2023 Propulsion Hub]] · shaft power $P = T\omega$, [[FEEG1002 A8 - Torsion of Circular Shafts]]

## Sources

- Dynamics Lecture 3.3
