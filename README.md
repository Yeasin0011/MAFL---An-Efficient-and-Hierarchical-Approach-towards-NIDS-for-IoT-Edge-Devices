## 🌐 MAFL: Metric Annealed Federated Learning for IoT NIDS

This repository features the complete implementation of **Metric Annealed Federated Learning (MAFL)**, an advanced and highly efficient framework for **Network Intrusion Detection Systems (NIDS)** tailored for deployment on **resource-constrained IoT edge devices**[cite: 282, 284]. [cite_start]By combining a specialized hierarchical model architecture with a novel aggregation strategy, MAFL addresses the core challenges of Federated Learning (FL) in distributed IoT networks: handling **non-IID data**, minimizing **computational overhead**, and reducing **communication costs**[cite: 283].

---

### 🧠 Core Components & Architecture

#### 1. Lightweight Hierarchical CNN-BiLSTM (HR-MAFL)
[cite_start]We introduce a deep learning model meticulously optimized for edge devices, containing only **$\sim 14,000$ total parameters**[cite: 41, 284].
* [cite_start]**Dual Heads:** The architecture includes shared feature extraction layers feeding into separate **binary** (normal vs. attack) and **multiclass** (attack type) classification heads, allowing simultaneous training for intrusion detection and type identification[cite: 143].
* [cite_start]**Efficiency:** This model is significantly lighter than comparable models, which often require in the range of 16,000 and 254,000 parameters[cite: 42].

#### 2. Metric Annealed Aggregation
[cite_start]MAFL introduces a unique server-side strategy based on **Simulated Annealing** to govern client selection and global model aggregation[cite: 189].
* [cite_start]**Performance-Based Metric:** Clients are evaluated using an **energy metric ($E$)** that prioritizes detection capability while maintaining a **low false positive rate**[cite: 193, 194].
* [cite_start]**Adaptive Probability:** Updates are accepted probabilistically using an exponential function $P=exp(\frac{E_{curr}-E_{prev}}{T})$, where an adaptive **temperature parameter ($T$)** controls the exploration-exploitation trade-off, enhancing robustness on heterogeneous non-IID data[cite: 209, 218].

#### 3. Optimized Training and Inference
* [cite_start]**Three-Phase Local Training:** A curriculum learning strategy is used to prevent catastrophic interference between the two tasks: first, training the binary head, then the multiclass head, and finally, a joint fine-tuning phase[cite: 157, 187].
* [cite_start]**Hierarchical Inference:** During deployment, the binary head first filters traffic, and only samples predicted as attacks proceed to the multiclass head, reducing unnecessary computations by approximately **$36.1\%$**[cite: 220, 223].

---

### 🎯 Results & Impact

On the **UNSW-NB15 dataset**, MAFL achieved:
* [cite_start]**Binary Classification Accuracy:** $\mathbf{98.8\%}$[cite: 42, 284].
* [cite_start]**Multiclass Classification Accuracy:** $\mathbf{81.1\%}$[cite: 42, 284].
* [cite_start]The system achieved an overall approximate **$60\%$ reduction in communication overhead** compared to FedAvg due to its adaptive client selection[cite: 269].

[cite_start]MAFL establishes itself as a viable and efficient framework for secure intrusion detection in distributed IoT networks[cite: 44].

---

### 📚 References

[cite_start]The MAFL framework leverages the **Flower Framework** for federated learning simulation [cite: 39, 191] [cite_start]and utilizes the **UNSW-NB15 Dataset** for evaluation[cite: 100].

### 💡 Future Directions

[cite_start]Future work will focus on integrating stronger privacy guarantees (e.g., differential privacy), optimizing client selection using reinforcement learning, and expanding evaluation to real-world IoT scenarios[cite: 285, 286].
