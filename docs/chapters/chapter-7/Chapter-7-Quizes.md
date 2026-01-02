
# **Chapter-7: Quizes**

---

!!! note "Quiz"
    **1. What is the central goal of solving an Initial Value Problem (IVP) in physics?**

    - A. To find the roots of a polynomial equation.
    - B. To calculate the area under a curve from discrete data points.
    - C. To predict a system's entire future trajectory given its initial state and the rules of its evolution.
    - D. To determine the final, static equilibrium state of a system.

    ??? info "See Answer"
        **Correct: C**

        *(An IVP is about simulating dynamics. It combines the "rules of change" (the differential equation, $\frac{dx}{dt} = f(x,t)$) and a starting point ($x(t_0)$) to "march forward in time" and compute the system's state at all future times.)*

---

!!! note "Quiz"
    **2. What is the defining characteristic of Euler's Method for solving ODEs?**

    - A. It uses a weighted average of four slope estimates.
    - B. It assumes the derivative (slope) is constant across the entire time step.
    - C. It is a fourth-order accurate method.
    - D. It perfectly conserves energy in all simulations.

    ??? info "See Answer"
        **Correct: B**

        *(Euler's method is the "straight-line" method. It calculates the slope once at the beginning of the step and takes a single step forward assuming that slope doesn't change, which is the source of its inaccuracy and instability.)*

---

!!! note "Quiz"
    **3. What is the global error order of Euler's Method, and what does it imply?**

    - A. $O(h^4)$, meaning it is highly accurate.
    - B. $O(h^2)$, meaning halving the step size reduces the error by a factor of 4.
    - C. $O(h)$, meaning halving the step size only halves the total error.
    - D. $O(1)$, meaning the error does not depend on step size.

    ??? info "See Answer"
        **Correct: C**

        *(Euler's method is a first-order method with global error $O(h)$. This slow convergence makes it very inefficient for achieving high accuracy.)*

---

!!! note "Quiz"
    **4. When simulating a conservative system like an undamped harmonic oscillator, what is the fatal flaw of Euler's Method?**

    - A. It systematically removes energy, causing the oscillation to decay.
    - B. It is computationally too expensive.
    - C. It systematically injects energy, causing the oscillation's amplitude to grow exponentially.
    - D. It cannot handle second-order differential equations.

    ??? info "See Answer"
        **Correct: C**

        *(For oscillatory systems, Euler's method is unconditionally unstable. At each step, it slightly "overshoots" the true circular path in phase space, leading to a spiraling-out trajectory and a non-physical, geometric growth in total energy.)*

---

!!! note "Quiz"
    **5. How do Runge-Kutta (RK) methods fundamentally improve upon Euler's Method?**

    - A. By using a much smaller, fixed time step.
    - B. By intelligently sampling the derivative at multiple points within the time step to get a better average slope.
    - C. By using only integer arithmetic to avoid round-off error.
    - D. By solving the equation backwards in time.

    ??? info "See Answer"
        **Correct: B**

        *(Instead of assuming the slope is constant (Euler's flaw), RK methods take multiple "test" steps within the interval to sample the slope's curvature, then combine these samples in a weighted average to make a much more accurate final step.)*

---

!!! note "Quiz"
    **6. The second-order Runge-Kutta (RK2) method is also known as the Midpoint Method because it:**

    - A. Uses the average of the start and end points.
    - B. Takes a half-step to estimate the state at the midpoint, then uses the slope at that midpoint for the full step.
    - C. Is only accurate for the middle 50% of the simulation.
    - D. Calculates the median of all possible slopes.

    ??? info "See Answer"
        **Correct: B**

        *(RK2 is a simple predictor-corrector method. It "predicts" the midpoint state with an Euler step, then "corrects" the final step using the more accurate slope calculated at that midpoint.)*

---

!!! note "Quiz"
    **7. What is the global error order of the "gold standard" RK4 method?**

    - A. $O(h)$
    - B. $O(h^2)$
    - C. $O(h^4)$
    - D. $O(h^5)$

    ??? info "See Answer"
        **Correct: C**

        *(RK4 is a fourth-order method, meaning its global error scales as $O(h^4)$. Halving the step size reduces the total error by a factor of $2^4 = 16$, making it extremely efficient for most problems.)*

---

!!! note "Quiz"
    **8. The final step of the RK4 method, $x_{n+1} = x_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)$, uses a weighted average of slopes that is mathematically analogous to which numerical integration rule?**

    - A. The Trapezoidal Rule
    - B. Simpson's Rule
    - C. Gaussian Quadrature
    - D. Monte Carlo Integration

    ??? info "See Answer"
        **Correct: B**

        *(The 1-2-2-1 weighting of the four slope estimates ($k_1, k_2, k_3, k_4$) is a direct parallel to the 1-4-1 weighting used in Simpson's rule for integrating a function over an interval, providing a similarly high order of accuracy.)*

---

!!! note "Quiz"
    **9. To solve a second-order ODE like Newton's Law ($x'' = F/m$) with an RK4 solver, what is the essential first step?**

    - A. Integrate the equation twice analytically.
    - B. Convert the single second-order ODE into a system of two coupled first-order ODEs.
    - C. Differentiate the equation to make it third-order.
    - D. Approximate the force F as a constant.

    ??? info "See Answer"
        **Correct: B**

        *(RK solvers are designed for first-order equations of the form $\frac{d\mathbf{S}}{dt} = f(t, \mathbf{S})$. By defining a state vector $\mathbf{S} = [x, v]$, where $v=x'$, the second-order equation becomes two first-order equations: $x' = v$ and $v' = F/m$.)*

---

!!! note "Quiz"
    **10. For a 2D projectile motion problem with position $(x, y)$, what would the 4-element state vector $\mathbf{S}$ be?**

    - A. $[x, y, a_x, a_y]$
    - B. $[x, v_x, y, v_y]$
    - C. $[x, y, v_x, v_y]$
    - D. $[F_x, F_y, a_x, a_y]$

    ??? info "See Answer"
        **Correct: C**

        *(The state vector must contain all the information needed to describe the system's state at one instant. For mechanics, this is typically the positions and velocities of all degrees of freedom. The standard convention is to list positions first, then velocities: $[x, y, v_x, v_y]$.)*

---

!!! note "Quiz"
    **11. What is the primary goal of adaptive step-size control in an ODE solver?**

    - A. To keep the step size $h$ as large as possible to finish quickly.
    - B. To dynamically adjust the step size $h$ to maintain a desired level of accuracy while maximizing efficiency.
    - C. To make the step size $h$ as small as possible to ensure perfect accuracy.
    - D. To ensure the total energy of the system is always increasing.

    ??? info "See Answer"
        **Correct: B**

        *(Adaptive control is about efficiency. It takes small steps when the solution is changing rapidly (to maintain accuracy) and large steps when the solution is smooth (to save computation time), all while keeping the local error below a set tolerance.)*

---

!!! note "Quiz"
    **12. How do adaptive solvers like RK45 typically estimate the local truncation error at each step?**

    - A. By asking the user to input the expected error.
    - B. By comparing the result of the current step to the result of the previous step.
    - C. By calculating the step with two different methods (e.g., a 4th-order and 5th-order method) and measuring the difference.
    - D. By measuring the computer's CPU temperature.

    ??? info "See Answer"
        **Correct: C**

        *(Embedded Runge-Kutta methods, like RK45, are designed to compute two different-order solutions simultaneously with minimal extra effort. The difference between these two solutions provides a reliable estimate of the local error.)*

---

!!! note "Quiz"
    **13. In an adaptive solver, what happens if the estimated local error $E$ is greater than the tolerance `tol`?**

    - A. The step is accepted, and the step size $h$ is increased.
    - B. The step is accepted, but a warning is printed.
    - C. The step is rejected, the step size $h$ is decreased, and the step is re-computed.
    - D. The simulation immediately halts.

    ??? info "See Answer"
        **Correct: C**

        *(If the error is too large, the step is deemed inaccurate and is thrown away. The algorithm reduces the step size to improve accuracy and attempts the step again from the same starting point.)*

---

!!! note "Quiz"
    **14. In the context of adaptive solvers, what is the difference between `rtol` (relative tolerance) and `atol` (absolute tolerance)?**

    - A. `rtol` is for Runge-Kutta and `atol` is for Euler.
    - B. `rtol` controls error when the solution is large, while `atol` controls error when the solution is near zero.
    - C. `rtol` is specified in radians, `atol` is specified in atoms.
    - D. There is no difference; they are synonyms.

    ??? info "See Answer"
        **Correct: B**

        *(The total tolerance is often `atol + rtol * |x|`. `atol` provides a floor for the error, which is important when the solution `x` is close to zero. `rtol` scales the error with the magnitude of the solution, maintaining a constant relative precision.)*

---

!!! note "Quiz"
    **15. When simulating projectile motion with quadratic air resistance ($\mathbf{F}_d \propto -|\mathbf{v}|\mathbf{v}$), the resulting system of ODEs is:**

    - A. Linear and uncoupled.
    - B. Linear and coupled.
    - C. Nonlinear and uncoupled.
    - D. Nonlinear and coupled.

    ??? info "See Answer"
        **Correct: D**

        *(The drag force depends on the magnitude of the velocity ($|\mathbf{v}| = \sqrt{v_x^2 + v_y^2}$), which makes the equations for $a_x$ and $a_y$ both nonlinear and coupled (the acceleration in x depends on $v_y$, and vice-versa).)*

---

!!! note "Quiz"
    **16. A key physical phenomenon observed in projectile motion with drag, which cannot be seen in the ideal case, is:**

    - A. The trajectory is a perfect, symmetric parabola.
    - B. The object accelerates indefinitely.
    - C. The vertical velocity asymptotically approaches a constant terminal velocity.
    - D. The total mechanical energy is conserved.

    ??? info "See Answer"
        **Correct: C**

        *(As the object falls, the drag force increases with speed until it exactly balances the force of gravity. At this point, the net force is zero, acceleration ceases, and the object falls at a constant terminal velocity.)*

---

!!! note "Quiz"
    **17. If you are writing the derivative function `f(t, S)` for the state vector $\mathbf{S} = [x, y, v_x, v_y]$, what must this function return?**

    - A. The state vector $\mathbf{S}$ itself.
    - B. The derivative of the state vector, $\frac{d\mathbf{S}}{dt} = [v_x, v_y, a_x, a_y]$.
    - C. The total energy of the system.
    - D. The time step $h$.

    ??? info "See Answer"
        **Correct: B**

        *(The job of the derivative function is to tell the solver the "rules of change." For a given state $\mathbf{S}$, it must compute and return the time derivative of each component of $\mathbf{S}$.)*

---

!!! note "Quiz"
    **18. What is the primary limitation of the RK4 method, which motivates the need for the methods in Chapter 8?**

    - A. It is only first-order accurate.
    - B. It is unconditionally unstable for all problems.
    - C. It cannot handle coupled systems of ODEs.
    - D. It does not perfectly conserve energy in long-term simulations of conservative systems.

    ??? info "See Answer"
        **Correct: D**

        *(While highly accurate in the short term, RK4 is not a "symplectic" integrator. In long-term simulations of Hamiltonian systems (like planetary orbits), it will exhibit a slow, systematic energy drift that eventually makes the simulation unphysical.)*

---

!!! note "Quiz"
    **19. The RK2 (Midpoint) method has a global error of $O(h^2)$. If you reduce the step size by a factor of 10, the total error will decrease by approximately what factor?**

    - A. 10
    - B. 20
    - C. 100
    - D. 1000

    ??? info "See Answer"
        **Correct: C**

        *(For an $O(h^2)$ method, the error scales with the square of the step size. Reducing $h$ by a factor of 10 reduces the error by a factor of $10^2 = 100$.)*

---

!!! note "Quiz"
    **20. The "state vector" $\mathbf{S}$ in the context of solving ODEs represents:**

    - A. The complete set of parameters needed to define the system's state at a single instant in time.
    - B. The list of all time steps taken by the solver.
    - C. The final equilibrium state of the system.
    - D. A vector of all the errors in the simulation.

    ??? info "See Answer"
        **Correct: A**

        *(The state vector is the "DNA" of the system at a moment in time. For a mechanical system, this is typically all the positions and all the velocities.)*

---

!!! note "Quiz"
    **21. Why is RK4 considered the "gold standard" or default integrator for many scientific problems?**

    - A. It is the only method that is perfectly stable.
    - B. It provides the best balance of high accuracy ($O(h^4)$) for a reasonable amount of computational effort (4 function calls per step).
    - C. It was invented by the most famous mathematician.
    - D. It is the only method that can be used with adaptive step-sizing.

    ??? info "See Answer"
        **Correct: B**

        *(RK4 hits a "sweet spot." It is dramatically more accurate than lower-order methods, but higher-order methods (like RK8) offer diminishing returns in accuracy for their increased complexity and computational cost.)*

---

!!! note "Quiz"
    **22. In the RK4 formula, the four slope estimates are $k_1, k_2, k_3, k_4$. Which slope is calculated using a full Euler step from the beginning of the interval?**

    - A. $k_1$
    - B. $k_2$
    - C. $k_3$
    - D. $k_4$

    ??? info "See Answer"
        **Correct: D**

        *(The formula for $k_4$ is $h \cdot f(x_n + k_3, t_n + h)$. It estimates the slope at the *end* of the interval ($t_n+h$) using a position predicted by the third slope estimate, $k_3$.)*

---

!!! note "Quiz"
    **23. The trajectory of a projectile with air drag is asymmetric. Specifically, the descent is:**

    - A. Steeper than the ascent.
    - B. Less steep than the ascent.
    - C. Identical to the ascent.
    - D. A straight vertical line.

    ??? info "See Answer"
        **Correct: A**

        *(The projectile loses horizontal velocity throughout its flight due to drag. It covers less horizontal distance during the second half of its flight (descent) than the first half (ascent), making the descent path steeper.)*

---

!!! note "Quiz"
    **24. A simulation of a simple harmonic oscillator using Euler's method shows the amplitude of oscillation growing over time. This is a numerical artifact indicating:**

    - A. The method is accurately capturing a physical resonance.
    - B. The method is unstable and is artificially adding energy to the system.
    - C. The time step $h$ is too small.
    - D. The system is experiencing physical damping.

    ??? info "See Answer"
        **Correct: B**

        *(For a conservative system like the SHO, energy should be constant. The growing amplitude is a classic sign of the instability of Euler's method, which systematically overshoots the true trajectory and adds energy.)*

---

!!! note "Quiz"
    **25. The transition from Chapter 7 to Chapter 8 is motivated by the need for what specific property in long-term orbital mechanics simulations?**

    - A. Higher short-term accuracy than RK4.
    - B. The ability to handle "stiff" differential equations.
    - C. Perfect, long-term conservation of energy and other invariants of motion.
    - D. A method that is simpler to program than Euler's method.

    ??? info "See Answer"
        **Correct: C**

        *(While RK4 is very accurate, its small energy drift is unacceptable for simulations over thousands of orbits. Chapter 8 introduces symplectic integrators (like Verlet/Leapfrog) which are designed specifically to conserve energy over very long time scales, even if their per-step accuracy is lower than RK4.)*
