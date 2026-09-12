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
RC Low-Pass Filter: Time-Domain Response Visualizer

A scientific computing tool built in Python to simulate, calculate, and visualize the time-domain voltage response and phase lag of a first-order passive RC low-pass filter.

This project bridges theoretical AC circuit theory with numerical computing, leveraging NumPy for vectorized signal generation and Matplotlib for high-resolution engineering plots.

Technical Overview

A passive RC low-pass filter passes low-frequency signals while attenuating frequencies above its cutoff frequency ($f_c$). Because a capacitor takes finite time to charge and discharge ($q = C \cdot v$), output signals undergo both magnitude attenuation and phase delay relative to the input signal.

This software models the behavior of an RC network under sinusoidal steady-state excitation, taking circuit component values ($R, C$) and input signal metrics ($f, V_{in}$) to plot high-resolution continuous waveforms over three full time periods ($3T$).

Circuit Theory & Mathematical Derivations

1. Transfer Function & Cutoff Frequency

The transfer function $H(j\omega)$ of a passive RC circuit acting as a voltage divider is given by:

$$H(j\omega) = \frac{V_{out}}{V_{in}} = \frac{Z_C}{R + Z_C} = \frac{1}{1 + j\omega RC}$$

where $\omega = 2\pi f$ is the angular frequency and $Z_C = \frac{1}{j\omega C}$ is the capacitive reactance.

The Cutoff Frequency ($f_c$), or the $-3\text{ dB}$ half-power point where $R = X_C$, is derived as:

$$f_c = \frac{1}{2\pi R C}$$

2. Voltage Gain & Attenuation

The magnitude of the complex transfer function determines the voltage gain $A_v$:

$$A_v = \vert{}H(j\omega)\vert{} = \frac{1}{\sqrt{1 + \left(\frac{f}{f_c}\right)^2}}$$

The output amplitude $V_{out}$ and attenuation in decibels are:

$$V_{out} = V_{in} \cdot A_v$$

$$\text{Gain}_{\text{dB}} = 20 \log_{10}(A_v)$$

3. Phase Lag ($\theta$)

The phase response of the system represents the temporal lag of the output waveform relative to the input:

$$\theta = \angle H(j\omega) = -\arctan\left(\frac{f}{f_c}\right) \quad \text{[radians]}$$

4. Continuous Vectorized Wave Equations

Using NumPy, continuous signal arrays over three complete cycles ($t \in [0, 3T]$) are calculated using vectorized array math:

$$v_{in}(t) = V_{in} \sin(2\pi f t)$$

$$v_{out}(t) = V_{out} \sin(2\pi f t + \theta)$$

Project Structure

├── Week3_Sine_Wave_Visualizer.ipynb   # Interactive Jupyter Notebook implementation
├── main.py                            # Standalone Python script with terminal inputs
├── RC_Visualizer.png                  # Exported 300-DPI engineering plot
├── requirements.txt                   # Project dependencies
└── README.md                          # Project documentation


Installation & Setup

Prerequisites

Python 3.9 or higher

pip package manager

Installation Steps

Clone the repository:

git clone https://github.com/your-username/rc-filter-visualizer.git
cd rc-filter-visualizer


Create and activate a virtual environment (optional but recommended):

python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install required libraries:

pip install numpy matplotlib


Usage

Run the main Python script from your terminal:

python main.py


Prompt Example:

What is the Resistance (in Ohms)?: 1000
What is the Capacitance (in Farads)?: 1e-6
What is the Signal Frequency (in Hertz)?: 1000
What is the Signal Voltage (in Volts)?: 5.0


Terminal Output:

========================================
      RC LOW-PASS FILTER RESULTS        
========================================
 Cutoff Frequency (fc) : 159.15 Hz
 Voltage Gain (Av)     : 0.157
 Gain in Decibels      : -16.07 dB
 Output Voltage (Vout) : 0.79 V
 Phase Shift           : -80.96°
----------------------------------------
Signal Region: Stopband (High-Frequency Attenuation)
========================================


Generated Visualization

Upon calculation, the program renders and exports a 300-DPI engineering plot (RC_Visualizer.png):

Key Visualization Features:

Dual-Trace Overlay: Clear visual contrast between $v_{in}(t)$ (dashed blue) and $v_{out}(t)$ (solid red).

Dynamic LaTeX Labels: Plot title updates dynamically with calculated $V_{out}$ and phase lag $\theta$.

High-DPI Output: Clean gridlines and zero-line references optimized for research reporting.

Future Extensions

[ ] Add frequency-domain Bode Plots (Magnitude & Phase vs Frequency).

[ ] Implement active RC filter topologies (e.g., Sallen-Key 2nd-order filters).

[ ] Add CSV export capabilities for time-series data validation against laboratory oscilloscope logs.

License

Distributed under the MIT License. See LICENSE for more information.

## 🧰 Tech Stack
* **Language:** Python 3.x
* **Core Libraries:** `math`
* **Environment:** Google Colab / Jupyter Notebooks

---

## 👤 Author
* **Aarav Sharma** – 1st Year ECE Student, IIIT Jabalpur
* **Focus:** Signal Processing, Analog Circuit Simulation, Embedded Systems
