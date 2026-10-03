---
title: "Energy Ledgers for Forced Harmonic ODEs"
subtitle: "Kirchhoff power balance and an unknown component with X = LRC"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-02"
abstract: |
  Multiplying a forced harmonic LRC equation by current turns its voltage
  balance into a power balance. Opposite entries identify the heat and source
  equations needed for a complete energy ledger; their remaining terms are
  left open. We then add the fictional voltage term $Xq'''$, with $X>0$ and
  its physical identity unknown. The sign of its power determines whether
  it supplies or absorbs energy. Exact numerical examples show both cases.
  Assuming only the coefficient relation $X=LRC$, we check the units
  and compare how component choices strengthen either contribution to the
  circuit's power equation. Rotary impact and hand-hammer examples connect
  the model to familiar mechanics, distinguishing useful assistance, losses,
  support movement and the unknown cost of supplying the fictional component.
keywords:
  - Kirchhoff voltage law
  - harmonic ordinary differential equations
  - power balance
  - energy accounting
  - unknown component
  - rotary impact driver
  - hammer and nail
---

\begingroup\scriptsize
\noindent PDF created: \pdfbuildtimestamp\par
\noindent Latest on GitHub: \url{https://github.com/hobnilre/physics-ode-energy}\par
\endgroup

# Kirchhoff's voltage law and the missing accounts

Consider the forced harmonic equation for a series LRC circuit,
\begin{equation}
Lq''+Rq'+\frac qC=f(t),
\qquad L>0,\quad C>0,\quad R\geq0.
\label{eq:base}
\end{equation}
Here $q$ is charge, $L$ is inductance, $R$ is resistance, $C$ is capacitance,
and $f(t)$ is the applied voltage. Coefficients are constant and trajectories
are smooth. The equation is second order because its highest derivative is
$q''$; it is linear and has degree one in that derivative.

Every term in \eqref{eq:base} is a voltage. The component laws are
$v_L=Lq''$, $v_R=Rq'$, and $v_C=q/C$. Kirchhoff's voltage law, written with
the source first, is
\begin{equation}
f(t)-Lq''-Rq'-\frac qC=0.
\label{eq:kvl}
\end{equation}
Once the ODE is solved, we have $q(t)$ and $q'(t)$. The series current is
$i=q'$. Multiplication by that current turns the voltage law into a
*power law*:
\begin{equation}
f(t)i-Lq''i-Rq'i-\frac{qi}{C}=0.
\label{eq:base-power}
\end{equation}
Each term is now voltage times current, measured in watts. The forcing
contributes $+fi$ to this equation; resistor absorption contributes
$-Rq'i=-Ri^2$.

The power sum is zero. To relate it to constant total energy, include the
heat recipient and the forcing source or sink:
\begin{equation}
\left\{
\begin{aligned}
1:\quad &\cdots+Rq'i+\cdots=0,\\
2:\quad &f(t)i-Lq''i-Rq'i-qi/C=0,\\
3:\quad &-f(t)i+\cdots=0.
\end{aligned}
\right.
\label{eq:three-rows}
\end{equation}
The first line belongs to the heat recipient and the third to the forcing
source or sink. Their full ODEs are unknown, but one transfer term in each
is already determined. The heat entry $-Rq'i$ in line 2 has the matching
$+Rq'i$ in line 1. The source entry $+fi$ in line 2 has the matching
$-fi$ in line 3.

This is the energy counterpart of double-entry economic accounting: a
transfer debits one account and credits another. If $fi<0$, the forcing
source receives energy, and those entries reverse direction.

The cancellation identifies the transfers needed for a complete ledger.
A proof that total energy is constant also requires the omitted terms,
including the relevant energy rates and physical reservoir laws. We leave
those blanks open here; completing them is a separate article. A prescribed
$f(t)$ alone does not specify a source's available energy.

# Does the unknown term $Xq'''$ supply or absorb power?

## The fourth line and the direction of transfer

Add one fictional component term, with constant $X>0$:
\begin{equation}
Xq'''+Lq''+Rq'+\frac qC=f(t).
\label{eq:third}
\end{equation}
Its physical identity is unknown. Its proposed voltage contribution is
$v_X=Xq'''$. The power equation and its matching entries become
\begin{equation}
\left\{
\begin{aligned}
1:\quad &\cdots+Rq'i+\cdots=0,\\
2:\quad &f(t)i-Xq'''i-Lq''i-Rq'i-qi/C=0,\\
3:\quad &-f(t)i+\cdots=0,\\
4:\quad &\cdots+Xq'''i+\cdots=0.
\end{aligned}
\right.
\label{eq:four-rows}
\end{equation}
The fourth line carries the opposite of the new contribution in line 2.
Define the two signed powers explicitly:
\begin{equation}
P_X=Xq'''i
\quad\text{(received by \(X\))},\qquad
P_{X\to2}=-Xq'''i
\quad\text{(contribution to line 2)}.
\label{eq:x-powers}
\end{equation}

| Sign of $q'''i$ | $P_X$ | $P_{X\to2}$ | Role of $X$ |
| :--- | :--- | :--- | :--- |
| Negative | Negative | Positive | Supplier |
| Positive | Positive | Negative | Absorber |
| Zero | Zero | Zero | No instantaneous transfer |

: Direction follows from the derivative product because $X>0$.

For example, positive current together with negative $q'''$ makes $X$ a
supplier. Positive current together with positive $q'''$ makes it an
absorber. A positive coefficient alone does not select either role.

Energy transfer follows from the signed power integral:
\begin{equation}
W_X(t_0,t_1)=\int_{t_0}^{t_1}Xq'''(t)i(t)\,dt,
\qquad W_{X\to2}=-W_X.
\label{eq:x-work}
\end{equation}
Positive $W_X$ is net energy received by $X$; negative $W_X$ is net energy
supplied by it. This specifies the required transfer while leaving the
remaining terms of line 4 open.

## Two numerical examples from exact trajectories

Take the illustrative values
$L=1\,\mathrm H$, $R=1\,\Omega$, $C=1\,\mathrm F$, and
$X=1\,\mathrm{H\,s}$. Put $u=t/(1\,\mathrm s)$.
In each example choose $q(t)$ and obtain the required $f(t)$ by substitution
into \eqref{eq:third}.

**Supplier.** Choose
\begin{equation}
q(t)=(1\,\mathrm C)\sin u,\qquad
i(t)=(1\,\mathrm A)\cos u,\qquad
q'''(t)=-(1\,\mathrm{A/s^2})\cos u.
\label{eq:supplier}
\end{equation}
The inductive and capacitive voltages cancel, as do the resistive and
$X$ voltages, so the required forcing is $f(t)=0$. The two powers are
\begin{equation}
P_X=-(1\,\mathrm W)\cos^2u,\qquad
P_{X\to2}=+(1\,\mathrm W)\cos^2u.
\label{eq:supplier-power}
\end{equation}
At $t=0$, $X$ contributes $+1\,\mathrm W$ to line 2.
Over the exact period $T=2\pi\,\mathrm s$,
\begin{equation}
W_X=-(1\,\mathrm J)\int_0^{2\pi}\cos^2u\,du=-\pi\,\mathrm J.
\label{eq:supplier-work}
\end{equation}
Thus $X$ supplies $\pi\,\mathrm J$ during the cycle. Here $P_X=-Ri^2$
pointwise, so the required transfer pays for the resistor's absorption.
The equation identifies the required debit in the unknown account; it
does not specify what physically supplies that energy.

**Absorber.** On $0\leq t\leq1\,\mathrm s$, choose
\begin{equation}
q(t)=(1\,\mathrm C)\frac{u^3}{6},\qquad
i(t)=(1\,\mathrm A)\frac{u^2}{2},\qquad
q'''(t)=1\,\mathrm{A/s^2}.
\label{eq:absorber}
\end{equation}
Direct substitution gives
\begin{equation}
f(t)=(1\,\mathrm V)\left(1+u+\frac{u^2}{2}+\frac{u^3}{6}\right).
\label{eq:absorber-forcing}
\end{equation}
Now $P_X=(1\,\mathrm W)u^2/2>0$ for $t>0$, so $X$ absorbs power.
At $t=1\,\mathrm s$, its contribution to line 2 is
$P_{X\to2}=-1/2\,\mathrm W$. Its received energy is
\begin{equation}
W_X=(1\,\mathrm J)\int_0^1\frac{u^2}{2}\,du=\frac16\,\mathrm J.
\label{eq:absorber-work}
\end{equation}
The same positive $X$ therefore supplies energy on the sinusoid and absorbs
energy on the polynomial trajectory. Both examples are exact substitutions
and evaluated power integrals.

\newpage

# Choosing $L$, $R$ and $C$ when $X=LRC$

## Units and what the coefficient determines

Assume only that the numerical value of the coefficient is given by
\begin{equation}
X=LRC>0.
\label{eq:coefficient}
\end{equation}
Consequently $R>0$ in this part. The identity and mechanism of $X$ remain
unknown. The relation determines its coefficient value, including units.

Since $\Omega\,\mathrm F=\mathrm s$, the dimensional check is
\begin{equation}
[X]=[LRC]=\mathrm{H\,s}
=\frac{\mathrm{V\,s^2}}{\mathrm A},
\qquad
[q''']=\frac{\mathrm A}{\mathrm{s^2}},
\qquad [Xq''']=\mathrm V.
\label{eq:units}
\end{equation}
Thus the new term is a voltage, and its contribution to line 2 is
\begin{equation}
P_{X\to2}=-LRC\,q'''i.
\label{eq:linked-power}
\end{equation}

## Maximizing the supplying or absorbing contribution

First hold the trajectory $q(t)$ fixed, including the time scale and
amplitude. Then the derivative product $q'''i$ is fixed at each instant.
Equation \eqref{eq:linked-power} gives the two design cases directly:

| Objective at an instant | Required trajectory sign | Magnitude to maximize |
| :--- | :--- | :--- |
| Supply power to line 2 | $q'''i<0$ | $LRC(-q'''i)$ |
| Absorb power from line 2 | $q'''i>0$ | $LRC(q'''i)$ |

: At fixed trajectory, both magnitudes increase with the product $LRC$.

Increasing any of $L$, $R$, or $C$ strengthens the existing direction of
transfer. Positive component choices cannot reverse that direction for the
same trajectory. With independent positive bounds on the three components,
the largest product uses all three upper bounds. Without such bounds there
is no finite maximum. The signed work in \eqref{eq:x-work} scales in the
same way when the trajectory and interval are fixed.

For the sinusoidal family $q=Q\sin(\omega t)$, where $Q>0$ is charge
amplitude and $\omega>0$ is angular frequency,
\begin{equation}
q'''=-\omega^2 i,\qquad
P_{X\to2}=LRC\,\omega^2 i^2\geq0.
\label{eq:sinusoidal-sign}
\end{equation}
Every positive choice of $L,R,C$ therefore makes $X$ a supplier on this
trajectory, except at current zeros. Absorption requires a trajectory with
$q'''i>0$, such as the polynomial in \eqref{eq:absorber}; changing positive
coefficients alone cannot produce it on the sinusoid.

If “effect” instead means magnitude relative to the resistor's absorption,
then, at $i\ne0$,
\begin{equation}
\frac{|P_{X\to2}|}{Ri^2}
=LC\left|\frac{q'''}{i}\right|.
\label{eq:relative}
\end{equation}
At fixed trajectory, larger $L$ or $C$ increases this ratio. Larger $R$
increases both powers equally and leaves the ratio unchanged. On a sinusoid
the ratio is $LC\omega^2$.

\newpage

## Numerical comparison in both roles

Use the two trajectories from Part 2. Compare the supplier at $t=0$ and
the absorber at $t=1\,\mathrm s$. For each component choice, recompute
$f(t)$ from \eqref{eq:third} so that the specified trajectory is retained.

| $(L,R,C)$ in $(\mathrm H,\Omega,\mathrm F)$ | $X$ ($\mathrm{H\,s}$) | Supplier ($\mathrm W$) | Absorber ($\mathrm W$) |
| :--------------------------- | --------------: | ------------------: | ------------------: |
| $(1,1,1)$ | $1$ | $+1$ | $-1/2$ |
| $(1,2,1)$ | $2$ | $+2$ | $-1$ |
| $(2,2,2)$ | $8$ | $+8$ | $-4$ |

: Exact signed contributions $P_{X\to2}$ of the unknown term.

For example, with independent bounds
$1\,\mathrm H\leq L\leq2\,\mathrm H$,
$1\,\Omega\leq R\leq2\,\Omega$, and
$1\,\mathrm F\leq C\leq2\,\mathrm F$, the last choice maximizes both
directional magnitudes for the specified trajectories. It supplies
$8\,\mathrm W$ at the supplier instant and absorbs $4\,\mathrm W$ at the
absorber instant. Over their respective intervals, the same exact integrals
give $8\pi\,\mathrm J$ supplied during the sinusoidal cycle and
$4/3\,\mathrm J$ absorbed during the polynomial interval.

These comparisons hold the motion fixed and adjust the forcing accordingly.
If $f(t)$ and the initial conditions are held fixed instead, changing
$L,R,C$ also changes $q(t)$; maximizing the product alone then does not
determine the maximum effect. The coefficient relation specifies the power
required of $X$ on a chosen motion. Its physical identity and the remaining
terms of line 4 are still open.

\newpage

# The same equation in a rotary impact driver

## A simplified output model

A rotary impact driver uses a motor to accelerate a hammer, which transfers
torque to an anvil and then to the bit and fastener. Established hammer
models distinguish acceleration, contact and release, with joint stiffness
and losses affecting the blow ([Wettstein et al., 2021][wettstein]). Here we
retain one smooth loading interval within a blow.

Let $\theta(t)$ be the output's angular displacement from a fixed local
reference, and $\Omega=\theta'$ its angular velocity. Use constant output
inertia $J>0$, resisting coefficient $b>0$, and torsional stiffness $k>0$.
The resisting torques are $b\Omega$ and $k\theta$. The hammer applies a
prescribed torque $\tau_h(t)$; its inertia is outside this output model and
is not included in $J$. Torque balance gives
\begin{equation}
J\theta''+b\theta'+k\theta=\tau_h(t).
\label{eq:rotary-base}
\end{equation}
This is the original harmonic ODE under the correspondence
$$
q\leftrightarrow\theta,\quad i\leftrightarrow\Omega,\quad
L\leftrightarrow J,\quad R\leftrightarrow b,\quad
C\leftrightarrow1/k,\quad f\leftrightarrow\tau_h.
$$
The spring and damping laws define a local ideal model. Contact switching,
successive blows and permanent fastener advance require additional laws.

Now assume that the fictional component exists somewhere inside the tool
and acts at this output. Write its rotational coefficient as $X_r$:
\begin{equation}
X_r\theta'''+J\theta''+b\theta'+k\theta=\tau_h(t),
\qquad X_r=\frac{Jb}{k}>0.
\label{eq:rotary-third}
\end{equation}
The relation is the rotational counterpart of $X=LRC$. Since $b/k$ has
units of seconds,
$$
[X_r]=\mathrm{N\,m\,s^3/rad}=\mathrm{kg\,m^2\,s},
\qquad [X_r\theta''']=\mathrm{N\,m},
$$
where radians are dimensionless in SI. Its coefficient is known; its
physical mechanism remains unspecified.

Multiplication by $\Omega$ gives the same source-first power equation:
\begin{equation}
\tau_h\Omega-X_r\theta'''\Omega-J\theta''\Omega
-b\Omega^2-k\theta\Omega=0.
\label{eq:rotary-power}
\end{equation}
The component receives $P_{X_r}=X_r\theta'''\Omega$, with the opposite
entry in this equation. It supplies power when $\theta'''\Omega<0$ and
absorbs when $\theta'''\Omega>0$. The heat and hammer accounts likewise
receive $+b\Omega^2$ and $-\tau_h\Omega$, as in the earlier ledger.

\newpage

## Comparing the work on the same motion

Hold the trajectory and interval fixed and calculate the required hammer
torque separately for the ordinary model and the model containing $X_r$.
Call these torques $\tau_0$ and $\tau_X$. Their difference is
$\tau_X-\tau_0=X_r\theta'''$. Integrating their signed port powers gives
\begin{equation}
W_h^{(X)}-W_h^{(0)}
=\int_{t_0}^{t_1}(\tau_X-\tau_0)\Omega\,dt
=\int_{t_0}^{t_1}X_r\theta'''\Omega\,dt=W_{X_r},
\label{eq:rotary-work-difference}
\end{equation}
where each $W_h$ is work delivered by the hammer to the output.
Thus supplying reduces the required hammer work by exactly the work
supplied by $X_r$. Absorbing increases it on the same motion; absorption
can instead serve a braking objective when the derivative product has the
required sign. Returning that absorbed energy later needs a component law.

For a concrete comparison, choose the smooth loading segment
\begin{equation}
\theta(t)=\Theta\sin(\nu t),\qquad
0\leq t\leq\frac{\pi}{2\nu},\qquad \Theta>0,\quad\nu>0.
\label{eq:rotary-motion}
\end{equation}
The angle increases while the output slows to rest. All comparisons start
with the same nonzero angular velocity $\Theta\nu$ and end at the same
angle $\Theta$. Since $\theta'''=-\nu^2\Omega$, $X_r$ supplies throughout
the moving part. Its signed work and the heat transfer are
\begin{align}
W_{X_r}&=\int_0^{\pi/(2\nu)}X_r\theta'''\Omega\,dt
=-\frac{\pi}{4}X_r\Theta^2\nu^3,\label{eq:rotary-x-work}\\
W_b&=\int_0^{\pi/(2\nu)}b\Omega^2\,dt
=\frac{\pi}{4}b\Theta^2\nu.\label{eq:rotary-heat}
\end{align}
On this trajectory, the required torque is also obtained by an ordinary
model with reduced damping
\begin{equation}
b_{\mathrm{eff}}=b-X_r\nu^2
=b\left(1-\frac{J\nu^2}{k}\right),
\qquad b_{\mathrm{eff}}\geq0.
\label{eq:rotary-effective-damping}
\end{equation}
Indeed, $X_r\theta'''+b\Omega=b_{\mathrm{eff}}\Omega$.
This equality concerns the chosen motion. In the fictional model the
original heat transfer remains and $X_r$ supplies the difference. In the
ordinary model less work becomes heat.

Take the following exact illustrative values; they are not measurements of a driver:
$$
J=10^{-4}\,\mathrm{kg\,m^2},\quad
b=\frac1{50}\,\mathrm{N\,m\,s/rad},\quad
k=1000\,\mathrm{N\,m/rad},\quad
\Theta=\frac1{10}\,\mathrm{rad},\quad\nu=1000\,\mathrm{s^{-1}}.
$$
Then $X_r=2\cdot10^{-9}\,\mathrm{kg\,m^2\,s}$,
$J\nu^2/k=1/10$, and $b_{\mathrm{eff}}=9/500\,\mathrm{N\,m\,s/rad}$.

| Model on the same motion | Heat ($\mathrm J$) | $W_{X_r}$ ($\mathrm J$) | $\Delta W_h$ ($\mathrm J$) |
| :----------------------------- | ---------: | ---------: | ---------: |
| Ordinary, original $b$ | $\pi/20$ | $0$ | $0$ |
| Fictional, original $b$ | $\pi/20$ | $-\pi/200$ | $-\pi/200$ |
| Ordinary, $b$ reduced by $10\%$ | $9\pi/200$ | $0$ | $-\pi/200$ |

: Exact transfers; $\Delta W_h$ is the change in hammer work relative to the first model.

\newpage

## How much conventional effort can $X_r$ replace?

An effective driver reaches a specified tightening target with less battery
work and time, within torque, vibration and wear limits. Conventional
mechanical design adjusts hammer preparation and contact with the anvil
([Wettstein et al., 2021][wettstein]); control adjusts motor effort and
impact timing ([Benazet et al., 2026][benazet]). The replacement by $X_r$
can be stated more precisely at our output boundary.

**During the useful motion, it can replace part of the hammer input.**
In the worked example, $X_r$ supplies $\pi/200\,\mathrm J$, so the hammer
can deliver exactly that much less work while retaining the same motion.
Its assisting torque is $1/5\,\mathrm{N\,m}$ at the start and falls to
zero at the end. The ordinary hammer work, evaluated from its port power, is
\begin{equation}
W_h^{(0)}=\int_0^{\pi/(2\nu)}\tau_0\Omega\,dt
=\left(\frac92+\frac{\pi}{20}\right)\mathrm J.
\label{eq:rotary-baseline-work}
\end{equation}
Thus $X_r$ replaces the fraction $\pi/(900+10\pi)$ of that input,
approximately $0.34\%$. The table's $10\%$ refers specifically to damping;
the fraction of total hammer work replaced is much smaller here.

**It can substitute for the input saving from reducing losses.**
On this sine motion, write $r=J\nu^2/k$. For $0<r<1$, $X_r$ covers the
fraction $r$ of the damping work, giving the same hammer-input reduction
as lowering $b$ by that fraction. Actual heating remains $W_b$ in the
fictional model. At $r=1$, it pays all the damping work; the inertial and
spring torques also cancel on this particular motion, so the required
hammer torque is zero throughout the segment. The initial rotation still
has to be prepared. For $r>1$, its supply exceeds the damping work, beyond
what reducing a nonnegative damping coefficient alone can reproduce.
Increasing $b$ raises both supply and heating equally; changing $J$ or $k$
also changes the output mechanics. A larger $X_r$ alone is not an optimum.

**It can replace braking effort only during absorption.**
Where $\theta'''\Omega>0$, $X_r$ takes the instantaneous power
$X_r\theta'''\Omega$. It can cover that amount of a separately required
braking load; conventional braking must cover any shortfall. Excess
absorption requires an adjusted drive or motion. Slowing down alone does
not establish this role: the worked sine slows to rest while $X_r$
*supplies* power, so it provides no replacement for a brake there.

**Contact design and control still determine when the assistance is useful.**
The term has no independent timing command: the motion fixes its sign.
Where $\theta'''=0$, it provides no torque assistance; where $\Omega=0$,
it transfers no power. Its work contribution therefore does not specify
a replacement for contact geometry, engagement and release, sensing, or
the decision to stop at the tightening target. Nor does the local work
saving specify a percentage reduction in hammer size or motor rating.

The quantified replacement concerns work at the output during a specified
motion. Battery savings also depend on motor and hammer preparation and
on whatever supplies or replenishes $X_r$. Its existence and coefficient
alone leave those costs open.

\newpage

# A hammer, a nail and the feel of a blow

## Putting familiar differences into the equation

Think of tapping a nail with a small hammer, then using a heavier head.
Or of striking a nail in a firmly backed board, then trying a board that
bends under the blow. The weight in the hand, the resistance of the wood
and the movement of the backing correspond to different parts of our ODE.

Let $x(t)$ be forward movement of the hammer face and nail head during a
smooth interval in which they remain in contact, and let $v=x'$. Measure
$x$ relative to a fixed support reference. Use effective moving mass $m>0$,
dominated by the hammer head, effective resistance $b>0$, and elastic
stiffness $k>0$. Unresolved motion inside the fictional component is outside
this one-coordinate description. We define the resisting forces as $bv$
and $kx$, giving
\begin{equation}
mx''+bx'+kx=F(t),\qquad
(L,R,C)\longleftrightarrow(m,b,1/k).
\label{eq:hammer-base}
\end{equation}
Here $F(t)$ is any continued external driving force along the stroke.
The electrical capacitance corresponds to mechanical *compliance*, $1/k$:
a larger compliance means a more yielding setup.

| Familiar change | Main place in the model |
| :------------------------------------ | :------------------------------------ |
| A heavier hammer head | Larger $m$, corresponding to $L$. |
| Wood gripping the nail more strongly | Larger effective $b$, corresponding to $R$. |
| Firm backing instead of a bending board | Larger effective $k$, hence smaller $C=1/k$. |
| Different nail geometry or contact compliance | Changes in $k$, and possibly $b$ as well. |

: These are model associations; a real change can affect several coefficients.

The velocity-proportional law $bv$ is an idealized resistance for this
interval. Actual nail friction is not specified by a single constant $b$.
Likewise, $x$ includes elastic movement of the wood and backing; it is not
automatically the nail's permanent penetration depth.

Assume that the fictional component now exists inside the hammer and acts
at its working face. Its proposed effective force law gives
\begin{equation}
X_hx'''+mx''+bx'+kx=F(t),\qquad X_h=\frac{mb}{k}>0.
\label{eq:hammer-third}
\end{equation}
Since $[b]=\mathrm{N\,s/m}$ and $[k]=\mathrm{N/m}$,
$[X_h]=\mathrm{kg\,s}$ and $X_hx'''$ is a force. Multiplication by $v$
gives the familiar power equation,
\begin{equation}
Fv-X_hx'''v-mx''v-bv^2-kxv=0.
\label{eq:hammer-power}
\end{equation}
The component receives $P_{X_h}=X_hx'''v$, with the opposite entry here.
It supplies when $x'''v<0$ and absorbs when $x'''v>0$. How a component
inside the hammer produces this force, carries its reaction and exchanges
the required energy remains unspecified.

\newpage

## The same incoming speed, with different heads, wood and backing

Hold the incoming speed $V$ fixed. Preparing the moving mass from rest requires
\begin{equation}
W_{\mathrm{in}}=\int mv\frac{dv}{dt}\,dt
=\int_0^V mv\,dv=\frac12mV^2.
\label{eq:hammer-preparation}
\end{equation}
A heavier head at the same speed therefore requires more preparation work.
If preparation work is fixed instead, its speed must be lower.

Take a horizontal stroke with no continued hand force, so $F=0$. Start at
$x(0)=0$, $v(0)=V$, and give the fictional model the additional initial
condition $x''(0)=0$, part of its assumed preparation. Put
$\omega=\sqrt{k/m}$. An exact solution is
\begin{equation}
x(t)=\frac{V}{\omega}\sin(\omega t),\qquad
0\leq t\leq t_*:=\frac{\pi}{2\omega},\qquad
x_*:=x(t_*)=\frac{V}{\omega}.
\label{eq:hammer-motion}
\end{equation}
Direct substitution gives $mx''+kx=0$ and $X_hx'''+bv=0$.
The head moves forward and slows to its first stop. Throughout this motion,
the fictional component supplies exactly the power taken by the resistance.
The signed transfers are
\begin{equation}
W_{X_h}=\int_0^{t_*}X_hx'''v\,dt
=-\int_0^{t_*}bv^2\,dt
=-\frac{\pi bV^2}{4\omega}=-W_b.
\label{eq:hammer-work}
\end{equation}
Elastic loading separately receives
$\int_0^{t_*}kxv\,dt=kx_*^2/2=mV^2/2$.
The prepared motion pays for this loading; $X_h$ pays the resistance
from its unknown account.

Choose illustrative reference values
$$
m=\frac12\,\mathrm{kg},\qquad b=1000\,\mathrm{N\,s/m},\qquad
k=500000\,\mathrm{N/m},\qquad V=2\,\mathrm{m/s}.
$$
Here $\omega=1000\,\mathrm{s^{-1}}$ and $t_*=\pi/2\,\mathrm{ms}$.
Change one coefficient at a time, keeping $V$ and $F=0$. Recompute
$X_h$, the motion and its stopping time for every case.

| Case | $X_h$ ($\mathrm{kg\,s}$) | $x_*$ ($\mathrm{mm}$) | $kx_*$ ($\mathrm N$) | $X_h$ supplies ($\mathrm J$) |
| :------------------------ | --------: | --------: | --------: | --------: |
| Reference | $1/1000$ | $2$ | $1000$ | $\pi$ |
| Twice the head mass | $1/500$ | $2\sqrt2$ | $1000\sqrt2$ | $\sqrt2\pi$ |
| Twice the resistance $b$ | $1/500$ | $2$ | $1000$ | $2\pi$ |
| Half the stiffness $k$ | $1/500$ | $2\sqrt2$ | $500\sqrt2$ | $\sqrt2\pi$ |

: Exact model results. $kx_*$ is elastic force at the stop, not peak contact force.

**Heavier head.** Preparation work rises from $1\,\mathrm J$ to
$2\,\mathrm J$. The greater travel and elastic force accompany that larger
input, as one expects when swinging more mass at the same speed.

**More wood resistance.** Travel stays unchanged only because $X_h$ supplies
$2\pi\,\mathrm J$ instead of $\pi\,\mathrm J$. All the extra supply pays
for the extra resistance.

**Softer backing.** Greater travel comes with less elastic force at the stop.
The extra movement may be bending of the board; it does not establish
better nail driving.

\newpage

## Does this make sense in the real world?

The ordinary model gives a useful comparison. With the reference $m,b,k$,
the same incoming speed and $F=0$, its exact solution is
\begin{equation}
x_0(t)=(2\,\mathrm{mm})\,u e^{-u},\qquad
u=\frac{t}{1\,\mathrm{ms}}.
\label{eq:hammer-ordinary}
\end{equation}
It satisfies \eqref{eq:hammer-base} directly and stops first at
$t=1\,\mathrm{ms}$, after $2/e\,\mathrm{mm}$ of head movement.
The fictional model reaches $2\,\mathrm{mm}$ instead. Its larger loading
movement is accompanied by $\pi\,\mathrm J$ supplied by $X_h$, in addition
to the $1\,\mathrm J$ initially put into the moving mass. The extra supply
is a requirement of this comparison; we have not identified its source.

Mass, resistance and compliance do capture familiar differences between
blows. A heavier head at equal speed carries more prepared work; a yielding
backing lets the workpiece move; greater resistance demands more work for
the same motion. Nail shape and wood grain also affect fiber damage and
splitting ([Rammer, 2021][rammer]). A change of nail or wood can therefore
change more than one model coefficient.

Driving a nail also leaves a permanent change. A linear spring describes
elastic resistance, while a driven nail can remain at its new depth. To
predict that depth, the model needs a law for irreversible penetration and
a distinction between nail motion through wood and motion of the wood
itself. Some resistance work is part of making the hole and setting the
nail; it cannot all be treated as avoidable waste. The present calculation
describes a loading interval, ending before rebound or release.

There is another consequence of $X_h=mb/k$: moving the same hammer to
different wood or a different backing changes its predicted coefficient.
Here the relation is an assumption about the *coupled setup*. An internal
component would need a response that depends on that load; its existence
alone does not explain such a response. The familiar feel of ordinary
hammering does not establish the proposed third-derivative force law.

For the practical question, compare reaching the same permanent nail depth
with less total supplied work. Include the swing and whatever prepares or
replenishes $X_h$, with comparable initial and final component states.
Just as increased fictional supply alone does not establish battery savings
in the driver, it does not establish reduced effort here. The model makes
the mass, resistance and backing effects understandable, and calculates the
energy that $X_h$ would have to exchange. Whether an actual component can
provide that exchange economically remains open because we still do not
know what $X_h$ is.

# References {-}

1. Andreas Wettstein, Patric Grauberger and Sven Matthiesen (2021).
   [Modeling dynamic mechanical system behavior using sequence modeling of
   embodiment function relations: case study on a hammer mechanism][wettstein].
   *SN Applied Sciences* **3**, article 128.
   DOI: 10.1007/s42452-021-04149-8.
2. Mark Benazet, Francesco Ricca, Dario Bralla, Melanie N. Zeilinger and
   Andrea Carron (2026). [Learning-based approximate model predictive control
   for an impact wrench tool][benazet]. *European Journal of Control*,
   article 101596, available online 28 July 2026.
   DOI: 10.1016/j.ejcon.2026.101596.
3. Douglas R. Rammer (2021). [Fastenings][rammer]. Chapter 8 in
   *Wood handbook: Wood as an engineering material*, General Technical
   Report FPL-GTR-282. U.S. Department of Agriculture, Forest Service,
   Forest Products Laboratory.

[wettstein]: https://doi.org/10.1007/s42452-021-04149-8
[benazet]: https://doi.org/10.1016/j.ejcon.2026.101596
[rammer]: https://research.fs.usda.gov/treesearch/62253
