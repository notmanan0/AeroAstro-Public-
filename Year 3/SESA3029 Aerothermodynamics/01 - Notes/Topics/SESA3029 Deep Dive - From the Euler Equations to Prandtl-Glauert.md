---
title: "SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 4: High-speed aerodynamics"
order: 8.5
tags: [sesa3029, compressible-flow, euler-equations, full-potential, small-perturbation, linearisation, prandtl-glauert, transonic, hypersonic, derivation, deep-dive]
aliases: ["Euler to Prandtl-Glauert", "Full potential equation derivation", "Small-perturbation order of magnitude", "Prandtl-Glauert deep dive", "Linearised potential equation in full"]
date: 2026-11-12
status: lectured
coverage: "Lectures 4.1, 4.3 and 4.4 in full depth: steady Euler equations to the exact full potential equation and its type, the exact perturbation-potential equation, an explicit order-of-magnitude argument for which terms survive in subsonic, transonic, supersonic and hypersonic flow (the slide 7 limits of 4.3), the linearised C_p to second order, and the Prandtl–Glauert transformation with its boundary condition, C_p correction and the wavy-wall exact solution"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]]"]
next_topics: ["[[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
key_concepts: ["[[Euler Equations]]", "[[Linearised Compressible Potential Equation]]", "[[Prandtl-Glauert Transformation]]", "[[Homentropic Flow]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture4-1.pdf", "02 - Sources/Lectures/Lecture4-3.pdf", "02 - Sources/Lectures/Lecture4-4.pdf", "02 - Sources/Lectures/Lecture4-1.txt", "02 - Sources/Lectures/06 November 2026 at 16_57_37.txt", "02 - Sources/Lectures/Lecture 4-4.txt"]
---

# SESA3029 Deep Dive - From the Euler Equations to Prandtl-Glauert

> [!abstract] Summary
> For steady, shock-free flow from a uniform stream, the Euler equations reduce exactly to the full potential equation, $(\Phi_x^2-a^2)\Phi_{xx}+2\Phi_x\Phi_y\Phi_{xy}+(\Phi_y^2-a^2)\Phi_{yy}=0$, with $a^2$ fixed by the energy equation; it is elliptic where the local flow is subsonic and hyperbolic where it is supersonic. Writing $\Phi=U_\infty x+\phi$ and sizing each term for a body of thickness ratio $\tau$ shows that the linear equation $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$ holds when $(\gamma+1)M_\infty^2\tau\ll|1-M_\infty^2|^{3/2}$ subsonically and $(\gamma+1)M_\infty^4\tau\ll(M_\infty^2-1)^{3/2}$ supersonically, which fails near $M_\infty=1$ and again when $M_\infty\tau$ approaches 1. Below $M_\infty=1$ the stretch $y_0=\beta y$ turns the linear equation into Laplace's, and $C_p=C_{p0}/\sqrt{1-M_\infty^2}$ follows for any choice of potential scaling.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the linearised potential equation from the Euler equations, for why it fails near $M_\infty=1$ or at hypersonic speed, or for the Prandtl–Glauert rule and its derivation.
> - **Assumptions:** steady, inviscid, adiabatic, no body forces, perfect gas; uniform upstream and no shocks, so homentropic and irrotational; thin body, $u',v'\ll U_\infty$; for Prandtl–Glauert $M_\infty<1$ and away from 1 (below about 0.8).
> - **Method:** 1. Steady Euler → $u^2u_x+uv(u_y+v_x)+v^2v_y=a^2(u_x+v_y)$ with $\mathrm dp=a^2\mathrm d\rho$. 2. Energy → $a^2=a_\infty^2-\tfrac{\gamma-1}2(u^2+v^2-U_\infty^2)$. 3. $u=U_\infty+u'$, $v=v'$; keep first-order terms only. 4. $u'=\phi_x$, $v'=\phi_y$ → $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$. 5. $\phi_0=\beta\phi$, $y_0=\beta y$ → Laplace; $C_p=-2u'/U_\infty=C_{p0}/\beta$.
> - **Common mistakes:** dropping $(\gamma-1)u'U_\infty$ from $a^2$ before the $C_p$ step, where it is first order; saying the linear equation fails at high $M_\infty$ because the $\phi_{yy}$ term becomes negligible (it never does; see §6).
> - **Practise:** [[#9. Numerical checks|§9 checks]] · [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Worked example: Cp0,min = −0.4|W07b, M_crit example]]

Compressible aerofoil theory starts from the same Euler equations that CFD codes solve ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]]). Four nonlinear, coupled equations have no general analytical solution, and two steps reduce them. The first is exact: for flow that comes from a uniform stream without passing through a shock, the entropy and stagnation enthalpy are uniform, the vorticity is zero, and the four equations collapse into one second-order equation for a velocity potential. The second is an approximation: a thin aerofoil changes the velocity by only a little, so the equation can be expanded about the free stream and all but its leading terms dropped.

Which terms may be dropped depends on how large each term is for a body of thickness ratio $\tau$, and that in turn depends on the free-stream Mach number, because compressibility changes how far the disturbance spreads. The sizing gives the limits of the linear theory (not near $M_\infty=1$, not hypersonic), the form of the transonic correction, and the Mach number at which each linear theory is most accurate.

## 1. Assumptions and the starting equations

The steady 2D Euler equations in conservation form are the time-independent part of the unsteady system:

$$
\frac{\partial(\rho u)}{\partial x}+\frac{\partial(\rho v)}{\partial y}=0,
$$

$$
\frac{\partial(\rho u^2+p)}{\partial x}+\frac{\partial(\rho uv)}{\partial y}=0,\qquad
\frac{\partial(\rho uv)}{\partial x}+\frac{\partial(\rho v^2+p)}{\partial y}=0,
$$

$$
\frac{\partial[(\rho e_t+p)u]}{\partial x}+\frac{\partial[(\rho e_t+p)v]}{\partial y}=0 .
$$

They come from a control volume with no viscous stress, no heat conduction and no body force ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#1. The control volume and the balance statement|W07a §§1–5]]). The further assumptions, each used at the step named, are:

- **steady**: $\partial/\partial t=0$ throughout;
- **perfect gas**: $p=\rho RT$ and $h=c_pT=a^2/(\gamma-1)$ with constant $\gamma$ (§3);
- **uniform upstream and no shocks**: every streamline starts in the same uniform free stream and the flow is smooth, so the entropy is the same everywhere (homentropic, $p=C\rho^\gamma$ with one constant $C$; §2) and so is the stagnation enthalpy (§3);
- **irrotational**: with uniform entropy and stagnation enthalpy, Crocco's theorem $T\nabla s=\nabla h_0-\vec V\times\vec\omega$ leaves $\vec V\times\vec\omega=\vec0$, and in planar flow $\vec\omega$ is normal to $\vec V$, so $\vec\omega=\vec0$ (§4; [[Homentropic Flow]]);
- **thin body**: the surface slope is of order $\tau\ll1$, so the disturbances $u'$, $v'$ are small compared with $U_\infty$ (from §5).

The first four make the full potential equation of §4 exact for shock-free flow. Only the last is an approximation.

## 2. One equation for the velocity field

The component-by-component route is in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#1. Steady Euler equations in non-conservative form|W07b §§1–2]]. In vector form the same result takes a few lines, and each line has one physical content.

Steady mass conservation, $\nabla\cdot(\rho\vec V)=0$, expanded by the product rule:

$$
\vec V\cdot\nabla\rho+\rho\,\nabla\cdot\vec V=0 .\qquad(1)
$$

The momentum equations, with continuity subtracted as in W07b §1, are Euler's equation in non-conservative form:

$$
\rho\left(\vec V\cdot\nabla\right)\vec V=-\nabla p .\qquad(2)
$$

Take the scalar product of (2) with $\vec V$. This keeps only the momentum balance along the streamline:

$$
\rho\,\vec V\cdot\left[\left(\vec V\cdot\nabla\right)\vec V\right]=-\vec V\cdot\nabla p .
$$

The flow is homentropic, so $p=C\rho^\gamma$ everywhere and $\mathrm dp=\gamma C\rho^{\gamma-1}\mathrm d\rho=(\gamma p/\rho)\,\mathrm d\rho=a^2\,\mathrm d\rho$. The gradient obeys the same rule:

$$
\nabla p=a^2\nabla\rho
\quad\Rightarrow\quad
-\vec V\cdot\nabla p=-a^2\,\vec V\cdot\nabla\rho .
$$

Use (1) to replace $\vec V\cdot\nabla\rho$ by $-\rho\nabla\cdot\vec V$:

$$
-\vec V\cdot\nabla p=a^2\rho\,\nabla\cdot\vec V .
$$

Equate the two expressions for the right-hand side and divide by $\rho$:

$$
\vec V\cdot\left[\left(\vec V\cdot\nabla\right)\vec V\right]=a^2\,\nabla\cdot\vec V .
$$

In components, $(\vec V\cdot\nabla)\vec V=(uu_x+vu_y,\ uv_x+vv_y)$ and $\nabla\cdot\vec V=u_x+v_y$:

$$
u\left(uu_x+vu_y\right)+v\left(uv_x+vv_y\right)=a^2\left(u_x+v_y\right).
$$

Collect the terms:

$$
\boxed{\left(u^2-a^2\right)u_x+uv\left(u_y+v_x\right)+\left(v^2-a^2\right)v_y=0}
$$

The density has gone; the equation holds for any steady, homentropic, inviscid 2D flow. It has three unknowns, $u$, $v$ and $a$, and the next two sections supply the other two relations.

## 3. The speed of sound from the energy equation

In steady flow the energy equation of 4.1 says that $h_t=h+\tfrac12V^2$ is carried unchanged along each streamline ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#4. Energy conservation|W07a §4]]). Every streamline starts in the free stream, so $h_t$ is the same everywhere:

$$
h+\tfrac12\left(u^2+v^2\right)=h_\infty+\tfrac12U_\infty^2 .
$$

For a perfect gas $h=a^2/(\gamma-1)$. Substitute and multiply by $\gamma-1$:

$$
a^2+\frac{\gamma-1}{2}\left(u^2+v^2\right)=a_\infty^2+\frac{\gamma-1}{2}U_\infty^2 .
$$

Solve for $a^2$:

$$
\boxed{a^2=a_\infty^2-\frac{\gamma-1}{2}\left(u^2+v^2-U_\infty^2\right)}
$$

This is exact. Where the flow speeds up, the gas cools and the speed of sound falls, which is why a flow can reach $M=1$ on an aerofoil while $M_\infty<1$.

## 4. The full potential equation

The flow is irrotational (§1), $\omega=v_x-u_y=0$, so a velocity potential $\Phi$ exists with

$$
u=\Phi_x,\qquad v=\Phi_y .
$$

Then $u_x=\Phi_{xx}$, $v_y=\Phi_{yy}$, and irrotationality makes the two cross derivatives equal, $u_y=v_x=\Phi_{xy}$. Substitute into the boxed equation of §2:

$$
\left(\Phi_x^2-a^2\right)\Phi_{xx}+\Phi_x\Phi_y\left(\Phi_{xy}+\Phi_{xy}\right)+\left(\Phi_y^2-a^2\right)\Phi_{yy}=0 .
$$

Combine the middle terms:

$$
\boxed{\left(\Phi_x^2-a^2\right)\Phi_{xx}+2\Phi_x\Phi_y\Phi_{xy}+\left(\Phi_y^2-a^2\right)\Phi_{yy}=0},\qquad a^2=a_\infty^2-\frac{\gamma-1}{2}\left(\Phi_x^2+\Phi_y^2-U_\infty^2\right).
$$

This is the **full potential equation**: one equation in one unknown, exact for steady, shock-free flow from a uniform stream, and nonlinear because the coefficients contain $\Phi_x$ and $\Phi_y$. Once $\Phi$ is known, the velocity comes from its gradient, $a$ from the energy equation, $M=V/a$, and $p$, $\rho$ and $T$ from the isentropic relations. It still describes the transonic flows of 4.2 up to the point where a shock appears, at which the homentropic assumption fails.

### Type of the full potential equation

A second-order equation $A\Phi_{xx}+2B\Phi_{xy}+C\Phi_{yy}=0$ is elliptic where $B^2-AC<0$ and hyperbolic where $B^2-AC>0$; in the hyperbolic case it has two real characteristic directions. Here

$$
A=\Phi_x^2-a^2,\qquad B=\Phi_x\Phi_y,\qquad C=\Phi_y^2-a^2 .
$$

Form the discriminant:

$$
B^2-AC=\Phi_x^2\Phi_y^2-\left(\Phi_x^2-a^2\right)\left(\Phi_y^2-a^2\right).
$$

Expand the product; the $\Phi_x^2\Phi_y^2$ terms cancel:

$$
B^2-AC=a^2\left(\Phi_x^2+\Phi_y^2\right)-a^4=a^2\left(V^2-a^2\right).
$$

Divide by $a^4$:

$$
\frac{B^2-AC}{a^4}=M^2-1 .
$$

The equation is elliptic where the local flow is subsonic and hyperbolic where it is supersonic, point by point. A transonic aerofoil flow is of mixed type, elliptic outside the sonic line of 4.2 and hyperbolic inside it. In axes aligned with the local velocity ($\Phi_y=0$, $\Phi_x=V$) the characteristic slopes $\mathrm dy/\mathrm dx=(B\pm\sqrt{B^2-AC})/A$ are $\pm a^2\sqrt{M^2-1}/(V^2-a^2)=\pm1/\sqrt{M^2-1}=\pm\tan\mu$: the Mach lines, the characteristics of the [[SESA3029 Deep Dive - Riemann Invariants, Full Derivation|method of characteristics]].

## 5. The exact perturbation-potential equation

Split the potential into the free stream and a perturbation:

$$
\Phi=U_\infty x+\phi,\qquad u=U_\infty+u',\quad v=v',\qquad u'=\phi_x,\quad v'=\phi_y .
$$

$U_\infty$ is constant, so $\Phi_{xx}=\phi_{xx}$, $\Phi_{xy}=\phi_{xy}$ and $\Phi_{yy}=\phi_{yy}$. The speed of sound from §3, with $u^2+v^2-U_\infty^2=2U_\infty u'+u'^2+v'^2$:

$$
a^2=a_\infty^2-\frac{\gamma-1}{2}\left(2U_\infty u'+u'^2+v'^2\right).
$$

Work out the three coefficients of the full potential equation. The first:

$$
a^2-u^2=a_\infty^2-\frac{\gamma-1}{2}\left(2U_\infty u'+u'^2+v'^2\right)-\left(U_\infty^2+2U_\infty u'+u'^2\right).
$$

Collect like terms ($2U_\infty u'$ appears with coefficients $-(\gamma-1)$ and $-2$, $u'^2$ with $-\tfrac{\gamma-1}2$ and $-1$):

$$
a^2-u^2=a_\infty^2-U_\infty^2-(\gamma+1)U_\infty u'-\frac{\gamma+1}{2}u'^2-\frac{\gamma-1}{2}v'^2 .
$$

The third, in the same way:

$$
a^2-v^2=a_\infty^2-(\gamma-1)U_\infty u'-\frac{\gamma-1}{2}u'^2-\frac{\gamma+1}{2}v'^2 .
$$

The middle one is $2uv=2(U_\infty+u')v'$. Write the full potential equation with the signs changed, $(a^2-u^2)\phi_{xx}-2uv\,\phi_{xy}+(a^2-v^2)\phi_{yy}=0$, insert the three coefficients, and divide every term by $a_\infty^2=U_\infty^2/M_\infty^2$. Keep the two terms that contain no perturbation in their coefficients on the left and move the rest to the right:

$$
\boxed{\begin{aligned}
\left(1-M_\infty^2\right)\phi_{xx}+\phi_{yy}
&=M_\infty^2\left[(\gamma+1)\frac{u'}{U_\infty}+\frac{\gamma+1}{2}\frac{u'^2}{U_\infty^2}+\frac{\gamma-1}{2}\frac{v'^2}{U_\infty^2}\right]\phi_{xx}\\
&\quad+M_\infty^2\left[(\gamma-1)\frac{u'}{U_\infty}+\frac{\gamma+1}{2}\frac{v'^2}{U_\infty^2}+\frac{\gamma-1}{2}\frac{u'^2}{U_\infty^2}\right]\phi_{yy}\\
&\quad+2M_\infty^2\frac{v'}{U_\infty}\left(1+\frac{u'}{U_\infty}\right)\phi_{xy}
\end{aligned}}
$$

(checked symbolically by expanding the full potential equation). Nothing has been dropped yet; this is the full potential equation rewritten. The left-hand side is linear in $\phi$. Every term on the right is a product of a perturbation velocity and a second derivative of $\phi$, so it is at least quadratic in the disturbance.

## 6. Order of magnitude: which terms survive

### Scales for a thin body

Let the body have chord $c$ and thickness ratio $\tau$, so its surface slope is of order $\tau$. Flow tangency at the surface gives $v'/(U_\infty+u')$ equal to the slope, so

$$
\frac{v'}{U_\infty}\sim\tau .
$$

The streamwise length scale is $c$. The lateral scale is the distance over which the disturbance changes, and the linear equation itself sets it: with $\phi_{yy}=-(1-M_\infty^2)\phi_{xx}$, a change over $c$ in $x$ is balanced by a change over $c/|\beta|$ in $y$, where $|\beta|=\sqrt{|1-M_\infty^2|}$ (the $\beta$ of Prandtl–Glauert below $M_\infty=1$, the $\lambda$ of Ackeret above). In subsonic flow this is the decay length $1/(\beta k)$ of the wavy wall in §8; in supersonic flow it is the height a Mach line climbs over one chord, $c\tan\mu=c/\lambda$.

With these scales, $\phi_y=v'\sim U_\infty\tau$ and a $y$-scale of $c/|\beta|$ give

$$
\phi\sim\frac{U_\infty\tau c}{|\beta|},\qquad
\frac{u'}{U_\infty}=\frac{\phi_x}{U_\infty}\sim\frac{\tau}{|\beta|},
$$

$$
\phi_{xx}\sim\frac{U_\infty\tau}{|\beta|c},\qquad
\phi_{yy}\sim\frac{|\beta|U_\infty\tau}{c},\qquad
\phi_{xy}\sim\frac{U_\infty\tau}{c}.
$$

The two kept terms are of the same size, $|1-M_\infty^2|\phi_{xx}\sim\phi_{yy}\sim|\beta|U_\infty\tau/c$, as they must be. Each term on the right of §5 can now be divided by $\phi_{yy}$:

| Term on the right of §5 | Size relative to the kept terms |
|---|---|
| (a) $(\gamma+1)M_\infty^2\dfrac{u'}{U_\infty}\phi_{xx}$ | $\dfrac{(\gamma+1)M_\infty^2\tau}{\lvert\beta\rvert^3}$ |
| (b) $(\gamma-1)M_\infty^2\dfrac{u'}{U_\infty}\phi_{yy}$ | $\dfrac{(\gamma-1)M_\infty^2\tau}{\lvert\beta\rvert}$ |
| (c) $2M_\infty^2\dfrac{v'}{U_\infty}\phi_{xy}$ | $\dfrac{2M_\infty^2\tau}{\lvert\beta\rvert}$ |
| quadratic terms, e.g. $\tfrac{\gamma+1}{2}M_\infty^2\dfrac{v'^2}{U_\infty^2}\phi_{yy}$ | $\tfrac{\gamma+1}{2}M_\infty^2\tau^2$, and squares of (a)–(c) in general |

The quadratic terms are of the order of the squares of (a)–(c), so they are negligible whenever (a)–(c) are. Everything therefore turns on the three first-order terms.

### Subsonic: the Prandtl–Glauert range

For $M_\infty$ well below 1, $|\beta|$ is of order 1 and all three ratios are of order $M_\infty^2\tau$, small for a thin body. Dropping the right-hand side leaves the linear equation:

$$
\left(1-M_\infty^2\right)\phi_{xx}+\phi_{yy}=0 .
$$

As $M_\infty\to1$, $|\beta|\to0$ and term (a) grows fastest, as $|\beta|^{-3}$. The linear equation holds only while

$$
\boxed{(\gamma+1)M_\infty^2\tau\ll\left(1-M_\infty^2\right)^{3/2}}
$$

For the 12 % section of the 4.2 CFD, the ratio is $0.20$ at $M_\infty=0.6$, $0.39$ at $0.7$ and $0.85$ at $0.8$, and it reaches 1 at $M_\infty=0.817$. The CFD pictures agree: the $M_\infty=0.6$ solution is smooth and close to incompressible, while at $0.8$ a supersonic region and a shock have appeared ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils#7. Flow regimes and the critical Mach number|W07a §7]]). A 5 % section keeps the ratio below 1 up to $M_\infty=0.890$. This is why the 4.4 title puts the Prandtl–Glauert limit near 0.8: the limit depends on thickness, and 0.8 is right for typical sections.

### Transonic: the term that must be kept

Near $M_\infty=1$, term (a) is comparable with the kept terms while (b) and (c) are still of order $\tau/|\beta|$, which is smaller. Keeping (a) and moving it to the left gives

$$
\left[1-M_\infty^2-(\gamma+1)M_\infty^2\frac{\phi_x}{U_\infty}\right]\phi_{xx}+\phi_{yy}=0,
$$

the transonic small-disturbance equation (the textbook name; not lectured), which carries the next order of terms. Its coefficient of $\phi_{xx}$ is the local version of $1-M^2$. From §3 to first order, the local Mach number is

$$
M^2=\frac{(U_\infty+u')^2+v'^2}{a^2}\approx M_\infty^2\left[1+\left(2+(\gamma-1)M_\infty^2\right)\frac{u'}{U_\infty}\right],
$$

and at $M_\infty=1$ the bracket factor is $2+(\gamma-1)=\gamma+1$ (expansion checked symbolically). So near $M_\infty=1$,

$$
1-M^2\approx1-M_\infty^2-(\gamma+1)M_\infty^2\frac{u'}{U_\infty}:
$$

the equation is elliptic where the local flow is subsonic and hyperbolic where it is supersonic, the same mixed type as the full potential equation of §4, and nonlinear. This is why the linear equation is not valid near $M_\infty=1$. Balancing (a) against the kept terms, $|\beta|^3\sim(\gamma+1)M_\infty^2\tau$, gives the transonic scaling: $|1-M_\infty^2|\sim[(\gamma+1)\tau]^{2/3}$ and $u'/U_\infty\sim\tau/|\beta|\sim\tau^{2/3}$, much larger than the $\tau$ of linear theory.

### Supersonic: the three terms combine

Above $M_\infty=1$ the three first-order terms have a fixed relation to one another. Above a thin aerofoil the linear solution is $\phi=f(x-\lambda y)$ ([[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils#2. General solution by characteristic coordinates|Ackeret deep dive §2]]), with $\lambda=\sqrt{M_\infty^2-1}$, so

$$
v'=-\lambda u',\qquad\phi_{xy}=-\lambda\phi_{xx},\qquad\phi_{yy}=\lambda^2\phi_{xx} .
$$

Rewrite (b) and (c) in terms of $u'$ and $\phi_{xx}$:

$$
(\gamma-1)M_\infty^2\frac{u'}{U_\infty}\phi_{yy}=(\gamma-1)\lambda^2M_\infty^2\frac{u'}{U_\infty}\phi_{xx},
$$

$$
2M_\infty^2\frac{v'}{U_\infty}\phi_{xy}=2M_\infty^2\frac{(-\lambda u')}{U_\infty}\left(-\lambda\phi_{xx}\right)=2\lambda^2M_\infty^2\frac{u'}{U_\infty}\phi_{xx} .
$$

Add (a), (b) and (c):

$$
M_\infty^2\frac{u'}{U_\infty}\phi_{xx}\left[(\gamma+1)+(\gamma-1)\lambda^2+2\lambda^2\right]=(\gamma+1)\left(1+\lambda^2\right)M_\infty^2\frac{u'}{U_\infty}\phi_{xx} .
$$

With $1+\lambda^2=M_\infty^2$, the sum is $(\gamma+1)M_\infty^4(u'/U_\infty)\phi_{xx}$. Its size relative to the kept term $\lambda^2\phi_{xx}$, with $u'/U_\infty\sim\tau/\lambda$, is

$$
\boxed{\frac{(\gamma+1)M_\infty^4\tau}{\left(M_\infty^2-1\right)^{3/2}}\ll1}
$$

One parameter covers both ends of the supersonic range. As $M_\infty\to1^+$ it becomes $(\gamma+1)\tau/\lambda^3$, the transonic criterion again. As $M_\infty\to\infty$, $(M_\infty^2-1)^{3/2}\to M_\infty^3$ and it becomes $(\gamma+1)M_\infty\tau$, so the linear theory fails once $M_\infty\tau$ is of order 1, however thin the body. That is the hypersonic limit of the linear theory: since $\mu\approx1/M_\infty$ at high Mach number, $M_\infty\tau\approx\tau/\mu$, and the theory fails when the Mach angle has shrunk to the size of the body slope, so that the waves lie close along the body instead of standing well clear of it.

The parameter is smallest, and the linear theory most accurate, where $(M_\infty^2-1)^{3/2}/M_\infty^4$ is largest. Write $m=M_\infty^2$ and differentiate $(m-1)^{3/2}m^{-2}$:

$$
\frac{\mathrm d}{\mathrm dm}\left[\frac{(m-1)^{3/2}}{m^2}\right]=\frac{\tfrac32(m-1)^{1/2}m^2-2m(m-1)^{3/2}}{m^4}=0 .
$$

Divide by $m(m-1)^{1/2}$:

$$
\tfrac32m-2(m-1)=0\quad\Rightarrow\quad m=4\quad\Rightarrow\quad M_\infty=2 .
$$

![[at_small_disturbance_regimes.png|900]]

| Regime | Largest dropped term | Linear theory holds when | Equation |
|---|---|---|---|
| subsonic, $M_\infty\lesssim0.8$ | (a), $(\gamma+1)M_\infty^2\tau/\beta^3$ | $(\gamma+1)M_\infty^2\tau\ll(1-M_\infty^2)^{3/2}$ | linear, elliptic (Prandtl–Glauert) |
| transonic, $M_\infty\approx1$ | (a) is of order 1 | never | keep (a): nonlinear, mixed type |
| supersonic, $M_\infty\gtrsim1.2$ | (a)+(b)+(c) combined | $(\gamma+1)M_\infty^4\tau\ll(M_\infty^2-1)^{3/2}$ | linear, hyperbolic (Ackeret) |
| hypersonic, $M_\infty\tau\sim1$ | (b) and (c), of order $M_\infty\tau$ | never | nonlinear |

The boundaries are orders of magnitude, not sharp lines; the figure marks where each ratio reaches 1 and 0.3.

## 7. The linearised equation and pressure coefficient

Dropping the whole right-hand side of §5 gives the linear equation and, from the kept terms, the linearised Euler equation:

$$
\boxed{\left(1-M_\infty^2\right)\phi_{xx}+\phi_{yy}=0}
\qquad\Longleftrightarrow\qquad
\left(1-M_\infty^2\right)\frac{\partial u'}{\partial x}+\frac{\partial v'}{\partial y}=0 .
$$

The pressure coefficient needs the same care about order. Start from the exact isentropic link between pressure and speed of sound ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#5. The linearised pressure coefficient|W07b §5]]):

$$
C_p=\frac{2}{\gamma M_\infty^2}\left(\frac{p}{p_\infty}-1\right),\qquad
\frac{p}{p_\infty}=\left(\frac{a^2}{a_\infty^2}\right)^{\gamma/(\gamma-1)} .
$$

Divide the exact $a^2$ of §5 by $a_\infty^2$:

$$
\frac{a^2}{a_\infty^2}=1-\varepsilon,\qquad
\varepsilon=\frac{\gamma-1}{2}M_\infty^2\left(\frac{2u'}{U_\infty}+\frac{u'^2}{U_\infty^2}+\frac{v'^2}{U_\infty^2}\right).
$$

Expand $(1-\varepsilon)^n$, $n=\gamma/(\gamma-1)$, to second order:

$$
\frac{p}{p_\infty}\approx1-n\varepsilon+\frac{n(n-1)}{2}\varepsilon^2 .
$$

The first-order part of $n\varepsilon$ is $\gamma M_\infty^2u'/U_\infty$, and its second-order part is $\tfrac\gamma2M_\infty^2(u'^2+v'^2)/U_\infty^2$. For the last term only the leading part of $\varepsilon$ is needed, $\varepsilon^2\approx(\gamma-1)^2M_\infty^4u'^2/U_\infty^2$, and $n(n-1)/2=\gamma/[2(\gamma-1)^2]$:

$$
\frac{n(n-1)}{2}\varepsilon^2\approx\frac{\gamma}{2}M_\infty^4\frac{u'^2}{U_\infty^2} .
$$

Collect:

$$
\frac{p}{p_\infty}-1\approx-\gamma M_\infty^2\frac{u'}{U_\infty}-\frac{\gamma}{2}M_\infty^2\frac{u'^2+v'^2}{U_\infty^2}+\frac{\gamma}{2}M_\infty^4\frac{u'^2}{U_\infty^2} .
$$

Multiply by $2/(\gamma M_\infty^2)$:

$$
\boxed{C_p\approx-\frac{2u'}{U_\infty}-\left(1-M_\infty^2\right)\frac{u'^2}{U_\infty^2}-\frac{v'^2}{U_\infty^2}}
$$

(checked symbolically). The first term is the linearised $C_p=-2u'/U_\infty$. The second-order terms are smaller by a factor of order $u'/U_\infty\sim\tau/|\beta|$, the same factor as the dropped terms of §6, so the first-order $C_p$ is consistent with the first-order potential equation. The $(\gamma-1)u'U_\infty$ term of $a^2$ is first order, and it is what produces the $\gamma M_\infty^2$ in $p/p_\infty$; dropping it before this step would lose the result ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#3. Linearising about the free stream|W07b §3]]).

The surface boundary condition is linearised in the same way. On a surface $y=f(x)$ tangency gives $v'(x,f)=(U_\infty+u')f'(x)$. Expanding $v'(x,f)\approx v'(x,0)+f\,\partial v'/\partial y$ and dropping the products of small quantities transfers the condition to the axis:

$$
\phi_y(x,0)=v'(x,0)=U_\infty f'(x) .
$$

## 8. The Prandtl–Glauert transformation

For $M_\infty<1$, $\beta=\sqrt{1-M_\infty^2}$ is real and the linear equation is $\beta^2\phi_{xx}+\phi_{yy}=0$. The course uses $\phi_0=\beta\phi$, $x_0=x$, $y_0=\beta y$. The scale factor on $\phi$ can be left general, which shows which parts of the transformation matter. Let

$$
\phi_0=A\,\phi,\qquad x_0=x,\qquad y_0=\beta y ,
$$

with $A$ any positive constant. Since $x_0=x$, $\partial/\partial x=\partial/\partial x_0$, and

$$
\phi_{xx}=\frac1A\frac{\partial^2\phi_0}{\partial x_0^2} .
$$

Since $y_0=\beta y$, the chain rule gives $\partial/\partial y=\beta\,\partial/\partial y_0$. Apply it twice:

$$
\phi_{yy}=\beta^2\frac{\partial^2}{\partial y_0^2}\left(\frac{\phi_0}{A}\right)=\frac{\beta^2}{A}\frac{\partial^2\phi_0}{\partial y_0^2} .
$$

Substitute both into $\beta^2\phi_{xx}+\phi_{yy}=0$:

$$
\frac{\beta^2}{A}\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\beta^2}{A}\frac{\partial^2\phi_0}{\partial y_0^2}=0 .
$$

$\beta^2/A\ne0$ for $M_\infty<1$, so

$$
\frac{\partial^2\phi_0}{\partial x_0^2}+\frac{\partial^2\phi_0}{\partial y_0^2}=0 .
$$

The stretch $y_0=\beta y$ alone makes the equation Laplace's; the factor $A$ plays no part (checked symbolically for general $A$). It enters through the boundary condition. On the axis, $\phi_y=U_\infty f'(x)$. In the new variables

$$
\phi_y=\frac{\partial(\phi_0/A)}{\partial y}=\frac{\beta}{A}\frac{\partial\phi_0}{\partial y_0},
$$

so the incompressible problem has

$$
\frac{\partial\phi_0}{\partial y_0}(x_0,0)=U_\infty\,\frac{A}{\beta}f'(x_0) :
$$

an incompressible body with slopes $A/\beta$ times the real ones. The pressure coefficient is

$$
C_p=-\frac{2}{U_\infty}\phi_x=-\frac{2}{AU_\infty}\frac{\partial\phi_0}{\partial x_0}=\frac{1}{A}\,C_{p0}\!\left[\tfrac{A}{\beta}f\right],
$$

where $C_{p0}[g]$ is the incompressible $C_p$ of a body with surface $g$. Incompressible thin-aerofoil theory is linear in the slope, $C_{p0}[kf]=k\,C_{p0}[f]$, so

$$
C_p=\frac1A\cdot\frac{A}{\beta}\,C_{p0}[f]
\quad\Rightarrow\quad
\boxed{C_p=\frac{C_{p0}}{\sqrt{1-M_\infty^2}}}
$$

for every $A$. The course's choice $A=\beta$ makes the incompressible body the same body ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#6. The Prandtl–Glauert transformation|W07b §6]]), so the rule compares one aerofoil at two Mach numbers. The choice $A=1$ leaves the potential unscaled and compares the real aerofoil with an incompressible one $1/\beta$ times thicker, the form some textbooks use. Both give the same $C_p$ because the theory is linear. $C_l$ and $C_m$ follow by integrating along the chord, where $x_0=x$ lets $1/\beta$ come outside the integral ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Lift and moment coefficients|W07b §7]]).

### An exact solution: the wavy wall

A wall $y=h\cos kx$ with $hk\ll1$ gives a closed-form solution of the linear equation that shows both effects of compressibility. Try

$$
\phi=\frac{U_\infty h}{\beta}e^{-\beta ky}\sin kx .
$$

Its second derivatives are

$$
\phi_{xx}=-k^2\phi,\qquad\phi_{yy}=\beta^2k^2\phi ,
$$

so $\beta^2\phi_{xx}+\phi_{yy}=-\beta^2k^2\phi+\beta^2k^2\phi=0$. The boundary condition needs $\phi_y(x,0)=U_\infty\,\mathrm d(h\cos kx)/\mathrm dx=-U_\infty hk\sin kx$:

$$
\phi_y(x,0)=\frac{U_\infty h}{\beta}\left(-\beta k\right)\sin kx=-U_\infty hk\sin kx .
$$

It is satisfied, and the disturbance decays as $y\to\infty$. The wall pressure is

$$
C_p=-\frac{2}{U_\infty}\phi_x(x,0)=-\frac{2hk}{\beta}\cos kx ,
$$

$1/\beta$ times the incompressible $-2hk\cos kx$. The decay rate $\beta k$ is smaller than the incompressible $k$, so the disturbance reaches $1/\beta$ times further from the wall, which is the lateral scale used in §6.

![[at_pg_wavy_wall.png|900]]

## 9. Numerical checks

All numbers use $\gamma=1.4$ and were computed in Python.

> [!check] Prandtl–Glauert against the worked examples
> - **Flat plate, $\alpha=4^\circ$, $M_\infty=0.7$:** $C_{l0}=2\pi(0.06981)=0.4386$, $\beta=0.7141$, $C_l=0.6142$.
> - **Critical Mach number, $C_{p0,min}=-0.4$:** the root of $C_{p0,min}/\beta=C_{p,cr}$ is $M_{crit}=0.747$, with $C_p=-0.602$ there ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Worked example: Cp0,min = −0.4|W07b §8]]).
> - **Wavy wall at $M_\infty=0.8$:** $1/\beta=1/0.6=1.667$, both for the wall pressure and for the decay length.

The supersonic criterion of §6 can be compared with the actual error of the linear theory. At $\theta=2^\circ$ the exact oblique-shock $C_p$ exceeds Ackeret's $2\theta/\lambda$ by 4.7 % at $M_\infty=1.5$, 4.5 % at 2 and 6.5 % at 3 ([[SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation#Leaving the Mach line: the weak-shock limit|θ–β–M deep dive §6]]). The parameter $(\gamma+1)M_\infty^4\theta/\lambda^3$ is 0.303, 0.258 and 0.300 at the same three Mach numbers. The error is a fraction of the parameter, as an order-of-magnitude estimate should give, and both are smallest at $M_\infty=2$.

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Lecture notes: [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]] (the Euler equations and the 4.2 CFD) · [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation]] (the lectured linearisation, $C_l$, $C_m$, $M_{crit}$, Kármán–Tsien)
- Next: [[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]] · [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]
- Related deep dives: [[SESA3029 Deep Dive - Riemann Invariants, Full Derivation]] (the characteristics of the hyperbolic case) · [[SESA3029 Deep Dive - Theta-Beta-Mach Relation, Full Derivation]] (the weak-shock limit)
- Concepts: [[Euler Equations]] · [[Linearised Compressible Potential Equation]] · [[Prandtl-Glauert Transformation]] · [[Homentropic Flow]] · [[Critical Mach Number]]
- Earlier years and other modules: [[SESA2022 T4 - Thin Aerofoil Theory]] (the incompressible $C_{p0}$) · [[Laplace's Equation]] · [[Streamfunction and Velocity Potential]]
- Formulae: [[SESA3029 Formula Sheet#Euler equations and compressible aerofoils|Formula sheet: Chapter 4]]

## Sources

- `Lecture4-1.pdf` (4.1 Euler Equations), slides 4–12: the conservation laws and vector form. Lectured Mon 2 Nov.
- `Lecture4-3.pdf` (4.3 Compressible Potential Flow Equations), slides 2–8: the steady equations, linearisation, $a^2$, the velocity potential equation and its limits, and $C_p$. Lectured Fri 6 Nov; recording `06 November 2026 at 16_57_37.txt` (L4-3).
- `Lecture4-4.pdf` (4.4 Prandtl-Glauert Transformation), slides 2–5: the transformation and the $C_p$, $C_l$, $C_m$ rules. Lectured Mon 9 Nov; recording `Lecture 4-4.txt` (L4-4).
- Anderson, *Modern Compressible Flow*, §§8.3–8.5 and 9.2–9.5 (the velocity potential equation, the perturbation equation and its order-of-magnitude reduction), and §11.4 (the transonic small-disturbance equation).
- Checks: the perturbation equation of §5, the second-order $C_p$ of §7, the local Mach number expansion of §6, the general-$A$ transformation and the wavy-wall solution of §8 were verified symbolically (sympy); all numbers were computed in Python. Figure `at_small_disturbance_regimes.png` from `generate_aerothermo_deepdive_figures.py`; `at_pg_wavy_wall.png` from `generate_aerothermo_w07_figures.py`.

## Self-study tasks

Tasks citing L4-1, L4-3 or L4-4 were set or posed in those lectures (Mon 2, Fri 6 and Mon 9 Nov; the same tasks appear in [[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Self-study tasks|W07b]]). Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(L4-3, ll. 55–327)** Derive $(1-M_\infty^2)\phi_{xx}+\phi_{yy}=0$ from the steady Euler equations, stating where each assumption enters. → [[#2. One equation for the velocity field|§§2–7]]
- [ ] **(L4-3, ll. 268–286)** Explain why the $(\gamma-1)u'U_\infty$ term is kept in $a^2$ but dropped from the linearised equation. → [[#7. The linearised equation and pressure coefficient|§7]]
- [ ] **(L4-3, ll. 355–378; L4-4, ll. 12–27)** Explain why the linear equation fails near $M_\infty=1$ and for hypersonic flow, using the size of the dropped terms. → [[#6. Order of magnitude: which terms survive|§6]]
- [ ] **(L4-4, ll. 28–138)** Derive the Prandtl–Glauert transformation and $C_p=C_{p0}/\sqrt{1-M_\infty^2}$. → [[#8. The Prandtl–Glauert transformation|§8]]

### Further practice

- [ ] **(L4-3, ll. 289–299)** The lecture invites a theory that keeps the second-order terms. Find the term that must be kept near $M_\infty=1$ and show that its coefficient is the local $1-M^2$. → [[#Transonic: the term that must be kept|§6, transonic]]
- [ ] (suggested, not lecturer-set) Derive the full potential equation and show that it is elliptic where $M<1$ and hyperbolic where $M>1$. → [[#4. The full potential equation|§4]]
- [ ] (suggested, not lecturer-set) Show that on a supersonic simple wave the three first-order nonlinear terms add to $(\gamma+1)M_\infty^4(u'/U_\infty)\phi_{xx}$, and that linear theory is most accurate at $M_\infty=2$. → [[#Supersonic: the three terms combine|§6, supersonic]]
- [ ] (suggested, not lecturer-set) Verify the wavy-wall solution and show that the Prandtl–Glauert $C_p$ is independent of the scale factor on $\phi$. → [[#8. The Prandtl–Glauert transformation|§8]]

## Transcript and slide slips

> [!warning] Why the linear equation fails at hypersonic speed
> Where: [[#6. Order of magnitude: which terms survive]].
>
> L4-3 (ll. 371–375) and L4-4 (ll. 19–23) explain the hypersonic limit by saying that when $1-M_\infty^2$ is a large negative number the $\phi_{xx}$ term dominates and the $\phi_{yy}$ term contributes very little. In any solution the two kept terms balance, $\phi_{yy}=(M_\infty^2-1)\phi_{xx}$, so neither becomes negligible. The failure comes from the dropped terms, whose combined size relative to the kept ones grows like $(\gamma+1)M_\infty\tau$ (§6).

### Slide slip (4.3)

> [!note] Slide 2 of 4.3
> Where: [[#2. One equation for the velocity field]].
>
> 4.3 slide 2 writes $u[\dots]$ outside the bracket in the $y$-momentum line; it should be $v[\dots]$. The bracket is zero by continuity, so the result is unaffected ([[SESA3029 W07b - Compressible Potential Flow and the Prandtl-Glauert Transformation#Transcript and slide slips|W07b]]).
