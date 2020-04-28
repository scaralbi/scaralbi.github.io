# Paper
Here there are some reviews of papers that I have read and considered interesting.

<ul>
  {% for post in site.papers %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
