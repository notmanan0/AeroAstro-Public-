---
title: "Eigenvectors as Mode Shapes"
module: "SESA3047 Advanced Aerospace Mechanics & Control"
type: concept
stream: "Chapter 6: Aircraft Flight Dynamics and Interpretation of Eigenvectors"
aliases: ["mode shapes", "modal vector", "eigenvector interpretation", "eigenvector initial condition", "interpretation of eigenvectors"]
tags: [sesa3047, concept, eigenvectors, modes, flight-dynamics]
status: complete
coverage: "Chapter 6 §6.4, lectured in L17 (Mon 9 Nov)"
parent_lectures: ["[[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation]]"]
related_concepts: ["[[Matrix Exponential and Modal Solution]]", "[[Eigenvalue Decomposition]]", "[[Damping Ratio and Natural Frequency]]", "[[Short Period Oscillation]]", "[[Phugoid Mode]]"]
sources: ["02 - Sources/Lectures/Lecture Notes - Chapter 6.pdf", "02 - Sources/Lectures/09 November 2026 at 11_54_07.txt"]
---

# Eigenvectors as Mode Shapes

An eigenvector $\mathbf v_k$ of a state matrix, $\mathbf A\mathbf v_k=\lambda_k\mathbf v_k$, is the shape of one mode of motion: the relative amplitudes and phases with which the states move together, while its eigenvalue $\lambda_k$ sets how that motion grows, decays or oscillates in time.

Started exactly on an eigenvector, a linear system stays on it. Because $\mathbf A^n\mathbf v_k=\lambda_k^n\mathbf v_k$, the series for $e^{\mathbf At}$ collapses to $e^{\mathbf At}\mathbf v_k=e^{\lambda_kt}\mathbf v_k$, so only that mode appears. A real start on the real part of a complex eigenvector, $\mathcal R(\mathbf v_k)=\tfrac12(\mathbf v_k+\bar{\mathbf v}_k)$, excites the conjugate pair together and gives the real oscillation $e^{\sigma t}[\mathcal R(\mathbf v_k)\cos\omega t-\mathcal I(\mathbf v_k)\sin\omega t]$. Any other start is a mixture, $\mathbf x(t)=\sum_kc_ke^{\lambda_kt}\mathbf v_k$ with $\mathbf c=\mathbf V^{-1}\mathbf x_0$, and after long enough the least stable mode dominates.

Reading an eigenvector takes three steps. The modulus of each entry is that state's relative amplitude, but entries in different units (m/s against rad) have to be scaled before they are compared; dividing velocities by $U_\infty$ turns them into angles. The argument of each entry is the state's phase, so entries with equal arguments peak together. And only ratios matter: any non-zero complex multiple of an eigenvector is still one, which is why MATLAB's choice of unit length, $\sqrt{\sum|v_i|^2}=1$, and its choice of overall phase are conventions. For a real $\mathbf A$, complex eigenvalues and their eigenvectors come in conjugate pairs.

For the longitudinal example of Chapter 6, the SPO eigenvector is dominated by $w$ (angle of attack) with $q$ and $\theta$ at nearly constant speed, and the phugoid eigenvector by $u$ and $\theta$ at nearly constant angle of attack. In the phugoid $u$ and $q$ are in phase, $w$ is in antiphase, and $\theta$ lags $q$ by $90^\circ+\arcsin\zeta$ because the kinematic row $\dot\theta=q$ forces $\theta=q/\lambda$. The same reading applies to the lateral modes and to the mode shapes of a vibrating structure.

![[amc_ch6_eigenvector_phasors.png|800]]

## Related

- Worked through for the Eq. 6.4 model: [[SESA3047 6.1 - Longitudinal Modes, Eigenvectors and the SPO Approximation#4. Eigenvectors and modes (6.17–6.18)|6.1 §§4–6]]
- [[Matrix Exponential and Modal Solution]] · [[Eigenvalue Decomposition]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]] · [[Eigenvalues and Eigenvectors]]
- [[Short Period Oscillation]] · [[Phugoid Mode]] · [[Longitudinal and Lateral Dynamics]]
