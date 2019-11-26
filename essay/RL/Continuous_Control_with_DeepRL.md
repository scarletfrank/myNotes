# Continuous Control through Deep Reinforcement Learning
> DDPG, Deep DPG
## Abstract
- Applying the successful Deep Q-learning to the continuous action domain
- an actor-critic, model-free based on the deterministic policy gradient that can operates over the continuous action spaces
- for many of the tasks the algorithm can learn policies "end-to-end": from raw pixels input
## Introduction
Discretizing the action space has many limitations, most notably the curse of dimensionality
## Background
If the target policy is deterministic, we can decribe it as a function $\pi \colon S \to A$ and avoid the inner expectation:
$$Q^{\mu}(s_t, a_t) = E[r(s_t, a_t) + \gamma Q^{\mu} (s_{t+1}, \mu(s_{t+1})] $$
## Algorithm
The DPG algorithm maintains a parameterized actor function $\mu(s_t | \theta^{\mu})$ which specifies the current policy by deterministically mapping states to a specific action. The critic $Q(s, a)$ is learned using the Bellman equation as in Q-learning.
- a copy of actor, critic networks
- *batch normalization* normalizes each dimension across samples in a minibatch to have unit mean and variance
- Exploration is a major challenge of learning in continuous action spaces
 Constructed a exploration policy by adding noise sampled from a noise process $N$ to our actor policy
## Results
## Related Work