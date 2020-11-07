# SC Dev
> ABMI Science Centre development website

[science.abmi.ca](https://science.abmi.ca)

Latest data summaries and model results for review before publishing on
[data portal](https://www.abmi.ca/data).

2585 species and counting:

- lichens: 262
- mosses: 312
- vascular plants: 1328
- soil mites: 279
- birds: 258
- mammals: 43
- habitat elements: 45

## Review process

Mammals and birds are reviewed on an _opt in_ basis, meaning that we only present
results for species where we are confident in the models due to higher scrutiny for these
species. Other groups are _opt out_, meaning that we do not present results for species
where we are not confident.

1. Organize results on the development website
2. Identify and notify internal and external reviewers
3. Conduct review (Disqus, ClickUp)
4. Finalize species lookup tables
5. Update dev website and package result for handoff (tabular outputs and maps).

## Implementation

The website is built on [Vue](https://vuejs.org/) and [Nuxt](https://nuxtjs.org/)
using the [Vuetify](https://vuetifyjs.com/) component library.
See [`package.json`](package.json) for version information.

The static page generation utilizes dynamic routes based on the
[species API](https://science.abmi.ca/results/reports/2020/images/index.json).
Pages consume the data fetched from the API.
The TOC pages for each species group and the individual species pages
use their own components to display the information and images.

The species pages contain a comments section.
Comments by species can be reviewed [here](https://disqus.com/home/forums/abmisc/).

## JSON API

### API root

`https://science.abmi.ca/results/reports/2020/images/`

The JSON blob at the API root contains the `taxa` and `species` properties.
`taxa` lists the species groups (as displayed in the left drawer of the web app).
`species` lists the individual species (all taxa combined).

### Taxon endpoint

`https://science.abmi.ca/results/reports/2020/images/${taxon}/`

The taxon endpoint lists all the species within a particular taxon only
(see [example](https://science.abmi.ca/results/reports/2020/images/mammals/index.json)).

### Species endpoint

`https://science.abmi.ca/results/reports/2020/images/${taxon}/${species}/`

The species endpoint lists the images (results) available
for a particular species (see [example](https://science.abmi.ca/results/reports/2020/images/mammals/Coyote/index.json)).

### Images

The images listed in the species blob can be found at the same path
as the species endpoint:

- `det.png`: detection map
- `useavail-north.png` and `useavail-south.png`: use-availability
- `coef-north.png`, `coef-south.png`: land cover associations
- `sector-north.png`, `sector-south.png`: sector effects
- `pred.png`: predictive maps

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```
