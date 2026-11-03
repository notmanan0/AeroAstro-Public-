---
title: "SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Materials"
order: 6
tags: [sesa2028, materials, light-alloys, aluminium, magnesium, titanium, precipitation-hardening]
status: lectured
coverage: "Mini-lectures ML8a, ML8b, ML8c, ML9a, ML9b and the aluminium weld case study ML10a"
date: 2026-10-30
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 M4 - Polymer Matrix Composites]]"]
next_topics: ["[[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]"]
key_concepts: ["[[Hall-Petch Relation]]", "[[Precipitation Hardening]]", "[[Titanium Alloy Classes]]", "[[Specific Stiffness and Strength]]"]
tutorial_sheets: ["[[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]]"]
sources: ["02 - Sources/Materials Lectures/Lightweighting 2025.pdf (lecture blocks 8-10)", "02 - Sources/Materials Lectures/Lightweighting 2026 SESA2028 ML8.pptx", "02 - Sources/Materials Lectures/mini lecture videos/ML8a Intro to Light metals and Al alloy classifications_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML8b Recap of strengthening mechanisms (from Part 1)_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML8c Al alloys wrought vs cast_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML9a Other light alloys_ Be and Mg_default_a3dc4bc5.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML9b Ti alloys_default.txt", "02 - Sources/Materials Lectures/mini lecture videos/ML10a Al weld case study_default.txt"]
---

# SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium

> [!abstract] Summary
> The light metals, aluminium, magnesium, beryllium and titanium, all have about the same specific stiffness as steel except beryllium, so their value lies in density, strength, corrosion resistance and ease of manufacture. Strength in any metal comes from making dislocations hard to move: grain boundaries (Hall–Petch), solute atoms, other dislocations (work hardening) and precipitates. Aluminium alloys exploit precipitation most fully, through solution treatment, quenching and ageing to a peak, and the wrought forms are much better than castings because casting defects start cracks. Magnesium is HCP, hard to work and mostly cast; beryllium is stiff but toxic and rare; titanium alloys are classed by how much of the HCP $\alpha$ and BCC $\beta$ phases their alloying stabilises, and the same composition can be made tough or fatigue-resistant by heat treatment. Welding throws away the careful heat treatment, as the aluminium weld case study shows.

> [!summary]- Exam use: quick path
> - **Use it when:** asked how to strengthen an alloy, why wrought aluminium beats cast, how an age-hardening heat treatment works, why magnesium is hot-worked and cast, which titanium class suits a job, or what welding does to an aluminium alloy.
> - **Assumptions:** room-temperature properties; equilibrium phase diagrams for the solution and ageing temperatures; HCP and BCC slip thermally activated.
> - **Method:** 1. Name the mechanism: grain size, solid solution, work hardening, precipitates. 2. For age hardening give the three steps (solution treat, quench, age) and where peak strength comes from. 3. For a choice of alloy, compare density, strength, ductility, temperature limit and manufacture. 4. For titanium, place the alloy on the $\alpha$–$\beta$ diagram. 5. Say what processing does to the microstructure (casting defects, weld zones).
> - **Common mistakes:** saying over-ageing adds precipitates (it coarsens them, so there are fewer); calling titanium $\alpha'$ as hard as steel martensite.
> - **Example:** [[#Why the heat treatment peaks]]. **Exercise:** [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]], Q1 and Q2.

The light metals are aluminium, beryllium, magnesium and titanium (ML8a, ll. 23–24). Their densities are about 2.7, 1.85, 1.74 and 4.51 g/cm³, against 7.87 for iron (ll. 26–30). Comparing the mass of beams of equal stiffness puts them in a group well below steels and the heavier alloys (ll. 7–22). They have other attractions: coherent protective oxide films that give good corrosion resistance, especially titanium; aluminium's electrical conductivity, which lets an airframe act as a cage against lightning; and, compared with the composites of [[SESA2028 M4 - Polymer Matrix Composites|M4]] and [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]], relative ease of manufacture and a large supply chain (ll. 32–48).

The physical picture for the whole note is a dislocation trying to glide through a crystal. Plastic deformation happens one row of atomic bonds at a time as dislocations move, so a metal is strong to the extent that its microstructure gets in the way: boundaries where the lattice ends, misfitting atoms, tangles of other dislocations, and particles of a second phase. Alloying and heat treatment are ways of building those obstacles in on purpose. The crystal structure then decides how easy the metal is to shape: face-centred cubic aluminium has plenty of easy slip systems, while hexagonal magnesium and $\alpha$ titanium do not, and need heat to work.

## 1. Aluminium alloy series

Aluminium alloys are designated by their main alloying element, and engineers in industry use the numbers all the time (ML8a, ll. 49–65):

| Series | Main addition | Heat-treatable | Typical use (ML8a, ML8c) |
|---|---|---|---|
| 1xxx | none (≥ 99 % Al) | no | food and chemical plant, heat exchangers, reflectors |
| 2xxx | Cu | yes | aerospace, especially damage-tolerant structure (2024) |
| 3xxx | Mn | no | utensils, general sheet |
| 4xxx | Si | no | less used structurally |
| 5xxx | Mg | no | marine, fuel lines |
| 6xxx | Mg + Si | yes | automotive and architectural extrusions, trucks, canoes, pipelines; also castings and pistons |
| 7xxx | Zn + Mg | yes | aerospace, high strength (7075-T6 is the strongest in the lecture table) |
| 8xxx | others, including Li | yes | aerospace Al–Li, attractive for its low density |

Aerospace has driven most of this development (ll. 62–65). The temper letters record the heat treatment: T4 means solution treated and aged naturally at room temperature, T6 solution treated and artificially aged at a raised temperature (ML8c, ll. 51–52, 72–74). The lecture table is not for memorising, but it shows the pattern: a 1xxx alloy annealed is weak and ductile, 7075-T6 is strong but much less ductile, and every alloy sits somewhere on that trade-off (ML8c, ll. 32–72).

## 2. Strengthening: making life hard for dislocations

This is revision of Part 1 (ML8b, ll. 6–27). A dislocation is an extra half-plane of atoms; as it moves it breaks one row of bonds at a time, which is why plastic flow needs much less stress than shearing a perfect crystal (ll. 8–12). Each dislocation carries a strain field, compressive on one side of its slip plane and tensile on the other (ll. 37–41). Every strengthening mechanism works by making that strain field interact with something in the microstructure.

### Grain size: Hall–Petch

A grain boundary is where two crystals of different orientation meet; the lattice is disordered there, and since a dislocation only exists as a defect of the lattice, it cannot cross (ll. 28–34). Dislocations moving on one slip plane pile up against the boundary, and their stress fields add. Yield spreads to the next grain when the pile-up's concentrated stress is enough to start slip there (ll. 34–47). Smaller grains mean more boundaries and shorter pile-ups, so less stress is concentrated and a higher applied stress is needed. The result is the Hall–Petch relation (ll. 47–59):

$$
\sigma_y=\sigma_0+k\,d^{-1/2},
$$

where $\sigma_0$ is the intrinsic resistance of the lattice to dislocation motion, $d$ the grain size and $k$ a material constant. See [[Hall-Petch Relation]].

### Solid solution

A solute atom smaller than the host pulls its neighbours in; a larger one pushes them out; a small interstitial atom also distorts the lattice (ll. 60–68). A dislocation can lower the total strain energy by holding small solute atoms on its compressive side, large ones on its tensile side, and interstitials in the larger gap below its extra half-plane (ll. 69–80). Having settled there, the solute pins it, and more stress is needed to move it on. Copper, zinc, magnesium and silicon, singly or in pairs, are the solutes that define the aluminium alloy families (ll. 81–88).

### Work hardening

Once a metal yields, more stress is needed to keep dislocations moving, and if it is unloaded and reloaded it yields at the new, higher stress, though with less elongation left (ll. 96–112). Wrought alloys get some of their strength this way from rolling, forging and extrusion (ll. 89–95). The reason is that the dislocations multiply and their stress fields interact: two of the same sign repel because their fields add, two of opposite sign attract and cancel, and the result is a tangle that obstructs further glide (ll. 113–132). The lecturer's image is a dislocation party, avoiding the guests they dislike and clustering with those they like.

### Precipitation hardening

If enough copper is added to aluminium, a second phase can form, $\theta$ ($\mathrm{Al_2Cu}$) with its own crystal structure (ll. 133–150). While a precipitate is small and **coherent**, its atomic planes line up with the matrix, and a dislocation can cut through it, at the cost of extra stress because the precipitate is harder: a temporary barrier. Once it grows large and **incoherent**, the lattices no longer match and the interface behaves like an internal grain boundary, a phase boundary; the dislocation cannot cut it, so it is pinned at the particles and bows out between them (ll. 141–176). What then matters is not the total amount of precipitate but how closely spaced the particles are: the same volume fraction as many fine particles strengthens far more than as a few coarse ones (ll. 161–182).

The phase diagram is used to get a fine distribution (ll. 183–222). Take an alloy whose equilibrium room-temperature structure is $\alpha+\theta$:

1. Solution treat in the single-phase $\alpha$ field, so all the copper dissolves.
2. Quench in water, too fast for diffusion, so the copper is trapped in a supersaturated $\alpha$ that would prefer to precipitate.
3. Age at a moderate temperature in the two-phase field, around 120 °C in the lecture, so precipitates nucleate everywhere as a very fine dispersion of the metastable $\theta'$; the ageing time controls how big they grow, and the temperature is too low for them to redissolve.

![[materials_al_cu_heat_treatment.png|900]]

Strength against ageing time rises, peaks and falls (ll. 222–244). While under-aged, more and more fine precipitates form and the interparticle spacing shrinks. At peak age the distribution is optimal. Held longer, the alloy over-ages: small precipitates dissolve and feed large ones, leaving fewer, more widely spaced particles, and the strength falls. The driving force is the interface energy, derived in the worked example. See [[Precipitation Hardening]].

## 3. Aluminium alloy systems

The real microstructures are more complex than the Al–Cu picture (ML8c, ll. 1–31). A TEM image of a 7xxx alloy shows rod-like, blocky and very fine precipitates of several kinds, plus coarse precipitates on the grain boundaries, each flanked by a precipitate-free zone, because fast diffusion along the boundary drained the copper and zinc out of the adjacent metal (ll. 3–14). The 2xxx alloys are aluminium with copper as the main addition, precipitating metastable $\theta'$ that later becomes $\theta$; they are ductile, formable, lower in strength and damage tolerant, a typical aerospace family (ll. 15–21). The 7xxx alloys, zinc with magnesium, form $\eta'$, $\eta$ and T precipitates and reach the highest strengths, and the balance of precipitates also affects corrosion (ll. 22–28). The 8xxx Al–Li alloys precipitate $\delta'$ and $\delta$ and offer lower density (ll. 28–31).

## 4. Wrought against cast aluminium

Wrought alloys are cast as ingots or billets and then rolled, forged or extruded into plate, sheet, foil, tube, rod, bar and wire before use, with heat treatments in between (ML8c, ll. 75–87). Their microstructure can be tuned by how much they are deformed and recrystallised, what grain size and alignment the heat treatments give, and what precipitates and solutes they contain. Aerospace has pushed this family hardest, for a balance of strength, toughness, damage tolerance and corrosion resistance; the interaction between composite and metallic parts is now a key area (ll. 88–100).

Cast alloys are poured straight into the final shape, in a sand mould or a permanent metal die (ll. 101–137). Casting is a near-net-shape process, cheap for long runs of an intricate part such as a piston, whereas thermomechanical forming is more expensive (ll. 119–134). The sprue is tapered and the metal poured gently, because turbulence entrains oxide and slag and dissolves gas; feeders supply liquid metal as the casting contracts on solidifying (ll. 105–116). If a section freezes and chokes off the feed, the metal behind it shrinks with nothing to replace it, and large interdendritic voids form, from millimetre-scale holes in an ingot to the gaps between dendrite arms seen on fracture surfaces where they started failure (ll. 138–158).

Those defects are why cast alloys have much lower elongation than wrought ones (ll. 159–164). Castings are used where shape and tolerance matter more than strength, toughness or fatigue: housings that hold other components, pump bodies, wheels (ll. 164–176). The lecturer suggests building your own comparison tables of the two, since it is a common assessment question (ll. 176–179).

## 5. Welding aluminium: a research case study

Aluminium alloys are seldom welded, because a welding torch undoes all the careful solution treatment, quenching and ageing, yet airframes need joints, and rivet holes bring their own fatigue cracks (ML10a, ll. 7–12). A Southampton–Cranfield project studied welds in 2024 made by variable-polarity plasma-arc (VPPA) and metal inert gas (MIG) welding, with Southampton focusing on how small cracks, up to about 1 mm, start and grow through the local microstructure (ll. 12–38).

A weld has three zones (ll. 85–104). The fusion zone melted and solidified as a cast dendritic structure; solute rejected during solidification forms brittle intermetallics between the dendrites, gas that was dissolved in the liquid forms pores as it cools, and contraction leaves tensile residual stress. Next to it is a partially melted zone, where some phases melt and coarser particles and grain-boundary decoration appear. Further out is the heat-affected zone, where the parent plate's precipitates are aged, coarsened or partly redissolved. A hardness traverse shows the zones directly: the weld, a peak in the transition region, a dip, and a rise to the parent value; a model built from the phases measured by differential scanning calorimetry and electron microscopy predicted it closely (ll. 105–120).

![[materials_al_weld_hardness.png|900]]

Every weld had a shorter fatigue life than the parent plate, especially at low stress ranges (ll. 121–129). MIG welds cracked from porosity in the fusion zone; the VPPA welds cracked in the heat-affected zone instead, where the residual stress peaked (ll. 133–138). In the fusion zone, cracks started at sharp interdendritic defects and ran along the dendrite boundaries; short cracks speed up and slow down as they meet grain boundaries before settling into Paris-law growth, and nearby cracks either shield each other or coalesce, like the line of rivet cracks in the Aloha Airlines accident (ll. 139–157). A model of initiation, short-crack growth and coalescence predicted the life to a 1 mm crack, about half the total life, and matched the data once residual stress was included (ll. 158–166). The critical failure feature was finely balanced between defects under 100 µm in the fusion zone and residual-stress peaks in the heat-affected zone (ll. 177–182).

## 6. Beryllium

Beryllium is very stiff and about a third lighter than aluminium, giving a specific stiffness about six times that of steel (ML9a, ll. 3–6). It is rare because it is a niche material with a small supply chain, hard to manufacture by powder metallurgy, of poor toughness, and above all highly toxic, so health and safety adds greatly to the cost (ll. 7–18). It earns its place in space structures, where mass is at a premium and light, rigid deployable structures with good thermal stability are needed through launch and orbit (ll. 19–31). Its main uses, though, are functional: it is transparent to X-rays and slows and reflects neutrons, and it is used mostly as an addition to other alloys, such as copper–beryllium for conductivity (ll. 32–40).

## 7. Magnesium

Magnesium has the lowest density of the structural metals (ML9a, ll. 42–45). It is hexagonal close-packed: its close-packed planes stack ABAB, so the only close-packed planes are the basal planes, and these do not provide enough slip systems (ll. 46–58). Slip must also run on non-close-packed planes, which needs thermal activation, as in BCC metals. So the yield stress falls as the temperature rises, there is a ductile–brittle transition, and formability is poor; magnesium is hard to work and mostly cast (ll. 59–76). That is why magnesium is forged hot, as asked in 2024-25 MQ1(a).

Magnesium's stiffness is low, so it gives no gain in specific stiffness, nor much in specific strength or ductility, and its corrosion resistance is poor (ll. 77–81). It is used where a part must be thick but light and carries little load, a spacer or a casing (ll. 82–93). Its low melting point suits precision die casting into tool-steel dies, giving intricate thin-walled parts (ll. 106–117). The designations show the form and the alloying: mostly aluminium, manganese and zinc, with silicon, rare earths, zirconium or thorium in some grades (ll. 118–131). In the lecture's table (after the ASM handbook) the wrought alloys, extruded, strain-hardened or artificially aged, have higher yield strengths and ductilities, up to 350 MPa tensile and 285 MPa yield for an aircraft forging alloy, while the as-cast alloys, with more aluminium, have lower yield strength and much lower elongation because of casting defects (ll. 132–171). Typical parts are gearbox casings, steering wheels, road wheels and rugged laptop cases: castings where low mass is the whole point (ll. 172–181).

## 8. Titanium alloys

Titanium is understood through its phase diagram (ML9b, ll. 9–36). Pure titanium is $\alpha$ (HCP) at low temperature and $\beta$ (BCC) at high temperature. Alloying elements are classed by which phase they stabilise, and the balance of $\alpha$ and $\beta$ stabilisers places an alloy on a generic diagram with $\alpha$, $\alpha+\beta$ and $\beta$ fields. Cooled fast enough, $\beta$ can also transform without diffusion, by shear, to a metastable phase $\alpha'$; this martensitic transformation is the same kind of change met in steels in [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying|M7]] (ll. 20–36).

![[materials_ti_phase_diagram.png|850]]

The classes follow from the diagram (ll. 37–55):

- The $\alpha$ and near-$\alpha$ alloys contain $\alpha$ stabilisers such as aluminium (and oxygen, which commercially pure titanium picks up from its environment), strengthened by solid solution (ll. 56–69). They are only moderately strong, but with no precipitates to coarsen or dissolve they are thermally stable and creep well. Being HCP they are hard to form, as with magnesium (ll. 70–84). Near-$\alpha$ alloys, with a little $\beta$ (which may become $\alpha'$), are forging alloys with complex thermomechanical processing (ll. 84–89).
- The $\alpha+\beta$ alloys, with Ti-6Al-4V the most widely used since the 1960s, are used for implants, compressor blades and discs, and airframes (ll. 90–96). The same composition gives very different microstructures (ll. 96–113). Slowly cooled from the $\beta$ field, $\alpha$ forms as laths in a basket-weave pattern that deflects cracks along a tortuous path, so it is tough and damage tolerant. Annealed in the $\alpha+\beta$ field, it forms small equiaxed $\alpha$ grains that confine slip and resist crack initiation, so it is better in fatigue.
- The $\beta$ alloys are fully heat-treatable, like aluminium: solution treat in the $\beta$ field, quench, and age to precipitate $\alpha$ (ll. 114–133). They reach the highest strengths, and in the solution-treated state they are soft enough to form before ageing. But the $\beta$ stabilisers are dense, raising the density 7–10 % above $\alpha+\beta$ alloys, high alloying causes segregation in casting, and the precipitates make them less stable at high temperature (ll. 124–133, 165–171).

The lecture's property table shows the progression (ll. 134–164): commercially pure titanium, annealed, is weak but very ductile, used for shrouds, airframe skins and corrosion-resistant chemical and marine plant; an $\alpha$ alloy with aluminium and tin is much stronger, used for engine cases and rings to about 480 °C; near-$\alpha$ alloys are forged for compressor discs; Ti-6Al-4V serves implants, chemical plant and airframes; a tin-modified version raises strength further for rocket-engine cases; and a solution-treated and aged $\beta$ alloy has the highest strength, for high-strength airframe components. Plotted as fracture toughness against strength, alloy development since Ti-6-4 shows the familiar trade-off: adding alloying raises strength but cuts toughness, $\beta$-annealing in the 1980s gave a tough basket-weave structure at lower strength, and moving up and to the right at once is very hard (ll. 172–187).

Titanium's appeal is high specific strength, corrosion resistance from its very adherent oxide, biocompatibility (bone grows onto it) and being non-magnetic (ll. 188–203). It is used for hip, dental and spinal implants, Formula One rocker arms, 3D-printed bicycles, hollow wide-chord fan blades made by superplastic forming, and anodised jewellery, whose colours come from controlling the oxide thickness (ll. 193–214). See [[Titanium Alloy Classes]].

## Worked examples

All numbers recomputed in Python. The mini-lectures set no calculations; these check claims made in them.

### Why the heat treatment peaks

Take a fixed volume $V$ of precipitate per unit volume of alloy, divided into $N$ spheres of radius $r$. The volume fixes the number:

$$
N\cdot\frac43\pi r^3=V
\quad\Longrightarrow\quad
N=\frac{3V}{4\pi r^3}.
$$

The total interface area is

$$
A=N\cdot4\pi r^2=\frac{3V}{4\pi r^3}\cdot4\pi r^2=\frac{3V}{r}.
$$

So the interface area, and the interface energy stored with it, falls as $1/r$: growing the same precipitate from 5 nm to 50 nm cuts the interface area tenfold. Given time at temperature, diffusion lets the alloy lower its energy that way, which is over-ageing (ML8b, ll. 234–244). The same arithmetic, with $N\propto r^{-3}$, shows the particles become far fewer and further apart, which is why the strength falls.

### Specific stiffness of the light metals

With $E$ in GPa and $\rho$ in g/cm³: steel $210/7.87=26.7$, aluminium $70/2.70=25.9$, magnesium $45/1.74=25.9$, titanium $116/4.51=25.7$, but beryllium $300/1.85=162$, which is $162/26.7=6.1$ times steel, matching ML9a (l. 6). Beryllium is $1-1.85/2.70=31$ % lighter than aluminium, the "third" of l. 5. Every other light metal is no stiffer per unit mass than steel; their case rests on strength, density and processing.

### Grain refinement in magnesium

Illustrative values, not lecturer-set: for a magnesium alloy with $\sigma_0\approx10$ MPa and $k\approx0.28$ MPa√m, refining the grain size from 50 μm to 10 μm raises the yield stress from

$$
10+\frac{0.28}{\sqrt{50\times10^{-6}}}=49.6\text{ MPa}
\quad\text{to}\quad
10+\frac{0.28}{\sqrt{10\times10^{-6}}}=98.5\text{ MPa}.
$$

HCP metals have large Hall–Petch constants, so grain control through hot working and recrystallisation is especially effective for them (2024-25 MQ1(b)).

## Transcript slips

> [!warning] Mini-lectures ML8a–ML10a
> | Where | Transcript says | Correct |
> |---|---|---|
> | ML8a, l. 7 | "a book called Palmier" | Polmear, *Light Alloys* |
> | ML8a, l. 28 | "detain is at 4.51" | titanium is at 4.51 |
> | ML8b, l. 46 | "a plaster deformation" | plastic deformation |
> | ML8b, l. 56 | "grain boundaries getting away with those dislocations" | getting in the way of |
> | ML8b, l. 82 | "the alpha aluminium solute solution" | solid solution |
> | ML8b, l. 112 | "aluminium alloys actually could work easily" | work harden easily |
> | ML8b, ll. 120–122 | opposite dislocations "come together … and will want to move apart" | opposite-signed dislocations attract and stay together; it is like-signed ones that repel (ll. 116–119) |
> | ML8b, l. 138 | "aluminium and copper ions" | atoms |
> | ML8b, l. 232 | "into particle spacing" | interparticle spacing |
> | ML8b, l. 234 | "as we keep holding it, it's peak age" | as we keep holding it past peak, it over-ages |
> | ML8c, ll. 41–42 | "manganesium" | magnesium |
> | ML8c, l. 50 | "the ineal condition" | the annealed condition |
> | ML8c, l. 51 | "7C75" | 7075 |
> | ML8c, l. 121 | "a neonate shape manufacturing process" | near-net-shape |
> | ML8c, l. 122 | "the raw tallies" | the wrought alloys |
> | ML9a, l. 1 | "lecture 9b is going to be beryllium and magnesium" | 9a covers Be and Mg; 9b is titanium |
> | ML9a, l. 11 | "Spirillium alloys" | beryllium alloys |
> | ML9a, l. 17 | "panormentality approaches" | powder metallurgy |
> | ML9a, l. 54 | "facing a cubic" | face-centred cubic |
> | ML9a, l. 64 | "your yield stress fares with temperature" | varies with temperature |
> | ML9a, ll. 73, 75 | "rot alloys", "neonate shape" | wrought alloys, near-net-shape |
> | ML9a, ll. 109, 112 | "dyes" | dies |
> | ML9b, ll. 4, 14 | "mic structure" | microstructure |
> | ML9b, l. 57 | aluminium "or oxygen, will tend to be substitutional solutes" | aluminium is substitutional; oxygen is an interstitial solute in titanium |
> | ML9b, l. 86 | "if we could it rapidly enough" | if we cool it rapidly enough |
> | ML9b, l. 144 | "solar solution strengthening" | solid solution strengthening |
> | ML9b, l. 175 | "kilograms per square inch" | ksi, thousands of pounds per square inch |
> | ML9b, l. 207 | "wide cord fan blades" | wide-chord |
> | ML9b, l. 210 | "the airfield that they actually want" | the aerofoil |
> | ML10a, ll. 28 | "metal inner gas welding" | metal inert gas |
> | ML10a, l. 57 | "britties" | brittle |
> | ML10a, l. 88 | "solid rejection" | solute rejection |
> | ML10a, l. 99 | "columnidendritic" | columnar dendritic |
> | ML10a, ll. 120, 163, 164, 176 | "world" | weld |
> | ML10a, ll. 127, 135, 136 | "VPA" | VPPA |
> | ML10a, ll. 177–178 | "SM performance", "wells" | S-N performance, welds |

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]] · Next: [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]
- Concepts: [[Hall-Petch Relation]] · [[Precipitation Hardening]] · [[Titanium Alloy Classes]] · [[Specific Stiffness and Strength]] · [[Ductile-Brittle Transition]]
- Related: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing#Welds|fatigue of welds]] · [[Martensite]] (compare titanium $\alpha'$) · [[SESA2028 Materials Selection and Comparison Tables]]
- Tutorial: [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]] · past papers: [[FEEG2005 Exam 2013-14 Solutions]] (B2(i)–(iii)) · [[FEEG2005 Exam 2022-23 Solutions]] (MQ2(i)) · [[FEEG2005 Exam 2024-25 Solutions]] (MQ1(a)–(c))

## Sources

- Lightweighting 2025 slides, lecture blocks 8–10, and the 2026 ML8 deck
- Mini-lecture transcripts ML8a (light metals and Al classification), ML8b (strengthening mechanisms), ML8c (wrought against cast Al), ML9a (Be and Mg), ML9b (Ti alloys), ML10a (Al weld case study)
- Numbers recomputed in Python

## Self-study tasks

The mini-lectures set no problems. ML8a (l. 68) and ML8b (l. 7) ask you to revise the Part 1 strengthening lectures, and ML8c (ll. 176–179) suggests building your own comparison tables of cast and wrought aluminium, since it is a common assessment question.

### Core

- [ ] Explain the four strengthening mechanisms in terms of dislocation strain fields (ML8b, ll. 6–182). → [[#2. Strengthening: making life hard for dislocations]]
- [ ] Describe the three-step age-hardening treatment and the shape of the ageing curve (ML8b, ll. 183–244). → [[#Precipitation hardening]] · [[#Why the heat treatment peaks]]
- [ ] Build a comparison table of cast and wrought aluminium (ML8c, ll. 176–179). → [[#4. Wrought against cast aluminium]]
- [ ] MT4 Q1 (raising the specific properties of Al) and Q2 (titanium classes). → [[SESA2028 Materials Tutorial MT4 - Alloy Design Solutions]]

### Further practice

- [ ] Explain why magnesium is mostly cast and is worked hot (ML9a, ll. 46–76; 2024-25 MQ1(a)). → [[#7. Magnesium]]
- [ ] Explain how the same Ti-6Al-4V can be made tough or fatigue-resistant (ML9b, ll. 90–113). → [[#8. Titanium alloys]]
- [ ] Explain why the VPPA and MIG welds cracked in different places (ML10a, ll. 121–182). → [[#5. Welding aluminium: a research case study]]
