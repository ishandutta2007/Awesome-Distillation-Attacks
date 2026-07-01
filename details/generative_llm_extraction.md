# The Generative & LLM Extraction Era

## Overview
In the modern era of foundation models, extraction attacks leverage LLMs to distill capability, formatting, and alignment parameters. Attackers prompt a teacher model (e.g. GPT-4o) using self-instruct templates or generative prompting pipelines, causing it to synthesize high-quality training pairs (e.g. complex instruction-response pairs or code traces). Some advanced attacks also target token-level probability vectors (logits) to invert layers or clone alignment profiles onto a smaller, open-weights student model (e.g. LLaMA-8B) at negligible cost compared to original training.

## Attack Architecture & Flow
```mermaid
flowchart TD
    Prompt["Self-Instruct Prompt Loops"] -->|Query API| Teacher["Commercial LLM API (Teacher)"]
    Teacher -->|Synthetic Instruction Pairs & Reasoning| SyntheticData["Prone Synthetic Dataset"]
    SyntheticData -->|Supervised Fine-Tuning (SFT)| Student["Open-Weights Student (e.g. 8B)"]
```

---
[← Back to README](../README.md)
