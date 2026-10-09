---
title: "SESA1015 M07 - Propeller Aircraft Range and Endurance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 7
tags: [sesa1015, propeller, range, endurance]
aliases: ["SESA1015 Mechanics 7", "Propeller Range and Endurance"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M06 - Jet Aircraft Range and Endurance]]"]
next_topics: ["[[SESA1015 M08 - Glide and Climb Performance]]"]
key_concepts: ["[[Breguet Range Equation]]", "[[Minimum Drag and Minimum Power]]"]
tutorial_sheets: ["[[SESA1015 T04 - Range and Endurance Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M07 - Propeller Aircraft Range and Endurance

> [!abstract] Summary
> A propeller engine supplies shaft power, of which the propeller converts a fraction $\eta_p$ into useful propulsive power $TV$. Because fuel flow is tied to shaft power rather than thrust, propeller endurance favours minimum aerodynamic power, whereas propeller range favours maximum $L/D$. The coefficient optimum therefore swaps relative to the jet case.

## 1. Power chain

$$P_{propulsive}=TV=\eta_pP_{shaft}.$$

In steady level flight $T=D$, so

$$P_{shaft}=\frac{DV}{\eta_p}.$$

If brake-specific fuel consumption relates fuel flow to shaft power, then fuel burn is proportional to $DV/\eta_p$.

## 2. Range

Distance per unit fuel is favoured by large

$$\frac{V}{P_{shaft}}=\frac{\eta_p}{D}=\frac{\eta_p}{W}\frac LD.$$

With constant $\eta_p$ and specific fuel consumption, integration gives the structural form

$$\boxed{R_p\propto\frac{\eta_p}{c_P}\frac LD\ln\frac{W_i}{W_f}}.$$

Thus the ideal aerodynamic condition for maximum propeller range is maximum $L/D$:

$$C_{L,R_p}=\sqrt{\frac{C_{D0}}k}.$$

## 3. Endurance

Time per unit fuel is favoured by minimum shaft power, hence minimum propulsive power if $\eta_p$ is constant. Aerodynamically,

$$P_R=DV\propto\frac{C_D}{C_L^{3/2}}W^{3/2}.$$

Therefore maximise

$$\frac{C_L^{3/2}}{C_D}$$

and obtain

$$\boxed{C_{L,E_p}=\sqrt{\frac{3C_{D0}}k}}.$$

This is the minimum-power condition.

## 4. Jet–propeller comparison

| Vehicle model | Maximum range | Maximum endurance |
|---|---|---|
| Jet | max $\sqrt{C_L}/C_D$ at constant altitude | max $C_L/C_D$ |
| Propeller | max $C_L/C_D$ | max $C_L^{3/2}/C_D$ |

The reason is not arbitrary: jet fuel flow is linked to thrust; propeller fuel flow is linked to power.

## 5. Efficiency is not constant in reality

Propeller efficiency changes with advance ratio, blade pitch, tip Mach and installation. Piston or turboprop fuel consumption also varies with power setting and altitude. A real optimum therefore maximises an entire propulsion–airframe combination, not an aerodynamic ratio alone.

> [!warning] SFC conventions
> Texts use mass or weight fuel flow and may express BSFC per watt, kilowatt or horsepower. Derive the units from the definition given rather than copying a prefactor from memory.

## 6. Worked optimum-speed relation

If a propeller aircraft has $V_{MD}=60\ \mathrm{m,s^{-1}}$, then the ideal maximum-endurance speed is

$$V_{MP}=3^{-1/4}V_{MD}=0.760(60)=45.6\ \mathrm{m,s^{-1}}.$$

Maximum-range speed remains $60\ \mathrm{m,s^{-1}}$ in this simple model. Both scale downward as weight is burned:

$$V^*\propto\sqrt W.$$

## 7. Operational interpretation

- Loiter tasks emphasise endurance.
- Ferry tasks emphasise range.
- Headwind raises the airspeed for maximum ground range; tailwind lowers it.
- Reserve requirements mean the final mass is not empty mass.
- A speed below stall or outside efficient propeller operation is not usable even if an ideal coefficient calculation suggests it.

## Year 2 bridge

- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] derives propulsive efficiency and connects it to engine and propeller operation.
- [[Breguet Range Equation]] provides a common comparison of jet and propeller forms.

