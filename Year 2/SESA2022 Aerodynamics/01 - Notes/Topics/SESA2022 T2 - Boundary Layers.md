---
title: "SESA2022 T2 - Boundary Layers"
module: "SESA2022 Aerodynamics"
type: topic
stream: "Topic 2: Incompressible Viscous Flow"
order: 2
tags:
  - sesa2022
  - boundary-layers
  - viscous-flow
aliases: ["Boundary Layers", "Incompressible Viscous Flow"]
date: 2026-09-23
status: complete
parent: ["[[SESA2022 Aerodynamics Hub]]"]
prerequisites: ["[[Streamfunction and Velocity Potential]]"]
next_topics: ["[[SESA2022 T3 - Potential Flow]]"]
key_concepts: ["[[Displacement and Momentum Thickness]]", "[[Momentum Integral Equation]]", "[[Law of the Wall]]", "[[Virtual Origin Method]]", "[[Boundary Layer Separation]]"]
tutorial_sheets: ["[[SESA2022 Tutorial 2 - Viscous Flow Solutions]]"]
sources: ["02 - Sources/BL/Topic 2 Boundary layers.pdf", "02 - Sources/BL/BLs.txt (lecture transcript)"]
---

# SESA2022 T2 - Boundary Layers

> [!abstract] Summary
> The **no-slip condition** forces the fluid velocity to zero at a wall, creating a thin **boundary layer (BL)** where viscosity matters. We characterise it with integral thicknesses ($\delta$, $\delta^*$, $\theta$, $H$), link its growth to **skin-friction drag** through the **momentum integral equation** ($c_f = 2\,d\theta/dx$), approximate laminar and turbulent profiles, describe the turbulent near-wall region with the **law of the wall**, handle **transition** with the **virtual origin method**, and explain **separation** under adverse pressure gradients.

## Key Concepts

- [[Displacement and Momentum Thickness]]: $\delta^*$, $\theta$, shape factor $H$
- [[Momentum Integral Equation]]: $c_f = 2\,d\theta/dx$ and $D'(x) = \rho U_\infty^2\theta(x)$
- [[Law of the Wall]]: inner units $U^+$, $y^+$
- [[Virtual Origin Method]]: drag for a plate with transition
- [[Boundary Layer Separation]]: favourable vs adverse pressure gradients, stall, bluff bodies

---

## 1. No-slip condition and the boundary layer

- Molecules hitting a surface leave with (on average) the surface velocity (diffuse reflection), so the fluid velocity at the wall equals the wall velocity.
- Any "slip" velocity is of order mean free path ($\sim10^{-8}$ m in air) × velocity gradient, which is negligible.
- **Exceptions**: rarefied flows where the Knudsen number $Kn > 0.01$ (hypersonics, micro-fluidics).

The BL develops from the leading edge as **laminar**, becomes unstable, **transitions**, and becomes **fully turbulent**. In a turbulent BL the velocity must be *time-averaged* at each point; a Pitot probe does this automatically because its frequency response is low.

![[bl_profiles.png|560]]

**Laminar vs turbulent profiles:**
- The turbulent BL is *fuller*: it recovers $U_\infty$ closer to the wall but is *thicker* overall.
- The turbulent BL has a **larger wall velocity gradient**, which gives a larger wall shear stress $\tau_w$ and so **more skin-friction drag**.

$$
\tau_w = \mu\left.\frac{du}{dy}\right|_{y=0}, \qquad c_f = \frac{\tau_w}{\tfrac12\rho U_\infty^2} = \frac{2\nu}{U_\infty^2}\left.\frac{du}{dy}\right|_{y=0}
$$

## 2. Measures of boundary-layer thickness

See [[Displacement and Momentum Thickness]] for the full definitions and physical meaning.

| Quantity | Definition | Meaning |
|---|---|---|
| $\delta = \delta_{99}$ | $u(\delta_{99}) = 0.99\,U_\infty$ | Edge of the BL (use linear interpolation in data) |
| $\delta^*$ | $\displaystyle\int_0^\infty\left(1-\frac{u}{U_\infty}\right)dy$ | How far the wall must be displaced in inviscid flow to give the same mass-flow deficit |
| $\theta$ | $\displaystyle\int_0^\infty\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)dy$ | Momentum deficit, directly proportional to the drag |
| $H$ | $\delta^*/\theta$ | Shape factor: laminar $H>2$ (Blasius $2.59$), turbulent $H<2$ |

In non-dimensional form with $\eta = y/\delta$:
$$
\frac{\delta^*}{\delta} = \int_0^1\left(1-\frac{u}{U_\infty}\right)d\eta,\qquad \frac{\theta}{\delta} = \int_0^1 \frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)d\eta
$$

> [!tip] Numerical evaluation
> With measured data use `np.trapz` (trapezoidal rule) on $y$ and $u/U_\infty$ up to $\delta$. The lecture's Python examples read the `.csv` with `pandas` (`pd.read_csv`, `pd.read_excel`).

## 3. Momentum integral equation and drag

For a flat plate at zero pressure gradient, apply mass and momentum conservation to a control volume from the leading edge ($x=0$) to $x$. The derivation is in [[Momentum Integral Equation]].

$$
\boxed{D'(x) = \rho U_\infty^2\,\theta(x)} \qquad\text{(drag per unit span, one side)}
$$

Differentiating, with $dD'/dx = \tau_w$:

$$
\boxed{c_f = 2\frac{d\theta}{dx}} \qquad \boxed{C_F = \frac{D'}{\tfrac12\rho U_\infty^2 L} = \frac{2\,\theta(L)}{L} = \frac1L\int_0^L c_f\,dx}
$$

- A plate has **two sides**, so the total $C_F$ (based on one planform area) is doubled.
- The same $\theta$-drag relation gives the **drag of a body from its wake**: integrate $\frac{u}{U_\infty}\left(1-\frac{u}{U_\infty}\right)$ across the wake (Tutorial 2 Q5).
- The MIE with a pressure gradient (Falkner–Skan) is beyond this module.

## 4. Approximate laminar profiles

**Self-similarity** (Blasius, 1908): the profiles $u/U_e$ vs $y/\delta$ collapse at every $x$. The same holds approximately for turbulent BLs.

### Worked derivation: linear profile $u/U_\infty = \eta$

$$
\frac{\delta^*}{\delta}=\int_0^1(1-\eta)\,d\eta=\tfrac12,\qquad \frac{\theta}{\delta}=\int_0^1\eta(1-\eta)\,d\eta = \tfrac16,\qquad H = 3
$$

Apply the MIE with $\tau_w = \mu U_e/\delta$ and $\delta = 6\theta$:

$$
\frac{d\theta}{dx} = \frac{\nu}{U_e^2}\frac{U_e}{\delta} = \frac{\nu}{6U_e\theta}\;\Rightarrow\;\theta\,d\theta = \frac{\nu}{6U_e}dx\;\Rightarrow\;\theta = \sqrt{\frac{\nu x}{3U_e}}
$$

$$
\frac{\theta}{x}=\frac{0.577}{\sqrt{Re_x}},\qquad \frac{\delta^*}{x}=\frac{1.732}{\sqrt{Re_x}},\qquad c_f=\frac{0.577}{\sqrt{Re_x}}
$$

### Blasius (exact) solution

$$
\frac{\delta}{x}=\frac{4.91}{\sqrt{Re_x}},\quad \frac{\delta^*}{x}=\frac{1.721}{\sqrt{Re_x}},\quad \frac{\theta}{x}=\frac{0.664}{\sqrt{Re_x}},\quad H=2.59,\quad c_f=\frac{0.664}{\sqrt{Re_x}},\quad C_F = \frac{1.328}{\sqrt{Re_L}}
$$

> [!example] Example (lecture): laminar UAV wing
> Wing chord $c = 0.2$ m, span $b = 1.2$ m, speeds 6–15 m/s, fully laminar, two sides.
> - $C_F$ per side $= 1.328/\sqrt{Re_c}$. Total viscous drag $D = 2\times\tfrac12\rho U^2 (bc)\, C_F$.
> - At 12 m/s: $Re_c = 12(0.2)/1.5\times10^{-5} = 1.6\times10^5$, $C_F = 1.328/400 = 0.00332$ per side, $D = 2(0.5)(1.225)(144)(0.24)(0.00332) \approx 0.14$ N.

> [!example] Exam-style: parabolic profile $u/U = 2\eta-\eta^2$ (2024-25 Q1)
> - $\delta^*/\delta = 1/3$, $\theta/\delta = 2/15$, so $H = 2.5$.
> - $\tau_w = 2\mu U/\delta$. The MIE gives $\theta\,d\theta/dx = \tfrac{4}{15}\nu/U$, so
>
> $$\frac{\theta}{x} = \sqrt{\frac{8}{15}}\frac{1}{\sqrt{Re_x}} = \frac{0.730}{\sqrt{Re_x}},\qquad c_f = \frac{0.730}{\sqrt{Re_x}}$$
>
> Full solution: [[SESA2022 Exam 2024-25 Solutions]].

## 5. Turbulent boundary layers

**Properties of turbulence**:
- Chaotic and unsteady, with a wide range of interacting eddies. The ratio of largest to smallest scales grows with $Re$.
- Richardson: "Big whorls have little whorls that feed on their velocity…"
- Real flows are almost always turbulent, so predicting turbulent drag matters (for example, the 50% emissions-reduction targets).

**Tools** (a trade-off between accuracy and cost):

| Tool | What it does | Cost |
|---|---|---|
| Force/pressure measurements, Pitot | Mean quantities | Low |
| Hot-wire, PIV | Fluctuations, full field | Medium to high |
| **RANS** | Solve the mean flow and *model* all turbulence (Reynolds stresses, closure problem: $k$–$\omega$, $k$–$\epsilon$, SA) | Low |
| **LES** | Resolve large eddies and model small ones | High |
| **DNS** | Resolve all scales; limited to low $Re$ | Very high |

### Power-law profile

$$
\frac{u}{U_\infty} = \left(\frac{y}{\delta}\right)^{1/n}\quad(n \approx 7\text{, found by fitting data})
$$

With $n=7$: $\;\delta^*/\delta = 1/8$, $\theta/\delta = 7/72$, $H = 9/7 \approx 1.29$.

> [!warning] Drawback
> $du/dy|_{y=0} = \infty$, so the power law **cannot give $\tau_w$**. We use empirical correlations for $c_f$ instead (below), or the [[Law of the Wall]].

Once $n$ is known at one station, the same $n$ applies at other stations of the same flow (self-similarity).

### Summary of flat-plate correlations

Use these only if you cannot get the values directly from the data.

| Property | Laminar (Blasius) | Turbulent ($n=7$ + data) |
|---|---|---|
| $\delta/x$ | $4.91/\sqrt{Re_x}$ | $0.38/Re_x^{1/5}$ |
| $\delta^*/x$ | $1.72/\sqrt{Re_x}$ | $0.048/Re_x^{1/5}$ |
| $\theta/x$ | $0.664/\sqrt{Re_x}$ | $0.037/Re_x^{1/5}$ |
| $c_{f,x}$ | $0.664/\sqrt{Re_x}$ | $0.059/Re_x^{1/5}$ |
| $C_F$ (one side) | $1.328/\sqrt{Re_L}$ | $0.074/Re_L^{1/5}$ |

![[bl_cf_transition.png|560]]

> [!example] Example (lecture): AUV, fully turbulent
> $c = 3$ m, $U = 2$ m/s in water ($\nu = 10^{-6}$): $Re_c = 6\times10^6$, so $C_F = 0.074/Re_c^{1/5} = 0.0033$.

**Fitting correlations to data**: assume $\theta/x = A\,Re_x^{b}$ and fit with `curve_fit`. The lecture data gave $A = 0.0729$, $b = -0.1968$ (close to $-1/5$).

## 6. Law of the wall

The outer scaling ($U_\infty$, $\delta$) hides the near-wall physics. Instead, use **inner (wall/plus) units**:

$$
U_\tau = \sqrt{\frac{\tau_w}{\rho}} = U_\infty\sqrt{\frac{c_f}{2}},\qquad l = \frac{\nu}{U_\tau},\qquad U^+ = \frac{U}{U_\tau},\qquad y^+ = \frac{yU_\tau}{\nu}
$$

$$
U^+ = \begin{cases} y^+ & y^+ < 5 \quad\text{(viscous sub-layer)}\\[4pt] \dfrac{1}{\kappa}\ln y^+ + B & y^+ > 50 \text{ and } y/\delta < 0.2\quad\text{(log layer)}\end{cases}
$$

- Slides: $\kappa = 0.4$, $B = 5.0$. **2024-25 exam rubric: $\kappa = 0.39$, $B = 4.3$.** The constants are empirical, so use whatever the paper gives.
- $5 < y^+ < 50$ is the **buffer layer**, where neither law fits.
- **CFD**: the first grid point should sit at $y^+ < 5$. Estimate $U_\tau$ from the flat-plate $c_f$ correlation, run the simulation, then check.

![[bl_law_of_wall.png|600]]

> [!example] Example (lecture)
> Turbulent profile: $U_\tau = U_\infty\sqrt{c_f/2}$. At $y = 1$ mm: $y^+ = 55$, $y/\delta = 0.2$, which is borderline log region. So $U = U_\tau\left(\tfrac{1}{\kappa}\ln 55 + B\right)$.

> [!example] Exam-style: riblet sizing (2023-24 Part A Q1v)
> Riblets 10 wall units high: $h = 10\nu/U_\tau$ with $c_f = 0.059Re_x^{-1/5}$. For $U_0 = 15$ m/s, $X = 3$ m: $Re = 3\times10^6$, $c_f = 0.002988$, $U_\tau = 0.580$ m/s, $h = 258.7\ \mu$m.

## 7. Transition and the virtual origin method

On a log–log plot, laminar $c_f$ has slope $-1/2$ and turbulent $c_f$ has slope $-1/5$. Transition typically happens at $Re_{x_T} \approx 3\times10^5$ to $10^6$.

**Method** (see [[Virtual Origin Method]]):
1. **Assumption**: $\theta_{lam}(x_T) = \theta_{turb}(x_T)$. The momentum thickness is continuous at transition.
2. Turbulent growth is measured from a **virtual origin** $x_0 < x_T$:

$$
\frac{0.664\,x_T}{\sqrt{U_\infty x_T/\nu}} = \frac{0.037\,(x_T-x_0)}{\left[U_\infty(x_T-x_0)/\nu\right]^{1/5}}
$$

   Solve for $x_0$ with `fsolve`. Last resort: $x_0 \approx x_T\left(1-38\,Re_{x_T}^{-3/8}\right)$.
3. The total plate drag comes from the **trailing-edge turbulent $\theta$ relative to $x_0$**:

$$
D' = \rho U_\infty^2\,\theta(c-x_0),\qquad C_F = 0.074\left(1-\frac{x_0}{c}\right)Re_{c-x_0}^{-1/5}
$$

![[bl_virtual_origin.png|560]]

> [!example] Lecture example
> $L = 0.3$ m. From the turbulent data, $x_0 = 0.187$ m, and matching with the laminar $\theta$ gives $x_T = 0.28$ m. Check: $x_0$ from the correlation is $0.185$ m, and $Re_{x_T} \approx 3\times10^5$. ✔

> [!example] Tutorial 2 Q4
> Symmetric thin foil, $Re_c = 6\times10^5$, transition at mid-chord: $x_0 = 0.337c$, $\theta_{TE} = 1.86\times10^{-3}c$, $C_F \approx 0.0073$ (both sides). Worked in [[SESA2022 Tutorial 2 - Viscous Flow Solutions]].

**Delaying transition** (passive distributed roughness, active actuators) reduces drag. This is ongoing research, and harder in high-speed flows because of shocks.

## 8. Pressure gradients and separation

- **Favourable** pressure gradient (FPG): $dp/dx < 0$, which accelerates the flow.
- **Adverse** pressure gradient (APG): $dp/dx > 0$, which decelerates the flow everywhere including near the wall. Eventually $\partial u/\partial y|_{y=0} = 0$ ($\tau_w = 0$) and the flow **separates**. On aerofoils this is **stall**.
- A **laminar BL separates earlier** because it has less near-wall momentum, giving a bigger separated region.
- **Tripping to turbulent** increases mixing and delays separation, giving a smaller wake and **lower pressure drag**. Examples: golf-ball dimples, trips on wind-tunnel models to mimic flight $Re$.
- **Bluff bodies**: early separation leads to **vortex shedding** and unsteady forces. Sharp corners separate immediately. That is why bodies are **streamlined**.

See [[Boundary Layer Separation]] and [[D'Alembert's Paradox]].

## Examples

> [!example] Tutorial 2 Q2: Remus-100 AUV, $L=1.6$ m, $U=2$ m/s, $\nu=10^{-6}$
> $Re_L = 3.2\times10^6$ (likely turbulent). Laminar gives $\delta = 4.4$ mm; **turbulent gives $\delta = 0.38L/Re_L^{1/5} = 30.4$ mm**. Use a safety factor because the correlation is empirical.

More in [[SESA2022 Tutorial 2 - Viscous Flow Solutions]] and the exam solutions linked from [[SESA2022 Past Paper Map]].

## Links

- Parent dashboard: [[SESA2022 Aerodynamics Hub]]
- Thermofluids foundation: [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]
- Next topic: [[SESA2022 T3 - Potential Flow]]
- Uses: [[Streamfunction and Velocity Potential]] (inviscid outer flow)
- Feeds into: Year 3 [[SESA3043 Advanced Aeronautics]] (viscous–inviscid interaction, XFOIL) and [[SESA3029 Aerothermodynamics]] (compressible BLs)
- Formula sheet: [[SESA2022 Formula Sheet]]

## Sources

- `02 - Sources/BL/Topic 2 Boundary layers.pdf` (slides 1–63)
- Lecture transcript `02 - Sources/BL/BLs.txt`
- Anderson, *Fundamentals of Aerodynamics*, Ch. 17–19
