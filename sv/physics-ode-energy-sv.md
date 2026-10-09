---
title: "Energibokföring för drivna harmoniska ODE:er"
subtitle: "Kirchhoffs effektbalans och en okänd komponent med X = LRC"
author: "Hob Nilre & Bo C. Herlin"
date: "2026-10-08"
lang: sv
abstract: |
  En tillagd term $Xq'''$ tillför eller absorberar energi beroende på tecknet
  hos $Xq'''q'$. Exakta förlopp visar båda fallen. Valet $X=LRC$
  skalar överföringen vid oförändrad rörelse men bestämmer inte dess riktning.
  Exempel med en hammare och ett roterande verktyg tillämpar samma regel
  och ger skenbara COP-värden för angivna energiinsatser, där komponentens
  bidrag inte ingår.
  Det räknade utbytet omfattar motståndsarbete och elastisk energilagring;
  komponentens fysiska identitet och återstående energibokföring lämnas öppna.
keywords:
  - Kirchhoffs spänningslag
  - harmoniska ordinära differentialekvationer
  - effektbalans
  - energibokföring
  - okänd komponent
  - slagskruvdragare
  - hammare och spik
---

\begingroup\scriptsize
\noindent PDF created: \pdfbuildtimestamp\par
\noindent Latest on GitHub: \url{https://github.com/hobnilre/physics-ode-energy}\par
\endgroup

Denna svenska version följer [den engelska originalartikeln][original].

# Från spänningsbalans till effektkonton

Utgå från den drivna [LRC-mallen][template], avsnitt 2:
\begin{equation}
Lq''+Rq'+\frac qC=f(t),
\qquad L,C>0,\quad R\geq0.
\label{eq:base}
\end{equation}
Här är $q$ laddning, $i=q'$ ström, $f$ drivspänning och $L,R,C$
induktans, resistans respektive kapacitans. Koefficienterna är konstanta,
förloppen glatta och primtecken anger tidsderivator.
Med [konventionen för seriekoppling][interconnect], avsnitt 1, multipliceras
varje spänningsterm med samma ström. Sätt källan först och bokför kretsens
effektbalans på rad 2, med motsatta överföringar på raderna 1 och 3:
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
Rad 1 hör till värmemottagaren och rad 3 till källan eller mottagaren;
$fi<0$ betyder att källan tar emot energi. Poster med motsatta tecken
bokför varje överföring på båda sidor. För att visa att den totala energin
är konstant behövs också de utelämnade energiändringarna per tidsenhet och
lagarna för reservoarerna; ett föreskrivet $f(t)$ anger inte källans kapacitet.

# När den tillagda termen tillför eller absorberar

Lägg till en fiktiv komponent med konstant $X>0$ och okänd fysisk identitet:
\begin{equation}
Xq'''+Lq''+Rq'+\frac qC=f(t).
\label{eq:third}
\end{equation}
Om $Xq'''$ behandlas som dess spänningsbidrag tillkommer ett fjärde konto:
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
Den mottagna effekten och bidraget till rad 2 blir då
\begin{equation}
P_X=Xq'''i,\qquad P_{X\to2}=-Xq'''i.
\label{eq:x-powers}
\end{equation}
Eftersom $X>0$ tillför komponenten effekt när $q'''i<0$ och absorberar
effekt när $q'''i>0$. Ingen effekt överförs när produkten är noll.
Över ett intervall gäller
\begin{equation}
W_X(t_0,t_1)=\int_{t_0}^{t_1}Xq'''(t)i(t)\,dt,
\qquad W_{X\to2}=-W_X.
\label{eq:x-work}
\end{equation}
Positivt $W_X$ är mottagen nettoenergi; negativt $W_X$ är tillförd
nettoenergi. Integralen bestämmer överföringen, medan resten av rad 4 lämnas öppen.

Välj $L=1\,\mathrm H$, $R=1\,\Omega$, $C=1\,\mathrm F$ och
$X=1\,\mathrm{H\,s}$. Sätt $u=t/(1\,\mathrm s)$ och bestäm $f(t)$
genom att sätta in varje valt förlopp i \eqref{eq:third}.

**Tillförsel.** För
\begin{equation}
q=(1\,\mathrm C)\sin u,\qquad
i=(1\,\mathrm A)\cos u,\qquad
q'''=-(1\,\mathrm{A/s^2})\cos u,
\label{eq:supplier}
\end{equation}
tar de induktiva och kapacitiva termerna ut varandra, liksom resistans- och
$X$-termerna, vilket ger $f(t)=0$. Därmed gäller
\begin{equation}
P_X=-(1\,\mathrm W)\cos^2u,\qquad
W_X(0,2\pi\,\mathrm s)=-(1\,\mathrm J)\int_0^{2\pi}\cos^2u\,du
=-\pi\,\mathrm J.
\label{eq:supplier-work}
\end{equation}
Vid $t=0$ tillför komponenten $1\,\mathrm W$; under en period tillför den
$\pi\,\mathrm J$. Här är $P_X=-Ri^2$ i varje ögonblick, så överföringen
täcker resistorns energiupptag. Ekvationen anger inte dess fysiska energikälla.

**Absorption.** På $0\leq t\leq1\,\mathrm s$ väljs
\begin{equation}
q=(1\,\mathrm C)\frac{u^3}{6},\qquad
i=(1\,\mathrm A)\frac{u^2}{2},\qquad
q'''=1\,\mathrm{A/s^2}.
\label{eq:absorber}
\end{equation}
Nu gäller
\begin{equation}
f(t)=(1\,\mathrm V)\left(1+u+\frac{u^2}{2}+\frac{u^3}{6}\right),
\qquad P_X=(1\,\mathrm W)\frac{u^2}{2},
\label{eq:absorber-forcing}
\end{equation}
och
\begin{equation}
W_X=(1\,\mathrm J)\int_0^1\frac{u^2}{2}\,du=\frac16\,\mathrm J.
\label{eq:absorber-work}
\end{equation}
Vid $t=1\,\mathrm s$ är $P_{X\to2}=-1/2\,\mathrm W$. Samma positiva
koefficient tillför energi i sinusförloppet och absorberar den i detta polynomförlopp.

# Vad valet $X=LRC$ ändrar

För $(a,b,c)=(L,R,1/C)$ väljer [*ODE Coefficient Synthesis*][synthesis],
avsnitt 1--3,
\begin{equation}
X=A_3=A_{-1,3}=\frac{ab}{c}=LRC>0.
\label{eq:coefficient}
\end{equation}
Här är $R>0$. Eftersom $RC$ har tidsenhet gäller $[X]=\mathrm{H\,s}$,
och $Xq'''$ är en spänning. Ekvation \eqref{eq:x-powers} blir
$P_{X\to2}=-LRC\,q'''i$.

Håll $q(t)$ fast, inklusive amplitud och tidsskala. Ett större $LRC$
förstärker då överföringen i den riktning som $q'''i$ redan bestämmer.
Arbetet, med sitt tecken, skalas på samma sätt över ett fast intervall.
Med oberoende positiva parametergränser fås störst absolutbelopp vid alla
tre övre gränserna; utan gränser finns inget ändligt maximum.
Beräkna om $f(t)$ för att behålla den valda rörelsen.

För $q=Q\sin(\omega t)$, med $Q,\omega>0$, gäller
\begin{equation}
q'''=-\omega^2i,\qquad P_{X\to2}=LRC\,\omega^2i^2\geq0.
\label{eq:sinusoidal-sign}
\end{equation}
Alla positiva val gör att $X$ tillför effekt, utom vid strömmens nollställen.
Absorption kräver ett annat derivatatecken, som i \eqref{eq:absorber}.
I förhållande till resistorns effektupptag gäller, vid $i\ne0$,
\begin{equation}
\frac{|P_{X\to2}|}{Ri^2}=LC\left|\frac{q'''}i\right|.
\label{eq:relative}
\end{equation}
Kvoten är $LC\omega^2$ för ett sinusförlopp. Ett större $R$ skalar båda
effekterna lika mycket; bara $L$ och $C$ ändrar deras kvot vid oförändrad rörelse.

Använd det tillförande fallet i avsnitt 2 vid $t=0$ och det absorberande
fallet vid $t=1\,\mathrm s$, med drivspänningen omräknad för varje rad.

| $(L,R,C)$ i $(\mathrm H,\Omega,\mathrm F)$ | $X$ ($\mathrm{H\,s}$) | Tillförsel ($\mathrm W$) | Absorption ($\mathrm W$) |
| :--------------------------- | --------------: | ------------------: | ------------------: |
| $(1,1,1)$ | $1$ | $+1$ | $-1/2$ |
| $(1,2,1)$ | $2$ | $+2$ | $-1$ |
| $(2,2,2)$ | $8$ | $+8$ | $-4$ |

: Bidrag $P_{X\to2}$ med bevarat tecken för samma två förlopp.

Med $1\leq L/(1\,\mathrm H),R/(1\,\Omega),C/(1\,\mathrm F)\leq2$
ger sista raden störst absolutbelopp i båda fallen. Samma integraler ger
$8\pi\,\mathrm J$ tillförd energi per sinusperiod och $4/3\,\mathrm J$
absorberad energi över polynomförloppets intervall.

Om drivningen och begynnelsevillkoren i stället hålls fasta ändras även
rörelsen när koefficienterna ändras. Att maximera enbart $LRC$ säger då
ingenting om den största överföringen.

# Hammare och spik

Låt $x$ vara hammarytans och spikhuvudets förskjutning under en kontaktfas
med glatt förlopp, $v=x'$, och $m,d,k>0$ massa, effektivt motstånd respektive
styvhet. [Översättningen mellan domäner][template], avsnitt 2--3,
ersätter $(L,R,C)$ med $(m,d,1/k)$:
\begin{equation}
X_hx'''+mx''+dx'+kx=F(t),\qquad X_h=\frac{md}{k}.
\label{eq:hammer-third}
\end{equation}
Anta att den okända komponenten verkar inuti hammaren. Dess mottagna
effekt är $X_hx'''v$; skalningen vid fast rörelse i avsnitt 3 blir $md/k$.

Tänk på $m$ som hammarens tyngd, $d$ som det motstånd den rörliga spiken
möter och $k$ som styvheten i kontakten, arbetsstycket och underlaget.
Här beskriver $dv$ motståndsförluster med en enkel hastighetsberoende
kraft, medan $kx$ är den återförande kraften från elastisk eftergivlighet.
Det ovana $x'''$ anger hur snabbt accelerationen ändras. Medan
hammarhuvudet rör sig framåt ger en allt kraftigare inbromsning
$x'''v<0$, så att den okända komponenten tillför effekt; när inbromsningen
avtar blir tecknet det motsatta, så att komponenten absorberar effekt.

För $F=0$, $x(0)=0$, $v(0)=v_0>0$ och $x''(0)=0$, sätt $\omega=\sqrt{k/m}$.
Fram till första stoppet gäller
\begin{equation}
x(t)=\frac{v_0}{\omega}\sin(\omega t),\qquad
0\leq t\leq t_*:=\frac{\pi}{2\omega}.
\label{eq:hammer-motion}
\end{equation}
Då är $mx''+kx=0$ och $X_hx'''+dv=0$, vilket ger
\begin{equation}
W_{X_h}=\int_0^{t_*}X_hx'''v\,dt
=-\int_0^{t_*}dv^2\,dt
=-\frac{\pi d v_0^2}{4\omega}=-W_d.
\label{eq:hammer-work}
\end{equation}
Komponenten tillför motståndsarbetet från sitt ospecificerade konto.

För att förstå detta idealiserade slag genom sådant vi känner igen,
ändra en koefficient i taget och håll de andra två och hastigheten
$v_0$ vid anslaget oförändrade. Hammarhuvudet förflyttas
$x(t_*)=v_0/\omega$ fram till sitt första stopp.

Ett större $m$ motsvarar en tyngre hammare. Vid samma hastighet hos
hammarhuvudet är trögheten större: det tar längre tid att stanna och
huvudet rör sig längre. Ett mindre $m$ ger en kortare förflyttning och
ett tidigare stopp. Den större massan ökar också $X_h$; vid dessa slag
tillför den okända komponenten mer arbete när motståndet verkar över
den längre förflyttningen. Samma hastighet vid anslaget innebär inte
att det krävs samma ansträngning för att svinga den tyngre hammaren.

Ett större $d$ motsvarar starkare motstånd vid samma hastighet---som
när en spik kärvar mer.
Ett mindre $d$ motsvarar att spiken går lättare. Extra motstånd skulle
ändra en vanlig hammares rörelse. I just detta slag ger dock ett
större $d$ också ett större $X_h$, så att den okända komponenten tillför precis det
extra motståndsarbetet. Stopptiden och hammarhuvudets förflyttning
förblir oförändrade, medan motståndsarbetet och komponentens tillförda
arbete båda ökar i proportion till $d$. Om $d$ minskar, minskar båda.
Att termerna tar ut varandra är den antagna komponentens särskilda
förutsägelse för det angivna rörelseförloppet.

Ett större $k$ motsvarar ett fastare underlag: en bräda med stöd nära
spiken ger efter mindre än en som kan böjas under slaget. Vid en given
förskjutning blir den återförande kraften större, och detta idealiserade
slag stannar tidigare efter en kortare förflyttning. Ett mindre $k$
låter rörelsen pågå längre och nå längre. Eftersom eftergivligheten
är $1/k$ minskar ett fastare underlag $X_h$ och, vid dessa slag, det
arbete som den okända komponenten tillför; ett mjukare underlag ökar
båda. Extra förflyttning hos hammarhuvudet kan vara elastisk böjning
av stödet. Spikens bestående inträngningsdjup förblir obestämt i modellen.

För ett prestandatal (COP) räknar vi arbetet som överförs till modellens
motstånd och fjäder som utbyte. Som insats räknar vi den ursprungliga
rörelseenergin och det pålagda arbetet, utan den okända komponentens
tillförda arbete. Vi kallar denna kvot ett skenbart COP-värde. För det
angivna slaget är energierna vid intervallets ändpunkter och arbetet på lasten
\begin{equation}
\begin{aligned}
K_0&=\frac12mv_0^2,\qquad
U_*:=\frac12kx(t_*)^2=K_0,\\
W_{\mathrm{load},h}&=\int_0^{t_*}(dv+kx)v\,dt=W_d+U_*.
\end{aligned}
\label{eq:hammer-load-work}
\end{equation}
Eftersom $F=0$ är det pålagda arbetet $\int_0^{t_*}Fv\,dt$ noll. Därmed fås
\begin{equation}
\mathrm{COP}_{\mathrm{app},h}
=\frac{W_{\mathrm{load},h}}{K_0}
=1+\frac{\pi d}{2\sqrt{mk}}.
\label{eq:hammer-cop}
\end{equation}
Till exempel ger $d=\sqrt{mk}$ värdet $1+\pi/2\approx2{,}57$. Vid samma
jämförelser, med en koefficient ändrad i taget och fast $v_0$, ökar kvoten
med $d$ men minskar med $m$ eller $k$. En tyngre hammare får mer arbete
från komponenten under detta slag, men dess ursprungliga rörelseenergi
växer snabbare. Kvoten räknar både dissiperat arbete och återvinningsbar
elastisk energi; ingen av dessa storheter mäter ensam spikens bestående
inträngning.

# Roterande utgång vid föreskriven rörelse

För utgångens vinkel $\theta$ och vinkelhastighet $\Omega=\theta'$ görs bytet
$(q,L,R,C,f)\mapsto(\theta,J,d,1/k,\tau_h)$ i \eqref{eq:third}.
Här är $J,d,k>0$ utgångens tröghetsmoment, dämpning och vridstyvhet;
$\tau_h$ är föreskrivet hammarmoment och $J$ omfattar inte hammaren.
Den antagna komponenten inuti verktyget har $X_r=Jd/k$.
Låt $\tau_X$ och $\tau_0$ vara de moment som krävs för samma rörelse med
respektive utan komponenten. Skillnaden i tillfört arbete är
\begin{equation}
\Delta W_h=\int_{t_0}^{t_1}(\tau_X-\tau_0)\Omega\,dt
=\int_{t_0}^{t_1}X_r\theta'''\Omega\,dt=W_{X_r}.
\label{eq:rotary-work-difference}
\end{equation}
Tillfört arbete från komponenten minskar alltså det hammararbete som krävs för denna rörelse.

För $\theta=\Theta\sin(\omega t)$, $\Theta,\omega>0$, och
$T=\pi/(2\omega)$ ger sambandet $\theta'''=-\omega^2\Omega$
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
När $J\omega^2/k\leq1$ ger en vanlig modell samma moment vid
denna rörelse med icke-negativ dämpning
\begin{equation}
d_{\mathrm{eff}}=d-X_r\omega^2=d\left(1-\frac{J\omega^2}{k}\right).
\label{eq:rotary-effective-damping}
\end{equation}
Till exempel ger $J\omega^2/k=1/10$ att $d_{\mathrm{eff}}=9d/10$ och
$W_{X_r}=-W_d/10$. Komponenten tillför arbete som minskad dämpning
i stället undviker att dissipera. Jämförelsen anpassar drivningen så att
rörelsen blir densamma; hammarens förberedelse och det okända kontot ingår inte.

Använd samma definition av skenbart COP-värde för intervallet med en
kvarts sinusperiod och välj $0<r:=J\omega^2/k\leq1$. Den ursprungliga
rörelseenergin och den slutliga elastiska energin är
\begin{equation}
U:=\frac12k\Theta^2,\qquad
K_0=\frac12J\Theta^2\omega^2=rU.
\label{eq:rotary-endpoint-energy}
\end{equation}
Motsvarande arbete på lasten och tillförda hammararbete fås genom att
integrera respektive effekt med dess tecken:
\begin{equation}
\begin{aligned}
W_{\mathrm{load},r}
&=\int_0^T(d\Omega+k\theta)\Omega\,dt=U+W_d,\\
W_h&=\int_0^T\tau_X\Omega\,dt
=U-K_0+(1-r)W_d=(1-r)(U+W_d).
\end{aligned}
\label{eq:rotary-cop-work}
\end{equation}
Här är $\tau_X=J\theta''+d\Omega+k\theta+X_r\theta'''$ det hammarmoment
som krävs med komponenten. När utgångens ursprungliga rörelseenergi
räknas med i nämnaren fås
\begin{equation}
\mathrm{COP}_{\mathrm{app},r}
=\frac{W_{\mathrm{load},r}}{K_0+W_h}
=\frac{U+W_d}{U+(1-r)W_d}.
\label{eq:rotary-cop}
\end{equation}
För $r=1/10$ ger det ytterligare valet $W_d=U$, likvärdigt med
$d\omega/k=2/\pi$, värdet $\mathrm{COP}_{\mathrm{app},r}=20/19\approx1{,}053$.
Att tillföra en tiondel av dämpningsarbetet innebär alltså inte att den
totala räknade energiinsatsen minskar med tio procent.

I båda exemplen överstiger kvoten ett därför att komponentens tillförda
arbete inte räknas med i insatsen. Om $-W_{X_h}=W_d$ respektive $-W_{X_r}=rW_d$
tas med i nämnaren blir kvoten exakt ett. Dessa identiteter för intervallet
lämnar komponentens återstående energibokföring öppen. Ett praktiskt
COP-värde för verktyget kräver dessutom ett definierat nyttigt utbyte i
spikdrivning eller åtdragning samt energikostnaden för förberedelse och
återställning av energitillgången.

# Referenser {-}

1. H. Nilre och B. C. Herlin (2026). [The ODE Template and Its Domain Equivalents][template].
2. H. Nilre och B. C. Herlin (2026). [ODE Coefficient Synthesis][synthesis].
3. H. Nilre och B. C. Herlin (2026). [Interconnecting Series and Parallel ODEs][interconnect].

[template]: https://github.com/hobnilre/physics-ode-template
[synthesis]: https://github.com/hobnilre/physics-ode-coefficient-synthesis
[interconnect]: https://github.com/hobnilre/physics-ode-interconnect-ser-par

[original]: https://github.com/hobnilre/physics-ode-energy/blob/main/physics-ode-energy.md
