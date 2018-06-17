## Engineering Roadmap

### Algorithms

- [ ] Make a recurrent convnet (last layer RNN)
- [ ] general Hydra architecture for all algos
- [ ] generic distributed worker for all algos
- [ ] PGQL https://arxiv.org/pdf/1611.01626.pdf
- [ ] Hindsight experience replay
- [ ] neuroevolution

### Environments

- [ ] add OpenAI gym retro
- [ ] update unity env and release

### Saving

- [ ] save entire agent. make independent of agent spec
- [ ] enjoy mode tau for boltzmann
- [ ] model saving: the best and the latest, checkpointing per 100 epi or 500 for big games.
- [ ] turn clock to saved stage. only for resume training.
- [ ] for enjoy mode, just load whole agent at end-stage, clock is restarted.
- [ ] resume training via model reload and clock turning

### Misc
- [ ] ability to resume from random search
- [ ] use torch vision tool for images, replace util
- [ ] early termination on solved condition
- [ ] add preprocessor: rms, ob std and clip
- [ ] add mltest
- [ ] tensor board
- [ ] Parameter noise from baselines
- [ ] Change Adam. MA convergence problem 
- [ ] long term: let memory keep soft reference to data space, make data space take arbitrary data.