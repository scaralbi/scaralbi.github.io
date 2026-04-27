---
layout: default
title: Recipes
permalink: /recipes/
---

<section class="recipes-index">
  <h1>Recipes</h1>
  <p class="recipes-intro">
    Cooking is the other kind of chemistry. Mediterranean by instinct, London by circumstance. Olive oil first, always. These are the things I make.
  </p>

  <div class="recipe-filters" id="recipe-filters">
    <input type="search" id="recipe-search" placeholder="Search recipes…" autocomplete="off">

    <div class="filter-row">
      <span class="filter-label">Quick filters:</span>
      <button class="filter-btn" data-filter="protein-high">≥ 25 g protein</button>
      <button class="filter-btn" data-filter="time-quick">≤ 10 min</button>
      <button class="filter-btn" data-filter="vegetarian">Vegetarian</button>
      <button class="filter-btn" data-filter="italian">Italian</button>
      <button class="filter-btn" data-filter="post-workout">Post-workout</button>
      <button class="filter-btn reset" data-filter="reset">Reset</button>
    </div>

    <div class="filter-row tag-filter-row" id="tag-filter-row">
      <span class="filter-label">Tags:</span>
      <!-- populated by JS -->
    </div>
  </div>

  <p id="recipe-count" class="recipe-count"></p>

  <div class="recipe-grid">
    {% assign sorted = site.recipes | sort: 'title' %}
    {% for recipe in sorted %}
      <a class="recipe-card"
         href="{{ recipe.url | relative_url }}"
         data-tags="{{ recipe.tags | join: ',' }}"
         data-diet="{{ recipe.diet }}"
         data-category="{{ recipe.category }}"
         data-protein="{{ recipe.macros_per_serving.protein_g | default: 0 }}"
         data-kcal="{{ recipe.macros_per_serving.kcal | default: 0 }}"
         data-time-active="{{ recipe.active }}"
         data-title="{{ recipe.title | downcase }}">
        <h3>{{ recipe.title }}</h3>
        {% if recipe.macros_per_serving %}
        <p class="recipe-card-macros">
          <strong>{{ recipe.macros_per_serving.kcal }} kcal</strong> ·
          {{ recipe.macros_per_serving.protein_g }} g protein
          {% if recipe.active %} · {{ recipe.active }}{% endif %}
        </p>
        {% endif %}
        {% if recipe.tags %}
        <p class="recipe-card-tags">
          {% for tag in recipe.tags limit:5 %}<span class="tag">{{ tag }}</span>{% endfor %}
        </p>
        {% endif %}
      </a>
    {% endfor %}
  </div>
</section>

<script>
(function() {
  const cards = Array.from(document.querySelectorAll('.recipe-card'));
  const search = document.getElementById('recipe-search');
  const tagRow = document.getElementById('tag-filter-row');
  const countEl = document.getElementById('recipe-count');

  // Build tag chips from all unique tags
  const allTags = new Set();
  cards.forEach(card => {
    (card.dataset.tags || '').split(',').forEach(t => {
      t = t.trim();
      if (t) allTags.add(t);
    });
  });

  Array.from(allTags).sort().forEach(tag => {
    const btn = document.createElement('button');
    btn.className = 'tag-chip';
    btn.textContent = tag;
    btn.dataset.tag = tag;
    tagRow.appendChild(btn);
  });

  const activeQuickFilters = new Set();
  const activeTags = new Set();
  let searchTerm = '';

  function parseTime(s) {
    if (!s) return Infinity;
    s = s.toLowerCase();
    let mins = 0;
    const h = s.match(/(\d+)\s*h/);
    const m = s.match(/(\d+)\s*min/);
    if (h) mins += parseInt(h[1]) * 60;
    if (m) mins += parseInt(m[1]);
    return mins || Infinity;
  }

  function applyFilters() {
    let visible = 0;
    cards.forEach(card => {
      const tags = (card.dataset.tags || '').split(',').map(t => t.trim());
      const diet = (card.dataset.diet || '').toLowerCase();
      const protein = parseFloat(card.dataset.protein) || 0;
      const time = parseTime(card.dataset.timeActive);
      const title = card.dataset.title || '';

      let show = true;

      if (searchTerm && !title.includes(searchTerm) && !tags.some(t => t.includes(searchTerm))) {
        show = false;
      }

      activeQuickFilters.forEach(f => {
        if (f === 'protein-high' && protein < 25) show = false;
        if (f === 'time-quick' && time > 10) show = false;
        if (f === 'vegetarian' && diet !== 'vegetarian' && diet !== 'vegan') show = false;
        if (f === 'italian' && !tags.includes('italian')) show = false;
        if (f === 'post-workout' && !tags.includes('post-workout')) show = false;
      });

      activeTags.forEach(t => {
        if (!tags.includes(t)) show = false;
      });

      card.style.display = show ? '' : 'none';
      if (show) visible++;
    });
    countEl.textContent = `${visible} ${visible === 1 ? 'recipe' : 'recipes'}`;
  }

  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      const f = btn.dataset.filter;
      if (f === 'reset') {
        activeQuickFilters.clear();
        activeTags.clear();
        searchTerm = '';
        search.value = '';
        document.querySelectorAll('.filter-btn.active, .tag-chip.active').forEach(b => b.classList.remove('active'));
      } else {
        if (activeQuickFilters.has(f)) {
          activeQuickFilters.delete(f);
          btn.classList.remove('active');
        } else {
          activeQuickFilters.add(f);
          btn.classList.add('active');
        }
      }
      applyFilters();
    });
  });

  tagRow.addEventListener('click', e => {
    if (!e.target.classList.contains('tag-chip')) return;
    const t = e.target.dataset.tag;
    if (activeTags.has(t)) {
      activeTags.delete(t);
      e.target.classList.remove('active');
    } else {
      activeTags.add(t);
      e.target.classList.add('active');
    }
    applyFilters();
  });

  search.addEventListener('input', () => {
    searchTerm = search.value.trim().toLowerCase();
    applyFilters();
  });

  applyFilters();
})();
</script>
