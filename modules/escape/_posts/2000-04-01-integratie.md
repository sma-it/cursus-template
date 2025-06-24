---
title: Integratie
---

<div class="header1" id="top" markdown="1"># 🧩 Escape Room Project – Les 6: Eerste integratie en verdieping
</div>

<div class="header2" markdown="1">## 🎯 Doelen van deze les
</div>


* De klassen van A en B worden **geïntegreerd in de centrale EscapeRoomManager**.
* Leerling C bouwt de EscapeRoomManager en koppelt:

  * de `Puzzle`-objecten van A (**via polymorfisme**),
  * het `Player`-object van B,
  * en de `Timer` & `Logger` van C zelf.

* **Iedereen werkt actief mee aan het verbeteren van de integratie:**

  * API's en interfaces verduidelijken
  * testscenario’s uitdenken
  * documentatie uitbreiden
  * extra helper-methoden toevoegen

---

<div class="header2" markdown="1">## 📝 **Taken per leerling**
</div>

| Leerling | Hoofdtaken in deze les                                                                                                                                                                                                                                                                 |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **C**    | Bouwt de `EscapeRoomManager` en integreert alle modules.                                                                                                                                                                                                                               |
| **A**    | Ondersteunt **C**. Past eventueel classes en documentatie aan. Levert een lijst met meerdere puzzels. |
| **B**    | Ondersteunt **C**. |


---

<div class="header2" markdown="1">## 📚 **Concrete instructies per leerling**
</div>

### 👤 **Leerling A – puzzles**

**Schrijf een Python-script `create_test_puzzles.py`** in jouw map.

   * Dit script maakt **minstens 3 puzzelobjecten** (bijv. 2 `RiddlePuzzle`, 1 `CodeLockPuzzle`).
   * Zet de puzzels in een **lijst** en geef die terug als variabele of via een functie.


---

### 👤 **Leerling B – users**

Ondersteun leerling C.

### 👤 **Leerling C – core / manager**

1. Begin met een **eenvoudige versie van `EscapeRoomManager`**:

   * Methode `__init__()` die puzzels, speler, timer initialiseert (met de testobjecten van A en B).
   * Methode `start_game()` die in een lus de puzzels toont en invoer simuleert.
   * Methode `show_status()` om de status van timer, speler en puzzels te tonen.

2. Integreer de objecten via **composition**:

   * Manager **bevat** puzzels (lijst van `Puzzle`-objecten), een `Player`, een `Timer`, een `Logger`.
   * Roep methoden aan zonder directe afhankelijkheid van subklassen (gebruik polymorfisme via abstracte klasse/interface).

3. Noteer **zaken die ontbreken of moeilijk zijn in de integratie** en communiceer dit naar A en B.

---

<div class="header2" markdown="1">## 🔍 **Samenwerking**
</div>

* A en B overleggen met C:

  * Is de interface duidelijk?
  * Zijn er methoden of attributen die beter of anders kunnen?
* A en B ondersteunen C door **documentatie aan te vullen** waar nodig:

  * Voeg extra uitleg toe aan docstrings.
  * Werk je `README.md` bij als methoden of klassen zijn uitgebreid.
