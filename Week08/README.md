# Week 08 — X-ray & CT Image Formation

Fundamentals of X-ray and computed-tomography (CT) imaging: radiographs vs tomographic slices,
attenuation physics, X-ray energetics, beam hardening, and CT reconstruction from projections.

## Contents

| File | Description |
|------|-------------|
| [XrayCT_ImageFormation.ipynb](XrayCT_ImageFormation.ipynb) | Runnable notes: projection/radiograph as a sum of attenuation, the Beer–Lambert law ($I=I_0e^{-\int\mu\,dx}$), energy–wavelength ($E=hc/\lambda$), beam hardening (soft-tissue vs bone contrast), and CT reconstruction via the Radon transform (sinogram → filtered back-projection). |

## Key concepts

- **Radiograph = projection**: cumulative attenuation through the *whole* volume (no depth); a **CT slice** is one tomographic plane reconstructed from many projections.
- **Beer–Lambert law**: $dI=-\mu I\,dx \Rightarrow I=I_0 e^{-\int \mu\,dx}$; $\mu$ = linear attenuation coefficient (the contrast-forming tissue property).
- **$E=h\nu=hc/\lambda$**: shorter wavelength → higher energy → resolves finer gaps, but more ionizing.
- **Beam hardening**: high-energy ("hardened") beams image **bone** (soft tissue transparent); lower-energy ("soft") beams are needed for **soft-tissue** contrast.
- **CT**: projections at many angles + **inverse Radon transform** (filtered back-projection) → tomographic slice (Nobel Prize, 1979), mirroring MRI k-space projection reconstruction.
- X-ray/CT trade-off: **very high spatial resolution**, **poor soft-tissue contrast**; the alternative when MRI is contraindicated (e.g. metal implants).

## Environment

Uses Python with **NumPy**, **matplotlib**, and **scikit-image** (phantom, `radon`/`iradon`).
