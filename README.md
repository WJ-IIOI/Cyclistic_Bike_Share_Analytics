# Cyclistic Bike-Share Analysis Case Study

![Alt Text](C:\Users\linji\OneDrive\Desktop)

### Introduction
Welcome to my capstone project for the Google Data Analytics Certificate course!\
In this case study, I will tackle many real-world tasks of a data analyst for a bike-share company to analyze historical data to identify trends in how annual members and casual riders use Cyclistic bikes differently and design marketing strategies to convert casual riders to members.

The main tools I used thought this project are **EXCEL**, **MySQL** and **Tableau**. Here are the highlights:
* Tableau Dashboard: [Bike-Share Analysis](https://public.tableau.com/app/profile/jia.wang3280/viz/Bike-shareanalysis2022/Overview).
* Course: [Google Data Analytics Capstone](https://www.coursera.org/learn/google-data-analytics-capstone).
* Data source: [Divvy trip history data](https://divvybikes.com/system-data).

In order to breakdown the tasks, I will follow the steps of the data analysis process down below: 
1. [Ask](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#step-1-ask--understand-the-problem)
2. [Prepare](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#step-2-prepare--A-description-of-data)
3. [Process](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#step-3-process--from-dirty-to-clean)
4. [Analyze](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#step-4-analyze--find-the-insights)
5. [Share](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#step-5-share---visualizing-findings)
6. [Act](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#step-6-act--conclusions-from-the-analysis)

### Scenario
* _I am assuming to be a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago_.
* _Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders_.
* _The director of marketing believes that maximizing the number of annual members will be key to the company's future growth_.
* _My team wants to better understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members_.
* _Cyclistic executives must approve our recommendations, so they must be backed up with compelling data insights and professional data
visualizations_.

### About the company
* _Cyclistic is a bike-share company which has grown to a fleet of 5,824 bicycles and a network of 692 stations across Chicago_.
* _It has 3 flexible pricing plans: single-ride passes, full-day passes, and annual memberships_.
* _Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members_.
* _Its users are more likely to ride for leisure, but about 30% use bikes to commute to work each day_.

## **STEP 1 ASK – Understand the problem**
### 1.1 Defining the problem
The main problem for the director of the marketing and marketing analytics team is this: 
Design marketing strategies aimed at converting Cyclistic’s casual riders into annual members.\
There are three questions that will guide this future marketing program. 
1. **How do annual members and casual riders use Cyclistic bikes differently?**
2. **Why would casual riders buy Cyclistic annual memberships?**
3. **How can Cyclistic use digital media to influence casual riders to become members?**

By looking at the data, we will be able to first get a broad sense of certain patterns that are occurring in the two different groups. Understanding the differences will provide more accurate customer profiles for each group. These insights will help the marketing analyst team design high quality targeted marketing for converting casual riders into members. For the executive team, these insights will help Cyclistic maximize the number of annual members and will fuel future growth for the company.

### 1.2 Business task
* Analyze historical bike trip data to identify trends in how annual members and casual riders use Cyclistic bikes differently.
* Design marketing strategies aimed at converting casual riders to members.

### 1.3 Identify key stakeholders
* **The director of marketing** who is responsible for the development of campaigns and initiatives to promote the bike-share program.
* **The executive team** which is notoriously detail-oriented and will decide whether to approve the recommended marketing program.
* **The marketing analytics team** which is a team of data analysts who are responsible for collecting, analyzing, and reporting data that helps guide marketing strategies.


## **STEP 2 PREPARE – A description of data**
### 2.1 Data source
I will work through this project by using **Divvy trip history data** from Jan 2022 to Dec 2022.\
_( Note: The datasets have a different name because Cyclistic is a fictional company. )_\
Data can be downloaded: [Divvy trip history data](https://divvy-tripdata.s3.amazonaws.com/index.html).

### 2.2 Licensing, privacy, security and accessibility
* **Licensing** — The data has been made available by Motivate International Inc. under this [license](https://ride.divvybikes.com/data-license-agreement).
* **Privacy** — The data-privacy issues prohibit using riders’ personally identifiable information such as gender and age.
* **Security and accessibility** — This is public data that we can use to work with and released on a monthly schedule.

### 2.3 Credibility of Data
The credibility and integrity of our data can be determined using the **ROCCC** system.
* **Reliable** — The data has a large sample size, reflecting the population size.
* **Original** — We can locate the primary source.
* **Comprehensive** — The data is understandable and does not contain any missing critical information needed to answer the business question or find the solution, nor does it has human error.
* **Current** — The data is relevant and up to date, thus indicating that the source refreshes its data regularly.
* **Cited** — The data source are publicly available provided by Motivate International Inc. and Chicago Department of Transportation.

The data integrity and credibility are sufficient to provide reliable and comprehensive insights for analysis.

### 2.4 Data organization
The data is ride records stored in 12 CSV files for each month.\
Each record is anonymized and includes 13 fields values:

#_Field | Field Name | Description | Date Type
:---: | --- | --- | ---
1 | ride_id | Unique ride_id | Varchar
2 | rideable_type | Bike type | Varchar
3 | started_at | Trip start day and time | Datetime
4 | ended_at | Trip end day and time | Datetime
5 | start_station_name | Trip start station | Varchar
6 | start_station_id | Trip start station id | Varchar
7 | end_station_name | Trip end station | Varchar
8 | end_station_id | Trip end station id | Varchar
9 | start_lat | Trip start latitude | Float
10 | start_lng | Trip start longitute | Float
11 | end_lat | Trip end latitude | Float
12 | end_lat| Trip end longitute | Float
13 | member_casual | Rider type | Varchar

### 2.5 Prepare data in MySQL Workbench
The data contains over millions of ride records. MySQL Workbench is a good tool to work with the huge size data through this project.\
In this step:
1. Creating project database and template table struture for loading files.
2. Importing data from the CSV files of each month.
3. Combining the 12 separate tables into one single table.

After above, it's ready for PROCESS.\
**MySQL query**: [01 Data prepare](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/blob/main/01_trip_2022_import.sql)


## **STEP 3 PROCESS – From dirty to cleaning**
* 3.1. [Backup data for cleaning](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#31-backup-data-for-cleaning)
* 3.2. [Remove duplicate data](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#32--remove-duplicate-data)
* 3.3. [Remove irrelevant data](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#33-remove-irrelevant-data)
* 3.4. [Deal with outliers and invalid data](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#34-deal-with-outliers-and-invalid-data)
* 3.5. [Check string values](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#35-check-string-values)
* 3.6. [Handle missing data](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#36-handle-missing-data)
* 3.7. [Do type conversion](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#37-do-type-conversion)
* 3.8. [Fix ambiguities and errors](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#38-fix-ambiguities-and-errors)
* 3.9. [Data-cleaning verification](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/tree/main#39-Data-cleaning-verification)

### 3.1 Backup data for cleaning
```sql
-- add new column called ride_length to caculate the length of each ride
-- total 5667717 rows before cleaning as original table

DROP TABLE IF EXISTS trip_2022_clean;

CREATE TABLE IF NOT EXISTS trip_2022_clean AS 
(	
    SELECT
        ride_id,
        rideable_type,
        started_at,
        ended_at,
        TIMEDIFF(ended_at, started_at) AS ride_length,
        start_station_name,
        start_station_id,
        end_station_name,
        end_station_id,
        start_lat,
        start_lng,
        end_lat,
        end_lng,
        member_casual
    FROM trip_2022
);  
```

### 3.2  Remove duplicate data
```sql
-- check duplicate rows by 'ride_id' column which is unique value 
-- 0 null value and 0 duplicate

SELECT
    SUM(isnull(ride_id)) AS null_value,
    COUNT(*) - COUNT(DISTINCT ride_id) AS duplicate_rows
FROM trip_2022_clean
;
```

### 3.3 Remove irrelevant data
```sql
-- check datetime range
-- all trips started in 2022 which means each trip record is relevant of 2022

SELECT 
    MIN(started_at),
    MAX(started_at)
FROM trip_2022_clean
;
```

### 3.4 Deal with outliers and invalid data
```sql
-- check ride length outlier

SELECT 
    MIN(ride_length),
    MAX(ride_length)
FROM trip_2022_clean
;
```

```sql
-- any trip with negative ride_length are considered invalid
-- any trip less than 60 ses are potentially false starts or users trying to re-dock a bike to ensure it was secure
-- any trip greater than 24 hrs are considered invalid outliers that are taken by staff as they service and inspect the system

SELECT
    started_at,
    ended_at,
    ride_length
    FROM trip_2022_clean
WHERE 
    ride_length < '00:01:00'
    OR ride_length > '24:00:00'
ORDER BY ride_length
;
```

* Update data
```sql
-- remove 126449 rows which ride_length < 1min or > 24hr

DELETE FROM trip_2022_clean
WHERE 
    ride_length < '00:01:00'
    OR ride_length > '24:00:00'
;
```

### 3.5 Check string values
```sql
-- check the distinct values in rideable_type column
-- only 3 strings 'classic_bike', 'electric_bike', docked_bike

SELECT 
    rideable_type,
    count(*)
FROM trip_2022_clean
GROUP BY 1
ORDER BY 2 DESC
;
```

* Update data
```sql
-- rename rideable_type column for more meaningful

ALTER TABLE trip_2022_clean
RENAME COLUMN rideable_type TO bike_type
;

-- trim string values

START TRANSACTION;

UPDATE trip_2022_clean
SET bike_type = trim('_bike' FROM bike_type)
;

COMMIT;
```


```sql
-- check the distinct values in member_casual column
-- only 2 strings with lowercase 'member', 'casual'

SELECT
    member_casual,
    count(*)
FROM trip_2022_clean
GROUP BY 1
ORDER BY 2 DESC
;
```

* Update data
```sql
-- rename member_casual column for more meaningful

ALTER TABLE trip_2022_clean
RENAME COLUMN member_casual TO ride_type
;

-- uppercase the first letter

START TRANSACTION;

UPDATE trip_2022_clean
SET ride_type = CONCAT(UPPER(SUBSTRING(ride_type, 1, 1)), LOWER(SUBSTRING(ride_type, 2)))
;

COMMIT;
```

### 3.6 Handle missing data
* Check the missing values of all columns
```sql
-- 802104 null values of start_station_name, start_station_id
-- 845268 null values of end_station_name, end_station_id
-- 702 null values of end_lat, end_lng

SELECT 
    sum(isnull(ride_id)) AS ride_id,
    sum(isnull(rideable_type)) AS rideable_type,
    sum(isnull(started_at)) AS started_at,
    sum(isnull(ended_at)) AS ended_at,
    sum(isnull(start_station_name)) AS start_station_name,
    sum(isnull(start_station_id)) AS start_station_id,
    sum(isnull(end_station_name)) AS end_station_name,
    sum(isnull(end_station_id)) AS end_station_id,
    sum(isnull(start_lat)) AS start_lat,
    sum(isnull(start_lng)) AS start_lng,
    sum(isnull(end_lat)) AS end_lat,
    sum(isnull(end_lng)) AS end_lng,
    sum(isnull(member_casual)) AS member_casual
FROM trip_2022_clean
;
```

```sql
-- if both end_station, end_lat & lng columns are null values,
-- they are invalid data and can be deleted

SELECT 
    end_station_name,
    end_station_id,
    end_lat,
    end_lng
FROM trip_2022_clean
WHERE 
    end_station_name is NULL
    AND end_station_id is NULL
    AND end_lat is NULL
    AND end_lng is NULL
;
```

* Update data
```sql
-- 702 rows which both end_station, end_lat & lng are null values deleted

DELETE FROM trip_2022_clean
WHERE 
    end_station_name is NULL
    AND end_station_id is NULL
    AND end_lat is NULL
    AND end_lng is NULL
;
```

* Check start_station_name, start_station_id wether are both null values
```sql
-- 802104 rows start_station_name & id are both null values, but still have start_lat & lng data

SELECT 
    start_station_name, 
    start_station_id,
    start_lat,
    start_lng
FROM trip_2022_clean
WHERE
    start_station_name IS NULL
    AND start_station_id IS NULL
;
```

* Based on start_lat & lng data, try to identify the missing start_station_name & id
```sql
-- check the max, min length of start lat & lng data which are start_station_name & id are null
-- which means the precision of all start_lat & lng are only rounded 2 decimals or less

SELECT
    max(length(start_lat)), -- max 5, length including'.' sign
    min(length(start_lat)), -- min 4, length including'.' sign
    max(length(start_lng)), -- max 6, length including '-','.' sign
    min(length(start_lng)) --  min 5, length including '-','.' sign
FROM trip_2022_clean
    WHERE start_station_name IS NULL
    AND start_station_id IS NULL
;

-- total 802104 rows
SELECT 
    start_station_id,
    start_lat, 
    start_lng
    FROM trip_2022_clean
WHERE 	
    start_station_name IS NULL
    AND start_station_id IS NULL
    AND length(start_lat) <= 5
    AND length(start_lng) <= 6
ORDER BY 2 DESC
;
```

```sql
-- find the start_station_id with the same start_lat & lng

WITH not_null_station AS 
(	
    SELECT 
        start_station_id,	
        start_lat,
        start_lng,
        count(*) AS count
        -- ROW_NUMBER() OVER (PARTITION BY start_lat, start_lng ORDER BY count(*) DESC) AS top
    FROM trip_2022_clean
    WHERE 
        start_station_name IS NOT NULL
        AND start_station_id IS NOT NULL
        AND length(start_lat)  <= 5
        AND length(start_lng)  <= 6
    GROUP BY 2, 3, 1
    ORDER BY 2, 3, 4 DESC
)
-- join null start_station_name & id and above CTE on same start_lat & lng 
SELECT 
    t.start_station_id AS n_start_station,
    t.start_lat AS n_start_lat,
    t.start_lng AS n_start_lng,
    n.start_station_id,
    n.start_lat,
    n.start_lng,
    count(*) AS n_count
FROM trip_2022_clean AS t
INNER JOIN not_null_station AS n
    ON t.start_lat = n.start_lat
    AND t.start_lng = n.start_lng
WHERE t.start_station_name IS NULL
AND t.start_station_id IS NULL
GROUP BY 1, 2, 3, 4, 5, 6
ORDER BY 2, 3, 7 DESC
;

-- after above qurey, we can't simply replace null station_id with start_station_id by the same start_lat & lng
-- because the precision of 2 decimal places is too imprecise,
-- many stations have the same lat & lng, we can't identify the specific start_station_name & id
-- so the data are not satisfied to replace the null values, need to remove all
```

* Update data
```sql
-- 802104 rows removed

DELETE FROM trip_2022_clean
WHERE 
    start_station_name is NULL
    AND start_station_id is NULL
;
```

* Handle with the missing data of end_station_name & id by the same ways\
**MySQL query**: [02 Data clean](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/blob/main/02_trip_2022_clean.sql)

### 3.7 Do type conversion
```sql
-- check all the lat & lng length

SELECT 
    MAX(length(start_lat)),
    MIN(length(start_lat)),
    MAX(length(start_lng)),
    MIN(length(start_lng)),
    MAX(length(end_lat)),
    MIN(length(end_lat)),
    MAX(length(end_lng)),
    MIN(length(end_lng))
FROM trip_2022_clean
;
```

* Update data
```sql
-- for geographic visulization only need 4 decimal places precision

ALTER TABLE trip_2022_clean
MODIFY COLUMN start_lat DECIMAL(6, 4),
MODIFY COLUMN start_lng DECIMAL(7, 4),
MODIFY COLUMN end_lat DECIMAL(6, 4),
MODIFY COLUMN end_lng DECIMAL(7, 4)
;
```

### 3.8 Fix ambiguities and errors
* Check the start_station_name whether have the unique start_station_id
```sql
-- 1541 start_station_name
-- 1263 start_station_id
-- check distinct values which means some station_id has more than 1 names

SELECT 
    COUNT(DISTINCT trim(start_station_name)), 
    COUNT(DISTINCT trim(start_station_id))
FROM trip_2022_clean;
```

* Use window function also discover same start_station_id have lots of different lat & lng
```sql
SELECT 
    start_station_id,
    start_lat,
    start_lng,
    COUNT(*) AS no_rides,
    ROW_NUMBER() OVER (PARTITION BY start_station_id ORDER BY count(*) DESC) AS top
FROM trip_2022_clean
GROUP BY 1, 2, 3
ORDER BY 1 DESC, 4 DESC, 5
;
```

* For viz requires each station has unique lat & lng
```sql
-- use start_station_id to identify unique start_lat & lng by ranking 1 with the most rides 

SELECT
    s.start_station_id,
    s.start_lat,
    s.start_lng,
    s.no_rides
FROM 
(
    SELECT 
        start_station_id,
        start_lat,
        start_lng,
        count(*) AS no_rides,
        -- Use PARTITION BY function to rank num of the lat & lng by each station_id
        ROW_NUMBER() OVER (PARTITION BY start_station_id ORDER BY count(*) DESC) AS top
    FROM trip_2022_clean
    GROUP BY 1, 2, 3
    ORDER BY 1, 4 DESC, 5
) AS s
-- Find the top 1 of each station_id which means the most accrate location
WHERE s.top = 1
ORDER BY 2, 3, 4 DESC
;
```

* Update start_station_id by unique start_lat & lng of the most rides
```sql
-- transaction

START TRANSACTION;

UPDATE trip_2022_clean AS t
JOIN 
(
    SELECT
        s.start_station_id,
        s.start_lat,
        s.start_lng,
        s.no_rides
    FROM 
    (
        SELECT 
            start_station_id,
            start_lat,
            start_lng,
            count(*) AS no_rides,
            -- Use PARTITION BY function to rank num of the lat & lng by each station_id
            ROW_NUMBER() OVER (PARTITION BY start_station_id ORDER BY count(*) DESC) AS top
        FROM trip_2022_clean
        GROUP BY 1, 2, 3
        ORDER BY 1, 4 DESC, 5
    ) AS s
	-- Find the top 1 of each station_id which means the most accrate location
    WHERE s.top = 1
    ORDER BY 2, 3, 4 DESC
) AS i
ON t.start_station_id = i.start_station_id
SET t.start_lat = i.start_lat,
    t.start_lng = i.start_lng
;

COMMIT;
```

* Check the start_station_id which have more than 1 name
```sql
-- 554 rows have 'no_id' > 1 group by start_station_name & id

WITH start_stations AS
(
    SELECT 
        start_station_name, 
        start_station_id, 
        COUNT(*) AS rides
    FROM trip_2022_clean
    GROUP BY 1 , 2
    ORDER BY 3 DESC, 1
),
count_id AS
(
    SELECT
        start_station_id, 
        COUNT(*) AS no_id
    FROM start_stations
    GROUP BY 1
    ORDER BY 2 DESC, 1 DESC
)
SELECT 
    a.start_station_name,
    a.start_station_id,
    a.rides,
    c.no_id
FROM start_stations AS a
INNER JOIN count_id AS c
ON a.start_station_id = c.start_station_id
WHERE c.no_id > 1
ORDER BY 4 DESC, 2 DESC
;
```

* Update start_station_name to the name of the most rides station by the same station_id
```sql
START TRANSACTION;

UPDATE trip_2022_clean AS t
JOIN 
(
    SELECT
        s.start_station_name,
        s.start_station_id
    FROM 
    (
        SELECT 
            start_station_name,
            start_station_id,
            count(*) AS no_rides,
            -- Use PARTITION BY function to rank num of the lat & lng by each station_id
            ROW_NUMBER() OVER (PARTITION BY start_station_id ORDER BY count(*) DESC) AS top
        FROM trip_2022_clean
        GROUP BY 1, 2
        ORDER BY 2 DESC, 4, 3 DESC, 1
    ) AS s
    WHERE s.top = 1
) AS i
ON t.start_station_id = i.start_station_id
SET t.start_station_name = i.start_station_name
;

COMMIT;
```

* Handle with ambiguities and errors of end_station_name & id by the same ways\
**MySQL query**: [02 Data clean](https://github.com/WJ-IIOI/Cyclistic_Bike_Share_Analysis_Using_MySQL_Tableau/blob/main/02_trip_2022_clean.sql)

### 3.9 Data-cleaning verification
Verifying the cleaned data ensures that the insights you gain from analysis can be trusted:
* **Checked duplicate data** — the data does not have duplicate values
* **Checked irrelevant data** — each trip record is relevant of 2022
* **Checked outliers** — removed outliers which ride_length < 1min or > 24hr
* **Checked missing values** — removed some data with missing values
* **Checked Date-Time format** — the date and time is consistent
* **Checked business Logic** — fix ambiguous data and business Logic 
* **Checked data formats** — the columns are accurate in format
* **Checked data consistency** — after cleaning up the data, the data for the 12 months remained consistent
* **Checked integrity** — the data is appropriate to answer the business questions

Now, the data is clean, accurate, consistent, complete and ready for ANALYSIS.


## **STEP 4 ANALYZE – Find the insights**
At this step, for better answering the business task, I will use MySQL for data analysis, and then use Tableau for visualization.
I will identify trends in how annual members and casual riders use Cyclistic bikes differently by analyzing the following:
* Number and proportion by user type
* Number and proportion by bike type
* Average of ride length by user type
* Distribution of ride length by user type
* Distribution of stations by user type
* Analyzing by year, month, weekday and hour respectively
### 4.1 Analyze number and proportion by user type
```sql
-- caculate number and proportion by year
SELECT 
    user_type,
    COUNT(*) AS rides,
    ROUND((COUNT(*) / (SELECT COUNT(*) FROM trip_2022_clean)) * 100, 2) AS pct
FROM trip_2022_clean
GROUP BY 1
;
```
![Alt Text](C:\Users\linji\OneDrive\Desktop)

```sql
-- caculate number and proportion by month
SELECT 
    EXTRACT(MONTH FROM started_at) AS month,
    user_type,
    COUNT(*) AS rides,
    ROUND((COUNT(*) / (SELECT COUNT(*) FROM trip_2022_clean)) * 100, 2) AS pct
FROM trip_2022_clean
GROUP BY 1 , 2
;
```
![Alt Text](C:\Users\linji\OneDrive\Desktop)

```sql
-- caculate number and proportion by weekday
SELECT 
    WEEKDAY(started_at) AS weekday,
    user_type,
    COUNT(*) AS rides,
    ROUND((COUNT(*) / (SELECT COUNT(*) FROM trip_2022_clean)) * 100, 2) AS pct
FROM trip_2022_clean
GROUP BY 1 , 2
ORDER BY 1 , 2
;
```
![Alt Text](C:\Users\linji\OneDrive\Desktop)

```sql
-- caculate number and proportion by hour
SELECT 
    HOUR(started_at) AS hour,
    user_type,
    COUNT(*) AS rides,
    ROUND((COUNT(*) / (SELECT COUNT(*) FROM trip_2022_clean)) * 100, 2) AS pct
FROM trip_2022_clean
GROUP BY 1 , 2
ORDER BY 1 , 2
;
```
![Alt Text](C:\Users\linji\OneDrive\Desktop)

> **Key insights:**
* 123
* 345

### 4.2 Caculate number and proportion by bike type
```sql
-- caculate number and proportion by year
SELECT 
    bike_type,
    user_type,
    COUNT(*) AS rides,
    ROUND((COUNT(*) / (SELECT COUNT(*) FROMntrip_2022_clean)) * 100, 2) AS pct
FROM trip_2022_clean
GROUP BY 1 , 2
ORDER BY 3 DESC
;
```
![Alt Text](C:\Users\linji\OneDrive\Desktop)

> **Key insights:**
* 123
* 345
* 
### 4.3 Analyze average of ride length by user type
### 4.4 Analyze distribution of ride length by user type
### 4.5 Analyze distribution of stations by user type




## **STEP 5 SHARE –  Visualizing findings**


## **STEP 6 ACT – Conclusions from the analysis**

## 6.1 Futher thinkings
* More bikes?
* More stations?

```
Hello, world!
```
