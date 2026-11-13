---
title: "SESA3029 Past Paper 2014-15 - Solutions"
module: "SESA3029 Aerothermodynamics"
type: past-paper-solutions
tags: [sesa3029, past-paper, solutions, laval-nozzle, pitot-probe, shock-expansion, ackeret, shock-reflection, swbli, supersonic-intake, method-of-characteristics, minimum-length-nozzle, heat-transfer, richardson-extrapolation]
paper: "2014-15"
theory_notes: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]", "[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]", "[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]", "[[SESA3029 W05a - Method of Characteristics]]", "[[SESA3029 W05b - Minimum-Length Nozzle Design]]", "[[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils]]", "[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]"]
status: complete
sources: ["03 - Exams & Past Papers/Past Papers/Southampton/SESA3029-201415-01-SESA3029W1.pdf"]
---

# SESA3029 Past Paper 2014-15 - Solutions

> [!abstract] Paper info
> 2014-15 Semester 1 examination (SESA3029W1, 2 hours). There is no formula sheet; the IFT, NST and oblique shock chart are provided. Four questions of 30 marks each, of which three are to be attempted for 90 marks; all four are solved here. Front-page constants: $R=287\ \text{J/(kg K)}$, $\gamma=1.4$, $\rho=1.225\ \text{kg/m}^3$, $\mu=1.79\times10^{-5}\ \text{N s/m}^2$, $1\ \text{bar}=10^5\ \text{N/m}^2$; where $c_p$ is needed it is $\gamma R/(\gamma-1)=1004.5\ \text{J/(kg K)}$. Question 4 parts (i) and (ii) are heat transfer and re-entry radiation (Weeks 9–12, not yet lectured); part (iii) is CFD verification. Table values are the IFT and NST rows at their 0.02 spacing, interpolated linearly, and every number was checked in Python against the exact relations.

| Q | Marks | Topic | Theory |
|---|---:|---|---|
| 1 | 30 | Blowdown tunnel ($M=2.4$, $p_0=6\ \text{bar}$, $T_0=298\ \text{K}$) and diamond aerofoil ($t/c=0.12$, $\alpha=0^\circ$): Pitot pressure, shock-expansion against Ackeret $C_p$, supersonic and transonic sections | [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]], [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]], [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]], [[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]], [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] |
| 2 | 30 | Strong and weak oblique shocks; wall reflection at $M_1=3$ ($\beta=39^\circ$, and failure at $40^\circ$); shock–boundary-layer interaction; normal and oblique intakes | [[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]], [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]] |
| 3 | 30 | $M=3.6$ minimum-length nozzle by MoC: interior point 8, simple region, wall point 9, nozzle CFD boundary conditions | [[SESA3029 W05a - Method of Characteristics|W05a]], [[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]] |
| 4 | 30 | (i)–(ii) $h$, $\text{Nu}$, laminar flat-plate heat transfer, lunar re-entry (heat transfer, Weeks 9–12, not yet lectured); (iii) Richardson extrapolation and CFD checks | Not yet lectured (i–ii); [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]] (iii) |

---

## Q1. Blowdown tunnel, symmetric diamond aerofoil and aerofoil design (30 marks)

> A supersonic blowdown tunnel ($p_0 = 6\ \text{bar}, T_0 = 298\ \text{K}, M = 2.4$) holds a symmetric diamond aerofoil ($t/c = 0.12, \alpha = 0^\circ$, Figure Q.1).
> (i) Find: (a) nozzle area ratio; (b) throat temperature; (c) test-section static pressure; (d) Pitot stagnation pressure in the test section. [8]
> (ii) (a) Sketch the wave pattern [2]; (b) compute $C_p$ on faces A and B by shock-expansion [12]; (c) compute $C_p$ on A and B by Ackeret's theory [4].
> (iii) Compare optimum aerofoil designs for supersonic versus transonic flight. [4]

### (i) Nozzle and Pitot conditions [8 marks]

The nozzle flow is steady and isentropic with $\gamma=1.4$, $p_0=6$ bar and $T_0=298$ K, and the tunnel runs at its design condition, so the throat is sonic and the test section is at $M=2.4$ ([[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow|W04]]). The IFT row $M=2.40$ gives $A/A^*=2.4031$, $p/p_0=0.0684$; the row $M=1.00$ gives $T/T_0=0.8333$.

(a) The test section is the nozzle exit, so the area ratio is

$$
\frac{A_e}{A^*}=\boxed{2.403}.
$$

(b) The throat temperature is

$$
T^*=0.8333\times298=\boxed{248.3\ \text{K}}.
$$

(c) The test-section static pressure is

$$
p_\infty=0.0684\times6=\boxed{0.4104\ \text{bar}}\ (41.04\ \text{kPa}).
$$

(d) The test section is supersonic, so a bow shock stands ahead of the Pitot probe and the probe reads the stagnation pressure behind a normal shock at $M_1=2.4$ ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]]). The NST row $M_1=2.40$ gives $p_{02}/p_{01}=0.5401$, and $p_{01}=p_0$ because the nozzle flow is isentropic:

$$
p_{02}=0.5401\times6=\boxed{3.241\ \text{bar}}.
$$

The same row gives $p_{02}/p_1=7.8969$, and $7.8969\times0.4104=3.241$ bar.

### (ii) Diamond aerofoil wave pattern and pressure coefficients [18 marks]

The diamond has its maximum thickness at mid-chord, so its semi-angle $\varepsilon$ satisfies

$$
\tan\varepsilon=\frac{t/2}{c/2}=\frac{t}{c}=0.12,
$$

$$
\varepsilon=\arctan0.12=6.8428^\circ.
$$

#### (a) Wave pattern

![[at_pp_201415_q1_diamond.png|850]]

At $\alpha=0^\circ$ the pattern is symmetric. An attached oblique shock leaves the leading edge on each side, turning the flow by $\varepsilon$ onto the front faces (A is the lower front face). A centred Prandtl–Meyer fan at each crest turns the flow by $2\varepsilon=13.69^\circ$ onto the rear faces (B is the lower rear face). At the trailing edge an oblique shock on each side turns the flow back parallel to the free stream.

#### (b) Shock-expansion pressure coefficients [12 marks]

On face A the shock turns $M_\infty=2.4$ by $\theta=6.8428^\circ$. The weak-shock angle comes from the θ–β–M relation by the secant rule, starting from $29^\circ$ and $32^\circ$ either side of the OSC reading:

| Iterate | $\beta$ (°) | $\theta(\beta)$ (°) |
|---:|---:|---:|
| 0 | 29.0000 | 5.5593 |
| 1 | 32.0000 | 8.9222 |
| 2 | 30.1450 | 6.8805 |
| 3 | 30.1107 | 6.8417 |
| 4 | 30.1117 | 6.8428 |

The first update is

$$
\beta_2=29+(6.8428-5.5593)\,\frac{32-29}{8.9222-5.5593}=29+1.1450=30.1450^\circ,
$$

and the exact weak root is $\beta=30.112^\circ$. The normal Mach number is

$$
M_{n1}=2.4\sin30.112^\circ=2.4\times0.50169=1.20405.
$$

The NST rows $M_{n1}=1.20$ ($M_{n2}=0.8422$, $p_2/p_1=1.5133$) and $1.22$ ($0.8300$, $1.5698$) bracket it, with $f=(1.20405-1.20)/0.02=0.2025$:

$$
M_{n2}=0.8422-0.2025\times(0.8422-0.8300)=0.8397,
$$

$$
\frac{p_A}{p_\infty}=1.5133+0.2025\times(1.5698-1.5133)=1.5247.
$$

The flow on face A is at $\beta-\theta=23.269^\circ$ to the shock:

$$
M_A=\frac{M_{n2}}{\sin(\beta-\theta)}=\frac{0.8397}{\sin23.269^\circ}=\frac{0.8397}{0.39505}=2.1256.
$$

The pressure coefficient uses $\tfrac12\rho_\infty U_\infty^2=\tfrac12\gamma p_\infty M_\infty^2$, so

$$
C_p=\frac{p-p_\infty}{\tfrac12\gamma p_\infty M_\infty^2}=\frac{p/p_\infty-1}{\tfrac12\gamma M_\infty^2},\qquad \tfrac12\gamma M_\infty^2=0.7\times2.4^2=4.032,
$$

$$
C_{p,A}=\frac{1.5247-1}{4.032}=\frac{0.5247}{4.032}=\boxed{+0.1301}.
$$

From face A to face B the flow expands through $2\varepsilon=13.6855^\circ$. The IFT rows $M=2.12$ ($\nu=29.6308^\circ$) and $M=2.14$ ($\nu=30.1613^\circ$) give, with $f=(2.1256-2.12)/0.02=0.28$,

$$
\nu_A=29.6308+0.28\times(30.1613-29.6308)=29.7793^\circ.
$$

The fan adds the turning angle:

$$
\nu_B=29.7793^\circ+13.6855^\circ=43.4648^\circ.
$$

The rows $M=2.68$ ($\nu=43.1868^\circ$) and $M=2.70$ ($\nu=43.6215^\circ$) bracket it:

$$
f=\frac{43.4648-43.1868}{43.6215-43.1868}=\frac{0.2780}{0.4347}=0.6396,
$$

$$
M_B=2.68+0.02\times0.6396=2.6928.
$$

With $p/p_0=\left(1+0.2M^2\right)^{-3.5}$,

$$
\frac{p_A}{p_0}=\left(1+0.2\times2.1256^2\right)^{-3.5}=1.9036^{-3.5}=0.10506,
$$

$$
\frac{p_B}{p_0}=\left(1+0.2\times2.6928^2\right)^{-3.5}=2.4502^{-3.5}=0.04343.
$$

$p_0$ is constant through the fan, so

$$
\frac{p_B}{p_\infty}=\frac{p_B/p_0}{p_A/p_0}\,\frac{p_A}{p_\infty}=\frac{0.04343}{0.10506}\times1.5247=0.6302,
$$

$$
C_{p,B}=\frac{0.6302-1}{4.032}=\boxed{-0.0917}.
$$

The exact relations give $C_{p,A}=0.1301$ and $C_{p,B}=-0.0917$.

#### (c) Ackeret pressure coefficients [4 marks]

With

$$
\sqrt{M_\infty^2-1}=\sqrt{2.4^2-1}=\sqrt{4.76}=2.1817
$$

and $\varepsilon=6.8428^\circ=0.11943$ rad, face A turns the flow into itself by $\varepsilon$ and face B turns it away by $\varepsilon$ relative to the free stream:

$$
C_{p,A}=\frac{2\varepsilon}{\sqrt{M_\infty^2-1}}=\frac{2\times0.11943}{2.1817}=\boxed{+0.1095},
$$

$$
C_{p,B}=\frac{-2\varepsilon}{\sqrt{M_\infty^2-1}}=\boxed{-0.1095}.
$$

Taking $\varepsilon\approx t/c=0.12$ rad gives $\pm0.1100$. Ackeret theory under-predicts the compression on A by $16\,\%$ and over-predicts the suction on B by $19\,\%$, because the linear result is symmetric in $\pm\theta$ while the real compression is stronger and the real expansion weaker.

### (iii) Optimum supersonic and transonic sections [4 marks]

A transonic section ([[SESA3029 W07a - Euler Equations and the Effect of Mach Number on Aerofoils|W07a]]) flies with a subsonic free stream and a local supersonic region on the upper surface. It keeps a rounded leading edge, which gives good low-speed behaviour, and a moderate thickness of about 10–12 %. The supercritical shape has a flat upper surface, which keeps the local acceleration small, and aft camber to recover the lift lost by flattening the top. The supersonic region then ends in a weaker shock further aft, which delays drag divergence and reduces shock-induced separation.

A supersonic section ([[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]]) needs a sharp leading edge, so that the leading-edge shock stays attached instead of forming a detached bow shock with a strong normal portion. It should be thin, because the thickness wave drag scales as $(t/c)^2/\sqrt{M_\infty^2-1}$, with typical values of 3–6 %. Camber adds wave drag without improving the lift, so the best sections are symmetric: the double wedge (diamond), which has the least thickness drag for a given $t/c$, or the biconvex section.

---

## Q2. Oblique shock branches, wall reflections, SWBLI and supersonic intakes (30 marks)

> (i) Explain strong and weak oblique-shock solutions with practical examples. [5]
> (ii) Oblique shock in $M_1 = 3$ impinges on a plane wall (Figure Q.2): (a) for $\beta = 39^\circ$, find $M_3$ after reflection; (b) find $p_3/p_1$; (c) for $\beta = 40^\circ$, explain why regular reflection fails and sketch the resulting pattern including slip lines. [15]
> (iii) Explain why laboratory experiments show the reflected shock originating upstream of the inviscid impingement point. [5]
> (iv) Sketch single-normal-shock vs oblique-shock supersonic intakes and explain which is preferred. [5]

![[at_pp_201415_q2_reflection.png|920]]

### (i) Strong and weak solutions [5 marks]

For a given $M_1>1$ and a deflection $\theta$ below the maximum $\theta_{\max}(M_1)$, the θ–β–M relation has two solutions for the shock angle ([[SESA3029 W02 - Oblique Shock Relations and Mach Waves|W02]]). The **weak solution** has the smaller $\beta$, so a smaller normal Mach number, a smaller pressure rise and a smaller entropy rise; the flow behind it is supersonic except in a narrow band of deflections just below $\theta_{\max}$. The **strong solution** has the larger $\beta$, closer to a normal shock, with a larger pressure and entropy rise and subsonic flow behind it. Which one occurs is set by the downstream pressure.

The weak solution is the one seen in external flows where the downstream pressure is not imposed: the attached shocks on wedges, cones and the leading edges of supersonic wings and intake ramps. The strong solution appears where a high downstream pressure is imposed or where the flow must become subsonic: near the axis of the detached bow shock ahead of a blunt body, where the shock is locally almost normal, and in an intake or diffuser run against a high back pressure.

### (ii) Inviscid wall reflection at M = 3 [15 marks]

#### (a) Mach number after the reflection for β = 39°

The incident shock has known $M_1$ and $\beta$, so its deflection follows directly from the θ–β–M relation ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]). With $\sin^239^\circ=0.39604$, $\cos78^\circ=0.20791$ and $\cot39^\circ=1.23490$:

$$
\tan\theta_1=2\cot\beta\,\frac{M_1^2\sin^2\beta-1}{M_1^2(\gamma+\cos2\beta)+2}=2\times1.23490\times\frac{9\times0.39604-1}{9\times(1.4+0.20791)+2},
$$

$$
\tan\theta_1=2.46980\times\frac{2.56436}{16.47121}=0.38452,
$$

$$
\theta_1=21.033^\circ.
$$

The normal Mach number is

$$
M_{n1}=M_1\sin\beta=3\sin39^\circ=3\times0.62932=1.88796.
$$

The NST rows $M_{n1}=1.88$ ($M_{n2}=0.5996$, $p_2/p_1=3.9568$) and $1.90$ ($0.5956$, $4.0450$) bracket it, with $f=(1.88796-1.88)/0.02=0.398$:

$$
M_{n2}=0.5996-0.398\times(0.5996-0.5956)=0.5980,
$$

$$
\frac{p_2}{p_1}=3.9568+0.398\times(4.0450-3.9568)=3.9919.
$$

Behind the incident shock the flow is parallel to the turned direction, at $\beta-\theta_1=17.967^\circ$ to the shock:

$$
M_2=\frac{M_{n2}}{\sin(\beta-\theta_1)}=\frac{0.5980}{\sin17.967^\circ}=\frac{0.5980}{0.30847}=1.9386.
$$

The wall forces the flow back parallel to itself, so the reflected shock must turn the $M_2=1.9386$ stream by $\theta_2=\theta_1=21.033^\circ$. That is possible only if $\theta_{\max}(M_2)$ exceeds $21.033^\circ$. The shock angle at maximum deflection satisfies

$$
\sin^2\beta^*=\frac{1}{\gamma M^2}\left[\frac{\gamma+1}{4}M^2-1+\sqrt{(\gamma+1)\left(\frac{\gamma+1}{16}M^4+\frac{\gamma-1}{2}M^2+1\right)}\right].
$$

At $M=1.9386$, with $M^2=3.75817$ and $M^4=14.12384$, the bracket is $1.25490+\sqrt{2.4\times3.87021}=1.25490+3.04770=4.30260$, so

$$
\sin^2\beta^*=\frac{4.30260}{1.4\times3.75817}=0.81776,\qquad \beta^*=64.73^\circ.
$$

Putting $\beta^*$ into the θ–β–M relation, with $M^2\sin^2\beta^*-1=2.07329$, $\cos2\beta^*=1-2\times0.81776=-0.63552$ and $\cot\beta^*=0.47207$:

$$
\tan\theta_{\max}=2\times0.47207\times\frac{2.07329}{3.75817\times(1.4-0.63552)+2}=0.94414\times\frac{2.07329}{4.87303}=0.40170,
$$

$$
\theta_{\max}(1.9386)=21.885^\circ>21.033^\circ,
$$

so a regular reflection exists. Its weak shock angle comes from the secant rule on $\theta(\beta)=21.033^\circ$ at $M=1.9386$, starting from $55^\circ$ and $60^\circ$:

| Iterate | $\beta_2$ (°) | $\theta(\beta_2)$ (°) |
|---:|---:|---:|
| 0 | 55.0000 | 19.6268 |
| 1 | 60.0000 | 21.3139 |
| 2 | 59.1670 | 21.1041 |
| 3 | 58.8838 | 21.0260 |
| 4 | 58.9086 | 21.0330 |

The first update is

$$
\beta_{2,2}=55+(21.0328-19.6268)\,\frac{60-55}{21.3139-19.6268}=55+4.1670=59.1670^\circ,
$$

and the iteration settles at $\beta_2=58.91^\circ$. The normal Mach number into the reflected shock is

$$
M_{n2,\text{ref}}=M_2\sin\beta_2=1.9386\times\sin58.91^\circ=1.9386\times0.85636=1.66013.
$$

The NST rows $M_{n1}=1.66$ ($M_{n2}=0.6512$, $p_2/p_1=3.0482$) and $1.68$ ($0.6458$, $3.1261$) bracket it, with $f=(1.66013-1.66)/0.02=0.0065$:

$$
M_{n3}=0.6512-0.0065\times(0.6512-0.6458)=0.6512,
$$

$$
\frac{p_3}{p_2}=3.0482+0.0065\times(3.1261-3.0482)=3.0487.
$$

The flow behind the reflected shock is parallel to the wall, at $\beta_2-\theta_2=37.877^\circ$ to the shock:

$$
M_3=\frac{M_{n3}}{\sin(\beta_2-\theta_2)}=\frac{0.6512}{\sin37.877^\circ}=\frac{0.6512}{0.61397}=\boxed{1.061}.
$$

The exact relations give $M_3=1.0605$.

#### (b) Overall pressure rise

$$
\frac{p_3}{p_1}=\frac{p_3}{p_2}\,\frac{p_2}{p_1}=3.0487\times3.9919=\boxed{12.17}.
$$

#### (c) Failure of regular reflection at β = 40°

Repeating the first step with $\beta=40^\circ$, with $\sin^240^\circ=0.41318$, $\cos80^\circ=0.17365$ and $\cot40^\circ=1.19175$:

$$
\tan\theta_1=2\times1.19175\times\frac{9\times0.41318-1}{9\times(1.4+0.17365)+2}=2.38350\times\frac{2.71858}{16.16283}=0.40091,
$$

$$
\theta_1=21.846^\circ.
$$

Then $M_{n1}=3\sin40^\circ=1.92836$; the NST rows $1.92$ ($M_{n2}=0.5918$) and $1.94$ ($0.5880$) give, with $f=0.418$, $M_{n2}=0.5918-0.418\times0.0038=0.5902$, and

$$
M_2=\frac{0.5902}{\sin(40^\circ-21.846^\circ)}=\frac{0.5902}{0.31157}=1.8943.
$$

The same maximum-deflection calculation at $M=1.8943$ gives $\sin^2\beta^*=0.81860$, $\beta^*=64.79^\circ$ and

$$
\theta_{\max}(1.8943)=21.06^\circ<21.85^\circ.
$$

The reflected shock would have to turn the flow by more than any attached shock at $M_2$ can, so the θ–β–M relation has no solution for $\beta_2$ and the calculation stops. The reflection becomes a **Mach reflection**. The incident shock no longer reaches the wall. It ends at a triple point above the wall, from which a nearly normal Mach stem runs down to the wall and a reflected shock runs back into the flow. A slip line leaves the triple point and trails downstream between the subsonic flow behind the Mach stem and the supersonic flow that has passed through the incident and reflected shocks; the two streams have equal pressure but different velocities and entropies.

### (iii) Upstream origin of the reflected shock in experiments [5 marks]

A real wall carries a boundary layer, and the flow near the wall in it is subsonic. The pressure rise of the incident shock can therefore travel upstream through the subsonic part of the layer ([[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method|W03]]; panel (b) of the figure). The adverse pressure gradient thickens the boundary layer ahead of the impingement point and, if the shock is strong enough, separates it in a bubble that starts upstream of the inviscid impingement point.

The thickening or separated layer deflects the outer supersonic flow away from the wall, like a compression ramp. The compression waves this produces coalesce into a separation shock, which is the reflected shock seen in the experiment, starting upstream of the nominal impingement point. The incident shock meets the edge of the bubble and reflects from it, a constant-pressure boundary, as an expansion fan. The flow turns back towards the wall and reattaches through a further set of compression waves, the reattachment shock.

### (iv) Normal-shock and oblique-shock intakes [5 marks]

Panel (d) of the figure sketches both. A normal-shock, or Pitot, intake brings the supersonic stream to subsonic speed through a single normal shock at the free-stream Mach number. An oblique-shock intake uses a ramp or centre-body to produce one or more oblique shocks, which slow the flow in steps, and ends the compression with a weak normal shock at a much lower Mach number.

The stagnation-pressure loss across a shock grows rapidly with its normal Mach number, so dividing the compression between several weaker shocks recovers much more stagnation pressure. Higher pressure recovery means more thrust and lower fuel consumption, so the oblique-shock intake is preferred, and above about $M_\infty\approx1.5$ it is necessary. The Pitot intake is simpler and lighter, and acceptable below that.

> [!check] Pressure recovery at M = 2.4
> A single normal shock at $M=2.4$ keeps $p_{02}/p_{01}=0.540$. A $10^\circ$ ramp shock ($\beta=33.0^\circ$, $p_{02}/p_{01}=0.978$) slows the flow to $M=2.00$, and a normal shock there keeps $0.721$, so the two together keep $0.978\times0.721=0.705$, about $30\,\%$ more.

---

## Q3. Method of characteristics for a Mach 3.6 nozzle and CFD boundary conditions (30 marks)

> A 2D C-D nozzle accelerates air to $M=3.6$ using 4 MoC characteristics (Figure Q.3). Known: point 4 ($M=2.20, \theta=29.05^\circ, x=1.21, y=1.04$) and point 7 ($M=2.20, \theta=9.68^\circ, x=2.16, y=0.43$).
> (i) Calculate flow quantities and coordinates at point 8. [14]
> (ii) (a) What is a simple region? (b) Which points bound it in Figure Q.3? (c) Given point 5 on the wall at $(2.17, 2.48)$, find coordinates of point 9. [10]
> (iii) Specify CFD inflow and outflow boundary conditions when simulating both convergent and divergent sections, explaining via characteristics. [6]

### (i) Flow state and coordinates at point 8 [14 marks]

![[at_pp_201415_q3_moc_point8.png|900]]

Figure Q.3 numbers the points as in the four-line nozzle of [[SESA3029 W05b - Minimum-Length Nozzle Design#14. Worked example: minimum-length nozzle for Me = 2.4|W05b §14]]. Point 8 is the intersection of the $C^-$ line from point 4 (the last line of the fan, d) and the $C^+$ line from point 7. With the course invariants, $R^+=\nu-\theta$ along $C^+$ and $R^-=\nu+\theta$ along $C^-$ ([[SESA3029 W05a - Method of Characteristics|W05a]]), point 8 takes $R^-$ from point 4 and $R^+$ from point 7.

The IFT row $M=2.20$ gives $\nu_4=\nu_7=31.7325^\circ$, and

$$
\mu_4=\mu_7=\arcsin\frac{1}{2.2}=27.0357^\circ.
$$

The invariants carried to point 8 are

$$
R^-_4=\nu_4+\theta_4=31.7325+29.05=60.7825^\circ,
$$

$$
R^+_7=\nu_7-\theta_7=31.7325-9.68=22.0525^\circ.
$$

At point 8 the unit process gives

$$
\nu_8=\frac{R^+_7+R^-_4}{2}=\frac{22.0525+60.7825}{2}=41.4175^\circ,
$$

$$
\theta_8=\frac{R^-_4-R^+_7}{2}=\frac{60.7825-22.0525}{2}=\boxed{19.37^\circ}\ (19.365^\circ).
$$

The IFT rows $M=2.60$ ($\nu=41.4147^\circ$) and $M=2.62$ ($\nu=41.8628^\circ$) bracket $\nu_8$:

$$
M_8=2.60+0.02\times\frac{41.4175-41.4147}{41.8628-41.4147}=2.60+0.02\times0.0062=\boxed{2.600},
$$

$$
\mu_8=\arcsin\frac{1}{2.6001}=22.619^\circ.
$$

| Point | $R^+$ (°) | $R^-$ (°) | $\theta$ (°) | $\nu$ (°) | $M$ | $\mu$ (°) | $\theta+\mu$ (°) | $\theta-\mu$ (°) | $x$ | $y$ |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 4 | 2.6825 | 60.7825 | 29.050 | 31.7325 | 2.200 | 27.036 | 56.086 | 2.014 | 1.21 | 1.04 |
| 7 | 22.0525 | 41.4125 | 9.680 | 31.7325 | 2.200 | 27.036 | 36.716 | −17.356 | 2.16 | 0.43 |
| 8 | 22.0525 | 60.7825 | 19.365 | 41.4175 | 2.600 | 22.619 | 41.984 | −3.254 | 2.8819 | 1.0219 |

The averaged slopes are

$$
\alpha_{78}=\tfrac12\left[(\theta+\mu)_7+(\theta+\mu)_8\right]=\tfrac12(36.716+41.984)=39.350^\circ,
$$

$$
\alpha_{48}=\tfrac12\left[(\theta-\mu)_4+(\theta-\mu)_8\right]=\tfrac12\left[2.014+(-3.254)\right]=-0.620^\circ,
$$

so $\tan\alpha_{78}=0.81994$ and $\tan\alpha_{48}=-0.01082$. The intersection, with $A=7$ on the $C^+$ line and $B=4$ on the $C^-$ line, is

$$
x_8=\frac{x_4\tan\alpha_{48}-x_7\tan\alpha_{78}+y_7-y_4}{\tan\alpha_{48}-\tan\alpha_{78}}=\frac{1.21\times(-0.01082)-2.16\times0.81994+0.43-1.04}{-0.01082-0.81994},
$$

$$
x_8=\frac{-2.39416}{-0.83076}=\boxed{2.882},
$$

$$
y_8=y_7+(x_8-x_7)\tan\alpha_{78}=0.43+(2.8819-2.16)\times0.81994=\boxed{1.022}.
$$

> [!check] The other characteristic
> Along the $C^-$ line from point 4, $y_8=1.04+(2.8819-1.21)\times(-0.01082)=1.0219$, the same point.

### (ii) Simple region and wall point 9 [10 marks]

#### (a) Definition

A **simple region** is a region of the flow crossed by characteristics of only one family that carry changes. The invariant of the other family has the same value everywhere in it, so each characteristic of the first family has constant $\theta$ and $\nu$ along it and is a straight line ([[SESA3029 W05b - Minimum-Length Nozzle Design|W05b]]). A centred Prandtl–Meyer fan is an example.

#### (b) Boundaries in Figure Q.3

In the minimum-length nozzle the simple region lies between the last $C^-$ line from the corner, 0–4–8–11–13, the designed wall 0–5–9–12–14, and the last $C^+$ line, 13–14. Every $C^-$ line in it carries $R^-=2\theta_{\max}$, and the $C^+$ lines 4–5, 8–9, 11–12 and 13–14 are straight. Upstream of 0–4–8–11–13 is the non-simple region, where $C^+$ and $C^-$ waves cross; downstream of 13–14 is the uniform test-section flow.

#### (c) Wall point 9

The wall is non-reflecting, so the $C^+$ line 8–9 is straight and point 9 has the state of point 8: $\theta_9=19.365^\circ$, $\mu_9=22.619^\circ$. In the same way $\theta_5=\theta_4=29.05^\circ$. The wall segment 5–9 has the average of the two wall flow angles as its slope:

$$
\alpha_{59}=\tfrac12(\theta_5+\theta_9)=\tfrac12(29.05+19.365)=24.208^\circ,\qquad \tan\alpha_{59}=0.44958.
$$

The $C^+$ line 8–9 has the constant slope

$$
\alpha_{89}=\theta_8+\mu_8=19.365+22.619=41.984^\circ,\qquad \tan\alpha_{89}=0.89989.
$$

The intersection formula with $A=8$ and the wall point $B=5$ gives

$$
x_9=\frac{x_5\tan\alpha_{59}-x_8\tan\alpha_{89}+y_8-y_5}{\tan\alpha_{59}-\tan\alpha_{89}}=\frac{2.17\times0.44958-2.8819\times0.89989+1.0219-2.48}{0.44958-0.89989},
$$

$$
x_9=\frac{0.97559-2.59340-1.45810}{-0.45031}=\frac{-3.07591}{-0.45031}=\boxed{6.83},
$$

$$
y_9=y_8+(x_9-x_8)\tan\alpha_{89}=1.0219+(6.8306-2.8819)\times0.89989=\boxed{4.58}.
$$

Along the wall from 5, $y_9=2.48+(6.8306-2.17)\times0.44958=4.575$, the same point.

### (iii) CFD boundary conditions for the whole nozzle [6 marks]

In quasi-one-dimensional flow the characteristics travel at $u$ (entropy waves), $u+a$ and $u-a$ (acoustic waves). One physical boundary condition is needed for each characteristic that enters the domain through a boundary; the remaining quantities are extrapolated from the interior ([[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes|W01]]).

At the inflow, in the convergent section, the flow is subsonic, $0<u<a$. The $u$ and $u+a$ characteristics enter the domain and the $u-a$ characteristic leaves it. Two conditions are imposed, usually the stagnation pressure and temperature $p_0$ and $T_0$ of the reservoir, and one quantity, such as the velocity, is extrapolated from inside. A two-dimensional calculation needs one more inflow condition, the flow direction, because the transverse velocity is carried in with the flow.

At the outflow, at the design condition, the flow is supersonic, $u>a$. All three characteristic speeds are positive and every characteristic leaves the domain, so no condition may be imposed and all variables are extrapolated from the interior. If the calculation were run at a back pressure that makes the exit subsonic, the $u-a$ characteristic would enter at the outlet and the static back pressure would have to be imposed there.

---

## Q4. Laminar boundary-layer heat transfer, lunar re-entry and Richardson extrapolation (30 marks)

> [!warning] Partly not yet lectured
> Parts (i) and (ii), 20 marks, are heat transfer and re-entry radiation (Weeks 9–12, not yet lectured). Part (iii), 10 marks, is CFD verification.

> (i) (a) Define $h$ and $\text{Nu}$; (b) laminar BL over a $20\ \text{cm} \times 10\ \text{cm}$ flat plate at $50^\circ\text{C}$ in air ($\text{Pr}=0.7, T_\infty=20^\circ\text{C}, U_\infty=5\ \text{m/s}$) with $\text{Nu}_x = 0.332\,\text{Re}_x^{1/2}\text{Pr}^{1/3}$: find total heat flux; (c) verify $\text{Re}_L$ is laminar. [14]
> (ii) Sketch lunar re-entry peak-heating shock layer, discuss radiation, and write the equilibrium surface temperature equation. [6]
> (iii) Uniformly second-order axisymmetric shock-fitting CFD gives peak radiative heat-flux coefficient $C_H = 0.0821$ ($100\times 100$) and $0.0762$ ($200\times 200$). Estimate exact $C_H$ and list additional CFD checks. [10]

### (i) Definitions, total heat transfer and the Reynolds-number check [14 marks]

#### (a) Definitions

The **convective heat transfer coefficient** $h$ relates the wall heat flux to the temperature difference between the wall and the free stream,

$$
q''=h\,(T_w-T_\infty),
$$

in $\text{W/(m}^2\text{ K)}$. The **Nusselt number** is the dimensionless coefficient based on a length $L$ and the fluid conductivity $k$,

$$
\text{Nu}=\frac{hL}{k},
$$

which is the ratio of convective to conductive heat transfer across the fluid, or equivalently the dimensionless temperature gradient at the wall.

#### (b) Total heat transfer from the plate

The front-page air properties are used, $\rho=1.225\ \text{kg/m}^3$ and $\mu=1.79\times10^{-5}$ N s/m², with $c_p=1004.5$ J/(kg K) and $\text{Pr}=0.7$. The conductivity follows from the Prandtl number:

$$
k=\frac{\mu c_p}{\text{Pr}}=\frac{1.79\times10^{-5}\times1004.5}{0.7}=0.02569\ \text{W/(m K)}.
$$

The plate has $L=0.20$ m in the flow direction, width $w=0.10$ m, and $\Delta T=50-20=30$ K. The Reynolds number at the trailing edge is

$$
\text{Re}_L=\frac{\rho U_\infty L}{\mu}=\frac{1.225\times5\times0.20}{1.79\times10^{-5}}=6.844\times10^4.
$$

The given correlation is local. Written for $h_x$, it is

$$
h_x=\frac{k}{x}\,0.332\,\text{Re}_x^{1/2}\text{Pr}^{1/3}=0.332\,k\,\text{Pr}^{1/3}\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}x^{-1/2}.
$$

The mean coefficient over the plate is the average of $h_x$ along it:

$$
\bar h=\frac{1}{L}\int_0^Lh_x\,\mathrm{d}x=\frac{0.332\,k\,\text{Pr}^{1/3}}{L}\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\int_0^Lx^{-1/2}\,\mathrm{d}x.
$$

$$
\bar h=\frac{0.332\,k\,\text{Pr}^{1/3}}{L}\left(\frac{\rho U_\infty}{\mu}\right)^{1/2}\,2L^{1/2}.
$$

$$
\bar h=\frac{k}{L}\,0.664\,\text{Re}_L^{1/2}\text{Pr}^{1/3},
$$

so the mean Nusselt number is $\overline{\text{Nu}}_L=0.664\,\text{Re}_L^{1/2}\text{Pr}^{1/3}$, twice the local value at $x=L$. With the numbers above,

$$
\overline{\text{Nu}}_L=0.664\times(6.844\times10^4)^{1/2}\times0.7^{1/3}=0.664\times261.60\times0.88790=154.23,
$$

$$
\bar h=\frac{\overline{\text{Nu}}_L\,k}{L}=\frac{154.23\times0.02569}{0.20}=19.81\ \text{W/(m}^2\text{ K)}.
$$

The total heat transfer from one face of the plate is

$$
\dot Q=\bar h\,(Lw)\,\Delta T=19.81\times(0.20\times0.10)\times30=\boxed{11.9\ \text{W}},
$$

a mean heat flux of $11.9/0.02=594\ \text{W/m}^2$.

#### (c) Laminar check

$\text{Re}_L=6.84\times10^4$ is well below the usual flat-plate transition value of about $5\times10^5$, so the boundary layer is laminar over the whole plate, as assumed.

### (ii) Lunar re-entry shock layer and surface radiative equilibrium [6 marks]

On return from the Moon a capsule enters at about $11$ km/s. A strong detached bow shock stands ahead of the blunt heat shield, and the gas in the shock layer between the shock and the thin boundary layer is heated to around $10\,000$ K, where it is dissociated and partly ionised. At these temperatures the shock layer radiates strongly, so the wall receives a radiative heat flux $q_{\text{rad}}$ from the gas in addition to the convective flux $q_{\text{conv}}$, and at lunar return speeds the radiative part is a large fraction of the total. The hot surface also loses heat by radiating outwards, $\varepsilon\sigma T_w^4$, where $\varepsilon$ is the surface emissivity.

If conduction into the structure is neglected, the surface reaches radiative equilibrium when the heat it radiates equals the heat it receives:

$$
q_{\text{conv}}+q_{\text{rad}}=\varepsilon\sigma T_w^4,
$$

$$
T_w=\left(\frac{q_{\text{conv}}+q_{\text{rad}}}{\varepsilon\sigma}\right)^{1/4}.
$$

### (iii) Richardson extrapolation and further CFD checks [10 marks]

For a uniformly second-order method the error in $C_H$ on a grid of spacing $h$ is $Kh^2$ to leading order, so

$$
C_{H,1}=C_{H,\text{exact}}+Kh_1^p,
$$

$$
C_{H,2}=C_{H,\text{exact}}+Kh_2^p,
$$

with $p=2$. The $200\times200$ grid halves the spacing of the $100\times100$ grid, so $r=h_1/h_2=2$ and $h_1^p=r^ph_2^p$. Subtract the second equation from the first:

$$
C_{H,1}-C_{H,2}=Kh_2^p\left(r^p-1\right),
$$

$$
Kh_2^p=\frac{C_{H,1}-C_{H,2}}{r^p-1}.
$$

Put this into the second equation:

$$
C_{H,\text{exact}}=C_{H,2}-Kh_2^p=C_{H,2}+\frac{C_{H,2}-C_{H,1}}{r^p-1}.
$$

Substitute $C_{H,1}=0.0821$, $C_{H,2}=0.0762$, $r=2$, $p=2$:

$$
C_{H,\text{exact}}=0.0762+\frac{0.0762-0.0821}{2^2-1}=0.0762-\frac{0.0059}{3}=\boxed{0.0742}.
$$

Besides grid refinement, the solution should be checked as follows:

- iterative convergence: the residuals have fallen by several orders of magnitude and the peak $C_H$ and the shock stand-off distance no longer change;
- conservation: mass, momentum and energy balance over the domain, and the fitted shock satisfies the Rankine–Hugoniot relations;
- independence of numerical and domain choices: time step or CFL number, position of the outer and outflow boundaries, and the outflow staying supersonic;
- validation of the physical modelling, including the radiation and gas chemistry, against flight or shock-tube data or established correlations for stagnation-point heating.

---

## Paper slips and ambiguities

- Q3 data. The given states are consistent with an evenly spaced four-line fan: $R^+_4=2.68^\circ$, $R^+_7=22.05^\circ$, $R^-_7=41.41^\circ$ and $R^-_4=60.78^\circ$ are $2\theta$ for fan angles $1.34^\circ$, $11.03^\circ$, $20.71^\circ$ and $30.39^\circ$, spaced $9.69^\circ$ apart. That makes $\nu(M_e)=60.78^\circ$ and $M_e=3.65$, slightly above the stated $3.6$ ($\nu(3.6)=60.09^\circ$). The answers use the given point data. An earlier draft called the equal Mach numbers at points 4 and 7 an exam convention; they follow from the even spacing.
- Q3 sign convention. An earlier draft used Anderson's $K^+=\theta-\nu$ under the name $R^+$. The solution above uses the course's $R^+=\nu-\theta$; the values of $\theta_8$ and $\nu_8$ are unchanged.
- Q4(i)(c). An earlier draft used $3\times10^5$ as the transition Reynolds number; the usual flat-plate value is about $5\times10^5$. Either way $\text{Re}_L=6.84\times10^4$ is laminar.
