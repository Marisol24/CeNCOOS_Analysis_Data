# CeNCOOS Analysis Data 
 Last Updated: 2/03/2023

**Background Information**

The data sets for this project contain seawater data collected from 2010-2021 (2020 not in use due to the COVID-19 Pandemic) at the Moss Landing shore station managed by Moss Landing Marine Laboratories, and collected with help from CenCOOs (Central and Northern California Ocean Observing System). This is a collaborative effort that “…enables sustained and coordinated measures, model nowcasts and forecasts, and integrated products to inform decisions about our regional ocean."

CeNCOOS Website: https://www.cencoos.org/

These datasets are comprised of: Temperature, Conductivity, Salinity, Chlorophyll Fluorescence, Beam attenuation, Transmission, Dissolved Oxygen, Dissolved Oxygen Saturation, and pH. 

Data are provided by month in comma-separated value (csv) format on the MLML Seawater Intake Public Data Portal.Data Portal with Seawater Intake Historical Text Data:

 September 2010-Present: http://pubdata.mlml.calstate.edu/seawater/index.php. 

Processed quality-controlled data for each year are archived in binary NetCDF format (format currently used in this project). Path and link below. Must request access from Dr. Thomas  Connolly. Github:tompc35

MLML Shore Station Data>Moss_Landing>netcdf https://drive.google.com/drive/u/3/folders/1kHGUe0LtATtH5veMkt-f35pgTuz2AGWZ


**Useful Links and File Pathways:**

*Note*:Proceed with caution when using Data from March 2020-March 2021, during the pandemic the instruments were unavailable for standard weekly cleaning and maintenance.


My GitHub repository: https://github.com/Marisol24
Path: Marisol24->Repositories->CeNCOOS_Analysis_Data->Data

**Steps to run on a different computer:**

1. MLML Shore Station Data>Moss_Landing>netcdf https://drive.google.com/drive/u/3/folders/1kHGUe0LtATtH5veMkt-f35pgTuz2AGWZ

Visit this drive, select net cdf files as needed. Save into local folder where you can access with Jupyter Lab or other data analysis software. 

Import all functions

2. Follow Data Exploration

All data explorations in this notebook are preliminary graphs are visualized raw data to look at general trends and if there is any lag/issues/oceanographic instrumentation drift.
Use cells as needed to check specific years as needed. 

3. Subsetting with Flags

 The netcdf files used in this project are processed quality-controlled data for each year and archived in binary NetCDF. The flag is represenative of a quality flag indicating data that has no problems based on processed quality contol. The flags used for this project is ==1 noting data is 'good' data. 

Ultimately the choosing of the quality flag is up to discretion of interpreter.

If the interpreter would like a different flag for the subset, simply replace the '==1' with another number. e.g. '==n'
i.e. data array with all qc flags as '==1' 
ii=np.array((df4['temp_flg'] == n) & (df4['sal_flg'] == n) & (df4['fluor_flg'] == n) & (df4['ph_flg'] == n) & (df4['nitrate_flg'] == n) & (df4['do2_flg'] == n))


3. Data Matrix (Corr and Cov)

Creating a new data frame with good flag data and creating a data matrix create (2d array where each column is a variable) that standardizes the data is again under the discretion of the interpreter. Use cells as needed and check the shape of the data with np.shape(). 

4. Factor Loading/Factor Loading Plot

 The columns of this new 'A' matrix are called the factor loadings for each principal component. These new axes we are going to be looking at are based off of waves, winds and tides.The factor loadings define those axes - both the orientation (eigenvector) and the spread of the data across each axis (square root of eigenvalue - which describes the standard deviation).
 
 For the plot, plug in variables as needed. 
 
 5. Principal Component Score
 
 This is the projection of each data vector onto new component axes. It is the new variables created from the original data, based on rotating axes. Each principal component score can be thought of as an "index" of variability in the data. 
 
 6. Time Series for PC's
 
 These time series that can be made with 'tau[:,n]' if are looking at how the variables vary together in time. Just replace the n with component as needed. 
 
 e.g plt.plot(tau[:,1]), is a time series for Principal Component '1'
 
  7. Peiodograms and Periodogram CI's

These are examples of temperature periodograms. The use of window is up the to direction of the interpreter. Use 'ylim' as necessary to focus in or significant peaks in periodogram. 
 
 8. Wind Roses

Packages:
1. %matplotlib inline 
2. from matplotlib import pyplot as plt
3. import matplotlib.cm as cm 
4. from math import pi 
5. !pip install windrose openpyxl
6. from windrose import WindroseAxes


**Sources and Thank You's!**
 
 Thank you to Dr. Tom Connolly, Jason Adelaars, Steven Cunningham, and CeNCOOS for their funding and all others that helped with files and Shore Station Data. 

"The collection and curation of Moss Landing Marine Lab’s (MLML) public data, and the knowledge derived from it, extends the use and value of our research results. Since establishment in 1966, MLML has grown an international reputation for excellence in marine science research and education, and is the second oldest marine lab in the Monterey Bay area. Our public data repositories hold vast quantities of data collected over the course of our 50 year history by Graduate Students, Faculty, and Research Affiliates in subject areas such as Oceanography (CenCOOS, MoBY) and Marine Vertebrate sightings, strandings and mortalities along the Pacific Coast (BeachCOMBERS)."

Sources that have aided in the interpretations of this data:

1.Booth, J. Ashley T. et al. “Natural Intrusions of Hypoxic, Low PH Water into Nearshore Marine Environments on the California Coast.” Continental Shelf Research 45 (2012): 108–115. Continental Shelf Research. Web.

2.Ryan, J. P. et al. “Causality of an Extreme Harmful Algal Bloom in Monterey Bay, California, during the 2014–2016 Northeast Pacific Warm Anomaly.” Geophysical Research Letters 44.11 (2017): 5571–5579. Geophysical Research Letters. Web.

3.Timothy Pennington, J., and Francisco P. Chavez. “Seasonal Fluctuations of Temperature, Salinity, Nitrate, Chlorophyll and Primary Production at Station H3/M1 over 1989-1996 in Monterey Bay, California.” Deep-Sea Research Part II: Topical Studies in Oceanography 47.5–6 (2000): 947–973. Deep-Sea Research Part II: Topical Studies in Oceanography. Web.

4.William J. Emery, Richard E. Thomson, Chapter 5 - Time-series Analysis Methods, Editor(s): William J. Emery, Richard E. Thomson, Data Analysis Methods in Physical Oceanography, Elsevier Science, 2001, Pages 371-567, ISBN 9780444507563, https://doi.org/10.1016/B978-044450756-3/50006-X.
![image](https://user-images.githubusercontent.com/51756657/216740767-9aca26ab-3896-4610-aa04-3a09950e9efc.png)
