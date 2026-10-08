# Energy Ledgers for Forced Harmonic ODEs

[Read the article (PDF)](physics-ode-energy.pdf) · [Manuscript](physics-ode-energy.md)

The sign of $Xq'''q'$ determines whether an unknown term supplies or
absorbs power. Exact sinusoidal and polynomial trajectories show both roles;
choosing $X=LRC$ scales the transfer on fixed motion. Short hammer and rotary
examples apply the rule while leaving the component's physical identity and
remaining energy account open.

The [ODE template](https://github.com/hobnilre/physics-ode-template) gives
the domain substitutions, [coefficient synthesis](https://github.com/hobnilre/physics-ode-coefficient-synthesis)
gives $X=A_{-1,3}=LRC$, and the [series connection rule](https://github.com/hobnilre/physics-ode-interconnect-ser-par)
fixes the common current in the power balance.

## Build

Install GNU Make, GNU Coreutils, Pandoc, XeLaTeX, the TeX Gyre fonts and the
LaTeX packages used by the included preambles and figures. Run `make pdf`;
all build inputs are in this repository.

The title date stays fixed; the PDF creation timestamp advances on rebuild.
Use `make -B pdf` to force a rebuild. Intermediates go to ignored `build/`,
or to the path set by `BUILD_DIR`. `make clean` removes that directory and
keeps the article PDF and figure assets.

<!-- article-tools:translations:start -->
## Translations

- Svenska: [PDF](sv/physics-ode-energy-sv.pdf) · [Markdown](sv/physics-ode-energy-sv.md)

<!-- article-tools:translations:end -->
