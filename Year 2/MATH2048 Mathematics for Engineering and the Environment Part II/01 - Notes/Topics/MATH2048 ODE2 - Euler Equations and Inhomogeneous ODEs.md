---
title: "MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 1: Ordinary Differential Equations"
order: 2
tags:
  - math2048
  - odes
  - euler-equation
  - undetermined-coefficients
aliases: ["MATH2048 Lecture 2", "Euler equations", "Undetermined coefficients"]
date: 2026-10-30
status: lectured
coverage: "Lecture 2 (1 Oct 2024, Ian Hawke): Euler equations and the pulsating-star example, the t = ln x substitution, the method of undetermined coefficients and clashes with the complementary function; the correction at the start of Lecture 3. The resonance slide (L3 slide 18) was on the slides but not talked through."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]"]
next_topics: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
key_concepts: ["[[Euler-Cauchy Equation]]", "[[Method of Undetermined Coefficients]]", "[[Resonance]]", "[[Auxiliary Equation]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 2.txt", "02 - Sources/Lectures/MATH2048 Lecture 3.txt (ll. 1-18)", "02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf (slide 18)", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§1.1.1-1.1.2)"]
---

# MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs

> [!abstract] Summary
> Euler equations $ax^2y''+bxy'+cy=0$ have each derivative multiplied by the matching power of $x$, so the guess $y=x^n$ gives the quadratic $an^2+(b-a)n+c=0$; for repeated or complex roots the substitution $t=\ln x$ turns them into constant-coefficient ODEs, which is why repeated roots bring in $\ln x$. Inhomogeneous ODEs are solved as complementary function plus particular integral, with the particular integral found by the method of undetermined coefficients, multiplying the guess by $x$ whenever it clashes with the complementary function.

> [!summary]- Exam use: quick path
> - **Use it when:** an ODE has $x^2y''$, $xy'$ and $y$ terms (Euler, often from polar or spherical coordinates), or has a polynomial, exponential or sine/cosine source.
> - **Assumptions:** Euler equations on $x>0$ (so $x^n$ and $\ln x$ are real); undetermined coefficients needs constant coefficients and a source made of polynomials, exponentials and sines/cosines.
> - **Method:** 1. Solve the homogeneous problem (ODE1 table, or the Euler table in §1). 2. Guess the particular integral from the source (table in §2). 3. If any term of the guess is in the complementary function, multiply by $x$ until it isn't. 4. Substitute and match coefficients. 5. Add complementary function and particular integral, then apply any conditions.
> - **Common mistakes:** writing $bn$ instead of $(b-a)n$ in the Euler auxiliary equation; trying $Ce^{kx}$ when $e^{kx}$ is already a complementary function, which can never balance.
> - **Practise:** [[#Clashes with the complementary function]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q3: Undetermined coefficients|PS1 Q3]]

The lecturer's reason for studying Euler equations is dimensions (L2, ll. 33–69). In $ay''+by'+cy=0$, if $y$ is a temperature and $x$ a length, the three terms have units of temperature per length squared, per length, and temperature, so either $a$, $b$ and $c$ carry units or the equation has been non-dimensionalised. The other way to make the units agree is to multiply each derivative by the matching power of the length itself: $x^2y''$, $xy'$ and $y$ all have the same units, and that is an Euler equation. Cartesian problems tend to give constant-coefficient equations, and cylindrical or spherical ones tend to give Euler equations (or Bessel's), because the radius is the natural length scale.

Because each $x$-derivative of $x^n$ loses one power of $x$, and the equation hands it straight back, a power of $x$ plays the role the exponential played in ODE1. The connection is exact: with $x=e^t$, a power $x^n$ is the exponential $e^{nt}$, so an Euler equation in $x$ is a constant-coefficient equation in $t=\ln x$ in disguise. That one substitution explains both the guess and what to do when the roots repeat.

For a source on the right-hand side, ODE1 showed that any particular integral will do. The method of undetermined coefficients is the quick way to find one: guess a function of the same shape as the source, with unknown coefficients, and let the equation fix them. It covers the sources that turn up in practice, and when it fails the lecturer's advice is to stop and use variation of parameters or computer algebra (ll. 249–255, 408–409).

---

## 1. Euler equations (L2)

The general Euler equation is

$$
ax^2y''+bxy'+cy=0\qquad(x>0,\ a,b,c\ \text{constant}).
$$

Guess a power:

$$
y=x^n.
$$

Each derivative lowers the power by one:

$$
y'=nx^{n-1},\qquad y''=n(n-1)x^{n-2}.
$$

Substitute; the $x^2$ and $x$ in the equation restore the lost powers:

$$
an(n-1)x^n+bnx^n+cx^n=0
$$

$$
\big[an^2+(b-a)n+c\big]x^n=0.
$$

For $x>0$, $x^n\neq0$, so

$$
an^2+(b-a)n+c=0.
$$

This is the Euler auxiliary equation. Compared with the constant-coefficient one, the $n^2$ and constant terms are the same and only the linear coefficient changes, from $b$ to $b-a$ (ll. 85–92). Writing $n(n-1)$ out explicitly before collecting terms is the safest way not to drop the $-a$.

| Roots of $an^2+(b-a)n+c=0$ | General solution |
|---|---|
| real, distinct $n_1\neq n_2$ | $c_1x^{n_1}+c_2x^{n_2}$ |
| real, repeated $n$ | $x^n(c_1+c_2\ln x)$ |
| complex, $\alpha\pm j\beta$ | $x^\alpha\big[c_1\cos(\beta\ln x)+c_2\sin(\beta\ln x)\big]$ |

### The pulsating star

The lecture's example is a model for radial pulsations of a star (ll. 99–108). A spherically symmetric fluid body under its own gravity, pulsing in and out as $e^{j\ell t}$, has a spatial part $X(r)$ satisfying

$$
\frac1r\frac{d^2}{dr^2}\big[rX\big]-\frac{\ell(\ell+1)}{r^2}X=0.
$$

Multiply through by $r^2$:

$$
r\frac{d^2}{dr^2}\big[rX\big]-\ell(\ell+1)X=0.
$$

Expand $(rX)''$ with the product rule twice, which is the step the lecturer went back over at the start of Lecture 3 (L3, ll. 1–18). Once:

$$
(rX)'=X+rX'.
$$

Twice:

$$
(rX)''=X'+X'+rX''=rX''+2X'.
$$

So

$$
r^2X''+2rX'-\ell(\ell+1)X=0,
$$

an Euler equation in $r$ with $a=1$, $b=2$ and $c=-\ell(\ell+1)$. With $X=r^n$ the auxiliary equation is

$$
n^2+(2-1)n-\ell(\ell+1)=0
$$

$$
n^2+n-\ell(\ell+1)=0
$$

$$
(n-\ell)(n+\ell+1)=0,
$$

so $n=\ell$ or $n=-(\ell+1)$, two distinct real roots, and

$$
X(r)=c_1r^\ell+\frac{c_2}{r^{\ell+1}}.
$$

The lecturer used this to make a point that comes back throughout the PDE block: physical conditions can kill whole solutions without any boundary value being given (ll. 154–170). For a star, $r$ runs down to the centre and $X$ must stay finite there, so $c_2=0$. For the field of a charged particle, valid out to $r\to\infty$, it is $c_1$ that must vanish instead. The same pair of powers reappears for Laplace's equation in polar coordinates.

### Repeated or complex roots: the substitution t = ln x

$x^n$ with a complex $n$ is awkward, and it isn't obvious what replaces "multiply by $x$" for a repeated root (ll. 171–179). The answer is to change the independent variable (ll. 181–207). Let

$$
t=\ln x,\qquad x=e^t,\qquad \frac{dt}{dx}=\frac1x,
$$

and write a dot for $d/dt$. The first derivative, by the chain rule:

$$
y'=\frac{dy}{dt}\frac{dt}{dx}=\frac1x\,\dot y,
$$

so

$$
xy'=\dot y.
$$

The second derivative, by the product rule on $\frac1x\cdot\dot y$, remembering that $\dot y$ depends on $x$ through $t$:

$$
y''=\frac{d}{dx}\Big(\frac1x\,\dot y\Big)
$$

$$
=-\frac1{x^2}\dot y+\frac1x\frac{d\dot y}{dt}\frac{dt}{dx}
$$

$$
=-\frac1{x^2}\dot y+\frac1{x^2}\ddot y,
$$

so

$$
x^2y''=\ddot y-\dot y.
$$

Substitute into $ax^2y''+bxy'+cy=0$:

$$
a(\ddot y-\dot y)+b\dot y+cy=0
$$

$$
a\ddot y+(b-a)\dot y+cy=0.
$$

This is a constant-coefficient ODE in $t$, and its auxiliary equation $a\lambda^2+(b-a)\lambda+c=0$ is the Euler auxiliary equation with $\lambda=n$. Solve in $t$ with the ODE1 table and convert back: $e^{nt}=x^n$, $te^{nt}=x^n\ln x$ and $e^{\alpha t}\cos\beta t=x^\alpha\cos(\beta\ln x)$. That is where the Euler table comes from, and it is also why the guess $x^n$ works at all (ll. 208–215). The final answer has to be in $x$; stopping at $y(t)$ loses marks.

In practice, try the auxiliary equation first and hope for real roots, distinct or repeated, multiplying by $\ln x$ rather than $x$ for a repeated root: "for 99% of engineering and mathematical physics problems, those are the solutions you're going to get anyway" (ll. 228–230). Only complex roots force the full substitution.

### Two worked Euler equations

The slide example has a repeated root (ll. 216–225): $x^2y''+3xy'+y=0$ gives

$$
n(n-1)+3n+1=n^2+2n+1=(n+1)^2=0,
$$

so $n=-1$ twice. In $t$ the equation is $\ddot y+2\dot y+y=0$, with solution $(c_1+c_2t)e^{-t}$, and converting back,

$$
y=\frac{c_1+c_2\ln x}{x}.
$$

*(Suggested, not lecturer-set.)* For complex roots, take $x^2y''+xy'+4y=0$. The auxiliary equation is $n(n-1)+n+4=n^2+4=0$, so $n=\pm2j$, with $\alpha=0$ and $\beta=2$. In $t$ it is $\ddot y+4y=0$, so $y=c_1\cos2t+c_2\sin2t$, and in $x$

$$
y=c_1\cos(2\ln x)+c_2\sin(2\ln x).
$$

> [!check] Checking $y_1=\cos(2\ln x)$ directly
> $y_1'=-\frac2x\sin(2\ln x)$ and $y_1''=\frac2{x^2}\sin(2\ln x)-\frac4{x^2}\cos(2\ln x)$, so $x^2y_1''+xy_1'+4y_1=(2\sin-4\cos)-2\sin+4\cos=0$. SymPy's `dsolve` gives the same general solution for both examples.

## 2. Inhomogeneous ODEs: complementary function plus particular integral

For $y''+py'+qy=r(x)$ the procedure has three steps (ll. 259–274):

1. Ignore the source and solve the homogeneous equation for the **complementary functions** $y_1$, $y_2$.
2. Find any **particular integral** $y_P$ that satisfies the full equation.
3. The general solution is $y=c_1y_1+c_2y_2+y_P$; only then apply initial or boundary conditions.

ODE1 showed that $y-y_P$ satisfies the homogeneous equation, so every solution has this form and none is missed. It also follows that it doesn't matter which particular integral you find: two of them differ by a solution of the homogeneous equation, which the constants $c_1$, $c_2$ absorb.

### The method of undetermined coefficients

Guess a particular integral of the same form as the source, with unknown coefficients, substitute, and match terms (ll. 264–274). The logic is balancing: a guess $Ax+B$ against a source $4x$ works because differentiating a polynomial gives lower powers, so the $Ax$ can balance the $4x$ and the $B$ can absorb the constant that differentiation produces, whereas a guess $x^2$ would leave an $x^2$ term with nothing on the right to balance it (ll. 289–318). An exponential differentiates into itself, so $Ce^{kx}$ balances $e^{kx}$ (ll. 319–328).

| Source $r(x)$ | Guess for $y_P$ |
|---|---|
| polynomial of degree $n$ | general polynomial of degree $n$, $A_nx^n+\dots+A_0$ |
| $e^{kx}$ | $Ce^{kx}$ |
| $\sin\omega x$ or $\cos\omega x$ | $C\sin\omega x+D\cos\omega x$ (always both) |
| $e^{kx}\sin\omega x$ or $e^{kx}\cos\omega x$ | $e^{kx}(C\sin\omega x+D\cos\omega x)$ |
| $x^ne^{kx}$ | $(A_nx^n+\dots+A_0)e^{kx}$ |
| a sum of the above | the sum of the guesses |

Sensible guesses exist only for polynomials, exponentials and simple trigonometric functions, the last being exponentials in disguise through Euler's formula. For logarithms, fractional powers and the like, "forget it" (ll. 410–420).

### The lecture example

Solve $y''+4y'+4y=4x+25e^{3x}$ (ll. 256–367).

The complementary functions come from $\lambda^2+4\lambda+4=(\lambda+2)^2=0$, a repeated root $\lambda=-2$:

$$
y_1=e^{-2x},\qquad y_2=xe^{-2x}.
$$

The source is a first-degree polynomial plus $e^{3x}$, neither of which appears in the complementary function, so guess

$$
y_P=Ax+B+Ce^{3x}.
$$

Differentiate:

$$
y_P'=A+3Ce^{3x},\qquad y_P''=9Ce^{3x}.
$$

Substitute:

$$
y_P''+4y_P'+4y_P=9Ce^{3x}+4(A+3Ce^{3x})+4(Ax+B+Ce^{3x})
$$

$$
=4Ax+4(A+B)+(9+12+4)Ce^{3x}
$$

$$
=4Ax+4(A+B)+25Ce^{3x}.
$$

Match to $4x+0+25e^{3x}$ term by term. From $x^0$: $4(A+B)=0$, so $B=-A$. From $x^1$: $4A=4$, so $A=1$ and $B=-1$. From $e^{3x}$: $25C=25$, so $C=1$. Hence

$$
y_P=x-1+e^{3x},
$$

and the general solution is

$$
y=(c_1+c_2x)e^{-2x}+x-1+e^{3x}.
$$

The lecturer pointed out that the answer can be spotted, but matching term by term is the habit that works when it can't (ll. 341–343). SymPy confirms that $y_P$ reproduces $4x+25e^{3x}$ exactly.

### Clashes with the complementary function

The complementary function is found first because it decides the guess (ll. 371–409). If the natural guess is already a complementary function, substituting it gives zero, so it can never balance the source; the fix is to multiply the guess by successive powers of $x$. Keeping the same left-hand side, with complementary functions $e^{-2x}$ and $xe^{-2x}$, the slide gives two clashing sources.

For $r=e^{-2x}$, both $Ce^{-2x}$ and $Cxe^{-2x}$ are complementary functions, so the first guess worth trying is $y_P=Cx^2e^{-2x}$. Differentiate:

$$
y_P'=C(2x-2x^2)e^{-2x},
$$

$$
y_P''=C(2-4x-4x+4x^2)e^{-2x}=C(2-8x+4x^2)e^{-2x}.
$$

Substitute:

$$
y_P''+4y_P'+4y_P=C\big[(2-8x+4x^2)+(8x-8x^2)+4x^2\big]e^{-2x}
$$

$$
=2Ce^{-2x},
$$

so $2C=1$, $C=\tfrac12$ and $y_P=\tfrac12x^2e^{-2x}$.

For $r=xe^{-2x}$, the natural guess is $(Ax+B)e^{-2x}$, and multiplying by $x^2$ removes the clash: $y_P=(Ax^3+Bx^2)e^{-2x}$. The shortcut below shows that only the cubic is needed, $y_P=\tfrac16x^3e^{-2x}$. The slide tries $Cx^2e^{-2x}$ first and finds it fails, then $Cx^3e^{-2x}$, which works.

The third slide source, $\log(\sin x^{3/4})$, has no sensible guess, and undetermined coefficients doesn't apply. Variation of parameters, $y_P=v_1y_1+v_2y_2$ with $v_1'=-ry_2/W$ and $v_2'=ry_1/W$, works for any $r$ but is long and not examinable.

The lecturer's practical rule is to give up after two failed guesses: for a second-order equation you may need up to $x^2$ times the guess, and checking each one by hand is tedious, so "go straight to computer algebra. It is not worth your time" (ll. 403–409).

### Why the powers of x work

*(Suggested, not lectured; it explains the clash rule.)* Put $y=u(x)e^{kx}$ into $y''+by'+cy$. Differentiate:

$$
y'=(u'+ku)e^{kx},
$$

$$
y''=(u''+2ku'+k^2u)e^{kx}.
$$

Substitute and collect:

$$
y''+by'+cy=\big[u''+(2k+b)u'+(k^2+bk+c)u\big]e^{kx}.
$$

The coefficient of $u$ is the auxiliary polynomial evaluated at $k$, which vanishes when $k$ is a root, so a constant $u$ (a plain $Ce^{kx}$) gives zero. The coefficient of $u'$ is that polynomial's derivative at $k$, which also vanishes when $k$ is a repeated root, leaving just $u''$. For $y''+4y'+4y$ with $k=-2$ both vanish, so the equation for $u$ is simply $u''=$ (source $\times e^{2x}$). For $r=e^{-2x}$ that is $u''=1$, giving $u=\tfrac12x^2$; for $r=xe^{-2x}$ it is $u''=x$, giving $u=\tfrac16x^3$. That is exactly why $x^2e^{-2x}$ fails for the second source: it gives $2e^{-2x}$, not anything proportional to $xe^{-2x}$.

### Resonance (L3 slide 18)

Lecture 2's slides end with a challenge, to explain the 1940 Tacoma Narrows bridge collapse, and the answer is the last slide of Lecture 3; neither was talked through in the recordings. An undamped oscillator driven at frequency $\omega_s$ obeys

$$
\ddot y+\omega_0^2y=\cos\omega_st,
$$

with complementary function $c_1\cos\omega_0t+c_2\sin\omega_0t$. If $\omega_s\neq\omega_0$ there is no clash, and the guess $y_P=A\cos\omega_st$ (no sine is needed because there is no $\dot y$ term) gives

$$
\ddot y_P+\omega_0^2y_P=A(\omega_0^2-\omega_s^2)\cos\omega_st,
$$

so $A=1/(\omega_0^2-\omega_s^2)$: a bounded response that grows as the forcing approaches the natural frequency. At $\omega_s=\omega_0$ the guess clashes, so multiply by $t$:

$$
y_P=t(A\cos\omega_0t+B\sin\omega_0t).
$$

Differentiate:

$$
\dot y_P=(A\cos\omega_0t+B\sin\omega_0t)+t\omega_0(-A\sin\omega_0t+B\cos\omega_0t),
$$

$$
\ddot y_P=2\omega_0(-A\sin\omega_0t+B\cos\omega_0t)-t\omega_0^2(A\cos\omega_0t+B\sin\omega_0t).
$$

The $t$ terms cancel against $\omega_0^2y_P$, leaving

$$
\ddot y_P+\omega_0^2y_P=2\omega_0(-A\sin\omega_0t+B\cos\omega_0t)=\cos\omega_0t,
$$

so $A=0$, $B=1/(2\omega_0)$ and

$$
y_P=\frac{t}{2\omega_0}\sin\omega_0t.
$$

The amplitude grows linearly in time, which is resonance.

![[m2048_ode_resonance.png|640]]

## Transcript slips

> [!warning] Lecture 2 slips
> | Where | Transcript says | Correct |
> |---|---|---|
> | L2, ll. 113–121 | expands $r(rX)''$ wrongly, then patches it on the slide | $r^2X''+2rX'-\ell(\ell+1)X=0$; the lecturer redid the product rule at the start of L3 (ll. 1–18) |
> | L2, l. 149 | roots "L or alternatively minus L plus 1" | $n=\ell$ or $n=-(\ell+1)$; the slide writes $c_2/r^{\ell+1}$ |
> | L2, l. 278 | "y double prime plus 4y prime plus 4y prime" | $y''+4y'+4y=0$ |
> | L2, ll. 401–402 | for the source $xe^{-2x}$, $x^2e^{-2x}$ "vanishes again on the left hand side but I'm not 100% sure" | it gives $2e^{-2x}$, not zero; it fails because it can't produce an $x e^{-2x}$ term |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · Next: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]
- The particular-integral idea for PDEs: [[MATH2048 PDE4 - Inhomogeneous PDEs and Inhomogeneous Boundary Conditions]]
- Concepts: [[Euler-Cauchy Equation]] · [[Method of Undetermined Coefficients]] · [[Resonance]] · [[Auxiliary Equation]]

## Sources

- Lecture 2 recording, 1 Oct 2024 (Ian Hawke): `MATH2048 Lecture 2.txt`; correction at the start of Lecture 3 (`MATH2048 Lecture 3.txt`, ll. 1–18)
- Slides `Lecture2_ODE.pdf`; `Lecture3_ODE.pdf` slide 18 (resonance)
- Appendix to Lectures 1–2; lecture notes §1.1.1–1.1.2
- Problem Sheet 1 Q2–Q3; worked solutions in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]

## Self-study tasks

Lecture 2 set the Tacoma Narrows challenge on its last slide and otherwise pointed to Problem Sheet 1 and the STACK practice quizzes.

### Core

- [ ] Derive $x^2y''=\ddot y-\dot y$ and $xy'=\dot y$ for $t=\ln x$, and hence the constant-coefficient form $a\ddot y+(b-a)\dot y+cy=0$ (L2, ll. 183–203). → [[#Repeated or complex roots: the substitution t = ln x]]
- [ ] PS1 Q2(a)–(c), one Euler equation of each root type. Answers: $c_1x^3+c_2x^{-2}$; $x^{-1}[c_1\cos(3\ln x)+c_2\sin(3\ln x)]$; $x^{-2}(c_1+c_2\ln x)$. → [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]
- [ ] PS1 Q3(a)–(c), undetermined coefficients with clashes. Answers: $y_P=2x^2e^x$; $y_P=-2xe^x\cos x$; $y_P=\tfrac16x^3e^{2x}$. → [[MATH2048 Problem Sheets 1-2 Solutions - ODEs#Q3: Undetermined coefficients]]

### Further practice

- [ ] Lecturer-set challenge (L2 slide 16): explain the Tacoma Narrows collapse, then derive $y_P=\frac{t}{2\omega_0}\sin\omega_0t$. → [[#Resonance (L3 slide 18)]]
- [ ] Find $y_P$ for $y''+4y'+4y=xe^{-2x}$ and show why $Cx^2e^{-2x}$ fails (suggested, not lecturer-set). → [[#Why the powers of x work]]
- [ ] Solve the pulsating-star equation and say which constant vanishes for a star and which for a point charge (L2, ll. 154–170). → [[#The pulsating star]]
