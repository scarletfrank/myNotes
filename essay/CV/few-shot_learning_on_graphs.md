# Few-Shot Leraning on Graphs via Super Classes Based on Graph Spectral Measures
> ICLR Blind Open Review: Weak Accept x 2, Weak Reject x 1
> Accept(Poster)
## Abstract
We present an approach where a probability measure is assigned to each graph based on the spectrum of the graph's normalized Laplacian. This enables us to accordingly cluster the graph base-labels associated with each graph into super-classes, where the $L^p$ Wasserstein distance serves as our underlying distance metric.
## Introduction
**Limitations and challenges**: Most recently proposed GNNs were designed based on empirical intuition and heuristic approaches. Most neighborhood aggregation and graph-pooling schemes had diminished discriminative power.
**Our Work**: Given this metric space of *graph spectral measures* and the underlying distance as $L^p$ Wasserstein distance, we compute *Wasserstein barycenters* for each set of graphs specific to a base class and term these barycenters as *prototype graphs*
=> *graph of graphs* called a *super-graph*
Given, the super-classes and the super-graph, Our GNN consists:
- *feature extractor* $F_\theta ()$ from a GIN(*graph isomorphism network*)
- $C^{sup}$ MLP layer to learn and predict the super class
- $C^{GAT}$ a *graph attention network* to predict the actual class label
Loss: sum of cross-entropy losses associated with $C^{sup}$ and $C^{GAT}$
**Contributions**: first to introduce few shot learning on graphs for graph classification
## Related Work
**Comparison to few-shot learning on images**: 
- Euclidean non-Euclidean domain
- abundance of the number of training samples from various classes
- well-known regularization methods
- the high degree of transferability of feature extractors
## Preliminaries
**Data sample sets**
*Notations*: $G$ a set of undirected unweighted graphs; $Y$ the set of associated class labels
- the set of *base class* labeled graphs, n $G_B$ $y^{(B)} = {1 \dots K}$
- the set of *novel class* labeled graphs, m $G_N$ $y^{(N)} = {K+1 \dots K'}$
- a set of *t* unlabeled *unseen* graphs $G_U$ for testing
> there are far fewer novel class labeled graphs compared to the base class labeled ones

**Learning procedure** : 
> Inspired by the *initialization based methods*, we similarly follow a two-stage approach of *training* followed by *fine-tuning*

1. graph feature extractor $F_\theta$ and a classifier $C(G_B)$ (standard cross-entropy loss)
2. fixed pre-trained feature extractor and a classifier $C(G_N)$ (the same loss function)
**Problem definition**: to classify $t$ unseen test graph samples from $G_U$. Moreover, if $m=qT$, where $T = K' - K$ i.e. each novel class label appears exactly q times in $G_N$ (q-shot learning)

**Graph spectral distance**
the set of eigenvalues of $\Delta_g = I - D^{-1/2}AD^{1/2}$ denoted by $\sigma(g)$
*graph spectral measure* : $\mu_{\sigma(g)}$

**Definition 1**
*p-th Wasserstein distance between measures $\mu$ and v* is given by
$$ W_p(u, v) = (\inf_\gamma \int_{[0, 2] \times [0, 2]} c(x,y)^p d\gamma | \gamma \in {\prod (u,v)})^{\frac 1 p}$$
**Definition 2**
$$W^p(g, g') = W_p(\mu_{\sigma(g)}, \mu_{\sigma(g')}) $$
## Our Method
(1) cluster abundant base-class labels into *super-classes* by computing *prototype graphs* from each class => super classes are then used in the creation of a *super-graph* (once-off process)
(2) *feature extractor* and a *classifier*
![](./_image/2019-12-05-10-00-10.jpg)
### Computing Super Classes
partition the set $G_B$ into *class-specific sets* $G^{(i)}$
The class prototype graph $p_i$ for the i-th class is the graph with the least average spectral distance to the rest of the graphs in the same class
$$p_i={argmin}_{g_i \in \pi_1 (G^{(i)})} \frac {1} {|G^{(i)}|} \sum_{j=1}^{|G^{(i)}|} W^p(g_i, g_j)$$ 
**clustering prototype graphs**: associate these spectral measures to *at most k* clusters, where $k \gt 1$ is a user defined parameter
$${argmin}_C \sum_{i=1}^k \sum_{s_i \in C_i} W_p(s_i, B(C_i) $$
$$B(C_i) = argmin_{p \in P([0, 2])} \sum_{j=1}^{|C_i|} W_p(p, s(i, j)$$
**Lloyd's algorithm**
a grouping of the prototype graphs into *k* groups => super-classes
![](./_image/2019-12-05-10-08-52.jpg)
### Our Graph Neural Network
**Feature Extractor**
$$H^{(j)} = MLP((1+\varepsilon)^j \odot H^{(j-1)} + A^T H^{(j-1)} )$$
$H_g = ||^R_{j=1} H^{(j)} \\ \text{with} \\ H^{(j)} = \sum_{v \in V} H^{(j)}_v$
$H_g$ now contains the graph embedding of a graph $g$ and is passed on to the classifier
**Classifier** 
"graph of graph embeddings" *super graph $g^{sup}$*, where each node is a graph feature vector
build the super-graph on a batch of base-labeled graphs as a collection of k-NN graphs, where each constituent k-NN graph is built on the graphs belonging to the same super-class
$g^{sup}$ is then passed through GAT
- *training*
$C^{GAT}$ to learn the associated class probabilities
$C^{sup}$ to learn the associated super-class labels
- *fine-tuning*
The intuition behind the construction of $g^{sup}$ to train $G^{GAT}$
intialization method
**Discussion**
assumption: the novel test classes belong to the same set of super-classes from the training graphs
we pass the novel graph samples through our trained $C^{sup}$ and infer its super-class label and this works very effectively for us, as is evidenced by our empirical results.
## Experimental Results
Datasets: *Letter-High*, *TRIANGLES*, *Reddit-12K*, and *ENZYMES*
partition the main model into *feature extraction* and *classifier* sub-models
*k*-NN search on the output embeddings of these algorithms
### Ablation study on number of super-classes
the super-class classifier $C^{sup}$
### Sensitivity Analysis of various attributes
- the number of super-classes 
- the k-th value in super-graph construction
## Conclusion
A promising future work is to propose new GNN models that break away from current neiborhood aggregation schemes to specifically