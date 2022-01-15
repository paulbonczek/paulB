---
layout: page
title: Posters
permalink: /posters/
description: A list of my posters while at UVA.
nav: false
display_categories: [posters]
---

<!-- pages/posters.md -->
<div class="projects">
{%- if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_posters = site.posters | where: "category", category -%}
  {%- assign sorted_posters = categorized_posters | sort: "importance" | reverse %}
  <!-- Generate cards for each project -->
  <div class="grid">
    {%- for poster in sorted_posters -%}
      {% include posters.html %}
    {%- endfor %}
  </div>
  {% endfor %}

{%- else -%}
<!-- Display posters without categories -->
  {%- assign sorted_posters = site.posters | sort: "importance" -%}
  <!-- Generate cards for each poster -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for poster in sorted_posters -%}
      {% include posters_horizontal.html %}
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
{%- endif -%}
</div>
