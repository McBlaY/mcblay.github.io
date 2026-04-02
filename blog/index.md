---
title: Blog
layout: default
---

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 24px;">
  <a href="/" style="color: #1abc9c; text-decoration: none; font-size: 1.3em;"><i class="fas fa-home"></i></a>
  <span style="color: #aaa; font-size: 1.1em;">/</span>
  <h1 style="margin: 0; font-size: 1.6em;">Blog</h1>
</div>

<div id="blog-cards" style="display: flex; flex-direction: column; gap: 20px; align-items: center;">
  {% assign sorted_blogs = site.blogs | sort: 'date' | reverse %}
  {% for post in sorted_blogs %}
  <div class="blog-card" style="display: flex; align-items: stretch; background: var(--card-bg); border-radius: 12px; overflow: hidden; box-shadow: 0 2px 8px rgba(23,0,0,0.08); width: 900px; max-width: 95vw;height: 180px;">
    <div style="flex: 0 0 35%; min-width: 140px; max-width: 240px; background: #fff; display: flex; align-items: center; justify-content: center;">
      <img src="{{ post.image | default: '/assets/images/header.png' }}" alt="{{ post.title }}" style="width: 100%; height: auto; object-fit: cover; display: block;">
    </div>
    <div style="flex: 0 0 65%; padding: 10px 16px; color: var(--card-text); display: flex; flex-direction: column; justify-content: space-between; overflow: hidden;">
      <h2 style="margin: 8px 0 4px; font-size: 1em;"><a href="{{ post.url }}" target="_blank" style="color: var(--card-text); text-decoration: none;">{{ post.title }}</a></h2>
      <p style="margin: 0 0 6px; font-size: 0.85em; line-height: 1.4; overflow: hidden; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical;">{{ post.excerpt | strip_html | truncatewords: 50 }}</p>
      <div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: nowrap; gap: 8px;">
        <span style="color: var(--muted); font-size: 0.82em;">{{ post.date | date: "%B %d, %Y" }}</span>
        <div>
          <a href="{{ post.github | default: '#' }}" target="_blank" style="color: #1abc9c; text-decoration: none; font-weight: bold;">
            <i class="fab fa-github"></i> GitHub
          </a>
        </div>
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<div id="blog-pagination" style="text-align: center; margin-top: 40px;"></div>

<script>
(function() {
  var perPage = 5;
  var cards = Array.from(document.querySelectorAll('.blog-card'));
  var nav = document.getElementById('blog-pagination');
  var totalPages = Math.ceil(cards.length / perPage);
  if (totalPages <= 1) { nav.style.display = 'none'; }

  function showPage(page) {
    cards.forEach(function(card, i) {
      card.style.display = (i >= (page - 1) * perPage && i < page * perPage) ? 'flex' : 'none';
    });
    renderNav(page);
    window.scrollTo(0, 0);
  }

  function renderNav(current) {
    var html = '';
    if (current > 1) html += '<a href="#" data-page="' + (current - 1) + '" style="margin: 0 8px; color: #1abc9c; text-decoration: none;">&larr; Prev</a>';
    for (var p = 1; p <= totalPages; p++) {
      if (p === current) {
        html += '<strong style="margin: 0 6px;">' + p + '</strong>';
      } else {
        html += '<a href="#" data-page="' + p + '" style="margin: 0 6px; color: #1abc9c; text-decoration: none;">' + p + '</a>';
      }
    }
    if (current < totalPages) html += '<a href="#" data-page="' + (current + 1) + '" style="margin: 0 8px; color: #1abc9c; text-decoration: none;">Next &rarr;</a>';
    nav.innerHTML = html;
    nav.querySelectorAll('a[data-page]').forEach(function(a) {
      a.addEventListener('click', function(e) { e.preventDefault(); showPage(+this.dataset.page); });
    });
  }

  showPage(1);
})();
</script>