# REINFORCE CartPole-v0

**Name:** reinforce_cartpole

**Date completed:**

**Description:** Baseline experiment

**Hypotheses:** N/A

**Prerequisites:** N/A

**Algorithms:** REINFORCE

**Environments:** CartPole-v0

**Specs:**
```json
{
  "reinforce_cartpole": {
    "agent": [{
      "name": "Reinforce",
      "algorithm": {
        "name": "Reinforce",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "add_entropy": false,
        "entropy_weight": 0.01,
        "continuous_action_clip": 2.0,
        "training_frequency": 1
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPdefault",
        "hid_layers": [32],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "loss_spec": {
          "name": "MSELoss"
        },
        "optim_spec": {
          "name": "Adam",
          "lr": 0.01
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 500,
        "lr_decay_min_timestep": 1000,
        "gpu": true
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch",
      "max_generation": null
    },
    "search": {
      "agent": [{
        "net": {
          "hid_layers__choice": [
            [16],
            [64],
            [32, 16],
            [64, 32]
          ],
          "hid_layers_activation__choice": ["sigmoid", "relu", "tanh"],
          "optim_spec": {
            "lr__uniform": [0.0001, 0.2]
          }
        }
      }]
    }
  }
}
```

**Running instructions:** use the spec above

**Commit:** 454f620fce3e6fe2f87a91bffd74667d1f8a94f9

**Results summary:**
