---
title: "SESA2023 Exam 2023-24 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2023-24"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-202324-02-SESA2023.pdf"]
---

# SESA2023 Exam 2023-24 Solutions

> [!info] Paper
> Answer all four questions, 25 marks each. The Thermofluids Data Book is provided. Cold air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$.

## Q1: Propane ramjet combustion

### (i) Enthalpy of reactants and products (4)
With no heat transfer, no work, no pressure loss and negligible kinetic energy, the SFEE gives **$H_{reactants} = H_{products}$**. The total enthalpy (formation plus sensible) is **unchanged**. The chemical (formation) enthalpy released reappears as sensible enthalpy, so the product temperature rises to the adiabatic flame temperature. See [[Adiabatic Flame Temperature]].

### (ii) Ideal vs real combustion (4)
1. **Incomplete combustion and dissociation** (CO, H₂, OH, unburnt fuel): less heat released, so a lower $T_{03}$.
2. **Stagnation-pressure loss**: heat addition to a moving flow (the Rayleigh loss) plus flame-holder and mixing drag.

Also: heat loss to the walls.

All of these reduce the jet velocity and thrust, and raise the fuel consumption.

### (iii) Fuel flow for stoichiometric propane, 50 kg/s of air (10)
$$
\mathrm{C_3H_8+5\,(O_2+3.762\,N_2^*)\to3\,CO_2+4\,H_2O+18.81\,N_2^*}
$$

$$
AFR_{st} = \frac{5(32+3.762\times28.15)}{44} = \frac{5(137.9)}{44} = 15.67,\qquad \dot m_f = \frac{50}{15.67} = \boxed{3.19\text{ kg/s}}
$$

(With air as 29 kg/kmol, $5\times4.762\times29/44 = 15.69$, the same to three significant figures.) See [[Stoichiometry and Equivalence Ratio]].

### (iv) Overall efficiency at M 2, 20 km, $F = 40$ kN (7)
$T_a = 216.7$ K (Table 25), so $V = 2\sqrt{1.4(287)(216.7)} = 590.1$ m/s. Propane LCV = 46.36 MJ/kg (Data Book Table 1).

$$
\eta_O = \frac{FV}{\dot m_fLCV} = \frac{40{,}000(590.1)}{3.19(46.36\times10^6)} = \boxed{0.160}
$$

Only 16 %: a stoichiometric mixture wastes fuel (a high $V_j$, so a low $\eta_P$) and M 2 is at the bottom of the ramjet's efficient range.

---

## Q2: Ramjet with measured pressures (20 km, M 3.2, $T_{03} = 2200$ K, $f = 0.05$, 250 kg/s)

### (i) $T$–$s$ diagram with losses (6)
![[prop_e2324_q2_ramjet_Ts.png|700]]

The ideal path is dashed: $a\to01$ isentropic, isobaric heating at $p_{01}$, isentropic expansion to $p_a$. The real path is solid:
- the diffuser ends on a **lower isobar** $p_{02}<p_{01}$ (entropy rises at constant $T_0$);
- the burner heats while $p_0$ falls further ($p_{03}<p_{02}$);
- the nozzle loses $p_0$ ($p_{04}<p_{03}$), so the exhaust ends hotter (950 K against the ideal 722 K).

The jet velocity is lower.

### (ii) Diffuser and burner stagnation-pressure ratios (6)
Ambient: $T_a = 216.7$ K and $p_a = 5.532$ kPa (Table 25).

$$
p_{01} = p_a\left(1+0.2\times3.2^2\right)^{3.5} = 5.532(49.44) = 273.5\text{ kPa}
$$

The kinetic energy is negligible between the diffuser exit and the nozzle entry, so the static pressures there **are** stagnation pressures:

$$
\Gamma_d = \frac{p_{02}}{p_{01}} = \frac{164.1}{273.5} = \boxed{0.600},\qquad \Gamma_b = \frac{p_{03}}{p_{02}} = \frac{147.7}{164.1} = \boxed{0.900}
$$

### (iii) Nozzle stagnation-pressure ratio (5)
The nozzle is adiabatic, so $T_{04} = T_{03} = 2200$ K. The exit is fully expanded ($p_4 = p_a$) at $T_4 = 950$ K. Relating the exit's own stagnation state to its static state:

$$
p_{04} = p_a\left(\frac{T_{04}}{T_4}\right)^{3.5} = 5.532\left(\frac{2200}{950}\right)^{3.5} = 104.6\text{ kPa},\qquad \Gamma_n = \frac{104.6}{147.7} = \boxed{0.708}
$$

### (iv) Thrust against the loss-free engine (8)
$$
V = 944.2\text{ m/s},\qquad V_e = \sqrt{2c_p(T_{04}-T_4)} = \sqrt{2(1005)(1250)} = 1585\text{ m/s}
$$

$$
F = 250[1.05(1585.1)-944.2] = \boxed{180\text{ kN}}
$$

**Without losses** (ideal, so $M_e = 3.2$ and $T_e = 721.8$ K): $V_e = 1723$ m/s, giving $F = 250[1.05(1723.3)-944.2] = \boxed{216\text{ kN}}$.

The losses ($\Gamma_{total} = 0.600\times0.900\times0.708 = 0.382$) cost **17 %** of the thrust. The intake is the main culprit: $\Gamma_d = 0.6$ is typical of a single normal-shock intake at M 3.2. See [[Intake Pressure Recovery]] and [[Component Stagnation Pressure Ratios]].

---

## Q3: Electric ducted fans

### (i) Under-wing nacelles or in the fuselage wake? (≤ 100 words) (5)
**Power is lower in the fuselage wake**, through **boundary-layer ingestion** (BLI).
- The wake air arrives slower than the flight speed, so the fan needs to add less kinetic energy to produce the same momentum increase.
- For thrust $F = \dot m(V_j-V_{in})$, the power needed is $P = \tfrac12\dot m(V_j^2-V_{in}^2)$. A lower $V_{in}$ reduces $P$ for the same $F$.
- It also re-energises the wake, reducing the momentum deficit (drag) the aircraft leaves behind.
- The penalty is distorted inflow, which makes the fan less efficient and increases aeromechanical loading.

### (ii) Schematic and $T$–$s$ (5)
- **Schematic**: intake (1 → 2), fan (2 → 3), nozzle (3 → 4), driven by an electric motor.
- **$T$–$s$**:
  - ambient static $a$ (230 K);
  - vertical line up to the stagnation state $01 = 02$ (261.1 K, isentropic intake);
  - the fan to $03$ on the higher isobar, sloping right ($\eta = 0.9$);
  - a vertical isentropic expansion from $03$ down to $p_a$ at static state 4, slightly hotter than ambient.

### (iii) Fan exit stagnation temperature (8)
$$
T_{01} = T_a+\frac{V^2}{2c_p} = 230+\frac{250^2}{2010} = 261.1\text{ K}
$$

$$
T_{03} = T_{01}\left[1+\frac{1.1^{0.2857}-1}{0.9}\right] = 261.1(1.03067) = \boxed{269.1\text{ K}}\quad(\Delta T_0 = 8.0\text{ K})
$$

### (iv) Hydrogen vs renewable liquid fuel and range (≤ 100 words) (4)
- Breguet: $s = \eta_O\frac{LCV}{g}\frac LD\ln\frac{m_1}{m_2}$.
- **LH₂**: an LCV of 120 MJ/kg (2.8× kerosene), so much more range per kg of fuel. But the density is about 71 kg/m³, needing about 4× the volume. Heavy insulated cryogenic tanks (inside the fuselage) raise the empty mass, and a longer fuselage raises drag, so $L/D$ falls and the usable fuel fraction falls.
- **Renewable liquid fuel (SAF)**: kerosene-like (about 43 MJ/kg) and a drop-in with existing tanks and $L/D$, but a much lower energy per kg.
- The net range depends on which effect dominates.

### (v) Maximum cruise range (3)
$$
s = \eta_O\frac{LCV}{g}\frac LD\ln\frac{m_1}{m_2} = 0.39\left(\frac{120\times10^6}{9.81}\right)(21)\ln\frac{100}{92} = \boxed{8350\text{ km}}
$$

See [[Breguet Range Equation]].

---

## Q4: Propeller and actuator disk

### (i) Section and velocity triangles (6)
- A cambered aerofoil section, set at a large pitch angle to the plane of rotation near the tip.
- **Inlet**: the absolute velocity is axial ($V_\infty$ plus the induced velocity), the blade velocity is $U = \Omega r$ in the plane of rotation, and the relative velocity $W_1 = V-U$ approaches at angle $\beta_1$ from the axis. The blade is set at a small angle of attack to $W_1$.
- **Outlet**: the absolute velocity has a higher axial component and a small swirl component in the direction of rotation. $W_2$ is turned slightly towards the axis.

See [[Velocity Triangles]] and [[Actuator Disk Theory]].

### (ii) Advance ratio (3)
$$
J = \frac{V_\infty}{nD}
$$

Here $V_\infty$ is the flight speed (m/s), $n$ the rotational speed (rev/s) and $D$ the propeller diameter (m). $\pi/J = U_{tip}/V_\infty$ is the tip-speed ratio.

### (iii) Distributions through an actuator disk (6)
- **Axial velocity**: rises smoothly from $V_\infty$ upstream, through $V_{disk}$ at the disk, to $V_j$ far downstream. It is **continuous** across the disk (mass conservation with equal areas).
- **Static pressure**: falls below $p_\infty$ approaching the disk (the flow accelerates), **jumps** by $\Delta p$ at the disk, then recovers to $p_\infty$ far downstream.
- **Stagnation pressure**: constant $p_{0\infty}$ upstream, jumps by $\Delta p$ at the disk (work input), then constant downstream.

### (iv) $V_{disk} = \tfrac12(V_\infty+V_j)$ (6)
1. **Momentum** on a control volume around the whole streamtube: $T = \dot m(V_j-V_\infty)$ with $\dot m = \rho AV_{disk}$.
2. **Pressure jump**: Bernoulli applies separately upstream and downstream of the disk (no work within each part):
   - $p_{0,up} = p_\infty+\tfrac12\rho V_\infty^2$;
   - $p_{0,down} = p_\infty+\tfrac12\rho V_j^2$;
   - so $\Delta p = \tfrac12\rho(V_j^2-V_\infty^2)$.
3. The force on the disk is $T = A\Delta p$.
4. Equate the two: $\rho AV_{disk}(V_j-V_\infty) = \tfrac12\rho A(V_j-V_\infty)(V_j+V_\infty)$, so $V_{disk} = \tfrac12(V_\infty+V_j)$ $\blacksquare$.

Half the velocity increase happens upstream of the disk.

### (v) Relative inlet angle at the tip (4)
$V_\infty = 100$ m/s and $V_j = 120$ m/s, so $V_{disk} = 110$ m/s. With $J = 1.1$:

$$
nD = \frac{100}{1.1} = 90.9\text{ m/s},\qquad U_{tip} = \pi nD = 285.6\text{ m/s}
$$

$$
\beta_{tip} = \arctan\frac{U_{tip}}{V_{disk}} = \arctan\frac{285.6}{110} = \boxed{68.9^\circ\text{ from the axis}}\ (21.1^\circ\text{ from the plane of rotation})
$$

The tip relative Mach number is about $\sqrt{110^2+285.6^2}/a$, which is 0.9 at low altitude. This is why propellers are limited to modest flight speeds.

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2023-24")
