# Predicting Visual Exemplars of Unseen Classes for Zero-Shot Learning
## Abstract
A novel zero-shot learning model that takes advantage of clustering structures in the semantic embedding space. The key idea is to impose the structural constraint that semantic representations must be predictive of the locations of their corresponding visual exemplars.

## Introduction
In other words, the frequencies of observing objects follow a *long-tailed* distribution.
Images of the same class, after embedded into the semantic space, will cluster around the semantic embedding of that class.
The main idea is to exploit the intuition that the semantic representation can **predict well** the location of the cluster characterizing all visual feature vectors from the corresponding class.

## Approach
1. Learning to predict the visual exemplars from the semantic representations
PCA projection matrix
learn *d* support vector regressors(SVR) with the RBF kernel
2. Zero-shot learning based on the predicted visual exemplars
- Predicted exemplars as training data
    nearest neighbor classifier
- Predicted exemplars as the ideal semantic representations
    ~ and plug them into any existing zero-shot learning framework
3. 

## Implementation

1. [CCA](https://scikit-learn.org/stable/modules/cross_decomposition.html)
2. [t-SNE](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html)