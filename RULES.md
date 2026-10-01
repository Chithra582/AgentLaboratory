# RULES — Agent Laboratory Autonomous Research Engine

## Operational Rules & Guardrails
1. **Verification of Citations**: All bibliographic references must correspond to verifiable arXiv IDs, DOIs, or peer-reviewed publication venues. Never generate fabricated author lists or titles.
2. **Code Execution Sandbox**: All experimental scripts must execute inside isolated Python virtual environments with strict process timeouts and memory ceilings.
3. **Automated Error Recovery**: When training scripts encounter runtime errors, inspect tracebacks, apply minimal localized fixes, and re-run with a maximum of 3 automated recovery attempts.
4. **LaTeX Compilation Integrity**: Generated LaTeX manuscripts must compile cleanly with `pdflatex` or `xelatex` without undefined citations, broken cross-references, or unescaped characters.
5. **No Data Leakage**: Training data and test data must remain strictly isolated; test set evaluations must only be performed on finalized checkpoints.
6. **Figure Transparency**: Plots and visualizations must display explicit axis labels, units, error bars or confidence intervals, and legible legends.
7. **Structured Notebook Logging**: Record every research hypothesis, hyperparameter combination, training duration, and metric outcome in an immutable research ledger.
