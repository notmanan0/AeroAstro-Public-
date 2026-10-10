---
title: "SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing"
module: "SESA3029 Aerothermodynamics"
type: tutorial
stream: "Block 2: Oblique Shocks and Expansions"
tags: [sesa3029, tutorial-lecture, shock-reflection, regular-reflection-limit, shock-expansion, aerodynamic-centre, wave-drag]
aliases: ["SESA3029 Tutorial 1", "SESA3029 Triangular Wing"]
date: 2026-10-10
status: complete
coverage: "Tutorial Lecture 1 (Fri 9 Oct): Example Sheet 1 Q3 and the isosceles triangular wing; weekend homework solved"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
theory_notes: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]"]
prerequisites: ["[[Regular Shock Reflection]]", "[[Shock-Expansion Theory]]", "[[Prandtl-Meyer Function]]"]
next_topics: ["[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
key_concepts: ["[[Regular Shock Reflection]]", "[[Mach Reflection]]", "[[Shock-Expansion Theory]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
sources: ["02 - Sources/Lectures/Tutorial Lecture #1.txt"]
---

# SESA3029 Tutorial Lecture 1 - Shock Reflection and a Triangular Wing

> [!abstract] Summary
> The first example-question lecture (Fri 9 Oct, `Tutorial Lecture #1.txt`, 240 lines). Prof. Kim meant to start the Laval nozzle, then remembered the slot was a tutorial (ll. 1–3). Two problems:
>
> 1. **Example Sheet 1 Q3**, a ramp shock reflected from a wall ($M_1=2.3$, $\theta=8^\circ$). Two oblique-shock "unit calculations" give $p_3=50.1$ kPa and $M_3=1.70$. Then a fixed-point search for the largest ramp angle that still reflects regularly: guess, check, interpolate, giving $\theta_{RR}\approx16.1^\circ$ (lecture 16.2°).
> 2. An **isosceles triangular wing** (flat bottom, apex at mid-chord, $10^\circ$ base angles) at $M_1=1.7$, $\alpha=10^\circ$, solved by shock-expansion theory. The upper front face is parallel to the stream and carries free-stream pressure; the lower surface takes a $10^\circ$ shock; the rear face a $20^\circ$ fan. Lift is $\approx2.9$ kN/m and $C_{m,LE}\approx-0.29$.
>
> This note adds two things the lecture skipped. First, the lecture's $D=N\sin\alpha$ is a flat-plate shortcut: the inclined upper faces also push **along** the chord, and including that raises the drag by 35% (515 → 694 N/m; $L/D$ 5.7 → 4.2). Second, the **weekend homework** (ll. 228–235), the aerodynamic centre from a second angle of attack, is solved: $x_{ac}/c=0.49$, "very close to half" as predicted.

## Key concepts

- [[Regular Shock Reflection]] · [[Mach Reflection]] · [[Theta-Beta-Mach Relation]] · [[Oblique-Shock Jump Relations]]
- [[Shock-Expansion Theory]] · [[Prandtl-Meyer Function]] · [[Expansion Fan]] · [[Slip Line]]
- [[Aerodynamic Centre and Centre of Pressure]] · [[Shock-Table Interpolation]]

> [!info] Where this sits
> The theory is [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]] §§1–2 (reflection) and §6 (shock-expansion method, Lecture 2.5). The question source is the Blackboard folder *Example questions and solutions → Example sheets and solutions* (ll. 4–7). The triangular wing is from the same folder; its sheet is **not filed in the vault**, so its data are taken from the transcript (ll. 118–189): $c=0.15$ m, $M_1=1.7$, $p_1=20$ kPa, $\alpha=10^\circ$, base angles $10^\circ$.

---

## The whole tutorial in one physical picture

Every problem in Block 2 is built from two Lego bricks. When the flow is turned **into** itself, use an oblique-shock brick. When it is turned **away**, use a Prandtl–Meyer-fan brick. The lecturer's message was to make each brick automatic: *"a standard procedure that you can just memorize… do mechanically"* (l. 35), *"four steps… a kind of unit you can always do without thinking"* (l. 46).

- A **reflection** is two shock bricks in series. The interesting question is when the second brick fails: when the flow behind the first shock is too slow to turn back by $\theta$.
- An **aerofoil made of flat faces** is one brick per corner. Each face then carries one uniform pressure, and the forces follow from pressure × area, face by face.

---

## Part 1. Example Sheet 1 Q3: ramp shock reflected from a wall (ll. 7–117)

$M_1=2.3$, ramp $\theta=8^\circ$, $p_1=0.2$ atm $=20.26$ kPa (l. 15), upper wall parallel to the free stream.

![[at_tut1_rr_limit.png|900]]

### The unit calculation (ll. 35–46)

For one oblique shock of deflection $\theta$ at upstream Mach $M$:

1. $\beta$ from the chart or the $\theta$–$\beta$–$M$ relation;
2. $M_{n1}=M\sin\beta$;
3. normal-shock table or relations: $M_{n2}$ and $p_2/p_1$;
4. $M_2=M_{n2}/\sin(\beta-\theta)$.

### (a) Pressures and Mach numbers

**Incident shock A (ll. 18–34).** The chart reads *"about 32 to 33 ish"*; precisely $\beta_A=32.42^\circ$ (l. 23).

$$
M_{n1}=2.3\sin32.42^\circ=1.2329,
$$

$$
M_{n2}=0.8224,\qquad\frac{p_2}{p_1}=1.6068,
$$

$$
p_2=1.6068\times20.265=32.56\ \text{kPa},
$$

$$
M_2=\frac{0.8224}{\sin(32.42^\circ-8^\circ)}=1.9896.
$$

**Reflected shock B (ll. 47–60).** The wall must turn zone 2 back to horizontal, so the deflection is again $8^\circ$, now at $M_2=1.99$ (l. 49):

$$
\beta_B=37.41^\circ,\qquad M_{n}=1.9896\sin37.41^\circ=1.2087,
$$

$$
M_{n3}=0.8368,\qquad\frac{p_3}{p_2}=1.5379,
$$

$$
p_3=1.5379\times32.56=50.08\ \text{kPa},\qquad M_3=\frac{0.8368}{\sin(37.41^\circ-8^\circ)}=1.704.
$$

All four match the lecture (32.6 kPa, 1.9895, 50.1 kPa, 1.7) and the sheet. The full solution, with the "nearest value" route, is [[SESA3029 Example Sheet 1 - Solutions#Q3. Ramp shock reflected from a wall|ES1 Q3]].

> [!check] Numerical check (Python)
> Exact $\theta$–$\beta$–$M$ roots and normal-shock relations reproduce every number above to the digits shown.

### (b) The largest ramp angle for regular reflection (ll. 63–113)

**Why there is a limit.** The reflected shock must turn zone 2 by the same $\theta$, so we need $\theta\le\theta_{max}(M_2)$. Raise $\theta$ and the incident shock steepens and strengthens, so $M_2$ falls, and $\theta_{max}$ falls with it (ll. 74–83). The two curves cross at the limit. Beyond it, a Mach stem forms ([[Mach Reflection]], ll. 64–66, 112–113).

**The lecture's iteration.**

| Step | Guess $\theta$ | $M_2$ | $\theta_{max}(M_2)$ exact | Lecture |
|---|---|---|---|---|
| 1 | $8^\circ$ | 1.9896 | $22.79^\circ$ | 22.6° from the chart (l. 85) |
| 2 | average $15.3^\circ$ | 1.6973 | $16.95^\circ$ | 16.9° (l. 94); $\beta_A\approx40^\circ$ ✓ |
| 3a | average again $16.1^\circ$ | 1.6634 | $16.17^\circ$ | "very very close" (ll. 95–99) |
| 3b | interpolated $16.2^\circ$ | 1.6591 | $16.07^\circ$ | "also 16.2" (ll. 108–109) |

**Interpolation route (ll. 100–107).** Treat $\theta_{max}$ as a straight line through the two samples $(8,\,22.6)$ and $(15.3,\,16.9)$:

$$
\theta_{max}(\theta)\approx22.6+(\theta-8)\,\frac{16.9-22.6}{15.3-8}=22.6-0.7808\,(\theta-8).
$$

Set $\theta_{max}=\theta$:

$$
\theta=22.6-0.7808\,\theta+6.247,
$$

$$
1.7808\,\theta=28.847,
$$

$$
\boxed{\theta\approx16.2^\circ}\qquad(\text{exact fixed point }16.13^\circ;\ \text{sheet }16^\circ).
$$

> [!tip] Why averaging and interpolating both work
> The curve $\theta_{max}(M_2(\theta))$ is smooth and nearly straight over $8^\circ$–$17^\circ$ (figure, panel b), so a secant through two guesses lands almost on the crossing. Averaging is bisection on the bracket $[\theta,\theta_{max}]$; the secant converges faster. This is the same "two guesses and interpolate" pattern as the slip-line problem in [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#3. Shock–shock interaction and slip lines|W03 §3]] and the $\beta$ search in Lecture 2.5.

> [!warning] "16.2 gives 16.2" is not quite right (ll. 108–109)
> Exactly, $\theta=16.2^\circ$ gives $\theta_{max}(M_2)=16.07^\circ<16.2^\circ$, so it is just past the limit. The true limit is $16.13^\circ$. The discrepancy comes from the chart readings (22.6 for 22.79). Quote **16.1°**, or 16° to the sheet's precision.

---

## Part 2. The isosceles triangular wing (ll. 118–235)

![[at_tut1_triangular_wing.png|900]]

### Geometry and which wave goes where (ll. 118–138)

The lower surface is the chord, $c=0.15$ m. The two upper faces rise at $\varepsilon=10^\circ$ to an apex at mid-chord:

$$
h=\tfrac{c}{2}\tan\varepsilon=0.075\times0.17633=0.01322\ \text{m},
\qquad
\ell=\frac{c/2}{\cos\varepsilon}=0.07616\ \text{m}.
$$

At $\alpha=10^\circ$, measured from the chord:

- **Upper front face** is inclined at $\varepsilon-\alpha=0$ to the stream: *"exactly tangential… the flow just slide through"* (ll. 128–132). No wave, so $M=1.7$, $p=20$ kPa.
- **Lower surface** turns the flow into itself by $\alpha=10^\circ$: an oblique shock (ll. 133–134).
- **Apex**: the flow turns away by $\varepsilon+\varepsilon=20^\circ$, *"not 10"* (ll. 135–138): a Prandtl–Meyer fan.

### Lower surface: one shock unit (ll. 154–164)

$$
\beta=47.17^\circ\quad(\text{chart: "about 47"}),
$$

$$
M_{n1}=1.7\sin47.17^\circ=1.2467,
$$

$$
\frac{p_L}{p_1}=1+\frac{2\gamma}{\gamma+1}\left(M_{n1}^2-1\right)=1+1.1667\times0.5542=1.6466,
$$

$$
p_L=1.6466\times20=32.93\ \text{kPa}\quad(\text{lecture: }33),
$$

$$
M_{n2}=0.8145,\qquad M_L=\frac{0.8145}{\sin37.17^\circ}=1.348.
$$

### Upper rear face: one fan unit (ll. 165–179)

From the isentropic table at $M=1.7$: $\nu=17.81^\circ$ and $p/p_0=0.2026$. Add the turn:

$$
\nu(M_{UR})=17.81^\circ+20^\circ=37.81^\circ.
$$

The table rows $M=2.44$ ($\nu=37.71^\circ$) and $2.46$ ($\nu=38.18^\circ$) bracket it. Interpolate:

$$
M_{UR}=2.44+0.02\times\frac{37.81-37.71}{38.18-37.71}=2.444,
\qquad
\frac{p}{p_0}=0.0638,
$$

$$
p_{UR}=\frac{0.0638}{0.2026}\times20=6.30\ \text{kPa}\quad(\text{lecture: }6.4).
$$

> [!tip] Unit calculation for a fan
> $\nu_{down}=\nu_{up}+\theta$; read $M$ and $p/p_0$ at the new $\nu$; divide by the upstream $p/p_0$, because $p_0$ is unchanged through the isentropic fan. *"The exam question will specify which method to use"*: nearest value or interpolation (l. 176).

### Forces: what the lecture did (ll. 184–195)

**Normal force** (perpendicular to the chord). The lower surface pushes up over the whole chord. Each upper face pushes down; its **projection** on the chord is $c/2$:

$$
N'=p_L\,c-p_{UF}\,\tfrac c2-p_{UR}\,\tfrac c2,
$$

$$
N'=(32.93-10.00-3.15)\times0.15=19.78\times0.15=2.967\ \text{kN/m}.
$$

**The lecture's resolution** treats the wing like a flat plate:

$$
L'\approx N'\cos\alpha=2922\ \text{N/m},
\qquad
D'\approx N'\sin\alpha=515\ \text{N/m},
\qquad
L/D\approx\cot\alpha=5.67.
$$

The lecture says "about six" (l. 195).

### Forces: the chordwise term the shortcut misses

The upper faces are **inclined**, so their pressure forces also have a component **along** the chord. The lecturer noticed this for the moment (ll. 216–224) but not for lift and drag.

- The front face's force is normal to the face, so it tilts **rearward** (it faces up and forward). Its chordwise part is $p_{UF}\,\ell\sin\varepsilon=p_{UF}\,h$.
- The rear face's force tilts **forward**, with chordwise part $p_{UR}\,h$.

The net **axial force** along the chord, positive towards the trailing edge, is:

$$
A'=(p_{UF}-p_{UR})\,h=(20-6.30)\times0.01322=0.181\ \text{kN/m}.
$$

Resolve $N'$ and $A'$ into lift and drag ($N'$ tilted back by $\alpha$, $A'$ along the chord, which points down-stream and down by $\alpha$):

$$
L'=N'\cos\alpha-A'\sin\alpha=2922-31=\boxed{2891\ \text{N/m}},
$$

$$
D'=N'\sin\alpha+A'\cos\alpha=515+178=\boxed{694\ \text{N/m}}.
$$

> [!warning] The flat-plate shortcut misses a quarter of this wing's drag
> $L/D$ drops from 5.67 to **4.17**. The extra drag is the pure **thickness wave drag**: high pressure on the forward-facing slope, low pressure on the rearward-facing slope. It exists even at zero lift, which is exactly why the [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#Diamond aerofoil|diamond aerofoil]] has drag at $\alpha=0$. Use $D=N\sin\alpha$ **only** for a flat plate. For any thick section, resolve each face's force (W03 §7, step 6).

$C_l=L'/(q_\infty c)$ with $q_\infty=\tfrac12\gamma p_1M_1^2=0.7\times20\times2.89=40.46$ kPa:

| | Lecture shortcut | Exact |
|---|---|---|
| $L'$ (N/m) | 2922 | 2891 |
| $D'$ (N/m) | 515 | 694 |
| $C_l$ | 0.4815 | 0.4763 |
| $C_d$ | 0.0849 | 0.1143 |
| $L/D$ | 5.67 | 4.17 |

> [!question] Lecture discussion: why don't airliners fly supersonic? (ll. 196–206)
> A good subsonic aerofoil has $L/D$ of 50 or more, and up to about 150 when highly optimised (l. 199). Supersonic wave drag caps it at single figures, here 4–6. That is why airliners cruise at Mach 0.8–0.9, and why Concorde burned so much fuel.

### Pitching moment about the leading edge (ll. 207–227)

**Lecture method** (nose-up positive). Each face's force acts at the midpoint of its chord projection:

$$
M'_{LE}\approx-p_L\,c\cdot\tfrac c2+p_{UF}\,\tfrac c2\cdot\tfrac c4+p_{UR}\,\tfrac c2\cdot\tfrac{3c}4,
$$

$$
M'_{LE}\approx c^2\left(-16.47+2.50+2.36\right)=-11.60\times0.0225=-0.2611\ \text{kN m/m}.
$$

**Exact.** Each face's force acts at the face midpoint, normal to the face.

- Front face: the line of action is perpendicular to the face through its midpoint, at distance $\ell/2$ from the LE along the face. Arm $=\ell/2$:

$$
M'_{UF}=+p_{UF}\,\ell\cdot\frac{\ell}{2}=p_{UF}\,\frac{c^2}{8\cos^2\varepsilon}=p_{UF}\,\frac{c^2}{8}\left(1+\tan^2\varepsilon\right).
$$

- Rear face: the midpoint is $\mathbf r=(3c/4,\ h/2)$ and the inward unit normal is $\mathbf n=(-\sin\varepsilon,-\cos\varepsilon)$. The arm is $|\mathbf r\times\mathbf n|$:

$$
|\mathbf r\times\mathbf n|=\tfrac{3c}{4}\cos\varepsilon-\tfrac h2\sin\varepsilon=\tfrac c4\,\frac{3\cos^2\varepsilon-\sin^2\varepsilon}{\cos\varepsilon},
$$

$$
M'_{UR}=+p_{UR}\,\ell\,|\mathbf r\times\mathbf n|=p_{UR}\,\frac{c^2}{8}\left(3-\tan^2\varepsilon\right).
$$

- Lower surface: $M'_L=-p_L\,c^2/2$, unchanged.

Add, with $\tan^2\varepsilon=0.03109$:

$$
M'_{LE}=c^2\left[-\frac{32.93}{2}+\frac{20\times1.03109}{8}+\frac{6.302\times2.96891}{8}\right]=0.0225\times(-11.549)=\boxed{-0.2599\ \text{kN m/m}}.
$$

This is the lecture's *"minus 260 as opposed to [2]61"* (l. 225): a 0.5% correction for the moment, but 35% for the drag. The moment is nose-down.

$$
C_{m,LE}=\frac{M'_{LE}}{q_\infty c^2}=-0.2868\ (\text{shortcut}),\quad-0.2854\ (\text{exact}).
$$

### Weekend homework: the aerodynamic centre (ll. 228–235)

> *"Use another angle of attack… for example 11 degrees or 9 degrees and calculate cl and cm values again and calculate this approximate derivative and check if you are going to get half"* (ll. 232–234).

$$
\frac{x_{ac}}{c}=-\frac{\mathrm dC_{m,LE}}{\mathrm dC_l}\approx-\frac{C_{m}(\alpha_2)-C_{m}(\alpha_1)}{C_l(\alpha_2)-C_l(\alpha_1)}.
$$

**What changes at a new $\alpha$.** The lower shock is now $\alpha$. The upper front face is no longer parallel to the stream: at $9^\circ$ it is turned **into** the flow by $1^\circ$ (a weak shock); at $11^\circ$ it is turned **away** by $1^\circ$ (a weak fan). The apex fan stays at $20^\circ$, but now starts from the new front-face Mach number.

| $\alpha$ | $p_L$ (kPa) | front face | $p_{UF}$ (kPa) | $M_{UF}$ | $M_{UR}$ | $p_{UR}$ (kPa) | $C_l$ | $C_{m,LE}$ |
|---|---|---|---|---|---|---|---|---|
| $9^\circ$ | 31.34 | $1^\circ$ shock | 21.05 | 1.666 | 2.403 | 6.72 | 0.4260 | −0.2599 |
| $10^\circ$ | 32.93 | none | 20.00 | 1.700 | 2.444 | 6.30 | 0.4815 | −0.2868 |
| $11^\circ$ | 34.62 | $1^\circ$ fan | 18.99 | 1.734 | 2.487 | 5.90 | 0.5380 | −0.3145 |

(Lecture's shortcut for $C_l$ and $C_m$; exact values in the figure.)

**Central difference** over $9^\circ\to11^\circ$:

$$
\frac{x_{ac}}{c}\approx-\frac{-0.3145-(-0.2599)}{0.5380-0.4260}=\frac{0.0546}{0.1120}=\boxed{0.487}\qquad(\text{exact forces: }0.491).
$$

One-sided differences give 0.484 ($9\to10^\circ$) and 0.490 ($10\to11^\circ$).

> [!check] Is "half" right?
> Close, as the lecturer expected (l. 235). Linearised supersonic (Ackeret) theory, Weeks 7–8, puts the aerodynamic centre of **any** thin aerofoil at exactly $c/2$. Shock-expansion theory is the exact, nonlinear version, so a $10^\circ$-thick section with finite turning angles lands at about $0.49c$. The 2% shortfall is a nonlinear effect. Compare the flat plate in [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#6. The shock-expansion method|W03 §6]], where $C_{m,LE}\propto C_l$ exactly.

> [!tip] Centre of pressure is not the aerodynamic centre here
> At $10^\circ$, $x_{cp}/c=-M'_{LE}/(N'c)=0.261/(2.967\times0.15)=0.587$: the cp sits **behind** the ac. For the flat plate the two coincided, because $C_{m,LE}$ was exactly proportional to $C_l$ (no zero-lift moment). The triangular wing is cambered in effect (flat bottom, peaked top), so it has a nose-down moment at zero lift. The cp then moves with $\alpha$ while the ac stays put.

### Why look at sharp, mid-chord-thickness shapes? (ll. 141–153)

Subsonic aerofoils have round leading edges and maximum thickness near the quarter chord. Supersonic sections are sharp-edged, with maximum thickness near **half chord**. *"Later on we will mathematically prove that this type… [is] best to reduce… wave drag"* (ll. 152–153). This is the optimum-aerofoil result of Weeks 7–8.

---

## Transcript slips (Tutorial Lecture 1)

> [!warning] Slips in `Tutorial Lecture #1.txt`
> | Line | Said | Correct |
> |---|---|---|
> | l. 2 | "level nozzle" | Laval nozzle |
> | l. 22 | "2.3 oh no it's not… 2.123" | garbled chart reading at $M_1=2.3$; $\beta_A=32.4^\circ$ (l. 23) |
> | ll. 68, 79 | "nine one point nine eight nine five", "one point nine nine nine five" | $M_2=1.9895$ |
> | ll. 71–73, 85 | $\theta_{max}(1.99)$ "about 23… 22.6" | $22.79^\circ$ exactly; 22.6 is a chart reading |
> | ll. 108–109 | guess 16.2° "then result theta is going to be also 16.2" | it gives $16.07^\circ$; the exact limit is $16.13^\circ$ |
> | l. 173 | $\nu(M_1)$ "70.81" | $17.81^\circ$ |
> | l. 174 | "37.7 is here" | $\nu(2.44)=37.71^\circ$, the lower bracketing row |
> | l. 178 | $p_{2U}$ "6.4 kilopascal" | **6.30 kPa** ($0.0638/0.2026\times20$) |
> | ll. 189–190 | "19.8 k times c… 0.15… 217 newton per metre" | $19.8\times0.15=2.97$ kN/m $=$ **2970 N/m** |
> | l. 193 | drag "508 newton" | $N'\sin\alpha=515$ N/m; exactly **694 N/m** (see the warning above) |
> | ll. 212–214 | "momentum is at the quarter core… three quarters" | moment **arm** $c/4$ and $3c/4$ |
> | l. 225 | "minus 260 as opposed to 161" | −260 vs **−261** N m/m |
> | l. 226 | "the one percent difference" | 0.46% |
> | l. 230 | ac as "the derivative of pitch moment with respect to cl" | $x_{ac}/c=-\mathrm dC_{m,LE}/\mathrm dC_l$ (minus sign) |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Theory: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]] (§§1–2 reflection, §6 shock-expansion)
- Next lecture topic (announced, l. 2): [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- Worked sheets: [[SESA3029 Example Sheet 1 - Solutions]] (Q3 in full; Q4 flat plate; Q6–Q7 diamond)
- Concepts: [[Regular Shock Reflection]] · [[Mach Reflection]] · [[Shock-Expansion Theory]] · [[Prandtl-Meyer Function]] · [[Aerodynamic Centre and Centre of Pressure]]
- Formulae: [[SESA3029 Formula Sheet]]

## Sources

- `02 - Sources/Lectures/Tutorial Lecture #1.txt` (Fri 9 Oct, 240 lines; Prof. Jae-Wook Kim)
- `03 - Exams & Past Papers/ExamplesSheet1.pdf`, Q3
- Triangular-wing question: Blackboard *Example questions and solutions* folder (not filed in the vault); data from the transcript
- Figures: `generate_aerothermo_tutorial_figures.py` (`tut1_rr_limit`, `tut1_triangular_wing`)

## Self-study tasks

> [!todo] What the tutorial set
> Two explicit pieces of homework (ll. 117 and 232–235), both solved here. The rest are *suggested, not lecturer-set*. Attempt each closed-book, then check against the linked section.

### Lecturer-set

- [ ] **Lecturer-set (l. 117):** *"You need to put in your work to get to find the answers yourself… it's your homework"*: do ES1 Q3 (a) and (b) in full, with the tables. → [[#Part 1. Example Sheet 1 Q3: ramp shock reflected from a wall (ll. 7–117)]]
- [ ] **Lecturer-set, weekend homework (ll. 232–235):** repeat the triangular wing at $\alpha=9^\circ$ or $11^\circ$, form $-\Delta C_m/\Delta C_l$ and check that $x_{ac}\approx c/2$. Answer: 0.487. → [[#Weekend homework: the aerodynamic centre (ll. 228–235)]]
- [ ] **Lecturer-set (ll. 35, 114–115):** practise the oblique-shock and fan "unit calculations" until they are automatic. → [[#The unit calculation (ll. 35–46)]], [[#Upper rear face: one fan unit (ll. 165–179)]]

### Calculations

- [ ] Triangular wing at $10^\circ$: $p_L=32.93$, $p_{UR}=6.30$ kPa; $L'=2891$, $D'=694$ N/m; $M'_{LE}=-260$ N m/m. → [[#Forces: the chordwise term the shortcut misses]]
- [ ] *(Suggested)* Find the regular-reflection limit with the secant from guesses $8^\circ$ and $15.3^\circ$. → [[#(b) The largest ramp angle for regular reflection (ll. 63–113)]]
- [ ] *(Suggested)* Find the trailing-edge slip-line angle of the triangular wing (the upper stream is compressed, the lower expanded). → [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#3. Shock–shock interaction and slip lines|W03 §3]] method

### Concepts

- [ ] Explain why $\theta_{max}(M_2)$ falls as the ramp angle rises, and what happens past the limit (ll. 74–83). → [[#(b) The largest ramp angle for regular reflection (ll. 63–113)]]
- [ ] Explain why $D=N\sin\alpha$ is exact for a flat plate but wrong for the triangular wing. → [[#Forces: the chordwise term the shortcut misses]]
- [ ] Explain why the cp and the ac coincide for a flat plate but not for this wing. → [[#Weekend homework: the aerodynamic centre (ll. 228–235)]]
- [ ] Explain why supersonic $L/D$ is so much lower than subsonic $L/D$ (ll. 196–206). → [[#Forces: the chordwise term the shortcut misses]]
