---
layout: default
title: "Research"
---

<div class="wrapper">
<div class="post-content">

# Research Overview



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
</div>
