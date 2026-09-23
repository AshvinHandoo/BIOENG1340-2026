# Week 03 — Image Filtering & Convolution as a Linear Operator

Spatial filtering and deconvolution in MATLAB, expressing convolution as a
matrix–vector product, and viewing images/derivatives in the frequency (k-space)
domain.

## Contents

| File | Description |
|------|-------------|
| [filteringImages.m](filteringImages.m) | Loads a DICOM slice, adds optional noise, and filters it. Demonstrates that convolution is a **linear operator** representable as $A x = b$ (kernel matrix $A$ times the vectorized image $x$ gives the blurred image $b$), then explores deconvolution in x-space. |
| [getConvMat.m](getConvMat.m) | Builds the convolution (Toeplitz-like) matrix `convMat` for a given kernel `h` and image, returning the matrix, the zero-padded image, and the convolved result. |
| Rendering.pdf | Slides / notes on rendering. |
| DelOperator.png, derivativesOfImageScalar.png | The del ($\nabla$) operator and image scalar-field derivatives. |
| KspaceToImageDomainTransformations.png | Relationship between k-space and the image domain. |
| Normals.png | Surface normals illustration. |

## Key concepts

- Convolution / correlation as spatial filtering (smoothing, noise)
- Convolution rewritten as a **matrix multiplication** $b = A x$ and the idea of
  **deconvolution** ($x = A^{-1} b$) and why it is ill-conditioned with noise
- Image gradients and the del operator $\nabla$
- The **k-space ↔ image-domain** (Fourier) relationship
