---
title: "MATH2048 VC3 - Line Integrals and Conservative Fields"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 17
tags:
  - math2048
  - vector-calculus
  - line-integrals
  - conservative-fields
aliases: ["MATH2048 Lecture 22", "MATH2048 Lecture 26", "Work integral", "Potential function", "Path independence"]
date: 2026-10-30
status: lectured
coverage: "End of Lecture 21 (18 Nov 2024): the work integral built from small segments. Lecture 22 (19 Nov 2024): two line integrals of the same field along different paths, a closed loop, and a gradient field whose integral doesn't depend on the path. Lecture 26 (27 Nov 2024): conservative fields with F = -grad phi, why the work is a difference of potentials, the curl test, and finding a potential. All Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]", "[[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]"]
next_topics: ["[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]"]
key_concepts: ["[[Line Integrals]]", "[[Conservative Vector Fields]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 21.txt", "02 - Sources/Lectures/MATH2048 Lecture 22.txt", "02 - Sources/Lectures/MATH2048 Lecture 26.txt", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.2.1, §8.3.3)"]
---

# MATH2048 VC3 - Line Integrals and Conservative Fields

> [!abstract] Summary
> The work done moving along a curve $C$ through a force field $\mathbf F$ is the line integral $\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F(\mathbf r(t))\cdot\frac{d\mathbf r}{dt}\,dt$, an ordinary integral in the curve's parameter. It doesn't depend on how the curve is parametrised, but in general it does depend on the path. The exception is a conservative field, $\mathbf F=-\nabla\phi$, for which the chain rule gives $\int_C\mathbf F\cdot d\mathbf r=\phi(A)-\phi(B)$, so every path between the same points gives the same work and every closed loop gives zero. A field on a region without holes is conservative when $\nabla\times\mathbf F=\mathbf 0$, and its potential is found by integrating one component at a time.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for a line integral, whether a field is conservative, or a potential (B1 in each of 2023/24, 2024/25 and 2025/26).
> - **Assumptions:** the curve given as $\mathbf r(t)$ with a direction; for the shortcut, $\mathbf F$ smooth on a region with no holes.
> - **Method:** 1. Compute $\nabla\times\mathbf F$. 2. If it is zero, find $\phi$ and use $\phi(A)-\phi(B)$ (with $\mathbf F=-\nabla\phi$). 3. Otherwise read $x(t)$, $y(t)$, $z(t)$ off $\mathbf r(t)$ and substitute into $\mathbf F$. 4. Differentiate $\mathbf r(t)$ and form $\mathbf F\cdot\frac{d\mathbf r}{dt}$. 5. Integrate over the parameter range.
> - **Common mistakes:** using the parameter's limits as coordinates; mixing the sign conventions $\mathbf F=\nabla\phi$ and $\mathbf F=-\nabla\phi$, which flips the answer.
> - **Practise:** [[#Same field, two paths (L22)]] · [[#Finding a potential (L26)]] · [[#4. Past exam questions B1]]

Lift on a wing, flow through a pipe, work moving a charge: the useful numbers from a field come from integrating it, and the simplest integral runs along a curve (L26, ll. 1–15). If a small particle moves along a curve through a force field, only the field on the curve affects it, so the work done is built from the field at each point of the curve and the direction of travel there (L22, ll. 9–18).

The answer usually depends on the route, which is what makes the special case so useful. For a field that is the gradient of a potential, the work is just the change in potential energy, as for gravity, and no integral is needed. The curl, from [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities|VC2]], tests for that case.

---

## 1. The work integral (L21)

For a constant force moving a particle along a straight segment, the work is the force dotted with the displacement (L21, ll. 322–329). For a curve through a varying field, split the curve into many short segments (ll. 330–348). Along the segment from $\mathbf r(t)$ to $\mathbf r(t+\Delta t)$, treat the force as constant, say $\mathbf F(\mathbf r(t))$, so the work along it is about

$$
\mathbf F(\mathbf r(t))\cdot\big[\mathbf r(t+\Delta t)-\mathbf r(t)\big]\approx\mathbf F(\mathbf r(t))\cdot\frac{d\mathbf r}{dt}\,\Delta t .
$$

Adding the segments and letting $\Delta t\to0$ turns the sum into an integral, just as the Fourier series became the Fourier transform (ll. 343–366):

$$
W=\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F\big(\mathbf r(t)\big)\cdot\frac{d\mathbf r}{dt}\,dt .
$$

Everything is now a function of the single parameter $t$, so this is an ordinary one-dimensional integral, and the result is one number.

Three properties follow (ll. 367–384). The value doesn't depend on the parametrisation: speeding up the parameter shrinks $dt$ and enlarges $\frac{d\mathbf r}{dt}$ by the same factor. Reversing the direction of travel flips the sign. But a genuinely different curve samples the field at different places, so in general it gives a different answer; only special fields are path-independent.

## 2. Computing line integrals (L22)

### Same field, two paths (L22)

Take $\mathbf F=2xy\,\mathbf i+(x^2-z^2)\,\mathbf j-3xz^2\,\mathbf k$ and move from the origin to $(2,1,3)$ along two curves (ll. 28–46).

The curved path $C_1$ is $\mathbf r=2t\,\mathbf i+t^3\,\mathbf j+3t^2\,\mathbf k$, $0\leq t\leq1$. Read off $x=2t$, $y=t^3$, $z=3t^2$ and substitute (ll. 47–68):

$$
\mathbf F\big|_{C_1}=4t^4\,\mathbf i+(4t^2-9t^4)\,\mathbf j-54t^5\,\mathbf k .
$$

This is $\mathbf F$ only on this curve with this parameter, not anywhere else. The tangent is (ll. 69–76)

$$
\frac{d\mathbf r}{dt}=2\,\mathbf i+3t^2\,\mathbf j+6t\,\mathbf k .
$$

In an orthonormal basis the dot product multiplies matching components (ll. 77–85):

$$
\mathbf F\cdot\frac{d\mathbf r}{dt}=8t^4+(12t^4-27t^6)-324t^6=20t^4-351t^6 .
$$

The parameter runs from 0 to 1, so (ll. 86–98)

$$
\int_{C_1}\mathbf F\cdot d\mathbf r=\int_0^1(20t^4-351t^6)\,dt=4-\frac{351}7=-\frac{323}7\approx-46.1 .
$$

The straight path $C_2$ is $\mathbf r=2t\,\mathbf i+t\,\mathbf j+3t\,\mathbf k$ (ll. 114–171). A straight line is always start point plus (end minus start) times the parameter, so its tangent is a constant vector, $2\,\mathbf i+\mathbf j+3\,\mathbf k$. On it

$$
\mathbf F\big|_{C_2}=4t^2\,\mathbf i-5t^2\,\mathbf j-54t^3\,\mathbf k ,
$$

so

$$
\mathbf F\cdot\frac{d\mathbf r}{dt}=8t^2-5t^2-162t^3=3t^2-162t^3 ,
$$

and

$$
\int_{C_2}\mathbf F\cdot d\mathbf r=\Big[t^3-\frac{162}4t^4\Big]_0^1=1-\frac{81}2=-\frac{79}2=-39.5 .
$$

Same endpoints, different answers: this integral depends on the path (ll. 179–193).

### Round a closed loop

Go out along $C_1$ and back along $C_2$ reversed (ll. 199–239). Reversing $C_2$ flips its sign, so

$$
\oint\mathbf F\cdot d\mathbf r=-\frac{323}7+\frac{79}2=\frac{-646+553}{14}=-\frac{93}{14}\approx-6.6 .
$$

A particle taken round the loop and returned to its start has had net work done on it. That isn't paradoxical; some processes simply don't return all the energy put in.

![[m2048_vc_two_paths.png|620]]

### A gradient field on the same two paths

Now take $\mathbf F=y^2z\,\mathbf i+2xyz\,\mathbf j+xy^2\,\mathbf k$, which is $\nabla(xy^2z)$ (ll. 240–316). On $C_1$,

$$
\mathbf F=3t^8\,\mathbf i+12t^6\,\mathbf j+2t^7\,\mathbf k,\qquad\mathbf F\cdot\frac{d\mathbf r}{dt}=6t^8+36t^8+12t^8=54t^8 ,
$$

so $\int_{C_1}=\frac{54}9=6$. On $C_2$,

$$
\mathbf F=3t^3\,\mathbf i+12t^3\,\mathbf j+2t^3\,\mathbf k,\qquad\mathbf F\cdot\frac{d\mathbf r}{dt}=6t^3+12t^3+6t^3=24t^3 ,
$$

so $\int_{C_2}=\frac{24}4=6$. Both equal $xy^2z$ at $(2,1,3)$ minus its value at the origin, $6-0$. That is the conservative case.

> [!check] SymPy
> The four integrals are $-\frac{323}7$, $-\frac{79}2$, $6$ and $6$. The first field has $\nabla\times\mathbf F=2z\,\mathbf i+3z^2\,\mathbf j\neq\mathbf 0$, consistent with its path dependence.

## 3. Conservative fields (L26)

A **conservative** vector field is one that can be written as the gradient of a scalar field, its **potential** (ll. 22–35). This course uses the convention

$$
\mathbf F=-\nabla\phi ,
$$

with a minus sign, because $\phi$ is usually a potential energy and the force pushes towards lower energy, as with gravity or electrostatics (ll. 46–50). If the potential is an entropy, which increases, the sign is plus. Lecture 22's example used the plus sign, so watch which one a question uses. The potential is not unique: adding a constant leaves $\nabla\phi$ unchanged, just as the zero of potential energy can be the floor, the desk or the ceiling, since only differences matter (ll. 51–59).

### The work is a difference of potentials

For a curve from $A=\mathbf r(a)$ to $B=\mathbf r(b)$ (ll. 60–112):

$$
\mathbf F\cdot\frac{d\mathbf r}{dt}=-\Big(\frac{\partial\phi}{\partial x}\frac{dx}{dt}+\frac{\partial\phi}{\partial y}\frac{dy}{dt}+\frac{\partial\phi}{\partial z}\frac{dz}{dt}\Big).
$$

Along the curve $\phi$ is a function of $t$ through $x(t)$, $y(t)$, $z(t)$, and the chain rule says the bracket is exactly $\frac{d\phi}{dt}$. So

$$
\int_C\mathbf F\cdot d\mathbf r=-\int_a^b\frac{d\phi}{dt}\,dt=\phi(A)-\phi(B).
$$

The work is the drop in potential energy from start to end. It doesn't depend on the parametrisation, which was true for any field, and now it doesn't depend on the route either.

A closed loop starts and ends at the same point, so for a conservative field

$$
\oint_C\mathbf F\cdot d\mathbf r=0 .
$$

Lecture 22 argued it the other way round (ll. 327–342): split the loop at two points into two paths from $A$ to $B$; path independence makes them equal, and going back along one of them flips its sign, so the two halves cancel.

### When is a field conservative?

The test uses the identity $\nabla\times\nabla\phi=\mathbf 0$ from [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities|VC2]] (ll. 118–127): a gradient field has zero curl, so compute $\nabla\times\mathbf F$, and if it isn't zero the field is not conservative and the line integral must be done in full. Zero curl is enough provided $\mathbf F$ is defined and differentiable everywhere in the region and the region has no holes (ll. 128–137). This fails, for example, at a point charge, where the potential goes like one over the distance and blows up, or around a perfect insulator inside which the potential means nothing.

### Finding a potential (L26)

$\mathbf F=-\nabla\phi$ is three first-order PDEs (ll. 138–164):

$$
F_1=-\frac{\partial\phi}{\partial x},\qquad F_2=-\frac{\partial\phi}{\partial y},\qquad F_3=-\frac{\partial\phi}{\partial z}.
$$

Integrating in $x$ leaves a "constant" that can be any function of $y$ and $z$. Rather than integrate all three and match three sets of such functions, integrate the easiest one, then differentiate the result in another variable and compare (ll. 165–176).

The lecture's example (ll. 177–290) is

$$
\mathbf F=\big(2xy+\cos2y\big)\,\mathbf i+\big(x^2-2x\sin2y+2y\big)\,\mathbf j .
$$

First the curl. $F_1$ and $F_2$ don't involve $z$ and $F_3=0$, so only the $\mathbf k$ component can be non-zero:

$$
\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y}=(2x-2\sin2y)-(2x-2\sin2y)=0 .
$$

So $\mathbf F$ is conservative. Start with the easiest equation, $-\phi_z=0$, so $\phi=f(x,y)$. Then $-f_x=2xy+\cos2y$; integrate in $x$ holding $y$ fixed:

$$
f=-x^2y-x\cos2y+g(y).
$$

Differentiate in $y$ and match to $F_2$:

$$
-f_y=x^2-2x\sin2y-g'(y)=x^2-2x\sin2y+2y ,
$$

so $g'=-2y$ and $g=-y^2+C$. Hence

$$
\phi=-x^2y-x\cos2y-y^2+C .
$$

The constant $C$ doesn't matter (ll. 261–284). Either set it to zero, as the course does, or choose it so the potential vanishes somewhere meaningful, such as at infinity for gravity.

### Potential flow

In fluids a velocity field with zero curl is irrotational: small fluid elements don't spin relative to each other, though the flow as a whole can still turn (ll. 291–311). Then $\mathbf u=\nabla\phi$, and if the flow is also incompressible, $\nabla\cdot\mathbf u=0$, so $\nabla^2\phi=0$: the whole flow follows from one solution of [[MATH2048 PDE5 - Laplace's Equation|Laplace's equation]]. This is potential flow, the basis of much of incompressible aerodynamics. Most real flows do have vorticity, and then the velocity has to be split into an irrotational part and a part with no divergence.

## 4. Past exam questions B1

**2023/24 B1(b).** $\mathbf G=z^2\,\mathbf i+2y\,\mathbf j+2xz\,\mathbf k$ along $\mathbf r=t^2\,\mathbf i+e^t\,\mathbf j+t\,\mathbf k$, $0\leq t\leq1$. Directly, $\mathbf G=t^2\,\mathbf i+2e^t\,\mathbf j+2t^3\,\mathbf k$ and $\frac{d\mathbf r}{dt}=2t\,\mathbf i+e^t\,\mathbf j+\mathbf k$, so

$$
\int_C\mathbf G\cdot d\mathbf r=\int_0^1\big(4t^3+2e^{2t}\big)\,dt=1+(e^2-1)=e^2 .
$$

$\nabla\times\mathbf G=(0-0)\,\mathbf i+(2z-2z)\,\mathbf j+(0-0)\,\mathbf k=\mathbf 0$ on all of space, so $\mathbf G$ is conservative and the integral depends only on the endpoints. Indeed $\mathbf G=\nabla(xz^2+y^2)$, and $xz^2+y^2$ goes from $1$ at $(0,1,0)$ to $1+e^2$ at $(1,e,1)$.

**2024/25 B1(b)–(d).** $\mathbf G=\big(y\cos xy+ze^{xz}\big)\,\mathbf i+x\cos xy\,\mathbf j+xe^{xz}\,\mathbf k$, with $\nabla\phi=-\mathbf G$ as in the course convention. Integrate the $\mathbf j$ component in $y$: $-\phi_y=x\cos xy$ gives $\phi=-\sin xy+h(x,z)$. Then $-\phi_z=-h_z=xe^{xz}$ gives $h=-e^{xz}+k(x)$, and $-\phi_x=y\cos xy+ze^{xz}-k'(x)$ must equal $G_1$, so $k$ is constant:

$$
\phi=-\sin xy-e^{xz} .
$$

From $(0,0,0)$ to $(1,0,1)$, $\int\mathbf G\cdot d\mathbf r=\phi(A)-\phi(B)=(-1)-(-e)=e-1$. For $\mathbf H=\mathbf G+\sin(xyz)\,\mathbf k$, the extra term has curl $xz\cos(xyz)\,\mathbf i-yz\cos(xyz)\,\mathbf j\neq\mathbf 0$, so $\mathbf H$ is not conservative and its line integral depends on the path.

**2025/26 B1.** $\mathbf F=xyz\,\mathbf i+z^2\,\mathbf j+y^2\,\mathbf k$ has

$$
\nabla\times\mathbf F=(2y-2z)\,\mathbf i+xy\,\mathbf j-xz\,\mathbf k\neq\mathbf 0 ,
$$

so it is not conservative and the integral along $\mathbf r=3(t+1)\,\mathbf i+t\,\mathbf j+t^2\,\mathbf k$ from $(3,0,0)$ to $(6,1,1)$ must be done directly. With $t$ from 0 to 1, $\mathbf F=3t^3(t+1)\,\mathbf i+t^4\,\mathbf j+t^2\,\mathbf k$ and $\frac{d\mathbf r}{dt}=3\,\mathbf i+\mathbf j+2t\,\mathbf k$:

$$
\int_C\mathbf F\cdot d\mathbf r=\int_0^1\big(10t^4+11t^3\big)\,dt=2+\frac{11}4=\frac{19}4 .
$$

> [!check] SymPy
> $e^2$, $e-1$ and $\frac{19}4$, and the potential of the L26 example satisfies $-\nabla\phi=\mathbf F$ exactly.

## Transcript slips

> [!warning] Lectures 21, 22 and 26
> | Where | Transcript says | Correct |
> |---|---|---|
> | L22, l. 139 | "the x component is 2z" | $x=2t$ |
> | L22, l. 171 | "1 minus 82 on 2" | $1-\frac{81}2=-\frac{79}2$ |
> | L22, ll. 184–190 | $-\frac{323}7$ is "negative 6.6 roughly", "a factor of 6" from $-39.5$ | $-\frac{323}7\approx-46.1$; the two differ by about 17 %. $-6.6$ is the closed-loop value $-\frac{93}{14}$ |
> | L22, l. 293 | "2 plus 2I plus J plus 3K" | $2\,\mathbf i+\mathbf j+3\,\mathbf k$ |
> | L22, l. 325 | conservative fields "in lecture 27" | Lecture 26 |
> | L26, l. 23 | "negative grad 5" | $-\nabla\phi$ |
> | L26, l. 40 | potentials "go like the charge density" | they go like one over the distance to the charge, as l. 42 says |
> | L26, l. 66 | B is at "the lower point of the parameter" | the upper limit, $t=b$ |
> | L26, l. 231 | $f=-x^2y+x\cos2y+g(y)$ | $-x\cos2y$, corrected at l. 237 |
> | L26, l. 294 | "gradient of the velocity field being irrotational" | the velocity is the gradient of a potential, so it is irrotational |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]] · Next: [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]
- Concepts: [[Line Integrals]] · [[Conservative Vector Fields]] · [[Gradient and Directional Derivative]] · [[Divergence, Curl and the Laplacian]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] · [[MATH2048 Past Paper Solutions]]

## Sources

- Lectures 21 (18 Nov 2024), 22 (19 Nov 2024) and 26 (27 Nov 2024), Ian Hawke: `MATH2048 Lecture 21.txt`, `MATH2048 Lecture 22.txt`, `MATH2048 Lecture 26.txt`
- Vector calculus slides; lecture notes §8.2.1 and §8.3.3
- Problem Sheet 8 Q7; 2023/24, 2024/25 and 2025/26 exam questions B1

## Self-study tasks

Lecture 22 said line integrals "should be something that you should be able to hammer through at speed now" (l. 349), and Lecture 26 flagged scalar potentials as needed for the coursework (l. 313).

### Core

- [ ] PS8 Q7(a)–(c). Answers: $2$; $0$ (conservative, equal potentials at the ends); $4\pi+\frac{16\pi^2}3$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] Rework both L22 paths for the first field and confirm the loop value $-\frac{93}{14}$. → [[#Same field, two paths (L22)]]
- [ ] 2025/26 B1: show $\mathbf F$ is not conservative and integrate it. → [[#4. Past exam questions B1]]

### Further practice

- [ ] 2024/25 B1(b)–(d): find $\phi$ with $\nabla\phi=-\mathbf G$ and use it. → [[#4. Past exam questions B1]]
- [ ] Find the potential of the L26 example starting from the $\mathbf j$ equation instead, and check you get the same $\phi$ up to a constant (suggested, not lecturer-set). → [[#Finding a potential (L26)]]
