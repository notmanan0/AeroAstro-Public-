---
title: "SESA1015 T04 - Range and Endurance Solutions"
module: "SESA1015 Intro to Aero & Astro"
type: tutorial-solutions
stream: "Mechanics of Flight revision workbook"
order: 4
tags: [sesa1015, tutorial, range, endurance, breguet]
aliases: ["SESA1015 Revision Q5 Q16 Q20 Q27 Q29", "Range and Endurance Solutions"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M06 - Jet Aircraft Range and Endurance]]", "[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]"]
sources: ["04 - Labs & Coursework/Revision & Spreadsheets/SESA1015 - Revision Questions (Original).xlsx (Questions 5, 16, 20, 27, 29)", "02 - Sources/Mechanics of Flight/Calculator for Revision Questions.xlsx"]
---

# SESA1015 T04 - Range and Endurance Solutions

Worked solutions to the range and endurance questions of the revision workbook. The question wording is authoritative; each sheet's input cells hold different (randomised) numbers, which are noted under each question with the answer they give. Constants: $g=9.81$ m/s², $R=287$ J/(kg K), $\gamma=1.4$, $\rho_{SL}=1.225$ kg/m³, 1 nautical mile $=1852$ m. Every number below was recomputed in Python. The theory is in [[SESA1015 M06 - Jet Aircraft Range and Endurance]] and [[SESA1015 M07 - Propeller Aircraft Range and Endurance]].

| Question | Topic | Answer |
|---:|---|---:|
| 5 | jet range, constant $L/D$ (Breguet) | 1691 km |
| 16 | jet SFC needed for a given range | $2.725\times10^{-4}$ N s⁻¹ N⁻¹ |
| 20 | flight time at fixed Mach, summer against winter | 48.8 min |
| 27 | minimum propeller fuel for a given range | 1367 N |
| 29 | jet range at constant altitude | 8544 km |

## Question 5

A jet aircraft with span 86.3 m and aspect ratio 8.5 cruises at $M=0.82$ in the stratosphere, where $T=223$ K and $\sigma=0.31$. The wing loading at the start of cruise is 5414 N/m² and the specific fuel consumption is 1.5 N of fuel per hour per newton of thrust. Find the distance covered when 683 182 N of fuel has been used, assuming $L/D$ stays constant, with $C_D=0.016+0.043C_L^2$. Answer in km to the nearest whole number.

With constant $L/D$ and constant Mach number in the stratosphere (constant speed, since $a$ is constant), the cruise is a cruise-climb and the Breguet range equation applies ([[SESA1015 M06 - Jet Aircraft Range and Endurance#4. Range at constant speed - the Breguet range equation|M06 §4]]):

$$
R=\frac{V}{c_t}\frac{L}{D}\ln\frac{W_1}{W_2}.
$$

The start-of-cruise wing loading already includes the fuel, so it gives $W_1$ directly:

$$
\begin{aligned}
S&=\frac{b^2}{AR}=\frac{86.3^2}{8.5}=876.20\ \text{m}^2,\\
W_1&=5414\times876.20=4\,743\,740\ \text{N},\qquad W_2=W_1-683\,182=4\,060\,558\ \text{N},\\
\ln\frac{W_1}{W_2}&=\ln1.16825=0.15551 .
\end{aligned}
$$

Speed, density and coefficients at the start of cruise:

$$
\begin{aligned}
a&=\sqrt{1.4\times287\times223}=299.33\ \text{m/s},\qquad V=0.82\times299.33=245.45\ \text{m/s},\\
\rho&=0.31\times1.225=0.37975\ \text{kg/m}^3,\\
C_L&=\frac{2(W/S)}{\rho V^2}=\frac{2\times5414}{0.37975\times245.45^2}=0.47327,\\
C_D&=0.016+0.043(0.47327)^2=0.025631,\qquad\frac LD=18.4645 .
\end{aligned}
$$

The SFC in s⁻¹ is $c_t=1.5/3600=4.1667\times10^{-4}$, so $V/c_t=589\,091$ m and

$$
R=589\,091\times18.4645\times0.15551=1\,691\,475\ \text{m}\approx\mathbf{1691\ km}.
$$

Spreadsheet note: the sheet's inputs are $b=83.3$ m, $AR=8.8$, $M=0.87$, $T=228$ K, $\sigma=0.34$, $W/S=5333$ N/m², SFC 1.1 N/(N h), fuel 630 911 N and $C_{D0}=0.017$; with those it gives 2263 km by the same method.

## Question 16

An aircraft with span 30.5 m, aspect ratio 9.1 and wing loading 5808 N/m² cruises at $M=0.81$ in the lower stratosphere, where $T=216.74$ K and $\rho=0.3724$ kg/m³. It carries 21 505 kg of fuel for the cruise and $C_D=0.016+0.044C_L^2$. Assuming $\frac{V}{s}\frac{L}{D}$ is constant, find the specific fuel consumption (N s⁻¹ N⁻¹) needed to cruise 3899 nautical miles.

Constant $\frac{V}{s}\frac{L}{D}$ is the Breguet assumption, so rearranging the range equation for the SFC:

$$
s=\frac{V}{R}\frac{L}{D}\ln\frac{W_1}{W_2}.
$$

Weights, with the fuel converted to newtons and subtracted from the start-of-cruise weight:

$$
\begin{aligned}
S&=\frac{30.5^2}{9.1}=102.225\ \text{m}^2,\qquad W_1=5808\times102.225=593\,724\ \text{N},\\
W_f&=21\,505\times9.81=210\,964\ \text{N},\qquad W_2=382\,760\ \text{N},\qquad\ln\frac{W_1}{W_2}=0.43901 .
\end{aligned}
$$

Speed and coefficients:

$$
\begin{aligned}
a&=\sqrt{1.4\times287\times216.74}=295.10\ \text{m/s},\qquad V=0.81\times295.10=239.03\ \text{m/s},\\
C_L&=\frac{2\times5808}{0.3724\times239.03^2}=0.54592,\qquad C_D=0.016+0.044(0.54592)^2=0.029113,\qquad\frac LD=18.7516 .
\end{aligned}
$$

The range is $R=3899\times1852=7\,220\,948$ m, so

$$
s=\frac{239.03\times18.7516\times0.43901}{7\,220\,948}=\mathbf{2.725\times10^{-4}\ \text{N s}^{-1}\text{N}^{-1}},
$$

which is 0.981 N of fuel per hour per newton of thrust. To three decimal places in the requested unit this would read 0.000, so give it in standard form.

Spreadsheet note: the sheet uses $b=36.3$ m, $AR=8.7$, $W/S=5560$ N/m², $T=218.11$ K, $\rho=0.3689$ kg/m³, 18 190 kg of fuel, $K=0.038$, 3898 nm and 1853 m per nautical mile, and gets $1.567\times10^{-4}$. Its own comment records the trap: the weight from the wing loading already contains the fuel, so $W_2=W_1-W_f$; adding the fuel to $W_1$ instead would give $1.887\times10^{-4}$ here.

## Question 20

A subsonic aircraft flies from London to San Francisco, 4894 nautical miles, at a cruise Mach number of 0.84. The temperature at cruise altitude is $-37$ °C in summer and $-72$ °C in winter. Find the difference in flight times in minutes, to one decimal place.

At a fixed Mach number the true airspeed is $V=Ma=M\sqrt{\gamma RT}$, so colder air means a lower speed of sound and a slower flight. Wind is ignored.

$$
\begin{aligned}
d&=4894\times1852=9\,063\,688\ \text{m},\\
\text{summer: } T&=236.15\ \text{K},\quad a=308.03\ \text{m/s},\quad V=258.75\ \text{m/s},\quad t=\frac{d}{V}=35\,029\ \text{s}=583.82\ \text{min},\\
\text{winter: } T&=201.15\ \text{K},\quad a=284.29\ \text{m/s},\quad V=238.81\ \text{m/s},\quad t=37\,954\ \text{s}=632.57\ \text{min}.
\end{aligned}
$$

$$
\Delta t=632.57-583.82=\mathbf{48.8\ min},
$$

with the winter flight the longer. As a check, $t\propto T^{-1/2}$, so $t_w/t_s=\sqrt{236.15/201.15}=1.0835$ and $583.82\times0.0835=48.8$ min.

Spreadsheet note: the sheet uses 4604 nm, $M=0.87$, $-34$ °C and $-61$ °C, and 1.853 km per nautical mile, giving 32.5 min.

## Question 27

Find the minimum weight of fuel for a propeller aircraft weighing 8697 N dry to fly 969 nautical miles. The propeller and transmission efficiency is 83.74 %, the SFC is 2.77 N/(kW h) and $C_D=0.028+0.070C_L^2$. Answer to the nearest newton.

The minimum fuel for a given distance is the maximum distance for that fuel, which for a propeller aircraft is at $(L/D)_{max}$ ([[SESA1015 M07 - Propeller Aircraft Range and Endurance#2. Range of a propeller aircraft|M07 §2]]):

$$
C_L=\sqrt{\frac{0.028}{0.070}}=0.63246,\qquad C_D=2(0.028)=0.056,\qquad\left(\frac LD\right)_{max}=\frac{1}{2\sqrt{0.070\times0.028}}=11.2938 .
$$

Units: $c_p=2.77/(1000\times3600)=7.6944\times10^{-7}$ N s⁻¹ W⁻¹, and $R=969\times1852=1\,794\,588$ m. The Breguet range equation for propeller aircraft, $R=\frac{\eta}{c_p}\frac{L}{D}\ln\frac{W_1}{W_2}$, rearranges to

$$
\begin{aligned}
\ln\frac{W_1}{W_2}&=\frac{Rc_p}{\eta\,(L/D)}=\frac{1\,794\,588\times7.6944\times10^{-7}}{0.8374\times11.2938}=0.146005,\\
W_1&=8697\,e^{0.146005}=10\,064.2\ \text{N},\\
W_f&=W_1-W_2=\mathbf{1367\ N}.
\end{aligned}
$$

That is 139 kg of fuel, 15.7 % of the dry weight. The same problem with different numbers (8000 N, 1112 km, 85 %, 2.7 N/(kW h), $C_D=0.025+0.07C_L^2$) gives 684 N ([[SESA1015 M07 - Propeller Aircraft Range and Endurance#Minimum fuel for a 1112 km flight|M07 worked example]]).

Spreadsheet note: the sheet uses 8101 N, 549 nm (1.853 km each), 82.73 %, 2.71 N/(kW h) and $C_D=0.025+0.075C_L^2$, giving 676 N. Using 1853 m per nautical mile with the question's numbers would give 1368 N.

## Question 29

Find the range of an aircraft cruising at a constant altitude of 35 000 ft, with start-of-cruise mass $251\times10^3$ kg, end-of-cruise mass $146\times10^3$ kg, Mach number at the start of cruise 0.48, total SFC $s=1.0\times10^{-4}$ N s⁻¹ N⁻¹, span 50.9 m, aspect ratio 9.0, $\sigma=0.309$, $\theta=0.759$ and $C_D=0.017+0.032C_L^2$. Answer in km to the nearest km.

The cruise is at constant altitude, and the Mach number is given only at the start, so the speed falls as the aircraft lightens at constant angle of attack. This is the constant-altitude, constant-$C_L$ pattern ([[SESA1015 M06 - Jet Aircraft Range and Endurance#7. Range at constant altitude|M06 §7]]):

$$
R=\frac{2}{s}\sqrt{\frac{2}{\rho S}}\,\frac{C_L^{1/2}}{C_D}\left(\sqrt{W_1}-\sqrt{W_2}\right).
$$

The workbook's own formula cell uses this expression.

Geometry, weights and atmosphere ($\sigma=0.309$ and $\theta=0.759$ are the ISA values at 35 000 ft):

$$
\begin{aligned}
S&=\frac{50.9^2}{9.0}=287.868\ \text{m}^2,\qquad W_1=251\,000\times9.81=2\,462\,310\ \text{N},\qquad W_2=146\,000\times9.81=1\,432\,260\ \text{N},\\
T&=0.759\times288.15=218.71\ \text{K},\qquad a=296.44\ \text{m/s},\qquad V_1=0.48\times296.44=142.29\ \text{m/s},\\
\rho&=0.309\times1.225=0.378525\ \text{kg/m}^3 .
\end{aligned}
$$

The lift coefficient at the start of cruise, which is held for the whole cruise:

$$
\begin{aligned}
C_L&=\frac{2W_1}{\rho V_1^2S}=\frac{2\times2\,462\,310}{0.378525\times142.29^2\times287.868}=2.2322,\\
C_D&=0.017+0.032(2.2322)^2=0.17645 .
\end{aligned}
$$

Substituting, with $\sqrt{2/(\rho S)}=0.135479$, $\sqrt{W_1}=1569.17$ and $\sqrt{W_2}=1196.77$:

$$
R=\frac{2}{1.0\times10^{-4}}\times0.135479\times\frac{\sqrt{2.2322}}{0.17645}\times(1569.17-1196.77)=8\,544\,159\ \text{m}\approx\mathbf{8544\ km}.
$$

The speed falls to $V_2=142.29\sqrt{146/251}=108.5$ m/s ($M=0.37$) by the end.

> [!warning] Not the log formula
> Holding the start-of-cruise $V$ and $L/D=12.65$ in the Breguet form gives $\frac{V_1}{s}\frac LD\ln\frac{W_1}{W_2}=9754$ km, which is the range of a cruise-climb, not of a constant-altitude cruise; the factor between the two is $2(1-\sqrt{W_2/W_1})/\ln(W_1/W_2)=0.876$. The data are also physically odd: a 251 t aircraft at $M=0.48$ at 35 000 ft needs $C_L=2.23$, beyond a clean wing's $C_{L,max}$, so the numbers exercise the formula rather than describe a real cruise.

Spreadsheet note: the sheet uses 239 t and 189 t, $M=0.5$, $s=1.9\times10^{-4}$, $b=62.1$ m, $AR=9.1$ and $C_D=0.016+0.041C_L^2$, giving 2595 km with the same constant-altitude formula.

## Related

- Topics: [[SESA1015 M06 - Jet Aircraft Range and Endurance]] · [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] · [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]
- Concepts: [[Breguet Range Equation]] · [[Cruise-Climb]] · [[Power Specific Fuel Consumption]] · [[Thrust Specific Fuel Consumption]]
- Index: [[SESA1015 Revision Workbook Coverage]]
