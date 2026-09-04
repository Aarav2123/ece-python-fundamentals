# ECE Python & Signal Processing Fundamentals

A curated collection of Python tools, numerical simulations, and hardware validation scripts for core Electronics and Communication Engineering (ECE) concepts.

---

## 📌 Repository Overview

This repository documents my progressive journey in bridging analytical circuit equations, computational simulation pipelines, and real-world hardware verification.

---

## 🛠️ Projects

### 1. Modular DC Circuit Analyzer (Week 1)
* **File:** `WEEK1_PROJECT.ipynb`
* **Description:** A modular script for calculating electrical parameters across basic DC circuit networks.
* **Key Features:**
  * Interactive CLI input for circuit parameters.
  * Analytical calculations for Voltage ($V = IR$) and Power dissipation ($P = I^2 R = \frac{V^2}{R}$).
  * Boundary checks to prevent division-by-zero errors.

---

### 2. RC Low-Pass Filter Evaluator (Week 2)
* **File:** `Week2_RC_Low_Pass_Filter.ipynb`
* **Description:** Analytical evaluation and frequency response calculator for single-pole passive RC low-pass filters.

#### **Governing Equations:**
* **Cutoff Frequency ($f_c$):** $f_c = \frac{1}{2\pi R C}$
* **Voltage Gain ($A_v$):** $A_v = \frac{1}{\sqrt{1 + \left(\frac{f}{f_c}\right)^2}}$
* **Decibel Gain ($A_{dB}$):** $A_{dB} = 20 \log_{10}(A_v)$
* **Phase Shift ($\theta$):** $\theta = -\arctan\left(\frac{f}{f_c}\right) \times \frac{180}{\pi}$

#### **Engineering Highlights:**
* **Input Validation:** Enforces $R > 0$, $C > 0$, $f \ge 0$ loops to guarantee physical system bounds.
* **Overvoltage Protection Warning:** Triggers safety warnings if input amplitude $|V_{in}| > 12\text{V}$.
* **Signal Classification:** Uses tolerance-aware classification (`math.isclose`) to group system state into **Passband**, **$-3\text{dB}$ Corner Cutoff**, or **Stopband**.

---

## 🧰 Tech Stack
* **Language:** Python 3.x
* **Core Libraries:** `math`
* **Environment:** Google Colab / Jupyter Notebooks

---

## 👤 Author
* **Aarav Sharma** – 1st Year ECE Student
* **Focus:** Signal Processing, Analog Circuit Simulation, Embedded Systems
