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
coverage: "Lectures 3.1–3.4 lectured Fri 16, Mon 19, Thu 22 and Fri 23 Oct (transcripts), plus the MoC coursework brief (L3-4); §16 from the supplementary note"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[Prandtl-Meyer Function]]", "[[Mach Waves and Mach Angle]]"]
next_topics: []
key_concepts: ["[[Method of Characteristics]]", "[[Riemann Invariants]]", "[[Homentropic Flow]]", "[[Minimum-Length Nozzle]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Lecture3-2.pdf", "02 - Sources/Lectures/Lecture3-3.pdf", "02 - Sources/Lectures/Lecture3-4.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt", "02 - Sources/Lectures/Lecture 3-2.txt", "02 - Sources/Lectures/Lecture 3-3.txt", "02 - Sources/Lectures/Lecture 3-4.txt"]
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
> - **3.3** adds the boundary conditions (reflecting wall, cancelling wall, symmetry plane) and designs the **minimum-length nozzle**: $\theta_{max}=\nu(M_e)/2$, so the throat angle alone gives the exit Mach number. For $M_e=2.4$ with four characteristics, $x_e/r_a=8.069$ and $y_e/r_a=2.400$, against the 1D $A_e/A^*=2.4031$.
> - **3.4** (Fri 23 Oct) works a channel symbolically, finds that point 3 cannot reflect, and solves the inverse problem: $M_4=2.2$, $M_6=2.4$ give $\theta_w=5.0140^\circ$ and $M_0=1.8340$. The lesson: *"always think about the results, whether it makes sense or not"* (L3-4, ll. 279–281). The lecture ended with the **MoC coursework brief**: a minimum-length nozzle for $M_e=3.x$ in **CO₂ ($\gamma=1.289$)** with five characteristics, due **15 Nov**.

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
> **Lecture 3.2 was lectured on Mon 19 Oct** (`Lecture 3-2.txt`, 481 lines, ll. 468–481 are only "bye-bye"). It covered the whole 3.2 deck:
> - admin: Test 2 and the coursework deadline (ll. 1–12);
> - the eigenvalue route (ll. 13–184), §8;
> - Mach waves, the zone of silence and the zones of dependence and influence (ll. 185–246), §9;
> - the unit process, why the lines bend, and the averaged slopes (ll. 247–356), §10;
> - the slide 9 example worked live with the class (ll. 357–459). The coordinates of point 3 were left as homework (l. 456). It ended with *"on Thursday … boundary conditions"* (ll. 461–466).
>
> **Lecture 3.3 was lectured on Thu 22 Oct** (`Lecture 3-3.txt`, 303 lines). It covered the whole 3.3 deck: a recap (ll. 7–43), the three boundary conditions (ll. 44–100), §11; the nozzle with a straightening section (ll. 103–143), §12; the minimum-length nozzle (ll. 144–214), §13; and the $M_e=2.4$ table up to slide 21 (ll. 215–301), §14. **The recording stops mid-sentence** at l. 303, *"And coincidentally…"*.
>
> **Lecture 3.4 was lectured on Fri 23 Oct** (`Lecture 3-4.txt`, 425 lines), the last MoC lecture. It covered the whole 3.4 deck:
> - admin: reading week next, Test 2 closes Sunday (ll. 1–6);
> - the symbolic table filled in step by step (ll. 7–200), with an exam hint at ll. 201–203, §15;
> - the "thorn": why point 3 cannot reflect and point 5 does not exist (ll. 206–297), §15;
> - the inverse problem, $M_0$ and $\theta_w$ from $M_4$ and $M_6$ (ll. 298–359), §15;
> - the **MoC coursework brief** on Blackboard (ll. 361–418): see [[#Announcements and deadlines]].
>
> §16 is from the supplementary note and was never on the slides.

## Announcements and deadlines

> [!important] Announcements (L3-1, ll. 3–12)
> - **Blackboard Test 2** opens on the morning of **Mon 19 Oct** and stays open until **Sunday 25 Oct, midnight** (ll. 3–5).
> - **MoC coursework:** the brief will be announced *"towards the end of next week"*, i.e. by about Fri 23 Oct (l. 6). It is due *"by end of week seven"*. Week 6 is a reading week, *"and then after that, you have one more week"* (ll. 8–11).
> - Date check: the Week 1 module guide said **15 Nov**. Counting W04 as the week of 12 Oct, the end of week 7 is about **Fri 6 Nov**. The two do not match. L3-2 pointed to 6 Nov (next callout), but **L3-4 gave 15 Nov**, the guide's date (last callout).

> [!important] Announcements (L3-2, ll. 1–12; L3-3, ll. 3–6)
> - **Test 2 is open**: two attempts, and you can look back at the questions and answers afterwards. It closes **Sunday midnight (25 Oct)** (L3-2, ll. 2–8).
> - **MoC coursework, 10 % of the module mark**: the brief is to be announced this week, and it is due at the *"end of week seven, which is two weeks as of Friday this week"* (L3-2, ll. 9–12). Two weeks from Fri 23 Oct is Fri 6 Nov. ~~This settles the date in favour of 6 Nov.~~ **Superseded by L3-4: due 15 Nov** (next callout).
> - **What the coursework is**: the lecturer called 3.3 *"a very important lecture"* for the coursework and the final exam (L3-3, ll. 3–6). The nozzle-design table of §14 is *"essentially what you are going to do in the coursework"* (l. 132) and *"the table that you're going to work on in the method of characteristics coursework"* (ll. 221–222).

> [!important] The MoC coursework (brief: `04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf`; announced L3-4, ll. 361–425)
> - **Due 23:59, Sun 15 Nov 2026**, on Blackboard. Worth **10 %** of the module. L3-4 gave the date (ll. 415–418); it replaces the 6 Nov of L3-2 and matches the module guide.
> - **Design Mach number $M_{des}=3.x$**, where $x$ is the last digit of your student ID (L3-4, ll. 371–372).
> - **The gas is carbon dioxide at room temperature, $\gamma=1.289$, not air.** The IFT, NST and OSC are all for $\gamma=1.4$, so none of them can be used for your numbers. Every $\nu$, $M$ and $A/A^*$ must come from your own code. The lecture did not mention this; it is only in the brief.
> - **Part A**: program a spreadsheet or Python function giving $\mu$ and $\nu$ for any $M$ and $\gamma$, and verify both against an alternative method.
> - **Part B**: a 2D minimum-length nozzle with **five characteristics** from the corner at $(x,y)=(0,1)$, with angles **equally spaced from $0.125^\circ$ to $\theta_{max}$** (not the $0.375^\circ$ start of §14). Keep **at least four significant figures** throughout. Five lines give **20 points** (L3-4, ll. 392–397): $n(n+3)/2$ for $n$ lines, five of them on the wall (ll. 406–408).
> - **Report**: at most **6 A4 pages** including tables and figures, with no separate title page. Sections and marks:
>
> | Part | Content | Marks |
> |---|---|---:|
> | i | title, name and ID, $M_{des}$; executive summary of 80–100 words for non-technical readers | 5 |
> | ii | the MoC method and how it designs a nozzle, 1–1.5 pages, concise but followable | 15 |
> | iii | $\mu$ and $\nu$ at $M_{des}$ for $\gamma=1.289$, and how the code was verified | 10 |
> | iv | the completed template (one page; by hand or by program) | 25 |
> | v | every computation step for points 1, 2 and the **last wall point** | 20 |
> | vi | plot of the nozzle and characteristics; discussion, comparison with quasi-1D $A/A^*$ for your $\gamma$, limitations (about one page) | 25 |
>
> - **Reading week w/c 26 Oct**, no teaching (L3-4, ll. 4–5, 418, 423): *"make the most of the week for revision and catching up and coursework"* (l. 5).
> - **Test 2 closes on Sunday** (25 Oct) (l. 6). Worked solutions: [[SESA3029 Test 2 - Solutions]].

> [!tip] What carries over from the notes, and what changes with $\gamma$
> Nothing in the procedure of §§10–14 depends on $\gamma$. Only the gas functions do:
>
> $$
> \nu(M)=\sqrt{\frac{\gamma+1}{\gamma-1}}\,\tan^{-1}\sqrt{\frac{\gamma-1}{\gamma+1}\left(M^2-1\right)}-\tan^{-1}\sqrt{M^2-1},
> $$
>
> $$
> \frac{A}{A^*}=\frac{1}{M}\left[\frac{2}{\gamma+1}\left(1+\frac{\gamma-1}{2}M^2\right)\right]^{(\gamma+1)/[2(\gamma-1)]}.
> $$
>
> - $\mu=\sin^{-1}(1/M)$ does **not** depend on $\gamma$. $\nu$ and $A/A^*$ do.
> - **Verifying the code ("an alternative method").** Two independent checks:
>   - Set $\gamma=1.4$ and compare with the IFT (e.g. $\nu(2.4)=36.7465^\circ$, $A/A^*=2.4031$).
>   - Integrate $\mathrm d\nu=\sqrt{M^2-1}\,\mathrm dM/[M(1+\tfrac{\gamma-1}{2}M^2)]$ numerically from $M=1$ and compare with the closed form at your $\gamma$ ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5]]).
> - **Inverting $\nu\to M$** at every point needs a root finder (bisection or Newton), because there is no table for $\gamma=1.289$.
> - **Validate the MoC code** on the lecture case first: $\gamma=1.4$, $M_e=2.4$, four lines from $0.375^\circ$ must give point 14 at $(8.069,\ 2.400)$ (§14). Then switch to your $\gamma$, $M_{des}$, five lines and $0.125^\circ$.
> - **Section vi check**: $y_e/r_a$ should approach $A_e/A^*$ **at $\gamma=1.289$** as lines are added (L3-4, ll. 403–411 encourage more lines).

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

---

## 11. Boundary conditions (3.3 slides 4–7)

![[at_moc_boundary_conditions.png|900]]

A wall point has only **one** characteristic arriving from upstream: a $C^+$ at the top wall, a $C^-$ at the bottom wall. So the interior formulas (two lines, two equations) cannot be used. The wall supplies the missing condition instead: the flow must be tangential to it.

In Anderson's nozzle sketch on slide 4, the wall points are 5, 8 and 12, and the centreline points are 3, 6, 10 and 11 (L3-3, ll. 44–49). The lecturer also added the non-reflecting condition (l. 46).

> [!tip] The rule behind every boundary condition: any two of four (L3-3, ll. 27–36)
> At every point there are four numbers, $R^+$, $R^-$, $\nu$ and $\theta$, linked by two equations: $R^+=\nu-\theta$ and $R^-=\nu+\theta$. *"All you need … is to obtain two of them."* The other two follow:
> - an interior point gets $R^+$ and $R^-$ from its two incoming lines;
> - a wall point gets one invariant from its incoming line and $\theta$ from the wall (l. 55);
> - a centreline point gets one invariant and $\theta=0$.

### BC 1: a prescribed wall reflects (slide 5)

L3-3, ll. 50–64. *"You know the geometry of the wall, so you definitely know the slope"* (l. 53).

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

*"What you can memorise in this case is R minus is R plus plus two times the wall angle"* (ll. 62–63).

If $\theta_A=\theta_W$, then $\nu_W=\nu_A$ and $R^-_W=\nu_A+\theta_A=R^-_A$. The "reflected" line carries the same invariant as the $C^-$ already through A, so **there is no new wave**. A reflection occurs only when $\theta_A\neq\theta_W$.

At a **bottom** wall the roles swap: $\nu_W=R^-_B-\theta_W$, and the reflected $C^+$ carries $R^+_W=R^-_B-2\theta_W$.

The slides give no coordinate formula for BC 1. Intersect the $C^+$ line from A with the known wall curve. $\theta_W$ depends on where the line lands, so iterate if you use averaged slopes. [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]] is a worked case.

### BC 2: a designed wall cancels (slide 6)

L3-3, ll. 65–87. Here the wall angle is **chosen**: set $\theta_W=\theta_A$, so the flow does not turn between A and W. A wave reflects only when the flow has to turn to follow the wall (ll. 65–70). Then

$$
\nu_W=R^+_A+\theta_W=(\nu_A-\theta_A)+\theta_A=\nu_A
\quad\Longrightarrow\quad
M_W=M_A ,
$$

and no wave is reflected. *"In that case you don't consider C minus"*: the wave *"just goes on to the far field forever and doesn't come back"* (ll. 73–74). This is how a nozzle is designed to give uniform exit flow.

**Location**, using the unit-process formula with P replaced by W and B the **previous wall point** (supplementary note eq. 17; ll. 76–87). Neither the position nor the slope of W is known beforehand. There is no B arriving from above, so *"you pick a point behind this one … and take it as a point B"*:

$$
\boxed{\alpha_{AW}=(\theta+\mu)_A,\qquad\alpha_{BW}=\tfrac12(\theta_B+\theta_W)}
$$

- A and W have the same state, so the $C^+$ segment is straight and needs no averaging.
- BW is a piece of wall, which is a streamline. Its slope is the average of the flow angles at its ends.

### BC 3: the symmetry plane is a mirror (slide 7)

L3-3, ll. 88–98. The centreline is *"effectively a wall"* (*"mirror or image effect"*): with no vertical velocity there, it is an **inviscid wall** (ll. 88–93). So BC 3 is BC 1 with $\theta_W=0$ (ll. 93–96). Put $\theta_W=0$ into the bottom-wall form of BC 1 and you get $\nu_P=R^-_B$ and $R^+_P=R^-_P$ at once.

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

The lecturer gave two equivalent ways to place P (ll. 97–98):
- use the **image point** A (B mirrored in the centreline) and the triangle A–B–P;
- or treat the previous centreline point as the "B" of BC 2, a wall point with slope $0$.

Both give $y_P=0$ and the $x_P$ above.

> [!tip] Why the lecturer called this amazing (ll. 99–100)
> Two coupled **nonlinear PDEs**, which are normally impossible to solve, have become *"just adding, subtracting, divide by two"*. The coordinates take a little more work, but the principle is just that.

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

**In the lecture** (L3-3, ll. 103–143, using slide 8's numbering):
- the calculation starts from a few points on a line just past the sonic throat. More points give more resolution (ll. 103–107);
- in the expansion section the wall is specified, $\theta$ is known there, and the waves reflect (ll. 110–115);
- the designed wall points 12 and 13 are made **non-reflecting** (ll. 115–117). The aim is a uniform exit flow (l. 118);
- why it works (ll. 119–131): point 11 is on the centreline, so $\theta_{11}=0$. No line crosses between 11 and 13, so $\theta$, $\nu$ and $M$ are the same along 11–13. The flow there is horizontal and uniform at $M_e$;
- if 12 reflected, a $C^-$ would come back down, cross 11–13 and change the flow there (ll. 126–129).

> [!warning] This $\theta_{max}$ is a wall slope, not a turning limit (L3-3, ll. 133–143)
> The nozzle's $\theta_{max}$ is the **largest wall slope**, reached at the junction of the expansion and straightening sections. After it, the slope decays slowly towards horizontal. It has nothing to do with the oblique-shock $\theta_{max}$ of W02, the largest deflection an attached shock can turn the flow through. *"Don't be confused"* (l. 138). The slope is tied to the exit Mach number (l. 143), as §13 shows.

---

## 13. The minimum-length nozzle (3.3 slide 10)

![[at_moc_min_length_nozzle.png|900]]

To make the nozzle as short as possible, remove the prescribed section entirely. All the expansion then happens in a **centred Prandtl–Meyer fan at a sharp corner C** at the throat, and the wall downstream is designed to cancel every wave. See [[Minimum-Length Nozzle]].

**In the lecture** (L3-3, ll. 144–200). The nozzle length runs from the throat to the exit. A real nozzle should be as short as possible, because extra length means extra weight and bulk (ll. 144–148). So drop the prescribed section and let *"nature"* design the whole wall (ll. 148–153). The wall slope then jumps from about $0$ to $\theta_{max}$ at the throat. *"What do you expect?"* An expansion fan, whose lines are Mach waves and therefore exactly the characteristics (ll. 156–163). Every downstream wall point is made non-reflecting, so straightening starts at once (ll. 164–167).

**Derivation of the corner angle.**

1. The throat is sonic: $M=1$, so $\nu(1)=0$ and $\theta=0$. **Why $\nu(1)=0$** (ll. 176–187): the Prandtl–Meyer function is defined as an integral from $M=1$,

$$
\nu(M)=\int_1^M\frac{\sqrt{M'^2-1}}{1+\frac{\gamma-1}{2}M'^2}\,\frac{\mathrm dM'}{M'} .
$$

At $M=1$ the integral runs from $1$ to $1$, so it is zero. The $M=1$ row of the IFT confirms $\nu=0$.
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

**Reading the exit Mach number off the throat** (L3-3, ll. 204–214). *"The far end and the very first … talk to each other"*: the throat slope and $M_e$ are linked by $\theta_{max}=\nu(M_e)/2$. Show the lecturer a nozzle, let them measure the wall angle at the throat, and they can tell you $M_e$ without a wind tunnel: *"it's what rocket scientists can do"*. Panel 2 of the figure in §10 plots this relation both ways.

> [!example] The lecturer's $M_e=3.2$, both ways (ll. 207–210; computed here)
> **Design.** $\nu(3.2)=53.470^\circ$, so
>
> $$\theta_{max}=\frac{53.470^\circ}{2}=26.735^\circ .$$
>
> **Inverse.** You measure $26.74^\circ$ at the throat corner. Double it:
>
> $$\nu(M_e)=2\times26.74^\circ=53.48^\circ .$$
>
> Invert in the IFT: $M_e=3.20$.
>
> For comparison, a corner of $18.375^\circ$ gives $M_e=2.400$ and $13.19^\circ$ gives $2.000$.

> [!warning] Only for a sharp-corner (minimum-length) nozzle
> In a nozzle with a gradual expansion section, the largest slope $\theta_{max}$ is reached at the junction point E (§12). The flow at E has already been expanded by its own wall turning ($\theta_{max}$) **and** by reflected waves from the centreline, so $\nu_E\ge\theta_{max}$. The last $C^-$ from E reaches the start of the uniform region, so
>
> $$\nu(M_e)=R^-_E=\nu_E+\theta_{max}\ge2\theta_{max}.$$
>
> Hence $\theta_{max}\le\nu(M_e)/2$, with equality only for the minimum-length nozzle. A gradual nozzle's measured maximum slope therefore **underestimates** $M_e$ if you double it. This is a derivation added here; the lecture applied the trick to a nozzle that starts at the throat.

**The design recipe** (supplementary note p. 11):

1. $\theta_{max}=\nu(M_e)/2$.
2. Choose the number of characteristics and their angles in the fan, from a **small** $\delta$ up to $\theta_{max}$. $\delta=0$ would give a line bouncing back and forth across the throat, which is useless.
3. In the fan $\nu=\theta$, because $R^+=0$ from the sonic throat. So each corner line carries $R^-=2\theta$.
4. Apply the unit process to all the points downstream.
5. Work left to right and compute the coordinates: interior points by §10, centreline points by BC 3, designed wall points by BC 2.

---

## 14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)

**Set-up** (slide 11; L3-3, ll. 215–222). Design a nozzle for $M_e=2.4$ using four characteristics a to d from the throat corner 0 at $(0,1)$, with $\theta_{0a}=0.375^\circ$. Find points 1 to 14. Lengths are scaled by the throat half-height $r_a=1$ (slide 21). More fan lines give more points and more resolution, but four lines and 14 points are *"something manageable"* (ll. 219–221).

**The columns** (ll. 226–231): $R^+$, $R^-$, $\theta$ and $\nu$ are the essential four. $M$ comes from $\nu$, $\mu$ from $M$, and $\theta\pm\mu$ are needed only for the slopes that place $x$ and $y$.

**Start from the exit** (ll. 232–239). Point 14 must have $M=2.4$, so $\nu_{14}=\nu(2.4)=36.7465^\circ$, rounded to $36.75^\circ$. Point 13 is the same, since nothing changes between 13 and 14. Halving gives $\theta_{max}=18.375^\circ$, which is $\nu=\theta$ on the last fan line 0d.

**Why $0.375^\circ$** (ll. 240–243). Spread the four lines evenly: $0.375$, $6.375$, $12.375$, $18.375^\circ$, adding $6^\circ$ each time. The first value is chosen *"for numerical convenience"*, so that the steps end exactly on $18.375^\circ$. It also keeps line 0a off $M=1$, where $\mu=90^\circ$ (§13 recipe, step 2).

**Step 1: the fan lines** (slides 13–15; ll. 244–250). Equal steps from $0.375^\circ$ to $\theta_{max}$. The fan lines carry only $R^-=\nu+\theta=2\theta$; $R^+$ is "not applicable" there (ll. 245–247):

| Line | $\theta=\nu$ | $R^-=2\theta$ | $M$ | $\mu$ | $\theta+\mu$ | $\theta-\mu$ |
|---|---:|---:|---:|---:|---:|---:|
| 0a | 0.375 | 0.750 | 1.0418 | 73.708 | 74.083 | −73.333 |
| 0b | 6.374 | 12.749 | 1.3074 | 49.894 | 56.268 | −43.519 |
| 0c | 12.374 | 24.748 | 1.5159 | 41.275 | 53.649 | −28.901 |
| 0d | 18.373 | 36.747 | 1.7192 | 35.568 | 53.941 | −17.194 |

All angles are in degrees. $R^+$ is "N/A" at the corner, since no $C^+$ arrives there.

**Step 2: the invariants** (slides 16–18; ll. 250–275, *"fairly straightforward and mechanical"*, l. 259). Fill in the invariants line by line before anything else:

- each $C^-$ keeps its corner value: points 2 and 6 have $R^-=12.75$; points 3, 7 and 10 have $24.75$; points 4, 8, 11 and 13 have $36.75$;
- each centreline point turns $R^-$ into an equal $R^+$ (BC 3), which then runs up its $C^+$: 1–5 carry $0.75$, 6–9 carry $12.75$, 10–12 carry $24.75$, 13–14 carry $36.75$;
- the wall points 5, 9, 12 and 14 are cancelling, so no $C^-$ leaves them ("N/A").

**Step 3: the states** (slide 19; ll. 275–283). $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$, then $M$ and $\mu$. Wall points copy the state of the point below them: point 5 has the $\theta$ and $\nu$ of point 4 (ll. 277–280).

**Step 4: the coordinates** (slide 20; ll. 285–292). Three typical points:

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

**Reading the result.** The wall is the polyline 0–5–9–12–14, the non-reflecting wall points (ll. 286–287). The lecturer read point 14 as $x=8.069$, $y=2.4$, normalised by the throat half-height (ll. 288–289), so the exit area is 2.4 times the throat area (l. 291). Its segment slopes are $18.19^\circ$, $15.00^\circ$, $9.00^\circ$ and $3.00^\circ$, falling back to $0$. At 13 the centreline reaches $M_e=2.4$, and the triangle 13–14–centreline is the uniform region.

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

**Refined design** (slide 21; supplementary note Fig. 10; ll. 293–301). With 20 characteristics the wall becomes a smooth curve. The centreline Mach number rises from 1 to 2.4 over the first $x/r_a\approx2.84$, the kernel, and stays at 2.4 after that (panel 3, lower plot). As slide 21 puts it, 1D theory gives $y_e/r_a=A_e/A^*=2.4031$ *"but it gives no clue about $x_e/r_a=8.069$ revealed by MoC"*. The lecturer read $2.403$ from the last IFT column, *"very well matched"* with MoC, and stressed that 1D theory *"didn't know what the length of the nozzle should be"* (ll. 297–301).

> [!info] Where the recording stops (l. 303)
> `Lecture 3-3.txt` ends mid-sentence: *"And coincidentally…"*. The rest is not recorded. The most likely point, given the slide, is that $y_e/r_a\approx2.40$ happens to equal the design Mach number $2.4$. That really is a coincidence. For $\gamma=1.4$, $A/A^*=M$ only at $M=2.397$; at $M_e=2$ the ratio is $1.6875$, and at $M_e=3$ it is $4.2346$. So $y_e/r_a=M_e$ is **not** a rule. This reading is an inference, not something the lecturer said.

> [!example] Your turn: $M_e=2.0$ (suggested; answer computed here)
> $\nu(2)=26.380^\circ$, so $\theta_{max}=13.190^\circ$. With four lines at $0.375$, $4.647$, $8.918$ and $13.190^\circ$, the corner invariants are $R^-=0.750$, $9.293$, $17.837$ and $26.380^\circ$.
>
> The results are $M_1=1.0671$ at $x_1=0.3355$, and the uniform region starts at 13, $x=1.905$. The exit is at $(x_e,y_e)=(4.815,\ 1.681)$, against $A_e/A^*=1.6875$. A lower design Mach number gives a much shorter nozzle.

---

## 15. The generic MoC example (Lecture 3.4)

![[at_moc_generic_example.png|900]]

> [!info] Lectured Fri 23 Oct (`Lecture 3-4.txt`)
> 3.4 was given as *"relatively quite simple and quick"* once 3.1–3.3 are digested (L3-4, ll. 1–2). It was originally written ahead from the slides and has now been backfilled with line references. *"Generic as opposed to numerical"*: only symbols, no numbers (ll. 8–10).

**Set-up** (slide 2; L3-4, ll. 11–31). A channel of half-height 1 carries supersonic flow $M_0$ along its centreline. At $(0,1)$ the upper wall turns up by $\theta_w$ and stays straight. The Prandtl–Meyer fan at 0 is represented by two characteristics: "a", the leading wave at the upstream state, and "b", the trailing wave at $\theta_w$. Find $\nu$ and $\theta$ at points 1 to 6 in terms of $\nu_a$ and $\theta_w$.

> [!tip] "The coarsest mesh that you can imagine" (ll. 14–20)
> Two lines for a whole fan is deliberately crude: *"this is not an ideal case, but we can still learn a lot from this simplest case."* More lines give more accuracy, *"which is what you are going to do in the coursework"* (ll. 19–20). The centreline acts *"effectively [as] a wall as well"* (l. 26), as in BC 3.

**What is known beforehand** (slide 3; ll. 34–56): $\theta=0$ at 0a and on the centreline (1, 4); $\theta=\theta_w$ at 0b and on the wall (3, 6); $\nu_{0a}=\nu_a$. No $C^+$ passes through 0a or 0b, so $R^+$ is *"not applicable"* there (ll. 36–37). *"That's the first thing that you can do without doing any calculation"* (l. 56).

**Steps** (slides 4–11, one fact at a time):

1. Across the fan, $\Delta\theta=\theta_w=\nu_b-\nu_a$, so $\nu_b=\nu_a+\theta_w$ (ll. 63–76).
2. Corner invariants: $R^-_{0a}=\nu_a+0=\nu_a$ and $R^-_{0b}=(\nu_a+\theta_w)+\theta_w=\nu_a+2\theta_w$ (ll. 59–61, 77–83).
3. Along the $C^-$ lines: $R^-_1=\nu_a$, and $R^-_2=R^-_4=\nu_a+2\theta_w$ (ll. 86–116; the class answered *"nu A"* at l. 97).
4. Centreline points, from $\nu=R^--\theta$ and $R^+=\nu-\theta$: point 1 has $\nu_1=\nu_a$, $R^+_1=\nu_a$; point 4 has $\nu_4=\nu_a+2\theta_w$, $R^+_4=\nu_a+2\theta_w$ (ll. 120–151).
5. Along the $C^+$ lines 1–2–3 and 4–5–6: $R^+_2=R^+_3=\nu_a$, and $R^+_5=R^+_6=\nu_a+2\theta_w$ (ll. 153–163).
6. Point 2: $\nu_2=\tfrac12(\nu_a+\nu_a+2\theta_w)=\nu_a+\theta_w$ and $\theta_2=\tfrac12(\nu_a+2\theta_w-\nu_a)=\theta_w$ (ll. 164–176).
7. Wall points, from $\nu=R^++\theta$: point 3 has $\nu_3=\nu_a+\theta_w$, $R^-_3=\nu_a+2\theta_w$; point 6 has $\nu_6=\nu_a+3\theta_w$, $R^-_6=\nu_a+4\theta_w$ (ll. 177–180).
8. Point 5, if it existed: $R^-_5=R^-_3=\nu_a+2\theta_w$, so $\theta_5=0$ and $\nu_5=\nu_a+2\theta_w$ (ll. 183–197).

The rule used at every line is the one from L3-3: *"it's your four variables and four equations … if you knew two of them, then you can work out the other two"* (ll. 120–134, 180).

> [!important] Exam hint (ll. 198–203)
> *"If you did it on your own, it would have been done in like 30 seconds, maybe 40 seconds."* And: *"this type of question was one of the questions in the past papers. So try and do it on your own … just in case something similar appears in this year's exam."*

**"Do you see a problem? What happens to point 3?"** (slides 12–14; ll. 206–297). The $C^+$ arriving at 3 comes from point 2, where $\theta_2=\theta_w$. The wall at 3 is also at $\theta_w$. By BC 1, a reflection needs $\theta_A\neq\theta_W$, so **nothing reflects at 3**. Delete $R^-_3$ and the whole of point 5. The $C^+$ from 4 runs straight to 6.

The lecturer's route to the same conclusion (ll. 208–277):

- *"Although you did everything correctly according to the rules … you did it without thinking about the physics"* (ll. 211–214).
- Look at the turning angles: every point has $\theta=0$ or $\theta_w$, *"nothing in between"*, only because there are so few lines (ll. 219–224). The free ones are 2 and 5: $\theta_2=\theta_w$ and $\theta_5=0$ (ll. 229–235).
- At 2 the flow is already parallel to the wall, so *"between point two and three, the flow doesn't turn"* (ll. 238–242). That is the **non-reflecting** condition of L3-3, which the class recalled at ll. 251–260.
- *"The nature says, there is no reflection here. This line doesn't exist"* (ll. 269–270). So $R^-_3$ is not applicable and *"0.5 doesn't exist. That is the correct complete table that you should have produced"* (ll. 273–277).

> [!important] "The most important lesson that you should learn from this lecture" (ll. 279–281)
> *"Please make sure that your calculations, your results comply with the nature. And always think about the results, whether it makes sense or not."* He called the blind version *"one of the very good examples of engineering practices, which you could do just blindedly … routinely, without thinking about the physics"* (ll. 217–218).

**Point 6 survives** (ll. 283–295). Without 5, $R^+_6=R^+_4=\nu_a+2\theta_w$ and $\theta_6=\theta_w$, the same as before: *"fortunately, even though you did something wrong, 0.6 was correct"* (l. 293). He warned that *"those type of fortunate cases don't happen often"* (l. 295).

> [!tip] The physical reason
> With two lines, wave "a" is only the **head** of the fan: the flow does not change across it, because the whole turn $\theta_w$ is lumped between a and b. Its reflection, the $C^+$ 1–2–3, is the head of the reflected fan and still carries no change, so there is nothing to reflect at 3. The reflected fan's **tail** (4–6) does carry the change. It meets the wall at 6, where the incoming flow has $\theta_4=0\neq\theta_w$, and it reflects there: $R^-_6=R^+_4+2\theta_w=\nu_a+4\theta_w$ (BC 1).
>
> The data at 6 are unchanged by removing 5, because states never depend on geometry (§10). The **coordinates** of 6 do change: without 5 the line 4–6 has no kink (slide 14). So the lecturer's *"0.6 was correct"* (l. 293) is true of the flow state, not of the point's position.

**The inverse problem** (slide 15; ll. 298–348). $M_4=2.2$ and $M_6=2.4$ are measured. Find $M_0$ and $\theta_w$. *"You have two conditions given. Therefore, you can work out two variables"* (ll. 303–305).

1. From the table: $\nu_4=\nu_a+2\theta_w$ and $\nu_6=\nu_a+3\theta_w$ (ll. 307–312).
2. IFT: $\nu_4=\nu(2.2)=31.7325^\circ$ and $\nu_6=\nu(2.4)=36.7465^\circ$ (ll. 313–325).
3. Subtract: $\theta_w=\nu_6-\nu_4=36.7465-31.7325=5.0140^\circ$ (ll. 330–333).
4. Back-substitute: $\nu_a=31.7325-2(5.0140)=21.7045^\circ$ with the table values (ll. 336–337); $21.7044^\circ$ from unrounded $\nu$.
5. Invert $\nu$: the IFT rows $1.82$ ($21.3021^\circ$) and $1.84$ ($21.8768^\circ$) bracket it, *"closer to the lower line"* (l. 345):

$$
M_0=1.82+0.02\times\frac{21.7045-21.3021}{21.8768-21.3021}=1.82+0.02\times0.700=1.8340\quad(\text{l. 347: }1.834).
$$

$$
\boxed{M_0=1.8340\ (\nu_a=21.7044^\circ),\qquad\theta_w=5.0140^\circ}
$$

> [!check] Against the slide and the lecture
> Slide 15 and L3-4 (ll. 333–347) give $M_0=1.8340$ ($\nu_a=21.7045^\circ$) and $\theta_w=5.0140^\circ$ ✓. The last digit of $\nu_a$ is rounding.

> [!tip] Why do it symbolically? (ll. 349–358)
> *"The beauty of using this table is … you don't have to recalculate the table all over again"* for a new case. Any other $M_0$ and $\theta_w$ drop straight into the same expressions, and so do measurements, as in the inverse problem: *"the beauty of doing these things using the pure, more pure form as much as possible. And you can use that form again and again."*
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

> [!warning] Slips and garbled passages in `Lecture 3-3.txt` (Thu 22 Oct)
> | Line | Said | Correct |
> |---|---|---|
> | ll. 28–30 | *"R plus is NU minus theta over 2. R minus is NU plus theta over 2. no sorry the other way around"* | $R^+=\nu-\theta$ and $R^-=\nu+\theta$, with **no** factor $\tfrac12$. The halving belongs to the inverse, $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$, as restated correctly at l. 31 |
> | l. 60 | *"R minus is R plus plus plus theta"* | $R^-_W=R^+_A+2\theta_W$ (corrected in the same line) |
> | l. 97 | *"use the a e p triangle to calculate point b"* | use the triangle A–B–P (A the image of B) to find point **P** |
> | l. 257 | *"0.8 is same as 0.11. So 36.75"* | $R^-_8=R^-_4=36.75^\circ$, carried on to $R^-_{11}=R^-_8$ |
> | l. 266 | *"0.789 share the same r plus"* | points 7, 8 and 9 share $R^+=12.75^\circ$ |
> | l. 279 | *"theta and mu are the same as 0.4"* | $\theta$ and $\nu$ (nu) at the cancelling wall point 5 equal those at point 4 |
> | l. 289 | *"normalized by the throat height, 1"* | by the throat **half**-height $r_a=1$ (slide 21) |
> | l. 303 | *"And coincidentally…"* | the recording ends here ([[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)\|§14]]) |

> [!warning] Slips and garbled passages in `Lecture 3-4.txt` (Fri 23 Oct)
> L3-4 is clean: every symbolic entry and every number checks out ($\theta_w=5.014^\circ$, $\nu_a=21.7045^\circ$, $M_0=1.834$; 20 coursework points). Only these need care.
>
> | Line | Said | Correct |
> |---|---|---|
> | l. 171 | *"theta is R minus R minus R plus"* | $\theta=\tfrac12(R^--R^+)$; the halving is said at l. 172 |
> | l. 265 | *"calculated the point bar which intersects with this R plus R line"* | garbled: the reflected $C^-$ from 3 meets the $C^+$ from 4 at **point 5** |
> | l. 268 | *"we calculate 0.6 based on 0.5"* | the **state** at 6 needs only $R^+_4$ and $\theta_w$. Point 5 changed only how 6 was **located** ([[#15. The generic MoC example (Lecture 3.4)\|§15]]) |
> | ll. 416–417 | *"three weeks … 15th of November"* | three weeks from Fri 23 Oct is Fri 13 Nov; the stated date, **Sun 15 Nov**, is the one to use (it matches the module guide) |

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
- `Lecture3-2.pdf`: 3.2 Theory (Part B), 12 slides: eigenvalues, zones, unit process, the slide 9 example. Lectured Mon 19 Oct.
- `Lecture3-3.pdf`: 3.3 MoC Boundary Conditions & Minimum-length Nozzle Design, 21 slides, with the full $M_e=2.4$ table. Lectured Thu 22 Oct.
- `Lecture3-4.pdf`: 3.4 Generic MoC Example, 15 slides. Lectured Fri 23 Oct.
- `Supplementary Note for MoC.pdf`: 12-page note. Derivation in $s$–$n$ coordinates, the eigen-decomposition, the unit process, walls, the minimum-length nozzle, and an axisymmetric appendix. It cites Anderson (2004) and Liepmann & Roshko (1957).
- `Lecture 3-1.txt`: the Fri 16 Oct recording of 3.1 (372 lines).
- `Lecture 3-2.txt`: the Mon 19 Oct recording of 3.2 (481 lines; the last 14 are goodbyes).
- `Lecture 3-3.txt`: the Thu 22 Oct recording of 3.3 (303 lines; cut off mid-sentence at the end of slide 21).
- `Lecture 3-4.txt`: the Fri 23 Oct recording of 3.4 (425 lines): the generic example (ll. 7–359) and the MoC coursework brief (ll. 361–425).
- `04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf`: the one-page coursework brief (due 23:59, Sun 15 Nov; $\gamma=1.289$).
- Anderson, *Modern Compressible Flow*, Ch. 11; *Fundamentals of Aerodynamics*, §13.3.
- Figures: `generate_aerothermo_w05_figures.py`. Eight geometry and data figures; the unit-process code reproduces the slide answers. `at_moc_supersonic_source.png` and `at_moc_mach_angle_throat_angle.png` were added from the L3-2 and L3-3 recordings. Derivations are native Obsidian LaTeX.

## Self-study tasks

> [!todo] How to use this list
> - Tasks citing `L3-1` to `L3-4` were set or worked in the lectures of Fri 16, Mon 19, Thu 22 and Fri 23 Oct. The formal homework was the point 3 coordinates (L3-2, l. 456), plus two "check in your own time" derivations. L3-4 added *"try and do it on your own"* for the symbolic table (ll. 201–203) and the coursework.
> - The rest are *suggested, not lecturer-set*.
>
> Deadlines: **Test 2 closes Sun 25 Oct, midnight** (L3-1, ll. 3–5; L3-2, ll. 2–8; L3-4, l. 6). The **MoC coursework** (10 %) is due **Sun 15 Nov** (L3-4, ll. 415–418), not the 6 Nov of L3-2 (see [[#Announcements and deadlines|the announcements]]).

### Lecturer-set or lecturer-prompted

- [ ] **(L3-1, l. 114)** *"You can find that one in your own time later"*: find the earlier bracket-expansion mass balance and compare it with the streamtube version. It is in Lecture 2.6, not 2.4. → [[#3. Mass conservation (3.1 slide 4)|§3]]
- [ ] **(L3-1, ll. 170–184)** Show that $(\partial p/\partial\rho)_s=a^2$ from $p=C\rho^\gamma$. → [[#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|§4]]
- [ ] **(L3-2, l. 349)** *"You can check in your own time"*: solve the two straight-line equations for $x_P$ and $y_P$ and recover the slide 8 formula. → [[#10. The unit process (3.2 slides 7–9)|§10]]
- [ ] **(L3-2, ll. 453–459) Homework:** confirm that point 3 of the slide 9 example is at $(1.3592,\ 0.2814)$. The class did the flow state; the coordinates were left to you. → [[#Worked example (3.2 slide 9)|§10, steps 5–8]]
- [ ] **(L3-3, ll. 132, 221–222)** Fill in the $M_e=2.4$ template yourself. This is the coursework procedure. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] **(L3-4, ll. 198–203)** Fill in the symbolic 3.4 table on your own in under a minute: *"this type of question was one of the questions in the past papers"*. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] **(L3-4, ll. 206–281)** Spot the non-physical entry before being told: why point 3 cannot reflect and point 5 does not exist. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] **(L3-4, ll. 298–348)** Recover $\theta_w=5.014^\circ$ and $M_0=1.834$ from $M_4=2.2$ and $M_6=2.4$. → [[#15. The generic MoC example (Lecture 3.4)|§15, the inverse problem]]
- [ ] **Test 2 on Blackboard**, two attempts, closes Sun 25 Oct (L3-1, ll. 3–5; L3-2, ll. 2–8; L3-4, l. 6). → [[SESA3029 Test 2 - Solutions]]
- [ ] **MoC coursework** (brief in `04 - Labs & Coursework/MoC Coursework/`; L3-4, ll. 361–418): minimum-length nozzle for $M_{des}=3.x$ ($x$ = last digit of your student ID), **CO₂, $\gamma=1.289$**, five characteristics from $0.125^\circ$, 20 points, four significant figures, sections i–vi, at most six A4 pages. **Due 23:59, Sun 15 Nov.** → [[#Announcements and deadlines]] and [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] **(Brief, part A)** Write and verify a $\mu$, $\nu$ (and $A/A^*$) function for any $\gamma$, with a root finder for $\nu\to M$. → [[#Announcements and deadlines|the γ tip box]]
- [ ] **(L3-4, ll. 400–411)** *Optional:* automate the table (Excel or Python) and add more lines to see the wall converge. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]

### Derivations

- [ ] Derive the streamtube geometry relation $\partial\theta/\partial n=\frac{1}{\Delta n}\partial\Delta n/\partial l$ (L3-1, ll. 56–80). → [[#2. The curved streamtube and its geometry (3.1 slide 3)|§2]]
- [ ] Derive $(M^2-1)\frac1u\partial u/\partial l=\partial\theta/\partial n$ from mass, $l$-momentum and homentropy (L3-1, ll. 86–204). → [[#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|§4]]
- [ ] Derive the irrotationality condition $\partial\theta/\partial l-\frac1u\partial u/\partial n=0$ (L3-1, ll. 212–239). → [[#5. Zero vorticity (3.1 slide 7)|§5]]
- [ ] Convert to Eq. 1 and Eq. 2 in $\nu$ and $\theta$ (L3-1, ll. 249–293). → [[#6. Rewriting in angles with the Prandtl–Meyer function (3.1 slide 8)|§6]]
- [ ] Add and subtract, then use the directional derivative to get $R^\pm$ (L3-1, ll. 297–357). → [[#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|§7]]
- [ ] Diagonalise $\underline A$: eigenvalues, eigenvectors, $\underline E^{-1}$, then decouple with $\underline E^{-1}$ on the left (L3-2, ll. 39–182). Then try [[SESA3029 Example Sheet 2 - Solutions#Q1. Eigenvalues and left eigenvectors|ES2 Q1]]. → [[#8. The eigenvalue route (3.2 slides 2–4)|§8]]
- [ ] Derive $\nu_P$ and $\theta_P$ from the two invariants (L3-2, ll. 263–277; L3-3, ll. 13–31). → [[#10. The unit process (3.2 slides 7–9)|§10]]
- [ ] Derive the three boundary conditions and their coordinate rules (L3-3, ll. 50–98). → [[#11. Boundary conditions (3.3 slides 4–7)|§11]]
- [ ] Derive $\theta_{max}=\nu(M_e)/2$, including why $\nu(1)=0$ (L3-3, ll. 168–200). → [[#13. The minimum-length nozzle (3.3 slide 10)|§13]]
- [ ] *(Suggested)* Show that a gradual-expansion nozzle has $\theta_{max}\le\nu(M_e)/2$. → [[#13. The minimum-length nozzle (3.3 slide 10)|§13, the warning]]

### Calculations

- [ ] **(L3-2, ll. 357–459)** Find $M_3$, $\theta_3$ and $(x_3,y_3)$ for the slide 9 example, with the calculator in degrees. Answer: $1.7039$, $8.9367^\circ$, $(1.3591,\ 0.2814)$. → [[#Worked example (3.2 slide 9)|§10]]
- [ ] **(L3-3, ll. 215–292)** Fill in the template for points 1–14 of the $M_e=2.4$ nozzle. Point 14 is at $(8.069,\ 2.400)$. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] **(L3-3, ll. 206–214)** The lecturer's trick: find $\theta_{max}$ for $M_e=3.2$, then recover $M_e$ from a measured $26.74^\circ$. Answer: $26.735^\circ$, $M_e=3.20$. → [[#13. The minimum-length nozzle (3.3 slide 10)|§13]]
- [ ] *(Suggested, in the spirit of L3-4, ll. 349–358)* Reuse the symbolic table for $M_4=2.0$, $M_6=2.2$. Answer: $\theta_w=5.353^\circ$, $\nu_a=15.674^\circ$, $M_0=1.628$. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] *(Suggested)* The $M_e=2.0$ nozzle with four lines. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14, "Your turn"]]
- [ ] Redo [[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]] and [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|Q3]] in the $R^\pm$ notation.
- [ ] *(Suggested, coursework preparation)* Program the unit process, as the supplementary note recommends for more than about six lines. Validate it with point 14 and with $y_e/r_a\to A_e/A^*$. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]

### Concepts

- [ ] Explain the new meaning of $\theta$ (inclination, not deflection) (L3-1, ll. 37–55). → [[#1. Why a two-dimensional method (3.1 slide 2)|§1]]
- [ ] Explain why the flow must be homentropic **and** irrotational, and why MoC fails for $M<1$. → [[#8. The eigenvalue route (3.2 slides 2–4)|§8]]
- [ ] Show that a Prandtl–Meyer fan is a simple region with $R^+$ uniform. → [[#7. Compatibility conditions and Riemann invariants (3.1 slides 9–12)|§7]]
- [ ] Distinguish non-simple, simple and uniform regions, and prescribed from designed walls. Explain why non-reflecting points 12 and 13 make 11–13 uniform (L3-3, ll. 103–131). → [[#12. Nozzles with a straightening section (3.3 slides 8–9)|§12]]
- [ ] **(L3-2, ll. 299–318)** Answer the lecturer's question: *"why will they turn?"* → [[#10. The unit process (3.2 slides 7–9)|§10]]
- [ ] Tell the nozzle's $\theta_{max}$ (wall slope) apart from the oblique-shock $\theta_{max}$ (L3-3, ll. 137–139). → [[#12. Nozzles with a straightening section (3.3 slides 8–9)|§12]]
- [ ] *(Suggested)* Explain what a listener hears from a supersonic speaker, and where the lecture's "reversed song" needs qualifying (L3-2, ll. 215–239). → [[#9. Zones of dependence and influence (3.2 slides 5–6)|§9]]
- [ ] Explain why 3.4's point 3 does not reflect, and why 6's state survives while its position changes (L3-4, ll. 238–295). → [[#15. The generic MoC example (Lecture 3.4)|§15]]
