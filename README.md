# Ontario-Geographers-Project
In 2023, Canada reported an increase in forest hectares burned from an average of 2.5 million to 16.5 million ha, counting up to 6100 forest firest. Considering the devasting effect it had on the nation, both economically and socially, something needs to be done to understand how and potentially predict when forest fires may occur. This involves thinking outside of the typical human factors,random acts of nature and climate data. Albeight some of these are usefull (especially climate data), we can consider effects from things like forestry trends such as age of forests, tree stand volume and harvesting years. The scope of the project is three fold: <br>
- Develope a general frame work to incorporate climate data, fire data and geotiff files representing various varibales concerning forestry trends to use in a machine learning scope
- Develope visuals to understand the potential impact of certain visuals
- Attempt to develop a predictive model based on generated data <br>

In this project, the data was gathered mostly form the Government of Canada, either directly from their servers or from associated branches such as the [National Forestry Database]() and [National Forestry Inforamtion System]. Most data can be downloaded or requested through servers simply as .csv format and filtered based on the need. On the other hand, the forestry data is mostly generated from LandSat, i.e files are in geotiff format and requires a slighty different approach to gathering and using the data. Here is a brief overview of the code found in this repository, as well as available data and restults.

The goal of the project is to take in all the data, merge them based on the spatial geometry of the aligned geotif, approximate the metrics from 2001 to 2021 (range of our relevant data) and output dataframes that look like this, which can be used for modelling, and visualization:

![FinishDf2](https://github.com/AntoinePepin6/Ontario-Geographers-Project/assets/113490341/1baddfbf-2453-4d0f-acf3-f9eed26260ea)

Each row has a vol, age approximation, a 1 if a fire occur, a 1 if a harvest occured and some climate data from the station nearest to that pixel.

### Overview of Data
#### Data Sources:
1) `Historical Climate Data` - from [url](https://climate.weather.gc.ca/historical_data/search_historic_data_e.html) or [server](https://dd.weather.gc.ca/climate/) <br>
2) `Canada Forest Fire Data` - from [CWFIS Datamart](https://cwfis.cfs.nrcan.gc.ca/datamart) <br>
3) `Canada Forestry Trends` - from [NFIS](https://opendata.nfis.org/mapserver/nfis-change_eng.html) for most recent (2015-2019), from [Gov. Canada](https://open.canada.ca/data/en/dataset/ec9e2659-1c29-4ddb-87a2-6aced147a990) for 2001 & 2011 <br>

#### Data Available:
- `data/source` Here you will find all the raw data available for climate, forest and fires. Some provide external storage links as the source files were very large<br>
- `data/aligned_geotiff_QGIS` Here you will find the aligned, cropped and resampled geotiff files for an Ontario box, with same CRS and 250mx250m granularity<br>
- `data/processed` Here you will find the processed dataframes for all three categories, climate, fire, and Ontario forest data file<br>
- `data/finaldataframes` Here you will find the final dataframes for each year_month used for viz and ml<br>
- `img` Here you will find various folders with vizualization snap shot at each month_year for various metrics, as well as our `workflow pipeline` , our `notebook pipeline` and a pdf of the presentation of the project <br>

### Overview of Notebooks
#### Forest Notebooks
- `Forest Data 1 Geotiff to CSV.ipynb` Notebook that takes in geotiff files and uses [rasterio](https://rasterio.readthedocs.io/en/stable/api/rasterio.io.html) module to output the data in csv format<br>
- `Forest Data 2 Create DataFrames.ipynb` Notebook that takes in the raw .csv files from raster and compiles them into useful DataFrames<br>
- `Forest Data 3 Merge with Forest and Approximate Age_Vol.ipyng` Also acts as as merging notebook, primarily focuses on the approximation of age and volume for each year_month<br>
- `Forest Data 4 Merging Approximations.ipynb` Notebook that takes in all the approximation and information and generates a single DataFrame for each year_month<br>
#### Fire Notebooks
- `Fire 1 Merge Forests to Fires.ipynb` Notebook that takes in fire point data and merges the coordinate grid from Forest Data 2 to it. Then the point fire information is merged back in Forest Data 3. The flow of this merge is presented below and available in the /img/ folder<br>
#### Climate Notebooks
- `Climate Data 1 Download CSV.ipynb` Notebook that scraps json code from the [climate data server](https://dd.weather.gc.ca/climate/) and downloads based on filtered years and location<br>
- `Climate Data 2 Concat and Clean.ipynb` Notebook that cleans and concats all the climate files into one DataFrame to merge on in Nearest Station<br>
- `Climate Data 3 Visuals.ipynb` Notebook that creates visuals for climate data<br>
#### Vizualization
- `Visulization.ipynb` Notebook that creates .png snapshots for different metrics for each year_month based on the final dataframes from `Merging Approximations.ipynb`<br>
- `Video Viz` Notebook that uses [imageio](https://imageio.readthedocs.io/en/stable/) module to generate videos from many .png frames<br>
#### Merging Notebooks
- `Nearest Station Merging` Notebook that merges the climate data onto the final data frames created in Forest Data 4 based on nearest station coordinates<br>
#### Machine Learning
- `Machine Learning 1 Classifier Data Leakage` Notebook that generates a randomforestclassifier based on some training data from our Forest Data 4 dataframes. There is a problem with how this model is set up, and data leakage cause unreliable results. This is explained further in the Notebook.<br>
### Link to Medium Article


### Pipelines/Flows
#### Simplified Pipelin
![Dummy Workflow Pipeline](https://github.com/AntoinePepin6/Ontario-Geographers-Project/assets/113490341/7f96ee52-a9eb-4ef2-a4cb-1d6317d1e58f)

#### Workflow Pipeline
![Workflow Pipeline](https://github.com/AntoinePepin6/Ontario-Geographers-Project/assets/113490341/6e342bb5-13a8-4431-b81c-b0abcfd63a5a)

#### Notebook Pipeline
![NOtebook Pipeline](https://github.com/AntoinePepin6/Ontario-Geographers-Project/assets/113490341/8d79003c-3e52-412f-8523-ce03b6ac4611)

