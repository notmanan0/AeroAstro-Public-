---
title: "FEEG1004 B1 - Semiconductors and Diodes"
module: "FEEG1004 Electronics"
type: topic
stream: "Part B: Electronics"
order: 1
tags: [feeg1004, electronics, semiconductors, band-theory, doping, pn-junction, diode, zener]
aliases: ["EL1 semiconductors", "Band theory", "P-N junction", "Diode characteristic"]
date: 2026-09-27
status: lectured
coverage: "Electronics Intro (6 Nov 2020) ll. 19–55; JKA 1a Semiconductor theory ll. 1–303; L6 (13 Nov 2024) ll. 20–125."
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 A1 - Electrostatics, Potential and Current]]", "[[FEEG1004 A3 - DC Circuit Laws - Ohm, KCL, KVL and Dividers]]"]
next_topics: ["[[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]"]
key_concepts: ["[[Band Theory and Semiconductor Doping]]", "[[P-N Junction Diode]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]"]
sources:
  - "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"
  - "02 - Sources/S1 Electronics/S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf"
  - "02 - Sources/Lectures/FEEG1004 Lecture 2020-11-06.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 1a.txt"
  - "02 - Sources/Lectures/FEEG1004 Lecture 6.txt"
  - "02 - Sources/Tutorial Sheets/Tutorial Sheet 03 - Electronics A - Diodes & Transistors.pdf"
---

# FEEG1004 B1 - Semiconductors and Diodes

> [!abstract] Summary
> A semiconductor has a filled valence band separated from an empty conduction band by a narrow forbidden gap ($1.1\ \mathrm{eV}$ in silicon), so thermal excitation and controlled doping with Group V donors or Group III acceptors set its conductivity. Joining p-type and n-type silicon creates a carrier-free depletion region whose built-in field opposes diffusion and gives a forward turn-on barrier of about $0.7\ \mathrm V$ ($0.3\ \mathrm V$ in germanium). In circuit analysis a diode is replaced by an assumed state, either conducting with a fixed forward drop $V_{\mathrm{on}}$ ($0.7\ \mathrm V$, or $0\ \mathrm V$ in the zero-drop ideal model) or blocking with $I_D=0$, and the assumption is then checked against the sign of the resulting current or voltage.

> [!summary]- Exam use: quick path
> - **Use it when:** explaining semiconductor conduction, doping and p-n junction behaviour, finding diode states, currents and node voltages in DC circuits, sizing an LED current-limiting resistor, or finding the conduction angle of a sinusoidal rectifier.
> - **Assumptions:** steady temperature; negligible reverse leakage current before breakdown; piecewise-linear diode model specified by the problem ($V_{\mathrm{on}}=0\ \mathrm V$ zero-drop ideal model or $V_{\mathrm{on}}=0.7\ \mathrm V$ constant-drop silicon model, or $V_{\mathrm{on}}=2.1\ \mathrm V$ for the indicator LED).
> - **Method:** 1. Identify the specified diode model ($0\ \mathrm V$ ideal or $0.7\ \mathrm V$ constant drop) and mark anode and cathode terminals. 2. Assume each diode is either ON (conducting) or OFF (blocking). 3. Replace an ON diode with a voltage source $V_D=V_{\mathrm{on}}$ (positive at the anode) and an OFF diode with an open circuit ($I_D=0$). 4. Solve the resulting linear resistive circuit using KVL, KCL and Ohm's law. 5. Check consistency: every ON diode must carry forward current ($I_D>0$ from anode to cathode), and every OFF diode must satisfy $V_D<V_{\mathrm{on}}$; if either check fails, reverse the assumption and re-solve.
> - **Common mistakes:** forgetting to verify that assumed forward current actually flows from anode to cathode after solving KVL; treating n-type or p-type bulk silicon as having a net electrostatic charge before carrier diffusion occurs.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q1: Four ideal-diode circuits (2.5 kΩ in series, diode across the output)|Tutorial 3 Q1]]

Pure silicon is a poor conductor at room temperature because each atom shares its four outer valence electrons in covalent bonds with four neighbours, which locks almost every electron in place. Replacing a tiny fraction of the silicon atoms with Group V phosphorus adds a fifth valence electron per dopant atom that is not needed for bonding and is easily freed into the crystal as a mobile negative carrier. Replacing them with Group III boron instead leaves each dopant one electron short of completing its bonds. The resulting vacancy, a hole, moves as neighbouring valence electrons hop into it and so behaves as a positive charge carrier. Either way the doped region stays electrically neutral overall, because every dopant atom brings equal numbers of protons and electrons into the lattice.

When p-type and n-type regions are formed next to each other in a single silicon crystal, random thermal motion carries mobile electrons from the n-type side across the boundary into the p-type side, where they recombine with holes. Departing electrons leave fixed, positively charged donor ions on the n-type side, while arriving electrons create fixed, negatively charged acceptor ions on the p-type side. This thin layer, stripped of mobile carriers, is the depletion region. Its uncovered ions set up an internal electric field pointing from the n-type side to the p-type side, which pulls electrons back towards the n-type side and opposes further diffusion until drift and diffusion balance in thermal equilibrium.

An external voltage across the junction disturbs this equilibrium asymmetrically. Making the n-type cathode positive with respect to the p-type anode reinforces the internal field, pulls majority carriers away from the boundary, widens the depletion region and blocks conduction apart from a tiny thermal leakage current. Making the p-type anode positive opposes the built-in field and narrows the depletion region. Once the forward voltage exceeds the built-in potential step of about $0.7\ \mathrm V$ in silicon, carriers flood across the junction and the current rises steeply for only a small further increase in voltage.

## 1. Energy bands in conductors, insulators and semiconductors

In an isolated atom, electrons occupy discrete allowed energy levels governed by the Pauli exclusion principle. Silicon has atomic number $14$, so a neutral silicon atom has $14$ protons in its nucleus and $14$ electrons: $2$ in the innermost shell, $8$ in the second shell and $4$ in the outer valence shell, which can hold up to $8$. When many atoms are brought close together to form a crystalline solid, the overlapping orbitals of neighbouring atoms split each discrete atomic level into a dense cluster of closely spaced states called an **energy band**. Adjacent bands are separated by **forbidden energy gaps** in which no allowed electron states exist.

Electrical conduction depends on the uppermost two bands. The **valence band** contains the electrons involved in covalent bonding between atoms, and the **conduction band** contains higher-energy states in which electrons are detached from individual atoms and free to drift through the lattice under an applied field. To accelerate under an electric field and contribute to a current, an electron must gain a small amount of kinetic energy, so it needs an adjacent unoccupied state to move into.

![[ee_b1_energy_bands.png|900]]

The three classes of electronic material differ in how these two bands are filled and spaced. In a conductor (a metal), either the valence band is only partly filled or the valence and conduction bands overlap in energy. Vacant states then sit immediately above the occupied ones, so even a small applied field promotes electrons into mobile states and drives a large current. In an insulator the valence band is completely full, the conduction band is completely empty and the gap between them is wide (typically greater than $5\ \mathrm{eV}$). Thermal agitation at room temperature cannot supply enough energy to cross the gap, and the full valence band has no vacant states, so no current flows unless an extreme field causes dielectric breakdown.

A pure semiconductor looks like an insulator at absolute zero, with a full valence band and an empty conduction band, but its band gap $E_g$ is narrow ($E_g\approx 1.1\ \mathrm{eV}$ in silicon). At room temperature, random thermal vibrations give a small fraction of valence electrons enough energy to jump the gap into the conduction band. The number of thermally promoted electrons rises rapidly with temperature, so a semiconductor's conductivity increases as it gets hotter, the opposite of a metal. This temperature sensitivity underpins negative-temperature-coefficient thermistors (developed in [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]) and explains why semiconductor circuits drift with temperature.

## 2. Intrinsic conduction, holes and extrinsic doping

A pure, undoped crystal of silicon or germanium is an **intrinsic semiconductor**. When thermal energy promotes an electron from the valence band into the conduction band, that electron drifts towards the positive terminal of an applied voltage source. Its departure also leaves a vacant bonding state, a **hole**, in the valence band. Under an applied field pointing from right to left, a neighbouring valence electron to the left of the vacancy is attracted towards the positive right-hand terminal and hops into the vacant bond, shifting the vacancy one atomic site to the left. As successive valence electrons hop rightwards from bond to bond, the hole migrates leftwards towards the negative terminal and acts as a positive carrier of charge $+e$. Conduction-band electrons moving towards the positive terminal and valence-band holes moving towards the negative terminal therefore both contribute to conventional current in the same direction, from positive to negative potential.

Intrinsic thermal promotion at room temperature produces very few carriers, so pure silicon conducts poorly. To control the carrier concentration and polarity, impurity atoms are diffused into selected regions of the silicon wafer in a high-temperature furnace, through windows patterned by photolithography in a protective silicon dioxide ($\mathrm{SiO_2}$) mask. A doped semiconductor is called an **extrinsic semiconductor**.

For **n-type** doping, silicon is doped with a pentavalent Group V element such as phosphorus ($\mathrm P$) or arsenic ($\mathrm{As}$), which places five-valence-electron atoms on four-bond lattice sites. Four of the phosphorus valence electrons form covalent bonds with the four neighbouring silicon atoms. The fifth is left loosely bound in a donor energy level just below the conduction band edge, and at room temperature it is readily excited into the conduction band without creating a valence-band hole. Electrons are then the **majority carriers** and thermally generated holes the **minority carriers**. The material is called n-type because its majority carriers are negative, even though the doped crystal remains electrically neutral overall (each phosphorus atom brings $15$ protons and $15$ electrons).

For **p-type** doping, silicon is doped with a trivalent Group III element such as boron ($\mathrm B$) or gallium ($\mathrm{Ga}$). Each boron atom can complete only three of its four surrounding covalent bonds, which introduces an empty **acceptor energy level** just above the valence band edge. Valence electrons at room temperature readily jump into these acceptor sites, leaving mobile holes in the valence band without adding electrons to the conduction band. Holes are then the majority carriers and thermally excited conduction electrons the minority carriers, and again the bulk material remains electrically neutral.

## 3. The p-n junction, depletion region and bias

An n-type region and a p-type region side by side in a single continuous silicon crystal form a **p-n junction**, which is the structure of a semiconductor diode. Metal contacts (typically sputtered aluminium) on the two ends form the **anode** (p-type side) and the **cathode** (n-type side).

Immediately after the junction forms, the conduction-electron concentration is high on the n-type side and low on the p-type side, while the hole concentration is high on the p-type side and low on the n-type side. **Diffusion**, the net transport of particles from high to low concentration driven by random thermal motion, carries electrons across the boundary from n-type into p-type and holes from p-type into n-type. Electrons crossing the boundary fall from the conduction band into valence-band holes and recombine. The released energy goes either into lattice vibrations (phonons, the dominant process in an indirect-band-gap material such as silicon) or into photons of light (in direct-band-gap compound semiconductors such as gallium arsenide, $\mathrm{GaAs}$, used in light-emitting diodes).

Each donor and acceptor atom was charge-neutral to begin with, so this diffusive loss of mobile carriers uncovers fixed lattice charges on either side of the boundary. Near the boundary the n-type side loses mobile electrons and is left with uncompensated, fixed **positively charged donor ions**, while the p-type side gains electrons (filling holes) and is left with fixed **negatively charged acceptor ions**.

This carrier-free zone straddling the junction is the **depletion region**. Its positive ions on the n-type side and negative ions on the p-type side set up a built-in electric field $\mathbf E$ pointing from the n-type side to the p-type side. On the energy-band diagram, this field raises the electron energy bands on the p-type side relative to the n-type side, creating an energy hill for electrons trying to cross from n to p. The built-in field drives a **drift current** (sweeping electrons from p to n and holes from n to p) that opposes the **diffusion current**. In an open-circuit diode at thermal equilibrium, the depletion region widens until the drift current exactly cancels the diffusion current:

$$
\begin{aligned}
I_{\mathrm{diffusion}}-I_{\mathrm{drift}}&=0,\\
I_{\mathrm{diffusion}}&=I_{\mathrm{drift}}.
\end{aligned}
$$

At this equilibrium the built-in potential barrier across the depletion region is approximately $V_0\approx 0.7\ \mathrm V$ for a silicon junction and $V_0\approx 0.3\ \mathrm V$ for a germanium junction.

### Reverse bias and forward bias

An external voltage source across the diode changes the potential barrier and depletion width according to its polarity.

In **reverse bias** (anode negative, cathode positive, $V_D<0$), the positive supply terminal is connected to the n-type cathode and the negative terminal to the p-type anode. Free electrons in the n-type region are drawn away from the junction towards the positive terminal, and holes in the p-type region are drawn away towards the negative terminal. The depletion region widens, the potential barrier increases and majority-carrier diffusion across the junction is blocked. Only a tiny **reverse leakage current** flows, typically nanoamperes to a few microamperes and sensitive to temperature, as thermally generated minority carriers in or near the depletion region are swept across by the field.

In **forward bias** (anode positive, cathode negative, $V_D>0$), the positive supply terminal is connected to the p-type anode and the negative terminal to the n-type cathode. Holes in the p-type region and electrons in the n-type region are pushed towards the junction, which narrows the depletion region and lowers the barrier. Once the applied forward voltage exceeds the built-in step ($V_D\gtrsim 0.7\ \mathrm V$ in silicon), electrons are injected continuously across the narrowed depletion region into the p-type side (and holes into the n-type side), where they recombine, sustaining a large forward current around the external circuit.

In the diode circuit symbol, the triangle (arrow) points from the p-type anode to the n-type cathode (marked by the bar), which is the direction of forward **conventional current** (hole flow). Electron flow in forward bias runs the other way, from cathode to anode.

## 4. Diode voltage–current characteristic and circuit models

Define the diode voltage $V_D=V_{\mathrm{anode}}-V_{\mathrm{cathode}}$, positive in forward bias, and the diode current $I_D$, positive from anode to cathode. A plot of $I_D$ against $V_D$ is strongly non-linear and has three regions.

In the forward-bias region ($V_D>0$), the current is negligible below the threshold ($V_D<0.7\ \mathrm V$ for silicon). Above $0.7\ \mathrm V$ the current rises exponentially with voltage, and because the curve is so steep, $V_D$ stays close to $0.7\ \mathrm V$ over the normal operating range of milliamperes to tens of milliamperes. In the reverse-bias region ($-V_{\mathrm{BD}}<V_D<0$) the diode blocks majority current and passes only the microampere-or-smaller leakage current, which textbooks plot on an expanded current scale so that it is visible.

The third region is reverse breakdown ($V_D\le -V_{\mathrm{BD}}$). When the reverse voltage reaches the breakdown magnitude $V_{\mathrm{BD}}$ (typically $50\ \mathrm V$ to several hundred volts for a standard rectifier diode), the field across the depletion region becomes strong enough either to tear covalent electrons directly from their bonds (**Zener breakdown**) or to accelerate carriers into ionising collisions (**avalanche breakdown**). The reverse current then increases sharply while the voltage across the diode stays nearly constant. Heavily doping the junction during manufacture thins the depletion layer and lets the breakdown voltage be set precisely between $1.8\ \mathrm V$ and $200\ \mathrm V$. A diode engineered to operate non-destructively in reverse breakdown is a **Zener diode**. Its circuit symbol bends the ends of the cathode bar, and its use as a voltage regulator is analysed in [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]].

![[ee_b1_diode_vi.png|900]]

### Piecewise-linear circuit models and the assume–solve–check method

Solving the exponential diode equation together with Kirchhoff's laws needs iteration, so circuit analysis replaces the curved forward characteristic with one of two piecewise-linear switch models. State which model is in use before writing any circuit equations.

The **constant-drop model** ($V_{\mathrm{on}}=0.7\ \mathrm V$ for silicon) is the standard one for realistic analysis. When OFF (reverse-biased or with insufficient forward voltage), the diode is an open circuit with $I_D=0$ for any $V_D<0.7\ \mathrm V$. When ON it holds a fixed forward drop $V_D=0.7\ \mathrm V$ for any $I_D\ge 0$, or $V_D=V_{\mathrm{LED}}$ (such as $2.1\ \mathrm V$) for a light-emitting diode.

The **zero-drop ("very ideal") model** ($V_{\mathrm{on}}=0\ \mathrm V$) is used when the supply voltages are much larger than $0.7\ \mathrm V$, or when a problem explicitly specifies an ideal diode, as in Tutorial Sheet 3 Q1–Q4. When OFF the diode is an open circuit ($I_D=0$ for $V_D<0$); when ON it is a closed switch (short circuit) with $V_D=0\ \mathrm V$ for $I_D\ge 0$.

For a single diode of threshold $V_{\mathrm{on}}$ in series with a supply $V_S$ and a current-limiting resistor $R$, with the anode towards the positive supply terminal, KVL around the loop gives

$$
\begin{aligned}
V_S-I_DR-V_D&=0,\\
I_DR&=V_S-V_D.
\end{aligned}
$$

Assuming the diode is ON sets $V_D=V_{\mathrm{on}}$. Substituting this and dividing by $R$ gives the forward current:

$$
\begin{aligned}
I_DR&=V_S-V_{\mathrm{on}},\\
\boxed{I_D=\frac{V_S-V_{\mathrm{on}}}{R}}\qquad (\text{valid for }V_S>V_{\mathrm{on}}).
\end{aligned}
$$

If the calculated current satisfies $I_D>0$, the ON assumption is consistent. If $V_S<V_{\mathrm{on}}$, the formula gives $I_D<0$, which violates one-way conduction. The ON assumption is then false and the diode is OFF, with

$$
I_D=0,\qquad V_R=I_DR=0,\qquad V_D=V_S<V_{\mathrm{on}}.
$$

## Worked examples

### Four shunt-diode circuits compared under ideal and constant-drop models

Tutorial Sheet 3 Q1 has four circuits (a)–(d). Each has a DC input rail $V_S\in\{+5\ \mathrm V,-5\ \mathrm V\}$ connected through a series resistor $R=2.5\ \mathrm{k\Omega}=2500\ \Omega$ to an output terminal $V_{\mathrm{out}}$, and a diode connected vertically between the $V_{\mathrm{out}}$ node and the $0\ \mathrm V$ reference rail. In all four, the branch current $I$ is defined downwards from the $V_{\mathrm{out}}$ node through the diode to the $0\ \mathrm V$ rail. No load current is drawn from $V_{\mathrm{out}}$, so the left-to-right resistor current equals the downward diode current $I$:

$$
\begin{aligned}
V_S-IR-V_{\mathrm{out}}&=0,\\
I&=\frac{V_S-V_{\mathrm{out}}}{R}.
\end{aligned}
$$

The sheet specifies the zero-drop ideal model ($V_{\mathrm{on}}=0\ \mathrm V$), which is applied to all four cases first.

In circuit (a), $V_S=+5\ \mathrm V$ and the diode points downwards (anode at $V_{\mathrm{out}}$, cathode at $0\ \mathrm V$). The diode voltage is $V_D=V_{\mathrm{out}}-0=V_{\mathrm{out}}$ and the forward current is $I_D=I$. Assume the diode is ON, so $V_D=0\ \mathrm V$ and therefore $V_{\mathrm{out}}=0\ \mathrm V$. The KVL relation then gives

$$
\begin{aligned}
I&=\frac{5.0\ \mathrm V-0\ \mathrm V}{2500\ \Omega},\\
I&=+2.00\times 10^{-3}\ \mathrm A=+2.00\ \mathrm{mA}.
\end{aligned}
$$

Because $I_D=+2.00\ \mathrm{mA}>0$, the ON assumption holds.

In circuit (b), $V_S=+5\ \mathrm V$ and the diode points upwards (cathode at $V_{\mathrm{out}}$, anode at $0\ \mathrm V$). Here $V_D=0-V_{\mathrm{out}}=-V_{\mathrm{out}}$ and the forward (upward) current is $I_D=-I$. Assume the diode is OFF, so $I=0\ \mathrm{mA}$, and KVL gives

$$
\begin{aligned}
V_{\mathrm{out}}&=V_S-IR,\\
V_{\mathrm{out}}&=5.0\ \mathrm V-(0\ \mathrm A)(2500\ \Omega)=+5.00\ \mathrm V.
\end{aligned}
$$

Then $V_D=-5.00\ \mathrm V<0\ \mathrm V$, so the diode is reverse-biased and OFF as assumed.

In circuit (c), $V_S=-5\ \mathrm V$ and the diode points downwards (anode at $V_{\mathrm{out}}$, cathode at $0\ \mathrm V$). Assume the diode is OFF, so $I=0\ \mathrm{mA}$ and

$$
V_{\mathrm{out}}=-5.0\ \mathrm V-(0\ \mathrm A)(2500\ \Omega)=-5.00\ \mathrm V.
$$

Since $V_D=V_{\mathrm{out}}=-5.00\ \mathrm V<0\ \mathrm V$, the OFF assumption is consistent.

In circuit (d), $V_S=-5\ \mathrm V$ and the diode points upwards (cathode at $V_{\mathrm{out}}$, anode at $0\ \mathrm V$). Here $V_D=0-V_{\mathrm{out}}=-V_{\mathrm{out}}$ and the upward forward current is $I_D=-I$. Assume the diode is ON, so $V_D=0\ \mathrm V$ and $V_{\mathrm{out}}=0\ \mathrm V$. The resistor equation gives

$$
\begin{aligned}
I&=\frac{-5.0\ \mathrm V-0\ \mathrm V}{2500\ \Omega},\\
I&=-2.00\times 10^{-3}\ \mathrm A=-2.00\ \mathrm{mA}.
\end{aligned}
$$

The forward current from anode to cathode (upwards) is $I_D=-I=+2.00\ \mathrm{mA}>0$. The diode is therefore ON, and $2.00\ \mathrm{mA}$ flows upwards from the $0\ \mathrm V$ rail through the diode and leftwards into the $-5\ \mathrm V$ supply.

With the $0.7\ \mathrm V$ constant-drop silicon model instead, the conducting circuits change. In circuit (a), forward conduction holds the anode $0.7\ \mathrm V$ above the $0\ \mathrm V$ cathode, so $V_{\mathrm{out}}=+0.70\ \mathrm V$ and the downward current becomes

$$
\begin{aligned}
I&=\frac{5.0\ \mathrm V-0.70\ \mathrm V}{2500\ \Omega},\\
I&=\frac{4.30\ \mathrm V}{2500\ \Omega}=+1.72\times 10^{-3}\ \mathrm A=+1.72\ \mathrm{mA}.
\end{aligned}
$$

In circuit (d), upward forward conduction holds the cathode $0.7\ \mathrm V$ below the $0\ \mathrm V$ anode, so $V_{\mathrm{out}}=-0.70\ \mathrm V$ and the downward-defined current is

$$
\begin{aligned}
I&=\frac{-5.0\ \mathrm V-(-0.70\ \mathrm V)}{2500\ \Omega},\\
I&=\frac{-4.30\ \mathrm V}{2500\ \Omega}=-1.72\times 10^{-3}\ \mathrm A=-1.72\ \mathrm{mA}.
\end{aligned}
$$

In circuits (b) and (c), the reverse bias of $-5.00\ \mathrm V$ is still well below $+0.7\ \mathrm V$, so both diodes stay OFF with $I=0\ \mathrm{mA}$, and $V_{\mathrm{out}}$ is $+5.00\ \mathrm V$ and $-5.00\ \mathrm V$ respectively.

| Circuit | Supply $V_S$ | Diode orientation | State | $V_{\mathrm{out}}$ ($0\ \mathrm V$ model) | $I$ ($0\ \mathrm V$ model) | $V_{\mathrm{out}}$ ($0.7\ \mathrm V$ model) | $I$ ($0.7\ \mathrm V$ model) |
|---|---|---|---|---|---|---|---|
| (a) | $+5\ \mathrm V$ | Down (anode top) | ON | $0\ \mathrm V$ | $+2.00\ \mathrm{mA}$ | $+0.70\ \mathrm V$ | $+1.72\ \mathrm{mA}$ |
| (b) | $+5\ \mathrm V$ | Up (cathode top) | OFF | $+5.00\ \mathrm V$ | $0\ \mathrm{mA}$ | $+5.00\ \mathrm V$ | $0\ \mathrm{mA}$ |
| (c) | $-5\ \mathrm V$ | Down (anode top) | OFF | $-5.00\ \mathrm V$ | $0\ \mathrm{mA}$ | $-5.00\ \mathrm V$ | $0\ \mathrm{mA}$ |
| (d) | $-5\ \mathrm V$ | Up (cathode top) | ON | $0\ \mathrm V$ | $-2.00\ \mathrm{mA}$ | $-0.70\ \mathrm V$ | $-1.72\ \mathrm{mA}$ |

> [!check] Model comparison and power balance in circuit (a)
> Including the $0.7\ \mathrm V$ silicon forward drop reduces the conducting current in circuits (a) and (d) from $2.00\ \mathrm{mA}$ to $1.72\ \mathrm{mA}$, a $14.0\%$ reduction because $0.7\ \mathrm V$ is a noticeable fraction of the $5.0\ \mathrm V$ supply. In circuit (a) under the $0.7\ \mathrm V$ model, the resistor absorbs $P_R=(4.30\ \mathrm V)(1.72\ \mathrm{mA})=7.396\ \mathrm{mW}$ and the diode dissipates $P_D=(0.70\ \mathrm V)(1.72\ \mathrm{mA})=1.204\ \mathrm{mW}$. Their sum, $7.396\ \mathrm{mW}+1.204\ \mathrm{mW}=8.600\ \mathrm{mW}$, matches the source power $P_S=(5.0\ \mathrm V)(1.72\ \mathrm{mA})=8.600\ \mathrm{mW}$.

### Sizing a current-limiting resistor for an indicator LED

An indicator LED is driven from a $V_S=5.0\ \mathrm V$ digital supply rail through a series current-limiting resistor $R$ (Week 7 interactive, p. 5). An LED uses a wider-band-gap compound semiconductor to emit visible photons, so its forward drop is larger than that of a silicon signal diode. The problem specifies a constant-drop model with $V_{\mathrm{LED}}=2.1\ \mathrm V$ at a target operating current of $I=60\ \mathrm{mA}=0.060\ \mathrm A$.

With the LED forward-biased and conducting, KVL around the series loop gives

$$
\begin{aligned}
V_S-V_{\mathrm{LED}}-V_R&=0,\\
V_R&=V_S-V_{\mathrm{LED}}.
\end{aligned}
$$

Substitute the supply and LED voltages:

$$
V_R=5.0\ \mathrm V-2.1\ \mathrm V=2.9\ \mathrm V.
$$

Apply Ohm's law to the series resistor and solve for $R$:

$$
\begin{aligned}
V_R&=IR,\\
R&=\frac{V_R}{I},\\
R&=\frac{2.9\ \mathrm V}{0.060\ \mathrm A}=48.33\ \Omega.
\end{aligned}
$$

To two significant figures the required series resistance is $\boxed{R=48\ \Omega}$. Without it, connecting the steep exponential V–I characteristic of the LED straight across a source even slightly above $2.1\ \mathrm V$ would drive a current limited only by wire and contact resistance, destroying the junction.

> [!check] Power dissipation check
> At $I=0.060\ \mathrm A$, the LED absorbs $P_{\mathrm{LED}}=V_{\mathrm{LED}}I=(2.1\ \mathrm V)(0.060\ \mathrm A)=0.126\ \mathrm W$ and the series resistor dissipates $P_R=V_RI=(2.9\ \mathrm V)(0.060\ \mathrm A)=0.174\ \mathrm W$, comfortably within the rating of a standard $0.25\ \mathrm W$ axial resistor. The total, $0.126\ \mathrm W+0.174\ \mathrm W=0.300\ \mathrm W$, equals the source power $P_S=(5.0\ \mathrm V)(0.060\ \mathrm A)=0.300\ \mathrm W$.

### Conduction angle of a silicon diode under a sinusoidal input

Tutorial Sheet 3 Q5 feeds a half-wave rectifier (a single silicon diode in series with a load resistor $R_L$) with a sinusoidal input of $V_{\mathrm{p\text{-}p}}=20\ \mathrm V$ peak-to-peak, and asks for the total conduction angle per cycle under the $0.7\ \mathrm V$ constant-drop model ($V_{\mathrm{on}}=0.7\ \mathrm V$).

First convert the peak-to-peak input into its peak amplitude $V_p$:

$$
\begin{aligned}
V_p&=\frac{V_{\mathrm{p\text{-}p}}}{2},\\
V_p&=\frac{20\ \mathrm V}{2}=10.0\ \mathrm V.
\end{aligned}
$$

Writing the phase angle as $\theta=\omega t$, the input over one cycle ($0^\circ\le\theta\le 360^\circ$) is

$$
v_{\mathrm{in}}(\theta)=V_p\sin\theta=(10.0\ \mathrm V)\sin\theta.
$$

The diode conducts only while $v_{\mathrm{in}}(\theta)>0.7\ \mathrm V$. The turn-on angle $\theta_1$ in the first quadrant satisfies

$$
\begin{aligned}
V_p\sin\theta_1&=V_{\mathrm{on}},\\
(10.0\ \mathrm V)\sin\theta_1&=0.7\ \mathrm V,\\
\sin\theta_1&=\frac{0.7\ \mathrm V}{10.0\ \mathrm V}=0.0700,\\
\theta_1&=\arcsin(0.0700)=4.014^\circ.
\end{aligned}
$$

By the symmetry of $\sin\theta$ about $\theta=90^\circ$, the diode keeps conducting until $v_{\mathrm{in}}(\theta)$ falls back through $0.7\ \mathrm V$ in the second quadrant at

$$
\begin{aligned}
\theta_2&=180^\circ-\theta_1,\\
\theta_2&=180^\circ-4.014^\circ=175.986^\circ.
\end{aligned}
$$

Subtracting $\theta_1$ from $\theta_2$ gives the total conduction angle per cycle:

$$
\begin{aligned}
\Delta\theta&=\theta_2-\theta_1,\\
\Delta\theta&=180^\circ-2\theta_1,\\
\Delta\theta&=180^\circ-2(4.014^\circ)=171.97^\circ\approx\boxed{172.0^\circ}.
\end{aligned}
$$

> [!check] Limiting case of the zero-drop ideal model
> Under the zero-drop ideal model ($V_{\mathrm{on}}\to 0\ \mathrm V$), $\theta_1=\arcsin(0)=0^\circ$ and $\Delta\theta=180^\circ-0^\circ=180^\circ$, recovering the exact half-cycle conduction of an ideal switch. If the peak input amplitude were reduced towards $0.7\ \mathrm V$, $\theta_1=\arcsin(0.7/V_p)$ would approach $90^\circ$ and the conduction angle $\Delta\theta$ would shrink to $0^\circ$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Next: [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Concepts: [[Band Theory and Semiconductor Doping]] · [[P-N Junction Diode]]
- Worked problems: [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions]]

## Sources

- `S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf`, pp. 3–14 (§1.1–1.5.1: band theory, intrinsic and extrinsic semiconductors, p-n junction depletion region, forward and reverse bias, and diode V–I characteristics) and pp. 19–20 (§1.5.4: Zener breakdown).
- Electronics Intro, `FEEG1004 Lecture 2020-11-06.txt` (ll. 19–55: overview of the five-week semiconductor and digital electronics block).
- 1a Semiconductor theory, `FEEG1004 Lecture 1a.txt` (ll. 1–62: silicon shells, lattice bonding and energy bands in conductors, insulators and semiconductors; ll. 63–132: electron and hole drift, intrinsic silicon, photolithography and phosphorus/boron doping; ll. 133–224: p-n junction fabrication, diffusion vs drift, depletion region and $0.7\ \mathrm V$ silicon / $0.3\ \mathrm V$ germanium barrier; ll. 225–303: reverse and forward bias, anode/cathode symbol, V–I curve, leakage current and reverse breakdown).
- L6, `FEEG1004 Lecture 6.txt` (ll. 20–67: comparison of the $0\ \mathrm V$ "very ideal" model, the $0.7\ \mathrm V$ constant-drop model, and the real curve; ll. 68–125: $2.1\ \mathrm V$, $60\ \mathrm{mA}$ LED current-limiting resistor calculation), matching `S1-W07-EL1 Semiconductors Diodes and Limiters - Interactive.pdf`, pp. 4–5.
- `Tutorial Sheet 03 - Electronics A - Diodes & Transistors.pdf`, Q1 (four shunt-diode circuits) and Q5 (half-wave rectifier conduction angle).
- All numerical values were recomputed and verified in Python. Figures `ee_b1_energy_bands.png` and `ee_b1_diode_vi.png` are generated by `generate_electronics_figures.py` using `feeg1004_style.py`.

## Self-study tasks

### Core

- [ ] Determine the diode state, current $I$ and output voltage $V_{\mathrm{out}}$ for all four shunt-diode circuits (a)–(d) under the ideal model, and compare with the $0.7\ \mathrm V$ silicon model (Tutorial Sheet 3 Q1). → [[#Four shunt-diode circuits compared under ideal and constant-drop models]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q1: Four ideal-diode circuits (2.5 kΩ in series, diode across the output)|Tutorial 3 Q1]]
- [ ] Calculate the series resistor required to run a $2.1\ \mathrm V$ LED at $60\ \mathrm{mA}$ from a $5\ \mathrm V$ supply (L6, ll. 68–125; interactive p. 5). → [[#Sizing a current-limiting resistor for an indicator LED]]
- [ ] Calculate the conduction angle per cycle of a $0.7\ \mathrm V$ silicon diode driven by a $20\ \mathrm V$ peak-to-peak sinusoidal source (Tutorial Sheet 3 Q5). → [[#Conduction angle of a silicon diode under a sinusoidal input]] · [[FEEG1004 Tutorial 3 - Diodes and Transistors Solutions#Q5: Conduction angle of a real (0.7 V) half-wave rectifier, 20 V p-p input|Tutorial 3 Q5]]

### Further practice

- [ ] Explain why electrons and holes moving in opposite directions both contribute to conventional current in the same direction (1a, ll. 69–91). → [[#2. Intrinsic conduction, holes and extrinsic doping]]
- [ ] Explain why n-type and p-type regions are each electrically neutral before they are joined, and why the depletion region acquires positively charged ions on the n-type side and negatively charged ions on the p-type side (1a, ll. 108–126 and 160–220). → [[#3. The p-n junction, depletion region and bias]]
- [ ] Sketch the diode V–I curve showing forward turn-on, reverse leakage and reverse breakdown, and state why the reverse current and voltage axes use different scales from the forward axes (1a, ll. 278–301; Mills §1.5.1). → [[#4. Diode voltage–current characteristic and circuit models]]

## Transcript and slide slips

### Proton count of silicon in the 1a recording

> [!warning] Atomic number 14 means 14 protons, not 4 protons
> Where: [[#1. Energy bands in conductors, insulators and semiconductors]]
> The 1a transcript, ll. 4–5 says that silicon appears in 14th place in the periodic table and therefore has "four protons and 14 electrons around it". Atomic number 14 means a neutral silicon atom has 14 protons in its nucleus and 14 electrons in its shells (2 in the inner shell, 8 in the middle shell, and 4 valence electrons in the outer shell, making it a Group IV element), as shown in Mills Figure 1.2.1 (p. 3).

### Left/right slip when describing carrier concentrations in 1a

> [!warning] P-type majority carriers are on the right side of the diagram
> Where: [[#3. The p-n junction, depletion region and bias]]
> The 1a transcript, ll. 182–183 states "Because we've got more N-type carriers on the left and more P-type carriers on the left". In the diagram discussed (Mills Figure 1.4.1–1.4.2, pp. 9–10), the n-type region with excess electrons is on the left and the p-type region with excess holes is on the right, so electrons diffuse from left to right and holes diffuse from right to left.
