# 🎬 Predicting IMDb Scores: Leveraging Pre-Release Movie Attributes

A machine learning framework to predict IMDb ratings using only pre-release movie data. Built using advanced regression and classification models, enriched with GPT-based interpretability to assist filmmakers with actionable insights.

---

---

- **Project Collaborators**: Jaswanth Kranthi Boppana, Vishnuvardhan Reddy Kollu, Vineela Kunisetti


---

## 📌 Project Overview

### 🎯 Purpose

This project forecasts IMDb scores using features available before a movie’s release—like director reputation, social media engagement, and genre—using regression and classification models. Results are further interpreted using GPT to provide filmmakers with human-readable recommendations for improving their film’s reception.

---

## 📂 Dataset

- **Source**: IMDb 5000 Movie Dataset
- **Records**: 5,043 movies across 100+ years and 66 countries
- **Features**: 27 predictors including genre, director, actors, budget, gross earnings, reviews, Facebook likes
- **Target Variable**: `imdb_score`

Key engineered features include:
- `Directors Avg_IMDb`: Aggregated IMDb score of past movies by a director
- `Expected Engagement`: Weighted metric derived from user and critic review counts

---

## 🔍 Data Preprocessing & Feature Engineering

- Removed or imputed missing values (e.g., facenumber_in_poster, content_rating)
- One-hot encoding for categorical variables; target encoding for high-cardinality features
- Outlier removal using Z-score
- Standardization with `StandardScaler` for numerical features
- Simplified multi-level categories like country

---

## 📊 Exploratory Data Analysis

Insights from EDA:
- USA dominates movie production (~79%)
- Strong correlation between user engagement and IMDb scores
- Notable financial success exists even among lower-rated movies
- Social media engagement aligns with higher scores, especially for PG-13 and R-rated films

---

## ⚙️ Methodology

### 📈 Regression Models
Used to predict continuous IMDb scores:
- **LightGBM** (Best: R² = 0.7557, MAE = 0.355)
- **XGBoost** (R² = 0.7531)
- **Gradient Boosting** (R² = 0.7516)
- **Random Forest** (R² = 0.7148)
- **Linear Regression** (Baseline, R² = 0.6807)

### 🎯 Classification Models
IMDb scores categorized into 4 classes:
- Poor (0–4)
- Average (4–6)
- Good (6–8)
- Excellent (8–10)

Models used:
- **LightGBM** (Best: Accuracy = 84.5%, F1 = 0.841)
- **Gradient Boosting** (Accuracy = 83.9%)
- **Random Forest** (Accuracy = 81.7%)

Class imbalance addressed via stratified sampling.

---

## 🤖 GPT Integration

We integrated OpenAI GPT API to translate model-driven feature importances into user-friendly suggestions. This bridge between data science and creative strategy allows filmmakers to understand *why* a movie might succeed or fail and what changes could help.

Sample output:
> “Consider increasing social media engagement, especially on Facebook for your lead actor. Historically, higher actor_facebook_likes correlate with top-rated movies in your genre.”

---

## 📈 Results

### ✅ Regression Summary
| Model            | R² Score | MAE   | RMSE  |
|------------------|----------|-------|--------|
| LightGBM         | 0.7557   | 0.355 | 0.488  |
| XGBoost          | 0.7531   | ~     | ~      |
| Gradient Boosting| 0.7516   | ~     | ~      |
| Random Forest    | 0.7148   | ~     | ~      |
| Linear Regression| 0.6807   | ~     | ~      |

### ✅ Classification Summary
| Model            | Accuracy | F1 Score |
|------------------|----------|----------|
| LightGBM         | 84.5%    | 0.841    |
| Gradient Boosting| 83.9%    | 0.836    |
| Random Forest    | 81.7%    | 0.799    |

---

## 🧩 Challenges & Solutions

- **Challenge**: Class imbalance in IMDb categories  
  **Solution**: Stratified sampling to preserve proportions

- **Challenge**: High-cardinality features like director/actor names  
  **Solution**: Aggregated historical averages (e.g., Director Avg IMDb)

- **Challenge**: Missing data in `budget`, `gross`  
  **Solution**: Row removal for critical features; imputation for less critical ones

---

## 🧠 Conclusion

This project provides a powerful framework for predicting IMDb scores using only pre-release data. The LightGBM model demonstrated the best performance in both regression and classification tasks. GPT integration enhances interpretability, empowering filmmakers to optimize strategies before release.

---

## 🔮 Future Scope

- Incorporate additional features like trailer view counts, sentiment from social media, and media coverage
- Extend predictions to box office revenue, ROI, and other commercial metrics
- Apply framework to web series, video games, or global TV shows



---

