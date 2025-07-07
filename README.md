# 🚢 Detecting Fishing Activity from Vessel Tracking Data

This project is a complete machine learning pipeline designed to detect and classify **fishing activity** from vessel movement data, using **AIS (Automatic Identification System)** records. It automatically identifies **when** and **where** vessels are likely engaged in fishing and distinguishes between gear types such as **longliners**, **trawlers**, and **purse seiners**.

---

## 🧠 Project Overview

This system leverages AIS trajectory data and supervised learning models to analyze fishing behaviors. It includes:
- Preprocessing of vessel movement data
- Feature extraction
- Model training with hyperparameter tuning
- Result evaluation and visualization with geospatial mapping

---

## 📁 Key Components

### 1. **Data**
**Location:** `data/` and `training-data/data/`  
**Contents:**
- Labeled vessel tracks (`.npz`) with extracted features and fishing labels.
- Features computed over various time windows (e.g., 1800s, 3600s).
- Grouped datasets by gear type: `longliners`, `trawlers`, `purse_seiners`, etc.
- Metadata: vessel MMSI lists, time ranges, false positives dataset.

---

### 2. **Source Code**
**Location:** `src/` and `src/utils/`

#### 🔧 Main Scripts:
- `grid_search_multicolumns.py` – Trains Random Forest / Gradient Boosting models with grid search.
- `results_analysis.py` – Evaluates models, computes metrics (accuracy, recall, F1-score), and generates plots.
- `reconstructing_tracks.py` – Reconstructs vessel tracks and overlays true vs predicted fishing activity on a map.

#### 🧰 Utilities:
- `pipeline_noLatLon.py` & `utilities.py` – Handle data loading, feature selection, splitting, and support functions.

---

### 3. **Models & Results**
**Location:** `results/`  
**Contents:**
- Trained models (`.pkl`)
- Evaluation summaries (`.txt`)
- Visual outputs: maps, graphs, and performance metrics

Each output image includes:
- A **super-title** with gear type, model type, and vessel MMSI
- Two panels: **actual fishing** vs **predicted fishing**
- Clear map features (coastlines, country borders, meridians/parallels)

---

### 4. **Documentation**
- `README.md` – Overview and usage instructions
- `AWS_setup.md` – Guide for cloud deployment (if applicable)
- `slides/` – PDF presentation about the project pipeline and findings

---

## ⚙️ How It Works

### 1. **Data Preparation**
- Load and clean AIS data with fishing labels
- Extract features over different time windows
- Group by vessel type and gear category

### 2. **Model Training**
- Split data by vessel to avoid leakage (train/val/test)
- Train models using:
  - **Random Forest (RF)**
  - **Gradient Boosting Classifier (GBC)**
- Use grid search for hyperparameter tuning
- Save best-performing models

### 3. **Model Evaluation**
- Run `results_analysis.py` to:
  - Load trained models
  - Evaluate on all splits
  - Compute accuracy, precision, recall, and F1-score
  - Generate comparison charts

### 4. **Track Reconstruction & Visualization**
- Use `reconstructing_tracks.py` to:
  - Predict fishing activity for selected vessels
  - Visualize on a world map with overlays
  - Include coastlines, EEZs, and clear labeling

---
