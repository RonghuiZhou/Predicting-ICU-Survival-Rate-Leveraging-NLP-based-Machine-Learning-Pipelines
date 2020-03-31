# <div align="center"> Predicting ICU Survival Rate Leveraging NLP-based Machine Learning Pipelines</div>
 ### <div align="center"> Data Scientist Nanodegree on [Udacity](https://www.udacity.com/course/data-scientist-nanodegree--nd025): Capstone Project</div>
 ##### <div align="center"> Author: [Ronghui Zhou](https://www.linkedin.com/in/ronghuizhou/); March 30, 2020</div>

### 1. About this project
#### 1.1 Jupyterbook is available inside the notebook folder:

    Predicting ICU Survival Rate within 30 Days Leveraging NLP-based Machine Learning Pipelines_final_revised.ipynb

#### 1.2 Library requirement:

    This project was developed on Jupyter Notebook with Python 3.7. Please refer to libary_requirement.txt for libraries used in this notebook.

#### 1.3 Additional report on Medium: 
    https://medium.com/@RonghuiZhou/icu-survival-rate-within-30-days-leveraging-natural-language-processing-a0d8fcaeecde

#### 1.4 How to run this project:
     Downlaod anaconda and pip install required libraries. Download the jupyter notebook from notebook folder for this project to evaluate it.

https://www.anaconda.com/

### 2. Introduction  
#### 2.1 Project Overview 
This project will outline how to select a patient cohort, clean the data for exploratory visualization and building a classification model to predict the mortality within 30 days after ICU admission, utilizing initial caregivers’ notes.

#### 2.2 Problem Statement 
The goal is to identify potential high risk patients and try to predict the possibility of survival within 30 days after the ICU admission. If the chance is low, actions should be taken to intervene.

#### 2.3 Data Set 
https://mimic.physionet.org/ 

MIMIC-III (Medical Information Mart for Intensive Care III) is a large, freely-available database comprising deidentified health-related data associated with over forty thousand patients who stayed in critical care units of the Beth Israel Deaconess Medical Center between 2001 and 2012. 

The database includes information such as demographics, vital sign measurements made at the bedside (~1 data point per hour), laboratory test results, procedures, medications, caregiver notes, imaging reports, and mortality (both in and out of hospital).
MIMIC is made available largely through the work of researchers at the MIT Laboratory for Computational Physiology and collaborating research groups. 

MIMIC-III, a freely accessible critical care database. Johnson AEW, Pollard TJ, Shen L, Lehman L, Feng M, Ghassemi M, Moody B, Szolovits P, Celi LA, and Mark RG. Scientific Data (2016). DOI: 10.1038/sdata.2016.35.

Available at: http://www.nature.com/articles/sdata201635

#### 2.4 Metrics  
We will evaluate the performance of machine learning models based on accuracy and confusion matrix.
Classification report shows the metrics: precision, recall, f1-score, and support.

### 3. Patient Cohort & Data Preparation
#### 3.1 Patient Cohort

In this project, ICU patients in the age range 18 to 100 are selected.

#### 3.2 Feature engineering

storetime_order was created based on the order of storetime, this allows me to keep only the initial note after icu admission. Machine learning models are built on the initial note only, neglecting subsequent notes.

    a. Age was calculated based on the difference between icu admission time and date of birth. 

    b. Death age was calculated based on the difference between date of death and date of birth. 

    c. Los_death was calcualted based on the difference between date of death and icu admission time, with number of days as the unit. 

    d. Icustay_order was created based on the order of icu admission time, this allows me to keep only the most recent icu admission. 

#### 3.3 Abnormalities 
    There are some entries found to have negative los_death, meaning the reported death time is earlier than the icu admission time. These entries are removed from this data set.
    
    
#### 3.4 Data engieering

    As the initial selected data set has more than 75% of survived patients, machine learning algorithms didn't perform well for the minority. This is handled by under-sampling the major data with patients survived, using pandas' sampling feature without replacement to generate balanced data sets between survived and died patient groups. This allows machine learning algorithms to train and fit properly, improving the performance on minor data set.

### 4. Exploratory Data Analysis
#### 4.1 Age distribution
    The average age of patients died is significantly higher than patients survived (more than 10 years older). It makes sense as older people have weaker health condition and harder to recover from serious diseases.

#### 4.2 Insurance distribution
    It is found that significantly higher portion of patients died had Medicare insurance, in comparison to private insurance for patients survived. 

#### 4.3 Top 10 diagnoses for different patient groups
    What are the top reasons for patients to go to ICU and die? In this data set, the top 10 reasons for going to ICU are: pneumonia, sepsis, intracranial hemorrhage, coronary artery disease, congestive heart failure, chest pain, altered mental status, gastrointestinal bleed, subarachnoid hemorrhage, and abdominal pain. Five out of these have less than 50% survival rate within 30 days, with the least one being sepsis with less than 30% patients survived. 

### 5. Conclusion & Perspective
This project demonstrated that it is possible to identify high risky patients and predict mortality with pretty good accuracy. Further improvement is possible to utilize biomedical natural language processing packages such as spaCy or SciSpaCy (https://spacy.io/), to understand medical notes more accurately and extract relevant information.

In this project, we haven’t used any lab results and radiology reports. More work needs to be done to incorporate these data to extract meaningful information. Advanced imaging processing techniques and deep learning algorithms might be helpful as well.

Healthcare is directly related with everyone. No matter how healthy you are today, you may interact with the healthcare system in one way or another as you get older or unexpected things can happen to you or your family. With growing digitized healthcare records and data and evolving natural language processing techniques and machine learning algorithms, data science can have a tremendous impact on the human life.

We wish the world without diseases!

### Acknowledgements
MIMIC-III, a freely accessible critical care database. Johnson AEW, Pollard TJ, Shen L, Lehman L, Feng M, Ghassemi M, Moody B, Szolovits P, Celi LA, and Mark RG. Scientific Data (2016). DOI: 10.1038/sdata.2016.35. Available at: http://www.nature.com/articles/sdata201635

