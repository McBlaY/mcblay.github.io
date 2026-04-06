---
title: About
permalink: /about
layout: default
---

<style>
  .about-section { margin-bottom: 40px; }
  .about-section h2 { font-size: 1.3em; border-bottom: 1px solid var(--section-border, #333); padding-bottom: 8px; margin-bottom: 20px; color: var(--accent); }
  .about-header { display: flex; gap: 36px; align-items: flex-start; justify-content: center; margin-bottom: 40px; }
  .about-header img { width: 160px; height: 160px; border-radius: 50%; object-fit: cover; background: var(--card-bg); flex-shrink: 0; }
  .about-header-text h1 { margin: 0 0 6px; font-size: 1.9em; }
  .about-header-text .subtitle { color: var(--muted); font-size: 1em; margin-bottom: 14px; text-align: center; }
  .about-header-text .social-links { display: flex; gap: 16px; font-size: 1.3em; justify-content: center; }
  .about-header-text .social-links a { color: var(--muted); text-decoration: none; }
  .about-header-text .social-links a:hover { color: var(--accent); }
  .timeline-item { margin-bottom: 22px; }
  .timeline-item .tl-header { display: flex; justify-content: space-between; align-items: baseline; flex-wrap: wrap; gap: 4px; }
  .timeline-item .tl-role { font-weight: 700; font-size: 1.05em; }
  .timeline-item .tl-org { color: var(--muted); font-size: 0.95em; }
  .timeline-item .tl-date { color: var(--accent); font-size: 0.88em; white-space: nowrap; }
  .timeline-item ul { margin: 8px 0 0 18px; padding: 0; }
  .timeline-item ul li { margin-bottom: 4px; font-size: 0.95em; line-height: 1.6; color: var(--text); }
  .skills-grid { display: flex; flex-wrap: wrap; gap: 10px; }
  .skill-tag { background: var(--card-bg); color: var(--card-text); border-radius: 20px; padding: 5px 14px; font-size: 0.88em; }
  .pub-list { list-style: none; padding: 0; margin: 0; }
  .pub-list li { margin-bottom: 14px; font-size: 0.93em; line-height: 1.7; padding-left: 20px; position: relative; }
  .pub-list li::before { content: "▸"; position: absolute; left: 0; color: var(--accent); }
  .reviewer-list { list-style: none; padding: 0; margin: 0; display: flex; flex-direction: column; gap: 8px; }
  .reviewer-list li { display: flex; justify-content: space-between; flex-wrap: wrap; font-size: 0.93em; background: var(--card-bg); padding: 10px 16px; border-radius: 8px; }
  .reviewer-list li .journal-if { color: var(--accent); font-weight: 600; font-size: 0.88em; }
</style>

<!-- Breadcrumb -->
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 28px;">
  <a href="/" style="color: #1abc9c; text-decoration: none; font-size: 1.3em;"><i class="fas fa-home"></i></a>
  <span style="color: #aaa; font-size: 1.1em;">/</span>
  <h1 style="margin: 0; font-size: 1.6em;">About Me</h1>
</div>

<!-- Header -->
<div class="profile" style="display:flex; gap:0px; align-items:flex-start; margin-bottom:40px;margin-left:100px;">
  <img src="/assets/images/profile_pic.jpg" alt="Michel Torny" onerror="this.style.background='#444';this.removeAttribute('src')" style="width:175px;height:175px;border-radius:50%;object-fit:cover;background:var(--card-bg);flex-shrink:0;">
  <div class="about-header-text" style="align-self: center; margin-right:175px;">
    <h1>Michel Torny, PhD</h1>
    <div class="subtitle">Data & Applied Scientist</div>
    <div class="social-links">
      <a href="https://github.com/McBlaY" target="_blank" title="GitHub"><i class="fab fa-github"></i></a>
      <a href="https://linkedin.com/in/hoesemicheltornyeviadzi" target="_blank" title="LinkedIn"><i class="fab fa-linkedin"></i></a>
      <a href="https://x.com/tornymichel" target="_blank" title="X / Twitter"><i class="fa-brands fa-x-twitter"></i></a>
      <a href="https://scholar.google.com/citations?user=Hoese+Michel+Tornyeviadzi" target="_blank" title="Google Scholar"><i class="fas fa-graduation-cap"></i></a>
    </div>
  </div>
</div>

<!-- Education -->
<div class="about-section">
  <h2><i class="fas fa-graduation-cap" style="margin-right:8px;"></i>Education</h2>
  <div class="timeline-item">
    <div class="tl-header">
      <span class="tl-role">PhD Engineering – HydroInformatics</span>
      <span class="tl-date">Jan 2020 – Dec 2023</span>
    </div>
    <div class="tl-org">Norwegian University of Science and Technology (NTNU)</div>
  </div>
  <div class="timeline-item">
    <div class="tl-header">
      <span class="tl-role">MPhil Applied Mathematics – System Identification</span>
      <span class="tl-date">Aug 2015 – Jun 2017</span>
    </div>
    <div class="tl-org">Kwame Nkrumah University of Science and Technology (KNUST)</div>
  </div>
</div>

<!-- Work Experience -->
<div class="about-section">
  <h2><i class="fas fa-briefcase" style="margin-right:8px;"></i>Work Experience</h2>

  <div class="timeline-item">
    <div class="tl-header">
      <span class="tl-role">Data & Applied Scientist – HydroInformatics</span>
      <span class="tl-date">Jan 2026 – Present</span>
    </div>
    <div class="tl-org">Stealth WFH</div>
  </div>

  <div class="timeline-item">
    <div class="tl-header">
      <span class="tl-role">Applied Scientist – HydroInformatics</span>
      <span class="tl-date">Jun 2024 – Dec 2025</span>
    </div>
    <div class="tl-org">HULO.AI</div>
  </div>

  <div class="timeline-item">
    <div class="tl-header">
      <span class="tl-role">Applied Research Scientist</span>
      <span class="tl-date">Jan 2024 – Dec 2024</span>
    </div>
    <div class="tl-org">Smart Water Lab, NTNU</div>
  </div>

  <div class="timeline-item">
    <div class="tl-header">
      <span class="tl-role">PhD Research Fellow</span>
      <span class="tl-date">Jan 2020 – Dec 2023</span>
    </div>
    <div class="tl-org">Smart Water Lab, NTNU</div>
  </div>
</div>

<!-- Presentations & Guest Talks -->
<div class="about-section">
  <h2 id="presentations-guest-talks"><i class="fas fa-microphone" style="margin-right:8px;"></i>Presentations & Guest Talks</h2>
  <ul class="pub-list">
    <li>Torny, H. M., (2024). Improving the Scalability of DMA based Leakage Detection through AI. Nordic Water Conference (NORDIWA), Copenhagen – Denmark. (Oral).</li>
    <li>Torny, H. M., (2024). Scalable District Metering Area Agnostic Leakage Detection. World Water Congress, Canada. (Oral).</li>
    <li>Torny, H. M., (2023). Near Realtime District Metering Area Agnostic Leakage Detection in WDNs. North American Water Loss Conference & Exposition, USA.</li>
    <li>Torny, H. M., (2022). Performance Evaluation of Anomaly Detection Algorithms for Leakage Detection in Water Distribution Networks. IWA Water Loss Asia, Malaysia.</li>
    <li>Torny, H. M., (2022). DMA Based Incipient Leakage Detection via BiLSTM Deep Autoencoder. IWA World Water Congress & Exhibition, Copenhagen – Denmark.</li>
  </ul>
  <ul class="pub-list">
    <li>Torny H. M. (2023), Domain Agnostic ML Methods for Anomaly Detection in Water Distribution Networks. SINTEF - Norway.</li>
    <li>Torny H. M. (2023), Data Driven Leakage Detection in Water Distribution Networks. VANFORSK - Norway.</li>
  </ul>
</div>

<!-- Journal Reviewer -->
<div class="about-section">
  <h2><i class="fas fa-tasks" style="margin-right:8px;"></i>Journal Reviewer</h2>
  <ul class="reviewer-list">
    <li><span><i class="fas fa-book" style="color:var(--accent);margin-right:8px;"></i><a href="https://www.sciencedirect.com/journal/engineering-applications-of-artificial-intelligence" target="_blank" style="color:var(--card-text);text-decoration:none;">Engineering Applications of Artificial Intelligence</a> – Elsevier</span></li>
    <li><span><i class="fas fa-book" style="color:var(--accent);margin-right:8px;"></i><a href="https://www.sciencedirect.com/journal/advanced-engineering-informatics" target="_blank" style="color:var(--card-text);text-decoration:none;">Advanced Engineering Informatics</a> – Elsevier</span></li>
    <li><span><i class="fas fa-book" style="color:var(--accent);margin-right:8px;"></i><a href="https://www.sciencedirect.com/journal/reliability-engineering-and-system-safety" target="_blank" style="color:var(--card-text);text-decoration:none;">Reliability Engineering &amp; System Safety</a> – Elsevier</span></li>
    <li><span><i class="fas fa-book" style="color:var(--accent);margin-right:8px;"></i><a href="https://www.sciencedirect.com/journal/expert-systems-with-applications" target="_blank" style="color:var(--card-text);text-decoration:none;">Expert Systems with Applications</a> – Elsevier</span></li>
    <li><span><i class="fas fa-book" style="color:var(--accent);margin-right:8px;"></i><a href="https://www.sciencedirect.com/journal/results-in-engineering" target="_blank" style="color:var(--card-text);text-decoration:none;">Results in Engineering</a> – Elsevier</span></li>
    <li><span><i class="fas fa-book" style="color:var(--accent);margin-right:8px;"></i><a href="https://ascelibrary.org/journal/jwrmd5" target="_blank" style="color:var(--card-text);text-decoration:none;">Journal of Water Resources Planning and Management</a> – ASCE</span></li>
  </ul>
</div>