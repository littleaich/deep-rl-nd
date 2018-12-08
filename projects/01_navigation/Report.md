[//]: # (Image References)

[dqn]: https://github.com/littleaich/deep-rl-nd/blob/master/projects/01_navigation/figures/dqn.png "Learning Algorithm"
[train-stats]: https://github.com/littleaich/deep-rl-nd/tree/master/projects/01_navigation/figures/training.png "Training Statistics"

# Implementation Details
Here, I implement simple [Deep Q-Network (DQN)](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf), which is the off-policy Q-learning algorithm using deep network as the function approximator. I also employ the idea **experience replay** and **fixed-Q table** described in the DQN paper and also in the Udacity video lessons. Code files are listed below:

* model.py _(deep network used as the function approximator)_ 
* dqn_agent.py _(Q-learning agent)_
* Navigation.ipynb _(contains the training and inference code for banana  game)_
* checkpoint.pth _(latest checkpoint file -- upto 1000 episodes)_
* model_best.pth _(best model and optimizer states, should be used for inference)_

#### Algorithm

The pseudocode for the algorithm is given below from the [DQN](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf) paper.

<!--
![Learning Algorithm][dqn]
-->


<div class="fig figcenter fighighlight">
  <img src="https://github.com/littleaich/deep-rl-nd/blob/master/projects/01_navigation/figures/dqn.png" width="50%">
  <div class="figcaption" style="color:gray; font-size:16px; font-family:monospace" align="center">
  </div>
</div>
&nbsp;


#### Hyperparameters
According to the project requirement, **an average score of +13 over 100 consecutive episodes** is considered solved and that is achievable within 1800 episodes. Using a simple fully connected neural network with 2 hidden layers of size 32 each, I was able to obtain that within 1000 episodes. Here are list of hyperparameters used for the experiment:
* number of episodes: 1000
* _epsilon_ for _epsilon_-greedy policy
    * initial: 1.0
    * final: 0.1
    * decay: 0.995
* batch size: 64
* discount factor: 0.99
* soft update parameter: 0.001 
* learning rate: 0.0005
* buffer length _(experience replay)_: 100,000
* update step _(fixed-Q learning)_: 4
* loss function: mean-squared error _(MSE)_

#### Architecture
I employ a simple deep model comprising only fully connected (FC) layers as described below:
| Layer No | Type | #Input | #Output |
|:--------:|:----:|:------:|:-------:|
|     1    |  FC  |   37   |    32   |
|     2    |  FC  |   32   |    32   |
|     3    |  FC  |   32   |    4    |

#### Training Statistics
![Training Statistics][train-stats]

#### Future Work
* Implementation of [Dueling network](https://arxiv.org/abs/1511.06581)
* Utilization of the advanced concepts from CNN and RNN family of architectures for improved performance.

