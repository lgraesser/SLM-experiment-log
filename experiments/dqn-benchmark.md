# DQN epsilon-greedy Benchmark

[Proposed by DeepMind in 2013](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf), Deep Q-Learning uses a deep neural network to approximate the Q-function - at a given state with multiple available actions, each of these have a Q-value, and the action with the highest is picked. DeepMind combined it with experience replay, frame-skip, and epsilon-greedy policy to obtain a breakthrough.
