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
  Finally, assuming only the coefficient relation $X=LRC$, we check the units
  and compare how component choices strengthen either contribution to the
  circuit's power equation.
keywords:
  - Kirchhoff voltage law
  - harmonic ordinary differential equations
  - power balance
  - energy accounting
  - unknown component
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
