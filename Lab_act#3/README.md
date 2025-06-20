# Laboratory Activity 3 

**Title:** Introduction to Symbolic Computation with SymPy

---

## 🚀 Quick Start

1. **Clone or open** this folder in Colab/Jupyter.
2. Install SymPy (if not already):

   ```bash
   pip install sympy
   ```
3. Launch `lab3_sympy_Saragena.ipynb` and run all cells.

---

## What You’ll Practice

* Importing and using **SymPy** modules
* Creating and manipulating **symbolic** objects
* Performing **exact** arithmetic (rationals, roots)
* Defining **symbols**, **equations**, and solving them
* **Simplifying** and **expanding** algebraic expressions

---

## Environment & Tools

* **Python 3.x**
* **SymPy** package
* **(Optional)** Google Colab for interactive access

---

## Activity Walkthrough

### Task 1: Import SymPy

* **Goal:** Load core SymPy functions.
* **Command:**

  ```python
  from sympy import *
  ```
* **Pro Tip:** Use `init_printing()` for prettier outputs in notebooks.

---

### Task 2: Exact Arithmetic

* **Goal:** Work with exact rationals and radicals.
* **Examples:**

  ```python
  Rational(5, 3) + sqrt(10)/2    # exact rational + radical
  sqrt(50) * sqrt(Rational(5, 9)) # nested roots
  ```
* **Check:** Call `.evalf()` on results to see decimal approximations.

---

### Task 3: Symbols & Equations

* **Goal:** Define variables and set up equations symbolically.
* **Commands:**

  ```python
  x, y = symbols('x y')
  eq1 = Eq(2*x + 3*y, 12)
  eq2 = Eq(x - y, 4)
  ```
* **Activity:** Use `solve([eq1, eq2], [x, y])` to find solutions.

---

### Task 4: Simplification

* **Goal:** Reduce expressions to their simplest form.
* **Examples:**

  ```python
  simplify((x**2 + 2*x + 1)/(x + 1))  # (x+1)**2/(x+1) → x+1
  simplify((1 - 1/(1 + 1/x)) / (1 + 1/x))  # nested fraction
  ```
* **Pro Tip:** Compare `factor()` vs. `simplify()` for alternate forms.

---

### Task 5: Expansion

* **Goal:** Expand polynomial expressions.
* **Examples:**

  ```python
  expand((2*x + 2)**2)    # multiplies out the square
  expand((2*x + y)*(x - 2*y))
  ```
* **Check:** Observe how terms distribute and combine.

---

## Computational Thinking Highlights

* **Abstraction:** Treat expressions as objects, apply generic functions (`simplify`, `expand`).
* **Decomposition:** Break workflows into import → definitions → operations → interpretation.
* **Generalization:** The same routines (e.g. `simplify`) work on arbitrarily complex formulas.
