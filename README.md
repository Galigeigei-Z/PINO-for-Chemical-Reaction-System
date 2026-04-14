# PINO for Chemical Reaction System

## Overview

This repository presents a lightweight public demo from my PINO work on coupled transport-reaction systems.

The main goal is to build surrogate models for chemical reaction systems that are fast enough for repeated use while still respecting the governing transport and reaction physics.

The framework is developed for two related tasks:

- forward prediction of spatiotemporal concentration fields
- inverse identification of model parameters from observations

## Repository Layout

Public demo files are organized by case:

- `case1/`: case 1 notebook and data
- `case2/`: coming soon
- `case3/`: case 3 inverse demo notebook and prepared files

## Methodology and Visual Overview

### Framework

<img width="1058" height="940" alt="Framework overview" src="https://github.com/user-attachments/assets/fae48990-3212-45d4-96c2-a41d9d64bc2c" />

### Case Study 1: Transient Diffusion-Reaction System

<img width="998" height="284" alt="Transient diffusion-reaction system" src="https://github.com/user-attachments/assets/58ad2a00-22d0-407a-8449-d48fb6b08f4c" />

### Case Study 3: Reactive Channel Flow

<img width="929" height="232" alt="Reactive channel flow inverse PINO" src="https://github.com/user-attachments/assets/3a77e9e3-2e10-4c6e-8d64-b660a656a09a" />

## Cases

### Case 1

`case1/` contains a single integrated notebook and the dataset files used by that notebook.

Main file:

- `case1/case1_demo.ipynb`

### Case 2

`case2/` is reserved for the next public release.

### Case 3

`case3/` contains the inverse demo notebook together with the prepared files it loads.

Main files:

- `case3/case3_demo.ipynb`
- `case3/case3_demo.executed.ipynb`
- `case3/github_demo_outputs/adr_channel_demo.pkl`
- `case3/github_demo_outputs/forward_surrogate_state_dict_demo.pt`

## Environment

The notebooks are intended for a standard Python environment with the following core packages available:

- Python 3.10 or newer
- `numpy`
- `matplotlib`
- `torch`
- `jupyter`

The notebooks can run on CPU. If CUDA-enabled PyTorch is available, they will use GPU automatically.

## Upstream Foundations

This public demo is built on the broader Fourier Neural Operator / Physics-Informed Neural Operator line of work.

Relevant upstream repositories:

- Fourier Neural Operator: <https://github.com/neuraloperator/neuraloperator>
- Physics-Informed Neural Operator: <https://github.com/neuraloperator/physics_informed>

## Citation

If this repository is useful for your work, please consider citing this paper:

```bibtex
Zhang, Z.; Lim, E. W. C. Physics-Informed Neural Operator Framework for Coupled Transport and Reaction Systems.
Industrial & Engineering Chemistry Research, published online April 13, 2026.
https://doi.org/10.1021/acs.iecr.5c04659
```

BibTeX:

```bibtex
@article{zhang2026pino,
  author = {Zhang, Ziyun and Lim, Eldin Wee Chuan},
  title = {Physics-Informed Neural Operator Framework for Coupled Transport and Reaction Systems},
  journal = {Industrial \\& Engineering Chemistry Research},
  year = {2026},
  doi = {10.1021/acs.iecr.5c04659},
  url = {https://doi.org/10.1021/acs.iecr.5c04659}
}
```

## Contact

Feel free to contact me: ziyun_zhang@u.nus.edu
