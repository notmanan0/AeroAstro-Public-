---
title: "SESA1016 T4 - Entropy and Isentropic Relations"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 4
tags: [sesa1016, entropy, isentropic, second-law]
aliases: ["Entropy", "Tds equations"]
date: 2026-09-25
status: written-ahead
coverage: "Chapter 4 §§4.1–4.5 from the lecture notes; no recording survives for the Entropy lectures (Feb 2025), so there is no transcript to confirm the scope"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T3 - Heat Engines and the Second Law]]"]
next_topics: ["[[SESA1016 T5 - Ideal Heat Engine Models]]"]
key_concepts: ["[[Entropy Generation]]", "[[Isentropic Ideal-gas Relations]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 4.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 03 - Heat Engines and Entropy.pdf"]
---

# SESA1016 T4 - Entropy and Isentropic Relations

> [!abstract] Summary
> Entropy is the property that every irreversible process generates and no process destroys. For a reversible process its change is $dS=dQ/T$; for any process $dS\ge dQ/T$, the difference being the entropy generated, so the entropy of an isolated system never decreases. Combining the definition with the first law gives the $T\,ds$ equations, and for a perfect gas these integrate to $\Delta s=c_v\ln(T_2/T_1)+R\ln(v_2/v_1)=c_p\ln(T_2/T_1)-R\ln(p_2/p_1)$. Setting $\Delta s=0$ gives the isentropic relations $Tv^{\gamma-1}$, $Tp^{(1-\gamma)/\gamma}$ and $pv^\gamma$ constant.

> [!summary]- Exam use: quick path
> - **Use it when:** you need the entropy change between two states, want to judge which of two processes is more irreversible, or need $T$, $p$ or $v$ at the end of a reversible adiabatic process.
> - **Assumptions:** perfect gas ($c_v$, $c_p$ constant) for the log formulas; reservoirs at fixed temperature for $\Delta S=Q/T$; isentropic means reversible and adiabatic.
> - **Method:** 1. Identify the two end states (any path between them gives the same $\Delta s$). 2. Pick the formula matching the known properties ($T$ and $v$, or $T$ and $p$). 3. For reservoirs, $\Delta S=Q/T$ for each, with $Q$ positive into it. 4. Add over everything involved to get $S_{gen}$, which must be $\ge0$. 5. For isentropic steps use $T_2/T_1=(p_2/p_1)^{(\gamma-1)/\gamma}=(v_1/v_2)^{\gamma-1}$.
> - **Common mistakes:** °C inside a logarithm or in $Q/T$; assuming adiabatic means isentropic (an irreversible adiabatic process has $\Delta s>0$).
> - **Practise:** [[#Worked example - which heat transfer is more irreversible]] · [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]] Q3.5–Q3.6

Irreversible processes have something in common. Many of them generate heat (friction, current through a resistor), but not all of them: air leaking from a cylinder into a room produces no friction to speak of, yet it cannot be undone. What every irreversible process does is generate entropy.

Microscopically, entropy measures disorder. A more useful picture for an engineer is that it measures the quality of energy. Compressed air at 10 bar in a cylinder can drive a piston and lift a weight. Open the valve and the same energy is still in the room, as a slightly higher pressure and temperature everywhere, but spread so thinly that it can do almost nothing. The energy has been conserved and its quality has dropped; the entropy of the room plus cylinder has risen. A hot cup of coffee could run a small heat engine against the room; once it has cooled, the same total energy can run nothing.

To turn this into numbers, the change in entropy is defined through reversible heat transfer, $dS=dQ_{rev}/T$. Because entropy is a property, its change between two states does not depend on the path, so it can always be computed along an imaginary reversible path even when the real process was irreversible. For a perfect gas this gives closed formulas in $T$, $p$ and $v$, and setting the change to zero gives the isentropic relations that every ideal engine and nozzle model uses.

---

## 1. Definition of entropy change

For a reversible process, the change in entropy is

$$
\boxed{dS=\frac{dQ}{T}}
$$

with $T$ the absolute temperature at which the heat crosses. The units are J/K, and specific entropy $s=S/m$ has units J kg⁻¹ K⁻¹. Entropy is a **property**: it depends only on the state, so $\Delta S$ between two states is the same whatever the path. The definition gives only changes, not absolute values, which is all any calculation here needs.

Because $S$ is a property, a process can be drawn on a **temperature–entropy** ($T$–$S$) diagram, just as on a $p$–$V$ diagram. Rearranging the definition, $dQ=T\,dS$, so for a reversible process

$$
Q_{12}=\int_1^2T\,dS
$$

and the heat transferred is the area under the path on a $T$–$S$ diagram, in the same way that work is the area under the path on a $p$–$V$ diagram.

Integrating $dS=dQ/T$ directly needs $Q$ as a function of $T$ along the path, which is usually not known. There are two exceptions.

For a **reversible isothermal** process $T$ is constant, so it comes out of the integral:

$$
\Delta S=\int_1^2\frac{dQ}{T}=\frac{1}{T}\int_1^2dQ
$$

$$
\boxed{\Delta S=\frac{Q_{12}}{T}}
$$

a horizontal line on the $T$–$S$ diagram. Heat in moves it to the right.

For a **reversible adiabatic** process $dQ=0$ throughout, so $\Delta S=0$: a vertical line on the $T$–$S$ diagram. Such a process is called **isentropic**. It is the model for efficient compressors, turbines, diffusers, jet and rocket nozzles and the compression and expansion strokes of piston engines, and every engine model in [[SESA1016 T5 - Ideal Heat Engine Models|T5]] uses it.

![[tf_ts_processes.png|900]]

## 2. Entropy generation

### The general inequality

The definition holds only for reversible processes. For any process,

$$
dS\ge\frac{dQ}{T}
$$

with equality for a reversible process and strict inequality for an irreversible one. Writing the difference explicitly as the **entropy generated** by irreversibilities,

$$
\boxed{dS=\frac{dQ}{T}+dS_{gen},\qquad dS_{gen}\ge0}
$$

The first term is entropy carried across the boundary with heat, which can have either sign. The second is entropy created inside by friction, unrestrained expansion, mixing or heat flow across a finite temperature difference, and it is never negative. A process with $S_{gen}<0$ is impossible.

Two consequences follow at once. An adiabatic process ($dQ=0$) has $dS=dS_{gen}\ge0$: it is isentropic only if it is also reversible, and any real adiabatic compressor or turbine raises the entropy of the gas. And for an **isolated system**, which exchanges no heat or work with anything, $dQ=0$ so

$$
dS_{isolated}\ge0
$$

The entropy of an isolated system cannot decrease. It stays constant at best, and in practice every process inside it raises it.

### Heat flow from hot to cold, step by step

A cup of coffee at 80 °C (353 K) sits inside a room of air at 20 °C (293 K), with the whole room insulated so that together they form an isolated system. Heat flows from the coffee to the air inside the boundary but none crosses it. Let a small amount, 1 J, pass, small enough that neither temperature changes noticeably. If the transfer is slow enough for each body to stay in equilibrium, $dS=dQ/T$ applies to each.

The coffee loses heat, $\delta Q=-1$ J:

$$
\delta S_{cup}=\frac{-1}{353}=-0.0028\ \mathrm{J/K}
$$

The air gains it, $\delta Q=+1$ J:

$$
\delta S_{air}=\frac{+1}{293}=+0.0034\ \mathrm{J/K}
$$

The isolated system:

$$
\delta S_{sys}=\delta S_{air}+\delta S_{cup}=+0.0006\ \mathrm{J/K}
$$

The same joule carries more entropy into the cold air than it took out of the hot coffee, because it is divided by a smaller temperature. The coffee's entropy falls, the room's rises by more, and the total goes up. Energy is conserved; entropy is not. It is generated continually and never destroyed, which makes the entropy generated a direct measure of how wasteful a process is. A well-designed process does its job while generating as little entropy as possible.

For a finite amount of heat $Q$ passing from a reservoir at $T_H$ to one at $T_C$, the same argument gives

$$
S_{gen}=-\frac{Q}{T_H}+\frac{Q}{T_C}
$$

$$
\boxed{S_{gen}=Q\left(\frac{1}{T_C}-\frac{1}{T_H}\right)}
$$

which is positive whenever $T_H>T_C$, grows with the temperature gap and vanishes as $T_C\to T_H$, matching the statement in [[SESA1016 T3 - Heat Engines and the Second Law#4. Reversible and irreversible processes|T3]] that heat transfer is reversible only across a vanishing temperature difference.

## 3. The T ds equations

To compute $\Delta S$ for general reversible processes, combine the definition with the first law. Rearrange the definition as

$$
dQ=T\,dS
$$

The first law in differential form is

$$
dU=dQ-dW
$$

Substitute $dQ$:

$$
dU=T\,dS-dW
$$

and the quasi-equilibrium work $dW=p\,dV$:

$$
dU=T\,dS-p\,dV
$$

Rearranging gives the **first $T\,dS$ equation**:

$$
T\,dS=dU+p\,dV
$$

or per unit mass,

$$
\boxed{T\,ds=du+p\,dv}
$$

For the second, differentiate the definition of enthalpy $h=u+pv$:

$$
dh=du+p\,dv+v\,dp
$$

so $du=dh-p\,dv-v\,dp$. Substitute into the first $T\,ds$ equation:

$$
T\,ds=dh-p\,dv-v\,dp+p\,dv
$$

$$
\boxed{T\,ds=dh-v\,dp}
$$

which is the **second $T\,dS$ equation**. These were derived along a reversible path, but they relate properties only. Since entropy is a property, they hold between any two equilibrium states whatever the real process was.

## 4. Entropy change of a perfect gas

Bring in the ideal-gas relations $pv=RT$, $du=c_v\,dT$ and $dh=c_p\,dT$.

In the first $T\,ds$ equation, replace $du$ by $c_v\,dT$ and $p$ by $RT/v$:

$$
T\,ds=c_v\,dT+\frac{RT}{v}\,dv
$$

Divide by $T$:

$$
ds=c_v\frac{dT}{T}+R\frac{dv}{v}
$$

In the second, replace $dh$ by $c_p\,dT$ and $v$ by $RT/p$:

$$
T\,ds=c_p\,dT-\frac{RT}{p}\,dp
$$

$$
ds=c_p\frac{dT}{T}-R\frac{dp}{p}
$$

If $c_v$ and $c_p$ vary with temperature these cannot be integrated without more information. For a perfect gas they are constants, and integrating from state 1 to state 2:

$$
\int_1^2ds=c_v\int_1^2\frac{dT}{T}+R\int_1^2\frac{dv}{v}
$$

$$
\boxed{s_2-s_1=c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1}}
$$

$$
\int_1^2ds=c_p\int_1^2\frac{dT}{T}-R\int_1^2\frac{dp}{p}
$$

$$
\boxed{s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}}
$$

The two forms give the same answer, and only end states enter. Use the one that matches the data. Temperatures must be in kelvin; any consistent unit works for $v$ and $p$ inside the ratios.

Two special cases come straight out. At constant volume the $v$ term vanishes, $\Delta s=c_v\ln(T_2/T_1)$; at constant pressure the $p$ term vanishes, $\Delta s=c_p\ln(T_2/T_1)$. For the same temperature rise the isobaric entropy change is larger, by the factor $\gamma$.

> [!check] The two forms agree
> Constant-pressure heating that doubles $T$ also doubles $v$. The $T$–$p$ form gives $c_p\ln2=1005\times0.693=696.6$ J kg⁻¹ K⁻¹. The $T$–$v$ form gives $c_v\ln2+R\ln2=(718+287)\ln2=696.6$ J kg⁻¹ K⁻¹, since $c_v+R=c_p$.

### Shapes of the processes on a T–s diagram

Along a reversible constant-volume line, $T\,ds=c_v\,dT$, so the slope is

$$
\left(\frac{\partial T}{\partial s}\right)_v=\frac{T}{c_v}
$$

and along a constant-pressure line $T\,ds=c_p\,dT$, so

$$
\left(\frac{\partial T}{\partial s}\right)_p=\frac{T}{c_p}
$$

Both curves are exponentials, $T\propto e^{s/c_v}$ and $T\propto e^{s/c_p}$, steepening as $T$ rises. Since $c_v<c_p$, an isochore is steeper than an isobar through the same point. Isotherms are horizontal and isentropes vertical. These shapes are what make the Otto and Brayton cycles in [[SESA1016 T5 - Ideal Heat Engine Models|T5]] look as they do on a $T$–$s$ diagram.

## 5. Isentropic relations

### Temperature and volume

Set $s_2-s_1=0$ in the $T$–$v$ form:

$$
c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1}=0
$$

$$
\ln\frac{T_2}{T_1}=\frac{R}{c_v}\ln\frac{v_1}{v_2}
$$

$$
\frac{T_2}{T_1}=\left(\frac{v_1}{v_2}\right)^{R/c_v}
$$

From [[SESA1016 T2 - Work, Heat and the First Law#Relations between the gas constants|T2]], $R/c_v=(c_p-c_v)/c_v=\gamma-1$, so

$$
\boxed{\frac{T_2}{T_1}=\left(\frac{v_1}{v_2}\right)^{\gamma-1}}\qquad\text{or}\qquad Tv^{\gamma-1}=\text{const}
$$

### Temperature and pressure

Set $s_2-s_1=0$ in the $T$–$p$ form:

$$
c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}=0
$$

$$
\ln\frac{T_2}{T_1}=\frac{R}{c_p}\ln\frac{p_2}{p_1}
$$

$$
\frac{T_2}{T_1}=\left(\frac{p_2}{p_1}\right)^{R/c_p}
$$

and $R/c_p=(c_p-c_v)/c_p=1-1/\gamma=(\gamma-1)/\gamma$:

$$
\boxed{\frac{T_2}{T_1}=\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}}\qquad\text{or}\qquad Tp^{(1-\gamma)/\gamma}=\text{const}
$$

### Pressure and volume

Both relations give $T_2/T_1$, so equate them:

$$
\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}=\left(\frac{v_1}{v_2}\right)^{\gamma-1}
$$

Raise both sides to the power $\gamma/(\gamma-1)$:

$$
\boxed{\frac{p_2}{p_1}=\left(\frac{v_1}{v_2}\right)^\gamma}\qquad\text{or}\qquad pv^\gamma=\text{const}
$$

These are the same three relations quoted for a reversible adiabatic process in [[SESA1016 T2 - Work, Heat and the First Law#Adiabatic processes|T2]], here derived from entropy. For air, $(\gamma-1)/\gamma=0.2857$, $\gamma-1=0.4$ and $\gamma=1.4$.

> [!warning] Isentropic needs reversible and adiabatic
> Use $pv^\gamma=$ const only when both hold. An isothermal process is reversible but not adiabatic; a throttled leak or a compressor with friction is adiabatic but not reversible. Neither follows the isentropic relations.

---

## Worked examples

### Worked example - which heat transfer is more irreversible

A source at 800 K loses 200 kJ of heat. In process A the heat goes to a sink at 500 K, in process B to a sink at 750 K. Which is more irreversible? (Problem Sheet 3, Q3.5, the sheet's worked solution.)

Both reservoirs stay at fixed temperature, so $\Delta S=Q/T$ for each with $Q$ positive into the reservoir. The source's change is the same in both cases:

$$
\Delta S_{source}=\frac{-200\,000}{800}=-250\ \mathrm{J/K}
$$

Process A:

$$
\Delta S_{sink}=\frac{200\,000}{500}=+400\ \mathrm{J/K},\qquad S_{gen,A}=400-250=150\ \mathrm{J/K}
$$

Process B:

$$
\Delta S_{sink}=\frac{200\,000}{750}=+266.7\ \mathrm{J/K},\qquad S_{gen,B}=266.7-250=16.7\ \mathrm{J/K}
$$

Process A generates nine times as much entropy and is more irreversible, because the heat crosses a larger temperature difference. The same 200 kJ at 500 K could drive a heat engine much less effectively than at 750 K.

### Worked example - heating at constant pressure or constant volume

Air at 20 °C in a piston–cylinder is heated to 100 °C. Find the entropy change per kilogram if the heating is isobaric and if it is isochoric. Then repeat with a fixed heat input of 100 kJ/kg instead of a fixed final temperature (Problem Sheet 3, Q3.6). Take $c_p=1005$, $c_v=718$ J kg⁻¹ K⁻¹.

With $T_1=293.15$ K and $T_2=373.15$ K:

$$
\Delta s_p=c_p\ln\frac{T_2}{T_1}=1005\ln\frac{373.15}{293.15}=243\ \mathrm{J\,kg^{-1}K^{-1}}
$$

$$
\Delta s_v=c_v\ln\frac{T_2}{T_1}=718\ln\frac{373.15}{293.15}=173\ \mathrm{J\,kg^{-1}K^{-1}}
$$

With $q=100$ kJ/kg fixed, the final temperatures differ. At constant pressure $q=c_p\Delta T$, so $T_2=293.15+100\,000/1005=392.65$ K and

$$
\Delta s_p=1005\ln\frac{392.65}{293.15}=294\ \mathrm{J\,kg^{-1}K^{-1}}
$$

At constant volume $q=c_v\Delta T$, so $T_2=293.15+100\,000/718=432.43$ K and

$$
\Delta s_v=718\ln\frac{432.43}{293.15}=279\ \mathrm{J\,kg^{-1}K^{-1}}
$$

For the same heat, constant-volume heating reaches a higher temperature, so each joule arrives at a higher average temperature and carries in less entropy.

### Worked example - isothermal expansion

10 kg of air expands isothermally and reversibly at 300 K from 5 bar to 1 bar, taking in $Q=1386$ kJ (Problem Sheet 2, Q2.4). Find $\Delta S$ two ways.

From the isothermal definition:

$$
\Delta S=\frac{Q}{T}=\frac{1\,385\,700}{300}=4619\ \mathrm{J/K}
$$

From the $T$–$p$ form with $T_2=T_1$:

$$
\Delta S=m\left(c_p\ln1-R\ln\frac{p_2}{p_1}\right)=10\times287\times\ln5=4619\ \mathrm{J/K}
$$

The gas's entropy rises because it takes in heat, not because anything irreversible happens: if the bath is at 300 K too, the bath loses exactly 4619 J/K and $S_{gen}=0$.

### Worked example - adiabatic but not isentropic

Air in a rigid insulated tank is held in one half by a partition, with vacuum in the other half. The partition bursts and the air fills the whole tank. Find $\Delta s$ (suggested example; compare Problem Sheet 1, Q1.4).

No heat crosses the insulated wall and no work is done (nothing moves at the boundary), so $\Delta U=0$ and the temperature of the ideal gas is unchanged. The volume doubles. The real process is violently non-equilibrium, but $\Delta s$ depends only on the end states:

$$
\Delta s=c_v\ln1+R\ln2=287\times0.693=199\ \mathrm{J\,kg^{-1}K^{-1}}
$$

The process is adiabatic, $Q=0$, so all of this is generated entropy: $s_{gen}=199$ J kg⁻¹ K⁻¹. This is the unrestrained expansion of [[SESA1016 T3 - Heat Engines and the Second Law#4. Reversible and irreversible processes|T3]], quantified.

### Worked example - isentropic compression of air

Air at 300 K and 1 bar is compressed isentropically to 8 bar. Find the exit temperature, and compare with a real compressor that delivers the air at 600 K (suggested example).

$$
T_{2s}=T_1\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}=300\times8^{0.2857}=543.4\ \mathrm K
$$

The real compressor's exit at the same pressure is hotter. Its entropy rise is

$$
\Delta s=c_p\ln\frac{600}{300}-R\ln8=696.6-596.8=99.8\ \mathrm{J\,kg^{-1}K^{-1}}
$$

positive, as it must be for an adiabatic process with friction. In propulsion this comparison becomes the isentropic efficiency ([[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]).

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T3 - Heat Engines and the Second Law]] · Next: [[SESA1016 T5 - Ideal Heat Engine Models]]
- Concepts: [[Entropy Generation]] · [[Isentropic Ideal-gas Relations]] · [[Internal Energy and Enthalpy]]
- Worked sheet: [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]] (Q3.5–Q3.6) · Formula list: [[SESA1016 Formula Sheet]]
- Continues in Propulsion: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · [[Entropy Change of a Perfect Gas]] · [[Isentropic Efficiency]]

## Sources

- `Chapter 4.pdf`: lecture notes Chapter 4, Entropy, §§4.1–4.5, Figs 4.1–4.6.
- `Problem Sheet 03 - Heat Engines and Entropy.pdf`: Q3.5–Q3.6, printed answers and the worked solution to Q3.5.
- No transcript: the Entropy lectures were not recorded, so this note is written from the lecture notes. The $T$–$s$ slopes in §4 are added here because [[SESA1016 T5 - Ideal Heat Engine Models|T5]] draws its cycles on $T$–$s$ diagrams.

## Self-study tasks

The weekly problem sheet is the set work; none of it can be tied to a transcript line.

### Core

- [ ] Q3.5, two heat transfers from an 800 K source (Problem Sheet 3, worked solution). Answer: A, 150 against 16.7 J/K. → [[#Worked example - which heat transfer is more irreversible]]
- [ ] Q3.6, entropy change for isobaric and isochoric heating, fixed $\Delta T$ and fixed $q$. Targets 243, 173, 294, 279 J kg⁻¹ K⁻¹. → [[#Worked example - heating at constant pressure or constant volume]]
- [ ] Derive both $T\,ds$ equations and the two perfect-gas entropy formulas (Chapter 4, §4.4). → [[#3. The T ds equations]] · [[#4. Entropy change of a perfect gas]]

### Further practice

- [ ] Derive the three isentropic relations from $\Delta s=0$ (Chapter 4, §4.5). → [[#5. Isentropic relations]]
- [ ] Check that $\sum\Delta s=0$ around the rectangular cycle of Problem Sheet 3, Q3.1, as it must for any cycle (suggested, not lecturer-set). → [[#4. Entropy change of a perfect gas]]
- [ ] Find the entropy generated when 1 kg of air expands freely into a vacuum to three times its volume (suggested, not lecturer-set; target 315 J kg⁻¹ K⁻¹). → [[#Worked example - adiabatic but not isentropic]]
