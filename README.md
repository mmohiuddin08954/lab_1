# Lab 1: Data Visualization, Data Preprocessing, and Statistical Analysis Using Python in Jupyter Notebook

**Name:** Muneeb Mohiuddin  
**Course:** Advanced Big Data and Data Mining (MSCS-634-M20)  
**Institution:** University of the Cumberlands  

---

## Purpose of the Lab

The purpose of this lab was to apply foundational data science techniques
using Python in a Jupyter Notebook environment. Specifically, the lab focused
on three core areas: data visualization, data preprocessing, and statistical
analysis. Using the Superstore Sales Dataset sourced from Kaggle, the goal
was to explore the data, understand its structure, clean and prepare it for
analysis, and extract meaningful insights through both visual and statistical
methods. This lab serves as a practical introduction to the end-to-end data
preparation pipeline that is essential before applying any machine learning
or data mining algorithms.

---

## Dataset

- **Name:** Superstore Sales Dataset  
- **Source:** [Kaggle - vivek468/superstore-dataset-final](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final)  
- **Description:** A retail dataset containing 9,994 records of orders across
  the United States, with information on sales, profit, quantity, discount,
  product categories, shipping modes, and regions.

---

## Key Insights from Visualizations

### Scatter Plot — Sales vs Profit
There is a general positive relationship between Sales and Profit. However,
several data points show high sales but negative profit, which can be
attributed to excessive discounting on certain orders. This highlights
that revenue alone does not guarantee profitability.

### Line Plot — Total Sales Over Time
Sales demonstrate a clear upward trend over the years, with noticeable
spikes occurring periodically. These spikes likely correspond to seasonal
shopping periods or promotional campaigns, suggesting that time-based
demand patterns play a significant role in this retail dataset.

### Bar Chart — Total Sales by Category
Technology recorded the highest total sales among the three product
categories, followed by Furniture and Office Supplies. This suggests
that the business generates the most revenue from technology products,
which could guide inventory and marketing decisions.

### Histogram — Distribution of Sales
The distribution of Sales values is heavily right-skewed, meaning the
majority of transactions involve relatively small amounts, while a small
number of high-value transactions pull the distribution to the right.
This skewness is an important consideration when applying machine
learning models that assume normality.

### Box Plot — Profit by Region
The West region consistently showed the highest median profit across
all four regions. All regions contained outliers on both ends of the
profit scale, indicating high variability in order-level profitability
regardless of geographic location.

### Pie Chart — Sales by Ship Mode
Standard Class was the dominant shipping mode, accounting for the
largest share of total sales. This suggests that most customers either
prefer or default to the standard shipping option, possibly due to
cost considerations.

---

## Key Insights from Statistical Analysis

### Central Tendency
- The mean Sales value was significantly higher than the median,
  further confirming the right-skewed nature of the Sales distribution.
- Profit had both a positive mean and a negative minimum, indicating
  that while the business is generally profitable, certain transactions
  result in losses.
- The most frequent Discount value (Mode) was 0.20, suggesting a
  standard 20% discount is commonly applied across orders.

### Dispersion
- Sales showed a very high standard deviation and range, reflecting
  the wide variety in transaction sizes from small office supplies
  to large furniture or technology orders.
- The IQR for Profit was relatively narrow compared to its full range,
  confirming that most profits are clustered in a moderate range
  with extreme outliers on both ends.

### Correlation Analysis
- Discount had a notable negative correlation with Profit, confirming
  that orders with higher discounts tend to generate lower or even
  negative profit margins.
- Sales and Profit showed a moderate positive correlation, though the
  relationship is weakened by the impact of discounting.
- Quantity had a weak correlation with both Sales and Profit,
  suggesting that volume alone does not strongly predict revenue
  or profitability.

---

## Challenges Faced and Decisions Made

### 1. Dataset Loading via KaggleHub
Rather than manually downloading and placing the CSV file, the dataset
was loaded directly using the `kagglehub` library. The code was written
to automatically detect the CSV file within the downloaded directory,
making the workflow more reproducible and portable across environments.

### 2. Encoding Issue
The CSV file required `encoding='latin-1'` to load correctly due to
special characters present in product names and customer data. Without
specifying the encoding, the file would throw a UnicodeDecodeError.
This was identified and resolved early in the data loading step.

### 3. Missing Values
Upon inspection, the dataset had very few missing values. The decision
was made to fill missing numeric values with the column mean and missing
categorical values with the column mode, rather than dropping rows, in
order to preserve as much data as possible for analysis.

### 4. Outlier Handling Decision
Outliers were detected in the Sales column using the IQR method.
Rather than removing them immediately from the main dataframe, a
separate cleaned dataframe (`df_no_outliers`) was created. This
decision was intentional — the original data was preserved for
statistical analysis while the cleaned version remains available
for future modeling tasks.

### 5. Discretization Bin Boundaries
When discretizing the Sales column into categories (Very Low, Low,
Medium, High, Very High), the bin boundaries were chosen based on
a manual inspection of the data distribution and domain knowledge
of typical retail transaction sizes, ensuring the categories were
meaningful and balanced.
