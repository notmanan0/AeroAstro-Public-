---
title: "FEEG1002 A6 - Statically Indeterminate Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 6
tags: [feeg1002, statics, beams, statically-indeterminate, double-integration, superposition, compatibility]
aliases: ["Statics 1 Lecture 11", "Propped cantilever", "Indeterminate beams", "Superposition method"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 11 (2 Dec 2024, ll. 1–823: recap of Macaulay's method, determinate and indeterminate beams, propped cantilever by double integration and by superposition, choice of method); slide deck 11 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
next_topics: ["[[FEEG1002 A7 - Euler Buckling of Struts]]"]
key_concepts: ["[[Superposition for Indeterminate Beams]]", "[[Macaulay's Method]]", "[[Standard Beam Deflections]]", "[[Static Determinacy]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 11 - Statically Indeterminate Beams.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 11 - Statics 1 - Statically indeterminate beams - December 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 05 - Beam Deflection and Statically Indeterminate Beams.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 05 - Beam Deflection and Statically Indeterminate Beams - Solutions.pdf"
---

# FEEG1002 A6 - Statically Indeterminate Beams

> [!abstract] Summary
> A beam loaded only vertically gives two useful equilibrium equations, vertical force and moment, so a beam with three or four unknown reactions, such as a propped cantilever or a beam built in at both ends, is statically indeterminate: equilibrium alone cannot say how the load is shared. The extra supports that cause the problem also solve it, because each one prescribes a deflection or slope. In the double integration method the unknown reactions are carried through Macaulay's method and the extra boundary conditions supply the missing equations; in the superposition method a redundant support is removed, the beam is split into standard determinate cases, and the redundant force is chosen so that the deflection at the support is zero. For a propped cantilever with a uniform load both give a prop reaction of $\tfrac38wL$.

> [!summary]- Exam use: quick path
> - **Use it when:** a beam has more unknown reactions than equilibrium equations, for instance built in at one end and propped at the other, or built in at both ends.
> - **Assumptions:** linear elastic, small deflections, so deflections from separate loads add; rigid supports (no settlement); uniform $EI$; $v$ downwards, $M$ sagging positive, $EI\,v''=-M$.
> - **Method:** 1. Replace the supports by unknown reactions and write the two equilibrium equations. 2. Write $M(x)$ with the reactions as symbols (Macaulay brackets if needed). 3. Integrate $EI\,v''=-M$ twice. 4. Apply every kinematic condition: the first two fix the constants, showing explicitly why each is zero; the rest are the extra equations. 5. Solve the set, then back-substitute for $v(x)$ and $M(x)$. (Superposition: remove the redundant support, add standard deflections, set the total to zero there.)
> - **Common mistakes:** using $M=0$ at a roller as the extra equation, which only repeats moment equilibrium; dropping a constant of integration without showing from a boundary condition that it is zero.
> - **Practise:** [[#Worked example - propped balcony beam]] · [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Q3 - Propped cantilever with a half-length UDL|Tutorial 5 Q3]]

Where a beam has only two unknown reactions (A3 to A5), the equilibrium equations are enough to find every reaction. An extra support removes that. A beam on three supports, or a cantilever whose free end rests on a prop, has one reaction too many: equilibrium says what the reactions must add up to, but not how the load is divided between them.

The way out is physical. Remove the extra support and the beam deflects at that point under the load. The reaction there is exactly the force needed to push the beam back up to zero deflection. How the load divides therefore depends on how the beam bends, which is why indeterminate beams need the deflection results of [[FEEG1002 A5 - Beam Deflection and Macaulay's Method|A5]].

Two methods turn this picture into equations. Double integration keeps the reactions as unknowns throughout and lets the extra boundary conditions close the system; it always works. Superposition builds the answer from standard cases whose deflections are already known; it needs more insight but is quick when the loads match those cases.

---

## 1. Statically determinate and indeterminate beams

### Counting reactions

For a beam with only vertical loads, horizontal equilibrium is trivial and the horizontal reactions are zero, so two equilibrium equations remain: vertical force and moment. A simply supported beam with a pin and a roller, or a cantilever with a force and a moment at its root, has two unknown vertical reactions. Two equations for two unknowns: these beams are **statically determinate**.

A beam with more unknowns than equations is **statically indeterminate**, by analogy with the truss test of [[FEEG1002 A2 - Pin-Jointed Trusses#6. Mechanisms, determinate and indeterminate trusses|A2]]:

| Beam | Unknown reactions (vertical loads) | Equations | Unknowns too many |
|---|---|---|---|
| Simply supported (pin and roller) | $R_A$, $R_B$ | 2 | 0 |
| Cantilever (built in, free) | $R_1$, $M_1$ | 2 | 0 |
| Propped cantilever (built in, roller) | $R_1$, $M_1$, $R_2$ | 2 | 1 |
| Pin and two rollers | $R_A$, $R_B$, $R_C$ | 2 | 1 |
| Built in at both ends | $R_A$, $M_A$, $R_B$, $M_B$ | 2 | 2 |

A reaction moment should be labelled $M_1$, $M_A$ or similar, never plain $M$, to keep it distinct from the internal bending moment.

![[s1_beam_reaction_count.png|900]]

### The missing equations come from deformation

Every extra support also prescribes something about the deformed shape: a roller fixes the deflection at its position, a built-in end fixes both the deflection and the slope. A statically indeterminate beam therefore has more kinematic boundary conditions than a determinate one, and exactly as many extra as it has extra unknowns. Those extra conditions supply the missing equations.

## 2. The double integration method

### Example: propped cantilever with a uniform load

A beam of length $L$ is built in at its left end ($x=0$) and rests on a roller at its right end ($x=L$). It carries a uniform load $w$ (N/m) along its whole length, a total of $wL$. Replace the supports by unknown reactions: a vertical force $R_1$ and a reaction moment $M_1$ at the wall (drawn anticlockwise), and a vertical force $R_2$ at the roller.

**Equilibrium.** Vertically,

$$
R_1+R_2=wL\tag{1}
$$

Take moments about the right-hand end, which removes $R_2$. The resultant $wL$ acts at $L/2$:

$$
R_1L=M_1+\frac{wL^2}{2}\tag{2}
$$

Two equations, three unknowns. Moments about any other point give a combination of (1) and (2), nothing new.

**Bending moment.** Cut at $x$ and keep the left part. The load on it is $wx$ at $x/2$ from the cut. The reaction moment $M_1$ is anticlockwise, in the same sense as the positive $M$ on the cut face, so it enters with the opposite sign to $M$:

$$
M=-M_1-\frac{wx^2}{2}+R_1x
$$

**Integrate.** From $EI\,v''=-M$:

$$
EI\frac{d^2v}{dx^2}=M_1+\frac{wx^2}{2}-R_1x
$$

$$
EI\frac{dv}{dx}=M_1x+\frac{wx^3}{6}-\frac{R_1x^2}{2}+C_0
$$

At the wall the beam cannot rotate, so the slope is zero, $dv/dx=0$ at $x=0$. (The beam is not symmetric, so there is no reason for zero slope at mid-span; and zero deflection at the wall is true but applies to $v$, not to the slope expression.)

$$
0=0+0-0+C_0\quad\Rightarrow\quad C_0=0
$$

Integrate again:

$$
EIv=M_1\frac{x^2}{2}+\frac{wx^4}{24}-R_1\frac{x^3}{6}+C_1
$$

The wall also prevents vertical movement, $v(0)=0$:

$$
0=0+0-0+C_1\quad\Rightarrow\quad C_1=0
$$

Each constant is zero because of a stated boundary condition, and that reasoning should always be written out, not assumed.

**The extra condition.** The roller prevents deflection at $x=L$:

$$
v(L)=0\quad\Rightarrow\quad M_1\frac{L^2}{2}+\frac{wL^4}{24}-R_1\frac{L^3}{6}=0\tag{3}
$$

Three equations for $R_1$, $R_2$ and $M_1$.

> [!warning] Zero moment at the roller is not a new equation
> $M(L)=0$ is also true, since a roller supplies no moment, but $M(L)=-M_1-wL^2/2+R_1L=0$ is equation (2) again: zero moment at the right-hand end is the same statement as moment equilibrium about the right-hand end. The independent extra equation has to come from the deformation, $v(L)=0$.

**Solve.** From (2):

$$
M_1=R_1L-\frac{wL^2}{2}
$$

From (3), dividing by $L^2/2$:

$$
M_1=R_1\frac L3-\frac{wL^2}{12}
$$

Equate the two:

$$
R_1L-\frac{wL^2}{2}=R_1\frac L3-\frac{wL^2}{12}
$$

$$
\frac23R_1L=wL^2\,\frac{6-1}{12}
$$

$$
R_1=\frac32\cdot\frac{5}{12}wL=\frac58wL
$$

Then (1) and (2) give

$$
R_2=wL-\frac58wL=\frac38wL,\qquad M_1=\frac58wL^2-\frac12wL^2=\frac{wL^2}{8}
$$

**Back-substitute.** With these reactions,

$$
\boxed{v=\frac{1}{EI}\left[\frac{wL^2}{16}x^2+\frac{w}{24}x^4-\frac{5wL}{48}x^3\right],\qquad M=-\frac{wL^2}{8}-\frac{wx^2}{2}+\frac58wLx}
$$

The deflection factorises as

$$
v=\frac{wx^2}{48EI}(L-x)(3L-2x)
$$

which shows the double root at the wall (zero deflection and zero slope) and the single root at the roller.

### Shape of the solution

The bending moment is $-wL^2/8$ at the wall, hogging, and rises to a sagging maximum where $Q=dM/dx=0$:

$$
\frac58wL-wx=0\quad\Rightarrow\quad x=\frac58L
$$

$$
M\!\left(\tfrac58L\right)=-\frac{wL^2}{8}-\frac{w}{2}\cdot\frac{25L^2}{64}+\frac58wL\cdot\frac58L=\frac{9}{128}wL^2
$$

The largest magnitude is the hogging $wL^2/8$ at the wall. The maximum deflection is where $dv/dx=0$; differentiating the factorised form gives $8x^2-15Lx+6L^2=0$, whose root inside the span is

$$
x=\frac{15-\sqrt{33}}{16}L=0.578L
$$

where $v_{max}=0.00542\,wL^4/EI\approx wL^4/185EI$.

![[s1_propped_cantilever_udl.png|900]]

### Summary of the double integration method

The double integration method is unchanged: use Macaulay's method, but carry the unknown reactions through to the end. The extra supports of an indeterminate beam provide extra boundary conditions, and together with equilibrium these give a set of equations to solve for the reactions.

## 3. The superposition method

### Idea

Instead of carrying the unknown reactions through, split the problem into standard, statically determinate cases. For a linear elastic beam with small deflections, the deflection under several loads is the sum of the deflections under each load separately. For the propped cantilever, remove the roller:

- case (′): a cantilever carrying the uniform load $w$, whose free end deflects by $v'(L)$;
- case (″): a cantilever carrying only an upward force $F$ at its free end, equal to the unknown roller reaction, whose free end deflects by $v''(L)$.

The primes label the two cases; they are not derivatives. Superposed, the two cases are the original beam, and the roller requires the total deflection at $x=L$ to vanish. This **compatibility condition** is

$$
v'(L)+v''(L)=0
$$

so $F$ is the force needed to bend the beam back to zero displacement at the prop.

### Case (′): cantilever with a uniform load

The wall supplies an upward force $wL$ and a reaction moment $wL^2/2$. Cut at $x$ and keep the left part:

$$
M=-\frac{wL^2}{2}-\frac{wx^2}{2}+wLx
$$

Then

$$
EI\frac{d^2v'}{dx^2}=\frac{wL^2}{2}+\frac{wx^2}{2}-wLx
$$

$$
EI\frac{dv'}{dx}=\frac{wL^2}{2}x+\frac{wx^3}{6}-\frac{wL}{2}x^2+C_0
$$

$$
EIv'=\frac{wL^2}{4}x^2+\frac{wx^4}{24}-\frac{wL}{6}x^3+C_0x+C_1
$$

At the built-in end $dv'/dx=0$ and $v'=0$ at $x=0$, so $C_0=C_1=0$. At the free end:

$$
EIv'(L)=\frac{wL^4}{4}+\frac{wL^4}{24}-\frac{wL^4}{6}=\frac{6+1-4}{24}wL^4
$$

$$
\boxed{v'(L)=\frac{wL^4}{8EI}}
$$

and the tip slope is $(wL^3/2+wL^3/6-wL^3/2)/EI=wL^3/(6EI)$. A balcony on a tower block is this case.

### Case (″): cantilever with an upward end force

With an upward force $F$ at the tip, the wall reactions are a downward force $F$ and a clockwise moment $FL$ (drawn in the positive directions, they come out as $-F$ and $-FL$; the directions drawn for reactions do not change $M$, but the sign convention for $M$ must not be changed). Cut at $x$ and keep the right part, where only $F$ acts, a distance $L-x$ from the cut. It bends the beam upwards into a sagging shape:

$$
M=F(L-x)=FL-Fx
$$

Then

$$
EI\frac{d^2v''}{dx^2}=-FL+Fx
$$

$$
EI\frac{dv''}{dx}=-FLx+\frac{Fx^2}{2}+C_0
$$

$$
EIv''=-FL\frac{x^2}{2}+F\frac{x^3}{6}+C_0x+C_1
$$

With $v''=0$ and $dv''/dx=0$ at the wall, $C_0=C_1=0$, and

$$
EIv''(L)=-\frac{FL^3}{2}+\frac{FL^3}{6}
$$

$$
\boxed{v''(L)=-\frac{FL^3}{3EI}}
$$

negative because the tip moves upwards. The tip slope has magnitude $FL^2/(2EI)$. Hoisting a load from the end of a cantilever is this case with the force reversed.

### Compatibility and the reactions

Substitute the two tip deflections:

$$
\frac{wL^4}{8EI}-\frac{FL^3}{3EI}=0
$$

$$
F=\frac38wL=R_2
$$

Then revisit the original beam with $R_2$ known. Vertical equilibrium gives $R_1=wL-\tfrac38wL=\tfrac58wL$, and moments give

$$
M_1-\frac58wL^2+\frac12wL^2=0\quad\Rightarrow\quad M_1=\frac{wL^2}{8}
$$

With all the reactions known, the beam is now determinate: cut at $x$ to get $M=-wL^2/8-wx^2/2+\tfrac58wLx$, and double integration with the boundary conditions gives the same deflection curve as before.

![[s1_superposition_propped_cantilever.png|900]]

### Summary of the superposition method

Split the problem into statically determinate standard cases, solve each for its reactions and deflection (by Macaulay's method or from a table of [[Standard Beam Deflections]]), set up the compatibility condition to find the newly imposed loads, and finally solve the original beam as usual. The method is convenient whenever the parts are standard solutions, such as the end deflection of a cantilever under a uniform or concentrated load. It is also useful for determinate beams, building a complicated deflection from simple cases.

## 4. Which method

Double integration always works, whatever the loading, and asks for no insight beyond writing $M(x)$ correctly. Superposition is quicker when the loads match tabulated cases and gives a direct physical meaning to each step, but it needs judgement about which support to remove and which cases to combine. For an exam question with a partial or unusual load, double integration is the safer choice; for a standard load, superposition is faster.

Indeterminacy also changes how the beam behaves. Under the same uniform load the propped cantilever's sagging moment, $\tfrac{9}{128}wL^2$, is much smaller than the simply supported beam's $\tfrac18wL^2$, though the largest moment moves to the wall; and its maximum deflection, $wL^4/185EI$, is less than half of $5wL^4/384EI=wL^4/77EI$.

---

## Worked examples

### Worked example - propped balcony beam

A balcony beam 4 m long is built into a wall and propped by a column at its outer end; it carries 6 kN/m. With $w=6$ kN/m and $L=4$ m:

$$
R_2=\frac38(6)(4)=9\ \mathrm{kN},\qquad R_1=\frac58(6)(4)=15\ \mathrm{kN},\qquad M_1=\frac{(6)(4)^2}{8}=12\ \mathrm{kN\,m}
$$

The bending moment is $-12$ kN m at the wall and reaches its sagging maximum at $x=\tfrac58(4)=2.5$ m:

$$
M_{max}=\frac{9}{128}(6)(4)^2=6.75\ \mathrm{kN\,m}
$$

With $EI=2$ MN m², the maximum deflection is at $x=0.578(4)=2.31$ m:

$$
v_{max}=0.00542\frac{(6000)(4)^4}{2\times10^6}=4.16\ \mathrm{mm}
$$

> [!check] Equilibrium of the reactions
> Vertical: $15+9=24=6\times4$ kN. Moments about the wall: $M_1+R_2L=12+36=48$ kN m, which equals the load's moment $wL^2/2=48$ kN m.

Without the prop, the same balcony would be a plain cantilever with a root moment of $wL^2/2=48$ kN m and a tip deflection of $wL^4/8EI=96$ mm. The prop cuts the largest moment by a factor of four and the deflection by more than twenty.

### Worked example - propped cantilever with a half-length load

Tutorial 5 Q3 loads the propped cantilever with $w$ over the half nearest the wall only. The load stops at $L/2$, so Macaulay's method needs a cancelling upward load from there. Equilibrium gives $R_A+R_B=wL/2$ and, about B, $-R_AL+M_A+\tfrac{wL}{2}\cdot\tfrac{3L}{4}=0$. With $M=-M_A+R_Ax-\tfrac{w}{2}x^2+\tfrac w2[x-\tfrac L2]^2$, the built-in end gives $C_0=C_1=0$ and $v(L)=0$ gives

$$
M_A\frac{L^2}{2}-R_A\frac{L^3}{6}+\frac{wL^4}{24}-\frac{w(L/2)^4}{24}=0
$$

Solving the three equations,

$$
R_A=\frac{57}{128}wL,\qquad R_B=\frac{7}{128}wL,\qquad M_A=\frac{9}{128}wL^2
$$

With the load concentrated near the wall, the prop carries only $7/64$ of it.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · Next: [[FEEG1002 A7 - Euler Buckling of Struts]]
- Concepts: [[Superposition for Indeterminate Beams]] · [[Macaulay's Method]] · [[Standard Beam Deflections]] · [[Static Determinacy]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Year 2: the same problems by energy in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]], where $\partial U/\partial R=0$ ([[Castigliano Second Theorem]]) is the compatibility condition; [[Maxwell-Betti Reciprocity]] and the [[Principle of Virtual Work]]; the stiffness method of [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]], which solves for displacements first and treats determinate and indeterminate structures alike

## Sources

- `Lecture 11 - Statically Indeterminate Beams.pdf` (S1 Lectures 11a–11c, 28 slides), read in full.
- `FEEG1002 Lecture 11 - Statics 1 - Statically indeterminate beams - December 2024.txt` (Lecture 11): Macaulay recap (ll. 13–93), determinate and indeterminate beams (ll. 94–184), the deformed-shape picture (ll. 185–231), double integration of the propped cantilever (ll. 237–558), superposition (ll. 559–802), choice of method (ll. 803–823).
- Tutorial Sheet 05 and its official solutions: Q3 and additional Q3.
- All results recomputed with SymPy, including the location and size of the maximum deflection.

## Self-study tasks

### Core

- [ ] Count the unknown reactions for a beam built in at both ends and for a propped cantilever (class questions, L11, ll. 137–184). Targets 4 and 3. → [[#Counting reactions]]
- [ ] Solve the propped cantilever by double integration, stating which boundary condition makes each constant zero (L11, ll. 237–545; constants shown explicitly, ll. 443–449). Targets $R_1=\tfrac58wL$, $R_2=\tfrac38wL$, $M_1=\tfrac18wL^2$. → [[#Example: propped cantilever with a uniform load]]
- [ ] Explain why $M(L)=0$ cannot replace $v(L)=0$ (L11, ll. 479–484). → [[#Example: propped cantilever with a uniform load]]
- [ ] Solve the same beam by superposition, deriving both cantilever tip deflections (L11, ll. 584–790). → [[#3. The superposition method]]
- [ ] Tutorial 5 Q3: propped cantilever with the load on the half nearest the wall. Targets $\tfrac{57}{128}wL$, $\tfrac{7}{128}wL$, $\tfrac{9}{128}wL^2$. → [[#Worked example - propped cantilever with a half-length load]] · [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Q3 - Propped cantilever with a half-length UDL|Tutorial 5 Q3]]

### Further practice

- [ ] Work through the motorway-sign superposition case study on Blackboard (week 10 schedule; L11, ll. 567–573). → [[#3. The superposition method]]
- [ ] Tutorial 5 additional Q3: set up enough equations for a beam built in at both ends with a uniform load and a central point load, then solve them. Targets $R_A=R_B=W/2+wL$ and end moments of magnitude $WL/4+wL^2/3$. → [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Extra Q3 - Fixed-fixed beam|Tutorial 5 Extra Q3]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 11, ll. 468, 566, 582 and 621–622)
> Where: [[#Example: propped cantilever with a uniform load]] · [[#3. The superposition method]].
>
> The support at $x=L$ is called an "additional pin support" at l. 468; it is the roller of l. 284, though either gives $v(L)=0$. Superposition is said to be useful for "normal statically indeterminate beams" (l. 566) and to split the problem into "familiar statically indeterminate beams" (l. 582); both should read determinate, as ll. 799 and 819 say. At ll. 621–622 the double-primed case is said to be "associated with the reaction moment"; it is associated with the roller's reaction force $F=R_2$.
