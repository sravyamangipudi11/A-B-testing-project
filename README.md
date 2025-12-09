# A/B Testing Analysis: Facebook Ads vs Google AdWords  
**Evaluating Marketing Campaign Performance & Cost Efficiency (2019 Data)**

## 1. Business Problem
A marketing agency wants to maximize ROI across two major paid advertising channels: **Facebook Ads** and **Google AdWords (now Google Ads)**.  
The goal is to determine which platform delivers:
- Higher clicks and conversions
- Better cost-efficiency (lower CPC, higher ROI)
- More predictable performance  

This will guide future budget allocation and campaign optimization.

## 2. Research Question
**Which platform — Facebook Ads or Google AdWords — is more effective in terms of clicks, conversions and overall cost-efficiency?**

## 3. Dataset Description
- **Time period**: 365 daily observations (January 1 – December 31, 2019)
- **Metrics for both platforms**:
  - Ad Views (Impressions)
  - Ad Clicks
  - Ad Conversions
  - Cost per Ad (total spend)
  - Derived KPIs:
    - CTR = Clicks / Views
    - Conversion Rate = Conversions / Clicks
    - CPC = Cost / Clicks
    - Cost per Conversion = Cost / Conversions

## 4. Methodology

### A. Data Cleaning
- Converted date column to datetime
- Removed/parsed currency symbols and percentages
- Handled missing values and outliers
- Created calculated KPIs (CTR, Conversion Rate, CPC, Cost per Conversion)

### B. Exploratory Data Analysis (EDA)
- Distribution analysis of clicks, conversions and cost metrics
- Weekly and monthly seasonality patterns
- Day-of-week performance comparison
- Trend visualization of cost per conversion over time

### C. Statistical Analysis
- Pearson correlation between clicks and conversions (per platform)
- Independent two-sample t-test (Facebook vs Google conversions)
- Cointegration test (Engle-Granger) to assess long-term equilibrium between spend and conversions

### D. Predictive Modeling
- Simple Linear Regression: Conversions ~ Clicks (separate models per platform)
- Evaluation metrics: R², MSE, residuals analysis

## 5. Key Insights

### Platform Performance Comparison
| Metric                  | Facebook Ads        | Google AdWords       | Winner      |
|-------------------------|---------------------|----------------------|-------------|
| Average Daily Conversions | **Higher**          | Lower                | Facebook    |
| Average CPC              | **Lower**           | Higher               | Facebook    |
| Click-to-Conversion Correlation | **0.87** (strong) | 0.45 (moderate)      | Facebook    |
| Cost-efficiency          | Significantly better| -                    | Facebook    |

### Statistical Significance
- Independent t-test: Facebook mean conversions >> Google mean conversions  
  **p-value ≈ 9.35e-134** (extremely significant)
- Cointegration test confirms a stable long-term relationship between **Facebook spend and conversions** (not found for Google)

### 📌 Confidence Interval for Mean Conversion Difference (Added Section)
To understand the *practical* performance difference, a 95% confidence interval was computed:

- **Mean conversions (Facebook):** 11.74  
- **Mean conversions (Google):** 5.98  
- **Mean difference:** **+5.76 conversions per day**  

**95% Confidence Interval:** **(5.42, 6.11)**  

**Interpretation:**  
We are 95% confident that **Facebook generates between 5.4 and 6.1 more conversions per day** than Google.  
Since the CI does **not** include zero, the difference is both statistically significant and practically meaningful.

### Temporal Patterns
- Highest conversion volume: **Mondays and Tuesdays**
- Monthly dips: February, April, June, August, November
- Lowest CPC (best cost-efficiency): **May and November**

### Predictive Modeling Results
- Linear Regression (Facebook): **R² = 0.76** (strong fit)
- Practical predictions:
  - 50 clicks → ~10.8 conversions
  - 80 clicks → ~15.2 conversions
- Google model performed notably worse (lower R²)

## 6. Technologies Used
- **Language**: Python
- **Data Manipulation**: Pandas, NumPy
- **Visualization**: Matplotlib, Seaborn
- **Statistical Tests**: SciPy (t-test), statsmodels (cointegration)
- **Modeling**: scikit-learn (Linear Regression)

## 7. Conclusion & Recommendations
**Facebook Ads clearly outperformed Google AdWords in 2019** across nearly every meaningful metric:
- Higher conversion volume
- Stronger click-to-conversion relationship
- Significantly lower cost per click and cost per conversion
- More stable long-term performance
- Better predictability

### Actionable Recommendations
1. **Reallocate budget**: Shift a larger portion (recommended 65-80%) toward Facebook Ads
2. **Day-parting optimization**: Increase bids/spend on Mondays and Tuesdays
3. **Seasonal planning**: Prepare for natural dips in Feb/Apr/Jun/Aug/Nov; capitalize on high-efficiency months (May, November)
4. **Performance forecasting**: Use the Facebook linear model for realistic conversion estimates when planning click volume

**Final Verdict**: For this business and dataset, **Facebook Ads delivered superior ROI and should be the primary advertising channel**, with Google AdWords used selectively for intent-based or competitor targeting only.

---
