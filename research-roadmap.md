## Research Roadmap

### CER

- extend: reproduce CER on replay for all algos and envs
- new: use CER for PER as CPER and compare results

### Regularization
[Requests for Research 2.0](https://blog.openai.com/requests-for-research-2/)
Regularization as example that directly tackles the reproducibility question. lab provides code + data + run instruction. here's what we did, the results, and how to run it for yourself. Take a step back, here's why it's reproducible, because you are already seeing everything and can rerun it for yourself without extra work.

### Hybrid Policy
- try Q with non-argmax output sampling like in PG
- try PG/AC methods with boltzmann/epsilon greedy policy

### Tobias’s intuitive theory research
check in on their env again for intuitive physics

### Multitask with hydra

- generalize hydra architecture to non-Q algos
- run experiments on hydra algos
- set up more multitask environment:
	- strategy: solve a, b, a-a, b-b, a-b, a*b
	- cartpole, 2dball
	- cartpole, acrobot
	- cartpole, gridworld
	- lunar, acrobot
	- 3dball
	- gridworld
	- arthur’s cartpole inside gridworld, i.e. a*b
- Canonical experiments: Get results for all implemented algorithms on cartpole, lunar, mountain car, acrobot, gridworld, 2d and 3d ball + 2 - 3 more
- NN architecture - head, tail, restricted body connections, multi body weight sharing

### Misc
* Fake rollout data training like supervised
* Multitask and architecture
* Correspondence
* Mutual Information ::Chong, see notebook::
* NN Frankenstein
* introspection vs reward signal
* GA, neuroevolution
* semantics grounding research. maybe do brain dump and research paper: ::Douwe Kiela::
* curriculum learning
* rewardless model-based like alpha go
* capacity measure
* homeostasis of NN 
* self-reward instead of human design
* meta learning using data vs human ingenuity
* focus on architecture design too, have memory.
* implement the env distribution distance idea
* implement the optimality/capacity for fitness idea.
* Multihead
* Breadboard dynamic graph 
