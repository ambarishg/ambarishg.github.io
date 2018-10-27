---
layout: page
title: awards
---
These are the awards that I was humbled and honoured to have from [DrivenData](http://www.drivendata.org) and [Kaggle](http://www.kaggle.com)          

<ul class="post-list">
{% for award in site.awards reversed %}
    <li>
        <h2><a class="poem-title" href="{{ award.url | prepend: site.baseurl }}">{{ award.title }}</a></h2>
        <p class="post-meta">{{ award.date | date: '%B %-d, %Y' }}</p>
         <p>{{ award.description }}</p>
      </li>
{% endfor %}
</ul>