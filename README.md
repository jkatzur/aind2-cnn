# AIND Mini Projects Continued - Convolutional Neural Nets

## First Mini Project: Review Deep Neural Nets
In this first project at /mnist-mlp we used Multi-Layer-Perceptrons (MLPs) like in the prior unit to predict handwritten digits (e.g 0123456789). We were able to use this instead of CNNs because the images were small, simple, and highly conforming. We had a big enough data set, clean images, and consistent sizing so MLPs worked. Key takeaways from this project were:
* Validation split is important to increase accuracy. Validation_split gives us a subset of our training data for validation. At each step, we add a validation checkpoint which freezes the parameters, including epoch # and saves the validation scores - helping you determine which number of epochs and other parameters perform best. We don't use the eventual test data because this would bias the test
* Checkpoint and verbosity in the model allows us to understand how various models performed so that we can see if adding complexity is leading to overfitting or if the model actually requires it.

## Motivation for CNNs
Briding the first and second project here, we reviewed the challenges of MLPs and motivated CNNs...
* MLPs only take in a vector not a matrix. In many domains that makes sense, but in image or video processing the distance between various points matters, and a vector has only 1d direction possible. Instead CNNs take a matrix as an input and understand the distance between points.
* Further, MLPs use fully connected layers. This provides rich ability to utilize prior knowledge across many layers, but it also makes processing take substantially longer. When dealing with very complex input (e.g images and movies) this is a huge overhead. Instead, CNNs introduce locally connected layers that bringi n only the subsets of the layer most likely to impact the next one.

## Key Types of Convolutional Layers
* Convolutional Layers: these layers are the backbone of CNNs. They take input matrices, sets of filters, and classify the input based on the filters. They can be stacked together so, say, the first layers look for boundaries, then the next layers look for size of image, then the next layer looks at possible images of that size, etc...
* Pooling Layers: these layers run on top of CNNs and their job is to reduce dimensionality. This improved computation performance and also helps avoid overfitting. 

## Second Mini Project: Convolutional Visualization
In this mini project we began building intuition for convolutional neural layers. We showed what the filtered image looked like to get an intuition for what a filter does and how it gets applied to an image in practice. Post-filter, an image only has highlighted the area that applies to the filter. In this example we supplied the filters (vs having a CNN build it). We supplied 4 basic filters - representing horizontal and vertical boundaries so we could see how an image recognizes borders.
