---
title: "SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 3: Nozzles and the Method of Characteristics"
order: 5
tags: [sesa3029, compressible-flow, method-of-characteristics, riemann-invariants, homentropic, prandtl-meyer, nozzle-design, minimum-length-nozzle]
aliases: ["SESA3029 Week 5", "SESA3029 Lecture 3.1", "SESA3029 Lecture 3.2", "SESA3029 Lecture 3.3", "SESA3029 Lecture 3.4", "MoC (SESA3029)"]
date: 2026-10-19
status: complete
coverage: "Lecture 3.1 lectured Fri 16 Oct (transcript); Lectures 3.2–3.4 written ahead from the slides and the supplementary note, awaiting lectures"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[Prandtl-Meyer Function]]", "[[Mach Waves and Mach Angle]]"]
next_topics: []
key_concepts: ["[[Method of Characteristics]]", "[[Riemann Invariants]]", "[[Homentropic Flow]]", "[[Minimum-Length Nozzle]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Lecture3-3.pdf", "02 - Sources/Lectures/Lecture3-4.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt"]
---

# SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design

> [!abstract] Summary
> **Steady, homentropic, irrotational, two-dimensional supersonic flow** reduces to two statements along the Mach lines:
>
> $$R^+=\nu-\theta=\text{const along }C^+\ (\text{inclined at }\theta+\mu),\qquad R^-=\nu+\theta=\text{const along }C^-\ (\text{inclined at }\theta-\mu).$$
>
> Here $\theta$ is the **flow inclination** to the $x$-axis (no longer a deflection), $\nu$ the Prandtl–Meyer function and $\mu$ the Mach angle.
>
> - **3.1** derives this from a curved streamtube: mass, $l$-momentum, homentropy and zero vorticity give two PDEs in $u$ and $\theta$. Swapping $u$ for $\nu$ and adding/subtracting turns them into the two **compatibility conditions**. $R^\pm$ are the **Riemann invariants**.
> - **3.2** gets the same result by diagonalising a $2\times2$ matrix (eigenvalues $\pm\tan\mu$), then builds the **unit process**: two known points give a third, $\nu_P=\tfrac12(R^+_A+R^-_B)$, $\theta_P=\tfrac12(R^-_B-R^+_A)$, located with averaged slopes.
> - **3.3** adds the boundary conditions (reflecting wall, cancelling wall, symmetry plane) and designs the **minimum-length nozzle**: $\theta_{max}=\nu(M_e)/2$. For $M_e=2.4$ with four characteristics, $x_e/r_a=8.069$ and $y_e/r_a=2.400$, against the 1D $A_e/A^*=2.4031$.
> - **3.4** works a channel symbolically, finds that point 3 cannot reflect, and solves the inverse problem: $M_4=2.2$, $M_6=2.4$ give $\theta_w=5.0140^\circ$ and $M_0=1.8340$.

## Key concepts

- New: [[Method of Characteristics]] · [[Riemann Invariants]] · [[Homentropic Flow]] · [[Minimum-Length Nozzle]]
- From W03: [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]] · [[Expansion Fan]]
- From W04: [[Isentropic Nozzle Flow]] (SESA2022) and the area–velocity relation, which reappears here in streamtube form
- Maths: [[Eigenvalues and Eigenvectors]] (MATH1054) · [[Characteristic Equation and Eigenvalues]] (SESA2027)

> [!info] Where this was lectured
> **Lecture 3.1 was lectured on Fri 16 Oct** (`Lecture 3-1.txt`, Prof. Jae-Wook Kim, 372 lines). 2.6 had announced MoC for Thursday, but Thursday 15 Oct was spent on 2.7 instead (L2-7, ll. 192–203). The lecture covered the whole 3.1 deck:
> - admin: Test 2 and the MoC coursework (ll. 3–12, see below);
> - why a 2D method, and the new meaning of $\theta$ (ll. 13–55);
> - streamtube geometry (ll. 56–85), mass (ll. 86–123), momentum with homentropy (ll. 124–204), zero vorticity (ll. 205–241);
> - the switch to $\nu$, the two angle equations (ll. 242–293), adding/subtracting (ll. 294–303);
> - the directional-derivative argument and the Riemann invariants (ll. 304–368). It ended with *"next week, I'm going to show you how to actually use that one"* (l. 370).
>
> **Lectures 3.2–3.4 have not been lectured yet.** By request they are written up in full from the slides and the supplementary note (§§8–16). Their tasks are marked **slide-set**. When the recordings arrive, add line references and slips as was done for W03 and W04.

## Announcements and deadlines

> [!important] Announcements (L3-1, ll. 3–12)
> - **Blackboard Test 2** opens on the morning of **Mon 19 Oct** and stays open until **Sunday 25 Oct, midnight** (ll. 3–5).
> - **MoC coursework:** the brief will be announced *"towards the end of next week"*, i.e. by about Fri 23 Oct (l. 6). It is due *"by end of week seven"*. Week 6 is a reading week, *"and then after that, you have one more week"* (ll. 8–11).
> - Date check: the Week 1 module guide said **15 Nov**. Counting W04 as the week of 12 Oct, the end of week 7 is about **Fri 6 Nov**. The two do not match, so take the date from the brief when it appears.

---

## The whole topic in one physical picture

Think of supersonic flow as a mesh of **Mach lines**. Each line carries one number from upstream and never changes it.

1. Through every point pass two Mach lines, one at $+\mu$ to the local flow ($C^+$, the left-running line) and one at $-\mu$ ($C^-$, the right-running line). Information travels only along them; nothing travels upstream.
2. A $C^+$ line carries $\nu-\theta$ unchanged and a $C^-$ line carries $\nu+\theta$ unchanged. Where two lines cross, the two numbers fix both $\nu$ (hence $M$) and $\theta$. **Solving the flow is bookkeeping**: no PDE has to be integrated.
3. Walls and the centreline decide what happens when a line arrives. A **prescribed** wall reflects it (a new line leaves). A **designed** wall is shaped to absorb it (nothing leaves). The centreline is a mirror.
4. Design a nozzle wall that absorbs every wave arriving at it and the exit flow is **uniform and shock-free**. Put all the expansion into a sharp corner at the throat and that nozzle is also the **shortest** possible.

---

## 1. Why a two-dimensional method (3.1 slide 2)

The 1D theory of W04 assumes properties are uniform across each section. That is exact only on the centreline. At the wall the velocity must be **tangential to the wall**, so it has a vertical component that 1D theory cannot see (ll. 18–24). Both the direction and the magnitude of the velocity vary across a section, and a rapidly expanding part drops the pressure locally (ll. 24–26). 1D theory also gives the exit area but **no length** (W04 §7, L2-6 ll. 279–291). MoC resolves both $x$ and $y$.

> [!warning] $\theta$ changes meaning in this chapter (slide 3; ll. 37–55, 85)
> In Lectures 2.1–2.7, $\theta$ was the **deflection**: how far the flow turned relative to the incoming velocity. In MoC, $\theta$ is the **inclination** of the local velocity to the fixed $x$-axis. A turn through a small angle is now $\Delta\theta$. The lecturer stressed this twice.

**Assumptions** (slide 2 and ll. 150–157, 212–216):

- steady and planar (infinite in $z$);
- inviscid and adiabatic, with **no shocks**, so entropy is constant **everywhere**, not just along each streamline. This is [[Homentropic Flow]];
- irrotational. The lecture assumes it. The supplementary note (p. 2) justifies it: by Crocco's theorem a steady flow with uniform $s$ and $T_0$ has zero vorticity. The lecturer called the result *"compressible potential flow"* (l. 216).

---

## 2. The curved streamtube and its geometry (3.1 slide 3)

![[at_moc_streamtube_geometry.png|900]]

Take a small element between two streamlines (ll. 29–40). Use local axes: $l$ along the velocity at the corner, $n$ normal to it. The element has width $\Delta l$ and height $\Delta n$. The flow has inclination $\theta$ to $x$.

Moving up by $\Delta n$, the top streamline is inclined at $\theta+\Delta\theta$, with

$$
\Delta\theta=\frac{\partial\theta}{\partial n}\,\Delta n .
$$

So over the length $\Delta l$ the right face is taller than the left face by the arc $\Delta l\,\Delta\theta$ (ll. 60–66):

$$
\Delta n'-\Delta n=\Delta\theta\,\Delta l .
$$

Substitute $\Delta\theta$:

$$
\Delta n'-\Delta n=\left(\frac{\partial\theta}{\partial n}\,\Delta n\right)\Delta l .
$$

Divide by $\Delta n\,\Delta l$:

$$
\frac{1}{\Delta n}\,\frac{\Delta n'-\Delta n}{\Delta l}=\frac{\partial\theta}{\partial n}.
$$

Let $\Delta l\to0$. The left side becomes a derivative along $l$ (ll. 76–79):

$$
\boxed{\frac{\partial\theta}{\partial n}=\frac{1}{\Delta n}\,\frac{\partial\,\Delta n}{\partial l}}
$$

> [!tip] What it says
> If the streamlines fan apart in the $n$-direction ($\partial\theta/\partial n>0$), the streamtube widens along the flow. $\partial\theta/\partial n$ plays the part of $\mathrm dA/A$ per unit length in the 1D nozzle.

---

## 3. Mass conservation (3.1 slide 4)

No flow crosses a streamline, so the mass flow per unit span is the same through both faces (ll. 86–102):

$$
\rho u\,\Delta n=\left(\rho+\frac{\partial\rho}{\partial l}\Delta l\right)\left(u+\frac{\partial u}{\partial l}\Delta l\right)\left(\Delta n+\frac{\partial\Delta n}{\partial l}\Delta l\right).
$$

Multiply out the first two brackets and drop the $\Delta l^2$ term:

$$
\left(\rho+\frac{\partial\rho}{\partial l}\Delta l\right)\left(u+\frac{\partial u}{\partial l}\Delta l\right)=\rho u+\rho\frac{\partial u}{\partial l}\Delta l+u\frac{\partial\rho}{\partial l}\Delta l.
$$

Multiply by the third bracket and drop the $\Delta l^2$ and $\Delta l^3$ terms:

$$
\rho u\,\Delta n=\rho u\,\Delta n+\rho\frac{\partial u}{\partial l}\Delta l\,\Delta n+u\frac{\partial\rho}{\partial l}\Delta l\,\Delta n+\rho u\frac{\partial\Delta n}{\partial l}\Delta l .
$$

Cancel $\rho u\,\Delta n$ from both sides (ll. 98–100):

$$
0=\rho\frac{\partial u}{\partial l}\Delta l\,\Delta n+u\frac{\partial\rho}{\partial l}\Delta l\,\Delta n+\rho u\frac{\partial\Delta n}{\partial l}\Delta l .
$$

Divide by $\rho u\,\Delta n\,\Delta l$:

$$
\frac{1}{u}\frac{\partial u}{\partial l}+\frac{1}{\rho}\frac{\partial\rho}{\partial l}+\frac{1}{\Delta n}\frac{\partial\Delta n}{\partial l}=0 .
$$

Replace the last term using §2 (ll. 117–121):

$$
\boxed{\frac{1}{u}\frac{\partial u}{\partial l}+\frac{1}{\rho}\frac{\partial\rho}{\partial l}+\frac{\partial\theta}{\partial n}=0}
$$

> [!tip] You have done this before
> This is the bracket expansion of the Laval-nozzle mass balance, $\mathrm d\rho/\rho+\mathrm dU/U+\mathrm dA/A=0$ ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#The lecture's route: a control volume with side walls|W04 §1]]), with the local streamtube height in place of the duct area. The lecturer pointed back to it but named the wrong lecture (see the slips table).

---

## 4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)

**Momentum in $l$** (ll. 124–147). Momentum out minus momentum in equals the net pressure force in $l$. Per unit span, $\dot m=\rho u\,\Delta n$. The forces are:

- $p\,\Delta n$ on the left face, pushing in $+l$;
- $\left(p+\tfrac12\frac{\partial p}{\partial l}\Delta l\right)(\Delta n'-\Delta n)$ from the inclined top face, pushing in $+l$. The face carries the mean pressure, and its $l$-projection is the height change;
- $\left(p+\frac{\partial p}{\partial l}\Delta l\right)\Delta n'$ on the right face, pushing in $-l$.

So

$$
\dot m\left(u+\frac{\partial u}{\partial l}\Delta l\right)-\dot m u=p\,\Delta n+\left(p+\frac{1}{2}\frac{\partial p}{\partial l}\Delta l\right)(\Delta n'-\Delta n)-\left(p+\frac{\partial p}{\partial l}\Delta l\right)\Delta n' .
$$

The left side is $\dot m\,\frac{\partial u}{\partial l}\Delta l=\rho u\,\Delta n\,\frac{\partial u}{\partial l}\Delta l$. Expand the right side:

$$
p\,\Delta n+p\,\Delta n'-p\,\Delta n+\frac{1}{2}\frac{\partial p}{\partial l}\Delta l\,(\Delta n'-\Delta n)-p\,\Delta n'-\frac{\partial p}{\partial l}\Delta l\,\Delta n' .
$$

The $p\,\Delta n$ and $p\,\Delta n'$ terms cancel. $\Delta n'-\Delta n=\Delta\theta\,\Delta l$ is itself of order $\Delta l$, so the half term is $O(\Delta l^2)$ and is dropped:

$$
\rho u\,\Delta n\,\frac{\partial u}{\partial l}\Delta l=-\frac{\partial p}{\partial l}\Delta l\,\Delta n' .
$$

Divide by $\Delta n\,\Delta l$ and let $\Delta l\to0$, so $\Delta n'\to\Delta n$:

$$
\boxed{\rho u\,\frac{\partial u}{\partial l}=-\frac{\partial p}{\partial l}}
$$

This is Euler's equation along a streamline, the same as $\rho U\,\mathrm dU=-\mathrm dp$ in W04 (l. 146).

**Homentropic link** (ll. 159–185). To remove $p$, write $\partial p/\partial l=(\partial p/\partial\rho)_s\,\partial\rho/\partial l$. With $p=C\rho^\gamma$:

$$
\frac{\partial p}{\partial\rho}=\gamma C\rho^{\gamma-1}=\gamma\,\frac{C\rho^\gamma}{\rho}=\gamma\,\frac{p}{\rho}=\gamma RT=a^2 .
$$

So the momentum equation becomes

$$
\rho u\,\frac{\partial u}{\partial l}=-a^2\,\frac{\partial\rho}{\partial l}.
$$

**Combine with mass** (ll. 186–200). From §3,

$$
\frac{\partial\rho}{\partial l}=-\rho\left(\frac{\partial\theta}{\partial n}+\frac{1}{u}\frac{\partial u}{\partial l}\right).
$$

Substitute:

$$
\rho u\,\frac{\partial u}{\partial l}=\rho a^2\left(\frac{\partial\theta}{\partial n}+\frac{1}{u}\frac{\partial u}{\partial l}\right).
$$

Divide by $\rho a^2$ and write the left side as $\frac{u^2}{a^2}\cdot\frac{1}{u}\frac{\partial u}{\partial l}=M^2\,\frac{1}{u}\frac{\partial u}{\partial l}$:

$$
M^2\,\frac{1}{u}\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}+\frac{1}{u}\frac{\partial u}{\partial l}.
$$

Collect the $u$ terms:

$$
\boxed{\left(M^2-1\right)\frac{1}{u}\frac{\partial u}{\partial l}=\frac{\partial\theta}{\partial n}}
$$

> [!check] It is the area–velocity relation again
> With $\partial\theta/\partial n$ as the fractional area change, this is $\mathrm dA/A=(M^2-1)\,\mathrm dU/U$ (W04 §1). For $M>1$, flow speeds up where the streamlines diverge, as in the Laval nozzle.

---

## 5. Zero vorticity (3.1 slide 7)

The equation in §4 has two unknowns, $u$ and $\theta$, so a second equation is needed (ll. 205–211). It comes from **irrotationality**:

$$
\omega=\frac{\partial v}{\partial l}-\frac{\partial u}{\partial n}=0,
$$

with $u$ along $l$ and $v$ along $n$ (ll. 219–223).

At the corner of the element $v=0$, because $l$ is aligned with the flow. At the right face the flow has turned by $\Delta\theta$, so its $n$-component is (ll. 226–229)

$$
\Delta v=\left(u+\frac{\partial u}{\partial l}\Delta l\right)\Delta\theta .
$$

Divide by $\Delta l$ and let $\Delta l\to0$ (ll. 230–236):

$$
\frac{\partial v}{\partial l}=\lim_{\Delta l\to0}\left(u+\frac{\partial u}{\partial l}\Delta l\right)\frac{\Delta\theta}{\Delta l}=u\,\frac{\partial\theta}{\partial l}.
$$

Substitute into $\omega=0$:

$$
u\,\frac{\partial\theta}{\partial l}-\frac{\partial u}{\partial n}=0 .
$$

Divide by $u$:

$$
\boxed{\frac{\partial\theta}{\partial l}-\frac{1}{u}\frac{\partial u}{\partial n}=0}
$$

> [!note] Why the story does not stop here (ll. 240–248)
> Two equations, two unknowns, *"so that's very good"*. But both contain the nonlinear $\frac1u\,\partial u/\partial(\cdot)$, and nobody could find a general solution. The way forward came from looking back at Lecture 2.4.

---

## 6. Rewriting in angles with the Prandtl–Meyer function (3.1 slide 8)

![[at_moc_characteristic_geometry.png|900]]

From Lecture 2.4 ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]), a supersonic flow turning gradually through Mach waves obeys (ll. 249–254)

$$
\frac{\mathrm du}{u}=\tan\mu\;\mathrm d\nu,
\qquad
\tan\mu=\frac{1}{\sqrt{M^2-1}} .
$$

It holds for a change in any direction, so (ll. 256–258)

$$
\frac{1}{u}\frac{\partial u}{\partial l}=\tan\mu\,\frac{\partial\nu}{\partial l},
\qquad
\frac{1}{u}\frac{\partial u}{\partial n}=\tan\mu\,\frac{\partial\nu}{\partial n}.
$$

**Equation 1.** Substitute the first into §4:

$$
\left(M^2-1\right)\tan\mu\,\frac{\partial\nu}{\partial l}=\frac{\partial\theta}{\partial n}.
$$

Simplify the coefficient (ll. 261–262):

$$
\left(M^2-1\right)\tan\mu=\frac{M^2-1}{\sqrt{M^2-1}}=\sqrt{M^2-1}=\frac{1}{\tan\mu}.
$$

So

$$
\frac{1}{\tan\mu}\,\frac{\partial\nu}{\partial l}=\frac{\partial\theta}{\partial n}.
$$

Multiply by $\tan\mu$:

$$
\boxed{\text{Eq. 1:}\quad\frac{\partial\nu}{\partial l}-\tan\mu\,\frac{\partial\theta}{\partial n}=0}
$$

**Equation 2.** Substitute the second into §5 (ll. 283–285):

$$
\boxed{\text{Eq. 2:}\quad\frac{\partial\theta}{\partial l}-\tan\mu\,\frac{\partial\nu}{\partial n}=0}
$$

Both equations are now about **angles**: $\nu$, $\theta$ and $\mu$. They are the same equation with $\nu$ and $\theta$ swapped (ll. 286–294, *"Wow. What's going on?"*). They are still nonlinear, because $\tan\mu$ depends on $M$ and so on $\nu$.

---

## 7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)

**Add and subtract** (ll. 297–303). Eq. 1 minus Eq. 2:

$$
\frac{\partial\nu}{\partial l}-\frac{\partial\theta}{\partial l}-\tan\mu\,\frac{\partial\theta}{\partial n}+\tan\mu\,\frac{\partial\nu}{\partial n}=0 .
$$

Group by unknown:

$$
\frac{\partial(\nu-\theta)}{\partial l}+\tan\mu\,\frac{\partial(\nu-\theta)}{\partial n}=0 .
\tag{A}
$$

Eq. 1 plus Eq. 2:

$$
\frac{\partial\nu}{\partial l}+\frac{\partial\theta}{\partial l}-\tan\mu\,\frac{\partial\theta}{\partial n}-\tan\mu\,\frac{\partial\nu}{\partial n}=0 .
$$

Group by unknown:

$$
\frac{\partial(\nu+\theta)}{\partial l}-\tan\mu\,\frac{\partial(\nu+\theta)}{\partial n}=0 .
\tag{B}
$$

Each equation now has **one** unknown combination.

**The bracket is a derivative along a line** (slides 9–10; ll. 306–330). For any function $f(l,n)$,

$$
\Delta f=\frac{\partial f}{\partial l}\Delta l+\frac{\partial f}{\partial n}\Delta n .
$$

Take $\Delta l$ out:

$$
\Delta f=\Delta l\left(\frac{\partial f}{\partial l}+\frac{\Delta n}{\Delta l}\,\frac{\partial f}{\partial n}\right).
$$

Now step along a line at angle $+\mu$ to the flow, so $\Delta n/\Delta l=\tan\mu$:

$$
\Delta f=\Delta l\left(\frac{\partial f}{\partial l}+\tan\mu\,\frac{\partial f}{\partial n}\right).
$$

If the bracket is zero, $f$ does not change along that line.

**Apply it** (slide 11; ll. 334–355). Put $f=\nu-\theta$. By (A) the bracket vanishes, so

$$
\Delta(\nu-\theta)=0\ \text{along the line at }+\mu .
$$

Put $f=\nu+\theta$ and step along $-\mu$ ($\Delta n/\Delta l=-\tan\mu$). By (B),

$$
\Delta(\nu+\theta)=0\ \text{along the line at }-\mu .
$$

The lines at $\pm\mu$ to the flow are the **Mach lines**, called the **characteristics** $C^\pm$. Relative to the $x$-axis they are inclined at $\theta\pm\mu$.

> [!important] The compatibility conditions (slide 12; ll. 361–367)
> $$\boxed{R^+=\nu-\theta\ \text{is constant along }C^+,\qquad R^-=\nu+\theta\ \text{is constant along }C^-}$$
>
> $R^+$ and $R^-$ are the **[[Riemann Invariants]]**. $C^+$ runs **left** of the flow (upwards for flow to the right), $C^-$ runs **right** of it.
>
> **Anderson's notation** is $K^+=-R^+=\theta-\nu$ and $K^-=R^-=\theta+\nu$. The physics is the same; just be consistent. [[SESA3029 Example Sheet 2 - Solutions]] was first written in Anderson's form and now gives both.

> [!tip] Why the lecturer was so pleased (ll. 341–360)
> Know $\nu-\theta$ at **one** point of an infinitely long $C^+$ line and you know it everywhere on that line. *"You don't have to solve it."* Two crossing lines give both $\nu$ and $\theta$ at the crossing. The PDE has become an initial-value problem marched downstream. Many numerical methods, CFD included, still use characteristics for this reason.

> [!check] The Prandtl–Meyer fan is a special case
> Uniform flow ($\theta=0$, $\nu=\nu_1$) passes a convex corner on an **upper** wall that turns it up by $\theta_w$. The corner sends out $C^-$ waves. Every $C^+$ line crossing the fan comes from the uniform stream, so $R^+=\nu_1-0$ throughout. After the fan, $\theta=\theta_w$, so $\nu_2-\theta_w=\nu_1$:
>
> $$\nu_2=\nu_1+\theta_w ,$$
>
> exactly the W03 result. A region where one invariant is the same everywhere is called a **simple** region (§12).

---

## 8. The eigenvalue route (3.2 slides 2–4)

Lecture 3.2 re-derives the same result by linear algebra (supplementary note §2). It is quicker, and it shows why the method needs $M>1$.

**Matrix form.** Write Eqs. 1 and 2 with $\hat Q=[\nu,\ \theta]^T$:

$$
\frac{\partial\hat Q}{\partial l}+\underline A\,\frac{\partial\hat Q}{\partial n}=\hat 0,
\qquad
\underline A=\begin{bmatrix}0&-\tan\mu\\-\tan\mu&0\end{bmatrix}.
$$

**Eigenvalues.**

$$
\det(\underline A-\lambda\underline I)=\begin{vmatrix}-\lambda&-\tan\mu\\-\tan\mu&-\lambda\end{vmatrix}=\lambda^2-\tan^2\mu=0 .
$$

So

$$
\lambda_1=+\tan\mu,\qquad\lambda_2=-\tan\mu .
$$

**Eigenvectors**, from $(\underline A-\lambda\underline I)\hat v=\hat 0$:

- $\lambda_1=\tan\mu$: the first row gives $-\tan\mu\,v_1-\tan\mu\,v_2=0$, so $v_2=-v_1$ and $\hat v_1\propto[1,\,-1]^T$.
- $\lambda_2=-\tan\mu$: the first row gives $\tan\mu\,v_1-\tan\mu\,v_2=0$, so $v_2=v_1$ and $\hat v_2\propto[1,\ 1]^T$.

Scale them as on the slide and invert:

$$
\underline E=\frac12\begin{bmatrix}1&1\\-1&1\end{bmatrix},
\qquad
\underline E^{-1}=\begin{bmatrix}1&-1\\1&1\end{bmatrix}.
$$

**Check the diagonalisation.** First

$$
\underline A\,\underline E=\frac12\begin{bmatrix}\tan\mu&-\tan\mu\\-\tan\mu&-\tan\mu\end{bmatrix}.
$$

Then

$$
\underline E^{-1}\underline A\,\underline E=\frac12\begin{bmatrix}\tan\mu+\tan\mu&-\tan\mu+\tan\mu\\\tan\mu-\tan\mu&-\tan\mu-\tan\mu\end{bmatrix}=\begin{bmatrix}\tan\mu&0\\0&-\tan\mu\end{bmatrix}=\underline\Lambda .
$$

**Decouple.** Substitute $\underline A=\underline E\,\underline\Lambda\,\underline E^{-1}$:

$$
\frac{\partial\hat Q}{\partial l}+\underline E\,\underline\Lambda\,\underline E^{-1}\frac{\partial\hat Q}{\partial n}=\hat 0 .
$$

Premultiply by $\underline E^{-1}$:

$$
\underline E^{-1}\frac{\partial\hat Q}{\partial l}+\underline\Lambda\,\underline E^{-1}\frac{\partial\hat Q}{\partial n}=\hat 0 .
$$

$\underline E$ contains no $\mu$, so it is a **constant** matrix and passes through the derivatives. Define

$$
\hat R=\underline E^{-1}\hat Q=\begin{bmatrix}\nu-\theta\\\nu+\theta\end{bmatrix}.
$$

Then

$$
\frac{\partial\hat R}{\partial l}+\underline\Lambda\,\frac{\partial\hat R}{\partial n}=\hat 0 .
$$

Row by row:

$$
\frac{\partial(\nu-\theta)}{\partial l}+\tan\mu\,\frac{\partial(\nu-\theta)}{\partial n}=0,
\qquad
\frac{\partial(\nu+\theta)}{\partial l}-\tan\mu\,\frac{\partial(\nu+\theta)}{\partial n}=0 .
$$

These are (A) and (B) of §7.

> [!tip] What the eigenvalues mean
> - The eigenvalues **are** the characteristic slopes $\Delta n/\Delta l=\pm\tan\mu$ relative to the streamline.
> - The eigenvectors are just "take the difference" and "take the sum" of $\nu$ and $\theta$.
> - Real, distinct eigenvalues make the system **hyperbolic**, which needs $M>1$. For $M<1$, $\mu=\sin^{-1}(1/M)$ does not exist. The system is then elliptic, every point influences every other, and marching fails. That is why MoC is a supersonic method.
> - The supplementary note warns that eigenvectors are defined only up to a scale factor, so a computer package may scale them differently. Any scaling with $\underline E\,\underline E^{-1}=\underline I$ works. Practise on [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]].

---

## 9. Zones of dependence and influence (3.2 slides 5–6)

![[at_moc_unit_process.png|900]]

**Recap of the Mach cone** (slide 5). A source moving at $U$ emits sound that spreads at $a$. After $3\Delta t$ the front has radius $3a\Delta t$ and the source has moved $3U\Delta t$. The envelope makes the angle

$$
\sin\mu=\frac{3a\,\Delta t}{3U\,\Delta t}=\frac{1}{M}
\quad\Longrightarrow\quad
\mu=\sin^{-1}\frac1M .
$$

**Zones** (slide 6, panel 1 of the figure). The two characteristics through a point P divide the plane:

- **zone of influence**: the wedge **downstream** between the $C^+$ and $C^-$ leaving P. P can affect only events there;
- **zone of dependence**: the wedge **upstream** between the $C^+$ and $C^-$ arriving at P. The state at P depends only on events there.

This is the Mach-cone idea from W02 applied to every point of the flow.

---

## 10. The unit process (3.2 slides 7–9)

**Flow state** (slide 7). Let A and B be known points, with A **below** (its $C^+$ reaches P) and B **above** (its $C^-$ reaches P). The invariants carry over unchanged:

$$
\nu_P-\theta_P=R^+_A=\nu_A-\theta_A,
\qquad
\nu_P+\theta_P=R^-_B=\nu_B+\theta_B .
$$

Add the two:

$$
2\nu_P=R^+_A+R^-_B
\quad\Longrightarrow\quad
\boxed{\nu_P=\frac{R^+_A+R^-_B}{2}}
$$

Subtract the first from the second:

$$
2\theta_P=R^-_B-R^+_A
\quad\Longrightarrow\quad
\boxed{\theta_P=\frac{R^-_B-R^+_A}{2}}
$$

Then $M_P$ comes from $\nu_P$ (IFT), and $\mu_P=\sin^{-1}(1/M_P)$. The solution has been **marched downstream**.

> [!tip] In planar flow the states do not need the geometry
> $\nu_P$ and $\theta_P$ depend only on $R^\pm$, never on $x$ or $y$. You can fill in the whole flow-state table first and find the coordinates afterwards. Lecture 3.4 does the entire example symbolically without a single coordinate. This decoupling fails for axisymmetric nozzles (§16).

**Location** (slide 8; supplementary note eqs. 14–16). The characteristics are curved, so use the **average** of their slopes at the two ends:

$$
\alpha_{AP}=\tfrac12\left[(\theta+\mu)_A+(\theta+\mu)_P\right],
\qquad
\alpha_{BP}=\tfrac12\left[(\theta-\mu)_B+(\theta-\mu)_P\right].
$$

Each segment is a straight line:

$$
\tan\alpha_{AP}=\frac{y_P-y_A}{x_P-x_A},
\qquad
\tan\alpha_{BP}=\frac{y_P-y_B}{x_P-x_B}.
$$

From the first,

$$
y_P=y_A+(x_P-x_A)\tan\alpha_{AP}.
$$

Substitute into the second, multiplied out:

$$
y_A+(x_P-x_A)\tan\alpha_{AP}-y_B=(x_P-x_B)\tan\alpha_{BP}.
$$

Collect the $x_P$ terms:

$$
x_P\left(\tan\alpha_{BP}-\tan\alpha_{AP}\right)=x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}-(y_B-y_A).
$$

Divide:

$$
\boxed{x_P=\frac{x_B\tan\alpha_{BP}-x_A\tan\alpha_{AP}-(y_B-y_A)}{\tan\alpha_{BP}-\tan\alpha_{AP}},\qquad y_P=y_A+(x_P-x_A)\tan\alpha_{AP}}
$$

### Worked example (3.2 slide 9)

Point 1 at $(0.69,\ 0.62)$ with $M_1=1.6$, $\theta_1=12^\circ$. Point 2 at $(1.08,\ 0)$ with $M_2=1.4$, $\theta_2=0$. Find point 3.

Point 1 is above, so its $C^-$ reaches 3 (role B). Point 2 is below, so its $C^+$ reaches 3 (role A).

1. Prandtl–Meyer and Mach angles: $\nu_1=\nu(1.6)=14.8604^\circ$, $\mu_1=38.6822^\circ$; $\nu_2=\nu(1.4)=8.9870^\circ$, $\mu_2=45.5847^\circ$.
2. Invariants: $R^-_1=14.8604+12=26.8604^\circ$; $R^+_2=8.9870-0=8.9870^\circ$.
3. Point 3: $\nu_3=\tfrac12(8.9870+26.8604)=17.9237^\circ$; $\theta_3=\tfrac12(26.8604-8.9870)=8.9367^\circ$.
4. Invert $\nu$: $M_3=1.7039$, so $\mu_3=\sin^{-1}(1/1.7039)=35.9371^\circ$.
5. $\alpha_{23}=\tfrac12[(0+45.5847)+(8.9367+35.9371)]=\tfrac12(45.5847+44.8738)=45.2292^\circ$, so $\tan\alpha_{23}=1.00803$.
6. $\alpha_{13}=\tfrac12[(12-38.6822)+(8.9367-35.9371)]=\tfrac12(-26.6822-27.0004)=-26.8413^\circ$, so $\tan\alpha_{13}=-0.50604$.
7. Point 1 plays B and point 2 plays A:

$$
x_3=\frac{0.69(-0.50604)-1.08(1.00803)-(0.62-0)}{-0.50604-1.00803}=\frac{-0.34917-1.08868-0.62}{-1.51407}=\frac{-2.05785}{-1.51407}=1.3591 .
$$

8. $y_3=0+(1.3591-1.08)(1.00803)=0.2814$.

$$
\boxed{M_3=1.7039,\quad\theta_3=8.9367^\circ,\quad(x_3,y_3)=(1.3591,\ 0.2814)}
$$

> [!check] Against the slide
> The slide gives $1.7039$, $8.9367^\circ$ and $(1.3592,\ 0.2814)$ ✓. The last digit of $x_3$ is rounding in the slide's intermediate angles.
>
> Using the slopes at points 1 and 2 only, with no averaging, moves point 3 to $(1.3584,\ 0.2841)$, about $0.003$ away. Averaging matters more when $\mu$ changes a lot between the points, as near $M=1$.

**Calculation procedure** (slides 10–11).

1. On a starting line where the flow is known, compute $\nu$, $\theta$ and $\mu$ at several points, then $R^+$ and $R^-$.
2. Compute $\theta+\mu$ and $\theta-\mu$ at each point.
3. March downstream to the crossing points and get $\nu$ and $\theta$ there.
4. Get $M$ from $\nu$, then $\mu=\sin^{-1}(1/M)$.
5. Get the angles $\alpha$, then the coordinates of the new points.
6. Repeat, applying the wall and symmetry **boundary conditions** where the lines reach a boundary (§11).

---

## 11. Boundary conditions (3.3 slides 4–7)

![[at_moc_boundary_conditions.png|900]]

A wall point has only **one** characteristic arriving from upstream: a $C^+$ at the top wall, a $C^-$ at the bottom wall. So the interior formulas (two lines, two equations) cannot be used. The wall supplies the missing condition instead: the flow must be tangential to it.

### BC 1: a prescribed wall reflects (slide 5)

The wall shape is given, so $\theta_W$ is known. At a top wall, the $C^+$ from A gives

$$
R^+_W=R^+_A
\quad\Longrightarrow\quad
\nu_W-\theta_W=R^+_A
\quad\Longrightarrow\quad
\boxed{\nu_W=R^+_A+\theta_W}
$$

$M_W$ follows from $\nu_W$. A **reflected** $C^-$ leaves W, carrying

$$
R^-_W=\nu_W+\theta_W=R^+_A+2\theta_W .
$$

If $\theta_A=\theta_W$, then $\nu_W=\nu_A$ and $R^-_W=\nu_A+\theta_A=R^-_A$. The "reflected" line carries the same invariant as the $C^-$ already through A, so **there is no new wave**. A reflection occurs only when $\theta_A\neq\theta_W$.

At a **bottom** wall the roles swap: $\nu_W=R^-_B-\theta_W$, and the reflected $C^+$ carries $R^+_W=R^-_B-2\theta_W$.

The slides give no coordinate formula for BC 1. Intersect the $C^+$ line from A with the known wall curve. $\theta_W$ depends on where the line lands, so iterate if you use averaged slopes. [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]] is a worked case.

### BC 2: a designed wall cancels (slide 6)

Here the wall angle is **chosen**: set $\theta_W=\theta_A$, so the flow does not turn between A and W. Then

$$
\nu_W=R^+_A+\theta_W=(\nu_A-\theta_A)+\theta_A=\nu_A
\quad\Longrightarrow\quad
M_W=M_A ,
$$

and no wave is reflected. This is how a nozzle is designed to give uniform exit flow.

**Location**, using the unit-process formula with P replaced by W and B the **previous wall point** (supplementary note eq. 17):

$$
\boxed{\alpha_{AW}=(\theta+\mu)_A,\qquad\alpha_{BW}=\tfrac12(\theta_B+\theta_W)}
$$

- A and W have the same state, so the $C^+$ segment is straight and needs no averaging.
- BW is a piece of wall, which is a streamline. Its slope is the average of the flow angles at its ends.

### BC 3: the symmetry plane is a mirror (slide 7)

On the centreline symmetry needs $\theta_P=0$. The $C^-$ from B gives

$$
R^-_B=R^-_P=\nu_P+0
\quad\Longrightarrow\quad
\boxed{\nu_P=R^-_B}
$$

The mirror image A of B has $\nu_A=\nu_B$ and $\theta_A=-\theta_B$, so

$$
R^+_A=\nu_A-\theta_A=\nu_B+\theta_B=R^-_B .
$$

Hence $R^+_P=R^-_P$: the $C^-$ arriving from above leaves as a $C^+$ with the same invariant, which is a reflected wave.

**Location.** $y_P=y_{centre}$, normally $0$. The $C^-$ from B satisfies $\tan\alpha_{BP}=(0-y_B)/(x_P-x_B)$, so

$$
\boxed{x_P=x_B-\frac{y_B}{\tan\alpha_{BP}},\qquad\alpha_{BP}=\tfrac12\left[(\theta-\mu)_B-\mu_P\right]}
$$

using $(\theta-\mu)_P=0-\mu_P$. By symmetry $\alpha_{AP}=-\alpha_{BP}$, so only half the nozzle has to be computed.

---

## 12. Nozzles with a straightening section (3.3 slides 8–9)

A practical supersonic nozzle downstream of the throat has two parts (Anderson's figure in 3.1 slide 2, 3.2 slide 12 and 3.3 slide 4; the ANSYS sketch in 3.3 slide 8):

- an **expansion section** of **prescribed** geometry. Characteristics from the walls reflect (BC 1) and cross each other, so the region is **non-simple**. The wall slope rises to $\theta_{max}$ at the end of this section (slide 9);
- a **straightening section** of **designed** geometry. Each arriving characteristic is cancelled (BC 2), and the wall slope falls back to zero.

The regions that result:

| Region | Characteristics | Example in the figures |
|---|---|---|
| non-simple | both families cross | the expansion section, the kernel behind the throat corner |
| **simple** | one family only, no crossings; one invariant is the same everywhere | the amber triangles next to the designed walls |
| **uniform** | none: constant $M_e$, $\theta=0$ | the blue exit core |

The start line cannot be the throat itself. At $M=1$, $\mu=90^\circ$, so the characteristics stand at right angles to the flow (supplementary note p. 9). The calculation starts just downstream.

---

## 13. The minimum-length nozzle (3.3 slide 10)

![[at_moc_min_length_nozzle.png|900]]

To make the nozzle as short as possible, remove the prescribed section entirely. All the expansion then happens in a **centred Prandtl–Meyer fan at a sharp corner C** at the throat, and the wall downstream is designed to cancel every wave. See [[Minimum-Length Nozzle]].

**Derivation of the corner angle.**

1. The throat is sonic: $M=1$, so $\nu(1)=0$ and $\theta=0$.
2. The fan at C turns the flow through $\theta_{max}$:

$$
\theta_{max}=\nu_C-\nu(M=1)=\nu_C .
$$

3. Follow the last $C^-$ leaving C. It carries

$$
R^-_C=\nu_C+\theta_C=\theta_{max}+\theta_{max}=2\theta_{max}.
$$

4. That line reaches the centreline at D, the first point of the uniform exit flow, where $\theta_D=0$ and $\nu_D=\nu(M_e)$ (BC 3):

$$
R^-_D=\nu_D+\theta_D=\nu(M_e).
$$

5. Same line, same invariant, $R^-_C=R^-_D$:

$$
2\theta_{max}=\nu(M_e)
\quad\Longrightarrow\quad
\boxed{\theta_{max}=\frac{\nu(M_e)}{2}}
$$

For $M_e=2.4$: $\nu(2.4)=36.7465^\circ$, so $\theta_{max}=18.373^\circ$ (the slides round this to $18.375^\circ$).

> [!tip] Why half?
> The corner fan supplies only **half** the expansion: it raises $\nu$ from $0$ to $\theta_{max}$ and turns the wall flow up by $\theta_{max}$. The fan then reflects off the centreline as $C^+$ waves. Crossing those waves expands the flow by another $\theta_{max}$ while turning it back to $\theta=0$.
>
> The designed wall absorbs each reflected wave as it arrives, so it turns back from $\theta_{max}$ to $0$. Along the wall $\nu+\theta$ stays at $2\theta_{max}=36.747^\circ$: the flow keeps accelerating as the wall straightens.

**The design recipe** (supplementary note p. 11):

1. $\theta_{max}=\nu(M_e)/2$.
2. Choose the number of characteristics and their angles in the fan, from a **small** $\delta$ up to $\theta_{max}$. $\delta=0$ would give a line bouncing back and forth across the throat, which is useless.
3. In the fan $\nu=\theta$, because $R^+=0$ from the sonic throat. So each corner line carries $R^-=2\theta$.
4. Apply the unit process to all the points downstream.
5. Work left to right and compute the coordinates: interior points by §10, centreline points by BC 3, designed wall points by BC 2.

---

## 14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)

**Set-up** (slide 11). Design a nozzle for $M_e=2.4$ using four characteristics a to d from the throat corner 0 at $(0,1)$, with $\theta_{0a}=0.375^\circ$. Find points 1 to 14. Lengths are scaled by the throat half-height $r_a=1$ (slide 21).

**Step 1: the fan lines** (slides 13–15). Equal steps from $0.375^\circ$ to $\theta_{max}$:

| Line | $\theta=\nu$ | $R^-=2\theta$ | $M$ | $\mu$ | $\theta+\mu$ | $\theta-\mu$ |
|---|---:|---:|---:|---:|---:|---:|
| 0a | 0.375 | 0.750 | 1.0418 | 73.708 | 74.083 | −73.333 |
| 0b | 6.374 | 12.749 | 1.3074 | 49.894 | 56.268 | −43.519 |
| 0c | 12.374 | 24.748 | 1.5159 | 41.275 | 53.649 | −28.901 |
| 0d | 18.373 | 36.747 | 1.7192 | 35.568 | 53.941 | −17.194 |

All angles are in degrees. $R^+$ is "N/A" at the corner, since no $C^+$ arrives there.

**Step 2: the invariants** (slides 16–18). Fill in the invariants line by line before anything else:

- each $C^-$ keeps its corner value: points 2 and 6 have $R^-=12.75$; points 3, 7 and 10 have $24.75$; points 4, 8, 11 and 13 have $36.75$;
- each centreline point turns $R^-$ into an equal $R^+$ (BC 3), which then runs up its $C^+$: 1–5 carry $0.75$, 6–9 carry $12.75$, 10–12 carry $24.75$, 13–14 carry $36.75$;
- the wall points 5, 9, 12 and 14 are cancelling, so no $C^-$ leaves them ("N/A").

**Step 3: the states** (slide 19). $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$, then $M$ and $\mu$. Wall points copy the state of the point below them.

**Step 4: the coordinates** (slide 20). Three typical points:

- **Point 1** (BC 3, from 0a): $\theta_1=0$, $\nu_1=0.750^\circ$, $M_1=1.0671$, $\mu_1=69.570^\circ$. Then $\alpha=\tfrac12(-73.333-69.570)=-71.451^\circ$ and $\tan\alpha=-2.9803$, so $x_1=0-1/(-2.9803)=0.3355$.
- **Point 2** (interior; A = 1, B = 0b): $\theta_2=\tfrac12(12.749-0.750)=5.999^\circ$, $\nu_2=6.749^\circ$, $M_2=1.3210$, $\mu_2=49.200^\circ$. Then $\alpha_{12}=\tfrac12(69.570+55.199)=62.385^\circ$ and $\alpha_{0b,2}=\tfrac12(-43.519-43.201)=-43.360^\circ$. The formula gives $(0.5747,\ 0.4573)$.
- **Point 5** (BC 2; A = 4, previous wall point 0): $\theta_5=\theta_4=17.998^\circ$ and $M_5=M_4=1.7320$. Then $\alpha_{45}=(\theta+\mu)_4=53.263^\circ$ and $\alpha_{05}=\tfrac12(18.373+17.998)=18.186^\circ$, giving $(1.2947,\ 1.4253)$.

**The completed table** (computed here; slide 20 values in the last column):

| Pt | Type | $R^+$ | $R^-$ | $\theta$ | $\nu$ | $M$ | $\mu$ | $x$ | $y$ | slide $(x,y)$ |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 1 | centre | 0.750 | 0.750 | 0 | 0.750 | 1.0671 | 69.570 | 0.3355 | 0 | 0.335, 0 |
| 2 | interior | 0.750 | 12.749 | 5.999 | 6.749 | 1.3210 | 49.200 | 0.5747 | 0.4573 | 0.574, 0.458 |
| 3 | interior | 0.750 | 24.748 | 11.999 | 12.749 | 1.5286 | 40.858 | 0.6917 | 0.6184 | 0.691, 0.619 |
| 4 | interior | 0.750 | 36.747 | 17.998 | 18.748 | 1.7320 | 35.265 | 0.7936 | 0.7539 | 0.793, 0.754 |
| 5 | wall | 0.750 | N/A | 17.998 | 18.748 | 1.7320 | 35.265 | 1.2947 | 1.4253 | 1.293, 1.425 |
| 6 | centre | 12.749 | 12.749 | 0 | 12.749 | 1.5286 | 40.858 | 1.0820 | 0 | 1.082, 0 |
| 7 | interior | 12.749 | 24.748 | 5.999 | 18.748 | 1.7320 | 35.265 | 1.3635 | 0.2452 | 1.363, 0.245 |
| 8 | interior | 12.749 | 36.747 | 11.999 | 24.748 | 1.9413 | 31.006 | 1.6248 | 0.4816 | 1.625, 0.482 |
| 9 | wall | 12.749 | N/A | 11.999 | 24.748 | 1.9413 | 31.006 | 3.1775 | 1.9298 | 3.177, 1.93 |
| 10 | centre | 24.748 | 24.748 | 0 | 24.748 | 1.9413 | 31.006 | 1.7858 | 0 | 1.786, 0 |
| 11 | interior | 24.748 | 36.747 | 5.999 | 30.747 | 2.1622 | 27.548 | 2.2074 | 0.2663 | 2.207, 0.266 |
| 12 | wall | 24.748 | N/A | 5.999 | 30.747 | 2.1622 | 27.548 | 5.1989 | 2.2499 | 5.199, 2.25 |
| 13 | centre | 36.747 | 36.747 | 0 | 36.747 | 2.4000 | 24.624 | 2.8323 | 0 | 2.832, 0 |
| 14 | wall | 36.747 | N/A | 0 | 36.747 | 2.4000 | 24.624 | **8.0691** | **2.4003** | **8.069, 2.4** |

> [!check] Reproducing the slides
> Every point agrees with slide 20 to within $0.002$. The slides round $\nu(2.4)$ to $36.75^\circ$ and $M$ to three decimals before taking $\mu$. Repeating the calculation with $M$ rounded the same way gives point 14 at exactly $(8.069,\ 2.400)$.

**Reading the result.** The wall is the polyline 0–5–9–12–14. Its segment slopes are $18.19^\circ$, $15.00^\circ$, $9.00^\circ$ and $3.00^\circ$, falling back to $0$. At 13 the centreline reaches $M_e=2.4$, and the triangle 13–14–centreline is the uniform region.

> [!check] Mass conservation checks the whole calculation
> The exit flow is uniform at $M_e$ and the throat flow is uniform at $M=1$, so the exit half-height must equal the 1D area ratio:
>
> $$\frac{y_e}{r_a}=\frac{A_e}{A^*}(2.4)=2.4031 .$$
>
> MoC gives $2.4003$ with four lines, $0.1\,\%$ low. With more characteristics it converges (first angle $\theta_{max}/n$):
>
> | $n$ | 4 | 10 | 20 | 50 | 120 | 300 |
> |---|---:|---:|---:|---:|---:|---:|
> | $x_e/r_a$ | 7.897 | 8.025 | 8.062 | 8.080 | 8.085 | 8.087 |
> | $y_e/r_a$ | 2.328 | 2.377 | 2.392 | 2.400 | 2.402 | 2.403 |
>
> **The first angle matters.** With four lines starting at $\theta_{max}/4=4.59^\circ$ instead of $0.375^\circ$, the exit drops to $2.328$. A small $\delta$ keeps the first line close to the sonic throat. Use the $y_e$ check to validate the coursework code.

**Refined design** (slide 21; supplementary note Fig. 10). With 20 characteristics the wall becomes a smooth curve. The centreline Mach number rises from 1 to 2.4 over the first $x/r_a\approx2.84$, the kernel, and stays at 2.4 after that (panel 3, lower plot). As slide 21 puts it, 1D theory gives $y_e/r_a=A_e/A^*=2.4031$ *"but it gives no clue about $x_e/r_a=8.069$ revealed by MoC"*.

> [!example] Your turn: $M_e=2.0$ (suggested; answer computed here)
> $\nu(2)=26.380^\circ$, so $\theta_{max}=13.190^\circ$. With four lines at $0.375$, $4.647$, $8.918$ and $13.190^\circ$, the corner invariants are $R^-=0.750$, $9.293$, $17.837$ and $26.380^\circ$.
>
> The results are $M_1=1.0671$ at $x_1=0.3355$, and the uniform region starts at 13, $x=1.905$. The exit is at $(x_e,y_e)=(4.815,\ 1.681)$, against $A_e/A^*=1.6875$. A lower design Mach number gives a much shorter nozzle.

---

## 15. The generic MoC example (Lecture 3.4)

![[at_moc_generic_example.png|900]]

**Set-up** (slide 2). A channel of half-height 1 carries supersonic flow $M_0$ along its centreline. At $(0,1)$ the upper wall turns up by $\theta_w$ and stays straight. The Prandtl–Meyer fan at 0 is represented by two characteristics: "a", the leading wave at the upstream state, and "b", the trailing wave at $\theta_w$. Find $\nu$ and $\theta$ at points 1 to 6 in terms of $\nu_a$ and $\theta_w$.

**What is known beforehand** (slide 3): $\theta=0$ at 0a and on the centreline (1, 4); $\theta=\theta_w$ at 0b and on the wall (3, 6); $\nu_{0a}=\nu_a$.

**Steps** (slides 4–11, one fact at a time):

1. Across the fan, $\Delta\theta=\theta_w=\nu_b-\nu_a$, so $\nu_b=\nu_a+\theta_w$.
2. Corner invariants: $R^-_{0a}=\nu_a+0=\nu_a$ and $R^-_{0b}=(\nu_a+\theta_w)+\theta_w=\nu_a+2\theta_w$.
3. Along the $C^-$ lines: $R^-_1=\nu_a$, and $R^-_2=R^-_4=\nu_a+2\theta_w$.
4. Centreline points, from $\nu=R^--\theta$ and $R^+=\nu-\theta$: point 1 has $\nu_1=\nu_a$, $R^+_1=\nu_a$; point 4 has $\nu_4=\nu_a+2\theta_w$, $R^+_4=\nu_a+2\theta_w$.
5. Along the $C^+$ lines 1–2–3 and 4–5–6: $R^+_2=R^+_3=\nu_a$, and $R^+_5=R^+_6=\nu_a+2\theta_w$.
6. Point 2: $\nu_2=\tfrac12(\nu_a+\nu_a+2\theta_w)=\nu_a+\theta_w$ and $\theta_2=\tfrac12(\nu_a+2\theta_w-\nu_a)=\theta_w$.
7. Wall points, from $\nu=R^++\theta$: point 3 has $\nu_3=\nu_a+\theta_w$, $R^-_3=\nu_a+2\theta_w$; point 6 has $\nu_6=\nu_a+3\theta_w$, $R^-_6=\nu_a+4\theta_w$.
8. Point 5, if it existed: $R^-_5=R^-_3=\nu_a+2\theta_w$, so $\theta_5=0$ and $\nu_5=\nu_a+2\theta_w$.

**"Do you see a problem? What happens to point 3?"** (slides 12–14). The $C^+$ arriving at 3 comes from point 2, where $\theta_2=\theta_w$. The wall at 3 is also at $\theta_w$. By BC 1, a reflection needs $\theta_A\neq\theta_W$, so **nothing reflects at 3**. Delete $R^-_3$ and the whole of point 5. The $C^+$ from 4 runs straight to 6.

> [!tip] The physical reason
> With two lines, wave "a" is only the **head** of the fan: the flow does not change across it, because the whole turn $\theta_w$ is lumped between a and b. Its reflection, the $C^+$ 1–2–3, is the head of the reflected fan and still carries no change, so there is nothing to reflect at 3. The reflected fan's **tail** (4–6) does carry the change. It meets the wall at 6, where the incoming flow has $\theta_4=0\neq\theta_w$, and it reflects there: $R^-_6=R^+_4+2\theta_w=\nu_a+4\theta_w$ (BC 1).
>
> The data at 6 are unchanged by removing 5, because states never depend on geometry (§10). The **coordinates** of 6 do change: without 5 the line 4–6 has no kink (slide 14).

**The inverse problem** (slide 15). $M_4=2.2$ and $M_6=2.4$ are measured. Find $M_0$ and $\theta_w$.

1. From the table: $\nu_4=\nu_a+2\theta_w$ and $\nu_6=\nu_a+3\theta_w$.
2. IFT: $\nu_4=\nu(2.2)=31.7325^\circ$ and $\nu_6=\nu(2.4)=36.7465^\circ$.
3. Subtract: $\theta_w=\nu_6-\nu_4=36.7465-31.7325=5.0140^\circ$.
4. Back-substitute: $\nu_a=31.7325-2(5.0140)=21.7044^\circ$.
5. Invert $\nu$: $M_0=1.8340$.

$$
\boxed{M_0=1.8340\ (\nu_a=21.7044^\circ),\qquad\theta_w=5.0140^\circ}
$$

> [!check] Against the slide
> Slide 15 gives $M_0=1.8340$ ($\nu_a=21.7045^\circ$) and $\theta_w=5.0140^\circ$ ✓. The last digit of $\nu_a$ is rounding.
>
> The figure locates every point with the unit process. Point 3 is a cancelling wall point at $(3.415,\ 1.300)$ and point 6 is a prescribed-wall point at $(4.779,\ 1.419)$. These coordinates are computed here, not on the slides.

---

## 16. Axisymmetric nozzles (supplementary note appendix)

*Not on the slides.* In an $x$–$r$ system the mass flow through an annulus is $\dot m=\rho u\,2\pi r\,\Delta n$. The changing radius adds a term $\frac1r\frac{\partial r}{\partial s}=\frac{\sin\theta}{r}$ to the mass equation. As a result the invariants are **no longer constant** along the characteristics:

$$
\frac{\partial R^\pm}{\partial\eta}=\frac{\sin\mu\,\sin\theta}{r},
$$

where $\eta$ is distance along the characteristic. The states and the coordinates must then be marched together, with an explicit Euler step or a predictor–corrector using the averaged angles of §10. For large $r$ the term vanishes and the planar method returns.

---

## 17. Problem-solving workflow

1. **Draw the net.** Number the points. Mark which lines are $C^+$ (up-and-right for flow to the right) and which are $C^-$.
2. **Fill in the invariants.** Each line keeps its value. At the centreline $R^+=R^-$. A cancelling wall sends nothing back. A prescribed wall sends $R^-_W=R^+_A+2\theta_W$ (top) or $R^+_W=R^-_B-2\theta_W$ (bottom).
3. **States**: $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$. Wall and centreline points use their known $\theta$.
4. $M$ from $\nu$ (IFT, interpolating), then $\mu=\sin^{-1}(1/M)$; then the $\theta\pm\mu$ columns.
5. **Coordinates last**, left to right:
   - interior: averaged $\alpha$, then the $x_P$ formula;
   - centreline: $x_P=x_B-y_B/\tan\alpha_{BP}$;
   - designed wall: $\alpha_{AW}=(\theta+\mu)_A$ and $\alpha_{BW}=\tfrac12(\theta_B+\theta_W)$.
6. **Check**: the exit height against $A_e/A^*$, and the corner angle against $\nu(M_e)/2$.

> [!info] What the exam gives you
> The official `Aerothermodynamics Formula Sheet.pdf` already lists $R^\pm=\nu\mp\theta$ and the intersection formulae for $\alpha_{AP}$, $\alpha_{BP}$, $x_P$ and $y_P$ ([[SESA3029 Formula Sheet#What the exam formula sheet gives you|formula sheet]]). What you must bring is the **procedure**: which invariant runs along which line, the three boundary conditions, and $\theta_{max}=\nu(M_e)/2$. The IFT has a $\nu$ column, so you can invert $\nu\to M$ by interpolation.

---

## Transcript slips (L3-1)

> [!warning] Slips and garbled passages in `Lecture 3-1.txt`
> | Line | Said | Correct |
> |---|---|---|
> | l. 51 | *"beta is just simply an angle of the velocity vector"* | $\theta$, the flow inclination |
> | l. 79 | *"partial N by partial N is 1 over delta N times partial delta N by partial L"* | $\partial\theta/\partial n=\frac{1}{\Delta n}\,\partial\Delta n/\partial l$ |
> | ll. 105–113 | the mass-balance bracket expansion with $\mathrm dA/A$ *"in lecture 2.4"* (after guessing 2.3 and 2.1) | **Lecture 2.6** ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#The lecture's route: a control volume with side walls\|W04 §1]]). Lecture 2.4 supplied $\mathrm du/u=\tan\mu\,\mathrm d\nu$, used at l. 253 |
> | l. 119 | *"partial beta by partial N"* | $\partial\theta/\partial n$ |
> | l. 200 | *"partial beta by partial M"* | $\partial\theta/\partial n$ |
> | l. 229 | *"multiplied by this tiny angle, delta V"* | $\Delta\theta$; $\Delta v$ is the velocity it produces |
> | l. 252 | *"tangent mu … is 1 divided by m squared minus 1"* | $\tan\mu=1/\sqrt{M^2-1}$ (slide 8 is correct) |
> | l. 253 | *"Pantelmeyer function"* | Prandtl–Meyer (Whisper) |
> | ll. 264–279 | the substitution garbled; the lecturer went back a slide | $(M^2-1)\tan\mu=\sqrt{M^2-1}=1/\tan\mu$, then multiply by $\tan\mu$ ([[#6. Rewriting in angles with the Prandtl–Meyer function (3.1 slide 8)\|§6]]) |
> | l. 303 | *"partial nu by theta by partial L"* | $\partial(\nu+\theta)/\partial l$ |
> | ll. 338–343 | *"mu over theta doesn't change … mu minus theta is preserved"* | $\nu-\theta$ (nu, not mu) is constant along $C^+$ |
> | l. 361 | *"C plus line, which is with the slope of tangent mu"* | **Not a slip; clarification only.** $\tan\mu$ is correct as the slope **relative to the streamline** ($\Delta n/\Delta l$). Relative to $x$ the line is inclined at $\theta+\mu$ |
> | l. 362 | *"along C minus theta is constant"* | $\nu+\theta$ is constant along $C^-$ |
> | l. 363 | garbled sentence | $R^+$ and $R^-$ are called the Riemann invariants |
> | l. 367 | *"R plus minus K plus"* | $R^+=-K^+$ and $R^-=K^-$ (Anderson) |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- Earlier this module: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5, the Prandtl–Meyer function]] · [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] (Mach waves)
- New concepts: [[Method of Characteristics]] · [[Riemann Invariants]] · [[Homentropic Flow]] · [[Minimum-Length Nozzle]]
- Related concepts: [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]] · [[Expansion Fan]] · [[Isentropic Nozzle Flow]] · [[Supersonic Wind Tunnel]]
- Maths: [[Eigenvalues and Eigenvectors]] · [[Characteristic Equation and Eigenvalues]]
- Worked sheet: [[SESA3029 Example Sheet 2 - Solutions]] (Q1–Q3)
- Formulae: [[SESA3029 Formula Sheet#Method of characteristics (Lectures 3.1–3.4)|Formula sheet: MoC]]

## Sources

- `Lecture3-1.pdf`: 3.1 Method of Characteristics, Theory (Part A), 12 slides. Lectured Fri 16 Oct.
- `Lecture3-2.pdf`: 3.2 Theory (Part B), 12 slides: eigenvalues, zones, unit process, the slide 9 example. Not yet lectured.
- `Lecture3-3.pdf`: 3.3 MoC Boundary Conditions & Minimum-length Nozzle Design, 21 slides, with the full $M_e=2.4$ table. Not yet lectured.
- `Lecture3-4.pdf`: 3.4 Generic MoC Example, 15 slides. Not yet lectured.
- `Supplementary Note for MoC.pdf`: 12-page note. Derivation in $s$–$n$ coordinates, the eigen-decomposition, the unit process, walls, the minimum-length nozzle, and an axisymmetric appendix. It cites Anderson (2004) and Liepmann & Roshko (1957).
- `Lecture 3-1.txt`: the Fri 16 Oct recording of 3.1 (372 lines).
- Anderson, *Modern Compressible Flow*, Ch. 11; *Fundamentals of Aerodynamics*, §13.3.
- Figures: `generate_aerothermo_w05_figures.py`. Six geometry and data figures; the unit-process code reproduces the slide answers. Derivations are native Obsidian LaTeX.

## Self-study tasks

> [!todo] How to use this list
> - Tasks citing `L3-1` were set or worked in the Fri 16 Oct lecture. The lecture set no formal homework.
> - Tasks marked **slide-set** come from the 3.2–3.4 decks, which have not been lectured yet.
> - The rest are *suggested, not lecturer-set*.
>
> Deadlines: **Test 2 closes Sun 25 Oct** (L3-1, ll. 3–5). The **MoC coursework** brief is due out about 23 Oct and is due at the end of week 7 (ll. 6–11; see [[#Announcements and deadlines|the date check]]).

### Lecturer-set or lecturer-prompted

- [ ] **(L3-1, l. 114)** *"You can find that one in your own time later"*: find the earlier bracket-expansion mass balance and compare it with the streamtube version. It is in Lecture 2.6, not 2.4. → [[#3. Mass conservation (3.1 slide 4)|§3]]
- [ ] **(L3-1, ll. 170–184)** Show that $(\partial p/\partial\rho)_s=a^2$ from $p=C\rho^\gamma$. → [[#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|§4]]
- [ ] **Test 2 on Blackboard**, open Mon 19 to Sun 25 Oct (L3-1, ll. 3–5).

### Derivations

- [ ] Derive the streamtube geometry relation $\partial\theta/\partial n=\frac{1}{\Delta n}\partial\Delta n/\partial l$ (L3-1, ll. 56–80). → [[#2. The curved streamtube and its geometry (3.1 slide 3)|§2]]
- [ ] Derive $(M^2-1)\frac1u\partial u/\partial l=\partial\theta/\partial n$ from mass, $l$-momentum and homentropy (L3-1, ll. 86–204). → [[#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|§4]]
- [ ] Derive the irrotationality condition $\partial\theta/\partial l-\frac1u\partial u/\partial n=0$ (L3-1, ll. 212–239). → [[#5. Zero vorticity (3.1 slide 7)|§5]]
- [ ] Convert to Eq. 1 and Eq. 2 in $\nu$ and $\theta$ (L3-1, ll. 249–293). → [[#6. Rewriting in angles with the Prandtl–Meyer function (3.1 slide 8)|§6]]
- [ ] Add and subtract, then use the directional derivative to get $R^\pm$ (L3-1, ll. 297–357). → [[#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|§7]]
- [ ] **Slide-set (3.2 slides 2–3):** the eigenvalue route, then [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]]. → [[#8. The eigenvalue route (3.2 slides 2–4)|§8]]
- [ ] **Slide-set (3.2 slides 7–8):** derive $\nu_P$, $\theta_P$ and the $x_P$, $y_P$ formulas. → [[#10. The unit process (3.2 slides 7–9)|§10]]
- [ ] **Slide-set (3.3 slides 5–7):** derive the three boundary conditions and their coordinate rules. → [[#11. Boundary conditions (3.3 slides 4–7)|§11]]
- [ ] **Slide-set (3.3 slide 10):** derive $\theta_{max}=\nu(M_e)/2$. → [[#13. The minimum-length nozzle (3.3 slide 10)|§13]]

### Calculations

- [ ] **Slide-set (3.2 slide 9):** find $M_3$, $\theta_3$ and $(x_3,y_3)$. Answer: $1.7039$, $8.9367^\circ$, $(1.3591,\ 0.2814)$. → [[#Worked example (3.2 slide 9)|§10]]
- [ ] **Slide-set (3.3 slides 11–20):** fill in the template for points 1–14 of the $M_e=2.4$ nozzle. Point 14 is at $(8.069,\ 2.400)$. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] **Slide-set (3.4 slides 2–15):** the symbolic table, the point-3 problem, and $M_0$, $\theta_w$ from $M_4$ and $M_6$. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] *(Suggested)* The $M_e=2.0$ nozzle with four lines. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14, "Your turn"]]
- [ ] Redo [[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]] and [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|Q3]] in the $R^\pm$ notation.
- [ ] *(Suggested, coursework preparation)* Program the unit process, as the supplementary note recommends for more than about six lines. Validate it with point 14 and with $y_e/r_a\to A_e/A^*$. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]

### Concepts

- [ ] Explain the new meaning of $\theta$ (inclination, not deflection) (L3-1, ll. 37–55). → [[#1. Why a two-dimensional method (3.1 slide 2)|§1]]
- [ ] Explain why the flow must be homentropic **and** irrotational, and why MoC fails for $M<1$. → [[#8. The eigenvalue route (3.2 slides 2–4)|§8]]
- [ ] Show that a Prandtl–Meyer fan is a simple region with $R^+$ uniform. → [[#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|§7]]
- [ ] Distinguish non-simple, simple and uniform regions, and prescribed from designed walls. → [[#12. Nozzles with a straightening section (3.3 slides 8–9)|§12]]
- [ ] Explain why 3.4's point 3 does not reflect, and why 6's state survives while its position changes. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
