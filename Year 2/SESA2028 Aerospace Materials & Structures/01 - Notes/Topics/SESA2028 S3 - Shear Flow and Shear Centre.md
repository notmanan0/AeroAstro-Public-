---
title: "SESA2028 S3 - Shear Flow and Shear Centre"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 3
tags: [sesa2028, structures, shear-flow, shear-centre, thin-walled]
date: 2026-10-30
status: lectured
coverage: "SL8 (2026-02-27, ll. 290–438), SL9 (2026-03-04), SL10 (2026-03-11)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
next_topics: ["[[SESA2028 S4 - Torsion of Thin-Walled Sections]]"]
key_concepts: ["[[Shear Flow]]", "[[Shear Centre]]", "[[First Moment of Area]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 2 - Bending Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL3 Shear stresses in beams under shear force.pdf", "02 - Sources/Structures Lectures/Structures Additional session-Shear.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-27.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-04.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-11 - SL10 shear. torsion.txt"]
---

# SESA2028 S3 - Shear Flow and Shear Centre

> [!abstract] Summary
> A shear force is not spread evenly over a beam's section: equilibrium of a small slice links the shear stress to the rate of change of bending stress along the beam, giving $\tau=Q\bar yA/(I_zt)$, parabolic in a rectangle and peaking at 1.5 times the average. In thin-walled sections the product $q=\tau t$, the shear flow, is constant across the wall and adds up at junctions like a fluid; starting from a free edge gives its distribution in an open section, and a closed section is cut to make it open, with the unknown flow at the cut found from moment equilibrium. The shear centre is the point through which a load produces no twist; for unsymmetrical sections it is not the centroid and may lie outside the section.

> [!summary]- Exam use: quick path
> - **Use it when:** a thin-walled open or closed section carries a shear force and you need the shear-stress distribution, its maximum or the shear centre.
> - **Assumptions:** thin walls ($t$ small, $\tau$ uniform across $t$ and parallel to the wall), linear elastic, $y$ downward and $z$ to the right through the centroid, $s$ measured along each wall from its start.
> - **Method:** 1. Section properties. 2. Start at a free edge ($q=0$), or cut a closed section and add an unknown $q_0$. 3. $q(s)=q_{out}-\frac{Q_yI_y-Q_zI_{yz}}{\Delta}\int ty\,ds-\frac{Q_zI_z-Q_yI_{yz}}{\Delta}\int tz\,ds$ wall by wall, carrying flows through junctions. 4. $q_0$ (closed) and the shear centre from moments of the wall forces. 5. $\tau=q/t$; check that the wall forces add up to the applied shear.
> - **Common mistakes:** losing the sign of $\bar y$ or $\bar z$ for the swept area; assuming the shear centre is at the centroid.
> - **Practise:** [[#Worked example: a square box loaded off-centre]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.4 - Shear-flow distribution|Tutorial 2 Q1.4]]

When a deck of cards is bent, the loose cards slide over each other. With the cards glued together, the glue has to carry a shear force to stop the sliding, and it carries most where the bending stress on one side of it changes fastest along the beam. In a thin-walled section the glue line runs along the wall, the shear force per unit length along it is the shear flow, and, like water in pipes, the flow must balance at every junction.

All those internal flows have a resultant, and the line it acts along is fixed by the section's geometry, not by where the load happens to be applied. That point is the shear centre. A load applied through it bends the section without twisting; a load applied anywhere else adds an offset torque that twists it. For a symmetric section the shear centre sits on the axis of symmetry, but for a channel it lies outside the section altogether.

## 1. Shear stress varies over the section

At a section carrying a shear force $Q$, the shear stress cannot be uniform at $Q/A$. At the top and bottom free surfaces nothing outside balances a shear stress, so by complementary shear it must be zero there. Finite-element contours of a tip-loaded cantilever show the bending stress varying linearly through the depth, and the shear stress near zero at the surfaces and largest at mid-depth. With the tip loaded instead by an equal and opposite pair of forces, a pure moment, the shear stress is essentially zero away from the end, apart from local disturbances near the load and small numerical error: shear stress comes from the shear force, that is, from the bending moment changing along the beam.

## 2. Shear stress in a rectangle

A slice of the beam $dx$ long, cut horizontally at height $y$, has a part beyond the cut of cross-sectional area $A$. Its two end faces carry bending stresses $\sigma_{xx}$ and $\sigma_{xx}+d\sigma_{xx}$, and the horizontal cut face, of width $t$ and length $dx$, carries a shear stress $\tau$. Axial force equilibrium of that part:

$$
\tau t\,dx=\int_A\left(\sigma_{xx}+d\sigma_{xx}\right)dA-\int_A\sigma_{xx}\,dA=\int_Ad\sigma_{xx}\,dA .
$$

Divide by $t\,dx$:

$$
\tau=\frac1t\int_A\frac{\partial\sigma_{xx}}{\partial x}\,dA .
$$

With $\sigma_{xx}=M_zy/I_z$, only $M_z$ changes along a prismatic beam:

$$
\frac{\partial\sigma_{xx}}{\partial x}=\frac{y}{I_z}\frac{dM_z}{dx}=\frac{Qy}{I_z},
$$

using $dM_z/dx=Q$ (the course sign convention). So

$$
\tau=\frac{Q}{I_zt}\int_Ay\,dA=\frac{Q\bar yA}{I_zt},
$$

where $\bar yA$ is the first moment, about the neutral axis, of the area beyond the cut ([[First Moment of Area]]).

For a rectangle of depth $h$ and width $t$, the area from the cut at $y$ to the surface at $h/2$ has

$$
\int_Ay\,dA=t\int_y^{h/2}\eta\,d\eta=\frac t2\left(\frac{h^2}{4}-y^2\right).
$$

So

$$
\tau=\frac{Q}{I_zt}\cdot\frac t2\left(\frac{h^2}{4}-y^2\right)=\frac{Q}{2I_z}\left(\frac{h^2}{4}-y^2\right),
$$

parabolic, and zero at the surfaces $y=\pm h/2$ as required. At the neutral axis, with $I_z=th^3/12$,

$$
\tau_{max}=\frac{Qh^2}{8I_z}=\frac{Qh^2}{8}\cdot\frac{12}{th^3}=\frac32\frac{Q}{th},
$$

1.5 times the average, so designing for the average shear stress is unconservative.

For a cantilever of length $L$ under a tip load $Q$, the largest bending stress is at the root, $\sigma_{max}=M c/I=QL(h/2)/(th^3/12)=6QL/th^2$, so

$$
\frac{\tau_{max}}{\sigma_{max}}=\frac{3Q/2th}{6QL/th^2}=\frac{h}{4L}.
$$

For a slender beam, $L>10h$ as a rule of thumb, the shear stress is under 2.5 % of the bending stress, and the shear deflection is similarly small ([[SESA2028 S7 - Strain Energy and Conservation of Energy#Shear deflection of a cantilever|S7]]), which is why Euler–Bernoulli theory works. Deep beams need Timoshenko theory, which includes shear. The two maxima also occur in different places, bending at the outer fibres and shear at mid-depth.

> [!warning] Bending and shear can still combine
> Treating bending and shear separately because they peak in different places works for a solid rectangle. In an I-section, though, the web just inside the flange carries a high bending stress and a high shear stress together, because the flanges add a large first moment above the web. A combined check (von Mises or Tresca) is still needed there.

## 3. Shear flow in thin-walled sections

For a thin wall the shear stress is uniform across the thickness $t$ and parallel to the wall, and the shear flow $q=\tau t$, a force per unit length, is the natural variable. Measure $s$ along the wall from its start. Axial equilibrium of the strip of wall between $s=0$ and $s$, taken as for the slice of the rectangle, gives

$$
q(s)\,dx-q_{out}\,dx+\int_0^st\,\frac{\partial\sigma_{xx}}{\partial x}\,dx\,ds=0,
$$

where $q_{out}$ is the flow entering at $s=0$. Divide by $dx$:

$$
q(s)=q_{out}-\int_0^st\frac{\partial\sigma_{xx}}{\partial x}\,ds .
$$

Now differentiate the general bending stress of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#4. The general bending stress|S1]] along $x$. Only the moments vary, with $dM_z/dx=Q_y$ and $dM_y/dx=Q_z$:

$$
\frac{\partial\sigma_{xx}}{\partial x}=\frac{\left(Q_yI_y-Q_zI_{yz}\right)y+\left(Q_zI_z-Q_yI_{yz}\right)z}{I_yI_z-I_{yz}^2}.
$$

Substitute; the brackets are constants, so they come outside the integral, leaving $\int_0^sty\,ds$ and $\int_0^stz\,ds$, the first moments $\bar yA$ and $\bar zA$ of the swept wall area:

$$
\boxed{q(s)=q_{out}-\frac{Q_yI_y-Q_zI_{yz}}{I_yI_z-I_{yz}^2}\,\bar yA-\frac{Q_zI_z-Q_yI_{yz}}{I_yI_z-I_{yz}^2}\,\bar zA}
$$

The overall sign depends on the shear-force convention and the direction of $s$; the shape of the distribution and the balance at junctions do not, and a final check that the wall forces add up to the applied shear catches sign errors. The formula applies only to thin walls ([[Shear Flow]]).

In an open section, start at a free edge, where $q_{out}=0$ because no external stress acts on the free face. For an angle, define $s_1$ along one leg from its free end: the swept area is $A=s_1t$, and $\bar y$, $\bar z$ are the distances of that strip's centroid from the section centroid, taken with their signs ($y$ down, $z$ right). The signs are where most mistakes are made. Repeat from the other free end with $s_2$.

At a junction the flows add like fluid in pipes. In an I-section, the flows from the two half-flanges arriving at the web junction add to give the $q_{out}$ that enters the web:

$$
q_{out,25}=q_{12}\!\left(\tfrac w2\right)+q_{32}\!\left(\tfrac w2\right).
$$

Within a wall, $dq/ds\propto-\partial\sigma_{xx}/\partial x$, so the shear flow is extreme where the wall crosses the neutral axis, where $\sigma_{xx}$ and its $x$-derivative change sign. In a symmetric section that is the centroid's height; in an unsymmetrical one it is wherever the tilted neutral axis cuts the wall.

### Example: the angle-section cantilever

The angle-section cantilever of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#Worked example: an angle-section cantilever|S1]] (1 m long, 10 kN/m, $I_z=24.2$, $I_y=6.6$, $I_{yz}=7.2\times10^6$ mm⁴, 20 mm walls) carries its largest shear force at the root, $Q_y=wL=10$ kN, with $Q_z=0$. Where is the bending shear stress largest?

With $Q_z=0$ the coefficients are

$$
\frac{Q_yI_y}{\Delta}=\frac{10^4\times6.6\times10^6}{107.9\times10^{12}}=6.12\times10^{-4}\ \text{N/mm}^{4},\qquad\frac{Q_yI_{yz}}{\Delta}=6.67\times10^{-4}\ \text{N/mm}^{4}.
$$

Model each leg by its centreline. The web centreline is at $z=20$ mm; measure $s$ up from its free bottom end at $y=130$ mm, so a point on the web is at $y=130-s$. The swept strip has $\int ty\,ds=20(130s-s^2/2)$ and $\int tz\,ds=20\times20\,s$, so

$$
q_{web}(s)=-6.12\times10^{-4}\times20\left(130s-\frac{s^2}{2}\right)+6.67\times10^{-4}\times400\,s=-1.324\,s+0.00612\,s^2\ \text{N/mm}.
$$

Its magnitude is largest where $dq/ds=0$:

$$
-1.324+0.01224\,s=0\quad\Longrightarrow\quad s=108.2\text{ mm},\quad y=130-108.2=21.8\text{ mm},
$$

which is exactly where the web crosses the neutral axis $y=1.09z$ at $z=20$. There

$$
|q|_{max}=1.324(108.2)-0.00612(108.2)^2=71.6\text{ N/mm},\qquad\tau_{max}=\frac{71.6}{20}=3.6\text{ MPa}.
$$

The flange, swept from its free tip at $z=-90$ along $y=-60$, carries at most 29 N/mm. So the maximum bending shear stress is in the web, 22 mm below the centroid, at about twice the average $Q/A=10\,000/6000=1.67$ MPa.

> [!check] Wall forces
> Integrating $q_{web}$ over the web's 190 mm length gives 9.9 kN, against the 10 kN applied; the flange carries a net horizontal force of only 0.13 kN. The 1 % shortfall is the centreline model of 20 mm thick walls, which overlaps and misses small areas at the corner.

![[structures_s3_angle_and_box_shear_flow.png|900]]

## 4. Closed sections

A closed section has no free edge, so no starting point where $q=0$ is known. Make a fictitious hairline cut anywhere: the section is now open, and $q_b(s)$ follows from the open-section formula with $q_{out}=0$ at the cut. The real section has no cut, so add a constant unknown flow $q_0$ all round:

$$
q(s)=q_b(s)+q_0 .
$$

A constant flow round a closed loop has no resultant force, so it does not upset force equilibrium, but it does have a moment. $q_0$ therefore comes from moment equilibrium: the moment of the wall forces about any point, usually the centroid, must equal the moment of the applied shear about the same point.

A shear load can produce two kinds of shear deformation, a twist of the section in its plane and a warping out of it, and the total shear strain is their sum. If the load passes through the shear centre of a closed section there is no twist, though there can be warping. The shear strain is $\tau/G=q/Gt$, and going once round the closed wall the warping displacement must return to its starting value, which with no twist gives a second condition:

$$
\oint\frac{\tau}{G}\,ds=0\quad\Longrightarrow\quad\oint\frac{q}{Gt}\,ds=0 .
$$

This can also fix $q_0$ when the load acts at the shear centre. $t$ may vary with $s$, but the wall must stay thin.

## 5. The shear centre

The shear centre is the point through which a shear load causes no twist ([[Shear Centre]]). If a section is symmetric about an axis, the shear centre lies on that axis, and if it is doubly symmetric it coincides with the centroid. For sections made of straight walls meeting at one point (an angle, a T), every wall force passes through that point, so the shear centre is at the junction. Otherwise it must be calculated, and it can lie outside the section, as for a channel.

The procedure is to find the shear-flow distribution, integrate it along each wall to get the wall forces ($q$ varies, so integrate rather than multiply by a length), and take moments about a convenient point: the applied shear, placed at the shear centre, must produce the same moment as the wall forces. A load applied elsewhere, at distance $e$ from the shear centre, is equivalent to the same load at the shear centre plus a torque $Qe$, which twists the section; the shear flows of the two parts superpose ([[SESA2028 S4 - Torsion of Thin-Walled Sections|S4]]).

### Channel section

A channel has web height $h$, flange width $b$ and uniform thickness $t$ (centreline dimensions), loaded by $Q_y$. It is symmetric about $z$, so $I_{yz}=0$ and the shear centre lies on the axis of symmetry. Start at a flange tip, where $q=0$, and measure $s$ along the flange. The flange is at $|y|=h/2$, so the swept first moment is $t\,(h/2)\,s$ and

$$
q(s)=\frac{Q_y}{I_z}\,t\,\frac h2\,s .
$$

The flow grows linearly to the corner. The flange force is its integral:

$$
F_{flange}=\int_0^bq\,ds=\frac{Q_yth}{2I_z}\cdot\frac{b^2}{2}=\frac{Q_yth\,b^2}{4I_z}.
$$

The two flange forces are equal and opposite, a couple of arm $h$, and the web carries $Q_y$. Take moments about the web centreline, where the web force has no arm: the applied shear at distance $e$ must balance the couple,

$$
Q_ye=F_{flange}h\quad\Longrightarrow\quad e=\frac{th^2b^2}{4I_z},
$$

on the side of the web away from the flanges. With the thin-walled second moment

$$
I_z=\frac{th^3}{12}+2bt\left(\frac h2\right)^2=\frac{th^2(h+6b)}{12},
$$

this becomes

$$
e=\frac{th^2b^2}{4}\cdot\frac{12}{th^2(h+6b)}=\frac{3b^2}{h+6b}.
$$

For the SL3 example, $d=300$ mm, $b=100$ mm and $t=10$ mm: $I_z=22.5\times10^6+45\times10^6=67.5\times10^6$ mm⁴ and

$$
e=\frac{3\times100^2}{300+600}=33.3\text{ mm}
$$

outside the web. A torsion test locates the same offset experimentally ([[SESA2028 S2 - Beam Deflection and Bending Design#Torsion test: locating the shear centre|S2]]).

> [!check] Limits of the channel formula
> As $b\to0$ the channel becomes a flat strip and $e\to0$: the shear centre returns to the web, as it must for a single straight wall. As $b\to\infty$, $e\to b/2$, the middle of the flanges.

## Worked example: a square box loaded off-centre

A square box, 100 × 100 mm on the centreline with 2 mm walls, carries 8 kN vertically, acting in the plane of one vertical wall. Sketch the shear-stress distribution and find the maximum.

The box is doubly symmetric, so its shear centre is at its centre, and the load is 50 mm from it. Move the load to the shear centre and add the torque:

$$
T=Q_ye=8000\times50=4\times10^5\text{ N mm}.
$$

### Shear through the centre

With $Q_z=0$ and $I_{yz}=0$, $q=q_{out}-(Q_y/I_z)\bar yA$. The thin-walled second moment, two webs plus two flanges at $\pm50$ mm:

$$
I_z=2\times\frac{2\times100^3}{12}+2\times(100\times2)\times50^2=0.333\times10^6+1.0\times10^6=1.333\times10^6\text{ mm}^4,
$$

so $Q_y/I_z=8000/1.333\times10^6=0.006$ N/mm⁴. By symmetry the flow is zero at the middle of each flange, so take the cuts there. Along a half flange from its middle, the swept area $2s$ sits at $|y|=50$ mm, and at the corner ($s=50$ mm)

$$
q_{corner}=0.006\times(2\times50)\times50=30\text{ N/mm}.
$$

Down the web from the corner, the strip of length $s$ adds $\int_0^s2\,(50-\eta)\,d\eta=2(50s-s^2/2)$ to the first moment, which at the neutral axis ($s=50$) is $2500$ mm³:

$$
q_{web,max}=30+0.006\times2500=45\text{ N/mm}.
$$

Each web carries $\int q\,ds=100\times30+\tfrac23\times100\times15=4000$ N, so together they carry the 8 kN.

### Torque

A closed single cell carries a torque as a constant shear flow ([[SESA2028 S4 - Torsion of Thin-Walled Sections#Torque and shear flow|S4]]):

$$
q_T=\frac{T}{2A_e}=\frac{4\times10^5}{2\times100\times100}=20\text{ N/mm}.
$$

### Superposition

The torque flow runs the same way round the cell everywhere, so it adds to the bending flow in the loaded web and subtracts in the other: 65 N/mm and 25 N/mm at mid-height. The maximum shear stress is

$$
\tau_{max}=\frac{65}{2}=32.5\text{ MPa}
$$

at mid-height of the loaded web, against 12.5 MPa in the other web. Had the load acted through the centre, the maximum would have been $45/2=22.5$ MPa: the 50 mm offset raises it by 44 %.

> [!check] The single-cut route
> Cutting the wall once, at the bottom-flange midpoint, and finding $q_0$ from moment equilibrium about the centre gives the same total distribution, since the superposition above is just $q_0$ split into its symmetric (zero) and torque (20 N/mm) parts.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S2 - Beam Deflection and Bending Design]] · Next: [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
- Concepts: [[Shear Flow]] · [[Shear Centre]] · [[First Moment of Area]]
- Problems: [[SESA2028 Structures Tutorial 2 - Bending Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Year 1 foundation: [[FEEG1002 A9 - Shear Stresses in Beams]]

## Sources

- Slides: `SL3 Shear stresses in beams under shear force.pdf` (derivation, thin-walled shear flow, closed sections, shear centre; example 1 the angle section, example 2 the channel) and `Structures Additional session-Shear.pdf`.
- Transcripts: `SESA2028 Lecture 2026-02-27.txt` (ll. 290–438), `SESA2028 Lecture 2026-03-04.txt` and `SESA2028 Lecture 2026-03-11 - SL10 shear. torsion.txt` (closed sections and the box).
- The angle-section distribution, the channel offset and the box flows were computed in Python (SymPy for the web integral). Figures: `generate_structures_s3_figures.py`; the generic open-section sketch in `generate_structures_figures.py` is used by the concept notes.

## Self-study tasks

### Core

- [ ] Derive $\tau=Q\bar yA/I_zt$ and the parabolic distribution in a rectangle (2026-02-27, ll. 395–420). → [[#2. Shear stress in a rectangle]]
- [ ] SL3 example 1: where the maximum bending shear stress occurs in the angle-section cantilever, with the distribution sketched (posed with solutions linked, 2026-03-04, ll. 360–395). → [[#Example: the angle-section cantilever]]
- [ ] SL3 example 2: the shear centre of the channel, $d=300$, $b=100$, $t=10$ mm. → [[#Channel section]]
- [ ] Shear centres of the T and angle sections, left for you to think through (2026-03-04, ll. 300–310). → [[#5. The shear centre]]
- [ ] The square box under an off-centre load, and the similar tutorial problem (2026-03-11, ll. 151–420). → [[#Worked example: a square box loaded off-centre]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q2 - Closed rectangular box under vertical shear|Tutorial 2 Q2]]

### Further practice

- [ ] Show that $\tau_{max}/\sigma_{max}=h/4L$ for a tip-loaded rectangular cantilever (2026-03-04, ll. 1–45). → [[#2. Shear stress in a rectangle]]
- [ ] Redo the box with the load through the centre and confirm the 22.5 MPa maximum (suggested, not lecturer-set). → [[#Shear through the centre]]

## Transcript and slide slips

> [!warning] Slide error left in deliberately: the box torque (2026-03-11, ll. 241–270)
> Where: [[#Worked example: a square box loaded off-centre]].
>
> The SL10 box slide says the twisting moment is zero. The box is doubly symmetric, so its shear centre is at its centre and the load, 50 mm away, does twist it ($T=400$ N m). The error was left on the slide deliberately, to be spotted.

> [!warning] Lecture overstatement (2026-03-04, ll. 40–50)
> Where: [[#2. Shear stress in a rectangle]].
>
> Bending and shear stresses are said never to need combining because they peak in different places. That is true for a solid rectangle but not for an I-section; see the warning in that section.
