# Predicting Visual Exemplars of Unseen Classes for Zero-Shot Learning
## Abstract
A novel zero-shot learning model that takes advantage of clustering structures in the semantic embedding space. The key idea is to impose the structural constraint that semantic representations must be predictive of the locations of their corresponding visual exemplars.

## Introduction
In other words, the frequencies of observing objects follow a *long-tailed* distribution.
Images of the same class, after embedded into the semantic space, will cluster around the semantic embedding of that class.
The main idea is to exploit the intuition that the semantic representation can **predict well** the location of the cluster characterizing all visual feature vectors from the corresponding class.

## Approach
0. create the visual exemplar of a class by averaging the PCA projections of data belong to that class

e.g. 2048-dimensional ResNet10 => 1024 dimensions => average them 

1. find a transformation function

$$ \phi (a_c) \approx v_c $$

Learning to predict the visual exemplars from the semantic representations, learn *d* support vector regressors(SVR) with the RBF kernel -- each of them predicts each dimension of visual exemplars from their corresponding semantic representaitons.

> e.g. 1024 regressors, each of them predict one dimension...so predict the exemplars of the test class

$$\phi (a_u) \to v_u$$

2. ZSL based on the predicted visual exemplars
    - Predicted exemplars as training data
        PCA processes the test visual features matrix, and for each sample, classify it through the nearest neighbor classifier => closet exemplar
    - Predicted exemplars as the ideal semantic representations
        ~ and plug them into any existing zero-shot learning framework
3. 

## Implementation

1. [CCA](https://scikit-learn.org/stable/modules/cross_decomposition.html)
2. [t-SNE](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html)