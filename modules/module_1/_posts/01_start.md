---
title: Start
---

<div class="header1" id="top" markdown = "1"># Titel op niveau 1
</div>

<div class="header2" markdown = "1">## Titel op niveau 2
</div>

De markdown syntax ga ik hier niet herhalen. Wel enkele pointers:

1. Je kan naar images in de img folder refereren op deze manier:

![image]({{ site.baseurl }}/img/cc-icons.png)

2. Je hoeft geen div rond een titel te zetten, maar zo zien ze er net iets mooier uit.

3. Je kan code invoegen in zowat elke syntax:

```python
print("Hello, hello")
```

4. Je kan custom css toevoegen. Dit zijn een paar voorbeelden. De css staat in _sass/_common.scss

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