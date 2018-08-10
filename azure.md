---
layout: page
title: azure
---

<ul class="post-list">
{% for book in site.azure reversed %}
    <li>
        <h2><a class="post-title" href="{{ book.url | prepend: site.baseurl }}">{{ azure.title }}</a></h2>
        <p class="post-meta">{{ azure.date | date: '%B %-d, %Y' }}</p>
        <p>{{ azure.description }}</p>
      </li>
{% endfor %}
</ul>

<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path }}" class="pagination-item newer">Previous</a>
  {% else %}
    <span class="pagination-item older">Previous</span>
  {% endif %}
  <span class="page_number ">Page: {{ paginator.page }} of {{ paginator.total_pages }}</span>
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path }}" class="pagination-item older">Next</a>
  {% else %}
    <span class="pagination-item newer">Next</span>
  {% endif %}

  
</div>