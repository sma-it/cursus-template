---
title: Implementatie
---

<div class="header1" id="top" markdown="1"># 🎯 Doel van deze fase
</div>

- Je implementeert eerst jouw **abstracte klasse** of **interface**.
- Daarna werk je je **concrete klassen** uit die hiervan erven.
- Je zorgt voor **duidelijke documentatie (docstrings)**, zodat de andere leden van het team jouw code kunnen begrijpen en gebruiken.
- Je maakt **unit tests** voor elke klasse, zodat je zeker weet dat je onderdelen correct werken.

---

<div class="header1" id="top" markdown="1"># 📚 Implementeer je abstracte klasse of interface
</div>


<div class="header2" markdown="1">## ➡️ Wat moet je doen?
</div>

1. Maak een Python-bestand aan in je eigen map (`puzzles/`, `users/`, of `core/`).
2. Implementeer de abstracte klasse of interface met behulp van de `abc` module.
3. Voeg een **duidelijke docstring** toe bovenaan je klasse. 

> 🔎 **Waarom beginnen met de abstracte klasse?**
- Zo **definieer je het contract** waar de concrete klassen zich aan moeten houden.
- Het helpt het team te begrijpen **welke methodes verplicht zijn**.

<div class="header2" markdown="1">## 📏 Voorbeeld: Abstracte klasse met docstring
</div>


```python
from abc import ABC, abstractmethod

class Animal(ABC):
    """
    Abstracte klasse die de basisdefinitie geeft voor alle dieren.

    Verplichte methoden:
    - make_sound(): moet het geluid van het dier teruggeven.
    - move(): moet beschrijven hoe het dier zich verplaatst.
    """

    @abstractmethod
    def make_sound(self) -> str:
        """Geeft het geluid van het dier terug."""
        pass

    @abstractmethod
    def move(self) -> str:
        """Geeft terug hoe het dier zich verplaatst."""
        pass
```

<div class="header2" markdown="1">## 🔎 Docstrings tips
</div>

- **Samenvattende uitleg** bovenaan de klasse.
- Geef aan:
  - Wat de klasse doet.
  - Wat de **verplichte methoden** zijn.
- Bij methoden: beschrijf **wat de methode doet**, wat de **input** en **output** is.

---

<div class="header1" id="top" markdown="1"># 📚 Implementeer je concrete klassen
</div>


1. Maak per concrete klasse een nieuw Python-bestand aan in je map.
2. Laat de concrete klasse **erven van de abstracte klasse of interface**.
3. Implementeer alle **verplichte methoden**.
4. Voeg opnieuw **docstrings** toe aan de klasse en methoden.

<div class="header2" markdown="1">## 📏 Voorbeeld: Concrete klasse met docstrings
</div>


```python
class Dog(Animal):
    """
    Concrete klasse die een hond voorstelt.

    Inherits:
        Animal: Abstracte klasse.

    Methoden:
    - make_sound(): geeft het geluid 'Bark!' terug.
    - move(): beschrijft dat de hond loopt.
    """

    def make_sound(self) -> str:
        """Geeft het geluid van een hond terug."""
        return "Bark!"

    def move(self) -> str:
        """Geeft terug dat de hond loopt."""
        return "The dog walks."
```

---


<div class="header1" id="top" markdown="1"># 📚 Unit tests schrijven
</div>


Een **unit test** controleert of een klein onderdeel (bijvoorbeeld een klasse of methode) **correct werkt**.

<div class="header2" markdown="1">## ➡️ Waarom?
</div>

- Fouten worden sneller ontdekt.
- Als je later iets verandert, controleer je met de tests of alles nog werkt.

<div class="header2" markdown="1">## ➡️ Hoe schrijf je een unit test
</div>

Alle uitleg over unit tests vind je in het hoofdstuk daarover, bij basics.


---

<div class="header1" id="top" markdown="1"># 📚 Toepassing op je project
</div>


<div class="header2" markdown="1">## 👤 Leerling A – Module `puzzles`
</div>

- **Abstracte klasse**: `Puzzle`
- **Concrete klassen**:
  - `RiddlePuzzle`: implementeer `check_solution()` en `get_hint()`.
  - `CodeLockPuzzle`: idem.

**Unit tests**:
- Controleer of de methodes correct werken:
  - Geeft `check_solution("antwoord")` het juiste resultaat?
  - Komt `get_hint()` terug met de verwachte string?

---

<div class="header2" markdown="1">## 👤 Leerling A – Module `users`
</div>

- **Abstracte klasse**: `User`
- **Concrete klassen**:
  - `Player`
  - `Admin`

**Unit tests**:
- Controleer of:
  - `get_role()` de juiste rol teruggeeft.
  - `display_info()` de juiste informatie toont.

---

<div class="header2" markdown="1">## 👤 Leerling A – Module `core`
</div>

- **Interface**: `Component`
- **Concrete klassen**:
  - `Timer`
  - `Logger`

**Unit tests**:
- Test of:
  - `start()` en `stop()` de status van het component aanpassen.
  - `status()` de verwachte output geeft.

