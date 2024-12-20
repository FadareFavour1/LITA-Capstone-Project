# LITA-Capstone-Project(Sales Data)

### Contents
 [Project Title](#Project-Title) 
 
 [Introduction](#Introduction) 
 
 [Project Overview](#Project-Overview)
 
 [Data Cleaning](#Data-Cleaning) 

 [Data Analysis](#Data-Analysis)

 [Data Visualization In Power BI](#Data-Visualization-In-Power-BI)

 [Conclusion](#Conclusion)

### Project Title
**Sales Data** 

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
1. **Total Sales by Product** : A Pivot Table was constructed to summarize total revenue and for each product. The `Product` field was placed in the rows section, while `Revenue` was added to the values area to calculate the sum.

![image](https://github.com/user-attachments/assets/21111202-c216-4b9a-95b5-d47b931771f3)

2. **Sales by Region**: Another Pivot Table was generated to analyze sales performance across different regions. The `Region` field served as the row label, and total revenue was calculated similarly by placing the `Revenue` field in the values area.
   
![image](https://github.com/user-attachments/assets/1fad2c13-0b43-4b28-8b4a-d0667912f14c)

3. **Monthly Sales Trends**: To track sales trends over time, the OrderDate was used to group sales data by month. This allowed us to visualize monthly sales fluctuations effectively
![image](https://github.com/user-attachments/assets/240ef28a-d4a5-47d7-bf77-34f90661bd66)

#### Analysis Performed in SQL
SQL was employed for more complex queries and data manipulations, leveraging its ability to handle large datasets efficiently. Key analyses performed included:

- **Total Sales for each Product Category** : To get the total Sales for each Product, we use;

  ```sql 
  SELECT Product, SUM (Revenue) AS TotalSales
  FROM [dbo].[LITA Capstone SalesData]
  GROUP BY Product                    

- **Number of Sales Transaction in each region**: To get the number of Sales transaction for all the regions we use;

  ```sql
  SELECT Region, Count(OrderID) AS Numberofsalestransaction 
  FROM [LITA Capstone SalesData]
  GROUP BY Region

- **Highest Selling Product by Total Sales Value**: To get the top selling product we use;

  ```sql
  SELECT Product, Sum(Revenue) AS TotalSalesValue
  FROM [dbo].[LITA Capstone SalesData]
  GROUP Product
  ORDER BY TotalSalesValue desc

- **Total Revenue per product**

  ```sql
  SELECT Product, SUM (Revenue) AS TotalSales
  FROM [dbo].[LITA Capstone SalesData]
  GROUP BY Product

- **Monthly Sales totals for the current year**

  ```sql
  SELECT Format(OrderDate,'yyyy-mm')as month,
  SUM(Revenue) AS Monthlysalesdata
  FROM [LITA Capstone SalesData]
  WHERE Year(OrderDate)=Year(GETDATE())
  GROUP BY FORMAT(OrderDate,'yyyy-mm')
  ORDER BY Month

- **Top 5 Customers by Total Purchase Amount**

  ```sql
  SELECT TOP 5(Customer_Id),
  SUM(Revenue) AS TotalPurchaseAmount FROM [dbo].[LITA Capstone SalesData]
  GROUP BY Customer_Id
  ORDER BY TotalPurchaseAmount desc

- **The percentage of total Sales attribute by each region**

  ```sql
  WITH TotalSales AS (
  SELECT sum(Revenue) as 
  TotalRevenue
  FROM [LITA Capstone SalesData]
  )
  SELECT
  Region,
	 SUM(Revenue) AS 
  RegionalRevenue,
  (SUM(Revenue)*100.0/
  (SELECT TotalRevenue FROM
  TotalSales)) AS SalesPercentage
  FROM [LITA Capstone SalesData]
  GROUP BY Region

- Products with no sales in the last quarter

  ```sql
  SELECT distinct Product
  FROM [LITA Capstone SalesData]
  WHERE Product NOT IN (
  SELECT Product
  FROM [LITA Capstone SalesData]
  WHERE OrderDate >=
  DATEADD(Month, -3,GETDATE())
  )

### Data Visualization In Power BI
  To present the sales data insights in an interactive and visually compelling format, Power BI was chosen for data visualization. Power BI’s visualization capabilities allowed for a clear and intuitive presentation of key metrics, trends, and relationships in the data.
  
1. **Revenue by Product** (Bar Chart)

- Visualization Type: Bar Chart

![Screenshot (44)](https://github.com/user-attachments/assets/cefdbd49-f901-47ad-8ce7-0c1101c32e56)
  
- Purpose: The bar chart displayed the total revenue generated by each product, making it easy to compare sales performance.
- Insights: The visualization revealed that Shoes and Shirts were the have the highest Revenue, while Jacket and Socks had lower sales figures. This insight is valuable for product inventory planning and promotional targeting.

2. **Sales by Region** (donut Chart)

- Visualization Type: donut Chart 

![Screenshot (46)](https://github.com/user-attachments/assets/46a6c682-a2e1-44c5-bf0d-1c045182a2b9)

- Purpose: The donut chart was used to show total revenue by region, providing a view of sales distribution.
- Insights: This chart highlighted that the South region has the highest revenue. Visualizing data on a donut made it easy to identify which regions contributed the most to sales, helping to tailor regional marketing efforts.

3. **Monthly Sales Trends** (Line Chart)

- Visualization Type: Line Chart

![Screenshot (47)](https://github.com/user-attachments/assets/a7647ccd-7ac4-4013-9e2f-65f063bf18db)

- Purpose: The line chart plotted monthly revenue, helping to visualize sales trends over time.
- Insights: A clear sales peak was observed in February. Understanding these seasonal trends enables better planning for future sales campaigns.

4. **Interactive Filters and Slicers**

![Screenshot (48)](https://github.com/user-attachments/assets/8c47f86f-7005-4725-b2e5-0439cf84aee6)

- Interactivity: Filters and slicers were added to allow users to explore the data by product, region, and time period.
- Purpose: This interactivity provided flexibility in data exploration, enabling users to drill down into specific products or regions for a more detailed analysis.
- Benefit: By applying filters, users could isolate sales for individual regions, such as comparing North vs. South, which offered deeper insights into regional performance.
  
### Conclusion
Through this analysis of our sales data, we uncovered several valuable insights that can guide strategic decision-making and improve overall business performance:
- **Product Performance**: Shoes and Shirts consistently emerged as the top selling products by Revenue.This insight highlights the importance of prioritizing inventory and marketing efforts for these items.

- **Regional Sales Trends**: Sales were highest in the South region, suggesting that these areas have a larger customer base or stronger demand. This trend can help the company allocate resources and tailor promotional efforts to maximize sales in these regions.

- **Seasonal Patterns**: The data revealed noticeable sales peak in December, which indicates an opportunity for targeted seasonal promotions and inventory stocking.

  These insights provide actionable steps to help the company optimize its operations and marketing strategy. By focusing on high-demand products, prioritizing key regions, and planning for seasonal trends, the company can enhance profitability and better serve its customer base.

#### Limitations
While this analysis provides valuable insights, a few limitations should be noted:

- Data Range: The analysis was limited to two years of sales data, which restricts the ability to identify long-term trends and patterns.

#### Future Work
To further build on this analysis, the following steps are recommended:

- Incorporate Additional Data: Including multi-year data could reveal longer-term trends and patterns, providing a more comprehensive view of sales performance.

Overall, this analysis offers a strong foundation for data-driven decision-making within the company. By leveraging these insights, the company can enhance its strategic planning and remain competitive in a dynamic market.
