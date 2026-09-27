---
layout: page
title: Gallery
permalink: /photos/
nav: true
nav_order: 5
description: "A small photo archive from research, fieldwork, and everyday observations."
---

Add photos to `assets/photos/`. This page automatically lists image files placed there.

Supported file types: `.jpg`, `.jpeg`, `.png`, `.webp`, `.gif`.

{% assign photo_files = site.static_files | sort: 'path' %}

<div class="row">
  {% assign photo_count = 0 %}
  {% for photo in photo_files %}
    {% assign ext = photo.extname | downcase %}
    {% if photo.path contains '/assets/photos/' %}
      {% if ext == '.jpg' or ext == '.jpeg' or ext == '.png' or ext == '.webp' or ext == '.gif' %}
        {% assign photo_count = photo_count | plus: 1 %}
        {% assign photo_caption = photo.name | remove: ext | replace: '-', ' ' | replace: '_', ' ' %}
        <div class="col-sm-6 col-md-4 mt-3">
          <a href="{{ photo.path | relative_url }}">
            <img src="{{ photo.path | relative_url }}" alt="{{ photo_caption }}" class="img-fluid rounded z-depth-1" loading="lazy">
          </a>
          <div class="caption">{{ photo_caption }}</div>
        </div>
      {% endif %}
    {% endif %}
  {% endfor %}
</div>

{% if photo_count == 0 %}

No photos have been added yet.

Put image files in:

```text
assets/photos/
```

Example:

```text
assets/photos/fieldwork-daegu-2025.jpg
assets/photos/wind-observation-tower.webp
assets/photos/cfd-visualization.png
```

{% endif %}
