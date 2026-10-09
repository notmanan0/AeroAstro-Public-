---
title: "SESA2023 Exam 2021-22 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2021-22"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]", "[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]", "[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-202122-02-SESA2023.pdf"]
---

# SESA2023 Exam 2021-22 Solutions

> [!info] Paper
> Answer Q1 (30 marks) and **two** of Q2–Q4 (35 marks each). The Thermofluids Data Book is provided (ISA Table 25, gas properties Table 2).

## Q1: CO₂/N₂* mixture in a converging nozzle

### (i) $\gamma$ and $R$ of the mixture (6)
From Data Book Table 2:
- CO₂: $c_p = 0.82$, $c_v = 0.63$ kJ kg⁻¹ K⁻¹, $\mathcal M = 44$.
- Atmospheric nitrogen N₂*: $c_p = 1.03$, $c_v = 0.74$, $\mathcal M = 28.15$.

Mass fractions are 0.25 and 0.75, and specific properties are **mass-weighted** (see [[Gas Mixtures and Dalton's Law]]):

$$
c_p = 0.25(0.82)+0.75(1.03) = 0.9775,\qquad c_v = 0.25(0.63)+0.75(0.74) = 0.7125\text{ kJ kg}^{-1}\text{ K}^{-1}
$$

$$
\boxed{\gamma = \frac{c_p}{c_v} = 1.372}
$$

Molar mass from the mole numbers per kg:

$$
\frac1{\mathcal M} = \frac{0.25}{44}+\frac{0.75}{28.15} = 0.03232\;\Rightarrow\;\mathcal M = 30.94,\qquad \boxed{R = \frac{8314.5}{30.94} = 268.8\text{ J kg}^{-1}\text{ K}^{-1}}
$$

The mass-weighted $R$ gives 268.5, the same. The rounded table values don't satisfy $c_p-c_v = R$ exactly (0.265), as the Data Book warns.

### (ii) Critical temperature and pressure (6)
With $T_0 = 1000$ K and $p_0 = 10$ bar (reservoir):

$$
T^* = \frac{2T_0}{\gamma+1} = \frac{2000}{2.372} = \boxed{843\text{ K}},\qquad p^* = p_0\left(\frac{2}{\gamma+1}\right)^{\gamma/(\gamma-1)} = 10(0.8432)^{3.688} = \boxed{5.33\text{ bar}}
$$

(With cold air instead: 833 K and 5.28 bar.)

### (iii)(a) Mass flow at $p_b = 1$ bar (6)
$p_b = 1$ bar is below $p^* = 5.33$ bar, so the converging nozzle is **choked**: the exit is at M = 1 and $p_e = p^*$.

$$
\dot m = A\,p_0\sqrt{\frac{\gamma}{RT_0}}\left(\frac2{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}} = 0.002(10^6)\sqrt{\frac{1.372}{268.8(1000)}}(0.5805) = \boxed{2.62\text{ kg/s}}
$$

### (iii)(b) Thrust as a rocket, ignoring pressure thrust (6)

$$
V_e = a^* = \sqrt{\gamma RT^*} = \sqrt{1.372(268.8)(843.2)} = 557.6\text{ m/s},\qquad F = \dot mV_e = \boxed{1.46\text{ kN}}
$$

Including the pressure thrust $(p^*-p_b)A = 0.87$ kN, the total would be 2.33 kN.

### (iv) Three ways to increase thrust (6)
The momentum thrust of a choked converging nozzle is $F = \dot ma^* = \rho^*a^{*2}A = \gamma p^*A$, which is proportional to $p_0A$.
1. **Raise the reservoir pressure $p_0$**: $\dot m\propto p_0$ at fixed $T_0$, and $a^*$ is unchanged, so $F\propto p_0$. Doubling to 20 bar doubles the momentum thrust.
2. **Increase the exit (throat) area $A$**: more mass flow at the same exit velocity, so $F\propto A$. More propellant is used, though.
3. **Add a diverging section** (C–D nozzle) designed for $p_e = p_b = 1$ bar ($A_e/A_t = 1.97$). The flow then expands supersonically to $V_e = 953$ m/s at the same $\dot m$, so $F = 2.50$ kN (+71 % on the momentum thrust, and more than the 2.33 kN total of the choked converging nozzle). This converts the pressure excess into jet velocity. It is the most propellant-efficient change, since $I_{sp}$ rises.

Also acceptable:
- **A lighter gas or a higher $T_0$** raise the exhaust velocity $a^*\propto\sqrt{\gamma RT_0}$, but the choked $\dot m\propto1/\sqrt{RT_0}$ falls in proportion. So momentum thrust at a fixed $p_0$ and $A$ **is unchanged**; only $I_{sp}$ improves.
- **Operating at a lower ambient pressure** (altitude) increases the pressure thrust.

---

## Q2: Ideal ramjet at 20 km, M 3.2

### (i) $T$–$s$ diagram (4)
Four processes:
1. isentropic ram compression $a\to02$ (vertical line up to the $p_{01}$ isobar);
2. isobaric heat addition $02\to03$ along $p_{03} = p_{02}$ to 2200 K;
3. isentropic expansion $03\to4$ (vertical line down to $p_a$);
4. (closing the cycle) isobaric heat rejection to the atmosphere.

See [[Ramjet]] and `prop_e2324_q2_ramjet_Ts.png`, where the ideal path is the dashed line.

### (ii) Ambient conditions (4)
Data Book Table 25 at 20 km: $T/T_{sl} = 0.7519$ and $p/p_{sl} = 0.0546$.

$$
T_a = \boxed{216.7\text{ K}},\qquad p_a = \boxed{5.53\text{ kPa}}
$$

### (iii) Flight speed (4)

$$
V = 3.2\sqrt{1.4(287)(216.7)} = \boxed{944\text{ m/s}}
$$

### (iv) Fuel-air ratio (7)
$T_{02} = 216.7(1+0.2\times3.2^2) = 660.4$ K. SFEE on the burner with a 298 K reference (fuel supplied at 298 K):

$$
c_p(T_{02}-298)+f\,LCV = (1+f)c_p(T_{03}-298)\;\Rightarrow\;f = \frac{T_{03}-T_{02}}{LCV/c_p-(T_{03}-298)} = \frac{2200-660.4}{41{,}791-1902} = \boxed{0.0386}
$$

### (v) Net thrust (8)
Ideal, so $M_e = M = 3.2$ and $T_e = 2200/3.048 = 721.8$ K:

$$
V_e = 3.2\sqrt{1.4(287)(721.8)} = 1723.3\text{ m/s}
$$

$$
F = \dot m_a[(1+f)V_e-V] = 250[1.0386(1723.3)-944.2] = \boxed{211\text{ kN}}
$$

(195 kN if the fuel mass is neglected.)

### (vi) Exhaust composition, kerosene C₁₀H₂₁ (8)
Stoichiometric reaction per kmol of fuel:

$$
\mathrm{C_{10}H_{21}+15.25\,(O_2+3.762\,N_2^*)\to10\,CO_2+10.5\,H_2O+57.37\,N_2^*}
$$

$$
AFR_{st} = \frac{15.25(32+3.762\times28.15)}{162} = 12.98,\qquad f_{st} = 0.0770,\qquad \phi = \frac{0.0386}{0.0770} = 0.501
$$

(The question's molar mass of 162 kg/kmol is used as given; C₁₀H₂₁ would strictly be 141 kg/kmol, which would give $AFR_{st} = 14.9$.)

Lean mixture: the air supplied is $15.25/\phi = 30.44$ kmol O₂ per kmol fuel.

| Product | kmol | Volume % |
|---|---|---|
| CO₂ | 10 | **6.66** |
| H₂O | 10.5 | **6.99** |
| O₂ (excess) | 30.44 − 15.25 = 15.19 | **10.11** |
| N₂* | 3.762 × 30.44 = 114.50 | **76.24** |
| Total | 150.2 | 100 |

For a perfect gas, volume fraction = mole fraction. See [[Stoichiometry and Equivalence Ratio]].

---

## Q3: Turbofan with bpr 10, fpr 1.5, equal jets

### (i) Bypass-air $T$–$s$ path (4)
1. Ambient static state $a$ (217 K, 21.7 kPa).
2. Isentropic intake: the **stagnation** state $02$ (244.8 K, 33.1 kPa) lies vertically above it, and the static state at fan face is somewhat below $T_{02}$.
3. The fan compresses to $013$ (278.2 K, 49.6 kPa). The line slopes to the **right** ($\eta_f = 0.9$), ending above the isentropic point.
4. The isentropic nozzle expands vertically down from $013$ to the static exit state $19$ at $p_a$: 219.6 K, slightly **hotter** than $T_a$ (the fan's entropy rise).
5. Stagnation $T_0$ is constant in the intake and nozzle. Draw the static and stagnation points joined by vertical dashed lines.

### (ii) Propulsive efficiency (16)

$$
V = 0.8\sqrt{1.4(287)(217)} = 236.2\text{ m/s},\qquad T_{02} = 244.8\text{ K},\qquad p_{02} = 33.08\text{ kPa}
$$

$$
T_{013} = 244.8\left[1+\frac{1.5^{0.2857}-1}{0.9}\right] = 278.2\text{ K},\qquad p_{013} = 49.62\text{ kPa}
$$

$$
V_{j} = \sqrt{2(1005)(278.2)\left[1-\left(\frac{21.7}{49.62}\right)^{0.2857}\right]} = 343.0\text{ m/s}
$$

Both jets are at 343.0 m/s and $f$ is neglected, so:

$$
\eta_P = \frac{2}{1+V_j/V} = \frac{2}{1+343.0/236.2} = \boxed{0.816}
$$

### (iii) Effect of a higher bypass ratio (≤ 250 words) (10)
- With the core (OPR, TET) unchanged, the LPT's available power is roughly fixed. Spreading that power over a **larger bypass flow** means each kg receives less work. So the **fan pressure ratio must fall** (to keep $V_{j,bypass}\approx V_{j,core}$ for the best $\eta_P$).
- A lower fpr gives a lower $V_j$, and **$\eta_P = 2/(1+V_j/V)$ rises**. With $\eta_{th}$ unchanged, $\eta_O$ rises, so **TSFC and fuel burn fall**.
- Specific thrust $\approx V_j-V$ falls, so **more total air flow** (a bigger fan) is needed for the same thrust.
- **Limits**:
  - diameter, nacelle weight and nacelle drag (wetted area $\propto D^2$);
  - installation (ground clearance under the wing);
  - LPT stage count, because the fan must turn more slowly (tip Mach), so a gearbox is needed;
  - at very low fpr the bypass nozzle becomes unchoked and sensitive, and a variable-area nozzle may be needed;
  - the fan becomes sensitive to intake distortion.
- So fuel burn improves with bpr up to an optimum where the installation penalties (weight, drag) cancel the $\eta_P$ gain. See `prop_turbofan_fpr.png` and [[Bypass Ratio and Fan Pressure Ratio]].

### (iv) LPT exit temperature (5)
The LPT drives the fan for the bypass air (10 kg per kg of core) **and** the fan root plus LPC for the core, which goes from $T_{02} = 244.8$ K to 330 K. Per kg of core, with the fuel neglected:

$$
T_{04}-T_{05} = BPR(T_{013}-T_{02})+(T_{025}-T_{02}) = 10(33.40)+(330-244.8) = 419.3\text{ K}
$$

$$
T_{05} = 1000-419.3 = \boxed{581\text{ K}}
$$

---

## Q4: Axial compressor stage

### (i) Compressor characteristic (6)
![[prop_compressor_map.png|620]]

- Pressure ratio against $\dot m\sqrt{T_{01}}/p_{01}$, with constant-$N/\sqrt{T_{01}}$ lines that steepen at high speed (vertical at **choke**).
- A **surge line** joins the peak of each speed line on the left.
- Efficiency islands are centred near the design point.
- The working line lies between them with a surge margin.

See [[Compressor and Turbine Characteristics]].

### (ii) Model test speed (4)
Same non-dimensional speed $ND/\sqrt{T_{01}}$:

$$
N_m = N_f\frac{D_f}{D_m}\sqrt{\frac{T_{01,m}}{T_{01,f}}} = 20{,}000(5)\sqrt{\frac{200}{300}} = \boxed{81{,}650\text{ rpm}}
$$

### (iii) Power ratio (4)
Same non-dimensional flow $\dot m\sqrt{c_pT_{01}}/(D^2p_{01})$ and the same $\Delta T_0/T_{01}$. So:

$$
\dot W = \dot mc_p\Delta T_0\propto D^2p_{01}\sqrt{T_{01}}
$$

At equal inlet pressure:

$$
\frac{\dot W_f}{\dot W_m} = 5^2\sqrt{\frac{300}{200}} = \boxed{30.6}
$$

The model rig needs only 3.3 % of the full-scale power, which is the point of the scaled, cold test. See [[Dimensional Analysis of Turbomachines]].

### (iv)–(v) Blades and velocity triangles (16)
$U = 280$ m/s, $V_x = 0.5U = 140$ m/s, $\alpha_1 = \alpha_3 = +23^\circ$, $\Delta h_0 = 0.4U^2 = 31.36$ kJ/kg (Euler: $\Delta V_\theta = 0.4U = 112$ m/s).

![[prop_e2122_q4_triangles.png|720]]

| | Absolute $V_\theta$ | $V$ | $\alpha$ | Relative $W_\theta = V_\theta-U$ | $W$ | $\beta$ |
|---|---|---|---|---|---|---|
| Rotor inlet (1) | 59.4 | **152.1** | 23.0° | −220.6 | **261.3** | **−57.6°** |
| Rotor exit (2) | 171.4 | **221.3** | **50.8°** | −108.6 | **177.2** | **−37.8°** |

- The rotor blades turn the relative flow from −57.6° to −37.8° (19.8°), diffusing $W$ from 261 to 177 m/s ($W_2/W_1 = 0.68$, just below the de Haller limit of 0.72, so heavily loaded).
- The stator turns the absolute flow from 50.8° back to 23°.
- Blade sketches: cambered compressor aerofoils, with the rotor leading edge aligned to $\beta_1$ and the stator leading edge to $\alpha_2$. Both are staggered, and the flow decelerates in both rows.

See [[Velocity Triangles]].

### (vi) Throttling at constant speed (5)
Closing the exit throttle reduces $\dot m$, so $V_x$ and $\phi$ fall. With $U$ fixed, the rotor's relative inlet angle becomes more tangential, meaning **positive incidence**.
- **Pressure ratio** rises along the speed line (more turning and work: with fixed blade exit angle, $\psi = 1-\phi(\tan\alpha_1+\tan|\beta_2|)$, which gives 0.40 at design, rises as $\phi$ falls) and peaks near the surge line.
- **Efficiency** passes through its maximum at design incidence, then falls as the suction-surface boundary layers thicken and separate.
- **Flow pattern**:
  1. boundary layers thicken and separate on the suction surfaces;
  2. **rotating stall** follows: stalled cells, covering part of the annulus, propagate around it at about 50 % of rotor speed;
  3. finally **surge**: the whole annulus stalls, the machine can no longer hold the downstream pressure, and flow **reverses**, oscillating violently.

See [[Compressor Stall and Surge]].

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2021-22" and extras)
