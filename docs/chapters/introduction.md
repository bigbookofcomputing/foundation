# **Welcome to *Foundations of Computation***

*A modern guide to the numerical, computational, and mathematical tools that power the physical sciences.*

Computational science has become the central engine of modern discovery. From modeling planetary orbits to simulating molecular dynamics, from solving Maxwell’s equations on a grid to analyzing massive datasets from experiments, computation is now as essential as theory and experiment themselves. This book introduces the mathematical foundations, numerical techniques, and computational workflows that every scientist, engineer, and researcher needs to work effectively in the digital era.

Whether you are a student encountering scientific computation for the first time or a practitioner seeking a deeper conceptual grounding, this book provides an integrated journey—from floating-point numbers and algorithms to differential equations, numerical integration, simulations, and data-driven analysis. Each chapter is paired with a **Workbook** and **Codebook** to help you immediately apply the concepts through exercises and real computational workflows.

---

### **How This Book Is Structured**

This book is divided into **six parts**, each representing a core pillar of computational science.
Below you’ll find an overview of each part, including a descriptive summary and a **compact part-level table** listing chapters and their key ideas.

---

### **Part I — The Digital Workbench**

#### *How scientists think, compute, document, and structure their numerical work.*

Part I builds your computational intuition. Before worrying about algorithms, we must understand the *environment* and *numerical reality* in which computation takes place. These chapters introduce floating-point arithmetic, reproducible workflows, error sources, and the conceptual ideas behind numerical methods.

#### **Summary Table — Part I**

| **Chapter** | **Title**                              | **Key Ideas**                                                                                 |
| ----------- | -------------------------------------- | --------------------------------------------------------------------------------------------- |
| **1**       | The Physicist’s “Digital Lab Notebook” | Reproducible workflows; computational hygiene; documentation; metadata; notebooks vs scripts. |
| **2**       | The Nature of Computational Numbers    | Floating-point representation; precision; roundoff error; error amplification.                |
| **3**       | Finding Order in Chaos: Root Finding   | Bracketing & open methods; convergence; sensitivity; numerical stability of solvers.          |
| **4**       | Interpolation & Fitting                | Polynomial & spline interpolation; curve fitting; modeling structured & noisy data.           |

---

### **Part II — The Computational Tools of Calculus**

#### *How computers differentiate, integrate, approximate, and accumulate change.*

Part II covers numerical analogs of calculus. You will learn how derivatives are approximated, how integrals are evaluated, and how algorithmic accuracy depends on error scaling and sampling strategies. This part forms the bridge between theory and simulation.

#### **Summary Table — Part II**

| **Chapter** | **Title**                 | **Key Ideas**                                                                             |
| ----------- | ------------------------- | ----------------------------------------------------------------------------------------- |
| **5**       | Numerical Differentiation | Finite differences; truncation error; smooth vs noisy data; high-order stencils.          |
| **6**       | Numerical Integration     | Newton–Cotes rules; Gaussian quadrature; Monte Carlo methods; integration error analysis. |

---

### **Part III — Evolving Systems: Ordinary Differential Equations**

#### *How we simulate time evolution, motion, decay, oscillation, and dynamical systems.*

Part III introduces numerical ODE solvers—methods that evolve physical systems in time. From simple Euler updates to energy-preserving symplectic integrators, this part teaches you how numerical time evolution works and why stability matters.

#### **Summary Table — Part III**

| **Chapter** | **Title**                                    | **Key Ideas**                                                                 |
| ----------- | -------------------------------------------- | ----------------------------------------------------------------------------- |
| **7**       | Initial Value Problems I: The Basics         | Euler & Runge–Kutta methods; step-size control; modeling dynamic systems.     |
| **8**       | Initial Value Problems II: Leapfrog & Verlet | Symplectic integrators; long-term stability; molecular dynamics applications. |
| **9**       | Boundary Value Problems                      | Shooting method; finite-difference BVPs; eigenvalue-type problems.            |

---

### **Part IV — Fields & Grids: Partial Differential Equations**

#### *How we discretize space, model fields, and simulate heat, waves, and steady-state systems.*

Part IV explores PDEs—fundamental equations governing fields in physics. You will learn how to discretize space, construct numerical schemes, stabilize solvers, and treat discontinuities such as shocks.

#### **Summary Table — Part IV**

| **Chapter** | **Title**       | **Key Ideas**                                                                        |
| ----------- | --------------- | ------------------------------------------------------------------------------------ |
| **10**      | Elliptic PDEs   | Laplace/Poisson equations; grid discretization; relaxation & multigrid acceleration. |
| **11**      | Parabolic PDEs  | Heat equation; explicit & implicit time-stepping; CFL stability.                     |
| **12**      | Hyperbolic PDEs | Wave propagation; upwinding; handling discontinuities and shocks.                    |

---

### **Part V — The Language of Physics: Linear Algebra**

#### *How matrices, linear systems, and eigenvalues form the backbone of modern computational physics.*

Part V introduces the linear algebraic machinery underlying numerical solvers, PDE methods, optimization, and data analysis. These methods appear throughout computational science.

#### **Summary Table — Part V**

| **Chapter** | **Title**                   | **Key Ideas**                                                                          |
| ----------- | --------------------------- | -------------------------------------------------------------------------------------- |
| **13**      | Systems of Linear Equations | Gaussian elimination; LU decomposition; iterative solvers; conditioning.               |
| **14**      | Eigenvalue Problems         | Spectral theory; power method; QR algorithm; symmetric matrices & physical eigenmodes. |

---

### **Part VI — Analyzing Signals & Data**

#### *How we understand time series, frequency content, dimensionality, and randomness.*

Part VI concludes the book with modern computational tools for analyzing data and signals. Fourier methods, PCA, SVD, and stochastic methods—core tools of modern research—are introduced here.

#### **Summary Table — Part VI**

| **Chapter** | **Title**                       | **Key Ideas**                                                              |
| ----------- | ------------------------------- | -------------------------------------------------------------------------- |
| **15**      | Fourier Analysis & the FFT      | Fourier series; continuous & discrete transforms; FFT efficiency.          |
| **16**      | Data-Driven Analysis: SVD & PCA | Singular values; dimensionality reduction; structure discovery in data.    |
| **17**      | Randomness in Physics           | Probability distributions; Monte Carlo; stochastic differential equations. |

---

### **What You Will Gain From This Book**

By the end of *Foundations of Computation*, you will be able to:

* Understand the numerical behaviors and limitations of computers.
* Implement and analyze classical numerical algorithms.
* Model and simulate physical systems using ODEs and PDEs.
* Work effectively with large systems, matrices, eigenvalue problems, and spectral methods.
* Apply Fourier transforms, PCA/SVD, and random methods in scientific data analysis.
* Build reproducible, well-structured, professional computational workflows.

This book is designed to be both **a structured course** and **a long-term reference**—a companion to your research, teaching, and computational practice.




