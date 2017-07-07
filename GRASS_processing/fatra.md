# Working on fatra
#### log in 
`ssh jajezior@fatra.cnr.ncsu.edu -X`

#### Launch GRASS
`grass-trunk`
# fatra - local - fatra (copying files)
in  the terminal on the **local** machine

## local -> fatra

#### orthophoto 
* `scp /media/jajezior/540ECB340ECB0E44/simwe/orthophotos/ortho_YYYY_MM_DD.tif jajezior@fatra.cnr.ncsu.edu:orthophotos/ortho_YYYY_MM_DD.tif`
#### pointcloud 
* `scp /media/jajezior/540ECB340ECB0E44/simwe/pointclouds/points_YYYY_MM_DD.las jajezior@fatra.cnr.ncsu.edu:pointclouds/points_YYYY_MM_DD.las`
#### DSMagi 
* `scp /media/jajezior/540ECB340ECB0E44/simwe/DSMagi/DSMagi_YYYY_MM_DD.tif jajezior@fatra.cnr.ncsu.edu:DSMagi/DSMagi_YYYY_MM_DD.tif`

## fatra -> local
#### orthophoto  
* `scp jajezior@fatra.cnr.ncsu.edu:orthophotos/ortho_YYYY_MM_DD.pack** /media/jajezior/540ECB340ECB0E44/simwe/orthophotos/ortho_YYYY_MM_DD.pack`

#### hydroDSM
* `scp jajezior@fatra.cnr.ncsu.edu:DEMS/hydroDSM_YYYY_MM_DD.pack /media/jajezior/540ECB340ECB0E44/simwe/DEMS/hydroDSM_YYYY_MM_DD.pack`
* `scp jajezior@fatra.cnr.ncsu.edu:DEMS/hydroDSM_YYYY_MM_DD_notrees.pack /media/jajezior/540ECB340ECB0E44/simwe/DEMS/hydroDSM_YYYY_MM_DD_notrees.pack`

#### DSM 
* `scp jajezior@fatra.cnr.ncsu.edu:**???** /media/jajezior/540ECB340ECB0E44/simwe/DSMagi/DSMagi_YYYY_MM_DD.tif`
