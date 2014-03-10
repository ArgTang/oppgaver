---
title: �rkenl�p
level: 1.6
language: nb-NO
embeds: ["*.png", "../../bilder/*.png"]
...

#�rkenl�p

# Introduksjon { .intro}
Dette er et spill for to, der en papeg�ye og en l�ve kjemper om � komme f�rst gjennom �rkenen. Hver spiller m� trykke en tast s� fort og ofte som mulig for � flytte figuren sin, og den som kommer f�rst til kanten av skjermen vinner.


![skjermbilde](orkenlop.png)

# Steg 1: Lage en scene og legg til figurer { .activity}

## Sjekkliste { .check}

+ Klikk p� Scene og hent en ny bakgrunn fra biblioteket. Velg __Natur/desert__.
+ Fjern Sprite1 ved � h�yreklikke p� figuren og velg Slett.
+ Legg til en ny figur ved � trykke p� ![Velg figur fra biblioteket](figur-fra-bibliotek.png). Velg __Dyr/Lionness__.
+ Legg s� til enda en ny figur: velg Dyr/Parrot. Krymp figuren slik at den er omtrendt like stor som l�vinnen ved � bruke ![Krymp](krymp.png).


# Steg 2: La l�ven og papeg�yen bevege seg { .activity}

Vi vil at figurene skal bevege seg n�r du trykker p� en knapp.

## Sjekkliste { .check}

+ Velg f�rst l�vefiguren og f� den til � `g� (4) steg`{.blockblue} n�r du trykker __�L�__ tasten.
    ```blocks
    n�r [l v] trykkes
    g� (4) steg
    ```

+ Velg s� papeg�yefiguren og la den `g� (4) steg`{.blockblue} n�r du trykker __�A�__ tasten.

    ```blocks
    n�r [a v] trykkes
    g� (4) steg
    ```

## Test prosjektet { .flag}

__Trykk p� det gr�nne flagget.__ 
Beveger l�ven og papeg�yen seg over skjermen n�r du trykker p� �A� og �L� tastene?

## Lagre prosjektet { .save}

# Steg 3: Start kappl�pet { .activity}

__N� m� vi kj�re i gang kappl�pet og k�re en vinner. Vi begynner med � lage startknapp.__

## Sjekkliste { .check}

+ Legg til en ny figur. Velg __Ting/Button3__. Flytt den til midten av scenen. 
+ Klikk p� Drakter-fanen og symbolet T for � legge til tekst. Trykk p� venstre kant av knappen for � legge til et tekstfelt og skriv inn teksten �start�. Du kan flytte p� teksten ved � trykke en gang p� den, og endre innhold ved � dobbeltklikke.
+ Legg n� til et skript som viser figuren n�r spillet starter:

    ```blocks
        n�r gr�nt flagg klikkes
        vis
    ```
+ I tillegg vil vi ha en knapp som teller ned fra 3, sier �L�P� og deretter blir skjult n�r den klikkes. Dette ordner du med f�lgende skript:

    ```blocks
    n�r denne figuren klikkes
        si [3] i (1) sekunder
        si [2] i (1) sekunder
        si [2] i (1) sekunder
        si [L�P!] i (1) sekunder
        skjul
    ```

## Test prosjektet { .flag}

__Klikk p� det gr�nne flagget__ og __trykk p� startknappen__.
Teller knappen ned? Sier den �L�P�? Blir den borte?

## Lagre prosjektet { .save}

Vi �nsker at figurene bare beveger seg etter at kappl�pet er startet og vi �nsker � vite n�r kappl�pet er over.

+ For � vite n�r kappl�pet har startet og sluttet lager vi en variabel med navnet `kappl�p`{.blockorange}. Variabelen skal v�re tilgjengelig for alle figurer. Fjern avhukingen foran variabelen, slik at den ikke vises p� scenen.
+ Sett __kappl�p__ til __[0]__ n�r spillet startes. Forandre `n�r flagget klikkes`{.blockyellow} skriptet slik:

    ```blocks
    n�r gr�nt flagg klikkes
        vis
        sett [kappl�p v] til (0)
    ```

+ N�r nedtellingen er ferdig og l�pet begynner, forandrer vi __kappl�p__verdien til 1. Dette gj�r du ved � legge til blokken `Sett [kappl�p] til (1)`{.blockorange} under `si [1] i (1) sekunder`{.blockpurple} i skriptet som starter med `n�r denne figuren klikkes`{.blockyellow}.
+ S� m� vi lage en regel som sier at figurene bare f�r lov til � bevege seg n�r l�pet har startet � det vil si n�r kappl�p har verdien 1. Klikk f�rst p� papeg�yen. S� legger du til:

    ```blocks
	n�r [a v] trykkes
	hvis <(kappl�p) = [1]>
		g� (4) steg
    ```
+ Gjenta det samme for l�vinnen.

## Test prosjektet { .flag}
__Klikk p� det gr�nne flagget.__

Kan l�ven og papeg�yen bare flytte seg n�r nedtellingen er ferdig?

## Lagre prosjektet { .save}

# Steg 4: Avslutte kappl�pet { .activity}

__N� vil vi vite hvem som vinner kappl�pet, og i tillegg gj�re klart for en ny runde.__

## Sjekkliste { .check}

+ Legg til en blokk i papeg�yens skript som `setter [kappl�p] til (0)`{.blockorange} hvis figuren ber�rer kanten av skjermen.


    ```blocks
    n�r [a v] trykkes
    hvis <(kappl�p) = [1]>
        g� (4) steg
        hvis <ber�rer [kant v]?>
			sett [kappl�p v] til (0)
    ```
+ Spill s� inn en lyd som skal avspilles hvis papeg�yen vinner.
Trykk p� Lyder-fanen og deretter mikrofon-ikonet og spill inn en morsom trudelutt! Opptaket starter n�r du har klikket p� rundingen slik at den blir r�d. Klikk Stopp (firkanten) n�r du er ferdig, og gi den et navn � for eksempel Polly. Noen nettlesere kan sp�rre om tillatelse til � spille inn lyd. Hvis du ikke �nsker dette, bruk lydene som f�lger med figurene.
+ Deretter legger du til blokkene som vil spille lyden og la papeg�yen fortelle at den vant:

    ```blocks
	    n�r [a v] trykkes
		hvis <(kappl�p) = [1]>
			g� (4) steg
			hvis <ber�rer [kant v]?>
				sett [kappl�p v] til (0)
                spill lyden [Polly v]
                si [Polly vinner! v] i (3) sekunder  
    ```
	
+ Gj�r det samme for l�vinnen.

## Test prosjektet { .flag}
__Klikk p� det gr�nne flagget.__

Kan du trykke p� startknappen og deretter bevege dyrene med tastene __A__ og __L__?
Kommer riktig vinnerlyd og melding opp p� skjermen?

## Lagre prosjektet { .save}

# Steg 5: Nullstill spillet { .activity}

__N�r kappl�pet er over m� vi fortelle de andre figurene at spillet er over og nullstille spillet, slik at er klart for en ny runde.__

## Sjekkliste { .check}

+ Klikk p� papeg�yefiguren og legg til en blokk som sender melding �avslutt� etter at figuren sier den har vunnet.


    ```blocks
	n�r [a v] trykkes
	hvis <(kappl�p) = [1]>
		g� (4) steg
		hvis <ber�rer [kant v]?>
			sett [kappl�p v] til (0)
			spill lyden [Polly v]
			si [Polly vinner! v] i (3) sekunder
			send melding [avslutt v]
    ```

+ Vi trenger n� et nytt skript som lytter etter denne avslutningsmeldingen og flytter papeg�yen tilbake til start.

    ```blocks
    n�r jeg mottar [avslutt v]
    sett x til (-170)
    ```
	
+ Legg til det samme skriptet for l�ven. Test forskjellige __x__-verdier for � v�re sikker p� at l�ven og papeg�yen starter fra samme sted.
+ For at figurene skal st� p� startstreken n�r kappl�pet starter den aller f�rste gangen m� vi ogs� legge til f�lgende blokk til begge figurene: 

    ```blocks
    n�r flagg klikkes
        sett x til (-170)
    ```
	
+ For at spillerne skal kunne klikke i gang nye runder m� passe p� at start-knappen kommer etter hver avsluttet runde. Klikk p� figuren og legg til et skript som viser knappen n�r avslutningsmeldingen er mottatt.

    ```blocks
    n�r jeg mottar [avslutt v]
    vis
    ```

	
## Test prosjektet { .flag}

__Klikk p� det gr�nne flagget.__

Kan du spille mot en venn? En av dere styrer papeg�yen ved � trykke A, og den andre l�ven
ved � trykke L.

## Lagre prosjektet { .save}


##Utfordring 1: Legg til en rakett! { .challenge}

* __Legg til en rakett__ som kan brukes �n gang per kappl�p og som flytter papeg�yen eller l�ven __30 steg p� en gang.__
* __Legg til en ny drakt__  med ild som kommer ut bak hver figur. La denne aktiveres n�r raketten avfyres.
* __Lag en lyd__ som figuren kan gi fra seg n�r raketten avfyres.

    ```blocks
	n�r [a v] trykkes
		hvis <(kappl�p) = (1) og (rakett) = (0)> 
			skift til drakt [parrot-b v]
			sett [rakett v] til (1)
			g� (4) steg
			spill lyden [Rooster v]
			hvis <ber�rer [kant v]?>
				sett [kappl�p v] til (0)
                spill lyden [Polly v]
                si [Polly vinner! v] i (3) sekunder
				send melding [avslutt v]
	
    
## Test prosjektet { .flag}

## Lagre prosjektet { .save}

## Utfordring 2: Bruk egendefinerte blokker for � forenkle skriptet ditt { .challenge}

Koden som brukes til � sjekke om kappl�pet er over brukes n� to steder for hver figur; n�r figuren beveger seg normalt og n�r den beveger seg med rakett.
Vi kan forenkle skriptet v�rt ved � bruke en egendefinert blokk. Dette er en samling kode som brukes flere steder. Det er nesten som at vi lager v�r egen Scratch kodeblokk!

+  Velg papeg�yens skript.
+ Velg `Flere klosser`{.blocklightgrey}-paletten og klikk s� p� `Lag en kloss`{.blocklightgrey} knappen.
+ Kall klossen din __ferdig__ og trykk OK.
+ Du vil n� f� en `definer ferdig`{.blockpurple} blokk i skriptvinduet ditt. Flytt den litt for seg selv. 
+ L�sriv `hvis`{.blockyellow} `ber�rer [kant v]?`{.blocklightblue}` blokken og dra den til `definer ferdig`{.blockpurple} blokken.

    ```blocks
    definer ferdig
	hvis <ber�rer [kant v]?>
				sett [kappl�p v] til (0)
                spill lyden [Polly v]
                si [Polly vinner! v] i (3) sekunder
				send melding [avslutt v]
    
    n�r [a v] trykkes 
    hvis <(kappl�p) = (1) og (rakett) = (0)>
		skift til drakt [parrot-b v]
		sett [rakett v] til (1)
		g� (4) steg
		spill lyden [Rooster v]
    ```
	
Kan du dra `ferdig`{.blockpurple} blokken fra paletten og bruke den slik som andre kodebiter?

Slett den andre `hvis`{.blockyellow}` ber�rer [kant v]?`{.blocklightblue} blokken fra skriptet ditt og erstatt den med en `ferdig`{.blockpurple} blokk.

Gj�r dette koden din enklere � lese? Kan du lage en tilsvarende egendefinert blokk for l�vinnen?

## Test prosjektet { .flag}

## Lagre prosjektet { .save}

__Veldig bra! N� er du ferdig og kan nye spillet du har laget!__
