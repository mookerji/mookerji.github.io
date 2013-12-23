---
layout: default
author: Bhaskar Mookerji
---

<div id="home">
  <h1> Commentary </h1>
  <ul class="posts">
    {% for post in site.posts %}
      {% if post.tags[0] == "commentary" %}
          <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endif %}
    {% endfor %}
  </ul>
  
  <h1> Projects </h1>
    <ul class="posts">
      {% for post in site.posts %}
      	{% if post.tags[0] == "projects" %}      	
           <li><a href="{{ post.url }}">{{ post.title }}</a></li>
	{% endif %}
      {% endfor %}
    </ul>
</div> 
