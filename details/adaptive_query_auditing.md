# Adaptive Query Auditing & Perturbation Layers

## Overview
This defense mechanism monitors incoming query traffic to identify and block model extraction attempts. Systems like PRADA track the distribution and relationship of incoming queries over time. If a user or IP range is flagged for sending highly un-correlated, programmatic, or synthetic queries (indicative of distillation attacks), the defense layer dynamically injects noise or slightly perturbs the output logits to destroy the gradient information required by the attacker.

## Attack Architecture & Flow
```mermaid
flowchart TD
    Query["Incoming API Queries"] --> Monitor["Query Auditor (e.g. PRADA)"]
    Monitor -->|Normal distribution| Normal["Normal response"]
    Monitor -->|Suspicious distribution| Perturb["Dynamic Noise/Perturbation Layer"]
    Perturb -->|Corrupted Logits| Response["API Response with destroyed gradients"]
```

---
[← Back to README](../README.md)
