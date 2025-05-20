# 🧠 Predicting Customer Retention in Brazilian E-Commerce

A Machine Learning project that aims to predict whether a customer will make a repeat purchase using the Olist e-commerce dataset. This end-to-end project includes data preparation, feature engineering, customer segmentation, classification modeling, and actionable business insights for improving retention strategies.

---

## 📌 Table of Contents
- [📊 Business Context](#-business-context)
- [📁 Dataset Description](#-dataset-description)
- [🧼 Data Preparation](#-data-preparation)
- [📈 Modeling Approach](#-modeling-approach)
- [🔍 Key Results](#-key-results)
- [💡 Business Recommendations](#-business-recommendations)
- [🧰 Tech Stack](#-tech-stack)
- [📂 Project Structure](#-project-structure)
- [🚀 How to Run](#-how-to-run)
- [📎 References](#-references)

---

## 📊 Business Context

Customer retention is a key profitability driver in online marketplaces. Repeat customers tend to buy **67% more** than first-time buyers. However, in marketplaces like Olist, many customers **disintermediate** after the first purchase.

This project investigates whether it's possible to **predict repeat purchases** using customer behavior data. Our goal is to build a **classification model** that identifies customers likely to return — enabling the business to proactively increase retention through targeted strategies.

---

## 📁 Dataset Description

We used the **Brazilian E-Commerce Public Dataset by Olist**, which contains orders from 2016 to 2018, across several relational tables:

- `orders`, `order_items`, `order_reviews`, `order_payments`, `customers`

Key characteristics:
- 100k+ orders
- 96% of customers made **only one purchase**
- Class imbalance: 3% retained vs. 97% not retained

---

## 🧼 Data Preparation

To model retention:
- We created a **temporal cutoff**: all purchases until `2017-05-31` are considered “past”; repeat purchases after this date define the target.
- The **target variable (`retention`)** is binary: 1 = customer bought again after the cutoff, 0 = did not.

Feature engineering included:
- **Customer profile**: location, payment method, purchase time
- **Behavioral metrics**: review scores, delivery delays, frequency
- **Product/service mix**: category diversity, freight value, shipping speed

All transformations and aggregations were done using **SQL + pandas**.

---

## 📈 Modeling Approach

We applied both **unsupervised** and **supervised** techniques:

### 🎯 Classification
- **Goal**: Predict whether a customer will make another purchase
- **Models**: Random Forest and Logistic Regression
- **Challenges**: Severe class imbalance, noisy features, limited data
- **Validation**: 10-fold cross-validation using `Recall` as the main metric

| Metric         | Class 0 (Did not return) | Class 1 (Returned) |
|----------------|--------------------------|---------------------|
| **Recall**     | 0.64                     | 0.03 (imbalanced)   |
| **Best model** | Random Forest            |                     |

> The model detected 41 true returning customers (true positives), valuable for focused marketing.

### 👥 Clustering
We applied **K-Means** clustering to segment customers based on behavior and location. This revealed potential personas for targeted campaigns.

---

## 🔍 Key Results

- Retained customers represented only **3%** of the dataset.
- Key retention signals:
  - High review scores
  - Reliable shipping (delivery within estimated date)
  - Use of credit card with installments
- The model correctly identified 41 repeat buyers — representing high direct value.
- **Black Friday** drove high sales volume but **low retention impact**.

---

## 💡 Business Recommendations

✅ Launch targeted marketing based on cluster profiles  
✅ Create loyalty programs to avoid disintermediation  
✅ Offer free shipping or discounts to high-value profiles  
✅ Improve delivery reliability metrics via seller education  
✅ Analyze false positives as potential reactivation targets

---

## 🧰 Tech Stack

- **Python** (pandas, scikit-learn, seaborn, matplotlib)
- **SQL** (for data extraction and table building)
- **Jupyter Notebooks**
- **PowerPoint / PDF** (for business presentation)
- **Random Forest / Logistic Regression**
- **K-Means Clustering**

---

## 📂 Project Structure

```
customer-retention-prediction/
│
├── data/
│   └── (instructions to download Olist dataset)
│
├── notebooks/
│   ├── Projeto_1_Grupo_3_Data_Preparation_VF.ipynb
│   └── Projeto_1_Grupo_3_Modelling_VF.ipynb
│
├── outputs/
│   └── visuals/       # Charts, EDA plots, cluster maps
│
├── presentation/
│   └── Apresentação_Projeto1_Grupo3.pdf
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 🚀 How to Run

1. Clone the repository:
```bash
git clone https://github.com/yourusername/customer-retention-prediction.git
cd customer-retention-prediction
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Open and run the notebooks in order:
- `notebooks/Projeto_1_Grupo_3_Data_Preparation_VF.ipynb`
- `notebooks/Projeto_1_Grupo_3_Modelling_VF.ipynb`

> Make sure the dataset is available in the `data/` folder as described in the notebook.

---

## 📎 References

- [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- [Salesduo - Amazon Retention](https://salesduo.com/blog/customer-retention-on-amazon/)
- [McKinsey - E-Commerce Deliveries](https://www.mckinsey.com/industries/logistics/our-insights/what-do-us-consumers-want-from-e-commerce-deliveries)
- [Earnest Analytics - Retention Benchmarks](https://www.earnestanalytics.com/insights/)

---

## 🤝 Contact

**André Teixeira**  
[LinkedIn](https://www.linkedin.com/in/andrelteixeira/) | [GitHub](https://github.com/yourusername)
