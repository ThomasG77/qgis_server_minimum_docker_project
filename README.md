Recipe mainly borrowed from https://github.com/3liz/py-qgis-server/blob/master/docker/README.md

```bash
docker run -p 8080:8080 \
       -v $pwd:/projects \
       -e QGSRV_SERVER_WORKERS=2 \
       -e QGSRV_LOGGING_LEVEL=DEBUG  \
       -e QGSRV_CACHE_ROOTDIR=/projects \
       -e QGSRV_CACHE_SIZE=10 \
       3liz/qgis-map-server:3.10.14-1.3.4
```


GetCapabilities http://localhost:8080/ows/?SERVICE=WMS&VERSION=1.1.0&REQUEST=GetCapabilities&MAP=atlas_minimum

GetProjectSettings http://localhost:8080/ows/?SERVICE=WMS&VERSION=1.1.0&REQUEST=GetProjectSettings&MAP=atlas_minimum

GetMap http://localhost:8080/ows/?MAP=atlas_minimum&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetMap&BBOX=-2561502.687626393978,3197812.441460153088,2617067.113106171135,7131874.009898217395&CRS=EPSG:3857&WIDTH=878&HEIGHT=667&LAYERS=OpenStreetMap,ne_110m_admin_0_countries,ne_110m_populated_places&STYLES=,,&FORMAT=image/jpeg&DPI=192&MAP_RESOLUTION=192&FORMAT_OPTIONS=dpi:192

GetPrint http://localhost:8080/ows/?MAP=atlas_minimum&SERVICE=WMS&VERSION=1.3.0&REQUEST=GetPrint&FORMAT=pdf&EXCEPTIONS=application/vnd.ogc.se_inimage&TRANSPARENT=true&SRS=EPSG:3857&DPI=100&TEMPLATE=layout_no_atlas&map0:extent=-2561502.687626393978,3197812.441460153088,2617067.113106171135,7131874.009898217395&map0:scale=2500000&map0:LAYERS=atlas_minimum&map0:STYLES=default&LAYERS=OpenStreetMap,ne_110m_admin_0_countries,ne_110m_populated_places&STYLES=default&OPACITIES=255

If you want atlas functionnality, clone the plugin in a directory https://github.com/3liz/qgis-atlasprint and use QGSRV_SERVER_PLUGINPATH variable to tell where to look for the plugin. Then look at the plugin doc to understand how to use it.
