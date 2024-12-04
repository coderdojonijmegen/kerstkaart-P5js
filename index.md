---
title: "Maak je eigen kerstkaart-animatie met P5.js! 🎄 🌟"
date: 2024-12-03T20:51:01+02:00
draft: false
toc: true
headercolor: "teal-background"
onderwerp: P5js 
---

Zo kort voor kerst gaan we een kerstkaart programmeren, compleet met een kerstboom, kerstballen, sneeuw en een leuke kerstwens. Kun jij de sneeuwvlokken echt laten vallen?

<!--more-->

We maken de kerstkaart met P5.js. Volg de handleiding stap voor stap en speel bij elke stap met de verschillende opties!

---


## Stap 1: Maak je eerste kerstboom! 🎄
1. **Ga in je browser naar <a href="https://editor.p5js.org/" target="_blank">editor.p5js.org</a>.**
    
    In het venster links kun je programmeren. 
    Als je op de afspeelknop linksbovenaan klikt dan wordt je code uitgevoerd. Je ziet het resultaat in het venster rechts. Probeer het maar eens.

2. **Begin aan je kerstkaart.** 

    Laten we beginnen door de achtergrond zwart te maken. Dat doe je door de functie `background()` een waarde van 0 te geven.

    Maak je kerstkaart passend door de nummers in `createCanvas(400, 400)` te veranderen. 
    
    Je kunt ook de nummers vervangen door `windowWidth` en `windowHeight`, dan past het altijd, dus ook als je het venster later groter maakt:

   ```javascript
     createCanvas(windowWidth, windowHeight);
    ```

    Klik op de afspeelknop om te kijken of het goed werkt.

3. **Begin met een kerstboom tekenen**:
   - Een kerstboom heeft een stam en groene takken.
   - Voor de stam kunnen we een rechthoek tekenen met de functie `rect()`:
    ```javascript
    rect(175, 300, 50, 100); // x, y, breedte, hoogte
    ```
   - De takken kun je tekenen met een driehoek (of met drie driehoeken half over elkaar heen). Gebruik daarvoor `triangle()`:

   ```javascript
   triangle(100,10, 60,100, 120,100); // top, links, rechts
   ```

4. **Run je code**! Zie je een kerstboom? Goed gedaan! 🎉


### Uitleg van coördinaten in P5.js 🖼️

Zoals je ziet gebruikt P5.js een **coördinatenstelsel** om vormen te tekenen op een bepaalde plek op het scherm. Dit zijn de belangrijkste punten om te begrijpen:

- Coördinaten worden weergegeven als `(x, y)`. `x` is de horizontale positie,`y` de verticale positie.
- Het **linkerbovenhoekpunt** van het venster is het beginpunt. De coördinaten van dit punt zijn `0,0`.
- De **x-coördinaat** betekent 'zoveel pixels vanaf de linkerkant'. Hoe hoger het getal voor x des te verder naar rechts het is.
- De **y-coördinaat** betekent 'zoveel pixels vanaf de bovenkant'. Hoe hoger het getal voor y des te verder naar beneden het is.

Als je `print(mouseX, mouseY);` toevoegt aan `draw()` (bijvoorbeeld één regel boven de gekrulde haak onderaan) dan zie je linksonderin de coördinaten van je muis. 

4. **De stam van de kerstboom vergroten en verplaatsen**
    
    Als je je rechthoek wil plaatsen op `(50, 100)`:
    - `x = 50`: 50 pixels naar rechts.
    - `y = 100`: 100 pixels naar beneden.
```javascript
rect(50, 100, 200, 150); // (x, y, breedte, hoogte)
```
- `(50, 100)` is de **linkerbovenhoek** van de rechthoek.
- De breedte is 200 pixels.
- De hoogte is 150 pixels.


---


## Stap 2: Kleur je kerstkaart 🌈
Geef nu je kerstboom wat kleur om er wat leven in te blazen!

1. **Wat betekenen `fill()` en `stroke()`?**
   - `fill(r, g, b)` geeft de binnenkleur.
   - `stroke(r, g, b)` bepaalt de randkleur.
   - `strokeWeight()` maakt de rand dikker of dunner.

2. **Probeer dit:**
   - Voeg dit toe na `background(200)` in de code:
     ```javascript
     stroke(255, 0, 0); // Rode randen
     strokeWeight(4); // Maak de randen dikker
     
     fill(139, 69, 19); // Bruin
     fill(0, 128, 0); // Groen
     fill(34, 139, 34); // Groen
     ```

3. **Speel met de kleuren!**
   - Probeer andere getallen bij `fill()` (bijvoorbeeld blauw `fill(0, 0, 255)` of lichtblauw `fill(200, 200, 255)`).

---

## Stap 3: Voeg kerstballen toe! 🎅
Laten we kerstballen toevoegen als je klikt met de muis.

1. **Schrijf deze code in je `draw()` functie:**
   ```javascript
   function mousePressed() {
     let r = random(255); // Random rood
     let g = random(255); // Random groen
     let b = random(255); // Random blauw
     let size = random(10, 30); // Random grootte

     fill(r, g, b); // Gebruik de random kleuren
     noStroke(); // Geen rand
     ellipse(mouseX, mouseY, size); // Een bal op de muispositie
   }
   ```

2. **Klik op de boom!**
   - Zie je hoe elke klik een kerstbal toevoegt?

---

## Stap 4: Voeg een kerstwens toe! 🎁
Een kerstkaart is niet compleet zonder een kerstwens!

1. **Gebruik de `text()` functie:**
   - Voeg dit toe aan de `setup()` functie:
     ```javascript
     fill(255, 255, 0); // Gele tekst
     textSize(74); // Maak de tekst groot
     text("Fijne feestdagen!", 50, 50); // Tekst en positie
     ```

2. **Run je code**:
   - Zie je de tekst bovenaan? 🎉

---




### **Wat is een object in P5.js?** 🛠️

Een **object** in P5.js is een **manier om gegevens (informatie)** en **functies (acties)** te combineren in één pakket. Dit maakt het makkelijk om dingen zoals vormen, sneeuwvlokken of andere items in je animatie te beheren.

#### **1. Waarom gebruiken we objecten?**
Stel dat je een sneeuwvlok wilt maken. Een sneeuwvlok heeft:
- **Eigenschappen**: Waar is de vlok? Hoe groot is hij?
- **Gedrag**: Wat doet de vlok? (Bijvoorbeeld vallen.)

In plaats van losse variabelen voor elke eigenschap te maken, kun je alles samenvoegen in een object.

#### **2. Hoe maak je een object in P5.js?**
- **Manier 1: Een eenvoudig object**
  ```javascript
  let sneeuwvlok = {
    x: 200, // Eigenschap: horizontale positie
    y: 0,   // Eigenschap: verticale positie
    size: 10, // Eigenschap: grootte

    // Gedrag: laat de vlok vallen
    vallen: function() {
      this.y += 2; // Beweeg de vlok 2 pixels omlaag
    },

    // Gedrag: teken de vlok
    tekenen: function() {
      ellipse(this.x, this.y, this.size); // Teken de vlok als een cirkel
    }
  };
  ```

- **Manier 2: Gebruik een class**
Een class is een blauwdruk om meerdere objecten te maken die hetzelfde gedrag hebben, bijvoorbeeld veel sneeuwvlokken.
  ```javascript
  class Sneeuwvlok {
    constructor(x, y, size) {
      this.x = x;
      this.y = y;
      this.size = size;
    }

    vallen() {
      this.y += 2;
    }

    tekenen() {
      ellipse(this.x, this.y, this.size);
    }
  }

  // Maak een sneeuwvlok
  let vlok = new Sneeuwvlok(200, 0, 10);
  vlok.vallen();
  vlok.tekenen();
  ```

#### **3. Belangrijke termen**
- **Eigenschappen**: Dit zijn de gegevens van een object, zoals `x`, `y`, of `size`.
- **Methoden**: Dit zijn de functies binnen een object, zoals `vallen()` of `tekenen()`.

#### **4. Waarom is dit handig?**
Als je 100 sneeuwvlokken wilt maken, kun je met een class gemakkelijk meerdere objecten beheren:
```javascript
let sneeuwvlokken = [];

function setup() {
  createCanvas(400, 400);
  for (let i = 0; i < 100; i++) {
    sneeuwvlokken.push(new Sneeuwvlok(random(width), random(height), random(5, 15)));
  }
}

function draw() {
  background(0);
  for (let vlok of sneeuwvlokken) {
    vlok.vallen();
    vlok.tekenen();
  }
}
```

---

Objecten zijn super-handig voor geavanceerde animaties in P5.js! 🚀

---

Gefeliciteerd! Je hebt een eigen kerstkaart-animatie gemaakt. Deel hem met je familie en vrienden om de kerstvreugde te verspreiden! 🎄✨

Hier zijn twee optionele stappen die je kunt volgen om je kerstanimatie nog specialer te maken en te delen met familie! ✨

---

## **Optionele Stap 6: Exporteer je animatie als een GIF** 🎥

Als je een account aanmaakt op [p5js.org](https://editor.p5js.org/signup) dan kun je je schets opslaan en de link naar familie en vrienden sturen.
Wat ook kan, is je kerstkaart-animatie opslaan als een bewegend plaatje (GIF), zodat je die kunt rondsturen. Hier is hoe dat werkt!

1. **Voeg de p5.js library "ccapture.js" toe**:
   - Ga naar de HTML-pagina van je project door linksbovenaan op het pijltje te klikken naast `sketch.js`.
   Klik op `index.html` en voeg daar deze regel toe in het `<head>`-gedeelte (kopiëer en plak de hele regel, dat scheelt een boel moeite en dan maak je geen typefouten):
     ```html
     <script src="https://cdnjs.cloudflare.com/ajax/libs/ccapture.js/1.1.0/CCapture.all.min.js"></script>
     ```

2. **Code toevoegen om je animatie op te nemen:**
   - Voeg de volgende code bovenaan je script toe:
     ```javascript
     let capturer; // Voor de GIF-opname
     let recording = false; // Om te weten wanneer je opneemt
     ```

   - Pas je `setup()` functie aan:
     ```javascript
     function setup() {
       createCanvas(400, 400);
       capturer = new CCapture({ format: 'gif', framerate: 30 });
     }
     ```

   - Voeg een toetsenbordactie toe om te beginnen of te stoppen met opnemen:
     ```javascript
     function keyPressed() {
       if (key === 'R' || key === 'r') { // Druk op 'R' om op te nemen
         if (!recording) {
           capturer.start();
           recording = true;
           console.log("Recording started!");
         } else {
           capturer.stop();
           capturer.save();
           recording = false;
           console.log("Recording stopped and saved!");
         }
       }
     }
     ```

   - Voeg dit toe aan je `draw()` functie om de frames op te nemen:
     ```javascript
     if (recording) {
       capturer.capture(canvas); // Neem het canvas op
     }
     ```

3. **Start de opname**:
   - Druk op de "R"-toets terwijl je animatie draait.
   - Druk opnieuw op "R" om de opname te stoppen en je GIF op te slaan. Je browser downloadt het bestand automatisch.

---

## **Optionele Stap 7: Laat een belletje klinken bij sneeuwvlokken** 🔔

Wil je een vrolijk belgeluid horen als een sneeuwvlok uit beeld verdwijnt? Hier is hoe je dat doet!

1. **Download een belgeluid**:
   - Zoek een gratis belgeluid (bijvoorbeeld van [freesound.org](https://freesound.org)) en download het in MP3- of WAV-formaat.
   - Voeg het geluidsbestand toe aan je project (bijvoorbeeld `bel.mp3`).

2. **Voeg de p5.sound library toe**:
   - Ga naar de HTML-pagina van je project en voeg deze regel toe in het `<head>`-gedeelte:
     ```html
     <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.6.0/addons/p5.sound.min.js"></script>
     ```

3. **Laad en speel het geluid in je code**:
   - Voeg dit bovenaan je script toe:
     ```javascript
     let bellSound;

     function preload() {
       bellSound = loadSound('bel.mp3'); // Zorg dat het bestand in je projectmap staat
     }
     ```

   - Speel het geluid af als een sneeuwvlok uit beeld verdwijnt:
     ```javascript
     // Stel dat je een array van sneeuwvlokken hebt genaamd "snowflakes"
     for (let i = snowflakes.length - 1; i >= 0; i--) {
       let flake = snowflakes[i];
       flake.update(); // Update de positie van de sneeuwvlok

       if (flake.y > height) { // Als de sneeuwvlok uit beeld gaat
         snowflakes.splice(i, 1); // Verwijder de sneeuwvlok
         bellSound.play(); // Speel het belgeluid
       }
     }
     ```

4. **Test je animatie**:
   - Run je code en luister naar het belletje elke keer dat een sneeuwvlok onderaan verdwijnt. 🎵

---

Met deze extra stappen kun je je animatie niet alleen interactief maken, maar ook delen als een GIF én een geluidseffect toevoegen voor extra kerstmagie. Veel plezier! 🎄✨



## Stap 5: Voeg je eigen magie toe ✨
- Probeer andere tekst te schrijven met `text()`.
- Maak speciale kerstballen met verschillende vormen.








## Licentie
Deze instructies worden, net als alle andere instructies van CoderDojo Nijmegen, aangeboden onder een [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Licentie](http://creativecommons.org/licenses/by-nc-sa/4.0/).
