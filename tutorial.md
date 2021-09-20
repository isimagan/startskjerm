# Startskjerm

## Intro @showdialog
Vi skal få LED-lysene til å lyse, en etter en, til hele skjermen er fylt.
![GIF-animasjon](https://isimagan.github.io/startskjerm/img/Visning.gif)
Dette skal vi gjøre med ``funksjoner``.
![Sluttprodukt](https://isimagan.github.io/startskjerm/img/microbit-Startskjerm.png)

## Steg 1
Lag to variabler: ``||variables:lysX||`` og ``||variables:lysY||``

## Hvorfor lys X og Y?
LED-lysene er et koordinatsystem. Øverst til venstre er punkt ``(0, 0)``. Det er det lyset du ser lyser. For hvert lys vi går mot høyre øker vi X med 1, og for hvert lys vi går nedover øker vi Y med 1.
![Punkt (0,0)](https://isimagan.github.io/startskjerm/img/Lys 0 0.png)

## Steg 2
Under ``||variables:Variabler||`` kan man trykke på ``Avansert``, og øverst på den lista som dukker opp ser du ``||functions:Funksjoner||``.
Trykk på ``Lag en funksjon``, og bytt ut navnet ``gjørNoe`` med ``startSkjerm``.
![Funksjoner](https://isimagan.github.io/startskjerm/img/Funksjoner.png)

## Steg 3 @showhint
Nå skal du ha fått en blokk hvor vi skal fylle ut funksjonen vi har laget.
``` blocks
function startSkjerm() {}
```

## Steg 4
Vi setter variablene våre til ``0``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
}
```

## Steg 5
Kan du regne ut hvor mange LED-lys det er til sammen på en micro:bit?

Vi skal sette inn løkken ``||loops:gjenta 4 ganger||``, men du må bytte ut tallet ``4`` med så mange lys det er.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 4; index++) {}
}
```

## Steg 6
Vi skal nå bruke en ny blokk vi ikke har brukt før: ``||led:Skjerm||``.

Sett inn ``||led:bytt x 0 y 0||``, og bytt ut ``0`` etter ``x`` med ``||variables:lysX||``, og tilsvarende med ``Y``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(0, 0)
    }
}
```

### Steg 6a
Bytt ut ``||led:x 0||`` med ``||variables:lysX||``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, 0)
    }
}
```

### Steg 6b
Bytt ut ``||led:y 0||`` med ``||variables:lysY||``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
    }
}
```

## Steg 7
Vi går til neste lys på samme linje. ``||led:Y||`` vil fortsatt være ``0``, så ``x`` må endres med ``1`` før ``||loops:gjenta||`` starter på nytt.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
    }
}
```

## Steg 8
Som vi så tidligere så begynner første linje på 0. Det vil si at når vi har kommet til 4 så er vi på enden.

Dette tar ikke kodingen hensyn til. Når vi har kommet til at ``||variables:ledX = 4||`` så vil neste bli ``5``. Så når vi kommer til ``5`` må vi gjøre noe for å bytte linje og starte på ``0`` igjen.

## Steg 9
Sett inn en ``||logic:hvis||``-blokk, bytt ut ``sann`` med ``||logic:0 = 0||``, første ``0`` med ``||variables:lysX||`` og andre ``0`` med ``5``.

``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (true) {}
    }
}
```

### Steg 9a
Bytt ut ``sann`` med ``0 = 0``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (0 == 0) {}
    }
}
```

### Steg 9b
Bytt ut første ``0`` med ``||variables:lysX||``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (lysX == 0) {}
    }
}
```

### Steg 9c
Bytt ut andre ``0`` med ``5``.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (lysX == 5) {}
    }
}
```

## Steg 10
Hva skal skje hvis ``||variables:lysX = 5||``? Jo, vi må starte på neste linje, og starte på første lys på den nye linjen.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (lysX == 5) {}
    }
}
```

### Steg 10a
Endre ``||variables:lysY||`` med ``1``, slik at vi starter på neste linje.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (lysX == 5) {
            lysY += 1
        }
    }
}
```

### Steg 10b
Sett ``||variables:lysX||`` til ``0`` så vi starter på første lys igjen.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (lysX == 5) {
            lysY += 1
            lysX = 0
        }
    }
}
```

## Steg 11
Hvis du hadde kjørt koden nå så ville du sett at alle lysene lyser med en gang. For at de skal lyse en etter en så må vi ha en liten pause mellom hvert lys. Du bestemmer hvor lang tid det skal gå mellom hvert lys som slås på.
``` blocks
function startSkjerm() {
    lysX = 0
    lysY = 0
    for (let index = 0; index < 25; index++) {
        led.toggle(lysX, lysY)
        lysX += 1
        if (lysX == 5) {
            lysY += 1
            lysX = 0
        }
        basic.pause(100)
    }
}
```

## Steg 12
**Funksjonen er ferdig!**

Sett inn en ``||basic:ved start||`` om den ikke er der allerede. Inni setter du inn ``||functions:kjør startSkjerm||``. Den finner du i ``||functions:Funksjoner||``-menyen.
``` blocks
startSkjerm()
function startSkjerm() {}
```

## Ferdig @showdialog
**Ekstraoppgaver:**
- Vi har brukt ``||led:bytt||``-blokken. Det vil si at lyset slås på om det er av, og av hvis det er på. Se hva som skjer hvis du også setter inn funksjonen når du trykker på ``||input:knapp A||``.
- Kan du lage en annen animasjon for å slå av lysene når du enten trykker på ``||input:knapp B||``, ``||input:knapp A+B||`` eller ``||input:når ristes||``?
```blocks
input.onButtonPressed(Button.A, function () {})
input.onButtonPressed(Button.B, function () {})
input.onButtonPressed(Button.AB, function () {})
input.onGesture(Gesture.Shake, function () {})
```

## Steg 13
Når du trykker på *"Slutt"* er du ferdig. Se på Showbie hvordan du overfører kodingen fra Safari til appen, og videre til en micro:bit.

<script src="https://makecode.com/gh-pages-embed.js"></script><script>makeCodeRender("https://makecode.microbit.org/", "isimagan/startskjerm");</script>