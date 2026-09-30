---
title: Responsive OpenStreetMap
date: 2026-09-30T10:00:00+02:00
draft: false
tags: ['osm','map']
params:
  catchline: Lightweight and privacy-friendly OpenStreetMap integration
  button: Learn more
osm: true
---

# Responsive OpenStreetMap

## Usage

Configure your OSM URL in your Hugo config file and enable the map in the front matter of your Markdown page.

### Hugo Config file

Add your OpenStreetMap (or uMap) embed URL:

```yaml
params:
  osm_url: https://www.openstreetmap.org/export/embed.html?bbox=-2.4050%2C46.6980%2C-2.3350%2C46.7320&layer=mapnik&marker=46.7141%2C-2.3681
```

### Markdown Page Front Matter

Add `osm: true` in your Markdown file:

```yaml
---
title: My Page
osm: true
---
```
