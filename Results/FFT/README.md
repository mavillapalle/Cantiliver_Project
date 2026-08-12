# Results

## Signal Processing and Data Analysis

The measured vibration signals from the cantilever were processed using
Python to determine the natural frequency and damping characteristics.

Three cantilever configurations were investigated:

- Normal Cantilever
- Drop Cantilever
- Mass Cantilever

The signal was analysed using different signal-processing techniques to
obtain and compare the vibration characteristics.

---

## 1. Fourier Transform (FFT)

The Fourier Transform was used to convert the measured vibration signal
from the time domain into the frequency domain. The dominant peak in the
frequency spectrum was used to determine the natural frequency of the
cantilever.

### Algorithm

```text
Raw Signal
    ↓
Remove DC Offset
    ↓
Apply Hann Window
    ↓
Fast Fourier Transform (FFT)
    ↓
Calculate Magnitude Spectrum
    ↓
Find Dominant Peak
    ↓
Natural Frequency
