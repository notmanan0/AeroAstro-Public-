---
title: "SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 2
tags:
  - sesa2023
  - thermodynamics
  - sfee
  - entropy
  - isentropic-efficiency
aliases: ["Propulsion thermodynamics", "SFEE for a turbojet", "SESA2023 Week 2"]
date: 2026-09-24
status: lectured
coverage: "Week 2 (Lectures 4–6)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA1016 T4 - Entropy and Isentropic Relations]]"]
next_topics: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
key_concepts: ["[[Two-Property Rule and Perfect Gas Model]]", "[[Gas Mixtures and Dalton's Law]]", "[[Steady Flow Energy Equation]]", "[[Entropy Change of a Perfect Gas]]", "[[Isentropic Efficiency]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 2 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-03.txt", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-06.txt", "02 - Sources/Tutorial Sheets/Additional question on thermodynamics.pdf"]
---

# SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency

> [!abstract] Summary
> Week 2 refreshes Part 1 thermodynamics with a propulsion slant ("nothing new", 3 Feb, ll. 29–30): two independent intensive properties fix the state of a simple gas, a perfect gas turns every enthalpy change into $c_p\Delta T$, and mixtures use mass fractions for specific properties and mole fractions for partial pressures. The steady flow energy equation, applied to each component of a turbojet in turn, gives the station-by-station method used for every engine in the module, and isentropic efficiency measures how far real compressors and turbines depart from the ideal.

> [!summary]- Exam use: quick path
> - **Use it when:** a component (diffuser, compressor, burner, turbine, nozzle) has known inlet conditions and you need an exit temperature, pressure, work or heat; or a mixture's composition or properties are asked for.
> - **Assumptions:** steady flow; perfect gas ($c_p$ constant, so pick one suited to the temperature range); potential energy neglected; KE neglected except at the intake entry and nozzle exit; adiabatic compressors and turbines; turbine work = compressor work.
> - **Method:** 1. Number the stations 1–6 and list what is known. 2. Write $q-w_x=\Delta h+\Delta\tfrac12V^2$ for the component and cross out the zero terms. 3. Isentropic exit from $T_{2s}/T_1=(p_2/p_1)^{(\gamma-1)/\gamma}$. 4. Real exit from $\eta_c$ or $\eta_t$. 5. Work or heat from $c_p\Delta T$.
> - **Common mistakes:** swapping the compressor and turbine efficiency definitions (check: the real exit is *hotter* than the isentropic one in both); weighting a mean molar mass by mass fractions instead of mole fractions.
> - **Practise:** [[#Worked example – turbine with isentropic efficiency]] · [[SESA2023 Problem Sheet 2 Solutions]] Q2.2–Q2.3

Follow one kilogram of air through a turbojet.

Its pressure and temperature fix its state: every other property, density, enthalpy and entropy, follows from the equations of state; that is the two-property rule. Each component changes its energy in one way: the burner adds heat, the compressor adds work, the turbine removes work, and the diffuser and nozzle trade enthalpy for speed. The steady flow energy equation, written once per component, accounts for each of these. For a perfect gas enthalpy is $c_pT$, so every energy term can be written as a temperature difference.

In a real machine, friction and turbulence turn some of the work into heat inside the gas, so the air leaves a real compressor or turbine hotter and at higher entropy than an ideal one; the compressor then needs more work and the turbine delivers less. A gas turbine works at all because lines of constant pressure fan apart on a $T$–$s$ diagram as the temperature rises, so expanding hot gas through a pressure ratio releases more work than compressing cold gas through the same ratio absorbs, and there is work left over.

---

## 1. Fundamentals (Lecture 4)

### Equilibrium, state and properties

- Thermodynamic equilibrium needs thermal (uniform $T$), mechanical (no net force), phase (no spontaneous phase change) and chemical (no change of composition) equilibrium, on a macroscopic scale (3 Feb, ll. 32–44). Chemical equilibrium does not mean reactions stop, only that the composition stops changing; this returns in [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium|W05]].
- **Zeroth Law**: if A and B are each in thermal equilibrium with C, they are in thermal equilibrium with each other.
- A state is the set of values of the properties; a process is the path between two states (3 Feb, ll. 51–64, 123–130).
- Property types:
  - intensive (independent of amount): $T$, $p$;
  - extensive (proportional to amount): $U$, $H$, $S$, $V$;
  - specific (per kilogram, lower case): $u$, $h$, $s$, $v$. In this course "specific" always means per unit mass, so specific properties behave as intensive ones (3 Feb, ll. 111–122).
- $c_p$ is sometimes written $C_p$. Always check the units.

### Two-property rule (state postulate)

> The state of a simple compressible system is completely specified by two independent intensive properties (notes §2.2.3).

"Simple" means no body forces, surface tension, magnetic or electric effects (3 Feb, l. 70). "Independent" is the catch:

- For an ideal gas $u=u(T)$ and $h=h(T)$, so $(T,h)$ or $(T,u)$ do not fix the state: knowing $T$ already tells you $h$.
- During a phase change (evaporating rocket propellant), $p$ and $T$ are tied by the saturation curve, so $(p,T)$ are not independent either.

### First Law and model processes

$$
\Delta U = Q-W
$$

with $Q>0$ for heat added to the system and $W>0$ for work done by the system (6 Feb, ll. 56–68). $\Delta U$ depends only on the end states; $Q$ and $W$ depend on the path (3 Feb, ll. 142–145).

| Process | Constant | Consequence |
|---|---|---|
| isothermal | $T$ | $\Delta u=0$ for an ideal gas; $pV$ = const |
| isobaric | $p$ | horizontal line on $p$–$V$; the burner model |
| isochoric | $V$ | vertical line on $p$–$V$; no displacement work |
| adiabatic | $Q=0$ | for a reversible adiabatic perfect gas, $pV^\gamma$ = const, steeper than the isotherm |
| isentropic | $s$ | adiabatic and reversible: the ideal compressor, turbine, intake and nozzle |
| isenthalpic | $h$ | throttling |

Isobaric and isentropic are the two that matter for propulsion.

"Isentropic = adiabatic + reversible" only works one way (L19, ll. 83–89). A reversible adiabatic process is isentropic, but an isentropic process needn't be adiabatic: an irreversible process that generates entropy and is cooled at just the right rate keeps $s$ constant. In this module every isentropic component is also adiabatic, so the distinction rarely matters. The displacement work is the area under the process on a $p$–$V$ diagram, so two different paths between the same states do different work (notes Fig. 2.1; 3 Feb, ll. 163–170).

### Specific heats, ideal gas and perfect gas

Definitions:

$$
h = u+pv,\qquad c_v = \left(\frac{\partial u}{\partial T}\right)_v,\qquad c_p = \left(\frac{\partial h}{\partial T}\right)_p
$$

Ideal gas (elastic collisions, negligible molecular volume, no intermolecular forces; 3 Feb, ll. 235–243). The equation of state in its three equivalent forms:

$$
pV = n\bar RT,\qquad pV = mRT,\qquad p = \rho RT,\qquad R = \frac{\bar R}{M}
$$

with $\bar R=8.3145$ kJ kmol⁻¹ K⁻¹. For an ideal gas $u$ and $h$ depend on $T$ only, but $c_v(T)$ and $c_p(T)$ still vary with temperature, so

$$
\Delta h = \int_{T_1}^{T_2}c_p(T)\,dT,\qquad \Delta u = \int_{T_1}^{T_2}c_v(T)\,dT
$$

The ideal-gas model fails near phase changes and as $p$ approaches the critical pressure (38 bar for air). Up to 20 bar the density error for air is about 1 % (3 Feb, ll. 231–234).

**Perfect gas:** $c_p$ and $c_v$ are constant, so the integrals collapse:

$$
\Delta h = c_p(T_2-T_1),\qquad \Delta u = c_v(T_2-T_1)
$$

with

$$
R = c_p-c_v,\qquad \gamma = \frac{c_p}{c_v}
$$

For air: $R=287$, $c_p=1005$ J kg⁻¹ K⁻¹, $\gamma=1.4$.

- A monatomic gas (argon) has constant $c_p$ at all temperatures. CO₂ and air do not: air's $c_p$ rises by about 200 J kg⁻¹ K⁻¹ (20 %) over a 1500 K range (3 Feb, ll. 207–216).
- From 300 K to 1000 K a single constant $c_p$ is fine. Across a combustor (say 250 → 1700 K) it is not; either use a higher constant value for the hot part, or split the process and use a different constant $c_p$ in each part (3 Feb, ll. 218–222, 263–269). This is why later weeks use separate $c_{pa}$ and $c_{pg}$ for air and combustion products.

> [!example] Adiabatic work on air (3 Feb, ll. 171–194)
> Air at $T_1=300$ K receives 100 kJ/kg of work adiabatically. Find $T_2$.
>
> First Law per unit mass, with $q=0$ and work done on the gas ($w_{12}=-100$ kJ/kg):
>
> $$c_v(T_2-T_1) = -w_{12}$$
>
> $$T_2 = 300+\frac{100}{0.718} = 439\ \mathrm K$$

---

## 2. Mixtures (Lecture 5)

### Mass and mole fractions

Species $i$ has $n_i$ moles and mass $m_i=n_iM_i$. The totals are $n=\sum n_i$ and $m=\sum m_i$.

$$
y_i = \frac{n_i}{n}\ \text{(mole fraction)},\qquad x_i = \frac{m_i}{m}\ \text{(mass fraction)}
$$

**Mean molar mass.** Divide total mass by total moles and substitute $m_i=n_iM_i$:

$$
M = \frac{m}{n} = \frac{\sum n_iM_i}{n} = \sum y_iM_i
$$

Or, using $n_i=m_i/M_i$:

$$
\frac1M = \frac{n}{m} = \frac{\sum m_i/M_i}{m} = \sum\frac{x_i}{M_i}
$$

**Conversion between fractions.** Divide $m_i=n_iM_i$ by $m=nM$:

$$
x_i = \frac{n_iM_i}{nM} = y_i\frac{M_i}{M}
$$

> [!warning] Transcript slip: mean molar mass from mass fractions (3 Feb, ll. 316–324)
> The lecturer computes the molar mass of air as $28\times0.78+32\times0.22$, i.e. weighting $M_i$ by the mass fractions $0.78$ and $0.22$. The correct mass-fraction form is $M=(\sum x_i/M_i)^{-1}=(0.78/28+0.22/32)^{-1}=28.79$ kg/kmol, against 28.88 from the slip. The numbers are close only because $M_{N_2}$ and $M_{O_2}$ are similar. For a mixture containing hydrogen the wrong method fails badly. Weight by mole fractions ($M=\sum y_iM_i$) or use the reciprocal mass-fraction form.

> [!example] H₂/O₂ rocket mixture (3 Feb, ll. 332–353, 388–395)
> 1 kg of H₂ burns with 7.94 kg of O₂.
>
> Mass fraction:
>
> $$x_{H_2} = \frac{1}{1+7.94} = 0.112$$
>
> Moles: $n_{H_2}=1/2=0.5$ kmol and $n_{O_2}=7.94/32=0.248$ kmol, so $n=0.748$ kmol and
>
> $$y_{H_2} = \frac{0.5}{0.748} = 0.668$$
>
> At a total pressure of 20 bar (Dalton, below): $p_{H_2}=0.668\times20=13.36$ bar and $p_{O_2}=(1-0.668)\times20=6.64$ bar.
>
> An 11 % mass fraction is a 67 % mole fraction: light species dominate the mole count.

> [!warning] Transcript slip (3 Feb, l. 334)
> "For the complete combustion of hydrogen, we need almost 8 kg of air." The 7.94 kg is oxygen (the mole count uses $M=32$). Burning 1 kg of H₂ in air needs about 34 kg of air.

Data tables quote molar masses in either kg/kmol or g/mol (3 Feb, ll. 345–348). They are numerically equal, but keep the units consistent with $\bar R$, 8.3145 kJ kmol⁻¹ K⁻¹ or J mol⁻¹ K⁻¹.

### Partial pressure, partial volume and Dalton's law

Partial pressure $p_i$: the pressure species $i$ would exert alone in the full volume $V$ at temperature $T$. Partial volume $V_i$: the volume it would occupy alone at the mixture's $p$ and $T$ (notes §2.3.1).

Derivation for an ideal gas. Write the equation of state for species $i$ alone in $V$, and for the mixture:

$$
p_iV = n_i\bar RT,\qquad pV = n\bar RT
$$

Divide; $V$, $\bar R$ and $T$ cancel:

$$
\frac{p_i}{p} = \frac{n_i}{n} = y_i
$$

Repeat at fixed $p$ with $pV_i=n_i\bar RT$:

$$
\frac{V_i}{V} = \frac{n_i}{n} = y_i
$$

Summing over species gives Dalton's law of partial pressures and its volume counterpart (Amagat):

$$
\boxed{p = \sum p_i,\qquad V = \sum V_i,\qquad \frac{p_i}{p} = \frac{V_i}{V} = y_i}
$$

So "percent by volume" means mole fraction.

### Properties of a mixture

Extensive properties add: $U=\sum U_i=\sum m_iu_i$. Divide by $m$ to get the specific property:

$$
u = \sum x_iu_i,\qquad h = \sum x_ih_i,\qquad s = \sum x_is_i,\qquad c_p = \sum x_ic_{p,i},\qquad c_v = \sum x_ic_{v,i}
$$

Specific properties are mass-weighted averages (3 Feb, ll. 396–412).

> [!example] $c_p$ of air (3 Feb, ll. 415–427)
> Air is 23.2 % O₂ and 76.8 % "atmospheric nitrogen" N₂* by mass (21/79 by volume). With $c_{p,O_2}=0.92$ and $c_{p,N_2^*}=1.03$ kJ kg⁻¹ K⁻¹:
>
> $$c_p = 0.232\times0.92+0.768\times1.03 = 0.213+0.791 = 1.004\ \mathrm{kJ\,kg^{-1}K^{-1}}$$

> [!warning] Transcript slip: the "typo" that was not a typo (3 Feb, ll. 421–427)
> The lecturer calls the slide's 1.004 a typo and "corrects" it to 1.01, reasoning that a weighted average of 0.92 and 1.03 cannot be 1.004. But 1.004 is between 0.92 and 1.03, and the arithmetic above gives exactly 1.0045. The slide value 1.004 is correct.

---

## 3. Steady Flow Energy Equation (Lecture 6)

### From the First Law to the SFEE

The SFEE is the First Law applied to a steady control volume (notes §2.4). The fluid carries specific total energy

$$
e_T = u+e_P+e_k+e_g = u+\frac p\rho+\tfrac12V^2+gz
$$

where $p/\rho$ is the flow (pressure) energy. Heat in minus shaft work out equals the energy carried out minus the energy carried in:

$$
\dot Q-\dot W_x = \sum_{out}\dot m\,e_T-\sum_{in}\dot m\,e_T
$$

Combine $u+p/\rho=h$:

$$
\dot Q-\dot W_x = \sum_{out}\dot m\Big(h+\tfrac12V^2+gz\Big)-\sum_{in}\dot m\Big(h+\tfrac12V^2+gz\Big)
$$

For a single stream divide by $\dot m$ and drop $gz$ (no significant height change in an engine):

$$
\boxed{q-w_x = \Big(h+\tfrac12V^2\Big)_{out}-\Big(h+\tfrac12V^2\Big)_{in}}
$$

$w_x$ is shaft work, not the $p\,dV$ displacement work of a closed system: the flow work is already inside $h$.

> [!warning] Transcript slip (6 Feb, ll. 86–87)
> "If we put together the first two terms, so the internal energy and the pressure energy, what we get is the entropy." It is the enthalpy, $h=u+p/\rho$.

The combination $h+\tfrac12V^2$ is the stagnation enthalpy $h_0$ (previewing W03), so the SFEE becomes $q-w_x=\Delta h_0$. "Working with the total quantity" in the lecture (6 Feb, ll. 164–176) means exactly this: inside the machines the kinetic energy is either small or lumped into $h_0$.

### The turbojet, component by component

Stations (6 Feb, ll. 136–147): 1 free stream, 2 diffuser exit / compressor inlet, 3 compressor exit / burner inlet, 4 burner exit / turbine inlet, 5 turbine exit / nozzle inlet, 6 nozzle exit. The same numbers are kept for the ramjet (no compressor or turbine) in W06.

Diffuser 1→2 (no heat, no work, exit KE negligible):

$$
0 = h_2-h_1-\tfrac12V_1^2
$$

Compressor 2→3 (adiabatic, KE negligible, work done *on* the gas so $w_{23}<0$):

$$
w_c = -w_{23} = h_3-h_2
$$

Burner 3→4 (constant pressure heat addition, no work; $q_{34}=\dot m_f\,LCV/\dot m_a$):

$$
q_{34} = h_4-h_3
$$

Turbine 4→5 (adiabatic, work done *by* the gas):

$$
-w_t = -w_{45} = h_5-h_4
$$

All of the turbine work drives the compressor:

$$
w_t = w_c\quad\Longrightarrow\quad h_4-h_5 = h_3-h_2
$$

Nozzle 5→6 (no heat, no work, inlet KE negligible):

$$
0 = h_6-h_5+\tfrac12V_6^2
$$

| Component | Zero terms | Result | Sign check |
|---|---|---|---|
| Diffuser 1→2 | $q$, $w$, $V_2$ | $h_2=h_1+\tfrac12V_1^2$ | $h$ rises |
| Compressor 2→3 | $q$, KE | $w_c=h_3-h_2$ | $h_3>h_2$ |
| Burner 3→4 | $w$, KE | $q_{34}=h_4-h_3$ | $h_4>h_3$ |
| Turbine 4→5 | $q$, KE | $w_t=h_4-h_5=w_c$ | $h_5<h_4$ |
| Nozzle 5→6 | $q$, $w$, $V_5$ | $\tfrac12V_6^2=h_5-h_6$ | $h_6<h_5$ |

The sign column above is a free first check on every component: "if you get that at the exit of the compressor your enthalpy is lower, you have to do something" (6 Feb, ll. 184–186).

Perfect gas and reversibility (notes §2.4.2). $\Delta h=c_p\Delta T$, and every reversible adiabatic process is isentropic, so (derived in §4)

$$
\frac{T_2}{T_1} = \left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}\qquad\Longleftrightarrow\qquad \frac{p_2}{p_1} = \left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)}
$$

> [!example] Intake temperature and pressure rise (6 Feb, ll. 222–235)
> A turbojet flies at $V_1=200$ m/s through air at $T_1=250$ K, $p_1=50$ kPa. Find the compressor inlet state (station 2).
>
> Diffuser SFEE with $\Delta h=c_p\Delta T$:
>
> $$T_2 = T_1+\frac{V_1^2}{2c_p} = 250+\frac{200^2}{2\times1005} = 269.9\ \mathrm K$$
>
> Isentropic compression:
>
> $$p_2 = p_1\left(\frac{T_2}{T_1}\right)^{3.5} = 50\times\left(\frac{269.9}{250}\right)^{3.5} = 65.4\ \mathrm{kPa}$$
>
> The ram effect alone gives a 31 % pressure rise at only Mach 0.63.

---

## 4. Entropy

### Definition and the TdS equations

Macroscopically, entropy changes with reversible heat transfer at temperature $T$ (notes eq. 2.58–2.59):

$$
dS = \frac{\delta Q_{rev}}{T},\qquad ds = \frac{\delta q_{rev}}{T}
$$

It is a state property, so $\Delta s$ between two states does not depend on the path. Only for isothermal heat transfer can you write $\Delta S=Q/T$ directly (6 Feb, ll. 237–248); otherwise you need the TdS equations.

Start from three relations (notes eqs. 2.60–2.62): the First Law, displacement work and the entropy definition,

$$
dU = \delta Q-\delta W,\qquad \delta W = p\,dV,\qquad \delta Q = T\,dS
$$

Substitute the second and third into the first:

$$
\boxed{T\,dS = dU+p\,dV}\qquad\text{(first TdS equation)}
$$

Differentiate $H=U+pV$:

$$
dH = dU+p\,dV+V\,dp
$$

so $dU+p\,dV=dH-V\,dp$, and

$$
\boxed{T\,dS = dH-V\,dp}\qquad\text{(second TdS equation)}
$$

No assumption about the substance has been made; both equations hold for any simple compressible system.

### Finite entropy changes of a perfect gas

Take the specific second TdS equation:

$$
T\,ds = dh-v\,dp
$$

Use $dh=c_p\,dT$ and the ideal-gas law $v=RT/p$:

$$
T\,ds = c_p\,dT-\frac{RT}{p}\,dp
$$

Divide by $T$:

$$
ds = c_p\frac{dT}{T}-R\frac{dp}{p}
$$

For a perfect gas $c_p$ is constant, so integrate from 1 to 2:

$$
\boxed{s_2-s_1 = c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}}
$$

The $T$–$v$ form (notes eq. 2.74). Start from the first TdS equation $T\,ds=du+p\,dv$ with $du=c_v\,dT$ and $p=RT/v$:

$$
ds = c_v\frac{dT}{T}+R\frac{dv}{v}\quad\Longrightarrow\quad s_2-s_1 = c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1}
$$

The $p$–$v$ form (notes eq. 2.75). From $pv=RT$, $\ln(T_2/T_1)=\ln(p_2/p_1)+\ln(v_2/v_1)$. Substitute into the $T$–$v$ form:

$$
s_2-s_1 = c_v\ln\frac{p_2}{p_1}+(c_v+R)\ln\frac{v_2}{v_1}
$$

and $c_v+R=c_p$:

$$
s_2-s_1 = c_v\ln\frac{p_2}{p_1}+c_p\ln\frac{v_2}{v_1}
$$

Use whichever pair of properties you are given.

### The isentropic relations follow

Set $s_2=s_1$ in the $T$–$p$ form:

$$
c_p\ln\frac{T_2}{T_1} = R\ln\frac{p_2}{p_1}
$$

Divide by $c_p$ and use $R/c_p=(c_p-c_v)/c_p=(\gamma-1)/\gamma$:

$$
\ln\frac{T_2}{T_1} = \frac{\gamma-1}{\gamma}\ln\frac{p_2}{p_1}
$$

$$
\boxed{\frac{T_2}{T_1} = \left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}}
$$

For air $(\gamma-1)/\gamma=0.2857$ and its inverse is 3.5.

### Why the isobars diverge, and why a gas turbine gives net work

Along an isobar ($dp=0$) the second TdS equation gives $T\,ds=c_p\,dT$, so

$$
\left(\frac{\partial T}{\partial s}\right)_p = \frac{T}{c_p}
$$

The slope of an isobar is proportional to $T$, so two isobars spread apart as temperature rises. For a given pressure ratio, the isentropic temperature *change* scales with the starting temperature:

$$
\Delta T_s = T_1\left[\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}-1\right]
$$

> [!check] Cold compression against hot expansion, same pressure ratio 30
> - Compress isentropically from 300 K: $w_{c,s}=1.005\times300\times(30^{0.2857}-1)=495$ kJ/kg.
> - Expand isentropically from 1500 K: $w_{t,s}=1.005\times1500\times(1-30^{-0.2857})=937$ kJ/kg.
>
> The turbine could deliver almost twice the work the compressor needs. In a turbojet the surplus becomes jet kinetic energy; in a turbofan it drives the fan.

---

## 5. Isentropic efficiency

Real compressors and turbines have friction and turbulence, which generate heat inside the gas and raise its entropy (6 Feb, ll. 276–299). On a $T$–$s$ diagram the real exit lies to the right of the isentropic exit on the same exit isobar, and because isobars slope upwards, higher.

![[prop_isentropic_efficiency_Ts.png|760]]

Compressor (notes eqs. 2.76–2.77): isentropic work over actual work,

$$
\eta_c = \frac{w_{c,s}}{w_c} = \frac{h_{2s}-h_1}{h_2-h_1} = \frac{T_{2s}-T_1}{T_2-T_1}
$$

Turbine (notes eqs. 2.78–2.79): actual work over isentropic work,

$$
\eta_t = \frac{w_t}{w_{t,s}} = \frac{h_1-h_2}{h_1-h_{2s}} = \frac{T_1-T_2}{T_1-T_{2s}}
$$

The ideal process always sits on the side that makes $\eta<1$: on the top for a compressor (it needs less work than the real one) and on the bottom for a turbine (it gives more work than the real one).

> [!warning] Transcript slip (6 Feb, ll. 303–307)
> "The work in the ideal case is given by the entropy at the point 2s… minus the entropy that we have at the beginning." It is the enthalpy: $w_{c,s}=h_{2s}-h_1$. The lecturer also corrects himself mid-sentence about which term is larger (ll. 308–311): the numerator $h_{2s}-h_1$ is the smaller one.

Four sanity checks (notes §2.5.4):

- $\eta<1$ for both machines;
- the real exit temperature is higher than the isentropic one, in both machines;
- a real compressor needs more work than an isentropic one ($w_c>w_{c,s}$);
- a real turbine delivers less work than an isentropic one ($w_t<w_{t,s}$).

### Worked example – turbine with isentropic efficiency

Turbine from $p_4=30$ bar, $T_4=1500$ K to $p_5=1$ bar with $\eta_t=0.85$; air properties.

Isentropic exit:

$$
T_{5s} = 1500\times\left(\frac{1}{30}\right)^{0.2857} = 567.6\ \mathrm K
$$

Real exit, rearranging the turbine definition:

$$
T_5 = T_4-\eta_t(T_4-T_{5s}) = 1500-0.85\times(1500-567.6) = 707.5\ \mathrm K
$$

Work:

$$
w_t = c_p(T_4-T_5) = 1.005\times(1500-707.5) = 796.5\ \mathrm{kJ/kg}
$$

Check: $T_5=707.5>T_{5s}=567.6$ K and $w_t<w_{t,s}=937$ kJ/kg ✔.

### Worked example – compressor and its entropy rise

Compressor from 300 K with pressure ratio 15 and $\eta_c=0.9$ (the Earth case of [[SESA2023 Problem Sheet 2 Solutions]] Q2.2).

$$
T_{2s} = 300\times15^{0.2857} = 650.4\ \mathrm K
$$

$$
T_2 = T_1+\frac{T_{2s}-T_1}{\eta_c} = 300+\frac{350.4}{0.9} = 689.3\ \mathrm K
$$

$$
w_c = 1.005\times(689.3-300) = 391\ \mathrm{kJ/kg}
$$

Entropy generated:

$$
s_2-s_1 = 1005\ln\frac{689.3}{300}-287\ln15 = 836.9-777.2 = 58.8\ \mathrm{J\,kg^{-1}K^{-1}}
$$

Positive, as it must be for an irreversible adiabatic process.

---

## 6. Problem-solving workflow

1. Sketch the engine and number the stations 1–6.
2. For each component write the SFEE and strike out the zero terms (table in §3).
3. Choose $c_p$ and $\gamma$ for the temperature range (air for the cold end, products for the hot end).
4. Isentropic exit temperature from the pressure ratio; then the real exit from $\eta_c$ or $\eta_t$.
5. Use $w_t=w_c$ to link turbine and compressor.
6. Check signs, the four efficiency checks, and that $\Delta s\ge0$ for every adiabatic process.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| two-property rule | state postulate | notes §2.2.3 | |
| perfect gas | calorically perfect gas | notes §2.2.6 | An ideal gas is then "thermally perfect". |
| atmospheric nitrogen N₂* | | data book, 3 Feb | N₂ plus the argon and trace gases, lumped. |
| mass fraction $x_i$ | gravimetric fraction, $Y_i$ | 3 Feb, l. 419 | Combustion texts often use $Y_i$. |
| mole fraction $y_i$ | volumetric fraction, $X_i$ | 3 Feb, l. 420 | Beware: some texts use $X_i$ for mole fraction. |
| shaft work $w_x$ | technical work | notes §2.4 | |
| burner | combustor, combustion chamber | notes Fig. 2.5 | |
| diffuser | intake, inlet | notes Fig. 2.5 | W04 uses "intake". |
| isentropic efficiency | adiabatic efficiency | notes §2.5.4 | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] · Next: [[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]
- Thermofluids foundation: [[SESA1016 T4 - Entropy and Isentropic Relations]] · [[SESA1016 T5 - Ideal Heat Engine Models]] · [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- Worked sheet: [[SESA2023 Problem Sheet 2 Solutions]] (includes the Mars compressor mixture question) · Formula list: [[SESA2023 Formula Sheet]]
- Applied to whole engines: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · combustion products and $c_{pg}$: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]

## Sources

- `Week 02 - Thermodynamics.pdf`: Week 2 notes (I. Peters, T. Grenga) §§2.2–2.5 and the Lecture 4–6 slides.
- Transcripts (line numbers refer to these files): `SESA2023 Lecture 2026-02-03.txt` (3 Feb, Lectures 4 and 5 back to back: fundamentals, gases, mixtures); `SESA2023 Lecture 2026-02-06.txt` (6 Feb, Lecture 6: SFEE, entropy, isentropic efficiency).
- `Additional question on thermodynamics.pdf`: the gap-fill handout for this refresher.
- Data book: molar masses and $c_p$, $c_v$ tables.

## Self-study tasks

Tasks marked *(set)* were set or explicitly left to you in the Week 2 lectures or notes; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Work [[SESA2023 Problem Sheet 2 Solutions|Problem Sheet 2]] (heat engine, Mars compressor, turbojet with isentropic components).
- [ ] *(set)* Adiabatic-work example: 300 K air, 100 kJ/kg of work (3 Feb, ll. 171–194). Target 439 K. → [[#Specific heats, ideal gas and perfect gas]]
- [ ] *(set)* H₂/O₂ mixture: mass and mole fractions, then partial pressures at 20 bar (3 Feb, ll. 332–395). Targets $x=0.112$, $y=0.668$, 13.36 and 6.64 bar. → [[#Mass and mole fractions]]
- [ ] *(set)* Intake example at 200 m/s, 250 K, 50 kPa (6 Feb, ll. 222–235). Targets 269.9 K, 65.4 kPa. → [[#The turbojet, component by component]]
- [ ] Write the SFEE for each of the five turbojet components from memory, with the sign check. → [[#The turbojet, component by component]]

### Further practice

- [ ] Derive both TdS equations, then the three perfect-gas entropy forms. → [[#Definition and the TdS equations]] · [[#Finite entropy changes of a perfect gas]]
- [ ] Derive $T_2/T_1=(p_2/p_1)^{(\gamma-1)/\gamma}$ from $\Delta s=0$. → [[#The isentropic relations follow]]
- [ ] Show $(\partial T/\partial s)_p=T/c_p$ and use it to explain why a gas turbine gives net work. → [[#Why the isobars diverge, and why a gas turbine gives net work]]
- [ ] Find the molar mass of air both ways and explain why the lecture's method only *happens* to work. → [[#Mass and mole fractions]]
- [ ] Recompute the $c_p$ of air and decide whether the slide's 1.004 was a typo. → [[#Properties of a mixture]]
- [ ] Turbine and compressor examples with isentropic efficiency, including $\Delta s$. → [[#Worked example – turbine with isentropic efficiency]] · [[#Worked example – compressor and its entropy rise]]
- [ ] *(set)* Explore the CoolProp Jupyter notebook on Blackboard for real-gas properties (3 Feb, ll. 270–272; notes slide "Real fluid properties"); Problem Sheet 2 Q2.4 uses it.
