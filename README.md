# EEG Signal Noise Reduction Using SVD

A Linear Algebra Approach to Biomedical Signal Enhancement.

## Team Members

**Team 9**
* Manohar P
* Mrudula
* Sainath
* Pushpak

## Base Reference Paper

This project recreates and validates the results of the research paper:
* **Title:** SVD based technique for noise reduction in electroencephalographic signals
* **Authors:** P.K. Sadasivan, D. Narayana Dutt (Department of ECE, Indian Institute of Science, Bangalore)
* **Journal:** Signal Processing 55 (1996) 179-189 (Elsevier)
* **DOI:** [https://doi.org/10.1016/S0165-1684(96)00129-6](https://doi.org/10.1016/S0165-1684(96)00129-6)

## Project Outline

The objective is to extract weak Electroencephalogram (EEG) signals hidden within strong Electrooculogram (EOG/eye movement) artifacts using Singular Value Decomposition (SVD).

**Key Methodology:**
1. **Data Construction:** Modeling the observed signal as a linear combination of source signals (artifacts) and noise (pure EEG).
2. **SVD Decomposition:** Decomposing the data matrix into singular vectors and singular values.
3. **Subspace Separation:** Separating the Signal Subspace (high-energy EOG artifacts) from the Noise Subspace (containing the desired EEG).
4. **Reconstruction:** Reconstructing the clean EEG by projecting the data onto the noise subspace.

## Implementation Updates

The core algorithm has been implemented in MATLAB.
* **Simulation Environment:** Created simulation generating Alpha (10Hz) and Beta (20Hz) rhythms mixed with EOG artifacts (0-4Hz).
* **High-Fidelity Reproduction:** Successfully recreated the "EOG-Contaminated EEG" with an input SNR of -9.5 dB.
* **Results:** Achieved an Output SNR of approximately 13.83 dB to 19.16 dB, aligning with the reported results in the reference paper.

## Challenges Resolved

* **Sign Indeterminacy:** Implemented a correlation check to handle singular vectors with inverted signs.
* **Rank Estimation:** Set the artifact subspace rank based on energy dominance.
* **Noise Scaling:** Tuned sensor-to-signal power ratios for accurate SNR matching.

## Future Plans

* **Direct Data Acquisition:** Recording EEG and EOG data using laboratory equipment.
* **Public Dataset Validation:** Testing the implementation against the EEG Eye Artifact Dataset.

## Evaluation Details

* **Platform:** macOS
* **Hardware:** CPU
* **Environment:** MATLAB
