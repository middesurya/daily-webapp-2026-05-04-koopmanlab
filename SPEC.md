# KoopmanLab — Interactive Koopman Operator Theory & Dynamic Mode Decomposition Laboratory

## Overview
An in-browser interactive laboratory for exploring Koopman operator theory, Dynamic Mode Decomposition (DMD), and data-driven dynamical systems analysis. No dependencies, no build step — pure HTML/CSS/JS with all numerical linear algebra implemented from scratch.

## Why This Matters
Koopman operator theory represents one of the most elegant ideas in modern applied mathematics: **any nonlinear dynamical system can be represented as a linear (but infinite-dimensional) operator acting on observable functions**. This transforms intractable nonlinear problems into tractable linear ones. It's the mathematical backbone behind data-driven methods like DMD, which has revolutionized fluid dynamics, neuroscience, control theory, and climate science.

## Modules (6 total)

### 1. DMD Engine
- Generate time-series from canonical dynamical systems (Lorenz, Van der Pol, Duffing, Double Pendulum)
- Compute exact DMD: SVD → low-rank projection → eigendecomposition
- Visualize DMD eigenvalues on the unit circle (stable inside, unstable outside)
- Show DMD mode amplitudes, frequencies, and growth/decay rates
- Reconstruct and forecast signals using DMD modes
- Interactive: adjust number of modes retained, see reconstruction error

### 2. Koopman Eigenfunctions
- Visualize the central concept: nonlinear dynamics become LINEAR in Koopman space
- Side-by-side: phase portrait in state space vs. linear evolution in eigenfunction coordinates
- Show how observable functions "lift" the dynamics
- Interactive eigenfunctions for 2D systems (Duffing oscillator, limit cycles)
- Color-coded eigenfunction level sets overlaid on phase portraits
- Real-time animation showing how points flow linearly along eigenfunction coordinates

### 3. EDMD with Dictionaries
- Extended Dynamic Mode Decomposition using basis function dictionaries
- Compare dictionary types: Monomials, Fourier, Radial Basis Functions (RBFs), Hermite polynomials
- Interactive dictionary size slider (number of basis functions)
- Visualize approximation quality: eigenvalue convergence as dictionary grows
- Residual error heatmap showing where the approximation breaks down
- Parsimony analysis: how many basis functions are really needed?

### 4. Deep Koopman Autoencoder
- Train a neural network to learn Koopman-invariant coordinates
- Architecture: Encoder → Linear dynamics (K matrix) → Decoder
- Real-time training visualization with TF.js
- Loss curve, latent space trajectory, reconstruction quality
- Compare: raw state space vs. learned Koopman coordinates
- Show the learned K matrix eigenvalues and their physical meaning

### 5. Flow Reconstruction
- Apply DMD to 2D flow fields (von Kármán vortex street, cavity flow, jet mixing)
- Decompose complex flows into coherent spatiotemporal modes
- Animate individual DMD modes and their superposition
- Interactive mode selection: toggle modes on/off, see contribution
- Frequency spectrum of the flow
- Forecast: extrapolate the flow forward in time using DMD

### 6. Koopman MPC (Model Predictive Control)
- Use Koopman linearization for control of nonlinear systems
- Control a cart-pole or inverted pendulum using Koopman-based linear MPC
- Side-by-side comparison: Koopman MPC vs. naive linear control
- Visualize the predicted trajectory and control inputs
- Adjust MPC horizon, control weight, and prediction accuracy
- Show how Koopman enables "linear" control of nonlinear systems

## Tech Stack
- Single HTML file, zero external dependencies
- All linear algebra (SVD, eigendecomposition, matrix operations) implemented in JS
- Canvas-based 2D rendering + WebGL for performance-critical parts
- TF.js (loaded from CDN) for Module 4 only
- CSS Grid layout with dark theme, responsive design

## Design
- Dark background (#0a0a0f) with neon accent colors
- Module tabs across the top
- Each module: control panel (left) + visualization canvas (right)
- Consistent color scheme: eigenvalues=cyan, modes=magenta, data=green, forecast=orange
