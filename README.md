# ECE Python & Signal Processing Fundamentals

A curated collection of Python tools, numerical simulations, and hardware validation scripts for core Electronics and Communication Engineering (ECE) concepts.

---

## 📌 Repository Overview

This repository documents my progressive journey in bridging analytical circuit equations, computational simulation pipelines, and real-world hardware verification.

---

## 🛠️ Projects

### 1. Modular DC Circuit Analyzer (Week 1)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Aarav2123/ece-python-fundamentals/blob/main/WEEK1_PROJECT.ipynb)

* **File:** `WEEK1_PROJECT.ipynb`
* **Description:** A modular script for calculating electrical parameters across basic DC circuit networks.
* **Key Features:**
  * Interactive CLI input for circuit parameters.
  * Analytical calculations for Voltage ($V = IR$) and Power dissipation ($P = I^2 R = \frac{V^2}{R}$).
  * Boundary checks to prevent division-by-zero errors.

---

### 2. RC Low-Pass Filter Evaluator (Week 2)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Aarav2123/ece-python-fundamentals/blob/main/Week2_RC_Low_Pass_Filter.ipynb)

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
# RC Low-Pass Filter: Time-Domain Signal Visualizer

An interactive Python simulation tool to compute, analyze, and visualize the time-domain signal response of a first-order passive RC low-pass filter. 

This project models continuous sinusoidal input signals and demonstrates real-time amplitude attenuation and phase shift ($\theta$) across different frequency operating regions (Passband, Corner Frequency, and Stopband).

---

## 📌 Project Features

- **Input Validation:** Interactive prompts for resistance ($R$), capacitance ($C$), frequency ($f$), and voltage ($V_{in}$) with physical boundary safety checks.
- **Physics Engine:** Computes exact cutoff frequency ($f_c$), voltage gain ($A_v$), gain in decibels ($\text{dB}$), output voltage ($V_{out}$), and phase lag ($\theta$).
- **Vectorized Signal Processing:** Uses `numpy.linspace` to sample 3 full signal cycles across 1,000 discrete points.
- **Publication-Quality Export:** Automatically generates and saves a 300 DPI publication-ready plot (`Week3_Sine_Wave_Visualizer.png`).

---

## 🧮 Theoretical Background & Equations

A passive first-order low-pass filter consists of a resistor ($R$) in series with a capacitor ($C$). The output is taken across the capacitor.

### 1. Cutoff Frequency ($f_c$)
The half-power (-3 dB corner) frequency where capacitive reactance equals resistance ($X_C = R$):
$$f_c = \frac{1}{2\pi R C}$$

### 2. Voltage Gain ($A_v$) & Decibel Attenuation
$$A_v = \frac{V_{out}}{V_{in}} = \frac{1}{\sqrt{1 + \left(\frac{f}{f_c}\right)^2}}$$

$$\text{Gain}_{\text{dB}} = 20 \log_{10}(A_v)$$

### 3. Phase Shift ($\theta$)
Because the capacitor requires time to charge, the output waveform lags behind the input:
$$\theta = -\arctan\left(\frac{f}{f_c}\right) \quad \text{(in radians)}$$

### 4. Time-Domain Signal Modeling
$$v_{in}(t) = V_{in} \sin(2\pi f t)$$
$$v_{out}(t) = V_{out} \sin(2\pi f t + \theta)$$

---

## 🚀 Quick Start

### Prerequisites

Ensure Python 3.8+ and the required scientific libraries are installed:

```bash
pip install numpy matplotlib

git clone [https://github.com/YOUR_GITHUB_USERNAME/RC-Filter-Visualizer.git](https://github.com/YOUR_GITHUB_USERNAME/RC-Filter-Visualizer.git)
cd RC-Filter-Visualizer
python Week3_Sine_Wave_Visualizer.py

========================================
      RC LOW-PASS FILTER RESULTS        
========================================
 Cutoff Frequency (fc) : 1591.55 Hz
 Voltage Gain (Av)     : 0.707
 Gain in Decibels      : -3.01 dB
 Output Voltage (Vout) : 3.54 V
 Phase Shift           : -45.00°
----------------------------------------
Signal Region: Cutoff Frequency (-3dB Corner Point)
========================================

## 🧰 Tech Stack
* **Language:** Python 3.x
* **Core Libraries:** `math`
* **Environment:** Google Colab / Jupyter Notebooks

---

## 👤 Author
* **Aarav Sharma** – 1st Year ECE Student, IIIT Jabalpur
* **Focus:** Signal Processing, Analog Circuit Simulation, Embedded Systems
