# 📊 E-commerce User Behavior Analysis

## 📌 Project Overview

This project analyzes user behavior in an e-commerce environment to identify key factors that drive purchase decisions.

The analysis combines:

* **SQL (BigQuery)** for data extraction
* **Python (Pandas, Matplotlib)** for data analysis
* **Looker Studio** for interactive dashboard visualization

---

## 🎯 Objectives

The main goal of this project is to answer the following question:

> **What factors influence user purchase behavior in an e-commerce platform?**

---

## 🛠️ Tools & Technologies

* Google BigQuery (SQL)
* Python (Pandas, Matplotlib)
* Looker Studio
* Google Colab (for Python execution)

---

## 📂 Dataset

The dataset contains user interaction data, including:

* `time_on_site` – time spent on the website
* `pages_viewed` – number of pages visited
* `cart_items` – number of items added to cart
* `previous_purchases` – number of past purchases
* `device_type` – device used (Mobile, Desktop, Tablet)
* `purchase` – target variable (0 = No, 1 = Yes)

---

## 🔍 Data Analysis

### 1. SQL Analysis (BigQuery)

Example query used to analyze behavior:

```sql
SELECT 
  purchase,
  AVG(time_on_site) AS avg_time,
  AVG(pages_viewed) AS avg_pages,
  AVG(cart_items) AS avg_cart,
  AVG(previous_purchases) AS avg_prev
FROM `ecommerce-analysis.ecommerce_data.user_behavior`
WHERE purchase IS NOT NULL
GROUP BY purchase;
```

---

### 2. Python Analysis

Example code:

```python
import pandas as pd

df = pd.read_csv("ecommerce_user_behavior_8000.csv")

df.groupby('purchase')[['time_on_site','pages_viewed','cart_items']].mean()
```

---

### 3. Data Visualization (Python)

```python
import matplotlib.pyplot as plt

df.groupby('purchase')['time_on_site'].mean().plot(kind='bar')
plt.title("Average Time on Site by Purchase")
plt.show()
```

---

## 📊 Dashboard (Looker Studio)

An interactive dashboard was created using Looker Studio.

### Key components:

* Conversion Rate (KPI)
* Average Time on Site by Purchase
* Average Pages Viewed by Purchase
* Cart Activity by Purchase Outcome
* User Distribution by Device Type

---

## 💡 Key Insights

* Users who spend more time on the website are significantly more likely to make a purchase.
* Cart activity is the strongest indicator of purchase intent.
* Users with more previous purchases are more likely to convert.
* Low engagement users show minimal purchase behavior.
* Mobile devices represent the majority of users.

---

## ⚠️ Data Limitations

* The dataset is highly imbalanced (very high conversion rate ~99%).
* Some missing values (NULL) were filtered during analysis.
* Results should be interpreted with caution.

---

## 📈 Conclusion

User engagement is the primary driver of conversion.
Metrics such as time on site, number of pages viewed, and cart activity strongly influence purchase decisions.

---

## 🚀 Future Improvements

* Use a more balanced dataset
* Apply machine learning models (classification)
* Add more behavioral features (e.g., session frequency)
* Enhance dashboard interactivity

---

## 👤 Author

This project was developed as part of a data analytics learning journey, focusing on real-world tools and business insights.

---

## 🌍 Note

This project is available in English for international accessibility.
An Italian version can be provided upon request.
