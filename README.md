```sql
-- Dataset: City Bike Lane Data
-- Source: Data Analytics Certificate Course, Break Into Tech


-- Step 1: Create a table for city bike lanes data
CREATE TABLE BIT_DB.CityBikeLanes (
    id INTEGER PRIMARY KEY,
    year_installed YEAR NOT NULL,
    year_updated YEAR NOT NULL,
    street VARCHAR NOT NULL,
    width_feet INTEGER NOT NULL,
    safetyrating INTEGER NOT NULL,
    protected VARCHAR NOT NULL
);

-- Step 2: Insert data into the CityBikeLanes table
INSERT INTO BIT_DB.CityBikeLanes VALUES
(1, 2012, 2020, 'Chestnut', 4, 4, 'yes'),
(2, 2016, 2020, 'Walnut', 4, 3.8, 'yes'),
(3, 2011, 2020, 'Market', 3.5, 2, 'no'),
(4, 2008, 2020, 'Locust', 4, 5, 'yes'),
(5, 2002, 2020, 'South', 4.5, 4.3, 'no'),
(6, 2012, 2021, '18th', 4, 4.7, 'yes'),
(7, 2016, 2021, '2nd', 4, 3.7, 'yes'),
(8, 2011, 2021, 'Lombard', 3.5, 2.2, 'no'),
(9, 2008, 2021, 'Pine', 4, 4.9, 'yes'),
(10, 2002, 2021, 'Tasker', 4.5, 4.8, 'no'),
(11, 2012, 2020, 'Earp', 4, 4.1, 'yes'),
(12, 2016, 2020, 'Titan', 4, 3.8, 'yes'),
(13, 2011, 2020, 'Manning', 3.4, 2, 'no'),
(14, 2008, 2020, 'Fieldcrest', 4, 4.9, 'yes'),
(15, 2002, 2020, 'York', 4.5, 4.5, 'no'),
(16, 2012, 2021, 'Race', 4, 4.7, 'yes'),
(17, 2016, 2021, 'Museum', 4, 3.8, 'yes'),
(18, 2011, 2021, 'Altin', 3.5, 2, 'no'),
(19, 2008, 2021, 'Fred', 4, 4.5, 'yes'),
(20, 2002, 2021, 'Morris', 4.5, 4.7, 'no'),
(21, 2012, 2020, 'Jameson', 4, 3.9, 'yes'),
(22, 2016, 2020, 'MLK', 4, 3.9, 'yes'),
(23, 2011, 2020, 'Parker', 3.6, 2, 'no'),
(24, 2008, 2020, 'Thomas', 4, 4.8, 'yes'),
(25, 2002, 2020, 'Running', 4.5, 4.3, 'no'),
(26, 2012, 2021, 'Waverly', 4, 4.5, 'yes'),
(27, 2016, 2021, 'Addison', 4, 3.9, 'yes'),
(28, 2011, 2021, 'Beaver', 3.5, 2.1, 'no'),
(29, 2008, 2021, 'Kensington', 4, 5, 'yes'),
(30, 2002, 2021, 'Mouse', 4.5, 4.5, 'no'),
(31, 2012, 2020, 'Chestnut', 4, 4.5, 'yes'),
(32, 2016, 2020, 'Walnut', 4, 3.7, 'yes'),
(33, 2011, 2020, 'Market', 3.8, 2, 'no'),
(34, 2008, 2020, 'Locust', 4, 4.8, 'yes'),
(35, 2002, 2020, 'South', 4.5, 4.7, 'no'),
(36, 2012, 2021, '18th', 4, 4.7, 'yes'),
(37, 2016, 2021, '2nd', 4, 3.2, 'yes'),
(38, 2011, 2021, 'Lombard', 3.5, 2.5, 'no'),
(39, 2008, 2021, 'Pine', 4, 5, 'yes'),
(40, 2002, 2021, 'Tasker', 4.5, 4.3, 'no'),
(41, 2012, 2020, 'Earp', 4, 4.5, 'yes'),
(42, 2016, 2020, 'Titan', 4, 3.9, 'yes'),
(43, 2011, 2020, 'Manning', 3.4, 2.7, 'no'),
(44, 2008, 2020, 'Fieldcrest', 4, 4.7, 'yes'),
(45, 2002, 2020, 'York', 4.5, 4.4, 'no'),
(46, 2012, 2021, 'Race', 4, 4.9, 'yes'),
(47, 2016, 2021, 'Museum', 4, 3.4, 'yes'),
(48, 2011, 2021, 'Altin', 3.7, 2, 'no'),
(49, 2008, 2021, 'Fred', 4, 4.7, 'yes'),
(50, 2002, 2021, 'Morris', 4.5, 4.4, 'no'),
(51, 2012, 2020, 'Jameson', 4, 4, 'yes'),
(52, 2016, 2020, 'MLK', 4, 4, 'yes'),
(53, 2011, 2020, 'Parker', 3.6, 2.3, 'no'),
(54, 2008, 2020, 'Thomas', 4, 4.5, 'yes'),
(55, 2002, 2020, 'Running', 4.5, 4.5, 'no'),
(56, 2012, 2021, 'Waverly', 4, 4.7, 'yes'),
(57, 2016, 2021, 'Addison', 4, 3.6, 'yes'),
(58, 2011, 2021, 'Beaver', 3.5, 2.5, 'no'),
(59, 2008, 2021, 'Kensington', 4, 4.9, 'yes'),
(60, 2002, 2021, 'Mouse', 4.5, 4.3, 'no');

-- Step 3: Basic queries to explore the data

-- Get the first 10 records from the CityBikeLanes table
SELECT * FROM CityBikeLanes LIMIT 10;

-- Get all records for bike lanes on 'Walnut' street
SELECT * FROM CityBikeLanes WHERE street = 'Walnut';

-- Step 4: Safety Rating Analysis

-- Provide a list of all bike lanes with an average safety rating of 4.0 or higher
-- Include their respective safety rating and a label "Safe Lane"
WITH average_safety_CTE AS (
    SELECT
        bike_lanes.street,
        AVG(safetyrating) AS average_safety
    FROM CityBikeLanes AS bike_lanes
    GROUP BY bike_lanes.street
)
SELECT 
    street, 
    average_safety,
    'Safe Lane' AS tag
FROM average_safety_CTE
WHERE average_safety >= 4
ORDER BY average_safety DESC;

-- Show all bike lanes with their safety ratings and the average safety rating for each lane
SELECT 
    street, 
    safetyrating,
    AVG(safetyrating) OVER (PARTITION BY street) AS Average_safety_rating
FROM CityBikeLanes;

-- Step 5: Recommendations Based on Safety Rating

-- Provide a list of all bike lanes, both safety ratings for each lane, the average safety rating for each lane,
-- and a recommendation label:
--   "Remove" (avg. safety rating less than 2.5),
--   "Leave As-Is"
