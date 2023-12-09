# GaGNet: Glance and Glaze Network for Monaural Speech Enhancement

GaGNet is a deep learning-based technique for monaural speech enhancement that leverages the human hearing system's ability to focus on local information provided in the speech signal while capturing context or global features.

## Block Diagram
Overall diagram of the implemented technique is provided below: 

![GaGNetBD](https://github.com/mohammadr8za/Glance-and-Glaze-s-README/assets/72736177/6d2053f6-8425-48c4-bb2b-34d7810a426a)

## Table of Contents
- [Overview](#Overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Overview
As presented in the block diagram GaGNet comprises two main modules: Featrure Extraction Module (FEM) and a stack of Glanc-Glaze Modules (GGMs). 

**Input:** Speech (or generally audio) has various ways to be represented, going from raw time series to time-frequency representations. Selections of an approriate representation plays a crucial role in the overall performance of your system. In the time-frequency domain, spectrogram has been proved to be a useful choice. Spectrograms consist in 2D image-like structures representing sequences of Short Time Fourier Transform (STFT) with time and frequency and axes, while brightness shows the strength of each frequency component at each time. Spectrograms include magnitude and phase components that each of them includes useful information during the enhancement process. In this project, despite previous techniques adopting only magnitude of the spectrogram, both magnitude and phase are utilized to provide a comprehensive method for speech enhancement as it has been shown that phase-inclusion during speech enhancement improves the results.

**Feature Extraction Module (FEM):**
## Requirements

## Installation

## Usage

## Results

## Contributing

## License
