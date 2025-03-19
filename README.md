# VisionStack - Illuminating Growth with Big Data

## Project Description

VisionStack is a big data analytics project focused on cleaning, processing, and analyzing customer and product datasets using PySpark. [cite: 1, 2, 3] The project aims to derive key performance indicators (KPIs) to provide actionable insights for businesses, enabling data-driven decision-making and growth. [cite: 1, 2, 3, 4]

## Key Features

* **Data Cleaning and Processing:** Utilizes PySpark to ensure data quality and consistency in large datasets. [cite: 13, 14, 15]
* **KPI Development:** Focuses on developing key performance indicators, including:
    * Yearly Sales [cite: 26, 27]
    * Quarterly Sales [cite: 28, 29]
    * Total number of orders by each category [cite: 30, 31]
    * Frequency of customer visited [cite: 32, 33]
    * Total amount spent by each customer [cite: 34, 35]
    * Amount spent by each food category [cite: 36, 37, 38]
    * Total amount sales in each month [cite: 39, 40]
    * Total sales by order source [cite: 41, 42]
* **Data Integration:** Combines multiple datasets into a unified format for comprehensive analysis. [cite: 21, 22]
* **Data Visualization:** Presents analytical results through intuitive visualizations. [cite: 24, 25]

## Architecture

The project follows a data processing pipeline:

1.  **Data Collection:** Gathers raw data from various sources, including sales records, order databases, mobile applications, and in-store point-of-sale systems. [cite: 9, 10] Data may include customer details, product categories, timestamps, sales amounts, and order sources. [cite: 10, 11, 12]
2.  **Data Cleaning:** Prepares raw data for analysis by addressing quality issues and structuring it into a usable format. [cite: 13, 14, 15]
3.  **Data Integration:** Combines multiple datasets into a unified, structured format. [cite: 21, 22]
4.  **Data Analysis:** Performs computations to derive actionable insights. [cite: 23, 24, 25]
5.  **Data Visualization:** Presents results through visualizations. [cite: 24, 25]
6.  **Outcome:** Deploys the analytical process for continuous data updates and system performance monitoring. [cite: 24, 25]

**\[See Figure 1 in the document for a flowchart of the architecture]**

## Implementation

The implementation involves the following key steps:

1.  **Workspace Setup (Databricks):**
    * Creates a cluster named "TripleByte Vision" with sufficient resources. [cite: 43, 44, 45]
    * Sets up a notebook named "VisionStack" for PySpark code. [cite: 46, 47]
2.  **Dataset Loading:**
    * Uses two datasets: Sales Data (product\_id, customer\_id, order\_date, location, source\_order) and Menu Data (product\_id, product\_name, price). [cite: 47, 48, 49]
    * Uploads the datasets (sales\_csv.txt and menu\_csv.txt) to the /FileStore/tables/ folder in Databricks. [cite: 47, 48, 49, 50]
3.  **Library Import:**
    * Imports necessary PySpark libraries. [cite: 50, 51]
4.  **Data Structure Definition:**
    * Defines schemas for Sales Data and Menu Data, specifying column names and data types. [cite: 51, 52, 53, 54]
5.  **Data Loading:**
    * Loads the datasets into DataFrames using the defined schemas. [cite: 54, 55]
6.  **Data Cleaning and Enhancement:**
    * Formats the order\_date column. [cite: 56, 57, 58, 59]
    * Extracts year, month, and quarter from the order date. [cite: 56, 57, 58, 59]
7.  **Data Combination:**
    * Joins the sales data with the menu data. [cite: 59, 60]
8.  **KPI Calculation:**
    * Calculates KPIs, including total amount spent by each customer, total sales by customer, yearly sales, order counts by category, sales by order source, customer visit frequency, quarterly sales, and monthly sales. [cite: 60, 61, 62, 63, 64, 65]
9.  **Result Export and Visualization:**
    * Exports KPIs to CSV files. [cite: 65, 66, 67]
    * Visualizes KPIs using Databricks. [cite: 65, 66, 67]

## Code Implementation for Each Goal

The project provides code snippets and results for each KPI calculation:

1.  **Total Amount Spent by Each Customer:**
    * Calculates total spending per customer. [cite: 67, 68, 69, 70, 71]
    * **Code Snippet:**
        ```python
        total_amount_spent = (sales_df.join(menu_df,'product_id').groupBy('customer_id').agg('price':'sum').orderBy('customer_id'))
        display(total_amount_spent)
        ```
    * **Metrics:** Data Quality, Volume, Velocity, Value, Veracity, Processing Time. [cite: 72, 73, 74, 75, 76]
2.  **Total Amount Spent by Each Food Category:**
    * Analyzes sales distribution across food categories. [cite: 76, 77, 78, 79, 80]
    * **Code Snippet:**
        ```python
        total_amount_spent = (sales_df.join(menu_df,'product_id').groupBy('product_name').agg('price': 'sum').orderBy('product_name'))
        display(total_amount_spent)
        ```
    * **Metrics:** Data Quality, Variety, Value, Veracity, Processing Time. [cite: 81, 82, 83, 84, 85]
3.  **Total Sales by Month:**
    * Derives monthly sales trends. [cite: 85, 86, 87, 88, 89]
    * **Code Snippet:**
        ```python
        df_month = (sale_df.join(menu_df,product_id').groupBy('order_month').agg('price':'sum').orderBy('order_month'))
        display(df_month)
        ```
    * **Metrics:** Volume, Velocity, Veracity, Value, Processing Time. [cite: 89, 90, 91]
4.  **Yearly Sales:**
    * Provides yearly sales trends. [cite: 91, 92, 93, 94, 95, 96]
    * **Code Snippet:**
        ```python
        df_year = (sales_df.join(menu_df,'product_id').groupBy('order_year').agg('price':'sum').orderBy('order_year')) dis-
        play(df_year)
        ```
    * **Metrics:** Velocity, Veracity, Value, Processing Time. [cite: 94, 95, 96]
5.  **Total Number of Orders by Each Category:**
    * Tracks the number of orders per product category. [cite: 96, 97, 98, 99, 100, 101, 102]
    * **Code Snippet:**
        ```python
        from pyspark.sql.functions import count
        most_df = (sales_df.join(menu_df, product_id').groupBy('product_id','product_name').agg(count('product_id').alias('product_count')).order
        display(most_df)
        ```
    * **Metrics:** Volume, Veracity, Value, Processing Time. [cite: 101, 102]
6.  **Total Sales by Order Source:**
    * Identifies the performance of different order sources. [cite: 102, 103, 104, 105, 106]
    * **Code Snippet:**
        ```python
        total_sales = (sales_df.join(menu_df,'product_id').groupBy('source_order').agg('price':'sum'))
        display(total_sales)
        ```
    * **Metrics:** Variety, Veracity, Value, Processing Time. [cite: 105, 106]
7.  **Quarterly Sales:**
    * Provides quarterly sales trends. [cite: 106, 107, 108, 109, 110, 111, 112]
    * **Code Snippet:**
        ```python
        df_quarter = (sales_df.join(menu_df,product_id').groupBy('order_quarter').agg('price':'sum').orderBy('order_quarter'))
        display(df_quarter)
        ```
    * **Metrics:** Velocity, Veracity, Value, Processing Time. [cite: 111, 112]
8.  **Frequency of Customer Visits:**
    * Determines how often customers visit. [cite: 112, 113, 114, 115, 116, 117]
    * **Code Snippet:**
        ```python
        from pyspark.sql.functions import countDistinct
        df = sales_df.filter(sales_df.source_order=='Restaurant').groupBy('customer_id').agg(countDistinct('order_date'))
        display(df)
        ```
    * **Metrics:** Velocity, Veracity, Value, Processing Time. [cite: 114, 115, 116, 117]

## Conclusion

VisionStack demonstrates the power of big data analytics in transforming raw datasets into actionable insights. [cite: 117, 118, 119, 120, 121, 122, 123, 124, 125] The project efficiently processes large volumes of data using PySpark, enabling the creation of meaningful KPIs. [cite: 117, 118, 119, 120, 121, 122, 123, 124, 125] Key results include identifying top customers, high-demand product categories, and seasonal sales trends. [cite: 119, 120, 121, 122, 123, 124, 125] The project maintains high data quality, scalability, and speed, making it suitable for real-time analysis scenarios. [cite: 119, 120, 121, 122, 123, 124, 125]

## GitHub Link

[https://github.com/kartikeya-datta/VisionStack](https://github.com/kartikeya-datta/VisionStack) [cite: 126]

## Citation and References

1.  Apache Software Foundation. (n.d.). PySpark Documentation. [https://spark.apache.org/docs/latest/api/python/](https://spark.apache.org/docs/latest/api/python/) [cite: 126]
2.  Databricks. (n.d.). Databricks Documentation: Data Engineering with Apache Spark. [https://docs.databricks.com/](https://docs.databricks.com/) [cite: 127]
3.  Databricks. (n.d.). Creating Schemas Using StructType. [https://spark.apache.org/docs/latest/sql-programming-guide.html#datasets-and-dataframes](https://spark.apache.org/docs/latest/sql-programming-guide.html#datasets-and-dataframes) [cite: 127]
4.  Laney, D. (2001). 3D Data Management: Controlling Data Volume, Velocity, and Variety. META Group Research Note. [https://www.gartner.com/](https://www.gartner.com/) [cite: 128]
5.  AWS. (n.d.). Best Practices for Big Data Analytics. [https://aws.amazon.com/big-data/](https://aws.amazon.com/big-data/) [cite: 128]
6.  Methodology based on SQL-style group-by aggregation techniques. Reference PySpark SQL functions: Apache Spark. (n.d.). Aggregate Functions. [https://spark.apache.org/docs/latest/sql-ref-functions-builtin.html](https://spark.apache.org/docs/latest/sql-ref-functions-builtin.html) [cite: 129]
7.  PySpark's withColumn and date\_format functions were used for time-based transformations. Reference: Apache Spark. (n.d.). Date Functions. [https://spark.apache.org/docs/latest/sql-ref-functions-builtin.html#date-functions](https://spark.apache.org/docs/latest/sql-ref-functions-builtin.html#date-functions) [cite: 129, 130]
8.  Pipino, L., Lee, Y., & Wang, R. (2002). Data Quality Assessment. *Communications of the ACM*, *45*(4), 211-218. [cite: 130, 131]
9.  McKinsey Global Institute. (2011). Big Data: The Next Frontier for Innovation, Competition, and Productivity. [cite: 131]
10. Zikopoulos, P., & Eaton, C. (2011). *Understanding Big Data: Analytics for Enterprise Class Hadoop and Streaming Data*. McGraw-Hill. [cite: 131, 132]
11. Davenport, T. H., & Harris, J. G. (2007). *Competing on Analytics: The New Science of Winning*. Harvard Business Review Press. [cite: 132, 133]
12. Chen, M., Mao, S., & Liu, Y. (2014). Big Data: A Survey. *Mobile Networks and Applications*, *19*(2), 171-209. [cite: 133, 134]
