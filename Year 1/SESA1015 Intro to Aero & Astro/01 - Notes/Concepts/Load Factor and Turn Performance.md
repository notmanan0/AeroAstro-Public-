---
title: "Load Factor and Turn Performance"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Load factor", "Turning Flight Relations", "n-g Turn", "Co-ordinated turn", "Corner speed"]
tags: [sesa1015, concept, load-factor, turning-flight]
date: 2026-09-27
status: complete
parent_lectures: ["[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
related_concepts: ["[[V-n Diagram]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]"]
sources: ["Mechanics of Flight Course Notes §7.4, pp. 42–48", "Mechanics of Flight Lecture Slides v2, pp. 169–182"]
---

# Load Factor and Turn Performance

The load factor is the ratio of lift to weight, $n=L/W$. In a level co-ordinated turn at bank angle $\phi$ it is $n=1/\cos\phi$, and it fixes the turn radius $R=V^2/(g\sqrt{n^2-1})$, the turn rate $\omega=g\sqrt{n^2-1}/V$ and the stall speed in the turn, $V_S\sqrt n$.

In a banked turn the lift tilts with the wings. Its vertical component $L\cos\phi$ must still equal the weight, and its horizontal component $L\sin\phi$ provides the centripetal force $(W/g)V^2/R$. Squaring and adding gives $L=W\sqrt{1+(V^2/gR)^2}$, so the lift always exceeds the weight in a level turn, and the bank angle and load factor are the same information: 60° of bank is 2 g on any aircraft at any speed. Equivalent radius forms are $R=V^2\cot\phi/g=V^2/(g\tan\phi)$, since $\tan\phi=\sqrt{n^2-1}$, and, with $V^2=2nW/(\rho SC_L)$, $R=\frac{2}{\rho gC_L}\frac{W}{S}\frac{n}{\sqrt{n^2-1}}$. A tight, fast turn needs a high $C_L$, a low [[Wing Loading]] and a high load factor.

Since the wing reaches the same $C_{L,max}$ at $n$ times the lift, the stall speed rises to $V_{S_T}=V_S\sqrt n$: by 19 % at 45° and 41 % at 60°. Three limits bound the turn at a given speed. The stall limit allows $n=(V/V_S)^2$, giving $R_{min}=V^2/\big(g\sqrt{(V/V_S)^4-1}\big)$, infinite at $V_S$ and falling towards $V_S^2/g$ at high speed. The structural limit $n_{max}$ gives $R_{min}=V^2/(g\sqrt{n_{max}^2-1})$, rising as $V^2$. They meet at the corner speed $V^*=V_S\sqrt{n_{max}}$, where both the smallest radius and the fastest instantaneous turn rate occur.

The third limit is thrust. The induced drag in the turn is $n^2$ times its level-flight value at the same speed, so holding the turn needs the excess thrust $T_{max}-D_L=(KW^2/qS)(n^2-1)$, which gives the thrust-limited radius

$$
R_{min}=\left(\frac{2KW^2V^2}{\rho Sg^2}\right)^{1/2}\frac{1}{\sqrt{T_{max}-D_L}}.
$$

This is smallest at $V^2=4KW^2/(\rho ST_{max})$, often below the stall speed, so the best sustained turn is usually where the thrust and stall limits cross. The largest sustainable load factor is $T_{max}/D_{min}=(T/W)(L/D)_{max}$. A turn at the corner speed is usually instantaneous only: for the Slides v2 p. 176 aircraft it gives 302 m at 25.1°/s, but needs 26.9 kN of thrust against 22.25 kN available; the best sustained turn is 304 m at 120 m/s.

The common trap is to take $L=W$ in a turn, which makes the induced drag (and the thrust required) far too small: a 6 g turn has 36 times the level-flight induced drag.

## Related

- Topic: [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]] · Solutions: [[SESA1015 T06 - Turning Flight Solutions]]
- Concepts: [[V-n Diagram]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Minimum Drag and Minimum Power]] · [[Aircraft Constraint Diagram]]
- Later: [[Manoeuvre Point and Manoeuvre Margin]] (SESA2022, stability in a pull-up)
