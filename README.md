# GaGNet: Glance and Gaze Network for Monaural Speech Enhancement
<div align="justify">
  GaGNet is a deep learning-based technique for monaural speech enhancement that leverages the human hearing system's ability to focus on local information provided in the speech signal while capturing contextual or global features.
</div>


## Block Diagram
<div align="justify">
  Overall diagram of the implemented technique is provided below: 
</div>


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
<div align="justify">
  As presented in the block diagram GaGNet comprises two main modules: Featrure Extraction Module (FEM) and a stack of Glance-Gaze Modules (GGMs). 
</div>


<div align="justify">
  <b>Input/Target:</b> Speech (or generally audio) has various ways to be represented, going from raw time series to time-frequency representations. Selection of an approriate representation plays a crucial role in the overall performance of your system. In the time-frequency domain, spectrogram has been proved to be a useful choice. Spectrograms consist in 2D image-like structures representing sequences of Short Time Fourier Transform (STFT) with time and frequency as axes, while brightness shows the strength of each frequency component at each time. Spectrograms include magnitude and phase components that each of them includes useful information during the enhancement process. In this project, despite previous techniques adopting only magnitude of the spectrogram, both magnitude and phase are utilized to provide a comprehensive method for speech enhancement as it has been shown that phase-inclusion during speech enhancement improves the results.
</div>

<div align="justify"> 
  <b>Feature Extraction Module (FEM):</b> As its name suggests, this module aims at extracting features from inputs. To mitigate the problem of information loss due to consecutive downsampling operators in the previously suggested encoders (feature extractors) and the issue of overlooking contextual information caused by small kernel size, ispired by U<sup>2</sup>Net normal 2D convolutional layers are replaced by recalibrated encoder layers (RELs). FEM mainly consists of a 2D-GLU, instance normalization (IN), PReLU, and a UNet block with the residual connection as shown in the figure below. 
</div>
<p align="center">
  <img src="https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/8ef4e528-b243-4466-ad43-8007aad8e86d" alt="image" width="25%" height="60%">
</p>

<div align="justify"> 
  <b>Glance-Gaze Module (GGM):</b> The motivation behind GGM is stemmed from the phusiological phenomenon that human can pay attention to both global and local components concurrently. So, two parallel block are designed accordingly, namely Glance Block (GLB) and Gaze Block (GAB). GLB estimates a gain function to suppress the noise in the magnitude domain, leading to the <i>glance</i> towards the overall spectrum. At the same time, GAB seeks a residual to repair the spectral details in the complex domain, which serves as the <i>gaze</i> operation. Both outputs are then applied to the collaborative reconstruction module (CRM) to obtain the spectrum estimation. Moreover, to adopt the multi-stage training strategy, multiple GGMs are repeatedly stacked and the RI (Real and Imaginary) components of current stage are iteratively updated based on that of the last stage. Structure of GLB and GAB are shown in Figure below. 
</div>
<p align="center">
  <img src="https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/dfc22d8c-e242-46d6-b272-e4b4d8443187" alt="image" width="50%" height="60%">
</p>

<div align="justify"> 
  Note: In the figure, S-TCM stands for the Squeezed version of Temporal Convolutional Module.
</div>


<div align="justify"> 
  <b>Collaborative Reconstruction Module (CRM):</b> This module uses and combines the outputs of GGMs and estimates the RI spectrum as shown in the Figure below.
</div>
<p align="center">
  <img src="https://github.com/mohammadr8za/Glance-and-Gaze-README/assets/72736177/d264d90b-d7b6-4d36-b177-21127c31674e" alt="image" width="25%" height="60%">
</p>

For more information, click [here](https://arxiv.org/abs/2106.11789).
## Requirements
- Python (version X.X)
- Torch (version X.X)
- Other dependencies:
  ```
  pip install -r requirements.txt
  ```
## Installation
Clone the repository using the following command:
```
git clone https://github.com/USERNAME/REPOSITORY.git
```

## Usage
1. Prepare your speech dataset
2. Train the GaGNet model using the provided training script:
   ```
   python train.py --dataset PATH_TO_DATASET --parameters OTHER_PARAMETERS
   ```
3. Evaluate the trained model on a test dataset:
   ```
   pyhton evaluate.py --dataset PATH_TO_TEST_DATASET --model PATH_TO_TRAINED_MODEL
   ```

## Results
We have extensively tested and evaluated GaGNet in different versions (by changing number of Glance-Gaze blocks (Q) and groups of S-TCMs (P), and compared it with other state-of-the-art speech enhancement methods. The results demonstrate that GaGNet provides competitive performance in terms of effectiveness and efficiency, providing enhanced speech quality. 

## Contributing
We welcome contributions from the community! If you would like to contribute to GaGNet, please follow these steps:
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Commit your changes and push your branch to your fork.
4. Submit a pull request with a detailed description of your changes.

## License
Ⓒ 2023 X. All rights reserved. 
