---
title: JafseFisk
level: 1.5
language: nb-NO
embeds: ["*.png", "../../bilder/*.png"]
...

#JafseFisk

#Introduksjon { .intro}
Vi skal n� lage et JafseFisk-spill! M�let i spillet er � hjelpe JafseFisk med � spise alle byttedyrene som sv�mmer rundt i havet.

![skjermbilde](jafsefisk.png)

# Steg 1: JafseFisk f�lger musepekeren { .activity}
__F�rst skal vi lage JafseFisk som sv�mmer rundt i havet!__

## Sjekkliste { .check}

+ __Start et nytt Scratch prosjekt__.
+ __Riktig bakgrunn__ f�r du ved � velge Scene og s� Bakgrunn-fanen. Importer bakgrunnen __Natur/underwater3__ ved � velge `Velg en ferdig bakgrunn`{.blocklightgrey}. Slett s� den andre bakgrunnen __backdrop1__.
+ Endre Sprite1's navn til `JafseFisk` ved � trykke p� det bl� '__i__' symbolet.
+ Gi figuren en haidrakt ved � velge `Velg drakt fra biblioteket`. Velg drakt __Dyr/shark-b.png__. Kall drakten `�pen munn`. Slett s� figurens andre drakt (__costume1__ og __costume2__).
+ Klikk p� det bl� '__i__' symbolet igjen, og pass p� at figuren bare kan bevege seg fra side til side ved � velge rotasjonsm�te `<-->`.
+ F� fisken til � f�lge musepekeren rundt i sj�en ved � lage dette skriptet:

```blocks
    n�r gr�nt flagg klikkes
    for alltid    	
        pek mot [musepeker v]
        g� (3) steg
```

## Test Prosjektet { .flag}

__Klikk det gr�nne flagget.__
Flytt musepekeren rundt i sj�en. F�lger fisken med?
Hva skjer hvis du ikke flytter musepekeren, og fisken n�r den igjen?
Hvordan ser den ut? Hvorfor gj�r den dette?

+ Du kan stoppe JafseFisks maniske flipping hvis du s�rger for at den bare flytter seg n�r den ikke er for n�r musepekeren
(`avstand til`{.blocklightblue} blokken ligger under `Sansning`{.blocklightgrey} paletten).

    ```blocks
    n�r gr�nt flagg klikkes
	for alltid
		hvis <(avstand til [musepeker v]) > (10)>
            pek mot [musepeker v]
            g� (3) steg
    ```

## Lagre prosjektet { .save}

## Ting � pr�ve { .try}

Hvis du vil kan du forandre tallene i skriptet, og se hvordan det forandrer bevegelsene:?
Sett avstandensgrensen til et stort tall (f.eks. 100), eller et lite tall (f.eks. 1).
Sett antall steg fisken flytter seg til et stort tall (f.eks. 20) eller et lite tall (f.eks. 1, eller 0).


# Steg 2: Legg til byttedyr { .activity}
__Det er p� tide � gi JafseFisk noe � spise!__

## Sjekkliste { .check}

+ Lag en ny figur fra biblioteket ved � bruke **Dyr/Fish2**. 
+ Gj�r figuren mindre med `krympeknappen`{.blocklightgrey} som ligger over den r�de stopp-knappen.
+ F� byttedyrene til � bevege seg i tilfeldige retninger. F�rst skal vi la dem bevege seg litt framover, og s� snu en tilfeldig valgt vinkel med eller mot klokka, og deretter gjenta. 

    ```blocks
    n�r gr�nt flagg klikkes
    for alltid		
		g� (2) steg
		vend til h�yre (tilfeldig tall fra (-20) to (20)) grader
		sprett tilbake ved kanten  
    ```

## Test prosjektet { .flag}

__Klikk p� det gr�nne flagget__ og se hvordan byttedyret sv�mmer rundt. Sv�mmer det slik du forventet? Ser bevegelsene naturlige ut?

__For �yeblikket samspiller ikke JafseFisk og byttedyret med hverandre. Det skal vi gj�re noe med i neste steg.__

## Lagre prosjektet { .save}

## Ting � pr�ve{ .try}

* Pr�v � forandre tallene for steg og `tilfeldig tall`{.blockgreen}. Hvordan forandrer det byttedyrenes bevegelser?

* Hva gj�r`sprett tilbake ved kanten`{.blockblue} blokken? Fjern blokken og se hva som skjer.

#Steg 3: JafseFisk spiser byttet { .activity}

__N� skal vi la JafseFisk spise byttet!__ N�r den har fanget byttet i munnen skal to ting skje:
* Den m� lukke munnen og lage en gomlelyd.
* Byttet m� forsvinne, og s� komme igjen en liten stund senere.

## Sjekkliste { .check}

+ Vi starter med � la byttet forsvinne hvis den ber�rer JafseFisk, og s� komme tilbake etter 3 sekunder. Bruk `ber�rer`{.blocklightblue}-blokken for � sjekke om byttet kommer borti JafseFisk.

    ```blocks
    n�r gr�nt flagg klikkes
    for alltid		
		g� (2) steg
		vend til h�yre (tilfeldig tall fra (-20) to (20)) grader
		sprett tilbake ved kanten
		hvis <ber�rer [JafseFisk v]?>
			skjul
			vent (3) sekunder
			vis
    ```

## Test prosjektet { .flag}
__Pr�v spillet ditt igjen. Ser du noen problemer?__ ? Legg merke til at byttet forsvinner uansett hvor det ber�rer JafseFisk. Dessuten kan fisken bare vente 3 sekunder og s� spise byttet i samme �yeblikk som det dukker opp igjen, det er ikke s�rlig rettferdig!


+ Hvordan kan vi sikre at byttet bare forsvinner hvis det ber�rer JafseFisks munn? Tja, vi kunne bruke `ber�rer farge`{.blocklightblue} blokken og se om den ber�rer fiskens tenner. For � gj�re dette, bytt ut `ber�rer`{.blocklightblue} blokken med en `ber�rer farge`{.blocklightblue} blokk i skriptet ditt, klikk p� fargen i blokken og klikk s� p� fiskens tenner. 
+ N� kan vi la byttet flytte seg til et tilfeldig punkt p� skjermen f�r den dukker opp igjen ved � bruke en `g� til`{.blockblue} blokk, og gi den en tilfeldig verdig for __x__ og __y__.

    ```blocks
    n�r gr�nt flagg klikkes
    for alltid
		g� (2) steg
		vend til h�yre (tilfeldig tall fra (-20) to (20)) grader
		sprett tilbake ved kanten
		hvis <ber�rer fargen [#FFFFFF]?>
			skjul
			vent (3) sekunder
			g� til x:(tilfeldig tall fra (-200) til (220)) y: (tilfeldig tall fra (-170) til 170))
			vis
    ```
    
## Test prosjektet { .flag}

Pr�v spillet igjen. Forsvinner byttet bare n�r det ber�rer fiskens tenner? Og kommer det igjen i et tilfeldig punkt p� skjermen � alts� ikke samme sted som det ble spist?

+ JafseFisk m� vite n�r den har spist noe slik at den kan gi fra seg en lyd og bytte drakt. For � gj�re dette kan vi la byttet `send melding`{.blockyellow} om at det er spist, f�r det forsvinner.

    ```blocks
	n�r gr�nt flagg klikkes
    for alltid
		g� (2) steg
		vend til h�yre (tilfeldig tall fra (-20) to (20)) grader
		sprett tilbake ved kanten
		hvis <ber�rer fargen [#FFFFFF]?>
			send melding [Du tok meg!]
			skjul
			vent (3) sekunder
			g� til x:(tilfeldig tall fra (-200) til (220)) y: (tilfeldig tall fra (-170) til 170))
			vis
    ```
    __N� vil vi at fiskens respons p� denne meldingen er � lage en gomlelyd og klikke med kjevene.__

+ Legg til drakten __Dyr/shark-a__ og lyden  __Effekter/bubbles__ til JafseFisk. Kall drakten `lukket munn`.
+ Legg s� til et nytt skript til JafseFisk slik at han kan svare p� meldingen `send melding`{.blockyellow} fra byttedyret. Dette skriptet gj�r at fisken spiller av boblelyden og `bytter drakt til`{.blockpurple} of lukket-munn drakten, venter litt og s� bytter tilbake.

    ```blocks
    n�r jeg mottar [Du tok meg! v]
    spill lyden [bubbles v]
    gjenta (2) ganger
		bytt drakt til [lukket munn v]
		vent (0.5) sekunder
		bytt drakt til [�pen munn v]
    ```

__N� er JafseFisk klar til � spise, s� la oss fylle havet med byttedyr. H�yreklikk p� byttefiguren og velg `lag kopi` til du f�ler du har f�tt nok fisk.__

## Test prosjektet { .flag}
Klikk p� det gr�nne flagget. Spiser JafseFisk byttet? Spiser den alle byttedyrene?

## Lagre prosjektet { .save}

## Noe � tenke p�
Hvorfor m� vi legge til en `vis`{.blockblue} blokk p� starten av byttedyrets skript? Tenk p� hva som ville skje om byttet blir spist og spillet stoppes f�r det dukker opp igjen. Og hva ville skje om spillet ble startet igjen?


__Godt gjort! Du har igrunn fullf�rt spillet! Men fins flere muligheter for utvidelse av spillet. Er du klar for en utfordring?__


## Utfordring 1: Forandre bevegelsene til byttedyrene { .challenge}

For �yeblikket beveger alle byttedyrene seg likt. __Kan du f� ett av dem til � bevegeseg annerledes?__ 
__Hint:__ Ikke bruke for lang tid p� denne oppgaven uten � se p� de andre aktivitene i dette prosjektet.

__Velg deg ut et byttedyr � eksperimentere med.__ Hvis de har samme drakt, bytt farge me `sett farge effekt`{.blockpurple} blokken. Slik kan du se forskjell fra resten av byttedyrene. Pr�v n� � f� dette byttedyret til � bevege seg saktere enn de andre.

F� byttedyret til � bevege seg saktere enn de andre. __Hint:__ Se p� blokken `g� (2) steg`{.blockblue}.


## Test prosjektet{ .flag}
Beveger byttet seg saktere? Gj�r dette spillet bedre?
Hvis du klarte dette, __, pr�v � gj�re et av byttedyrene kjappere enn de andre.__


Beveger byttedyrene seg p� en fornuftig m�te?  Gj�r disse forandringene spillet bedre?
__Hint:__ Hvis byttet ditt sv�mmer rundt i sirkler, sjekk verdiene i `tilfeldig tall`{.blockgreen} blokken i `vend`{.blockblue} blokken.

Hva om du lar alle byttedyrene bevege seg forskjellig, ved � bruke forskjellige kombinasjoner av disse bevegelsene?

Gj�r noen av disse forandringene spillet bedre? Gj�r de spillet med interessant, morsommere, vanskeligere eller lettere? Er noe av dette bedre, syns du?

## Lagre prosjektet { .save}

## Utfordring 2: Hjelp byttet � unng� JafseFisk { .challenge}

Byttedyrene i dette spillet er skikkelig dumme! De sv�mmer bare tilfeldig rundt til de blir spist. Ekte fisk sv�mmer vekk fra rovfisker. N� vil vi __la ett av byttedyrene sv�mme vekk fra JafseFisk.__

Det fins ingen blokk i Scratch som kan gi oss retningen til en annen figur. Men du kan f� en figur til � snu seg i retningen av en annen, og deretter la den snu seg i motsatt retning. Blokkene du trenger er i `Bevegelse`{.blocklightgrey} paletten.

Pr�v n� � hjelpe et av byttedyrene med � __snu seg vekk fra JafseFisk__. Du vil kanskje ogs� la den virre mens den sv�mmer bort?
Du vil kanskje oppdage at byttet setter seg fast i et hj�rne? Du  �nsker kanskje at byttet bare �nsker � flykte dersom JafseFisk kommer for n�re?
__Hint:__ Se tilbake p� hvordan vi brukte `avstand til`{.blocklightblue} blokken tidligere i spillet. 

## Test prosjektet { .flag}
Gj�r dette at fisken er vanskeligere � ta? Gj�r det spillet bedre?

## Lagre prosjektet{ .save}

## Utfordring 3: Legg til poeng { .challenge}
Det er ikke nok bare � spise fisk. Hvordan vet du at du er en bedre spiller enn vennene dine? __Du m� kunne samle poeng, s� la oss legge til en poengtavle.__ Se p� __Keep Score scratch card__ for � f� noen hint om hvordan det kan gj�res. 
Pass p� at poengene g�r tilbake til null ved begynnelsen av spillet. Hvor skal du legge inn denne blokken?

## Test prosjektet { .flag}
G�r poengsummen tilbake til null n�r spillet starter? G�r den opp hver gang du spiser byttedyr?

## Lagre prosjektet { .save}

## Utfordring 4: Legg til en nedtelling { .challenge}

__Gi deg selv en tidsfrist.__ Hvor mange fisk kan du spise p� 30 sekunder?

Se p� __Timer scratch card__  for � se hvordan man legger til en tidtaker til et spill. Begynn med 30 sekunders-spill.

## Test prosjektet { .flag}
Begynner tidtakeren p� 30?
Teller den ned med rett hastighet? 
Kan du fange fisk mens tiden telles ned? Stopper spillet n�r telleren n�r null?

## Lagre prosjektet { .save}

## Utfordring 5: Legg til bonuspoeng { .challenge}
Legg til en bel�nning med h�y bonus poeng om du kan spise alle tre fiskene samtidig. Hvordan kan du vite hvor mange som er spist?

__Hint:__ En m�te � gj�re dette p� er � bruke en variabel for � __telle hvor mange byttedyr som sv�mmer i havet.__

## Lagre prosjektet { .save}

## Utfordring 6: Forandre spillet: Hold byttedyrene i live! { .challenge}
Av og til kan man f� glimrende nye id�er ved � gj�re det motsatte av det man allerede har gjort.

__Endre spillet slik at du isteden kontrollerer et byttedyr i et hav av mange JafseFisk.__ Hvor lenge kan du holde det g�ende f�r du blir spist? Istedet for � bruke poeng, hva med �  gi byttedyret 3 liv og avslutte spillet n�r de er brukt opp?

## Lagre prosjektet { .save}

__Godt gjort, du er ferdig! N� kan du nyte spillet ditt!__
Ikke glem at du kan dele spillet med alle vennene og familien din ved � klikke p� __Legg ut__ i topp-menyen!

