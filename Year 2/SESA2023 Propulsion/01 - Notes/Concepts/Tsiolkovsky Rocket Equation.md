---
title: "Tsiolkovsky Rocket Equation"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["rocket equation", "ideal rocket equation", "delta-v", "mass ratio", "gravity loss", "drag loss"]
tags: [sesa2023, concept, rockets]
status: complete
parent_lectures: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Rocket Staging]]", "[[Rocket Performance Parameters]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf"]
---

# Tsiolkovsky Rocket Equation

The Tsiolkovsky rocket equation gives the ideal velocity change of a rocket from its exhaust velocity and mass ratio:

$$
\Delta V_{ideal} = c_e\ln\frac{m_0}{m_{bo}} = c_e\ln\frac{1}{\lambda+\delta},\qquad MR = \frac{m_0}{m_{bo}},\quad\lambda = \frac{m_{pl}}{m_0},\quad\delta = \frac{m_{dw}}{m_0} .
$$

The derivation, asked in 2024-25 Q2(i), takes a fully expanded nozzle, so $F = \dot mc_e$ with $\dot m = -dm/dt$ as the mass decreases. Newton's second law in free space with no drag is then $m\,dV/dt = -c_e\,dm/dt$, and separating and integrating from $m_0$ to $m_{bo}$, $\int dV = -c_e\int dm/m$, gives $\Delta V = c_e\ln(m_0/m_{bo})$. With gravity and drag included,

$$
\Delta V = c_e\ln\frac{m_0}{m_{bo}}-\int_0^tg\sin\psi\,dt-\int_0^t\frac{D}{m}dt .
$$

The gravity loss is smallest for a short burn and a low flight-path angle, and the drag loss for a slow climb through the dense lower atmosphere. The two conflict, which is why launchers fly a gravity turn. The levers are $c_e$ (propellant chemistry, chamber pressure, expansion) and the mass ratio (light structure), and the return on the mass ratio is only logarithmic. Inverted, the equation sizes a vehicle:

$$
\lambda = e^{-\Delta V/c_e}-\delta,\quad m_0 = m_{pl}/\lambda,\quad m_p = m_0(1-\lambda-\delta) .
$$

In PS10 Q10.1 ($\Delta V = 9140$ m/s, $I_{sp} = 400$ s, $\delta = 0.03$, 2 t payload) that gives $m_0 = 29.7$ t, burning 268 kg/s over 100 s; in 2024-25 Q2(ii) ($\Delta V = 5$ km/s, 450 s, $\delta = 0.08$, 2 t payload) it gives $\lambda = 0.242$, $m_0 = 8.26$ t and $m_p = 5.60$ t.

The legacy papers (2016-17, 2017-18, 2018-19) use it to show that a single stage to orbit isn't feasible. With structural efficiency $\epsilon = m_{dw}/(m_{dw}+m_p)$ and no payload, $MR = 1/\epsilon$. With $\epsilon = 0.10$ and the best $I_{sp}$ of 450 s, $\Delta V_{ideal} = 4414\ln10 = 10{,}165$ m/s, which after 40 % losses leaves 6099 m/s, short of the 7788 m/s circular speed at 200 km. Reaching orbit would need $MR = 18.9$, or $\epsilon = 5.3\%$, which is structurally impractical; hence staging. The Year 1 version, discrete momentum exchange by throwing bricks off a wagon, is in [[FEEG1002 D4 - Linear Impulse and Momentum]].

## Related

- [[Rocket Staging]] · [[Rocket Performance Parameters]]
