---
title: "Energy Ledgers for Forced Harmonic ODEs"
subtitle: "Heat, forcing and a fictional third derivative"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-02"
abstract: |
  A forced harmonic ordinary differential equation describes energy exchange
  with its surroundings. Integrating each signed voltage-current product gives
  an exact balance of stored energy, heat and source work. For a series RLC equation,
  we display the additional heat and source equations and prove that their
  signed transfers cancel. A finite capacitor supply makes the source account
  explicit. We then add a fictional third-derivative term to the same equation.
  Integration by parts separates its work into a boundary cross term and a
  squared-acceleration integral. An exact sinusoidal cycle shows the additional
  energy debit required to close the ledger. Every energy expression is derived
  from a power integral. All calculations are algebraic and exact.
keywords:
  - harmonic ordinary differential equations
  - energy conservation
  - forcing and dissipation
  - third derivatives

---

\begingroup\scriptsize
\noindent PDF created: \pdfbuildtimestamp\par
\noindent Latest on GitHub: \url{https://github.com/hobnilre/physics-ode-energy}\par
\endgroup

# Energy conservation for forced harmonic ODEs

## The equation and its system boundary

Consider a series inductor, resistor and capacitor driven by a voltage $v(t)$.
Let $q(t)$ be capacitor charge and $i(t)=\dot q(t)$ the series current. The
capacitance is written $C$; the coefficient of charge is its reciprocal. The
component laws and the series voltage balance give
\begin{equation}
L\ddot q+R\dot q+\frac{q}{C}=v(t),
\qquad L>0,\quad C>0,\quad R\geq0.
\label{eq:rlc}
\end{equation}
All coefficients are constant. The voltage is continuous and the solutions
have the derivatives used below. Impulses and switching events are outside
this model. Here *order* means the highest time derivative: equation
\eqref{eq:rlc} is second order and linear. The third-order equation in
Section 2 will remain linear as well.

Initially the system boundary contains the three circuit elements, but excludes
the voltage source and the surroundings receiving the resistor's heat. Positive
$vi$ denotes electrical power entering this circuit. Charge is measured in
coulombs, current in amperes, voltage in volts, and each energy below in joules.

Energy transferred through a port is defined by the signed integral of its
power. Write $[g]_{t_0}^{t_1}=g(t_1)-g(t_0)$. The component voltages are
$v_L=L\dot i$, $v_R=Ri$ and $v_C=q/C$. Their work inputs are therefore
\begin{align}
W_L&=\int_{t_0}^{t_1}v_Li\,dt
=\int_{t_0}^{t_1}L\dot i\,i\,dt
=\left[\frac L2i^2\right]_{t_0}^{t_1},\label{eq:inductor-work}\\
W_C&=\int_{t_0}^{t_1}v_Ci\,dt
=\int_{t_0}^{t_1}\frac qC\dot q\,dt
=\left[\frac{q^2}{2C}\right]_{t_0}^{t_1},\label{eq:capacitor-work}\\
W_R&=\int_{t_0}^{t_1}v_Ri\,dt
=\int_{t_0}^{t_1}Ri^2\,dt.\label{eq:resistor-work}
\end{align}
These are exact symbolic integrals. In the ideal lossless inductor and
capacitor, the work received is retained as stored energy. The first two
integrals depend only on their endpoint states. Choosing zero energy at
$q=i=0$ therefore gives, as an evaluated work primitive,
\begin{equation}
E_0(q,i)=\frac{L}{2}i^2+\frac{q^2}{2C}.
\label{eq:storage}
\end{equation}
No storage formula has been assumed in place of a power calculation.
The component laws, ideal retention of inductive and capacitive work, and
conversion of resistive work into recipient internal energy are the physical
model assumptions. The algebra below proves their consequences. The use of
conjugate effort and flow to account for energy exchanged between subsystems
is also the basis of port-Hamiltonian modelling
([van der Schaft, 2006][schaft]).

## The algebraic balance and the matching entries

\begin{theorem}[Energy ledger for the forced harmonic circuit]
For every classical solution of \eqref{eq:rlc}, the work integrals satisfy
\begin{equation}
W_{\rm in}:=\int_{t_0}^{t_1}vi\,dt=W_L+W_C+W_R.
\label{eq:interval-balance}
\end{equation}
The storage obtained from these integrals in \eqref{eq:storage} satisfies
\begin{equation}
\dot E_0=vi-Ri^2.
\label{eq:open-balance}
\end{equation}
If the enlarged system includes a heat recipient with internal energy $U$
and a source with available energy $S$, with no other energy transfers, their
work accounts are $\Delta U=\int_{t_0}^{t_1}Ri^2\,dt$ and
$\Delta S=-\int_{t_0}^{t_1}vi\,dt$. Equivalently, their energy rates are
\begin{equation}
\dot U=Ri^2,\qquad \dot S=-vi,
\label{eq:reservoirs}
\end{equation}
Adding these rates yields
\begin{equation}
\frac{d}{dt}(E_0+U+S)=0.
\label{eq:total}
\end{equation}
Consequently $E_0(t)+U(t)+S(t)$ is constant on each connected interval where
the model and its solution remain valid.
\end{theorem}

\begin{proof}
Multiply \eqref{eq:rlc} by $i=\dot q$ and integrate every term from $t_0$
to $t_1$. Substituting the separately evaluated component work integrals
\eqref{eq:inductor-work}--\eqref{eq:resistor-work} proves
\eqref{eq:interval-balance}. Since $\Delta E_0=W_L+W_C$, the fundamental
theorem of calculus gives \eqref{eq:open-balance}. Substituting
\eqref{eq:reservoirs} and adding gives
$$
\dot E_0+\dot U+\dot S=(vi-Ri^2)+Ri^2-vi=0.
$$
The integrated identity also gives
$$
\Delta E_0+\Delta U+\Delta S
=W_L+W_C+W_R-W_{\rm in}=0.
$$
The cancellation is pointwise; solving the ODE is unnecessary.
\end{proof}

The complete system of differential equations can be written
\begin{equation}
\begin{aligned}
\dot q&=i, & L\dot i&=v(t)-Ri-q/C,\\
\dot U&=Ri^2, & \dot S&=-v(t)i.
\end{aligned}
\label{eq:full-system}
\end{equation}
The energy entries make the double-entry structure explicit:

| Transfer | Circuit storage rate | Heat recipient rate | Source energy rate |
| :--- | ---: | ---: | ---: |
| Electrical work | $+vi$ | $0$ | $-vi$ |
| Resistive heating | $-Ri^2$ | $+Ri^2$ | $0$ |

: Each internal transfer has zero sum across the enlarged system.

The resistor term $Ri$ in the voltage equation has units of volts; its
corresponding heat rate is $Ri^2$, with units of watts. It is this power that
appears with opposite signs in the energy equations. Heat is energy in
transfer; $U$ is the internal energy of the material that receives it, with
its change obtained by integrating the received heat power.

If $vi>0$, the source loses energy; if $vi<0$, it receives energy. A source
that can only supply power cannot realize every such history. Likewise,
heat leaving the recipient would require another equation containing the
opposite heat-transfer term. The total is constant only after all external
energy transfers have been brought inside the boundary.

For $R>0$, the circuit's own storage generally decreases when $v=0$.
Equation \eqref{eq:total} therefore concerns the enlarged system, including
the destination of that decrease. The first law motivates the physical
reservoir balances; their cancellation is the algebraic result. Assigning
$\dot S=-vi$ to an otherwise unspecified source does not establish its
capacity, constitutive law or ability to produce a chosen voltage forever.

## A finite source and an exact interval ledger

A second capacitor provides a concrete source model. Let its capacitance be
$C_s>0$, its terminal voltage be $v$, and the outgoing current be $i$.
Its charge law gives $C_s\dot v=-i$. The closed circuit and heat recipient
then obey
\begin{equation}
\dot q=i,\qquad
L\dot i=v-Ri-q/C,\qquad
C_s\dot v=-i,\qquad
\dot U=Ri^2.
\label{eq:capacitor-source}
\end{equation}
Here the forcing voltage is determined by the coupled system and its initial
state. Calculate the work entering that source from its signed port power:
\begin{equation}
\Delta S=\int_{t_0}^{t_1}(-vi)\,dt
=\int_{t_0}^{t_1}C_sv\dot v\,dt
=\left[\frac{C_s}{2}v^2\right]_{t_0}^{t_1}.
\label{eq:source-capacitor-work}
\end{equation}
Thus $S=C_sv^2/2$ after choosing the zero-voltage reference, and
$\dot S=-vi$ follows from this work primitive. Hence
\begin{equation}
\frac{d}{dt}\left(\frac L2i^2+\frac{q^2}{2C}
+\frac{C_s}{2}v^2+U\right)=0.
\label{eq:finite-source-total}
\end{equation}
This source can receive returned energy as well as supply it. The coupled
equations replace the indefinitely prescribed external voltage with a
finite store. A different source requires its own component laws.

For a separate exact example of a prescribed drive, take $0\leq t\leq T$,
$q(0)=0$, $i(0)=I$, and
\begin{equation}
q(t)=It,\qquad i(t)=I,\qquad v(t)=RI+It/C.
\label{eq:constant-current}
\end{equation}
Direct substitution verifies \eqref{eq:rlc}. This example uses a source able
to generate the displayed voltage, rather than the supply capacitor in
\eqref{eq:capacitor-source}. Evaluate each transfer separately:
\begin{align}
W_{\rm in}&=\int_0^T v(t)i(t)\,dt
 =RI^2T+\frac{I^2T^2}{2C},\label{eq:input-work}\\
Q_{\rm heat}&=\int_0^T Ri(t)^2\,dt=RI^2T,\label{eq:heat-work}\\
\Delta S&=-W_{\rm in},\qquad \Delta U=Q_{\rm heat}.
\label{eq:reservoir-work}
\end{align}
The stored energies at the endpoints are
$$
E_0(0)=\frac L2I^2,\qquad
E_0(T)=\frac L2I^2+\frac{I^2T^2}{2C}.
$$
Thus $\Delta E_0+\Delta U+\Delta S=0$ exactly. The initial inductor energy
has been retained, even though it cancels from the difference. If $S$ is
nonnegative available source energy, the example requires
$S(0)\geq W_{\rm in}$. All integrals are exact polynomial antiderivatives;
there is no numerical integration or numerical residual.

## The same proof in other domains and at first order

The common equation and supplied work are
\begin{equation}
A\ddot x+B\dot x+Kx=f(t),\qquad
W_{\rm in}=\int_{t_0}^{t_1}f\dot x\,dt.
\label{eq:domain-form}
\end{equation}
The port must use the indicated effort and its conjugate flow:

| Domain | $x$ | $A$ | $B$ | $K$ | Input $f$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Electrical | Charge | Inductance | Resistance | Inverse capacitance | Voltage |
| Translational | Position | Mass | Viscous drag | Spring stiffness | Force |
| Rotational | Angle | Moment of inertia | Rotary drag | Torsional stiffness | Torque |

: In every case the supplied power is $f\dot x$.

For harmonic storage, take $A>0$, $K>0$ and $B\geq0$. The paired equations
follow by separately integrating the component powers:
\begin{align}
W_A&=\int_{t_0}^{t_1}(A\ddot x)\dot x\,dt
=\left[\frac A2\dot x^2\right]_{t_0}^{t_1},\label{eq:inertial-work}\\
W_K&=\int_{t_0}^{t_1}(Kx)\dot x\,dt
=\left[\frac K2x^2\right]_{t_0}^{t_1},\label{eq:elastic-work}\\
\Delta U&=\int_{t_0}^{t_1}B\dot x^2\,dt,
\qquad \Delta S=-\int_{t_0}^{t_1}f\dot x\,dt.
\label{eq:domain-reservoirs}
\end{align}
Define $\Delta E=W_A+W_K$ from the retained work. The integrated equation
gives $\Delta E+\Delta U+\Delta S=0$. Differentiating these accounts gives
$\dot E=f\dot x-B\dot x^2$, $\dot U=B\dot x^2$ and $\dot S=-f\dot x$.

Two first-order members of this class obey the same accounting. Setting $A=0$
and $B>0$ gives $B\dot x+Kx=f$, retaining the work integral $W_K$ only.
Setting $K=0$ and taking $w=\dot x$ as the state gives $A\dot w+Bw=f$,
retaining $W_A=\int A\dot w\,w\,dt=[Aw^2/2]$ only. Integrating the
equation times $\dot x$ or $w$, respectively, gives the same source and
heat accounts. These are exact models with a storage element omitted, not
approximations to a nonzero coefficient. Order zero is an algebraic relation,
not an ODE.

This proves the claim for the stated harmonic class and its reductions.
Derivative order alone does not supply a physical energy law for an arbitrary
ODE. Negative damping would require an active energy source, and changing
coefficients in time introduces additional work terms. Those cases need their
own accounts.

# Adding a fictional third derivative

## The added term and its power

Now change only the original equation by adding a constant real coefficient
$X\ne0$ multiplying $\dddot q$:
\begin{equation}
X\dddot q+L\ddot q+R\dot q+q/C=v(t).
\label{eq:third}
\end{equation}
The coefficient has units of inductance times time, or $\mathrm{H\,s}$, so
$X\dddot q$ is a voltage. No physical component law is asserted for it.
For $X\ne0$ the initial state includes $\ddot q(0)$ as well as $q(0)$ and
$\dot q(0)$. Set $a=\ddot q=\dot i$; here $a$ is a charge acceleration,
not a mechanical acceleration.

The work entering the fictional element must be calculated from its voltage
and current, just as for the original components:
\begin{equation}
P_X=(X\dddot q)\dot q,\qquad
W_X=\int_{t_0}^{t_1}X\dot q\,\dddot q\,dt.
\label{eq:x-work-definition}
\end{equation}
Multiplying \eqref{eq:third} by $i=\dot q$ and integrating gives
\begin{equation}
W_{\rm in}=W_L+W_C+W_R+W_X.
\label{eq:third-work}
\end{equation}
With the storage change already derived from $W_L+W_C$, the corresponding
instantaneous balance is
\begin{equation}
\dot E_0=vi-Ri^2-P_X,\qquad
P_X=X\dot q\,\dddot q.
\label{eq:third-power}
\end{equation}
Thus $P_X$ is the power entering the fictional element under the circuit
port convention. With just the original heat and source equations,
\begin{equation}
\frac{d}{dt}(E_0+U+S)=-P_X.
\label{eq:missing-port}
\end{equation}
The old ledger is incomplete unless this term vanishes. Calling it a loss
does not fix the account: $P_X$ has no fixed sign, even when $X>0$.

## The cross term and the remaining square

Evaluate the extra work by exact integration by parts:
\begin{equation}
W_X=\int_{t_0}^{t_1}X\dot q\,\dddot q\,dt
=\left[X\dot q\,\ddot q\right]_{t_0}^{t_1}
-\int_{t_0}^{t_1}X(\ddot q)^2\,dt.
\label{eq:x-parts}
\end{equation}
The first contribution is a boundary term; the second depends on the
trajectory. Grouping the boundary term with the original storage work gives
$$
\Delta E_*:=W_L+W_C+\left[X\dot q\,\ddot q\right]_{t_0}^{t_1}
=W_{\rm in}-W_R+\int_{t_0}^{t_1}X(\ddot q)^2\,dt.
$$
Its primitive and derivative are therefore
\begin{equation}
E_*=\frac L2\dot q^2+\frac{q^2}{2C}+X\dot q\,\ddot q,
\qquad
\dot E_*=vi-R\dot q^2+X(\ddot q)^2.
\label{eq:cross-balance}
\end{equation}
Consequently the original source and heat accounts leave
\begin{equation}
\frac{d}{dt}(E_*+U+S)=X(\ddot q)^2.
\label{eq:remainder}
\end{equation}
The third derivative has supplied both a cross term in the candidate energy
and an additional power term. Retaining only one of these would give an
incorrect balance.

An additional account $B_X$ would have to receive the signed work
$\Delta B_X=-\int_{t_0}^{t_1}X(\ddot q)^2\,dt$. Consequently
\begin{equation}
\dot B_X=-X(\ddot q)^2,
\qquad
\frac{d}{dt}(E_*+U+S+B_X)=0.
\label{eq:extra-account}
\end{equation}
Equivalently, define the fictional element's complete account by
$H_X=X\dot q\,\ddot q+B_X$. Then
\begin{equation}
\dot H_X=P_X,\qquad
\frac{d}{dt}(E_0+U+S+H_X)=0.
\label{eq:element-account}
\end{equation}
This is the opposite-sign entry: $-P_X$ in the circuit balance is
paired with $+P_X$ in the extra element. After separating the cross term,
$+X(\ddot q)^2$ is paired with $-X(\ddot q)^2$.

For $X>0$, $B_X$ supplies energy whenever $\ddot q\ne0$; for $X<0$, it
receives energy. The latter sign alone does not justify calling it a real
heat bath. Also, $E_*$ is not a nonnegative storage function: for any fixed
$\dot q\ne0$ and $X\ne0$, the term $X\dot q\,\ddot q$ is unbounded below
as the freely specified initial $\ddot q$ varies. Conservation of an
algebraically defined quantity and the existence of physically admissible
energy stores are different claims.

Equations \eqref{eq:extra-account} and \eqref{eq:element-account} complete
the formal ledger. They do not manufacture a physical component, establish
its capacity, or prove stability. In particular, a finite supplying account
cannot support an unlimited energy debit without replenishment.

## Exact energy transfers during one cycle

Choose a charge amplitude $Q>0$ and frequency $\omega>0$, and prescribe
\begin{equation}
q(t)=Q\sin(\omega t),\qquad T=2\pi/\omega.
\label{eq:sinusoid}
\end{equation}
Substitution in \eqref{eq:third} gives the exact required voltage
\begin{equation}
v(t)=Q\left[(C^{-1}-L\omega^2)\sin(\omega t)
+(R\omega-X\omega^3)\cos(\omega t)\right].
\label{eq:sinusoidal-drive}
\end{equation}
Both $E_0$ and the cross term return to their initial values after $T$.
The instantaneous power of the added term is
$$
P_X=-XQ^2\omega^4\cos^2(\omega t).
$$
Using the exact identities
$\int_0^T\cos^2(\omega t)\,dt
=\int_0^T\sin^2(\omega t)\,dt=T/2$
and $\int_0^T\sin(\omega t)\cos(\omega t)\,dt=0$, each signed transfer is
\begin{align}
W_{\rm in}&=\int_0^T vi\,dt
=\pi Q^2\omega(R-X\omega^2),\label{eq:cycle-source}\\
Q_{\rm heat}&=\int_0^T Ri^2\,dt=\pi RQ^2\omega,\label{eq:cycle-heat}\\
W_X&=\int_0^T P_X\,dt=-\pi XQ^2\omega^3.
\label{eq:cycle-extra}
\end{align}
The original circuit balance closes as
$\Delta E_0=W_{\rm in}-Q_{\rm heat}-W_X=0$.
The enlarged balance closes as
$$
\Delta E_0+\Delta U+\Delta S+\Delta H_X
=0+Q_{\rm heat}-W_{\rm in}+W_X=0.
$$
Because the cross term also returns, $\Delta B_X=\Delta H_X=W_X$.
For positive $X$, the fictional element delivers energy during this cycle;
the amount delivered is $\pi XQ^2\omega^3$. It is a debit to that element's
account.

The accounting becomes particularly direct when $R>0$ and
\begin{equation}
\omega^2=\frac{1}{LC},\qquad X=RLC.
\label{eq:unforced-cycle}
\end{equation}
Then the voltage \eqref{eq:sinusoidal-drive} is identically zero, yet the
sinusoid remains an exact solution of the fictional equation and the resistor
receives $\pi RQ^2\omega>0$ per cycle. The fictional element's account loses
exactly the same energy. Indeed, on this trajectory
$\dot H_X=-Ri^2$ pointwise. Without that account, the specified circuit
model has an energy deficit of $\pi RQ^2\omega$ in its supply ledger per
cycle. This is a property of the proposed equation, not evidence for a
physical device producing energy without a source.

## What the added derivative establishes

For $X=0$, the first section's harmonic energy and its heat and source
equations suffice. For $X\ne0$, the same manipulation leaves a new transfer:
either retain $P_X$ as a separate port, or split it into the derivative of
$X\dot q\,\ddot q$ and the remainder $-X(\ddot q)^2$. In both forms a
matching account is required.

The equation alone supplies no physical interpretation for that account.
It therefore does not establish a violation of energy conservation in
nature, nor a realizable conservative device. It establishes exactly what
the proposed extra term would require the rest of the system to supply or
receive. A third derivative changes this particular ledger; derivative
order by itself is not a universal test of energy conservation.

# References {-}

1. Arjan van der Schaft (2006). “Port-Hamiltonian systems: an introductory
   survey.” *Proceedings of the International Congress of Mathematicians*,
   Vol. III, pp. 1339–1365. European Mathematical Society.
   [Author manuscript][schaft].

[schaft]: https://ris.utwente.nl/ws/portalfiles/portal/5386843/ICMvanderSchaft.pdf
