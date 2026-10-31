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
<div class="repo-grid">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}

<script>
(function () {
  var colors = {Python: '#3572A5', JavaScript: '#f1e05a', TypeScript: '#3178c6', Jupyter: '#DA5B0B', 'Jupyter Notebook': '#DA5B0B', HTML: '#e34c26', CSS: '#563d7c', Shell: '#89e051', 'C++': '#f34b7d', C: '#555555', Java: '#b07219', R: '#198CE7', MATLAB: '#e16737'};
  document.querySelectorAll('.repo-card[data-repo]').forEach(function (card) {
    fetch('https://api.github.com/repos/' + card.dataset.repo)
      .then(function (r) { return r.ok ? r.json() : Promise.reject(); })
      .then(function (d) {
        card.querySelector('.repo-card-desc').textContent = d.description || 'No description provided.';
        var show = function (sel, text) {
          var el = card.querySelector(sel);
          el.querySelector(sel === '.repo-card-lang' ? '.repo-card-lang-name' : 'span').textContent = text;
          el.hidden = false;
        };
        if (d.language) {
          show('.repo-card-lang', d.language);
          card.querySelector('.repo-card-dot').style.background = colors[d.language] || '#8b949e';
        }
        show('.repo-card-stars', d.stargazers_count);
        show('.repo-card-forks', d.forks_count);
      })
      .catch(function () {});
  });
})();
</script>
