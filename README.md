# Calibrating-implicit-volatility-surface-with-Deutsche-Boerse-A7
_Canari.dev (www.canari.dev), Jan-2021_

How to retrieve options intraday data from Deutsche Boerse A7 and calibrate a volatility surface.

**This project showcases the possibilities offered by the API of Deutsche Boerse's A7 service.
You will need a valid A7 subscription to run it.
For this, please go to :
https://www.mds.deutsche-boerse.com/mds-en/analytics/A7-analytics-platform
Once you have been registered as a A7 user, connect to the A7 website in order to get an API token :
https://a7.deutsche-boerse.com/
After logging in, click on the face icon next to your name on the top right of the page and then select API Token generation.

A general example of how to retrieve data from the API is given at https://deutsche-boerse.github.io/a7/usecases/02_simple_rdi.html

The Trades_Dynamics Jupyter Notebook provided here provided here build on the knowledge shown in this usecase to retrieve all data from each relevant option for a designated underlying and the calibrate a volitility surface.
This volatility can then be shown as a time series or used in more advances examples such as :
https://github.com/canari-dev/Trades-Dynamics-with-Deutsche-Boerse-A7
https://github.com/canari-dev/Timing-Disperions-Strategies-with-Deutsche-Boerse-A7
https://github.com/canari-dev/Defining-Idiosyncratic-Volatility-with-Deutsche-Boerse-A7

You will need a Python 3.8 interpreter with the following packages :
- QuantLib
- numpy, pandas
- math, datetime, matplotlib
- sklearn, scipy
- requests, warnings

You will also need to download the python files provided in this git :
DateAndTime.py, PricingAndCalibration.py, SetUp.py

A7 allows you to preprocess the data in a fast and efficient way. This will both drastically reduce the volume of data that you will need to import through the API and fasten the process as the preprocessing will run as a C++ code on Deutsche Boerse's servers.
The API environnement on A7 website helps you design your preprocessing code (see doc on A7 website after loggin in). You can subsequently download and upload this code in a ".yml" format.
For the purpose of this git, we have designed a simple preprocessing code saved as minsize_level_tb.yml, available in the "code" folder of this git.
It retains the Top Of Book (TOB, ie. first limit) of the order book, provided that the quantity available is more than a pre defined threshold. If not, it averages limit prices until finding the min quantity.

This file must be loaded in your A7 environnement though A7 website prior to running the notebook.


Here is the kind of graph that you can generate. (More details in the Jupyter Notebook)


Vol Calibration:

![plot](./images/Vol_Calibration.png)


Market Prices vs Faire Prices

![plot](./images/Fair_Prices.png)
