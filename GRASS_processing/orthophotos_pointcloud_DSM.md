# GRASS processing - orthophoto DSM and pointcloud upload and saving 
If the data is chosen for further investigation (hydrological modeling) on fatra, the processing will be executed on linux 
### Move the outputs to the folder accessible from linux 
* orthophoto `simwe/orthophotos/media/jajezior/540ECB340ECB0E44/simwe/orthophotos/`
* DSM `simwe/DSMagi/media/jajezior/540ECB340ECB0E44/simwe/DSMagi`
* pointcloud `simwe/pointclouds/media/jajezior/540ECB340ECB0E44/simwe/pointclouds`

## LINUX
  
### Packing Agisoft generated outputs (GRASS on linux)
#### orthophoto
* mapset `orthophotos` res=~0.03m 
* working directory `/home/jajezior/orthophotos`
```
r.in.gdal
r.composite red=ortho_YYYY_MM_DD.red@orthophotos green=ortho_YYYY_MM_DD.green@orthophotos blue=ortho_YYYY_MM_DD.blue@orthophotos output=ortho_YYYY_MM_DD 
g.remove -f type=raster name=red=ortho_YYYY_MM_DD.red@orthophotos,ortho_YYYY_MM_DD.green@orthophotos,ortho_YYYY_MM_DD.blue@orthophotos 
```
```
r.null map=ortho_YYYY_MM_DD@orthophotos setnull=0
r.pack input=ortho_YYYY_MM_DD@orthophotos
```
#### DSM

### GRASS processing workflow
for the creation of high resolution DSM by interpolation from pointcloud, refer to GRASS processing folder
* [fatra setting and copying](https://github.com/inioslawa/UAS_data_processing/blob/master/GRASS_processing/fatra.md)
* [interpolating high resolution DSM from pointcloud](https://github.com/inioslawa/UAS_data_processing/blob/master/GRASS_processing/interpolation.md)
* [removing trees for hydrological modeling](https://github.com/inioslawa/UAS_data_processing/blob/master/GRASS_processing/removing_trees.md) 
* packing the outputs



