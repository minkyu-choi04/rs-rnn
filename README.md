# RS-RNN in Pytorch (Submitted to AAAI-22, Under review)
This repository contains the official implementation and pre-trained models for the retinal sampling recurrent neural network (RS-RNN). 
- ['Retinal Transformation and Recurrent Attention Improve Adversarial Robustness'](https://drive.google.com/file/d/1-2GsINBWSuITlfntbu3Z1t7QTb5pCv04/view?usp=sharing). 

Full code and data will be available soon. 

## Introduction
<p align="center">
    <img src="figures/intro.png" width= "800">
</p>

One of the most distinguished features of human vision from modern CNNs is adversarial robustness. While humans seems to be not affected by adversarial images, CNNs are vulnerable to the adversarial attacks. In this work, we try to discover sources of human robustness and improve machine vision's robustness by focusing on 1) eye movements, and 2) retinal sampling found in the visual systems of primates. 

Primates actively search for informative regions in the scene, while CNNs process all the image regions. Inspired by primate eye movements, we propose a novel framework that explores images by sequentially attending different regions of images (Figure a). 
However, the eye movement is not merely for choosing a region to crop. Instead, primate retina addresses the center of focus, while suppressing the peripheral regions. Once a fixation point is determined, our proposed model first transforms an image into a retinal image and processes it (Figure b).

As an example, assume that the model sequentially attends to a dog, a Frisbee and a person as shown in the figure. The retinal image corresponding to each object maintains the high resolution for the attended objects, but rest of the regions are downsampled. At each time step, RS-RNN receives information from a certain region and builds accumulated representations of an image by recurrent networks. Based on the representations, RS-RNN recognizes objects in an image and determines a location to look next. 

<p align="center">
    <img src="figures/model.png" width= "800">
</p>
The above figure (a) illustrates the model architecture. The model consists of convolutional encoders and gated recurrent units to process images. The attention module is further illustrated in (b), and its internal representations are shown in (c). 

Contributions
- a
- b
- c

## Results
To investigate effects of each design choices on adversarial robustness, baseline models are carefully chosen (Table 1). 
<p align="center">
    <img src="figures/table.png" width= "800">
</p>

RS-RNN and baseline models are evaluated under adversarial attack (PGD). 
<p align="center">
    <img src="figures/model.png" width= "800">
</p>
<p align="center">
    <img src="figures/table.png" width= "800">
</p>
<p align="center">
    <img src="figures/table.png" width= "800">
</p>
<p align="center">
    <img src="figures/table.png" width= "800">
</p>
