## Research Roadmap

### CER

- extend: reproduce CER on replay for all algos and envs
- new: use CER for PER as CPER and compare results
- Exponentially decay sampling from replay (old OpenAI Lab memory ideas)
- Research: SIL with CER and PER

### Hybrid Policy
- try Q with non-argmax output sampling like in PG
- try PG/AC methods with boltzmann/epsilon greedy policy

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
- Hydra experiment: compile a list of basic motor skills we think are crucial, train on each head-tail on disjoint tasks to master each head-tail individually. 
Then, switch training to using composite tasks and let it master them. Might need to add auxiliary network to prevent forgetting.
- Canonical experiments: Get results for all implemented algorithms on cartpole, lunar, mountain car, acrobot, gridworld, 2d and 3d ball + 2 - 3 more
- NN architecture - head, tail, restricted body connections, multi body weight sharing

### Tobias’s intuitive theory research
check in on their env again for intuitive physics

### Regularization
[Requests for Research 2.0](https://blog.openai.com/requests-for-research-2/)
Regularization as example that directly tackles the reproducibility question. lab provides code + data + run instruction. here's what we did, the results, and how to run it for yourself. Take a step back, here's why it's reproducible, because you are already seeing everything and can rerun it for yourself without extra work.

### OpenAI Retro contest
Apparently there's still room for improvement. Theoretical max score is 10k, top performance is only 4692. https://blog.openai.com/first-retro-contest-retrospective/

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
