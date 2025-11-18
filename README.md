# Regression-to-deep-learning-demo

This repository contains a hands-on demo showcasing **regression to deep learning** concepts.  
We generate non-linear 2D datasets, train small PyTorch neural networks, and visualize their decision boundaries.

---

## Overview

This project demonstrates:

- Generating 2D datasets with varying complexity (spirals)
- Preparing train and validation sets
- Building and training neural networks with PyTorch
- Experimenting with different architectures:
  - Number of hidden layers (depth)
  - Width of each layer (number of neurons)
- Visualizing:
  - Training and validation loss curves
  - Decision boundaries
- Comparing model performance and understanding overfitting/underfitting

---

## Key Insights: Layers & Neurons

- **More neurons or more layers ≠ better performance**  
  Too many neurons or layers can cause **overfitting**.  
  Small networks or too few neurons may lead to **underfitting**.

- **Rule of Thumb:**  
  Moderate depth + moderate width = best **generalization**.  
  A very large network does not always guarantee better performance.

---

## Requirements

- Python 3.x
- NumPy
- PyTorch
- Matplotlib

Install missing packages using pip:

```bash
pip install numpy torch matplotlib
