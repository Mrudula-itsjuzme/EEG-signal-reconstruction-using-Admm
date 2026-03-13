# D9_MFC4_SVD-BASED-NOISE-REDUCTION-IN-EEG-SIGNALS-
 A Linear Algebra Approach to Biomedical Signal Enhancement 


## 1. Team Members
**Team 9**
* **Manohar P** - [CB.SC.U4AIE24339]
* **Mrudula** - [CB.SC.U4AIE24340]
* **Sainath** - [CB.SC.U4AIE24309]
* **Pushpak** - [CB.SC.U4AIE24328]



## 2. Base/Reference Paper
This project attempts to recreate and validate the results of the following research paper:
* **Title:** *SVD based technique for noise reduction in electroencephalographic signals*
* **Authors:** P.K. Sadasivan, D. Narayana Dutt (Department of ECE, Indian Institute of Science, Bangalore)
* **Journal:** Signal Processing 55 (1996) 179-189 (Elsevier)
* **DOI/Source:** [https://doi.org/10.1016/S0165-1684(96)00129-6](https://doi.org/10.1016/S0165-1684(96)00129-6)

## 3. Project Outline
The objective of this project is to extract weak Electroencephalogram (EEG) signals hidden within strong Electrooculogram (EOG/eye movement) artifacts using Singular Value Decomposition (SVD).

**Key Methodology:**
1.  **Data Construction:** Modeling the observed signal as a linear combination of source signals (artifacts) and noise (pure EEG).
2.  **SVD Decomposition:** Decomposing the data matrix $M$ into singular vectors ($U, V$) and singular values ($\Sigma$).
3.  **Subspace Separation:**
    * **Signal Subspace:** Corresponds to the largest singular values (dominated by high-energy EOG artifacts).
    * **Noise Subspace:** Corresponds to the smaller singular values (containing the desired EEG).
4.  **Reconstruction:** Reconstructing the clean EEG by projecting the data onto the noise subspace, effectively filtering out the artifacts.

## 4. Updates
We have successfully implemented the core algorithm in MATLAB and verified the results against the reference paper.

* **Simulation Environment:** Created a simulation generating Alpha (10Hz) and Beta (20Hz) rhythms mixed with EOG artifacts (0-4Hz).
* **High-Fidelity Reproduction:** Successfully recreated the "EOG-Contaminated EEG" with an input SNR of -9.5 dB to match the paper's harsh testing conditions.
* **Algorithm Success:** Implemented the SVD projection and reconstruction.
    * **Result:** Achieved an Output SNR of **~13.83 dB** (1 Ref) and **~19.16 dB** (2 Refs), which aligns with and slightly exceeds the paper's reported ~10 dB.
* **Validation:** Generated Linear Prediction (LP) Spectra comparisons showing the successful removal of low-frequency artifact peaks while preserving Alpha/Beta rhythms.

## 5. Challenges / Issues Faced
During the implementation, we encountered and solved the following technical hurdles:
* **Sign Indeterminacy:** The SVD algorithm often returned singular vectors with inverted signs (a known mathematical property of SVD). This resulted in the reconstructed EEG being "upside down." We implemented a correlation check against the input to automatically flip the sign if necessary.
* **Rank Estimation:** Determining the exact rank ($r$) of the artifact subspace was critical. We found that since EOG power is significantly higher (~20x) than EEG, the first singular value almost always captured the artifact, allowing us to set $r=1$ for this simulation.
* **Noise Scaling:** Tuning the simulation to exactly match the -9.5 dB Input SNR required precise adjustment of the EOG-to-EEG power ratios, which we solved by normalizing the signal powers before mixing.

## 6. Future Plans
* **Getting our own dataset:** We plan to record our own EEG and EOG data using the equipment available in the Robotics Lab. This will allow us to test the algorithm on fresh, real-world biological signals.
* **Public Dataset Validation:** In addition to our own data, we will validate the SVD implementation using the **EEG Eye Artifact Dataset** hosted on Zenodo: https://zenodo.org/records/4002038.

## 7. Evaluation Details

- Platform used: mac
- Hardware: cpu
- Time taken: 273 s
- Environment: Matlab
