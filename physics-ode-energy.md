---
title: "Energy Ledgers for Forced Harmonic ODEs"
subtitle: "Kirchhoff power balance, an unknown third derivative, and X = LRC"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-02"
abstract: |
  Multiplying the voltage equation of a forced series LRC circuit by current
  gives a power identity. Integrating the separate port powers derives the
  storage changes and identifies the heat and source equations needed for a
  constant total energy. A finite capacitor supplies a concrete source model.
  We then add the fictional voltage term $Xq'''$ with $X$ positive but its physical
  identity unknown. Exact integration by parts retains a boundary cross term
  and a signed trajectory integral. Worked examples show both directions of
  power transfer and the additional account required by the new term.
  Finally, assuming only that the numerical coefficient is $X=LRC$, we check
  its units, derive its effect relative to resistor heating, and compare
  component choices under fixed operating conditions. Numerical examples
  evaluate exact formulas; every energy expression begins with signed power.
keywords:
  - Kirchhoff voltage law
  - harmonic ordinary differential equations
  - energy accounting
  - third derivatives
  - component selection
---

\begingroup\scriptsize
\noindent PDF created: \pdfbuildtimestamp\par
\noindent Latest on GitHub: \url{https://github.com/hobnilre/physics-ode-energy}\par
\endgroup

# From Kirchhoff's voltage law to a complete energy ledger

## Voltage balance and the two missing equations

Let $q(t)$ denote capacitor charge and let the series current be
$i(t)=q'(t)$. Consider constant $L>0$, $C>0$, and $R\geq0$, and an applied
voltage $f(t)$. The ideal component laws are
$v_L=Li'=Lq''$, $v_R=Ri=Rq'$, and $v_C=q/C$. Kirchhoff's voltage law gives
\begin{equation}
Lq''+Rq'+q/C=f(t),
\qquad
Lq''+Rq'+q/C-f(t)=0.
\label{eq:kvl}
\end{equation}
Every term is a voltage. A solution gives $q$ and $q'=i$; initial charge and
current select a solution. All solutions considered here are smooth on the
interval in use, with no impulses or switching. Coefficients are constant.

Here *order* means the highest time derivative: \eqref{eq:kvl} is second
order. Its degree as a polynomial in its highest derivative is one. Adding
a term proportional to $q'''$ increases the order to three while retaining
degree one and linearity.

Multiplying the voltage law by the common current gives
\begin{equation}
Lq''i+Rq'i+\frac{qi}{C}-f(t)i=0,
\qquad i=q'.
\label{eq:power-kvl}
\end{equation}
Each term now has units of watts: voltage times current. Positive component
power means power entering that component; positive $fi$ means power
supplied to the LRC circuit. Thus $Ri^2$ is resistive absorption and $-fi$
is the entry on the supplying side of the voltage port.

To include the surroundings, the resistor's absorbed power needs a destination
and the forcing port needs a source or sink. Before specifying either one,
the required structure is
\begin{equation}
\begin{cases}
\underbrace{\,?\,}_{\text{heat recipient rate}}-Rq'i=0,\\
Lq''i+Rq'i+qi/C-f(t)i=0,\\
\underbrace{\,?\,}_{\text{source rate}}+f(t)i=0.
\end{cases}
\label{eq:blank-ledger}
\end{equation}
The known transfers already have opposite entries. This resembles double-entry
economic accounting: a debit to one account is a credit to another. Here the
entries measure signed energy transfer, without the additional conventions of
financial account classes.

The zero in \eqref{eq:power-kvl} establishes a power identity. Constant
*total energy* requires identifying the component work and completing the two
missing rate equations. The circuit's own stored energy can change.

## Deriving the accounts by integrating power

Fix an interval $[t_0,t_1]$, and write $[g]_{t_0}^{t_1}=g(t_1)-g(t_0)$.
Calculate each signed component work separately:
\begin{align}
W_L&=\int_{t_0}^{t_1}(Li')i\,dt
=\left[\frac L2 i^2\right]_{t_0}^{t_1},\label{eq:wl}\\
W_C&=\int_{t_0}^{t_1}\frac qC q'\,dt
=\left[\frac{q^2}{2C}\right]_{t_0}^{t_1},\label{eq:wc}\\
W_R&=\int_{t_0}^{t_1}Ri^2\,dt,\qquad
W_f=\int_{t_0}^{t_1}fi\,dt.
\label{eq:wr-wf}
\end{align}
The first two evaluations use $i\,di=i i'\,dt$ and $q\,dq=q q'\,dt$.
With ideal retention of received work and zero references at $i=q=0$, the
evaluated primitives define the circuit storage:
\begin{equation}
E_0(q,i)=\frac L2i^2+\frac{q^2}{2C},
\qquad \Delta E_0=W_L+W_C.
\label{eq:e0}
\end{equation}

The physical coupling assumption is stated independently of the algebra:
the ideal inductor and capacitor retain their received work; the resistor
retains no energy and transfers all its absorbed work to a heat recipient;
the source loses exactly the electrical work it supplies. The enlarged
boundary contains these stores and the recipient, with no other transfers.
These are first-law and component assumptions. Algebra proves their
consequences, rather than establishing the physical laws themselves.

Let $U$ be recipient internal energy and $S$ source energy. Their signed work
integrals fill the missing accounts:
\begin{equation}
U(t_1)-U(t_0)=W_R,\qquad S(t_1)-S(t_0)=-W_f.
\label{eq:reservoir-integrals}
\end{equation}
Heat is the transfer; $U$ is the internal energy that receives it. For example,
an insulated recipient with constant heat capacity $C_h>0$ and temperature
$\vartheta$ obeys $C_h\vartheta'=Ri^2$. Integrating its received power gives
$\Delta U=\int C_h\vartheta'\,dt=C_h[\vartheta]_{t_0}^{t_1}$.

Integrating \eqref{eq:power-kvl}, with each term evaluated as above, gives
\begin{equation}
W_L+W_C+W_R-W_f=0,
\qquad
\Delta E_0+\Delta U+\Delta S=0.
\label{eq:base-interval}
\end{equation}
Differentiating the work primitives gives the complete three-row ledger:
\begin{equation}
\begin{cases}
U'-Ri^2=0,\\
E_0'+Ri^2-fi=0,\\
S'+fi=0,
\end{cases}
\qquad E_0'=Li'i+(q/C)i.
\label{eq:base-rates}
\end{equation}
The corresponding differential system includes the motion and both destinations:
\begin{equation}
\begin{aligned}
q'&=i, & Li'&=f(t)-Ri-q/C,\\
U'&=Ri^2, & S'&=-f(t)i.
\end{aligned}
\label{eq:base-system}
\end{equation}

\begin{theorem}[Conditional conservation for the harmonic model]
Under the stated component and reservoir assumptions, every admissible
classical solution of \eqref{eq:base-system} satisfies
\begin{equation}
(E_0+U+S)'=(fi-Ri^2)+Ri^2-fi=0.
\label{eq:base-total}
\end{equation}
Consequently $E_0+U+S$ is constant on each connected interval of validity.
\end{theorem}

\begin{proof}
The separately integrated power law gives \eqref{eq:base-interval}.
Its equivalent local form is \eqref{eq:base-rates}. Adding the three rows
cancels every transfer with its opposite entry and yields
\eqref{eq:base-total}.
\end{proof}

| Transfer | Circuit rate $E_0'$ | Recipient rate $U'$ | Source rate $S'$ |
| :--- | ---: | ---: | ---: |
| Electrical work | $+fi$ | $0$ | $-fi$ |
| Resistive heat | $-Ri^2$ | $+Ri^2$ | $0$ |

: Internal transfers in the enlarged system sum to zero.

A positive $fi$ debits the source; a negative $fi$ credits it. A source must
actually support both directions if the chosen history requires them.
A prescribed $f(t)$ supplies no capacity or constitutive law for such a source.
Defining $S'=-fi$ by itself completes an algebraic ledger. A physical model
also requires admissible reservoirs and their independent laws. The general
language of energy ports and interconnected subsystems is developed in
[van der Schaft (2006)][schaft].

## A finite source with its own differential equation

Use a second capacitor with capacitance $C_s>0$, voltage $f$, and outgoing
current $i$. Its charge law gives $C_s f'=-i$. For the insulated heat
recipient described above, the full closed model is
\begin{equation}
\begin{aligned}
q'&=i, & Li'&=f-Ri-q/C,\\
C_s f'&=-i, & C_h\vartheta'&=Ri^2.
\end{aligned}
\label{eq:finite-source-system}
\end{equation}
Here $f$ is a state determined by the source and circuit together. It is no
longer an independently prescribed function. Its signed received work is
\begin{equation}
\Delta S=\int_{t_0}^{t_1}(-fi)\,dt
=\int_{t_0}^{t_1}C_s f f'\,dt
=\left[\frac{C_s}{2}f^2\right]_{t_0}^{t_1}.
\label{eq:finite-source-work}
\end{equation}
Thus the source primitive is $S=C_s f^2/2$. The recipient's primitive is
$U-U_{\mathrm{ref}}=C_h(\vartheta-\vartheta_{\mathrm{ref}})$, as obtained
from its integral. Substitution into the derived rates gives
\begin{equation}
(E_0+S+U)'=(fi-Ri^2)-fi+Ri^2=0.
\label{eq:finite-total}
\end{equation}
Also $(q+C_s f)'=0$, independently confirming the source's charge transfer.
The capacitor is finite: continued supply changes its voltage and available
energy. Validity is required only while the circuit and reservoirs remain
physically admissible.

## An exact interval with separately evaluated transfers

A first-order member of the same class gives a short complete example.
Omit the inductor exactly, take $R>0$ and $C_s=C$, and set
$q(0)=0$, $f(0)=V_0>0$. The equations are
$Rq'+q/C=f$ and $Cf'=-q'$. Define $\tau=RC/2$. Direct differentiation
and substitution verify
\begin{equation}
q(t)=\frac{CV_0}{2}(1-e^{-t/\tau}),\qquad
i(t)=\frac{V_0}{R}e^{-t/\tau},\qquad
f(t)=\frac{V_0}{2}(1+e^{-t/\tau}).
\label{eq:rc-solution}
\end{equation}
This is an exact solution of the first-order model.

For any admissible $T>0$, write $r=e^{-T/\tau}$. The signed transfers,
evaluated independently from their powers, are
\begin{align}
W_C&=\int_0^T(q/C)i\,dt
=\frac{CV_0^2}{8}(1-r)^2,\label{eq:rc-wc}\\
\Delta U&=\int_0^T Ri^2\,dt
=\frac{CV_0^2}{4}(1-r^2),\label{eq:rc-heat}\\
\Delta S&=-\int_0^T fi\,dt
=\frac{CV_0^2}{8}\bigl((1+r)^2-4\bigr).
\label{eq:rc-source}
\end{align}
The load's initial storage is zero and its final storage is
$CV_0^2(1-r)^2/8$. The source's initial and final stores are
$CV_0^2/2$ and $CV_0^2(1+r)^2/8$. Therefore the finite-interval ledger closes:
\begin{equation}
\Delta E_0+\Delta U+\Delta S
=\frac{CV_0^2}{8}
\left((1-r)^2+2(1-r^2)+(1+r)^2-4\right)=0.
\label{eq:rc-ledger}
\end{equation}
The source debit pays both capacitor charging and heating. No numerical
integration is involved.

## The harmonic class and the limits of the statement

The same argument applies to $Ax''+Bx'+Kx=F(t)$ with constant positive
retained storage coefficients and $B\geq0$, when $F x'$ is the physical
port power. In translation $(A,B,K)=(m,b,k)$; in rotation these become
inertia, damping and torsional stiffness. Integrating their component powers
first gives
$$
\int Ax''x'\,dt=[A(x')^2/2],\qquad
\int Kxx'\,dt=[Kx^2/2],\qquad
\int B(x')^2\,dt.
$$
These evaluations supply the storage changes and heat transfer, with
$-\int F x'\,dt$ entered on the source account. The same cancellation follows.

The exact RC reduction omits $L$ and retains the capacitor primitive.
The exact RL reduction omits the capacitor voltage term, giving
$Li'+Ri=f$, and retains the inductor primitive. Both are first-order
models with the same heat and source entries.

Derivative order alone supplies none of the required component laws,
power ports or reservoir assumptions. Accordingly, this conditional proof
does not extend to every arbitrary ODE of order at most two. Time-dependent
coefficients require their own parameter-work terms. Conservation here
concerns the completed system on admissible intervals.

# Adding the unknown term $Xq'''$

## Its power and the fourth account

Add exactly one fictional voltage contribution to the same equation:
\begin{equation}
Xq'''+Lq''+Rq'+q/C-f(t)=0,\qquad X>0.
\label{eq:third-ode}
\end{equation}
The physical identity of $X$ is unknown. For now $X$ is a constant
coefficient specifying a voltage term. Put $a=q''=i'$; then
$v_X=Xa'=Xq'''$. The proposed port power is
\begin{equation}
P_X=v_Xi=Xq'''q',
\qquad
W_X=\int_{t_0}^{t_1}Xq'''q'\,dt.
\label{eq:x-port}
\end{equation}
Positive $P_X$ means absorption from the modeled circuit, while negative
$P_X$ means delivery to it. Since $X>0$, the sign is the sign of $q'''q'$.
It has no fixed sign for arbitrary trajectories.

Multiplication by current now gives the required four-row structure:
\begin{equation}
\begin{cases}
\underbrace{\,?\,}_{\text{heat recipient rate}}-Ri^2=0,\\
Xq'''i+Lq''i+Ri^2+qi/C-fi=0,\\
\underbrace{\,?\,}_{\text{source rate}}+fi=0,\\
-P_X+\underbrace{\,?\,}_{\text{additional rate}}=0.
\end{cases}
\label{eq:four-blanks}
\end{equation}
The first and third rows are already determined in Part 1. The fourth row
identifies what remains to be supplied.

Integrating every term separately gives
\begin{equation}
W_L+W_C+W_R+W_X-W_f=0,
\qquad
\Delta(E_0+U+S)=-W_X.
\label{eq:third-interval}
\end{equation}
A required extra energy account $A_X$ would therefore have to satisfy
\begin{equation}
A_X(t_1)-A_X(t_0)=W_X,\qquad A_X'=P_X.
\label{eq:ax}
\end{equation}
Its rate is the missing entry, without specifying the identity of $X$.
The completed rates are
\begin{equation}
\begin{cases}
U'-Ri^2=0,\\
E_0'+Ri^2+P_X-fi=0,\\
S'+fi=0,\\
A_X'-P_X=0,
\end{cases}
\quad
(E_0+U+S+A_X)'=0.
\label{eq:four-ledger}
\end{equation}
For a prescribed $f$, the full differential system is
\begin{equation}
\begin{aligned}
q'&=i,& i'&=a,&
a'&=\frac{f-La-Ri-q/C}{X},\\
U'&=Ri^2,& S'&=-fi,&
A_X'&=i(f-La-Ri-q/C).
\end{aligned}
\label{eq:third-system}
\end{equation}
The initial motion state now includes $a(0)$. Introducing $A_X$ proves the
bookkeeping identity. Interpreting it as a physical energy account requires
independent information about the unknown term's mechanism and capacity.

## Integration by parts: boundary work and the remainder

The work in \eqref{eq:x-port} has the exact evaluation
\begin{equation}
W_X=\int_{t_0}^{t_1}Xq'q'''\,dt
=[Xq'q'']_{t_0}^{t_1}
-\int_{t_0}^{t_1}X(q'')^2\,dt.
\label{eq:x-parts}
\end{equation}
Both contributions must be retained. The boundary term can make $W_X$
positive, despite the negative sign of the trajectory integral.

For clarity, name the boundary primitive $K_X=Xq'q''=Xia$ and define a
remaining account through its signed integral,
\begin{equation}
B_X(t_1)-B_X(t_0)=-\int_{t_0}^{t_1}X(q'')^2\,dt,
\qquad A_X=K_X+B_X,
\label{eq:bx-integral}
\end{equation}
where the additive reference constants are chosen consistently.
Grouping the boundary primitive with $E_0$ produces $E_*=E_0+K_X$.
Differentiating the evaluated integrals gives
\begin{equation}
E_*'=fi-Ri^2+Xa^2,\qquad B_X'=-Xa^2,
\qquad (E_*+U+S+B_X)'=0.
\label{eq:split-ledger}
\end{equation}
The $+Xa^2$ entry requires exactly the $-Xa^2$ entry in the additional
account. With $X>0$, $B_X$ decreases whenever $a\ne0$. The complete
account $A_X$ can still increase when $K_X$ increases sufficiently.

These names describe algebraic accounts. They supply no physical identity
for $X$. In particular, $K_X$ need not be positive, and at fixed $i\ne0$
the expression $E_0+Xia$ is unbounded below as the independent initial $a$
varies. The cross term is therefore not established as a nonnegative
physical store. Higher derivative order by itself establishes neither
energy conservation nor its violation.

## Numerical example: positive work into the unknown port

Take the illustrative values
$L=1\,\mathrm H$, $R=1\,\Omega$, $C=1\,\mathrm F$,
$X=1\,\mathrm{H\,s}$. Define dimensionless time $u=t/(1\,\mathrm s)$
and, on $0\leq t\leq1\,\mathrm s$, choose
\begin{equation}
q(t)=(1\,\mathrm C)\frac{u^3}{6},
\qquad
f(t)=(1\,\mathrm V)\left(1+u+\frac{u^2}{2}+\frac{u^3}{6}\right).
\label{eq:poly-example}
\end{equation}
Substitution verifies the proposed ODE exactly. Here
$i=(1\,\mathrm A)u^2/2$ and $q'''=1\,\mathrm{A/s^2}$, so
$P_X=(1\,\mathrm W)u^2/2$ is positive for $t>0$.
Its work and the two contributions in \eqref{eq:x-parts} are
\begin{equation}
W_X=\int_0^{1\,\mathrm s}P_X\,dt=\frac16\,\mathrm J,
\qquad
[K_X]_0^{1\,\mathrm s}=\frac12\,\mathrm J,\qquad
\int_0^{1\,\mathrm s}Xa^2\,dt=\frac13\,\mathrm J.
\label{eq:poly-x-work}
\end{equation}
The remaining signed works are $W_L=1/8\,\mathrm J$,
$W_C=1/72\,\mathrm J$, $W_R=1/20\,\mathrm J$, and
$W_f=16/45\,\mathrm J$, each obtained by integrating its polynomial power.
Thus the full ledger is
$$
\Delta E_0+\Delta U+\Delta S+\Delta A_X
=\left(\frac18+\frac1{72}+\frac1{20}-\frac{16}{45}+\frac16\right)
\mathrm J=0.
$$
This interval credits the unknown account with $1/6\,\mathrm J$.
Its $B_X$ part loses $1/3\,\mathrm J$, while its boundary part gains
$1/2\,\mathrm J$.

## Exact sinusoidal cycles: delivery from the unknown port

Choose $Q>0$, $\omega>0$, and a period $T=2\pi/\omega$. The trajectory
and the forcing needed to realize it in the proposed ODE are
\begin{align}
q(t)&=Q\sin(\omega t),\label{eq:sine-q}\\
f(t)&=Q\left[(C^{-1}-L\omega^2)\sin(\omega t)
+(R\omega-X\omega^3)\cos(\omega t)\right].
\label{eq:sine-f}
\end{align}
This $f$ is determined by exact substitution. It is a prescribed-drive
example; a particular finite source must also satisfy its own component law.

Here $q'''=-\omega^2 i$, so
\begin{equation}
P_X=-X\omega^2 i^2=-XQ^2\omega^4\cos^2(\omega t)\leq0.
\label{eq:sine-power}
\end{equation}
The unknown port delivers energy throughout the cycle except at current
zeros. In general it can absorb power, as the preceding example shows.

Using the exact antiderivatives of $\sin^2$, $\cos^2$, and $\sin\cos$,
evaluate the separate signed cycle transfers:
\begin{align}
W_L&=0,\qquad W_C=0,\label{eq:sine-storage-work}\\
W_R&=\int_0^T Ri^2\,dt=\pi RQ^2\omega,\label{eq:sine-heat}\\
W_X&=\int_0^T P_X\,dt=-\pi XQ^2\omega^3,\label{eq:sine-x}\\
W_f&=\int_0^T fi\,dt=\pi Q^2\omega(R-X\omega^2).
\label{eq:sine-source}
\end{align}
For example, $\int_0^T\cos^2(\omega t)\,dt=\pi/\omega$ and
$\int_0^T\sin(\omega t)\cos(\omega t)\,dt=0$. Both storage states return;
$K_X(0)=K_X(T)=0$, and
$\Delta B_X=\Delta A_X=-\pi XQ^2\omega^3$. The exact total is
\begin{equation}
\Delta E_0+\Delta U+\Delta S+\Delta A_X
=0+\pi RQ^2\omega-\pi Q^2\omega(R-X\omega^2)
-\pi XQ^2\omega^3=0.
\label{eq:sine-ledger}
\end{equation}

With the same illustrative components as above and $Q=1\,\mathrm C$,
the following numbers are exact evaluations of these formulas.

| $\omega$ ($\mathrm{s^{-1}}$) | $T$ ($\mathrm s$) | $\Delta U$ ($\mathrm J$) | $\Delta S=-W_f$ ($\mathrm J$) | $\Delta A_X=W_X$ ($\mathrm J$) |
| ---: | ---: | ---: | ---: | ---: |
| $1/2$ | $4\pi$ | $\pi/2$ | $-3\pi/8$ | $-\pi/8$ |
| $1$ | $2\pi$ | $\pi$ | $0$ | $-\pi$ |
| $2$ | $\pi$ | $2\pi$ | $+6\pi$ | $-8\pi$ |

: Signed energy changes over one cycle; $\Delta E_0=0$ in every case.

At $\omega=1/2$, the applied source and the unknown port jointly pay for heat.
At $\omega=1$, \eqref{eq:sine-f} is identically zero: the unknown account
pays all the heating. At $\omega=2$, its $8\pi\,\mathrm J$ debit pays
$2\pi\,\mathrm J$ of heating and credits the forcing source with
$6\pi\,\mathrm J$. An account with finite available energy can support
only an admissible number of such cycles. The repeated sinusoidal motion
of the formal ODE does not establish an unlimited physical supply.

# Assuming the numerical coefficient $X=LRC$

## Units and the effect on a sinusoidal trajectory

Now assume only the coefficient relation
\begin{equation}
X=LRC>0.
\label{eq:link}
\end{equation}
This determines a numerical value from $L$, $R$, and $C$, with $R>0$ in
this part. It supplies no identity, construction or energy source for $X$.

Since $RC$ has units of seconds, the units are consistent:
\begin{equation}
[LRC]=\mathrm{H}\,\Omega\,\mathrm F
=\mathrm{H\,s}=\frac{\mathrm{V\,s^2}}{\mathrm A},
\qquad
[q''']=\frac{\mathrm A}{\mathrm{s^2}}.
\label{eq:x-units}
\end{equation}
Consequently $Xq'''$ is a voltage and $Xq'''i$ is a power.
Dimensional consistency is a necessary check on the proposed equation.

For a sinusoid, $v_X=-X\omega^2i$ and $v_R=Ri$. Their sum and the
ratio of the cycle delivery to resistor heating are
\begin{equation}
v_R+v_X=R(1-LC\omega^2)i,\qquad
\rho:=\frac{-W_X}{W_R}=\frac{X\omega^2}{R}=LC\omega^2.
\label{eq:relative-effect}
\end{equation}
This relation applies to sinusoidal trajectories. The general instantaneous
law remains $P_X=Xq'''i$.

Define $\omega_0=1/\sqrt{LC}$. Then $\rho=(\omega/\omega_0)^2$.
For $\rho<1$, the unknown port covers part of the heat and the forcing
source supplies the remainder over a cycle. At $\rho=1$, it covers all
the heating; for $\rho>1$, it also credits the forcing source. Substitution
into \eqref{eq:sine-f} gives
\begin{equation}
f(t)=Q(1-LC\omega^2)
\left[C^{-1}\sin(\omega t)+R\omega\cos(\omega t)\right].
\label{eq:linked-forcing}
\end{equation}
For this linked coefficient, $\omega=\omega_0$ makes the whole applied
voltage zero, including its reactive part.

The corresponding exact factorization of the same ODE is
\begin{equation}
\left(RC\frac{d}{dt}+1\right)
\left(Lq''+\frac qC\right)=f(t).
\label{eq:factor}
\end{equation}
For $f=0$, its characteristic factors are
$(RC\lambda+1)(L\lambda^2+C^{-1})$, so the formal solutions are
$$
q(t)=A\cos(\omega_0 t)+B\sin(\omega_0 t)+D e^{-t/(RC)}.
$$
In particular, a nonzero sinusoid is an exact unforced solution. On that
trajectory $P_X=-Ri^2$ pointwise and the cycle debit is
$\pi RQ^2\omega_0$. The resistor heating is matched by this required
decrease of the unknown account. A physical interpretation still needs
the information that the coefficient relation leaves unspecified.

## Choosing components requires a stated objective

An effect can mean absolute power, energy delivered per cycle, or delivery
relative to heating. These quantities give different design questions.
From the separate power integrals in Part 2, the positive delivery per
sinusoidal cycle and its average rate are
\begin{equation}
D_X:=-W_X=\pi LRCQ^2\omega^3,\qquad
\overline P_{\mathrm{deliver}}=\frac{D_X}{T}
=\frac12 LRCQ^2\omega^4.
\label{eq:design-fixed}
\end{equation}
These formulas hold with the specified trajectory. Changing components while
keeping an applied $f(t)$ fixed generally changes $q(t)$ and its amplitude.

At fixed $Q$ and $\omega$, increasing any of $L,R,C$ increases the absolute
delivery. Increasing $L$ or $C$ also increases $\rho=LC\omega^2$.
Increasing $R$ increases delivery and heating in the same proportion and
leaves $\rho$ unchanged. If each component is independently bounded by a
positive allowed range, the product and the absolute delivery are maximized
by taking all three at their upper bounds. Without bounds there is no finite
maximum.

There is a different result when frequency follows $\omega_0$. For fixed
charge amplitude $Q$, substitution into \eqref{eq:design-fixed} gives
\begin{equation}
D_X\big|_{\omega_0}=\frac{\pi RQ^2}{\sqrt{LC}},
\qquad
\overline P_{\mathrm{deliver}}\big|_{\omega_0}
=\frac{RQ^2}{2LC},
\qquad \rho=1.
\label{eq:design-resonance-charge}
\end{equation}
Increasing $LC$ now decreases both quantities, even though $X=LRC$
increases. With independent positive component bounds, their maximum at
fixed resonant charge amplitude uses the largest $R$ and the smallest $L,C$.
The relative effect remains one for every positive choice.

If instead the resonant current amplitude $I=Q\omega_0$ is fixed, the same
integrals with $Q=I/\omega_0$ give
\begin{equation}
D_X\big|_{\omega_0,I}=\pi RI^2\sqrt{LC},\qquad
\overline P_{\mathrm{deliver}}\big|_{\omega_0,I}=\frac12 RI^2.
\label{eq:design-resonance-current}
\end{equation}
Larger $LC$ increases energy per cycle by lengthening the period; at fixed
$I$ the average delivery is independent of $L,C$. Thus maximizing the
coefficient alone does not specify the maximum power or work of a trajectory.

## Numerical component comparisons

Take $Q=1\,\mathrm C$. First compare at fixed $\omega=1\,\mathrm{s^{-1}}$;
then retune each choice to its own $\omega_0$. All entries are exact
substitutions into \eqref{eq:relative-effect}, \eqref{eq:design-fixed},
and \eqref{eq:design-resonance-charge}. Component values are illustrative,
rather than properties of an identified $X$ device.

| $(L,R,C)$ in $(\mathrm H,\Omega,\mathrm F)$ | $X$ ($\mathrm{H\,s}$) | $\rho$ at $\omega=1$ | $D_X$ at $\omega=1$ ($\mathrm J$) | $D_X$ at $\omega_0$ ($\mathrm J$) |
| :--- | ---: | ---: | ---: | ---: |
| $(1,1,1)$ | $1$ | $1$ | $\pi$ | $\pi$ |
| $(4,1,1)$ | $4$ | $4$ | $4\pi$ | $\pi/2$ |
| $(1,3,1)$ | $3$ | $1$ | $3\pi$ | $3\pi$ |
| $(1,1,4)$ | $4$ | $4$ | $4\pi$ | $\pi/2$ |
| $(4,3,4)$ | $48$ | $16$ | $48\pi$ | $3\pi/4$ |

: Absolute delivery and relative effect under two specified frequency choices.

\newpage

For example, impose the independent illustrative bounds
$1\,\mathrm H\leq L\leq4\,\mathrm H$, $1\,\Omega\leq R\leq3\,\Omega$, and
$1\,\mathrm F\leq C\leq4\,\mathrm F$. At fixed $Q=1\,\mathrm C$ and
$\omega=1\,\mathrm{s^{-1}}$, the upper choices give
$X=48\,\mathrm{H\,s}$ and the maximum $D_X=48\pi\,\mathrm J$.
Separately evaluated heating is $W_R=3\pi\,\mathrm J$, and applied-source
work is $W_f=-45\pi\,\mathrm J$. The signed ledger is
$$
\Delta E_0+\Delta U+\Delta S+\Delta A_X
=(0+3\pi+45\pi-48\pi)\,\mathrm J=0.
$$
The unknown account must supply $48\pi\,\mathrm J$ per cycle; the enlarged
system also needs a source able to receive $45\pi\,\mathrm J$.

Within those same bounds, at resonant frequency with fixed $Q$, the maximum
instead occurs at $(L,R,C)=(1,3,1)$: $D_X=3\pi\,\mathrm J$ and
$\overline P_{\mathrm{deliver}}=3/2\,\mathrm W$. For $(4,3,4)$,
the resonant frequency is $1/4\,\mathrm{s^{-1}}$ and the debit is only
$3\pi/4\,\mathrm J$ per cycle. The numerical value of $X$ therefore becomes
a useful comparison only after fixing the operating conditions and objective.

The coefficient relation, the sign of each power, and the required account
debits follow exactly from the proposed ODE. Whether an unknown component
can support those histories remains a physical question about its independent
laws and available energy. The ledger states that requirement explicitly.

# References {-}

1. Arjan van der Schaft (2006). “Port-Hamiltonian systems: an introductory
   survey.” *Proceedings of the International Congress of Mathematicians*,
   Vol. III, pp. 1339–1365. European Mathematical Society.
   [Author manuscript][schaft].

[schaft]: https://ris.utwente.nl/ws/portalfiles/portal/5386843/ICMvanderSchaft.pdf
