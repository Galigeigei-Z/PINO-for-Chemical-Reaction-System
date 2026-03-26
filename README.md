# Physics-Informed Neural Operator Framework for Coupled Transport and Reaction Systems

## Overview

This repository presents a lightweight public demo from my PINO work on coupled transport-reaction systems.

The broader goal of this framework is application-oriented: to build a surrogate model that can replace repeated high-cost simulations in reaction engineering while still respecting the governing transport and reaction physics.

The framework is developed for two closely related tasks:

- forward prediction of spatiotemporal concentration fields
- inverse identification of kinetic and transport parameters from limited observations

In this setting, the objective is not only speed, but also physical consistency. By combining operator learning with PDE-based constraints, the framework provides a practical middle ground between purely data-driven surrogates and full CFD-based optimization.

## Availability

This repository currently contains a demo and representative figures.

The full research codebase will be made available when the paper is online.

## What This Demo Does

In this demo I use a reactive channel flow case with advection, diffusion, and reaction to show the full forward-inverse workflow:

1. Solve a forward ADR problem for `A + B -> C`
2. Generate a synthetic reference field
3. Train the forward surrogate using data loss only
4. Start the backward stage and identify the kinetic parameter `k` from a single-species reference field `c_A`
5. Export publication-style figures

For the GitHub version, I cleaned up the original notebook so that it is easier to run and easier to read:

- no cluster-specific `sys.path` edits
- no absolute local font paths
- all outputs are written to `github_demo_outputs/`
- result filenames are consistent across cells
- notebook outputs were stripped before release

## Methodology and Visual Overview

### Framework

<img width="1058" height="940" alt="Framework overview" src="https://github.com/user-attachments/assets/fae48990-3212-45d4-96c2-a41d9d64bc2c" />

### Case Study 1: Transient Diffusion-Reaction System

<img width="998" height="284" alt="Transient diffusion-reaction system" src="https://github.com/user-attachments/assets/58ad2a00-22d0-407a-8449-d48fb6b08f4c" />

### Case Study 3: Reactive Channel Flow

<img width="929" height="232" alt="Reactive channel flow inverse PINO" src="https://github.com/user-attachments/assets/3a77e9e3-2e10-4c6e-8d64-b660a656a09a" />

## Environment Setup

### Option 1: pip

Create a clean Python environment and install the minimal dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

### Option 2: conda

```bash
conda create -n case3-pino-demo python=3.10 -y
conda activate case3-pino-demo
pip install -r requirements.txt
```

### Cluster GPU environment used here

If you are running on your cluster with the existing shared environment, the helper scripts in this folder use:

```bash
conda activate /scratch/e1518147/vanda_pypkg/envs/py310
```

### Expected Core Packages

- Python 3.10 or newer
- `numpy`
- `matplotlib`
- `torch`
- `jupyter`
- `nbconvert`

### GPU Note

The notebook can run on CPU. If CUDA-enabled PyTorch is available, it will automatically use GPU:

```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
```

## Repository Contents

- `model3-paper-demo-github.ipynb`: GitHub-ready notebook
- `generate_case3_github_demo.py`: script used to generate the cleaned notebook
- `requirements.txt`: minimal Python dependencies for this demo
- `model3-paper-demo-github.executed.ipynb`: optional executed notebook artifact
- `github_demo_outputs/`: generated output figures and pickle files after execution
- `run_notebook_gpu.sh`: run the notebook on a GPU node using the shared `py310` environment
- `submit_gpu_job.pbs`: submit the notebook as a PBS GPU job

## How to Run

### Run interactively

Open the notebook and execute cells from top to bottom:

```bash
jupyter notebook model3-paper-demo-github.ipynb
```

or

```bash
jupyter lab model3-paper-demo-github.ipynb
```

### Run from command line

```bash
python3 -m nbconvert --to notebook --execute model3-paper-demo-github.ipynb --output model3-paper-demo-github.executed.ipynb --ExecutePreprocessor.timeout=0
```

### Run on the cluster GPU node with the shared `py310` environment

After entering a GPU node, run:

```bash
bash ./run_notebook_gpu.sh
```

Or submit directly with PBS:

```bash
qsub ./submit_gpu_job.pbs
```

All generated files will be written to:

- `github_demo_outputs/`

## Expected Outputs

After a successful run, you should expect files such as:

- `github_demo_outputs/adr_channel_demo.pkl`
- `github_demo_outputs/adr_channel_demo.svg`
- `github_demo_outputs/adr_pino_result_k_only_demo.pkl`
- `github_demo_outputs/field_comparison_demo.svg`
- `github_demo_outputs/triple_panel_identification_demo.svg`

## Upstream Foundations

This is not a from-scratch implementation. It is my cleaned and adapted demo built on the broader Fourier Neural Operator / Physics-Informed Neural Operator line of work.

Relevant upstream repositories:

- Fourier Neural Operator: <https://github.com/neuraloperator/neuraloperator>
- Physics-Informed Neural Operator: <https://github.com/neuraloperator/physics_informed>

If you use or redistribute this demo, please cite the relevant FNO/PINO papers and repositories, and make clear that this repository is an adapted downstream demo built on that foundation.

## Research Context

This demo sits inside a broader PINO framework that I use for coupled transport-reaction systems. In the larger study, the framework is used for:

- forward prediction of spatiotemporal fields
- inverse identification of kinetic and transport parameters
- reactor modeling
- catalyst characterization
- process optimization in chemical reaction engineering

Some representative results from the broader workflow are:

- `R² ≈ 0.997` for a transient diffusion-reaction forward case
- mean parameter deviation around `0.018` for a porous catalyst inverse case
- `94–99%` reduction in computational time versus CFD-based adjoint-gradient optimization for the reactive channel inverse case

## Scope Note

This folder is meant to be a lightweight, reproducible public demo. It is not a full archival release of every private experiment in the original working directory.
