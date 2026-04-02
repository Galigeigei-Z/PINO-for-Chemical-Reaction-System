# Physics-Informed Neural Operator Framework for Coupled Transport and Reaction Systems

## Overview

This repository presents a lightweight public demo from my PINO work on coupled transport-reaction systems.

The broader goal of this framework is application-oriented: to build a surrogate model that can replace repeated high-cost simulations in reaction engineering while still respecting the governing transport and reaction physics.

The framework is developed for two closely related tasks:

- forward prediction of spatiotemporal concentration fields
- inverse identification of kinetic and transport parameters from limited observations

In this setting, the objective is not only speed, but also physical consistency. By combining operator learning with PDE-based constraints, the framework provides a practical middle ground between purely data-driven surrogates and full CFD-based optimization.



## What This Demo Does

In this demo I use a reactive channel flow case with advection, diffusion, and reaction to show the full forward-inverse workflow:

1. Solve a forward ADR problem for `A + B -> C`
2. Generate a synthetic reference field
3. Train the forward surrogate using data loss only
4. Start the backward stage and identify the kinetic parameter `k` from a single-species reference field `c_A`
5. Export publication-style figures


## Methodology and Visual Overview

### Framework

<img width="1058" height="940" alt="Framework overview" src="https://github.com/user-attachments/assets/fae48990-3212-45d4-96c2-a41d9d64bc2c" />

### Case Study 1: Transient Diffusion-Reaction System

<img width="998" height="284" alt="Transient diffusion-reaction system" src="https://github.com/user-attachments/assets/58ad2a00-22d0-407a-8449-d48fb6b08f4c" />

### Case Study 3: Reactive Channel Flow

<img width="929" height="232" alt="Reactive channel flow inverse PINO" src="https://github.com/user-attachments/assets/3a77e9e3-2e10-4c6e-8d64-b660a656a09a" />

## Environment Setup

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

The notebook can also run on CPU. If CUDA-enabled PyTorch is available, it will automatically use GPU (NVDIA A40 with 48 GB RAM used in our work):

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


## Upstream Foundations

This is not a from-scratch implementation. It is my cleaned and adapted demo built on the broader Fourier Neural Operator / Physics-Informed Neural Operator line of work.

Relevant upstream repositories:

- Fourier Neural Operator: <https://github.com/neuraloperator/neuraloperator>
- Physics-Informed Neural Operator: <https://github.com/neuraloperator/physics_informed>

If you use or redistribute this demo, please cite the relevant FNO/PINO papers and repositories, and make clear that this repository is an adapted downstream demo built on that foundation.

## Contact

Questions, feedback, or collaboration ideas are welcome.
Please contact: ziyun_zhang@u.nus.edu
