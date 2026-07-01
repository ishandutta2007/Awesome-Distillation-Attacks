# Data-Free Adversarial Distillation

## Overview
In scenarios where the adversary has absolutely no natural dataset to query the victim API, they employ Data-Free Adversarial Distillation. This method uses a generative adversarial training scheme. A generator network is trained to synthesize synthetic data samples that maximize the discrepancy (or entropy) of the victim model's outputs. Concurrently, a student model is trained on these synthetic samples to minimize the discrepancy, distilling the model's knowledge in a completely data-free, zero-shot fashion.

## Attack Architecture & Flow
```mermaid
flowchart TD
    Gen["Generative Network (GAN Generator)"] -->|Synthesizes Noise/Sample| Victim["Victim API"]
    Gen -->|Synthesizes Noise/Sample| Student["Student Model"]
    Victim -->|Logits v| Discrepancy["Discrepancy / Entropy Loss"]
    Student -->|Logits s| Discrepancy
    Discrepancy -->|Maximize (Update)| Gen
    Discrepancy -->|Minimize (Update)| Student
```

---
[← Back to README](../README.md)
