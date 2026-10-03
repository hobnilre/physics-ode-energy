# Energy Ledgers for Forced Harmonic ODEs

Kirchhoff power balance and an unknown component with X = LRC.

[Article repository](https://github.com/hobnilre/physics-ode-energy).

## What this article adds, and why it matters

The article follows six questions. First, multiplying the harmonic LRC
voltage equation by current produces a power balance. A three-line system
exposes the opposite heat and source entries, like debit and credit in a
double-entry ledger. Completing its missing energy equations is left open.

Second, adding the fictional voltage term X q''' adds an opposite power
entry in a fourth line. Its sign determines whether X supplies or absorbs
power. A sinusoidal example supplies energy; a polynomial example absorbs
it. Their energy transfers follow exact signed power integrals.

Third, the numerical coefficient relation X=LRC is checked for consistent
units. Component comparisons show how to strengthen either contribution
for a fixed trajectory, and why positive coefficients alone cannot reverse
its direction. X's physical identity remains unknown.

Fourth, a hammer and nail connect the same coefficients to familiar changes
in head mass, wood resistance and backing stiffness. Exact examples separate
head movement from permanent nail depth and show the energy the fictional
component must supply. Practical benefit requires the same useful result
with less total input, including preparation or replenishment of X.

Fifth, the same equation is applied to a simplified rotary impact driver,
assuming the fictional component exists inside the tool. An exact comparison
shows how its supplied work and an ordinary reduction in damping can reduce
hammer input by the same amount on a chosen motion. The prose quantifies
how much hammer work is replaced, distinguishes that from the damping
percentage, and states when X could cover a braking load. Contact design,
timing and the fictional component's energy cost remain part of the
whole-tool comparison.

Sixth, a comparison with [Third- and Higher-Order ODEs](https://github.com/hobnilre/physics-ode-3rd-deg/blob/4bdb25cbf6057a848bf9fba09c98db7c5ddc9e9a/third-and-higher-order-odes.md)
explains their shared signed-power method. An exact integration-by-parts
identity connects the two presentations. Assigning a term to the unknown
component here differs from deriving a higher-order equation by eliminating
ordinary internal states. A shorter algebraic treatment can look similar
while leaving the physical energy accounts and interpretation open.

[Read the article (PDF)](physics-ode-energy.pdf) ·
[Manuscript source](physics-ode-energy.md)

## Standalone build

Install GNU Make, GNU Coreutils, Pandoc, XeLaTeX, the TeX Gyre fonts, and the
LaTeX packages used by the preambles. Run `make pdf` in this directory.
All build inputs are present here. Numerical examples evaluate exact
closed forms; the article uses no numerical integration or simulations.

The title date records the first version and remains fixed across revisions.
The PDF creation timestamp advances on a rebuild. Run `make -B pdf` to force one.
Build intermediates go to ignored `build/` by default; `BUILD_DIR=/absolute/path`
selects another location. The `make clean` command removes that directory and
keeps the PDF.

Typography is installed in `article-style.yaml`, `preamble.tex`, and
`figures/figure-style.tex`. Article-specific definitions are in
`preamble-local.tex`. The GitHub address printed in the PDF points to the article repository.
