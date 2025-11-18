---
layout: default
title: "Research"
---
<style>
/* Custom styles for better readability */
.research-container {
  max-width: 900px;
  margin: 0 auto;
  padding: 20px 40px;
}
.research-header {
  border-bottom: 2px solid #e1e4e8;
  padding-bottom: 16px;
  margin-bottom: 32px;
}
.research-section {
  margin-bottom: 48px;
}
.research-section h2 {
  color: #0366d6;
  border-bottom: 1px solid #e1e4e8;
  padding-bottom: 8px;
  margin-bottom: 24px;
}
.research-item {
  margin-bottom: 32px;
  padding: 20px;
  background-color: #f6f8fa;
  border-radius: 6px;
  border-left: 4px solid #0366d6;
}
.research-item h3 {
  margin-top: 0;
  margin-bottom: 8px;
}
.research-item h3 a {
  color: #24292e;
  text-decoration: none;
}
.research-item h3 a:hover {
  color: #0366d6;
  text-decoration: underline;
}
.research-date {
  color: #586069;
  font-size: 14px;
  margin-bottom: 12px;
}
.research-excerpt {
  color: #24292e;
  line-height: 1.6;
  margin-bottom: 12px;
}
.research-excerpt a {
  color: #0366d6;
  text-decoration: none;
}
.research-excerpt a:hover {
  text-decoration: underline;
}
.read-more {
  display: inline-block;
  color: #0366d6;
  text-decoration: none;
  font-weight: 500;
}
.read-more:hover {
  text-decoration: underline;
}
.no-items {
  color: #586069;
  font-style: italic;
  padding: 20px;
  background-color: #f6f8fa;
  border-radius: 6px;
}
/* Mobile responsiveness */
@media (max-width: 768px) {
  .research-container {
    padding: 20px;
  }
  
  .research-item {
    padding: 16px;
  }
}
</style>
<div class="research-container">
  <h1 class="research-header">Research Overview</h1>
  
  {% assign categories = "environment,energy,biotechnology" | split: "," %}
  {% for cat in categories %}
    {% assign category_name = ""  %}

    <div class="research-section">
    {% if cat == "environment" %}
      {% assign category_name = "Environment, Chemistry, IP & Economics" %}
    {% elsif cat == "energy" %}
      {% assign category_name = "Energy Systems & Energy Economics" %}
    {% elsif cat == "biotechnology" %}
      {% assign category_name = "Biotechnology & Bioprocess Engineering" %}
  {% endif %}
      
      {% assign posts_in_area = 0 %}
      {% for post in site.posts %}
        {% if post.research_area == cat %}
          {% assign posts_in_area = posts_in_area | plus: 1 %}
          <div class="research-item">
            <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
            <div class="research-date"><strong>Date:</strong> {{ post.date | date: "%B %Y" }}</div>
            {% if post.excerpt %}
            <div class="research-excerpt">
              {{ post.excerpt | strip_html | remove: 'Download' | truncatewords: 40 }}
            </div>
            <a href="{{ post.url | relative_url }}" class="read-more">Read More →</a>
            {% endif %}
          </div>
        {% endif %}
      {% endfor %}
      
      {% if posts_in_area == 0 %}
      <div class="no-items">
        No research items currently tagged under {{ category_name }}.
      </div>
      {% endif %}
    </div>
  {% endfor %}
</div>
