# **Problem Statement**

### **Context**

Jamboree, a leading test preparation and admissions counseling company, has recently introduced a feature on their website that allows students to estimate their probability of gaining admission to Ivy League colleges. This feature is tailored to reflect the admissions landscape from an Indian perspective, helping students gauge their chances based on their academic and extracurricular profiles.

To enhance this tool, Jamboree seeks to better understand the key factors that influence graduate admissions. The objective of this analysis is twofold: first, to identify and analyze the factors that significantly impact admissions decisions, and second, to develop a predictive model that accurately estimates a student's chances of admission based on these factors.


### **How can you help here?**

Your analysis will provide Jamboree with insights into the importance of various factors, such as GRE scores, TOEFL scores, CGPA, research experience, and more. Additionally, it will explore how these factors are interrelated and how they collectively influence the likelihood of admission. The results of this study will be crucial in refining Jamboree's admissions prediction tool and in guiding students toward improving their profiles to increase their chances of acceptance into top graduate programs.

---
# Concepts, Algorithm, and Technologies Used

### Language:
- **Python**

### Modules:
- **NumPy**: For numerical computations and array operations.
- **Pandas**: For data manipulation, cleaning, and analysis.
- **Matplotlib**: For creating static visualizations to explore data distributions and relationships.
- **Seaborn**: For enhanced data visualizations, particularly for exploring relationships between variables.
- **Scikit-learn (sklearn)**: For implementing and evaluating machine learning models, including linear regression.
- **SciPy**: For performing statistical tests, such as the Goldfeld-Quandt test for homoscedasticity.

### Algorithm:
- **Linear Regression**: Used to model the relationship between the target variable (`Chance of Admit`) and the predictor variables (`GRE Score`, `TOEFL Score`, `CGPA`, etc.). This includes both standard linear regression and Ridge regression (L2 regularization) for model refinement.

### Concepts:
- **Exploratory Data Analysis (EDA)**: To understand the data, check for missing values, detect outliers, and analyze the distributions and relationships between variables.
- **Correlation Analysis**: To identify the strength of relationships between different variables and how they influence the target variable.
- **Assumptions of Linear Regression**: Ensuring the assumptions of linearity, no multicollinearity, normality of errors, and homoscedasticity were met to validate the model's reliability.
- **Model Performance Evaluation**: Using metrics like R², Adjusted R², MAE, MSE, and RMSE to assess the accuracy and predictive power of the regression models.
- **Regularization**: Implementing Ridge regression to prevent overfitting and ensure model generalization.
- **Statistical Testing**: Conducting tests such as the Goldfeld-Quandt test to verify the assumption of homoscedasticity in the regression model.

---
# **Insights**

## Summarizing Insights

### Exploratory Data Analysis (EDA) Insights

1. **Dataset Overview**:
   - **Rows/Samples**: 500
   - **Columns**: 8 (7 features and 1 target)
   - **No Missing Values or Duplicates**
   - **All Numeric Columns** (No encoding required)

2. **Distributions**:
   - GRE scores, TOEFL scores, CGPA, and the Chance of Admit follow a near-normal distribution.
   - SOP, LOR, and University Rating also exhibit a normal-like distribution.
   - **Research Work**: 56% (280 out of 500 applicants) mentioned research experience in their applications.

3. **Outliers**:
   - Some outliers exist in LOR and Chance of Admit, but overall, the dataset is outlier-free.

4. **Correlations**:
   - High correlation among GRE Score, TOEFL Score, CGPA, and Chance of Admit.
   - Applicants with research experience tend to have higher scores in GRE, TOEFL, CGPA, and higher chances of admission.
   - Strong linear relationships observed between the Chance of Admit and other features.

5. **Group Comparisons**:
   - Applicants with higher GRE, TOEFL scores, or CGPA generally have stronger SOP, LOR, and apply to higher-rated universities.
   - Similar patterns are seen in applicants with a higher chance of admission.

6. **Correlation Scores**:
   - Most feature pairs have a correlation score of ≥ 0.5, except for TOEFL Score vs Research, University Rating vs Research, SOP vs Research, and LOR vs Research.

### Linear Regression Insights

1. **Model Performance (Statsmodels)**:
   - **Training R²**: 0.826, **Adjusted R²**: 0.82
   - **Test R²**: 0.797, **Adjusted R²**: 0.779
   - **MAE**: 0.04, **MSE**: 0.003, **RMSE**: 0.059

2. **Assumptions of Linear Regression**:
   - **Linearity**: The target variable is linearly dependent on all features.
   - **No Multicollinearity**: VIF scores for all features are < 5, indicating no multicollinearity.
   - **Error Distribution**:
     - Errors are left-skewed and not normally distributed.
     - Minimal variance in high admission chances but high variance in low admission chances, suggesting the need for more data in the latter.
   - **Homoscedasticity**:
     - Initially appeared heteroscedastic but confirmed to be homoscedastic via the Goldfeld-Quandt test.

### sklearn Linear Regression Models

- **Linear Regression (without Regularization)**:
  - R²: 0.797, Adjusted R²: 0.781, MAE: 0.04, MSE: 0.003, RMSE: 0.059

- **Ridge Linear Regression (L2-Regularization)**:
  - Similar results to the non-regularized model, indicating minimal improvement with regularization.

- **Lasso Linear Regression (L1-Regularization)**:
  - Similar results to the non-regularized model, indicating minimal improvement with regularization.

### Conclusion
This analysis highlights the importance of GRE, TOEFL, CGPA, and research experience in predicting the chances of admission, with strong linear relationships and minimal multicollinearity present in the data.

---
# **Recommendations**

### 1. Focus on High-Impact Features
- **GRE Score, TOEFL Score, and CGPA**: These factors are highly correlated with the chance of admission. Encourage students to prioritize improving their scores in these areas as they significantly impact admission chances.
- **Research Experience**: Since applicants with research experience tend to have higher scores and better admission chances, Jamboree could emphasize the importance of research and potentially offer guidance or opportunities to help students gain research experience.

### 2. Tailored Student Support
- **Targeted Training for Lower-Scoring Students**: The analysis shows higher variance in admission chances among applicants with lower scores. Jamboree could develop specialized programs or resources aimed at boosting the GRE, TOEFL, and CGPA scores of these students, increasing their chances of admission.
- **Enhanced SOP and LOR Preparation**: Students with higher scores tend to have stronger SOPs and LORs. Jamboree could offer workshops or personalized coaching to help all students, especially those with lower scores, craft compelling SOPs and secure strong LORs.

### 3. Data-Driven Decision Making
- **Focus on Data Collection**: The analysis identified a need for more data, particularly for applicants with lower chances of admission. Jamboree should consider collecting more detailed data from these applicants to refine the predictive model and provide more accurate predictions.
- **Continuous Model Improvement**: Regularly update the predictive model as more data becomes available to ensure its accuracy and reliability. This will help keep the admission probability feature relevant and valuable to students.

### 4. Targeted University Applications
- **Strategic University Selection**: The analysis shows that students with higher scores tend to apply to higher-rated universities. Jamboree could offer tailored advice on university selection, guiding students to apply to institutions that match their profiles, thereby optimizing their chances of admission.