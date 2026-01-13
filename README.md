# Physics-Informed Neural Operator Framework for Coupled Transport and Reaction Systems
Overview

This project develops a unified Physics-Informed Neural Operator (PINO) framework for modeling coupled transport–reaction systems, integrating the spectral learning efficiency of neural operators with explicit physical constraints derived from governing PDEs.

The framework is designed to serve as a computationally efficient surrogate for both:

forward prediction of spatiotemporal fields, and

inverse identification of kinetic and transport parameters,

while maintaining PDE-level predictive fidelity and CFD-comparable inference accuracy at a fraction of the computational cost.



Methodology

The proposed framework unifies forward and inverse PINO formulations within a consistent operator-learning architecture, enabling stable learning across diffusion-dominated, reaction-limited, and convective–reactive regimes.

Key features include:

Spectral neural operators for efficient global representation

Physics-based regularization enforcing conservation laws

End-to-end differentiable inverse learning for parameter estimation

Case Studies and Key Results
1. Transient Diffusion–Reaction System (Forward PINO)

A forward PINO model was trained on sampled concentration data to predict the spatiotemporal evolution of concentration fields over a wide range of Thiele moduli.

<img width="998" height="284" alt="image" src="https://github.com/user-attachments/assets/58ad2a00-22d0-407a-8449-d48fb6b08f4c" />

Key results:



Average prediction deviation below 0.005

Testing coefficient of determination R² ≈ 0.997

Performance competitive with analytical benchmarks (HPM)

Improved stability and accuracy compared to conventional FNO and PINN surrogates under nonlinear kinetics

2. Porous Catalyst System (Inverse PINO)

An inverse PINO formulation was applied to a cylindrical porous catalyst, identifying intrinsic Thiele modulus and effective diffusivity using only a single steady-state radial concentration profile.

Key results:

Mean parameter deviation of 0.018 from reference values

Predicted effectiveness factor within ~0.04 of experimental observations

Demonstrated potential for accelerating catalyst design and kinetic parameterization

3. Reactive Channel Flow (Inverse PINO with Convection)

The framework was extended to a convective–diffusive–reactive channel flow, representing a CFD-level transport–reaction environment.

<img width="929" height="232" alt="image" src="https://github.com/user-attachments/assets/3a77e9e3-2e10-4c6e-8d64-b660a656a09a" />


Key results:

Reduced kinetic parameter error from >90% to <1% using single-species measurements

Achieved 94–99% reduction in computational time compared to CFD-based adjoint-gradient optimization

Maintained consistent physical fidelity across inverse iterations



Significance

Collectively, these results demonstrate that the proposed forward–backward PINO framework acts as a physically consistent and computationally efficient surrogate for coupled transport–reaction systems.

By bridging data-driven learning and first-principles modeling, the framework offers a scalable and generalizable tool for:

Reactor modeling

Catalyst characterization

Inverse kinetic identification

Process optimization in chemical reaction engineering

