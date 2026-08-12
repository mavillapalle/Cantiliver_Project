# Cantilever Characterisation Using Position Sensitive Detector

## 📌 Project Overview

This project focuses on the experimental characterisation of a
cantilever using an optical lever measurement system and a Position
Sensitive Detector (PSD).

The main aim is to measure the free-vibration response of a cantilever
and determine its:

- Natural Frequency
- Damping Ratio
- Quality Factor

The measured optical signal is converted into an electrical signal
using analogue signal-conditioning circuits, acquired using a PicoScope,
and analysed using Python.

Three cantilever configurations were investigated:

1. Normal Cantilever
2. Drop Cantilever
3. Mass Cantilever

---

# 🎯 Objectives

The main objectives of the project were:

- Develop an optical-lever measurement system.
- Detect small cantilever vibrations using a PSD.
- Convert PSD photocurrent into voltage using a Transimpedance Amplifier.
- Extract the differential signal using a differential amplifier.
- Acquire the signal using PicoScope.
- Process the measured signal using Python.
- Determine the natural frequency.
- Determine the damping ratio.
- Calculate the quality factor.
- Compare different cantilever configurations.
- Analyse the signal using time-domain and frequency-domain methods.

---

# 🔬 System Overview

The complete measurement chain is:

```text
Laser
  ↓
Mirror 1
  ↓
Cantilever
  ↓
Mirror 2
  ↓
Position Sensitive Detector (PSD)
  ↓
Transimpedance Amplifier (TIA)
  ↓
Differential Amplifier
  ↓
PicoScope
  ↓
Python Data Analysis
```

The laser beam is reflected from the vibrating cantilever and directed
towards the PSD.

The PSD converts the movement of the laser spot into photocurrents.
These small currents are converted into voltage signals using two
Transimpedance Amplifiers.

The two voltage signals are then processed by a differential amplifier
to obtain a single output voltage.

The output is acquired using PicoScope and analysed using Python.

---

# ⚙️ Experimental Setup

## Main Components

- Laser diode module
- Two steering mirrors
- Microcantilever
- Hamamatsu S3932 Position Sensitive Detector
- MCP6002 Transimpedance Amplifiers
- LM324 Differential Amplifier
- PicoScope 2000 Series
- Optical breadboard
- Python / Jupyter
- LTspice
- KiCad

Three cantilever configurations were tested:

```text
Normal Cantilever
       ↓
Drop-loaded Cantilever
       ↓
Mass-loaded Cantilever
```

The cantilever was lightly tapped to initiate free vibration.

---

# 💡 Optical Lever Principle

The optical measurement is based on the law of reflection.

\[
\theta_i = \theta_r
\]

where:

- \(\theta_i\) = angle of incidence
- \(\theta_r\) = angle of reflection

For small angular movements of the cantilever:

\[
\theta_r = 2\theta
\]

where:

- \(\theta\) = angular displacement of the cantilever
- \(\theta_r\) = angular displacement of the reflected beam

If the detector is at a distance \(D\) from the mirror, the laser spot
displacement is approximately:

\[
x \approx 2D\theta
\]

where:

- \(x\) = laser spot displacement
- \(D\) = distance between mirror and detector
- \(\theta\) = cantilever angular displacement

This provides optical amplification of the small cantilever movement.

---

# 📡 Position Sensitive Detector

A Hamamatsu S3932 one-dimensional lateral-effect PSD was used to detect
the position of the laser beam.

The position of the incident beam is calculated using the two photocurrents:

\[
x =
\frac{l_x}{2}
\frac{I_{x1}-I_{x2}}
{I_{x1}+I_{x2}}
\]

where:

- \(x\) = position of the incident beam
- \(l_x\) = length of the resistive layer
- \(I_{x1}\) = current from the first electrode
- \(I_{x2}\) = current from the second electrode

---

# 📐 Cantilever Natural Frequency

The first-mode natural frequency of a uniform cantilever is given by
Euler-Bernoulli beam theory:

\[
f_1 =
\frac{1}{2\pi}
\beta_1^2
\sqrt{\frac{EI}{mL^4}}
\]

where:

- \(f_1\) = first natural frequency
- \(E\) = modulus of elasticity
- \(I\) = area moment of inertia
- \(m\) = mass per unit length
- \(L\) = cantilever length
- \(\beta_1 = 1.875\) for the first mode

### Effect of Parameters

| Parameter | Effect on Natural Frequency |
|-----------|-----------------------------|
| Increase in \(E\) | Frequency increases |
| Increase in \(I\) | Frequency increases |
| Increase in \(L\) | Frequency decreases |
| Increase in \(m\) | Frequency decreases |

Adding mass increases the effective inertia of the cantilever and
therefore reduces its natural frequency.

---

# 🌊 Damping

The free vibration of a damped cantilever can be represented as:

\[
x(t) =
Ae^{-\delta t}
\cos(\omega_d t+\phi)
\]

where:

- \(x(t)\) = displacement
- \(A\) = initial amplitude
- \(\delta\) = damping constant
- \(\omega_d\) = damped natural angular frequency
- \(\phi\) = initial phase
- \(t\) = time

The vibration amplitude decreases because mechanical energy is lost
through effects such as air resistance and internal friction.

---

# 📉 Logarithmic Decrement

The logarithmic decrement is calculated from successive vibration peaks:

\[
\Lambda =
\ln\left(\frac{x_1}{x_2}\right)
\]

where:

- \(x_1\) = first peak amplitude
- \(x_2\) = second peak amplitude

For peaks separated by \(n\) cycles:

\[
\Lambda =
\frac{1}{n}
\ln\left(\frac{x_1}{x_{n+1}}\right)
\]

where:

- \(n\) = number of cycles
- \(x_1\) = initial peak amplitude
- \(x_{n+1}\) = peak amplitude after \(n\) cycles

---

# 📊 Damping Ratio

The damping ratio is calculated using:

\[
\zeta =
\frac{\Lambda}
{\sqrt{4\pi^2+\Lambda^2}}
\]

where:

- \(\zeta\) = damping ratio
- \(\Lambda\) = logarithmic decrement

For the peak-detection method used in the analysis, the report also
uses the approximation:

\[
\zeta =
\frac{\delta}{2\pi}
\]

---

# 🔄 Natural Angular Frequency

The natural angular frequency is related to natural frequency by:

\[
\omega_n = 2\pi f_n
\]

where:

- \(\omega_n\) = natural angular frequency
- \(f_n\) = natural frequency

---

# ⚙️ Damping Constant

The damping constant is:

\[
\delta = \zeta\omega_n
\]

where:

- \(\delta\) = damping constant
- \(\zeta\) = damping ratio
- \(\omega_n\) = natural angular frequency

---

# ⭐ Quality Factor

The quality factor describes the sharpness of the resonance.

It is calculated from the damping ratio:

\[
Q = \frac{1}{2\zeta}
\]

A higher \(Q\) corresponds to a sharper resonance and lower relative
damping.

The report also expresses the quality factor in terms of stored and
lost energy:

\[
Q =
2\pi
\frac{E_{\text{stored}}}
{E_{\text{lost per cycle}}}
\]

---

# 🔌 Signal Conditioning

## Transimpedance Amplifier

The PSD produces very small photocurrents. Two MCP6002-based
Transimpedance Amplifiers were used to convert the photocurrents into
voltage signals.

The feedback resistor was:

\[
R_f = 100\,k\Omega
\]

A feedback capacitor was used to improve stability.

---

# 📶 TIA Bandwidth

The approximate Transimpedance Amplifier bandwidth is:

\[
BW =
\frac{1}{2R_fC_{PSD}}
\]

where:

- \(R_f\) = feedback resistance
- \(C_{PSD}\) = PSD terminal capacitance

Increasing \(R_f\) increases gain but reduces the basic bandwidth.

LTspice was used to investigate the feedback capacitor and amplifier
response.

The simulation showed that approximately 20 pF to 30 pF provided a
suitable response for the application.

---

# ➖ Differential Amplifier

The two TIA output voltages are represented as:

\[
V_A
\]

and

\[
V_B
\]

The differential amplifier produces:

\[
V_{out}=V_A-V_B
\]

An LM324 quad operational amplifier was used for the differential
amplifier stage.

The resulting voltage was sent to the PicoScope for acquisition.

---

# 🧪 SPICE Simulation

A 1D Pi-network equivalent model of the S3932 PSD was created in LTspice.

The model included:

- PSD resistance
- PSD capacitance
- MCP6002 equivalent model
- Feedback resistor
- Feedback capacitor

Transient analysis and parameter sweeps were performed to investigate
the circuit stability and suitable feedback capacitor values.

---

# 💻 Signal Processing

The measured signal was acquired using PicoScope and processed in Python
using Jupyter.

The following analysis methods were implemented:

1. Fourier Transform (FFT)
2. Peak Detection
3. Zero-Crossing
4. Parabolic Interpolation

---

# 1️⃣ Fourier Transform (FFT)

The Fourier Transform converts the signal from the time domain into the
frequency domain.

The FFT is calculated as:

\[
X_k =
\sum_{n=0}^{N-1}
x_n e^{-j2\pi kn/N}
\]

where:

- \(X_k\) = FFT output
- \(x_n\) = input signal
- \(N\) = number of samples
- \(k\) = frequency-bin index

## FFT Algorithm

```text
Raw Signal
    ↓
Remove DC Offset
    ↓
Apply Hann Window
    ↓
Calculate FFT
    ↓
Calculate Magnitude Spectrum
    ↓
Locate Largest Peak
    ↓
Output Dominant Frequency
```

## FFT Results

| Configuration | FFT Frequency |
|---------------|--------------:|
| Normal | 474.0 Hz |
| Drop | 358.3 Hz |
| Mass | 290.7 Hz |

---

# 2️⃣ Peak Detection Method

The peak-detection method works directly on the time-domain signal.

The signal is filtered and successive local maxima are detected.

The average time between peaks is used to calculate the vibration period.

The natural frequency is:

\[
f_n = \frac{1}{T}
\]

where:

- \(T\) = vibration period
- \(f_n\) = natural frequency

The logarithmic decrement is:

\[
\delta =
\frac{1}{n}
\ln\left(\frac{x_0}{x_n}\right)
\]

and the damping ratio used for this method is:

\[
\zeta =
\frac{\delta}{2\pi}
\]

## Peak Detection Algorithm

```text
Raw Signal
    ↓
Band-Pass Filtering
    ↓
Detect Local Peaks
    ↓
Calculate Time Between Peaks
    ↓
Calculate Average Period
    ↓
Calculate Natural Frequency
    ↓
Calculate Logarithmic Decrement
    ↓
Calculate Damping Ratio
```

The peak amplitudes also provide information about the exponential
decay of the cantilever vibration.

---

# 3️⃣ Zero-Crossing Method

The zero-crossing method determines the natural frequency from the
time-domain signal.

A complete vibration cycle contains two zero crossings.

The signal is first filtered using a Butterworth filter to reduce noise.

Two neighbouring points around each crossing are used for interpolation.

The zero-crossing time is calculated as:

\[
t_0 =
t_1-\frac{v_1}{m}
\]

where:

- \(t_0\) = estimated zero-crossing time
- \(t_1\) = time of the neighbouring point
- \(v_1\) = signal value at the neighbouring point
- \(m\) = slope between the two points

The time difference between consecutive crossings is calculated and
averaged to determine the vibration period.

The natural frequency is then:

\[
f_n = \frac{1}{T}
\]

## Zero-Crossing Algorithm

```text
Raw Signal
    ↓
Butterworth Filtering
    ↓
Detect Zero Crossings
    ↓
Select Neighbouring Points
    ↓
Calculate Slope
    ↓
Linear Interpolation
    ↓
Calculate Zero-Crossing Time
    ↓
Calculate Time Differences
    ↓
Calculate Average Period
    ↓
Calculate Frequency
```

---

# 4️⃣ Parabolic Interpolation of FFT Peak

Parabolic interpolation was used to refine the FFT frequency estimate.

The FFT produces discrete frequency bins, so the actual resonance
frequency may lie between two bins.

The method assumes a Gaussian-shaped peak:

\[
Y =
A e^{-\frac{(f-f_0)^2}{2\sigma^2}}
\]

Taking the logarithm:

\[
\ln Y =
\ln A -
\frac{(f-f_0)^2}{2\sigma^2}
\]

This produces a parabolic relationship around the peak.

The FFT peak bin is represented by \(k\).

The neighbouring bins \(k-1\), \(k\), and \(k+1\) are used.

The fractional shift is:

\[
\delta =
\frac{L_{k-1}-L_{k+1}}
{2(L_{k+1}-2L_k+L_{k-1})}
\]

The refined frequency is:

\[
f_{\text{refined}}
=
(k+\delta)\Delta f
\]

where:

- \(k\) = dominant FFT peak bin
- \(\delta\) = fractional peak shift
- \(\Delta f\) = FFT frequency resolution
- \(f_{\text{refined}}\) = refined frequency

## Parabolic Interpolation Algorithm

```text
FFT Magnitude Spectrum
        ↓
Locate Peak Bin k
        ↓
Take k-1, k and k+1
        ↓
Calculate Log Magnitude
        ↓
Fit Parabola
        ↓
Calculate Vertex Offset
        ↓
Calculate Fractional Shift δ
        ↓
Calculate Refined Frequency
```

---

# 📈 Parabolic Interpolation Results

| Configuration | Discrete Peak | Refined Peak | Correction |
|---------------|--------------:|-------------:|-----------:|
| Normal | 472.00 Hz | 472.03 Hz | +0.03 Hz |
| Drop | 358.00 Hz | 359.23 Hz | +0.23 Hz |
| Mass | 290.00 Hz | 290.37 Hz | +0.37 Hz |

The correction was small for all three configurations, showing that the
record length was already sufficient to resolve the resonance accurately.

---

# 📊 Final Results

The final comparison of the three cantilever configurations is:

| Configuration | Natural Frequency (Hz) | Damping Ratio (ζ) | Quality Factor (Q) |
|---------------|-----------------------:|------------------:|-------------------:|
| Normal | 472.03 | 0.0030 | 168.5275 |
| Drop | 358.23 | 0.0021 | 236.9374 |
| Mass | 290.37 | 0.0015 | 326.8341 |

---

# 🔎 Results Analysis

## Normal Cantilever

\[
f_n = 472.03\ Hz
\]

\[
\zeta = 0.0030
\]

\[
Q = 168.5275
\]

The Normal cantilever had the highest natural frequency.

---

## Drop Cantilever

\[
f_n = 358.23\ Hz
\]

\[
\zeta = 0.0021
\]

\[
Q = 236.9374
\]

The Drop configuration showed a lower natural frequency than the Normal
cantilever.

---

## Mass Cantilever

\[
f_n = 290.37\ Hz
\]

\[
\zeta = 0.0015
\]

\[
Q = 326.8341
\]

The Mass cantilever had the lowest natural frequency and highest quality
factor.

---

# 📌 Main Observations

- Adding mass reduced the natural frequency.
- The Normal cantilever had the highest natural frequency.
- The Mass cantilever had the lowest natural frequency.
- All three configurations were lightly damped.
- The quality factor increased for the loaded configurations.
- The Mass cantilever had the highest quality factor.
- FFT provided the frequency-domain resonance peak.
- Peak Detection provided time-domain frequency and damping information.
- Zero-Crossing provided an independent time-domain frequency estimate.
- Parabolic Interpolation refined the FFT peak frequency.

---

# 👩‍💻 My Contribution

This was a **team engineering project**.

My main contribution was in the **signal-processing and data-analysis
part** of the project.

I contributed by:

- Developing and implementing the Fourier Transform (FFT) algorithm.
- Developing and implementing the Peak Detection algorithm.
- Developing and implementing the Zero-Crossing algorithm.
- Performing natural frequency analysis.
- Performing quality factor analysis.
- Comparing the different cantilever configurations.
- Preparing the results.
- Contributing to the technical report documentation.

---

# 🛠️ Tools & Technologies

| Tool / Technology | Application |
|-------------------|-------------|
| Python | Signal processing and analysis |
| Jupyter | Running analysis |
| NumPy | Numerical calculations |
| Matplotlib | Result visualization |
| PicoScope | Data acquisition |
| LTspice | Circuit simulation |
| KiCad | Circuit schematic |
| MCP6002 | Transimpedance amplifier |
| LM324 | Differential amplifier |
| Hamamatsu S3932 | Position Sensitive Detector |
| GitHub | Version control |

---

# 📁 Repository Structure

```text
Cantilever_Project/
│
├── Data_Sets_and_Codes/
│   ├── Normal_Cantilever/
│   ├── Drop_Cantilever/
│   └── Mass_Cantilever/
│
├── Experimental_Setup/
│   ├── Circuit_Schematic_Breadboard/
│   └── System_Overview/
│
├── Results/
│   ├── FFT/
│   ├── Peak_Detection_Method/
│   ├── Zero_Crossing_Method/
│   └── Parabolic_Interpolation_Method/
│
├── Documentation/
│   ├── Final_Report.pdf
│   └── Presentation/
│
└── README.md
```

---

# ✅ Conclusion

The cantilever vibration was successfully measured using an optical
lever and Position Sensitive Detector.

The analogue signal-conditioning circuit converted the PSD photocurrent
into a measurable voltage, which was acquired using PicoScope.

Python-based signal-processing methods were then used to determine the
natural frequency, damping ratio and quality factor.

The experimental results showed that adding mass to the cantilever
reduced its natural frequency.

At the same time, the quality factor increased for the loaded
configurations.

The project provided practical experience in:

- Optical measurement
- Position sensing
- Analogue electronics
- Circuit simulation
- Signal processing
- Python programming
- Vibration analysis
- Experimental data analysis
- Engineering documentation
- Teamwork

---

# 🤝 Team Project

This project was completed as a collaborative engineering project.

The team contributed across:

- Physical experimental setup
- Optical measurement
- Transimpedance amplifier design
- Differential amplifier design
- SPICE simulation
- Data collection
- Python signal processing
- Results analysis
- Technical documentation..
