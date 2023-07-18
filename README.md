## Introduction:
Discovering novel trends, metrics, and analyses in data collected on COVID-19 can set precedents for future interactions between humans and novel viruses. Using datasets from the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University created the opportunity to explore global demographic, timeseries, morbidity, and institutional forms of data. Applying machine learning techniques to these datasets allow us to model various features of interest in a global and local context. The analyses within this report are inferential in nature, given that the Global Pandemic is still ongoing. The datasets used within the analyses are time-sensitive in nature, and can be considered time-series datasets.
## General Data Description:
The main dataset source that is used is the COVID-19 Data Repository by the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University. The data was collected starting January 22, 2020 and has been ongoing since. The repository contains several datasets (some for the United States specifically, for example). Two of these were used: the daily COVID-19 report dataset for the day of May 30th, 2021 (RQ 1, 2, 3), and the COVID-19 global confirmed cases time series dataset (RQ 4). The daily COVID-19 report has 4000 entries and 14 features, with each entry representing either a country or a state/province/county within a country. The COVID-19 global confirmed cases has 300 entries and approximately 500 features with every entry representing a country and every feature representing the number of confirmed cases totalled up till that day. Some features some as mapping and coordinate features were not used, the main features that were looked at were:

- Province_State: Province, state or dependency name.
*  Country_Region: Country, region or sovereignty name.
+ Last Update: MM/DD/YYYY HH:mm:ss (24 hour format, in UTC).
- Confirmed: Counts include confirmed and probable (where reported).
* Deaths: Counts include confirmed and probable (where reported).
+ Recovered: Recovered cases are estimates based on local media reports
_ Active: Active cases = total cases - total recovered - total deaths.
* Incident_Rate: Incidence Rate = cases per 100,000 persons.
+ Case_Fatality_Ratio (%): Case-Fatality Ratio (%) = Number recorded deaths
/ Number cases.
## Research/application questions:
After examining the CSSE dataset, it was decided that these will be the questions to be explored:
1. Is there a relation between COVID-19 vaccinations and people admitted to Intensive Critical Care units in Canada?
2. What factors are possibly affecting COVID-19 related deaths?
3. What factors are possibly affecting COVID-19 incidence rates?
4. Covid 19 Number of confirmed cases analysis and prediction on US
Research Question 1: Is there a relation between COVID-19 vaccinations and people admitted to Intensive Critical Care units in Canada?
### Q1 Data Description:
The “Our World in Data COVID Vaccination data repository”, was chosen because of it s up-to-date vaccination features and it shares the same data source for “total_cases'' and “total_deaths'' that the CSSE at Johns Hopkins University uses. The features of interest from this dataset that were used to conduct the final analyses were:
_ Date: date of observation
* Total_cases: daily new confirmed COVID-19 cases
+ Total_deaths: new confirmed COVID-19 deaths
- Reproduction_rate: the average number of new infections by a single infected
individual. If the rate is greater than 1, the infection is able to spread in the population. If it is below 1, the number occurring in the population will gradually decrease to zero
* Icu_patients: daily number of patients’ admitted to a hospital’s Intensive Care Unit because of COVID-19
- Hosp_patients: daily number of people admitted to a hospital’s Intensive Care Unit because of COVID-19
+ total_vaccinations: total number of vaccinations administered. This is counted as a single dose, meaning that it will increase by 1 each time a person receives a dose.
_ People_vaccinated: number of people that have taken their first dose of a vaccine
* People_fully_vaccinated: number of people that have taken all doses of a vaccine
+ New_vaccinations: number of first doses approved to be administered
