# Student Performance Prediction System

A classroom prototype that estimates whether a student is at risk of failing the final grade, built for a Data Mining laboratory exercise.

## Problem
Academic risk is often noticed only after poor results. This prototype explores early identification of students who may need additional academic support, using indicators such as study time, absences, past failures, and the period grades G1 and G2.

## Dataset
UCI Machine Learning Repository, *Student Performance* (ID 320):
https://archive.ics.uci.edu/dataset/320/student+performance

The data is downloaded automatically by `train_model.py` through the `ucimlrepo` package and saved as `student_data.csv`.

## Prediction target
- `G3 < 10` → **AT RISK** (1)
- `G3 >= 10` → **NOT AT RISK** (0)

`G3` is used only to derive the target and is **never** an input feature (avoids target leakage).

## Technologies
Python 3.10+, pandas, scikit-learn (Random Forest), joblib, Streamlit, Git/GitHub.

## Installation and run
```bash
pip install -r requirements.txt
python train_model.py      # downloads data, trains, evaluates, saves student_model.pkl
streamlit run app.py       # opens http://localhost:8501
```
In the app, download the sample input CSV, then upload it to see predictions. Results can be downloaded as CSV.

## Project structure
```
student-performance-prediction/
├── train_model.py
├── app.py
├── requirements.txt
└── README.md
```

## Limitations
- Trained on one Portuguese secondary-school dataset; it may not generalize to other institutions or populations.
- Using G1 and G2 makes prediction easier but later in the term; see the optional extension that removes them.
- Predictions are not diagnoses and must not be the sole basis for real student decisions. Use them only to prompt a human conversation and support.
