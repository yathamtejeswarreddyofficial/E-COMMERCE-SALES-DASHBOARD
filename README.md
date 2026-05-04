# Week 4 - E-Commerce Sales Dashboard using ETL and Power BI

## 📌 Project Overview

This project focuses on **ETL and Data Visualization for an E-Commerce Sales Dashboard** using the **Sample Superstore** dataset. The project performs data extraction, cleaning, transformation, KPI calculation, chart generation, and dashboard development using **Power BI**.

The main goal of this project is to analyze sales performance, profit trends, customer segments, product categories, and loss-making orders to support better business decision-making.

---

## 🎯 Objectives

- Extract sales data from the Sample Superstore CSV dataset.
- Clean and preprocess the dataset using Python.
- Create useful business metrics such as revenue, profit, profit margin, shipping days, and loss-making orders.
- Generate visual charts for sales and profit analysis.
- Build an interactive Power BI dashboard for business insights.
- Identify top-performing products, categories, segments, and yearly trends.

---

## 🗂️ Project Files

```text
Week - 4 New.pbix.zip
├── Week - 4 ETL (1).html       # Exported Python/Jupyter ETL notebook report
├── DataModel                   # Power BI data model file
├── Report/Layout               # Power BI report layout
├── Metadata                    # Power BI metadata
├── Settings                    # Power BI settings
├── Version                     # Power BI version information
├── DiagramLayout               # Power BI model diagram layout
├── SecurityBindings            # Power BI security-related file
└── Report/StaticResources      # Power BI theme/resources
```

> Note: The uploaded ZIP contains the internal structure of a Power BI `.pbix` report along with an HTML-exported ETL notebook.

---

## 🧰 Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Plotly**
- **Power BI**
- **Tableau-ready cleaned CSV output**
- **Jupyter Notebook / HTML Export**

---

## 📊 Dataset Used

**Dataset:** Sample Superstore CSV

The dataset contains e-commerce sales records with fields such as:

- Order ID
- Order Date
- Ship Date
- Customer Name
- Segment
- Country
- City
- State
- Region
- Category
- Sub-Category
- Product Name
- Sales
- Quantity
- Discount
- Profit

---

## 🔄 ETL Workflow

### 1. Extract

The dataset is loaded from a CSV file using Python.

```python
df = pd.read_csv(csv_path, encoding='latin1')
```

The script also includes an automatic file finder to locate the `Sample - Superstore.csv` file from common local folders such as Downloads, Desktop, and Documents.

### 2. Transform

The following cleaning and transformation steps are performed:

- Removed duplicate records.
- Removed rows with missing `Sales` or `Profit` values.
- Converted `Order Date` and `Ship Date` into proper date format.
- Created new columns for analysis:
  - `Year`
  - `Month`
  - `Profit Margin`
  - `Days to Ship`
  - `Loss Making`

```python
df['Year'] = df['Order Date'].dt.year
df['Month'] = df['Order Date'].dt.to_period('M')
df['Profit Margin'] = df['Profit'] / df['Sales']
df['Days to Ship'] = (df['Ship Date'] - df['Order Date']).dt.days
df['Loss Making'] = df['Profit'] < 0
```

### 3. Load

The cleaned dataset is exported as:

```text
cleaned_superstore.csv
```

This file can be used directly in Power BI or Tableau.

---

## 📈 Key Performance Indicators

The ETL output calculated the following KPIs:

| Metric | Value |
|---|---:|
| Total Records | 9,994 |
| Total Columns After Cleaning | 26 |
| Missing Values | 0 |
| Duplicate Rows | 0 |
| Date Range | 2014-01-03 to 2017-12-30 |
| Total Revenue | $2,297,200.86 |
| Total Profit | $286,397.02 |
| Average Profit Margin | 12.0% |
| Unique Orders | 5,009 |
| Loss-Making Orders | 1,871 |
| Loss Rate | 18.7% |

---

## 📅 Yearly Performance Summary

| Year | Revenue | Profit | Orders | Customers | Margin |
|---|---:|---:|---:|---:|---:|
| 2014 | $484,247 | $49,544 | 969 | 595 | 10.2% |
| 2015 | $470,533 | $61,619 | 1,038 | 573 | 13.1% |
| 2016 | $609,206 | $81,795 | 1,315 | 638 | 13.4% |
| 2017 | $733,215 | $93,439 | 1,687 | 693 | 12.7% |

---

## 📊 Generated Visualizations

The ETL notebook generated multiple charts for analysis:

1. Revenue and Profit Trend
2. Category-wise Bar Chart
3. Top Products Analysis
4. Segment Funnel Chart
5. Sub-Category Profit Margin
6. Loss Rate Analysis
7. Sales Map
8. Yearly Performance Summary
9. Discount vs Profit Analysis
10. Summary Dashboard

---

## 📌 Power BI Dashboard

The Power BI report contains a dashboard built from the cleaned Superstore dataset. It helps visualize:

- Revenue performance
- Profit performance
- Sales by category
- Sales by region/state
- Top products
- Segment-wise performance
- Discount impact on profit
- Loss-making orders
- Yearly business growth

---

## 🚀 How to Run This Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/your-repository-name.git
cd your-repository-name
```

### Step 2: Install Python Libraries

```bash
pip install pandas numpy matplotlib seaborn plotly
```

### Step 3: Place Dataset

Place the dataset file in your project folder:

```text
Sample - Superstore.csv
```

### Step 4: Run the ETL Notebook or Python Script

Run the ETL code from the notebook or convert it into a Python file:

```bash
python etl_superstore.py
```

After running, the cleaned file will be generated:

```text
cleaned_superstore.csv
```

### Step 5: Open Power BI Dashboard

1. Open **Power BI Desktop**.
2. Load the `.pbix` report file.
3. If required, reconnect the data source to `cleaned_superstore.csv`.
4. Refresh the dashboard.

---

## 📐 Suggested Power BI DAX Measures

```DAX
Revenue = SUM('cleaned_superstore'[Sales])
```

```DAX
Total Profit = SUM('cleaned_superstore'[Profit])
```

```DAX
Profit Margin = DIVIDE([Total Profit], [Revenue], 0)
```

```DAX
Total Orders = DISTINCTCOUNT('cleaned_superstore'[Order ID])
```

```DAX
Total Customers = DISTINCTCOUNT('cleaned_superstore'[Customer ID])
```

```DAX
Loss Making Orders = CALCULATE(COUNTROWS('cleaned_superstore'), 'cleaned_superstore'[Profit] < 0)
```

```DAX
Loss Rate = DIVIDE([Loss Making Orders], COUNTROWS('cleaned_superstore'), 0)
```

---

## 📷 Dashboard Preview

Add your Power BI dashboard screenshot here:

```markdown
![Dashboard Preview](images/dashboard-preview.png)
```

---

## ✅ Key Insights

- Revenue increased strongly from 2014 to 2017.
- Profit also improved year by year, with 2017 showing the highest profit.
- A considerable number of orders were loss-making, showing the importance of discount and profit analysis.
- Category, sub-category, and segment-level analysis helps identify profitable and non-profitable business areas.
- The cleaned dataset is ready for Power BI and Tableau reporting.

---

## 📚 Learning Outcomes

Through this project, I learned how to:

- Build an ETL pipeline using Python.
- Clean and transform raw CSV data.
- Create calculated business metrics.
- Generate charts using Python visualization libraries.
- Prepare cleaned data for BI tools.
- Build an interactive sales dashboard using Power BI.
- Analyze business KPIs such as revenue, profit, margin, and loss rate.

---

## 🔮 Future Enhancements

- Add more advanced DAX measures.
- Add forecasting for future sales and profit.
- Create region-wise drill-through pages.
- Add product-level profitability recommendations.
- Publish the dashboard to Power BI Service.
- Add automated refresh using cloud data sources.

---

## 👤 Author

**Yatham Tejeswar Reddy**

---

## 📄 License

This project is created for educational and portfolio purposes.
