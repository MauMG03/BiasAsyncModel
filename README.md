# BOTS Experiments Notebook

## Overview

This repository contains a self-contained Jupyter notebook that reproduces the experiments presented in Section 6 of the paper:

> *Consensus under Cognitive Biases in an Asynchronous Multi-Agent Model of Opinion Evolution*

The notebook implements the BOTS model and reproduces the experimental figures and empirical analyses reported in the paper.

The notebook includes:

* The complete simulation library.
* Implementations of the cognitive bias functions.
* Experiment pipelines for all Section 6 experiments.
* An experiment with a run execution with bias function in M
* Figure generation code.
* Result serialization utilities.

No external project files are required.

---

# Notebook Structure

The notebook is organized into the following sections.

## 1. Configuration

Defines the experimental scale through the `SAMPLE_SCALE` parameter.

```python
# SAMPLE_SCALE = 0.1
SAMPLE_SCALE = 1.0
```

### Recommended Settings

| Value | Purpose                            | Runtime          |
| ----- | ---------------------------------- | ---------------- |
| `0.1` | Fast sanity-check execution        | minutes          |
| `1.0` | Full reproduction of paper figures | Potentially long |

---

## 2. Simulation Library

Implements:

* The asynchronous BOTS opinion dynamics model.
* Bias function families.
* Scheduling mechanisms.
* Consensus and convergence utilities.
* Graph generation utilities.

The implementation follows the formal definitions and theoretical framework described in the paper.

---

## 3. Section 6.1 — Receptive-Resistant Region (Figure 4)

This experiment evaluates empirical:

* `$\epsilon$-consensus` rates
* convergence behavior
* stability under receptive-resistant bias functions

The experiments are based on the theoretical guarantees of Theorem 1.

### Main Goals

* Measure finite-horizon convergence.
* Compare different bias configurations.
* Estimate empirical consensus probabilities.

---

## 4. Section 6.2 — Malleability Region Phase Diagram (Figure 5)

This section evaluates the conservativeness of the sufficient consensus condition:

[
\sigma_{ji} I_{ij} < 1
]

Experiments sweep:

* graph sizes
* influence parameters
* sigma scales

using Erdős–Rényi random graphs.

### Outputs

* Consensus probability heatmaps.
* Empirical phase-transition behavior.
* Analysis of effective influence thresholds.

---

## 5. Section 6.2 — 24-Permutation Sweep (Figure 6)

This experiment studies all possible activation schedules for a minimal 3-agent running graph.

### Purpose

Demonstrates that:

* fairness alone does not determine convergence behavior,
* schedule ordering can significantly affect outcomes beyond the sufficient consensus bound.

### Characteristics

* Exhaustive permutation analysis.
* Deterministic setting.
* No confidence intervals required.

---

## 6. Section 6.3 — Backfire Region (Figure 7)

This experiment studies dynamics under backfire bias functions.

The analysis is motivated by Theorem 3, which states that convergent fair runs evolve toward bipartite consensus states.

### Investigated Properties

* Polarization behavior.
* Bipartite convergence.
* Long-term opinion separation.
* Empirical convergence frequency.

## 7. Export Utilities

Optional utilities are provided to export:

* generated figures,
* JSON experiment results,
* compressed ZIP archives.

Generated files include:

```text
bots_results.zip
bots_figures.zip
```

---

# Requirements

## Python Version

Recommended:

```text
Python 3.10+
```

## Required Libraries

All libraries required to execute the notebooks are listed in requirements.txt file.

Install dependencies with:

```bash
pip install -r requirements.txt
```

---

# Running the Notebook

## Option 1 — Jupyter Notebook

```bash
jupyter notebook BOTS_experiments.ipynb
```

## Option 2 — JupyterLab

```bash
jupyter lab BOTS_experiments.ipynb
```

## Option 3 — Google Colab

The notebook can also be executed in Google Colab.

For limited computational resources, use:

```python
SAMPLE_SCALE = 0.1
```

---

# Expected Outputs

After execution, the notebook generates:

## Figures

```text
figure_4_section_6_1.png
figure_5_section_6_2_phase_diagram.png
figure_6_section_6_2_permutations.png
figure_7_section_6_3_backfire.png
```

## Result Files

JSON files containing:

* experiment parameters,
* convergence statistics,
* confidence intervals,
* aggregate metrics.

## ZIP Archives

```text
bots_results.zip
bots_figures.zip
```

---

# Reproducibility Notes

For reproducible executions, the notebook includes optional fixed-hash configuration:

```python
# os.environ['PYTHONHASHSEED'] = '0'
```

Additional reproducibility recommendations:

* Fix NumPy random seeds.
* Use identical package versions.
* Execute notebook cells sequentially.

---

# Computational Considerations

The full experimental setup (`SAMPLE_SCALE = 1.0`) may require substantial execution time depending on:

* CPU performance,
* graph sizes,
* number of runs,
* available memory.

The reduced setting (`0.1`) is recommended for:

* quick validation,
* debugging,
* educational demonstrations.

---

# Citation

If you use this notebook in academic work, please cite the corresponding paper:

```bibtex
@article{bots_opinion_dynamics,
  title={Incorporating Cognitive Biases into an Asynchronous Model of Opinion Evolution},
  author={...},
  journal={...},
  year={...}
}
```

Replace the placeholder bibliographic information with the final publication metadata.

---

# Contact

For questions, issues, or collaborations, please contact the repository authors or open an issue in the repository.
