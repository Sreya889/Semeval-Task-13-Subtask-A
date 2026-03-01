This repository contains the official implementation for our submission to SemEval-2026 Task 13 (Subtask A). Our system focuses on Out-of-Distribution (OOD) Robustness by prioritizing structural code logic over surface-level stylistic signatures.

Prerequisites & Requirements
Before running the scripts, ensure your environment meets the following specifications:

Python Version: 3.10

Core Libraries: * torch==2.1.0

transformers==4.36.0

pandas, numpy, scikit-learn, datasets

Hardware: CUDA-enabled GPU (recommended for training and fast inference).

 Key Methodology Highlights
1. Generator-Based Data Splitting
We avoided the "Validation Trap" (standard random splitting) which often leads to over-optimistic results due to generator leakage. Instead, we held out 13 specific generator families—Llama, DeepSeek, and Yi—exclusively for OOD validation.

2. Adversarial Obfuscation
To force the model to learn logic rather than "handwriting," we implemented an 80% augmentation rate including:

Identifier Obfuscation: Renaming variables to generic tokens (e.g., var_0).

Normalization: Removing single-line comments, docstrings, and extra whitespace.

3. Seen & Unseen Languages
Our model demonstrates strong cross-lingual generalization, training on Python, Java, and C++, while successfully evaluating on unseen languages: Go, PHP, C#, C, and JavaScript.

 Reproduction Guide
To reproduce our Attempt 4 results (the configuration used for the final submission):

Model Base: microsoft/codebert-base

Hyperparameters: * Learning Rate: 1.5e-5

Dropout: 0.3

Weight Decay: 0.02

Effective Batch Size: 48

Early Stopping: Training must be halted strictly at Step 1,000.

Why Step 1,000? Our findings proved that 48,000 highly regularized samples outperform 500,000 unregularized samples in OOD scenarios by preventing representation collapse.

📊Performance & Results
Official Test F1: 0.439 (A 62% improvement over our unregularized baseline).

Leaderboard Rank: 51st.

Qualitative Note: The system excels at structural logic detection but remains challenged by short, boilerplate code snippets.
