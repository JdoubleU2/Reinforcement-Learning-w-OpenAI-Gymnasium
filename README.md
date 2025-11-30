# Modern AI Final Project – Reinforcement Learning with OpenAI Gymnasium

This repository contains the code and experiments for a Modern Artificial Intelligence final project exploring Deep Q-Networks (DQN) and Proximal Policy Optimization (PPO) on Atari and MuJoCo environments using Stable Baselines3 (SB3) and Gymnasium.

---

## Project overview

The goal of this project is to study how value-based and policy-gradient reinforcement learning algorithms perform across discrete and continuous control tasks. The work covers four main tasks:

- Discrete vs continuous control (Atari Freeway, MuJoCo Ant)
- Frequent-reward discrete environment (Atari Riverraid)
- Sparse-reward discrete environment (Atari Breakout)
- Continuous control environment (MuJoCo Reacher)

All experiments and analyses are documented in `ModernAI_FinalProjectPaper.pdf`.

---

## Environments and algorithms
| Task | Environment | Type | Algorithm | Notes |
|------|-------------|------|-----------|-------|
| 1 | Atari Freeway | Discrete | DQN (CNN policy) | Uses SB3 Atari baseline hyperparameters for stable learning. |
| 1 | MuJoCo Ant | Continuous | PPO (MLP policy) | Hyperparameters inspired by the PPO paper and SB3 MuJoCo baselines. |
| 2 | Atari Riverraid | Discrete, frequent reward | DQN / PPO (CNN) | Custom survival and milestone rewards to reduce suicidal behavior. |
| 3 | Atari Breakout | Discrete, sparse reward | DQN (CNN) | Inference tweaks: auto-fire after life loss and short NOOP warm-up. |
| 4 | MuJoCo Reacher | Continuous | PPO (MLP) | Reacher arm tracks random targets within 50 timesteps. |

DQN is used for image-based discrete Atari games, while PPO is used for continuous control in MuJoCo. Stable Baselines3 provides the reference implementations and exposes hyperparameters such as learning rate, gamma, buffer size, batch size, `n_steps`, entropy coefficient, clip range, GAE lambda, max gradient norm, and value function coefficient.

---
## Results (high level)

- **Freeway (DQN)**: Achieves a mean score around the low 20s, indicating convergence to a near-optimal policy under the given training budget. 
- **Ant (PPO)**: Learns to move forward robustly with stable reward curves after tuning PPO hyperparameters.  
- **Riverraid (DQN/PPO)**: Performance improves with reward shaping but remains unstable, illustrating challenges of noisy, dense reward structures and catastrophic forgetting.
- **Breakout (DQN)**: Reaches double-digit average scores and shows improved play after inference tweaks, with reward still increasing at the end of training. 
- **Reacher (PPO)**: Converges to a plateaued high reward, keeping the arm close to the target across episodes.

For detailed plots, hyperparameter tables, and discussion, see `ModernAI_FinalProjectPaper.pdf`.

This project was completed as part of **ELEG 6360: Modern Artificial Intelligence** in the Department of Electrical and Computer Engineering at Prairie View A&M University.