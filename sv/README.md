# Energibokföring för drivna harmoniska ODE:er

[Läs artikeln (PDF)](physics-ode-energy-sv.pdf) · [Manuskript](physics-ode-energy-sv.md)

Tecknet hos $Xq'''q'$ avgör om en okänd term tillför eller absorberar effekt.
Exakta sinus- och polynomförlopp visar båda fallen; valet $X=LRC$ skalar
överföringen vid oförändrad rörelse. Ett hammarexempel kopplar massa,
motstånd och underlagets styvhet till slagets rörelse och den okända
termens arbete; ett exempel med ett roterande verktyg tillämpar samma regel.
Båda ger skenbara COP-värden för motståndsarbete och elastisk energilagring
i förhållande till ursprunglig rörelseenergi och pålagt arbete, med den
okända termens bidrag räknat separat.
Komponentens fysiska identitet och återstående energibokföring lämnas öppna.

[ODE-mallen](https://github.com/hobnilre/physics-ode-template) ger bytena
mellan domäner, [koefficientsyntesen](https://github.com/hobnilre/physics-ode-coefficient-synthesis)
ger $X=A_{-1,3}=LRC$ och [regeln för seriekoppling](https://github.com/hobnilre/physics-ode-interconnect-ser-par)
bestämmer den gemensamma strömmen i effektbalansen.
