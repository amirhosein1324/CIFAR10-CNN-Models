# Comparative Analysis of CNN Models on CIFAR-10 Dataset

## Introduction

This project explores the performance of three distinct Convolutional Neural Network (CNN) architectures — LeNet-5 , AlexNet , and VGG16 which trained on the CIFAR-10 dataset. The goal is to compare their accuracy, loss convergence , and computational efficiency over a fixed training duration of 3 epochs.

## Methodology

### 1. Dataset & Preprocessing

- Dataset: CIFAR-10 (60,000 32x32 color images in 10 classes).
- LeNet-5: Inputs are kept at the native 32x32 resolution. Data augmentation (RandomCrop , RandomHorizontalFlip) is applied.
- AlexNet & VGG16: Inputs are upscaled to 227x227 to match the original architecture specifications. No heavy augmentation was observed in the AlexNet script, while VGG16 used standard normalization.

### 2. Hyperparameters

All models were trained with the following consistent settings:
- Epochs: 3
- Batch Size : 64
- Optimizer: SGD (Stochastic-Gradient-Descent)
- Learning Rate: 0.01
- Momentum : 0.9

### 3. Architecture Overview
| Model   | Layers              | Input Size | Characteristics                                                                 |
|---------|---------------------|------------|----------------------------------------------------------------------------------|
| LeNet-5 | 7 (2 Conv, 3 FC)     | 32×32      | Shallow network, originally designed for MNIST. Very fast to train.              |
| AlexNet | 8 (5 Conv, 3 FC)     | 227×227    | Deeper than LeNet, uses ReLU and Dropout. Significant jump in parameters.         |
| VGG16   | 16 (13 Conv, 3 FC)   | 227×227    | Very deep, uses uniform 3×3 convolutions. Extremely parameter-heavy.              |

### 4. Results Comparison
after 3 epochs :
| Metric          | LeNet-5 | AlexNet | VGG16     |
|-----------------|---------|---------|-----------|
| Final Accuracy  | 51.27%  | 71.30%  | 71.54%   |
| Final Loss      | 1.3524  | 0.9769  | 1.1914   |
| Time per Epoch  | ~21 seconds | Moderate | ~15 minutes |

Analysis:
- LeNet-5: struggled to capture complex features in only 3 epochs, achieving ~51% accuracy. However, it was extremely efficient, taking only seconds to train.
- AlexNet: showed a massive improvement over LeNet, jumping to 71.30% accuracy. It provided the best balance between performance and training speed.
- VGG16: achieved the highest accuracy (71.54%), but the gain over AlexNet was negligible (+0.24%) relative to the massive increase in computational cost (taking ~15 minutes per epoch vs. seconds/minutes for the others).

### 5. Conclusion
For the CIFAR-10 dataset restricted to a short training cycle (3 epochs):
- AlexNet is the most efficient choice, offering high accuracy without the extreme computational overhead of VGG16.
- VGG16 is likely overkill for this specific setup, as the resizing to 227x227 introduces significant computational load for marginal accuracy gains in early epochs.
- LeNet-5 is insufficient for high accuracy on this dataset but serves as a good baseline for speed testing.


Thanks for reading (:







