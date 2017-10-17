* location: `LakeWheeler`
* mapset:`PERMANENT`
### Importing points
```
g.region n=219657.343931 s=219320.143864 e=637072.65134968 w=636731.851429 
v.in.lidar -r -t -b -o input=**/home/jajezior/pointclouds/points_YYYY_MM_DD.las** output=**xYYYY_MM**
```

### Interpolation
```
v.surf.rst input=**xYYYY_MM@PERMANENT** elevation=hydroDSM_YYYY_MM_DD nprocs=4 tension=20 smooth=1 npmin=80 dmin=0.2 dmax=0.75
```
