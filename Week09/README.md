# Week 09 — Algebraic Reconstruction (solving for the $\mu$'s)

Reconstructing a hypothetical **4×4 attenuation image** (16 unknown $\mu$'s) from **pencil X-ray
beam** projections, exactly as **Hounsfield's EMI scanner** did: each ray is one **Beer–Lambert
equation**, and the stack of rays forms a linear system $A\,\boldsymbol\mu = \mathbf{p}$ that we solve.

## Contents

| File | Description |
|------|-------------|
| [AlgebraicReconstruction_4x4.ipynb](AlgebraicReconstruction_4x4.ipynb) | Runnable notes: pencil-beam Beer–Lambert equations, a worked **2×2 (4-unknown)** example solved by direct inverse and **OLS normal equations** $(A^\top A)^{-1}A^\top\mathbf b$, building the ray/path-length matrix $A$, rank deficiency of horizontal+vertical views, diagonal views to raise the rank, the leftover null-space **"ghost"**, direct **least-squares** and iterative **ART / Kaczmarz** reconstruction, and the effect of **Poisson photon noise** (dose vs quality). |

## Key concepts

- **One beam = one equation**: Beer–Lambert $I=I_0e^{-\sum_i\mu_i\Delta x}$ becomes, after taking the
  log, a linear **weighted sum** $p=-\ln(I/I_0)=\sum_i\mu_i\Delta x$. Weights are **path lengths** (1
  for axis-aligned, $\sqrt2$ for diagonal rays).
- **System matrix**: each ray is a row of $A$ over the 16 flattened pixels; the measurements form
  $A\,\boldsymbol\mu=\mathbf p$.
- **Minimum equations**: like fitting a line ($y=\beta_0+\beta_1x$, 2 unknowns) needs 2 points, 16
  unknown $\mu$'s need ≥ 16 **independent** equations; more than 16 gives a least-squares best fit.
  Hounsfield's **EMI scanner** did this at scale (~180 angles × 160 measurements per slice).
- **Rank & orientations**: a 4×4 image needs ≥ 16 **independent** equations. Horizontal + vertical
  rays alone give rank 7 (badly underdetermined); adding **diagonal / anti-diagonal** views raises the
  rank to 15.
- **Null-space "ghost"**: with only four orientations, one checkerboard image produces zero signal on
  every ray, so any multiple of it can be added without changing the projections — the reason real CT
  acquires **many angles**.
- **Reconstruction**: a **direct least-squares** solve and the iterative **ART / Kaczmarz** row-action
  update converge to the same image; ART is the historical EMI-scanner method.
- **Noise & dose**: photon counts are Poisson, $I\sim\text{Poisson}(I_0e^{-p})$; lower incident flux
  $I_0$ (less dose) → noisier projections → worse reconstruction — the CT dose/quality trade-off.

## Environment

Uses Python with **NumPy** and **matplotlib** only.
