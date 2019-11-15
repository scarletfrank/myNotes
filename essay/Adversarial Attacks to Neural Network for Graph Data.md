# Adversarial Attacks to Neural Network for Graph Data
## Abstract
- Adversaries are common on the web.
- In addition to attack at test time, we tackle the more challenging class of poisoning/causative attacks, which focus on the training pharse of a machine learning model.
- unnoticeable perturbations, which preserves important data characteristics (e.g. degree distribution, co-occurence of features)
- an efficient algorithm NETTACK exploiting incremental computations
- transferable attack: the learned attacks generalize to other state-of-the-art node classification models and unsupervised approaches
## Introduction
### Opportunities
*targets*: nodes which we aim to misclassify
*attackers*: nodes which we can manipulate
### Challenges
- find adversarial examples in discrete domain
- how to capture the notion of unnoticeable change in a (binary, attributed) graph
- graph-based learning in a transductive setting is inherently related to the challenging poisoning/causative attacks
fool GCN/CLN/DeepWalk (semi-supervised, unsupervised)
computing attacks based on linearization ideas
## Preliminaiers
## Related Work
**Deep Learning for Graphs**
**Adversarial Attacks**
   - poisoning/causative attacks which target the training data (specifically, the model’s training phase is performed after the attack)
   - evasion/exploratory attacks which target the test data/application phase (here, the learned model is assumed fixed)
**Generating Adversarial Perturbations**
**Adversarial Attacks when Learning with Graphs**
## Attack Models
- **structure attacks**
- **feature attacks**
