# Continuous Control through Deep Reinforcement Learning
> DDPG, Deep DPG
## Abstract
- Applying the successful Deep Q-learning to the continuous action domain
- an actor-critic, model-free based on the deterministic policy gradient that can operates over the continuous action spaces
- for many of the tasks the algorithm can learn policies "end-to-end": from raw pixels input
## Introduction
 limitations of discretizing the action space: most notably the curse of dimensionality
DQN is able to learn value functions using such function approximators in a stable and robust way due to two innovations: off-policy training | target Q network

## Background
If the target policy is deterministic, we can decribe it as a function $\mu \colon A \to S$ and avoid the inner expectation:
$$Q^{\mu}(s_t, a_t) = \Bbb E_{r_t, s_{t+1} ~ E} [r(s_t, a_t) + \gamma Q^{\mu} (s_{t+1}, \mu(s_{t+1})] $$
The expectation depends only on the environment, which means that it is possible to learn $Q^{\mu}$ *off-policy*, using transitions which are generated from a different stochastic behavior policy $\beta$
two major changes to implement: the use of *replay buffer* and a separate *target network*
## Algorithm
The DPG algorithm maintains a parameterized actor function $\mu(s_t | \theta^{\mu})$ which specifies the current policy by deterministically mapping states to a specific action. The critic $Q(s, a)$ is learned using the Bellman equation as in Q-learning.
actor is updated by following the applying hte chain rule to the expected return with respect to the actor parameters (formula 6) *policy gradient* the gradient of the policy's performance
challenge when using neural networks for reinforcement learning is that most optimization algorithms assume that the samples are independently and identically distributed. => learn in minibatches rather than online
- a copy of actor, critic networks to softly update
- *batch normalization* normalizes each dimension across samples in a minibatch to have unit mean and variance
- Exploration is a major challenge of learning in continuous action spaces
 Constructed a exploration policy by adding noise sampled from a noise process $N$ to our actor policy
### DDPG
随机初始化critic network $Q(s, a | \theta^Q)$和actor $\mu (s|\theta^\mu)$ with weights $\theta^Q$ and $\theta^\mu$
初始化target network $Q '$ and $\mu '$
初始化replay buffer $R$
for episode = 1, M 
    初始化一个随机过程用于action探索
    初始观察状态 $s_1$
    for t= 1, T
        根据现在的策略和探索噪声选择一个action $a_t = \mu (s_t | \theta^\mu)$
        执行action $a_t$, 观察reward $r_t$ 和 新状态$s_{t+1}$
        存储transition (s_t, a_t, r_t, s_{t+1}) in R
        随机minibatch采样 of N transitions (s_i, a_i, r_i, s_{i+1}) from R
        set $y_i = r_i + \gamma Q' (s_{i+1}, \mu ' (s_{i+1} | \theta^{\mu '})|\theta^{Q'})$
        更新critic 最小化一个loss $L=\frac 1 N $
        更新the actor policy 通过采样过的策略梯度
        更新target network $\theta^{Q'}$ 和 $\theta^{\mu '}$
## Results
## Related Work