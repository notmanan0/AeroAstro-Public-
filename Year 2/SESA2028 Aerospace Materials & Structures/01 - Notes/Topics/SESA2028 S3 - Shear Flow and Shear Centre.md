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
sources: ["02 - Sources/Structures Lectures/SL3 Shear stresses in beams under shear force.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-27.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-04.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-11 - SL10 shear. torsion.txt"]
---

# SESA2028 S3 - Shear Flow and Shear Centre

> [!abstract] Summary
> A shear force is not spread evenly over a beam's section: equilibrium of a small slice links the shear stress to the rate of change of bending stress along the beam, giving the parabolic distribution $\tau=Q\bar yA/(I_zt)$ in a rectangle, peaking at 1.5 times the average. In thin-walled sections the product $q=\tau t$, the shear flow, is constant across the wall and adds up at junctions like a fluid, and starting from a free edge gives its distribution in an open section; a closed section is cut to make it open, and the unknown flow at the cut is found from moment equilibrium. The shear centre is the point through which a load produces no twist; for unsymmetrical sections it is not the centroid and may lie outside the section.

> [!summary]- Exam use: quick path
> - **Use it when:** a thin-walled open or closed section carries a shear force and you need the shear-stress distribution, its maximum or the shear centre.
> - **Assumptions:** thin walls ($t$ small, $\tau$ uniform across $t$), linear elastic, $y$ downward and $z$ to the right, shear flow measured along $s$ from the start of each wall.
> - **Method:** 1. Section properties. 2. Start at a free edge ($q=0$), or cut a closed section and add an unknown $q_0$. 3. $q(s)=q_{out}-\frac{Q_yI_y-Q_zI_{yz}}{\Delta}\int ty\,ds-\frac{Q_zI_z-Q_yI_{yz}}{\Delta}\int tz\,ds$ wall by wall, carrying flows through junctions. 4. Find $q_0$ (closed) and the shear centre by moments of the wall forces. 5. $\tau=q/t$.
> - **Common mistakes:** losing the sign of $\bar y$ or $\bar z$ for the swept area; assuming the shear centre is at the centroid.
> - **Practise:** [[#Worked example: a square box loaded off-centre]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.4 - Shear-flow distribution|Tutorial 2 Q1.4]]

Shear was introduced at the end of SL8 and developed over SL9 and SL10 (2026-02-27, ll. 290–438; 2026-03-04; 2026-03-11). The slides now match the Blackboard version exactly, and the worked examples link directly to their solution PDFs and videos (2026-02-27, ll. 290–330).

When a deck of cards is bent, loose cards slide over each other; if they are glued, the glue has to carry a shear force to stop them sliding, and it carries most where the most bending stress builds up on one side of it. In a thin-walled section the "glue line" runs along the wall, the shear force per unit length along it is the shear flow, and like water in pipes it must balance at every junction. Where all those internal flows, added up, exert their resultant is the shear centre: push there and the section bends without twisting; push anywhere else and an extra torque twists it.

## 1. Shear stress varies over the section

At a section carrying a shear force $Q$, the shear stress cannot simply be $Q/A$: at the top and bottom free surfaces it must be zero, since nothing outside balances it (2026-02-27, ll. 340–380). Finite-element contours of a tip-loaded cantilever show the bending stress varying linearly through the depth and the shear stress near zero at the surfaces and largest at mid-depth. Load the tip with an equal and opposite pair of forces instead, a pure moment, and the shear stress is essentially zero away from the end, apart from local disturbances near the load and small numerical error (ll. 360–395).

## 2. Shear stress in a rectangle

Take a slice $dx$ long and cut it horizontally at height $y$; consider the part beyond the cut, of area $A$ (slides; ll. 395–420). Its end faces carry bending stresses $\sigma_{xx}$ and $\sigma_{xx}+d\sigma_{xx}$, and the cut face of width $t$ carries a shear stress $\tau$. Axial equilibrium of that part gives

$$
\tau t\,dx=\int_Ad\sigma_{xx}\,dA
\quad\Longrightarrow\quad
\tau=\frac1t\int_A\frac{\partial\sigma_{xx}}{\partial x}\,dA .
$$

With $\sigma_{xx}=M_zy/I_z$ and $dM_z/dx=Q$ (the slide sign convention),

$$
\tau=\frac{Q}{I_zt}\int_Ay\,dA=\frac{Q\bar yA}{I_zt},
$$

where $\bar yA$ is the first moment about the neutral axis of the area beyond the cut ([[First Moment of Area]]). For a rectangle of depth $h$ and width $t$, the area from the cut at $y$ to the surface at $h/2$ has $\int y\,dA=t\int_y^{h/2}\eta\,d\eta$, so

$$
\tau=\frac{Q}{I_zt}\cdot\frac t2\left(\frac{h^2}{4}-y^2\right)=\frac{Q}{2I_z}\left(\frac{h^2}{4}-y^2\right),
$$

parabolic, zero at the surfaces. At the neutral axis, with $I_z=th^3/12$,

$$
\tau_{max}=\frac{Qh^2}{8I_z}=\frac{3}{2}\frac{Q}{th},
$$

1.5 times the average, so designing for the average shear stress is unconservative (2026-03-04, ll. 1–10).

For a cantilever of length $L$ under a tip load, $\sigma_{max}=6QL/th^2$, so

$$
\frac{\tau_{max}}{\sigma_{max}}=\frac{3Q/2th}{6QL/th^2}=\frac{h}{4L}.
$$

For a slender beam, $L>10h$ as a rule of thumb, the shear stress is small compared with the bending stress, as is the shear deflection, which is why Euler–Bernoulli theory works; deep beams need Timoshenko theory, which includes shear (ll. 1–45). The two maxima also occur in different places, bending at the outer fibres and shear at mid-depth.

> [!warning] Lecture overstatement (2026-03-04, ll. 40–50)
> "You don't need to try and combine the bending stress and shear stress" because they peak in different places. That holds for a solid rectangle, but in an I-section the web just inside the flange carries high bending stress and high shear stress together, so a combined check (von Mises or Tresca) is still needed there.

## 3. Shear flow in thin-walled sections

For a thin wall the shear stress is uniform across the thickness $t$ and parallel to the wall, and the shear flow $q=\tau t$ (force per unit length) is the natural variable (2026-03-04, ll. 61–120). Measure $s$ along the wall. The same slice equilibrium gives

$$
q(s)=q_{out}-\int_0^st\frac{\partial\sigma_{xx}}{\partial x}\,ds,
$$

where $q_{out}$ is the flow entering at $s=0$. Differentiate the general bending stress of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending|S1]] along $x$ with $dM_z/dx=Q_y$ and $dM_y/dx=Q_z$:

$$
\frac{\partial\sigma_{xx}}{\partial x}=\frac{\left(Q_yI_y-Q_zI_{yz}\right)y+\left(Q_zI_z-Q_yI_{yz}\right)z}{I_yI_z-I_{yz}^2}.
$$

Substitute, recognising $\int ty\,ds=\bar yA$ and $\int tz\,ds=\bar zA$ for the swept area:

$$
\boxed{q(s)=q_{out}-\frac{Q_yI_y-Q_zI_{yz}}{I_yI_z-I_{yz}^2}\,\bar yA-\frac{Q_zI_z-Q_yI_{yz}}{I_yI_z-I_{yz}^2}\,\bar zA}
$$

The overall sign depends on the shear-force convention and the direction of $s$; the shape of the distribution and the balance at junctions do not, and a final check that the wall forces add up to the applied shear catches sign errors. It applies only to thin walls ([[Shear Flow]]).

In an open section, start at a free edge, where $q_{out}=0$ because no external stress acts on the free face (ll. 121–180). For an angle, define $s_1$ along one leg from its free end: $A=s_1t$, and $\bar y$, $\bar z$ are the distances of that strip's centroid from the section centroid, taken with their signs ($y$ down, $z$ right), "the point where many students make mistakes". Repeat from the other free end with $s_2$.

At a junction the flows add like fluid in pipes (ll. 181–240). In an I-section, the flows from the two half-flanges arriving at the web junction add to give the $q_{out}$ that enters the web:

$$
q_{out,25}=q_{12}\!\left(\tfrac w2\right)+q_{32}\!\left(\tfrac w2\right).
$$

## 4. Closed sections

A closed section has no free edge, so no starting point where $q=0$ (2026-03-11, ll. 1–90). Make a fictitious hairline cut anywhere: the section is now open and $q_b(s)$ follows from the open-section formula with $q_{out}=0$ at the cut. The real section has no cut, so add a constant unknown flow $q_0$ all round:

$$
q(s)=q_b(s)+q_0 .
$$

$q_0$ comes from moment equilibrium: the moments of the wall forces about any point, usually the centroid, must equal the moment of the applied shear about the same point.

Shear load can produce two kinds of shear deformation: twist of the section in its plane and warping out of it, the total shear strain being the sum (ll. 91–120). If the load passes through the shear centre of a closed section there is no twist, though there can be warping; with $\tau/G$ the shear strain round the wall, this gives a second condition (ll. 121–150):

$$
\oint\frac{\tau}{G}\,ds=0
\quad\Longrightarrow\quad
\oint\frac{q}{Gt}\,ds=0,
$$

which can also fix $q_0$ when the load acts at the shear centre. $t$ may vary with $s$, but the wall must stay thin.

## 5. The shear centre

The shear centre is the point through which a shear load causes no twist (2026-03-04, ll. 213–300; [[Shear Centre]]). If a section is symmetric about an axis, the shear centre lies on it, and if doubly symmetric it coincides with the centroid; for sections made of straight walls meeting at one point (an angle, a T), it lies approximately at the junction, since all the wall forces pass through it. Otherwise it must be calculated and can lie outside the section, as for a channel.

The procedure is to find the shear-flow distribution, integrate it along each wall to get the wall forces ($q$ varies, so integrate rather than multiply by length), and take moments about a convenient point: the applied shear placed at the shear centre must produce the same moment as the wall forces (ll. 300–390). A load applied elsewhere, at distance $e$ from the shear centre, is equivalent to the same load at the shear centre plus a torque $Qe$, which twists the section; the shear flows from the two superpose ([[SESA2028 S4 - Torsion of Thin-Walled Sections|S4]]; 2026-03-11, ll. 151–210).

For a channel with web height $h$, flange width $b$ and uniform thickness $t$, loaded by $Q_y$, $I_{yz}=0$ by symmetry, and from a flange tip

$$
q(s)=\frac{Q_y}{I_z}\,t\,\frac h2\,s
\quad\Longrightarrow\quad
F_{flange}=\int_0^bq\,ds=\frac{Q_yth\,b^2}{4I_z}.
$$

The two flange forces are equal and opposite, a couple $F_{flange}h$; the web carries $Q_y$. Moments about the web centreline give the shear centre's distance $e$ from the web, on the side away from the flanges:

$$
Q_ye=F_{flange}h
\quad\Longrightarrow\quad
e=\frac{th^2b^2}{4I_z}.
$$

With $I_z=th^3/12+2bt(h/2)^2=th^2(h+6b)/12$,

$$
e=\frac{3b^2}{h+6b}.
$$

The lab measures this directly ([[SESA2028 S2 - Beam Deflection and Bending Design#5. The structures lab|S2]]). For $h=100$ mm and $b=50$ mm, $e=3\times2500/400=18.75$ mm outside the web.

## Worked example: a square box loaded off-centre

The SL10 problem (2026-03-11, ll. 151–420): a square box, 100 × 100 mm, wall thickness 2 mm, carries 8 kN acting in the plane of one vertical wall. Sketch the shear-stress distribution and find the maximum. The slide also says the twisting moment is zero, an error left in deliberately: the box is doubly symmetric, so its shear centre is at its centre, the load is 50 mm away from it, and the section twists (ll. 241–270).

Move the load to the shear centre and add the torque:

$$
T=Q_ye=8000\times50=4\times10^5\text{ N mm}.
$$

Shear through the centre. With $Q_z=0$ and $I_{yz}=0$, $q=q_{out}-(Q_y/I_z)\bar yA$. The second moment, thin-walled:

$$
I_z=2\times\frac{2\times100^3}{12}+2\times(100\times2)\times50^2=1.333\times10^6\text{ mm}^4,
$$

so $Q_y/I_z=0.006$ N/mm⁵. By symmetry the flow is zero at the middle of each flange, so cut there. Along a half flange from the cut, $\bar y=50$ mm and $A=2s$, reaching at the corner

$$
q_{corner}=0.006\times2\times50\times50=30\text{ N/mm}.
$$

Down the web, the strip from the corner adds $0.006\times2\times(50s-s^2/2)$, which at the neutral axis ($s=50$) is 15 N/mm:

$$
q_{web,max}=30+15=45\text{ N/mm}.
$$

Each web carries $\int q\,ds=100\times(30+\tfrac23\times15)=4000$ N, together the 8 kN.

Torque. A closed single cell carries torque as a constant shear flow ([[SESA2028 S4 - Torsion of Thin-Walled Sections|S4]]):

$$
q_T=\frac{T}{2A_e}=\frac{4\times10^5}{2\times100\times100}=20\text{ N/mm}.
$$

Superposed, the flow adds in the loaded web and subtracts in the other: 65 and 25 N/mm at mid-height. The maximum shear stress is

$$
\tau_{max}=\frac{65}{2}=32.5\text{ MPa}
$$

at mid-height of the loaded web, against 12.5 MPa in the other web (Python check). The lecture solves the same problem with a single cut at the bottom-flange midpoint and $q_0$ from moment equilibrium about the centre, which gives the same total.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S2 - Beam Deflection and Bending Design]]
- Next: [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
- Concepts: [[Shear Flow]] · [[Shear Centre]] · [[First Moment of Area]]
- Year 1 foundation: [[FEEG1002 A9 - Shear Stresses in Beams]]

![[structures_open_section_shear_flow.png|720]]

## Sources

- Structures slides `SL3 Shear stresses in beams under shear force.pdf`, with transcripts `SESA2028 Lecture 2026-02-27.txt` (ll. 290–438), `SESA2028 Lecture 2026-03-04.txt` and `SESA2028 Lecture 2026-03-11 - SL10 shear. torsion.txt`
- Worked examples recomputed in Python

## Self-study tasks

### Core

- [ ] Derive $\tau=Q\bar yA/I_zt$ and the parabolic distribution in a rectangle (2026-02-27, ll. 395–420). → [[#2. Shear stress in a rectangle]]
- [ ] The angle-section and channel cantilevers: maximum shear stress from the shear-flow distribution (posed with solutions linked, 2026-03-04, ll. 360–395). → [[#3. Shear flow in thin-walled sections]]
- [ ] Shear centres of the T and angle sections "give some thought yourself" (ll. 300–310), and the channel. → [[#5. The shear centre]]
- [ ] The square box under an off-centre load, and the similar tutorial problem (2026-03-11, ll. 151–420). → [[#Worked example: a square box loaded off-centre]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q2 - Closed rectangular box under vertical shear|Tutorial 2 Q2]]

### Further practice

- [ ] Show that $\tau_{max}/\sigma_{max}=h/4L$ for a tip-loaded rectangular cantilever (2026-03-04, ll. 1–45). → [[#2. Shear stress in a rectangle]]
