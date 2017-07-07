* mapset `PERMANENT` res=0.3 
* working directory `/home/jajezior/DEMS`

###### create a mask with lidar DEM for the areas with trees
	r.mapcalc --overwrite "lidarDEM_region_trees = midpines_lidar_DEM_2015"

## FOR EACH MAP

##### Set the small region (trees surroundings) 
`g.region n=219417.34388346 s=219402.64388052 e=637011.45136396 w=636986.25136984`

##### create a difference map
`r.mapcalc --overwrite "testdiff = YYYY_MM - lidarDEM_region_trees"`

##### leave only areas with the trees (the rest should be null)
* `r.mapcalc --overwrite "trees = if(testdiff>1,2,null())"
* `r.mapcalc --overwrite "trees2 = if(testdiff<(-0.2),2,null())"`
* `r.patch --overwrite input=trees@PERMANENT,trees2@PERMANENT output=trees`

##### check if the layer is not empty --> of it is = no trees visible, no removal needed
`r.univar trees`

##### come back to the previous region	
`g.region n=219657.343931 s=219320.143864 e=637072.65134968 w=636731.851429`

##### create a buffer (4 cells around =1.2m)
`r.grow --overwrite input=trees output=trees_grow radius=4 new=3`

##### create a mask with the values of DEM
`r.mapcalc "xYYYY_MM_lidar_trees = if(isnull(trees_grow),null(), midpines_lidar_DEM_2015)"`

##### make a hole in the UAS DEM
`r.mapcalc "vYYYY_MM* = if(isnull(xYYYY_MM_lidar_trees),YYYY_MM,null())"`

##### create an overlap
`r.grow --overwrite input=x**2015_06**_lidar_trees output=lidar_trees_grow radius=12 new=1`
`r.mapcalc "vYYYY_MM_lidar_trees_grow = if(isnull(lidar_trees_grow), null(), midpines_lidar_DEM_2015)"`

##### patch lidar and UAS 
`r.patch.smooth input_a=vYYYY_MM input_b=vYYYY_MM_lidar_treesgrow output=YYYY_MM_patch smooth_dist=5`

##### pack BOTH outputs
* `r.pack input=YYYY_MM_patch output=hydroDSM_YYYY_MM_DD_notrees.pack` 
* `r.pack input=YYYY_MM output=hydroDSM_YYYY_MM_DD.pack`
##### remember to copy it from fatra to local ([see how](https://github.com/inioslawa/UAS_data_processing/blob/master/GRASS_processing/fatra.md))
