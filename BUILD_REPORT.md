# BUILD REPORT — KoopmanLab
**Date:** 2026-05-04
**Build Time:** ~45 minutes
**Status:** Deployed and Live

## Links
- **Live:** https://koopmanlab.vercel.app
- **GitHub:** https://github.com/middesurya/daily-webapp-2026-05-04-koopmanlab

## Idea Source
- Trending on arXiv & SIAM journals: Koopman operator theory for data-driven dynamical systems
- Gap in existing portfolio: Had chaos/bifurcation lab (BifurX) and PINNs but nothing on the spectral/operator-theoretic approach to nonlinear dynamics
- Connected to AlphaEvolve trends: data-driven algorithm discovery for scientific computing

## What Was Built

### 6 Interactive Modules:
1. **DMD Engine** — Full Dynamic Mode Decomposition pipeline: generate time-series from Lorenz/Van der Pol/Duffing systems → SVD → low-rank projection → eigendecomposition → mode extraction. Visualizes eigenvalue spectrum on unit circle + time-series reconstruction.

2. **Koopman Eigenfunctions** — Visualizes how nonlinear dynamics become linear in eigenfunction space. Phase portrait with eigenfunction heatmap overlay, trajectory-wise eigenfunction evolution, and nonlinear-vs-linear comparison.

3. **EDMD with Dictionaries** — Extended DMD with 4 dictionary types (Monomials, Fourier, RBF, Hermite). Computes K = pinv(Ψ_X) · Ψ_Y, shows eigenvalue spectrum, prediction vs. truth, and dictionary function visualization grid.

4. **Deep Koopman Autoencoder** — Neural network trained in-browser (pure JS, no TF.js) to learn Koopman-invariant coordinates. Shows training loss, latent space trajectories, reconstruction quality, and learned K-matrix heatmap.

5. **Flow Reconstruction** — Generates synthetic 2D flow fields (von Kármán vortex, jet mixing, cavity), applies DMD, shows singular value spectrum and approximate mode shapes. Animated time slider.

6. **Koopman MPC** — Model Predictive Control using Koopman linearization. Shooting MPC for inverted pendulum and cart-pole. Real-time simulation with angle/control plots.

## Technical Architecture
- **Single HTML file**: 1650+ lines, zero external dependencies
- **Linear algebra from scratch**: Householder QR, Jacobi SVD, QR iteration with Wilkinson shifts, pseudo-inverse via SVD
- **RK4 integrator** for all dynamical systems
- **Canvas-based rendering** with responsive dark theme
- **IIFE module pattern** for clean scope isolation

## Scoring
| Criterion | Weight | Score (1-10) | Weighted |
|-----------|--------|-------------|----------|
| Novelty | 3x | 9 | 27 |
| Feasibility | 3x | 8 | 24 |
| Wow Factor | 2x | 8 | 16 |
| Learning Value | 2x | 10 | 20 |
| Utility | 1x | 7 | 7 |
| **Total** | | | **94/110** |

## Challenges & Lessons
1. **Disk space crisis**: /sessions filesystem was 100% full. Solved by writing files to the mounted personal_proj directory and using GitHub/Vercel APIs directly instead of CLI tools.
2. **Variable scoping**: `const by` used for both pendulum bob position and chart baseline in the same function. Fixed by renaming to `bobX`/`bobY`.
3. **Git on mounted filesystem**: Windows FUSE mount doesn't support `.git` directory operations properly. Used GitHub Contents API for all file uploads.
4. **Parallel API uploads**: GitHub Contents API rejects parallel writes due to SHA conflicts. Sequential uploads required.

## Key Differentiator
This project fills a genuinely unique niche: there is no existing interactive browser-based Koopman operator theory lab. The closest alternatives are MATLAB toolboxes (not interactive, not web) or Python libraries (not visual). KoopmanLab makes graduate-level operator theory accessible through direct manipulation.
