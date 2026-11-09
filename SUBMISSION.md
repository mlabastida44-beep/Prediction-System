# Student Performance Prediction System: Laboratory Submission

## 1. SAD mini-analysis

| SAD element | Response |
|---|---|
| Problem statement | Academic risk is often noticed only after poor results. This prototype explores early identification of students at risk of failing the final Mathematics grade, using available student indicators. |
| Users | Faculty member or academic analyst. |
| Inputs | Student attributes and academic indicators (study time, absences, past failures, G1, G2, and demographic/social fields) supplied as a CSV file. |
| Process | Validate required columns → preprocess (impute, scale, encode) → apply trained Random Forest model → classify risk (G3 < 10). |
| Outputs | AT RISK / NOT AT RISK label per student, a count of predicted at-risk records, a downloadable results CSV, and a model evaluation summary. |
| Key limitation | A model trained on one Portuguese secondary-school dataset may not generalize to another institution or population. |

Use case: the user uploads a CSV → the system checks required columns → the model predicts risk → the system displays and exports the results.

## 2. Model evaluation results (fill in after `python train_model.py`)

Test split: 20%, `random_state=42`, stratified. Model: Random Forest (100 trees, balanced class weights).

| Metric | Not at risk | At risk |
|---|---|---|
| Precision | ___ | ___ |
| Recall | ___ | ___ |
| F1-score | ___ | ___ |

Overall accuracy: ___

Do not interpret accuracy alone: look at recall for the "At risk" class.

## 3. Testing evidence

| Test | Expected result | Pass? |
|---|---|---|
| Run train_model.py | CSV and model files are created without errors. | ☐ |
| Run Streamlit app | Dashboard loads in browser. | ☐ |
| Upload sample CSV | Predictions are displayed. | ☐ |
| Upload CSV missing a required column | The app displays a helpful error message. | ☐ |
| Download results | A CSV containing predictions is downloaded. | ☐ |
| Open GitHub repository | Source files and README are visible. | ☐ |

## 4. Reflection answers

1. **Prediction target and why G3 is excluded.** The target is whether a student is at risk: 1 if the final grade G3 is below 10, otherwise 0. G3 is excluded from the features because the target is computed directly from it. Including it would leak the answer to the model, giving unrealistically high accuracy and a model that could not be used before final grades exist.

2. **Recall for the "At risk" class.** It is the share of students who truly ended up at risk that the model correctly flagged. High recall means few at-risk students are missed; low recall means many are overlooked, even if overall accuracy looks good. For a support-oriented tool, missed students are the costly error.

3. **Why performance may differ at your institution.** The data comes from two Portuguese secondary schools. Grading scales, curricula, teaching practices, student demographics, and social context can differ, so the relationships the model learned (for example between absences, failures, and grades) may not hold. The data is also small and historical, so the model should be re-validated or retrained on local data.

4. **Action after an "AT RISK" prediction.** Treat it as a prompt for human follow-up, not a verdict. The faculty member should review the student's actual records, talk with the student, and offer support such as tutoring or counseling. The prediction should never be the sole basis for a decision about the student.

## 5. Submission checklist

1. ☑ SAD mini-analysis (section 1)
2. ☑ train_model.py and app.py
3. ☑ requirements.txt and README.md
4. ☐ Model evaluation results (fill in section 2 after training)
5. ☐ Screenshot of the Streamlit dashboard and prediction results
6. ☐ GitHub repository URL: ______________________
