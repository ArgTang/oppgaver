---
title: Hva er det?
level: 1.7
language: nb-NO
stylesheet: scratch
embeds: ["*.png", "../../bilder/*.png"]
...

# Introduksjon { .intro}

Et bilde av en tilfeldig ting vises p� tavlen. Men bildet er forvrengt, slik at du m� gjette hva det er ved � klikke p� et av alternativene som vises under. Desto raskere du gjetter riktig, desto flere poeng f�r du.


![skjermbilde](hvaerdet.png)

#Steg 1: F� flere ting til � vise seg p� tavlen { .activity}
__Vi vil at noen forskjellige bilder skal komme opp p� tavlen.__

## Sjekkliste { .check}

+ Start et nytt Scratch-prosjekt og slett kattefiguren.
+ Klikk p� Scene og deretter Bakgrunner-fanen. �pne biblioteket med bakgrunner ved � trykke p� ![Velg en ferdig bakgrunn](velg-bakgrunn.png) og velg s� __Innend�rs/chalkboard__.
+ Importer en valgfri figur. Velg gjerne en fra Ting-mappen.
+ Plasser figuren p� midten av tavlen, og endre st�rrelsen hvis den ikke passer.
+ Legg til fire nye drakter fra Ting-mappen. Du kan velge hva du vil!
+ La oss n� f� en tilfeldig ting til � dukke opp. Bruk dette skriptet. 

    ```blocks
        n�r gr�nt flagg klikkes
        gjenta <tilfeldig tall fra(1) til (5)> ganger
            neste drakt
		slutt
    ```

##Test prosjektet { .flag}
__Trykk p� det gr�nne flagget.__
Endrer figuren seg? Klikk flere ganger. F�r figuren stadig nye drakter? Flott. 

Det gj�r ingenting om samme drakt kommer opp flere ganger p� rad. Det er helt normalt n�r det trekkes en tilfeldig drakt hver gang. 
Du legger kanskje merke til at det flimrer litt n�r drakten skiftes? Det skal vi fikse i neste steg.


##Lagre prosjektet {.save}

#Steg 2: Forvreng bildet {.activity}

__La oss n� forvrenge figuren n�r den dukker opp p� tavlen, s� det blir vanskeligere � gjette hva det er. Deretter skal vi gradvis gj�re vi den tydeligere igjen.__

Vi skal bruke en poeng-variabel til � kontrollere graden av forvrenging. Dersom poengscoren er h�y vil bildet bli veldig forvrengt. N�r antallet poeng synker, vil ogs� graden av forvrenging synke. Poengvariabelen fungerer dermed som en tidteller.

## Sjekkliste { .check}

+ Velg Data-paletten og opprett en variabel kalt __poeng__. 

+ Endre skriptet slik:

    ```blocks	
		n�r gr�nt flagg klikkes
		skjul
		gjenta <tilfeldig tall fra(1) til (5)> ganger
            neste drakt
        slutt
        sett [poeng v] til (110)
        gjenta til ((poeng) = (0)
            endre [poeng v] med [-10]
            sett [piksel v] effekt til (poeng)
            sett [farge v] effekt til (poeng)
            vis
            vent (1) sekunder
        slutt
    ```

##Test prosjektet { .flag}
__Trykk p� det gr�nne flagget.__

Kommer det opp et tilfeldig og forvrengt bilde?

Blir bildet gradvis tydeligere?

G�r poengsummen ned i takt med at bildet blir tydeligere?

Blir bildet fullstendig tydelig n�r poengsummen er 0?

F�r du fremdeles nye ting p� tavlen n�r du klikker p� det gr�nne flagget?


##Lagre prosjektet{ .save}

##Ting � pr�ve { .try .activity}

+ __Pr�v � endre poengsummen fra start, samt hvor mye den skal forandre seg for hver gang den g�r gjennom l�kka.__ Hvordan endrer deg utseendet til bildet? Blir det vanskeligere eller enklere � se hva bildet forestiller?

+ __Fors�k noen ulike grafiske effekter fra nedtrekkslisten.__ Hvordan p�virker dette vanskelighetgsraden?

#Steg 3: La spilleren pr�ve � gjette bildet {.activity}

S� langt har vi f�tt v�rt tilfeldige bilde til gradvis � bli tydeligere, samtidig som poengsummen synker. Men hvordan skal man vinne spillet? Vi vil legge til noen figurer nederst p� skjermen som spilleren kan klikke p�. Klikker man p� den rette, vinner man spillet. Klikker man p� feil, forsvinner figuren og spillet fortsetter med en ny figur.

F�rst m� vi � vite hva det rette svaret er.

## Sjekkliste { .check} 

+ __Opprett en ny variabel__ og kall den __svar__. Pass p� at den er tilgjengelig for alle figurer.
+ Endre skriptet slik at det klarer � holde styr p� hva som er rett svar.  Etter den f�rste `gjenta`{.blockorange}-l�kken legger du derfor til blokken `sett [svar] til`{.blockorange} `drakt #`{.blockpurple}:

    ```blocks
		n�r gr�nt flagg klikkes
		skjul
		gjenta <tilfeldig tall fra(1) til (5)> ganger
            neste drakt
        slutt
		sett [svar v] til (drakt #)
        sett [poeng v] til (110)
        gjenta til ((poeng) = (0)
            endre [poeng v] med [-10]
            sett [piksel v] effekt til (poeng)
            sett [farge v] effekt til (poeng)
            vis
            vent (1) sekunder
        slutt
    ```
__N� m� vi legge til flere figurer som spilleren kan klikke p�.__

+ Gi f�rst figuren din navnet __sp�rsm�l__.
+ Lag s� en kopi av figuren ved � h�yreklikke p� den. P� scenen drar du deretter figuren ned til det venstre hj�rnet.
+ Endre figurens navn til __svar1__.
+ Slett skriptet til __svar1__ og alle kostymer bortsett fra det f�rste.
+ Gjenta de tre siste stegene igjen (kall neste kopi __svar2__), men plasser __svar2__ ved siden av __svar1__ og slett alle bortsett fra den andre drakten.
+ Gjenta disse punktene tre ganger til, slik at du har f�tt laget __svar3__, __svar4__ og __svar5__.
Du skal n� ha en rad med fem svar-figurer nederst p� scenen, hver viser en drakt som hovedfiguren kan ha. __Ingen av svar-figurene skal ha skript knyttet til seg.__

+ N� m� vi f� alle figurene til � reagere n�r de blir klikket p�. Hva som skal skje avhenger av om spilleren har klikket riktig eller galt. Legg til dette skriptet til __svar1__:

    ```blocks
        n�r denne figuren klikkes
        hvis <(svar) = (1)>
            send melding [vant v]
        ellers
            skjul
        
    ```

+ Dra skriptet over til de andre figurene, slik at alle f�r hver sin kopi. __For hver figur, bytt 1 til 2, 3, osv.__
+ N� skal vi lage skriptet som gir melding til spilleren n�r han har vunnet. Klikk p� __sp�rsm�l__ igjen og legg til dette skriptet:

    ```blocks
        n�r jeg mottar [vant v]
        si (sett sammen [Gratulerer! Din poengsum ble] (poeng))
    ```

##Test prosjektet {.flag}
__Trykk p� det gr�nne flagget.__

N�r du tester spillet kan du bruke svarskjermen p� scenen for � si hva rett svar er. Det
fungerer bra for testing.

Hva skjer n�r du klikker p� __riktig svar__?

Hva skjer n�r du klikker p� __galt svar__?

Hva skjer med det gale svaret n�r du __starter p� et nytt spill__?

__Testen viser oss to problemer:__
F�rst og fremst, ting som ble klikket p� ved galt svar kommer ikke tilbake n�r et nytt spill starter. 
For det andre, poengsummen fortsetter � g� ned, selv n�r man har klikket p� riktig svar.

+ For � fikse det f�rste problemet m� vi legge til f�lgende skript for hver av de fem svarfigurene:

    ```blocks
        n�r gr�nt flagg klikkes
        vis
    ```

For � fikse det andre problemet m� vi f� stoppet __sp�rsm�lfigurens__�s `gjenta til`{.blockyellow}-l�kke, n�r spilleren klikker p� riktig svar. Vi kan bruke en ny variabel for � gj�re det. 
Vi kaller denne __vant__ og legger inn en `sett`{.blockorange}-blokk som gir den verdien 0 n�r spillet starter, og en annen som setter verdien til 1 n�r spillet vinnes. Se skript under.
+ I tillegg m� vi stoppe `gjenta til`{.blockyellow}-l�kken n�r poengsummen har blitt 0 eller vant er 1. 
+ Til slutt legger vi ogs� inn en `ta bort grafiske effekter`{.blockpurple}-blokk som avsl�rer sp�rsm�lsfiguren, n�r spilleren har gjettet riktig. Skriptet skal n� se slik ut:

    ```blocks
		n�r gr�nt flagg klikkes
		skjul
		gjenta <tilfeldig tall fra(1) til (5)> ganger
            neste drakt
        slutt
		sett [svar v] til (drakt #)
        sett [poeng v] til (110)
		sett [vant v] tuk (0)
        gjenta til <<((poeng) = (0)> eller <(vant) = (1)>>
            endre [poeng v] med [-10]
            sett [piksel v] effekt til (poeng)
            sett [farge v] effekt til (poeng)
            vis
            vent (1) sekunder
        slutt
	
	    
		n�r jeg mottar [vant v]
		sett [vant v] til (1)
		ta bort grafiske effekter
        si (sett sammen [Gratulerer! Din poengsum ble] (poeng))
        
    ```

##Lagre prosjektet{.save}

__Gratulerer! Du er n� ferdig med spillet. Men det fins mange flere ting du kan gj�re med det. Pr�v deg gjerne p� utfordringene vi har laget!__


##Utfordring 1:Gj�r spillet enklere eller vanskeligere {.challenge}

Endre vanskelighetsgrad for spillet.

* Fors�k � endre hvor lenge bildet vises frem og hvor raskt poengsummen minker.
* Fors�k � endre forvrengingen av bildet.
* Fors�k � gj�re tingene likere hverandre eller mer forskjellig. Husk ogs� � forandre svarfigurenes drakter.

##Lagre prosjektet{.save}

##Utfordring 2: Forvreng bildet ulikt fra gang til gang {.challenge}

For �yeblikket bruker spillet samme forvrengingsalgoritme hele tiden. Men i steg 2 pr�vde du kanskje ut noen forskjellige alternativer. Pr�v n� om du kan finne noen flere forvrenginger som du synes virker like bra som farge og piksler.
 
Endre spillet slik at hvert spill bruker forskjellige forvrengninger i gjenta til-l�kken.

__Hint:__ 
Fors�k � opprette en ny variabel som du kaller forvrenging. Sett denne til en tilfeldig verdi i starten av spillet. Bruk s� hvis-blokker i gjenta til-l�kken for � velge ut en forvrenging til det hvert spill.


##Lagre prosjektet{.save}

##Utfordring 3: La hvert spill ha flere runder {.challenge}

For �yeblikket er hvert spill uavhengig av andre. Pr�v om du kan legge til flere
runder slik at man f�r gjette p� tre ting og kan vinne inntil 300 poeng.

__Hint:__ Du vil trenge en ekstra variabel for � lagre den totale poengsummen. Du m� ogs� ha en l�kke som g�r rundt for hver runde.

__Hint:__ Du vil trenge en ekstra variabel for � lagre den totale poengsummen. Du m� ogs� ha en l�kke som g�r rundt for hver runde.


##Lagre prosjektet{.save}

##Utfordring 4: �k vanskelighetsgraden gradvis {.challenge}

Gj�r n� spillet vanskeligere og vanskeligere for hver runde.

Kanskje hver runde
ogs� skal gi ulikt antall poeng? B�r spilleren ogs� f� ekstra mange poeng for � gjette kjapt i de vanskeligste rundene? 


__Hint:__ : Hvordan kan du vite hvilken runde du er i? Hvordan kan du bruke det til � endre vanskelighetsgraden og poengsummen?


##Lagre prosjektet{.save}

##Utfordring 5: Fortsett til spilleren gj�r feil {.challenge}

steden for et bestemt antall runder, kan du la spillet g� til det blir klikket p� feil svar. Dette funker nok best dersom man ogs� �ker vanskelighetsgraden utover i spillet.

##Lagre prosjektet{.save}

##Utfordring 6: Gj�r spillet enklere eller vanskeligere basert p� hvor flink spilleren er {.challenge}

Istedenfor � gj�re det stadig vanskeligere kan vi tilpasse vanskelighetsgraden til spillernes dyktighet. Hvis de raskt gjetter riktig ting, kan den neste runden gj�res vanskeligere. Hvis de klikker feil eller gjetter sakte, kan neste runde gj�res enklere.

Dette fungerer bare hvis du ikke samler opp poengsummen fra runde til runde.

##Lagre prosjektet{.save}

##Utfordring 7: Hold styr p� rekorden {.challenge}

Finn en m�te � lagre den h�yeste poengsummen p�. Klarer du ogs� � lagre navnet til spilleren, og f� spillet til � si hvem som har rekorden?


##Lagre prosjektet{.save}

##Utfordring 8: Gi en straff for galt svar {.challenge}

Slik spillet er n� kan man bare klikke som en gal p� alle svarene, s� vil man raskt finne riktig svar. Det kan derfor v�re en god id� � trekke fra poeng hver gang spilleren klikker galt.

Gj�r dette spillet bedre?

##Lagre prosjektet{.save}

__Veldig bra! N� er du ferdig og kan nye spillet du har laget!__
Ikke glem � del spillet ditt med venner og familie ved � trykke p� __Legg ut__ i menyen!
