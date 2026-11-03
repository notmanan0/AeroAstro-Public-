---
title: "SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 2: Combustion"
order: 5
tags:
  - sesa2023
  - combustion
  - stoichiometry
  - adiabatic-flame-temperature
  - chemical-equilibrium
aliases: ["Combustion", "Adiabatic flame temperature", "SESA2023 Week 5"]
date: 2026-09-24
status: lectured
coverage: "Week 5 (Lectures 13–15)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
next_topics: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
key_concepts: ["[[Stoichiometry and Equivalence Ratio]]", "[[Calorific Value]]", "[[Adiabatic Flame Temperature]]", "[[Chemical Equilibrium and Dissociation]]", "[[Gas Mixtures and Dalton's Law]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 5 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 05 - Combustion.pdf", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-24.txt", "02 - Sources/Lectures/SESA2023 Lecture 2026-02-27.txt", "02 - Sources/Data Book.pdf"]
---

# SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium

> [!abstract] Summary
> Earlier weeks modelled the burner as heat added to air; in a real engine fuel is burned and chemical energy becomes thermal energy (L1, ll. 20–25). This week balances atoms for the stoichiometric air requirement, the air–fuel ratio and the equivalence ratio, uses the lower calorific value (the heat released by isothermal combustion at 298 K), and finds the adiabatic flame temperature, or the fuel flow for a given burner exit temperature, by a three-step path through 298 K. At high temperature the products dissociate (CO₂ ⇌ CO + ½O₂), with Le Chatelier's principle giving the trends and equilibrium constants the composition.

> [!summary]- Exam use: quick path
> - **Use it when:** a question names a fuel and asks for the air needed, $\phi$, the product composition, the flame temperature, the fuel–air ratio for a given $T_{04}$, or an equilibrium composition (CO, NO, H₂).
> - **Assumptions:** air is 21 % O₂ and 79 % N₂* by volume; N₂* is inert; complete combustion to CO₂ and H₂O unless equilibrium is asked for; the burner is adiabatic with no work; constant mixture $c_p$ for reactants and for products; LCV at 298 K; partial pressures in bar.
> - **Method:** 1. Balance C, H, O (and N₂*) per kmol of fuel. 2. $AFR=m_a/m_f$, $\phi=AFR_{st}/AFR$. 3. Flame temperature or $f$ from the three-step energy balance. 4. For equilibrium: unknown product moles → atom balances → one unknown. 5. $K^\theta$ from Table 5 with $p_i=(n_i/n)p$; solve; keep the positive root.
> - **Common mistakes:** forgetting the 3.762 N₂* that comes with each O₂ (it carries heat and mass); using mole numbers instead of masses in the $c_p$ average.
> - **Practise:** [[#Worked example – stoichiometric methane flame temperature]] · [[#Worked example – CO equilibrium at 2600 K and 3 bar]] · [[SESA2023 Problem Sheet 5 Solutions]] Q5.1–Q5.3

Combustion conserves atoms: every carbon, hydrogen and oxygen atom that goes in comes out, and only the molecules change, so balancing atoms tells you how much air a kilogram of fuel needs. For every molecule of oxygen, air carries 3.76 molecules of nitrogen, which in this course don't react but still have to be heated, so they keep the flame temperature down.

The chemical energy is stored in the bonds. Reactants have a high formation enthalpy and products a low one, and in an adiabatic burner the total enthalpy is fixed, so the chemical enthalpy that disappears comes back as sensible enthalpy and the gas gets hot (24 Feb, ll. 376–402). The data book gives values only at 298 K, because the calorific value is measured by burning at 25 °C and removing the heat. To use it in a hot engine, imagine cooling the reactants to 298 K, burning there and heating the products to the exit temperature; energy is a state property, so the detour gives the right answer. Finally, at 2500–3000 K some of the products dissociate: collisions are violent enough to split CO₂ back into CO and O₂, and the products settle at a balance between forming and breaking up that is set by temperature and pressure.

---

## 1. Combustion chemistry (Lecture 13)

### Conservation of atoms and mass

Mass and elements are conserved through a reaction; molecules and moles are not (24 Feb, ll. 101–129). For

$$
\mathrm{2CO+O_2\to2CO_2}
$$

carbon: 2 = 2; oxygen: 2 + 2 = 4; mass: $2\times28+32=56+32=88=2\times44$ kg. The coefficients are relative kmol numbers and can be scaled; only their ratios matter.

Two ways to balance (24 Feb, ll. 131–158):

- *By inspection* for a few species: put 1 in front of the fuel, then balance C, then H, then O.
- *Systematically* for many species: give each product an unknown coefficient and write one equation per element.

For methane in pure oxygen, $a\,\mathrm{CH_4}+b\,\mathrm{O_2}\to c\,\mathrm{CO_2}+d\,\mathrm{H_2O}$:

$$
\text{C: } a = c,\qquad \text{H: } 4a = 2d,\qquad \text{O: } 2b = 2c+d
$$

Put $a=1$: then $c=1$, $d=2$ and $b=(2+2)/2=2$.

$$
\mathrm{CH_4+2O_2\to CO_2+2H_2O}
$$

### Global and elementary reactions

The equation above is a global reaction: it links the starting reactants to the final products. What actually happens is a network of elementary reactions, each a real collision, each reversible (24 Feb, ll. 159–195; 27 Feb, ll. 50–81). Hydrogen–oxygen combustion runs through H, O, OH and others; methane–air needs the GRI mechanism with 53 species and more than 300 reactions (27 Feb, ll. 176–184). The intermediate species live in a flame front only micrometres thick.

### Combustion in air

Air is modelled as 21 % O₂ and 79 % atmospheric nitrogen N₂* by volume (23.2 % and 76.8 % by mass). N₂* lumps nitrogen with the argon and trace gases and is treated as inert (24 Feb, ll. 221–243). In reality some nitrogen does react at high temperature to form NO and NO₂, which are pollutants; inert nitrogen is a pencil-and-paper simplification.

Per kmol of O₂ there are

$$
\frac{0.79}{0.21} = 3.762\ \mathrm{kmol\ N_2^*}
$$

and the mass of that "kmol of O₂ worth of air" is

$$
32+3.762\times28.15 = 137.9\ \mathrm{kg}
$$

with $M_{N_2^*}=28.15$ kg/kmol from the data book.

**Methane in air.** Using the systematic method with $b$ kmol of air units, O: $2\times0.21b=2c+d=4$, so $b=2/0.21$ kmol of air, i.e. 2 kmol of O₂ with $2\times3.762$ kmol of N₂*:

$$
\mathrm{CH_4+2\big(O_2+3.762N_2^*\big)\to CO_2+2H_2O+7.524N_2^*}
$$

> [!warning] Transcript slips in the balancing (24 Feb, ll. 210, 249, 252)
> - l. 210: "two hydrogen from here, two hydrogen from water" while counting oxygen atoms on the right (2 in CO₂ + 2 in 2H₂O = 4).
> - l. 249: "D is equal 1": it is $d=2$ (the lecturer gets it right at l. 219).
> - l. 252: "0.79 over 0.21 for hydrogen": that ratio belongs to nitrogen.

### Complete combustion

**Complete combustion**: all the carbon goes to CO₂ and all the hydrogen to H₂O, so no fuel and no oxidiser remain in stoichiometric conditions, and the heat release is the maximum possible (24 Feb, ll. 254–262). Incomplete combustion leaves fuel, CO, soot or H₂, either because there is not enough oxygen or because of poor mixing, flow or temperature conditions.

### Air–fuel ratio

$$
AFR = \frac{m_a}{m_f}\quad\left(=\frac{\dot m_a}{\dot m_f}\text{ in steady flow}\right),\qquad f = \frac{1}{AFR}
$$

A closed reactor uses masses; a burner in an engine uses mass flow rates. The ratio is the same because the burner sees a continuous stream of each (24 Feb, ll. 271–318).

For methane, mass of air over mass of fuel from the balanced equation:

$$
AFR_{st} = \frac{2\times32+2\times3.762\times28.15}{1\times16} = \frac{2\times137.9}{16} = 17.24
$$

So 1 kg/s of methane needs 17.24 kg/s of air entering the burner (24 Feb, ll. 320–324).

> [!warning] Transcript slips: the names of the ratios (24 Feb, ll. 279–280, 294)
> - l. 279: "the fuel-air ratio, that is also called equivalence ratio". It is not: the fuel–air ratio is $f=1/AFR$, and the equivalence ratio $\phi$ (below) compares the actual mixture with the stoichiometric one.
> - l. 294: the slide had the nitrogen ratio inverted (21/79); the lecturer corrects it to 79/21.

### Equivalence ratio

$$
\boxed{\phi = \frac{AFR_{st}}{AFR} = \frac{n_{a,st}}{n_a}}\qquad\begin{cases}\phi>1 & \text{fuel-rich (unburned fuel)}\\ \phi=1 & \text{stoichiometric}\\ \phi<1 & \text{fuel-lean (excess O}_2\text{ in the products)}\end{cases}
$$

The mass and molar forms agree because the fuel amount is fixed and only the air changes, so the air mass is proportional to the air moles (24 Feb, ll. 336–341).

### Worked example – methane at φ = 0.5

From the lecture (24 Feb, ll. 342–354).

$$
AFR = \frac{AFR_{st}}{\phi} = \frac{17.24}{0.5} = 34.48
$$

The air doubles, $n_a=n_{a,st}/\phi$, and the unused 2 kmol of O₂ appear in the products:

$$
\mathrm{CH_4+4\big(O_2+3.762N_2^*\big)\to CO_2+2H_2O+2O_2+15.05N_2^*}
$$

Check from the masses: $4\times137.9/16=34.48$ ✔.

### Worked example – kerosene at φ = 0.2

Notes §5.3.5. Kerosene is modelled as C₁₀H₂₁ ($M=141$ kg/kmol).

**Stoichiometric.** $\mathrm{C_{10}H_{21}}+a_{st}(\mathrm{O_2}+3.762\mathrm{N_2^*})\to b_1\mathrm{CO_2}+b_2\mathrm{H_2O}+3.762a_{st}\mathrm{N_2^*}$:

$$
\text{C: } b_1 = 10,\qquad \text{H: } 2b_2 = 21\Rightarrow b_2 = 10.5,\qquad \text{O: } 2a_{st} = 2b_1+b_2\Rightarrow a_{st} = 15.25
$$

At $\phi=0.2$, $a=a_{st}/\phi=76.25$; the extra $76.25-15.25=61$ kmol of O₂ pass through:

$$
\mathrm{C_{10}H_{21}+76.25\big(O_2+3.762N_2^*\big)\to10CO_2+10.5H_2O+61O_2+286.9N_2^*}
$$

$$
AFR_{st} = \frac{15.25\times137.9}{141} = 14.9,\qquad f_{st} = \frac{1}{14.9} = 0.067
$$

Gas turbines run so lean because a stoichiometric kerosene flame is far too hot for the turbine (W01). They run at an overall $f\approx0.02$–0.025, or $\phi\approx0.3$–0.4, and the surplus air dilutes and cools the hot gas before the turbine. Ramjets and afterburners, with no turbine to protect, run much nearer stoichiometric.

---

## 2. Combustion thermodynamics (Lecture 14)

### Formation and sensible enthalpy

Each species' enthalpy has two parts (24 Feb, ll. 376–402): a formation enthalpy $h_f^\circ$ (chemical bonds, tabulated at 298 K) and a sensible part that depends on temperature:

$$
h_i(T) = h_{f,i}^\circ+\int_{T_0}^{T}c_{p,i}\,dT,\qquad T_0 = 298\ \mathrm K
$$

Reactants have a higher total formation enthalpy than products.

> [!warning] Transcript slip (24 Feb, ll. 388–413)
> Throughout this passage the transcript says "entropy formation" and even "H always stays for entropy". The quantity is the formation enthalpy $h_f^\circ$, the one tabulated with a superscript zero.

### Two model processes

Both at constant pressure with no shaft work (notes §5.4.1). The SFEE is $\dot Q-\dot W_x=\dot m(h_{out}-h_{in})$.

- Adiabatic ($\dot Q=0$): $h_{out}=h_{in}$. The total enthalpy does not change, but the temperature rises, because the drop in formation enthalpy is exactly matched by a rise in sensible enthalpy. On an $h$–$T$ diagram: a horizontal line from the reactant curve to the product curve.
- Isothermal ($T_{out}=T_{in}$): heat $\dot Q=\dot m(h_{out}-h_{in})<0$ must be removed. On an $h$–$T$ diagram: a vertical line.

![[prop_w05_h_T_combustion.png|760]]

### Calorific value

The calorific value is the heat released per kilogram of fuel by isothermal combustion at the reference state, $T_0=298.15$ K and $p_0=1$ bar (notes §5.4.1; 24 Feb, ll. 431–445). That is how it is measured.

- LCV (lower calorific value): the water in the products stays as vapour. Propulsion always uses the LCV.
- HCV (higher): the water condenses, releasing its latent heat, so HCV > LCV.

Data book Table 1: H₂ 120, CH₄ 50.01, C₃H₈ 46.36, n-octane 44.43 MJ/kg; kerosene is taken as about 43 MJ/kg. The pressure dependence is negligible; the temperature dependence is not, which is the reason for the next section.

> [!warning] Transcript slip (24 Feb, l. 436)
> "Found for a specific temperature, that is 28": it is 298 K (25 °C), as the lecturer says at l. 438.

### Steady-flow adiabatic combustion: the three-step path

The real burner takes reactants at $T_1$ to products at $T_2$ adiabatically. The LCV is only known at $T_0=298$ K, so replace the process with three hypothetical steps that start and end at the same states (notes §5.4.2, Fig. 5.3; 24 Feb, ll. 446–479):

1. Bring the reactants from $T_1$ to $T_0$ (heat $\dot Q_{10}$, negative if $T_1>T_0$):

$$
\dot Q_{10} = \sum_{react}\dot m_i\left(h_{i,0}-h_{i,1}\right)
$$

2. Burn isothermally at $T_0$, rejecting the calorific value:

$$
\dot Q_r = -\dot m_f\,LCV
$$

3. **Heat the products from $T_0$ to $T_2$**:

$$
\dot Q_{02} = \sum_{prod}\dot m_j\left(h_{j,2}-h_{j,0}\right)
$$

The overall process is adiabatic with no net work, so the three heats sum to zero (notes eq. 5.22):

$$
\sum_{react}\dot m_i\left(h_{i,0}-h_{i,1}\right)-\dot m_f\,LCV+\sum_{prod}\dot m_j\left(h_{j,2}-h_{j,0}\right) = 0
$$

Because enthalpy is a state property, the detour gives the same $T_2$ as the real process. $T_2$ is the adiabatic flame temperature.

**With mean specific heats.** Let the reactant and product mixtures have mass-weighted constant $c_{p,r}$ and $c_{p,p}$, and total mass flow $\dot m=\dot m_a+\dot m_f$ (the same in and out):

$$
\dot mc_{p,r}(T_0-T_1)-\dot m_f\,LCV+\dot mc_{p,p}(T_2-T_0) = 0
$$

Divide by $\dot m$ and use $\dot m_f/\dot m=1/(AFR+1)$:

$$
c_{p,r}(T_0-T_1)-\frac{LCV}{AFR+1}+c_{p,p}(T_2-T_0) = 0
$$

$$
\boxed{T_2 = T_0+\frac{\dfrac{LCV}{AFR+1}-c_{p,r}(T_0-T_1)}{c_{p,p}}}
$$

The mixture specific heats are mass-weighted, as in W02:

$$
c_{p,r} = \frac{AFR\,c_{p,a}+c_{p,f}}{AFR+1},\qquad c_{p,p} = \frac{\sum m_jc_{p,j}}{\sum m_j}
$$

### Worked example – stoichiometric methane flame temperature

The lecture example (24 Feb, ll. 480–508): stoichiometric CH₄–air, reactants at $T_1=400$ K; $c_{p,r}=1072$ and $c_{p,p}=1116$ J kg⁻¹ K⁻¹ (the lecturer recomputed both from the data book to confirm them); $LCV=50.01$ MJ/kg; $AFR=17.24$.

**Chemical term:**

$$
\frac{LCV}{AFR+1} = \frac{50.01\times10^6}{18.24} = 2.742\times10^6\ \mathrm{J/kg}
$$

**Reactant cooling term:**

$$
c_{p,r}(T_0-T_1) = 1072\times(298-400) = -1.093\times10^5\ \mathrm{J/kg}
$$

**Flame temperature:**

$$
T_2 = 298+\frac{2.742\times10^6+1.093\times10^5}{1116} = 298+2555 = 2853\ \mathrm K
$$

> [!check] Numerical checks
> - The lecture quotes 2854 K; the 1 K difference is rounding in $AFR$.
> - Hotter reactants give a hotter flame: each 100 K of preheat adds about $1072\times100/1116=96$ K.
> - 2853 K is well above the roughly 2300 K that a real methane flame with 400 K reactants reaches, because dissociation (§3) is ignored here: the products are assumed to be only CO₂, H₂O and N₂.

![[prop_adiabatic_flame_temperature.png|640]]

### The same balance in gas-turbine form

In W06–W07 the question is reversed: the turbine sets the burner exit temperature $T_{04}$, and the fuel–air ratio $f$ must be found. Per kilogram of air, with air entering at $T_{03}$ and fuel supplied at $T_{ref}=298$ K:

$$
c_{pa}(T_{ref}-T_{03})-f\,LCV+(1+f)\,c_{pp}(T_{04}-T_{ref}) = 0
$$

Expand and collect the $f$ terms:

$$
f\left[LCV-c_{pp}(T_{04}-T_{ref})\right] = c_{pp}(T_{04}-T_{ref})-c_{pa}(T_{03}-T_{ref})
$$

$$
\boxed{f = \frac{c_{pp}(T_{04}-T_{ref})-c_{pa}(T_{03}-T_{ref})}{LCV-c_{pp}(T_{04}-T_{ref})}}
$$

> [!example] Typical numbers
> $T_{03}=800$ K, $T_{04}=1600$ K, $c_{pa}=1005$, $c_{pp}=1148$ J kg⁻¹ K⁻¹, $LCV=43$ MJ/kg:
>
> $$f = \frac{1148\times1302-1005\times502}{43\times10^6-1148\times1302} = \frac{1.495\times10^6-0.504\times10^6}{41.5\times10^6} = 0.0239$$
>
> With $f_{st}=0.067$ for kerosene, $\phi=0.0239/0.067=0.36$: inside the lean band above.

This is the formula used for every engine in [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat|W06]]–[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection|W07]]. See [[Adiabatic Flame Temperature]].

---

## 3. Chemical equilibrium (Lecture 15)

### Reversible reactions

Molecules in a gas keep colliding. A collision can form a product, and a later collision can break it up again. The rate of each depends on how much of each species is present and on the activation energy (27 Feb, ll. 28–38). When forward and backward rates match, the composition stops changing: chemical equilibrium, which is dynamic, not static.

- The oxidation of the fuel itself (CH₄ + O₂) releases so much energy that it is effectively one-way.
- Its products do equilibrate: CO₂ ⇌ CO + ½O₂, H₂O ⇌ H₂ + ½O₂, and N₂ + O₂ ⇌ 2NO (notes §5.5).
- Dissociation matters because it makes pollutants (CO, NOₓ) and lowers the heat actually released, so the efficiency and the flame temperature fall (notes §5.5).

The rate of an elementary reaction follows an Arrhenius form, $k\propto\exp(-E_a/(\bar RT))$: a high activation energy makes a reaction unlikely, and a high temperature makes it more likely (27 Feb, ll. 123–130). Pressure matters too: more molecules in the same volume means more collisions (ll. 87–89).

### Le Chatelier's principle

> "If a chemical system at equilibrium experiences a change in concentration, temperature or pressure, then the equilibrium shifts to counteract the imposed change and a new equilibrium is established." (notes §5.5.1)

- **Temperature.** For $\mathrm{CO+\tfrac12O_2\to CO_2}$, Table 4 gives $\Delta h<0$: the forward reaction is exothermic. Raising $T$ favours the endothermic direction, i.e. dissociation of CO₂.
- **Pressure.** The forward reaction goes from 1.5 kmol to 1 kmol of gas. Raising $p$ favours the side with fewer moles, i.e. less dissociation.
- NO formation ($\mathrm{N_2+O_2\to2NO}$) is endothermic at all temperatures, so NO appears only in the hottest regions (27 Feb, ll. 188–190).

### Equilibrium constant

For $a\,\mathrm A+b\,\mathrm B\rightleftharpoons c\,\mathrm C+d\,\mathrm D$ (notes eq. 5.27):

$$
\boxed{K^\theta = \frac{(p_C/p^\theta)^c\,(p_D/p^\theta)^d}{(p_A/p^\theta)^a\,(p_B/p^\theta)^b}}
$$

- $p^\theta=1$ bar, so with partial pressures in bar the $p^\theta$ factors disappear.
- The exponents are the stoichiometric coefficients.
- $K^\theta$ depends on temperature only; data book Table 5 lists $\ln K^\theta$.
- Partial pressures come from Dalton's law (W02), $p_i=y_ip=(n_i/n)p$.

How it behaves: start with only A and B and the numerator is zero; as products form, the numerator grows and the denominator shrinks until the ratio reaches $K^\theta$ (27 Feb, ll. 162–170).

Method (notes §5.5.3):

1. Write the global reaction with unknown product moles.
2. Use atom balances to reduce to one unknown.
3. Look up $\ln K^\theta$ at the temperature, for the reaction written in the same direction as in the table.
4. Substitute $p_i=(n_i/n)p$, with $n$ the total moles of products.
5. Solve numerically; keep the root with all $n_i>0$.

### Worked example – CO equilibrium at 2600 K and 3 bar

Notes §5.5.3: start with 2 kmol CO and 3 kmol O₂; find the equilibrium composition at 2600 K and 3 bar.

**Step 1, global reaction:**

$$
\mathrm{2CO+3O_2\to a\,CO+b\,O_2+c\,CO_2}
$$

**Step 2, atom balances:**

$$
\text{C: } 2 = a+c\quad\Rightarrow\quad a = 2-c
$$

$$
\text{O: } 2+6 = a+2b+2c\quad\Rightarrow\quad b = 3-\tfrac12c
$$

Total moles: $n=a+b+c=5-\tfrac12c$.

Step 3, equilibrium constant for $\mathrm{CO+\tfrac12O_2\rightleftharpoons CO_2}$ at 2600 K: $\ln K^\theta=2.800$, $K^\theta=16.445$, and

$$
K^\theta = \frac{p_{CO_2}}{p_{CO}\,p_{O_2}^{1/2}}
$$

Step 4, substitute $p_i=(n_i/n)p$:

$$
K^\theta = \frac{(c/n)p}{(a/n)p\,\big[(b/n)p\big]^{1/2}} = \frac{c}{a\,b^{1/2}}\left(\frac{n}{p}\right)^{1/2}
$$

$$
16.445 = \frac{c}{(2-c)(3-c/2)^{1/2}}\left(\frac{5-c/2}{3}\right)^{1/2}
$$

**Step 5, solve:** $c=1.906$, so $a=0.094$ and $b=2.047$, $n=4.047$:

| Species | kmol | Mole (volume) fraction |
|---|---|---|
| CO | 0.094 | 2.3 % |
| O₂ | 2.047 | 50.6 % |
| CO₂ | 1.906 | 47.1 % |

> [!check] Le Chatelier check
> Raise the pressure to 30 bar and the same equation gives $c=1.969$: CO falls to 0.8 %. Higher pressure suppresses dissociation, as predicted.

### Worked example – carbon in pure oxygen at φ = 0.25

The lecture example (27 Feb, ll. 191–244): carbon burns in pure O₂ at $\phi=0.25$; the products CO, CO₂ and O₂ are at 3000 K and 2 bar. Find the volume fraction of CO.

**Air–fuel ratio.** Stoichiometric $\mathrm{C+O_2\to CO_2}$ gives $AFR_{st}=32/12$; at $\phi=0.25$ the oxygen is quadrupled, $AFR=4\times32/12$, so

$$
\mathrm{C+4O_2\to a\,CO+b\,O_2+c\,CO_2}
$$

**Atom balances:**

$$
\text{C: } 1 = a+c\quad\Rightarrow\quad c = 1-a
$$

$$
\text{O: } 8 = a+2b+2c\quad\Rightarrow\quad b = \frac{8-a-2(1-a)}{2} = 3+\frac a2
$$

Total moles: $n=a+b+c=4+a/2$.

Equilibrium ($\mathrm{CO+\tfrac12O_2\rightleftharpoons CO_2}$, 3000 K): $\ln K^\theta=1.110$, $K^\theta=3.034$:

$$
3.034 = \frac{1-a}{a\,(3+a/2)^{1/2}}\left(\frac{4+a/2}{2}\right)^{1/2}
$$

Cleared of fractions this is a cubic in $a$; its roots are two negative values and $a=0.211$ (27 Feb, ll. 238–241). Keep the positive one:

$$
a = 0.211,\qquad c = 0.789,\qquad b = 3.106,\qquad n = 4.106
$$

$$
y_{CO} = \frac{0.211}{4.106} = 5.1\ \%
$$

![[prop_equilibrium_co.png|640]]

> [!warning] Transcript slips in this example (27 Feb, ll. 192, 223–224, 236)
> - l. 192: "carbon that burns with pure hydrogen". It burns in pure oxygen.
> - ll. 223–224: the lecturer notes that the slide's equilibrium expression is mislabelled; it is the CO + ½O₂ ⇌ CO₂ reaction.
> - l. 236: "the value that we read is 1.11": that is $\ln K^\theta$, so $K^\theta=e^{1.11}=3.034$.

> [!warning] Transcript slip (27 Feb, l. 49)
> In the lean methane example: "we have some remaining hydrogen that do not participate". It is excess oxygen that remains.

---

## 4. Problem-solving workflow

1. Write the fuel's formula and the air as $(\mathrm{O_2}+3.762\mathrm{N_2^*})$. Balance C, H, O per kmol of fuel.
2. $AFR_{st}$ from masses; $\phi$ or $AFR$ from the question; extra O₂ (lean) or unburned fuel (rich) in the products.
3. Mixture $c_p$ by mass weighting (reactants and products separately).
4. Flame temperature: the three-step balance through 298 K. Burner design: solve the same balance for $f$.
5. Equilibrium: unknowns → atom balances → $K^\theta$ with $p_i=(n_i/n)p$ in bar → positive root → mole fractions.
6. Check: atoms balance; $T_2$ is a few thousand kelvin at most; Le Chatelier trends point the right way.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| air–fuel ratio $AFR$ | A/F | notes §5.3.2 | Mass basis. $f=1/AFR$ is the fuel–air ratio of W01. |
| equivalence ratio $\phi$ | — | notes §5.3.4 | Some texts define $\lambda=1/\phi$ (air excess ratio). |
| atmospheric nitrogen N₂* | — | data book, notes §5.3.2 | $M=28.15$ kg/kmol. |
| lower calorific value (LCV) | lower heating value (LHV), net calorific value | notes §5.4.1 | |
| higher calorific value (HCV) | higher heating value (HHV), gross calorific value | notes §5.4.1 | |
| formation enthalpy $h_f^\circ$ | standard enthalpy of formation | 24 Feb | |
| adiabatic flame temperature | — | notes §5.4.2 | |
| mole fraction $y_i$, mass fraction $x_i$ | $X_i$, $Y_i$ in combustion texts | 24 Feb, ll. 55–63 | "Some books call this the mole fraction X and mass fraction Y, so be careful." |
| equilibrium constant $K^\theta$ | $K_p$ | notes eq. 5.27 | Table 5 lists $\ln K^\theta$. |
| burner | combustor, combustion chamber | throughout | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]] · Next: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]
- Mixtures and Dalton's law: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency#2. Mixtures (Lecture 5)|W02 §2]]
- Worked sheet: [[SESA2023 Problem Sheet 5 Solutions]] (propane, flame temperature, NO equilibrium) · Formula list: [[SESA2023 Formula Sheet]]
- Exams: [[SESA2023 Exam 2013-14 Solutions]] Q4 (H₂O dissociation), [[SESA2023 Exam 2021-22 Solutions]] Q2(vi) (kerosene products), [[SESA2023 Exam 2023-24 Solutions]] Q1 (propane ramjet), [[SESA2023 Exam 2022-23 Solutions]] Q3(iv) (combustor with heat loss)
- Rocket propellants and $T_c$: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]

## Sources

- `Week 05 - Combustion.pdf`: Week 5 notes (I. Peters, T. Grenga) §§5.3–5.5 and the Lecture 13–15 slides.
- Transcripts (line numbers refer to these files): `SESA2023 Lecture 2026-02-24.txt` (24 Feb, Lectures 13–14: chemistry, AFR, $\phi$, calorific value, flame temperature); `SESA2023 Lecture 2026-02-27.txt` (27 Feb, Lecture 15: reversible reactions, Le Chatelier, equilibrium constants). L1 is `SESA2023 Lecture 1.txt`.
- Data book: Table 1 (calorific values), Table 2 (molar masses, $c_p$), Table 4 (reaction enthalpies), Table 5 ($\ln K^\theta$).

## Self-study tasks

Tasks marked *(set)* were set or explicitly worked in the Week 5 lectures; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Balance CH₄ in O₂ and in air by both methods; find $AFR_{st}=17.24$ (24 Feb, ll. 196–300). → [[#Combustion in air]] · [[#Air–fuel ratio]]
- [ ] *(set)* Methane at $\phi=0.5$ (24 Feb, ll. 342–354). Target $AFR=34.48$. → [[#Worked example – methane at φ = 0.5]]
- [ ] *(set)* Stoichiometric methane flame temperature with reactants at 400 K, including checking $c_{p,r}=1072$ and $c_{p,p}=1116$ from the data book as the lecturer did (24 Feb, ll. 480–508). Target 2853 K. → [[#Worked example – stoichiometric methane flame temperature]]
- [ ] *(set)* Carbon in pure O₂ at $\phi=0.25$, 3000 K, 2 bar (27 Feb, ll. 191–244). Target 5.1 % CO. → [[#Worked example – carbon in pure oxygen at φ = 0.25]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 5 Solutions|Problem Sheet 5]] (propane combustion, flame temperature, NO equilibrium) and the Week 5 Blackboard quiz (27 Feb, l. 9).

### Further practice

- [ ] Kerosene at $\phi=0.2$: balance, $AFR_{st}$ and $f_{st}$. Targets 14.9, 0.067. → [[#Worked example – kerosene at φ = 0.2]]
- [ ] Derive the boxed flame-temperature formula from the three-step path. → [[#Steady-flow adiabatic combustion: the three-step path]]
- [ ] Derive the gas-turbine fuel–air-ratio formula and evaluate it for $T_{03}=800$ K, $T_{04}=1600$ K. Target $f=0.0239$. → [[#The same balance in gas-turbine form]]
- [ ] CO equilibrium at 2600 K and 3 bar, then at 30 bar; explain the change with Le Chatelier. Targets 2.3 % and 0.8 % CO. → [[#Worked example – CO equilibrium at 2600 K and 3 bar]]
- [ ] Sketch the $h$–$T$ diagram with the adiabatic, isothermal and three-step paths. → [[#Two model processes]]
- [ ] *(set)* Install GasTurb for the propulsion lab and read the lab quiz (24 Feb, ll. 19–27); it draws on W06–W07.
