# 🎧 Regression Analysis on Spotify Song Attributes

**Course:** MATH564  

---

## 📌 Problem Statement

This project investigates which audio features and metadata influence a listener’s engagement with songs, measured by `msPlayed` (milliseconds played). Using multiple regression analysis, we aim to predict playback time and uncover meaningful patterns across genres and artists.

---

## 📁 Dataset Overview

- **Source:** Spotify Song Attributes  
- **Total Records:** 10,080  
- **Response Variable:** `msPlayed`  
- **Predictors:**
  - 🎵 Continuous: `danceability`, `energy`, `tempo`  
  - 🎤 Categorical: `genre`, `artistName`

---

## 🧹 Data Preparation & Cleaning

- ✨ **Imputation:** KNN (k=5) for missing values in numerical features  
- 🎯 **Categorical Handling:** Cleaned `genre` and `artistName`, grouped rare levels into `"Other"`  
- 🧮 **Outlier Treatment:** IQR capping applied  
- 📏 **Normalization:** Min-Max scaling on continuous variables  
- 🗂️ **Encoding:** Dummy variables for categorical columns  

---

## 📊 Exploratory Data Analysis (EDA)

### 🎼 Continuous Variables
- `msPlayed` was right-skewed  
- `danceability`, `energy`, and `tempo` became well-centered after normalization  

### 📚 Categorical Distribution
- Dominant genres: Pop, Alternative, Bollywood, Phonk  
- Top artists: blackbear, Lauv, Linkin Park  
- `"Other"` category helped reduce noise from rare entries

### 💫 Bivariate Analysis
- No clear linear relationships between playback time and features like tempo or energy  
- Notable artist outliers: Low Roar, Radwimps  
- Genre variability: Metal and Pop showed higher spread

---

## 🧮 Regression Modeling

### 🔧 Initial Model
```R
lm(msPlayed ~ danceability + energy + tempo + genre + artistName, data = dataset)
```

* 📉 **Adjusted R²:** 0.0425
* ⭐ Significant predictors: `artistNameAlan Walker`, `genreEDM`, `artistNameDJ Snake`
* 🚫 Many aliased coefficients due to high dimensionality

---

## 🔍 Model Diagnostics

### ✅ Assumption Checks

* ✔️ **Homoscedasticity:** Passed (Breusch-Pagan p > 0.05)
* ⚠️ **Multicollinearity:** Resolved by grouping rare categories
* 🧨 **Influential Points:** Identified using Cook’s Distance and Leverage

---

## 🧪 Remediation Phase

### 🔁 Log Transformation

* 📈 Log-transformed `msPlayed` improved normality and variance stabilization
* 💡 Adjusted R² increased to **0.2627**

### 🧹 Influential Points Removed

* 📉 Final Residual Standard Error: **1.45**
* ✅ Adjusted R²: **0.3687**
* 🎯 Significant predictors now included:

  * `danceability`
  * `genreasian pop`, `genrebaroque pop`
  * `artistNameAnson Seabra`, `artistNameHans Zimmer`

---

## 🧠 Insights & Interpretations

* 🎵 Categorical variables (genre, artistName) influenced playback more than continuous ones
* 🎧 Listener behavior is nuanced—playback is affected by factors beyond audio features
* 🔍 Linear models help, but they don’t fully capture the complexity of music engagement

---

## ❌ Limitations

* 🧪 63% variance in playback time remains unexplained
* 🎙️ Artist & genre categories still carry high dimensionality
* 💭 User context, playlist type, or mood could be critical missing factors

---

## 🔮 Future Work

* 🌳 Use **tree-based models** (Random Forest, XGBoost) for non-linear insights
* ✂️ Apply **LASSO/Ridge regression** for smarter feature selection
* 🧬 Add user-specific data (e.g., time of day, playlists, skip behavior)
* 🌀 Explore **interaction effects** between predictors
* 🔬 Genre-specific deep dives with clustering

---

## 💾 Output Dataset

Final cleaned dataset for modeling:

```bash
spotify_analysis_data
```

---

## 📎 References

* 📄 Project Report: [Spotify-Regression-Analysis.pdf](./Spotify-Regression-Analysis.pdf)

---


