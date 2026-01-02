# Chapter 3: Root Finding Codebook

## Project-1: Quantum Mechanics - Finding Odd States Energy Levels

| Project Title | Relevant Theoretical Background |
| :--- | :--- |
| **Finding Odd States Energy Levels** | The **Time-Independent Schrödinger Equation** yields a transcendental equation for bound states in a finite potential well. These roots, $k_n$, are non-analytical. |
| **Core Equation** | The equation for **odd-parity states** is solved for roots $k$ using the coupling parameter $\alpha=8.0$: $f_{\text{odd}}(k) = \cot(k) + \sqrt{\frac{\alpha^2}{k^2} - 1} = 0$. |
| **Physical Result** | The allowed energy levels are discrete and calculated from the roots: $E_n = \frac{\hbar^2 k_n^2}{2m}$. |

-----

### Complete Python Code


```python

import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import root_scalar

# ==========================================================
# Project: Quantum Mechanics - Finding Odd States Energy Levels
# ==========================================================

# --- Project Description ---
# This project solves the transcendental equation for the odd-parity bound states
# in a 1D finite potential well. It demonstrates the necessity of numerical
# root-finding (Chapter 3) for physical systems where analytical solutions are
# impossible or complex. The solution relies on bracketing the roots between
# known asymptotes (e.g., cot(k) singularities).
# ---------------------------

# ==========================================================
# 1. Setup Physical Constants and Parameters
# ==========================================================
# For simplicity, we set constants to 1.0.
HBAR = 1.0  # Reduced Planck constant
MASS = 1.0  # Mass of the particle
# Alpha (α) parameter controls the well depth. We use α=8.0 to ensure 
# the first two odd states are bound (k <= ALPHA).
ALPHA = 8.0 

# Energy calculation factor: E = (hbar^2 / (2 * m)) * k^2
ENERGY_FACTOR = (HBAR**2) / (2.0 * MASS) 

# ==========================================================
# 2. Define the Transcendental Equation (Odd States)
# ==========================================================
def odd_state_equation(k, alpha=ALPHA):
    """
    f_odd(k) = cot(k) + sqrt(alpha^2/k^2 - 1) = 0
    k is the wave number parameter.
    """
    # The term inside the square root must be non-negative (k <= alpha)
    if k > alpha:
        return np.inf
    
    # Check for cot(k) singularity at k=n*pi
    if np.isclose(np.sin(k), 0):
        return np.inf
        
    cot_k = 1.0 / np.tan(k)
    sqrt_term = np.sqrt((alpha / k)**2 - 1.0)
    
    return cot_k + sqrt_term

# ==========================================================
# 3. Determine Brackets (The safety phase)
# ==========================================================
# Odd states roots k_n are found in the intervals [ (n-1/2)π, nπ ].
# k1 interval: [π/2, π]. k2 interval: [3π/2, 2π].
# Small offsets (0.01 and 1e-3) are used to avoid cot(k) singularities/infinities.

# First Odd State (k1)
bracket_k1_low = np.pi / 2.0 + 0.01
bracket_k1_high = np.pi - 1e-3

# Second Odd State (k2)
bracket_k2_low = 3.0 * np.pi / 2.0 + 0.01
# Max possible k is ALPHA=8.0. We check this bound: 2*pi ≈ 6.28.
bracket_k2_high = min(2.0 * np.pi - 1e-3, ALPHA - 1e-3) 

# ==========================================================
# 4. Find the Roots using Brent's Method (The speed phase)
# ==========================================================

try:
    # Use root_scalar with the brentq method for high reliability and efficiency.
    
    # Root 1 (k1)
    result_k1 = root_scalar(odd_state_equation, bracket=[bracket_k1_low, bracket_k1_high], method='brentq')
    k1 = result_k1.root
    
    # Root 2 (k2)
    result_k2 = root_scalar(odd_state_equation, bracket=[bracket_k2_low, bracket_k2_high], method='brentq')
    k2 = result_k2.root
    
    # ==========================================================
    # 5. Calculate Physical Energy Levels
    # ==========================================================
    E1 = ENERGY_FACTOR * k1**2
    E2 = ENERGY_FACTOR * k2**2
    
    # ==========================================================
    # 6. Final Output
    # ==========================================================
    print(f"--- Results for Finite Potential Well (ALPHA = {ALPHA:.1f}) ---")
    print(f"Transcendental Equation Solved: f(k) = cot(k) + sqrt(α²/k² - 1) = 0")
    
    print("\n[1] First Odd State (n=1):")
    print(f"  Wave Number k₁: {k1:.6f}")
    print(f"  Energy E₁:      {E1:.6f} (Units: ℏ²/2m)")
    
    print("\n[2] Second Odd State (n=3):")
    print(f"  Wave Number k₂: {k2:.6f}")
    print(f"  Energy E₂:      {E2:.6f} (Units: ℏ²/2m)")
    
    print("\n--- Verification ---")
    print(f"Final check f(k₁): {odd_state_equation(k1):.3e}")
    print(f"Final check f(k₂): {odd_state_equation(k2):.3e}")

except Exception as e:
    print(f"An error occurred: {e}")
    print("Please ensure the chosen ALPHA parameter (well depth) is large enough to contain at least two bound odd states.")

```

    --- Results for Finite Potential Well (ALPHA = 8.0) ---
    Transcendental Equation Solved: f(k) = cot(k) + sqrt(α²/k² - 1) = 0
    
    [1] First Odd State (n=1):
      Wave Number k₁: 2.785902
      Energy E₁:      3.880625 (Units: ℏ²/2m)
    
    [2] Second Odd State (n=3):
      Wave Number k₂: 5.521446
      Energy E₂:      15.243185 (Units: ℏ²/2m)
    
    --- Verification ---
    Final check f(k₁): 8.882e-16
    Final check f(k₂): -7.050e-13


### Analysis of Results

The numerical solution successfully identified the two lowest odd-parity energy states for the given potential depth ($\alpha=8.0$).

  * **Wave Numbers ($k_n$):** The calculated wave numbers $k_1 \approx 2.786$ and $k_2 \approx 5.521$ both satisfy the binding condition $k < \alpha=8.0$.
  * **Energy Levels ($E_n$):** The energies $E_1 \approx 3.881$ and $E_2 \approx 15.243$ are distinct and quantized, confirming the physical behavior of the quantum well.
  * **Convergence:** The final function checks ($f(k_n)$) are extremely close to zero ($10^{-13}$ to $10^{-15}$), demonstrating that Brent's method achieved machine-level accuracy in solving the transcendental equation.
