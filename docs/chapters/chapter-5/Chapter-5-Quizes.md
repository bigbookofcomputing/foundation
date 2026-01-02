# **Chapter-5: Quizes**

---

!!! note "Quiz"
    **1. What is the fundamental mathematical tool used to derive all finite-difference formulas for numerical differentiation?**

    - A. The Fourier Transform
    - B. The Taylor Series
    - C. The Method of Least Squares
    - D. The Runge-Kutta Method

    ??? info "See Answer"
        **Correct: B**

        *(The Taylor series acts as the bridge between the continuous world of calculus and the discrete world of grid-point arithmetic, allowing us to express derivatives in terms of function values.)*

---

!!! note "Quiz"
    **2. What is the order of accuracy for the Forward Difference formula, $f'(x) \approx \frac{f(x+h) - f(x)}{h}$?**

    - A. $O(1)$
    - B. $O(h)$
    - C. $O(h^2)$
    - D. $O(h^3)$

    ??? info "See Answer"
        **Correct: B**

        *(The Forward Difference is a first-order accurate method, meaning the truncation error is directly proportional to the step size $h$.)*

---

!!! note "Quiz"
    **3. Why is the Central Difference formula, $f'(x) \approx \frac{f(x+h) - f(x-h)}{2h}$, considered the "workhorse" of numerical differentiation?**

    - A. It is the easiest to implement.
    - B. It is second-order accurate ($O(h^2)$), offering a much faster convergence rate than the Forward Difference.
    - C. It is immune to round-off error.
    - D. It can be used at the boundaries of a grid without modification.

    ??? info "See Answer"
        **Correct: B**

        *(Its $O(h^2)$ accuracy means halving the step size reduces the truncation error by a factor of four, making it vastly more efficient.)*

---

!!! note "Quiz"
    **4. The "great war" of numerical differentiation refers to the trade-off between which two types of error?**

    - A. Syntax Error and Logic Error
    - B. Systematic Error and Random Error
    - C. Truncation Error and Round-off Error
    - D. Aliasing Error and Quantization Error

    ??? info "See Answer"
        **Correct: C**

        *(Truncation error (from the algorithm) decreases as $h$ gets smaller, while round-off error (from hardware precision) increases, creating a conflict.)*

---

!!! note "Quiz"
    **5. What happens to the total error in the Central Difference formula when the step size $h$ is made extremely small (e.g., $h \sim 10^{-15}$)?**

    - A. The error approaches zero.
    - B. The error is dominated by truncation error.
    - C. The error explodes due to catastrophic cancellation.
    - D. The error becomes constant.

    ??? info "See Answer"
        **Correct: C**

        *(When $h$ is tiny, the subtraction $f(x+h) - f(x-h)$ loses significant digits, and the result (dominated by noise) is amplified by division by a very small $2h$.)*

---

!!! note "Quiz"
    **6. What is the characteristic shape of a log-log plot of absolute error versus step size $h$ for a numerical derivative?**

    - A. A straight horizontal line
    - B. A "V" shape
    - C. An "S" shape
    - D. A bell curve

    ??? info "See Answer"
        **Correct: B**

        *(The "V-Plot" shows truncation error dominating on the right (downward slope) and round-off error dominating on the left (upward slope), with a minimum at the "sweet spot".)*

---

!!! note "Quiz"
    **7. For the $O(h^2)$ Central Difference formula, the optimal step size $h_{opt}$ that minimizes total error scales with machine epsilon ($\epsilon_m$) as:**

    - A. $h_{opt} \sim \epsilon_m$
    - B. $h_{opt} \sim \sqrt{\epsilon_m}$
    - C. $h_{opt} \sim \epsilon_m^{1/3}$
    - D. $h_{opt} \sim \epsilon_m^{2/3}$

    ??? info "See Answer"
        **Correct: C**

        *(Balancing the truncation error ($Ch^2$) and round-off error ($D\epsilon_m/h$) leads to an optimal step size that scales with the cube root of machine epsilon, typically around $10^{-5}$ to $10^{-6}$ for double precision.)*

---

!!! note "Quiz"
    **8. What is the three-point stencil formula for the second derivative, $f''(x)$?**

    - A. $\frac{f(x+h) - f(x-h)}{2h}$
    - B. $\frac{f(x+h) - 2f(x) + f(x-h)}{h^2}$
    - C. $\frac{f(x+h) - 2f(x) + f(x-h)}{2h}$
    - D. $\frac{f(x+2h) - 2f(x+h) + f(x)}{h^2}$

    ??? info "See Answer"
        **Correct: B**

        *(This formula is derived by adding the forward and backward Taylor expansions and is the numerical approximation of the 1D Laplacian operator.)*

---

!!! note "Quiz"
    **9. In the V-plot, what is the approximate slope of the error curve in the truncation-dominated region (right side) for the Central Difference method?**

    - A. +1
    - B. +2
    - C. -1
    - D. -2

    ??? info "See Answer"
        **Correct: B**

        *(Because the method is $O(h^2)$ accurate, the error is proportional to $h^2$. On a log-log plot, this corresponds to a line with a slope of +2.)*

---

!!! note "Quiz"
    **10. In physics, the force $F(x)$ can be computed from the potential energy $V(x)$ using which relationship?**

    - A. $F(x) = \int V(x) dx$
    - B. $F(x) = \frac{d^2V}{dx^2}$
    - C. $F(x) = V(x) \cdot x$
    - D. $F(x) = -\frac{dV}{dx}$

    ??? info "See Answer"
        **Correct: D**

        *(Force is the negative gradient (or derivative in 1D) of the potential energy. This relationship is fundamental to classical mechanics and molecular dynamics.)*

---

!!! note "Quiz"
    **11. The numerical formula $\frac{f(x+h) - 2f(x) + f(x-h)}{h^2}$ is the discrete approximation of which fundamental operator in physics?**

    - A. The Gradient ($\nabla$)
    - B. The Curl ($\nabla \times$)
    - C. The Divergence ($\nabla \cdot$)
    - D. The Laplacian ($\nabla^2$)

    ??? info "See Answer"
        **Correct: D**

        *(This stencil is the 1D numerical Laplacian, essential for solving the Heat, Wave, and Schrödinger equations.)*

---

!!! note "Quiz"
    **12. When deriving the Central Difference formula for $f'(x)$, which terms are perfectly cancelled out by subtracting the backward Taylor expansion from the forward one?**

    - A. The odd-powered terms ($h, h^3, h^5, \dots$)
    - B. The even-powered terms ($h^0, h^2, h^4, \dots$)
    - C. Only the $f(x)$ term
    - D. No terms are cancelled

    ??? info "See Answer"
        **Correct: B**

        *(The symmetric nature of the stencil causes the constant term $f(x)$, the second derivative term $f''(x)$, and all other even-powered terms to cancel, leading to the method's high accuracy.)*

---

!!! note "Quiz"
    **13. In the Lennard-Jones potential application, what was the purpose of having an analytical solution for the force?**

    - A. To make the computation faster.
    - B. To serve as a "ground truth" to verify the accuracy of the numerical method.
    - C. It was required to choose the parameters $\epsilon$ and $\sigma$.
    - D. It was not used in the project.

    ??? info "See Answer"
        **Correct: B**

        *(By comparing the numerical result to the exact analytical answer, we can precisely measure the error and confirm that our method achieves the expected machine-precision accuracy.)*

---

!!! note "Quiz"
    **14. If you are using a first-order accurate method and decrease your step size $h$ by a factor of 100, how much do you expect the truncation error to decrease?**

    - A. By a factor of 10.
    - B. By a factor of 100.
    - C. By a factor of 1,000.
    - D. By a factor of 10,000.

    ??? info "See Answer"
        **Correct: B**

        *(For a first-order ($O(h)$) method, the error is linearly proportional to $h$. Reducing $h$ by a factor of 100 reduces the error by the same factor.)*

---

!!! note "Quiz"
    **15. If you are using a second-order accurate method and decrease your step size $h$ by a factor of 100, how much do you expect the truncation error to decrease?**

    - A. By a factor of 10.
    - B. By a factor of 100.
    - C. By a factor of 1,000.
    - D. By a factor of 10,000.

    ??? info "See Answer"
        **Correct: D**

        *(For a second-order ($O(h^2)$) method, the error is proportional to $h^2$. Reducing $h$ by a factor of 100 reduces the error by a factor of $100^2 = 10,000$.)*

---

!!! note "Quiz"
    **16. What is the physical meaning of the repulsive ($r^{-12}$) term in the Lennard-Jones potential?**

    - A. It models the long-range gravitational attraction between atoms.
    - B. It models the van der Waals attraction at long distances.
    - C. It models the Pauli exclusion principle, preventing atoms from occupying the same space.
    - D. It models the covalent bond energy.

    ??? info "See Answer"
        **Correct: C**

        *(The steep $r^{-12}$ term creates a strong repulsive force at very short distances, representing the quantum mechanical effect that prevents electron orbitals from overlapping.)*

---

!!! note "Quiz"
    **17. In the V-plot, what is the approximate slope of the error curve in the round-off-dominated region (left side)?**

    - A. +2
    - B. +1
    - C. -1
    - D. -2

    ??? info "See Answer"
        **Correct: C**

        *(The round-off error scales as $\epsilon_m/h$, or $h^{-1}$. On a log-log plot, a function proportional to $h^{-1}$ has a slope of -1.)*

---

!!! note "Quiz"
    **18. When computing the force from the Lennard-Jones potential, an error of $10^{-14}$ was achieved. This result is considered:**

    - A. A failure, because the error should be zero.
    - B. A success, because this is near the limit of machine precision for 64-bit floats.
    - C. Mediocre, as an error of $10^{-20}$ should be achievable.
    - D. A sign that the step size $h$ was too large.

    ??? info "See Answer"
        **Correct: B**

        *(An error of $10^{-14}$ to $10^{-15}$ indicates that the numerical method is so accurate that the only remaining error is the unavoidable round-off error inherent in the computer's hardware.)*

---

!!! note "Quiz"
    **19. When deriving the second derivative formula, which terms are cancelled by adding the forward and backward Taylor expansions?**

    - A. The even-powered terms ($h^0, h^2, h^4, \dots$)
    - B. The odd-powered terms ($h, h^3, h^5, \dots$)
    - C. Only the second derivative term
    - D. All terms are doubled

    ??? info "See Answer"
        **Correct: B**

        *(The odd derivative terms have opposite signs in the two expansions ($+hf'(x)$ and $-hf'(x)$), so they cancel when added, leaving only the even derivative terms.)*

---

!!! note "Quiz"
    **20. The minimum error achievable for the Central Difference first derivative is approximately proportional to:**

    - A. $\epsilon_m$
    - B. $\sqrt{\epsilon_m}$
    - C. $\epsilon_m^{1/3}$
    - D. $\epsilon_m^{2/3}$

    ??? info "See Answer"
        **Correct: D**

        *(By substituting $h_{opt} \sim \epsilon_m^{1/3}$ back into the total error formula, the minimum error is found to scale as $(\epsilon_m^{1/3})^2 \sim \epsilon_m^{2/3}$, which is approximately $10^{-11}$ for double precision.)*

---

!!! note "Quiz"
    **21. What is the primary disadvantage of the Forward Difference method compared to the Central Difference method?**

    - A. It is harder to program.
    - B. It requires more memory.
    - C. It has a slower rate of convergence ($O(h)$ vs $O(h^2)$).
    - D. It is more susceptible to overflow errors.

    ??? info "See Answer"
        **Correct: C**

        *(Its first-order accuracy means it requires a much finer grid (and thus more computation) to achieve the same level of accuracy as the second-order Central Difference method.)*

---

!!! note "Quiz"
    **22. A "stencil" in the context of numerical differentiation refers to:**

    - A. A type of error analysis plot.
    - B. The geometric pattern of grid points and weights used to approximate a derivative.
    - C. A method for choosing the optimal step size $h$.
    - D. The analytical formula for a derivative.

    ??? info "See Answer"
        **Correct: B**

        *(For example, the second derivative uses a three-point stencil with weights $[+1, -2, +1]$ applied to the grid values $[f(x-h), f(x), f(x+h)]$.)*

---

!!! note "Quiz"
    **23. The equilibrium separation distance between two atoms in the Lennard-Jones potential occurs where:**

    - A. The potential energy $V(r)$ is zero.
    - B. The potential energy $V(r)$ is at its minimum.
    - C. The potential energy $V(r)$ is at its maximum.
    - D. The force $F(r)$ is at its maximum.

    ??? info "See Answer"
        **Correct: B**

        *(Equilibrium is the point of zero force, which corresponds to an extremum in the potential energy. For a stable bond, this is the minimum of the potential well.)*

---

!!! note "Quiz"
    **24. If a numerical method is described as "second-order accurate," it means its truncation error $E_{trunc}$ is proportional to:**

    - A. $h$
    - B. $h^2$
    - C. $1/h$
    - D. $1/h^2$

    ??? info "See Answer"
        **Correct: B**

        *(The "order" of a method refers to the power of $h$ in its leading truncation error term. Second-order means the error scales with $h^2$.)*

---

!!! note "Quiz"
    **25. Why is it a bad idea to choose a step size $h$ that is smaller than the optimal "sweet spot" value?**

    - A. The calculation becomes too slow.
    - B. The truncation error becomes unacceptably large.
    - C. The round-off error, amplified by catastrophic cancellation, begins to dominate and corrupts the result.
    - D. The program is more likely to crash due to memory limits.

    ??? info "See Answer"
        **Correct: C**

        *(Moving left from the sweet spot on the V-plot means entering the round-off dominated region, where decreasing $h$ actually increases the total error, making the result less accurate.)*
