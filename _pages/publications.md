---
layout: page
permalink: /publications/
title: Publications
description: (*) denotes equal contribution
# years: [2022, 2021, 2020, 1967, 1956, 1950, 1935]
years: [2022, 2021, 2020]
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f {{ site.scholar.bibliography }} -q @*[year={{y}}]* %}
{% endfor %}

</div>
