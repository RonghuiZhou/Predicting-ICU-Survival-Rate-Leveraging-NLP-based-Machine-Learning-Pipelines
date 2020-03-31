# Predicting ICU Survival Rate Leveraging NLP-based Machine Learning Pipelines
 ### Udacity Data Scientist Nanodegree Capstone Project 
 ##### Ronghui Zhou, Ph.D.

### 1. About this project
    1.1 Jupyterbook is available inside the notebook folder:

Predicting ICU Survival Rate within 30 Days Leveraging NLP-based Machine Learning Pipelines_final_revised.ipynb

    1.2 Library requirement:

This project was developed on Jupyter Notebook with Python 3.7. Please refer to libary_requirement.txt for libraries used in this notebook.

    1.3 Additional report on Medium: 
https://medium.com/@RonghuiZhou/icu-survival-rate-within-30-days-leveraging-natural-language-processing-a0d8fcaeecde

### 2. Introduction  
#### Project Overview 
This project will outline how to select a patient cohort, clean the data for exploratory visualization and building a classification model to predict the mortality within 30 days after ICU admission, utilizing initial caregivers’ notes.

#### Problem Statement 
The goal is to identify potential high risk patients and try to predict the possibility of survival within 30 days after the ICU admission. If the chance is low, actions should be taken to intervene.

#### Data Set 
https://mimic.physionet.org/ 

MIMIC-III (Medical Information Mart for Intensive Care III) is a large, freely-available database comprising deidentified health-related data associated with over forty thousand patients who stayed in critical care units of the Beth Israel Deaconess Medical Center between 2001 and 2012. 

The database includes information such as demographics, vital sign measurements made at the bedside (~1 data point per hour), laboratory test results, procedures, medications, caregiver notes, imaging reports, and mortality (both in and out of hospital).
MIMIC is made available largely through the work of researchers at the MIT Laboratory for Computational Physiology and collaborating research groups. 

MIMIC-III, a freely accessible critical care database. Johnson AEW, Pollard TJ, Shen L, Lehman L, Feng M, Ghassemi M, Moody B, Szolovits P, Celi LA, and Mark RG. Scientific Data (2016). DOI: 10.1038/sdata.2016.35.

Available at: http://www.nature.com/articles/sdata201635

#### Metrics  
We will evaluate the performance of machine learning models based on accuracy and confusion matrix.
Classification report shows the metrics: precision, recall, f1-score, and support.

### 3. Patient Cohort & Data Preparation
#### Patient Cohort

In this project, ICU patients in the age range 18 to 100 are selected.

#### Feature engineering

storetime_order was created based on the order of storetime, this allows me to keep only the initial note after icu admission. Machine learning models are built on the initial note only, neglecting subsequent notes.

    a. Age was calculated based on the difference between icu admission time and date of birth. 

    b. Death age was calculated based on the difference between date of death and date of birth. 

    c. Los_death was calcualted based on the difference between date of death and icu admission time, with number of days as the unit. 

    d. Icustay_order was created based on the order of icu admission time, this allows me to keep only the most recent icu admission. 

#### Abnormalities 
    There are some entries found to have negative los_death, meaning the reported death time is earlier than the icu admission time. These entries are removed from this data set.

### 4. Conclusion & Perspective
This project demonstrated that it is possible to identify high risky patients and predict mortality with pretty good accuracy. Further improvement is possible to utilize biomedical natural language processing packages such as spaCy or SciSpaCy (https://spacy.io/), to understand medical notes more accurately and extract relevant information.

In this project, we haven’t used any lab results and radiology reports. More work needs to be done to incorporate these data to extract meaningful information. Advanced imaging processing techniques and deep learning algorithms might be helpful as well.

Healthcare is directly related with everyone. No matter how healthy you are today, you may interact with the healthcare system in one way or another as you get older or unexpected things can happen to you or your family. With growing digitized healthcare records and data and evolving natural language processing techniques and machine learning algorithms, data science can have a tremendous impact on the human life.

We wish the world without diseases!

### Acknowledgements
MIMIC-III, a freely accessible critical care database. Johnson AEW, Pollard TJ, Shen L, Lehman L, Feng M, Ghassemi M, Moody B, Szolovits P, Celi LA, and Mark RG. Scientific Data (2016). DOI: 10.1038/sdata.2016.35. Available at: http://www.nature.com/articles/sdata201635

