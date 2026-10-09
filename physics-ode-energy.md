---
title: "Energy Ledgers for Forced Harmonic ODEs"
subtitle: "Kirchhoff power balance and an unknown component with X = LRC"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-02"
abstract: |
  An added term $Xq'''$ supplies or absorbs energy according to the sign
  of $Xq'''q'$. Exact trajectories show both roles. Choosing $X=LRC$
  scales the transfer on fixed motion; it does not choose its direction.
  Hammer and rotary examples apply the same rule and give apparent
  coefficients of performance relative to specified ordinary inputs.
  Their counted output includes resistance work and elastic storage;
  the component's physical identity and remaining energy account stay open.
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

# From voltage balance to power accounts

Start with the forced [LRC template][template], Section 2:
\begin{equation}
Lq''+Rq'+\frac qC=f(t),
\qquad L,C>0,\quad R\geq0.
\label{eq:base}
\end{equation}
Here $q$ is charge, $i=q'$ current, $f$ forcing voltage, and $L,R,C$
inductance, resistance and capacitance. Coefficients are constant,
trajectories smooth, and primes denote time derivatives.
In the [series convention][interconnect], Section 1, the same current
multiplies every voltage term. Put the source first and record the
circuit power balance in line 2, with opposite transfers in lines 1 and 3:
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
Line 1 belongs to the heat recipient and line 3 to the source or sink;
$fi<0$ means the source receives energy. Opposite entries record each
transfer on both sides. Constant total energy also requires the omitted
energy rates and reservoir laws; prescribed $f(t)$ alone gives no source capacity.

# When the added term supplies or absorbs

Add a fictional component with constant $X>0$ and unknown physical identity:
\begin{equation}
Xq'''+Lq''+Rq'+\frac qC=f(t).
\label{eq:third}
\end{equation}
Treating $Xq'''$ as its voltage contribution adds a fourth account:
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
Thus the received power and the contribution to line 2 are
\begin{equation}
P_X=Xq'''i,\qquad P_{X\to2}=-Xq'''i.
\label{eq:x-powers}
\end{equation}
Since $X>0$, the component supplies power when $q'''i<0$, absorbs it
when $q'''i>0$, and transfers none when the product is zero.
Over an interval,
\begin{equation}
W_X(t_0,t_1)=\int_{t_0}^{t_1}Xq'''(t)i(t)\,dt,
\qquad W_{X\to2}=-W_X.
\label{eq:x-work}
\end{equation}
Positive $W_X$ is net received energy; negative $W_X$ is net supplied
energy. The integral fixes the transfer, while the rest of line 4 remains open.

Take $L=1\,\mathrm H$, $R=1\,\Omega$, $C=1\,\mathrm F$ and
$X=1\,\mathrm{H\,s}$. Put $u=t/(1\,\mathrm s)$ and obtain $f(t)$
by substituting each chosen trajectory into \eqref{eq:third}.

**Supplier.** For
\begin{equation}
q=(1\,\mathrm C)\sin u,\qquad
i=(1\,\mathrm A)\cos u,\qquad
q'''=-(1\,\mathrm{A/s^2})\cos u,
\label{eq:supplier}
\end{equation}
the inductive and capacitive terms cancel, as do the resistive and $X$
terms, giving $f(t)=0$. Hence
\begin{equation}
P_X=-(1\,\mathrm W)\cos^2u,\qquad
W_X(0,2\pi\,\mathrm s)=-(1\,\mathrm J)\int_0^{2\pi}\cos^2u\,du
=-\pi\,\mathrm J.
\label{eq:supplier-work}
\end{equation}
At $t=0$, the component supplies $1\,\mathrm W$; over a cycle it supplies
$\pi\,\mathrm J$. Here $P_X=-Ri^2$ at every instant, so this transfer
covers the resistor's absorption. The equation leaves its physical source unspecified.

**Absorber.** On $0\leq t\leq1\,\mathrm s$, choose
\begin{equation}
q=(1\,\mathrm C)\frac{u^3}{6},\qquad
i=(1\,\mathrm A)\frac{u^2}{2},\qquad
q'''=1\,\mathrm{A/s^2}.
\label{eq:absorber}
\end{equation}
Now
\begin{equation}
f(t)=(1\,\mathrm V)\left(1+u+\frac{u^2}{2}+\frac{u^3}{6}\right),
\qquad P_X=(1\,\mathrm W)\frac{u^2}{2},
\label{eq:absorber-forcing}
\end{equation}
and
\begin{equation}
W_X=(1\,\mathrm J)\int_0^1\frac{u^2}{2}\,du=\frac16\,\mathrm J.
\label{eq:absorber-work}
\end{equation}
At $t=1\,\mathrm s$, $P_{X\to2}=-1/2\,\mathrm W$. The same positive
coefficient supplies energy on the sinusoid and absorbs it on this polynomial.

# What choosing $X=LRC$ changes

For $(a,b,c)=(L,R,1/C)$, [*ODE Coefficient Synthesis*][synthesis],
Sections 1--3, selects
\begin{equation}
X=A_3=A_{-1,3}=\frac{ab}{c}=LRC>0.
\label{eq:coefficient}
\end{equation}
Here $R>0$. Since $RC$ has units of time, $[X]=\mathrm{H\,s}$ and
$Xq'''$ is a voltage. Equation \eqref{eq:x-powers} becomes
$P_{X\to2}=-LRC\,q'''i$.

Fix $q(t)$, including amplitude and time scale. Increasing $LRC$ then
strengthens whichever direction $q'''i$ already selects. The signed work
scales the same way on a fixed interval. With independent positive bounds,
the greatest magnitude uses all three upper bounds; without bounds there
is no finite maximum. Recompute $f(t)$ to retain the chosen motion.

For $q=Q\sin(\omega t)$, with $Q,\omega>0$,
\begin{equation}
q'''=-\omega^2i,\qquad P_{X\to2}=LRC\,\omega^2i^2\geq0.
\label{eq:sinusoidal-sign}
\end{equation}
All positive choices make $X$ a supplier except at current zeros.
Absorption needs a different derivative sign, as in \eqref{eq:absorber}.
Relative to resistor absorption, at $i\ne0$,
\begin{equation}
\frac{|P_{X\to2}|}{Ri^2}=LC\left|\frac{q'''}i\right|.
\label{eq:relative}
\end{equation}
This ratio is $LC\omega^2$ on a sinusoid. Increasing $R$ scales both
powers equally; only $L$ and $C$ change their ratio on fixed motion.

Use Section 2's supplier at $t=0$ and absorber at $t=1\,\mathrm s$,
recomputing the forcing for each row.

| $(L,R,C)$ in $(\mathrm H,\Omega,\mathrm F)$ | $X$ ($\mathrm{H\,s}$) | Supplier ($\mathrm W$) | Absorber ($\mathrm W$) |
| :--------------------------- | --------------: | ------------------: | ------------------: |
| $(1,1,1)$ | $1$ | $+1$ | $-1/2$ |
| $(1,2,1)$ | $2$ | $+2$ | $-1$ |
| $(2,2,2)$ | $8$ | $+8$ | $-4$ |

: Signed contributions $P_{X\to2}$ on the same two trajectories.

With $1\leq L/(1\,\mathrm H),R/(1\,\Omega),C/(1\,\mathrm F)\leq2$,
the last row maximizes both magnitudes. The same integrals give
$8\pi\,\mathrm J$ supplied per sinusoidal cycle and $4/3\,\mathrm J$
absorbed over the polynomial interval.

If forcing and initial conditions are fixed instead, changing the
coefficients changes the motion too. Maximizing $LRC$ alone then says
nothing about the maximum transfer.

# Hammer and nail

Let $x$ be hammer-face and nail-head movement during smooth contact,
$v=x'$, and $m,d,k>0$ mass, effective resistance and stiffness.
The [domain map][template], Sections 2--3, replaces $(L,R,C)$ by $(m,d,1/k)$:
\begin{equation}
X_hx'''+mx''+dx'+kx=F(t),\qquad X_h=\frac{md}{k}.
\label{eq:hammer-third}
\end{equation}
Assume the unknown component acts inside the hammer. Its received power
is $X_hx'''v$; Section 3's fixed-motion scaling becomes $md/k$.

Think of $m$ as the hammer's heft, $d$ as the resistance encountered by
the moving nail, and $k$ as the stiffness of the contact, workpiece and
backing. Here $dv$ represents resisting losses by a simple speed-dependent
force, while $kx$ is the restoring force from elastic give. The unfamiliar $x'''$ measures
how quickly acceleration changes. While the head moves forward, a
deceleration that builds in strength gives $x'''v<0$, so the unknown
component supplies power; a deceleration that eases gives the opposite
sign, so it absorbs power.

For $F=0$, $x(0)=0$, $v(0)=v_0>0$ and $x''(0)=0$, put $\omega=\sqrt{k/m}$.
Up to the first stop,
\begin{equation}
x(t)=\frac{v_0}{\omega}\sin(\omega t),\qquad
0\leq t\leq t_*:=\frac{\pi}{2\omega}.
\label{eq:hammer-motion}
\end{equation}
Indeed, $mx''+kx=0$ and $X_hx'''+dv=0$, so
\begin{equation}
W_{X_h}=\int_0^{t_*}X_hx'''v\,dt
=-\int_0^{t_*}dv^2\,dt
=-\frac{\pi d v_0^2}{4\omega}=-W_d.
\label{eq:hammer-work}
\end{equation}
The component supplies the resistance work from its unspecified account.

To read this ideal blow in familiar terms, change one coefficient at a
time, keeping the other two and the incoming speed $v_0$ fixed.
The head travels $x(t_*)=v_0/\omega$ before its first stop.

Increasing $m$ corresponds to using a heavier hammer. At the same head speed,
there is more inertia to arrest: the blow takes longer to stop and the
head travels farther. Reducing $m$ gives a shorter movement and an earlier
stop. The larger mass also raises $X_h$; on these blows the unknown
component supplies more work as resistance acts over the longer movement.
Keeping the incoming speed the same does not mean that the heavier hammer
takes the same effort to swing.

Increasing $d$ represents stronger opposition at the same speed---the
drag one associates with a nail that grips harder. Decreasing $d$ represents
easier movement. Extra drag would change an ordinary hammer's motion.
In this particular blow, however, increasing $d$ also increases $X_h$
so that the unknown component supplies exactly the extra resistance work.
The stopping time and head travel stay unchanged, while the resistance
work and the component's supplied work both increase in proportion to $d$.
Reducing $d$ reduces both. This cancellation is the distinctive prediction
of the assumed component on the stated trajectory.

Increasing $k$ corresponds to firmer backing: a board supported close
to the nail gives less than one that can bend under the blow. At a given
displacement the restoring force is larger, and this ideal blow stops
sooner after less head travel. Decreasing $k$ lets the movement continue
longer and farther. Since compliance is $1/k$, firmer backing reduces
$X_h$ and, on these blows, the work supplied by the unknown component;
softer backing increases both. Extra head travel can be elastic bending
of the support. Permanent nail depth remains undetermined by this model.

For a coefficient of performance (COP), count work delivered to the
modeled resistance and spring as output. Count initial kinetic energy
and applied work as input, excluding the unknown component's supplied
work. Call this ratio an apparent COP. For the stated blow, the endpoint
energies and load work are
\begin{equation}
\begin{aligned}
K_0&=\frac12mv_0^2,\qquad
U_*:=\frac12kx(t_*)^2=K_0,\\
W_{\mathrm{load},h}&=\int_0^{t_*}(dv+kx)v\,dt=W_d+U_*.
\end{aligned}
\label{eq:hammer-load-work}
\end{equation}
Since $F=0$, the applied work $\int_0^{t_*}Fv\,dt$ is zero. Thus
\begin{equation}
\mathrm{COP}_{\mathrm{app},h}
=\frac{W_{\mathrm{load},h}}{K_0}
=1+\frac{\pi d}{2\sqrt{mk}}.
\label{eq:hammer-cop}
\end{equation}
For example, $d=\sqrt{mk}$ gives $1+\pi/2\approx2.57$. Under the same
one-at-a-time comparisons at fixed $v_0$, increasing $d$ raises the ratio,
while increasing $m$ or $k$ lowers it. A heavier hammer receives more work
from the component on this blow, but its initial kinetic energy grows faster.
The ratio counts both dissipated work and recoverable elastic energy;
neither quantity by itself measures permanent nail penetration.

# Rotary output on prescribed motion

For output angle $\theta$ and speed $\Omega=\theta'$, substitute
$(q,L,R,C,f)\mapsto(\theta,J,d,1/k,\tau_h)$ in \eqref{eq:third}.
Here $J,d,k>0$ are output inertia, damping and torsional stiffness;
$\tau_h$ is prescribed hammer torque and $J$ excludes the hammer.
The assumed component inside the tool has $X_r=Jd/k$.
On identical motion, let $\tau_X$ and $\tau_0$ be the required torques with
and without it. Their input-work difference is
\begin{equation}
\Delta W_h=\int_{t_0}^{t_1}(\tau_X-\tau_0)\Omega\,dt
=\int_{t_0}^{t_1}X_r\theta'''\Omega\,dt=W_{X_r}.
\label{eq:rotary-work-difference}
\end{equation}
Supplied work therefore reduces the required hammer input on that motion.

For $\theta=\Theta\sin(\omega t)$, $\Theta,\omega>0$, and
$T=\pi/(2\omega)$, the relation $\theta'''=-\omega^2\Omega$ gives
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
When $J\omega^2/k\leq1$, an ordinary model gives the same torque on
this motion with nonnegative damping
\begin{equation}
d_{\mathrm{eff}}=d-X_r\omega^2=d\left(1-\frac{J\omega^2}{k}\right).
\label{eq:rotary-effective-damping}
\end{equation}
For example, $J\omega^2/k=1/10$ gives $d_{\mathrm{eff}}=9d/10$ and
$W_{X_r}=-W_d/10$. The component supplies work that reduced damping
avoids dissipating. This comparison adjusts the forcing to match motion;
hammer preparation and the unknown account remain outside it.

Apply the same apparent-COP definition to the quarter-sine interval,
taking $0<r:=J\omega^2/k\leq1$. Its initial kinetic and final elastic
energies are
\begin{equation}
U:=\frac12k\Theta^2,\qquad
K_0=\frac12J\Theta^2\omega^2=rU.
\label{eq:rotary-endpoint-energy}
\end{equation}
The corresponding load work and applied hammer work follow from their
signed power integrals:
\begin{equation}
\begin{aligned}
W_{\mathrm{load},r}
&=\int_0^T(d\Omega+k\theta)\Omega\,dt=U+W_d,\\
W_h&=\int_0^T\tau_X\Omega\,dt
=U-K_0+(1-r)W_d=(1-r)(U+W_d).
\end{aligned}
\label{eq:rotary-cop-work}
\end{equation}
Here $\tau_X=J\theta''+d\Omega+k\theta+X_r\theta'''$ is the required
hammer torque with the component. Including the output's initial kinetic
energy in the denominator gives
\begin{equation}
\mathrm{COP}_{\mathrm{app},r}
=\frac{W_{\mathrm{load},r}}{K_0+W_h}
=\frac{U+W_d}{U+(1-r)W_d}.
\label{eq:rotary-cop}
\end{equation}
For $r=1/10$, additionally choosing $W_d=U$, equivalently
$d\omega/k=2/\pi$, gives $\mathrm{COP}_{\mathrm{app},r}=20/19\approx1.053$.
Supplying one tenth of the damping work therefore does not imply a
ten-percent reduction in the total counted input.

In both examples, the excess over one comes from excluding the component's
supplied work from the input. Including $-W_{X_h}=W_d$ or $-W_{X_r}=rW_d$
in the respective denominator makes the ratio exactly one. These interval
identities leave the component's remaining account open. A practical tool
COP additionally needs a defined useful nail-driving or fastening output
and the energy cost of preparation and replenishment.

# References {-}

1. H. Nilre and B. C. Herlin (2026). [The ODE Template and Its Domain Equivalents][template].
2. H. Nilre and B. C. Herlin (2026). [ODE Coefficient Synthesis][synthesis].
3. H. Nilre and B. C. Herlin (2026). [Interconnecting Series and Parallel ODEs][interconnect].

[template]: https://github.com/hobnilre/physics-ode-template
[synthesis]: https://github.com/hobnilre/physics-ode-coefficient-synthesis
[interconnect]: https://github.com/hobnilre/physics-ode-interconnect-ser-par
