# google drive database
* Create the **YYYY_MM_DD** folder and **Flight_data** at google drive 
* Download **imagery** and **flight log** to the **Flight_data** subfolder
  - if needed, convert the `.jxl` file (flight log) to `.txt` using the [**jxl2csv.py**](https://github.com/wenzeslaus/jxl2csv.git) script

# Agisoft processing 
Data is processed in [Agisoft PhotoScan Professional](http://www.agisoft.com/downloads/installer/). 
Projects are saved at shared NGAT drive [\\cnrdata.cnr.ncsu.edu\NGAT\NgatData\LW\JJ\projects](\\cnrdata.cnr.ncsu.edu\NGAT\NgatData\LW\JJ\projects)
* Geographical settings `(ESPG: 3358)`
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
  
