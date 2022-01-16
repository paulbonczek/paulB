---
layout: page
title: Posters
permalink: /posters/
description: A collection of past and present works.
nav: true
display_categories: [UVA]
horizontal: false
---

<!-- pages/projects.md -->
<div class="posters">
<!-- Display categorized posters -->
{%- for category in page.display_categories %}
<h2 class="category">{{ category }}</h2>
{%- assign categorized_posters = site.posters | where: "category", category -%}
{%- assign sorted_posters = categorized_posters | sort: "importance" | reverse %}
<!-- Generate cards for each project -->
{% if page.horizontal -%}
<div class="container">
  <div class="row row-cols-2">
  {%- for poster in sorted_posters -%}
    {% include projects_horizontal.html %}
  {%- endfor %}
  </div>
</div>
{%- else -%}
<div class="grid">
  {%- for poster in sorted_posters -%}
    {% include posters.html %}
  {%- endfor %}
</div>
{%- endif -%}
{% endfor %}

</div>
