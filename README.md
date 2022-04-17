# CeNCOOS_Analysis_Data updated, 4/17/2022

Background Information

There is a Scientific and Industrial Seawater and Intake Pipe that brings in water from the bay, as seen below in Figure 1 and then dispersed throughout MLML, MBARI and Phil's Restaurant for various purposes. The water is brought through the pump house (the pump house located just onshore of the intake pipe) where the sensors and oceanographic instruments are all housed and maintained.  All instruments are configured in such (e.g raspberry pies) so that the oceanographic information being collected can then be read into a computer and be seen on the MLML public data portal interface as time series data in real time.

The data sets used represent seawater data collected from 2010-2019, (2020 not in use due to the COVID-19 Pandemic) and 2021 at the Moss Landing shore station managed by Moss Landing Marine Laboratories. These datasets are comprised of temperature, conductivity, salinity, chlorophyll fluorescence, beam attenuation, transmission, dissolved oxygen, dissolved oxygen saturation, and pH. Data are provided by month in comma-separated value (csv) format. Processed quality-controlled data for each year are archived in binary NetCDF format which is the format I will be using in this project. 

This data was collected with help by CenCOOs, which is the Central and Northern California Ocean Observing System. This is a collaborative effort that “…enables sustained and coordinated measures, model nowcasts and forecasts, and integrated products to inform decisions about our regional ocean."

This shore station time series data is important because knowing what the bay’s rhythms are may help describe overall trends and patterns of the organisms that live in the bay. It can also aid scientists and policy makers about what future work needs to be done in order to best preserve the bay as well. Looking at and exploring trends in time series is almost like detective work where you have patterns and you need to look at them to find out what’s actually happening below the surface in such a complex system. Knowing what happens in terms of these parameters can inform biologists of blooms or it can let people at MLML know when there is a possible big anoxic event about to occur (e.g. to switch tanks for experiments being done in the aquarium if it will be harmful to animals). 







Raw data used in this Notebook is from: http://pubdata.mlml.calstate.edu/seawater/index.php and from MLML Shore Station Data>Moss_Landing>netcdf https://drive.google.com/drive/u/3/folders/1kHGUe0LtATtH5veMkt-f35pgTuz2AGWZ

My GitHub repository is: https://github.com/Marisol24
And the path is Marisol24->Repositories->CeNCOOS_Analysis_Data->Data

These datasets are comprised of temperature, conductivity, salinity, chlorophyll fluorescence, beam attenuation, transmission, dissolved oxygen, dissolved oxygen saturation, nitrate, and pH. 
Data are provided by month in comma-separated value (csv) format on http://pubdata.mlml.calstate.edu/seawater/index.php. Processed quality-controlled data for each year are archived in binary NetCDF format which is what is used for this project. 
MLML Public Data Portal with all Seawater Intake Historical Text Data: September 2010-Present(excluding Cornona Virus Shutdown). Procees with Caution when using Data from March 2020 onward.

Steps to run on a different computer:

1. MLML Shore Station Data>Moss_Landing>netcdf https://drive.google.com/drive/u/3/folders/1kHGUe0LtATtH5veMkt-f35pgTuz2AGWZ

Visit this drive, select net cdf files as needed. Save into local folder where you can access with Jupyter Lab or other data analysis software. 

Import all functions

2. Follow Data Exploration

All data explorations are with raw data at first to look at general trends and if there is any lag/issues/oceanographic instrumentation drift.
Use cells as needed to check specific years as needed. 

3. Subsetting with Flags

 The netcdf files used in this project are processed quality-controlled data for each year and archived in binary NetCDF. The flag is represenative of a quality flag indicating data that has no problems based on processed quality contol. The flag used for this project is ==1. 

Ultimately the choosing of the quality flag is up to discretion of interpreter.

If the interpreter would like a different flag for the subset, simply replace the '==1' with another number. e.g. '==n'
ii=np.array((df4['temp_flg'] == n) & (df4['sal_flg'] == n) & (df4['fluor_flg'] == n) & (df4['ph_flg'] == n) & (df4['nitrate_flg'] == n) & (df4['do2_flg'] == n))


3. Data Matrix (Corr and Cov)

Creating a new data frame with good flag data and creating a data matrix create (2d array where each column is a variable) that standardizes the data is again under the discretion of the interpreter. Use cells as needed and check the shape of the data with np.shape(). 

4. Factor Loading/Factor Loading Plot

 The columns of this new A matrix are called the factor loadings for each principal component. These new axes we are going to be looking at are based off of waves, winds and tides.The factor loadings define those axes - both the orientation (eigenvector) and the spread of the data across each axis (square root of eigenvalue - which describes the standard deviation).
 
 For the plot, plug in variables as needed. 
 
 5. Principal Component Score
 
 This is the projection of each data vector onto new component axes. It is the new variables created from the original data, based on rotating axes. Each principal component score can be thought of as an "index" of variability in the data. 
 
 6. Time Series for PC's
 
 These last time series that can be made with 'tau[:,n]' are looking at how the variables vary together in time. Just replace the n with component. 
 
 e.g plt.plot(tau[:,1]), is a time series for Principal Component 1

7. Sources and Thank You's!
 
 Thank you to Dr. Tom Connolly, Jason Adelaars, CeNCOOS for their funding and all others that helped with files and Shore Station Data. 
 "The collection and curation of Moss Landing Marine Lab’s (MLML) public data, and the knowledge derived from it, extends the use and value of our research results. Since establishment in 1966, MLML has grown an international reputation for excellence in marine science research and education, and is the second oldest marine lab in the Monterey Bay area. Our public data repositories hold vast quantities of data collected over the course of our 50 year history by Graduate Students, Faculty, and Research Affiliates in subject areas such as Oceanography (CenCOOS, MoBY) and Marine Vertebrate sightings, strandings and mortalities along the Pacific Coast (BeachCOMBERS)."
 
MLML Public Data Portal: http://pubdata.mlml.calstate.edu/index.php

CeNCOOS Website: https://www.cencoos.org/

1.	Booth, J. Ashley T. et al. “Natural Intrusions of Hypoxic, Low PH Water into Nearshore Marine Environments on the California Coast.” Continental Shelf Research 45 (2012): 108–115. Continental Shelf Research. Web.

2.	Ryan, J. P. et al. “Causality of an Extreme Harmful Algal Bloom in Monterey Bay, California, during the 2014–2016 Northeast Pacific Warm Anomaly.” Geophysical Research Letters 44.11 (2017): 5571–5579. Geophysical Research Letters. Web.

3.	Timothy Pennington, J., and Francisco P. Chavez. “Seasonal Fluctuations of Temperature, Salinity, Nitrate, Chlorophyll and Primary Production at Station H3/M1 over 1989-1996 in Monterey Bay, California.” Deep-Sea Research Part II: Topical Studies in Oceanography 47.5–6 (2000): 947–973. Deep-Sea Research Part II: Topical Studies in Oceanography. Web.

4. William J. Emery, Richard E. Thomson, Chapter 5 - Time-series Analysis Methods, Editor(s): William J. Emery, Richard E. Thomson, Data Analysis Methods in Physical Oceanography, Elsevier Science, 2001, Pages 371-567, ISBN 9780444507563, https://doi.org/10.1016/B978-044450756-3/50006-X.
