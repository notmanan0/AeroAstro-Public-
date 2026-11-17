---
title: "Ackeret Theory"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 4: High-speed aerodynamics"
aliases: ["Ackeret theory", "Ackeret formula", "linearised supersonic theory", "linear supersonic aerofoil theory", "first-order supersonic theory", "supersonic thin-aerofoil theory"]
tags: [sesa3029, concept, supersonic, linear-theory, aerofoil]
status: complete
parent_lectures: ["[[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils]]", "[[SESA3029 Tutorial Lecture 2 - Diamond Aerofoil by Ackeret Theory]]"]
related_concepts: ["[[Linearised Compressible Potential Equation]]", "[[Supersonic Wave Drag]]", "[[Shock-Expansion Theory]]", "[[Mach Waves and Mach Angle]]", "[[Riemann Invariants]]"]
sources: ["02 - Sources/Lectures/Lecture4-5.pdf", "02 - Sources/Lectures/Lecture 4-5.txt", "02 - Sources/Lectures/Lecture4-6.pdf"]
---

# Ackeret Theory

Ackeret theory is the linearised theory of thin aerofoils in supersonic flow. Its central result is that the pressure coefficient on a surface depends only on the local inclination $\theta$ of that surface to the free stream:

$$
C_p=\frac{2\theta}{\sqrt{M_\infty^2-1}}\qquad(\theta\text{ in radians, positive for compression}).
$$

For $M_\infty>1$ the linearised potential equation is the wave equation $\lambda^2\phi_{xx}=\phi_{yy}$, $\lambda=\sqrt{M_\infty^2-1}$. Its solution above the body is $\phi=f(x-\lambda y)$, constant along the free-stream Mach lines, so $u'=-v'/\lambda$. Flow tangency gives $v'/U_\infty=\theta$, and $C_p=-2u'/U_\infty$ then gives the formula. No field solution is needed: the surface slope fixes $C_p$ point by point. The same result is the weak-wave limit of the method of characteristics: above the body the invariant $R^-=\nu+\theta$ is uniform, so the flow is a simple flow region.

The sign of $\theta$ follows from a duct picture. A face and a streamline just outside it form a channel; if the channel narrows downstream, the supersonic flow slows and the pressure rises (compression, $\theta>0$), and if it widens, the flow speeds up and the pressure falls (expansion, $\theta<0$). On a flat plate at positive incidence the upper surface is the expansion, $\theta_u=-\alpha$, and the lower the compression, $\theta_l=+\alpha$.

For a thin aerofoil at incidence $\alpha$, with thickness $h(x)$ and camber $y_c(x)$:

$$
C_l=\frac{4\alpha}{\sqrt{M_\infty^2-1}},\qquad
C_d=\frac{4}{\sqrt{M_\infty^2-1}}\left[\alpha^2+\frac1c\int_0^c\left(\frac{\mathrm dh}{\mathrm dx}\right)^2\mathrm dx+\frac1c\int_0^c\left(\frac{\mathrm dy_c}{\mathrm dx}\right)^2\mathrm dx\right].
$$

Lift depends only on $\alpha$. Camber and thickness only add drag ([[Supersonic Wave Drag]]). On a flat plate $\Delta C_p$ is uniform, so the centre of pressure is at mid-chord. More generally $C_{m,LE}=-\tfrac12C_l-\frac{4}{\lambda c^2}\int_0^cy_c\,\mathrm dx$, so every thin aerofoil has its aerodynamic centre at $c/2$, and a symmetric one (a diamond, say) has its centre of pressure there too.

Accuracy: at $M_\infty=2$, $\alpha=10^\circ$, Ackeret gives $C_l=0.4031$ and $C_d=0.0703$, against the exact shock-expansion $0.4075$ and $0.0719$. It applies for $M_\infty$ from about 1.2 up to 3–4 and fails near $M_\infty=1$ and in hypersonic flow.

The theory assumes isentropic flow, although real supersonic aerofoils carry shocks. It still works because weak shocks are nearly isentropic: the stagnation-pressure loss grows like $\theta^3$, $1-p_{02}/p_{01}\simeq\gamma(\gamma+1)M_\infty^6\theta^3/(12\lambda^3)$, while the linearisation itself drops terms of order $\theta^2$ in $C_p$. On a 5 % diamond at $M_\infty=1.8$, $\alpha=2^\circ$, the stronger shock loses 0.16 % of the stagnation pressure ($M_{n1}=1.116$) while Ackeret's $C_p$ on that face is 10 % low. The loss reaches 1 % at $M_{n1}=1.23$.

![[at_ackeret_mach_lines.png|760]]

## Related

- [[SESA3029 W07c - Ackeret Theory and Optimum Supersonic Aerofoils|W07c]] (derivations and examples) · [[SESA3029 Example Sheet 2 - Solutions#Q4. Flat plate by Ackeret theory|ES2 Q4–Q5]] · [[SESA3029 Tutorial Lecture 2 - Diamond Aerofoil by Ackeret Theory|Tutorial 2]] (diamond face by face, $x_{AC}=c/2$, validity across weak shocks)
- [[Linearised Compressible Potential Equation]] · [[Prandtl-Glauert Transformation]] (subsonic counterpart) · [[Shock-Expansion Theory]] (exact method)
- [[Mach Waves and Mach Angle]] · [[Riemann Invariants]]
- Every step, with checks against shock-expansion: [[SESA3029 Deep Dive - Ackeret Theory and Optimum Supersonic Aerofoils]]
