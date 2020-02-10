# Book Notes
*Reinforcement Learning: An Introduction second edition*

## Structure
- Introduction
- Tabular Solution Methods
- Approximate Solution Methods
- Looking Deeper
> Tabular, arranged in a table or in columns and rows
### Introduction

#### Definition of RL
- a *computational* approach to learning from interaction
- RL is much more focused on goal-directed learning from interaction than are other approaches to machine learning
> Reinforcement learning is learning what to do - how to map situations to actions - so as to maximize a numerical reward signal.
- two characteristics: trial-and-error search and delayer reward
different from supervised learning and unsupervised learning
> unsupervised learning, which is typically about finding structure hidden in collections of unlabeled data

One of the challenges thath arise in RL, is the trade-off between **exploration** and **exploitation**. The agent has to *exploit* what it has already experienced in order to obtain reward, but it also has to *explore* in order to make better action selections in the future.

#### Elements of RL
the agent and the environment.
*a policy, a reward signal, a value function and a model of the environment*
Whereas the reward signal indicates what is good in an immediate sense, a *value function* specifies what is good in the long run.

#### Limitations and scope
Most of the reinforcement learning methods we consider in this book are structured around estimating value functions, but evolutionary methods never estimate value functions.

#### Example: Tic-Tac-Toe
> Classical techniques and evolutionary method cannot solve this problem in a satisfactory way
> "minimax" solution from game theory assumes a particular way of playing by the opponent
> Dynamic programming require as input a complete specification of that opponent, including the probabilities with which the opponent makes each move in each board state.
> 上述信息可以通过经验来估计，通过跟对手玩很多局游戏，学习到这个知识再去运用动态规划，但这个方法就是偏向RL的方法了。

*value function*：a table of numbers, one for each possible state of the game
*Initialization*: for all states with three Xs in a row the probability of winnning is 1, three Os in a row ... is 0, others is 0.5
*Moving*: "Most of the time, we move *greedily*. Occasionally, we select randomly from among the other moves instead.(*exploratory*)
*Playing*: change the values of the states according to

$$V(S_t) \leftarrow V(S_t) + \alpha [V(S_{t+1}) - V(S_t)]$$

α is a small positive fraction called the *step-size parameter*. This update rule is an example of a *temporal-difference* learning method

> In the end, evolutionary and value function methods both search the space of policies, but learning a value function takes advantage of information available during the course of play
> RL also applies in the case of a "game against nature" | continuous-time problems | large or infinite state set |
> Model-free systems cannot even think about how their environments will change in response to a single action

#### Exercise
- *Self-Play*
- *Symmetries*
- *Greedy Play*
- *Learning from Exploration*
- *Other Improvements*
#### Early History
TBD

## Tabular Solution Methods

### Multi-armed Bandits
> The most important feature distinguishing reinforcement learning from other types of learning is that it uses training information that *evaluates* the actions taken rather than *instructs* by giving correct actions.
> The particular *nonassociative*, evaluative feedback problem that we explore is a simple version of the *k*-armed bandit problem.

$$q_*(a) = E [ {\it R_t } | A_t = a] $$
**Balancing exploration and exploitation**

#### Action-value Methods
- averaging the rewards actually received

$$Q_t(a) = TBD$$

sum of rewards when a taken prior to t / number of times a taken prior to t
- *greedy* action selection method:

$$A_t = \underset {a} {argmax} Q_t(a)$$

- *sigma-greedy* method
with small probability sigma, instead select randomly from among all the actions with equal probability, independently of the action-value estimates

#### Incremental Implementation

$$Q_{n+1} = Q_n + \frac 1 n [R_n - Q_n] \\ NewEstimate \leftarrow OldEstimate + StepSize [Target - OldEstimate]$$

**A simple bandit algorithm**

$$  \text {Initialize, for a = 1 to k} \\ Q(a) \leftarrow 0 \\ N(a) \leftarrow 0 \\ Loop forever \\A \leftarrow TBD \\ R \leftarrow \it bandit(A) \\ N(A) \leftarrow N(A) + 1 \\ Q(A) \leftarrow Q(A) + \frac 1 N(A) [R - Q(A)]$$

#### Tracking a Nonstationary Problem
*exponential recency-weighted average*

$$Q_{n+1} = Q_n + \alpha [R_n - Q_n] \\ Q_{n+1} = {(1-\alpha)}^n Q_1 + \sum_{i=1}^n \alpha {(1-\alpha)}^{n-i} R_i$$

#### Optimistic Initial Values
Initial action values can also be used as a simple way to encourage exploration.
#### Upper-Confidence-Bound Action Selection

$$A_t = \underset {a} {argmax} \{  Q_t(a) + c \sqrt {\frac {\ln t} {N_t(a)}} \}$$

#### Gradient Bandit Algorithms
> learning a numerical *preference* for each action a, which we denote *H_t(a)*

**The Bandit Gradient Algorithm as Stochastic Gradient Ascent**
pi_t(a): for the probability of taking action a at time t
Proof TBD

#### Associative Search(Contextual Bandits)
Nonassociative tasks, that is, tasks in which there is no need to associate different actions with different situations.

#### Exersice
*2.1* sigma=0.5, for the case of two actions, what is the probability that the greedy action is selected? 0.5

**The 10-armed Testbed**
*2.6 Mysterious Spikes*
*2.7 Unbiased Constant-Step-Size Trick*

### Finite Markov Decision Processes
> Whereas in bandit problems we estimated the value q(a) of each action a, in MDPs we estimate the value q(s, a) of each action a in each state s, or we estimate the value v(s) of each state given optimal action selections. These state-dependent quantities are essential to accurately assigning credit for long-term consequences to individual action selections.

#### The Agent-Environment Interface
The MDP and agent together thereby give rise to a sequence or *trajectory* that begins like this:

$$S_0, A_0, R_1, S_1, A_1, R_2, S_2, A_2, R_3,... (3.1) \\ p(s', r | s, a) \dot = Pr \{ S_t = s' , R_t = r | S_{t-1} = s, A_{t-1} = a \} (3.2)$$

The function *p* defines the *dynamics* of the MDP. The dot over the equals sign in the equation reminds us that is a definition (in this case of the fcuntion *p*) rather than a fact that follows from previous definitions.
*Markov property*
From the four-argument dynamics function, p, one can compute anything else one might want to know about the environment:
- *state-transition probabilities* three-argument
- expected rewards for state-action pairs two-argument
- expected rewards for state-action-next-state triples three-argument
The agent-environment boundary represents the limit of the agent's *absolute control*, not of its knowledge.
- Bioreactor
- Pick-and-Place Robot
- Recycling Robot

#### Goals and Rewards
*reward hypothesis* : That all of what we mean by goals and purposes can be well thought of as the maximization of the expected value of the cumulativesum of a received scalar signal (called reward)

#### Returns and Episodes
(1) *expected return*
simplest case the return is the sum of the rewards, where T is a final time step. 
~ when the agent-environment interaction breaks naturally into subsequences, which we call *episodes*, such as plays of a game, trips through a maze, or any sort of repeated interaction.
Each episode ends in a *terminal state*.

$$G_t \dot = R_{t+1} + R_{t+2} + R_{t+3} + ... + R_T$$

(2) *discounted return*
$\gamma$ is discount rate

$$G_t \dot = R_{t+1} + \gamma R_{t+2} + \gamma ^ 2 R_{t+3} + ... = \sum_{k=0}^{\inf} {\gamma}^k R_{t+k+1}$$

(3) Pole-Balancing Example
episodic task or continuing task

#### Unified Notation for Episodic and Continuing Tasks

$$G_t \dot = \sum_{k=t+1}^T {\gamma}^{k-t-1} R_k $$

including the possbility that T = $\inf$ or $\gamma$ = 1 (but not both)

#### Policies and Value Functions
*value functions* - functions of states (or of state-action pairs) that estimate *how good* it is for the agent to be in a given state (or how good it is to perform a given action in a given state). Accordingly, value functions are defined with respect to particular ways of acting, called policies.

a *policy* is a mapping from states to probabilities of selecting each possible action.
The *value function* of a state s under a policy pi, denoted as v_pi(s), is the expected return when starting in s and following pi thereafter. 
*action-value function*: Similarly, we define the value of taking action a in state s under a policy pi, denoted as q_pi(s, a), as the expected return starting from s, taking the action a, and thereafter following policy pi

$$v_{\pi}(s) \dot = E_{\pi}[G_t | S_t = s] = TBD \\ q_{\pi}(s, a) \dot = E_{\pi} [G_t | S_t = s, A_t = a] = TBD$$

*Monte Carlo methods* : averaging over many random samples of actual returns
estimate v_pi(s) and q_pi(s, a)
*Bellman equation for v_pi* It expresses a relationship between the value of a state and the values of its successor states.

$$v_{\pi} (s) = \sum_{s', r} p(s' , r | s, a) [r + \gamma v_{\pi} (s')]$$

**Backup diagram for v_pi** : Because they diagram relationships that form the basis of the update or *backup* operations. These operations transfer value information *back* to a state(or a state-action pair) from its successor states (or state-action pairs).
Exercise TBD

#### Optimal Policies and Optimal Value Functions
**Bellman optimality equation for v_star and q_star**

$$v_*(s) = \max_{a} \sum_{s',r} p(s', r| s, a) [r+ \gamma v_*(s')] \\ q_*(s, a) = \sum_{s',r} p(s', r| s, a)[r+\gamma \max_{a'} q_*(s', a')]$$

#### Optimality and Approximation
The online nature of reinforcement learning makes it possible to approximate optimal policies in ways that put more effort into learning to make good decisions for frequently encountered states, at the expense of less effort for infrequently encountered states. This is one key property that distinguishes reinforcement learning from other approaches to approximately solving MDPs.

### Dynamic Programming
> Introduction to Algorithms

Classical DP algorithms are of limited utility in reinforcement learning both because of their assumption of a perfect model and because of their great computational expense, but they are still important theoretically.

#### Policy Evaluation (Prediction)

$$ v_{k+1}(s) \dot = \sum_{a} \pi(a|s) \sum_{s', r} p(s', r | s, a) [r+ \gamma v_k(s')]$$

4x4 gridworld example (evaluate random policy)

#### Policy Improvement

*policy improvement theorem*: $q_{\pi '} (s) \geq v_{\pi}(s)$

consider the new *greedy* policy $\pi '$, given by

$$\argmax_a  \sum_{s', r} p(s', r |s, a) [r+ \gamma v_{\pi}(s')]$$

The process of making a new policy that improves on an original policy, by making it greedy with respect to the value function of the original policy, is called *policy improvement*

deterministic => *stochastic case*

#### Policy Iteration

$$\pi_0 \to v_{\pi_0} $$

This way of finding an optimal policy is called *policy iteration*

Example: Jack's Car Rental

#### Value Iteration
#### Asynchronus Dynamic Programming
#### Generalized Policy Iteration
#### Efficiency of Dynamic Programming
### Monte Carlo Methods
Monte Carlo methods are ways of solving reinforcement learning problem based on averaging sample returns.
#### Monte Carlo Prediction
#### Monte Carlo Estimation of Action Values
#### Temporal-Difference Learning