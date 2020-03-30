# Predicting ICU Survival Rate Leveraging NLP-based Machine Learning Pipelines
 Udacity Data Scientist Nanodegree Capstone Project
 
 Ronghui Zhou, Ph.D.

Predicting ICU Survival Rate within 30 Days Leveraging NLP-based Machine Learning Pipelines_final.ipynb

Report on Medium: https://medium.com/@RonghuiZhou/icu-survival-rate-within-30-days-leveraging-natural-language-processing-a0d8fcaeecde

1. Introduction
Project Overview
This project will outline how to select a patient cohort, clean the data for exploratory visualization and building a classification model to predict the mortality within 30 days after ICU admission, utilizing initial caregivers’ notes.

Problem Statement
The goal is to identify potential high risk patients and try to predict the possibility of survival within 30 days after the ICU admission. If the chance is low, actions should be taken to intervene.

Data Set
https://mimic.physionet.org/

MIMIC-III (Medical Information Mart for Intensive Care III) is a large, freely-available database comprising deidentified health-related data associated with over forty thousand patients who stayed in critical care units of the Beth Israel Deaconess Medical Center between 2001 and 2012.

The database includes information such as demographics, vital sign measurements made at the bedside (~1 data point per hour), laboratory test results, procedures, medications, caregiver notes, imaging reports, and mortality (both in and out of hospital).
MIMIC is made available largely through the work of researchers at the MIT Laboratory for Computational Physiology and collaborating research groups.

MIMIC-III, a freely accessible critical care database. Johnson AEW, Pollard TJ, Shen L, Lehman L, Feng M, Ghassemi M, Moody B, Szolovits P, Celi LA, and Mark RG. Scientific Data (2016). DOI: 10.1038/sdata.2016.35.
Available at: http://www.nature.com/articles/sdata201635

Metrics
We will evaluate the performance of machine learning models based on accuracy and confusion matrix.
Classification report shows the metrics: precision, recall, f1-score, and support.

2. Patient Cohort & Data Preparation
Patient Cohort

In this project, ICU patients in the age range 18 to 100 will be selected.
Database Setup: PostgreSQL
https://mimic.physionet.org/tutorials/install-mimic-locally-windows/
Installing MIMIC-III in a local Postgres database on Windows
Note that before proceeding with this guide you will need to:
a. Download the MIMIC-III Clinical Database
b. Extract the MIMIC-III Clinical Database as .csv files somewhere on your local computer
c. Download the PostgreSQL scripts — only the files which end in .sql are required
Note: I tried to install gzip and 7-zip and added to the path, but didn’t work. So I installed cygwin which worked for me.
https://cygwin.com/install.html
