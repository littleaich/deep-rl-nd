[//]: # (Image References)

[image1]: https://github.com/littleaich/deep-rl-nd/blob/master/projects/03_collab-compet/figures/tennis.gif "Trained Agent"

# Project 3: Collaboration and Competition

### Introduction

This is the third project for the [**Deep Reinforcement Learning NanoDegree**](https://github.com/udacity/deep-reinforcement-learning) at Udacity. For this project, you will train a couple of tennis playing agents to control the rackets to bounce a ball over a net. The agents will learn from information such as the position and the velocity of the ball and their own rackets.   

![Trained Agent][image1]

A reward of +0.1 is provided for each step the agent hits the ball over the net. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

The observation space consists of 8 variables (24 in total for 3 stacked observations) corresponding to the position and velocity of the ball and racket. Each agent receives its own, local observation. Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

The task is episodic, and in order to solve the environment, the agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). More specifically, after each episode, the rewards that each agent received (without discounting) are added to get a score for each agent. This yields 2 (potentially different) scores of which the maximum is considered the score for that episode.

The environment is considered solved, when the average (over 100 episodes) of those scores is at least +0.5.

### Prerequisites
1. Python3.6
2. PyTorch v0.4 (or, higher might work)
3. Unity ML-Agents v0.4

###### Note that you don't need to install Unity! Also, this project environment is similar, but not identical to the Reacher environment on the [Unity ML-Agents Github page](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md). You can find a complete list of the dependencies in the repo of **Deep Reinforcement Learning ND** at Udacity [here](https://github.com/udacity/deep-reinforcement-learning#dependencies)

### Getting Started
1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)


2. Place the file in the same directory as the codes, and unzip (or decompress) the file.

#### Code Description
Here, I implement [Deep Deterministic Policy Gradient (DDPG)](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf), an Actor-Critic algorithm appropriate for continuous control tasks. The approach described in the paper follows the off-policy method to train both actor and critic models. The same models (shared weights) are trained for both agents. Code files are listed below:

* model.py _(actor and critic networks used as the function approximator)_
* ddpg_agent.py _(DDPG agent)_
* Continuous_Control.ipynb _(contains the training and inference code for Reacher environment)_
* checkpoint_actor_*.pth _(actor checkpoint files -- upto 300 episodes)_
* checkpoint_critic_*.pth _(critic checkpoint files -- upto 300 episodes)_

#### Optional:
You can build your own environment in Unity ML-Agents following the instructions [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Getting-Started-with-Balance-Ball.md)
