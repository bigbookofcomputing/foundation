
!!! note "Quiz"

    ??? question "1. The Wave Equation, $\frac{\partial^2 y}{\partial t^2} = v^2 \frac{\partial^2 y}{\partial x^2}$, is the classic example of what type of Partial Differential Equation?"
        - a) Elliptic PDE
        - b) **Hyperbolic PDE**
        - c) Parabolic PDE
        - d) Schrödinger PDE

        ??? info "See Answer"
            **b) Hyperbolic PDE**. Hyperbolic PDEs are characterized by a second-order time derivative, which gives rise to wave-like, propagative solutions, as opposed to the diffusive solutions of Parabolic PDEs.

    ??? question "2. What is the key difference in the time derivative term between the Heat Equation (Parabolic) and the Wave Equation (Hyperbolic)?"
        - a) There is no time derivative in the Wave Equation.
        - b) The Wave Equation has a first-order time derivative, while the Heat Equation has a second-order one.
        - c) **The Wave Equation has a second-order time derivative ($\frac{\partial^2 y}{\partial t^2}$), while the Heat Equation has a first-order one ($\frac{\partial T}{\partial t}$).**
        - d) Both have a second-order time derivative, but the sign is different.

        ??? info "See Answer"
            **c) The Wave Equation has a second-order time derivative ($\frac{\partial^2 y}{\partial t^2}$), while the Heat Equation has a first-order one ($\frac{\partial T}{\partial t}$).** This is the fundamental structural difference that leads to propagation instead of diffusion.

    ??? question "3. To fully specify a problem involving the 1D Wave Equation, how many initial conditions are required?"
        - a) One: the initial position $y(x, 0)$.
        - b) **Two: the initial position $y(x, 0)$ and the initial velocity $\frac{\partial y}{\partial t}(x, 0)$.**
        - c) One: the initial velocity $\frac{\partial y}{\partial t}(x, 0)$.
        - d) None, only boundary conditions are needed.

        ??? info "See Answer"
            **b) Two: the initial position $y(x, 0)$ and the initial velocity $\frac{\partial y}{\partial t}(x, 0)$.** Because the equation is second-order in time, it is analogous to Newton's second law and requires both initial position and initial velocity to define the state.

    ??? question "4. The explicit FTCS finite difference scheme for the Wave Equation is structurally identical to which well-known ODE integration algorithm?"
        - a) The Euler Method
        - b) The Runge-Kutta (RK4) Method
        - c) **The Verlet Algorithm**
        - d) The Leapfrog Method

        ??? info "See Answer"
            **c) The Verlet Algorithm**. The recurrence relation $y_{i, n+1} = 2y_{i, n} - y_{i, n-1} + C^2 (\dots)$ has the exact same form as the Verlet integrator $x_{n+1} = 2x_n - x_{n-1} + h^2 a_n$, making it an excellent choice for energy-conserving systems.

    ??? question "5. What is the definition of the Courant Number, $C$, for the 1D Wave Equation?"
        - a) $C = \frac{v h_x}{h_t}$
        - b) $C = v \frac{h_t}{h_x^2}$
        - c) **$C = \frac{v h_t}{h_x}$**
        - d) $C = v h_t$

        ??? info "See Answer"
            **c) $C = \frac{v h_t}{h_x}$**. The Courant number is the ratio of the physical distance the wave travels in one time step ($v h_t$) to the size of a spatial grid cell ($h_x$).

    ??? question "6. What is the Courant-Friedrichs-Lewy (CFL) stability condition for the explicit FTCS scheme for the 1D Wave Equation?"
        - a) $C > 1$
        - b) **$C \le 1$**
        - c) $C \le 0.5$
        - d) $C$ must be an integer.

        ??? info "See Answer"
            **b) $C \le 1$**. The numerical scheme is stable only if the Courant number is less than or equal to one. This means the numerical speed of information ($h_x/h_t$) must be greater than or equal to the physical wave speed ($v$).

    ??? question "7. What is the physical interpretation of the CFL condition, $C \le 1$?"
        - a) The time step must be smaller than the wave speed.
        - b) **The wave cannot travel more than one spatial grid cell ($h_x$) in a single time step ($h_t$).**
        - c) The simulation must conserve energy.
        - d) The spatial resolution must be higher than the temporal resolution.

        ??? info "See Answer"
            **b) The wave cannot travel more than one spatial grid cell ($h_x$) in a single time step ($h_t$).** If it does ($C>1$), the numerical algorithm literally "misses" information, causing instability.

    ??? question "8. The main FTCS recurrence relation for the Wave Equation is a 'three-level' scheme. What is the 'first step problem' this creates?"
        - a) The first step is always unstable.
        - b) The first step requires solving a matrix equation.
        - c) **To calculate the state at $n=1$, the scheme requires the state at $n=-1$, which is unknown.**
        - d) The first step has a very large truncation error.

        ??? info "See Answer"
            **c) To calculate the state at $n=1$, the scheme requires the state at $n=-1$, which is unknown.** The main loop needs data from two previous time steps ($n$ and $n-1$), but at the beginning, we only have data for $n=0$.

    ??? question "9. How is the 'first step problem' solved?"
        - a) By assuming the state at $n=-1$ is zero.
        - b) By using the Euler method for the first step.
        - c) **By using the initial velocity condition, $\frac{\partial y}{\partial t}(x,0)$, to derive a special, one-time formula for the state at $n=1$.**
        - d) By setting $C=1$, which simplifies the equation.

        ??? info "See Answer"
            **c) By using the initial velocity condition, $\frac{\partial y}{\partial t}(x,0)$, to derive a special, one-time formula for the state at $n=1$.** A central difference approximation of the initial velocity allows us to eliminate the unknown $y_{i, -1}$ term.

    ??? question "10. In the 'plucked string' simulation, the string is released from rest. How does this simplify the special formula for the first time step?"
        - a) It makes the Courant number equal to 1.
        - b) **The term involving the initial velocity ($h_t v_{i,0}$) becomes zero.**
        - c) The Laplacian term becomes zero.
        - d) The formula for the first step becomes identical to the main recurrence relation.

        ??? info "See Answer"
            **b) The term involving the initial velocity ($h_t v_{i,0}$) becomes zero.** If the initial velocity is zero, the first step update depends only on the initial shape and the spatial curvature.

    ??? question "11. Unlike the FTCS scheme for the Heat Equation, the FTCS scheme for the Wave Equation has a stability constraint that is:"
        - a) Quadratic: $h_t \propto h_x^2$
        - b) **Linear: $h_t \propto h_x$**
        - c) Exponential: $h_t \propto e^{h_x}$
        - d) Independent of $h_x$

        ??? info "See Answer"
            **b) Linear: $h_t \propto h_x$**. The CFL condition $h_t \le h_x/v$ means that if you halve the grid spacing $h_x$, you only need to halve the time step $h_t$. This is less restrictive than the quadratic relationship for the parabolic FTCS scheme.

    ??? question "12. In the provided Python code for the CFL stability test, what was the result of running the simulation with a Courant number $C=1.1$?"
        - a) The wave propagated correctly but with some numerical damping.
        - b) The simulation was stable but inaccurate.
        - c) **The wave amplitude grew exponentially, leading to a numerical explosion.**
        - d) The wave did not move from its initial position.

        ??? info "See Answer"
            **c) The wave amplitude grew exponentially, leading to a numerical explosion.** The plot of maximum amplitude vs. time clearly shows bounded oscillation for the stable case ($C=0.9$) and exponential growth for the unstable case ($C=1.1$).

    ??? question "13. Why is an explicit, non-dissipative scheme like the Verlet-style FTCS often preferred for wave problems over an implicit, dissipative scheme like Crank-Nicolson?"
        - a) Explicit schemes are always more accurate.
        - b) **Waves must conserve energy and propagate without losing amplitude, and implicit schemes often introduce numerical damping that would artificially smooth out the wave.**
        - c) Implicit schemes cannot handle the second-order time derivative.
        - d) Explicit schemes are unconditionally stable for wave problems.

        ??? info "See Answer"
            **b) Waves must conserve energy and propagate without losing amplitude, and implicit schemes often introduce numerical damping that would artificially smooth out the wave.** The energy-conserving nature of the Verlet-like scheme is a physical feature that is desirable to preserve in the numerical model.

    ??? question "14. In the 'plucked string' simulation, the initial triangular shape splits into two pulses that travel in opposite directions. What phenomenon is observed when these pulses reach the fixed ends of the string?"
        - a) They are absorbed by the boundary.
        - b) They pass through the boundary.
        - c) **They reflect off the boundary and invert their sign.**
        - d) They reflect off the boundary without inverting their sign.

        ??? info "See Answer"
            **c) They reflect off the boundary and invert their sign.** For a fixed (Dirichlet) boundary condition, a wave pulse reflects with an inverted amplitude.

    ??? question "15. The interference of the reflected waves in the plucked string simulation leads to the formation of:"
        - a) Shock waves
        - b) Solitons
        - c) **Standing waves (harmonics)**
        - d) Diffusive waves

        ??? info "See Answer"
            **c) Standing waves (harmonics)**. The superposition of the left- and right-traveling waves and their reflections creates stable patterns of oscillation known as standing waves, which correspond to the natural frequencies (harmonics) of the string.

    ??? question "16. If a string were fixed at one end but free at the other (a Neumann boundary condition, $\frac{\partial y}{\partial x}=0$), how would a wave reflect from the free end?"
        - a) It would reflect and invert its sign.
        - b) **It would reflect without inverting its sign.**
        - c) It would be completely absorbed.
        - d) The simulation would become unstable.

        ??? info "See Answer"
            **b) It would reflect without inverting its sign.** A free end allows the string to move, and the wave reflects with the same sign (a crest reflects as a crest).

    ??? question "17. The FTCS recurrence relation for the wave equation is $y_{i, n+1} = 2y_{i, n} - y_{i, n-1} + C^2 (y_{i+1, n} - 2y_{i, n} + y_{i-1, n})$. The term $(y_{i+1, n} - 2y_{i, n} + y_{i-1, n})$ is a finite difference approximation of:"
        - a) The first spatial derivative.
        - b) **The second spatial derivative (the Laplacian).**
        - c) The first time derivative.
        - d) The wave speed.

        ??? info "See Answer"
            **b) The second spatial derivative (the Laplacian).** This term represents the spatial curvature of the string, which provides the restoring force that drives the acceleration.

    ??? question "18. What is the primary purpose of the `ftcs_wave_solve` function in the first code project?"
        - a) To simulate the formation of harmonics.
        - b) **To demonstrate the stability difference between a simulation with $C \le 1$ and one with $C > 1$.**
        - c) To solve the 'first step problem'.
        - d) To implement an implicit solver.

        ??? info "See Answer"
            **b) To demonstrate the stability difference between a simulation with $C \le 1$ and one with $C > 1$.** The code runs two cases, one stable and one unstable, and plots the maximum amplitude over time to show the bounded vs. explosive behavior.

    ??? question "19. In the second code project ('Plucked String'), why is the Courant number $C$ set to exactly 1.0?"
        - a) It is the only stable value.
        - b) **It allows for the largest possible time step, making the simulation run fastest while remaining stable.**
        - c) It simplifies the first-step formula.
        - d) It is required for Neumann boundary conditions.

        ??? info "See Answer"
            **b) It allows for the largest possible time step, making the simulation run fastest while remaining stable.** Since the scheme is stable for $C \le 1$, choosing $C=1$ is the most computationally efficient option.

    ??? question "20. What does the plot in the 'Plucked String' simulation, showing snapshots at different times, illustrate?"
        - a) The exponential decay of the wave.
        - b) The violation of the CFL condition.
        - c) **The propagation of the initial shape, its reflection at the boundaries, and its return to the (inverted) initial shape after one full period.**
        - d) The diffusion of the initial shape into a flat line.

        ??? info "See Answer"
            **c) The propagation of the initial shape, its reflection at the boundaries, and its return to the (inverted) initial shape after one full period.** The snapshots capture the key dynamics of wave motion: propagation, reflection, and superposition.

    ??? question "21. If the initial velocity of the string was not zero (e.g., a string being struck by a hammer), which part of the simulation code would need to be changed?"
        - a) The main FTCS recurrence loop.
        - b) The boundary conditions.
        - c) **The special formula used for the first time step.**
        - d) The value of the wave speed `v`.

        ??? info "See Answer"
            **c) The special formula used for the first time step.** The term $h_t v_{i,0}$ in the first-step formula, which was previously zero, would now be non-zero and would need to be calculated.

    ??? question "22. The progression from Elliptic to Parabolic to Hyperbolic PDEs demonstrates a move from:"
        - a) 1D problems to 3D problems.
        - b) Linear problems to non-linear problems.
        - c) **Static equilibrium (Elliptic), to dissipative evolution (Parabolic), to propagative evolution (Hyperbolic).**
        - d) Problems solvable by hand to problems requiring computers.

        ??? info "See Answer"
            **c) Static equilibrium (Elliptic), to dissipative evolution (Parabolic), to propagative evolution (Hyperbolic).** This sequence represents an increase in dynamic complexity, from static fields to smoothing/diffusing systems to energy-conserving waves.

    ??? question "23. The FTCS scheme for the Wave Equation is explicit. This means:"
        - a) It requires solving a matrix system at each step.
        - b) **The future state $y_{i, n+1}$ can be calculated directly from the known states at previous time steps ($n$ and $n-1$).**
        - c) It is unconditionally stable.
        - d) It is only first-order accurate.

        ??? info "See Answer"
            **b) The future state $y_{i, n+1}$ can be calculated directly from the known states at previous time steps ($n$ and $n-1$).** No matrix inversion or system solve is needed, making each step computationally cheap.

    ??? question "24. In the stability analysis plot, why is a logarithmic scale used for the Y-axis ('Max Displacement')?"
        - a) To make the stable oscillations look larger.
        - b) **To clearly visualize the difference between the bounded oscillation of the stable case and the exponential growth of the unstable case.**
        - c) Because displacement is always a logarithmic quantity.
        - d) To hide the negative values of the displacement.

        ??? info "See Answer"
            **b) To clearly visualize the difference between the bounded oscillation of the stable case and the exponential growth of the unstable case.** On a log scale, exponential growth appears as a straight line with a positive slope, making the instability immediately obvious compared to the flat, bounded line of the stable case.

    ??? question "25. The conclusion of Part 4 (PDEs) is that the Finite Difference Method consistently transforms PDE problems into what other type of mathematical problem?"
        - a) Root-finding problems.
        - b) Optimization problems.
        - c) **Systems of linear equations.**
        - d) Fast Fourier Transforms.

        ??? info "See Answer"
            **c) Systems of linear equations.** Whether solving BVPs directly or using implicit methods for time-dependent PDEs, the FDM approach ultimately requires solving large, often sparse, matrix systems of the form $\mathbf{A}\mathbf{x} = \mathbf{b}$. This motivates the deep dive into linear algebra in Part 5.
