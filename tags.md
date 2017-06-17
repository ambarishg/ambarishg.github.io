---
layout: page
title: tags
---

{% for tag in site.tags %}

{% capture tag_name %}{{ tag | first }}{% endcapture %}

<h3>{{ tag_name }} </h3>
   
{% for post in site.tags[tag_name] %}
 * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

{% endfor %}
