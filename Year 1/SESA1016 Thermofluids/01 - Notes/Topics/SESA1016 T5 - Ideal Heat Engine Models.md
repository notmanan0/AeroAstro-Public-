---
title: "SESA1016 T5 - Ideal Heat Engine Models"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 5
tags: [sesa1016, carnot, otto, diesel, brayton]
aliases: ["Ideal Cycles", "Air-standard cycles"]
date: 2026-09-25
status: lectured
coverage: "Lecture of 20 Feb 2025 (ll. 1–416: gas turbines, the Brayton cycle, comparison of all four cycles on a T–s diagram, Brayton example); mock-exam solutions of 13 May 2025 (ll. 12–198: Carnot limits and a Stirling engine); Chapter 5 §§5.1–5.3 (Carnot, Otto, Diesel) from the lecture notes, as those lectures were not recorded"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
next_topics: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
key_concepts: ["[[Thermal Efficiency and COP]]", "[[Isentropic Ideal-gas Relations]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 5.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-02-20.txt", "02 - Sources/Lectures/SESA1016 Lecture 2025-05-13.txt", "02 - Sources/Tutorial Sheets/Problem Sheet 04 - Heat Engine Models.pdf"]
---

# SESA1016 T5 - Ideal Heat Engine Models

> [!abstract] Summary
> Four model engines use the processes of T2 and T4. The Carnot cycle (two isotherms, two isentropes) is fully reversible and sets the upper limit $\eta=1-T_C/T_H$ for any engine between two reservoirs. The Otto, Diesel and Brayton cycles model spark-ignition, compression-ignition and gas-turbine engines; their efficiencies depend only on a volume or pressure ratio and $\gamma$: $1-r^{1-\gamma}$ for Otto, the same with a cut-off correction for Diesel, and $1-r_p^{-(\gamma-1)/\gamma}$ for Brayton. Drawn on one $T$–$s$ diagram with the same inlet and peak states, the Brayton cycle comes closest to Carnot.

> [!summary]- Exam use: quick path
> - **Use it when:** a cycle is named (or described as isentropic legs joined by constant-$v$, constant-$p$ or isothermal legs) and you need state temperatures, efficiency, net work or power.
> - **Assumptions:** closed air-standard cycle, perfect gas with $\gamma=1.4$, $c_p=1005$, $c_v=718$ J kg⁻¹ K⁻¹, isentropic compression and expansion, combustion replaced by heat addition and exhaust/intake by heat rejection.
> - **Method:** 1. Sketch the cycle on $p$–$v$ and $T$–$s$ and label states 1–4. 2. March round the cycle with the isentropic relations and the constant-$v$ or constant-$p$ ratios. 3. $q_{in}$ and $q_{out}$ from $c_v\Delta T$ (isochoric) or $c_p\Delta T$ (isobaric). 4. $\eta=1-q_{out}/q_{in}$ and check against the closed-form result. 5. $w_{net}=q_{in}-q_{out}$; power $=\dot m\,w_{net}$.
> - **Common mistakes:** using $c_p$ for a constant-volume leg (or $c_v$ for constant pressure); using °C in $1-T_C/T_H$.
> - **Practise:** [[#Worked example - Brayton cycle power]] · [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]] Q4.4, Q4.6

An engine must take in heat at high temperature and reject some at low temperature ([[SESA1016 T3 - Heat Engines and the Second Law|T3]]), and irreversible processes waste the quality of energy ([[SESA1016 T4 - Entropy and Isentropic Relations|T4]]). The best possible engine is therefore one in which every process is reversible, so that every joule of heat is used to its full potential. The Carnot engine is that engine: it takes in heat only at the source temperature and rejects it only at the sink temperature, across zero temperature difference, and does all its compression and expansion isentropically.

The Carnot engine cannot be built, because heat transfer across zero temperature difference takes forever. Practical engines have to add heat over a range of temperatures, quickly. A petrol engine burns its charge so fast that the piston hardly moves, which is modelled as heat addition at constant volume (the Otto cycle). A diesel engine injects fuel over a longer part of the stroke, which is closer to heat addition at constant pressure (the Diesel cycle). A gas turbine burns fuel continuously in a combustor at almost constant pressure, and it also rejects heat at constant pressure (the Brayton cycle).

All four use the same building blocks, so their efficiencies come out of the same algebra, and drawing them on one $T$–$s$ diagram shows at a glance why a gas turbine is so efficient: its heat addition and rejection stay closer to the Carnot isotherms than either piston-engine cycle.

---

## 1. The Carnot cycle

### Processes

The Carnot engine runs between a hot reservoir at $T_H$ and a cold one at $T_C$ through four reversible processes:

- 1–2: isothermal heat addition (expansion) at $T_1=T_2=T_H$, across zero temperature difference;
- 2–3: reversible adiabatic (isentropic) expansion from $T_H$ to $T_C$;
- 3–4: isothermal heat rejection (compression) at $T_3=T_4=T_C$;
- 4–1: isentropic compression from $T_C$ back to $T_H$.

On a $T$–$s$ diagram the two isotherms are horizontal and the two isentropes vertical, so the cycle is a rectangle.

### Carnot efficiency

Start from the efficiency in specific form,

$$
\eta_{th}=1-\frac{q_{out}}{q_{in}}
$$

Heat crosses only on the two isotherms, where $dq=T\,ds$ with $T$ constant:

$$
q_{in}=q_{12}=T_H(s_2-s_1)
$$

$$
q_{out}=-q_{34}=-T_C(s_4-s_3)=T_C(s_3-s_4)
$$

Substitute:

$$
\eta_{th}=1-\frac{T_C(s_3-s_4)}{T_H(s_2-s_1)}
$$

The two isentropes are vertical lines, so $s_3=s_2$ and $s_4=s_1$, and therefore $s_3-s_4=s_2-s_1$. The entropy terms cancel:

$$
\boxed{\eta_{Carnot}=1-\frac{T_C}{T_H}}
$$

The efficiency depends only on the two reservoir temperatures, in kelvin, and not on the working fluid. Raising $T_H$ or lowering $T_C$ improves it. To be fully reversible the engine needs a frictionless piston, perfect insulation for the adiabatic legs and processes slow enough to stay in equilibrium, and the isothermal heat transfer with zero temperature difference to drive it would take an infinite time. It is a target, not a design.

### Why nothing beats Carnot

The Carnot cycle generates no entropy (see [[#Worked example - entropy balance for a Carnot engine]]). For any engine between the same two reservoirs, the reservoirs' entropy changes are $-Q_{in}/T_H$ and $+Q_{out}/T_C$, and the engine's own entropy returns to its starting value each cycle. The second law needs the total to be non-negative:

$$
-\frac{Q_{in}}{T_H}+\frac{Q_{out}}{T_C}\ge0
$$

$$
\frac{Q_{out}}{Q_{in}}\ge\frac{T_C}{T_H}
$$

$$
\eta_{th}=1-\frac{Q_{out}}{Q_{in}}\le1-\frac{T_C}{T_H}
$$

with equality only for a reversible engine. A claimed efficiency above the Carnot value is impossible however well its first-law balance closes. A cycle that is reversible but adds heat below $T_H$, or rejects it above $T_C$, also falls short of Carnot (Problem Sheet 4, Q4.2): the temperature at which heat crosses the boundary matters as well as reversibility.

> [!tip] Lowering the sink beats raising the source
> Differentiate $\eta=1-T_C/T_H$: $\partial\eta/\partial T_C=-1/T_H$ and $\partial\eta/\partial T_H=T_C/T_H^2$. Since $T_C<T_H$, a kelvin off the sink is worth more than a kelvin on the source. In practice the sink is the atmosphere, which cannot be changed, so engine development pushes $T_H$ up instead (Problem Sheet 4, Q4.3).

## 2. The Otto cycle

### From spark-ignition engine to model

A four-stroke spark-ignition engine compresses an air–fuel mixture, sparks it near top dead centre so that fast combustion raises the pressure and drives the piston down (power stroke), pushes the products out (exhaust stroke) and draws in fresh mixture (intake stroke). The **Otto cycle** models this as a closed system with four processes:

- 1–2: isentropic compression from $V_1$ to $V_2$;
- 2–3: constant-volume heat addition ($V_3=V_2$), standing in for combustion so fast that the piston hardly moves;
- 3–4: isentropic expansion from $V_3$ to $V_4$;
- 4–1: constant-volume heat rejection ($V_4=V_1$), standing in for the exhaust and intake strokes.

The gas temperature changes during both constant-volume legs, so heat is not exchanged at a single temperature, and with fixed-temperature reservoirs those legs are not reversible.

### Otto efficiency

Both heat transfers are at constant volume, so each equals the change in internal energy:

$$
q_{in}=c_v(T_3-T_2),\qquad q_{out}=c_v(T_4-T_1)
$$

$$
\eta_{th}=1-\frac{c_v(T_4-T_1)}{c_v(T_3-T_2)}=1-\frac{T_4-T_1}{T_3-T_2}
$$

Take $T_1$ out of the numerator and $T_2$ out of the denominator:

$$
\eta_{th}=1-\frac{T_1}{T_2}\left(\frac{T_4/T_1-1}{T_3/T_2-1}\right)
$$

The two isentropic legs give

$$
\frac{T_1}{T_2}=\left(\frac{V_2}{V_1}\right)^{\gamma-1},\qquad \frac{T_4}{T_3}=\left(\frac{V_3}{V_4}\right)^{\gamma-1}
$$

and with $V_3=V_2$ and $V_4=V_1$ the right-hand sides are equal, so

$$
\frac{T_1}{T_2}=\frac{T_4}{T_3}
$$

Cross-multiplying, $T_3/T_2=T_4/T_1$, so the bracket is 1 and

$$
\eta_{th}=1-\frac{T_1}{T_2}=1-\left(\frac{V_2}{V_1}\right)^{\gamma-1}
$$

With the **compression ratio** $r=V_1/V_2$:

$$
\boxed{\eta_{Otto}=1-\frac{1}{r^{\gamma-1}}}
$$

The efficiency depends only on $r$ and $\gamma$, not on how much heat is added. It rises with compression ratio with diminishing returns, but in a spark-ignition engine $r$ is capped (typically around 10) because a hot compressed air–fuel mixture ignites on its own before the spark (knock).

![[tf_cycle_efficiency.png|900]]

## 3. The Diesel cycle

### Compression ignition

A diesel engine compresses air only. The compression heats it above the auto-ignition temperature of the fuel, and fuel injected near the end of the stroke ignites spontaneously. Injection takes longer than a spark-ignition burn, so the combustion continues while the piston moves down, and the model adds heat at constant pressure instead of constant volume:

- 1–2: isentropic compression from $V_1$ to $V_2$;
- 2–3: constant-pressure heat addition ($p_3=p_2$);
- 3–4: isentropic expansion;
- 4–1: constant-volume heat rejection ($V_4=V_1$).

Since only air is compressed, there is no knock limit, and diesel engines run at much higher compression ratios than petrol engines.

### Diesel efficiency

Heat in is at constant pressure, heat out at constant volume:

$$
q_{in}=c_p(T_3-T_2),\qquad q_{out}=c_v(T_4-T_1)
$$

$$
\eta_{th}=1-\frac{c_v(T_4-T_1)}{c_p(T_3-T_2)}=1-\frac{1}{\gamma}\frac{T_4-T_1}{T_3-T_2}
$$

$$
\eta_{th}=1-\frac{T_1}{\gamma T_2}\left(\frac{T_4/T_1-1}{T_3/T_2-1}\right)
$$

As before $T_1/T_2=r^{1-\gamma}$, but the other ratios no longer cancel. Define the **cut-off ratio**, the volume ratio over which heat is added,

$$
r_c=\frac{V_3}{V_2}
$$

Since $p_3=p_2$, the ideal-gas law turns it into a temperature ratio:

$$
r_c=\frac{V_3}{V_2}=\frac{mRT_3/p_3}{mRT_2/p_2}=\frac{T_3}{T_2}
$$

For the isentropic expansion,

$$
\frac{T_4}{T_3}=\left(\frac{V_3}{V_4}\right)^{\gamma-1}
$$

and with $V_3=r_cV_2$ and $V_4=V_1$,

$$
\frac{T_4}{T_3}=\left(\frac{r_cV_2}{V_1}\right)^{\gamma-1}=r_c^{\gamma-1}\left(\frac{V_2}{V_1}\right)^{\gamma-1}=r_c^{\gamma-1}\frac{T_1}{T_2}
$$

Rearrange:

$$
\frac{T_4}{T_1}=r_c^{\gamma-1}\frac{T_3}{T_2}
$$

and use $T_3/T_2=r_c$:

$$
\frac{T_4}{T_1}=r_c^\gamma
$$

Substitute $T_1/T_2=r^{1-\gamma}$, $T_4/T_1=r_c^\gamma$ and $T_3/T_2=r_c$ into the efficiency:

$$
\boxed{\eta_{Diesel}=1-\frac{1}{r^{\gamma-1}}\left[\frac{r_c^\gamma-1}{\gamma(r_c-1)}\right]}
$$

The bracket is the difference from the Otto cycle. For $r_c>1$ it is greater than 1 (for $r_c=2$ and $\gamma=1.4$ it is 1.17), so at the same compression ratio the Diesel cycle is less efficient than the Otto cycle: 53.4 % against 60.2 % at $r=10$, $r_c=2$. As $r_c\to1$ the bracket tends to 1 and the Otto result is recovered. The Diesel engine wins in practice because it can use a much higher $r$.

## 4. Gas turbines and the Brayton cycle

### The gas turbine engine

A gas turbine has a compressor and a turbine on a common shaft, with a combustion chamber between them. Air from the atmosphere is compressed, fuel is burnt in it at nearly constant pressure, and the hot gas expands through the turbine, which drives the compressor. What happens to the rest of the turbine's output depends on the application: in a power station about half drives a generator; in a jet engine almost all of it drives the compressor (apart from a little electrical power for the aircraft) and the useful output is the exhaust jet leaving through a nozzle. Gas turbines also power ships, and they are valued for high power, quick changes of power output and high efficiency. Most run on an **open cycle**: the exhaust leaves to atmosphere and fresh air enters.

A compressor differs from the closed systems of T1–T4 in one important way. A piston compressor squeezes a fixed mass, which has a single $p$ and $T$ at each instant. In a rotating compressor air flows continuously in at low pressure and out at high pressure, so the pressure and temperature vary through the machine; it is a **control volume**, not a closed system. Analysing it properly needs the control-volume methods of [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]]. Only the states at each component's inlet and outlet are tracked here, and work and heat are given per kilogram of air passing through ($w$, $q$). The amount of air is set by the mass flow rate $\dot m$ (kg/s) rather than a volume, and power follows as

$$
\dot W=\dot m\,w_{net}
$$

.

### The Brayton cycle

The **Brayton cycle** closes the loop for modelling: combustion is replaced by constant-pressure heat addition, and the exhaust and intake by constant-pressure heat rejection that returns the gas to the compressor inlet.

- 1–2: isentropic compression from $p_1$ to $p_2$ (compressor);
- 2–3: constant-pressure heat addition ($p_3=p_2$);
- 3–4: isentropic expansion from $p_3$ to $p_4$ (turbine);
- 4–1: constant-pressure heat rejection ($p_4=p_1$).

Only two pressures appear, so the cycle is characterised by the **pressure ratio**

$$
r_p=\frac{p_2}{p_1}=\frac{p_3}{p_4}
$$

.

![[tf_ideal_cycles_pv.png|900]]

### Brayton efficiency

Both heat transfers are at constant pressure:

$$
q_{in}=c_p(T_3-T_2),\qquad q_{out}=c_p(T_4-T_1)
$$

$$
\eta_{th}=1-\frac{T_4-T_1}{T_3-T_2}=1-\frac{T_1}{T_2}\left(\frac{T_4/T_1-1}{T_3/T_2-1}\right)
$$

The isentropic relations in pressure form give

$$
\frac{T_1}{T_2}=\left(\frac{p_1}{p_2}\right)^{(\gamma-1)/\gamma}=\left(\frac{1}{r_p}\right)^{(\gamma-1)/\gamma}
$$

$$
\frac{T_4}{T_3}=\left(\frac{p_4}{p_3}\right)^{(\gamma-1)/\gamma}=\left(\frac{1}{r_p}\right)^{(\gamma-1)/\gamma}
$$

so $T_1/T_2=T_4/T_3$, hence $T_3/T_2=T_4/T_1$, the bracket is 1, and

$$
\boxed{\eta_{Brayton}=1-\frac{T_1}{T_2}=1-\frac{1}{r_p^{(\gamma-1)/\gamma}}}
$$

. The efficiency rises with pressure ratio, which shaped the development of jet engines: the earliest had pressure ratios under 10, the latest exceed 40. Power-station gas turbines use more moderate ratios.

### Comparing the four cycles on one T–s diagram

Put all four cycles between the same two temperature extremes, with the same inlet state 1 and the same peak state 3 (highest temperature and highest pressure).

![[tf_cycle_comparison_ts.png|900]]

The Otto cycle compresses isentropically to $2_O$, adds heat at constant volume up to 3, expands isentropically to $4_O$ and rejects heat at constant volume. The Diesel cycle can compress further, to $2_D$ at the peak pressure, because it then adds heat at constant pressure up to the same state 3; after that it follows the Otto path through $4_O$ back to 1. The Brayton cycle shares the Diesel cycle's compression and heat addition, but rejects heat at constant pressure, so its turbine expands all the way down to $p_1$ and reaches a lower temperature $4_B$. The Carnot cycle compresses all the way to $T_{max}$, adds heat isothermally, expands to $T_{min}$ and rejects heat isothermally.

Of the three practical cycles, Brayton hugs the Carnot rectangle most closely: its heat addition reaches state 3 along the flatter isobar, and its heat rejection runs along the flatter low-pressure isobar close to the bottom isotherm. With the inlet and peak states of [[#Worked example - Otto cycle]] (293 K, 1 bar; 1908 K, 65.1 bar):

| Cycle | Key ratio | Efficiency |
|---|---|---|
| Otto | $r=10$ | 60.2 % |
| Diesel | $r=19.7$, $r_c=1.97$ | 64.6 % |
| Brayton | $r_p=65.1$ | 69.7 % |
| Carnot | $T_C/T_H=293/1908$ | 84.6 % |

A second reason gas turbines reach high efficiency is that many techniques exist to raise the turbine inlet temperature, the upper corner of the cycle.

### Pressure ratio for maximum specific work

Efficiency alone does not decide the design: an engine that does very little work per kilogram needs a huge mass flow for a given power. With $T_1$ and $T_3$ fixed (the turbine inlet temperature is limited by the blades), the net work depends on $r_p$. Write $a=(\gamma-1)/\gamma$. The isentropic legs give $T_2=T_1r_p^a$ and $T_4=T_3r_p^{-a}$, so

$$
w_{net}=c_p(T_3-T_2)-c_p(T_4-T_1)
$$

$$
w_{net}=c_p\left(T_3-T_1r_p^{a}-T_3r_p^{-a}+T_1\right)
$$

Differentiate with respect to $r_p$ and set to zero:

$$
\frac{dw_{net}}{dr_p}=c_p\left(-aT_1r_p^{a-1}+aT_3r_p^{-a-1}\right)=0
$$

$$
T_1r_p^{a-1}=T_3r_p^{-a-1}
$$

Multiply both sides by $r_p^{a+1}$:

$$
T_1r_p^{2a}=T_3
$$

$$
\boxed{r_{p,opt}=\left(\frac{T_3}{T_1}\right)^{1/(2a)}=\left(\frac{T_3}{T_1}\right)^{\gamma/(2(\gamma-1))}}
$$

At this pressure ratio $T_2=T_1r_p^a=T_1(T_3/T_1)^{1/2}=\sqrt{T_1T_3}$, and $T_4=T_3r_p^{-a}=T_3(T_1/T_3)^{1/2}=\sqrt{T_1T_3}$ too. The compressor exit and turbine exit temperatures are equal. Below $r_{p,opt}$ the cycle is too thin (little compression); above it, the heat addition from $T_2$ to $T_3$ shrinks and the cycle is too short. Efficiency keeps rising past $r_{p,opt}$, so design pressure ratios trade work against efficiency.

![[tf_brayton_work_vs_rp.png|900]]

---

## Worked examples

### Worked example - entropy balance for a Carnot engine

A Carnot engine takes heat from a reservoir at 1000 K and rejects it to one at 300 K, producing 1 kJ of work per cycle. Find the entropy generated per cycle (Chapter 5, Example 5.1).

$$
\eta=1-\frac{300}{1000}=0.7
$$

$$
Q_{in}=\frac{W_{net}}{\eta}=\frac{1000}{0.7}=1428.6\ \mathrm J,\qquad Q_{out}=Q_{in}-W_{net}=428.6\ \mathrm J
$$

The hot reservoir loses $Q_{in}$ and the cold one gains $Q_{out}$, each at fixed temperature:

$$
\Delta S_H=-\frac{1428.6}{1000}=-1.4286\ \mathrm{J/K},\qquad \Delta S_C=+\frac{428.6}{300}=+1.4286\ \mathrm{J/K}
$$

The engine's own entropy returns to its start, so $\Delta S_{total}=0$. It has to be zero: if the forward cycle generated entropy, running it backwards would have to destroy entropy, which is impossible, yet a reversible cycle can run either way.

### Worked example - Otto cycle

An ideal Otto cycle starts at 20 °C, 1 bar and 1 L, with a minimum volume of 0.1 L and 1 kJ of heat added per cycle. Find the maximum pressure and temperature, the work per cycle and the efficiency (Chapter 5, Example 5.2). Air: $R=287$, $c_v=718$ J kg⁻¹ K⁻¹, $\gamma=1.4$.

State 1: $T_1=293.15$ K, $p_1=10^5$ Pa, $V_1=10^{-3}$ m³. The compression ratio is $r=10$. Isentropic compression:

$$
T_2=T_1r^{\gamma-1}=293.15\times10^{0.4}=736.4\ \mathrm K
$$

$$
p_2=p_1r^\gamma=10^5\times10^{1.4}=2.512\times10^6\ \mathrm{Pa}
$$

The mass, from state 1:

$$
m=\frac{p_1V_1}{RT_1}=\frac{10^5\times10^{-3}}{287\times293.15}=1.189\times10^{-3}\ \mathrm{kg}
$$

Constant-volume heat addition, $Q_{23}=mc_v(T_3-T_2)$:

$$
T_3=T_2+\frac{Q_{23}}{mc_v}=736.4+\frac{1000}{1.189\times10^{-3}\times718}=1908\ \mathrm K
$$

$$
p_3=\frac{mRT_3}{V_3}=\frac{1.189\times10^{-3}\times287\times1908}{10^{-4}}=6.509\times10^6\ \mathrm{Pa}
$$

So $T_{max}=1908$ K and $p_{max}=65.1$ bar. Then

$$
\eta=1-10^{-0.4}=0.602,\qquad W_{net}=\eta Q_{in}=602\ \mathrm J
$$

> [!check] Net work from the heats
> $T_4=T_3/r^{0.4}=759.6$ K, so $Q_{out}=mc_v(T_4-T_1)=1.189\times10^{-3}\times718\times466.5=398$ J and $W_{net}=1000-398=602$ J.

### Worked example - Diesel cycle with the same peak state

A Diesel cycle has the same inlet state as the Otto example and the same maximum temperature and pressure. Find $r$, $r_c$ and $\eta$ (Chapter 5, Example 5.3).

Heat addition is at the maximum pressure, so $p_2=p_3=6.509\times10^6$ Pa. Isentropic compression from state 1:

$$
V_2=V_1\left(\frac{p_1}{p_2}\right)^{1/\gamma}=10^{-3}\times\left(\frac{10^5}{6.509\times10^6}\right)^{1/1.4}=5.066\times10^{-5}\ \mathrm{m^3}
$$

$$
r=\frac{V_1}{V_2}=19.74
$$

State 3 has the same $p$ and $T$ as in the Otto example, so the same volume, $V_3=10^{-4}$ m³:

$$
r_c=\frac{V_3}{V_2}=\frac{10^{-4}}{5.066\times10^{-5}}=1.974
$$

$$
\eta=1-\frac{1}{19.74^{0.4}}\left[\frac{1.974^{1.4}-1}{1.4\times0.974}\right]=0.646
$$

Limited to the same peak pressure and temperature, the Diesel cycle beats the Otto cycle (64.6 % against 60.2 %) because it reaches a much higher compression ratio.

### Worked example - Brayton cycle power

A gas turbine is modelled as an ideal Brayton cycle on air. The inlet is at 300 K and 1 bar, the pressure ratio is 20 and the turbine inlet temperature is 1000 K. Find the net specific work, the power for a mass flow of 100 kg/s, and the efficiency.

The compressor and turbine works cannot be found separately without the control-volume energy equation ([[SESA1016 T13 - Conservation of Energy and Propulsion|T13]]), but energy conservation for the cycle still gives $w_{net}=q_{in}-q_{out}$. Isentropic compression and expansion with $a=0.4/1.4=0.2857$:

$$
T_2=T_1r_p^a=300\times20^{0.2857}=706.1\ \mathrm K
$$

$$
T_4=\frac{T_3}{r_p^a}=\frac{1000}{20^{0.2857}}=424.9\ \mathrm K
$$

$$
w_{net}=c_p(T_3-T_2)-c_p(T_4-T_1)=1005\times(293.9-124.9)=169.9\ \mathrm{kJ/kg}
$$

$$
\dot W=\dot m\,w_{net}=100\times169\,900=17.0\ \mathrm{MW}
$$

$$
\eta=1-\frac{1}{20^{0.2857}}=57.5\ \%
$$

> [!check] Efficiency from the heats
> $q_{in}=1005\times(1000-706.1)=295.4$ kJ/kg, and $169.9/295.4=0.575$.

### Worked example - Brayton pressure ratio for maximum work

Compressor inlet 20 °C, turbine inlet 1000 °C. Find the maximum net specific work and the efficiency at that condition (Chapter 5, Example 5.4).

$$
r_{p,opt}=\left(\frac{1273.15}{293.15}\right)^{1.4/0.8}=13.07
$$

$$
T_2=T_4=\sqrt{293.15\times1273.15}=610.9\ \mathrm K
$$

$$
w_{net}=1005\times(1273.15-610.9)-1005\times(610.9-293.15)=346.2\ \mathrm{kJ/kg}
$$

$$
\eta=1-13.07^{-0.2857}=52.0\ \%
$$

### Worked example - inverse Diesel cycle

A cycle has isentropic compression with $r=5$, constant-volume heat addition to 1000 K, isentropic expansion and constant-pressure rejection back to state 1 at 300 K, 1 bar. Find the maximum pressure and efficiency and compare with Carnot and Brayton (Problem Sheet 4, Q4.4).

$$
T_2=300\times5^{0.4}=571.1\ \mathrm K,\qquad p_2=5^{1.4}=9.52\ \mathrm{bar}
$$

$$
p_3=p_2\frac{T_3}{T_2}=9.52\times\frac{1000}{571.1}=16.7\ \mathrm{bar}
$$

The expansion ends at $p_4=p_1$:

$$
T_4=1000\times\left(\frac{1}{16.67}\right)^{0.2857}=447.6\ \mathrm K
$$

$$
\eta=1-\frac{c_p(T_4-T_1)}{c_v(T_3-T_2)}=1-\frac{1005\times147.6}{718\times428.9}=51.8\ \%
$$

Carnot between 300 and 1000 K gives 70 %; a Brayton cycle between 1 and 16.7 bar gives $1-16.7^{-0.2857}=55.2$ %.

### Worked example - solar furnace and a Stirling engine

A solar furnace reaches 3500 K with a peak thermal power of 1 MW; a propane flame reaches about 2000 K. A heat engine rejecting heat at 300 K drives a generator of efficiency 80 %. Compare the Carnot limits, find the largest possible electrical power, then the efficiency and power of a Stirling engine, modelled as two isochoric processes joined by two isotherms, with $V_{max}/V_{min}=10$ and air as the working fluid (mock exam).

The Carnot limits are

$$
\eta_{solar}=1-\frac{300}{3500}=91.4\ \%,\qquad \eta_{propane}=1-\frac{300}{2000}=85\ \%
$$

and the largest possible electrical power is $1\ \mathrm{MW}\times0.914\times0.8=731$ kW.

Number the Stirling cycle 1→2 isochoric heating at $V_{min}$ from $T_C$ to $T_H$, 2→3 isothermal expansion at $T_H$ to $V_{max}$, 3→4 isochoric cooling to $T_C$, 4→1 isothermal compression at $T_C$. Heat enters on 1→2 and on the isothermal expansion, where $\Delta u=0$ so $q=w=RT_H\ln(V_3/V_2)$:

$$
q_{in}=c_v(T_H-T_C)+RT_H\ln10=718\times3200+287\times3500\times\ln10=4611\ \mathrm{kJ/kg}
$$

Heat leaves on the matching legs, the isothermal one now at $T_C$:

$$
q_{out}=c_v(T_H-T_C)+RT_C\ln10=718\times3200+287\times300\times\ln10=2496\ \mathrm{kJ/kg}
$$

$$
\eta=1-\frac{2496}{4611}=45.9\ \%,\qquad P_{el}=1\ \mathrm{MW}\times0.459\times0.8=367\ \mathrm{kW}
$$

On a $p$–$V$ diagram the Stirling cycle looks like the Otto cycle, but its curved legs are isotherms, not isentropes, so the Otto formula $1-r^{1-\gamma}$ does not apply. The large isochoric heat input is why it falls so far short of Carnot.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T4 - Entropy and Isentropic Relations]] · Next: [[SESA1016 T6 - Dimensional Analysis and Similarity]]
- Concepts: [[Thermal Efficiency and COP]] · [[Isentropic Ideal-gas Relations]] · [[Entropy Generation]]
- Worked sheet: [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Gas turbine as a control volume: [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]] · Propulsion: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]

## Sources

- `Chapter 5.pdf`: lecture notes Chapter 5, Heat engine models, §§5.1–5.4, Examples 5.1–5.4, Figs 5.1–5.9.
- `SESA1016 Lecture 2025-02-20.txt` (20 Feb 2025): gas turbines as control volumes (ll. 1–123), the Brayton cycle (ll. 124–191), all four cycles on one $T$–$s$ diagram (ll. 192–285), Brayton efficiency (ll. 286–333), example at $r_p=20$ (ll. 336–406).
- `SESA1016 Lecture 2025-05-13.txt` (13 May 2025): mock-exam solutions, question 1 (ll. 12–198), the solar furnace and Stirling engine.
- `Problem Sheet 04 - Heat Engine Models.pdf`: Q4.1–Q4.6, printed answers and worked solutions to Q4.2 and Q4.6.
- The Carnot, Otto and Diesel lectures were not recorded; §§1–3 are written from the lecture notes.

## Self-study tasks

### Core

- [ ] Brayton example at $r_p=20$: the efficiency was left to you (20 Feb, ll. 404–406). Target 57.5 %. → [[#Worked example - Brayton cycle power]]
- [ ] Q4.1, dual cycle: state temperatures, efficiency formula, $T_{max}$, $p_{max}$, $\eta$ (Problem Sheet 4, the tutorial problem). Targets 2089 K, 13.9 bar, 51.7 %. → [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]
- [ ] Q4.2, reversible cycle with sloping heat addition against Carnot (worked solution). Targets 66.7 % and 75 %. → [[#Why nothing beats Carnot]] · [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]
- [ ] Q4.3, Carnot engine between 500 °C and 20 °C. Targets 62.1 %, 1611 kJ, 611 kJ, −2.08 kJ/K. → [[#Carnot efficiency]] · [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]
- [ ] Q4.4, inverse Diesel cycle. → [[#Worked example - inverse Diesel cycle]]
- [ ] Q4.5, three-process cycle with a straight-line heat rejection. Targets 1679 J, 39.2 % (but read the warning in the solution note). → [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]
- [ ] Q4.6, Brayton turbine inlet temperature for 100 kJ/kg at $r_p=12$ (worked solution). Target 806 K. → [[#Brayton efficiency]] · [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]]

- [ ] Mock exam question 1: Carnot limits for a solar furnace and a Stirling engine (13 May, ll. 12–198). Targets 91.4 %, 85 %, 731 kW, 45.9 %, 367 kW. → [[#Worked example - solar furnace and a Stirling engine]]

### Further practice

- [ ] Draw the Otto, Diesel, Brayton and Carnot cycles on one $T$–$s$ diagram with the same state 1 and state 3, and explain from it why Brayton is the most efficient practical cycle (20 Feb, ll. 192–268). → [[#Comparing the four cycles on one T–s diagram]]
- [ ] Derive the Otto, Diesel and Brayton efficiencies from $1-q_{out}/q_{in}$. → [[#Otto efficiency]] · [[#Diesel efficiency]] · [[#Brayton efficiency]]
- [ ] Derive $r_{p,opt}$ and show $T_2=T_4=\sqrt{T_1T_3}$ there (Chapter 5, Example 5.4). → [[#Pressure ratio for maximum specific work]]

## Transcript and slide slips

> [!warning] Transcript slip (20 Feb, l. 399)
> Where: [[#Worked example - Brayton cycle power]].
>
> The net work is first read out as 117 kJ/kg, then used as 170 000 J/kg to get 17 MW (ll. 402–403). The correct value is 169.9 kJ/kg, so 17 MW stands.

> [!warning] Transcript slips on process names (20 Feb, ll. 188 and 310)
> Where: [[#The Brayton cycle]] · [[#Brayton efficiency]].
>
> Process 3–4 is called an isobaric expansion (l. 188) and process 1–2 an isobaric compression (l. 310). Both are isentropic; the board relations used with them are the isentropic ones.

> [!warning] Lecture-notes slip (Chapter 5, eq. 5.79)
> Where: [[#The Brayton cycle]].
>
> The pressure ratio is printed $r_p=p_2/p_1=p_3/p_2$. Since $p_3=p_2$ that would make $r_p=1$; it should be $p_3/p_4$, as the transcript has (20 Feb, ll. 180–182).

> [!warning] Lecture-notes slip (Chapter 5, text after eq. 5.64)
> Where: [[#Diesel efficiency]].
>
> "Combining this with equation (5.61)" should refer to eq. (5.60), the compression relation $T_1/T_2=(V_2/V_1)^{\gamma-1}$, which is the one substituted.

> [!warning] Transcript slip (13 May, ll. 34–35)
> Where: [[#Worked example - solar furnace and a Stirling engine]].
>
> The Carnot efficiency of the solar furnace is read out as 94.1 % and then written 0.914. $1-300/3500=0.914$, i.e. 91.4 %, which is the value used for the 731 kW.
