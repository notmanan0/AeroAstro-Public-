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

The Breguet range equation gives the cruise range of an aircraft from its aerodynamics, its engine and the fraction of its weight that is fuel:

$$
s = \frac{L}{D}\frac{V_0}{g_0\,\text{TSFC}}\ln\frac{W_1}{W_2} = \eta_O\frac{LCV}{g_0}\frac{L}{D}\ln\frac{W_1}{W_2}\qquad(W_1\text{ initial},\ W_2\text{ final}).
$$

The derivation has been asked for 12 marks (2014-15 Q1(iii)) and 10 marks (2016-17 Q3(ii)):

1. In steady level cruise $L = W$ and $F = D$, so $W = F\,L/D$.
2. Fuel burn: $dW/dt = -\dot m_fg_0 = -g_0\,\text{TSFC}\,F = -g_0\,\text{TSFC}\,W/(L/D)$.
3. Convert time to distance with $ds = V_0\,dt$: $dW/W = -\dfrac{g_0\,\text{TSFC}}{V_0\,L/D}ds$.
4. Integrate at constant $V_0$, $L/D$ and TSFC: $\ln(W_2/W_1) = -\dfrac{g_0\,\text{TSFC}}{V_0\,L/D}s$.
5. Substitute $\text{TSFC} = V_0/(\eta_OLCV)$ for the second form.

The assumptions to state are steady level flight, constant $V$, $L/D$ and TSFC (a cruise-climb in practice), constant $g$, and no allowance for climb, descent or reserves. The equation separates the three levers on range: the engine through $\eta_O\,LCV$, the aerodynamics through $L/D$, and the structure and fuel fraction through $W_1/W_2$.

Fuel choice enters through the LCV (2023-24 Q3(iv)). Hydrogen has 2.8 times the LCV of kerosene (120 against 43 MJ/kg), so for the same fuel mass fraction the range is much larger, but liquid hydrogen is about four times bulkier per unit energy and needs heavy cryogenic tanks, which cut both $L/D$ and the fuel fraction.

Worked values: a Boeing 777-200 with $L/D = 20$, 248 m/s and TSFC $1.614\times10^{-5}$, going from 243 t to 201 t, gives 5944 km (published 6112 km). In PS1 Q1.3b, $L/D = 10$ and 4202 km give $W_1/W_2 = 1.420$, a dry mass of 238 t. In 2023-24 Q3(v), $\eta_O = 0.39$, LCV 120 MJ/kg, $L/D = 21$ and 100 t to 92 t give 8353 km.

## Related

- [[Thrust Specific Fuel Consumption]] · [[Thermal and Overall Efficiency]]
