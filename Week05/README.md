# Week 05 — MR Physics: Larmor Frequency & Gyromagnetic Ratio

Introduction to nuclear magnetic resonance: spin precession, the Larmor equation,
and computing the proton gyromagnetic ratio from measured data.

## Contents

| File | Description |
|------|-------------|
| [GyromagneticRatio.ipynb](GyromagneticRatio.ipynb) | Computes the proton gyromagnetic ratio $\gamma$ from the Larmor equation $\omega = \gamma B_0$ given $B_0 = 2.35\ \text{T}$ and a resonance frequency of 100 MHz, with explicit unit conversions (MHz → Hz, cyclic → angular frequency), and compares against the CODATA value. |
| Precession-WheelExperiment_PaulCallaghan.mp4 | Sir Paul Callaghan's spinning-wheel demonstration of precession. |

## Key concepts

- **Larmor equation**: $\omega_{\text{Larmor}} = \gamma B_0$ and $f_{\text{Larmor}} = \dfrac{\gamma}{2\pi} B_0$
- Unit conversions: MHz → Hz, cyclic frequency $f$ → angular frequency $\omega = 2\pi f$
- Proton gyromagnetic ratio: $\gamma \approx 2.675\times10^{8}$ rad s$^{-1}$ T$^{-1}$, i.e. $\gamma/2\pi \approx 42.58$ MHz/T
- A 2.35 T field corresponds to the classic **100 MHz** proton NMR system

## References — Paul Callaghan MRI/NMR video lectures

Sir Paul Callaghan's video series on the principles of NMR and MRI:

- Playlist: <https://www.youtube.com/watch?v=jUKdVBpCLHM&list=PLbMizTOj9NEmNUhHHi08cZKTeMAnpO2En&index=2>
