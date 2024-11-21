# Causal Curiosity in Reinforcement Learning

This repository contains the implementation of the causal curiosity framework described in Chapter 8 of the thesis. The framework integrates causal reasoning with reinforcement learning to create agents that actively explore and learn causal structures in their environment.

## Overview

The notebook implements a causal model-based reinforcement learning agent that is intrinsically motivated to discover and validate causal relationships. The agent combines:
- Traditional RL capabilities (state observation, action selection, reward optimization)
- Causal model learning through a discovery algorithm
- Intrinsic motivation mechanisms for causal exploration

## Requirements

```
python>=3.7
torch
numpy
networkx
pandas
causal-discovery-package  # for causal discovery algorithms
gymnasium                 # for RL environments
```

## Key Components

### 1. Causal Agent Architecture
- **Causal Model**: Maintains a DAG representing discovered causal relationships
- **Meta-controller**: Generates intrinsic rewards based on causal model stability
- **Controller**: Handles action selection considering both extrinsic and intrinsic rewards

### 2. Causal Discovery
The implementation offers two approaches for causal discovery:
- Full implementation using the causal discovery package
- Simplified version with basic rules for faster convergence:
  - Association: Identifies simultaneous events
  - Causation: Validates relationships through interventions

### 3. Action Selection
- Uses ε-greedy policy modified by causal knowledge
- Restricts action space to ancestors of reward variables
- Incorporates both exploration and exploitation phases

### 4. Training Process
The notebook includes experiments with:
- 500 episodes
- 100 trials per episode
- 5 variables sampled from a structural causal model (SCM)
- Random causal graph generation
- Linear relationships between variables

## Usage

1. Set up the environment:
```bash
pip install -r requirements.txt
```

2. Open the Jupyter notebook:
```bash
jupyter notebook causal_curiosity.ipynb
```

3. The notebook is organized into sections:
   - Environment setup
   - Agent implementation
   - Training loop
   - Visualization and analysis

## Key Functions

### Environment
- `create_random_scm()`: Generates random structural causal models
- `sample_from_scm()`: Samples values from the SCM

### Agent
- `update_causal_model()`: Updates the agent's causal graph
- `compute_intrinsic_reward()`: Calculates exploration bonus
- `select_action()`: Chooses actions based on causal knowledge

### Training
- `train_episode()`: Runs a single training episode
- `evaluate_performance()`: Measures agent's performance

## Visualization

The notebook includes visualizations for:
- Causal graph evolution
- Intrinsic reward profiles
- Learning curves
- Action selection patterns

## References

This implementation is based on the research presented in Chapter 8, which builds upon:
- Pearl's causality framework
- Reinforcement learning principles
- Causal discovery algorithms

## Contributing

Feel free to open issues or submit pull requests for:
- Bug fixes
- Performance improvements
- Additional features
- Documentation enhancements

## License

MIT License
