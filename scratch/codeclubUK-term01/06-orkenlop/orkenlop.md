---
title: �rkenl�p
level: 1.6
language: nb-NO
embeds: ["*.png", "../../bilder/*.png"]
...

#�rkenl�p

# Introduction { .intro}
Dette er et spill for to, der en papeg�ye og en l�ve kjemper om � komme f�rst gjennom �rkenen. Hver spiller m� trykke en tast s� fort og ofte som mulig for � flytte figuren sin, og den som kommer f�rst til kanten av skjermen vinner.


![screenshot](�rkenl�p.png)

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

+ For � vite n�r kappl�pet har startet og sluttet lager vi en variabel med navnet `kappl�p`{.blockorange}. Fjern avhukingen til venstre for variabelen, slik at den ikke vises p� scenen.
+ Sett __kappl�p__ til __[0]__ n�r spillet startes. Forandre `n�r flagget klikkes`{.blockyellow} skriptet slik:

    ```blocks
    n�r gr�nt flagg klikkes
        vis
        sett [kappl�p v] til (0)
    ```
+ N�r nedtellingen er ferdig og l�pet begynner, forandrer vi __kappl�p__verdien til 1.
+ Now we need to stop the lion and the parrot from moving unless the racing variable is set to be 1. Click on the parrot sprite. __Add a control block to the script__ that only allows the parrot to move if __racing = 1__.

    ```blocks
    
        when [a v] key pressed
        if <(racing) = [1]>
            move (4) steps
    ```
+ Now do the same for the lion sprite.

## Test prosjektet { .flag}
__Klikk p� det gr�nne flagget.__

Does the lioness or the parrot move only after the countdown has finished?

We want to know who wins the race and reset it when it has finished so you can
race again.

## Lagre prosjektet { .save}

# Steg 4: Finishing the race { .activity}

## Sjekkliste { .check}

+ Add a block to the parrot�s script that sets the **racing** variable to be 0 when the sprite touches the edge of the screen.

    ```blocks
    when [a v] key pressed
    if <(racing) = [1]>
        move (4) steps
        if <touching [edge v]?>
        set (racing) to [0]
    ```
+ Now we want the parrot to let us know if it wins the race. Record a new sound for the Parrot sprite that will be played when the parrot wins. Click `sounds`{.blocklightgrey} and then record the sound of the parrot winning the race!
+ Now add blocks that `play`{.blockpurple} the sound you recorded and makes the parrot say it has won:

    ```blocks
        when [a v] key pressed
        if <(racing) = [1]>
            move (4) steps
            if <touching [edge v]?>
                set (racing) to [0]
                play sound [recording1 v]
                say [The Parrot Wins! v] for (3) secs   
    ```
+ Now repeat these steps for the lioness.

## Test prosjektet { .flag}
__Klikk p� det gr�nne flagget.__

Can you press the start button and race by pressing the �A� and �L� keys?
Do the sprites make their winning sound and say they�ve won when they reach the end of the race?

## Lagre prosjektet { .save}

# Steg 5: Resetting the game { .activity}

After the race is finished we need to tell the other sprites we have won and reset the game so we can play again.

__We need the winning sprite to broadcast that it has won.__

## Sjekkliste { .check}

+ Click on the Parrot sprite.
Add a block that broadcasts a **"finished�** message after the sprite says it has won.

    ```blocks
    when [a v] key pressed
    if <(racing) = [1]>
        move (4) steps
        if <touching [edge v]?>
            set (racing) to [0]
            play sound [recording1 v]
            say [The Parrot Wins! v] for (3) secs
            broadcast [finished v]
    ```

+ Now we need to add a new script that listens for the finished broadcast and moves the parrot back to the start. What happens if you change the value that **x** is set to?

    ```blocks
    when I receive [finished v]
        set x to (-170)
    ```
+ Now add the same script for the lioness. Test different **x** values to make sure the lion and the parrot line up at the start.
+ We also want to put the lion and the parrot in the same position when the project is run, so add another script to each that moves them to the start when we click the flag.

    ```blocks
    when FLAG clicked
        set x to (-170)
    ```
+ Now click on the button sprite and add a script that shows it when it receives the finished message.

## Test prosjektet { .flag}

__Klikk p� det gr�nne flagget.__

Can you race against a friend, one of you moving the parrot by pressing �A� and the other moving the Lion by pressing �L�?

## Lagre prosjektet { .save}

##Challenge 1: Add a booster { .challenge}

* __Try to add a booster__ that you can use once each race that moves the parrot or the lion __30 steps in 1 go.__
* __Add a new costume__ with fire coming out behind for each sprite and make it appear when the boost is pressed.
* __Create another sound__ that the sprite will make when the boost is pressed.

    ```blocks
    when [p v] key pressed
    if <<(racing) = [1]> and <(boosted) = [0]>>
        switch to costume [parrot-boost v]
        set [boosted v] to [1]     
        move (4) steps
        if <touching [edge v]?>
             set (racing) to [0]
            play sound [recording1 v]
            say [The Parrot Wins! v] for (3) secs
            broadcast [finished v]
    ```
    
## Test prosjektet { .flag}

## Lagre prosjektet { .save}

##Challenge 2: Use custom blocks to simplify your script { .challenge}

The code to check if the race has finished is now used in two places for each sprite: when the sprite is moving normally and when it's moving with the booster. We can simplify our script using a custom block which is a chunk of code that gets used in more than one place. It's a bit like making up our own Scratch code block!

+  Choose the Parrot's script.
+ Select the `More Blocks`{.blocklightgrey} palette and then click the `Make a Block`{.blocklightgrey} button. 
+ Give the custom block a name by typing **"finished"** into the pink box. Then click OK.
+ You'll now see a `define finished`{.blockpurple} block appear in the scripts window. Drag it to a clear area.
+ Detach the `if`{.blockyellow}`touching edge?`{.blocklightblue}`then`{.blockyellow} block and drag it to the `define finished`{.blockpurple} block.


    ```blocks
    define finished
     if <touching [edge v]?>
         set (racing) to [0]
         play sound [recording1 v]
         say [The Parrot Wins! v] for (3) secs
         broadcast [finished v]
    
    when [q v] key pressed 
    if <<(racing) = [1]> and <(boosted) = [0]>>
        switch to costume [parrot-boost v]
        set [boosted v] to [1]     
        move (4) steps
    finished
    ```
Can you drag the `finished`{.blockpurple} block from the palette and use it like any other code item?

Delete the other `if`{.blockyellow}`touching edge?`{.blocklightblue} block from your script and replace it with another `finished`{.blockpurple} custom block.

Does this make your code easier to read? Can you create a similar custom block for the lioness sprite?

## Test prosjektet { .flag}

## Lagre prosjektet { .save}

__Well done you�ve finished, now you can enjoy the game!__
