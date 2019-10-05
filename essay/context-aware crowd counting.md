# CANet
## Abstract
**end-to-end trainable deep architecture** that combines features obtained using multiple receptive field sizes and learns the importance of each such feature at each image location
*receptive field*
## Introduction
emphasis on developing *counting-by-density* algorithms (recent years)
Our contribution is therefore an approach that incorporates multi-scale contextual information directly into an end-to-end trainable crowd counting pipeline, and learns to exploit the right context at each image location.
## Related work
> from *counting-by-detection* to *counting-by-density-estimation*

## Approach
### Scale-Aware Contextual Features
```mathjax
f_v = F_{vgg}(I) \; (1) \\
s_j = U_{bi} (F_j (P_{ave}(f_v , j), {\theta}_j )) \; (2) 
```
Limitation of F_vgg is that it encodes the same receptive field over the entire image. To remedy this, we compute scale-aware features by performing *Spartial Pyramid Pooling* to extract multi-scale context information from the VGG features of (1). 
Specifically, we compute these scale-aware features as (2), where, for each scale j:
- P_ave(·, j) averages the VGG features into k(j) x k(j) blocks; 
- F_j is a convolutional network with kernel size 1 to combine the context features accross channels without changing their dimensions.
- U_bi represents bilinear interpolation to up-sample the array of contextual features to be of the same size as f_v
> Practical Hyperparameters: S = 4 different scales, k(j) from {1, 2, 3, 6}

**concatenate** all of them(scale-aware features) to the original VGG features f_v. This,  however, would not account for the fact that scale varies accross the image. To model this, we propose to learn to predict weight maps that set the relative influence of each scale-aware feature at each spatial location.

Define contrast features as (3)
Each such auxiliary network outputs a scale-specific weight map of the form (4)
F_{sa}^j : a 1x1 convolutional layer followed by a sigmoid function to avoid division by zero
channel-wise concatenation operation | element-wise product between a weight map and a feature map
```mathjax
c_j = s_j - f_v \; (3) \\
w_j = F_{sa}^j (c_j, {\theta}_{sa}^j) \; (4) \\
f_I = [f_v | \frac {\sum_{j=1}^S w_j \bigodot s_j } {\sum_{j=1}^S w_j}] \; (5)
```
> This network already outperforms the state of the art on all benchmark datasets, without explicitly using information about camera geometry.

### Geometry-Guided Context Learning
### Loss
```mathjax
L({\theta}) = \frac {1} {2B} \sum_{i=1}^B || D_i^{st} - D_i^{est} || _2^2
```