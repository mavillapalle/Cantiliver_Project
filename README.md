# Cantilever Characterisation Using Position Sensitive Detector

## 📌 Project Overview

This project focuses on the experimental characterisation of a
cantilever using an optical lever measurement system.

The main aim was to measure the free-vibration response of a cantilever
and determine its:

- Natural Frequency
- Damping Ratio
- Quality Factor

A laser beam was reflected from the vibrating cantilever onto a
Position Sensitive Detector (PSD). The PSD output was converted into a
voltage using analogue signal-conditioning circuits. The signal was
then acquired using PicoScope and analysed using Python.

Three cantilever configurations were investigated:

- Normal Cantilever
- Drop Cantilever
- Mass Cantilever

The complete system combines optical measurement, analogue electronics,
data acquisition and digital signal processing.

---

# 🎯 Objectives

The main objective was to develop an optical-lever measurement chain
capable of capturing the free-vibration response of a cantilever.

The project objectives were:

- Set up the optical lever measurement system.
- Detect small cantilever movements using a PSD.
- Convert the PSD photocurrent into a measurable voltage.
- Design and test the Transimpedance Amplifier.
- Extract the differential signal using a differential amplifier.
- Acquire the signal using PicoScope.
- Process the measured signal using Python.
- Determine the natural frequency.
- Determine the damping ratio.
- Calculate the quality factor.
- Compare different cantilever configurations.
- Cross-check the vibration results using different signal-processing
  methods.

The project was designed to obtain frequency and damping information from
both time-domain and frequency-domain measurements. :contentReference[oaicite:1]{index=1}

---

# 🔬 System Overview

The complete measurement chain is:

```text
                    OPTICAL PATH
                        
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
              ELECTRICAL PATH
  ↓
Transimpedance Amplifier (TIA)
  ↓
Differential Amplifier
  ↓
PicoScope
  ↓
Python Signal Processing
```

The laser is directed onto the cantilever.

When the cantilever vibrates, the reflected laser beam moves across the
PSD.

The PSD converts the laser spot movement into photocurrents.

The Transimpedance Amplifier converts these small photocurrents into
voltage signals.

The differential amplifier combines the two signals to produce the
measurement output.

The output is acquired using PicoScope and analysed using Python.

This optical-to-electrical signal chain is the central measurement
system used in the project. :contentReference[oaicite:2]{index=2}

---

# ⚙️ Experimental Setup

## Main Components

- Laser diode module
- Steering mirrors
- Microcantilever
- Hamamatsu S3932 Position Sensitive Detector
- MCP6002 operational amplifier
- LM324 operational amplifier
- Transimpedance Amplifier
- Differential Amplifier
- PicoScope
- Optical breadboard
- LTspice
- KiCad
- Python / Jupyter

The physical setup used optical posts, kinematic mirror mounts, a fixed
cantilever clamp and a vibration-damped optical breadboard. :contentReference[oaicite:3]{index=3}

---

# 💡 Optical Lever Principle

The measurement is based on the law of reflection.

When a laser beam strikes a reflective surface:

\[
\theta_i = \theta_r
\]

### What does this mean?

The angle at which the laser hits the mirror is equal to the angle at
which it is reflected.

Where:

- \(\theta_i\) = angle of incidence
- \(\theta_r\) = angle of reflection

When the cantilever rotates by a small angle \(\theta\), the reflected
beam rotates by approximately twice that angle:

\[
\theta_r = 2\theta
\]

This means a very small cantilever movement produces a larger movement
of the laser spot at the detector.

If the detector is placed at a distance \(D\), the approximate laser
spot displacement is:

\[
x \approx 2D\theta
\]

Where:

- \(x\) = displacement of the laser spot
- \(D\) = distance between the reflecting surface and PSD
- \(\theta\) = angular displacement of the cantilever

### In simple terms

```text
Small Cantilever Rotation
          ↓
Reflected Beam Rotates
          ↓
Laser Spot Moves More
          ↓
PSD Detects the Movement
```

This is why the optical lever can detect very small cantilever
vibrations.

The report describes this reflection principle and the doubled reflected
angle in the experimental theory. :contentReference[oaicite:4]{index=4}

---

# 📡 Position Sensitive Detector

The Position Sensitive Detector converts the position of the laser spot
into electrical currents.

The PSD has two output currents:

\[
I_{x1}
\]

and

\[
I_{x2}
\]

The laser position is calculated using:

\[
x =
\frac{l_x}{2}
\frac{I_{x1}-I_{x2}}
{I_{x1}+I_{x2}}
\]

### What does this formula mean?

The numerator:

\[
I_{x1}-I_{x2}
\]

tells us how different the two currents are.

The denominator:

\[
I_{x1}+I_{x2}
\]

normalises the measurement based on the total detected current.

The resulting value gives the position of the laser spot on the PSD.

Where:

- \(x\) = laser spot position
- \(l_x\) = length of the PSD resistive layer
- \(I_{x1}\) = current from the first electrode
- \(I_{x2}\) = current from the second electrode

This PSD position equation is given in the project report. :contentReference[oaicite:5]{index=5}

---

# 📐 Cantilever Natural Frequency

Natural frequency is the frequency at which the cantilever naturally
vibrates after it is disturbed.

For a uniform cantilever beam, the first-mode natural frequency is:

\[
f_1 =
\frac{1}{2\pi}
\beta_1^2
\sqrt{\frac{EI}{mL^4}}
\]

Where:

- \(f_1\) = first natural frequency
- \(\beta_1 = 1.875\) for the first vibration mode
- \(E\) = Young's modulus
- \(I\) = area moment of inertia
- \(m\) = mass per unit length
- \(L\) = cantilever length

### Effect of mass

The important relationship for this project is:

```text
Additional Mass
      ↓
Higher Effective Inertia
      ↓
Lower Natural Frequency
```

This behaviour was observed experimentally: the Normal cantilever had
the highest frequency, while the Mass cantilever had the lowest. :contentReference[oaicite:6]{index=6}

---

# 🌊 Damping

When the cantilever is tapped and released, it vibrates freely.

The amplitude gradually decreases because energy is lost through
damping mechanisms such as friction and drag.

The damped vibration can be represented as:

\[
x(t)=Ae^{-\delta t}
\cos(\omega_dt+\phi)
\]

### What does this equation show?

The cosine part:

\[
\cos(\omega_dt+\phi)
\]

represents the oscillation.

The exponential part:

\[
e^{-\delta t}
\]

represents the decrease in amplitude over time.

Where:

- \(x(t)\) = displacement at time \(t\)
- \(A\) = initial amplitude
- \(\delta\) = damping constant
- \(\omega_d\) = damped angular frequency
- \(\phi\) = initial phase
- \(t\) = time

---

# 📉 Logarithmic Decrement

Logarithmic decrement describes how quickly the vibration amplitude
decreases from one peak to another.

For two successive peaks:

\[
\Lambda =
\ln\left(\frac{x_1}{x_2}\right)
\]

Where:

- \(x_1\) = first peak amplitude
- \(x_2\) = next peak amplitude
- \(\Lambda\) = logarithmic decrement

If the peaks are separated by \(n\) cycles:

\[
\Lambda =
\frac{1}{n}
\ln\left(\frac{x_1}{x_{n+1}}\right)
\]

### Simple interpretation

```text
Large Peak
    ↓
Smaller Peak
    ↓
Smaller Peak
    ↓
Smaller Peak
```

The faster the amplitude decreases, the greater the damping.

---

# 📊 Damping Ratio

The damping ratio tells us how strongly the cantilever vibration is
damped.

It is calculated from logarithmic decrement as:

\[
\zeta =
\frac{\Lambda}
{\sqrt{4\pi^2+\Lambda^2}}
\]

Where:

- \(\zeta\) = damping ratio
- \(\Lambda\) = logarithmic decrement

For a lightly damped system, the damping ratio is small.

The measured cantilevers had damping ratios in approximately the
\(0.001\) to \(0.003\) range. :contentReference[oaicite:7]{index=7}

---

# 🔄 Natural Angular Frequency

The natural frequency can also be written as angular frequency:

\[
\omega_n = 2\pi f_n
\]

Where:

- \(\omega_n\) = natural angular frequency in rad/s
- \(f_n\) = natural frequency in Hz

### Example

If:

\[
f_n = 472.03\ Hz
\]

then the corresponding angular frequency is obtained by multiplying the
frequency by \(2\pi\).

---

# ⚙️ Damping Constant

The damping constant is related to damping ratio and natural angular
frequency:

\[
\delta = \zeta\omega_n
\]

Where:

- \(\delta\) = damping constant
- \(\zeta\) = damping ratio
- \(\omega_n\) = natural angular frequency

This connects the measured damping behaviour to the natural frequency
of the cantilever.

---

# ⭐ Quality Factor

The quality factor \(Q\) describes the sharpness of the resonance.

For a lightly damped system:

\[
Q = \frac{1}{2\zeta}
\]

Where:

- \(Q\) = quality factor
- \(\zeta\) = damping ratio

### What does a high Q mean?

```text
Low Damping
     ↓
Less Energy Lost
     ↓
Sharper Resonance
     ↓
Higher Q
```

The report also expresses quality factor using stored and lost energy:

\[
Q =
2\pi
\frac{E_{\text{stored}}}
{E_{\text{lost per cycle}}}
\]

Where:

- \(E_{\text{stored}}\) = energy stored in the cantilever
- \(E_{\text{lost per cycle}}\) = energy lost during one vibration cycle

The increase in Q observed in the loaded configurations corresponds to
narrower resonance bandwidths. :contentReference[oaicite:8]{index=8}

---

# 🔌 Signal Conditioning

## Transimpedance Amplifier

The PSD produces very small photocurrents.

The Transimpedance Amplifier converts the photocurrent into a voltage
signal.

The basic relationship is:

\[
V_{out}=-I_{in}R_f
\]

Where:

- \(V_{out}\) = output voltage
- \(I_{in}\) = input photocurrent
- \(R_f\) = feedback resistance

The project used:

\[
R_f = 100\,k\Omega
\]

A feedback capacitor was also investigated to improve the amplifier
stability and frequency response.

---

# 📶 TIA Bandwidth

The approximate bandwidth relationship used for the TIA is:

\[
BW =
\frac{1}{2R_fC_{PSD}}
\]

Where:

- \(BW\) = approximate bandwidth
- \(R_f\) = feedback resistance
- \(C_{PSD}\) = PSD capacitance

### Design trade-off

```text
Higher Feedback Resistance
          ↓
Higher Gain
          ↓
Lower Basic Bandwidth
```

LTspice was used to investigate the PSD equivalent circuit and select
suitable feedback components.

---

# ➖ Differential Amplifier

The two TIA channels produce two voltage signals:

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

Where:

- \(V_A\) = first TIA output
- \(V_B\) = second TIA output
- \(V_{out}\) = differential output

The differential output is used as the final vibration measurement
signal.

An LM324 was used for the differential stage.

The report states that the TIA and differential amplifier together
provided the required measurable output for further signal processing.
:contentReference[oaicite:9]{index=9}

---

# 🧪 SPICE Simulation

LTspice was used to simulate the PSD and Transimpedance Amplifier.

A 1D Pi-network equivalent circuit was used to represent the S3932 PSD.

The simulation was used to investigate:

- PSD behaviour
- Feedback resistor selection
- Feedback capacitor selection
- Frequency response
- Transient response
- Circuit stability

The final hardware schematic was created in KiCad.

---

# 💻 Signal Processing

The acquired vibration signal was processed using Python.

Four signal-processing techniques were investigated:

1. Fourier Transform (FFT)
2. Peak Detection
3. Zero-Crossing
4. Parabolic Interpolation

The report includes separate flowcharts and results for each of these
methods. :contentReference[oaicite:10]{index=10}

---

# 1️⃣ Fourier Transform (FFT)

FFT converts the measured vibration signal from the time domain into the
frequency domain.

The Discrete Fourier Transform is:

\[
X_k =
\sum_{n=0}^{N-1}
x_n e^{-j2\pi kn/N}
\]

Where:

- \(x_n\) = measured signal sample
- \(X_k\) = frequency-domain value
- \(N\) = total number of samples
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
Find Dominant Peak
    ↓
Natural Frequency
```

The dominant FFT peak represents the main resonance frequency.

## FFT Results

| Configuration | FFT Frequency |
|---------------|--------------:|
| Normal | 474.0 Hz |
| Drop | 358.3 Hz |
| Mass | 290.7 Hz |

These are the FFT frequencies reported for the three configurations.
:contentReference[oaicite:11]{index=11}

---

# 2️⃣ Peak Detection Method

The peak detection method analyses the signal directly in the time
domain.

The raw signal is first filtered.

Local maxima are then detected.

The time between successive peaks gives the vibration period.

The natural frequency is:

\[
f_n = \frac{1}{T}
\]

Where:

- \(f_n\) = natural frequency
- \(T\) = vibration period

### In simple terms

If one vibration cycle takes more time:

```text
Longer Period
     ↓
Lower Frequency
```

If one vibration cycle takes less time:

```text
Shorter Period
     ↓
Higher Frequency
```

## Peak Detection Algorithm

```text
Raw Signal
    ↓
Band-Pass Filtering
    ↓
Detect Local Peaks
    ↓
Average Time Between Peaks
    ↓
Calculate Period T
    ↓
Calculate Natural Frequency
    ↓
Calculate Logarithmic Decrement
    ↓
Calculate Damping Ratio
```

This follows the peak-detection flow used in the report. :contentReference[oaicite:12]{index=12}

### Damping from Peak Amplitudes

The amplitude of the detected peaks decreases as the cantilever
oscillation decays.

The logarithmic decrement is calculated from the peak amplitudes:

\[
\Lambda =
\frac{1}{n}
\ln\left(\frac{x_1}{x_{n+1}}\right)
\]

The damping ratio can then be estimated from the logarithmic decrement.

---

# 3️⃣ Zero-Crossing Method

The zero-crossing method provides another time-domain estimate of the
natural frequency.

The signal is first filtered using a Butterworth filter.

The algorithm then identifies where the signal crosses the zero-amplitude
line.

Because the actual zero crossing can occur between two sampled points,
linear interpolation is used.

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
Calculate Time Difference
    ↓
Calculate Average Period
    ↓
Calculate Natural Frequency
```

### Linear Interpolation

The zero-crossing time is estimated using:

\[
t_0 =
t_1-\frac{v_1}{m}
\]

Where:

- \(t_0\) = estimated zero-crossing time
- \(t_1\) = time of the neighbouring point
- \(v_1\) = signal value at that point
- \(m\) = slope between the two neighbouring points

### Frequency

The period is obtained from alternating zero crossings:

\[
T=t_{i+2}-t_i
\]

Then:

\[
f_n=\frac{1}{T}
\]

### Why use zero crossing?

It provides an independent time-domain frequency estimate that can be
compared with the FFT and peak-detection results.

---

# 4️⃣ Parabolic Interpolation

The FFT provides frequency values at discrete frequency bins.

Therefore, the actual resonance peak may lie between two FFT bins.

Parabolic interpolation is used to refine the position of the FFT peak.

## Algorithm

```text
FFT Magnitude Spectrum
        ↓
Find Peak Bin k
        ↓
Take k-1, k and k+1
        ↓
Calculate ln(|X|)
        ↓
Fit Parabola
        ↓
Find Parabola Vertex
        ↓
Calculate Fractional Shift
        ↓
Calculate Refined Frequency
```

The report specifically uses the logarithm of the FFT magnitude at
\(k-1\), \(k\), and \(k+1\), then calculates the vertex offset. :contentReference[oaicite:13]{index=13}

### Parabolic Fit

The three log-magnitude points are:

\[
L_{k-1},\quad L_k,\quad L_{k+1}
\]

The fitted parabola can be written as:

\[
y=ax^2+bx+c
\]

The position of the parabola vertex is:

\[
\delta^*=-\frac{b}{2a}
\]

This value represents the fractional shift of the FFT peak.

### Refined Frequency

The refined frequency is:

\[
f_{\text{refined}}
=
(k+\delta^*)\Delta f
\]

Where:

- \(k\) = FFT peak-bin index
- \(\delta^*\) = fractional peak shift
- \(\Delta f\) = frequency resolution of the FFT
- \(f_{\text{refined}}\) = refined frequency

### Why is this useful?

```text
Discrete FFT Peak
       ↓
Peak may be between bins
       ↓
Fit Parabola
       ↓
Find Exact Peak Position
       ↓
Refined Frequency
```

This reduces the small frequency error caused by the discrete FFT bins.

---

# 📈 Parabolic Interpolation Results

| Configuration | Discrete Peak | Refined Peak | Correction |
|---------------|--------------:|-------------:|-----------:|
| Normal | 472.00 Hz | 472.03 Hz | +0.03 Hz |
| Drop | 358.00 Hz | 359.23 Hz | +0.23 Hz |
| Mass | 290.00 Hz | 290.37 Hz | +0.37 Hz |

The corrections were small and below one FFT-bin width. The refined
values were therefore used as the final frequency estimates. :contentReference[oaicite:14]{index=14}

---

# 📊 Final Results

The final comparison of the three cantilever configurations is:

| Configuration | Natural Frequency (Hz) | Damping Ratio (ζ) | Quality Factor (Q) |
|---------------|-----------------------:|-------------------:|-------------------:|
| Normal | 472.03 | 0.0030 | 168.5275 |
| Drop | 358.23 | 0.0021 | 236.9374 |
| Mass | 290.37 | 0.0015 | 326.8341 |

These values are the final comparison reported in Table 5 of the latest
project report. :contentReference[oaicite:15]{index=15}

---

# 🔎 Results Analysis

## Normal Cantilever

Natural frequency:

\[
f_n=472.03\ Hz
\]

Damping ratio:

\[
\zeta=0.0030
\]

Quality factor:

\[
Q=168.5275
\]

The Normal cantilever had the highest natural frequency.

---

## Drop Cantilever

Natural frequency:

\[
f_n=358.23\ Hz
\]

Damping ratio:

\[
\zeta=0.0021
\]

Quality factor:

\[
Q=236.9374
\]

The Drop cantilever showed a lower natural frequency than the Normal
configuration.

---

## Mass Cantilever

Natural frequency:

\[
f_n=290.37\ Hz
\]

Damping ratio:

\[
\zeta=0.0015
\]

Quality factor:

\[
Q=326.8341
\]

The Mass cantilever had the lowest natural frequency and highest quality
factor.

---

# 📌 Main Observations

### Natural Frequency

```text
Normal
472.03 Hz
   ↓
Drop
358.23 Hz
   ↓
Mass
290.37 Hz
```

Adding mass reduced the natural frequency because the effective inertia
of the system increased.

### Quality Factor

```text
Normal
Q = 168.5275
   ↓
Drop
Q = 236.9374
   ↓
Mass
Q = 326.8341
```

The quality factor increased for the loaded configurations.

The report relates the higher Q to greater stored energy relative to
energy lost through friction and drag, and to a narrower resonance
bandwidth. :contentReference[oaicite:16]{index=16}

---

# 🛠️ Tools & Technologies

| Tool / Technology | Purpose |
|-------------------|---------|
| Python | Signal processing and data analysis |
| Jupyter | Running analysis code |
| NumPy | Numerical calculations |
| Matplotlib | Plotting results |
| PicoScope | Data acquisition |
| LTspice | Circuit simulation |
| KiCad | Hardware schematic |
| MCP6002 | Transimpedance stage |
| LM324 | Differential amplifier |
| Hamamatsu S3932 | Position Sensitive Detector |
| GitHub | Version control |

The report identifies LTspice for PSD/TIA simulation, KiCad for the final
hardware schematic, GitHub for maintaining the codebase, and VS Code/Jupyter
for running the Python signal-processing code. :contentReference[oaicite:17]{index=17}

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
│   ├── Optical_Setup/
│   ├── Circuit_Diagram/
│   ├── Schematic/
│   └── Breadboard/
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

# 👩‍💻 My Contribution

This was a **team engineering project**.

My main contribution was focused on **data analysis and signal
processing**.

I:

- Developed and implemented the Fourier Transform algorithm.
- Developed and implemented the Peak Detection algorithm.
- Developed and implemented the Zero-Crossing algorithm.
- Performed natural frequency analysis.
- Performed quality factor analysis.
- Compared the different cantilever configurations.
- Prepared the project results.
- Contributed to the technical report documentation.

This contribution is explicitly listed in the final team contribution
section of the project report. :contentReference[oaicite:18]{index=18}

---

# 🤝 Team Project

This project was completed collaboratively.

The team contributed across:

- Physical experimental setup
- Optical measurement
- Data collection
- Transimpedance amplifier design
- Differential amplifier design
- SPICE validation
- Schematic development
- Signal processing
- Results analysis
- Technical documentation

---

# ✅ Conclusion

The cantilever vibration response was successfully measured using an
optical lever and Position Sensitive Detector.

The PSD photocurrent was converted into a measurable voltage using the
Transimpedance Amplifier and differential amplifier stages.

The conditioned signal was acquired using PicoScope and analysed using
Python.

Four signal-processing methods were investigated:

- Fourier Transform
- Peak Detection
- Zero-Crossing
- Parabolic Interpolation

The final results showed that adding mass to the cantilever reduced its
natural frequency:

\[
472.03\ Hz
\rightarrow
358.23\ Hz
\rightarrow
290.37\ Hz
\]

At the same time, the quality factor increased:

\[
168.5275
\rightarrow
236.9374
\rightarrow
326.8341
\]

Overall, the project demonstrated a complete measurement and analysis
chain for experimentally characterising cantilever vibration.
