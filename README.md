![Statens Kartverk](https://github.com/kartverket/etinglysing-systembeskrivelse/blob/master/doc/kartverket.png)


# Veileder for elektronisk innsending av vedlegg


## Innledning

Fra versjon 3.16 av elektronisk tinglysing vil det være mulig å sende med vedlegg sammen med elektronisk innsendte dokumenter. 

Dette har frem til nå vært en klar begrensning ved elektronisk innsending, og å åpne for dette vil potensielt kunne øke andelen elektronisk innsendte dokumenter betydelig. 

## Dokumenter som kan ha vedlegg

Det vil i første omgang kun være mulig å sende inn vedlegg sammen med 
* Overdragelse (Overdragelse av eiendomsrett i fast eiendom, Overdragelse av festerett med bygning, og Overdragelse av borettslagsandel) 
* Vanlig pantedokument 
* Pantedokument med urådighetserklæring (sikringspant) 

Spesielt for overdragelser er andelen elektronisk innsending relativt lav, og det antas at mye av grunnen til dette er manglende muligheter til å sende med vedlegg. 

Det vil foreløpig ikke være mulig å sende inn vedlegg sammen med en sletting, men her antas det at fullmaktsmodulen fortsatt skal være tilstrekkelig.

## Kategorier av vedlegg

Det vil i tillegg være begrensninger på hvilke kategorier av vedlegg som kan sendes inn. Disse kategoriene vil til versjon 3.16 være 
* Skifteattest/Uskifteattest
* Skiftefullmakt
* Testament
* Gjensidig testament
* Salgsfullmakt
* Kjøpsfullmakt
* Begrunnelse for dokumentavgift
* Annet 

Dette gjør at det nå vil være mulig å elektronisk sende inn for eksempel de fleste skifteoppgjør, og skjøtepakker der det signeres iht fullmakt. 

Vi regner med at kategoriene det åpnes for vil være dekkende for de fleste elektroniske innsendinger av overdragelser og pantedokumenter, men listen av kategorier vil også kunne utvides etterhvert.

Innsender må selv angi hvilke kategori (er) et elektronisk vedlegg tilhører. Dersom en kategori antas å kunne påvirke en valideringsregel, vil valideringsregelen sende saken til manuell behandling. 

Et eksempel her kan være at en elektronisk overdragelses som inneholder et vedlegg av kategorien salgsfullmakt, av signaturkontrollen vil sendes til manuell behandling, uavhengig av om 
hjemmelshaver har signert på dokumentet eller ikke. 

Valideringsregler som ikke er berørt av de oppgitte kategoriene av vedlegg vil fortsatt kjøres som vanlig, og disse kan resultere i at saken allikevel blir avvist. 
Dersom de angitte kategoriene av vedlegg i en innsending ikke påvirker noen valideringsregler, og den innsendte saken heller ikke blir avvist som følge av andre valideringsregler, vil saken allikevel sendes til manuell behandling. Det er derfor ingen elektroniske innsendinger med vedlegg som vil kunne bli automatisk tinglyst. 

Det er i tillegg lagt inn en del faglige/logiske regler for de forskjellige vedleggskategoriene. Et par eksempler på dette er at det ikke er mulig å legge ved skiftefullmakt eller testament uten at det også ligger ved en skifteattest, og at det ikke er mulig å legge ved en begrunnelse for dokumentavgift på et pantedokument. 

Et vedlegg kan angis med flere forskjellige kategorier, og det er mulig å legge ved flere vedlegg til et dokument.
 
## Litt om regler ved bruk av de forskjellige vedleggskategoriene

### Skifteattest/Uskifteattest

Skifteattest/Uskifteattest kan legges ved overdragelser, pantedokument og sikringspant. 

Skifteattest/Uskifteattest må alltid legges ved en overdragelse dersom denne gjelder et uskifte-/skifteoppgjør, [GBOK-13648](https://jira.statkart.no/browse/GBOK-13648). 

Ved overdragelser gjør dette vedlegget at signaturkontrollen for selger/hjemmelshaver settes til side, og saken går til manuell behandling, [GBOK-13624](https://jira.statkart.no/browse/GBOK-13624). 
Tilsvarende gjelder ved innsending av pantedokument og sikringspant, [GBOK-13627](https://jira.statkart.no/browse/GBOK-13627) og [GBOK-13734](https://jira.statkart.no/browse/GBOK-13734).

Skifteattest/Uskifteattest gjør også at erklæring om sivilstand fra hjemmelshaver ikke er påkrevd, så lenge hjemmelshaver ikke har signert elektronisk på dokumentet. 
Dette gjelder både for overdragelser og pantedokumenter, [GBOK-13673](https://jira.statkart.no/browse/GBOK-13673) og [GBOK-13674](https://jira.statkart.no/browse/GBOK-13674).

Ved skifteoppgjør vil det ikke alltid være krav om signatur fra en rettighetshaver til en eventuell råderettsbegrensende heftelse. 
På grunn av dette vil denne signaturkontrollen overstyres både for overdragelser og pant, og saken sendes til manuell behandling, [GBOK-13716](https://jira.statkart.no/browse/GBOK-13716).

Skifteattest/Uskifteattest vil også gjøre at signaturkontrollen for kjøper ved overdragelse av boligseksjon settes til side, 
og saken sendes til manuell behandling, [GBOK-13625](https://jira.statkart.no/browse/GBOK-13625).

#### Spesialtilfeller
I visse tilfeller skal rettigheter fra skifteattest og testament tinglyses sammen med overdragelsen til arvingene:
* Fra skifteattest kan det fremgå at ikke alle arvinger er gjeldsovertagende. Dette tinglyses som rettsstiftelsen 
  * AH_GAR - BARE GJELDSOVERTAKENDE ARVINGER KAN RÅDE OVER REGISTERENHETEN
* Fra testament kan det fremgå bestemmelse om privat beslagsforbud. Dette tinglyses som en av rettsstiftelsene
  * AH_PBF - BESTEMMELSE OM PRIVAT BESLAGSFORBUD, JF. DEKNINGSLOVEN § 3-1
  * AH_PBG - BESTEMMELSE OM PRIVAT BESLAGSFORBUD, JF. DEKNINGSLOVEN § 3-2
  * AH_PBH - BESTEMMELSE OM PRIVAT BESLAGSFORBUD, JF. DEKNINGSLOVEN §§ 3-1 OG 3-2
* Fra testament kan det fremgå bestemmelse om særeie. Dette tinglyses som rettsstiftelsen 
  * EN_SAT - SÆREIE IFØLGE TESTAMENT

Ved elektronisk innsending med skifteattest og/eller testament som vedlegg, der disse inneholder bestemmelser som nevnt over, må rettighetene 
være lagt inn som rettsstiftelser i signert elektronisk dokument for at tinglysing skal kunne godkjennes.

Det anvendes ikke egne signaturregler for rettsstiftelsene over ved elektronisk innsending. Da disse alltid må sendes inn i samme dokument som en overdragelse med 
vedlegg, følger de signaturreglene for overdragelsen.

### Skiftefullmakt

Skiftefullmakt kan bare legges ved dokumenter der det også er lagt ved Skifteattest/Uskifteattest, 
og dokumenter med Skiftefullmakt vil derfor følge samme regler som dokumenter med Skifteattest/Uskifteattest

### Testament

Testament kan bare legges ved dokumenter der det også er lagt ved Skifteattest/Uskifteattest, og dokumenter med Testament vil derfor følge samme regler som 
dokumenter med Skifteattest/Uskifteattest.

### Gjensidig testament

Gjensidig testament kan bare legges ved dokumenter der det også er lagt ved Skifteattest/Uskifteattest, og dokumenter med Gjensidig testament vil derfor følge samme regler som 
dokumenter med Skifteattest/Uskifteattest.  I motsetning til ved vanlig testament, vil en overdragelse som inneholder et gjensidig testament være gebyrfri. 

### Salgsfullmakt

Salgsfullmakt kan legges ved overdragelser, pantedokumenter og sikringspant. 

Ved overdragelser gjør dette vedlegget at signaturkontrollen for selger/hjemmelshaver settes til side, og saken går til manuell behandling, [GBOK-13624](https://jira.statkart.no/browse/GBOK-13624). 
Det samme gjelder for pantedokument og sikringspant, [GBOK-13627](https://jira.statkart.no/browse/GBOK-13627) og [GBOK-13734](https://jira.statkart.no/browse/GBOK-13734).

Salgsfullmakt gjør også at elektronisk erklæring om sivilstand fra hjemmelshaver ikke er påkrevd, så lenge hjemmelshaver selv ikke har signert elektronisk på dokumentet. 
Dette gjelder både for overdragelser og pantedokumenter, [GBOK-13673](https://jira.statkart.no/browse/GBOK-13673) og [GBOK-13674](https://jira.statkart.no/browse/GBOK-13674), 
og skyldes at en slik erklæring i stedet kan fremgå av selve salgsfullmakten.

### Kjøpsfullmakt
Kjøpsfullmakt kan legges ved overdragelser, pantedokumenter og sikringspant. 

For pantedokument og sikringspant gjør dette vedlegget at signaturkontrollen for hjemmelshaver settes til side, 
og saken går til manuell behandling,  [GBOK-13627](https://jira.statkart.no/browse/GBOK-13627) og [GBOK-13734](https://jira.statkart.no/browse/GBOK-13734).

Kjøpsfullmakt vil også gjøre at signaturkontrollen for kjøper ved overdragelse av boligseksjon settes til side, 
og saken sendes til manuell behandling, [GBOK-13625](https://jira.statkart.no/browse/GBOK-13625).

### Begrunnelse for dokumentavgift

Begrunnelse for dokumentavgift kan bare legges ved overdragelser. 

Overdragelser som inneholder vedlegg av denne typen vil kjøre gjennom alle valideringsregler som vanlig, og kan avvises som følge av disse. 
Dersom overdragelsen ikke blir avvist som følge av valideringsreglene vil den sendes til manuell behandling, [GBOK-13667](https://jira.statkart.no/browse/GBOK-13667).

### Annet

Vedlegg med kategori Annet kan legges ved overdragelser, pantedokumenter og sikringspant. 

Dokumenter som inneholder vedlegg av denne typen vil kjøre gjennom alle valideringsregler som vanlig, og kan bli avvist som følge av disse. 

Dersom dokumentet ikke blir avvist som følge av valideringsreglene vil det sendes til manuell behandling, [GBOK-13664](https://jira.statkart.no/browse/GBOK-13664).
Vedlegg av type Annet er altså ikke i seg selv nok til at et dokument ikke blir avvist men blir sendt til manuell behandling.

## Påtegning av vedlegg

Det arbeides med å avklare nærmere hvordan, og i hvilke tilfeller, det vil være aktuelt å påtegne vedlegg som legges ved 
elektroniske innsendinger. Inntil en slik avklaring er på plass, vil vi anse alle vedlegg som legges ved elektroniske innsendinger 
som «kopier» av et originaldokument, og vil kreve samme type påtegning på disse som ved papirinnsending i dag. 

Det vil si at alle vedlegg, av en slik type (f.eks. en fullmakt) at det ved papirinnsending ville vært krav om bekreftelse av 
rett kopi, og inneståelse fra advokat, eiendomsmegler el. om at en fullmakt fortsatt gjelder, skal påtegnes på samme måte der 
vedlegget legges ved elektroniske innsendinger.

## Arkivering av vedlegg

Elektroniske vedlegg vil, på samme måte som vedlegg til papirinnsendinger, arkiveres i tinglysingens pantebok. 
Dette gjør at vedleggene er tilgjengelig for ettertiden og Kartverkets arkiveringsplikt blir ivaretatt. 

Vedleggene blir ikke lagt ved ordinære bestillinger fra panteboken, men kan være aktuelle å gi ut ved eventuelle innsynsbegjæringer. 
Dersom et dokument har flere vedlegg ved innsending, vil disse slås sammen til en vedleggsfil i panteboken. 

## Vedlegg vs registrerte fullmakter
Det er mulig å registrere fullmakter hos Kartverket for anvendelse ved elektronisk innsending til tinglysing. Det arbeides med å utvide denne
fullmaktsløsningen, bl.a. slik at den vil gjelde flere disposisjoner som overdragelse og pant.

Som beskrevet i denne veilederen kan fullmakter også sendes inn som vedlegg. Det er imidlertid ønskelig at fullmakter blir registrert
i de tilfeller der en fullmakt skal benyttes flere/mange ganger.

Fordelene med registrerte fullmakter er at man ved validering får et klart resultat hva angår signaturkontroll, man får raskere 
saksgang da saksbehandlingen kan automatiseres, og man trenger ikke legge ved fullmakten som vedlegg ved hver innsending.