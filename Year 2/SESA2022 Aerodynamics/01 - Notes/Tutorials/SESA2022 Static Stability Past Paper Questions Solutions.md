---
title: "SESA2022 Static Stability Past Paper Questions Solutions"
module: "SESA2022 Aerodynamics"
type: tutorial
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
tags:
  - sesa2022
  - tutorial-solutions
  - static-stability
  - past-papers
sheet: "Past paper questions (SESA2025 Mechanics of Flight Q2, 2021-22 to 2024-25)"
theory_notes: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]"]
key_concepts: ["[[Neutral Point and Static Margin]]", "[[Maximum Lift-to-Drag Ratio]]"]
status: complete
sources: ["02 - Sources/Stability/Past_paper_questions_static_stability.pdf"]
---

# SESA2022 Static Stability Past Paper Questions Solutions

> [!abstract] Sheet Info
> These are the static-stability questions from SESA2025 *Mechanics of Flight* papers, provided with the Topic 6 material. The lecturer's answer keys are included in the PDF, and every value below reproduces them unless flagged ⚠.

Common definitions (see [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]):

$$
K=\frac{S_Tl}{Sc},\quad C_{L_\alpha}=a_0\frac{\pi Ae}{\pi Ae+a_0},\quad \epsilon_\alpha=\frac{C_{L_\alpha}}{\pi Ae},\quad k=a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1},\quad C_{L_{T,\alpha}}=k(1-\epsilon_\alpha),\quad H_s=h_0-h+K\frac{C_{L_{T,\alpha}}}{C_{L_\alpha}+C_{L_{T,\alpha}}S_T/S}
$$

---

## 2024-25 Q2: Air-racing aircraft

**Data**: $g=9.81$, $m=726$ kg, $\rho=1.225$, $A=9$, $S=10$ m², $e=0.85$, $A_T=3$, $S_T=2$ m², $e_T=0.70$, $h_0=0.25$, $h=0.20$, $l=3.5$ m, $\gamma=0$, $C_{M_0}=-0.01$, $a_0=a_1=2\pi$, $a_2=3.5$, $\alpha_s=0$. Rectangular wing: $c=\sqrt{S/A}$.

### (i) Zero-lift angle $\alpha_0$ to trim with $\eta = 0$ at $V = 86$ m/s (stick fixed)
- $c = \sqrt{10/9} = 1.0541$ m, $K = \dfrac{2(3.5)}{10(1.0541)} = 0.6641$
- $C_{L^*} = C_W = \dfrac{726(9.81)}{\tfrac12(1.225)(86^2)(10)} = 0.1572$
- $C_{L_T} = \dfrac{C_{M_0}+C_{L^*}(h-h_0)}{K} = \dfrac{-0.01+0.1572(-0.05)}{0.6641} = -0.0269$ (a download, because the CG is ahead of the AC)
- $C_L = C_{L^*}-C_{L_T}S_T/S = 0.1572+0.0054 = 0.1626$
- $C_{L_\alpha} = 2\pi\dfrac{\pi(9)(0.85)}{\pi(9)(0.85)+2\pi} = 4.9810$ rad⁻¹, $\epsilon_\alpha = 4.9810/24.033 = 0.2073$
- With $\eta=0$: $\alpha_{T_{eff}} = C_{L_T}/a_1 = -4.28\times10^{-3}$ rad

Substitute $\alpha = \alpha_0+C_L/C_{L_\alpha}$ into $\alpha_{T_{eff}} = (1-\epsilon_\alpha)\alpha+\epsilon_\alpha\alpha_0+\alpha_s-\dfrac{C_{L_T}}{\pi A_Te_T}$. The $\alpha_0$ terms combine to $\alpha_0$:

$$
\alpha_0 = \alpha_{T_{eff}}-(1-\epsilon_\alpha)\frac{C_L}{C_{L_\alpha}}+\frac{C_{L_T}}{\pi A_Te_T} = -0.00428-0.7927(0.03264)-\frac{0.0269}{6.597} = \boxed{-0.0342\text{ rad} = -1.96^\circ}
$$

### (ii) Static margin
$k = 2\pi\dfrac{6.597}{6.597+2\pi} = 3.2182$, $C_{L_{T,\alpha}} = 3.2182(0.7927) = 2.5512$, $C_{L^*_\alpha} = 4.9810+2.5512(0.2) = 5.4912$

$$
H_s = 0.25-0.20+0.6641\frac{2.5512}{5.4912} = \boxed{0.3585}
$$

The aircraft is statically stable with a large margin (35.9% MAC). That makes it very stiff in pitch, which is **not ideal for an air racer** that needs manoeuvrability.

### (iii) Reduce $H_s$ to 28%
The options are to move the neutral point forward or the CG aft:
- Move the CG aft (increase $h$).
- Reduce the tail volume $K$: smaller $S_T$, shorter $l$, or larger $S$ or $c$.
- Reduce $C_{L_{T,\alpha}}$: lower $A_T$ or $e_T$.
- Increase $C_{L_\alpha}$: raise $A$ via the geometry.

### (iv) Wing aspect ratio only, $A = 5$ (same $S$)
$c = \sqrt{10/5} = 1.4142$, $K = 0.4950$, $C_{L_\alpha} = 4.2726$, $\epsilon_\alpha = 0.3200$, $C_{L_{T,\alpha}} = 3.2182(0.68) = 2.1884$, $C_{L^*_\alpha} = 4.7102$

$$
H_s = 0.05+0.4950\frac{2.1884}{4.7102} = \boxed{0.2800}
$$

### (v) Interpolate for $H_s = 0.28$
The points are $(A,H_s) = (5, 0.2800)$ and $(9, 0.3585)$, giving slope $0.0196$ per unit $A$:

$$
A = 5+\frac{0.28-0.2800}{0.0196} = \boxed{5.00}
$$

A lower aspect ratio means a larger chord, so a smaller $K$ and more wing downwash, which gives less margin.

---

## 2023-24 Q2: Piston aircraft for elephant surveys (always stick fixed)

**Data**: $A=8$, $e=0.9$, $S=20$ m², $A_T=7$, $e_T=0.85$, $S_T=3$ m², $l=7$ m, $c=1.58$ m, $h_0=0.25$, $C_{M_0}=-0.01$, $C_{D_0}=0.01$, $\gamma=0$, $m=1500$ kg, $\rho=1.0$, $a_0=a_1=2\pi$.

### (i) Speed and CG for maximum range, stability check, and the $H_s = 0.3$ penalty
**Maximum range for a piston/propeller aircraft** means maximum $L/D$ (Breguet: $R\propto\frac{\eta_p}{c}\frac{L}{D}$). Here range $\propto C_{L^*}/C_D$, where the drag includes the **tail's induced drag**:

$$
C_D = C_{D_0}+\frac{C_L^2}{\pi Ae}+\frac{S_T}{S}\frac{C_{L_T}^2}{\pi A_Te_T},\qquad C_{L^*} = C_L+\frac{S_T}{S}C_{L_T}
$$

Minimising $C_D$ for a given $C_{L^*}$ (Lagrange multipliers) gives the **optimal lift split**:

$$
\frac{C_{L_T}}{C_L} = \frac{\pi A_Te_T}{\pi Ae} = \frac{18.692}{22.619} = 0.8264
$$

With $f = 1+\frac{S_T}{S}(0.8264) = 1.12396$, both $C_{L^*}$ and the induced drag scale by $f$. So

$$
C_{L^*,opt} = \sqrt{\pi Ae\,C_{D_0}f} = \sqrt{22.619(0.01)(1.12396)} = 0.5042
$$

$$
V = \sqrt{\frac{2mg}{\rho SC_{L^*}}} = \sqrt{\frac{2(14715)}{1.0(20)(0.5042)}} = \boxed{54.02\text{ m/s}}
$$

$C_L = 0.5042/1.12396 = 0.4486$ and $C_{L_T} = 0.8264(0.4486) = 0.3707$. The CG position follows from the moment equation:

$$
h_{opt} = h_0+\frac{C_{L_T}K-C_{M_0}}{C_{L^*}} = 0.25+\frac{0.3707(0.66456)+0.01}{0.5042} = \boxed{0.7584}
$$

**Stability**: $h_n = h_0+K\dfrac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}} = 0.25+0.66456\dfrac{3.6802}{5.4693} = \boxed{0.6971}$. Since $h_{opt}>h_n$ the design is **statically unstable** ($H_s<0$).

**With $H_s = 0.3$**: $h = h_n-0.3 = 0.397$. The key quotes $h = 0.3917$ ⚠. That is about 0.3054 behind $h_n$, probably from rounding; both give the same range penalty. At $V = 60$ m/s:
- $C_{L^*} = 0.4088$, $C_{L_T} = 0.0755$, $C_L = 0.3974$
- $C_D = 0.01+0.006983+0.000046 = 0.01703$, so $L/D = 24.00$

The optimum is $(L/D)_{max} = C_{L^*,opt}/(2C_{D_0}) = 25.21$ (at the optimum, induced drag equals $C_{D_0}$). So the

$$
\text{range reduction} = 1-\frac{24.00}{25.21} = \boxed{4.8\%}
$$

### (ii) Neutral point from flight test (Figure 1)
Read the slopes of $\eta$ vs $C_{L^*}$ from the figure:
- $h = 0.2$: $d\eta/dC_{L^*}\approx-0.31$ rad per unit $C_{L^*}$ (from about $0.23$ at $C_{L^*}=0$ down to about $-0.18$ at $1.33$)
- $h = 0.4$: $d\eta/dC_{L^*}\approx-0.17$

The slope varies linearly with $h$ and is zero at $h_n$:

$$
h_n = 0.2+0.2\frac{-0.31}{-0.31+0.17}\approx0.64\text{–}0.70
$$

The result is sensitive to how you read the slopes; the key gives $\boxed{h_n = 0.702}$. For $H_s = 0.3$ the CG must be no further aft than $h \approx 0.40$. At $h = 0.27$, $H_s\approx0.43 > 0.3$, so the requirement is **satisfied** ✔.

---

## 2022-23 Q2: Civil aircraft (descent) and a student UAV

### (i) Tailplane setting for trim without elevator, then the damaged stabiliser
**Data**: $a_0=a_1=2\pi$, $a_2=2.9$, $e=0.92$, $e_T=0.90$, $A=11$, $S=90$, $S_T=10$, $h=0.27$, $l=34$, $c=4.8$, $m=120000$, $C_{M_0}=-0.2$, $h_0=0.22$, $\alpha_0=-7^\circ$, $\rho=1.0$, $A_T=8$, $\gamma=-8^\circ$, $V=192$ m/s.

- $K = \dfrac{10(34)}{90(4.8)} = 0.7870$, $C_{L_\alpha} = 5.2464$, $\epsilon_\alpha = 0.1650$
- $C_{L^*} = \dfrac{mg\cos\gamma}{\tfrac12\rho V^2S} = 0.7027$
- $C_{L_T} = \dfrac{-0.2+0.7027(0.05)}{0.7870} = -0.2095$
- $C_L = 0.7027+0.2095(0.111) = 0.7260$
- $\alpha = -7^\circ+\dfrac{0.7260}{5.2464} = 0.929^\circ$
- $\epsilon = \epsilon_\alpha(\alpha-\alpha_0) = 1.308^\circ$, $\epsilon_T = \dfrac{C_{L_T}}{\pi A_Te_T} = -0.531^\circ$

With $\eta = 0$, $C_{L_T} = a_1(\alpha+\alpha_s-\epsilon-\epsilon_T)$, so

$$
\alpha_s = \frac{C_{L_T}}{a_1}-\alpha+\epsilon+\epsilon_T = -1.910^\circ-0.929^\circ+1.308^\circ-0.531^\circ = \boxed{-2.06^\circ}
$$

**Stabiliser limited to $\alpha_s = -1^\circ$**:

$$
\eta = \frac{C_{L_T}-a_1(\alpha+\alpha_s-\epsilon-\epsilon_T)}{a_2} = \boxed{-2.30^\circ}
$$

The elevator must be deflected 2.30° upward (trailing edge up).

### (ii) Student UAV: tail enlargement claim
**Data**: $a_0=a_1=2\pi$, $A_T=9$, $e=0.8$, $e_T=0.7$, $A=13.6$, $S=3.4$, $S_T=0.31$, $h=0.57$, $l=3.2$, $c=0.5$, $h_0=0.38$. The requirement is $H_s\ge0.25$.

(a) $K = 0.5835$ gives $H_s = \boxed{0.224} < 0.25$, so the team mate is right that it **fails**.

(b) With $S_T\times1.15 = 0.3565$ m² ($K = 0.6711$) and the CG moving aft by 2% ($h = 0.59$): $H_s = \boxed{0.262}\ge0.25$, so it **satisfies** the requirement ✔ (the key says 0.26).

---

## 2021-22 Q2: Flight tests and fuel-transfer trim

### (i) Neutral point from flight tests
$m = 1500$ kg, $S = 32$ m², $\rho = 1.225$.

| $h$ | $V$ | $\eta$ |
|---|---|---|
| 0.34 | 80 | $-1^\circ$ |
| 0.34 | 90 | $1^\circ$ |
| 0.37 | 80 | $-0.5^\circ$ |
| 0.37 | 90 | $1.2^\circ$ |

- $C_{L^*}(80) = \dfrac{14715}{\tfrac12(1.225)(6400)(32)} = 0.1173$ and $C_{L^*}(90) = 0.0927$
- Slopes: $\left.\dfrac{d\eta}{dC_{L^*}}\right|_{0.34} = \dfrac{1-(-1)}{0.0927-0.1173} = -81.2$ deg and $\left.\dfrac{d\eta}{dC_{L^*}}\right|_{0.37} = -69.05$ deg

The slope varies linearly with $h$ and vanishes at $h_n$:

$$
h_n = 0.34-(-81.235)\frac{0.03}{-69.05+81.235} = \boxed{0.540}\;(54\%\text{ MAC})
$$

### (ii) CG position for trim without control deflection
**Data**: $A=8$, $S=3.78$, $e=0.9$, $m=45$ kg, $S_T=0.54$, $a_0=2\pi$, $l=5$, $c=0.7$, $C_{M_0}=-0.006$, $\alpha_0=-0.9^\circ$, $\rho=1.225$, $V=20$, $\alpha=4.6^\circ$, $h_0=0.25$.

- $C_{L^*} = \dfrac{45(9.81)}{\tfrac12(1.225)(400)(3.78)} = 0.4767$
- $C_{L_\alpha} = 4.9173$, so $C_L = 4.9173(4.6+0.9)^\circ = 0.4720$
- $C_{L_T} = (C_{L^*}-C_L)\dfrac{S}{S_T} = 0.0326$
- $K = \dfrac{0.54(5)}{3.78(0.7)} = 1.0204$

$$
h = h_0+\frac{C_{L_T}K-C_{M_0}}{C_{L^*}} = 0.25+\frac{0.0326(1.0204)+0.006}{0.4767} = \boxed{0.332}\;(33.2\%\text{ MAC})
$$

## Sources
- `02 - Sources/Stability/Past_paper_questions_static_stability.pdf` (questions and lecturer keys)
- All numbers verified in Python
