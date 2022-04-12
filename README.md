# AirPIT
Created by the Spring 2020 MSFC Washington Health &amp; Air Quality project. This tool displays particulate matter, nitrogen dioxide, sulfur dioxide, carbon monoxide, formaldehyde,  methane, and ozone concentrations in the Pacific Northwest region of the United States. Users can select a region and dates of interest, and display pollutants for those. 

Date Created: April 7, 2020

This tool displays particulate matter, nitrogen dioxide, sulfur dioxide, carbon monoxide, formaldehyde, 
methane, and ozone concentrations in the Pacific Northwest region of the United States. Users can select a region and dates of interest, and display pollutants for those. 

 Required Packages
===================
* Google Earth Engine access
* No other assets are required


 Parameters
-------------
1. User must have a Google Earth Engine account. To request an
account, go to https://earthengine.google.com and click on "Sign Up Now." (link last accessed on April 7, 2020)
2. Enter the code into the Google Earth Engine code editor (https://code.earthengine.google.com). Click "save" to maintain a personal copy of the code. Click "run" to launch the AirPIT tool. User may need to click "run" twice to make the tool load.
3. Click the "close" button on the introduction panel to clear the panel.
4. Click the "Pollutants" button in the bottom left corner of the map to display the tool control panel.
5. Choose a location/zoom level from the drop-down menu at the top of the tool control panel. There are three options - Puget Sound, Washington State, and Pacific Northwest. Please note that because PM2.5 data has only been validated within Washington State, PM2.5 data outside of that region may be less accurate.
6. Choose a pollutant from the buttons on the tool control panel. The map will display data for that pollutant for two weeks before the present date. Data is displayed in the units micrograms/m^3 for all pollutants except methane, which is displayed in ppm. Please note that the "Particulate Matter" layer only displays AOD at this stage, and not predicted PM2.5 values. The pixel colors do not reflect the exact parameters of the EPA Air Quality Index; to change that, go to step 11.
7. Choose a date to display from the date slider at the bottom of the tool control panel. The map will display data for a two-day range starting with the date selected. Any layers previously visible on the map will disappear, and user must reselect a pollutant from the tool control panel to visualize it for their chosen dates. Please note that PM2.5 estimates are only available for dates in June, July, August, and September. For dates outside of those months, the map layer will not display PM2.5, and an error message will appear in the Console tab above the map display.
8. The "Layers" panel in the upper right section of the map display can be used to toggle pollutant map layers on or off by clicking on the checkboxes next to the pollutant names. It is possible to display more than one pollutant at once by selecting more than one checkbox at a time. The sliders to the right side of the pollutant names can be used to adjust the opacity of the map layers. 
9. The basemap is automatically set to "Satellite." To change the basemap, click on one of the buttons in the upper right corner of the map display. The other available basemaps are "Map" and "SoftGrey."
10. To identify the values of specific pixels in the map imagery, navigate to the Inspector tab above the map display and to the right of the code. Then click on the pixel in question. The Inspector tab will display the available data for the pixel. The first line gives the latitude and longitude values for the selected pixel. The "Pixels" category lists the pixels for each layer in the map, including the layers not currently in the display. Clicking the down arrow next to each layer name in the "Pixels" category shows a second line for each layer. The numerical value in those lines is the concentration of the pollutant for that layer in the selected pixel. Concentrations are in micrograms/m^3, except for methane, which is in ppm.
11. To adjust the visualization of the pollutants so that the colors
match the EPA Air Quality Index ratings (good, moderate, unhealthy, etc), choose a date in the date slider and adjust the syntax in lines 493 through 501 as follows. There are no EPA AQI guidelines for methane and formaldehyde, so this adjustment is not possible for those pollutants.
  var layers = [
    ui.Map.Layer(ee.Image(newPM).sldStyle(PM_sld_intervals), {}, 'Particulate Matter', false),
    ui.Map.Layer(newNOXConvertedUnits.sldStyle(NOX_sld_intervals), {}, 'Nitrogen Dioxide', false),
    ui.Map.Layer(newCOConvertedUnits.sldStyle(CO_sld_intervals), {}, 'Carbon Monoxide', false),
    ui.Map.Layer(newHCHOConvertedUnits, HCHO_viz, 'Formaldehyde', false),
    ui.Map.Layer(newCH4, CH4_viz, 'Methane', false),
    ui.Map.Layer(newO3ConvertedUnits.sldStyle(O3_sld_intervals), {}, 'Ozone', false),
    ui.Map.Layer(newSO2ConvertedUnits.sldStyle(SO2_sld_intervals), {}, 'Sulfur Dioxide', false),
  ];
To revert back to the original symbology to make it possible to view concentration values as in step 10, adjust the syntax in lines 493 through 501 as follows.
  var layers = [
    ui.Map.Layer(ee.Image(newPM), PM_viz, 'Particulate Matter', false),
    ui.Map.Layer(newNOXConvertedUnits, NOX_viz, 'Nitrogen Dioxide', false),
    ui.Map.Layer(newCOConvertedUnits, CO_viz, 'Carbon Monoxide', false),
    ui.Map.Layer(newHCHOConvertedUnits, HCHO_viz, 'Formaldehyde', false),
    ui.Map.Layer(newCH4, CH4_viz, 'Methane', false),
    ui.Map.Layer(newO3ConvertedUnits, O3_viz, 'Ozone', false),
    ui.Map.Layer(newSO2ConvertedUnits, SO2_viz, 'Sulfur Dioxide', false),
  ];


 Contact
---------
Name: Amiya Kalra
E-mail: ack.lmno@yahoo.com

 Programmers
-------------
Amiya Kalra
Ray Deininger

 Other Team Members (did not participate in coding)
-----------------------------------------------------
Richard Murray
Rachel Earwood
***
