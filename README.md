# Brain-Oscillations-Simulation
# Neural Dynamics: Linear Systems & Jacobian Analysis

A computational neuroscience framework designed to analyze how network topology dictates neural population dynamics. This project investigates a 2-node linear rate model of Excitatory-Inhibitory (E-I) interaction, using Jacobian matrix analysis and eigenvalue decomposition to demonstrate the emergence of oscillatory activity based on René Thomas' conjecture.

## Overview

René Thomas' conjecture asserts that the presence of a negative feedback loop (an odd number of inhibitory connections) is a necessary condition for stable, sustained oscillations in dynamical systems. 

This project mathematically proves and computationally simulates how altering synaptic weights in a two-population (Excitatory vs. Inhibitory) rate model pushes the eigenvalues across the imaginary axis, inducing a Hopf bifurcation that generates spiraling, oscillatory activity.

## Mathematical Model

The dynamics of the 2-node linear rate system are defined by two coupled ordinary differential equations (ODEs), where \(x_1\) represents the Excitatory population and \(x_2\) represents the Inhibitory population:

\[\frac{dx_{1}}{dt} = -x_{1} + w_{ee}x_{1} - w_{ei}x_{2}\]

\[\frac{dx_{2}}{dt} = -x_{2} + w_{ie}x_{1} - w_{ii}x_{2}\]

### Model Parameters
* **\(w_{ee}\):** Excitatory self-feedback weight
* **\(w_{ei}\):** Inhibition strength onto the Excitatory population
* **\(w_{ie}\):** Excitation strength onto the Inhibitory population
* **\(w_{ii}\):** Inhibitory self-leak weight

## Jacobian Matrix & Stability Analysis

The local stability of the system around its equilibrium point is governed by the Jacobian Matrix (\(J\)):

\[J = \begin{bmatrix} -1+w_{ee} & -w_{ei} \\ w_{ie} & -1-w_{ii} \end{bmatrix}\]

To demonstrate an unstable oscillation (Hopf Bifurcation), the inclusion of the odd inhibitory loop (\(w_{ei} > 0\)) must push the eigenvalues (\(\lambda\)) of \(J\) across the imaginary axis such that:

\[\text{Re}(\lambda) > 0 \quad \text{and} \quad \text{Im}(\lambda) \neq 0\]

## Key Features

* **Eigenvalue Analysis:** Calculates the exact complex eigenvalues of the system's Jacobian matrix to evaluate phase space behavior.
* **Numerical ODE Integration:** Solves the continuous linear rate system using `scipy.integrate.solve_ivp`.
* **Dual Visualization:** Produces side-by-side plots displaying:
  * Eigenvalues plotted on the complex plane.
  * Time-series activity showing the trajectory of Excitatory (\(x_1\)) and Inhibitory (\(x_2\)) populations.

## Technical Stack & Dependencies

The project relies on Python 3 and the following scientific computing libraries:

| Library | Purpose |
| :--- | :--- |
| **numpy** | Matrix operations & eigenvalue computation (`np.linalg.eig`) |
| **scipy** | Differential equation solving (`scipy.integrate.solve_ivp`) |
| **matplotlib** | Complex plane and time-series plotting |
| **brian2** | Spiking neural network simulation ecosystem (pre-configured) |

## Installation

Install all required Python packages using pip:

```bash
pip install brian2 scipy matplotlib numpy
```
