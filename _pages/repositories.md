---
layout: page
permalink: /repositories/
title: Repositories
description: Most of my research has code open-sourced at GitHub.
nav: true
nav_order: 3
---

## GitHub users

{% if site.data.repositories.github_users %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.html username=user %}
  {% endfor %}
</div>

---

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
  {% if site.data.repositories.github_users.size > 1 %}
  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% include repository/repo_trophies.html username=user %}
  </div>

  ---

{% endfor %}
{% endif %}
{% endif %}

## GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}

---

## Visitor Statistics

<div class="text-center my-4">

<p style="font-size: 1.05em; margin-bottom: 1.2rem;" id="busuanzi_container">
  <i class="fas fa-eye mr-1"></i> Total Visits:&nbsp;<span id="busuanzi_value_site_pv">...</span>
  &emsp;|&emsp;
  <i class="fas fa-user mr-1"></i> Unique Visitors:&nbsp;<span id="busuanzi_value_site_uv">...</span>
</p>

<div style="max-width: 600px; margin: 0 auto;" id="clustrmaps-container"></div>

</div>

<script>
(function () {
  if (localStorage.getItem('site_owner') === '1') return;
  // busuanzi
  var bsz = document.createElement('script');
  bsz.async = true;
  bsz.src = '//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js';
  document.head.appendChild(bsz);
  // clustrmaps
  var cm = document.createElement('script');
  cm.type = 'text/javascript';
  cm.src = '//clustrmaps.com/map_v2.js?d=kCyV_lwXF6uxEPCyHMK5e43qpF_MxPS5Dd03ky1jE74&cl=ffffff&w=a';
  document.getElementById('clustrmaps-container').appendChild(cm);
})();
</script>
