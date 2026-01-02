
# **Chapter-8: Quizes**

---

!!! note "Quiz"
    **1. What is the fundamental, long-term flaw of the RK4 method when applied to conservative systems like planetary orbits?**

    - A. It is only first-order accurate, making it too slow.
    - B. It systematically adds or removes energy from the system over time, causing a "secular drift."
    - C. It cannot handle second-order differential equations.
    - D. It requires an extremely small, fixed time step to be stable.

    ??? info "See Answer"
        **Correct: B**

        *(RK4 is not "symplectic." While highly accurate per-step, it doesn't preserve the geometric structure of Hamiltonian mechanics. This leads to a small, accumulating error that causes the total energy of the simulated system to drift monotonically, making long-term simulations physically incorrect.)*

---

!!! note "Quiz"
    **2. What is the defining characteristic of a "symplectic integrator" like the Verlet or Leapfrog algorithm?**

    - A. It achieves the highest possible order of accuracy per step.
    - B. It perfectly conserves the true energy of the system to machine precision.
    - C. It is designed to preserve the phase-space area/volume, ensuring that the total energy error remains bounded over time.
    - D. It only works for dissipative (energy-losing) systems.

    ??? info "See Answer"
        **Correct: C**

        *(The core philosophy of a symplectic integrator is to sacrifice some short-term precision to guarantee long-term fidelity. By preserving the geometric structure of phase space (Liouville's Theorem), it ensures the energy doesn't drift, but rather oscillates around the true value.)*

---

!!! note "Quiz"
    **3. According to Liouville's Theorem, what property of a cluster of initial conditions in phase space must be conserved as a Hamiltonian system evolves?**

    - A. The shape of the cluster.
    - B. The average position of the cluster.
    - C. The total volume (or area) occupied by the cluster.
    - D. The maximum momentum of any point in the cluster.

    ??? info "See Answer"
        **Correct: C**

        *(Liouville's Theorem is a cornerstone of Hamiltonian mechanics. It states that while the shape of a region in phase space may stretch and deform over time, its total volume is an invariant of motion. Symplectic integrators are built to respect this rule.)*

---

!!! note "Quiz"
    **4. How does the energy behavior of a symplectic integrator differ from that of RK4 in a long-term simulation of a conservative system?**

    - A. Symplectic energy drifts, while RK4 energy is perfectly constant.
    - B. Symplectic energy oscillates around the true value, while RK4 energy drifts away monotonically.
    - C. Both methods show identical energy drift.
    - D. Symplectic energy decays to zero, while RK4 energy grows to infinity.

    ??? info "See Answer"
        **Correct: B**

        *(This is the key visual difference. A plot of energy vs. time for a symplectic method shows bounded oscillations, while the same plot for RK4 shows a slow, steady, unbounded creep away from the correct value.)*

---

!!! note "Quiz"
    **5. The original Störmer-Verlet algorithm is derived by adding the forward and backward Taylor expansions of position, $x(t+h)$ and $x(t-h)$. What is the main consequence of this addition?**

    - A. It increases the accuracy to $\mathcal{O}(h^5)$.
    - B. It makes the algorithm require four function calls per step.
    - C. It causes all odd-power terms (like velocity $v$) to cancel out, resulting in a position-only update.
    - D. It makes the algorithm non-time-reversible.

    ??? info "See Answer"
        **Correct: C**

        *(The symmetry of adding the two expansions, $x(t \pm h)$, perfectly eliminates terms like $h v$, $h^3 \dddot{x}$, etc. This leads to the simple, elegant, and velocity-free update formula: $x_{n+1} = 2x_n - x_{n-1} + h^2 a_n$.)*

---

!!! note "Quiz"
    **6. What is the primary disadvantage of the original Störmer-Verlet algorithm that motivated the development of Velocity-Verlet?**

    - A. It is not symplectic.
    - B. It has a very low order of accuracy, $\mathcal{O}(h)$.
    - C. It does not explicitly calculate the velocity at each time step, making it inconvenient to find kinetic energy.
    - D. It is computationally very expensive.

    ??? info "See Answer"
        **Correct: C**

        *(While velocities can be approximated using finite differences, it's inconvenient. The Velocity-Verlet algorithm was developed to provide both position and velocity synchronously at each time step while retaining the symplectic nature of the original.)*

---

!!! note "Quiz"
    **7. The Velocity-Verlet algorithm is often described as a "Kick-Drift-Kick" sequence. What do these terms represent?**

    - A. Kick: Update position. Drift: Update velocity.
    - B. Kick: A half-step velocity update. Drift: A full-step position update.
    - C. Kick: Calculate energy. Drift: Calculate momentum.
    - D. Kick: A full-step position update. Drift: A half-step velocity update.

    ??? info "See Answer"
        **Correct: B**

        *(The sequence is: 1. **Kick** velocity by a half step. 2. **Drift** position by a full step using the new half-step velocity. 3. **Kick** velocity again by a half step using the new acceleration.)*

---

!!! note "Quiz"
    **8. What is the order of accuracy for both the Störmer-Verlet and Velocity-Verlet algorithms?**

    - A. $\mathcal{O}(h)$
    - B. $\mathcal{O}(h^2)$
    - C. $\mathcal{O}(h^3)$
    - D. $\mathcal{O}(h^4)$

    ??? info "See Answer"
        **Correct: B**

        *(Unlike RK4's $\mathcal{O}(h^4)$, Verlet-family algorithms are second-order. They trade some per-step accuracy for perfect long-term energy stability.)*

---

!!! note "Quiz"
    **9. The Leapfrog algorithm is mathematically equivalent to Velocity-Verlet but is structurally different. What is its key structural feature?**

    - A. It calculates positions at integer time steps ($t_n$) and velocities at half-integer time steps ($t_{n+1/2}$).
    - B. It uses a much larger time step than Velocity-Verlet.
    - C. It is a fourth-order accurate method.
    - D. It is not time-reversible.

    ??? info "See Answer"
        **Correct: A**

        *(This "staggered grid" is the defining feature of Leapfrog. Positions and velocities "leapfrog" over each other, which provides exceptional stability, especially in celestial mechanics.)*

---

!!! note "Quiz"
    **10. Why are symplectic integrators like Velocity-Verlet the standard choice for N-body simulations in astrophysics and molecular dynamics?**

    - A. Because they are the fastest algorithms available.
    - B. Because they can be run with very large time steps.
    - C. Because they conserve total energy and momentum over cosmic timescales, preventing orbits from spiraling away or molecules from "exploding."
    - D. Because they are the only algorithms that can handle more than two bodies.

    ??? info "See Answer"
        **Correct: C**

        *(The long-term stability provided by their structure-preserving nature is non-negotiable for these fields. An RK4 simulation of the solar system would fail relatively quickly as planets drift out of their orbits due to numerical energy errors.)*

---

!!! note "Quiz"
    **11. A "shadow Hamiltonian" ($\tilde{H}$) is a concept used to explain how symplectic integrators work. What is it?**

    - A. The true Hamiltonian of the system.
    - B. A modified energy function, slightly different from the true one, that the numerical solution conserves *perfectly*.
    - C. The potential energy part of the Hamiltonian.
    - D. A Hamiltonian that includes dissipative forces.

    ??? info "See Answer"
        **Correct: B**

        *(A symplectic integrator doesn't stay on the exact energy surface of the true Hamiltonian ($H$), but it finds a nearby "shadow" surface ($\tilde{H}$) and stays on it perfectly. This is why the energy error is bounded.)*

---

!!! note "Quiz"
    **12. The computational cost of calculating all pairwise forces in an N-body simulation scales as:**

    - A. $\mathcal{O}(N)$
    - B. $\mathcal{O}(N \log N)$
    - C. $\mathcal{O}(N^2)$
    - D. $\mathcal{O}(N^3)$

    ??? info "See Answer"
        **Correct: C**

        *(Each of the N bodies interacts with the other N-1 bodies, leading to a total of roughly $N \times (N-1)/2$ force calculations, which is an $\mathcal{O}(N^2)$ scaling.)*

---

!!! note "Quiz"
    **13. What does it mean for a numerical integrator to be "time-reversible"?**

    - A. It can only simulate systems that look the same forwards and backwards in time.
    - B. If you run the simulation forward and then backward for the same number of steps, you will return to the exact initial state.
    - C. The time step $h$ can be negative.
    - D. The total energy of the simulation always decreases.

    ??? info "See Answer"
        **Correct: B**

        *(Symplectic integrators have this property. If you stop at time $T$, flip the sign of all velocities, and integrate back to $t=0$, you will recover your starting state perfectly. RK4 does not have this property.)*

---

!!! note "Quiz"
    **14. In the Velocity-Verlet "Kick-Drift-Kick" sequence, the "Drift" step updates the position. Which velocity is used for this update?**

    - A. The velocity from the beginning of the step, $v_n$.
    - B. The velocity from the end of the step, $v_{n+1}$.
    - C. The half-step velocity calculated in the first kick, $v_{n+1/2}$.
    - D. The average of the start and end velocities, $(v_n + v_{n+1})/2$.

    ??? info "See Answer"
        **Correct: C**

        *(The sequence is precise: $x_{n+1} = x_n + h \cdot v_{n+1/2}$. Using this intermediate velocity is crucial for the algorithm's symplectic nature and $\mathcal{O}(h^2)$ accuracy.)*

---

!!! note "Quiz"
    **15. The Störmer-Verlet formula $x_{n+1} = 2x_n - x_{n-1} + h^2 a_n$ has a "startup problem." Why?**

    - A. It requires knowing the acceleration $a_n$, which is unknown.
    - B. To calculate the first step $x_1$, it requires a previous point $x_{-1}$, which doesn't exist.
    - C. The formula is unstable for the first few steps.
    - D. It cannot be used with a time step $h=0$.

    ??? info "See Answer"
        **Correct: B**

        *(The formula is a three-point rule. To get started, one typically uses a different, two-point method (like an Euler step) to find $x_1$ from $x_0$ just to "seed" the Verlet algorithm.)*

---

!!! note "Quiz"
    **16. Phase space for a 1D simple harmonic oscillator is a 2D plane. What are the axes of this plane?**

    - A. Position (x) and Time (t)
    - B. Velocity (v) and Time (t)
    - C. Position (x) and Momentum (p)
    - D. Kinetic Energy (K) and Potential Energy (U)

    ??? info "See Answer"
        **Correct: C**

        *(Phase space is the geometric space of all possible states of a system. For a classical mechanical system, the state is completely defined by the positions and momenta of all its components.)*

---

!!! note "Quiz"
    **17. If you simulate a stable circular orbit with RK4, what will you likely observe over a very long time?**

    - A. The orbit will remain a perfect circle.
    - B. The orbit will decay and spiral into the central mass.
    - C. The orbit will gain energy and spiral outwards, eventually escaping.
    - D. The orbit will become highly elliptical.

    ??? info "See Answer"
        **Correct: C**

        *(While the direction of drift can vary, for oscillatory systems, RK4 typically introduces a small amount of energy at each step, causing the simulated object to slowly spiral away from its stable trajectory.)*

---

!!! note "Quiz"
    **18. What is the primary philosophical difference between the design of RK4 and the design of a symplectic integrator?**

    - A. RK4 prioritizes speed; symplectic integrators prioritize simplicity.
    - B. RK4 prioritizes local (per-step) accuracy; symplectic integrators prioritize global (long-term) structural fidelity.
    - C. RK4 is for physics; symplectic integrators are for finance.
    - D. RK4 is deterministic; symplectic integrators are probabilistic.

    ??? info "See Answer"
        **Correct: B**

        *(This is the core trade-off. RK4 aims to minimize the error at each individual step. Symplectic methods accept a slightly larger per-step error in exchange for perfectly preserving the underlying geometric structure, which prevents the accumulation of error over time.)*

---

!!! note "Quiz"
    **19. In the two-body orbit simulation, the total momentum of the system should be conserved. For a two-body system starting from rest at its center of mass, the total momentum should remain:**

    - A. Equal to the total energy.
    - B. A large, constant value.
    - C. Zero.
    - D. Oscillating around a non-zero mean.

    ??? info "See Answer"
        **Correct: C**

        *(For an isolated system with no external forces, the total momentum is a conserved quantity. If the center of mass is initially at rest, the total momentum must remain zero for all time.)*

---

!!! note "Quiz"
    **20. The final step in the Velocity-Verlet algorithm is $v_{n+1} = v_{n+1/2} + \frac{h}{2} a_{n+1}$. Which acceleration is used here?**

    - A. The acceleration from the beginning of the step, $a_n$.
    - B. The acceleration calculated from the *new* position, $a_{n+1} = F(x_{n+1})/m$.
    - C. The average of the old and new accelerations.
    - D. A predicted acceleration from a Taylor series.

    ??? info "See Answer"
        **Correct: B**

        *(This is crucial. The final velocity "kick" must use the acceleration corresponding to the new position calculated in the "drift" step. This symmetric use of accelerations is key to the method's stability.)*

---

!!! note "Quiz"
    **21. This chapter on symplectic methods completes the study of what major class of problems?**

    - A. Boundary Value Problems (BVPs)
    - B. Root-Finding Problems
    - C. Initial Value Problems (IVPs)
    - D. Optimization Problems

    ??? info "See Answer"
        **Correct: C**

        *(Chapters 7 and 8 cover IVPs: problems where you know the initial state and the rules of evolution, and you must predict the future. The next chapter transitions to BVPs.)*

---

!!! note "Quiz"
    **22. A simulation of a simple harmonic oscillator with Velocity-Verlet shows the total energy oscillating with a maximum deviation of $10^{-5}$. An RK4 simulation with the same step size shows a final energy drift of $10^{-10}$. Which result is better for a long-term simulation?**

    - A. The RK4 result, because the final error is smaller.
    - B. The Velocity-Verlet result, because its error is bounded and will not grow further, whereas the RK4 error will continue to accumulate.
    - C. Both are equally good.
    - D. Neither is acceptable.

    ??? info "See Answer"
        **Correct: B**

        *(The absolute magnitude of the error at one point in time is less important than the trend. The Verlet error is stable and bounded, guaranteeing long-term physical behavior. The RK4 error, though small now, is growing and will eventually destroy the simulation.)*

---

!!! note "Quiz"
    **23. Which of the following physical systems would be an inappropriate choice for a symplectic integrator?**

    - A. A simulation of the solar system over a billion years.
    - B. A molecular dynamics simulation of a protein in a water box.
    - C. A simulation of a pendulum with air friction.
    - D. A simulation of a perfectly elastic collision between two particles.

    ??? info "See Answer"
        **Correct: C**

        *(Symplectic integrators are designed for *conservative* systems. A pendulum with air friction is a *dissipative* system—it loses energy. For this type of problem, a high-accuracy method like RK4 is the more appropriate choice.)*

---

!!! note "Quiz"
    **24. In the Leapfrog algorithm, how would you calculate the kinetic energy at an integer time step $t_n$?**

    - A. It is directly available from the algorithm as $v_n$.
    - B. It is impossible to know the kinetic energy at integer times.
    - C. By averaging the half-step velocities before and after: $v_n \approx (v_{n-1/2} + v_{n+1/2}) / 2$.
    - D. By using the position: $K_n = \frac{1}{2} x_n^2$.

    ??? info "See Answer"
        **Correct: C**

        *(This is the main inconvenience of the Leapfrog scheme. Since velocities are only known at half-steps, one must perform an averaging step to estimate the velocity (and thus kinetic energy) at the same integer time steps where position is known.)*

---

!!! note "Quiz"
    **25. The transition from Chapter 8 to Chapter 9 involves moving from Initial Value Problems (IVPs) to what other class of problems?**

    - A. Eigenvalue Problems
    - B. Boundary Value Problems (BVPs)
    - C. Fourier Analysis Problems
    - D. Partial Differential Equations (PDEs)

    ??? info "See Answer"
        **Correct: B**

        *(An IVP is like shooting a cannon: you know the start and must find the end. A BVP is like building a bridge: you know the start and end points and must find the curve that connects them.)*
