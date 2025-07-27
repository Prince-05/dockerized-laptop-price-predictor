# 🐳 Laptop Price Predictor — Fully Dockerized Streamlit App 💻💰

Predict laptop prices based on specifications using a **machine learning model** served via a **Dockerized Streamlit app**.  
No Python setup. No Jupyter nonsense. Just run the container and launch the UI in your browser — like a boss.
---

## 📌 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Dataset](#dataset)
- [Feature Engineering](#feature-engineering)
- [Model Comparison](#model-comparison)
- [Streamlit UI](#streamlit-ui)
- [Run with Docker](#run-with-docker)
- [Future Work](#future-work)
- [License](#license)

---

## 🧠 Overview

This project predicts the price of a laptop based on its specs (like brand, RAM, CPU, GPU, screen resolution, etc.) using ML regression models. The best-performing model is deployed behind a **Streamlit** interface that runs inside a **Docker container**.

---

## 🧰 Tech Stack

- Python 3.x
- Pandas, NumPy, Matplotlib, Seaborn
- Scikit-Learn (for modeling)
- Random Forest Regressor (final model)
- Streamlit (frontend UI)
- Docker (containerized app)

---

## 📂 Dataset

Cleaned and preprocessed dataset with the following relevant features:

- `Company`, `TypeName`
- `RAM`, `Weight`, `Touchscreen`, `IPS`
- `Screen Size`, `Resolution`, `PPI` (engineered)
- `CPU Brand`, `GPU Brand`, `HDD`, `SSD`
- `Operating System`
- 🎯 **Target Variable**: `Price`

---

## 🛠️ Feature Engineering

- Converted `Touchscreen` and `IPS` to binary
- Engineered `PPI` from resolution and screen size
- Extracted CPU/GPU brands
- One-hot encoded categorical features
- Outlier removal using percentiles

---

## 🤖 Model Comparison

| Model              | R² Score | MAE   | Notes                           |
|-------------------|----------|-------|---------------------------------|
| Linear Regression | 0.81     | ~2100 | Simple and interpretable        |
| Ridge Regression  | 0.83     | ~1950 | Reduced overfitting             |
| Lasso Regression  | 0.80     | ~2200 | Dropped some useful features    |
| Random Forest     | 0.87     | ~1700 | ✅ Best accuracy, deployed       |

The **Random Forest model** was selected for deployment due to superior performance on cross-validation.

---

## 🌐 Streamlit UI

The Streamlit app allows users to:

- Select brand, CPU, GPU, RAM, screen size, storage, etc.
- See predicted price instantly
- Use it from any browser without code

Sample UI:

```text
📊 Select your laptop specs
🔮 Click "Predict"
💰 See the estimated price
```

---

## 🐳 Run with Docker

No local setup required. Just pull and run:

### 1. Pull the image

```bash
docker pull prince050/laptop
```

### 2. Run the Streamlit app

```bash
docker run -p 8501:8501 prince050/laptop
```

### 3. Open in your browser:

```
http://localhost:8501
```

Streamlit will load the prediction interface automatically 🎉

---

## 🚀 Future Work

- Add support for custom resolution inputs
- Integrate deep learning models (EfficientNet for OCR specs? 👀)
- Add model explainability using SHAP/LIME
- Track metrics using MLFlow or Weights & Biases

---

## 📜 License

MIT License — free to use, modify, and deploy. But seriously, don’t try to sell it as your idea. That’s just rude 😤

---

## 🙌 Acknowledgments

- Inspired by real-world laptop specs scraping
- Modeled using Scikit-learn’s classic regression suite
- Deployed with Streamlit + Docker like a damn pro
