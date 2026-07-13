---
layout: page
title: Fisica
subtitle: "Esploriamo le leggi che governano l'universo"
---

<!-- 1. GENERAZIONE AUTOMATICA DEI TAG DI FISICA -->
<div style="margin-bottom: 35px; padding: 15px; background: #f8f9fa; border-left: 4px solid #1f365c; border-radius: 0 6px 6px 0;">
  <span style="font-weight: 700; color: #1f365c; margin-right: 15px; font-size: 0.95rem; text-transform: uppercase; letter-spacing: 0.5px;">
    Sottocategorie:
  </span>
  
  <!-- Cliccando qui si azzera il filtro e si vedono tutti i post di fisica -->
  <button onclick="filtraFisica('all')" class="btn-filtro active" style="margin: 2px 5px; padding: 4px 10px; border: 1px solid #1f365c; background: #1f365c; color: white; border-radius: 4px; font-size: 0.85rem; cursor: pointer; font-weight: 600;">
    Tutti i post
  </button>

  <!-- Script Jekyll per trovare solo i tag presenti nei post di fisica -->
  {% assign post_fisica = site.categories.fisica %}
  {% assign tag_fisica = "" | split: "," %}
  
  {% for post in post_fisica %}
    {% for tag in post.tags %}
      {% unless tag_fisica contains tag %}
        {% assign tag_fisica = tag_fisica | push: tag %}
      {% endunless %}
    {% endfor %}
  {% endfor %}

  {% for tag in tag_fisica %}
  <button onclick="filtraFisica('{{ tag | slugify }}')" class="btn-filtro" style="margin: 2px 5px; padding: 4px 10px; border: 1px solid #1f365c; background: transparent; color: #1f365c; border-radius: 4px; font-size: 0.85rem; cursor: pointer;">
    #{{ tag }}
  </button>
  {% endfor %}
</div>

<!-- 2. ELENCO DEI POST DI FISICA -->
<div class="posts-list">
  {% if post_fisica.size > 0 %}
    {% for post in post_fisica %}
      
      <!-- Creiamo una classe CSS temporanea per ogni tag del post -->
      {% assign tag_classes = "" %}
      {% for tag in post.tags %}
        {% assign tag_slug = tag | slugify %}
        {% assign tag_classes = tag_classes | append: " tag-" | append: tag_slug %}
      {% endfor %}

      <article class="post-preview voce-articolo {{ tag_classes }}" style="margin-bottom: 40px; transition: all 0.3s ease;">
        <a href="{{ post.url | relative_url }}">
          <h2 class="post-title" style="margin-bottom: 5px;">{{ post.title }}</h2>
          {% if post.subtitle %}
            <h3 class="post-subtitle" style="margin-top: 0; color: #666; font-size: 1.1rem;">{{ post.subtitle }}</h3>
          {% endif %}
        </a>
        <p class="post-meta" style="color: #999; font-size: 0.85rem;">Pubblicato il {{ post.date | date: "%d/%m/%Y" }}</p>
        <div class="post-entry">
          {{ post.excerpt | strip_html | truncatewords: 30 }}
          <a href="{{ post.url | relative_url }}" class="post-read-more" style="font-weight: bold;">[Leggi tutto]</a>
        </div>
      </article>
    {% endfor %}
  {% else %}
    <div style="text-align: center; margin: 40px auto; padding: 20px; background: #f8f9fa; border-radius: 6px;">
      <p style="color: #666; font-size: 1.1rem; margin: 0;">
        🔬 Stiamo preparando i primi articoli di Fisica. Il laboratorio è in piena attività!
      </p>
    </div>
  {% endif %}
</div>

<!-- 3. SCRIPT JAVASCRIPT PER IL FILTRAGGIO RAPIDO -->
<script>
function filtraFisica(tag) {
  // Gestione stile dei pulsanti
  const pulsanti = document.querySelectorAll('.btn-filtro');
  pulsanti.forEach(p => {
    p.style.background = 'transparent';
    p.style.color = '#1f365c';
  });
  event.target.style.background = '#1f365c';
  event.target.style.color = 'white';

  // Mostra o nasconde gli articoli in base al tag cliccato
  const articoli = document.querySelectorAll('.voce-articolo');
  articoli.forEach(art => {
    if (tag === 'all') {
      art.style.display = 'block';
    } else {
      if (art.classList.contains('tag-' + tag)) {
        art.style.display = 'block';
      } else {
        art.style.display = 'none';
      }
    }
  });
}
</script>
