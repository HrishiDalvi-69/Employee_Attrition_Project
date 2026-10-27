# Employee_Attrition_Project
## Project title
Machine Learning-Based Employee Attrition Prediction in Indian IT Companies

## Two operating modes

### Mode 1 — Existing Trained Model
Uses the supplied `data/Employee.csv` and the already trained best model. This mode is for predicting new individual employees when they have the same eight input features used during training.

### Mode 2 — New Dataset Training
Upload a different employee/HR CSV in Streamlit. Select the target column. The application automatically handles numerical/categorical preprocessing, trains Logistic Regression, Decision Tree, Random Forest and SVM, compares Accuracy/Precision/Recall/F1/ROC-AUC, and selects the best model.

The generic mode supports **binary classification** (exactly two target classes). It cannot reliably turn a completely unrelated CSV into an attrition problem; the user must select a meaningful target column and provide a suitable employee/HR dataset.

## Dataset used in the original mode
`data/Employee.csv` contains 4,653 rows and these features:
- Education
- JoiningYear
- City
- PaymentTier
- Age
- Gender
- EverBenched
- ExperienceInCurrentDomain
- LeaveOrNot (target)

## Original model result
The original dataset was evaluated with four models. The selected model is the Decision Tree based on F1 score, followed by Recall and ROC-AUC as tie-breakers.

## Run the project

python -m venv venv
venv\Scripts\activate
python -m pip install -r requirements.txt
python -m src.train
python -m streamlit run app.py



## Recommended demonstration
1. Open **Existing Trained Model** and demonstrate prediction using the original trained Decision Tree.
2. Switch to **New Dataset Training**.
3. Upload another suitable employee/HR CSV.
4. Select its binary target column.
5. Train and compare models.
6. Explain why the best model can change when the dataset changes.

## Important limitation
A trained ML model does not automatically work with arbitrary columns. A saved model expects the feature structure it was trained on. For a new dataset with a different feature structure, retraining is the correct approach.

## Academic and ethical note
This is an academic decision-support project. Predictions should not be used as the sole basis for employment, termination, compensation, or other high-impact decisions. Model outputs are statistical predictions, not causal explanations.

### Windows plotting note
The training script uses Matplotlib's non-GUI `Agg` backend, so `python -m src.train` can generate PNG reports without opening Tkinter windows. This prevents Tkinter `main thread is not in main loop` errors on Windows.
