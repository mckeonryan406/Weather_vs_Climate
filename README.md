# Weather vs. Climate
Created By: Ryan McKeon | Date First Released: 12 February 2020 | Contact: ryan.e.mckeon@dartmouth.edu

This R dashboard uses daily weather station data from the Global Historical Climatology Network to illustrate the difference between weather and climate and also how climate may or may not be changing. This code is run in R using R Markdown and knits a dashboard of visualizations using Flexdashboards.  At the moment the code is static, but by editing the station ID and year variables described below, one can pick any GHCN weather station in the lower 48 states to visualize.  Click the ***weather_vs_climate_dashboard.html*** file in the repo to see an example of the output dashboard for Hanover New Hampshire.

### Running the Code

The code is written in an R Markdown file *(weather_vs_climate_dashboard.Rmd)* which can be run section by section or knit to build a Flex Dashboard that outputs as a .html file.  The only necessary file it requires at a runtime is the *GHCN_Weather_Stations_ALL.txt* file found in the repo. At first, the code is set up to visualize data for Hanover, New Hampshire, but these inputs can be easily changed to any station in the contiguous U.S. and any year in the record. The code requires internet access so that it can reach the GHCN weather data on NOAA servers using functions from the ***rnoaa*** package.   

**Quick Start Steps:**

1. Download *weather_vs_climate_dashboard.Rmd* and *GHCN_Weather_Stations_ALL.txt* and place them in the same directory. Open up RStudio and create a new project pointed at the directory with the two files.
2. Knit the Dashboard for Hanover New Hampshire to run the full code, download data, and generate the dashboard. This will take a minute or two to download and process the weather station data.
3. Check out the plots and pan and zoom around on the Leaflet map.  The Map is dynamic and if you click on a station (colored point) a popup window appears that gives you the Station ID number needed to created a dashboard for that weather station. 

**How to Analyze a Different Location/Year (for daily temperature plotting):**

The two primary variables you are likely to want to change are found in the first code block just below the package imports. Use the map to find a different weather station to analyze by clicking on a point on the map and recording the station ID number.   

- **stationID** = The GHCN ID number for the weather station to be analyzed.  Begins with USC00xxxxxx, Type = Character

- **currentYear** = The year for the daily temperature plot, Type = Integer



### Output

This dashboard (which is saved as a .html file when you "Knit" the R Markdown file) contains one map and six different plots which are explained here:

- **Map of GHCN Weather Stations** - This Leaflet map shows the location of the current station (the blue pin) with all of the possible GHCN weather stations (symbolized by the length of the record for each station) that can be analyzed using this dashboard.  The map is dynamic and the points are clickable, a popup window give the length of the record and the station ID.
- **Monthly Temperature and Precipitation** - This is the classic "Climograph" where average monthly temperature (left Y axis) and precipitation (right Y axis) are displayed together.  This plot averages data over a 30 year period starting in 1981 and ending in 2010 (commonly referred to as the Normal by climate scientists).
- **Data Completeness Matrix** - This tile plot show the data density for the full length of the record for the current weather station.  Every day for the record is represented, where color ranges from blue to red it is showing the daily mean temperature, where gray or white are present means that no temperature data was recorded.
- **Daily Temperature Range** - This plot compares the daily temperature range for a single year (the colorful vertical lines) to the average daily high and low temperature (light gray) and the record high and low temperature observed at the current station (darker gray). Red and blue diamonds indicate when the high or low temperature record was set during the particular year being observed.  
- **Hotness and Coldness Indices** - This pair of plots are based on a recent paper in ***EOS*** https://eos.org/geofizz/hotness-and-coldness-indexes-based-on-the-fahrenheit-scale and illustrate how the intensity and number of hot and cold days are changing over the course of the data record. For the Hotness index, a value of 75 for a particular year means that the maximum daily temperature equalled or exceeded 75 degrees Fahrenheit 75 times during the year. ***If the Hotness index is increasing, both the number of hot days and the temperature on those days is increasing.***  The Coldness index is similar; here a value of 25 means that the minimum daily temperature equalled or exceeded 25 degrees Fahrenheit *below* the freezing point of water (at 32 deg F)  25 times during the year. ***If the Coldness index is dropping year to year, it means that cold days are warmer and less frequent.***  
- **Monthly Mean Temperature Anomaly** - This plot illustrates how the monthly mean temperature from the last 10 years compares to the monthly mean temperature calculated using the full record from the weather station.  The "anomaly" is calculated as the difference between the last 10 years and the full record for each month.













