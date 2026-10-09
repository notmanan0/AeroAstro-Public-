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

## Definition

> [!note] Definition
>
> $$\Delta V_{ideal} = c_e\ln\frac{m_0}{m_{bo}} = c_e\ln\frac{1}{\lambda+\delta},\qquad MR = \frac{m_0}{m_{bo}},\quad\lambda = \frac{m_{pl}}{m_0},\quad\delta = \frac{m_{dw}}{m_0}$$

## Explanation
**Derivation** (2024-25 Q2(i)):
1. Take a fully expanded nozzle, so $F = \dot mc_e$ with $\dot m = -dm/dt$ (mass decreases).
2. Newton's second law in free space with no drag: $m\,dV/dt = -c_e\,dm/dt$.
3. Separate and integrate from $m_0$ to $m_{bo}$: $\int dV = -c_e\int dm/m$, giving $\Delta V = c_e\ln(m_0/m_{bo})$.

**With losses**:

$$\Delta V = c_e\ln\frac{m_0}{m_{bo}}-\int_0^tg\sin\psi\,dt-\int_0^t\frac{D}{m}dt$$

- Gravity loss is minimised by a short burn and a low flight-path angle.
- Drag loss is minimised by a slow climb through dense air. These conflict, so a **gravity turn** is used.

**Levers**: raise $c_e$ (propellant chemistry, $P_c$, expansion) and the mass ratio (light structure). Returns are only logarithmic in the mass ratio.

**Inverted**:

$$\lambda = e^{-\Delta V/c_e}-\delta,\quad m_0 = m_{pl}/\lambda,\quad m_p = m_0(1-\lambda-\delta)$$

**SSTO feasibility** (legacy 2016-17, 2017-18, 2018-19):
- With structural efficiency $\epsilon = m_{dw}/(m_{dw}+m_p)$ and zero payload, $MR = 1/\epsilon$.
- With $\epsilon = 0.10$ and the best $I_{sp} = 450$ s: $\Delta V_{ideal} = 4414\ln10 = 10{,}165$ m/s. After 40 % losses that leaves 6099 m/s, **below the 7788 m/s** circular speed at 200 km.
- The required MR would be 18.9 ($\epsilon$ = 5.3 %), which is structurally impractical. Hence **staging**.

## Examples
- PS10 Q10.1: $\Delta V = 9140$ m/s, $I_{sp} = 400$ s, $\delta = 0.03$, 2 t payload: $m_0 = 29.7$ t, 268 kg/s over 100 s.
- 2024-25 Q2(ii): $\Delta V = 5$ km/s, 450 s, $\delta = 0.08$, 2 t payload: $\lambda = 0.242$, $m_0 = 8.26$ t, $m_p = 5.60$ t.

## Related
- [[Rocket Staging]] · [[Rocket Performance Parameters]]

## Year 1 foundation
- Discrete momentum exchange (throwing bricks off a wagon): [[FEEG1002 D4 - Linear Impulse and Momentum]].

## Sources
- Week 10 notes §10.3.2; Lecture 29; Data Book p. 17
