---
title: "SESA1015 A04 - Rocket Equation and Launch Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Astronautics"
order: 16
tags: [sesa1015, rocket-equation, thrust, specific-impulse]
aliases: ["SESA1015 Astronautics 4", "Rocket Performance"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 A03 - Launch Environment]]"]
next_topics: ["[[SESA1015 A05 - Staging and Payload Fraction]]"]
key_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Mass Fractions]]"]
tutorial_sheets: []
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf"]
---

# SESA1015 A04 - Rocket Equation and Launch Performance

> [!abstract] Summary
> A rocket accelerates by expelling mass; it does not need to push against the atmosphere. Momentum flux and nozzle pressure create thrust, while the changing vehicle mass makes attainable velocity increment logarithmic in mass ratio. Specific impulse measures propellant efficiency, but a launch vehicle must also pay gravity, drag and steering losses. The rocket equation is therefore a mass-and-propulsion ledger, not a complete trajectory model.

## 1. Thrust from a control volume

For a steady one-dimensional nozzle with negligible inlet momentum in the rocket frame,

$$\boxed{T=\dot m v_e+(p_e-p_a)A_e}.$$

- $\dot m v_e$ is momentum thrust.
- $(p_e-p_a)A_e$ is pressure thrust.
- At the design expansion condition $p_e=p_a$, pressure thrust is zero, not total thrust.

Define effective exhaust velocity

$$c\equiv\frac{T}{\dot m}$$

and specific impulse

$$\boxed{I_{sp}=\frac{T}{\dot m g_0}=\frac{c}{g_0}}.$$

$I_{sp}$ is reported in seconds because it is thrust divided by propellant weight flow.

## 2. Deriving the ideal rocket equation

Consider a rocket of mass $m$ and velocity $v$ ejecting a small mass $-dm>0$ with exhaust velocity $c$ relative to the vehicle. Neglect external force over the infinitesimal interval. Momentum conservation gives

$$m\,dv=-c\,dm.$$

Because vehicle mass decreases, $dm<0$, so $dv>0$. Rearrange:

$$dv=-c\frac{dm}{m}.$$

For constant $c$, integrate from $m_0$ to $m_f$:

$$\boxed{\Delta v=c\ln\frac{m_0}{m_f}=g_0I_{sp}\ln\frac{m_0}{m_f}}.$$

![[astro_rocket_equation.png|760]]

## 3. What $\Delta v$ means

$\Delta v$ is the time integral of thrust acceleration, expressed as an equivalent velocity change. It is a capability budget, not necessarily the difference between initial and final speed. During ascent, thrust may be spent holding against gravity or redirecting the velocity vector.

## 4. Real ascent equation

Along the trajectory, a schematic equation is

$$\dot v=\frac Tm-\frac Dm-g\sin\gamma$$

with additional geometry for flight-path rotation. Integrating motivates

$$\boxed{\Delta v_{prop}=\Delta v_{required}+\Delta v_{gravity}+\Delta v_{drag}+\Delta v_{steering}+\Delta v_{residual}}.$$

- Gravity loss grows when the vehicle spends longer thrusting with a vertical component.
- Drag loss depends on atmospheric density, speed, reference area and drag coefficient.
- Steering loss occurs when thrust is not aligned with velocity.
- Residuals and margins account for unusable propellant and dispersions.

## 5. Thrust-to-weight ratio

At liftoff,

$$\frac TW>1$$

is required for upward acceleration in the simplest vertical model. As propellant burns, mass falls and $T/W$ often rises, increasing acceleration. Throttling may be used to limit max-q or crew/payload g-load.

## 6. Nozzle and ambient pressure

A nozzle converts thermal/pressure energy into directed kinetic energy. Expansion ratio trades sea-level and vacuum performance:

- underexpanded: $p_e>p_a$, further expansion possible outside;
- ideally expanded: $p_e=p_a$;
- overexpanded: $p_e<p_a$, with risk of separation at low altitude.

Vacuum engines can use larger expansion ratios because external pressure is low.

## 7. Worked rocket-equation check

Let $I_{sp}=320\ \mathrm s$ and $m_0/m_f=4$:

$$c=g_0I_{sp}=9.80665(320)=3138\ \mathrm{m,s^{-1}},$$

$$\Delta v=3138\ln4=4350\ \mathrm{m,s^{-1}}.$$

Increasing mass ratio from 4 to 5 gives only

$$\Delta(\Delta v)=3138\ln(5/4)\approx700\ \mathrm{m,s^{-1}},$$

illustrating the logarithmic return.

## 8. Sensitivity and design meaning

$$\frac{\partial\Delta v}{\partial I_{sp}}=g_0\ln\frac{m_0}{m_f},\qquad \frac{\partial\Delta v}{\partial m_0}=\frac c{m_0}$$

Higher $I_{sp}$ helps, but propulsion selection also depends on thrust, density, storability, complexity, safety, restart and cost. Electric propulsion has high $I_{sp}$ but typically too little thrust for Earth launch.

## 9. Workflow

1. Define the initial and final mass of the same burn.
2. Ensure dry mass and payload remain in $m_f$ unless discarded.
3. Convert $I_{sp}$ to $c=g_0I_{sp}$.
4. Use the natural logarithm.
5. Add stages as separate burn intervals.
6. Keep ideal $\Delta v$ distinct from mission and loss terms.

> [!failure] Common errors
> - Setting $m_f$ equal to zero-propellant stage dry mass while forgetting payload/upper stages.
> - Treating $I_{sp}$ in seconds as an exhaust speed.
> - Using $\log_{10}$.
> - Saying a rocket pushes on air.
> - Equating orbital speed directly to launch $\Delta v$ without losses and Earth rotation.

## Year 2 bridge

- [[Tsiolkovsky Rocket Equation]] is the reusable derivation/reference.
- [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]] connects chamber/nozzle performance to launch-vehicle $\Delta v$.
- [[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]] develops propellants and nozzle sizing.
- [[SESA2024 07 - Spacecraft Propulsion]] compares high-thrust and high-$I_{sp}$ propulsion for in-space use.

