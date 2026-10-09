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

## Formula

$$
\boxed{\tan\theta=2\cot\beta\left[\frac{M_1^2\sin^2\beta-1}{M_1^2\left(\gamma+\cos2\beta\right)+2}\right]}
$$

$\theta$ is the flow deflection and $\beta$ the shock angle, both measured from $\mathbf V_1$.

## Derivation route

1. From the velocity triangles: $\tan\beta=U_{n1}/U_t$ and $\tan(\beta-\theta)=U_{n2}/U_t$, using $U_{t1}=U_{t2}$.
2. Divide: $U_{n1}/U_{n2}=\tan\beta/\tan(\beta-\theta)$.
3. Mass: $U_{n1}/U_{n2}=\rho_2/\rho_1$. Insert the density jump at $M_{n1}=M_1\sin\beta$:

   $$\frac{\tan\beta}{\tan(\beta-\theta)}=\frac{(\gamma+1)M_1^2\sin^2\beta}{2+(\gamma-1)M_1^2\sin^2\beta}.$$

4. Expand $\tan(\beta-\theta)=(\tan\beta-\tan\theta)/(1+\tan\beta\tan\theta)$, collect the $\tan\theta$ terms, and use $(\gamma-1)\sin^2\beta+(\gamma+1)\cos^2\beta=\gamma+\cos2\beta$.

Step-by-step algebra and figure: [[SESA3029 W02 - Oblique Shock Relations and Mach Waves#5. The θ–β–M relation, step by step|W02 §5]].

## Key features

- **Explicit in $\theta$, implicit in $\beta$.** Use the chart or a root finder to get $\beta(\theta,M_1)$.
- **Two roots** for $0<\theta<\theta_{max}$: weak (lower $\beta$) and strong (higher $\beta$).
- **$\theta_{max}(M_1)$:** 12.1° at $M_1=1.5$, 23.0° at 2, 34.1° at 3, 41.1° at 5, and 45.6° as $M_1\to\infty$. Beyond it the shock detaches.
- **$\theta=0$:** $\beta=90^\circ$ (normal shock) or $\beta=\mu=\sin^{-1}(1/M_1)$ (Mach wave). Hence $\mu\le\beta\le90^\circ$.
- **$M_1\to\infty$:** $\tan\theta\to\sin2\beta/(\gamma+\cos2\beta)$, independent of $M_1$.

![[at_theta_beta_m_chart.png|700]]

## Related

- [[Oblique-Shock Jump Relations]] · [[Weak and Strong Oblique Shocks]] · [[Mach Waves and Mach Angle]] · [[Oblique Shock Waves]] (SESA2023)
