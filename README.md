 Customer Shopping Behavior Analysis

 Overview

This project analyzes customer shopping behavior to identify purchasing patterns, customer segments, product performance, revenue trends, and subscription behavior.

The project follows an end-to-end data analytics workflow:

**Data Loading → Exploratory Data Analysis → Data Cleaning → Feature Engineering → SQL Analysis → Power BI Dashboard → Report & Presentation**

The objective is to transform raw customer shopping data into meaningful business insights that can support data-driven decision-making.

---

 Dataset

The dataset contains **3,900 customer purchase records** and **18 original columns**.

Key attributes include:

- Customer ID
- Age
- Gender
- Item Purchased
- Category
- Purchase Amount (USD)
- Location
- Size
- Color
- Season
- Review Rating
- Subscription Status
- Shipping Type
- Discount Applied
- Promo Code Used
- Previous Purchases
- Payment Method
- Frequency of Purchases

During the analysis, additional fields were created, including:

- `age_group`
- `purchase_frequency_days`

The `Review Rating` missing values were handled using the median rating within each product category.

---

 Tools & Technologies

 Python
- Python
- Pandas
- Jupyter Notebook / Google Colab

Used for:
- Loading the dataset
- Data exploration
- Data cleaning
- Missing-value treatment
- Column standardization
- Feature engineering

 SQL

SQL was used for business analysis and querying the cleaned customer dataset.

The project includes queries for:

- Revenue by gender
- Discounted purchases above average spending
- Top-rated products
- Shipping-type spending comparison
- Subscriber vs. non-subscriber analysis
- Products with the highest discount rates
- Customer segmentation
- Top products within categories
- Repeat buyers and subscription behavior
- Revenue by age group

The SQL analysis uses techniques such as:

- `GROUP BY`
- `ORDER BY`
- Aggregate functions
- `CASE`
- Subqueries
- Common Table Expressions (CTEs)
- Window functions

 Databases

The project includes database connection workflows for:

- PostgreSQL
- MySQL
- Microsoft SQL Server

 Power BI

Power BI was used to create an interactive dashboard for presenting customer and sales insights.

 Gamma

Gamma was used to create a presentation summarizing the project, methodology, findings, and business insights.

---

 Project Steps

 1. Load the Dataset

The dataset was loaded into Python using Pandas.

```python
import pandas as pd

df = pd.read_csv("customer_shopping_behavior.csv")
```

Initial inspection was performed using:

```python
df.head()
df.info()
df.describe(include="all")
```

---

 2. Exploratory Data Analysis

The dataset was explored to understand:

- Dataset structure
- Data types
- Numerical statistics
- Categorical variables
- Missing values
- Customer purchasing behavior

Missing values were checked using:

```python
df.isnull().sum()
```

---

 3. Data Cleaning

The following cleaning activities were performed:

- Handled missing `Review Rating` values.
- Standardized column names using snake_case.
- Renamed `purchase_amount_(usd)` to `purchase_amount`.
- Removed the `promo_code_used` column after checking its relationship with `discount_applied`.

Example:

```python
df.columns = df.columns.str.lower()
df.columns = df.columns.str.replace(" ", "_")
```

---
 4. Feature Engineering

New analytical features were created to support deeper analysis.

 Age Group

Customers were divided into four age groups:

- Young Adult
- Adult
- Middle-aged
- Senior

 Purchase Frequency

Purchase frequency categories were converted into the number of days between purchases.

For example:

- Weekly → 7 days
- Fortnightly → 14 days
- Monthly → 30 days
- Quarterly → 90 days
- Annually → 365 days

These derived fields helped make the data easier to analyze using SQL and Power BI.

---

SQL Analysis

After cleaning and transforming the dataset, the data was loaded into a database table named:

```text
customer
```

SQL queries were then used to answer business questions.

Examples include:

 Revenue by Gender

```sql
SELECT gender,
       SUM(purchase_amount) AS revenue
FROM customer
GROUP BY gender;
```

 Subscriber Analysis

```sql
SELECT subscription_status,
       COUNT(customer_id) AS total_customers,
       ROUND(AVG(purchase_amount), 2) AS avg_spend,
       ROUND(SUM(purchase_amount), 2) AS total_revenue
FROM customer
GROUP BY subscription_status;
```

Customer Segmentation

Customers were categorized into:

- New
- Returning
- Loyal

based on their number of previous purchases.

The project also uses CTEs and window functions to identify the most purchased products within each category.

---

Power BI Dashboard

An interactive Power BI dashboard was created to present the analyzed data in an easy-to-understand format.

The dashboard can be used to explore areas such as:

- Customer demographics
- Purchase behavior
- Revenue
- Product performance
- Customer subscriptions
- Discounts
- Shipping preferences
- Customer segments

The dashboard provides a visual layer on top of the cleaned and analyzed dataset, making the findings easier for business users to understand.

---

Results & Insights

The analysis focuses on identifying patterns such as:

- Differences in revenue between customer groups
- Spending behavior of subscribed and non-subscribed customers
- Product ratings and product performance
- Discount usage across products
- Differences between shipping methods
- Customer loyalty based on previous purchases
- Repeat-purchase behavior
- Revenue contribution across age groups
- Top-performing products within categories

For example, the SQL analysis calculates revenue by age group and orders the groups by total revenue.

These insights can help businesses better understand customer behavior and identify areas for improving customer engagement, promotions, and product strategy.

---

Project Deliverables

The project includes:

```text
Customer Shopping Behavior Analysis
│
├── customer_shopping_behavior.csv
├── Customer_Shopping_Behavior_Analysis.ipynb
├── customer_behavior_sql_queries.sql
├── customer_behavior_dashboard.pbix
├── Project Report
└── Gamma Presentation
```

---
 How to Run

 Step 1: Clone or Download the Project

Download the project files to your local machine.

 Step 2: Install Python Libraries

Install the required Python libraries:

```bash
pip install pandas sqlalchemy psycopg2-binary pymysql pyodbc
```

 Step 3: Open the Notebook

Open:

```text
Customer_Shopping_Behavior_Analysis.ipynb
```

using Jupyter Notebook, JupyterLab, or Google Colab.

 Step 4: Load the Dataset

Place the CSV file in the appropriate project directory and run the data-loading cells.

```python
df = pd.read_csv("customer_shopping_behavior.csv")
```

 Step 5: Perform Data Preparation

Run the EDA, data-cleaning, and feature-engineering steps in the notebook.

 Step 6: Load Data into SQL

Create a database named:

```text
customer_behavior
```

Then load the cleaned DataFrame into a table named:

```text
customer
```

The notebook contains connection examples for PostgreSQL, MySQL, and Microsoft SQL Server.

**Important:** Replace database usernames, passwords, host details, and other connection settings with your own local configuration. Do not commit passwords or credentials to GitHub.

 Step 7: Run SQL Queries

Open:

```text
customer_behavior_sql_queries.sql
```

Run the queries against the `customer` table to reproduce the business analysis.

 Step 8: Open the Power BI Dashboard

Open:

```text
customer_behavior_dashboard.pbix
```

If required, update the data source connection in Power BI and refresh the dataset.

 Step 9: Review the Report and Presentation

The final insights can be summarized using the project report and Gamma presentation.

---

 Key Skills Demonstrated

- Data Analysis
- Exploratory Data Analysis (EDA)
- Data Cleaning
- Data Transformation
- Feature Engineering
- Python
- Pandas
- SQL
- PostgreSQL
- MySQL
- SQL Server
- Power BI
- Data Visualization
- Business Insights
- Presentation & Reporting

---

 Conclusion

This project demonstrates an end-to-end approach to data analytics, starting with raw customer data and progressing through data preparation, SQL-based business analysis, visualization, reporting, and presentation.

It showcases the ability to work with data using **Python and SQL**, transform analysis into **Power BI visualizations**, and communicate findings through a structured report and presentation.
