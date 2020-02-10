# Zero-shot Recognition via Semantic Embedding and Knowledge Graphs
## Abstract
zero-shot recognition: learning a visual classifier for a category with zero training examples, just using the word embedding of the category and its relationship to other categories, which visual data are provided.
## Introduction
distill both the implicit knowledge representations (i.e. word embedding) and explicit relationships (i.e. knowledge graphs) for learning visual classifiers of novel classes
a 6-layer deep GCN that outputs the classifiers of different categories
## Recent Work
## Approach
### Preliminaries: Graph Convolutional Network
### GCN for Zero-shot Learning
the visual classifier we want the GCN to predict is a logistic regression model on the fixed pre-trained ConvNet features
each node in the knowledge-graph(KG) represents a semantic category. $n$ categories => $n$ nodes in the graph, 
6-layer GCN:
-  For the first layer the input is $X$ which is an $n \times k$ matrix ($k$ is the dimensionality of the word-embedding vecotr). 
- For the final-layer the output feature-vector is $W$ which has the size of $n \times D$ ; $D$ being the dimensionality of the classifier or visual feature vector

**Loss-function**:
$$\frac 1 m \sum_{i=1}^m L_{mse}(\hat{w}_i, w_i)$$

### Implementatation Details
Deep GCN
LeakyReLU
L2-Normalization
use the GloVe text model to obtain the word embeddings for GCN inputs
## Experiment
robust to different pre-trained ConvNets and noise in the KG
1. Never-Ending Language Learning(NELL) and Never-Ending Image Learning(NEIL)
2. ImageNet dataset, WordNet knowledge graph
### Experiments on NELL and NEIL
sub-graph: BFS starting from the NEIL nodes, paths with maximum length $K=7$ hops such that the first and the last node in these paths into our sub-graph
### Experiments on WordNet and ImageNet
