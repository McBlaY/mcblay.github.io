---
title: Blog
layout: default
pagination:
  enabled: true
  per_page: 5
  permalink: "/blog/page/:num/"
  sort_reverse: true
  collection: "blogs"
---

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 24px;">
  <a href="/" style="color: #1abc9c; text-decoration: none; font-size: 1.3em;"><i class="fas fa-home"></i></a>
  <span style="color: #aaa; font-size: 1.1em;">/</span>
  <h1 style="margin: 0; font-size: 1.6em;">Blog</h1>
</div>

<div style="display: flex; flex-direction: column; gap: 20px; align-items: center;">
  {% for post in paginator.posts %}
  <div class="blog-card" style="display: flex; align-items: stretch; background: var(--card-bg); border-radius: 12px; overflow: hidden; box-shadow: 0 2px 8px rgba(23,0,0,0.08); width: 900px; max-width: 95vw;">
    <div style="flex: 0 0 35%; min-width: 140px; max-width: 240px; background: #111; display: flex; align-items: center; justify-content: center;">
      <img src="{{ post.image | default: '/assets/blog1.jpg' }}" alt="{{ post.title }}" style="width: 100%; height: auto; object-fit: cover; display: block;">
    </div>
    <div style="flex: 0 0 65%; padding: 16px; color: var(--card-text); display: flex; flex-direction: column; justify-content: center;">
      <h2 style="margin-top:0;"><a href="{{ post.url }}" style="color: var(--card-text); text-decoration: none;">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
      <div style="display: flex; justify-content: space-between; align-items: center; margin-top: 16px;">
        <div>
          <a href="{{ post.website | default: '#' }}" target="_blank" style="margin-right: 18px; color: #1abc9c; text-decoration: none; font-weight: bold;">
            <i class="fas fa-globe"></i> Website
          </a>
          <a href="{{ post.github | default: '#' }}" target="_blank" style="color: #1abc9c; text-decoration: none; font-weight: bold;">
            <i class="fab fa-github"></i> GitHub
          </a>
        </div>
        <span style="color: var(--muted); font-size: 0.82em;">{{ post.date | date: "%B %d, %Y" }}</span>
      </div>
    </div>
  </div>
  {% endfor %}
</div>

{% if paginator.total_pages > 1 %}
<div style="text-align: center; margin-top: 40px;">
  {% if paginator.previous_page %}
  <a href="{{ paginator.previous_page_path }}" style="margin-right: 16px; color: #1abc9c; text-decoration: none;">&#8592; Previous</a>
  {% endif %}
  {% for page in (1..paginator.total_pages) %}
    {% if page == paginator.page %}
    <strong style="margin: 0 6px;">{{ page }}</strong>
    {% else %}
    <a href="{% if page == 1 %}/blog/{% else %}/blog/page/{{ page }}/{% endif %}" style="margin: 0 6px; color: #1abc9c; text-decoration: none;">{{ page }}</a>
    {% endif %}
  {% endfor %}
  {% if paginator.next_page %}
  <a href="{{ paginator.next_page_path }}" style="margin-left: 16px; color: #1abc9c; text-decoration: none;">Next &#8594;</a>
  {% endif %}
</div>
{% endif %}