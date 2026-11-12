---
title: "Take-off Ground Run"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Takeoff Ground Roll", "Ground run", "s1", "Take-off run"]
tags: [sesa1015, concept, takeoff, ground-run]
status: complete
parent_lectures: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
related_concepts: ["[[Take-off Reference Speeds]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]"]
sources: ["Mechanics of Flight Course Notes §7.3, pp. 38–41", "Mechanics of Flight Lecture Slides v2, pp. 156–167"]
---

# Take-off Ground Run

The take-off ground run $s_1$ is the distance an aircraft rolls along the runway while accelerating from rest to its lift-off speed, taken as $V_2\approx V_{LOF}$, typically $1.2V_s$ for a jet.

Along a level runway the thrust is opposed by drag and by rolling friction on the part of the weight the wing does not yet carry, so $T-D-\mu_r(W-L)=\frac Wg\frac{dV}{dt}$. Replacing $dV/dt$ by $V\,dV/dx$ gives an equation in distance, $\frac TW-\frac DW-\mu_r\left(1-\frac LW\right)=\frac Vg\frac{dV}{dx}$. With $T/W$ constant and lift and drag neglected the left side is constant, the acceleration is $g(T/W-\mu_r)$, and integration from rest gives

$$
s_1=\frac{V_2^2}{2g\left(\frac TW-\mu_r\right)}=\frac{1.44}{\rho g}\left(\frac WS\right)\left(\frac{1}{C_{L_{max}}}\right)\frac{1}{\left(\frac TW-\mu_r\right)},
$$

the second form using $V_2=1.2V_s$ and $V_s^2=2W/(\rho SC_{L_{max}})$. A short run needs low wing loading, high $C_{L_{max}}$ (flaps and slats), high $T/W$ and dense air: since $s_1\propto1/\rho$, hot and high airfields need longer runways. A headwind $V_w$ reduces the ground speed to be reached to $V_2-V_w$, and a downhill slope adds a component of weight to the thrust; both shorten the run.

When lift and drag are kept, with $T$, $C_L$ and $C_D$ constant the net force per unit weight is $a-bV^2$ with $a=T/W-\mu_r$ and $b=\frac{\rho S}{2W}(C_D-\mu_rC_L)$, and the run is

$$
s_1=\frac{1}{2gb}\ln\left(\frac{a}{a-bV_2^2}\right),
$$

which reduces to the simple result when $bV_2^2\ll a$. For the 27-tonne twin of Slides v2 at Mexico City this gives 2822 m against 2158 m from the simple formula. Varying thrust or coefficients need a numerical integration, $x_{n+1}=x_n+G(V_n)(V_{n+1}-V_n)$ with $G=V/(gF)$.

The common traps are using sea-level density at a high airfield, forgetting to subtract $\mu_r$, and, in the full model, carrying the friction term past the speed where $L=W$, beyond which $\mu_r(1-L/W)$ turns negative and stops being physical.

## Related

- Topic: [[SESA1015 M09 - Take-off and Landing Performance]] (derivations, sea-level, Denver, Mexico City and engine-failure examples, landing run)
- Solutions: [[SESA1015 T02 - Take-off and Landing Solutions]]
- Concepts: [[Take-off Reference Speeds]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Aircraft Constraint Diagram]] (the take-off constraint $T/W=\mu_r+V_2^2/(2gs_1)$)
