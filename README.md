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

The main fact table is:

**FactProperty**

It contains the property listing and numerical information used for analysis.

Dimension tables include:

* **DimDate**
* **DimLocation**


The model follows a star-schema structure:


```

## FactProperty

The `FactProperty` table contains transactional/listing-level information such as:

* Property ID
* Listing Date
* Price
* Price per Square Foot
* Living Area
* Bedrooms
* Bathrooms
* Building Area
* Garage Spaces
* Property Age
* Property characteristics

## DimDate

The `DimDate` table supports time-based analysis.

It contains:

* Date
* Year
* Month Number
* Month
* Month Year
* Quarter

 <img width="417" height="215" alt="image" src="https://github.com/user-attachments/assets/a8eccf77-85f5-4285-a487-4eb1eef410a8" />


## DimLocation

The `DimLocation` table contains geographic information such as:

* State
* County
* City
* ZIP Code

This dimension allows users to analyse property prices geographically.

## DimProperty

The `DimProperty` table contains descriptive property characteristics such as:

* Home Type
* Bedroom Category
* Price Category
* Year Built
* Property Age
* Garage
* Pool
* New Construction

---

# 8. Relationships

The dimensions are connected to the central `FactProperty` table using one-to-many relationships where appropriate.

The intended structure is:

```text
DimDate       1 ───────── * FactProperty

DimLocation   1 ───────── * FactProperty

DimProperty   1 ───────── * FactProperty
```

Single-direction filtering is used to avoid unnecessary ambiguous filter paths.

The examination requires appropriate relationship cardinality, filter direction, keys and a dedicated Date Table.

---

# 9. DAX Measures

A minimum of 12 meaningful DAX measures is required by the examination.

The following measures were developed.

### 1. Total Properties

```DAX
Total Properties =
DISTINCTCOUNT(FactProperty[id])
```

Counts the unique property listings.

### 2. Total Property Value

```DAX
Total Property Value =
SUM(FactProperty[Price])
```

Calculates the total listed value of properties.

### 3. Average Property Price

```DAX
Average Property Price =
AVERAGE(FactProperty[Price])
```

Calculates the average listed property price.

### 4. Median Property Price

```DAX
Median Property Price =
MEDIAN(FactProperty[Price])
```

Calculates the median property price.

### 5. Average Price Per Square Foot

```DAX
Average Price Per Sq Ft =
AVERAGE(FactProperty[PricePerSqFt])
```

Measures the average property price relative to living area.

### 6. Average Living Area

```DAX
Average Living Area =
AVERAGE(FactProperty[LivingArea])
```

Calculates the average living area.

### 7. Average Bedrooms

```DAX
Average Bedrooms =
AVERAGE(FactProperty[Bedrooms])
```

Calculates the average number of bedrooms.

### 8. Average Bathrooms

```DAX
Average Bathrooms =
AVERAGE(FactProperty[Bathrooms])
```

Calculates the average number of bathrooms.

### 9. Properties With Garage

```DAX
Properties With Garage =
CALCULATE(
    [Total Properties],
    FactProperty[HasGarage] = 1
)
```

Counts properties that have a garage.

### 10. Properties With Pool

```DAX
Properties With Pool =
CALCULATE(
    [Total Properties],
    FactProperty[Pool] = 1
)
```

Counts properties with a pool.

### 11. New Construction Properties

```DAX
New Construction Properties =
CALCULATE(
    [Total Properties],
    FactProperty[IsNewConstruction] = 1
)
```

Counts properties identified as new construction.

### 12. Garage Percentage

```DAX
Garage Percentage =
DIVIDE(
    [Properties With Garage],
    [Total Properties],
    0
)
```

Calculates the percentage of properties with garages.

### 13. New Construction Percentage

```DAX
New Construction % =
DIVIDE(
    [New Construction Properties],
    [Total Properties],
    0
)
```

Calculates the proportion of listings classified as new construction.

### 14. Price Difference from Average

```DAX
Price Difference from Average =
[Average Property Price]
-
CALCULATE(
    [Average Property Price],
    ALL(FactProperty)
)
```

Measures the difference between the selected context's average price and the overall market average.

### 15. County Price Rank

```DAX
County Price Rank =
RANKX(
    ALL(FactProperty[county]),
    [Average Property Price],
    ,
    DESC,
    DENSE
)
```

Ranks counties according to average property price.

The measures use DAX functions such as `DISTINCTCOUNT`, `CALCULATE`, `DIVIDE`, `ALL`, and `RANKX`, demonstrating both core and advanced analytical calculations. The examination specifically identifies these functions as examples of advanced DAX techniques.

---

# 10. Dashboard Design

The Power BI report contains three main dashboard pages following the required progression:

**Overview → Detailed Analysis → Deeper Insights**

This structure follows the dashboard guidance in the examination document.

---

## Page 1 — Executive Overview

### Purpose

The Executive Overview provides a high-level summary of the California real estate market.

### Main KPIs

* Total Properties
* Average Property Price
* Median Property Price
* Average Price Per Square Foot
* Average Living Area

### Main Visuals

* Average Property Price Over Time
* Average Property Price by County
* Properties by Home Type
* Interactive slicers for county, city, property type, price category and year

### Main Question

> What does the California real estate market look like overall?

---

# Page 2 — Property & Location Analysis

### Purpose

This page investigates differences in property values across locations and property characteristics.

### Main Visuals

* Average Property Price by County
* Average Property Price by Bedroom Category
* Average Price Per Square Foot by County
* Property Count by City
* Living Area versus Property Price scatter plot

### Main Question

> Where are properties more expensive and what types of properties dominate different markets?

---

# Page 3 — Market Diagnostic Analysis

### Purpose

This page investigates factors that may explain differences in property prices.

### Main Visuals

* Average Price by Property Age
* Average Price by Garage Availability
* Average Price by Pool Availability
* Average Price by New Construction Status
* Bedrooms versus Price
* County analytical table

### Main Question

> Why might some properties command higher prices than others?

This page focuses on diagnostic analysis rather than simply describing the market.

---

# 11. Interactivity

The report incorporates Power BI interactive features including:

* Slicers
* Cross-filtering
* Drill-down
* Interactive charts
* Dynamic filtering
* Dashboard navigation

The slicers allow users to investigate the market by:

* County
* City
* Property Type
* Price Category
* Year

These features allow users to move from overall market performance to specific locations and property characteristics.

---

# 12. Key Business Insights

The final insights will be based on the completed Power BI analysis.

The report is designed to identify:

1. Differences in average and median property prices.
2. Counties and cities with relatively high property values.
3. Differences in price per square foot between locations.
4. The relationship between living area and property price.
5. Differences in property prices according to bedrooms and bathrooms.
6. Price differences between properties with and without garages.
7. Price differences between properties with and without pools.
8. Differences between new construction and existing properties.
9. Changes in property prices over the available listing period.
10. Property categories that represent significant portions of the market.

**Note:** Specific numerical findings should be entered here after the final Power BI dashboard has been completed so that the README reports the actual results rather than assumed values.

---

# 13. Conclusion

This project demonstrates the use of Business Intelligence techniques to transform raw California real estate listing data into an interactive analytical solution.

Power Query was used to clean and transform the dataset, while a dimensional data model was developed to support efficient analysis. DAX measures were then created to calculate key property and market indicators.

The final Power BI dashboards provide an interactive way to explore property prices, locations, property characteristics and market differences.

The project demonstrates the complete BI workflow:

**Data Acquisition → Data Cleaning → Data Transformation → Data Modelling → DAX Analysis → Dashboard Development → Business Insights**

---

# 14. Repository Structure

The GitHub repository follows the recommended structure:

```text
DSA3050-PowerBI-Wilson-RegNo/
│
├── README.md
│
├── data/
│   └── RealEstate_California.csv
│
├── powerbi/
│   └── DSA3050_Wilson.pbix
│
└── screenshots/
    ├── 01_raw_data.png
    ├── 02_power_query.png
    ├── 03_model.png
    ├── 04_dax_measures.png
    ├── 05_dashboard_overview.png
    ├── 06_dashboard_analysis.png
    ├── 07_dashboard_diagnostics.png
    └── 08_key_insights.png
```

The examination specifically recommends including the dataset, PBIX file, README and screenshots in the repository.

---

# 15. Screenshots

The following screenshots provide evidence of the development process:

| Screenshot                     | Evidence                      |
| ------------------------------ | ----------------------------- |
| `01_raw_data.png`              | Original dataset              |
| `02_power_query.png`           | Power Query transformations   |
| `03_model.png`                 | Completed data model          |
| `04_dax_measures.png`          | DAX calculations              |
| `05_dashboard_overview.png`    | Executive Overview            |
| `06_dashboard_analysis.png`    | Property & Location Analysis  |
| `07_dashboard_diagnostics.png` | Market Diagnostic Analysis    |
| `08_key_insights.png`          | Important analytical findings |

---

# 16. Project Development Process

The project was developed progressively rather than importing the dataset and immediately creating visualizations.

The development process was:

1. Acquire and inspect the dataset.
2. Identify the analytical/business problem.
3. Clean and transform the data using Power Query.
4. Create appropriate dimension tables.
5. Develop the analytical data model.
6. Create a dedicated Date Table.
7. Develop DAX measures.
8. Create interactive dashboard pages.
9. Analyse and interpret the results.
10. Document the project using GitHub.
11. Capture screenshots showing the development process.

Meaningful Git commits should be used to demonstrate progressive development, as recommended by the examination requirements.

---

## 17. Technologies Used

* **Microsoft Power BI Desktop**
* **Power Query**
* **DAX**
* **GitHub**
* **CSV Dataset**

---

## 18. Academic Integrity

This project represents an individual Business Intelligence practical examination. All Power Query transformations, data modelling decisions, DAX calculations and dashboard designs should be understood by the student and be explainable during assessment.

The examination states that students should be prepared to explain the transformations, modelling decisions, DAX measures and dashboard features used in their submission.
