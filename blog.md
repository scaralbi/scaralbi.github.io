---
layout: default
title: Writing
---

<h1>Writing</h1>

<div class="filter-bar">
  <button class="filter-btn active" data-filter="all">All</button>
  <button class="filter-btn" data-filter="poetry">Poetry</button>
  <button class="filter-btn" data-filter="music">Music</button>
  <button class="filter-btn" data-filter="science">Science</button>
</div>

<ul class="post-list" id="post-list">
  {% for post in site.posts %}
    {% assign tag_string = post.tags | join: ' ' | downcase %}
    <li data-tags="{{ tag_string }}">
      <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
      <time class="post-date">{{ post.date | date: "%B %d, %Y" }}</time>
      {% if post.tags %}
        <div class="tags">
          {% for tag in post.tags %}<span class="tag">{{ tag }}</span> {% endfor %}
        </div>
      {% endif %}
    </li>
  {% endfor %}
</ul>

<script>
(function () {
  var CATEGORIES = {
    poetry:  ['poesia', 'poetry', 'narrata', 'ita', 'eng'], music:   ['music', 'jamming', 'piffero', 'dj', 'dj sets'], science: ['science', 'cyanobacteria', 'energy']
  };

  var buttons = document.querySelectorAll('.filter-btn');
  var items   = document.querySelectorAll('#post-list li');

  buttons.forEach(function (btn) {
    btn.addEventListener('click', function () {
      buttons.forEach(function (b) { b.classList.remove('active'); });
      btn.classList.add('active');

      var filter = btn.dataset.filter;

      items.forEach(function (item) {
        if (filter === 'all') { item.style.display = ''; return; }
        var tags  = item.dataset.tags ? item.dataset.tags.split(' ') : [];
        var match = CATEGORIES[filter] && CATEGORIES[filter].some(function (t) {
          return tags.indexOf(t) !== -1;
        });
        item.style.display = match ? '' : 'none';
      });
    });
  });
}());
</script>
