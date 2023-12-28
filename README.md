# New-Yor-City-Short-Term-Rental-Insight-
A Data Analytics Project  Using Micro soft Excel, SQL and Tableau for Visualization
## Table of Content

  - [Project Overview](#project-overview)
  - [Dataset URL](#Dataset-URL)
  - [Data-Wrangling-and-Cleaning](#Data-Wrangling-and-Cleaning)
  - [Data Analysis and Insights Generation](#Data-Analysis-and-Insights-Generation)
  - [Presenting my findings for Business Impact](#Presenting-my-findings-for-Business-Impact)
  - [Tableau Result and Findings](#Tableau-Result-and-Findings)
  - [Recommendations And Conclusion](#Recommendations-And-Conclusion)
  - [SQL Codes Result Worked With](#SQL-Codes-Result-Worked-With)
### Project Overview
This project analysis is to analyze the New York City short-term rental insights, some data was given with three different tables which are Prices, Reviews and room types. This analysis will help Pillow Palooza to know the most profitable areas and properties to invest in.
The project will be divided into three parts:
- Data Wrangling and Cleaning
- Data Analysis and Insights Generation
- Presenting your findings for Business Impact
### Dataset URL  
postgres://Test:bQNxVzJL4g6u@ep-noisy-flower-846766-pooler.us-east-2.aws.neon.tech/Airbnb

### Data Wrangling and Cleaning
The data which was a raw data was cleaned with the help of the google spreadsheet these steps were taken:
Data Collection, Data Inspection, Data Cleaning, Data Transformation, Data Integration, Data Formatting, Data Validation and  Documentation

### Data Analysis and Insights Generation
The tool that was used here was the Structured Query Language (SQL), where the three tables which are the prices, reviews and room types table were being analysed based on the question of the sprints.

### Presenting my findings for Business Impact
In this stage, tableau public was used to analys and present my business questions. These questions were based on some questions which are:
- Most popular Neighborhood for short-term rental in New York City.
- Most commonly rented property types of Airbnb in New York City.
- Top 5 average rental prices in New York City Neighborhood.
### Tableau Result and Findings
![image](https://github.com/Chuks200/New-Yor-City-Short-Term-Rental-Insight-/assets/150162291/a6ebd5e4-20b3-408f-82f7-196ac10f0686)

[The Tableau dashboard link](https://public.tableau.com/app/profile/chuks.chukwunonso.agbataekwe/viz/Mystryproject2/Dashboard2?publish=yes)

[The loom presentation video](https://www.loom.com/share/4e6ea0b6e66c47a8ba53548f489cb24c?sid=d2bfd390-bf91-4d95-b5f9-20eb74b40d5a)

![image](https://github.com/Chuks200/New-Yor-City-Short-Term-Rental-Insight-/assets/150162291/fb537237-47ec-40a5-bbbd-1d3c6fbdb979)
#### Most popular Neighborhood for short-term rental in New York City.

![image](https://github.com/Chuks200/New-Yor-City-Short-Term-Rental-Insight-/assets/150162291/70b4a980-4230-402f-9c1a-b7365d645f25)
#### Most commonly rented property types of Airbnb in New York City.

![image](https://github.com/Chuks200/New-Yor-City-Short-Term-Rental-Insight-/assets/150162291/a3b34573-8443-4cd1-9d98-149be96769e5)
##### Top 5 average rental prices in New York City Neighborhood

### Recommendations And Conclusion
In recommendation to Pillow Palooza, this points should be put into consideration
- Williamsburg should be considered as a better neighbourhood to start-up an Airbnb short-term rental, this is because it has the highest amount of booking per year in New York City. It should also be rented on an average price of £142 to be affordable for customers.
- Entire home/apartment and private rooms should be the properties to be invested in, this is because people in the New York neighbourhood prefer to rent such properties than the share room apartment.

In conclusion, from the SQL analysis and tableau presentation, it shows how important and profitable the New York Airbnb investment is, and Williamsburg is a suitable neighbourhood for pillow palooza to invest in, this is with the aid of properties such as entire home/apartment and private rooms.

### SQL Codes Result Worked With
  ``` beekeeper studio
-- Example query (PostgreSQL)
SELECT * FROM "prices";

-- Tips:
-- (*) Table names containing punctuation, capitalization, or spaces should be
--     quoted, e.g. "Test Data.csv".
-- (*) Add more data by using the Upload Data button.
-- (*) Create additional schemas for namespacing your tables, e.g. "CREATE SCHEMA my_schema;".
-- (*) When querying tables created outside of the public (default) schema,
--     be sure to specify the desired schema, e.g. "SELECT * FROM my_schema."my data.csv";".;

--1. What is the most common room type in NYC Airbnb listings?
SELECT room_type,  COUNT (*) AS count 
FROM room_types   
GROUP BY room_type
ORDER BY count DESC
LIMIT 1;

--2. What is the average price of a listing by room type?
SELECT AVG(p.price) AS avg_room_type 
FROM prices p
JOIN room_types r ON p.listing_id = r.listing_id
WHERE room_type = 'shared room'



--3. Which borough has the highest average price per month?
SELECT borough, AVG(price) AS average_price
FROM prices
GROUP BY borough
ORDER BY average_price DESC
LIMIT 1;

--4. How many listings of each room type are in each borough?
Complete the ___???___ with the correct answer.

SELECT p.borough, r.room_type, COUNT(*) AS count_listing
FROM prices p
JOIN room_types r ON p.listing_id = r.listing_id
GROUP BY p.borough, r.room_type;


--6.. What is the distribution of listing prices by borough?
Complete the ___??___ with the correct answer

SELECT borough, COUNT(*) AS count_listings, AVG(price) AS average_price, MIN(price) AS min_price, MAX(price) AS max_price
FROM prices
GROUP BY borough;


--7.. What is the estimated amount of revenue generated by hosts in each borough?
Complete the ___???___ with the correct answer.

SELECT p.borough , SUM (price * booked_days_365) AS revenue
FROM prices p
JOIN reviews r ON p.listing_id = r.listing_id
GROUP BY p.borough;


--8.. What is the average price per month for listings in each neighborhood?
Complete the ___???___ with the correct answer.

SELECT p.neighbourhood ,r.room_type, AVG(p.price_per_month) as avg_price_per_month
FROM prices p
JOIN  room_types r on p.listing_id = r.listing_id
WHERE neighbourhood = 'Sea Gate'
GROUP BY p.neighbourhood ,r.room_type;

--9.. How many listings have no reviews?
SELECT COUNT(listing_id),  number_of_reviews
FROM reviews
WHERE number_of_reviews < 1
GROUP BY listing_id,  number_of_reviews;
---








