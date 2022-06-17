# Landsat8-satellite-scenes
### If you are looking to access landsat 8 scenes in an automated way, the code above can help you.

The code is designed to specifically request NDVI indices, but can be changed to look for other specific bands. The main flow of the code is as follows:
* Read a shapefile of the region of interest and extract its boundaries (the minimum and maximum of longitude and latitude).
* Access the [EROS API](https://m2m.cr.usgs.gov/) and use the shapefile boundaries to describe the Minimum bounding rectangle (MBR) and fetch all the scenes that cover the region in a time interval specified. There is a loop in this part that has been used to traverse the region over the years and find the combination of scenes with the least cloud cover, but the loop can be removed..
* The scene list is passed to the [ESPA API](https://espa.cr.usgs.gov/) which will request the scenes. The EROS API also generates Scene Download orders, but the ESPA API delivers spectral indices (NDVI, EVI...).
* When all the scenes are processed, the download can be done using the script made available by ESPA itself. After all scenes are downloaded, the .tiff file containing the NDVI band is extracted from each downloaded scene.

To access the EROS and ESPA API, [create a USGS account](https://ers.cr.usgs.gov/register) is required.
