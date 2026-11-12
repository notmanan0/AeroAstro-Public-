---
title: "SESA1016 T2 - Work, Heat and the First Law"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 2
tags: [sesa1016, first-law, heat, work, enthalpy]
aliases: ["Work and Heat"]
date: 2026-09-25
status: written-ahead
coverage: "Chapter 2 §§2.1–2.3 from the lecture notes; no recording survives for the Work and Heat lectures (28 Jan – 19 Feb 2025), so there is no transcript to confirm the scope"
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T1 - Thermodynamic Systems, Properties and State]]"]
next_topics: ["[[SESA1016 T3 - Heat Engines and the Second Law]]"]
key_concepts: ["[[Boundary Work]]", "[[Internal Energy and Enthalpy]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 02 - Work and Heat Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 02 - Work and Heat.pdf"]
---

# SESA1016 T2 - Work, Heat and the First Law

> [!abstract] Summary
> Energy is conserved, so for a closed system in equilibrium the change in internal energy equals the heat put in minus the work taken out, $\Delta U=Q-W$. For a quasi-equilibrium piston process the work is $W=\int p\,dV$, the area under the path on a $p$–$V$ diagram, so it depends on the path while $\Delta U$ does not. For a perfect gas $\Delta U=mc_v\Delta T$ and $\Delta H=mc_p\Delta T$ for any process, which with the constraint of each process (constant $V$, $p$ or $T$, or no heat) gives the work and heat in closed form.

> [!summary]- Exam use: quick path
> - **Use it when:** a fixed mass of gas is heated, cooled, compressed or expanded through one or more named processes and you need $W$, $Q$ or $\Delta U$ for each leg.
> - **Assumptions:** closed system, quasi-equilibrium (a single pressure throughout), frictionless piston, perfect gas ($c_v$, $c_p$ constant), $pV^\gamma=$ const only for a reversible adiabatic process.
> - **Method:** 1. Sketch the path on a $p$–$V$ diagram and number the states. 2. Find every end state with $pV=mRT$ and the process constraint. 3. $W=\int p\,dV$ for each leg (zero, $p\Delta V$, $mRT\ln(V_2/V_1)$ or $(p_1V_1-p_2V_2)/(\gamma-1)$). 4. $\Delta U=mc_v\Delta T$. 5. $Q=\Delta U+W$.
> - **Common mistakes:** the sign of $W$ (work done by the gas is positive, so compression is negative); assuming an isothermal process needs no heat.
> - **Practise:** [[#Worked example - heavy piston lifted by heating]] · [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]] Q2.4–Q2.5

The gas in a closed system stores energy in the motion and structure of its molecules. That microscopic energy is the internal energy $U$, and for an ideal gas it depends only on temperature. The gas has no bulk kinetic or potential energy worth tracking: any swirling motion would mean it was not in equilibrium, and once the swirl dies away its energy has become internal energy anyway.

There are only two ways to change $U$ from outside. Heat flows in or out through the walls when they touch something hotter or colder. Work is any other energy transfer: a piston pushed in, a paddle turned, a current through a resistor. A piston that moves while gas pushes on it transfers energy as work equal to force times distance, and since force is pressure times area and area times distance is volume change, the work is $\int p\,dV$.

The first law ties the three together. Once the constraint on a process is known (rigid walls, a constant load on the piston, contact with a large bath, or perfect insulation), the work integral can be evaluated and the heat follows from the first law. The cycles of [[SESA1016 T3 - Heat Engines and the Second Law|T3]]–[[SESA1016 T5 - Ideal Heat Engine Models|T5]] are built from these four cases.

---

## 1. The first law for a closed system

Energy cannot be created or destroyed, only converted. For a closed system in equilibrium the only stored energy that changes is the internal energy $U$, so any energy that enters and does not leave must show up as a rise in $U$:

$$
\Delta U=E_{in}-E_{out}
$$

Energy crosses the boundary as heat or as work, and the historical heat-engine sign convention is used, in which heat in and work out are the useful quantities:

- $Q$ is the net heat transferred **into** the system, $Q=Q_{in}-Q_{out}$;
- $W$ is the net work done **by** the system, $W=W_{out}-W_{in}$.

Substituting $E_{in}-E_{out}=Q-W$ gives the first law for a closed system:

$$
\boxed{\Delta U=Q-W}
$$

Dividing by the mass gives the specific form, with $u$, $q$ and $w$ in J/kg:

$$
\Delta u=q-w
$$

The signs carry the physics. Pushing a piston in is work done on the gas, so $W<0$ and, with no heat loss, $\Delta U>0$: the gas warms. A gas that expands against a piston does positive work, and unless heat is supplied its internal energy falls.

$\Delta U$ depends only on the end states, because $U$ is a property. $Q$ and $W$ separately depend on the path, which is the content of Problem Sheet 2, Q2.3 and of [[#Worked example - three paths between the same two states]].

## 2. Pressure–volume work

### The work integral

Mechanical work is force times displacement, $W=F\Delta x$. Gas at pressure $p$ under a piston of area $A$ pushes with force

$$
F=pA
$$

If the piston moves out by a small distance $dx$, the work done by the gas is

$$
dW=F\,dx=pA\,dx
$$

and since the volume swept is $dV=A\,dx$,

$$
dW=p\,dV
$$

Adding up the small contributions from state 1 to state 2:

$$
\boxed{W=\int_{V_1}^{V_2}p\,dV}
$$

Two assumptions hide in this. First, there must be a single pressure acting both throughout the gas and on the piston face, which is true only if the process is quasi-equilibrium. A piston pulled out very fast would leave low pressure just under it and higher pressure further away, and the integral would have no meaning; in practice that matters only when the piston speed approaches the speed of sound. Second, all the work reaches the piston rod only if the piston is frictionless; friction turns part of it into heat in the wall. The result holds for any closed system in a quasi-equilibrium process, not only a piston.

### Work as area, and why it depends on the path

An integral is an area, so the work is the area under the process curve on a $p$–$V$ diagram. Two different curves between the same end states enclose different areas and so do different amounts of work. Work is therefore a path function: the end states alone do not fix it.

The direction matters too. Moving left to right (expansion, $dV>0$) gives positive work; reversing the same path gives the same magnitude with a negative sign. For an isothermal path from 2 back to 1, for example,

$$
W_{2\to1}=mRT\int_{V_2}^{V_1}\frac{dV}{V}=mRT\ln\frac{V_1}{V_2}=-mRT\ln\frac{V_2}{V_1}=-W_{1\to2}
$$

![[tf_processes_pv.png|900]]

### Constant pressure (isobaric)

A frictionless piston carrying a fixed load, with the atmosphere above, keeps the gas pressure fixed at $p=p_{atm}+F_L/A$ (see [[SESA1016 T1 - Thermodynamic Systems, Properties and State#Pressure set by a free piston|T1]]). With $p=p_1$ constant it comes out of the integral:

$$
W=p_1\int_{V_1}^{V_2}dV
$$

$$
W=p_1(V_2-V_1)
$$

the area of the rectangle under the horizontal line. For an ideal gas, $p_1V_2=mRT_2$ and $p_1V_1=mRT_1$, so the same result can be written

$$
W=mR(T_2-T_1)
$$

### Constant volume (isochoric)

A rigid tank, or a piston held in place, keeps $V$ fixed while heat changes $p$ and $T$. Then $dV=0$ at every step, so

$$
W=\int p\,dV=0
$$

Three views agree: the force is finite but the displacement is zero; the integrand is multiplied by $dV=0$; and a vertical line on the $p$–$V$ diagram has no area under it.

### Constant temperature (isothermal)

A cylinder in good thermal contact with a large bath, compressed or expanded slowly, stays at the bath temperature because any small temperature change drives heat to or from the bath. Now $p$ and $V$ both change, so $p(V)$ is needed. For an ideal gas at fixed $T$:

$$
p=\frac{mRT}{V}
$$

Substitute into the work integral:

$$
W=\int_{V_1}^{V_2}\frac{mRT}{V}\,dV
$$

$m$, $R$ and $T$ are all constant, so they come out:

$$
W=mRT\int_{V_1}^{V_2}\frac{dV}{V}
$$

$$
W=mRT\left(\ln V_2-\ln V_1\right)
$$

$$
\boxed{W=mRT\ln\frac{V_2}{V_1}}
$$

At constant $T$, $p_1V_1=p_2V_2$, so $V_2/V_1=p_1/p_2$ and equally $W=mRT\ln(p_1/p_2)$. Since $mRT=p_1V_1$, the work can also be written $p_1V_1\ln(V_2/V_1)$ without knowing $m$.

## 3. Heat, internal energy and the specific heats

### Constant-volume heating and the specific heat at constant volume

At constant volume $W=0$, so the first law reduces to

$$
Q=\Delta U
$$

To use this, $\Delta U$ must be linked to something measurable. That is the job of the **specific heat at constant volume**,

$$
c_v\equiv\left(\frac{\partial u}{\partial T}\right)_v
$$

For a real substance $u$ depends on two properties, hence the partial derivative. For an ideal gas $u$ depends on $T$ alone, so

$$
c_v=\frac{du}{dT}
$$

$c_v$ varies a little with temperature, mainly at high temperature. A gas whose $c_v$ is taken as constant is a **perfect gas**, the model used throughout this module. Then the derivative becomes a ratio of finite changes:

$$
c_v=\frac{\Delta u}{\Delta T}
$$

$$
\boxed{\Delta u=c_v\Delta T,\qquad \Delta U=mc_v\Delta T}
$$

No process was assumed in getting here, only that $u=u(T)$ and $c_v$ is constant. So $\Delta U=mc_v\Delta T$ holds for every process of a perfect gas, whatever the name of the specific heat suggests. What is special about constant volume is only that the heat equals $\Delta U$:

$$
Q=\Delta U=mc_v\Delta T\qquad\text{(constant volume)}
$$

### Constant-pressure heating

When gas is heated at constant pressure, the heat does two jobs: it raises the internal energy and it pushes the piston out. From the first law, with $W=p\Delta V$:

$$
Q=\Delta U+W
$$

$$
Q=\Delta U+p\Delta V
$$

$$
Q=mc_v\Delta T+p\Delta V
$$

Since $p\Delta V>0$ for heating at constant pressure, more heat is needed for the same temperature rise than at constant volume. The combination $\Delta U+p\Delta V$ appears so often that it gets its own property.

### Enthalpy and the specific heat at constant pressure

**Enthalpy** is defined as

$$
H=U+pV,\qquad h=u+pv
$$

It is a property because $U$, $p$ and $V$ are. The **specific heat at constant pressure** is

$$
c_p\equiv\left(\frac{\partial h}{\partial T}\right)_p
$$

For an ideal gas $h=u+pv=u+RT$ depends on $T$ only, so $c_p=dh/dT$; for a perfect gas $c_p$ is constant and

$$
\boxed{\Delta h=c_p\Delta T,\qquad \Delta H=mc_p\Delta T}
$$

again for any process. For constant-pressure heating, a finite change in $h=u+pv$ is

$$
\Delta h=\Delta u+\Delta(pv)
$$

and at constant pressure $\Delta(pv)=p\Delta v$, so

$$
\Delta h=\Delta u+p\Delta v
$$

which is exactly the per-kilogram heat $q=\Delta u+p\Delta v$ found above. Therefore

$$
\boxed{Q=\Delta H=mc_p\Delta T}\qquad\text{(constant pressure)}
$$

The enthalpy form avoids having to find $\Delta V$ first.

### Relations between the gas constants

For an ideal gas $h=u+pv$ and $pv=RT$, so

$$
h=u+RT
$$

Differentiate with respect to $T$:

$$
\frac{dh}{dT}=\frac{du}{dT}+R
$$

$$
\boxed{c_p=c_v+R}
$$

which confirms that $c_p>c_v$: the extra $R$ per kelvin is the work done pushing the piston, since $p\Delta v=R\Delta T$ at constant pressure. Define the **ratio of specific heats**

$$
\gamma=\frac{c_p}{c_v}
$$

Then only two of $R$, $c_v$, $c_p$, $\gamma$ are independent. Divide $c_p-c_v=R$ by $c_v$:

$$
\gamma-1=\frac{R}{c_v}
$$

$$
c_v=\frac{R}{\gamma-1}
$$

and multiply by $\gamma$:

$$
c_p=\gamma c_v=\frac{\gamma R}{\gamma-1}
$$

> [!check] Air
> With $R=287$ J kg⁻¹ K⁻¹ and $\gamma=1.4$: $c_v=287/0.4=717.5$ and $c_p=1.4\times717.5=1004.5$ J kg⁻¹ K⁻¹, matching the tabulated 718 and 1005. Heating 1 kg of air from 300 to 400 K takes 71.8 kJ in a rigid tank and 100.5 kJ under a free piston; the 28.7 kJ difference is $R\Delta T$, the work done lifting the piston.

### Isothermal heat transfer

It is tempting to think that no temperature change means no heat. But $T$ constant means $\Delta U=0$ for an ideal gas, and the first law then gives

$$
0=Q-W
$$

$$
Q=W=mRT\ln\frac{V_2}{V_1}
$$

An isothermal expansion needs heat equal to the work done, supplied by the bath; an isothermal compression must reject heat equal to the work put in.

### Adiabatic processes

An **adiabatic** process has $Q=0$. That needs good insulation, or a process fast enough that there is no time for heat to flow; real compressors, turbines and engine strokes are close to adiabatic for the second reason. The first law becomes

$$
\Delta U=-W
$$

so any work done by the gas comes out of its internal energy and it cools; work done on it heats it.

To evaluate $W=\int p\,dV$ the path $p(V)$ is needed. The result for a reversible adiabatic process of a perfect gas is usually justified from entropy ([[SESA1016 T4 - Entropy and Isentropic Relations|T4]]); it can also be derived here from the first law alone. For a small step of a quasi-equilibrium adiabatic process, $dU=-p\,dV$, and with $dU=mc_v\,dT$:

$$
mc_v\,dT=-p\,dV
$$

Replace $p$ using $p=mRT/V$:

$$
mc_v\,dT=-\frac{mRT}{V}\,dV
$$

Divide by $mc_vT$:

$$
\frac{dT}{T}=-\frac{R}{c_v}\frac{dV}{V}
$$

and $R/c_v=\gamma-1$:

$$
\frac{dT}{T}=-(\gamma-1)\frac{dV}{V}
$$

Integrate from state 1 to state 2:

$$
\ln\frac{T_2}{T_1}=-(\gamma-1)\ln\frac{V_2}{V_1}
$$

$$
\boxed{TV^{\gamma-1}=\text{const}}
$$

Substitute $T=pV/(mR)$; the constant $mR$ is absorbed into the constant:

$$
\frac{pV}{mR}V^{\gamma-1}=\text{const}
$$

$$
\boxed{pV^\gamma=\text{const}}
$$

Finally substitute $V=mRT/p$ into $pV^\gamma=$ const:

$$
p\left(\frac{mRT}{p}\right)^\gamma=\text{const}
$$

$$
p^{1-\gamma}T^\gamma=\text{const}
$$

and raising to the power $1/\gamma$,

$$
\boxed{Tp^{(1-\gamma)/\gamma}=\text{const}}
$$

The quasi-equilibrium assumption entered when $dW=p\,dV$ was used with the gas pressure, and no friction was allowed: together these make the process reversible. A real adiabatic process with friction does not follow $pV^\gamma=$ const.

The adiabatic work then follows two ways. From the first law:

$$
W=-\Delta U=mc_v(T_1-T_2)
$$

Using $c_v=R/(\gamma-1)$ and $mRT=pV$:

$$
W=\frac{mR(T_1-T_2)}{\gamma-1}
$$

$$
\boxed{W=\frac{p_1V_1-p_2V_2}{\gamma-1}}
$$

Or directly from the integral, with $p=p_1V_1^\gamma V^{-\gamma}$:

$$
W=p_1V_1^\gamma\int_{V_1}^{V_2}V^{-\gamma}\,dV
$$

$$
W=p_1V_1^\gamma\,\frac{V_2^{1-\gamma}-V_1^{1-\gamma}}{1-\gamma}
$$

$$
W=\frac{p_2V_2-p_1V_1}{1-\gamma}
$$

using $p_1V_1^\gamma V_2^{1-\gamma}=p_2V_2^\gamma V_2^{1-\gamma}=p_2V_2$. This is the same result.

On a $p$–$V$ diagram the adiabat $pV^\gamma=$ const is steeper than the isotherm $pV=$ const through the same point, because $\gamma>1$: in an adiabatic expansion the gas cools as well as expanding, so its pressure falls faster.

> [!warning] Three words that are easy to mix up
> Adiabatic means no heat crosses the boundary, not constant temperature: an adiabatic compression heats the gas. Isothermal means constant temperature, and it usually needs heat transfer to stay that way. Isochoric means constant volume, and $p$ and $T$ both change.

## 4. Summary of the four processes

For a perfect gas in a quasi-equilibrium closed process:

| Process | Constraint | $W=\int p\,dV$ | $\Delta U$ | $Q=\Delta U+W$ |
|---|---|---|---|---|
| isochoric | $V$ const, $p/T$ const | $0$ | $mc_v\Delta T$ | $mc_v\Delta T$ |
| isobaric | $p$ const, $V/T$ const | $p(V_2-V_1)=mR\Delta T$ | $mc_v\Delta T$ | $mc_p\Delta T$ |
| isothermal | $T$ const, $pV$ const | $mRT\ln(V_2/V_1)$ | $0$ | $mRT\ln(V_2/V_1)$ |
| reversible adiabatic | $pV^\gamma$ const | $(p_1V_1-p_2V_2)/(\gamma-1)$ | $mc_v\Delta T$ | $0$ |

A multi-stage process is handled one leg at a time: find each end state, then $W_i$, $\Delta U_i$ and $Q_i$ for each leg, then add. Around a closed cycle the gas returns to its starting state, so $\Delta U_{cycle}=0$ and the net heat in equals the net work out; that is the starting point for [[SESA1016 T3 - Heat Engines and the Second Law|T3]].

---

## Worked examples

### Worked example - signs in the first law

3 kJ of work is done on a gas by compressing it in a cylinder. The pressure rises from 1 to 2 bar and the temperature to 40 °C, and the gas loses 0.1 kJ of heat to the surroundings. Find $\Delta U$ (Chapter 2, Example 2.1).

Work done on the gas is negative work by the gas, $W=-3$ kJ. Heat lost is negative heat in, $Q=-0.1$ kJ. Then

$$
\Delta U=Q-W=(-0.1)-(-3)=2.9\ \mathrm{kJ}
$$

The pressures and temperature are not needed: the first law needs only the energy transfers.

### Worked example - three paths between the same two states

A gas goes from $p_1=2$ bar, $V_1=0.1$ m³ to $p_2=1$ bar, $V_2=0.2$ m³. Since $p_1V_1=p_2V_2$ the two states are at the same temperature, so $\Delta U=0$ for an ideal gas whichever path is taken. Compare three paths (a suggested example on §2.2).

![[tf_work_paths.png|900]]

Path A, isothermal:

$$
W_A=p_1V_1\ln\frac{V_2}{V_1}=2\times10^5\times0.1\times\ln2=13.9\ \mathrm{kJ}
$$

Path B, expand at 2 bar to 0.2 m³, then cool at constant volume to 1 bar. Only the first leg does work:

$$
W_B=p_1(V_2-V_1)=2\times10^5\times0.1=20.0\ \mathrm{kJ}
$$

Path C, cool at constant volume to 1 bar, then expand at 1 bar:

$$
W_C=p_2(V_2-V_1)=1\times10^5\times0.1=10.0\ \mathrm{kJ}
$$

In each case $Q=\Delta U+W=W$, so the heat supplied is also 13.9, 20.0 or 10.0 kJ. Same end states, same $\Delta U$, three different values of $Q$ and $W$.

### Worked example - heavy piston lifted by heating

A vertical cylinder of area 0.1 m² has a piston of mass 203.9 kg resting on a support, with 0.05 m³ of gas below at 1 bar and 26.85 °C (300 K); the atmosphere above is at 1 bar. For the gas, $R=0.290$ and $c_v=0.725$ kJ kg⁻¹ K⁻¹. Heat is added until the piston has risen 200 mm. Find the mass of gas, the pressures, and the heat and work for each stage (Problem Sheet 2, Q2.1, the tutorial problem).

![[tf_piston_support_pv.png|900]]

The process has two legs. While the piston sits on the support, the volume is fixed and heating raises the pressure (1→2, vertical on the $p$–$V$ diagram). Once the gas pressure can hold the piston up, further heating lifts it at constant pressure (2→3, horizontal).

Mass from state 1:

$$
m=\frac{p_1V_1}{RT_1}=\frac{10^5\times0.05}{290\times300}=0.05747\ \mathrm{kg}
$$

The piston just lifts when the upward force from the gas balances the atmosphere and the piston's weight:

$$
p_2A=p_{atm}A+m_pg
$$

$$
p_2=p_{atm}+\frac{m_pg}{A}=10^5+\frac{203.9\times9.81}{0.1}=1.200\times10^5\ \mathrm{Pa}
$$

and the same load acts while the piston rises, so $p_3=p_2=1.2$ bar. At constant volume $T_2=T_1p_2/p_1=360$ K.

Stage 1→2: no movement, so $W_{12}=0$ and

$$
Q_{12}=\Delta U_{12}=mc_v(T_2-T_1)=0.05747\times725\times60=2.50\ \mathrm{kJ}
$$

Stage 2→3: the piston rises 0.2 m, so $V_3=0.05+0.1\times0.2=0.07$ m³. At constant pressure $T_3=T_2V_3/V_2=360\times1.4=504$ K. Then

$$
W_{23}=p_2(V_3-V_2)=1.2\times10^5\times0.02=2.40\ \mathrm{kJ}
$$

$$
\Delta U_{23}=mc_v(T_3-T_2)=0.05747\times725\times144=6.00\ \mathrm{kJ}
$$

$$
Q_{23}=\Delta U_{23}+W_{23}=8.40\ \mathrm{kJ}
$$

> [!check] Constant-pressure shortcut
> With $c_p=c_v+R=1.015$ kJ kg⁻¹ K⁻¹, $Q_{23}=mc_p\Delta T=0.05747\times1015\times144=8.40$ kJ, the same answer without computing $W$ first.

### Worked example - isothermal expansion then adiabatic compression

0.5 kg of air at 300 K and 100 kPa expands isothermally until its volume doubles, then is compressed reversibly and adiabatically back to the original volume. Take $R=287$ J kg⁻¹ K⁻¹ and $\gamma=1.4$ (Problem Sheet 2, Q2.5).

Isothermal leg: $T_2=300$ K and $p_2=p_1V_1/V_2=50$ kPa.

$$
W_{12}=mRT\ln2=0.5\times287\times300\times\ln2=29.84\ \mathrm{kJ}
$$

and $Q_{12}=W_{12}=29.84$ kJ, since $\Delta U_{12}=0$.

Adiabatic leg, $V_2/V_3=2$:

$$
T_3=T_2\left(\frac{V_2}{V_3}\right)^{\gamma-1}=300\times2^{0.4}=395.9\ \mathrm K
$$

$$
p_3=p_2\left(\frac{V_2}{V_3}\right)^\gamma=50\times2^{1.4}=132.0\ \mathrm{kPa}
$$

$$
W_{23}=-\Delta U_{23}=mc_v(T_2-T_3)=0.5\times717.5\times(300-395.9)=-34.4\ \mathrm{kJ}
$$

with $Q_{23}=0$.

> [!check] Same work from the pressure–volume form
> $V_1=mRT_1/p_1=0.4305$ m³ and $V_2=0.861$ m³. Then $(p_2V_2-p_3V_3)/(\gamma-1)=(50\,000\times0.861-131\,950\times0.4305)/0.4=-34.4$ kJ.

The gas ends at the original volume but at a higher pressure and temperature than it started: more work went in during compression (34.4 kJ) than came out during expansion (29.8 kJ), and the difference is now internal energy.

---

## Links

- Parent: [[SESA1016 Thermofluids Hub]] · Previous: [[SESA1016 T1 - Thermodynamic Systems, Properties and State]] · Next: [[SESA1016 T3 - Heat Engines and the Second Law]]
- Concepts: [[Boundary Work]] · [[Internal Energy and Enthalpy]] · [[Thermodynamic State and Process]]
- Worked sheet: [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]] · Formula list: [[SESA1016 Formula Sheet]]
- Used again in: [[SESA1016 T4 - Entropy and Isentropic Relations|T4]] (isentropic relations from entropy) · [[SESA1016 T5 - Ideal Heat Engine Models|T5]] (each cycle leg) · [[SESA1016 T13 - Conservation of Energy and Propulsion|T13]] (enthalpy in the steady-flow energy equation) · [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]

## Sources

- `Chapter 2.pdf`: lecture notes Chapter 2, Work and heat, §§2.1–2.3, Example 2.1, Figs 2.1–2.12.
- `Problem Sheet 02 - Work and Heat.pdf`: Q2.1–Q2.5 with printed answers and the worked solution to Q2.2.
- No transcript: the recordings between Lecture 1 (27 Jan) and 20 Feb 2025 were not downloaded, so this note is written from the lecture notes.

## Self-study tasks

The weekly problem sheet is the set work. None of these tasks can be tied to a transcript line because the lectures were not recorded.

### Core

- [ ] Q2.1, heavy piston on a support: sketches, $p$–$V$ path, $m$, $p_2$, $Q_{12}$, $W_{23}$, $Q_{23}$ (Problem Sheet 2, the tutorial problem). Targets 0.0575 kg, 1.2 bar, 2.5 kJ, 2.4 kJ, 8.4 kJ. → [[#Worked example - heavy piston lifted by heating]]
- [ ] Q2.2, ratio of adiabatic compression work to constant-pressure expansion work (Problem Sheet 2, worked solution). Target $-0.256$ for $\gamma=1.4$, $r=6$. → [[#Adiabatic processes]] · [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]]
- [ ] Q2.3, two expansions between the same states. Targets $\Delta U=-4$ kJ, $W_B=13$ kJ. → [[#1. The first law for a closed system]] · [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]]
- [ ] Q2.4, isothermal expansion then isochoric heating of 10 kg of air. Targets 1386 kJ, 0, 1386 kJ; 0, 8616 kJ, 8616 kJ. → [[#4. Summary of the four processes]] · [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]]
- [ ] Q2.5, isothermal expansion then adiabatic compression. → [[#Worked example - isothermal expansion then adiabatic compression]]

### Further practice

- [ ] Derive $TV^{\gamma-1}=$ const, $pV^\gamma=$ const and $Tp^{(1-\gamma)/\gamma}=$ const from the first law for a reversible adiabatic process (suggested, not lecturer-set). → [[#Adiabatic processes]]
- [ ] Show that $c_p-c_v=R$ and derive $c_v=R/(\gamma-1)$ and $c_p=\gamma R/(\gamma-1)$ (suggested, not lecturer-set). → [[#Relations between the gas constants]]
- [ ] Repeat the three-path example for an adiabatic path from state 1 to the same final volume and explain why it cannot reach state 2 (suggested, not lecturer-set). → [[#Worked example - three paths between the same two states]]
