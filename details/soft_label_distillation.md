# Soft-Label Distillation Attacks

## Overview
Soft-Label Distillation Attacks rely on obtaining the full, un-truncated probability distribution (logits) for each class from the target API. Because these soft values represent how the model distributes its confidence across all classes, they contain crucial information about the model's internal representations (often called 'dark knowledge'). The attacker optimizes a distillation loss function (such as Kullback-Leibler divergence) to match the student's output probabilities to the teacher's soft labels.

## Attack Architecture & Flow
```mermaid
flowchart LR
    Query["Input Query"] --> Victim["Victim API"]
    Victim -->|Full Soft Logits p(y|x)| KL["KL Divergence Loss"]
    Student["Student Model"] -->|Student Probabilities q(y|x)| KL
    KL -->|Backpropagation| Update["Update Student Weights"]
```

---
[← Back to README](../README.md)
