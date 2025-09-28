# Physiological Signal-Based Sleep Apnea Detection

This project implements an automated pipeline for detecting **sleep apnea events** from physiological signals using both classical machine learning and deep learning models. The work is based on the MIT-BIH Polysomnographic Database (PhysioNet).

---

## Project Overview
Sleep apnea is a common sleep disorder characterized by repeated pauses in breathing. Traditional diagnosis with polysomnography is accurate but costly and inconvenient. This project explores a cost-effective, wearable-signal–based solution for automated detection.

We used:
- Electrocardiography (ECG)
- Electroencephalography (EEG)
- Oxygen Saturation (SpO₂)

The models were trained to classify segments into **apnea vs. non-apnea events**.

---

## Methodology

1. **Data Source**  
   - MIT-BIH Polysomnographic Database (via PhysioNet).  
   - Includes ECG, EEG, SpO₂, and detailed apnea annotations.  

2. **Signal Preprocessing**  
   - Bandpass filtering (0.5–40 Hz for ECG).  
   - R-R peak detection using Pan–Tompkins algorithm / NeuroKit2.  
   - SpO₂ desaturation events analyzed from oximeter readings.  
   - EEG spectrograms generated from 30s windows.  

3. **Feature Engineering and Selection**  
   - Extracted statistical features (mean, variance, RMS, skew, kurtosis, etc.) from ECG R-R intervals and SpO₂ signals.  
   - EEG band powers (delta, theta, alpha, beta, gamma).  
   - Mann–Whitney U-test applied to confirm discriminative features.  

4. **Models**  
   - Random Forest Classifier on handcrafted features.  
   - ResNet-18 CNN on recurrence plots (ECG) and spectrograms (EEG).  

---

## Results

### Classical Machine Learning
- Random Forest (combined features): **83% accuracy**.  
- Important features: SpO₂ max/zero-crossing rate, ECG R-R median.

### Deep Learning
- ResNet-18 (ECG recurrence plots): ~77% accuracy.  
- ResNet-18 (EEG spectrograms): ~74% accuracy.  

---

## Tech Stack
- Python  
- Libraries: NumPy, Pandas, Matplotlib, SciPy, scikit-learn, PyTorch, NeuroKit2  

---

## Future Work
- Extend to multi-class classification (obstructive apnea, central apnea, hypopnea).  
- Deploy lightweight models for wearable healthcare devices.  
- Real-time inference optimization for streaming signals.  

---

## Author
Afia Zuhaira  
Tasnim Islam
Graduate Student, Computer Science, UMBC  

---

## Acknowledgments
- PhysioNet for providing the MIT-BIH Polysomnographic Database.  
- NeuroKit2 library for ECG preprocessing tools.  
- UMBC Neural Engineering coursework for project guidance.  

---


