# Parabolic Interpolation of FFT Peak

## Overview

Parabolic interpolation was used to refine the dominant frequency obtained
from the FFT spectrum.

The FFT provides frequency values at discrete bins. Therefore, the actual
resonance frequency may lie between two FFT bins. To improve the frequency
estimate, the dominant FFT peak and its two neighbouring bins are used to
fit a parabola.

The refined peak is then used as the final frequency estimate.

---

## Algorithm

```text
Input Vibration Signal
        ↓
Remove DC Offset
        ↓
Apply Hann Window
        ↓
Calculate FFT
        ↓
Calculate Magnitude Spectrum
        ↓
Find Dominant Peak Bin (k)
        ↓
Select k-1, k and k+1
        ↓
Calculate Log Magnitude
        ↓
Fit Parabolic Curve
        ↓
Calculate Fractional Shift (δ)
        ↓
Calculate Refined Frequency
        ↓
Output Refined Natural Frequency
