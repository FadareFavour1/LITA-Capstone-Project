# LITA-Capstone-Project(Sales Data)

### Contents
 [Project Title](#Project-Title) 
 
 [Introduction](#Introduction) 
 
 [Project Overview](#Project-Overview)
 
 [Data Cleaning](#Data-Cleaning) 

 [Data Analysis](#Data-Analysis)

### Project Title
Sales Data 

### Introduction
#### Project Purpose
The objective of this project is to analyze a dataset of sales transactions to uncover insights that can drive business decisions. Sales data analysis helps businesses understand customer preferences, regional performance, monthly sales trends and product success, allowing them to optimize strategies for higher revenue and customer satisfaction.

#### Scope of the Project
This analysis focuses on identifying patterns and trends in sales performance, revenue generation, and customer behavior. By examining factors such as product demand across regions and time periods, the project aims to provide insights into factors driving sales and potential growth opportunities.

#### Tools Used
The project utilizes three primary tools:

- Excel: Used for preliminary data exploration and basic calculations, as well as for creating charts and pivot tables for initial insights.
- SQL Server Studio: Applied for data cleaning and preparation tasks, including data extraction, transformation, and loading (ETL) processes. SQL’s powerful querying capabilities allow for efficient handling of complex data structures and cleaning steps.
- Power BI: Chosen for its data visualization capabilities, Power BI enables the creation of interactive dashboards and reports, facilitating a deeper understanding of sales trends and metrics through visual representation.
This project’s findings will be documented to highlight key sales insights, supporting decision-making for various business units.

### Project Overview
This project focuses on analyzing sales data to gain insights into revenue trends, and regional performance. 

 #### Dataset Summary
The dataset includes information on historical sales transactions, providing fields such as OrderId, CustomerId, Product, Region, Order Date, Quantity, Unit Price, and Revenue. The data covers multiple regions and product categories, allowing for a detailed examination of sales patterns across different dimensions.

#### Project Objectives
##### The primary goals of this analysis are to:

* Identify high-performing products and regions to understand what drives revenue.
* Analyze seasonal and time-based trends to predict periods of high and low demand.
* Assess customer purchasing behavior to support marketing and sales strategies.
* Provide insights into potential areas for growth or improvement in sales performance.
* Key Questions to Explore
  
##### The analysis seeks to answer the following questions:

- Which products and regions generate the highest revenue, and why?
- Are there specific time periods where sales peak or drop significantly?
- What customer demographics contribute most to revenue, and how can we optimize marketing to better engage these customers?
- Are there any patterns in product performance that can guide inventory or pricing decisions?

### Data Cleaning
In this section, we detail the steps taken to prepare the sales data for analysis. These steps help to ensure the dataset is complete, consistent, and reliable for meaningful insights.

1. Handling Missing Values 
- Upon inspecting the data, missing values were found in the Revenue 
- To address this, missing Revenue values were calculated by multiplying Quantity by Unit Price using the formula
  
  ` =PRODUCT(F2:G2) `

### Data Analysis
In this section, we discuss the analysis performed using Excel and SQL, focusing on how each tool contributed to deriving insights from the sales data.

#### Analysis Performed in Excel

Excel was utilized for its robust data visualization and analytical capabilities. The following analyses were conducted:

##### Descriptive Statistics: 
 Using Excel functions such as SUM, AVERAGEIF, and SUMIF, we calculated key metrics including total Sales,Average sales by product  and total revenue by region.

For example,
- The total Sales was calculated using the formula:

 ` =SUM(H2:H50001) `

- The average sales for each product was calculated using the formula:
 
` =AVERAGEIF(C2:C50001,C2,H2:H50001) `

- The Total revenue for each region was calculated using the formula:
 
` =SUMIF(D2:D50001,D2,H2:H50001) `

##### Pivot Tables: 
To facilitate a deeper understanding of the sales data, Pivot Tables were employed in Excel. A Pivot Table is a powerful tool that allows users to summarize and analyze large datasets interactively, enabling quick insights into data patterns and trends.

Several Pivot Tables were created to explore different dimensions of the sales data :
1. Total Sales by Product : A Pivot Table was constructed to summarize total revenue and for each product. The `Product` field was placed in the rows section, while `Revenue` was added to the values area to calculate the sum.












