# 📊 Predicting Customer Conversion in Digital Marketing Campaigns

> A machine learning project that identifies which customers are most likely to convert, using behavioral engagement and campaign data — enabling smarter, data-driven marketing decisions.

---

## 🗂️ Table of Contents

- [Project Summary](#project-summary)
- [Objectives](#objectives)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Tools & Libraries](#tools--libraries)
- [Key Results](#key-results)
- [How to Run](#how-to-run)
- [Visualizations](#visualizations)
- [Ethics & Interpretability](#ethics--interpretability)
- [Author](#author)

---

## Project Summary

This project applies supervised machine learning to a digital marketing dataset of 8,000 customer records to predict whether a customer will **convert** (i.e., complete a desired action such as a purchase). Two classification models — **Logistic Regression** and **Random Forest** — are trained, evaluated, and compared. The analysis spans the full analytics lifecycle: exploratory data analysis, data preprocessing, predictive modeling, and actionable business insights.

The Random Forest model achieves **88.4% accuracy** and an **AUC of 0.82**, while Logistic Regression offers a more interpretable baseline with **95.2% precision**. Feature importance analysis reveals that **behavioral engagement metrics** (time on site, click-through rate, pages per visit) are the strongest predictors of conversion — more so than demographic or campaign channel variables.

---

## Objectives

1. **Identify the strongest predictors** of customer conversion across demographic, campaign, and behavioral features.
2. **Build and evaluate predictive models** (Logistic Regression and Random Forest) using accuracy, precision, recall, F1, and AUC-ROC.
3. **Answer business-relevant questions** about campaign channel effectiveness, customer segments, and actionable levers for improving conversion rates.
4. **Reflect on ethical implications** of deploying conversion prediction models, including demographic bias and model explainability.

---

## Dataset

| Attribute | Details |
|-----------|---------|
| **Source** | [Kaggle — Digital Marketing Campaign Dataset](https://www.kaggle.com/datasets/rabieelkharoua/predict-conversion-in-digital-marketing-dataset) |
| **Records** | 8,000 customers |
| **Features** | 20 (10 integer, 5 float, 5 categorical) |
| **Target** | `Conversion` — binary (1 = converted, 0 = did not convert) |
| **Class Balance** | 87.65% converted, 12.35% did not convert |

**Key features include:**
- **Demographics:** Age, Gender, Income
- **Campaign attributes:** CampaignChannel (Social Media, Email, PPC, Referral, SEO), CampaignType (Awareness, Retention, Conversion, Consideration), AdSpend
- **Behavioral engagement:** ClickThroughRate, ConversionRate, WebsiteVisits, PagesPerVisit, TimeOnSite, SocialShares, EmailOpens, EmailClicks
- **Customer history:** PreviousPurchases, LoyaltyPoints

---

## Project Structure

```
digital-marketing-conversion/
│
├── README.md                        ← You are here
├── .gitignore
│
├── notebooks/
│   └── Nancy_Final_Project.ipynb    ← Main analysis notebook (also on Colab — see below)
│
├── report/
│   └── term_project_report.docx     ← Final written report
│
└── visualizations/
    ├── 01_feature_histograms.png
    ├── 02_gender_distribution.png
    ├── 03_campaign_channel_distribution.png
    ├── 04_conversion_by_gender.png
    ├── 05_conversion_by_channel.png
    ├── 06_conversion_by_campaign_type.png
    ├── 07_correlation_heatmap.png
    ├── 08_logistic_regression_confusion_matrix.png
    ├── 09_random_forest_confusion_matrix.png
    ├── 10_logistic_regression_roc_curve.png
    ├── 11_random_forest_roc_curve.png
    └── 12_random_forest_feature_importances.png
```

---

## Tools & Libraries

| Tool / Library | Purpose |
|----------------|---------|
| **Python 3.x** | Core language |
| **pandas** | Data loading, manipulation, and exploration |
| **NumPy** | Numerical operations |
| **scikit-learn** | ML models, pipelines, preprocessing, and evaluation metrics |
| **matplotlib** | Base visualizations |
| **seaborn** | Statistical data visualization |
| **Google Colab** | Cloud-based notebook environment |
| **GitHub** | Version control and portfolio hosting |

---

## Key Results

### Model Performance Comparison

| Metric | Logistic Regression | Random Forest |
|--------|-------------------|---------------|
| Accuracy | 75.25% | **88.38%** |
| Precision | **95.23%** | 88.43% |
| Recall | 75.53% | **99.79%** |
| F1 Score | 84.25% | **93.77%** |
| ROC-AUC | 0.78 | **0.82** |

### Top Predictive Features (Random Forest)

1. **TimeOnSite** — How long a customer spends browsing is the single strongest signal
2. **ClickThroughRate** — High engagement with ads predicts intent
3. **PagesPerVisit** — Depth of site exploration indicates purchase consideration
4. **AdSpend** — Higher investment correlates with better audience targeting
5. **LoyaltyPoints / PreviousPurchases** — Existing customer relationships drive conversion

> Campaign channel (Social Media, Email, PPC, etc.) and campaign type have **low predictive importance** — *how* customers engage matters far more than *which* channel reaches them.

---

## How to Run

### Option 1: Google Colab (Recommended)

Click the badge below to open the notebook directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1PfMPS_PQYLVe5MXeP-PrD_UZau1WTkKf)

**Steps:**
1. Click the Colab badge above (or use the link in `notebooks/`)
2. In Colab, go to **File → Save a copy in Drive** to make your own editable copy
3. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/rabieelkharoua/predict-conversion-in-digital-marketing-dataset) and upload `digital_marketing_campiagn_dataset.csv` to your Colab session (or mount Google Drive)
4. Run all cells: **Runtime → Run all**

### Option 2: Run Locally

```bash
# 1. Clone the repository
git clone https://github.com/YOUR_USERNAME/digital-marketing-conversion.git
cd digital-marketing-conversion

# 2. Install dependencies
pip install pandas numpy scikit-learn matplotlib seaborn jupyter

# 3. Download the dataset from Kaggle and place it in the project root
#    File: digital_marketing_campiagn_dataset.csv

# 4. Launch Jupyter and open the notebook
jupyter notebook notebooks/Nancy_Final_Project.ipynb
```

---

## Visualizations

All plots are saved in the `visualizations/` folder. Key visuals include:

| # | Plot | Description |
|---|------|-------------|
| 01 | Feature Histograms | Distribution of all 16 numerical features |
| 02 | Gender Distribution | ~4,850 female vs. ~3,150 male customers |
| 03 | Campaign Channel Distribution | Roughly equal split across 5 channels |
| 04–06 | Conversion by Category | Conversion breakdown by Gender, Channel, and Campaign Type |
| 07 | Correlation Heatmap | Inter-feature linear relationships |
| 08–09 | Confusion Matrices | Logistic Regression vs. Random Forest classification results |
| 10–11 | ROC Curves | AUC = 0.78 (LR) vs. AUC = 0.82 (RF) |
| 12 | Feature Importances | Top 20 features ranked by Random Forest importance |

---

## Ethics & Interpretability

**Demographic bias:** Gender and Age are included as features. The Logistic Regression model assigns a positive coefficient to `Gender_Male`, which could lead to unequal campaign targeting. Any deployment should include **fairness audits** and consider whether demographic attributes reflect genuine purchase intent or introduce discriminatory patterns.

**Explainability:** Logistic Regression is directly interpretable via its coefficients — suitable for stakeholder communication. Random Forest, while more accurate, is a black-box ensemble. Tools like **SHAP** or **LIME** should be applied for per-prediction explanations, especially if the model is used to make automated decisions affecting customers.

**Deployment considerations:** Models should be monitored for performance drift over time, regularly re-evaluated for fairness, and subject to human oversight before being used to exclude or deprioritize customers from campaigns.

---

## Author

**Nancy**
Business Analytics Program
Boston University — Sargent College

---

*This project was completed as a term project for a Business Analytics course. Dataset sourced from Kaggle under open license.*
