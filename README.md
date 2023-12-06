# Ontario-Geographers-Project
In 2023, Canad reported an increased in forest ha's burned from an average of 2.5 million to 16.5 million ha, counting up to 6100 forest firest. Considering the devasting effect it had on the nation, but economically and socially, something needs to be done to understand how and potentially predict when forest fires may occur. This involves thinking outside of the typical human factors,random acts of nature and climate data. Albeight some of these are usefull (especially climate data), we can consider effects from things like forestry trendsm such as age of forests, tree stand volume and harvesting years. The scope of the project is three fold: <br>
- Develope a general frame work to incorporate together climate data, fire data and geotiff files representing various varibales concerning forestry trends to use in a machine learning scope
- Develope visuals to understand the potential impact of certain visuals
- Develop a predictive model based on generated data <br>

In this project, the data was gathered mosltly form the Government of Canada], either directly from their servers or from associated branches such as the [National Forestry Database]() and [National Forestry Inforamtion System]. Most data can be dowlnoaded or requested through servers simply as .csv format and filtered baesd on the need. On the other hand, the forestry data is mostly generated from LandSat, i.e files are in geotiff format and requires a slighty difference approach to gathering and using the data. Here is a brief overview of the code found in this repository, as well as available data and restults.

### Overview of Data
#### Data Sources:
`Historical Climate Data` - from [url](https://climate.weather.gc.ca/historical_data/search_historic_data_e.html) or [server](https://dd.weather.gc.ca/climate/) <br>
`Canada Forest Fire Data` - from [CWFIS Datamart](https://cwfis.cfs.nrcan.gc.ca/datamart) <br>
`Canada Forestry Trends` - from [NFIS](https://opendata.nfis.org/mapserver/nfis-change_eng.html) for most recent (2015-2019), from [Gov. Canada](https://open.canada.ca/data/en/dataset/ec9e2659-1c29-4ddb-87a2-6aced147a990) for 2001 & 2011 <br>

#### Data Available:
`data/source` Here you will find all the raw data available for climate, forest and fires. Some provide external storage links as the source files were very large<br>
`data/aligned_geotiff_QGIS` Here you will find the aligned, cropped and resample geotiff files for an Ontario box, with same CRS and 250mx250m granularity<br>
`data/processed` Here you will find the processed dataframes for all three categories, a climate, fire and Ontario fores data file<br>
`data/finaldataframes` Here you will find the final dataframes for each year_month used for viz and ml<br>
`img` Here you will find various folders with vizualization snap shot at each month_year for various metrics<br>

### Overview of Notebooks
#### Forest Notebooks
`Forest Data 1 Geotiff to CSV.ipynb` Notebook that takes in geotiff files and uses [rasterio](https://rasterio.readthedocs.io/en/stable/api/rasterio.io.html) module to output the data in csv format<br>
`Forest Data 2 Create DataFrames.ipynb` Notebook that takes in the raw .csv files from raste rand compiles them into usefull DataFrames<br>
`Forest Data 3 Merge with Fores and Approximate Age_Vol.ipyng` Also acts as as merging notebook, primarly focuses on the apporximation of age and volume for each year_month
#### Fire Notebooks


#### Climate Notebooks

#### Vizualization

#### Merging Notebooks


