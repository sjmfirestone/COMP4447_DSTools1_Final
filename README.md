# Bursting the Bubble
#### COMP-4447: Data Science Tools 1
#### Final Project

## Description

The purpose of this notebook is to explore housing pricing collected and analyze by Zillow and compare it to the US Census' household median income data.
This analysis aims to see if there are any similiarities between today's housing market standings against the infamous 2008's housing market crash.

---

## Table of Contents

1. [Purpose](#purpose)
2. [Background](#background)
    * [Methodology](#methodology)
    * [Definitions](#definitions)
        * [Linux](#linux)
        * [Windows](#windows)
3. [Installation](#installation)
    * [Install Jupyter Notebook](#install-jupyter-notebook)
    * [Virtual Environment](#virtual-environment)
    * [Install Libraries](#install-libraries)	 
4. [Usage](#usage)
    * [Setup](#setup)
    * [Jupyter Notebook: Linux Setup With Command Line](#jupyter-notebook:-linux-setup-with-command-line)
    * [VSCode: Linux Setup With Command Line](#vscode:-linux-setup-with-command-line)
    * [Tips](#tips)
5. [Contributors](#contributors)
5. [Appendix](#appendix)
    * [Project Structure & Files](#project-structure--files)
    * [Troubleshooting](#troubleshooting)

---
## Purpose

This repository is the submission for the COMP-4447: Data Science Tools 1 Final Project. This repository was developed by Sammantha Firestone and Jacquelyn Noyes.

The Final Project aims to test our data cleaning and exploratory analysis skills. 

## Background

Currently in the United States, one of the largest economic barriers that exists is the unaffordability of housing. Historically, the average cost of a single-family home was around five times more than that of the average yearly household income; however, in recent years, that ratio has increased to the average house costing over seven times more than the average household income.<br>
The motivation of this analysis was to further understand the disproportionate increase of housing prices compared to household incomes, and see how the current state of the housing market compares to the years leading up to the infamous housing-market crash of 2008. Then we want to ultimately tease out and theorize the questions:<br><br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**Are we in a housing bubble? And if we are, will it burst?**<br>

__Note__: More information on this can be seen in this report by Longtermtrends.net: [Home to Price Income Ratio (US & UK)](https://www.longtermtrends.net/home-price-median-annual-income-ratio/)


### Methodology

>__<u>Household Income<u>__<br>
>The data for median household income was collected from the US Census. The data is organized based on median income per year, from 1984 to 2021, for each state in the United States. There is also a row that shows the median income throughout the years for the entire country.
    
>__<u>Housing Prices<u>__<br>
>The data for the average price of a typical home was collected from Zillow known as the Zillow Home Value Index (ZHVI). This dataset lists the smoothed, seasonally adjusted price of a house based on year and region of the United States. This dataset reflects the typical value for homes in the 35th to 65th percentile range. For a better understanding of the ZHVI, checkout [this guide](https://www.zillow.com/research/zhvi-user-guide/) and/or this [deep-dive into its methodology](https://www.zillow.com/research/zhvi-methodology-2019-deep-26226/). Please note, the ZHVI does NOT represent the "median home value", but instead it is the "typical home value".

>__<u>Data Analysis Approach<u>__<br>
>For this analysis, we will clean and combine the data taken from the above datasets to create a singular data frame that includes median household income and typical house price based on year and state/region. We will then work to visualize the growing gap between household wages and housing market prices, and look at the trends between the housing market today, and the years rising up to the 2008 housing market crash.

### Definitions

<u>Key Dataframes</u>
- **housing_prices**: Raw ZHVI Zillow Housing Data
- **household_income**: Raw US Census Median Household Income data
- **region_prices**: Parsed ZHVI Zillow Housing Data by United States Region
- **region_income**: Parsed US Census Median Household Income data by United States Region
- **income_over_prices**: Median household income over typical house price
- **income_over_prices_regioned**: Median household income over typical price by United States Region
- **iop**: Geo DataFrame versioned copy of the income_over_prices dataframe

---

## Installation

**When running this notebook, ensure that all of the files in the `Data_Analysis_Files` directory is in the same location as the .ipynb file. If it is not in the same directory, you will get an error when pulling in the data files.**


### Install Jupyter Notebook

##### Linux or WSL

Jupyter Notebook or an IDE like VSCode is necessary to run this analysis. Follow the instructions below if you do not have either of these IDES:

1. Ensure your Linux or WSL distribution is up-to-date:

	`sudo apt update && upgrade`

2. If Python 3 is not installed, run the following commands:

	`sudo apt install python3 python3-pip ipython3`
	`sudo apt install python3-pip`

3. Ensure you have Python 3 installed. The following command should not return any errors:

	`python3 --version`


### Virtual Environment

##### Linux or WSL

Setup a Virtual Environment by following these instructions ideally utilizing Linux or WSL:

1. Make sure you have 'virtualenv' installed

    `python -m pip install virtualenv`

2. Enter the project directory
    
    `cd COMP4447_DSTools1_Final`

3. Create a virtual environment named 'env'

    `python -m venv env`
    * To enter the virtual environment: `source env/bin/activate`
    * To exit the virtual environment: `deactivate`

### Install Libraries

##### Linux or Windows (WSL)

1. Enter your virtual environment

    `source env/bin/activate`
    * Your command line prompt should now be preceded by '(env)'

2. Upgrade your pip in the virtual environment if necessary

    `python -m pip install --upgrade pip`

3. Install the libraries required for this project

    `python -m pip install -r requirements.txt`
    * This ensures that your virtual environment is set up to exactly match the creator's environment when the code was written
    * A full list of the python libraries and versions can be found in the requirements.txt file

4. Check that you have, at minimum, the required libraries listed below

    `python -m pip list`

Required Python Libraries:
* [GeoPandas](https://geopandas.org/en/stable/getting_started/install.html/ "GeoPandas")
* [Pandas](https://pandas.pydata.org/ "Pandas")
* [Jupyter](https://pypi.org/project/jupyter/ "Jupyter")
* [Matplotlib](https://matplotlib.org/stable/users/installing/index.html/ "Matplotlib")
* [Seaborn](https://seaborn.pydata.org/installing.html/ "Seaborn")
* [iPython](https://ipython.readthedocs.io/en/stable/install/index.html/ "iPython")

---

## Usage

### Setup

The ideal way to run this file is threw Jupyter Notebook or VSCode.

### Jupyter Notebook: Linux Setup With Command Line

Save the project directory parent folder 'COMP4447_DSTools1_Final' to your local machine. Follow the instructions in [Installation](#installation) to set up your virtual environment and install the required python libraries. The following will open the notebook in a Jupyter Notebook instance:

1. Enter the project directory

    `cd COMP4447_DSTools1_Final`

2. Activate your virtual environment
    
    `source env/bin/activate`

3. Move all files from the 'Data_Analysis_Files' folder to the same directory as 'SJ-JN_BurstingTheBubble.ipynb' file.

    `cp Data_Analysis_Files/* .`

4. Start up an Jupyter Notebook instance with the following command:

    `jupyter notebook`

5. Copy and paste one of the output URLs into a browser

6. Click open the 'SJ-JN_BurstingTheBubble.ipynb' and have fun!

### VSCode: Linux Setup With Command Line

1. Enter the project directory

    `cd COMP4447_DSTools1_Final`

2. Activate your virtual environment
    
    `source env/bin/activate`

3. Move all files from the 'Data_Analysis_Files' folder to the same directory as 'SJ-JN_BurstingTheBubble.ipynb' file.

    `cp Data_Analysis_Files/* .`

4. Start up an Jupyter Notebook instance with the following command:

    `code SJ-JN_BurstingTheBubble.ipynb`

5. The file should be open in the correct kernel (env)! Have Fun!

### Tips

You only need to run each cell once! If you run the same cell multiple times, it may impact final results.

---

## Contributors

* Sammy Firestone (<sammy.firestone@du.edu>)
* Jacquelyn Noyes (<jacquelyn.noyes@du.edu>)

---

## Appendix

### Project Structure & Files

* Additional Files
	* Final Background.docx
	* FinalProject-InitialExploration.ipynb
* Data_Analysis_Files
	* Household_Income.csv
	* Metro_Data_Legacy.csv
	* us-states.json
* README.md
* SF-JN_BurstingTheBubble.ipynb
* requirements.txt


### Troubleshooting

* Check that your Python 3 environment is up to date.
* Restart your virtual environment
* Re-install Python libraries.
* Delete previous virtual environment and create a new one