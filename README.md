# Structured-Illumination-Microscopy-
Self Project 
Structured Illumination Microscopy (SIM): Image Simulation and Reconstruction

Author: Kshitij Bajpai, Sophomore IIT BOMBAY 


Implementation: Python 

Project Overview
This project provides a complete computational model of the 2D linear Structured Illumination Microscopy (SIM) pipeline. SIM is a super-resolution technique that overcomes the diffraction limit of light, achieving approximately double the spatial resolution of conventional wide-field microscopy.


The simulation begins with a high-resolution ground-truth image, generates a series of low-resolution images with sinusoidal illumination patterns, and computationally reconstructs a final super-resolved image. The entire process is implemented in Python, utilizing libraries like NumPy and SciPy for Fourier analysis.



The core principle demonstrated is how patterned illumination creates Moiré fringes, which down-modulate high-frequency spatial information into the observable range of the microscope's Optical Transfer Function (OTF). This information is then computationally recovered and repositioned, effectively extending the OTF and enhancing resolution.






Code: The Python code for this project can be found in the following Google Colab notebook: https://colab.research.google.com/drive/19YP6u3mPhHtZFfdPMmEBWXYQ0f3Ezmn?usp=sharing.

Key Features

End-to-End Pipeline: Simulates the entire SIM workflow from ground truth image creation to final super-resolved image reconstruction.




Frequency Domain Analysis: Utilizes 2D Fast Fourier Transforms (FFT) to visualize and manipulate image frequency components in k-space.




Resolution Enhancement: Demonstrates a nearly two-fold improvement in spatial resolution over conventional widefield imaging.



Noise Robustness Testing: Evaluates the reconstruction fidelity under realistic imaging conditions by simulating both Poisson (photon shot) and Gaussian (sensor) noise.

Methodology
The simulation methodology is broken down into the following key steps:


Ground Truth (GT) Image Generation:

A 512x512 pixel test image (

skimage.data.camera) is used as the high-resolution ground truth.

A 50-pixel scale bar is added to provide a reference for measuring resolution improvement.

Widefield Simulation (Low-Pass Filtering):

A circular low-pass filter with a cutoff frequency of 0.25x Nyquist is applied in the Fourier domain to simulate the diffraction limit of a conventional microscope.


This results in a blurred, low-resolution "widefield" image.

Structured Illumination Simulation:

The widefield image is illuminated with sinusoidal grating patterns at three different angles (0°, 60°, 120°).

This produces three modulated images containing Moiré fringes, which encode high-frequency details.


Fourier Transform Analysis:

The 2D FFT is applied to the modulated images, revealing distinct sidebands in the frequency spectrum that carry the high-frequency information shifted into the observable range.


Frequency Component Separation:

The central (low-frequency) and sideband (high-frequency) components of the modulated images are isolated in the Fourier domain using a mask.


High-Resolution Image Reconstruction:

The separated sidebands are shifted back to their correct positions in Fourier space.

All components are combined to form an extended OTF.


An inverse FFT is applied to produce the final, super-resolved SIM image.

Noise Simulation and Analysis:

Gaussian and Poisson noise are added to the modulated images to test the algorithm's robustness.

The simulation shows that while reconstruction quality degrades slightly, the SIM process remains robust to moderate noise levels.

Results
The simulation successfully demonstrates the super-resolution capability of SIM.

<img width="1064" height="385" alt="image" src="https://github.com/user-attachments/assets/ffc8d758-ad01-422d-a9c9-532246cd00df" />


The reconstructed image clearly restores fine details that were lost in the blurred widefield image, and the extended frequency coverage is visible in the final combined Fourier spectrum.
