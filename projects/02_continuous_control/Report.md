[//]: # (Image References)

[ddpg]: https://github.com/littleaich/deep-rl-nd/blob/master/projects/02_continuous_control/figures/ddpg.png "Learning Algorithm"
[train-stats]: https://github.com/littleaich/deep-rl-nd/blob/master/projects/02_continuous_control/figures/training.png "Training Statistics"

# Implementation Details
Here, I implement [Deep Deterministic Policy Gradient (DDPG)](https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf), an Actor-Critic algorithm appropriate for continuous control tasks. The approach described in the paper follows the off-policy method to train both actor and critic models. Code files are listed below:

* model.py _(actor and critic networks used as the function approximator)_
* ddpg_agent.py _(DDPG agent)_
* Continuous_Control.ipynb _(contains the training and inference code for Reacher environment)_
* checkpoint_actor_*.pth _(actor checkpoint files -- upto 300 episodes)_
* checkpoint_critic_*.pth _(critic checkpoint files -- upto 300 episodes)_

#### Algorithm

The pseudocode for the algorithm is given below from the [DDPG](https://arxiv.org/pdf/1509.02971.pdf) paper.

<!--
![Learning Algorithm][ddpg]
-->


<div class="fig figcenter fighighlight">
  <img src="https://github.com/littleaich/deep-rl-nd/blob/master/projects/02_continuous_control/figures/ddpg.png" width="50%">
  <div class="figcaption" style="color:gray; font-size:16px; font-family:monospace" align="center">
  </div>
</div>
&nbsp;


#### Hyperparameters
According to the project requirement, **an average score of +30 over 100 consecutive episodes** is considered solved. Using a simple fully connected neural network with 2 hidden layers of size 64 each (both actor and critic), I was able to obtain that in less than 300 episodes in the 20-agents version of the environment. Here are list of hyperparameters used for the experiment:
* number of episodes: <300 (I started getting score of 30+ from <100 episodes)
* batch size: 128
* discount factor: 0.99
* soft update parameter: 0.01
* learning rate: 0.001 (both actor and critic) with ADAM optimizer
* buffer length _(experience replay)_: 100,000
* Ornstein-Uhlenbeck (OH) process is used to add noise in actor predictions.

#### Architecture
I employ a simple deep model comprising only fully connected (FC) layers as described below:
<table class="tg">
  <tr>
    <th class="tg-uys7">Layer No</th>
    <th class="tg-uys7">Type</th>
    <th class="tg-uys7">#Input</th>
    <th class="tg-uys7">#Output</th>
  </tr>
  <tr>
    <td class="tg-uys7">1</td>
    <td class="tg-uys7">FC</td>
    <td class="tg-uys7">33</td>
    <td class="tg-uys7">64</td>
  </tr>
  <tr>
    <td class="tg-uys7">2</td>
    <td class="tg-uys7">FC</td>
    <td class="tg-uys7">64</td>
    <td class="tg-uys7">64</td>
  </tr>
  <tr>
    <td class="tg-uys7">3</td>
    <td class="tg-uys7">FC</td>
    <td class="tg-uys7">64</td>
    <td class="tg-uys7">4(actor)/1(critic)</td>
  </tr>
</table>

#### Training Statistics
<!--
![Training Statistics][train-stats]
-->

<div class="fig figcenter fighighlight">
  <img src="https://github.com/littleaich/deep-rl-nd/blob/master/projects/02_continuous_control/figures/training.png" width="50%">
  <div class="figcaption" style="color:gray; font-size:16px; font-family:monospace" align="center">
  </div>
</div>
&nbsp;


#### Future Work
* I would like to try the on-policy version of DDPG.
* Deeper understanding of the implications of OH noise in predictions.
