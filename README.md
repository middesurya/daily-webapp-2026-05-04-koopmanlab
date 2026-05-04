# KoopmanLab

**Interactive Koopman Operator Theory & Dynamic Mode Decomposition Laboratory**

An in-browser interactive laboratory for exploring one of the most elegant ideas in modern applied mathematics: **Koopman operator theory**, which transforms intractable nonlinear dynamical systems into tractable linear ones.

## 6 Interactive Modules

1. **DMD Engine** — Generate time-series from chaotic systems (Lorenz, Van der Pol, Duffing), compute Dynamic Mode Decomposition, visualize eigenvalue spectra on the unit circle, and reconstruct/forecast signals using DMD modes.

2. **Koopman Eigenfunctions** — Visualize how nonlinear dynamics become LINEAR in Koopman eigenfunction coordinates. Side-by-side phase portraits with eigenfunction heatmaps and trajectory evolution.

3. **EDMD with Dictionaries** — Extended DMD using monomial, Fourier, RBF, and Hermite polynomial dictionaries. Compare approximation quality and visualize basis functions.

4. **Deep Koopman Autoencoder** — Train a neural network (pure JS, no TF.js) to learn Koopman-invariant coordinates where dynamics are linear. Real-time training with loss curves, latent space, and K-matrix visualization.

5. **Flow Reconstruction** — Decompose 2D fluid flows (vortex streets, jets, cavity flows) into coherent spatiotemporal DMD modes. Animate individual modes and their superposition.

6. **Koopman MPC** — Model Predictive Control using Koopman linearization. Control an inverted pendulum or cart-pole using "linear" control of fundamentally nonlinear systems.

## Technical Highlights

- **Zero dependencies** — all linear algebra (SVD, QR, eigendecomposition, pseudo-inverse) implemented from scratch in JavaScript
- **Single HTML file** — no build step, no bundler, no framework
- **Householder QR**, **Jacobi SVD**, **QR iteration with Wilkinson shifts** for eigendecomposition
- **RK4 integration** for dynamical systems
- **Canvas-based rendering** with responsive dark theme

## The Mathematics

The Koopman operator K acts on observable functions g(x) of a dynamical system x' = f(x):

**(Kg)(x) = g(f(x))**

Even when f is nonlinear, K is always linear (but infinite-dimensional). DMD and EDMD approximate this infinite-dimensional operator from data, enabling linear analysis of nonlinear phenomena.

## Live Demo

Deployed on Vercel (link in repo description)

## License

MIT — Built with Claude Code
