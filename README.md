# Generative Oversampling with GAN and CycleGAN

**Authors**: Alessandro Soccol, Marco Cosseddu, Giovanni Murgia  
**Institution**: University of Cagliari

## Abstract

This project explores the use of Generative Adversarial Networks (GAN) and CycleGAN to generate synthetic data for oversampling in binary classification tasks. The goal is to determine whether using generative models can improve classification performance compared to traditional augmentation techniques.

![demo_gans](https://github.com/user-attachments/assets/34e22c67-ac01-4428-8ca6-a06cf4e63395)

## Table of Contents

1. [Project Overview](#project-overview)
2. [Objectives](#objectives)
3. [Project Phases](#project-phases)
4. [Results](#results)
5. [Conclusions](#conclusions)
6. [References](#references)

## Project Overview

The core question of this project is: _Does generating new samples using GAN or CycleGAN models provide better performance compared to classical augmentation techniques?_ To answer this, we applied these models to datasets containing cats and dogs, analyzing the results in terms of classifier performance.

### Architecture

The project uses the following structure:
- **Preprocessing**
- **Binary Classifier**
- **GAN for Upsampling**
- **CycleGAN for Domain Transfer**

## Objectives

We aimed to address several specific objectives:
1. **Generate new instances**: We used two GAN models—one generating cats, and another generating dogs.
2. **Apply CycleGAN**: We transformed data from one domain to another to generate new examples.
3. **Evaluate performance**: We evaluated classifier performance using both original and generated data.
4. **Assess GAN effectiveness**: We examined whether GAN and CycleGAN-based oversampling provided better performance than classical augmentation.

## Project Phases

The project was divided into several concurrent phases:
1. **Binary Classifier**: We used a pre-trained EfficientNetB0 model for classification, with fine-tuning for binary tasks.
2. **GAN Training**: We trained two separate GANs, one for generating cats and another for dogs.
3. **CycleGAN Training**: We used CycleGAN to perform domain transfer between cats and dogs.
4. **Results Collection**: Results were gathered and presented through performance metrics like accuracy, F1-score, precision, and recall.

## Results

### GAN Training

- **Generator Architecture**: 6,258,659 total parameters
- **Discriminator Architecture**: 1,149,890 total parameters

We faced several challenges:
- Training time and resource constraints
- Hyperparameter tuning (batch size, noise dimension, weight initialization, dropout rate, etc.)
- Dataset limitations

### Binary Classifier Results

The classifier was trained with both balanced and imbalanced datasets using traditional augmentation and generated data for comparison. The results are summarized below:

| Dataset          | Loss  (Train) | F1-Score (Train) | F1-Score (Test) |
|------------------|---------------|------------------|-----------------|
| Balanced         | 0.250         | 0.891            | 0.859           |
| Imbalanced (Cats)| 0.269         | 0.887            | 0.853           |
| Augmented (Cats) | 0.257         | 0.890            | 0.857           |
| Generated (Cats) | 0.257         | 0.891            | 0.854           |

### CycleGAN Results

CycleGAN was used to transfer data between domains (cats to dogs and vice versa). However, we encountered challenges with insufficient computational resources, and the results indicated that CycleGAN was not optimal for our specific oversampling goal.

## Conclusions

- **GANs for oversampling**: While GAN-generated samples can improve the quality of the dataset, their effectiveness depends heavily on the dataset's characteristics. In the case of the cat dataset, GAN oversampling resulted in more stable training curves.
- **CycleGAN limitations**: CycleGAN, while conceptually promising for domain transfer, was not effective due to resource constraints and the specific nature of our problem.
- **Final assessment**: Generative models can be beneficial for oversampling, but their application is highly resource-intensive. For most practical purposes, traditional augmentation remains a more viable option unless significant computational resources are available.

## References

- GAN: [Generative Adversarial Networks Paper](https://arxiv.org/pdf/1406.2661.pdf)
- CycleGAN: [CycleGAN Paper](https://arxiv.org/pdf/1703.10593.pdf)
- Binary Classifier: [EfficientNet Paper](https://arxiv.org/pdf/1905.11946.pdf)
