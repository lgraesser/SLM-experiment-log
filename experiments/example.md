## Q-learning comparison

**Name:** e.g. *Q-learning comparison*

**Date completed:** e.g. *01/23/2018*

**Description:** brief description of the experiment. e.g. *Comparison of the DQN, DoubleDQN, and DuelingDQN algorithms on the benchmark set of environments. All hyper-parameters and network architecture should be held constant across algorithms so as to evaluate the performance difference from just the algorithm*

**Hypotheses:** brief description of what you expect to find e.g. *DQN will learn faster the other two algorithms on CartPole since the task is so simple. However it might not be as stable or consistent. DoubleDQN and DuelingDQN will be more stable, consistent, and achieve higher scores than DQN on the harder environment LunarLander. It is unclear whether they will learn faster*

**Prerequisites:** what needs to have been completed before running this experiment. e.g. *Param search has been run using DQN on CartPole-v0 and LunarLander-v0 to find a good set of params.*

**Algorithms:** algorithms involved. e.g.
- *DQN*
- *DoubleDQN*
- *DuelingDQN*

**Environments:** environments involved. e.g. *benchmark discrete environments*

**Specs:** specs involved. Specs should not be reused across experiments. e.g.
- *(dqn.json, dqn_benchmark)*
- *(dqn.json, doubledqn_benchmark)*
- *(dqn.json, duelingdqn_benchmark)*

**Running instructions:** Command to be copied and pasted into `experiments.json` along with any other notes for running the experiment *e.g. each trial should be run 10 times and the results averaged*
```json
{
  "dqn.json": {
    "dqn_benchmark": "benchmark",
  },
  "dqn.json": {
    "doubledqn_benchmark": "benchmark",
  },
  "dqn.json": {
    "duelingdqn_benchmark": "benchmark",
  },
}
```
**Results summary:** This should include a brief description of the results and links to the results files.
