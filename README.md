# Sliding-Mode–Based Instantaneously Optimal Guidance for Precision Soft Landing on Asteroids

## Overview

This repository contains a **MATLAB implementation and extension** of the guidance framework proposed in the paper:

> **Sliding-Mode-Control–Based Instantaneously Optimal Guidance for Precision Soft Landing on Asteroid**

The original work introduces a guidance law that combines **sliding-mode control (SMC)** with **instantaneous optimality**, enabling precise and robust soft landing on small celestial bodies under severe uncertainty and low-gravity conditions.

This repository translates the theoretical formulation into a **modular, simulation-ready codebase**, designed for:
- Reproducibility
- Readability
- Extension to new asteroid models, vehicle dynamics, or guidance objectives

---

## Motivation

Asteroid landing presents several challenges:
- Extremely low and uncertain gravity
- Limited sensing and computational resources
- Strict terminal constraints (zero velocity at touchdown)
- Sensitivity to modeling errors

Classical optimal control methods often require solving computationally expensive optimization problems over a full time horizon.  
This framework avoids that by enforcing optimality **locally in time**, while guaranteeing **global convergence** using sliding-mode principles.

---

## Core Concept (Intuitive Explanation)

The guidance strategy operates as follows:

1. **Define a sliding variable** that encodes landing objectives  
   (e.g., position error and velocity error).

2. **Design a sliding-mode control law** that forces the system to converge to this surface despite uncertainties.

3. **Embed instantaneous optimality**, ensuring the control input minimizes a local cost (such as control effort) at each time step without solving a full optimal control problem.

The result is a guidance law that is:
- Robust
- Computationally efficient
- Well-suited for real-time implementation

---

## Repository Structure

```text
.
├── main.m                    # Main simulation entry point
├── Optimizer.m               # Instantaneously optimal control computation
├── SlidingVariable.m         # Sliding surface definition
├── HeadingErrorDynamics.m    # Direction / heading error dynamics
├── VelocityProfile.m         # Reference velocity shaping for soft landing
├── GetGravity.m              # Asteroid gravity model
├── utilities.m               # Shared helper functions
├── plots.m                   # Visualization of simulation results
└── README.md
