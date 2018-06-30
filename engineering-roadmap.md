## Engineering Roadmap

### Algorithms

- add different networks: density net, choice net
- Make a recurrent convnet (last layer RNN)
- curiosity for PPO/A2C
- general Hydra architecture for all algos
- generic distributed worker for all algos
- general value function from Sutton and Barto last chapter
- PGQL https://arxiv.org/pdf/1611.01626.pdf
- autoreward with IRL: https://arxiv.org/pdf/1806.04640.pdf and https://arxiv.org/abs/1806.01946
- World model, GAN
- MAML, meta learning formulation from Pieter’s keynote
- DYNA and full model based methods
- Hindsight experience replay
- neuroevolution

### Environments

- build the reacher and push unity envs
- add OpenAI gym retro
- update unity env and release
- add GVG-AI

### Saving

- save entire agent. make independent of agent spec
- enjoy mode tau for boltzmann
- model saving: the best and the latest, checkpointing per 100 epi or 500 for big games.
- turn clock to saved stage. only for resume training.
- for enjoy mode, just load whole agent at end-stage, clock is restarted.
- resume training via model reload and clock turning

### Misc
- ability to resume from random search
- use torch vision tool for images, replace util
- early termination on solved condition
- add preprocessor: rms, ob std and clip
- add mltest
- tensor board
- Parameter noise from baselines
- Change Adam. MA convergence problem
- long term: let memory keep soft reference to data space, make data space take arbitrary data.