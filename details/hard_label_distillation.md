# Hard-Label Distillation Attacks

## Overview
When production APIs are secured to return only the final top-1 class prediction or token string (completely hiding numerical logits), attackers must use decision-boundary probing. Using iterative, gradient-free optimization or boundary exploration algorithms (e.g., HopSkipJump), the attacker searches for the geometric transition boundaries in the input space where the class label flips. This boundary information is then used to construct training data to clone the decision frontier.

## Attack Architecture & Flow
```mermaid
flowchart TD
    Start["Initialize Input Sample"] --> Probe["Perturb Input slightly"]
    Probe -->|Query Label| API["Hard-Label API"]
    API -->|Top-1 Class Output| BoundaryCheck["Check if Class flipped"]
    BoundaryCheck -->|Yes| Map["Map Decision Boundary Point"]
    BoundaryCheck -->|No| Probe
    Map -->|Aggregate Boundary Points| Train["Train Student Classifier"]
```

---
[← Back to README](../README.md)
