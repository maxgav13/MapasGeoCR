## Mapas geologicos de Costa Rica

Los mapas se encuentran en formato de Teselas (MBTiles), por lo que pueden ser accedidos por medio del paquete [`leaflet`](https://rstudio.github.io/leaflet), para mapas interactivos. Los mapas han sido generados por personal de la [Escuela Centroamericana de Geologia](http://geologia.ucr.ac.cr) y del [Centro de Investigacion en Ciencias Geologicas](http://www.cicg.ucr.ac.cr/)

### Ejemplo

```{r}
library(leaflet)
library(leafem)

fuente = '<a href="http://geologia.ucr.ac.cr">Escuela Centroamericana de Geologia, UCR</a>'
tilesCabuya = "http://maxgav13.github.io/MapasGeoCR/cabuya/{z}/{x}/{y}.png"
tilesRioArio = "http://maxgav13.github.io/MapasGeoCR/rioario/{z}/{x}/{y}.png"
leaflet() %>% 
  addTiles(group='OSM') %>% 
  addTiles(urlTemplate = tilesCabuya,
           attribution = paste0('Fuente: ', fuente),
           group = 'Mapas Geo', 
           layerId = 'Cabuya') %>% 
  addTiles(urlTemplate = tilesRioArio,
           attribution = paste0('Fuente: ', fuente),
           group = 'Mapas Geo', 
           layerId = 'Rio Ario') %>% 
  addLayersControl(baseGroups = c('OSM','Mapas Geo'),
                   position = 'topleft') %>% 
  addMouseCoordinates() %>% 
  addScaleBar(position = 'bottomleft',
              options = scaleBarOptions(imperial = F))
```
Imagen de ambos mapas

![](images/ejemplo.png)

Imagen del mapa Cabuya con mayor zoom (detalle)

![](images/ejemplo_cabuya_z14.png)
