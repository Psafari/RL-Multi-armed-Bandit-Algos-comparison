# Multi-Armed Bandit Algorithms: 


## Overview

This repository contains the complete implementation and results for Assignment 1 of the Reinforcement Learning course. We implement and compare four multi-armed bandit algorithms across both stationary (Part 1) and non-stationary (Part 2) environments, providing comprehensive analysis of their performance characteristics.

## Algorithms Implemented


1. **Greedy**: Pure exploitation strategy (Q₀ = 0)
2. **ε-Greedy**: Balanced exploration-exploitation with ε=0.1
3. **Optimistic Greedy**: Greedy with optimistic initialization (Q₀ = 2.5)
4. **Gradient Bandit**: Preference-based learning with α=0.1

## Experimental Scenarios

### Part 1: Stationary Environment
- **Setup**: 10-armed bandit with N(μᵢ, 1) reward distributions
- **Arm means**: μᵢ drawn from N(0, 1)
- **Duration**: 2000 time steps per simulation
- **Repetitions**: 1000 independent simulations
- **Metrics**: Average reward and percentage optimal actions

### Part 2: Non-Stationary Environments
Four types of environmental changes:

1. **Drift**: μᵢ,ₜ = μᵢ,ₜ₋₁ + εᵢ,ₜ, εᵢ,ₜ ~ N(0, 0.01²)
2. **Mean-Reverting**: μᵢ,ₜ = 0.5μᵢ,ₜ₋₁ + εᵢ,ₜ, εᵢ,ₜ ~ N(0, 0.01²)
3. **Abrupt**: Random permutation of means at t=501
4. **Reset**: Hard reset of action values at t=501

## Requirements

```
numpy>=1.21.0
matplotlib>=3.5.0
seaborn>=0.11.0
tqdm>=4.64.0
pandas>=1.3.0
scipy>=1.7.0
```


## Results Summary

### Part 1: Stationary Environment Performance

| Algorithm | Average Reward | % Optimal Actions | Key Characteristics |
|-----------|---------------|-------------------|---------------------|
| Gradient Bandit | 1.55 | 87% | Best overall performance |
| Optimistic Greedy | 1.45 | 85% | Excellent early exploration |
| ε-Greedy (ε=0.1) | 1.35 | 82% | Robust and reliable |
| Greedy | 1.0 | 37% | Poor due to no exploration |

### Part 2: Non-Stationary Environment Performance

| Change Type | Best Algorithm | % Optimal Actions | Key Insights |
|-------------|---------------|-------------------|--------------|
| Abrupt | Gradient Bandit | 88% | Preference-based adaptation excels |
| Drift | Gradient Bandit | 85% | Gradual changes easier to track |
| Mean-Reverting | Gradient Bandit | 85% | Bounded changes manageable |
| Reset | Gradient Bandit | 85% | Hard resets benefit most algorithms |



### Algorithm Rankings

1. **Gradient Bandit**: Superior in both stationary and non-stationary environments
2. **ε-Greedy**: Excellent robustness across all conditions  
3. **Optimistic Greedy**: Good for stationary, struggles with non-stationarity
4. **Greedy**: Poor performance due to lack of exploration
