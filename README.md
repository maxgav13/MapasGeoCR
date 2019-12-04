## Mapas geologicos de Costa Rica

Los mapas se encuentran en formato de Teselas (MBTiles), por lo que pueden ser accedidos por medio del paquete [`leaflet`](https://rstudio.github.io/leaflet), para mapas interactivos.

### Ejemplo

```{r}
library(leaflet)
library(leafem)

fuente = '<a href="http://geologia.ucr.ac.cr">Escuela Centroamericana de Geologia, UCR</a>'
tilesCabuya = "http://maxgav13.github.io/MapasGeoCR/cabuya/{z}/{x}/{y}.png"
leaflet() %>% 
  addTiles(group='OSM') %>% 
  addTiles(urlTemplate = tilesCabuya,
           attribution = paste0('Fuente: ', fuente),
           group = 'Mapas Geo', 
           layerId = 'Cabuya') %>% 
  addLayersControl(baseGroups = c('OSM','Mapas Geo'),
                   position = 'topleft') %>% 
  addMouseCoordinates() %>% 
  addScaleBar(position = 'bottomleft',
              options = scaleBarOptions(imperial = F))
```

