---
layout: page
title: Activities
permalink: /activities/
nav: true
nav_order: 2
description: "Academic activities, visits, conferences, and project-based experiences."
---

Academic activities, visits, conferences, and project-based experiences organised by year. Open an activity to view the note and related photos.

{% for year in site.data.activity_years %}
<h2 class="mt-4"><strong>{{ year }}</strong></h2>

{% assign activities = site.data.activities[year] %}
{% for activity in activities %}
<details class="mb-3 border rounded p-3" {% if forloop.first %}open{% endif %}>
<summary class="d-flex flex-wrap justify-content-between align-items-center" style="cursor: pointer;">
<span><strong>{{ activity.title }}</strong></span>
{% if activity.date %}
<span class="text-muted small">{{ activity.date }}</span>
{% endif %}
</summary>

<div class="mt-3">
<p>{{ activity.summary }}</p>

{% if activity.highlights %}
<ul>
{% for highlight in activity.highlights %}
<li>{{ highlight }}</li>
{% endfor %}
</ul>
{% endif %}

{% if activity.photos %}
<div class="row">
{% for photo in activity.photos %}
<div class="col-sm-6 col-md-4 mt-3">
<a href="{{ photo.src | relative_url }}">
<img src="{{ photo.src | relative_url }}" alt="{{ photo.alt | default: activity.title }}" class="img-fluid rounded z-depth-1" loading="lazy">
</a>
{% if photo.caption %}
<div class="caption">{{ photo.caption }}</div>
{% endif %}
</div>
{% endfor %}
</div>
{% endif %}
</div>
</details>
{% endfor %}

{% unless activities %}
<p class="text-muted">Activities will be added as they are confirmed for public release.</p>
{% endunless %}
{% endfor %}

To update this page, add activities to the matching file in `_data/activities/` and place activity photos in `assets/photos/`.
