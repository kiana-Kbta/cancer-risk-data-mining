# Cancer Risk Data Mining Analysis

A data mining and machine learning project focused on analyzing relationships between smoking behavior, environmental factors, and cancer risk levels using statistical analysis, association rule mining, and visualization techniques.

---

## Project Overview

This project explores a cancer-related dataset to identify patterns and relationships between multiple health and environmental factors and cancer severity levels.

The notebook includes:
- Data preprocessing and cleaning
- Outlier detection and removal
- Statistical hypothesis testing
- Exploratory data visualization
- Frequent pattern mining using Apriori
- Association rule extraction
- Basic machine learning classification

The main objective of the project was to investigate whether factors such as smoking, air pollution, occupational hazards, obesity, chest pain, dust allergy, and genetic risk are associated with higher cancer levels.

---

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- SciPy
- Scikit-learn
- MLXtend
- Matplotlib
- Seaborn
- Plotly

---
## Full Data Dictionary & Schema

The dataset contains 1,000 patient records mapping across 25 distinct columns. Aside from `Age` and `Gender`, the behavioral, environmental, and clinical symptoms are quantified on a progressive risk/severity scale (typically ranging from `1` as lowest to `8` or `9` as highest extreme). 

During Phase II (Pattern Mining), the pipeline expands these ordinal rankings into separate binary columns (e.g., `Smoking1`, `Smoking2`, etc.) to evaluate transactional itemset combinations.

| Attribute Field | Variable Type | Operational Context & Scale |
| :--- | :--- | :--- |
| `Patient Id` | Object / String | Unique identifier format (cleaned of sequential duplicate collisions). Removed before modeling. |
| `Age` | Continuous Integer | Chronological patient age (mathematically truncated via IQR to bounds: `1.875 < Age < 70.875`). |
| `Gender` | Binary Categorical | Patient biological sex profile (`1` or `2`). |
| `Air Pollution` | Ordinal Risk Index | Severity of ambient air pollution exposure (Scale: 1–8). |
| `Alcohol use` | Ordinal Risk Index | Quantified frequency/volume of alcohol consumption (Scale: 1–8). |
| `Dust Allergy` | Ordinal Risk Index | Hypersensitivity metric to dust and fine particulate matter (Scale: 1–8). |
| `Occupational Hazards` | Ordinal Risk Index | Environmental safety risk exposure levels at workplace/industry (Scale: 1–8). |
| `Genetic Risk` | Ordinal Risk Index | Hereditary and familial history markers for oncology indicators (Scale: 1–7). |
| `chronic Lung Disease` | Ordinal Risk Index | Severity/progression tracking of pre-existing pulmonary conditions (Scale: 1–7). |
| `Balanced Diet` | Ordinal Risk Index | Nutritional health compliance index (Scale: 1–7). |
| `Obesity` | Ordinal Risk Index | Body Mass Index (BMI) risk categorization mapping (Scale: 1–7). |
| `Smoking` | Ordinal Risk Index | Direct tobacco usage tracking index; primary hypothesis target (Scale: 1–8). |
| `Passive Smoker` | Ordinal Risk Index | Quantified secondhand smoke exposure indices (Scale: 1–8). |
| `Chest Pain` | Ordinal Symptom Index | Reported physiological frequency/severity of thoracic pain (Scale: 1–9). |
| `Coughing of Blood` | Ordinal Symptom Index | Hemoptysis clinical severity and frequency indicators (Scale: 1–9). |
| `Fatigue` | Ordinal Symptom Index | Chronic clinical exhaustion metrics (Scale: 1–9). |
| `Weight Loss` | Ordinal Symptom Index | Unexplained rapid reduction in overall body mass (Scale: 1–8). |
| `Shortness of Breath` | Ordinal Symptom Index | Dyspnea severity tracking under stationary or active conditions (Scale: 1–9). |
| `Wheezing` | Ordinal Symptom Index | High-pitched airway obstruction whistling indicators (Scale: 1–8). |
| `Swallowing Difficulty` | Ordinal Symptom Index | Dysphagia physiological marker progression (Scale: 1–8). |
| `Clubbing of Finger Nails`| Ordinal Symptom Index | Hypertrophic osteoarthropathy clinical indicators (Scale: 1–9). |
| `Frequent Cold` | Ordinal Symptom Index | Immuno-susceptibility baseline tracking upper respiratory infections (Scale: 1–7). |
| `Dry Cough` | Ordinal Symptom Index | Non-productive cough persistence index (Scale: 1–7). |
| `Snoring` | Ordinal Symptom Index | Sleep apnea/airway restriction proxy indicators (Scale: 1–7). |
| `Level` | **Target Class** | Mapped categorical diagnosis tier: Low (`1`), Medium (`2`), High (`3`). |
---

## Dataset Processing

The dataset was cleaned and preprocessed before analysis:

- Missing values were filled using column mode values
- Duplicate patient IDs were detected and replaced
- Outliers in the age column were removed using the IQR method
- Low-frequency categorical outliers were filtered
- Cancer severity labels (`Low`, `Medium`, `High`) were encoded numerically

---

## Statistical Analysis

Several statistical techniques were used to analyze the relationship between smoking level and cancer severity:

### Methods Used
- Chi-Squared Test
- Shapiro-Wilk Normality Test
- Kruskal-Wallis Test
- Variance and skewness analysis
- Distribution visualization using:
  - Heatmaps
  - Boxplots
  - Histograms
  - Density plots

### Findings

The statistical analysis indicated that smoking rates differ significantly across cancer severity groups.

Since the data distributions were not normal according to the Shapiro-Wilk test, the Kruskal-Wallis test was used instead of ANOVA.

The results suggested statistically significant differences in smoking behavior between cancer level groups.

---

## Frequent Pattern Mining

Apriori association rule mining was applied to discover combinations of features strongly associated with high cancer levels.

### Important Patterns Found

Several feature combinations showed strong association with high cancer severity (`Level3`), including:

- Obesity
- Chest Pain
- Occupational Hazards
- Dust Allergy
- Genetic Risk
- Air Pollution
- Chronic Lung Disease

Some association rules achieved:
- Confidence values close to or equal to `1.0`
- Lift values above `2.5`

This suggests strong relationships between these combined factors and high cancer severity.

### Example Rules

- `(Obesity7) → (Level3)`
- `(Obesity7, Chest Pain7) → (Level3)`
- `(Air Pollution6, Obesity7) → (Level3)`
- `(Dust Allergy7, Chest Pain7) → (Level3)`
- `(Occupational Hazards7, Chest Pain7) → (Level3)`

---

## Visualization

The project includes several visualizations for exploratory analysis and association rule interpretation:

- Smoking distribution across cancer levels
- Heatmaps for contingency tables
- Boxplots and density plots
- Scatter plot of support vs confidence for association rules

---

## Project Structure

```text
project/
│── notebook.ipynb
│── requirements.txt
│── README.md
```

---

## Data Access & Governance

Out of absolute compliance with academic department guidelines, corporate non-disclosure protocols, and distribution boundaries, the raw unaggregated spreadsheets are omitted from this repository. The analytics system is wholly format-agnostic; it is built to run cleanly against any valid structured data template matching the clinical column schema outlined in the Full Data Dictionary & Schema section.