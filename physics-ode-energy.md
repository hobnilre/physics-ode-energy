---
title: "Energy Ledgers for Forced Harmonic ODEs"
subtitle: "Kirchhoff power balance and an unknown component with X = LRC"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-02"
abstract: |
  An added term $Xq'''$ supplies or absorbs energy according to the sign
  of $Xq'''q'$. Exact trajectories show both roles. Choosing $X=LRC$
  scales the transfer on fixed motion; it does not choose its direction.
  Brief hammer and rotary examples apply the same rule. The component's
  physical identity and remaining energy account stay open.
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
Movement $x$ includes elastic support motion; permanent nail depth is undetermined.

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

# References {-}

1. H. Nilre and B. C. Herlin (2026). [The ODE Template and Its Domain Equivalents][template].
2. H. Nilre and B. C. Herlin (2026). [ODE Coefficient Synthesis][synthesis].
3. H. Nilre and B. C. Herlin (2026). [Interconnecting Series and Parallel ODEs][interconnect].

[template]: https://github.com/hobnilre/physics-ode-template
[synthesis]: https://github.com/hobnilre/physics-ode-coefficient-synthesis
[interconnect]: https://github.com/hobnilre/physics-ode-interconnect-ser-par
