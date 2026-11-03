---
title: "SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 6
tags: [sesa2028, structures, buckling, beam-column, secant-formula]
date: 2026-10-30
status: lectured
coverage: "SL14 (2026-04-24, ll. 200–660), buckling tutorial (2026-04-27, two groups), buckling problems at the start of SL15 (2026-04-30, ll. 1–100); plate buckling not lectured in 2025–26"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S5 - Euler Buckling and Effective Length]]"]
next_topics: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
key_concepts: ["[[Secant Formula]]", "[[Beam-Column]]", "[[Beam-Column Amplification]]", "[[Plate Buckling]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 4 - Buckling Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL7 buckling of beams with imperfection.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-24.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-27 - 0901.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-27 - 1400.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-30.txt"]
---

# SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling

> [!abstract] Summary
> Real columns are never perfect: an eccentric load, an initial curvature or a lateral load makes them bend from the first increment of load, so there is no clean bifurcation, and deflection and stress grow faster and faster as the load approaches the Euler load. For an eccentric load the result is the secant formula, $\sigma_{max}=\frac PA\left[1+\frac{ec}{\kappa^2}\sec\mu L_e\right]$; for an initial bow the deflection is amplified by $1/(1-P/P_{cr})$; for a lateral load the bending moment is amplified in the same way. Because $\mu$ depends on $P$, design problems such as finding a section size are nonlinear and are solved graphically or by bisection.

> [!summary]- Exam use: quick path
> - **Use it when:** a compression member has an eccentric load, an initial crookedness or a transverse load as well.
> - **Assumptions:** linear elastic, small deflections, $\mu^2=P/EI$, failure when the extreme-fibre compressive stress reaches $\sigma_Y$ (with a safety factor).
> - **Method:** 1. Section properties, $\kappa^2=I/A$, $c$. 2. Identify the case and its formula. 3. Eccentric: $\sigma_{max}=\frac PA[1+\frac{ec}{\kappa^2}\sec\mu L]$ (fixed–free; $L/2$ for pinned). 4. Curved: $\sigma_{max}=\frac PA[1+\frac{ac}{\kappa^2}\frac1{1-P/P_{cr}}]$. 5. Lateral load: $\sigma_{max}=\frac PA+\frac{M_{max}c}{I}$ with the amplified moment; check Euler buckling about the weak axis too.
> - **Common mistakes:** using the secant formula with $e=0$ (it then says nothing; use Euler); checking only the bending plane and not weak-axis buckling.
> - **Practise:** [[#Worked examples]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q2 - Permissible initial curvature of a control rod|Tutorial 4 Q2]]

The perfect column of [[SESA2028 S5 - Euler Buckling and Effective Length|S5]] stays straight up to $P_{cr}$ and then bifurcates. The opening poll asked what happens to a column with a small initial curvature: it deflects from the start, never reaches a bifurcation point, and its load capacity is below $P_{cr}$ (2026-04-24, ll. 200–240).

Press the ends of a slightly bent drinking straw and the bend grows at once, because the load's line of action misses the bent middle and so applies a bending moment there; the extra bend moves the middle further from that line, which increases the moment again. Far below the Euler load this feedback is weak, but near it each extra bit of bending generates nearly as much again, and the deflection runs away. An eccentric load, a crooked column and a side load all start that feedback in different ways.

## 1. The four-step method

Every case follows the same steps as the perfect column (2026-04-24, ll. 240–280): draw the buckled shape and take a cut; write the moment at the cut from equilibrium; substitute $M=-EIv''$ to get the governing equation; solve it (complementary function plus particular integral) and fix the constants from the boundary conditions. The lecture derives the eccentric case in full and leaves the initially curved and laterally loaded cases to mini-lecture videos with the derivations on the slides (ll. 441–500).

## 2. Eccentric load: the secant formula

A column of length $L$ is clamped at its base and free at its top, where a load $P$ acts at eccentricity $e$ from the axis (ll. 241–440). Measure $x$ down from the top, with $v(x)$ the lateral deflection and $a=v(0)$ the unknown tip deflection. The moment at the cut is $P$ times its lever arm, $M_x=P(e+a-v)$, so with $M=-EIv''$ and $\mu^2=P/EI$,

$$
\frac{d^2v}{dx^2}+\mu^2v=\mu^2(e+a).
$$

The general solution is the complementary function plus the constant particular integral:

$$
v=A\sin\mu x+B\cos\mu x+e+a .
$$

At the top, $v(0)=a$:

$$
B+e+a=a
\quad\Longrightarrow\quad
B=-e .
$$

At the clamped base, $v'(L)=0$:

$$
A\mu\cos\mu L-B\mu\sin\mu L=0
\quad\Longrightarrow\quad
A=-e\tan\mu L .
$$

At the base, $v(L)=0$:

$$
-e\tan\mu L\sin\mu L-e\cos\mu L+e+a=0 .
$$

Combine the first two terms, $\frac{\sin^2\mu L+\cos^2\mu L}{\cos\mu L}=\sec\mu L$:

$$
v_{max}=a=e\left(\sec\mu L-1\right).
$$

The largest moment is at the base, $M_{max}=P(e+a)=Pe\sec\mu L$, and the largest compressive stress adds the axial and bending parts at the extreme fibre $c$:

$$
\sigma_{max}=\frac PA+\frac{Pe\sec\mu L\,c}{I}=\frac PA\left[1+\frac{ec}{\kappa^2}\sec\mu L\right].
$$

This is the secant formula ([[Secant Formula]]). A pinned column of length $L$ behaves like two such cantilevers of length $L/2$, so replace $\mu L$ by $\mu L/2$ (ll. 441–460). As $P\to P_{cr}$, $\mu L\to\pi/2$ for the cantilever, the secant goes to infinity, and so do the deflection and stress; the formula is only valid for $e>0$, and for $e=0$ the Euler formula applies instead (ll. 361–440). Plotted against $P$, $v_{max}$ starts rising immediately and bends towards the Euler load asymptotically, more gradually for larger eccentricity: there is no bifurcation.

## 3. Initially curved column

A pinned column has an initial bow $v_0=a\sin(\pi x/L)$ (slides 24–36). Under $P$ it deflects a further $v_1$; the moment uses the total offset, $M=P(v_0+v_1)$, and only $v_1$ produces curvature from the unstressed shape:

$$
EI\frac{d^2v_1}{dx^2}=-P\left(v_0+v_1\right)
\quad\Longrightarrow\quad
\frac{d^2v_1}{dx^2}+\mu^2v_1=-\mu^2a\sin\frac{\pi x}{L}.
$$

Try $v_1=C\sin(\pi x/L)$, which satisfies the pinned ends:

$$
\left(-\frac{\pi^2}{L^2}+\mu^2\right)C=-\mu^2a
\quad\Longrightarrow\quad
C=\frac{\mu^2a}{\pi^2/L^2-\mu^2}=\frac{a\,P/P_{cr}}{1-P/P_{cr}} .
$$

The total midspan offset is

$$
a+C=\frac{a}{1-P/P_{cr}},
$$

the initial bow amplified by $1/(1-P/P_{cr})$ ([[Beam-Column Amplification]]). The maximum stress is

$$
\sigma_{max}=\frac PA\left[1+\frac{ac}{\kappa^2}\cdot\frac{1}{1-P/P_{cr}}\right].
$$

## 4. Laterally loaded column (beam-column)

A pinned column of length $L$ carries an axial load $P$ and a uniform transverse load $w$ (slides 38–49). The moment now has a beam part and an axial part:

$$
M=\frac{wx(L-x)}{2}+Pv
\quad\Longrightarrow\quad
\frac{d^2v}{dx^2}+\mu^2v=-\frac{w\,x(L-x)}{2EI}.
$$

Solving with $v(0)=v(L)=0$ and evaluating the moment at midspan gives

$$
M_{max}=\frac{w}{\mu^2}\left[\sec\frac{\mu L}{2}-1\right],
\qquad
\sigma_{max}=\frac PA+\frac{M_{max}c}{I}.
$$

As $P\to0$, the bracket expands to $\mu^2L^2/8$ and $M_{max}\to wL^2/8$, the ordinary beam moment; the axial load amplifies it ([[Beam-Column]]). Two checks are needed: the combined stress in the bending plane, and Euler buckling about the weak axis, where the transverse load does not act (slide 50 hint).

## 5. Design problems are nonlinear

The lecture's design example is a pet toy: a cantilever post with an overhang from which a treat hangs, carrying the 25 kg dog at the overhang's tip, so the load is eccentric (2026-04-24, ll. 501–640; 2026-04-30, ll. 1–30). With a factor of safety of 4 on the compressive strength, the allowable stress is a quarter of it, and the secant formula has to be solved for the side $b$ of a solid square section. Because $b$ appears inside $\sec\mu L$ through $A$, $I$ and $\kappa$, there is no closed-form answer: tabulate $\sigma_{max}$ against $b$ (in Excel, starting from 100 mm and reducing), plot it, and read off where it reaches the allowable value, or use bisection. For a rectangle, use the smaller $I$.

> [!warning] Lecture slip (2026-04-24, ll. 521–530)
> The dog's weight is given as 25 kg on the slide but read out as "25 kilonewton". The load is $25\times9.81=245$ N.

## Worked examples

Steel throughout, $E=200$ GPa, $\sigma_Y=250$ MPa; all recomputed in Python (2026-04-30, ll. 1–100).

### Eccentric load on the hollow circular column

The 3 m cantilever column of [[SESA2028 S5 - Euler Buckling and Effective Length#Worked example: two columns|S5]] ($D_o=100$, $D_i=80$ mm; $A=2827$ mm², $I=2.898\times10^6$ mm⁴, $\kappa=32.0$ mm) buckled at 158.9 kN with a central load. With the load 10 mm off-centre, solve

$$
\frac{P}{2827}\left[1+\frac{10\times50}{32.0^2}\sec\left(\sqrt{\frac{P}{200\,000\times2.898\times10^6}}\times3000\right)\right]=250
$$

for $P$ by bisection: $P=136$ kN, at which the tip has deflected 76 mm. A 10 mm eccentricity costs 14 % of the load capacity.

### Initially curved hollow square column

The pinned 75 × 5 mm square column of S5 ($A=1400$ mm², $\kappa=28.7$ mm, $P_{cr}=252$ kN) carries 120 kN with an initial bow of 0.5 % of its length, $a=15$ mm (slide 37). Then $P/P_{cr}=0.476$ and

$$
\sigma_{max}=85.7\left[1+\frac{15\times37.5}{28.7^2}\cdot\frac{1}{1-0.476}\right]=198\text{ MPa},
$$

131 % above the 85.7 MPa of the straight column, leaving a safety factor of only 1.26 against yield.

### Beam-column I-section

A 4 m simply supported I-beam, 254 mm deep with 146 mm flanges, all walls 6 mm, carries 4 kN/m plus its own weight and an axial compression of 200 kN (slide 50). Then $A=3204$ mm², $I_z=3.40\times10^7$ mm⁴ (strong) and $I_y=3.12\times10^6$ mm⁴ (weak), and self-weight adds $7850\times9.81\times3204\times10^{-9}=0.25$ N/mm. In the bending plane, $\mu=\sqrt{P/EI_z}$ and

$$
M_{max}=\frac{4.25}{\mu^2}\left[\sec\frac{\mu L}{2}-1\right]=8.93\text{ kN m}
$$

against 8.49 kN m without the axial load, so

$$
\sigma_{max}=\frac{200\,000}{3204}+\frac{8.93\times10^6\times127}{3.40\times10^7}=95.7\text{ MPa},
$$

a safety factor of 2.61 against yield. About the weak axis, $P_{cr}=\pi^2EI_y/L^2=384$ kN, a factor of only 1.92, which governs.

## 6. Plate buckling

Plate buckling of skin panels between stiffeners has slides in the folder from an earlier version of the course (`SL13 Buckling 5 - Plate Buckling.pdf`), but it was not lectured in 2025–26; local skin buckles were only shown as photographs in SL13 ([[SESA2028 S5 - Euler Buckling and Effective Length#1. Stability and equilibrium|S5]]). The concept note [[Plate Buckling]] keeps the background.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S5 - Euler Buckling and Effective Length]]
- Next: [[SESA2028 S7 - Strain Energy and Conservation of Energy]]
- Concepts: [[Secant Formula]] · [[Beam-Column]] · [[Beam-Column Amplification]] · [[Plate Buckling]] · [[Plate Buckling Coefficient]]

![[structures_beam_column_amplification.png|720]]

## Sources

- Structures slides `SL7 buckling of beams with imperfection.pdf` (examples on slides 23, 37 and 50), with transcripts `SESA2028 Lecture 2026-04-24.txt` (ll. 200–660), the two buckling tutorials of 2026-04-27 and `SESA2028 Lecture 2026-04-30.txt` (ll. 1–100)
- Examples recomputed in Python (bisection with SciPy)

## Self-study tasks

### Core

- [ ] Derive the secant formula for an eccentrically loaded cantilever column (2026-04-24, ll. 241–440). → [[#2. Eccentric load: the secant formula]]
- [ ] Watch the mini-lectures and derive the initially curved and laterally loaded cases with the same four steps (ll. 441–500). → [[#3. Initially curved column]] · [[#4. Laterally loaded column (beam-column)]]
- [ ] The three slide problems: eccentric hollow circle, curved hollow square, beam-column I-section (2026-04-30, ll. 1–100). → [[#Worked examples]]
- [ ] Structures tutorial 4, Q1–Q4 (tutorials 2026-04-27). → [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q3 - Water-filled C-channel beam-column|Q3]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q4.1 - Pin-ended column under a midspan transverse load|Q4.1]]

### Further practice

- [ ] Size the pet-toy post by a graphical or bisection solution of the secant formula (ll. 501–640; supply your own $E$, strength and dimensions). → [[#5. Design problems are nonlinear]]
