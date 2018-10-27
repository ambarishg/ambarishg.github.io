---
layout: page
title: books
---

<ul class="post-list">
{% for book in site.books reversed %}
    <li>
        <h2><a class="poem-title" href="{{ book.url | prepend: site.baseurl }}">{{ book.title }}</a></h2>
        <p class="post-meta">{{ book.date | date: '%B %-d, %Y' }}</p>
        <p>{{ book.description }}</p>
      </li>
{% endfor %}
</ul>

<p>
Please provide any feedback through <a href="https://goo.gl/forms/xeLYuyVmLESJHx2q2">Little Books Feedback</a>
</p>
