# arcgis-nasa-earthdata
This repository aims to streamline use of NASA Earthdata in ArcGIS. These catalogs and collections within are searchable and presented by NASA using SpatioTemporal Asset Catalog (STAC) API.

## Land Processes Distributed Active Archive Center (LP DAAC)
Initial efforts focus on the Harmonized Landsat Sentinel-2 (HLS v2) data in collections HLSL30_2.0 and HLSS30_2.0 within the LPCLOUD catalog https://cmr.earthdata.nasa.gov/cloudstac This imagery is already cloud-optimized as Cloud-Optimized GeoTIFF. 

The HLS v2 User Guide was instrumental in understanding and managing HLS v2 data in ArcGIS: https://lpdaac.usgs.gov/documents/1698/HLS_User_Guide_V2.pdf (Junchang Ju, Christopher Neigh, Martin Claverie, Sergii Skakun, Jean-Claude Roger, Eric Vermote, Jennifer Dungan)

## Creation of ArcGIS Cloud Storage connection files.
A Python notebook is provided to automate creation of ArcGIS Cloud Storage (ACS) connection files. https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/create-cloud-storage-connection-file.htm These files handle the necessary authentication token refresh requirement when accessing NASA Earthdata.

A free NASA Earthdata account is required and can be created at: https://www.earthdata.nasa.gov/data/earthdata-login

ArcGIS Pro version 3.5.0 and higher is required to create ACS connection files using S3 access protocol. These connections must be creted and used on a virtual machine in AWS colocated with the NASA Earthdata in us-west-2 (Oregon) region. The S3 protocol ACS connections are ideal for large scale visualization and persisting analysis as new datasets.

ArcGIS Pro version 3.5.2 and higher is required to create ACS connection files using HTTPS access protocol. These connections can be made from any machine with an Internet connection. The HTTPS protocol ACS connections are ideal for smaller scale visualization and analysis on-the-fly.  

## ArcGIS Raster Types
Custom Raster Type XML files to use with the HLSL and HLSS imagery. Together they unify HLSL and HLSS items in a common number and order of bands. https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/raster-products-and-raster-types.htm

## ArcGIS Raster Function Templates
Raster Function Teaplate XML files to use with HLS Mosaic Datasets. These empower users to select from a variety of color composites and band indices including a set for dynamic range adjustment and a set for cloud-masking with use of the HLS v2 Fmask quality band. https://pro.arcgis.com/en/pro-app/latest/help/analysis/raster-functions/raster-functions.htm

## Making STAC Connections
ArcGIS Pro provides a graphical user interface for making STAC Connections to browse, search and select item(s) for use in Maps, Scenes and Mosaic Datasets. https://pro.arcgis.com/en/pro-app/latest/help/data/imagery/create-a-stac-connection.htm 

## Automation in HLS Mosaic Dstaset management
A Python ntebook is provided to automate the imagery management steps with HLS v2 data including:
* Query STAC over time and space and writing results into CSV file
* Create Mosaic Dataset with HLS v2 band names
* Add Rasters to Mosaic Dataset using the STAC items CSV file and custom HLS v2 Raster Types
* Add the set of Raster Function Templates
* Enable time in the Mosaic Dataset and apply default Mosaic Dataset properties