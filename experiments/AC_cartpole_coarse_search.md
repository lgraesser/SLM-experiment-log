# Actor Critic Cartpole Coarse Search

**Name:** Actor Critic Cartpole Coarse Search

**Date completed:** 02/04/18

**Description:** Coarse search to start narrowing down on a good benchmark set of params for AC in this environment. A series of ablation studies will follow.

**Hypotheses:** N/A

**Prerequisites:** N/A

**Algorithms:** Actor Critic with Generalized Advantage Estimation, episodic training

**Environments:** Cartpole

**Specs:** ("actor_critic.json", "actor_critic_cartpole_coarse_search")

**Running instructions:**
```json
{
  "actor_critic.json": {
    "actor_critic_cartpole_coarse_search": "search"
  }
}
```

**Commit**: c4538fc9c6e6cd5f1fb91ba742d95225ca4ad4a1

**Results summary:**

- adding entropy has a small improvement on speed
- gamma in range 0.9 - 0.925 improves speed
- 4 iterations of training per batch marginally best
- the smaller the network, the faster learning is. Single layer network with 16 nodes appears sufficient for this task and algorithm
- Separate params yields slightly stronger and more stable algorithms, but at the expense of speed
- Learning rate of 0.01 to 0.03 appears best
- Relu marginally better than sigmoid activations


data: ActorCritic_CartPole-v0_2018_02_04_013652
![](/assets/ActorCritic_CartPole-v0_experiment_graph.png)
data: actor_critic_cartpole_coarse_search_2018_01_30
![](/assets/actor_critic_cartpole_coarse_search_experiment_graph.png)
