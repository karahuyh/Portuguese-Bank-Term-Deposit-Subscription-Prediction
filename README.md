<div align="center">

# Portuguese Bank Term Deposit Subscription Prediction
### Predicting customer subscription likelihood using machine learning and cost-sensitive classification

![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-0F766E?style=for-the-badge)
![CRISP-DM](https://img.shields.io/badge/CRISP--DM-455A64?style=for-the-badge)
![SMOTE](https://img.shields.io/badge/SMOTE-0EA5A4?style=for-the-badge)
![Random Forest](https://img.shields.io/badge/Random%20Forest-2E7D32?style=for-the-badge)
![SVM](https://img.shields.io/badge/SVM-7C3AED?style=for-the-badge)

</div>


## 💻 Project Overview
This machine learning project aims to predict customer subscriptions to term deposits in a Portuguese bank’s marketing campaign during the period of 2008-2010. The project applies the **CRISP-DM methodology** (Cross-Industry Standard Process for Data Mining), imbalance handling techniques, and four classification models to optimise marketing performance while minimising business costs.

## 🔧 Business Context and Strategic Importance
Term deposits are a key source of stable funding of banks, supporting liquidity, lending and profitability. During the  2008-2019 global financial crisis and eurozone debt crisis, Portuguese banks relied heavily on attracting long-term deposits to strengthen financial stability and meet increased capital requirements. 

## 💼 Business Value of Predictive Modeling
Predictive modeling improves the efficiency of term deposit marketing by identifying customers most likely to subcribe. This helps banks to reduce:
- unnecessary marketing contacts,
- lower operating costs,
- optimize resource allocation,
- personalize customer engagement and
- increase campaign ROI through targeted marketing strategies

## 💰 Business Objectives 
This project aims to:

- Increase campaign ROI by identifying customers with a subscription probability above 30%, aiming for conversion rates of 25–35%.
- Improve marketing efficiency by allocating resources to high-value customer segments, reducing marketing costs by 20–30% while maintaining or improving subscription rates.
- Reduce customer contact fatigue by cutting unnecessary marketing contacts by at least 40%, improving customer relationships and ensuring continued campaign effectiveness.


## 🔧 Business Question
a) Customer Segmentation
- Which demographic factors (age, job, marital status, education) and financial indicators
(balance, default, housing, loan) most strongly predict subscription likelihood?
- Which customer profiles combine high conversion potential with manageable risk?

b) Resource Optimization
- How should marketing budgets and contacts be allocated across segments and channels
(cellular vs. telephone) to maximize ROI?
- Which customer groups offer the highest return per contact or marketing dollar?

c) Campaign Timing and Contact Strategy
- How do timing variables (day of week, economic conditions) influence response rates?
- What is the optimal contact frequency to maximize conversions without causing fatigue?

d) Reach–Precision Balance
- What is the ideal trade-off between broad campaign reach and targeted precision to sustain customer trust and maximize long-term value?


## 📊 Dataset 
### Dataset Overview

- **Source:** Portuguese Bank Marketing Dataset (`bank-additional-full.csv`)
- **Records:** 41,188 customer observations
- **Features:** 20 input variables + 1 target variable (
- **Target Variable:** `y` (Term Deposit Subscription: Yes/No)
- **Problem Type:** Binary Classification
- **Class Distribution:** Highly imbalanced (~11% positive class)

<div align="center">

<img width="450" height="284" alt="Screenshot 2026-06-30 at 4 00 38 PM" src="https://github.com/user-attachments/assets/23b4f070-c3ca-44af-a1d7-941252913788" />

</div>

### 🧹 Dataset Cleaning, and Preperation
| Data Cleaning Task | Description|
| ------------- | ------------- |
| Duplicate Data | Entries with non-positive call durations, abnormal ages (<18 or >100) and repeated rows were removed |
| Missing/Incomplete Data  | Converted `unknown` to NA  |
| Outlier Management | Capped numerical variables at the 1st and 99th percentiles to reduce the influence of extreme values  |
| Categorical Encoding | Applied ordinal encoding to ordered variables and one-hot encoding to nominal variables  |
| Feature Engineering | Created a new feature, `previously_contacted`, from the `pdays` variable to indicate whether a customer had been contacted previously. The original `pdays` column was then removed to avoid redundancy  |


## Data Sampling and Validation Strategy
### Temporal Data Handling and Train-Test Split
| Sampling | Description|
| ------------- | ------------- |
| Temporal Data Handling and Train-Test Split | Sorted records chronologically (March to December) and performed a 70/30 temporal train-test split to prevent data leakage  |
| Class Imbalance Handling | Compared Random Oversampling, Random Undersampling, ROSE, and SMOTE, ultimately selecting SMOTE as the best sampling technique for model training  |


<div align="center">
  
<img width="554" height="413" alt="Screenshot 2026-07-01 at 3 01 23 PM" src="https://github.com/user-attachments/assets/9beec2e1-03be-4900-8dbc-4cce2f4ee34f" />

*Temporal Data Preparation and Train-Test Split*


<img width="575" height="340" alt="Screenshot 2026-07-01 at 3 02 59 PM" src="https://github.com/user-attachments/assets/f5d7457e-8919-45b4-ba43-3d479d1a7325" />

*Class Imbalance Summary: 9.8% positive class - training data, 14.67% - test data*

</div>

### Sampling Strategy
| Type | Description|
| ------------- | ------------- |
| Imbalanced (Original) | Used during testing -> helps reflect real-world customer distribution.   |
| Balanced (Unsampled | Used during model training to help the algorithm learn both classes fairly and improve its ability to identify subscribers.|

## 🔍 Machine learning models:
Models developed
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- k-Nearest Neighbours (kNN)

## 📈 Models Evaluation Summary
### Model Comparison

| Model | Accuracy | Precision | Recall | F1 Score | AUC-ROC | Strength |
|:------|---------:|----------:|-------:|---------:|--------:|:---------|
| Decision Tree | 76.56% | 38.14% | **96.14%** | 54.62% | 87.06% | Highest recall, highly interpretable |
| Random Forest | 80.78% | 42.50% | 88.02% | 57.33% | **89.80%** | Best ranking performance (AUC) |
| SVM | **83.20%** | **46.50%** | 82.60% | **59.50%** | 86.30% | Best overall balance (highest Accuracy & F1) |
| kNN | 81.00% | 41.52% | 71.63% | 52.57% | 85.10% | Simple baseline with competitive performance |

### 🏆 Best Performing Models

| Category | Model |
|:---------|:------|
| Highest Accuracy | 🥇 Support Vector Machine (83.20%) |
| Highest Precision | 🥇 Support Vector Machine (46.50%) |
| Highest Recall | 🥇 Decision Tree (96.14%) |
| Highest F1 Score | 🥇 Support Vector Machine (59.50%) |
| Highest ROC-AUC | 🥇 Random Forest (89.80%) |

### Model benefits to the Portuguese Banks & Business Insights:
**Support Vector Machine (SVM)**
- **Organizational Benefits**: SVM acts as the premier model for high-precision targeting. For a Portuguese bank, deploying this model maximizes term deposit acquisitions while minimizing unnecessary outreach costs and avoiding contact fatigue.
- **Business Insights**: The large-margin classification principle of the RBF (Radial Basis Function) kernel handles non-linear customer behaviors effectively, proving highly successful at mapping complex demographic-economic interactions. This ensures steady, reliable performance across complex customer segments.

**Random Forest (RF)**
- **Organizational Benefits**: Random Forest delivers the highest AUC and recall. Its structural advantage lies in its stability, and native feature importance metrics, making it significantly easier to operationalize, govern, and explain to non-technical stakeholders compared to margin-based black boxes.
- **Business Insights**: Because it achieves the highest AUC, the RF model is the most powerful tool for ranking customers. If a bank has a constrained marketing budget or a fixed number of available telemarketing hours, it can use the model to rank leads from highest to lowest probability and strictly contact the top- $N$ candidates to maximize conversion ROI.

**Decision Tree**
- **Organizational Benefits**: While it underperforms on precision, the Decision Tree achieves the absolute highest recall. Its primary value to an organization is its absolute rule-based transparency. It serves as an excellent low-cost triage pass to coarsely segment a large customer database before handing leads off to more complex models.
- **Business Insights**: The tree reveals call duration as the single most critical behavioral indicator of intent, making its first statistical split at 364 seconds. It uncovers that calls lasting over 553 seconds result in an 88% success rate, whereas short calls yield a mere 2% subscription rate.

**k-Nearest Neighbors (kNN)**
- **Organizational Benefits**: kNN provides a simpler, proximity-based framework for identifying potential subscribers based on customer similarity.
- **Business Insights**: While it underperformed relative to the ensemble and margin-based models due to its sensitivity to mixed data types and data imbalance, its precision-recall curve proved that it still retrieves subscribers at a rate substantially better.

### Macro-Economic & Strategic Insights for the Organization
- **Counter-Cyclical Saving Behaviors**: The report highlights a crucial historical window (2008–2010) marked by the global financial crisis and the Eurozone sovereign-debt crisis. During this highly volatile period, tighter lending conditions heavily constricted job growth, resulting in strong positive correlations between employment levels (nr.employed), employment variation rates (emp.var.rate), and interest rates (euribor3m).  
- **Leveraging Consumer Risk-Aversion**: While overall consumer confidence was weak, Portuguese banks were under intense regulatory pressure to capture stable, long-term funding to meet higher capital requirements. The models successfully exploit the business reality that during economic instability, specific low-risk demographics (such as retirees, who achieved a 25.23% conversion rate, and customers aged 65+, who achieved a 47.21% conversion rate) heavily seek safe, government-insured options like term deposits.
- **Optimal Communication Channels**: The report identifies a stark contrast between outreach mechanisms, showing that cellular communication yielded a vastly higher success rate (14.74%) compared to traditional telephone lines (5.23%). This insight allows the organization to shift its communication infrastructure directly toward mobile-first strategies to maximize conversion per contact dollar.
