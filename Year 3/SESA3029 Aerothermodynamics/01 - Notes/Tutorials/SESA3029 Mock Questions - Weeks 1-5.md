---
title: "SESA3029 Mock Questions - Weeks 1-5"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Blocks 1–3: normal and oblique shocks, expansions, nozzles, method of characteristics"
tags: [sesa3029, tutorial-solutions, mock-exam, exam-prep, normal-shock, pitot, oblique-shock, shock-reflection, shock-expansion, nozzle, method-of-characteristics]
sheet: "Self-written mock questions (not lecturer-set)"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]"]
status: complete
date: 2026-10-24
sources: ["01 - Notes/Topics", "01 - Notes/SESA3029 Formula Sheet.md", "02 - Sources/Lectures/IFT.pdf", "02 - Sources/Lectures/NST.pdf", "02 - Sources/Lectures/OSC.pdf"]
---

# SESA3029 Mock Questions - Weeks 1-5

> [!warning] Self-written mock questions, not lecturer-set
> Self-written mock questions, not lecturer-set; written from lectured content up to Lecture 3.4 (23 Oct 2026). Nothing here comes from a past paper. The questions were written to practise the calculation types in the topic notes and the [[SESA3029 Aerothermodynamics Hub#Week 1 exam skills|hub's exam-skill lists]], with new numbers, so they do not repeat [[SESA3029 Example Sheet 1 - Solutions|Example Sheet 1]], [[SESA3029 Example Sheet 2 - Solutions|Example Sheet 2]], [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing|Tutorial Lecture 1]] or Tests [[SESA3029 Test 1 - Solutions|1]] and [[SESA3029 Test 2 - Solutions|2]].

> [!abstract] How to use this set
> - **Eight questions, 127 marks.** Each shows its marks per part and a target time.
> - **Timing assumption: 1.8 min per mark.** That is a typical rate for a written engineering paper (for example, 100 marks in 3 hours). The set as a whole is about two papers' worth, so pick three or four questions for a timed sitting.
> - **Gas and data.** Air, $\gamma=1.4$, $R=287$ J/kg K. The exam provides the formula sheet, the IFT, the NST and the OSC ([[SESA3029 Formula Sheet#What the exam formula sheet gives you|what is and is not given]]). The lecturer says exam questions name the method: nearest table value, average, linear interpolation or exact equations (L2-2, ll. 74–80). Here the solutions use the **exact relations**, and quote the **table-interpolated** value next to them wherever a table look-up is the normal route.
> - **Verification.** Every number was computed in Python (SciPy root finders for θ–β–M, $\nu^{-1}$ and $A/A^*$ inversions). The key values are in each `[!check]` callout. The table-interpolated values were generated from the exact relations rounded to 4 d.p. at the tables' 0.02 spacing, which reproduces `IFT.pdf` and `NST.pdf`.

| Q | Topic | Marks | Time | Theory |
|---|---|---:|---:|---|
| 1 | normal shock and Pitot probe | 15 | 27 min | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes\|W01 §5, §7]] |
| 2 | oblique shock on an intake ramp | 15 | 27 min | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves\|W02 §4–6]] |
| 3 | regular shock reflection | 12 | 22 min | [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method\|W03 §1–2]] |
| 4 | diamond aerofoil, shock-expansion | 18 | 32 min | [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method\|W03 §5–6]] |
| 5 | Laval nozzle off design | 20 | 36 min | [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow\|W04 §2–5]] |
| 6 | MoC unit process and a wall point | 15 | 27 min | [[SESA3029 W05a - Method of Characteristics\|W05a §7, §10]] |
| 7 | minimum-length nozzle, three lines | 20 | 36 min | [[SESA3029 W05b - Minimum-Length Nozzle Design\|W05b §11–14]] |
| 8 | short conceptual questions | 12 | 22 min | W03 §4, W04 §5 and §7, W05b §15 |

---

## Q1. Normal shock and Pitot probe on a supersonic aircraft

**[15 marks; target 27 min]**

An aircraft cruises at $M_1=2.3$ at 11 km, where $p_1=22.70$ kPa and $T_1=216.65$ K. A Pitot probe on its nose faces the oncoming flow. A detached bow shock stands just ahead of the probe; treat the part of it in front of the probe mouth as a **normal shock**.

- **(a)** Find the flight speed. **[2]**
- **(b)** Find $M_2$, $p_2$, $T_2$ and $\rho_2/\rho_1$ just behind the normal part of the bow shock. **[5]**
- **(c)** Find the pressure the Pitot probe reads. Do it via $p_{02}/p_2$, and check it with the Rayleigh Pitot formula (or the NST's $p_{02}/p_1$ column). **[3]**
- **(d)** A faulty air-data computer applies the **subsonic** isentropic Pitot formula to the measured $p_{02}/p_1$. What Mach number does it display? What test should it have made first? **[3]**
- **(e)** Find the fraction of stagnation pressure lost across the shock and the entropy rise. Explain why $T_0$ is unchanged. **[2]**

### Q1 solution

**(a) Flight speed.** Speed of sound first:

$$
a_1=\sqrt{\gamma RT_1}=\sqrt{1.4\times287\times216.65}=295.04\ \text{m/s}.
$$

$$
U_1=M_1a_1=2.3\times295.04=\boxed{678.6\ \text{m/s}}
$$

**(b) Normal-shock jumps** ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#5. Normal shock from conservation laws|W01 §5]]). With $M_1^2=5.29$:

$$
\frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_1^2-1\right)=1+\frac{2.8}{2.4}\times4.29=6.0050.
$$

$$
\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2}=\frac{2.4\times5.29}{2+0.4\times5.29}=\frac{12.696}{4.116}=\boxed{3.0845}
$$

$$
\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1}=\frac{6.0050}{3.0845}=1.9468.
$$

$$
M_2^2=\frac{2+(\gamma-1)M_1^2}{2\gamma M_1^2-(\gamma-1)}=\frac{4.116}{14.412}=0.28560
\quad\Rightarrow\quad
\boxed{M_2=0.5344}
$$

Multiply by the upstream values:

$$
p_2=6.0050\times22.70=\boxed{136.3\ \text{kPa}},
\qquad
T_2=1.9468\times216.65=\boxed{421.8\ \text{K}}.
$$

The NST row $M_1=2.30$ gives the same four ratios directly (6.0050, 3.0845, 1.9468, 0.5344).

**(c) What the probe reads.** Behind the shock the flow is subsonic, so it decelerates **isentropically** into the probe mouth ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Case 3: compressible supersonic|W01 §7, Case 3]]):

$$
\frac{p_{02}}{p_2}=\left(1+\frac{\gamma-1}{2}M_2^2\right)^{\gamma/(\gamma-1)}=\left(1+0.2\times0.28560\right)^{3.5}=1.05712^{3.5}=1.2146.
$$

$$
p_{02}=1.2146\times136.31=\boxed{165.6\ \text{kPa}}
$$

**Check with the [[Rayleigh Pitot Formula]]**:

$$
\frac{p_{02}}{p_1}=\left[\frac{(\gamma+1)M_1^2}{2}\right]^{\gamma/(\gamma-1)}\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}.
$$

$$
=\left[\frac{2.4\times5.29}{2}\right]^{3.5}\left[\frac{2.4}{14.412}\right]^{2.5}=644.51\times0.011317=7.2937.
$$

$$
p_{02}=7.2937\times22.70=165.6\ \text{kPa}\ ✓
$$

This is the NST's last column at $M_1=2.30$.

**(d) The wrong formula.** The subsonic relation inverted for $M$ ([[SESA3029 Formula Sheet#Pitot relations|formula sheet]]) is

$$
M^2=\frac{2}{\gamma-1}\left[\left(\frac{p_0}{p}\right)^{(\gamma-1)/\gamma}-1\right].
$$

Put in $p_0/p=7.2937$:

$$
M^2=5\left[7.2937^{1/3.5}-1\right]=5\left[1.76424-1\right]=3.8212.
$$

$$
M_{\text{displayed}}=\boxed{1.955}\quad(\text{true value }2.30)
$$

The display reads 15 % low, because the formula ignores the bow shock's stagnation-pressure loss. **The test to make first:** subsonic flow can never give $p_0/p$ above its sonic value,

$$
\left.\frac{p_0}{p}\right|_{M=1}=1.2^{3.5}=1.8929.
$$

The measured ratio $7.29>1.893$, so the flow is supersonic and the Rayleigh formula must be used.

**(e) Loss and entropy.** The free-stream stagnation pressure is

$$
p_{01}=p_1\left(1+0.2M_1^2\right)^{3.5}=22.70\times2.058^{3.5}=22.70\times12.5043=283.85\ \text{kPa}.
$$

$$
\frac{p_{02}}{p_{01}}=\frac{165.57}{283.85}=0.5833
\quad\Rightarrow\quad
\text{loss}=\boxed{41.7\ \%}
$$

$T_{01}=T_{02}$, so the entropy rise comes from the pressure term alone ([[Entropy Change Across a Shock]]):

$$
\Delta s=-R\ln\frac{p_{02}}{p_{01}}=-287\ln0.5833=287\times0.53905=\boxed{154.7\ \text{J/(kg K)}}
$$

$T_0$ is unchanged because the shock is **adiabatic**: the energy equation $h_1+U_1^2/2=h_2+U_2^2/2$ says $h_0$, and so $T_0=h_0/c_p$, is the same on both sides. $p_0$ falls because the process is not isentropic. Here $T_{01}=T_{02}=216.65\times2.058=445.9$ K.

> [!check] Python
> $a_1=295.042$ m/s, $U_1=678.60$ m/s. $p_2/p_1=6.0050$, $\rho_2/\rho_1=3.0845$, $T_2/T_1=1.9468$, $M_2=0.53442$; $p_2=136.313$ kPa, $T_2=421.77$ K. $p_{02}/p_2=1.21460$, $p_{02}=165.567$ kPa; Rayleigh $p_{02}/p_1=7.29368$ (same $p_{02}$). Wrong subsonic $M=1.95478$. $p_{01}=283.847$ kPa, $p_{02}/p_{01}=0.58329$, $\Delta s=154.71$ J/(kg K). Every ratio matches the NST row at 2.30 to 4 d.p.

> [!tip] Why the probe can still be used
> The probe does not measure $p_{01}$ in supersonic flight. It measures $p_{02}$, which is a known function of $M_1$ and $p_1$. That is why the Rayleigh formula exists: it turns the "wrong" reading into the right Mach number.

---

## Q2. Oblique shock on a supersonic intake ramp

**[15 marks; target 27 min]**

A two-dimensional intake ramp deflects a stream at $M_1=2.5$, $p_1=30$ kPa, $T_1=250$ K through $\theta=12^\circ$. An attached weak oblique shock forms at the ramp leading edge.

- **(a)** Find the shock angle $\beta$. Use two guesses of $\beta$ in the θ–β–M relation and interpolate, then state the exact value. **[4]**
- **(b)** Find $p_2$, $T_2$ and $M_2$. **[5]**
- **(c)** Find $p_{02}/p_{01}$. Compare it with a normal shock at $M_1=2.5$, and with the ramp shock followed by a normal shock. Comment on intake design. **[3]**
- **(d)** What is the largest ramp angle for which the shock stays attached at $M_1=2.5$? Describe the flow if the ramp is set at $32^\circ$. **[3]**

### Q2 solution

**(a) Shock angle** ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#5. The θ–β–M relation, step by step|W02 §5]]). The relation gives $\theta$ explicitly for a given $\beta$:

$$
\tan\theta=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}.
$$

The weak root lies between the Mach angle $\mu_1=\sin^{-1}(1/2.5)=23.58^\circ$ and $\beta_{max}=64.78^\circ$. Guess twice:

| $\beta$ | $\theta$ from the relation |
|---:|---:|
| $33^\circ$ | $11.192^\circ$ |
| $34^\circ$ | $12.197^\circ$ |

Interpolate to $\theta=12^\circ$:

$$
\beta=33^\circ+1^\circ\times\frac{12-11.192}{12.197-11.192}=33^\circ+0.804^\circ=33.80^\circ.
$$

The exact root is $\beta=\boxed{33.80^\circ}$ (33.8016°). On the OSC, the $M_1=2.5$ curve at $\theta=12^\circ$ reads about $34^\circ$. The strong root, $\beta=84.61^\circ$, is not what a sharp ramp in open flow produces ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#Weak and strong solutions|W02 §6]]).

**(b) Downstream state.** The shock is a normal shock in the normal component ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#4. It is a normal shock in the normal component|W02 §4]]):

$$
M_{n1}=M_1\sin\beta=2.5\sin33.80^\circ=2.5\times0.55632=1.3908.
$$

$$
M_{n1}^2=1.9343.
$$

$$
\frac{p_2}{p_1}=1+\frac{2.8}{2.4}\left(1.9343-1\right)=2.0900
\quad\Rightarrow\quad
p_2=2.0900\times30=\boxed{62.70\ \text{kPa}}
$$

$$
\frac{\rho_2}{\rho_1}=\frac{2.4\times1.9343}{2+0.4\times1.9343}=1.6737,
\qquad
\frac{T_2}{T_1}=\frac{2.0900}{1.6737}=1.2488
\quad\Rightarrow\quad
T_2=\boxed{312.2\ \text{K}}
$$

$$
M_{n2}^2=\frac{2+0.4\times1.9343}{2.8\times1.9343-0.4}=0.55297
\quad\Rightarrow\quad
M_{n2}=0.74362.
$$

Turn the normal component back into the full Mach number:

$$
M_2=\frac{M_{n2}}{\sin(\beta-\theta)}=\frac{0.74362}{\sin21.80^\circ}=\frac{0.74362}{0.37139}=\boxed{2.002}
$$

**(c) Stagnation-pressure recovery.** The NST $p_{02}/p_{01}$ at $M_{n1}=1.3908$ (rows 1.38: 0.9630, 1.40: 0.9582) is

$$
\left.\frac{p_{02}}{p_{01}}\right|_{\text{ramp}}=0.9605.
$$

| Intake shock system | $p_0$ recovered |
|---|---:|
| one normal shock at $M=2.5$ (NST) | 0.4990 |
| $12^\circ$ ramp shock, then a normal shock at $M_2=2.002$ | $0.9605\times0.7199=0.6914$ |
| ramp shock alone | 0.9605 |

A pitot intake (one normal shock) loses half the stagnation pressure. Turning the flow first with a weak oblique shock lowers the Mach number before the terminal normal shock, and the recovery rises from 50 % to 69 %. The loss depends on $M_{n1}$, not $M_1$ ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#Why p₀₂/p₀₁ depends only on Mₙ₁ (derivation)|W02 §4]]), so several weak shocks beat one strong one. This is the W02 intake example ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#10.2 Example 2: a supersonic intake at M₁ = 3|§10.2]]) at a different Mach number.

**(d) Detachment.** Maximise $\theta(\beta)$ at $M_1=2.5$: $\theta_{max}=\boxed{29.80^\circ}$, at $\beta=64.78^\circ$. The OSC envelope gives about $29.8^\circ$ ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves#Maximum deflection and detachment|W02 §6]]).

At $32^\circ>\theta_{max}$ no attached solution exists. The shock **detaches** and stands ahead of the ramp as a curved bow shock. It is normal where it crosses the stagnation streamline, so the flow there is subsonic ($M=0.513$) and loses half its stagnation pressure ($p_{02}/p_{01}=0.499$). Further out the bow shock weakens through every strong and weak oblique solution towards a Mach wave.

> [!check] Python
> Exact weak root $\beta=33.80158^\circ$ (two-guess interpolation 33.8038°, which returns $\theta=12.002^\circ$). $M_{n1}=1.39080$, $p_2/p_1=2.09003$, $T_2/T_1=1.24876$, $M_{n2}=0.74362$, $M_2=2.00224$, $p_2=62.701$ kPa, $T_2=312.19$ K. $p_{02}/p_{01}=0.96046$ (NST interpolation 0.96041). Normal shock at 2.5: 0.49901; ramp then normal: 0.69142. $\theta_{max}=29.7974^\circ$ at $\beta=64.782^\circ$. Strong root $84.612^\circ$.

---

## Q3. Regular reflection of a ramp shock from a wall

**[12 marks; target 22 min]**

In a two-dimensional channel a stream at $M_1=2.8$, $p_1=20$ kPa meets a $14^\circ$ compression ramp on the lower wall. The ramp shock crosses the channel and strikes the flat upper wall, which is parallel to the oncoming stream.

- **(a)** Find the incident shock angle, $p_2$ and $M_2$. **[4]**
- **(b)** Show that a regular reflection is possible. **[2]**
- **(c)** Find the reflected shock's angle $\phi$ to the upper wall, $p_3$ and $M_3$. **[4]**
- **(d)** Find $p_{03}/p_{01}$. Explain why $\phi$ is not equal to the incident shock angle, so the reflection is not "mirror-like". **[2]**

### Q3 solution

The method is two oblique-shock "unit calculations" in a row ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#1. Regular shock reflection from a wall|W03 §1]]).

**(a) Incident shock.** $M_1=2.8$, $\theta=14^\circ$. The weak root of θ–β–M is

$$
\beta_1=32.82^\circ.
$$

$$
M_{n1}=2.8\sin32.82^\circ=1.5177,
\qquad
M_{n1}^2=2.3034.
$$

$$
\frac{p_2}{p_1}=1+\frac{2.8}{2.4}\left(2.3034-1\right)=2.5206
\quad\Rightarrow\quad
p_2=\boxed{50.41\ \text{kPa}}
$$

$$
M_{n2}=\sqrt{\frac{2+0.4\times2.3034}{2.8\times2.3034-0.4}}=0.69492,
\qquad
M_2=\frac{0.69492}{\sin(32.82^\circ-14^\circ)}=\frac{0.69492}{\sin18.82^\circ}=\boxed{2.154}
$$

The flow in region 2 is inclined at $14^\circ$ **towards** the upper wall.

**(b) Is regular reflection possible?** The wall forces the flow back parallel to itself, so the reflected shock must turn the region-2 flow by $14^\circ$ again, now from $M_2=2.154$. That needs

$$
\theta=14^\circ\le\theta_{max}(M_2)=\theta_{max}(2.154)=25.4^\circ.
$$

It holds, so an attached reflected shock exists and the reflection is **regular**. Had $14^\circ$ exceeded $\theta_{max}(M_2)$, a [[Mach Reflection]] with a near-normal Mach stem would form ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#2. Mach reflection|W03 §2]]). For this $M_1$ the switch happens at a ramp angle of $20.2^\circ$ (computed by the [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#The regular-reflection limit, derived|regular-reflection-limit]] search).

**(c) Reflected shock.** Same turn, $\theta=14^\circ$, from $M_2=2.154$. The weak root is $\beta_2=40.90^\circ$, measured from the region-2 flow direction.

$$
M_{n2}'=2.1539\sin40.90^\circ=1.4103,
\qquad
\left(M_{n2}'\right)^2=1.9888.
$$

$$
\frac{p_3}{p_2}=1+\frac{2.8}{2.4}\left(1.9888-1\right)=2.1536
\quad\Rightarrow\quad
p_3=2.1536\times50.41=\boxed{108.6\ \text{kPa}}
$$

$$
M_{n3}=0.73543,
\qquad
M_3=\frac{0.73543}{\sin(40.90^\circ-14^\circ)}=\frac{0.73543}{\sin26.90^\circ}=\boxed{1.626}
$$

The region-2 flow points $14^\circ$ into the wall, so the reflected shock's angle **to the wall** is

$$
\phi=\beta_2-\theta=40.90^\circ-14^\circ=\boxed{26.90^\circ}
$$

**(d) Losses and the angle.** Stagnation-pressure ratios multiply across a shock chain:

$$
\frac{p_{03}}{p_{01}}=\frac{p_{02}}{p_{01}}\cdot\frac{p_{03}}{p_{02}}=0.92409\times0.95560=\boxed{0.8831}
$$

$\phi=26.9^\circ$ is less than the incident $32.8^\circ$ for two reasons. The reflected shock meets a **slower** stream ($M_2=2.154<2.8$), and it sits in a flow already inclined towards the wall, so its angle to the wall is $\beta_2-\theta$, not $\beta_2$. A shock reflection is a new oblique shock fixed by the wall boundary condition, not an optical mirror ([[Regular Shock Reflection]]).

> [!check] Python
> Incident: $\beta_1=32.8218^\circ$, $M_{n1}=1.51768$, $p_2/p_1=2.52058$, $M_2=2.15395$, $p_2=50.412$ kPa. $\theta_{max}(2.154)=25.435^\circ$. Reflected: $\beta_2=40.8993^\circ$, $M_{n}=1.41026$, $p_3/p_2=2.15364$, $p_3=108.568$ kPa, $M_3=1.62553$, $\phi=26.8993^\circ$. $p_{03}/p_{01}=0.88306$. Regular-reflection limit at $M_1=2.8$: ramp angle $20.207^\circ$, where $M_2=1.850$.

---

## Q4. Diamond aerofoil by shock-expansion theory

**[18 marks; target 32 min]**

A symmetric diamond aerofoil has chord $c=1$ m and thickness ratio $t/c=0.10$, with its maximum thickness at mid-chord. It flies at $\alpha=3^\circ$ in a stream at $M_\infty=2.0$, $p_\infty=25$ kPa.

- **(a)** Find the half-angle $\varepsilon$. Sketch the wave pattern on the four faces, and give the turning angle and wave type at each face. **[3]**
- **(b)** Find the pressure on each face. **[8]**
- **(c)** Find the lift and drag per unit span, $C_l$ and $C_d$. **[5]**
- **(d)** Compare with a flat plate at the same $\alpha$, and comment on where the extra drag comes from. **[2]**

### Q4 solution

![[at_mock_diamond.png|900]]

**(a) Geometry and waves** ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#Diamond aerofoil|W03 §6, diamond]]).

$$
\varepsilon=\tan^{-1}\frac{t/2}{c/2}=\tan^{-1}0.10=5.711^\circ.
$$

Since $\alpha<\varepsilon$, both front faces turn the flow **into** itself, so both leading edges carry shocks:

| Face | Turn at its leading corner | Wave |
|---|---|---|
| 1u (upper front) | $\varepsilon-\alpha=2.711^\circ$ into the flow | weak oblique shock |
| 2u (upper rear) | $2\varepsilon=11.421^\circ$ away | Prandtl–Meyer fan |
| 1l (lower front) | $\varepsilon+\alpha=8.711^\circ$ into the flow | oblique shock |
| 2l (lower rear) | $2\varepsilon=11.421^\circ$ away | Prandtl–Meyer fan |

The trailing-edge waves (a shock on one side, a fan on the other, and a slip line) cannot reach the surface in supersonic flow, so they are not needed for the forces.

**(b) Face pressures** ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]]).

*Face 1u.* Shock with $\theta=2.711^\circ$ at $M=2$; the weak root is $\beta=32.25^\circ$. (A turn this small cannot be read accurately off the OSC; iterate θ–β–M.)

$$
M_{n1}=2\sin32.25^\circ=1.06736,
\qquad
\frac{p}{p_\infty}=1+\frac{2.8}{2.4}\left(1.13925-1\right)=1.16246.
$$

$$
p_{1u}=1.16246\times25=\boxed{29.06\ \text{kPa}}
$$

$$
M_{n2}=0.93820,
\qquad
M_{1u}=\frac{0.93820}{\sin(32.25^\circ-2.71^\circ)}=\frac{0.93820}{\sin29.54^\circ}=1.9027.
$$

*Face 2u.* Expand by $11.421^\circ$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]):

$$
\nu(M_{2u})=\nu(1.9027)+11.421^\circ=23.662^\circ+11.421^\circ=35.084^\circ.
$$

IFT rows 2.32 ($34.7825^\circ$) and 2.34 ($35.2787^\circ$):

$$
M_{2u}=2.32+0.02\times\frac{35.084-34.7825}{35.2787-34.7825}=2.3321.
$$

$p_0$ is constant through the fan, so

$$
p_{2u}=p_{1u}\,\frac{(p_0/p)_{1.9027}}{(p_0/p)_{2.3321}}=29.061\times\frac{6.7286}{13.1486}=29.061\times0.51174=\boxed{14.87\ \text{kPa}}
$$

*Face 1l.* Shock with $\theta=8.711^\circ$ at $M=2$; $\beta=37.94^\circ$.

$$
M_{n1}=2\sin37.94^\circ=1.22970,
\qquad
\frac{p}{p_\infty}=1+\frac{2.8}{2.4}\left(1.51217-1\right)=1.59754.
$$

$$
p_{1l}=1.59754\times25=\boxed{39.94\ \text{kPa}}
$$

$$
M_{n2}=0.82426,
\qquad
M_{1l}=\frac{0.82426}{\sin(37.94^\circ-8.71^\circ)}=\frac{0.82426}{\sin29.23^\circ}=1.6879.
$$

*Face 2l.*

$$
\nu(M_{2l})=\nu(1.6879)+11.421^\circ=17.455^\circ+11.421^\circ=28.876^\circ
\quad\Rightarrow\quad
M_{2l}=2.0918
$$

(IFT rows 2.08, $28.56^\circ$, and 2.10, $29.0971^\circ$, interpolate to the same 2.0918.)

$$
p_{2l}=39.938\times\frac{4.8470}{9.0277}=39.938\times0.53690=\boxed{21.44\ \text{kPa}}
$$

**(c) Forces.** Each face has length $s=(c/2)/\cos\varepsilon$. Its pressure force $ps$ acts along the face normal, which is tilted by $\varepsilon$ from the chord normal. So each face contributes

$$
ps\cos\varepsilon=p\,\frac c2\ \ (\text{normal to the chord}),
\qquad
ps\sin\varepsilon=p\,\frac t2\ \ (\text{along the chord}).
$$

Normal force (upwards positive), summing lower minus upper:

$$
N'=\frac c2\Big[(p_{1l}+p_{2l})-(p_{1u}+p_{2u})\Big]=\frac12\big[61.381-43.933\big]=8.724\ \text{kN/m}.
$$

Chordwise force (towards the trailing edge positive): front faces push back, rear faces pull forward:

$$
A'=\frac t2\Big[(p_{1u}+p_{1l})-(p_{2u}+p_{2l})\Big]=0.05\big[69.000-36.315\big]=1.634\ \text{kN/m}.
$$

Rotate into wind axes ([[SESA3029 Formula Sheet#Shock-expansion method (Lecture 2.5)|formula sheet]]), with $\cos3^\circ=0.99863$ and $\sin3^\circ=0.05234$:

$$
L'=N'\cos\alpha-A'\sin\alpha=8.712-0.086=\boxed{8.63\ \text{kN/m}}
$$

$$
D'=N'\sin\alpha+A'\cos\alpha=0.457+1.632=\boxed{2.09\ \text{kN/m}}
$$

Dynamic pressure, from $q_\infty=\tfrac12\gamma p_\infty M_\infty^2$:

$$
q_\infty=0.7\times25\times4=70\ \text{kPa}.
$$

$$
C_l=\frac{L'}{q_\infty c}=\frac{8.627}{70}=\boxed{0.1232},
\qquad
C_d=\frac{D'}{q_\infty c}=\frac{2.089}{70}=\boxed{0.0298}.
$$

So $L/D=4.13$.

**(d) Against a flat plate.** At $\alpha=3^\circ$ a flat plate has a $3^\circ$ shock below ($p_L=29.52$ kPa) and a $3^\circ$ fan above ($p_U=21.04$ kPa), giving

$$
C_l=\frac{(p_L-p_U)\cos\alpha}{q_\infty}=0.1210,
\qquad
C_d=\frac{(p_L-p_U)\sin\alpha}{q_\infty}=0.0063.
$$

The lift is almost the same (0.121 against 0.123). The drag is **4.7 times** larger. The extra is **thickness wave drag**: the front faces carry high pressure and the rear faces low pressure, and both resolve backwards along the chord ($A'$ above). The diamond at $\alpha=0$ alone has $C_d=0.0232$, and $0.0063+0.0232=0.0295$, close to the 0.0298 found. Drag from lift and drag from thickness nearly add; linear theory (Weeks 7–8) makes that additivity exact.

> [!check] Python
> $\varepsilon=5.7106^\circ$. 1u: $\beta=32.2543^\circ$, $p=29.0614$ kPa, $M=1.90270$. 2u: $\nu=35.0836^\circ$, $M=2.33214$, $p=14.8718$ kPa. 1l: $\beta=37.9412^\circ$, $p=39.9384$ kPa, $M=1.68792$. 2l: $\nu=28.8762^\circ$, $M=2.09177$, $p=21.4429$ kPa. $N'=8.7240$, $A'=1.6343$, $L'=8.6265$, $D'=2.0886$ kN/m; $C_l=0.12324$, $C_d=0.02984$, $L/D=4.130$. Flat plate: $C_l=0.12103$, $C_d=0.00634$. Diamond at $\alpha=0$: $C_d=0.02320$. (Moment, not asked: $M'_{LE}=-3.83$ kN, $x_{cp}=0.444c$.)

---

## Q5. Laval nozzle at design and off-design back pressures

**[20 marks; target 36 min]**

A converging–diverging nozzle has throat area $A_t=100$ cm² and exit area $A_e=300$ cm². It is fed from a reservoir at $p_0=1.0$ MPa, $T_0=600$ K.

- **(a)** Find the design exit Mach number, exit pressure, exit temperature and exit velocity. **[4]**
- **(b)** Find the choked mass flow. **[2]**
- **(c)** Find the back pressure $p_{b3}$ at which the nozzle just chokes with subsonic flow throughout, and the back pressure $p_{b5}$ at which a normal shock sits at the exit plane. **[4]**
- **(d)** The back pressure is 500 kPa. Identify the regime and locate the shock: give its Mach number and the area where it stands. **[6]**
- **(e)** The nozzle exhausts to sea level, $p_a=101.3$ kPa. Identify the regime, find the angle and turning of the lip shocks, and say whether they cross regularly. Find the thrust and compare it with the thrust at the design condition. **[4]**

### Q5 solution

**(a) Design point** ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#2. The area–Mach relation (homework, slide 5; Anderson §10.3)|W04 §2]]). The throat is sonic, so $A_e/A^*=A_e/A_t=3.0$. The supersonic root of the area–Mach relation is

$$
\frac{A}{A^*}=\frac1M\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{3}=3.0
\quad\Rightarrow\quad
M_e=\boxed{2.637}
$$

(IFT rows 2.62, 2.9511, and 2.64, 3.0073, interpolate to 2.6374.) Then

$$
\frac{p_e}{p_0}=\left(1+0.2M_e^2\right)^{-3.5}=2.3912^{-3.5}=0.04730
\quad\Rightarrow\quad
p_e=\boxed{47.30\ \text{kPa}}
$$

$$
T_e=\frac{T_0}{1+0.2M_e^2}=\frac{600}{2.3912}=\boxed{250.9\ \text{K}}
$$

$$
u_e=M_e\sqrt{\gamma RT_e}=2.6374\times317.52=\boxed{837.4\ \text{m/s}}
$$

**(b) Mass flow** ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#3. Mass flow and choking|W04 §3]]):

$$
\dot m=\frac{p_0A^*}{\sqrt{T_0}}\sqrt{\frac{\gamma}{R}}\left(\frac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}.
$$

The constant is $\sqrt{1.4/287}\times(2/2.4)^3=0.069843\times0.57870=0.040418$:

$$
\dot m=0.040418\times\frac{10^6\times0.01}{\sqrt{600}}=0.040418\times\frac{10^4}{24.495}=\boxed{16.50\ \text{kg/s}}
$$

**(c) Critical back pressures** ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#Computing the three critical back pressures|W04 §4]]).

*$p_{b3}$*: the **subsonic** root of $A/A^*=3.0$ is $M=0.1974$ (IFT rows 0.18, 3.2779, and 0.20, 2.9635, give 0.1977). Then

$$
\frac{p_{b3}}{p_0}=\left(1+0.2\times0.1974^2\right)^{-3.5}=0.9732
\quad\Rightarrow\quad
p_{b3}=\boxed{973.2\ \text{kPa}}
$$

*$p_{b5}$*: a normal shock at $M_e=2.6374$ ($M_e^2=6.9559$):

$$
\frac{p_2}{p_1}=1+\frac{2.8}{2.4}\left(6.9559-1\right)=7.9485.
$$

$$
p_{b5}=7.9485\times47.30=\boxed{376.0\ \text{kPa}}
$$

So the map is: $p_{b3}=973$ kPa, $p_{b5}=376$ kPa, $p_{b6}=p_e=47.3$ kPa.

**(d) $p_b=500$ kPa.** It lies between $p_{b5}=376$ and $p_{b3}=973$ kPa, so a **normal shock stands inside the diverging section** ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#Where is the shock for a given back pressure?|W04 §4]]).

*Step 1.* Mass flow and $T_0$ are the same at the throat and the exit, so $p_{01}A_t=p_{0e}A_e^*$. Hence

$$
\frac{p_e}{p_{0e}}\cdot\frac{A_e}{A_e^*}=\frac{p_bA_e}{p_{01}A_t}=\frac{500\times3}{1000}=1.500.
$$

*Step 2.* The left side depends only on $M_e$ (subsonic). The IFT product $(p/p_0)(A/A^*)$ is 1.5014 at $M=0.38$ and 1.4242 at $M=0.40$:

$$
M_e=0.38+0.02\times\frac{1.5014-1.500}{1.5014-1.4242}=0.3804.
$$

*Step 3.* Stagnation pressure at the exit:

$$
p_{0e}=p_b\left(1+0.2M_e^2\right)^{3.5}=500\times1.10495=552.5\ \text{kPa}.
$$

$$
\frac{p_{02}}{p_{01}}=\frac{552.5}{1000}=0.5525.
$$

*Step 4.* NST $p_{02}/p_{01}$ rows 2.36 (0.5572) and 2.38 (0.5486):

$$
M_s=2.36+0.02\times\frac{0.5572-0.5525}{0.5572-0.5486}=2.3709\approx\boxed{2.37}
$$

*Step 5.* The shock stands where the supersonic flow reaches $M_s$:

$$
\frac{A_s}{A_t}=\frac{A}{A^*}(2.3709)=2.340
\quad\Rightarrow\quad
A_s=\boxed{234\ \text{cm}^2}
$$

That is inside the nozzle ($100<234<300$ cm²) ✓. Behind it $M=0.526$, and the subsonic flow diffuses to $M_e=0.380$ at the exit.

**(e) Sea level.** $p_{b6}=47.3<101.3<p_{b5}=376$ kPa, so the nozzle is **over-expanded**: the exit flow is supersonic and shock-free, but $p_e<p_a$. Oblique **lip shocks** raise the jet pressure to ambient ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)|W04 §5]]):

$$
\frac{p_a}{p_e}=\frac{101.3}{47.30}=2.1417.
$$

$$
M_{n1}=\sqrt{1+\frac{\gamma+1}{2\gamma}\left(\frac{p_a}{p_e}-1\right)}=\sqrt{1+\frac{2.4}{2.8}\times1.1417}=\sqrt{1.9786}=1.4066.
$$

$$
\beta=\sin^{-1}\frac{M_{n1}}{M_e}=\sin^{-1}\frac{1.4066}{2.6374}=\boxed{32.23^\circ}
$$

This is the "easy direction" of θ–β–M (β known), so $\theta$ follows directly: $\theta=\boxed{11.90^\circ}$, with $M_2=2.12$ behind the lip shock. The jet boundary turns **inwards** by $11.9^\circ$. At the axis each stream must be turned back by $11.9^\circ<\theta_{max}(2.12)=24.9^\circ$, so the lip shocks **cross regularly**, with no Mach disc. The shock-diamond pattern follows.

**Thrust** ($T=\dot m u_e+(p_e-p_a)A_e$):

$$
T_{\text{sea level}}=16.50\times837.4+(47.30-101.3)\times10^3\times0.03=13\,818-1\,620=\boxed{12.20\ \text{kN}}
$$

At the design condition ($p_a=p_e$) the pressure term vanishes and $T=\dot mu_e=13.82$ kN. Over-expansion costs 12 % of the thrust here.

> [!check] Python
> $M_e=2.63740$ (subsonic root 0.19738), $p_e/p_0=0.047299$, $T_e=250.92$ K, $u_e=837.44$ m/s, $\dot m=16.5008$ kg/s. $p_{b3}=973.18$ kPa, $p_{b5}=375.96$ kPa. At $p_b=500$ kPa: $M_e=0.38030$, $p_{0e}=552.49$ kPa, $M_s=2.37093$ (NST interpolation 2.37096), $A_s/A_t=2.33970$, $M$ behind the shock 0.52626. Sea level: $M_{n1}=1.40662$, $\beta=32.2312^\circ$, $\theta=11.8950^\circ$, $M_2=2.12048$, $\theta_{max}(M_2)=24.931^\circ$; thrust 12.198 kN against 13.818 kN.

---

## Q6. Method of characteristics unit process and a reflecting wall

**[15 marks; target 27 min]**

In a steady, planar, homentropic supersonic flow, two points are known (lengths in metres, angles from the $x$-axis):

| Point | $x$ | $y$ | $M$ | $\theta$ |
|---|---:|---:|---:|---:|
| A (below) | 1.20 | 0.30 | 2.00 | $3.0^\circ$ |
| B (above) | 1.00 | 0.80 | 2.20 | $9.0^\circ$ |

The $C^+$ characteristic through A and the $C^-$ characteristic through B meet at P.

- **(a)** State the compatibility conditions and derive expressions for $\nu_P$ and $\theta_P$. **[3]**
- **(b)** Find $\nu_P$, $\theta_P$, $M_P$ and $\mu_P$. **[4]**
- **(c)** Locate P using the averaged characteristic slopes. **[5]**
- **(d)** The $C^+$ through P next meets the upper wall, which is straight and inclined at $\theta_W=12^\circ$. Find the wall Mach number and the Riemann invariant carried by the reflected characteristic. **[3]**

### Q6 solution

**(a) Compatibility conditions** ([[SESA3029 W05a - Method of Characteristics#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|W05a §7]]). In the lecture's notation:

$$
R^+=\nu-\theta\ \text{is constant along }C^+\ (\text{slope }\theta+\mu),
\qquad
R^-=\nu+\theta\ \text{is constant along }C^-\ (\text{slope }\theta-\mu).
$$

P lies on A's $C^+$ and on B's $C^-$, so

$$
\nu_P-\theta_P=R^+_A,
\qquad
\nu_P+\theta_P=R^-_B.
$$

Add the two:

$$
2\nu_P=R^+_A+R^-_B
\quad\Rightarrow\quad
\nu_P=\tfrac12\left(R^+_A+R^-_B\right).
$$

Subtract the first from the second:

$$
2\theta_P=R^-_B-R^+_A
\quad\Rightarrow\quad
\theta_P=\tfrac12\left(R^-_B-R^+_A\right).
$$

**(b) State at P** ([[SESA3029 W05a - Method of Characteristics#10. The unit process (3.2 slides 7–9)|W05a §10]]). From the IFT (exact to 4 d.p. at these rows):

$$
\nu_A=\nu(2.00)=26.3798^\circ,\quad\mu_A=30.0000^\circ;
\qquad
\nu_B=\nu(2.20)=31.7325^\circ,\quad\mu_B=27.0357^\circ.
$$

$$
R^+_A=\nu_A-\theta_A=26.3798-3=23.3798^\circ.
$$

$$
R^-_B=\nu_B+\theta_B=31.7325+9=40.7325^\circ.
$$

$$
\nu_P=\tfrac12(23.3798+40.7325)=\boxed{32.0561^\circ}
$$

$$
\theta_P=\tfrac12(40.7325-23.3798)=\boxed{8.6764^\circ}
$$

Invert $\nu$ with IFT rows 2.20 ($31.7325^\circ$) and 2.22 ($32.2494^\circ$):

$$
M_P=2.20+0.02\times\frac{32.0561-31.7325}{32.2494-31.7325}=2.20+0.02\times0.626=\boxed{2.2125}
$$

$$
\mu_P=\sin^{-1}\frac{1}{2.2125}=\boxed{26.8705^\circ}
$$

**(c) Location.** Average the slopes at the two ends of each segment:

$$
\alpha_{AP}=\tfrac12\left[(\theta+\mu)_A+(\theta+\mu)_P\right]=\tfrac12\left[33.0000+35.5469\right]=34.2735^\circ,
\qquad
\tan\alpha_{AP}=0.68148.
$$

$$
\alpha_{BP}=\tfrac12\left[(\theta-\mu)_B+(\theta-\mu)_P\right]=\tfrac12\left[-18.0357-18.1942\right]=-18.1149^\circ,
\qquad
\tan\alpha_{BP}=-0.32714.
$$

Intersect the two straight segments:

$$
x_P=\frac{x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}-(y_B-y_A)}{\tan\alpha_{BP}-\tan\alpha_{AP}}.
$$

$$
=\frac{1.00(-0.32714)-1.20(0.68148)-0.50}{-0.32714-0.68148}=\frac{-0.32714-0.81777-0.50}{-1.00862}=\frac{-1.64491}{-1.00862}.
$$

$$
x_P=\boxed{1.6309\ \text{m}}
$$

$$
y_P=y_A+(x_P-x_A)\tan\alpha_{AP}=0.30+0.4309\times0.68148=\boxed{0.5936\ \text{m}}
$$

**(d) Wall point** (prescribed wall, BC 1; [[SESA3029 W05b - Minimum-Length Nozzle Design#BC 1: a prescribed wall reflects (slide 5)|W05b §11]]). The $C^+$ from P carries $R^+_P=R^+_A=23.3798^\circ$ to the wall, and the wall fixes $\theta_W=12^\circ$:

$$
\nu_W=R^+_P+\theta_W=23.3798+12=35.3798^\circ.
$$

IFT rows 2.34 ($35.2787^\circ$) and 2.36 ($35.7715^\circ$):

$$
M_W=2.34+0.02\times\frac{35.3798-35.2787}{35.7715-35.2787}=\boxed{2.3441}
$$

The reflected $C^-$ carries *"R plus plus two times the wall angle"* (L3-3, ll. 62–63):

$$
R^-_W=R^+_P+2\theta_W=23.3798+24=\boxed{47.3798^\circ}
$$

A reflection exists because the arriving flow ($\theta_P=8.68^\circ$) is not parallel to the wall ($12^\circ$). The wall is inclined $3.32^\circ$ further away from the flow, so the flow must turn outwards to follow it and the reflected wave is an **expansion**: $M$ rises from 2.21 to 2.34.

> [!check] Python
> $\nu_A=26.37976^\circ$, $\nu_B=31.73250^\circ$, $\mu_B=27.03565^\circ$. $\nu_P=32.05613^\circ$, $\theta_P=8.67637^\circ$, $M_P=2.21252$, $\mu_P=26.87051^\circ$. $\alpha_{AP}=34.2735^\circ$, $\alpha_{BP}=-18.1149^\circ$, $P=(1.63089,\ 0.59365)$. Using unaveraged end slopes instead moves P to $(1.6460,\ 0.5896)$. Wall: $\nu_W=35.37976^\circ$, $M_W=2.34410$, $R^-_W=47.37976^\circ$.

> [!warning] Two classic slips
> - Degrees, not radians: $\sin^{-1}(1/2.2125)$ is $26.87^\circ$, not 0.469 (L3-2, ll. 411–421).
> - In the $x_P$ formula, A is the point whose $C^+$ reaches P (below) and B the one whose $C^-$ does (above). Swapping them swaps the slopes and gives nonsense.

---

## Q7. Minimum-length nozzle with three characteristics

**[20 marks; target 36 min]**

Design the upper half of a planar minimum-length nozzle for $M_e=2.6$, $\gamma=1.4$, by the method of characteristics. The sharp throat corner 0 is at $(0,\ 1)$, lengths are scaled by the throat half-height $r_a$, and the centreline is $y=0$. Represent the corner fan by **three** characteristics 0a, 0b and 0c, with $\theta_{0a}=\theta_{max}-20^\circ$, $\theta_{0b}=\theta_{max}-10^\circ$ and $\theta_{0c}=\theta_{max}$.

Number the points as in Lecture 3.3: 0a reaches the centreline at 1, then 2 and 3 are interior points on the $C^+$ from 1, and 4 is the wall point it reaches. Then 5 (centreline), 6 (interior) and 7 (wall); then 8 (centreline) and 9 (wall, the exit).

- **(a)** Show that $\theta_{max}=\nu(M_e)/2$ and evaluate it. **[3]**
- **(b)** Tabulate $\theta$, $\nu$, $R^-$, $M$ and $\mu$ on the three fan lines. **[3]**
- **(c)** Find $R^+$, $R^-$, $\theta$, $\nu$ and $M$ at points 1 to 9. **[6]**
- **(d)** Find the coordinates of points 1 and 2, and, given that point 3 is at $(0.9365,\ 0.7812)$, of wall point 4. **[5]**
- **(e)** The full net puts the exit, point 9, at $(10.473,\ 2.946)$. Check this against one-dimensional theory and comment. **[3]**

### Q7 solution

![[at_mock_mln_net.png|900]]

**(a) Corner angle** ([[SESA3029 W05b - Minimum-Length Nozzle Design#13. The minimum-length nozzle (3.3 slide 10)|W05b §13]]).

1. The throat is sonic: $\theta=0$ and $\nu(1)=0$, because $\nu(M)$ is an integral that starts at $M=1$.
2. The corner fan turns the wall flow through $\theta_{max}$. Every $C^+$ crossing the fan comes from the throat, where $R^+=0$, so $\nu=\theta$ in the fan. On the last fan line, $\nu_C=\theta_{max}$.
3. That line's invariant is $R^-_C=\nu_C+\theta_C=2\theta_{max}$.
4. It reaches the centreline at the first point of the uniform exit flow, where $\theta=0$ and $\nu=\nu(M_e)$, so $R^-=\nu(M_e)$ there.
5. Same $C^-$, same invariant:

$$
2\theta_{max}=\nu(M_e)
\quad\Rightarrow\quad
\theta_{max}=\frac{\nu(M_e)}{2}.
$$

From the IFT, $\nu(2.6)=41.4147^\circ$, so

$$
\theta_{max}=\boxed{20.707^\circ}
$$

The lines are therefore at $0.707^\circ$, $10.707^\circ$ and $20.707^\circ$: the "numerical convenience" choice of L3-3, ll. 240–243, with a small first angle that keeps line 0a off $M=1$.

**(b) Fan lines.** $\nu=\theta$ and $R^-=2\theta$:

| Line | $\theta=\nu$ | $R^-$ | $M$ | $\mu$ | $\theta-\mu$ |
|---|---:|---:|---:|---:|---:|
| 0a | 0.7074 | 1.4147 | 1.0645 | 69.955 | −69.248 |
| 0b | 10.7074 | 21.4147 | 1.4592 | 43.259 | −32.552 |
| 0c | 20.7074 | 41.4147 | 1.7994 | 33.762 | −13.055 |

All angles are in degrees.

**(c) The invariants, then the states** ([[SESA3029 W05b - Minimum-Length Nozzle Design#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|W05b §14]] procedure).

- **$R^-$ along each $C^-$:** 1 has 1.4147 (from 0a); 2 and 5 have 21.4147 (from 0b); 3, 6 and 8 have 41.4147 (from 0c).
- **Centreline points** (BC 3) turn $R^-$ into an equal $R^+$: $R^+=1.4147$ on 1–2–3–4, $21.4147$ on 5–6–7, $41.4147$ on 8–9.
- **Interior points:** $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$.
- **Wall points** (BC 2, cancelling) copy the state of the point below them; no $C^-$ leaves them.

| Pt | Type | $R^+$ | $R^-$ | $\theta$ | $\nu$ | $M$ |
|---|---|---:|---:|---:|---:|---:|
| 1 | centre | 1.4147 | 1.4147 | 0 | 1.4147 | 1.1041 |
| 2 | interior | 1.4147 | 21.4147 | 10.0000 | 11.4147 | 1.4833 |
| 3 | interior | 1.4147 | 41.4147 | 20.0000 | 21.4147 | 1.8239 |
| 4 | wall | 1.4147 | N/A | 20.0000 | 21.4147 | 1.8239 |
| 5 | centre | 21.4147 | 21.4147 | 0 | 21.4147 | 1.8239 |
| 6 | interior | 21.4147 | 41.4147 | 10.0000 | 31.4147 | 2.1878 |
| 7 | wall | 21.4147 | N/A | 10.0000 | 31.4147 | 2.1878 |
| 8 | centre | 41.4147 | 41.4147 | 0 | 41.4147 | 2.6000 |
| 9 | wall | 41.4147 | N/A | 0 | 41.4147 | 2.6000 |

Two worked lines. Point 2: $\theta_2=\tfrac12(21.4147-1.4147)=10^\circ$ and $\nu_2=\tfrac12(21.4147+1.4147)=11.4147^\circ$. Point 6: $\theta_6=\tfrac12(41.4147-21.4147)=10^\circ$ and $\nu_6=31.4147^\circ$. The equal $10^\circ$ steps make every $\theta$ a round number. Point 8 reaches $\nu(M_e)$ exactly, as the design intends.

**(d) Coordinates.**

*Point 1* (centreline; B = corner on line 0a). $\mu_1=\sin^{-1}(1/1.1041)=64.925^\circ$.

$$
\alpha_{B1}=\tfrac12\left[(\theta-\mu)_{0a}+(0-\mu_1)\right]=\tfrac12\left[-69.248-64.925\right]=-67.086^\circ,
\qquad
\tan\alpha_{B1}=-2.36576.
$$

$$
x_1=x_B-\frac{y_B}{\tan\alpha_{B1}}=0-\frac{1}{-2.36576}=\boxed{0.4227},
\qquad
y_1=0.
$$

*Point 2* (interior; A = point 1, B = corner on line 0b). $\mu_2=42.389^\circ$, so $(\theta+\mu)_2=52.389^\circ$ and $(\theta-\mu)_2=-32.389^\circ$.

$$
\alpha_{12}=\tfrac12\left[(\theta+\mu)_1+(\theta+\mu)_2\right]=\tfrac12\left[64.925+52.389\right]=58.657^\circ,
\qquad
\tan\alpha_{12}=1.64193.
$$

$$
\alpha_{B2}=\tfrac12\left[(\theta-\mu)_{0b}+(\theta-\mu)_2\right]=\tfrac12\left[-32.552-32.389\right]=-32.471^\circ,
\qquad
\tan\alpha_{B2}=-0.63635.
$$

$$
x_2=\frac{0\times(-0.63635)-0.4227\times1.64193-(1-0)}{-0.63635-1.64193}=\frac{-1.69404}{-2.27828}=\boxed{0.7436}
$$

$$
y_2=0+(0.7436-0.4227)\times1.64193=\boxed{0.5268}
$$

*Point 4* (designed wall, BC 2; A = point 3, B = previous wall point, the corner, with wall slope $\theta_{max}$). $\mu_3=33.249^\circ$.

$$
\alpha_{34}=(\theta+\mu)_3=20+33.249=53.249^\circ,
\qquad
\tan\alpha_{34}=1.33909.
$$

$$
\alpha_{04}=\tfrac12(\theta_0+\theta_4)=\tfrac12(20.707+20.000)=20.354^\circ,
\qquad
\tan\alpha_{04}=0.37098.
$$

$$
x_4=\frac{0\times0.37098-0.9365\times1.33909-(1-0.7812)}{0.37098-1.33909}=\frac{-1.25405-0.21882}{-0.96812}=\boxed{1.5214}
$$

$$
y_4=0.7812+(1.5214-0.9365)\times1.33909=\boxed{1.5644}
$$

**(e) Mass-conservation check.** The exit flow is uniform at $M_e$ and the throat is uniform at $M=1$, so the exit half-height must equal the 1D area ratio:

$$
\frac{y_e}{r_a}=\frac{A_e}{A^*}(2.6)=2.8960.
$$

The three-line net gives $2.946$, **1.7 % high**. Three lines with $10^\circ$ steps are a very coarse model of a $20.7^\circ$ fan: each lumped wave carries a large, sudden change of $\theta$, and the straight segments between points miss the curvature of the characteristics. With more lines (first angle $\theta_{max}/n$) the exit converges to the 1D value, $y_e/r_a=2.819$, 2.881 and 2.895 for $n=5$, 20 and 200, while the length settles near $x_e/r_a\approx10.38$. 1D theory fixes the height but gives *"no clue"* about the length (3.3 slide 21). Only MoC does.

> [!check] Python
> $\nu(2.6)=41.41467^\circ$, $\theta_{max}=20.70734^\circ$. States as tabulated (e.g. $M_2=1.48325$, $M_6=2.18780$). Coordinates: 1 $(0.42270,\ 0)$; 2 $(0.74356,\ 0.52683)$; 3 $(0.93649,\ 0.78118)$; 4 $(1.52137,\ 1.56441)$; 5 $(1.5605,\ 0)$; 6 $(2.1855,\ 0.4413)$; 7 $(4.8349,\ 2.4522)$; 8 $(3.4039,\ 0)$; 9 $(10.4731,\ 2.9455)$. Wall segment slopes $20.354^\circ$, $15.000^\circ$, $5.000^\circ$. $A_e/A^*(2.6)=2.89598$. The figure's script (`generate_aerothermo_mock_figures.py`) uses the W05 unit-process functions and reproduces every value.

> [!tip] Why point 4 has the state of point 3
> Between 3 and 4 no other characteristic crosses, so the $C^+$ segment 3–4 runs through uniform flow. The designed wall is set parallel to that flow ($\theta_4=\theta_3$), so nothing reflects and the wave from 0c is cancelled. That is what makes the region next to the wall **simple** and the exit **uniform**.

---

## Q8. Short conceptual questions

**[12 marks; target 22 min]**

- **(a)** Show, with one number, why an "expansion shock" ($M_{n1}<1$) cannot exist. **[2]**
- **(b)** A supersonic wind tunnel is to run at $M=2.5$. Find the minimum second-throat to first-throat area ratio for starting, and explain why the second throat is made variable. **[3]**
- **(c)** In an over-expanded jet, the lip shock reaches the jet boundary. What does it reflect as, and why is this different from a shock meeting a solid wall? **[2]**
- **(d)** In the Lecture 3.4 generic channel (upper wall turned up by $\theta_w$ at the corner, fan represented by two lines a and b), the table gives $\nu_4=\nu_a+2\theta_w$ on the centreline and $\nu_6=\nu_a+3\theta_w$ on the wall. A test measures $M_4=2.0$ and $M_6=2.2$. Find $\theta_w$ and the upstream Mach number $M_0$. **[3]**
- **(e)** In the same example, why does no characteristic reflect from wall point 3? **[2]**

### Q8 solution

**(a)** The entropy change across a normal shock is ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#4. Entropy across a shock and why shocks compress|W03 §4]])

$$
\frac{s_2-s_1}{c_v}=\ln\frac{p_2}{p_1}-\gamma\ln\frac{\rho_2}{\rho_1}.
$$

Apply the jump relations formally at $M_{n1}=0.8$ ($M_{n1}^2=0.64$):

$$
\frac{p_2}{p_1}=1+\frac{2.8}{2.4}(0.64-1)=0.5800,
\qquad
\frac{\rho_2}{\rho_1}=\frac{2.4\times0.64}{2+0.4\times0.64}=0.6809.
$$

$$
\frac{s_2-s_1}{c_v}=\ln0.5800-1.4\ln0.6809=-0.54473+0.53817=-0.00655.
$$

$$
\frac{s_2-s_1}{R}=\frac{-0.00655}{\gamma-1}=-0.0164<0.
$$

An adiabatic process cannot reduce entropy (second law), so $M_{n1}<1$ "shocks", which would be expansion shocks, are impossible. **Shocks only compress**; expansions must happen isentropically through fans.

**(b)** With the starting shock in the test section at $M=2.5$ ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#7. The supersonic wind tunnel (slides 8–11)|W04 §7]]):

$$
\frac{A_{t2}}{A_{t1}}\ge\frac{p_{01}}{p_{02}}=\frac{1}{0.4990}=\boxed{2.004}
$$

Equivalently, $A/A^*(2.5)\big/A/A^*(0.5130)=2.6367/1.3158=2.004$. The second throat must pass the same $\dot m$ at the lower $p_0$ behind the starting shock, so it must be larger. It is made **variable** because this size is only needed to swallow the shock. Once the test section is supersonic, closing it towards $A_{t1}$ makes the diffuser shock weaker and recovers more pressure.

**(c)** The jet boundary is a **constant-pressure** [[Slip Line]]; it cannot support a pressure jump. So a shock arriving at it reflects as an **expansion fan**, which brings the pressure back down to ambient. A solid wall instead fixes the flow **direction**, so a shock reflects as a shock (Q3). Then the fans reflect from the boundary as compressions, and the cycle gives the shock diamonds ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#5. Over-expanded jets: lip shocks and shock diamonds (Lecture 2.7, slides 3–4)|W04 §5]]).

**(d)** ([[SESA3029 W05b - Minimum-Length Nozzle Design#15. The generic MoC example (Lecture 3.4)|W05b §15]], the inverse problem with new numbers.) From the IFT, $\nu_4=\nu(2.0)=26.3798^\circ$ and $\nu_6=\nu(2.2)=31.7325^\circ$. Subtract the two table expressions:

$$
\nu_6-\nu_4=\theta_w
\quad\Rightarrow\quad
\theta_w=31.7325-26.3798=\boxed{5.3527^\circ}
$$

Back-substitute:

$$
\nu_a=\nu_4-2\theta_w=26.3798-10.7054=15.6744^\circ.
$$

IFT rows 1.62 ($15.4518^\circ$) and 1.64 ($16.0427^\circ$):

$$
M_0=1.62+0.02\times\frac{15.6744-15.4518}{16.0427-15.4518}=1.62+0.02\times0.377=\boxed{1.6275}
$$

**(e)** The $C^+$ arriving at 3 comes from point 2, where $\theta_2=\theta_w$: the flow is already parallel to the wall. A prescribed wall reflects only if $\theta_A\neq\theta_W$; here the flow does not turn between 2 and 3, so nothing is reflected and point 5 does not exist. The lecturer's lesson: *"make sure that your calculations … comply with the nature"* (L3-4, ll. 279–281).

> [!check] Python
> (a) At $M_{n1}=0.8$: $\Delta s/c_v=-0.00655$, $\Delta s/R=-0.01638$. (b) $p_{02}/p_{01}(2.5)=0.49901$, ratio 2.00395; $A/A^*(2.5)=2.63672$, $M_2=0.51299$, $A/A^*(M_2)=1.31576$. (d) $\theta_w=5.35268^\circ$, $\nu_a=15.67432^\circ$, $M_0=1.62753$ (IFT interpolation 1.62753).

---

## Links

- Theory: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]] · [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]] · [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]] · [[SESA3029 W05a - Method of Characteristics]] · [[SESA3029 W05b - Minimum-Length Nozzle Design]]
- Concepts: [[Normal-Shock Jump Relations]] · [[Rayleigh Pitot Formula]] · [[Compressible Pitot Probe]] · [[Theta-Beta-Mach Relation]] · [[Weak and Strong Oblique Shocks]] · [[Regular Shock Reflection]] · [[Mach Reflection]] · [[Prandtl-Meyer Function]] · [[Shock-Expansion Theory]] · [[Over- and Under-Expanded Jets]] · [[Supersonic Wind Tunnel]] · [[Riemann Invariants]] · [[Method of Characteristics]] · [[Minimum-Length Nozzle]] · [[Entropy Change Across a Shock]]
- Other worked sets: [[SESA3029 Example Sheet 1 - Solutions]] · [[SESA3029 Example Sheet 2 - Solutions]] · [[SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing]] · [[SESA3029 Test 1 - Solutions]] · [[SESA3029 Test 2 - Solutions]]
- Module: [[SESA3029 Aerothermodynamics Hub]] · [[SESA3029 Formula Sheet]]

## Sources

- Self-written from the topic notes W01–W05b, which cover Lectures 1.1–3.4 and Tutorial Lecture 1 (`02 - Sources/Lectures/`). No question is taken from a past paper.
- Calibration: `03 - Exams & Past Papers/ExamplesSheet1.pdf`, `ExamplesSheet2.pdf`, the Blackboard Test 1 and 2 question files, and the lecturer's exam remarks (L2-2, ll. 74–80; L2-3, ll. 317–319, 379–382; L3-4, ll. 198–203).
- Data sheets: `Aerothermodynamics Formula Sheet.pdf`, `IFT.pdf`, `NST.pdf`, `OSC.pdf`.
- Figures: `01 - Notes/Figures/generate_aerothermo_mock_figures.py` (`at_mock_diamond.png`, `at_mock_mln_net.png`).

## Self-study tasks

> [!todo] All suggested, not lecturer-set
> These are self-set practice tasks for this mock; none was set in a lecture. Each links to its worked solution.

- [ ] Sit Q1, Q4 and Q5 under exam conditions (about 95 min), then mark against the solutions. → [[#Q1. Normal shock and Pitot probe on a supersonic aircraft]] · [[#Q4. Diamond aerofoil by shock-expansion theory]] · [[#Q5. Laval nozzle at design and off-design back pressures]]
- [ ] Redo Q2 (a) and Q3 using the OSC by eye and the NST, and see how far the table answers drift from the exact ones. → [[#Q2. Oblique shock on a supersonic intake ramp]] · [[#Q3. Regular reflection of a ramp shock from a wall]]
- [ ] Redo Q6 without looking, keeping every angle in degrees; then repeat (c) with unaveraged slopes and compare. → [[#Q6. Method of characteristics unit process and a reflecting wall]]
- [ ] Complete Q7 (d) for points 3 and 5–9 and confirm the exit at $(10.473,\ 2.946)$. → [[#Q7. Minimum-length nozzle with three characteristics]]
- [ ] Answer Q8 (a)–(e) aloud in under five minutes each. → [[#Q8. Short conceptual questions]]
