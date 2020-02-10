# Generalizing from a Few Examples: A Survey on Few-Shot Learning
## Abstract
core issue of FSL: unreliable empirical risk minimizer
three perspectives: 
- data uses the prior knowledge to aument the supervised experience
- model constrains the hypothesis space by prior knowledge
- algorithm uses prior knowledge to alter the search for the parameter of the best hypothesis in the hypothesis space
## Introduction
- FSL advances the development of robotics which targets at developing machines that can replicate human actions so as to replace humans in some scenarios.
- FSL can help reduce the data gathering effort for these data intensive applications, such as image classification, image retrieval, object tracking, gesture recognition, image captioning and visual question answering, video event detection, and language modeling.
- drug discovery task: process of discovering the properties of new molecules so as to identify useful ones as new drugs, a FSL problem
- meta-learning method, embedding learning method and generative modeling method
## Overview
### Notation
*N-way-K-shot* classification task
### Problem Definition
*Machine Learning*:  A computer program is said to learn from experience *E* with respect to some classes of task *T* and performance measure *P* if its performance can improve with*E* on *T* measured by *P*
*Few-Shot Learning*: A type of machine learning problems (specified by *E*, *T* and *P*) where *E* contains a little supervised information for the target *T*
Typical scenarios of FSL:
- *Act as a test bed for human-like learning*
- *Reduce data gathering effort and computation cost*
- *Learn for rare cases*
### Relevant Learning Problems
- *semi-supervised learning*
- *Imbalanced learning*
- *Transfer learning*
- *Meta-learning*
### Core Issue
*approximation error* and *estimation error* => in FSL, *the empirical risk minimizer $h_I$ is no longer reliable*
### Sample Complexity
Sample complexity refers to the numer of training samples needed to guarantee the loss of minimizing epirical risk instead of expected risk is at most $\epsilon$ with probability $1-\sigma$
### Taxonomy
> Existing FSL works use prior knowledge to satisfy or reduce $S$

## Data
**Transform** $D^{train}$
- handcrafted rule
- learned transformation
**Transform Other Data Sets**
- weakly labeled or unlabeled data set
- similar data set

## Model
**Multitask Learning**
hard and soft parameter shareing strategies
**Embedding Learning**
- *Task-specific*
- *Task-invariant*
- *A Combination of Task-invariant and Task-specific* : *ProtoNet*, *Relation graph*, *SNAIL*
**Learning with External Memory**
**Generative Modeling**
- *Parts and Relations*
- *Super Classes*
- *Latent Variables*
## Algorithm
**Refine existing parameters ${\theta}^0$**
- *Fine-tune ${\theta}^0$ with Regularization*
- *Aggregate a Set of ${\theta}^0$*
- *Fine-tune ${\theta}^0 with New Parameters$*
**Refine meta-learned $\theta$**
- *Refine by Gradient Descent* : MAML
- *Refine in Consideration of Uncertainty*
- *Learn Search Steps*
**Learn search steps**
## Future Works
### Problem Setup
multi-modality prior knowledge, frequently used in zero-shot learning
use the multi-modality as one type of prior knowledge and design methods to deal with them based on those mentioned in data, model and algorithm
### Techniques
*Automated machine learning* (AutoML)
### Applications
image retrieval, object tracking, gesture recognition, image captioning and visual question answering and video event detection
translation and language modeling
cold-start item recommendation
few-shot drug discovery
robotics and game playing by reinforcement-learning
### Theories




