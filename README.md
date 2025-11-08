# 🏁 Formula 1 Race Predictions

This project predicts **Formula 1 race outcomes** (average lap times and finishing order) using **machine learning** trained on historical FastF1 data.

The model uses factors of each driver such as **qualifying lap time**, and **starting position** to estimate **finishing order** or **average race pace** — to derive the predicted results for upcoming Grands Prix.

---

## 📂 Contents

- `Formula 1 Race Predictions.ipynb` – main notebook with data loading, preprocessing, model training, and prediction.
- `f1_cache/` – FastF1 cache directory (automatically created).

---

## 🧠 Project Overview

### 1️⃣ Data Collection
Historical Formula 1 data (2022 – 2024) is retrieved using the [`FastF1`]([https://theoehrly.github.io/Fast-F1/](https://docs.fastf1.dev/)) library:
- Qualifying sessions → driver lap times (`Q1`, `Q2`, `Q3`)
- Race sessions → average lap times, total race times, grid positions

### 2️⃣ Feature Engineering
For each driver–year entry:
- `finalQualiLap(s)` = best valid qualifying lap
- `GridPosition` = starting grid position
- `Position` = qualifying position
- `AvgLapTime(s)` = mean race lap time (excluding DNFs)
- `TotalTime(s)` = absolute race duration derived from FastF1’s winner time + gaps

### 3️⃣ Modeling
A **gradient-boosted regression model** (XGBoost) predicts `Finishing Position` or `AvgLapTime(s)` from:
- `finalQualiLap(s)` = best valid qualifying lap
- `GridPosition` = starting grid position
- `Position` = qualifying position

## 🧩 Requirements
| Library | Purpose |
|----------|----------|
| `fastf1` | Retrieve F1 telemetry and timing data |
| `xgboost` | Machine-learning model |
| `pandas`, `numpy` | Data handling |
| `scikit-learn` | Preprocessing & cross-validation |

## 📊 Future Improvements
- Incorporate **Quali deltas** and **race deltas** instead of absolute lap times  
- Add **weather**, **temperature**, and **tire-compound** data for richer modeling  
- Train a **multi-track, multi-season generalized model** to predict any circuit  
- Include **DNFs**, **safety-car periods**, and **pit-stop timing** adjustments  
- Explore driver/team performance trends over multiple seasons  

---

### 🏎️ “Speed meets data.”  
*Predicting performance one lap at a time.*
