# ORIE 4741 Midterm Report
#### Anusha Avyukt (aa2686), Fei Xia (fx43), Siyang Liu (sl2687)
### 1. Problem Statement
Our project focuses on hospital selection for emergency cases, based on patients’ medical conditions and other relevant features. Given a patient’s personal information, we want to give an estimate of total charges and length of stay. We hope to develop a strategy to find a best fit that meet the patients’ need.
## 2.Dataset
### 2.1 Data Description
The dataset we will mainly use is the Statewide Planning and Research Cooperative System (SPARCS) inpatient de-Identified dataset, which provides details on patient characteristics, diagnoses, treatments, services, and charges. The discharge year of the dataset is 2012 only. This data contains basic record level detail regarding the discharge. Till now, there are 2.54 million rows and 34 columns entries in the dataset. 
### 2.2 Data Cleaning
Specifically, the dataset provides information on service area, age group/gender/race/ethnicity of patients, type of admission, diagnosis, risk of morality, zip code of hospital, and total charges/costs. There are different types of data including: numerical data such as length of stay,  ordinal data such as severity of illness, boolean data such as Emergency Department Indicator, and categorical data such as payment type. To clean the dataset, we first deleted the duplicated columns where they provide the identical information, for example, the column ‘APR MDC Description’ is a detailed explanation of ‘APR MDC Code’ where APR MDC stands for All Patient Refined Major Diagnostic Category. We also dropped the birth weight column because it is not considered useful in our analysis. We deleted payment typology 2 and 3 because they have too many NaN data and their information overlapped with payment typology 1. As emergency is the most frequent type of admission, we then delete the rows where they show non-emergency types.  We also dropped the rows where the abortion edit indicator shows yes. We then transform the string values such as ‘120 +’ in Length of Stay columns to numerical 120 and performed one-hot encoding to all the categorical data.

## 3. Data Exploration Analysis
To better understand how the emergency charges are affected by the conditions of the patients and hospitals, we plotted the total charges of emergency versus health service area, counties, type of disease, payment types, medical procedures (non-surgical or surgical). Below we only show four of the plots due to the space limit of the repot. According to the given dataset, we found that most of the medical charges for emergency lie between 0 - 20,000 dollars, with a mean of 18,800 dollars. In Figure (a), we showed the total charges difference across difference health service areas. We found Hudson Valley and Long Island has the highest mean charges. In Figure (b), we showed the differences in hospital choices across disease types, and found that there could be potential expertise difference of the hospitals that obviously attract patients with certain diseases. In Figure (c), we showed the charges across different payment type and found that self-pay produces the lowest charges. In Figure (d), we showed that certain hospitals attracts more 0-17 age group patients meaning more children related expertise. The data exploration analysis helped us determined intuitively the features that can be considered for the modeling part.



## 4. Feature Selection
We also explored feature selection more quantitatively using Random Forests model. Random Forests model can naturally select the most important features for a specific regression target. Here, we found the top 7 important factors that influence the total charges in emergency, which are length of stay, medical diagnosis category, medical surgery types, hospital, service area, severity of illness and hospital county. We will use these 7 features as the main feature of consideration in our future analysis.


## 5. Future Work
Our next step will be more focused on the modeling for the total charges based on the features we selected. We will also
