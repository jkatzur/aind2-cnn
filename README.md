# AIND Mini Projects Continued - Convolutional Neural Nets

## Motivation for CNNs
In this first project, we reviewed the challenges of MLPs and motivated CNNs...
* MLPs only take in a vector not a matrix. In many domains that works, but in image or video processing the distance between various points matters, and a vector has only 1d direction possible. Instead CNNs take a matrix as an input and understand the distance between points.
* Further, MLPs use fully connected layers. This provides rich ability to utilize prior knowledge across many layers, but it also makes processing take substantially longer. When dealing with very complex input (e.g images and movies) this is a huge overhead. Instead, CNNs introduce locally connected layers that bring in only the subsets of the layer most likely to impact the next one.

## Key Types of Convolutional Layers
* Convolutional Layers: these layers are the backbone of CNNs. They take input matrices, sets of filters, and classify the input based on the filters. They can be stacked together so, say, the first layers look for boundaries, then the next layers look for size of image, then the next layer looks at possible images of that size, etc... Importantly, over time in an algorithm we want the convolutional layers to gain more depth.
* Pooling Layers: these layers run on top of CNNs and their job is to reduce dimensionality. This improved computation performance and also helps avoid overfitting. This helps make sure that over time our layers have less width and height.
Intuitively, these combine to tell us that over time we want to move from questions like "what color are the pixels closest to this pixel" all the way to "are there wheels in this picture". More depth gets us further down that line, and reducing dimensionality helps prevent overfitting and focusing on specific pixels.

## Best Practices when Using CNNs
* Start with the data and split to training, validation, and testing (like in MLPs)
* Extend your training data with image augmentation. This ensures that you have images with different scales, angles, and location in the image for objects
* Go from Input Data --> Convolutional + Pooling Layers (typically alternating in a repeating pattern) --> Dense Layers --> Softmax for prediction. 

## Mini Project 1: Review Deep Neural Nets
In this first project at /mnist-mlp we used Multi-Layer-Perceptrons (MLPs) like in the prior unit to predict handwritten digits (e.g 0123456789). We were able to use this instead of CNNs because the images were small, simple, and highly conforming. We had a big enough data set, clean images, and consistent sizing so MLPs worked. Key takeaways from this project were:
* Validation split is important to increase accuracy. Validation_split gives us a subset of our training data for validation. At each step, we add a validation checkpoint which freezes the parameters, including epoch # and saves the validation scores - helping you determine which number of epochs and other parameters perform best. We don't use the eventual test data because this would bias the test
* Checkpoint and verbosity in the model allows us to understand how various models performed so that we can see if adding complexity is leading to overfitting or if the model actually requires it.

## Mini Project 2: Convolutional Visualization
In this mini project at /conv-visualization we began building intuition for convolutional neural layers. We showed what the filtered image looked like to get an intuition for what a filter does and how it gets applied to an image in practice. Post-filter, an image only has highlighted the area that applies to the filter. In this example we supplied the filters (vs having a CNN build it). We supplied 4 basic filters - representing horizontal and vertical boundaries so we could see how an image recognizes borders.

## Mini Project 3: Cifar Classification
In this project at /cifar-classification we put together the convolutional layers and the pooling layers to build an actual CNN. The goal was to identify the correct image from the Cifar database https://www.cs.toronto.edu/~kriz/cifar.html. Key takeaways here are:
* Best practice to alternate between convolutional layers and pool layers.
* You want convolutional layers to get deeper over time (so you can more accurately classify the correct image), and you want the pool layers to make sure the spatial information (e.g which pixel is next to which one) is reduced in dimensionality over time. You want the filters to bubble up information more like "it has wheels" than "these pixels are both red"
* After some number of convolutional layers we need to flatten and move to the Dense layers we saw before so that we can use softmax or sigmoid activation to turn the results into a probability

## Mini Project 4: Cifar Augmentation
In this project at /cifar-augmentation we extended our understanding to include the fact that images contain a lot of noise you need to separate to identify an object. Removing the noise breaks in to three main types:
* Scale invariance - how big the item is
* Angle invariance - what angle is the item
* Translation invariance - where in the image is the item
We handle these by augmenting our existing image database to include many possibilities of the image. The more we handle these items in the augmentation step the easier it is for the CNN to classify later. We can do this with a Python library called ImageDataGenerator that's in keras.

## Resources
Some great resources from the lessons in this section are:
* https://www.youtube.com/watch?v=AgkfIQ4IGaM&t=78s: Great video explaining how a CNN learns over it's multiple layers. Helps build good intuition for how the training actually occurs in practice
* https://experiments.withgoogle.com/ai/what-neural-nets-see: Continues the above intuition but includes an understanding of how this can be applied to art
* https://deepdreamgenerator.com/ example of ML driven art - how you can start with a base image and utilizing a trained networks ability to identify something else create a psychedelic hybrid image
* https://medium.com/merantix/picasso-a-free-open-source-visualizer-for-cnns-d8ed3a35cfc5: introducing Picasso, an open-source visualization framework for CNNs
