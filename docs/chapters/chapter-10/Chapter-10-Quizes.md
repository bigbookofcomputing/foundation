
# **Chapter-10: Quizes**

---

!!! note "Quiz"
    **1. Elliptic Partial Differential Equations (PDEs), like Laplace's Equation, are used to model what kind of physical systems?**

    - A. Systems that are evolving rapidly in time.
    - B. Systems that are propagating as waves.
    - C. Systems that have reached a static, steady-state equilibrium.
    - D. Systems that are purely one-dimensional.

    ??? info "See Answer"
        **Correct: C**

        *(Elliptic PDEs are pure Boundary Value Problems. They describe fields (like temperature or electrostatic potential) that are no longer changing with time ($\partial/\partial t = 0$) and whose shape is determined entirely by the fixed conditions on the boundaries.)*

---

!!! note "Quiz"
    **2. What is the mathematical representation of Laplace's Equation?**

    - A. $\nabla^2 \phi = \rho$
    - B. $\frac{\partial \phi}{\partial t} = D \nabla^2 \phi$
    - C. $\nabla^2 \phi = 0$
    - D. $\frac{\partial^2 \phi}{\partial t^2} = c^2 \nabla^2 \phi$

    ??? info "See Answer"
        **Correct: C**

        *(Laplace's Equation, $\nabla^2 \phi = 0$, describes a field in a source-free region at equilibrium. Poisson's Equation, $\nabla^2 \phi = \rho$, describes a field with a fixed source density $\rho$.)*

---

!!! note "Quiz"
    **3. The Finite Difference Method (FDM) for the 2D Laplacian operator ($\nabla^2$) results in the "Five-Point Stencil." What is the physical interpretation of this rule for Laplace's Equation?**

    - A. The potential at a point is the sum of its four neighbors.
    - B. The potential at a point is the product of its four neighbors.
    - C. The potential at a point is the average of the potentials of its four immediate neighbors.
    - D. The potential at a point is always zero.

    ??? info "See Answer"
        **Correct: C**

        *(The stencil $\phi_{i,j} = \frac{1}{4}(\phi_{i+1,j} + \phi_{i-1,j} + \phi_{i,j+1} + \phi_{i,j-1})$ is the mathematical definition of equilibrium. If a point is not the average of its surroundings, there would be a non-zero curvature ($\nabla^2 \phi \neq 0$), implying a source or sink.)*

---

!!! note "Quiz"
    **4. The iterative process of solving the FDM system for elliptic PDEs is known as "relaxation." What is the physical analogy for this process?**

    - A. A ball rolling down a hill.
    - B. A wave propagating across a pond.
    - C. A taut rubber sheet, pinned at the edges, settling into its final, stable shape.
    - D. A planet orbiting a star.

    ??? info "See Answer"
        **Correct: C**

        *(The iterative updates are like the vibrations in a perturbed rubber sheet slowly damping out until it reaches the smoothest possible configuration allowed by the fixed boundary "pins.")*

---

!!! note "Quiz"
    **5. What is the key difference between the Jacobi method and the Gauss-Seidel method for relaxation?**

    - A. Jacobi is faster than Gauss-Seidel.
    - B. Jacobi requires one grid, while Gauss-Seidel requires two.
    - C. Jacobi updates synchronously (using only old values), while Gauss-Seidel updates sequentially (using new values immediately).
    - D. Jacobi is for 3D problems, while Gauss-Seidel is for 2D problems.

    ??? info "See Answer"
        **Correct: C**

        *(Jacobi calculates all new points based on the grid from the previous iteration. Gauss-Seidel uses the newly computed values from the current iteration as soon as they are available, which accelerates the propagation of information.)*

---

!!! note "Quiz"
    **6. Why does the Gauss-Seidel method typically converge about twice as fast as the Jacobi method?**

    - A. It uses a higher-order stencil.
    - B. It uses a smaller time step.
    - C. It allows new information from the boundaries to propagate across the grid more quickly within a single iteration.
    - D. It is inherently parallelizable.

    ??? info "See Answer"
        **Correct: C**

        *(By using updated values immediately, the influence of the boundaries spreads faster. In a standard sweep, information from the left and bottom boundaries can influence the top-right corner in a single pass, whereas in Jacobi it would take many iterations.)*

---

!!! note "Quiz"
    **7. The Successive Over-Relaxation (SOR) method accelerates convergence by introducing an over-relaxation factor, $\omega$. What is the purpose of this factor?**

    - A. To ensure the solution remains stable by damping the updates ($\omega < 1$).
    - B. To intentionally "overshoot" the Gauss-Seidel estimate, helping the solution "settle" into equilibrium much faster.
    - C. To reduce the memory required by the algorithm.
    - D. To increase the accuracy of the five-point stencil.

    ??? info "See Answer"
        **Correct: B**

        *(For $1 < \omega < 2$, SOR pushes the update past the simple average value. This "over-correction" helps to more rapidly damp out the high-frequency errors in the initial guess, leading to dramatically faster convergence.)*

---

!!! note "Quiz"
    **8. What is the valid range for the over-relaxation factor $\omega$ in the SOR method for it to be stable and effective?**

    - A. $0 < \omega < 1$
    - B. $1 < \omega < 2$
    - C. $\omega > 2$
    - D. $\omega$ can be any real number.

    ??? info "See Answer"
        **Correct: B**

        *(If $\omega \le 1$, the method is under-relaxed and converges slowly (or is just Gauss-Seidel if $\omega=1$). If $\omega \ge 2$, the method becomes unstable and will not converge.)*

---

!!! note "Quiz"
    **9. In the context of solving the FDM system, what are the Jacobi, Gauss-Seidel, and SOR methods actually doing from a linear algebra perspective?**

    - A. They are methods for calculating the determinant of the FDM matrix.
    - B. They are iterative methods for solving the large, sparse system of linear equations $\mathbf{A}\mathbf{x} = \mathbf{b}$.
    - C. They are methods for finding the eigenvalues of the FDM matrix.
    - D. They are methods for inverting the FDM matrix.

    ??? info "See Answer"
        **Correct: B**

        *(The FDM converts the PDE into a massive system of linear equations. Direct solvers like Gaussian elimination are too slow ($\mathcal{O}(N^3)$). The relaxation methods are efficient iterative techniques designed to find the solution vector $\mathbf{x}$ for this specific type of sparse system.)*

---

!!! note "Quiz"
    **10. When visualizing the solution to the electrostatic box problem, what is the physical relationship between the equipotential contour lines and the electric field $\mathbf{E}$?**

    - A. The electric field is parallel to the equipotential lines.
    - B. The electric field is always perpendicular to the equipotential lines.
    - C. The electric field points towards the highest potential.
    - D. The electric field is zero everywhere along the equipotential lines.

    ??? info "See Answer"
        **Correct: B**

        *(The electric field is defined as the negative gradient of the potential, $\mathbf{E} = -\nabla\phi$. The gradient is always perpendicular to the level sets (contour lines) of a function, pointing in the direction of steepest ascent. Therefore, $\mathbf{E}$ points "downhill," perpendicular to the lines of constant potential.)*

---

!!! note "Quiz"
    **11. Which of the three relaxation methods is most suitable for implementation on a parallel computing architecture (like a GPU)?**

    - A. Gauss-Seidel, because it is the fastest.
    - B. SOR, because it requires the fewest iterations.
    - C. Jacobi, because the update for each point depends only on old values, allowing all points to be calculated independently and simultaneously.
    - D. None of them can be parallelized.

    ??? info "See Answer"
        **Correct: C**

        *(The synchronous nature of the Jacobi update (requiring two grids) means there are no data dependencies between the calculations for different points within a single iteration. This makes it trivial to parallelize, even though it converges slowly.)*

---

!!! note "Quiz"
    **12. The convergence of an iterative relaxation method is typically checked by:**

    - A. Running for a fixed number of iterations.
    - B. Measuring the total energy of the system.
    - C. Calculating the maximum change (residual) in potential at any grid point between one iteration and the next, and stopping when it's below a tolerance.
    - D. Comparing the numerical solution to a known analytical solution.

    ??? info "See Answer"
        **Correct: C**

        *(The algorithm is considered to have "relaxed" or converged when the updates become negligibly small. This is quantified by tracking the maximum absolute difference between `phi_new` and `phi_old` across the entire grid.)*

---

!!! note "Quiz"
    **13. What is the primary difference between Laplace's Equation ($\nabla^2 \phi = 0$) and Poisson's Equation ($\nabla^2 \phi = \rho$)?**

    - A. Laplace's equation is for 2D, while Poisson's is for 3D.
    - B. Laplace's equation describes a source-free region, while Poisson's equation includes a source term $\rho$ (like charge density).
    - C. Laplace's equation is linear, while Poisson's is nonlinear.
    - D. Laplace's equation is time-dependent, while Poisson's is static.

    ??? info "See Answer"
        **Correct: B**

        *(The right-hand side of the equation represents sources or sinks. A zero on the right-hand side (Laplace) means the field is at equilibrium with no sources present in the domain. A non-zero term (Poisson) means the field is influenced by a fixed source distribution.)*

---

!!! note "Quiz"
    **14. If you use the Gauss-Seidel method, why do you only need one copy of the potential grid in memory (as opposed to two for Jacobi)?**

    - A. Because it converges in a single iteration.
    - B. Because the updates are performed "in-place," overwriting the old values as the sweep progresses.
    - C. Because it uses a different, more compact stencil.
    - D. Because it is less accurate and doesn't need to store old values.

    ??? info "See Answer"
        **Correct: B**

        *(The sequential nature of Gauss-Seidel means that as soon as `phi[i,j]` is calculated, the old value is no longer needed for subsequent calculations in that sweep. This "in-place" update reduces the memory footprint by half compared to Jacobi.)*

---

!!! note "Quiz"
    **15. The five-point stencil for the 2D Laplacian has a local truncation error of what order?**

    - A. $\mathcal{O}(h)$
    - B. $\mathcal{O}(h^2)$
    - C. $\mathcal{O}(h^3)$
    - D. $\mathcal{O}(h^4)$

    ??? info "See Answer"
        **Correct: B**

        *(This is because it is derived from the central difference formula for the second derivative, which is itself $\mathcal{O}(h^2)$ accurate.)*

---

!!! note "Quiz"
    **16. In the SOR update rule, $\phi_{new} = (1-\omega)\phi_{old} + \omega\phi_{GS}$, what does the term $\phi_{GS}$ represent?**

    - A. The value from the Jacobi iteration.
    - B. The value that would have been calculated using the standard Gauss-Seidel method.
    - C. The value from the previous time step.
    - D. The boundary condition value.

    ??? info "See Answer"
        **Correct: B**

        *(SOR is a direct acceleration of Gauss-Seidel. It first calculates the normal Gauss-Seidel update and then "pushes" the solution further in that direction by the factor $\omega$.)*

---

!!! note "Quiz"
    **17. A plot of the maximum residual versus iteration number for a converging relaxation method will typically show what shape on a log-linear scale?**

    - A. A parabola.
    - B. A sine wave.
    - C. A nearly straight line with a negative slope.
    - D. A horizontal line.

    ??? info "See Answer"
        **Correct: C**

        *(This indicates that the error is decreasing exponentially with each iteration, which is the hallmark of a linearly convergent iterative method.)*

---

!!! note "Quiz"
    **18. This chapter on elliptic PDEs serves as a bridge to the next chapter on parabolic PDEs. What is the key feature that parabolic PDEs (like the heat equation) re-introduce?**

    - A. A non-zero source term.
    - B. A first-order time derivative ($\partial/\partial t$).
    - C. A second-order time derivative ($\partial^2/\partial t^2$).
    - D. A third spatial dimension.

    ??? info "See Answer"
        **Correct: B**

        *(Parabolic PDEs describe diffusion and other time-dependent relaxation processes. They couple the spatial Laplacian ($\nabla^2 \phi$) from this chapter with a time-evolution term, $\partial \phi / \partial t$.)*

---

!!! note "Quiz"
    **19. If you set the over-relaxation factor $\omega = 1$ in the SOR method, what method do you get?**

    - A. The Jacobi method.
    - B. The Gauss-Seidel method.
    - C. The Euler method.
    - D. The method becomes unstable.

    ??? info "See Answer"
        **Correct: B**

        *(Setting $\omega=1$ in the SOR formula, $\phi_{new} = (1-1)\phi_{old} + 1\cdot\phi_{GS}$, simplifies it to $\phi_{new} = \phi_{GS}$. This shows that Gauss-Seidel is just a special case of SOR with no over-relaxation.)*

---

!!! note "Quiz"
    **20. For a fixed grid size, which method would you choose to get the fastest convergence for solving Laplace's equation on a single-processor computer?**

    - A. Jacobi
    - B. Gauss-Seidel
    - C. Successive Over-Relaxation (SOR) with an optimal $\omega$.
    - D. A direct matrix solver.

    ??? info "See Answer"
        **Correct: C**

        *(For serial computation, SOR with a well-tuned $\omega$ is significantly faster than both Jacobi and Gauss-Seidel, often reducing the number of iterations by an order of magnitude.)*

---

!!! note "Quiz"
    **21. The "Dirichlet boundary condition" used in the electrostatic box problem specifies what?**

    - A. The value of the derivative of the potential on the boundary.
    - B. The value of the potential itself on the boundary.
    - C. The potential is zero on the boundary.
    - D. The boundary is periodic.

    ??? info "See Answer"
        **Correct: B**

        *(Dirichlet boundary conditions mean the value of the function (e.g., potential $\phi$) is fixed at the boundary. Neumann boundary conditions, by contrast, specify the value of the normal derivative on the boundary.)*

---

!!! note "Quiz"
    **22. How would the five-point stencil for Poisson's equation, $\nabla^2 \phi = \rho$, differ from the one for Laplace's equation?**

    - A. It would be identical.
    - B. The update rule would include the source term: $\phi_{i,j} = \frac{1}{4}(\dots) - \frac{h^2}{4}\rho_{i,j}$.
    - C. It would become a seven-point stencil.
    - D. It would involve time derivatives.

    ??? info "See Answer"
        **Correct: B**

        *(Discretizing $\nabla^2 \phi = \rho$ yields $\frac{1}{h^2}(\dots - 4\phi_{i,j}) = \rho_{i,j}$. Solving for $\phi_{i,j}$ moves the source term to the right-hand side, modifying the simple average rule.)*

---

!!! note "Quiz"
    **23. What is the main trade-off when choosing between the Jacobi and Gauss-Seidel methods?**

    - A. Accuracy vs. Speed.
    - B. Memory vs. Stability.
    - C. Simplicity of parallelization vs. Serial convergence speed.
    - D. 2D vs. 3D applicability.

    ??? info "See Answer"
        **Correct: C**

        *(Jacobi is slower but easy to parallelize because its updates are independent. Gauss-Seidel is faster on a single processor but harder to parallelize because of its sequential data dependencies.)*

---

!!! note "Quiz"
    **24. In the rubber sheet analogy, the final height of the sheet at any point corresponds to what in the electrostatic problem?**

    - A. The electric field.
    - B. The charge density.
    - C. The electrostatic potential ($\phi$).
    - D. The total energy.

    ??? info "See Answer"
        **Correct: C**

        *(The height of the sheet is analogous to the scalar potential $\phi$. The steepness (gradient) of the sheet would be analogous to the electric field $\mathbf{E}$.)*

---

!!! note "Quiz"
    **25. The methods in this chapter are "iterative." What does this mean?**

    - A. The solution is found in a single, direct calculation.
    - B. The methods involve repeatedly applying an update rule to refine an initial guess until the solution converges.
    - C. The methods only work for problems that are periodic in nature.
    - D. The methods are a form of recursion.

    ??? info "See Answer"
        **Correct: B**

        *(Unlike a direct solver that computes the answer in one go, iterative methods start with a guess and progressively improve it in a loop until the change between iterations is negligible.)*
