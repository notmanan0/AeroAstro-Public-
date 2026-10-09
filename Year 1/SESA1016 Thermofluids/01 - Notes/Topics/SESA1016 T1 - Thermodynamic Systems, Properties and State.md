---
title: "SESA1016 T1 - Thermodynamic Systems, Properties and State"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 1
tags: [sesa1016, thermodynamics, ideal-gas, state]
aliases: ["Thermodynamic Systems and State"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: []
next_topics: ["[[SESA1016 T2 - Work, Heat and the First Law]]"]
key_concepts: ["[[Closed System vs Control Volume]]", "[[Thermodynamic State and Process]]", "[[Ideal-gas Law]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 1.pdf"]
---

# SESA1016 T1 - Thermodynamic Systems, Properties and State

> [!abstract] Summary
> Thermodynamics begins by drawing a boundary. A **closed system** contains a fixed mass; a **control volume** occupies a chosen region through which mass may flow. Properties define the system's state. At equilibrium a small set of independent intensive properties fixes every other property; for a low-density gas the closure relation is usually the **ideal-gas law** $pV=mRT$.

## 1. Choosing the object of study

| Model | Boundary | Mass crossing? | Typical example |
|---|---|---:|---|
| Closed system | may move or deform | No | gas under a piston |
| Control volume | usually fixed in space | Yes | nozzle, turbine, pipe junction |
| Isolated system | closed and energy-tight | No | ideal insulated rigid vessel |

The choice is not cosmetic. For a closed system, energy crosses as heat or work. For a control volume, flowing mass also carries enthalpy, kinetic and potential energy.

See [[Closed System vs Control Volume]].

## 2. Properties

A **property** depends only on state, not on how the state was reached.

- **Intensive**: independent of system size: $p,T,\rho$.
- **Extensive**: scales with mass: $m,V,U,S$.
- **Specific**: extensive property per unit mass: $v=V/m$, $u=U/m$, $s=S/m$.

The split-in-half test is useful: cutting a uniform system into two equal parts leaves $p$ and $T$ unchanged but halves $V$, $m$ and $U$.

## 3. Continuum assumption

Real fluids are molecular, but engineering thermofluids treats $p(\mathbf x)$, $T(\mathbf x)$ and $\rho(\mathbf x)$ as smooth fields. This is valid when the characteristic length is much larger than the molecular mean free path. It fails in sufficiently rarefied gases and microscale devices.

## 4. State and equilibrium

A system is in thermodynamic equilibrium when there is no unbalanced tendency to change:

- thermal equilibrium: no temperature gradient driving heat transfer;
- mechanical equilibrium: no unbalanced pressure force;
- phase/chemical equilibrium where relevant.

A **process** moves between equilibrium states. A **quasi-equilibrium** process is slow enough that the system passes through a sequence of almost-equilibrium states, so a single pressure can be used in $W=\int p\,dV$.

> [!warning] State function versus path function
> $p,V,T,U,H,S$ are properties. Heat $Q$ and work $W$ are transfers during a process, so they are not “contained” in a system and depend on the path.

## 5. Ideal-gas law

$$
\boxed{pV=mRT}\qquad\Longleftrightarrow\qquad pv=RT\qquad\Longleftrightarrow\qquad p=\rho RT
$$

For air, $R\approx287\ \mathrm{J\,kg^{-1}K^{-1}}$. Use **absolute pressure** and **absolute temperature**.

Between two equilibrium states of the same fixed mass:

$$
\frac{p_1V_1}{T_1}=\frac{p_2V_2}{T_2}
$$

This ratio form eliminates $mR$, but it does not remove the requirement for kelvin and absolute pressure.

### Moving piston equilibrium

For a piston of area $A$ carrying load $F_L$ and exposed to atmosphere above:

$$
p_{gas}A=p_{atm}A+F_L\quad\Rightarrow\quad p_{gas}=p_{atm}+\frac{F_L}{A}
$$

Heating a freely moving piston at constant load therefore produces an approximately **constant-pressure** process. A stop changes the model: after contact the volume is fixed and subsequent heating raises pressure.

## 6. Worked micro-example

A rigid $0.50\ \mathrm{m^3}$ vessel contains $0.60\ \mathrm{kg}$ of air at $20^\circ\mathrm C$.

$$
p=\frac{mRT}{V}=\frac{0.60(287)(293.15)}{0.50}=1.01\times10^5\ \mathrm{Pa}
$$

The result is close to one atmosphere, a useful scale check.

## Links

- Parent: [[SESA1016 Thermofluids Hub]]
- Concepts: [[Closed System vs Control Volume]] · [[Thermodynamic State and Process]] · [[Ideal-gas Law]]
- Tutorial: [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]]
- Next: [[SESA1016 T2 - Work, Heat and the First Law]]

## Sources

- `02 - Sources/Lectures/Chapter 1.pdf`, §§1.1-1.6.

