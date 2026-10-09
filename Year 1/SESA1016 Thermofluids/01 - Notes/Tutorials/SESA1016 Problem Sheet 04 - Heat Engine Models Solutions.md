---
title: "SESA1016 Problem Sheet 04 - Heat Engine Models Solutions"
module: "SESA1016 Thermofluids"
type: tutorial
stream: "Part A: Closed-system Thermodynamics"
tags: [sesa1016, tutorial-solutions, ideal-cycles]
sheet: "Problem Sheet 04 - Heat Engine Models"
theory_notes: ["[[SESA1016 T5 - Ideal Heat Engine Models]]"]
key_concepts: ["[[Thermal Efficiency and COP]]", "[[Isentropic Ideal-gas Relations]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 04 - Heat Engine Models.pdf"]
---

# SESA1016 Problem Sheet 04 - Heat Engine Models Solutions

> [!abstract] Sheet Info
> Six questions on dual, Carnot, inverse-Diesel, three-process and Brayton cycles. All printed numerical answers are reproduced.

## Q4.1 Dual cycle

Processes: 1->2 isentropic compression, 2->3 constant-volume heating, 3->4 constant-pressure heating, 4->5 isentropic expansion to $p_5=p_1$, 5->1 constant-pressure rejection.

### (a-b) State temperatures

With $r=v_1/v_2$, $r_p=p_3/p_2$ and $r_c=v_4/v_3$:

$$
T_2=T_1r^{\gamma-1},\qquad p_2=p_1r^\gamma
$$

$$
T_3=r_pT_2=T_1r^{\gamma-1}r_p
$$

$$
T_4=r_cT_3=T_1r^{\gamma-1}r_pr_c
$$

Since $p_4/p_1=r^\gamma r_p$ and 4->5 is isentropic:

$$
T_5=T_4\left(\frac{p_1}{p_4}\right)^{(\gamma-1)/\gamma}
=T_1r_c r_p^{1/\gamma}.
$$

### (c) Efficiency

$$
q_{in}=c_v(T_3-T_2)+c_p(T_4-T_3)
$$

$$
=c_vT_1r^{\gamma-1}\left[(r_p-1)+\gamma r_p(r_c-1)\right].
$$

$$
q_{out}=c_p(T_5-T_1)=\gamma c_vT_1\left(r_cr_p^{1/\gamma}-1\right).
$$

Therefore

$$
\boxed{\eta=1-
\frac{\gamma(r_cr_p^{1/\gamma}-1)}
{r^{\gamma-1}[(r_p-1)+\gamma r_p(r_c-1)]}}.
$$

### (d-e) Numerical design

$r=4$, $r_p=2$, $r_c=2$, $T_1=300$ K, $p_1=1$ bar, $\gamma=1.4$:

$$
T_2=522.3\ \mathrm K,\quad T_3=1044.7\ \mathrm K,
\quad \boxed{T_{max}=T_4=2089\ \mathrm K}
$$

$$
p_2=p_1r^\gamma=6.96\ \mathrm{bar},\qquad
\boxed{p_{max}=p_3=p_4=13.9\ \mathrm{bar}}.
$$

Substitution in the efficiency expression gives

$$
\boxed{\eta=51.7\%}\;\checkmark
$$

### (f) Why the constant-volume leg can help

On the $T$-$s$ diagram, constant-volume heat addition raises pressure before the constant-pressure leg. For fixed maximum $T$ and $p$, this can raise the average temperature at which heat is supplied and reduce entropy rise per unit heat, increasing the fraction convertible to work. The gain is idealised; real early combustion creates pressure-rise, loss and material constraints.

## Q4.2 Reversible non-Carnot cycle

On a reversible $T$-$s$ diagram, heat is area $\int Tds$. Let the common entropy width be $\Delta s$.

$$
q_{out}=300\Delta s,qquad
q_{in}=\frac{600+1200}{2}\Delta s=900\Delta s.
$$

$$
\boxed{\eta=1-300/900=66.7\%}.
$$

A Carnot engine between 300 and 1200 K gives

$$
\boxed{\eta_C=1-300/1200=75.0\%}.
$$

Reversibility alone does not guarantee Carnot efficiency: the non-Carnot cycle adds some heat below $T_{max}$.

## Q4.3 Carnot engine

$T_H=500^\circ$C $=773.15$ K; $T_C=20^\circ$C $=293.15$ K.

Lowering $T_C$ by a given amount changes efficiency more than raising $T_H$ by that amount because

$$
\left|\frac{\partial\eta}{\partial T_C}\right|=\frac1{T_H}
>\frac{T_C}{T_H^2}=\frac{\partial\eta}{\partial T_H}.
$$

The environmental sink temperature is normally not under the designer's control.

### (a-c) Heat and work

$$
\boxed{\eta_C=1-293.15/773.15=62.1\%}.
$$

With $W=1000$ kJ:

$$
\boxed{Q_H=W/\eta=1611\ \mathrm{kJ}},\qquad
\boxed{Q_C=Q_H-W=611\ \mathrm{kJ}}.
$$

### (d) Engine entropy change during rejection

The working fluid loses $Q_C$ reversibly at $T_C$:

$$
\boxed{\Delta S_{engine,rej}=-\frac{611}{293.15}=-2.08\ \mathrm{kJ/K}}\;\checkmark
$$

Its total entropy change over the complete cycle is zero.

## Q4.4 Inverse Diesel cycle

$r=5$, $T_1=300$ K, $p_1=1$ bar. Isentropic compression gives

$$
T_2=300(5)^{0.4}=571.1\ \mathrm K,qquad
p_2=1(5)^{1.4}=9.52\ \mathrm{bar}.
$$

Constant-volume heat addition to $T_3=1000$ K gives

$$
\boxed{p_3=p_2T_3/T_2=16.7\ \mathrm{bar}}.
$$

Because 4->1 is isobaric, $p_4=p_1$. Isentropic expansion gives

$$
T_4=T_3(p_4/p_3)^{(\gamma-1)/\gamma}=447.9\ \mathrm K.
$$

$$
q_{in}=c_v(T_3-T_2),\qquad q_{out}=c_p(T_4-T_1)
$$

$$
\boxed{\eta=1-q_{out}/q_{in}=51.8\%}.
$$

Carnot between 300 and 1000 K:

$$
\boxed{\eta_C=70.0\%}.
$$

Ideal Brayton between the same pressure limits:

$$
\boxed{\eta_B=1-(1/16.7)^{0.4/1.4}=55.2\%}\;\checkmark
$$

## Q4.5 Three-process engine

$m=0.004$ kg, state 1: 100 kPa, 300 K; state 2: 1 MPa after isentropic compression.

$$
T_2=T_1(10)^{0.4/1.4}=579.2\ \mathrm K.
$$

Constant-pressure heat addition $Q_{23}=2.76$ kJ gives

$$
T_3=T_2+\frac{Q_{23}}{mc_p}
=579.2+\frac{2.76}{0.004(1.005)}=1265.8\ \mathrm K.
$$

Specific volumes:

$$
v_1=RT_1/p_1=0.861,qquad
v_3=RT_3/p_3=0.3633\ \mathrm{m^3/kg}.
$$

Process 3->1 is a straight line $p=c_1v+c_2$, so its work is trapezoidal:

$$
W_{31}=m\frac{p_3+p_1}{2}(v_1-v_3)=1.095\ \mathrm{kJ}.
$$

$$
\Delta U_{31}=mc_v(T_1-T_3)=-2.774\ \mathrm{kJ}
$$

$$
Q_{31}=\Delta U_{31}+W_{31}=-1.679\ \mathrm{kJ}.
$$

Thus heat rejected is $\boxed{1.679\ \mathrm{kJ}}$ and

$$
\boxed{\eta=1-1.679/2.76=39.2\%}\;\checkmark
$$

## Q4.6 Ideal Brayton turbine-inlet temperature

$T_1=300$ K, $r_p=12$, $w_{net}=100$ kJ/kg, $c_p=1.005$ kJ/(kg K).

Let $a=(\gamma-1)/\gamma=0.285714$. Then

$$
T_2=T_1r_p^a,qquad T_4=T_3r_p^{-a}.
$$

$$
w_{net}=c_p[(T_3-T_2)-(T_4-T_1)].
$$

Solving:

$$
T_3=\frac{w_{net}/c_p+T_1(r_p^a-1)}{1-r_p^{-a}}
=\boxed{806\ \mathrm K}\;\checkmark
$$

## Related

- [[SESA1016 T5 - Ideal Heat Engine Models]] · [[SESA1016 Formula Sheet#4. Ideal cycles]]

