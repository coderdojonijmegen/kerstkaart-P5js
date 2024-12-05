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

    - Laten we beginnen door de achtergrond zwart te maken. Dat doe je door de functie `background()` een waarde van 0 te geven.
    - Voor wat we zo gaan doen is het belangrijk dat `background()` in `setup()` staat en niet in `draw()`. Selecteer die hele regel, knip en plak hem op een regel direct onder `createCanvas()`.
    - Maak je kerstkaart passend door de nummers in `createCanvas(400, 400)` te veranderen. 
    
    Je kunt ook de nummers vervangen door `windowWidth` en `windowHeight`, dan past het altijd, dus ook als je het venster later groter maakt:

   ```javascript
     createCanvas(windowWidth, windowHeight);
    ```

    Klik op de afspeelknop om te kijken of het goed werkt.

3. **Begin met een kerstboom tekenen**:
   - Een kerstboom heeft een stam en groene takken.
   - Voor de stam kunnen we een rechthoek tekenen met de functie `rect()`. Zet deze code in het script, ná `background()`:
    ```javascript
    rect(90, 100, 30, 20); // x, y, breedte, hoogte
    ```
   - De takken kun je tekenen met een driehoek. Gebruik daarvoor `triangle()`:
    ```javascript
    triangle( 70,100, 140,100, 105,10 ); // links, rechts, top
    ```

4. **Run je code**! Zie je een kerstboom? Goed gedaan! 🎉

---

### Uitleg van coördinaten in P5.js 🖼️

Zoals je ziet gebruikt P5.js een **coördinatenstelsel** om vormen te tekenen op een bepaalde plek op het scherm. Dit zijn de belangrijkste punten om te begrijpen:

- Coördinaten worden weergegeven als `(x, y)`. `x` is de horizontale positie,`y` de verticale positie.
- Het **linkerbovenhoekpunt** van het venster is het beginpunt. De coördinaten van dit punt zijn `0,0`.
- **x** betekent 'zoveel pixels vanaf de linkerkant'. Hoe groter het getal voor x des te verder naar rechts het is.
- **y** betekent 'zoveel pixels vanaf de bovenkant'. Hoe groter het getal voor y des te verder naar beneden het is.

Als je `print(mouseX, mouseY);` toevoegt aan `draw()` dan zie je linksonderin de coördinaten van je muis als je die over je animatie beweegt. 

---

5. **Maak de kerstboom een heel stuk groter! 🎄**
    
    Maak de kerstboom bijna even hoog als het venster. Begin met de takken.

    - Een driehoek teken je door in `triangle()` de coördinaten op te geven van drie hoekpunten.
    - Om een mooie grote driehoek te tekenen moet je even zoeken naar de juiste getallen. Het is een kwestie van uitproberen. Verander dus de coördinaten voor de drie punten in ```triangle()```.
        ```javascript
        triangle( x,y, x,y, x,y );
        ```
    - Als je wil kun je je boom ook tekenen met drie overlappende driehoeken van verschillende grootte, door nog twee regels met ```triangle()``` toe te voegen. 

6. **Verplaats de stam 🪵**

    - Om de rechthoek weer onder de driehoek te plaatsen verander je de eerste twee argumenten van `rect()`:
        - het eerste getal is `x`, het aantal pixels naar rechts
        - het tweede getal is `y`, het aantal pixels naar beneden.
        - Deze coördinaten zijn de **linkerbovenhoek** van de rechthoek.

    - Om de grootte van de rechthoek te veranderen pas je de laatste twee argumenten van `rect()` aan.
       ```javascript
       rect(x, y, breedte, hoogte);
       ```

---


## Stap 2: Kleur je kerstkaart in 🌈
Geef nu je kerstboom wat kleur om er wat leven in te blazen!

1. **Wat betekenen `fill()` en `stroke()`?**
   - Met `fill(r, g, b)` geef je de vormen een kleur.
   - `stroke(r, g, b)` bepaalt de randkleur.
   - `strokeWeight()` maakt de rand dikker of dunner.

    Je kunt kleuren opgeven met een getal tussen 0 en 255. 255 betekent 'helemaal aan' en 0 betekent 'helemaal uit'. Dus als je bijvoorbeeld een vorm fel rood wil kleuren, dan zet je er een `fill()` boven met rood vol aan en groen en blauw op 0:
    ```javascript
     fill(255, 0, 0);
    ```

2. **Probeer het:**
   - Voeg dit toe na `background(0)` in de code:
     ```javascript
     stroke(255, 0, 0); // Rode randen
     strokeWeight(4); // Maak de randen dikker
     
     fill(255, 200, 255); // lichtroze
     ```

3. **Ronde randen**
   - Als je dat mooier vindt, kun je `strokeJoin(ROUND);` gebruiken om de boom afgeronde randen te geven.
   - Als je een vorm helemaal geen rand wil geven dan kun je er `noStroke();` boven zetten.

4. **Speel met de kleuren!**
   - Probeer andere getallen bij `fill()` (bijvoorbeeld bruin `fill(139, 69, 19);`).
   - Geef de stam, de takken en de rand elk een andere kleur.
   - Op de website <a href="https://rgbcolorpicker.com/" target="_blank">rgbcolorpicker.com</a> kun je gemakkelijk kleuren uitkiezen.

---

## Stap 3: Voeg kerstballen toe! 🎅🔮
Laten we kerstballen toevoegen als je klikt met de muis.

1. **Kopiëer deze code en plak hem onderaan je script:**
   ```javascript
   function mousePressed() {

     let r = random(255); // willekeurig rood
     let g = random(255); // willekeurig groen
     let b = random(255); // willekeurig blauw

     let grootte = random(10, 30); // willekeurige grootte

     fill(r, g, b); // Gebruik de random kleuren
     noStroke(); // Geen rand

     circle(mouseX, mouseY, grootte); // Teken een bal op de muispositie
   }
   ```
   (Zorg dat je deze code helemaal onderaan zet, dus ná de gekrulde haak `}` die de `draw()`-functie afsluit.)

2. **Klik op de boom! 🌲**
   - Zie je hoe elke klik een kerstbal toevoegt?
   - `mousePressed()` is een functie die P5.js uitvoert elke keer dat je op de muis klikt.
   - De functie `random()` geeft een willekeurig getal tussen 0 en het nummer dat je opgeeft. Elke kerstbal krijgt dus andere mix van kleuren.
   - Als je twee getallen opgeeft bij `random()` dan krijg je een willekeurig getal tussen die twee waarden. Op die manier zijn de kerstballen dus steeds een andere grootte, maar niet kleiner dan 10 pixels en niet groter dan 30.

---

## Stap 4: Voeg een kerstwens toe! 🎁
Een kerstkaart is niet compleet zonder een kerstwens!

1. **Gebruik de `text()` functie:**
   - Voeg dit toe aan de `setup()` functie, ónder het tekenen van je kerstboom:
     ```javascript
     noStroke();                    // geen rand
     textSize(30);                  // grootte van de letters
     fill(246, 246, 255);           // tekstkleur
     text("Fijne kerst!", 50, 50);  // Tekst en positie
     ```

2. **Run je code**:
   - Zie je de tekst bovenaan? 🎉

3. **Maak de tekst groot en kleurig**
    - Hoe groter het getal in `textSize();` des te groter de tekst groter. Maak je kerstwens lekker beeldvullend!
    - Verander de coördinaten in `text()` om de tekst in het midden van je kerstkaart te zetten. Gebruik `height/2` als de y-positie om de tekst automatisch in het midden van het venster te zetten.
    - Pas `fill()` aan om de kleur van de tekst wat meer kerstig te maken. 

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

## **Optionele Stap 6: Laat een belletje klinken bij sneeuwvlokken** 🔔

Wil je een vrolijk belgeluid horen als een sneeuwvlok op de grond valt? Hier is hoe je dat doet!

1. **Download een belgeluid**:
   - Zoek een gratis belgeluid (bijvoorbeeld van [freesound.org](https://freesound.org)) en download het in MP3- of WAV-formaat.
   - Sla het geluidsbestand op op je computer (bijvoorbeeld als `bel.wav`).

2. **Voeg het geluid toe aan je project**:
   - Klik in je P5.js-editor op het pijltje onder de afspeelknop, dus naast 'sketch.js'. Je ziet nu de bestanden van je animatie. Klik op de **+** bovenaan het lijstje en kies voor 'upload file'. Sleep je geluidsbestand naar het venster dat nu opent (of klik erop om een venster te openen waarmee je je bestand kunt zoeken).  

3. **Laad en speel het geluid in je code**:
   - Voeg dit helemaal bovenaan je script toe:
     ```javascript
     let geluid;

     function preload() {
       geluid = loadSound('bel.wav');
     }
     ```

   - Speel het geluid af als een sneeuwvlok uit beeld verdwijnt door `geluid.play()` toe te voegen aan het if-statement dat checkt of een sneeuwvlok de grond raakt: 
     ```javascript
     if (this.posY > windowHeight - 5) {
        geluid.play(); // Speel het belgeluid
     ```

4. **Test je animatie**:
   - Run je code en luister naar het belletje elke keer dat een sneeuwvlok onderaan neervalt. 🎵

5. **Iets minder vaak graag 🙄**
    - Ok dat zijn wel heel veel belletjes. Als je het belletje minder vaak wil horen, gebruik dan de `random()` functie om bijvoorbeeld een kans van 1 op de 20 te hebben dat het geluid te horen is:
        ```javascript
        if (random(20) < 1) {
            geluid.play();
        }
        ```

---

Met deze extra stappen kun je je animatie niet alleen interactief maken, maar ook en geluidseffect toevoegen voor extra kerstmagie. Veel plezier! 🎄


## **Optionele Stap 7: deel je kerstkaart met familie en vrienden! 🥰** 

   Als je een account aanmaakt op [p5js.org](https://editor.p5js.org/signup) dan kun je je schets opslaan en hem aan anderen laten zien.

   - Klik rechtsbovenaan in het scherm van je animatie op 'sign up' om een account aan te maken.
   - Als dat gelukt is, sla dan je animatie op.
   Je kerstkaart krijgt dan een eigen weblink en die kun je naar familie en vrienden sturen!


## **Voeg extra magie toe ✨**
- Maak speciale kerstballen met verschillende vormen.
- Geef sommige sneeuwvlokken de eigenschap (dus met een extra variabele in het object) dat ze *niet* neerslaan op de boom of de tekst. Je kunt op die manier met een if-statement zorgen dat die vlokken voor de boom en de tekst langs zweven.
- Laat de hele tijd een kerstig achtergrondmuziekje spelen.
- Als je nog meer mooie dingen wil maken met P5.js dan kan dat natuurlijk! Zie onze andere [instructie voor P5.js](https://coderdojo-nijmegen.nl/instructies/p5.js-art/).



## Licentie
Deze instructies worden, net als alle andere instructies van CoderDojo Nijmegen, aangeboden onder een [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Licentie](http://creativecommons.org/licenses/by-nc-sa/4.0/).
