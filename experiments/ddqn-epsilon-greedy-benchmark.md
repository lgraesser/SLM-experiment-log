# DDQN Epsilon-greedy Benchmark

[Proposed by DeepMind in 2015](https://arxiv.org/abs/1509.06461), Double-DQN is an extension of DQN to prevent value overestimation. It uses a separate target network to estimate the target value, and the two networks are rotated periodically.