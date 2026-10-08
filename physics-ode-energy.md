---
title: "Energy Ledgers for Forced Harmonic ODEs"
subtitle: "Kirchhoff power balance and an unknown component with X = LRC"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-02"
abstract: |
  We add an unknown term $Xq'''$ to a forced harmonic LRC equation and
  determine whether it supplies or absorbs energy by integrating its signed
  power. Exact trajectories exhibit both roles. For $X=LRC$, coefficient
  choices scale the transfer on a fixed trajectory; its direction follows
  from the derivative product. Brief hammer and rotary applications reuse
  these rules. The unknown component's remaining energy account is left open.
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

Use the [LRC template][template], Section 2, with the
[series connection convention][interconnect], Section 1:
\begin{equation}
Lq''+Rq'+\frac qC=f(t),
\qquad L>0,\quad C>0,\quad R\geq0.
\label{eq:base}
\end{equation}
Here $q$ is charge, $i=q'$ current and $f$ the applied forcing voltage; $L,R,C$ are
inductance, resistance and capacitance. Coefficients are constant, trajectories
smooth, and primes denote time derivatives. Multiplying by $i$ and putting
the source first gives
\begin{equation}
f(t)i-Lq''i-Rq'i-\frac{qi}{C}=0.
\label{eq:base-power}
\end{equation}
Every term is voltage times current. The input contributes $+fi$ and the
resistor contributes $-Ri^2$: the single-loop power identity of
[Tellegen (1952)][tellegen].

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
Lines 1 and 3 belong to the heat recipient and the forcing source or sink.
Their entries $+Ri^2$ and $-fi$ oppose the transfers in line 2; the remaining
terms are unspecified. If $fi<0$, the forcing source receives energy.

Cancellation identifies the transfers. Constant total energy also requires
the omitted energy rates and reservoir laws. Those accounts remain open;
a prescribed $f(t)$ alone does not specify the source's available energy.

# Does the unknown term $Xq'''$ supply or absorb power?

## The fourth line and the direction of transfer

Add one fictional component term, with constant $X>0$:
\begin{equation}
Xq'''+Lq''+Rq'+\frac qC=f(t).
\label{eq:third}
\end{equation}
Its physical identity is unknown. Treat $Xq'''$ as its voltage contribution.
The power equation and its matching entries become
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

# Choosing $L$, $R$ and $C$ when $X=LRC$

## Units and what the coefficient determines

For $(a,b,c)=(L,R,1/C)$, the family and staircase in
[*ODE Coefficient Synthesis*][synthesis], Sections 1--3, give
\begin{equation}
X=A_3=A_{-1,3}=\frac{ab}{c}=LRC>0.
\label{eq:coefficient}
\end{equation}
Here $R>0$. This is the chosen coefficient; the component's identity remains
unknown. Since $RC$ has units of time, $[X]=\mathrm{H\,s}$ and
$[Xq''']=\mathrm V$.
Its contribution to line 2 is
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

With independent bounds $1\leq L/(1\,\mathrm H)\leq2$,
$1\leq R/(1\,\Omega)\leq2$ and $1\leq C/(1\,\mathrm F)\leq2$,
the last row maximizes both directional magnitudes. Part 2's integrals
then give $8\pi\,\mathrm J$ supplied over the sinusoidal cycle and
$4/3\,\mathrm J$ absorbed over the polynomial interval.

These comparisons hold the motion fixed and adjust the forcing accordingly.
If $f(t)$ and the initial conditions are held fixed instead, changing
$L,R,C$ also changes $q(t)$; maximizing the product alone then does not
determine the maximum effect. The coefficient relation specifies the power
required of $X$ on a chosen motion. Its physical identity and the remaining
terms of line 4 are still open.

# Hammer and nail: applying Parts 2 and 3

Let $x$ be hammer-face and nail-head movement during smooth contact,
$v=x'$, and $m,d,k>0$ constant mass, resistance and stiffness. The
[domain map][template] $(L,R,C,q,i)\mapsto(m,d,1/k,x,v)$ gives
\begin{equation}
X_hx'''+mx''+dx'+kx=F(t),\qquad X_h=\frac{md}{k}.
\label{eq:hammer-third}
\end{equation}
Here $F$ is external driving force. Part 2 gives received power
$X_hx'''v$: its sign determines supply or absorption. Part 3 gives the
fixed-motion scaling through $md/k$, with $F$ recomputed.

For one exact blow, set $F=0$, $x(0)=0$, $v(0)=v_0>0$ and $x''(0)=0$.
With $\omega=\sqrt{k/m}$, the solution up to the first stop is
\begin{equation}
x(t)=\frac{v_0}{\omega}\sin(\omega t),\qquad
0\leq t\leq t_*:=\frac{\pi}{2\omega}.
\label{eq:hammer-motion}
\end{equation}
Indeed, $mx''+kx=0$ and $X_hx'''+dv=0$. Applying
\eqref{eq:x-work} gives
\begin{equation}
W_{X_h}=\int_0^{t_*}X_hx'''v\,dt
=-\int_0^{t_*}dv^2\,dt
=-\frac{\pi d v_0^2}{4\omega}=-W_d.
\label{eq:hammer-work}
\end{equation}
The component supplies the resistance work from its unspecified account.
Movement $x$ includes elastic support motion; permanent nail depth is undetermined.

# Rotary impact driver: work on a prescribed motion

Let $\theta$ be output angle, $\Omega=\theta'$, and $J,d,k>0$ constant
inertia, damping and torsional stiffness. Prescribed hammer torque is
$\tau_h$; $J$ excludes the hammer. Substituting $(L,R,C)\mapsto(J,d,1/k)$ gives
\begin{equation}
X_r\theta'''+J\theta''+d\theta'+k\theta=\tau_h,
\qquad X_r=\frac{Jd}{k}.
\label{eq:rotary-third}
\end{equation}
At identical motion and coefficients, let $\tau_X$ and $\tau_0$ be the
required torques with and without the unknown term. Part 2's work rule gives
\begin{equation}
\Delta W_h=\int_{t_0}^{t_1}(\tau_X-\tau_0)\Omega\,dt
=\int_{t_0}^{t_1}X_r\theta'''\Omega\,dt=W_{X_r}.
\label{eq:rotary-work-difference}
\end{equation}
Thus supplied work reduces the required hammer input on that motion.

Take $\theta=\Theta\sin(\omega t)$, with $\Theta,\omega>0$, on
$0\leq t\leq T:=\pi/(2\omega)$. Since $\theta'''=-\omega^2\Omega$,
\begin{equation}
\begin{aligned}
W_{X_r}&=\int_0^T X_r\theta'''\Omega\,dt
=-\frac{\pi X_r\Theta^2\omega^3}{4},\\
W_d&=\int_0^T d\Omega^2\,dt
=\frac{\pi d\Theta^2\omega}{4},\qquad
\frac{-W_{X_r}}{W_d}=\frac{J\omega^2}{k}.
\end{aligned}
\label{eq:rotary-work}
\end{equation}
The ratio is Part 3's $LC\omega^2$. On this motion, an ordinary model
requires the same torque with damping
\begin{equation}
d_{\mathrm{eff}}=d-X_r\omega^2=d\left(1-\frac{J\omega^2}{k}\right)\geq0.
\label{eq:rotary-effective-damping}
\end{equation}
For example, $J\omega^2/k=1/10$ gives $d_{\mathrm{eff}}=9d/10$ and
$W_{X_r}=-W_d/10$. The unknown component supplies work that the reduced
damping avoids dissipating.

The forcing is recomputed, as in Part 3; matching this motion does not
establish equal responses to a fixed drive. Hammer preparation and the
account of $X_r$ remain outside the output-work comparison.

# References {-}

1. B. D. H. Tellegen (1952). [A general network theorem, with applications][tellegen].
   *Philips Research Reports* **7**, 259–269.
2. H. Nilre and B. C. Herlin (2026). [The ODE Template and Its Domain Equivalents][template].
3. H. Nilre and B. C. Herlin (2026). [ODE Coefficient Synthesis][synthesis].
4. H. Nilre and B. C. Herlin (2026). [Interconnecting Series and Parallel ODEs][interconnect].

[tellegen]: https://pearl-hifi.com/06_Lit_Archive/02_PEARL_Arch/Vol_16/Sec_53/Philips_Rsrch_Reports_1946_thru_1977/Philips%20Research%20Reports-07-1952.pdf#page=263
[template]: https://github.com/hobnilre/physics-ode-template
[synthesis]: https://github.com/hobnilre/physics-ode-coefficient-synthesis
[interconnect]: https://github.com/hobnilre/physics-ode-interconnect-ser-par
