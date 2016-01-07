mapr
====



[![Build Status](https://api.travis-ci.org/ropensci/mapr.png)](https://travis-ci.org/ropensci/mapr)
[![Build status](https://ci.appveyor.com/api/projects/status/3tyojycmeqmj2pcw?svg=true)](https://ci.appveyor.com/project/sckott/mapr)
[![codecov.io](https://codecov.io/github/ropensci/mapr/coverage.svg?branch=master)](https://codecov.io/github/ropensci/mapr?branch=master)
[![rstudio mirror downloads](http://cranlogs.r-pkg.org/badges/mapr?color=FAB657)](https://github.com/metacran/cranlogs.app)

Helper for making maps of species occurrence data, including for:

* [spocc](https://github.com/ropensci/spocc)
* [rgbif](https://github.com/ropensci/rgbif)

This package has utilities for:

* Making maps, with:
    * base R
    * ggplot2
    * Leaflet
    * GitHub Gists
    * ...

## Installation

Install `mapr`


```r
install.packages("mapr", dependencies = TRUE)
```

Or the development version from GitHub


```r
devtools::install_github("ropensci/mapr")
```


```r
library("mapr")
library("spocc")
```

## Make maps

### Leaflet


```r
spp <- c('Danaus plexippus', 'Accipiter striatus', 'Pinus contorta')
dat <- occ(query = spp, from = 'gbif', has_coords = TRUE)
map_leaflet(dat, dest = ".")
```

![leafletmap](http://f.cl.ly/items/3w2Y1E3Z0T2T2z40310K/Screen%20Shot%202014-02-09%20at%2010.38.10%20PM.png)

### Github gist


```r
dat <- fixnames(dat)
map_gist(dat, color = c("#976AAE","#6B944D","#BD5945"))
```

![gistmap](http://f.cl.ly/items/343l2G0A2J3T0n2t433W/Screen%20Shot%202014-02-09%20at%2010.40.57%20PM.png)

### ggplot2 family maps

#### ggmaps


```r
ecoengine_data <- occ(query = 'Lynx rufus californicus', from = 'ecoengine', limit = 100)
map_ggmaps(ecoengine_data)
```

![ggmaps](http://f.cl.ly/items/1L3r0b3k1W2o1Z3j2I3r/Screen%20Shot%202015-07-02%20at%202.55.59%20PM.png)

#### ggplot


```r
map_ggplot(ecoengine_data, "usa")
```

![ggplot2](http://f.cl.ly/items/1k2a012u1F1H1E13370U/Screen%20Shot%202015-07-02%20at%203.21.31%20PM.png)

### Base R plots


```r
map_plot(dat, cex = 1, pch = 10)
```

![basremap](http://f.cl.ly/items/2J3d1z1t0U3r410o2T3d/Screen%20Shot%202015-07-02%20at%202.57.04%20PM.png)

## Meta

* Please [report any issues or bugs](https://github.com/ropensci/mapr/issues).
* License: MIT
* Get citation information for `mapr` in R doing `citation(package = 'mapr')`
* Please note that this project is released with a [Contributor Code of Conduct](CONDUCT.md). By participating in this project you agree to abide by its terms.

[![ropensci_footer](http://ropensci.org/public_images/github_footer.png)](http://ropensci.org)