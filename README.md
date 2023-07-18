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
  ![data](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/3e1a1916-bdb7-406e-9456-2d37c598517b)
 Figure 1 is a set of three visualizations from the “Our World in Data COVID Vaccination data repository”, specifically the people_vaccinated, people_fully_vaccinated, and the new_vaccinations features. The zero value, represented by a flat line on the x-axis, from April to January 20201 demonstrates Canada’s lack of vaccines. Interestingly, as Canada began to secure and administer more vaccinations in January 2021, Canada experienced a delay in the vaccination procurement process. This delay ended roughly around the end of March, which is represented in the line graphs by a slight dip in the trend lines of all three features before rising exponentially.

## Q4 Data Description:
The study has used one of the datasets prepared by the John Hopkins university center for system science and engineering. It is a time series data of covid 19 global confirmed cases. The original dataset has 276 rows and 499 columns. It has a large number of columns, each day since the pandemic hits taken as a column to record each country's daily confirmed cases. For this study purpose the dataset has been transformed to 495 rows and 5 columns. The daily column values are melted to rows via panda functions as shown in the below tables:

### General Trend of the spread of the virus since January 2020
The two-line graphs show the general trend of the spread of the virus in the US since Jan 22, 2020. The first graph depicts the trend of the daily confirmed cases by date. As it can be seen the pandemic has highest daily cases around January 2021. After that date it has started declining. The second graph demonstrates the growth ratio of Covid-19 cases by date. The red line depicts the mean growth ratio which is value of 1.04. The growth ratio is below the mean since around May 2020. Before the given date, the growth ratio was unstable.
 ![Picture1](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/892fe80c-8718-4b8a-93b5-b68a5d9267ce)
 Figure: confirmed cases by date
 ![Picture2](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/3d6192bb-3868-4d8c-afc5-b0e0235d9436)
 Figure: growth ratio by date with mean growth ratio

### Linear Regression
The first model implemented was simple linear regression on growth ratio by number of days. Growth ratio of virus on day N is calculated as the number of confirmed cases on day N divided by the number of confirmed cases on day N-1. From the results of the linear regression, there is a slight downward trend on growth ratio. Residual plot of linear regression on growth ratio is almost constant straight line at around 0 growth ratio which confirms reasonable assumption.

![Picture3](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/a007ad82-4a06-4765-8b51-9b40bd5975d8)

![Picture4](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/a6dff052-0dd4-4e3a-aae0-a6ed862b47fb)
### Ridge Regression
To further enhance the prediction, I implemented Ridge regression on growth ratio by number of days with Alpha value 1. 80% training and 20% test data used to carry out the model. As shown on the predicted growth ratio graph it is a slightly sharper downward trend on growth ratio than the linear regression.

![Picture5](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/c4a9c551-07c2-49c5-8c95-812c348976bd)


### CV-Ridge Regression
The third model implemented was cross validation ridge regression on growth ratio by number of days. Among the range of 1-30 the best alpha value selected by the model is 2.72. From the result value of coefficients are smaller than ridge regression with MSE 0.01123 and R2 10%, which is higher than the previous model (Ridge regression). This model also tested via a 20% test dataset and resulted in a less sharp downward trend on growth ratio than Ridge regression.
![Picture7](https://github.com/SeidaAhmed/An-application-of-Machine-Learning-to-COVID-19-data/assets/65707004/eddba620-e42f-4109-8fd5-fdab50beaa3b)

  

