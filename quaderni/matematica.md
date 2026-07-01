---
layout: page
title: Quaderni di Matematica
subtitle: Esplora gli articoli di Algebra, Geometria e Analisi
---

Benvenuto nei Quaderni di Matematica. Seleziona una branca per visualizzare gli approfondimenti dedicati:

## 📐 Geometria
<ul>
  {% for post in site.tags.geometria %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%d/%m/%Y" }}</li>
  {% endfor %}
</ul>

## 🔢 Algebra
<ul>
  {% for post in site.tags.algebra %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%d/%m/%Y" }}</li>
  {% endfor %}
</ul>

## 📊 Analisi e altre branche
<ul>
  {% for post in site.tags.analisi %}
    <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a> - {{ post.date | date: "%d/%m/%Y" }}</li>
  {% endfor %}
</ul>
