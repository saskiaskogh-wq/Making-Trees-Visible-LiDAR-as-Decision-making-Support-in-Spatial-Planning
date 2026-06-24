Making Trees Visible: LiDAR as Decision-making Support in Spatial Planning
R scripts for ALS-based individual tree detection and DBH screening in peri-urban landscapes. Implements vwf (ForestTools) and li2012 (lidR) with grid search parameter optimisation. Developed for a spatial planning context in Helsingborg, Sweden.
This code accompanies the following work:

Skogh, S. (2026). Making Trees Visible: LiDAR as Decision-making Support in Spatial Planning. Master's thesis, Swedish University of Agricultural Sciences. https://stud.epsilon.slu.se/22247/


Repository structure
ScriptDescription02_vwf_detection.RHeight normalisation, CHM generation, and vwf tree detection with default parameters03_vwf_grid_search.RGrid search parameter optimisation for vwf across reference plots04_li2012_detection.RHeight normalisation and li2012 point cloud-based tree detection with default parameters05_li2012_grid_search.RGrid search parameter optimisation for li2012 across reference plots

Accuracy assessment (buffer-based TP/FP/FN matching) and DBH crown area classification (Standard / High Value / Protected tiers) were conducted in ArcGIS Pro and are not included in this repository.


Note: Script names above are approximate — please verify against the actual filenames in this repository.


Dependencies
The following R packages are required:
rinstall.packages("lidR")
install.packages("ForestTools")
install.packages("sf")
install.packages("terra")
PackageVersion usedReferencelidR4.2.2Roussel et al. (2023)ForestTools[version unknown — please check]Plowright (2026)sf[version unknown — please check]—terra[version unknown — please check]—

Note: Please add the exact package versions you used. You can retrieve them with packageVersion("lidR") etc.


Data
The ALS point cloud used in this study was collected on behalf of the City of Helsingborg in April–May 2025 (point density ~25 pts/m², SWEREF99 TM / RH2000). This dataset is not publicly available and is owned by the City of Helsingborg.
To run these scripts on your own data, you will need:

A classified ALS point cloud in LAS/LAZ format
A field-validated tree inventory for accuracy assessment (optional but recommended)
Coordinate system compatible with your study area


Usage

Note: Detailed usage instructions, including expected input formats and parameter settings, should be added here by the author. The scripts were developed and validated on the Helsingborg dataset described above and may require adaptation for other datasets or coordinate systems.

General workflow:

Run 02_vwf_detection.R or 04_li2012_detection.R for initial detection with default parameters — both scripts include height normalisation and CHM generation
Run 03_vwf_grid_search.R or 05_li2012_grid_search.R to optimise parameters for your reference plots
Export detected treetops and crown polygons to GIS software for accuracy assessment and DBH classification

Optimised parameters from this study:

vwf: slope = 0.05, intercept = 3.0, minHeight = 5 m
li2012: dt1 = 7.0, dt2 = 9.0, Zu = 10, R = 2, hmin = 5, speed_up = 10

These parameters were optimised for mixed deciduous broadleaved vegetation in a peri-urban agricultural landscape in southern Sweden and may not transfer directly to other vegetation types or regions.

Citation
If you use these scripts in your work, please cite both the paper and the code:
Paper:

Skogh, S. (2026). Making Trees Visible: LiDAR as Decision-making Support in Spatial Planning. Master's thesis, Swedish University of Agricultural Sciences. https://stud.epsilon.slu.se/22247/

Code:

Skogh, S. (2026). Making Trees Visible — R scripts for ALS-based tree detection and DBH screening. GitHub. https://github.com/saskiaskogh-wq


Algorithm references

vwf: Popescu, S.C. & Wynne, R.H. (2004). Seeing the Trees in the Forest: Using Lidar and Multispectral Data Fusion with Local Filtering and Variable Window Size for Estimating Tree Height. Photogrammetric Engineering and Remote Sensing, 70(5), pp. 589–604.
li2012: Li, W., Guo, Q., Jakubowski, M.K. & Kelly, M. (2012). A New Method for Segmenting Individual Trees from the Lidar Point Cloud. Photogrammetric Engineering & Remote Sensing, 78(1), pp. 75–84.
lidR package: Roussel, J-R., Auty, D., Herold, M. & Dalponte, M. (2023). lidR: Airborne LiDAR Data Manipulation and Visualization for Forestry Applications. R package version 4.2.2.
ForestTools package: Plowright, A. (2026). ForestTools: Tools for Analyzing Remote Sensing Forest Data.
