# CAR-SALES
The analysis focuses on the car sales dataset, providing critical insights into sales trends, performance metrics, and market behaviors to support data-driven decision-making.

## Table View
- Below is the table view of the dataset to be analyzed. The first five rows are displayed for an initial overview, providing key insights into the data.

|Car_id | Date | Customer Name | Gender | Annual Income | Dealer_Name | Company | Model | Engine | Transmission | Color | Price ($) | Dealer_No | Body Style | Phone | Dealer_Region|
|----|---|----|------|----|-----|-----|----|----|----|------|-----|-------|------|------|----|
|C_CND_000001 | 1/2/2022 | Geraldine | Male | 13500 | Buddy Storbeck's Diesel Service Inc | Ford | Expedition | DoubleÂ Overhead Camshaft | Auto | Black | 26000 | 06457-3834 | SUV | 8264678 | Middletown|
|C_CND_000002 | 1/2/2022 | Gia | Male | 1480000 | C & M Motors Inc | Dodge | Durango | DoubleÂ Overhead Camshaft | Auto | Black | 19000 | 60504-7114 | SUV | 6848189 | Aurora|
|C_CND_000003 | 1/2/2022 | Gianna | Male | 1035000 | Capitol KIA | Cadillac | Eldorado | Overhead Camshaft | Manual | Red | 31500 | 38701-8047 | Passenger | 7298798 | Greenville|
|C_CND_000004 | 1/2/2022 | Giselle | Male | 13500 | Chrysler of Tri-Cities | Toyota | Celica | Overhead Camshaft | Manual | Pale White | 14000 | 99301-3882 | SUV | 6257557 | Pasco|
|C_CND_000005 | 1/2/2022 | Grace | Male | 1465000 | Chrysler Plymouth | Acura | TL | DoubleÂ Overhead Camshaft | Auto | Red | 24500 | 53546-9427 | Hatchback | 7081483 | Janesville|

## Data Insight
> Gender Representation: Male customers account for the highest car purchases, contributing significantly to overall revenue generation in the dataset.

> Top Sales Regions: Sales are distributed across multiple regions like Middletown, Aurora, Greenville, Pasco, Janesville and Austin.

> Income Levels: Annual incomes range from $10,080 to $11,2000,000, showing a vast range in customer profiles. This could indicate different pricing strategies or product preferences within these income brackets.

> Price Range: Vehicle prices range from $1,200 to $85,800 , offering insights into the affordability and market segmentation of the vehicles sold.

> Color Trends: Pale White  dominate the dataset, showing potential customer color preferences.

## SQL QUERIES 
```SQL
create database car;
use car;

select * from [dbo].[car_data_usa 2];
---Questions
/*1. Retrieve all the car details from the dataset.

2. Fetch the names of all customers who purchased cars.

3. Get a list of distinct car companies available in the dataset.

Filtering Data:

4. Retrieve all car records where the price is greater than $400,000.

5. Fetch details of cars sold in the "Austin" region.

6. List all cars with a specific transmission type (e.g., "Automatic").

Aggregation and Grouping:

7. Find the average price of cars sold by each company.

8. Get the total sales revenue generated in each dealer region.

9. Count the number of cars sold by gender.*/

--1.
select * from [dbo].[car_data_usa 2];
--2.
select customer_name from [dbo].[car_data_usa 2];
--3.
select distinct Company from [dbo].[car_data_usa 2];
--4.
select * from [dbo].[car_data_usa 2]
where price >400000;
--5.
select * from [dbo].[car_data_usa 2]
where Dealer_REGION = 'Austin';
--6.
select * from [dbo].[car_data_usa 2]
where Transmission='auto';
--7.
select AVG(price) as Average_price,Company from [dbo].[car_data_usa 2]
group by company;
--8.
SELECT SUM(CAST(COALESCE(annual_income, 0) AS BIGINT)) as Total_revenue , Dealer_Region
FROM [dbo].[car_data_usa 2]
group by Dealer_Region;

--9.
select COUNT(CAR_ID) as Total_CAR ,Gender from [dbo].[car_data_usa 2]
group by Gender;

SELECT SUM(cast(annual_income AS BIGINT))
FROM [dbo].[car_data_usa 2];
```

## Visualization
### Excel Dashbord

![car excel](https://github.com/user-attachments/assets/61d1e949-e2c7-4085-a903-f01095359060)

