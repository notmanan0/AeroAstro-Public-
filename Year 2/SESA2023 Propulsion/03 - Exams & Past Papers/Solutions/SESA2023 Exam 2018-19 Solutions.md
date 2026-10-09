---
title: "SESA2023 Exam 2018-19 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2018-19"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-201819-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2018-19 Solutions

> [!info] Paper
> Closed book with a data book and formula sheet. Four questions of 25 marks: *General Propulsion System Performance*, *Real Turbojet Cycle Analysis*, *Single Stage to Orbit*, *Supersonic Flight*. Air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$.

## Q1: General performance

### (i) Speed and altitude limits (5)
1. **Dynamic pressure and structure**: $q = \tfrac12\rho V^2$ sets aerodynamic loads, which bounds low-altitude, high-speed flight.
2. **Kinetic heating**: $T_0 = T_a(1+0.2M^2)$. Aluminium is limited to about M 2.2, titanium to about M 3.2, and beyond that nickel alloys, ceramics or active cooling are needed.
3. **Lift and combustion at altitude**: low $\rho$ requires a high $C_L$ or high speed; low pressure makes combustion unstable and relight hard.

**Propulsion speed limits**:
- turboprop: M < 0.7 (propeller tip Mach);
- turbofan: M < 1–1.5;
- turbojet: M < 2.3–3 (compressor-exit and TET limits);
- ramjet: M 2–5;
- scramjet: M 5–15;
- rocket: unlimited (no air needed).

### (ii) Materials in a large civil turbofan (e.g. Trent XWB / 900-series) (5)
*(Diagram: engine cross-section with the modules labelled.)*

| Module | Temperature | Material |
|---|---|---|
| Fan blades | ambient | Hollow diffusion-bonded **Ti-6Al-4V** (carbon-fibre composite in the newest engines) |
| Fan containment case | ambient | Aluminium, Kevlar wrap or CFRP |
| Nacelle | ambient | CFRP composites and acoustic liners |
| IP compressor and front HP compressor | up to ≈ 600 °C | **Titanium alloys** (Ti-6-4, Ti-6246, IMI 834); blisks |
| Rear HP compressor | 600–700 °C, above the Ti fire and creep limit | **Nickel alloys** (IN718, RR1000) |
| Combustor | 2000+ K gas | Ni/Co sheet alloys with effusion cooling and **thermal barrier coatings** (yttria-stabilised zirconia) |
| HP turbine blades | TET ≈ 1800 K | **Single-crystal Ni superalloys** (CMSX-4, CMSX-10) with film cooling and TBC |
| HP turbine discs | | Powder-metallurgy Ni (RR1000) |
| IP and LP turbines | cooler | Directionally solidified or equiaxed Ni alloys (TiAl in some newer LPTs) |
| Casings and exhaust | | Ni and Ti alloys |

The logic is **specific strength** at the front (Ti, composites, where weight matters) and **temperature capability** (creep and oxidation resistance) at the back (Ni).

### (iii) Ideal turbofan specific thrust (5)
See [[SESA2023 Exam 2016-17 Solutions]] Q3(iii):

$$
\frac{F}{\dot m_{aC}} = (1+f)V_{jHOT}+BPR\,V_{jCOLD}-V(1+BPR)
$$

### (iv) Compressor adaptations for OPR ≈ 40 (5)
At high OPR, the front stages choke and the rear stages stall at part speed, because the density ratio across the machine changes with speed.
1. **Multiple spools** (2 or 3 shafts): each compressor runs at its own best speed, so stages stay matched over the operating range. The LP spool slows, the HP spool speeds up.
2. **Variable inlet guide vanes and stator vanes** (front HP stages): re-stagger at low speed to keep incidence near design, avoiding front-stage stall.
3. **Handling bleed valves**: dump mid-compressor air at low speed and during transients, raising front-stage flow and surge margin.

Also: 3D aerodynamic blading (sweep and lean), active tip-clearance control, blisks, and casing treatments. See [[Compressor Stall and Surge]].

### (v) Thermal efficiency (5)
Treat the engine as a heat engine whose useful output is the increase in kinetic energy of the working fluid, and whose input is the chemical energy of the fuel:

$$
\eta_{th} = \frac{\text{rate of KE increase}}{\text{rate of fuel energy input}} = \frac{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}{\dot m_fLCV} = \frac{(1+f)V_j^2-V^2}{2f\,LCV}
$$

- **Numerator**: the mechanical power delivered to the gas stream. It is the gas generator's output, and whatever is not converted to jet KE leaves as heat in the exhaust.
- **Denominator**: the heat input rate.

$\eta_{th}$ rises with OPR, TET and component efficiencies (see [[Brayton Cycle]]). See [[Thermal and Overall Efficiency]].

---

## Q2: Real turbojet

### (i) Stagnation and static profiles through an ideal turbojet (3)
- $T_0$: constant through the intake; rises in the compressor; jumps in the combustor; falls in the turbine; constant in the nozzle.
- $p_0$: constant (ideal) in the intake; rises in the compressor; constant in the combustor; falls in the turbine; constant in the nozzle.
- Static $T$ and $p$ follow the stagnation values in the low-speed core. They rise in the intake (ram diffusion) and fall steeply in the nozzle as $V$ rises to $V_j$.

See the table in [[SESA2023 Exam 2016-17 Solutions]] Q4(i), with reheat off.

### (ii) Specific thrust with component losses (22)
**Assumptions**:
- air properties throughout ($c_p = 1005$, $\gamma = 1.4$);
- no combustor pressure loss (not given) and complete combustion;
- $T_{ref} = 0$ energy balance;
- adiabatic intake and nozzle ($T_0$ constant), with losses only as the stated $\Gamma$;
- fully expanded nozzle;
- the turbine exactly drives the compressor.

| Station | Working | Result |
|---|---|---|
| Flight | $V = 0.75\sqrt{1.4(287)(225)}$ | **225.5 m/s** |
| Intake | $T_{02} = 225(1.1125)$; $p_{02} = \Gamma_dp_a(1.1125)^{3.5} = 0.9(20)(1.4523)$ | **250.3 K**, **26.14 kPa** |
| Compressor | $T_{03s} = 250.3(30)^{0.2857}$; $T_{03} = 250.3+411.2/0.85$ | 661.5 K, **734.0 K**, $p_{03} = 784.2$ kPa |
| Burner | $f = \dfrac{1005(1550-734.0)}{42\times10^6-1005(1550)}$ | **$f = 0.0203$** |
| Turbine | $T_{05} = 1550-\dfrac{483.7}{1.0203}$; $T_{05s} = 1550-\dfrac{474.1}{0.89}$ | **1075.9 K**, 1017.3 K, $\pi_t = $ **4.37**, $p_{05} = 179.6$ kPa |
| Nozzle | $p_{06} = \Gamma_np_{05} = 161.7$ kPa; $V_j = \sqrt{2c_pT_{05}[1-(20/161.7)^{0.2857}]}$ | $T_6 = 592$ K, **$V_j = 986.0$ m/s** |

$$
\boxed{\frac{F}{\dot m_a} = (1+f)V_j-V = 1.0203(986.0)-225.5 = 781\text{ N s/kg}},\qquad \boxed{\text{TSFC} = \frac{f}{F/\dot m_a} = 26.0\text{ g kN}^{-1}\text{ s}^{-1}}
$$

Without the two 10 % $p_0$ losses, $V_j$ would be 1021 m/s and $F/\dot m_a$ would be 816 N s/kg. The losses cost about 4 % of the specific thrust. See [[Component Stagnation Pressure Ratios]].

---

## Q3: Single stage to orbit

### (i) SSTO impossible with $I_{sp}<450$ s and 15 % structure (5)
Zero payload and $\epsilon = 0.15$ give $MR = 1/0.15 = 6.67$.

$$
\Delta V_{ideal}<450(9.81)\ln6.67 = 8375\text{ m/s},\qquad \Delta V_{net} = (1-0.30-0.10)(8375) = 5025\text{ m/s}\ll7788\text{ m/s}
$$

$V_{orb}$ at 200 km is 7788 m/s. Even with the best propellant and no payload the vehicle falls about 2.8 km/s short, so SSTO is impossible.

**Staging**:
- Split the $\Delta V$ between stages and drop each stage's structure when empty.
- Each stage then needs only $MR_i = e^{\Delta V_i/c}$ (e.g. about 2.7 per stage for three equal stages), which is achievable with 15 % structure.
- The overall payload fraction $\prod\lambda_i$ becomes positive.

See [[Tsiolkovsky Rocket Equation]] and [[Rocket Staging]].

### (ii) SABRE working principle (10)
*(Schematic: axisymmetric translating-cone intake → **precooler** → turbo-compressor → combustion chamber and nozzles; closed **helium loop**; **hydrogen** feed; LOX tank for rocket mode.)*
- **Air path**: intake shocks decelerate the air (about 1000 K+ stagnation at M 5). The **precooler** (thousands of thin-walled micro-tubes carrying cold helium) cools it to about 150 K in about 10 ms, with methanol injection or frost control to prevent icing. A light **turbo-compressor** then compresses the cold, dense air to about 140 bar and delivers it to the **pre-burner** and the main **rocket-type combustion chambers**.
- **Helium loop** (closed Brayton cycle, the heat-transfer medium):
  1. He picks up heat in the precooler;
  2. is heated further in the pre-burner heat exchanger;
  3. expands through the **helium turbine** that drives the air compressor;
  4. rejects heat to the liquid hydrogen in a He/H₂ heat exchanger;
  5. is recirculated by a helium compressor.
- **Hydrogen path**: LH₂ is pumped to high pressure, used as the ultimate **heat sink** (cooling the helium), drives the hydrogen turbopump, then burns fuel-rich in the pre-burner (with some air) and finally in the main chambers with the compressed air. Excess H₂ is burned in spill ducts or ramjet burners around the nacelle.
- **Modes**: air-breathing from 0 to about M 5.5 and 25 km. Then the intake closes and the **same chambers** run as a closed-cycle LOX/LH₂ rocket to orbit (up to about M 25).

### (iii) How SABRE avoids ramjet limitations (10)
- **Static thrust**: the turbo-compressor provides compression at zero speed, whereas a ramjet needs M > 1–2.
- **Compression work** $w = c_p\Delta T_0\propto T_{in}$. Precooling from about 1000 K to 150 K cuts the compressor work per unit pressure ratio by about 6×, so a **high pressure ratio** (≈ 140) is reached with a light single-shaft machine, even at M 5 where a turbojet's compressor would overheat.
- **High chamber pressure**: rocket-like chambers (≈ 140 bar) give a compact, high-$C_F$ nozzle in both modes, so one engine does both jobs. That saves the mass of carrying two engines.
- **No ram-temperature limit**: a ramjet's heat addition falls as $T_{02}\to T_{max}$. SABRE removes the ram heat into the He/H₂ sink and puts it back as fuel enthalpy (regeneration). The "ram heat" drives the turbines instead of limiting combustion.
- **Efficiency**: the air supplies the oxidiser for the first part of the ascent, so there is no LOX to carry. The effective air-breathing $I_{sp}$ is about 3500–4500 s, far above a rocket's 450 s. Its TSFC is comparable to a turbojet's (though it is fuel-rich, since the H₂ flow is set by the cooling need).
- **$T$–$s$ sketch**:
  1. air rises along the ram compression to a high $T_{01}$;
  2. isobaric cooling in the precooler moves it far to the **left** (entropy is removed to the helium);
  3. a short, steep compression follows;
  4. then combustion at high $p$ and expansion.
  
  Compared with a ramjet, the cycle reaches a much higher peak pressure for the same peak temperature, so $\eta_{th}$ is higher.

---

## Q4: Supersonic flight

### (i) Ramjet modules (3)
See [[SESA2023 Exam 2014-15 Solutions]] Q2(i).

### (ii) Proof of the ideal ramjet specific thrust (10)
Ideal ramjet: isentropic diffuser and nozzle, isobaric combustion ($p_{04} = p_{03} = p_{02} = p_{01}$), fully expanded ($p_e = p_a$, so no pressure thrust), constant $\gamma$ and $R$.

1. Thrust with $p_e = p_a$: $F = \dot m_a[(1+f)V_j-V]$.
2. Stagnation-pressure equality and full expansion give $p_{0e}/p_e = p_{01}/p_a$. With the isentropic relation this means $1+\tfrac{\gamma-1}2M_e^2 = 1+\tfrac{\gamma-1}2M^2$, so **$M_e = M$**.
3. The nozzle is adiabatic, so $T_{0e} = T_{0c}$ and $T_e = T_{0c}\left(1+\tfrac{\gamma-1}2M^2\right)^{-1}$.
4. Therefore $V_j = M\sqrt{\gamma RT_e} = M\sqrt{\gamma RT_a}\sqrt{\dfrac{T_{0c}}{T_a}}\left(1+\tfrac{\gamma-1}2M^2\right)^{-1/2}$.
5. With $V = M\sqrt{\gamma RT_a}$:

$$
\boxed{\frac{F}{\dot m_a} = M\sqrt{\gamma RT_a}\left[(1+f)\sqrt{\frac{T_{0c}}{T_a}}\left(1+\frac{\gamma-1}{2}M^2\right)^{-1/2}-1\right]}\;\blacksquare
$$

See [[Ramjet]].

### (iii) Real ramjet: specific thrust and mass flow (12)
Assumptions:
- air properties throughout;
- $T_{ref} = 0$ energy balance and complete combustion;
- adiabatic components with the given $\Gamma$;
- ideally (fully) expanded nozzle;
- $T_{0c} = 2850$ K is the nozzle-entry $T_0$.

$$
V = 2.5\sqrt{1.4(287)(255)} = 800.2\text{ m/s},\qquad T_{02} = 255(2.25) = 573.8\text{ K}
$$

$$
f = \frac{1005(2850-573.8)}{42\times10^6-1005(2850)} = 0.0585
$$

Overall pressure ratio to the nozzle exit:

$$
\frac{p_{04}}{p_a} = \frac{p_{01}}{p_a}\Gamma_d\Gamma_c\Gamma_n = 17.09(0.85)(0.90)(0.80) = 10.46
$$

$$
T_e = \frac{2850}{10.46^{0.2857}} = 1457.4\text{ K},\qquad V_e = \sqrt{2(1005)(2850-1457.4)} = 1673.0\text{ m/s}
$$

$$
\frac{F}{\dot m_a} = (1+f)V_e-V = 1.0585(1673.0)-800.2 = \boxed{971\text{ N s/kg}},\qquad \dot m_a = \frac{50{,}000}{970.6} = \boxed{51.5\text{ kg/s}}
$$

For comparison, the ideal formula from (ii) gives 1088 N s/kg. The combined $\Gamma = 0.612$ costs about 11 % of the thrust. See [[Component Stagnation Pressure Ratios]].

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2018-19")
