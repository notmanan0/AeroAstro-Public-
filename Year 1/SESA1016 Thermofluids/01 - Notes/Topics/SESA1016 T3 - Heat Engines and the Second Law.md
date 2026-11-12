---
title: "SESA1016 T3 - Heat Engines and the Second Law"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 3
tags: [sesa1016, heat-engine, second-law, efficiency]
aliases: ["Heat Engines"]
date: 2026-09-25
status: written-ahead
coverage: "Chapter 3 §§3.1–3.5 from the lecture notes; no recording survives for the Heat Engines lectures (Feb 2025), so there is no transcript to confirm the scope"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T2 - Work, Heat and the First Law]]"]
next_topics: ["[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
key_concepts: ["[[Thermal Efficiency and COP]]", "[[Entropy Generation]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 3.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 03 - Heat Engines and Entropy.pdf"]
---

# SESA1016 T3 - Heat Engines and the Second Law

> [!abstract] Summary
> A heat engine runs a closed system round a cycle so that it can keep turning heat into work. Because the gas returns to its starting state, $\Delta U_{cycle}=0$ and the net work equals the net heat, $W_{net}=Q_{in}-Q_{out}$, which is the area enclosed on the $p$–$V$ diagram. The thermal efficiency $\eta_{th}=W_{net}/Q_{in}=1-Q_{out}/Q_{in}$ can never reach 1: the second law (Kelvin–Planck) says every cyclic engine must reject heat to a colder sink. Engines come closest to the limit when every process is reversible.

> [!summary]- Exam use: quick path
> - **Use it when:** a cycle is described process by process and you need the net work, the heat in and out, or the efficiency; or a claimed engine must be judged possible or impossible.
> - **Assumptions:** closed system, perfect gas, quasi-equilibrium processes, the same mass throughout the cycle.
> - **Method:** 1. Draw the cycle on a $p$–$V$ diagram (clockwise means net work out). 2. Find every state with $pV=mRT$ and the process constraints. 3. Find $Q$ for each leg and sort them into $Q_{in}$ (legs with $Q>0$) and $Q_{out}$ (the magnitude of the legs with $Q<0$). 4. $W_{net}=Q_{in}-Q_{out}$, or add the leg works as a check. 5. $\eta_{th}=W_{net}/Q_{in}$.
> - **Common mistakes:** dividing by the net heat instead of the heat supplied; leaving out a heat-input leg (an isothermal expansion also takes in heat).
> - **Practise:** [[#Worked example - a three-process engine]] · [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]] Q3.1, Q3.2, Q3.4

A single expansion can do work once. An isothermal expansion of gas under a piston turns all the heat it takes in into work, but then the piston is at the top of the cylinder and the device is finished. To get work continuously the gas has to be brought back to where it started, over and over. That return trip is the problem: pushing the gas back along the same isotherm takes exactly as much work as the expansion gave, so the net gain is zero.

The way out is to come back by a route at lower pressure, so that less work is needed to compress the gas than it delivered when it expanded. Lower pressure at the same volume means lower temperature, so the gas has to be cooled on the way back, and that means rejecting heat. Every engine that runs in a cycle therefore takes heat in at high temperature, gives some of it out at low temperature and keeps the difference as work. Exhaust from a jet engine is the rejected heat of one such cycle.

That the rejected heat can never be zero is the second law of thermodynamics, which also says which way heat flows on its own and why friction and leaks waste work. Entropy ([[SESA1016 T4 - Entropy and Isentropic Relations|T4]]) measures how far a process is from reversible, and the best efficiency any engine can reach between two temperatures follows from it ([[SESA1016 T5 - Ideal Heat Engine Models|T5]]).

---

## 1. Thermodynamic cycles

### Why a cycle needs a different return path

An isothermal expansion of a perfect gas has $\Delta U=0$, so the first law gives

$$
W_{12}=Q_{12}
$$

all the heat taken in becomes work. Reversing it along the same isotherm needs work done on the gas equal to the heat it then rejects, $W_{21}=Q_{21}=-W_{12}$, and the two together give zero net work.

To finish with net work the return path must lie below the expansion path on the $p$–$V$ diagram, because the work is the area under each curve. An isobaric compression at the lower pressure $p_2$ back to the starting volume needs less work than the expansion produced:

$$
-W_{23}<W_{12}
$$

The gas is now at the original volume but at lower pressure and temperature. An isochoric heating at that volume takes it back to state 1 with no work at all, since $dV=0$. The cycle is complete and

$$
W_{net}=W_{12}+W_{23}+W_{31}>0
$$

![[tf_example_cycle_pv.png|900]]

Any closed loop traced clockwise on a $p$–$V$ diagram encloses positive net work, because the expansion (moving right) happens at higher pressure than the compression (moving left). The net work is the enclosed area. An anticlockwise loop needs net work put in. Many cycles are possible; the design goal is the one that gives the most net work for each joule of heat supplied.

### The first law for a cycle

Apply $\Delta U=Q-W$ to each leg and add:

$$
\Delta U_{12}+\Delta U_{23}+\Delta U_{31}=(Q_{12}+Q_{23}+Q_{31})-(W_{12}+W_{23}+W_{31})
$$

$$
\Delta U_{cycle}=Q_{net}-W_{net}
$$

The gas ends in the state it started in. $U$ is a property, so it returns to its starting value with $p$, $V$ and $T$:

$$
\Delta U_{cycle}=0
$$

and therefore

$$
\boxed{W_{net}=Q_{net}}
$$

The net heat is the heat supplied minus the heat rejected, not the heat supplied. The net work can therefore be computed either way round, from the works or from the heats, and the easier route (often the heats) can be chosen, with the other as a check.

## 2. Thermal efficiency

Split the net heat explicitly into the heat supplied $Q_{in}$ and the waste heat rejected $Q_{out}$, both positive numbers:

$$
Q_{net}=Q_{in}-Q_{out}
$$

Only $Q_{in}$ costs anything: it is the fuel burnt. The rejected heat, like the hot exhaust leaving a jet engine, cannot be fed back to run the cycle. What is wanted is the net work. The **thermal efficiency** is the net work divided by the heat supplied:

$$
\boxed{\eta_{th}=\frac{W_{net}}{Q_{in}}}
$$

Substitute $W_{net}=Q_{net}=Q_{in}-Q_{out}$:

$$
\eta_{th}=\frac{Q_{in}-Q_{out}}{Q_{in}}
$$

$$
\boxed{\eta_{th}=1-\frac{Q_{out}}{Q_{in}}}
$$

Both forms hold per unit mass, $\eta_{th}=w_{net}/q_{in}=1-q_{out}/q_{in}$. The second form shows the two ways to improve an engine: reject less heat for the same input, or take in more heat for the same rejection. The second law puts a hard limit on both.

![[tf_heat_engine_energy_flow.png|900]]

## 3. The second law

### Direction of processes

The first law allows any process that conserves energy. A cup of coffee at 80 °C in a room at 20 °C cools, losing perhaps 5 kJ of internal energy while the room gains 5 kJ. The reverse, the room losing 5 kJ so the coffee warms up, conserves energy just as well, and never happens. The **second law** supplies the missing rule: heat flows spontaneously only from a higher temperature to a lower one. A process is possible only if it satisfies both laws.

### Kelvin–Planck statement and thermal reservoirs

A **thermal reservoir** is a body so large that heat can be added or removed without changing its temperature. A **source** supplies heat at a fixed high temperature $T_H$ (a combustion process is close to this); a **sink** absorbs heat at a fixed low temperature $T_C$ (usually the ambient air).

The **Kelvin–Planck statement** is the second law for heat engines:

> It is impossible for any device that operates on a cycle to receive heat from a single reservoir and produce a net amount of work.

Every heat engine therefore needs a sink as well as a source, $Q_{out}>0$, and

$$
\eta_{th}<1
$$

for every engine, however well built. The first law alone would allow $Q_{out}=0$ and 100 % efficiency; the second law forbids it. The reason is not friction (Problem Sheet 3, Q3.3): even a perfectly reversible engine must reject heat.

The direction of heat flow fixes the reservoir temperatures needed by any particular cycle. Heat can enter the gas only from something hotter than the gas, so the source must be hotter than the hottest point at which heat is added; heat can leave only to something colder, so the sink must be colder than the coldest point at which heat is rejected. The rejected heat can then never be returned to the source, because that would need heat to flow from the colder sink to the hotter source on its own ([[#Worked example - which reservoirs does the cycle need]]).

### Heat pumps

Each process of an engine cycle can run backwards. Run the cycle of §1 anticlockwise, 1→3→2→1: isochoric cooling, isobaric expansion taking in heat at low temperature, and isothermal compression rejecting heat at high temperature. Now net work must be supplied, $W_{in}=Q_{out}-Q_{in}$, and in return heat is moved from a cold body to a hot one.

That does not break the second law, which only forbids heat flowing from cold to hot on its own; here work drives it. A **heat pump** used for heating a building takes heat from the cold outside air or ground and delivers it indoors, so it can deliver several joules of heat per joule of work, far more than a heater that converts the work directly. Refrigerators, air conditioners and dehumidifiers use the same principle with the cold side as the useful one.

Applying the same rule as for efficiency, the output wanted divided by the work paid for, to a heat pump, the **coefficient of performance** is $COP_{HP}=Q_H/W_{in}$ for heating and $COP_R=Q_C/W_{in}$ for refrigeration. Since $W_{in}=Q_H-Q_C$, $COP_{HP}=COP_R+1$. A COP above 1 is normal, because it measures heat moved per unit work, not energy converted.

## 4. Reversible and irreversible processes

A **reversible** process is one that, after it has been run backwards, leaves no trace anywhere, in the system or its surroundings, that it ever happened. No real process is reversible, but some come close, and engines are most efficient when all their processes approach reversibility.

Three common sources of irreversibility are friction, unrestrained expansion and heat transfer across a finite temperature difference. Work spent overcoming friction becomes heat in the rubbing surfaces, and heating the surfaces will never push the piston back, so a gas compressed by a piston with friction and then expanded back to the same pressure leaves heat behind, which is the trace. Air leaking from a tyre is an unrestrained expansion: it does no useful work on the way out, and nothing recovers that work to push it back in. Heat transfer across a finite temperature difference runs one way only; the coffee cools in the room but never warms up from it.

Mixing (milk into coffee), plastic deformation, most chemical reactions including combustion, and current through a resistor are irreversible too. A quick test is a film of the process played backwards: if it looks impossible, the process is irreversible. Heat generation often accompanies irreversibility, but it is not the definition, and not every irreversible process generates heat.

The near-reversible counterparts are lifting a weight without friction (all the work comes back when it is lowered), slow controlled expansion of gas under a frictionless piston (the work extracted can push it back), compressing a perfectly elastic spring, spinning up a frictionless flywheel, and heat transfer across a vanishingly small temperature difference. The last is a limit rather than a practical process, since zero temperature difference means no heat flows at all; the design aim is to keep the difference as small as practical.

All irreversible processes generate entropy, the measure of irreversibility ([[SESA1016 T4 - Entropy and Isentropic Relations|T4]]). The best possible efficiency between two reservoirs, reached when every process is reversible, is the Carnot efficiency $1-T_C/T_H$ derived in [[SESA1016 T5 - Ideal Heat Engine Models|T5]].

---

## Worked examples

### Worked example - a three-process engine

Air in a piston–cylinder starts at $T_1=600$ K, $p_1=5$ bar, $V_1=1$ L. It expands isothermally to $V_2=5$ L, is compressed isobarically back to $V_3=1$ L and returns to state 1 at constant volume. Show that the net work equals the net heat, and find the efficiency (Chapter 3, Examples 3.1–3.2). Take $R=287$, $c_p=1005$, $c_v=718$ J kg⁻¹ K⁻¹.

Isothermal expansion 1→2. With $m=p_1V_1/(RT_1)$ and $T=T_1$, the pressure along the path is $p=mRT_1/V=p_1V_1/V$, so

$$
W_{12}=p_1V_1\int_{V_1}^{V_2}\frac{dV}{V}=p_1V_1\ln\frac{V_2}{V_1}
$$

$$
W_{12}=5\times10^5\times1\times10^{-3}\times\ln5=804.7\ \mathrm J
$$

The volume ratio is dimensionless, so any volume unit works inside the logarithm.

Isobaric compression 2→3. At constant temperature $p_2=p_1V_1/V_2=1\times10^5$ Pa, and

$$
W_{23}=p_2(V_3-V_2)=1\times10^5\times(1-5)\times10^{-3}=-400\ \mathrm J
$$

Isochoric heating 3→1: $W_{31}=0$. So

$$
W_{net}=804.7-400+0=404.7\ \mathrm J
$$

For the heats, the mass is

$$
m=\frac{p_1V_1}{RT_1}=\frac{5\times10^5\times1\times10^{-3}}{287\times600}=2.904\times10^{-3}\ \mathrm{kg}
$$

and $T_3=p_2V_3/(mR)=120$ K. For 1→2, $\Delta U=0$, so $Q_{12}=W_{12}=804.7$ J. For 2→3 at constant pressure, $Q=mc_p\Delta T$:

$$
Q_{23}=2.904\times10^{-3}\times1005\times(120-600)=-1400.7\ \mathrm J
$$

For 3→1 at constant volume, $Q=mc_v\Delta T$:

$$
Q_{31}=2.904\times10^{-3}\times718\times(600-120)=1000.7\ \mathrm J
$$

$$
Q_{net}=804.7-1400.7+1000.7=404.7\ \mathrm J=W_{net}
$$

Heat enters on two legs, $Q_{in}=804.7+1000.7=1805.4$ J, and leaves on one, $Q_{out}=1400.7$ J. Then

$$
\eta_{th}=\frac{W_{net}}{Q_{in}}=\frac{404.7}{1805.4}=22.4\ \%
$$

> [!check] Efficiency both ways
> $1-Q_{out}/Q_{in}=1-1400.7/1805.4=0.224$, the same 22.4 %.

### Worked example - which reservoirs does the cycle need

For the same cycle, show that a sink is needed and that the waste heat cannot go back to the source (Chapter 3, Example 3.3).

Heat enters during 1→2 with the gas at 600 K throughout. Heat flows only from hot to cold, so the source must be hotter than that:

$$
T_H>600\ \mathrm K
$$

Heat leaves during 2→3, while the gas cools from 600 K to 120 K. The sink must be colder than the gas at every point of the rejection, so colder than the lowest gas temperature:

$$
T_C<120\ \mathrm K
$$

Returning $Q_{out}$ to the source would need heat to flow from below 120 K to above 600 K with nothing driving it, which the second law forbids. The isochoric heating 3→1, which starts at 120 K, also has to be supplied from the source. A cycle that rejects heat at such a low temperature is impractical; the cycles of [[SESA1016 T5 - Ideal Heat Engine Models|T5]] add and reject heat over narrower temperature ranges.

### Worked example - two engineers, two cycles

Both cycles start with constant-volume heating of air from 1 bar and 300 K to 900 K and end with constant-pressure heat rejection back to state 1. Cycle A closes with a reversible adiabatic expansion to 1 bar, cycle B with an isothermal expansion to 1 bar. Engineer A says A is better because it needs less heat; engineer B says B is better because it gives more work. Which is more efficient? (Problem Sheet 3, Q3.2, the sheet's worked solution.)

![[tf_two_engines_pv.png|900]]

Shared heating 1→2 at constant volume:

$$
q_{12}=c_v(T_2-T_1)=718\times600=430.8\ \mathrm{kJ/kg}
$$

and $p_2=p_1T_2/T_1=3$ bar.

Cycle A: the reversible adiabatic expansion to 1 bar gives

$$
T_{3A}=T_2\left(\frac{p_1}{p_2}\right)^{(\gamma-1)/\gamma}=900\times\left(\tfrac13\right)^{0.2857}=657.5\ \mathrm K
$$

and the isobaric rejection is $q_{out}=c_p(T_{3A}-T_1)=1005\times357.5=359.3$ kJ/kg. So

$$
\eta_A=1-\frac{359.3}{430.8}=16.6\ \%
$$

Cycle B: the isothermal leg at 900 K takes in heat equal to its work. With $v_3/v_2=p_2/p_1=3$,

$$
q_{23}=RT_2\ln\frac{v_3}{v_2}=287\times900\times\ln3=283.8\ \mathrm{kJ/kg}
$$

so $q_{in}=430.8+283.8=714.6$ kJ/kg, and the rejection starts from 900 K, $q_{out}=c_p(900-300)=603.0$ kJ/kg. So

$$
\eta_B=1-\frac{603.0}{714.6}=15.6\ \%
$$

Both engineers are right about their facts: A takes in and rejects less heat, B gives more net work (111.6 against 71.5 kJ/kg). Neither fact decides the efficiency, which is a ratio. A wins, narrowly, because B's extra work costs proportionally more heat.

### Worked example - the triangle engine

An engine traces a triangle on the $p$–$V$ diagram: state 1 at 1 bar, 1 L, 300 K; state 2 at 10 bar, 10 L; state 3 at 1 bar, 10 L; working fluid air. Is it any good? (Problem Sheet 3, Q3.4.)

Process 1→2 is a straight line, not a standard process, but the work is still the area under it, a trapezium:

$$
W_{12}=\frac{p_1+p_2}{2}(V_2-V_1)=\frac{(1+10)\times10^5}{2}\times9\times10^{-3}=4.95\ \mathrm{kJ}
$$

The mass is $m=p_1V_1/(RT_1)=1.161\times10^{-3}$ kg, and since $pV$ rises by a factor of 100, $T_2=100T_1=30\,000$ K. Then

$$
\Delta U_{12}=mc_v(T_2-T_1)=1.161\times10^{-3}\times718\times29\,700=24.77\ \mathrm{kJ}
$$

$$
Q_{12}=\Delta U_{12}+W_{12}=29.7\ \mathrm{kJ}
$$

The net work is the triangle's area:

$$
W_{net}=\tfrac12(10-1)\times10^5\times(10-1)\times10^{-3}=4.05\ \mathrm{kJ}
$$

Legs 2→3 (constant volume, pressure falling) and 3→1 (constant pressure, volume falling) both cool the gas, so 1→2 is the only heat input. Along 1→2, $p\propto V$, so $dQ=dU+p\,dV$ is positive all the way (both $T$ and $V$ rise), and $Q_{in}=29.7$ kJ:

$$
\eta_{th}=\frac{4.05}{29.7}=13.6\ \%
$$

This cycle is impractical: the peak temperature of 30 000 K would destroy any material, and 13.6 % is poor for such an extreme cycle.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T2 - Work, Heat and the First Law]] · Next: [[SESA1016 T4 - Entropy and Isentropic Relations]]
- Concepts: [[Thermal Efficiency and COP]] · [[Entropy Generation]] · [[Thermodynamic State and Process]]
- Worked sheet: [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Continues in: [[SESA1016 T5 - Ideal Heat Engine Models|T5]] (Carnot limit and engine models) · [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] (thermal and overall efficiency of jet engines)

## Sources

- `Chapter 3.pdf`: lecture notes Chapter 3, Heat engines, §§3.1–3.5, Examples 3.1–3.3, Figs 3.1–3.8.
- `Problem Sheet 03 - Heat Engines and Entropy.pdf`: Q3.1–Q3.4 on cycles and the second law (Q3.5–Q3.6 belong to [[SESA1016 T4 - Entropy and Isentropic Relations|T4]]), printed answers and worked solutions to Q3.2 and Q3.5.
- No transcript: the Heat Engines lectures were not recorded, so this note is written from the lecture notes. The heat-pump COP paragraph goes slightly beyond the notes, which describe heat pumps only qualitatively.

## Self-study tasks

The weekly problem sheet is the set work; none of it can be tied to a transcript line.

### Core

- [ ] Q3.1, spacecraft environmental-control cycle (rectangle on the $p$–$V$ diagram; Problem Sheet 3, the tutorial problem). Targets $T_2=600$ K, $p_3=p_4=41.7$ kPa, $T_4=125$ K, $w_{net}=50.2$ kJ/kg, $\eta=11.8$ %. → [[#2. Thermal efficiency]] · [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]
- [ ] Q3.2, two engineers and two cycles (worked solution). Targets 16.6 % and 15.6 %. → [[#Worked example - two engineers, two cycles]]
- [ ] Q3.3, why no engine can be 100 % efficient. Answer (c). → [[#Kelvin–Planck statement and thermal reservoirs]]
- [ ] Q3.4, the triangle engine. Targets 4.95 kJ, 29.7 kJ, 4.05 kJ, 13.6 %. → [[#Worked example - the triangle engine]]

### Further practice

- [ ] Rework Chapter 3 Examples 3.1–3.3 closed-book. → [[#Worked example - a three-process engine]] · [[#Worked example - which reservoirs does the cycle need]]
- [ ] For each process in Q3.1, say whether it could be reversible and what the source and sink temperatures would have to be (Problem Sheet 3, Q3.1e). → [[#4. Reversible and irreversible processes]]
- [ ] Run the cycle of Example 3.1 backwards as a heat pump and find the work input and heat delivered at the top temperature (suggested, not lecturer-set). → [[#Heat pumps]]

## Transcript and slide slips

> [!warning] Lecture-notes slip (Chapter 3, eq. 3.28)
> Where: [[#Worked example - a three-process engine]].
>
> The isochoric heat is written $2.904\cdot10^{-3}\times817\times(600-120)$. The value of $c_v$ quoted at the start of the example is 718 J kg⁻¹ K⁻¹, and 1000.7 J is the result with 718; with 817 it would be 1138.7 J. Only the substituted digits are transposed.

> [!warning] Problem-sheet slip (Problem Sheet 3, answers to Q3.1)
> Where: [[#2. Thermal efficiency]].
>
> The answers are labelled a), b), c) although the questions asking for them are b), c), d), and "$T_2=600$ K" is printed twice. The values themselves are correct.
