# google drive database
* Create the **YYYY_MM_DD** folder and **Flight_data** at google drive 
* Download **imagery** and **flight log** to the **Flight_data** subfolder
  - if needed, convert the .jxl file (flight log) to .txt using the [**jxl2csv.py**](https://github.com/wenzeslaus/jxl2csv.git) script

# Agisoft processing 
Data is processed in [Agisoft PhotoScan Professional](http://www.agisoft.com/downloads/installer/). 
* Geographical settings (ESPG: 
* Loading photos
* Aligning photos (accuracy: low)
* Placing the markers
* Batch processing:
```
  - Optimize alignment
  - Build point cloud
  - Generate Mesh
  - Generate Texture
  - Build DEM
  - Build orthophoto
```
* Export the outputs (name accordingly to the [database structure](https://github.com/inioslawa/UAS_data_processing/blob/master/README.md)): 
  * orthophoto (.tif),
  * DSM (.tif),
  * pointcloud (.las),
  * model (.zip containing .obj and .jpg texture)
  * report (.pdf)

# 3D model to sketchfab 
upload the model to the [osgeolab skechfab account](https://sketchfab.com/osgeolab) (exported .zip file or directly from PhotoScan)
  * login:`jajezior@ncsu.edu`
  * password:`osgeolab`
  
# GRASS processing 
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
refer to GRASS processing folder
* fatra setting and copying
* interpolating high resolution DSM from pointcloud
* removing trees for hydrological modeling 
* packing the outputs


