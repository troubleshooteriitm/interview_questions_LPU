# Data Analyst Interview Questions & Answers

## 1. What is Data Analysis?

**Answer:**
Data Analysis is the process of collecting, cleaning, transforming, and interpreting data to discover useful information, identify patterns, and support decision-making.

---

## 2. What is Data Analytics?

**Answer:**
Data Analytics is the broader field that includes data collection, cleaning, analysis, visualization, statistical modeling, and predictive techniques to solve business problems.

---

## 3. Difference between Data Analysis and Data Analytics

| Data Analysis | Data Analytics |
|---------------|----------------|
| Focuses on analyzing historical data | Includes analysis, prediction, and optimization |
| Answers "What happened?" | Answers "Why?", "What will happen?", and "What should we do?" |
| Narrow scope | Broad scope |

---

## 4. What is ETL?

**Answer:**

ETL stands for:

- **Extract:** Collect data from different sources.
- **Transform:** Clean, validate, and convert the data.
- **Load:** Store the processed data into a database or data warehouse.

---

## 5. What is ELT?

**Answer:**

ELT stands for:

- **Extract**
- **Load**
- **Transform**

Unlike ETL, data is loaded first and transformed later inside the data warehouse.

---

## 6. What is a Data Warehouse?

**Answer:**

A Data Warehouse is a centralized repository that stores integrated historical data from multiple sources for reporting and business intelligence.

Characteristics:
- Subject-oriented
- Integrated
- Time-variant
- Non-volatile

---

## 7. Difference between Database and Data Warehouse

| Database | Data Warehouse |
|----------|----------------|
| Stores current operational data | Stores historical data |
| Used for transactions | Used for analytics |
| Frequent INSERT/UPDATE | Mostly SELECT queries |

---

## 8. What is OLTP?

**Answer:**

OLTP (Online Transaction Processing) manages day-to-day transactions like banking, shopping, and booking systems.

Characteristics:
- Fast transactions
- Highly normalized
- Many INSERT, UPDATE, DELETE operations

---

## 9. What is OLAP?

**Answer:**

OLAP (Online Analytical Processing) is designed for complex analytical queries and reporting.

Characteristics:
- Historical data
- Complex aggregations
- Optimized for analysis

---

## 10. Difference between OLTP and OLAP

| OLTP | OLAP |
|------|------|
| Operational system | Analytical system |
| Current data | Historical data |
| Fast transactions | Complex queries |
| Highly normalized | Usually denormalized |

---

## 11. What is Normalization?

**Answer:**

Normalization is the process of organizing data to reduce redundancy and improve data integrity.

Types:
- 1NF
- 2NF
- 3NF
- BCNF

---

## 12. What is Denormalization?

**Answer:**

Denormalization combines tables to reduce joins and improve query performance. It increases redundancy but speeds up reporting.

---

## 13. What is a Primary Key?

**Answer:**

A Primary Key uniquely identifies each row in a table.

Properties:
- Unique
- Cannot contain NULL values
- Only one primary key per table

---

## 14. What is a Foreign Key?

**Answer:**

A Foreign Key is a column that references the Primary Key of another table and maintains referential integrity.

---

## 15. Difference between Primary Key and Unique Key

| Primary Key | Unique Key |
|-------------|------------|
| Cannot be NULL | May allow NULL (DBMS dependent) |
| One per table | Multiple allowed |
| Uniquely identifies rows | Ensures uniqueness |

---

## 16. What is an Index?

**Answer:**

An Index is a database object that improves the speed of data retrieval operations.

Advantages:
- Faster SELECT queries

Disadvantages:
- Uses extra storage
- Slows INSERT, UPDATE, DELETE

---

## 17. Clustered vs Non-Clustered Index

| Clustered Index | Non-Clustered Index |
|-----------------|---------------------|
| Stores actual data | Stores pointers to data |
| One per table | Multiple allowed |
| Faster for range queries | Faster for specific lookups |

---

## 18. What are ACID Properties?

**Answer:**

- **Atomicity:** All operations succeed or none do.
- **Consistency:** Data remains valid.
- **Isolation:** Transactions don't interfere.
- **Durability:** Committed data is permanently stored.

---

## 19. What is a Fact Table?

**Answer:**

A Fact Table stores measurable business data.

Example:
- Sales Amount
- Quantity Sold
- Profit

---

## 20. What is a Dimension Table?

**Answer:**

Dimension Tables store descriptive information.

Examples:
- Customer
- Product
- Date
- Region

---

## 21. Difference between Star Schema and Snowflake Schema

| Star Schema | Snowflake Schema |
|--------------|------------------|
| Denormalized | Normalized |
| Fewer joins | More joins |
| Faster queries | Less redundancy |

---

## 22. What is Cardinality?

**Answer:**

Cardinality refers to the uniqueness of values in a column.

Examples:
- Employee ID → High cardinality
- Gender → Low cardinality

---

## 23. What is Granularity?

**Answer:**

Granularity is the level of detail stored in a dataset.

Example:
- Transaction-level data → Fine granularity
- Monthly summary → Coarse granularity

---

## 24. What is Data Cleaning?

**Answer:**

Data Cleaning improves data quality by:
- Removing duplicates
- Handling missing values
- Standardizing formats
- Correcting invalid values
- Removing inconsistencies

---

## 25. What is Data Validation?

**Answer:**

Data Validation ensures that data is accurate, complete, consistent, and follows predefined rules before analysis.

---

## 26. What is Exploratory Data Analysis (EDA)?

**Answer:**

EDA is the process of exploring data using statistics and visualizations to understand distributions, identify outliers, detect relationships, and uncover patterns before modeling.

---

## 27. What is Mean?

**Answer:**

Mean is the arithmetic average.

Formula:
Mean = Sum of values / Number of values

---

## 28. What is Median?

**Answer:**

Median is the middle value after arranging the data in ascending or descending order.

Median is preferred when data contains outliers.

---

## 29. What is Mode?

**Answer:**

Mode is the value that appears most frequently in a dataset.

---

## 30. Difference between Mean, Median, and Mode

| Mean | Median | Mode |
|------|--------|------|
| Arithmetic average | Middle value | Most frequent value |

---

## 31. What is Variance?

**Answer:**

Variance measures how far data points are spread from the mean.

Higher variance means greater variability.

---

## 32. What is Standard Deviation?

**Answer:**

Standard deviation is the square root of variance and measures the spread of data around the mean.

Lower standard deviation means data is more consistent.

---

## 33. What is Correlation?

**Answer:**

Correlation measures the strength and direction of the relationship between two variables.

Range:
- +1 → Perfect positive
- 0 → No relationship
- -1 → Perfect negative

---

## 34. Difference between Correlation and Covariance

| Correlation | Covariance |
|-------------|------------|
| Standardized (-1 to 1) | Not standardized |
| Measures strength and direction | Measures direction only |

---

## 35. What is an Outlier?

**Answer:**

An Outlier is an observation significantly different from the rest of the data.

Detection methods:
- IQR
- Z-score
- Box Plot

---

## 36. What are Missing Values?

**Answer:**

Missing values represent unavailable or unknown data.

Common methods to handle them:
- Remove rows
- Fill with mean/median/mode
- Predict using machine learning

---

## 37. What is Sampling?

**Answer:**

Sampling is selecting a subset of data from a larger population for analysis.

Types:
- Random Sampling
- Stratified Sampling
- Systematic Sampling

---

## 38. What is Population?

**Answer:**

Population refers to the complete set of observations under study.

Example:
All customers of Amazon.

---

## 39. What is a Sample?

**Answer:**

A Sample is a subset of the population selected for analysis.

Example:
10,000 randomly selected Amazon customers.

---

## 40. What is the Data Analysis Process?

**Answer:**

1. Define the problem.
2. Collect data.
3. Clean data.
4. Perform Exploratory Data Analysis (EDA).
5. Analyze data.
6. Visualize results.
7. Interpret findings.
8. Communicate recommendations.

---

## 41. What is Business Intelligence (BI)?

**Answer:**

Business Intelligence is the process of collecting, analyzing, and visualizing data to support business decision-making using tools like Power BI, Tableau, and Excel.

---

## 42. What are KPIs?

**Answer:**

KPIs (Key Performance Indicators) are measurable metrics used to evaluate business performance.

Examples:
- Revenue
- Profit Margin
- Customer Retention
- Churn Rate
- Conversion Rate

---

## 43. What is a Dashboard?

**Answer:**

A Dashboard is a visual interface that displays key metrics, charts, and reports to monitor business performance in real time.

---

## 44. What is Data Visualization?

**Answer:**

Data Visualization is the graphical representation of data using charts, graphs, maps, and dashboards to make information easier to understand.

---

## 45. What is Data Integrity?

**Answer:**

Data Integrity refers to the accuracy, consistency, and reliability of data throughout its lifecycle.

---

## 46. What is Data Governance?

**Answer:**

Data Governance is the framework of policies, standards, and procedures that ensure data quality, security, privacy, and compliance across an organization.

---

## 47. What is Metadata?

**Answer:**

Metadata is "data about data." It describes the structure, source, format, and characteristics of a dataset.

Example:
- Column names
- Data types
- Creation date
- File size

---

## 48. What is Big Data?

**Answer:**

Big Data refers to extremely large and complex datasets that cannot be efficiently processed using traditional database systems.

The 5 Vs:
- Volume
- Velocity
- Variety
- Veracity
- Value

---

## 49. What is Data Mining?

**Answer:**

Data Mining is the process of discovering hidden patterns, trends, and relationships in large datasets using statistical and machine learning techniques.

---

## 50. What skills are essential for a Data Analyst?

**Answer:**

A strong Data Analyst should have knowledge of:
- SQL
- Excel
- Python (Pandas, NumPy)
- Power BI/Tableau
- Statistics
- Data Cleaning
- Data Visualization
- Business Understanding
- Communication Skills

---

## 51. What is Data Modeling?

**Answer:**

Data Modeling is the process of designing how data is stored, organized, and related in a database. It helps ensure data consistency, efficiency, and scalability.

---

## 52. What are the different types of Data Models?

**Answer:**

- Conceptual Data Model
- Logical Data Model
- Physical Data Model

---

## 53. What is Referential Integrity?

**Answer:**

Referential Integrity ensures that relationships between tables remain consistent by preventing invalid foreign key values.

---

## 54. What is Data Redundancy?

**Answer:**

Data Redundancy is the unnecessary duplication of data in a database, leading to increased storage usage and possible inconsistencies.

---

## 55. What is Data Consistency?

**Answer:**

Data Consistency means the data remains accurate and uniform across all tables, databases, and transactions.

---

## 56. What is Structured Data?

**Answer:**

Structured Data is organized into rows and columns with a predefined schema.

Examples:
- SQL databases
- Excel tables

---

## 57. What is Semi-Structured Data?

**Answer:**

Semi-structured data does not follow a fixed table structure but contains tags or keys.

Examples:
- JSON
- XML

---

## 58. What is Unstructured Data?

**Answer:**

Unstructured Data has no predefined format.

Examples:
- Images
- Videos
- Emails
- PDFs
- Audio files

---

## 59. What is Data Profiling?

**Answer:**

Data Profiling is the process of examining data to understand its quality, completeness, uniqueness, and consistency.

---

## 60. What is Data Wrangling?

**Answer:**

Data Wrangling is the process of cleaning, transforming, and preparing raw data for analysis.

---

## 61. What is Data Transformation?

**Answer:**

Data Transformation converts data from one format or structure into another for analysis.

Examples:
- Currency conversion
- Date formatting
- Unit conversion

---

## 62. What is Data Aggregation?

**Answer:**

Data Aggregation combines multiple records into summary values.

Examples:
- Monthly sales
- Average salary
- Total revenue

---

## 63. What is Data Filtering?

**Answer:**

Data Filtering removes unnecessary records based on specified conditions.

Example:
Show employees with salary greater than ₹50,000.

---

## 64. What is Data Sorting?

**Answer:**

Sorting arranges data in ascending or descending order.

---

## 65. What is Data Partitioning?

**Answer:**

Partitioning divides large tables into smaller pieces to improve query performance and maintenance.

---

## 66. What is Data Compression?

**Answer:**

Data Compression reduces storage space while preserving data.

Benefits:
- Faster queries
- Reduced storage costs

---

## 67. What is a Surrogate Key?

**Answer:**

A Surrogate Key is a system-generated unique identifier with no business meaning.

Example:
Customer_ID = 10001

---

## 68. What is a Natural Key?

**Answer:**

A Natural Key is a real-world attribute that uniquely identifies a record.

Example:
Passport Number
Aadhaar Number

---

## 69. What is a Composite Key?

**Answer:**

A Composite Key consists of two or more columns used together to uniquely identify a row.

---

## 70. What is Data Integrity Constraint?

**Answer:**

Integrity constraints enforce data accuracy.

Types:
- Primary Key
- Foreign Key
- Unique
- Check
- Not Null

---

## 71. What is NULL?

**Answer:**

NULL represents missing, unknown, or unavailable data.

NULL is not equal to zero, an empty string, or FALSE.

---

## 72. Difference between NULL and 0

| NULL | 0 |
|------|---|
| Unknown value | Numeric value |
| Represents missing data | Represents zero |

---

## 73. Difference between CHAR and VARCHAR

| CHAR | VARCHAR |
|------|----------|
| Fixed length | Variable length |
| Faster | Saves storage |
| Pads extra spaces | No extra padding |

---

## 74. What is a Constraint?

**Answer:**

A Constraint is a rule applied to a table to maintain data integrity.

Examples:
- NOT NULL
- UNIQUE
- PRIMARY KEY
- CHECK
- FOREIGN KEY

---

## 75. What is a View?

**Answer:**

A View is a virtual table created from one or more SQL queries.

Advantages:
- Security
- Simpler queries
- Reusable logic

---

## 76. What is a Materialized View?

**Answer:**

A Materialized View stores query results physically, improving performance for complex queries.

---

## 77. What is a Stored Procedure?

**Answer:**

A Stored Procedure is a precompiled collection of SQL statements stored in the database.

Benefits:
- Faster execution
- Code reuse
- Security

---

## 78. What is a Trigger?

**Answer:**

A Trigger is a database object that automatically executes when an INSERT, UPDATE, or DELETE event occurs.

---

## 79. What is a Cursor?

**Answer:**

A Cursor processes SQL query results row by row.

It should be avoided when set-based operations are possible because it is slower.

---

## 80. What is Query Optimization?

**Answer:**

Query Optimization improves SQL query performance by minimizing execution time and resource usage.

Techniques:
- Indexing
- Avoid SELECT *
- Optimize joins
- Use execution plans

---

## 81. What is an Execution Plan?

**Answer:**

An Execution Plan shows how the database engine executes a SQL query.

It helps identify bottlenecks and optimize performance.

---

## 82. What is Data Skew?

**Answer:**

Data Skew occurs when data is unevenly distributed across partitions or categories, causing performance issues.

---

## 83. What is Sampling Bias?

**Answer:**

Sampling Bias occurs when the selected sample does not accurately represent the population.

---

## 84. What is Selection Bias?

**Answer:**

Selection Bias occurs when some members of the population have a higher chance of being selected than others.

---

## 85. What is Confidence Interval?

**Answer:**

A Confidence Interval is a range of values likely to contain the true population parameter with a given confidence level.

Example:
95% Confidence Interval

---

## 86. What is Hypothesis Testing?

**Answer:**

Hypothesis Testing is a statistical method used to determine whether there is enough evidence to support a claim about a population.

---

## 87. What is the Null Hypothesis?

**Answer:**

The Null Hypothesis (H₀) states that there is no significant difference or relationship between variables.

---

## 88. What is the Alternative Hypothesis?

**Answer:**

The Alternative Hypothesis (H₁) states that a significant difference or relationship exists.

---

## 89. What is a P-value?

**Answer:**

A P-value measures the probability of observing the data if the null hypothesis is true.

A small P-value (typically < 0.05) suggests rejecting the null hypothesis.

---

## 90. What is Statistical Significance?

**Answer:**

Statistical Significance indicates that the observed results are unlikely to have occurred by random chance.

---

## 91. What is Regression?

**Answer:**

Regression is a statistical technique used to model relationships between dependent and independent variables.

---

## 92. What is Linear Regression?

**Answer:**

Linear Regression predicts a continuous dependent variable using a straight-line relationship with one or more independent variables.

---

## 93. What is Classification?

**Answer:**

Classification is a machine learning technique used to predict categorical outcomes.

Examples:
- Spam or Not Spam
- Fraud or Not Fraud

---

## 94. What is Clustering?

**Answer:**

Clustering groups similar data points together without predefined labels.

Example:
Customer Segmentation

---

## 95. What is Feature Engineering?

**Answer:**

Feature Engineering is the process of creating new variables from existing data to improve model performance.

---

## 96. What is Overfitting?

**Answer:**

Overfitting occurs when a model learns the training data too well, including noise, resulting in poor performance on new data.

---

## 97. What is Underfitting?

**Answer:**

Underfitting occurs when a model is too simple to capture the underlying patterns in the data.

---

## 98. What is Cross Validation?

**Answer:**

Cross Validation evaluates model performance by dividing data into multiple training and testing subsets.

The most common method is K-Fold Cross Validation.

---

## 99. What is Data Security?

**Answer:**

Data Security involves protecting data from unauthorized access, corruption, theft, or loss through encryption, authentication, and access controls.

---

## 100. What are the responsibilities of a Data Analyst?

**Answer:**

A Data Analyst is responsible for:
- Collecting data
- Cleaning and validating data
- Performing exploratory data analysis (EDA)
- Writing SQL queries
- Building dashboards
- Creating reports
- Identifying trends and patterns
- Communicating insights to stakeholders
- Supporting business decisions with data