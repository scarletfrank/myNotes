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

### DQN

### DDPG

### UVFA

an extension of DQN to the setup where there is more than one goal we may try to achieve.

## HER

### A motivating example

### Multi-goal RL

### Algorithm


