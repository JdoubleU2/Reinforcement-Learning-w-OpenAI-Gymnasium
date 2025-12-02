# Modern AI Final Project – Reinforcement Learning with OpenAI Gymnasium

This repository contains the code and experiments for my Modern Artificial Intelligence final project exploring Deep Q-Networks (DQN) and Proximal Policy Optimization (PPO) on Atari and MuJoCo environments using Stable Baselines3 (SB3) and Gymnasium.

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


<p align="center">
  <video src="https://github.com/user-attachments/assets/bd76e72c-597b-4acd-bc3a-86c34ce145fb" width="480" controls>
    Your browser does not support the video tag.
  </video>
</p>

- **Ant (PPO)**: Learns to move forward robustly with stable reward curves after tuning PPO hyperparameters.


<p align="center">
  <video src="https://github.com/user-attachments/assets/5dd3378d-4cb8-4ed6-9cde-25c9c515b078" width="480" controls>
    Your browser does not support the video tag.
  </video>
</p>

- **Riverraid (DQN/PPO)**: Performance improves with reward shaping but remains unstable, illustrating challenges of noisy, dense reward structures and catastrophic forgetting.


<p align="center">
  <video src="https://github.com/user-attachments/assets/c2c9683e-3b82-452f-96d8-1edba51056e7" width="480" controls>
    Your browser does not support the video tag.
  </video>
</p>

- **Breakout (DQN)**: Reaches double-digit average scores and shows improved play after inference tweaks, with reward still increasing at the end of training. 


<p align="center">
  <video src="https://github.com/user-attachments/assets/4508b7e9-780c-42b8-b903-99e6a6c7b2fa" width="480" controls>
    Your browser does not support the video tag.
  </video>
</p>

- **Reacher (PPO)**: Converges to a plateaued high reward, keeping the arm close to the target across episodes.


<p align="center">
  <video src="https://github.com/user-attachments/assets/fe4f5875-4cd3-4a85-9358-9e26c5eb824e" width="480" controls>
    Your browser does not support the video tag.
  </video>
</p>


For detailed plots, hyperparameter tables, and discussion, see `ModernAI_FinalProjectPaper.pdf`.
