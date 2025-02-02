# Bank-churn-analysis-using-powerbi
## Project Objective
This project is about analyzing customer churn in a bank to understand why customers leave. The goal is to identify trends and insights that can help in retention strategies.

### Step 1: Load the Data
* Imported the dataset into Power BI.
* Verified the structure and identified necessary transformations.

### Step 2: Data Transformation
* Check data types and column names.
* Ensure column names begin with a capital letter.
* Converted binary values to meaningful text values:
  * Churn Status:  1 → Churned, 0 → Not Churned
  * Active Status:  1 → Active, 0 → Inactive
  * Credit Card:  1 → Owned, 0 → Not Owned
* Transforming Product Column- Used "Column from Examples" feature to rewrite product numbers and Renamed this column as Products.
   * 1 → Product 1
   * 2 → Product 2
   * 3 → Product 3
   * 4 → Product 4
* Create conditional columns for grouping based on existing data:
    * Age Group (derived from Age)
    * Credit Scores (derived from Credit Score)
    * Account Balance (derived from Balance)

### Step 3: Data Modeling 
Construct reference tables and develop conditional columns:

* Create a reference table from the bank customer churn prediction table, rename it to 'Age Group Table', retain only the 'Age_Group' column, and removed duplicates.
* Introduce an 'Age Id' conditional column in the 'Age Group Table'.
* Similarly, create reference tables for 'Account Balance' and 'Credit_Scores'. Insert respective Id's as conditional columns and sorted Id's in ascending order.
* Applied close & apply to save transformations.
* Established relationships among tables using Power BI’s Model View.

### Step 4: Creating Measures using DAX
Developed the following DAX measures for analysis:

* To calculate the number of customers(Total Customers) -
  * Customers = COUNT('Bank Customer Churn Prediction'[Customer_Id])
    
* To calculate the number of lost customers(Churned) -
  * Customers Lost = CALCULATE('Bank Customer Churn Prediction'[Customers],'Bank Customer Churn Prediction'[Churn Status]="Churned")
    
* To calculate the churn rate -
  * Churn Rates = 'Bank Customer Churn Prediction'[Customers Lost]/'Bank Customer Churn Prediction'[Customers]

### Step 5: Data Visualization (Dashboard Design)
KPIs (Cards)

* Total Customers
* Lost Customers
* Churn Rate

Charts
* Donut Charts for:
  * Customers by Gender
  * Customers by Active Status
  * Customers by Credit Card 
  * Customers by Country
  * Customers by Products
    
* Stacked Column & Line Charts for:
  * Customers & Churn Rate by Age Group
  * Customers & Churn Rate by Account Balance


