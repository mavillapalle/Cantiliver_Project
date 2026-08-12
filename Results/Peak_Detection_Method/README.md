# Peak Detection Method

## Overview

The peak detection method was used to determine the natural frequency
and damping behaviour of the cantilever from its time-domain vibration
response.

The measured signal is first filtered to reduce unwanted noise. The
algorithm then identifies the local maxima of the vibration signal.
The time difference between consecutive peaks is used to determine the
vibration period and natural frequency.

The decay of the peak amplitudes is also analysed to estimate the damping
behaviour.

## Algorithm

```text
Raw Signal
    ↓
Signal Filtering
    ↓
Detect Local Peaks
    ↓
Calculate Peak-to-Peak Time
    ↓
Calculate Average Period
    ↓
Calculate Natural Frequency
    ↓
Analyse Amplitude Decay
    ↓
Calculate Damping
