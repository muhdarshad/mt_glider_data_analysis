# Glider Flight Data Analysis

## Description
The aim of the project is to detect, analyse, classify and visualize thermal lift regions from the previous
glider flight data. This folder houses the runnable notebooks, reusable modules, conversion utilities, and derived data products that power the glider flight analysis workflow.

**Layout**
- `Glider_Flight_Data_Analysis_v7.ipynb` – notebook to parse, load, clean and analyse previous glider flight data
- `Raw_data/` – accomodates previous glider flight data from LARUS devices (f37 format) and igc exports from weglide.org (FLARM data).
- `Results/` – stores dataframes, summarized results, plots, and KML exports of flight paths.
- `larus_to_df.py` – tool that converts Larus sensor dumps into typed pandas DataFrames saved next to the source file.

## Visuals
Plots used for in-depth visualization are exported into `Results/plots/`. Include captions that describe the flight ID and the metric being validated.

## Installation
**Requirements**
- Python 3.10+
- `pip` or `conda`
- Access to the private telemetry bundle under `Raw_data/`

**Steps**
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r ../01_ENV/requirements.txt
# or: conda env create -f ../01_ENV/FSR_ENV3.yml
```

## Usage
1. Add previous glider flight data into `Raw_data` folder. Classify into different folders based on the format of the file.
2. Set mode in the code such that to select the type of the file used for analysis.
3. Rename the Larus data in the following format according to the naming scheme in weglide `YYYY-MM-DD PilotName FlightID`.
4. Fine tune the code with the help of the second cell in the notebook which is used for setup and configuration. This cell also controls which plots or results to generate.
5. Find all the outputs in the `Results` folder.

## Roadmap
- `Glider_Flight_Data_Anlaysis` focuses on the basic package for data analysis plots and visualization, summarization of performance characteristics of flight paths, especially during the thermalling regions
- Newer versions will focus on building a machine learning program to predict the performance for a defined flight parameter

## Authors and Acknowledgment
Maintained by the Institute of Flight Systems and Automatic Control (FSR) of Technical University of Darmstadt. Thanks to the pilots  who collected and curated the flight data.
