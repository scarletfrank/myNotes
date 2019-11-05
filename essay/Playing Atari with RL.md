# Playing Atari with Deep Reinforcement Learning
> DQN in 2013

## Abstract
The model is a convolutional neural network, trained with a variant of Q-learning, whose input is raw pixels and whose output is a value function estimating future rewards.
## Background
## Related Works
*TD-gammon*
*gradient temporal-difference*
## Deep Reinforcement Learning
*experience replay* $e_t = (s_t, a_t, r_t, s_{t+1})$
our Q-function works on fixed length representations of histories produced by a function $$
**Deep Q-learning with Experience Replay**:
**several advantages** over standard online Q-learning:
- each step of experience is potentially used in many weight updates, which allows for greater data efficiency
- randomizing the samples breaks the correlations between the consecutive samples and therefore reduces the variance of the updates
- off-policy
### Preprocessing and Model Architecture
$84 \times 84$ region, RGB representation to gray-scale
the function $\phi$ from algorithm 1 applies this preprocessing to the last 4 frames of a history and stacks them to produce the input to the $Q$-function
We instead use an architecture in which there is a separate output unit for each possible action, and only the state representation is an output to the neural network.
## Experiments
### Training and Stability
Another, more stable, metric is the  estimated policy's action-value function Q, which provides an estimate of how much discounted reward the agent can gain by following its policy from any given state. 
### Visualizing the Value Function
### Main Evaluation