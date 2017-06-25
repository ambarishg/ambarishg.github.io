---
layout: page
title: DataStories
---


{% for post in site.posts %}
	{% for tag in post.tags %}
		{% if (tag == 'DataVisualization') %}
* {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
		{% endif %}
	{% endfor %}
{% endfor %}

