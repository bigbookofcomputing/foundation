# Chapter 2: The Nature of Computational Numbers Codebook

-----

## Project 1: Comparing Exact vs. Computed Ratios (Cumulative Error)

| Project Title | Relevant Theoretical Background |
| :--- | :--- |
| **Comparing Exact vs. Computed Ratios** | The decimal number $1/7$ has an infinite binary representation, leading to inherent **round-off error** when stored as a finite float. |
| **Core Concept** | Performing repeated arithmetic (summing $1/7$ seven times) **propagates and accumulates** the initial round-off error, demonstrating that the final result is **not** the mathematically exact value of $1.0$. |

### Complete Python Code


```python
import numpy as np
import matplotlib.pyplot as plt

# ==========================================================
# Chapter 2 Codebook: The Nature of Computational Numbers
# Project 1: Comparing Exact vs. Computed Ratios (Cumulative Error)
# ==========================================================

# ==========================================================
# 1. Setup Parameters and Calculation
# ==========================================================
TRUE_VALUE_FRACTION = 1.0 / 7.0
N_SUMS = 7

# Compute the sum (repeated addition, compounding round-off error)
x_sum = TRUE_VALUE_FRACTION + TRUE_VALUE_FRACTION + TRUE_VALUE_FRACTION + TRUE_VALUE_FRACTION + TRUE_VALUE_FRACTION + TRUE_VALUE_FRACTION + TRUE_VALUE_FRACTION

# The true target sum
y_target = 1.0

# ==========================================================
# 2. Calculate Errors
# ==========================================================
absolute_error = np.abs(x_sum - y_target)
relative_error = absolute_error / np.abs(y_target)
epsilon = np.finfo(float).eps 

# ==========================================================
# 3. Analysis Output
# ==========================================================
print("--- Project 1: Comparing Exact vs. Computed Ratios ---")
print(f"Computed Sum (7 * 1/7): {x_sum:.17f}")
print(f"Target Value (1.0):     {y_target:.17f}")
print(f"Machine Epsilon (ε):    {epsilon:.2e}")
print("-" * 40)
print(f"Absolute Error: {absolute_error:.2e}")
print(f"Relative Error: {relative_error:.2e}")
print("\nConclusion: The non-zero error confirms that the initial round-off error from \nrepresenting 1/7 was propagated and accumulated across 7 additions.")

```

    --- Project 1: Comparing Exact vs. Computed Ratios ---
    Computed Sum (7 * 1/7): 0.99999999999999978
    Target Value (1.0):     1.00000000000000000
    Machine Epsilon (ε):    2.22e-16
    ----------------------------------------
    Absolute Error: 2.22e-16
    Relative Error: 2.22e-16
    
    Conclusion: The non-zero error confirms that the initial round-off error from 
    representing 1/7 was propagated and accumulated across 7 additions.


## Project 2: Visualizing the Gaps on the Number Line

| Project Title | Relevant Theoretical Background |
| :--- | :--- |
| **Visualizing the Gaps on the Number Line** | The **IEEE 754 standard** uses an exponent to set the scale. |
| **Core Concept** | The **absolute distance (gap)** between adjacent floating-point numbers is **not constant**; it increases with the number's magnitude (the **'gappy ruler'** effect). However, the **relative precision** (gap size / number) remains constant, fixed by **Machine Epsilon ($\epsilon$)**. |

### Complete Python Code


```python

import numpy as np
import matplotlib.pyplot as plt

# ==========================================================
# Chapter 2 Codebook: The Nature of Computational Numbers
# Project 2: Visualizing the Gaps on the Number Line
# ==========================================================

# ==========================================================
# 1. Setup Function and Test Values
# ==========================================================

def calculate_gap_size(x):
    """Calculates the absolute gap between x and the next largest representable number."""
    # np.nextafter finds the next representable float in the direction of +infinity
    gap = np.nextafter(x, np.inf) - x
    return gap

# Test values spanning many orders of magnitude
x_values_test = [1.0, 10**3, 10**8, 10**16]
gap_sizes = [calculate_gap_size(x) for x in x_values_test]

# ==========================================================
# 2. Analysis Output
# ==========================================================
print("\n--- Project 2: Visualizing the Gaps on the Number Line ---")
print("Comparing absolute gap size across different magnitudes:")
print("-" * 65)

for x, gap in zip(x_values_test, gap_sizes):
    # Calculate the relative precision (should be close to epsilon)
    relative_precision = gap / x
    print(f"Value x: {x:<10.1e} | Absolute Gap: {gap:.3e} | Gap / x (Relative Precision): {relative_precision:.2e}")

print(f"\nConclusion: The Absolute Gap increases with x, but the Relative Precision remains \nconstant (close to machine epsilon), confirming the 'gappy ruler' effect.")

```

    
    --- Project 2: Visualizing the Gaps on the Number Line ---
    Comparing absolute gap size across different magnitudes:
    -----------------------------------------------------------------
    Value x: 1.0e+00    | Absolute Gap: 2.220e-16 | Gap / x (Relative Precision): 2.22e-16
    Value x: 1.0e+03    | Absolute Gap: 1.137e-13 | Gap / x (Relative Precision): 1.14e-16
    Value x: 1.0e+08    | Absolute Gap: 1.490e-08 | Gap / x (Relative Precision): 1.49e-16
    Value x: 1.0e+16    | Absolute Gap: 2.000e+00 | Gap / x (Relative Precision): 2.00e-16
    
    Conclusion: The Absolute Gap increases with x, but the Relative Precision remains 
    constant (close to machine epsilon), confirming the 'gappy ruler' effect.



## Project 3: Simulating and Visualizing Aliasing

| Project Title | Relevant Theoretical Background |
| :--- | :--- |
| **Simulating and Visualizing Aliasing** | **Sampling** (discretization in time) of a continuous signal must obey the **Nyquist-Shannon Criterion**: the sampling rate ($f_s$) must be at least twice the maximum frequency ($2f_{\max}$). |
| **Core Concept** | **Aliasing** occurs when $f_s < 2f_{\max}$, causing a high frequency to be incorrectly interpreted as a lower, false frequency (the alias). |

### Complete Python Code


```python

import numpy as np
import matplotlib.pyplot as plt

# ==========================================================
# Chapter 2 Codebook: The Nature of Computational Numbers
# Project 3: Simulating and Visualizing Aliasing
# ==========================================================

# ==========================================================
# 1. Setup Parameters and True Signal
# ==========================================================
F_MAX = 10.0         # True signal frequency (10 Hz)
T_DURATION = 1.0     # 1 second duration
N_HIGH_RES = 1000    # High resolution points for continuous plot
T_HIGH_RES = np.linspace(0, T_DURATION, N_HIGH_RES, endpoint=False)

def continuous_sine(t, f):
    """The continuous true signal."""
    return np.sin(2 * np.pi * f * t)

Y_TRUE = continuous_sine(T_HIGH_RES, F_MAX)

# ==========================================================
# 2. Case 1: Sufficient Sampling (No Aliasing)
# ==========================================================
FS_SUFFICIENT = 50.0 # Fs > 2*F_MAX (50 Hz > 20 Hz)
T_SAMPLED_SUF = np.linspace(0, T_DURATION, int(FS_SUFFICIENT * T_DURATION), endpoint=False)
Y_SAMPLED_SUF = continuous_sine(T_SAMPLED_SUF, F_MAX)

# ==========================================================
# 3. Case 2: Insufficient Sampling (Aliasing Occurs)
# ==========================================================
FS_INSUFFICIENT = 15.0 # Fs < 2*F_MAX (15 Hz < 20 Hz)
T_SAMPLED_INS = np.linspace(0, T_DURATION, int(FS_INSUFFICIENT * T_DURATION), endpoint=False)
Y_SAMPLED_INS = continuous_sine(T_SAMPLED_INS, F_MAX)

# Calculate the alias frequency (f_alias = |f_max - n*Fs|)
F_ALIAS = np.abs(F_MAX - 1.0 * FS_INSUFFICIENT) 
Y_ALIAS_RECONSTRUCTED = continuous_sine(T_HIGH_RES, F_ALIAS)

# ==========================================================
# 4. Visualization
# ==========================================================
fig, ax = plt.subplots(figsize=(8, 5))
ax.plot(T_HIGH_RES, Y_TRUE, 'k:', label=f"True Signal (F={F_MAX} Hz)")
ax.plot(T_SAMPLED_SUF, Y_SAMPLED_SUF, 'bo', markersize=3, label=f"Sampled (Fs={FS_SUFFICIENT} Hz, No Alias)")
ax.plot(T_SAMPLED_INS, Y_SAMPLED_INS, 'ro', markersize=5, alpha=0.8, label=f"Sampled (Fs={FS_INSUFFICIENT} Hz, Aliased)")
ax.plot(T_HIGH_RES, Y_ALIAS_RECONSTRUCTED, 'r-', alpha=0.6, label=f"Alias Reconstruction (F={F_ALIAS} Hz)")

ax.set_title("Nyquist-Shannon Criterion and Aliasing")
ax.set_xlabel("Time (s)")
ax.set_ylabel("Amplitude")
ax.grid(True)
ax.legend(loc='upper right')
plt.tight_layout()
plt.show()

# ==========================================================
# 5. Analysis Output
# ==========================================================
print("\n--- Aliasing Analysis ---")
print(f"True Signal Frequency (F_max): {F_MAX} Hz")
print(f"Insufficient Sampling Rate (Fs): {FS_INSUFFICIENT} Hz")
print(f"Nyquist Limit (2*F_max): {2 * F_MAX} Hz")
print(f"Resulting Alias Frequency: {F_ALIAS} Hz")
print("\nConclusion: The insufficient sampling rate (15 Hz) fails to capture the 10 Hz signal, \ncreating a false 5 Hz wave (the alias). The reconstructed signal follows \nonly the lower, aliased frequency.")

```


    
![png](Chapter-2-CodeBook_files/output_5_0.png)
    


    
    --- Aliasing Analysis ---
    True Signal Frequency (F_max): 10.0 Hz
    Insufficient Sampling Rate (Fs): 15.0 Hz
    Nyquist Limit (2*F_max): 20.0 Hz
    Resulting Alias Frequency: 5.0 Hz
    
    Conclusion: The insufficient sampling rate (15 Hz) fails to capture the 10 Hz signal, 
    creating a false 5 Hz wave (the alias). The reconstructed signal follows 
    only the lower, aliased frequency.

