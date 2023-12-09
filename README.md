# GaGNet: Glance and Gaze Network for Monaural Speech Enhancement

GaGNet is a deep learning-based technique for monaural speech enhancement that leverages the human hearing system's ability to focus on local information provided in the speech signal while capturing contextual or global features.

## Block Diagram
Overall diagram of the implemented technique is provided below: 

![GaGNetBD](https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/6d2053f6-8425-48c4-bb2b-34d7810a426a)

## Table of Contents
- [Overview](#Overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Overview
As presented in the block diagram GaGNet comprises two main modules: Featrure Extraction Module (FEM) and a stack of Glance-Gaze Modules (GGMs). 

**Input/Target:** Speech (or generally audio) has various ways to be represented, going from raw time series to time-frequency representations. Selection of an approriate representation plays a crucial role in the overall performance of your system. In the time-frequency domain, spectrogram has been proved to be a useful choice. Spectrograms consist in 2D image-like structures representing sequences of Short Time Fourier Transform (STFT) with time and frequency as axes, while brightness shows the strength of each frequency component at each time. Spectrograms include magnitude and phase components that each of them includes useful information during the enhancement process. In this project, despite previous techniques adopting only magnitude of the spectrogram, both magnitude and phase are utilized to provide a comprehensive method for speech enhancement as it has been shown that phase-inclusion during speech enhancement improves the results.

**Feature Extraction Module (FEM):** As its name suggests, this module aims at extracting features from inputs. To mitigate the problem of information loss due to consecutive downsampling operators in the previously suggested encoders (feature extractors) and the issue of overlooking contextual information caused by small kernel size, ispired by $U^{2}Net$ normal 2D convolutional layers are replaced by recalibrated encoder layers (RELs). FEM mainly consists of a 2D-GLU, instance normalization (IN), PReLU, and a UNet block with the residual connection as shown in the figure below. 
<p align="center">
  <img src="https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/8ef4e528-b243-4466-ad43-8007aad8e86d" alt="image" width="25%" height="60%">
</p>

**Glance-Gaze Module (GGM):** The motivation behind GGM is stemmed from the phusiological phenomenon that human can pay attention to both global and local components concurrently. So, two parallel block are designed accordingly, namely Glance Block (GLB) and Gaze Block (GAB). GLB estimates a gain function to suppress the noise in the magnitude domain, leading to the *glance* towards the overall spectrum. At the same time, GAB seeks a residual to repair the spectral details in the complex domain, which serves as the *gaze* operation. Both outputs are then applied to the collaborative reconstruction module (CRM) to obtain the spectrum estimation. Moreover, to adopt the multi-stage training strategy, multiple GGMs are repeatedly stacked and the RI (Real and Imaginary) components of current stage are iteratively updated based on that of the last stage. Structure of GLB and GAB are shown in Figure below. 

<p align="center">
  <img src="https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/dfc22d8c-e242-46d6-b272-e4b4d8443187" alt="image" width="50%" height="60%">
</p>

Note: In the figure, S-TCM stands for the Squeezed version of temporal convolutional module.

**Collaborative Reconstruction Module (CRM):** This module uses and combines the outputs of GGMs and estimates the RI spectrum as shown in the Figure below.

<p align="center">
  <img src="https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/d264d90b-d7b6-4d36-b177-21127c31674e" alt="image" width="25%" height="60%">
</p>

For more information, click [here](https://arxiv.org/abs/2106.11789).
## Requirements
- Python (version X.X)
- PyTorch (version X.X)
- Other dependencies:
  ```
  pip install -r requirements.txt
  ```
## Installation

## Usage

## Results

## Contributing

## License
