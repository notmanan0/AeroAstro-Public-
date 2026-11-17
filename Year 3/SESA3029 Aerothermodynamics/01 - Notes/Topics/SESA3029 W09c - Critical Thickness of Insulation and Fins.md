---
title: "SESA3029 W09c - Critical Thickness of Insulation and Fins"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 5: Heat transfer"
order: 12
tags: [sesa3029, heat-transfer, conduction, convection, insulation, critical-radius, fins, extended-surfaces, fin-efficiency, fin-effectiveness]
aliases: ["SESA3029 Lecture 5.4", "SESA3029 W09c"]
date: 2026-11-17
status: written-ahead
coverage: "Lecture 5.4 (all 25 slides) written ahead from the slides; no transcript yet"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]", "[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]"]
next_topics: ["[[SESA3029 W09d - Thermal Radiation]]"]
key_concepts: ["[[Critical Radius of Insulation]]", "[[Fin Equation]]", "[[Fin Efficiency and Effectiveness]]", "[[Newton's Law of Cooling]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 3 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.4(1).pdf"]
---

# SESA3029 W09c - Critical Thickness of Insulation and Fins

> [!abstract] Summary
> Both halves of this topic come from conduction and convection acting in series on a surface whose area changes. Insulation round a pipe or wire adds conduction resistance but also enlarges the outer surface, so the heat loss is greatest at the critical radius $r_{cr}=k/h$; below it, adding insulation increases the heat loss. A fin adds surface area: an energy balance on a slice gives $\mathrm d^2\theta/\mathrm dx^2-a^2\theta=0$ with $a^2=hp/kA_c$, whose solutions give $\dot Q=\sqrt{hpkA_c}\,\theta_b$ for an infinitely long fin and $\sqrt{hpkA_c}\,\theta_b\tanh aL$ for an insulated tip. Fin efficiency compares a fin with an ideal one at the base temperature, and fin effectiveness compares it with no fin at all.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks whether insulating a pipe or wire reduces its heat loss, or for the heat rate, tip temperature, efficiency or effectiveness of a fin.
> - **Assumptions:** steady; one-dimensional (radial in the insulation, along $x$ in the fin); constant $k$ and $h$; for fins a constant cross-section and $T$ uniform over each cross-section; no radiation.
> - **Method:** 1. Insulation: compare $r_i$ with $r_{cr}=k/h$ (cylinder). 2. Fins: compute $p$, $A_c$, $a=\sqrt{hp/kA_c}$ and $aL$. 3. Choose the tip condition: long fin if $aL\gtrsim2.65$, otherwise insulated tip. 4. $\dot Q=\sqrt{hpkA_c}\,\theta_b$ or $\times\tanh aL$. 5. $\eta_{\mathrm{fin}}=\dot Q_{\mathrm{fin}}/hA_{\mathrm{fin}}\theta_b$ and $\epsilon_{\mathrm{fin}}=\dot Q_{\mathrm{fin}}/hA_b\theta_b$.
> - **Common mistakes:** concluding that more insulation always reduces heat loss (false for $r_o<k/h$); using the long-fin formulas $\sqrt{hpkA_c}\,\theta_b$ and $\eta=1/(aL)$ on a short fin, where they give $\eta>1$.
> - **Practise:** [[#Example 2 - aluminium and steel pin fins|the pin-fin example]] · [[#Example 1 - insulating a thin wire|the insulated-wire example]]

Heat leaving a hot surface into a fluid passes first by conduction through any solid layers and then by convection from the outermost surface. In the thermal resistance picture of [[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]] these are resistances in series, and the convection resistance $1/hA$ falls as the surface area grows. That one fact has two consequences.

The first is a trap. Wrapping insulation round a cylinder adds conduction resistance, which slows the heat, but it also pushes the outer surface outwards and so increases the area for convection, which speeds the heat. When the cylinder is thin enough, the second effect wins and the insulation increases the heat loss. The dividing radius, the critical radius of insulation, follows from a one-line optimisation.

The second is a design tool. If the surface temperature $T_s$ and the fluid temperature $T_\infty$ are fixed by the design, Newton's law of cooling $\dot Q=hA_s(T_s-T_\infty)$ leaves two ways to raise the heat transfer: raise $h$ (a fan, at extra cost) or raise $A_s$. Making the whole system bigger costs money and space, so instead the surface is extended with **fins**, as on a heat sink on a computer processor, a motorcycle cylinder or an air-cooled transformer. A fin works only as well as heat can be conducted along it, so its temperature falls from base to tip, and the analysis is a balance between conduction along the fin and convection from its sides.

## 1. Critical thickness of insulation

Consider a layer of insulation of conductivity $k$ round a circular pipe of length $L$. The inner surface of the insulation, at radius $r_i$, is at $T_i$; the outer surface, at radius $r_o$, is exposed to a convection environment at $T_\infty$ with heat transfer coefficient $h$. The heat flows radially outwards through two resistances in series, conduction through the insulation and convection from its outer surface ([[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]] derives the cylindrical conduction resistance):

$$
R_{\mathrm{total}}=\frac{\ln(r_o/r_i)}{2\pi kL}+\frac{1}{2\pi r_oLh},
\qquad
\dot Q=\frac{\Delta T}{R_{\mathrm{total}}}=\frac{T_i-T_\infty}{R_{\mathrm{total}}}.
$$

Multiply the numerator and denominator by $2\pi L$:

$$
\dot Q=\frac{2\pi L\,(T_i-T_\infty)}{\dfrac{\ln(r_o/r_i)}{k}+\dfrac{1}{r_oh}} .
$$

As $r_o$ increases, the first term in the denominator (conduction) grows, but only logarithmically, while the second (convection) falls as $1/r_o$, because the convective surface area grows linearly with radius. The heat rate therefore has a turning point.

**The critical radius.** Call the denominator $D(r_o)$:

$$
D(r_o)=\frac{\ln(r_o/r_i)}{k}+\frac{1}{r_oh},
\qquad
\dot Q=\frac{2\pi L\,(T_i-T_\infty)}{D(r_o)} .
$$

Differentiate $D$, using $\dfrac{\mathrm d}{\mathrm dr_o}\ln\dfrac{r_o}{r_i}=\dfrac1{r_o}$:

$$
\frac{\mathrm dD}{\mathrm dr_o}=\frac{1}{kr_o}-\frac{1}{hr_o^2}.
$$

Differentiate $\dot Q$ by the chain rule:

$$
\frac{\mathrm d\dot Q}{\mathrm dr_o}=-\frac{2\pi L\,(T_i-T_\infty)}{D^2}\frac{\mathrm dD}{\mathrm dr_o}
=\frac{-2\pi L\,(T_i-T_\infty)\left(\dfrac{1}{kr_o}-\dfrac{1}{hr_o^2}\right)}{\left[\dfrac{\ln(r_o/r_i)}{k}+\dfrac{1}{r_oh}\right]^2}.
$$

The extremum is where this is zero. The prefactor and the denominator are non-zero, so

$$
\frac{1}{kr_o}-\frac{1}{hr_o^2}=0 .
$$

Multiply through by $khr_o^2$:

$$
hr_o-k=0
$$

$$
\boxed{r_{cr}=\frac kh}\qquad(\text{cylinder; }k\text{ of the insulation, }h\text{ outside}).
$$

**Maximum, not minimum.** For $r_o<k/h$, $hr_o<k$, so $\dfrac{1}{kr_o}<\dfrac{1}{hr_o^2}$ and $\mathrm dD/\mathrm dr_o<0$: the total resistance falls and the heat rate rises as insulation is added. For $r_o>k/h$ the signs reverse. Formally, the second derivative of $D$ is

$$
\frac{\mathrm d^2D}{\mathrm dr_o^2}=-\frac{1}{kr_o^2}+\frac{2}{hr_o^3},
$$

and at $r_o=k/h$ this is $-\dfrac{h^2}{k^3}+\dfrac{2h^2}{k^3}=\dfrac{h^2}{k^3}>0$. $D$ (the total resistance) is a minimum, so for $T_i>T_\infty$ the heat rate is a **maximum** at $r_o=r_{cr}$: the critical radius maximises the heat transfer.

So a thicker layer of insulation does not always reduce the heat transfer rate. If the outer radius is greater than $r_{cr}$, adding insulation decreases the heat rate; if it is less, adding insulation increases it. This happens for sufficiently small $h$ (large $k/h$) or a thin pipe or wire. Two cases follow:

- $r_i\ge r_{cr}$: the heat rate falls with every layer added, so insulation always helps. Typical pipe insulation has $k\approx0.04$ W m⁻¹ K⁻¹ and $h\approx10$ W m⁻² K⁻¹, so $r_{cr}=4$ mm, smaller than almost any pipe.
- $r_i<r_{cr}$: the heat rate first rises to a maximum at $r_o=r_{cr}$ and only then falls, and it returns to the bare value only at a much larger radius. Thin electrical wires are in this regime, which is useful: the plastic sheath helps the wire shed heat.

![[at_w09c_critical_radius.png|900]]

### Example 1 - insulating a thin wire

*A wire of radius $r_i=1$ mm at 50 K above the surrounding air ($h=10$ W m⁻² K⁻¹) is covered with plastic of $k=0.15$ W m⁻¹ K⁻¹ (suggested, not lecturer-set).*

$r_{cr}=k/h=0.15/10=0.015$ m $=15$ mm, which is larger than $r_i$. The bare wire loses, per metre,

$$
\frac{\dot Q}{L}=2\pi r_ih\,\Delta T=2\pi(0.001)(10)(50)=3.14\ \text{W m}^{-1}.
$$

With insulation to $r_o=r_{cr}$,

$$
\frac{\dot Q}{L}=\frac{2\pi(50)}{\dfrac{\ln(15)}{0.15}+\dfrac{1}{0.015\times10}}=\frac{314.16}{18.05+6.67}=12.7\ \text{W m}^{-1},
$$

four times the bare value. Insulation out to $r_o=2$ mm gives 5.75 W m⁻¹ and out to $r_o=5$ mm gives 10.2 W m⁻¹. The heat loss falls back to the bare-wire 3.14 W m⁻¹ only at $r_o\approx3.3$ km, so for a wire like this any practical sheath increases the heat loss.

> [!check] The same argument for a sphere (suggested, not lecturer-set)
> For a spherical shell, $R_{\mathrm{total}}=\dfrac{1}{4\pi k}\left(\dfrac1{r_i}-\dfrac1{r_o}\right)+\dfrac{1}{4\pi r_o^2h}$. Then $\dfrac{\mathrm dR}{\mathrm dr_o}=\dfrac{1}{4\pi kr_o^2}-\dfrac{2}{4\pi hr_o^3}=0$, so $r_{cr}=2k/h$, twice the cylinder value, because the sphere's area grows as $r_o^2$.

## 2. Fins: the energy balance

Take a fin of length $L$ attached to a wall at its base, $x=0$, where the temperature is $T_b$. The fin has a constant cross-sectional area $A_c$ and perimeter $p$ (for a rectangular fin of width $w$ and thickness $t$, $A_c=wt$ and $p=2(w+t)$; for a pin fin of diameter $D$, $A_c=\pi D^2/4$ and $p=\pi D$). It is surrounded by fluid at $T_\infty$ with heat transfer coefficient $h$. Heat is transferred along the fin by conduction and from the fin to the surroundings by convection.

Assume that the fin is thin enough for the temperature to be uniform over each cross-section, so that $T$ depends on $x$ only, and take a volume element of thickness $\Delta x$ at position $x$.

![[at_w09c_fin_element.png|900]]

**Energy balance on the element** under steady-state conditions:

$$
\begin{pmatrix}\text{rate of heat}\\\text{conduction into}\\\text{the element at }x\end{pmatrix}
=
\begin{pmatrix}\text{rate of heat}\\\text{conduction from the}\\\text{element at }x+\Delta x\end{pmatrix}
+
\begin{pmatrix}\text{rate of heat}\\\text{convection from}\\\text{the element}\end{pmatrix}
$$

$$
\dot Q_{\mathrm{cond},x}=\dot Q_{\mathrm{cond},x+\Delta x}+\dot Q_{\mathrm{conv}} .
$$

The element's convecting surface is its perimeter times its thickness, $A_s=p\,\Delta x$, so by Newton's law of cooling

$$
\dot Q_{\mathrm{conv}}=hA_s(T-T_\infty)=h\,(p\,\Delta x)(T-T_\infty).
$$

Substitute and move everything to one side:

$$
\dot Q_{\mathrm{cond},x+\Delta x}-\dot Q_{\mathrm{cond},x}+hp\,\Delta x\,(T-T_\infty)=0 .
$$

Divide by $\Delta x$:

$$
\frac{\dot Q_{\mathrm{cond},x+\Delta x}-\dot Q_{\mathrm{cond},x}}{\Delta x}+hp\,(T-T_\infty)=0 .
$$

Take the limit $\Delta x\to0$; the first term becomes a derivative:

$$
\frac{\mathrm d\dot Q_{\mathrm{cond}}}{\mathrm dx}+hp\,(T-T_\infty)=0 .
$$

**Fourier's law** for conduction along the fin, through the cross-section $A_c$ at position $x$:

$$
\dot Q_{\mathrm{cond}}=-kA_c\frac{\mathrm dT}{\mathrm dx}.
$$

Substitute:

$$
\frac{\mathrm d}{\mathrm dx}\left(-kA_c\frac{\mathrm dT}{\mathrm dx}\right)+hp\,(T-T_\infty)=0 .
$$

Multiply by $-1$; the sign of the convection term changes because of the minus sign in Fourier's law:

$$
\frac{\mathrm d}{\mathrm dx}\left(kA_c\frac{\mathrm dT}{\mathrm dx}\right)-hp\,(T-T_\infty)=0 .
$$

**Constant cross-section and constant conductivity.** If $A_c$ and $p$ do not change with $x$ and $k$ is constant, $kA_c$ comes out of the derivative:

$$
kA_c\frac{\mathrm d^2T}{\mathrm dx^2}-hp\,(T-T_\infty)=0 .
$$

Divide by $kA_c$:

$$
\frac{\mathrm d^2T}{\mathrm dx^2}-\frac{hp}{kA_c}(T-T_\infty)=0 .
$$

Define the temperature excess and the fin parameter

$$
\theta=T-T_\infty,\qquad a^2=\frac{hp}{kA_c}.
$$

$T_\infty$ is a constant, so $\mathrm d^2\theta/\mathrm dx^2=\mathrm d^2T/\mathrm dx^2$, and

$$
\boxed{\frac{\mathrm d^2\theta}{\mathrm dx^2}-a^2\theta=0}
$$

$a$ has units of m⁻¹, and $1/a$ is the length over which the fin temperature excess decays by a factor $e$ on a long fin. $a^2$ is the ratio of the convective conductance per unit length, $hp$, to the conductive conductance along the fin, $kA_c$ (per unit length squared).

## 3. General solution

The equation is a linear, homogeneous, second-order ODE with constant coefficients. Try $\theta=e^{\lambda x}$:

$$
\lambda^2e^{\lambda x}-a^2e^{\lambda x}=0
\quad\Rightarrow\quad
\lambda^2=a^2
\quad\Rightarrow\quad
\lambda=\pm a .
$$

The general solution is the sum of the two exponentials:

$$
\theta(x)=C_1e^{ax}+C_2e^{-ax},
$$

with $C_1$ and $C_2$ constants set by two boundary conditions. One is always the base temperature:

$$
x=0:\qquad\theta=\theta_b=T_b-T_\infty .
$$

At the fin tip several conditions are possible. The two treated here are (a) the infinitely long fin, $T_{\mathrm{fin\text{-}tip}}=T_\infty$, and (b) the insulated fin tip, with negligible heat loss from the tip, $\dot Q_{\mathrm{fin\text{-}tip}}=0$.

## 4. Infinitely long fin

For a sufficiently long fin the temperature at the tip approaches the environment temperature:

$$
\text{BC 1:}\quad x=L\to\infty:\quad\theta=T(L)-T_\infty=0 .
$$

As $x\to\infty$, $e^{ax}\to\infty$, so any non-zero $C_1$ would make $\theta\to\infty$ at the tip, which contradicts BC 1. Hence $C_1=0$, and the solution is a multiple of $e^{-ax}$:

$$
\theta(x)=C_2e^{-ax}.
$$

$$
\text{BC 2:}\quad\theta(0)=T_b-T_\infty=C_2e^0
\quad\Rightarrow\quad C_2=\theta_b .
$$

$$
\theta(x)=\theta_be^{-ax}
\quad\Rightarrow\quad
\boxed{\frac{T(x)-T_\infty}{T_b-T_\infty}=e^{-ax}=e^{-x\sqrt{hp/kA_c}}}
$$

The temperature decreases exponentially along the fin.

**Heat rate.** All the heat lost by the fin enters it by conduction through the base, so by Fourier's law at $x=0$:

$$
\dot Q_{\mathrm{long\ fin}}=-kA_c\left.\frac{\mathrm dT}{\mathrm dx}\right|_{x=0}=-kA_c\left.\frac{\mathrm d\theta}{\mathrm dx}\right|_{x=0}.
$$

$\mathrm d\theta/\mathrm dx=-a\theta_be^{-ax}$, which is $-a\theta_b$ at $x=0$:

$$
\dot Q_{\mathrm{long\ fin}}=kA_c\,a\,\theta_b=kA_c\sqrt{\frac{hp}{kA_c}}\,\theta_b .
$$

$$
\boxed{\dot Q_{\mathrm{long\ fin}}=\sqrt{hpkA_c}\,(T_b-T_\infty)}
$$

> [!check] The same heat rate from the convection along the fin
> Integrate the convection from the whole surface: $\int_0^\infty hp\,\theta\,\mathrm dx=hp\,\theta_b\int_0^\infty e^{-ax}\,\mathrm dx=\dfrac{hp\,\theta_b}{a}=hp\sqrt{\dfrac{kA_c}{hp}}\,\theta_b=\sqrt{hpkA_c}\,\theta_b$ ✓. What enters at the base leaves through the sides.

## 5. Insulated fin tip

Very long fins are uncommon. A more realistic case is a fin whose tip loses negligible heat, since heat transfer from a fin is proportional to its surface area and the tip is a small fraction of the total fin surface. Zero heat flow at the tip means zero temperature gradient there:

$$
\text{BC 1:}\quad\dot Q_{\mathrm{fin\text{-}tip}}=0
\quad\Rightarrow\quad
\left.\frac{\mathrm d\theta}{\mathrm dx}\right|_{x=L}=0 ,
$$

$$
\text{BC 2:}\quad x=0:\quad\theta=\theta_b=T_b-T_\infty .
$$

Apply BC 2 to $\theta(x)=C_1e^{ax}+C_2e^{-ax}$:

$$
\theta_b=C_1+C_2 .
$$

Differentiate, $\mathrm d\theta/\mathrm dx=a\left(C_1e^{ax}-C_2e^{-ax}\right)$, and apply BC 1:

$$
0=a\left(C_1e^{aL}-C_2e^{-aL}\right)
\quad\Rightarrow\quad
C_2=C_1e^{2aL}.
$$

Substitute into the BC 2 equation:

$$
\theta_b=C_1\left(1+e^{2aL}\right)
\quad\Rightarrow\quad
C_1=\frac{\theta_b}{1+e^{2aL}},
$$

$$
C_2=\frac{\theta_be^{2aL}}{1+e^{2aL}}=\frac{\theta_b}{e^{-2aL}+1}.
$$

So

$$
\frac{\theta}{\theta_b}=\frac{e^{-ax}}{1+e^{-2aL}}+\frac{e^{ax}}{1+e^{2aL}} .
$$

**Hyperbolic form.** With $\sinh x=\tfrac12(e^x-e^{-x})$, $\cosh x=\tfrac12(e^x+e^{-x})$ and $\tanh x=\sinh x/\cosh x$, multiply the first fraction by $e^{aL}/e^{aL}$ and the second by $e^{-aL}/e^{-aL}$:

$$
\frac{\theta}{\theta_b}=\frac{e^{a(L-x)}}{e^{aL}+e^{-aL}}+\frac{e^{-a(L-x)}}{e^{-aL}+e^{aL}} .
$$

The denominators are now the same:

$$
\frac{\theta}{\theta_b}=\frac{e^{a(L-x)}+e^{-a(L-x)}}{e^{aL}+e^{-aL}}=\frac{2\cosh a(L-x)}{2\cosh aL}.
$$

$$
\boxed{\frac{\theta}{\theta_b}=\frac{T(x)-T_\infty}{T_b-T_\infty}=\frac{\cosh a(L-x)}{\cosh aL}}
$$

At the tip, $x=L$, $\cosh0=1$ and the tip excess is $\theta_L=\theta_b/\cosh aL$.

**Heat rate.** Differentiate, with $\dfrac{\mathrm d}{\mathrm dx}\cosh a(L-x)=-a\sinh a(L-x)$:

$$
\frac{\mathrm d\theta}{\mathrm dx}=-a\theta_b\frac{\sinh a(L-x)}{\cosh aL}
\quad\Rightarrow\quad
\left.\frac{\mathrm d\theta}{\mathrm dx}\right|_{x=0}=-a\theta_b\frac{\sinh aL}{\cosh aL}=-a\theta_b\tanh aL .
$$

By Fourier's law at the base,

$$
\dot Q_{\mathrm{insulated\text{-}tip}}=-kA_c\left.\frac{\mathrm dT}{\mathrm dx}\right|_{x=0}=kA_c\,a\,\theta_b\tanh aL
$$

$$
\boxed{\dot Q_{\mathrm{insulated\text{-}tip}}=\sqrt{hpkA_c}\,(T_b-T_\infty)\tanh aL}
$$

The integral of the convection along the sides, $\int_0^Lhp\,\theta\,\mathrm dx$, gives the same result, as it must: the heat entering at the base leaves through the sides.

![[at_w09c_fin_temperature.png|900]]

**When a fin counts as long.** The two results differ only by the factor $\tanh aL$, which rises from 0 towards 1 as $aL$ grows. $\tanh aL=0.99$ at $aL=2.65$, so a fin with $aL\gtrsim2.65$ already transfers 99 % of what an infinitely long fin of the same section would, and its tip excess has fallen to 14 % of $\theta_b$ ($1/\cosh2.65=0.14$). Beyond that, extra length adds weight and material for almost no extra heat transfer. For short fins (small $aL$) the long-fin formula overestimates the heat rate badly, and the dashed and solid curves in the figure above differ most.

## 6. Fin efficiency

In the limiting case of zero thermal resistance along the fin, or infinite thermal conductivity $k\to\infty$, every point on the fin would be at the base temperature $T_b$, and the fin would transfer the most heat it possibly could:

$$
\dot Q_{\mathrm{fin,max}}=hA_{\mathrm{fin}}(T_b-T_\infty),
$$

where $A_{\mathrm{fin}}$ is the fin's convecting surface. A real fin's temperature falls along its length (for example from 100 °C at the base to 75 °C at the tip), so each part of it convects less than it would at $T_b$. The **fin efficiency** is the ratio

$$
\eta_{\mathrm{fin}}=\frac{\text{actual heat transfer rate}}{\text{ideal heat transfer rate}}=\frac{\dot Q_{\mathrm{fin}}}{\dot Q_{\mathrm{fin,max}}}.
$$

For a fin with an insulated or infinitely distant tip, the convecting area is the side area, $A_{\mathrm{fin}}=p\times L$.

**Long fin:**

$$
\eta_{\mathrm{long\text{-}fin}}=\frac{\sqrt{hpkA_c}\,(T_b-T_\infty)}{hpL\,(T_b-T_\infty)}=\frac1L\sqrt{\frac{kA_c}{hp}}=\frac{1}{aL}.
$$

**Insulated fin tip:**

$$
\eta_{\mathrm{insulated\text{-}tip}}=\frac{\sqrt{hpkA_c}\,(T_b-T_\infty)\tanh aL}{hpL\,(T_b-T_\infty)}=\frac{\tanh aL}{aL}.
$$

The insulated-tip efficiency tends to 1 as $aL\to0$ (a very short or very conductive fin is nearly isothermal) and falls as $aL$ grows. The long-fin efficiency $1/(aL)$ exceeds 1 for $aL<1$, which is impossible, so it applies only when the fin really is long ($aL\gtrsim2.65$), where it agrees with $\tanh(aL)/aL$.

![[at_w09c_fin_performance.png|900]]

## 7. Fin effectiveness

Fins are there to enhance heat transfer, so the more useful question is how much heat the fin transfers compared with the bare base area it covers. Without the fin, the base area $A_b$ would convect

$$
\dot Q_{\mathrm{no\ fin}}=hA_b(T_b-T_\infty).
$$

The **fin effectiveness** is

$$
\epsilon_{\mathrm{fin}}=\frac{\dot Q_{\mathrm{fin}}}{\dot Q_{\mathrm{no\ fin}}}.
$$

- $\epsilon=1$: the fin does not affect the heat transfer;
- $\epsilon<1$: the fin slows down the heat transfer, acting as insulation;
- $\epsilon>1$: the fin enhances the heat transfer, as intended.

For a fin of constant section the base area it covers is its cross-section, $A_b=A_c$.

**Long fin:**

$$
\epsilon_{\mathrm{long\text{-}fin}}=\frac{\sqrt{hpkA_c}\,(T_b-T_\infty)}{hA_c\,(T_b-T_\infty)}=\sqrt{\frac{hpkA_c}{h^2A_c^2}}=\sqrt{\frac{kp}{hA_c}}.
$$

**Insulated fin tip:**

$$
\epsilon_{\mathrm{insulated\text{-}fin}}=\frac{\sqrt{hpkA_c}\,(T_b-T_\infty)\tanh aL}{hA_c\,(T_b-T_\infty)}=\sqrt{\frac{kp}{hA_c}}\tanh aL .
$$

**Relationship between efficiency and effectiveness.** From the definition of efficiency,

$$
\dot Q_{\mathrm{fin}}=\eta_{\mathrm{fin}}\times\dot Q_{\mathrm{fin,max}}=\eta_{\mathrm{fin}}hA_{\mathrm{fin}}(T_b-T_\infty).
$$

Divide by $\dot Q_{\mathrm{no\ fin}}$:

$$
\epsilon_{\mathrm{fin}}=\frac{\eta_{\mathrm{fin}}hA_{\mathrm{fin}}(T_b-T_\infty)}{hA_b(T_b-T_\infty)}
\quad\Rightarrow\quad
\boxed{\epsilon_{\mathrm{fin}}=\frac{A_{\mathrm{fin}}}{A_b}\eta_{\mathrm{fin}}}
$$

A fin can have a low efficiency and still be very effective, because it may have tens of times the base area.

**Design considerations from the effectiveness relation.** $\epsilon_{\mathrm{long\text{-}fin}}=\sqrt{kp/hA_c}$ shows what makes a fin worthwhile:

- the thermal conductivity should be as high as possible, which is why fins are metal (aluminium and copper above all);
- the ratio of perimeter to cross-sectional area $p/A_c$ should be as high as possible, so thin, slender fins are more effective (for a pin fin $p/A_c=4/D$);
- fins are most effective when $h$ is low, that is, with free convection or a gas rather than a liquid. Where $h$ is already high, as on the water side of a heat exchanger, fins add little and are usually left off.

## 8. Worked example

### Example 2 - aluminium and steel pin fins

*A pin fin of diameter $D=5$ mm and length $L=50$ mm sticks out from a surface at $T_b=100^\circ$C into air at $T_\infty=25^\circ$C with $h=20$ W m⁻² K⁻¹. Find the heat rate, efficiency, effectiveness and tip temperature for (a) aluminium, $k=200$ W m⁻¹ K⁻¹, and (b) stainless steel, $k=15$ W m⁻¹ K⁻¹, treating the tip as insulated (suggested, not lecturer-set).*

The geometry:

$$
p=\pi D=0.015708\ \text{m},\qquad A_c=\frac{\pi D^2}{4}=1.9635\times10^{-5}\ \text{m}^2,\qquad \theta_b=100-25=75\ \text{K}.
$$

**(a) Aluminium.**

$$
a=\sqrt{\frac{hp}{kA_c}}=\sqrt{\frac{20\times0.015708}{200\times1.9635\times10^{-5}}}=8.944\ \text{m}^{-1},\qquad aL=0.447 .
$$

$aL$ is far below 2.65, so this is not a long fin and the insulated-tip result is needed.

$$
\sqrt{hpkA_c}=\sqrt{20\times0.015708\times200\times1.9635\times10^{-5}}=0.03512\ \text{W K}^{-1},
$$

$$
\dot Q_{\mathrm{fin}}=0.03512\times75\times\tanh0.447=\boxed{1.105\ \text{W}}.
$$

The efficiency, with $A_{\mathrm{fin}}=pL=7.854\times10^{-4}$ m² and $\dot Q_{\mathrm{fin,max}}=20\times7.854\times10^{-4}\times75=1.178$ W:

$$
\eta_{\mathrm{fin}}=\frac{\tanh aL}{aL}=\frac{\tanh0.447}{0.447}=0.938=\frac{1.105}{1.178}\ ✓
$$

Without the fin, the base area would convect $\dot Q_{\mathrm{no\ fin}}=20\times1.9635\times10^{-5}\times75=0.02945$ W, so

$$
\epsilon_{\mathrm{fin}}=\frac{1.105}{0.02945}=37.5=\frac{A_{\mathrm{fin}}}{A_b}\eta_{\mathrm{fin}}=\frac{4L}{D}\eta_{\mathrm{fin}}=40\times0.938\ ✓
$$

The tip temperature is $T_\infty+\theta_b/\cosh aL=25+75/1.1017=93.1^\circ$C, so the aluminium fin is nearly isothermal.

**(b) Stainless steel.** With $k=15$: $a=32.66$ m⁻¹, $aL=1.633$, $\sqrt{hpkA_c}=0.009619$ W K⁻¹, so

$$
\dot Q_{\mathrm{fin}}=0.009619\times75\times\tanh1.633=0.668\ \text{W},\qquad \eta_{\mathrm{fin}}=\frac{\tanh1.633}{1.633}=0.567,\qquad \epsilon_{\mathrm{fin}}=22.7 .
$$

A conductivity 13 times lower costs 40 % of the heat rate.

> [!warning] The long-fin formula on a short fin
> For the aluminium fin, $\sqrt{hpkA_c}\,\theta_b=2.63$ W and $1/(aL)=2.24$. That is more than twice the 1.18 W an isothermal fin of the same area could transfer, so it is physically impossible. Always check $aL$ before choosing the tip condition.

## Problem-solving workflow

1. For insulation on a cylinder, compute $r_{cr}=k/h$ (sphere $2k/h$) and compare it with the bare radius and the proposed outer radius; then compute $\dot Q$ from the series resistances if a number is asked for.
2. For a fin, write $p$ and $A_c$ for the cross-section, and $\theta_b=T_b-T_\infty$.
3. Compute $a=\sqrt{hp/kA_c}$ and $aL$; choose the long fin if $aL\gtrsim2.65$ or the question says so, otherwise the insulated tip.
4. $\dot Q=\sqrt{hpkA_c}\,\theta_b$ (long) or $\sqrt{hpkA_c}\,\theta_b\tanh aL$ (insulated tip); $\theta(x)$ from $e^{-ax}$ or $\cosh a(L-x)/\cosh aL$.
5. $\eta_{\mathrm{fin}}=\dot Q/(hpL\theta_b)$, $\epsilon_{\mathrm{fin}}=\dot Q/(hA_c\theta_b)$, and check $\epsilon=(A_{\mathrm{fin}}/A_b)\eta$.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| critical radius of insulation $r_o=k/h$ | critical thickness of insulation; $r_{cr}$ | L5.4 slides 4–5 | The slides write the critical radius with the outer-radius symbol $r_o$ |
| fins | extended surfaces | L5.4 slides 6–25 | |
| $a^2=hp/kA_c$ | $m^2$ (Çengel, Incropera); fin parameter | L5.4 slides 12–24 | |
| $\theta=T-T_\infty$ | excess temperature; temperature excess | L5.4 slide 12 | Not named on the slides |
| insulated fin tip | adiabatic tip | L5.4 slides 14, 17–18 | |
| infinitely long fin (long fin) | semi-infinite fin | L5.4 slides 15–16, 21, 24 | |
| fin efficiency $\eta_{\mathrm{fin}}$; fin effectiveness $\epsilon_{\mathrm{fin}}$ | (no common alternatives; easily swapped by mistake) | L5.4 slides 19–25 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]] (Newton's law of cooling and $h$) · Next: [[SESA3029 W09d - Thermal Radiation]]
- Conduction and resistances: [[SESA3029 W09a - Heat Conduction and Thermal Resistance]] (Fourier's law, cylindrical resistance)
- New concepts: [[Critical Radius of Insulation]] · [[Fin Equation]] · [[Fin Efficiency and Effectiveness]] · [[Newton's Law of Cooling]]
- Later in the block: [[SESA3029 W09e - Numerical Methods in Conduction]] (conduction problems without closed-form solutions)
- Worked sheet: [[SESA3029 Example Sheet 3 - Solutions]] (no fin or critical-radius question; Q1 and Q3 use the series resistances of §1)
- Formulae: [[SESA3029 Formula Sheet]]

## Sources

- `Lecture5.4(1).pdf`: Lecture 5.4, critical thickness of insulation and fins, 25 slides. No lecturer is named on the deck. Slides 2–5 the critical radius; slide 6 Newton's law of cooling and the case for extended surfaces; slides 7–13 the fin geometry, energy balance, fin equation and general solution; slides 14–16 the tip conditions and the infinitely long fin; slides 17–18 the insulated tip; slides 19–21 fin efficiency; slides 22–25 fin effectiveness, its relation to efficiency and the design considerations. The deck has no worked example.
- This note is written ahead from the slides. No transcript exists yet; it will be reconciled with the transcript once the lecture has been given.
- Additions not on the slides, each derived here: the second-derivative check that $r_{cr}$ is a maximum, the sphere result $2k/h$, the two worked examples, the conversion from exponentials to $\cosh$ written out, the energy check on the heat rates, and the $aL\approx2.65$ long-fin criterion.
- Figures: `generate_aerothermo_w09bc_figures.py` (`at_w09c_critical_radius.png`, `at_w09c_fin_element.png`, `at_w09c_fin_temperature.png`, `at_w09c_fin_performance.png`).
- Textbooks cited in the course: Çengel, *Heat Transfer: A Practical Approach*, 2nd ed. (fins and the critical radius); Holman, *Heat Transfer*, 10th ed.

## Self-study tasks

There is no transcript yet and the deck sets no exercises, so the slide references below are where each derivation appears.

### Core

- [ ] **(L5.4 slides 2–5)** Derive $r_{cr}=k/h$ for insulation on a cylinder and show that it maximises the heat loss. → [[#1. Critical thickness of insulation|§1]]
- [ ] **(L5.4 slides 9–12)** Derive the fin equation $\theta''-a^2\theta=0$ from an energy balance on a slice. → [[#2. Fins: the energy balance|§2]]
- [ ] **(L5.4 slides 17–18)** Solve for the insulated tip: $C_1$, $C_2$, the $\cosh$ form and $\dot Q=\sqrt{hpkA_c}\,\theta_b\tanh aL$. → [[#5. Insulated fin tip|§5]]
- [ ] **(L5.4 slides 21–24)** Derive $\eta$ and $\epsilon$ for the long and insulated-tip fins and show $\epsilon=(A_{\mathrm{fin}}/A_b)\eta$. → [[#6. Fin efficiency|§§6–7]]
- [ ] (suggested, not lecturer-set) Aluminium and steel pin fins: $\dot Q$, $\eta$, $\epsilon$ and tip temperature. Answers 1.105 W, 0.938, 37.5, 93.1 °C; 0.668 W, 0.567, 22.7. → [[#Example 2 - aluminium and steel pin fins|§8]]

### Further practice

- [ ] **(L5.4 slides 15–16)** Infinitely long fin: show $C_1=0$, $\theta=\theta_be^{-ax}$ and $\dot Q=\sqrt{hpkA_c}\,\theta_b$, and check the heat rate by integrating the convection. → [[#4. Infinitely long fin|§4]]
- [ ] (suggested, not lecturer-set) Insulated wire: $r_{cr}$, the bare and maximum heat loss per metre. Answers 15 mm, 3.14 and 12.7 W m⁻¹. → [[#Example 1 - insulating a thin wire|§1, Example 1]]
- [ ] (suggested, not lecturer-set) Show that $r_{cr}=2k/h$ for a sphere. → [[#1. Critical thickness of insulation|§1, the check]]

## Transcript and slide slips

> [!warning] "Particular integral" on L5.4 slide 13
> Where: [[#3. General solution]].
>
> Slide 13 describes the solution as "complementary function + particular integral". The fin equation $\theta''-a^2\theta=0$ is homogeneous, so the particular integral is zero and $\theta=C_1e^{ax}+C_2e^{-ax}$ is the complementary function alone. (Written in $T$, the particular integral is the constant $T_\infty$, which the substitution $\theta=T-T_\infty$ removes.)
