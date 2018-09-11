# Faster R-CNN

**Faster R-CNN** is a meta-architecture based on two stages that together serve as a unified network for detecting objects in images. In the first stage named the _Region Proposal Network_ \(RPN\), the images \(with the object that we hope to detect\) will be processed by a series of convolutional layers, known as the _feature extractor_. The output of this stage will be a series of agnostic box proposals, which are rectangles that possibly contain an object within it. The reason it is called agnostic is that at this point, the model does not know what kind of object it is, it only knows it is _something_ that might be an object.

In the second stage, the box proposals previously found, will be fed to the rest of the feature extractor with the goal of predicting the label of the object and a better position of the bounding box that surrounds it.

The original paper that describes the system is available at: __[Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks](https://arxiv.org/pdf/1506.01497.pdf).

