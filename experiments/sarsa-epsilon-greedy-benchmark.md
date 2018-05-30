# SARSA Epsilon-greedy Benchmark

[Proposed by Rummery and Rinanjan in 1994](
http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.17.2539&rep=rep1&type=pdf), SARSA uses the partial trajectory `s, a, r, s'` to calculate the current Q-estimate `x = Q(s, a)` and the target estimate Q value `y = r + gamma * Q(s', a')` (bootstrapping of the Bellman equation). The loss is calculated with `L(x, y)`.