---
title: Carte OpenStreetMap Responsive
date: 2026-09-30T10:00:00+02:00
draft: false
tags: ['osm','map']
params:
  catchline: Intégration OpenStreetMap légère et interactive avec Leaflet
  button: En savoir plus
osm: true
---

# Carte OpenStreetMap Responsive

Le thème **Air** permet d'afficher une carte OpenStreetMap interactive directement en bas de page.

## Deux modes de configuration

### 1. Mode Multi-marqueurs interactifs (recommandé)

Définissez une liste de marqueurs (`osm_markers`) avec coordonnées, titres, descriptifs et liens optionnels dans votre `hugo.yaml` ou dans le front matter :

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

La carte s'ajuste automatiquement (`fitBounds`) pour afficher l'ensemble des marqueurs avec un niveau de zoom optimal.

### 2. Mode Iframe (export standard OSM ou uMap)

Si vous préférez une carte issue d'un iframe OSM ou uMap :

```yaml
params:
  osm_url: https://www.openstreetmap.org/export/embed.html?bbox=3.02%2C50.62%2C3.07%2C50.66&layer=mapnik&marker=50.6439%2C3.0504
```

### Activation sur la page

Ajoutez simplement `osm: true` dans le front matter Markdown :

```yaml
---
title: Ma page
osm: true
---
```
