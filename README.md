# heart disease
# Heart Disease Prediction

A Flask web app that predicts whether a patient is likely to have heart disease based on health and lifestyle inputs, using a machine learning model trained on the Framingham Heart Study dataset.

## How it works

1. **Input** — the user fills out a form (`index.html`) with health details: sex, age, smoking status, cigarettes per day, blood pressure medication, history of stroke, hypertension, diabetes, total cholesterol, systolic/diastolic blood pressure, BMI, heart rate, and glucose.
2. **Encoding** — categorical fields (sex, smoker, medication, stroke, hypertension, diabetes) are converted to binary values.
3. **Scaling** — the numeric feature vector is scaled using a pre-fitted `scaler.pkl`.
4. **Prediction** — the scaled features are passed to a pre-trained classifier to predict heart disease risk (1 = disease, 0 = no disease).
5. **Result** — the prediction is rendered back on the page as a plain-language result.

## Tech stack

- **Flask** — web server and routing
- **scikit-learn** (pickled model + scaler) — prediction
- **NumPy** — feature array handling
- **HTML** (Jinja templates) — form and result display

## Project structure

```
heart_disease/
├── app.py                                  # Flask app: routes, encoding, prediction logic
├── main.py                                  # Model training / experimentation script
├── datasets_4123_6408_framingham.csv         # Framingham Heart Study dataset used for training
├── heart.pkl                                # Trained classifier
├── scaler.pkl                               # Fitted feature scaler
└── templates/
    └── index.html                           # Form + result page (rendered by app.py)
```

> **Heads up:** `app.py` currently loads a file named `model.pkl`, but the repo contains `heart.pkl` instead. You'll need to either rename `heart.pkl` to `model.pkl` or update the `pickle.load` call in `app.py` before running the app, or it will fail to start.

## Getting started

### Prerequisites

- Python 3.8+

### Installation

```bash
git clone https://github.com/archil-09/heart_disease.git
cd heart_disease
pip install flask scikit-learn numpy
```

(There's no `requirements.txt` in the repo yet — the above covers the imports used in `app.py`.)

### Running the app

```bash
python app.py
```

By default Flask runs in debug mode on `http://127.0.0.1:5000/`.

### Usage

1. Open the app in your browser.
2. Fill in the patient's health details in the form.
3. Submit to get a prediction: **"The Patient has Heart Disease"** or **"The Patient has No Heart Disease"**.

## Model input features

| Field | Type | Notes |
|---|---|---|
| Sex | categorical | "Male" / other |
| Age | numeric | years |
| Current smoker | categorical | Yes/No |
| Cigarettes per day | numeric | |
| On BP medication | categorical | Yes/No |
| History of stroke | categorical | Yes/No |
| Hypertension | categorical | Yes/No |
| Diabetes | categorical | Yes/No |
| Total cholesterol | numeric | mg/dL |
| Systolic BP | numeric | mmHg |
| Diastolic BP | numeric | mmHg |
| BMI | numeric | |
| Heart rate | numeric | bpm |
| Glucose | numeric | mg/dL |

## Disclaimer

This tool is for educational/demonstration purposes only and is **not a substitute for professional medical advice, diagnosis, or treatment**.

## License

No license specified. Add a `LICENSE` file if you intend to make usage terms explicit.
