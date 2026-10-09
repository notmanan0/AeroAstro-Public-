---
title: "SESA1016 T2 - Work, Heat and the First Law"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 2
tags: [sesa1016, first-law, heat, work, enthalpy]
aliases: ["Work and Heat"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T1 - Thermodynamic Systems, Properties and State]]"]
next_topics: ["[[SESA1016 T3 - Heat Engines and the Second Law]]"]
key_concepts: ["[[Boundary Work]]", "[[Internal Energy and Enthalpy]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 02 - Work and Heat Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf"]
---

# SESA1016 T2 - Work, Heat and the First Law

> [!abstract] Summary
> The first law is an accounting identity: energy cannot be created or destroyed. For the closed systems used here, heat into the gas increases its internal energy or leaves as boundary work. The central equation is $\Delta U=Q-W$, with $W=\int p\,dV$ for quasi-equilibrium piston work. The process constraint determines the path and therefore the work and heat.

## 1. Sign convention

The course convention is:

- $Q>0$: heat transferred **into** the system;
- $W>0$: work done **by** the system on the surroundings.

Ignoring macroscopic kinetic and potential energy for an equilibrium closed system:

$$
\boxed{\Delta U=Q-W}
$$

Expansion usually gives $W>0$; compression gives $W<0$.

## 2. Boundary work

A piston moves through $dx$ under gas pressure $p$. With piston area $A$, $dW=Fdx=pA\,dx=p\,dV$:

$$
\boxed{W_{1\to2}=\int_{V_1}^{V_2}p\,dV}
$$

The work is the signed area under the process path on a $p$-$V$ diagram. End states alone do not determine it.

![[tf_processes_pv.png|700]]

## 3. Ideal-gas internal energy and enthalpy

For a calorically perfect ideal gas:

$$
\Delta U=mc_v(T_2-T_1),\qquad H=U+pV,qquad \Delta H=mc_p(T_2-T_1)
$$

$$
c_p-c_v=R,\qquad \gamma=\frac{c_p}{c_v}
$$

Enthalpy appears naturally in constant-pressure heating because

$$
Q=\Delta U+W=mc_v\Delta T+p\Delta V=mc_v\Delta T+mR\Delta T=mc_p\Delta T=\Delta H.
$$

See [[Internal Energy and Enthalpy]].

## 4. Process library

### Constant volume

$$
W=0,\qquad Q=\Delta U=mc_v\Delta T
$$

All heat changes internal energy.

### Constant pressure

$$
W=p(V_2-V_1)=mR\Delta T,\qquad Q=mc_p\Delta T
$$

### Isothermal ideal gas

Because $U=U(T)$, $\Delta U=0$:

$$
W=mRT\ln\frac{V_2}{V_1}=mRT\ln\frac{p_1}{p_2},\qquad Q=W
$$

### Adiabatic

$Q=0$, but generally $\Delta T\ne0$:

$$
W=-\Delta U=mc_v(T_1-T_2)
$$

If the process is also reversible:

$$
pV^\gamma=\text{constant},\qquad TV^{\gamma-1}=\text{constant}
$$

> [!warning] Three distinctions
> - **Adiabatic** means no heat crosses the boundary; it does not mean constant temperature.
> - **Isothermal** means constant temperature; heat may be required to maintain it.
> - **Isochoric** means constant volume; pressure and temperature may change.

## 5. Multi-stage processes

Treat each leg separately:

1. identify the constraint and state relation;
2. determine the unknown end state;
3. calculate $\Delta U_i$, $W_i$ and $Q_i$;
4. sum $\Delta U=\sum\Delta U_i$, $W=\sum W_i$, $Q=\sum Q_i$.

For a complete cycle, $\Delta U_{cycle}=0$ and therefore $Q_{net}=W_{net}$.

## 6. Sanity checks

- Rigid vessel: $W=0$.
- Ideal-gas isothermal process: $\Delta U=0$.
- Adiabatic expansion: $Q=0$, $W>0$, so $T$ falls.
- At the same $\Delta T$, constant-pressure heating needs more heat than constant-volume heating because $c_p>c_v$.

## Links

- Previous: [[SESA1016 T1 - Thermodynamic Systems, Properties and State]]
- Concepts: [[Boundary Work]] · [[Internal Energy and Enthalpy]]
- Tutorial: [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]]
- Next: [[SESA1016 T3 - Heat Engines and the Second Law]]

## Sources

- `02 - Sources/Lectures/Chapter 2.pdf`, §§2.1-2.3.

