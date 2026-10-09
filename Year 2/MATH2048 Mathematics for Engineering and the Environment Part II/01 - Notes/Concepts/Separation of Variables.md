---
title: "Separation of Variables"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 4: Partial Differential Equations"
aliases: ["Six-step method", "Normal modes", "Product solution"]
tags: [math2048, concept, pdes, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]", "[[MATH2048 PDE3 - The Heat Equation]]", "[[MATH2048 PDE5 - Laplace's Equation]]"]
related_concepts: ["[[ODE Eigenvalue Problems]]", "[[Half-Range Expansions]]", "[[Wave Equation]]", "[[Heat Equation]]", "[[Laplace's Equation]]", "[[Eigenfunction Expansion Method]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/PDEs/Lecture15_Hyperbolic2.pdf"]
---

# Separation of Variables

## Definition

> [!note] Definition
> Look for solutions of a linear homogeneous PDE with homogeneous BCs in the product form $u=X(x)T(t)$ (or $X(x)Y(y)$). The PDE then splits into ODEs linked by a **separation constant** $\lambda$.

## Explanation
**The six steps**, the same every time (25 marks in every exam):
1. Substitute $u=XT$, divide by $XT$, and set each side equal to $\lambda$. This gives two ODEs.
2. Turn the BCs on $u$ into BCs on $X$. $T$ gets **no** BCs.
3. Solve the eigenproblem for $X$ in the three cases $\lambda<0$, $\lambda=0$, $\lambda>0$. This gives $\lambda_n$ and $X_n$.
4. Solve the $T_n$ ODE:
   - wave equation: $\cos$ and $\sin$;
   - heat equation: $e^{-\kappa^2k_n^2t}$;
   - Laplace's equation: $\cosh$ and $\sinh$ in the second coordinate.
5. Superpose: $u=\sum X_nT_n$.
6. Fit the initial data (or the last BC) with a half-range Fourier series, or by inspection using orthogonality.

**Which series to use**:

| BCs | $X_n$ |
|---|---|
| D–D | $\sin\frac{n\pi x}{L}$ |
| N–N | $1$ and $\cos\frac{n\pi x}{L}$ |
| D–N | $\sin\frac{(2n-1)\pi x}{2L}$ |

**Why the constant exists**: one side of the equation depends only on $t$ and the other only on $x$. Two functions of different variables can only be equal everywhere if both are the same constant.

**When the method fails**: a source term in the PDE, or inhomogeneous BCs. Use the [[Eigenfunction Expansion Method]] or subtract a particular solution.

**Watch the sign convention**: $X''=\lambda X$ versus $X''+\lambda X=0$ swaps which sign of $\lambda$ oscillates.

## Examples
- Guitar string: $y=\sum_{\text{odd}}\frac{8}{(n\pi)^3}\cos n\pi ct\,\sin n\pi x$.
- Insulated rod: $u=\frac16-\sum_{\text{even}}\frac{4}{(n\pi)^2}e^{-(n\pi)^2t}\cos n\pi x$.
- Laplace on a square: $u=\sum_{\text{odd}}\frac{8\sin n\pi x\sinh n\pi y}{(n\pi)^3\sinh n\pi}$.

## Related
- [[ODE Eigenvalue Problems]] · [[Half-Range Expansions]] · [[Wave Equation]] · [[Heat Equation]] · [[Laplace's Equation]]

## Sources
- Lectures 15–20
