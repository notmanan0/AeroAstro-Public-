---
title: "SESA2028 S8 - Virtual Work and Castigliano Theorems"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 8
tags: [sesa2028, structures, virtual-work, castigliano, energy-methods]
date: 2026-10-30
status: lectured
coverage: "SL3 (2026-02-04, ll. 240–482), SL4 (2026-02-11), SL5 (2026-02-13), SL6 and the recorded L-frame video (2026-02-18)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
next_topics: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
key_concepts: ["[[Principle of Virtual Work]]", "[[Unit Load Method]]", "[[Castigliano Theorem]]", "[[Castigliano Second Theorem]]", "[[Complementary Energy]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL9 - Energy methods 2 - Virtual Work and Strain Energy Solutions.pdf", "02 - Sources/Structures Lectures/SL15 - EnergyMethods 2 - The Pricinple of Virtual Work 1.pdf", "02 - Sources/Structures Lectures/SL16 - EnergyMethods 3 - The Pricinple of Virtual Work 2.pdf", "02 - Sources/Structures Lectures/SL17 - EnergyMethods 4 - The Pricinple of Virtual Work 3.pdf", "02 - Sources/Structures Lectures/SL18 - EnergyMethods 5 - Castigilianos Theorems.pdf", "02 - Sources/Structures Lectures/Structures Additional session- Energy Methods.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-11 - SL4 Energy Method. General virtual work.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-13 - SL5 Energy method. Castigliano.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-18 - SL6 Energy method. Asymmetric beams.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-18 - Redundant video.txt"]
---

# SESA2028 S8 - Virtual Work and Castigliano Theorems

> [!abstract] Summary
> Conservation of energy gives a deflection only where a load acts and in its direction. The principle of virtual work (PVW) removes that limit: put a virtual (usually unit) force where the displacement is wanted, and the external virtual work of that force through the real displacement equals the internal virtual work of its member forces or moments through the real deformations, so $u=\sum p_iP_iL_i/E_iA_i$ for a truss and $u=\int M^*M/EI\,dx$ for a beam. Castigliano's theorems say the same thing as derivatives: a force is $\partial U/\partial u$, a displacement is $\partial C/\partial F$, and for a linear structure $C=U$ so $u=\partial U/\partial F$. A dummy load, set to zero after differentiating, gives displacements where no load acts, and setting a derivative to zero handles statically indeterminate structures.

> [!summary]- Exam use: quick path
> - **Use it when:** you need a deflection or rotation at a point, or in a direction, where no load acts; a deflection of a truss, frame or curved member; a redundant reaction or moment; or the force needed to impose a known displacement.
> - **Assumptions:** linear elastic (essential for Castigliano's second theorem), small displacements, quasi-static loading, no body forces; axial and shear energy of beams neglected unless stated (Euler–Bernoulli).
> - **Method:** 1. Real system: member forces $P_i$ or moments $M(x)$, segment by segment. 2. Virtual system: unit force (or unit moment) at the point and in the direction wanted, giving $p_i$ or $M^*(x)$ with the same sign convention. 3. $u=\sum p_iP_iL_i/E_iA_i$ or $\int M^*M/EI\,dx$, member by member. 4. Or Castigliano: write $U(F,Q)$, $u=\partial U/\partial Q$, then $Q=0$. 5. Indeterminate: set the redundant's displacement or rotation, $\partial U/\partial R$, to zero.
> - **Common mistakes:** different sign conventions (or a different origin for $x$) in the real and virtual moment equations; putting the dummy load at the real load rather than where the displacement is wanted.
> - **Practise:** [[#The L-frame pet house]] · [[#Stiffness of a proving ring]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q2 - Quarter-circular cantilever|Tutorial 1 Q2]]

Conservation of energy, $W_e=U$ ([[SESA2028 S7 - Strain Energy and Conservation of Energy|S7]]), balances the work done at the one point where the load acts, so it gives the deflection there, in the load's direction, and nowhere else. It has nothing to say about how far the loaded joint of a truss moves sideways under a vertical load, because no external work is done sideways. Solving the joint geometry directly is possible but means a pair of quadratic equations for every joint between the support and the load.

Virtual work imagines a second, separate load case. A small force is placed at the point of interest, in the direction of interest, and the structure is then allowed to deform under the real loads. That imagined force does work through the real displacement at its point, and its own internal forces do work through the real member deformations; the two must match. Since the imagined force is chosen as 1, the work it does is the displacement itself. The force never exists in the real structure: it is a label that picks out the one displacement wanted.

Castigliano's theorems express the same energy balance as derivatives of the strain energy. They are often faster when the loading is already written algebraically, and the derivative form makes indeterminate problems (a propped beam, a closed ring) almost automatic: the unknown redundant is whatever makes the energy stationary.

## 1. The principle of virtual work

A particle is in static equilibrium under forces $\mathbf F_1,\dots,\mathbf F_n$, so their resultant is zero:

$$
\mathbf F_R=\sum_{k=1}^n\mathbf F_k=\mathbf 0 .
$$

Give the particle a **virtual displacement** $\boldsymbol\Delta$: any displacement that need not actually happen but is geometrically possible. During it the forces are held constant and parallel to their original lines of action. The virtual work is

$$
W^*=\sum_{k=1}^n\mathbf F_k\cdot\boldsymbol\Delta .
$$

Take the common displacement outside the sum:

$$
W^*=\left(\sum_{k=1}^n\mathbf F_k\right)\cdot\boldsymbol\Delta=\mathbf F_R\cdot\boldsymbol\Delta=0 .
$$

The converse holds too: if $\mathbf F_R\cdot\boldsymbol\Delta=0$ for every possible $\boldsymbol\Delta\neq\mathbf 0$, then $\mathbf F_R=\mathbf 0$ and the particle is in equilibrium. So the principle of virtual work is an equilibrium statement: for quasi-static loading, a system of forces in equilibrium does zero net work in any virtual displacement. In scalar form (as on the slides), with $u_k$ the displacement components along the forces, $F_1u_1+F_2u_2+\dots+F_nu_n=0$.

A deformable body in equilibrium has every particle in equilibrium. Summing the zero virtual work of every particle, the forces split into external loads, which act on the boundary, and internal forces, which act between particles and do work through the relative movement of neighbouring particles, that is, through the strain. Hence

$$
W^*_{ext}=W^*_{int},
$$

and for a truss with $j$ loaded joints and $n$ members, where member force $P_i$ moves through its extension $\Delta_i$,

$$
\sum_{j}F_ju_j=\sum_{i=1}^{n}P_i\Delta_i .
$$

For a continuous body the internal work is the stress doing work through the strain over the volume, and the external work is the boundary traction $\mathbf T$ doing work through the boundary displacement:

$$
\int_S\mathbf T^*\cdot\mathbf u\,dS=\int_V\boldsymbol\sigma^*:\boldsymbol\varepsilon\,dV ,
$$

where $\boldsymbol\sigma^*:\boldsymbol\varepsilon=\sigma^*_{xx}\varepsilon_{xx}+\sigma^*_{yy}\varepsilon_{yy}+\dots$ is the sum of matching products ([[Principle of Virtual Work]]). The stars mark the virtual system; unstarred quantities belong to the real loading. Both forms neglect body forces such as gravity and assume quasi-static loading.

Two features make this useful. The force system and the displacement system need not belong to the same load case: any set of forces in equilibrium may be paired with any compatible set of displacements. And there is no factor of $\tfrac12$, because the virtual forces are already at full value while the real displacements happen.

## 2. Virtual forces in a truss: the unit-load formula

Using the real forces in $\sum Fu=\sum P\Delta$ only reproduces conservation of energy. With several loads it is worse, since every load contributes an unknown displacement to the left-hand side. The fix is to pair the real displacements with a separate, virtual set of forces.

Suppose the joint B of a truss carries no load and its horizontal displacement $u_B$ under a real load $F$ is wanted. Apply the virtual force $F^*$ at B, horizontally, first. On its own it produces member forces $P_i^*$, extensions $\Delta_i^*$ and a displacement $u_B^*$ at B. Then, with $F^*$ still in place, apply the real load $F$, which produces member forces $P_i$, extensions $\Delta_i$, and a displacement $u$ at its own point and $u_B$ at B.

The external work has three parts. $F^*$ ramps up through $u_B^*$; $F$ ramps up through $u$; and $F^*$, already at full value, rides through $u_B$:

$$
W_e=\tfrac12F^*u_B^*+\tfrac12Fu+F^*u_B .
$$

The last term has no half because $F^*$ is constant while $F$ is being applied. The internal energy follows from the total member forces $P_i+P_i^*$:

$$
U=\sum_i\frac{\left(P_i+P_i^*\right)^2L_i}{2E_iA_i}.
$$

Expand the square:

$$
U=\sum_i\frac{P_i^{*2}L_i}{2E_iA_i}+\sum_i\frac{P_i^2L_i}{2E_iA_i}+\sum_i\frac{P_i^*P_iL_i}{E_iA_i}.
$$

The virtual problem on its own satisfies conservation of energy, so the first sum equals $\tfrac12F^*u_B^*$. The real problem on its own does the same, so the second sum equals $\tfrac12Fu$. Set $W_e=U$ and cancel those two pairs:

$$
F^*u_B=\sum_i\frac{P_i^*P_iL_i}{E_iA_i}.
$$

Recognise $P_iL_i/E_iA_i=\Delta_i$, the real extension of member $i$:

$$
F^*u_B=\sum_iP_i^*\Delta_i .
$$

This is the PVW with virtual forces and real displacements. Choosing $F^*=1$ removes the division, and writing $p_i$ for the member forces due to that unit load gives the unit-load method ([[Unit Load Method]]):

$$
\boxed{u_B=\sum_i p_i\Delta_i=\sum_i\frac{p_iP_iL_i}{E_iA_i}}
$$

Any other value of $F^*$ gives the same $u_B$ once it is divided out, since every $P_i^*$ scales with $F^*$. In practice two truss problems are solved side by side, one with the real load (giving $P_i$ and hence $\Delta_i$) and one with the unit load (giving $p_i$). The real load has not disappeared: it lives inside every $\Delta_i$. Repeating with a unit load horizontally ($F_x^*=1$) and vertically ($F_y^*=1$) at each joint maps out the whole displaced shape. A positive answer means the joint moves in the direction of the unit load.

### Example: the three-bay truss

The truss below is pinned to a wall at B and F, with 2 m bays; every member has $A=1000$ mm² and $E=200$ GPa, and D carries 10 kN downwards. Find the displacements of D and G.

![[structures_s8_truss_real_and_unit.png|900]]

The method of joints gives the real forces. At D only CD and GD meet, so vertical equilibrium needs $P_{GD}\sin45^\circ=-10$ kN, giving $P_{GD}=-14.14$ kN (compression), and horizontal equilibrium then gives $P_{CD}=+10$ kN. Working back through G and C gives the rest:

| Member | $P_i$ (kN) | $L_i$ (mm) | $\Delta_i=P_iL_i/EA$ (mm) | $p_i$, $F_x^*=1$ at D | $p_i$, $F_y^*=1$ (down) at G |
|---|---|---|---|---|---|
| BC | $+20$ | 2000 | $+0.2$ | $+1$ | $+1$ |
| CD | $+10$ | 2000 | $+0.1$ | $+1$ | $0$ |
| FG | $-10$ | 2000 | $-0.1$ | $0$ | $0$ |
| FC | $-14.14$ | 2828 | $-0.2$ | $0$ | $-1.414$ |
| GC | $+10$ | 2000 | $+0.1$ | $0$ | $+1$ |
| GD | $-14.14$ | 2828 | $-0.2$ | $0$ | $0$ |

The vertical displacement of D, where the load acts, needs no virtual system: conservation of energy gives $\tfrac12(10\text{ kN})v_D=\tfrac12\sum P_i\Delta_i$. Sum the products in kN·mm:

$$
\sum P_i\Delta_i=20(0.2)+10(0.1)+(-10)(-0.1)+(-14.14)(-0.2)+10(0.1)+(-14.14)(-0.2)=12.66,
$$

so

$$
v_D=\frac{12.66}{10}=1.27\text{ mm (down)}.
$$

For the horizontal displacement of D, put $F_x^*=1$ at D. D has only CD and GD, and the unit load is horizontal, so GD carries no force and CD carries $+1$. At G, with GD unloaded, GC and FG are zero too, and at C the force in CD passes straight into BC. Only BC and CD carry load:

$$
u_D=(1)(0.2)+(1)(0.1)=0.30\text{ mm},
$$

positive, so D moves 0.30 mm away from the wall. For G, a horizontal unit load loads only FG, so $u_G=(1)(-0.1)=-0.10$ mm: G moves 0.10 mm towards the wall as FG shortens. A downward unit load at G loads GC, FC and BC:

$$
v_G=(1)(0.2)+(-1.414)(-0.2)+(1)(0.1)=0.58\text{ mm (down)}.
$$

A downward unit load at D, where the real load is, gives $p_i=P_i/10$ kN in every member, so $v_D=\sum p_i\Delta_i=12.66/10=1.27$ mm, the same as conservation of energy. The unit-load method contains conservation of energy as the special case where the virtual load sits on the real one.

> [!check] Against the joint-by-joint geometry
> The same displacements follow from compatibility, without energy. Joint C must sit where BC has grown by 0.2 mm and FC has shortened by 0.2 mm, which gives two quadratics in $(u_{xC},u_{yC})$; solving them numerically gives $u_{xC}=0.19994$ mm and $u_{yC}=0.48284$ mm. The unit-load method, with $p=+1$ in BC for a horizontal load at C and $p_{BC}=+1$, $p_{FC}=-1.414$ for a vertical one, gives $0.200$ mm and $0.483$ mm. The tiny difference is the second-order geometry that the small-displacement theory drops, and to reach D the geometric route would need three such pairs.

## 3. Beams and frames

For a beam the external virtual work is easy. A unit virtual force $F^*=1$ at the point of interest gives

$$
\int_S\mathbf T^*\cdot\mathbf u\,dS=F^*u=u .
$$

The internal virtual work takes more thought. In an Euler–Bernoulli beam (bending deformation only) the only stress that matters is $\sigma_{xx}$, so the double contraction keeps a single product:

$$
\int_V\boldsymbol\sigma^*:\boldsymbol\varepsilon\,dV=\int_V\sigma^*_{xx}\,\varepsilon_{xx}\,dV .
$$

The virtual stress comes from the virtual moment by the bending formula:

$$
\sigma^*_{xx}=\frac{M_z^*(x)\,y}{I_{zz}} .
$$

The real strain comes from the real stress through Hooke's law in one dimension, the constitutive law without which no deflection can be found:

$$
\varepsilon_{xx}=\frac{\sigma_{xx}}{E}=\frac{M_z(x)\,y}{EI_{zz}} .
$$

Substitute both, with $dV=dA\,dx$:

$$
\int_V\sigma^*_{xx}\varepsilon_{xx}\,dV=\int_0^L\int_A\frac{M_z^*y}{I_{zz}}\cdot\frac{M_zy}{EI_{zz}}\,dA\,dx .
$$

The moments depend on $x$ only, and for a uniform beam $E$ and $I_{zz}$ are constants, so the area integral separates:

$$
\int_V\sigma^*_{xx}\varepsilon_{xx}\,dV=\frac{1}{EI_{zz}^2}\int_0^LM_z^*M_z\,dx\int_Ay^2\,dA .
$$

The remaining area integral is the second moment of area, $\int_Ay^2\,dA=I_{zz}$:

$$
\int_V\sigma^*_{xx}\varepsilon_{xx}\,dV=\frac{1}{EI_{zz}}\int_0^LM_z^*M_z\,dx .
$$

Equating to the external virtual work gives the unit-load formula for beams:

$$
\boxed{u=\int_0^L\frac{M_z^*(x)\,M_z(x)}{EI_{zz}}\,dx}
$$

where $M_z$ is the bending moment distribution caused by the real loads and $M_z^*$ the distribution caused by the unit force. A unit virtual moment in place of the unit force gives the rotation there. Frames are integrated member by member, each with its own coordinate, and the sum is taken at the end. Moments, shear forces and axial forces are **stress resultants**, the integrated effect of the internal stresses over the section, which is why the volume integral collapses to an integral of moments along the length.

Two energy terms are left out. Axial energy in frame members is far smaller than bending energy in slender members, so the axial force a horizontal arm passes into a vertical leg is normally neglected. Shear deformation is neglected too: including it adds a term $\int Q^*Q/(kGA)\,dx$ and turns the model into a Timoshenko beam, which matters only for deep, short beams (see the shear deflection estimate in [[SESA2028 S7 - Strain Energy and Conservation of Energy#Shear deflection of a cantilever|S7]], under 1 % at $L=10h$).

Every structural problem needs the same four pieces of information: the loading (equilibrium), the boundary conditions, any geometric compatibility conditions (essential for an indeterminate structure), and the material's constitutive law (here Young's modulus). Equilibrium alone gives moments and stresses; only the constitutive law turns them into strains and so into deflections.

## 4. Strain energy and complementary energy

### Force from the strain energy

A truss with loads $F_1$ at D and $F_2$ elsewhere is in equilibrium with member forces $P_i$ and real displacements $u_1$, $u_2$, $\Delta_i$. The PVW with real forces gives

$$
F_1u_1+F_2u_2=P_1\Delta_1+P_2\Delta_2+\dots+P_n\Delta_n .\tag{1}
$$

Let D move a small extra amount $\delta u_1$ along $F_1$ while $u_2$ is held. The members are connected, so each extends by a small extra $\delta\Delta_i$, and the forces stay in equilibrium:

$$
F_1(u_1+\delta u_1)+F_2u_2=P_1(\Delta_1+\delta\Delta_1)+\dots+P_n(\Delta_n+\delta\Delta_n).\tag{2}
$$

Subtract (1) from (2):

$$
F_1\,\delta u_1=P_1\,\delta\Delta_1+P_2\,\delta\Delta_2+\dots+P_n\,\delta\Delta_n=\sum_iP_i\,\delta\Delta_i .
$$

Each $P_i\,\delta\Delta_i$ is the strip of area under member $i$'s force–extension curve, that is, its increment of strain energy, so the sum is the increment of total strain energy:

$$
F_1\,\delta u_1=\delta U .
$$

With every other displacement held, $\delta U=(\partial U/\partial u_1)\,\delta u_1$, and so

$$
\boxed{F_j=\frac{\partial U}{\partial u_j}}
$$

The external force at a joint is the partial derivative of the strain energy with respect to the displacement at that joint, in line with the force. This is **Castigliano's first theorem**. The argument only used the area under the curve, so it holds whether the material is linear or not, provided it is elastic.

### Displacement from the complementary energy

Perturb the force instead: $F_1\to F_1+\delta F_1$ with $F_2$ held, so the member forces change by $\delta P_i$ while the displacements are kept at their values:

$$
(F_1+\delta F_1)u_1+F_2u_2=(P_1+\delta P_1)\Delta_1+\dots+(P_n+\delta P_n)\Delta_n .
$$

Subtract (1):

$$
\delta F_1\,u_1=\delta P_1\,\Delta_1+\dots+\delta P_n\,\Delta_n=\sum_i\delta P_i\,\Delta_i .
$$

On a force–displacement plot, $\delta P\,\Delta$ is a strip to the left of the curve, between it and the force axis. The area in that region is the **complementary energy** $C$ ([[Complementary Energy]]):

$$
C=\int_0^P\Delta\,dP,\qquad U=\int_0^\Delta P\,d\Delta .
$$

So the right-hand side is $\delta C$, and

$$
\delta F_1\,u_1=\delta C\quad\Longrightarrow\quad \boxed{u_j=\frac{\partial C}{\partial F_j}}
$$

The displacement of a joint in the direction of its force is the partial derivative of the complementary energy with respect to that force. The two areas together fill the rectangle under the final point of the curve, for any elastic system:

$$
U+C=P\Delta .
$$

For a linear elastic system the curve is a straight line through the origin, the two triangles are equal, and

$$
U=C=\tfrac12P\Delta .
$$

> [!check] When $C\neq U$
> For a nonlinear elastic member with $P=k\Delta^2$: $U=\int_0^\Delta k\Delta^2\,d\Delta=\tfrac13k\Delta^3$, and $C=P\Delta-U=\tfrac23k\Delta^3$. Writing $C$ in terms of $P$, with $\Delta=(P/k)^{1/2}$, gives $C=\tfrac23P^{3/2}k^{-1/2}$, and $\partial C/\partial P=(P/k)^{1/2}=\Delta$ as it should. But $U=\tfrac13P^{3/2}k^{-1/2}$ in terms of $P$, and $\partial U/\partial P=\tfrac12\Delta$, which is wrong by a factor of 2. Differentiating $U$ with respect to a force only works when the structure is linear.

## 5. Castigliano's theorems

For a linear elastic structure $C=U$, so the complementary-energy result can be written with the strain energy, which is the quantity already known for bars, beams and shafts. That gives the pair:

$$
\text{first theorem:}\quad F_i=\frac{\partial U}{\partial u_i},\qquad\qquad \text{second theorem:}\quad u_i=\frac{\partial U}{\partial F_i}\quad(\text{linear elastic}).
$$

The first is used to find a force when a displacement is known, the second to find a displacement when the force is known ([[Castigliano Theorem]], [[Castigliano Second Theorem]]). The same reasoning, with a moment working through a rotation or a torque through a twist, gives

$$
\theta_i=\frac{\partial U}{\partial M_i},\qquad \theta_i=\frac{\partial U}{\partial T_i}.
$$

For a beam under a point load $F$, with $U=\int_0^LM^2/2EI\,dx$, the second theorem can be used in two orders. Integrate first, then differentiate:

$$
v=\frac{\partial}{\partial F}\int_0^L\frac{M^2}{2EI}\,dx .
$$

Or differentiate under the integral first, by the chain rule $\partial(M^2)/\partial F=2M\,\partial M/\partial F$:

$$
v=\int_0^L\frac{M}{EI}\frac{\partial M}{\partial F}\,dx .
$$

The second form is usually less algebra, and it shows why the methods agree: $\partial M/\partial F$ is the moment produced by a unit value of $F$, which is $M^*$, so this is the unit-load formula of §3 again.

### Castigliano or the PVW?

Castigliano's theorems can be applied at a point with several loads, but only at a point where an external load is applied, and only in that load's direction. The PVW can be applied at any point of the structure. The two combine: add a dummy (virtual) force $Q$ at the point and in the direction where the displacement is wanted, write $U(F,Q)$, differentiate with respect to $Q$, and then set $Q=0$:

$$
u_Q=\left.\frac{\partial U(F,Q)}{\partial Q}\right|_{Q=0}.
$$

The dummy load goes where the displacement is wanted, never automatically at the real load. Because the theorem relies on superposition, this works only for a linear structure.

## 6. Statically indeterminate structures

A structure is statically determinate when the equilibrium equations are as many as the unknown reactions. A propped cantilever has three unknowns (the wall moment, the wall force and the prop force) but only two independent equilibrium equations for vertical loading, so one reaction is redundant. The missing equation is a compatibility condition from the physical picture: the prop does not move, the clamped end does not rotate, a symmetric section does not rotate.

Energy methods express such a condition as a derivative. Treat the redundant reaction $R$ as an external load, write $U(R,\text{loads})$, and apply the second theorem at the support:

$$
\frac{\partial U}{\partial R}=\text{displacement at }R=0 .
$$

For an internal redundant, such as the moment at a cut in a closed ring, the derivative with respect to that moment is the relative rotation of the two faces of the cut, which is zero because the ring is continuous. Either way the redundant is the value that makes $U$ stationary. Once it is known, the deflection anywhere follows from a unit load or a dummy load as usual, and the virtual system may use any statically determinate version of the structure, because the virtual forces only have to be in equilibrium.

## Worked examples

### Concentric tubes under a common shortening

Two hollow cylinders are arranged concentrically between rigid end plates, so both shorten by the same amount. The inner tube is aluminium ($E=70$ GPa) with diameters 6 mm and 7 mm; the outer shell is unidirectional carbon fibre ($E=130$ GPa) with diameters 7 mm and 8 mm; both are 760 mm long. Find the force needed to shorten the assembly by $\delta=0.1$ mm.

The displacement is given and the force is wanted, so this is the first theorem: write $U$ in terms of $\delta$ and differentiate. Both tubes shorten by $\delta$, like springs in parallel, so tube $i$ carries

$$
\delta=\frac{P_iL}{E_iA_i}\quad\Longrightarrow\quad P_i=\frac{E_iA_i}{L}\delta .
$$

Its strain energy, in terms of $\delta$, is

$$
U_i=\frac{P_i^2L}{2E_iA_i}=\frac{1}{2}\frac{E_iA_i}{L}\delta^2 .
$$

Summing the two tubes:

$$
U=\frac{\delta^2}{2L}\left(E_1A_1+E_2A_2\right).
$$

Differentiate with respect to $\delta$:

$$
F=\frac{\partial U}{\partial\delta}=\frac{\delta}{L}\left(E_1A_1+E_2A_2\right).
$$

The areas are

$$
A_{CF}=\frac\pi4\left(8^2-7^2\right)=11.78\text{ mm}^2,\qquad A_{Al}=\frac\pi4\left(7^2-6^2\right)=10.21\text{ mm}^2 .
$$

The axial stiffnesses are $E_{CF}A_{CF}=130\,000\times11.78=1.532\times10^6$ N and $E_{Al}A_{Al}=70\,000\times10.21=0.715\times10^6$ N, so

$$
F=\frac{0.1}{760}\left(1.532+0.715\right)\times10^6=296\text{ N}.
$$

The carbon shell carries 202 N and the aluminium 94 N, in proportion to their $EA$.

> [!check] Energy and work
> The stored energy is $U=\tfrac12(2956\text{ N/mm})(0.1)^2=14.8$ N·mm, and $\tfrac12F\delta=\tfrac12(296)(0.1)=14.8$ N·mm, as conservation of energy requires.

### Tip deflection of a cantilever

A cantilever of length $L$ carries $F$ at its tip. Measure $x$ from the tip, so $M=-Fx$ and $\partial M/\partial F=-x$. The second theorem, differentiating first:

$$
v=\int_0^L\frac{(-Fx)(-x)}{EI}\,dx=\frac{F}{EI}\int_0^Lx^2\,dx=\frac{FL^3}{3EI}.
$$

Conservation of energy gives the same, since the load and the wanted displacement coincide: $\tfrac12Fv=\int_0^LF^2x^2/2EI\,dx=F^2L^3/6EI$.

### Midspan deflection under a uniform load

A simply supported beam of span $L$ carries a uniform load $w$; find the midspan deflection. No point load acts at midspan, so add a dummy load $F$ there. Each support then carries $wL/2+F/2$, and for the left half, $0\le x\le L/2$,

$$
M=\frac{wL}{2}x-\frac{wx^2}{2}+\frac F2x ,\qquad \frac{\partial M}{\partial F}=\frac x2 .
$$

The right half mirrors the left, so the integral is twice the left half's. Apply the second theorem and set $F=0$ inside:

$$
v=2\int_0^{L/2}\frac{1}{EI}\left(\frac{wL}{2}x-\frac{wx^2}{2}\right)\frac x2\,dx .
$$

Multiply out:

$$
v=\frac{1}{EI}\int_0^{L/2}\left(\frac{wL}{2}x^2-\frac w2x^3\right)dx .
$$

Integrate:

$$
v=\frac{1}{EI}\left[\frac{wL}{6}x^3-\frac{w}{8}x^4\right]_0^{L/2}=\frac{1}{EI}\left(\frac{wL^4}{48}-\frac{wL^4}{128}\right).
$$

Over the common denominator 384:

$$
v=\frac{wL^4}{EI}\cdot\frac{8-3}{384}=\frac{5wL^4}{384EI}.
$$

Setting $F=0$ before integrating is allowed because $\partial M/\partial F$ has already been taken.

### Point load away from midspan

A simply supported beam carries $F$ at distance $a$ from the left support; find the deflection under the load. The load point is where the displacement is wanted, so the second theorem applies directly. The reactions are

$$
R_1=\frac{F(L-a)}{L},\qquad R_2=\frac{Fa}{L}.
$$

Measure $x$ from each support towards the load, so $M=R_1x$ on the left segment ($0\le x\le a$) and $M=R_2x'$ on the right ($0\le x'\le L-a$). Integrate first:

$$
U=\int_0^a\frac{R_1^2x^2}{2EI}\,dx+\int_0^{L-a}\frac{R_2^2x'^2}{2EI}\,dx'=\frac{R_1^2a^3}{6EI}+\frac{R_2^2(L-a)^3}{6EI}.
$$

Substitute the reactions:

$$
U=\frac{F^2(L-a)^2a^3}{6EIL^2}+\frac{F^2a^2(L-a)^3}{6EIL^2}=\frac{F^2a^2(L-a)^2}{6EIL^2}\left[a+(L-a)\right].
$$

The bracket is $L$:

$$
U=\frac{F^2a^2(L-a)^2}{6EIL}.
$$

Differentiate:

$$
v=\frac{\partial U}{\partial F}=\frac{Fa^2(L-a)^2}{3EIL}.
$$

With $a=L/2$ this is $FL^3/48EI$, the central-load result of [[SESA2028 S7 - Strain Energy and Conservation of Energy#Central load on a simply supported beam|S7]].

### Propped cantilever under a uniform load

A beam of span $L$ is clamped at one end and simply supported (propped) at the other, under a uniform load $w$; find the prop reaction and show the midspan deflection is $wL^4/192EI$.

The beam is indeterminate to the first degree. Take the prop reaction $R$ as the redundant and measure $x$ from the prop, so the moment (sagging positive) is

$$
M=Rx-\frac{wx^2}{2},\qquad\frac{\partial M}{\partial R}=x .
$$

The prop does not move, so by the second theorem

$$
\frac{\partial U}{\partial R}=\int_0^L\frac{M}{EI}\frac{\partial M}{\partial R}\,dx=\frac1{EI}\int_0^L\left(Rx^2-\frac{wx^3}{2}\right)dx=0 .
$$

Integrate:

$$
\frac{RL^3}{3}-\frac{wL^4}{8}=0\quad\Longrightarrow\quad R=\frac{3wL}{8}.
$$

For the midspan deflection, no load acts there, so use a unit load. The virtual system may be any determinate version of the beam; the simplest is the cantilever without the prop, with a downward unit load at $x=L/2$. Its moment is zero between the prop end and midspan and $M^*=-(x-L/2)$ beyond. Then

$$
v=\int_{L/2}^{L}\frac{1}{EI}\left[-\left(x-\frac L2\right)\right]\left(\frac{3wL}{8}x-\frac{wx^2}{2}\right)dx .
$$

Substitute $\xi=x-L/2$, $0\le\xi\le L/2$, and expand $\tfrac{3wL}{8}(\xi+\tfrac L2)-\tfrac w2(\xi+\tfrac L2)^2=-\tfrac w2\xi^2-\tfrac{wL}{8}\xi+\tfrac{wL^2}{16}$:

$$
v=\frac{w}{EI}\int_0^{L/2}\left(\frac{\xi^3}{2}+\frac{L\xi^2}{8}-\frac{L^2\xi}{16}\right)d\xi .
$$

Integrate:

$$
v=\frac{w}{EI}\left[\frac{\xi^4}{8}+\frac{L\xi^3}{24}-\frac{L^2\xi^2}{32}\right]_0^{L/2}=\frac{wL^4}{EI}\left(\frac{1}{128}+\frac{1}{192}-\frac{1}{128}\right)=\frac{wL^4}{192EI}.
$$

> [!check] Against the determinate beam
> The propped beam deflects $wL^4/192EI$ at midspan against $5wL^4/384EI=2.5\times(wL^4/192EI)$ for the same beam simply supported: the clamp cuts the midspan deflection by 60 %. The prop force $3wL/8$ is also the textbook value, and the clamp takes the remaining $5wL/8$.

### The L-frame pet house

An outdoor scratching post for a cat is an L-shaped timber frame clamped at its base D. The vertical leg C–D is $L=1.5$ m tall and the horizontal arm A–C is $s=1$ m long. The cat (10 kg) and its cubby house (5 kg) are idealised as one load $F_c=15g=147.2$ N at B, $c=0.25$ m in from the free end A, the worst case. The timber is C16 with $E=8.8$ GPa, available as 50 × 50 mm or 75 × 75 mm square sections. How far does A drop for each?

The load acts at B and the displacement is wanted at A, so use the PVW with a unit vertical force at A, solving the real and virtual problems side by side. Measure $x$ from A along the arm, and along the leg measure from C downwards; hogging moments come out negative with this convention, the same in both systems. Axial energy in the leg is neglected.

![[structures_s8_l_frame_moments.png|900]]

The real moments, from a free body cut at $x$, are

$$
M=0\ (\text{A–B}),\qquad M=-F_c(x-c)\ (\text{B–C}),\qquad M=-F_c(s-c)\ (\text{C–D}).
$$

On the leg the moment is constant, because the arm's load has a fixed lever arm $s-c$ about every point of the leg. The virtual moments, from the unit load at A, are

$$
M^*=-x\ (\text{A–C}),\qquad M^*=-s\ (\text{C–D}).
$$

The external virtual work is $F_y^*u_y=u_y$, since the only other place with a virtual force is the support D, which does not move. The internal virtual work splits into three integrals, and A–B contributes nothing because $M=0$ there:

$$
u_y=\frac{1}{EI}\left[\int_c^s(-x)\big(-F_c(x-c)\big)dx+\int_0^L(-s)\big(-F_c(s-c)\big)dx\right].
$$

The arm integral:

$$
\int_c^sF_c\left(x^2-cx\right)dx=F_c\left[\frac{x^3}{3}-\frac{cx^2}{2}\right]_c^s=F_c\left(\frac{s^3}{3}-\frac{cs^2}{2}-\frac{c^3}{3}+\frac{c^3}{2}\right)=F_c\left(\frac{s^3}{3}-\frac{cs^2}{2}+\frac{c^3}{6}\right).
$$

The leg integral has a constant integrand:

$$
\int_0^LF_cs(s-c)\,dx=F_c\,s\,L\,(s-c).
$$

So

$$
u_y=\frac{F_c}{EI}\left[\frac{s^3}{3}-\frac{cs^2}{2}+\frac{c^3}{6}+sL(s-c)\right].
$$

In millimetres, the bracket is

$$
\frac{1000^3}{3}-\frac{250(1000)^2}{2}+\frac{250^3}{6}+(1000)(1500)(750)=0.2109\times10^9+1.125\times10^9=1.336\times10^9\text{ mm}^3 .
$$

For the 50 mm section, $I=50^4/12=5.208\times10^5$ mm⁴ and $EI=8800\times5.208\times10^5=4.583\times10^9$ N·mm², so

$$
u_y=\frac{147.2\times1.336\times10^9}{4.583\times10^9}=42.9\text{ mm}.
$$

For the 75 mm section, $I=75^4/12=2.637\times10^6$ mm⁴ and

$$
u_y=\frac{147.2\times1.336\times10^9}{8800\times2.637\times10^6}=8.47\text{ mm}.
$$

The 75 × 75 mm timber is the better choice: 8.5 mm over a 1 m arm is a gentle slope, whereas 43 mm is not. Deflection goes as $1/I\propto1/b^4$, so the ratio of the two answers should be $(75/50)^4=5.06$, and $42.9/8.47=5.06$.

> [!tip] Where the deflection comes from
> The leg contributes $1.125/1.336=84\,\%$ of the deflection. The leg is longer than the loaded part of the arm and carries the full moment $F_c(s-c)$ all the way down, and its rotation at C swings the whole arm, with A at the end of a 1 m lever. Stiffening the leg alone would do most of the good.

### Stiffness of a proving ring

A load cell is a thin ring of radius $R$ and bending stiffness $EI$, squeezed by two equal and opposite forces $F$ along a diameter. Show that its stiffness is $K=F/u=EI/\left[R^3(\pi/4-2/\pi)\right]$.

![[structures_s8_ring_moment.png|900]]

Cutting the ring along the diameter perpendicular to the loads leaves each cut face, by symmetry, carrying $F/2$ in the load direction, no shear across it, and an unknown moment $M_0$: the ring is closed, so equilibrium alone cannot give $M_0$, and the problem is indeterminate. At angle $\phi$ round from the cut, the lever arm of the $F/2$ at the cut is $R(1-\cos\phi)$, so

$$
M(\phi)=M_0-\frac F2R\left(1-\cos\phi\right).
$$

The ring has four identical quarters, and along the curved length $ds=R\,d\phi$, so

$$
U=4\int_0^{\pi/2}\frac{M^2}{2EI}R\,d\phi=\frac{2R}{EI}\int_0^{\pi/2}M^2\,d\phi .
$$

The compatibility condition: by mirror symmetry the section at the cut does not rotate, so

$$
\frac{\partial U}{\partial M_0}=\frac{4R}{EI}\int_0^{\pi/2}M\frac{\partial M}{\partial M_0}\,d\phi=\frac{4R}{EI}\int_0^{\pi/2}M\,d\phi=0 .
$$

Substitute $M(\phi)$:

$$
\int_0^{\pi/2}\left[M_0-\frac{FR}{2}(1-\cos\phi)\right]d\phi=M_0\frac\pi2-\frac{FR}{2}\left(\frac\pi2-1\right)=0 .
$$

Solve for $M_0$:

$$
M_0=\frac{FR}{2}\left(1-\frac2\pi\right)=0.182\,FR .
$$

Put this back into $M(\phi)$; the constant terms combine:

$$
M(\phi)=\frac{FR}{2}\left(1-\frac2\pi\right)-\frac{FR}{2}+\frac{FR}{2}\cos\phi=\frac{FR}{2}\left(\cos\phi-\frac2\pi\right).
$$

The moment is largest under the loads, $M(\pi/2)=-FR/\pi=-0.318\,FR$, and changes sign at $\cos\phi=2/\pi$, $\phi=50.5^\circ$.

Now Castigliano's second theorem with respect to $F$ gives the approach $u$ of the two load points (the pair of forces does work $\tfrac12Fu$). With $M_0$ held, $\partial M/\partial F=-\tfrac R2(1-\cos\phi)$:

$$
u=\frac{\partial U}{\partial F}=\frac{4R}{EI}\int_0^{\pi/2}M\frac{\partial M}{\partial F}\,d\phi=\frac{4R}{EI}\int_0^{\pi/2}\frac{FR}{2}\left(\cos\phi-\frac2\pi\right)\left(-\frac R2\right)(1-\cos\phi)\,d\phi .
$$

Collect the constants:

$$
u=-\frac{FR^3}{EI}\int_0^{\pi/2}\left(\cos\phi-\frac2\pi\right)(1-\cos\phi)\,d\phi .
$$

Expand the integrand:

$$
\left(\cos\phi-\frac2\pi\right)(1-\cos\phi)=\cos\phi-\cos^2\phi-\frac2\pi+\frac2\pi\cos\phi .
$$

Integrate term by term over $0\le\phi\le\pi/2$, using $\int\cos\phi=1$ and $\int\cos^2\phi=\pi/4$:

$$
\int_0^{\pi/2}(\dots)\,d\phi=1-\frac\pi4-\frac2\pi\cdot\frac\pi2+\frac2\pi=\frac2\pi-\frac\pi4 .
$$

Therefore

$$
u=\frac{FR^3}{EI}\left(\frac\pi4-\frac2\pi\right)=0.149\,\frac{FR^3}{EI},\qquad K=\frac Fu=\frac{EI}{R^3\left(\frac\pi4-\frac2\pi\right)}=6.72\,\frac{EI}{R^3}.
$$

Castigliano is used twice: once with respect to the moment, to find the redundant, and once with respect to the force, to find the displacement.

> [!check] Holding $M_0$ or not makes no difference
> If $M_0(F)$ is substituted first, $M=\tfrac{FR}{2}(\cos\phi-\tfrac2\pi)$ and $\partial M/\partial F=\tfrac R2(\cos\phi-\tfrac2\pi)$. Then $u=\frac{FR^3}{EI}\int_0^{\pi/2}(\cos\phi-\tfrac2\pi)^2d\phi=\frac{FR^3}{EI}\left(\frac\pi4-\frac4\pi+\frac2\pi\right)$, the same $0.149\,FR^3/EI$. The extra term from $\partial M_0/\partial F$ is multiplied by $\partial U/\partial M_0$, which is zero. SymPy gives the same coefficient, $(\pi^2-8)/4\pi=0.1488$.

The same method handles any curved beam or closed frame: write $M$ round the member with $ds=R\,d\phi$, use symmetry for the compatibility conditions, and differentiate. Curved fuselage frames and engine rings are analysed this way, and the principles carry over to plates, shells and composite structures.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S7 - Strain Energy and Conservation of Energy]] · Next: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]
- Concepts: [[Principle of Virtual Work]] · [[Unit Load Method]] · [[Castigliano Theorem]] · [[Castigliano Second Theorem]] · [[Complementary Energy]] · [[Maxwell-Betti Reciprocity]]
- Problems: [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Energy methods applied to unsymmetrical sections: [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]. The same principle in finite elements: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]].

## Sources

- Slides: `SL9 - Energy methods 2 - Virtual Work and Strain Energy Solutions.pdf` (the 2025–26 deck: PVW, truss, strain and complementary energy, Castigliano, examples 1–4), `SL15`–`SL18` (the same material split over four lectures), and `Structures Additional session- Energy Methods.pdf` (truss by compatibility; the cat-house L-frame with full numbers, slides 9–30).
- Transcripts: `SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt` (ll. 240–482, PVW and the truss derivation), `2026-02-11 - SL4 Energy Method. General virtual work.txt` (virtual forces, beam form, propped cantilever), `2026-02-13 - SL5 Energy method. Castigliano.txt` (strain and complementary energy, concentric tubes, Castigliano), `2026-02-18 - SL6 Energy method. Asymmetric beams.txt` and `2026-02-18 - Redundant video.txt` (L-frame, beam examples, ring).
- The L-frame numbers come from the additional-session slides, because the 2025–26 L-frame slide is not in the sources (see [[#Transcript and slide slips]]). Maxwell–Betti reciprocity was not lectured in 2025–26.
- Every result in the worked examples was recomputed in Python: the truss by a joint-equilibrium solver and the compatibility quadratics by `fsolve`; the beams and the ring with SymPy. Figures: `generate_structures_s8_figures.py`.

## Self-study tasks

### Core

- [ ] Derive the unit-load formula for a truss from the three-term external work (SL3, 2026-02-04, ll. 330–480). → [[#2. Virtual forces in a truss: the unit-load formula]]
- [ ] Find the vertical and horizontal displacements of D and G in the three-bay truss (SL9 slides 8–9, worked in SL3–SL4). → [[#Example: the three-bay truss]]
- [ ] Derive $\int_V\boldsymbol\sigma^*:\boldsymbol\varepsilon\,dV=\int M_z^*M_z/EI_{zz}\,dx$ from the bending stress and Hooke's law; this step was deliberately left out of the lecture as an exercise (SL4, 2026-02-11, ll. 296–305). → [[#3. Beams and frames]]
- [ ] Propped cantilever: find the prop reaction by energy and show the midspan deflection is $wL^4/192EI$ (SL9 slide 17; SL4, ll. 345–405). → [[#Propped cantilever under a uniform load]]
- [ ] Derive $F=\partial U/\partial u$, $u=\partial C/\partial F$ and Castigliano's second theorem (SL5, 2026-02-13, ll. 1–300). → [[#4. Strain energy and complementary energy]] · [[#5. Castigliano's theorems]]
- [ ] Concentric tubes: the force to shorten the assembly 0.1 mm (SL9 slide 28; SL5, ll. 200–240). → [[#Concentric tubes under a common shortening]]
- [ ] SL9 examples 1–4 (cantilever tip, uniform load with a dummy load, point load at $a$, proving ring), discussed in SL6 with full solutions posted on Blackboard (2026-02-18, ll. 186–440). → [[#Tip deflection of a cantilever]] · [[#Midspan deflection under a uniform load]] · [[#Point load away from midspan]] · [[#Stiffness of a proving ring]]
- [ ] The L-frame: the deflection of A for both timber sections (2026-02-18, ll. 1–180; additional session slides 9–30). → [[#The L-frame pet house]]
- [ ] Structures tutorial 1, Q2–Q4. → [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q2 - Quarter-circular cantilever|Q2]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q3 - L-shaped cantilever|Q3]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q4 - Slope and displacement at B|Q4]]

### Further practice

- [ ] Solve joint C of the three-bay truss by the two compatibility quadratics and compare with the unit-load answer (additional session slides 4–8; SL5, ll. 321–400). → [[#Example: the three-bay truss]]
- [ ] Rework the L-frame with the load at the midpoint of the arm ($c=0.5$ m); you should get 27.4 mm and 5.42 mm (suggested, not lecturer-set). → [[#The L-frame pet house]]
- [ ] Show that, for $P=k\Delta^2$, differentiating $U$ with respect to $P$ gives half the true displacement (suggested, not lecturer-set). → [[#Displacement from the complementary energy]]

## Transcript and slide slips

> [!warning] Slide slip: member label (SL4, 2026-02-11, ll. 69–70)
> Where: [[#2. Virtual forces in a truss: the unit-load formula]].
>
> A slide in the truss derivation labels a member "AB" where it should read "BC"; the slip was confirmed in the lecture.

> [!warning] L-frame numbers (2026-02-18, ll. 19 and 169)
> Where: [[#The L-frame pet house]].
>
> The recording says the weight acts at the arm's midpoint (l. 19) and quotes 2.9 mm for the smaller section (l. 169). The 2025–26 slide is not in the sources. The additional-session version of the same problem puts the load 0.25 m from the free end and gives 42.9 mm and 8.47 mm, which this note reproduces. A midpoint load would give 27.4 mm, so 2.9 mm matches neither; it is most likely 42.9 mm with the first digit lost in transcription.

> [!warning] Slide slip: additional session, L-frame slide 24
> Where: [[#The L-frame pet house]].
>
> The intermediate line evaluates the arm integral as $s^3/2-cs^2/2$; the upper-limit term is $s^3/3$, as the slide's own final line ($s^3/3-cs^2/2+c^3/6$) shows.

> [!warning] Slide slips: complementary energy (SL9 slide 25, SL17 slide 7)
> Where: [[#Displacement from the complementary energy]].
>
> The perturbed sum is printed as $\delta P_1\Delta_1+\delta P_2\Delta_2+\dots+P_n\delta\Delta_n$; the last term should be $\delta P_n\Delta_n$, since the force, not the displacement, is perturbed.

> [!warning] Slide slip: second theorem (SL18 slide 5)
> Where: [[#5. Castigliano's theorems]].
>
> SL18 says the second theorem is "used to find external forces"; it finds displacements, as SL9 slide 32 and SL18's own summary state.

> [!warning] Transcript slip (2026-02-13, l. 223)
> Where: [[#Concentric tubes under a common shortening]].
>
> The tube shortening is transcribed as "P L by E I"; for an axial member it is $P_iL/E_iA_i$.
