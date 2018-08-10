---
layout: azure
title: azure
---

<ul class="post-list">
{% for book in site.azure reversed %}
    <li>
        <h2><a class="poem-title" href="{{ book.url | prepend: site.baseurl }}">{{ book.title }}</a></h2>
        <p class="post-meta">{{ book.date | date: '%B %-d, %Y' }}</p>
        <p>{{ book.description }}</p>
      </li>
{% endfor %}
</ul>


