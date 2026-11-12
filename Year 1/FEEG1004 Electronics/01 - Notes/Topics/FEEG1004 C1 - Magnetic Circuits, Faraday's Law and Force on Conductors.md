---
title: "FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 1
tags:
- feeg1004
- machines
- magnetic-circuit
- mmf
- reluctance
- faraday
- lorentz
- motional-emf
aliases:
- Electric Machines 01
- Magnetic field quantities
- E = NBLu
- Machines introduction
date: 2026-09-27
status: lectured
parent:
- "[[FEEG1004 Electronics Hub]]"
prerequisites:
- "[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]"
next_topics:
- "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"
key_concepts:
- "[[Magnetomotive Force and Reluctance]]"
- "[[Motional EMF in Electric Machines]]"
- "[[Faraday's Law and Lenz's Law]]"
- "[[Lorentz Force]]"
tutorial_sheets:
- "[[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]]"
sources:
- 02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf
- 02 - Sources/S2 Machines/S2-W18-21 Electric Machines 01 - Intro and Faraday - Lecture Slides.pdf
- 02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf
- 02 - Sources/Lectures/FEEG1004 Lecture 2025-01-27.txt
- 02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf
coverage: "FEEG1004 Lecture 2025-01-27 (ll. 256–664)"
---

# FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors

> [!abstract] Summary
> Generators, motors and transformers rest on the laws of [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]], rewritten for flux guided by iron cores and conductors moving through air-gap fields. A coil's magnetomotive force $\mathcal{F}=Ni$ drives flux through a core of reluctance $\mathcal{R}=l/(\mu_0\mu_rA)$ according to $\mathcal{F}=\Phi\mathcal{R}$, the magnetic analogue of $V=IR$, and a millimetre-scale air gap can dominate that reluctance. A conductor cutting a field develops the motional EMF $E=NBLu$ (Fleming's right-hand rule), and a conductor carrying current across a field feels $F=BiL$ (left-hand rule). In a loaded machine both effects act at once, and $Ei=Fu$.

> [!summary]- Exam use: quick path
> - **Use it when:** finding MMF, flux, flux density, field intensity or inductance of a cored coil, with or without an air gap; finding the EMF of a moving conductor or coil; finding the force on a current-carrying wire; sketching flux and EMF for a magnet falling through a coil.
> - **Assumptions:** uniform flux across the core section; linear iron (below the knee of the $B$–$H$ curve); no leakage or fringing at the gap; $B$, $L$ and $u$ (or $i$) mutually perpendicular unless an angle is given.
> - **Method:** 1. Find $\mathcal{F}=Ni$. 2. Add series reluctances, $\mathcal{R}_{\text{tot}}=\mathcal{R}_c+\mathcal{R}_g$. 3. Get $\Phi=\mathcal{F}/\mathcal{R}_{\text{tot}}$, then $B=\Phi/A$ and $H=B/\mu$. 4. For moving conductors use $E=NBLu$ and $F=NBiL$ with only the active length in the field. 5. Check the power balance $Ei=Fu$ or Ampère's law $\sum H_kl_k=Ni$.
> - **Common mistakes:** treating reluctance as the ease of flux flow (it is the opposition; permeance is the ease); counting conductor length outside the field, or the side arms of a coil, in $L$.
> - **Practise:** [[#Worked examples]] · [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q3: 10 m cable carrying 1 kA DC east–west across a 10⁻⁴ T northward field|Tutorial 5 Q3]]

Every generator, transformer and motor, from a $700\ \text{MW}$ hydroelectric alternator down to a miniature stepper motor driving a microfluidic pump, uses a magnetic circuit to channel flux across a narrow air gap. In that gap, conductors either cut flux lines and generate a voltage, or carry current across flux lines and feel a force that produces torque.

The iron core plays the part that copper wire plays in an electric circuit. A coil supplies the magnetomotive push, the iron offers an easy path, and the flux follows it round. Iron is only a few thousand times more permeable than air, so the gap the rotor needs to turn freely costs a large share of the coil's MMF, and machine designers keep it as small as tolerances allow.

Once the field is in place, two laws do the energy conversion. Moving a conductor through the field induces an EMF, and passing a current through a conductor in the field produces a force. Neither law switches off in a working machine: a loaded generator feels a braking force, and a spinning motor generates a back EMF. The balance between the two is how electrical power $Ei$ becomes mechanical power $Fu$ and back.

## 1. Electromagnetism and magnetic field quantities

An **electric machine** is an electromechanical energy converter that links an electrical circuit to a mechanical system through a magnetic field. A **generator** accepts mechanical shaft power from a prime mover (a steam, hydro or wind turbine, or an internal-combustion engine) and converts it into electrical power; a **motor** accepts electrical power from a supply and converts it into torque and shaft rotation. A rotating machine has a stationary outer cylinder, the **stator**, and an inner rotating cylinder, the **rotor**, separated by a narrow radial **air gap**. The gap is typically a few millimetres in large machines and under a millimetre in small motors, so that the rotor can spin freely while the flux lost across the gap stays small.

The field in a machine comes either from permanent magnets or from a direct current $i$ in a coil of $N$ turns, which forms an electromagnet. Flux lines from a coil form closed loops through its interior and back round the outside. The **right-hand grip rule** gives their direction: with the fingers of the right hand curled round the coil in the direction of conventional current $i$, the thumb points along the internal flux $\Phi$ towards the **North pole**, the end from which flux lines emerge. The opposite end, where they re-enter, is the **South pole**.

Six quantities describe the field and the coil geometry:

| Quantity | Symbol and defining relation | SI unit | Physical meaning |
|---|---|---|---|
| Magnetic flux | $\Phi$ | $\text{Wb}$ ($\text{V}\,\text{s}$) | Total magnetic field passing through a given cross-sectional surface |
| Flux linkage | $\lambda = N\Phi$ | $\text{Wb-turns}$ | Total flux linked by all $N$ turns of a coil connected in series |
| Magnetic flux density | $B = \dfrac{\Phi}{A}$ (uniform field) | $\text{T}$ ($\text{Wb}\,\text{m}^{-2}$) | Magnetic flux per unit area normal to the flux lines |
| Magnetomotive force (MMF) | $\mathcal{F} = Ni$ | $\text{A-turns}$ (or $\text{A}$) | Driving effort supplied by $N$ turns carrying current $i$ |
| Magnetic field intensity | $H$, where $\oint H\,\mathrm{d}l = Ni$ | $\text{A}\,\text{m}^{-1}$ | MMF expended per unit path length along a closed flux loop |
| Magnetic reluctance | $\mathcal{R} = \dfrac{\mathcal{F}}{\Phi}$ | $\text{A}\,\text{Wb}^{-1}$ ($\text{H}^{-1}$) | Opposition of a magnetic path to the establishment of magnetic flux |

Over a uniform cross-section of area $A$ with the flux lines normal to the surface, flux and flux density are related by

$$\Phi = B A \iff B = \frac{\Phi}{A}.$$

Along a closed magnetic path made of $K$ piecewise-uniform segments with lengths $l_1, l_2, \dots, l_K$ and field intensities $H_1, H_2, \dots, H_K$, **Ampère's circuital law** states that the line integral of $H$ round the loop equals the enclosed current $Ni$:

$$\mathcal{F} = Ni = \oint H\,\mathrm{d}l = \sum_{k=1}^{K} H_k l_k.$$

In a single uniform toroidal core of mean perimeter $l$, $H$ is constant along the mean path, so Ampère's law reduces to

$$\mathcal{F} = H l \iff H = \frac{Ni}{l}.$$

## 2. Magnetic circuits, reluctance and air gaps

Machines and transformers wind their coils on ferromagnetic cores of soft iron or silicon steel, which concentrate and steer the flux without needing a large coil current. In an isotropic material of relative permeability $\mu_r$ and absolute permeability $\mu = \mu_0 \mu_r$, where $\mu_0 = 4\pi \times 10^{-7}\ \text{H}\,\text{m}^{-1}$ is the permeability of free space, a field intensity $H$ produces the flux density

$$B = \mu H = \mu_0 \mu_r H.$$

Take the flux $\Phi$ as uniform across a core of cross-sectional area $A$ and mean path length $l$. Substituting $H = B/(\mu_0 \mu_r)$ and then $B = \Phi/A$ into Ampère's law relates the MMF directly to the flux:

$$\begin{aligned}
\mathcal{F} &= H l \\[4pt]
&= \left(\frac{B}{\mu_0 \mu_r}\right) l \\[4pt]
&= \left(\frac{\Phi}{\mu_0 \mu_r A}\right) l \\[4pt]
&= \Phi \left(\frac{l}{\mu_0 \mu_r A}\right) \\[4pt]
&= \Phi \mathcal{R},
\end{aligned}$$

where the **magnetic reluctance** of the uniform path is

$$\mathcal{R} = \frac{l}{\mu_0 \mu_r A} = \frac{l}{\mu A}.$$

The relation $\mathcal{F} = \Phi \mathcal{R}$, often called **Hopkinson's law**, is the magnetic analogue of Ohm's law $V = I R$ for a uniform conductor of length $l$, cross-sectional area $A$ and conductivity $\sigma = 1/\rho$:

| Electrical circuit quantity | Formula | Magnetic circuit analogue | Formula |
|---|---|---|---|
| Electromotive force (voltage) | $V$ [$\text{V}$] | Magnetomotive force (MMF) | $\mathcal{F} = Ni$ [$\text{A-turns}$] |
| Electric current | $I = J A$ [$\text{A}$] | Magnetic flux | $\Phi = B A$ [$\text{Wb}$] |
| Current density | $J = \sigma E$ [$\text{A}\,\text{m}^{-2}$] | Magnetic flux density | $B = \mu H$ [$\text{T}$] |
| Electric field strength | $E = V/l$ [$\text{V}\,\text{m}^{-1}$] | Magnetic field intensity | $H = \mathcal{F}/l$ [$\text{A}\,\text{m}^{-1}$] |
| Electrical conductivity | $\sigma$ [$\text{S}\,\text{m}^{-1}$] | Magnetic permeability | $\mu = \mu_0 \mu_r$ [$\text{H}\,\text{m}^{-1}$] |
| Electrical resistance | $R = \dfrac{l}{\sigma A} = \dfrac{V}{I}$ [$\Omega$] | Magnetic reluctance | $\mathcal{R} = \dfrac{l}{\mu_0 \mu_r A} = \dfrac{\mathcal{F}}{\Phi}$ [$\text{A}\,\text{Wb}^{-1}$] |

The analogy has two limits. First, copper has a conductivity $\sigma_{\text{Cu}} \approx 6 \times 10^7\ \text{S}\,\text{m}^{-1}$, roughly $10^{20}$ times that of air, so current stays inside a wire. Soft steel has $\mu_r \sim 400\text{--}5000$, only three to four orders of magnitude above air ($\mu_r = 1$), so a noticeable fraction of the flux leaks out of the core into the surrounding air (**leakage flux**) or bows outwards where it crosses a gap (**fringing**). Second, $\mu_r$ is constant only below the knee of the $B$–$H$ curve ($B \lesssim 1.5\ \text{T}$ for silicon steel); above saturation it drops sharply towards $1$.

> [!warning] Reluctance stores energy; it does not dissipate it
> A current $I$ in a resistance $R$ continuously dissipates $I^2 R$. A steady DC flux $\Phi$ in a reluctance $\mathcal{R}$ instead stores the static magnetic energy $\tfrac{1}{2}\mathcal{R}\Phi^2 = \tfrac{1}{2}Li^2$ and dissipates nothing in the reluctance itself. The only DC loss is $i^2 R_{\text{coil}}$ in the copper winding.

The self-inductance $L$ of an $N$-turn coil on a core of reluctance $\mathcal{R}$ follows from $\mathcal{F} = Ni = \Phi \mathcal{R}$ and the definition of flux linkage, $\lambda = N\Phi = Li$:

$$\begin{aligned}
L &= \frac{\lambda}{i} \\[4pt]
&= \frac{N\Phi}{i} \\[4pt]
&= \frac{N}{i}\left(\frac{Ni}{\mathcal{R}}\right) \\[4pt]
&= \frac{N^2}{\mathcal{R}} = \frac{\mu_0 \mu_r N^2 A}{l}.
\end{aligned}$$

### Air gap in a series magnetic circuit

In a rotating machine the flux must cross the radial gap between the stator and rotor cores. Consider a core of mean iron path length $l_c$, relative permeability $\mu_r \gg 1$ and cross-sectional area $A$, interrupted by a thin air gap of length $l_g$ with the same effective area $A$ (fringing neglected). The same flux $\Phi$ passes in series through iron and gap, so $B_c = B_g = \Phi/A$, and Ampère's circuital law gives

$$\begin{aligned}
\mathcal{F} &= H_c l_c + H_g l_g \\[4pt]
&= \left(\frac{B}{\mu_0 \mu_r}\right) l_c + \left(\frac{B}{\mu_0}\right) l_g \\[4pt]
&= \Phi \left(\frac{l_c}{\mu_0 \mu_r A} + \frac{l_g}{\mu_0 A}\right) \\[4pt]
&= \Phi (\mathcal{R}_c + \mathcal{R}_g) = \Phi \mathcal{R}_{\text{tot}}.
\end{aligned}$$

The core and gap reluctances add in series, like series resistors:

$$\mathcal{R}_c = \frac{l_c}{\mu_0 \mu_r A}, \qquad \mathcal{R}_g = \frac{l_g}{\mu_0 A}, \qquad \mathcal{R}_{\text{tot}} = \mathcal{R}_c + \mathcal{R}_g = \frac{1}{\mu_0 A}\left(\frac{l_c}{\mu_r} + l_g\right).$$

Their ratio shows why the gap governs machine design:

$$\frac{\mathcal{R}_g}{\mathcal{R}_c} = \mu_r \frac{l_g}{l_c}.$$

A gap of thickness $l_g$ has the same reluctance as a length $\mu_r l_g$ of core. With $\mu_r = 2000$, a $1\ \text{mm}$ gap opposes flux as strongly as $2000\ \text{mm} = 2\ \text{m}$ of steel. Designers therefore make the clearance between rotor and stator as narrow as manufacturing tolerances, shaft stiffness and thermal expansion permit.

## 3. Faraday's law, Lenz's law and motional EMF

**Faraday's law of electromagnetic induction** ([[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]) is the first of the two laws behind electromechanical energy conversion. When the flux $\Phi(t)$ linking an $N$-turn coil changes with time, an EMF $e(t)$ appears across the coil terminals, proportional to the rate of change of flux linkage $\lambda = N\Phi$:

$$e(t) = -\frac{\mathrm{d}\lambda}{\mathrm{d}t} = -\frac{\mathrm{d}(N\Phi)}{\mathrm{d}t} = -N\frac{\mathrm{d}\Phi}{\mathrm{d}t}.$$

The minus sign is **Lenz's law**: the induced EMF has the polarity that, if the circuit is closed and an induced current $i_{\text{ind}}$ flows, makes the field of $i_{\text{ind}}$ oppose the change in external flux that caused it.

Consider a bar magnet with its North pole pointing downwards, dropped vertically towards a stationary horizontal coil. As the North pole approaches the top of the coil, the downward flux through the coil increases ($\mathrm{d}\Phi/\mathrm{d}t > 0$). The induced current must set up an upward field, an induced North pole on the coil's upper face, which opposes the increase and pushes up on the falling magnet. The right-hand grip rule with the thumb upwards then gives an induced current, and EMF, circulating anticlockwise when viewed from above. If the magnet falls right through the coil at constant speed (as in [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q1: Bar magnet falling at constant speed through a coil|Tutorial 5 Q1]]), the linked flux rises from zero as the leading pole enters and reaches a flat peak with the magnet halfway through, where $\mathrm{d}\Phi/\mathrm{d}t = 0$ and so $e = 0$. It falls back to zero as the trailing pole leaves; there $\mathrm{d}\Phi/\mathrm{d}t < 0$, so $e$ reverses and a second pulse of opposite polarity appears.

### Motional EMF from flux cutting

In rotating machines and linear transducers the total flux enclosed by a moving coil is awkward to measure, whereas the local air-gap flux density $B$ is easy to measure or specify. Faraday's law can be rewritten in terms of the velocity $u$ at which a conductor cuts uniform flux lines.

A rectangular coil of $N$ turns and active transverse width $L$ lies in the plane of the page, partly inside a uniform field of flux density $B$ pointing out of the page. The length of coil still inside the field at time $t$ is $x(t)$, so that the area exposed to the field is $A(t) = L x(t)$. The coil is pulled horizontally out of the field at velocity $u = -\mathrm{d}x/\mathrm{d}t$, so $x$ decreases at rate $u$. The flux linking each turn is

$$\Phi(t) = B A(t) = B L x(t).$$

With $N$, $B$ and $L$ constant in time, Faraday's law gives

$$\begin{aligned}
e(t) &= -\frac{\mathrm{d}(N\Phi)}{\mathrm{d}t} \\[4pt]
&= -\frac{\mathrm{d}\bigl(N B L x(t)\bigr)}{\mathrm{d}t} \\[4pt]
&= -N B L \frac{\mathrm{d}x}{\mathrm{d}t} \\[4pt]
&= N B L u.
\end{aligned}$$

The magnitude of the **motional EMF** induced in $N$ series-connected conductors of active length $L$, cutting a uniform perpendicular field $B$ at speed $u$, is therefore

$$E = N B L u.$$

For a single straight conductor ($N = 1$), $e_c = B L u$. Two geometric conditions apply whenever the formula is used. Only the **active length** $L$, the part of the conductor inside the field and cutting across the flux lines, contributes to $E$: the two side arms joining the moving edge to the terminals move along their own length without sweeping out new flux area, and conductors outside the field ($B = 0$) contribute nothing. And $B$, $L$ and $u$ must be mutually perpendicular. If the conductor moves at an angle $\theta$ to the flux lines, only the velocity component $u_\perp = u\sin\theta$ perpendicular to $\mathbf{B}$ cuts flux, giving $E = N B L u \sin\theta$.

The polarity follows **Fleming's right-hand rule** for generators. Hold the thumb, first finger and second finger of the right hand mutually perpendicular: the thumb points along the conductor's motion $\mathbf{u}$ relative to the field, the first finger along the field $\mathbf{B}$ (North to South), and the second finger along the induced EMF, the direction in which conventional current would be driven out of the conductor's positive terminal. The mnemonic is thumb–motion, first finger–field.

![[ee_c1_motor_generator_effect.png|900]]

## 4. Lorentz force on conductors and the interaction principle

The second law is the **motor effect**. A straight conductor of active length $L$ carrying current $i$ at right angles to a uniform field of flux density $B$ feels a mechanical **Lorentz force** of magnitude

$$F = B i L.$$

In vector form $\mathbf{F} = i\,\mathbf{L} \times \mathbf{B}$, so if the conductor makes an angle $\theta$ with $\mathbf{B}$ the magnitude is $F = B i L \sin\theta$, acting perpendicular to the plane containing the wire and the field lines.

Physically the force comes from superposing two fields (Sharkh §2.3, Fig. 2.5). The magnet produces a uniform field $\mathbf{B}$ from North to South, and the current produces concentric circular field lines round the wire (right-hand grip rule). On one side of the conductor the wire's field points the same way as $\mathbf{B}$, crowding the flux lines together and raising the local flux density; on the other side the two fields oppose and partly cancel. Flux lines behave like stretched elastic bands that also repel one another sideways, so the conductor is pushed from the crowded, strong-field side towards the weak-field side.

The direction follows **Fleming's left-hand rule** for motors. With the thumb, first finger and second finger of the left hand mutually perpendicular, the first finger points along the field $\mathbf{B}$ (North to South), the second finger along the conventional current $i$, and the thumb along the resulting force or motion $\mathbf{F}$ (first–field, second–current, thumb–motion).

### Simultaneous motor and generator action

$E = NBLu$ is called the generator effect and $F = BiL$ the motor effect, but neither law switches off when a machine runs in the other mode. Whenever a conductor both moves through a field ($u \neq 0$) and carries current ($i \neq 0$), both act at once.

In a loaded generator, a prime mover pushes the conductor at velocity $u$ across the field, inducing $E = NBLu$ (right-hand rule). Once a load is connected, current $i$ flows in the direction of $E$. The conductor now carries current in the field, so it feels a Lorentz force $F = NBiL$ which, by the left-hand rule, points opposite to $u$. To hold the speed constant, the prime mover must apply an equal and opposite driving force $F_{\text{drive}} = NBiL$, supplying mechanical power

$$P_{\text{mech}} = F_{\text{drive}} u = (NBiL) u = (NBLu) i = E i = P_{\text{elec}}.$$

In a motor, a supply drives current $i$ through the conductor, producing the force $F = NBiL$ (left-hand rule) that accelerates the rotor. As soon as the conductor moves at speed $u$ it cuts flux and induces a motional EMF $E' = NBLu$ whose polarity, by the right-hand rule, opposes the supply voltage. This is the **back EMF**. To drive current into the motor against $E'$ the supply must deliver electrical power $E'i = (NBLu)i = (NBiL)u = Fu$, which is the mechanical power delivered to the rotor.

The equality of electrical power $Ei$ and mechanical power $Fu$ (or $T\omega$ in rotating form) is conservation of energy, enforced by Lenz's law, and it holds throughout Part C.

The same two laws apply in later modules. Spacecraft **magnetorquers** are air-cored or rod-cored coils whose magnetic dipole interacts with Earth's field through $\mathbf{F} = I\mathbf{L} \times \mathbf{B}$, while **reaction wheels** are brushless DC motors governed by $E = NBLu$ and $F = BiL$ ([[Attitude Sensors and Torquers]], [[Reaction Wheels and Momentum Dumping]], [[SESA2024 06 - Attitude Control]]). Hall-effect thrusters use a radial magnetic circuit ($\mathcal{F} = \Phi \mathcal{R}$ across an annular channel gap) to trap electrons by the Lorentz force while xenon ions are accelerated electrostatically ([[Electric (Ion) Propulsion]]). Variable-reluctance proximity pickups and the **LVDT** sense displacement by moving a ferromagnetic core, which changes the reluctance $\mathcal{R}$ and hence the inductance $L = N^2/\mathcal{R}$ or the mutual flux linkage of a coil ([[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]], [[Linear Variable Differential Transformer]]).

### Conventions for Part C

Notes [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems|C2]] to [[FEEG1004 C6 - DC Motor Characteristics and Speed Control|C6]] use two conventions. The pole count $N_p$ (or $p$) is the total number of magnetic poles, an even integer ($2, 4, 6, \dots$), so the number of North–South pole pairs is $N_p/2$. And $\omega$ is the mechanical angular velocity in $\text{rad}\,\text{s}^{-1}$, while $\text{rpm}$ is revolutions per minute, related by

$$\omega = \frac{2\pi\,\text{rpm}}{60}\ \text{rad}\,\text{s}^{-1} \iff \text{rpm} = \frac{60\,\omega}{2\pi}.$$

## Worked examples

### Soft-steel toroid

A toroidal soft-steel core (`S2-W18-21 Electric Machines 02` slide 3) has mean circumference $l = 0.4\ \text{m}$, uniform cross-sectional area $A = 500\ \text{mm}^2$ and reluctance $\mathcal{R}_c = 1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}$. A coil of $N = 100$ turns carries a direct current $I = 4\ \text{A}$, entering over the outer top edge of the ring on the left side and wrapping behind the inner edge. The task is to find the direction of the flux, the MMF $\mathcal{F}$, the flux $\Phi$, the mean flux density $B$, the field intensity $H$, the relative permeability $\mu_r$ at this operating point, and the coil inductance $L$.

For the direction, apply the right-hand grip rule to the coil on the left limb. Curling the fingers over the front of the core and behind the inner wall in the direction of the $4\ \text{A}$ current points the thumb upwards along the left side of the ring, so the flux circulates **clockwise** round the toroid.

The MMF is

$$\begin{aligned}
\mathcal{F} &= N I \\[4pt]
&= 100 \times 4\ \text{A} \\[4pt]
&= 400\ \text{A-turns}.
\end{aligned}$$

Hopkinson's law $\mathcal{F} = \Phi \mathcal{R}_c$ gives the flux:

$$\begin{aligned}
\Phi &= \frac{\mathcal{F}}{\mathcal{R}_c} \\[4pt]
&= \frac{400\ \text{A-turns}}{1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}} \\[4pt]
&= 2.381 \times 10^{-4}\ \text{Wb} = 0.238\ \text{mWb}.
\end{aligned}$$

In SI units the area is $A = 500\ \text{mm}^2 = 500 \times 10^{-6}\ \text{m}^2 = 5.0 \times 10^{-4}\ \text{m}^2$. With the flux uniform across the section,

$$\begin{aligned}
B &= \frac{\Phi}{A} \\[4pt]
&= \frac{2.381 \times 10^{-4}\ \text{Wb}}{5.0 \times 10^{-4}\ \text{m}^2} \\[4pt]
&= 0.476\ \text{T},
\end{aligned}$$

well below the saturation limit of soft steel ($\sim 1.5\ \text{T}$).

Ampère's circuital law round the mean path $l = 0.4\ \text{m}$ gives the field intensity:

$$\begin{aligned}
H &= \frac{\mathcal{F}}{l} \\[4pt]
&= \frac{400\ \text{A-turns}}{0.4\ \text{m}} \\[4pt]
&= 1000\ \text{A}\,\text{m}^{-1}.
\end{aligned}$$

From $B = \mu_0 \mu_r H$ with $\mu_0 = 4\pi \times 10^{-7}\ \text{H}\,\text{m}^{-1}$, the relative permeability of the steel is

$$\begin{aligned}
\mu_r &= \frac{B}{\mu_0 H} \\[4pt]
&= \frac{0.4762\ \text{T}}{(4\pi \times 10^{-7}\ \text{H}\,\text{m}^{-1})(1000\ \text{A}\,\text{m}^{-1})} \\[4pt]
&= 378.9.
\end{aligned}$$

The self-inductance of the $100$-turn winding is

$$\begin{aligned}
L &= \frac{N^2}{\mathcal{R}_c} \\[4pt]
&= \frac{100^2}{1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}} \\[4pt]
&= 5.952 \times 10^{-3}\ \text{H} = 5.95\ \text{mH}.
\end{aligned}$$

> [!check] Reluctance and flux linkage
> Recomputing the reluctance from $\mu_r = 378.94$, $l = 0.4\ \text{m}$ and $A = 5.0 \times 10^{-4}\ \text{m}^2$ gives
> $$\mathcal{R}_c = \frac{l}{\mu_0 \mu_r A} = \frac{0.4\ \text{m}}{(4\pi \times 10^{-7}\ \text{H}\,\text{m}^{-1})(378.94)(5.0 \times 10^{-4}\ \text{m}^2)} = 1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}.$$
> The inductance from flux linkage per unit current, $L = N\Phi/I = (100 \times 2.381 \times 10^{-4}\ \text{Wb})/(4\ \text{A}) = 5.95\ \text{mH}$, matches $N^2/\mathcal{R}_c$ to three significant figures.

### Toroid with a 1 mm air gap

A radial slot of width $l_g = 1.0\ \text{mm}$ ($1.0 \times 10^{-3}\ \text{m}$) is cut into the same toroid ($l_c \approx 0.4\ \text{m}$, $A = 5.0 \times 10^{-4}\ \text{m}^2$, $\mathcal{R}_c = 1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}$, $N = 100$), neglecting fringing. The questions are the gap reluctance compared with the core's, the new flux and flux density at $I = 4\ \text{A}$, and the current needed to restore $B = 0.476\ \text{T}$ for a $1.0\ \text{mm}$ and a $2.0\ \text{mm}$ gap.

In air $\mu_r = 1$, so

$$\begin{aligned}
\mathcal{R}_g &= \frac{l_g}{\mu_0 A} \\[4pt]
&= \frac{1.0 \times 10^{-3}\ \text{m}}{(4\pi \times 10^{-7}\ \text{H}\,\text{m}^{-1})(5.0 \times 10^{-4}\ \text{m}^2)} \\[4pt]
&= 1.592 \times 10^6\ \text{A}\,\text{Wb}^{-1}.
\end{aligned}$$

The total series reluctance is

$$\begin{aligned}
\mathcal{R}_{\text{tot}} &= \mathcal{R}_c + \mathcal{R}_g \\[4pt]
&= 1.680 \times 10^6\ \text{A}\,\text{Wb}^{-1} + 1.592 \times 10^6\ \text{A}\,\text{Wb}^{-1} \\[4pt]
&= 3.272 \times 10^6\ \text{A}\,\text{Wb}^{-1}.
\end{aligned}$$

The gap is only $1\ \text{mm}/400\ \text{mm} = 0.25\%$ of the circumference, yet its reluctance is nearly that of the whole $400\ \text{mm}$ core and makes up $1.592/3.272 = 48.6\%$ of the total.

With $\mathcal{F} = NI = 400\ \text{A-turns}$ unchanged, the new flux is

$$\begin{aligned}
\Phi' &= \frac{\mathcal{F}}{\mathcal{R}_{\text{tot}}} \\[4pt]
&= \frac{400\ \text{A-turns}}{3.272 \times 10^6\ \text{A}\,\text{Wb}^{-1}} \\[4pt]
&= 1.223 \times 10^{-4}\ \text{Wb} = 0.122\ \text{mWb},
\end{aligned}$$

and the flux density in both core and gap is

$$\begin{aligned}
B' &= \frac{\Phi'}{A} \\[4pt]
&= \frac{1.223 \times 10^{-4}\ \text{Wb}}{5.0 \times 10^{-4}\ \text{m}^2} \\[4pt]
&= 0.245\ \text{T}.
\end{aligned}$$

The $1.0\ \text{mm}$ slot nearly halves the flux density, from $0.476\ \text{T}$ to $0.245\ \text{T}$.

To restore the original flux $\Phi = 2.381 \times 10^{-4}\ \text{Wb}$ ($B = 0.476\ \text{T}$) through $\mathcal{R}_{\text{tot}} = 3.272 \times 10^6\ \text{A}\,\text{Wb}^{-1}$, the required MMF and current are

$$\begin{aligned}
\mathcal{F}_{\text{restore}} &= \Phi \mathcal{R}_{\text{tot}} = (2.381 \times 10^{-4}\ \text{Wb})(3.272 \times 10^6\ \text{A}\,\text{Wb}^{-1}) = 779.0\ \text{A-turns} \\[4pt]
I_{\text{restore}} &= \frac{\mathcal{F}_{\text{restore}}}{N} = \frac{779.0\ \text{A-turns}}{100} = 7.79\ \text{A}.
\end{aligned}$$

Doubling the gap to $l_g = 2.0\ \text{mm}$ doubles its reluctance to $\mathcal{R}_g = 3.183 \times 10^6\ \text{A}\,\text{Wb}^{-1}$, so $\mathcal{R}_{\text{tot}} = (1.680 + 3.183) \times 10^6 = 4.863 \times 10^6\ \text{A}\,\text{Wb}^{-1}$. The gap is now $3.183/4.863 = 65.5\%$ of the total, and the current needed is $I_{\text{restore}} = (2.381 \times 10^{-4})(4.863 \times 10^6)/100 = 11.58\ \text{A}$.

> [!check] Ampère's law across core and gap
> At $I = 4\ \text{A}$ with the $1.0\ \text{mm}$ gap ($B' = 0.2445\ \text{T}$), the field intensities in the steel ($\mu_r = 378.94$) and in the gap are
> $$H_c = \frac{B'}{\mu_0 \mu_r} = \frac{0.2445\ \text{T}}{(4\pi \times 10^{-7})(378.94)} = 513.5\ \text{A}\,\text{m}^{-1}, \qquad H_g = \frac{B'}{\mu_0} = \frac{0.2445\ \text{T}}{4\pi \times 10^{-7}} = 1.946 \times 10^5\ \text{A}\,\text{m}^{-1}.$$
> Summing the MMF drops round the loop,
> $$H_c l_c + H_g l_g = (513.5\ \text{A}\,\text{m}^{-1})(0.4\ \text{m}) + (1.946 \times 10^5\ \text{A}\,\text{m}^{-1})(1.0 \times 10^{-3}\ \text{m}) = 205.4\ \text{A-turns} + 194.6\ \text{A-turns} = 400.0\ \text{A-turns} = NI.$$
> The gap field $H_g$ is $\mu_r \approx 379$ times $H_c$.

### Force on a DC cable and a coil pulled from a field

The first part is [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q3: 10 m cable carrying 1 kA DC east–west across a 10⁻⁴ T northward field|Tutorial Sheet 5 Q3]]. Earth's field in Southampton has a horizontal northward flux density $B = 1.0 \times 10^{-4}\ \text{T}$. A straight horizontal cable of length $L = 10\ \text{m}$ and resistance $R = 0.1\ \Omega$ carries a direct current $I = 1\ \text{kA}$ east–west, perpendicular to the field. The task is the magnitude and direction of the force on the cable, and the role of the $0.1\ \Omega$ resistance.

The cable is perpendicular ($\theta = 90^\circ$) to the field, so with $I = 1000\ \text{A}$

$$\begin{aligned}
F &= B I L \\[4pt]
&= (1.0 \times 10^{-4}\ \text{T})(1000\ \text{A})(10\ \text{m}) \\[4pt]
&= 1.0\ \text{N}.
\end{aligned}$$

By Fleming's left-hand rule (or $\mathbf{F} = I\mathbf{L} \times \mathbf{B}$) the force is vertical. For current flowing west to east (first finger North, second finger East) the thumb points upwards, giving $1.0\ \text{N}$ upwards; for current flowing east to west (second finger West) it points downwards, giving $1.0\ \text{N}$ downwards.

The resistance does not enter $F = BIL$ once $I = 1000\ \text{A}$ is fixed. It sets only the DC voltage drop along the $10\ \text{m}$ length, $V = IR = 1000\ \text{A} \times 0.1\ \Omega = 100\ \text{V}$, and the Joule heating in the cable, $P = I^2 R = 1000^2 \times 0.1 = 100\ \text{kW}$.

The second part extends this to the power balance in a coil. A rectangular coil of $N = 20$ turns, active width $L = 0.25\ \text{m}$ and winding resistance $R_c = 0.5\ \Omega$ is pulled at constant speed $u = 8.0\ \text{m}\,\text{s}^{-1}$ out of a uniform perpendicular field $B = 0.6\ \text{T}$, with its terminals shorted together. The task is the induced EMF, the circulating current, the braking force, and a comparison of the pulling power $F_{\text{brake}} u$ with the ohmic dissipation $i^2 R_c$.

The motional EMF is

$$\begin{aligned}
E &= N B L u \\[4pt]
&= 20 \times (0.6\ \text{T}) \times (0.25\ \text{m}) \times (8.0\ \text{m}\,\text{s}^{-1}) \\[4pt]
&= 24.0\ \text{V}.
\end{aligned}$$

With the terminals shorted through $R_c = 0.5\ \Omega$, Ohm's law gives the circulating current

$$\begin{aligned}
i &= \frac{E}{R_c} \\[4pt]
&= \frac{24.0\ \text{V}}{0.5\ \Omega} \\[4pt]
&= 48.0\ \text{A}.
\end{aligned}$$

Each of the $20$ active conductors now carries $48.0\ \text{A}$ across $B = 0.6\ \text{T}$ over $L = 0.25\ \text{m}$, and the total Lorentz force opposing the motion is

$$\begin{aligned}
F_{\text{brake}} &= N B i L \\[4pt]
&= 20 \times (0.6\ \text{T}) \times (48.0\ \text{A}) \times (0.25\ \text{m}) \\[4pt]
&= 144.0\ \text{N}.
\end{aligned}$$

> [!check] Electromechanical power balance
> The pulling agent must supply $P_{\text{mech}} = F_{\text{brake}}\,u = (144.0\ \text{N})(8.0\ \text{m}\,\text{s}^{-1}) = 1152\ \text{W}$ to hold the speed. The electrical power generated is $P_{\text{elec}} = E i = (24.0\ \text{V})(48.0\ \text{A}) = 1152\ \text{W}$, and the dissipation in the winding is $i^2 R_c = (48.0\ \text{A})^2 (0.5\ \Omega) = 1152\ \text{W}$. Mechanical input and electrical output match exactly ($1.152\ \text{kW}$).

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Prerequisite: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]
- Next: [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]
- Concepts: [[Magnetomotive Force and Reluctance]] · [[Motional EMF in Electric Machines]] · [[Faraday's Law and Lenz's Law]] · [[Lorentz Force]]
- Worked problems: [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions]] (Q1, Q3)

## Sources

- `02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf` (§1 Introduction and §2 Review of Electromagnetism, pp. 3–9).
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 01 - Intro and Faraday - Lecture Slides.pdf` (slides 1–12).
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf` (slide 3: toroid magnetic circuit exercise).
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-01-27.txt` (ll. 256–664: machines overview, magnetic field quantities, toroid poll exercise, Faraday's law, Lenz's law, motional EMF $E = NBLu$, and Lorentz force $F = BiL$).
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf` (Q1, Q3).
- E. Hughes, *Electrical and Electronic Technology*, Chs. 6–8 (Electromagnetism, Simple Magnetic Circuits, Inductance).

## Self-study tasks

### Core

- [ ] For the soft-steel toroid ($N = 100$, $I = 4\ \text{A}$, $\mathcal{R} = 1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}$, $A = 500\ \text{mm}^2$, $l = 0.4\ \text{m}$), find the flux direction, $\mathcal{F}$, $\Phi$, $B$ and $H$ (`S2-W18-21 Electric Machines 02` slide 3; Lecture 2025-01-27, ll. 461–527). → [[#Soft-steel toroid]]
- [ ] Starting from $e = -\mathrm{d}(N\Phi)/\mathrm{d}t$, derive $E = NBLu$ for a rectangular $N$-turn coil of active width $L$ pulled at velocity $u$ out of a uniform perpendicular field $B$ (`S2-W18-21 Electric Machines 01` slide 10; Lecture 2025-01-27, ll. 598–631). → [[#Motional EMF from flux cutting]]
- [ ] Sketch $\Phi(t)$ and the terminal voltage $v(t)$ as a long bar magnet falls at constant velocity right through a coil, marking the point of maximum voltage ($A$) and the midpoint ($B$) (Tutorial Sheet 5 Q1). → [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q1: Bar magnet falling at constant speed through a coil|Tutorial 5 Q1]]; [[#3. Faraday's law, Lenz's law and motional EMF]]
- [ ] Find the magnitude and direction of the force on a $10\ \text{m}$ east–west cable of resistance $0.1\ \Omega$ carrying $1\ \text{kA}$ DC across Earth's northward field of $1.0 \times 10^{-4}\ \text{T}$ (Tutorial Sheet 5 Q3). → [[#Force on a DC cable and a coil pulled from a field]]; [[FEEG1004 Tutorial 5 - Faraday, Generators and Transformers Solutions#Q3: 10 m cable carrying 1 kA DC east–west across a 10⁻⁴ T northward field|Tutorial 5 Q3]]

### Further practice

- [ ] Repeat the air-gap example for a silicon-steel core with $\mu_r = 2500$, $l_c = 0.5\ \text{m}$, $A = 4.0 \times 10^{-4}\ \text{m}^2$ and a $1.5\ \text{mm}$ gap, and verify that the gap carries $\mu_r l_g/(l_c + \mu_r l_g) = 3.75/4.25 = 88.2\%$ of the total reluctance (suggested, not lecturer-set). → [[#Toroid with a 1 mm air gap]]; [[#2. Magnetic circuits, reluctance and air gaps]]

## Transcript and slide slips

### Factor of one million missing from the spoken toroid reluctance

> [!warning] Transcript slip (Lecture 2025-01-27, ll. 488–490)
> Where: [[#Soft-steel toroid]]
> Reading out Question 3 of the toroid exercise (`S2-W18-21 Electric Machines 02` slide 3), the transcript gives the core reluctance as "1.68 amp per Weber" ($1.68\ \text{A}\,\text{Wb}^{-1}$), omitting the factor of $10^6$ printed on the slide ($\mathcal{R} = 1.68 \times 10^6\ \text{A}\,\text{Wb}^{-1}$). The factor of $10^6$ is needed to give $\Phi = 0.238\ \text{mWb}$ and $B = 0.476\ \text{T}$.

### Reluctance described as ease rather than opposition

> [!warning] Notes and transcript phrasing (Sharkh p. 6 §2.1; Lecture 2025-01-27, ll. 431–433)
> Where: [[#1. Electromagnetism and magnetic field quantities]] and [[#2. Magnetic circuits, reluctance and air gaps]]
> Section 2.1 of the printed notes, and the spoken summary, describe the reluctance $\mathcal{R}$ in $\mathcal{F} = \Phi \mathcal{R}$ as "a measure of how easy it is for the magnetic flux to flow in the coil core". Because $\Phi = \mathcal{F}/\mathcal{R}$, a larger reluctance $\mathcal{R} = l/(\mu_0 \mu_r A)$ gives a smaller flux for a given MMF. Reluctance measures the opposition of a path to flux (like resistance $R = V/I$); its reciprocal, the **permeance** $\mathcal{P} = 1/\mathcal{R}$, measures how easily flux flows (like conductance $G = 1/R$).

### Transcription garbling of Faraday, Lenz and Lorentz

> [!warning] Speech-to-text artefacts (Lecture 2025-01-27, ll. 533–654)
> Where: [[#3. Faraday's law, Lenz's law and motional EMF]] and [[#4. Lorentz force on conductors and the interaction principle]]
> The automated transcription renders "Michael Faraday" as "microphiles" (l. 533) and "my pathology" (l. 550); "Faraday's law of induction" as "Friday's law of induction" (ll. 547, 631, 653), "5G slope in Daxing" (l. 598) and "Frizi's law" (l. 615); "Lenz" as "length" (l. 552) and "lens" (l. 573); and "Lorentz force" as "Lawrence-Fourth" (l. 635) and "Lauren's Law of Force" (l. 654).
