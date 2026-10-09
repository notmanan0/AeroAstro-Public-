---
title: "SESA2023 Exam 2020-21 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2020-21"
tags: [sesa2023, exam-solutions, past-papers, open-book]
topics: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-202021-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2020-21 Solutions

> [!info] Paper
> Online open-book assessment (the recommended time is 2–4 h). Answer all four questions, 25 marks each. This is the first paper written for the **current syllabus**: compressible flow, real ramjet, reheat turbojet and turbofan LPT design. ISA values come from the Data Book (Table 24, ft).

## Q1: C–D nozzle and normal shock

### (i) Pressure distributions as $p_b$ falls (9)
![[prop_cd_nozzle_regimes.png|700]]

As $p_b/p_0$ is lowered from 1:
1. **$p_b = p_0$**: no flow.
2. **Subsonic venturi**: $p$ dips to a minimum at the throat and recovers. The flow is subsonic everywhere, and $\dot m$ rises as $p_b$ falls.
3. **First critical** ($p_b = p_{e,sub}$): M = 1 at the throat only; subsonic diffusion afterwards. **The throat is now choked**, so $\dot m$ is fixed at its maximum and is independent of any further fall in $p_b$.
4. **Normal shock in the divergent section**: supersonic expansion after the throat is terminated by a normal shock. The pressure jumps, then the subsonic flow diffuses to $p_b$. The shock moves downstream as $p_b$ falls.
5. **Shock at the exit plane**.
6. **Over-expanded** ($p_e<p_b$): isentropic supersonic flow inside the nozzle. Oblique shocks outside raise the pressure to $p_b$.
7. **Design point** ($p_b = p_e$): fully expanded, shock-free jet.
8. **Under-expanded** ($p_b<p_e$): expansion fans outside the nozzle.

Key features to name: choked throat, sonic line, normal shock, oblique shocks and expansion fans at the lip, jet boundary. See [[Converging-Diverging Nozzle Operating Regimes]].

### (ii) Argon normal shock (9)
$\gamma = 1.67$, $R = 208$, $V_1 = 700$ m/s, $p_1 = 125$ kPa, $T_1 = 350$ K:

$$
a_1 = \sqrt{1.67(208)(350)} = 348.7\text{ m/s},\qquad M_1 = 2.008
$$

$$
\frac{p_2}{p_1} = 1+\frac{2\gamma}{\gamma+1}(M_1^2-1) = 4.791\Rightarrow\boxed{p_2 = 599\text{ kPa}},\qquad \frac{\rho_2}{\rho_1} = \frac{(\gamma+1)M_1^2}{(\gamma-1)M_1^2+2} = 2.289\Rightarrow\boxed{V_2 = \frac{700}{2.289} = 306\text{ m/s}}
$$

Also $M_2 = 0.606$, $T_2 = 732$ K and $p_{02}/p_{01} = 0.760$. See [[Normal Shock Waves]]: the relations hold for any $\gamma$ (not the $\gamma = 1.4$ tables).

### (iii) Same velocity change, isentropically (5)
Adiabatic, so $T_0 = 350+700^2/(2c_p) = 822.6$ K with $c_p = \gamma R/(\gamma-1) = 518.4$. The same exit velocity (306 m/s) therefore gives the **same** $T_2 = 732.4$ K. Isentropically:

$$
p_{2,s} = p_1\left(\frac{T_2}{T_1}\right)^{\gamma/(\gamma-1)} = 125\left(\frac{732.4}{350}\right)^{2.49} = \boxed{787\text{ kPa}}
$$

With the fallback 200 m/s drop: $T = 581.5$ K, giving 443 kPa.

### (iv) Is the shock pressure larger? (2)
**No.** Both processes have the same $T_0$ and the same final $V$ and $T$, but the shock generates entropy ($\Delta s = R\ln(p_{0,1}/p_{0,2}) = 57$ J kg⁻¹ K⁻¹). At the same $T$, higher entropy means lower pressure ($ds = c_p\,dT/T-R\,dp/p$). So $p_{2,shock} = 599$ kPa is **less than** $p_{2,isentropic} = 787$ kPa. The isentropic diffuser recovers more pressure, and the difference is the shock's irreversibility.

---

## Q2: Real ramjet

### (i) Specific thrust (16)
M 2.5, $T_a = 260$ K, $T_{03} = 2850$ K, LCV 42 MJ/kg at 298 K, $\Gamma_d = 0.87$, $\Gamma_c = 0.94$, $\Gamma_n = 0.72$, fully expanded, air properties.

$$
V = 2.5\sqrt{1.4(287)(260)} = 808.0\text{ m/s},\qquad T_{02} = 260(2.25) = 585.0\text{ K}
$$

Burner, with reactants and products referred to 298 K:

$$
f = \frac{T_{03}-T_{02}}{LCV/c_p-(T_{03}-298)} = \frac{2265}{41{,}791-2552} = 0.0577
$$

Nozzle expansion ratio (static exit = ambient):

$$
\frac{p_{04}}{p_a} = (2.25)^{3.5}(0.87)(0.94)(0.72) = 17.09(0.5889) = 10.06
$$

$$
T_e = \frac{2850}{10.06^{0.2857}} = 1473.6\text{ K},\qquad V_e = \sqrt{2(1005)(2850-1473.6)} = 1663.3\text{ m/s}
$$

$$
\frac{F}{\dot m_a} = 1.0577(1663.3)-808.0 = \boxed{951\text{ N s/kg}}
$$

### (ii) Mach number range (4)
- **Lower limit (about M 1.5–2)**:
  - The ram pressure ratio $(1+0.2M^2)^{3.5}$ is small (3.7 at M 1.5), so there is little expansion available for the jet and a low $\eta_{th} = 1-T_a/T_{02}$.
  - There is no static thrust at all, so the vehicle needs a booster.
- **Upper limit (about M 5–6)**:
  - $T_{02}$ approaches the material and stoichiometric limit on $T_{03}$, so the heat added and the thrust go to zero.
  - The subsonic combustor sees very high static temperatures, so dissociation absorbs the heat release.
  - Normal-shock losses and wall heating grow.
  - Above this, **scramjets** keep the combustor flow supersonic.

### (iii) Real vs ideal ramjet losses (5)
- **Intake**: shock losses (the normal shock is the dominant loss), boundary-layer friction, shock–boundary-layer interaction and separation, and spillage and bleed. These give $\Gamma_d<1$.
- **Combustor**:
  - The **Rayleigh loss**: heat added to a moving flow lowers $p_0$ (see [[Friction and Heat Addition in Constant-Area Ducts]]).
  - Flame-holder drag and mixing losses.
  - Incomplete combustion and dissociation ($\eta_b<1$).
  - Wall heat loss.
- **Nozzle**: friction, divergence (non-axial exit flow), off-design over- or under-expansion, and non-equilibrium (frozen) chemistry.
- **Gas properties**: the higher $c_p$ and lower $\gamma$ of the products.

All of these lower $p_{04}/p_a$ or $T_{04}$, so $V_e$ and the thrust fall. See [[Component Stagnation Pressure Ratios]].

---

## Q3: Reheat turbojet at M 1.5, 31,000 ft

ISA at 31,000 ft: $T_a = 226.73$ K and $p_a = 28.7$ kPa. Air $c_p = 1005$, $\gamma = 1.4$; products $c_p = 1200$, $\gamma = 1.35$ (so $\gamma/(\gamma-1) = 3.857$).

### (i) Afterburner off (10)
![[prop_e2021_q3_reheat_Ts.png|680]]

| Station | Working | Result |
|---|---|---|
| Flight | $V = 1.5\sqrt{1.4(287)(226.73)}$ | 452.7 m/s |
| Intake (isentropic) | $T_{02} = 226.73(1.45)$; $p_{02} = 28.7(1.45)^{3.5}$ | 328.8 K, 105.4 kPa |
| Compressor | $T_{03} = 328.8[1+(18^{0.2857}-1)/0.88]$ | **808.4 K**, $p_{03} = 1896$ kPa |
| Burner (298 K ref.) | $f = \dfrac{1200(1600-298)-1005(808.4-298)}{43\times10^6-1200(1600-298)}$ | **$f = 0.02533$** |
| Turbine | $1005(808.4-328.8) = 1.02533(1200)(1600-T_{05})$ | $T_{05} = $ **1208.3 K**, $T_{05s} = 1174.2$ K, $\pi_t = 3.30$, $p_{05} = 574.9$ kPa |
| Nozzle | $V_j = \sqrt{2(1200)(1208.3)[1-(28.7/574.9)^{0.2593}]}$ | **$V_j = 1252$ m/s**, $T_9 = 555$ K |

The mass flow isn't given, so the "net thrust" is per unit air mass flow:

$$
\frac{F}{\dot m_a} = (1+f)V_j-V = \boxed{831\text{ N s/kg}},\qquad \text{TSFC} = \frac{f}{F/\dot m_a} = \boxed{30.5\text{ g kN}^{-1}\text{ s}^{-1}}
$$

$$
\eta_P = \frac{FV}{\tfrac12\dot m_a[(1+f)V_j^2-V^2]} = \boxed{0.537}\quad(0.531\text{ from }2/(1+V_j/V))
$$

### (ii) Afterburner lit, $T_{08} = 1800$ K (10)
Same $\dot m_a$ and $p_{05}$, so the nozzle pressure ratio is unchanged.

$$
f_{ab} = \frac{1.02533(1200)(1800-1208.3)}{43\times10^6-1200(1800-298)} = 0.01767,\qquad f_{tot} = 0.0430
$$

$$
V_j = \sqrt{2(1200)(1800)(0.5403)} = \boxed{1528\text{ m/s}},\qquad \frac{F}{\dot m_a} = 1.043(1527.7)-452.7 = \boxed{1141\text{ N s/kg}}
$$

$$
\text{TSFC} = \boxed{37.7\text{ g kN}^{-1}\text{ s}^{-1}},\qquad \eta_P = \boxed{0.463}
$$

On the $T$–$s$ diagram, the afterburner adds an isobar $p_{05}$ from 1208 K to 1800 K, and the expansion to $p_a$ now starts from the higher $T$.

**Nozzle throat area**: the throat is choked, so $\dot m = A_8p_0\Gamma/\sqrt{RT_0}$. With $p_0$ fixed:

$$
\frac{A_{8,ab}}{A_{8,dry}} = \frac{1+f_{tot}}{1+f}\sqrt{\frac{1800}{1208.3}} = \frac{1.0430}{1.0253}(1.2206) = 1.242\;\Rightarrow\;\boxed{+24\%}
$$

**Summary**: thrust **+37 %**, TSFC **+24 %**, $\eta_P$ down from 0.54 to 0.46 (a faster jet).

### (iii) Alternatives to reheat (≤ 250 words) (5)
- **Higher TET** (better materials, cooling and TBCs): raises specific thrust *and* $\eta_{th}$, so TSFC barely rises. But it needs costly cooling technology, and turbine life falls sharply (creep life roughly halves per +10–15 K). Reserve it for short take-off ratings.
- **Larger engine / more mass flow** (a bigger compressor, or a higher OPR at a fixed TET): more thrust at a similar TSFC. But the engine is heavier and has a larger frontal area, hence more drag, especially supersonic.
- **Low-bypass turbofan or variable-cycle engine**: adds a slower bypass stream (a better $\eta_P$ at subsonic speed), with a mode switch for high thrust. It is complex and heavier.
- **Water/methanol injection**: cools the compressor air (more mass flow and a lower $T_{03}$ for the same TET, so more fuel), giving short-term take-off boost. It needs a consumable tank and has little effect at altitude.
- **Rocket assist (JATO)**: very high thrust briefly, but very high propellant consumption and logistics.

Reheat remains attractive because it gives +40–70 % thrust from a **light, simple** add-on, used only briefly. The alternatives trade mass, cost or life for a better TSFC.

---

## Q4: Three-spool turbofan LPT design (M 0.8, 35,000 ft)

ISA 35,000 ft: $T_a = 218.81$ K and $p_a = 23.8$ kPa. Cold air throughout; fuel flow neglected.

### (i) Downstream of the fan (3)

$$
T_{02} = 218.81(1.128) = 246.8\text{ K},\qquad p_{02} = 23.8(1.128)^{3.5} = 36.28\text{ kPa}
$$

$$
T_{013} = 246.8\left[1+\frac{1.6^{0.2857}-1}{0.9}\right] = \boxed{286.2\text{ K}},\qquad p_{013} = 1.6(36.28) = \boxed{58.05\text{ kPa}}
$$

### (ii) LPT stage count, direct drive (12)
- **Fan speed**: $\Omega = U_{tip}/r_{tip} = 300/1.25 = 240$ rad/s (2292 rpm). The LPT turns at the same speed, so the mean-line blade speed is $U = 0.4(240) = \mathbf{96\text{ m/s}}$.
- **LPT work** (per kg of core flow, which is the LPT flow): the fan compresses $1+BPR = 13$ kg for every kg of core.

$$
\Delta h_{0,LPT} = 13c_p(T_{013}-T_{02}) = 13(1005)(39.41) = 515\text{ kJ/kg}
$$

- **Stage loading**: choose **$\psi = 2.5$**. That is the practical upper limit for turbines (see [[Flow and Work Coefficients]]); higher loading means excessive turning, high exit Mach numbers and shock losses, and a sharp fall in efficiency. LPTs are designed for the highest loading they tolerate, precisely because $U$ is so low.

$$
n = \frac{\Delta h_{0,LPT}}{\psi U^2} = \frac{514{,}947}{2.5(96)^2} = 22.4\;\Rightarrow\;\boxed{23\text{ stages}}
$$

(Choosing $\psi = 2$ gives 28 stages.) That is completely impractical: it would be far too long and heavy. The LPT exit temperature is $T_0 = 1100-514{,}947/1005 = 588$ K.

### (iii) Geared fan, ×3 (5)
The LPT now turns 3× faster, so $U = 288$ m/s. Stage count scales as $1/U^2$, so it falls by 9×:

$$
n = \frac{514{,}947}{2.5(288)^2} = 2.48\;\Rightarrow\;\boxed{3\text{ stages}}
$$

### (iv) Advantages of the geared turbofan for the LPT (≤ 200 words) (5)
- The fan tip speed is capped (about 300–450 m/s) by shock noise, efficiency and blade loads. In a direct drive this forces a slow LPT, and with $\Delta h_0 = \psi U^2$ a slow turbine needs **many stages**: Trent 1000 about 6–7, GEnx 7, both with large mean radii to raise $U$.
- A reduction gearbox (GTF, e.g. the PW1000G/GT1524) lets the LPT spin about 3× faster, so the work per stage rises 9×:
  - **Far fewer stages** (3 against 7 in real engines; 3 against 23 here): shorter, lighter, fewer aerofoils, lower cost and maintenance.
  - A **smaller LPT radius** is possible, which suits a smaller core.
  - It can run at a **lower $\psi$ with a better $\phi$**, i.e. nearer peak efficiency on the Smith chart.
  - The fan can be slowed further, enabling **higher bpr and lower fpr** (better $\eta_P$ and less noise) without penalising the turbine.
- **Costs**: gearbox mass, about 1 % transmission loss (heat rejection requiring oil cooling), and reliability risk.

See [[Bypass Ratio and Fan Pressure Ratio]].

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2020-21")
