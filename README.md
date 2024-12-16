# COVID-19 Pandemic Analysis

This project analyses COVID-19 case rates, hospitalisation rates, and death rates across the United States during five key pandemic waves (2020–2023). It also explores state-level variations and the impact of vaccination coverage on COVID-19 outcomes.

# Repository Structure 
├── code/                  # Contains all R scripts for data wrangling and analysis  
│   ├── final-project.qmd  # Quarto file for rendering the final report  
│   ├── data-wrangling.R   # Script for cleaning and preparing datasets  
│   └── analysis.R         # Code for statistical analysis and visualisations  
├── data/                  # Processed and raw data  
│   ├── clean/             # Cleaned datasets ready for analysis  
│   └── raw/               # Original datasets (raw files)  
├── docs/                  # Final outputs (HTML, PDF)  
├── raw-data/              # Supplementary or backup raw data  
└── README.md              # Project instructions and details  

# Data Sources

The data utilised in this project is sourced from reliable public APIs and government datasets:
	1.	US Census Bureau API: State-level population estimates (2020–2023).
	•	API Endpoint: Census Population API
	2.	CDC COVID-19 API:
	•	Cases: https://data.cdc.gov/resource/pwn4-m3yp.json
	•	Hospitalisations: https://data.cdc.gov/resource/39z2-9zu6.json
	•	Deaths: https://data.cdc.gov/resource/r8kw-7aab.json
	•	Vaccinations: https://data.cdc.gov/resource/rh2h-3yt2.json
	3.	Manual Population Data: Raw census file: NST-EST2023-ALLDATA.csv
	
# Installation Instructions

To reproduce the project, ensure you have the following software and R packages installed:

Software:
	•	R (version ≥ 4.0)
	•	Quarto (for rendering final-project.qmd)

R Packages:

Install required libraries using:
install.packages(c("tidyverse", "janitor", "stringr", "httr2", "zoo", "RColorBrewer", "lubridate"))  

# Steps to Reproduce

Follow these steps to reproduce the analysis and generate the final report:
	1.	Clone the Repository:
git clone https://github.com/your-repo-name.git  
cd your-repo-name  
	2.	Prepare the Data:
Run the script to clean and process the population and COVID-19 datasets:
source("code/data-wrangling.R")  
	3.	Run the Analysis:
Perform statistical analyses and create visualisations:
source("code/analysis.R")  
	4.	Generate the Report:
Render the final report using Quarto:
quarto render code/final-project.qmd  
	5.	Outputs:
The final report (HTML or PDF) will be generated in the docs/ directory.

# Key Results
	•	Analysis of COVID-19 trends across five pandemic waves, including cases, hospitalisations, and deaths.
	•	State-level disparities in death rates over time and across waves.
	•	Evaluation of COVID-19 virulence (Case Fatality Ratio and Hospitalisation-to-Death Ratio) and its decline over time.
	•	Strong negative correlation between vaccination coverage and death rates across all waves.
	
# Supplementary Information

Additional visualisations and results are included in the supplementary section of the report:
	•	Figure S1: COVID-19 Cases, Deaths, and Hospitalisations Over Time.
	•	Figure S2: Hospitalisation-to-Death Ratio (HDR) Over Time by Wave.
	•	Figure S3: State-Level Comparison of HDR by Wave.
	•	Figure S4: Rolling Averages of Cases, Deaths, and Hospitalisations.

These figures further support the main findings and provide deeper insight into trends observed during the analysis.
	
