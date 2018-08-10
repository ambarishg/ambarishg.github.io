---
layout: page
title: tags
---

<p>
{% for tag in site.tags %}
{% capture tag_name %}{{ tag | first }}{% endcapture %}
<a href = "#{{ tag_name }}" class ="tagbox">{{ tag_name }}</a>
{% endfor %}
</p>

{% for tag in site.tags %}
{% capture tag_name %}{{ tag | first }}{% endcapture %}
<h3 id="{{ tag_name }}">{{ tag_name }} </h3>
<p></p>
{% for post in site.tags[tag_name] %}
 * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endfor %}

{% endfor %}

