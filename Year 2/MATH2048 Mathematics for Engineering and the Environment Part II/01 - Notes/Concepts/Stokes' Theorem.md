---
title: "Stokes' Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Stokes's theorem", "Green's theorem", "Circulation theorem"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
related_concepts: ["[[Line Integrals]]", "[[Conservative Vector Fields]]", "[[Divergence Theorem]]", "[[Kelvin's Circulation Theorem]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture30_vector10.pdf", "02 - Sources/Lectures/MATH2048 Lecture 30.txt"]
---

# Stokes' Theorem

**Stokes' theorem** states that for an open surface $S$ with boundary curve $C$, $\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_C\mathbf F\cdot d\mathbf r$, with the normal and the direction round $C$ related by the right-hand rule.

With the thumb along the normal, the fingers give the direction of travel, so an upward normal means anticlockwise seen from above. The normal component of the curl is the circulation per unit area round a tiny loop; tiling the surface with such loops, the shared internal edges cancel and only $C$ remains. The surface must have an edge, so a closed surface gives zero.

The right-hand side depends only on $C$, so every surface with the same boundary gives the same curl flux. In Lecture 30, $\mathbf F=(2z-y)\,\mathbf i+(x+z)\,\mathbf j+(3x-2y)\,\mathbf k$ has constant curl $-3\,\mathbf i-\mathbf j+2\,\mathbf k$, and the paraboloid $z=9-x^2-y^2$, the flat disc beneath it, a cone with the same rim and the line integral round the circle $x^2+y^2=9$ all give $18\pi$. In the plane it reduces to Green's theorem, $\iint(\partial_xF_2-\partial_yF_1)\,dx\,dy=\oint(F_1\,dx+F_2\,dy)$.

![[m2048_vc_stokes_paraboloid.png|460]]

## Related

- Derivation and examples: [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem#3. Stokes' theorem (L30)|VC5 §3]]
- [[Line Integrals]] · [[Divergence, Curl and the Laplacian]] · [[Divergence Theorem]] · [[Conservative Vector Fields]]
