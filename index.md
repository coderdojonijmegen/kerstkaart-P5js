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
    Je kunt ook de nummers vervangen door `windowWidth` en `windowHeight`, dan past het altijd, dus ook als je het venster later groter maakt.
    - Je hele script ziet er dan zo uit:
      ```javascript
      function setup() {
        createCanvas(windowWidth, windowHeight);
        background(0);
      }

      function draw() {
      }
      ```
    - Klik op de afspeelknop om te kijken of het goed werkt.

3. **Begin met een kerstboom tekenen**:
   - Een kerstboom heeft een stam en groene takken.
   - Voor de stam kunnen we een rechthoek tekenen met de functie `rect()`. Zet deze code in het script, ná `background()` en boven de gekrulde haak `}` die `setup()` afsluit:
      ```javascript
      rect(90, 100, 20, 20); // x, y, breedte, hoogte
      ```
    - De takken kun je tekenen met een driehoek. Gebruik daarvoor `triangle()`:
      ```javascript
      triangle( 60,100, 100,10, 140,100 ); // links, top, rechts
      ```

4. **Run je code**! Zie je een kerstboom? Goed gedaan! 🎉

---

### Uitleg van coördinaten in P5.js 🖼️

Zoals je ziet gebruikt P5.js een **coördinatenstelsel** om vormen te tekenen op een bepaalde plek op het scherm. Dit zijn de belangrijkste punten om te begrijpen:

- Coördinaten worden weergegeven als `(x, y)`. `x` is de horizontale positie,`y` de verticale positie.
- Het **linkerbovenhoekpunt** van het venster is het beginpunt. De coördinaten van dit punt zijn `0,0`.
- **x** betekent 'zoveel pixels vanaf de linkerkant'. Hoe groter het getal voor x, des te verder naar rechts het is.
- **y** betekent 'zoveel pixels vanaf de bovenkant'. Hoe groter het getal voor y, des te verder naar beneden het is.

Als je deze `print()` toevoegt aan `draw()` dan zie je linksonderin de coördinaten van je muis als je die over je animatie beweegt:
```javascript
print("x:", mouseX, "  y:", mouseY);
```

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
   - Op de website <a href="https://rgbcolorpicker.com/" target="_blank">rgbcolorpicker.com</a> kun je gemakkelijk kleuren uitkiezen. Als je een Mac hebt, kun je de app Color Picker gebruiken.

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

3. **Goudkleurige rand? 🌟**

    Als je de kerstballen een goudkleurige rand wil geven, vervang `noStroke()' dan door:
    ```javascript
    stroke(190,166,40);
    strokeWeight(3);
    ```

---

## Stap 4: Voeg een kerstwens toe! 🎁
Een kerstkaart is niet compleet zonder een kerstwens!

1. **Gebruik de `text()` functie:**
   - Voeg dit toe aan de `setup()` functie, **ná het tekenen van je kerstboom**:
     ```javascript
     noStroke();                    // geen rand
     textSize(30);                  // grootte van de letters
     fill(246, 246, 255);           // tekstkleur
     text("Fijne kerst!", 50, 50);  // Tekst en positie
     ```
    - (Als je deze regels bóven de `rect()`en `triangle()` zou zetten dan zou de kerstboom over je tekst heen kunnen vallen.)

2. **Run je code**:
   - Zie je de tekst bovenaan? 🎉

3. **Maak de tekst groot en kleurig**
    - Hoe groter het getal in `textSize();` des te groter de tekst groter. Maak je kerstwens lekker beeldvullend!
    - Verander de coördinaten in `text()` om de tekst in het midden van je kerstkaart te zetten. Gebruik `height/2` als de y-positie om de tekst automatisch in het midden van het venster te zetten.
    - Pas `fill()` aan om de kleur van de tekst wat meer kerstig te maken.

4. **Kies je eigen lettertype! ✍🏼 𝒦ℰℛ𝒮𝒯**

    - Je kunt een eigen lettertype gebruiken, maar daarvoor heb je wel een account nodig op [p5js.org](https://editor.p5js.org/signup). Klik rechtsbovenaan je script op 'sign up'. Als je daar nu geen zin in hebt, ga dan hieronder verder met de stap 'Laat het sneeuwen'.

    - Zoek een leuk lettertype, bijvoorbeeld op [1001fonts.com](https://www.1001fonts.com/). 
    - Als je er één gevonden hebt die je leuk lijkt, klik dan op 'download' en sla hem op op je computer.
    - Waarschijnlijk komt het lettertype binnen als een zip-bestand en moet je het eerst uitpakken. Vraag één van de mentoren om hulp als dat niet lukt of als je niet weet hoe dat moet.

5. **Voeg het lettertype toe aan je project**:
   - Klik in je P5.js-editor op het pijltje `>` onder de afspeelknop, dus naast 'sketch.js'. Je ziet nu de bestanden van je animatie. 
   - Klik op de **+** bovenaan het lijstje en kies voor 'upload file'. 
   - Sleep je lettertype-bestand naar het venster dat nu opent (of klik op het venster om het bestand op te zoeken).
   - Je ziet nu in het rijtje links het toegevoegde bestand. Klik er één keer op. Je kunt nu bovenaan de hele bestandsnaam selecteren en kopiëren (de naam eindigt op `.ttf` of `.otf`).

6. **Laad en gebruik het lettertype in je code**:
   - Ga terug naar je script door te klikken op 'sketch.js'.
   - Nu gaan we eerst je letterype laden. Neem deze code over, helemaal bovenaan in je script en plak de naam van het lettertype in de functie `loadFont()`. Het zou er zo uit moeten zien:
      ```javascript
      let font = 'BerkshireSwash-Regular.ttf';
      function preload() {
        font = loadFont(font);
      }
      ```
    - Nu het lettertype geladen is kun je P5.js laten weten dat je dat lettertype wil gebruiken voor je kerstwens. Zet dit commando in `setup()`, boven de regel met `text()` van daarstraks:
      ```javascript
      textFont(font); 
      ```
7. **Bewonder het resultaat 📝 😍**

---

## Stap 5: Laat het sneeuwen! ❄️❄️❄️

Nu wordt het pas echt interessant. We gaan het laten sneeuwen, en daarvoor gaan we **objecten** gebruiken.

Het helpt als je een beetje de ruimte hebt om te programmeren, dus klik op **∨** naast 'clear' om het console-venster weg te klikken, en schuif het preview-venster wat verder naar rechts.


1. **Wat is een object? 🛠️** 

    - Objecten zijn een manier om variabelen en functies bij elkaar te houden die bij één onderdeel in je programma horen. (In ons geval is dat een sneeuwvlok.)

2. **Waarom gebruiken we objecten?**

    Een rondje tekenen is in P5.js heel makkelijk. Dat zag je net al bij de kerstballen. Om zo'n rondje als een sneeuwvlok naar beneden te laten gaan heeft hij een paar dingen nodig:
    - **eigenschappen**: Waar is de vlok? Hoe groot is hij?
    - **gedrag**: Wat kan de vlok doen? (Bijvoorbeeld vallen.)

    We kunnen variabelen maken om de x- en y-positie van dat rondje te onthouden en die positie elke keer dat `draw()` wordt uitgevoerd een klein beetje veranderen. Op die manier kunnen we rondjes naar beneden laten vallen.

    Dat is best eenvoudig, maar het wordt veel ingewikkelder als we een flinke sneeuwbui willen. Dan hebben we een **paar honderd sneeuwvlokken** nodig die allemaal een eigen positie, grootte en snelheid hebben. Daarvoor hebben we ook honderden variabelen nodig en die willen we niet één voor één klaarzetten want dat is veel te veel werk.

    Daarom gaan we voor elke sneeuwvlok een apart object maken, zodat elke sneeuwvlok zelf kan onthouden waar hij is en weet waar hij heen moet.


3. **Maak een sjabloon voor je objecten**

    - Een `class` is een soort **sjabloon**, in ons geval van hoe een sneeuwvlok eruitziet. We hoeven het sjabloon maar één keer te maken en dan kunnen we op basis daarvan heel veel objecten maken die hetzelfde zijn.

    - We noemen onze class 'Sneeuwvlok'. Zet hem helemaal onderaan in je script, dus ná de gekrulde haak van `mousePressed`:

      ```javascript
      class Sneeuwvlok {

        constructor() {
          this.startX = random(windowWidth);
          this.posX = this.startX;
          this.posY = 0;
          this.grootte = random(1, 5);
          this.valsnelheid = random(1, 5);
        }

      }
      ```
    - De `constructor` is een functie die alleen uitgevoerd wordt als een nieuw object wordt aangemaakt op basis van deze `class`.
    - In deze constructor zetten we variabelen klaar (in een `class` heten dat **attributen**). Dit zijn ze:
      - `startX` voor de startpositie; elke sneeuwvlok begint op een andere willekeurige horizontale plek tussen 0 en de breedte van het venster.
      - `posX` is steeds de horizontale positie. We kunnen straks de sneeuwvlok laten dwarrelen, maar hij begint op de startpositie.
      - `posY` is de verticale positie en die begint bovenaan, dus op 0.
      - `grootte` onthoud hoe groot deze sneeuwvlok is, en dat kan verschillen tussen 1 en 5 pixels breed.
      - `valsnelheid` wisselt ook tussen de 1 en 5 pixels, zodat de sneeuwvlokken niet allemaal even snel vallen.
    - `this.` voor elke variabele betekent 'we bedoelen de variabele van **dit** object'. We hebben tenslotte een heleboel sneeuwvlokken uit elkaar te houden!
    
4. **Geef de class functies**

    - Nu we attributen hebben gedefiniëerd voor onze sneeuwvlokken, gaan we functies toevoegen. Functies in een `class` worden **methoden** genoemd. 
    - Met de methoden zorgen we dat de sneeuwvlokken ook iets kunnen doén, namelijk vallen. 😆
    - Zet de methoden `verplaats()` en `teken()` in de class, direct onder de gekrulde haak die de constructor afsluit:
      ```javascript
      verplaats() {
        this.posY += this.valsnelheid;
        this.posX += random(-2, 2);
      }

      teken() {
        fill(255);
        noStroke();
        circle(this.posX, this.posY, this.grootte);
      }
      ```
    - Elke keer dat `verplaats()` wordt aangeroepen, wordt de y-positie groter met het aantal in `this.valsnelheid`.
    - We verplaatsen `posX` twee pixels naar links of naar rechts om de sneeuw een beetje te laten dwarrelen.  
    - Elke keer dat `teken()` wordt aangeroepen, wordt een witte cirkel (zonder rand) getekend op de positie `posX,posY` met de opgegeven grootte. 

5. **Maak objecten op basis van de class**

    - Helemaal bovenaan in je script zetten we een lijst klaar waar we nieuwe objecten aan toe kunnen voegen:
      ```javascript
      let sneeuwvlokken = [];
      ```
    - Nu kun je in `draw()` steeds opnieuw een nieuwe sneeuwvlok toevoegen aan de lijst:
      ```javascript
      sneeuwvlokken.push(new Sneeuwvlok());
      ```

6. **Laat maar komen die sneeuwstorm!** ☃️
    - Om je sneeuwvlokken allemaal te laten zien, moeten we ze in `draw()` steeds opnieuw verplaatsen en tekenen. Dat doen we door met een for-loop alle objecten in de lijst af te gaan en de methoden van elk object aan te roepen:
      ```javascript
      for (var s in sneeuwvlokken) {

        sneeuwvlokken[s].verplaats();
        sneeuwvlokken[s].teken();

      }
      ```
    - Run je code maar eens!
    - Hé, maar nu zie je alleen maar strepen! Meer een soort natte sneeuw 😧 Dat kun je fiksen door bovenaan in `draw()` steeds opnieuw een nieuwe achtergrond te tekenen voordat je de sneeuwvlokken tekent:
      ```javascript
      background(0);
      ```
    - Run je code opnieuw! Mooier zo?
    - Hoe kun je het harder laten sneeuwen? Er is een makkelijke manier om twee keer zo vaak een sneeuwvlok te maken...
    
7. **Sneeuw combineren met de rest van de kerstkaart ☃️**
    - Nu hebben we er wel een probleem bij: de rest van de kerstkaart is verdwenen. Dat komt doordat we nu in `draw()` steeds de achtergrond opnieuw tekenen en alles dat we daarvoor getekend hebben uitwissen.
    - We gaan dat probleem oplossen door een plaatje te bewaren van onze kerstkaart, en die steeds opnieuw te tekenen vóórdat we de sneeuwvlokken tekenen.
    - Maak een variabele aan om het plaatje op op te slaan, helemaal bovenaan je script:
      ```javascript
      let kerstwens;
      ```

      In `setup()`, ná het tekenen van de kerstboom en kerstwens:
      ```javascript
      kerstwens = createGraphics(width, height);
      kerstwens.image(get(), 0, 0);
      ```
    - En in `draw()` laat je steeds opnieuw dat plaatje zien:
      ```javascript
      image(kerstwens, 0, 0);
      ```
    - Probeer het maar, als het goed is dan zie je nu de sneeuw over je kerstkaart heen!
    - De kerstballen zijn nog steeds niet te zien, omdat die niet bestonden toen we het plaatje van je kerstkaart maakten. Dat kun je oplossen door ze aan dat plaatje toe te voegen. Dat doe je door `kerstwens.` voor de functies te zetten:
      ```javascript
        kerstwens.fill(r, g, b);
        kerstwens.stroke(190, 166, 40);
        kerstwens.strokeWeight(3);
        kerstwens.ellipse(mouseX, mouseY, size);
      ```

8. **Waarom sneeuwt het steeds langzamer?**

    - Je ziet dat de animatie al gauw heel traag wordt. Dat komt doordat er in hoog tempo sneeuwvlokjes bij komen, ongeveer 60 per seconde (zo vaak wordt `draw()` uitgevoerd). 
    - De lijst waar al die objecten in wordt bijgehouden, de variabele `sneeuwvlokken`, wordt dus ook steeds langer.
    - De oplossing voor dit probleem is een **if-statement**. Daarmee kun je P5.js een vraag laten stellen. In dit geval is die vraag: is een sneeuwvlok al verder naar beneden gevallen dan de hoogte van mijn scherm? Als het antwoord *ja* is dan halen we dat object uit de `sneeuwvlokken`-lijst.
    - We doen dat in een nieuwe methode `sneeuwruimen()` in de class `Sneeuwvlok`:
      ```javascript
      sneeuwruimen(s) {

        if (this.posY > windowHeight) {

          sneeuwvlokken.splice(s, 1);
          
        }

      }
      ```
    - Je ziet dat we het juiste object uit de lijst kunnen halen omdat we met de variabele `s` doorgeven welk nummer dit object in de lijst heeft.
    - Nu hoef je alleen nog in `draw()` deze nieuwe methode aan te roepen, direct na de regel met `teken()`:
      ```javascript
      sneeuwvlokken[s].sneeuwruimen(s);
      ```
    - Werkt de animatie nu soepeler?


## Stap 6: Mooiere sneeuw! 🌨️

1. **Sneeuw hoort te dwarrelen, toch?** 

    - We laten de sneeuw nu een klein beetje dwarrelen met de `random`-functie, maar het ziet er veel mooier uit als je `noise()` gebruikt.
    - Voeg dit toe aan de constructor:
      ```javascript
      this.xoff = random(3000);
      ```
    - In `verplaats()`:
      ```javascript
      this.posX += random(-2, 2); // deze regel haal je weg
      this.posX = this.startX + map(noise(this.xoff), 0, 1, -250, 250);
      this.xoff += 0.002;
      ```
    - Je kunt de sneeuw wilder laten dwarrelen met een hogere waarde in de laatste regel, bijvoorbeeld 0.008.
    - Als je meer wil weten over hoe `noise()` werkt, kijk dan [deze video over Perlin noise](https://www.youtube.com/watch?v=Qf4dIN99e2w) van Daniel Shiffman (in het Engels, maar je kunt de automatische vertaling en ondertitels aanzetten). Je kunt ook de voorbeelden op [p5js.org](https://p5js.org/reference/p5/noise/) bekijken.

2. **De sneeuw laten liggen** ☃️

    - Eigenlijk heb je pas echt iets aan sneeuw als het lekker blijft liggen. Laten we het zo maken dat onze sneeuwvlokken blijven liggen als een dik pak sneeuw op de boom, de letters en de grond!
    - Om te beginnen maken we een plaatje aan alleen voor het paksneeuw. Daarvoor maken een variabele aan, helemaal bovenaan ons script:
      ```javascript
      let paksneeuw;
      ```
    - In `setup()` vertellen we P5.js dat `paksneeuw` een plaatje moet worden met dezelfde afmetingen als ons venster:
      ```javascript
      paksneeuw = createGraphics(width, height);
      ```
    - Dat plaatje gaan we in `draw()` elke keer laten zien, nádat we het plaatje met de boom en de kerstwens hebben neergezet:
      ```javascript
        image(kerstwens, 0, 0); // deze staat er dus al
        image(paksneeuw, 0, 0); // deze komt er nu bij
      ```
    - In de functie `sneeuwruimen()` kijken wanneer een sneeuwvlok de boom of de tekst raakt. Dat plaatje gaan we in `draw()` elke keer laten zien, nádat we het plaatje met de boom en de kerstwens hebben neergezet:
      ```javascript
        image(kerstwens, 0, 0); // deze staat er dus al
        image(paksneeuw, 0, 0); // deze komt er nu bij
      ```



  


---

Gefeliciteerd! Je hebt een eigen kerstkaart-animatie gemaakt! 🎄✨

Hier zijn een paar optionele stappen die je kunt volgen om je kerstanimatie nog specialer te maken, en hem te delen met je familie en vrienden om de kerstvreugde te verspreiden! 🎁

---

## Optionele Stap 7: deel je kerstkaart met familie en vrienden! 🥰

   Als je een account aanmaakt op [p5js.org](https://editor.p5js.org/signup) dan kun je je schets opslaan en hem aan anderen laten zien.

   - Klik rechtsbovenaan in het scherm van je animatie op 'sign up' om een account aan te maken.
   - Als dat gelukt is, sla dan je animatie op.
   Je kerstkaart krijgt dan een eigen weblink en die kun je naar familie en vrienden sturen!
   - Eventueel kun je je hele project ook kopiëren naar [Openprocessing.org](https://openprocessing.org/). Daar opent je kerstkaart zich beeldvullend en ook daar krijg je een weblink als je een account aanmaakt.
   - Voeg een extra kerstwens toe ('Groeten van ..').

## Optionele Stap 8: Laat een belletje klinken bij sneeuwvlokken 🔔

Wil je een vrolijk belgeluid horen als een sneeuwvlok op de grond valt? Hier is hoe je dat doet!

(Je hebt hiervoor een account nodig op [p5js.org](https://editor.p5js.org/signup). Klik rechtsbovenaan je script op 'sign up' als je niet al ingelogd bent. Sla anders deze stap over.)

1. **Download een belgeluid**:
   - Zoek online een gratis belgeluid (bijvoorbeeld op [bigsoundbank.com](https://bigsoundbank.com/)). Het werkt het best als het een heel kort geluidje is.
   - Download het in MP3- of WAV-formaat.
   - Sla het geluidsbestand op op je computer (bijvoorbeeld als `bel.wav`).

2. **Voeg het geluid toe aan je project**:
   - Klik in je P5.js-editor op het pijltje onder de afspeelknop, dus naast 'sketch.js'. Je ziet nu de bestanden van je animatie. Klik op de **+** bovenaan het lijstje en kies voor 'upload file'. Sleep je geluidsbestand naar het venster dat nu opent (of klik erop om een venster te openen waarmee je je bestand kunt zoeken).  

3. **Laad en speel het geluid in je code**:
   - Maak een variabele klaar om je geluid in op te slaan, helemaal bovenaan je script:
        ```javascript
     let geluid;
     ```

    - In de preload-functie zet je het geluid alvast klaar zodat het later afgespeeld kan worden. (`preload()` heb je waarschijnlijk al gedaan voor het lettertypes.)
      ```javascript
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

## Optionele stap 9: Laat het aantal objecten zien
  - Als je het leuk vindt om te weten hoeveel sneeuwvlokken er steeds in beeld zijn, kun je als tekst laten zien hoeveel objecten er in de lijst met sneeuwvlokken staan. Zet deze code onderaan in `draw()`: 
    ```javascript
    textFont('Arial', 13);
    text(sneeuwvlokken.length + " sneeuwvlokken ", width - 5, 5);
    ```
  - Met een extra variabele kun je ook nog laten zien hoeveel sneeuwvlokken er in totaal zijn gevallen.

## **Nog meer magie! ✨**
- Laat een tekstje 'klik op mij' zien op de kerstboom zolang er nog niet geklikt is voor de kerstballen. Dit kun je doen met een extra variabele en een if-statement.
- Laat de sneeuw ook pas vallen als er geklikt is.
- Maak speciale kerstballen met verschillende vormen.
- Geef sommige sneeuwvlokken de eigenschap (dus met een extra variabele in het object) dat ze *niet* neerslaan op de boom of de tekst. Je kunt met een if-statement zorgen dat die vlokken voor de boom en de tekst langs zweven.
- Laat de hele tijd een kerstig achtergrondmuziekje spelen.
- Als je nog meer mooie dingen wil maken met P5.js dan kan dat natuurlijk! Zie onze andere [instructie voor P5.js](https://coderdojo-nijmegen.nl/instructies/p5.js-art/).



## Licentie
Deze instructies worden, net als alle andere instructies van CoderDojo Nijmegen, aangeboden onder een [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International Licentie](http://creativecommons.org/licenses/by-nc-sa/4.0/).
