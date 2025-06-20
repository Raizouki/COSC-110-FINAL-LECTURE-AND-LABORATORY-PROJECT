````markdown
# Laboratory Activity 1  
**Title:** Computational Thinking with the Titanic Dataset  

---

## Quick Start  
1. **Clone this folder** to your machine or open it in Colab/GitHub Codespaces.  
2. Ensure `titanic.csv` sits alongside the notebook (or update its path).  
3. Install dependencies:  
   ```bash
   pip install pandas matplotlib
````

4. Launch `lab1_titanic_Saragena.ipynb` and hit “Run All.”

---

## What You’ll Learn

* **Data Ingestion:** How to read CSVs into pandas.
* **Data Profiling:** Use `df.info()`, `df.describe()`, and value counts.
* **Cleaning Strategies:** Dropping/filling missing values thoughtfully.
* **Statistics:** Computing survival rates and conditional logic.
* **Visualization:** Crafting histograms to compare age groups.

---

## Environment & Tools

* **Python 3.x**
* **pandas** for data manipulation
* **matplotlib** for plotting
* **(Optional)** Google Colab – simply mount your Drive in the first cell:

  ```python
  from google.colab import drive
  drive.mount('/content/drive')
  ```

---

## Activity Walkthrough

### Q1: Load & Peek

* **Goal:** Bring `titanic.csv` into a DataFrame.
* **Commands:**

  ```python
  import pandas as pd
  df = pd.read_csv('titanic.csv')
  df.head(), df.info()
  ```
* **Pro Tip:** `df.sample(5)` gives a random glimpse—great for spotting odd values!

### Q2: Missing Data Triage

* **Goal:** Identify and handle nulls.
* **Strategy:**

  1. **Drop** `Cabin` (too many NAs).
  2. **Fill** `Age` with median.
  3. **Fill** `Embarked` with mode.
* **Check:**

  ```python
  df.isnull().sum()
  ```

### Q3: Who Survived?

* **Goal:** Compute overall survival percentage.
* **One liner:**

  ```python
  survival_rate = df['Survived'].mean() * 100
  ```
* **Insight:** If >50%, “Most lived!” else “Most perished.”

### Q4: Age vs. Fate

* **Goal:** Plot and compare ages of survivors vs. non survivors.
* **Approach:**

  ```python
  import matplotlib.pyplot as plt

  s = df[df['Survived']==1]['Age']
  ns = df[df['Survived']==0]['Age']
  plt.hist(s, bins=20, alpha=0.6)
  plt.hist(ns, bins=20, alpha=0.6)
  plt.legend(['Survived','Didn’t Survive'])
  plt.title('Age Distribution by Survival')
  plt.show()
  ```
* **Pro Tip:** Compute `s.mean()` vs. `ns.mean()` to quantify differences.

---

## Computational Thinking Highlights

* **Decompose:** Break tasks into small, testable chunks (load → inspect → clean → analyze → visualize).
* **Pattern Match:** Recognize “missingness” patterns (entire column vs. sporadic gaps).
* **Abstraction:** Use functions (e.g. a helper to fill nulls) to generalize cleaning steps.
* **Evaluation:** Always verify results (no nulls left? plots make sense?).
