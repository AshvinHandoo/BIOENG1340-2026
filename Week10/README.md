# Week 10 — CT Reconstruction Methods (Fourier, FBP & Algebraic)

The head-to-head study of **how** a sinogram becomes an image, building on the Week 09 acquisition and
algebraic-reconstruction material. Two notebooks: the **Fourier theory** that underpins CT, and a
**comparison** of the three reconstruction families.

## Contents

| File | Description |
|------|-------------|
| [FourierTheory_Parseval_CT.ipynb](FourierTheory_Parseval_CT.ipynb) | The Fourier basis of CT: 1D/2D Fourier transforms and k-space, **Parseval's theorem** (energy conservation, verified to round-off) and its meaning for SNR/filtering, the **Fourier Slice Theorem** (1D FFT of a projection = a radial line of the image's 2D FFT), and why polar sampling forces the **ramp filter** in FBP. |
| [ReconstructionMethods_Compare.ipynb](ReconstructionMethods_Compare.ipynb) | Head-to-head of three reconstructions on a Shepp–Logan phantom: **direct Fourier** (gridding), **filtered back-projection**, and **algebraic (SART)** — compared with full views, **sparse views** (where SART beats FBP's streaks), and **noisy** projections, with RMSE metrics and a speed-vs-robustness trade-off table. |

## Key concepts

- **Parseval's theorem**: total energy is conserved between the spatial and frequency domains
  ($\sum|x_n|^2=\tfrac1N\sum|X_k|^2$) — the basis for reasoning about SNR and how filtering removes a
  measurable fraction of image energy.
- **Fourier Slice Theorem**: the 1D FFT of a projection at angle $\theta$ is a **radial line** of the
  image's 2D FFT. Many angles fill k-space → inverse 2D FFT returns the image.
- **Ramp filter**: projections sample k-space in polar form, oversampling the center ($\sim1/|k|$); the
  ramp $|k|$ cancels this — the analytic core of **filtered back-projection**.
- **Method trade-off**: **direct Fourier** and **FBP** are fast (FBP accurate with dense, clean data;
  naive Fourier shows gridding artifacts), while iterative **ART/SART** is slower but far more robust
  to **sparse views** and **noise** — the reason modern scanners use iterative reconstruction.

## Prerequisites

Builds on Week 09: [AlgebraicReconstruction_4x4.ipynb](../Week09/AlgebraicReconstruction_4x4.ipynb)
(the $A\boldsymbol\mu=\mathbf p$ system) and
[CTScanners_Sinogram_BackProjection.ipynb](../Week09/CTScanners_Sinogram_BackProjection.ipynb)
(sinogram, Radon transform, and back-projection).

## Environment

Uses Python with **NumPy**, **SciPy**, **scikit-image**, and **matplotlib**.
