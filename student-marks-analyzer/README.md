# 📊 Student Performance Analysis Using Pandas

A data analysis project built with Python and Pandas to clean, process, and analyse a real-world messy student score dataset. The project covers the full data analysis pipeline — from raw dirty data to structured insights.

---

## 📁 Project Structure

```
student-performance-analysis/
├── student_performance_analysis.ipynb   # Jupyter Notebook with full analysis
├── data.csv                             # Raw dataset (100 students, 3 subjects)
└── cleaned_data.csv                     # Exported clean and enriched dataset
```

---

## 📋 Dataset Overview

The raw dataset contained **100 student records** across three subjects — Math, Science, and English — with several data quality issues that had to be resolved before any analysis.

| Column | Raw Type | Issues Found |
|---|---|---|
| name | string | Duplicate entries |
| math | string | `ABSENT`, `NULL`, `NaN`, missing values |
| science | float | Missing values |
| english | string | `ERROR`, `N/A`, missing values |

---

## 🧹 Data Cleaning Pipeline

**Step 1 — Inspect the data**
Used `.info()` and `.isnull().sum()` to understand column types and identify null counts across all columns.

**Step 2 — Remove duplicates**
Detected and dropped all duplicate rows, then reset the index.
```python
students_df = students_df.drop_duplicates()
students_df = students_df.reset_index(drop=True)
```

**Step 3 — Replace invalid text values**
Standardised all non-numeric placeholders to `pd.NA`.
```python
students_df = students_df.replace(['ABSENT', 'ERROR', 'NULL', 'N/A'], pd.NA)
```

**Step 4 — Convert columns to numeric**
Cast all score columns from string to float using `errors='coerce'` to safely handle any remaining invalid entries.
```python
for col in ['math', 'science', 'english']:
    students_df[col] = pd.to_numeric(students_df[col], errors='coerce')
```

**Step 5 — Drop remaining nulls**
Dropped all rows that still had missing values after conversion and reset the index.

**Result after cleaning: 89 complete, valid records.**

---

## 🔍 Analysis

### 1. Average Score per Student
Calculated each student's average across all three subjects using `mean(axis=1)`.

### 2. Average Score per Subject

| Subject | Average Score |
|---|---|
| Math | 76.16 |
| Science | 77.81 |
| English | 76.29 |

### 3. Grade Classification
Each student was assigned a letter grade based on their overall average using a custom function:

| Grade | Average Range |
|---|---|
| A | 85 and above |
| B | 75 – 84 |
| C | 65 – 74 |
| F | Below 65 |

**Grade Distribution:**

| Grade | Count |
|---|---|
| A | 30 |
| B | 26 |
| C | 17 |
| F | 16 |

### 4. Per-Subject Performance Labels
Each student was labelled `Above Average` or `Below Average` per subject, compared against that subject's mean score.

| Subject | Above Average | Below Average |
|---|---|---|
| Math | 51 | 38 |
| Science | 51 | 38 |
| English | 52 | 37 |

### 5. Best Subject per Student
Identified each student's highest-scoring subject using `idxmax(axis=1)`.

| Best Subject | Count |
|---|---|
| Science | 65 |
| English | 22 |
| Math | 2 |

### 6. Top 10 Students
Ranked by overall average — **Emily** achieved the highest average of **96.33**, followed by Isabella and Aubrey at **94.00**.

### 7. Students at Risk
Identified 7 students with averages between 60 and 65 — borderline cases needing academic support.

### 8. Failed Students
Filtered all students with grade `F` (average below 65).

- **16 students** received a failing grade
- **Failed percentage: 17.98%**

---

## 💡 Key Insights

- **Emily** achieved the highest overall average in the dataset (96.33).
- **Science** was the best-performing subject for the majority of students (65 out of 89).
- **Mathematics** had the lowest class average, suggesting it is the most challenging subject.
- **17.98%** of students failed, with 7 additional students identified as being at risk.

---

## 💾 Output

The cleaned and fully enriched dataset was exported as `cleaned_data.csv`, containing all original scores plus the computed columns: `average`, `grade`, `math_performance`, `science_performance`, `english_performance`, and `best_subject`.

---

## 🛠️ Tools & Libraries

- Python 3.13
- Pandas
- Jupyter Notebook

---

## ▶️ How to Run

1. Clone the repository:
```bash
git clone https://github.com/vidushanpathir505-bot/student-performance-analysis.git
```

2. Install dependencies:
```bash
pip install pandas jupyter
```

3. Open the notebook:
```bash
jupyter notebook student_performance_analysis.ipynb
```

---

## 💡 Future Improvements

- 📊 Add visualisations — bar charts, histograms, and heatmaps using Matplotlib or Seaborn
- 📈 Subject correlation analysis — explore relationships between scores
- 🔔 Automated at-risk student alerts
- 🌐 Interactive dashboard using Plotly or Streamlit

---

## 👨‍💻 Author

**Vidushan Pathirana**

⭐ If you found this useful, give it a star!
