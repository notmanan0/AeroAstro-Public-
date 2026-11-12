---
title: "SESA1015 M12 - Aircraft Constraint Analysis"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 12
tags:
  - sesa1015
  - mechanics-of-flight
  - constraint-analysis
  - aircraft-design
  - wing-loading
aliases: ["SESA1015 Mechanics 12", "Aircraft Sizing Constraints", "Constraint Diagram"]
date: 2026-09-27
status: lectured
coverage: "Constraint analysis: thrust to weight ratio against wing loading for a constant-velocity turn, climb at a given rate, take-off ground run, approach (stall) speed and level-flight (cruise) speed; the feasible region and the design point; the course spreadsheet for a 15 kg UAV reproduced; ceiling and refined take-off forms added from the same equations of motion. Slides v2 pp. 180–181, Slides v1 pp. 91, 102, 191, 220–225, Constraint Analysis spreadsheet."
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]", "[[SESA1015 M08 - Glide and Climb Performance]]", "[[SESA1015 M09 - Take-off and Landing Performance]]", "[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
next_topics: []
key_concepts: ["[[Aircraft Constraint Diagram]]", "[[Thrust-to-Weight Ratio]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]", "[[Take-off Ground Run]]", "[[Load Factor and Turn Performance]]"]
tutorial_sheets: ["[[SESA1015 T08 - Constraint Analysis Solutions]]", "[[SESA1015 T02 - Take-off and Landing Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 180–181)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides.pdf (older deck, pp. 91, 102, 191, 220–225)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Constraint Analysis.xlsx", "04 - Labs & Coursework/constraint_analysis_simplified.xlsx (identical copy)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§4.2, §4.3, §7.2–7.4)"]
---

# SESA1015 M12 - Aircraft Constraint Analysis

> [!abstract] Summary
> Every performance requirement (take-off run, climb rate, turn load factor, cruise speed, approach speed) can be rewritten as an inequality between two ratios, the thrust to weight ratio $T/W$ and the wing loading $W/S$. Drawn on one $T/W$ against $W/S$ plane, the approach (stall) requirement is a vertical line that caps $W/S$, the simple take-off requirement is a horizontal line, and cruise, turn and climb are U-shaped curves $T/W=qC_{D0}/(W/S)+Kn^2(W/S)/q\,(+V_V/V)$. The feasible region lies above every curve and to the left of the stall line; the design point is normally its lowest corner at the highest allowed wing loading, which fixes the wing area $S=W/(W/S)$ and the installed thrust $T=W(T/W)$ in one step.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a runway length and $V_2$, a turn load factor, a climb rate or a cruise speed together with a drag polar, and asks for the minimum $T/W$, the wing loading where two constraints meet, or the maximum wing loading for an approach speed.
> - **Assumptions:** parabolic polar $C_D=C_{D0}+KC_L^2$; steady flight with $L=nW$ in a level turn and $L\approx W$ in a shallow climb; take-off with $T/W$ constant and $L/W$, $D/W$ negligible on the ground run; all constraints referred to the same weight and the same thrust (sea level, low-altitude UAV, so no lapse correction unless stated); $W/S$ in N/m².
> - **Method:** 1. Take-off: $T/W=V_2^2/(2gs_1)+\mu$. 2. Approach: $W/S\leq\frac12\rho V_s^2C_{L\max}$. 3. Manoeuvre curve: $T/W=V_V/V+qC_{D0}/x+Kn^2x/q$ with $q=\frac12\rho V^2$. 4. Where two meet, multiply by $x$ and solve the quadratic $\frac{Kn^2}{q}x^2-\big(\frac TW-\frac{V_V}{V}\big)x+qC_{D0}=0$. 5. Take the root the question asks for (usually the lower one) and check it against the stall line.
> - **Common mistakes:** putting $V_V/V$ on the wrong side when forming the climb quadratic; reading the axis of the typical-constraints plot as N/m² when its numbers are kg/m² (factor 9.81).
> - **Practise:** [[#Constraint chart for a 15 kg UAV]] · [[SESA1015 T08 - Constraint Analysis Solutions#Question 35]]

Each performance requirement has its own formula: the take-off run from the wing loading, lift coefficient and thrust (M09), the turn radius from the load factor (M10), the climb rate from the specific excess thrust (M08), the level-flight speeds from the drag polar (M04, M05). A designer has all of these requirements at once and two main choices to make: how big a wing to give the aircraft for its weight, and how much thrust to install. Iterating each formula separately until all are satisfied is slow. Constraint analysis puts them on one chart.

The two axes are chosen because they are what the requirements actually depend on. For a fixed flight condition the lift coefficient needed is set by $W/S$ alone, so wing loading measures how hard the wing has to work, and thrust to weight ratio measures how much force is available per newton of aircraft to overcome drag, climb or accelerate. Weight and size then drop out: two aircraft of different mass with the same $W/S$, $T/W$ and drag polar have the same take-off run, climb rate and turn radius.

On this plane each requirement becomes a boundary with an acceptable side. A low wing loading (large wing) makes the low-speed requirements easy, since landing and stall speeds are low, but it makes the cruise expensive, because a large wing carries a lot of zero-lift drag at cruise dynamic pressure. A high wing loading (small wing) does the opposite. The thrust needed for cruise, turn and climb therefore falls steeply as $W/S$ rises from small values, passes a minimum and rises again, while the approach speed puts a hard ceiling on $W/S$. The design point is the cheapest one that satisfies every boundary.

![[mof_m12_design_space.png|900]]

## 1. The design plane and its two ratios

Write $x=W/S$ for the wing loading (N/m²) and $y=T/W$ for the thrust to weight ratio (dimensionless). The link between wing loading and aerodynamics is the lift equation. In a steady condition with load factor $n=L/W$ at dynamic pressure $q=\frac12\rho V^2$,

$$
L=qSC_L .
$$

Substituting $L=nW$,

$$
nW=qSC_L,
$$

and dividing by $qS$,

$$
\boxed{C_L=\frac{n}{q}\,\frac WS} .
$$

With the parabolic drag polar of [[Parabolic Drag Polar|M03]],

$$
C_D=C_{D0}+KC_L^2,\qquad K=\frac{1}{\pi eAR},
$$

the drag at that condition is

$$
D=qSC_D=qS\left[C_{D0}+K\left(\frac nq\,\frac WS\right)^2\right].
$$

Dividing by $W$ turns $S/W$ into $1/x$:

$$
\frac DW=\frac{qC_{D0}}{W/S}+\frac{Kn^2}{q}\,\frac WS .
$$

This one expression drives three of the five constraints. The first term is the zero-lift (profile) drag per unit weight and falls as $1/x$; the second is the induced drag per unit weight and grows linearly in $x$. A requirement that fixes $q$ (a cruise or turn speed) and $n$ turns it into a curve on the $x$–$y$ plane.

$K$ follows from the aspect ratio $AR$ with an empirical Oswald efficiency (course spreadsheet),

$$
e_0=1.78\left(1-0.045AR^{0.68}\right)-0.64,
$$

which for $AR=9$ gives $e_0=0.7831$ and $K=1/(\pi\times9\times0.7831)=0.04516$ (cells C42, C43).

## 2. Stall and approach constraint

At the stall the lift coefficient is $C_{L\max}$ and, in level flight, $L=W$ at the stalling speed $V_s$ (course notes §4.2, p. 19):

$$
W=\tfrac12\rho V_s^2SC_{L\max}.
$$

Dividing by $S$,

$$
\frac WS=\tfrac12\rho V_s^2C_{L\max}.
$$

For a required stalling speed, any larger wing loading would stall at a higher speed than allowed. The requirement is therefore an upper limit (Slides v1, p. 223):

$$
\boxed{\frac WS\leq\tfrac12\rho V_s^2C_{L\max}=q_sC_{L\max}}
$$

This does not involve $T/W$ at all, so on the diagram it is a vertical line, with the feasible side to the left. The $C_{L\max}$ is the one for the configuration in which the speed limit applies: for an approach constraint it is the landing configuration with flaps and slats out (DC-9: about 1.2 clean, 2.5–3.0 with high-lift devices, Slides v1, p. 91).

An approach speed is flown with a margin above the stall, $V_{app}=f\,V_s$. The factor is $f=1.1$ (StallReserveFactor in the spreadsheet), so the stall speed that enters the constraint is

$$
V_s=\frac{V_{app}}{1.1}.
$$

Some revision questions instead put the approach speed straight into $q$ (Revision Q39); read which speed the question gives before using it.

A landing field length leads to the same vertical line. On the landing roll with $T=0$ and $L=0$ (Slides v2, p. 181; this is not strictly true) and drag neglected, the equation of motion

$$
\frac TW-\frac DW-\mu\left(1-\frac LW\right)=\frac Vg\,\frac{dV}{dx}
$$

reduces to

$$
-\mu=\frac Vg\,\frac{dV}{dx}.
$$

Separating and integrating from the touchdown speed $V_{TD}$ down to rest over the roll $s_L$,

$$
\begin{aligned}
-\mu\int_0^{s_L}dx&=\frac1g\int_{V_{TD}}^0V\,dV\\
-\mu s_L&=-\frac{V_{TD}^2}{2g}\\
s_L&=\frac{V_{TD}^2}{2g\mu}.
\end{aligned}
$$

A maximum roll fixes a maximum $V_{TD}$, a fixed ratio $V_{TD}/V_s$ then fixes a maximum $V_s$, and the inequality above turns it into a maximum $W/S$.

## 3. Cruise (level-flight speed) constraint

In steady level flight $n=1$ and thrust equals drag (course notes §4.3, p. 21), so the thrust to weight ratio needed to hold a given speed is $D/W$. Starting from the drag (Slides v1, pp. 102 and 224),

$$
\begin{aligned}
\frac TW&=\frac DW=\frac1W\left[\tfrac12\rho V^2S\left(C_{D0}+KC_L^2\right)\right]\\
&=qC_{D0}\,\frac{1}{W/S}+qkC_L^2\,\frac{1}{W/S}.
\end{aligned}
$$

In level flight $C_L=W/(qS)$, so

$$
qkC_L^2\,\frac{1}{W/S}=qk\left(\frac{W/S}{q}\right)^2\frac{1}{W/S}=\frac kq\,\frac WS ,
$$

and

$$
\boxed{\frac TW=\frac{qC_{D0}}{W/S}+\frac kq\,\frac WS}\qquad\text{(cruise at }q=\tfrac12\rho V^2\text{)}
$$

### The minimum of the curve

The curve has a minimum because one term falls and the other rises. Differentiating with respect to $x=W/S$ at fixed $q$,

$$
\frac{d}{dx}\left(\frac TW\right)=-\frac{qC_{D0}}{x^2}+\frac kq .
$$

Setting this to zero,

$$
\begin{aligned}
\frac{qC_{D0}}{x^2}&=\frac kq\\
x^2&=\frac{q^2C_{D0}}{K}\\
x^*&=q\sqrt{\frac{C_{D0}}{K}} .
\end{aligned}
$$

The second derivative $2qC_{D0}/x^3$ is positive, so this is a minimum. Substituting back,

$$
\begin{aligned}
\left(\frac TW\right)_{\min}&=\frac{qC_{D0}}{q\sqrt{C_{D0}/K}}+\frac kq\,q\sqrt{\frac{C_{D0}}K}\\
&=\sqrt{KC_{D0}}+\sqrt{KC_{D0}}\\
&=2\sqrt{KC_{D0}} .
\end{aligned}
$$

At $x^*$ the cruise lift coefficient is $C_L=x^*/q=\sqrt{C_{D0}/K}$, the minimum-drag lift coefficient of [[SESA1015 M05 - Minimum Drag, Power and Performance Curves|M05]], and $2\sqrt{KC_{D0}}=1/(L/D)_{\max}$. The bottom of the cruise curve is therefore the wing loading at which the given cruise speed is the minimum-drag speed, and there the thrust needed is just $W/(L/D)_{\max}$. At lower wing loading the wing is oversized and profile drag dominates; at higher wing loading the wing flies at a high $C_L$ and induced drag dominates.

![[mof_m12_curve_anatomy.png|900]]

## 4. Turn constraint

The spreadsheet's turn is a constant-velocity, level, co-ordinated turn ("CV turn") at the cruise speed. In such a turn $T=D$, $L\cos\phi=W$ and $L\sin\phi=(W/g)V^2/R$ (course notes §7.4, p. 42), so the load factor and bank angle are linked by

$$
n=\frac LW=\frac1{\cos\phi}.
$$

The lift coefficient needed is $n$ times the level-flight value, $C_L=nW/(qS)$, from Section 1. The thrust equals the drag (Slides v1, p. 220):

$$
T=qSC_D=qS\left\{C_{D0}+K\left(\frac{nW}{qS}\right)^2\right\}.
$$

Dividing by $W$,

$$
\begin{aligned}
\frac TW&=\frac{qC_{D0}}{W/S}+qk\,\frac{n^2}{q^2}\,\frac{W}{S}\\
&=q\left[\frac{C_{D0}}{W/S}+K\left(\frac nq\right)^2\frac WS\right],
\end{aligned}
$$

which is the form used for the constraint curves. Written out,

$$
\boxed{\frac TW=\frac{qC_{D0}}{W/S}+\frac{Kn^2}{q}\,\frac WS}\qquad\text{(level turn at load factor }n\text{)}
$$

With $n=1$ it is the cruise constraint. Only the induced term changes, by the factor $n^2$, so a turn requirement lifts the right-hand branch of the U and leaves the left-hand branch almost untouched. Repeating the minimisation of Section 3 with $K$ replaced by $Kn^2$,

$$
x^*=\frac qn\sqrt{\frac{C_{D0}}{K}},\qquad\left(\frac TW\right)_{\min}=2n\sqrt{KC_{D0}} .
$$

The cruise turn uses $n=1.41$ (n_cvt), a bank angle of $\cos^{-1}(1/1.41)=44.8°$ (cell C48), at the cruise dynamic pressure.

## 5. Climb constraint

In a steady climb at angle $\gamma$ with zero thrust-vector angle (course notes §7.2, p. 37),

$$
T-D=W\sin\gamma,\qquad L=W\cos\gamma .
$$

The rate of climb is the vertical component of the flight speed, so

$$
V_V=V\sin\gamma=\frac{V(T-D)}{W}=V\left(\frac TW-\frac DW\right).
$$

Dividing by $V$ and rearranging for the thrust,

$$
\frac TW=\frac{V_V}{V}+\frac DW .
$$

For a shallow climb $\cos\gamma\approx1$, so $L\approx W$ and $D/W$ is the level-flight value of Section 3 at the climb dynamic pressure $q_{cl}=\frac12\rho V_{cl}^2$ (Slides v1, p. 222):

$$
\boxed{\frac TW=\frac{V_V}{V}+\frac{q\,C_{D0}}{W/S}+\frac kq\,\frac WS}\qquad\text{(climb at rate }V_V\text{ and speed }V\text{)}
$$

The climb rate adds the constant $V_V/V=\sin\gamma$, which shifts the whole curve up. Because the climb is flown slower than the cruise ($V_{cl}=0.8V_{cr}$ in the spreadsheet), $q$ is smaller, so the profile term is smaller at low $W/S$ and the induced term larger at high $W/S$: the climb curve sits below the cruise curve on the far left and well above it on the right (figure in Section 3).

## 6. Ceiling constraint

A ceiling is a climb requirement at altitude. At the absolute ceiling the best achievable climb rate is zero, so the aircraft can only just hold level flight. With the speed free, the least thrust it needs for level flight is at the minimum-drag condition, which from Section 3 is

$$
\left(\frac TW\right)_{\text{at altitude}}=2\sqrt{KC_{D0}}=\frac{1}{(L/D)_{\max}},
$$

independent of wing loading: a horizontal line. A service ceiling is defined by a small residual climb rate (commonly 100 ft/min, 0.508 m/s), which adds $V_V/V$ from Section 5 at the climb speed there. Since the engine produces less thrust in thinner air, the line has to be referred back to the take-off thrust before it shares a diagram with the take-off line. With $T_h=\alpha T_{SL}$ for a thrust lapse $\alpha$ (a first estimate for a jet in the troposphere is $\alpha\approx\sigma$),

$$
\frac{T_{SL}}{W}=\frac1\alpha\left(\frac{T_h}{W}\right)_{\text{required}} .
$$

The service ceiling is 500 ft (152.4 m, spreadsheet cell C21), which the spreadsheet does not plot as a ceiling column. At 152.4 m the ISA density ratio is $\sigma=0.985$, so the ceiling line is at most $0.120$ for this UAV (worked in [[#Constraint chart for a 15 kg UAV]]), far below the take-off line. For a low-flying UAV the ceiling does not bind.

The same referral applies to every curve flown at a weight or thrust different from the take-off reference. If a requirement holds at weight $\beta W_{TO}$ with thrust $\alpha T_{SL}$, writing its curve as $(T/W)_{\text{local}}=f\big((W/S)_{\text{local}}\big)$ and substituting the local values gives

$$
\begin{aligned}
\frac{\alpha T_{SL}}{\beta W_{TO}}&\geq f\!\left(\beta\,\frac{W_{TO}}{S}\right)\\
\frac{T_{SL}}{W_{TO}}&\geq\frac\beta\alpha\,f\!\left(\beta\,\frac{W_{TO}}{S}\right).
\end{aligned}
$$

For the stall line, a landing weight $W_L=\beta W_{TO}$ gives $(W_{TO}/S)\leq q_sC_{L\max}/\beta$. In the spreadsheet every condition is at sea-level density and the design gross weight, so $\alpha=\beta=1$ throughout.

## 7. Take-off constraint

### The simple form

On the ground run, with $\mu$ the rolling coefficient of friction acting on the wheel load $W-L$, the equation of motion along the runway is (course notes §7.3, p. 40; Slides v2, p. 181)

$$
\frac TW-\frac DW-\mu\left(1-\frac LW\right)=\frac1g\,\frac{dV}{dt}=\frac Vg\,\frac{dV}{dx}.
$$

With $T/W$ constant and $L/W$, $D/W$ negligible during the run,

$$
\frac TW-\mu=\frac Vg\,\frac{dV}{dx}.
$$

Separating and integrating from rest to $V_2$ over the ground run $s_1$,

$$
\begin{aligned}
\left(\frac TW-\mu\right)\int_0^{s_1}dx&=\frac1g\int_0^{V_2}V\,dV\\
\left(\frac TW-\mu\right)s_1&=\frac{V_2^2}{2g}\\
s_1&=\frac{V_2^2}{2g\left(\frac TW-\mu\right)} .
\end{aligned}
$$

Solving for the thrust to weight ratio that gives a required run (Slides v1, pp. 191 and 221),

$$
\boxed{\frac TW=\frac{V_2^2}{2gs_1}+\mu}
$$

The first term is the thrust per unit weight that accelerates the aircraft to $V_2$ in the available length; the second is what the wheels absorb. With $V_2$ given directly the line does not depend on $W/S$, so it is horizontal, with the feasible side above. If instead $V_2=1.2V_s$ is tied to the stall, then $V_2^2=1.44\times2(W/S)/(\rho C_{L\max})$ and the boundary becomes the course-notes form $s_1=\frac{1.44}{\rho g}\frac WS\frac{1}{C_{L\max}}\frac{1}{T/W-\mu}$ (course notes p. 41; Slides v2, p. 180), a straight line through $T/W=\mu$ rising with $W/S$:

$$
\frac TW=\mu+\frac{1.44}{\rho gs_1C_{L\max}}\,\frac WS .
$$

### Keeping lift and drag on the ground run

The values $C_{L,TO}=0.97$, $C_{D,TO}=0.0898$ and a take-off dynamic pressure $q_{TO}=\frac12\rho(V_2/\sqrt2)^2$ (spreadsheet cells C34, C35, C46) are not used by the plotted take-off column. They belong to the form in which lift and drag stay in the equation of motion, evaluated at a mean dynamic pressure. Writing $L=\bar qSC_{L,TO}$ and $D=\bar qSC_{D,TO}$ with one representative $\bar q$ over the run,

$$
\frac DW+\mu\left(1-\frac LW\right)=\mu+\frac{\bar q}{W/S}\left(C_{D,TO}-\mu C_{L,TO}\right).
$$

The left side of the equation of motion is then constant, and the same integration gives

$$
\left(\frac TW-\mu-\frac{\bar q\left(C_{D,TO}-\mu C_{L,TO}\right)}{W/S}\right)s_1=\frac{V_2^2}{2g},
$$

so

$$
\frac TW=\frac{V_2^2}{2gs_1}+\mu+\left(C_{D,TO}-\mu C_{L,TO}\right)\frac{\bar q}{W/S} .
$$

The speed $V_2/\sqrt2$ is the speed at which $V^2$ is half its final value, so $\bar q=\frac12q_2$ is the dynamic pressure at that speed, which for constant acceleration (where $V^2$ grows in proportion to distance) is the average of $q$ over the length of the run. For the spreadsheet aircraft $C_{D,TO}-\mu C_{L,TO}=0.0898-0.17\times0.97=-0.0751$: lift relieves the friction faster than drag adds to the resistance, the correction is negative, and the simple line is conservative. At the design wing loading of 151.6 N/m² the refined value is $0.386-0.0751\times77.89/151.6=0.347$.

![[mof_m12_takeoff_refined.png|800]]

## 8. The feasible region and the design point

Each boundary splits the plane. An aircraft meets a thrust requirement if its $T/W$ lies on or above that curve, and meets the stall requirement if its $W/S$ lies on or left of that line. The **feasible region** is the set of points that satisfy all of them at once:

$$
\frac WS\leq\left(\frac WS\right)_{\text{stall}},\qquad\frac TW\geq\max\left\{\left(\frac TW\right)_{\text{TO}},\left(\frac TW\right)_{\text{climb}},\left(\frac TW\right)_{\text{turn}},\left(\frac TW\right)_{\text{cruise}}\right\}.
$$

Its lower edge is the upper envelope of the thrust curves, and the curve forming the envelope at a given $W/S$ is the active (sizing) constraint there. On the left, where $1/(W/S)$ is large, the profile-drag terms dominate and the curve with the highest $qC_{D0}$ wins (cruise and turn at the cruise $q$). Once the U-curves have dropped below the take-off line, take-off sizes the engine.

The **design point** is chosen on the boundary of the feasible region, because any point inside it carries more thrust or more wing than the requirements need. With a horizontal take-off line as the top constraint on the right, the least thrust is available along the whole stretch of that line inside the region, and moving right along it costs nothing in thrust while shrinking the wing. The lowest-cost point is therefore the corner where the take-off line meets the stall line: the highest permitted wing loading at the least thrust. In practice a margin is left from that corner, because $C_{L\max}$, $C_{D0}$ and installed thrust are estimates at this stage.

From the design point the two sizing quantities follow directly:

$$
S=\frac{W}{(W/S)},\qquad T=W\left(\frac TW\right).
$$

The final step is to put $S$ and $T$ back into the original performance formulas (take-off run, climb rate, turn, cruise $C_L$) and confirm each requirement is met.

### Where the take-off line meets a U-curve

Revision questions 35–37 ask for "the lowest wing loading that will result in the minimum required thrust to weight ratio", that is, the left end of the stretch of take-off line inside the region. It is the left intersection of the horizontal line $y_{TO}$ with the curve

$$
y=\frac{V_V}{V}+\frac{qC_{D0}}{x}+\frac{Kn^2}{q}\,x ,
$$

which covers cruise ($n=1$, $V_V=0$), turn ($V_V=0$) and climb ($n=1$). Setting $y=y_{TO}$,

$$
y_{TO}-\frac{V_V}{V}=\frac{qC_{D0}}{x}+\frac{Kn^2}{q}\,x .
$$

Multiplying by $x>0$ and collecting terms gives a quadratic in $x$:

$$
\frac{Kn^2}{q}\,x^2-\left(y_{TO}-\frac{V_V}{V}\right)x+qC_{D0}=0 .
$$

With $a=Kn^2/q$, $b=y_{TO}-V_V/V$ and $c=qC_{D0}$,

$$
x=\frac{b\pm\sqrt{b^2-4ac}}{2a} .
$$

Real roots exist only when $b^2\geq4ac$, that is when

$$
y_{TO}-\frac{V_V}{V}\geq2n\sqrt{KC_{D0}},
$$

the condition that the take-off line lies above the bottom of the U (Section 4). The smaller root is the left crossing. The larger root is where the induced branch climbs back through the line, usually at a wing loading far beyond the stall limit.

![[mof_m12_revision_crossings.png|900]]

The spreadsheet workbooks for these questions find the root with Excel's Solver from a guessed wing loading. Since the problem is a quadratic, the formula is exact and needs no guess.

## Worked examples

### Constraint chart for a 15 kg UAV

The UAV has a mass of 15 kg and flies at low altitude. Its inputs are in imperial units and are converted in spreadsheet cells C18–C28:

| Requirement | Input | SI value |
|---|---|---|
| ground run $s_1$ | 197 ft | 60.05 m |
| take-off speed $V_2$ | 31 kn | 15.95 m/s |
| cruise speed | 58.3 kn TAS | 29.99 m/s |
| climb speed ($0.8\times$ cruise) | 46.64 kn | 23.99 m/s |
| rate of climb $V_V$ | 591 ft/min | 3.002 m/s |
| approach speed | 29.5 kn | 15.18 m/s |
| stall speed (approach $/1.1$) | 26.82 kn | 13.80 m/s |
| turn load factor $n$ | 1.41 | bank 44.8° |
| $AR$, $C_{D0}$, $\mu$, $C_{L\max,app}$ | 9, 0.0418, 0.17, 1.3 | $K=0.04516$ |

All densities are 1.225 kg/m³. The dynamic pressures are

$$
q_{cr}=\tfrac12(1.225)(29.99)^2=550.96\ \text{Pa},\qquad q_{cl}=\tfrac12(1.225)(23.99)^2=352.61\ \text{Pa},
$$

$$
q_s=\tfrac12(1.225)(13.80)^2=116.58\ \text{Pa}.
$$

Approach (stall) limit:

$$
\frac WS\leq q_sC_{L\max}=116.58\times1.3=151.56\ \text{N/m}^2=15.45\ \text{kg/m}^2 .
$$

Take-off line:

$$
\begin{aligned}
\frac TW&=\frac{(15.948)^2}{2(9.81)(60.046)}+0.17\\
&=0.2159+0.17\\
&=0.3859 .
\end{aligned}
$$

The three U-curves, with $x$ in N/m²:

$$
\begin{aligned}
\text{turn: }\frac TW&=\frac{550.96\times0.0418}{x}+\frac{0.04516\times1.41^2}{550.96}\,x=\frac{23.03}{x}+1.630\times10^{-4}x,\\
\text{climb: }\frac TW&=\frac{3.0023}{23.994}+\frac{352.61\times0.0418}{x}+\frac{0.04516}{352.61}\,x=0.1251+\frac{14.74}{x}+1.281\times10^{-4}x,\\
\text{cruise: }\frac TW&=\frac{23.03}{x}+8.197\times10^{-5}x .
\end{aligned}
$$

> [!check] Against the spreadsheet rows
> At $x=6$ Pa (row 61) the formulas give turn 3.8393, climb 2.5824, take-off 0.3859 and cruise 3.8388, the values in G61:J61. At $x=10$ Pa (row 101) turn gives 2.3046 and climb 1.6003, again matching. The chart plots these against column F, which is $x\times0.10197=x/9.80665$, so its horizontal axis is in kg/m²; the approach line sits at 15.45 on that axis.

At the stall limit the U-curves stand at turn 0.177, climb 0.242 and cruise 0.164, all below the take-off line, so take-off is the active constraint at the design point. Their minima (0.123, 0.212 and 0.087, at 376, 339 and 530 N/m²) all lie above the stall limit. The left crossings with the take-off line, from the quadratic of Section 8, are

| Curve | $a$ | $b$ | $c$ | lower root (N/m²) | (kg/m²) |
|---|---|---|---|---|---|
| turn | $1.630\times10^{-4}$ | 0.3859 | 23.03 | 61.27 | 6.25 |
| climb | $1.281\times10^{-4}$ | 0.2608 | 14.74 | 58.19 | 5.93 |
| cruise | $8.197\times10^{-5}$ | 0.3859 | 23.03 | 60.46 | 6.16 |

The turn crossing is the furthest right, so the take-off line forms the floor of the feasible region from 61.3 to 151.6 N/m², which matches the crossing near 6.2 kg/m² on the course plot.

For the ceiling of Section 6: at 500 ft, $\sigma=0.985$ and $\rho=1.207$ kg/m³. At the design wing loading the minimum-drag lift coefficient $\sqrt{C_{D0}/K}=0.962$ is reached at $V=\sqrt{2(151.6)/(1.207\times0.962)}=16.2$ m/s. A residual 0.508 m/s climb there needs $0.508/16.2+2\sqrt{KC_{D0}}=0.031+0.087=0.118$ of the local weight in thrust, or $0.118/0.985=0.120$ of sea-level thrust if the thrust falls with density. That is a third of the take-off value.

### Lowest wing loading for the minimum thrust to weight ratio

For the spreadsheet aircraft, the take-off and climb requirements alone give the left crossing as follows. With $y_{TO}=0.3859$, $V_V/V=3.0023/23.994=0.1251$ and $q=352.61$ Pa,

$$
\begin{aligned}
a&=\frac{K}{q}=\frac{0.04516}{352.61}=1.2808\times10^{-4},\\
b&=0.3859-0.1251=0.2607,\\
c&=qC_{D0}=352.61\times0.0418=14.739 .
\end{aligned}
$$

The discriminant is

$$
b^2-4ac=0.06798-4(1.2808\times10^{-4})(14.739)=0.06798-0.00755=0.06043,
$$

so

$$
x=\frac{0.2607-\sqrt{0.06043}}{2(1.2808\times10^{-4})}=\frac{0.2607-0.2458}{2.5616\times10^{-4}}=58.2\ \text{N/m}^2 .
$$

> [!check] Root by substitution
> At $x=58.19$ N/m²: $0.1251+14.739/58.19+1.2808\times10^{-4}\times58.19=0.1251+0.2533+0.0075=0.3859$, equal to the take-off value. The other root is 1978 N/m², thirteen times the stall limit.

### Sizing the wing and the engine

Take the design point at the corner, $W/S=151.6$ N/m² and $T/W=0.386$. With $W=15\times9.81=147.15$ N,

$$
S=\frac{147.15}{151.56}=0.971\ \text{m}^2,\qquad b=\sqrt{AS}=\sqrt{9\times0.971}=2.96\ \text{m},
$$

$$
T=0.3859\times147.15=56.8\ \text{N}.
$$

Checking the original requirements with these numbers: the ground run is $V_2^2/[2g(T/W-\mu)]=15.948^2/[2(9.81)(0.2159)]=60.05$ m, exactly the 197 ft required; the stall speed is $\sqrt{2(151.56)/(1.225\times1.3)}=13.80$ m/s, giving the 29.5 kn approach with the 1.1 margin; the cruise lift coefficient is $151.56/550.96=0.275$ and the cruise needs $T/W=0.164$, 43 % of the installed thrust; and with full thrust at the climb speed the climb rate is $V(T/W-D/W)=23.99\,(0.3859-0.1167)=6.46$ m/s, more than twice the 3.0 m/s asked for. A take-off-sized aircraft has surplus climb and turn performance, which is the usual outcome for a short-field UAV.

## Links

- Parent: [[SESA1015 Intro to Aero & Astro Hub]] · Solutions: [[SESA1015 T08 - Constraint Analysis Solutions]] · Workbook map: [[SESA1015 Revision Workbook Coverage]]
- Builds on: [[SESA1015 M04 - Steady Level Flight and Stall]] (stall and level-flight thrust) · [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] ($(L/D)_{\max}$) · [[SESA1015 M08 - Glide and Climb Performance]] (specific excess thrust) · [[SESA1015 M09 - Take-off and Landing Performance]] (ground run) · [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]] (load factor)
- Concepts: [[Aircraft Constraint Diagram]] · [[Thrust-to-Weight Ratio]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Take-off Ground Run]] · [[Load Factor and Turn Performance]] · [[Minimum Drag and Minimum Power]]
- Later in the degree: thrust lapse with altitude and installed engine thrust in [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]; the polar and $C_{L\max}$ from wing theory in [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]; manoeuvres beyond steady states in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]. Aircraft design (SESA1201 on the slides) is not in this vault.

## Sources

- Mechanics of Flight Lecture Slides version 2 (Prof. A. Keane), p. 180 (role of performance in design, the four sizing formulae), p. 181 (take-off, landing and turn rubric)
- Older lecture deck (`Mechanics of Flight - Lecture Slides.pdf`), p. 91 (stalling speed constraint), p. 102 (level flight speed constraint), p. 191 (take-off constraint), pp. 220–224 (turn, take-off, climb, stall and cruise constraints), p. 225 (plot of typical constraints)
- Mechanics of Flight Course Notes §4.2 (p. 19), §4.3 (p. 21), §7.2 (pp. 37–38), §7.3 (pp. 38–41), §7.4 (pp. 42–43)
- `Mechanics of Flight - Constraint Analysis.xlsx` (Sheet1: inputs C2–C48, formula list A50–B54, curves E2:K2002 and the chart); `04 - Labs & Coursework/constraint_analysis_simplified.xlsx` is a byte-identical copy
- Revision workbook, Questions 35–39
- Figures: `01 - Notes/Figures/generate_mof_m12_figures.py`

## Self-study tasks

No problem list was set for this topic beyond the revision workbook. The workbook questions and the spreadsheet are the practice.

### Core

- [ ] Revision Q35: take-off on 88 m and a 2 g constant-velocity turn at 31 m/s; lowest wing loading at the minimum $T/W$. → [[SESA1015 T08 - Constraint Analysis Solutions#Question 35]] · method in [[#Where the take-off line meets a U-curve]]
- [ ] Revision Q36: take-off on 56 m and a 6.4 m/s climb at 34 m/s. → [[SESA1015 T08 - Constraint Analysis Solutions#Question 36]] · [[#Lowest wing loading for the minimum thrust to weight ratio]]
- [ ] Revision Q37: take-off on 98 m and cruise at 38 m/s. → [[SESA1015 T08 - Constraint Analysis Solutions#Question 37]]
- [ ] Revision Q38: take-off $T/W$ alone for an 85 m run. → [[SESA1015 T02 - Take-off and Landing Solutions#Question 38]] · [[#7. Take-off constraint]]
- [ ] Revision Q39: maximum wing loading from an approach speed and landing $C_{L\max}$. → [[SESA1015 T02 - Take-off and Landing Solutions#Question 39]] · [[#2. Stall and approach constraint]]
- [ ] Rebuild the course spreadsheet (inputs, $K$ from $e_0$, the four curves and the approach line) and reproduce row 61 and the 15.45 kg/m² approach line (Constraint Analysis spreadsheet; Slides v1, p. 225). → [[#Constraint chart for a 15 kg UAV]]

### Further practice

- [ ] Derive the minimum of the turn curve, $x^*=(q/n)\sqrt{C_{D0}/K}$ and $(T/W)_{\min}=2n\sqrt{KC_{D0}}$, and show that $C_L$ there is the minimum-drag value (suggested, not lecturer-set). → [[#The minimum of the curve]]
- [ ] Redo the spreadsheet take-off line with the unused $C_{L,TO}$, $C_{D,TO}$ and $q_{TO}$ cells, and explain why the correction is negative (suggested, not lecturer-set). → [[#Keeping lift and drag on the ground run]]
- [ ] Revision Q30: cruise wing loading from a Mach number, altitude and cruise $C_L$, the cruise curve's $W/S=qC_L$ read the other way. → [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 30]]

## Transcript and slide slips

> [!warning] Slide slip (older deck, p. 225)
> Where: [[#8. The feasible region and the design point]].
>
> The "Plot of Typical Constraints" labels its horizontal axis "W/S (N/m²)" with values 0–20 and the approach line near 15.4. The plot is the course spreadsheet's chart, whose series use column F, $W/S$ in kg/m² (the chart's own axis title is "W/S (Kg/M^2)"). In N/m² the range is 0–196 and the approach line is at 151.6 N/m².

> [!warning] Slide slip (older deck, p. 220)
> Where: [[#4. Turn constraint]].
>
> The turn slide writes the lift coefficient needed in the turn as "$nC_L=nW/qS$". It should read $C_L=nW/(qS)$: the lift coefficient itself is $n$ times the level-flight value.

> [!warning] Slide slip (older deck, p. 222)
> Where: [[#5. Climb constraint]].
>
> The climb slide writes $V_V=V(T/W-D/L)$. The exact expression is $V(T/W-D/W)$; replacing $W$ by $L$ is the shallow-climb approximation $L\approx W$, which the final constraint also uses.

> [!warning] Spreadsheet slip (Constraint Analysis.xlsx, cell C20)
> Where: [[#Constraint chart for a 15 kg UAV]].
>
> TakeOffElevation_m is computed as `=CB5*0.3048`, referring to an empty cell CB5 instead of C5. It returns 0, which happens to equal the entered elevation of 0 ft, and no curve uses it, so the plotted results are unaffected. The spreadsheet also mixes $g=9.81$ (take-off) with $1/9.80665$ (the kg/m² column), a 0.03 % difference.
