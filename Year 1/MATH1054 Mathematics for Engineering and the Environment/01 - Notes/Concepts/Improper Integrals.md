---
title: "Improper Integrals"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Improper integral", "Convergent integral", "Divergent integral"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M10 - Integration III]]"]
related_concepts: ["[[Partial Fractions]]", "[[Laplace Transform]]", "[[Convergence Tests for Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.2", "MATH1054 Module Booklet, Module 10"]
---

# Improper Integrals

An improper integral is an integral over an infinite range, or of an integrand that is unbounded (has a singularity) somewhere on the range; it is defined as a limit of ordinary integrals, and it converges if that limit is finite and diverges otherwise.

The bad end is replaced by a variable and the limit taken afterwards:

$$
\int_a^\infty f\,\mathrm dx=\lim_{R\to\infty}\int_a^Rf\,\mathrm dx,\qquad\int_0^1f\,\mathrm dx=\lim_{\varepsilon\to0^+}\int_\varepsilon^1f\,\mathrm dx\quad(f\text{ unbounded at }0).
$$

A singularity inside the range, or a range infinite at both ends, is split into pieces with one bad end each, and every piece must converge on its own.

The benchmark is the p-integral. For $p\ne1$,

$$
\int_1^Rx^{-p}\,\mathrm dx=\frac{R^{1-p}-1}{1-p},\qquad\int_\varepsilon^1x^{-p}\,\mathrm dx=\frac{1-\varepsilon^{1-p}}{1-p}.
$$

$R^{1-p}\to0$ only when $p>1$, and $\varepsilon^{1-p}\to0$ only when $p<1$. So $\int_1^\infty x^{-p}\,\mathrm dx$ converges (to $\frac{1}{p-1}$) iff $p>1$, and $\int_0^1x^{-p}\,\mathrm dx$ converges (to $\frac{1}{1-p}$) iff $p<1$. At $p=1$ the integral is a logarithm, $\ln R$ or $-\ln\varepsilon$, and diverges at both ends. A tail must decay faster than $1/x$; a spike must be milder than $1/x$.

Taking the limits uses three standard results: $\varepsilon\ln\varepsilon\to0$ (L'Hôpital on $\ln\varepsilon/(1/\varepsilon)$), $R^ne^{-R}\to0$ (L'Hôpital $n$ times) and $\tan^{-1}R\to\frac\pi2$.

Worked example (James Example 9.1(c)): $\int_0^1\ln x\,\mathrm dx$ is singular at $0$. By parts, $\int\ln x\,\mathrm dx=x\ln x-x$, so

$$
\int_\varepsilon^1\ln x\,\mathrm dx=(0-1)-(\varepsilon\ln\varepsilon-\varepsilon)\to-1 .
$$

Other verified values from Module 10 (James Examples 9.1 and 9.4, Specimen Test 10): $\int_0^1x^{-2/3}\,\mathrm dx=3$; $\int_1^\infty x^{-3/2}\,\mathrm dx=2$; $\int_0^\infty e^{-x}\sin x\,\mathrm dx=\frac12$; $\int_{-\infty}^\infty e^{3x}e^{-e^x}\,\mathrm dx=\int_0^\infty u^2e^{-u}\,\mathrm du=2$ with $u=e^x$; and $\int_1^\infty x^{-1/2}\,\mathrm dx$ diverges.

The trap is a singularity inside the range. $\int_{-1}^1x^{-2}\,\mathrm dx$ is undefined, because each half diverges like $\int_0^1x^{-2}\,\mathrm dx$. Evaluating $-1/x$ straight across gives $-2$, which is negative for a positive integrand and therefore wrong: the antiderivative is not continuous on $[-1,1]$, so the fundamental theorem does not apply.

Improper integrals recur throughout engineering: the Laplace transform $\int_0^\infty e^{-st}f\,\mathrm dt$ ([[Laplace Transform]]), the normalisation of a probability density ([[Random Variables, PDF and CDF]]) and the escape energy $\int_{R_E}^\infty GMm/r^2\,\mathrm dr=GMm/R_E$ are all of this kind.

## Related

- Topics: [[MATH1054 M10 - Integration III]] ([[MATH1054 M10 - Integration III#7. The p-integrals and convergence|p-integrals]], [[MATH1054 M10 - Integration III#8. Worked examples: improper integrals|worked examples]]) · [[MATH1054 M10 Solutions - Integration III]] · [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]
- Concepts: [[Partial Fractions]] · [[Laplace Transform]] · [[Convergence Tests for Series]] · [[L'Hôpital's Rule]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §9.2 pp. 702–707; MATH1054 Module Booklet, Module 10.
