# R-FCN

**Region-based Fully Convolutional Networks** \(R-FCN\) is an architecture that follows the two-stage approach previously introduced while discussing Faster-RCNN. As before, during the first stage, the Region Proposal Network will extract areas of interests, also known as _proposal regions_ \(RoI\), which will be used by the actual network, which is mostly made of convolutional layers.

What differentiates this meta-architecture from Faster-RCNN is that the crops \(detections boxes\) are obtained from the last convolutional layer. At this layer, a position-sensitive score is calculated for each possible class, plus the "background" class \(absence of object\). The purpose of this value is to measure how much of an object is actually inside the RoI, so after this step, we will have an n + 1-dimensional \(n classes, plus background\) vector for each RoI. Lastly, a softmax operation is applied to these vectors to produce the probability of each of the classes.

The original paper that describes the system is available at: [R-FCN: Object Detection via Region-based Fully Convolutional Networks](https://arxiv.org/pdf/1605.06409.pdf)

