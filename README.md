# Predicting Ozone Nonattainment in US Counties with Supervised Learning

**Course:** UE24CS352A — Machine Learning  
**Section:** 5E  
**Team:** 28

## Team Members
- Mueez Ahmed (PES2UG24CS286)
- Merwyn Prince Lobo (PES2UG24CS276)

## 1. Project Overview

This project uses supervised machine learning to classify US counties according to their ozone nonattainment status.

County-level features are derived from 2025 daily ozone measurements and combined with historical ozone status information from the US Environmental Protection Agency (EPA).

Three classification algorithms are evaluated: Logistic Regression, Decision Tree, and Random Forest.

## 2. Dataset

**Ozone measurements:** US EPA AirData, 2025  
**Ozone parameter code:** 44201  
**Status data:** US EPA Green Book historical county-status data  
**Unit of analysis:** US counties

Daily ozone measurements were aggregated at the county level and joined to status records using state and county FIPS codes.

The working dataset contains 755 county records:
- Class 0: 603 records
- Class 1: 152 records

Class 1 represents counties labelled as nonattainment under the project's target-construction procedure.

## 3. Features

The following county-level features were used:

- Number of daily ozone records
- Mean daily ozone concentration
- Maximum daily ozone concentration
- Mean daily Air Quality Index (AQI)
- Mean observation percentage

## 4. Machine Learning Models

The following supervised learning models were implemented:

1. Logistic Regression
2. Decision Tree
3. Random Forest

The models were compared using stratified five-fold cross-validation. Random Forest was also evaluated on an additional stratified test split.

## 5. Results

| Model / Evaluation | Accuracy | Precision | Recall | F1-score |
|---|---:|---:|---:|---:|
| Logistic Regression — 5-fold CV | 0.781 | 0.476 | 0.770 | 0.588 |
| Decision Tree — 5-fold CV | 0.818 | 0.554 | 0.533 | 0.542 |
| Random Forest — 5-fold CV | 0.871 | 0.737 | 0.566 | 0.638 |
| Random Forest — Additional Test Split | 0.801 | 0.500 | 0.533 | 0.520 |

Precision, recall, and F1-score refer to class 1 (nonattainment).

### Random Forest Confusion Matrix

The confusion matrix for the additional test split was:

    [[105, 16],
     [ 14, 16]]

The model achieved 80.1% accuracy and an F1-score of 0.520 for the nonattainment class.

## 6. Conclusion

Random Forest achieved the highest mean accuracy and F1-score in five-fold cross-validation. Logistic Regression achieved the highest recall for the nonattainment class.

The results indicate that the selected features contain patterns associated with the constructed nonattainment labels. However, identifying nonattainment counties remains challenging.

## 7. Limitations

- The experiment uses measurements and status labels from the same year; it does not forecast future nonattainment.
- County-level aggregation may conceal variation within counties.
- Results depend on the accuracy of the target-label construction.
- The additional test split was created after earlier model and threshold exploration and is not a fully untouched final test.

Future work could incorporate multiple years of measurements, verify the status labels, and evaluate predictions on a later held-out year.

## 8. Data Sources

- [US EPA AirData](https://aqs.epa.gov/aqsweb/airdata/download_files.html)
- [US EPA Green Book Data](https://www.epa.gov/green-book/green-book-data-download)

## 9. Project Report

The project report is available in:

[View the Project Report](Ozone_Nonattainment_ML_Report.pdf)

## 10. Project Files

The repository contains the source code, project report, and documentation required to understand and reproduce the project.

## Installation and Setup

Clone the repository:

```bash
git clone https://github.com/Mueez751/ozone-nonattainment-ml.git
cd ozone-nonattainment-ml

pip install -r requirements.txt
