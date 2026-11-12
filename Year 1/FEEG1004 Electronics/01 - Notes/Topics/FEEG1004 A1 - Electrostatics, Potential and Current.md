---
title: "FEEG1004 A1 - Electrostatics, Potential and Current"
module: "FEEG1004 Electronics"
type: topic
stream: "Part A: Electrical Fundamentals and DC Circuits"
order: 1
tags: [feeg1004, fundamentals, electrostatics, electric-field, potential, current, power]
aliases: ["Lecture 1a-1b", "Electrostatics", "Electric current", "Voltage and electric field"]
date: 2026-09-27
status: lectured
coverage: "1a Electrostatics ll. 12–207; 1b Electric Current ll. 1–96; L1 (9 Oct 2024) ll. 199–235, 309–410, 453–526. Short names expanded in Sources."
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]"]
key_concepts: ["[[Coulomb's Law and Electric Field]]", "[[Electric Potential and Voltage]]", "[[Electric Current and Electrical Power]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]"]
sources:
  - "02 - Sources/S1 Fundamentals/S1-W02-1ab Electrostatics and Electric Current - Recorded.pdf"
  - "02 - Sources/S1 Fundamentals/S1-W02 Electrostatics - Interactive.pdf"
  - "02 - Sources/S1 Fundamentals/S1 Equations Sheet.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2020-07-21 - 1a Electrostatics EC FEEG1004 PGJ 21 July 2020 at 14 44 21.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2020-07-21 - 1b Electric Current EC FEEG1004 PGJ 21 July 2020 at 17 31 03.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 1.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors.pdf"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 01 - Electrostatics, Magnetism & Resistors - Answers.pdf"
---

# FEEG1004 A1 - Electrostatics, Potential and Current

> [!abstract] Summary
> Electric charges exert forces described by Coulomb's law, and the electric field gives force per unit positive test charge, $\mathbf E=\mathbf F/q$. Potential difference describes energy per charge, with $\Delta U_e=q\Delta V$ and $E_x=-dV/dx$. Moving charge produces current, $i=dQ/dt$, and transfers power, $p=vi$, with its sign determined by the voltage polarity and current direction.

> [!summary]- Exam use: quick path
> - **Use it when:** finding forces or fields from charges, particle energy across a voltage, current from transferred charge, drift speed or electrical power.
> - **Assumptions:** fixed point charges in free space, or air approximated as free space; uniform plate field only away from the edges; negligible energy losses for particle acceleration; steady current for $Q=It$.
> - **Method:** 1. Draw charges, axes and voltage polarities. 2. Find each field contribution and add vectors. 3. Use the signed potential change to find energy. 4. Use charge per time for current, then the voltage across and current through the same element for power.
> - **Common mistakes:** taking electron motion as the direction of conventional current; using the wire diameter as its radius when calculating area.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q1: Two +1 mC charges at x = -10 cm and x = +10 cm|Tutorial 1 Q1]]

A charged object changes the forces experienced by other charges around it. Field lines show the direction in which a small positive test charge would be pushed, while their spacing indicates field strength. A negative charge experiences a force in the opposite direction. When several charges are present, each contributes to the field at the same observation point.

Potential describes the energy change as a charge moves between positions. A positive charge released from rest gains kinetic energy as it moves towards lower potential; an electron gains kinetic energy towards higher potential. In a metal, an applied field adds a small average drift to the electrons' rapid random motion. Current measures the resulting charge transfer, while voltage is the energy transferred per coulomb.

## 1. Electric charge

**Electric charge** is a property of matter that can be positive or negative. Like charges repel and unlike charges attract. The algebraic total charge of a closed system is conserved: transferring electrons between objects changes their individual charges without creating net charge.

For the electron and proton transfers considered here, charge occurs in integer multiples of the elementary charge, $e=1.602\times10^{-19}\ \mathrm C$. An electron carries $-e$ and a proton carries $+e$. If $N$ counts the excess elementary charges with their sign,

$$
Q=Ne.
$$

The number of elementary charges corresponding to a charge magnitude is therefore

$$
|N|=\frac{|Q|}{e}.
$$

For the $1\ \mathrm C$ reference amount,

$$
|N|=\frac{1\ \mathrm C}{1.602\times10^{-19}\ \mathrm C}=6.24\times10^{18}.
$$

Triboelectric charging transfers electrons when materials are rubbed together. An aircraft can acquire charge through contact with particles during flight, so charge equalisation before refuelling prevents a potential difference from producing a spark near fuel vapour. An object can also respond to a nearby charge without gaining net charge, through the redistribution described below.

## 2. Coulomb's law and the electric field

For stationary point charges in free space, separated by distance $r$, Coulomb's law gives the force magnitude:

$$
|F|=\frac{1}{4\pi\varepsilon_0}\frac{|q_1q_2|}{r^2}.
$$

Here $\varepsilon_0\approx8.85\times10^{-12}\ \mathrm{C^2\,N^{-1}\,m^{-2}}$ is the permittivity of free space. The force acts along the line joining the charges; attraction or repulsion fixes its direction. The magnitude formula does not by itself give a signed Cartesian component. These calculations approximate air by free space.

Bulk matter contains large positive and negative charges whose effects largely cancel. Removing a fraction of its electrons leaves a net positive charge: that imbalance enters Coulomb's law, which explains why even a small fractional imbalance can have a large effect.

The **electric field** is force per unit positive test charge. For a test charge $q_t>0$ small enough not to disturb the source charge distribution,

$$
\mathbf E=\frac{\mathbf F}{q_t}.
$$

For one point source charge $q$, substitute Coulomb's law:

$$
|E|=\frac{1}{q_t}\left(\frac{1}{4\pi\varepsilon_0}\frac{|q|q_t}{r^2}\right).
$$

Cancelling the test charge gives

$$
|E|=\frac{1}{4\pi\varepsilon_0}\frac{|q|}{r^2}.
$$

The field points away from a positive source and towards a negative source. Once the field is known, the force on a charge of either sign follows by rearranging its definition:

$$
\mathbf F=q\mathbf E.
$$

### Adding fields and reading field lines

Superposition means finding each source's field at the observation point, including its direction, then adding the vectors:

$$
\mathbf E_{\mathrm{total}}=\sum_k\mathbf E_k.
$$

Horizontal components are added separately from vertical ones. Equal field magnitudes cancel only when their directions are opposite. For two equal positive charges placed symmetrically to the left and right of a point P, their fields at P cancel. Adding a negative charge directly above P leaves a resultant field pointing upwards, towards that negative charge.

Field lines point along the force on a positive test charge. Closely spaced lines indicate a stronger field. A pattern joining two charges with arrows from left to right therefore identifies the left source as positive and the right source as negative. A light positive particle passing a much heavier positive charge can be deflected while the heavy charge moves very little; the deflection is repulsive, as in the Rutherford-scattering picture.

### Attraction through induced charge

A nearby positive charge polarises a neutral block: negative charge is displaced towards the near surface and positive charge towards the far surface. The nearer opposite charge attracts more strongly than the farther like charge repels, because the interaction decreases with distance squared. The resulting force is attractive in this arrangement even though the block has zero net charge. Reversing the inducing charge reverses the polarisation, so the force remains attractive for this neutral, polarisable block.

## 3. Electric potential: the gravity analogy

Gravitational potential separates the landscape from the mass placed in it: the change in height determines energy change per unit mass. Electric potential does the corresponding job for charge. The symbol $U_e$ denotes electrical potential energy, leaving $\mathbf E$ for the electric field. Between positions A and B, define $\Delta V=V_B-V_A$:

$$
\Delta V=\frac{\Delta U_e}{q}.
$$

Multiplying by the transported charge gives

$$
\Delta U_e=q\Delta V.
$$

Thus $1\ \mathrm V=1\ \mathrm{J\,C^{-1}}$. For a fixed voltage difference, doubling the transported charge doubles the energy change. The sign matters: a positive charge moved to higher potential gains potential energy, whereas an electron making the same move loses potential energy.

### Why the field is the negative potential gradient

For a small displacement along the x direction, the work done by the electric force is

$$
dW_{\mathrm{field}}=F_x\,dx.
$$

Electrostatic work reduces electrical potential energy:

$$
F_x\,dx=-dU_e.
$$

For a fixed charge, substitute $dU_e=q\,dV$:

$$
F_x\,dx=-q\,dV.
$$

Divide by $dx$, then by $q$:

$$
F_x=-q\frac{dV}{dx}.
$$

$$
\boxed{E_x=-\frac{dV}{dx}}.
$$

The field points towards decreasing potential. Because $1\ \mathrm J=1\ \mathrm{N\,m}$, the units $\mathrm{V\,m^{-1}}$ and $\mathrm{N\,C^{-1}}$ are equivalent.

### Uniform fields and voltage arrows

Take A at $x=0$ and B at $x=L$. Rearranging the gradient relation,

$$
dV=-E_x\,dx.
$$

Integrating between the endpoints gives

$$
V_B-V_A=-\int_0^L E_x\,dx.
$$

Assuming $E_x$ is constant along this straight path,

$$
V_B-V_A=-E_xL.
$$

For a separation along the field, the magnitude relation is therefore

$$
\boxed{|\Delta V|=EL}.
$$

Between broad parallel plates this uniform-field approximation applies away from their edges. With $0\ \mathrm V$ on the left, $5\ \mathrm V$ on the right and a $4\ \mathrm m$ gap, taking x positive to the right gives

$$
E_x=-\frac{5\ \mathrm V-0\ \mathrm V}{4\ \mathrm m}=-1.25\ \mathrm{V\,m^{-1}}.
$$

The magnitude is $1.25\ \mathrm{V\,m^{-1}}$, directed left. The voltage arrow has its head at the higher-potential end for a positive labelled voltage, so it points opposite to the field in this example. A ground symbol can mark the chosen zero-potential reference without implying a physical connection to Earth.

![[ee_a1_uniform_field.png|900]]

The accelerator above has the opposite polarity: the left plate is at higher potential, so the field and the acceleration of positive protons point right.

### Converting potential energy to kinetic energy

Assuming the electric field is the only force doing work, with negligible losses,

$$
\Delta K=-\Delta U_e.
$$

Substitute the potential-energy relation:

$$
K_f-K_i=-q(V_f-V_i).
$$

Changing the order of the potential terms gives

$$
K_f-K_i=q(V_i-V_f).
$$

For release from rest, $K_i=0$. Positive charge gains kinetic energy by moving from high to low potential; negative charge gains kinetic energy by moving from low to high potential. Equal charge magnitudes crossing the same voltage magnitude gain equal kinetic energies, even when their masses differ.

## 4. Current and conduction

**Conventional current** has the direction in which positive charge would move. In a metal, mobile electrons drift opposite to conventional current through a lattice of positive ions. In an ionic solution, positive ions move with the field and negative ions against it; both motions contribute to conventional current in the same direction.

At a chosen cross-section, current is the rate of signed charge transfer:

$$
i=\frac{dQ}{dt}.
$$

For steady current $I$, multiply by $dt$ and integrate over a time interval $\Delta t$:

$$
\begin{aligned}
dQ&=I\,dt,\\
\Delta Q&=\int_0^{\Delta t}I\,dt,\\
\Delta Q&=I\Delta t.
\end{aligned}
$$

An ampere is a coulomb per second. If current varies with time, retain the integral of $i(t)$ rather than multiplying one instantaneous value by the whole interval.

### Deriving drift speed by counting electrons

Let $\rho_e$ be the number of mobile electrons per unit volume, $A$ the wire cross-sectional area and $v$ the drift-speed magnitude, for a uniform wire with uniform average drift. In time $\Delta t$, the electrons advance a distance $v\Delta t$, sweeping volume $Av\Delta t$. The number passing the section is

$$
\Delta N=\rho_eAv\Delta t.
$$

Multiplying by the charge magnitude per electron gives the transferred charge magnitude:

$$
|\Delta Q|=e\rho_eAv\Delta t.
$$

Divide by the time interval:

$$
I=e\rho_eAv.
$$

Solving for speed gives

$$
\boxed{v=\frac{I}{e\rho_eA}}.
$$

Here $I$ is the current magnitude; the electron drift direction is opposite to its conventional direction. Random electron motion has a much greater speed but no preferred direction, so it does not itself produce this net current. The electrical disturbance propagates along the wire as an electromagnetic signal, much faster than the electrons drift.

## 5. Power

To calculate power absorbed by an element, choose a voltage $v$ with labelled positive and negative terminals and take positive current $i$ as entering its positive terminal. This is the **passive sign convention**. Passing signed charge $dQ$ through the element from the labelled positive terminal to the labelled negative terminal transfers energy

$$
dW_{\mathrm{absorbed}}=v\,dQ.
$$

Divide by time:

$$
\frac{dW_{\mathrm{absorbed}}}{dt}=v\frac{dQ}{dt}.
$$

Using the definitions of power and current gives

$$
\boxed{p=vi}.
$$

For steady DC values this becomes $P=VI$. Positive absorbed power means energy enters the element; negative absorbed power means the element supplies energy. If current is defined as leaving the positive terminal, power absorbed is $-vi$. Use the voltage across and current through the same element.

The units check directly: $(\mathrm{J\,C^{-1}})(\mathrm{C\,s^{-1}})=\mathrm{J\,s^{-1}}=\mathrm W$. This energy accounting applies to a particle beam as well as to a circuit component.

## Worked examples

### Two positive charges: force and field between them

Tutorial 1 Q1 places $q=+1\ \mathrm{mC}=+10^{-3}\ \mathrm C$ at each of $x=\pm10\ \mathrm{cm}$. Their separation is $r=0.20\ \mathrm m$, so the force magnitude on the left charge is

$$
|F|=\frac{(10^{-3}\ \mathrm C)(10^{-3}\ \mathrm C)}{4\pi(8.85\times10^{-12}\ \mathrm{C^2\,N^{-1}\,m^{-2}})(0.20\ \mathrm m)^2}.
$$

Evaluating gives $|F|=2.25\times10^5\ \mathrm N$. Repulsion pushes the left charge to the left, so its signed force is $F_x=-2.25\times10^5\ \mathrm N$.

For an observation point between the charges, use x in metres and take right as positive. Its distances from the left and right sources are $0.10\ \mathrm m+x$ and $0.10\ \mathrm m-x$. The left field points right and the right field points left, giving

$$
\begin{aligned}
E_{\mathrm{left},x}&=\frac{10^{-3}\ \mathrm C}{4\pi\varepsilon_0(0.10\ \mathrm m+x)^2},\\
E_{\mathrm{right},x}&=-\frac{10^{-3}\ \mathrm C}{4\pi\varepsilon_0(0.10\ \mathrm m-x)^2}.
\end{aligned}
$$

Add the two signed contributions:

$$
E_x=E_{\mathrm{left},x}+E_{\mathrm{right},x}.
$$

$$
\boxed{E_x(x)=\frac{10^{-3}\ \mathrm C}{4\pi\varepsilon_0}\left[\frac{1}{(0.10\ \mathrm m+x)^2}-\frac{1}{(0.10\ \mathrm m-x)^2}\right]}.
$$

This expression applies only for $-0.10\ \mathrm m<x<0.10\ \mathrm m$. Outside the charges, both fields point in the same direction and the signs must be reassessed. At the charge positions the ideal point-charge field is singular.

![[ee_a1_field_superposition.png|900]]

> [!check] Midpoint cancellation
> At $x=0\ \mathrm m$, the contributions are $+8.99\times10^8\ \mathrm{N\,C^{-1}}$ and $-8.99\times10^8\ \mathrm{N\,C^{-1}}$. Their sum is zero. This cancellation at the midpoint does not remove the repulsive force between the source charges.

### Proton accelerator: field, energy, current and power

The accelerator has a $100\ \mathrm V$ potential difference across a $0.10\ \mathrm m$ gap, with the left plate positive. Neglect fringing and losses, and assume the beam does not significantly alter the applied field. Its field magnitude is

$$
E=\frac{100\ \mathrm V}{0.10\ \mathrm m}=1.00\times10^3\ \mathrm{V\,m^{-1}}.
$$

For $Q=+0.10\ \mathrm C$ of protons moving from $100\ \mathrm V$ to $0\ \mathrm V$, substitute into the kinetic-energy change:

$$
\Delta K=(0.10\ \mathrm C)(100\ \mathrm V-0\ \mathrm V)=10\ \mathrm J.
$$

If this charge crosses the gap steadily in $2.0\ \mathrm s$, rearrange $Q=I\Delta t$:

$$
I=\frac{Q}{\Delta t}.
$$

$$
I=\frac{0.10\ \mathrm C}{2.0\ \mathrm s}=0.050\ \mathrm A.
$$

The protons and conventional current both travel left to right. The electrical power transferred to the beam is

$$
P=(100\ \mathrm V)(0.050\ \mathrm A)=5.0\ \mathrm W.
$$

> [!check] Energy and power agree
> Over $2.0\ \mathrm s$, the transferred energy is $(5.0\ \mathrm W)(2.0\ \mathrm s)=10\ \mathrm J$, equal to the beam's kinetic-energy gain. An ideal source supplying this transfer has absorbed power $-5.0\ \mathrm W$ under the passive sign convention.

### Electron and proton across the same voltage

An electron and a proton are released from opposite plates, $4\ \mathrm{cm}$ apart with a $1000\ \mathrm V$ difference. The electron moves from the negative plate to the positive plate, so

$$
\Delta K_e=(-1.602\times10^{-19}\ \mathrm C)(0\ \mathrm V-1000\ \mathrm V)=1.602\times10^{-16}\ \mathrm J.
$$

For the proton travelling the other way,

$$
\Delta K_p=(+1.602\times10^{-19}\ \mathrm C)(1000\ \mathrm V-0\ \mathrm V)=1.602\times10^{-16}\ \mathrm J.
$$

For non-relativistic motion from rest, rearrange the kinetic-energy formula one operation at a time:

$$
\begin{aligned}
K&=\frac12mv^2,\\
2K&=mv^2,\\
\frac{2K}{m}&=v^2,\\
v&=\sqrt{\frac{2K}{m}}.
\end{aligned}
$$

The equal energies therefore give different speeds: the heavier proton is slower, so the answer is C. With the voltage-arrow head at the right plate, that plate is positive and the proton starts on the right.

### Drift speed in the copper wire

The stated values are $I=1\ \mathrm A$, wire diameter $d=0.10\ \mathrm{cm}$, $\rho_e=8.5\times10^{22}\ \mathrm{cm^{-3}}$ and the rounded electron charge magnitude $e=1.6\times10^{-19}\ \mathrm C$. Keep all lengths in centimetres so the number-density units cancel consistently. First find the radius:

$$
r=\frac{0.10\ \mathrm{cm}}{2}=0.050\ \mathrm{cm}.
$$

The circular cross-sectional area is

$$
A=\pi(0.050\ \mathrm{cm})^2=7.854\times10^{-3}\ \mathrm{cm^2}.
$$

Substitute into the drift-speed result:

$$
v=\frac{1\ \mathrm{C\,s^{-1}}}{(1.6\times10^{-19}\ \mathrm C)(8.5\times10^{22}\ \mathrm{cm^{-3}})(7.854\times10^{-3}\ \mathrm{cm^2})}.
$$

This gives $v=9.36\times10^{-3}\ \mathrm{cm\,s^{-1}}$. Converting the time unit,

$$
v=(9.36\times10^{-3}\ \mathrm{cm\,s^{-1}})(3600\ \mathrm{s\,h^{-1}})=33.7\ \mathrm{cm\,h^{-1}}.
$$

> [!check] Recovering the current
> Using the unrounded area and speed, $e\rho_eAv=1.00\ \mathrm A$. Equivalently, $6.25\times10^{18}$ electrons cross the section per second. The small drift speed is consistent with a large number of mobile carriers.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: none; this is the first topic.
- Next: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]
- Concepts: [[Coulomb's Law and Electric Field]] · [[Electric Potential and Voltage]] · [[Electric Current and Electrical Power]]
- Worked problems: [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions]]
- Circuit continuation: [[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]

## Sources

- `S1-W02-1ab Electrostatics and Electric Current - Recorded.pdf`, PDF pp. 4–15 and 18–24; `S1-W02 Electrostatics - Interactive.pdf`, pp. 13–22. Both decks were read in full, including their diagrams. Paths are in the frontmatter.
- **1a Electrostatics:** `FEEG1004 Lecture 2020-07-21 - 1a Electrostatics EC FEEG1004 PGJ 21 July 2020 at 14 44 21.txt` (ll. 12–90: charge, Coulomb and field; ll. 91–160: potential and superposition; ll. 161–207: induction and uniform field).
- **1b Electric Current:** `FEEG1004 Lecture 2020-07-21 - 1b Electric Current EC FEEG1004 PGJ 21 July 2020 at 17 31 03.txt` (ll. 1–21: carriers and current; ll. 22–65: drift; ll. 66–96: voltage arrows and power).
- **L1:** `FEEG1004 Lecture 1.txt`, mapped to 9 October 2024 by the Transcript Index (ll. 199–235: recap; ll. 309–348: field direction; ll. 350–410: accelerator; ll. 453–475: repulsive scattering; ll. 481–526: electron–proton comparison and reference potential). All three transcripts were read in full; administrative material is excluded from coverage.
- `S1 Equations Sheet.pdf`, PDF pp. 2–3: Coulomb, field, voltage and power entries. The remaining entries belong to later topics.
- Tutorial Sheet 01, Q1(a–b), with its official answers p. 1. The force, field signs and domain agree with the official solution.
- All numerical values were recomputed in Python, including the four worked examples, unit conversions and independent energy/current checks. Figures: `generate_fundamentals_figures.py`, using the shared Year 3 style through `feeg1004_style.py`.

## Self-study tasks

### Core

- [ ] Find the magnitude and direction of the force on the left charge (Tutorial Sheet 1 Q1(a)). → [[#Two positive charges: force and field between them]] · [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q1: Two +1 mC charges at x = -10 cm and x = +10 cm|Tutorial 1 Q1]]
- [ ] Derive the signed field between the two charges and state its domain (Tutorial Sheet 1 Q1(b)). → [[#Two positive charges: force and field between them]] · [[FEEG1004 Tutorial 1 - Electrostatics, Magnetism and Resistors Solutions#Q1: Two +1 mC charges at x = -10 cm and x = +10 cm|Tutorial 1 Q1]]
- [ ] Explain the upward resultant for the three-charge arrangement, then explain how vector addition still works if P is moved (L1, ll. 309–329). → [[#Adding fields and reading field lines]]
- [ ] Find the accelerator's field, energy transfer, current and current direction (L1, ll. 350–410; interactive p. 17). → [[#Proton accelerator: field, energy, current and power]]
- [ ] Compare the electron's and proton's impact energies and speeds, and identify the proton using the voltage arrow (L1, ll. 481–526; interactive pp. 20–22). → [[#Electron and proton across the same voltage]]
- [ ] Calculate the copper-wire drift speed from the stated diameter (1b, ll. 22–46; recorded p. 21). → [[#Drift speed in the copper wire]]

### Further practice

- [ ] Use Coulomb's law and the large force in Q1 to explain why the 1%-electron-removal thought experiment would have a large electrostatic effect (1a, ll. 61–65; reading prompt on recorded p. 6). → [[#2. Coulomb's law and the electric field]]
- [ ] Identify the charge signs from the field-line arrows and explain the repulsive-scattering picture (L1, ll. 343–348 and 453–475; interactive pp. 16 and 18–19). → [[#Adding fields and reading field lines]]
- [ ] Explain why reversing the charge near the neutral block still gives attraction (1a, ll. 161–184; recorded p. 13). → [[#Attraction through induced charge]]
- [ ] Calculate the signed field for the $0\ \mathrm V$ and $5\ \mathrm V$ plates, and distinguish its direction from the voltage arrow (1a, ll. 185–205; recorded p. 14). → [[#Uniform fields and voltage arrows]]

## Transcript and slide slips

### Missing minus sign in the potential gradient

> [!warning] Force points down the potential gradient
> Where: [[#Why the field is the negative potential gradient]]
> Recorded p. 9 and 1a, ll. 121–134 give $F_x=q\,dV/dx$ and $E_x=dV/dx$. For the electric force and the usual potential, the correct signs are $F_x=-q\,dV/dx$ and $E_x=-dV/dx$. L1, l. 358 explicitly gives the negative gradient. The positive line integral on Equations Sheet A is a voltage drop along the path, $V_A-V_B$, rather than the potential increase $V_B-V_A$.

### Wire diameter used as a radius

> [!warning] The stated wire gives a larger drift speed
> Where: [[#Drift speed in the copper wire]]
> Recorded p. 21 states diameter $0.10\ \mathrm{cm}$ but quotes $0.002\ \mathrm{cm\,s^{-1}}=7.2\ \mathrm{cm\,h^{-1}}$, repeated approximately in 1b, ll. 37–39. The stated diameter gives $0.00936\ \mathrm{cm\,s^{-1}}=33.7\ \mathrm{cm\,h^{-1}}$. Using $0.10\ \mathrm{cm}$ as the radius instead gives $0.00234\ \mathrm{cm\,s^{-1}}=8.43\ \mathrm{cm\,h^{-1}}$: this explains the main factor-of-four discrepancy, with additional rounding in the printed result.

### Energy direction on the particle-comparison slide

> [!warning] Higher potential raises a positive charge's potential energy
> Where: [[#Electron and proton across the same voltage]]
> Interactive p. 22 says a positive particle moving left to right would gain kinetic energy, although its voltage arrow identifies the right plate as higher potential. That motion would increase its potential energy and reduce its kinetic energy. The proton released from the right plate accelerates left, losing potential energy and gaining kinetic energy, consistent with L1, ll. 509–526.

### Permittivity units on the Coulomb slide

> [!warning] The charge unit must be squared
> Where: [[#2. Coulomb's law and the electric field]]
> Recorded p. 6 prints $\varepsilon_0$ in $\mathrm{C\,N^{-1}\,m^{-2}}$, also read that way in 1a, l. 59. Coulomb's law requires $\mathrm{C^2\,N^{-1}\,m^{-2}}$, so that dividing $q_1q_2$ by $\varepsilon_0r^2$ gives newtons.
