# Week 08 — X-ray & CT Image Formation

Fundamentals of X-ray and computed-tomography (CT) imaging: radiographs vs tomographic slices,
attenuation physics, X-ray energetics, beam hardening, and CT reconstruction from projections.

## Contents

| File | Description |
|------|-------------|
| [XrayCT_ImageFormation.ipynb](XrayCT_ImageFormation.ipynb) | **Lecture 1.** Runnable notes: projection/radiograph as a sum of attenuation, the Beer–Lambert law ($I=I_0e^{-\int\mu\,dx}$), energy–wavelength ($E=hc/\lambda$), beam hardening (soft-tissue vs bone contrast), and CT reconstruction via the Radon transform (sinogram → filtered back-projection). |
| [LectureNotes_XrayPhysics_Dosimetry.ipynb](LectureNotes_XrayPhysics_Dosimetry.ipynb) | **Lecture 2.** The physics behind the picture: discrete serial-block attenuation, discrete vs continuous Beer–Lambert, the **polyenergetic X-ray spectrum** (photon flux, mean energy, tungsten characteristic peaks), **beam hardening**, ionization (photoelectric $\propto Z^3/E^3$ vs Compton), energy-dependent soft/hard tissue separability, **half-value layer** ($\text{HVL}=0.693/\mu$), linear vs **mass attenuation** ($\mu/\rho$), and **Hounsfield units** with windowing and contrast agents. |

## Key concepts

- **Radiograph = projection**: cumulative attenuation through the *whole* volume (no depth); a **CT slice** is one tomographic plane reconstructed from many projections.
- **Beer–Lambert law**: $dI=-\mu I\,dx \Rightarrow I=I_0 e^{-\int \mu\,dx}$; $\mu$ = linear attenuation coefficient (the contrast-forming tissue property).
- **$E=h\nu=hc/\lambda$**: shorter wavelength → higher energy → resolves finer gaps, but more ionizing.
- **Beam hardening**: high-energy ("hardened") beams image **bone** (soft tissue transparent); lower-energy ("soft") beams are needed for **soft-tissue** contrast.
- **CT**: projections at many angles + **inverse Radon transform** (filtered back-projection) → tomographic slice (Nobel Prize, 1979), mirroring MRI k-space projection reconstruction.
- X-ray/CT trade-off: **very high spatial resolution**, **poor soft-tissue contrast**; the alternative when MRI is contraindicated (e.g. metal implants).

### Lecture 2 additions (X-ray physics & dosimetry)

- **Serial-block model**: a beam path crosses several tissues; the projection is the aggregate line integral $\sum_i\mu_i\Delta x$ — the number of blocks sets how many $\mu_i$ reconstruction must solve for.
- **Discrete ↔ continuous Beer–Lambert**: photon-count removal $n\to n-\Delta n$ is equivalent to intensity $I=I_0e^{-\mu x}$ with the same $\mu$.
- **Polyenergetic spectrum**: X-ray tubes emit a *range* of energies (bremsstrahlung continuum + tungsten characteristic peaks ~59 keV). **Photon flux** = area under $S(E)$; **mean energy** $\bar E=\int E\,S\,dE/\int S\,dE$.
- **Beam hardening**: filtration removes low-energy ("soft") photons, raising mean energy — lowers dose, reduces soft-tissue contrast. Soft = low energy, hard = high energy.
- **Ionization** (threshold ~13.6 eV; diagnostic X-rays 12–124 keV; γ-rays MeV): **photoelectric effect** $\propto Z_\text{eff}^3/E^3$ (bone conspicuity at low kVp) and **Compton scattering** $\propto$ electron density.
- **Energy dependence of $\mu$**: separability of bone vs soft tissue is largest at low energy (the "white mouse" vs "bony mouse").
- **Half-value layer**: $\text{HVL}=\ln 2/\mu=0.693/\mu$ — energy-specific thickness that halves the photon count.
- **Linear vs mass attenuation**: $\mu$ (cm$^{-1}$) rises with density/electron density; $\mu/\rho$ (cm$^2$/g) removes the density effect.
- **Hounsfield units**: $\text{HU}=1000(\mu-\mu_\text{water})/\mu_\text{water}$ (water 0, air ≈ −1000); **bright = high $\mu$**; **iodine** contrast raises $\mu$ to highlight vessels. Windowing (center/width) reveals soft-tissue vs bone.
- *Next class*: CT-number ranges, the **EMI scanner** history, **algebraic reconstruction**, and contrast agents.

## Environment

Uses Python with **NumPy**, **matplotlib**, and **scikit-image** (phantom, `radon`/`iradon`).
