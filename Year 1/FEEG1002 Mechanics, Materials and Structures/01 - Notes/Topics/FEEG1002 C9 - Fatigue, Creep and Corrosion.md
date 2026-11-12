---
title: "FEEG1002 C9 - Fatigue, Creep and Corrosion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 24
tags: [feeg1002, materials, fatigue, s-n-curve, paris-law, creep, corrosion, galvanic]
aliases: ["Materials Lectures 13 and 14", "Failure of Materials 3 and 4", "Fatigue", "Creep and corrosion"]
date: 2026-11-05
status: lectured
coverage: "Materials L13 (19 Nov 2024, ll. 1–831): cyclic loading, stress range and amplitude, initiation at slip steps, rotating-bending tests and S–N curves, fatigue limit, life and strength, initiation and propagation, high- and low-cycle fatigue, factors affecting fatigue, damage-tolerant design with ΔK and the Paris law, the Southwest 1380 fan-blade case study. Materials L14 (25 Nov 2024, ll. 1–744): creep and its three stages, the steady-state creep rate equation, designing against creep and turbine-blade grain structures; corrosion as anodic and cathodic reactions, the standard emf and galvanic series, eight forms of corrosion, passivation, sacrificial anodes, impressed current, design rules and the metal-on-metal hip case study. Slide decks 14 and 15 in full."
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]", "[[FEEG1002 C3 - Diffusion]]"]
next_topics: ["[[FEEG1002 C10 - Polymers - Structure and Mechanics]]"]
key_concepts: ["[[S-N Curves and Paris Law]]", "[[Creep]]", "[[Galvanic Corrosion and Passivation]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 14 - Failure of Materials 3 - Fatigue.pdf", "02 - Sources/Materials/Lectures/Lecture 15 - Failure of Materials 4 - Creep and Corrosion.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 13 - Materials Fatigue.txt", "02 - Sources/Lectures/FEEG1002 Lecture 14 - Materials Creep and corrosion.txt", "02 - Sources/Materials/Tutorials/Tutorial Sheet 04 - Failure of Materials.pdf"]
---

# FEEG1002 C9 - Fatigue, Creep and Corrosion

> [!abstract] Summary
> Three ways components fail in service at stresses below those that would break them in a single load. Fatigue, behind about 90 % of metallic service failures, is the growth of a crack under cyclic stress: S–N curves of polished specimens rank materials and give the fatigue limit, life and strength, while damage-tolerant design assumes a crack is present and integrates the Paris law $da/dN=A(\Delta K)^m$ to find how many cycles it takes to reach the critical size. Creep is slow, diffusion-controlled deformation under constant load above about 0.3–0.4 $T_m$, with a steady-state rate $\dot\varepsilon_s=K_2\sigma^n\exp(-Q_c/RT)$. Corrosion is electrochemical: the metal with the more negative electrode potential is the anode and dissolves, and it is controlled by passive oxide films, sacrificial anodes, impressed current and careful design.

> [!summary]- Exam use: quick path
> - **Use it when:** you are asked to read a fatigue limit, life or strength from an S–N curve, find a stress range, amplitude or $\Delta K$, estimate a fatigue life with the Paris law, recognise the stages of creep, calculate a steady-state creep rate at new conditions, or say which metal in a couple corrodes and how to protect it.
> - **Assumptions:** constant-amplitude loading with $\sigma_{min}$ (and $K_{min}$) taken as zero if compressive; constant $Y$ in the Paris integration; $T$ in kelvin in the creep equation; standard emf series for pure metals in standard solutions, galvanic series for real alloys in seawater.
> - **Method:** 1. $\Delta\sigma=\sigma_{max}-\sigma_{min}$, $\sigma_a=\Delta\sigma/2$. 2. $\Delta K=Y\Delta\sigma\sqrt{\pi a}$; fast fracture when $K_{max}=K_{IC}$, giving $a_c$. 3. Integrate $dN=da/[A(Y\Delta\sigma\sqrt{\pi a})^m]$ from $a_0$ to $a_c$. 4. Creep: take ratios of $\dot\varepsilon=K_2\sigma^n e^{-Q_c/RT}$ so $K_2$ cancels. 5. Corrosion: more negative potential is the anode; cell voltage $=E_{cathode}-E_{anode}$.
> - **Common mistakes:** confusing fatigue limit (a stress with no failure) with fatigue strength (a stress at a stated number of cycles); using °C in the creep exponent.
> - **Practise:** [[#Worked example - lifing a cracked plate with the Paris law]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]] Q5–Q7

Even a component designed with its peak stress safely below yield, with a safety factor, can still fail in service (L13, ll. 1–36). It may be loaded and unloaded millions of times, held hot under load for years, or sit in seawater. None of these is captured by a single tensile test, and each needs its own picture of what the material is doing over time.

Fatigue is the most important. A wing flexes in turbulence, a ship's hull on every wave, a hip replacement at every step, a fan blade on every take-off. Each cycle may do almost nothing, but a tiny crack can start at a slip step on the surface and grow a little at every cycle until it is long enough for fast fracture ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics|C8]]). The modern way to handle this is to assume that every component already contains a crack and to predict how fast it grows, so that the part is inspected and replaced in time.

Creep and corrosion rest on familiar mechanisms: creep is diffusion ([[FEEG1002 C3 - Diffusion|C3]]) under stress at high temperature, and corrosion is the oxidation that ceramics are immune to because they are already oxides ([[FEEG1002 C1 - Atoms and Bonding#6. Bonding explains the three material classes|C1]]). Both also feed fatigue, by roughening surfaces and creating pits that act as crack starters.

---

## 1. Fatigue

### Cyclic stress

**Fatigue** is failure under fluctuating stress after many cycles, even though the maximum stress is below the yield strength and the fracture stress. It is associated with about 90 % of metallic failures in service (slide "Fatigue"; L13, ll. 37–72). It is not wearing out: the part is cycled until it breaks. In a test the load is idealised as a sine wave between a maximum stress $\sigma_{max}$ and a minimum $\sigma_{min}$. The **stress range** is

$$
\Delta\sigma=\sigma_{max}-\sigma_{min}
$$

and the **stress amplitude** is half of it,

$$
\sigma_a=\frac{\Delta\sigma}{2}=\frac{\sigma_{max}-\sigma_{min}}{2}
$$

(L13, ll. 73–92).

![[m9_fatigue_cycle.png|900]]

### How a fatigue crack starts

A polished part can fail by fatigue at a stress it could carry once with no trouble, because the damage is local. In one grain, a slip system is a little better aligned than the rest and starts to operate. Dislocations run along that one slip plane and emerge at the surface, leaving a tiny step. The step is a stress concentration; more slip happens next to it, the step deepens into an intrusion, and a microcrack forms and starts to propagate (L13, ll. 93–136). This can take hundreds of thousands of cycles. The fatigue process therefore has three steps (slide "S-N Curves: Fatigue Life / Fatigue Strength"): crack initiation, taking $N_i$ cycles; crack propagation, taking $N_p$ cycles; and final fracture, which is so rapid (about one cycle) that it adds nothing to the life. The fatigue life is therefore

$$
N_f=N_i+N_p
$$

In **high-cycle fatigue**, at low stress levels, most of the life is spent in initiation: $N_i$ is long. In **low-cycle fatigue**, at higher stress levels, a crack starts quickly (or is already there) and propagation dominates: $N_p$ becomes much greater than $N_i$ (L13, ll. 266–319).

### S–N curves

Materials are ranked by their fatigue resistance in a **rotating-bending test**: a mirror-polished cylindrical specimen is rotated while it is bent, so every point on its surface goes from tension to compression and back once per revolution (slide "S-N Curves: Fatigue Characterisation"; L13, ll. 137–187). Each specimen is run to failure at a fixed stress amplitude $S$, and a series of tests at decreasing amplitudes gives the **S–N curve**: stress amplitude against the number of cycles to failure, on a logarithmic scale. The higher the amplitude, the fewer the cycles, because the crack starts sooner. A curve higher and further to the right means a better material in fatigue. A test can run for a week, and many specimens are needed because of the scatter.

![[m9_sn_curves.png|900]]

Three quantities are read from the curve, and two of them are easily confused (slides "S-N Curves: Fatigue Limit" and "Fatigue Life / Fatigue Strength"; L13, ll. 188–265):

- The **fatigue limit** is the largest fluctuating stress that will not cause failure for an essentially infinite number of cycles: the level at which the curve becomes horizontal. Only some alloys have one, notably iron (steels) and titanium alloys; for steels it is 35–60 % of the tensile strength. This is one reason titanium alloys are so valued.
- The **fatigue life** $N_f$ is the number of cycles to cause failure at a specified stress level: read across from the stress to the curve, then down.
- The **fatigue strength** is the stress level at which failure occurs for some specified number of cycles: read up from the number of cycles to the curve, then across. Alloys with no fatigue limit, such as aluminium alloys, are characterised this way, typically at $10^7$ cycles.

The fatigue limit and the fatigue strength must be kept apart; the first is a stress with no failure at all, the second a stress for a given life.

### What affects fatigue life

The S–N curve of polished specimens ranks materials, but it is not useful for finding the safe life of a real structure (slide "Fatigue Life Influencers"; L13, ll. 320–374). A real component is not a polished dog-bone specimen:

- A rough surface has many stress concentrations ready to start cracks, which reduces $N_i$ and shifts the whole S–N curve down.
- Sharp corners and other stress concentrations designed into a structure start cracks, however low the stress is elsewhere.
- Surface treatments such as case hardening (carburising, [[FEEG1002 C3 - Diffusion|C3]]) put carbon into the surface of a steel, which pins dislocations there and delays initiation.
- There is always a large scatter in $N$ at a given $S$, because every specimen differs in grain structure, orientation, hard particles and machining.

### Damage-tolerant design

Damage-tolerant design assumes that every engineering structure contains defects, intentional or unavoidable, and designs around how fast a crack grows, its **fatigue crack growth rate** $da/dN$ (slide "Damage tolerant design"; L13, ll. 375–430). The crack tip is a stress concentration described by $K$ ([[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#4. The stress intensity factor|C8]]), and under cyclic load it is the **stress intensity factor range** that matters:

$$
\Delta K=K_{max}-K_{min}
$$

Since $K=Y\sigma\sqrt{\pi a}$ at every instant,

$$
\Delta K=Y\sigma_{max}\sqrt{\pi a}-Y\sigma_{min}\sqrt{\pi a}
$$

$$
\boxed{\Delta K=Y\Delta\sigma\sqrt{\pi a}}
$$

A crack grows only while it is pulled open. When $\sigma_{min}$ is compressive, the crack faces are pressed shut and the crack does not grow during that part of the cycle (the faces, once separated, do not weld back together). So if $\sigma_{min}$ is compressive, $\sigma_{min}$ and $K_{min}$ are taken to be zero, and $\Delta K=K_{max}$ (L13, ll. 431–475). Even at a constant stress range, $\Delta K$ is not constant: the crack grows a little every cycle, so $a$, $K_{max}$ and $\Delta K$ all increase as the test goes on (L13, ll. 476–525). When $K_{max}$ reaches $K_{IC}$, the crack has reached its critical length and fast fracture follows (L13, ll. 547–562).

### The Paris law

Plotted on log–log axes, the crack growth rate $da/dN$ against $\Delta K$ has three regions (slide "Crack Propagation Rate"; L13, ll. 563–590). At low $\Delta K$ cracks grow very slowly or not at all (region I). At high $\Delta K$, as $K_{max}$ approaches $K_{IC}$, growth accelerates towards fast fracture (region III). In between, region II is a straight line:

$$
\log\frac{da}{dN}=\log A+m\log\Delta K
$$

which, taking antilogarithms, is the **Paris law**:

$$
\boxed{\frac{da}{dN}=A(\Delta K)^m}
$$

$A$ and $m$ are material constants found from crack-growth tests; $m$ is typically between 2 and 4 for metals. The law is named after the engineer Paris, not the city.

![[m9_paris_law.png|900]]

### Integrating the Paris law

The life spent growing a crack from one length to another is found by integration, which is the basis of structural lifing (slide "Crack Propagation Rate"). Substitute $\Delta K$ into the Paris law, taking $Y$ and $\Delta\sigma$ as constant:

$$
\frac{da}{dN}=A\left(Y\Delta\sigma\sqrt{\pi a}\right)^m=A\,Y^m\Delta\sigma^m\pi^{m/2}a^{m/2}
$$

Separate the variables:

$$
dN=\frac{da}{A\,Y^m\Delta\sigma^m\pi^{m/2}a^{m/2}}
$$

Integrate from the initial crack length $a_0$ (at $N=0$) to the critical length $a_c$ (at $N=N_f$); everything except $a$ is a constant:

$$
N_f=\frac{1}{A\,Y^m\Delta\sigma^m\pi^{m/2}}\int_{a_0}^{a_c}a^{-m/2}\,da
$$

For $m\neq2$ the integral is

$$
\int_{a_0}^{a_c}a^{-m/2}\,da=\left[\frac{a^{1-m/2}}{1-m/2}\right]_{a_0}^{a_c}=\frac{2}{2-m}\left(a_c^{(2-m)/2}-a_0^{(2-m)/2}\right)
$$

and reversing the order of the bracket to make the factor positive for $m>2$,

$$
\boxed{N_f=\frac{2}{(m-2)\,A\,Y^m\Delta\sigma^m\pi^{m/2}}\left(a_0^{(2-m)/2}-a_c^{(2-m)/2}\right)}
$$

with the critical crack length from fast fracture at $K_{max}=K_{IC}$:

$$
a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma_{max}}\right)^2
$$

Because $m>2$, the term in $a_0$ dominates the bracket: the life depends mostly on the size of the initial crack, and hardly at all on $K_{IC}$. A crack spends most of its life while it is small and growing slowly. This is why the inspection interval is set so that a crack missed at one inspection cannot reach the critical size before the next: let it grow to a set length, inspect at set intervals, and replace the part before failure (L13, ll. 591–632).

### Case study: Southwest Airlines Flight 1380

In April 2018 a fan blade of a CFM56-7B engine on a Boeing 737-700 broke off in flight; debris punctured the cabin and one passenger died (slides "Case Study"; L13, ll. 633–806). The blade had accumulated 67,040 flight hours and 40,569 flight cycles; the engine had been overhauled at 6,125 and 21,924 cycles, and the blades inspected visually and by fluorescent penetrant, 10,712 engine cycles before the accident. **Ratchet marks** on the fracture surface showed that the crack had started at more than one site. Six **arrest lines** (beach marks) recorded each relubrication during servicing, about 1,255 to 2,201 flight cycles apart, and the spacing between them widened as the crack grew, because $\Delta K$ rose with $a$. About 1,704 cycles after the last arrest line, $K_{max}$ reached $K_{IC}$ and the remaining section failed by fast fracture. The investigation concluded that the crack was probably not detectable by penetrant at the last overhaul, and ultrasonic inspection of the blades at every lubrication was introduced. An open crack blocks ultrasound passing through the blade, so it shows up clearly (L13, ll. 807–818).

## 2. Creep

### What creep is

**Creep** is time-dependent deformation under a constant static stress, normally at elevated temperature (slide "Creep"; L14, ll. 26–75). It matters in metals above about 0.3–0.4 of the absolute melting temperature $T_m$, and in ceramics above about 0.4–0.5 $T_m$. The reason melting temperature matters is diffusion: creep is a diffusion-controlled process, and diffusion becomes significant at a similar fraction of $T_m$ in all metals ([[FEEG1002 C3 - Diffusion|C3]]). A tungsten lamp filament sags under its own weight at its operating temperature; old lead pipes, with lead's low melting point (327 °C), sag down walls on hot days. Polymers creep near room temperature, which depends on their glass transition temperature ([[FEEG1002 C10 - Polymers - Structure and Mechanics#Creep and stress relaxation|C10]]).

### The three stages

A creep test holds a specimen at constant load and temperature and records strain against time (slide "Creep Stages"; L14, ll. 76–120). On loading there is an instantaneous elastic strain. In **primary creep** that follows, the creep rate decreases continuously, because the material strain-hardens as dislocations move. The rate then settles to a constant value in **secondary**, or **steady-state**, creep, where the strain–time curve is a straight line; the majority of the service life is spent here. In **tertiary creep** the rate accelerates as the cross-section shrinks and internal damage grows, ending in rupture.

![[m9_creep_curve.png|900]]

### Steady-state creep rate

Because most of the life is spent in secondary creep, the steady-state creep rate $\dot\varepsilon_s=\Delta\varepsilon/\Delta t$ is the key parameter for life planning (slide "Creep rate"; L14, ll. 121–205). It depends on stress and temperature as

$$
\boxed{\dot\varepsilon_s=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right)}
$$

where $K_2$ is a material constant found by experiment, $Q_c$ is the activation energy for creep, $R$ is the gas constant and $T$ is the absolute temperature, which must be in kelvin. The exponential is the same Arrhenius factor as for diffusion, because creep is diffusion-controlled. The stress exponent $n$, between about 1 and 9, depends on the mechanism: stress-induced vacancy diffusion through the grains, grain-boundary diffusion allowing grain-boundary sliding, and diffusion assisting dislocation motion. Knowing the rate and the load lets the dimensional change over time be predicted, and the part removed before it no longer fits or its stresses change. Taking ratios between two conditions cancels $K_2$:

$$
\frac{\dot\varepsilon_2}{\dot\varepsilon_1}=\left(\frac{\sigma_2}{\sigma_1}\right)^n\exp\left[-\frac{Q_c}{R}\left(\frac1{T_2}-\frac1{T_1}\right)\right]
$$

### Designing against creep

Creep resistance comes from a high melting temperature, so that the service temperature is a lower fraction of $T_m$ and the activation energy is high; a high elastic modulus, which reflects strong bonding; and large grains, which mean fewer grain boundaries to slide and fewer fast diffusion paths (L14, ll. 233–257). This is the opposite of the fine grains wanted for strength at room temperature ([[FEEG1002 C5 - Strengthening Mechanisms and Annealing#The Hall–Petch relation|C5]]).

Turbine blades show the progression (L14, ll. 258–311). A blade carries a large centrifugal tensile load from its root in hot gas. A cheap cast blade with equiaxed grains has grain boundaries in every direction and a short creep life. A **directionally solidified** blade has long columnar grains aligned with the load, so the boundaries lie along the stress and slide much less. A **single-crystal** blade, grown through a spiral grain selector so that only one grain survives, has no grain boundaries at all, and is precipitation hardened to block dislocations as well; it is the most expensive and lasts longest.

## 3. Corrosion

### Anodic and cathodic reactions

Corrosion of a metal in a wet environment is electrochemical, and needs two coupled reactions (slide "Oxidation vs. Reduction"; L14, ll. 318–348). At the **anode** the metal is oxidised: it gives up its valence electrons and goes into solution as positive ions,

$$
\mathrm{M}\rightarrow\mathrm{M}^{n+}+ne^-\qquad\text{e.g.}\qquad\mathrm{Fe}\rightarrow\mathrm{Fe}^{2+}+2e^-
$$

At the **cathode** the electrons are used up in a reduction reaction, which depends on the solution; in an acid, hydrogen is reduced,

$$
2\mathrm{H}^++2e^-\rightarrow\mathrm{H}_2
$$

The two rates must balance, because every electron released at the anode is consumed at the cathode. It is the anode that corrodes, so it is the anode to worry about.

### The standard emf series and cell voltage

Which metal of a pair becomes the anode is set by the **standard electrode potentials**, measured when each metal, in a standard solution of its own ions, is coupled to a standard hydrogen electrode (slides "Electrical Potentials", "The Standard emf Series"; L14, ll. 349–398). The more negative the potential, the more readily the metal gives up electrons, so in a couple the more negative metal is the anode and the more positive the cathode. The cell voltage is

$$
E_{cell}=E_{cathode}-E_{anode}
$$

| Couple | Potential (V) |
|---|---:|
| Cu²⁺/Cu | +0.340 |
| H⁺/H₂ | 0.000 |
| Fe²⁺/Fe | −0.440 |
| Zn²⁺/Zn | −0.763 |
| Mg²⁺/Mg | −2.38 |

For iron coupled to copper, iron is the anode and

$$
E_{cell}=0.340-(-0.440)=0.780\ \mathrm V
$$

Iron dissolves and copper is deposited. For zinc coupled to iron, zinc is now the anode. The further apart two metals are in the series, the larger the voltage and the faster the anode corrodes; very reactive metals such as sodium and magnesium sit at the negative end (L14, ll. 430–471). A lemon with zinc and copper electrodes gives about 0.9 V on a multimeter, less than the standard 1.10 V, because the acidic, sugary juice is not a standard solution. The rule of thumb is not to put dissimilar metals in contact in an electrolyte.

![[m9_emf_series.png|900]]

### The galvanic series

Real alloys in real environments do not behave exactly as the standard series says. In seawater, the chloride ions change the electrochemistry and carry charge very well, and metals that form protective oxide films behave far more nobly than their standard potential suggests. The **galvanic series** ranks real alloys in seawater, with separate active and passive entries for metals such as stainless steel (slide "The Galvanic series (Sea Water)"; L14, ll. 457–471, 596–602). Titanium is the striking case: its standard potential is very negative, yet in seawater it sits near the noble end because its oxide film makes it inert ([[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q7 - Corrosion of titanium and protecting buried steel|Tutorial 4, Q7]]).

### Eight forms of corrosion

Eight forms of corrosion are distinguished (slide "Types of Corrosion"; L14, ll. 472–542). The simplest is **uniform attack**, corrosion at about the same rate over the whole exposed surface. In **galvanic corrosion** two different metals or alloys are electrically coupled in an electrolyte, and the more anodic one corrodes.

Several forms are local cells set up on a single metal. **Crevice corrosion** occurs in crevices and other places with local depletion of oxygen: the oxygen-starved region becomes the anode and the surface outside the crevice the cathode, and attack inside is accelerated. **Pitting** is localised attack in which pits form, typically from the top of horizontal surfaces. The pit makes its own microenvironment, with the anode at the bottom and the cathode at the mouth, and it is an ideal starting point for a fatigue crack. **Intergranular corrosion** runs preferentially along grain boundaries, which are more reactive than the grain interiors, and in **selective leaching** one element or constituent of an alloy is removed preferentially.

The last two forms combine corrosion with mechanical action. **Tribocorrosion** is the combined action of chemical attack and mechanical wear. Wear strips the corrosion product (like rust wiped off a nail) and exposes fresh metal, and corrosion makes the surface easier to wear, so together they remove far more than either alone. In **stress corrosion**, cracks form and propagate from the combination of corrosion and an applied tensile stress.

### Passivation

Not all corrosion is bad (slides "Corrosion Protection: Oxide formation", "Passivated Metals"; L14, ll. 543–602). Some metals form an oxide layer that adheres well, is coherent and free of defects, and so protects the metal underneath: aluminium (alumina), chromium (Cr₂O₃) and titanium (TiO₂). The oxide is a ceramic: it does not conduct electrons, and it is a barrier to the diffusion of metal ions outwards and oxygen ions inwards, so further corrosion is stifled. This is **passivation**. Stainless steels contain at least 12 % chromium, which oxidises preferentially at the surface and produces an impervious Cr₂O₃ layer; cobalt–chromium–molybdenum hip alloys have about 26–30 % chromium for the same reason. Aluminium can be **anodised**, oxidised further electrochemically to thicken its protective layer, which can also be dyed. Rust on iron, by contrast, is porous and does not protect.

### Protecting against corrosion

Beyond choosing a passive alloy, there are four main methods (slides "Sacrificial Anodes", "Corrosion Protection"; L14, ll. 603–655). Two of them make the structure the cathode. A **sacrificial anode** is a more reactive metal deliberately coupled to the structure so that it becomes the anode and corrodes instead. Galvanised steel is coated with zinc ($-0.763$ V, against $-0.440$ V for iron), which corrodes first and protects the steel even where the coating is scratched. Zinc blocks bolted to a ship's hull below the waterline do the same, and stop working if they are painted over with antifouling. Buried pipes and tanks are protected by magnesium anodes ($-2.38$ V) buried in backfill next to them. **Impressed current** protection reaches the same result electrically: a rectifier drives a current from a separate anode (often scrap metal) through the soil to the structure, so that the structure is forced to be the cathode. It needs a power supply and maintenance.

The other two methods stop the cell from forming at all. Breaking the circuit separates dissimilar metals with insulating washers, paint or other insulation, and protective coatings, oxides or paints, keep the electrolyte off the metal and block the flow of electrons.

### Designing against corrosion

The design rules follow from the electrochemistry (slide "Summary"; L14, ll. 718–743):

- Think about where the anode is, and avoid small anodes coupled to large cathodes: the whole cathodic current is then concentrated on a small area, which corrodes rapidly.
- Anodes form where oxygen is depleted, so avoid crevices and water traps; provide drainage holes, use good detailing and avoid sharp edges.
- Welded joints are preferable to bolted joints, which have crevices; if bolting dissimilar metals, isolate them.
- Avoid bimetallic couples, and use protective coatings.

Even small differences in microstructure can set up a cell: in a forged hip stem whose grain size differed between its top and bottom, the difference was enough to drive galvanic corrosion in the body. Metal-on-metal hip implants show several of these effects at once (L14, ll. 656–717). Cobalt–chromium heads on taper stems corroded at the joint by mechanically assisted crevice corrosion: micromotion stripped the passive oxide, the low oxygen in tissue stopped it re-forming, and the crevice geometry concentrated the attack. One retrieval had lost about 8 mm³ of chromium and cobalt as ions, enough to cause a pseudotumour and destroy the surrounding tissue. Corrosion also leaves pits and grooves that act as stress concentrations for fatigue.

---

## Worked examples

### Worked example - stress range with a compressive minimum

A component is cycled between $\sigma_{max}=200$ MPa and $\sigma_{min}=-50$ MPa. Find the stress range and amplitude, and the effective stress range for crack growth.

$$
\Delta\sigma=200-(-50)=250\ \mathrm{MPa},\qquad\sigma_a=\frac{250}{2}=125\ \mathrm{MPa}
$$

These are the values for the S–N curve. For crack growth, the compressive part of the cycle closes the crack, so $\sigma_{min}$ is taken as zero and the effective range is $\Delta\sigma=200-0=200$ MPa, giving $\Delta K=K_{max}=Y\times200\sqrt{\pi a}$.

### Worked example - lifing a cracked plate with the Paris law

A large steel plate ($Y=1$) is cycled between 0 and 100 MPa. Its fracture toughness is $K_{IC}=25$ MPa√m and its Paris constants are $A=1.0\times10^{-12}$ and $m=3$ (with $\Delta K$ in MPa√m and $da/dN$ in m/cycle). Inspection can find surface cracks of 0.25 mm. Estimate the fatigue life.

The critical crack length, at $K_{max}=K_{IC}$ with $\sigma_{max}=100$ MPa:

$$
a_c=\frac1\pi\left(\frac{25}{1\times100}\right)^2=\frac{0.0625}{\pi}=0.0199\ \mathrm m
$$

about 20 mm. With $\Delta\sigma=100$ MPa, $m=3$ and $a_0=2.5\times10^{-4}$ m, the exponent $(2-m)/2=-\tfrac12$:

$$
N_f=\frac{2}{(3-2)\times10^{-12}\times1^3\times100^3\times\pi^{3/2}}\left(a_0^{-1/2}-a_c^{-1/2}\right)
$$

$$
\frac{2}{10^{-12}\times10^6\times5.568}=3.592\times10^5
$$

$$
a_0^{-1/2}-a_c^{-1/2}=(2.5\times10^{-4})^{-1/2}-(0.0199)^{-1/2}=63.25-7.09=56.16
$$

$$
N_f=3.592\times10^5\times56.16=2.02\times10^7\ \text{cycles}
$$

> [!check] Where the life goes
> A numerical integration of $da/[A(\Delta\sigma\sqrt{\pi a})^3]$ gives the same $2.02\times10^7$ cycles. Doubling the crack from 0.25 mm to 0.5 mm takes 33 % of the life, and the crack is still only 5 mm long after 87 % of the life. The growth rate rises from $2.2\times10^{-11}$ m per cycle at the start to $1.6\times10^{-8}$ m per cycle at the end, a factor of 700. Most of the life is spent with a crack too small to see, which is why the detectable size $a_0$ controls the answer and $K_{IC}$ hardly does.

### Worked example - sensitivity of creep to temperature and stress

An alloy creeps with $Q_c=280$ kJ/mol and $n=5$. By what factor does the steady-state creep rate rise if the service temperature goes up from 900 K to 950 K at the same stress, or if the stress rises by 10 % at the same temperature? If the rate at 900 K is $2\times10^{-9}$ s⁻¹ and the design allows 1 % creep strain, how long will the part last?

$$
\frac{\dot\varepsilon_{950}}{\dot\varepsilon_{900}}=\exp\left[\frac{280\,000}{8.314}\left(\frac1{900}-\frac1{950}\right)\right]=\exp(1.97)=7.2
$$

$$
\frac{\dot\varepsilon_{1.1\sigma}}{\dot\varepsilon_\sigma}=1.1^5=1.61
$$

A 50 K rise multiplies the creep rate by seven, much more than a 10 % increase in stress. Ignoring the short primary stage, the time to reach 1 % strain at $2\times10^{-9}$ s⁻¹ is

$$
t=\frac{0.01}{2\times10^{-9}}=5\times10^6\ \mathrm s=1389\ \mathrm h
$$

about 58 days of continuous running, or only about 8 days at 950 K.

### Worked example - which metal corrodes

Steel is to be protected by zinc, and a buried steel tank by magnesium. Confirm that each protective metal is the anode and find the cell voltages.

For zinc and iron, zinc ($-0.763$ V) is more negative than iron ($-0.440$ V), so zinc is the anode:

$$
E_{cell}=-0.440-(-0.763)=0.323\ \mathrm V
$$

For magnesium and iron, magnesium ($-2.38$ V) is the anode:

$$
E_{cell}=-0.440-(-2.38)=1.94\ \mathrm V
$$

In both cases the protective metal corrodes and the steel, as the cathode, is protected; magnesium drives a larger current, which suits the poorly conducting soil around a buried tank.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]] · Next: [[FEEG1002 C10 - Polymers - Structure and Mechanics]]
- Concepts: [[S-N Curves and Paris Law]] · [[Creep]] · [[Galvanic Corrosion and Passivation]] · [[Griffith Criterion and Fracture Toughness]]
- Worked sheet: [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]] (Q5–Q7) · Formula list: [[FEEG1002 Formula Sheet]]
- Year 2: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]] · [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]] · [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]] · [[Paris Law]] · [[S-N Curve and Basquin Law]] · [[Creep Curve and Mechanisms]] · [[Nernst Equation and Galvanic Series]]

## Sources

- `FEEG1002 Lecture 13 - Materials Fatigue.txt` (L13, 19 Nov 2024): motivation (ll. 1–72), stress range and amplitude (ll. 73–92), initiation (ll. 93–136), rotating bending and S–N curves (ll. 137–265), initiation and propagation, high- and low-cycle fatigue (ll. 266–319), influences (ll. 320–374), damage tolerance and ΔK (ll. 375–525), crack growth and the Paris law (ll. 526–632), Southwest 1380 (ll. 633–818), summary (ll. 819–831).
- `FEEG1002 Lecture 14 - Materials Creep and corrosion.txt` (L14, 25 Nov 2024): creep and its threshold (ll. 26–75), the three stages (ll. 76–120), the creep rate equation (ll. 121–205), designing against creep and turbine blades (ll. 206–311), anodic and cathodic reactions (ll. 318–348), potentials and cells (ll. 349–429), environment and the galvanic series (ll. 430–471), forms of corrosion (ll. 472–542), passivation (ll. 543–602), sacrificial anodes and impressed current (ll. 603–655), the hip case study (ll. 656–717), design rules (ll. 718–743).
- `Lecture 14 - Failure of Materials 3 - Fatigue.pdf` (slide deck 14) and `Lecture 15 - Failure of Materials 4 - Creep and Corrosion.pdf` (slide deck 15). Figures after Callister and Ashby and Jones.
- `Tutorial Sheet 04 - Failure of Materials.pdf`: Q5–Q7.
- The Paris-law worked example uses typical steel constants chosen for illustration; the integration is on the slide in words and is carried out here. The creep sensitivity example uses illustrative values of $Q_c$ and $n$.

## Self-study tasks

### Core

- [ ] Tutorial 4, Q5: fatigue limit, lives at 280 and 400 MPa, and fatigue strengths at 30 000 and 200 000 cycles from the S–N curve. Targets 200 MPa; about $2\times10^5$ and $1\times10^4$ cycles; about 355 and 283 MPa. → [[#S–N curves]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q5 - Reading the S–N curve]]
- [ ] Tutorial 4, Q6: why the creep rate has the form $K_2\sigma^ne^{-Q_c/RT}$, and the rate at 1123 K and 25 MPa. Target $2.3\times10^{-5}$ s⁻¹. → [[#Steady-state creep rate]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q6 - Steady-state creep]]
- [ ] Tutorial 4, Q7: why titanium is inert in seawater despite its negative potential, and how to protect a buried steel pipe and tank. → [[#Passivation]] · [[#Protecting against corrosion]] · [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q7 - Corrosion of titanium and protecting buried steel]]
- [ ] Distinguish the fatigue limit from the fatigue strength, flagged at L13, ll. 25–27. → [[#S–N curves]]
- [ ] Recognise the three stages of creep (L14, ll. 207–208) and remember that $T$ must be in kelvin (L14, ll. 156–165). → [[#The three stages]]

### Further practice

- [ ] Integrate the Paris law for a crack growing from a detectable size to the critical size, the integration described on the slide but not carried out in the lecture. → [[#Integrating the Paris law]] · [[#Worked example - lifing a cracked plate with the Paris law]]
- [ ] Use the standard emf series to pick the anode in a couple and work out the cell voltage (L14, ll. 741–743). → [[#Worked example - which metal corrodes]]

## Transcript and slide slips

> [!warning] Transcript and slide slip: endurance limit (L13, ll. 222–223; slide "Fatigue Life / Fatigue Strength")
> Where: [[#S–N curves]].
>
> The fatigue strength is said to be "sometimes … written as the endurance limit", and the slide labels it "Fatigue Strength (endurance limit)". In Callister and most texts the endurance limit is another name for the fatigue limit, the stress below which there is no failure, not for the fatigue strength at a given life. Treat "endurance limit" as meaning fatigue limit.

> [!warning] Transcript slips (L13, ll. 318, 452–453 and 577–582)
> Where: [[#How a fatigue crack starts]] · [[#Damage-tolerant design]] · [[#The Paris law]].
>
> At l. 318 the propagation-dominated case is called high-cycle fatigue; it is low-cycle fatigue (high-cycle fatigue is initiation-dominated, as the line before says). At ll. 452–453 $K_{min}$ "stops at zero" when the load goes "into tension"; it is when the load goes into compression (corrected at ll. 457–461). Region I of the crack-growth plot is called the "initiation region"; it is the near-threshold region of very slow or non-propagating growth.

> [!warning] Transcript slips (L14, ll. 11, 285–286, 306, 396–397 and 420–423)
> Where: [[#What creep is]] · [[#Designing against creep]] · [[#The standard emf series and cell voltage]].
>
> Creep is first said to start at "around half the melting point"; the slide and the rest of the lecture give 0.3–0.4 $T_m$ for metals. A slip system "at an angle 90 degrees" to the load is said not to inhibit slip; with the slip direction at 90° to the load the resolved shear stress is zero, so slip is inhibited, which is the point of orienting the grains. Blades are to be "overaged" and precipitation hardened; over-ageing lowers strength, so peak-ageing is meant. The potentials are read as "3.40" and "−4.40"; they are +0.340 V and −0.440 V, and the 0.78 V result is right. The iron-screw lemon cell is said to give a much bigger voltage than zinc–copper; by the standard series either iron couple gives less (0.78 or 0.32 V against 1.10 V), so the remark should not be relied on.
