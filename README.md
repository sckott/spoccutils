mapr
====



[![R-check](https://github.com/ropensci/mapr/workflows/R-check/badge.svg)](https://github.com/ropensci/mapr/actions/)
[![cran checks](https://cranchecks.info/badges/worst/mapr)](https://cranchecks.info/pkgs/mapr)
[![codecov](https://codecov.io/gh/ropensci/mapr/branch/master/graph/badge.svg)](https://codecov.io/gh/ropensci/mapr)
[![rstudio mirror downloads](https://cranlogs.r-pkg.org/badges/mapr?color=FAB657)](https://github.com/metacran/cranlogs.app)
[![cran version](https://www.r-pkg.org/badges/version/mapr)](https://cran.r-project.org/package=mapr)


Helper for making maps of species occurrence data, including for:

* [spocc](https://github.com/ropensci/spocc)
* [rgbif](https://github.com/ropensci/rgbif)
* and some `sp` classes

This package has utilities for making maps with:

* base R
* ggplot2
* Leaflet - via `leaflet` pkg
* GitHub Gists - via `gistr` package

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
dat <- occ(query = spp, from = 'gbif', has_coords = TRUE, limit = 50)
map_leaflet(dat)
```

![leafletmap](http://f.cl.ly/items/3l3e0g3l031e212u0W3G/Screen%20Shot%202016-05-01%20at%2012.32.05%20PM.png)

### Github gist


```r
dat <- fixnames(dat)
map_gist(dat, color = c("#976AAE","#6B944D","#BD5945"))
```

![gistmap](http://f.cl.ly/items/343l2G0A2J3T0n2t433W/Screen%20Shot%202014-02-09%20at%2010.40.57%20PM.png)

### ggplot


```r
map_ggplot(x, "usa")
```

![ggplot2](http://f.cl.ly/items/1k2a012u1F1H1E13370U/Screen%20Shot%202015-07-02%20at%203.21.31%20PM.png)

### Base R plots


```r
map_plot(dat, size = 1, pch = 10)
```

![basremap](http://f.cl.ly/items/2J3d1z1t0U3r410o2T3d/Screen%20Shot%202015-07-02%20at%202.57.04%20PM.png)

### via dismo

if that's your jam, though you might find `rgbif` easier


```r
library("dismo")
g <- gbif('Batrachoseps', 'luciae', geo = TRUE, end = 300)
map_leaflet(g, lon = "lon", lat = "lat", name = "scientificName")
```

![dismomap](http://f.cl.ly/items/2u2V0n0B3Y2y0p1d0f1M/Screen%20Shot%202016-01-22%20at%204.46.12%20PM.png)

## Meta

* Please [report any issues or bugs](https://github.com/ropensci/mapr/issues).
* License: MIT
* Get citation information for `mapr` in R doing `citation(package = 'mapr')`
* Please note that this package is released with a [Contributor Code of Conduct](https://ropensci.org/code-of-conduct/). By contributing to this project, you agree to abide by its terms.

[![ropensci_footer](http://ropensci.org/public_images/github_footer.png)](https://ropensci.org)
