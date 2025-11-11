# Tic-Tac-Toe Reinforcement Learning with Q-Learning

A reinforcement learning agent trained to play Tic-Tac-Toe using Q-Learning.  
The project explores how reward shaping, exploration decay, and opponent strategies influence learning and gameplay behavior.

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![RL](https://img.shields.io/badge/Reinforcement_Learning-Q_Learning-brightgreen.svg)
![Game](https://img.shields.io/badge/Game-TicTacToe-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)
![Notebook](https://img.shields.io/badge/Jupyter-Notebook-yellow.svg)

---

## Project Overview
This project trains a Q-Learning agent to master Tic-Tac-Toe and analyzes how reinforcement learning behaves in a simple, interpretable game setting.  

We systematically examine:

- Learning vs randomness
- Learning vs perfect play (MinMax)
- Impact of **reward shaping**
- Q-value heatmaps to understand agent intuition

The focus is **not just winning**, but understanding *how the agent learns strategy*.

---

## Objectives
- Train a Q-Learning agent for Tic-Tac-Toe  
- Compare performance against random and MinMax opponents  
- Visualize learning curves and Q-values  
- Study exploration-exploitation trade-offs  
- Demonstrate reward shaping impact  

---

## RL Setup
| Component | Description |
|---|---|
Algorithm | Q-Learning  
Policy | ε-greedy with decay  
State | 3×3 board (tabular)  
Actions | Valid moves (0-8)  
Training episodes | 200,000  

---

## Experiments & Results

### 🎯 Baseline — MinMax vs Random  
- MinMax never loses  
- ~90% wins, ~10% draws  
> Establishes optimal benchmark.

📈 `plots/WOT_MinMax_vs_RandomPlayer.png`

---

### 🧠 Q-Learning Agent vs Random Player  
- Starts ~40% wins (high exploration)  
- Improves steadily  
- Final: ~69% wins, ~20% losses, ~10% draws  

> Agent learns winning strategies successfully.

📈 `plots/WOT_RandomPlayer_vs_Agent.png`

---

### 🆚 Agent vs MinMax (No Reward Shaping)  
- 0 wins  
- ~50% draws, ~50% losses  

> Q-Learning avoids basic mistakes but **cannot beat optimal play**.

📈 `plots/WOT_MinMax_vs_Agent.png`

---

### 🎯 Reward-Shaped Agent vs MinMax  
Reward: + for taking center on first move.  

**Result:**  
- 0 losses across 200k games  
- 100% draws  

> Small reward tweak → **near-optimal strategy** (never loses).

📈 `plots/WOT_MinMax_vs_Agent_wMRF.png`

---

## Q-Value Heatmaps (Learning Insight)

Visualizing learned board preferences:


<p align="center">
  <img src="plots/heatMap_Before.png" width="45%" />
  &nbsp;&nbsp;
  <img src="plots/heatMap_After.png" width="45%" />
</p>

> Reward shaping leads to strategic behavior — agent prefers center and avoids losing positions.

---

## Summary of Results

| Experiment | Opponent | Result | Key Insight |
|---|---|---|---|
Baseline | MinMax vs Random | MinMax wins ~90% | Optimal benchmark |
Agent vs Random | Q-Learning | ~69% wins | Learns winning patterns |
Agent vs MinMax | Q-Learning | 0 wins, ~50% losses | Can't plan long-term |
Reward-Shaped Agent vs MinMax | Q-Learning + bonus | **0 losses** | Reward shaping → strategy |

---

## What I Learned
- How Q-Learning updates state-action values  
- Importance of ε-decay in exploration/exploitation  
- Reward shaping accelerates strategic learning  
- Tabular RL struggles vs optimal long-term planning  
- Heatmaps/Q-tables reveal agent decision patterns  

---

## How to Run
```bash
jupyter notebook RL-TicTacToe.ipynb
```

### Required libraries (if needed):
```bash
pip install numpy matplotlib
```

## Repository Structure
<pre>
📦 RL-TicTacToe
├── RL-TicTacToe.ipynb
├── plots/
│   ├── *.png  # performance charts & heatmaps
└── README.md
</pre>

## Future Improvements
- Extend to Deep Q-Networks (DQN)
- Interactive UI to play against the agent
