---
layout: page
title : categories
---

{% for category in site.categories %}

{% capture category_name %}{{ category | first }}{% endcapture %}

<h3>{{ category_name }} </h3>
   
{% for post in site.categories[category_name] %}
 * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

{% endfor %}
