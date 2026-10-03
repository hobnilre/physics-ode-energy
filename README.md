# Energy Ledgers for Forced Harmonic ODEs

Kirchhoff power balance and an unknown component with X = LRC.

Local draft; not published.

## What this article adds, and why it matters

The article follows three questions. First, multiplying the harmonic LRC
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
`preamble-local.tex`. The GitHub address printed in the PDF is the configured
future destination for this local draft.
