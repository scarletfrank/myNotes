# Focal loss for object detection
## Abstract
> Our results show that when trained with the focal loss, RetinaNet is able to match the speed of previous one-stage detectors while surpassing the accuracy of all existing state-of-the-art two-stage detectors.
> Extreme foreground-background class imbalance encountered during training of dense detectors is the central cause, () one-stage detectors have trailed the accuracy of two-stage detectors thus far 

$$ CE(p_t) = -log(p_t)$$
$$ FL(p_t) = -(1-p_t)^{\gamma} log(p_t) $$
Setting ${\gamma} > 0$ reduces the relative loss for well-classified examples ($p_t > .5$), putting more focus on hard, misclassified examples.
## Introduction
Before: two-stage, proposal-driven mechanism. Faster R-CNN
Now: RetinaNet (one-stage)
To achieve this result,  we identify *class imbalance* during training as the main obstacle impeding one-stage detector from achieving state-of-the-art  accuracy and propose a new loss function that eliminates this barrier.
Class imbalance is addressed in R-CNN-like detectors by a two-stage cascade and sampling heuristics. It reduces the number of candidate object locations to a small number. While a one-stage detector must process a much larger set of candidate object locations regularly sampled accross an image.
> challenging COCO benchmark

## Related Work
## Focal Loss