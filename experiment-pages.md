```json
{
  "reinforce.json": {
    "reinforce_mlp_cartpole": "search",
    "reinforce_rnn_cartpole": "search",
  },
  "ac.json": {
    "ac_mlp_shared_cartpole": "search",
    "ac_mlp_separate_cartpole": "search",
    "ac_rnn_shared_cartpole": "search",
    "ac_rnn_separate_cartpole": "search",
  },
  "a2c.json": {
    "a2c_mlp_shared_cartpole": "search",
    "a2c_mlp_separate_cartpole": "search",
    "a2c_rnn_shared_cartpole": "search",
    "a2c_rnn_separate_cartpole": "search",
  },
  "ppo.json": {
    "ppo_mlp_shared_cartpole": "search",
    "ppo_mlp_separate_cartpole": "search",
    "ppo_rnn_shared_cartpole": "search",
    "ppo_rnn_separate_cartpole": "search",
  },
  "sil.json": {
    "sil_mlp_shared_cartpole": "search",
    "sil_mlp_separate_cartpole": "search",
    "sil_rnn_shared_cartpole": "search",
    "sil_rnn_separate_cartpole": "search",
  },
  "sarsa.json": {
    "sarsa_mlp_boltzmann_cartpole": "search",
    "sarsa_mlp_epsilon_greedy_cartpole": "search",
    "sarsa_rnn_boltzmann_cartpole": "search",
    "sarsa_rnn_epsilon_greedy_cartpole": "search"
  },
  "dqn.json": {
    "vanilla_dqn_cartpole": "search",
    "dqn_boltzmann_cartpole": "search",
    "dqn_epsilon_greedy_cartpole": "search",
    "drqn_boltzmann_cartpole": "search",
    "drqn_epsilon_greedy_cartpole": "search"
  },
  "ddqn.json": {
    "ddqn_boltzmann_cartpole": "search",
    "ddqn_epsilon_greedy_cartpole": "search",
    "ddrqn_boltzmann_cartpole": "search",
    "ddrqn_epsilon_greedy_cartpole": "search"
  },
  "dueling_dqn.json": {
    "dueling_dqn_boltzmann_cartpole": "search",
    "dueling_dqn_epsilon_greedy_cartpole": "search",
  }
}
```

```json
{
  "reinforce.json": {
    "reinforce_mlp_pendulum": "search",
    "reinforce_rnn_pendulum": "search",
  },
  "ac.json": {
    "ac_mlp_shared_pendulum": "search",
    "ac_mlp_separate_pendulum": "search",
    "ac_rnn_shared_pendulum": "search",
    "ac_rnn_separate_pendulum": "search",
  },
  "a2c.json": {
    "a2c_mlp_shared_pendulum": "search",
    "a2c_mlp_separate_pendulum": "search",
    "a2c_rnn_shared_pendulum": "search",
    "a2c_rnn_separate_pendulum": "search",
  },
  "ppo.json": {
    "ppo_mlp_shared_pendulum": "search",
    "ppo_mlp_separate_pendulum": "search",
    "ppo_rnn_shared_pendulum": "search",
    "ppo_rnn_separate_pendulum": "search",
  },
  "ppo_sil.json": {
    "ppo_sil_mlp_shared_pendulum": "search",
    "ppo_sil_mlp_separate_pendulum": "search",
    "ppo_sil_rnn_shared_pendulum": "search",
    "ppo_sil_rnn_separate_pendulum": "search",
  },
  "sil.json": {
    "sil_mlp_shared_pendulum": "search",
    "sil_mlp_separate_pendulum": "search",
    "sil_rnn_shared_pendulum": "search",
    "sil_rnn_separate_pendulum": "search",
  }
}
```

Sep 9 2018

```json
{
  "reinforce_mlp_cartpole": {
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
        "add_entropy": true,
        "entropy_coef": 0.01,
        "training_frequency": 1,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "hid_layers": [64],
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
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 100
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "gamma__uniform": [0.97, 0.999]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "reinforce_rnn_cartpole": {
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
        "add_entropy": true,
        "entropy_coef": 0.01,
        "training_frequency": 1,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
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
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "gamma__uniform": [0.97, 0.999]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ac_mlp_shared_cartpole": {
    "agent": [{
      "name": "ActorCritic",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 100,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": true,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ac_mlp_separate_cartpole": {
    "agent": [{
      "name": "ActorCritic",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 100,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": false,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ac_rnn_shared_cartpole": {
    "agent": [{
      "name": "ActorCritic",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 100,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": true,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ac_rnn_separate_cartpole": {
    "agent": [{
      "name": "ActorCritic",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 100,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": false,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_gae_mlp_shared_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": true,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": true,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "lam__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_gae_mlp_separate_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": true,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": false,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "lam__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_gae_rnn_shared_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": true,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": true,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "lam__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_gae_rnn_separate_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": true,
        "lam": 1.0,
        "use_nstep": false,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": false,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "lam__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_nstep_mlp_shared_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": true,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": true,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "num_step_returns__uniform": [1, 4, 8],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_nstep_mlp_separate_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": true,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": false,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "num_step_returns__uniform": [1, 4, 8],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_nstep_rnn_shared_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": true,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": true,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "num_step_returns__uniform": [1, 4, 8],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "a2c_nstep_rnn_separate_cartpole": {
    "agent": [{
      "name": "A2C",
      "algorithm": {
        "name": "ActorCritic",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "use_gae": false,
        "lam": 1.0,
        "use_nstep": true,
        "num_step_returns": 1,
        "add_entropy": true,
        "entropy_coef": 0.01,
        "policy_loss_coef": 1.0,
        "val_loss_coef": 0.01,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": false,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "num_step_returns__uniform": [1, 4, 8],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ppo_mlp_shared_cartpole": {
    "agent": [{
      "name": "PPO",
      "algorithm": {
        "name": "PPO",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "lam": 1.0,
        "clip_eps": 0.10,
        "entropy_coef": 0.01,
        "val_loss_coef": 0.1,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": true,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "lam__uniform": [0.1, 1.0],
          "clip_eps__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ppo_mlp_separate_cartpole": {
    "agent": [{
      "name": "PPO",
      "algorithm": {
        "name": "PPO",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "lam": 1.0,
        "clip_eps": 0.10,
        "entropy_coef": 0.01,
        "val_loss_coef": 0.1,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicyReplay"
      },
      "net": {
        "type": "MLPNet",
        "shared": false,
        "hid_layers": [64],
        "hid_layers_activation": "relu",
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "num_step_returns__uniform": [1, 4, 8],
          "clip_eps__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ppo_rnn_shared_cartpole": {
    "agent": [{
      "name": "PPO",
      "algorithm": {
        "name": "PPO",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "lam": 1.0,
        "clip_eps": 0.10,
        "entropy_coef": 0.01,
        "val_loss_coef": 0.1,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": true,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "lam__uniform": [0.1, 1.0],
          "clip_eps__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  },
  "ppo_rnn_separate_cartpole": {
    "agent": [{
      "name": "PPO",
      "algorithm": {
        "name": "PPO",
        "action_pdtype": "default",
        "action_policy": "default",
        "action_policy_update": "no_update",
        "explore_var_start": null,
        "explore_var_end": null,
        "explore_anneal_epi": null,
        "gamma": 0.99,
        "lam": 1.0,
        "clip_eps": 0.10,
        "entropy_coef": 0.01,
        "val_loss_coef": 0.1,
        "training_frequency": 1,
        "training_epoch": 8,
        "normalize_state": true
      },
      "memory": {
        "name": "OnPolicySeqReplay"
      },
      "net": {
        "type": "RecurrentNet",
        "shared": false,
        "hid_layers": [],
        "hid_layers_activation": "relu",
        "rnn_hidden_size": 64,
        "rnn_num_layers": 1,
        "seq_len": 4,
        "clip_grad": false,
        "clip_grad_val": 1.0,
        "use_same_optim": false,
        "actor_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "critic_optim_spec": {
          "name": "Adam",
          "lr": 0.02
        },
        "lr_decay": "rate_decay",
        "lr_decay_frequency": 1000,
        "lr_decay_min_timestep": 1000,
        "lr_anneal_timestep": 100000,
        "gpu": false
      }
    }],
    "env": [{
      "name": "CartPole-v0",
      "max_timestep": null,
      "max_episode": 500,
      "save_epi_frequency": 1000
    }],
    "body": {
      "product": "outer",
      "num": 1
    },
    "meta": {
      "distributed": false,
      "max_session": 4,
      "max_trial": 100,
      "search": "RandomSearch"
    },
    "search": {
      "agent": [{
        "algorithm": {
          "num_step_returns__uniform": [1, 4, 8],
          "clip_eps__uniform": [0.1, 1.0],
          "val_loss_coef__uniform": [0.01, 1.0]
        },
        "net": {
          "hid_layers_activation__choice": ["tanh", "relu", "selu"],
          "rnn_hidden_size__choice": [16, 32, 64],
          "actor_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          },
          "critic_optim_spec": {
            "lr__uniform": [0.0001, 0.1]
          }
        }
      }]
    }
  }
}
```



