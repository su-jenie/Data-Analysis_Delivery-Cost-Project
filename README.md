# Delivery Cost & Commission Strategy Analysis

This project analyzes the cost structure of a food delivery platform and explores how different commission strategies affect the profitability of both the platform and merchants.

The analysis was conducted as part of a **data analytics bootcamp project** and focuses on applying data analysis to support platform pricing decisions.

---

# Business Context

Food delivery platforms generate revenue primarily through **commissions charged to restaurants**.

However, commission policies involve a key trade-off:

- Higher commissions increase **platform revenue**
- But they reduce **merchant margins**, potentially discouraging restaurants from remaining on the platform.

This creates an important strategic question:

**How can a delivery platform design a commission structure that maximizes profit while maintaining sustainable merchant margins?**

This project explores that question using exploratory data analysis and commission simulations.

---

# Key Questions

1. How is revenue distributed between the platform and merchants?
2. How do different commission rates affect platform profit?
3. What commission range maintains sustainable merchant margins?
4. Can **tiered commission strategies** outperform a flat commission model?

---

# Dataset

Dataset used in this project:

ZERO Base Project – Delivery Cost Analysis  
Source: Kaggle  

https://www.kaggle.com/datasets/linerpark/zero-base-project-delivery-cost-analysis

The dataset contains simulated food delivery order data including:

- Restaurant ID
- Order value
- Delivery cost
- Platform share
- Merchant share
- Platform profit
- Merchant profit

Each row represents a single delivery order.

---

# Analytical Approach

The analysis follows the steps below.

## 1. Data Cleaning

- Handling missing values
- Preparing variables for profit analysis

## 2. Exploratory Data Analysis (EDA)

Key aspects explored:

- Distribution of order values
- Profit distribution between platform and merchants
- Differences across restaurants

## 3. Profit Structure Analysis

Order revenue is decomposed into:

- Platform revenue
- Merchant revenue
- Platform profit
- Merchant profit

This helps reveal how value is distributed within the delivery ecosystem.

## 4. Commission Rate Simulation

Different commission rate scenarios are simulated to evaluate:

- Platform total profit
- Merchant average margin

Constraints are applied to ensure realistic business conditions.

## 5. Segment-Based Commission Strategy

Restaurants are segmented by **sales percentile**, and different commission rates are applied to each segment.

This approach reflects real-world pricing strategies used by platform businesses.

---

# Key Insights

The analysis suggests several important insights:

- Increasing commission rates improves platform profit only up to a certain threshold.
- Beyond that point, merchant margins decline rapidly.
- **Segmented commission structures** can balance platform profitability and merchant sustainability more effectively than a flat commission model.

---

# Technologies Used

Python libraries used in this project:

- pandas
- numpy
- matplotlib
- seaborn

---

# Repository Structure

delivery-cost-analysis  
│  
├── notebook  
│   └── Delivery_Cost_Analysis.ipynb  
│  
├── data  
│   └── food_orders_new_delhi.csv  
│  
├── requirements.txt  
│  
└── README.md  

---

# How to Run

Clone the repository

git clone https://github.com/su-jenie/Data-Analysis_Delivery-Cost-Project.git

Install dependencies

pip install -r requirements.txt

Open the notebook

notebook/Delivery_Cost_Analysis.ipynb

The analysis can be executed using:

- Jupyter Notebook
- Google Colab

---

# Author

Sujin Heo
