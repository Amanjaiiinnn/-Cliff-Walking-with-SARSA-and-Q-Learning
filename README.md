# Reinforcement Learning: Cliff Walking with SARSA and Q-Learning

This repository explores the classic "Cliff Walking" reinforcement learning problem using two prominent Q-learning algorithms: SARSA (State-Action-Reward-State-Action) and Q-Learning.

## Project Overview

The Cliff Walking environment is a grid-world task where an agent must navigate from a start state to a goal state while avoiding a "cliff" region. Falling into the cliff results in a large negative reward and resets the episode. The goal is to find an optimal policy that minimizes the number of steps and maximizes cumulative reward, effectively finding the safest and shortest path to the goal.

This project implements and compares:

*   **SARSA (On-Policy TD Control)**: Learns the Q-value for the policy currently being followed, meaning it considers the next action chosen by the *same* exploration policy.
*   **Q-Learning (Off-Policy TD Control)**: Learns the optimal Q-value independently of the policy being followed, by assuming the agent takes the best possible next action.

## Environment: Gymnasium's CliffWalking-v1

The project utilizes the `CliffWalking-v1` environment from the Gymnasium library. This environment is a 4x12 grid where:

*   **Start State (S)**: Bottom-left corner.
*   **Goal State (G)**: Bottom-right corner.
*   **Cliff (C)**: The cells directly between S and G, excluding S and G, in the bottom row. Moving into a cliff cell results in a large negative reward (typically -100) and resets the agent to the start.
*   **Normal Cells**: Moving into any other cell gives a small negative reward (typically -1).
*   **Actions**: Up, Down, Left, Right.

## Implementation Details

The core of the solution involves:

*   **Q-Table**: A 2D NumPy array `q[state, action]` stores the estimated maximum future reward for taking a specific action in a specific state.
*   **Epsilon-Greedy Policy**: Used for action selection during training to balance exploration (trying new actions) and exploitation (choosing actions with the highest known Q-value).
    *   `epsilon` parameter controls the trade-off.
*   **Learning Rate (`alpha`)**: Determines how much new information overrides old information.
*   **Discount Factor (`gamma`)**: Determines the importance of future rewards.
*   **Episodes**: The number of complete runs (from start to goal/cliff) the agent performs to learn.
