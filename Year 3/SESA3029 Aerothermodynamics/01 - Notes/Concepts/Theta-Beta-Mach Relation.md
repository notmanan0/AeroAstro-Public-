---
title: "Theta-Beta-Mach Relation"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["θ-β-M relation", "theta-beta-M", "oblique shock relation", "oblique shock chart"]
tags: [sesa3029, concept, oblique-shock]
status: complete
parent_lectures: ["[[SESA3029 W02 - Oblique Shock Relations and Mach Waves]]"]
related_concepts: ["[[Oblique-Shock Jump Relations]]", "[[Weak and Strong Oblique Shocks]]", "[[Mach Waves and Mach Angle]]"]
sources: ["02 - Sources/Lectures/Lecture2-1.pdf", "02 - Sources/Lectures/Lecture 2-1.txt"]
---

# Theta-Beta-Mach Relation

The $\theta$–$\beta$–$M$ relation links the flow deflection $\theta$ and the shock angle $\beta$, both measured from $\mathbf V_1$, for an oblique shock at upstream Mach number $M_1$:

$$
\boxed{\tan\theta=2\cot\beta\left[\frac{M_1^2\sin^2\beta-1}{M_1^2\left(\gamma+\cos2\beta\right)+2}\right]}
$$

## Where it comes from

The tangential velocity is the same on both sides, so the velocity triangles give $\tan\beta=U_{n1}/U_t$ and $\tan(\beta-\theta)=U_{n2}/U_t$. Dividing, $U_{n1}/U_{n2}=\tan\beta/\tan(\beta-\theta)$. Mass conservation says $U_{n1}/U_{n2}=\rho_2/\rho_1$, and the density jump at $M_{n1}=M_1\sin\beta$ then gives

$$\frac{\tan\beta}{\tan(\beta-\theta)}=\frac{(\gamma+1)M_1^2\sin^2\beta}{2+(\gamma-1)M_1^2\sin^2\beta}.$$

Expanding $\tan(\beta-\theta)=(\tan\beta-\tan\theta)/(1+\tan\beta\tan\theta)$, collecting the $\tan\theta$ terms and using $(\gamma-1)\sin^2\beta+(\gamma+1)\cos^2\beta=\gamma+\cos2\beta$ gives the boxed form. The step-by-step algebra is in [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#5. The θ–β–M relation, step by step|W02 §5]].

## Reading it

The relation is explicit in $\theta$ but not in $\beta$, so in practice you get $\beta(\theta,M_1)$ from the chart or a root finder. For $0<\theta<\theta_{max}$ there are two roots, a weak one at lower $\beta$ and a strong one at higher $\beta$ ([[Weak and Strong Oblique Shocks]]). Above $\theta_{max}$ there is no attached solution and the shock detaches. $\theta_{max}$ is 12.1° at $M_1=1.5$, 23.0° at 2, 34.1° at 3, 41.1° at 5, and tends to 45.6° as $M_1\to\infty$.

At $\theta=0$ the two roots are $\beta=90^\circ$, the normal shock, and $\beta=\mu=\sin^{-1}(1/M_1)$, the Mach wave, so every oblique shock has $\mu\le\beta\le90^\circ$. As $M_1\to\infty$ the relation becomes $\tan\theta\to\sin2\beta/(\gamma+\cos2\beta)$, independent of $M_1$.

![[at_theta_beta_m_chart.png|700]]

## Related

- [[Oblique-Shock Jump Relations]] · [[Weak and Strong Oblique Shocks]] · [[Mach Waves and Mach Angle]] · [[Oblique Shock Waves]] (SESA2023)
