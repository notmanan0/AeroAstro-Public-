---
title: "SESA2028 M3 - Corrosion, Wear and Surface Engineering"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 3
tags: [sesa2028, materials, corrosion, electrochemistry, wear, coatings]
status: lectured
coverage: "Mini-lectures ML3a, ML3b, ML3c, ML4a, ML4b and ML4c"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
next_topics: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
key_concepts: ["[[Nernst Equation and Galvanic Series]]", "[[Evans Diagram and Passivation]]", "[[Localised Corrosion]]", "[[Sensitisation and Weld Decay]]", "[[Stress Corrosion Cracking]]", "[[Corrosion Protection]]"]
sources: ["02 - Sources/Materials Lectures/Structural Performance 2025.pdf (slides 41-66)", "02 - Sources/Materials Lectures/mini lecture videos/ML3a electrochemistry fundamentals_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML3b Polarisation and Passivation_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML3c Corrosion types_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML4a Localised corrosion_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML4b Other processes and corrosion prevention_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML4c Wear and Surface Protection_default.txt"]
---

# SESA2028 M3 - Corrosion, Wear and Surface Engineering

> [!abstract] Summary
> Wet corrosion is an electrochemical cell: metal dissolves at an anode, the electrons it releases are consumed by a cathodic reaction elsewhere on the same piece of metal, and ions carry the current back through the water. Electrode potentials decide which region is the anode, Faraday's law turns the current into a rate of metal loss, and polarisation and passivation decide how large that current actually is. Localised corrosion (galvanic, pitting, crevice, intergranular, stress corrosion cracking) is the dangerous kind, up to $10^5$ times faster than uniform attack, because a large cathode drives all its current into a small anode, and the pits and cracks it leaves start fatigue. Wear is the mechanical counterpart at surfaces, and surface engineering (coatings and diffusion treatments) answers both.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks why a joint, weld or structure corroded, what form of attack to expect, what "other service problems" a humid or salty environment adds to a fatigue life, or how to protect a part.
> - **Assumptions:** a cell needs an anode, a cathode, electrical contact between them, an electrolyte and a cathodic reactant (dissolved O₂ in neutral water, H⁺ in acid).
> - **Method:** 1. Find the anode: the more active metal in the galvanic series, or the region with less oxygen. 2. Compare anode and cathode areas: small anode with large cathode is the worst case. 3. Check for a passive film and what could break it (crevice, chloride, scratch, sensitisation). 4. Link to mechanical damage: pits start fatigue, stress plus environment gives SCC. 5. Choose protection: material, coating, design detail, cathodic protection, environment.
> - **Common mistakes:** saying a paint works by sealing out oxygen (it mainly blocks the local electrical circuit); calling a sacrificial anode "anodic protection" (it is cathodic protection, ML4b, l. 81).
> - **Example:** [[#Corrosion rate from a current]]. **Exercise:** the weld-decay part of [[FEEG2005 Exam 2013-14 Solutions|2013-14 B3(iii)]].

Corrosion is the degradation of a material by its environment. In dry heat it is oxidation, covered in [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]]; with water present it is wet corrosion, an oxidation process running through an electrolyte (ML3a, ll. 14–18). It matters structurally in two ways. It removes section, so the strength and stiffness fall, and engineers working on offshore monopiles calculate the rate at which the steel piles are thinning to decide how long they will stand (ll. 18–24). And it changes the surface, leaving the small pits and grooves that start fatigue cracks. The UK spends billions of pounds a year replacing corroded equipment or maintaining against corrosion (ll. 24–26).

Corrosion works like a small battery short-circuited through the metal itself: one patch of the surface gives up metal ions and electrons; the electrons travel through the metal to another patch where something in the water, usually dissolved oxygen, takes them up; ions moving through the water complete the circuit. Anything that makes one patch different from another, a different metal, a different phase, a different oxygen supply, can set up such a cell. How fast it runs depends on how easily each half can pass current, and the rate of metal loss at the anode depends on how concentrated that current is. Most of this note is working out those three questions: where the anode is, how much current flows, and over what area.

## 1. The corrosion cell

The galvanic cell of school chemistry has a zinc electrode and a copper electrode in solutions of their own ions, joined by a wire and a permeable barrier (ML3a, ll. 28–35, 80–83). Zinc dissolves, $\mathrm{Zn\rightarrow Zn^{2+}+2e^-}$, the electrons flow to the copper, and copper plates out, $\mathrm{Cu^{2+}+2e^-\rightarrow Cu}$. The **anode** is the electrode that dissolves; the **cathode** is where electrons are consumed. In any corrosion problem the first question is which part is the anode, because that is where metal is lost (ll. 36–38).

A single piece of steel in water does the same thing with no second metal (ll. 38–57). At the anode,

$$
\mathrm{M\rightarrow M^{n+}+ne^-},
\qquad
\text{for steel }\mathrm{Fe\rightarrow Fe^{2+}+2e^-}.
$$

The electrons pass through the metal to a cathodic region, and what happens there depends on the environment. In acid, hydrogen ions are reduced and hydrogen gas bubbles off:

$$
\mathrm{2H^++2e^-\rightarrow H_2}.
$$

In neutral or basic water there are few hydrogen ions, and dissolved oxygen is reduced instead:

$$
\mathrm{O_2+2H_2O+4e^-\rightarrow4OH^-}.
$$

The hydroxyl ions migrate towards the anode and meet the $\mathrm{Fe^{2+}}$ coming the other way, so the rust precipitates between the anode and the cathode, not on top of the pit (ll. 55–57).

## 2. Electrode potentials and the galvanic series

Which region becomes the anode is decided by electrode potentials (ML3a, ll. 58–80). Each metal in a solution of its own ions has a potential, but only differences can be measured, so every half-cell is measured against a reference: the standard hydrogen electrode, a platinum surface with hydrogen gas bubbled over it in a 1 M solution of $\mathrm H^+$, defined as 0 V (ll. 61–70). Each half-reaction can run either way, dissolving or plating, depending on what it is connected to (l. 71).

![[materials_electrode_potentials.png|800]]

Noble metals such as gold sit at the top with positive potentials; connected to the hydrogen electrode they become cathodes. Active metals such as zinc, aluminium and magnesium sit at the bottom with negative potentials and become anodes (ll. 72–77). For any pair, the lower one is the anode (ll. 77–80). For zinc and copper, with standard reduction potentials

$$
E^0_{\mathrm{Zn}}=-0.76\text{ V},
\qquad
E^0_{\mathrm{Cu}}=+0.34\text{ V},
$$

zinc is the anode. The cell potential, taking cathode minus anode, is

$$
E_{cell}=E^0_{cathode}-E^0_{anode}=0.34-(-0.76)=+1.10\text{ V}.
$$

The lecture and slide 46 compute "the most negative minus the least negative", $-0.76-0.34=-1.10$ V (ll. 84–93). The magnitude is the same; the sign convention differs. With cathode minus anode, a positive $E_{cell}$ means the reaction runs on its own, because the free-energy change is

$$
\Delta G=-nFE_{cell}=-2\times96\,485\times1.10=-212\text{ kJ/mol},
$$

with $F=96\,485$ C/mol the Faraday constant. Standard potentials are for pure metals in 1 M solutions of their own ions. The **galvanic series** ranks real alloys in a real environment such as seawater, including the passive states of stainless steel and titanium; it is the table to use for design.

### The Nernst equation and concentration cells

The potential also depends on concentration (ML3a, ll. 93–100). Slide 47 gives it as $E=E^0-(0.592/n)\log C_{ion}$; the derivation shows what it should be. For the reduction $\mathrm{M^{n+}+ne^-\rightarrow M}$ the free-energy change at a general concentration is

$$
\Delta G=\Delta G^0+RT\ln\frac{1}{C_{ion}},
$$

since the solid metal has unit activity. Using $\Delta G=-nFE$ on both sides,

$$
-nFE=-nFE^0+RT\ln\frac{1}{C_{ion}}.
$$

Divide by $-nF$:

$$
E=E^0-\frac{RT}{nF}\ln\frac{1}{C_{ion}}=E^0+\frac{RT}{nF}\ln C_{ion}.
$$

At 25 °C, $RT\ln10/F=8.314\times298.15\times2.303/96\,485=0.0592$ V, so in base-10 logarithms

$$
E=E^0+\frac{0.0592}{n}\log_{10}C_{ion}.
$$

The slide's coefficient is ten times too large, and its minus sign belongs to the opposite way of writing the reaction. What matters physically is that differences in concentration alone give differences in potential, and so **concentration cells** with no second metal. Zinc in a $10^{-6}$ M solution, for instance, sits at $-0.76+0.0296\times(-6)=-0.94$ V, more active than in 1 M.

The corrosion-lab water drop is the classic case (ML3a, ll. 100–119). A clean steel sheet with a drop of water on it develops a ring of rust. Oxygen reaches the water easily at the thin edge of the drop and poorly at the thick centre. For the oxygen reaction, Nernst gives a potential that rises with oxygen concentration (by $0.0592/4=0.015$ V for each factor of ten), so the cathodic reaction is favoured at the well-aerated rim, and the centre, starved of oxygen, becomes the anode by default. Iron dissolves at the centre, hydroxyl forms at the rim, and rust precipitates in a ring where they meet. This **differential aeration** is the same mechanism that drives crevice corrosion in Section 5.

![[materials_differential_aeration.png|900]]

## 3. Corrosion rate: Faraday's law

Engineers want to know how fast metal is lost (ML3a, ll. 119–128). Faraday's law says the mass dissolved is proportional to the charge passed, $w=kIt$ (slide 48). The constant follows from counting electrons. A current $I$ for a time $t$ carries charge $It$, which is $It/F$ moles of electrons. Each metal atom releases $n$ electrons, so the moles of metal dissolved are

$$
\frac{It}{nF},
$$

and with molar mass $M$ the mass is

$$
w=\frac{MIt}{nF},
\qquad
k=\frac{M}{nF}.
$$

The rate of loss per unit area per second is therefore

$$
\frac{w}{At}=\frac{kI}{A}=k\,i,
$$

proportional to the **current density** $i=I/A$ (ll. 124–127). Dividing by the density $\rho$ turns it into a penetration rate:

$$
\frac{dx}{dt}=\frac{Mi}{nF\rho}.
$$

The same current concentrated on a small area therefore corrodes much faster than when it is spread over a large one. This is why area ratio matters so much. The current is usually limited by the cathodic reaction, which depends on how much oxygen the cathode can take up and so on its area, $I\propto A_{cathode}$, while the penetration rate goes as $I/A_{anode}$. Together,

$$
\text{penetration rate}\propto\frac{A_{cathode}}{A_{anode}},
$$

the quantitative form of the lecturer's warning about a small anode and a large cathode (ML3c, ll. 23–34).

Faraday's law gives a general rate. The current that actually flows is set by the kinetics, which is the next section (ML3a, ll. 127–130).

## 4. Polarisation and passivation

### Polarisation

When current flows, the reactions change the solution next to each electrode (ML3b, ll. 3–28). At a cathode reducing hydrogen ions, the ions are used up faster than they arrive, so a depletion zone forms; at a cathode plating zinc or copper the metal ions are depleted the same way. Since potential depends on local concentration, the cathode's potential moves more negative as the current increases, and by the same argument the anode's moves more positive. This shift is **polarisation**, and the amount by which each potential has moved is the anodic or cathodic overpotential (ll. 24–28).

Each half-reaction starts at its own equilibrium potential and can run anodically (potential rising with current) or cathodically (potential falling); which it does depends on what it is paired with (ll. 29–34). Plotting potential against the logarithm of current gives an **Evans diagram**. Where the anodic line of one reaction crosses the cathodic line of the other, the potentials are equal and the currents balance: that point gives the corrosion potential $E_{corr}$ and the corrosion current $i_{corr}$ (ll. 34–49).

![[materials_polarisation_passivation.png|900]]

Shallow lines meet at a large current; steep lines meet early, at a small one. So strong polarisation is good: it means a larger driving potential is needed to keep the cell running, and the corrosion slows down (ll. 45–48, 58–65). An aluminium–iron galvanic couple in 3 % sodium chloride shows it directly: the current density starts high and falls with time as polarisation builds up (ll. 59–63). Zinc in acid is the opposite, a large corrosion current (ll. 53–57). The rate is often limited by how fast the species needed for the cathodic reaction, usually dissolved oxygen, can reach the cathode (ll. 75–76).

> [!warning] The baked-bean tin
> The lecture argues that polarisation develops faster at higher temperature, so a tin of beans in the fridge polarises less and can corrode faster than one at room temperature (ML3b, ll. 66–74). Treat this as a special case. Reaction rates normally rise with temperature, and the usual rule is that corrosion speeds up when it is warmer; a cold, open, acidic tin is helped mainly by the greater amount of oxygen that dissolves in cold liquid. The safe exam point is the slide's: the rate depends on polarisation and on the supply of the cathodic reactant.

### Passivation

Stainless steels are stainless because of passivation (ML3b, ll. 77–101). Some metals (chromium-rich steels, aluminium, titanium) can form a thin, very protective oxide once their potential is pushed high enough. The anodic curve then has an unusual shape: an active region where current rises with potential, a nose, then a jump back to a very low current, the passive region, where the film holds the dissolution rate down, and at still higher potential a transpassive region where current rises again (ll. 78–87).

What happens depends on where the cathodic curve cuts the anodic one (ll. 88–101, slide 52). A cathodic reaction with a low starting potential (1) crosses in the active region: a large current and fast corrosion. A more oxidising cathodic reaction (2) crosses in the passive region: a stable oxide forms, and if it is scratched it reforms almost immediately. An even more strongly oxidising reaction (3) crosses in the transpassive region: the oxide may still be there, but a scratch is not repaired and the metal corrodes actively. The slide sums it up as safe and unsafe conditions: in reducing conditions the oxide is not repaired and the surface goes active, which is why stainless steel can fail where oxygen is excluded.

## 5. Types of corrosion

Uniform corrosion, such as the general attack on a steel structure in the tidal zone and under salt spray, is the type covered so far (ML3c, ll. 1–13). It is measurable, it can be predicted from a dissolution rate, and it is preventable. The real danger is localised corrosion, where rates can be many orders of magnitude higher, up to 100,000 times those of uniform attack on slide 54 (ll. 14–17). Two things control it: whatever creates a local difference in electrode potential, either a difference of material or a difference of concentration, and the relative sizes of the anode and cathode, because the cathode controls the reaction rate (ll. 18–34).

### Galvanic corrosion

Two different metals in electrical contact with an electrolyte form a galvanic cell (ML3c, ll. 36–46). Bolt dissimilar metals together, leave them out in the rain, and the more active one corrodes, as with a zinc fastener in steel, which dissolves rapidly and loses its function. The same effect can be used deliberately (ll. 46–55). A zinc coating on steel, galvanising, protects partly as a barrier, but mainly because zinc is anodic to iron: if the coating is scratched and a small area of steel is exposed, the steel becomes the cathode and is protected, while the surrounding zinc corrodes instead.

### Pitting

Inside a microstructure, particular phases can be locally anodic or cathodic to the surrounding matrix; in aluminium alloys some second-phase particles are cathodic to the aluminium and some anodic (ML3c, ll. 56–64). If a small particle is anodic, the matrix round it is a large cathode and all its current is concentrated into the particle, which dissolves rapidly to form a pit (ll. 65–70). The chemistry inside a pit becomes unusual and complex, and whether it stays active or repassivates is a research area in its own right (ll. 70–73). Pits are not always the simple shapes they look from the surface: they can be narrow and deep, wide and shallow, elliptical, undercut, or run sideways along grain boundaries (ll. 73–78), and each is a stress concentration from which fatigue cracks grow (ll. 79–82), like the thumbnail cracks on the dinghy mast in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]].

### Crevice corrosion

When a bolt is removed from a plate, the metal that was under its head is often badly corroded while the surface outside is not (ML4a, ll. 8–15). Crevice corrosion is localised, rapid and dangerous because it is hidden. It happens under bolt heads, under debris or leaves, in gaps between assembled parts, anywhere a thin layer of water is cut off from the air (ll. 16–27).

The mechanism is differential aeration again (ll. 31–47, slide 59). At first the water in the gap holds the same oxygen as the water outside, and corrosion is general, with small anodes and cathodes spread at random. But the micro-cathodes inside the gap use up their oxygen, and little more can diffuse in, so the water there becomes stagnant and de-aerated. The gap is now a low-oxygen anode and the free surface a large, well-aerated cathode: the worst area ratio. Metal ions released in the gap react to form corrosion products that clog it, cutting off oxygen even more, and the trapped solution can become acidic, so the attack accelerates.

### Intergranular corrosion and weld decay

Stainless steel resists corrosion because, with more than about 12 % chromium in solution, it forms a coherent chromium-rich oxide (ML4a, ll. 48–52, 66–69). If it is held at an intermediate temperature, as in the heat-affected zone of a weld that cools slowly, chromium carbides ($\mathrm{Cr_{23}C_6}$) precipitate on the grain boundaries (ll. 52–59). To form them, chromium diffuses in from the surrounding metal, so a thin zone along each boundary is left with too little chromium to form a protective film (ll. 59–62, 69–71). The steel is now **sensitised**: the depleted boundaries are anodes, the passive grain centres are cathodes, and a tiny cell attacks the boundaries rapidly (ll. 62–66). This is **weld decay**, and it is one reason stainless steels are awkward to weld.

![[materials_weld_decay_cr_profile.png|900]]

There are three ways to prevent it (ll. 71–81, slide 61). Cool quickly through the dangerous range, so the carbides have no time to form. Reduce the carbon content, so little carbide can form at all; grades such as 316L ("L" for low carbon) are used for welding. Or add an element that forms a more stable carbide than chromium does, titanium or niobium, so the carbon is tied up and the chromium stays in solution. The steel grades and their alloying are in [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying|M7]].

### Cavitation and erosion

Corrosion often works together with mechanical damage (ML4b, ll. 1–38). Cavitation happens in fast-flowing liquid round, for example, a ship's propeller: vapour bubbles form and then implode near the surface, each collapse jetting liquid at the metal and giving a pressure pulse (ll. 2–14). The repeated pulses break up the protective oxide film and load the surface cyclically, so cavitation combines accelerated corrosion with fatigue and erosion (ll. 13–18).

Erosion is caused by particles carried in a fluid, which may be a gas or a liquid, as in a pipeline carrying slurry (ll. 20–38). It depends on the flow medium, the velocity and the angle of impact. Particles striking at 90° deform the surface plastically, rather like shot peening, or chip a brittle one; at shallow angles they cut and abrade it away (ll. 23–30). Pipework design therefore needs the fluid mechanics of how particles are carried and where they strike, and erosion combined with corrosion can give very rapid failure because each removes the protection against the other (ll. 31–38).

### Stress corrosion cracking

Stress corrosion cracking (SCC) produces branched cracks, like tree roots, that grow at a constant load in a corrosive environment (ML4b, ll. 39–48). It needs three things at once: a susceptible material, a specific corrosive environment and a tensile stress. The attack is usually intergranular and catastrophic, with very little warning, because the cracks grow at stresses far lower than the fracture toughness would predict, as little as 1 % of the $K_{Ic}$-based value (ll. 45–50, slide 64). The process is a balance at the crack tip: the environment controls how the protective film forms and what chemistry develops in the crack, the stress controls how often the film ruptures, and the microstructure controls where it happens (ll. 51–62). Where SCC is a known problem a threshold $K_{ISCC}$ can be measured, below which it does not occur (ll. 57–58).

## 6. Preventing corrosion

The electrochemistry can be turned to advantage (ML4b, ll. 64–82). A buried steel pipeline cannot be dug up and repainted regularly, but it can be connected to a block of magnesium. Magnesium has a much more negative electrode potential than iron, so it becomes the anode and corrodes in place of the pipe, which is forced to be the cathode: a **sacrificial anode** (ll. 66–75, 93–95). Alternatively, an underwater tank can be connected through a power supply to a piece of scrap metal, and an imposed current forces the tank to be the cathode: **impressed-current** protection (ll. 75–80). Both are **cathodic protection**, because both make the protected structure the cathode.

Sealing a system also works (ll. 83–93). If a bolted joint is sealed so that no fresh oxygen can reach the water inside, a little corrosion uses up the oxygen and then stops, just as the water in a closed central-heating system does not keep corroding the radiators.

The general rules come back to the anode (ll. 97–118, slides 65–66): know where it is and why; avoid a small anode with a large cathode; detail the design to remove crevices, sharp edges and water traps, with drainage holes and no dirt or leaf traps; prefer welded to bolted joints where crevices would form; avoid dissimilar metals in contact. Paints and similar coatings do not mainly work by sealing out oxygen; they work as electrical insulators that stop the local currents the cells need (ll. 113–118). Metals such as stainless steel and titanium protect themselves with coherent oxides, which return in M8. Slide 66 groups the options as materials selection (a non-metallic material may avoid the problem altogether), coatings (metallic such as zinc, inorganic, or organic such as paint), design (avoid excessive stress, dissimilar-metal contact and crevices; exclude air), cathodic or anodic protection, and environmental control: temperature, flow velocity, oxygen level, ion concentrations, inhibitors and regular cleaning (ll. 122–134).

## 7. Wear

Wear, or tribology, is the mechanical damage of surfaces that rub or press against each other (ML4c, ll. 1–30). A hard particle ploughing through a softer metal scratches it. Two rough surfaces touch only at their asperities, where the local pressures and temperatures are very high; the contacts can weld, oxidise and break off as hard debris that then rolls between the surfaces. A roller pressing on a surface repeatedly creates oscillating contact stresses below it, which grow fatigue cracks until fragments come away (ll. 4–14). The stress state at an asperity contact is complex (ll. 17–19). In reciprocating machinery the result is loss of fit, cyclic loads that start fatigue, or seizure (ll. 20–23).

The lecture names three kinds (ll. 24–49). In **abrasive wear** a harder material cuts a softer one, as an unintended machining process; it is two-body wear when the hard surface itself cuts, and three-body wear when a loose hard particle is trapped between the surfaces. In **adhesive wear** the surfaces are pressed together so hard that they micro-weld or interdiffuse at the contacts and then tear apart, transferring material or forming particles. In **sliding wear** the surfaces deform plastically into lips, debris collects between them, and the oscillating stresses grow fatigue cracks. Wear can be studied from scratches and debris at the mesoscale, through local fracture, plasticity, phase changes and tribofilms (oxide films formed under pressure) a short distance below the surface, down to single asperities and surface chemistry at the atomic scale; Southampton's national tribology centre works across these scales (ll. 50–84).

## 8. Surface engineering

Because corrosion and wear both start at the surface, the answer is often to engineer the surface separately from the bulk (ML4c, ll. 85–127). The methods shown were:

- hot-dip galvanising: dipping steel in molten zinc, for sacrificial corrosion protection (ll. 92–94);
- chemical vapour deposition of very different materials, such as a hard, wear-resistant diamond-like carbon film for reciprocating parts (ll. 95–97);
- electroplating, running the corrosion cell backwards to make the part a cathode and plate on, for example, chromium (ll. 98–99, 123–124);
- thermal spraying of ceramic particles, which arrive semi-molten at high speed and splat onto a grit-blasted surface to build up a hard, wear-resistant layer (ll. 100–106);
- a thermal barrier coating system on a nickel superalloy turbine blade: an aluminide bond coat, a thermally grown oxide and a columnar ceramic top coat put down by physical vapour deposition, described in [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]] (ll. 107–112);
- anodising, which thickens the protective oxide on aluminium and titanium alloys by driving the oxidation electrochemically (ll. 114–115);
- diffusion treatments: carburising puts carbon into the surface of a steel to give a hard, wear-resistant high-carbon case over a tougher low-carbon core, and nitriding forms a hard, gold-coloured nitride layer (ll. 116–119);
- weld overlay, depositing a different material on a substrate much as additive manufacturing does (l. 122).

## Worked examples

All numbers recomputed in Python. None of these was set in the mini-lectures, which deferred worked exam questions to the tutorials (ML4a, ll. 5–8).

### Corrosion rate from a current

Steel corroding uniformly at a current density of 1 μA/cm². With $M=55.85$ g/mol, $n=2$ and $\rho=7.87$ g/cm³,

$$
\frac{dx}{dt}=\frac{Mi}{nF\rho}=\frac{55.85\times10^{-6}}{2\times96\,485\times7.87}=3.68\times10^{-11}\text{ cm/s}.
$$

A year is $3.156\times10^7$ s, so

$$
\frac{dx}{dt}=3.68\times10^{-11}\times3.156\times10^{7}=1.16\times10^{-3}\text{ cm/yr}=0.012\text{ mm/yr},
$$

a slow, predictable uniform rate. If the same total current, set by a cathode of fixed size, is concentrated on an anode one hundredth of the area, the local rate becomes 1.2 mm per year, through a typical aircraft skin in a year or two.

### Sizing a sacrificial anode

A buried pipe needs a protection current of 0.1 A. Over one year the anode passes $0.1\times3.156\times10^7=3.16\times10^6$ C. The mass consumed is $MIt/nF$:

$$
m_{\mathrm{Mg}}=\frac{24.31\times3.16\times10^6}{2\times96\,485}=398\text{ g},
\qquad
m_{\mathrm{Zn}}=\frac{65.38\times3.16\times10^6}{2\times96\,485}=1.07\text{ kg}.
$$

Magnesium does the job with less than half the mass of zinc, and its more negative potential gives a larger driving voltage, which is why the lecture's pipeline uses it.

### Is it spontaneous?

For iron in acid, $\mathrm{Fe+2H^+\rightarrow Fe^{2+}+H_2}$, the cell potential is $0-(-0.44)=+0.44$ V, so $\Delta G=-2\times96\,485\times0.44=-84.9$ kJ/mol and iron dissolves. For copper in acid it is $0-0.34=-0.34$ V and $\Delta G=+65.6$ kJ/mol: copper does not dissolve in a non-oxidising acid.

## Transcript slips

> [!warning] Mini-lectures ML3a–ML4c
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML3a, l. 41 | "M goes to MN plus plus 10 N electrons" | $\mathrm{M\rightarrow M^{n+}+ne^-}$ |
> | ML3a, l. 93; slide 46 | cell potential "minus 1.1 volts" | by the usual convention $E_{cell}=E_{cathode}-E_{anode}=+1.10$ V; the lecture's "most negative minus least negative" gives the same magnitude with the opposite sign |
> | ML3a, l. 95 | "different levels of iron" | different levels of ions |
> | Slide 47 | $E=E^0-(0.592/n)\log C_{ion}$ | $E=E^0+(0.0592/n)\log_{10}C_{ion}$ for a reduction potential at 25 °C (Section 2) |
> | ML3a, l. 111 | "the cathodic reaction is basically promoted here" (at the centre of the drop) | promoted at the rim; the centre becomes the anode because the cathodic reaction is not promoted there (l. 109) |
> | ML3b, l. 72 | "you can etch up with faster corrosion" | you can end up with faster corrosion |
> | ML3c, l. 54 | "sil substrate" | steel substrate |
> | ML3c, l. 70 | "very fast the solution of the pit" | very fast dissolution of the pit |
> | ML3c, l. 80 | "microstretch" | microstructure |
> | ML4a, ll. 28, 34 | "amnes", "anusen cathodes" | anodes, anodes and cathodes |
> | ML4a, l. 70 | "c23 c6" | $\mathrm{Cr_{23}C_6}$ |
> | ML4a, ll. 71, 83 | "well decay" | weld decay |
> | ML4a, l. 74 | "stained steel" | stainless steel |
> | ML4a, l. 80 | "316 lc" | 316L |
> | ML4b, l. 46 | "fralic process" | brittle process |
> | ML4b, ll. 50, 53 | "crack dip", "cracked it" | crack tip |
> | ML4b, l. 72 | "allowing the the iron flow" | allowing the ion flow |
> | ML4b, l. 74 | "magneem" | magnesium |
> | ML4b, l. 81; slide 65 | the magnesium sacrificial anode is "anodic protection" | it is cathodic protection, as is the impressed current; anodic protection is a different method that raises a passivating metal's potential into its passive range |
> | ML4b, l. 92 | "preliminary creation" | preliminary corrosion |
> | ML4b, l. 124 | "more like to crow" | more likely to corrode |
> | ML4c, l. 8 | "local failure defamation processes" | deformation |
> | ML4c, l. 11 | "underwear fatigue" | wear (contact) fatigue |
> | ML4c, l. 39 | "micro-well" | micro-weld |
> | ML4c, ll. 100–101 | high-velocity oxy-fuel coating uses "a plasma gun" | HVOF uses a combustion gun; plasma spraying is a separate thermal-spray process. Both fire semi-molten particles at the surface |
> | ML4c, l. 76 | "Aeromecanship students" | aero, mechanical and ship-science students |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]] · Next: [[SESA2028 M4 - Polymer Matrix Composites]]
- Concepts: [[Nernst Equation and Galvanic Series]] · [[Evans Diagram and Passivation]] · [[Localised Corrosion]] · [[Sensitisation and Weld Decay]] · [[Stress Corrosion Cracking]] · [[Corrosion Protection]]
- Related: [[Stainless Steel Classes]] · [[Thermal Barrier Coatings]] · [[Oxidation Rate Laws]] · [[Shot Peening]]
- Past papers: [[FEEG2005 Exam 2013-14 Solutions]] (B1(iii) humid and salty service, B3(iii) intergranular attack) · [[FEEG2005 Exam 2017-18 Solutions]] (A2 brewery vessel) · [[FEEG2005 Exam 2021-22 Solutions]] (MQ1(c) welding austenitic stainless)

## Sources

- Structural Performance 2025 slides 41–66
- Mini-lecture transcripts ML3a (electrochemistry fundamentals), ML3b (polarisation and passivation), ML3c (corrosion types), ML4a (localised corrosion), ML4b (other processes and prevention), ML4c (wear and surface protection)
- Numbers in the worked examples recomputed in Python

## Self-study tasks

No problems were set in these mini-lectures; worked exam questions were moved into the tutorials that year (ML4a, ll. 5–8). ML3c (ll. 79–82) asks why a particular part of a microstructure becomes the anode, and ML4c (l. 129) points to the first two materials tutorials. The corrosion lab's water-drop experiment is described in ML3a (ll. 100–104).

### Core

- [ ] Explain the rust ring in the corrosion-lab water drop (ML3a, ll. 100–119). → [[#The Nernst equation and concentration cells]]
- [ ] Why does part of a microstructure become an anode, and why does a pit start fatigue? (ML3c, ll. 79–82). → [[#Pitting]]
- [ ] Explain crevice corrosion and weld decay, with ways to prevent each (ML4a). → [[#Crevice corrosion]] · [[#Intergranular corrosion and weld decay]]
- [ ] Corrosion rate and the area-ratio effect (suggested, not lecturer-set). → [[#Corrosion rate from a current]]

### Further practice

- [ ] Use an Evans diagram to explain why polarisation is good and why a passive metal can be safe or unsafe (ML3b). → [[#4. Polarisation and passivation]]
- [ ] Compare sacrificial-anode and impressed-current protection and size an anode (ML4b, ll. 64–82; sizing suggested, not lecturer-set). → [[#6. Preventing corrosion]] · [[#Sizing a sacrificial anode]]
- [ ] Past paper: 2013-14 B1(iii) and B3(iii). → [[FEEG2005 Exam 2013-14 Solutions]]
