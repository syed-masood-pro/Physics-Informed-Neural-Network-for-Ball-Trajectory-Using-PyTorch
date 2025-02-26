# PINN for Ball Trajectory

This repository contains a Python implementation of a Physics-Informed Neural Network (PINN) for modeling the trajectory of a ball under gravity. The implementation is based on PyTorch and demonstrates how incorporating physical laws into the training process can lead to accurate predictions even when the experimental data is noisy.

## Overview

In this project, the PINN is used to predict the ball's height over time, following the analytical solution:

$$
h(t) = h_0 + v_0 t - 0.5\*g\*t^2
$$

The network is trained using three different regimes:
- **Full PINN:** Combines data loss, physics (ODE) loss, and initial condition loss.
- **Data-Only Loss:** Relies solely on fitting the noisy data.
- **Physics-Only Loss:** Enforces the physical law (ODE) and initial condition, ignoring the noisy data loss.

The **Physics-Only Loss** regime is particularly highlighted as it shows that the PINN can perform well on noisy data by leveraging the underlying physical law:

$$
\frac{dh}{dt} = v_0 - g \* t
$$

and the initial condition:

$$
h(0) = h_0
$$

## Features

- **Simple MLP Architecture:** A feed-forward neural network with two hidden layers using tanh activations.
- **Physics-Informed Loss Functions:** Combines data loss, ODE loss, and initial condition loss to guide the training.
- **Multiple Training Regimes:** Experiments with full PINN, data-only, and physics-only loss formulations.
- **Visualization:** Plots comparing the PINN predictions with the analytical solution and noisy data.

## Prerequisites

- Python 3.x
- [PyTorch](https://pytorch.org/)
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)

Install the required packages using pip:

```bash
pip install torch numpy matplotlib
```
# PINN for Ball Trajectory

This repository contains a Python implementation of a Physics-Informed Neural Network (PINN) for modeling the trajectory of a ball under gravity. The implementation is based on PyTorch and demonstrates how incorporating physical laws into the training process can lead to accurate predictions even when the experimental data is noisy.

## Overview

In this project, the PINN is used to predict the ball's height over time, following the analytical solution:

$$
h(t) = h_0 + v_0 t - 0.5\*g\*t^2
$$

The network is trained using three different regimes:
- **Full PINN:** Combines data loss, physics (ODE) loss, and initial condition loss.
- **Data-Only Loss:** Relies solely on fitting the noisy data.
- **Physics-Only Loss:** Enforces the physical law (ODE) and initial condition, ignoring the noisy data loss.

The **Physics-Only Loss** regime is particularly highlighted as it shows that the PINN can perform well on noisy data by leveraging the underlying physical law:

$$
\frac{dh}{dt} = v_0 - g \* t
$$

and the initial condition:

$$
h(0) = h_0
$$

## Features

- **Simple MLP Architecture:** A feed-forward neural network with two hidden layers using tanh activations.
- **Physics-Informed Loss Functions:** Combines data loss, ODE loss, and initial condition loss to guide the training.
- **Multiple Training Regimes:** Experiments with full PINN, data-only, and physics-only loss formulations.
- **Visualization:** Plots comparing the PINN predictions with the analytical solution and noisy data.

## Prerequisites

- Python 3.x
- [PyTorch](https://pytorch.org/)
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)

Install the required packages using pip:

```bash
pip install torch numpy matplotlib
```

## Getting Started

1. Clone the Repository
```bash
git clone https://github.com/your-username/PINN-for-Ball-Trajectory.git
cd PINN-for-Ball-Trajectory
```
2. Run the Code
    * <ul>Jupyter Notebook: Open the notebook file and run all cells sequentially.</ul>
    * <ul>Python Script: Execute the script directly:
    
    ```bash
     python your_script_name.py
    ```
    </ul>

## Code Structure

* **PINN Model Definition:**
  - Implements a simple multi-layer perceptron (MLP) with two hidden layers and tanh activations.

* **Synthetic Data Generation:**
  - Generates noisy experimental data based on the analytical equation:

$$
h(t) = h_0 + v_0 t - 0.5\*g\*t^2
$$

* **Loss Functions:**
  - **Data Loss:** Mean squared error (MSE) between model predictions and noisy data.
  - **Physics Loss:** Enforces the differential equation:

$$
\frac{dh}{dt} = v_0 - g \* t
$$

* **Initial Condition Loss:** Ensures that the initial condition h(0) = h0 is satisfied.
* **Training Regimes:**
   - **Full PINN:** Uses a weighted sum of data, ODE, and initial condition losses.
   - **Data-Only Loss:** Trains solely on the data loss.
   - **Physics-Only Loss:** Focuses on physics loss and initial condition loss. This regime demonstrates that even with noisy data, enforcing the physical constraints allows the PINN to accurately capture the ball's trajectory.


## Results

The experiments show that the **Physics-Only Loss** regime performs well on noisy data. By strictly enforcing the physics-based constraints, the PINN is able to converge to a solution that closely matches the analytical trajectory of the ball. Visualizations included in the project illustrate that the network's predictions align well with the true solution despite the presence of noise.


## Contributing

Contributions are welcome! If you have any suggestions or improvements, please feel free to open an issue or submit a pull request.

