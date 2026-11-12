---
title: "FEEG1002 A2 - Pin-Jointed Trusses"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 2
tags: [feeg1002, statics, trusses, method-of-joints, method-of-sections, static-determinacy, truss-deformation]
aliases: ["Statics 1 Lecture 3", "Statics 1 Lecture 4", "Trusses", "Method of Joints", "Method of Sections", "Displacement diagram"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 3 (Oct 2024, ll. 12–761: truss model, supports, three-bar example by the method of joints, zero-force member) and Lecture 4 (Oct 2024, ll. 1–848: method of sections, mechanisms and statically determinate/indeterminate trusses, truss deformation and the displacement diagram); slide decks 3 and 4 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
key_concepts: ["[[Method of Joints and Method of Sections]]", "[[Static Determinacy]]", "[[Williot Displacement Diagram]]", "[[Free Body Diagram and Equilibrium]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 03 - Pin-Jointed Trusses, Method of Joints.pdf"
  - "02 - Sources/Statics 1/Lectures/Lecture 04 - Pin-Jointed Trusses, Method of Sections.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 3 - Statics 1 - Trusses, method of joints - Oct 2024.txt"
  - "02 - Sources/Lectures/FEEG1002 Lecture 4 - Statics 1 - Trusses, method of sections - October 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 02 - Trusses.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 02 - Trusses - Solutions.pdf"
---

# FEEG1002 A2 - Pin-Jointed Trusses

> [!abstract] Summary
> A pin-jointed truss is a set of straight bars joined by frictionless pins and loaded only at the joints, so every bar carries a pure axial force and no bending. The bar forces follow from equilibrium: the method of joints balances forces at one joint at a time (two equations per joint), while the method of sections cuts through up to three bars and uses a moment equation to find one force at a time. A truss is statically determinate when $2j=r+m$, a mechanism when $r+m<2j$ and statically indeterminate when $r+m>2j$, though the count alone can mislead. Once the bar forces are known, each bar changes length by $\Delta L=FL/EA$, and requiring the bars to stay pinned together gives the joint displacements through a displacement diagram.

> [!summary]- Exam use: quick path
> - **Use it when:** forces in some or all bars of a plane truss are wanted, a frame must be classified as a mechanism, determinate or indeterminate, or the displacement of a joint is needed.
> - **Assumptions:** straight bars, frictionless pins, loads and reactions only at joints, self-weight neglected (or lumped at the joints), small deformations so equilibrium is written on the undeformed geometry, linear elastic bars for deformation.
> - **Method:** 1. Find the reactions from the FBD of the whole truss. 2. Replace each cut bar by a force pulling away from the joint (tension positive). 3. Method of joints: start at a joint with at most two unknown bar forces and use $\sum F_V=0$, $\sum F_H=0$. Method of sections: cut at most three bars and take moments about the point where two of them meet. 4. Read the sign: positive is tension, negative compression. 5. For displacements, find $\Delta L=FL/EA$ for each bar and impose compatibility.
> - **Common mistakes:** flipping the sign of a force without flipping its arrow; cutting through a joint instead of through bars.
> - **Practise:** [[#Worked example - Warren truss by the method of sections]] · [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Q1 - Bike frame|Tutorial 2 Q1]]

A truss bridge is mostly air. Straight bars arranged in triangles carry the load along their lengths, so very little material does a great deal of work; the same idea appears in roof structures, cranes, bicycle frames and the space frames of satellite structures. A planar truss lies in one plane; a bridge is usually two planar trusses, one each side of the deck, joined across.

The pin-jointed model makes the analysis simple. If the bars are joined by frictionless pins, a bar cannot transmit a moment to its neighbours, and if the loads act only at the joints, nothing pushes on a bar between its ends. Each bar is then pulled or pushed along its own line, like an elastic band in tension or a strut in compression, and the whole problem reduces to finding one number per bar.

As in [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain|A1]], there are two analyses. Strength needs the largest bar forces, to check whether any bar fails; equilibrium alone gives them. Stiffness needs the joint displacements, since the bars stretch and shorten like springs; these come from adding compatibility of the deformed bars.

---

## 1. The pin-jointed truss

### Bars and frictionless pins

A **truss** is a structure of straight members (bars) attached to each other at joints. In a **pin-jointed truss** the joints are frictionless pins: the bar ends sit on a pin and are free to rotate about it. A bar with a frictionless pin at each end and no load between its ends is a **two-force member**: the only forces on it act at its two pins, so for the bar to be in equilibrium they must be equal, opposite and along the line joining the pins. It carries an axial force only, with no shear force and no bending moment.

Real joints are rarely pins. A bicycle frame is welded, and a Victorian railway station is full of pins and holes, which themselves cause stress concentrations. The model still works well when the joints are flexible enough that little moment passes through them and the bars are long and slender. Short, chunky members joined rigidly do transmit moments and have to be analysed as beams ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams|A3]]).

### Further assumptions

The model also assumes that external loads and reactions act only at the joints. A load applied part-way along a bar would bend it, and the bar would then need beam theory. Deformations are small, so the equilibrium equations are written on the undeformed geometry and the angles between bars do not change noticeably. Self-weight is usually neglected: for a bicycle frame it is tiny compared with the rider. For a bridge it is not, and each bar's weight is then split, half to each of its end joints, so that the loads still act at joints.

### Supports

A **pin support**, drawn as a triangle on hatched ground, prevents translation in both directions and supplies a horizontal and a vertical reaction. A **roller** (or sliding) support, drawn as a triangle on rollers, supplies a single reaction perpendicular to the surface it rolls on. The rollers are imagined running in rails, so that reaction can push or pull: it can act up or down for a floor roller, and left or right for a roller on a wall. Getting the orientation right matters. In the three-bar truss below, joint A sits on a roller against a vertical wall: it is free to slide vertically, so it has a horizontal reaction and no vertical one.

## 2. Bar forces and the sign convention

Cutting a bar exposes the force it exerts on the joints at its ends. The convention used throughout is to replace every cut bar by a force drawn pulling away from the joint, which is what a bar in tension does. If the answer comes out negative, the bar is in compression and actually pushes on the joint. A bar in tension pulls inwards on both of its end joints; a bar in compression pushes outwards on both.

When a negative result is redrawn with its true direction, the arrow must be flipped as well as the sign. Dropping the minus sign without flipping the arrow, or flipping the arrow and keeping the minus sign, gives the wrong direction.

## 3. The method of joints

### Procedure

The **method of joints** isolates one joint at a time. A joint is a point where several forces meet, so moments give nothing new and there are two useful equations per joint, $\sum F_V=0$ and $\sum F_H=0$. The procedure is:

1. Draw the FBD of the whole truss and find the reactions.
2. Choose a joint with at most two unknown bar forces.
3. Replace the cut bars by tensile forces and apply the two force balances.
4. Move to the next joint whose unknowns have been reduced to two, and repeat.

Within a joint, start with whichever equation contains a single unknown.

### Example: the three-bar truss

The truss has joint B pinned to a wall, joint A on a wall roller 5 m directly below B, and joint C 10 m out from A at the same level. Bar AB is vertical, AC horizontal and BC inclined at

$$
\theta=\tan^{-1}\frac{5}{10}=26.6^\circ
$$

so $\sin\theta=1/\sqrt5=0.447$ and $\cos\theta=2/\sqrt5=0.894$. A load of 200 N acts **upwards** at C.

![[s1_truss_three_bar_forces.png|900]]

**Reactions.** A has only a horizontal reaction $H_A$; B has $H_B$ and $V_B$. All three are drawn in the positive $x$ and $y$ directions. Vertical equilibrium, up positive:

$$
V_B+200=0
$$

$$
V_B=-200\ \mathrm N
$$

so the reaction at B actually acts downwards. Moments about A remove $H_A$ and $V_B$ (both pass through the wall line at A or B, and $V_B$ is vertical through B, directly above A). Anticlockwise positive, the load at 10 m from A gives $+2000$ N m and $H_B$, pointing right at 5 m above A, gives $-5H_B$:

$$
(10)(200)-5H_B=0
$$

$$
H_B=400\ \mathrm N
$$

Horizontal equilibrium then gives

$$
H_A+H_B=0
$$

$$
H_A=-400\ \mathrm N
$$

so the wall pulls A to the left.

**Joint C.** Two bars meet at C: AC along the horizontal and BC inclined. Drawn as tensile forces, $F_{AC}$ points left from C towards A, and $F_{BC}$ points up and to the left from C towards B, at $\theta$ above the horizontal. Horizontal equilibrium has two unknowns, but vertical equilibrium has only one, so start there. Up positive:

$$
\sin\theta\,F_{BC}+200=0
$$

$$
F_{BC}=\frac{-200}{\sin\theta}=-447\ \mathrm N
$$

BC is in compression and pushes on the joint. Horizontal equilibrium, right positive:

$$
-F_{AC}-\cos\theta\,F_{BC}=0
$$

$$
F_{AC}=-\cos\theta\,F_{BC}=-(0.894)(-447)=+400\ \mathrm N
$$

AC is in tension. Equivalently $F_{AC}=(\cos\theta/\sin\theta)\,200=2\times200=400$ N, since $\tan\theta=1/2$.

**Joint B.** At B act the reactions (400 N to the right, 200 N downward once their signs are applied), the tensile force in AB pointing down towards A, and the tensile force in BC pointing down and to the right towards C. Vertical equilibrium, up positive:

$$
-F_{AB}-\sin\theta\,F_{BC}-200=0
$$

Substitute $F_{BC}=-200/\sin\theta$:

$$
-F_{AB}-\sin\theta\left(\frac{-200}{\sin\theta}\right)-200=0
$$

$$
-F_{AB}+200-200=0
$$

$$
F_{AB}=0
$$

Horizontal equilibrium at B checks the rest: $400+\cos\theta\,F_{BC}=400+(0.894)(-447)=0$.

**Joint A as a check.** At A the forces are $F_{AC}=400$ N pulling right, $H_A=400$ N pulling left, and $F_{AB}$ along the vertical. The roller supplies no vertical force, so vertical equilibrium gives $F_{AB}=0$ again, and horizontally $400-400=0$.

### Zero-force members

Bar AB carries nothing under this load and is called a **zero-force member**. It is not useless. Remove it and joint A, sitting on a roller that only resists horizontal movement, would be free to slide up or down the wall: if the load at C were reversed to point downwards, the truss would swing about B. AB keeps the truss stable for loads other than the one analysed.

The summary for this truss: AC is in tension at 400 N and pulls inwards on A and C; BC is in compression at 447 N and pushes outwards on B and C; AB is unloaded. The method of joints works well for a truss with few bars, working joint by joint across the structure. For a long truss where only a few bar forces are wanted, it is slow.

## 4. The method of sections

### Procedure

The **method of sections** isolates a whole part of the truss rather than a single joint:

1. Find the reactions from the FBD of the whole truss.
2. Cut the truss along a line passing through the bars of interest, at most three of them, and never through a joint.
3. Draw the FBD of one side and replace each cut bar by a tensile force.
4. Use equilibrium of that part. Because the forces are no longer concurrent, a moment equation is available as well as the two force balances, so three unknown bar forces can be found.

The efficient choice is an equation with a single unknown. A moment about the point where the lines of action of two cut bars intersect removes both of them; a force balance in a direction perpendicular to two parallel cut bars removes those two. The moment point need not lie inside the isolated part.

### Example: the five-joint truss

The truss has bottom joints A, B and C at $x=0$, $2L$ and $4L$, top joints E and D at $x=L$ and $3L$, height $L$, so the diagonals are at 45°. A roller supports A and a pin supports C; a load $F$ acts downwards at B. Horizontal equilibrium gives $H_C=0$, since it is the only horizontal force, and symmetry with vertical equilibrium gives $V_A=V_C=\tfrac12F$.

![[s1_truss_method_of_sections.png|900]]

A section through ED, EB and AB isolates the left part, containing joints A and E.

**Force in ED.** The lines of action of $F_{EB}$ and $F_{AB}$ both pass through B, so take moments about B, anticlockwise positive. The reaction $\tfrac12F$ at A, $2L$ to the left of B, turns the part clockwise; $F_{ED}$, pointing right along the top chord a height $L$ above B, also turns it clockwise:

$$
-(2L)\left(\tfrac12F\right)-LF_{ED}=0
$$

$$
F_{ED}=-F
$$

The top chord is in compression.

**Force in EB.** $F_{ED}$ and $F_{AB}$ are horizontal, so vertical equilibrium contains only $F_{EB}$. Down positive, with $F_{EB}$ pointing down and to the right from E towards B:

$$
\sin45^\circ\,F_{EB}-\tfrac12F=0
$$

$$
F_{EB}=\frac{F/2}{1/\sqrt2}=\tfrac12\sqrt2\,F
$$

in tension.

**Force in AB.** $F_{EB}$ and $F_{ED}$ both pass through E, so take moments about E. The reaction at A is $L$ to the left of E (clockwise) and $F_{AB}$ pulls right along the bottom chord, a distance $L$ below E (anticlockwise):

$$
-L\left(\tfrac12F\right)+LF_{AB}=0
$$

$$
F_{AB}=\tfrac12F
$$

in tension. Horizontal equilibrium of the part, $F_{ED}+F_{EB}\cos45^\circ+F_{AB}=-F+\tfrac12F+\tfrac12F=0$, checks all three.

### Checking the sign physically

Without bar ED the truss would fold at B: joints E and D would swing towards each other, so ED must be holding them apart, which is compression. Without AB, joints A and B would spread apart, so AB must be holding them together, in tension. A simply supported truss behaves like a sagging beam: the top chord is squeezed and the bottom chord stretched.

## 5. Choosing a method

Both methods isolate part of the structure and apply equilibrium. The method of joints uses only force balance, two equations per joint, and is the natural way to find every bar force in a small truss. The method of sections adds moment equilibrium, three equations for a section, and is the efficient way to find a few bar forces in a large truss. In both, the art is choosing the joint or cut, and the equation, that leaves one unknown at a time.

## 6. Mechanisms, determinate and indeterminate trusses

### Three classes of frame

A pin-jointed frame falls into one of three classes. A **mechanism** has more equilibrium equations than unknown forces: its bars can rotate without changing length, so it cannot carry general static loads. A square of four bars on a pin and a roller collapses into a parallelogram. Mechanisms are useless as structures but essential in machinery, where motion is the point.

A **statically determinate** frame has as many equilibrium equations as unknowns. Adding one diagonal to the square fixes every joint position: no joint can move without some bar changing length, and every bar force follows from equilibrium alone. All the trusses analysed above are of this kind.

A **statically indeterminate** frame has more unknowns than equations. Adding the second diagonal over-prescribes the joint positions: if that bar were made slightly too long, the pins could only be fitted by forcing it in, and the frame would carry internal forces with no external load at all. The extra bar does bring redundancy: remove it and the frame still stands, which is valuable for safety.

### The counting test

For a 2D pin-jointed frame with $j$ joints (support joints included), there are two equilibrium equations per joint, $2j$ in all. The unknowns are one force for each of the $m$ members and the $r$ reaction components from the supports. The frame is statically determinate when the counts match:

$$
2j=r+m
$$

It is a mechanism if $r+m<2j$ and statically indeterminate if $r+m>2j$. For the square on a pin and a roller ($r=3$, $j=4$, $2j=8$):

| Frame | $m$ | $r+m$ | Class |
|---|---|---|---|
| Square | 4 | 7 | mechanism |
| One diagonal | 5 | 8 | statically determinate |
| Two diagonals | 6 | 9 | statically indeterminate |

![[s1_truss_static_determinacy.png|900]]

The test counts bars but does not look at where they are. A frame of seven joints and eleven bars on a pin and a roller satisfies $2(7)=3+11$, yet if one bay carries both diagonals and the next carries none, the first bay is indeterminate and the second a mechanism. Moving the extra diagonal to the empty bay gives a stable determinate truss with the same count. The test is necessary but not sufficient, so look at the geometry as well.

Statically indeterminate trusses can be solved, but their bar forces depend on the bar stiffnesses and need the deformation analysis below; they are not covered here. Statically indeterminate beams are ([[FEEG1002 A6 - Statically Indeterminate Beams|A6]]).

## 7. Truss deformation

### Bar extensions

Once every bar force is known, each bar's change in length follows from treating it as a spring ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#A bar is a spring|A1]]):

$$
F=\frac{EA}{L}\Delta L
$$

$$
\Delta L=\frac{L}{EA}F
$$

For the three-bar truss with $A=1\times10^{-4}$ m² and $E=70$ GPa (aluminium), $EA=7\times10^6$ N:

| Bar | Force (N) | Length (m) | $\Delta L=FL/EA$ (μm) |
|---|---|---|---|
| AB | 0 | 5 | 0 |
| AC | +400 | 10 | +571 |
| BC | −447 | 11.2 | −714 |

Half a millimetre on a ten-metre bar: the deformations are tiny, which justifies writing equilibrium on the undeformed shape.

### Compatibility

In a pin-jointed structure the bars extend or contract along their own axes and are free to rotate about the pins, but they always stay attached to each other at the joints. The individual bar deformations must therefore be **compatible**: each free joint must sit where all the bars meeting there can reach it.

In the three-bar truss, B is pinned and A cannot move (AB does not change length and the roller only allows A to slide along AB's line). Joint C must lie on a circle about A of radius $10\ \mathrm m+\Delta L_{AC}$ and on a circle about B of radius $L_{BC}+\Delta L_{BC}$; its new position is where the two arcs intersect.

### The displacement diagram

Because the displacements are so small, each arc can be replaced by a straight line at right angles to its bar. The **displacement diagram** draws, from the original position of C, the extension of AC along AC (to the right, 571 μm), and the shortening of BC along BC (towards B, 714 μm); perpendiculars to the two bars through the ends of these vectors meet at the displaced position of C.

![[s1_williot_displacement.png|900]]

The horizontal displacement is read off at once. AC is horizontal and A does not move, so the component of C's displacement along AC is AC's extension:

$$
\Delta X_C=\Delta L_{AC}=571\ \mu\mathrm m
$$

For the vertical displacement, split the diagram into two right-angled triangles. In the first, the perpendicular to AC drawn from the tip of $\Delta L_{AC}$ rises a height $\Delta Y_{C1}$ before meeting the line through C parallel to the perpendicular of BC; the angle at the top is $\theta$, so

$$
\tan\theta=\frac{\Delta L_{AC}}{\Delta Y_{C1}}
$$

In the second, the shortening of BC, of magnitude $|\Delta L_{BC}|$, is the side opposite $\theta$ with hypotenuse $\Delta Y_{C2}$:

$$
\sin\theta=\frac{|\Delta L_{BC}|}{\Delta Y_{C2}}
$$

Adding the two heights,

$$
\Delta Y_C=\Delta Y_{C1}+\Delta Y_{C2}
$$

$$
\Delta Y_C=\frac{\Delta L_{AC}}{\tan\theta}+\frac{|\Delta L_{BC}|}{\sin\theta}
$$

$$
\Delta Y_C=\frac{\cos\theta\,\Delta L_{AC}+|\Delta L_{BC}|}{\sin\theta}
$$

### Vector form of the same result

The geometry can be checked with vectors. Let $\mathbf u_C=(u_x,u_y)$ be C's displacement, with $y$ upwards, and let $\mathbf e$ be the unit vector along a bar from its fixed end to C. For a small displacement the change in a bar's length is the component of the displacement of its free end along the bar:

$$
\Delta L=\mathbf u_C\cdot\mathbf e
$$

For AC, $\mathbf e_{AC}=(1,0)$, so $u_x=\Delta L_{AC}$. For BC, $\mathbf e_{BC}=(\cos\theta,-\sin\theta)$, since C is below and to the right of B:

$$
u_x\cos\theta-u_y\sin\theta=\Delta L_{BC}
$$

$$
u_y=\frac{u_x\cos\theta-\Delta L_{BC}}{\sin\theta}
$$

With $\Delta L_{BC}$ negative this is the same expression as above.

> [!check] Numbers for the three-bar truss
> $\Delta Y_{C1}=571/0.5=1143$ μm and $\Delta Y_{C2}=714/0.447=1597$ μm, so $\Delta Y_C=2.74$ mm upwards, in the direction of the 200 N load. The vector form gives $u_y=(571\times0.894+714)/0.447=2740$ μm.

The vertical movement is about five times the horizontal one, $u_x=\Delta L_{AC}=571$ μm, because AC and BC meet at only 26.6°. Two length constraints along nearly parallel directions fix the joint well along those directions but poorly across them, and the $1/\sin\theta$ in the result expresses that weakness: a shallow truss is flexible in the direction normal to its bars.

### Strength and buckling

With the bar forces known, the stress in each bar follows from its area and can be compared with the allowable stress of the material, giving the first bar to fail. A bar in tension fails by yielding or fracture. A slender bar in compression usually fails first by buckling, at a load well below its yield load ([[FEEG1002 A7 - Euler Buckling of Struts|A7]]).

---

## Worked examples

### Worked example - bike frame by the method of joints

Tutorial 2 Q1 models a bicycle frame as a pin-jointed truss (set in L3, ll. 749–758). Joint A (top left, at the head tube) is pinned and joint D (bottom right, at the rear axle) is on a roller. With A at the origin, B is 0.5 m to the right of A, C is 0.5 m below B, and D is 0.5 m to the right of C. The bars are AB, AC, BC, BD and CD, so AC and BD are at 45°. The rider's weight $F=750$ N acts downwards at B.

The role of each bar shows when it is removed. Without CD the rear triangle would splay open, so CD is in tension; without BD it would collapse, so BD is in compression.

**Reactions.** Moments about A, anticlockwise positive: $1.0F_D-0.5(750)=0$, so $F_D=375$ N upwards, and vertical equilibrium gives $F_A=375$ N upwards.

**Joint D.** Only BD and CD meet at D. The tensile force in BD points from D towards B, up and to the left at 45°; the tensile force in CD points left. Vertical, up positive:

$$
375+F_{BD}\sin45^\circ=0
$$

$$
F_{BD}=-\frac{375}{0.707}=-530\ \mathrm N
$$

Horizontal, right positive:

$$
-F_{CD}-F_{BD}\cos45^\circ=0
$$

$$
F_{CD}=-(-530)(0.707)=+375\ \mathrm N
$$

BD is in compression at 530 N and CD in tension at 375 N, as predicted. Carrying on through joints C and B gives $F_{AC}=+530$ N, $F_{BC}=-375$ N and $F_{AB}=-375$ N.

### Worked example - Warren truss by the method of sections

Tutorial 2 Q2 is a Warren truss of span 24 m and height 3 m. The bottom joints A, G, F and E are at $x=0$, 8, 16 and 24 m, the top joints B, C and D at $x=4$, 12 and 20 m, so each diagonal is the hypotenuse of a 3–4–5 triangle: $\sin\theta=3/5$, $\cos\theta=4/5$. A is pinned, E is on a roller, and 15 kN hangs from each of G and F. Find the forces in DE, GF and GC.

**Reactions.** Horizontal equilibrium gives $H_A=0$. Moments about A: $24V_E=8(15)+16(15)$, so $V_E=15$ kN, and $V_A=30-15=15$ kN.

**DE by the method of joints at E.** Only DE and FE meet at E, and FE is horizontal. The tensile force in DE points from E up and to the left towards D. Vertical, up positive:

$$
15+F_{DE}\sin\theta=0
$$

$$
F_{DE}=-\frac{15}{3/5}=-25\ \mathrm{kN}
$$

**GF by a section.** Cut through BC, GC and GF and keep the right-hand part (joints C, D, F, E). BC and GC meet at C, $(12,3)$, so take moments about C, anticlockwise positive. The tensile force in GF pulls left along the bottom chord, 3 m below C (clockwise); the 15 kN at F, 4 m right of C, is clockwise; the 15 kN reaction at E, 12 m right of C, is anticlockwise:

$$
-3F_{GF}-4(15)+12(15)=0
$$

$$
F_{GF}=\frac{180-60}{3}=+40\ \mathrm{kN}
$$

**GC from the same section.** BC and GF are horizontal, so vertical equilibrium of the right part contains only GC. Its tensile force on the right part points from C down and to the left towards G. Up positive:

$$
15-15-F_{GC}\sin\theta=0
$$

$$
F_{GC}=0
$$

The middle bay carries no shear between the two equal loads, just as the shear force in a symmetric beam is zero between two equal symmetric loads ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams|A3]]).

![[s1_t2_q2_warren_truss.png|900]]

### Worked example - the five-joint truss with numbers

Put $F=12$ kN on the truss of section 4. Then $F_{ED}=-12$ kN, $F_{EB}=\tfrac12\sqrt2(12)=8.49$ kN and $F_{AB}=6$ kN, independent of the size $L$: the bar forces depend only on the angles, while the bar lengths, and so the deflections, scale with $L$.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] · Next: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]
- Concepts: [[Method of Joints and Method of Sections]] · [[Static Determinacy]] · [[Williot Displacement Diagram]] · [[Free Body Diagram and Equilibrium]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 A7 - Euler Buckling of Struts|A7]] (compression members buckle; which way round to fit the braces)
- Year 2: joint displacements without a diagram by the [[Unit Load Method]] and indeterminate trusses by [[Castigliano Second Theorem]] in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]; the bar stiffness assembled into $\mathbf K\mathbf u=\mathbf F$ in [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] ([[Global Stiffness Matrix Assembly]])

## Sources

- `Lecture 03 - Pin-Jointed Trusses, Method of Joints.pdf` (S1 Lectures 3a–3b, 20 slides) and `Lecture 04 - Pin-Jointed Trusses, Method of Sections.pdf` (S1 Lectures 4a–4c, 30 slides), read in full.
- `FEEG1002 Lecture 3 - Statics 1 - Trusses, method of joints - Oct 2024.txt` (Lecture 3): truss definition (ll. 53–75), pin-jointed model (ll. 76–152), further assumptions (ll. 153–191), supports (ll. 192–263), aims and methods (ll. 264–301), reactions (ll. 302–458), method of joints at C, B and A (ll. 459–662), zero-force member (ll. 663–687), summary (ll. 688–748), tutorial (ll. 749–758).
- `FEEG1002 Lecture 4 - Statics 1 - Trusses, method of sections - October 2024.txt` (Lecture 4): method of sections (ll. 29–76), example (ll. 77–317), comparison and physical check (ll. 318–363), mechanisms and determinacy (ll. 364–602), truss deformation and the displacement diagram (ll. 603–838), buckling and tutorial (ll. 839–848).
- Tutorial Sheet 02 and its official solutions: Q1–Q2 and additional Q1–Q3.
- All numbers recomputed in Python, including a full joint-equilibrium solve of each truss.

## Self-study tasks

### Core

- [ ] Find the reactions and all three bar forces of the three-bar truss, then check joint A (L3, ll. 302–662). → [[#Example: the three-bar truss]]
- [ ] Tutorial 2 Q1: decide which bars of the bike frame are in tension or compression, then find $F_{BD}$ and $F_{CD}$ (set in L3, ll. 749–758). Targets −530 N and +375 N. → [[#Worked example - bike frame by the method of joints]] · [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Q1 - Bike frame|Tutorial 2 Q1]]
- [ ] Tutorial 2 Q2: forces in DE, GF and GC of the Warren truss by joints or sections (deck 4, slide 30; set in L4, ll. 843–847). Targets −25 kN, +40 kN and 0. → [[#Worked example - Warren truss by the method of sections]] · [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Q2 - Warren truss|Tutorial 2 Q2]]
- [ ] Classify the square, braced and double-braced frames with $2j=r+m$, then explain why the seven-joint frame passes the test but fails (L4, ll. 448–592). → [[#The counting test]]
- [ ] Derive $\Delta Y_C$ for the three-bar truss from the displacement diagram and evaluate it (L4, ll. 786–833). Target 2.74 mm upwards. → [[#The displacement diagram]]

### Further practice

- [ ] Tutorial 2 additional Q1: force in AB with one moment equation. Target 160 N. → [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Extra Q1 - Truss with an upward load|Tutorial 2 Extra Q1]]
- [ ] Tutorial 2 additional Q2: forces in the legs of the braced tower. Targets −20, −60 and −120 kN. → [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Extra Q2 - Braced tower|Tutorial 2 Extra Q2]]
- [ ] Tutorial 2 additional Q3: displacement of C for the three-bar truss with an inclined load. Targets 13 μm and 32 μm. → [[#7. Truss deformation]] · [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions#Extra Q3 - Displacement of a three-bar truss|Tutorial 2 Extra Q3]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 3, ll. 298–301 and 348–351)
> Where: [[#Supports]].
>
> The plan is given as "the method of sections, the method of joints" today and the method of sections next week; Lecture 3 covers the method of joints and Lecture 4 the method of sections. At ll. 348–351 the roller at A is said to move "in vertical direction" and so give no vertical reaction, which is right for this wall roller but is the opposite orientation to the floor roller defined at ll. 232–254; the reaction is always perpendicular to the surface the roller runs on.

> [!warning] Transcript slips (Lecture 4, ll. 183–190, 510 and 841)
> Where: [[#Example: the five-joint truss]] · [[#The counting test]] · [[#Strength and buckling]].
>
> Moments about E are first suggested for $F_{ED}$; E lies on ED's own line, so that moment equation does not contain $F_{ED}$ at all, and the lecture switches to B, which is correct. E is the right point for $F_{AB}$. At l. 510 the square frame is said to have "seven unknown bar forces"; it has seven unknowns, four bar forces and three reactions. At l. 841 a bar in compression "will fail by buckling"; the slide says compressed bars will mostly fail this way, which is true of slender bars, while short stocky bars yield first.
