# Air, a theme for [Hugo](https://gohugo.io/).

The intent of this theme is to provide a solid starting place for Hugo sites with basic features and include best practices for performance, accessibility, and rapid development.

## Live Demo

Just visit [fducat18.github.io/hugo-air-demo](https://fducat18.github.io/hugo-air-demo)

## Local Demo

1. Clone this repository into a folder named `air`:
   ```bash
   git clone https://github.com/fducat18/hugo-air.git air
   ```
2. Enter the folder: `cd air`
3. Run the demo:
   ```bash
   hugo server -s exampleSite --themesDir ../..
   ```


## Features

|    	  Awesome features                                                          |
|---------------------------------------------------------------------------------|       
| ✨ Full **Responsive**                                                          |
| ✨ **Bootstrap** ready                                                          |
| ✨ **Custom Header Image** from page bundle                                     |
| ✨ Shortcode **Image Gallery** from page bundle (Instagram or Masonry Style) 	 |               
| ✨ Page Type **Image Gallery** from page bundle (Instagram or Masonry Style)    |
| ✨ **Single-page** landing homepage   	                                         |
| ✨ Embedded OpenStreetMap & Google Maps                                         |
| ✨ Smooobu Booking **shortcode**      	                                         |
| ✨ **Multilingual** Support shortcode      	                                   |

## Installation

### First Installation: as a git submodule

Install Air Theme as a Git Submodule. Naviguate to the folder of your Hugo site run:

```bash
git submodule add https://github.com/fducat18/hugo-air.git themes/air
```

If you clone a Hugo site that already uses this theme as a submodule, initialize it with:

```bash
git submodule update --init --recursive
```

### Update an existing installation

If you already have Air Theme installed, naviguate to the folder of your Hugo site run: 

```bash
git submodule update --remote --merge
```

## Quick Start with Example Site

To get started quickly with the example content:

1.  Copy the contents of `themes/air/exampleSite/content` to your project's `content` directory.
2.  Copy `themes/air/exampleSite/hugo.yaml` to your project root. **Note:** This will overwrite your existing configuration. If you have existing settings, merge them manually.
3.  The `hugo.yaml` file contains essential configuration for the theme, including:
    - **Menu Structure**: `menu.main` and `menu.footer`.
    - **Theme Params**: `params.mainColor`, `params.osm_url`, `params.gmaps_url`, etc.

## Usage

### Edit your config file

```yaml
baseURL: https://example.com/
languageCode: en-us
title: Example Site
theme: air
params:
  author:
    name: François
    siteUrl: https://notes.ducatillon.net/
  osm_url: https://www.openstreetmap.org/export/embed.html?bbox=-2.4050%2C46.6980%2C-2.3350%2C46.7320&layer=mapnik&marker=46.7141%2C-2.3681
  mainColor: "#386641"
  footer: "Hugo Air theme is great and customizable"
menu:
  main:
  - name: Home 
    url: /
    weight: 20
    params:
      target: 
  - name: Features 
    url: /features
    weight: 30
    params:
      target: 
  - name: Shortcode Gallery
    pageRef: /features/shortcode-gallery/
    parent: Features
    weight: 20
  - name: Landing Page
    url: /landing-page
    weight: 40
    params:
      target: 
  footer:
  - name: Home 
    url: /
    weight: 20
    params:
      target: 

markup:
  goldmark:
    parser:
      attribute:
        block: true
    renderer:
      unsafe: true
```

### Customize main color

In your config file, add:

```yaml
params:
  mainColor: "#386641"
```

This will override the main.scss

```css
/*
=======================================================
=                   CSS Variables                     =
=======================================================
*/

/* 
Main color for the website
It can be overridden in the config file by setting "Params.mainColor" to any color value
*/
:root {
  --main-color: #035c8c; /* default color */
}
```

### Maps Configuration (OpenStreetMap & Google Maps)

Air theme supports embedding interactive maps via **OpenStreetMap** (recommended: lightweight, privacy-friendly, zero external JS) or **Google Maps** (legacy compatibility).

> **Important**: The `osm` and `gmaps` options are **mutually exclusive per page**. Choose one or the other. If both are mistakenly set on the same page, OpenStreetMap takes precedence.

#### 1. OpenStreetMap (Recommended)

You can configure OpenStreetMap in two ways:

##### A. Interactive Map with Markers (Multi-pin Leaflet Map)

Define one or more markers directly in your site configuration (`params.osm_markers`) or in the page front matter:

```yaml
params:
  osm_zoom: 12 # Optional zoom level
  osm_center: [46.715, -2.355] # Optional custom center [lat, lon]
  osm_markers:
    - title: "Quartier Libre"
      lat: 50.643936
      lon: 3.050444
      description: "Espace convivial & culturel au bord de la Deûle — Lille"
      link: "https://www.openstreetmap.org/search?lat=50.643936&lon=3.050444" # optional link in popup
    - title: "Le p'tit quinquin"
      lat: 50.637125
      lon: 3.039490
      description: "Statue et symbole lillois — Square Foch, Lille"
      link: "https://www.openstreetmap.org/search?lat=50.637125&lon=3.039490"
```

Each marker supports:
- `title` (or `name`): popup heading.
- `lat`: latitude.
- `lon` (or `lng`): longitude.
- `description` (or `desc`): optional text shown below title.
- `link` (or `url`): optional URL making the popup title clickable.

When `osm_zoom` is specified, the map uses this explicit zoom level (centered on `osm_center` if provided, or on the barycenter of all markers). If `osm_zoom` is omitted, the map automatically fits the bounds (`fitBounds`) to show all markers at optimal zoom.

##### B. Embed Iframe (Standard OSM Export or uMap)

Alternatively, provide a direct embed URL:

```yaml
params:
  osm_url: https://www.openstreetmap.org/export/embed.html?bbox=-2.4050%2C46.6980%2C-2.3350%2C46.7320&layer=mapnik&marker=46.7141%2C-2.3681
  # or a uMap URL:
  # osm_url: https://umap.openstreetmap.fr/fr/map/my-custom-map_12345
```

##### Enabling the Map

Enable the map in your page front matter:

```yaml
---
title: My Page
osm: true
---
```

You can also override `osm_markers` or `osm_url` per-page directly in the page front matter.

#### 2. Google Maps alternative

1. Set your Google Maps embed URL in your site configuration:

```yaml
params:
  gmaps_url: https://www.google.com/maps/d/u/0/embed?mid=...
```

2. Enable Google Maps in your page front matter:

```yaml
---
title: My Page
gmaps: true
---
```

### Customizing Favicon

To change the favicon of your site:

1.  Use your favicon or generate it using [favicon.io](https://favicon.io/).
2.  Copy the generated file (e.g. `favicon.ico`) to your `static/` directory.

### Setup Google Analytics 

In your config file, add:

```yaml
services:
  googleAnalytics:
  id: G-12345  #Replace with your Google Analytics ID
```

### Image Gallery

#### Use as partial
In your `.md` file, specify the type of the page with `type: gallery-masonry` or  `type: gallery-insta` like this:

```yaml
---
title: Air is a great hugo theme
type: gallery-masonry
---
Air is a great hugo theme with outstanding features like image gallery from page bundle
```

#### Use as shortcode

Assuming your folder structure would look something like this

```yaml
content/
└── pages/
    └── my-page/                # Page Bundle
        ├── index.md            # Page content
        ├── featured-image.jpg  # Image Resource used as gallery image 1
        ├── card.jpg            # Image Resource used as gallery image 2 AND as card featured image
        ├── photo1.jpg          # Image Resource used as gallery image 3
        ├── photo2.jpg          # Image Resource used as gallery image 4
        └── photo3.jpg          # Image Resource used as gallery image 5
```

In your `.md` file, add this block to display your instagram image gallery

`{{` `< gallery-masonry page="my-page" >` `}}` 


where "my-page" is the page bundle object passed as a variable to the shortcode

Alternatively, use instagram gallery style with

`{{` `< gallery-insta page="my-page" >` `}}`

### Custom Header image

Add one image called `featured-image.jpg` in your page bundle.

#### Use as a featured header image in `single.html`
Automatically loaded as a header image on your page

##### Use the default featured header image
Automatically loaded from the `static/img` folder.
- `header-960.jpg` for screens higher than 960px
- `header-480.jpg` for screens lower than 960px

### Custom Bootstrap Card image

#### Use as featured card image in `list.html`
When listing pages/posts, it displays bootstrap cards with a thumbnail image.  
By default it uses the card image from  `static/img/card.jpg`
Customize the card image by adding one image called `featured-image.jpg` or `card.jpg ` in your page bundle.  

### Single-page landing homepage

Add pages to a folder. These page will render as a single-page.

Example with this page bundle:

```yaml
content/
└── landing-page/
    └── page-1/                 # Page Bundle
        ├── featured-image.jpg  # 
        ├── index.md            # Page 1
    ├── _index.md               # File that calls the landing-page type
    ├── page-2.md               # Page 2
    ├── page-3.md               # Page 3
    ├── page-4.md               # Page 4
    └── page-5.md               # Page 5
```

Edit your  `content/landing-page/_index.md` to add `type: landing-page`

```yaml 
---
title: Landing Page
catchline: Awesome One Page Landing Page
type: landing-page
---
```

Add a weight to each page to render them by weight ✨: 

```yaml
---
title: Page 1
weight: 10
---
Content of Page 1
```

## Theme Development

If you are developing this theme inside a Hugo site (usually in `themes/air`), remember that this is a **Git submodule**.

### Making changes
1. Enter the theme directory: `cd themes/air`
2. Ensure you are on the main branch: `git checkout main`
3. Make your changes, then commit and push from within the theme directory:
   ```bash
   git add .
   git commit -m "Your feature"
   git push origin main
   ```
4. Go back to your Hugo site root and update the theme pointer:
   ```bash
   cd ../..
   git add themes/air
   git commit -m "Update theme pointer"
   git push origin main
   ```

## Screenshot

 ### Mobile
![screenshot](https://fducat18.github.io/hugo-air/img/hugo-air-theme-mobile.jpg)
 
 ### Desktop
![screenshot](https://fducat18.github.io/hugo-air/img/hugo-air-theme-desktop.jpg)
