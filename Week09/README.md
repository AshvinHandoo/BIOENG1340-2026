# Week 09 — Algebraic CT Reconstruction & Study Design

Topics: (1) reconstructing a hypothetical **4×4 attenuation image** (16 unknown $\mu$'s) from
**pencil X-ray beam** projections, exactly as **Hounsfield's EMI scanner** did — each ray is one
**Beer–Lambert equation**, and the stack of rays forms a linear system $A\,\boldsymbol\mu = \mathbf{p}$
that we solve; and (2) **cohort (sample) size determination** for a patient–control study.

> The CT **acquisition** material (scanner generations, the sinogram / Radon transform, and
> back-projection), the **Fourier theory** (Parseval + the Fourier Slice Theorem), and the head-to-head
> **comparison of reconstruction methods** (direct Fourier / FBP / algebraic) are all in
> **[Week 10](../Week10/)**.

## Contents

| File | Description |
|------|-------------|
| [AlgebraicReconstruction_4x4.ipynb](AlgebraicReconstruction_4x4.ipynb) | Runnable notes: pencil-beam Beer–Lambert equations, a worked **2×2 (4-unknown)** example solved by direct inverse and **OLS normal equations** $(A^\top A)^{-1}A^\top\mathbf b$, building the ray/path-length matrix $A$, rank deficiency of horizontal+vertical views, diagonal views to raise the rank, the leftover null-space **"ghost"**, direct **least-squares** and iterative **ART / Kaczmarz** reconstruction, and the effect of **Poisson photon noise** (dose vs quality). |
| [CohortSizeDetermination.ipynb](CohortSizeDetermination.ipynb) | Sample-size / power analysis for a patient–control study: Type I/II errors ($\alpha,\beta$) and **power**, the four levers, **Cohen's $d$**, sample size for **two means** (with power curves) and **two proportions**, **unequal allocation** (more controls per case), a **Monte-Carlo** power check, and practical **dropout** and **multiple-testing** corrections. |

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

### Cohort size determination

- **Errors & power**: $\alpha$ = false-positive rate (Type I), $\beta$ = false-negative rate
  (Type II), **power** $=1-\beta$ = chance of detecting a true effect (target 80–90%).
- **Four levers**: required $n$ grows with stricter $\alpha$, higher power, **smaller effect size**,
  and larger **variability** $\sigma$.
- **Effect size**: **Cohen's $d=|\mu_1-\mu_2|/\sigma$** for means; required $n\propto 1/d^2$ (halving
  the detectable effect roughly **quadruples** the cohort). Binary outcomes use a **two-proportion**
  formula (hardest near 50% and for small rate differences).
- **Allocation**: recruiting more controls per case lowers the number of hard-to-get cases, but never
  below half the balanced requirement.
- **In practice**: a **Monte-Carlo** simulation reproduces the analytic power; always round **up** and
  inflate for **dropout** ($n/(1-f)$) and **multiple testing** (Bonferroni $\alpha/m$).

## Environment

Uses Python with **NumPy**, **SciPy**, **scikit-image**, and **matplotlib**.
