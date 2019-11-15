# Asynchronous Methods for Deep Reinforcement Learning
## Abstract
framework for deep reinforcement learning that uses asynchronous gradient descent for optimization of deep neural network controllers.
## Related Work
Keyword: parallel, distributed, evolutionary methods
## RL Background
one-step Q-learning => n-step Q-learning
One way of propagating rewards faster is using n-step returns.
When an approximate value function is used as the baseline, the quantity $R_t - b_t$ used to scale the policy gradient can be seen as an estimate of  the *advantage* of an action $a_t$ in state $s_t$.
## Asynchronous RL Framework    