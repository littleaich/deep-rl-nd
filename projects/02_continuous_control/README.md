[//]: # (Image References)

[image1]: https://github.com/littleaich/deep-rl-nd/blob/master/projects/02_continuous_control/figures/reacher.gif "Trained Agent"

# Project 2: Continuous Control

### Introduction

This is the second project for the [**Deep Reinforcement Learning NanoDegree**](https://github.com/udacity/deep-reinforcement-learning) at Udacity. For this project, you will train an agent to navigate (and collect bananas!) in a large, square world. The agent will learn from information such as its velocity, along with ray-based perception of objects around its forward direction.   

![Trained Agent][image1]

A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of the agent is to maintain its position at the target location as many time steps as possible.

The state space has 33 dimensions corresponding to the position, rotation, velocity, and angular velocities of the arm.  Given this information, the agent has to learn how to best select actions.  The action space is continuous and expressed as a 4D vector, corresponding to torque applicable to two joints. Each entry in the action vector must be a number in the range \[-1,+1\].

### Distributed Training
For this project, there are 2 versions of the Unity environment available :
* A Reacher environment with a single agent.
* The second version contains 20 identical agents, each with its own copy of the environment.

The second version is useful for algorithms like [PPO](https://arxiv.org/abs/1707.06347), [A3C](https://arxiv.org/abs/1602.01783), and [D4PG](https://arxiv.org/abs/1804.08617) that use multiple, non-interacting, and parallel copies of the same agent to distribute the task for gathering experience. I solve this parallel version of the environment here.

### Prerequisites
1. Python3.6
2. PyTorch v0.4 (or, higher might work)
3. Unity ML-Agents v0.4 

###### Note that you don't need to install Unity! Also, this project environment is similar, but not identical to the Reacher environment on the [Unity ML-Agents Github page](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md). You can find a complete list of the dependencies in the repo of **Deep Reinforcement Learning ND** at Udacity [here](https://github.com/udacity/deep-reinforcement-learning#dependencies)

### Getting Started
1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:

#### Version 1: One (1) Agent
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)


#### Version 2: Twenty (20) Agents
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/one_agent/Reacher_Linux_NoVis.zip) (version 1) or [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P2/Reacher/Reacher_Linux_NoVis.zip) (version 2) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the Linux operating system above.)

2. Place the file in the same directory as the codes, and unzip (or decompress) the file. 

#### Code Description 
Here, I implement [Deep Deterministic Policy Gradient (DDPG)](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf), an Actor-Critic algorithm appropriate for continuous control tasks. The approach described in the paper follows the off-policy method to train both actor and critic models. Code files are listed below:

* model.py _(actor and critic networks used as the function approximator)_
* ddpg_agent.py _(DDPG agent)_
* Continuous_Control.ipynb _(contains the training and inference code for Reacher environment)_
* checkpoint_actor_*.pth _(actor checkpoint files -- upto 300 episodes)_
* checkpoint_critic_*.pth _(critic checkpoint files -- upto 300 episodes)_

#### Optional:
You can build your own environment in Unity ML-Agents following the instructions [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Getting-Started-with-Balance-Ball.md)
