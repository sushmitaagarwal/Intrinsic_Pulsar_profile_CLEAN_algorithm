## CLEAN-based Deconvolution of Scatter-Broadened Pulsar Profiles
### Overview

This repository contains a Python implementation of a CLEAN-based deconvolution algorithm to recover intrinsic pulsar pulse profiles affected by interstellar scattering. The approach follows the methodology introduced by Bhat et al. (2003) and later refinements, using iterative CLEAN components, pulse broadening functions (PBFs), and physically motivated stopping criteria as described in Bathula et al. 2025.

The code demonstrates the full pipeline: **profile simulation + scattering + noise injection → CLEAN decomposition → Intrinsic Profile restoration**.

### Scientific Motivation
Radio pulses from pulsars are temporally broadened due to multi-path propagation in the interstellar medium (ISM). This scattering distorts pulse shapes and biases timing measurements. The CLEAN-based approach treats scattering as a convolution process and iteratively removes the scattering response to recover the intrinsic profile.

### Key Features
- Simulation of **two-component intrinsic pulse profiles**
- Thin-screen **pulse broadening function (PBF)** modeling
- Instrumental response convolution
- Iterative **CLEAN decomposition** with loop gain control
- FFT-based **off-pulse RMS estimation**
- Physically motivated **3σ stopping criterion**
- Restoration using Gaussian CLEAN components
- Extensive diagnostic and convergence plots

### Method Overview
The observed profile is modeled as:


### Code Structure
- **Profile generation**: Multi-Gaussian intrinsic pulses
- **Scattering model**: One-sided exponential PBF
- **System response**: PBF ⊗ instrumental response
- **Noise injection**: Controlled by user-defined SNR
- **CLEAN loop**:
    - Peak detection
    - Component subtraction
    - Residual tracking
- **Restoration**: Gaussian restoring function + final residual

### Outputs
The code produces:
- Intrinsic, scattered, and observed pulse profiles
- Dirty beam and instrumental response plots
- CLEAN component distributions
- Iterative residual evolution
- Convergence diagnostics
- Final recovered intrinsic profile comparison

All figures are saved in publication-ready PDF format.

### Requirements
    Python ≥ 3.8
    NumPy
    SciPy
    Matplotlib

### Usage
Run the script directly after setting:
  - Number of bins
  - Scattering timescale (tau_sc)
  - Signal-to-noise ratio (snr)
  - CLEAN loop gain and thresholds

The code is modular and can be adapted for:

  - Different PBF models
  - Alternative stopping criteria
  - Real pulsar data inputs

### Limitations
- Currently optimized for only two-gaussian pulsar profile
- Performance degrades at low S/N
- Assumes circular convolution (FFT-based)
- Currently uses a single thin-screen PBF
- Not yet optimized for large-scale batch processing


### Future Extensions
- Simulation for multi-component intrinsic pulse profiles
- Multiple PBF models (thick screen, truncated screen)
- Automated τ_sc optimization using figure-of-merit curves
- Application to wideband and real PSRFITS data
- Computational optimization

References
- Bhat, N. D. R., Cordes, J. M., & Chatterjee, S. (2003), ApJ, 584, 782, DOI 10.1086/345775
- A. Bathula, M. A. Krishnakumar, and S. Jena, (2025), https://arxiv.org/abs/2511.22299v1
- Bracewell, R. (1965), The Fourier Transform and Its Applications
