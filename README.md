# Semeval-Task-13-Subtask-A
official implementation for Subtask A. Our system focuses on Out-of-Distribution (OOD) Robustness by prioritizing structural code logic over surface-level stylistic signatures.

Key Highlights
Generator-Based Data Splitting: We avoided the "Validation Trap" (random splitting) by holding out 13 specific generator families (Llama, DeepSeek, Yi) for pure OOD testing.

Adversarial Obfuscation: Implemented an 80% augmentation rate using Identifier Obfuscation to rename variables and Normalization to remove comments/whitespace.

Seen & Unseen Languages: Demonstrated generalization from training languages (Python, Java, C++) to unseen test languages (Go, PHP, C#, C, and JavaScript).

Performance
Official Test F1: 0.439 (62% improvement over our baseline).

Leaderboard Rank: 51st.

Finding: Proved that 48,000 highly regularized samples outperform 500,000 unregularized samples in OOD scenarios.

Reproduction Guide
To reproduce our Attempt 4 results:

Model: microsoft/codebert-base

Hyperparameters: LR 1.5e-5, Dropout 0.3, Weight Decay 0.02.

Early Stopping: Halt training strictly at Step 1,000 (Effective batch size 48).

Requirements: Python 3.10, PyTorch 2.1.0, Transformers 4.36.0.
