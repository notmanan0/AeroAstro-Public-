---
title: "SESA2023 Exam 2015-16 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2015-16"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-201516-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2015-16 Solutions

> [!info] Paper
> 120 min, closed book. Answer Q1 and **any two** of Q2–Q4 (30 marks each). Air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$.

## Q1: Gas-turbine design

### (i) Radial vs axial compressors (3)

| | Radial (centrifugal) | Axial |
|---|---|---|
| Pressure ratio per stage | High (4–8) | Low (1.1–1.6) |
| Frontal area per unit flow | Large | Small, so low drag |
| Efficiency | ≈ 80–85 % | ≈ 88–92 % |
| Robustness and cost | Rugged (FOD tolerant), cheap, short | Many delicate blades, costly |
| Multi-staging | Awkward (return ducts) | Natural, so OPR 40+ |

Axials dominate large engines, where flow per unit area and efficiency matter. Radials suit small engines, APUs, helicopters and the last HP stage of small turbofans. See [[Specific Speed]].

### (ii) Mechanical arrangement and bearings (3)
- A single-spool turbojet's rotor is carried on **three bearings**:
  - a **thrust (ball) bearing** at the compressor end, carrying the net axial load and locating the shaft;
  - **roller bearings** at the compressor front and at the turbine, which carry radial loads and allow axial thermal growth.
- Multi-spool engines use concentric shafts, each with one ball (location) bearing and roller bearings, plus inter-shaft bearings.
- **Reasoning**:
  - The compressor pushes forward and the turbine pulls aft, so thrust loads partly cancel on a common shaft, and the ball bearing takes only the residual.
  - Only one bearing locates each shaft axially, so differential thermal expansion between the hot shaft and the casing is taken up by the rollers without large tip-clearance changes.
  - Bearings are kept away from the hottest sections where possible, and fed by oil in sealed and buffered sumps.

*(Sketch: shaft with ball bearing B1 ahead of the compressor, roller R1 behind the compressor, roller R2 behind the turbine.)*

### (iii) Surge and its mitigation (4)
**Surge** is a system-level instability. Mass flow falls at constant speed, blade incidence rises, and stall spreads (rotating stall cells). When the compressor can no longer sustain the pressure rise against the downstream volume, the whole flow breaks down and **reverses**. The result is violent axial oscillation, a bang, flame-out, possible over-temperature and blade damage.

Mitigation:
- **Variable inlet guide vanes and stators** re-set incidence at part speed.
- **Bleed valves** at intermediate stages dump air at low speed so the front stages see more flow.
- **Multiple spools** let each compressor run nearer its own optimum speed.
- **Casing treatment** (slots and grooves).
- **Fuel scheduling** limits acceleration so the operating line keeps a **surge margin**.
- Active control.

See [[Compressor Stall and Surge]].

### (iv) Propulsive efficiency derivation (10)
Control volume around the engine: air enters at $V$ with $\dot m_a$; fuel $\dot m_f = f\dot m_a$ enters with no axial momentum; the jet leaves at $V_j$ with pressure $P_j$ over $A_j$.

$$
F = \dot m_a[(1+f)V_j-V]+(P_j-P_{atm})A_j
$$

**Useful power** delivered to the aircraft is the thrust times flight speed, $FV$. **Power given to the gas stream** is its rate of increase of kinetic energy:

$$
\dot W_{KE} = \tfrac12(\dot m_a+\dot m_f)V_j^2-\tfrac12\dot m_aV^2 = \tfrac12\dot m_a[(1+f)V_j^2-V^2]
$$

Hence:

$$
\eta_p = \frac{FV}{\dot W_{KE}} = \frac{V\{\dot m_a[(1+f)V_j-V]+(P_j-P_{atm})A_j\}}{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}\;\blacksquare
$$

- **Numerator**: the thrust power, i.e. the rate of useful work on the aircraft.
- **Denominator**: the jet kinetic-energy production (the engine's "mechanical output").
- **Difference**: the KE lost in the wake. For $f\to0$ and $P_j = P_{atm}$ this gives $\eta_p = 2/(1+V_j/V)$. See [[Propulsive Efficiency]].

### (v) Civil turbofan vs military turbojet (10)
- $\eta_O = \eta_P\eta_{th}$.
  - $\eta_P = 2/(1+V_j/V)$ requires $V_j\to V$: a large mass flow with a small $\Delta V$.
  - $\eta_{th}$ requires a high OPR and TET.
  - Specific thrust $F/\dot m\approx V_j-V$ requires a *large* $\Delta V$.
- **Civil** (range, fuel cost, noise, emissions):
  - high bpr (8–12+), low fpr (1.4–1.6), $V_j\approx1.2$–$1.4V$, $\eta_P\approx0.8$;
  - OPR 40–50 and TET about 1700–1900 K for $\eta_{th}\approx0.5$;
  - a large fan diameter is acceptable at M 0.85 (and quieter);
  - the driver is minimum TSFC, since range ∝ 1/TSFC.
- **Military** (thrust/weight, thrust/frontal area, supersonic dash, manoeuvre):
  - low bpr (0–0.7) or pure turbojet, and reheat;
  - high $V_j$ matched to supersonic $V$, where $\eta_P$ is acceptable;
  - OPR about 25–35, chosen near maximum specific work;
  - a small diameter for low wave drag;
  - fuel efficiency at subsonic cruise is sacrificed.
- Diagram: $\eta_P$ against $V_j/V$ ([[Propulsive Efficiency]], `prop_propulsive_efficiency.png`) and Brayton $w_{net}$ and $\eta$ against $r_p$ (`prop_brayton_trends.png`). Maximum work and maximum efficiency occur at different $r_p$.

---

## Q2: Rocket propulsion

### (i) H₂/O₂ vs RP-1/O₂ (3)
- **H₂/LOX**: the lowest molar mass of products (about 10–13 kg/kmol, run fuel-rich) and high $T_c$ give the **highest $I_{sp}$** (about 450 s vacuum), because $c\propto\sqrt{T_c/\mathcal M}$. It is clean, and ideal as a coolant (expander cycles).
  - Drawbacks: extremely low density (71 kg/m³) means huge, heavy tanks, and high drag and structure mass for boosters; cryogenic at 20 K (boil-off, insulation, embrittlement); leaks; needs high pump tip speeds.
- **RP-1/LOX**: dense (about 810 kg/m³), storable at ambient temperature, compact and cheap tanks, high **density-impulse**, giving high thrust for boosters.
  - Drawbacks: lower $I_{sp}$ (about 300–350 s); soot and coking in cooling channels.

### (ii) Launch vehicle selection (4)
- Payload mass, and required orbit or $\Delta V$ (LEO, GTO, escape, inclination), including the launch site latitude.
- Performance margin.
- Reliability, heritage and insurance cost.
- Price per kg, and ride-share options.
- Fairing volume and interfaces.
- Environment: loads, acoustics, vibration, g-levels, thermal, cleanliness.
- Schedule and availability, and cadence.
- Injection accuracy.
- Political and export (ITAR) constraints.

### (iii) Why high $p_c$ and $T_c$? (5)
Assume ideal, isentropic, fully expanded flow of a perfect gas:

$$
I_{sp} = \frac1{g_0}\sqrt{\frac{2\gamma}{\gamma-1}\frac{\bar RT_c}{\mathcal M}\left[1-\left(\frac{p_e}{p_c}\right)^{\frac{\gamma-1}\gamma}\right]}
$$

- **$T_c$**: $I_{sp}\propto\sqrt{T_c/\mathcal M}$, so hotter, lighter products give a faster exhaust.
- **$p_c$**: for a given exit pressure (ambient), a larger $p_c/p_e$ makes the bracket approach 1, so more of the enthalpy is converted. High $p_c$ also suppresses dissociation (see [[Chemical Equilibrium and Dissociation]]), gives a smaller throat for a given thrust ($F = C_Fp_cA_t$), and allows higher expansion ratios in a compact nozzle.

### (iv) Turbopumps (9)
- Pumps raise the propellants from low tank pressure (2–5 bar, allowing thin, light tanks) to above $p_c$ (plus injector and cooling-jacket losses). A turbine on the same shaft drives them (or a gearbox, or separate shafts).
- **Common requirements**:
  - high power density (tens of MW in a small package);
  - cavitation avoidance (inducers, NPSH);
  - cryogenic bearings and seals, with seals between fuel and oxidiser;
  - fast start and shut-down transients;
  - rotor-dynamics;
  - H₂ pumps need very high tip speeds (multi-stage) because head is proportional to $U^2$ and the density is low.
- **Expander**:
  - The turbine is driven by heated fuel vapour at low temperature (about 200–600 K).
  - Available power is limited, so the turbine must be **highly efficient** with a low pressure ratio.
  - The environment is benign, and the life is long.
- **Gas generator**:
  - Turbine flow is dumped, so a **small flow at a high pressure ratio** (supersonic impulse turbines) is used, keeping the wasted propellant small. Turbine efficiency is less critical.
  - Hot gas (about 900 K, fuel-rich) risks coking with RP-1.
- **Staged combustion**:
  - The turbine flow is the whole of one propellant at high pressure, so a **large flow at a low pressure ratio**.
  - Pump discharge pressure is about 1.5–2 × $p_c$ (the pre-burner sits upstream of the chamber).
  - Turbines work in hot fuel-rich (hydrogen embrittlement) or **oxidiser-rich** gas (burning risk; special coatings and alloys).
  - Boost pumps are needed, and the rotor-dynamics are demanding.

### (v) RD-253 staged combustion (5)
- The RD-253 (Proton first stage) is **oxidiser-rich staged combustion** with storable hypergolic UDMH/N₂O₄.
- *Schematic*: N₂O₄ pump and UDMH pump on the shaft of a single turbine. **All** the N₂O₄ and a **small fraction** of the UDMH go to the pre-burner. Its oxidiser-rich gas (about 700–800 K) drives the turbine and then passes through the hot-gas duct into the main chamber. There it meets the remaining UDMH, which has cooled the chamber and nozzle regeneratively.
- **Philosophy**:
  - No propellant is dumped, and $p_c$ is about 150 bar, giving a high $I_{sp}$ for storable propellants (about 285 s at sea level).
  - Hypergolic ignition makes the engine simple and reliable.
  - The oxidiser-rich turbine gas avoids coking but needs oxidation-resistant materials.

### (vi) RD-270 full-flow staged combustion (4)
- Two pre-burners:
  - a **fuel-rich** one (all the fuel plus a little oxidiser) drives the fuel pump turbine;
  - an **oxidiser-rich** one (all the oxidiser plus a little fuel) drives the oxidiser pump turbine.
- Both exhausts enter the chamber as gases.
- **Reasoning and advantages over SC**:
  - **All** the propellant passes through the turbines, so each turbine can run **cooler** for the same power, giving longer life or a higher $p_c$ (the RD-270 was about 260 bar).
  - Separate shafts need no fuel–oxidiser inter-propellant seal on a common shaft, which removes a failure mode.
  - Gas–gas injection gives better mixing, more complete combustion and a shorter chamber.
- **Cost**: two pre-burners and two turbopumps make it the most complex and hardest to start. It was not flown until Raptor.

---

## Q3: Turbojet

### (i) Operable flight corridor (5)
- **Upper bound (altitude)**: too little density for **lift** at a tolerable $C_L$ (stall), and for **combustion stability and relight** (low pressure, so poor flame stability).
- **Lower bound (speed and dynamic pressure)**:
  - **structural load and dynamic-pressure** limits ($q = \tfrac12\rho V^2$, typically 20–90 kPa) at low altitude and high speed;
  - **kinetic heating** of skin and intake ($T_0$) with Mach number;
  - for engines, compressor-inlet temperature and $p_0$ limits, and TET.
- **Speed limits by engine type**:
  - turbofan/turbojet: limited by compressor-exit temperature and TET, to about M 2.3–3;
  - ramjet: M 2–5 (insufficient ram compression below; $T_{02}\to T_{03}$ above);
  - scramjet: M 5–15.
- The resulting corridor in the altitude–Mach plane is bounded below by $q_{max}$ and heating, and above by lift and combustion.

### (ii) Specific thrust (20)
Assumptions: ideal diffuser and nozzle; no combustor pressure loss; air properties throughout; complete combustion; fully expanded exhaust; $T_{ref} = 0$ energy balance.

| Step | Working | Result |
|---|---|---|
| Flight | $V = 0.89\sqrt{1.4(287)(220)}$ | 264.6 m/s |
| Intake | $T_{02} = 220(1+0.2\times0.89^2)$; $p_{02} = 21(1.1584)^{3.5}$ | 254.9 K, 35.14 kPa |
| Compressor | $T_{03s} = 254.9(30)^{0.2857}$; $T_{03} = T_{02}+\Delta T_s/0.82$ | 673.5 K, **765.4 K**, $p_{03} = 1054$ kPa |
| Burner | $f = \dfrac{1005(1600-765.4)}{42\times10^6-1005(1600)}$ | **0.0208** |
| Turbine | $T_{05} = 1600-\dfrac{510.5}{1.0208}$; $T_{05s} = 1600-\dfrac{500.1}{0.87}$ | 1099.9 K, 1025.1 K, $\pi_t = $ **4.75** |
| Nozzle | $p_{05} = 221.9$ kPa; $V_j = \sqrt{2c_pT_{05}[1-(21/221.9)^{0.2857}]}$ | $T_6 = 560.8$ K, **$V_j = 1041$ m/s** |

$$
\frac{F}{\dot m_a} = (1+f)V_j-V = 1.0208(1041.0)-264.6 = \boxed{798\text{ N s/kg}}\qquad\text{TSFC} = 26.0\text{ g kN}^{-1}\text{ s}^{-1}
$$

### (iii) Afterburner (5)
- **Principle**: extra fuel is injected into the turbine exhaust (which is still about 15 % O₂), with flame holders (V-gutters). The gas is heated to $T_{06}\approx2000$–2200 K, **unconstrained by turbine blades**.
- With the same nozzle pressure ratio, $V_j = \sqrt{2c_pT_{06}[1-(p_a/p_{06})^{(\gamma-1)/\gamma}]}\propto\sqrt{T_{06}}$. Thrust rises 40–70 % for a small, light addition.
- A **variable-area nozzle** is essential: for a choked throat $\dot m = A_8p_{06}\,\Gamma(\gamma)/\sqrt{RT_{06}}$, so $A_8\propto\sqrt{T_{06}}$ keeps the engine operating point (turbine back pressure) unchanged. See [[Afterburning (Reheat)]].
- **Advantages**: large, quick thrust boost for take-off, transonic acceleration, supersonic dash and combat; little weight.
- **Disadvantages**: heat is added at **low pressure** (after the turbine), so the cycle efficiency is poor and TSFC roughly doubles. There is a dry-thrust penalty from the duct pressure losses, plus heavy IR and noise signature, and long jet-pipe length and cooling needs.

---

## Q4: Ramjet and other engines

### (i) Modules (3)
See [[SESA2023 Exam 2014-15 Solutions]] Q2(i).

### (ii) Why a ramjet can run away when $T_{03}$ is not limited (5)
- A slight fuel increase raises $T_{03}$, which raises $V_e$ and the thrust, so the vehicle accelerates.
- A higher $M$ gives a higher ram pressure ratio $p_{02}/p_a = (1+0.2M^2)^{3.5}$. That means **more expansion available**, so $V_e$ rises further and the air mass flow $\dot m = \rho AV$ rises.
- With a fixed fuel-air ratio, the fuel flow and heat release rise in proportion to the air flow, so thrust grows faster than drag.
- On the $T$–$s$ diagram, the compression line lengthens (to a higher isobar) and the heat-addition isobar moves up and to the right, enlarging the cycle area and raising $\eta_{th} = 1-T_a/T_{02}$.
- Positive feedback means the vehicle keeps accelerating until the temperature limit (materials, $T_{02}\to T_{03}$) or intake unstart intervenes. The engine must be throttled back to hold speed. This is the SR-71 experience in [[SESA2023 Exam 2016-17 Solutions]] Q4(iv); see [[Ramjet]].

### (iii) Flight speed and Mach number (5)
$T_a = 235$ K, $f = 0.05$, $T_{03} = 2900$ K, LCV = 41 MJ/kg:

$$
T_{02} = 1.05(2900)-0.05(40{,}796) = 1005.2\text{ K},\qquad M = \sqrt{\frac{1005.2/235-1}{0.2}} = \boxed{4.05},\qquad V = \boxed{1244\text{ m/s}}
$$

### (iv) Exhaust (5)
$M_e = \boxed{4.05}$. $T_e = 2900/(1+0.2\times4.048^2) = 678.0$ K.

$$
V_e = 4.048\sqrt{1.4(287)(678.0)} = \boxed{2113\text{ m/s}}
$$

$F/\dot m = 1.05(2113)-1244 = 975$ N s/kg.

### (v) Why Concorde cruised at M 2 (6)
- **Range** is set by $\eta_O(L/D)$ (Breguet: $s = \eta_O\frac{LCV}{g}\frac LD\ln\frac{w_1}{w_2}$).
  - Supersonic $L/D$ is poor (about 7 against 18 subsonic).
  - $\eta_O$ **rises with Mach number** for a turbojet: ram compression ($p_{01}/p_a = 7.8$ at M 2) boosts $\eta_{th}$, and $V_j/V$ falls towards 1, boosting $\eta_P = 2/(1+V_j/V)$.
  - At M 2 Concorde's Olympus 593 reached $\eta_O\approx40\%$, better than contemporary subsonic engines. That partly offsets the poor $L/D$, so the $\eta_OL/D$ product was acceptable for the transatlantic range.
- **Upper limit**: the stagnation temperature $T_0 = T_a(1+0.2M^2)\approx390$ K at M 2 (about 120 °C). That was the limit for the **aluminium alloy** (RR.58/Hiduminium) airframe's creep and fatigue life. At M 2.2 it is about 427 K, which would need titanium or steel (cost and weight).
- Productivity (block time halved) needed high speed, while sonic-boom restrictions confined supersonic flight to overwater. **M 2.0 was the best compromise** of efficiency, materials and time saving.

### (vi) Fixed-shaft vs free-turbine turboprops (3)
- **Fixed (single) shaft**: the propeller is geared to the gas-generator shaft, so propeller speed and core speed are locked.
  - Advantages: simple, quick throttle response (large inertia), good engine braking.
  - Disadvantages: high starting torque (turns the propeller too); constant-speed operation.
  - Examples: Dart, TPE331, Garrett (commuter aircraft, APUs).
- **Free (power) turbine**: a separate turbine drives the propeller, and the gas generator runs independently.
  - Advantages: easy starting (propeller not turned); prop and core speeds optimised separately; flexible installation (PT6A, PW100).
  - Disadvantages: slower response.
  - Widely used on regional turboprops and helicopters (turboshafts).

### (vii) APU role in ETOPS (3)
- The APU is a small gas turbine (usually in the tail) providing **bleed air** (engine start, air-conditioning and pressurisation) and **electrical power** on the ground and in flight.
- For ETOPS twins (flying up to 180+ min from a diversion airport), after an engine failure the APU is a **backup power source**. It restores electrical and pneumatic redundancy while the remaining engine carries the aircraft.
- It must be capable of **in-flight start at high altitude after cold soak** (cold-soak start reliability, typically ≥ 95 % demonstrated), and may be required to run throughout ETOPS segments.
- It must meet high reliability requirements, and be certified for altitude operation and continuous running.

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2015-16")
