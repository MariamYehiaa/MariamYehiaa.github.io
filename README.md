#uk youtubers project
# Objective 
the objective of the project is that the Head of Marketing wants to find out who the top 3 youtuber channels that would be best to run marketing campaigns throughout the rest of the year and that will happen by creating dashboard that provides insights into the top 3 UK YouTubers in 2024 that includes their
subscriber count ,total views ,total videos, and engagement metrics
# Data source
the data needed for this project (top UK YouTubers in 2024) includes their
channel names
total subscribers
total views
total videos uploaded
The dataset of the project is from Kaggle (an Excel extract), [see here to find it.](https://www.kaggle.com/datasets/bhavyadhingra00020/top-100-social-media-influencers-2024-countrywise?resource=download)
# Stages of the project
this involves design,development,testing,Analysis
# Design
Dashboard is composed of the 3 channels having the highest average views per video,Potential product sales per video which is average views per video times the conversion rate,potential revenue per video which is average views per video times product cost, finally net profit which is potential revenue per video minus campaign cost where each variable has 2 columns(excel in one column and sql in other column)
Tools
Excel-->	Exploring the data
SQL Server-->	Cleaning, testing, and analyzing the data
Power BI-->	Visualizing the data via interactive dashboards
GitHub-->	Hosting the project documentation and version control
# Development
Get the data from kaggle
Explore the data in Excel
Load the data into SQL Server
Clean the data with SQL
Test the data with SQL
Visualize the data in Power BI
Generate the findings based on the insights
# Data exploration
1.4 columns at least that contain the data we need for this analysis, which indicates that we have everything needed for the project
2.The first column contains channel IDs, which include the channel names separated by the @ symbol. We need to extract only the channel names from this data.
3.Some column headers and cell values are in a different language. We need to determine if these columns are necessary and, if so, find a way to standardize or translate them.
4.some columns and not required and as a result would be removed
# Data cleaning
all redundant columns and rows must be removed and column numbers must be 4 and row number must be 100, ensuring datatype of columns is matched like the table below and all column values must be non-null values.
| Property         | Description |
|-----------------|------------|
| Number of Rows  | 100        |
| Number of Columns | 4        |

| Column Name       | Data Type | Nullable |
|------------------|----------|----------|
| channel_name    | VARCHAR  | NO       |
| total_subscribers | INTEGER  | NO       |
| total_views     | INTEGER  | NO       |
| total_videos    | INTEGER  | NO       |
steps required for data cleaning.1)extract channel names from first column(Nombre column),remove redundant rows and columns,renaming columns using alias
# Transfrom Data
image below shows:1)selecting required columns.2)extracting channel names from Nombre Columns
![image](https://github.com/user-attachments/assets/6aaaf6ea-91d8-4936-b472-68bbb6a97b8f)
2) ## Create the SQL view

```sql
/* 
# 1. Create a view to store the transformed data 
# 2. Cast the extracted channel name as VARCHAR(100) 
# 3. Select the required columns from the top_uk_youtubers_2024 SQL table 
*/

-- 1.
CREATE VIEW view_uk_youtubers_2024 AS

-- 2.
SELECT 
    CAST(SUBSTRING(NOMBRE, 1, CHARINDEX('@', NOMBRE) - 1) AS VARCHAR(100)) AS channel_name, -- 2.
    total_subscribers,
    total_views,
    total_videos

-- 3.
FROM top_uk_youtubers_2024;








