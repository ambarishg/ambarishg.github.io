---
layout: page
title: testimonials
---
<ul class="post-list">
{% for testimonial in site.testimonials  %}
    <li>
        <p>
            <b>{{ testimonial.title }} workshop</b>
        </p>
        <p>{{ testimonial.name }} - {{ testimonial.jobtitle }}</p>
        <p>{{ testimonial.content }}</p>
      </li>
{% endfor %}
</ul>