---
title: "FEEG1002 A1 - Forces, Equilibrium, Stress and Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 1
tags: [feeg1002, statics, equilibrium, free-body-diagram, stress, strain, hookes-law]
aliases: ["Statics 1 Lecture 1", "Statics 1 Lecture 2", "Forces and Equilibrium", "Stress and Strain"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 1 (7 Oct 2024, ll. 33–856: forces, free body diagrams, equilibrium, seesaw, portal crane) and Lecture 2 (8 Oct 2024, ll. 6–579: stress, allowable stress, safety factor, stress concentration, shear stress, strain, Young's modulus, bar stiffness, Poisson's ratio, shear strain); slide decks 1 and 2 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
key_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Stress, Strain and Young's Modulus]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 01 - Forces and Equilibrium.pdf"
  - "02 - Sources/Statics 1/Lectures/Lecture 02 - Stress and Strain.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 1 - Statics 1 - Forces and equilibrium_07 October 2024.txt"
  - "02 - Sources/Lectures/FEEG1002 Lecture 2 - Statics 1 - Stress and Strain_08 October 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 01 - Forces and Equilibrium, Stress and Strain.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 01 - Forces and Equilibrium, Stress and Strain - Solutions.pdf"
---

# FEEG1002 A1 - Forces, Equilibrium, Stress and Strain

> [!abstract] Summary
> Every structural question asks whether a part is strong enough and whether it deforms too much, and both answers start from the forces on it. A free body diagram isolates the part and replaces its surroundings by reaction forces and moments; a static body then has zero resultant force and moment, which in 2D gives three equations for the unknowns. Dividing force by area gives stress, $\sigma=F/A$, which can be compared with a material limit, and dividing extension by length gives strain, $\varepsilon=\Delta L/L_0$. For a linear elastic bar in uniaxial tension $\sigma=E\varepsilon$, so the bar behaves as a spring of stiffness $EA/L_0$.

> [!summary]- Exam use: quick path
> - **Use it when:** support reactions are wanted, a bar or pin must be sized against an allowable stress, or the extension of a bar under load is needed.
> - **Assumptions:** the body is static (no acceleration); 2D, so three equilibrium equations; uniform stress over the cross-section away from the ends of a bar; linear elastic material in uniaxial tension or compression for $\sigma=E\varepsilon$; small strains, angles in radians for shear strain.
> - **Method:** 1. Draw the free body diagram and draw each unknown reaction in an assumed direction. 2. Choose and mark positive directions for forces and moments. 3. Take moments about a point through which most unknowns pass, then use force balance for the rest. 4. Convert the internal force to stress with the area that carries it (count shear planes). 5. Use $\Delta L=FL_0/(EA)$ for the deformation.
> - **Common mistakes:** taking moments with a distance that is not perpendicular to the line of action; forgetting that a pin in a fork joint shears on two planes, each carrying $F/2$.
> - **Practise:** [[#Worked example - crane tipping]] · [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Q3 - Bolt clamping force|Tutorial 1 Q3]]

A structure fails the designer in one of two ways: it breaks, or it bends and stretches so much that it stops doing its job. Judging either needs the forces acting on it, and the first difficulty is that forces come in pairs. When a car stands on a road, the wheels push down on the road and the road pushes up on the wheels with equal and opposite forces; without that reaction the car would sink. Separating the forces on the object of interest from the forces it exerts on everything else is what a free body diagram does.

Once the external forces are known, the next need is to describe how the material carries the force internally. A bar twice as wide carries twice the load before it breaks, so force alone says nothing about the material. Dividing by the area gives a stress, which the material either can or cannot sustain. In the same way, a bar twice as long stretches twice as far under the same force, so dividing the extension by the length gives a strain, a measure of how hard the material itself is being stretched. Stress and strain are linked by the stiffness of the material, Young's modulus, and that link turns a bar into a spring.

Reactions, equilibrium equations, stress, strain and Hooke's law, all in one dimension, are the starting point for the rest of Statics 1. Their generalisation to stresses and strains in several directions is covered in Statics 2 ([[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]).

---

## 1. Forces on bodies

### Newton's third law and reaction forces

**Newton's third law** states that the force exerted by a body A on a body B is equal in magnitude and opposite in direction to the force exerted by B on A. Supports exist because of it. The ground under a portal crane pushes up on each leg with a **reaction force**, and the crane pushes down on the ground with an equal force; the weight of the crane and its load is the gravitational force that the reactions balance.

### External and internal forces

An **external force** acts on a body from outside it: gravity, the push of a support, a magnet pulling a car, a box strapped to a roof. An **internal force** acts between parts of the same body, such as the force between passengers and their seats in a car, or the tension in the cable of a crane between the jib and the load. Whether a force is internal or external depends on where the boundary of the system is drawn. Draw the boundary around the whole crane and the cable tension is internal and invisible; cut through the cable and draw the boundary around the load alone, and the cable tension becomes an external force on the load.

### Free body diagrams

A **free body diagram** (FBD) is a sketch of the body isolated from its surroundings, with every contact replaced by the forces and moments it exerts. The procedure is two steps: isolate the object of interest, then replace each support by its reaction forces and/or moments. Where the boundary goes depends on the question. To check whether the crane's foundations are adequate, isolate the whole crane and replace the ground by $F_A$ and $F_B$ under the legs. To check whether the cable is strong enough, isolate the container and the cable below a cut, which reveals $F_{cable}$.

The direction of an unknown reaction is usually not known in advance. Draw it in an assumed positive direction, solve, and read the sign of the answer: a negative value means the force acts the other way.

## 2. Equilibrium

### Static means no acceleration

Statics deals with bodies that do not accelerate, in translation or in rotation. **Newton's first law** says that a body with no resultant external force or moment has no acceleration. A stationary crane has plenty of forces on it, but their resultant is zero. If the resultant were not zero, Newton's second law would give an acceleration, which is a dynamics problem ([[FEEG1002 D1 - Linear Motion of Particles]]).

Forces are vectors, so a zero resultant means each component is zero. Decompose every force into horizontal and vertical components and require each set to balance separately.

### The three equations in 2D

For a body in a plane, equilibrium gives three independent conditions:

$$
\sum F_V=0,\qquad\sum F_H=0,\qquad\sum M_A=0
$$

the last about any point A. In 3D there are six (three force components and three moments), but the problems here are almost entirely 2D. Three equations can determine at most three unknown reactions; a body with more unknowns than that is statically indeterminate (see [[FEEG1002 A2 - Pin-Jointed Trusses#6. Mechanisms, determinate and indeterminate trusses|A2]] and [[FEEG1002 A6 - Statically Indeterminate Beams|A6]]).

The positive direction for each sum is a free choice, but it has to be marked on the diagram and kept for every term. The crane examples take downward as positive for vertical forces and anticlockwise as positive for moments.

### Moment of a force

The **moment** of a force about a point is the force multiplied by the perpendicular distance from the point to the force's line of action, in N m. A container hanging from a crane exerts its weight along a vertical line, so its moment arm about a support is the horizontal distance to that line, however high the container hangs.

### Example: the container on a cable

The simplest FBD is a container hanging still on its cable: weight $F_{Gbox}$ down, cable tension $F_{cable}$ up. With downward positive,

$$
F_{Gbox}-F_{cable}=0
$$

$$
F_{cable}=F_{Gbox}
$$

The two forces are equal and opposite.

### Example: the seesaw, and choosing the moment point

A seesaw pivots at A. Box 1 (weight $F_{Gbox1}$) sits a distance $a$ to the left of the pivot and box 2 ($F_{Gbox2}$) a distance $b$ to the right; the pivot pushes up with $F_A$.

![[s1_seesaw_moment_point.png|900]]

Vertical equilibrium, downward positive:

$$
F_{Gbox1}+F_{Gbox2}-F_A=0
$$

$$
F_A=F_{Gbox1}+F_{Gbox2}
$$

Moments about the pivot A, anticlockwise positive. Box 1 on the left turns the seesaw anticlockwise, box 2 on the right turns it clockwise, and $F_A$ has zero arm:

$$
aF_{Gbox1}-bF_{Gbox2}=0
$$

$$
F_{Gbox1}=\frac baF_{Gbox2}
$$

A heavy box close to the pivot balances a light box far from it. The moment point can be any point. Take moments about box 1 instead: its own weight has zero arm, $F_A$ acts upward at distance $a$ to the right (anticlockwise, positive) and box 2 acts downward at $a+b$ (clockwise, negative):

$$
0\cdot F_{Gbox1}+aF_A-(a+b)F_{Gbox2}=0
$$

Substitute $F_A$ from vertical equilibrium:

$$
a(F_{Gbox1}+F_{Gbox2})-(a+b)F_{Gbox2}=0
$$

$$
aF_{Gbox1}+aF_{Gbox2}-aF_{Gbox2}-bF_{Gbox2}=0
$$

$$
aF_{Gbox1}=bF_{Gbox2}
$$

The same result. The pivot was the better choice only because the unknown $F_A$ passes through it and drops out at once.

## 3. The portal crane

### Load at mid-span

A portal crane stands on two legs, A and B, a distance $2a$ apart, and lifts a container of weight $F_G$ midway between them; the weight of the crane itself is ignored. Vertical equilibrium, downward positive:

$$
F_G-F_A-F_B=0
$$

Moments about A, anticlockwise positive. $F_A$ passes through A; the container is at distance $a$ and turns the frame clockwise; $F_B$ at distance $2a$ turns it anticlockwise:

$$
0\cdot F_A-aF_G+2aF_B=0
$$

$$
2F_B=F_G
$$

$$
F_B=\tfrac12F_G
$$

and from vertical equilibrium $F_A=F_G-F_B=\tfrac12F_G$. Each leg carries half, as symmetry says it must.

### Load off centre: the lever rule

With the container moved so that it hangs a distance $b$ from leg A and $c$ from leg B, vertical equilibrium is unchanged, $F_G=F_A+F_B$. Moments about A:

$$
0\cdot F_A-bF_G+(b+c)F_B=0
$$

$$
(b+c)F_B=bF_G
$$

$$
F_B=\frac{b}{b+c}F_G
$$

Then

$$
F_A=F_G-F_B=\left(1-\frac{b}{b+c}\right)F_G
$$

$$
F_A=\frac{c}{b+c}F_G
$$

Dividing the two results gives $F_A/F_B=c/b$: each leg carries a share proportional to the distance from the load to the other leg, so the leg nearer the load carries more. It is the seesaw again, with the load as the pivot.

> [!check] Extreme cases
> With $c=0$ the container hangs directly over leg B, and the formulae give $F_A=0$, $F_B=F_G$. With $b=0$ it hangs over A and $F_A=F_G$, $F_B=0$. Both are what the physical picture demands, which is a quick test of any equilibrium result.

![[s1_portal_crane_reactions.png|900]]

## 4. Stress

### Why force is not enough

A square bar of side $D$ can carry a maximum tensile force $F$. A bar of the same material twice as wide, $2D$ by $D$, is just two of the first bars side by side and carries $2F$. Whether a part breaks therefore depends on the force per unit area, not on the force. A round bar and a square bar under the same force cannot be compared until their cross-sectional areas are known.

### Normal stress

**Stress** is force normalised by the area that carries it:

$$
\sigma=\frac FA
$$

in N/m², or pascals (Pa). It is positive in tension and negative in compression. Engineering values are large, so MPa (MN/m², the same as N/mm²) is the usual unit.

### Allowable stress and safety factor

The stress in a part is compared with a limit for the material. The **ultimate tensile strength** (UTS) is the maximum engineering stress it sustains before failing; the **yield stress** is the stress beyond which deformation becomes permanent. Designs normally stay below yield, the elastic limit. Typical values:

| Material | Yield stress (MPa) | UTS (MPa) |
|---|---|---|
| Steel (A36) | 250 | 400 |
| Aluminium alloy | 400 | 500 |

These depend strongly on composition and microstructure ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]). A mild-steel yield stress of 250 MPa is 250 N on every square millimetre: a wire of 1 mm² cross-section yields under the weight of about $250/9.81=25.5$ kg.

Designing a part to reach 249 MPa in a 250 MPa steel would be reckless: the loads are uncertain, the analysis is simplified, and the yield stress varies from batch to batch. A **safety factor** $K_{SF}>1$ divides the material limit to give the design limit:

$$
\sigma_{max,design}=\frac{1}{K_{SF}}\,\sigma_{max,material}
$$

With $K_{SF}=2$, a 250 MPa steel is designed to 125 MPa.

### Stress concentrations

Stress need not be uniform. Pulling on a plate with a hole forces the load to flow around the hole, and the stress at the edge of the hole rises well above the average over the section. The **stress concentration factor** $K_T$ is defined by

$$
\sigma_{max}=K_T\,\sigma_{mean}
$$

For a small circular hole in a very wide plate, $K_T=3$: the peak stress at the hole edge is three times the stress far from the hole. Abrupt changes of geometry do the same, for instance at the shoulder of a stepped shaft, which is why real designs round the corner with a fillet. Stress is therefore a local quantity, defined at a point as

$$
\sigma(x,y)=\frac{dF}{dA}
$$

and the average $F/A$ is only the uniform value well away from holes, steps and the gripped ends of a bar.

![[s1_stress_concentration_hole.png|820]]

### Shear stress

Two plates joined by a pin and pulled apart load the pin sideways: each plate tries to slide its part of the pin past the other, like a knife through clay. The force acts in the plane of the cut rather than normal to it, and the **shear stress** is that force divided by the area of the plane:

$$
\tau=\frac{F_{shear}}{A}
$$

also in Pa. In the tensor notation of Statics 2, $\tau$ is written $\sigma_{xy}$.

On a general cut through a loaded body the force per unit area has both a normal component and shear components, so stress on a plane is a vector (a traction), not a single number like a pressure. Describing such a state properly needs the stress tensor of [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels|B1]]. In the one-dimensional treatment here the stress is either uniaxial or pure shear.

### Worked example - equally strong rod and pin

Tutorial 1 Q2 joins two round steel rods with a pin through a fork, and asks for rod and pin diameters that fail at the same working load $F=5000$ N, given an allowable tensile stress of 400 MPa and an allowable shear stress of 240 MPa (L2, ll. 220–229).

The rod is in tension and must have area $A=F/\sigma$. For a circle $A=\pi D^2/4$:

$$
\frac{\pi D_{rod}^2}{4}=\frac F\sigma
$$

$$
D_{rod}=\sqrt{\frac{4F}{\pi\sigma}}=\sqrt{\frac{4(5000)}{\pi(400\times10^6)}}=3.99\times10^{-3}\ \mathrm m
$$

For the pin to pull out of the fork it must shear on two planes, one each side of the eye, so each plane carries $F/2=2500$ N:

$$
D_{pin}=\sqrt{\frac{4(F/2)}{\pi\tau}}=\sqrt{\frac{4(2500)}{\pi(240\times10^6)}}=3.64\times10^{-3}\ \mathrm m
$$

The rod needs 4.0 mm and the pin 3.6 mm. Designing them to the same load avoids wasting material on a part that can never be the one to fail.

## 5. Strain and Hooke's law

### Engineering strain

A bar of initial length $L_0$ under a tensile force stretches by $\Delta L$. The **engineering strain** normalises the extension by the original length:

$$
\varepsilon=\frac{\Delta L}{L_0}
$$

It is dimensionless, positive in tension and negative in compression. A strain of 0.1 means the bar is 10 % longer.

The length must be divided out because a bar of length $2L_0$ under the same force is two bars of length $L_0$ in series, each stretching $\Delta L$, so the total extension is $2\Delta L$ but

$$
\varepsilon=\frac{2\Delta L}{2L_0}=\frac{\Delta L}{L_0}
$$

the same strain. The material is stretched by the same amount in both bars, which is what strain measures.

### Young's modulus and Hooke's law

Plotting force against extension for a bar gives a curve that depends on both the geometry and the material. Plotting stress against strain removes the geometry. For a **linear elastic** material the plot is a straight line through the origin, and its slope is **Young's modulus**:

$$
E=\frac\sigma\varepsilon
$$

in Pa. $E$ is the material's stiffness, an intrinsic property independent of the shape of the specimen. A rubber band is an example of a material whose curve is not straight: it stiffens as it is stretched.

Rearranged, this is **Hooke's law** in one dimension:

$$
\sigma=E\varepsilon
$$

It holds in this form only for a linear elastic material in uniaxial tension or compression. When stresses act in two or three directions at once, the Poisson effect below couples them, and the generalised Hooke's law of [[FEEG1002 B3 - Generalised Hooke's Law|B3]] replaces it.

### A bar is a spring

Substitute the definitions of stress and strain into Hooke's law:

$$
\frac FA=E\frac{\Delta L}{L_0}
$$

$$
\boxed{F=\frac{EA}{L_0}\,\Delta L}
$$

This has the form $F=k\Delta x$ of a spring, with stiffness

$$
k=\frac{EA}{L_0}
$$

A stiffer material, a thicker bar or a shorter bar all make it harder to stretch. A 1 cm bar stretched by 1 cm is at 100 % strain, but a 1 m bar stretched by the same 1 cm is at only 1 % strain, so long bars are much easier to stretch by a given amount. Inverting the spring law gives the extension for a known force,

$$
\Delta L=\frac{FL_0}{EA}
$$

which is how truss deformations are found in [[FEEG1002 A2 - Pin-Jointed Trusses#7. Truss deformation|A2]].

### Poisson's ratio

A stretched bar also becomes thinner. With $x$ along the bar and $y$, $z$ across its breadth and depth, the lateral strains are $\varepsilon_{yy}=\Delta w/w_0$ and $\varepsilon_{zz}=\Delta d/d_0$. They are equal, and proportional to the axial strain through **Poisson's ratio** $\nu$:

$$
\varepsilon_{yy}=\varepsilon_{zz}=-\nu\,\varepsilon_{xx}
$$

The minus sign is there because axial extension produces lateral contraction. Like $E$, $\nu$ is a material property; for steel $\nu\approx0.3$, so the lateral strains are 30 % of the axial strain.

### Shear strain and the shear modulus

A rectangular block of height $H_0$ with its base fixed and a shear force on its top surface deforms into a parallelogram; the top moves sideways by $\Delta S$ and the vertical sides tilt through an angle $\varphi$. The **engineering shear strain** is

$$
\gamma=\frac{\Delta S}{H_0}=\tan\varphi
$$

For small strains $\tan\varphi\approx\varphi$, with $\varphi$ in radians, so $\gamma\approx\varphi$. This definition assumes the block does not rotate; a free material element generally does, and Statics 2 uses a more complete definition ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain|B2]]).

Shear stress and shear strain are related by a law of the same form as Hooke's:

$$
\tau=G\gamma
$$

where $G$ is the **shear modulus**. It is not an independent property: for an isotropic material

$$
G=\frac{E}{2(1+\nu)}
$$

so only two elastic constants, $E$ and $\nu$, are needed. The derivation needs the multi-dimensional stress and strain of Statics 2 and is given in [[FEEG1002 B3 - Generalised Hooke's Law|B3]]. For steel with $E=210$ GPa and $\nu=0.3$, $G=210/2.6=80.8$ GPa.

![[s1_stress_strain_definitions.png|900]]

---

## Worked examples

### Worked example - off-centre container

A portal crane with legs 8 m apart lifts a 25 t container whose centre hangs 6 m from leg A and 2 m from leg B. The crane's own weight is ignored. The container weight is $F_G=25\,000\times9.81=245.3$ kN, so

$$
F_B=\frac{b}{b+c}F_G=\frac68(245.3)=183.9\ \mathrm{kN}
$$

$$
F_A=\frac{c}{b+c}F_G=\frac28(245.3)=61.3\ \mathrm{kN}
$$

Leg B, nearer the load, carries three times as much as leg A, and $F_A/F_B=c/b=1/3$ as the lever rule predicts.

### Worked example - crane tipping

Tutorial 1 Q1 is a mobile crane of mass 5000 kg with a box hanging 4 m in front of the front axle A; the crane's centre of gravity is 3 m behind A and the rear axle B is 5 m behind A (L1, ll. 839–851). Find the largest box mass before it tips, and the axle loads for a 1000 kg box.

![[s1_crane_tipping_fbd.png|900]]

As the box gets heavier the rear axle is unloaded. Tipping begins when $F_B$ reaches zero and the crane pivots about A. Take moments about A so that $F_A$ drops out, with the box's moment (clockwise, in front) against the crane's and the rear axle's (anticlockwise, behind):

$$
4F_{G,box}+0\cdot F_A-3F_{G,crane}+5F_B=0
$$

Set $F_B=0$ at the point of tipping:

$$
4m_{box}g=3m_{crane}g
$$

$$
m_{box}=\tfrac34(5000)=3750\ \mathrm{kg}
$$

With a 1000 kg box the same moment equation gives the rear axle load:

$$
F_B=\frac{3(5000)g-4(1000)g}{5}=21.6\ \mathrm{kN}
$$

and vertical equilibrium gives the front axle load:

$$
F_A=(1000+5000)g-F_B=58.9-21.6=37.3\ \mathrm{kN}
$$

> [!check] Moments about B as a cross-check
> About the rear axle, the box is 9 m away and the crane's centre of gravity 2 m away, both on the same side, while $F_A$ acts at 5 m: $5F_A=9(1000)g+2(5000)g=186.4$ kN m, so $F_A=37.3$ kN.

### Worked example - bolt clamping force

Tutorial 1 Q3: a steel bolt of diameter 6 mm and length 350 mm, $E=209$ GPa, clamps two plates assumed perfectly rigid; the thread has a pitch of 0.5 mm per turn. How many turns of the nut produce a clamping force of 4000 N? (L2, ll. 570–577.)

The bolt is a bar in uniaxial tension. Its area and stress are

$$
A=\frac{\pi(0.006)^2}{4}=2.827\times10^{-5}\ \mathrm{m^2}
$$

$$
\sigma=\frac FA=\frac{4000}{2.827\times10^{-5}}=141.5\ \mathrm{MPa}
$$

The strain and extension follow from Hooke's law:

$$
\varepsilon=\frac\sigma E=\frac{141.5\times10^6}{209\times10^9}=6.77\times10^{-4}
$$

$$
\Delta L=\varepsilon L_0=6.77\times10^{-4}\times350=0.237\ \mathrm{mm}
$$

With rigid plates every bit of nut travel stretches the bolt, so the number of turns is $0.237/0.5=0.47$, about half a turn.

In reality the plates are compressed as well. The same nut travel is then shared between stretching the bolt and squashing the plates, so the bolt stretches less and the clamping force is smaller than 4000 N; the nut has to be turned further.

### Worked example - Poisson contraction of a steel bar

A steel bar of diameter 20 mm and length 1 m carries 50 kN in tension; $E=210$ GPa and $\nu=0.3$.

$$
\sigma=\frac{50\,000}{\pi(0.02)^2/4}=159.2\ \mathrm{MPa}
$$

$$
\varepsilon_{xx}=\frac{159.2\times10^6}{210\times10^9}=7.58\times10^{-4},\qquad \Delta L=0.758\ \mathrm{mm}
$$

$$
\varepsilon_{yy}=-\nu\varepsilon_{xx}=-2.27\times10^{-4},\qquad \Delta D=-2.27\times10^{-4}\times20=-4.5\ \mu\mathrm m
$$

The bar lengthens by three-quarters of a millimetre and its diameter shrinks by under five micrometres. The stress is below the 250 MPa yield of A36 steel, so the linear elastic law applies.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Next: [[FEEG1002 A2 - Pin-Jointed Trusses]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Stress, Strain and Young's Modulus]] · [[Stress Concentration Factor and Factor of Safety]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 A2 - Pin-Jointed Trusses|A2]] (bar forces and $\Delta L=FL/EA$) · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams|A3]] (cutting a beam to reveal internal forces) · [[FEEG1002 B3 - Generalised Hooke's Law|B3]] (Hooke's law in 3D and the origin of $G=E/2(1+\nu)$) · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation|C4]] (where yield and UTS come from)
- Year 2: bar strain energy in [[SESA2028 S7 - Strain Energy and Conservation of Energy]]; the bar stiffness $EA/L$ as the element of [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]; a crack as the extreme stress raiser in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]

## Sources

- `Lecture 01 - Forces and Equilibrium.pdf` (S1 Lectures 1a–1b, 19 slides) and `Lecture 02 - Stress and Strain.pdf` (S1 Lectures 2a–2b, 22 slides), read in full.
- `FEEG1002 Lecture 1 - Statics 1 - Forces and equilibrium_07 October 2024.txt` (Lecture 1): strength and stiffness (ll. 33–60), Newton's third law (ll. 61–75), external and internal forces (ll. 76–111), FBDs (ll. 112–183), equilibrium (ll. 184–352), seesaw (ll. 365–578), symmetric portal crane (ll. 579–680), off-centre load and extreme cases (ll. 682–834), tutorial (ll. 839–851).
- `FEEG1002 Lecture 2 - Statics 1 - Stress and Strain_08 October 2024.txt` (Lecture 2): stress (ll. 21–64), yield, UTS and safety factor (ll. 65–117), stress concentration (ll. 118–172), shear stress and the hinge tutorial (ll. 173–229), stress vector (ll. 230–270), strain (ll. 271–342), Young's modulus and Hooke's law (ll. 343–437), bar stiffness (ll. 438–470), Poisson's ratio (ll. 471–510), shear strain and $G$ (ll. 511–569), bolt tutorial (ll. 570–577).
- Tutorial Sheet 01 and its official solutions: Q1–Q3 and the three additional problems.
- All numbers in the worked examples were recomputed in Python.

## Self-study tasks

### Core

- [ ] Predict what happens to the leg reactions as the container moves towards B, then confirm with the extreme cases $b=0$ and $c=0$ (L1, ll. 685–705 and 805–834). → [[#Load off centre: the lever rule]]
- [ ] Tutorial 1 Q1: maximum box mass and axle loads for the crane on wheels (set in L1, ll. 839–851). Targets 3750 kg; 37.3 kN and 21.6 kN. → [[#Worked example - crane tipping]] · [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Q1 - Crane with a suspended box|Tutorial 1 Q1]]
- [ ] Tutorial 1 Q2: size the rod and pin of the hinge to be equally strong, and list what else matters (set in L2, ll. 220–229). Targets 4.0 mm and 3.6 mm. → [[#Worked example - equally strong rod and pin]] · [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Q2 - Pinned hinge|Tutorial 1 Q2]]
- [ ] Tutorial 1 Q3: turns of the nut for a 4000 N clamping force, and the effect of compliant plates (set in L2, ll. 570–577). Target 0.47 turns. → [[#Worked example - bolt clamping force]] · [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Q3 - Bolt clamping force|Tutorial 1 Q3]]

### Further practice

- [ ] Tutorial 1 additional Q1: FBDs and counterweight of the bascule bridge. Target 50 t. → [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Extra Q1 - Bascule bridge|Tutorial 1 Extra Q1]]
- [ ] Tutorial 1 additional Q2: force to punch a 12 mm hole in 2 mm sheet. Target 15.08 kN. → [[#Shear stress]] · [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Extra Q2 - Hole punch|Tutorial 1 Extra Q2]]
- [ ] Tutorial 1 additional Q3: Young's modulus of a bar loaded through a mid-length collar. Target 64.81 MPa. → [[#A bar is a spring]] · [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions#Extra Q3 - Bar loaded through a collar|Tutorial 1 Extra Q3]]
- [ ] Explain why drilling a hole in a loaded plate raises the local stress, and where the peak sits (raised in L2, ll. 142–145). → [[#Stress concentrations]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 1, ll. 196–203, 453–455, 716 and 770)
> Where: [[#Static means no acceleration]] · [[#Example: the seesaw, and choosing the moment point]] · [[#3. The portal crane]].
>
> Newton's first law is first stated as "no external force, so no acceleration" and its converse; it is the resultant external force that must vanish, as l. 219 then says. The moment of the right-hand box is called anticlockwise at ll. 453–455; it is clockwise (l. 447), and the minus sign in the equation is right. At l. 716 vertical equilibrium is said to include "the crane and the box", but the slide equation $F_G=F_A+F_B$ contains only the container, with the crane's weight ignored. At l. 770 the denominator is read as "b plus g"; it is $b+c$.

> [!warning] Transcript slips (Lecture 2, ll. 84, 108, 144–145 and 466)
> Where: [[#Allowable stress and safety factor]] · [[#Stress concentrations]] · [[#A bar is a spring]].
>
> The 25 kg wire is said to have a cross-section of "one millimeter"; it is one square millimetre. The safety factor is said to be "always larger than two"; the slide condition is $K_{SF}>1$. A hole is said to make the structure "three times less strong"; $K_T=3$ is the ratio of the peak stress at the hole edge to the far-field stress in a wide plate, not a general factor on strength. At l. 466 the 1 m bar is stretched to "one millimeter"; the example uses one centimetre (1 % strain).
