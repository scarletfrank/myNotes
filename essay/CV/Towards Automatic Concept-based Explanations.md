# Towards Automatic Concept-based Explanations
> Interpretability Beyond Feature Attribution:
Quantitative Testing with Concept Activation Vectors (TCAV)
## Abstract
Most of the current explanation methods provide explanations through feature importance scores, which identify features that are important *for each individual input*.
In this work, we propose principles and desiderata for concept based explanation, which goes beyond per-sample features to identify higher level human-understandable concepts that apply across the entire dataset.
## Introduction
drawbacks of the "feature-based" explanations:
- vulnerability even to simple shifts
- adversarial perturbation
- susceptible to human confirmation biases
Automatic Concept-based Explanation(ACE) works by aggregating related local image segments across diverse data.
## Concept-based Explanation Desiderata
*Desired properties*:
1. Meaningfulness
2. Coherency
3. Importance
## Methods
Three main components of an explanation algorithm: 
- a trained classification model
- a set of test data points from the same classification task
- a importance computation procedure that assigns importance to features, pixels, concepts
### Step-by-step
Procedure:
1. Multi-resolution segmentation of images
2. clustering similar segments and removing outliers
3. computing saliency of concepts

**To measure the similarity of segments**
the state-of-the-art convolutional neural networks trained on large-scale datasets like ImageNet, the euclidean distance in the activation space of final layers is an effective perceptual similarity metric
### How ACE is designed to achieve the three desiderata
ACE uses simple and fast super-pixel segmentation methods instead of deep neural networks which imposes higher computational cost. These methods could be applied with any desire level of resolution with low computational cost, at the cost of suffering from lower segmentation quality.
ACE uses a ImageNet-trained CNN to go over all segments, clusters similar segments as concepts and remove meaningless or dissimilar segments.
ACE utilizes the TCAV score as a concept's importance metric 