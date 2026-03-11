# Dataset Information

## Dataset Used
**UCI Mushroom Dataset** (via scikit-learn / UCI ML Repository)

## Source
- Original source: UCI Machine Learning Repository
- Loaded via: `sklearn.datasets.fetch_openml(name='mushroom', version=1)`
- Fallback: direct CSV from UCI ML Repository

## Description
The Mushroom dataset contains 8124 instances of hypothetical samples corresponding to 23 species of gilled mushrooms. Each sample is classified as edible or poisonous. It has 22 categorical features which are label-encoded to numeric values for use with logistic regression.

## Why This Dataset
- **Binary classification** task — matches the problem type in the paper (IEThresh operates on binary classification with noisy labels)
- **Used in the original paper** — the authors explicitly use the UCI Mushroom dataset in their experiments (Table 1, Section 4.1)
- **Large enough** (8124 samples) to simulate a realistic active learning scenario with an unlabeled pool
- **CPU-friendly** — no GPU required, runs in seconds

## How It Is Used
1. Features are label-encoded from categorical to numeric
2. Data is split 70%/30% into train/test (matching the paper's protocol, Section 4.1)
3. From the training split, 1 positive and 1 negative example form the initial labeled set
4. The rest of the training split serves as the unlabeled pool for active learning
5. Multiple noisy oracles are simulated by flipping true labels with oracle-specific error rates

## Limitations Compared to Original Paper
- The original paper tests on 6 UCI datasets plus 2 Amazon Mechanical Turk datasets; we use only Mushroom
- We simulate noisy oracles rather than using real human annotators
- Our implementation uses a simplified feature encoding rather than the original preprocessing
