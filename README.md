# UAS data processing
This is a workflow for UAS data processing and the database management in the Center for Geospatial Analytics at NCSU
The database is stored on the [google drive](https://drive.google.com/open?id=0B1AfQGDB8tPXfi1pbXJzWUd4Y21sb2ZhZ1ZmYmF0VS0zVnlPRGJoZTdpRC1kRkN1TkgtLWc)
The host is jajezior@ncsu.edu (UAS/uav_timeseries), this folder is accesible (to view) for anyone in the .ncsu.edu domain.
Requests for viewing/editing direct to jajezior@ncsu.edu
### Steps for preserving consistency in the UAS database
* The workflow for the processing is described in the processing_workflow.md file
* The workflow for the GRASS processing (generating DSM for hydrological modeling) on fatra - see GRASS processing folder

# Database structure 
- data is organized in folders **YYYY_MM_DD** (where **YYYY** = year, **MM** = month, **DD** = day)
- In each folder, there is a subfolder **flight_data** containing 
  - imagery (pictures captured by UAS) and 
  - a flight log

### The usual outputs include:
*	**DSM** - DSMagi_YYYY_MM_DD.tif
*	**Orthophoto** - ortho_YYYY_MM_DD_.tif
*	**Pointcloud** - YYYY_MM_DD_points.las
*	**Model** - model_YYYY_MM_DD.zip
*	**Processing report** - report_YYYY_MM_DD.pdf


For the outputs that have been chosen for further analysis (because of the quality of the outputs and suitability for modeling) there are **packed files ready to upload to GRASS**
* **orthophoto** ortho_YYYY_MM_DD.pack 
  * full extent, fine resolution 0.1m
* **DSM** - DSMagi_YYYY_MM_DD.pack
  * full extent, fine resolution 0.15m
* **DSM (interpolated)** - hydroDSM_YYYY_MM_DD.pack 
  * limited extent, the same for all DSMs, resolution: 0.3m
  * for the workflow for interpolation refer to file
* **DSM (interpolated, trees removed)** - hydroDSM_YYYY_MM_DD_DSM_notrees.pack* 
  * limited extent, the same for all DSMs, trees removed for hydrological modeling, resolution: 0.3m
  *  for the workflow for interpolation refer to file
