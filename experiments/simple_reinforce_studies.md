# Simple Reinforce Studies

**Name:** Simple Reinforce Studies

**Date completed:** 2018_02_16

**Description:** Simple set of experiments using REINFORCE in the CartPole environment. They are intended to illustrate the effect of varying entropy, gamma (the discount rate), and the learning rate.

**Hypotheses:** N/A

**Prerequisites:** N/A

**Algorithms:** Reinforce

**Environments:** CartPole-v0

**Specs:** ("reinforce_cartpole_studies.json")

**Running instructions:**
Save the following in config/experiments.json

```json
{
  "reinforce_cartpole_studies.json": {
    "reinforce_cartpole_gamma": "search",
    "reinforce_cartpole_lr": "search",
    "reinforce_cartpole_entropy": "search",
  }
}
```

Then run in the library root folder
```bash
yarn start
```

**Commit**: 259747c023822c4341fc79a2caca25cbf37546aa

**Results summary:**

![](/assets/reinforce_cartpole_gamma_experiment_graph.png)
![](/assets/reinforce_cartpole_entropy_experiment_graph.png)
![](/assets/reinforce_cartpole_lr_experiment_graph.png)
