---
title: Opstart en Architectuur
---

<div class="header1" id="top" markdown="1"># 📚 Theorie: Hoe bouwen we een goed softwareontwerp?
</div>


In dit project ga je een **escape room software** bouwen. We werken **modulair**: elk van jullie maakt een **deelmodule** die later geïntegreerd wordt in een groter geheel.

Om dit goed te doen, hebben we **duidelijke afspraken** nodig over hoe we de software ontwerpen. We werken daarom met **architectuurprincipes** die ervoor zorgen dat ons programma:

- makkelijk te begrijpen is,
- eenvoudig aanpasbaar is,
- en vlot samenwerkt tussen verschillende onderdelen.

---

<div class="header2" markdown="1">## 3-lagenarchitectuur
</div>


Een **3-lagenarchitectuur** verdeelt een programma in **drie aparte delen** (lagen), elk met een eigen verantwoordelijkheid. Hierdoor wordt je code **duidelijk gestructureerd** en **makkelijker aanpasbaar**.

| Laag               | Rol                                                              | Voorbeeld in de escape room |
|--------------------|------------------------------------------------------------------|-----------------------------|
| **Presentation**   | Verzorgt de interactie met de gebruiker.                        | Console-interface: invoer van antwoorden, tonen van hints. |
| **Logic** | Bevat de kernlogica en spelregels van het programma.             | Puzzels oplossen, hints geven, scores bijhouden. |
| **Data/Support** | Beheert ondersteunende taken zoals data-opslag of timing.        | Timer bijhouden, logging van acties. |

> 🔎 **Waarom?**  
Stel dat je later een grafische interface wilt toevoegen in plaats van een console: met een 3-lagenarchitectuur hoef je **alleen de Presentation-laag aan te passen**, en blijft de logica hetzelfde.

---

<div class="header2" markdown="1">## Objectgeoriënteerd programmeren (OOP)
</div>

Bij **OOP** (objectgeoriënteerd programmeren) ontwerpen we software als **een verzameling van objecten**. Elk object is een instantie van een klasse en heeft:

- **Attributen** (eigenschappen)
- **Methoden** (gedrag)

### ➡️ **Waarom OOP?**
- **Herbruikbaar**: één keer geschreven, meerdere keren gebruikt.
- **Uitbreidbaar**: nieuwe types objecten kan je toevoegen zonder bestaande code te breken.
- **Onderhoudbaar**: duidelijke structuur, makkelijk aanpasbaar.

### 📏 **Belangrijke OOP-principes**

| Principe                  | Betekenis                                                                 | Voorbeeld in ons project |
|---------------------------|---------------------------------------------------------------------------|--------------------------|
| **Single Responsibility** | Elke klasse heeft **één taak** en doet die goed.                          | `Timer` houdt enkel de tijd bij, niet de score. |
| **High Cohesion**          | De onderdelen van een klasse **werken nauw samen** rond die ene taak.     | `Puzzle` heeft alles wat met een puzzel te maken heeft (vraag, oplossing, hints). |
| **Low Coupling**           | Klassen zijn **zo min mogelijk afhankelijk** van elkaar.                  | `Player` weet niets over hoe `Puzzle` werkt, enkel dat er puzzels zijn. |

---
<div class="header2" markdown="1">## Abstracte klassen
</div>

Een **abstracte klasse** is een soort **blauwdruk** voor andere klassen. Ze **bepaalt wat er moet zijn**, maar niet **hoe** het werkt. Je kan geen object maken van een abstracte klasse.

### 🧩 **Voorbeeld:**

```python
from abc import ABC, abstractmethod

class Puzzle(ABC):  # Abstracte klasse

    @abstractmethod
    def check_solution(self, answer: str) -> bool:
        """Controleert of het antwoord juist is."""
        pass

    @abstractmethod
    def get_hint(self) -> str:
        """Geeft een hint voor de puzzel."""
        pass
```

- `Puzzle` **verplicht** alle subclasses om de methodes `check_solution()` en `get_hint()` te implementeren.
- Je kan geen object van `Puzzle` maken, maar wel van klassen die ervan erven (zoals `RiddlePuzzle` of `CodeLockPuzzle`).

### 🔎 **Waarom abstracte klassen gebruiken?**

- Ze zorgen voor **consistentie**: alle soorten puzzels werken op dezelfde manier (hebben dezelfde methodes).
- Ze **beschermen tegen fouten**: je vergeet nooit een belangrijke methode te implementeren.
- Ze helpen bij **low coupling**: andere delen van het programma hoeven enkel te weten dat er een `Puzzle` is, zonder te weten welk type.

---

<div class="header2" markdown="1">## Interfaces in Python
</div>


In sommige talen bestaan **interfaces** als apart concept (bijvoorbeeld in Java). In Python gebruiken we hiervoor meestal **abstracte basisklassen (ABC)**.

Een **interface** is als een **contract**: het zegt welke methodes een klasse **moet hebben**, maar **niet hoe** ze werken.

### 📏 **Voorbeeld:**

```python
class Component(ABC):  # Interface

    @abstractmethod
    def start(self):
        """Start het component."""
        pass

    @abstractmethod
    def stop(self):
        """Stopt het component."""
        pass

    @abstractmethod
    def status(self) -> str:
        """Geeft de status van het component."""
        pass
```

- Elk component dat iets moet kunnen **starten, stoppen en status geven** (zoals een timer of hintensysteem), moet dit **contract** volgen.
- Zo kunnen verschillende onderdelen op **dezelfde manier** aangeroepen worden, wat integratie eenvoudiger maakt.

---

<div class="header2" markdown="1">## 📐 UML-klassendiagrammen ontwerpen met draw.io
</div>

Een klassendiagram is een visuele voorstelling van de structuur van je code: welke klassen er zijn, welke attributen en methoden ze hebben, en hoe ze met elkaar verbonden zijn. Het helpt je nadenken over het ontwerp vóór je begint te coderen.

We gebruiken draw.io (diagrams.net) om je diagrammen te tekenen. Deze tool kan je rechtstreeks aan GitHub koppelen, zodat je je diagrammen veilig in de repository bewaart.

<div class="header1" id="top" markdown="1"># 🔧 Keuze: wie werkt aan welk onderdeel?
</div>


Jullie kiezen **één module per persoon**. Alle modules bevatten **abstracte klassen of interfaces**, zodat iedereen deze concepten toepast:

| Module              | Abstracte klasse / Interface  | Concrete klassen (voorbeelden)          | Rol                                                                 |
|---------------------|-------------------------------|------------------------------------------|---------------------------------------------------------------------|
| **A: Puzzelsysteem** | `Puzzle` (abstract)           | `RiddlePuzzle`, `CodeLockPuzzle`         | Beheert de puzzels die spelers moeten oplossen.                     |
| **B: Gebruikersbeheer** | `User` (abstract)              | `Player`, `Admin`                        | Beheert gebruikers: registratie, voortgang, rollen.                 |
| **C: Kerncomponenten** | `Component` (interface)       | `Timer`, `Logger`, `HintSystem`          | Algemene onderdelen die het spel ondersteunen: tijd, logs, hints.   |

---

<div class="header1" id="top" markdown="1"># 🛠️ Opdracht voor vandaag
</div>

<div class="header2" markdown="1">## Stap 1: Kies je module
</div>

Bespreek met je klasgenoten wie welke module uitwerkt.

---

<div class="header2" markdown="1">## Stap 2: Repository op GitHub opzetten
</div>

1. **Repository aanmaken** (gebeurt door de leerkracht of een van jullie).
2. Iedereen maakt **een eigen branch** aan:
   - `feature/puzzles` (A)
   - `feature/users` (B)
   - `feature/core-components` (C)

---

<div class="header2" markdown="1">## Stap 3: Ontwerp je klassendiagram
</div>

### 🔗 **Repository structuur en koppeling met draw.io**

1. **Maak een map in de repository** die **exact dezelfde naam** heeft als jouw branch:
   - `puzzles` voor leerling A
   - `users` voor leerling B
   - `core` voor leerling C

2. **Open draw.io** en kies voor **"Device"** als opslaglocatie.
3. Zodra je je diagram af hebt, sla je het bestand op als:
   - `klassendiagram.drawio` in jouw map (`puzzles/`, `users/`, `core/`).
4. **Koppel draw.io aan GitHub**:
   - Via *File > Save As > GitHub*, meld je aan met je account en sla je het bestand direct in de juiste map op je branch op.

---

### 🛠️ **Wat moet er in jouw klassendiagram staan?**

Iedereen ontwerpt een **abstracte klasse of interface** én minstens **twee concrete klassen** die hiervan erven. Elk klassendiagram bevat:

- De **naam van de klasse** bovenaan.
- **Attributen** (eigenschappen) in het midden.
- **Methoden** (gedragingen) onderaan, met **argumenten en returntypes**.
- **Relaties**:
  - **Erfenis**: een pijl met een witte driehoek (subklasse erft van een superklasse).
  - **Associaties** (indien nodig): een lijn tussen klassen (bijvoorbeeld: een speler **heeft** puzzels).

---

<div class="header2" markdown="1">## Stap 3: Ontwerp je klassendiagram
</div>

### 📏 **Specifieke opdrachten per leerling**

#### 👤 **Leerling A – Module `puzzles`**

**Abstracte klasse**: `Puzzle`

**Concrete klassen**: `RidldlePuzzle` en `CodeLockPuzzle`

**Stap-voor-stap hulp**:
- Vraag jezelf af: **Wat heeft elke puzzel sowieso nodig?**
  - Een vraag, een juiste oplossing, misschien meerdere hints.
- Wat is specifiek aan een raadseltje? Wat is specifiek aan een codekluisje?

---

#### 👤 **Leerling B – Module `users`**

**Abstracte klasse**: `User`

**Concrete klassen**: `Player` en `Admin`

**Stap-voor-stap hulp**:
- Denk na over: **Wat doet een gebruiker sowieso?**
  - Naam opslaan, informatie tonen, rol aangeven.
- Wat is anders bij een speler tegenover een admin? Een speler moet weten hoeveel hints hij gebruikte en hoeveel puzzels hij oploste. Een admin moet het spel kunnen resetten.


#### 👤 **Leerling C – Module `core`**

**Interface (abstracte klasse)**: `Component`

**Concrete klassen**: `Timer` en `Logger`

**Stap-voor-stap hulp**:
- **Wat betekent het om een component te starten/stoppen?**
  - Voor een timer: begint de tijd te lopen. Moet weten hoeveel tijd er nog rest.
  - Voor een logger: begint of stopt met loggen. Je moet een bericht kunnen toevoegen.

### 💡 **Tips voor het bepalen van methoden en attributen:**

1. **Vraag jezelf af**:
   - Wat **moet** elke klasse kunnen doen?
   - Welke **informatie** moet elke klasse bijhouden?

2. **Gebruik beschrijvende namen**:
   - Methoden: altijd een werkwoord + beschrijving (bv. `check_solution`, `display_info`).
   - Attributen: zelfstandig naamwoord (bv. `name`, `time_remaining`).

3. **Bepaal de types**:
   - Gebruik types zoals `str`, `int`, `bool`, `None`, `List[str]`, enzovoort.


<div class="header2" markdown="1">## Stap 4: Documenteer je module
</div>

3. Schrijf een **`README.md`** in jouw modulemap met:
   - Een korte uitleg over **wat jouw module doet**.
   - Wat je abstracte klasse/interface **beschrijft**.


