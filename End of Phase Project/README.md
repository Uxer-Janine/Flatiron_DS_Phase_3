# Water Pump Functionality Prediction in Tanzania
![Water in an arid area](Images/view-fantasy-landscape-with-surreal-running-water-tap-world-water-day-awareness.jpg)
Author: **Janine Makorre**

## Project Overview
This project develops a logistic regression model to predict the functionality status of water pumps in Tanzania (functional, non-functional, or functional needs repair) using data from [Taarifa](https://taarifa.org/) and the [Tanzanian Ministry of Water](https://www.maji.go.tz/). The goal is to assist the Ministry in prioritizing pump maintenance to ensure clean water access, addressing Tanzania's water crisis.

## Business Problem
Tanzania faces a water crisis, with many of its 57 million residents lacking access to clean water despite numerous water points. The Ministry of Water struggles to identify which pumps are non-functional or likely to fail, hindering efficient maintenance. This project aims to predict pump functionality to optimize repair efforts and improve water access.

## Data
The dataset, sourced from the [Pump it Up: Data Mining the Water Table competition](https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/data/), includes:

- **Training Values:** 59,400 rows, 40 predictors (numerical and categorical, e.g., water_quality, construction_year).
- **Training Labels:** 59,400 rows with status_group (functional: 54.3%, non-functional: 38.4%, functional needs repair: 7.3%).
- **Test Values:** 14,850 rows, 40 predictors.Key features include water quantity, pump age, and permit status, processed to handle missing values, placeholders, and high cardinality.

## Classification
### Model
A logistic regression model was built with:

- **Preprocessing:** One-hot encoding for categorical features, standard scaling for numerical features, and SMOTE to address class imbalance.
- **Baseline Model:** Achieved ~70–75% test accuracy.
- **Tuned Model:** Optimized via grid search (best C ~0.1–1), slightly improving performance.

### Evaluation

Performance Metrics:
- **Test accuracy:** ~75%.
- **Non-functional pumps:** Moderate F1-score (~0.70), critical for maintenance prioritization.
- **Functional needs repair:** Low F1-score (~0.30–0.40) due to minority class.


### Key Visualizations:

1.**Pump Distribution by Functional Status**

![Pump Distribution by Functional Status](Images/Pump%20Distribution%20by%20Functional%20Status.png) 

- It shows functional pumps dominate (54.3%), with non-functional (38.4%) and functional needs repair (7.3%) less common.

2. **Effect of Water Quantity on Pump Functionality**
![Effect of Water Quantity on Pump Functionality](Images/Effect%20of%20water%20quantity%20in%20a%20well%20on%20the%20Pump's%20functionality%20status.png)

- It highlights that dry wells strongly correlate with non-functional pumps.

3. **Feature Importance**
![Feature Importance](Images/Top%2010%20Feature%20Importance%20Logistic%20Regression.png)

- Identifies quantity_group_dry, permit, and age as top predictors.


4. **Confusion Matrix**
![Confusion Matrix](Images/Confusion%20Matrix_Tuned%20Logistic%20Regression.png)

- Reveals misclassifications, particularly for the minority class (functional needs repair).

## Conclusion
The model achieves moderate success (~75% accuracy) in predicting pump functionality, with strong interpretability for stakeholder use. It effectively identifies non-functional pumps, aiding maintenance prioritization, but struggles with the minority class (functional needs repair).

## Limitations

1. **Class Imbalance:** The minority class (functional needs repair, 7.3%) limits model performance, even with SMOTE.
2. **Linear Assumptions:** Logistic regression assumes linear relationships, potentially missing complex patterns better captured by non-linear models (e.g., Random Forest).
3. **Data Quality:** High placeholder values (e.g., 70% zeros in amount_tsh) and missing data may reduce predictive power.
4. **Feature Limitations:** Some features (e.g., population) have limited variability, reducing their utility.

## Recommendations

1. **Prioritize Maintenance:** Focus on pumps in dry wells and those over 20 years old, as they are likely non-functional.
2. **Investigate Processes:** Examine permit and public meeting processes, which correlate with functionality.
3. **Explore Advanced Models:** Consider ensemble methods (e.g., Random Forest, Gradient Boosting) to improve performance on minority classes.
4. **Enhance Data Collection:** Improve data quality by reducing placeholders and capturing more granular data (e.g., maintenance history).

##  For More Information
See the full analysis in the [Jupyter Notebook](https://github.com/Uxer-Janine/Flatiron_DS_Phase_3/blob/main/End%20of%20Phase%20Project/index.ipynb) or review this [presentation]().

For additional info, contact [janinemakorre@gmail.com](janinemakorre@gmail.com).

## Repository Structure
├── Files
├──Images
├──index.ipynb
├──README.md
└──Presentation.pdf