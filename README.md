# Energy Ledgers for Forced Harmonic ODEs

Heat, forcing and a fictional third derivative.

Local draft; not published.

## What this article adds, and why it matters

The article derives energy transfers by integrating signed power in the forced
harmonic equation L q'' + R q' + q/C = v(t), with corresponding forms in other
physical domains. Heat received by the surroundings and work supplied or
absorbed by the source have equal-and-opposite entries in coupled differential
equations. Under the stated assumptions, their complete ledger sums to zero.

The second section adds only the fictional term X q''' to that equation.
Exact integration by parts exposes a boundary cross term and an additional
power integral. A sinusoidal cycle identifies precisely how much energy an
extra account must supply or receive. Assigning an account is distinguished
from demonstrating a physical component. No numerical integration or
simulations are used, and familiar storage formulas are derived from power.

## Article and build

[Read the article (PDF)](physics-ode-energy.pdf) ·
[Manuscript source](physics-ode-energy.md)

Install GNU Make, GNU Coreutils, Pandoc, XeLaTeX and the TeX Gyre fonts, including
the LaTeX packages used by `preamble.tex` and `preamble-local.tex`. Run `make pdf`
from this directory. The build requires no sibling repository or private files.

The title date records the first version and stays fixed across revisions. The
PDF creation timestamp advances only on a rebuild. `make -B pdf` forces one.
Build intermediates go to ignored `build/` by default; `BUILD_DIR=/absolute/path`
selects another location. `make clean` removes that directory and keeps the PDF.

Typography is installed locally in `article-style.yaml`, `preamble.tex`
and `figures/figure-style.tex`. Article-specific definitions are in
`preamble-local.tex`. The GitHub address printed in this local draft is the
configured future destination; no remote publication has been made.
