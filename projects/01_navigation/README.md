[//]: # (Image References)

[image1]: https://user-images.githubusercontent.com/10624937/42135619-d90f2f28-7d12-11e8-8823-82b970a54d7e.gif "Trained Agent"

# Project 1: Navigation

### Introduction

This is the first project for the [**Deep Reinforcement Learning NanoDegree**](https://github.com/udacity/deep-reinforcement-learning) at Udacity. For this project, you will train an agent to navigate (and collect bananas!) in a large, square world. The agent will learn from information such as its velocity, along with ray-based perception of objects around its forward direction.   

![Trained Agent][image1]

A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana.  Thus, the goal of your agent is to collect as many yellow bananas as possible while avoiding blue bananas.  

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around agent's forward direction.  Given this information, the agent has to learn how to best select actions.  Four discrete actions are available, corresponding to:
- **`0`** - move forward.
- **`1`** - move backward.
- **`2`** - turn left.
- **`3`** - turn right.

The task is episodic, and in order to solve the environment, your agent must get **an average score of +13 over 100 consecutive episodes**.

### Prerequisites
1. Python3.6
2. PyTorch v0.4 (or, higher might work)
3. Unity ML-Agents v0.4 

###### Note that you don't need to install Unity! Also, this project environment is similar to, but not identical to the Banana Collector environment on the [Unity ML-Agents Github page](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#banana-collector)). You can find a complete list of the dependencies in the repo of **Deep Reinforcement Learning ND** at Udacity [here](https://github.com/udacity/deep-reinforcement-learning#dependencies)

### Getting Started
1. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.

2. Place the file in the same directory as the codes, and unzip (or decompress) the file. 

#### Code Description
Here, I implement simple [Deep Q-Network (DQN)](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf), which is the off-policy Q-learning algorithm using deep network as the function approximator. I also employ the idea **experience replay** and **fixed-Q table** described in the DQN paper and also in the Udacity video lessons. Code files are listed below:

* model.py _(deep network used as the function approximator)_ 
* dqn_agent.py _(Q-learning agent)_
* Navigation.ipynb _(contains the training and inference code for banana  game)_
* checkpoint.pth _(latest checkpoint file -- upto 1000 episodes)_
* model_best.pth _(best model and optimizer states, should be used for inference)_

#### Optional:
You can build your own environment in Unity ML-Agents following the instructions [here](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Getting-Started-with-Balance-Ball.md)
