---
title: "SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
order: 6
tags:
  - sesa2023
  - cycle-analysis
  - brayton
  - ramjet
  - turbojet
  - afterburner
aliases: ["Cycle analysis", "Turbojet analysis", "Ramjet analysis", "SESA2023 Week 6"]
date: 2026-09-24
status: lectured
coverage: "Week 6 (Lectures 16–19)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA1016 T5 - Ideal Heat Engine Models]]"]
next_topics: ["[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
key_concepts: ["[[Brayton Cycle]]", "[[Specific Thrust]]", "[[Ramjet]]", "[[Turbojet]]", "[[Afterburning (Reheat)]]", "[[Turbine Entry Temperature and Blade Cooling]]", "[[Component Stagnation Pressure Ratios]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 4 Solutions]]", "[[SESA2023 Problem Sheet 7 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf", "02 - Sources/Lectures/SESA2023 Lecture 16.txt", "02 - Sources/Lectures/SESA2023 Lecture 17.txt", "02 - Sources/Lectures/SESA2023 Lecture 18.txt", "02 - Sources/Lectures/SESA2023 Lecture 19.txt"]
---

# SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat

> [!abstract] Summary
> Every air-breathing jet approximates a Brayton cycle of compression, constant-pressure heating and expansion: a ramjet compresses by ram effect alone, while a turbojet adds a compressor driven by a turbine on the same shaft, so that $w_t=w_c$ on each spool. The method starts from the atmosphere, switches to the engine's frame with stagnation properties, marches through the components with the SFEE, the isentropic relations and the isentropic efficiencies, and finishes with specific thrust, TSFC and the three efficiencies. Real engines lose performance through component inefficiency, stagnation-pressure losses, the higher $c_p$ of the products and turbine cooling air; the levers are the overall pressure ratio, $T_{04}/T_{02}$ and component efficiencies, and reheat buys thrust at a large sfc penalty.

> [!summary]- Exam use: quick path
> - **Use it when:** given a flight condition, pressure ratio, turbine entry (or peak) temperature and component efficiencies, and asked for station temperatures and pressures, $f$, specific thrust, sfc or the efficiencies; or for the speed at which an ideal ramjet produces a given thrust.
> - **Assumptions:** steady; perfect gas with cold-air properties up to the burner and product properties after it; adiabatic components; intake $\Gamma_d=1$ and fuel at $T_{ref}=298$ K unless stated; turbine work = compressor work (one spool, no power off-take); nozzle isentropic and fully expanded unless stated.
> - **Method:** 1. ISA → $V=M\sqrt{\gamma RT}$, $T_{01}$, $p_{01}$. 2. Compressor: $T_{03s}$ from $r_c$, then $T_{03}$ from $\eta_c$; $w_c=c_{pa}(T_{03}-T_{02})$. 3. Burner: $f$ from the energy balance; $p_{04}=\Gamma_bp_{03}$. 4. Turbine: $T_{05}$ from $w_t=w_c$ with $(1+f)c_{pp}$, then $T_{05s}$ from $\eta_t$, then $p_{05}$ with $\gamma_p$. 5. Nozzle: $T_6$ from $p_a/p_{05}$, $V_j=\sqrt{2c_{pp}(T_{05}-T_6)}$; then $F/\dot m_a=(1+f)V_j-V$, sfc $=f/(F/\dot m_a)$.
> - **Common mistakes:** using $\gamma_a$ instead of $\gamma_p$ in the turbine and nozzle pressure ratios (L19, ll. 281–286); forgetting the $(1+f)$ on the turbine mass flow.
> - **Practise:** [[#Worked example – turbojet at Mach 2 and 31,000 ft]] · [[SESA2023 Problem Sheet 7 Solutions]] · [[SESA2023 Problem Sheet 4 Solutions]] Q4.1

A jet engine is a heat engine that pushes instead of turning a shaft. It compresses air, burns fuel in it at roughly constant pressure and expands the hot gas; in a turbojet the turbine takes back just enough work to drive the compressor, and everything left over goes into the jet. A higher pressure ratio raises the thermal efficiency, because the more the gas is compressed before heat is added, the larger the fraction of that heat that can later be turned back into work. A higher temperature ratio raises the specific work: the hotter the turbine entry relative to the intake, the more surplus work per kilogram, which is why blade cooling, letting the gas run hotter than the metal can bear, is so valuable.

In flight, the intake compresses the air before it reaches the compressor. At Mach 3 ram compression in the intake alone gives a pressure ratio of about 40 (L18, ll. 153–155), so a compressor and the turbine to drive it are no longer worth carrying, and that is a ramjet. Real components fall short of the ideal: inefficient turbomachinery, pressure drops, the properties of hotter gas and cooling air each take a few points off the ideal efficiency. The simple model gets the trends right, not the exact numbers.

---

## 1. Design requirements and engine families (Lecture 16)

### Requirements beyond thrust

The basic requirements are enough thrust, good efficiency (fuel must be carried, so the two are linked) and a jet faster than the flight speed. Beyond these (L16, ll. 113–182; handout §6.2):

- **Safety and reliability**: complete a take-off after one engine fails at rotation; operate over water on fewer engines; relight at altitude; contain blade failures. The A380's engines sit well ahead of the main spar so a released turbine blade (which cannot be contained) misses the wing structure.
- **Life-cycle cost**: development, materials, manufacture, fuel and maintenance. Fuel is only about a third of an airline's operating cost, but a 1 % fuel-burn saving is worth more than 1 % of payload, because the fuel must be lifted too (L16, ll. 148–162).
- **Operations**: runway length and gate infrastructure (a much bigger fan raises the fuselage), maintenance intervals, noise, emissions.

### Climate impact

Aviation contributes about 2.5 % of CO₂ emissions and about 3.5 % of effective radiative forcing; the difference is mainly contrails, which are short-lived and so potentially quick to tackle (L16, ll. 185–198). Be sceptical of "regulation requires" claims: CORSIA lets aviation buy credits from other sectors without reducing its own emissions (ll. 199–208). Sustainable aviation fuels are about 0.1–0.5 % of supply, mostly from waste fats and used cooking oil (ll. 212–234).

### Efficiency and why different engines suit different speeds

A propulsion system produces thrust, not shaft work, and burns fuel rather than receiving heat, so the relevant figure is the overall efficiency of W01 (L16, ll. 246–278):

$$
\eta_O = \frac{F_NV}{\dot m_f\,LCV} = \eta_P\,\eta_{th},\qquad \eta_P\approx\frac{2V}{V+V_j},\qquad F_N\approx\dot m_a(V_j-V)
$$

| Flight regime | Engine | Reason |
|---|---|---|
| Low subsonic | turboprop, open rotor | huge effective $\dot m$, tiny $\Delta V$; limited by propeller-tip Mach number |
| High subsonic (M 0.8) | high-bypass turbofan | large $\dot m$ at moderate $V_j$ |
| Supersonic to M ≈ 2–2.3 | turbojet or low-bypass turbofan, with reheat | a high $V_j$ is now close to $V$; limited by the combustor-entry temperature |
| M ≈ 2.5–5 | ramjet | ram compression alone gives the pressure ratio; a compressor would overheat the air |
| M > 5 | scramjet | slowing to subsonic would exceed temperature limits, so combustion stays supersonic |

The lecture's operating limits: turbojet combustion to M < 2.3, ramjet to M < 4.2, scramjet above. The SR-71's J58 was a turbo-ramjet: a turbojet at take-off, with the geometry changing so most air bypassed the core at Mach 3+ (L16, ll. 465–470).

Propulsive efficiency isn't limited by Carnot (L16, ll. 282–321): "we're not limited. It's not a thermodynamic efficiency." The waste is simply the kinetic energy left in the jet, which ends up stirring the atmosphere and dissipating as heat. Kinetic energy goes with $V^2$ but thrust with $V$, so moving more air more slowly leaves less energy behind for the same thrust, hence the growth from the slim engines of the 1957 Boeing 707 to the 787's fans, where only about 10 % of the air goes through the core (ll. 298–327).

Other directions mentioned (L16, ll. 328–350, 493–529):

- *Distributed electric fans* (the Airbus/Rolls-Royce E-Thrust concept): one gas turbine generating electricity for six wing-mounted fans. The fans can sit in the wing's thick upper-surface boundary layer. That air is already slower than the aircraft, so ingesting it means less ram drag and better propulsive efficiency, at the cost of generator, cable and motor weight.
- *Scramjets*: the supersonic flow must still be compressed (by shocks) before heat is added, and the fuel may autoignite, but stabilising a flame in flow at thousands of m/s, when a turbulent flame only travels tens of m/s, is the big challenge. The NASA test vehicle shown was dropped from a bomber, boosted to about Mach 2 by a rocket, then reached Mach 9.6 on the scramjet.

The fighter context (L18, ll. 13–20): the F-35 tops out around M 1.6 (stealth and manoeuvrability matter more than speed), the F-22 at M 2.3, while the SR-71 flew above Mach 3 in the 1960s by switching to ramjet mode.

---

## 2. The ideal Brayton cycle (Lecture 17)

### Thermal efficiency

The ideal cold-air-standard Brayton cycle (handout §6.4): isentropic compression 1→2, constant-pressure heating 2→3, isentropic expansion 3→4, constant-pressure cooling 4→1; a perfect gas with $c_p=1005$ J kg⁻¹ K⁻¹ and $\gamma=1.4$. Let the pressure ratio be $r_p=p_2/p_1=p_3/p_4$ and write $x=r_p^{(\gamma-1)/\gamma}$.

Heat in and heat out:

$$
q_{in} = c_p(T_3-T_2),\qquad q_{out} = c_p(T_4-T_1)
$$

The isentropic relations on the two pressure changes give the same ratio:

$$
\frac{T_2}{T_1} = x = \frac{T_3}{T_4}\qquad\Longrightarrow\qquad T_2 = xT_1,\quad T_4 = \frac{T_3}{x}
$$

Thermal efficiency:

$$
\eta_{th} = \frac{w_{net}}{q_{in}} = 1-\frac{q_{out}}{q_{in}} = 1-\frac{T_4-T_1}{T_3-T_2} = 1-\frac{T_3/x-T_1}{T_3-xT_1}
$$

Factor $1/x$ out of the numerator:

$$
\eta_{th} = 1-\frac{1}{x}\cdot\frac{T_3-xT_1}{T_3-xT_1}
$$

$$
\boxed{\eta_{th} = 1-\frac{1}{r_p^{(\gamma-1)/\gamma}}}
$$

The efficiency depends only on the pressure ratio (and $\gamma$). For $r_p=30$: $1-30^{-0.2857}=62.2$ %.

- A higher $\gamma$ also raises it, which is why some closed-cycle plants use helium ($\gamma=1.66$) or the cheaper argon (L17, ll. 32–36).
- $\eta_{th}\to100$ % as $r_p\to\infty$. That does not break the Second Law: an infinite pressure ratio also means an infinite temperature ratio, and Carnot allows 100 % for that (L17, ll. 171–176).
- "Cold air standard" means $c_p$ and $\gamma$ taken at ambient temperature; real air's $c_p$ depends on temperature, so you must say which air you mean (L17, ll. 22–28).

### Why the turbine pressure ratio is smaller than the compressor's

In a ground power plant the turbine expands back to ambient, so compressor and turbine have the same pressure ratio (L17, ll. 46–56). In a turbojet the turbine only has to supply the compressor's work, and work depends on a temperature difference, not a ratio (L17, ll. 57–77):

$$
c_{pa}(T_{03}-T_{02}) = (1+f)c_{pp}(T_{04}-T_{05})
$$

The turbine works at a much higher temperature, so it delivers that temperature drop with a smaller temperature ratio, and so a smaller pressure ratio. The pressure left over after the turbine drives the propulsive nozzle, and since the nozzle pressure ratio exceeds the intake's, $V_j>V$: net thrust. (In the W06 worked example: compressor 30, turbine $6467/400=16.2$.)

### Specific work and its optimum

With $\theta=T_3/T_1$ (the cycle temperature ratio):

$$
w_{net} = c_p(T_3-T_4)-c_p(T_2-T_1) = c_pT_1\left[\theta\left(1-\frac1x\right)-(x-1)\right]
$$

Differentiate with respect to $x$ and set to zero:

$$
\frac{dw_{net}}{dx} = c_pT_1\left[\frac{\theta}{x^2}-1\right] = 0\qquad\Longrightarrow\qquad x = \sqrt\theta
$$

So the ideal cycle gives maximum specific work at $r_p=\theta^{\gamma/[2(\gamma-1)]}$, i.e. where $T_2=T_4$. For $T_3=1500$ K and $T_1=288$ K, $\theta=5.21$ and the optimum is $r_p=17.9$, far below the pressure ratios that maximise efficiency.

![[prop_brayton_trends.png|760]]

With irreversible turbomachinery ($\eta_c=\eta_t=0.9$, L17, ll. 200–240):

- an optimum pressure ratio for efficiency appears, and it rises with $T_{04}/T_{02}$;
- maximum specific work occurs at a much lower $r_p$ (about 8–16);
- in the 1960s, with 85 % compressors and turbines, the optimum was about $r_p=25$; better turbomachinery (over 90 %) and hotter turbines now justify about 50 : 1 (L17, ll. 183–187, 232–234);
- so fighters, which want thrust per unit size, use $r_p\approx15$; civil turbofans, which want range, use $r_p\approx45$. Civil engines are designed for efficiency rather than specific work because the fuel (about 100 t on a 787) outweighs the engines (about 30 t), so a heavier, more efficient engine pays (L17, ll. 235–241);
- raising the TET raises both efficiency and specific work; irreversibility hurts most at high $r_p$.

A gas turbine recycles work internally (L17, l. 191): it "actually does a lot of recycling of work between the turbine, sending it back to the compressor, and then harvesting it again in the turbine." In the worked example below the compressor absorbs 749 kJ/kg while the net jet power is only about 400 kJ/kg, and small percentage losses on those large recycled flows are why $\eta_c$ and $\eta_t$ matter so much.

### Why real engines differ from the ideal cycle

From the handout §6.4: pressure losses in intake, combustor and nozzle; non-isentropic turbomachinery; $c_p$ and $\gamma$ vary with temperature, and $c_p$ of products is higher than that of air; combustion is internal; fuel adds mass through the turbine; the exhaust goes to atmosphere (an open cycle). In addition, for aircraft: inlet conditions depend on altitude and Mach number; there is no net work per spool; and the turbine back pressure may differ from ambient because of the nozzle pressure drop.

---

## 3. Ramjets (Lecture 18)

### Layout, pros and cons

A ramjet is a "degenerate gas turbine" with no compressor or turbine (L18, l. 4): a supersonic diffuser (normal or oblique shocks, then a subsonic diffuser to M ≈ 0.2–0.3), a combustor, and a C–D nozzle.

- **Pros:** simple; high thrust/weight; can run a higher combustor-exit temperature (no turbine to protect); reliable.
- **Cons:** needs to be boosted to speed; poor efficiency below M ≈ 2.5; high thermal stress.

### Why compressors disappear at high Mach number

The argument of L18, ll. 28–92 (and L16, ll. 449–458):

1. The hottest the turbine and combustor materials can sustain long-term, with every cooling and coating trick, is roughly 1700 °C ≈ 2000 K.
2. To leave headroom to add heat, the combustor inlet must stay below about 1000 K.
3. Ram compression heats the air before the compressor, and a fixed compressor pressure ratio means a fixed temperature *ratio* on top of that. A turbojet with $r_c=30$ reaches 1000 K at the combustor inlet at about M 2.3.
4. Delete the compressor: ram compression alone puts the combustor inlet in the same band at about M 3, and exceeds it by about M 4.5. Above about M 4.2 even a ramjet runs out of headroom, and dissociation above 2000 K adds losses (W05).
5. Beyond that, the flow cannot be slowed to subsonic at all: a scramjet burns supersonically.

> [!warning] The handout's ramjet section is a placeholder
> In `Week 06-07 - Jet Engines.pdf`, §6.8 "Ramjet engines" contains only the letters "sdf". The ramjet material is in the Lecture 18 slides and transcript, which this section follows.

### The ideal ramjet: exit Mach equals flight Mach

Stations: 1 free stream (static $=p_a$), 2 diffuser exit, 3 combustor exit, 4 nozzle exit. Ideal: adiabatic; isentropic diffuser and nozzle; isobaric combustor ($\Gamma_d=\Gamma_c=\Gamma_n=1$); fully expanded, $p_4=p_a$ (L18, ll. 102–109).

1. Stagnation pressure is constant all the way through: $p_{04}=p_{03}=p_{02}=p_{01}$ (L18, ll. 439–443).
2. The static pressure at entry and exit is the same, $p_4=p_1=p_a$.
3. So the isentropic stagnation-to-static ratio is the same at both ends:

$$
\frac{p_{01}}{p_1} = \frac{p_{04}}{p_4}\qquad\Longrightarrow\qquad \left(1+\frac{\gamma-1}{2}M_1^2\right)^{\frac{\gamma}{\gamma-1}} = \left(1+\frac{\gamma-1}{2}M_4^2\right)^{\frac{\gamma}{\gamma-1}}
$$

$$
\boxed{M_4 = M_1}
$$

The velocities differ because the speed of sound is much higher in the hot jet (L18, ll. 443–449).

**Jet velocity.** $T_{04}=T_{03}$ (adiabatic nozzle) and $T_4=T_{03}/(1+\tfrac{\gamma-1}{2}M_1^2)$, so

$$
V_4 = M_1\sqrt{\gamma RT_4} = M_1\sqrt{\frac{\gamma RT_{03}}{1+\frac{\gamma-1}{2}M_1^2}}
$$

**Specific thrust.** Note $T_{01}=T_{02}=T_a(1+\tfrac{\gamma-1}{2}M_1^2)$, so $V_4=M_1\sqrt{\gamma RT_a}\sqrt{T_{03}/T_{02}}=V\sqrt{T_{03}/T_{02}}$:

$$
\frac{F}{\dot m_a} = (1+f)V_4-V = M_1\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{03}}{T_{02}}}-1\right]
$$

The units are N s kg⁻¹, i.e. m/s: specific thrust is an "effective velocity increase" through the engine (L18, ll. 294–302).

### Worked example – ideal ramjet at Mach 3 and 51,000 ft

The lecture example (L18, ll. 95–302): 51,000 ft, M 3, cold-air properties, LCV 41 MJ/kg at 298 K with fuel injected at 298 K, complete combustion, $T_{03}=1800$ K, fully expanded.

Station 1 (data book Table 24: $T_a=216.65$ K, $p_a=0.111$ bar):

$$
V = 3\sqrt{1.4\times287\times216.65} = 885.1\ \mathrm{m/s}
$$

$$
T_{01} = 216.65\times(1+0.2\times9) = 606.6\ \mathrm K,\qquad p_{01} = 0.111\times2.8^{3.5} = 4.08\ \mathrm{bar}
$$

Ram compression alone gives a pressure ratio of about 37 ("about forty", L18, l. 154).

Diffuser 1→2 (no $q$, no $w$, isentropic): $T_{02}=T_{01}$, $p_{02}=p_{01}$.

**Combustor 2→3.** The W05 balance per kilogram of air with fuel at $T_{ref}$, and a single $c_p$:

$$
c_p(T_{ref}-T_{02})-f\,LCV+(1+f)c_p(T_{03}-T_{ref}) = 0
$$

Solve for $f$:

$$
f = \frac{T_{03}-T_{02}}{LCV/c_p-(T_{03}-T_{ref})} = \frac{1800-606.6}{41\times10^6/1005-(1800-298)} = \frac{1193.4}{39\,294} = 0.0304
$$

Nozzle 3→4 ($M_4=M_1=3$):

$$
V_4 = 3\sqrt{\frac{1.4\times287\times1800}{2.8}} = 1524.7\ \mathrm{m/s}
$$

**Specific thrust:**

$$
\frac{F}{\dot m_a} = 1.0304\times1524.7-885.1 = 686\ \mathrm{m/s}
$$

> [!check] Numerical checks
> - The lecture quotes "686" (L18, l. 298). ✔
> - $\eta_P=2V/(V+V_4)=0.73$ and $\eta_O=(F/\dot m_a)V/(f\,LCV)=0.49$: a very large excess velocity, so a modest propulsive efficiency (L18, ll. 302–308). A modern turbofan's specific thrust is under 100 m/s.

> [!warning] Transcript slip: units of specific thrust (L18, ll. 298–300)
> "Which works out as 686 Newtons… I've written the units wrong there, actually." Specific thrust is in N s kg⁻¹, which is m/s.

The ideal ramjet is exactly a Brayton cycle (L18, l. 324), with ram compression as its only compressor. Its pressure ratio is $p_{01}/p_a$ and the isentropic relation gives $(p_{01}/p_a)^{(\gamma-1)/\gamma}=T_{01}/T_a$, so

$$
\eta_{th} = 1-\left(\frac{p_a}{p_{01}}\right)^{(\gamma-1)/\gamma} = 1-\frac{T_a}{T_{01}}
$$

At M 3: $1-216.65/606.6=64$ %, the same as a Brayton cycle with $r_p=36.7$.

Trends with flight Mach number (L18, ll. 312–348): with only $M$ and $T_{03}$ as free parameters,

- at low $M$ there is little ram compression, so low efficiency and very low thrust;
- at high $M$ the combustor inlet approaches $T_{03}$, so less and less heat can be added; for $T_{03}=2000$ K the thrust falls to zero near M 6;
- the TSFC also rises again at high $M$: it tracks the overall efficiency, and the propulsive efficiency falls even though the thermal efficiency keeps rising.

![[prop_ramjet_performance.png|760]]

### The real ramjet

Real components are modelled with stagnation-pressure ratios and a combustion efficiency (L18, ll. 355–378):

$$
\Gamma_d = \frac{p_{02}}{p_{01}},\qquad \Gamma_c = \frac{p_{03}}{p_{02}},\qquad \Gamma_n = \frac{p_{04}}{p_{03}},\qquad \eta_b = \frac{LCV_{eff}}{LCV}
$$

- The supersonic diffuser cannot be isentropic (shocks, W04).
- The combustor loses $p_0$ to viscous effects and, if the flow is not slowed below about M 0.3, to heat addition itself (W04 heating; "not going to be examined on", ll. 359–363).
- High combustor temperatures bring dissociation (W05), so $\eta_b<1$; use $\eta_b\,LCV$ in place of $LCV$.
- Accelerating nozzle flow keeps boundary layers thin, so $\Gamma_n$ is close to 1.

Then

$$
\frac{p_{04}}{p_a} = \Gamma_d\Gamma_c\Gamma_n\,\frac{p_{01}}{p_a}
$$

and the jet expands through a smaller pressure ratio, so $M_4<M_1$ and the thrust falls. On a $T$–$s$ diagram, each real state lies on the reduced-$p_0$ isobar at the same $T_0$ as the ideal state, so it is shifted right (L18, ll. 415–434). See [[Component Stagnation Pressure Ratios]].

The $\Gamma$s and $\eta_b$ depend on the engine (L18, ll. 388–399). For subsonic gas turbines the intake and nozzle losses are small, the combustor loss is about 5 % and dissociation is small below 1800 K, so gas-turbine questions often give no $\Gamma$s and no combustion efficiency, and you assume 1. Ramjet questions "complicate your lives by adding these additional coefficients".

> [!warning] Which energy balance for $f$?
> - Lecture form (fuel at $T_{ref}$): $f=\dfrac{T_{03}-T_{02}}{LCV/c_p-(T_{03}-T_{ref})}$.
> - Problem Sheet 4 and the pre-2020 papers effectively set $T_{ref}=0$: $(1+f)c_pT_{03}=c_pT_{02}+f\,LCV$.
>
> The difference is only about 1 %. State which you use.

---

## 4. Turbojet analysis (Lecture 19)

### Worked example – turbojet at Mach 2 and 31,000 ft

The handout §6.5 example, worked in L19 (ll. 14–336). Flight at M 2.0 and 31,000 ft ($T_1=226.73$ K, $p_1=28.7$ kPa, data book Table 24). Compressor $r_c=30$, $\eta_c=0.90$; fuel LCV 43 MJ/kg supplied at 298 K; combustor stagnation-pressure loss 4 % and $T_{04}=1500$ K; $\eta_t=0.90$; ideal, fully expanded nozzle. Air: $c_{pa}=1005$, $\gamma_a=1.40$; products: $c_{pp}=1100$, $\gamma_p=1.33$.

**Inlet 1 (flight condition):**

$$
V = 2.0\sqrt{1.4\times287\times226.73} = 603.7\ \mathrm{m/s}
$$

$$
T_{01} = 226.73\times(1+0.2\times4) = 408.1\ \mathrm K,\qquad p_{01} = 28.7\times1.8^{3.5} = 224.6\ \mathrm{kPa}
$$

Because the flight is supersonic, the intake must really be a converging–diverging duct and the nozzle a C–D nozzle, though the schematic does not show it (L19, ll. 43–45). Most of the module's gas-turbine examples are subsonic, which is why intakes and nozzles are usually taken as isentropic (ll. 19–24).

Intake 1→2 (adiabatic, no work, taken as isentropic, L19, ll. 100–110):

$$
T_{02} = T_{01} = 408.1\ \mathrm K,\qquad p_{02} = p_{01} = 224.6\ \mathrm{kPa}
$$

Compressor 2→3 (pressure ratios in gas turbines are stagnation ratios by default, L19, ll. 113–116):

$$
T_{03s} = 408.1\times30^{0.2857} = 1078.5\ \mathrm K
$$

$$
T_{03} = T_{02}+\frac{T_{03s}-T_{02}}{\eta_c} = 408.1+\frac{670.4}{0.9} = 1153.0\ \mathrm K
$$

$$
p_{03} = 30\times224.6 = 6737\ \mathrm{kPa},\qquad w_c = 1005\times(1153.0-408.1) = 748.6\ \mathrm{kJ/kg}
$$

**Burner 3→4.** Stagnation pressure: $p_{04}=0.96\times6737=6467$ kPa. Energy, per kilogram of air (W05 gas-turbine form, fuel at $T_{ref}$):

$$
c_{pa}(T_{ref}-T_{03})-f\,LCV+(1+f)c_{pp}(T_{04}-T_{ref}) = 0
$$

$$
f = \frac{c_{pp}(T_{04}-T_{ref})-c_{pa}(T_{03}-T_{ref})}{LCV-c_{pp}(T_{04}-T_{ref})} = \frac{1100\times1202-1005\times855.0}{43\times10^6-1100\times1202} = 0.01111
$$

**Turbine 4→5.** The spool has zero net work (L19, ll. 243–250), so per kilogram of air

$$
c_{pa}(T_{03}-T_{02}) = (1+f)\,c_{pp}(T_{04}-T_{05})
$$

$$
T_{05} = 1500-\frac{748.6\times10^3}{1.01111\times1100} = 826.9\ \mathrm K
$$

Isentropic exit from $\eta_t$ (ideal turbine does *more* work, so it ends colder):

$$
T_{05s} = T_{04}-\frac{T_{04}-T_{05}}{\eta_t} = 1500-\frac{673.1}{0.9} = 752.2\ \mathrm K
$$

Pressure, inverting the isentropic relation with $\gamma_p$ (exponent $\gamma_p/(\gamma_p-1)=4.03$):

$$
p_{05} = p_{04}\left(\frac{T_{05s}}{T_{04}}\right)^{\gamma_p/(\gamma_p-1)} = 6467\times\left(\frac{752.2}{1500}\right)^{4.03} = 400.4\ \mathrm{kPa}
$$

Nozzle 5→6 (isentropic, fully expanded to $p_a$):

$$
T_6 = T_{05}\left(\frac{p_a}{p_{05}}\right)^{(\gamma_p-1)/\gamma_p} = 826.9\times\left(\frac{28.7}{400.4}\right)^{0.2481} = 430.0\ \mathrm K
$$

$$
V_j = \sqrt{2c_{pp}(T_{05}-T_6)} = \sqrt{2\times1100\times396.9} = 934.5\ \mathrm{m/s}
$$

**Performance:**

$$
\frac{F_N}{\dot m_a} = (1+f)V_j-V = 1.01111\times934.5-603.7 = 341.2\ \mathrm{m/s}
$$

$$
\mathrm{sfc} = \frac{f}{F_N/\dot m_a} = \frac{0.01111}{341.2} = 32.55\ \mathrm{g\,s^{-1}kN^{-1}}
$$

$$
\eta_O = \frac{(F_N/\dot m_a)V}{f\,LCV} = 43.1\ \%,\qquad \eta_{th} = \frac{(1+f)V_j^2-V^2}{2f\,LCV} = 54.3\ \%,\qquad \eta_P = \frac{\eta_O}{\eta_{th}} = 79.4\ \%
$$

![[prop_turbojet_Ts.png|640]]

> [!check] Numerical checks
> - $T_{03}>T_{03s}$ and $T_{05}>T_{05s}$: real exits hotter than isentropic ones in both machines ✔ (W02 check).
> - $\eta_{th}>\eta_O$ ✔ (the jet is not 100 % efficient at propelling the aircraft, L19, ll. 330–336).
> - $p_{05}/p_a=14$: the nozzle is far from choked-and-matched in reality (a convergent nozzle would choke at about 1.85), so "fully expanded" implies a C–D nozzle.

For cold air the lecture uses $c_p = 1005$ J kg⁻¹ K⁻¹ while the data book lists about 1010; "you can use either", so state your value (L19, ll. 36–39).

> [!warning] Sign on the slide's SFEE (L19, l. 198)
> "Work output there should be probably a minus sign more than a plus sign." The SFEE is $\dot Q-\dot W_x=\Delta(\dot mh_0)$; in the burner both terms are zero anyway. Likewise for the compressor $w_x$ comes out negative, because work is put in (ll. 171–176).

> [!warning] Transcript slip (L19, ll. 321–330)
> The lecturer introduces "the propulsive efficiency", writes out the kinetic-energy expression and then corrects himself: "this is not the propulsive efficiency, is it? This is the thermal efficiency." The thermal efficiency is the kinetic-energy rate over the fuel heat; $\eta_P$ is then $\eta_O/\eta_{th}$.

On the $T$–$s$ diagram, draw a real compression or expansion as a dotted line, because only its end states are equilibrium states and the path in between isn't defined (L19, ll. 122–128).

> [!info] Exam technique (L19, ll. 460–477)
> 1. State your assumptions.
> 2. Draw the schematic with station numbers.
> 3. Sketch the $T$–$s$ diagram.
> 4. Write the SFEE in full, then cross out terms for each component.
> 5. Check the real compressor and turbine exits are hotter than their isentropic values.
>
> "If we can see what your thought process has been… we don't have to subtract too many marks." And: "in an exam question it's difficult to ask you to do all those steps… I think you need to be able to do all those steps" (ll. 337–339).

---

## 5. How much do the modelling assumptions matter? (Lecture 19, Table 2)

Base case: $r_p=30$, $T_{04}=1500$ K, flight at M 0.8 and 31,000 ft. Each row adds one assumption to the one above (handout §6.6, Table 2; L19, ll. 341–459).

| Model | $\eta$ | Change |
|---|---|---|
| Ideal Brayton, cold air | 62.2 % | |
| + 90 % turbomachinery | 47.9 % | −14.3 pts (more $w_c$, less $w_t$) |
| Turbojet in flight (open cycle) | 61.0 % | +13.1 pts (ram compression; at M 0.8 the overall ratio rises from 30 to about 45) |
| Combustion instead of heating (same $c_p$) | 61.1 % | only the extra fuel mass through the turbine |
| Products $c_p=1100$, $\gamma=1.35$ | 58.4 % | −2.7 pts |
| GasTurb equilibrium, semi-perfect gas | 58.6 % | |
| + 4 % combustor $\Delta p_0$ | 57.8 % | −0.8 pts |
| + 10 % cooling air | 55.7 % | −2.1 pts |

The simple cold-air model gets the trends right, which is why it is used for hand calculations. It is not quantitatively accurate: the 1100 J kg⁻¹ K⁻¹ product value happens to give nearly the GasTurb answer here, "but if you pick the wrong value it won't… when you go work for Rolls-Royce this is not what you're going to do" (L19, ll. 430–436).

> [!warning] 62.2 % or 62.6 %?
> The Lecture 19 slide ("simple formula for efficiency") prints 62.6 % for the ideal cycle at $r_p=30$, while the handout's Table 2 gives 62.2 %. The formula gives $1-30^{-0.2857}=62.15$ %, so 62.2 % is right and the slide value is a slip.

> [!warning] Inconsistent cooling-air number (L19, ll. 446, 457–458)
> The lecturer says the cooling air costs "another percent", then, at the summary slide, "it looks like two percent, I'm not sure these numbers are consistent with the previous slides". The handout's Table 2 value, −2.1 points, is used above.

> [!check] The ram effect at M 0.8
> $p_{01}/p_1=(1+0.2\times0.64)^{3.5}=1.52$, so the overall pressure ratio is $30\times1.52=45.6$ ("from 30 to 1 to about 45 to 1", L19, ll. 370–372), and the ideal Brayton value for 45.6 is $1-45.6^{-0.2857}=66.4$ %.

---

## 6. Turbine entry temperature and cooling (Lecture 17)

- TET limits efficiency improvement (L17, l. 242). It is set by turbine materials: single-crystal nickel superalloys melt at about 1500 K, and creep, oxidation and thermal fatigue set the working limit lower. Creep (slow elongation under load) is very sensitive to temperature: 10 K hotter roughly halves the creep life (L16, ll. 444–447).
- Metallurgy (L17, ll. 244–281): conventional nickel alloys (Inconel), then directionally solidified (DS) blades with grain boundaries aligned with the centrifugal load, then single-crystal (SX) blades with no grain boundaries at all. Together these added only about 100–150 K in 60 years. Ceramic-matrix composites (CMCs) do not creep but are brittle; the lecturer thinks the published forecast of CMC turbine blades by 2020 was optimistic.
- The overall gain from all technologies: from about 1200 K (900 °C) combustor outlet in the 1960s to about 1800 K sustainable now (Whittle's first engine was about 900 K) (L17, ll. 213–217, 282–286).
- Typical high-bypass values: take-off 1750 K ($T_{04}/T_{02}=6.07$), top of climb 1600 K (6.52; highest rotational speed), cruise 1500 K (6.11; sets engine life).
- Cooling uses compressor air at 800–900 K: convective (internal passages), film (holes and slots blanketing the surface) and thermal barrier coatings (worth about 100 K).
- The combustor must have a pressure drop (3–5 %), or the compressor-delivery air could not be pushed out through the turbine-blade cooling holes (L19, ll. 30–33).
- 10–25 % of compressor air goes to cooling (up to about 15 % from the HPC exit alone, L17, l. 331). It must come from the highest-pressure point and bypass the combustor, and feeding it into blades spinning at very high speed through drilled single-crystal passages is a major manufacturing feat (ll. 297–319). It costs compression work that a non-isentropic compressor cannot recover, and it rejoins the flow at lower pressure, so there is an optimum between the TET gain and the cooling loss (ll. 322–337).

See [[Turbine Entry Temperature and Blade Cooling]].

---

## 7. Reheat (afterburning)

Burn extra fuel downstream of the turbine to raise $T_{06}$ (handout §6.9; L16, ll. 369–390). A hotter gas has a higher speed of sound, so the jet through the choked nozzle is faster and the thrust rises. It lets a military engine meet short extreme demands (carrier take-off, rapid acceleration) without being sized for them (ll. 354–368).

**Flame holders.** The flow behind the turbine moves at about 100 m/s, but a turbulent flame can only propagate upstream at 10–50 m/s (a laminar one at under 1 m/s), so a flame would simply blow out. V-gutters create slow recirculating regions behind them where the flame can anchor (L16, ll. 374–383).

On the $T$–$s$ diagram the reheat adds a second, smaller Brayton-like loop (5→6, then expansion) to the cycle. Its area adds work, but its heat is added at a much lower pressure ratio than the main combustor's, so this "mini Brayton cycle" is much less efficient (L16, ll. 391–408).

**Why the nozzle area must open.** The engine upstream should not notice the afterburner: the turbine exit (nozzle entry) mass flow and $p_{06}$ must stay the same. For a choked nozzle (W03, compact form with product properties),

$$
\dot m = \frac{A_8\,p_{06}}{\sqrt{T_{06}}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}
$$

Holding $\dot m$ and $p_{06}$ fixed (ignoring the small extra fuel mass and $\gamma$ change):

$$
A_8\propto\sqrt{T_{06}}
$$

So a variable-area nozzle is needed. For example, raising $T_{06}$ by 50 % needs $A_8$ to grow by $\sqrt{1.5}=1.22$, about 22 % (compare [[SESA2023 Exam 2020-21 Solutions]] Q3, where $A_8$ grows by 24 %).

**Why reheat is inefficient.** Its heat is added at a much lower pressure than the main combustor's, so the effective pressure ratio of that heat addition is small, and by §2 so is its efficiency. It is used only briefly: take-off, intercept, transonic acceleration. "If increased thrust is required throughout a mission, it would be more efficient to install a more powerful gas turbine without reheat" (handout §6.9). See [[Afterburning (Reheat)]].

---

## 8. Problem-solving workflow

1. Draw the block diagram (diffuser, compressor, burner, turbine, nozzle) and number the stations 1–6 (W02 convention; the ramjet keeps the numbers without compressor and turbine).
2. Sketch the $T$–$s$ diagram with the isobars $p_a$, $p_{02}$, $p_{03}\approx p_{04}$, $p_{05}$.
3. Inlet: ISA, $V$, $T_{01}$, $p_{01}$. Work in stagnation quantities inside the engine (L18, ll. 168–174).
4. For each component write the SFEE and cross out terms; use $\eta_c$, $\eta_t$, $\Gamma$s where given; switch to product properties after the burner.
5. Nozzle: fully expanded unless told otherwise; check for choking if it is convergent.
6. Performance: $F/\dot m_a$, sfc, $\eta_O$, $\eta_{th}$, $\eta_P$; check $\eta_O=\eta_P\eta_{th}$.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| Brayton cycle | Joule cycle | handout §6.4, footnote 1 | |
| turbine entry temperature (TET), $T_{04}$ | turbine inlet temperature (TIT), combustor outlet temperature | L17, handout §6.7 | The course uses all three phrases. |
| specific thrust $X$ or $F_N/\dot m_a$ | net thrust per unit air flow | L19, l. 297 | "The symbol I use… is $X$. It's not universally used." |
| sfc | TSFC | L19, handout §6.5.1.7 | Same quantity as W01, here in g s⁻¹ kN⁻¹. |
| spool | shaft | L19, l. 247 | compressor + shaft + turbine. |
| stagnation pressure ratio $\Gamma$ | pressure recovery, $\pi$ | L18, ll. 370–387 | |
| combustion efficiency $\eta_b$ | burner efficiency | L18, ll. 374–378 | |
| reheat | afterburning, augmentation | handout §6.9 | |
| GasTurb | — | L19, ll. 417–420 | The software used in the propulsion lab. |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]] · Next: [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]
- Foundations: [[SESA1016 T5 - Ideal Heat Engine Models]] (ideal Brayton) · [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] (SFEE, $\eta_c$, $\eta_t$) · [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]] (intakes, $\Gamma_d$)
- Worked sheets: [[SESA2023 Problem Sheet 4 Solutions]] (ramjets), [[SESA2023 Problem Sheet 7 Solutions]] (cycle trends, combustor fuel flow) · Formula list: [[SESA2023 Formula Sheet]]
- Exam staples: turbojet specific thrust (2013-14, 2014-15, 2015-16, 2016-17, 2017-18, 2018-19, 2020-21, 2024-25) and ideal ramjet flight speed (2013-14 to 2017-18). See [[SESA2023 Past Paper Map]].

## Sources

- `Week 06-07 - Jet Engines.pdf`: Weeks 6–7 handout (E. Richardson) §§6.2–6.10, including Table 2, and the Lecture 16–19 slides.
- Transcripts (line numbers refer to these files): L16 `SESA2023 Lecture 16.txt` (3 Mar: requirements, climate, engine families); L17 `SESA2023 Lecture 17.txt` (3 Mar: Brayton trends, TET, cooling); L18 `SESA2023 Lecture 18.txt` (6 Mar: ramjets); L19 `SESA2023 Lecture 19.txt` (10 Mar: turbojet worked example, modelling assumptions).
- Data book: ISA Table 24, SFEE with reference state, isentropic efficiency definitions.

## Self-study tasks

Tasks marked *(set)* were set or explicitly pointed to in the Week 6 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Turbojet at M 2, 31,000 ft, every station: "you need to be absolutely rock solid in your ability to analyze a gas turbine engine" (L19, ll. 337–339, 460–463). Targets $T_{03}=1153$ K, $f=0.0111$, $V_j=934.5$ m/s, $F/\dot m_a=341$ m/s, sfc 32.6 g s⁻¹ kN⁻¹. → [[#Worked example – turbojet at Mach 2 and 31,000 ft]]
- [ ] *(set)* Ideal ramjet at M 3, 51,000 ft (L18, ll. 95–302). Target 686 m/s. → [[#Worked example – ideal ramjet at Mach 3 and 51,000 ft]]
- [ ] *(set)* Show $M_4=M_1$ for an ideal ramjet: "you'll see that in the analysis you do in the problem sheet for the week" (L18, ll. 446–450). → [[#The ideal ramjet: exit Mach equals flight Mach]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 4 Solutions|Problem Sheet 4]] (ideal and real ramjets) and the week's quiz (L18, l. 459); then [[SESA2023 Problem Sheet 7 Solutions|Problem Sheet 7]] (gas-turbine cycle).
- [ ] *(set)* Draw the ideal and real ramjet $T$–$s$ diagrams, locating each real state on its reduced-$p_0$ isobar (L18, ll. 399–434). → [[#The real ramjet]]

### Further practice

- [ ] Derive $\eta_{th}=1-r_p^{-(\gamma-1)/\gamma}$ for the ideal Brayton cycle. → [[#Thermal efficiency]]
- [ ] Derive the pressure ratio for maximum ideal specific work, $x=\sqrt\theta$; evaluate for 1500 K and 288 K. Target 17.9. → [[#Specific work and its optimum]]
- [ ] Explain each row of Table 2 in one sentence. → [[#5. How much do the modelling assumptions matter? (Lecture 19, Table 2)]]
- [ ] Show that the ideal ramjet is a Brayton cycle with $\eta_{th}=1-T_a/T_{01}$, and evaluate it at M 3. Target 64 %. → [[#The real ramjet]]
- [ ] Explain why the turbojet's turbine pressure ratio is smaller than its compressor's. → [[#Why the turbine pressure ratio is smaller than the compressor's]]
- [ ] Explain, with the 1000 K combustor-inlet limit, why turbojets give way to ramjets above about M 2.3 and ramjets to scramjets above about M 4.5. → [[#Why compressors disappear at high Mach number]]
- [ ] Derive $A_8\propto\sqrt{T_{06}}$ for reheat and explain why reheat is inefficient. → [[#7. Reheat (afterburning)]]
- [ ] Explain why a combustor must have a pressure drop when the turbine blades are cooled. → [[#6. Turbine entry temperature and cooling (Lecture 17)]]
- [ ] *(set)* Use GasTurb for the propulsion lab (L19, ll. 417–420).
