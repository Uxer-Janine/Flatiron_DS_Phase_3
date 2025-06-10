Water Pump Functionality Prediction in Tanzania
Project Overview
This project develops a logistic regression model to predict the functionality status of water pumps in Tanzania (functional, non-functional, or functional needs repair) using data from Taarifa and the Tanzanian Ministry of Water. The goal is to assist the Ministry in prioritizing pump maintenance to ensure clean water access, addressing Tanzania's water crisis.
Business Problem
Tanzania faces a water crisis, with many of its 57 million residents lacking access to clean water despite numerous water points. The Ministry of Water struggles to identify which pumps are non-functional or likely to fail, hindering efficient maintenance. This project aims to predict pump functionality to optimize repair efforts and improve water access.
Data
The dataset, sourced from the Pump it Up: Data Mining the Water Table competition, includes:

Training Values: 59,400 rows, 40 predictors (numerical and categorical, e.g., water_quality, construction_year).
Training Labels: 59,400 rows with status_group (functional: 54.3%, non-functional: 38.4%, functional needs repair: 7.3%).
Test Values: 14,850 rows, 40 predictors.Key features include water quantity, pump age, and permit status, processed to handle missing values, placeholders, and high cardinality.

Classification
Model
A logistic regression model was built with:

Preprocessing: One-hot encoding for categorical features, standard scaling for numerical features, and SMOTE to address class imbalance.
Baseline Model: Achieved ~70–75% test accuracy.
Tuned Model: Optimized via grid search (best C ~0.1–1), slightly improving performance.

Evaluation

Performance Metrics:
Test accuracy: ~75%.
Non-functional pumps: Moderate F1-score (~0.70), critical for maintenance prioritization.
Functional needs repair: Low F1-score (~0.30–0.40) due to minority class.


Key Visualizations:
Pump Distribution by Functional Status (Images/Pump Distribution by Functional Status.png): Shows functional pumps dominate (54.3%), with non-functional (38.4%) and functional needs repair (7.3%) less common.
Effect of Water Quantity on Pump Functionality (Images/Effect of water quantity in a well on the Pump's functionality status.png): Highlights that dry wells strongly correlate with non-functional pumps.
Feature Importance (Images/Top 10 Feature Importance: Logistic Regression.png): Identifies quantity_group_dry, permit, and age as top predictors.


Confusion Matrix (Images/Confusion Matrix_Tuned Logistic Regression.png): Reveals misclassifications, particularly for the minority class (functional needs repair).

Conclusion
The model achieves moderate success (~75% accuracy) in predicting pump functionality, with strong interpretability for stakeholder use. It effectively identifies non-functional pumps, aiding maintenance prioritization, but struggles with the minority class (functional needs repair).
Limitations

Class Imbalance: The minority class (functional needs repair, 7.3%) limits model performance, even with SMOTE.
Linear Assumptions: Logistic regression assumes linear relationships, potentially missing complex patterns better captured by non-linear models (e.g., Random Forest).
Data Quality: High placeholder values (e.g., 70% zeros in amount_tsh) and missing data may reduce predictive power.
Feature Limitations: Some features (e.g., population) have limited variability, reducing their utility.

Recommendations

Prioritize Maintenance: Focus on pumps in dry wells and those over 20 years old, as they are likely non-functional.
Investigate Processes: Examine permit and public meeting processes, which correlate with functionality.
Explore Advanced Models: Consider ensemble methods (e.g., Random Forest, Gradient Boosting) to improve performance on minority classes.
Enhance Data Collection: Improve data quality by reducing placeholders and capturing more granular data (e.g., maintenance history).

