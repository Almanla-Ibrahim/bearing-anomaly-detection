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
## Results (NASA IMS Bearing Dataset)

| Test | Fault | Simple RMS threshold | Isolation Forest |
|---|---|---|---|
| 2nd (10 min sampling) | Outer race, bearing 1 | alarm 76.3 h before end | 74.8 h |
| 3rd (30 min sampling) | Outer race, bearing 3 | alarm 136.0 h before end | 134.5 h |

Alarm limit = maximum of the smoothed score on unseen healthy data; alarm requires 3 consecutive exceedances. Lead time is measured to the end of the recording, not to an exact failure time.

## Findings
- Both methods give days of warning with zero false alarms on the validation window.
- A simple RMS threshold performed as well as Isolation Forest on these two runs (within 1.5 h). The multi-feature model is not better on strong outer-race faults.

## Next
- [ ] Test 1 (inner race and roller element faults), where RMS may react later
- [ ] FFT / envelope spectrum features

## Tools
Python, NumPy, SciPy, scikit-learn, Matplotlib
