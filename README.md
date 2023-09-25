# AI VARIANT DATA ANALYST INTERNSHIP PROJECT: EMPLOYEE RETENTION

## Table of Contents

1. [Introduction](#introduction)
2. [Project Overview](#project-overview)
3. [Key Performance Indicators (KPIs)](#key-performance-indicators-kpis)
4. [Data Collection and Preprocessing](#data-collection-and-preprocessing)
    - [Data Sources](#data-sources)
    - [Data Cleaning and Transformation](#data-cleaning-and-transformation)
5. [Dashboard Creation](#dashboard-creation)
    - [Excel Dashboard](#excel-dashboard)
    - [Power BI Dashboard](#power-bi-dashboard)
    - [Tableau Dashboard](#tableau-dashboard)
6. [SQL Queries and Data Analysis](#sql-queries-and-data-analysis)
    - [Data Import into SQL](#data-import-into-sql)
    - [Purpose of SQL Queries](#purpose-of-sql-queries)
    - [KPI 1: Average Attrition rate for all Departments](#kpi-1-average-attrition-rate-for-all-departments)
    - [KPI 2: Average Hourly rate of Male Research Scientist](#kpi-2-average-hourly-rate-of-male-research-scientist)
    - [KPI 3: Attrition rate Vs Monthly income stats](#kpi-3-attrition-rate-vs-monthly-income-stats)
    - [KPI 4: Average working years for each Department](#kpi-4-average-working-years-for-each-department)
    - [KPI 5: Job Role Vs Work life balance](#kpi-5-job-role-vs-work-life-balance)
    - [KPI 6: Attrition rate Vs Year since last promotion relation](#kpi-6-attrition-rate-vs-year-since-last-promotion-relation)
    - [SQL Code and Explanation](#sql-code-and-explanation)
    - [Insights from SQL Analysis](#insights-from-sql-analysis)
7. [Usage Instructions](#usage-instructions)
8. [Conclusion](#conclusion)
9. [Contact Information](#contact-information)
10. [Additional Resources](#additional-resources)

## Introduction

Welcome to the AI Variant Data Analyst Internship Project: Employee Retention! This project was completed during an internship at AI Variant after completing the Data Analyst course at ExcelR. The project revolves around HR Analytics and focuses on analyzing employee retention using two datasets, HR_1 and HR_2, each containing 50,000 records.

## Project Overview

- **Domain:** HR Analytics
- **Project Name:** Employee Retention
- **Dataset Names:** HR_1 & HR_2
- **Dataset Type:** Excel Data
- **Dataset Size:** 50,000 records each

## Key Performance Indicators (KPIs)

The project emphasizes six key performance indicators (KPIs) to gain insights into employee retention and related factors:

1. Average Attrition rate for all Departments.
2. Average Hourly rate of Male Research Scientist.
3. Attrition rate Vs Monthly income stats.
4. Average working years for each Department.
5. Job Role Vs Work life balance.
6. Attrition rate Vs Year since last promotion relation.

## Data Collection and Preprocessing

### Data Sources

The HR dataset was initially imported into an SQL database to centralize the data source.

### Data Cleaning and Transformation

The dataset in the SQL database underwent thorough data preprocessing, including handling missing values, data type conversions, and duplicate removal, to prepare it for analysis in Power BI and Tableau.

## Dashboard Creation

### Excel Dashboard
The Excel dashboard provides a clear and organized platform for visualizing critical HR Analytics insights. It utilizes various data visualization components such as charts, graphs, and PivotTables to represent key performance indicators (KPIs) effectively. User-friendly features like dropdown menus, data filtering, and dynamic updates enhance the user experience.

![e1](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/b21b52ca-6fb3-403a-bbaa-9a5837bde98c)


### Power BI Dashboard

The Power BI dashboard offers an immersive and interactive data exploration experience, allowing users to uncover insights and trends within the HR dataset. Its intuitive layout balances visualizations and filtering options, ensuring clarity and responsiveness. Here are some key features of the Power BI dashboard:

![p1](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/b69114da-dae5-4627-b8f3-bd846a9a69cf)

- **User-Friendly Interface:** The dashboard is designed with a user-friendly interface that welcomes users with a clear and organized layout.

- **Rich Visualizations:** It leverages rich data visualizations, including charts, graphs, and tables, to present HR Analytics insights effectively.

- **Slicers and Filters:** Power BI's slicers and filtering options empower users to interactively explore the data. Users can select specific criteria to filter data and instantly observe how it impacts the visualizations.

- **Cross-Filtering:** The dashboard's cross-filtering capabilities enable users to achieve instant updates across visuals when making selections, enhancing the interactive data exploration experience.

![p2](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/e5163e0e-0c70-48fe-9831-4339918d3a36)

### Tableau Dashboard

The Tableau dashboard provides an interactive platform for in-depth HR Analytics, facilitating a deeper understanding of employee retention patterns. Its modern design integrates a variety of data visualization components, including bar charts, donut charts, and more, to depict KPIs. Here are some highlights of the Tableau dashboard:

![t1](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/61974ec9-da0a-42cc-867e-893d8e27350a)

- **Modern Design:** The Tableau dashboard follows a modern and aesthetically pleasing design approach. It offers a visually appealing environment for data exploration.

- **Diverse Visualization Components:** Users can explore a diverse range of data visualization components, including  bar charts, donut charts, and more. These components enable users to gain comprehensive insights.

- **Interactive Filters:** Tableau's interactive filters empower users to dynamically adjust visualizations by selecting and interacting with filters. Users can explore correlations and patterns by fine-tuning their selections.

- **Tooltips:** Detailed tooltips provide additional information and context when users hover over data points or visual elements, enhancing user comprehension.

- **Filter Actions and Highlight Actions:** The dashboard leverages filter actions and highlight actions, allowing users to interact with one visualization to affect others. This functionality provides a seamless and interconnected experience.

![t2](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/7416174f-1032-48d0-a5e3-ce2690dd9250)

## SQL Queries and Data Analysis

### Data Import into SQL

The HR dataset was imported into an SQL database, serving as the primary data source for both Power BI and Tableau dashboards.

### Purpose of SQL Queries

SQL queries played a crucial role in extracting and analyzing data for the key performance indicators (KPIs).

### KPI 1: Average Attrition rate for all Departments

**SQL Query:**
```sql
    CREATE VIEW KPI1 AS
	SELECT 
			Department,
			 
    ROUND((AVG((Attrition_Count)/(EmployeeCount))*100),2) as Avg_Attrition_Rate
	FROM 
			hr_1
	GROUP BY 
			Department
	ORDER BY 
			Avg_Attrition_Rate DESC;
```
**SQL Query to Print:**

```sql
	 #USING VIEWS FOR KPI 1
    SELECT * FROM KPI1;
```
![1](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/c9716d9d-febf-4c88-9de9-4d4a9fe35444)


### KPI 2: Average Hourly rate of Male Research Scientist

**SQL Query:**

```sql
    CREATE VIEW KPI2 AS 
    SELECT 
			JobRole,
			Gender,
			ROUND(AVG(HourlyRate),2) as Avg_HourlyRate
	FROM
			hr_1
	WHERE
			Gender = "Male" AND JobRole = 'Research Scientist';
```

**SQL Query to Print:**

```sql
	 #USING VIEWS FOR KPI 2
     SELECT * FROM KPI2;
```

![2](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/a3ad22ef-1e33-47ed-96d3-77de58cb4905)

### KPI 3: Attrition rate Vs Monthly income stats

**SQL Query:**

```sql
     CREATE VIEW KPI3 AS
     SELECT 
			hr_1.Attrition,
			ROUND(AVG(hr_2.MonthlyIncome),2) AS Avg_MonthlyIncome,
			MIN(hr_2.MonthlyIncome) AS Min_MonthlyIncome,
			MAX(hr_2.MonthlyIncome) AS Max_MonthlyIncome,
            SUM(hr_2.monthlyincome) as Total_MonthlyIncome
	FROM 
			hr_1
	JOIN
			hr_2 ON hr_2.`Employee ID` = hr_1.EmployeeNumber
	GROUP BY
			Attrition;
```

**SQL Query to Print:**

```sql
	 #USING VIEWS FOR KPI 3
     SELECT * FROM KPI3;
```

![3](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/2f258e38-3171-403d-8664-34910d0388b4)

### KPI 4: Average working years for each Department

**SQL Query:**

```sql
     CREATE VIEW KPI4 AS
     SELECT
			hr_1.Department,
			ROUND(AVG(hr_2.TotalWorkingYears),2) AS Avg_Working_Years
	 FROM
			hr_1
	 INNER JOIN
			hr_2 ON hr_2.`Employee ID` = hr_1.EmployeeNumber
	 GROUP BY
			Department
	 ORDER BY 
			Department;
```

**SQL Query to Print:**

```sql
	 #USING VIEWS FOR KPI 4
     SELECT * FROM KPI4;
```

![4](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/66848941-04b5-4eff-ac7e-ca36ef093bc0)


### KPI 5: Job Role Vs Work life balance

**SQL Query:**

```sql
    CREATE VIEW KPI5 AS
	SELECT
			hr_1.JobRole,
			SUM(CASE WHEN hr_2.WorkLifeBalance = 4 THEN 1 ELSE 0 END) AS Excellent,
			SUM(CASE WHEN hr_2.WorkLifeBalance = 3 THEN 1 ELSE 0 END) AS Good,
			SUM(CASE WHEN hr_2.WorkLifeBalance = 2 THEN 1 ELSE 0 END) AS Average,
			SUM(CASE WHEN hr_2.WorkLifeBalance = 1 THEN 1 ELSE 0 END) AS Poor
	FROM
			hr_1
	INNER JOIN
			hr_2 ON hr_2.`Employee ID` = hr_1.EmployeeNumber
	GROUP BY
			JobRole
	ORDER BY
			JobRole;
```

**SQL Query to Print:**

```sql
	 #USING VIEWS FOR KPI 5
     SELECT * FROM KPI5;
```

![5](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/7f7c85a9-e5c0-4697-8d37-75f9e0a77073)


### KPI 6: Attrition rate Vs Year since last promotion relation

**SQL Query:**

```sql
     CREATE VIEW KPI6 AS
     SELECT 
			hr_2.YearsSinceLastPromotion,
            ROUND((SUM(Attrition_Count)/SUM(EmployeeCount))*100,2) AS AttritionRate            
	 FROM
			hr_1
	 JOIN
			hr_2 ON hr_2.`Employee ID` = hr_1.EmployeeNumber
	 GROUP BY 
			1
	 ORDER BY 
			1;
```

**SQL Query to Print:**

```sql
	 #USING VIEWS FOR KPI 6
     SELECT * FROM KPI6;
```

![6](https://github.com/DeveshGaonkar/Employee_Retention/assets/138006145/db94cc4e-45c0-4daa-8a90-13f9e970660f)

### SQL Code and Explanation

Each SQL query's code is designed to calculate specific metrics, and the accompanying explanation provides clarity on the logic applied within the project's context.

### Insights from SQL Analysis

The SQL analysis reveals insights into employee attrition, hourly rates, income statistics, working years, job roles, and their impact on employee retention.

## Usage Instructions

- Clone the project repository using the command: `git clone [repository URL]`.
- Ensure the Excel datasets (HR_1.xlsx and HR_2.xlsx) are available in the designated folders.
- Open the respective dashboard tools (Excel, Power BI, Tableau) and link the datasets to your project.
- Access and interact with the dashboards to explore HR Analytics insights.
- Run SQL queries in your SQL environment to analyze the data further.

## Conclusion

### Project Summary

This project successfully analyzed employee retention using HR Analytics. It created interactive dashboards and utilized SQL queries to gain insights into key performance indicators.

### Achievements and Insights

The project revealed valuable insights related to attrition rates, hourly rates, income statistics, working years, job roles, and their impact on employee retention.

### Lessons Learned

Challenges included data preprocessing and tool-specific nuances. The project underscored the importance of clear visualization design and thorough data understanding for meaningful analysis.

### Future Enhancements

Future work could involve predictive modeling for employee retention, advanced SQL analysis, or integration with live HR data sources for real-time insights.

## Contact Information

- **Name:** Devesh Ghanshyam Gaonkar
- **Email Address:** gaonkardevesh@gmail.com
- **LinkedIn Profile:** [https://www.linkedin.com/in/devesh-gaonkar/]
- **GitHub Repository:** [Your GitHub Repository URL]

## Additional Resources

- [Link to Excel Dashboard](https://docs.google.com/spreadsheets/d/1I7s_MWoLK590qn4cj3XjAFBi7rM9rw1S/edit?usp=sharing&ouid=115465960996122487206&rtpof=true&sd=true)
- [Link to Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNWM0ODE5YTktMTI2Ni00Y2ExLTg2NWItNTUzYjU5YjlhY2UxIiwidCI6ImI1NDhiOWUyLTQ2NmEtNGQ4MS05MDNiLTI0Y2Y4Y2M1ZTM3ZSJ9)
- [Link to Tableau Dashboard](https://public.tableau.com/views/EmployeeRetention_16956529694950/Story?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link)
- [Documentation or tutorials on using Excel](https://www.javatpoint.com/excel-tutorial)
- [Documentation or tutorials on using Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/fundamentals/service-get-started)
- [Documentation or tutorials on using Tableau](https://help.tableau.com/current/guides/get-started-tutorial/en-us/get-started-tutorial-home.htm)
- [Documentation or tutorials on using SQL (e.g., MySQL)](https://www.javatpoint.com/mysql-tutorial)
