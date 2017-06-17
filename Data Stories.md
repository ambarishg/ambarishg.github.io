---
layout: page
title: Data Stories
---


{% for post in site.posts %}
	{% for tag in post.tags %}
		{% if (tag == 'Data Visualization') %}
* {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
		{% endif %}
	{% endfor %}
{% endfor %}

