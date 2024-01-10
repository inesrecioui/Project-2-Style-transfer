# Project-2-Style-transfer

## Introduction
This code is implementing style transfer which is a technique that combines the content of one image with the artistic style of another to create a new image that merges both aspects.

## Code explanation:
### 1. (1-3) code cells:

* In the first code cell we are importing the packages and libraries we are going to use which are:

> * **PIL:** Image processing library in Python.
> * **Matplotlib:** Visualization library for plotting graphs and images.
> * **NumPy:** Library for numerical operations in Python.
> * **torch and torch.optim:** PyTorch libraries for machine learning and optimization.
> * **requests:** For handling HTTP requests.
> * **torchvision:** Part of PyTorch specifically for computer vision tasks and datasets. 

* On the second code cell we are loading the VGG19 tranfer leaning model by getting the model from tourchvision.models and then freezing it by setting "requires_grad" to False for every parameter in the VGG19 model we lock these parameters to ensure they won't change during training. This keeps their current values and prevents any updates while the model learns from new data.

* On the third code cell we are checking if CUDA-enabled GPU is available, if yes, we're gonna set the device to GPU by assigning the device variable to CUDA. Otherwise, it defaults to the CPU.

### 2. (4-7) code cells:

* On the forth cell we are creating a function to load an image from a local file path or a URL. If the image is accessed through a URL, it's retrieved via an HTTP request. Then we limited the image size to max_size. After that, we defined the transformation pipeline.

* On the fifth code cell we loaded two images: the first one is for the surprised cat meme (content) and the second one is for Andrea Patrisi painting (style).

* On the sixth code cell we created a helper function for un-normalizing an image and converting it from a Tensor image to a NumPy image for display.

* On the seventh one we displayed the images side-by-side

### 3. 8th cell:

We created a function called 'get_features', this function does this:

* **Layer Mapping:** Aligns PyTorch VGGNet layer names with those from a paper, crucial for image content and style extraction.

* **Default Layering:** If not specified, defaults to specific VGGNet convolutional layers.

* **Extracts Features:** Runs the input image through the model, extracting features from specified layers, storing them in a dictionary.

* **Output:** Returns a dictionary with image features extracted at specified model layers.

### 4. 9th cell:

We created another function called 'gram_metrix', this function computes the gram metrix for the tensor, by:

* **Tensor Dimensions:** Obtains the dimensions of the input tensor - batch size, depth, height, and width.
  
* **Reshaping Tensor:** Rearranges the tensor's shape to have depth as the first dimension.

* **Gram Matrix Calculation:** Computes the Gram Matrix by multiplying the tensor with its transpose and scales the result.

* **Normalization:** Divides the calculated Gram Matrix by the product of batch size, depth, height, and width to normalize the values.

* **Returns:** Provides the normalized Gram Matrix as the output.

### 5. 10th cell:

Now we are getting the content and style features only once before training. Then, we are gonna calculate the gram matrices for each layer of our style representation. After that, we created a third "target" image and prepared it for change

### 6. 11th cell:
Here, we are setting weights for each style layer, weighting earlier layers more will result in larger style artifacts, notice we are excluding `conv4_2` our content representation.

### 7. 12th cell:
Now we are trainig the model, and tweaking a picture by mixing its content and style. It repeats the process, adjusting the picture bit by bit to match the content and style desired. After some time, it displays the evolving image and reports how much it's changed.

### 8. Final cell
Finally we are displaying the content and final, target image and comparing them side-by-side

## summery:
We implemented VGG19-based style transfer code that blends image style and content for a unique merged image.
