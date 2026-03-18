# Classical Mechanics: Numerical Modeling & AI Evaluation
**MA PH 343 – Classical Mechanics II | University of Alberta**  
**Author:** Rudmila Samuad Eka  
**Date:** December 2025

---

## Overview

This repository contains a classical mechanics project from MA PH 343 at the University of Alberta, combining first-principles analytical derivation with Python-based numerical simulation and critical evaluation of generative AI outputs.

---

## Project: Hamster + Armadillo-in-a-Ball in a Rolling Wheel

### Problem
A vertical wheel rolls without slipping on a horizontal table. Inside the wheel:
- A **hamster** of mass $m_H$ runs at constant speed $V$ on a circular track of radius $R - h$
- An **armadillo** rolled in a ball of mass $m_A$ rolls freely without slipping inside the wheel on the same radius

Find the configuration manifold, derive the Euler-Lagrange equations, analyze energy conservation, and find equilibria. Use generative AI (ChatGPT) to assist — then document how much directing was required.

---

## Research Questions
> 1. What are the equations of motion for this coupled nonlinear system?
> 2. Is energy conserved? Is it equal to kinetic + potential energy?
> 3. Are there equilibria, and are they stable or unstable?
> 4. How capable is generative AI at solving advanced classical mechanics problems?

---

## Methods

| Step | Approach | Tool |
|------|----------|------|
| Coordinate setup | Generalized coordinates (φ, θ) on $S^1 \times S^1$ | Analytical |
| No-slip constraint | $h\dot{\psi} + (R-h)\dot{\theta} = R\dot{\varphi}$ | Analytical |
| Time-independent Lagrangian | Substitution $q = \varphi + \Omega_H t$ | Analytical |
| Equations of motion | Euler-Lagrange via automatic differentiation | `SymPy` |
| Numerical integration | `solve_ivp` with rtol=1e-8, atol=1e-9 | `SciPy` |
| Energy conservation | Verified numerically across t ∈ [0, 20] s | `NumPy` |

---

## Key Results

| Quantity | Result |
|----------|--------|
| Configuration space | $\mathcal{Q} = S^1 \times S^1$ |
| Equilibrium | Both hamster and armadillo at bottom of wheel |
| $q(t)$ behaviour | Slow, large-amplitude oscillations |
| $\theta(t)$ behaviour | Fast, small-amplitude oscillations |
| Energy conservation | Confirmed — max deviation < 10⁻⁶ J |

Both angles oscillate about zero, consistent with the equilibrium at the bottom. The difference in oscillation frequencies reflects the different effective inertias of the two subsystems.

---

## AI Evaluation Summary

ChatGPT required significant directing across three areas:

**1. Coordinates & Constraints**
Initially used wrong coordinate conventions and omitted the ball's rotational kinetic energy. Required explicit correction of the no-slip constraint.

**2. Time Dependence**
Retained explicit time dependence from the hamster motion until directed to introduce $q = \varphi + \Omega_H t$ to produce a time-independent Lagrangian.

**3. Symbolic Computation**
Hand-expanded equations of motion were long and error-prone. Redirected to encode the Lagrangian in SymPy and derive EOM by automatic differentiation.

**Conclusion:** AI functioned as a useful computational assistant only after the physical model, constraints, and coordinate choices were carefully specified and verified against the textbook solution. Physical reasoning required human direction throughout.

---

## Repository Structure

```
classical-mechanics-modeling/
│
├── notebooks/
│   └── classical_mechanics_chatgpt.ipynb   # Full analysis notebook
├── report/
│   └── hamster_armadillo_report.pdf        # Final submitted report (Dec 2025)
└── README.md
```

---

## How to Run

```bash
# Clone the repo
git clone https://github.com/RudmilaS/classical-mechanics-modeling.git

# Install dependencies
pip install numpy matplotlib scipy sympy jupyter

# Launch notebook
jupyter notebook notebooks/classical_mechanics_chatgpt.ipynb
```

> ⚠️ The SymPy symbolic computation step may take 1–2 minutes — this is expected behaviour.

---

## Tools Used

| Tool | Purpose |
|------|---------|
| `SymPy` | Symbolic Lagrangian construction, automatic EOM derivation |
| `SciPy` | Numerical ODE integration (`solve_ivp`) |
| `NumPy` | Array operations, energy verification |
| `Matplotlib` | Solution and energy conservation visualization |
| `Jupyter Notebook` | Interactive analysis and documentation |

---

## References

1. Classical Mechanics course textbook, Chapter 3 — Hamster/Armadillo problem
2. MA PH 343 Project 2 specification, University of Alberta, Fall 2025

---

*University of Alberta · Mathematical Physics · Science Co-op Program*
