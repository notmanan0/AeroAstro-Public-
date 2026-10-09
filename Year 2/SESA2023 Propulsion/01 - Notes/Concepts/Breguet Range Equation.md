---
title: "Breguet Range Equation"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["range equation", "Breguet"]
tags: [sesa2023, concept, range]
status: complete
parent_lectures: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]"]
related_concepts: ["[[Thrust Specific Fuel Consumption]]", "[[Thermal and Overall Efficiency]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf"]
---
# Breguet Range Equation

## Definition

> [!note] Definition
>
> $$s = \frac{L}{D}\frac{V_0}{g_0\,\text{TSFC}}\ln\frac{W_1}{W_2} = \eta_O\frac{LCV}{g_0}\frac{L}{D}\ln\frac{W_1}{W_2}\qquad(W_1\text{ initial},\ W_2\text{ final})$$

## Explanation
**Derivation** (asked in 2014-15 Q1(iii) for 12 marks, and in 2016-17 Q3(ii) for 10 marks):
1. Assume steady level cruise: $L = W$ and $F = D$, so $W = F\,L/D$.
2. Fuel burn: $dW/dt = -\dot m_fg_0 = -g_0\,\text{TSFC}\,F = -g_0\,\text{TSFC}\,W/(L/D)$.
3. Convert time to distance with $ds = V_0\,dt$: $dW/W = -\dfrac{g_0\,\text{TSFC}}{V_0\,L/D}ds$.
4. Integrate at constant $V_0$, $L/D$ and TSFC: $\ln(W_2/W_1) = -\dfrac{g_0\,\text{TSFC}}{V_0\,L/D}s$.
5. Substitute $\text{TSFC} = V_0/(\eta_OLCV)$ to get the second form. Range is proportional to 1/TSFC.

**Assumptions to state**:
- steady, level flight;
- constant $V$, $L/D$ and TSFC (cruise-climb in practice);
- climb, descent and reserves ignored;
- $g$ constant.

**Three levers**:
- engine: $\eta_O\,LCV$;
- aerodynamics: $L/D$;
- structures and fuel fraction: $W_1/W_2$.

**Fuel choice** (2023-24 Q3(iv)): hydrogen has 2.8× the LCV of kerosene (120 vs 43 MJ/kg), so for the same fuel *mass* fraction the range is much larger. But LH₂ is about 4× bulkier per unit energy and needs heavy cryogenic tanks, which reduces $L/D$ and the fuel fraction.

## Examples
- Boeing 777-200: $L/D = 20$, 248 m/s, $1.614\times10^{-5}$, 243 t → 201 t, giving **5944 km** (published 6112 km).
- PS1 Q1.3b: $L/D = 10$ and 4202 km give $W_1/W_2 = 1.420$, so the dry mass is **238 t**.
- 2023-24 Q3(v): $\eta_O = 0.39$, LCV 120 MJ/kg, $L/D = 21$, 100 t → 92 t, giving **8353 km**.

## Related
- [[Thrust Specific Fuel Consumption]] · [[Thermal and Overall Efficiency]]

## Sources
- Week 1 notes §1.3; Data Book p. 16
