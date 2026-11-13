---
title: "FEEG1002 B4 - Stress Transformation and Mohr's Circle"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 13
tags: [feeg1002, statics-2, stress-transformation, mohrs-circle, principal-stresses, maximum-shear]
aliases: ["Statics 2 Lecture 5", "Statics 2 Lecture 6", "Stress transformation", "Mohr's circle", "Principal stresses"]
date: 2026-11-05
status: lectured
coverage: "Statics 2 Lecture 5 (24 Feb 2025, ll. 1–590): stresses on an inclined section of a bar, butt, scarf and finger joints, the wedge derivation of the plane-stress transformation equations, applications; Lecture 6 (3 Mar 2025, ll. 1–653): double-angle form, Mohr's circle and its construction, rotation on the circle, principal directions and stresses, maximum in-plane shear; recap in Lecture 9 (12 May 2025, ll. 296–463)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]"]
next_topics: ["[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
key_concepts: ["[[Stress Transformation Equations]]", "[[Mohr's Circle]]", "[[Principal Stresses]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions]]", "[[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]]", "[[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 05 - Stresses on Inclined Sections and Stress Transformation.pdf", "02 - Sources/Statics 2/Lectures/Lecture 06 - Mohr's Circle.pdf", "02 - Sources/Lectures/FEEG1002 Lecture 5 - Statics 2 - Stresses on inclinded sections, Stress transformation - Fe.txt", "02 - Sources/Lectures/FEEG1002 Lecture 6 - Statics 2 - Mohr's circle - March 2025.txt", "02 - Sources/Lectures/FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 04 - Stresses on Inclined Sections and Stress Transformation.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 05 - Mohr's Circle.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 08 - Revision Problems.pdf"]
---

# FEEG1002 B4 - Stress Transformation and Mohr's Circle

> [!abstract] Summary
> The same stress state gives different normal and shear stresses on differently oriented surfaces. Force equilibrium of a wedge gives the plane-stress transformation equations for an element rotated anticlockwise by $\theta$, $\sigma_{x'x'}=\sigma_{xx}\cos^2\theta+\sigma_{yy}\sin^2\theta+2\sigma_{xy}\sin\theta\cos\theta$ and $\sigma_{x'y'}=-(\sigma_{xx}-\sigma_{yy})\sin\theta\cos\theta+\sigma_{xy}(\cos^2\theta-\sin^2\theta)$. Eliminating $\theta$ shows that every pair $(\sigma_{x'x'},\sigma_{x'y'})$ lies on Mohr's circle, centred at $\sigma_{average}=(\sigma_{xx}+\sigma_{yy})/2$ with radius $R$. With shear plotted positive downwards, rotating the element by $\theta$ moves the point by $2\theta$ the same way; the principal stresses are $\sigma_{I,II}=\sigma_{average}\pm R$, on planes free of shear, and the maximum in-plane shear stress is $R$, at 45° to them.

> [!summary]- Exam use: quick path
> - **Use it when:** you need the stresses on a weld, glue line, fibre direction or slip plane at an angle, or the principal stresses, their directions and the maximum shear stress of a plane stress state.
> - **Assumptions:** plane stress (or plane strain; $\sigma_{zz}$ does not enter); $\theta$ measured from $x$ to the new normal $x'$, anticlockwise positive; course sign convention for $\sigma_{xy}$ read from the right-hand face.
> - **Method:** 1. Read $\sigma_{xx}$, $\sigma_{yy}$ and the sign of $\sigma_{xy}$ from the element. 2. Centre $\sigma_{average}=(\sigma_{xx}+\sigma_{yy})/2$ and radius $R=\sqrt{((\sigma_{xx}-\sigma_{yy})/2)^2+\sigma_{xy}^2}$. 3. Plot the $x$-face point $(\sigma_{xx},\sigma_{xy})$ with shear positive downwards and draw the circle. 4. Principal stresses $\sigma_{average}\pm R$, maximum shear $R$. 5. Measure $2\theta$ from the $x$-face point to the point you want, in the same sense as the physical rotation, and halve it.
> - **Common mistakes:** taking the angle of the weld line instead of the angle of its normal; plotting $\sigma_{xy}$ with the wrong sign, which mirrors the circle and turns the principal direction the wrong way.
> - **Practise:** [[#Worked example - sail element]] · [[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]]

The force on the cut face of a potato has a normal part and a shear part. A cut perpendicular to the local force has no shear at all, and tilting the knife introduces shear. Nothing about the potato has changed, only the surface. Stress transformation relates the normal and shear stresses on one surface to those on another through the same point.

It matters because materials and joints fail on particular planes. A ductile metal pulled in tension slips on planes at 45°, where the shear stress is largest; a glued joint fails when the stress across the glue line is too high; a fibre composite is strong along its fibres and weak across them; a spiral-welded pipe needs the stresses across its weld. In each case the stresses on an element aligned with $x$ and $y$ are known and those on an element turned through some angle are needed.

Mohr's circle is a graphical form of the answer, devised in the nineteenth century to avoid laborious calculation. It survives because it lets you see at once how the stresses change with orientation, where the largest normal stress acts and where the largest shear acts, without losing track of the algebra.

---

## 1. Stresses on an inclined section of a bar

### Area and force components

A bar of cross-section $A$ carries a tensile force $F$, so the stress on a cross-section is $\sigma_{xx}=F/A$. On a plane whose normal $x'$ makes an angle $\theta$ with the bar axis, horizontal equilibrium of the piece still needs a force $F$ on the cut, but the cut is larger:

$$
A_\theta=\frac{A}{\cos\theta}
$$

Resolve $F$ along the normal and along the surface:

$$
F_N=F\cos\theta,\qquad F_S=F\sin\theta
$$

### Normal and shear stress on the section

On a small element at the cut, with $x'$ along the normal and $y'$ along the surface, the normal stress is

$$
\sigma_{x'x'}=\frac{F_N}{A_\theta}=\frac{F\cos\theta}{A/\cos\theta}
$$

$$
\boxed{\sigma_{x'x'}=\sigma_{xx}\cos^2\theta}
$$

One cosine comes from resolving the force and the other from the larger area. The shear force on the right-hand piece points down the slope, in the negative $y'$ direction, while a positive shear stress on a face with positive normal points in $+y'$; hence a minus sign:

$$
\sigma_{x'y'}=-\frac{F_S}{A_\theta}=-\frac{F\sin\theta}{A/\cos\theta}
$$

$$
\boxed{\sigma_{x'y'}=-\sigma_{xx}\sin\theta\cos\theta}
$$

Neither stress is a stress multiplied by a single cosine or sine; both carry the double dependence on $\theta$.

### How the stresses vary with the angle

On the cross-section, $\theta=0$, the normal stress is the full $\sigma_{xx}$ and there is no shear. As $\theta$ grows the normal stress falls, reaching zero on a plane parallel to the bar, since nothing pulls across such a plane. The shear stress is zero at $\theta=0$ and at $\pm90^\circ$, and in between its magnitude peaks where $\sin\theta\cos\theta=\tfrac12\sin2\theta$ is largest, at $\theta=\pm45^\circ$:

$$
|\sigma_{x'y'}|_{max}=\frac{\sigma_{xx}}{2}
$$

with a normal stress of $\sigma_{xx}/2$ on the same plane. An element rotated by 45° therefore carries $\sigma_{xx}/2$ normal stress and $\sigma_{xx}/2$ shear stress on all four faces, even though the bar is in simple tension.

![[s2_inclined_section_uniaxial.png|850]]

### Joints and failure in shear

A butt joint, glued straight across, carries only normal stress in the glue. A scarf joint, cut at an angle, carries both. A finger joint uses long, shallow fingers, so the glue area is large and is loaded mainly in shear, at a low shear stress; and because each piece of wood thins as the other thickens, the stress and strain in the two pieces stay equal along the joint, so the glue is not sheared by differential stretching. The same result says that a material loaded in uniaxial tension can fail in shear at 45° if its shear strength is less than half its tensile strength; this is the starting point of the Tresca criterion in [[FEEG1002 B6 - Yield Criteria|B6]].

## 2. Plane-stress transformation

### Setting up the wedge

In general an element carries $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$. The stresses on an element rotated by $\theta$ are wanted, with $\theta$ the angle from the $x$ axis to the new axis $x'$, **positive anticlockwise**. Multiplying each stress by a cosine or a sine does not work; the stresses have to be found from equilibrium.

Take a wedge cut from the element: a vertical face of area $A$ with outward normal $-x$, a horizontal face of area $A\tan\theta$ with outward normal $-y$, and an inclined face of area $A/\cos\theta$ whose outward normal is $x'$. The vertical face carries $\sigma_{xx}$ acting in $-x$ and $\sigma_{xy}$ acting in $-y$; the bottom face carries $\sigma_{yy}$ acting in $-y$ and $\sigma_{xy}$ acting in $-x$; the inclined face carries the unknowns $\sigma_{x'x'}$ along $x'$ and $\sigma_{x'y'}$ along $y'$. All are drawn positive.

![[s2_wedge_equilibrium.png|900]]

### Equilibrium along the new x axis

The unit vectors are $\hat x'=(\cos\theta,\sin\theta)$ and $\hat y'=(-\sin\theta,\cos\theta)$. Resolving every force along $x'$ and setting the sum to zero:

$$
\sigma_{x'x'}\frac{A}{\cos\theta}=\sigma_{xx}A\cos\theta+\sigma_{xy}A\sin\theta+\sigma_{yy}A\tan\theta\sin\theta+\sigma_{xy}A\tan\theta\cos\theta
$$

Multiply through by $\cos\theta/A$:

$$
\sigma_{x'x'}=\sigma_{xx}\cos^2\theta+\sigma_{xy}\sin\theta\cos\theta+\sigma_{yy}\sin^2\theta+\sigma_{xy}\sin\theta\cos\theta
$$

$$
\boxed{\sigma_{x'x'}=\sigma_{xx}\cos^2\theta+\sigma_{yy}\sin^2\theta+2\sigma_{xy}\sin\theta\cos\theta}
$$

### Equilibrium along the new y axis

Resolving along $y'$:

$$
\sigma_{x'y'}\frac{A}{\cos\theta}=-\sigma_{xx}A\sin\theta+\sigma_{xy}A\cos\theta+\sigma_{yy}A\tan\theta\cos\theta-\sigma_{xy}A\tan\theta\sin\theta
$$

Multiply through by $\cos\theta/A$:

$$
\sigma_{x'y'}=-\sigma_{xx}\sin\theta\cos\theta+\sigma_{xy}\cos^2\theta+\sigma_{yy}\sin\theta\cos\theta-\sigma_{xy}\sin^2\theta
$$

$$
\boxed{\sigma_{x'y'}=-(\sigma_{xx}-\sigma_{yy})\sin\theta\cos\theta+\sigma_{xy}\left(\cos^2\theta-\sin^2\theta\right)}
$$

Setting $\sigma_{yy}=\sigma_{xy}=0$ recovers the bar results of [[#Normal and shear stress on the section]].

### The normal stress on the other face

The normal stress on the face with normal $y'$ is the stress on a face rotated by $\theta+90^\circ$. With $\cos(\theta+90^\circ)=-\sin\theta$ and $\sin(\theta+90^\circ)=\cos\theta$:

$$
\sigma_{y'y'}=\sigma_{xx}\sin^2\theta+\sigma_{yy}\cos^2\theta-2\sigma_{xy}\sin\theta\cos\theta
$$

. Adding it to $\sigma_{x'x'}$, every $\theta$ term cancels through $\sin^2\theta+\cos^2\theta=1$:

$$
\sigma_{x'x'}+\sigma_{y'y'}=\sigma_{xx}+\sigma_{yy}
$$

The sum of the normal stresses is an **invariant**: it does not depend on the orientation.

### What the equations say

Each new stress depends on all three old ones, normal and shear alike. The derivation used only equilibrium, no material law, so the equations hold for any material, and because $\sigma_{zz}$ acts normal to the plane and does not enter the in-plane force balance they hold for plane strain as well as plane stress. The practical difficulty is the angle: draw the surface, draw its normal, and measure $\theta$ from $x$ to that normal, anticlockwise positive.

## 3. Double-angle form

With the identities

$$
\cos^2\theta=\frac{1+\cos2\theta}{2},\qquad \sin^2\theta=\frac{1-\cos2\theta}{2},\qquad 2\sin\theta\cos\theta=\sin2\theta
$$

the normal stress becomes

$$
\sigma_{x'x'}=\sigma_{xx}\frac{1+\cos2\theta}{2}+\sigma_{yy}\frac{1-\cos2\theta}{2}+\sigma_{xy}\sin2\theta
$$

$$
\boxed{\sigma_{x'x'}=\frac{\sigma_{xx}+\sigma_{yy}}{2}+\frac{\sigma_{xx}-\sigma_{yy}}{2}\cos2\theta+\sigma_{xy}\sin2\theta}
$$

and, with $\sin\theta\cos\theta=\tfrac12\sin2\theta$ and $\cos^2\theta-\sin^2\theta=\cos2\theta$, the shear stress becomes

$$
\boxed{\sigma_{x'y'}=-\frac{\sigma_{xx}-\sigma_{yy}}{2}\sin2\theta+\sigma_{xy}\cos2\theta}
$$

The two forms are equivalent; the double-angle form removes the squares, which mattered when angles were looked up in tables, and it leads straight to Mohr's circle.

## 4. Mohr's circle

### Eliminating the angle

Move the average normal stress to the left of the first equation:

$$
\sigma_{x'x'}-\frac{\sigma_{xx}+\sigma_{yy}}{2}=\frac{\sigma_{xx}-\sigma_{yy}}{2}\cos2\theta+\sigma_{xy}\sin2\theta
$$

$$
\sigma_{x'y'}=-\frac{\sigma_{xx}-\sigma_{yy}}{2}\sin2\theta+\sigma_{xy}\cos2\theta
$$

Write $a=(\sigma_{xx}-\sigma_{yy})/2$ for brevity, square both equations and add them. The squared terms give $a^2(\cos^22\theta+\sin^22\theta)$ and $\sigma_{xy}^2(\sin^22\theta+\cos^22\theta)$; the cross terms are $+2a\sigma_{xy}\sin2\theta\cos2\theta$ from the first equation and $-2a\sigma_{xy}\sin2\theta\cos2\theta$ from the second, and cancel:

$$
\left(\sigma_{x'x'}-\frac{\sigma_{xx}+\sigma_{yy}}{2}\right)^2+\sigma_{x'y'}^2=a^2+\sigma_{xy}^2
$$

With

$$
\sigma_{average}=\frac{\sigma_{xx}+\sigma_{yy}}{2},\qquad R=\sqrt{\left(\frac{\sigma_{xx}-\sigma_{yy}}{2}\right)^2+\sigma_{xy}^2}
$$

this is

$$
\boxed{\left(\sigma_{x'x'}-\sigma_{average}\right)^2+\sigma_{x'y'}^2=R^2}
$$

the equation of a circle in the plane of normal stress against shear stress, centred at $(\sigma_{average},0)$ with radius $R$. Since $\theta$ has gone, every orientation of the element gives a point on this circle.

### Constructing the circle

Given $\sigma_{xx}$, $\sigma_{yy}$ and $\sigma_{xy}$ for an element in the $xy$ axes:

1. Draw axes with normal stress positive to the right and **shear stress positive downwards**.
2. Mark $\sigma_{xx}$ and $\sigma_{yy}$ on the normal-stress axis; the centre $\sigma_{average}$ is midway between them.
3. Plot the point $(\sigma_{xx},\sigma_{xy})$, the stresses on the face whose normal is $x$, which is the point for zero rotation, $\theta=0$.
4. Join it to the centre; that length is $R$, by Pythagoras on the horizontal leg $(\sigma_{xx}-\sigma_{yy})/2$ and the vertical leg $\sigma_{xy}$. Draw the circle.

The formula for $R$ squares both legs, so it gives the right radius whatever the signs, provided $\sigma_{xx}-\sigma_{yy}$ is computed with the signs included. Sketching the circle is the quickest check that the centre really lies midway between the two normal stresses.

### Why shear is plotted downwards

The downward shear axis is chosen so that rotating the element anticlockwise turns the point anticlockwise on the page. The proof is short. Write the point relative to the centre as page coordinates $(u,v)$, with $v$ upwards; since shear is plotted downwards, $v=-\sigma_{x'y'}$. From the double-angle equations, with $a=(\sigma_{xx}-\sigma_{yy})/2$,

$$
u=a\cos2\theta+\sigma_{xy}\sin2\theta,\qquad v=a\sin2\theta-\sigma_{xy}\cos2\theta
$$

At $\theta=0$ the point is at $(a,-\sigma_{xy})$; call its page angle $\phi_0$, so $a=R\cos\phi_0$ and $-\sigma_{xy}=R\sin\phi_0$. Substituting,

$$
u=R\left(\cos\phi_0\cos2\theta-\sin\phi_0\sin2\theta\right)=R\cos(\phi_0+2\theta)
$$

$$
v=R\left(\cos\phi_0\sin2\theta+\sin\phi_0\cos2\theta\right)=R\sin(\phi_0+2\theta)
$$

The page angle grows from $\phi_0$ to $\phi_0+2\theta$: an anticlockwise rotation $\theta$ of the element is an anticlockwise rotation $2\theta$ of the point. Textbooks that plot shear upwards get the opposite sense, so check the convention before using another book's figures.

![[s2_mohr_rotation.png|900]]

### The x-face and y-face points

Rotating the element by 90° puts $x'$ along the old $y$ axis and turns the point by 180°, to the opposite end of the diameter. There the normal stress is $\sigma_{yy}$ and the shear is $-\sigma_{xy}$: the physical shear stress has not changed, but on the rotated element it points against the positive direction for that face. So the points for the two faces of any element, $(\sigma_{x'x'},\sigma_{x'y'})$ and $(\sigma_{y'y'},-\sigma_{x'y'})$, are always diametrically opposite, and as the element turns they swing round the circle while the centre stays fixed. That is the invariant $\sigma_{x'x'}+\sigma_{y'y'}$ seen geometrically.

Do not confuse the horizontal axis of the circle with the $x$ axis of the element. A point lies on the horizontal axis only when the face it represents carries no shear.

## 5. Principal stresses and maximum shear

### Principal directions

The circle always crosses the normal-stress axis twice, so every plane stress state has two orientations with no shear stress at all, 180° apart on the circle and therefore 90° apart on the element. These are the **principal directions**; on an element aligned with them there is only stretching or compression, no angular distortion.

### Principal stresses

The normal stresses in the principal directions are the **principal stresses**. The first principal stress $\sigma_I$ is the crossing on the right of the circle and the second $\sigma_{II}$ the crossing on the left, whatever their signs:

$$
\boxed{\sigma_I=\sigma_{average}+R,\qquad \sigma_{II}=\sigma_{average}-R}
$$

### Angle to the principal directions

The rotation from the $x$-face point to $\sigma_I$ is $2\theta_p$ on the circle, in the same sense as the physical rotation $\theta_p$. Setting $\sigma_{x'x'}=\sigma_I$ in the double-angle equation gives $a\cos2\theta_p+\sigma_{xy}\sin2\theta_p=R$, and since $a^2+\sigma_{xy}^2=R^2$ this holds only for

$$
\cos2\theta_p=\frac{\sigma_{xx}-\sigma_{yy}}{2R},\qquad \sin2\theta_p=\frac{\sigma_{xy}}{R}
$$

so that

$$
\tan2\theta_p=\frac{2\sigma_{xy}}{\sigma_{xx}-\sigma_{yy}}
$$

The tangent alone has two solutions 90° apart on the element, one for each principal direction; the signs of the cosine and sine, or a sketch of the circle, show which belongs to $\sigma_I$.

### The principal stress is the extreme normal stress

Differentiate the double-angle form of $\sigma_{x'x'}$:

$$
\frac{d\sigma_{x'x'}}{d\theta}=-(\sigma_{xx}-\sigma_{yy})\sin2\theta+2\sigma_{xy}\cos2\theta
$$

$$
\frac{d\sigma_{x'x'}}{d\theta}=2\sigma_{x'y'}
$$

so the normal stress is stationary exactly where the shear stress vanishes. $\sigma_I$ is the largest in-plane normal stress at the point and $\sigma_{II}$ the smallest, which is why brittle materials, which crack under normal stress, are checked against $\sigma_I$.

### Maximum in-plane shear stress

The largest shear stresses are at the top and bottom of the circle, 90° round from the principal points, so the element is rotated 45° from the principal directions:

$$
\boxed{\sigma_{x'y'}^{max}=\pm R=\pm\frac{\sigma_I-\sigma_{II}}{2}}
$$

On those planes the normal stress is not zero: both faces carry $\sigma_{average}$, the centre of the circle.

### Special cases

| Stress state | Circle | Consequence |
|---|---|---|
| Uniaxial, $\sigma_{xx}$ only | passes through the origin, $R=\sigma_{xx}/2$ | maximum shear $\sigma_{xx}/2$ at 45° with normal stress $\sigma_{xx}/2$ |
| Pure shear, $\sigma_{xy}$ only (torsion) | centred on the origin, $R=\sigma_{xy}$ | $\sigma_{I,II}=\pm\sigma_{xy}$ at 45°: tension along one diagonal, compression along the other |
| Equibiaxial, $\sigma_{xx}=\sigma_{yy}$, $\sigma_{xy}=0$ | a single point | the same normal stress on every plane and no shear anywhere (spherical vessel) |

![[s2_mohr_pure_shear.png|900]]

### Beyond the plane

A 3D stress state has three principal stresses on three mutually perpendicular planes. In plane stress the third is $\sigma_{III}=0$, normal to the plate, and it still matters: two tensile in-plane principal stresses give a larger shear on a plane through the thickness than in the plane. [[FEEG1002 B6 - Yield Criteria|B6]] uses all three.

---

## Worked examples

### Worked example - element at 45 degrees in a bar

A bar carries $\sigma_{xx}=F/A=100$ MPa. The circle has $\sigma_{average}=(100+0)/2=50$ MPa and $R=\sqrt{50^2+0}=50$ MPa, so it passes through the origin and through $\sigma_I=100$ MPa. The top of the circle is 90° anticlockwise from the $x$-face point, so the maximum shear acts on an element rotated 45° anticlockwise, with

$$
\sigma_{x'x'}=50\ \mathrm{MPa},\qquad \sigma_{x'y'}=-50\ \mathrm{MPa}
$$

The negative sign agrees with the bar result $\sigma_{x'y'}=-\sigma_{xx}\sin45^\circ\cos45^\circ$: on that face the shear points down the slope.

![[s2_mohr_uniaxial.png|900]]

### Worked example - rotating a general element

An element carries $\sigma_{xx}=80$, $\sigma_{yy}=20$ and $\sigma_{xy}=30$ MPa (suggested, not lecturer-set). On an element rotated 30° anticlockwise,

$$
\sigma_{x'x'}=80\cos^230^\circ+20\sin^230^\circ+2(30)\sin30^\circ\cos30^\circ=60+5+25.98=91.0\ \mathrm{MPa}
$$

$$
\sigma_{x'y'}=-(80-20)\sin30^\circ\cos30^\circ+30\left(\cos^230^\circ-\sin^230^\circ\right)=-25.98+15=-11.0\ \mathrm{MPa}
$$

$$
\sigma_{y'y'}=80\sin^230^\circ+20\cos^230^\circ-2(30)\sin30^\circ\cos30^\circ=20+15-25.98=9.0\ \mathrm{MPa}
$$

and $91.0+9.0=100=80+20$, as the invariant requires. On the circle, $\sigma_{average}=50$ MPa and $R=\sqrt{30^2+30^2}=42.4$ MPa; the $x$-face point $(80,30)$ sits below the axis, and turning it 60° anticlockwise passes through $\sigma_I=92.4$ MPa (at $2\theta_p=45^\circ$, $\theta_p=22.5^\circ$) and arrives at $(91.0,-11.0)$, just above the axis, as the [[#Why shear is plotted downwards|figure]] shows.

### Worked example - helical weld in a pressure vessel

A thin-walled vessel of diameter 1.2 m and wall 7 mm carries 2 MPa internal pressure. Find the normal and shear stresses on a weld at 60° to the longitudinal axis (Tutorial 4 Q1).

With $x$ along the axis, [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels|B1]] gives

$$
\sigma_{xx}=\frac{pR}{2t}=\frac{(2\times10^6)(0.6)}{2(0.007)}=85.7\ \mathrm{MPa},\qquad \sigma_{yy}=\frac{pR}{t}=171.4\ \mathrm{MPa},\qquad \sigma_{xy}=0
$$

The weld line is at 60° to the axis, so the normal to the weld plane is at $\theta=90^\circ-60^\circ=30^\circ$ to $x$:

$$
\sigma_{x'x'}=85.7\cos^230^\circ+171.4\sin^230^\circ+0=107\ \mathrm{MPa}
$$

$$
\sigma_{x'y'}=-(85.7-171.4)\sin30^\circ\cos30^\circ+0=37.1\ \mathrm{MPa}
$$

On the circle ($\sigma_{average}=128.6$ MPa, $R=42.9$ MPa) the $x$-face point is $\sigma_{II}$ itself, and turning it 60° gives $(128.6-42.9\cos60^\circ,\ 42.9\sin60^\circ)=(107.1,37.1)$. A weld running the other way round the vessel has its normal at $-30^\circ$: the normal stress is the same and the shear stress changes sign, so the magnitude 37.1 MPa is what matters. A longitudinal seam would carry the full 171 MPa hoop stress across it, which is why spiral welding is attractive.

![[s2_mohr_t4_weld.png|900]]

### Worked example - sail element

A sail element carries 4 MPa in $x$ and 1 MPa in $y$, with a 1 MPa shear stress drawn pointing down on the right-hand face and left on the top face (Tutorial 5).

Down on the right-hand face is the negative $y$ direction on a face with positive normal, so $\sigma_{xy}=-1$ MPa. Then

$$
\sigma_{average}=\frac{4+1}{2}=2.5\ \mathrm{MPa},\qquad R=\sqrt{\left(\frac{4-1}{2}\right)^2+(-1)^2}=1.80\ \mathrm{MPa}
$$

$$
\sigma_I=2.5+1.80=4.30\ \mathrm{MPa},\qquad \sigma_{II}=2.5-1.80=0.70\ \mathrm{MPa}
$$

With shear positive downwards, the $x$-face point $(4,-1)$ plots above the axis, so reaching $\sigma_I$ on the right means turning clockwise through $|2\theta_p|=\tan^{-1}(2/3)=33.7^\circ$. The element must be turned clockwise by half that:

$$
\theta_p=-16.8^\circ
$$

> [!check] Substitute back
> $\sigma_{x'x'}(-16.8^\circ)=4(0.9164)+1(0.0836)+2(-1)(-0.2769)=4.30$ MPa, and $\sigma_{x'y'}(-16.8^\circ)=0$ to rounding. Both principal stresses are tensile, so the sail cloth is stretched in every direction and does not wrinkle at this point.

![[s2_mohr_t5_sail.png|900]]

### Worked example - revision element

An element carries $\sigma_{xx}=10$ MPa, $\sigma_{yy}=50$ MPa and a 15 MPa shear stress drawn pointing down on the right-hand face (Tutorial 8 Q4). Find the principal stresses, the maximum in-plane shear stress, the normal stress on the planes of maximum shear and the direction of $\sigma_I$.

The arrow points in $-y$ on the positive $x$-face, so $\sigma_{xy}=-15$ MPa. Then

$$
\sigma_{average}=\frac{10+50}{2}=30\ \mathrm{MPa},\qquad R=\sqrt{\left(\frac{10-50}{2}\right)^2+(-15)^2}=25\ \mathrm{MPa}
$$

$$
\sigma_I=55\ \mathrm{MPa},\qquad \sigma_{II}=5\ \mathrm{MPa},\qquad \sigma_{x'y'}^{max}=25\ \mathrm{MPa}
$$

and both faces of the maximum-shear element carry $\sigma_{average}=30$ MPa. The $x$-face point $(10,-15)$ is above the axis and to the left of the centre, so $\sigma_I$ is reached by going clockwise over the top of the circle. The angle from the point to $\sigma_{II}$ is $\beta=\tan^{-1}(15/20)=36.87^\circ$, so

$$
|2\theta_p|=180^\circ-36.87^\circ=143.1^\circ,\qquad \theta_p=-71.6^\circ
$$

The first principal stress lies 71.6° clockwise from $x$, which is the same line as 108.4° anticlockwise. That is close to the $y$ axis, as expected since $\sigma_{yy}>\sigma_{xx}$.

![[s2_mohr_t8_q4.png|900]]

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 B3 - Generalised Hooke's Law]] · Next: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
- Concepts: [[Stress Transformation Equations]] · [[Mohr's Circle]] · [[Principal Stresses]] · [[Stress Tensor and Stress Element]]
- Worked sheets: [[FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions]] · [[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]] (Q4) · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes|B5]] (the same equations for strain) · [[FEEG1002 B6 - Yield Criteria|B6]] (principal stresses feed the yield criteria) · resolved shear stress on slip planes in [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]
- Year 2: the same transformation and circle for second moments of area, [[Principal Axes of a Section]], in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]] · principal stresses are the eigenvalues of the stress tensor ([[Characteristic Equation and Eigenvalues]]) and the rotation is the rotation-matrix algebra of [[Euler Angles and Rotation Matrices]]

## Sources

- `Lecture 05 - Stresses on Inclined Sections and Stress Transformation.pdf`: Lectures 5a–5b, uniaxial inclined section, joints, wedge equilibrium, transformation equations, applications.
- `Lecture 06 - Mohr's Circle.pdf`: Lectures 6a–6b, double-angle form, circle equation, procedure, rotation, principal directions and stresses, maximum shear.
- `FEEG1002 Lecture 5 - Statics 2 - Stresses on inclinded sections, Stress transformation - Fe.txt` (24 Feb 2025): motivation (ll. 18–56), inclined section of a bar (ll. 57–255), joints (ll. 256–297), the general problem (ll. 298–361), wedge derivation (ll. 362–532), validity and applications (ll. 533–586).
- `FEEG1002 Lecture 6 - Statics 2 - Mohr's circle - March 2025.txt` (3 Mar 2025): double-angle form (ll. 49–123), circle equation (ll. 124–190), construction (ll. 191–297), rotation and opposite faces (ll. 298–408), uniaxial example (ll. 409–482), principal directions and stresses (ll. 483–614), maximum shear (ll. 615–629).
- `FEEG1002 Lecture 9 - Statics 2 - Revision - May 2025 at 10 57 43.txt` (12 May 2025): recap (ll. 296–463).
- Tutorial sheets 4, 5 and 8 (Q4) with solutions.

## Self-study tasks

### Core

- [ ] Tutorial 4 Q1, helical weld (the application flagged at Lecture 5, ll. 556–565; tutorial and quiz problems at ll. 515–518). Targets 107 MPa and 37.1 MPa. → [[#Worked example - helical weld in a pressure vessel]] · [[FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions]]
- [ ] Tutorial 5, sail element (tutorial problems at Lecture 6, ll. 639–641). Targets 4.30 MPa, 0.70 MPa, $-16.8^\circ$. → [[#Worked example - sail element]] · [[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]]
- [ ] Tutorial 8 Q4, revision element. Targets 55, 5 and 25 MPa, $-71.6^\circ$. → [[#Worked example - revision element]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]
- [ ] Derive the transformation equations from the wedge (worked through at Lecture 5, ll. 410–488, "good to understand where it comes from"). → [[#Equilibrium along the new x axis]] · [[#Equilibrium along the new y axis]]

### Further practice

- [ ] Convert to the double-angle form and eliminate $2\theta$ to get the circle, keeping the cross terms (Lecture 6, ll. 65–190). → [[#Eliminating the angle]]
- [ ] Prove that plotting shear downwards makes the circle rotate in the same sense as the element. → [[#Why shear is plotted downwards]]
- [ ] Rotate the 80/20/30 MPa element by 30° by formula and by circle (suggested, not lecturer-set). → [[#Worked example - rotating a general element]]

## Transcript and slide slips

> [!warning] Transcript slip (Lecture 6, l. 356)
> Where: [[#The x-face and y-face points]].
>
> Rotating the element by 90° is described as "we rotate by 180 degrees, the reality, or 90 degrees in Moore's circle". It is the other way round: 90° on the element is 180° on the circle, as stated correctly a few lines earlier (ll. 338–340) and on the slide.
