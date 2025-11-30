# Predict-Student-Dropout-XGBoost-and-Neural-Networks

## Project Background

This project applies supervised learning techniques to predict student dropout risk across three stages of the student journey:

1. **Stage 1 – Early:** Applicant and course information  
2. **Stage 2 – Mid:** Student engagement and attendance behaviour  
3. **Stage 3 – Late:** Academic performance metrics  

Student retention is critical for institutional financial stability, academic outcomes, and overall student satisfaction. Predicting dropout risk allows targeted interventions at different stages, optimising resource allocation and maximising retention.

The analysis leverages both **XGBoost** and **Neural Network** models to evaluate predictive performance at each stage, highlighting how feature availability affects model accuracy, precision, and recall.

---

## Objective

- Explore student datasets across three stages  
- Preprocess and engineer features, including demographic, behavioural, and academic performance data  
- Predict dropout using XGBoost and Neural Networks  
- Optimise models via hyperparameter tuning for maximum F1 score  
- Compare models and stages to determine best strategies for intervention  

---

## Data Overview

- **Stage 1:** Demographics, course, and institutional features (25,059 rows, 16 columns)  
- **Stage 2:** Adds attendance behaviour features (Authorised and Unauthorised Absences)  
- **Stage 3:** Adds academic performance features (Assessed, Passed, Failed Modules)  

Data preprocessing included:
- Dropping identifiers and columns with >50% missing values  
- Converting dates to age  
- Binary, ordinal, and one-hot encoding  
- Mean imputation for missing performance metrics  

---

## Recommendations

- **Stage 1 – Early Intervention:** Use NN1 predictions to flag potential at-risk students based on demographic and course information. Focus on broad preventative measures such as orientation support, engagement campaigns, and monitoring attendance trends.  

- **Stage 2 – Mid-Course Intervention:** Combine NN2 and XGB2 outputs to balance recall and precision. Target students showing early signs of disengagement or attendance issues with personalised outreach, mentoring, and academic support.  

- **Stage 3 – Late-Stage Intervention:** Prioritise XGB3 predictions for high-confidence identification of students at immediate risk. Implement intensive retention efforts, such as one-on-one tutoring, academic counselling, and tailored support plans.  

- **Feature-Based Strategies:**  
  - Track attendance and absence patterns closely to identify early risk indicators.  
  - Monitor academic performance metrics (Assessed, Passed, Failed Modules) to inform targeted interventions.  
  - Use insights from demographic and institutional features to tailor support programmes to different student groups.  

- **Operational Actions:**  
  - Allocate resources dynamically based on predicted risk stage.  
  - Develop automated dashboards to monitor dropout risk in real time.  
  - Regularly retrain models with new student data to maintain predictive accuracy.  
  - Coordinate cross-departmental intervention strategies involving faculty, tutors, and student support services.  

- **Policy Recommendations:**  
  - Establish early-warning protocols for students flagged at each stage.  
  - Invest in engagement initiatives during the first weeks of the course to reduce early-stage dropout risk.  
  - Implement targeted support for students struggling academically in late-stage courses.  
  - Review and refine institutional and course-level policies that influence student retention.
 
---

## Model Summary

### Stage 1 – Early Risk

**Neural Network (NN1)**  
- F1 improved from 0.567 → 0.636  
- Recall: 0.498 → 0.691 (aggressive detection)  
- Precision: 0.658 → 0.590  

**XGBoost (XGB1)**  
- Initial F1 = 0; Optimised F1 = 0.610  
- Recall: 0.549, Precision: 0.687  
- Feature importance dominated by nationality and centre-related features  

**Insight:** Early intervention prioritises recall; NN1 better flags at-risk students, XGB1 reduces false positives.

---

### Stage 2 – Mid-Course Risk

**Neural Network (NN2)**  
- F1: 0.599 → 0.663  
- Recall: 0.500 → 0.670  
- Precision: 0.746 → 0.657  

**XGBoost (XGB2)**  
- F1: 0 → 0.665  
- Recall: 0.598, Precision: 0.749  
- Institutional and course features gain predictive weight  

**Insight:** Mid-course prediction balances recall and precision; NN2 detects slightly more potential dropouts, XGB2 is more precise, reducing unnecessary interventions.

---

### Stage 3 – Late-Stage Risk

**Neural Network (NN3)**  
- F1: 0.787 → 0.866  
- Recall: 0.742 → 0.809  
- Precision: 0.838 → 0.931  

**XGBoost (XGB3)**  
- F1: 0 → 0.921  
- Recall: 0.909, Precision: 0.934  
- Academic performance features dominate feature importance  

**Insight:** Late-stage prediction requires high precision and recall. XGB3 offers the most reliable predictions for targeted retention efforts.

---

## Cross-Stage Analysis

- Predictive performance improves as more features become available.  
- Feature importance shifts: demographics → institutional/course context → academic performance.  
- Early-stage interventions must accept some false positives; mid-stage allows selective targeting; late-stage focuses on high-certainty cases.  

**Model Selection Guidance:**  
- **Stage 1:** Prioritise NN for recall  
- **Stage 2:** Trade-off between NN recall and XGB precision  
- **Stage 3:** XGB dominates for high-confidence retention targeting  

---

## Key Takeaways

- Optimisation consistently improved F1 scores, balancing recall and precision per stage  
- Absence and academic performance features provide strong predictive signals  
- Neural Networks and XGBoost each have advantages depending on stage and intervention goals  
- Feature evolution reflects real-world information availability and guides stage-specific strategies  

---
