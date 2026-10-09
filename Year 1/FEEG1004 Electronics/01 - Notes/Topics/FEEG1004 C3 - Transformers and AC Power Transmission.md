---
title: "FEEG1004 C3 - Transformers and AC Power Transmission"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 3
tags: [feeg1004, machines, transformer, turns-ratio, emf-equation, transmission, ac-vs-dc]
aliases: ["Electric Machines 04", "Transformer", "4.44 f N Phi", "AC vs DC"]
date: 2026-09-27
status: complete
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
next_topics: ["[[FEEG1004 C4 - DC Generators and the Commutator]]"]
key_concepts: ["[[Ideal Transformer]]", "[[Transformer EMF Equation]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 04 - Transformers and AC Power - Lecture Slides.pdf"]
---

# FEEG1004 C3 - Transformers and AC Power Transmission

> [!abstract] Summary
> A transformer is two windings on a laminated steel core. The same alternating flux links both.
> - Faraday: $v_1/v_2 = N_1/N_2$. For an ideal (lossless) transformer $v_1i_1 = v_2i_2$, so $i_2/i_1 = N_1/N_2$.
> - For a sinusoid, $V_{rms} = 4.44fN\Phi_m$ fixes the core flux (keep $B_m\lesssim1.5$ T).
> - This is **why power is AC**: raising the voltage cuts the current, so the $I^2R$ loss falls as $1/V^2$.

## Key Concepts
- [[Ideal Transformer]] · [[Transformer EMF Equation]]

---

## 1. Why AC? (Sharkh §3.4)
- AC is natural to rotating machines.
- It is easy to switch off: the current passes through zero twice per cycle, so arcs self-extinguish.
- It **transforms** efficiently. Since $p = vi$, a higher $v$ carries the same power at lower $i$, giving smaller cables and lower $I^2R$ loss.
- In the UK: generation → **400 kV** transmission → substations → 400 V three-phase industrial / 230 V single-phase domestic.
- DC sources (batteries, fuel cells, PV, thermocouples) need **converters** to interface with AC.

![[ee_c3_transformer_transmission.png|900]]

The left panel moves 100 MW through a 1 Ω line: 82.6 MW would be lost at 11 kV but only 62.5 kW at 400 kV.

## 2. The transformer (§3.5)
- The **primary** connects to the source; the **secondary** to the load.
- The laminated core (limbs and yokes) carries nearly all the flux. It is the low-reluctance path ([[Magnetomotive Force and Reluctance]]).
- Faraday on each winding, neglecting resistance and leakage flux:

$$
v_1 = N_1\frac{d\Phi}{dt},\quad v_2 = N_2\frac{d\Phi}{dt}\ \Rightarrow\ \frac{v_1}{v_2} = \frac{N_1}{N_2}
$$

- Power: $\eta = p_2/p_1$, approaching 99 % in large units. Ideal: $p_1 = p_2$, so $\dfrac{i_2}{i_1} = \dfrac{N_1}{N_2}$. Stepping voltage **up** steps current **down**.
- In rms terms: $V_2/V_1 = N_2/N_1$ and $I_2/I_1 = N_1/N_2$.

## 3. The EMF equation
- A sinusoidal flux $\Phi = \Phi_m\sin2\pi ft$ gives $e = 2\pi fN\Phi_m\cos2\pi ft$. Hence

$$
E_{rms} = \frac{2\pi}{\sqrt2}fN\Phi_m = 4.44\,fN\Phi_m
$$

- Given the supply voltage, this fixes the **peak flux**. The core area then sets $B_m = \Phi_m/A$, which must stay below about 1.5 T to avoid saturation.
- This is why a transformer designed for 60 Hz overheats on 50 Hz, and why 400 Hz aircraft transformers are small.

> [!example] Lecture: 400/1000 turns, 60 cm² core, 500 V at 50 Hz
> - $V_2 = 500\times1000/400$ = **1250 V**.
> - $\Phi_m = 500/(4.44\times50\times400)$ = **5.63 mWb**, so $B_m = 0.00563/0.006$ = **0.94 T**, comfortably below 1.5 T.

> [!example] Tutorial 5 Q5: 70/350 turns, 100 cm², 230 V at 50 Hz
> - $B_m = 230/(4.44\times50\times70\times0.01)$ = **1.48 T**, right at the practical limit.
> - $V_2 = 230\times5$ = **1150 V**.
> - A 10 kW resistive load draws $I_2$ = 8.70 A, so $I_1 = 10\,000/230$ = **43.5 A**.

## Year 2 bridge
- **Aircraft** use transformer-rectifier units (TRUs) to derive 28 V DC from the 115 V, 400 Hz AC bus ([[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]).
- **Spacecraft** use DC buses and DC–DC converters. Inside, these are high-frequency transformers, where the $4.44fN\Phi$ scaling makes them tiny ([[SESA2024 08 - Electrical Power Subsystem]]).
- The **LVDT** is a transformer with a movable core ([[Linear Variable Differential Transformer]]).
- Reactive power drawn to magnetise transformer cores is part of the power-factor story ([[FEEG1004 D4 - AC Power and Power Factor]]).

## Links
- Previous: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · Next: [[FEEG1004 C4 - DC Generators and the Commutator]]
- Worked problems: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q5)

## Sources
- Sharkh/Niu machines notes §3.4–3.5; Electric Machines 04 slides; Hughes Ch. 32, 37.
