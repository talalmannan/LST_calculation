Land Surface Temperature (LST) calculation using Google Earth Engine

This code demonstrates how to calculate LST from a Landsat 8 image using Google Earth Engine (GEE). It also shows how to create an interactive map using the geemap library and display the calculated LST on the map.
Prerequisites

    You need to have a GEE account and be authenticated to use the API.
    You need to install the following libraries:
        ee (Google Earth Engine Python API)
        pandas
        geemap

Inputs

    A Landsat 8 image. In this code, the image is obtained from the Landsat 8 TOA image collection and filtered based on the date range and ROI.
    A shapefile defining the region of interest (ROI). In this code, the shapefile is loaded using the geemap.shp_to_ee() function and converted to an Earth Engine FeatureCollection.

Outputs

    An interactive map showing the calculated LST for the ROI.
    A dictionary containing the calculated LST values, with keys being the pixel coordinates and values being the LST values. This is obtained using the getInfo() method on the LST image.
    
        
Steps

    Initialize and authenticate the GEE API.
    Create an interactive map using the geemap.Map() function.
    Define the ROI using the drawing tool provided by the interactive map.
    Load the shapefile defining the ROI and convert it to an Earth Engine FeatureCollection.
    Filter the Landsat 8 image collection based on the date range and ROI.
    Clip the image to the ROI using the clip() method.
    Add the RGB bands of the image to the map using the addLayer() method.
    Define a function process_image() to calculate LST from the input image. The function performs the following steps:
        Calculate Top of Atmosphere (TOA) Radiance using the Band 10 temperature values.
        Calculate Brightness Temperature (BT) using the TOA Radiance values.
        Calculate Normalized Difference Vegetation Index (NDVI) using the Band 5 and Band 4 values.
        Calculate the minimum and maximum NDVI values for the ROI.
        Calculate Proportion of Vegetation (PV) using the NDVI values and the minimum and maximum NDVI values for the ROI.
        Calculate Land Surface Emissivity (LSE) using the PV values.
        Calculate LST using the Band 10 temperature values and the LSE values.
        Add the LST band to the input image and return the modified image.
    Apply the process_image() function to the input image and store the result in a variable.
    Extract the LST values from the image using the select() and getInfo() methods    Define a visualization dictionary for the LST band, specifying the minimum and maximum values and a color palette.
    Add the calculated LST band to the interactive map using the addLayer() method.

Notes

    The LST calculation is based on the method described in the paper "A New Method for Estimating Land Surface Temperature from Landsat 8 Data" by Qihao Weng et al. (2014).
    The visualization dictionary can be customized according to your preference.
    The ROI can also be defined using a point or a bounding box, in addition to the shapefile used in this code.
    The code can be modified to process multiple images and create an animation or a time series analysis.
    This project is licensed under the MIT License. This means that you are free to use, modify, and distribute the software, as long as you include the original copyright notice and the license's disclaimer in all copies or substantial portions of the software.