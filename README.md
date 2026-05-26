# 📈 Multi-Asset Risk Monitoring System

An interactive, web-based dashboard designed to analyze volatility dynamics, evaluate the leverage effect, and quantify downside risk across multiple assets using over **2,500+ daily observations**.

---

## 🔍 Overview & Capabilities

- **Downside Risk Assessment**: Built-in 95% Value-at-Risk (VaR) forecasting.
- **Asymmetric Leverage Effects**: Analyzes how negative market shocks impact volatility differently than positive ones.
- **Interactive Dashboard**: A clean, modern Streamlit user interface featuring dynamic visualizations of volatility dynamics, model parameters, and risk metrics.
- **Robust Statistical Validation**: Features backtesting and statistical testing of risk model accuracy.

---

## 🧪 Econometric Modeling & Methodology

The core of the system comprises three volatility models, estimated via **Gaussian Maximum Likelihood Estimation (MLE)**:

1. **ARIMA-GARCH**: Captures linear dependencies in the mean equation and symmetric volatility clusters in the conditional variance.
2. **GJR-GARCH (Glosten-Jagannathan-Runkle GARCH)**: Captures asymmetric responses of volatility to positive and negative shocks.
3. **EGARCH (Exponential GARCH)**: Models log-variance directly, ensuring positive variance and capturing exponential asymmetry.

### 📊 Validation & Backtesting
* **95% VaR Backtesting**: Historical returns are compared against the modeled VaR threshold.
* **Kupiec POF (Proportion of Failure) Test**: Formally tests whether the number of VaR exceptions aligns with the theoretical 5% significance level.
* **Model Selection**: The **EGARCH** model was identified as the superior model for capturing asymmetric volatility, especially during periods of high market stress.

### 💡 Key Finding
* **News Impact Curves (NIC)**: Showed a **1.7x variance response to negative shocks** compared to positive shocks of the same magnitude, proving the existence of a strong asymmetric leverage effect in the analyzed assets.

---

## 🛠️ Tech Stack

- **Language**: Python
- **Data Wrangling & Analysis**: NumPy, Pandas
- **Econometric Modeling**: `statsmodels`, `scipy`, `arch`
- **Visualization**: Matplotlib, Plotly
- **Web Dashboard**: Streamlit

---

## 🚀 Getting Started

### Prerequisites
Make sure you have Python 3.8+ installed.

### 1. Install Dependencies
Install the required packages from the project root directory:
```bash
pip install -r requirements.txt
```

### 2. Run the Streamlit Dashboard
Execute the application:
```bash
streamlit run streamlit_app.py
```

### 3. Using the Dashboard
Once the app launches in your browser, you can:
- **Upload Data**: Load the provided `SP500_2016-2026.csv` or `Gold_2016-2026.csv` datasets.
- **Select Models**: Estimate GARCH, GJR-GARCH, or EGARCH models on the fly.
- **Technical Details (Nerd Mode)**: Toggle this option to view underlying LaTeX equations for the models and the Kupiec Test.
