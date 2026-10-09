---
title: "SESA2023 Exam 2014-15 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2014-15"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-201415-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2014-15 Solutions

> [!info] Paper
> 120 min, closed book. Answer Q1 and **any two** of Q2–Q4 (30 marks each). Air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$. Fuel-air ratio from $(1+f)c_pT_{0,out} = c_pT_{0,in}+f\,LCV$.

## Q1: Efficiencies and range

### (i) Meaning of the efficiency expressions (3)

$$
\eta_{th} = \frac{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}{\dot m_fLCV},\qquad \eta_p = \frac{V\{\dot m_a[(1+f)V_j-V]+(P_j-P_{atm})A_j\}}{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}
$$

- $\eta_{th}$ numerator: the **rate of increase of kinetic energy** of the gas passing through the engine. This is the useful mechanical output of the engine viewed as a heat engine.
- $\eta_{th}$ denominator: the **rate of chemical energy release** by the fuel (fuel power).
- $\eta_p$ numerator: the **thrust power** $FV$ delivered to the aircraft (net thrust times flight speed).
- $\eta_p$ denominator: the same kinetic-energy increase. The difference between them is the kinetic energy **left in the wake**, $\tfrac12\dot m(V_j-V)^2$, which is wasted.

### (ii) Large civil engines (3)
Assume $f\ll1$ (about 0.02) and a fully expanded jet ($P_j = P_{atm}$). Then:

$$
\eta_p = \frac{\dot mV(V_j-V)}{\tfrac12\dot m(V_j^2-V^2)} = \frac{2V(V_j-V)}{(V_j-V)(V_j+V)} = \boxed{\frac{2}{1+V_j/V}}
$$

### (iii) Breguet range equation (12)
Assumptions:
- steady, level cruise, so $L = W = mg_0$ and $F = D$;
- constant $V$, $L/D$ and TSFC (or $\eta_O$);
- $g_0$ constant;
- climb, descent and reserves neglected.

1. Fuel flow: $\dot m_f = -\dfrac{dm}{dt} = \text{TSFC}\cdot F = \text{TSFC}\cdot D = \text{TSFC}\dfrac{mg_0}{L/D}$.
2. With $ds = V\,dt$: $\dfrac{dm}{m} = -\dfrac{g_0\,\text{TSFC}}{V(L/D)}ds$.
3. Integrate from the initial mass $w_2$ to the final mass $w_1$:

$$
s = \frac{V}{g_0\,\text{TSFC}}\frac LD\ln\frac{w_2}{w_1}
$$

4. The overall efficiency is $\eta_O = FV/(\dot m_fLCV) = V/(\text{TSFC}\cdot LCV)$, so $V/\text{TSFC} = \eta_OLCV$:

$$
\boxed{s = \frac LD\frac{\eta_OLCV}{g_0}\ln\frac{w_2}{w_1}}\qquad\text{and}\qquad s\propto\frac{1}{\text{TSFC}}\text{ at a given }V\;\blacksquare
$$

See [[Breguet Range Equation]].

### (iv) Why high subsonic speed and turbofans? (8)
- **Range factor**: range $\propto V(L/D)/\text{TSFC} = \eta_O(L/D)LCV/g_0$. The best $\eta_O$ is reached at high flight speed, because the thermal efficiency benefits from ram compression and $\eta_P$ is high when $V_j$ is only slightly above $V$.
- **Speed limit**: above M ≈ 0.85, **wave drag** from transonic flow over the wing makes $L/D$ collapse. Sweep and supercritical aerofoils push the drag-divergence Mach number to about 0.85, which is where airliners cruise. Higher speed also gives more trips per day (productivity).
- **Turbojets** have high $V_j$ (about 900 m/s), so $\eta_P = 2/(1+V_j/V)\approx0.4$ at 250 m/s. They are noisy and fuel-hungry.
- **Turboprops** have excellent $\eta_P$ but propeller tip Mach limits (helical tip speed must stay subsonic) restrict them to about M 0.6–0.7. Blade compressibility losses and noise rise sharply beyond that.
- **Turbofans** move a large bypass mass flow at modest $\Delta V$ ($V_j\approx300$ m/s), giving $\eta_P\approx0.8$ at M 0.8 in a ducted fan whose relative tip Mach number the intake controls. That makes them the best compromise at high subsonic speed.

See [[Bypass Ratio and Fan Pressure Ratio]] and [[Propulsive Efficiency]].

### (v) Military vs civil design drivers (4)
- **Civil**: range, fuel burn, noise and cost dominate, so designs aim for maximum $\eta_O = \eta_P\eta_{th}$. That means high bpr (low $V_j$, high $\eta_P$) and high OPR and TET (high $\eta_{th}$). Engines are large in diameter and heavy.
- **Military**: thrust per unit frontal area and thrust-to-weight dominate (supersonic flight, manoeuvre), so specific thrust must be high. That means low bpr (0–1), high $V_j$ and reheat, with low $\eta_P$ at subsonic speed accepted. OPR is chosen near the **maximum specific work** point (about 15–25) rather than maximum efficiency.

---

## Q2: Ramjet

### (i) Modules at supersonic speed (3)
- **Supersonic diffuser**: a spike or ramp creates oblique shocks and then a weak terminal normal shock at the throat, decelerating the flow to subsonic speed. A subsonic diffuser then slows it to M ≈ 0.2–0.3 with ram compression ($p_{01}/p_a$ up to about 30 at M 3). See [[Oblique Shock Waves]].
- **Combustor**: fuel injectors, and flame holders (gutters) create recirculation zones that anchor the flame in the fast stream. Heat is added at almost constant pressure.
- **C–D nozzle**: expands the hot gas back to supersonic speed. The exit speed exceeds flight speed because $T_{03}\gg T_{02}$.

### (ii) Air vehicles and issues (6)
- **Vehicles**: supersonic missiles (Bloodhound, Meteor, BrahMos), target drones, and the ramjet mode of the J58.
- **Performance**: no static thrust, so a booster is needed; poor below M ≈ 2 (low ram pressure ratio, low $\eta_{th}$); thrust falls to zero near M 5–6 as $T_{02}\to T_{03}$; narrow optimum.
- **Aerodynamics**: intake–shock matching and unstart; spillage drag off-design; wave drag.
- **Materials**: stagnation heating of the airframe, and combustor and nozzle walls at the full flame temperature with no turbine limit. Cooling, refractory metals or ceramics are needed.

### (iii) $T$–$s$ with Mach number at fixed $T_{03}$ (5)
See [[SESA2023 Exam 2013-14 Solutions]] Q2(ii) and [[Ramjet]]:
- a higher $M$ raises $T_{02}$ and $p_{02}$;
- $\eta_{th} = 1-T_a/T_{02}$ rises;
- the heat addition $T_{03}-T_{02}$ shrinks;
- specific thrust peaks, then falls to zero when $T_{02} = T_{03}$.

### (iv) Flight speed and Mach number (5)
$T_a = 230$ K, $f = 0.04$, $T_{03} = 2800$ K, LCV = 41 MJ/kg.

$$
T_{02} = (1+f)T_{03}-f\frac{LCV}{c_p} = 1.04(2800)-0.04(40{,}796) = 1280.2\text{ K}
$$

$$
M = \sqrt{\frac{1280.2/230-1}{0.2}} = \boxed{4.78},\qquad V = 4.78\sqrt{1.4(287)(230)} = \boxed{1452\text{ m/s}}
$$

### (v) Exhaust (5)
Ideal, so $M_e = M = \boxed{4.78}$. Then $T_e = 2800/(1+0.2\times4.778^2) = 503.1$ K and:

$$
V_e = 4.78\sqrt{1.4(287)(503.1)} = \boxed{2148\text{ m/s}}
$$

Specific thrust: $1.04(2148)-1452 = 782$ N s/kg.

### (vi) The J58 and scramjets (6)
- **The J58 (SR-71, M 3.2)** was a **turbo-ramjet** (a bleed-bypass turbojet).
  - At low speed it ran as an afterburning turbojet.
  - Above about M 2, six **bypass tubes** took air bled from the 4th compressor stage around the core directly into the afterburner. The engine then acted mostly as a ramjet, and the afterburner generated most of the thrust.
  - The **translating inlet spike** (moving aft by about 0.66 m at M 3.2) and forward and aft bypass doors positioned the shocks and matched intake flow to engine demand. At cruise the inlet produced most of the total thrust.
  - This avoided compressor over-temperature and choking at high Mach while keeping static thrust for take-off.
- **Ramjet limits**:
  - Decelerating to subsonic speed at M > 5–6 makes the static temperature after the diffuser so high that dissociation means heat added goes into breaking bonds, not into temperature rise.
  - Normal-shock $p_0$ losses and wall heating become prohibitive.
  - Thrust tends to zero as $T_{02}\to T_{03,max}$.
- **Scramjets** keep the combustor flow **supersonic**. Only oblique shocks provide partial compression, so the static temperature and pressure stay tolerable, extending operation to M ≈ 6–15. The challenges are:
  - mixing and burning within about 1 ms of residence time (hydrogen fuel);
  - thermal loads;
  - intake–combustor–nozzle integration with the airframe;
  - no thrust below about M 4–5 (a booster or combined cycle is needed).

---

## Q3: Turbojet cycle

### (i)–(ii) Block diagram and $T$–$s$ (10)
The answer is the same as [[SESA2023 Exam 2013-14 Solutions]] Q1(i)–(ii): see [[Turbojet]] and `prop_turbojet_Ts.png`.

### (iii) Compressor entry (5)
$M = 0.8$, $p_a = 23$ kPa, $T_a = 225$ K:

$$
T_{02} = 225(1.128) = \boxed{253.8\text{ K}},\qquad p_{02} = 23(1.128)^{3.5} = \boxed{35.06\text{ kPa}}
$$

### (iv) Fuel-air ratio (5)
$r_c = 25$, $\eta_c = 0.85$, $T_{04} = 1900$ K:

$$
T_{03s} = 253.8(25)^{0.2857} = 636.7\text{ K},\qquad T_{03} = 253.8+\frac{382.9}{0.85} = 704.2\text{ K},\qquad p_{03} = 876.5\text{ kPa}
$$

$$
f = \frac{1005(1900-704.2)}{41\times10^6-1005(1900)} = \boxed{0.0307}
$$

### (v) Turbine pressure ratio (5)

$$
T_{05} = 1900-\frac{450.4}{1.0307} = 1463.0\text{ K},\qquad T_{05s} = 1900-\frac{437.0}{0.9} = 1414.5\text{ K}
$$

$$
\frac{p_{04}}{p_{05}} = \left(\frac{1900}{1414.5}\right)^{3.5} = \boxed{2.81}
$$

### (vi) Specific thrust (5)
$p_{05} = 876.5/2.809 = 312.0$ kPa and $V = 0.8\sqrt{1.4(287)(225)} = 240.5$ m/s.

$$
V_j = \sqrt{2(1005)(1463.0)\left[1-\left(\frac{23}{312.0}\right)^{0.2857}\right]} = 1242.8\text{ m/s}
$$

$$
\frac{F}{\dot m_a} = 1.0307(1242.8)-240.5 = \boxed{1041\text{ N s/kg}}
$$

TSFC = 29.6 g kN⁻¹ s⁻¹.

---

## Q4: Rocket engines

### (i) Definitions (4)
- $I_{sp} = F/(\dot mg_0)$.
- $c = F/\dot m = V_e+(p_e-p_a)A_e/\dot m$.
- $C^* = p_cA_t/\dot m$ (chamber and propellant quality).
- $C_F = F/(p_cA_t)$ (nozzle quality, typically 1.3–1.9).
- They are linked by $c = C^*C_F$. See [[Rocket Performance Parameters]].

### (ii) $I_{sp}$ derivation (5)
The same as [[SESA2023 Exam 2013-14 Solutions]] Q4(ii).

### (iii) Booster, main and upper-stage engines (3)

| Type | Role | Typical thrust | Mass flow | Features |
|---|---|---|---|---|
| **Booster** (strap-on SRB or liquid) | Lift-off and first ~2 min | 1–15 MN each (Shuttle SRB ≈ 12.5 MN) | 1–5 t/s | High thrust, moderate $I_{sp}$ (≈ 250–300 s at sea level), short burn, sea-level nozzle ($\epsilon$ ≈ 7–16) |
| **Main / core stage** | Lift-off to high altitude, long burn | 1–7 MN (SSME 2.2 MN vacuum, RD-180 4 MN) | 0.5–2 t/s | High $p_c$, high $I_{sp}$ (≈ 360–450 s vacuum), must work at sea level and in vacuum ($\epsilon$ ≈ 30–80) |
| **Upper stage** | Orbit insertion, restarts | 10–200 kN (RL10 110 kN, Vinci 180 kN) | 10–40 kg/s | Vacuum only, very large $\epsilon$ (100–280), highest $I_{sp}$ (450–465 s with LH₂/LOX), restartable, lightweight |

### (iv) Five rocket power cycles (18)
**Relevance to thrust.**
- Thrust is $F = C_Fp_cA_t$, so a higher chamber pressure gives more thrust from a given throat. It also permits a larger expansion ratio within a given exit size, raising $I_{sp}$.
- The power cycle determines how high $p_c$ can be: pumps must deliver more than $p_c$.
- It also determines whether any propellant is wasted.

For each cycle, sketch the tanks, pumps (P), turbine (T), pre-burner or gas generator, the cooling jacket and the chamber, with the flow paths:
1. **Pressure-fed**: high-pressure He pressurises the tanks and flows go straight to the chamber.
   - Advantages: simplest, most reliable, restartable, no turbomachinery.
   - Disadvantages: tank walls must withstand more than $p_c$, so they are heavy.
   - Limitation: $p_c$ ≲ 10–20 bar, so it suits upper stages, OMS and RCS.
2. **Gas generator (open)**: a small combustor burns a fuel-rich fraction (1–5 %) of the propellants to drive the turbine, and the exhaust is **dumped** overboard.
   - Advantages: turbopumps decoupled from the chamber; high $p_c$ (70–100 bar); simple, throttleable, proven (F-1, Merlin, Vulcain).
   - Disadvantages: the dumped gas lowers the effective $I_{sp}$ by about 1–3 %.
3. **Expander (closed)**: fuel (H₂ or CH₄) is heated in the regenerative cooling jacket, the vapour drives the turbine, and it is then injected into the chamber.
   - Advantages: nothing dumped (high $I_{sp}$); benign turbine temperatures; very reliable and restartable (RL10, Vinci).
   - Limitation: turbine power is limited by the heat picked up from the walls. Wall area scales as $L^2$ while flow scales as $L^3$, so the cycle is thrust-limited to about 300 kN.
4. **Tap-off / expander-bleed (open)**: hot gas is tapped from the chamber (or heated fuel bled from the jacket) to drive the turbine, then dumped.
   - Advantages: no separate gas generator (J-2S, LE-5B).
   - Disadvantages: the tapped gas is hot and dirty; there are start-up complexities; the dumped flow costs $I_{sp}$.
5. **Staged combustion (closed)**: all of one propellant passes, with a little of the other, through a **pre-burner**. The fuel-rich (SSME) or oxidiser-rich (RD-170, RD-180) exhaust drives the turbine and then enters the main chamber.
   - Advantages: nothing is wasted and the highest $p_c$ is possible (200–300 bar), so both $I_{sp}$ and thrust-to-weight are highest.
   - Disadvantages: very high pump discharge pressures (about 1.5–2 × $p_c$); a hot, rich turbine environment (especially oxidiser-rich, which needs special alloys); complexity and cost.
6. (Also acceptable) **Full-flow staged combustion**: separate fuel-rich and oxidiser-rich pre-burners so all the propellant passes through the turbines (RD-270, Raptor).

See [[Rocket Engine Power Cycles]].

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2014-15")
