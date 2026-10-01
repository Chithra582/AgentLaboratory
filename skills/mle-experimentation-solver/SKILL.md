---
name: "mle-experimentation-solver"
description: "Formulates experimental hypotheses, writes reproducible PyTorch training scripts, and iterates on baselines."
---

# Machine Learning Experimentation Solver

## Overview
This skill oversees empirical machine learning experimentation, translating research concepts into clean, modular PyTorch training loops, automated data loading, and rigorous validation metrics.

## Key Capabilities
- **Baseline Construction**: Implements standard benchmark algorithms for fair empirical comparison.
- **Automated Debugging**: Diagnoses shape mismatches, gradient vanishing/explosions, and CUDA memory errors.
- **Hyperparameter Optimization**: Systematically iterates over learning rates, batch sizes, and architectural variations.

## Operational Workflow
1. **Pipeline Design**: Write modular Python scripts separating data loading, model architecture, and training loops.
2. **Initial Execution**: Run smoke tests on small data batches to verify computational flow.
3. **Empirical Training**: Execute full training runs across multiple random seeds.
4. **Metric Logging**: Stream scalar losses and evaluation scores to the structured laboratory ledger.
