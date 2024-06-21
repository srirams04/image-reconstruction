# Image Reconstruction and Compression using Matrix Factorization

The main objective of this project is to reconstruct missing patches in images using **different algorithms** and compare their performance. We explore the effects of patch **size, location, and complexity** on reconstruction quality. 

<p align="center">
<img src="https://github.com/srirams04/image-reconstruction/assets/75443405/5f03458c-0112-4bb6-8f93-82e36fa5dca3" width="60%" height="60%">
</p>


## Tasks and Approaches

### 1. Image Reconstruction

In this task, we explore reconstructing missing regions in images using matrix factorization techniques.

#### 1.1 Reconstructing Specific Regions

We consider two scenarios:
- A rectangular block of 30x30 pixels is missing
- A random subset of 900 (30x30) pixels is missing

Approaches:
- **Matrix Factorization with Gradient Descent**: We decompose the image matrix I into two lower-rank matrices U and V such that I ≈ UV^T. Gradient descent is used to optimize U and V, minimizing the reconstruction error.
- **Random Fourier Features (RFF) with Linear Regression**: RFF is used to approximate kernel methods efficiently. We map the input to a higher-dimensional space using random Fourier features and then apply linear regression for reconstruction.

Metrics:
- Mean Squared Error (MSE)
- Peak Signal-to-Noise Ratio (PSNR)

#### 1.2 Varying Region Size

We extend the analysis by varying the size of the missing region:
N x N, where N = [20, 40, 60, 80]

Both scenarios (rectangular block and random subset) are considered for each size.

#### 1.3 Alternating Least Squares (ALS)

We implement the ALS algorithm as an alternative to gradient descent. ALS alternates between fixing U and solving for V, then fixing V and solving for U. This method often converges faster than gradient descent for matrix factorization problems.

### 2. Data Compression

In this task, we explore using matrix factorization for efficient image storage and compression.

#### 2.1 Compressing Image Patches

We consider a 50x50 image patch and compress it using low-rank matrix factorization. Three types of patches are analyzed:
1. Patch with mainly a single color
2. Patch with 2-3 different colors
3. Patch with at least 5 different colors

Approach:
- **Low-Rank Matrix Factorization**: We decompose the patch matrix P into two smaller matrices U and V such that P ≈ UV^T. The rank r determines the level of compression.

We vary the low-rank value: r = [5, 10, 25, 50]

## Techniques Used

### Matrix Factorization
Matrix factorization decomposes a matrix into the product of two or more matrices. In our case, we use it to approximate the original image or patch with lower-rank matrices, which can be used for both reconstruction and compression.

### Gradient Descent
Gradient descent is an optimization algorithm used to minimize the reconstruction error. It iteratively updates the factorized matrices U and V in the direction that reduces the error most rapidly.

### Random Fourier Features (RFF)
RFF is a technique used to approximate kernel methods. It maps input data to a higher-dimensional space using randomly sampled Fourier features, allowing for efficient computation of kernel-based algorithms.

### Alternating Least Squares (ALS)
ALS is an iterative algorithm for matrix factorization. It alternates between fixing one factor matrix and optimizing the other, which often leads to faster convergence compared to gradient descent for certain problems.

## Implementation Details

Check out `main.ipynb` for thorough implementation of various approaches, accompanied by visual plots and insightful comparisons.

## Acknowledgements

This project was completed as part of the Machine Learning course under [Prof. Nipun Batra](https://nipunbatra.github.io/) at IIT Gandhinagar. The course materials and discussions were instrumental in developing a good understanding of these machine learning concepts and their applications in image processing.


