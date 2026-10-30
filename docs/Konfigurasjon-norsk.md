# VoltDeck: illustrert konfigurasjonsguide

[Visningsgalleri: Deck og Digital med/uten bilde, valg og telemetrikilder](Visningsgalleri-norsk.md)

[Hjem](../README.md) | [Installasjon](../README.md#install-voltdeck) | [English](Configuration.md)

**Før installasjon:** ta backup av ETHOS-modellen og `/scripts/vc3*.cfg`-parene. Les
[VD8 backup og tilbakeføring](#vd8-backup-og-tilbakeføring); v10 kan ikke lese innstillinger lagret som VD8.

Bruk [pakken VoltDeck-2026.10-v11.zip](https://github.com/bliatun-code/VoltDeck/releases/download/voltdeck-2026.10-v11/VoltDeck-2026.10-v11.zip).
Samme ZIP brukes til begge installasjonsmåtene:

- **FrSky Suite:** Koble til radioen, åpne **Lua library**, velg **Install Lua scripts**, velg ZIP-filen og trykk **Install scripts**.
- **Manuelt:** Pakk ut ZIP-filen, opprett `/scripts/VoltDeck/` på radioens skriptdisk og kopier alle de fem utpakkede filene dit. Lua-filen skal ligge som `/scripts/VoltDeck/main.lua`.

Start ETHOS på nytt etter installasjonen. Ved første installasjon velger du
**VoltDeck** i et fullskjerms widgetfelt. Åpne **Configure widget** fra widgetmenyen
og kontroller versjonen øverst. Suite viser denne versjonen som **26.10.11**.
Hvis installasjonen ikke vises oppdatert i Suite, gå ut av og inn i **Lua library**.
Viser widgeten fortsatt en eldre versjon etter omstart, koble til radioen igjen,
fjern bare `/scripts/VoltDeck/main.luac` og start ETHOS på nytt.
Ta sikkerhetskopi av modellen før oppdatering. Behold widgeten som er satt opp og cfg/dat-filene;
lagrede innstillinger, kildevalg og flytellere beholdes.

**Fullskjerm:** Widgetfeltet må fylle hele LCD-flaten på radioen. Dette gjelder også radioer med lavere oppløsning. Et delt felt viser **Full screen required**; velg et fullskjermsfelt for å få instrumentene tilbake. **Screen size unavailable** betyr at skjermmål ikke kunne leses; appen prøver automatisk på nytt. Valgte kilder og innstillinger beholdes.

Se [oppgradering og tilbakeføring](Konfigurasjon-norsk.md#vd8-backup-og-tilbakeføring) før du går tilbake til en eldre utgave.

## VD8 backup og tilbakeføring

Før installasjon eller første start av v11: ta backup av **ETHOS-modellen** og kopier
alle eksisterende **`/scripts/vc3*.cfg`-filer** til datamaskinen. Behold også en fullstendig
filoversikt fra før installasjonen. Registrer om a/b-paret for hvert nøyaktige modellprefiks
opprinnelig har **0, 1 eller 2 filer**, og hvilken motpart som eventuelt mangler. En ufullstendig
kopi av mappen beviser ikke at en fil var fraværende. Behold den konfigurerte widgeten og
eksisterende flytellere i `.dat`-filer.
Hvis modellen ikke har et identifiserbart prefiks før oppgraderingen, behold hele før-listen.
Finn modellens opprettede/endrede filnavn etter å ha brukt bare denne modellen, og sammenlign
prefikset mot den fullstendige før-listen for å fastslå opprinnelig 0/1/2-tilstand før tilbakeføring.

VoltDeck v11 leser gamle **VD5-, VD6- og VD7**-innstillinger og bevarer de tidligere valgene.
Vanlig lagring skriver **VD8** med det nye feltet, også når minstegrensen står på standardverdien.
**Stabil v10 kan ikke lese en lagret VD8-record.** Bare å installere v10 gjenoppretter ikke
det gamle formatet. Arkiver først den oppgraderte modellen og cfg-filer separat. Installer
den opprinnelige v10-pakken og hent tilbake den opprinnelige modellen og **nøyaktig opprinnelig
filtilstand** for modellens cfg-par før v10 startes:

| Opprinnelige cfg-filer for modellen | Tilstand som skal gjenopprettes |
| --- | --- |
| 2 filer | Hent tilbake begge opprinnelige a/b-filer med nøyaktig samme filnavn og byte fra backupen. |
| 1 fil | Hent tilbake den opprinnelige filen. Hvis v11 opprettet motparten som manglet, arkiver og fjern bare denne nøyaktig navngitte motparten. |
| 0 filer | Arkiver først filene. Fjern deretter bare de nøyaktige a/b-filnavnene v11 opprettet for denne modellen, og som er bevist fraværende i den fullstendige før-listen. |

Bruk modellens nøyaktige prefiks; behold andre modellers filer. Registrer opprettede
filnavn før de fjernes. Sammenlign før-listen og originalbytene med den gjenopprettede mappen.
Bare å kopiere én gammel fil tilbake mens en nyere VD8-motpart ligger igjen, kan fortsatt sperre
v10. Å slette den nyeste filen alene er ingen tilbakeføringsprosedyre. Ikke omdøp VD8 til VD7
eller rediger checksummen.
Native kildevalg beholder sitt eksisterende lagringsformat, og flytellernes `.dat`-filer er uendret.

Følg gruppene nedenfor i samme rekkefølge som på radioen.
Innstillinger og kildevalg tilhører den aktive modellen.

Etter side- eller modellbytte kan første korte trykk velge widgeten og neste
åpne menyen. Se [Widgetmenyen](#widgetmenyen) for Home-menyen, Diagnostics og RTN.

Grå felt er inaktive for valgt metode eller visning. Lagrede verdier beholdes
når du bytter tilbake. Kildevelgeren bruker ETHOS sin vanlige liste; kontroller
både kildetype, enhet og navn.

Oppsettsbildene viser simulatorens menyfelt. Velg sensorene som finnes i din
modell; tabellene forklarer hva kildene skal måle. Visningseksemplene for
hovedskjerm og flylogg bruker illustrative verdier.

Widgetmenyen og Appearance-bildene nedenfor er tatt i 2026.10-v9 og beholdes som historiske referanser. Det nye Battery-feltet står i den oppdaterte tabellen. Eldre detaljbilder av kilder og varsler beholdes som feltreferanser; bruk tabellene for dagens grupperekkefølge og velg egne oppdagede sensorer.

<table>
<tr>
<td><img src="images/native-voltdeck-widget-menu.png" alt="VoltDecks widgetmeny"><br><b>Widgetmeny</b></td>
<td><img src="images/native-voltdeck-appearance.png" alt="VoltDeck Appearance"><br><b>Appearance</b></td>
</tr>
</table>

## 1. Appearance

<table>
<tr>
<td><img src="images/native-voltdeck-style-choices.png" alt="Display style: Deck / Digital"><br><b>Display style</b></td>
<td><img src="images/native-voltdeck-image-choices.png" alt="Image source: Selected model / Image file / Hidden"><br><b>Image source</b></td>
</tr>
</table>

| Felt | Hva det endrer |
|---|---|
| Display style | **Deck** eller **Digital**; Digital viser informasjonslinjen **Instrument focus: Power**. |
| Background | **Radio theme** følger ETHOS-fargene; **Black** gir svart bakgrunn; **Custom** bruker din bakgrunnsfarge. |
| Background color | Aktivt med **Custom**. |
| Accent color | Aktivt med **Black** eller **Custom**. **Radio theme** bruker temaets aksentfarge. |
| Font file | Valgfri fontsti. La feltet være tomt for radioens innebygde fonter. |
| Image source | **Selected model** gjenbruker modellbildet; **Image file** velger et separat bilde; **Hidden** skjuler det. |
| Image file | Aktivt med **Image file**. Velg bilde fra `/bitmaps/models`. |

Velg **Display style = Deck** for de stående batteriene og den kjente instrumenteringen. **Digital** gir en alternativ instrumentvisning med **Instrument focus: Power**. Fokuslinjen er informasjon om denne visningen. Deck er standard for nye modeller og innstillinger fra utgaver før Digital. Tidligere lagrede Deck/Digital-valg beholdes.

**Image source** er et eget valg i begge stiler: **Selected model**, **Image file** eller **Hidden**. Med Hidden brukes bildeplassen til større målinger. I Deck beholder et valgt modellbilde den kjente sammensetningen. En bildefeil beholder bildeplassen og viser feilen; manglende telemetri flytter heller ikke instrumentene.

Stil- og bildevalg endrer ikke beregningsmetoder, telemetrikilder, enheter, varsler, godkjenning eller flylogg. Grå felt beholder sine lagrede verdier.

Bruk vanlig **8-bit RGB eller RGBA PNG**. **290 × 191** passer bildefeltet;
**480 × 272** og **480 × 320** støttes også. Sideforholdet beholdes.
Grensen er 160 000 piksler, så **800 × 480** er for stort. Indekserte/palettbilder
og PNG med 16-bit fargekanaler støttes ikke. Gjennomsiktighet lar bakgrunnen
synes gjennom.

Eksempelbildet [Ultimate AMR](images/ultimate-amr.png) er 290 × 191;
se [NOTICE](../NOTICE.md) for bruksvilkår.

## 2. Battery

![Batteriinnstillinger](images/voltdeck-setup-battery.png)

Det eldre referansebildet viser ikke det nye **Idle current floor**-feltet rett etter **Remaining from**. Bruk den oppdaterte tabellen nedenfor.

| Felt | Hva du velger |
|---|---|
| Remaining from | **Consumed mAh** bruker kapasitet minus forbruk etter batterikontrollen nedenfor. **% sensor** bruker en kilde med gjenværende prosent. **Voltage estimate** anslår lading fra pakkespenning, batteritype og celletall. |
| Idle current floor | Standard **0,30 A**, justerbar til **1,50 A** i trinn på **0,10 A**. Aktiv bare med **Consumed mAh**. Effektiv grense er den høyeste av dette valget og kapasitetsgrensen, begrenset til 1,50 A. En verdiendring krever ny kontroll og beholder forbruk, tidtakere og flyteller. |
| Battery type | Lipo, LiHV, Li-ion eller LiFe, tilsvarende batteriet. Brukes av spenningsestimat, cellemålerens skala, forbrukskontroll, full-pack KV-skala og batterietikett. |
| Capacity | Batteriets kapasitet i mAh. Brukes også av **mAh display / Remaining** når batteriprosenten kommer fra en annen metode. |
| Cells | Antall celler i serie. Brukes av batterietikett, gjennomsnittlig cellevolt, forbrukskontroll, spenningsestimat og full-pack KV-skala. |
| mAh display | **Consumed** viser valgt forbruksavlesning. **Remaining** viser kapasitet minus godkjent forbruk. Denne separate mAh-visningen trenger **Consumed mAh**-telemetri også ved de to andre prosentmetodene. |

Med et kontrollert batteri på 2500 mAh og 650 mAh forbrukt blir gjenstående kapasitet 1850 mAh,
altså 74%. Sett opp forbrukssensorens nullstilling for hvert nytt eller oppladet
batteri; VoltDeck nullstiller ikke sensoren.

**Voltage estimate** er omtrentlig og påvirkes av belastning og spenningsfall.
**% sensor** trenger en kilde som faktisk gir gjenværende lading fra 0 til 100%.
En spenningskilde blir ikke omregnet til prosent bare ved å velges her.

Et uventet fall i forbrukstelleren gjør beregnet gjenværende kapasitet ukjent.
Kontroller faktisk lading og mAh-avlesning før du bruker
**Accept battery counter...**, beskrevet under [Widgetmenyen](#widgetmenyen).
Kort telemetribortfall eller dearming godtar ikke et tellerreset automatisk.

Med **% sensor** eller **Voltage estimate** beskytter denne resetsperren fortsatt
den valgfrie **mAh display / Remaining**. Godkjenning krever en gyldig faktisk
ARM-kilde AV, gyldig forbrukt mAh og aktuell pakkespenning når en spenningskilde
er valgt. Den påvirker bare gjenværende mAh; hovedprosenten følger fortsatt
valgt metode.

Hvis ESC-en starter på **0 mAh** hver gang modellen slås på, mangler avlesningen
forbruket fra tidligere turer med samme batteri. Ved flere turer uten lading
trengs en forbrukskilde som beholder dette forbruket. En kalkulert ETHOS-sensor
kan brukes; kontroller nullstillingsvalgene og prøv at totalen beholdes når
modellen slås av og på. Nullstill den bare ved nytt eller oppladet batteri.

### Kontroll før gjenværende lading vises

Med **Remaining from = Consumed mAh** viser radiooppstart eller oppdaget
batteribortfall **CHECKING PACK**, **-- %** og tomme batterisegmenter inntil
avlesningene er kontrollert. Gjenværende mAh er også ukjent under kontrollen;
**Consumed** kan fortsatt vise sensorens avlesning. Kontrollen gjelder ved alle
forbruksnivåer, ikke bare når telleren er nær null.

La batteriet stabilisere seg. VoltDeck trenger gyldig
pakkespenning, strøm og forbrukt mAh, fulgt av **10 sekunder med stabile
avlesninger ved lav strøm**. Strømmen må være minst null og innenfor grensen
for kontrollen. Effektiv grense er
`min(1,50 A; max(Idle current floor; 3 × kapasitet_mAh / 20000))`.
**Idle current floor** er normalt **0,30 A** og kan økes fra **0,30 til 1,50 A**
i trinn på **0,10 A**. Den eksisterende kapasitetsgrensen er **0,15 C**. Med standardverdien
tillater **450 mAh 0,30 A**, **2500 mAh 0,375 A**, **3000 mAh 0,450 A** og **4000 mAh 0,60 A**.
En høyere kapasitetsgrense gjelder fortsatt når den overstiger valgt minstegrense.
En verdiendring forkaster det gamle kontrollvinduet og en gammel bekreftelse straks, og krever
en ny ti-sekunderskontroll. Forbruk, tellerreset-vern, tidtakere og flyteller beholdes.
Null strøm er også gyldig. Forskjellen mellom høyeste og laveste spenning kan være høyst
**0,20 V for hele pakken**, ikke per celle. Høyere strøm, manglende avlesninger
eller større spenningsvariasjon starter målevinduet på nytt. Det er ingen egen
ventetid. **Arm switch** sperrer ikke denne batterikontrollen; den styrer
fortsatt flyloggingen.

Kontrollen sammenligner tellerens gjenværende prosent med en grov
spenningsreferanse for valgt batteritype. Mulig overestimering kontrolleres mot
vinduets **laveste spenning**, og underestimering mot **høyeste spenning**.
Det største avviket bestemmer resultatet, målt i **prosentpoeng**.
Dialogen avrunder avviket opp til nærmeste 0,1 prosentpoeng; trekker du de to
avrundede prosentene fra hverandre, kan resultatet derfor bli 0,1 poeng lavere.

| Avvik | Resultat |
|---|---|
| 10 prosentpoeng eller mindre | Godtas automatisk; beregnet prosent og batterisegmentene vises. |
| Over 10, til og med 20 prosentpoeng | **CHECK PACK/COUNTER** beholdes i rødt og gjenværende lading er ukjent. Kontroller batteri og sensor, og bruk **Accept battery counter...** for å lese begge prosentene og avviket før bekreftelse. |
| Over 20 prosentpoeng | Gjenværende lading forblir ukjent. Rett lading, batteriinnstillinger eller forbruksavlesning; menyen kan ikke omgå denne grensen. |

**Accept battery counter...** viser hva som hindrer kontrollen, blant annet
manglende eller uegnede kilder, målt strøm mot grensen, spenningsvariasjon eller
fremdrift i 10-sekundersvinduet. Et høyere tellerestimat varsler om mulig
overestimering; et lavere ber deg kontrollere forbruk, kapasitet og kalibrering
av sensoren. Bekreftelsen bruker det kontrollerte spenningsområdet, slik at
variasjon innenfor området ikke krever en identisk øyeblikksavlesning.
Aktuell telemetri og batterioppsettet må fortsatt være gyldige når du bekrefter.

For **LiFe** gir spenning ingen pålitelig prosentvis sammenligning.
Etter samme lavstrømskontroll må du kontrollere faktisk lading, kapasitet og
forbrukt mAh og bekrefte med **Accept battery counter...**. Denne batteritypen
har ingen beregnet spenningsprosent eller avviksverdi å godkjenne.

Godkjenningen gjelder denne batteritilkoblingen. Under flyging bruker VoltDeck
telleren uten å gjenta spenningssammenligningen, slik at spenningsfall under
belastning ikke trekker godkjenningen tilbake. Et tellerreset krever fremdeles
eksplisitt godkjenning. Sammenhengende bortfall av **Pack voltage** i **Pack loss
delay**, også ved bortfall av all modelltelemetri, krever ny kontroll. Omstart
av radioen eller endring av batterikilder, kapasitet, celletall eller type gir
også ny kontroll. Retur etter et langt opphold i widgetens batteriavlesninger
kan også kreve ny kontroll. Kortere gap beholder godkjenningen, men manglende
aktuell spenning eller forbruk viser fortsatt ukjent lading.

Dette er en plausibilitetskontroll ved stabil, lav belastning, ikke en måling
av lading etter full hvile. De separate referansene bruker [STs OCV-tabeller
for 4,20 V og 4,35 V](https://github.com/st-sw/STC3115GenericDriver/blob/master/Docs/Config/STC3115%20OCV%20curve%20-%20default%20register%20values.pdf)
for henholdsvis Lipo/Li-ion og LiHV. Temperatur, alder, selve batteriet og
gjenværende belastning påvirker resultatet. Visningen **Voltage estimate**
beholder sin eksisterende skala, også **3,57 V = 30%** for Lipo; den er ikke
referansen for denne kontrollen.

**CHECK CELLS/TYPE** betyr at høyeste spenning i kontrollen overstiger full
cellevolt for valgt batteritype med mer enn 0,15 V/celle. Rett
**Cells**, **Battery type** eller spenningskilden; varselet kan ikke godtas bort
med tellermenyen. Totalspenningen kan ikke fastslå riktig celletall.

Kontroller batteriet og sensoren før du godtar en teller. **Ikke godta 0 mAh på
et delvis brukt batteri**: gjenopprett korrekt akkumulert forbruk, sett inn et
oppladet batteri eller velg **Voltage estimate** med begrensningene det har.
Kontrollen kan ikke gjenfinne manglende forbruk eller verifisere en feil strømkilde.
**Kontroller at batteriet er fulladet før hver flyging.** Sammenlign rapportert
forbruk i mAh med det laderen fyller tilbake over flere turer, til samme
ladenivå hver gang. Undersøk systematiske forskjeller og følg ESC-produsentens
kalibreringsanvisning dersom dette støttes; for eksempel har
[Scorpion Tribunus II Current Sensitivity Gain](https://www.scorpionsystem.com/files/download/Tribunus%20II%20Instructions%20-%20220922.pdf).
En bestått kontroll garanterer ikke en bestemt reserve ved landing.

<table>
<tr>
<td><img src="images/battery-checking.png" alt="Batterikontroll pågår"><br><b>Checking pack</b><br>Gjenværende lading er ukjent under kontrollen ved stabil, lav strøm.</td>
<td><img src="images/battery-manual-confirm.png" alt="Bekreftelse med 14 prosentpoeng avvik"><br><b>Manuell bekreftelse</b><br>Les begge estimatene og avviket før du godtar telleren.</td>
</tr>
<tr>
<td><img src="images/battery-counter-check.png" alt="Varsel om forbrukstelleren"><br><b>Check pack/counter</b><br>6S Lipo ved 22,9 V, 303 mAh og 0 A: gjenværende lading er ukjent.</td>
<td><img src="images/battery-blocked-dialog.png" alt="Avvik over 20 prosentpoeng med bare Close-knapp"><br><b>Over 20 prosentpoeng</b><br>Dialogen forklarer spriket; det kan ikke godkjennes.</td>
</tr>
<tr>
<td colspan="2"><img src="images/battery-cells-check.png" width="400" alt="Varsel om celletall eller batteritype"><br><b>Check cells/type</b><br>25,2 V med 5S valgt: rett batterioppsettet.</td>
</tr>
</table>

### Alerts i Battery

![Batterivarsling](images/voltdeck-setup-alert.png)

| Felt | Funksjon |
|---|---|
| Battery alert | Slår på widgetens batterilyd ved **30% eller lavere**. |
| Alert on estimate | Aktivt når varsling er på og **Remaining from = Voltage estimate**. Tillater lydvarsel basert på det omtrentlige spenningsestimatet. |
| Repeat | Minstetid mellom varsler, i sekunder. Aktivt når varsling er på. |
| Audio folder | Mappe for lydvelgeren, normalt `/audio`. Aktivt når varsling er på. Endre mappen og åpne konfigurasjonen på nytt før du velger fil. |
| Alert WAV | Aktivt når varsling er på. Velg PCM WAV: **32 kHz, mono, 16-bit**. Manglende eller ugyldig fil gir en tone. |

Neste varsel venter til valgt lyd er ferdig. Kort tilbakekomst eller manglende
avlesninger starter ikke venteintervallet på nytt. Preview spiller ikke varsler.
Disse valgene endrer ikke ETHOS sine egne telemetrialarmer.

## 3. Telemetry

![Telemetrikilder](images/voltdeck-setup-telemetry.png)

![Resterende telemetrikilder](images/voltdeck-setup-telemetry-more.png)

Velg målekilder fra **Telemetry**, og en ETHOS-timer til **Flight timer**.
Liknende sensornavn kan ha forskjellige enheter.

| Felt, i menyrekkefølge | Måling og bruk |
|---|---|
| Pack voltage | Hele motorbatteriets spenning i **V**; **mV** omregnes til V. Brukes på hovedskjermen, til Watt, gjennomsnittlig cellevolt, spennings-/KV-estimat og batteriøkter. |
| Current | Motorbatteriets strøm i **A**; **mA** omregnes til A. Brukes på hovedskjermen, til Watt, høyeste strøm i flyloggen og innledende batterikontroll. |
| Consumed mAh | Akkumulert forbruk siden batteriet ble ladet, i **mAh**; **Ah** omregnes til mAh. Brukes av mAh-visning og forbruksbasert gjenværende kapasitet. Feltet er aktivt ved alle batterimetoder. |
| RF1 source | RSSI i **dB**, eller VFR/signalkvalitet i **%**, på første RF-plass. |
| RF2 source | RSSI i **dB**, eller VFR/signalkvalitet i **%**, på andre RF-plass. |
| Rx1 voltage | Første mottakerbatteris spenning i **V** eller **mV**. |
| Rx2 voltage | Andre mottakerbatteris spenning i **V** eller **mV**, dersom det finnes. |
| Tx voltage | Senderspenning i **V** eller **mV**. Tomt felt bruker radioens egen batterikilde. |
| Flight timer | En ETHOS-timer som gir sekunder. Denne timeren på hovedskjermen er uavhengig av flyloggens opptjente kvalifiseringstid. |
| Battery % source | Gjenværende lading i **%**, fra 0 til 100. Aktivt bare med **Remaining from = % sensor**. |

Bruk helst kilder med riktig ETHOS-enhet. Rå tallkilder for spenning, strøm,
forbruk og RPM må allerede gi henholdsvis V, A, mAh og rpm; enhetsteksten
skalerer ikke verdien. For **Battery % source** må en rå kilde ha eksplisitt
`%`-enhetstekst og gyldig verdi fra 0 til 100.
RF-kilder må ha ETHOS-enheten dB eller %; enhetstekst på en rå kilde er ikke nok.
Den innledende batterikontrollen krever faktiske ETHOS-enheter V/mV og A/mA.
Råkilder for spenning og strøm kan fortsatt brukes til vanlig visning, men kan
ikke godkjenne gjenværende lading fra **Consumed mAh**.

Manglende eller avviste målinger vises som **--**. Det betyr ikke null forbruk
eller fullt batteri. En inaktiv valgt RF-kilde beholder navn og enhet; andre
RF-enheter avvises. Radioens batteri og timer kan fortsatt være tilgjengelige
når modelltelemetrien er borte.

![Manglende modelltelemetri](images/native-voltdeck-missing-telemetry.png)

## 4. RF signals

![RF-profiler](images/voltdeck-setup-rf.png)

![Resterende RF-grenser](images/voltdeck-setup-rf-more.png)

| Felt, i menyrekkefølge | Funksjon |
|---|---|
| RF1 profile | **ACCESS / TD / TW**, **ACCST** eller **Custom**, for første RF-plass og dens flygraf. Velg protokollen, ikke bare etter frekvensen i sensornavnet. |
| RF2 profile | Samme valg for andre RF-plass og dens flygraf. |
| RSSI scale min | Nedre ende av RSSI-måler/-graf, i dB. |
| RSSI scale max | Øvre ende av RSSI-måler/-graf, i dB; må overstige minimum. VFR bruker alltid 0–100%. |
| RF1 low RSSI | Gul RSSI-grense i dB for plass 1; aktivt med **RF1 profile = Custom**. |
| RF1 critical RSSI | Rød RSSI-grense i dB for plass 1; aktivt med **Custom**. |
| RF1 early VFR | Gul VFR-grense i % for plass 1; aktivt med **Custom**. |
| RF1 low VFR | Rød VFR-grense i % for plass 1; aktivt med **Custom**. |
| RF2 low RSSI | Gul RSSI-grense i dB for plass 2; aktivt med **RF2 profile = Custom**. |
| RF2 critical RSSI | Rød RSSI-grense i dB for plass 2; aktivt med **Custom**. |
| RF2 early VFR | Gul VFR-grense i % for plass 2; aktivt med **Custom**. |
| RF2 low VFR | Rød VFR-grense i % for plass 2; aktivt med **Custom**. |

Velg **Custom** før du endrer grensene for den plassen. Både dB- og %-grensene
er tilgjengelige fordi hovedskjerm og graf kan bruke ulike typer RF-kilde.

| Profil | RSSI gul / rød | VFR gul / rød |
|---|---|---|
| ACCESS / TD / TW | ≤35 / ≤32 dB | ≤95 / ≤50% |
| ACCST | ≤45 / ≤42 dB | ≤95 / ≤50% |
| Custom | Dine grenser for plassen | Dine grenser for plassen |

Dette er visuelle grenser. De setter ikke radioens alarmer;
95% er VoltDecks tidlige VFR-markering, ikke en ETHOS-alarmgrense.

## 5. Lower deck

![Nedre visning](images/voltdeck-setup-lower-deck.png)

![Resterende innstillinger for nedre visning](images/voltdeck-setup-lower-deck-more.png)

| Felt | Funksjon |
|---|---|
| Show | **Only Custom**, **RPM**, **Watts**, **Cell volts**, **Voltage estimate**, **RPM + Watts**, **RPM + W + cell** eller **Hidden**. En valgt Custom-kilde legger til en rad i visningen. |
| Meter style | **Numeric** gir tall; **Retro LCD** gir tall med segmentert måler. Inaktivt med **Hidden**. |
| Custom source | En egnet tallkilde, tilgjengelig når Show ikke er **Hidden**. Enheten kommer fra kilden. Velg **---** for å fjerne den ekstra raden. |
| Custom position | Plass **1**, **2** eller **3**, regnet ovenfra. Aktivt når en Custom-kilde vises sammen med andre verdier. Med færre rader blir en plass etter siste rad satt sist. |
| Custom label | Aktivt når Custom er med i visningen. Tomt felt bruker kildenavnet. |
| Custom min | Målerens nedre grense; aktivt når Custom er med i **Retro LCD**. |
| Custom max | Målerens øvre grense; aktivt når Custom er med i **Retro LCD**. Må overstige minimum. |
| Decimals (-1 auto) | Aktivt når Custom er med. **-1** følger kildens desimaler; 0–3 velger fast antall. |
| Red zone | Starten på rødt område, som prosent av målerens skala, for **RPM**, **Watts** og **Custom** med **Retro LCD**. Cell volts og Voltage estimate bruker batterigrenser i stedet. |
| Watt max | Øvre grense i W, aktivt når **Watts** inngår i en **Retro LCD**-visning. |

Watt beregnes fra **Pack voltage × Current**, uten behov for en egen effektsensor.
Det er elektrisk tilført effekt. Cellevolt er **Pack voltage ÷ Cells**;
gjennomsnittet kan ikke avsløre en svak enkeltcelle. Spenningsestimatet nederst
kan vises samtidig som hovedbatteriets prosent beregnes fra forbruk.

### Eksempel: turtall, effekt og ESC-temperatur

Sett **Show = RPM + Watts**, velg ESC-ens temperatursensor som **Custom source**,
og sett **Custom position = 3**. Da vises RPM, Watts og ESC-temperatur.
Temperaturkilden bør ha °C som enhet; målergrensene kan for eksempel være
0–100 °C. Grensene setter bare skalaen, ikke en temperaturalarm.
**Only Custom** viser bare denne kilden.

| Custom position | Rad 1 | Rad 2 | Rad 3 |
|---|---|---|---|
| 1 | Custom | RPM | Watts |
| 2 | RPM | Custom | Watts |
| 3 | RPM | Watts | Custom |

Med **Deck + Image source = Hidden** fordeles de valgte verdiene over den nedre instrumentstripen. **RPM + W + cell** sammen med Custom viser alle fire verdier. **Custom position** 1–3 beholdes som plassering, og Custom får ikke en ny MAX-verdi.

Deck med bilde og Digital beholder maksimalt tre rader: med **RPM + W + cell** erstatter Custom celleraden. Fjernes Custom, kommer celleraden tilbake. **Lower deck > Show = Hidden** skjuler hele nedre instrumentstripe og gir hovedmålingene mer plass.
En valgt kilde beholder raden ved telemetribortfall og viser ukjent verdi til
målingene kommer tilbake.

![RPM, Watts og Custom-temperatur](images/native-voltdeck-custom-position-3.png)

### Cellevolt: skala og farger

**Cell volts** har en fast skala for valgt batteritype, i stedet for å starte på
null. Både tallet og de fylte målersegmentene følger cellespenningen. Verdier
på eller under nedre grense, og over øvre grense, er røde.

| Battery type | Målerskala, V/celle | Nedre rødgrense, V/celle | Øvre grense, V/celle |
|---|---|---|---|
| Lipo | 3,27–4,20 | 3,57 | 4,20 |
| LiHV | 3,37–4,35 | 3,685 | 4,35 |
| Li-ion | 2,97–4,20 | 3,36 | 4,20 |
| LiFe | 2,77–3,65 | 3,055 | 3,65 |

For Lipo er celleverdien oransje over 3,57 til og med 3,615 V, gul over 3,615
til og med 3,66 V, og grønn over 3,66 til og med 4,20 V. Andre typer bruker de
samme 30/35/40%-grensene i sitt eksisterende lineære spenningsestimat.
Hovedbatteriets prosent følger valgt beregningsmetode og avrundes til heltall;
fargen kan derfor avvike fra celleverdien nær en grense.
Cellefargen følger uavrundet spenning: en vist verdi på 4,20 V kan ligge litt
over 4,20 V og derfor være rød.

Dette er omtrentlige visningsgrenser, ikke en måling av faktisk lading.
Lipo-estimatet beholder **3,57 V = 30%**; belastning og spenningsrestitusjon
påvirker målingen. LiHV har **4,35 V** som øvre grense, i samsvar med
[Tattus LiHV-veiledning](https://www.genstattu.com/content/instock/LiHv-Manual.pdf).
Følg alltid batteriprodusentens merkede grenser, også for LiFe.
Gjennomsnittet som vises kan ikke fastslå om hver enkeltcelle er innenfor
sine grenser.

![Lipo-cellevolt ved nedre rødgrense](images/cell-voltage-lipo-low.png)

![LiHV-cellevolt ved fulladet grense](images/cell-voltage-lihv-full.png)

## 6. Motor / RPM

![Motor- og RPM-innstillinger](images/voltdeck-setup-rpm.png)

| Felt | Funksjon |
|---|---|
| RPM source | Faktisk mekanisk turtall i **rpm** (ETHOS kan vise **r/m**). Aktivt for målt RPM nederst eller når logging er på. Flyloggen beholder målt RPM også når hovedskjermen viser et estimat. |
| RPM value | **Measured RPM** eller **KV x volts (est.)**. Aktivt når nedre visning inkluderer RPM. |
| Motor KV | Motorens KV i rpm/V. Brukes av KV-estimat, **Full-pack KV**-skala og flyloggens KV-potensial. Logging holder feltet aktivt også uten RPM nederst. |
| Estimate factor | 10–100%, aktivt ved KV-estimert RPM-visning. Standard 100% viser friløpspotensial; velg en lavere faktor bare ut fra målinger av eget motor-/propelloppsett. |
| RPM scale | **Manual** eller **Full-pack KV**, aktivt for en RPM-måler med **Retro LCD**. Sistnevnte gir fast fulladet skala ut fra batteritype, celletall og KV. |
| RPM max | Manuell skalagrense i rpm. Tilgjengelig som reservegrense dersom **Full-pack KV** mangler gyldig KV-verdi. Aktivt bare for den aktuelle RPM-skalaen i **Retro LCD**. |

KV × aktuell pakkespenning beregner et elektrisk turtallspotensial.
Det måler ikke akselturtallet. Visningen er merket **RPM ESTIMATE**.
Faktoren gjelder estimert visning; flyloggens **KV potential** er uten denne
korreksjonen.

## 7. Flight log

![Flylogginnstillinger](images/voltdeck-setup-flight.png)

![Flytelling og tidsgrenser for økten](images/voltdeck-setup-flight-more.png)

![RF-grafer, tellernullstilling og Preview](images/voltdeck-setup-flight-end.png)

| Felt, i menyrekkefølge | Funksjon |
|---|---|
| Enable log | Slår på kvalifisering og modellspesifikk flytelling. |
| Arm switch | Motorens faktiske arm-bryter eller logiske betingelse. Kreves for logging. Sperrer ikke batterikontrollen ved **Consumed mAh**. Med **% sensor** eller **Voltage estimate** krever resetsperren for valgfri gjenværende mAh fortsatt en gyldig faktisk ARM AV-indikasjon ved godkjenning, også når logging er av. |
| Throttle source | Faktisk gasskontroll/-kanal. Aktivt for diagnostikk også med logging av. |
| Airborne gate | Valgfri bryter/logisk betingelse som må være PÅ for opptjening av kvalifiseringstid. **---** og **Always on** passerer. Aktivt for diagnostikk. |
| Throttle low (raw) | Råverdi ved null gass, vist i **Flight diagnostics**. Standard -1024. |
| Throttle high (raw) | Råverdi ved full gass. Standard 1024; må overstige nedre endepunkt. Begge endepunktene er aktive for diagnostikk. |
| Flight minimum | Minst opptjent kvalifiseringstid; standard 60 s. Aktivt med logging på. |
| Throttle gate | Normalisert gassgrense; standard 50%. Aktivt med logging på. |
| High throttle | Opptjent tid ved/over gassgrensen; standard 5 s. Aktivt med logging på. |
| Pack loss delay | Sammenhengende bortfall av gyldig, positiv **Pack voltage** før økten avsluttes; standard 10 s, område 3–120 s. Alltid aktivt fordi det også krever ny batterikontroll og tillater ny forbruksavlesning etter batteribortfall. |
| Auto-open log | Åpner loggen etter en kvalifisert økt. Aktivt med logging på; standard Av. |
| Extra log delay | Ekstra ventetid etter **Pack loss delay**; standard 5 s, område 0–120 s. Aktivt når logging og automatisk åpning er på. |
| RF graph 1 | Valgfri RSSI-kilde i **dB** eller VFR-kilde i **%** for graf 1; tomt felt bruker **RF1 source**. Aktivt med logging på. |
| RF graph 2 | Samme for graf 2; tomt felt bruker **RF2 source**. Aktivt med logging på. |
| Reset counter | Aktivt med logging på. **Reset...** åpner bekreftelse. Dearm og koble fra batteriet lenge nok til at økten avsluttes først. Bekreftelse nullstiller modellens teller og fjerner beholdt logg. |

Les gassendepunktene i **Flight diagnostics**, ikke bare prosentene i
kanalmonitoren. Kilder kan bruke -1024/+1024, -100/+100 eller 0/100.
VoltDeck omregner valgt område til 0–100%; midtstilling kan derfor være 50%
selv om kanalmonitoren viser 0%.

Kvalifisering krever ARM PÅ, gyldig gass og pakkespenning, godkjent airborne gate
og begge tidskravene. Sekundene over gassgrensen summeres.
En armert benktest kan kvalifisere; en airborne-betingelse kan filtrere bedre,
men beviser ikke at modellen flyr. Slå av logging ved benkarbeid som ikke skal
telles.

### En økt per batteritilkobling

Dearming eller airborne gate AV pauser opptjent tid. Rearming med samme
tilkoblede batteri fortsetter samme logg; økten kan telles bare én gang.
RF-historikken fortsetter gjennom pausene, mens opptjent flytid stopper.

Bare sammenhengende pakkebortfall i **Pack loss delay** avslutter økten.
Spenning tilbake før fristen lar økten fortsette. Positivt spenningsfall avslutter
ikke økten. Langt telemetribortfall kan ligne frakobling, mens et batteribytte
raskere enn forsinkelsen kan bli oversett.

Siste kvalifiserte logg beholdes etter at modellen slås av og mens neste flyging
kvalifiseres. En avvist kandidat erstatter den ikke. Flytelleren lagres per modell;
siste statistikk og grafer forsvinner ved omstart av radioen.

### Automatisk åpning av flylogg

Med **Pack loss delay = 10 s** og **Extra log delay = 5 s** åpnes loggen omtrent
15 s etter sammenhengende pakkebortfall. Bare en ny, avsluttet og kvalifisert økt
utløser byttet. Spenning tilbake, modellbytte, logging/auto-open av, preview,
konfigurasjon eller manuelt visningsbytte avbryter ventende åpning.
Den skjer én gang for flygingen, inne i VoltDecks gjeldende widgetfelt.

### Flight diagnostics

Åpne **Flight log** fra Home, og velg **Diagnostics** nederst til høyre.
Knappen er tilgjengelig også før en flyging er registrert. Med scrollehjulet
ruller du til høyre for å velge knappen og korttrykker for å åpne; rull til venstre
for å fjerne markeringen. Berøring åpner knappen direkte. **RTN** går til Dashboard.

Diagnostikken viser rå/beregnet gass, endepunkter, ARM, airborne gate,
pakkespenning og fremdrift mot begge tidskravene. Les statuslinjen sammen med
de enkelte vilkårene. **LOG DISABLED** betyr at logging er av selv om øvrige
vilkår passerer. Diagnostikken endrer ikke radioens sikkerhetsfunksjoner.
Hold motoren sikkert deaktivert mens du kontrollerer gassendepunkter.

![Diagnostics-knapp i en tom flylogg](images/flight-log-empty.png)

![Flydiagnostikk uten valgt airborne-kilde](images/flight-diagnostics.png)

![Flydiagnostikk med Always on som ARM-kilde og null gass](images/flight-diagnostics-always-on.png)

## 8. Preview

**Preview** gir eksempelverdier for å se på utformingen. Det teller ikke flyginger,
spiller ikke varsler og endrer ikke reelle forbrukssperrer eller maksimumsverdier.
Slå det av før kontroll av modelltelemetri eller godkjenning av forbruksteller.

Preview beholder et godkjent batteri når reell telemetri fortsetter. Et faktisk
bortfall av batterispenning i **Pack loss delay** under Preview krever ny kontroll
når du går tilbake til aktuelle avlesninger.

## Widgetmenyen

Home-menyen ved korttrykk har fem valg som vises uten scrolling.
Når en av Home-menyene er åpen, står bakgrunnen stille i opptil **30 sekunder**.
Den oppdateres igjen når menyen lukkes eller tiden er ute. Telemetri, varsler og
flylogging fortsetter hele tiden.

| Menyvalg | Resultat |
|---|---|
| Flight log / Dashboard | Bytter mellom hovedvisning og flylogg. |
| Reset live peaks | Nullstiller hovedskjermens RPM- og Watt-maksimum. Endrer ikke flyteller eller maksimum i registrert flylogg. |
| Accept battery counter... | Viser status og eventuelle gjenværende sperrer for [batterikontrollen](#kontroll-før-gjenværende-lading-vises) ved **Consumed mAh**, eller et reset av den valgfrie telleren for gjenværende mAh med en annen metode. Kontroller faktisk lading og sensor før bekreftelse. Den kan ikke omgå avvik over 20 prosentpoeng eller **CHECK CELLS/TYPE** i batterikontrollen. Godkjenning gjenoppretter ikke manglende forbruk, nullstiller ikke sensoren, fyller ikke batteriet og endrer ikke flytellingen. |
| Configure widget | Åpner gruppene ovenfor. |
| Configure screens | Åpner ETHOS' skjermkonfigurasjon. |

**Diagnostics** ligger inne i Flight log. Når Flight log eller Diagnostics er valgt,
går **RTN** til Dashboard. Er en meny eller dialog åpen, lukker første RTN den.
Et ekstra RTN på Dashboard følger ETHOS' vanlige navigasjon og kan fjerne widgetens
fokus. Langt trykk åpner fortsatt ETHOS-menyen Reset flight / Reset telemetry / Reset timers.

## Visningseksempler

### RPM, Watt og gjennomsnittlig cellevolt

<table>
<tr>
<td><img src="images/native-voltdeck-lower-2-retro.png" alt="LCD målt RPM"><br><b>RPM / Retro LCD</b><br>Measured RPM, Manual, RPM max 12000.</td>
<td><img src="images/native-voltdeck-lower-6-retro.png" alt="RPM og elektrisk effekt"><br><b>RPM + Watts / Retro LCD</b><br>Watt max 1500 W.</td>
</tr>
<tr>
<td><img src="images/native-voltdeck-lower-7-retro.png" alt="RPM Watt og gjennomsnittlig cellevolt"><br><b>RPM + W + cell / Retro LCD</b></td>
<td><img src="images/native-voltdeck-lower-2-numeric.png" alt="RPM som tall"><br><b>RPM / Numeric</b></td>
</tr>
<tr>
<td><img src="images/native-voltdeck-lower-3-retro.png" alt="Watt som LCD"><br><b>Watts / Retro LCD</b></td>
<td><img src="images/native-voltdeck-lower-4-numeric.png" alt="Gjennomsnittlig cellevolt på svart bakgrunn"><br><b>Cell volts / Numeric</b><br>Svart bakgrunn; mAh display Remaining.</td>
</tr>
</table>

Bildene viser 22,8 V × 24,5 A, omtrent **559 W** elektrisk tilført effekt.
22,8 V ÷ 6 celler gir **3,80 V** gjennomsnittlig cellevolt.
Manglende spenning/strøm vises med streker fremfor oppdiktet effekt.

### Valgfri telemetri og KV-estimat

![Valgfri temperaturmåler](images/native-voltdeck-lower-1-retro.png)

Velg **Only Custom**, en temperaturkilde, etiketten **ESC TEMP**, område
0–150 °C og 0 desimaler. Den faktiske temperaturenheten kommer fra kilden.

![KV-basert RPM-estimat](images/native-voltdeck-kv-estimate.png)

Eksemplet bruker **RPM / Retro LCD**, **RPM value = KV x volts (est.)**, **Motor KV = 500**, **Estimate factor = 90%**, **RPM scale = Manual** og **RPM max = 12000**. Ved 22,8 V blir det 500 × 22,8 × 0,90 = **10260 rpm**. Faktoren er et illustrasjonsvalg, ikke en generell korreksjon for propellbelastning. Dette er estimert turtall, ikke en måling.

### Batterifarger

| Gjenværende lading | Farge |
|---|---|
| Over 40% | Grønn |
| Over 35%, til og med 40% | Gul |
| Over 30%, til og med 35% | Oransje |
| 30% eller lavere | Rød |

<table>
<tr>
<td><img src="images/battery-yellow-40.png" alt="Batteri 40 prosent"><br><b>40%: gul</b></td>
<td><img src="images/battery-orange-35.png" alt="Batteri 35 prosent"><br><b>35%: oransje</b></td>
</tr>
</table>

![Batteri 30 prosent med lavbatterimarkering](images/battery-red-30.png)

### VFR-grafer i stedet for RSSI

![Flylogg med VFR-grafer](images/flight-log-vfr.png)

Hovedskjermens **RF1/RF2 source** kan vise RSSI i dB, mens **RF graph 1/2**
viser VFR i %. Dette er ulike målinger. Velg grafkilder før flyging;
hver økt beholder kildene, navnene og enhetene fra starten.
Visuelle profiler kan fortsatt justeres. Manglende data gir brudd i kurven;
korte fall beholdes. Sanntidsgrafen kan ligge noen sekunder etter.

![Inaktive RF-kilder beholder navn og enhet](images/rf-inactive-units.png)

![Flylogg med RSSI-grafer](images/flight-log-rssi.png)

RSSI-eksemplet bruker **ACCST** med 45/42 dB som visuelle grenser.
Oppsummeringen skiller målt RPM fra KV-potensial og viser flytid,
maksimal strøm/Watt, pakkespenning lav/høy og modellens flyteller.

### Bilder av batteriøktene

| Motor dearmert, samme batteri | Batteriet frakoblet lenge nok |
|---|---|
| ![Kvalifisert økt pauset](images/flight-paused.png) | ![Siste kvalifiserte logg beholdes](images/flight-last-retained.png) |
| Teller 3 og samme logg beholdes. | LAST FLIGHT LOG beholdes med teller 3. |

| Neste flyging kvalifiseres | Neste flyging har kvalifisert |
|---|---|
| ![Forrige logg mens neste kvalifiseres](images/flight-next-qualifying.png) | ![Ny kvalifisert flyging](images/flight-next-qualified.png) |
| Forrige logg beholdes; telleren er fortsatt 3. | Telleren blir 4; ny logg erstatter den gamle. |

Kontroller kilder, kapasitet, celletall, forbruksreset, lyd og kontrollvilkår
for modellen før flyging. Ta sikkerhetskopi av modell og SD-kortinnstillinger,
og behold radioens egne alarmer og failsafe.
