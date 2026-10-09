---
title: "SESA1016 T5 - Ideal Heat Engine Models"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 5
tags: [sesa1016, carnot, otto, diesel, brayton]
aliases: ["Heat Engine Models", "Ideal Cycles"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
next_topics: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
key_concepts: ["[[Thermal Efficiency and COP]]", "[[Isentropic Ideal-gas Relations]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5.pdf"]
---

# SESA1016 T5 - Ideal Heat Engine Models

> [!abstract] Summary
> Carnot supplies the reversible upper limit. Otto, Diesel and Brayton replace real combustion and machinery with idealised heat-transfer and isentropic processes. The reliable solution method is always the same: label states, write the constraint for each leg, complete the state table, compute heat and work process by process, then close the cycle.

![[tf_ideal_cycles_pv.png|720]]

## 1. Universal cycle workflow

1. Draw the cycle and fix state numbering.
2. Write the process constraint on every leg.
3. Fill a table of $p,T,v$ before calculating heat or work.
4. Use $q=c_v\Delta T$ for constant-volume heat and $q=c_p\Delta T$ for constant-pressure heat.
5. Use isentropic ratios for reversible adiabatic compression/expansion.
6. Calculate $\eta=1-q_{out}/q_{in}$ and check $0<\eta<\eta_C$.

## 2. Carnot cycle

Two reversible isotherms and two reversible adiabatics operate between $T_H$ and $T_C$:

$$
\boxed{\eta_C=1-\frac{T_C}{T_H}}
$$

No engine between the same reservoirs can be more efficient. Carnot efficiency depends only on reservoir temperatures, not working fluid.

## 3. Otto cycle

Ideal spark-ignition sequence:

1. 1-2 isentropic compression;
2. 2-3 constant-volume heat addition;
3. 3-4 isentropic expansion;
4. 4-1 constant-volume heat rejection.

With compression ratio $r=v_1/v_2$:

$$
\boxed{\eta_{Otto}=1-\frac1{r^{\gamma-1}}}
$$

Higher $r$ improves ideal efficiency but real engines are limited by knock, heat loss, stress and emissions.

## 4. Diesel cycle

Ideal compression-ignition sequence replaces Otto's constant-volume heat addition with constant-pressure heat addition. Define cut-off ratio $r_c=v_3/v_2$:

$$
\boxed{\eta_{Diesel}=1-\frac1{r^{\gamma-1}}
\frac{r_c^\gamma-1}{\gamma(r_c-1)}}
$$

At the same compression ratio and heat input, the Otto idealisation is more efficient; real diesel engines commonly use much larger compression ratios.

## 5. Brayton cycle

Ideal gas-turbine sequence:

1. 1-2 isentropic compressor;
2. 2-3 constant-pressure heat addition;
3. 3-4 isentropic turbine;
4. 4-1 constant-pressure heat rejection.

With pressure ratio $r_p=p_2/p_1$:

$$
\boxed{\eta_{Brayton}=1-\frac1{r_p^{(\gamma-1)/\gamma}}}
$$

Compressor work is not a small correction: a substantial fraction of turbine work drives the compressor. Net work is $w_t-w_c$.

![[tf_cycle_efficiency.png|720]]

## 6. Dual cycle

The dual cycle splits heat addition into constant-volume and constant-pressure legs. It is a better idealisation of real combustion and is handled with the same state-table method; no new thermodynamic law is required.

## 7. Comparing cycles responsibly

An efficiency comparison is meaningful only after stating what is held fixed: compression ratio, maximum pressure, maximum temperature, heat input or net work. Different constraints can reverse a ranking.

> [!tip] Quick checks
> - Heat-addition legs must raise temperature.
> - Isentropic compression raises both $p$ and $T$.
> - Isentropic expansion lowers both.
> - Net cycle work equals net heat.

## Links

- Previous: [[SESA1016 T4 - Entropy and Isentropic Relations]]
- Tutorial: [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]
- Formulae: [[SESA1016 Formula Sheet#4. Ideal cycles]]
- Continues in Propulsion: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · [[Brayton Cycle]]
- Next: [[SESA1016 T6 - Dimensional Analysis and Similarity]]

## Sources

- `02 - Sources/Lectures/Chapter 5.pdf`, §§5.1-5.4.
