
!!! note "Quiz"

    ??? question "1. The Heat Equation, $\frac{\partial T}{\partial t} = D \nabla^2 T$, is the classic example of what type of Partial Differential Equation?"
        - a) Elliptic PDE
        - b) Hyperbolic PDE
        - c) **Parabolic PDE**
        - d) Integral Equation

        ??? info "See Answer"
            **c) Parabolic PDE**. Parabolic PDEs, like the Heat/Diffusion Equation, are characterized by a first-order derivative in time and a second-order derivative in space, governing time-evolving, dissipative systems.

    ??? question "2. The Forward-Time Centered-Space (FTCS) method for the 1D Heat Equation is constructed by combining a Forward Difference in time with what stencil for the spatial derivative?"
        - a) A Forward Difference in space
        - b) A Backward Difference in space
        - c) **A Central Difference in space**
        - d) A five-point stencil in space

        ??? info "See Answer"
            **c) A Central Difference in space**. The FTCS scheme uses an $\mathcal{O}(h_t)$ Forward Difference for the time derivative and a more accurate $\mathcal{O}(h_x^2)$ Central Difference for the spatial second derivative.

    ??? question "3. In the context of the FTCS method, what is the definition of the dimensionless Diffusion Number, $\alpha$?"
        - a) $\alpha = D \frac{h_x^2}{h_t}$
        - b) **$\alpha = D \frac{h_t}{h_x^2}$**
        - c) $\alpha = D h_t$
        - d) $\alpha = \frac{D}{h_x^2}$

        ??? info "See Answer"
            **b) $\alpha = D \frac{h_t}{h_x^2}$**. The diffusion number $\alpha$ is a crucial parameter that relates the thermal diffusivity, the time step, and the square of the spatial step. It governs the stability of the explicit FTCS method.

    ??? question "4. What is the strict Courant–Friedrichs–Lewy (CFL) stability condition for the explicit FTCS method when applied to the 1D Heat Equation?"
        - a) $\alpha > 1$
        - b) $\alpha \le 1$
        - c) **$\alpha \le 0.5$**
        - d) $\alpha$ can be any value

        ??? info "See Answer"
            **c) $\alpha \le 0.5$**. For the FTCS method to be stable, the diffusion number $\alpha$ must be less than or equal to 0.5. If $\alpha > 0.5$, numerical errors will be amplified at each time step, leading to a catastrophic explosion of the solution.

    ??? question "5. If you increase the spatial resolution of an FTCS simulation by a factor of 10 (i.e., $h_x \to h_x/10$), how must the time step $h_t$ change to maintain stability?"
        - a) It can remain the same.
        - b) It must decrease by a factor of 10.
        - c) **It must decrease by a factor of 100.**
        - d) It must increase by a factor of 100.

        ??? info "See Answer"
            **c) It must decrease by a factor of 100.** The stability condition $h_t \le \frac{0.5 \cdot h_x^2}{D}$ shows that the time step is proportional to the square of the spatial step. This "tyranny of $h^2$" makes the FTCS method extremely inefficient for high-resolution simulations.

    ??? question "6. Why are methods like BTCS (Backward-Time Centered-Space) and Crank-Nicolson classified as 'implicit'?"
        - a) They are less accurate than explicit methods.
        - b) They can only be used for steady-state problems.
        - c) **They create a system of equations where the unknown future state at a point is coupled to its unknown future neighbors.**
        - d) They calculate the future state directly from known present values.

        ??? info "See Answer"
            **c) They create a system of equations where the unknown future state at a point is coupled to its unknown future neighbors.** This implicit coupling means you cannot solve for any single point's future value in isolation; you must solve for the entire spatial grid simultaneously by solving a matrix system like $\mathbf{A} \mathbf{T}_{n+1} = \mathbf{b}$.

    ??? question "7. What is the primary advantage of implicit methods (like BTCS and Crank-Nicolson) over the explicit FTCS method?"
        - a) They are computationally cheaper per time step.
        - b) **They are unconditionally stable.**
        - c) They are easier to program.
        - d) They are fourth-order accurate in time.

        ??? info "See Answer"
            **b) They are unconditionally stable.** Their unconditional stability (A-stability) means you can choose a time step based on the desired accuracy of the simulation, not by a restrictive stability constraint, making them far more efficient for most problems.

    ??? question "8. The Crank-Nicolson method is considered the 'gold standard' for parabolic PDEs because it combines unconditional stability with what order of accuracy in time?"
        - a) $\mathcal{O}(h_t)$
        - b) **$\mathcal{O}(h_t^2)$**
        - c) $\mathcal{O}(h_t^3)$
        - d) $\mathcal{O}(h_t^4)$

        ??? info "See Answer"
            **b) $\mathcal{O}(h_t^2)$**. Crank-Nicolson achieves second-order accuracy in time, a significant improvement over the first-order accuracy of FTCS and BTCS, making it much more efficient for achieving a given level of precision.

    ??? question "9. How does the Crank-Nicolson method achieve its higher $\mathcal{O}(h_t^2)$ accuracy?"
        - a) By using a five-point stencil for the time derivative.
        - b) By using a very small time step.
        - c) **By averaging the spatial derivative (central difference stencil) between the present time ($n$) and the future time ($n+1$).**
        - d) By explicitly calculating the error at each step.

        ??? info "See Answer"
            **c) By averaging the spatial derivative (central difference stencil) between the present time ($n$) and the future time ($n+1$).** This centered-in-time approximation of the spatial derivative is analogous to the Trapezoidal Rule for integration, which gives it second-order accuracy.

    ??? question "10. When solving the Heat Equation with an implicit method like Crank-Nicolson, what is the characteristic structure of the matrix $\mathbf{A}$ in the system $\mathbf{A} \mathbf{T}_{n+1} = \mathbf{b}$ for a 1D problem?"
        - a) A dense, full matrix
        - b) A diagonal matrix
        - c) **A tridiagonal matrix**
        - d) A purely symmetric matrix

        ??? info "See Answer"
            **c) A tridiagonal matrix**. Because the finite difference stencil only couples a point `i` to its immediate neighbors `i-1` and `i+1`, the resulting matrix has non-zero elements only on the main diagonal, the sub-diagonal, and the super-diagonal.

    ??? question "11. What is the computational advantage of the matrix system being tridiagonal?"
        - a) It can be inverted in $\mathcal{O}(1)$ time.
        - b) **It can be solved very efficiently in $\mathcal{O}(N)$ time using specialized solvers like the Thomas Algorithm.**
        - c) It guarantees the solution will never oscillate.
        - d) It requires no boundary conditions.

        ??? info "See Answer"
            **b) It can be solved very efficiently in $\mathcal{O}(N)$ time using specialized solvers like the Thomas Algorithm.** This linear time complexity is vastly superior to the $\mathcal{O}(N^3)$ complexity of general solvers for dense matrices, making implicit methods computationally feasible.

    ??? question "12. In the 'quenched rod' simulation, the Crank-Nicolson method successfully produced a smooth solution even with a diffusion number $\alpha = 12.5$. What would happen to an FTCS simulation with this $\alpha$?"
        - a) It would run slowly but produce the correct result.
        - b) It would produce a result with minor, decaying oscillations.
        - c) **It would fail almost instantly, with solution values growing exponentially in a numerical explosion.**
        - d) It would converge to the wrong steady-state solution.

        ??? info "See Answer"
            **c) It would fail almost instantly, with solution values growing exponentially in a numerical explosion.** An $\alpha$ of 12.5 violates the FTCS stability condition ($\alpha \le 0.5$) by a factor of 25, guaranteeing catastrophic failure.

    ??? question "13. The time evolution of the Heat Equation eventually leads to a steady-state temperature profile. The PDE governing this final, static profile is:"
        - a) The Wave Equation ($\frac{\partial^2 T}{\partial t^2} = v^2 \nabla^2 T$)
        - b) **Laplace's Equation ($\nabla^2 T = 0$)**
        - c) The Advection Equation ($\frac{\partial T}{\partial t} + v \frac{\partial T}{\partial x} = 0$)
        - d) A simple Ordinary Differential Equation (ODE)

        ??? info "See Answer"
            **b) Laplace's Equation ($\nabla^2 T = 0$)**. Steady-state is defined by the condition that there is no more change in time, so $\frac{\partial T}{\partial t} = 0$. This reduces the Heat Equation to $D \nabla^2 T = 0$, which is Laplace's Equation (an Elliptic PDE, as covered in Chapter 10).

    ??? question "14. What is the fundamental trade-off when choosing between an explicit (FTCS) and an implicit (Crank-Nicolson) method?"
        - a) Accuracy vs. programming difficulty.
        - b) **A cheap but small (unstable) step vs. an expensive but large (stable) step.**
        - c) IVP vs. BVP.
        - d) Dirichlet vs. Neumann boundary conditions.

        ??? info "See Answer"
            **b) A cheap but small (unstable) step vs. an expensive but large (stable) step.** FTCS steps are computationally cheap (just arithmetic), but the CFL condition forces them to be tiny. Implicit steps are expensive (requiring a matrix solve), but their unconditional stability allows them to be enormous, making them far more efficient overall.

    ??? question "15. In the provided Python code for the Crank-Nicolson solver, which `scipy` function was used to efficiently solve the tridiagonal system?"
        - a) `scipy.linalg.inv`
        - b) `scipy.linalg.solve`
        - c) **`scipy.linalg.solve_banded`**
        - d) `scipy.optimize.fsolve`

        ??? info "See Answer"
            **c) `scipy.linalg.solve_banded`**. This function is optimized for banded matrices (like a tridiagonal matrix) and is much more efficient than a general-purpose solver like `solve` or explicitly inverting the matrix with `inv`.

    ??? question "16. The BTCS (Backward-Time Centered-Space) method is also unconditionally stable. Why is Crank-Nicolson generally preferred over BTCS?"
        - a) BTCS is an explicit method.
        - b) BTCS does not result in a tridiagonal matrix.
        - c) **BTCS is only first-order accurate in time ($\mathcal{O}(h_t)$), while Crank-Nicolson is second-order accurate ($\mathcal{O}(h_t^2)$).**
        - d) BTCS is harder to implement.

        ??? info "See Answer"
            **c) BTCS is only first-order accurate in time ($\mathcal{O}(h_t)$), while Crank-Nicolson is second-order accurate ($\mathcal{O}(h_t^2)$).** For a given computational effort, Crank-Nicolson will almost always yield a more accurate result due to its superior temporal accuracy.

    ??? question "17. A simulation of the Heat Equation using FTCS shows rapid, non-physical oscillations that grow in magnitude. What is the most likely cause?"
        - a) The initial condition was not smooth.
        - b) The thermal diffusivity `D` is too high.
        - c) **The time step `h_t` is too large for the given spatial step `h_x`, violating the CFL condition.**
        - d) A programming error in the boundary conditions.

        ??? info "See Answer"
            **c) The time step `h_t` is too large for the given spatial step `h_x`, violating the CFL condition.** This is the classic signature of numerical instability in the FTCS method. The correct fix is to decrease `h_t` such that $\alpha \le 0.5$.

    ??? question "18. In the Crank-Nicolson matrix system $\mathbf{A} \mathbf{T}_{n+1} = \mathbf{b}$, the vector $\mathbf{b}$ on the right-hand side depends on:"
        - a) Only the boundary conditions.
        - b) **The known temperature distribution at the present time, $T_n$.**
        - c) The unknown temperature distribution at the future time, $T_{n+1}$.
        - d) A constant vector that is calculated only once.

        ??? info "See Answer"
            **b) The known temperature distribution at the present time, $T_n$.** The RHS vector $\mathbf{b}$ must be re-calculated at every time step because it is constructed from the results of the previous step.

    ??? question "19. The Heat Equation is a 'hybrid' problem because it must be treated as:"
        - a) A linear and non-linear problem simultaneously.
        - b) A 1D and 2D problem simultaneously.
        - c) **An Initial Value Problem (IVP) in time and a Boundary Value Problem (BVP) in space.**
        - d) A diffusion and a wave problem simultaneously.

        ??? info "See Answer"
            **c) An Initial Value Problem (IVP) in time and a Boundary Value Problem (BVP) in space.** It requires an initial temperature distribution $T(x, t=0)$ to start the time-marching (IVP), and boundary conditions like $T(0, t)$ and $T(L, t)$ to constrain the spatial grid (BVP).

    ??? question "20. What physical quantity is 'diffusing' in the Black-Scholes equation, making it mathematically analogous to the Heat Equation?"
        - a) Money
        - b) Stock price
        - c) **Risk or option value**
        - d) Interest rates

        ??? info "See Answer"
            **c) Risk or option value**. The Black-Scholes equation models how the value of an option and its associated risk diffuse or spread out over time due to random market fluctuations, which are modeled with the same mathematical structure as the random motion of particles causing heat diffusion.

    ??? question "21. If you implement a Neumann boundary condition (e.g., an insulated end where $\frac{\partial T}{\partial x} = 0$), how does this affect the numerical solution?"
        - a) It makes the FTCS method unconditionally stable.
        - b) **It requires modifying the matrix equations (or stencil updates) at the boundary points.**
        - c) It forces the temperature at the boundary to be zero.
        - d) It can only be handled by explicit methods.

        ??? info "See Answer"
            **b) It requires modifying the matrix equations (or stencil updates) at the boundary points.** A Neumann condition is a condition on the derivative, which must be approximated using finite differences (e.g., by introducing a 'ghost point'), thus changing the equation for the boundary grid point.

    ??? question "22. The FTCS update rule is $T_{i, n+1} = T_{i, n} + \alpha ( T_{i+1, n} - 2T_{i, n} + T_{i-1, n} )$. This is considered an 'explicit' rule because:"
        - a) It explicitly states the stability condition.
        - b) **$T_{i, n+1}$ is calculated using only known values from time level $n$.**
        - c) It is explicitly written in the textbook.
        - d) It requires an explicit matrix inversion.

        ??? info "See Answer"
            **b) $T_{i, n+1}$ is calculated using only known values from time level $n$.** No system of equations is needed; the future value is found directly by arithmetic operations on present values.

    ??? question "23. After solving the Heat Equation for a long period, the temperature profile stops changing. At this point, the time derivative $\frac{\partial T}{\partial t}$ is effectively zero. This implies that the solution to the Parabolic PDE has converged to the solution of:"
        - a) A Hyperbolic PDE
        - b) **An Elliptic PDE (Laplace's Equation)**
        - c) An ODE
        - d) An advection equation

        ??? info "See Answer"
            **b) An Elliptic PDE (Laplace's Equation)**. When $\frac{\partial T}{\partial t} = 0$, the Heat Equation $\frac{\partial T}{\partial t} = D \nabla^2 T$ simplifies to $\nabla^2 T = 0$, which is the definition of Laplace's Equation.

    ??? question "24. In the Python code for the FTCS stability test, the unstable case with $\alpha=0.75$ produced a plot with:"
        - a) A smooth curve that decayed too slowly.
        - b) A flat line at zero.
        - c) **Rapid, high-frequency oscillations that grew in amplitude until the simulation failed.**
        - d) A smooth curve that decayed to a negative temperature.

        ??? info "See Answer"
            **c) Rapid, high-frequency oscillations that grew in amplitude until the simulation failed.** This is the classic visual evidence of numerical instability, where round-off errors are amplified exponentially.

    ??? question "25. The transition from Parabolic PDEs (Chapter 11) to Hyperbolic PDEs (Chapter 12) involves changing which part of the governing equation?"
        - a) Changing the second-order space derivative $\nabla^2 y$ to a first-order space derivative.
        - b) **Changing the first-order time derivative $\frac{\partial y}{\partial t}$ to a second-order time derivative $\frac{\partial^2 y}{\partial t^2}$.**
        - c) Adding a non-linear term to the equation.
        - d) Removing the boundary conditions.

        ??? info "See Answer"
            **b) Changing the first-order time derivative $\frac{\partial y}{\partial t}$ to a second-order time derivative $\frac{\partial^2 y}{\partial t^2}$.** This change transforms the dissipative Heat Equation into the propagative Wave Equation, which describes systems that retain and transport energy, like waves on a string.
