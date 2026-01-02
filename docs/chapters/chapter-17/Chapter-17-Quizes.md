
!!! note "Quiz"

    ---
    
    ??? question "1. Why are deterministic solvers like RK4 or PDE solvers insufficient for modeling systems in statistical mechanics or quantum mechanics?"
        - a) They are too computationally expensive.
        - b) These physical systems are inherently stochastic and probabilistic, not deterministic.
        - c) They cannot handle high-dimensional data.
        - d) They are numerically unstable for long simulations.
    
        ??? info "See Answer"
            - **b) These physical systems are inherently stochastic and probabilistic, not deterministic.**
            - **Explanation:** The behavior of individual particles in a gas or the outcome of a quantum measurement is governed by chance, which deterministic rules cannot capture.
    
    ---
    
    ??? question "2. What is a Pseudo-Random Number Generator (PRNG)?"
        - a) A hardware device that generates true random numbers from atmospheric noise.
        - b) A deterministic algorithm that produces a sequence of numbers that appears random but is fully reproducible from a starting 'seed'.
        - c) A quantum mechanical process that guarantees true randomness.
        - d) A method for sorting numbers in a random order.
    
        ??? info "See Answer"
            - **b) A deterministic algorithm that produces a sequence of numbers that appears random but is fully reproducible from a starting 'seed'.**
            - **Explanation:** PRNGs create an illusion of randomness using a fixed mathematical formula, which is essential for scientific reproducibility.
    
    ---
    
    ??? question "3. What is the most important scientific advantage of using a 'seed' in a PRNG for a complex simulation?"
        - a) It makes the simulation run significantly faster.
        - b) It guarantees the random numbers are uniformly distributed.
        - c) It allows the exact same sequence of 'random' events to be reproduced, which is crucial for debugging and verification.
        - d) It increases the period length of the random sequence.
    
        ??? info "See Answer"
            - **c) It allows the exact same sequence of 'random' events to be reproduced, which is crucial for debugging and verification.**
            - **Explanation:** Reproducibility is a cornerstone of the scientific method, and seeds ensure that stochastic simulations can be verified by others.
    
    ---
    
    ??? question "4. The Linear Congruential Generator (LCG) is a simple PRNG defined by the formula $r_{n+1} = (a r_n + c) \bmod m$. What do the parameters $a, c,$ and $m$ represent?"
        - a) The seed, the step size, and the number of dimensions.
        - b) The multiplier, the increment, and the modulus.
        - c) The mean, the standard deviation, and the variance.
        - d) The initial position, the velocity, and the acceleration.
    
        ??? info "See Answer"
            - **b) The multiplier, the increment, and the modulus.**
            - **Explanation:** These carefully chosen integer constants define the specific sequence and statistical properties of the LCG.
    
    ---
    
    ??? question "5. The Random Walk is a microscopic, stochastic model for which macroscopic physical process?"
        - a) Wave propagation.
        - b) Simple harmonic motion.
        - c) Gravitational orbits.
        - d) Diffusion (as described by the Heat Equation).
    
        ??? info "See Answer"
            - **d) Diffusion (as described by the Heat Equation).**
            - **Explanation:** The collective behavior of many random walkers is described by the same mathematics as the diffusion of heat or particles.
    
    ---
    
    ??? question "6. What is the fundamental relationship between the net displacement ($\Delta x$) of a random walker and the elapsed time ($t$)?"
        - a) $\Delta x \propto t$
        - b) $\Delta x \propto t^2$
        - c) $\Delta x \propto \sqrt{t}$
        - d) $\Delta x$ is constant.
    
        ??? info "See Answer"
            - **c) $\Delta x \propto \sqrt{t}$**
            - **Explanation:** This square-root scaling is the hallmark of diffusive processes and distinguishes them from ballistic motion where displacement is linear with time.
    
    ---
    
    ??? question "7. What is the primary advantage of Monte Carlo Integration over grid-based methods like Simpson's Rule for high-dimensional integrals?"
        - a) Its error scales as $\mathcal{O}(1/N^4)$, which is superior to all other methods.
        - b) It is always more accurate for any number of dimensions.
        - c) Its error scales as $\mathcal{O}(1/\sqrt{N})$ regardless of dimension, thus avoiding the 'Curse of Dimensionality'.
        - d) It does not require the function to be continuous.
    
        ??? info "See Answer"
            - **c) Its error scales as $\mathcal{O}(1/\sqrt{N})$ regardless of dimension, thus avoiding the 'Curse of Dimensionality'.**
            - **Explanation:** For high dimensions, the exponential growth of grid points makes grid-based methods impossible, while Monte Carlo remains feasible.
    
    ---
    
    ??? question "8. The 'Mean Value' method of Monte Carlo integration approximates an integral $I = \int_a^b f(x) dx$ using the formula:"
        - a) $I \approx (b-a) \cdot \max(f(x_i))$
        - b) $I \approx (b-a) \cdot \frac{1}{N} \sum_{i=1}^N f(x_i)$
        - c) $I \approx \frac{1}{N} \sum_{i=1}^N (f(x_i))^2$
        - d) $I \approx (b-a) \cdot f((a+b)/2)$
    
        ??? info "See Answer"
            - **b) $I \approx (b-a) \cdot \frac{1}{N} \sum_{i=1}^N f(x_i)$**
            - **Explanation:** The integral is approximated as the volume of the domain multiplied by the average value of the function, estimated from random samples.
    
    ---
    
    ??? question "9. The 'Inverse Transform Method' is a technique for what purpose?"
        - a) Calculating the inverse of a matrix.
        - b) Performing a Fourier transform.
        - c) Generating random numbers that follow a specific, non-uniform probability distribution using a uniform random number source.
        - d) Solving an integral by transforming the variable.
    
        ??? info "See Answer"
            - **c) Generating random numbers that follow a specific, non-uniform probability distribution using a uniform random number source.**
            - **Explanation:** It's a fundamental technique to translate the uniform output of a PRNG into physically meaningful distributions like exponential decay.
    
    ---
    
    ??? question "10. To use the Inverse Transform Method to sample from a probability distribution $p(x)$, one must first calculate its Cumulative Distribution Function (CDF), $P(x)$. How is the sampled value $x$ then found from a uniform random number $r \in [0, 1)$?"
        - a) $x = P(r)$
        - b) $x = p(r)$
        - c) $x = P^{-1}(r)$ (the inverse of the CDF evaluated at r)
        - d) $x = \int p(r) dr$
    
        ??? info "See Answer"
            - **c) $x = P^{-1}(r)$ (the inverse of the CDF evaluated at r)**
            - **Explanation:** By setting the uniform probability `r` equal to the cumulative probability `P(x)`, we can solve for `x` by inverting the function.
    
    ---
    
    ??? question "11. The Box-Muller Transform is a specialized and efficient algorithm for generating random numbers that follow which important distribution?"
        - a) Uniform distribution
        - b) Exponential distribution
        - c) Gaussian (Normal) distribution
        - d) Poisson distribution
    
        ??? info "See Answer"
            - **c) Gaussian (Normal) distribution**
            - **Explanation:** It's a widely used method to generate normally distributed random numbers, which are central to many statistical models.
    
    ---
    
    ??? question "12. If you simulate a large ensemble of 1D random walkers and plot a histogram of their final positions, what shape will the distribution have?"
        - a) A flat, uniform distribution.
        - b) A sharp peak at x=0.
        - c) An exponential decay.
        - d) A Gaussian (bell curve) distribution.
    
        ??? info "See Answer"
            - **d) A Gaussian (bell curve) distribution.**
            - **Explanation:** This convergence to a Gaussian distribution is a manifestation of the Central Limit Theorem and demonstrates the link between the random walk and the Diffusion Equation.
    
    ---
    
    ??? question "13. For which of the following problems would Monte Carlo integration be a better choice than Simpson's Rule?"
        - a) Calculating the 1D integral of $\sin(x)$ from 0 to $\pi$ to high precision.
        - b) Calculating the 10-dimensional volume of a hypersphere.
        - c) Finding the area of a simple 2D circle.
        - d) Integrating a smooth, well-behaved 1D function.
    
        ??? info "See Answer"
            - **b) Calculating the 10-dimensional volume of a hypersphere.**
            - **Explanation:** The 'Curse of Dimensionality' makes grid-based methods like Simpson's Rule computationally impossible for high-dimensional problems, whereas Monte Carlo's error is independent of dimension.
    
    ---
    
    ??? question "14. The error of a Monte Carlo integration estimate decreases with the number of samples $N$ as:"
        - a) $1/N$
        - b) $1/N^2$
        - c) $1/\sqrt{N}$
        - d) $e^{-N}$
    
        ??? info "See Answer"
            - **c) $1/\sqrt{N}$**
            - **Explanation:** This statistical error scaling comes from the Central Limit Theorem and is the method's greatest strength (dimension independence) and weakness (slow convergence).
    
    ---
    
    ??? question "15. What are the three foundational 'pillars' of computational physics developed in Volume I?"
        - a) 1. Algebra, 2. Calculus, 3. Geometry
        - b) 1. Deterministic Solvers, 2. Data-Driven Analysis, 3. Stochastic Modeling.
        - c) 1. Python, 2. C++, 3. Fortran.
        - d) 1. ODEs, 2. PDEs, 3. Linear Algebra.
    
        ??? info "See Answer"
            - **b) 1. Deterministic Solvers, 2. Data-Driven Analysis, 3. Stochastic Modeling.**
            - **Explanation:** This represents the complete toolkit: solving predictable systems, analyzing the resulting data, and modeling systems governed by chance.
    
    ---
    
    ??? question "16. In the Python code `np.random.seed(42)`, what is the purpose of the number 42?"
        - a) It specifies the number of random numbers to generate.
        - b) It is the seed for the PRNG, ensuring that the same sequence of random numbers is generated every time the code is run.
        - c) It sets the upper limit for the random numbers.
        - d) It is a parameter for the LCG algorithm.
    
        ??? info "See Answer"
            - **b) It is the seed for the PRNG, ensuring that the same sequence of random numbers is generated every time the code is run.**
            - **Explanation:** Using a fixed seed is critical for creating reproducible scientific simulations.
    
    ---
    
    ??? question "17. The Monte Carlo methods introduced in this chapter serve as a direct bridge to which major topic in Volume II?"
        - a) General Relativity
        - b) Fluid Dynamics
        - c) Statistical Mechanics (e.g., the Metropolis Algorithm)
        - d) Quantum Field Theory
    
        ??? info "See Answer"
            - **c) Statistical Mechanics (e.g., the Metropolis Algorithm)**
            - **Explanation:** The Metropolis algorithm, a cornerstone of statistical physics simulations, is a sophisticated random walk designed to sample from physical distributions like the Boltzmann distribution.
    
    ---
    
    ??? question "18. Why are simple PRNGs like the Linear Congruential Generator (LCG) now considered inadequate for serious scientific work?"
        - a) They are too slow to compute.
        - b) They can have short periods and statistical correlations that make them non-random for demanding applications.
        - c) They can only generate floating-point numbers.
        - d) They require a hardware key to use.
    
        ??? info "See Answer"
            - **b) They can have short periods and statistical correlations that make them non-random for demanding applications.**
            - **Explanation:** Modern simulations require higher quality PRNGs like the Mersenne Twister to avoid artifacts caused by poor randomness.
    
    ---
    
    ??? question "19. To simulate radioactive decay, where the probability of decay is $p(t) = \lambda e^{-\lambda t}$, the Inverse Transform Method gives the formula $t = -\frac{1}{\lambda} \ln(r)$. What does $r$ represent in this formula?"
        - a) The decay constant $\lambda$.
        - b) The elapsed time $t$.
        - c) A uniform random number between 0 and 1.
        - d) The initial number of nuclei.
    
        ??? info "See Answer"
            - **c) A uniform random number between 0 and 1.**
            - **Explanation:** The formula transforms a uniform random probability `r` into a correctly distributed decay time `t`.
    
    ---
    
    ??? question "20. In the random walk simulation code, why is the simulation run for a large ensemble of `N_WALKERS` instead of just one?"
        - a) To make the code run in parallel and thus faster.
        - b) To obtain a statistical average, as the path of a single walker is random and not representative of the overall diffusive behavior.
        - c) To test different step sizes simultaneously.
        - d) To ensure the total number of steps is large enough.
    
        ??? info "See Answer"
            - **b) To obtain a statistical average, as the path of a single walker is random and not representative of the overall diffusive behavior.**
            - **Explanation:** Statistical physics relies on ensemble averages to extract meaningful, stable properties from noisy microscopic dynamics.
    
    ---
    
    ??? question "21. What does the 'Curse of Dimensionality' refer to?"
        - a) The fact that matrices become singular in high dimensions.
        - b) The exponential increase in the number of grid points required for grid-based methods (like quadrature) as the number of dimensions grows.
        - c) The difficulty of visualizing data in more than three dimensions.
        - d) The tendency for random walks to become trapped in high-dimensional spaces.
    
        ??? info "See Answer"
            - **b) The exponential increase in the number of grid points required for grid-based methods (like quadrature) as the number of dimensions grows.**
            - **Explanation:** This makes grid-based integration computationally impossible for problems with many variables, a problem that Monte Carlo methods solve.
    
    ---
    
    ??? question "22. In the Monte Carlo integration code, the error plot is shown on a log-log scale. A theoretical error scaling of $1/\sqrt{N}$ should appear as a straight line with what slope?"
        - a) -1.0
        - b) -0.5
        - c) 1.0
        - d) 0.5
    
        ??? info "See Answer"
            - **b) -0.5**
            - **Explanation:** If Error $\propto N^{-0.5}$, then $\log(\text{Error}) \propto -0.5 \log(N)$. On a log-log plot, the slope of the line is the exponent.
    
    ---
    
    ??? question "23. Brownian motion, the jittery movement of a pollen grain in water, is a physical example of:"
        - a) A deterministic trajectory.
        - b) A random walk.
        - c) A stable orbit.
        - d) A standing wave.
    
        ??? info "See Answer"
            - **b) A random walk.**
            - **Explanation:** The pollen grain's motion is the macroscopic result of countless random collisions with microscopic water molecules.
    
    ---
    
    ??? question "24. If you double the number of samples $N$ in a Monte Carlo integration, by what factor does the statistical error decrease?"
        - a) A factor of 2.
        - b) A factor of 4.
        - c) A factor of $\sqrt{2}$.
        - d) The error does not decrease.
    
        ??? info "See Answer"
            - **c) A factor of $\sqrt{2}$.**
            - **Explanation:** Since the error scales as $1/\sqrt{N}$, doubling $N$ changes the error by a factor of $1/\sqrt{2N} = (1/\sqrt{N}) \cdot (1/\sqrt{2})$. To halve the error, you must quadruple the number of samples.
    
    ---
    
    ??? question "25. Modern scientific libraries like NumPy use sophisticated PRNGs like the Mersenne Twister instead of simple LCGs primarily because they offer:"
        - a) Faster computation speed.
        - b) Much longer periods and better statistical properties (less correlation).
        - c) The ability to generate numbers in any base.
        - d) A simpler implementation.
    
        ??? info "See Answer"
            - **b) Much longer periods and better statistical properties (less correlation).**
            - **Explanation:** High-quality scientific work requires random numbers that are statistically indistinguishable from true random numbers over very long sequences.
    
    ---
    
    