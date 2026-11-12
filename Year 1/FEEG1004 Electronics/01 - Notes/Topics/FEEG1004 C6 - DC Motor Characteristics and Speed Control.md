---
title: "FEEG1004 C6 - DC Motor Characteristics and Speed Control"
module: "FEEG1004 Electronics"
type: topic
stream: "Part C: Electric Machines"
order: 6
tags: [feeg1004, machines, dc-motor, torque-speed, shunt, series, chopper, pwm, h-bridge, brushless]
aliases: ["Electric Machines 07-08", "Torque-speed characteristic", "DC motor speed control", "Chopper", "H-bridge"]
date: 2026-09-27
status: lectured
coverage: "FEEG1004 Lecture 2025-02-20 (ll. 1–515)"
parent: ["[[FEEG1004 Electronics Hub]]"]
prerequisites: ["[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]", "[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
next_topics: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]"]
key_concepts: ["[[Torque-Speed Characteristics of DC Motors]]", "[[DC Motor Speed Control]]", "[[Flyback Diode]]", "[[Electric and Magnetic Loading]]"]
tutorial_sheets: ["[[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf", "02 - Sources/Lectures/FEEG1004 Lecture 2025-02-20.txt", "02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf"]
---

# FEEG1004 C6 - DC Motor Characteristics and Speed Control

> [!abstract] Summary
> Eliminating the armature current between $V = K_E\omega + iR_a$ and $T = K_T i$, with $K_E = K_T = K$ in SI units, gives the linear torque–speed line $\omega = V/K - (R_a/K^2)T$ of a constant-flux DC motor, with no-load speed $\omega_0 = V/K$ and stall torque $T_{\text{stall}} = KV/R_a$. Shunt and separately excited motors follow this near-constant-speed line, while a series motor, whose flux grows with its current, has $T \propto i^2$ and $\omega \propto 1/\sqrt{T}$: a large starting torque but runaway at no load. Speed is set through the armature voltage (efficiently, with a PWM chopper and freewheeling diode), a series resistance (wasteful except when starting) or the field flux (field weakening, above base speed), and direction through an H-bridge. Because torque scales with rotor volume, $T = 2BAV_R$, slow high-torque loads are driven by small fast motors through a step-down gearbox.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for the steady speed, torque, current or terminal voltage of a DC motor driving a known load, directly, through a gearbox or from a chopper.
> - **Assumptions:** steady state, so $L_a\,\mathrm{d}i/\mathrm{d}t = 0$; constant flux with $K_E = K_T = K$ in SI units (for a series motor $K = k_s i$ instead); ideal gears, and ideal switches unless their voltage drops are given.
> - **Method:** 1. Refer the load to the motor shaft with $\omega_m = G\omega_d$ and $T_m = T_d/G$. 2. Find the current from $i = T/K$. 3. Write $V = K\omega + iR_{\text{tot}}$, with $V = V_{\text{avg}} = \delta(V_S - V_{\text{sw}})$ for a chopper. 4. Solve for the unknown; a fan load $T_L = k\omega^2$ gives a quadratic in $\omega$, so take the positive root. 5. Check the power balance $Vi = K\omega i + i^2R_{\text{tot}}$.
> - **Common mistakes:** using the passenger mass instead of the net mass left after the counterweight; treating a series motor as a straight-line machine, when its $K$ grows with current so that $T \propto i^2$.
> - **Practise:** [[#Counterweighted passenger lift]] · [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q6: Torque–speed characteristics, shunt vs series|Tutorial 6 Q6]]

A DC motor does not run at a speed chosen in isolation. It accelerates or decelerates until the electromagnetic torque $T$ developed by its rotor equals the opposing torque $T_L$ that the load demands at that angular velocity $\omega$.

Plotting the motor's steady-state $T(\omega)$ curve alongside the load's $T_L(\omega)$ curve gives the equilibrium operating point where the two intersect. The same plot shows whether the motor can start the load from rest ($\omega = 0$) and whether the operating speed stays stable when the load fluctuates.

The motor curve can be reshaped in two ways: by choosing how the field winding is wired relative to the armature, or by controlling the terminal voltage, the circuit resistance or the field current. Between them these set the starting torque, the running speed and the direction of rotation.

## 1. Field connections and series runaway

Small fractional-kilowatt DC motors use permanent magnets on the stator to set a fixed pole flux $\Phi$. In larger industrial and traction machines permanent magnets become expensive, brittle and impossible to adjust in operation, so the stator poles carry **field windings** of $N_f$ turns excited by a DC field current $i_f$. The torque and back-EMF constant $K = \dfrac{Z N_p \Phi}{2\pi a}$ is proportional to the pole flux $\Phi$, so the shape of the torque–speed characteristic depends on how the field winding is connected to the armature.

| Excitation topology | Field winding connection | Pole flux $\Phi$ behaviour | Torque–speed characteristic | Typical engineering application |
|---|---|---|---|---|
| Permanent-magnet (PM) | None (fixed stator magnets) | Constant $\Phi$ | Straight drooping line with finite no-load speed $\omega_0 = V/K$ | Small servo actuators, automotive blowers, instrumentation |
| Separately excited | Fed from an independent DC supply $V_f$ | Constant for fixed $i_f = V_f/R_f$; independently adjustable | Straight drooping line; $\omega_0$ and slope adjustable via $i_f$ | Precision variable-speed industrial drives, rolling mills |
| Shunt-wound | Connected in parallel (shunt) with the armature across $V$ | Constant when terminal voltage $V$ is constant ($i_f = V/R_f$) | Identical to separately excited at fixed $V$, with a slight speed droop from $\omega_0$ to full load | Lathes, machine tools, constant-speed fans and centrifugal pumps |
| Series-wound | Connected in series with the armature ($i_f = i_a = i$) | Proportional to armature current ($\Phi \propto i$) before core saturation | Nonlinear inverse-root curve $\omega \propto 1/\sqrt{T}$: very large starting torque ($T \propto i^2$), runaway at no load | Electric rail traction, cranes, hoists, IC engine starter motors |
| Compound-wound | Both a shunt coil and a series coil on each stator pole | $\Phi = \Phi_{\text{shunt}} + \Phi_{\text{series}}(i)$ | Intermediate curve: high starting torque from the series turns, but bounded no-load speed from the shunt turns | Heavy presses, shears, lifts, reciprocating compressors |

In a **series-wound DC motor** the heavy-gauge field winding, of resistance $R_f$, is wired in series with the armature, of resistance $R_a$, so the same current $i$ flows through both. Provided the stator core stays below magnetic saturation, the pole flux is proportional to the current, and the machine factor $K(\Phi)$ scales linearly with $i$:

$$
K(i) = k_s i
$$

Here $k_s$ is a proportionality constant with SI units $\text{N}\,\text{m}\,\text{A}^{-2} = \text{V}\,\text{s}\,\text{A}^{-1}\,\text{rad}^{-1}$. Substituting $K(i) = k_s i$ into the torque expression $T = K(i)\,i$ gives a torque proportional to the square of the current:

$$
T = (k_s i)\,i = k_s i^2
$$

Inverting for the current,

$$
i = \sqrt{\frac{T}{k_s}}.
$$

At low speed or stall, doubling the current quadruples the torque, which gives the series motor the highest starting torque per ampere of any DC machine topology. Substituting $K(i) = k_s i$ into the back-EMF relation $E' = K(i)\,\omega$ gives

$$
E' = k_s i \omega.
$$

KVL around the series loop of supply voltage $V$, armature resistance $R_a$ and field resistance $R_f$ gives

$$
V = E' + i(R_a + R_f) = k_s i \omega + i(R_a + R_f).
$$

Dividing both sides by $k_s i$ and solving for $\omega$,

$$
\omega = \frac{V}{k_s i} - \frac{R_a + R_f}{k_s}.
$$

Substituting $i = \sqrt{T/k_s}$ expresses the speed as a function of torque:

$$
\omega = \frac{V}{\sqrt{k_s T}} - \frac{R_a + R_f}{k_s}
$$

When the winding resistances are small compared with the back EMF, $\omega \propto 1/\sqrt{T}$, or equivalently $T \propto 1/\omega^2$.

![[ee_c6_torque_speed_types.png|900]]

> [!warning] An energised series motor must never lose its mechanical load
> As the load torque $T$ approaches zero in $\omega = \dfrac{V}{\sqrt{k_s T}} - \dfrac{R_a + R_f}{k_s}$, the armature current falls and weakens the series field flux $\Phi \propto i$. To generate a back EMF $E' = K(i)\,\omega \approx V$ from a vanishing flux the rotor must spin ever faster, so $\omega \to \infty$. An unloaded series motor accelerates until centrifugal stresses burst the rotor windings and commutator bars (series runaway). Series motors are therefore coupled permanently to their loads through gears rather than belts, which could snap or slip off.

## 2. The linear torque-speed characteristic and load matching

### Deriving the torque-speed line

For a permanent-magnet DC motor, or a separately excited or shunt motor at constant field current $i_f$, the pole flux $\Phi$ is fixed, so $K_E = K_T = K$ is constant. In steady DC operation the armature current is constant and the inductive drop $L_a\,\mathrm{d}i/\mathrm{d}t$ vanishes. The machine is then described by the armature voltage equation and the torque equation from [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]:

$$
V = E' + iR_a = K\omega + iR_a
$$

$$
T = Ki
$$

Solving the torque equation for the current,

$$
i = \frac{T}{K}.
$$

Substituting into the voltage equation eliminates the current:

$$
V = K\omega + \left(\frac{T}{K}\right)R_a
$$

Subtracting $\dfrac{R_a}{K}T$ from both sides isolates the back-EMF term:

$$
K\omega = V - \frac{R_a}{K}T
$$

Dividing through by $K$ gives the **speed–torque equation** of a constant-flux DC motor:

$$
\omega = \frac{V}{K} - \frac{R_a}{K^2}T
$$

With torque as the subject, the same line is the **torque–speed form**:

$$
T = \frac{KV}{R_a} - \frac{K^2}{R_a}\omega
$$

The line is fixed by its two intercepts and its slope. With no opposing torque ($T = 0$) there is no current and no ohmic drop, so the back EMF $E' = K\omega_0$ rises until it balances the supply voltage. This gives the **no-load speed**

$$
\omega_0 = \frac{V}{K}.
$$

With the rotor locked ($\omega = 0$, as at the instant of starting or with a jammed shaft) the back EMF is zero and the whole supply voltage appears across $R_a$. The **stall current** and **stall torque** are

$$
i_{\text{stall}} = \frac{V}{R_a}, \qquad T_{\text{stall}} = K i_{\text{stall}} = \frac{KV}{R_a}.
$$

Between these, as the load torque rises from zero to the rated torque $T_{\text{nom}}$, the speed falls linearly with gradient

$$
\frac{\mathrm{d}\omega}{\mathrm{d}T} = -\frac{R_a}{K^2}.
$$

The armature is wound with a very small $R_a$, so this slope is shallow. The motor therefore runs at nearly constant speed from $\omega_0$ to its **nominal (rated) operating point** $(T_{\text{nom}}, \omega_{\text{nom}})$, where the continuous armature current reaches its thermal rating $I_{\text{nom}}$.

### Step-down gearboxes and motor sizing

As shown in [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]], the torque of a cylindrical DC machine is bounded by its magnetic loading $B$, its electric loading $A = Z i_c / (\pi D)$ and its rotor volume $V_R = \pi D^2 L / 4$:

$$
T_m = 2 B A V_R \implies V_R = \frac{T_m}{2 B A}
$$

Core saturation limits $B$ (typically $0.5\text{--}1.0\ \text{T}$) and insulation cooling limits $A$, so the size, mass and cost of a motor are set by its torque rating $T_m$, not by its power rating $P = T_m \omega_m$. Driving a heavy, slow load (a lift drum, crane winch or vehicle wheel needing high torque $T_L$ at low speed $\omega_L$) directly at $\omega_m = \omega_L$ would need a large, expensive motor of volume $V_R = T_L / (2BA)$.

Instead, a small high-speed motor running at $\omega_m = G \omega_L$ drives the load through a **step-down gearbox** of ratio $1:G$, with $G > 1$. An ideal lossless gearbox conserves shaft power:

$$
P_{\text{mech}} = T_m \omega_m = T_L \omega_L
$$

Substituting $\omega_m = G \omega_L$ reduces the required motor torque, and with it the rotor volume, by the factor $G$:

$$
T_m = \frac{\omega_L}{\omega_m} T_L = \frac{T_L}{G} \implies V_R = \frac{T_L}{2 G B A}
$$

When the gearbox drives a cable drum of diameter $D_d = 2 r_d$ lifting a net vertical force $F$ at linear speed $v$, the drum turns at $\omega_d = v / r_d$, the motor at $\omega_m = G \omega_d$, and the motor torque is $T_m = \dfrac{F v}{\omega_m} = \dfrac{F r_d}{G}$.

### Load characteristics and equilibrium speed

A motor coupled to a load accelerates according to Newton's second law for rotation, $J\dfrac{\mathrm{d}\omega}{\mathrm{d}t} = T(\omega) - T_L(\omega)$, and reaches equilibrium ($\mathrm{d}\omega/\mathrm{d}t = 0$) where $T(\omega) = T_L(\omega)$. Two load laws cover the problems here.

Hoists, lifts, cranes and conveyor belts are constant-torque loads. Gravity exerts a constant force $F = \Delta m\,g$ whatever the hoisting speed $v$, so the load torque referred to the motor shaft is the same at every speed:

$$
T_L(\omega) = T_0, \qquad P_L(\omega) = T_0 \omega \propto \omega
$$

Because $T_L$ does not depend on speed, neither does the steady motor current $i = T_0 / K$.

Centrifugal fans, blowers and marine propellers meet aerodynamic or hydrodynamic drag that scales with the square of flow speed. The load torque therefore scales with the square of angular velocity and the mechanical power with its cube:

$$
T_L(\omega) = k\omega^2, \qquad P_L(\omega) = T_L(\omega)\,\omega = k\omega^3
$$

Here $k$ is the fan load constant ($\text{N}\,\text{m}\,\text{s}^2\,\text{rad}^{-2}$). Halving the speed of a cooling fan cuts its torque, and the motor current, to one quarter and its shaft power to one eighth.

## 3. Speed control by armature voltage, series resistance and field weakening

With an external resistance $R$ added to the armature circuit, so that $R_{\text{tot}} = R_a + R$, the steady speed of a constant-flux or separately excited motor is

$$
\omega = \frac{V}{K(\Phi)} - \frac{R_a + R}{K(\Phi)^2}T = \frac{V - i(R_a + R)}{K(\Phi)}.
$$

Three quantities in this equation can be varied to control speed: the armature voltage $V$, the series resistance $R$ and the flux $\Phi$.

![[ee_c6_speed_control.png|900]]

### Armature voltage control

Varying $V$ at constant $K$ with $R = 0$ changes the no-load speed $\omega_0 = V/K$ and the stall torque $T_{\text{stall}} = KV/R_a$ in proportion to $V$, while the gradient $-R_a/K^2$ is unchanged. On the $(\omega, T)$ plane the characteristic moves as a family of **parallel straight lines**. No resistor is added and the slope stays shallow (small speed droop), so armature voltage control is smooth, stiff against load disturbances and, with a switch-mode chopper, highly efficient. It is the standard method for controlling speed from zero up to the rated base speed.

### Series armature resistance control

Adding an external rheostat or resistor $R$ in series with the armature at constant $V$ and $K$ raises the circuit resistance to $R_{\text{tot}} = R_a + R$. The no-load intercept $\omega_0 = V/K$, where $i = 0$, is unchanged, while the stall torque falls to $T_{\text{stall}} = \dfrac{KV}{R_a + R}$ and the slope steepens to $-\dfrac{R_a + R}{K^2}$. On the $(\omega, T)$ plane the line pivots downwards about the fixed no-load point $(\omega_0, 0)$.

In continuous running this method has two serious drawbacks. The resistor dissipates $P_R = i^2 R$ as heat all the time, which cuts the efficiency of the drive, and the steeper slope means that small changes in load torque cause large changes in speed (poor speed regulation). A temporary **starter resistor** $R_{\text{start}}$ is still a practical way to limit the inrush current at start-up ($\omega = 0$, $E' = 0$) to $i_{\text{max}} = \dfrac{V}{R_a + R_{\text{start}}}$, until the rotor has accelerated and built up a back EMF $E' = K\omega$.

### Field weakening

In a shunt or separately excited motor, an adjustable resistance in series with the field winding reduces the field current $i_f$, which weakens the pole flux $\Phi$ and reduces $K$. Since $\omega_0 = V/K$, reducing $K$ raises the no-load speed, while the stall torque $T_{\text{stall}} = KV/R_a$ falls and the slope $-R_a/K^2$ becomes much steeper, so the characteristic lines cross one another. The field current is much smaller than the armature current, so resistive control in the field circuit wastes little power. Insulation limits prevent raising $V$ above its rated value, so **field weakening** is the only way to drive a DC motor above its rated base speed, at the cost of a lower maximum torque.

## 4. PWM choppers, H-bridges and brushless drives

### Chopper operation and the freewheeling diode

To vary the effective armature voltage without burning power in a series resistor, DC drives use a **DC chopper**, a pulse-width-modulated buck converter. A fast power switch, typically a MOSFET or IGBT, is driven at a switching frequency $f_{\text{sw}} = 1/T_{\text{sw}}$ above about $15\ \text{kHz}$, at the top of the audible range, so that the laminations do not whine audibly. It chops a fixed DC bus voltage $V_S$ into rectangular pulses of on-time $t_{\text{on}}$ and off-time $t_{\text{off}}$.

The **duty ratio** (duty cycle) $\delta$ is the fraction of each switching period $T_{\text{sw}} = t_{\text{on}} + t_{\text{off}}$ for which the switch conducts:

$$
\delta = \frac{t_{\text{on}}}{t_{\text{on}} + t_{\text{off}}} = \frac{t_{\text{on}}}{T_{\text{sw}}} = f_{\text{sw}} t_{\text{on}}, \qquad 0 \le \delta \le 1
$$

For an ideal switch ($V_{\text{sw}} = 0$) and ideal diode ($V_D = 0$), the motor terminal voltage is $v_m(t) = V_S$ during $t_{\text{on}}$ and $v_m(t) = 0$ during $t_{\text{off}}$. Averaging over one switching period gives the mean armature voltage:

$$
V_{\text{avg}} = \frac{1}{T_{\text{sw}}}\int_0^{T_{\text{sw}}} v_m(t)\,\mathrm{d}t = \frac{t_{\text{on}}}{t_{\text{on}} + t_{\text{off}}} V_S = \delta V_S
$$

When the switch has an on-state voltage drop $V_{\text{sw}}$ (for example $V_{\text{sw}} = 0.6\ \text{V}$), the voltage across the motor during $t_{\text{on}}$ is $V_{\text{on}} = V_S - V_{\text{sw}}$. The simplified chopper model takes the off-state terminal voltage as zero, which gives

$$
V_{\text{avg}} = \delta (V_S - V_{\text{sw}}).
$$

If the forward drop $V_D$ of the conducting freewheeling diode during $t_{\text{off}} = (1-\delta)T_{\text{sw}}$ is also kept, the terminal voltage during $t_{\text{off}}$ is $v_m(t) = -V_D$, and the period-averaged terminal voltage becomes

$$
V_{\text{avg,exact}} = \delta(V_S - V_{\text{sw}}) - (1 - \delta)V_D.
$$

Two mechanisms act during each switching period. First, the armature coils wound on the iron rotor have a significant self-inductance $L_a$, which smooths the current. During $t_{\text{on}}$, when $v_m = V_S - V_{\text{sw}} > E' + iR_a$, the current ramps up at $\dfrac{\mathrm{d}i}{\mathrm{d}t} = \dfrac{v_m - E' - iR_a}{L_a} > 0$, storing magnetic energy $\tfrac{1}{2}L_a i^2$. During $t_{\text{off}}$ it ramps down slowly at $\dfrac{\mathrm{d}i}{\mathrm{d}t} = \dfrac{-V_D - E' - iR_a}{L_a} < 0$. Because $T_{\text{sw}}$ is much shorter than the electrical time constant $\tau_e = L_a / R_a$, the current does not fall to zero; it stays continuous, with a small triangular ripple about its mean $I_{\text{avg}}$.

Second, the **freewheeling diode** ([[Flyback Diode]]) gives that current a path when the switch is off. When the switch turns off abruptly, $L_a$ keeps the armature current flowing in the same direction, and the diode, connected in inverse parallel across the motor terminals, becomes forward-biased and carries the armature current until the switch turns on again. Without it, interrupting $i$ in nanoseconds would induce a voltage spike $v_L = L_a\,\mathrm{d}i/\mathrm{d}t$ of hundreds of volts, which would avalanche and destroy the switch.

![[ee_c6_chopper_fan.png|900]]

### Quadratic speed equation for a chopper-driven fan

When a chopper drives a centrifugal fan or pump with load torque $T_L = k\omega^2$, the steady motor current depends on speed:

$$
i = \frac{T_L}{K} = \frac{k\omega^2}{K}
$$

Substituting this current into the average armature voltage equation $V_{\text{avg}} = iR_a + K\omega$ gives a quadratic in $\omega$:

$$
\left(\frac{R_a k}{K}\right)\omega^2 + K\omega - V_{\text{avg}} = 0
$$

The quadratic formula, keeping the physically meaningful positive root ($\omega > 0$), gives the fan speed at any duty ratio $\delta$:

$$
\omega = \frac{-K + \sqrt{K^2 + 4\left(\dfrac{R_a k}{K}\right)V_{\text{avg}}}}{2\left(\dfrac{R_a k}{K}\right)}
$$

### H-bridge direction control and brushless motors

A single-switch buck chopper can apply only positive voltage ($V_{\text{avg}} \ge 0$) and positive current ($i \ge 0$), so the motor turns in one direction only (first-quadrant operation). Reversing a PM or separately excited motor requires reversing either the armature current or the field flux. In solid-state drives the armature sits across the crossbar of an **H-bridge** of four switches $T_1, T_2, T_3, T_4$, each with an inverse-parallel freewheeling diode $D_1, D_2, D_3, D_4$.

For forward rotation, the diagonally opposite switches $T_1$ (top-left) and $T_4$ (bottom-right) are turned on. This connects the left motor terminal to $+V_S$ and the right terminal to $0\ \text{V}$, driving current from left to right. For reverse rotation, $T_1$ and $T_4$ are turned off and $T_3$ (top-right) and $T_2$ (bottom-left) turned on, which connects the right terminal to $+V_S$ and the left to $0\ \text{V}$ and reverses the armature current and torque.

> [!warning] Shoot-through
> The two switches in the same vertical leg ($T_1$ and $T_2$, or $T_3$ and $T_4$) must never be on at the same time: together they form a direct low-impedance short circuit across $V_S$ (shoot-through). Gate drivers insert a short dead-time between turning one switch off and turning its partner on.

In **brushless DC (BLDC)** and **stepper** motors, the commutator and carbon brushes, which suffer from friction, sparking, electrical noise and wear, are removed by turning the machine inside out. The permanent magnets are mounted on the rotor and the multi-phase armature windings on the stator. Rotor position sensors, such as Hall-effect sensors or optical encoders, feed a microcontroller and transistor inverter bridge that switches current between the stator coils in step with the rotor angle, so commutation is done electronically. Where neither speed control nor commutator maintenance is wanted, in heavy fixed-speed industrial plant, the AC **induction motor** remains the rugged, low-cost choice.

## Worked examples

### Counterweighted passenger lift

A permanent-magnet DC motor drives a passenger lift through a $1:20$ step-down gearbox, so the motor turns $20$ times faster than the winding drum, of diameter $D_d = 0.40\ \text{m}$. The empty cabin has mass $m_{\text{cabin}} = 200\ \text{kg}$ and is balanced by a counterweight of mass $m_{\text{cw}} = 300\ \text{kg}$. Take $g = 9.81\ \text{N}\,\text{kg}^{-1}$ and neglect friction in the pulley and gearbox. (a) Raising $m_{p,1} = 300\ \text{kg}$ of passengers at a constant $v = 1.0\ \text{m}\,\text{s}^{-1}$, the motor draws $I_1 = 20\ \text{A}$ at a terminal voltage $V_1 = 102\ \text{V}$. Find the mechanical power, the motor speed $\omega_m$, the motor torque $T_1$, the constants $K_T = K_E$ and the armature resistance $R_a$. (b) Find the terminal voltage $V_2$ needed to raise $m_{p,2} = 500\ \text{kg}$ at the same speed. (2021 exam question)

(a) The rising side of the cable carries the cabin and passengers, $m_{\text{cabin}} + m_{p,1}$, while the descending counterweight $m_{\text{cw}}$ assists the drum. The net mass lifted against gravity is

$$
\Delta m_1 = m_{\text{cabin}} + m_{p,1} - m_{\text{cw}} = 200\ \text{kg} + 300\ \text{kg} - 300\ \text{kg} = 200\ \text{kg}.
$$

The unbalanced gravitational force at the drum rim is

$$
F_1 = \Delta m_1 g = 200\ \text{kg} \times 9.81\ \text{N}\,\text{kg}^{-1} = 1962\ \text{N}.
$$

Raising this force at $v = 1.0\ \text{m}\,\text{s}^{-1}$ requires mechanical power

$$
P_{\text{mech},1} = F_1 v = 1962\ \text{N} \times 1.0\ \text{m}\,\text{s}^{-1} = 1962\ \text{W}.
$$

The drum radius is $r_d = D_d / 2 = 0.40\ \text{m} / 2 = 0.20\ \text{m}$, so the drum turns at

$$
\omega_d = \frac{v}{r_d} = \frac{1.0\ \text{m}\,\text{s}^{-1}}{0.20\ \text{m}} = 5.0\ \text{rad}\,\text{s}^{-1}.
$$

Through the $1:20$ gearbox ($G = 20$) the motor turns $20$ times faster:

$$
\omega_m = G\omega_d = 20 \times 5.0\ \text{rad}\,\text{s}^{-1} = 100\ \text{rad}\,\text{s}^{-1}
$$

Conserving power between the motor shaft and the cable gives the motor torque:

$$
T_1 = \frac{P_{\text{mech},1}}{\omega_m} = \frac{1962\ \text{W}}{100\ \text{rad}\,\text{s}^{-1}} = 19.62\ \text{N}\,\text{m}
$$

Equivalently, the drum torque is $T_{d,1} = F_1 r_d = 1962\ \text{N} \times 0.20\ \text{m} = 392.4\ \text{N}\,\text{m}$, which the $1:20$ gearbox reduces at the motor shaft to $T_1 = T_{d,1}/20 = 392.4/20 = 19.62\ \text{N}\,\text{m}$.

The motor develops $T_1 = 19.62\ \text{N}\,\text{m}$ at $I_1 = 20\ \text{A}$, so its torque constant, and the equal SI back-EMF constant, are

$$
K_T = \frac{T_1}{I_1} = \frac{19.62\ \text{N}\,\text{m}}{20\ \text{A}} = 0.981\ \text{N}\,\text{m}\,\text{A}^{-1}, \qquad K_E = 0.981\ \text{V}\,\text{s}\,\text{rad}^{-1}.
$$

At $\omega_m = 100\ \text{rad}\,\text{s}^{-1}$ the back EMF is

$$
E_1' = K_E \omega_m = 0.981\ \text{V}\,\text{s}\,\text{rad}^{-1} \times 100\ \text{rad}\,\text{s}^{-1} = 98.1\ \text{V}.
$$

From $V_1 = E_1' + I_1 R_a$, the armature resistance is

$$
R_a = \frac{V_1 - E_1'}{I_1} = \frac{102\ \text{V} - 98.1\ \text{V}}{20\ \text{A}} = \frac{3.9\ \text{V}}{20\ \text{A}} = 0.195\ \Omega.
$$

(b) With $m_{p,2} = 500\ \text{kg}$ the net unbalanced mass doubles:

$$
\Delta m_2 = m_{\text{cabin}} + m_{p,2} - m_{\text{cw}} = 200\ \text{kg} + 500\ \text{kg} - 300\ \text{kg} = 400\ \text{kg}
$$

The net cable force and mechanical power at $v = 1.0\ \text{m}\,\text{s}^{-1}$ are

$$
F_2 = \Delta m_2 g = 400\ \text{kg} \times 9.81\ \text{N}\,\text{kg}^{-1} = 3924\ \text{N}, \qquad P_{\text{mech},2} = F_2 v = 3924\ \text{W}.
$$

The linear speed is unchanged, so the motor speed stays at $\omega_m = 100\ \text{rad}\,\text{s}^{-1}$ and the back EMF at $E_2' = K_E \omega_m = 98.1\ \text{V}$. The new torque and current are

$$
T_2 = \frac{P_{\text{mech},2}}{\omega_m} = \frac{3924\ \text{W}}{100\ \text{rad}\,\text{s}^{-1}} = 39.24\ \text{N}\,\text{m},
$$

$$
I_2 = \frac{T_2}{K_T} = \frac{39.24\ \text{N}\,\text{m}}{0.981\ \text{N}\,\text{m}\,\text{A}^{-1}} = 40.0\ \text{A}.
$$

Substituting $I_2 = 40.0\ \text{A}$, $R_a = 0.195\ \Omega$ and $E_2' = 98.1\ \text{V}$ into the voltage equation gives the terminal voltage:

$$
V_2 = E_2' + I_2 R_a = 98.1\ \text{V} + (40.0\ \text{A})(0.195\ \Omega) = 98.1\ \text{V} + 7.8\ \text{V} = 105.9\ \text{V}
$$

Doubling the torque from $19.62\ \text{N}\,\text{m}$ to $39.24\ \text{N}\,\text{m}$ needs only $3.9\ \text{V}$ more (from $102\ \text{V}$ to $105.9\ \text{V}$, a $3.8\%$ change) to hold the speed, because the PM characteristic has the shallow slope $-R_a/K^2$.

> [!check] Copper-loss check on $R_a$ and the power balance
> In (a) the electrical input is $P_{\text{in},1} = V_1 I_1 = 102\ \text{V} \times 20\ \text{A} = 2040\ \text{W}$ and the mechanical output is $P_{\text{mech},1} = 1962\ \text{W}$. With friction neglected, the difference is armature copper loss, so
> $$P_{\text{cu},1} = P_{\text{in},1} - P_{\text{mech},1} = 2040\ \text{W} - 1962\ \text{W} = 78\ \text{W} \implies R_a = \frac{P_{\text{cu},1}}{I_1^2} = \frac{78\ \text{W}}{(20\ \text{A})^2} = \frac{78}{400}\ \Omega = 0.195\ \Omega\ \checkmark$$
> In (b) the input is $P_{\text{in},2} = 105.9 \times 40.0 = 4236\ \text{W}$; subtracting the copper loss $I_2^2 R_a = (40.0)^2 \times 0.195 = 312\ \text{W}$ leaves $4236 - 312 = 3924\ \text{W} = P_{\text{mech},2}$.

### Series and starting resistance on a 230 V motor

A permanent-magnet DC motor connected across a $V = 230\ \text{V}$ DC supply draws $i = 20\ \text{A}$ while driving a constant-torque load. It has $K_E = 1.00\ \text{V}\,\text{s}\,\text{rad}^{-1}$ (so $K_T = 1.00\ \text{N}\,\text{m}\,\text{A}^{-1}$) and $R_a = 0.50\ \Omega$. (a) Find the steady speed $\omega_1$ and the mechanical output $P_{\text{mech},1}$. (b) Find the series resistance $R$ that halves the speed ($\omega_2 = \tfrac{1}{2}\omega_1$) with the same load, and the power dissipated in it. (c) Find the stall current $i_{\text{stall}}$ if the motor is switched straight onto $230\ \text{V}$ at standstill, and the starter resistance $R_{\text{start}}$ that limits the starting current to $i_{\text{max}} = 40\ \text{A}$ (twice rated current).

(a) From $V = K_E \omega_1 + i R_a$ with $R = 0$,

$$
\omega_1 = \frac{V - i R_a}{K_E} = \frac{230\ \text{V} - (20\ \text{A})(0.50\ \Omega)}{1.00\ \text{V}\,\text{s}\,\text{rad}^{-1}} = \frac{230\ \text{V} - 10\ \text{V}}{1.00\ \text{V}\,\text{s}\,\text{rad}^{-1}} = 220\ \text{rad}\,\text{s}^{-1} \quad (2101\ \text{rpm}).
$$

The torque and shaft power, neglecting friction, are

$$
T = K_T i = (1.00\ \text{N}\,\text{m}\,\text{A}^{-1})(20\ \text{A}) = 20.0\ \text{N}\,\text{m},
$$

$$
P_{\text{mech},1} = T \omega_1 = (20.0\ \text{N}\,\text{m})(220\ \text{rad}\,\text{s}^{-1}) = 4400\ \text{W}.
$$

(b) The load torque stays at $T = 20.0\ \text{N}\,\text{m}$, so the current stays at $i = T/K_T = 20\ \text{A}$. The target speed is

$$
\omega_2 = \frac{\omega_1}{2} = \frac{220\ \text{rad}\,\text{s}^{-1}}{2} = 110\ \text{rad}\,\text{s}^{-1}.
$$

At this speed the back EMF falls to $E_2' = K_E \omega_2 = 110\ \text{V}$. With $R$ in series with $R_a$, the loop equation is

$$
V = K_E \omega_2 + i(R_a + R).
$$

Solving for the total resistance,

$$
R_a + R = \frac{V - K_E \omega_2}{i} = \frac{230\ \text{V} - (1.00\ \text{V}\,\text{s}\,\text{rad}^{-1})(110\ \text{rad}\,\text{s}^{-1})}{20\ \text{A}} = \frac{120\ \text{V}}{20\ \text{A}} = 6.00\ \Omega.
$$

Subtracting $R_a = 0.50\ \Omega$ gives the external resistance:

$$
R = 6.00\ \Omega - 0.50\ \Omega = 5.50\ \Omega
$$

The power wasted continuously in $R$ is

$$
P_R = i^2 R = (20\ \text{A})^2 (5.50\ \Omega) = 400\ \text{A}^2 \times 5.50\ \Omega = 2200\ \text{W} \quad (2.20\ \text{kW}).
$$

(c) At the instant of starting the back EMF is $E' = K_E(0) = 0\ \text{V}$. Connected straight to $230\ \text{V}$, the stall current and torque are

$$
i_{\text{stall}} = \frac{V}{R_a} = \frac{230\ \text{V}}{0.50\ \Omega} = 460\ \text{A}, \qquad T_{\text{stall}} = K_T i_{\text{stall}} = 460\ \text{N}\,\text{m}.
$$

This $460\ \text{A}$ surge is $23$ times the $20\ \text{A}$ running current and would burn out the commutator and brushes. Limiting the starting current to $i_{\text{max}} = 40\ \text{A}$ needs a total resistance $R_a + R_{\text{start}} = V / i_{\text{max}}$:

$$
R_{\text{start}} = \frac{V}{i_{\text{max}}} - R_a = \frac{230\ \text{V}}{40\ \text{A}} - 0.50\ \Omega = 5.75\ \Omega - 0.50\ \Omega = 5.25\ \Omega
$$

Once the rotor accelerates and $E' = K_E\omega$ rises, $R_{\text{start}}$ is switched out so that it wastes no power in normal running.

> [!check] Power budget, and the same speed from a PWM chopper
> With resistive control at $\omega_2 = 110\ \text{rad}\,\text{s}^{-1}$,
> $$\begin{aligned} P_{\text{in}} &= V i = (230\ \text{V})(20\ \text{A}) = 4600\ \text{W} \\ P_{\text{mech},2} &= E_2' i = (110\ \text{V})(20\ \text{A}) = 2200\ \text{W} \\ P_{\text{cu},a} &= i^2 R_a = (20\ \text{A})^2(0.50\ \Omega) = 200\ \text{W} \\ P_R &= i^2 R = (20\ \text{A})^2(5.50\ \Omega) = 2200\ \text{W} \end{aligned}$$
> and $2200 + 200 + 2200 = 4600\ \text{W} = P_{\text{in}}\ \checkmark$. The drive efficiency is $\eta_{\text{res}} = \dfrac{2200\ \text{W}}{4600\ \text{W}} = 47.8\%$, with nearly half the supply power lost in the external resistor.
> An ideal PWM chopper instead lowers the average terminal voltage to $V_{\text{avg}} = E_2' + i R_a = 110\ \text{V} + (20\ \text{A})(0.50\ \Omega) = 120\ \text{V}$ (duty ratio $\delta = 120/230 = 52.2\%$). The input falls to $P_{\text{in,PWM}} = 120\ \text{V} \times 20\ \text{A} = 2400\ \text{W}$, and the efficiency rises from $47.8\%$ to $\eta_{\text{PWM}} = \dfrac{2200\ \text{W}}{2400\ \text{W}} = 91.7\%$.

### Chopper speed control of a cooling fan

A permanent-magnet DC motor with $R_a = 0.10\ \Omega$ drives a cooling fan whose power is proportional to the cube of speed ($P_L \propto \omega^3$, so $T_L = k\omega^2$). It is supplied from a $V_S = 12.0\ \text{V}$ battery through a transistor chopper at $20\ \text{kHz}$; the switch and the freewheeling diode each drop $0.60\ \text{V}$ when conducting. (a) At $100\%$ duty ($\delta = 1.00$) the motor runs at $N_{100} = 3600\ \text{rpm}$ and draws $I_{100} = 15.0\ \text{A}$. Find the terminal voltage $V_{100}$, the constants $K_E = K_T$, the torque $T_{100}$ and the fan constant $k$. (b) The duty ratio is reduced to $\delta = 0.40$. Using the simplified model $V_{\text{avg}} = \delta V_{100}$, set up and solve the quadratic for the new speed $\omega_{40}$ (in $\text{rad}\,\text{s}^{-1}$ and $\text{rpm}$) and current $I_{40}$, and compare the unrounded result with the one obtained when $K_E$ and $k$ are rounded to two significant figures.

(a) At $\delta = 1.00$ the switch is on continuously and drops $V_{\text{sw}} = 0.60\ \text{V}$, so the motor sees

$$
V_{100} = V_S - V_{\text{sw}} = 12.0\ \text{V} - 0.60\ \text{V} = 11.4\ \text{V}.
$$

The speed in radians per second is

$$
\omega_{100} = \frac{2\pi N_{100}}{60} = \frac{2\pi \times 3600}{60} = 120\pi\ \text{rad}\,\text{s}^{-1} = 376.99\ \text{rad}\,\text{s}^{-1} \quad (\approx 377\ \text{rad}\,\text{s}^{-1}).
$$

From $V_{100} = K_E \omega_{100} + I_{100} R_a$, the motor constants are

$$
K_E = \frac{V_{100} - I_{100} R_a}{\omega_{100}} = \frac{11.4\ \text{V} - (15.0\ \text{A})(0.10\ \Omega)}{376.99\ \text{rad}\,\text{s}^{-1}} = \frac{9.90\ \text{V}}{376.99\ \text{rad}\,\text{s}^{-1}} = 0.02626\ \text{V}\,\text{s}\,\text{rad}^{-1},
$$

$$
K_T = K_E = 0.02626\ \text{N}\,\text{m}\,\text{A}^{-1} \quad (0.026 \text{ to two significant figures}).
$$

The torque driving the fan at $3600\ \text{rpm}$ is

$$
T_{100} = K_T I_{100} = (0.02626\ \text{N}\,\text{m}\,\text{A}^{-1})(15.0\ \text{A}) = 0.3939\ \text{N}\,\text{m} \quad (0.39\ \text{N}\,\text{m} \text{ to two significant figures}).
$$

Since $P_L = T_L \omega \propto \omega^3$, the fan torque is $T_L = k\omega^2$. Evaluating $k$ at full duty,

$$
k = \frac{T_{100}}{\omega_{100}^2} = \frac{0.3939\ \text{N}\,\text{m}}{(376.99\ \text{rad}\,\text{s}^{-1})^2} = \frac{0.3939}{1.4212 \times 10^5} = 2.772 \times 10^{-6}\ \text{N}\,\text{m}\,\text{s}^2\,\text{rad}^{-2} \quad (2.7 \times 10^{-6} \text{ when rounded}).
$$

(b) Under the simplified model, the average terminal voltage at $\delta = 0.40$ is

$$
V_{40} = \delta V_{100} = 0.40 \times 11.4\ \text{V} = 4.56\ \text{V}.
$$

At any steady speed $\omega$, the fan torque $T = k\omega^2$ needs an armature current

$$
I = \frac{T}{K_T} = \frac{k\omega^2}{K_T}.
$$

Substituting into $V_{40} = I R_a + K_E \omega$ gives

$$
V_{40} = \left(\frac{R_a k}{K_T}\right)\omega^2 + K_E \omega.
$$

With the unrounded values $R_a = 0.10\ \Omega$, $K_E = K_T = 0.02626\ \text{V}\,\text{s}\,\text{rad}^{-1}$ and $k = 2.772 \times 10^{-6}\ \text{N}\,\text{m}\,\text{s}^2\,\text{rad}^{-2}$, the quadratic coefficient is $\dfrac{R_a k}{K_T} = \dfrac{0.10 \times 2.772 \times 10^{-6}}{0.02626} = 1.0554 \times 10^{-5}\ \text{V}\,\text{s}^2\,\text{rad}^{-2}$. Dividing the whole equation by $1.0554 \times 10^{-5}$ puts it in monic form:

$$
\omega^2 + 2488.2\,\omega - 4.3205 \times 10^5 = 0
$$

The positive root is

$$
\omega_{40} = \frac{-2488.2 + \sqrt{(2488.2)^2 + 4(4.3205 \times 10^5)}}{2} = \frac{-2488.2 + 2814.1}{2} = 163.0\ \text{rad}\,\text{s}^{-1} \quad (1556\ \text{rpm}),
$$

and the armature current at $40\%$ duty is

$$
I_{40} = \frac{k\omega_{40}^2}{K_T} = \frac{(2.772 \times 10^{-6})(163.0)^2}{0.02626} = 2.80\ \text{A}.
$$

With the values rounded to two significant figures, $K_E = K_T = 0.026$ and $k = 2.7 \times 10^{-6}$, the coefficient is $\dfrac{R_a k}{K_T} \approx 1.0 \times 10^{-5}$. The equation becomes $\omega^2 + 2600\,\omega - 4.56 \times 10^5 = 0$, with positive root $\omega_{40} = 164.9\ \text{rad}\,\text{s}^{-1}$ ($1575\ \text{rpm}$). If the $0.60\ \text{V}$ diode drop during the $60\%$ off-time is also subtracted, $V_{\text{avg,exact}} = 0.40(11.4) - 0.60(0.60) = 4.20\ \text{V}$ and the speed is $150.8\ \text{rad}\,\text{s}^{-1} = 1440\ \text{rpm}$.

> [!check] Voltage loop and cubic power scaling
> At $\omega_{40} = 163.0\ \text{rad}\,\text{s}^{-1}$ and $I_{40} = 2.80\ \text{A}$,
> $$I_{40} R_a + K_E \omega_{40} = (2.80\ \text{A})(0.10\ \Omega) + (0.02626\ \text{V}\,\text{s}\,\text{rad}^{-1})(162.97\ \text{rad}\,\text{s}^{-1}) = 0.280\ \text{V} + 4.280\ \text{V} = 4.560\ \text{V} = V_{40}\ \checkmark$$
> The speed ratio is $163.0/377.0 = 0.4323$, so the fan power should fall to $(0.4323)^3 = 8.08\%$ of its full-speed value. Directly, it falls from $P_{100} = T_{100}\omega_{100} = 148.5\ \text{W}$ to $P_{40} = k\omega_{40}^3 = 12.0\ \text{W}$, and $12.0/148.5 = 8.08\%\ \checkmark$.

## Links

- Parent: [[FEEG1004 Electronics Hub]]
- Previous: [[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]
- Next: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]
- Concepts: [[Torque-Speed Characteristics of DC Motors]] · [[DC Motor Speed Control]] · [[Flyback Diode]] · [[Electric and Magnetic Loading]]
- Tutorial solutions: [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions]] (Q5, Q6)
- Closed-loop servo actuators (aircraft control surfaces, thrust-vectoring gimbals, robot joints) place the linear motor model $\omega(V, T)$ inside a feedback loop, with the chopper duty ratio $\delta$ as the control input from the compensator: [[SESA2027 B1 - Control System Fundamentals and PID Control]], [[PID Controller]].
- Spacecraft reaction wheels use brushless DC motors driven by four-quadrant H-bridges or three-phase inverters, and their momentum capacity is bounded by the no-load speed $\omega_0 = V/K_E$: [[Reaction Wheels and Momentum Dumping]].
- A PWM signal is generated in hardware by comparing a control voltage with a high-frequency triangle carrier in an [[Op-Amp Comparator]], or by a digital timer built from [[Shift Registers and Binary Counters]].

## Sources

- `02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf` (§4.4–4.8, pp. 26–32: torque–speed equation, wound-field motor types, resistive and field speed control, the simplified chopper model $V_{\text{avg}} = \delta(V_S - V_{\text{sw}})$ with zero off-state voltage, H-bridge and brushless motors; the chopper fan example on p. 30 rounds to $K_E = K_T = 0.026$, $T_{100} = 0.39\ \text{N}\,\text{m}$ and $k = 2.7 \times 10^{-6}$)
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf` (slides 1–12: torque–speed derivation, field connections, 2021 exam passenger lift problem)
- `02 - Sources/S2 Machines/S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf` (slides 1–13: speed control curves, series resistance example, PWM chopper, freewheeling diode MCQ, cooling fan example, H-bridge and brushless drives)
- `02 - Sources/Lectures/FEEG1004 Lecture 2025-02-20.txt` (ll. 1–515: torque–speed characteristics, lift problem, speed control, chopper fan problem and H-bridges)
- `02 - Sources/Tutorial Sheets/Tutorial Sheet 06 - Electric Machines 2 - DC Motors & Characteristics.pdf` (Q5 on step-down gearboxes and Q6 on shunt and series torque–speed characteristics)

## Self-study tasks

### Core

- [ ] Explain, using $T = 2BAV_R$ and $P = T\omega$, why a slow high-torque load is driven by a fast motor through a step-down gearbox rather than by a direct-drive motor of the same power rating (Tutorial Sheet 6 Q5; 2025-02-20 transcript ll. 68–105). → [[#Step-down gearboxes and motor sizing]]; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q5: Why use a step-down gearbox with a slow load?|Tutorial 6 Q5]].
- [ ] Sketch and derive the torque–speed characteristics of shunt and series motors, give an application for each, and explain why a series motor must never run without a load (Tutorial Sheet 6 Q6; 2025-02-20 transcript ll. 15–67). → [[#1. Field connections and series runaway]]; [[FEEG1004 Tutorial 6 - DC Motors and Characteristics Solutions#Q6: Torque–speed characteristics, shunt vs series|Tutorial 6 Q6]].
- [ ] Work both parts of the counterweighted lift problem ($300\ \text{kg}$ and $500\ \text{kg}$ of passengers, $1:20$ gearbox, $0.40\ \text{m}$ drum, $1.0\ \text{m}\,\text{s}^{-1}$) and check $K_T$, $R_a$ and $V_2$ (Electric Machines 07 slides 9–11; 2025-02-20 transcript ll. 68–195). → [[#Counterweighted passenger lift]].
- [ ] Explain what the armature current does during $t_{\text{off}}$ of a PWM chopper and what would happen to the switch without the freewheeling diode (Electric Machines 08 slide 8; 2025-02-20 transcript ll. 320–374). → [[#Chopper operation and the freewheeling diode]].

### Further practice

- [ ] For the cooling-fan motor at $\delta = 0.80$, find $V_{80}$, the steady speed in $\text{rpm}$ and the mean armature current, and sketch $v_m(t)$ and $i(t)$ over two switching periods, comparing with `ee_c6_chopper_fan.png` (Electric Machines 08 slide 9; Sharkh notes p. 30). → [[#Chopper speed control of a cooling fan]]; [[#Chopper operation and the freewheeling diode]].
- [ ] With no passengers ($m_p = 0\ \text{kg}$), the $300\ \text{kg}$ counterweight outweighs the $200\ \text{kg}$ cabin as the lift rises at $1.0\ \text{m}\,\text{s}^{-1}$. Show that gravity now aids the motion, find the sign of $I$, and find $V = E' + IR_a$ with the machine acting as a regenerative brake returning power to the DC bus (suggested, not lecturer-set). → [[#Counterweighted passenger lift]].

## Transcript and slide slips

> [!warning] Lift torque slide prints 2000 instead of 1962 W
> Where: [[#Counterweighted passenger lift]]
> On slide 10 of `S2-W18-21 Electric Machines 07 - DC Motors Characteristics - Lecture Slides.pdf`, after computing $P = F \times v = 1962 \times 1 = 1962\ \text{W}$, the next line prints $T = \dfrac{P}{\omega} = \dfrac{2000}{100} = 19.62\ \text{N}\,\text{m}$. The numerator $2000$ is a typographical slip for $1962\ \text{W}$; dividing $1962\ \text{W}$ by $\omega_m = 100\ \text{rad}\,\text{s}^{-1}$ gives the printed answer $19.62\ \text{N}\,\text{m}$.

> [!warning] Back-EMF constant unit printed as V s rad
> Where: [[#Series and starting resistance on a 230 V motor]]
> Slide 3 of `S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf` gives the motor constant as "$K_E' = 1\ \text{v}\cdot\text{s}\cdot\text{rad}$". Since $E' = K_E\omega$ is in volts and $\omega$ in $\text{rad}\,\text{s}^{-1}$, the SI unit of $K_E$ is $\text{V}\,\text{s}\,\text{rad}^{-1}$ (equivalent to $\text{N}\,\text{m}\,\text{A}^{-1}$).

> [!warning] Armature resistance printed as 0.1 W
> Where: [[#Chopper speed control of a cooling fan]]
> Slide 9 of `S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf` gives the fan motor an "armature resistance of $0.1\ \text{W}$". As in earlier decks, a missing Symbol-font mapping turned the capital omega $\Omega$ (ASCII `W` in the Symbol font) into a Latin `W`; the armature resistance is $R_a = 0.1\ \Omega$.

> [!warning] Spelling slips in §4.5 and §4.6 of the printed notes
> Where: [[#1. Field connections and series runaway]]
> In `S2 Electric Machines Notes - Sharkh.pdf`, the opening paragraph of §4.5 (p. 27) prints "connected in paralle (shunt), in series, or a combination of series and shunt (compund)" and "Connected seperately", and the chopper fan example on p. 30 prints "Substituting for $I$ from the second equation into the fist equation" and "When the duty cycle was reduce to 40%". These are spelling slips for *parallel*, *compound*, *separately*, *first* and *reduced*.
