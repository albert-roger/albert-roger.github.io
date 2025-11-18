---
layout: default
title: "Research"
---

<style>
  /* This CSS block creates a centered reading area with a comfortable width */
  #custom-research-content {
    max-width: 900px; /* Sets a maximum width for readability */
    margin: 0 auto;  /* Centers the entire content block */
    padding: 0 20px; /* Adds padding on the sides for smaller screens */
  }
</style>

<div id="custom-research-content">

# Research Overview

My work focuses on the intersection of engineering and economics, with specific interests across three major areas of innovation and sustainability: Environment, Energy, and Biotechnology.

---

{% assign categories = "environment,energy,biotechnology" | split: "," %}

{% for cat in categories %}
  {% assign category_name = cat | capitalize %}

{% if category_name == 'Environment' %}
## 1. {{ category_name }} 🌍
{% elsif category_name == 'Energy' %}
## 2. {{ category_name }} 💡
{% elsif category_name == 'Biotechnology' %}
## 3. {{ category_name }} 🔬
{% endif %}

<br>

  {% assign posts_in_area = 0 %}

  {% for post in site.posts reversed %}
    {% if post.research_area == cat %}
      {% assign posts_in_area = posts_in_area | plus: 1 %}
      
### [{{ post.title }}]({{ post.url | relative_url }})
**Date:** {{ post.date | date: "%B %Y" }}

{% if post.excerpt %}
{{ post.excerpt | strip_html | truncatewords: 40 }}
[[Read More]({{ post.url | relative_url }})]
{% endif %}

<br>
    {% endif %}
  {% endfor %}

  {% if posts_in_area == 0 %}
<p>No research items currently tagged under {{ category_name }}.</p>
  {% endif %}

---
{% endfor %}

</div>
