# Practical Execution Task (AI/ML)

**Duration:** 3 hours (2:00 PM – 5:00 PM)  
**Prepared By:** JobAxle  

---

## 📌 Overview
This project demonstrates a complete machine learning workflow applied to housing price prediction. The dataset contains housing attributes such as **area (sqft), bedrooms, bathrooms, year built, location, and garage availability**, with the target variable being **price**. The goal was to clean and analyze the dataset, train multiple models, evaluate their performance, and select the most suitable approach for real-world application.

---

## 🛠️ Steps and Findings

### Q1: Load Dataset
- Imported dataset using **pandas**.  
- Inspected structure, data types, and anomalies (missing values, inconsistent entries).

### Q2: Clean Dataset
- Handled missing values via imputation/removal.  
- Corrected inconsistent categorical entries.

### Q3: Visualize Patterns
- Used histograms, scatter plots, and correlation heatmaps.  
- Found strong correlation between **area** and **price**, weaker relation with **year built**.

### Q4: Encode Categorical Variables
- Applied **one-hot encoding** for location and garage.  
- Used **label encoding** for condition.

### Q5: Split Dataset
- Train-test split: **80/20 ratio**.  
- Justified as a standard balance between training and evaluation.

### Q6: Train Linear Regression
- Trained model and interpreted coefficients.  
- Weak fit due to non-linear housing data.

### Q7: Evaluate Linear Regression
- **R² (Test) = -0.023** → poor performance.  
- MAE and RMSE indicated large prediction errors.

### Q8: Train Decision Tree
- Trained with depth tuning.  
- Observed overfitting at higher depths.  
- **R² (Test) = -0.116**.

### Q9: Feature Scaling
- Applied **StandardScaler**.  
- Scaling improved KNN performance slightly, minimal effect on Linear Regression and Decision Tree.

### Q10: Implement KNN
- Tuned k values.  
- Best k gave **R² (Test) = -0.19** → weak accuracy.

### Q11: Save & Reload Model
- Saved Decision Tree using **joblib**.  
- Reloaded successfully for prediction.

### Q12: Predictions on Unseen Data
- Predicted price = **299,396.5**.  
- Actual price = **310,000**.  
- Validation: MAE = **10,603.5**, RMSE = **10,603.5** (~3–4% error).

### Q13: Clustering
- Applied **KMeans (k=3)**.  
- Cluster 0: large homes (~4169 sqft).  
- Cluster 1: small homes (~1270 sqft).  
- Cluster 2: mid-sized homes (~2732 sqft).  
- Interpreted clusters as market segments.

### Q14: Compare Models

| Model              | R² (Test) | Notes                                      |
|--------------------|-----------|--------------------------------------------|
| Linear Regression  | -0.023    | Simplest model, assumes linearity           |
| Decision Tree      | -0.116    | Captures non-linear splits, risk of overfit |
| KNN                | -0.19     | Sensitive to scaling, weakest performance   |

**Best Selection:**  
Despite all low R² values, **Decision Tree** was chosen. It captures non-linear housing patterns better than Linear Regression or KNN, and can be improved with tuning or ensembles.

---

## Q15: Real-World Problem and Model Choice

**Problem:** Predict housing prices for a real estate company to guide buyers and sellers.  

**Detailed Justification:**  
- **Linear Regression** gave the least negative R² (-0.023), but it assumes a straight-line relationship between features and price. Housing markets rarely behave linearly — location, amenities, and thresholds (e.g., area > 2000 sqft) cause sudden jumps in price. This makes Linear Regression misleading despite its slightly better metric.  
- **Decision Tree**, although showing a lower R² (-0.116), is more suitable because it can capture **non-linear interactions and conditional rules**. For example: *“If area > 2000 sqft and garage = yes, then higher price.”* These rules are interpretable and align with how real estate agents explain pricing to clients.  
- **KNN** performed worst (-0.19) due to sensitivity to scaling and lack of robustness for this dataset.  

**Trade-Offs:**  
- **Pros (Decision Tree):** Handles complex data, interpretable, easy to explain to non-technical users.  
- **Cons:** Risk of overfitting, lower raw R² compared to Linear Regression.  
- **Solution:** Performance can be improved with tuning (depth control, pruning) or ensemble methods (Random Forest, Gradient Boosting).  

**Conclusion:**  
Decision Tree is the most practical choice for real-world housing price prediction. While Linear Regression appears “better” by raw R², it oversimplifies the data and fails to capture the true complexity of housing markets. Decision Trees align better with real-world patterns and can be enhanced further, making them more useful in practice.

---

##  Final Summary
This project executed the full ML pipeline: data cleaning, visualization, encoding, model training, evaluation, clustering, and deployment.  
Although all models showed low R², the **Decision Tree** was selected as the most practical choice due to its ability to capture non-linear relationships and provide interpretable rules.  
This highlights the importance of considering **real-world applicability and trade-offs** beyond raw metrics when selecting machine learning models.
