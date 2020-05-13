## Learning Algorithm
Based on my learning from the previous project (Continuous Control) and Udacity's Multi-Agent RL example, I decided to reuse a big chunk of existing code. The solution uses a Multi Agent Deep Deterministic Policy Gradients ([MADDPG](https://papers.nips.cc/paper/7217-multi-agent-actor-critic-for-mixed-cooperative-competitive-environments.pdf)). It builds on top of DDPG which in turn is an enhancement of deep Q-learning algorithm(DQN). Multi-agent systems learn to perform complex tasks while simultaneously collaborating and/or competing with other agents.

The environment for the project requires the training of two separate agents, and the agents need to collaborate under certain situations (don't let the vall hit the ground) and compete under other situations (get as many points as possible). In our case, each agent in this model has its own actor and critic model. Each actor receive individual state or observations as input and provide action as output. The critic model of each actor receives the states and actions of all actors. The agents use a common experience replay buffer during training. 

It took many iterations of tweaking hyperparams and rerunning the model. The results were not consistent. I started with a list of params I was going to modify and experiment. I updated one parameter a time with extreme value first, trained, tweaked the param again to see the impact on performance and continued with the next.

## Network Architecture
I didn't change much from the basic implementation in terms of number layers. The network architecture is made up of two fully connected hidden layers with 256 units and ReLu action function for both actors and critics. In order to help speed up learning and avoid getting stuck in a local minimum, batch normalization was used for each hidden layer for both actor and critic networks. Tanh activation function was used on the output layer for the actor-network as it ensures that every entry in the action vector is a number between -1 and 1. Adam optimizer was used for both actor and critic networks.

## Plot of Rewards


## Ideas for Future Work
