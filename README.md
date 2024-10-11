
# International Debt Analysis with SQL

## Introduction
This project analyzes international debt statistics collected by **The World Bank**. The dataset contains detailed information on the debt (in USD) owed by developing countries across multiple categories. The goal of this analysis is to answer key questions about the debt distribution and repayment patterns among these countries.

## Dataset Overview
The dataset used in this project includes the following columns:
- **country_name:** Name of the country
- **country_code:** Code representing the country
- **indicator_name:** Description of the debt indicator
- **indicator_code:** Code representing the debt indicator
- **debt:** Value of the debt indicator for the given country (in current USD)

## Objectives
The key questions aimed to answer using SQL queries are:
1. **Number of distinct countries** present in the dataset.
2. **Country with the highest total debt**.
3. **Country with the lowest amount of repayments on external long-term debt**.

## SQL Queries and Analysis

### 1. Number of Distinct Countries
I used the following SQL query to find the number of unique countries in the dataset:

```sql
SELECT COUNT(DISTINCT country_name) AS total_distinct_countries
FROM public.international_debt;
```
- **Result:** X distinct countries were found in the dataset.

### 2. Country with the Highest Debt
To find the country with the highest amount of total debt, I summed up the debt for each country:

```sql
SELECT country_name, SUM(debt) AS total_debt
FROM public.international_debt
GROUP BY country_name
ORDER BY total_debt DESC
LIMIT 1;
```
- **Result:** The country with the highest debt is **China**, with a total debt of USD Y.

### 3. Country with the Lowest Repayment
I identified the country with the lowest amount of repayments on long-term external debt using the following query:

```sql
SELECT country_name, indicator_name, SUM(debt) AS total_repayment
FROM public.international_debt
WHERE indicator_code = 'DT.AMT.DLXF.CD'
GROUP BY country_name, indicator_name
ORDER BY total_repayment ASC
LIMIT 1;
```
- **Result:** The country with the lowest repayment on long-term debt is **Timor-Leste**.

## Insights and Visualizations
- **Highest Debt Country:** China has the largest debt burden, likely due to its extensive infrastructure projects and large population.
- **Lowest Repayment Country:** Timor-Leste has the lowest repayment amount, indicating possible challenges in meeting its external debt obligations.
  

## Conclusion
This project provides key insights into the debt patterns of developing countries. The SQL queries used demonstrate the ability to extract valuable information from large datasets, helping inform economic decisions and policymaking.

## Skills Demonstrated
- SQL querying (aggregations, grouping, filtering)
- Data analysis with real-world datasets
- Extracting actionable insights
