---
title: "SESA3029 Test 1 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Block 1: compressible-flow toolkit and Pitot probes"
tags: [sesa3029, tutorial-solutions, blackboard-test, isentropic-flow, stagnation, pitot]
sheet: "Blackboard Test 1"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]"]
status: complete
due: 2026-10-11
sources: ["03 - Exams & Past Papers/aerothermo quiz questions - solved on ipad but write own solutions for completeness.txt"]
---

# SESA3029 Test 1 - Solutions

> [!abstract] Test info
> Blackboard Test 1 (2.5% of the module, best of two attempts). Released on 5 Oct, **due Sun 11 Oct, 23:59** (L2-4, ll. 1–3). Five questions, all on Week 1 material: adiabatic and isentropic relations, mass flow, and the Pitot probe. These are worked solutions for revision, written after the questions had already been answered by hand. Every number was checked in Python with $\gamma=1.4$ and $R=287$ J/kg K.

| Q | Answer | Tool | Theory |
|---|---|---|---|
| 1 | $T=295.2$ K | adiabatic $T_0/T$ | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#4. Stagnation properties\|W01 §4]] |
| 2 | $M=2.67$ | gas law, then $T_0/T$ | W01 §3–4 |
| 3 | $\rho_2=2.23$ kg/m³ | gas law, then isentropic $p$–$\rho$ | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Isentropic relations: derivation\|W01 §3]] |
| 4 | $\dot m=0.50$ kg/s | $\dot m=\rho UA$ with $U=Ma$ | W01 §1, §3 |
| 5 | $M_1=1.163$ | isentropic $p_{02}/p_2$, then normal shock | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#7. Pitot probe: three regimes\|W01 §7]] |

All five use only the first three lines of the [[SESA3029 Formula Sheet#What the exam formula sheet gives you|exam formula sheet]] plus the shock-jump relations.

---

## Q1. Static temperature in a wind-tunnel test section

> Find the static temperature in the test section of a wind tunnel operating at $M=1.6$, given $T_0=446.4$ K. One decimal place.

The flow from the settling chamber to the test section is **adiabatic**, so $T_0$ is constant and

$$
\frac{T_0}{T}=1+\frac{\gamma-1}{2}M^2.
$$

Substitute $M=1.6$:

$$
\frac{T_0}{T}=1+0.2\times1.6^2=1+0.2\times2.56=1.512.
$$

Rearrange for $T$:

$$
T=\frac{446.4}{1.512}=\boxed{295.2\ \text{K}}.
$$

> [!check] Table route
> The IFT row $M=1.60$ gives $T/T_0=0.6614$, so $T=0.6614\times446.4=295.2$ K ✓. The numbers were chosen to give 295.2 K (about room temperature): the tunnel heats its supply air so that the test section is not freezing.

---

## Q2. Local Mach number from $T_0$, $\rho$ and $p$

> A point in a flow has $T_0=805$ K, $\rho=0.29$ kg/m³ and $p=27.6$ kPa. Find $M$ to two decimal places.

**Step 1: static temperature from the gas law.**

$$
T=\frac{p}{\rho R}=\frac{27\,600}{0.29\times287}=\frac{27\,600}{83.23}=331.6\ \text{K}.
$$

**Step 2: invert the adiabatic relation.**

$$
1+\frac{\gamma-1}{2}M^2=\frac{T_0}{T}=\frac{805}{331.6}=2.4276.
$$

$$
M^2=\frac{2.4276-1}{0.2}=7.138.
$$

$$
M=\boxed{2.67}.
$$

> [!check] Table route
> $T/T_0=331.6/805=0.4119$ lies between the IFT rows $M=2.66$ (0.4141) and $2.68$ (0.4104). Interpolation gives $M=2.66+0.02\times(0.4141-0.4119)/0.0037=2.672$ ✓.

> [!warning] Use static, not stagnation, values in the gas law
> $p=\rho RT$ links **static** quantities. Writing $p=\rho RT_0$ gives $T_0$ in place of $T$ and an answer of $M=0$, which should look wrong at once.

---

## Q3. Density at a second point in an isentropic flow

> Point 1: $p_1=342.6$ kPa, $T_1=313.4$ K. Point 2 (same isentropic flow): $p_2=161.9$ kPa. Find $\rho_2$ to two decimal places.

**Step 1: density at point 1.**

$$
\rho_1=\frac{p_1}{RT_1}=\frac{342\,600}{287\times313.4}=3.809\ \text{kg/m}^3.
$$

**Step 2: isentropic link between the two points.** From the formula sheet, $p_2/p_1=(\rho_2/\rho_1)^\gamma$, so

$$
\frac{\rho_2}{\rho_1}=\left(\frac{p_2}{p_1}\right)^{1/\gamma}=\left(\frac{161.9}{342.6}\right)^{1/1.4}=0.47257^{0.7143}=0.5854.
$$

$$
\rho_2=0.5854\times3.809=\boxed{2.23\ \text{kg/m}^3}.
$$

> [!check] Two-route check
> Get $T_2$ first: $T_2=T_1(p_2/p_1)^{(\gamma-1)/\gamma}=313.4\times0.47257^{0.2857}=253.0$ K. Then $\rho_2=p_2/(RT_2)=161\,900/(287\times253.0)=2.230$ kg/m³ ✓.

---

## Q4. Mass flow rate through a duct

> Air at $M=0.3$ in a duct of area $65$ cm². At the measuring station $p=80$ kPa and $T=480$ K. Find $\dot m$ to two decimal places.

Everything is given at **one** station as **static** values, so no stagnation relation is needed.

**Step 1: density.**

$$
\rho=\frac{p}{RT}=\frac{80\,000}{287\times480}=0.5807\ \text{kg/m}^3.
$$

**Step 2: speed of sound and velocity.**

$$
a=\sqrt{\gamma RT}=\sqrt{1.4\times287\times480}=439.2\ \text{m/s},
\qquad
U=Ma=0.3\times439.2=131.7\ \text{m/s}.
$$

**Step 3: mass flow.** Convert the area: $65\ \text{cm}^2=65\times10^{-4}\ \text{m}^2=0.0065\ \text{m}^2$.

$$
\dot m=\rho UA=0.5807\times131.7\times0.0065=\boxed{0.50\ \text{kg/s}}\quad(0.4973).
$$

> [!warning] Unit trap
> $1\ \text{cm}^2=10^{-4}\ \text{m}^2$, not $10^{-2}$. Using $10^{-2}$ gives 49.7 kg/s.

> [!tip] A compact form
> $\dot m=\rho UA=\dfrac{p}{RT}M\sqrt{\gamma RT}\,A=pMA\sqrt{\dfrac{\gamma}{RT}}$. Here $80\,000\times0.3\times0.0065\times\sqrt{1.4/(287\times480)}=0.497$ kg/s ✓.

---

## Q5. Supersonic Pitot probe with the static tapping moved behind the shock

> In Lecture 1-3 the static tapping was ahead of the Pitot probe. Now it is moved to the **rear** of the probe. The readings are 160 kPa (static tapping) and 261 kPa (Pitot). The aircraft is supersonic. Find $M$ to three decimal places.

### What each instrument now measures

In supersonic flight a detached bow shock stands ahead of the probe; on the axis it is locally **normal** ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Case 3: compressible supersonic|W01 §7, Case 3]]).

- The Pitot tube still brings the flow behind the shock to rest isentropically, so it reads $p_{02}=261$ kPa.
- A tapping **behind** the shock sits in the subsonic zone-2 flow. It reads $p_2=160$ kPa, **not** the free-stream $p_1$.

This is the trap. The measured ratio, 261/160 = 1.631, is **below** the sonic value of the Rayleigh ratio, $p_{02}/p_1=1.893$. So the Rayleigh formula (which needs $p_1$) has **no supersonic solution**. And treating the probe as subsonic would contradict the statement that the aircraft is supersonic.

### Step 1: Mach number behind the shock (isentropic, from state 2 to state 02)

Between the tapping and the Pitot mouth the flow is subsonic and isentropic, so

$$
\frac{p_{02}}{p_2}=\left(1+\frac{\gamma-1}{2}M_2^2\right)^{\gamma/(\gamma-1)}.
$$

Invert:

$$
M_2^2=\frac{2}{\gamma-1}\left[\left(\frac{p_{02}}{p_2}\right)^{(\gamma-1)/\gamma}-1\right]=5\left[1.63125^{0.2857}-1\right]=5\times0.15005=0.7503.
$$

$$
M_2=0.8662.
$$

### Step 2: free-stream Mach number (normal-shock relation, inverted)

The formula sheet gives $M_2$ in terms of $M_1$ for a normal shock ($M_{n1}=M_1$):

$$
M_2^2=\frac{2+(\gamma-1)M_1^2}{2\gamma M_1^2-(\gamma-1)}.
$$

Solve for $M_1^2$. Cross-multiply:

$$
M_2^2\left(2\gamma M_1^2-(\gamma-1)\right)=2+(\gamma-1)M_1^2.
$$

Collect the $M_1^2$ terms:

$$
M_1^2\left(2\gamma M_2^2-(\gamma-1)\right)=2+(\gamma-1)M_2^2.
$$

$$
M_1^2=\frac{2+(\gamma-1)M_2^2}{2\gamma M_2^2-(\gamma-1)}.
$$

The relation is **symmetric**: swapping 1 and 2 gives the same formula. Substitute $M_2^2=0.7503$:

$$
M_1^2=\frac{2+0.4\times0.7503}{2.8\times0.7503-0.4}=\frac{2.3001}{1.7008}=1.3524.
$$

$$
M_1=\boxed{1.163}.
$$

> [!check] Table route and consistency
> - IFT: $p_2/p_{02}=160/261=0.6130$ lies between $M=0.86$ (0.6170) and $0.88$ (0.6041), so $M_2=0.8662$.
> - NST: $M_{n2}=0.8662$ lies between $M_{n1}=1.16$ (0.8682) and $1.18$ (0.8549), so $M_1=1.16+0.02\times0.0020/0.0133=1.1631$ ✓.
> - Implied free-stream static pressure: $p_2/p_1=1+\tfrac{2\gamma}{\gamma+1}(M_1^2-1)=1.411$, so $p_1=113.4$ kPa. The Rayleigh formula with $p_1=113.4$ kPa gives $p_{02}/p_1=2.302$, i.e. $p_{02}=261$ kPa ✓.

> [!tip] Why this is a good question
> It tests whether you know **which state each instrument sees**, not just a formula. The same two numbers give three different answers depending on where the tapping is: subsonic $M=0.866$ (tapping in the free stream, flight subsonic), no solution (tapping in the free stream, flight supersonic), or $M=1.163$ (tapping behind the shock).

---

## Links

- Theory: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] · [[Compressible Pitot Probe]] · [[Rayleigh Pitot Formula]] · [[Normal-Shock Jump Relations]] · [[Stagnation Properties]]
- Module: [[SESA3029 Aerothermodynamics Hub]] · [[SESA3029 Formula Sheet]]
- Other worked sheets: [[SESA3029 Example Sheet 1 - Solutions]]

## Sources

- `03 - Exams & Past Papers/aerothermo quiz questions - solved on ipad but write own solutions for completeness.txt` (the five Test 1 questions, copied from Blackboard)
- Release and due date: `Lecture 2-4.txt`, ll. 1–3. Scope (*"the test is always looking backwards a bit"*): ll. 457–459.
- Tables: `02 - Sources/Lectures/IFT.pdf`, `NST.pdf`.

## Self-study tasks

> [!todo] Not lecturer-set beyond the test itself
> The test was set on Blackboard (L2-4, ll. 1–3). The extra tasks below are *suggested, not lecturer-set*.

- [ ] **Submit Test 1 by Sun 11 Oct, 23:59** (L2-4, l. 3); two attempts, highest mark counts.
- [ ] Redo Q5 with the tapping **ahead** of the probe and readings of 80 and 150 kPa (Lecture 1-3 Example 1). → [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Example 1 in full — subsonic, by formula and by table|W01 §7]]
- [ ] Show that the normal-shock $M_2(M_1)$ relation is symmetric in $M_1$ and $M_2$. → [[#Step 2: free-stream Mach number (normal-shock relation, inverted)]]
- [ ] Derive the compact mass-flow form $\dot m=pMA\sqrt{\gamma/RT}$. → [[#Q4. Mass flow rate through a duct]]
