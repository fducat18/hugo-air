---
title: Responsive OpenStreetMap
date: 2026-09-30T10:00:00+02:00
draft: false
tags: ['osm','map']
params:
  catchline: Lightweight and interactive OpenStreetMap integration with Leaflet
  button: Learn more
osm: true
---

# Responsive OpenStreetMap

The **Air** theme lets you embed an interactive OpenStreetMap map directly at the bottom of any page.

## Two Configuration Modes

### 1. Interactive Multi-Markers Mode (Recommended)

Define a list of markers (`osm_markers`) with coordinates, titles, descriptions, and optional links in your `hugo.yaml` or page front matter:

```yaml
params:
  osm_zoom: 16
  osm_markers:
    - title: "Quartier Libre"
      lat: 50.643936
      lon: 3.050444
      description: "Espace convivial & culturel au bord de la Deûle — Lille"
      link: "https://www.openstreetmap.org/search?lat=50.643936&lon=3.050444"
    - title: "Le p'tit quinquin"
      lat: 50.637125
      lon: 3.039490
      description: "Statue et symbole lillois — Square Foch, Lille"
      link: "https://www.openstreetmap.org/search?lat=50.637125&lon=3.039490"
```

The map automatically fits bounds (`fitBounds`) to display all markers at the optimal zoom level.

### 2. Iframe Mode (Standard OSM Export or uMap)

If you prefer an iframe from OSM or uMap:

```yaml
params:
  osm_url: https://www.openstreetmap.org/export/embed.html?bbox=3.02%2C50.62%2C3.07%2C50.66&layer=mapnik&marker=50.6439%2C3.0504
```

### Page Activation

Add `osm: true` to the Markdown front matter:

```yaml
---
title: My Page
osm: true
---
```
