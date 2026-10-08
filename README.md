# Energy Ledgers for Forced Harmonic ODEs

Kirchhoff power balance and an unknown component with X = LRC.

[Article repository](https://github.com/hobnilre/physics-ode-energy).

## Focus

Parts 2 and 3 develop the main argument: the signed power of an unknown
term X q''' determines whether it supplies or absorbs energy, and the
coefficient relation X=LRC scales that transfer on a fixed trajectory.
Exact sinusoidal and polynomial examples show both roles. Positive
coefficients alone cannot reverse the direction of transfer.

Part 1 establishes the Kirchhoff power ledger and its missing accounts.
Parts 4 and 5 briefly apply the same sign and scaling rules to a hammer
and to rotary output motion, with exact work integrals. The component's
physical identity and remaining energy account stay open.

[Read the article (PDF)](physics-ode-energy.pdf) ·
[Manuscript source](physics-ode-energy.md)

[Earlier Swedish edition / Tidigare svensk version](https://github.com/hobnilre/physics-ode-energy-sv).

## Four related articles

| Article | Main role |
| --- | --- |
| [Template](https://github.com/hobnilre/physics-ode-template) | Common equation, domain dictionary, duality and harmonic convention. |
| [Coefficient synthesis](https://github.com/hobnilre/physics-ode-coefficient-synthesis) | Coefficient family, LRC table, stairs and phasor factors. |
| [Interconnection](https://github.com/hobnilre/physics-ode-interconnect-ser-par) | Series/parallel constraints, initial coordinates, elimination and phasor solutions. |
| [Energy](physics-ode-energy.pdf) | Signed power and work of the added term, with fixed-motion coefficient scaling. |

Each article states its local assumptions. Shared derivations are linked
where they are used. The energy article uses the coefficient-synthesis
article for $A_{-1,3}=LRC$.

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
