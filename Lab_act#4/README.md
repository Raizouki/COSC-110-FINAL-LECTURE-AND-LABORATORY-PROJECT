````markdown 
# Laboratory Activity 4  
**Title:** Symbolic Calculus & Equation Solving with SymPy  

---

## Quick Start  
1. **Clone or open** this folder in Jupyter/Colab.  
2. Ensure SymPy is installed:  
   ```bash
   pip install sympy
````

3. Launch `lab4_sympy_Saragena_.ipynb` and “Run All.”

---

## What You’ll Learn

* Manipulating **symbols** and **expressions**
* Computing **limits** of functions
* Finding **derivatives** symbolically
* Generating **Taylor series** expansions
* **Solving** algebraic equations
* Reflecting on results to build intuition

---

## Environment & Tools

* **Python 3.x**
* **SymPy** library
* **(Optional)** Google Colab for instant setup

---

## Activity Walkthrough

### Task 1: Play with Symbols

* **Goal:** See how SymPy handles algebraic symbols.
* **Snippet:**

  ```python
  x = symbols('x')
  x + x    # → 2*x  
  x * x    # → x**2  
  ```
* **Pro Tip:** Call `init_printing()` for MS‑Word‑like math formatting.

---

### Task 2: Compute Limits

* **Goal:** Evaluate common limits analytically.
* **Snippet:**

  ```python
  limit(sin(x)/x, x, 0)  # → 1  
  ```
* **Pro Tip:** Try `limit(1/x, x, oo)` to see how SymPy handles infinity.

---

### Task 3: Derivatives

* **Goal:** Differentiate simple to compound expressions.
* **Snippet:**

  ```python
  diff(x**2, x)        # → 2*x  
  diff(sin(x**2), x)   # → 2*x*cos(x**2)  
  ```
* **Pro Tip:** Use `diff(expr, x, 2)` for second derivatives.

---

### Task 4: Series Expansion

* **Goal:** Generate a Taylor series about zero.
* **Snippet:**

  ```python
  exp(x).series(x, 0, 5)  
  # → 1 + x + x**2/2 + x**3/6 + x**4/24 + O(x**5)  
  ```
* **Pro Tip:** Adjust the order parameter to include more or fewer terms.

---

### Task 5: Solve Equations

* **Goal:** Symbolically solve quadratics and simple systems.
* **Snippet:**

  ```python
  solve(Eq(x**2 - 4, 0), x)           # → [-2, 2]  
  solve([Eq(x + y, 5), Eq(x - y, 1)], [x, y])  # → {x: 3, y: 2}  
  ```
* **Pro Tip:** For inequalities, explore `reduce_inequalities()`.

---

### Task 6: Reflect & Extend

* **Goal:** Write brief answers to:

  1. Which task was easiest/hardest—and why?
  2. How might symbolic tools speed up real‑world problem‑solving?
* **Pro Tip:** Note any surprises in the way SymPy represents large expressions.

---

## Computational Thinking Highlights

* **Abstraction:** Symbols let you manipulate formulas generically.
* **Decomposition:** Split calculus workflows into limit → derivative → series → solve.
* **Evaluation:** Always compare symbolic outputs to numeric checks (e.g. `float(expr)`).
