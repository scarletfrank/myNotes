# Octave Convolution
## Abstract
design a novel Octave Convolution operation to store and process feature maps that vary spartially "slower" as low spatial resolution that reduce both memory and computation cost
## Introduction
A natural image can be decomposed into a low spartial frequency component that describes the smoothly changing structure and a high spartial frequency component that describes the rapidly changing fine details.
OctConv which takes in features maps containing tensors of two frequencies one octave apart, and extracts information directly from the low-frequency maps without the need of decoding it back to the high-frequency map.
## Related Work
**Improving the efficiency of CNNs**
**Multi-scale Representation Learning**
## Method
### Octave Feature Representation
### Octave Convolution
the output of $Y= { Y^H, Y^L22} $ will be given by $Y^H = Y^{H \to H} + Y^{L \to H}$ and $Y^L = Y^{L \to L} + Y^{H \to L}$
split the convolutional kernel W into two components: $W = {W^H, W^L}$, which are $W^H = [W^{H \to H}, W^{L \to H}]$ and $W^L = [W^{L \to L} + W^{W \to L}]$
### Implementation Details

## Experiment Evaluation
## Conclution