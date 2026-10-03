# Energy Ledgers for Forced Harmonic ODEs

Kirchhoff power balance, an unknown third derivative, and X = LRC.

Local draft; not published.

## What this article adds, and why it matters

Multiplying the forced harmonic LRC equation by current gives a power balance.
The article derives every energy expression from a signed power integral,
then fills in the heat recipient and forcing source equations that make the
total ledger constant. A finite capacitor has its own source equation, and
an exact charging example evaluates all interval transfers separately.

A second part adds the fictional voltage term X q''' with X positive and its
physical identity unknown. Integration by parts exposes both a boundary term
and a trajectory integral. Exact numerical examples show when the new port
absorbs energy, when it supplies energy, and which additional account must
receive the matching debit or credit.

A third part assumes only the numerical coefficient relation X = LRC.
It checks dimensions and compares absolute cycle work, average power, and
delivery relative to resistor heating. Component choices depend on the
amplitude and frequency held fixed; a maximum requires specified bounds.
The coefficient relation supplies no physical mechanism for X.

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
