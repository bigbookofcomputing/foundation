## 📙 Volume I — The Foundation of Computing


### Part I — The Digital Workbench

??? note "Chapter 1 — The Physicist’s “Digital Lab Notebook”   |   <a href='chapters/chapter-1/read'>📖 Read</a>   |   <a href='chapters/chapter-1/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-1/codebook'>💻 Codebook</a>"
    
    *A chapter on how scientists structure, document, and maintain computational work for clarity and reproducibility.*
    
    ??? note "1.1 Why Scientists Compute"
        
        Scientists compute to explore models, test hypotheses, and analyze data computationally when analytic solutions are insufficient.

    ??? note "1.2 From Analytic to Numeric Thinking"
        
        This section explains how scientific problems shift from symbolic manipulations to approximation-based numerical reasoning.

    ??? note "1.3 Floating-Point Machines: A First Look"
        
        A gentle introduction to how computers represent numbers and why precision limits matter.

    ??? note "1.4 Reproducibility & Computational Hygiene"
        
        This section introduces best practices that ensure computational results can be repeated, verified, and extended.
        
        ##### 1.4.1 Notebooks vs Scripts  
        ##### 1.4.2 Version Control Basics  
        ##### 1.4.3 The Importance of Metadata  


??? note "Chapter 2 — The Nature of Computational Numbers   |   <a href='chapters/chapter-2/read'>📖 Read</a>   |   <a href='chapters/chapter-2/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-2/codebook'>💻 Codebook</a>"
    
    *A chapter on how computers represent numbers and the fundamental errors that arise from doing arithmetic digitally.*
    
    ??? note "2.1 Number Systems and Computer Representation"
        
        A survey of how integers and floating-point numbers are encoded and manipulated inside digital hardware.
        
        ##### 2.1.1 Integers  
        ##### 2.1.2 Floating-Point Format  
        ##### 2.1.3 Machine Precision  

    ??? note "2.2 Roundoff Error"
        
        Roundoff error arises because finite-precision arithmetic introduces unavoidable discrepancies between real numbers and their representations.
        
        ##### 2.2.1 Absolute and Relative Error  
        ##### 2.2.2 Catastrophic Cancellation  

    ??? note "2.3 Stability in Computation"
        
        Stability measures how errors grow during computation and distinguishes reliable algorithms from fragile ones.
        
        ##### 2.3.1 Conditioning of Problems  
        ##### 2.3.2 Stability of Algorithms  

    ??? note "2.4 When Computers Lie: Pitfalls & Examples"
        
        Shows real situations where floating-point arithmetic behaves unintuitively or deceptively.


??? note "Chapter 3 — Finding Order in Chaos: Root Finding   |   <a href='chapters/chapter-3/read'>📖 Read</a>   |   <a href='chapters/chapter-3/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-3/codebook'>💻 Codebook</a>"
    
    *A chapter on numerical strategies for solving equations by identifying where functions cross zero.*
    
    ??? note "3.1 What It Means to Find a Root"
        
        Root-finding searches for solutions to equations of the form f(x) = 0, fundamental in science and engineering.

    ??? note "3.2 Bracketing Methods"
        
        Bracketing methods guarantee convergence by enclosing a root between two points.
        
        ##### 3.2.1 Bisection  
        ##### 3.2.2 False Position  

    ??? note "3.3 Open Methods"
        
        Open methods converge faster but rely on good starting values and may fail without careful use.
        
        ##### 3.3.1 Newton’s Method  
        ##### 3.3.2 Secant Method  

    ??? note "3.4 Convergence & Stability"
        
        This section details how quickly root-finding algorithms converge and when they remain reliable.

    ??? note "3.5 Practical Considerations"
        
        Practical pitfalls—like poor initial guesses and non-smooth functions—affect real-world performance.


??? note "Chapter 4 — Working with Data: Interpolation & Fitting   |   <a href='chapters/chapter-4/read'>📖 Read</a>   |   <a href='chapters/chapter-4/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-4/codebook'>💻 Codebook</a>"
    
    *A chapter introducing ways to construct functions from data, either exactly (interpolation) or approximately (fitting).*
    
    ??? note "4.1 Interpolation Fundamentals"
        
        Interpolation constructs smooth functions that exactly pass through known data points.
        
        ##### 4.1.1 Polynomial Interpolation  
        ##### 4.1.2 Piecewise Interpolation  

    ??? note "4.2 Spline Theory & Practice"
        
        Splines provide smooth, stable interpolation by stitching low-degree polynomials together.

    ??? note "4.3 Curve Fitting & Regression"
        
        Fitting derives approximate models from imperfect data using optimization and statistics.

    ??? note "4.4 Error Analysis"
        
        This section explains how interpolation and fitting errors arise and how to estimate them.

---

### Part II — The Computational Tools of Calculus

??? note "Chapter 5 — Numerical Differentiation   |   <a href='chapters/chapter-5/read'>📖 Read</a>   |   <a href='chapters/chapter-5/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-5/codebook'>💻 Codebook</a>"
    
    *A chapter on approximating derivatives when only discrete data or function samples are available.*
    
    ??? note "5.1 Finite Difference Approximations"
        
        Finite differences estimate derivatives by comparing function values at nearby points.

    ??? note "5.2 Truncation Error"
        
        Truncation errors arise when infinite series are approximated with finite expressions.

    ??? note "5.3 High-Order Formulas"
        
        Higher-order difference formulas improve accuracy at the cost of more computation.

    ??? note "5.4 Differentiation of Noisy Data"
        
        Differentiation amplifies noise, requiring smoothing or specialized techniques.


??? note "Chapter 6 — Numerical Integration (Quadrature)   |   <a href='chapters/chapter-6/read'>📖 Read</a>   |   <a href='chapters/chapter-6/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-6/codebook'>💻 Codebook</a>"
    
    *A chapter on methods to approximate definite integrals using weighted sums of function values.*
    
    ??? note "6.1 Riemann Sums"
        
        Riemann sums introduce numerical integration by summing areas of simple geometric shapes.

    ??? note "6.2 Newton–Cotes Formulas"
        
        Newton-Cotes formulas approximate integrals by interpolating the integrand with polynomials.
        
        ##### 6.2.1 Trapezoidal  
        ##### 6.2.2 Simpson  

    ??? note "6.3 Gaussian Quadrature"
        
        Gaussian quadrature achieves high accuracy using optimally chosen evaluation points.

    ??? note "6.4 Monte Carlo Integration"
        
        Monte Carlo techniques estimate integrals using randomness, ideal for high-dimensional problems.

    ??? note "6.5 Error Bounds & Convergence"
        
        This section explores how integral approximations converge and how to bound their errors.

---

### Part III — Evolving Systems: Ordinary Differential Equations

??? note "Chapter 7 — Initial Value Problems I: The Basics   |   <a href='chapters/chapter-7/read'>📖 Read</a>   |   <a href='chapters/chapter-7/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-7/codebook'>💻 Codebook</a>"
    
    *A chapter on solving differential equations where the solution evolves from a known starting point.*
    
    ??? note "7.1 ODEs in Physics"
        
        Physical systems often evolve according to differential laws describable by ODEs.

    ??? note "7.2 Euler’s Method"
        
        Euler’s method gives a simple but low-accuracy approach to evolving differential systems.

    ??? note "7.3 Runge–Kutta Methods"
        
        Runge–Kutta schemes achieve higher accuracy by sampling the system multiple times per step.

    ??? note "7.4 Step-Size Control"
        
        Adaptive step-size methods adjust resolution on the fly to improve stability and efficiency.


??? note "Chapter 8 — Initial Value Problems II: Leapfrog & Verlet   |   <a href='chapters/chapter-8/read'>📖 Read</a>   |   <a href='chapters/chapter-8/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-8/codebook'>💻 Codebook</a>"
    
    *A chapter on symplectic integrators that preserve geometric properties of physical systems.*
    
    ??? note "8.1 Symplectic Integrators"
        
        Symplectic schemes conserve physical invariants like momentum and energy over long simulations.

    ??? note "8.2 Energy Conservation in Numerical Orbits"
        
        Numerical orbits benefit from integrators that avoid long-term drift in energy.

    ??? note "8.3 The Verlet Family"
        
        Verlet methods implement stable, efficient updates used widely in mechanics and molecular dynamics.

    ??? note "8.4 Molecular Dynamics Applications"
        
        Verlet-type schemes power large-scale simulations of particle systems and materials.


??? note "Chapter 9 — Boundary Value Problems   |   <a href='chapters/chapter-9/read'>📖 Read</a>   |   <a href='chapters/chapter-9/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-9/codebook'>💻 Codebook</a>"
    
    *A chapter on solving differential equations where values are specified at multiple boundaries.*
    
    ??? note "9.1 What Makes BVPs Different"
        
        Boundary value problems require matching constraints at two or more points, unlike initial value problems.

    ??? note "9.2 Shooting Method"
        
        The shooting approach converts BVPs into IVPs that are tuned to match boundary conditions.

    ??? note "9.3 Finite Difference Method"
        
        Finite difference grids transform differential equations into solvable algebraic systems.

    ??? note "9.4 Eigenvalue-Type BVPs"
        
        Many BVPs lead to eigenvalue problems with physically meaningful modes or frequencies.

---

### Part IV — Fields and Grids: Partial Differential Equations

??? note "Chapter 10 — Elliptic PDEs   |   <a href='chapters/chapter-10/read'>📖 Read</a>   |   <a href='chapters/chapter-10/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-10/codebook'>💻 Codebook</a>"
    
    *A chapter focused on steady-state systems described by elliptic equations like Poisson and Laplace.*
    
    ??? note "10.1 Laplace & Poisson Equations"
        
        Elliptic equations describe equilibrium systems such as electrostatic fields and steady heat flow.

    ??? note "10.2 Discretization on Grids"
        
        Grid-based methods approximate continuous fields with lattice-based finite differences.

    ??? note "10.3 Relaxation Methods"
        
        Relaxation iteratively improves approximate solutions to elliptic equations.

    ??? note "10.4 Multigrid Techniques"
        
        Multigrid accelerates convergence by operating across many spatial scales.


??? note "Chapter 11 — Parabolic PDEs   |   <a href='chapters/chapter-11/read'>📖 Read</a>   |   <a href='chapters/chapter-11/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-11/codebook'>💻 Codebook</a>"
    
    *A chapter on time-dependent diffusion-type systems described by parabolic equations.*
    
    ??? note "11.1 The Heat Equation"
        
        The canonical parabolic PDE models diffusion processes across physics and engineering.

    ??? note "11.2 Explicit Methods"
        
        Explicit time-stepping is simple but constrained by stability limits.

    ??? note "11.3 Implicit Methods"
        
        Implicit schemes allow larger time steps at the cost of solving linear systems.

    ??? note "11.4 Stability & the CFL Condition"
        
        The CFL condition governs when numerical solutions remain stable.


??? note "Chapter 12 — Hyperbolic PDEs   |   <a href='chapters/chapter-12/read'>📖 Read</a>   |   <a href='chapters/chapter-12/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-12/codebook'>💻 Codebook</a>"
    
    *A chapter on wave-like systems governed by hyperbolic equations.*
    
    ??? note "12.1 Wave Equation Basics"
        
        Hyperbolic PDEs govern wave propagation, signaling, and transport phenomena.

    ??? note "12.2 Finite Difference Schemes"
        
        Difference stencils approximate spatial and temporal derivatives for evolving wave fields.

    ??? note "12.3 Upwinding"
        
        Upwind schemes handle directional information to reduce numerical oscillations.

    ??? note "12.4 Discontinuities & Shocks"
        
        Hyperbolic systems can form discontinuities that require shock-capturing techniques.

---

### Part V — The Language of Physics: Linear Algebra

??? note "Chapter 13 — Systems of Linear Equations   |   <a href='chapters/chapter-13/read'>📖 Read</a>   |   <a href='chapters/chapter-13/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-13/codebook'>💻 Codebook</a>"
    
    *A chapter on solving linear systems, the computational core of numerical methods.*
    
    ??? note "13.1 Gaussian Elimination"
        
        Gaussian elimination provides a systematic approach to solving dense linear systems.

    ??? note "13.2 LU Decomposition"
        
        LU factorization breaks matrices into simpler components for repeated solves.

    ??? note "13.3 Iterative Methods"
        
        Iterative solvers handle large sparse systems efficiently.

    ??? note "13.4 Conditioning of Linear Systems"
        
        Conditioning measures how sensitive solutions are to errors in input data.


??? note "Chapter 14 — Eigenvalue Problems   |   <a href='chapters/chapter-14/read'>📖 Read</a>   |   <a href='chapters/chapter-14/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-14/codebook'>💻 Codebook</a>"
    
    *A chapter on finding eigenvalues and eigenvectors, essential across physics and applied math.*
    
    ??? note "14.1 What Eigenvalues Mean in Physics"
        
        Eigenvalues describe natural modes, frequencies, and stability properties of physical systems.

    ??? note "14.2 The Power Method"
        
        The power method extracts dominant eigenvalues through repeated iteration.

    ??? note "14.3 The QR Algorithm"
        
        QR iteration computes full eigenvalue spectra efficiently and reliably.

    ??? note "14.4 Symmetric Matrices & Spectral Theory"
        
        Symmetric matrices yield real eigenvalues and orthogonal eigenvectors with physical significance.

---

### Part VI — Analyzing Signals & Data

??? note "Chapter 15 — Fourier Analysis & the FFT   |   <a href='chapters/chapter-15/read'>📖 Read</a>   |   <a href='chapters/chapter-15/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-15/codebook'>💻 Codebook</a>"
    
    *A chapter on representing signals using frequency components and computing transforms efficiently.*
    
    ??? note "15.1 Fourier Series"
        
        Fourier series express periodic functions as sums of sines and cosines.

    ??? note "15.2 Fourier Transform"
        
        The Fourier transform decomposes signals into continuous frequency spectra.

    ??? note "15.3 The Discrete Transform"
        
        The DFT enables numerical frequency analysis of sampled signals.

    ??? note "15.4 FFT Implementation & Complexity"
        
        The FFT accelerates DFT computation from quadratic to near-linear time.


??? note "Chapter 16 — Data-Driven Analysis: SVD & PCA   |   <a href='chapters/chapter-16/read'>📖 Read</a>   |   <a href='chapters/chapter-16/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-16/codebook'>💻 Codebook</a>"
    
    *A chapter introducing methods to extract structure from high-dimensional data.*
    
    ??? note "16.1 Singular Value Decomposition"
        
        SVD factors matrices into interpretable geometric components.

    ??? note "16.2 Principal Component Analysis"
        
        PCA reduces dimensionality by identifying dominant variance directions.

    ??? note "16.3 Dimensionality Reduction"
        
        Dimensionality reduction compresses data while preserving meaningful structure.

    ??? note "16.4 Applications in Modern Physics"
        
        Data-driven techniques reveal patterns in experiments, simulations, and signals.


??? note "Chapter 17 — Randomness in Physics   |   <a href='chapters/chapter-17/read'>📖 Read</a>   |   <a href='chapters/chapter-17/workbook'>📘 Workbook</a>   |   <a href='chapters/chapter-17/codebook'>💻 Codebook</a>"
    
    *A chapter about randomness, probability, and simulation-based modeling in physical systems.*
    
    ??? note "17.1 Random Variables & Distributions"
        
        Probability distributions describe uncertainty and natural fluctuations.

    ??? note "17.2 Monte Carlo Models"
        
        Monte Carlo simulations model stochastic systems using random sampling.

    ??? note "17.3 Stochastic Differential Equations"
        
        SDEs describe systems driven by both deterministic and random forces.

    ??? note "17.4 Noise in Measurement Systems"
        
        Measurement noise arises from physical, electronic, and statistical sources.




