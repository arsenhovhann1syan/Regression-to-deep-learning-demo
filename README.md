# Deep Learning Exploration: Spiral Dataset Classification

This repository contains a set of experiments conducted using **PyTorch** to determine the optimal Multilayer Perceptron (MLP) architecture for classifying the non-linearly separable **Two-Spirals Dataset**. The goal was to study the trade-off between model complexity (depth and width) and generalization performance.

## 🛠️ Methodology and Dataset

The classification task uses a **medium-complexity two-spirals dataset**. This synthetic dataset, generated via the `make_spiral` function, is challenging because a solution requires a highly non-linear decision boundary, making it an excellent benchmark for deep learning models.

* **Generation Parameters:** N=800 samples with a **noise level of 0.15**.
* **Model:** Fully-connected MLPs (ReLU activation, Sigmoid output).

---

## Experimental Results Summary

We tested ten different MLP architectures. Below are the key configurations and their corresponding **Validation Accuracy** scores:

### Performance Breakdown by Architecture:

* **Micro Models (Underfitting):**
    * Micro 1 layer `[4]`: Accuracy **0.531**
    * Micro 2 layers `[4, 4]`: Accuracy **0.625**
* **Balanced & Strong Performers:**
    * 1 hidden layer `[32]`: Accuracy **0.850** (Significant Improvement)
    * 2 hidden layers `[16, 16]`: Accuracy **0.881**
    * 2 hidden layers `[32, 16]`: Accuracy **0.881**
* **Optimal & Near-Optimal Performers:**
    * **2 hidden layers `[32, 32]`**: Accuracy **0.894**
    * **3 hidden layers `[16, 12, 8]`**: Accuracy **0.894**
* **Deeper/Wider Models:**
    * 3 hidden layers `[16, 16, 16]`: Accuracy **0.869** (Slightly decreased performance)
    * 3 hidden layers `[32, 24, 16]`: Accuracy **0.863** (Lower accuracy)
    * 4 hidden layers `[32, 24, 16, 8]`: Accuracy **0.869** (Deeper complexity)

---

## 🏆 Optimal Architectures

Two models achieved the peak validation accuracy of **0.894**, demonstrating the concept of "equifinality" in model selection, where multiple structures can achieve comparable optimal results:

1.  **Best Maximal Model (Wider):** `2 hidden layers [32, 32]`
2.  **Best Minimal Model (Deeper/Tapered):** `3 hidden layers [16, 12, 8]`

---

## 💡 Key Insights on Model Capacity

The results strongly support the general principles of selecting appropriate model capacity for a given task:

### 1. Underfitting
* **Description:** Small networks (e.g., `[4]`, `[4, 4]`) lack the capacity to learn the complex, non-linear patterns inherent in the spiral shape.
* **Illustration:** Accuracies of **0.531** and **0.625** for micro-models.

### 2. Overfitting Risk
* **Description:** Excessively large or deep networks, while powerful, risk memorizing training noise, which can slightly degrade validation performance compared to optimal models.
* **Illustration:** The deepest models (e.g., `[32, 24, 16]`) showed lower accuracy than the optimal ones.

### 3. Rule of Thumb
* **Description:** Finding a balance between depth and width ensures the best chance of learning the underlying function without memorizing noise.
* **Rule:** **Moderate depth + moderate width = best generalization.**
* **Illustration:** The models that strike a balance (`[32, 32]` and `[16, 12, 8]`) achieved the highest accuracy.

A very large network does not always guarantee better performance; finding the minimum effective capacity is crucial for efficiency and generalization.
