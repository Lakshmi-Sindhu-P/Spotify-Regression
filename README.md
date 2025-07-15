# 🎧 Regression Analysis on Spotify Song Attributes

**Course:** MATH564  
**Contributors:** Lakshmi Sindhu Pulugundla, Lasya Priya Thota, Kaustubh Dangche

---

## 📌 Problem Statement

This project aims to identify key audio features and metadata that significantly influence the total playback time (`msPlayed`) of songs on Spotify. We build a regression model using both continuous and categorical attributes to better understand user engagement patterns with music.

---

## 📁 Dataset Overview

- **Source:** Spotify Song Attributes  
- **Total Records:** 10,080  
- **Response Variable:** `msPlayed` (playback time in milliseconds)  
- **Predictors:**
  - **Continuous:** `danceability`, `energy`, `tempo`
  - **Categorical:** `genre`, `artistName`

---

## 🧭 Project Workflow

### 1. Data Preparation & Cleaning
- **Handled Missing Values:**  
  - Applied **KNN Imputation** (k = 5) on `danceability`, `energy`, and `tempo`
- **Categorical Cleaning:**  
  - Standardized `genre` and `artistName` by:
    - Lowercasing
    - Removing whitespace
    - Mapping rare values to `"Other"`
- **Outlier Treatment:**  
  - Applied **IQR-based capping** to continuous variables
- **Normalization:**  
  - Scaled `danceability`, `energy`, and `tempo` between 0 and 1 using Min-Max normalization

### 2. Feature Engineering
- Created dummy variables for categorical columns
- Retained `trackName` for traceability
- Stored imputation flags for regression transparency

---

## 📊 Exploratory Data Analysis (EDA)

### 3.1 Continuous Variable Distributions

| Variable       | Distribution Observation                       |
|----------------|------------------------------------------------|
| `msPlayed`     | Right-skewed, large number of short-played tracks |
| `danceability` | Balanced after normalization                  |
| `energy`       | Balanced with slight left skew                |
| `tempo`        | Normalized and centered                        |

<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/d4e9472b-85bc-40b2-9bae-4ac45553083c" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/7e8fa361-aaa6-40e5-bdd1-597831d8254f" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/85ff901c-970f-4f52-9601-a6d46f29287b" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/eefda1d6-3560-4a68-bab2-73faa3a52790" />

---

### 3.2 Categorical Variable Distributions

- **Genres**: Pop, Phonk, Alternative, and Bollywood were dominant
- **Artists**: blackbear, Lauv, and Linkin Park were top contributors

<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/1e2fa0a1-8125-45ff-80b3-4367ab148e83" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/957a6ff3-cb76-41b2-a0f2-11d5828e3a49" />

Filtered `"Other"` category for focused analysis.

---

### 3.3 Correlation Analysis

- Low correlation between `msPlayed` and continuous features.
- Moderate correlation between `danceability` and `energy`.

<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/c4c52e7d-0d40-4f35-b7c6-f6f6ca8175c0" />

---

### 3.4 Playback Time Analysis by Categorical Variables

Boxplots showed:
- Variability across **genres** (metal/pop had high spread)
- High playback time outliers for artists like **Low Roar**

<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/be150820-eb04-4354-82f4-1a47fe426eb5" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/9dabff57-e530-4af7-b873-326c4a74b230" />

---

### 3.5 Bivariate Analysis: Continuous vs Playback

- No strong linear relationships were found.
- Visualized scatter plots for:
  - `danceability` vs `msPlayed`
  - `energy` vs `msPlayed`
  - `tempo` vs `msPlayed`

<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/05aaf803-7703-49ca-847e-0e945f45bc47" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/4220f5fb-2e5e-4c55-abe4-54c9f8e2bf51" />
<img width="1280" height="880" alt="image" src="https://github.com/user-attachments/assets/c8bdb1df-e3ab-40cb-b7af-af532c851553" />

---

## 🧮 Regression Modeling

### Model Type:
**Multiple Linear Regression**  
```R
lm(msPlayed ~ danceability + energy + tempo + genre + artistName, data = dataset)
```

### Model Summary:

* **R² = 0.0841**, Adjusted R² = 0.04247
* Genres like **Asian Pop, Chill Pop, EDM** were significant
* Artists like **Alan Walker, DJ Snake** had impactful coefficients
* Continuous predictors were mostly insignificant

---

## ✅ Interpretation & Limitations

### Key Learnings:

* **Categorical variables** had more influence than continuous ones
* **Playback behavior** is complex and driven by external factors beyond song attributes (e.g., listener context, playlist placement)

### Limitations:

* Low R² suggests a limited fit for linear regression
* `"Other"` grouping reduced feature specificity
* Further improvements possible via non-linear modeling (Random Forests, Gradient Boosting)

---

## 🔮 Future Work

* Explore **interaction terms** or **polynomial regression**
* Apply **tree-based models** to capture non-linearity
* Expand dataset with listener-specific behavior for personalization modeling

---

## 💾 Output

A cleaned and reduced dataset was saved for model building:

```bash
spotify_analysis_data.csv
```

---

## 📎 References

* Spotify Developer API
* DataCamp: Regression Analysis in R
* Project PDF Report: [Spotify-Regression-Analysis.pdf](./Spotify-Regression-Analysis.pdf)

---

## 👥 Contributors

* **Lakshmi Sindhu Pulugundla**
* **Lasya Priya Thota**
* **Kaustubh Dangche**

---

