---
layout: none
title: My Personal Blog Home
permalink: /
---
<script>(function(){var t=localStorage.getItem('theme')||'dark';document.documentElement.setAttribute('data-theme',t);})();</script>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
<style>
  :root { --bg:#181818; --text:#eeeeee; --hero-border:#333333; --accent:#1abc9c; --card-bg:#2a2a2a; --card-text:#eeeeee; --muted:#999999; --section-border:#333; }
  [data-theme="light"] { --bg:#f5f5f5; --text:#222222; --hero-border:#cccccc; --accent:#0e9b78; --card-bg:#e0e0e0; --card-text:#222222; --muted:#666666; --section-border:#ccc; }
  *, *::before, *::after { box-sizing: border-box; }
  html, body { height: 100%; }
  body { margin:0; background:var(--bg); color:var(--text); transition:background 0.25s,color 0.25s; font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif; display:flex; flex-direction:column; min-height:100vh; }
  #theme-toggle { position:fixed; top:14px; right:16px; background:rgba(128,128,128,0.25); color:var(--text); border:1px solid rgba(128,128,128,0.4); border-radius:50%; width:40px; height:40px; font-size:1.1em; cursor:pointer; box-shadow:0 2px 8px rgba(0,0,0,0.3); z-index:9999; display:flex; align-items:center; justify-content:center; padding:0; transition:background 0.25s; }
  #theme-toggle:hover { opacity:0.8; }
  .page-wrap { max-width:980px; margin:0 auto; padding:0 20px 60px; }
  /* Nav */
  .home-nav { display:flex; justify-content:center; gap:120px; padding:20px 0 16px; }
  .home-nav a { color:var(--accent); text-decoration:none; text-align:center; display:flex; flex-direction:column; align-items:center; gap:6px; font-size:1.1em; }
  .home-nav a i { font-size:1.8em; }
  /* Profile */
  .profile { display:flex; gap:40px; align-items:flex-start; padding:20px 0 24px; }
  .profile-text p { margin:0 0 14px; line-height:1.7; text-align:justify; }
  /* Section headings */
  .section-heading { display:flex; justify-content:space-between; align-items:center; margin:10px 0 14px; border-bottom:1px solid var(--section-border); padding-bottom:8px; }
  .section-heading h2 { margin:0; font-size:1.4em; }
  .section-heading a { color:var(--accent); text-decoration:none; font-size:0.9em; }
  /* Latest cards */
  .latest-cards { display:flex; flex-direction:column; gap:14px; }
  .latest-card { display:flex; align-items:stretch; background:var(--card-bg); border-radius:10px; overflow:hidden; box-shadow:0 2px 6px rgba(0,0,0,0.12); height:110px; }
  .latest-card .card-thumb { flex:0 0 120px; width:120px; height:110px; background:#111; display:flex; align-items:center; justify-content:center; overflow:hidden; }
  .latest-card .card-thumb img { width:100%; height:100%; object-fit:cover; display:block; }
  .latest-card .card-body { flex:1; padding:14px 16px; display:flex; flex-direction:column; justify-content:center; }
  .latest-card .card-body h3 { margin:0 0 6px; font-size:1.05em; }
  .latest-card .card-body h3 a { color:var(--card-text); text-decoration:none; }
  .latest-card .card-body h3 a:hover { color:var(--accent); }
  .latest-card .card-body p { margin:0 0 10px; font-size:0.88em; color:var(--muted); line-height:1.5; }
  .latest-card .card-meta { font-size:0.78em; color:var(--muted); }
  .card-type { font-size:0.85em; font-weight:600; color:var(--accent); text-decoration:none; }
  .card-type:hover { opacity:0.8; }
</style>

<button id="theme-toggle" title="Toggle light/dark theme"></button>

<div style="position:relative;">
  <img src="/assets/images/header.png" alt="Header" style="width:100%;max-height:220px;object-fit:cover;display:block;">
</div>

<div style="background:var(--bg);border-top:1px solid var(--hero-border);flex:1;">
  <div class="page-wrap">

    <!-- Nav -->
    <nav class="home-nav">
      <a href="/blog"><i class="fa fa-calendar"></i>Blog</a>
      <a href="/research"><i class="fa fa-book"></i>Research</a>
      <a href="/projects"><i class="fa fa-folder"></i>Projects</a>
      <a href="/about"><i class="fa fa-user"></i>About Me</a>
    </nav>

    <!-- Profile -->
    <div class="profile">
      <div style="display:flex;flex-direction:column;align-items:center;gap:10px;flex-shrink:0;">
        <img src="/assets/images/profile_pic.jpg" alt="Michel Torny, PhD" onerror="this.style.background='#444';this.removeAttribute('src')" style="width:220px;height:220px;border-radius:50%;object-fit:cover;background:var(--card-bg);">
        <div style="font-size:1.15em;font-weight:600;color:var(--text);">Michel Torny</div>
        <div style="display:flex;gap:16px;font-size:1.4em;">
          <a href="https://github.com/McBlaY" target="_blank" style="color:var(--muted);text-decoration:none;" title="GitHub"><i class="fab fa-github"></i></a>
          <a href="https://linkedin.com/in/yourprofile" target="_blank" style="color:var(--muted);text-decoration:none;" title="LinkedIn"><i class="fab fa-linkedin"></i></a>
          <a href="https://twitter.com/yourhandle" target="_blank" style="color:var(--muted);text-decoration:none;" title="Twitter / X"><i class="fa-brands fa-x-twitter"></i></a>
        </div>
      </div>
      <div class="profile-text">
        <h1 style="margin:0 0 18px;font-size:1.9em;text-align:center;">Michel Torny, PhD</h1>
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia.</p>
      </div>
    </div>

    <!-- What's New -->
    <div class="section-heading">
      <h2><i class="fa fa-bolt" style="color:var(--accent);margin-right:8px;"></i>What's New</h2>
    </div>
    <div class="latest-cards">
      {% assign all_items = site.blogs | concat: site.research | concat: site.projects | sort: 'date' | reverse %}
      {% for item in all_items limit:5 %}
      <div class="latest-card">
        <div class="card-thumb">
          <img src="{{ item.image | default: '/assets/images/header.png' }}" alt="{{ item.title }}">
        </div>
        <div class="card-body">
          <h3 style="margin-top:0;">{% if item.collection == 'blogs' %}<a href="/blog" class="card-type">Blog</a>{% elsif item.collection == 'research' %}<a href="/research" class="card-type">Research</a>{% elsif item.collection == 'projects' %}<a href="/projects" class="card-type">Project</a>{% endif %} <span style="color:var(--muted);font-weight:300;">|</span> <a href="{{ item.url }}" style="color:var(--card-text);text-decoration:none;">{{ item.title }}</a></h3>
          <p>{{ item.excerpt | strip_html | truncatewords: 20 }}</p>
          <span class="card-meta">{{ item.date | date: "%B %d, %Y" }}</span>
        </div>
      </div>
      {% endfor %}
    </div>

  </div>
</div>

<footer style="background:var(--card-bg);border-top:1px solid var(--section-border);padding:24px 20px;text-align:center;">
  <div style="max-width:980px;margin:0 auto;display:flex;flex-direction:column;gap:10px;align-items:center;">
    <div style="display:flex;gap:20px;font-size:1.3em;">
      <a href="https://github.com/McBlaY" target="_blank" style="color:var(--muted);text-decoration:none;" title="GitHub"><i class="fab fa-github"></i></a>
      <a href="https://linkedin.com/in/yourprofile" target="_blank" style="color:var(--muted);text-decoration:none;" title="LinkedIn"><i class="fab fa-linkedin"></i></a>
      <a href="https://twitter.com/yourhandle" target="_blank" style="color:var(--muted);text-decoration:none;" title="Twitter / X"><i class="fa-brands fa-x-twitter"></i></a>
    </div>
    <div style="font-size:0.85em;color:var(--muted);">
      &copy; {{ 'now' | date: "%Y" }} Michel Torny &middot;
      <a href="/blog" style="color:var(--muted);text-decoration:none;margin:0 6px;">Blog</a>
      <a href="/research" style="color:var(--muted);text-decoration:none;margin:0 6px;">Research</a>
      <a href="/projects" style="color:var(--muted);text-decoration:none;margin:0 6px;">Projects</a>
      <a href="/about" style="color:var(--muted);text-decoration:none;margin:0 6px;">About</a>
    </div>
  </div>
</footer>

<script>
(function() {
  var html = document.documentElement;
  var btn = document.getElementById('theme-toggle');
  function applyTheme(t) {
    html.setAttribute('data-theme', t);
    btn.innerHTML = t === 'dark' ? '<i class="fas fa-sun"></i>' : '<i class="fas fa-moon"></i>';
  }
  applyTheme(localStorage.getItem('theme') || 'dark');
  btn.addEventListener('click', function() {
    var next = html.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
    localStorage.setItem('theme', next);
    applyTheme(next);
  });
})();
</script>
