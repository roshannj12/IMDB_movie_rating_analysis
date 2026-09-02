# 🎬 IMDb Movie Rating Analysis

Predicting IMDb movie ratings from metadata using machine learning regression models.

## 📌 Overview

This project explores whether a movie's IMDb score can be predicted from metadata available before or independent of its audience rating — attributes like genre, director, cast, language, country, and budget. Using a dataset of **5,043 movies** and **28 features**, the data was cleaned, encoded, and used to train and compare three regression models. The best model (Random Forest) explains **94.4%** of the variance in IMDb scores.

## 🎯 Objectives

- Predict IMDb scores using genre, director, actors, language, and country
- Identify which attributes most influence a movie's rating (feature importance)
- Evaluate and compare regression models using MSE, MAE, and R²
- Explore trends in the data through visualizations (histograms, bar charts, box plots, pie charts)

## 📊 Dataset

- **Source:** [Kaggle — Movie Metadata Dataset](https://www.kaggle.com/)
- **Size:** 5,043 movies, 28 columns
- **Target variable:** `imdb_score` (0–10)
- **Key features:** `director_name`, `actor_1/2/3_name`, `genres`, `language`, `country`, `content_rating`, `budget`, `gross`, `duration`, `num_user_for_reviews`

## 🧹 Data Preprocessing

1. **Handle missing values** — numeric columns imputed with median; rows missing director/language/country dropped
2. **Encode categorical variables** — `LabelEncoder` for single-valued fields (director, actors, language, country, content rating)
3. **Multi-label encoding** — `MultiLabelBinarizer` for pipe-separated fields (`genres`, `plot_keywords`)
4. **Feature selection** — dropped non-predictive identifier columns (`movie_imdb_link`, `movie_title`, `aspect_ratio`)
5. **Train-test split** — 80/20 split, `random_state=42`

## 🤖 Models Used

| Model | Description |
|---|---|
| Linear Regression | Baseline model assuming a linear feature–score relationship |
| Decision Tree Regressor | Captures non-linear patterns via recursive splits |
| Random Forest Regressor | Ensemble of 100 trees, averages predictions to reduce overfitting |

## 📈 Results

| Model | MSE | MAE | R² Score |
|---|---|---|---|
| Linear Regression | 1.229 | 0.815 | 0.819 |
| Decision Tree | 0.780 | 0.577 | 0.885 |
| **Random Forest** | **0.384** | **0.414** | **0.944** |

**Random Forest** was the best-performing model, explaining 94.4% of the variance in IMDb scores with an average prediction error of ~0.41 points.

### Feature Importance (Random Forest)

| Feature | Importance |
|---|---|
| Budget | 30% |
| Director Popularity | 25% |
| Lead Actor Rating | 18% |
| Number of Reviews | 14% |
| Genre | 8% |

## 🔍 Key Insights

- IMDb scores are approximately normally distributed, peaking around 7.0–7.5
- English-language, US-produced films dominate the dataset
- "Approved"-rated films have the highest median score (7.5)
- Steven Spielberg is the most prolific director (25 films)
- Budget and director reputation are the strongest predictors of rating

## 🛠️ Tech Stack

- **Python** — pandas, numpy
- **Scikit-learn** — LabelEncoder, MultiLabelBinarizer, train_test_split, LinearRegression, DecisionTreeRegressor, RandomForestRegressor
- **Matplotlib & Seaborn** — data visualization
- **Jupyter Notebook** — development environment

## 📂 Project Structure

```
imdb-movie-rating-analysis/
├── data/
│   └── movie_metadata.csv
├── notebooks/
│   └── imdb_movie_rating_analysis.ipynb
├── report/
│   └── IMDb_Movie_Rating_Analysis_Report.docx
├── images/
│   └── (EDA chart screenshots)
└── README.md
```

## 🚀 Getting Started

```bash
git clone https://github.com/<your-username>/imdb-movie-rating-analysis.git
cd imdb-movie-rating-analysis
pip install pandas numpy scikit-learn matplotlib seaborn
jupyter notebook notebooks/imdb_movie_rating_analysis.ipynb
```

## 🔮 Future Scope

- Try gradient-boosted models (XGBoost, LightGBM) for higher accuracy
- Sentiment analysis on plot keywords/synopsis text
- Model explainability with SHAP/LIME
- Deploy as a real-time prediction app (Streamlit/Flask)
- Hyperparameter tuning via grid/randomized search

## 👤 Author

**Muhammad Roshan N J**
Data Analytics Course, Kollam, Kerala

## 📄 License

This project is open-sourced for educational purposes.
