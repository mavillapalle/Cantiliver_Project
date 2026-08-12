# Zero-Crossing Method

## Overview

The zero-crossing method was implemented to determine the natural
frequency of the cantilever from its time-domain vibration signal.

The measured signal is first filtered to reduce noise. The algorithm then
detects the points where the signal crosses the zero-amplitude line.
Linear interpolation is used around each crossing to obtain a more
accurate crossing time.

## Algorithm

```text
Raw Signal
    ↓
Butterworth Filtering
    ↓
Detect Zero Crossings
    ↓
Select Two Neighbouring Points
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
