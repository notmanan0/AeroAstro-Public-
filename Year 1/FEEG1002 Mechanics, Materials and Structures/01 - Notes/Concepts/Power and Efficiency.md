---
title: "Power and Efficiency"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["power", "P = Fv", "mechanical efficiency", "horsepower", "rate of doing work", "P = M omega"]
tags: [feeg1002, concept, dynamics, energy, power]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D3 - Work, Energy and Power]]"]
related_concepts: ["[[Work-Energy Principle]]", "[[Newton's Laws of Motion]]", "[[Dependent Motion and Pulley Constraints]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 03 - Work, Energy and Power.pdf"]
---

# Power and Efficiency

Power is the rate at which a force does work, and the efficiency of a machine is the ratio of the power it delivers to the power supplied to it.

$$
P=\frac{dU}{dt}=\mathbf F\cdot\mathbf v=Fv\cos\theta,\qquad \eta=\frac{P_o}{P_i}
$$

Dividing $dU=\mathbf F\cdot d\mathbf r$ by $dt$ gives the first result, with $\theta$ the angle between the force and the velocity. Power is in watts (1 W = 1 J/s) and 1 hp = 746 W. A couple does work $M\,d\theta$, so its power is $M\omega$. Friction in any machine dissipates part of the input, which is why $\eta<1$.

Power is an instantaneous quantity: it needs only the force and the speed at the instant, and these may come from any earlier tool, usually Newton's second law. At constant tractive force the power rises in proportion to the speed, so a vehicle accelerating at a steady rate needs its greatest power at the end of the run.

For the motor hoisting a 50 kg block through a pulley, the cable constraint $s_P+2s_A=l$ gives the block's acceleration from the motor end's, Newton's law for the block on two strands gives $T=320.25$ N, and the motor's output is $P_o=Tv_P=320.25\times12=3843$ W. With $\eta=0.8$ the motor must be supplied with $P_i=4.80$ kW. The same output appears at the block, $2Tv_A=3843$ W, since the cable only transmits it. Using the speed of the block with the tension of a single strand is the trap here.

A vehicle at constant speed up a slope $\theta$ against rolling resistance $C_RN$ has no change of kinetic energy, so its power balances the weight component and the resistance: $P=mgv(\sin\theta+C_R\cos\theta)$. The climbing time depends on mass and power only through $m/P$.

![[d_t3_q10_car_power.png|620]]

## Related

- [[FEEG1002 D3 - Work, Energy and Power#4. Power and efficiency|D3 §4]] · [[FEEG1002 D3 - Work, Energy and Power#Motor hoisting a block through a pulley|motor hoist]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Work of a couple|work of a couple]]
- [[Work-Energy Principle]] · [[Newton's Laws of Motion]] · [[Dependent Motion and Pulley Constraints]]
- Year 2: thrust power and [[Propulsive Efficiency]] in [[SESA2023 Propulsion Hub|SESA2023 Propulsion]]
