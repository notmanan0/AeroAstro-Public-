---
title: "SESA2023 W01 - Thrust, Efficiency, Range and the ISA"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 1: Introduction and Fundamentals"
order: 1
tags:
  - sesa2023
  - thrust
  - efficiency
  - breguet-range
  - isa
aliases: ["Propulsion fundamentals", "Thrust and efficiency", "SESA2023 Week 1"]
date: 2026-09-24
status: lectured
coverage: "Week 1 (Lectures 1–3)"
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA1016 T12 - Conservation of Momentum]]", "[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
next_topics: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
key_concepts: ["[[Thrust Equation]]", "[[Propulsive Efficiency]]", "[[Thermal and Overall Efficiency]]", "[[Thrust Specific Fuel Consumption]]", "[[Breguet Range Equation]]", "[[International Standard Atmosphere]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 1 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf", "02 - Sources/Lectures/SESA2023 Lecture 1.txt", "02 - Sources/Lectures/SESA2023 Lecture 2.txt", "02 - Sources/Lectures/SESA2023 Lecture 2026-01-30.txt", "02 - Sources/Data Book.pdf"]
---

# SESA2023 W01 - Thrust, Efficiency, Range and the ISA

> [!abstract] Summary
> Thrust comes from a momentum balance on a control volume: a rocket expels only what it carries, while an air-breather also pays ram drag $\dot m_aV_0$ on the air it captures. The conversion of fuel into useful work splits into thermal efficiency (heat to jet kinetic energy) and propulsive efficiency (jet kinetic energy to aircraft power $FV_0$), whose product, the overall efficiency, fixes the TSFC. TSFC, $L/D$ and the fuel fraction then set the Breguet range, with the engine inlet conditions at altitude taken from the International Standard Atmosphere.

> [!summary]- Exam use: quick path
> - **Use it when:** you are asked for thrust, fuel flow, $f$, TSFC, an efficiency or a cruise range, or for $p$, $T$, $\rho$ at a flight altitude.
> - **Assumptions:** steady flow in the engine's frame; uniform jet; CV boundaries drawn where $p=P_A$. The simplified forms need a fully expanded jet ($P_j=P_A$) and $f\ll1$. Breguet needs steady level cruise with constant $V_0$, $L/D$ and TSFC.
> - **Method:** 1. Get $V_0$ from $M_0\sqrt{\gamma RT}$ with $T$ from the ISA table. 2. Thrust $F=\dot m_a[(1+f)V_j-V_0]+A_j(P_j-P_A)$. 3. $\dot m_f=f\dot m_a$ and TSFC $=\dot m_f/F$. 4. $\eta_P$, $\eta_{th}$, $\eta_O=FV_0/(\dot m_f\,LCV)$; check $\eta_O=\eta_P\eta_{th}$. 5. Range $s=\frac{L}{D}\frac{V_0}{g_0\,\mathrm{TSFC}}\ln\frac{W_1}{W_2}$.
> - **Common mistakes:** forgetting the ram-drag term $-\dot m_aV_0$ (that is rocket thrust, not jet thrust); putting the end weight on top of the logarithm without the minus sign, which gives a negative range.
> - **Practise:** [[#Worked example – Boeing 777 cruise efficiencies]] · [[SESA2023 Problem Sheet 1 Solutions]] Q1.2–Q1.3

An aircraft in flight has nothing solid to push against. All it can do is throw gas backwards and feel the reaction (Lecture 1, ll. 304–316).

Thrust comes from a momentum balance: the momentum per second leaving the engine minus the momentum per second entering it is the force. A rocket's propellant starts at rest in the rocket's frame, so all of the momentum out is thrust; a jet engine has to swallow air that is already arriving at $V_0$, so it only gets credit for the increase in momentum. Every kilogram of air does two jobs (L1, ll. 343–348): it is the oxidiser that burns the fuel and the propellant that gets accelerated. The air flow is about 500 times the fuel flow (ll. 363–364), so the thrust comes almost entirely from accelerating air.

Energy is lost in two stages: the engine first turns the fuel's chemical energy into jet kinetic energy, which is the thermal efficiency, and then only part of that kinetic energy does work on the aircraft, because the jet leaves with leftover speed relative to the ground, which is the propulsive efficiency. That leftover speed is wasted, so a slow jet is efficient, but a slow jet gives little thrust per kilogram. The way out of this propulsive dilemma is to accelerate a lot of air a little, hence today's very large fans.

Range is efficiency integrated over a flight. As fuel burns the aircraft gets lighter, so it needs less lift, less drag, less thrust and less fuel, and that feedback makes the range depend on the logarithm of the weight ratio.

---

## 1. Module map (Lecture 1)

| Section | Weeks | Lecturer |
|---|---|---|
| Fundamentals: thermodynamics, gas dynamics | 1–4 | T. Grenga |
| Combustion | 5 | T. Grenga |
| Ramjets, gas turbines, turbojets, turbofans | 6–7 | E. Richardson |
| Turbomachinery (and propellers) | 8–9 | E. Richardson |
| Rockets | 10–11 | T. Grenga (with E. Richardson) |

**Assessment:** 80 % sit-down, closed-book exam in May with the data book provided, and 20 % coursework. The coursework is three summative Blackboard quizzes (3 % each) and two lab quizzes (nozzle lab and propulsion/ramjet lab, 5.5 % each). Lab attendance is mandatory (L3, ll. 11–22).

> [!warning] Transcript slip (L1, ll. 53–54)
> The lecturer says the courseworks add up to 20 % and "the remaining 20 is a in-person written exam". The exam is 80 % (slide 3, "Exam (80%)").

Two families of propulsion (L1, ll. 325–370):

- Rocket (non-air-breathing): carries fuel and oxidiser (or a monopropellant such as hydrogen peroxide, or an inert gas for electric propulsion). No momentum comes in, so all the momentum out is thrust. The drawback is that the oxidiser has to be carried too.
- **Air-breathing**: captures air (free oxidiser and working fluid) and carries only fuel. The penalty is the ram drag $\dot m_aV_0$ of the captured air.

The lecturer cares about jet speed for a second reason too (L1, ll. 435–442). Large fans accelerate a large mass of air by a small amount, and besides the better propulsive efficiency a slower jet is much quieter: jet noise scales roughly with $V_j^{\,7}$, "jet velocity power of seven" in the lecture, while the Weeks 6–7 handout says the eighth power ([[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection#Noise|W07]]).

---

## 2. Thrust from momentum conservation

The course starts from the steady control-volume momentum equation in the $x$-direction (notes eq. 1.1):

$$
\dot M_{x,out}-\dot M_{x,in} = \sum F_x
$$

### Choosing the control volume

"There's a bit of art and foresight in how you define your control volume" (L2, ll. 17–19). Every control volume gives the right answer, but the convenient one is drawn:

- in the engine's frame, so the thrust $F$ is the force needed to hold the engine (and CV) still;
- with side boundaries along stream tubes, so no mass crosses them;
- with the upstream and downstream faces far enough away that the streamlines are parallel. Parallel streamlines mean no pressure gradient across them, so the pressure there is atmospheric, $P_A$ (L2, ll. 131–147).

Then the atmospheric pressure acts on a closed surface and cancels everywhere except on the part of the exit plane occupied by the jet, of area $A_j$, where the jet pressure $P_j$ may differ from $P_A$.

### Rocket

Assume a static test stand, a uniform exhaust velocity $V_j$ relative to the rocket, and exhaust mass flow $\dot m=\dot m_{fuel}+\dot m_{ox}$ (combustion does not create or destroy mass, L2, ll. 74–76).

1. There is no inlet, so

$$
\dot M_{x,in} = 0
$$

2. The momentum flux out is mass flow times velocity:

$$
\dot M_{x,out} = \dot mV_j
$$

3. Forces in $+x$ (the jet direction): atmospheric pressure on the upstream face pushes in $+x$; the jet pressure on the exit plane pushes in $-x$ on the CV; the stand force $F$ holds the rocket. Over the closed surface the atmospheric parts cancel except over $A_j$, leaving

$$
\sum F_x = P_AA_j-P_jA_j+F
$$

4. Substitute into the momentum balance:

$$
\dot mV_j-0 = P_AA_j-P_jA_j+F
$$

5. Solve for $F$:

$$
\boxed{F = \dot mV_j+A_j(P_j-P_A)}
$$

$\dot mV_j$ is the momentum thrust and $A_j(P_j-P_A)$ the pressure thrust.

A rocket with a supersonic exit flow doesn't know what the ambient pressure is (L2, ll. 94–101). Pressure information can't travel upstream into the nozzle, so $\dot m$, $V_j$ and $P_j$ are fixed by the chamber and the nozzle alone, and only the pressure-thrust term changes with altitude, through $P_A$. That is why a sea-level static test is valid for predicting the thrust in vacuum.

> [!example] Rocket thrust rises with altitude ([[SESA2023 Problem Sheet 1 Solutions]] Q1.1)
> A rocket gives 2000 kN fully expanded at sea level ($P_j=P_A=101.325$ kPa). With the same exit state in vacuum ($P_A=0$) it gains $A_jP_j$, and the thrust becomes 2318 kN. The worked solution gets $A_j$ from $\dot m=\rho_eV_jA_j$.

### Jet engine

Two differences from the rocket (notes §1.2.2): air enters the CV, and the exit mass flow is larger than the inlet mass flow because fuel is added.

1. Air enters at the flight speed $V_0$ (in the engine's frame, all of the upstream air moves at $V_0$, L2, ll. 162–167):

$$
\dot M_{x,in} = \dot m_aV_0
$$

2. Air plus fuel leave at $V_j$:

$$
\dot M_{x,out} = (\dot m_a+\dot m_f)V_j
$$

3. The pressure forces are the same as for the rocket, so

$$
(\dot m_a+\dot m_f)V_j-\dot m_aV_0 = P_AA_j-P_jA_j+F
$$

4. Solve for $F$:

$$
F = (\dot m_a+\dot m_f)V_j-\dot m_aV_0+A_j(P_j-P_A)
$$

5. Introduce the fuel–air ratio $f=\dot m_f/\dot m_a$, so $\dot m_a+\dot m_f=\dot m_a(1+f)$:

$$
\boxed{F = \dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A)}
$$

| Term | Name | Meaning |
|---|---|---|
| $\dot m_a(1+f)V_j$ | gross (momentum) thrust | momentum per second thrown out |
| $-\dot m_aV_0$ | ram drag | momentum per second the captured air already had |
| $A_j(P_j-P_A)$ | pressure thrust | zero when the jet is fully expanded |

With a fully expanded jet ($P_j=P_A$) and $f\ll1$ (notes eq. 1.30):

$$
F = \dot m_a(V_j-V_0)
$$

> [!warning] The simplification needs both conditions
> $f\ll1$ alone does not remove the pressure term; $P_j=P_A$ alone does not remove the $(1+f)$. For a large civil turbofan $f\approx1/500$ (L2, ll. 151–153), so dropping $f$ costs about 0.2 % in thrust. For an under-expanded supersonic jet the pressure term can be several per cent, and you must keep it.

The stream tube splays out in front of the engine because the fan face can only accept subsonic flow, roughly Mach 0.6, even in flight at Mach 1.8 (L2, ll. 119–131). The transcript's "Mach 1.6" is almost certainly a mis-transcription, since the lecturer goes on to say that anything faster would bring shocks into the fan. The air therefore decelerates, and its pressure rises, before it reaches the engine, so the local pressure at the intake lip isn't $P_A$, which is why the control volume's inlet face is drawn far upstream.

---

## 3. Breguet range equation (Lecture 2)

### Assumptions

Steady, level cruise at constant $V_0$ and altitude; constant $L/D$ (the airframe flies at a fixed angle of attack, typically $L/D\approx20$–22, L2, ll. 199–203); constant TSFC; climb and descent ignored (L2, ll. 247–251).

### Derivation (one move per line)

Force balance in cruise: thrust equals drag and lift equals weight,

$$
F = D,\qquad L = W
$$

Multiply $W=L$ by $D/D=1$ and replace $D$ by $F$:

$$
W = D\,\frac{L}{D} = F\,\frac{L}{D}
$$

The aircraft loses weight at the rate fuel is burned:

$$
\frac{dW}{dt} = -\dot m_fg_0
$$

Define the thrust specific fuel consumption (notes eq. 1.13):

$$
\mathrm{TSFC} = \frac{\dot m_f}{F}
$$

Substitute $\dot m_f=\mathrm{TSFC}\cdot F$:

$$
\frac{dW}{dt} = -g_0\,\mathrm{TSFC}\,F
$$

Substitute $F=W/(L/D)$:

$$
\frac{dW}{dt} = -\frac{g_0\,\mathrm{TSFC}}{L/D}\,W
$$

Separate the variables (multiply by $dt$, divide by $W$):

$$
\frac{dW}{W} = -\frac{g_0\,\mathrm{TSFC}}{L/D}\,dt
$$

Change from time to distance with $ds=V_0\,dt$:

$$
\frac{dW}{W} = -\frac{g_0\,\mathrm{TSFC}}{V_0\,(L/D)}\,ds
$$

Integrate from the start of cruise ($s=0$, $W=W_1$) to the end ($s$, $W=W_2$). Everything on the right is constant:

$$
\int_{W_1}^{W_2}\frac{dW}{W} = -\frac{g_0\,\mathrm{TSFC}}{V_0\,(L/D)}\int_0^s ds
$$

$$
\ln\frac{W_2}{W_1} = -\frac{g_0\,\mathrm{TSFC}}{V_0\,(L/D)}\,s
$$

Solve for $s$ (the course form, notes eq. 1.20, has the minus sign):

$$
s = -\frac{L}{D}\,\frac{V_0}{g_0\,\mathrm{TSFC}}\ln\frac{W_2}{W_1}
$$

Since $-\ln(W_2/W_1)=\ln(W_1/W_2)$:

$$
\boxed{s = \frac{L}{D}\,\frac{V_0}{g_0\,\mathrm{TSFC}}\ln\frac{W_1}{W_2}}\qquad\left(= \frac{C_L}{C_D}\frac{V_0}{g_0\,\mathrm{TSFC}}\ln\frac{W_1}{W_2}\right)
$$

Because $W_2<W_1$, the logarithm is positive in this form.

The range is a logarithm because the burn rate is proportional to the current weight (L2, ll. 204–209). At the start of cruise the aircraft is heavy, needs more lift, so more drag and more thrust, and burns fuel fast; near the end it is light and burns slowly. A rate proportional to the current amount is exponential decay, and its inverse is a logarithm.

### Range in terms of overall efficiency

From §4, $\eta_O=V_0/(\mathrm{TSFC}\cdot LCV)$, so

$$
\frac{V_0}{\mathrm{TSFC}} = \eta_O\,LCV
$$

and substituting into the boxed Breguet equation:

$$
\boxed{s = \eta_O\,\frac{LCV}{g_0}\,\frac{L}{D}\,\ln\frac{W_1}{W_2}}
$$

Range rises with high $\eta_O$ (engine), high $L/D$ (aerodynamics) and a high fuel fraction (structures). At fixed $V_0$ it is inversely proportional to TSFC. The derivation appears in the 2014-15, 2016-17 and 2023-24 papers. See [[Breguet Range Equation]].

### Worked example – Boeing 777-200 range

Lecture data (L2, ll. 252–340): MTOW 243 t, fuel burned 42 t, $V_0=248$ m/s (M 0.84), $L/D=20$, TSFC $=1.614\times10^{-5}$ kg s⁻¹ N⁻¹, $g_0=9.81$ m s⁻². Take $W_1$ as MTOW (neglecting climb fuel) and $W_2=243-42=201$ t (neglecting descent fuel):

$$
\frac{V_0}{g_0\,\mathrm{TSFC}} = \frac{248}{9.81\times1.614\times10^{-5}} = 1.566\times10^{6}\ \mathrm m
$$

$$
\ln\frac{243}{201} = 0.1898
$$

$$
s = 20\times1.566\times10^{6}\times0.1898 = 5.94\times10^{6}\ \mathrm m = 5944\ \mathrm{km}
$$

The published range at maximum payload (R1) is 6112 km.

> [!check] Numerical checks
> - Recomputed: $s=5944$ km, matching the lecturer's "5945" (L2, l. 340).
> - The flight speed: at 35,000 ft the data book gives $T=218.81$ K, so $a=\sqrt{1.4\times287\times218.81}=296.5$ m/s and $V_0=0.84\times296.5=249$ m/s. The lecturer's 248 m/s is the same to the precision of the inputs.
> - The implied overall efficiency is $\eta_O=V_0/(\mathrm{TSFC}\cdot LCV)=248/(1.614\times10^{-5}\times44.65\times10^{6})=0.34$, inside the 0.3–0.4 band quoted for current engines.

> [!warning] Transcript slips and loose ends in the 777 example
> - L2, l. 307: "It comes out from memory at about 590 kilometers". The answer is about 5900 km; the lecturer corrects himself at l. 309.
> - The "mysterious 11 tons" (L2, ll. 319–339): empty mass 136 t + maximum payload 54.6 t + fuel burned 42 t is 232.6 t, which is 10.4 t short of the 243 t MTOW. The missing mass is reserve fuel, which is carried but not burned, as a student pointed out. Strictly, $W_2$ still includes the reserve, so the calculation above is unchanged.
> - L2, ll. 274–277: the TSFC was based on a two-significant-figure source, so quoting it to four figures is "a bit naughty". In the exam, give answers to sensible precision: here "about 5900 km".

Ignoring the climb and descent fuel ought to make the predicted range too long, because those phases burn fuel while covering little distance, yet the prediction comes out 3 % short (L2, ll. 312–317). With $L/D$ and TSFC known only to two figures ($L/D$ could be 19–21), a 3 % miss in either direction is within the input uncertainty.

---

## 4. Efficiencies (Lecture 3)

The energy chain is

$$
\underbrace{\dot Q_{in}=\dot m_f\,LCV}_{\text{fuel heat}}\ \xrightarrow{\ \eta_{th}\ }\ \underbrace{\dot W_{jet}}_{\text{jet KE rate}}\ \xrightarrow{\ \eta_P\ }\ \underbrace{\dot W_{aircraft}=FV_0}_{\text{aircraft power}}
$$

and the overall efficiency is the product (notes eq. 1.22):

$$
\eta_O = \eta_P\,\eta_{th}
$$

The LCV (lower calorific value) is the heat released per kilogram of fuel with the water in the products left as vapour (detailed in [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium|W05]]).

### Propulsive efficiency

Definition (notes eq. 1.23): aircraft power over the rate of increase of the working fluid's kinetic energy,

$$
\eta_P = \frac{\dot W_{aircraft}}{\dot W_{jet}}
$$

Aircraft power is thrust times flight speed:

$$
\dot W_{aircraft} = FV_0 = V_0\Big\{\dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A)\Big\}
$$

The kinetic-energy rate is what leaves minus what enters:

$$
\dot W_{jet} = \tfrac12(\dot m_a+\dot m_f)V_j^2-\tfrac12\dot m_aV_0^2 = \tfrac12\dot m_a\big[(1+f)V_j^2-V_0^2\big]
$$

Dividing gives the general form (notes eq. 1.27):

$$
\eta_P = \frac{V_0\Big\{\dot m_a\big[(1+f)V_j-V_0\big]+A_j(P_j-P_A)\Big\}}{\tfrac12\dot m_a\big[(1+f)V_j^2-V_0^2\big]}
$$

Simplification 1, fully expanded jet ($P_j=P_A$); $\dot m_a$ then cancels:

$$
\eta_P = \frac{V_0\big[(1+f)V_j-V_0\big]}{\tfrac12\big[(1+f)V_j^2-V_0^2\big]}
$$

**Simplification 2, $f\ll1$:**

$$
\eta_P = \frac{2V_0(V_j-V_0)}{V_j^2-V_0^2}
$$

Factorise the difference of squares, $V_j^2-V_0^2=(V_j-V_0)(V_j+V_0)$, and cancel $(V_j-V_0)$:

$$
\eta_P = \frac{2V_0}{V_j+V_0}
$$

Divide top and bottom by $V_0$:

$$
\boxed{\eta_P = \frac{2}{1+V_j/V_0}}
$$

![[prop_propulsive_efficiency.png|700]]

The wasted energy is the jet's kinetic energy in the ground frame. The jet leaves with speed $V_j-V_0$ and carries away $\tfrac12\dot m_a(V_j-V_0)^2$ per second, and indeed $\dot W_{jet}-FV_0=\tfrac12\dot m_a(V_j^2-V_0^2)-\dot m_a(V_j-V_0)V_0=\tfrac12\dot m_a(V_j-V_0)^2$. So $\eta_P<1$ is simply the kinetic energy left behind in the wake.

### Why not make the jet as slow as the aircraft

Lecture 3 (ll. 116–140) asks this directly. $\eta_P\to1$ as $V_j\to V_0$, but the simplified thrust $F=\dot m_a(V_j-V_0)\to0$. To keep $F$ as $V_j-V_0$ shrinks, $\dot m_a$ must grow. By continuity, $\dot m_a=\rho_0V_0A_0$ at the inlet face, so

$$
A_0 = \frac{\dot m_a}{\rho_0V_0}
$$

For a fixed thrust, $\dot m_a=F/(V_j-V_0)$, so

$$
A_0 = \frac{F}{\rho_0V_0\,(V_j-V_0)}
$$

The capture area, and so the engine diameter, grows without limit as $V_j\to V_0$. There is no room under the wing, and the nacelle drag and weight grow with it (L3, ll. 129–132; notes §1.4.1). The industry compromise is a large mass of air accelerated a little: hence the progression from the fanless Jumo 004 to the GE90 (L3, ll. 132–140). This is the basis of the turbofan in [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection|W07]].

### Overall and thermal efficiency

Overall efficiency (notes eq. 1.31): aircraft power over fuel heat,

$$
\eta_O = \frac{FV_0}{\dot m_f\,LCV}
$$

With $P_j=P_A$ and $f\ll1$, $F=\dot m_a(V_j-V_0)$:

$$
\eta_O = \frac{\dot m_a(V_j-V_0)V_0}{\dot m_f\,LCV}
$$

Divide top and bottom by $\dot m_a$ and use $f=\dot m_f/\dot m_a$:

$$
\eta_O = \frac{(V_j-V_0)V_0}{f\,LCV}
$$

Alternatively, write $F/\dot m_f=1/\mathrm{TSFC}$ in the definition (notes eq. 1.33):

$$
\boxed{\eta_O = \frac{V_0}{\mathrm{TSFC}\cdot LCV}}
$$

The LCV is fixed once the fuel is chosen; TSFC is what the engine designer can improve (L3, ll. 187–188).

Thermal efficiency (notes eq. 1.34): jet kinetic-energy rate over fuel heat, with $f\ll1$,

$$
\eta_{th} = \frac{\dot W_{jet}}{\dot Q_{in}} = \frac{\tfrac12\dot m_a(V_j^2-V_0^2)}{\dot m_f\,LCV} = \frac{V_j^2-V_0^2}{2f\,LCV}
$$

Check that $\eta_P\eta_{th}=\eta_O$ (the notes say "You can verify that…"):

$$
\eta_P\eta_{th} = \frac{2V_0(V_j-V_0)}{V_j^2-V_0^2}\times\frac{V_j^2-V_0^2}{2f\,LCV}
$$

$$
\eta_P\eta_{th} = \frac{V_0(V_j-V_0)}{f\,LCV} = \eta_O\quad\checkmark
$$

| Efficiency | General definition | Simplified ($P_j=P_A$, $f\ll1$) |
|---|---|---|
| Propulsive | $\eta_P=\dfrac{FV_0}{\tfrac12\dot m_a[(1+f)V_j^2-V_0^2]}$ | $\dfrac{2}{1+V_j/V_0}$ |
| Thermal | $\eta_{th}=\dfrac{\tfrac12\dot m_a[(1+f)V_j^2-V_0^2]}{\dot m_f\,LCV}$ | $\dfrac{V_j^2-V_0^2}{2f\,LCV}$ |
| Overall | $\eta_O=\dfrac{FV_0}{\dot m_f\,LCV}$ | $\dfrac{V_0(V_j-V_0)}{f\,LCV}=\dfrac{V_0}{\mathrm{TSFC}\cdot LCV}$ |

### Raising the thermal efficiency

From L3, ll. 158–224. For an ideal Brayton cycle (SESA1016, revisited in [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat|W06]]) the thermal efficiency rises with the overall pressure ratio, the ratio between the combustor pressure (set by the compressor) and the ambient pressure (set by the altitude). It also rises with the turbine entry temperature (TET).

- Pressure ratios rose from about 15 to over 40 in about 40 years.
- TET rose from about 1000 K to nearly 1800 K, above the blade material limit, thanks to cooled blades (internal passages fed with cooler compressor air, from the 1960s) and thermal barrier coatings (later).
- Current engines: $\eta_P\approx0.6$–0.7 and $\eta_{th}\approx0.5$–0.6, so $\eta_O\approx0.3$–0.4.

The turbine entry, not the combustor, sets the temperature limit (L3, ll. 207–220). A combustor liner is stationary and can be cooled, so it survives gas above 2000 K, but a turbine blade carries a huge centrifugal load while spinning at thousands of rpm and creeps at high temperature. The first turbine stage is therefore the weakest point, and its entry temperature caps the whole cycle.

### Worked example – Boeing 777 cruise efficiencies

Lecture data (L3, ll. 226–257): $\dot m_a=1295$ kg/s, $V_0=251$ m/s, $V_j=299$ m/s, $\dot m_f=0.58$ kg/s, $LCV=44.65$ MJ/kg. Assume a fully expanded jet.

Thrust ($f\ll1$):

$$
F = 1295\times(299-251) = 62.2\ \mathrm{kN}
$$

**Fuel–air ratio:**

$$
f = \frac{0.58}{1295} = 4.48\times10^{-4}\ll1
$$

so the simplified efficiencies are justified.

**Propulsive efficiency:**

$$
\eta_P = \frac{2}{1+299/251} = 0.913
$$

**Thermal efficiency:**

$$
\eta_{th} = \frac{299^2-251^2}{2\times4.48\times10^{-4}\times44.65\times10^{6}} = \frac{26\,400}{40\,000} = 0.660
$$

**Overall efficiency:**

$$
\eta_O = \frac{FV_0}{\dot m_f\,LCV} = \frac{62\,160\times251}{0.58\times44.65\times10^{6}} = 0.602
$$

and $\eta_P\eta_{th}=0.913\times0.660=0.602$ ✔.

> [!check] How good is the simplified $\eta_P$, and how realistic are these numbers?
> - Keeping $f$ in the fully expanded form gives $\eta_P=0.914$ instead of $0.913$, a 0.1 % difference. (Problem Sheet 1 Q1.4 explores this error in general.)
> - The implied TSFC is $0.58/62\,160=9.3\times10^{-6}$ kg s⁻¹ N⁻¹, much lower than the $1.614\times10^{-5}$ used for the same aircraft in Lecture 2. That is why $\eta_O$ comes out at 60 % here but 34 % from the Lecture 2 TSFC. The slide's fuel flow and jet velocity are illustrative; a real cruise $\eta_O$ is about 35 %.

---

## 5. International Standard Atmosphere

The ISA gives reference values of pressure, temperature and density against altitude. The data book (Tables 24 and 25), which you get in the exam, gives ratios to the sea-level values (notes eqs. 1.35–1.37):

$$
\delta = \frac{P}{P_{ref}},\qquad \theta = \frac{T}{T_{ref}},\qquad \sigma = \frac{\rho}{\rho_{ref}}
$$

with $P_{ref}=101.325$ kPa, $T_{ref}=288.15$ K and $\rho_{ref}=1.225$ kg/m³. Table 24 lists selected cruise altitudes in feet; Table 25 lists every 1000 m.

- Troposphere (0–11 km): $T$ falls linearly, $T=288.15-6.5h$ with $h$ in km.
- Lower stratosphere (11–20 km): $T=216.65$ K, constant. Pressure falls exponentially.

![[prop_isa.png|640]]

### Where the table comes from (beyond the lecture)

The lecture uses the tables only, but the shape of the pressure curve follows from two lines of physics. Hydrostatic balance and the perfect-gas law:

$$
\frac{dP}{dh} = -\rho g,\qquad \rho = \frac{P}{RT}
$$

Eliminate $\rho$:

$$
\frac{dP}{P} = -\frac{g}{RT}\,dh
$$

Troposphere, $T=T_{ref}-Lh$ with lapse rate $L=6.5$ K/km, so $dh=-dT/L$:

$$
\frac{dP}{P} = \frac{g}{RL}\,\frac{dT}{T}
$$

Integrate from sea level:

$$
\frac{P}{P_{ref}} = \left(\frac{T}{T_{ref}}\right)^{g/(RL)},\qquad \frac{g}{RL} = \frac{9.80665}{287.05\times0.0065} = 5.256
$$

Stratosphere, $T=T_{11}=216.65$ K constant:

$$
\frac{P}{P_{11}} = \exp\!\left[-\frac{g\,(h-h_{11})}{RT_{11}}\right]
$$

> [!check] Formula against the data book
> - 10 km: the formula gives $T=223.15$ K and $P=26.44$ kPa. Table 25 gives $\theta=0.7748$ ($T=223.26$ K) and $\delta=0.2615$ ($P=26.50$ kPa). Agreement to 0.2 %.
> - 20 km: the formula gives 5.47 kPa; Table 25 gives $\delta=0.0546$, i.e. 5.53 kPa (1 % higher).
> - **Use the data-book values in the exam.** Every worked answer in this vault uses them.

| Altitude | $T$ (K) | $p$ (kPa) | Used in |
|---|---|---|---|
| 2 km | 275.15 | 79.50 | PS2 Q2.3 |
| 6 km | 249.19 | 47.22 | intake exercise (W04) |
| 10 km | 223.26 | 26.50 | PS4 Q4.1 |
| 31,000 ft | 226.73 | 28.7 | turbojet worked example, 2020-21 Q3 |
| 35,000 ft | 218.81 | 23.8 | turbofan exercises (W07), 2020-21 Q4 |
| 15 km | 216.66 | 12.11 | 2024-25 Q1 |
| 20 km | 216.66 | 5.53 | 2021-22 Q2, 2023-24 Q1–Q2 |
| 51,000 ft | 216.65 | 11.1 | ramjet lecture example |

The lecturer's advice was to learn the data book now: "that data book is the same that is going to be provided to you at the exam… using that in a fast way will help you in the exam" (L3, ll. 262–271). Many of the module's equations are printed in it, so the exam tests understanding and use rather than recall.

See [[International Standard Atmosphere]].

---

## 6. Problem-solving workflow

1. Draw the CV: engine frame, stream-tube sides, inlet and exit faces where $p=P_A$. Label $V_0$, $V_j$, $\dot m_a$, $\dot m_f$, $A_j$, $P_j$.
2. Get the flight state from the ISA table, then $V_0=M_0\sqrt{\gamma RT}$.
3. Write the full thrust equation, then decide whether $P_j=P_A$ and $f\ll1$ apply. Say so.
4. Fuel flow, $f$ and TSFC from the given data; efficiencies from the definitions; check $\eta_O=\eta_P\eta_{th}$.
5. For range, identify $W_1$ and $W_2$ (what fuel is burned in cruise? is there reserve?) and use $\ln(W_1/W_2)>0$.
6. Sanity-check: $\eta_P<1$, $\eta_O\approx0.3$–0.4 for a modern engine, TSFC $\sim10^{-5}$ kg s⁻¹ N⁻¹, ranges of a few thousand km.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| fuel–air ratio $f$ | fuel-to-air ratio, FAR | notes eq. 1.9, all engine weeks | The notes once call it the "air-fuel ratio" (before eq. 1.26); it is $\dot m_f/\dot m_a$. AFR in W05 is its inverse. |
| TSFC | sfc, specific fuel consumption | notes eq. 1.13, L2 | US industry quotes lb/(lbf h); always convert to kg s⁻¹ N⁻¹ (L2, ll. 291–298). |
| fully expanded jet | ideally expanded, matched nozzle, design condition | notes §1.4.1 | $P_j=P_A$. |
| ram drag | inlet momentum drag, intake momentum drag | slides, L2 | $\dot m_aV_0$. |
| aircraft power $\dot W_{aircraft}$ | thrust power, propulsive power | notes eq. 1.23 | $FV_0$. |
| $\dot W_{jet}$ | jet power, rate of KE production | notes eq. 1.25 | |
| LCV | lower heating value, LHV, net calorific value | notes eq. 1.31, W05 | |
| turbine entry temperature (TET) | turbine inlet temperature (TIT), $T_{04}$ | L3, Fig. 1.4 | |
| range at maximum payload (R1) | harmonic range | L2, ll. 253–255 | |

## Links

- Parent: [[SESA2023 Propulsion Hub]] · Next: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]
- Thermofluids foundation: [[SESA1016 T12 - Conservation of Momentum]] · [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- Worked sheet: [[SESA2023 Problem Sheet 1 Solutions]] · Formula list: [[SESA2023 Formula Sheet]]
- Reused in every engine calculation: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · large fans: [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]
- Rocket thrust and pressure thrust return in [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]].

## Sources

- `Week 01 - Introduction and Fundamentals.pdf`: Week 1 notes (I. Peters, T. Grenga) §§1.2–1.5, Lectures 1–2 slides, and Mattingly, *Elements of Propulsion*, App. A altitude tables.
- Transcripts (line numbers refer to these files): L1 `SESA2023 Lecture 1.txt` (27 Jan, E. Richardson: module introduction, history); L2 `SESA2023 Lecture 2.txt` (27 Jan, E. Richardson: thrust, Breguet); L3 `SESA2023 Lecture 2026-01-30.txt` (30 Jan, T. Grenga: efficiencies, ISA).
- `Data Book.pdf`: ISA sea-level values and Tables 24–25.

## Self-study tasks

Tasks marked *(set)* were set or explicitly left to you in the Week 1 lectures or notes; the rest are suggested, not lecturer-set. Attempt each closed-book, then check against the linked section.

### Core

- [ ] *(set)* Derive the Breguet range equation from $F=D$, $L=W$ and the TSFC definition. "You need to know how to derive the [Breguet] range [equation]" (L2, ll. 341–342). → [[#Derivation (one move per line)]]
- [ ] *(set)* Compute the 777 range: "Maybe somebody quick with the calculator can tell us the answer" (L2, ll. 306–309). Target 5944 km. → [[#Worked example – Boeing 777-200 range]]
- [ ] *(set)* 777 cruise efficiencies exercise (L3, ll. 225–257). Targets $F=62.2$ kN, $\eta_P=0.91$, $\eta_{th}=0.66$, $\eta_O=0.60$. → [[#Worked example – Boeing 777 cruise efficiencies]]
- [ ] *(set)* Verify $\eta_P\eta_{th}=\eta_O$ with the simplified forms ("You can verify that…", notes after eq. 1.34). → [[#Overall and thermal efficiency]]
- [ ] *(set)* Work [[SESA2023 Problem Sheet 1 Solutions|Problem Sheet 1]] (thrust, efficiencies, range); the problem sheets are "more like the exam questions" (L1, ll. 62–63).

### Further practice

- [ ] *(set)* M 0.84 at 35,000 ft gives 248 m/s: "You'll be able to do that calculation Friday" (L2, ll. 264–267). → [[#Worked example – Boeing 777-200 range]]
- [ ] *(set)* Learn to find $T$, $p$, $\rho$ in data-book Tables 24 and 25 quickly (L3, ll. 262–271). → [[#5. International Standard Atmosphere]]
- [ ] *(set)* Blackboard Quiz 1 (L3, ll. 23–30): unlimited attempts, the last attempt is marked, save before closing.
- [ ] Derive the rocket and jet-engine thrust equations from a sketched CV, stating where $p=P_A$. → [[#2. Thrust from momentum conservation]]
- [ ] Derive $\eta_P=2/(1+V_j/V_0)$ from the general definition, stating each assumption. → [[#Propulsive efficiency]]
- [ ] Show that the kinetic energy wasted in the wake is $\tfrac12\dot m_a(V_j-V_0)^2$. → [[#Propulsive efficiency]]
- [ ] Explain, with the capture-area result, why $V_j=V_0$ is not used. → [[#Why not make the jet as slow as the aircraft]]
- [ ] Resolve the "missing 11 tonnes" of the 777 data. → [[#Worked example – Boeing 777-200 range]]
- [ ] *(Optional, beyond the lecture)* Derive the troposphere law $P/P_{ref}=(T/T_{ref})^{5.256}$. → [[#Where the table comes from (beyond the lecture)]]
