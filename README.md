# CeNCOOS_Analysis_Data so far, 6-26-2020

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
