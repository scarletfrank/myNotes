# From Open Set to Closed Set: Counting Objects by Spatial Divide-and-Conquer

## Abstract
- A dense region can always be divided until sub-region counts are within the previously observed closed set.
- To avoid repeatedly computing sub-region convolutional features, S-DC is executed on the feature map instead of on the input image. 

## Introduction

Counting has an unique property--spatially decomposable.

Drawback of the naive way: blur the image and lead to exponentially-increased computation cost and memory consumption when repeatably extracting the feature map. => achieve S-DC on the feature map

In contrast to the conventional density map regression, we discretize continuous count values into a set of intervals and design the counting predictor to be a classifier.

## Related Work

- **Density Map Regression**
- **Local Count Regression**
- **Beyond Naive Regression**

## Spatial Divide-and-Conquer Network

### From Quantity to Interval

*systematic error caused by adopting $C_M$ for the last class* (but the error can be mitigated via S-DC)

### Single-Stage Spatial Divide-and-Conquer

S-DCNet includes a VGG16 feature encoder, an UNet-like decoder, a count-interval classifier and a division decider.

$$DIV_1 = (1 - W_1) \circ avg(C_0) + W_1 \circ C_1$$

### Multi-Stage Spatial Divide-and-Conquer

$$DIV_i = (1 - W_i) \circ avg(DIV_{i-1}) + W_i \circ C_i$$

the overall loss $L$ is a summation of all losses, i.e., $L=\sum^N_{i=0} L^i_C + L ^N_R$

## Open Set or Closed Set? A Toy-Level Jusitification

## Experiments on Real-World Datasets

## Conclusion