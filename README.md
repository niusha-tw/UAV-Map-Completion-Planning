# UAV-Map-Completion-Planning
Integrating Learned Map Completion with Uncertainty-Aware Planning for Autonomous Robot Exploration –Advanced Topics Of AI_ Course project (Instituto Superior Técnico)
# Integrating Learned Map Completion with Uncertainty-Aware Planning for Autonomous Robot Exploration

Authors: 
Niusha Khosravi – PhD Student, Instituto Superior Técnico, University of Lisbon, Portugal  

---

## 📄 Overview

The project investigates how deep learning-based map completion (LaMa ensemble) can be integrated with uncertainty-aware frontier-based planning to improve autonomous robotic exploration. It evaluates how localization uncertainty (odometry drift) affects both predicted map quality and exploration efficiency.

---

## 🎯 Motivation

Autonomous robots rely on complete and accurate maps for navigation in unknown environments.  
While LiDAR-based SLAM provides accurate local maps, it:
- Remains incomplete until extensive exploration is done
- Suffers from accumulated pose drift
- Ignores the potential of learned models to predict unobserved regions

Key idea:  
Combine ensemble-based learned map completion with uncertainty-aware exploration planning to:
- Predict plausible unobserved regions
- Quantify model confidence
- Use uncertainty information to select more informative exploration targets

---

## 🛠 Methodology

The proposed system extends the [MapEx](https://arxiv.org/abs/2409.15590) framework with explicit pose uncertainty modeling and uncertainty-weighted frontier selection.

### Pipeline Stages
1. Sensing – 2D LiDAR simulation with realistic parameters for indoor exploration.
2. Map Prediction – Domain-adapted LaMa ensemble:
   - Takes partial occupancy grids + observation masks
   - Produces mean map predictions and pixel-wise uncertainty via ensemble variance
3. Planning – Frontier detection + uncertainty-weighted information gain:
   - Scores candidate frontiers based on potential uncertainty reduction per unit travel cost
4. Execution – Robot follows planned path to selected frontier
5. Pose Uncertainty Simulation – Controlled odometry drift to test robustness
6. Proposed Extensions – EKF + scan-to-map registration for drift correction (future work)

---

## 📊 Key Findings

- Without drift – The `visvarprob` (uncertainty-aware) approach yields the highest IoU and most efficient coverage.
- With drift – Both deterministic and probabilistic methods degrade, but `visvarprob` remains more robust than `visvar`.
- Drift impact – Causes misaligned frontier detection, redundant paths, and poor inpainting performance due to misregistered observations.
- Conclusion – Tight integration of SLAM, uncertainty-aware planning, and learned mapping is essential for real-world deployment.

---


