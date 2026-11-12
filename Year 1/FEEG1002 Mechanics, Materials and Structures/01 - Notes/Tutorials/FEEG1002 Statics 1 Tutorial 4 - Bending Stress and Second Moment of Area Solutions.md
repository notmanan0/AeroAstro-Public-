---
title: "FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, bending-stress, second-moment-of-area]
sheet: "Statics-1 Tutorial problem sheet 4"
theory_notes: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]", "[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
key_concepts: ["[[Engineer's Bending Theory]]", "[[Parallel Axis Theorem]]", "[[Second Moments of Area]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 04 - Beams, Stress and 2nd Moment of Area.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 04 - Beams, Stress and 2nd Moment of Area - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions

> [!abstract] Sheet info
> Three core questions (sizing a square beam, the second moments of an unequal I-section, and the load limit of an inverted-T hoist) and three additional problems (a boom of three rods, a block with two holes, and a sheet-metal water channel). All printed answers are reproduced and every number was recomputed in Python.

Theory: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] · [[Engineer's Bending Theory]] · [[Parallel Axis Theorem]]

The strength questions all follow the procedure of [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Procedure|A4]]: find the largest moment from the BMD, locate the centroid and work out $I$ about it, find the fibre furthest from the neutral axis (on the weaker side if tension and compression limits differ), and apply $\sigma=My/I$. The section-property questions need only the middle two steps.

---

## Q1 - Square beam with an overhanging UDL

Taught in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Example: rectangular cantilever with an end load|A4, rectangular section strength]] · [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Procedure for sketching|A3, sketching]]

The beam has length $2L$ with $L=3$ m. A UDL $w=6$ kN/m acts on the overhang $0\le x\le L$, the pin is at $x=L$ and the roller at $x=2L$. The section is a square of side $H$, and the allowable stress is 300 MPa in tension or compression.

**Reactions.** The resultant $wL$ acts at $x=L/2$. Moments about the roller, then vertical equilibrium:

$$
R_a=\tfrac32wL=27\ \mathrm{kN},\qquad R_b=-\tfrac12wL=-9\ \mathrm{kN}
$$

so the roller pulls down.

**Diagrams.** $Q$ falls linearly from 0 to $-wL$ at the pin, jumps by $R_a$ to $+wL/2$ and stays constant to the roller. $M$ is parabolic over the overhang, reaching

$$
M_{max}=-\tfrac12(wL)L=-\frac{wL^2}{2}=-27\ \mathrm{kN\,m}
$$

over the pin (hogging), then returns linearly to 0 at the roller.

![[s1_t4_q1.png|720]]

**Section size.** For the square, $I=H^4/12$ and $y_{max}=H/2$, so

$$
\sigma_{max}=\frac{M(H/2)}{H^4/12}=\frac{6M}{H^3}
$$

Setting $\sigma_{max}$ to the allowable value:

$$
H=\sqrt[3]{\frac{6|M_{max}|}{\sigma_{max}}}=\sqrt[3]{\frac{3wL^2}{\sigma_{max}}}=\sqrt[3]{\frac{3(6000)(9)}{300\times10^6}}=0.0814\ \mathrm m
$$

## Q2 - Unequal I-section

Taught in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#5. The parallel axis theorem|A4, parallel axis theorem]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#6. Sections with one axis of symmetry|A4, one axis of symmetry]]

The section is a bottom flange (1) 100 mm wide and 20 mm deep, a web (2) 15 mm wide and 40 mm deep, and a top flange (3) 60 mm wide and 15 mm deep, all centred on the vertical axis.

**(i) $I_{yy}$, horizontal bending** about the vertical symmetry axis. Every part has its centroid on this axis, so there are no parallel-axis terms, and each part contributes $db^3/12$ with $b$ its width:

$$
I_{yy}=\frac{20(100)^3}{12}+\frac{40(15)^3}{12}+\frac{15(60)^3}{12}
$$

$$
I_{yy}=(1.667+0.011+0.270)\times10^{-6}=1.95\times10^{-6}\ \mathrm m^4
$$

**(ii) $I_{zz}$, vertical bending.** The section is not symmetric top to bottom, so first locate the centroid from the base:

$$
\bar y=\frac{2000(10)+600(40)+900(67.5)}{3500}=29.93\ \mathrm{mm}
$$

It sits low because the wide bottom flange dominates the area. The part centroids are then $h=19.93$, 10.07 and 37.57 mm from the neutral axis.

| Part | $bd^3/12$ (mm⁴) | $Ah^2$ (mm⁴) | Total (m⁴) |
|---|---|---|---|
| 1 | 66 667 | 794 300 | $8.61\times10^{-7}$ |
| 2 | 80 000 | 60 860 | $1.41\times10^{-7}$ |
| 3 | 16 875 | 1 270 450 | $1.29\times10^{-6}$ |

$$
I_{zz}=2.29\times10^{-6}\ \mathrm m^4
$$

The top flange contributes most, despite being the smaller flange, because it is furthest from the neutral axis.

## Q3 - Inverted-T cantilever hoist

Taught in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Worked example - inverted-T hoist|A4, inverted-T hoist]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Locating the neutral axis|A4, locating the neutral axis]]

A cantilever with an inverted-T section carries a vertical load $F$ 1.0 m from the wall; the allowable stress is 330 MPa. The web (1) is 0.01 m wide and 0.09 m tall, with its centroid 0.055 m above the base, and the flange (2) is 0.1 m wide and 0.01 m deep, with its centroid 0.005 m above the base.

**Section.**

$$
\bar y=\frac{9\times10^{-4}(0.055)+10^{-3}(0.005)}{1.9\times10^{-3}}=0.0287\ \mathrm m
$$

$$
I=\left[\frac{0.01(0.09)^3}{12}+9\times10^{-4}(0.0263)^2\right]+\left[\frac{0.1(0.01)^3}{12}+10^{-3}(0.0237)^2\right]=1.80\times10^{-6}\ \mathrm m^4
$$

**Moment.** With the wall at $x=0$, $Q=F$ and $M=-F(L-x)$, so the largest moment is $|M_{max}|=FL$ at the wall, hogging, with tension on top.

**Critical fibre.** The top of the web is $0.1-0.0287=0.0713$ m from the neutral axis, further than the base at 0.0287 m, and it is the tension side. The limiting moment is

$$
M_{max}=\frac{\sigma I}{y_{max}}=\frac{330\times10^6(1.80\times10^{-6})}{0.0713}=8.33\ \mathrm{kN\,m}
$$

and with $L=1.0$ m, $F=8.33$ kN.

![[s1_bending_stress_tsection.png|860]]

> [!tip] Orientation matters
> Turn the T over, flange on top, under the same hogging moment and the far fibre (now the web tip at the bottom) is in compression instead. For a material weaker in tension, such as cast iron or concrete, the wide flange belongs on the tension side so that the far fibre is in compression.

---

## Extra Q1 - Crane boom of three rods

Taught in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#5. The parallel axis theorem|A4, parallel axis theorem]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Circle|A4, circle]]

Three solid rods of diameter $D=0.1$ m sit at the corners of a triangle of height $H=0.6$ m, rod 1 at the apex and rods 2 and 3 on the base line. Taking moments of area about the base line, $3A\,h=AH$, so the centroid is $h=H/3$ above it. Rod 1 is then $\tfrac23H$ from the neutral axis and rods 2 and 3 are $\tfrac13H$ from it:

$$
I_1=\frac{\pi D^4}{64}+\frac{\pi D^2}{4}\left(\frac23H\right)^2,\qquad I_2=I_3=\frac{\pi D^4}{64}+\frac{\pi D^2}{4}\left(\frac13H\right)^2
$$

Adding:

$$
I_{zz}=\pi\left(\frac{3D^4}{64}+\frac{D^2H^2}{6}\right)=0.0019\ \mathrm m^4
$$

The rods' own second moments make up only 0.8% of the total; almost all of it is the $Ah^2$ terms.

## Extra Q2 - Block with two holes

Taught in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#I-section by subtraction|A4, subtraction]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#5. The parallel axis theorem|A4, parallel axis theorem]]

A block 60 mm wide and 80 mm deep has two holes of diameter 22 mm with centres 20 mm above and below its centre. Subtract the holes, each of area 380.13 mm². For $I_{zz}$ the holes are 20 mm off the axis:

$$
I_{zz}=\frac{60(80)^3}{12}-2\left[\frac{\pi(22)^4}{64}+380.13(20)^2\right]=2.23\times10^{-6}\ \mathrm m^4
$$

For $I_{yy}$ both holes are centred on the axis, so there is no parallel-axis term:

$$
I_{yy}=\frac{80(60)^3}{12}-2\frac{\pi(22)^4}{64}=1.42\times10^{-6}\ \mathrm m^4
$$

## Extra Q3 - Sheet-metal water channel

Taught in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Example: channel section|A4, channel section]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Worked example - channel section|A4, channel worked example]]

A U-channel of 3 mm sheet is 400 mm wide and 200 mm deep outside, carries water 150 mm deep and spans simply supported; the allowable stress is 35 MPa and the self-weight is neglected.

**Load.** The water is $400-2(3)=394$ mm wide, so

$$
w=\rho gA=1000(9.81)(0.394)(0.15)=579.8\ \mathrm{N/m}
$$

a UDL on a simply supported span, with $M_{max}=wL^2/8$ at midspan.

**Section.** The two walls are 197 mm by 3 mm (591 mm² each, centroids 101.5 mm above the base) and the base 400 mm by 3 mm (1200 mm², centroid 1.5 mm above the base). Then $\bar y=51.12$ mm above the base and $I=9.78\times10^{-6}$ m⁴.

**Critical fibre.** The tops of the walls are $200-51.1=148.9$ mm from the neutral axis, in compression under the sagging moment, and further away than the base. So

$$
\frac{wL^2}{8}\cdot\frac{0.1489}{9.78\times10^{-6}}\le35\times10^6
$$

$$
L_{max}=\sqrt{\frac{8(35\times10^6)(9.78\times10^{-6})}{579.8(0.1489)}}=5.63\ \mathrm m
$$

## Sources

- Tutorial Sheet 04 and its official solutions: Q1 pp. 1–2, Q2 pp. 3–5, Q3 pp. 6–7, additional Q1 pp. 8–9, additional Q2 p. 10, additional Q3 pp. 11–12.
- Section properties recomputed in Python and in `Figures/generate_statics1_figures.py`.
- The official solution to additional Q3 (p. 12) writes the stress inequality the wrong way round and gives the centroid as 51.12 m; it is 51.12 mm. The answer is unaffected.
