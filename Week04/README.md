# Week 04 — SNR & CNR

Signal-to-noise ratio (SNR) and contrast-to-noise ratio (CNR): building synthetic
images, measuring per-region SNR/CNR, testing statistical distinguishability, and
recovering contrast by signal averaging.

## Contents

| File | Description |
|------|-------------|
| [GenerateTwoCircles.ipynb](GenerateTwoCircles.ipynb) | Generates a synthetic image with two circles of distinct `int8` intensities using SimpleITK, adds different noise per region, saves clean/noisy/label images, computes per-region SNR and pairwise CNR (manual NumPy vs SimpleITK `LabelStatisticsImageFilter`), and runs Welch's t-test on each region pair. |
| [GenerateTwoCircles-SuperNoisy.ipynb](GenerateTwoCircles-SuperNoisy.ipynb) | A high-noise / small-image variant where the regions are *not* statistically distinguishable (large p-values), then generates 50 noisy samples, **averages** them, and shows SNR/CNR and significance recovered ($\propto\sqrt{N}$). |
| [OptimizingSNR_CNR.ipynb](OptimizingSNR_CNR.ipynb) | Illustrates the lesson that high SNR does not imply high CNR, and that for an exponentially decaying signal $S(k,t)=S_0e^{-kt}$ the contrast/sensitivity to the tissue property $k$ is maximized at $t_0 = 1/k$. |
| PixelsVoxls-CNR-SNR.pdf, optimizingCNR-SNR.pdf | Lecture slides. |
| `output/` | Generated NIfTI images (clean, noisy, labels, averaged) and the 50-sample stack. |

## Key concepts

- $\mathrm{SNR} = S/\sigma$ (measurement precision) vs $\mathrm{CNR} = (S_1-S_2)/\sigma$ (tissue discrimination)
- Per-region statistics via label maps; manual vs library agreement
- **Welch's t-test** on region pixels: is the mean difference zero?
- **Signal averaging** reduces noise by $\sqrt{N}$, raising SNR/CNR
- Optimal measurement time $t_0 = 1/k$ for an exponentially decaying signal

## Environment

Notebooks use Python with **SimpleITK**, **NumPy**, **matplotlib**, and **SciPy**
(installed into the notebook kernel on first run).
