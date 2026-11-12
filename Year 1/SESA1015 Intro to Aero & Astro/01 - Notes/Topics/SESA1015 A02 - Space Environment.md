---
title: "SESA1015 A02 - Space Environment"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 14
tags:
  - sesa1015
  - astronautics
  - space-environment
  - radiation
  - atomic-oxygen
  - debris
aliases: ["SESA1015 Astronautics 2", "Space Environment"]
date: 2026-09-27
status: lectured
coverage: "Astronautics Part 2 (Environment), pp. 1–38: natural and induced environments; the Sun's electromagnetic and particle radiation, solar proton events and galactic cosmic rays; the upper atmosphere (layers, exospheric temperature and the solar cycle, density and scale height, constituents, atomic oxygen); the magnetosphere and Van Allen trapped radiation; natural and artificial debris; effects on design (vacuum and outgassing, microgravity, UV, ionising radiation and total dose, drag, atomic-oxygen erosion with the Kapton example). The launch environment, pp. 39–46, is in A03."
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A01 - Astronautics Foundations, Missions and Applications]]"]
next_topics: ["[[SESA1015 A03 - Launch Environment]]"]
key_concepts: ["[[Space Environment Hazards]]", "[[Exponential Atmosphere and Scale Height]]", "[[Atomic Oxygen Erosion]]", "[[Van Allen Radiation Belts]]", "[[Blackbody Radiation]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 2 - Environment.pdf"]
---

# SESA1015 A02 - Space Environment

> [!abstract] Summary
> In the Solar System the space environment is cold (2.7 K background), a hard vacuum and effectively weightless, and its main input is the Sun: about 1370 W/m² of near-black-body radiation at 1 AU, plus the solar wind, solar proton events and, from outside, galactic cosmic rays. Around the Earth the atmosphere and magnetic field add three hazards that vary strongly with altitude and the 11-year solar cycle: residual density, which causes drag and falls off as $\rho_i=\rho_{i0}e^{-(h-h_0)/H_i}$ with scale height $H_i=RT/(M_ig)$; atomic oxygen, which erodes surfaces by an amount proportional to the fluence $F_0=n_{AO}Vt$; and the Van Allen belts, which set the yearly radiation dose. Debris completes the list. Each environment maps onto a design effect, from outgassing and UV embrittlement to single-event upsets and the 19 µm of Kapton lost on a ten-day Shuttle flight.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for AO fluence or erosion depth, a radiation dose in rad or J/kg, the scale height or density ratio of an atmospheric species, the solar flux at a planet, the kinetic energy of a debris impact, or which environment causes a given failure.
> - **Assumptions:** AO: constant number density and speed over the time, surface facing the velocity vector (ram), recession proportional to fluence. Scale height: isothermal layer, constant $g$, each species in its own hydrostatic balance. Solar flux: inverse square from 1370 W/m² at 1 AU.
> - **Method:** 1. Identify the environment and the quantity asked. 2. AO: $F_0=n_{AO}Vt$ with $V=\sqrt{\mu/r}$ and $t$ in seconds, then depth = (recession per $10^{24}$ m$^{-2}$) $\times F_0/10^{24}$. 3. Dose: read rad(Si)/year at the shielding thickness, multiply by years, $100$ rad $=1$ J/kg. 4. Density: $H=RT/(Mg)$, $\rho/\rho_0=e^{-\Delta h/H}$. 5. State the design response (coating, shielding, part selection, material choice).
> - **Common mistakes:** leaving $t$ in days in $F_0=n_{AO}Vt$; treating 1 rad as 1 J/kg (it is 0.01 J/kg).
> - **Practise:** [[#Atomic-oxygen erosion of Kapton on a Shuttle flight]] · [[#Self-study tasks]]

A spacecraft meets more than one environment in its life. Before launch it is fabricated, assembled, tested and transported, and then it is launched; these are the **induced** environments, created by people and machines. Once in orbit it meets the **natural** space environment (p. 3). The launch is usually the harshest of the induced environments and is treated in [[SESA1015 A03 - Launch Environment]].

Space is sometimes pictured as empty, but a satellite in low Earth orbit flies through a thin gas of atomic oxygen at 7.7 km/s, sits in sunlight strong enough to darken glass, and is crossed every second by charged particles fast enough to flip a bit in its memory. Further out, in the radiation belts and at GEO, the particle dose rises by orders of magnitude. Some of the environment helps: there is no rain, no wind, no corrosion by water vapour and no structural weight to carry once in orbit. Whether space is hostile or friendly depends on which effect is asked about (p. 29), and the engineering task is to map each environment onto what it does to materials, electronics and people.

---

## 1. Natural and induced environments

| Phase | Environment | Type |
|---|---|---|
| fabrication, assembly, test | handling loads, contamination, test levels | induced |
| terrestrial transportation | vibration, shock, humidity | induced |
| launch | acceleration, vibration, acoustics | induced ([[SESA1015 A03 - Launch Environment]]) |
| space | vacuum, temperature, radiation, atmosphere, debris | natural |

In the Solar System as a whole, space is a vacuum with a background temperature of 2.7 K and negligible gravity far from any planet, and the main input to the environment is the Sun (pp. 4–5).

## 2. The Sun

The Sun is a sphere about 1 400 000 km in diameter powered by nuclear fusion. It emits **electromagnetic radiation** and **particle radiation** (p. 6).

### Electromagnetic radiation and the solar constant

The average energy flux at 1 AU, the **solar constant**, is $S_0=1370$ W/m² (p. 7). The output varies over an 11-year **solar cycle**. Over the ultraviolet, visible and infrared the spectrum is close to that of a black body at about 6000 K, peaking in the visible near 0.5 µm (p. 10). Both statements follow from the solar constant and the Sun's size.

The Sun radiates equally in all directions, so the whole output $L$ crosses a sphere of radius 1 AU:

$$
L=4\pi(1\ \text{AU})^2S_0
$$

$$
=4\pi\,(1.496\times10^{11})^2\times1370=3.85\times10^{26}\ \text{W}.
$$

A black body of radius $R_\odot$ at temperature $T$ radiates $L=4\pi R_\odot^2\sigma T^4$ ([[Blackbody Radiation]]). Equating and solving for $T$ with $R_\odot=0.7\times10^9$ m:

$$
T^4=\frac{L}{4\pi R_\odot^2\sigma}
$$

$$
T=\left(\frac{3.85\times10^{26}}{4\pi\,(0.7\times10^9)^2\times5.67\times10^{-8}}\right)^{1/4}=5760\ \text{K}.
$$

Wien's displacement law, $\lambda_{max}T=2898$ µm K, then puts the peak at

$$
\lambda_{max}=\frac{2898}{5760}=0.50\ \mu\text{m},
$$

in the green part of the visible band (p. 10).

![[astro_a02_solar_blackbody.png|900]]

The same inverse-square argument gives the flux at any distance $d$ from the Sun: $S=S_0\,(1\ \text{AU}/d)^2$. At Mars (1.524 AU) this is $1370/1.524^2=590$ W/m², and at Jupiter (5.2 AU) only 51 W/m², which is why outer-planet missions such as Galileo and Cassini used radioisotope power rather than solar arrays.

The variability over the solar cycle depends strongly on wavelength (p. 10): radio output changes by a factor of about 100, infrared very little, visible by less than 1%, ultraviolet by a factor of a few and X-rays by a factor of about 100. The total, dominated by the visible and infrared, therefore stays close to 1370 W/m², but the short wavelengths that heat the upper atmosphere swing widely, which drives the density changes of §3. The atmosphere absorbs most of the ultraviolet, X-ray and infrared before they reach sea level (p. 9), which is why telescopes for those bands must be in space.

### Particle radiation

The Sun also throws out a stream of protons, electrons and ions (atomic nuclei stripped of their electrons), the **solar wind**, produced by violent eruptions at its surface and in its atmosphere (p. 11). At Earth the number density is about $n\approx5\times10^6$ protons/m³ and the speed $v\approx200$ to $800$ km/s, depending on solar activity. The particle flux is $nv=1\times10^{12}$ to $4\times10^{12}$ m$^{-2}$s$^{-1}$, and the kinetic energy of a solar-wind proton at 400 km/s is

$$
E=\tfrac12m_pv^2=\tfrac12\times1.67\times10^{-27}\times(4\times10^5)^2=1.34\times10^{-16}\ \text{J}=0.84\ \text{keV}.
$$

Two other particle populations are far more energetic (p. 12). Near solar maximum, flares become more frequent and violent and can send a cloud of energetic particles towards the Earth: a **solar proton event** (SPE), or solar storm, raises the flux of protons at 1 MeV to 1 GeV for a few hours to a few days, a few times a year. **Galactic cosmic rays** (GCR) come from outside the Solar System with energies of $10^9$ to $10^{12}$ eV. An SPE proton thus carries a thousand to a million times the energy of a solar-wind proton, and a cosmic ray up to a billion times, enough to pass through any practical shielding.

## 3. The Earth's atmosphere

The Earth is protected from much of the Sun's output by two things: its atmosphere and its magnetic field (p. 13).

### Layers and the exosphere

Temperature divides the atmosphere into layers (p. 14). The troposphere extends to 6 to 20 km (lowest at the poles), the stratosphere to about 50 km, the mesosphere to 85 to 100 km and the thermosphere to 400 to 700 km; above that is the exosphere, where molecules are so sparse that they follow ballistic paths and some escape. The ionosphere, the ionised region that reflects radio waves, overlaps the thermosphere. The Space Station, the Shuttle and sounding rockets all operate in the thermosphere.

In the thermosphere the temperature rises steeply with height because the gas absorbs solar ultraviolet and X-rays, and it levels off at the **exospheric temperature** $T_\infty$ (p. 15). Since those wavelengths vary strongly over the solar cycle, so does $T_\infty$: about 700 to 800 K at solar minimum (1985) and about 1500 K at solar maximum (1990). Solar activity is tracked by the 10.7 cm radio flux $F_{10.7}$, in units of $10^{-22}$ W m$^{-2}$ Hz$^{-1}$; values of 50, 150 and 250 correspond to $T_\infty\approx671$, 1131 and 1458 K (p. 16), and $F_{10.7}$ has cycled between about 70 and 250 every 11 years since the 1950s.

### Density and the scale height

The density above a reference height $h_0$ follows from hydrostatic balance and the ideal gas law (p. 18). Above about 100 km turbulent mixing stops and each gas settles independently in the gravity field, a state called diffusive equilibrium. Take species $i$ with molar mass $M_i$, density $\rho_i$ and partial pressure $p_i$. A thin horizontal slab of thickness $dh$ and unit area must have its weight carried by the pressure difference across it:

$$
dp_i=-\rho_i g\,dh .
$$

The ideal gas law for that species, with the universal gas constant $R=8.314$ J mol$^{-1}$ K$^{-1}$, is

$$
p_i=\frac{\rho_iRT}{M_i}.
$$

For an isothermal layer ($T$ constant) differentiate:

$$
dp_i=\frac{RT}{M_i}\,d\rho_i .
$$

Substitute into the hydrostatic equation:

$$
\frac{RT}{M_i}\,d\rho_i=-\rho_ig\,dh .
$$

Separate the variables:

$$
\frac{d\rho_i}{\rho_i}=-\frac{gM_i}{RT}\,dh .
$$

Integrate from $h_0$, where $\rho_i=\rho_{i0}$, to $h$, holding $g$ constant:

$$
\ln\frac{\rho_i}{\rho_{i0}}=-\frac{gM_i}{RT}(h-h_0),
$$

$$
\rho_i=\rho_{i0}\exp\!\left[-\frac{gM_i}{RT}(h-h_0)\right],
$$

which is equation (2.1). Defining the **scale height**

$$
H_i=\frac{RT}{M_ig},
$$

the height over which the density falls by a factor $e=2.718$, gives the compact form $\rho_i=\rho_{i0}e^{-(h-h_0)/H_i}$. The total density is written $\rho=\rho_0e^{-(h-h_0)/H}$ (2.2) with a single effective $H$, which works over a limited height range where one species dominates.

Since $H_i\propto T/M_i$, light species thin out slowly and heavy ones quickly. At $T=1000$ K and $g=9.0$ m/s² (the value near 300 km):

| Species | $M_i$ (kg/mol) | $H_i=RT/(M_ig)$ |
|---|---|---|
| O$_2$ | 0.032 | 28.9 km |
| N$_2$ | 0.028 | 33.0 km |
| O | 0.016 | 57.7 km |
| He | 0.004 | 230.9 km |
| H | 0.001 | 923.8 km |

The ratio of two species therefore changes exponentially with height. For atomic oxygen against nitrogen,

$$
\frac{n_O}{n_{N_2}}=\left(\frac{n_O}{n_{N_2}}\right)_0\exp\!\left[(h-h_0)\left(\frac{1}{H_{N_2}}-\frac{1}{H_O}\right)\right],
$$

and $1/33.0-1/57.7=0.0130$ km$^{-1}$, so every 77 km of height multiplies the ratio by $e$. Starting from $n_{N_2}=3\times10^{17}$ and $n_O=1.2\times10^{17}$ m$^{-3}$ at 120 km, atomic oxygen overtakes nitrogen at

$$
h=120+\frac{\ln(3/1.2)}{0.0130}=191\ \text{km},
$$

and helium overtakes oxygen near 760 km by the same calculation. This matches the measured profiles (p. 19): atomic oxygen is the main constituent from about 200 km to several hundred kilometres, with helium and then hydrogen above.

![[astro_a02_scale_heights.png|900]]

The scale height also explains the solar-cycle effect on density (p. 17). A hotter thermosphere has larger $H$, so the same base density decays more slowly with height and the density at a given orbital altitude rises. Between solar minimum ($F_{10.7}=75$) and solar maximum ($F_{10.7}=225$) the density at 400 to 1000 km changes by roughly an order of magnitude, at 400 km from a few times $10^{-13}$ to a few times $10^{-12}$ kg/m³. Drag and orbital lifetime in LEO change by the same factor.

### Orbital drag

A satellite of mass $m$, drag coefficient $C_D$ and frontal area $A$ moving at $v$ feels a drag force

$$
D=\tfrac12\rho v^2C_DA .
$$

At 400 km near solar maximum take $\rho=3\times10^{-12}$ kg/m³; with $v=7669$ m/s, $C_D=2.2$ and $A=1$ m²,

$$
D=\tfrac12\times3\times10^{-12}\times7669^2\times2.2\times1=1.94\times10^{-4}\ \text{N},
$$

a fifth of a millinewton. Small as it is, it acts continuously and lowers the orbit. The orbital energy of a circular orbit of radius $a$ is $E=-\mu m/(2a)$, and drag removes energy at the rate $Dv$:

$$
\frac{dE}{dt}=-Dv .
$$

Differentiate the energy with respect to time:

$$
\frac{dE}{dt}=\frac{\mu m}{2a^2}\frac{da}{dt}.
$$

Equate the two and solve for $da/dt$:

$$
\frac{da}{dt}=-\frac{2a^2Dv}{\mu m}.
$$

Substitute $D=\tfrac12\rho v^2C_DA$:

$$
\frac{da}{dt}=-\frac{\rho C_DA}{m}\frac{a^2v^3}{\mu}.
$$

Use $v^2=\mu/a$, so $v^3=\mu^{3/2}a^{-3/2}$:

$$
\frac{da}{dt}=-\frac{\rho C_DA}{m}\sqrt{\mu a}.
$$

Multiply by the period $T=2\pi\sqrt{a^3/\mu}$ for the loss per orbit:

$$
\Delta a_{rev}=-2\pi\frac{C_DA}{m}\rho a^2 .
$$

For a 1000 kg satellite with the values above and $a=6.778\times10^6$ m,

$$
\Delta a_{rev}=-2\pi\times\frac{2.2\times1}{1000}\times3\times10^{-12}\times(6.778\times10^6)^2=-1.9\ \text{m},
$$

or about 30 m per day at 15.6 orbits per day. The ratio $m/(C_DA)$, the ballistic coefficient, sets the lifetime: a light, large spacecraft decays fastest. Lower down the decay accelerates sharply because $\rho$ grows exponentially. The same calculation is used for mission design in [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]].

> [!tip] Drag speeds a satellite up
> Since $v=\sqrt{\mu/a}$, a falling $a$ means a rising $v$. Drag removes total energy, but the potential energy falls twice as fast as the kinetic energy rises, so a decaying satellite moves faster as it spirals in.

### Atomic oxygen

Above about 200 km atomic oxygen (AO) is the dominant species (p. 19). It forms when solar ultraviolet splits O$_2$, and at these densities the atoms rarely meet to recombine. Its number density at a given height rises with solar activity: from p. 20, roughly $10^{14}$ to $10^{16}$ m$^{-3}$ at 300 km between low and high activity, falling with height. AO is chemically reactive, and a spacecraft at 7.7 km/s hits each atom with about 5 eV of kinetic energy ($\tfrac12\times16\times1.66\times10^{-27}\times7700^2=7.9\times10^{-19}$ J), enough to break bonds in polymers (design effects in §6).

## 4. The magnetic field and trapped radiation

The Earth's magnetic field is approximately that of a dipole, like a bar magnet aligned roughly with the spin axis (p. 21). The solar wind compresses it on the day side, forming a **bow shock** where the supersonic wind first meets the field, and stretches it into a long **magnetotail** on the night side; the region the field controls is the **magnetosphere** (pp. 22–23). Its boundary moves with the strength of the solar wind, and sudden changes are called magnetic storms.

A charged particle in a magnetic field spirals around the field line. As it moves towards a pole the field strengthens and the spiral tightens until the particle turns back at a **mirror point**; it then bounces between northern and southern mirror points while drifting around the Earth (p. 24). Particles entering near the magnetic poles become trapped in this way, forming the **Van Allen trapped radiation belts** (p. 23).

![[astro_a02_van_allen_belts.png|900]]

There are two belts (p. 25). The inner belt, centred about 1.5 Earth radii from the centre, holds high-energy protons ($E\geq100$ MeV) with fluxes up to about $10^3$ cm$^{-2}$s$^{-1}$. The outer belt, from about 3 to 7 Earth radii, holds electrons ($E>0.5$ MeV) with fluxes up to about $10^6$ to $10^8$ cm$^{-2}$s$^{-1}$. A circular orbit at 2000 km ($r=1.31R_E$) just reaches the lower edge of the inner belt, which is one reason the top of LEO is drawn there; GEO, at $6.61R_E$, sits in the outer electron belt. Highly eccentric orbits cross both belts twice per revolution. This geometry sets the yearly dose (§6).

## 5. Debris

Debris divides into natural and artificial (p. 26). Natural debris is the meteoroids the Earth sweeps up along its orbit, about 100 tonnes per day entering the atmosphere. Artificial debris is human-made: dead satellites, spent upper stages, fragments from explosions and collisions. In 2009 NASA counted 3371 operational satellites and 11 492 debris objects of 10 cm or larger in Earth orbit (pp. 26–27), and the number has grown since.

The danger comes from the speed. Two objects in LEO at 400 km each move at 7.67 km/s, so a head-on encounter closes at up to $2\times7.67=15.3$ km/s, and a typical impact is around 10 km/s. A 1 cm aluminium sphere ($\rho=2700$ kg/m³) has mass

$$
m=2700\times\tfrac43\pi(0.005)^3=1.41\times10^{-3}\ \text{kg},
$$

and at 10 km/s carries

$$
E=\tfrac12\times1.41\times10^{-3}\times(10^4)^2=70.7\ \text{kJ},
$$

the kinetic energy of a one-tonne car at $\sqrt{2\times70\,700/1000}=11.9$ m/s (43 km/h), delivered by a marble. Objects of 10 cm and above can be tracked and avoided; smaller ones must be shielded against or accepted as a risk ([[Space Debris Mitigation]], SESA2024).

## 6. Effects on design and on people

The environments sort into hostile and friendly (p. 29). The hostile ones are the high vacuum, particle radiation, high-energy electromagnetic radiation, atomic oxygen in the Earth's atmosphere, and debris. The friendly ones are the absence of water vapour and rain, the absence of wind, the clean environment and the zero effective gravity, which lets very light structures work once deployed.

### Vacuum

In hard vacuum some materials evaporate, which is called **outgassing**: resins, adhesives, lubricants and some metals (p. 30). The rate rises steeply with temperature:

| Material | Temperature for 0.1 µm/yr | Temperature for 1 mm/yr |
|---|---|---|
| Cadmium | 38 °C | 122 °C |
| Magnesium | 110 °C | 233 °C |
| Gold | 660 °C | 950 °C |
| Titanium | 920 °C | 1250 °C |

At normal spacecraft temperatures the loss of material is far too slow to threaten structural integrity; the problem is contamination. Outgassed vapour condenses on the coldest surfaces nearby, which are often optics, sensors and radiators, and a film a fraction of a micrometre thick can ruin an optical surface or change a radiator's emittance. Cadmium is the warning case, outgassing measurably at 38 °C, and it is not used on spacecraft. Materials are screened for outgassing and baked out before flight.

### Microgravity

An orbiting spacecraft is in free fall, so everything on board floats. Gravity has not gone: at 400 km it is $g_0(R_E/r)^2=9.81\times(6378/6778)^2=8.68$ m/s², 88% of its surface value. Free fall affects design in several ways (p. 31). Structures need not carry their own weight in orbit, so they can be lighter, but then mechanisms such as solar-array and antenna deployments cannot easily be tested on the ground, where they must be supported by rigs that offload gravity. Without gravity there is no buoyancy, so there is no natural convection and heat moves only by conduction and radiation. Liquid propellant does not settle over the tank outlet, so propellant management devices or small settling burns are needed. Crews suffer physiological effects such as bone and muscle loss.

### Solar electromagnetic radiation

Solar ultraviolet changes the optical and electrical properties of materials, embrittles polymers and darkens solar-array cover glass and adhesives (p. 32). Darkening reduces the light reaching the cells and so the power, and changes in a surface's absorptance shift the spacecraft's temperature ([[Spacecraft Thermal Balance Equation]]).

### Ionising particle radiation and total dose

Trapped particles, solar protons and cosmic rays ionise material as they pass through it (p. 33). They degrade semiconductor devices, including solar cells, whose output falls with accumulated dose; a single energetic particle can deposit enough charge in a memory cell to flip it, a **single event upset** (SEU) that corrupts software or data; charge building up on surfaces causes **spacecraft charging** and discharges; and crews receive a biological dose.

Accumulated damage scales with the **total dose**, the energy deposited per unit mass. The standard unit is the rad(Si), the dose that deposits 100 erg in each gram of silicon (p. 34). With $1\ \text{erg}=10^{-7}$ J,

$$
1\ \text{rad}=\frac{100\times10^{-7}\ \text{J}}{10^{-3}\ \text{kg}}=0.01\ \text{J/kg},
$$

so 100 rad $=1$ J/kg, which is 1 gray (Gy), the SI unit.

![[astro_a02_dose_shielding.png|900]]

The yearly dose depends on the orbit and on the thickness of aluminium in front of the component (p. 34). With about 5 mm of aluminium the yearly doses read from the curves are roughly:

| Orbit | Dose behind 5 mm Al | In J/kg |
|---|---|---|
| GEO | $6\times10^3$ rad/yr | 60 Gy/yr |
| highly elliptic | $1\times10^4$ rad/yr | 100 Gy/yr |
| 700 km polar | $6\times10^2$ rad/yr | 6 Gy/yr |
| 500 km, 28° | 20 rad/yr | 0.2 Gy/yr |

The ordering follows the belt geometry of §4. The low-inclination LEO orbit stays under the belts almost all the time; the polar orbit at 700 km passes through the "horns" of the outer belt that dip towards the poles; GEO sits in the outer electron belt; and the highly elliptic orbit crosses both. The curves also show diminishing returns. For GEO, going from 1 mm to 5 mm of aluminium cuts the dose by a factor of about 250 because the low-energy electrons are stopped, but going from 5 mm to 12.5 mm gains only about a factor of 12, because the remaining dose comes from energetic protons and from the X-rays (bremsstrahlung) that stopped electrons emit. Every millimetre of aluminium costs 2.7 kg per square metre of box wall, so beyond a few millimetres it is cheaper to buy radiation-tolerant parts.

### The Earth's atmosphere

The residual atmosphere causes aerodynamic drag (§3), lift and heating, the last being severe during re-entry, and erosion by atomic oxygen (p. 35).

The amount of erosion depends on how many atoms strike unit area of the surface, the **AO fluence** $F_0$ (p. 36). A ram-facing surface of area $A$ moving at speed $V$ through gas of number density $n_{AO}$ sweeps out a volume $AVt$ in time $t$ and so meets every atom in it:

$$
N=n_{AO}\times AVt .
$$

Dividing by the area gives the fluence, equation (2.3):

$$
F_0=\frac{N}{A}=n_{AO}Vt\qquad(\text{m}^{-2}).
$$

The thermal speed of the oxygen atoms, about 1 km/s at 1000 K, is small next to the 7.7 km/s orbital speed and is neglected.

![[astro_a02_atomic_oxygen.png|900]]

Measured surface recession is proportional to fluence and is quoted per $10^{24}$ atoms/m² (p. 37):

| Material | Recession per $10^{24}$ atoms/m² |
|---|---|
| Kapton | 2.8 µm |
| Teflon | 0.029 µm |
| Aluminium | 0.00035 µm |
| Silver | 9.8 µm |

Kapton, a polyimide film widely used in multilayer insulation blankets, erodes fast; Teflon about a hundred times more slowly; aluminium hardly at all, because a thin oxide layer forms and protects the metal beneath. Silver is the worst, because its oxide flakes off and exposes fresh metal, which matters for silver-plated solar-cell interconnects. Protective coatings such as silicon oxide work only while they are continuous, since AO undercuts any pinhole or crack.

## Worked examples

### Atomic-oxygen erosion of Kapton on a Shuttle flight

Estimate the depth of erosion of Kapton for a typical Space Shuttle mission of 10 days during solar maximum (pp. 35–36).

A typical Shuttle altitude is 300 km, where the AO number density at solar maximum is about $n_{AO}=10^{15}$ m$^{-3}$. The orbital speed there is $V=\sqrt{398\,600/6678}=7.73$ km/s; take $7.7\times10^3$ m/s. The duration is $t=10\times86\,400=8.64\times10^5$ s. The fluence is

$$
F_0=n_{AO}Vt
$$

$$
=(10^{15})(7.7\times10^3)(8.64\times10^5)
$$

$$
=6.65\times10^{24}\ \text{atoms/m}^2 .
$$

At 2.8 µm per $10^{24}$ atoms/m², the depth of erosion is

$$
d=2.8\ \mu\text{m}\times\frac{6.65\times10^{24}}{10^{24}}=18.6\ \mu\text{m}\approx19\ \mu\text{m}.
$$

> [!check] Numerical check
> The same fluence would remove $0.029\times6.65=0.19$ µm of Teflon, $0.00035\times6.65=0.0023$ µm of aluminium and $9.8\times6.65=65$ µm of silver. A 25 µm Kapton film, a common blanket outer layer, needs $25/2.8=8.9\times10^{24}$ atoms/m² to wear through, which at the same $n_{AO}V$ takes $8.9\times10^{24}/(7.7\times10^{18})=1.16\times10^6$ s, or 13.4 days.

### Radiation dose for a ten-year GEO mission

A GEO communications satellite carries electronics behind 5 mm of aluminium. From the p. 34 curves the yearly dose is about $6\times10^3$ rad(Si), so over ten years

$$
D=10\times6\times10^3=6\times10^4\ \text{rad(Si)}=60\ \text{krad(Si)}=600\ \text{J/kg}.
$$

Parts must be chosen to tolerate this with margin. Behind only 2.5 mm the yearly dose is about $1.2\times10^5$ rad, twenty times more, so the extra 2.5 mm of aluminium (6.75 kg per m² of wall) buys a factor of 20. The energy involved is tiny: a 1 g silicon chip absorbs $600\times10^{-3}=0.6$ J over the whole mission. The damage comes from where the energy goes, into ionising the crystal lattice and trapping charge in oxides, not from heating.

### Solar flux at Mars

At 1.524 AU the flux is $S=1370/1.524^2=590$ W/m², 43% of the value at Earth. A solar array sized for a given power at Earth must be $1/0.43=2.3$ times larger at Mars, before allowing for dust.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Previous: [[SESA1015 A01 - Astronautics Foundations, Missions and Applications]] · Next: [[SESA1015 A03 - Launch Environment]]
- Concepts: [[Space Environment Hazards]] · [[Exponential Atmosphere and Scale Height]] · [[Atomic Oxygen Erosion]] · [[Van Allen Radiation Belts]] · [[Blackbody Radiation]] · [[Earth Orbit Zones]]
- Related in this module: the lower atmosphere and the ISA in [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]; [[International Standard Atmosphere]]
- Later in the degree: [[SESA2024 10 - Thermal Control]] and [[Spacecraft Thermal Balance Equation]] use the solar flux and surface properties; [[SESA2024 08 - Electrical Power Subsystem]] and [[Solar Cells and Arrays]] size arrays for the flux and the radiation degradation; [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]] develops drag decay; [[SESA2024 15 - Space Sustainability, Debris and NewSpace]] and [[Space Debris Mitigation]] treat debris.

## Sources

- SESA1015 Astronautics Part 2, Environment (Dr S.J.I. Walker), pp. 1–38: natural and induced environments p. 3; the Sun pp. 4–12; atmosphere pp. 13–20; magnetic field and trapped radiation pp. 21–25; debris pp. 26–27; summary p. 28; effects on design pp. 29–37. The launch environment, pp. 39–46, is in [[SESA1015 A03 - Launch Environment]].
- Further reading set on p. 48: Fortescue, Stark and Swinerd, *Spacecraft Systems Engineering*, Chapter 2; *How Spacecraft Fly*, Chapter 6.
- Dose values in §6 and the AO number densities in §3 are read from the graphs on pp. 20 and 34 and are approximate. The orbital-drag derivation, the black-body temperature of the Sun, the debris energy and the scale-height table are worked from the slide data. All numbers were recomputed in Python; figures from `01 - Notes/Figures/generate_astro_a02_figures.py`.

## Self-study tasks

### Core

- [ ] Work the AO erosion example: depth of Kapton erosion on a 10-day Shuttle mission at 300 km during solar maximum (pp. 35–36). → [[#Atomic-oxygen erosion of Kapton on a Shuttle flight]]
- [ ] Derive equation (2.1) for the density of species $i$ from hydrostatic balance and the ideal gas law, and compute $H$ for N$_2$, O and He at 1000 K (p. 18; derivation suggested, not lecturer-set). → [[#Density and the scale height]]
- [ ] For each item on the hostile/friendly list (p. 29), name one effect on spacecraft design. → [[#6. Effects on design and on people]]

### Further practice

- [ ] Estimate the yearly and ten-year dose for a GEO and a 500 km, 28° mission behind 5 mm of aluminium, in rad(Si) and J/kg (suggested, not lecturer-set). → [[#Radiation dose for a ten-year GEO mission]]
- [ ] Estimate the drag force and the loss of altitude per orbit for a 1000 kg, 1 m², $C_D=2.2$ satellite at 400 km with $\rho=3\times10^{-12}$ kg/m³ (suggested, not lecturer-set). → [[#Orbital drag]]
## Transcript and slide slips

> [!warning] Slide slip (Part 2, p. 18)
> Where: [[#Density and the scale height]].
>
> Under equation (2.2) the scale height is given as "H = scale height (T/Mi)". The scale height is $H=RT/(Mg)$; it is proportional to $T/M$, not equal to it, and for the total density $M$ is the mean molar mass, not that of one species.
