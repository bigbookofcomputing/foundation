
# **Chapter-9: Quizes**

---

!!! note "Quiz"
    **1. What is the fundamental difference between an Initial Value Problem (IVP) and a Boundary Value Problem (BVP)?**

    - A. IVPs are for time evolution, while BVPs are for static spatial configurations.
    - B. IVPs specify all conditions at a single starting point, while BVPs specify conditions at two different boundary points.
    - C. IVPs are solved with Runge-Kutta methods, while BVPs are solved with Euler's method.
    - D. IVPs are always linear, while BVPs are always nonlinear.

    ??? info "See Answer"
        **Correct: B**

        *(An IVP is like launching a projectile: you know its initial position and velocity. A BVP is like stringing a cable between two poles: you know the start and end points, but not the initial angle.)*

---

!!! note "Quiz"
    **2. When trying to solve a second-order ODE BVP like $y''(x) = f(x)$ with boundary conditions $y(0)=A$ and $y(L)=B$, what crucial piece of information is missing to use a standard IVP solver?**

    - A. The initial position, $y(0)$.
    - B. The final position, $y(L)$.
    - C. The initial slope, $y'(0)$.
    - D. The length of the domain, $L$.

    ??? info "See Answer"
        **Correct: C**

        *(A standard IVP solver like RK4 requires a complete set of initial conditions, which for a second-order ODE would be $y(0)$ and $y'(0)$. The BVP only provides $y(0)$ and a condition at the far end, $y(L)$.)*

---

!!! note "Quiz"
    **3. The "Shooting Method" solves a BVP by converting it into what other type of problem?**

    - A. A matrix eigenvalue problem.
    - B. A system of linear equations.
    - C. A root-finding problem.
    - D. A Fourier analysis problem.

    ??? info "See Answer"
        **Correct: C**

        *(The method "shoots" trajectories by guessing the initial slope $g = y'(0)$. It defines an error function $E(g)$ as the "miss distance" at the far boundary. The problem is solved when a root-finder finds the specific slope $g$ for which $E(g)=0$.)*

---

!!! note "Quiz"
    **4. What is the primary and significant disadvantage of the Shooting Method, especially for ODEs whose solutions can grow exponentially?**

    - A. It is computationally very efficient.
    - B. It is extremely stable and always converges.
    - C. It is prone to severe instability because small errors in the initial slope guess are amplified exponentially.
    - D. It can only solve linear ODEs.

    ??? info "See Answer"
        **Correct: C**

        *(If the true solution has exponential character, a tiny error in the initial slope guess will cause the numerical trajectory to diverge dramatically, often to infinity, making it impossible for the root-finder to converge.)*

---

!!! note "Quiz"
    **5. The Finite Difference Method (FDM) takes a completely different approach. What is its core strategy?**

    - A. It iteratively guesses the solution at every point.
    - B. It converts the differential equation into a large system of coupled algebraic (linear) equations.
    - C. It uses a Monte Carlo simulation to find the most probable path.
    - D. It relies on the Shooting Method as a sub-component.

    ??? info "See Answer"
        **Correct: B**

        *(FDM discretizes the domain and replaces derivatives with finite difference stencils. This transforms the calculus problem into a linear algebra problem, $\mathbf{A}\mathbf{y} = \mathbf{b}$, which can be solved globally and stably.)*

---

!!! note "Quiz"
    **6. In the Finite Difference Method, the second derivative $y''(x_i)$ is typically replaced by which stencil?**

    - A. The forward difference: $(y_{i+1} - y_i) / h$
    - B. The backward difference: $(y_i - y_{i-1}) / h$
    - C. The central difference: $(y_{i+1} - 2y_i + y_{i-1}) / h^2$
    - D. The Simpson's rule stencil.

    ??? info "See Answer"
        **Correct: C**

        *(This second-order accurate stencil is the cornerstone of the FDM for second-order ODEs. It relates the value at a point $y_i$ to its immediate neighbors, $y_{i-1}$ and $y_{i+1}$.)*

---

!!! note "Quiz"
    **7. When FDM is used to solve a linear BVP, the resulting matrix $\mathbf{A}$ in the system $\mathbf{A}\mathbf{y} = \mathbf{b}$ has what special, computationally advantageous structure?**

    - A. It is a dense, fully populated matrix.
    - B. It is a diagonal matrix.
    - C. It is a tridiagonal matrix.
    - D. It is an identity matrix.

    ??? info "See Answer"
        **Correct: C**

        *(Because the central difference stencil only connects a point to its immediate neighbors, the resulting matrix has non-zero elements only on the main diagonal and the two adjacent off-diagonals. This allows for very fast $\mathcal{O}(N)$ solvers.)*

---

!!! note "Quiz"
    **8. When solving the Time-Independent Schrödinger Equation (TISE) with FDM, the problem is transformed into what specific type of matrix problem?**

    - A. A standard system of linear equations ($\mathbf{A}\mathbf{x} = \mathbf{b}$).
    - B. A matrix inversion problem ($\mathbf{x} = \mathbf{A}^{-1}\mathbf{b}$).
    - C. A matrix eigenvalue problem ($\mathbf{H}\mathbf{\psi} = E\mathbf{\psi}$).
    - D. A determinant calculation problem.

    ??? info "See Answer"
        **Correct: C**

        *(The FDM discretization naturally maps the TISE into the form $\mathbf{H}\mathbf{\psi} = E\mathbf{\psi}$, where $\mathbf{H}$ is the Hamiltonian matrix.)*

---

!!! note "Quiz"
    **9. In the matrix eigenvalue problem for the TISE, $\mathbf{H}\mathbf{\psi} = E\mathbf{\psi}$, what do the eigenvalues $E$ and eigenvectors $\mathbf{\psi}$ represent physically?**

    - A. $E$ are the wavefunctions, $\mathbf{\psi}$ are the energy levels.
    - B. $E$ are the allowed energy levels, $\mathbf{\psi}$ are the corresponding wavefunctions.
    - C. $E$ is the potential, $\mathbf{\psi}$ is the kinetic energy.
    - D. $E$ is the position, $\mathbf{\psi}$ is the momentum.

    ??? info "See Answer"
        **Correct: B**

        *(This is the power of the method. The eigenvalues of the Hamiltonian matrix directly give the quantized energy levels, and the eigenvectors give the spatial shape of the stationary state wavefunctions.)*

---

!!! note "Quiz"
    **10. Which of the following is a classic example of a Boundary Value Problem?**

    - A. Predicting the trajectory of a thrown ball given its initial speed and angle.
    - B. Simulating the decay of a radioactive nucleus over time.
    - C. Finding the steady-state temperature distribution along a metal rod with its ends held at fixed, different temperatures.
    - D. Calculating the velocity of a falling object at each second after it is dropped.

    ??? info "See Answer"
        **Correct: C**

        *(This is a BVP because the constraints (the temperatures) are given at the boundaries (the ends of the rod), and we must find the solution "in-between.")*

---

!!! note "Quiz"
    **11. Why is the Finite Difference Method generally preferred over the Shooting Method for professional applications?**

    - A. It is simpler to understand conceptually.
    - B. It is significantly more stable and robust, especially for sensitive or stiff problems.
    - C. It requires fewer lines of code.
    - D. It always gives an exact analytical solution.

    ??? info "See Answer"
        **Correct: B**

        *(The global nature of the FDM avoids the exponential error amplification that can plague the iterative, guess-based Shooting Method, making it the reliable choice for a wider range of problems.)*

---

!!! note "Quiz"
    **12. In the FDM formulation of the TISE, the off-diagonal elements of the Hamiltonian matrix $\mathbf{H}$ represent what physical quantity?**

    - A. The potential energy at each point.
    - B. The total energy of the system.
    - C. The kinetic energy coupling between neighboring grid points.
    - D. The normalization constant of the wavefunction.

    ??? info "See Answer"
        **Correct: C**

        *(The term $(-\hbar^2 / 2mh^2)$ that appears on the off-diagonals comes directly from the discretization of the second derivative (the kinetic energy operator, $-\frac{\hbar^2}{2m}\frac{d^2}{dx^2}$), representing how adjacent points influence each other.)*

---

!!! note "Quiz"
    **13. The Shooting Method is a hybrid algorithm that couples an IVP solver with what other algorithm?**

    - A. A Fast Fourier Transform (FFT).
    - B. A root-finding algorithm (like Secant or Bisection).
    - C. A sorting algorithm (like Quicksort).
    - D. A matrix eigensolver.

    ??? info "See Answer"
        **Correct: B**

        *(The "outer loop" of the Shooting Method is a root-finder that intelligently updates the guess for the initial slope, while the "inner loop" is an IVP solver that computes the trajectory for each guess.)*

---

!!! note "Quiz"
    **14. In the FDM system $\mathbf{A}\mathbf{y} = \mathbf{b}$, where do the known boundary conditions (e.g., $y_0$ and $y_N$) typically get incorporated?**

    - A. Into the matrix $\mathbf{A}$.
    - B. Into the right-hand side vector $\mathbf{b}$.
    - C. Into the solution vector $\mathbf{y}$.
    - D. They are ignored.

    ??? info "See Answer"
        **Correct: B**

        *(For the equations corresponding to the points right next to the boundaries (i=1 and i=N-1), the known values $y_0$ and $y_N$ are moved to the right-hand side, becoming part of the constant vector $\mathbf{b}$.)*

---

!!! note "Quiz"
    **15. What is the primary advantage of using a specialized tridiagonal eigensolver (like `scipy.linalg.eigh_tridiagonal`) over a general-purpose eigensolver?**

    - A. It can handle complex-valued matrices.
    - B. It is significantly faster, with a computational cost of $\mathcal{O}(N^2)$ instead of $\mathcal{O}(N^3)$.
    - C. It finds more eigenvalues.
    - D. It is more accurate for dense matrices.

    ??? info "See Answer"
        **Correct: B**

        *(Exploiting the sparse, tridiagonal structure of the Hamiltonian matrix allows for much more efficient computation, which is critical when the number of grid points N is large.)*

---

!!! note "Quiz"
    **16. A BVP is described by $y'' = -9.8$ with $y(0)=0$ and $y(10)=0$. This physically represents:**

    - A. A quantum particle in a box.
    - B. The shape of a hanging cable or the trajectory of a projectile that starts and ends at the same height.
    - C. A simple harmonic oscillator.
    - D. A decaying exponential function.

    ??? info "See Answer"
        **Correct: B**

        *(This is the equation for an object under constant downward acceleration (gravity), with the boundary conditions specifying it starts and ends at a height of zero. The solution is a parabola.)*

---

!!! note "Quiz"
    **17. The "Relaxation Method" is another name for which technique?**

    - A. The Shooting Method.
    - B. The Finite Difference Method (FDM).
    - C. The Runge-Kutta Method.
    - D. The Secant Method.

    ??? info "See Answer"
        **Correct: B**

        *(The term "Relaxation" comes from an older, iterative way of solving the FDM system where the solution values were imagined to "relax" into their final, correct configuration.)*

---

!!! note "Quiz"
    **18. In the FDM solution to the "particle in a box" problem, the potential energy $V_i$ is set to what value on the main diagonal of the Hamiltonian?**

    - A. A very large number.
    - B. Zero.
    - C. A value proportional to the position, $x_i$.
    - D. A random number.

    ??? info "See Answer"
        **Correct: B**

        *(For the idealized "particle in a box" or infinite square well, the potential is zero everywhere inside the box. This simplifies the main diagonal of $\mathbf{H}$ to be constant.)*

---

!!! note "Quiz"
    **19. If you increase the number of grid points $N$ in the Finite Difference Method, what happens to the accuracy of the solution?**

    - A. The accuracy decreases.
    - B. The accuracy increases.
    - C. The accuracy is unaffected.
    - D. The method becomes unstable.

    ??? info "See Answer"
        **Correct: B**

        *(A larger N means a smaller step size $h$. Since the central difference stencil has an error of $\mathcal{O}(h^2)$, decreasing $h$ reduces the discretization error and makes the numerical solution converge to the true analytical solution.)*

---

!!! note "Quiz"
    **20. The Shooting Method requires two initial guesses for the slope, $g_1$ and $g_2$, to start a root-finder like the Secant method. What is a potential problem with choosing these guesses?**

    - A. If both guesses are positive, the method fails.
    - B. The guesses must be very close to the true value.
    - C. If the resulting errors $E(g_1)$ and $E(g_2)$ have the same sign, the true root may not lie between them, causing convergence issues.
    - D. The guesses must be integers.

    ??? info "See Answer"
        **Correct: C**

        *(Many root-finders, like Bisection, require the initial guesses to "bracket" the root (i.e., the errors must have opposite signs). Finding such a bracket can be a major challenge for the Shooting Method.)*

---

!!! note "Quiz"
    **21. The FDM converts the continuous wavefunction $\psi(x)$ into:**

    - A. A single number representing the total energy.
    - B. A discrete vector $\mathbf{\psi}$ where each element $\psi_i$ is the value of the wavefunction at grid point $x_i$.
    - C. A polynomial function.
    - D. The derivative of the wavefunction.

    ??? info "See Answer"
        **Correct: B**

        *(This is the essence of discretization. The continuous function is replaced by a finite list of its values at discrete points, which becomes the eigenvector in the matrix problem.)*

---

!!! note "Quiz"
    **22. Which method is better suited for finding the allowed energy levels of a quantum well with a complicated potential shape, $V(x)$?**

    - A. The Shooting Method, because it can handle any potential.
    - B. The Finite Difference Method, because the potential shape can be easily incorporated into the main diagonal of the Hamiltonian matrix.
    - C. Both are equally unsuitable.
    - D. An analytical pen-and-paper solution is always possible.

    ??? info "See Answer"
        **Correct: B**

        *(The FDM is exceptionally flexible. Any arbitrary potential function $V(x)$ can be handled simply by sampling its values at the grid points, $V_i = V(x_i)$, and adding them to the main diagonal of $\mathbf{H}$.)*

---

!!! note "Quiz"
    **23. The solution to a BVP is a function $y(x)$ over a spatial domain, while the solution to an IVP is typically a function $y(t)$ over a temporal domain. What does this imply about the nature of the problems?**

    - A. BVPs describe static or equilibrium systems, while IVPs describe dynamic, evolving systems.
    - B. BVPs are always easier to solve than IVPs.
    - C. BVPs are for 1D problems, while IVPs are for 2D problems.
    - D. There is no fundamental difference.

    ??? info "See Answer"
        **Correct: A**

        *(This is a key conceptual distinction. IVPs march forward in time from a known starting state. BVPs find the stable, static configuration of a system subject to fixed boundary constraints.)*

---

!!! note "Quiz"
    **24. In the FDM system $\mathbf{A}\mathbf{y} = \mathbf{b}$, what does the vector $\mathbf{y}$ represent?**

    - A. The known boundary conditions.
    - B. The vector of unknown solution values at the interior grid points.
    - C. The coefficients of the matrix $\mathbf{A}$.
    - D. The error at each grid point.

    ??? info "See Answer"
        **Correct: B**

        *(The goal of solving the matrix system is to find the values of the function $y_i$ at all the interior points $x_i$ where it is not already known.)*

---

!!! note "Quiz"
    **25. This chapter on BVPs serves as a bridge to the final part of the book, which deals with what topic?**

    - A. Advanced root-finding methods.
    - B. Machine Learning and Neural Networks.
    - C. Partial Differential Equations (PDEs).
    - D. Stochastic Methods and Monte Carlo.

    ??? info "See Answer"
        **Correct: C**

        *(The Finite Difference Method, particularly the 2D Laplacian stencil, is the foundational technique for solving elliptic PDEs like Laplace's and Poisson's equations, which are the subject of the next chapter.)*
