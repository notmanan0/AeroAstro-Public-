---
title: "SESA3029 W09f - Heat Exchangers"
module: "SESA3029 Aerothermodynamics"
type: topic
stream: "Block 5: Heat transfer"
order: 15
tags: [sesa3029, heat-transfer, heat-exchanger, lmtd, effectiveness, ntu, overall-heat-transfer-coefficient]
aliases: ["SESA3029 Lecture 5.8", "SESA3029 Lecture 5.9", "SESA3029 Lecture 5.10", "SESA3029 W09f"]
date: 2026-11-17
status: written-ahead
coverage: "Lectures 5.8 (types of heat exchangers, LMTD method), 5.9 (number of heat transfer units) and 5.10 (heat exchanger examples), all slides; written ahead from the decks, no transcripts yet"
parent: ["[[SESA3029 Aerothermodynamics Hub]]"]
prerequisites: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]", "[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]", "[[SESA3029 W09e - Numerical Methods in Conduction]]"]
next_topics: []
key_concepts: ["[[Overall Heat Transfer Coefficient]]", "[[Types of Heat Exchangers]]", "[[Heat Capacity Rate]]", "[[Log Mean Temperature Difference]]", "[[Heat Exchanger Effectiveness and NTU]]"]
tutorial_sheets: ["[[SESA3029 Example Sheet 3 - Solutions]]"]
sources: ["02 - Sources/Lectures/Lecture5.8(1).pdf", "02 - Sources/Lectures/Lecture5.9(1).pdf", "02 - Sources/Lectures/Lecture5.10.pdf"]
---

# SESA3029 W09f - Heat Exchangers

> [!abstract] Summary
> A heat exchanger passes heat from a hot fluid to a cold one through a wall, without mixing them. The two convective films and the wall are thermal resistances in series, which combine into one overall heat transfer coefficient $U$, and the rate is $\dot Q=UA_s\Delta T_{\rm lm}$, where the log mean temperature difference $\Delta T_{\rm lm}=(\Delta T_1-\Delta T_2)/\ln(\Delta T_1/\Delta T_2)$ follows from an energy balance on an element of the exchanger, for parallel and counter flow alike. When only the inlet temperatures are known, the effectiveness $\epsilon=\dot Q/\dot Q_{\max}$ is found from the number of heat transfer units $\mathrm{NTU}=UA_s/C_{\min}$ and the capacity ratio $c=C_{\min}/C_{\max}$, and for the same NTU and $c$ a counter-flow exchanger always transfers at least as much heat as a parallel-flow one.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives two fluid streams separated by a wall (a concentric tube, a shell-and-tube condenser, a cooler) and asks for a heat rate, an outlet temperature, a surface area or a tube length.
> - **Assumptions:** steady flow; constant mass flow rates, $c_p$ and $U$; outer surface insulated; axial conduction along the tube negligible; thin wall ($R_{\rm wall}\approx0$, $A_i\approx A_o=A_s$) unless the wall is given; no phase change except where a stream condenses or boils at constant temperature ($C\to\infty$, $c=0$).
> - **Method:** 1. $C_h=\dot m_hc_{ph}$, $C_c=\dot m_cc_{pc}$, and $1/U=1/h_i+1/h_o$ (find each $h$ from a Nusselt correlation, with Re deciding laminar or turbulent). 2. If both outlet temperatures are known or follow from $\dot Q=C_h\Delta T_h=C_c\Delta T_c$, use LMTD: $\Delta T_1$, $\Delta T_2$ at the two ends, then $A_s=\dot Q/(U\Delta T_{\rm lm})$. 3. If only the inlets are known, use NTU: $c$, $\mathrm{NTU}=UA_s/C_{\min}$, $\epsilon$ from the formula for the arrangement, $\dot Q=\epsilon C_{\min}(T_{h,\rm in}-T_{c,\rm in})$. 4. Outlet temperatures from $\dot Q/C_h$ and $\dot Q/C_c$. 5. Convert area to length: $A_s=N\pi DL$, and divide by the number of passes.
> - **Common mistakes:** pairing the wrong end temperatures in counter flow ($\Delta T_1=T_{h,\rm in}-T_{c,\rm out}$, not $T_{h,\rm in}-T_{c,\rm in}$); using $C_{\max}$ in $\dot Q_{\max}$, which gives an effectiveness that can exceed 1.
> - **Practise:** [[#Worked example: counter-flow area by the LMTD method|the LMTD sizing example]] · [[SESA3029 Example Sheet 3 - Solutions#Q5. Parallel-flow heat exchanger|ES3 Q5]]

Heat exchangers are everywhere that heat has to move between two fluids that must not touch. In a gas-cooled nuclear reactor the radioactive gas that cools the core heats water into steam for the turbines through a heat exchanger, so the steam never meets the gas. Rocket engines recuperate heat from the combustion chamber to warm the propellant, and Falcon 9 warms the helium that pressurises its tanks in a heat exchanger. The same device sits in every aircraft as a fuel–oil cooler or an environmental-control precooler.

The physics is the combination of the two earlier parts of the block. Heat crosses from the hot fluid to the wall by convection, through the wall by conduction, and from the wall into the cold fluid by convection again ([[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]] and [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]]). What is new is that the fluids change temperature as they flow, so the driving difference $T_h-T_c$ is not one number but varies along the exchanger. In parallel flow it is large at the inlet and shrinks exponentially towards the outlet. Averaging it correctly gives the logarithmic mean; asking how close the exchanger comes to the best possible performance gives the effectiveness. Both views rest on the same energy balance on a slice of the exchanger.

Heat exchangers can be run for long periods without any change in operating conditions, so they are treated as steady-flow devices: the mass flow rates and the inlet and outlet temperatures do not change with time.

## 1. The overall heat transfer coefficient

Take a concentric tube with the hot fluid inside at temperature $T_i$ and the cold fluid outside at $T_o$, so that $h_i$ and $A_i$ belong to the inner (hot) surface and $h_o$, $A_o$ to the outer (cold) one. Radiation between the fluids and the wall is usually lumped into the heat transfer coefficients. The same heat flow $\dot Q$ passes through three resistances in series:

$$
R_i=\frac{1}{h_iA_i},\qquad R_{\rm wall}=\frac{\ln(r_o/r_i)}{2\pi kL},\qquad R_o=\frac{1}{h_oA_o}.
$$

Resistances in series add, so

$$
R_{\rm th}=R_i+R_{\rm wall}+R_o=\frac{1}{h_iA_i}+\frac{\ln(r_o/r_i)}{2\pi kL}+\frac{1}{h_oA_o},
\qquad
\dot Q=\frac{\Delta T}{R_{\rm th}},\quad \Delta T=T_i-T_o .
$$

![[at_w09f_resistance_network.png|900]]

The **overall heat transfer coefficient** $U$ packs the whole chain into a single Newton's-law form, $\dot Q=UA\,\Delta T$:

$$
\dot Q=\frac{\Delta T}{R_{\rm th}}=UA_s\Delta T=U_iA_i\Delta T=U_oA_o\Delta T
\quad\Rightarrow\quad
\frac{1}{UA_s}=\frac{1}{U_iA_i}=\frac{1}{U_oA_o}=R_{\rm th}.
$$

$U$ on its own is ambiguous until an area is named: $U_i$ goes with the inner area and $U_o$ with the outer, and only the product $UA$ is unique. Multiplying $R_{\rm th}$ by the inner area $A_i=2\pi r_iL$ gives the inner-surface value with a wall of finite thickness:

$$
\frac{1}{U_i}=A_iR_{\rm th}=\frac{1}{h_i}+\frac{2\pi r_iL\ln(r_o/r_i)}{2\pi kL}+\frac{2\pi r_iL}{h_o\,2\pi r_oL}
$$

$$
\Rightarrow\quad
\frac{1}{U_i}=\frac{1}{h_i}+\frac{r_i\ln(r_o/r_i)}{k}+\frac{r_i}{r_o}\frac{1}{h_o}.
$$

The tube wall is normally thin and made of a high-conductivity metal, so its resistance is negligible, $R_{\rm wall}\approx0$, and the inner and outer areas are almost equal, $A_i\approx A_o=A_s$. Then

$$
\frac{1}{UA_s}\approx\frac{1}{h_iA_s}+\frac{1}{h_oA_s}
\quad\Rightarrow\quad
\boxed{\frac{1}{U}\approx\frac{1}{h_i}+\frac{1}{h_o}}\qquad(\text{thin wall},\ A_i\approx A_o=A_s).
$$

$U$ is always smaller than the smaller of $h_i$ and $h_o$, and when the two differ greatly the smaller one controls it. In the concentric-tube oil–water exchanger of §7, $h=2250$ W m⁻² K⁻¹ on the water side and $38.9$ W m⁻² K⁻¹ on the oil side give $U=38.25$ W m⁻² K⁻¹: improving the water side would gain almost nothing, while doubling the oil-side coefficient would nearly double $U$. This is why gas- and oil-side surfaces carry fins (see [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]]).

## 2. Types of heat exchangers

The simplest exchanger is the concentric tube (double pipe): one fluid in the inner tube, the other in the annulus around it. Its two arrangements differ only in the direction of the outer flow.

- **Parallel flow:** both fluids enter at the same end and move in the same direction. The temperature difference is largest at the inlet and decays towards the outlet, and the cold outlet can never rise above the hot outlet.
- **Counter flow:** the fluids enter at opposite ends and move in opposite directions. The hot inlet faces the cold outlet, the temperature difference stays more uniform along the tube, and the cold outlet can exceed the hot outlet.

![[at_w09f_flow_arrangements.png|900]]

The temperature curves in the figure are the parallel- and counter-flow solutions of §4 for the same $U$, area and capacity rates, those of the sizing and rating examples of §§4–5. With identical hardware the counter-flow arrangement transfers 120.0 kW against 108.8 kW in parallel flow.

In a **crossflow** exchanger the two fluids move perpendicular to one another, typically a gas flowing across a bank of tubes that carry a liquid. Plate fins between the tubes make the cross-flow fluid **unmixed**: it can move only along the interfin spacing and cannot move in the transverse direction, so each streamline keeps its own temperature history. Without fins the cross-flow fluid is **mixed**, free to move transversely and even out its temperature, and mixing can have a significant effect on the heat transfer. The tube fluid is unmixed in both cases, since each tube confines its own stream.

A **shell-and-tube** exchanger packs a large number of tubes into a shell. Baffles in the shell force the shell-side fluid across the tube bank in a zig-zag, which raises its heat transfer coefficient, and multi-pass arrangements (the tube fluid crossing the shell two or more times) improve the heat transfer further. Shell-and-tube exchangers are generally heavy and are not preferred for aerospace applications; their home is the power-station condenser of [[#Worked example: shell-and-tube condenser|§7]].

![[at_w09f_crossflow_shell_tube.png|900]]

## 3. Energy balance and the heat capacity rate

The analysis of every arrangement rests on four modelling assumptions:

- steady flow, so the mass flow rates and the inlet and outlet temperatures are constant;
- axial heat conduction along the tube is insignificant compared with the heat carried by the fluids;
- the outer surface of the exchanger is perfectly insulated, so no heat is lost to the surroundings;
- (implicit in what follows) constant specific heats, no change of phase except at constant temperature, and negligible changes of kinetic and potential energy.

Apply the steady-flow energy equation ([[Steady-flow Energy Equation]]) to each stream with no shaft work. The heat leaving the hot stream and the heat entering the cold one are

$$
\dot Q_h=\dot m_hc_{ph}\left(T_{h,\rm in}-T_{h,\rm out}\right),\qquad T_{h,\rm in}>T_{h,\rm out},
$$

$$
\dot Q_c=\dot m_cc_{pc}\left(T_{c,\rm out}-T_{c,\rm in}\right),\qquad T_{c,\rm out}>T_{c,\rm in}.
$$

With the outer surface insulated, everything the hot fluid rejects is gained by the cold one, and the first law gives

$$
\dot Q_h=\dot Q_c=\dot Q .
$$

The product of mass flow rate and specific heat appears so often that it gets its own name, the **heat capacity rate**,

$$
C_h=\dot m_hc_{ph},\qquad C_c=\dot m_cc_{pc}\qquad(\text{W K}^{-1}),
$$

so that $\dot Q=C_h(T_{h,\rm in}-T_{h,\rm out})=C_c(T_{c,\rm out}-T_{c,\rm in})$. $C$ is the rate of heat transfer needed to change the temperature of the stream by 1 °C. Dividing the two forms of $\dot Q$,

$$
\frac{T_{h,\rm in}-T_{h,\rm out}}{T_{c,\rm out}-T_{c,\rm in}}=\frac{C_c}{C_h},
$$

so the stream with the larger heat capacity rate has the smaller temperature change, and the one with the smaller $C$ the larger. In the sizing example of §4, $C_h=3000$ and $C_c=1500$ W K⁻¹: the hot stream falls by 40 K and the cold one rises by 80 K. A stream that condenses or boils at constant pressure absorbs or releases heat with no temperature change at all, which is the limit $C\to\infty$ ([[Heat Capacity Rate]]).

The two methods of §§4–5 come from the same differential energy balance, rearranged for different unknowns. LMTD suits sizing, where the temperatures are known and the area is wanted; $\epsilon$–NTU suits rating, where the hardware is known and the outlet temperatures are wanted:

| Method | Use it for | Given | Unknown | Core equation |
|---|---|---|---|---|
| LMTD (§4) | Sizing (find $A_s$ or tube length $L$) | Duty $\dot Q$ and all four terminal temperatures (two given, two from the energy balance) | $A_s$ (or $L$) | $\dot Q = U A_s \Delta T_{\rm lm}$ |
| $\epsilon$–NTU (§5) | Rating (predict the performance of an existing unit) | Hardware $UA_s$, flow rates and both inlet temperatures | $\dot Q$ and both outlet temperatures | $\dot Q = \epsilon(\mathrm{NTU}, c)\,C_{\min}(T_{h,\rm in}-T_{c,\rm in})$ |

§6 collects the inverted NTU relations (for sizing with NTU) and the exam convention for multi-pass shell-and-tube units.

## 4. The log mean temperature difference method

The LMTD method is used to select a heat exchanger that will achieve a specified temperature range in a fluid stream of known mass flow rate. By analogy with Newton's law of cooling, the rate is written

$$
\dot Q=UA_s\Delta T_m ,
$$

where $\Delta T_m$ is a suitable mean temperature difference between the two fluids. The local difference $T_h-T_c$ varies along the exchanger: in parallel flow it is large at the inlet and decreases exponentially towards the outlet. A plain arithmetic average overweights the large end. The correct mean comes out of an energy balance on a differential section of the exchanger and turns out to be logarithmic.

Measure position along the exchanger by the heat-transfer area $A_s$ swept from end 1 (where the hot fluid enters) to end 2. Over an element $\mathrm dA_s$ the local heat flow is

$$
\delta\dot Q=U(T_h-T_c)\,\mathrm dA_s .
$$

This assumes $U$ is the same all along the exchanger, which in turn needs the fluid properties, and hence $h_i$ and $h_o$, to be roughly constant; the properties are evaluated at the mean temperature of each stream.

### 4.1 Parallel flow

Integrating the element balance across a parallel-flow exchanger gives $\dot Q=UA_s\Delta T_{\rm lm}$ with end differences $\Delta T_1=T_{h,\rm in}-T_{c,\rm in}$ and $\Delta T_2=T_{h,\rm out}-T_{c,\rm out}$. Both fluids move from end 1 to end 2. Over the element the hot fluid loses heat, so its temperature falls ($\mathrm dT_h<0$), and the cold fluid gains it ($\mathrm dT_c>0$):

$$
\delta\dot Q=-\dot m_hc_{ph}\,\mathrm dT_h
\quad\Rightarrow\quad
\mathrm dT_h=-\frac{\delta\dot Q}{\dot m_hc_{ph}},
$$

$$
\delta\dot Q=\dot m_cc_{pc}\,\mathrm dT_c
\quad\Rightarrow\quad
\mathrm dT_c=\frac{\delta\dot Q}{\dot m_cc_{pc}}.
$$

Subtract the second from the first:

$$
\mathrm dT_h-\mathrm dT_c=\mathrm d(T_h-T_c)=-\delta\dot Q\left(\frac{1}{\dot m_hc_{ph}}+\frac{1}{\dot m_cc_{pc}}\right).
$$

Substitute $\delta\dot Q=U(T_h-T_c)\,\mathrm dA_s$:

$$
\mathrm d(T_h-T_c)=-U(T_h-T_c)\,\mathrm dA_s\left(\frac{1}{\dot m_hc_{ph}}+\frac{1}{\dot m_cc_{pc}}\right).
$$

Separate the variables:

$$
\frac{\mathrm d(T_h-T_c)}{T_h-T_c}=-U\,\mathrm dA_s\left(\frac{1}{\dot m_hc_{ph}}+\frac{1}{\dot m_cc_{pc}}\right).
$$

Integrate from end 1 to end 2, with $U$ and the bracket constant:

$$
\int_1^2\frac{\mathrm d(T_h-T_c)}{T_h-T_c}=-U\left(\frac{1}{\dot m_hc_{ph}}+\frac{1}{\dot m_cc_{pc}}\right)\int_1^2\mathrm dA_s
$$

$$
\Rightarrow\quad
\ln\frac{T_{h,\rm out}-T_{c,\rm out}}{T_{h,\rm in}-T_{c,\rm in}}=-UA_s\left(\frac{1}{\dot m_hc_{ph}}+\frac{1}{\dot m_cc_{pc}}\right).
\tag{4.1}
$$

The bracket still contains the capacity rates. Eliminate them with the overall energy balance. Since $\dot m_cc_{pc}(T_{c,\rm out}-T_{c,\rm in})=\dot m_hc_{ph}(T_{h,\rm in}-T_{h,\rm out})$,

$$
\dot m_cc_{pc}=\dot m_hc_{ph}\,\frac{T_{h,\rm in}-T_{h,\rm out}}{T_{c,\rm out}-T_{c,\rm in}}
\quad\Rightarrow\quad
\frac{1}{\dot m_cc_{pc}}=\frac{T_{c,\rm out}-T_{c,\rm in}}{\dot m_hc_{ph}\left(T_{h,\rm in}-T_{h,\rm out}\right)}.
$$

Put this into (4.1) and take $1/(\dot m_hc_{ph})$ outside:

$$
\ln\frac{T_{h,\rm out}-T_{c,\rm out}}{T_{h,\rm in}-T_{c,\rm in}}=-\frac{UA_s}{\dot m_hc_{ph}}\left(\frac{T_{c,\rm out}-T_{c,\rm in}}{T_{h,\rm in}-T_{h,\rm out}}+1\right)
=-\frac{UA_s}{\dot m_hc_{ph}}\,\frac{\left(T_{c,\rm out}-T_{c,\rm in}\right)+\left(T_{h,\rm in}-T_{h,\rm out}\right)}{T_{h,\rm in}-T_{h,\rm out}}.
$$

Define the temperature differences at the two ends,

$$
\Delta T_1=T_{h,\rm in}-T_{c,\rm in},\qquad \Delta T_2=T_{h,\rm out}-T_{c,\rm out}\qquad(\text{parallel flow}),
$$

and regroup the numerator:

$$
\left(T_{c,\rm out}-T_{c,\rm in}\right)+\left(T_{h,\rm in}-T_{h,\rm out}\right)=\left(T_{h,\rm in}-T_{c,\rm in}\right)-\left(T_{h,\rm out}-T_{c,\rm out}\right)=\Delta T_1-\Delta T_2 .
$$

So

$$
\ln\frac{\Delta T_2}{\Delta T_1}=-\frac{UA_s}{\dot m_hc_{ph}}\,\frac{\Delta T_1-\Delta T_2}{T_{h,\rm in}-T_{h,\rm out}}.
$$

The denominator $\dot m_hc_{ph}(T_{h,\rm in}-T_{h,\rm out})$ is $\dot Q$. Multiply both sides by $-\dot Q$ and use $\ln(\Delta T_2/\Delta T_1)=-\ln(\Delta T_1/\Delta T_2)$:

$$
\dot Q\ln\frac{\Delta T_1}{\Delta T_2}=UA_s\left(\Delta T_1-\Delta T_2\right)
\quad\Rightarrow\quad
\boxed{\dot Q=UA_s\Delta T_{\rm lm},\qquad \Delta T_{\rm lm}=\frac{\Delta T_1-\Delta T_2}{\ln(\Delta T_1/\Delta T_2)}}
$$

$\Delta T_{\rm lm}$ is the **log mean temperature difference**. Equation (4.1) also says what the profiles look like: $T_h-T_c$ decays exponentially with $A_s$, with decay rate $U(1/C_h+1/C_c)$.

### 4.2 Counter flow

Counter flow yields the **same** LMTD formula, $\dot Q=UA_s\Delta T_{\rm lm}$, with the end differences paired at each physical end: $\Delta T_1=T_{h,\rm in}-T_{c,\rm out}$ and $\Delta T_2=T_{h,\rm out}-T_{c,\rm in}$. Keep end 1 at the hot inlet and $A_s$ increasing towards end 2, the hot outlet. The cold fluid now enters at end 2 and flows back towards end 1, so the cold inlet is at end 2 and the cold outlet at end 1. Following $A_s$ from 1 to 2 the cold temperature therefore decreases, even though the cold fluid is being heated in its own direction of motion. The hot side is unchanged, but the cold-side balance changes sign:

$$
\delta\dot Q=-\dot m_hc_{ph}\,\mathrm dT_h
\quad\Rightarrow\quad
\mathrm dT_h=-\frac{\delta\dot Q}{\dot m_hc_{ph}},
$$

$$
\delta\dot Q=-\dot m_cc_{pc}\,\mathrm dT_c
\quad\Rightarrow\quad
\mathrm dT_c=-\frac{\delta\dot Q}{\dot m_cc_{pc}}.
$$

Subtract:

$$
\mathrm d(T_h-T_c)=-\delta\dot Q\left(\frac{1}{\dot m_hc_{ph}}-\frac{1}{\dot m_cc_{pc}}\right)=-U(T_h-T_c)\,\mathrm dA_s\left(\frac{1}{\dot m_hc_{ph}}-\frac{1}{\dot m_cc_{pc}}\right).
$$

Separate and integrate from 1 to 2. At end 1, $T_h-T_c=T_{h,\rm in}-T_{c,\rm out}$; at end 2, $T_h-T_c=T_{h,\rm out}-T_{c,\rm in}$:

$$
\ln\frac{T_{h,\rm out}-T_{c,\rm in}}{T_{h,\rm in}-T_{c,\rm out}}=-UA_s\left(\frac{1}{\dot m_hc_{ph}}-\frac{1}{\dot m_cc_{pc}}\right).
\tag{4.2}
$$

Use the same substitution for $1/(\dot m_cc_{pc})$ as before:

$$
\ln\frac{T_{h,\rm out}-T_{c,\rm in}}{T_{h,\rm in}-T_{c,\rm out}}=-\frac{UA_s}{\dot m_hc_{ph}}\left(1-\frac{T_{c,\rm out}-T_{c,\rm in}}{T_{h,\rm in}-T_{h,\rm out}}\right)
=-\frac{UA_s}{\dot m_hc_{ph}}\,\frac{\left(T_{h,\rm in}-T_{h,\rm out}\right)-\left(T_{c,\rm out}-T_{c,\rm in}\right)}{T_{h,\rm in}-T_{h,\rm out}}.
$$

The end differences for counter flow are

$$
\Delta T_1=T_{h,\rm in}-T_{c,\rm out},\qquad \Delta T_2=T_{h,\rm out}-T_{c,\rm in}\qquad(\text{counter flow}),
$$

and the numerator regroups to the same combination:

$$
\left(T_{h,\rm in}-T_{h,\rm out}\right)-\left(T_{c,\rm out}-T_{c,\rm in}\right)=\left(T_{h,\rm in}-T_{c,\rm out}\right)-\left(T_{h,\rm out}-T_{c,\rm in}\right)=\Delta T_1-\Delta T_2 .
$$

Hence

$$
\ln\frac{\Delta T_2}{\Delta T_1}=-\frac{UA_s}{\dot m_hc_{ph}}\,\frac{\Delta T_1-\Delta T_2}{T_{h,\rm in}-T_{h,\rm out}}=-\frac{UA_s\left(\Delta T_1-\Delta T_2\right)}{\dot Q}
\quad\Rightarrow\quad
\boxed{\dot Q=UA_s\Delta T_{\rm lm},\qquad \Delta T_{\rm lm}=\frac{\Delta T_1-\Delta T_2}{\ln(\Delta T_1/\Delta T_2)}}
$$

This is the same formula as for parallel flow. Only the definitions of $\Delta T_1$ and $\Delta T_2$ differ: in both arrangements they are the hot-minus-cold differences at the two physical ends of the exchanger, and in counter flow the hot inlet sits opposite the cold outlet.

> [!warning] Pair the temperatures at each end
> In counter flow $\Delta T_1=T_{h,\rm in}-T_{c,\rm out}$ and $\Delta T_2=T_{h,\rm out}-T_{c,\rm in}$. Writing $T_{h,\rm in}-T_{c,\rm in}$ out of habit from parallel flow is the most common slip. A quick check is to sketch the $T$–$A_s$ diagram and read off the vertical gap at each end. In counter flow $\Delta T_2$ may be larger than $\Delta T_1$ (95 K against 55 K in the sizing example below); the formula does not care, because it is symmetric.

### 4.3 Properties of the LMTD

The formula is symmetric in the two end differences: swapping them changes the sign of both numerator and denominator,

$$
\frac{\Delta T_2-\Delta T_1}{\ln(\Delta T_2/\Delta T_1)}=\frac{-(\Delta T_1-\Delta T_2)}{-\ln(\Delta T_1/\Delta T_2)}=\frac{\Delta T_1-\Delta T_2}{\ln(\Delta T_1/\Delta T_2)},
$$

so it does not matter which end is called 1.

When the end differences are equal it reads $0/0$, but the limit is finite. Write $\Delta T_2=\Delta T_1(1+\delta)$ with $\delta\to0$:

$$
\Delta T_{\rm lm}=\frac{-\delta\,\Delta T_1}{\ln\dfrac{1}{1+\delta}}=\frac{\delta\,\Delta T_1}{\ln(1+\delta)}=\frac{\delta\,\Delta T_1}{\delta-\tfrac12\delta^2+\dots}\ \to\ \Delta T_1 .
$$

So with $\Delta T_1=\Delta T_2=\Delta T$ the log mean is just $\Delta T$, which is the case of balanced counter flow ($C_h=C_c$, §5.5) and of a condensing stream exchanging heat with a stream at constant temperature. For end differences of 30 K and 31 K the LMTD is 30.497 K, against an arithmetic mean of 30.5 K.

![[at_w09f_lmtd_vs_mean.png|900]]

For unequal end differences the log mean always lies below the arithmetic mean $(\Delta T_1+\Delta T_2)/2$. The gap is small when the ends are similar (a ratio of 0.6 costs about 2 %) and large when one end pinches: for a ratio of 0.1 the log mean is 0.39 of the larger difference against an arithmetic 0.55. Using the arithmetic mean therefore overestimates $\dot Q$ for a given area and undersizes the exchanger; in the sizing example below it would give 9.82 m² instead of 10.06 m².

The comparison between the arrangements needs care with its conditions. For the **same inlet and outlet temperatures**, parallel flow has a larger $\Delta T_1$ and a much smaller $\Delta T_2$ than counter flow, and its log mean is smaller:

$$
\Delta T_{\rm lm,CF}>\Delta T_{\rm lm,PF}\qquad(\text{same four terminal temperatures, both streams changing temperature}).
$$

In the sizing example below, the four temperatures 150, 110, 15 and 95 °C give $\Delta T_{\rm lm}=73.19$ K in counter flow and 54.61 K in parallel flow, so parallel flow would need $A_s=13.48$ m² instead of 10.06 m², 34 % more surface for the same duty. A smaller surface area is sufficient to achieve a specified heat transfer rate with a counter-flow exchanger. The exception is a stream at constant temperature (a condenser or boiler): its inlet and outlet temperatures are equal, the two arrangements then have the same end differences and the same LMTD, and the flow direction does not matter. Some duties are also impossible in parallel flow, since there the cold outlet cannot exceed the hot outlet; counter flow has no such limit.

### Worked example: counter-flow area by the LMTD method

*Counter-flow heat exchanger. Cold side: $C_c=1500$ W K⁻¹, $h_c=275$ W m⁻² K⁻¹, $T_{c,\rm in}=15$ °C. Hot side: $C_h=3000$ W K⁻¹, $h_h=400$ W m⁻² K⁻¹, $T_{h,\rm in}=150$ °C. Find the area $A$ for which the hot outlet temperature is $T_{h,\rm out}=110$ °C.*

**1. Heat transfer rate**, from the hot stream, whose both temperatures are known:

$$
\dot Q=C_h\left(T_{h,\rm in}-T_{h,\rm out}\right)=3000\times(150-110)=120\,000\ \text{W}=120\ \text{kW}.
$$

**2. Cold outlet temperature**, from the cold stream's balance:

$$
T_{c,\rm out}=T_{c,\rm in}+\frac{\dot Q}{C_c}=15+\frac{120\,000}{1500}=15+80=95\ ^\circ\text{C}.
$$

**3. Overall heat transfer coefficient**, thin wall:

$$
\frac1U=\frac{1}{h_c}+\frac{1}{h_h}=\frac{1}{275}+\frac{1}{400}=3.6364\times10^{-3}+2.5000\times10^{-3}=6.1364\times10^{-3}
\quad\Rightarrow\quad
U=162.963\ \text{W m}^{-2}\,\text{K}^{-1}.
$$

**4. Log mean temperature difference**, with the counter-flow pairing:

$$
\Delta T_1=T_{h,\rm in}-T_{c,\rm out}=150-95=55\ \text{K},\qquad \Delta T_2=T_{h,\rm out}-T_{c,\rm in}=110-15=95\ \text{K},
$$

$$
\Delta T_{\rm lm}=\frac{\Delta T_2-\Delta T_1}{\ln(\Delta T_2/\Delta T_1)}=\frac{95-55}{\ln(95/55)}=\frac{40}{0.54654}=73.187\ \text{K}.
$$

**5. Area:**

$$
A=\frac{\dot Q}{U\Delta T_{\rm lm}}=\frac{120\,000}{162.963\times73.187}=\boxed{10.06\ \text{m}^2}.
$$

> [!check] The area fed back through the element balance
> Unrounded, $A=10.061$ m². Integrating the element equations numerically over $A_s=10.06$ m² with $T_{h,\rm in}=150$ °C and $T_{c,\rm in}=15$ °C returns $T_{h,\rm out}=110.00$ °C and $T_{c,\rm out}=94.99$ °C, so the LMTD formula and the differential balance agree.

## 5. Effectiveness and the number of heat transfer units

The LMTD method is useful in designing a heat exchanger when the inlet and outlet temperatures of the fluids are known (or follow from the energy balance). Often only the inlet temperatures are known: an existing exchanger of given area receives two streams, and the question is how much heat it will pass and at what temperatures the fluids will leave. LMTD then needs trial and error, because $\Delta T_{\rm lm}$ depends on the unknown outlets. The **effectiveness or number of heat transfer units method** answers the question directly: mass flow rates and inlet temperatures are usually known, and with them the heat transfer rate can be found without knowing the outlet temperatures.

### 5.1 Effectiveness and the maximum heat transfer rate

The **heat exchanger effectiveness** compares what the exchanger does with what any exchanger could do with the same two inlet streams:

$$
\epsilon=\frac{\dot Q}{\dot Q_{\max}}=\frac{\text{actual heat transfer rate}}{\text{maximum possible heat transfer rate}},
\qquad
\dot Q=C_c\left(T_{c,\rm out}-T_{c,\rm in}\right)=C_h\left(T_{h,\rm in}-T_{h,\rm out}\right).
$$

The largest temperature difference anywhere in the exchanger is between the two inlets,

$$
\Delta T_{\max}=T_{h,\rm in}-T_{c,\rm in}.
$$

No fluid can be heated above $T_{h,\rm in}$ or cooled below $T_{c,\rm in}$, so the most that either stream can change temperature is $\Delta T_{\max}$. Only the stream with the smaller heat capacity rate can actually achieve it, which fixes

$$
\boxed{\dot Q_{\max}=C_{\min}\left(T_{h,\rm in}-T_{c,\rm in}\right)},\qquad C_{\min}=\min\{C_c,C_h\}=\min\{\dot m_cc_{pc},\ \dot m_hc_{ph}\}.
$$

Using $C_{\max}$ instead would look like a larger heat rate, but it is not achievable. Suppose the $C_{\max}$ stream changed temperature by the full $\Delta T_{\max}$. The energy balance then demands that the other stream change by

$$
\Delta T_{\min\text{-stream}}=\frac{\dot Q}{C_{\min}}=\frac{C_{\max}\Delta T_{\max}}{C_{\min}}>\Delta T_{\max},
$$

which would take the $C_{\min}$ fluid beyond the limit set by the other fluid's inlet temperature: physically impossible. $C_{\min}$ belongs to the fluid that needs less energy per unit temperature change, so it is the one that can run through the whole available range. With $\dot Q_{\max}$ defined this way, $0\le\epsilon\le1$, and once $\epsilon$ is known

$$
\dot Q=\epsilon\dot Q_{\max}=\epsilon C_{\min}\left(T_{h,\rm in}-T_{c,\rm in}\right).
$$

### 5.2 Number of heat transfer units and capacity ratio

The effectiveness of a heat exchanger depends on its geometry and flow arrangement. The integrated balances (4.1) and (4.2) contain $U$, $A_s$, $C_h$ and $C_c$ only in two dimensionless groups. The first is the **number of heat transfer units**,

$$
\mathrm{NTU}=\frac{UA_s}{C_{\min}}=\frac{UA_s}{(\dot mc_p)_{\min}},
$$

which is proportional to $A_s$: for given $U$ and $C_{\min}$, NTU is a measure of the heat exchanger's surface area, and the larger the NTU, the larger the exchanger. The second is the **capacity ratio**,

$$
c=\frac{C_{\min}}{C_{\max}},\qquad 0\le c\le1 .
$$

Effectiveness is a function of the number of heat transfer units and the capacity ratio alone, $\epsilon=f(\mathrm{NTU},c)$, with a different function for each flow arrangement.

### 5.3 Parallel-flow effectiveness

Eliminating the outlet temperatures from (4.1) gives $\epsilon_{\text{parallel-flow}}=\{1-\exp[-\mathrm{NTU}(1+c)]\}/(1+c)$, whichever stream is $C_{\min}$. Start from the parallel-flow result (4.1), written with the capacity rates:

$$
\ln\frac{T_{h,\rm out}-T_{c,\rm out}}{T_{h,\rm in}-T_{c,\rm in}}=-UA_s\left(\frac{1}{C_h}+\frac{1}{C_c}\right).
$$

Write both outlet temperatures in terms of $\dot Q$ and the inlets:

$$
T_{h,\rm out}=T_{h,\rm in}-\frac{\dot Q}{C_h},\qquad T_{c,\rm out}=T_{c,\rm in}+\frac{\dot Q}{C_c}.
$$

The numerator of the logarithm becomes

$$
T_{h,\rm out}-T_{c,\rm out}=\left(T_{h,\rm in}-T_{c,\rm in}\right)-\dot Q\left(\frac{1}{C_h}+\frac{1}{C_c}\right).
$$

Put $\dot Q=\epsilon C_{\min}\left(T_{h,\rm in}-T_{c,\rm in}\right)$ and divide by $T_{h,\rm in}-T_{c,\rm in}$:

$$
\frac{T_{h,\rm out}-T_{c,\rm out}}{T_{h,\rm in}-T_{c,\rm in}}=1-\epsilon\left(\frac{C_{\min}}{C_h}+\frac{C_{\min}}{C_c}\right).
$$

Whichever stream is $C_{\min}$, one of the two ratios is 1 and the other is $c$, so the bracket is $1+c$. On the right-hand side, take $1/C_{\min}$ out of the bracket in the same way:

$$
-UA_s\left(\frac{1}{C_h}+\frac{1}{C_c}\right)=-\frac{UA_s}{C_{\min}}\left(\frac{C_{\min}}{C_h}+\frac{C_{\min}}{C_c}\right)=-\mathrm{NTU}(1+c).
$$

So

$$
\ln\left[1-(1+c)\,\epsilon\right]=-\mathrm{NTU}(1+c).
$$

Exponentiate and solve for $\epsilon$:

$$
1-(1+c)\,\epsilon=\exp\left[-\mathrm{NTU}(1+c)\right]
\quad\Rightarrow\quad
\boxed{\epsilon_{\text{parallel-flow}}=\frac{1-\exp\left[-\mathrm{NTU}(1+c)\right]}{1+c}}
$$

Taking $C_c$ as $C_{\min}$ and $C_h$ as $C_{\max}$ from the start writes the bracket as $1+C_c/C_h$ and the left side as $1-(1+C_c/C_h)\,\epsilon\,C_{\min}/C_c$, which is the same equation. The symmetric route above shows directly that the result is the same whichever fluid has the smaller heat capacity rate: there is no difference whether $C_{\min}$ belongs to the hot or the cold fluid.

### 5.4 Counter-flow effectiveness

Eliminating the outlet temperatures from (4.2) gives $\epsilon_{\text{counter-flow}}=\{1-\exp[-\mathrm{NTU}(1-c)]\}/\{1-c\exp[-\mathrm{NTU}(1-c)]\}$ for $c\neq1$ (with the $c=1$ limit $\mathrm{NTU}/(1+\mathrm{NTU})$ in §5.5). Start from the counter-flow result (4.2):

$$
\ln\frac{T_{h,\rm out}-T_{c,\rm in}}{T_{h,\rm in}-T_{c,\rm out}}=-UA_s\left(\frac{1}{C_h}-\frac{1}{C_c}\right).
$$

Here the two cases must be taken separately, because the bracket is a difference. Take first $C_c=C_{\min}$ and $C_h=C_{\max}$. The right-hand side is

$$
-\frac{UA_s}{C_c}\left(\frac{C_c}{C_h}-1\right)=-\frac{UA_s}{C_{\min}}\left(\frac{C_{\min}}{C_{\max}}-1\right)=-\mathrm{NTU}(c-1),
$$

so

$$
\frac{T_{h,\rm out}-T_{c,\rm in}}{T_{h,\rm in}-T_{c,\rm out}}=\exp\left[-\mathrm{NTU}(c-1)\right].
$$

The outlet temperatures in terms of $\dot Q$ are

$$
T_{c,\rm out}=T_{c,\rm in}+\frac{\dot Q}{C_c}=T_{c,\rm in}+\frac{\dot Q}{C_{\min}},\qquad
T_{h,\rm out}=T_{h,\rm in}-\frac{\dot Q}{C_h}=T_{h,\rm in}-\frac{\dot Q}{C_{\max}}.
$$

Substitute them:

$$
\frac{T_{h,\rm in}-\dot Q/C_{\max}-T_{c,\rm in}}{T_{h,\rm in}-\dot Q/C_{\min}-T_{c,\rm in}}=\exp\left[-\mathrm{NTU}(c-1)\right].
$$

Now $\dot Q=\epsilon C_{\min}(T_{h,\rm in}-T_{c,\rm in})$, so $\dot Q/C_{\min}=\epsilon(T_{h,\rm in}-T_{c,\rm in})$ and $\dot Q/C_{\max}=\epsilon c\,(T_{h,\rm in}-T_{c,\rm in})$:

$$
\frac{\left(T_{h,\rm in}-T_{c,\rm in}\right)-\epsilon c\left(T_{h,\rm in}-T_{c,\rm in}\right)}{\left(T_{h,\rm in}-T_{c,\rm in}\right)(1-\epsilon)}=\exp\left[-\mathrm{NTU}(c-1)\right]
\quad\Rightarrow\quad
\frac{1-\epsilon c}{1-\epsilon}=\exp\left[-\mathrm{NTU}(c-1)\right].
$$

Invert both sides, which changes the sign of the exponent:

$$
\frac{1-\epsilon}{1-\epsilon c}=\exp\left[-\mathrm{NTU}(1-c)\right].
$$

Multiply out:

$$
1-\epsilon=\exp\left[-\mathrm{NTU}(1-c)\right]-\epsilon c\exp\left[-\mathrm{NTU}(1-c)\right].
$$

Collect the $\epsilon$ terms on the left:

$$
\epsilon\left(1-c\exp\left[-\mathrm{NTU}(1-c)\right]\right)=1-\exp\left[-\mathrm{NTU}(1-c)\right]
$$

$$
\Rightarrow\quad
\boxed{\epsilon_{\text{counter-flow}}=\frac{1-\exp\left[-\mathrm{NTU}(1-c)\right]}{1-c\exp\left[-\mathrm{NTU}(1-c)\right]}}
$$

For the other case, $C_h=C_{\min}$, the right-hand side of (4.2) is $-(UA_s/C_h)(1-C_h/C_c)=-\mathrm{NTU}(1-c)$. The numerator becomes $T_{h,\rm in}-\dot Q/C_{\min}-T_{c,\rm in}=(1-\epsilon)(T_{h,\rm in}-T_{c,\rm in})$ and the denominator $T_{h,\rm in}-T_{c,\rm in}-\dot Q/C_{\max}=(1-\epsilon c)(T_{h,\rm in}-T_{c,\rm in})$, which is the inverted equation $(1-\epsilon)/(1-\epsilon c)=\exp[-\mathrm{NTU}(1-c)]$ directly. Both choices give the same effectiveness.

### 5.5 Limiting cases

Each limit below is a statement about the two formulas, so each carries its own condition.

**One stream at constant temperature, $c=0$.** A condensing vapour or boiling liquid changes phase at constant temperature: $\Delta T_h=0$, so $C_h\to\infty$, $C_{\min}=C_c$ and $c=0$. Both formulas reduce to the same result:

$$
\epsilon_{\text{parallel-flow}}\big|_{c=0}=\frac{1-e^{-\mathrm{NTU}}}{1}=1-e^{-\mathrm{NTU}},\qquad
\epsilon_{\text{counter-flow}}\big|_{c=0}=\frac{1-e^{-\mathrm{NTU}}}{1-0}=1-e^{-\mathrm{NTU}}.
$$

The same follows from the element balance directly, without any assumption about flow direction. With the hot side fixed at $T_h$, $C_c\,\mathrm dT_c=U(T_h-T_c)\,\mathrm dA_s$; separating and integrating over the cold stream's path,

$$
\int_{T_{c,\rm in}}^{T_{c,\rm out}}\frac{\mathrm dT_c}{T_h-T_c}=\frac{U}{C_c}\int_0^{A_s}\mathrm dA_s
\quad\Rightarrow\quad
\ln\frac{T_h-T_{c,\rm in}}{T_h-T_{c,\rm out}}=\mathrm{NTU}
\quad\Rightarrow\quad
\epsilon=\frac{T_{c,\rm out}-T_{c,\rm in}}{T_h-T_{c,\rm in}}=1-e^{-\mathrm{NTU}}.
$$

Since the hot stream has a single temperature, it does not matter whether the cold stream runs with it, against it, across it or through several passes. That is why the two-pass shell-and-tube condenser of §7 can use the counter-flow formula with $c=0$, and why the LMTDs of the two arrangements coincide for a condenser.

**Balanced counter flow, $c=1$.** With $C_c=C_h$ the counter-flow formula reads $0/0$ (both numerator and denominator are $1-1$), so the formula itself cannot be evaluated and $\delta\dot Q=U(T_h-T_c)\,\mathrm dA_s$ has to be integrated directly. When $C_c=C_h$ the element balance gives $C_c\,\mathrm dT_c=C_h\,\mathrm dT_h$ (both temperatures fall in the direction of $A_s$ by the same amount), so

$$
\mathrm dT_c=\mathrm dT_h\quad\Rightarrow\quad\mathrm d(\Delta T)=0 ,
$$

and the temperature difference is the same everywhere: $\Delta T=\Delta T_1=\Delta T_2=T_{h,\rm in}-T_{c,\rm out}$. Then

$$
\epsilon=\frac{\dot Q}{\dot Q_{\max}}=\frac{UA_s\Delta T}{C_{\min}\left(T_{h,\rm in}-T_{c,\rm in}\right)}=\mathrm{NTU}\,\frac{T_{h,\rm in}-T_{c,\rm out}}{T_{h,\rm in}-T_{c,\rm in}}.
$$

The cold outlet is $T_{c,\rm out}=T_{c,\rm in}+\dot Q/C_{\min}=T_{c,\rm in}+\epsilon(T_{h,\rm in}-T_{c,\rm in})$, so

$$
\epsilon=\mathrm{NTU}\,\frac{\left(T_{h,\rm in}-T_{c,\rm in}\right)-\epsilon\left(T_{h,\rm in}-T_{c,\rm in}\right)}{T_{h,\rm in}-T_{c,\rm in}}=\mathrm{NTU}(1-\epsilon)
\quad\Rightarrow\quad
\boxed{\epsilon=\frac{\mathrm{NTU}}{1+\mathrm{NTU}}}\qquad(\text{counter flow},\ c=1).
$$

The same value is the limit of the general formula as $c\to1$: with $x=\mathrm{NTU}(1-c)\to0$, $1-e^{-x}\approx x$ and $1-ce^{-x}\approx(1-c)+cx$, so $\epsilon\approx x/[(1-c)+cx]=\mathrm{NTU}/(1+c\,\mathrm{NTU})\to\mathrm{NTU}/(1+\mathrm{NTU})$. Numerically, the general formula at $\mathrm{NTU}=2$, $c=1-10^{-7}$ gives $\epsilon=0.66667=2/3$.

**Balanced parallel flow, $c=1$.** No difficulty here: $\epsilon=\tfrac12\left(1-e^{-2\,\mathrm{NTU}}\right)$, which can never exceed $\tfrac12$.

**Large exchangers, $\mathrm{NTU}\to\infty$.** In parallel flow $e^{-\mathrm{NTU}(1+c)}\to0$, so $\epsilon\to1/(1+c)$: the two streams approach a common outlet temperature and no amount of extra area takes them further. In counter flow with $c<1$, $e^{-\mathrm{NTU}(1-c)}\to0$ and $\epsilon\to1$; with $c=1$, $\mathrm{NTU}/(1+\mathrm{NTU})\to1$ as well. Only counter flow can in principle reach $\dot Q_{\max}$ with both streams changing temperature.

**Small exchangers, $\mathrm{NTU}\to0$.** Expanding the exponentials to first order, both formulas give $\epsilon\approx\mathrm{NTU}$, independent of $c$: when the streams barely change temperature, $T_h-T_c\approx\Delta T_{\max}$ everywhere and $\dot Q\approx UA_s\Delta T_{\max}$.

### 5.6 Observations on effectiveness

![[at_w09f_effectiveness_ntu.png|900]]

Effectiveness varies from 0 to 1. It increases rapidly with NTU for small values and rather slowly for larger ones, and larger NTU values mean a larger heat exchanger. For counter flow with $c=0.5$, raising NTU from 1 to 2 lifts $\epsilon$ from 0.565 to 0.775, while doubling again from 2 to 4 adds only 0.153 more, to 0.927. A heat exchanger with a high effectiveness may therefore be desirable from a heat transfer point of view but undesirable economically, since the last few per cent cost a disproportionate amount of surface, weight and money.

For a given NTU and capacity ratio, the counter-flow exchanger has the highest effectiveness and the parallel-flow exchanger the lowest; crossflow and shell-and-tube arrangements lie in between. The gap closes at small NTU (both $\approx\mathrm{NTU}$) and at $c=0$ (both $1-e^{-\mathrm{NTU}}$), and is widest for balanced streams: at $c=1$ and $\mathrm{NTU}=5$, $\epsilon=0.833$ in counter flow against 0.500 in parallel flow.

### Worked example: outlet temperatures by the NTU method

*Counter-flow heat exchanger with the data of the sizing example: $C_c=1500$ W K⁻¹, $h_c=275$ W m⁻² K⁻¹, $T_{c,\rm in}=15$ °C; $C_h=3000$ W K⁻¹, $h_h=400$ W m⁻² K⁻¹, $T_{h,\rm in}=150$ °C. Find the outlet temperatures if $A_s=10.06$ m².*

This is the sizing problem run backwards: the area found there is now given, and the outlets are unknown.

**1. NTU.** $U=162.963$ W m⁻² K⁻¹ as before (conduction through the wall ignored). $C_{\min}=\min\{C_c,C_h\}=C_c=1500$ W K⁻¹, so

$$
\mathrm{NTU}=\frac{UA_s}{C_{\min}}=\frac{162.963\times10.06}{1500}=1.09294 .
$$

**2. Effectiveness.** $c=C_{\min}/C_{\max}=1500/3000=0.5$, and $\mathrm{NTU}(1-c)=0.54647$, so $\exp[-\mathrm{NTU}(1-c)]=0.57899$:

$$
\epsilon=\frac{1-0.57899}{1-0.5\times0.57899}=\frac{0.42101}{0.71051}=0.59255 .
$$

**3. Heat transfer rate:**

$$
\dot Q=\epsilon C_{\min}\left(T_{h,\rm in}-T_{c,\rm in}\right)=0.59255\times1500\times(150-15)=119\,991\ \text{W}\approx120\ \text{kW}.
$$

**4. Outlet temperatures:**

$$
T_{h,\rm out}=T_{h,\rm in}-\frac{\dot Q}{C_h}=150-\frac{120\,000}{3000}=\boxed{110\ ^\circ\text{C}},\qquad
T_{c,\rm out}=T_{c,\rm in}+\frac{\dot Q}{C_c}=15+\frac{120\,000}{1500}=\boxed{95\ ^\circ\text{C}}.
$$

These are the temperatures the sizing example started from, as they must be. In kelvin, $423\ \text{K}-40\ \text{K}=383\ \text{K}=110\ ^\circ\text{C}$; differences are the same in either unit. With the unrounded $\dot Q=119\,991$ W the outlets are 110.003 °C and 94.994 °C.

> [!check] The same hardware in parallel flow
> With the same NTU and $c$ the parallel-flow formula gives $\epsilon=[1-e^{-1.09294\times1.5}]/1.5=0.53727$, so $\dot Q=108.8$ kW, $T_{h,\rm out}=113.7$ °C and $T_{c,\rm out}=87.5$ °C. A numerical integration of the element balance reproduces all three values. Turning the cold stream round gains 11.2 kW (10 %) for nothing.

## 6. Choosing the method

The two methods contain the same physics, (4.1) and (4.2), rearranged for different unknowns. LMTD suits a **sizing** problem: the duty and therefore all four terminal temperatures are known (two given, two from the energy balance), and the area or length is wanted. NTU suits a **rating** problem: the exchanger and the inlets are known and the outlets are wanted. Each can do the other's job. For a sizing problem with NTU, find $\epsilon$ from the temperatures and invert the formula for NTU; solving the boxed results for NTU gives

$$
\mathrm{NTU}_{\text{parallel-flow}}=-\frac{\ln\left[1-\epsilon(1+c)\right]}{1+c},\qquad
\mathrm{NTU}_{\text{counter-flow}}=\frac{1}{c-1}\ln\frac{\epsilon-1}{\epsilon c-1}\quad(c\neq1),
$$

and with $c=0$ both become $\mathrm{NTU}=-\ln(1-\epsilon)$, which is how the condenser of §7 is sized. For the rating example of §5, $\epsilon=0.59255$ and $c=0.5$ in the counter-flow inversion return $\mathrm{NTU}=1.09294$. A rating problem with LMTD needs a guessed outlet temperature, an area check and iteration.

> [!note] Multi-pass shell-and-tube exchangers on exams
> For a multi-pass shell-and-tube exchanger with two sensible streams ($c>0$), textbook analyses multiply the counter-flow LMTD by a geometry correction factor $F<1$ or use a shell-and-tube $\epsilon$–NTU correlation. In this course, use the counter-flow relation whenever the paper prescribes it or supplies no $F$-chart or shell-and-tube formula: [[SESA3029 Past Paper 2022-23 - Solutions#Q5. Counterflow oil-water heat exchanger via LMTD (18 marks)|2022–23 Q5]] names an 8-pass exchanger "counterflow" with no $F$-chart (so $F=1$, versus $F=0.878$ from the chart), and [[SESA3029 Past Paper 2024-25 A - Solutions#Q4. Shell-and-tube heat exchanger (20 marks)|2024–25 A/B Q4]] print the counter-flow effectiveness formula for a double-pass shell-and-tube unit ($\epsilon=0.818$, versus $0.784$ for one shell pass and two tube passes). For a condenser or boiler ($c=0$), the arrangement does not matter and $\epsilon=1-e^{-\mathrm{NTU}}$ is exact (§5.5).

## 7. Heat exchanger examples

The two examples here bring in the parts that the sizing and rating examples took as given: the heat transfer coefficients come from Nusselt correlations ([[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]]), with the Reynolds number deciding between laminar and turbulent flow, and the area is turned into a tube length.

![[at_w09f_example_profiles.png|900]]

### Worked example: concentric tube heat exchanger

*Oil flows in the annulus and water in the inner tube of a counter-flow concentric tube heat exchanger, $D_i=25$ mm, $D_o=45$ mm. Oil: $\dot m_h=0.1$ kg s⁻¹, $T_{h,i}=100$ °C. Water: $\dot m_c=0.2$ kg s⁻¹, $T_{c,i}=30$ °C. Oil properties at $\overline T_h=80$ °C: $c_{p,h}=2131$ J kg⁻¹ K⁻¹, $\mu_h=3.25\times10^{-2}$ N s m⁻², $k_h=0.138$ W m⁻¹ K⁻¹. Water properties at $\overline T_c=35$ °C: $c_{p,c}=4178$ J kg⁻¹ K⁻¹, $\mu_c=7.25\times10^{-4}$ N s m⁻², $k_c=0.625$ W m⁻¹ K⁻¹, $\Pr_c=4.85$. Find the tube length to achieve a hot fluid outlet temperature of 60 °C.*

These examples write the subscripts $i$/$o$ in place of "in/out": $T_{h,i}$ is the hot inlet and $T_{h,o}$ the hot outlet.

**Heat transfer rate**, from the oil, whose both temperatures are known:

$$
\dot Q=\dot m_hc_{p,h}\left(T_{h,i}-T_{h,o}\right)=0.1\times2131\times(100-60)=8524\ \text{W}.
$$

**Cold outlet temperature:**

$$
T_{c,o}=T_{c,i}+\frac{\dot Q}{\dot m_cc_{p,c}}=30+\frac{8524}{0.2\times4178}=30+10.20=40.2\ ^\circ\text{C}.
$$

The water properties were taken at 35 °C, the mean of 30 and 40.2 °C to the nearest degree, and the oil properties at 80 °C, the mean of 100 and 60 °C, so the property data are consistent with the answer.

**Water side (inner tube).** With $\dot m_c=\rho_cV_cA_i$, the product $\rho_cV_c=\dot m_c/A_i$, and the Reynolds number needs no density:

$$
\mathrm{Re}_i=\frac{\rho_cV_cD_i}{\mu_c}=\frac{\dot m_cD_i}{A_i\mu_c}=\frac{0.2\times0.025}{\tfrac{\pi}{4}\times0.025^2\times7.25\times10^{-4}}=14\,049.5>2000 .
$$

The water flow is turbulent pipe flow, and the interior fluid is heated, so the turbulent pipe-flow correlation of [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]] applies with exponent 0.4 on Pr:

$$
\mathrm{Nu}=0.023\,\mathrm{Re}_i^{4/5}\Pr_c^{0.4}=\frac{h_cD_i}{k_c}
\quad\Rightarrow\quad
h_c=\frac{0.023\,\mathrm{Re}_i^{4/5}\Pr_c^{0.4}k_c}{D_i}.
$$

Here $\mathrm{Re}_i^{4/5}=2080.3$ and $\Pr_c^{0.4}=1.8806$, so $\mathrm{Nu}=0.023\times2080.3\times1.8806=89.98$ and

$$
h_c=\frac{89.98\times0.625}{0.025}=2249.5\ \text{W m}^{-2}\,\text{K}^{-1}.
$$

**Oil side (annulus).** A non-circular duct uses the **hydraulic diameter** $D_h=4A_c/P$, four times the flow area over the wetted perimeter. For the annulus both walls are wetted:

$$
A_h=\frac{\pi}{4}\left(D_o^2-D_i^2\right),\qquad P=\pi\left(D_o+D_i\right)
\quad\Rightarrow\quad
D_h=\frac{4\cdot\frac{\pi}{4}(D_o-D_i)(D_o+D_i)}{\pi(D_o+D_i)}=D_o-D_i=0.020\ \text{m}.
$$

(The $h$ in $D_h$ means hydraulic; in $h_h$, $A_h$ and $\mu_h$ it means hot.) Then

$$
\mathrm{Re}_o=\frac{\rho_hV_hD_h}{\mu_h}=\frac{\dot m_hD_h}{A_h\mu_h}=\frac{0.1\times(0.045-0.025)}{\frac{\pi}{4}\left(0.045^2-0.025^2\right)\times3.25\times10^{-2}}=55.97\ll2000 ,
$$

so the oil flow is laminar. Oil is about 45 times as viscous as water here, which is why its Reynolds number is 250 times smaller. For fully developed laminar flow in an annulus with one surface insulated and the other at constant temperature, the Nusselt number on the inner surface is a tabulated constant, $\mathrm{Nu}_i=5.64$ for this diameter ratio, $D_i/D_o=0.56$ (Bergman, p. 554). The oil exchanges heat only with the inner tube, the outer pipe being insulated, so

$$
h_h=\frac{\mathrm{Nu}_ik_h}{D_h}=\frac{5.64\times0.138}{0.02}=38.92\ \text{W m}^{-2}\,\text{K}^{-1}.
$$

**Overall coefficient**, thin inner-tube wall:

$$
\frac1U=\frac{1}{h_c}+\frac{1}{h_h}=\frac{1}{2249.5}+\frac{1}{38.92}=4.445\times10^{-4}+2.5694\times10^{-2}=2.6139\times10^{-2}
\quad\Rightarrow\quad
U=38.25\ \text{W m}^{-2}\,\text{K}^{-1}.
$$

(The unrounded coefficients give 38.254.) The oil film carries 98.3 % of the total resistance.

**LMTD**, counter flow:

$$
\Delta T_1=T_{h,i}-T_{c,o}=100-40.2=59.8\ \text{K},\qquad \Delta T_2=T_{h,o}-T_{c,i}=60-30=30\ \text{K},
$$

$$
\Delta T_{\rm lm}=\frac{59.8-30}{\ln(59.8/30)}=\frac{29.8}{0.68981}=43.2\ \text{K}.
$$

**Tube length.** The heat transfer surface is the inner tube, $A_s=\pi D_iL$:

$$
\dot Q=UA_s\Delta T_{\rm lm}=U\pi D_iL\,\Delta T_{\rm lm}
\quad\Rightarrow\quad
L=\frac{\dot Q}{U\pi D_i\Delta T_{\rm lm}}=\frac{8524}{38.25\times\pi\times0.025\times43.2}=\boxed{65.67\ \text{m}}.
$$

> [!check] The same length from the NTU method
> $C_h=213.1$ W K⁻¹ and $C_c=835.6$ W K⁻¹, so here the hot fluid is $C_{\min}$ and $c=0.2550$. The effectiveness is $\epsilon=8524/[213.1\times(100-30)]=0.5714$, and the counter-flow inversion of §6 gives $\mathrm{NTU}=0.9259$. Then $L=\mathrm{NTU}\,C_{\min}/(U\pi D_i)=0.9259\times213.1/(38.25\pi\times0.025)=65.67$ m, the same as LMTD. The unrounded chain gives 65.674 m. In parallel flow the same duty would need 71.4 m.

A tube 66 m long is impractical as a single straight run; it would be coiled or split into several passes. The length is set almost entirely by the laminar oil film, so the effective improvement is on the oil side (fins, or a faster, turbulent oil flow), not on the water side.

### Worked example: shell-and-tube condenser

*The condenser of a power plant is a shell-and-tube heat exchanger with a single shell and 30 000 tubes, each executing two passes. The temperature on the hot side is constant at 50 °C (condensing steam). Inflow on the cold side is at 20 °C. Tubes: $D=0.025$ m, $h_o=11\times10^3$ W m⁻² K⁻¹ (condensing steam on the outside), $\dot m=1$ kg s⁻¹ of water per tube. Water properties at $\overline T_c=27$ °C: $c_{p,c}=4179$ J kg⁻¹ K⁻¹, $\mu_c=8.55\times10^{-4}$ N s m⁻², $k_c=0.613$ W m⁻¹ K⁻¹, $\Pr_c=5.83$. The heat transfer rate is $\dot Q=2\times10^9$ W. What is the temperature of the cooling water emerging from the condenser, and what is the pass length $L$?*

**Cold outlet temperature.** The 30 000 tubes on the cold side carry

$$
\dot m_c=N\dot m=30\,000\times1=30\,000\ \text{kg s}^{-1},
$$

$$
T_{c,o}=T_{c,i}+\frac{\dot Q}{\dot m_cc_{p,c}}=20+\frac{2\times10^9}{30\,000\times4179}=20+15.953=\boxed{35.953\ ^\circ\text{C}}.
$$

The water properties at 27 °C are close to the mean of 20 and 36 °C.

**Water side, one tube.** Each tube carries 1 kg s⁻¹:

$$
\mathrm{Re}=\frac{\rho_cV_cD}{\mu_c}=\frac{\dot mD}{A\mu_c}=\frac{1\times0.025}{\frac{\pi}{4}\times0.025^2\times8.55\times10^{-4}}=59\,567>2000,
$$

which is turbulent pipe flow, with the fluid in the pipe heated:

$$
h_c=\frac{0.023\,\mathrm{Re}^{4/5}\Pr_c^{0.4}k_c}{D}=\frac{0.023\times59\,567^{4/5}\times5.83^{0.4}\times0.613}{0.025}=7542.56\ \text{W m}^{-2}\,\text{K}^{-1}
$$

($\mathrm{Re}^{4/5}=6607.0$, $\Pr_c^{0.4}=2.0243$, $\mathrm{Nu}=307.6$).

**Overall coefficient**, thin tube wall:

$$
\frac1U=\frac{1}{h_c}+\frac{1}{h_o}=\frac{1}{7542.56}+\frac{1}{11\,000}
\quad\Rightarrow\quad
U=4474.47\ \text{W m}^{-2}\,\text{K}^{-1}.
$$

**NTU method.** The steam condenses at constant temperature, $\Delta T_h=0$, so $C_h=\infty$. The cooling water is $C_{\min}$:

$$
C_{\min}=C_c=\dot m_cc_{p,c}=30\,000\times4179=1.2537\times10^8\ \text{W K}^{-1},\qquad c=\frac{C_{\min}}{C_{\max}}=0 .
$$

$$
\dot Q_{\max}=C_{\min}\left(T_{h,i}-T_{c,i}\right)=1.2537\times10^8\times(50-20)=3.7611\times10^9\ \text{W},
$$

$$
\epsilon=\frac{\dot Q}{\dot Q_{\max}}=\frac{2\times10^9}{3.7611\times10^9}=0.53176 .
$$

With $c=0$ the counter-flow formula, like every other arrangement (§5.5), reduces to $\epsilon=1-\exp(-\mathrm{NTU})$, so a two-pass shell-and-tube exchanger can be treated with it:

$$
\epsilon=1-\exp(-\mathrm{NTU})\quad\Rightarrow\quad-\mathrm{NTU}=\ln(1-\epsilon)
\quad\Rightarrow\quad
\mathrm{NTU}=-\ln(1-0.53176)=0.75877 .
$$

**Tube length.** Let $L'$ be the total length of one tube over both passes, so the total surface is $A_s=\pi DL'N$:

$$
\mathrm{NTU}=\frac{UA_s}{C_{\min}}=\frac{U\pi DL'N}{C_{\min}}
\quad\Rightarrow\quad
L'=\frac{\mathrm{NTU}\,C_{\min}}{U\pi DN}=\frac{0.75877\times1.2537\times10^8}{4474.47\times\pi\times0.025\times30\,000}=9.023\ \text{m}.
$$

Each tube makes two passes, so the pass length is

$$
L=\frac{L'}{2}=\boxed{4.512\ \text{m}}.
$$

**The same by LMTD.** The hot side is at 50 °C throughout. With the end differences

$$
\Delta T_1=T_{h,i}-T_{c,o}=50-35.953=14.047\ \text{K},\qquad \Delta T_2=T_{h,o}-T_{c,i}=50-20=30\ \text{K},
$$

$$
\Delta T_{\rm lm}=\frac{\Delta T_2-\Delta T_1}{\ln(\Delta T_2/\Delta T_1)}=\frac{30-14.047}{\ln(30/14.047)}=21.024\ \text{K},
$$

$$
\dot Q=UA_s\Delta T_{\rm lm}=U\pi DL'N\Delta T_{\rm lm}
\quad\Rightarrow\quad
L'=\frac{\dot Q}{U\pi DN\Delta T_{\rm lm}}=\frac{2\times10^9}{4474.47\times\pi\times0.025\times30\,000\times21.024}=9.023\ \text{m}.
$$

Both methods give the same length, which they must: with $c=0$, $\ln(\Delta T_2/\Delta T_1)=\ln[1/(1-\epsilon)]=\mathrm{NTU}$, and the flow arrangement does not enter.

> [!check] Condenser numbers
> Unrounded values: $T_{c,o}=35.953$ °C, $\mathrm{Re}=59\,567$, $h_c=7542.56$ W m⁻² K⁻¹, $U=4474.47$ W m⁻² K⁻¹, $\epsilon=0.531759$, $\mathrm{NTU}=0.758773$, $L'=9.0230$ m by both routes, $L=4.512$ m. The total surface is $\pi DL'N=21\,260$ m². As a rough scale, at a latent heat of about 2.38 MJ kg⁻¹ for water at 50 °C (not given in the question) the condenser would condense about 840 kg of steam per second.

## Problem-solving workflow

1. Write down $C_h=\dot m_hc_{ph}$ and $C_c=\dot m_cc_{pc}$; a condensing or boiling stream has $C\to\infty$.
2. Find any unknown terminal temperature from $\dot Q=C_h(T_{h,\rm in}-T_{h,\rm out})=C_c(T_{c,\rm out}-T_{c,\rm in})$.
3. If $U$ is not given, find each $h$: Re from $\dot m D/(A\mu)$ (hydraulic diameter for an annulus), then the laminar or turbulent Nusselt relation stated in the question, then $1/U=1/h_i+1/h_o$ for a thin wall.
4. Sizing (all temperatures known): $\Delta T_1$ and $\Delta T_2$ from a sketch of the $T$–$A_s$ diagram, $\Delta T_{\rm lm}$, $A_s=\dot Q/(U\Delta T_{\rm lm})$.
5. Rating (only inlets known): $c$, NTU, $\epsilon$ from the arrangement's formula (any arrangement with $c=0$: $1-e^{-\mathrm{NTU}}$), $\dot Q=\epsilon C_{\min}\Delta T_{\max}$, then the outlets.
6. Area to length: $A_s=N\pi DL'$; pass length $L'/n_{\rm passes}$.
7. Check: $0<\epsilon<1$, the cold outlet below the hot inlet, in parallel flow $T_{c,\rm out}<T_{h,\rm out}$, and the property temperatures roughly equal to the mean stream temperatures.

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| overall heat transfer coefficient $U$ | U-value; overall conductance (for $UA$) | 5.8 slides 6, 12 | Always tied to an area: $U_iA_i=U_oA_o$ |
| heat capacity rate $C=\dot mc_p$ | capacity rate; thermal capacity rate | 5.8 slide 10; 5.9 slides 3–4 | |
| capacity ratio $c=C_{\min}/C_{\max}$ | heat capacity ratio; $C_r$ (Bergman, Çengel; ES3) | 5.9 slides 8–9, 14 | |
| log mean temperature difference (LMTD) $\Delta T_{\rm lm}$ | log-mean temperature difference | 5.8 slides 11–19 | |
| number of heat transfer units (NTU) | number of transfer units | 5.9 slides 2, 8 | |
| effectiveness $\epsilon$ | heat exchanger effectiveness; thermal effectiveness; $\varepsilon$ | 5.9 slides 2–17 | |
| parallel flow | co-current flow; parallel-flow | 5.8 slides 7, 11–13 | |
| counter flow | counterflow; countercurrent flow | 5.8 slides 7, 14–19 | |
| concentric tube heat exchanger | double-pipe heat exchanger | 5.10 slides 2–6 | |

## Links

- Parent: [[SESA3029 Aerothermodynamics Hub]]
- Previous: [[SESA3029 W09e - Numerical Methods in Conduction]]
- New concepts: [[Overall Heat Transfer Coefficient]] · [[Types of Heat Exchangers]] · [[Heat Capacity Rate]] · [[Log Mean Temperature Difference]] · [[Heat Exchanger Effectiveness and NTU]]
- Earlier in the block: [[SESA3029 W09a - Heat Conduction and Thermal Resistance|W09a]] (thermal resistance of a cylinder, resistances in series) · [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy|W09b]] (Nusselt correlations, the turbulent pipe-flow correlation of 5.3) · [[SESA3029 W09c - Critical Thickness of Insulation and Fins|W09c]] (fins on the low-$h$ side)
- Earlier years: [[Steady-flow Energy Equation]] (SESA1016) · [[Reynolds Number]]
- Worked sheets and papers: [[SESA3029 Example Sheet 3 - Solutions#Q5. Parallel-flow heat exchanger|ES3 Q5]] · [[SESA3029 Example Sheet 3 - Solutions#Q6. Minimum condenser-pipe length|ES3 Q6]] · [[SESA3029 Past Paper 2022-23 - Solutions#Q5. Counterflow oil-water heat exchanger via LMTD (18 marks)|2022–23 Q5]] (LMTD, counter flow) · [[SESA3029 Past Paper 2023-24 - Solutions#Q4. Steam-condensing shell-and-tube heat exchanger (20 marks)|2023–24 Q4]] (condenser, $c=0$) · [[SESA3029 Past Paper 2024-25 A - Solutions#Q4. Shell-and-tube heat exchanger (20 marks)|2024–25 A Q4]] · [[SESA3029 Past Paper 2024-25 B - Solutions#Q4. Shell-and-tube heat exchanger (16 marks)|2024–25 B Q4]]
- Formulae: [[SESA3029 Formula Sheet]]

## Sources

- `Lecture5.8(1).pdf`: Lecture 5.8, Heat exchangers: types of heat exchangers and the LMTD method, 19 slides (practical examples 2–3; overall heat transfer coefficient 4–6; types 7–8; general equations and heat capacity rate 9–10; LMTD derivation for parallel flow 11–13 and counter flow 14–16; worked example 17–19) → §§1–4.
- `Lecture5.9(1).pdf`: Lecture 5.9, Heat exchangers: number of heat transfer units concept, 17 slides (effectiveness and $\dot Q_{\max}$ 2–4; parallel-flow effectiveness 5–8; counter-flow effectiveness 9–11; the $c=1$ case 12–13; observations 14; worked example 15–17) → §§5–6.
- `Lecture5.10.pdf`: Lecture 5.10, Heat exchanger examples, 11 slides (concentric tube heat exchanger 2–6; shell-and-tube condenser 7–11) → §7.
- No transcript exists yet. This note was written ahead from the slides, which are last year's decks re-issued; the lectures are expected in early December 2026, and the note will be reconciled with the transcripts once the lectures have been given. The decks do not name the lecturer.
- Figures: `generate_aerothermo_w09f_figures.py` (`at_w09f_resistance_network.png`, `at_w09f_flow_arrangements.png`, `at_w09f_crossflow_shell_tube.png`, `at_w09f_lmtd_vs_mean.png`, `at_w09f_effectiveness_ntu.png`, `at_w09f_example_profiles.png`). The temperature profiles are numerical integrations of the element balance with the example data; the drawings are redrawn from the physics, not copied from the slides.
- Reading: Çengel, *Heat Transfer*, chapter on heat exchangers (the crossflow sketch on 5.8 slide 8 is from it); Bergman et al., *Fundamentals of Heat and Mass Transfer*, chapter 11, and the laminar annulus table cited on 5.10 slide 5. Shell-and-tube picture on 5.8 slide 8 from Parisher and Rhea, *Pipe Drafting and Design*, 3rd ed.

## Self-study tasks

No tasks are explicitly set on the slides. The tasks below are the slide derivations and worked examples, citing the slide where each is set, plus the related sheet and past-paper questions. Tasks marked so are suggested, not lecturer-set.

### Core

- [ ] **(5.8 slides 17–19)** Counter-flow exchanger, $C_c=1500$, $C_h=3000$ W K⁻¹, $h_c=275$, $h_h=400$ W m⁻² K⁻¹, 15 °C and 150 °C in: find $A$ for $T_{h,\rm out}=110$ °C. Answer 10.06 m². → [[#Worked example: counter-flow area by the LMTD method]]
- [ ] **(5.9 slides 15–17)** The same exchanger with $A_s=10.06$ m²: find the outlet temperatures by the NTU method. Answer 110 °C and 95 °C. → [[#Worked example: outlet temperatures by the NTU method]]
- [ ] **(5.10 slides 2–6)** Concentric tube oil–water exchanger: tube length for an oil outlet of 60 °C. Answer 65.67 m. → [[#Worked example: concentric tube heat exchanger]]
- [ ] **(5.10 slides 7–11)** Power-plant condenser, 30 000 tubes, two passes: cooling-water outlet and pass length by NTU and by LMTD. Answers 35.95 °C and 4.512 m. → [[#Worked example: shell-and-tube condenser]]
- [ ] **(5.8 slides 12–15)** Derive $\dot Q=UA_s\Delta T_{\rm lm}$ for parallel flow and for counter flow from the energy balance on an element $\mathrm dA_s$, with the correct sign of $\mathrm dT_c$ in each. → [[#4.1 Parallel flow|§4.1]], [[#4.2 Counter flow|§4.2]]

### Further practice

- [ ] **(5.9 slides 5–11)** Derive $\epsilon_{\text{parallel-flow}}$ and $\epsilon_{\text{counter-flow}}$ in terms of NTU and $c$, and show that the choice of which fluid is $C_{\min}$ does not matter. → [[#5.3 Parallel-flow effectiveness|§5.3]], [[#5.4 Counter-flow effectiveness|§5.4]]
- [ ] **(5.9 slides 12–13)** Show that for counter flow with $c=1$ the temperature difference is constant and $\epsilon=\mathrm{NTU}/(1+\mathrm{NTU})$. → [[#5.5 Limiting cases|§5.5]]
- [ ] **(5.9 slide 4)** Explain why $\dot Q_{\max}$ uses $C_{\min}$ and not $C_{\max}$. → [[#5.1 Effectiveness and the maximum heat transfer rate|§5.1]]
- [ ] **(5.8 slides 5–6)** Derive $1/U=1/h_i+1/h_o$ from the resistance network, stating the two approximations. → [[#1. The overall heat transfer coefficient|§1]]
- [ ] [[SESA3029 Example Sheet 3 - Solutions#Q5. Parallel-flow heat exchanger|ES3 Q5]] (parallel flow, NTU method; with the course's $c$ in place of $C_r$: $c=0.754$, $\mathrm{NTU}=0.257$, $\epsilon=0.207$, outlets 73.5 °C hot and 22.5 °C cold) and [[SESA3029 Example Sheet 3 - Solutions#Q6. Minimum condenser-pipe length|ES3 Q6]] (condenser pipe, $c=0$).
- [ ] Past papers: [[SESA3029 Past Paper 2022-23 - Solutions#Q5. Counterflow oil-water heat exchanger via LMTD (18 marks)|2022–23 Q5]] (LMTD sizing, eight passes) · [[SESA3029 Past Paper 2023-24 - Solutions#Q4. Steam-condensing shell-and-tube heat exchanger (20 marks)|2023–24 Q4]] (condensing steam, $c=0$) · [[SESA3029 Past Paper 2024-25 A - Solutions#Q4. Shell-and-tube heat exchanger (20 marks)|2024–25 A Q4]] · [[SESA3029 Past Paper 2024-25 B - Solutions#Q4. Shell-and-tube heat exchanger (16 marks)|2024–25 B Q4]].
- [ ] (suggested, not lecturer-set) Show that the LMTD tends to $\Delta T$ when $\Delta T_1\to\Delta T_2$, and that it is always below the arithmetic mean. → [[#4.3 Properties of the LMTD|§4.3]]
- [ ] (suggested, not lecturer-set) Rework the 5.8 example in parallel flow with the same four terminal temperatures and show that 34 % more area is needed (13.48 m²). → [[#4.3 Properties of the LMTD|§4.3]]
- [ ] (suggested, not lecturer-set) Check the concentric-tube length by the NTU method ($C_{\min}=C_h$, $c=0.255$, $\epsilon=0.571$, $\mathrm{NTU}=0.926$). → [[#Worked example: concentric tube heat exchanger|§7]]

## Transcript and slide slips

No transcripts exist yet; all items are slide slips.

> [!warning] 5.8 slide 18 and 5.9 slide 15: step title and units of U
> Where: [[#Worked example: counter-flow area by the LMTD method]].
>
> 5.8 slide 18 heads step 3 "Compute heat transfer rate", but the step computes the overall heat transfer coefficient $U$ (the rate was step 1). On both slides $U$ is printed as $162.963\ \text{W m}^{-2}\,\text{K}$; the unit is W m⁻² K⁻¹, as the same slides write it in the next lines.

> [!warning] 5.9 slide 7: "heat capacity ratio"
> Where: [[#5.3 Parallel-flow effectiveness]].
>
> The slide says "$C_{\max}$ is the larger heat capacity ratio". $C_{\max}$ is the larger heat capacity **rate**; the ratio is $c=C_{\min}/C_{\max}$.

> [!warning] 5.9 slide 12: "not defined for c = 1"
> Where: [[#5.5 Limiting cases]].
>
> The counter-flow formula is $0/0$ at $c=1$ and cannot be evaluated there, but the effectiveness itself is well defined: direct integration (slides 12–13) gives $\epsilon=\mathrm{NTU}/(1+\mathrm{NTU})$, which is also the limit of the formula as $c\to1$. The slide's own result shows this; only the wording is loose.

> [!warning] 5.9 slide 16: missing exponential
> Where: [[#Worked example: outlet temperatures by the NTU method]].
>
> The denominator is printed $1-0.5(-1.09294(1-0.5))$, without the exponential. It should be $1-0.5\exp(-1.09294(1-0.5))=0.71051$. The printed $\epsilon=0.59255$ is the correct value with the exponential; evaluating the printed expression would give $0.42101/1.27324=0.331$.

> [!warning] 5.10 slides 2 and 4: units of thermal conductivity
> Where: [[#Worked example: concentric tube heat exchanger]].
>
> $k_h=0.138$ and $k_c=0.625$ are printed in W m⁻¹ K; the unit is W m⁻¹ K⁻¹ (slide 7 has it right for the condenser).

> [!warning] 5.10 slides 7–8: the heat rate is not in the problem statement
> Where: [[#Worked example: shell-and-tube condenser]].
>
> The problem on slide 7 gives no heat rate, and the cooling-water outlet cannot be found without one. Slide 8 then uses $Q=2\times10^9$ W (written without the dot) to get $T_{c,o}=35.953$ °C, and slides 9 and 11 use the same value. Read the question as including $\dot Q=2\times10^9$ W.

> [!warning] 5.10 slide 11: L′ on both sides
> Where: [[#Worked example: shell-and-tube condenser]].
>
> The LMTD route is printed $L'=\dot Q/(U\pi DL'N\Delta T_{\rm lm})$, with $L'$ in the denominator as well. It should be $L'=\dot Q/(U\pi DN\Delta T_{\rm lm})$; the numbers that follow use the correct form and give 9.023 m.
