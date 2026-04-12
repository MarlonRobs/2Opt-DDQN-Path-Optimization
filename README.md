# Autonomous Harvest Path Optimization using Spatial Decomposition DDQN

This repository contains the implementation of a hybrid route optimization framework for autonomous harvesting. The project leverages image processing for cluster detection and a **Double Deep Q-Network (DDQN)** agent combined with **2-Opt refinement** to solve the Traveling Salesperson Problem (TSP) in high-density orchard environments.

![Python Version](https://img.shields.io/badge/python-3.13.1-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Topic](https://img.shields.io/badge/robotics-precision_agriculture-orange)

## 📌 Project Overview

Optimizing the harvest path in an orchard of 22.47m x 13.06m is a significant computational challenge due to the high density of fruit clusters. This project proposes a "Divide and Conquer" strategy to make Reinforcement Learning feasible for large-scale path planning.

### Key Features:
*   **Image Processing Pipeline**: Uses morphological opening and contour-area detection to identify 340 fruit clusters from aerial imagery.
*   **Spatial Decomposition**: Divides the orchard into 10 sections (2x5 grid) to reduce the DDQN state-space complexity.
*   **Wavy Navigation Logic**: Implements a global "wavy" movement pattern to connect distributed local agents.
*   **2Opt-DDQN Hybrid**: Combines deep reinforcement learning with classical 2-Opt geometric refinement.

## 🚀 Performance
*   **DDQN vs. Greedy Nearest Neighbor**: 6.42% distance reduction.
*   **2Opt-DDQN vs. Greedy**: 9.64% total distance reduction.
*   **Convergence**: Training stabilizes at approximately $4200 \pm 500$ episodes per section.

---

## 💻 Hardware & Software

### Hardware Specifications
- **CPU**: AMD Ryzen 7 8845HS @ 3.8 GHz
- **GPU**: Radeon 780M Graphics (8GB VRAM)
- **RAM**: 16GB DDR5

### Software Requirements
- **Python**: 3.13.1 (or compatible 3.x)
- **Libraries**: `tensorflow`, `keras`, `opencv-python`, `numpy`, `scipy`, `matplotlib`.

---

## 📂 Repository Structure

The project consists of two main Jupyter Notebooks:

### 1. `Path_Optimization_Training.ipynb`
This file contains the backbone of the project:
- **Classes & Functions**: Definition of the DDQN Agent, the environment, and the GNN baseline.
- **Image Analysis**: Morphological operations to separate overlapping fruits and centroid calculation.
- **Training Pipeline**: Distributed training of 10 DDQN agents for each orchard section.

### 2. `Comparison_and_Visualization.ipynb`
This file is dedicated to analysis and graphical results:
- **Metric Plots**: Cumulative reward vs. episodes and distance evolution graphs.
- **Path Visualization**: Comparison of generated routes (GNN vs. DDQN vs. 2Opt-DDQN) for individual sections and the full orchard.
- **Statistical Tables**: Bar charts comparing the efficiency of the three models.

---

## 🛠 Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/MarlonRobs/harvest-path-optimization.git
   cd harvest-path-optimization
