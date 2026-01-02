
!!! note "Quiz"

    ---
    
    ??? question "1. What is the primary challenge that Principal Component Analysis (PCA) and Singular Value Decomposition (SVD) are designed to address in the context of modern computational physics?"
        - a) Solving non-linear ordinary differential equations.
        - b) The 'Data Deluge' problem: finding dominant, underlying patterns in massive, high-dimensional data matrices.
        - c) Calculating the frequency components of a time-domain signal.
        - d) Ensuring the numerical stability of PDE solvers.
    
        ??? info "See Answer"
            - **b) The 'Data Deluge' problem: finding dominant, underlying patterns in massive, high-dimensional data matrices.**
            - **Explanation:** As simulations produce vast amounts of data (e.g., molecular dynamics trajectories), PCA and SVD are essential for reducing dimensionality and extracting meaningful physical insights from the chaos.
    
    ---
    
    ??? question "2. The Singular Value Decomposition (SVD) factorizes any matrix $\mathbf{X}$ into the product $\mathbf{U} \mathbf{\Sigma} \mathbf{V}^T$. What do the diagonal entries of the $\mathbf{\Sigma}$ matrix represent?"
        - a) The principal components of the data.
        - b) The mean of each column in $\mathbf{X}$.
        - c) The singular values ($\sigma_i$), which quantify the 'importance' or magnitude of each corresponding mode.
        - d) The eigenvectors of the data matrix $\mathbf{X}$.
    
        ??? info "See Answer"
            - **c) The singular values ($\sigma_i$), which quantify the 'importance' or magnitude of each corresponding mode.**
            - **Explanation:** The singular values are sorted in descending order and represent the amount of variance or energy captured by each singular vector, making them crucial for ranking and truncation.
    
    ---
    
    ??? question "3. How does truncated SVD achieve data compression and noise filtering?"
        - a) By increasing the precision of the floating-point numbers in the matrix.
        - b) By keeping only the top $K$ largest singular values and their corresponding vectors, discarding the smaller values which often represent noise.
        - c) By applying a Fourier transform to the data.
        - d) By centering the data around its mean.
    
        ??? info "See Answer"
            - **b) By keeping only the top $K$ largest singular values and their corresponding vectors, discarding the smaller values which often represent noise.**
            - **Explanation:** SVD provides a low-rank approximation of the matrix by retaining the most significant components, effectively compressing the data and filtering out high-frequency noise.
    
    ---
    
    ??? question "4. What is the primary goal of Principal Component Analysis (PCA)?"
        - a) To find the inverse of the data matrix.
        - b) To transform the data into a new, orthogonal basis where the axes (Principal Components) are aligned with the directions of greatest variance.
        - c) To calculate the determinant of the covariance matrix.
        - d) To solve a system of linear equations.
    
        ??? info "See Answer"
            - **b) To transform the data into a new, orthogonal basis where the axes (Principal Components) are aligned with the directions of greatest variance.**
            - **Explanation:** PCA finds the 'natural' axes of a data cloud, allowing for dimensionality reduction and easier interpretation of the system's behavior.
    
    ---
    
    ??? question "5. Mathematically, PCA is achieved by solving the eigenvalue problem for which specific matrix derived from the data $\mathbf{X}$?"
        - a) The original data matrix $\mathbf{X}$ itself.
        - b) The inverse of the data matrix, $\mathbf{X}^{-1}$.
        - c) The Covariance Matrix, $\mathbf{C} \propto \mathbf{X}^T \mathbf{X}$.
        - d) The identity matrix.
    
        ??? info "See Answer"
            - **c) The Covariance Matrix, $\mathbf{C} \propto \mathbf{X}^T \mathbf{X}$.**
            - **Explanation:** The eigenvectors of the symmetric covariance matrix are the principal components, and the eigenvalues represent the variance along those components.
    
    ---
    
    ??? question "6. In the context of PCA, what do the eigenvectors ($\mathbf{v}_i$) and eigenvalues ($\lambda_i$) of the covariance matrix represent?"
        - a) Eigenvectors are the variance; eigenvalues are the principal components.
        - b) Eigenvectors are the principal components (the new axes); eigenvalues are the variance along those axes.
        - c) Eigenvectors are the singular values; eigenvalues are the left singular vectors.
        - d) Both represent the amount of noise in the data.
    
        ??? info "See Answer"
            - **b) Eigenvectors are the principal components (the new axes); eigenvalues are the variance along those axes.**
            - **Explanation:** This is the fundamental mapping between the linear algebra result and the physical interpretation in PCA.
    
    ---
    
    ??? question "7. What is the crucial first step that must be performed on the data matrix $\mathbf{X}$ before calculating the covariance matrix in PCA?"
        - a) Normalize each column to have a unit norm.
        - b) Center the data by subtracting the mean of each column.
        - c) Transpose the matrix.
        - d) Compute its SVD.
    
        ??? info "See Answer"
            - **b) Center the data by subtracting the mean of each column.**
            - **Explanation:** PCA is about variance around the mean, so the data must first be centered to have a mean of zero.
    
    ---
    
    ??? question "8. What is the relationship between the SVD of a data matrix $\mathbf{X}$ and the PCA of that same data?"
        - a) There is no relationship between them.
        - b) The left singular vectors ($\mathbf{U}$) of $\mathbf{X}$ are the principal components.
        - c) The right singular vectors ($\mathbf{V}$) of $\mathbf{X}$ are the principal components (the eigenvectors of $\mathbf{X}^T \mathbf{X}$).
        - d) The singular values are the principal components.
    
        ??? info "See Answer"
            - **c) The right singular vectors ($\mathbf{V}$) of $\mathbf{X}$ are the principal components (the eigenvectors of $\mathbf{X}^T \mathbf{X}$).**
            - **Explanation:** Computing PCA via SVD is often more numerically stable than forming and solving the eigenvalue problem for the covariance matrix directly.
    
    ---
    
    ??? question "9. In analyzing a molecular dynamics trajectory with PCA, what do the first few principal components with the largest eigenvalues typically represent?"
        - a) Random, uncorrelated thermal noise.
        - b) The initial positions of the atoms.
        - c) Coherent, collective physical motions of the system (e.g., rotation, vibration, folding).
        - d) Errors in the simulation's force field.
    
        ??? info "See Answer"
            - **c) Coherent, collective physical motions of the system (e.g., rotation, vibration, folding).**
            - **Explanation:** PCA excels at separating the low-dimensional, large-amplitude collective motions from the high-dimensional, small-amplitude thermal noise.
    
    ---
    
    ??? question "10. When using SVD for image compression, a 500x500 pixel image has 500 singular values. If you reconstruct the image using only the top K=10 singular values, what is the expected result?"
        - a) A perfectly clear image, identical to the original.
        - b) A heavily distorted image with no recognizable features.
        - c) A blurrier but recognizable version of the original image.
        - d) An inverted-color version of the image.
    
        ??? info "See Answer"
            - **c) A blurrier but recognizable version of the original image.**
            - **Explanation:** The top 10 singular values capture the most dominant, low-rank features of the image, preserving its main structure but losing fine details.
    
    ---
    
    ??? question "11. In the Python codebook, which `scipy.linalg` function is used to solve the symmetric eigenvalue problem for the covariance matrix in PCA?"
        - a) `svd()`
        - b) `inv()`
        - c) `eigh()`
        - d) `solve()`
    
        ??? info "See Answer"
            - **c) `eigh()`**
            - **Explanation:** `eigh` is specifically designed for symmetric (or Hermitian) matrices like the covariance matrix, making it faster and more numerically stable than the general `eig` solver.
    
    ---
    
    ??? question "12. After performing PCA, how is the 'explained variance ratio' for each principal component calculated?"
        - a) By dividing each eigenvalue by the number of dimensions.
        - b) By dividing each eigenvalue by the total sum of all eigenvalues.
        - c) By taking the square root of each eigenvalue.
        - d) It is equal to the singular value.
    
        ??? info "See Answer"
            - **b) By dividing each eigenvalue by the total sum of all eigenvalues.**
            - **Explanation:** This ratio shows the percentage of the total data variance that is captured by each individual principal component.
    
    ---
    
    ??? question "13. To project the high-dimensional centered data `X_centered` onto a 2D subspace defined by the first two principal components (PC1, PC2), what matrix operation is performed?"
        - a) `X_reduced = X_centered + [PC1, PC2]`
        - b) `X_reduced = X_centered @ [PC1, PC2]` (Matrix multiplication)
        - c) `X_reduced = X_centered * [PC1, PC2]` (Element-wise multiplication)
        - d) `X_reduced = [PC1, PC2] @ X_centered`
    
        ??? info "See Answer"
            - **b) `X_reduced = X_centered @ [PC1, PC2]` (Matrix multiplication)**
            - **Explanation:** Projecting the data onto the new basis is done by matrix-multiplying the centered data by the matrix whose columns are the desired principal components.
    
    ---
    
    ??? question "14. In the SVD code example for image filtering, the filtered matrix is reconstructed using `X_filtered = U_k @ s_k @ Vt_k`. What does `s_k` represent?"
        - a) The full array of singular values.
        - b) A diagonal matrix containing only the top `K` truncated singular values.
        - c) The first `K` columns of the `U` matrix.
        - d) A single scalar value.
    
        ??? info "See Answer"
            - **b) A diagonal matrix containing only the top `K` truncated singular values.**
            - **Explanation:** The `s` output of `svd` is a 1D array, which must be converted back into a diagonal matrix `s_k` for the reconstruction matrix multiplication.
    
    ---
    
    ??? question "15. If the PCA of a 10-dimensional dataset reveals that 99% of the variance is captured by the first 2 principal components, what does this imply about the data?"
        - a) The data is essentially random noise.
        - b) The data has a true, intrinsic dimensionality of 2, despite being embedded in a 10D space.
        - c) The PCA calculation has failed.
        - d) All 10 dimensions are equally important.
    
        ??? info "See Answer"
            - **b) The data has a true, intrinsic dimensionality of 2, despite being embedded in a 10D space.**
            - **Explanation:** This is a classic sign that the data lies on or near a low-dimensional manifold (like a plane or curve) within the higher-dimensional space.
    
    ---
    
    ??? question "16. The covariance matrix `C` is always:"
        - a) Diagonal
        - b) Invertible
        - c) Symmetric
        - d) An orthogonal matrix
    
        ??? info "See Answer"
            - **c) Symmetric**
            - **Explanation:** The covariance of variable A with B is the same as B with A, making the covariance matrix symmetric. This property guarantees real eigenvalues and orthogonal eigenvectors.
    
    ---
    
    ??? question "17. In the SVD formula $\mathbf{X} = \mathbf{U} \mathbf{\Sigma} \mathbf{V}^T$, what are the properties of the matrices $\mathbf{U}$ and $\mathbf{V}$?"
        - a) They are both diagonal.
        - b) They are both symmetric.
        - c) They are both orthogonal matrices.
        - d) They are both singular.
    
        ??? info "See Answer"
            - **c) They are both orthogonal matrices.**
            - **Explanation:** Orthogonality means their columns (and rows) form orthonormal bases, which is key to their role as basis vectors for the row and column spaces of $\mathbf{X}$.
    
    ---
    
    ??? question "18. When analyzing the sorted eigenvalues from a PCA of a physical system, a sharp 'cliff' in the plot (a few large values followed by a long tail of tiny values) indicates what?"
        - a) A clear separation between coherent physical motion (large eigenvalues) and random noise (small eigenvalues).
        - b) A failure in the eigenvalue solver.
        - c) That the system is purely chaotic with no underlying structure.
        - d) That the data was not centered correctly.
    
        ??? info "See Answer"
            - **a) A clear separation between coherent physical motion (large eigenvalues) and random noise (small eigenvalues).**
            - **Explanation:** This 'spectral gap' is the signature of a system with a low-dimensional set of important dynamics.
    
    ---
    
    ??? question "19. Why is PCA considered a 'data-driven' analysis method?"
        - a) Because it requires a physical model of the system to work.
        - b) Because the new basis vectors (the PCs) are determined entirely by the structure and correlations within the data itself, not by a predefined basis like Fourier analysis.
        - c) Because it only works on data that has been manually cleaned and labeled.
        - d) Because it was invented by data scientists.
    
        ??? info "See Answer"
            - **b) Because the new basis vectors (the PCs) are determined entirely by the structure and correlations within the data itself, not by a predefined basis like Fourier analysis.**
            - **Explanation:** Unlike FFT which uses a fixed sinusoidal basis, PCA finds the optimal basis for a given dataset.
    
    ---
    
    ??? question "20. In the Python code `C = np.cov(X_centered, rowvar=False)`, what is the purpose of the `rowvar=False` argument?"
        - a) It tells the function that the matrix is not square.
        - b) It specifies that each column represents a variable and each row is an observation.
        - c) It prevents the calculation of the variance.
        - d) It tells the function that each row represents a variable and each column is an observation.
    
        ??? info "See Answer"
            - **b) It specifies that each column represents a variable and each row is an observation.**
            - **Explanation:** This is the standard data layout for many scientific and statistical applications, and `np.cov` needs to know which dimension to calculate the covariance across.
    
    ---
    
    ??? question "21. The SVD is described as the 'master factorization' in linear algebra because:"
        - a) It is the fastest algorithm to compute.
        - b) It applies to any arbitrary matrix, regardless of whether it is square, symmetric, or invertible.
        - c) It was the first matrix factorization to be discovered.
        - d) It is only used for data compression.
    
        ??? info "See Answer"
            - **b) It applies to any arbitrary matrix, regardless of whether it is square, symmetric, or invertible.**
            - **Explanation:** Its generality and the complete picture it provides of a matrix's structure make it a fundamental tool.
    
    ---
    
    ??? question "22. If PC1 explains 84% of the variance and PC2 explains 15%, what is the cumulative variance explained by the first two components?"
        - a) 69%
        - b) 84%
        - c) 99%
        - d) 100%
    
        ??? info "See Answer"
            - **c) 99%**
            - **Explanation:** The cumulative variance is the sum of the individual variances (84% + 15% = 99%).
    
    ---
    
    ??? question "23. The three pillars of computation developed in Volume I are Deterministic Solvers, Data-Driven Analysis, and what final ingredient, which is the subject of Chapter 17?"
        - a) Quantum Computing
        - b) Artificial Intelligence
        - c) Randomness (for Monte Carlo methods)
        - d) GPU Programming
    
        ??? info "See Answer"
            - **c) Randomness (for Monte Carlo methods)**
            - **Explanation:** The book builds a toolkit for deterministic systems (solvers), data analysis (FFT/PCA), and finally, probabilistic systems (Monte Carlo).
    
    ---
    
    ??? question "24. When visualizing the singular values of a noisy image matrix on a log-plot, the 'knee' or 'elbow' in the plot often suggests a good rank `K` for truncation. Why?"
        - a) It marks the point where the singular values become zero.
        - b) It indicates the transition point where the singular values stop representing the main signal and start representing noise.
        - c) It is always located at K=10.
        - d) It corresponds to the Nyquist frequency of the image.
    
        ??? info "See Answer"
            - **b) It indicates the transition point where the singular values stop representing the main signal and start representing noise.**
            - **Explanation:** The initial steep drop represents the important structural components, while the long, flat tail represents the noise floor. The 'elbow' is the optimal point to separate them.
    
    ---
    
    ??? question "25. After sorting the eigenvalues and eigenvectors from `eigh`, why is it necessary to reorder the eigenvectors according to the sorted eigenvalue indices (`eigenvectors[:, idx]`)?"
        - a) The `eigh` function does not guarantee that the eigenvalues and their corresponding eigenvectors are returned in the same order.
        - b) The `eigh` function returns eigenvalues in ascending order, but PCA requires them in descending order, so the eigenvectors must be reordered to match.
        - c) The eigenvectors are randomly shuffled by default.
        - d) It is not necessary; the order is always correct.
    
        ??? info "See Answer"
            - **b) The `eigh` function returns eigenvalues in ascending order, but PCA requires them in descending order, so the eigenvectors must be reordered to match.**
            - **Explanation:** To ensure that the first principal component (PC1) corresponds to the largest eigenvalue (variance), both arrays must be sorted in the same descending order.
    
    ---
    
    