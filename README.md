# SQL-US-Accidents
SQL Project to analize Traffic Accident Dataset (2016 - 2023)

## Dataset Link
https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents

## Project Overview
This project analyzes US car accidents between 2016-2023 with SQL queries. It provides insights about car accidents across different states.


## Key Insights
- Total rows 7,728,394

- California leading by far the total of accidents

- Miami has the most car accidents, with 186,768

- Total accidents in fair weather are 2.5 times higher than in moustly cloudy conditions

- Accidents rates are higher during working hours

- December, November and January have the highest number of total accidents

## Tools & Technologies
-SQL

-DuckDB

-Python

-Jupyter Notebook

-Data Visualization

## SQL Queries
-Top 10 States with Most Accidents:

duckdb.sql(f"""
SELECT State, COUNT(*) AS total_accidents
FROM read_csv_auto('{file_path}')
GROUP BY State
ORDER BY total_accidents DESC
LIMIT 10
""").df()

-Top 10 Cities with Most Accidents:

duckdb.sql(f"""
SELECT City, State, COUNT(*) AS total_accidents
FROM read_csv_auto('{file_path}')
GROUP BY City, State
ORDER BY total_accidents DESC
LIMIT 10
""").df()

-Accidents by Weather Condition:

con.sql("""
SELECT Weather_Condition, COUNT(*) AS total_accidents
FROM accidents
WHERE Weather_Condition IS NOT NULL
GROUP BY Weather_Condition
ORDER BY total_accidents DESC
LIMIT 10
""").df()

-Accidents by Time Hour:

con.sql("""
SELECT EXTRACT(HOUR FROM Start_Time) AS accident_hour,
       COUNT(*) AS total_accidents
FROM accidents
GROUP BY accident_hour
ORDER BY total_accidents DESC
LIMIT 10
""").df()



-For full SQL analysis, check the Jupyter Notebook in this repository:

https://github.com/ipiniella/SQL-US-Accidents/blob/main/SQL_Accidents_final.ipynb


