---
title: "SESA3029 W05b - Minimum-Length Nozzle Design"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 3: Nozzles and the Method of Characteristics"
order: 6
tags: [sesa3029, compressible-flow, method-of-characteristics, boundary-conditions, nozzle-design, minimum-length-nozzle, coursework]
aliases: ["SESA3029 Lecture 3.3", "SESA3029 Lecture 3.4", "SESA3029 W05b"]
date: 2026-10-22
status: lectured
coverage: "Lectures 3.3–3.4 lectured Thu 22 and Fri 23 Oct (transcripts), plus the MoC coursework brief (L3-4); §16 from the supplementary note"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[Method of Characteristics]]", "[[Riemann Invariants]]", "[[Prandtl-Meyer Function]]"]
next_topics: []
key_concepts: ["[[Minimum-Length Nozzle]]", "[[Method of Characteristics]]", "[[Riemann Invariants]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 2 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture3-3.pdf", "02 - Sources/Lectures/Lecture3-4.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-3.txt", "02 - Sources/Lectures/Lecture 3-4.txt", "04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf"]
---

# SESA3029 W05b - Minimum-Length Nozzle Design

> [!note] Section numbers continue from [[SESA3029 W05a - Method of Characteristics|W05a]] (§§1–10, Lectures 3.1–3.2), so this note starts at §11 and existing "§14"-style references stay valid.

> [!abstract] Summary
> Lectures 3.3–3.4 turn the unit process of [[SESA3029 W05a - Method of Characteristics|W05a]] into a design tool. The states still come from $R^+=\nu-\theta$ along $C^+$ and $R^-=\nu+\theta$ along $C^-$. What is new is what happens where a characteristic meets a wall or the centreline, and how to shape a wall so that nothing comes back.
>
> - **3.3** adds the boundary conditions (reflecting wall, non-reflecting wall, symmetry plane) and designs the **minimum-length nozzle**: $\theta_{max}=\nu(M_e)/2$, so the throat angle alone gives the exit Mach number. For $M_e=2.4$ with four characteristics, $x_e/r_a=8.069$ and $y_e/r_a=2.400$, against the 1D $A_e/A^*=2.4031$.
> - **3.4** (Fri 23 Oct) works a channel symbolically, finds that point 3 cannot reflect, and solves the inverse problem: $M_4=2.2$, $M_6=2.4$ give $\theta_w=5.0140^\circ$ and $M_0=1.8340$. The lesson: *"always think about the results, whether it makes sense or not"* (L3-4, ll. 279–281). The lecture ended with the **MoC coursework brief**: a minimum-length nozzle for $M_e=3.x$ in **CO₂ ($\gamma=1.289$)** with five characteristics, due **15 Nov**.

> [!summary]- Exam use: quick path
> - **Use it when:** a characteristic reaches a wall or the centreline, or you design a minimum-length nozzle (including the coursework).
> - **Assumptions:** as W05a, and planar (an axisymmetric nozzle needs the §16 extension); $\gamma=1.4$ for the IFT but $\gamma=1.289$ for the CO₂ coursework.
> - **Method:** 1. $\theta_{max}=\nu(M_e)/2$; split the expansion fan into $n$ lines with $\nu=\theta$, $R^-=2\theta$. 2. Interior points by the unit process. 3. Centreline: $\theta_P=0$, $\nu_P=R^-$ arriving. 4. Non-reflecting wall: $\theta_W=\theta_A$, $M_W=M_A$, position by averaged slopes. 5. Check $y_e/r_a$ against $A_e/A^*$.
> - **Common mistakes:** using the $\gamma=1.4$ IFT for CO₂; letting a designed (non-reflecting) wall send a reflected wave back.
> - **Practise:** [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14 worked nozzle]] · [[SESA3029 Mock Questions - Weeks 1-5#Q7. Minimum-length nozzle with three characteristics|Mock Q7]]

## Key concepts

- New: [[Minimum-Length Nozzle]]
- From W05a: [[Method of Characteristics]] · [[Riemann Invariants]] · [[Homentropic Flow]] (the unit process and $R^\pm$ are used at every point)
- From W03: [[Prandtl-Meyer Function]] · [[Expansion Fan]] (the Prandtl–Meyer expansion fan at the throat)
- From W04: [[Isentropic Nozzle Flow]] (SESA2022) and $A/A^*$, which checks the exit height · [[Supersonic Wind Tunnel]]

> [!info] Where this was lectured
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

> [!important] Announcements (L3-3, ll. 3–6)
> - **What the coursework is**: the lecturer called 3.3 *"a very important lecture"* for the coursework and the final exam (L3-3, ll. 3–6). The nozzle-design table of §14 is *"essentially what you are going to do in the coursework"* (l. 132) and *"the table that you're going to work on in the method of characteristics coursework"* (ll. 221–222).

> [!important] The MoC coursework (brief: `04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf`; announced L3-4, ll. 361–425)
> - **Due 23:59, Sun 15 Nov 2026**, on Blackboard. Worth **10 %** of the module. L3-4 gave the date (ll. 415–418); it replaces the 6 Nov of L3-2 and matches the module guide.
> - **Design Mach number $M_{des}=3.x$**, where $x$ is the last digit of your student ID (L3-4, ll. 371–372).
> - **The gas is carbon dioxide at room temperature, $\gamma=1.289$, not air.** The IFT, NST and OSC are all for $\gamma=1.4$, so none of them can be used for your numbers. Every $\nu$, $M$ and $A/A^*$ must come from your own code. The lecture did not mention this; it is only in the brief.
> - **Part A**: program a spreadsheet or Python function giving $\mu$ and $\nu$ for any $M$ and $\gamma$, and verify both against an alternative method.
> - **Part B**: a 2D minimum-length nozzle with **five characteristics** from the expansion corner at $(x,y)=(0,1)$, with angles **equally spaced from $0.125^\circ$ to $\theta_{max}$** (not the $0.375^\circ$ start of §14). Keep **at least four significant figures** throughout. Five lines give **20 points** (L3-4, ll. 392–397): $n(n+3)/2$ for $n$ lines, five of them on the wall (ll. 406–408).
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

## The topic in one physical picture

[[SESA3029 W05a - Method of Characteristics|W05a]] turned supersonic flow into bookkeeping on a mesh of Mach lines. This half adds the edges of the mesh, and with them a way to design a wall.

1. An interior point of the net gets both invariants from its two incoming lines, so the unit process gives $\nu$ and $\theta$ at once.
2. A boundary point has only **one** incoming line. The wall or the centreline supplies the missing number, the flow angle $\theta$: *"all you need … is to obtain two of them"* (L3-3, ll. 27–36).
3. Walls and the centreline decide what happens when a line arrives. A **prescribed** wall reflects it (a new line leaves). A **designed** wall is shaped to absorb it (nothing leaves). The centreline is a mirror.
4. Design a nozzle wall that absorbs every wave arriving at it and the exit flow is **uniform and shock-free**. Put all the expansion into a sharp corner at the throat and that nozzle is also the **shortest** possible.
5. In that minimum-length nozzle the wall's maximum slope at the throat alone fixes the exit Mach number, $\theta_{max}=\nu(M_e)/2$. The 1D area ratio checks the exit height, but only MoC gives the **length**.
6. Blind bookkeeping can invent waves that do not exist. A wall reflects only if the arriving flow has to turn to follow it, so always check that the table makes physical sense (Lecture 3.4).

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

### BC 2: a designed wall is non-reflecting (slide 6)

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

- an **expansion section** of **prescribed** geometry. Characteristics from the walls reflect (BC 1) and cross each other, so this is a **complex region**. The wall slope rises to $\theta_{max}$ at the end of this section (slide 9);
- a **straightening section** of **designed** geometry. Each arriving characteristic is cancelled (BC 2), and the wall slope falls back to zero.

The regions that result:

| Region | Characteristics | Example in the figures |
|---|---|---|
| **complex region** | both families cross | the expansion section; in the minimum-length nozzle, the region behind the expansion corner |
| **simple flow region** | one family only, no crossings (*"characteristics from one direction only"*, slide 10); one invariant is the same everywhere | the amber triangles next to the designed walls |
| **uniform flow region** | none: constant $M_e$, $\theta=0$ | the blue exit core |

The names are the course's: "simple flow region" and "uniform flow region" are on slides 8 and 10, and the supplementary note (p. 10) calls the crossing zones "complex zones". Other names are in [[#Terminology and alternative names]].

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

To make the nozzle as short as possible, remove the prescribed section entirely. All the expansion then happens in a **Prandtl–Meyer expansion fan at point C**, a sharp expansion corner at the throat, and the wall downstream is designed to be non-reflecting, so every wave that reaches it is cancelled. See [[Minimum-Length Nozzle]].

**In the lecture** (L3-3, ll. 144–200). The nozzle length runs from the throat to the exit. A real nozzle should be as short as possible, because extra length means extra weight and bulk (ll. 144–148). So drop the prescribed section and let *"nature"* design the whole wall (ll. 148–153). The wall slope then jumps from about $0$ to $\theta_{max}$ at the throat. *"What do you expect?"* An expansion fan, whose lines are Mach waves and therefore exactly the characteristics (ll. 156–163). Every downstream wall point is made non-reflecting, so straightening starts at once (ll. 164–167).

**Derivation of the maximum slope.**

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
> The expansion fan at C supplies only **half** the expansion: it raises $\nu$ from $0$ to $\theta_{max}$ and turns the wall flow up by $\theta_{max}$. The fan then reflects off the centreline as $C^+$ waves. Crossing those waves expands the flow by another $\theta_{max}$ while turning it back to $\theta=0$.
>
> The designed wall absorbs each reflected wave as it arrives, so it turns back from $\theta_{max}$ to $0$. Along the wall $\nu+\theta$ stays at $2\theta_{max}=36.747^\circ$: the flow keeps accelerating as the wall straightens.

**Reading the exit Mach number off the throat** (L3-3, ll. 204–214). *"The far end and the very first … talk to each other"*: the throat slope and $M_e$ are linked by $\theta_{max}=\nu(M_e)/2$. Show the lecturer a nozzle, let them measure the wall angle at the throat, and they can tell you $M_e$ without a wind tunnel: *"it's what rocket scientists can do"*. Panel 2 of the figure in §10 plots this relation both ways.

> [!example] The lecturer's $M_e=3.2$, both ways (ll. 207–210; computed here)
> **Design.** $\nu(3.2)=53.470^\circ$, so
>
> $$\theta_{max}=\frac{53.470^\circ}{2}=26.735^\circ .$$
>
> **Inverse.** You measure a maximum slope of $26.74^\circ$ at the throat. Double it:
>
> $$\nu(M_e)=2\times26.74^\circ=53.48^\circ .$$
>
> Invert in the IFT: $M_e=3.20$.
>
> For comparison, a maximum slope of $18.375^\circ$ gives $M_e=2.400$ and $13.19^\circ$ gives $2.000$.

> [!warning] Only for a sharp-corner (minimum-length) nozzle
> In a nozzle with a gradual expansion section, the largest slope $\theta_{max}$ is reached at the junction point E (§12). The flow at E has already been expanded by its own wall turning ($\theta_{max}$) **and** by reflected waves from the centreline, so $\nu_E\ge\theta_{max}$. The last $C^-$ from E reaches the start of the uniform region, so
>
> $$\nu(M_e)=R^-_E=\nu_E+\theta_{max}\ge2\theta_{max}.$$
>
> Hence $\theta_{max}\le\nu(M_e)/2$, with equality only for the minimum-length nozzle. A gradual nozzle's measured maximum slope therefore **underestimates** $M_e$ if you double it. This is a derivation added here; the lecture applied the trick to a nozzle that starts at the throat.

**The design recipe** (supplementary note p. 11):

1. $\theta_{max}=\nu(M_e)/2$.
2. Choose the number of characteristics and their angles in the fan, from a **small** $\delta$ up to $\theta_{max}$. $\delta=0$ would give a line bouncing back and forth across the throat, which is useless.
3. In the fan $\nu=\theta$, because $R^+=0$ from the sonic throat. So each line of the expansion fan carries $R^-=2\theta$.
4. Apply the unit process to all the points downstream.
5. Work left to right and compute the coordinates: interior points by §10, centreline points by BC 3, designed wall points by BC 2.

---

## 14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)

**Set-up** (slide 11; L3-3, ll. 215–222). Design a nozzle for $M_e=2.4$ using four characteristics a to d from point 0 at $(0,1)$, the expansion corner at the throat, with $\theta_{0a}=0.375^\circ$. Find points 1 to 14. Lengths are scaled by $r_a$, *"the nozzle throat's half-width"*, with $r_a=1$ (slide 21). More lines in the expansion fan give more points and more resolution, but four lines and 14 points are *"something manageable"* (ll. 219–221).

**The columns** (ll. 226–231): $R^+$, $R^-$, $\theta$ and $\nu$ are the essential four. $M$ comes from $\nu$, $\mu$ from $M$, and $\theta\pm\mu$ are needed only for the slopes that place $x$ and $y$.

**Start from the exit** (ll. 232–239). Point 14 must have $M=2.4$, so $\nu_{14}=\nu(2.4)=36.7465^\circ$, rounded to $36.75^\circ$. Point 13 is the same, since nothing changes between 13 and 14. Halving gives $\theta_{max}=18.375^\circ$, which is $\nu=\theta$ on 0d, *"the last line of the expansion fan"* (l. 239).

**Why $0.375^\circ$** (ll. 240–243). Spread the four lines evenly: $0.375$, $6.375$, $12.375$, $18.375^\circ$, adding $6^\circ$ each time. The first value is chosen *"for numerical convenience"*, so that the steps end exactly on $18.375^\circ$. It also keeps line 0a off $M=1$, where $\mu=90^\circ$ (§13 recipe, step 2).

**Step 1: the lines of the expansion fan** (slides 13–15; ll. 244–250). Equal steps from $0.375^\circ$ to $\theta_{max}$. These lines carry only $R^-=\nu+\theta=2\theta$; $R^+$ is "not applicable" there (ll. 245–247). The rows 0a–0d of the lecturer's *Template for MoC Calculation* (slides 12–14), in its column order:

| Point | $R^+$ | $R^-$ | $\theta$ | $\nu$ | $M$ | $\mu$ | $\theta+\mu$ | $\theta-\mu$ | $x$ | $y$ |
|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0a | N/A | 0.750 | 0.375 | 0.375 | 1.0418 | 73.708 | 74.083 | −73.333 | 0 | 1 |
| 0b | N/A | 12.749 | 6.374 | 6.374 | 1.3074 | 49.894 | 56.268 | −43.519 | 0 | 1 |
| 0c | N/A | 24.748 | 12.374 | 12.374 | 1.5159 | 41.275 | 53.649 | −28.901 | 0 | 1 |
| 0d | N/A | 36.747 | 18.373 | 18.373 | 1.7192 | 35.568 | 53.941 | −17.194 | 0 | 1 |

All angles are in degrees. $R^+$ is "N/A" at the corner, since no $C^+$ arrives there. Slide 14 writes $R^-=0.75$, $12.75$, $24.75$, $36.75$, from the rounded $\theta_{max}=18.375^\circ$.

**Step 2: the invariants** (slides 16–18; ll. 250–275, *"fairly straightforward and mechanical"*, l. 259). Fill in the invariants line by line before anything else:

- each $C^-$ keeps the value it leaves the expansion fan with: points 2 and 6 have $R^-=12.75$; points 3, 7 and 10 have $24.75$; points 4, 8, 11 and 13 have $36.75$;
- each centreline point turns $R^-$ into an equal $R^+$ (BC 3), which then runs up its $C^+$: 1–5 carry $0.75$, 6–9 carry $12.75$, 10–12 carry $24.75$, 13–14 carry $36.75$;
- the wall points 5, 9, 12 and 14 are non-reflecting, so no $C^-$ leaves them ("N/A").

**Step 3: the states** (slide 19; ll. 275–283). $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$, then $M$ and $\mu$. Wall points copy the state of the point below them: point 5 has the $\theta$ and $\nu$ of point 4 (ll. 277–280).

**Step 4: the coordinates** (slide 20; ll. 285–292). Three typical points:

- **Point 1** (BC 3, from 0a): $\theta_1=0$, $\nu_1=0.750^\circ$, $M_1=1.0671$, $\mu_1=69.570^\circ$. Then $\alpha=\tfrac12(-73.333-69.570)=-71.451^\circ$ and $\tan\alpha=-2.9803$, so $x_1=0-1/(-2.9803)=0.3355$.
- **Point 2** (interior; A = 1, B = 0b): $\theta_2=\tfrac12(12.749-0.750)=5.999^\circ$, $\nu_2=6.749^\circ$, $M_2=1.3210$, $\mu_2=49.200^\circ$. Then $\alpha_{12}=\tfrac12(69.570+55.199)=62.385^\circ$ and $\alpha_{0b,2}=\tfrac12(-43.519-43.201)=-43.360^\circ$. The formula gives $(0.5747,\ 0.4573)$.
- **Point 5** (BC 2; A = 4, previous wall point 0): $\theta_5=\theta_4=17.998^\circ$ and $M_5=M_4=1.7320$. Then $\alpha_{45}=(\theta+\mu)_4=53.263^\circ$ and $\alpha_{05}=\tfrac12(18.373+17.998)=18.186^\circ$, giving $(1.2947,\ 1.4253)$.

**The completed table** (computed here), in the column order of the lecturer's *Template for MoC Calculation* (slides 12–14). The point type and the slide 20 coordinates are added after the template's columns:

| Point | $R^+$ | $R^-$ | $\theta$ | $\nu$ | $M$ | $\mu$ | $\theta+\mu$ | $\theta-\mu$ | $x$ | $y$ | Type | slide $(x,y)$ |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|---|
| 0a | N/A | 0.750 | 0.375 | 0.375 | 1.0418 | 73.708 | 74.083 | −73.333 | 0 | 1 | expansion fan | 0, 1 |
| 0b | N/A | 12.749 | 6.374 | 6.374 | 1.3074 | 49.894 | 56.268 | −43.519 | 0 | 1 | expansion fan | 0, 1 |
| 0c | N/A | 24.748 | 12.374 | 12.374 | 1.5159 | 41.275 | 53.649 | −28.901 | 0 | 1 | expansion fan | 0, 1 |
| 0d | N/A | 36.747 | 18.373 | 18.373 | 1.7192 | 35.568 | 53.941 | −17.194 | 0 | 1 | expansion fan | 0, 1 |
| 1 | 0.750 | 0.750 | 0 | 0.750 | 1.0671 | 69.570 | 69.570 | −69.570 | 0.3355 | 0 | centre | 0.335, 0 |
| 2 | 0.750 | 12.749 | 5.999 | 6.749 | 1.3210 | 49.200 | 55.199 | −43.201 | 0.5747 | 0.4573 | interior | 0.574, 0.458 |
| 3 | 0.750 | 24.748 | 11.999 | 12.749 | 1.5286 | 40.858 | 52.857 | −28.860 | 0.6917 | 0.6184 | interior | 0.691, 0.619 |
| 4 | 0.750 | 36.747 | 17.998 | 18.748 | 1.7320 | 35.265 | 53.263 | −17.267 | 0.7936 | 0.7539 | interior | 0.793, 0.754 |
| 5 | 0.750 | N/A | 17.998 | 18.748 | 1.7320 | 35.265 | 53.263 | −17.267 | 1.2947 | 1.4253 | wall | 1.293, 1.425 |
| 6 | 12.749 | 12.749 | 0 | 12.749 | 1.5286 | 40.858 | 40.858 | −40.858 | 1.0820 | 0 | centre | 1.082, 0 |
| 7 | 12.749 | 24.748 | 5.999 | 18.748 | 1.7320 | 35.265 | 41.264 | −29.266 | 1.3635 | 0.2452 | interior | 1.363, 0.245 |
| 8 | 12.749 | 36.747 | 11.999 | 24.748 | 1.9413 | 31.006 | 43.005 | −19.007 | 1.6248 | 0.4816 | interior | 1.625, 0.482 |
| 9 | 12.749 | N/A | 11.999 | 24.748 | 1.9413 | 31.006 | 43.005 | −19.007 | 3.1775 | 1.9298 | wall | 3.177, 1.93 |
| 10 | 24.748 | 24.748 | 0 | 24.748 | 1.9413 | 31.006 | 31.006 | −31.006 | 1.7858 | 0 | centre | 1.786, 0 |
| 11 | 24.748 | 36.747 | 5.999 | 30.747 | 2.1622 | 27.548 | 33.547 | −21.548 | 2.2074 | 0.2663 | interior | 2.207, 0.266 |
| 12 | 24.748 | N/A | 5.999 | 30.747 | 2.1622 | 27.548 | 33.547 | −21.548 | 5.1989 | 2.2499 | wall | 5.199, 2.25 |
| 13 | 36.747 | 36.747 | 0 | 36.747 | 2.4000 | 24.624 | 24.624 | −24.624 | 2.8323 | 0 | centre | 2.832, 0 |
| 14 | 36.747 | N/A | 0 | 36.747 | 2.4000 | 24.624 | 24.624 | −24.624 | **8.0691** | **2.4003** | wall | **8.069, 2.4** |

> [!check] Reproducing the slides
> Every point agrees with slide 20 to within $0.002$. The slides round $\nu(2.4)$ to $36.75^\circ$ and $M$ to three decimals before taking $\mu$. Repeating the calculation with $M$ rounded the same way gives point 14 at exactly $(8.069,\ 2.400)$.

**Reading the result.** The wall is the polyline 0–5–9–12–14, the non-reflecting wall points (ll. 286–287). The lecturer read point 14 as $x=8.069$, $y=2.4$, normalised by the throat half-width $r_a$ (slide 21; he said *"throat height"*, ll. 288–289), so the exit area is 2.4 times the throat area (l. 291). Its segment slopes are $18.19^\circ$, $15.00^\circ$, $9.00^\circ$ and $3.00^\circ$, falling back to $0$. At 13 the centreline reaches $M_e=2.4$, and the triangle 13–14–centreline is the uniform region.

> [!check] Mass conservation checks the whole calculation
> The exit flow is uniform at $M_e$ and the throat flow is uniform at $M=1$, so the exit half-width must equal the 1D area ratio:
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

**Refined design** (slide 21; supplementary note Fig. 10; ll. 293–301). With 20 characteristics the wall becomes a smooth curve. The centreline Mach number rises from 1 to 2.4 over the first $x/r_a\approx2.84$, where the centreline borders the complex region, and stays at 2.4 after that (panel 3, lower plot). As slide 21 puts it, 1D theory gives $y_e/r_a=A_e/A^*=2.4031$ *"but it gives no clue about $x_e/r_a=8.069$ revealed by MoC"*. The lecturer read $2.403$ from the last IFT column, *"very well matched"* with MoC, and stressed that 1D theory *"didn't know what the length of the nozzle should be"* (ll. 297–301).

> [!info] Where the recording stops (l. 303)
> `Lecture 3-3.txt` ends mid-sentence: *"And coincidentally…"*. The rest is not recorded. The most likely point, given the slide, is that $y_e/r_a\approx2.40$ happens to equal the design Mach number $2.4$. That really is a coincidence. For $\gamma=1.4$, $A/A^*=M$ only at $M=2.397$; at $M_e=2$ the ratio is $1.6875$, and at $M_e=3$ it is $4.2346$. So $y_e/r_a=M_e$ is **not** a rule. This reading is an inference, not something the lecturer said.

> [!example] Your turn: $M_e=2.0$ (suggested; answer computed here)
> $\nu(2)=26.380^\circ$, so $\theta_{max}=13.190^\circ$. With four lines at $0.375$, $4.647$, $8.918$ and $13.190^\circ$, the lines of the expansion fan carry $R^-=0.750$, $9.293$, $17.837$ and $26.380^\circ$.
>
> The results are $M_1=1.0671$ at $x_1=0.3355$, and the uniform region starts at 13, $x=1.905$. The exit is at $(x_e,y_e)=(4.815,\ 1.681)$, against $A_e/A^*=1.6875$. A lower design Mach number gives a much shorter nozzle.

---

## 15. The generic MoC example (Lecture 3.4)

![[at_moc_generic_example.png|900]]

> [!info] Lectured Fri 23 Oct (`Lecture 3-4.txt`)
> 3.4 was given as *"relatively quite simple and quick"* once 3.1–3.3 are digested (L3-4, ll. 1–2). It was originally written ahead from the slides and has now been backfilled with line references. *"Generic as opposed to numerical"*: only symbols, no numbers (ll. 8–10).

**Set-up** (slide 2; L3-4, ll. 11–31). An expanding channel of half-width 1 carries supersonic flow $M_0$ along its centreline. At $(0,1)$ the upper wall turns up by $\theta_w$ and stays straight. The Prandtl–Meyer fan at 0 is represented by two characteristics: "a", the leading wave at the upstream state, and "b", the trailing wave at $\theta_w$. Find $\nu$ and $\theta$ at points 1 to 6 in terms of $\nu_a$ and $\theta_w$.

> [!tip] "The coarsest mesh that you can imagine" (ll. 14–20)
> Two lines for a whole fan is deliberately crude: *"this is not an ideal case, but we can still learn a lot from this simplest case."* More lines give more accuracy, *"which is what you are going to do in the coursework"* (ll. 19–20). The centreline acts *"effectively [as] a wall as well"* (l. 26), as in BC 3.

**What is known beforehand** (slide 3; ll. 34–56): $\theta=0$ at 0a and on the centreline (1, 4); $\theta=\theta_w$ at 0b and on the wall (3, 6); $\nu_{0a}=\nu_a$. No $C^+$ passes through 0a or 0b, so $R^+$ is *"not applicable"* there (ll. 36–37). *"That's the first thing that you can do without doing any calculation"* (l. 56).

**Steps** (slides 4–11, one fact at a time):

1. Across the fan, $\Delta\theta=\theta_w=\nu_b-\nu_a$, so $\nu_b=\nu_a+\theta_w$ (ll. 63–76).
2. Invariants on the two lines of the expansion fan: $R^-_{0a}=\nu_a+0=\nu_a$ and $R^-_{0b}=(\nu_a+\theta_w)+\theta_w=\nu_a+2\theta_w$ (ll. 59–61, 77–83).
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
> The figure locates every point with the unit process. Point 3 is a non-reflecting wall point at $(3.415,\ 1.300)$ and point 6 is a prescribed-wall point at $(4.779,\ 1.419)$. These coordinates are computed here, not on the slides.

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
2. **Fill in the invariants.** Each line keeps its value. At the centreline $R^+=R^-$. A non-reflecting wall sends nothing back. A prescribed wall sends $R^-_W=R^+_A+2\theta_W$ (top) or $R^+_W=R^-_B-2\theta_W$ (bottom).
3. **States**: $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$. Wall and centreline points use their known $\theta$.
4. $M$ from $\nu$ (IFT, interpolating), then $\mu=\sin^{-1}(1/M)$; then the $\theta\pm\mu$ columns.
5. **Coordinates last**, left to right:
   - interior: averaged $\alpha$, then the $x_P$ formula;
   - centreline: $x_P=x_B-y_B/\tan\alpha_{BP}$;
   - designed wall: $\alpha_{AW}=(\theta+\mu)_A$ and $\alpha_{BW}=\tfrac12(\theta_B+\theta_W)$.
6. **Check**: the exit half-width $y_e/r_a$ against $A_e/A^*$, and the maximum slope $\theta_{max}$ against $\nu(M_e)/2$.

> [!info] What the exam gives you
> The official `Aerothermodynamics Formula Sheet.pdf` already lists $R^\pm=\nu\mp\theta$ and the intersection formulae for $\alpha_{AP}$, $\alpha_{BP}$, $x_P$ and $y_P$ ([[SESA3029 Formula Sheet#What the exam formula sheet gives you|formula sheet]]). What you must bring is the **procedure**: which invariant runs along which line, the three boundary conditions, and $\theta_{max}=\nu(M_e)/2$. The IFT has a $\nu$ column, so you can invert $\nu\to M$ by interpolation.

---

## Transcript slips

Whisper renders some words consistently wrongly in these recordings: "mark" for Mach, "I-centric"/"isentrific" for isentropic, "oxine" for arcsine, "Pranthal/frontal/planter/quantum mayor" for Prandtl–Meyer (and in L3-4 *"quantum wave function"*, l. 68, and *"plant and mayor fat"* for the fan, l. 375), "menstrual characteristics" for method of characteristics, and "0.N" for "point N". These are not listed below.

> [!warning] Slips and garbled passages in `Lecture 3-3.txt` (Thu 22 Oct)
> | Line | Said | Correct |
> |---|---|---|
> | ll. 28–30 | *"R plus is NU minus theta over 2. R minus is NU plus theta over 2. no sorry the other way around"* | $R^+=\nu-\theta$ and $R^-=\nu+\theta$, with **no** factor $\tfrac12$. The halving belongs to the inverse, $\nu=\tfrac12(R^++R^-)$ and $\theta=\tfrac12(R^--R^+)$, as restated correctly at l. 31 |
> | l. 60 | *"R minus is R plus plus plus theta"* | $R^-_W=R^+_A+2\theta_W$ (corrected in the same line) |
> | l. 97 | *"use the a e p triangle to calculate point b"* | use the triangle A–B–P (A the image of B) to find point **P** |
> | l. 257 | *"0.8 is same as 0.11. So 36.75"* | $R^-_8=R^-_4=36.75^\circ$, carried on to $R^-_{11}=R^-_8$ |
> | l. 266 | *"0.789 share the same r plus"* | points 7, 8 and 9 share $R^+=12.75^\circ$ |
> | l. 279 | *"theta and mu are the same as 0.4"* | $\theta$ and $\nu$ (nu) at the non-reflecting wall point 5 equal those at point 4 |
> | l. 289 | *"normalized by the throat height, 1"* | by the throat **half**-width $r_a=1$: *"the nozzle throat's half-width"* (slide 21) |
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

## Terminology and alternative names

This note uses the course's own words. Textbooks (Anderson in particular), other universities and CFD software often use other names for the same ideas. Use the course term in the coursework and the exam, and treat the others as search terms.

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| complex region (crossing characteristics) | kernel; non-simple region; non-simple wave region | Supplementary Note p. 10: *"complex zones (with crossing characteristics)"* | "Kernel" is the usual textbook name for the crossing region behind the expansion corner of a minimum-length nozzle. The slides draw it but do not label it |
| simple flow region (characteristics from one direction only) | simple-wave region; simple region; simple wave | L3.3 slides 8 and 10; Supplementary Note p. 9 ("'simple' regions") | One family of characteristics only, so one Riemann invariant is the same everywhere |
| uniform flow region | uniform region; exit core flow | L3.3 slides 8 and 10; L3-3, l. 196 | No characteristics cross it: $M=M_e$, $\theta=0$ |
| non-reflecting wall; wave cancellation (no reflection); designed geometry | cancelling wall; wave-cancelling wall; contoured wall | L3.3 slides 6 and 8; L3-3, ll. 46, 65–87, 115–142, 277–287 | The lecturer says "non-reflecting" throughout. The Supplementary Note (pp. 8–9) says the line is "cancelled" at the wall and calls it "the cancelling approach" |
| reflecting wall; prescribed geometry | solid wall; wall point (Anderson) | L3.3 slides 5 and 8 | BC 1. A reflection occurs only when $\theta_A\neq\theta_W$ |
| symmetry plane; centreline | axis of symmetry; symmetry boundary (CFD) | L3.3 slide 7; Supplementary Note p. 9 | The lecturer's *"mirror or image effect"* (L3-3, ll. 88–93) |
| $r_a$, the nozzle throat's half-width | throat half-height; throat radius (axisymmetric); $y^*$ | L3.3 slide 21 | Slide 9 marks the same length as $y^*$. The lecturer said *"throat height"* (L3-3, l. 289) |
| exit half-width $y_e/r_a$ | exit half-height; exit area ratio | L3.3 slide 21 | Equals $A_e/A^*$ for a planar nozzle |
| maximum slope $\theta_{max}$ (of the wall) | maximum wall angle; throat wall angle; $\theta_{w,max}$ (Anderson) | L3.3 slide 9, *"Maximum Slope ($\theta$max)"*; L3-3, ll. 137–142 | Not the oblique-shock $\theta_{max}$ of W02 |
| Prandtl–Meyer (PM) expansion fan; lines of the expansion fan | centred expansion fan; Prandtl–Meyer fan; expansion wave; fan rays | L3.3 slide 10 ("PM expansion fan at C"); L3.4 slide 2; L3-3, ll. 160–175, 216, 239 | 0a–0d are *"the last line of the expansion fan"* and the ones before it (L3-3, l. 239) |
| expansion corner (point C on slide 10, point 0 in the examples) | sharp corner; throat corner; sharp throat | Coursework brief ("the expansion corner (x=0, y=1)"); L3.3 slides 10–11 | The lecturer describes it as a *"discontinuity of the slope"* (L3-3, l. 158) |
| Template for MoC Calculation | MoC table; characteristic table; MoC spreadsheet | L3.3 slides 12–14 | Columns Point, $R^+$, $R^-$, $\theta$, $\nu$, $M$, $\mu$, $\theta+\mu$, $\theta-\mu$, $x$, $y$; "N/A" where no line arrives or leaves |
| Riemann invariants $R^+=\nu-\theta$, $R^-=\nu+\theta$ | $K^+$, $K^-$ (Anderson), with $K^+=-R^+=\theta-\nu$ and $K^-=R^-=\theta+\nu$ | L3.1 slide 12; Supplementary Note p. 5 | Same physics, different sign of $K^+$; do not mix the two in one table |
| minimum-length nozzle | sharp-corner nozzle; MLN | L3.3 slide 10 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W05a - Method of Characteristics]] (theory, Riemann invariants and the unit process, §§1–10)
- Earlier this module: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]] (1D nozzle and $A/A^*$) · [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#5. Expansion waves and the Prandtl–Meyer function|W03 §5, the Prandtl–Meyer function]]
- New concepts: [[Minimum-Length Nozzle]]
- From W05a: [[Method of Characteristics]] · [[Riemann Invariants]] · [[Homentropic Flow]]
- Related concepts: [[Prandtl-Meyer Function]] · [[Mach Waves and Mach Angle]] · [[Expansion Fan]] · [[Isentropic Nozzle Flow]] · [[Supersonic Wind Tunnel]]
- Worked sheet: [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|ES2 Q3]] (a prescribed-wall duct, BC 1 and BC 3)
- Formulae: [[SESA3029 Formula Sheet#Method of characteristics (Lectures 3.1–3.4)|Formula sheet: MoC]]
- **Builds on / connects to** (cross-module):
  - [[SESA3043 3.6 - Viscous-Inviscid Interaction#3. Surface displacement method (slides 10–13)|SESA3043 3.6 §3]] and [[SESA3043 3.1 - Boundary-Layer Concepts and Thickness Measures|SESA3043 3.1]]: MoC designs the *inviscid* wall. Practical nozzle contours are then moved outwards by the boundary-layer displacement thickness $\delta^*$, which is the surface displacement idea of 3.6 used in reverse. (Bridging remark; not lectured in SESA3029.)

## Sources

- `Lecture3-3.pdf`: 3.3 MoC Boundary Conditions & Minimum-length Nozzle Design, 21 slides, with the full $M_e=2.4$ table. Lectured Thu 22 Oct.
- `Lecture3-4.pdf`: 3.4 Generic MoC Example, 15 slides. Lectured Fri 23 Oct.
- `Supplementary Note for MoC.pdf`: 12-page note. Derivation in $s$–$n$ coordinates, the eigen-decomposition, the unit process, walls, the minimum-length nozzle, and an axisymmetric appendix. It cites Anderson (2004) and Liepmann & Roshko (1957).
- `Lecture 3-3.txt`: the Thu 22 Oct recording of 3.3 (303 lines; cut off mid-sentence at the end of slide 21).
- `Lecture 3-4.txt`: the Fri 23 Oct recording of 3.4 (425 lines): the generic example (ll. 7–359) and the MoC coursework brief (ll. 361–425).
- `04 - Labs & Coursework/MoC Coursework/MoC Coursework 2026-27.pdf`: the one-page coursework brief (due 23:59, Sun 15 Nov; $\gamma=1.289$).
- Anderson, *Modern Compressible Flow*, Ch. 11; *Fundamentals of Aerodynamics*, §13.3.
- Figures: `generate_aerothermo_w05_figures.py`. Eight geometry and data figures; the unit-process code reproduces the slide answers. `at_moc_supersonic_source.png` and `at_moc_mach_angle_throat_angle.png` were added from the L3-2 and L3-3 recordings. Derivations are native Obsidian LaTeX.

## Self-study tasks

> [!todo] How to use this list
> - Tasks citing `L3-3` or `L3-4` were set or worked in the lectures of Thu 22 and Fri 23 Oct. L3-4 added *"try and do it on your own"* for the symbolic table (ll. 201–203) and the coursework. The 3.1–3.2 tasks, including the point 3 homework, are in [[SESA3029 W05a - Method of Characteristics#Self-study tasks|W05a]].
> - The rest are *suggested, not lecturer-set*.
>
> Deadlines: **Test 2 closes Sun 25 Oct, midnight** (L3-1, ll. 3–5; L3-2, ll. 2–8; L3-4, l. 6). The **MoC coursework** (10 %) is due **Sun 15 Nov** (L3-4, ll. 415–418), not the 6 Nov of L3-2 (see [[#Announcements and deadlines|the announcements]]).

### Core

- [ ] **(L3-3, ll. 132, 221–222)** Fill in the $M_e=2.4$ template yourself. This is the coursework procedure. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] **(L3-4, ll. 198–203)** Fill in the symbolic 3.4 table on your own in under a minute: *"this type of question was one of the questions in the past papers"*. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] **(L3-4, ll. 298–348)** Recover $\theta_w=5.014^\circ$ and $M_0=1.834$ from $M_4=2.2$ and $M_6=2.4$. → [[#15. The generic MoC example (Lecture 3.4)|§15, the inverse problem]]
- [ ] **MoC coursework** (brief in `04 - Labs & Coursework/MoC Coursework/`; L3-4, ll. 361–418): minimum-length nozzle for $M_{des}=3.x$ ($x$ = last digit of your student ID), **CO₂, $\gamma=1.289$**, five characteristics from $0.125^\circ$, 20 points, four significant figures, sections i–vi, at most six A4 pages. **Due 23:59, Sun 15 Nov.** → [[#Announcements and deadlines]] and [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] Derive $\theta_{max}=\nu(M_e)/2$, including why $\nu(1)=0$ (L3-3, ll. 168–200). → [[#13. The minimum-length nozzle (3.3 slide 10)|§13]]

### Further practice

#### Lecturer-set or lecturer-prompted

- [ ] **(L3-4, ll. 206–281)** Spot the non-physical entry before being told: why point 3 cannot reflect and point 5 does not exist. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] **(Brief, part A)** Write and verify a $\mu$, $\nu$ (and $A/A^*$) function for any $\gamma$, with a root finder for $\nu\to M$. → [[#Announcements and deadlines|the γ tip box]]
- [ ] **(L3-4, ll. 400–411)** *Optional:* automate the table (Excel or Python) and add more lines to see the wall converge. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]

#### Derivations

- [ ] Derive the three boundary conditions and their coordinate rules (L3-3, ll. 50–98). → [[#11. Boundary conditions (3.3 slides 4–7)|§11]]
- [ ] *(Suggested)* Show that a gradual-expansion nozzle has $\theta_{max}\le\nu(M_e)/2$. → [[#13. The minimum-length nozzle (3.3 slide 10)|§13, the warning]]

#### Calculations

- [ ] **(L3-3, ll. 215–292)** Fill in the template for points 1–14 of the $M_e=2.4$ nozzle. Point 14 is at $(8.069,\ 2.400)$. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]
- [ ] **(L3-3, ll. 206–214)** The lecturer's trick: find $\theta_{max}$ for $M_e=3.2$, then recover $M_e$ from a measured $26.74^\circ$. Answer: $26.735^\circ$, $M_e=3.20$. → [[#13. The minimum-length nozzle (3.3 slide 10)|§13]]
- [ ] *(Suggested, in the spirit of L3-4, ll. 349–358)* Reuse the symbolic table for $M_4=2.0$, $M_6=2.2$. Answer: $\theta_w=5.353^\circ$, $\nu_a=15.674^\circ$, $M_0=1.628$. → [[#15. The generic MoC example (Lecture 3.4)|§15]]
- [ ] *(Suggested)* The $M_e=2.0$ nozzle with four lines. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14, "Your turn"]]
- [ ] Redo [[SESA3029 Example Sheet 2 - Solutions#Q2. Characteristics and Riemann invariants|ES2 Q2]] and [[SESA3029 Example Sheet 2 - Solutions#Q3. Flow in a symmetric 2D duct|Q3]] in the $R^\pm$ notation.
- [ ] *(Suggested, coursework preparation)* Program the unit process, as the supplementary note recommends for more than about six lines. Validate it with point 14 and with $y_e/r_a\to A_e/A^*$. → [[#14. Worked example: minimum-length nozzle for Me = 2.4 (3.3 slides 11–21)|§14]]

#### Concepts

- [ ] Distinguish the complex, simple flow and uniform flow regions, and prescribed (reflecting) from designed (non-reflecting) walls. Explain why non-reflecting points 12 and 13 make 11–13 uniform (L3-3, ll. 103–131). → [[#12. Nozzles with a straightening section (3.3 slides 8–9)|§12]]
- [ ] Tell the nozzle's $\theta_{max}$ (wall slope) apart from the oblique-shock $\theta_{max}$ (L3-3, ll. 137–139). → [[#12. Nozzles with a straightening section (3.3 slides 8–9)|§12]]
- [ ] Explain why 3.4's point 3 does not reflect, and why 6's state survives while its position changes (L3-4, ll. 238–295). → [[#15. The generic MoC example (Lecture 3.4)|§15]]
