````markdown
# Laboratory Activity 2  
**Title:** Titanic Data Cleaning & Exploratory Visualization  

---

## Quick Start  
1. **Clone or download** this folder.  
2. Ensure `train.csv` is side by side with your notebook.  
3. (Optional) If you’re on Colab, mount your Drive in cell 1.  
4. Install dependencies:  
   ```bash
   pip install pandas matplotlib
````

5. Open & “Run All” in `lab2_titanic_Saragena.ipynb`.

---

## What You’ll Practice

* **Data Profiling:** `.info()`, `.describe()`, `.isnull().sum()`
* **Null Value Strategy:** median imputation, dropping high NA columns
* **De-duplication:** detecting & removing duplicate rows
* **Type Casting:** converting numeric codes into `category`s
* **Standardization:** renaming & lowercasing columns
* **File I/O:** exporting a clean CSV
* **Visualization:** basic bar charts & histograms to reveal survival patterns

---

## Environment & Tools

* **Python** 3.x
* **pandas** for data wrangling
* **matplotlib** for charts
* **(Colab users)** remember to mount Drive:

  ```python
  from google.colab import drive
  drive.mount('/content/drive')
  ```

---

## Activity Walkthrough

### Q1: Load & Inspect

* **Goal:** Read `train.csv` into a DataFrame and peek at its shape, types, and head.
* **Pro Tip:**

  ```python
  df.head()          # first five rows
  df.info()          # dtype & null counts
  df.describe()      # numeric summaries
  ```

### Q2: Triage Missing Data

* **Goal:** Quantify and handle nulls.
* **Checklist:**

  * `df.isnull().sum()` → find columns with NAs
  * **Drop** `Cabin` (lots of NAs)
  * **Impute** `Age` with median
  * **Impute** `Embarked` with mode
* **Pro Tip:** Always re‑run `df.info()` to confirm nulls are gone.

### Q3: Remove Duplicates & Fix Types

* **Goal:** Ensure each passenger is unique and cast codes to categories.
* **Commands:**

  ```python
  df.drop_duplicates(inplace=True)
  df['survived'] = df['survived'].astype('category')
  df['pclass']   = df['pclass'].astype('category')
  ```
* **Why?**
  – Duplicates skew counts.
  – Categorical dtype optimizes memory and grouping.

### Q4: Standardize & Save

* **Goal:** Clean up column names and export.
* **Commands:**

  ```python
  df.columns = df.columns.str.lower()
  df.to_csv('titanic_cleaned.csv', index=False)
  ```
* **Pro Tip:** lowercase names avoid silly typos later.

### Q5: Visual Insights

* **5.1 Survivors vs. Non‑Survivors Bar**

  ```python
  df['survived'].value_counts().plot(kind='bar')
  ```
* **5.2 Age Distribution Histogram**

  ```python
  df['age'].plot(kind='hist', bins=20)
  ```
* **5.3 Survival by Gender**

  ```python
  df.groupby('sex')['survived'].mean().plot(kind='bar')
  ```
* **5.4 Survival by Class**

  ```python
  df.groupby('pclass')['survived'].mean().plot(kind='bar')
  ```
* **Pro Tip:** Add `.set_title()` and axis labels so your plots communicate clearly.

---

## Computational Thinking Highlights

* **Decompose:** isolate cleaning tasks—nulls, duplicates, types, names, I/O.
* **Pattern Match:** spot missing value “signatures” (e.g. 77% missing cabin).
* **Abstraction:** turn repeated code into short, reusable snippets.
* **Visualization:** check your logic by eyeballing charts.