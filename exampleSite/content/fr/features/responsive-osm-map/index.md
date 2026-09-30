---
title: Carte OpenStreetMap Responsive
date: 2026-09-30T10:00:00+02:00
draft: false
tags: ['osm','map']
params:
  catchline: Intégration OpenStreetMap légère et respectueuse de la vie privée
  button: En savoir plus
osm: true
---

# Carte OpenStreetMap Responsive

## Usage

Configurez l'URL OSM dans votre fichier de configuration Hugo et activez la carte dans le front matter de votre page Markdown.

### Fichier de configuration Hugo

Ajoutez votre URL d'embed OpenStreetMap (ou uMap) :

```yaml
params:
  osm_url: https://www.openstreetmap.org/export/embed.html?bbox=-2.4050%2C46.6980%2C-2.3350%2C46.7320&layer=mapnik&marker=46.7141%2C-2.3681
```

### Front matter de la page Markdown

Ajoutez `osm: true` dans le fichier Markdown :

```yaml
---
title: Ma page
osm: true
---
```
