# Blog
Here there is a list of post in chronological order. Some are poems, some are journal entries, some are uncategorised.

<ul class="posts">
  {% for post in site.posts %}
    {% unless post.next %}
    <div class="line"><span>{{ post.date | date: '%Y' }}</span></div>
    {% else %}
      {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
      {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
      {% if year != nyear %}
        <div class="line"><span>{{ post.date | date: '%Y' }}</span></div>
      {% endif %}
    {% endunless %}

    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
