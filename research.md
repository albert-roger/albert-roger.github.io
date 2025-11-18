---
layout: default
title: "Research"
---

# Research Overview

My work focuses on the intersection of engineering and economics, with specific interests across three major areas of innovation and sustainability: Environment, Energy, and Biotechnology.

---

{% assign research_posts = site.posts | where: "categories", "research" | sort: "date" | reverse %}

{% assign categories = "environment,energy,biotechnology" | split: "," %}

{% for cat in categories %}
  {% assign category_name = cat | capitalize %}
  
  {% if category_name == 'Environment' %}
  ## 1. {{ category_name }} 🌍  {% elsif category_name == 'Energy' %}
  ## 2. {{ category_name }} 💡  {% elsif category_name == 'Biotechnology' %}
  ## 3. {{ category_name }} 🔬  {% endif %}
  
  {% assign filtered_posts = research_posts | where: "research_area", cat %}
  
  {% if filtered_posts.size > 0 %}
    {% for post in filtered_posts %}
      ### [{{ post.title }}]({{ post.url | relative_url }})
      **Date:** {{ post.date | date: "%B %d, %Y" }}
      
      {% if post.excerpt %}
        {{ post.excerpt | strip_html | truncatewords: 40 }}
        [[Read More]({{ post.url | relative_url }})]
      {% endif %}
    {% endfor %}
  {% else %}
    <p>No posts currently available in the {{ category_name }} area. Please check back soon!</p>
  {% endif %}

---
{% endfor %}
