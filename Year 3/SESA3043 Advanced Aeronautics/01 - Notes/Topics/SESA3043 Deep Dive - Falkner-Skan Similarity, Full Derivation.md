---
title: "SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation"
module: "SESA3043 Advanced Aeronautics"
type: topic
stream: "Chapter 3: Methods for Boundary Layers"
order: 10.5
tags: [sesa3043, boundary-layer, falkner-skan, blasius, similarity, wedge-flow, shooting-method, derivation, deep-dive]
aliases: ["Falkner-Skan deep dive", "Falkner-Skan derivation in full", "Falkner-Skan similarity derivation"]
date: 2026-11-12
status: lectured
coverage: "Every step from the Prandtl boundary-layer equations with U_e = c x^m to the Falkner–Skan ODE (CH3-2 slides 75–96 and the Falkner–Skan Blackboard notes, lectured BL2 on 23 Oct), the wedge-flow origin of U_e and β, why similarity needs a power law, the wall and integral identities, and a shooting solution checked against the slide 96 table and the BL3 worked problem (5 Nov)"
parent: ["[[SESA3043 Advanced Aeronautics Hub]]"]
prerequisites: ["[[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]]", "[[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]", "[[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]]"]
next_topics: ["[[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method]]", "[[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]]"]
key_concepts: ["[[Blasius and Falkner-Skan Similarity Solutions]]", "[[Wedge and Corner Flows]]", "[[Prandtl Boundary-Layer Equations]]", "[[Shooting Method and the Blasius Solution]]"]
tutorial_sheets: ["03 - Exams & Past Papers/Ch3_Revision_Questions.pdf"]
sources: ["02 - Sources/Lectures/CH3-2 Blasius and Falkner-Skan(1).pdf", "02 - Sources/Lectures/Ch3_Notes_Falkner-Skan.pdf", "02 - Sources/Lectures/Ch3_Notes_Blasius.pdf", "02 - Sources/Lectures/23 October 2026 at 14_53_16.txt", "02 - Sources/Lectures/05 November 2026 at 13_59_07.txt"]
---

# SESA3043 Deep Dive - Falkner-Skan Similarity, Full Derivation

> [!abstract] Summary
> When the edge velocity is a power of the distance along the wall, $U_e=cx^m$, the laminar boundary layer keeps one shape and only stretches as it grows. The variables $\xi=\sqrt{2\nu x/[(m+1)U_e]}$, $\eta=y/\xi$ and $f=\psi/(U_e\xi)$ then turn the two boundary-layer PDEs into the single ODE $f'''+ff''+\beta(1-f'^2)=0$ with $\beta=2m/(m+1)$, the wedge angle divided by $\pi$. A power law is the only edge velocity that allows this, the wall curvature is $f'''(0)=-\beta$, and integrating the ODE across the layer gives $f''(0)=(1+\beta)\theta^*+\beta\eta^*$, the momentum integral equation in similarity form. Shooting reproduces every column of the course's Falkner–Skan table.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the Falkner–Skan equation from the boundary-layer equations, or for $\delta_{99}$, $\delta^*$, $\theta$ or $C_f$ on a wedge or near a stagnation point.
> - **Assumptions:** 2-D, steady, incompressible, laminar, attached; $U_e=cx^m$ with $x$ measured along the wall from the apex; $m\neq-1$.
> - **Method:** 1. Find $m$ from $U_e(x)$, then $\beta=2m/(m+1)$. 2. Form $\xi=\sqrt{2\nu x/[(m+1)U_e]}$. 3. Read $\eta_{99}$, $\eta^*$, $\theta^*$ and $f''(0)$ for that $\beta$ from the table. 4. $\delta_{99}=\eta_{99}\xi$, $\delta^*=\eta^*\xi$, $\theta=\theta^*\xi$, $C_f=2\nu f''(0)/(U_e\xi)$. 5. Check $H=\eta^*/\theta^*$ and $f''(0)=(1+\beta)\theta^*+\beta\eta^*$.
> - **Common mistakes:** using the Blasius $\xi$ without the $(m+1)$; taking $\theta^*=f''(0)$ for $\beta\neq0$, which holds only for the flat plate.
> - **Example:** [[#Stagnation point of a cylinder]] · **Exercise:** [[#A 90 degree wedge]]

A laminar layer on a flat plate grows like $\sqrt x$ and keeps its shape, because nothing in the problem supplies a length: the plate is semi-infinite and $U_e$ is constant. A power-law edge velocity keeps that property. Scale $x$ by any factor and $U_e=cx^m$ is only multiplied by a constant, so the outer flow still has no length of its own, and the profiles at different stations are again stretched copies of one another. The velocity profile is then a single function $u/U_e=f'(\eta)$ of one scaled wall distance, and the boundary-layer PDEs collapse to an ODE for that function.

The flows with $U_e=cx^m$ are the wedge and corner flows of Chapter 1. A symmetric wedge of included angle $\beta\pi$ speeds the outer flow up along its faces, $m>0$, and a wall that turns away from the flow at a convex corner slows it down, $m<0$. The exponent fixes the pressure gradient, $\mathrm dp/\mathrm dx=-\rho mU_e^2/x$, and the parameter $\beta=2m/(m+1)$ that appears in the ODE measures that gradient against the inertia of the layer. A favourable gradient ($\beta>0$) pushes the slow fluid near the wall along, so the profile fills out, the layer thins and the wall shear rises. An adverse gradient ($\beta<0$) empties the profile until, at $\beta=-0.19884$, the wall shear vanishes and the layer is about to separate. The compressed version of the derivation, with the bump picture and the effective body, is in [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions|3.2]].

## 1. Assumptions and the boundary-layer equations

The derivation uses these assumptions, each at a definite step:

- **two-dimensional and steady**: $w=0$ and $\partial/\partial t=0$, so a stream function exists and the equations are in $x$ and $y$ only;
- **incompressible**: $\rho$ constant, so continuity is $\partial u/\partial x+\partial v/\partial y=0$;
- **laminar**: no Reynolds stresses, so the only stress is $\mu\,\partial u/\partial y$;
- **thin layer**, $\delta\ll x$: the Prandtl boundary-layer approximations of [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers|1.4]] hold, so $\partial p/\partial y=0$ and the streamwise diffusion $\partial^2u/\partial x^2$ is negligible;
- **attached**: the solution ends where the wall shear reaches zero;
- **power-law edge velocity**: $U_e=cx^m$, with $x$ the distance along the wall from the apex or leading edge and $c$, $m$ constants.

Under these assumptions the layer obeys the [[Prandtl Boundary-Layer Equations|Prandtl boundary-layer equations]]:

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=0,
\qquad
u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=-\frac1\rho\frac{\mathrm dp}{\mathrm dx}+\nu\frac{\partial^2u}{\partial y^2}.
$$

The pressure is impressed by the outer flow, because $\partial p/\partial y=0$ carries the edge pressure down to the wall. Just outside the layer the flow is inviscid and steady, so Bernoulli holds along the edge:

$$
p+\tfrac12\rho U_e^2=\text{constant}.
$$

Differentiate with respect to $x$:

$$
\frac{\mathrm dp}{\mathrm dx}+\rho U_e\frac{\mathrm dU_e}{\mathrm dx}=0.
$$

Divide by $-\rho$:

$$
-\frac1\rho\frac{\mathrm dp}{\mathrm dx}=U_e\frac{\mathrm dU_e}{\mathrm dx}.
$$

The momentum equation therefore takes the form used throughout Chapter 3, with the pressure gradient written through the known edge velocity:

$$
u\frac{\partial u}{\partial x}+v\frac{\partial u}{\partial y}=U_e\frac{\mathrm dU_e}{\mathrm dx}+\nu\frac{\partial^2u}{\partial y^2}.
$$

With $U_e(x)$ supplied by the potential flow, this leaves two unknowns, $u$ and $v$, for two equations.

The stream function $\psi$ is defined by

$$
u=\frac{\partial\psi}{\partial y},\qquad v=-\frac{\partial\psi}{\partial x}.
$$

Continuity is then satisfied identically, because mixed partial derivatives commute:

$$
\frac{\partial u}{\partial x}+\frac{\partial v}{\partial y}=\frac{\partial^2\psi}{\partial x\,\partial y}-\frac{\partial^2\psi}{\partial y\,\partial x}=0.
$$

Substituting $u$ and $v$ into the momentum equation gives the six-term reduced boundary-layer equation, with the terms numbered as in the course:

$$
\underbrace{\frac{\partial\psi}{\partial y}}_{①}\underbrace{\frac{\partial^2\psi}{\partial x\,\partial y}}_{②}-\underbrace{\frac{\partial\psi}{\partial x}}_{③}\underbrace{\frac{\partial^2\psi}{\partial y^2}}_{④}=\nu\underbrace{\frac{\partial^3\psi}{\partial y^3}}_{⑤}+\underbrace{U_e\frac{\mathrm dU_e}{\mathrm dx}}_{⑥}.
$$

One third-order PDE in $\psi$ has replaced two PDEs in $u$ and $v$. The boundary conditions are no flow through the wall and no slip, $\psi=\partial\psi/\partial y=0$ at $y=0$, and $\partial\psi/\partial y\to U_e$ as $y\to\infty$.

| Symbol | Meaning |
|---|---|
| $x$ | distance along the wall from the apex (wedge) or leading edge (plate) |
| $y$ | distance normal to the wall |
| $U_e(x)=cx^m$ | edge velocity, the potential-flow speed along the wall |
| $m$ | velocity exponent; $\beta=2m/(m+1)$, the wedge angle divided by $\pi$ |
| $\xi(x)$ | similarity length, Falkner–Skan variable 1 |
| $\eta=y/\xi$ | similarity coordinate, variable 2 |
| $f(\eta)=\psi/(U_e\xi)$ | dimensionless stream function, variable 3; primes are $\mathrm d/\mathrm d\eta$ |
| $\eta^*$, $\theta^*$ | integral types A and B, $\int_0^\infty(1-f')\,\mathrm d\eta$ and $\int_0^\infty f'(1-f')\,\mathrm d\eta$ |

## 2. The edge velocity of a wedge

The power law comes from the complex potential of [[Wedge and Corner Flows]] ([[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#7. Wedge and corner flows|1.3 §7]]):

$$
\Phi=-kz^{m+1},\qquad k>0 .
$$

Write $z=re^{i\theta}$. Then

$$
\Phi=-kr^{m+1}e^{i(m+1)\theta}.
$$

The imaginary part is the stream function:

$$
\psi_{\text{pot}}=-kr^{m+1}\sin\left[(m+1)\theta\right].
$$

It vanishes on $\theta=0$ and on $\theta=\pm\pi/(m+1)$. The two rays $\theta=\pm\pi/(m+1)$ are the walls and $\theta=0$ is the dividing streamline that runs into the apex. The fluid fills the angle between the walls, $2\pi/(m+1)$, so the solid wedge occupies the rest of the full turn:

$$
\beta\pi=2\pi-\frac{2\pi}{m+1}.
$$

Put the right-hand side over the common denominator $m+1$:

$$
\beta\pi=\frac{2\pi(m+1)-2\pi}{m+1}=\frac{2m\pi}{m+1}.
$$

Divide by $\pi$:

$$
\boxed{\beta=\frac{2m}{m+1}}
$$

Solve for $m$: $\beta(m+1)=2m$, so $\beta=m(2-\beta)$ and

$$
m=\frac{\beta}{2-\beta}.
$$

Each face of a symmetric wedge turns the oncoming flow through half the included angle, $\beta\pi/2$. The 90° wedge has $\beta=\tfrac12$ and $m=\tfrac13$, with faces at $45^\circ$ to the stream.

The speed along a wall follows from the complex velocity. Differentiate $\Phi$:

$$
\frac{\mathrm d\Phi}{\mathrm dz}=-k(m+1)z^m .
$$

On the upper wall, $z=se^{i\pi/(m+1)}$ with $s$ the distance from the apex, so

$$
\frac{\mathrm d\Phi}{\mathrm dz}=-k(m+1)s^me^{im\pi/(m+1)} .
$$

The speed is the modulus, and the exponential has modulus 1:

$$
U_e(s)=\left|\frac{\mathrm d\Phi}{\mathrm dz}\right|=k(m+1)s^m .
$$

In Chapter 3 the distance along the wall is called $x$, and the constant $k(m+1)$ is called $c$:

$$
U_e(x)=cx^m,\qquad c=k(m+1).
$$

This is the slightly different definition of $U_e$ and $m$ used in Chapter 3. Differentiate, then divide by $U_e$:

$$
\frac{\mathrm dU_e}{\mathrm dx}=cmx^{m-1}=\frac{m}{x}\,cx^m=\frac{mU_e}{x}.
$$

So term ⑥ is

$$
U_e\frac{\mathrm dU_e}{\mathrm dx}=\frac{mU_e^2}{x},
$$

and by §1 the pressure gradient along the wall is

$$
\frac{\mathrm dp}{\mathrm dx}=-\rho\frac{mU_e^2}{x}.
$$

For $m>0$ the pressure falls along the wall (favourable); for $m<0$ it rises (adverse).

For $m<0$ the symmetric picture fails, since the fluid would need more than $2\pi$. One half is used instead: the dividing streamline $\theta=0$ becomes a wall, and the second wall at $\theta=\pi/(m+1)>\pi$ is the continuation of the first, turned away from the flow at a convex corner by

$$
\delta_w=\frac{\pi}{m+1}-\pi=-\frac{m\pi}{m+1}=-\frac{\beta\pi}{2}.
$$

A single wall that turns away by $\delta_w$ therefore has $\beta=-2\delta_w/\pi$. Separation, $\beta=-0.19884$, needs a turn of only $0.0994\pi=17.9^\circ$.

| Flow | $m$ | $\beta$ | Geometry |
|---|---:|---:|---|
| flat plate (Blasius) | 0 | 0 | $\delta_w=0$ |
| 54° wedge | 0.17647 | 0.3 | faces at $27^\circ$ |
| 90° wedge | 1/3 | 0.5 | faces at $45^\circ$ |
| stagnation point (Hiemenz) | 1 | 1 | flow meeting a wall head on |
| incipient separation | −0.09043 | −0.19884 | wall turned away by $17.9^\circ$ |

## 3. The Falkner–Skan variables and their derivatives

The three variables generalise those of Blasius ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#2. The Blasius similarity variables|3.2 §2]]), with $(m+1)$ inside the length scale:

$$
\xi=\left[\frac{2\nu x}{(m+1)U_e}\right]^{1/2},\qquad\eta=\frac y\xi,\qquad f(\eta)=\frac{\psi}{U_e\xi}.
$$

§6 shows where the $(m+1)$ comes from. Here it is taken as given.

### Variable 1, the length scale

Substitute $U_e=cx^m$ into $\xi^2$:

$$
\xi^2=\frac{2\nu x}{(m+1)cx^m}=\frac{2\nu}{(m+1)c}\,x^{1-m}.
$$

Differentiate both sides with respect to $x$:

$$
2\xi\frac{\mathrm d\xi}{\mathrm dx}=\frac{2\nu}{(m+1)c}(1-m)x^{-m}.
$$

Write $x^{-m}$ as $x^{1-m}/x$, so that the right-hand side contains $\xi^2$ again:

$$
2\xi\frac{\mathrm d\xi}{\mathrm dx}=(1-m)\,\frac{1}{x}\,\frac{2\nu}{(m+1)c}x^{1-m}=(1-m)\frac{\xi^2}{x}.
$$

Divide by $2\xi$:

$$
\boxed{\frac{\mathrm d\xi}{\mathrm dx}=\frac{\xi}{2x}(1-m)}
$$

The Notes reach the same result with the product rule on $x^{1/2}U_e^{-1/2}$ and $(1/U_e)\,\mathrm dU_e/\mathrm dx=m/x$. Since $\xi\propto x^{(1-m)/2}$, the layer grows like $\sqrt x$ on a flat plate, more slowly on a wedge and not at all at a stagnation point ($m=1$). $\xi$ does not depend on $y$.

### Variable 2, the similarity coordinate

$\eta=y/\xi$ depends on $x$ only through $\xi$. By the chain rule:

$$
\frac{\partial\eta}{\partial x}=\frac{\mathrm d\eta}{\mathrm d\xi}\,\frac{\mathrm d\xi}{\mathrm dx}=-\frac{y}{\xi^2}\,\frac{\mathrm d\xi}{\mathrm dx}.
$$

Substitute $\mathrm d\xi/\mathrm dx$:

$$
\frac{\partial\eta}{\partial x}=-\frac{y}{\xi^2}\,\frac{\xi}{2x}(1-m).
$$

Cancel one $\xi$ and write $y/\xi=\eta$:

$$
\frac{\partial\eta}{\partial x}=-\frac{\eta}{2x}(1-m)=\frac{\eta}{2x}(m-1).
$$

In $y$ the scale $\xi$ is a constant:

$$
\frac{\partial\eta}{\partial y}=\frac1\xi.
$$

### Variable 3, the stream function

$f$ depends on $x$ and $y$ only through $\eta$, so each partial derivative is $f'$ times the matching derivative of $\eta$:

$$
\frac{\partial f}{\partial x}=f'\frac{\partial\eta}{\partial x}=\frac{\eta}{2x}(m-1)f',\qquad\frac{\partial f}{\partial y}=f'\frac{\partial\eta}{\partial y}=\frac1\xi f'.
$$

| No. | Variable | $\partial/\partial x$ | $\partial/\partial y$ |
|---|---|---|---|
| 1 | $\xi=\left[2\nu x/((m+1)U_e)\right]^{1/2}$ | $\dfrac{\xi}{2x}(1-m)$ | 0 |
| 2 | $\eta=y/\xi$ | $\dfrac{\eta}{2x}(m-1)$ | $\dfrac1\xi$ |
| 3 | $f=\psi/(U_e\xi)$ | $\dfrac{\eta}{2x}(m-1)f'$ | $\dfrac1\xi f'$ |

With $m=0$ every entry reduces to the Blasius table of 3.2.

## 4. The derivatives of the stream function

Every term of the reduced equation is built from $\psi=U_e\xi f(\eta)$. $U_e$ and $\xi$ depend on $x$ only, so in $y$ they are constants.

### Terms 1, 4 and 5: derivatives in y

The first $y$-derivative brings out $\partial f/\partial y=f'/\xi$:

$$
\frac{\partial\psi}{\partial y}=U_e\xi\frac{\partial f}{\partial y}=U_e\xi\cdot\frac1\xi f'=U_ef'.
$$

Since $\partial\psi/\partial y=u$, this says $f'=u/U_e$: the slope of $f$ is the velocity profile. Each further $y$-derivative of a function of $\eta$ brings another factor $1/\xi$:

$$
\frac{\partial^2\psi}{\partial y^2}=\frac{\partial}{\partial y}\left(U_ef'\right)=U_ef''\frac{\partial\eta}{\partial y}=\frac{U_e}{\xi}f'' .
$$

$$
\frac{\partial^3\psi}{\partial y^3}=\frac{\partial}{\partial y}\left(\frac{U_e}{\xi}f''\right)=\frac{U_e}{\xi}f'''\frac{\partial\eta}{\partial y}=\frac{U_e}{\xi^2}f''' .
$$

### Term 3: the derivative in x

All three factors of $\psi$ depend on $x$. The product rule gives three terms:

$$
\frac{\partial\psi}{\partial x}=\frac{\mathrm dU_e}{\mathrm dx}\,\xi f+U_e\frac{\mathrm d\xi}{\mathrm dx}f+U_e\xi\frac{\partial f}{\partial x}.
$$

Substitute $\mathrm dU_e/\mathrm dx=mU_e/x$, $\mathrm d\xi/\mathrm dx=\xi(1-m)/(2x)$ and $\partial f/\partial x=\eta(m-1)f'/(2x)$:

$$
\frac{\partial\psi}{\partial x}=\frac{mU_e}{x}\xi f+U_e\frac{\xi}{2x}(1-m)f+U_e\xi\frac{\eta}{2x}(m-1)f'.
$$

Take $U_e\xi/(2x)$ outside; the first term becomes $2mf$:

$$
\frac{\partial\psi}{\partial x}=\frac{U_e\xi}{2x}\left[2mf+(1-m)f+(m-1)\eta f'\right].
$$

Collect the $f$ terms, $2m+1-m=m+1$:

$$
\boxed{\frac{\partial\psi}{\partial x}=\frac{U_e\xi}{2x}\left[(m+1)f+(m-1)\eta f'\right]}
$$

At the wall $\eta=0$ and $f=0$, so $v=-\partial\psi/\partial x=0$. Far from the wall $f\to\eta-\eta^*$ and $f'\to1$, so

$$
v\to-\frac{U_e\xi}{2x}\left[(m+1)(\eta-\eta^*)+(m-1)\eta\right]=-\frac{U_e\xi}{2x}\left[2m\eta-(m+1)\eta^*\right].
$$

For the flat plate this is the familiar outflow $v_\infty=U_e\xi\eta^*/(2x)=0.8604\,U_e/\sqrt{Re_x}$, the displacement effect seen by the outer flow. For $m>0$ the $2m\eta$ term is the inflow of the wedge's own potential flow towards the wall.

### Term 2: the mixed derivative

Differentiate the boxed $\partial\psi/\partial x$ with respect to $y$. The prefactor $U_e\xi/(2x)$ is constant in $y$, and the bracket is a function of $\eta$, so its $y$-derivative is its $\eta$-derivative divided by $\xi$:

$$
\frac{\partial^2\psi}{\partial x\,\partial y}=\frac{U_e\xi}{2x}\cdot\frac1\xi\,\frac{\mathrm d}{\mathrm d\eta}\left[(m+1)f+(m-1)\eta f'\right].
$$

Differentiate the bracket, using the product rule on $\eta f'$:

$$
\frac{\mathrm d}{\mathrm d\eta}\left[(m+1)f+(m-1)\eta f'\right]=(m+1)f'+(m-1)\left(f'+\eta f''\right).
$$

Collect the $f'$ terms, $(m+1)+(m-1)=2m$:

$$
(m+1)f'+(m-1)f'+(m-1)\eta f''=2mf'+(m-1)\eta f''.
$$

Cancel $\xi$:

$$
\boxed{\frac{\partial^2\psi}{\partial x\,\partial y}=\frac{U_e}{2x}\left[2mf'+(m-1)\eta f''\right]}
$$

The same result follows from differentiating $\partial\psi/\partial y=U_ef'$ in $x$ instead, which is a useful check:

$$
\frac{\partial}{\partial x}\left(U_ef'\right)=\frac{\mathrm dU_e}{\mathrm dx}f'+U_ef''\frac{\partial\eta}{\partial x}=\frac{mU_e}{x}f'+U_ef''\frac{\eta}{2x}(m-1)=\frac{U_e}{2x}\left[2mf'+(m-1)\eta f''\right].
$$

### Term 6: the pressure gradient

From §2:

$$
U_e\frac{\mathrm dU_e}{\mathrm dx}=\frac{mU_e^2}{x}.
$$

## 5. Substitution and the Falkner–Skan equation

Substitute the six terms into ①② − ③④ = ν⑤ + ⑥. The first product is

$$
①②=U_ef'\cdot\frac{U_e}{2x}\left[2mf'+(m-1)\eta f''\right]=\frac{U_e^2}{2x}\left[2mf'^2+(m-1)\eta f'f''\right].
$$

In the second product the $\xi$ in term ③ cancels the $1/\xi$ in term ④:

$$
③④=\frac{U_e\xi}{2x}\left[(m+1)f+(m-1)\eta f'\right]\frac{U_e}{\xi}f''=\frac{U_e^2}{2x}\left[(m+1)ff''+(m-1)\eta f'f''\right].
$$

Subtract. The two $(m-1)\eta f'f''$ terms cancel:

$$
①②-③④=\frac{U_e^2}{2x}\left[2mf'^2-(m+1)ff''\right].
$$

This cancellation removes the only place where $\eta$ appears explicitly. Without it the equation would still depend on $\eta$ on its own, not only through $f$ and its derivatives.

For the viscous term, invert the definition of $\xi$: $1/\xi^2=(m+1)U_e/(2\nu x)$. Then

$$
\nu⑤=\nu\frac{U_e}{\xi^2}f'''=\nu U_e\frac{(m+1)U_e}{2\nu x}f'''=\frac{U_e^2}{2x}(m+1)f'''.
$$

Write term ⑥ over the same factor:

$$
⑥=\frac{mU_e^2}{x}=\frac{U_e^2}{2x}\cdot2m.
$$

Assemble the equation:

$$
\frac{U_e^2}{2x}\left[2mf'^2-(m+1)ff''\right]=\frac{U_e^2}{2x}(m+1)f'''+\frac{U_e^2}{2x}\cdot2m.
$$

Multiply by $2x/U_e^2$. Every $x$ disappears:

$$
2mf'^2-(m+1)ff''=(m+1)f'''+2m.
$$

Move everything to the right-hand side:

$$
0=(m+1)f'''+(m+1)ff''+2m-2mf'^2.
$$

Factor the last two terms:

$$
(m+1)f'''+(m+1)ff''+2m\left(1-f'^2\right)=0.
$$

Divide by $m+1$, which needs $m\neq-1$:

$$
f'''+ff''+\frac{2m}{m+1}\left(1-f'^2\right)=0.
$$

The coefficient is $\beta$ from §2, the wedge angle divided by $\pi$:

$$
\boxed{f'''+ff''+\beta\left(1-f'^2\right)=0,\qquad\beta=\frac{2m}{m+1}}
$$

The boundary conditions on $\psi$ become conditions on $f$. At the wall $\psi=0$, and $\psi=U_e\xi f$ with $U_e\xi\neq0$, so $f(0)=0$. No slip, $u=0$, is $U_ef'(0)=0$, so $f'(0)=0$. At the edge $u\to U_e$, so $f'\to1$:

$$
f(0)=0,\qquad f'(0)=0,\qquad f'(\infty)=1 .
$$

Two conditions sit at the wall and one at infinity, which is why the equation is solved by shooting (§9).

### Blasius as the case m = 0

Put $m=0$. The edge velocity is constant, $U_e=c$, so the plate has no pressure gradient. The similarity length becomes the Blasius one, $\xi=\sqrt{2\nu x/U_e}$, with $\mathrm d\xi/\mathrm dx=\xi/(2x)$ and $\partial\eta/\partial x=-\eta/(2x)$. The coefficient vanishes, $\beta=0$, and the equation reduces to

$$
f'''+ff''=0,
$$

the Blasius equation of [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#3. Deriving the Blasius equation|3.2 §3]], with the same three boundary conditions. Every flat-plate result is the $\beta=0$ column of the Falkner–Skan table: $f''(0)=0.46960$, $\eta^*=1.21678$, $\theta^*=0.46960$, $\eta_{99}=3.472$.

## 6. Why the edge velocity must be a power law

§§3–5 assumed $U_e=cx^m$ and the matching $\xi$, and showed that the equation closes. Starting from an arbitrary $U_e(x)$ shows that nothing else works. Take

$$
\psi=U_e(x)\,\xi(x)\,f(\eta),\qquad\eta=\frac{y}{\xi(x)},
$$

with $U_e$ and $\xi$ unknown functions, and primes on $U_e$ and $\xi$ meaning $\mathrm d/\mathrm dx$ only in this section. The $y$-derivatives are unchanged from §4:

$$
\psi_y=U_ef',\qquad\psi_{yy}=\frac{U_e}{\xi}f'',\qquad\psi_{yyy}=\frac{U_e}{\xi^2}f'''.
$$

The derivative of $\eta$ in $x$ is now

$$
\frac{\partial\eta}{\partial x}=-\frac{y}{\xi^2}\xi'=-\eta\frac{\xi'}{\xi}.
$$

The $x$-derivative of $\psi$ is the product rule on $(U_e\xi)$ and $f$:

$$
\psi_x=\left(U_e\xi\right)'f+U_e\xi f'\frac{\partial\eta}{\partial x}=\left(U_e\xi\right)'f-U_e\xi'\eta f'.
$$

The mixed derivative is $\partial(U_ef')/\partial x$:

$$
\psi_{xy}=U_e'f'+U_ef''\frac{\partial\eta}{\partial x}=U_e'f'-U_e\frac{\xi'}{\xi}\eta f''.
$$

Form the left-hand side of the reduced equation:

$$
\psi_y\psi_{xy}-\psi_x\psi_{yy}=U_ef'\left(U_e'f'-U_e\frac{\xi'}{\xi}\eta f''\right)-\left[\left(U_e\xi\right)'f-U_e\xi'\eta f'\right]\frac{U_e}{\xi}f''.
$$

Multiply out:

$$
=U_eU_e'f'^2-U_e^2\frac{\xi'}{\xi}\eta f'f''-\frac{U_e\left(U_e\xi\right)'}{\xi}ff''+U_e^2\frac{\xi'}{\xi}\eta f'f''.
$$

The $\eta f'f''$ terms cancel for any $\xi(x)$, so

$$
U_eU_e'f'^2-\frac{U_e\left(U_e\xi\right)'}{\xi}ff''=\nu\frac{U_e}{\xi^2}f'''+U_eU_e'.
$$

Multiply by $\xi^2/(\nu U_e)$:

$$
\frac{\xi^2U_e'}{\nu}f'^2-\frac{\xi\left(U_e\xi\right)'}{\nu}ff''=f'''+\frac{\xi^2U_e'}{\nu}.
$$

Name the two coefficients

$$
\alpha(x)=\frac{\xi\left(U_e\xi\right)'}{\nu},\qquad\beta(x)=\frac{\xi^2U_e'}{\nu},
$$

and rearrange:

$$
f'''+\alpha\,ff''+\beta\left(1-f'^2\right)=0.
$$

This is an ODE in $\eta$ alone only if $\alpha$ and $\beta$ are constants; otherwise $x$ survives in the coefficients and the profiles at different stations differ in shape. The two conditions fix both $U_e$ and $\xi$. Combine them as $2\alpha-\beta$. Expand $\xi(U_e\xi)'$ with the product rule:

$$
\nu\alpha=\xi\left(U_e'\xi+U_e\xi'\right)=U_e'\xi^2+U_e\xi\xi'.
$$

Then

$$
\nu(2\alpha-\beta)=2U_e'\xi^2+2U_e\xi\xi'-U_e'\xi^2=U_e'\xi^2+2U_e\xi\xi'.
$$

The right-hand side is the derivative of $U_e\xi^2$:

$$
\nu(2\alpha-\beta)=\left(U_e\xi^2\right)'.
$$

The left-hand side is constant, so integrate from the apex, where the layer starts with $U_e\xi^2=0$:

$$
U_e\xi^2=\nu(2\alpha-\beta)\,x.
$$

Substitute this $\xi^2$ into the definition of $\beta$:

$$
\beta=\frac{U_e'}{\nu}\cdot\frac{\nu(2\alpha-\beta)x}{U_e}=(2\alpha-\beta)\frac{x}{U_e}\frac{\mathrm dU_e}{\mathrm dx}.
$$

So the logarithmic slope of $U_e$ is a constant, called $m$:

$$
\frac{x}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{\mathrm d\ln U_e}{\mathrm d\ln x}=\frac{\beta}{2\alpha-\beta}\equiv m.
$$

Integrate:

$$
\ln U_e=m\ln x+\text{constant}\quad\Rightarrow\quad U_e=cx^m .
$$

The power law is forced. The size of $\xi$ is still free: replacing $\xi$ by $k\xi$ multiplies both $\alpha$ and $\beta$ by $k^2$, so one of them can be set to any convenient value. The course sets $\alpha=1$. Then $m=\beta/(2-\beta)$, which inverts to $\beta=2m/(m+1)$ as in §2, and

$$
\xi^2=\frac{\nu(2-\beta)x}{U_e}.
$$

With $2-\beta=2-2m/(m+1)=2/(m+1)$:

$$
\xi^2=\frac{2\nu x}{(m+1)U_e},
$$

the course's variable 1. The other common choice, $\alpha=\tfrac12$, gives the Blasius scaling $\eta_o=y\sqrt{U_e/(\nu x)}$ of 1.4 and SESA2029, with $f_o'''+\tfrac12f_of_o''=0$ ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#2. The Blasius similarity variables|3.2 §2]]).

The derivation divided by $2\alpha-\beta$. If $2\alpha=\beta$, which is $\beta=2$ with $\alpha=1$ (the limit $m\to\infty$), then $U_e\xi^2$ is constant and $U_e'/U_e=\beta\nu/(U_e\xi^2)$ is constant too, so $U_e$ grows exponentially. That is the only other edge velocity with similar profiles. The $\beta=2$ and $\beta=10$ columns of the course's Falkner–Skan table ($m=-1.25$ for $\beta=10$) are solutions of the same ODE but not wedge flows.

## 7. The wall: curvature, shear and the inflection point

The Falkner–Skan equation evaluated at $\eta=0$, where $f=0$ and $f'=0$, gives

$$
f'''(0)+0\cdot f''(0)+\beta\left(1-0\right)=0,
$$

so

$$
\boxed{f'''(0)=-\beta}
$$

In dimensional form, $\partial^2u/\partial y^2=\partial^3\psi/\partial y^3=U_ef'''/\xi^2$. At the wall:

$$
\left.\frac{\partial^2u}{\partial y^2}\right|_0=-\beta\frac{U_e}{\xi^2}.
$$

Substitute $\beta=2m/(m+1)$ and $1/\xi^2=(m+1)U_e/(2\nu x)$:

$$
\left.\frac{\partial^2u}{\partial y^2}\right|_0=-\frac{2m}{m+1}\cdot\frac{(m+1)U_e^2}{2\nu x}=-\frac{mU_e^2}{\nu x}.
$$

Since $mU_e^2/x=U_e\,\mathrm dU_e/\mathrm dx$:

$$
\nu\left.\frac{\partial^2u}{\partial y^2}\right|_0=-U_e\frac{\mathrm dU_e}{\mathrm dx}=\frac1\rho\frac{\mathrm dp}{\mathrm dx}.
$$

This is the boundary-layer equation at the wall, where $u=v=0$ and the pressure gradient is balanced by viscous diffusion alone. It is revision 3.3 Q2, and it is the fourth condition used to build the Pohlhausen quartic ([[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients#The BL equation at the wall|3.3, the BL equation at the wall]]). In the Falkner–Skan profiles it means:

- $\beta>0$ (favourable): the profile curves towards the wall from the start, and $f''$ falls monotonically from its wall value;
- $\beta=0$: $f'''(0)=0$ and the Blasius shear profile is flat at the wall;
- $\beta<0$ (adverse): $f'''(0)>0$, so the shear rises away from the wall, peaks inside the layer and then decays. The peak of $f''$ is where $f'''=0$, an inflection point of $u(y)$.

Every adverse-gradient profile has an inflection point. Computed by shooting, it lies at $\eta_i=1.098$, $1.579$, $1.804$ and $2.343$ for $\beta=-0.1$, $-0.16$, $-0.18$ and $-0.19884$, where $u/U_e=0.402$, $0.475$, $0.491$ and $0.503$. These are the open circles in the figure of §9. An inflection point matters for stability: it makes the profile inviscidly unstable by Rayleigh's criterion, which is one reason an adverse gradient brings transition forward ([[SESA3043 3.4 - Transition to Turbulence#8. The effect of pressure gradients|3.4 §8]]).

> [!check] Wall curvature in numbers
> For the 90° wedge of §10 at $x=0.1$ m ($U_e=20$ m/s, $\nu=1.5\times10^{-5}$ m²/s, $\xi=3.354\times10^{-4}$ m), $-\beta U_e/\xi^2=-0.5\times20/(3.354\times10^{-4})^2=-8.889\times10^7$ s⁻¹m⁻¹, and $-U_e(\mathrm dU_e/\mathrm dx)/\nu=-20\times66.67/1.5\times10^{-5}=-8.889\times10^7$ s⁻¹m⁻¹.

The wall shear is the first derivative instead:

$$
\tau_w=\mu\left.\frac{\partial u}{\partial y}\right|_0=\mu U_ef''(0)\frac{\partial\eta}{\partial y}=\frac{\mu U_ef''(0)}{\xi},
$$

so

$$
C_f=\frac{\tau_w}{\tfrac12\rho U_e^2}=\frac{2\nu f''(0)}{U_e\xi}.
$$

With $\xi=x\sqrt{2/(m+1)}/\sqrt{Re_x}$ and $Re_x=U_ex/\nu$ this is $C_f\sqrt{Re_x}=2f''(0)\sqrt{(m+1)/2}$. Separation, $\tau_w=0$, is $f''(0)=0$, which happens at $\beta_{sep}=-0.19884$.

## 8. Integrating the equation across the layer

The Blasius result $\theta^*=f''(0)$ ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#Integral type B|3.2, integral type B]]) is the $\beta=0$ case of an identity that holds for every $\beta$. Integrate the Falkner–Skan equation from the wall to infinity, term by term:

$$
\int_0^\infty f'''\,\mathrm d\eta+\int_0^\infty ff''\,\mathrm d\eta+\beta\int_0^\infty\left(1-f'^2\right)\mathrm d\eta=0.
$$

The first integral is exact. The shear vanishes at the edge, $f''(\infty)=0$:

$$
\int_0^\infty f'''\,\mathrm d\eta=\big[f''\big]_0^\infty=-f''(0).
$$

For the second, the product rule gives

$$
\frac{\mathrm d}{\mathrm d\eta}\left[f\left(f'-1\right)\right]=f'\left(f'-1\right)+ff'',
$$

so

$$
ff''=\frac{\mathrm d}{\mathrm d\eta}\left[f\left(f'-1\right)\right]+f'\left(1-f'\right).
$$

Integrate:

$$
\int_0^\infty ff''\,\mathrm d\eta=\big[f\left(f'-1\right)\big]_0^\infty+\int_0^\infty f'\left(1-f'\right)\mathrm d\eta.
$$

The bracket is zero at both ends: $f(0)=0$ at the wall, and at the edge $1-f'$ decays faster than $f\sim\eta$ grows, the series argument of 3.2. The remaining integral is integral type B:

$$
\int_0^\infty ff''\,\mathrm d\eta=\theta^* .
$$

For the third, factor the difference of squares and split it:

$$
1-f'^2=\left(1-f'\right)\left(1+f'\right)=\left(1-f'\right)+f'\left(1-f'\right).
$$

So it integrates to the sum of the two integral types:

$$
\int_0^\infty\left(1-f'^2\right)\mathrm d\eta=\eta^*+\theta^* .
$$

Put the three pieces back:

$$
-f''(0)+\theta^*+\beta\left(\eta^*+\theta^*\right)=0 .
$$

Rearrange:

$$
\boxed{f''(0)=(1+\beta)\,\theta^*+\beta\,\eta^*}
$$

At $\beta=0$ this is $f''(0)=\theta^*$. At separation $f''(0)=0$, so $\theta^*/\eta^*=-\beta_{sep}/(1+\beta_{sep})$, which is $1/H$ at separation: $H_{sep}=(1+\beta_{sep})/(-\beta_{sep})=0.80116/0.19884=4.029$.

> [!check] The identity against the Falkner–Skan table
> With the printed values, $(1+\beta)\theta^*+\beta\eta^*$ gives 0.12864 at $\beta=-0.18$ (table $f''(0)=0.12864$), 0.77476 at 0.3 (0.77476), $2(0.29235)+0.64790=1.23260$ at 1 (1.23259), $3(0.23079)+2(0.49743)=1.68723$ at 2 (1.68722) and $11(0.11523)+10(0.24077)=3.67523$ at 10 (3.67523). The table satisfies the identity to its last printed digit.

### The same identity is the momentum integral equation

The identity is the [[SESA3043 3.5 - Momentum Integral Equation|momentum integral equation]] (MIE) applied to a similar layer. The MIE ([[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method|MIE deep dive]]) reads

$$
\frac{\mathrm d\theta}{\mathrm dx}+(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\frac{C_f}{2}.
$$

Insert the similarity forms term by term. Since $\theta=\theta^*\xi$ with $\theta^*$ constant, and $\mathrm d\xi/\mathrm dx=\xi(1-m)/(2x)$:

$$
\frac{\mathrm d\theta}{\mathrm dx}=\theta^*\frac{\xi}{2x}(1-m).
$$

With $H=\eta^*/\theta^*$ and $(1/U_e)\,\mathrm dU_e/\mathrm dx=m/x$:

$$
(2+H)\frac{\theta}{U_e}\frac{\mathrm dU_e}{\mathrm dx}=\left(2+\frac{\eta^*}{\theta^*}\right)\theta^*\xi\,\frac mx=\frac{\xi}{x}\left(2m\theta^*+m\eta^*\right).
$$

From §7:

$$
\frac{C_f}{2}=\frac{\nu f''(0)}{U_e\xi}.
$$

Add the two left-hand terms over $\xi/x$:

$$
\frac{\xi}{x}\left[\frac{1-m}{2}\theta^*+2m\theta^*+m\eta^*\right]=\frac{\nu f''(0)}{U_e\xi}.
$$

Combine the $\theta^*$ terms, $(1-m)/2+2m=(1+3m)/2$:

$$
\frac{\xi}{x}\left[\frac{1+3m}{2}\theta^*+m\eta^*\right]=\frac{\nu f''(0)}{U_e\xi}.
$$

Multiply by $x/\xi$:

$$
\frac{1+3m}{2}\theta^*+m\eta^*=\frac{\nu x}{U_e\xi^2}f''(0).
$$

Use $\xi^2=2\nu x/[(m+1)U_e]$ on the right:

$$
\frac{\nu x}{U_e\xi^2}=\frac{\nu x(m+1)U_e}{2\nu xU_e}=\frac{m+1}{2}.
$$

Multiply by $2/(m+1)$:

$$
f''(0)=\frac{1+3m}{m+1}\theta^*+\frac{2m}{m+1}\eta^*.
$$

Since $(1+3m)/(m+1)=1+2m/(m+1)=1+\beta$, this is the boxed identity. The MIE holds for any attached layer; the Falkner–Skan solutions satisfy it exactly, and an approximate profile (Pohlhausen, Thwaites) is judged by how well it does.

## 9. Solving by shooting

![[aa_deepdive_falkner_skan_profiles.png|900]]

The equation is third order and nonlinear, with two conditions at the wall and one at infinity, so it cannot be marched directly. The guess-and-shooting method turns it into a sequence of initial-value problems:

1. guess $s=f''(0)$;
2. integrate $f'''=-ff''-\beta(1-f'^2)$ from $f(0)=0$, $f'(0)=0$, $f''(0)=s$ out to a large $\eta_{max}$ standing in for infinity;
3. compare $f'(\eta_{max})$ with 1, adjust $s$ and repeat until they agree.

The integration here is an eighth-order Runge–Kutta scheme (DOP853) with tolerance $10^{-12}$, and $s$ is adjusted by bisection on the sign of $f'(\eta_{max})-1$, which is more robust than a secant update. For $\beta>0$ a guess that is too large or too small makes $f'$ run off to $\pm\infty$ within a few units of $\eta$, so $\eta_{max}$ must be kept short (10 for $0\le\beta\le1$, 8 for $\beta=2$, 4 for $\beta=10$; the thicker adverse-gradient layers use 14); bisection only needs the sign of the miss and copes with the blow-up. Once $s$ is known, $\eta^*=\eta_{max}-f(\eta_{max})$ because $f\to\eta-\eta^*$, $\theta^*$ comes from quadrature of $f'(1-f')$, and $\eta_{99}$ is the root of $f'=0.99$.

| $\beta$ | $m$ | $f''(0)$ | $\eta^*$ | $\theta^*$ | $H$ | $\eta_{99}$ | $(1+\beta)\theta^*+\beta\eta^*$ |
|---:|---:|---:|---:|---:|---:|---:|---:|
| −0.19884 | −0.09043 | 0 | 2.35885 | 0.58543 | 4.029 | 4.789 | 0.00000 |
| −0.18 | −0.08257 | 0.12864 | 1.87158 | 0.56771 | 3.297 | 4.282 | 0.12864 |
| 0 | 0 | 0.46960 | 1.21678 | 0.46960 | 2.591 | 3.472 | 0.46960 |
| 0.3 | 0.17647 | 0.77475 | 0.91099 | 0.38574 | 2.362 | 2.965 | 0.77475 |
| 0.5 | 0.33333 | 0.92768 | 0.80455 | 0.35027 | 2.297 | 2.750 | 0.92768 |
| 1 | 1 | 1.23259 | 0.64790 | 0.29234 | 2.216 | 2.379 | 1.23259 |
| 2 | $\infty$ | 1.68722 | 0.49743 | 0.23078 | 2.155 | 1.948 | 1.68722 |
| 10 | −1.25 | 3.67523 | 0.24077 | 0.11523 | 2.090 | 1.022 | 3.67523 |

> [!check] Shooting against the Falkner–Skan table (White & Majdalani)
> Every entry agrees with the printed table to within one unit in the fifth decimal place. The only differences are last-digit roundings: $f''(0)=0.774755$ at $\beta=0.3$ (printed 0.77476), $\eta^*=1.871575$ at $-0.18$ (1.87157), $\theta^*=0.292344$ at 1 (0.29235), $0.230784$ at 2 (0.23079) and $0.585434$ at separation (0.58544). The last column reproduces $f''(0)$ to $10^{-11}$, an independent check on the quadrature. Moving $\eta_{max}$ from 10 to 18 changes $f''(0)$ at $\beta=0.3$ by less than $10^{-15}$.

The separation value is found by shooting in $\beta$ with $s=0$ fixed: $\beta_{sep}=-0.198838$, $m_{sep}=-0.090429$, matching the course's value. Close to it the wall shear falls steeply, roughly as $f''(0)\approx0.85\sqrt{\beta-\beta_{sep}}$ ($f''(0)=0.0251$ at $\beta=-0.198$ and $0.0052$ at $-0.1988$), so a small error in $\beta$ near separation gives a large relative error in $C_f$.

Adverse gradients bring a second difficulty. For $\beta<0$ the miss $f'(\eta_{max})-1$ changes only by about 0.02 across a wide range of guesses, and it has two roots. At $\beta=-0.18$ the second is $f''(0)=-0.09769$, a profile with reversed flow near the wall (minimum $u/U_e=-0.0265$, back to zero at $\eta=1.08$). It satisfies the ODE and all three boundary conditions, but it is not the attached layer of the table, so a shooting code for $\beta<0$ needs a bracket with $f''(0)>0$.

Panel (a) of the figure shows the profiles of the table's columns. Each larger $\beta$ fills the profile out and pulls $\eta_{99}$ in, from 4.79 at separation to 1.02 at $\beta=10$. Panel (b) shows the shear $f''$: its wall value is $f''(0)$ and its wall slope is $-\beta$, so favourable profiles have their largest shear at the wall and the adverse ones peak inside the layer at the inflection point.

In physical variables, with $\xi=x\sqrt{2/(m+1)}/\sqrt{Re_x}$, the table gives the coefficients of $1/\sqrt{Re_x}$:

| $\beta$ | $\delta_{99}\sqrt{Re_x}/x$ | $\delta^*\sqrt{Re_x}/x$ | $\theta\sqrt{Re_x}/x$ | $C_f\sqrt{Re_x}$ |
|---:|---:|---:|---:|---:|
| −0.19884 | 7.101 | 3.498 | 0.868 | 0 |
| −0.18 | 6.322 | 2.763 | 0.838 | 0.174 |
| 0 | 4.910 | 1.721 | 0.664 | 0.664 |
| 0.3 | 3.866 | 1.188 | 0.503 | 1.188 |
| 0.5 | 3.368 | 0.985 | 0.429 | 1.515 |
| 1 | 2.379 | 0.648 | 0.292 | 2.465 |

The $\beta=0$ row is the Blasius set $4.91$, $1.721$, $0.664$, $0.664$, and the $\beta=0.3$ row is revision 3.2 Q4 ([[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions#7.2 Revision 3.2 Q4: the wedge with β = 0.3|3.2 §7.2]]). $Re_x$ is formed with the local $U_e(x)$.

## 10. Worked examples

### Stagnation point of a cylinder

A cylinder of radius $R=0.1$ m sits in a stream $U_\infty=30$ m/s with $\nu=1.46\times10^{-5}$ m²/s. Find $\delta_{99}$ near the front stagnation point (the typical exam problem).

The potential-flow surface speed is $U_e=2U_\infty\sin\theta$, with $\theta$ measured round the cylinder from the stagnation point and $x=R\theta$ along the surface. For small $\theta$, in radians, $\sin\theta\approx\theta=x/R$:

$$
U_e\approx\frac{2U_\infty}{R}x .
$$

So $c=2U_\infty/R=600$ s⁻¹, $m=1$ and

$$
\beta=\frac{2\times1}{1+1}=1,
$$

the Hiemenz stagnation-point flow. Substitute $m=1$ and $U_e=cx$ into $\xi$:

$$
\xi=\sqrt{\frac{2\nu x}{(1+1)cx}}=\sqrt{\frac{\nu}{c}}=\sqrt{\frac{\nu R}{2U_\infty}} .
$$

Numerically:

$$
\xi=\sqrt{\frac{1.46\times10^{-5}\times0.1}{2\times30}}=\sqrt{2.433\times10^{-8}}=1.560\times10^{-4}\ \text{m}.
$$

The $\beta=1$ column of the table first reaches $f'=0.99$ at the grid point $\eta=2.4$ ($f'=0.99055$), so

$$
\delta_{99}=2.4\times1.560\times10^{-4}\ \text{m}=0.374\ \text{mm},
$$

the answer to the course's worked problem.

> [!check] The same problem from the shooting solution
> Shooting puts $f'=0.99$ at $\eta_{99}=2.3794$ (the table's grid point 2.4 is the first tabulated value above 0.99), so $\delta_{99}=0.371$ mm. Also $\delta^*=0.64790\xi=0.101$ mm, $\theta=0.29234\xi=0.0456$ mm and $H=2.216$. At the grid point, the computed $f'(2.4)=0.990549$ matches the table's 0.99055.

Because $\xi=\sqrt{\nu/c}$ contains no $x$, the stagnation-point layer has constant thickness: the $\xi\propto x^{(1-m)/2}$ of §3 with $m=1$. The wall shear $\tau_w=\mu U_ef''(0)/\xi=\mu cxf''(0)/\sqrt{\nu/c}$ grows linearly with $x$, from zero at the stagnation point.

### A 90 degree wedge

A symmetric wedge of included angle $90^\circ$ in air ($\nu=1.5\times10^{-5}$ m²/s, $\rho=1.2$ kg/m³) has $U_e=20$ m/s at $x=0.1$ m from the apex along a face. Find $\delta_{99}$, $\delta^*$, $\theta$, $C_f$ and $\tau_w$ there, and check the MIE.

The included angle is $\beta\pi=\pi/2$, so $\beta=0.5$ and

$$
m=\frac{\beta}{2-\beta}=\frac{0.5}{1.5}=\frac13 .
$$

The constant in $U_e=cx^m$ is $c=20/0.1^{1/3}=43.09$ m$^{2/3}$s⁻¹ (and $k=c/(m+1)=32.32$ in the Chapter 1 potential). The similarity length is

$$
\xi=\sqrt{\frac{2\nu x}{(m+1)U_e}}=\sqrt{\frac{2\times1.5\times10^{-5}\times0.1}{\tfrac43\times20}}=\sqrt{1.125\times10^{-7}}=3.354\times10^{-4}\ \text{m}.
$$

With the $\beta=0.5$ row of the shooting table:

$$
\delta_{99}=2.750\xi=0.922\ \text{mm},\qquad\delta^*=0.80455\xi=0.270\ \text{mm},\qquad\theta=0.35027\xi=0.1175\ \text{mm}.
$$

The local Reynolds number is $Re_x=20\times0.1/1.5\times10^{-5}=1.333\times10^5$, so

$$
C_f=\frac{2\nu f''(0)}{U_e\xi}=\frac{2\times1.5\times10^{-5}\times0.92768}{20\times3.354\times10^{-4}}=4.149\times10^{-3},
$$

which is $1.515/\sqrt{Re_x}$, and $\tau_w=\tfrac12\rho U_e^2C_f=0.5\times1.2\times400\times4.149\times10^{-3}=0.996$ Pa. The pressure gradient driving the layer is $\mathrm dp/\mathrm dx=-\rho mU_e^2/x=-1.2\times\tfrac13\times400/0.1=-1600$ Pa/m.

> [!check] MIE at x = 0.1 m
> $\mathrm d\theta/\mathrm dx=\theta(1-m)/(2x)=0.1175\times10^{-3}/0.3=3.916\times10^{-4}$, and $(2+H)(\theta/U_e)\,\mathrm dU_e/\mathrm dx=(2+2.297)\times0.1175\times10^{-3}\times(1/3)/0.1=1.683\times10^{-3}$. The sum, $2.074\times10^{-3}$, equals $C_f/2=2.074\times10^{-3}$, as §8 requires. A finite-difference derivative of $\theta(x)$ gives the same sum to six figures.

Compared with a flat plate at the same $Re_x$, the favourable gradient makes the layer 31 % thinner ($3.368$ against $4.910$) and raises the skin friction by a factor 2.28 ($1.515$ against $0.664$). The layer grows like $x^{(1-m)/2}=x^{1/3}$ instead of $x^{1/2}$.

## 11. Common mistakes

Most errors come from the scalings rather than from the ODE:

- using the Blasius $\xi=\sqrt{2\nu x/U_e}$ for a wedge, which misses the factor $\sqrt{2/(m+1)}$ in every thickness;
- forming $Re_x$ with $U_\infty$ instead of the local $U_e(x)=cx^m$;
- taking $\theta^*=f''(0)$ for $\beta\neq0$; the general relation is $f''(0)=(1+\beta)\theta^*+\beta\eta^*$;
- confusing $\beta$ with $m$, or taking $\beta\pi$ as the turn of one wall; one face of a symmetric wedge turns the flow by $\beta\pi/2$, and a single wall turned away by $\delta_w$ has $\beta=-2\delta_w/\pi$;
- writing the free-stream condition as $f'(\infty)=0$; it is $f'(\infty)=1$;
- applying the similarity results to a body whose $U_e$ is not a power law (an aerofoil, a bump); there only the integral methods of 3.3 and 3.5 apply, and a local $\beta$ gives a qualitative picture.

## Links

- Parent: [[SESA3043 Advanced Aeronautics Hub]]
- Lecture note: [[SESA3043 3.2 - Blasius and Falkner-Skan Similarity Solutions]] (the same derivation in compressed form, the bump picture and revision 3.2 Q4)
- Next: [[SESA3043 Deep Dive - Momentum Integral Equation and Pohlhausen Method]] · [[SESA3043 3.3 - Pohlhausen Method and Pressure Gradients]] · [[SESA3043 3.5 - Momentum Integral Equation]]
- Where $U_e=cx^m$ comes from: [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#7. Wedge and corner flows|1.3 §7]] · [[Wedge and Corner Flows]] · [[Complex Velocity Potential]]
- The boundary-layer equations: [[SESA3043 1.4 - Two-Dimensional Incompressible Boundary Layers]] · [[Prandtl Boundary-Layer Equations]]
- Concepts: [[Blasius and Falkner-Skan Similarity Solutions]] · [[Shooting Method and the Blasius Solution]] · [[Displacement and Momentum Thickness]] · [[Boundary Layer Separation]] · [[Pohlhausen Method]]
- Stability of the inflected profiles: [[SESA3043 3.4 - Transition to Turbulence]] · [[Linear Stability and Transition Prediction]]
- Formulae: [[SESA3043 Formula Sheet]] · Worked: [[SESA3043 Ch3 Revision Questions - Worked Solutions]]

## Sources

- `CH3-2 Blasius and Falkner-Skan(1).pdf`, slides 75–96 (the generalised layers, the special cases, the Falkner–Skan variables and equation, the solution plot and the White & Majdalani table) and slides 103–106 (the cylinder worked problem).
- `Ch3_Notes_Falkner-Skan.pdf` (3 pp., Blackboard, updated 10 Sep 2026): variables, Table 1, Eqs. 1–8.
- `Ch3_Notes_Blasius.pdf` (6 pp.): the $\beta=0$ case and integral types A and B.
- `23 October 2026 at 14_53_16.txt` (BL2, Fri 23 Oct; Falkner–Skan at ll. 488–676) and `05 November 2026 at 13_59_07.txt` (BL3, Thu 5 Nov; the worked problem at ll. 84–167). BL1 (`22 October 2026 at 13_51_55.txt`, ll. 313–322) for the $U_e\,\mathrm dU_e/\mathrm dx$ form of the pressure term.
- CH1-3 (wedge flows) through [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli|1.3]].
- F. M. White & J. Majdalani, *Viscous Fluid Flow*, 4th ed. (2022), §4.3, for the table.
- Checks: the general reduction of §6 was verified symbolically (sympy), including $\alpha=1$ and $\beta=2m/(m+1)$ for the course variables; every number in §§7–10 was computed in Python (DOP853 shooting at tolerance $10^{-12}$, adaptive quadrature). Figure: `generate_aa_deepdive_figures.py` (`fig_falkner_skan_profiles`).

## Self-study tasks

BL2 left the Falkner–Skan derivatives and the simplification for home study with the Blackboard notes or White (ll. 554–557, 598–602) and pointed to revision 3.2 Q4 (ll. 671–673); BL3 called the table-reading problem a typical exam question (ll. 149–152). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(BL2, ll. 554–557)** Derive the $x$- and $y$-derivatives of $\xi$, $\eta$ and $f$ and fill in the summary table. → [[#3. The Falkner–Skan variables and their derivatives|§3]]
- [ ] **(BL2, ll. 584–602)** Find all six terms of the reduced equation and simplify to $f'''+ff''+\beta(1-f'^2)=0$, naming the cancellation that removes $\eta$. → [[#4. The derivatives of the stream function|§4]] · [[#5. Substitution and the Falkner–Skan equation|§5]]
- [ ] **(BL3, ll. 149–152; slides 103–106)** Find $\delta_{99}$ at the front stagnation point of the cylinder from a blank page, reading $\eta_{99}$ from the table. Answer 0.374 mm. → [[#Stagnation point of a cylinder]]
- [ ] **(BL2, ll. 671–673; revision 3.2 Q4)** $\delta^*(x)$ and $\theta(x)$ along a wedge with $\beta=0.3$. Answer $1.188x/\sqrt{Re_x}$ and $0.503x/\sqrt{Re_x}$. → [[#9. Solving by shooting|§9, physical coefficients]]
- [ ] **(BL2, ll. 497–528)** From $\Phi=-kz^{m+1}$, derive $U_e=k(m+1)s^m$ and $\beta=2m/(m+1)$, and show that one wall turned away by $\delta_w$ has $\beta=-2\delta_w/\pi$. → [[#2. The edge velocity of a wedge|§2]]

### Further practice

- [ ] **(Revision 3.3 Q2)** Show that $f'''(0)=-\beta$ is $\nu\,\partial^2u/\partial y^2|_0=-U_e\,\mathrm dU_e/\mathrm dx$, and explain why every adverse-gradient profile has an inflection point. → [[#7. The wall: curvature, shear and the inflection point|§7]]
- [ ] (suggested, not lecturer-set) Starting from an arbitrary $U_e(x)$ and $\xi(x)$, show that similarity forces $U_e=cx^m$ and recover the course's $\xi$. → [[#6. Why the edge velocity must be a power law|§6]]
- [ ] (suggested, not lecturer-set) Integrate the Falkner–Skan equation across the layer to get $f''(0)=(1+\beta)\theta^*+\beta\eta^*$, check it against two columns of the table, and show it is the MIE. → [[#8. Integrating the equation across the layer|§8]]
- [ ] (suggested, not lecturer-set) Write a shooting code and reproduce the $\beta=0.5$ row: $f''(0)=0.92768$, $\eta^*=0.80455$, $\theta^*=0.35027$, $\eta_{99}=2.750$; then find the 90° wedge numbers. → [[#9. Solving by shooting|§9]] · [[#A 90 degree wedge]]

## Transcript and slide slips

> [!warning] Slips in the slides and notes
> Where: [[#2. The edge velocity of a wedge]] and [[#5. Substitution and the Falkner–Skan equation]].
>
> - `Ch3_Notes_Falkner-Skan.pdf` p. 3: the last two lines, including the boxed Eq. 8, print $f'''+f'f''+\beta(1-f'^2)=0$. The line above and slide 94 have $ff''$, which is correct; with $f'f''$ the equation would not reduce to Blasius.
> - Slides 76–77 mark $\beta\pi$ at the expansion corner, where a single wall turns away by $-\beta\pi/2$; $\beta\pi$ is the included angle of a symmetric wedge.
> - Slide 96 (White & Majdalani): five entries differ from the shooting values in the fifth decimal (§9). They are roundings, not errors.

### Transcript slips (BL2, BL3)

> [!warning] Slips in `23 October 2026 at 14_53_16.txt` and `05 November 2026 at 13_59_07.txt`
> "Falkner–Skan" is heard as *"faulkner scan"*, *"partner scan"*, *"fafner"* and similar, and $\xi$ as *"c"*. These are not listed.
>
> | Where | Said | Correct |
> |---|---|---|
> | BL2, l. 511 | *"beta is the wedge angle and the wedge angle is beta times pi"* | $\beta\pi$ is the included angle; one face turns the flow by $\beta\pi/2$ |
> | BL2, ll. 521–523 | *"if m and beta are equal to one then we have a flat plate"* | flat plate is $m=\beta=0$; $m=\beta=1$ is the stagnation point (l. 524) |
> | BL2, l. 553 | *"the cosine dx is equal to c over 2x times 1 minus m"* | $\mathrm d\xi/\mathrm dx=\xi(1-m)/(2x)$ |
> | BL2, l. 616 | *"f prime is equal to 0 as eta goes to infinity"* | $f'(\infty)=1$ |
> | BL2, l. 646 | *"positive theta"* | positive $\beta$ |
> | BL3, l. 131 | *"we have m from m v no beta"* | $\beta$ follows from $m$ |
> | BL3, ll. 144–145 | *"square root of twice nu x divided by m plus 1 u e over x"* | $\xi=\sqrt{2\nu x/[(m+1)U_e]}$ |
