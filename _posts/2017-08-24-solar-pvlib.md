---
published: false
layout: post
tags:
  - solar
  - pvlib
---
## A New Post

import os
import pandas as pd
import numpy as np
import pvlib
from pvlib.pvsystem import PVSystem
from pvlib.location import Location
from pvlib.modelchain import ModelChain
from pvlib.modelchain import basic_chain

def importPSMData():
    df = pd.read_csv('C:\\Users\\mtcraig\\Documents\\NSRDBData\\dd\\622240_30.77_-99.3_tmy.csv',skiprows=[0,1])
    #Rename paramters for input to PVlib
    df.rename(columns={'DHI':'dhi','DNI':'dni','GHI':'ghi','Temperature':'temp_air',
                        'Wind Speed':'wind_speed'},inplace=True)
    #Rename date parameters in order to run to_datetime
    df.rename(columns={'Year':'year','Month':'month','Day':'day','Hour':'hour',
                        'Minute':'minute'},inplace=True)
    df['dt'] = pd.to_datetime(df[['year', 'month', 'day', 'hour', 'minute']])
    #Set index to DT for run_model call
    df.set_index(df['dt'],inplace=True)
    #Drop unnecessary columns
    df = df.drop('Dew Point', 1)
    df = df.drop('Pressure', 1)
    df = df.drop('year', 1)
    df = df.drop('month', 1)
    df = df.drop('day', 1)
    df = df.drop('hour', 1)
    df = df.drop('minute', 1)
    df = df.drop('dt',1)
    return df

sandia_modules = pvlib.pvsystem.retrieve_sam('SandiaMod')
cec_inverters = pvlib.pvsystem.retrieve_sam('cecinverter')

module = sandia_modules['BP_Solar_BP3220N_Module___2010_'] #18% eff, c-Si
inv = cec_inverters['ABB__ULTRA_1100_TL_OUTD_3_US_690_x_y_z_690V__CEC_2013_']
system = PVSystem(module_parameters=module,inverter_parameters=inv,surface_azimuth=180,
                    modules_per_string=23,strings_per_inverter=9897)

loc = Location(latitude=30.77,longitude=-99.3,tz='Etc/GMT+7',altitude=500)

mc = ModelChain(system,loc,name='test',
            orientation_strategy='south_at_latitude_tilt') 

weatherData = importPSMData()
mc.run_model(times=weatherData.index,weather=weatherData)
print(mc.ac)
