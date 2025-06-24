# SMA-IT: Cursus Template
Dit is een voorbeeld van een cursus op GitHub. Deze cursus kan je raadplegen op [https://sma-it.github.io/cursus-template/](https://sma-it.github.io/cursus-template/)

## Een nieuwe cursus maken
1. Maak je github repository (leeg).
2. Maak een lokale clone van je repository
3. Kopiër de inhoud van dit project naar je repository
4. Upload je code
5. Gan naar de Settings van je repository op github
6. Kies voor Pages
7. Bij Build and deployment kies je voor 'deploy' from a branch', en daaronder de main branch.
8. Elke push naar main is nu een build trigger.


## Installatie

Vooreerst heb je [Visual Studio Code](https://code.visualstudio.com/) nodig. Het cursus project kan je openen door rechtsboven op de groene knop 'Clone or download' te klikken. Dan kan je kiezen tussen Visual Studio en GitHub Desktop. Voor dit project is Visual Studio niet echt zinvol. _(Je kan dat wel gebruiken voor de download, maar het maakt het complexer.)_ Wanneer je op GitHub Desktop klikt krijg je ook een optie om dat programma eerst te installeren.

Daarna heb je ook nog Ruby nodig om de site lokaal te kunnen testen. _(De compilatie van de site gebeurt via Ruby)_. Je kan hier de windows installer [downloaden](https://rubyinstaller.org/). Na de installatie verschijnt er nog een console. Klik daar gewoon steeds op enter.

Als je ruby geinstalleerd hebt, kan je VS Code openen. Daarin kies je voor 'open folder', en open je de project folder in je GitHub directory. Eens open, kan je Ctrl+\` typen om de geintegreerde terminal te openen. Die maakt alles veel eenvoudiger, en je kan ook powershell kiezen om het nog iets eenvoudiger te maken. _(Powershell is beter in het terug oproepen van vorige commando's e.d.)_

In de terminal typ je eerst

```ruby --version```

om zeker te zijn dat ruby nu in je path zit.

Vervolgens heb je bundler nodig:
```gem install bundler```
Dan moet je de nodige bundles voor de site installeren. Zorg dat je zeker in de project directory zit en typ
```
bundle install
bundle update
```
De bovenstaande stappen moet je maar een keer uitvoeren. Vanaf nu gaat het min of meer vanzelf. Je kan nu de webserver voor de site openen via:
```bundle exec Jekyll serve```

## Structuur
Alle modules staan in de folder `\modules`. De hoofdstukken voor elke module staan in `\modules\modulenaam\_posts`. Daarin moet elk bestand met een datum beginnen, wat we gebruiken om de volgorde van de hoofdstukken te bepalen.

Afbeeldingen staan in de folder `\img`. Daarin wordt dezelfde structuur als bij de modules gevolgd.

## Wijzigingen
Als je iets aangepast hebt, dan toon VS Code links (3de icon) in het blauw het aantal aangepaste bestanden. Klik daar op en je krijgt een overzicht met al die bestanden en de optie om een commit naar GitHub uit te voeren: Je omschrijft je wijzigingen en kiest commit. Daarna in het dropdown menu Push Changes. Je zal dan je GitHub account ook aan VS Code kenbaar moeten maken en dan worden je wijzigingen naar GitHub gestuurd.

GitHub zal zelf de site terug renderen, maar dat kan wel even minuten duren. Daarom is het handiger om lokaal met ruby en bundler te werken zodat je het resultaat onmiddellijk kan zien.

## Syntax

Een cheatsheet voor Markdown: [link](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet)

### Headers
Headers worden aangegeven met een of meerdere hekjes (`#`), waarbij het aantal voor het niveau staat. Niveau 1 gebruik ik normaal niet, omdat dat nogal groot is.

### Consistentie
Om de opmaak consistent te houden kunnen we de volgende regels volgen:

* Inline code, vermelding van een class, of c# reserved words schrijven we tussen backticks (`\``).
* Menu navigatie maken we duidelijk via pijltjes, cursief: _File -> New -> Project_.
* Bestandsnamen staan in het vet: **Program.cs**.

Daarnaast zijn er ook nog enkele HTML tags voorzien:

```html
<div class="note oefening">
<p>Gebruik dit om een oefening te markeren.</p>
</div>
```

```html
<div class="note protip">
<p>Een tip waarop je de aandacht wil vestigen.</p>
</div>
```

```html
<div class="note waarschuwing">
<p>Een waarschuwing, verschijnt in het rood.</p>
</div>
```
 
---

This course was created using the [Jekyll Course template from P2PU](http://github.com/p2pu/jekyll-course-template).

## Belangrijke bestanden en folders
Als je de template meer wil aanpassen zijn dit de belangrijkste bestanden:

- _data/course.yml: hierin moet je je modules declareren
- img: hierin zet je je afbeeldingen
- modules: hierin staat je cursustekst
- _config.yml: bevat een paar algemene configuratie opties
- index.markdown: de homepage van je site
- README.md: dit bestand, maar geen onderdeel van de cursus