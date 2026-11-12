---
title: "Buckingham Pi Theorem"
module: "SESA1016 Thermofluids"
type: concept
stream: "Similarity"
aliases: ["Buckingham Pi", "pi theorem"]
tags: [sesa1016, concept, dimensional-analysis]
status: complete
parent_lectures: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]"]
related_concepts: ["[[Reynolds Number]]"]
sources: ["02 - Sources/Lectures/Chapter 6.pdf"]
---

# Buckingham Pi Theorem

The Buckingham pi theorem says that a physically meaningful relation among $n$ dimensional variables, involving $k$ independent dimensions, can be rewritten as a relation among $n-k$ independent dimensionless groups.

It rests on dimensional homogeneity: every term of a correct physical equation has the same dimensions, so the equation can always be divided through to make it dimensionless. The theorem counts how many dimensionless groups are left once that is done. For the drag on a sphere, $D=f(\rho,V,d,\mu)$ has five variables in M, L and T, so there are $5-3=2$ groups and the whole problem collapses to $C_D=f(Re)$, one curve instead of a family of surfaces.

The method of repeating variables builds the groups systematically. Choose $k$ repeating variables that together contain all the dimensions but cannot themselves form a dimensionless group (for flow problems usually $\rho$, $V$ and a length). Combine each remaining variable with powers of the repeating ones, $\Pi=X\rho^aV^bL^c$, and solve the exponent equations for M, L and T. The groups are not unique: any product or power of groups is also a valid group, which is how $\rho Vd/\mu$ and $\mu/(\rho Vd)$ both appear.

The theorem says how many groups exist, not what the function between them is; that still comes from experiment or theory. Its practical value is in planning experiments and scale models: matching every group between model and full scale (complete similarity) guarantees that the dimensionless results transfer.

## Related

- [[SESA1016 T6 - Dimensional Analysis and Similarity#3. The Buckingham pi theorem|T6 §3]] · [[SESA1016 T6 - Dimensional Analysis and Similarity#Method of repeating variables|repeating variables]] · [[SESA1016 T6 - Dimensional Analysis and Similarity#5. Scale models and similarity|similarity]]
- [[Reynolds Number]]
