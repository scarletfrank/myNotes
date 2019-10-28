# Hindsight Experience Replay

> ablation studies

## Abstract
A novel technique called *Hindsight Experience Replay* which allows sample-efficient learning from rewards which are sparse and binary and therefore avoid the need for complicated reward engineering. It can be combined with an arbitrary off-policy RL algorithm and may be seen as a form of implicit curriculum.

## Introduction
Wide range of successes in learning policies for sequential decision-making problems, such as:
- Simulated Environments: Playing Atari games and defeating the best human player at the game of Go
- Robotic tasks: Helicopter control, hitting a baseball, screwing a cap onto a bottle or door opening

*Common challenge*: especially for robotics, is the need to engineer a reward function that not only reflects the task at hand but is also carefully shaped to guide the policy optimization

The pivotal idea behind HER is to replay each episode with a different goal than the one the agent was trying to achieve, e.g. one of goals was achieved in the episode.

## Background

### RL

> Key elements of reinforcement learning 

A deterministic policy is a mapping from states to actions: $\pi \colon S \to A$.

At every timestep *t* the agent produces an action based on the current state.$a_t = \pi (s_t)$

Then it gets the reward $r_t = r(s_t, a_t)$ 

and the environment's new state is sampled from the distribution $p(\cdot | s_t, a_t)$

*Return*, A discounted sum of future rewards is called a return: $R_t = \sum\nolimits_{i=t}^{\infty} {\gamma}^{i-t} r_i$

Goal of the agent: maximize its expected return $E[R_t | s_t, a_t]$

Let $\pi^*$ denote an *optimal policy* i.e. any policy $\pi^*$ s.t. $Q^{\pi^*}(s, a) \geq Q^{\pi}(s, a)$ for every $s \in S, a \in A$ and any policy $\pi$

All optimal policies have the same Q-function which is called *optimal Q-function* and denoted $Q^*$

*Bellman equation* : 

$$Q^*(s, a) = E_{s' \thicksim p(\cdot|s_t, a_t)} [r(s, a) + {\gamma} \max_{a \in A} Q^* (s', a')]$$

### DQN
> model-free RL algorithm for discrete action spaces

maintain a neural network Q which approximates $Q^*$

*greedy* policy $\pi_Q(s) = argmax_{\alpha \in A} Q(s, a)$

$\epsilon$-greedy w.r.t. Q is a policy which with probability $\epsilon$ takes a random action and takes the action $\pi_Q(s)$ with probability $1 - \epsilon$

the transition tuples $(s_t, a_t, r_t, s_{t+1})$ stored in the so-called *replay buffer*

mini-batch gradient descent on the loss $L = E(Q(s_t, a_t) - y_t )^2$  where $y_t = r_t + \gamma \max_{a' \in A} Q(s_{t+1}, a')$

### DDPG
> model-free RL algorithm for continuous action spaces

maintain two neural networks: 
- a *target policy*, also called an *actor* $\pi \colon S \to A$
- an action-value function approximator, also called a *critic* $Q \colon S \times A \to R$

### UVFA

an extension of DQN to the setup where there is more than one goal we may try to achieve.

The Q-function now depends not only on a state-action pair but also on a goal $Q^{\pi}(s_t, a_t, g) = E[R_t | s_t, a_t, g]$

## HER

### A motivating example
bit-flipping environment with the state space $S= \{0, 1\} ^n$ and the action space $A = \{0, 1, \dots, n-1\}$ for some integer $n$ in which executing the $i$-th action flips the $i$-th bit of the state. For every episode we sample uniformly an initial state as well as a target state and the policy gets a reward of -1 as long as it is not in the target state, i.e. $r_g(s, a) = -[s \neq g]$

standard solution: shaped reward function $r_g(s, a) = - {||s-g||}^2$

different solution which does not require any domain knowledge: 
**re-examine this trajectory with a different goal**

while this trajectory may not help us learn how to achieve the state g, it definitely tells us something about how to achieve the state $s_T$

### Multi-goal RL

### Algorithm

1. simple idea behind HER

after experiencing some episode $s_0, s_1, \cdots, s_T$ we store in the replay buffer every transition $s_t \to s_{t+1}$ non only with the original goal used for this episode but also with a subset of other goals

one choice which has to be made in order to use HER is the set of additional goals used for replay.

*simplest* version: $m(s_T)$, i.e. the goal which is achieved in the final state of the episode

## After Works
[HER](https://arxiv.org/pdf/1707.01495)

[Releasing Multi-Goal RL Environments](https://arxiv.org/pdf/1802.09464)

[Learning Dexterous In-Hand Manipulation](https://arxiv.org/abs/1808.00177v5)

[SOLVING RUBIK’S CUBE WITH A ROBOT HAND](https://arxiv.org/abs/1910.07113)

[Blog OpenAI Five](https://openai.com/blog/openai-five/)

[Blog Learning Dexterity](https://openai.com/blog/learning-dexterity/)

[Blog Solving Rubik’s Cube with a Robot Hand](https://openai.com/blog/solving-rubiks-cube/)



