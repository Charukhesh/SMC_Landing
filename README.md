# Thrust-Limited Sliding-Mode–Based Instantaneously Optimal Guidance  
## Fuel-Aware Precision Soft Landing on Asteroids

## Overview

This repository presents a **MATLAB implementation and research extension** of the guidance framework introduced in:

> **Sliding-Mode-Control–Based Instantaneously Optimal Guidance for Precision Soft Landing on Asteroid**

While the original paper formulates an **unconstrained instantaneously optimal sliding-mode guidance law**, this project extends the framework by **explicitly incorporating thrust magnitude limits as nonlinear constraints**.  
This modification transforms the guidance problem from a convex instantaneous optimization into a **non-convex, fuel-aware constrained control problem**, bringing the formulation closer to **realistic spacecraft propulsion limits**.

The repository therefore focuses on:
- Enforcing **physical thrust bounds**
- Studying their effect on optimality and convergence
- Designing **fuel-efficient guidance laws** under actuator constraints

## Motivation for the Extension

The original formulation assumes that the optimal control computed instantaneously is **fully realizable by the actuator**.  
In practical asteroid landing missions, this assumption is rarely valid:

- Thrusters have **strict magnitude limits**
- Saturation can destabilize classical sliding-mode designs
- Fuel consumption must be minimized to maximize mission viability

Introducing thrust limits fundamentally changes the nature of the problem:
- The instantaneous optimization becomes **non-convex**
- Classical analytical optimal solutions are no longer guaranteed
- Trade-offs emerge between convergence speed, robustness, and fuel usage

This repository explores these trade-offs explicitly.

## Core Concept (Extended Framework)

The extended guidance strategy operates as follows:

1. **Sliding Variable Definition**  
   A sliding variable is constructed from position and velocity errors to encode terminal landing objectives.

2. **Instantaneously Optimal Control Formulation**  
   At each time step, a local cost (related to control effort / fuel usage) is minimized **instantaneously**, rather than over a full horizon.

3. **Nonlinear Thrust Constraints**  
   The control input is constrained by:
   - Upper and lower thrust bounds
   - Directional feasibility due to heading dynamics  

   These constraints introduce **non-convexity** into the instantaneous optimization problem.

4. **Constraint-Aware Sliding Enforcement**  
   The control law is designed to:
   - Respect thrust limits
   - Preserve sliding-mode convergence
   - Avoid excessive fuel consumption or aggressive switching

The result is a **physically realizable, fuel-aware guidance law** that retains the robustness properties of sliding-mode control.

## Key Contributions of This Repository

Compared to the original paper, this implementation:

- Introduces **explicit thrust magnitude constraints**
- Handles the resulting **non-convex instantaneous optimization**
- Demonstrates the impact of actuator limits on:
  - Landing accuracy
  - Convergence rate
  - Fuel efficiency
- Provides a **modular simulation framework** for further extensions

This makes the work suitable not only for theoretical analysis, but also for **mission-relevant design studies**.

## Repository Structure

```text
.
├── main.m                    # Simulation entry point with thrust-limited guidance
├── Optimizer.m               # Non-convex instantaneous optimization with thrust bounds
├── SlidingVariable.m         # Sliding surface definition
├── HeadingErrorDynamics.m    # Thrust direction and heading error dynamics
├── VelocityProfile.m         # Fuel-aware reference velocity shaping
├── GetGravity.m              # Low-gravity asteroid environment model
├── utilities.m               # Shared helper and math utilities
├── plots.m                   # Trajectory, control, and fuel-efficiency visualization
└── README.md
