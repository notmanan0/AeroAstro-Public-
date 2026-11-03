---
title: "Dirac Delta Function"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["Delta function", "Impulse", "Sifting property", "Impulse response"]
tags: [math2048, concept, transforms]
status: complete
parent_lectures: ["[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
related_concepts: ["[[Heaviside Step Function]]", "[[Laplace Transform Properties and Proofs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 13.txt"]
---

# Dirac Delta Function

The **Dirac delta** $\delta(x-c)$ is defined by what it does inside an integral: $\int_a^b\delta(x-c)f(x)\,dx=f(c)$ if $c$ lies inside $(a,b)$, and $0$ otherwise. This is the sifting property, and its Laplace transform follows from it at once, $\mathcal L[\delta(x-a)]=e^{-as}$ for $a>0$.

It is not a function but a functional, something that takes a function and returns a number, so it should only be used under an integral or a transform. The usual picture is a rectangle of unit area that gets narrower and taller, or a spike that is zero except at one point where it is infinite. Both are fine for intuition and useless for calculation. Physically it models an impulse, a force that changes the momentum in an instant, such as a hammer blow or the contact force on a ball bouncing off a wall. In the generalised sense it is the derivative of the [[Heaviside Step Function]].

Inside a product, $g(x)\delta(x-a)=g(a)\delta(x-a)$, so $\delta(x-2\pi)\cos x$ is just $\delta(x-2\pi)$ (PS5 Q3(h)). For $\alpha y''+\beta y'+\gamma y=\delta(x-a)$ with zero initial conditions, $\tilde y=e^{-as}/(\alpha s^2+\beta s+\gamma)$, so the solution is the impulse response $h=\mathcal L^{-1}[1/(\alpha s^2+\beta s+\gamma)]$, delayed to start at $x=a$. At the impulse $y$ stays continuous and $y'$ jumps by $1/\alpha$. The 2025/26 exam's $y''+2y'+2y=\delta(x-13)$ gives $y=H(x-13)e^{-(x-13)}\sin(x-13)$.

A train of impulses is handled term by term. Lecture 13's pendulum struck every $\pi$, $\ddot y+y=\sum_{n\geq0}\delta(t-n\pi)$, gives $y=\sum H(t-n\pi)\sin(t-n\pi)$: alternate strikes start and stop it. Strikes a whole period $2\pi$ apart would add in phase and the amplitude would grow by 1 with each.

## Related

- Derivation and examples: [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]
- [[Heaviside Step Function]] · [[Laplace Transform Properties and Proofs]]
