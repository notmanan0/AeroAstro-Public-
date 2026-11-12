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
sources: ["02 - Sources/Structures Lectures/SL7 buckling of beams with imperfection.pdf", "02 - Sources/Structures Lectures/Structures Additional session_buckling.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-24.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-27 - 0901.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-27 - 1400.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-30.txt"]
---

# SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling

> [!abstract] Summary
> Real columns are never perfect: an eccentric load, an initial curvature or a lateral load makes them bend from the first increment of load, so there is no clean bifurcation, and deflection and stress grow faster and faster as the load approaches the Euler load. For an eccentric load the result is the secant formula, $\sigma_{max}=\frac PA\left[1+\frac{ec}{\kappa^2}\sec\mu L_e\right]$; for an initial bow the bow is amplified by $1/(1-P/P_{cr})$; for a lateral load the bending moment is amplified in the same way. Because $\mu$ depends on $P$ and on the section, design problems such as finding a section size are nonlinear and are solved graphically or by bisection.

> [!summary]- Exam use: quick path
> - **Use it when:** a compression member has an eccentric load, an initial crookedness or a transverse load as well.
> - **Assumptions:** linear elastic, small deflections, $\mu^2=P/EI$, failure when the extreme-fibre compressive stress reaches $\sigma_Y$ (or an allowable stress with a safety factor).
> - **Method:** 1. Section properties, $\kappa^2=I/A$, $c$. 2. Identify the case and its formula. 3. Eccentric: $\sigma_{max}=\frac PA[1+\frac{ec}{\kappa^2}\sec\mu L]$ (fixed–free; $\mu L/2$ for pinned). 4. Curved: $\sigma_{max}=\frac PA[1+\frac{ac}{\kappa^2}\frac1{1-P/P_{cr}}]$. 5. Lateral load: $\sigma_{max}=\frac PA+\frac{M_{max}c}{I}$ with the amplified moment, and check Euler buckling about the weak axis too.
> - **Common mistakes:** using the secant formula with $e=0$ (it then says nothing; use Euler); checking only the bending plane and not weak-axis buckling.
> - **Practise:** [[#Worked examples]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q2 - Permissible initial curvature of a control rod|Tutorial 4 Q2]]

The perfect column of [[SESA2028 S5 - Euler Buckling and Effective Length|S5]] stays straight up to $P_{cr}$ and then bifurcates. A column with a small initial curvature behaves differently: it deflects from the start, never reaches a bifurcation point, and fails below $P_{cr}$.

Pressing the ends of a slightly bent drinking straw makes the bend grow at once, because the load's line of action misses the bent middle and so applies a bending moment there. The extra bend moves the middle further from that line, which increases the moment again. Far below the Euler load this feedback is weak; near it, each extra bit of bending generates nearly as much again, and the deflection runs away. An eccentric load, a crooked column and a side load all start that feedback in different ways, and the analysis of each follows the same four steps.

## 1. The four-step method

Every case follows the steps used for the perfect column:

1. draw the deflected shape and take a cut;
2. write the moment at the cut from equilibrium, including $P$ times the lateral offset;
3. substitute $M=-EIv''$ to get the governing equation;
4. solve it (complementary function plus particular integral) and fix the constants from the boundary conditions.

## 2. Eccentric load: the secant formula

A column of length $L$ is clamped at its base and free at its top, where a load $P$ acts at eccentricity $e$ from the axis. Measure $x$ down from the top, with $v(x)$ the lateral deflection and $a=v(0)$ the unknown tip deflection. At a cut at $x$, the load's lever arm about the section is $e+a-v$, so

$$
M(x)=P\left(e+a-v\right).
$$

With $M=-EIv''$ in the sense that bends the column further, and $\mu^2=P/EI$,

$$
EI\frac{d^2v}{dx^2}=P(e+a-v)\quad\Longrightarrow\quad\frac{d^2v}{dx^2}+\mu^2v=\mu^2(e+a).
$$

The general solution is the complementary function plus the constant particular integral, $v_p=e+a$:

$$
v=A\sin\mu x+B\cos\mu x+e+a .
$$

At the top, $v(0)=a$:

$$
B+e+a=a\quad\Longrightarrow\quad B=-e .
$$

At the clamped base the slope is zero, $v'(L)=0$:

$$
A\mu\cos\mu L-B\mu\sin\mu L=0\quad\Longrightarrow\quad A=B\tan\mu L=-e\tan\mu L .
$$

At the base the deflection is zero, $v(L)=0$:

$$
-e\tan\mu L\sin\mu L-e\cos\mu L+e+a=0 .
$$

Combine the first two terms over $\cos\mu L$:

$$
e\,\frac{\sin^2\mu L+\cos^2\mu L}{\cos\mu L}=e\sec\mu L .
$$

So $-e\sec\mu L+e+a=0$, and

$$
v_{max}=a=e\left(\sec\mu L-1\right).
$$

The largest moment is at the base, where the lever arm is $e+a$:

$$
M_{max}=P(e+a)=Pe\sec\mu L .
$$

The largest compressive stress adds the axial and bending parts at the extreme fibre $c$; with $I=A\kappa^2$,

$$
\sigma_{max}=\frac PA+\frac{Pe\sec\mu L\;c}{I}=\frac PA\left[1+\frac{ec}{\kappa^2}\sec\mu L\right].
$$

This is the secant formula ([[Secant Formula]]). A pinned column of length $L$ under an eccentric load deflects symmetrically, and each half behaves like a cantilever of length $L/2$ clamped at midspan, so $\mu L$ is replaced by $\mu L/2$.

As $P\to P_{cr}$, $\mu L\to\pi/2$ for the cantilever, $\sec\mu L\to\infty$, and so do the deflection and the stress. The formula needs $e>0$; with $e=0$ it gives $v=0$ at every load below $P_{cr}$ and the Euler formula applies instead. Plotted against $P$, $v_{max}$ starts rising immediately and bends over towards the Euler load asymptotically, more gradually for a larger eccentricity: there is no bifurcation.

> [!check] The small-load limit
> For small $\mu L$, $\sec\mu L\approx1+\tfrac12(\mu L)^2$, so $a\approx\tfrac12e\mu^2L^2=\dfrac{(Pe)L^2}{2EI}$: the tip deflection of a cantilever under an end moment $Pe$, as ordinary beam theory gives when the axial load is too small to amplify anything.

![[structures_s6_secant_and_sizing.png|900]]

## 3. Initially curved column

A pinned column has an initial bow $v_0=a\sin(\pi x/L)$, with no stress in it. Under $P$ it deflects a further $v_1$. The moment uses the total offset from the line of action, but only the extra deflection $v_1$ produces curvature from the unstressed shape:

$$
M=P\left(v_0+v_1\right),\qquad EI\frac{d^2v_1}{dx^2}=-P\left(v_0+v_1\right).
$$

Divide by $EI$ and rearrange:

$$
\frac{d^2v_1}{dx^2}+\mu^2v_1=-\mu^2a\sin\frac{\pi x}{L}.
$$

Try $v_1=C\sin(\pi x/L)$, which already satisfies $v_1(0)=v_1(L)=0$. Then $v_1''=-(\pi/L)^2C\sin(\pi x/L)$, and substituting,

$$
\left(-\frac{\pi^2}{L^2}+\mu^2\right)C=-\mu^2a\quad\Longrightarrow\quad C=\frac{\mu^2a}{\pi^2/L^2-\mu^2}.
$$

Divide top and bottom by $\pi^2/L^2$ and use $\mu^2L^2/\pi^2=P/P_{cr}$:

$$
C=\frac{a\,P/P_{cr}}{1-P/P_{cr}}.
$$

The total midspan offset is

$$
a+C=a\left[1+\frac{P/P_{cr}}{1-P/P_{cr}}\right]=\frac{a}{1-P/P_{cr}},
$$

the initial bow amplified by $1/(1-P/P_{cr})$ ([[Beam-Column Amplification]]). The largest moment, at midspan, is $P$ times this offset, so

$$
\sigma_{max}=\frac PA+\frac{P\,a\,c}{I\left(1-P/P_{cr}\right)}=\frac PA\left[1+\frac{ac}{\kappa^2}\cdot\frac{1}{1-P/P_{cr}}\right].
$$

At half the Euler load the bow has doubled; at 90 % it is ten times its initial value.

![[structures_beam_column_amplification.png|640]]

## 4. Laterally loaded column (beam-column)

A pinned column of length $L$ carries an axial load $P$ and a uniform transverse load $w$. The moment at $x$ now has a beam part and an axial part:

$$
M=\frac{wx(L-x)}{2}+Pv .
$$

With $M=-EIv''$ and $\mu^2=P/EI$:

$$
\frac{d^2v}{dx^2}+\mu^2v=-\frac{w}{2EI}\left(Lx-x^2\right).
$$

### Particular integral

The right-hand side is a quadratic, so try $v_p=\alpha x^2+\beta x+\gamma$, with $v_p''=2\alpha$:

$$
2\alpha+\mu^2\left(\alpha x^2+\beta x+\gamma\right)=-\frac{w}{2EI}\left(Lx-x^2\right).
$$

Match the $x^2$ terms: $\mu^2\alpha=w/2EI$, so $\alpha=w/2P$. Match the $x$ terms: $\mu^2\beta=-wL/2EI$, so $\beta=-wL/2P$. Match the constants: $2\alpha+\mu^2\gamma=0$, so $\gamma=-w/(P\mu^2)$. Hence

$$
v_p=-\frac{w}{2P}x(L-x)-\frac{w}{P\mu^2}.
$$

### Constants and the midspan moment

The full solution is $v=A\sin\mu x+B\cos\mu x+v_p$. At $x=0$, $v=0$:

$$
B-\frac{w}{P\mu^2}=0\quad\Longrightarrow\quad B=\frac{w}{P\mu^2}.
$$

At $x=L$, $v=0$:

$$
A\sin\mu L+B\cos\mu L-\frac{w}{P\mu^2}=0\quad\Longrightarrow\quad A=B\,\frac{1-\cos\mu L}{\sin\mu L}=B\tan\frac{\mu L}{2},
$$

using $1-\cos\mu L=2\sin^2\tfrac{\mu L}2$ and $\sin\mu L=2\sin\tfrac{\mu L}2\cos\tfrac{\mu L}2$. So

$$
v=\frac{w}{P\mu^2}\left[\tan\frac{\mu L}{2}\sin\mu x+\cos\mu x-1\right]-\frac{w}{2P}x(L-x).
$$

At midspan, $\tan\tfrac{\mu L}2\sin\tfrac{\mu L}2+\cos\tfrac{\mu L}2=\sec\tfrac{\mu L}2$, so

$$
v_{max}=\frac{w}{P\mu^2}\left[\sec\frac{\mu L}{2}-1\right]-\frac{wL^2}{8P}.
$$

The midspan moment is the beam moment $wL^2/8$ plus $Pv_{max}$, and the $wL^2/8$ terms cancel:

$$
M_{max}=\frac{wL^2}{8}+Pv_{max}=\frac{w}{\mu^2}\left[\sec\frac{\mu L}{2}-1\right],\qquad\sigma_{max}=\frac PA+\frac{M_{max}c}{I}.
$$

> [!check] Without the axial load
> As $P\to0$, $\sec\tfrac{\mu L}2-1\approx\tfrac12\left(\tfrac{\mu L}2\right)^2=\mu^2L^2/8$, so $M_{max}\to wL^2/8$, the ordinary beam moment; the next term of the expansion recovers $v_{max}\to5wL^4/384EI$. The axial load only amplifies what the transverse load starts ([[Beam-Column]]).

Two checks are needed for a beam-column: the combined stress in the bending plane, and Euler buckling about the weak axis, where the transverse load does not act.

## 5. Design problems are nonlinear

Sizing a member with these formulae is awkward because the unknown dimension appears inside $\sec\mu L$, through $A$, $I$ and $\kappa$. There is no closed-form answer, so the equation is solved by plotting $\sigma_{max}$ against the dimension (in Excel, say) and reading off where it reaches the allowable value, or by bisection. A safe starting guess matters: if the trial section is too small, $\mu L$ passes $\pi/2$ and the secant formula gives meaningless (negative or infinite) stresses, so start large, around 100 mm, and work down.

### The dog-toy post

A toy keeps a treat out of a dog's reach: a solid square timber post, fixed at the base and 1.8 m tall, with a 0.5 m overhang from which the treat hangs on a rope. The worst case is the 25 kg dog hanging fully off the ground from the treat, so the post carries $P=25\times9.81=245$ N at an eccentricity $e=0.5$ m. The timber is C16 with $E=8.8$ GPa and a compressive failure stress of 17 MPa; with a safety factor of 4 the allowable stress is $17/4=4.25$ MPa. Self-weight is neglected. What side $b$ is needed?

For a solid square, $A=b^2$, $I=b^4/12$, $\kappa^2=I/A=b^2/12$ and $c=b/2$, so

$$
\frac{ec}{\kappa^2}=\frac{e\,(b/2)}{b^2/12}=\frac{6e}{b},\qquad\mu L=L\sqrt{\frac{12P}{Eb^4}}.
$$

The equation to solve is

$$
\frac{245}{b^2}\left[1+\frac{6\times500}{b}\sec\left(1800\sqrt{\frac{12\times245}{8800\,b^4}}\right)\right]=4.25 .
$$

Bisection: $b=50$ mm gives 6.53 MPa (too high), $b=70$ mm gives 2.24 MPa (too low), $b=60$ mm gives 3.62 MPa (too low), and the interval closes on

$$
b=57\text{ mm}.
$$

> [!check] What governs the post
> At $b=57$ mm, $\mu L=0.32$ and $\sec\mu L=1.05$, while the Euler load of the post is $\pi^2EI/(2L)^2=5.9$ kN, 24 times the dog's weight. The axial stress is only $245/57^2=0.075$ MPa; almost all of the 4.25 MPa is bending from the 0.5 m overhang, and the secant amplification adds just 5 %. This post is designed by eccentric bending, not by buckling.

## Worked examples

Steel throughout, $E=200$ GPa and $\sigma_Y=250$ MPa.

### Eccentric load on the hollow circular column

The 3 m cantilever column of [[SESA2028 S5 - Euler Buckling and Effective Length#Hollow circular cantilever column|S5]] ($D_o=100$, $D_i=80$ mm; $A=2827$ mm², $I=2.898\times10^6$ mm⁴, $\kappa=32.0$ mm, $c=50$ mm) buckled at 158.9 kN under a central load. With the load 10 mm off-centre, first yield occurs when

$$
\frac{P}{2827}\left[1+\frac{10\times50}{32.0^2}\sec\left(3000\sqrt{\frac{P}{200\,000\times2.898\times10^6}}\right)\right]=250 .
$$

Solving by bisection gives $P=136$ kN, at which $\mu L=1.45$, $\sec\mu L=8.6$ and the tip has deflected $a=10(8.6-1)=76$ mm. A 10 mm eccentricity, a tenth of the diameter, costs 14 % of the load capacity.

### Initially curved hollow square column

The pinned 75 × 5 mm square column of S5 ($A=1400$ mm², $\kappa=28.7$ mm, $c=37.5$ mm, $P_{cr}=252$ kN) carries 120 kN with an initial bow of 0.5 % of its length, $a=15$ mm. Then $P/P_{cr}=0.476$ and the amplification is $1/(1-0.476)=1.91$:

$$
\sigma_{max}=85.7\left[1+\frac{15\times37.5}{28.7^2}\times1.91\right]=85.7\times2.31=198\text{ MPa}.
$$

That is 131 % above the 85.7 MPa of the straight column, leaving a safety factor of only $250/198=1.26$ against yield, compared with 2.10 against buckling for the straight column. Setting $\sigma_{max}=250$ MPa and solving for $P$ gives first yield at 139 kN, 55 % of the Euler load.

### Beam-column I-section

A 4 m simply supported I-beam, 254 mm deep with 146 mm flanges, all walls 6 mm thick, carries 4 kN/m plus its own weight and an axial compression of 200 kN. Check it against yield and buckling.

The section properties are

$$
A=2\times146\times6+242\times6=3204\text{ mm}^2,
$$

$$
I_z=\frac{146\times254^3-140\times242^3}{12}=3.40\times10^7\text{ mm}^4,\qquad I_y=\frac{2\times6\times146^3+242\times6^3}{12}=3.12\times10^6\text{ mm}^4 .
$$

Self-weight adds $7850\times9.81\times3204\times10^{-9}=0.25$ N/mm, so $w=4.25$ N/mm. In the bending plane, $\mu=\sqrt{P/EI_z}=\sqrt{200\,000/(200\,000\times3.40\times10^7)}=1.71\times10^{-4}$ mm⁻¹ and $\mu L/2=0.343$:

$$
M_{max}=\frac{4.25}{\mu^2}\left[\sec0.343-1\right]=8.93\text{ kN m},
$$

against $wL^2/8=8.49$ kN m without the axial load. The peak stress is

$$
\sigma_{max}=\frac{200\,000}{3204}+\frac{8.93\times10^6\times127}{3.40\times10^7}=62.4+33.3=95.7\text{ MPa},
$$

a safety factor of 2.61 against yield. About the weak axis, where nothing bends the beam,

$$
P_{cr}=\frac{\pi^2EI_y}{L^2}=\frac{\pi^2\times200\,000\times3.12\times10^6}{4000^2}=384\text{ kN},
$$

a factor of only $384/200=1.92$, which governs.

> [!check] The amplification shortcut
> In the bending plane $P_{cr,z}=\pi^2EI_z/L^2=4.20$ MN, so $P/P_{cr,z}=0.048$ and $wL^2/8\times1/(1-0.048)=8.49\times1.050=8.92$ kN m, within 0.2 % of the exact 8.93 kN m. The simple amplification factor is a good estimate when the transverse load's deflected shape is close to a half sine.

## 6. Plate buckling

Plate buckling of skin panels between stiffeners was not lectured in 2025–26. Slides from an earlier version of the course exist (`SL13 Buckling 5 - Plate Buckling.pdf`), and local skin buckles appear only as photographs ([[SESA2028 S5 - Euler Buckling and Effective Length#Why buckling matters|S5]]). The concept note [[Plate Buckling]] gives the background.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S5 - Euler Buckling and Effective Length]] · Next: [[SESA2028 S7 - Strain Energy and Conservation of Energy]]
- Concepts: [[Secant Formula]] · [[Beam-Column]] · [[Beam-Column Amplification]] · [[Plate Buckling]] · [[Plate Buckling Coefficient]]
- Problems: [[SESA2028 Structures Tutorial 4 - Buckling Solutions]] · Formulae: [[SESA2028 Formula Sheet]]

## Sources

- Slides: `SL7 buckling of beams with imperfection.pdf` (eccentric, initially curved and laterally loaded columns; examples on slides 23, 37 and 50) and `Structures Additional session_buckling.pdf` (the dog-toy post with full data and the bisection, slides 18–24).
- Transcripts: `SESA2028 Lecture 2026-04-24.txt` (ll. 200–660), the two buckling tutorials of 2026-04-27 (`… - 0901.txt`, `… - 1400.txt`) and `SESA2028 Lecture 2026-04-30.txt` (ll. 1–100).
- All examples recomputed in Python (bisection with SciPy `brentq`); the beam-column particular integral checked symbolically. Figures: `generate_structures_s6_figures.py` and `generate_structures_figures.py` (amplification factor).

## Self-study tasks

### Core

- [ ] Derive the secant formula for an eccentrically loaded cantilever column (2026-04-24, ll. 241–440). → [[#2. Eccentric load: the secant formula]]
- [ ] Watch the mini-lectures and derive the initially curved and laterally loaded cases with the same four steps (2026-04-24, ll. 441–500). → [[#3. Initially curved column]] · [[#4. Laterally loaded column (beam-column)]]
- [ ] The three slide problems: eccentric hollow circle, curved hollow square, beam-column I-section (SL7 slides 23, 37, 50; 2026-04-30, ll. 1–100). → [[#Worked examples]]
- [ ] Size the dog-toy post by plotting or bisecting the secant formula (2026-04-24, ll. 501–640; 2026-04-30, ll. 1–30). → [[#The dog-toy post]]
- [ ] Structures tutorial 4, Q1–Q4 (tutorials 2026-04-27). → [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q2 - Permissible initial curvature of a control rod|Q2]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q3 - Water-filled C-channel beam-column|Q3]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q4.1 - Pin-ended column under a midspan transverse load|Q4.1]]

### Further practice

- [ ] Find the load at which the curved square column first yields (139 kN) and compare it with $P_{cr}$ (suggested, not lecturer-set). → [[#Initially curved hollow square column]]
- [ ] Show that the beam-column midspan deflection tends to $5wL^4/384EI$ as $P\to0$ (suggested, not lecturer-set). → [[#Constants and the midspan moment]]

## Transcript and slide slips

> [!warning] Transcript slip (2026-04-24, ll. 521–530)
> Where: [[#The dog-toy post]].
>
> The dog's weight is given as 25 kg on the slide but read out as "25 kilonewton". The load is $25\times9.81=245$ N.
