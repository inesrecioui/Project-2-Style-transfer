# Project-2-Style-transfer

## Introduction
This code is implementing style transfer which is a technique that combines the content of one image with the artistic style of another to create a new image that merges both aspects.

## Code explanation:
### 1. (1-3) code cells:

* In the first code cell we are importing the packages and libraries we are going to use which are:

**PIL:** Image processing library in Python.
**Matplotlib:** Visualization library for plotting graphs and images.
**NumPy:** Library for numerical operations in Python.
**torch and torch.optim:** PyTorch libraries for machine learning and optimization.
**requests:** For handling HTTP requests.
**torchvision:** Part of PyTorch specifically for computer vision tasks and datasets. 

* On the second code cell we are loading the VGG19 tranfer leaning model by getting the model from tourchvision.models and then freezing it by setting "requires_grad" to False for every parameter in the VGG19 model we lock these parameters to ensure they won't change during training. This keeps their current values and prevents any updates while the model learns from new data.

* On the third code cell we are checking if CUDA-enabled GPU is available, if yes, we're gonna set the device to GPU by assigning the device variable to CUDA. Otherwise, it defaults to the CPU.

### 2. (4-7) code cells:

* On the forth cell we are creating a 
