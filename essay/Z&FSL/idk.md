# 毕业设计
## Abstract
## Introduction
(related works)
图像领域构建了一个KG，一个节点代表word-embedding，然后edge关系基于两个node有关系。
图领域构建则是挑选了prototype graph，将prototype graph利用k-NN聚类为一个个super-class的想法，同时在一个super-class上做super-graph(graph of graph embeddings)
super-graph和KG上做GCN的想法类似，如果两个概念类似/有关联，那就能用这种关系指导分类（不管是few-shot还是zero-shot）
(改造)
KG可以换用其他方法，比如GraphSAGE来挖掘关系（但是速度应该很慢，毕竟是在线更新，如果一下子KG的更新增加很多，不如GCN），但知识图不应该是永久不变的。
KG的挖掘方式，可以先语义聚类建立super-class，然后依据此建立super-graph。
(zero-shot learning on graphs)
没见过的节点：单个节点情况类似，缺少语义信息。不过都可以迁移，比如一个社交网络，一个新的用户必然有基础的信息，就可以放入一个图中利用GNN生成特征
没见过的图：比起图像来说，缺少语义信息
(视觉系)
实现visual exemplars，将他嵌入一个已有的ZSL框架
(人脸数据集)
在人脸数据集上做zero-shot learning的意义：感觉抓抓犯罪分子还行
以及如果利用语义信息指导GAN生成人脸，意味着对一个人的脸部描述可以生成一张近似的脸出来...最坏的情况这个可以对人脸识别进行攻击。
### Preliminaries: GAN
GANs are just one kind of generative model.
A generative adversarial network (GAN) has two parts:
- The **generator** learns to generate plausible data.
- The **discriminator** learns to distinguish the generator's fake data from real data.
*using the discriminator to train the generator*
Loss functions:
- **minimax loss**
- **Wasserstein loss**
## Our Methods
## Experiments
## Conclusion
## References
1. Zero-shot Recognition via Semantic Embeddings and Knowledge Graphs
2. Few-Shot Learning On Graphs via Super-classes Based on Graph Sepctral Measures