---
title: "SESA3029 W05a - Method of Characteristics"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 3: Nozzles and the Method of Characteristics"
order: 5
tags: [sesa3029, compressible-flow, method-of-characteristics, riemann-invariants, homentropic, prandtl-meyer, eigenvalues, unit-process]
aliases: ["SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design", "SESA3029 Week 5", "SESA3029 Lecture 3.1", "SESA3029 Lecture 3.2", "MoC (SESA3029)"]
date: 2026-10-19
status: lectured
coverage: "Lectures 3.1–3.2 lectured Fri 16 and Mon 19 Oct (transcripts): MoC theory, the eigenvalue route, zones of dependence and the unit process"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[Prandtl-Meyer Function]]", "[[Mach Waves and Mach Angle]]"]
next_topics: ["[[SESA3029 W05b - Minimum-Length Nozzle Design]]"]
key_concepts: ["[[Method of Characteristics]]", "[[Riemann Invariants]]", "[[Homentropic Flow]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt", "02 - Sources/Lectures/Lecture 3-2.txt"]
---

# SESA3029 W05a - Method of Characteristics

> [!note] This note holds §§1–10 (Lectures 3.1–3.2). Boundary conditions, nozzle design, the 3.4 example, the axisymmetric note and the workflow (§§11–17) continue in [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]].

> [!abstract] Summary
> **Steady, homentropic, irrotational, two-dimensional supersonic flow** reduces to two statements along the Mach lines:
>
> $$R^+=\nu-\theta=\text{const along }C^+\ (\text{inclined at }\theta+\mu),\qquad R^-=\nu+\theta=\text{const along }C^-\ (\text{inclined at }\theta-\mu).$$
>
> Here $\theta$ is the **flow inclination** to the $x$-axis (no longer a deflection), $\nu$ the Prandtl–Meyer function and $\mu$ the Mach angle.
>
> - **3.1** derives this from a curved streamtube: mass, $l$-momentum, homentropy and zero vorticity give two PDEs in $u$ and $\theta$. Swapping $u$ for $\nu$ and adding/subtracting turns them into the two **compatibility conditions**. $R^\pm$ are the **Riemann invariants**.
> - **3.2** gets the same result by diagonalising a $2\times2$ matrix (eigenvalues $\pm\tan\mu$), then builds the **unit process**: two known points give a third, $\nu_P=\tfrac12(R^+_A+R^-_B)$, $\theta_P=\tfrac12(R^-_B-R^+_A)$, located with averaged slopes.
> - **3.3–3.4** (boundary conditions, the minimum-length nozzle, the generic example and the MoC coursework) continue in [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]].

> [!summary]- Exam use: quick path
> - **Use it when:** a 2-D supersonic flow has non-uniform inclination and you know the state at two neighbouring points.
> - **Assumptions:** steady, **planar**, homentropic, irrotational, $M>1$; $\theta$ is the flow inclination to $x$; IFT values are $\gamma=1.4$ only.
> - **Method:** 1. Tabulate $R^+=\nu-\theta$ and $R^-=\nu+\theta$ at A (below) and B (above). 2. $\nu_P=\tfrac12(R^+_A+R^-_B)$, $\theta_P=\tfrac12(R^-_B-R^+_A)$. 3. $M_P$ and $\mu_P$ from $\nu_P$. 4. Averaged slopes $\alpha_{AP}=\tfrac12[(\theta+\mu)_A+(\theta+\mu)_P]$, $\alpha_{BP}=\tfrac12[(\theta-\mu)_B+(\theta-\mu)_P]$. 5. Intersect for $x_P$, $y_P$, then recompute $R^\pm$ at P as a check.
> - **Common mistakes:** swapping the families (the $C^+$ from the point **below** carries $R^+$); using only the start-point slope instead of the average.
> - **Practise:** [[#Worked example (3.2 slide 9)]] · [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]]

## Key concepts

- New: [[Method of Characteristics]] · [[Riemann Invariants]] · [[Homentropic Flow]]
- From W03: [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]] · [[Expansion Fan]]
- From W04: [[Isentropic Nozzle Flow]] (SESA2022) and the area–velocity relation, which reappears here in streamtube form
- Maths: [[Eigenvalues and Eigenvectors]] (MATH1054) · [[Characteristic Equation and Eigenvalues]] (SESA2027)
- Continues in [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]]: [[Minimum-Length Nozzle]]

> [!info] Where this was lectured
> **Lecture 3.1 was lectured on Fri 16 Oct** (`Lecture 3-1.txt`, Prof. Jae-Wook Kim, 372 lines). 2.6 had announced MoC for Thursday, but Thursday 15 Oct was spent on 2.7 instead (L2-7, ll. 192–203). The lecture covered the whole 3.1 deck:
> - admin: Test 2 and the MoC coursework (ll. 3–12, see below);
> - why a 2D method, and the new meaning of $\theta$ (ll. 13–55);
> - streamtube geometry (ll. 56–85), mass (ll. 86–123), momentum with homentropy (ll. 124–204), zero vorticity (ll. 205–241);
> - the switch to $\nu$, the two angle equations (ll. 242–293), adding/subtracting (ll. 294–303);
> - the directional-derivative argument and the Riemann invariants (ll. 304–368). It ended with *"next week, I'm going to show you how to actually use that one"* (l. 370).
>
> **Lecture 3.2 was lectured on Mon 19 Oct** (`Lecture 3-2.txt`, 481 lines, ll. 468–481 are only "bye-bye"). It covered the whole 3.2 deck:
> - admin: Test 2 and the coursework deadline (ll. 1–12);
> - the eigenvalue route (ll. 13–184), §8;
> - Mach waves, the zone of silence and the zones of dependence and influence (ll. 185–246), §9;
> - the unit process, why the lines bend, and the averaged slopes (ll. 247–356), §10;
> - the slide 9 example worked live with the class (ll. 357–459). The coordinates of point 3 were left as homework (l. 456). It ended with *"on Thursday … boundary conditions"* (ll. 461–466).
>
> Lectures 3.3 (Thu 22 Oct) and 3.4 (Fri 23 Oct) are written up in [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]].

## Announcements and deadlines

> [!important] Announcements (L3-1, ll. 3–12)
> - **Blackboard Test 2** opens on the morning of **Mon 19 Oct** and stays open until **Sunday 25 Oct, midnight** (ll. 3–5).
> - **MoC coursework:** the brief will be announced *"towards the end of next week"*, i.e. by about Fri 23 Oct (l. 6). It is due *"by end of week seven"*. Week 6 is a reading week, *"and then after that, you have one more week"* (ll. 8–11).
> - Date check: the Week 1 module guide said **15 Nov**. Counting W04 as the week of 12 Oct, the end of week 7 is about **Fri 6 Nov**. The two do not match. L3-2 pointed to 6 Nov (next callout), but **L3-4 gave 15 Nov**, the guide's date ([[SESA3029 W05b - Minimum-Length Nozzle Design#Announcements and deadlines|W05b, announcements]]).

> [!important] Announcements (L3-2, ll. 1–12)
> - **Test 2 is open**: two attempts, and you can look back at the questions and answers afterwards. It closes **Sunday midnight (25 Oct)** (L3-2, ll. 2–8).
> - **MoC coursework, 10 % of the module mark**: the brief is to be announced this week, and it is due at the *"end of week seven, which is two weeks as of Friday this week"* (L3-2, ll. 9–12). Two weeks from Fri 23 Oct is Fri 6 Nov. ~~This settles the date in favour of 6 Nov.~~ **Superseded by L3-4: due 15 Nov** (the full brief is in [[SESA3029 W05b - Minimum-Length Nozzle Design#Announcements and deadlines|W05b]]).

---

## The topic in one physical picture

Think of supersonic flow as a mesh of **Mach lines**. Each line carries one number from upstream and never changes it.

1. Through every point pass two Mach lines, one at $+\mu$ to the local flow ($C^+$, the left-running line) and one at $-\mu$ ($C^-$, the right-running line). Information travels only along them; nothing travels upstream.
2. A $C^+$ line carries $\nu-\theta$ unchanged and a $C^-$ line carries $\nu+\theta$ unchanged. Where two lines cross, the two numbers fix both $\nu$ (hence $M$) and $\theta$. **Solving the flow is bookkeeping**: no PDE has to be integrated.
3. Two known points therefore give a third, the **unit process**, and the solution marches downstream point by point. What happens where the lines reach walls and the centreline, and how that designs a nozzle, is [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]].
4. All of this needs $M>1$. Only then do real Mach lines exist to march along; for $M<1$ every point talks to every other.

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
> exactly the W03 result. A region where one invariant is the same everywhere is called a **simple flow region** ([[SESA3029 W05b - Minimum-Length Nozzle Design#12. Nozzles with a straightening section (3.3 slides 8–9)|W05b §12]]).

---

## 8. The eigenvalue route (3.2 slides 2–4)

Lecture 3.2 re-derives the same result by linear algebra (supplementary note §2; L3-2, ll. 13–184). It also shows why the method needs $M>1$.

**Why bother, when adding and subtracting worked?** The lecturer's answer (ll. 16–19, 179–184): Friday's add-and-subtract *"sort of happened to be the right one"*, *"rather kind of by chance"*. With more complex equations you cannot guess the right combination. The eigenvector route finds it systematically, and it is *"more mathematically general"*. The problem it solves (ll. 21–36): Eq. 1 is "about" $\nu$ but contains $\partial\theta/\partial n$, and Eq. 2 the other way round, so neither can be solved alone. The two are *"tangled"*, and the eigenvectors *"untangle"* them.

**Matrix form.** Write Eqs. 1 and 2 with $\hat Q=[\nu,\ \theta]^T$ (ll. 39–50; a hat marks a vector and an underline a matrix, l. 49):

$$
\frac{\partial\hat Q}{\partial l}+\underline A\,\frac{\partial\hat Q}{\partial n}=\hat 0,
\qquad
\underline A=\begin{bmatrix}0&-\tan\mu\\-\tan\mu&0\end{bmatrix}.
$$

**Eigenvalues** (ll. 55–67).

$$
\det(\underline A-\lambda\underline I)=\begin{vmatrix}-\lambda&-\tan\mu\\-\tan\mu&-\lambda\end{vmatrix}=\lambda^2-\tan^2\mu=0 .
$$

So

$$
\lambda_1=+\tan\mu,\qquad\lambda_2=-\tan\mu .
$$

A $2\times2$ matrix has two eigenvalues, and a $3\times3$ up to three (ll. 56–59).

**Eigenvectors**, from $(\underline A-\lambda\underline I)\hat v=\hat 0$ (ll. 68–94). The lecturer chose $x_1=\tfrac12$, $y_1=-\tfrac12$ and $x_2=y_2=\tfrac12$:

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

$\underline E$ contains no $\mu$, so it is a **constant** matrix and passes through the derivatives (ll. 147–148). Define

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

These are (A) and (B) of §7: *"we came to the same conclusions"* (l. 182).

> [!warning] Premultiply by the inverse, on the left (ll. 115–146)
> The lecturer first said *"multiply E … on the left side of each term"* (l. 117), then corrected it to $\underline E^{-1}$ (l. 130). Two points to keep straight:
> - matrix products do not commute, so $\underline E^{-1}$ must go on the **left** of every term (*"you need to be very careful"*, ll. 118–119);
> - the matrix after the premultiplication is $\underline\Lambda$, not $\underline A$, because $\underline E^{-1}\underline A=\underline\Lambda\,\underline E^{-1}$. A student asked exactly this, and the answer was *"Lambda"* (ll. 156–166).

> [!tip] What the eigenvalues mean
> - The eigenvalues **are** the characteristic slopes $\Delta n/\Delta l=\pm\tan\mu$ relative to the streamline.
> - The eigenvectors are just "take the difference" and "take the sum" of $\nu$ and $\theta$.
> - Real, distinct eigenvalues make the system **hyperbolic**, which needs $M>1$. For $M<1$, $\mu=\sin^{-1}(1/M)$ does not exist. The system is then elliptic, every point influences every other, and marching fails. That is why MoC is a supersonic method.
> - The supplementary note warns that eigenvectors are defined only up to a scale factor, so a computer package may scale them differently. Any scaling with $\underline E\,\underline E^{-1}=\underline I$ works. Practise on [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]].

---

## 9. Zones of dependence and influence (3.2 slides 5–6)

![[at_moc_unit_process.png|900]]

**The lines and what they carry** (slide 4; L3-2, ll. 185–202). $C^\pm$ are the Mach waves, measured at $\pm\mu$ from the velocity vector. If nothing crosses a line, its invariant is the same *"infinitely"* far along it. Where lines cross, $\nu$ and $\theta$ change, but each line's own invariant is still conserved. This is the basis of the method.

**Recap of the Mach cone** (slide 5; ll. 204–224). A source moving at $U$ emits sound that spreads at $a$. After $3\Delta t$ the front has radius $3a\Delta t$ and the source has moved $3U\Delta t$. The envelope makes the angle

$$
\sin\mu=\frac{3a\,\Delta t}{3U\,\Delta t}=\frac{1}{M}
\quad\Longrightarrow\quad
\mu=\sin^{-1}\frac1M .
$$

**Zones** (slide 6, panel 1 of the figure; ll. 232–246). The two characteristics through a point P divide the plane:

- **zone of influence**: the wedge **downstream** between the $C^+$ and $C^-$ leaving P. P can affect only events there;
- **zone of dependence**: the wedge **upstream** between the $C^+$ and $C^-$ arriving at P. The state at P depends only on events there. *"Nothing in here or there do anything for P"* (l. 246).

This is the Mach-cone idea from W02 applied to every point of the flow. The lecturer started from the listener (ll. 232–239). Ahead of the cone, a supersonic source heading towards you is *"absolute silence"* until the cone sweeps over you. That region is the **zone of silence**, and the inside of the cone is the zone of influence.

![[at_moc_supersonic_source.png|900]]

> [!tip] The reversed Taylor Swift song (ll. 215–224), and what else you would hear
> The lecturer's aside: a supersonic speaker playing a song passes you, and *"you are going to hear a Taylor Swift song in reverse order"*, because the latest pulse reaches you first.
>
> That is right for part of the song. The arrival time of a pulse emitted at $t_e$ is $t_a=t_e+r(t_e)/a$, where $r$ is its distance to you. While the source closes on you along your line of sight faster than $a$, a later pulse arrives **earlier**. Those pulses are heard backwards.
>
> The order flips at the emission point E, where that closing speed equals $a$. That is where the line from the source to you makes $\cos^{-1}(1/M)=90^\circ-\mu$ with the flight path. E's pulse arrives first, and that is the boom.
>
> After the boom, $t_a(t_e)$ has two branches (panel 2). So you hear the earlier part of the song **backwards and the later part forwards, at the same time**. For $M=2$ at miss distance $d$, the boom arrives $0.866\,d/a$ after the source passes overhead, which matches the cone geometry: $d/\tan30^\circ$ divided by $U=2a$. A source flying straight at you closes faster than $a$ throughout its approach, so that case is reversed for the whole approach.

---

## 10. The unit process (3.2 slides 7–9)

**Flow state** (slide 7; L3-2, ll. 263–277). Let A and B be known points, with A **below** (its $C^+$ reaches P) and B **above** (its $C^-$ reaches P). The invariants carry over unchanged:

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

Then $M_P$ comes from $\nu_P$ (IFT), and $\mu_P=\sin^{-1}(1/M_P)$. The solution has been **marched downstream**: *"simple as that"* (l. 277).

**Two numbers fix everything** (ll. 249–261, 278–287). The IFT row found from $\nu_P$ gives $M_P$, and with it $p/p_0$, $\rho/\rho_0$ and $T/T_0$. $\theta_P$ then splits the velocity into $u=V\cos\theta$ and $v=V\sin\theta$. The lecturer's illustration was $\nu_P\approx8.4^\circ\Rightarrow M\approx1.38$ (ll. 283–284).

> [!check] The l. 284 table look-up
> $\nu(1.38)=8.413^\circ$, and $\nu=8.4^\circ$ inverts to $M=1.3795$ ✓.

**Why the characteristics bend** (ll. 288–318). The lecturer asked the class *"why will they turn?"* The answer: the direction of a Mach line is set by $\mu=\sin^{-1}(1/M)$, and $M$ at P differs from $M$ at A and B. So the $C^\pm$ lines leaving P are slightly *"misaligned"* with those arriving, and each line turns a little at every crossing. The slides draw them straight, but your coursework net will not be straight (ll. 288–297; L3-3, ll. 10–12).

![[at_moc_mach_angle_throat_angle.png|900]]

In the slide 9 example (panel 1), $\mu$ falls from $45.58^\circ$ at point 2 to $35.94^\circ$ at point 3. So $\theta+\mu$ on the $C^+$ falls from $45.58^\circ$ to $44.87^\circ$, even though $\theta$ rises by $8.94^\circ$. That is why the location step averages the two ends.

> [!tip] In planar flow the states do not need the geometry
> $\nu_P$ and $\theta_P$ depend only on $R^\pm$, never on $x$ or $y$. You can fill in the whole flow-state table first and find the coordinates afterwards. Lecture 3.4 does the entire example symbolically without a single coordinate. This decoupling fails for axisymmetric nozzles (§16).

**Location** (slide 8; supplementary note eqs. 14–16; L3-2, ll. 320–351). The characteristics are curved, so use the **average** of their slopes at the two ends:

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

This is the derivation the lecturer left for you: *"you can check in your own time, and you arrive at the same equations here"* (l. 349).

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

> [!example] How it went in the lecture (L3-2, ll. 357–459)
> The class worked steps 1–4 aloud with printed IFTs:
> - $\nu_1=14.8604^\circ$ (ll. 389–398) and $\nu_2=8.9870^\circ$ (ll. 402–409, garbled in the transcript as "8.098" and "8.870" before the right value);
> - $R^+_2=\nu_2-\theta_2=8.9870^\circ$ (l. 410) and $R^-_1=\nu_1+\theta_1=26.8604^\circ$ (ll. 422–423);
> - $\mu_2=45.5847^\circ$ (l. 421) and $\mu_1=38.6821^\circ$ (l. 427; $38.6822^\circ$ to four decimals);
> - $\nu_3=17.9237^\circ$ (l. 435), then $M_3$ *"about 1.7 something"* from the nearest table row (ll. 441–449). The IFT has $\nu(1.70)=17.81^\circ$ and $\nu(1.71)=18.10^\circ$, and interpolating gives the slide's $1.7039$.
>
> $\theta_3$ was never finished aloud (l. 436, see the slips). **The coordinates were set as homework**: *"So this is your whole mark. See if the coordinate of 0.3 is this value … search this one and confirm it"* (ll. 453–459). "Whole mark" is Whisper's rendering of "homework", and "0.3" of "point 3". Steps 5–8 above are the solution.

> [!warning] Set the calculator to degrees (ll. 411–421)
> The first answer for $\mu_2=\sin^{-1}(1/1.4)$ from the class was $0.795$. That is the angle in **radians** ($0.7956$ rad $=45.58^\circ$). Every MoC angle, including the IFT's $\nu$ column, is in degrees, so one radian value poisons the whole table.

**Calculation procedure** (slides 10–11; L3-2, ll. 351–355: *"You keep doing it, and then you can fill the space with lots of points"*).

1. On a starting line where the flow is known, compute $\nu$, $\theta$ and $\mu$ at several points, then $R^+$ and $R^-$.
2. Compute $\theta+\mu$ and $\theta-\mu$ at each point.
3. March downstream to the crossing points and get $\nu$ and $\theta$ there.
4. Get $M$ from $\nu$, then $\mu=\sin^{-1}(1/M)$.
5. Get the angles $\alpha$, then the coordinates of the new points.
6. Repeat, applying the wall and symmetry **boundary conditions** where the lines reach a boundary (§11).

> [!info] Putting it all together
> The complete hand-calculation procedure, with the boundary conditions and the final checks, is the problem-solving workflow in [[SESA3029 W05b - Minimum-Length Nozzle Design#17. Problem-solving workflow|W05b §17]].

---

## Transcript slips

Whisper renders some words consistently wrongly in these recordings: "mark" for Mach, "I-centric"/"isentrific" for isentropic, "oxine" for arcsine, "Pranthal/frontal/planter/quantum mayor" for Prandtl–Meyer (and in L3-4 *"quantum wave function"*, l. 68, and *"plant and mayor fat"* for the fan, l. 375), "menstrual characteristics" for method of characteristics, and "0.N" for "point N". These are not listed below.

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

> [!warning] Slips and garbled passages in `Lecture 3-2.txt` (Mon 19 Oct)
> | Line | Said | Correct |
> |---|---|---|
> | l. 42 | *"0, minus 1, mu, and minus 1, mu, and 0"* | $\underline A$ has $0$ on the diagonal and $-\tan\mu$ off it (garbled) |
> | l. 64 | *"diagonal terms minus half-diagonal terms"* | product of the diagonal terms minus product of the **off**-diagonal terms: $\lambda^2-\tan^2\mu$ |
> | l. 86 | *"… minus tangent mu times y1 equals tangent mu"* | $-\tan\mu\,y_1=\tan\mu\,x_1$, so $y_1=-x_1$ |
> | l. 117 | *"multiply E, matrix, on the left side of each term"* | $\underline E^{-1}$ on the left; corrected at l. 130 ([[#8. The eigenvalue route (3.2 slides 2–4)\|§8]]) |
> | l. 151 | *"C inverse E inverse E inverse Q"* | garbled: $\partial(\underline E^{-1}\hat Q)/\partial l+\underline\Lambda\,\partial(\underline E^{-1}\hat Q)/\partial n=\hat 0$ |
> | ll. 216–224 | the speaker's song is heard *"in reverse order"* | true only for pulses emitted before the critical point E; later ones arrive in order, at the same time ([[#9. Zones of dependence and influence (3.2 slides 5–6)\|§9]]) |
> | l. 244 | *"this is zone of dependence, it's a zone of influence, something like that"* | upstream wedge: zone of **dependence** of P; downstream wedge: its zone of **influence** |
> | ll. 263–266 | the lines *"collide at point B"*, *"at point B, the R-plus value"* | at point **P** |
> | l. 270 | *"R-plus value should be maintained, which is nu plus theta"* | $R^+=\nu-\theta$; $\nu+\theta$ is $R^-$ (said correctly at l. 272) |
> | l. 275 | *"theta P is R-minus, take away R-minus, take away R-minus, divided by 2"* | $\theta_P=\tfrac12(R^-_B-R^+_A)$ |
> | l. 361 | *"point A, Mach number is 1.6"* | point **1** |
> | l. 424 | *"And mu two, could you calculate arcsine of 1 over 1.6"* | that is $\mu_1=38.6822^\circ$ ($\mu_2$ was the $1.4$ value at l. 421) |
> | l. 429 | *"half of r plus 2 plus r minus 1 divided by 2"* | halve **once**: $\nu_3=\tfrac12(R^+_2+R^-_1)=17.9237^\circ$ (the number at l. 435 is right) |
> | l. 436 | *"theta 3, which is r1 minus minus r2 plus divided by 2, which is 26.8604"* | $\theta_3=\tfrac12(26.8604-8.9870)=8.9367^\circ$. $26.8604^\circ$ is $R^-_1$, read out before the subtraction |

## Terminology and alternative names

This note uses the course's own words. Textbooks (Anderson in particular), other universities and CFD software often use other names for the same ideas. Use the course term in the coursework and the exam, and treat the others as search terms.

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| compatibility conditions | compatibility relations; compatibility equations; characteristic (compatibility) equations | L3.1 slide 12 and L3.2 slide 4 (*"Compatibility conditions"*); Supplementary Note pp. 3, 5; L3-1, l. 361 | "Characteristic equation" also means the eigenvalue polynomial $\det(\underline A-\lambda\underline I)=0$ of §8, so avoid it for $R^\pm$ |
| Riemann invariants $R^+=\nu-\theta$ (along $C^+$), $R^-=\nu+\theta$ (along $C^-$) | $K^+$, $K^-$ (Anderson), with $K^+=-R^+=\theta-\nu$ and $K^-=R^-=\theta+\nu$; characteristic invariants | L3.1 slide 12, which also gives Anderson's $R^+=-K^+$, $R^-=K^-$; Supplementary Note p. 5 | Same physics, different sign of $K^+$. ES2 was first written in Anderson's form |
| characteristics $C^+$, $C^-$ (characteristic lines) | left-running and right-running characteristics; Mach lines; Mach waves | L3.1 slides 11–12; Supplementary Note p. 2 ("left-running" $C^+$, "right-running" $C^-$) | Both names are in the course material; $C^\pm$ is what the slides and the template use |
| zone of influence; zone of dependence | domain of influence; domain of dependence; range of influence | L3.2 slide 6 (zones); Supplementary Note p. 3 (domains) | |
| homentropic flow | uniform-entropy (isentropic everywhere) flow | L3.1 slide 2; Supplementary Note p. 1 | Stronger than isentropic: the same entropy on every streamline |
| flow angle $\theta$; flow inclination angle | flow direction; streamline angle | L3.1 slide 3 ("relative to the $x$-axis"); L3-1, l. 53 (*"flow inclination angle rather than flow deflection angle"*); L3-4, ll. 43–52; Supplementary Note p. 1 | Measured from the $x$-axis, not a deflection as in W02–W03 |
| Prandtl–Meyer (PM) function $\nu$ | Prandtl–Meyer angle | L3.4 slide 2 ("PM function"); Supplementary Note p. 5 ("Prandtl-Meyer function") and pp. 2, 11 ("Prandtl-Meyer angle") | Both are used in the course material |
| unit process | interior-point unit process; MoC step | L3.2 slides 7–10 ("Repeat Unit Process Downstream"); Supplementary Note §3 | |
| simple flow region | simple-wave region; simple region | L3.3 slides 8 and 10; Supplementary Note p. 9 | Introduced in W05b §12; a Prandtl–Meyer fan fed by uniform flow is one (§7) |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]
- Next: [[SESA3029 W05b - Minimum-Length Nozzle Design]] (boundary conditions, the minimum-length nozzle, the 3.4 generic example and the MoC coursework)
- Earlier this module: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5, the Prandtl–Meyer function]] · [[SESA3029 W02 - Oblique Shock Relations and Mach Waves]] (Mach waves)
- New concepts: [[Method of Characteristics]] · [[Riemann Invariants]] · [[Homentropic Flow]]
- Related concepts: [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]] · [[Expansion Fan]] · [[Isentropic Nozzle Flow]]
- Maths: [[Eigenvalues and Eigenvectors]] · [[Characteristic Equation and Eigenvalues]]
- Worked sheet: [[SESA3029 Example Sheet 2 - Solutions]] (Q1–Q2; Q3 also needs the boundary conditions of W05b)
- Formulae: [[SESA3029 Formula Sheet#Method of characteristics (Lectures 3.1–3.4)|Formula sheet: MoC]]
- **Builds on / connects to** (cross-module):
  - [[SESA3043 2.1 - Complex Functions and Conformal Mapping|SESA3043 2.1]] and [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli#Why the derivative is u − iv (derivation)|SESA3043 1.3 §3]]: steady 2-D irrotational flow is a pair of first-order PDEs in both modules. Subsonically (incompressible in SESA3043) the pair is the Cauchy–Riemann equations: the system is elliptic, has no real characteristics, and its general solution is any analytic $\Phi(z)$. Supersonically (here) the eigenvalues $\pm\tan\mu$ of [[#8. The eigenvalue route (3.2 slides 2–4)|§8]] are real, the system is hyperbolic, and the compatibility conditions $\mathrm d(\nu\mp\theta)=0$ along $C^\pm$ take the place of Cauchy–Riemann. The two modules ask the same question and get opposite answers.
  - [[SESA3043 1.2b - Potential-Flow Review|SESA3043 1.2b]]: Laplace's equation, the incompressible limit, where every point influences every other (contrast the zones of dependence of [[#9. Zones of dependence and influence (3.2 slides 5–6)|§9]]).

## Sources

- `Lecture3-1.pdf`: 3.1 Method of Characteristics, Theory (Part A), 12 slides. Lectured Fri 16 Oct.
- `Lecture3-2.pdf`: 3.2 Theory (Part B), 12 slides: eigenvalues, zones, unit process, the slide 9 example. Lectured Mon 19 Oct.
- `Supplementary Note for MoC.pdf`: 12-page note. Derivation in $s$–$n$ coordinates, the eigen-decomposition, the unit process, walls, the minimum-length nozzle, and an axisymmetric appendix. It cites Anderson (2004) and Liepmann & Roshko (1957).
- `Lecture 3-1.txt`: the Fri 16 Oct recording of 3.1 (372 lines).
- `Lecture 3-2.txt`: the Mon 19 Oct recording of 3.2 (481 lines; the last 14 are goodbyes).
- Anderson, *Modern Compressible Flow*, Ch. 11; *Fundamentals of Aerodynamics*, §13.3.
- Figures: `generate_aerothermo_w05_figures.py`. Eight geometry and data figures; the unit-process code reproduces the slide answers. `at_moc_supersonic_source.png` and `at_moc_mach_angle_throat_angle.png` were added from the L3-2 and L3-3 recordings. Derivations are native Obsidian LaTeX.

## Self-study tasks

> [!todo] How to use this list
> - Tasks citing `L3-1` or `L3-2` were set or worked in the lectures of Fri 16 and Mon 19 Oct. The formal homework was the point 3 coordinates (L3-2, l. 456), plus two "check in your own time" derivations (L3-1, l. 114; L3-2, l. 349).
> - The rest are *suggested, not lecturer-set*. Tasks on the boundary conditions, nozzle design, the 3.4 example and the coursework are in [[SESA3029 W05b - Minimum-Length Nozzle Design#Self-study tasks|W05b]].
>
> Deadlines: **Test 2 closes Sun 25 Oct, midnight** (L3-1, ll. 3–5; L3-2, ll. 2–8; L3-4, l. 6). The **MoC coursework** (10 %) is due **Sun 15 Nov** (L3-4, ll. 415–418), not the 6 Nov of L3-2 (see [[SESA3029 W05b - Minimum-Length Nozzle Design#Announcements and deadlines|the W05b announcements]]).

### Core

- [ ] **(L3-2, l. 349)** *"You can check in your own time"*: solve the two straight-line equations for $x_P$ and $y_P$ and recover the slide 8 formula. → [[#10. The unit process (3.2 slides 7–9)|§10]]
- [ ] **(L3-2, ll. 453–459) Homework:** confirm that point 3 of the slide 9 example is at $(1.3592,\ 0.2814)$. The class did the flow state; the coordinates were left to you. → [[#Worked example (3.2 slide 9)|§10, steps 5–8]]
- [ ] **Test 2 on Blackboard**, two attempts, closes Sun 25 Oct (L3-1, ll. 3–5; L3-2, ll. 2–8; L3-4, l. 6). → [[SESA3029 Test 2 - Solutions]]
- [ ] Add and subtract, then use the directional derivative to get $R^\pm$ (L3-1, ll. 297–357). → [[#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|§7]]
- [ ] Diagonalise $\underline A$: eigenvalues, eigenvectors, $\underline E^{-1}$, then decouple with $\underline E^{-1}$ on the left (L3-2, ll. 39–182). Then try [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]]. → [[#8. The eigenvalue route (3.2 slides 2–4)|§8]]

### Further practice

#### Lecturer-set or lecturer-prompted

- [ ] **(L3-1, l. 114)** *"You can find that one in your own time later"*: find the earlier bracket-expansion mass balance and compare it with the streamtube version. It is in Lecture 2.6, not 2.4. → [[#3. Mass conservation (3.1 slide 4)|§3]]
- [ ] **(L3-1, ll. 170–184)** Show that $(\partial p/\partial\rho)_s=a^2$ from $p=C\rho^\gamma$. → [[#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|§4]]

#### Derivations

- [ ] Derive the streamtube geometry relation $\partial\theta/\partial n=\frac{1}{\Delta n}\partial\Delta n/\partial l$ (L3-1, ll. 56–80). → [[#2. The curved streamtube and its geometry (3.1 slide 3)|§2]]
- [ ] Derive $(M^2-1)\frac1u\partial u/\partial l=\partial\theta/\partial n$ from mass, $l$-momentum and homentropy (L3-1, ll. 86–204). → [[#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|§4]]
- [ ] Derive the irrotationality condition $\partial\theta/\partial l-\frac1u\partial u/\partial n=0$ (L3-1, ll. 212–239). → [[#5. Zero vorticity (3.1 slide 7)|§5]]
- [ ] Convert to Eq. 1 and Eq. 2 in $\nu$ and $\theta$ (L3-1, ll. 249–293). → [[#6. Rewriting in angles with the Prandtl–Meyer function (3.1 slide 8)|§6]]
- [ ] Derive $\nu_P$ and $\theta_P$ from the two invariants (L3-2, ll. 263–277; L3-3, ll. 13–31). → [[#10. The unit process (3.2 slides 7–9)|§10]]

#### Calculations

- [ ] **(L3-2, ll. 357–459)** Find $M_3$, $\theta_3$ and $(x_3,y_3)$ for the slide 9 example, with the calculator in degrees. Answer: $1.7039$, $8.9367^\circ$, $(1.3591,\ 0.2814)$. → [[#Worked example (3.2 slide 9)|§10]]

#### Concepts

- [ ] Explain the new meaning of $\theta$ (inclination, not deflection) (L3-1, ll. 37–55). → [[#1. Why a two-dimensional method (3.1 slide 2)|§1]]
- [ ] Explain why the flow must be homentropic **and** irrotational, and why MoC fails for $M<1$. → [[#8. The eigenvalue route (3.2 slides 2–4)|§8]]
- [ ] Show that a Prandtl–Meyer fan is a simple flow region with $R^+$ uniform. → [[#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|§7]]
- [ ] **(L3-2, ll. 299–318)** Answer the lecturer's question: *"why will they turn?"* → [[#10. The unit process (3.2 slides 7–9)|§10]]
- [ ] *(Suggested)* Explain what a listener hears from a supersonic speaker, and where the lecture's "reversed song" needs qualifying (L3-2, ll. 215–239). → [[#9. Zones of dependence and influence (3.2 slides 5–6)|§9]]
