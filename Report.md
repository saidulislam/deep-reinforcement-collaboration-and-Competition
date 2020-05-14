## Learning Algorithm
Based on my learning from the previous project (Continuous Control) and Udacity's Multi-Agent RL example, I decided to reuse a big chunk of existing code. The solution uses a Multi Agent Deep Deterministic Policy Gradients ([MADDPG](https://arxiv.org/pdf/1706.02275.pdf)). It builds on top of DDPG which in turn is an enhancement of deep Q-learning algorithm(DQN). Multi-agent systems learn to perform complex tasks while simultaneously collaborating and/or competing with other agents.

The environment for the project requires the training of two separate agents, and the agents need to collaborate under certain situations (don't let the vall hit the ground) and compete under other situations (get as many points as possible). In our case, each agent in this model has its own actor and critic model. Each actor receive individual state or observations as input and provide action as output. The critic model of each actor receives the states and actions of all actors. The agents use a common experience replay buffer during training. 

It took many iterations of tweaking hyperparams and rerunning the model. The results were not consistent. I started with a list of params I was going to modify and experiment. I updated one parameter a time with extreme value first, trained, tweaked the param again to see the impact on performance and continued with the next.

### Why MADDPG
To model more real-world scenario, we need multi-agent systems which learn to perform complex tasks while simultaneously collaborating and/or competing with other agents. The more complex the task, more likely that multi-agents are needed. One of the advantages of a multi-agent approach is this additional factor of learning via cooperation or competition. Instead of one agent trying to master several tasks, the tasks can be divided among multiple agents and one can agent can utilize the knowledge acquired by the other. This ensures solving much more complex tasks modeling real-world situations such as simulating a self-driving car or in our case playing tennis.


### Some approaches


### Noise


### Hyperparameters why


### Model architecture for Actor/Critic


## Network Architecture
I didn't change much from the basic implementation in terms of number layers. The network architecture is made up of two fully connected hidden layers with 256 units and ReLu action function for both actors and critics. In order to help speed up learning and avoid getting stuck in a local minimum, batch normalization was used for each hidden layer for both actor and critic networks. Tanh activation function was used on the output layer for the actor-network as it ensures that every entry in the action vector is a number between -1 and 1. Adam optimizer was used for both actor and critic networks.

## Hyperparameters
- Buffer Size = 10000
- Batch Size = 64
- Noise Start = 0.5
- Noise Decay = 1.0
- Update Interval = 2
- Gamma/Discount Factor = .9999
- tau = 1e-3
- learning rate (actor) = 1e-4
- learning rate (critic) = 3e-4

## Plot of Rewards
<img src="images/collaboration.png" align="top-left" alt="" title="Plot" />

## Ideas for Future Work
- Experiment with incorporating prioritized replay. It should help further reduce the correlations so that there is less bias in the agent's training while it learns the optimal policy.
- Experiment using Multi-Agent Proximal Policy Optimization (MAPPO) to see how it compares to MADDPG.
