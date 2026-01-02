# Chapter 4: Working with Data: Interpolation & Fitting

---

## Project 1: Non-Linear Fitting — Radioactive Decay Half-Life

### Project Detail

| Feature | Description |
| :--- | :--- |
| **Goal** | Determine the decay constant ($\lambda$) and half-life ($t_{1/2}$) of a substance by fitting noisy experimental data to an exponential decay model. |
| **Method** | **Non-Linear Least Squares Fitting** using $\text{scipy.optimize.curve\_fit}$. This method is required because the decay constant ($\lambda$) is a non-linear parameter (an exponent). |
| **Mathematical Model** | $$N(t) = N_0 e^{-\lambda t}$$ |
| **Error Analysis** | The uncertainty of the fitted parameters is extracted from the diagonal elements of the **Covariance Matrix ($\mathbf{P}_{\text{cov}}$)** returned by $\text{curve\_fit}$. The uncertainty in $\lambda$ is $\Delta \lambda = \sqrt{\mathbf{P}_{\text{cov}}[1, 1]}$. |
| **Physical Result** | The half-life is calculated as $t_{1/2} = \frac{\ln(2)}{\lambda}$. |

-----

### Complete Python Code


```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import curve_fit

# ==========================================================
# 1. Setup Data and Model
# ==========================================================

# Define the TRUE underlying parameters
TRUE_N0 = 1000.0  # Initial number of atoms
TRUE_LAMBDA = 0.1 # Decay constant (s⁻¹)

# Generate synthetic time data (0 to 50 seconds)
time_data = np.linspace(0, 50, 50) 
# Generate true decay values
N_true = TRUE_N0 * np.exp(-TRUE_LAMBDA * time_data)
# Add Gaussian noise to simulate experimental error (noisy data)
NOISE_STD = 5.0
N_data = N_true + np.random.normal(0, NOISE_STD, size=time_data.size)

# Define the non-linear model function for curve_fit
def exponential_decay_model(t, N0, lambda_):
    """N(t) = N0 * exp(-lambda * t)"""
    return N0 * np.exp(-lambda_ * t)

# ==========================================================
# 2. Perform Non-Linear Least Squares Fit
# ==========================================================

# Initial guesses for the parameters (important for convergence)
p0 = [1100.0, 0.05] 

# Perform the fit: popt = optimal parameters, pcov = covariance matrix
popt, pcov = curve_fit(
    exponential_decay_model, 
    time_data, 
    N_data, 
    p0=p0, 
    sigma=np.full_like(N_data, NOISE_STD), # Use known error for weighted fit
    absolute_sigma=True
)

# Extract optimal parameters and their uncertainties (standard deviations)
N0_fit, lambda_fit = popt
perr = np.sqrt(np.diag(pcov)) # Diagonal elements of pcov are the variances (err²).
N0_err, lambda_err = perr

# ==========================================================
# 3. Calculate Physical Result (Half-Life)
# ==========================================================

# Half-life calculation and error propagation
t_half = np.log(2) / lambda_fit
# Error propagation for t_half: Δt_half = |dt_half/dλ| * Δλ
t_half_err = np.abs(-np.log(2) / (lambda_fit**2)) * lambda_err

# ==========================================================
# 4. Visualization and Analysis
# ==========================================================

# Generate the smooth fitted curve for plotting
N_fit_curve = exponential_decay_model(time_data, N0_fit, lambda_fit)

fig, ax = plt.subplots(figsize=(8, 5))
ax.errorbar(time_data, N_data, yerr=NOISE_STD, fmt='o', capsize=3, color='gray', label="Experimental Data (N + Noise)")
ax.plot(time_data, N_fit_curve, 'r-', linewidth=2, label="Least Squares Fit")
ax.set_title(r"Non-Linear Fit of Radioactive Decay $N(t) = N_0 e^{-\lambda t}$")
ax.set_xlabel("Time (s)")
ax.set_ylabel("Number of Particles ($N$)")
ax.legend()
ax.grid(True)
plt.tight_layout()
plt.show()

# Analysis Output
print("\n--- Fit Results ---")
print(f"Fitted N₀:      {N0_fit:.4f} ± {N0_err:.4f}")
print(f"Fitted λ:       {lambda_fit:.6f} ± {lambda_err:.6f} s⁻¹")
print(f"True λ:         {TRUE_LAMBDA:.6f} s⁻¹")

print("\n--- Physical Conclusion ---")
print(f"Half-Life (t₁/₂): {t_half:.2f} ± {t_half_err:.2f} seconds")
print(f"True Half-Life:   {np.log(2) / TRUE_LAMBDA:.2f} seconds")

# Final Conclusion: The fitted half-life and decay constant accurately reflect the 
# true parameters despite the added noise, and the error bounds are successfully quantified 
# using the covariance matrix.


```


    
![png](Chapter-4-CodeBook_files/output_1_0.png)
    


    
    --- Fit Results ---
    Fitted N₀:      1000.2360 ± 2.8954
    Fitted λ:       0.099897 ± 0.000431 s⁻¹
    True λ:         0.100000 s⁻¹
    
    --- Physical Conclusion ---
    Half-Life (t₁/₂): 6.94 ± 0.03 seconds
    True Half-Life:   6.93 seconds



## Project 2: Interpolation — Comet Trajectory and Velocity

### Project Detail

| Feature | Description |
| :--- | :--- |
| **Goal** | Find the instantaneous position, velocity, and acceleration of a comet at an arbitrary time point using discrete, sparse positional data. |
| **Method** | **Cubic Spline Interpolation** using $\text{scipy.interpolate.CubicSpline}$. This is used because the data is assumed to be **clean and exact** (from an almanac or simulation) and requires a continuous function for calculus operations. |
| **Mathematical Concept** | The spline object $\mathbf{S}(t)$ serves as a continuous function $\mathbf{r}(t) = (x(t), y(t))$. The velocity $\mathbf{v}(t)$ and acceleration $\mathbf{a}(t)$ are the first ($\nu=1$) and second ($\nu=2$) derivatives of the spline: $$\mathbf{v}(t) = \frac{d\mathbf{S}}{dt} = \mathbf{S}(t, \nu=1)$$ |
| **Key Insight** | The continuous derivatives of the spline are built-in, providing a fast and accurate way to perform calculus on discrete data, bridging Chapter 4 and Chapter 5 (Numerical Differentiation). |

-----

### Complete Python Code


```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.interpolate import CubicSpline

# ==========================================================
# 1. Setup Data: Comet Trajectory (Clean, Sparse Data)
# ==========================================================

# Time in days (sparse observation points)
time_points = np.array([0.0, 10.0, 25.0, 40.0, 60.0, 85.0, 110.0])

# x and y positions (simulated clean data in AU)
x_data = np.array([5.00, 4.87, 4.30, 3.48, 2.05, 0.50, -1.05])
y_data = np.array([0.00, 0.98, 1.95, 2.60, 2.95, 2.50, 1.10])

# Combine x and y data into a single matrix for a vectorized spline
r_data = np.vstack((x_data, y_data))

# ==========================================================
# 2. Create Cubic Spline Objects
# ==========================================================

# The CubicSpline function fits separate cubic polynomials to each interval
# ensuring continuity in the function, slope (v), and curvature (a).
r_spline = CubicSpline(time_points, r_data, axis=1)

# ==========================================================
# 3. Analysis: Evaluate Position, Velocity, and Acceleration
# ==========================================================

# Generate a fine time array for smooth plotting and accurate interpolation
time_fine = np.linspace(time_points.min(), time_points.max(), 500)

# Evaluate the spline at the fine time points:
# Position: nu=0 (default)
r_interpolated = r_spline(time_fine, nu=0)
# Velocity: nu=1 (first derivative)
v_interpolated = r_spline(time_fine, nu=1)
# Acceleration: nu=2 (second derivative)
a_interpolated = r_spline(time_fine, nu=2)

# Specific calculation: Find the state at t = 30 days
t_arbitrary = 30.0
r_30 = r_spline(t_arbitrary)
v_30 = r_spline(t_arbitrary, nu=1)
a_30 = r_spline(t_arbitrary, nu=2)

# ==========================================================
# 4. Visualization
# ==========================================================

fig, ax = plt.subplots(1, 2, figsize=(10, 5))
C_MAG = np.linalg.norm(v_interpolated, axis=0) # Velocity magnitude for color mapping

# --- Plot 1: Trajectory and Velocity Field (Space Domain) ---
ax[0].scatter(x_data, y_data, marker='o', color='red', s=50, label="Observed Data")
ax[0].plot(r_interpolated[0], r_interpolated[1], 'k-', linewidth=1, label="Cubic Spline Trajectory")

# Add a few velocity vectors (e.g., every 50th point)
skip = 50
ax[0].quiver(r_interpolated[0, ::skip], r_interpolated[1, ::skip],
             v_interpolated[0, ::skip], v_interpolated[1, ::skip],
             C_MAG[::skip], cmap='viridis', scale=50, label="Velocity Vectors")
ax[0].set_title("Comet Trajectory and Velocity Field")
ax[0].set_xlabel("x Position (AU)")
ax[0].set_ylabel("y Position (AU)")
ax[0].axis('equal')
ax[0].grid(True)


# --- Plot 2: Acceleration Magnitude vs. Time ---
ax[1].plot(time_fine, np.linalg.norm(a_interpolated, axis=0), 'g-', linewidth=2)
ax[1].axvline(t_arbitrary, color='gray', linestyle='--', label="t = 30 days")
ax[1].set_title("Acceleration Magnitude $|\\mathbf{a}(t)|$")
ax[1].set_xlabel("Time (days)")
ax[1].set_ylabel("Acceleration Magnitude (AU/day²)")
ax[1].grid(True)
ax[1].legend()

plt.tight_layout()
plt.show()

# Analysis Output
print("\n--- Instantaneous State at t = 30.0 days ---")
print(f"Position (x, y):      ({r_30[0]:.4f}, {r_30[1]:.4f}) AU")
print(f"Velocity (vx, vy):    ({v_30[0]:.4f}, {v_30[1]:.4f}) AU/day")
print(f"Acceleration (ax, ay): ({a_30[0]:.4f}, {a_30[1]:.4f}) AU/day²")

```


    
![png](Chapter-4-CodeBook_files/output_3_0.png)
    


    
    --- Instantaneous State at t = 30.0 days ---
    Position (x, y):      (4.0543, 2.1981) AU
    Velocity (vx, vy):    (-0.0514, 0.0468) AU/day
    Acceleration (ax, ay): (-0.0010, -0.0012) AU/day²

