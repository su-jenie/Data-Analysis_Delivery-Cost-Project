# Platform Strategy Simulation for a Delivery Marketplace
### Commission and Promotion Optimization for a Two-Sided Platform

## Overview

This project analyzes the profitability structure of a hypothetical food delivery platform and explores how different **commission policies** and **promotion strategies** affect both the platform and merchants.

Rather than focusing only on descriptive analysis, this project was designed around a business question: **how can a new platform grow through promotions without undermining long-term profitability or merchant sustainability?**

To answer that question, I constructed profit-related metrics from raw transaction data and simulated alternative operating policies such as **tiered commission rates, promotion cost-sharing rules, and customer-segmented coupon strategies**.

## Dataset

This project uses a delivery-related dataset provided through a bootcamp exercise and sourced from ZeroBase:

[Delivery Cost Analysis Dataset](https://www.kaggle.com/datasets/linerpark/zero-base-project-delivery-cost-analysis)

The dataset contains order-level information such as:

- order value
- commission fee
- delivery fee
- discount campaigns
- payment processing fee

These variables were used to reconstruct the profit structure of both the platform and merchants.

## Business Objective

The goal of this project was to design a more sustainable operating strategy for a delivery marketplace by addressing three practical questions:

1. How should promotion costs be shared between the platform and merchants?
2. Should the same commission rate apply to every restaurant?
3. How should coupon campaigns be structured to balance customer acquisition, retention, and profitability?

Instead of maximizing platform profit alone, the analysis aimed to identify policies that could improve platform profitability **while maintaining merchant viability**.

## Metric Design

One of the main challenges in this project was defining derived metrics in a way that better reflects how a real platform might operate.

The raw dataset did not directly provide platform or merchant profit, so profit-related metrics were constructed based on explicit business assumptions.

```python
df['Real Order Value'] = df['Order Value'] - df['Discount Cost']

df['Platform Profit'] = (
    df['Commission Fee']
    - df['Discount Cost Platform']
    - df['Delivery Fee Platform']
)

df['Merchant Profit'] = (
    df['Real Order Value']
    - df['Commission Fee']
    - df['Payment Processing Fee']
    - df['Delivery Fee Merchant']
)

df['Platform Share'] = df['Platform Profit'] / df['Real Order Value']
df['Merchant Share'] = df['Merchant Profit'] / df['Real Order Value']
```

This structure made it possible to compare different policy scenarios by changing cost-sharing assumptions, coupon rules, and commission schemes.

## Strategy Design

### 1. Tiered Commission Policy by Restaurant Revenue

Restaurants were segmented by total sales percentile, and different commission rates were applied to each group instead of using a flat rate.

| Restaurant Segment | Commission Rate |
|---|---:|
| Top 35% | 13% |
| Middle 35–65% | 12% |
| Bottom 65–100% | 11% |

This reflects the idea that a uniform commission policy may not be appropriate for all merchants. Higher-revenue restaurants may be able to absorb a slightly higher take rate, while smaller merchants may require a lower fee structure.

### 2. Promotion Cost Sharing Between Platform and Merchants

Promotion and delivery costs were shared as follows:

**Platform 30% : Merchant 70%**

This ratio was designed under two constraints:

- platform average margin should remain at or above **10%**
- merchant average margin should remain at or above the **baseline level from the original dataset (~68%)**

The merchant margin threshold was based on the original data, under the assumption that a new strategy should at least avoid making merchant profitability worse than before.

### 3. New User Coupon Restriction

The dataset included a **15% New User** coupon.

To prevent overuse, the policy was revised so that this coupon would function strictly as a first-order acquisition tool. If the same customer used the **15% New User** coupon again on a second order, the second coupon was removed.

This reflects a common marketplace strategy: offer a strong initial incentive to encourage trial, but prevent repeated use of a high-cost acquisition coupon.

### 4. VIP-Focused Coupon Targeting

The **10% discount coupon** was redesigned as a targeted retention tool.

Customers were ranked by total order value, and multiple VIP thresholds were tested. Under this policy:

- VIP customers retained the **10% coupon**
- non-VIP customers were reassigned to lower-cost alternatives:
  - **5% on App**
  - **50 off Promo**
  - or **no coupon**

This approach aimed to reserve higher-cost promotions for customers with stronger revenue contribution, while reducing unnecessary discount spending on lower-value segments.

### 5. Simulation-Based Policy Evaluation

Instead of selecting policies based only on intuition, the project evaluated multiple policy scenarios through simulation.

Examples include:

- testing different VIP thresholds
- reassigning coupons for non-VIP customers
- comparing repeated random promotion reassignment outcomes

This made it possible to compare policy alternatives under both favorable and unfavorable conditions, rather than relying on a single fixed assumption.

## Key Findings

- Profitability is highly sensitive to how promotion costs are allocated between the platform and merchants.
- A flat commission policy can create uneven pressure across restaurants with different revenue levels.
- High-cost coupons become more effective when their role is clearly separated between **customer acquisition** and **customer retention**.
- Promotion design becomes more sustainable when combined with explicit profit constraints for both sides of the marketplace.

## Tech Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab

## Project File

- `Delivery_Cost_Analysis.ipynb`

## Author

**Sujin Heo**  
Mobile Software Test Engineer interested in data analytics, decision systems, and platform strategy
