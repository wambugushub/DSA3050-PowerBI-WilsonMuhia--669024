# California Real Estate Market Analysis

## DSA 3050A — Business Intelligence & Data Visualization

### Student Information

* **Student Name:** Wilson
* **Registration Number:** *669024*
* **Course:** DSA 3050A — Business Intelligence & Data Visualization
* **Software:** Microsoft Power BI Desktop
* **Project:** End Semester Practical Examination
* **Dataset:** California Real Estate Dataset

---

## 1. Project Overview

This project develops a complete Business Intelligence solution using Microsoft Power BI to analyze residential real estate listings in California.

The project follows the complete Business Intelligence development process:

**Dataset → Power Query → Data Model → DAX → Dashboard → Business Insights**

The analysis focuses on property prices, property characteristics, geographic differences, and factors that may be associated with differences in property values.

The examination requires students to acquire and understand a real-world dataset, perform data preparation using Power Query, develop an analytical data model, create DAX calculations, and build interactive dashboards.

---

## 2. Dataset Description

The dataset used in this project is the **California Real Estate Dataset** provided as `RealEstate_California.csv`.

The dataset contains **35,389 property records and 39 variables**. It contains information about residential property listings, including prices, property characteristics, location, construction information, and listing information.

### Main Variables

| Variable             | Description                                        |
| -------------------- | -------------------------------------------------- |
| `id`                 | Unique property/listing identifier                 |
| `price`              | Listed property price                              |
| `pricePerSquareFoot` | Price per square foot                              |
| `city`               | City where the property is located                 |
| `county`             | County where the property is located               |
| `zipcode`            | Property ZIP code                                  |
| `state`              | State                                              |
| `datePostedString`   | Date the property listing was posted               |
| `yearBuilt`          | Year the property was constructed                  |
| `livingArea`         | Property living area                               |
| `bathrooms`          | Number of bathrooms                                |
| `bedrooms`           | Number of bedrooms                                 |
| `buildingArea`       | Building area                                      |
| `parking`            | Parking information                                |
| `garageSpaces`       | Number of garage spaces                            |
| `pool`               | Indicates whether the property has a pool          |
| `spa`                | Indicates whether the property has a spa           |
| `homeType`           | Type of property                                   |
| `isNewConstruction`  | Indicates whether the property is new construction |
| `hasGarage`          | Indicates whether the property has a garage        |
| `hasPetsAllowed`     | Indicates whether pets are allowed                 |

The examination recommends datasets with at least 20,000 records, multiple numerical and categorical variables, date/time information, and variables that can support KPI calculations. This dataset satisfies those requirements.

---

## 3. Dataset Source

**Dataset:** California Real Estate Dataset
**File:** `RealEstate_California.csv`

**Source:** *(https://www.kaggle.com/datasets/yellowj4acket/real-estate-california)*


---

## 4. Business Problem

The California real estate market contains properties with substantial differences in price, size, location, property type, and amenities.

The purpose of this project is to develop an interactive Business Intelligence solution that can help users understand:

* Overall property price levels
* Geographic differences in property prices
* Differences between property types
* The relationship between property size and price
* The influence of property characteristics such as bedrooms, bathrooms and garages
* Differences between new and existing properties
* Changes in property prices over time

The main business problem is:

> **How can real estate listing data be transformed into useful business intelligence that explains property prices and identifies important differences across California's real estate market?**

---

## 5. Analytical Questions

The Power BI solution is designed to answer the following questions:

1. What are the overall average and median property prices in the dataset?
2. Which California counties have the highest average property prices?
3. How does property size relate to property price?
4. How do bedrooms, bathrooms, garages and pools relate to property prices?
5. How do property prices vary across property types, locations and time?

---

# 6. Data Preparation Using Power Query

Power Query was used to transform the raw dataset into a form suitable for analysis.

The examination requires significant Power Query transformations and documentation of at least eight transformations using the format:

**Problem → Transformation → Reason → Result**.

## Transformation 1 — Removing Unnecessary Columns

### Problem

The dataset contained an unnecessary imported index column named `Column 1`.

### Transformation

The `Column 1` column was removed using **Remove Columns** in Power Query.

<img width="453" height="277" alt="image" src="https://github.com/user-attachments/assets/3937826a-5b6a-4ac5-859d-22cecdbc1e1f" />


### Reason

The column does not represent a meaningful business variable.

### Result

The dataset contains only relevant analytical fields.

---

## Transformation 2 — Correcting Data Types

### Problem

Several variables required appropriate data types before analysis.

### Transformation

Data types were corrected for numerical, categorical and date variables.

For example:

* Price → Decimal Number
* Bedrooms → Decimal/Whole Number
* Bathrooms → Decimal Number
* Year Built → Whole Number
* Listing Date → Date
* City → Text
* County → Text

 <img width="342" height="200" alt="image" src="https://github.com/user-attachments/assets/d46ce38d-6348-4078-8633-b71b66a3c1a2" />


### Reason

Correct data types are necessary for accurate calculations, filtering and time-based analysis.

### Result

The dataset is prepared for modelling and DAX calculations.

---

## Transformation 3 — Removing Duplicate Records
<img width="1159" height="652" alt="image" src="https://github.com/user-attachments/assets/a7039960-beca-4da0-b168-1122ba00a056" />


### Problem

Duplicate listing IDs could result in properties being counted more than once.

### Transformation

Duplicate records were removed using the property/listing ID.

### Reason

Each listing should be represented by a unique analytical record.

### Result

Duplicate listing records were removed.

---

## Transformation 4 — Handling Missing Values

### Problem

Some fields contained null or missing values.

<img width="435" height="369" alt="image" src="https://github.com/user-attachments/assets/68ab5db9-121e-46bb-8c72-89f59e3e7cff" />


### Transformation

Missing values in non-essential descriptive fields were handled appropriately, while records without a usable listing date were excluded from time-based analysis.

### Reason

Missing values can interfere with analysis, particularly when they occur in important fields.

### Result

The dataset contains more reliable values for analysis.

---

## Transformation 5 — Cleaning Text Fields

### Problem

Text fields may contain unnecessary spaces or hidden characters.

### Transformation

<img width="646" height="432" alt="image" src="https://github.com/user-attachments/assets/8c491e4b-54fc-45ba-9c52-cec243123501" />


The **Trim** and **Clean** transformations were applied to important categorical fields such as city, county and property type.

### Reason

Inconsistent text formatting can create duplicate categories.

### Result

Categorical values are standardized for analysis.

---

## Transformation 6 — Standardizing Levels

### Problem

The Levels feild is full of the same data in different formats.

<img width="336" height="580" alt="image" src="https://github.com/user-attachments/assets/1d6a3506-c9a9-4b8d-b7f8-a4fb83373b2a" />


### Transformation

Levels values were standardized into more consistent categories.

<img width="360" height="416" alt="image" src="https://github.com/user-attachments/assets/e3792b4b-324b-4769-8559-961f2cebe90f" />


### Reason

Readable categories improve dashboard presentation and interpretation.



---

## Transformation 7 — Creating Price Categories

### Problem

Analyzing individual property prices can make it difficult to identify broad market segments.

### Transformation

A conditional column called `PriceCategory` was created.

The categories are:

* Under $500K
* $500K–$1M
* $1M–$2M
* $2M+

 <img width="1110" height="566" alt="image" src="https://github.com/user-attachments/assets/f7b8e91e-a848-4e22-8332-ab29d4a8a639" />


### Reason

Price categories allow properties to be compared across broad market segments.

### Result

The dataset contains an additional business dimension for price analysis.

---

## Transformation 8 — Creating Property Age

### Problem

The original dataset contains `yearBuilt`, but property age is more useful for direct analysis.

### Transformation

A calculated column called `PropertyAge` was created using the property's construction year.

<img width="678" height="432" alt="image" src="https://github.com/user-attachments/assets/4e99f607-7876-410d-858d-6d8867cc91b3" />


### Reason

Property age can be used to investigate whether newer or older properties have different price levels.

### Result

The dataset contains a new variable for analysing property age.

---

## Transformation 9 — Creating Bedroom Categories

### Problem

The raw bedroom count can be difficult to interpret when comparing groups.

### Transformation

A `BedroomCategory` column was created.

The categories include:

* 0–1 Bedroom
* 2 Bedrooms
* 3 Bedrooms
* 4 Bedrooms
* 5+ Bedrooms

<img width="909" height="482" alt="image" src="https://github.com/user-attachments/assets/a325d821-3675-452d-908c-4c128f26b2b9" />
 

### Reason

This allows properties to be grouped into meaningful bedroom segments.

### Result

Bedroom-based comparisons can be performed more effectively.

---

## Transformation 10 — Creating Dimension Tables

### Problem

A single flat table can make analytical modelling less efficient.

### Transformation

Reference queries were used to create dimension tables for location.

### Reason

A dimensional model improves organization and filtering.

### Result

The data can be structured using a star-schema approach.

---
# 7. Data Model 
## DimDate

The DimDate table supports time-based analysis.

It contains:

Date
Year
Month Number
Month
Month Year
Quarter

## DimLocation

The DimLocation table contains geographic information such as:

State
County
City
ZIP Code

This dimension allows users to analyse property prices geographically.

# 8. Relationships

The dimensions are connected to the central FactProperty table using one-to-many relationships where appropriate.

<img width="1024" height="885" alt="image" src="https://github.com/user-attachments/assets/e32737e3-57a1-448a-b63d-45e35d44a5f7" />


# 9. DAX Measures

A minimum of 12 meaningful DAX measures is required by the examination.

The following measures were developed.

### 1. Total Properties

<img width="305" height="69" alt="image" src="https://github.com/user-attachments/assets/ed3dffcd-5603-42f3-b131-e1cef7c61669" />


Counts the unique property listings.

### 2. Total Property Value

<img width="231" height="64" alt="image" src="https://github.com/user-attachments/assets/c673e8a8-662b-4bc9-99d6-d74bcbc6c928" />


Calculates the total listed value of properties.

### 3. Average Property Price

<img width="242" height="67" alt="image" src="https://github.com/user-attachments/assets/0a740d92-104c-40a9-a706-74f4feab9a8d" />


Calculates the average listed property price.

### 4. Median Property Price

<img width="250" height="78" alt="image" src="https://github.com/user-attachments/assets/56b109e7-ec7e-4f73-afab-566d67ae4c45" />


Calculates the median property price.

### 5. Average Price Per Square Foot

<img width="322" height="72" alt="image" src="https://github.com/user-attachments/assets/6433a5fc-45d2-498b-b5f8-73765f857998" />


Measures the average property price relative to living area.

### 6. Average Living Area

<img width="275" height="72" alt="image" src="https://github.com/user-attachments/assets/396d9d02-4639-4cab-8116-3cc940f4f9e2" />


Calculates the average living area.

### 7. Average Bedrooms

<img width="266" height="67" alt="image" src="https://github.com/user-attachments/assets/33da2e78-e284-4030-9d2a-4125655b3c8b" />


Calculates the average number of bedrooms.

### 8. Average Bathrooms

<img width="249" height="67" alt="image" src="https://github.com/user-attachments/assets/1b4a349f-78c8-49a6-b15a-a1e43db379fa" />


Calculates the average number of bathrooms.

### 9. Properties With Garage

<img width="308" height="104" alt="image" src="https://github.com/user-attachments/assets/00ac56dd-771b-4dbd-88a3-9b3dff770b07" />


Counts properties that have greater than or equal to 1 garage space.

### 10. Properties With Pool

<img width="268" height="116" alt="image" src="https://github.com/user-attachments/assets/82cd7146-2d68-4620-800c-9ba9b361da8b" />


Counts properties with a pool.

### 11. New Construction Properties

<img width="298" height="113" alt="image" src="https://github.com/user-attachments/assets/a4a68117-ea46-45a7-9152-76200f97adbe" />


Counts properties identified as new construction.

### 12. Garage Percentage

<img width="296" height="146" alt="image" src="https://github.com/user-attachments/assets/93aea03f-bb1f-4347-93a6-84203cdfb885" />


Calculates the percentage of properties with garages.

### 13. New Construction Percentage

<img width="307" height="144" alt="image" src="https://github.com/user-attachments/assets/bbcb92bf-6f55-426d-9f91-fb8acab5c3bb" />


Calculates the proportion of listings classified as new construction.

### 14. Price Difference from Average

<img width="301" height="153" alt="image" src="https://github.com/user-attachments/assets/31701a29-4862-4753-9fed-97b6327b7c2b" />


Measures the difference between the selected context's average price and the overall market average.

### 15. County Price Rank

<img width="343" height="172" alt="image" src="https://github.com/user-attachments/assets/3024f82b-33ad-442d-bdac-e3ad83cf9990" />


Ranks counties according to average property price.

The measures use DAX functions such as `DISTINCTCOUNT`, `CALCULATE`, `DIVIDE`, `ALL`, and `RANKX`, demonstrating both core and advanced analytical calculations. The examination specifically identifies these functions as examples of advanced DAX techniques.

---

# 10. Dashboard Design

The Power BI report contains three main dashboard pages following the required progression:

**Overview → Detailed Analysis → Deeper Insights**

This structure follows the dashboard guidance in the examination document.

---

## Page 1 — Executive Overview

<img width="1302" height="726" alt="image" src="https://github.com/user-attachments/assets/7f8b09db-32c9-469a-a58b-927b612a1a35" />

---

# Page 2 — Property & Location Analysis

<img width="1269" height="746" alt="image" src="https://github.com/user-attachments/assets/9c8f0148-1d1f-4e39-a8c7-17c359d84cc7" />


---

# Page 3 — Market Diagnostic Analysis

<img width="1302" height="735" alt="image" src="https://github.com/user-attachments/assets/a8a38a27-2fef-432e-9caa-d8d994ee9a79" />




---

# 11. Key Business Insights

The Power BI dashboard transforms the California real estate listing data into useful business intelligence by showing differences in property prices, locations, property sizes, home types, bedrooms, pools, and time periods.

The dashboard shows that the California real estate market has substantial variation in property prices. The overall average property price is approximately $1.21 million, while the median property price is approximately $694,700. This large difference suggests that some very expensive properties are increasing the overall average.

Geographically, property prices vary considerably between counties. Santa Barbara County has the highest average property price at approximately $3.6 million, followed by Napa County and San Mateo County. The dashboard also shows differences in average price per square foot, with Modoc County having the highest value among the counties displayed.

Property characteristics also have an important relationship with price. The scatter plot shows a positive relationship between living area and property price, meaning that larger properties generally tend to have higher prices. Properties with more bedrooms also tend to have higher average prices, with 4+ bedroom properties averaging approximately $3.1 million.

Property type is another important factor. Single-family homes account for approximately 62.46% of the properties, making them the dominant property type in the dataset. Lots and condos represent smaller proportions of the market.

The dashboard also indicates that properties with pools have a higher average price than properties without pools. Properties with a pool have an average price of approximately $2.9 million, compared with approximately $1.0 million for properties without a pool.

Finally, property prices change over time. The average property price generally increased between 2017 and 2019, reaching a peak of approximately $1.5 million in 2019, before declining toward 2021.

Therefore, the main business problem is addressed by using Power BI to identify price patterns, geographic differences, property characteristics, and changes over time, enabling real estate businesses and potential buyers or investors to better understand the California property market.

---

#12. Analytical Questions

##1. What are the overall average and median property prices?
Average: $1.21M
Median: $694.7K

The higher average indicates the presence of high-priced properties.

##2. Which counties have the highest average prices?

The highest include:

Santa Barbara County: ~$3.6M
Napa County: ~$2.85M
San Mateo County: ~$2.65M
Marin County: ~$2.48M
##3. How does property size relate to price?

There is a positive relationship between living area and price. Larger properties generally have higher prices.

##4. How do property characteristics relate to price?

Properties with more bedrooms generally have higher prices. Properties with pools also have higher average prices (~$2.9M vs ~$1.0M without pools). The dashboard does not provide enough information to conclude the specific effect of bathrooms and garages.

##5. How do prices vary by type, location and time?

Single-family homes dominate the dataset at 62.46%. Prices vary significantly by county, with Santa Barbara among the highest. Average prices increased significantly up to 2019, when they reached about $1.5M, before declining toward 2021.
---

# 13. Conclusion

The Power BI analysis shows that California's real estate market has significant differences in property prices, locations, sizes, and property characteristics. The average property price is about $1.21M, with Santa Barbara County having some of the highest average prices. Larger properties, properties with more bedrooms, and properties with pools generally have higher prices. Prices also changed considerably over time, reaching a peak around 2019. Overall, the dashboard provides useful insights that can support property pricing, investment decisions, and market analysis.

---



The examination states that students should be prepared to explain the transformations, modelling decisions, DAX measures and dashboard features used in their submission.
