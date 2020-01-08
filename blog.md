# Blog
Here there is a list of post in chronological order. Some are poems, some are journal entries, some are uncategorised.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
