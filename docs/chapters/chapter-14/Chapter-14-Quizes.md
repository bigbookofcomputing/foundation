
!!! note "Quiz"

    ??? question "1. The Eigenvalue Problem, $\mathbf{A}\mathbf{x} = \lambda \mathbf{x}$, is used to find the 'natural' or 'intrinsic' properties of a system. In this equation, what do $\lambda$ and $\mathbf{x}$ represent?"
        - a) $\lambda$ is the source vector, and $\mathbf{x}$ is the response vector.
        - b) **$\lambda$ is an eigenvalue (a scalar), and $\mathbf{x}$ is the corresponding eigenvector (a vector).**
        - c) $\lambda$ is the system matrix, and $\mathbf{x}$ is the solution.
        - d) $\lambda$ is a differential operator, and $\mathbf{x}$ is a function.

        ??? info "See Answer"
            **b) $\lambda$ is an eigenvalue (a scalar), and $\mathbf{x}$ is the corresponding eigenvector (a vector).** The goal is to find the special vectors (eigenvectors) that are only scaled, not rotated, by the matrix transformation, and the corresponding scaling factors (eigenvalues).

    ??? question "2. When the Finite Difference Method (FDM) is applied to the Time-Independent Schrödinger Equation (TISE), it transforms the differential equation into what kind of problem?"
        - a) A system of linear equations, $\mathbf{A}\mathbf{x} = \mathbf{b}$.
        - b) **A matrix eigenvalue problem, $\mathbf{H}\boldsymbol{\psi} = E\boldsymbol{\psi}$.**
        - c) A root-finding problem, $f(E) = 0$.
        - d) An initial value problem.

        ??? info "See Answer"
            **b) A matrix eigenvalue problem, $\mathbf{H}\boldsymbol{\psi} = E\boldsymbol{\psi}$.** The Hamiltonian differential operator becomes the Hamiltonian matrix $\mathbf{H}$, the wavefunctions $\psi(x)$ become the eigenvectors $\boldsymbol{\psi}$, and the allowed energies $E$ become the eigenvalues.

    ??? question "3. The Hamiltonian matrices derived from physical problems are almost always Hermitian (or real-symmetric). What is the most important physical consequence of this property?"
        - a) It guarantees that the eigenvalues are complex.
        - b) **It guarantees that the eigenvalues (e.g., energy levels) are real numbers.**
        - c) It makes the matrix easy to invert.
        - d) It means the system has no ground state.

        ??? info "See Answer"
            **b) It guarantees that the eigenvalues (e.g., energy levels) are real numbers.** Physical observables like energy must be real, and the Hermitian nature of the underlying operators ensures this.

    ??? question "4. The Power Iteration method is a simple algorithm used to find:"
        - a) All eigenvalues of a matrix simultaneously.
        - b) The smallest eigenvalue of a matrix.
        - c) **The dominant (largest in magnitude) eigenvalue and its corresponding eigenvector.**
        - d) The solution to $\mathbf{A}\mathbf{x} = \mathbf{b}$.

        ??? info "See Answer"
            **c) The dominant (largest in magnitude) eigenvalue and its corresponding eigenvector.** It works by repeatedly applying the matrix to a random vector, which causes the component associated with the largest eigenvalue to grow the fastest.

    ??? question "5. To find the smallest eigenvalue (like the ground state energy) using an iterative method, one should apply the Power Iteration to which matrix?"
        - a) The transpose of the matrix, $\mathbf{A}^T$.
        - b) **The inverse of the matrix, $\mathbf{A}^{-1}$.**
        - c) The square of the matrix, $\mathbf{A}^2$.
        - d) The identity matrix.

        ??? info "See Answer"
            **b) The inverse of the matrix, $\mathbf{A}^{-1}$.** The eigenvalues of $\mathbf{A}^{-1}$ are the reciprocals of the eigenvalues of $\mathbf{A}$. Therefore, the smallest eigenvalue of $\mathbf{A}$ corresponds to the largest (dominant) eigenvalue of $\mathbf{A}^{-1}$.

    ??? question "6. The QR Algorithm is the workhorse method for finding:"
        - a) Only the dominant eigenvalue of a sparse matrix.
        - b) The solution to a tridiagonal system.
        - c) **All eigenvalues and eigenvectors of a small-to-medium-sized dense matrix.**
        - d) The determinant of a matrix.

        ??? info "See Answer"
            **c) All eigenvalues and eigenvectors of a small-to-medium-sized dense matrix.** It's an iterative $\mathcal{O}(N^3)$ method that rotates the matrix until it becomes triangular, with the eigenvalues appearing on the diagonal.

    ??? question "7. For solving the 1D TISE, the FDM produces a Hamiltonian matrix that is both symmetric and tridiagonal. Which `scipy` function is the most efficient and numerically stable choice for this specific structure?"
        - a) `scipy.linalg.eig`
        - b) `scipy.linalg.eigh`
        - c) **`scipy.linalg.eigh_tridiagonal`**
        - d) `scipy.linalg.solve`

        ??? info "See Answer"
            **c) `scipy.linalg.eigh_tridiagonal`**. This specialized solver is highly optimized for matrices that are both symmetric and tridiagonal, offering significant performance gains (often $\mathcal{O}(N^2)$ or better) over general-purpose eigensolvers.

    ??? question "8. In the context of coupled oscillators, the equation of motion can be written as the generalized eigenvalue problem $\mathbf{K}\mathbf{x} = \omega^2 \mathbf{M} \mathbf{x}$. What do the eigenvalues ($\lambda = \omega^2$) and eigenvectors ($\mathbf{x}$) represent?"
        - a) The eigenvalues are the masses, and the eigenvectors are the spring constants.
        - b) The eigenvalues are the displacements, and the eigenvectors are the frequencies.
        - c) **The eigenvalues are the squared natural frequencies of oscillation, and the eigenvectors are the normal mode shapes.**
        - d) The eigenvalues are the kinetic energies, and the eigenvectors are the potential energies.

        ??? info "See Answer"
            **c) The eigenvalues are the squared natural frequencies of oscillation, and the eigenvectors are the normal mode shapes.** Each eigenvector represents a pattern of motion where all masses oscillate at the same, single frequency determined by the corresponding eigenvalue.

    ??? question "9. In the provided Python code for the TISE solver, the main diagonal of the Hamiltonian matrix was constructed from which two physical quantities?"
        - a) The mass and the spatial step size.
        - b) **The kinetic energy term ($\hbar^2 / (m h^2)$) and the potential energy at each grid point ($V(x_i)$).**
        - c) The energy eigenvalue and the wavefunction.
        - d) The spring constant and Planck's constant.

        ??? info "See Answer"
            **b) The kinetic energy term ($\hbar^2 / (m h^2)$) and the potential energy at each grid point ($V(x_i)$).** The diagonal elements of the discrete Hamiltonian are $H_{ii} = \frac{\hbar^2}{m h^2} + V(x_i)$.

    ??? question "10. The off-diagonal elements of the FDM Hamiltonian matrix represent:"
        - a) The potential energy coupling between grid points.
        - b) **The kinetic energy coupling between adjacent grid points.**
        - c) The energy eigenvalues.
        - d) The boundary conditions.

        ??? info "See Answer"
            **b) The kinetic energy coupling between adjacent grid points.** The term $-\frac{\hbar^2}{2m h^2}$ in the off-diagonals comes directly from the central difference stencil for the second derivative (the kinetic energy operator).

    ??? question "11. The Python code for the coupled oscillators problem used `scipy.linalg.eigh(K, M)`. Why was this generalized solver necessary instead of a standard one?"
        - a) Because the stiffness matrix `K` was not symmetric.
        - b) **Because the problem was of the form $\mathbf{A}\mathbf{x} = \lambda \mathbf{B}\mathbf{x}$ (where $\mathbf{B}$ is the mass matrix `M`), not the standard form $\mathbf{A}\mathbf{x} = \lambda \mathbf{x}$.**
        - c) Because the masses were not all equal.
        - d) Because the eigenvalues were expected to be complex.

        ??? info "See Answer"
            **b) Because the problem was of the form $\mathbf{A}\mathbf{x} = \lambda \mathbf{B}\mathbf{x}$ (where $\mathbf{B}$ is the mass matrix `M`), not the standard form $\mathbf{A}\mathbf{x} = \lambda \mathbf{x}$.** The presence of the mass matrix `M` on the right-hand side requires a generalized eigensolver.

    ??? question "12. The results of the TISE solver for the Simple Harmonic Oscillator potential showed that the energy levels were:"
        - a) Degenerate (all had the same energy).
        - b) Spaced quadratically ($E_n \propto n^2$).
        - c) **Evenly spaced ($E_{n+1} - E_n = \text{constant}$).**
        - d) Spaced randomly.

        ??? info "See Answer"
            **c) Evenly spaced ($E_{n+1} - E_n = \text{constant}$).** The numerical results correctly reproduced the famous quantum result that the energy levels of the SHO are separated by a constant amount, $\hbar\omega$.

    ??? question "13. The eigenvectors found in the coupled oscillators problem represent the 'normal modes'. What is a normal mode?"
        - a) Any random motion of the masses.
        - b) A motion where only one mass moves.
        - c) **A specific pattern of motion where all masses oscillate with the same single frequency.**
        - d) The motion where all masses move in the same direction with the same amplitude.

        ??? info "See Answer"
            **c) A specific pattern of motion where all masses oscillate with the same single frequency.** Normal modes are the fundamental, decoupled patterns of vibration for the entire system.

    ??? question "14. The 'magic trick' of computational physics referred to in this chapter is:"
        - a) Using Python to solve physics problems.
        - b) **Converting a continuous differential equation into a discrete matrix eigenvalue problem.**
        - c) The ability of the QR algorithm to find all eigenvalues.
        - d) The fact that physical matrices are always symmetric.

        ??? info "See Answer"
            **b) Converting a continuous differential equation into a discrete matrix eigenvalue problem.** This transformation allows the power of linear algebra algorithms to be applied to problems in calculus, which is a cornerstone of the field.

    ??? question "15. If you needed to find only the 10 lowest energy states of a very large 2D quantum system (resulting in a huge, sparse Hamiltonian matrix), which type of solver would be most appropriate?"
        - a) A direct, dense solver like `eigh`.
        - b) The Power Iteration method.
        - c) **A sparse, iterative solver like `scipy.sparse.linalg.eigsh`.**
        - d) The `eigh_tridiagonal` solver.

        ??? info "See Answer"
            **c) A sparse, iterative solver like `scipy.sparse.linalg.eigsh`.** For huge, sparse matrices where you only need a subset of the eigenvalues (e.g., the lowest few), iterative sparse solvers are the only feasible option.

    ??? question "16. In the coupled oscillator simulation, the first normal mode was 'Symmetric'. What did its eigenvector shape look like?"
        - a) The middle mass was stationary, and the outer masses moved in opposite directions.
        - b) **The middle mass moved with the largest amplitude, and the outer masses moved with smaller amplitudes in the same direction.**
        - c) All masses moved with equal amplitude in the same direction.
        - d) The masses moved in a complex, alternating pattern.

        ??? info "See Answer"
            **b) The middle mass moved with the largest amplitude, and the outer masses moved with smaller amplitudes in the same direction.** The plot shows the central bar is tallest, with the two side bars also positive, representing a symmetric, in-phase motion.

    ??? question "17. The second normal mode was 'Anti-Symmetric'. What was its characteristic motion?"
        - a) All masses were stationary.
        - b) **The middle mass was stationary, and the two outer masses moved with equal and opposite amplitudes.**
        - c) The two left masses moved together, and the rightmost mass moved in the opposite direction.
        - d) All masses moved in the same direction.

        ??? info "See Answer"
            **b) The middle mass was stationary, and the two outer masses moved with equal and opposite amplitudes.** The plot for Mode 2 shows a zero amplitude for the middle mass and equal but opposite amplitudes for the outer masses.

    ??? question "18. The process of solving the eigenvalue problem is often referred to as 'diagonalizing the matrix'. Why?"
        - a) Because it only works for diagonal matrices.
        - b) **Because the process is equivalent to finding a change of basis in which the matrix transformation becomes a simple diagonal matrix, with the eigenvalues on the diagonal.**
        - c) Because the eigenvectors are the diagonal elements.
        - d) Because the final step is to divide by the diagonal.

        ??? info "See Answer"
            **b) Because the process is equivalent to finding a change of basis in which the matrix transformation becomes a simple diagonal matrix, with the eigenvalues on the diagonal.** In the basis of its own eigenvectors, the matrix operation is just a simple scaling.

    ??? question "19. What is the primary difference between the 'driven problem' ($\mathbf{A}\mathbf{x}=\mathbf{b}$) and the 'natural problem' ($\mathbf{A}\mathbf{x}=\lambda\mathbf{x}$)? "
        - a) The driven problem is linear, while the natural problem is non-linear.
        - b) **The driven problem solves for the system's response to an external source $\mathbf{b}$, while the natural problem finds the intrinsic properties (modes, frequencies, energies) of the system $\mathbf{A}$ itself.**
        - c) The driven problem is an ODE, while the natural problem is a PDE.
        - d) The driven problem requires iterative solvers, while the natural problem uses direct solvers.

        ??? info "See Answer"
            **b) The driven problem solves for the system's response to an external source $\mathbf{b}$, while the natural problem finds the intrinsic properties (modes, frequencies, energies) of the system $\mathbf{A}$ itself.**

    ??? question "20. The wavefunctions ($\psi_n$) obtained from the TISE solver must be normalized. What does this normalization represent physically?"
        - a) It ensures the energy is conserved.
        - b) **It ensures that the total probability of finding the particle somewhere in space is equal to 1.**
        - c) It sets the ground state energy to zero.
        - d) It makes the wavefunction easier to plot.

        ??? info "See Answer"
            **b) It ensures that the total probability of finding the particle somewhere in space is equal to 1.** The squared magnitude of the wavefunction, $|\psi(x)|^2$, is a probability density, and the integral over all space must be 1.

    ??? question "21. The number of nodes (zero-crossings) in the wavefunction $\psi_n$ for the Simple Harmonic Oscillator corresponds to:"
        - a) The energy of the state, $E_n$.
        - b) **The quantum number of the state, $n$.**
        - c) The value of Planck's constant.
        - d) The width of the potential well.

        ??? info "See Answer"
            **b) The quantum number of the state, $n$.** The ground state ($n=0$) has zero nodes, the first excited state ($n=1$) has one node, the second ($n=2$) has two nodes, and so on. This is a general feature of 1D bound state problems.

    ??? question "22. Why is it generally not a good idea to write your own eigensolver for production code?"
        - a) It is impossible to do in Python.
        - b) **Library functions like those in `scipy.linalg` are highly optimized, numerically stable, and tested, and will almost always outperform a custom implementation.**
        - c) Eigensolvers are protected by copyright.
        - d) Physics problems do not require eigensolvers.

        ??? info "See Answer"
            **b) Library functions like those in `scipy.linalg` are highly optimized, numerically stable, and tested, and will almost always outperform a custom implementation.** Reinventing the wheel is inefficient and prone to error when robust, high-performance tools are readily available.

    ??? question "23. The eigenvalues of the coupled oscillator problem were $\omega^2$. What mathematical operation was needed to find the actual frequencies, $f$?"
        - a) Squaring the eigenvalues and multiplying by $2\pi$.
        - b) **Taking the square root of the eigenvalues (to get $\omega$) and then dividing by $2\pi$.**
        - c) Taking the logarithm of the eigenvalues.
        - d) The eigenvalues are the frequencies, so no operation was needed.

        ??? info "See Answer"
            **b) Taking the square root of the eigenvalues (to get $\omega$) and then dividing by $2\pi$.** The eigenvalues give the angular frequency squared ($\omega^2$), which must be converted to frequency in Hertz ($f = \omega / 2\pi$).

    ??? question "24. The FDM converts the continuous wavefunction $\psi(x)$ into a discrete vector $\boldsymbol{\psi}$. What does each element of this vector, $\psi_i$, represent?"
        - a) The energy of the particle at grid point $i$.
        - b) **The amplitude of the wavefunction at the discrete spatial grid point $x_i$.**
        - c) The probability of finding the particle at grid point $i$.
        - d) The momentum of the particle at grid point $i$.

        ??? info "See Answer"
            **b) The amplitude of the wavefunction at the discrete spatial grid point $x_i$.** The eigenvector is a list of numbers representing the value of the continuous function at each discrete point in the spatial grid.

    ??? question "25. This chapter completes the core toolkit for solving physics problems with linear algebra. The next part of the book (Part 6) will focus on what?"
        - a) More advanced PDE solving techniques.
        - b) Non-linear dynamics and chaos.
        - c) **Data analysis techniques, such as Fourier analysis (FFT) and Principal Component Analysis (PCA).**
        - d) Building graphical user interfaces for physics simulations.

        ??? info "See Answer"
            **c) Data analysis techniques, such as Fourier analysis (FFT) and Principal Component Analysis (PCA).** Having learned how to generate data from simulations, the focus now shifts to analyzing that data to extract physical insights.
