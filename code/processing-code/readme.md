---
editor_options: 
  markdown: 
    wrap: sentence
---

THE FINAL CODE USED FOR THE DATA CLEANING IS processingcodemz \# processing-code

This script outlines the step-by-step cleaning and preparation of SEER data for analysis.
Below is a high-level summary of the transformations applied:

#Data Loading

Loaded the raw dataset from a CSV file using readr::read_csv().
Loaded the codebook to understand variable definitions.
Initial Data Inspection

Used glimpse(), summary(), head(), and skimr::skim() to get an overview of the dataset.

#Data Cleaning Steps

##Fixed Data Types

Converted Year of diagnosis, RX Summ--Surg Prim Site (1998+), and Patient ID to character (since they are categorical).
Converted Survival months to numeric for proper analysis.

##Converted Categorical Variables to Factors

Transformed variables such as Sex, Race, Metastasis Indicators, Survival Flags, and Cause-Specific Death Classification into factor format to ensure categorical consistency.

##Filtered Patients Based on Age

Excluded patients in the age categories "01-04 years" and "15-19 years" to focus on the relevant population.
Included Only Stage IVA and IVB Patients

Filtered the dataset to retain only patients classified under Stage IVA and IVB in Derived AJCC Stage Group, 7th ed (2010-2015).

##Excluded Patients Based on Cause-Specific Death Classification

Removed patients with "Dead (missing/unknown COD)" and "N/A not seq 0-59" from SEER cause-specific death classification.

##Removed Patients with Missing Survival Data

Ensured Survival months is not missing (NA) to maintain analytical integrity.

#Final Dataset Assignment

Assigned the fully cleaned dataset to processeddata for future use.

#Saved Cleaned Data

Stored the cleaned dataset as an RDS file (processeddata.rds) using saveRDS(), which preserves data types and structures.
Provided references on best practices for data storage.
Notes on Data Handling

Documented that removing patients with missing data is one approach, but other imputation or handling strategies might be considered depending on the research question.
