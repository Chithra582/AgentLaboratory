# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **Agent Laboratory Autonomous Research Engine** (`agent-laboratory`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** Agent Laboratory Autonomous Research Engine (`agent-laboratory`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Data & Analytics / Autonomous Scientific Research & Discovery  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), OWASP LLM Top 10, MITRE ATLAS  

---

## How the Agent Decides

The Agent Laboratory Autonomous Research Engine is an end-to-end autonomous research workflow powered by LLM agents. It conducts systematic scientific research across three unified phases: (1) Literature Review, (2) Empirical Experimentation, and (3) Publication-Ready Report Writing. It integrates tools like arXiv, Hugging Face, Python/PyTorch, and LaTeX. Its operational purpose is to serve as an autonomous research co-pilot that accelerates scientific discovery by automating repetitive coding, experimentation, literature compilation, and document formatting while keeping the human researcher in control of ideation and critical direction.

### 1. Decision Architecture

The research topic intake, literature review, empirical experimentation, and LaTeX paper compilation pipeline operates across a deterministic, five-stage architecture:

```
Research Idea / Topic Directive (Scientific Hypothesis / Benchmark Target / Dataset Reference)
    │
    ▼
[Stage 1: Research Ideation & Literature Synthesis]
    │  - Queries arXiv, Semantic Scholar, and Hugging Face for state-of-the-art baselines
    │  - Analyzes related work, identifying empirical gaps and baseline benchmarks
    │  - Formulates formalized research hypotheses and experimental plans
    ▼
[Stage 2: Experimental Code Generation & Setup]
    │  - Synthesizes PyTorch / scikit-learn machine learning experimentation code
    │  - Generates data loaders, model architectures, and training hyperparameters
    │  - Validates script syntax, GPU hardware requirements, and dependency manifests
    ▼
[Stage 3: Subprocess Experiment Execution & Metric Logging]
    │  - Executes training and evaluation runs in isolated local subprocess sandboxes
    │  - Captures numerical metrics (loss, accuracy, F1, latency) with floating-point rigor
    │  - Iterates through corrective self-debugging loops if execution fails (up to 3 cycles)
    ▼
[Stage 4: Scientific Figure & Table Synthesis]
    │  - Renders publication-quality vector plots (matplotlib, seaborn) from empirical logs
    │  - Compiles comparative ablation tables with statistical significance markers
    │  - Formats figure captions and LaTeX tabular structures adhering to conference styles
    ▼
[Stage 5: Publication-Ready LaTeX Compilation & Archival]
    │  - Typesets complete academic papers (ICLR, NeurIPS, ACL templates) via pdflatex
    │  - Resolves BibTeX citations and verifies mathematical formula rendering
    │  - Commits verified code, data logs, and compiled PDF papers to local workspace
    ▼
Validated Research Deliverable & Auditable Scientific Experiment Trajectory Record
```

### 2. Decision Logic & Scientific Evaluation Formulations

Agent Laboratory evaluates literature relevance, experimental confidence, and paper completeness using deterministic mathematical models:

1. **Literature Citation Relevance Score ($S_{\text{citation}}$)**:
   $$S_{\text{citation}}(p) = (w_s \cdot S_{\text{semantic}}) + (w_c \cdot C_{\text{citations}}) + (w_y \cdot Y_{\text{recency}})$$
   where:
   - $S_{\text{semantic}} \in [0, 1]$ represents embedding similarity to the research hypothesis.
   - $C_{\text{citations}} \in [0, 1]$ represents normalized citation impact.
   - $Y_{\text{recency}} \in [0, 1]$ prioritizes recent breakthrough papers (<3 years).
   - Weights: $w_s = 0.50, w_c = 0.25, w_y = 0.25$ ($\sum w_i = 1.0$).

2. **Empirical Verification Index ($I_{\text{empirical}}$)**:
   $$I_{\text{empirical}} = \frac{1}{3} \left( M_{\text{baseline}} + S_{\text{significance}} + R_{\text{reproducibility}} \right)$$
   where each metric is evaluated $\in [0, 1]$, certifying that the proposed method outperforms competitive baselines with verified reproducibility.

### 3. Thresholding & Refusal Decision Criteria

Agent Laboratory Autonomous Research Engine enforces strict scientific integrity and ethical boundaries:
- **Refusal to Fabricate Empirical Findings**: The engine strictly prohibits inventing imaginary experimental results or fabricating data tables; results must derive from actual executed runs (`ERR_DATA_FABRICATION_PROHIBITED`).
- **Refusal to Plagiarize Published Literature**: Direct unquoted text copying from external arXiv papers is detected and blocked (`ERR_PLAGIARISM_PREVENTED`).
- **Turn Ceiling Enforcement**: Research and experimentation loops enforce a ceiling of `max_turns: 25` to prevent infinite exploratory training runs (`WARN_TURN_BUDGET_REACHED`).
- **Local Directory Boundary Enforcement**: Code and paper generation writes strictly to the local workspace; external directory writes are blocked (`ERR_OUT_OF_BOUNDS_WRITE`).

### 4. Fallback Decision Mechanism

Continuous scientific productivity is maintained through multi-tier fault recovery:
- **Model Cascade Failover**: When the primary foundation model experiences latency spikes or HTTP 429 rate limits, the orchestrator cascades automatically between `claude-3-5-sonnet`, `gpt-4o`, and `gemini-2.0-flash`.
- **Hardware-Aware CPU Fallback**: If GPU training memory is exhausted (CUDA OOM), the agent automatically downsizes batch sizes or switches to lightweight CPU models.
- **Graceful LaTeX Compilation Repair**: If `pdflatex` compilation fails on non-standard packages, the engine identifies missing tags and recompiles with standard packages.

### 5. Human-in-the-Loop Governance

Human researchers retain complete intellectual leadership and supervisory control:
- **Mandatory Human Direction Gates**: The core research hypothesis, experimental scope, and final manuscript require human scientist sign-off before paper submission.
- **Emergency Experiment Kill Switch**: Operators can halt long-running training loops instantly via standard `Ctrl+C` interrupt signals.
- **Inspectable Scientific Artifacts**: All raw training logs, model checkpoints, generated plots, and LaTeX source files remain completely accessible and editable by the researcher.

---

## The Data It Uses

Agent Laboratory operates under strict privacy, data minimization, and local workspace isolation standards.

### 1. Ingested Input Data

The agent processes only operational assets necessary to fulfill autonomous research:
- **Research Topic Briefs**: Natural language problem descriptions, benchmark goals, and hypothesis statements.
- **Public Academic Papers**: arXiv abstracts, PDF papers, and BibTeX citations retrieved via public academic APIs.
- **Experimental Datasets**: Tabular datasets, benchmark tensors, and evaluation split files scoped to the workspace.

### 2. Configuration & Reference Data

- **Conference LaTeX Templates**: Official style files and document classes for NeurIPS, ICML, ICLR, and ACL.
- **Academic API Schemas**: Query parameters and endpoint manifests for arXiv, Semantic Scholar, and Hugging Face Hub.
- **Plotting Style Guidelines**: Color palettes, font sizes, and DPI configurations for publication-quality figures.

### 3. Base Model & Inference Lineage

- **Deterministic Scientific Libraries**: PyTorch, NumPy, scikit-learn, matplotlib, and pdflatex executed natively (100% deterministic with zero LLM variance).
- **Foundation LLMs**: High-capability frontier models (`claude-3-5-sonnet`, `gpt-4o`, `gemini-2.0-flash`) utilized for literature synthesis, code authoring, and academic paper composition.
- **Zero Training on Proprietary Research**: Unpublished experimental results, proprietary algorithms, and draft manuscripts are never transmitted to external cloud servers or used for model training.

### 4. Data Privacy, Storage, and Retention

- **OWASP LLM & MITRE ATLAS Hardened**: Defended against prompt injection, ungrounded hallucination, and unauthorized agency.
- **Local-Only Manuscript Storage**: All generated models, raw training logs, and compiled PDF manuscripts reside exclusively on the user's filesystem.
- **Credential Scrubbing**: API keys, database connection strings, and local user paths are scrubbed from generation logs.
- **Zero Commercial Monetization**: Research manuscripts, proprietary candidate algorithms, and computational logs are never monetized, aggregated, or shared with third parties.

---

## Limitations

Understanding the operational boundaries and technical constraints of Agent Laboratory is essential for research deployment.

### 1. Extremely Long-Running Multi-Day Model Training
- **Limitation**: Training frontier foundation models requiring hundreds of GPU-hours exceeds single-agent session boundaries.
- **Mitigation**: The engine focuses on rapid scientific experimentation, prototype benchmarking, and comparative ablations on manageable models.

### 2. Physical Wet-Lab Biological/Chemical Validation
- **Limitation**: Autonomous research is conducted in silico; physical laboratory experiments cannot be physically performed by software agents.
- **Mitigation**: Generated papers explicitly delineate computational predictions from required future physical laboratory experiments.

### 3. Novel Mathematical Theorem Proving
- **Limitation**: While proficient at mathematical formulation and empirical validation, proving complex novel formal mathematical theorems is challenging for current LLMs.
- **Mitigation**: The agent focuses on empirical and algorithmic research, utilizing standard symbolic packages (SymPy) for algebraic verification.

### 4. LaTeX Package Incompatibility Warnings
- **Limitation**: Combining multiple specialized LaTeX packages can trigger minor typesetting warnings or font conflicts.
- **Mitigation**: The engine adheres to standard, verified conference template packages and strips non-essential package declarations.

### 5. Subjective Peer-Review Aesthetic Judgments
- **Limitation**: Reviewers at academic conferences evaluate papers with subjective aesthetic and institutional preferences.
- **Mitigation**: The agent formats papers adhering strictly to official reviewer rubrics, emphasizing clear empirical ablation graphs and bold contributions.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Decision logic & scientific evaluation formulations | Section 2 | Verified |
| - Thresholding & refusal decision criteria | Section 3 | Verified |
| - Fallback decision mechanism | Section 4 | Verified |
| - Human-in-the-loop governance & oversight | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested topic briefs, academic papers & datasets | Section 1 | Verified |
| - Configuration, conference LaTeX templates & schemas | Section 2 | Verified |
| - Base model lineage & deterministic scientific engines | Section 3 | Verified |
| - Data privacy, retention lifecycle & MITRE/OWASP | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Extremely long-running multi-day model training | Section 1 | Verified |
| - Physical wet-lab biological/chemical validation | Section 2 | Verified |
| - Novel mathematical theorem proving | Section 3 | Verified |
| - LaTeX package incompatibility warnings | Section 4 | Verified |
| - Subjective peer-review aesthetic judgments | Section 5 | Verified |
