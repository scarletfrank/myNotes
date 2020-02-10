# Proximal Policy Optimization Algorithms
## Abstract
alternate between sampling data through interaction with the environment, and optimizing a "surrogate" objective function using stochastic gradient ascent.
## Introduction
an algorithm that attains the data efficiency and reliable performance of TRPO, while using only first-order optimization. A novel objective with clipped probability ratios, which performs a pessimistic estimate of the performance of the policy.
## Background: Policy Optimization
### Policy Gradient Methods
$g = \mathbb E _t []$
### Trust Region Methods
an objective function(the "surrogate" objective) is maximized subject to a constraint on the size of the policy update
## Clipped Surrogate Objective  
Let $r_t(\theta)$ denote the probability ratio
$ r_t(\theta) = \frac {\pi_{\theta} (a_t | s_t) } { \pi_{\theta_{\text{old}} (a_t | s_t)} }$
$$L^{CLIP}(\theta) = \mathbb E_t [\text{min}(r_t(\theta)A_t, \text{clip}(r_t(\theta), 1-\epsilon, 1+\epsilon)A_t]$$
## Adaptive KL Penalty Coefficient
an alternative to the clipped surrogate objective, or in addition to it, is to use a penalty on KL divergence
## Algorithm
## Experiments