# Bearing Anomaly Detection (Vibration-Based Early Warning)

Predictive maintenance project by Ibrahim Almanla, mechanical maintenance engineer (12+ years in cement and power generation, vibration analysis CAT I).

## Goal
Detect developing bearing faults early from vibration data, to allow planned instead of emergency maintenance.

## Method
1. Extract condition indicators per measurement: RMS, kurtosis, peak, crest factor
2. Train an Isolation Forest on healthy data only
3. Set the alarm limit on separate healthy validation data (avoids data leakage)
4. Smooth the anomaly score (moving average) and require consecutive exceedances
5. Evaluate lead time and false alarms

## Status
- [x] Pipeline on synthetic data (first alarm 15 measurements after fault onset, 0 false alarms)
- [ ] Real data: NASA IMS Bearing Dataset (run-to-failure)
- [ ] Spectrum (FFT) based features
