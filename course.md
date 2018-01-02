---
layout: page
title: Course
permalink: /course/
---

{% for dayInCourse in site.course %}

{% if dayInCourse.redirect %}
<div class="project">
    <div class="thumbnail">
        <a href="{{ dayInCourse.redirect }}" target="_blank">
        {% if dayInCourse.img %}
        <img class="thumbnail" src="{{ dayInCourse.img }}"/>
        {% endif %}    
        <span>
            <h1>{{ dayInCourse.title }}</h1>
            <br/>
            <p>{{ dayInCourse.description }}</p>
        </span>
        </a>
    </div>
</div>
{% else %}

<div class="dayInCourseBox ">
    
        <a href="{{ site.baseurl }}{{ dayInCourse.url }}">
        {{ dayInCourse.title }}
        </a>
        {% if dayInCourse.img %}
        <img class="thumbnail" src="{{ dayInCourse.img }}"/>
        {% endif %}    
        <span>
            
            <br/>
            <p>{{ dayInCourse.description }}</p>
        </span>
        
   
</div>

{% endif %}

{% endfor %}
