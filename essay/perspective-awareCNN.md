# PACNN
## Abstract

## Introduction
The contribution of our work concerns two aspects regarding:
- the perspective generation
- its integration with crowd density regression

## Perspective-aware CNN
### Ground truth (GT) generation
**GT density map generation**
**GT Perspective map generation**
Considering the above facts, now we introduce a novel nonlinear way to fit the perspective values, aiming to produce an accurate perspective map that clearly underlines the general head size change from near to far in the image.
$$ p^g = a \cdot tanh(b \cdot (y_h + c)) $$
### Network architecture
**Density map regression** We regress three density maps from the outputs of Conv4_3, Conv5_1_3 and Conv6_1_1 simultaneously.
$$ D^e = \frac {D^{e_1} + Up(\frac {D^{e_2} + Up(D^{e_3} ) }  2 )  }  2 $$
$ D^e $ is of 1/8 resolution of the input, and we need to down-sample the corresponding ground truth as well. 
**Perspective map regression**
$ P^{e_s} $ denote the regressed perspective map after Conv5_2_3
**Perspective-aware weighting**
To make use of the estimated perspective maps $P^{e_s}$ and $ P^e $ , we add two perspective-aware(PA) weighting layers in the network.
$$ D^{e_s} = W^s \odot D^{e_2} + (1-W^s) \odot Up(D^{e_3}) $$
### Loss function and network training
$$ TBD $$
The training is optimized with Stochastic Gradient Descent (SGD) in two phases.
- Phase 1: optimize the density regression 
- Phase 2: finetune the model by adding the perspective-aware weighting layers to jointly optimize the perspective and density regressions