# GraphSAGE
## Abstract
Low-dimensional embeddings of nodes in large graphs useful in prediction tasks from content recommendation to identifying protein functions. 
However previous approaches are inherently *transductive*. 
GraphSAGE, general *inductive* framework. Instead of training individual embeddings of each node, we learn a function that generates embeddings by sampling and aggregating features from a node's local neighborhood.
 Our algorithm our performs strong baselines on three inductive node-classification benchmarks: 
- citation and Reddit post (classify the catagory)
- protein-protein interactions (generalizes to completely unseen graphs)
## Introduction
The basic idea behind node embedding approaches is to use dimensionality reduction techniques to distill high-dimensional information about a node's graph neighborhood into a dense vector embedding.
Inductive capability is essential for high-throughput, production machine learning systems, which operate on evolving graphs and constantly encounter unseen nodes(e.g., posts on Reddt, users and videos on Youtube)
The inductive embedding problem is especially difficult, compared to the transductive setting.
The majority of these approaches directly optimize the embeddings for each node using matrix-factorization-based objectives, and do not naturally generalize to unseen data, since they make predictions on nodes in a single, fixed graph. 
So far, graph convolutional networks have only been applied in the transductive setting with fixed graphs. In this work we both extend GCNs to the task of inductive unsupervised learning and propose a framework that generalizes the GCN approach to use trainable aggregation functions(beyond simple convolutions)
**Present works**
Instead of training a distinct embedding vector for each node, we train a set of *aggregator functions* that learn to aggregate feature information from a node's local neighborhood.
## Related works
**Factorization-based embedding approaches**
There are a number of recent node embedding approaches that learn low-dimensional embeddings using random walk statistics and matrix factorization-based learning objectives. These methods also bear close relationships to more classic approaches to spectral clustering, multi-dimensional scaling, as well as the PageRank algorithm.
**Supervised learning over graphs**
**Graph convolutional networks**
The original GCN algorithm is designed for semi-supervised learning in a transductive setting, and the exact algorithm requires that the full graph Laplacian is known during training.
## Proposed method: GraphSAGE
### Embedding generation (i.e. forward propagation) algorithm
$K$ aggregator functions
**Relation to the Weisfeiler-Lehman Isomorphism Test** (testing graph isomorphism)
**Neighborhood definition**
$N(v)$ fixed-size, uniform draw from the set
$K=2 \\ S_1 \cdot S_2 \leq 500$
### Learning the parameters of GraphSAGE
The graph-based loss function encourages nearby nodes to have similar representations, while enforcing that the representations of disparate nodes are highly distinct.
$$ J_G(z_u) = - log (\sigma(z_u^T z_v)) - Q \cdot E_{v_n \~ P_n(v)} log (\sigma(z_u^T z_{vn}))$$
$v$ is a node that co-occurs near $u$ on fixed-length random walk
### Aggregator Architectures
**Mean aggregator**
$$ h_v^k \leftarrow \sigma(W \cdot MEAN(h_v^{k-1}) \cup \{ h_u^{k-1}, \forall u \in N(v) \} $$
**LSTM aggregator**
**Pooling aggregator**
$$ AGGREGATE_k^{pool} = \max ({\sigma (W_{pool} h_{u_i}^k + b), \forall u_i \in N(v)})$$
### Experiments
four baselines: a random classifier, a logistic regression feature-based classifier, the DeepWalk algorithm as a representative factorization-based approach, and a concatenation of the raw features and DeepWalk embeddings.
four variants of GraphSAGE that use the different aggregator functions.