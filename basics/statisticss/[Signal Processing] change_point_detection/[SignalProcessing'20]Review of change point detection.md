# [Signal Processing'20] Selective review of offline change point detection methods
1. Link: 
   1. Paper: https://arxiv.org/pdf/1801.00718
   2. Repo: https://centre-borelli.github.io/ruptures-docs/
2. Arthurs and institution: Charles Truonga, Laurent Oudreb, Nicolas Vayatis from CMLA, CNRS, ENS Paris Saclay and L2TI, University Paris 13

**TL;DR**
A selective survey of algorithms for the offline detection of multiple change points in multivariate time series, while it not cover the Bayesian methods.
![alt text](image.png)
## Thoughts and critisims
## Problem formulation
1. data
![alt text](image-1.png)
2. Objective
   ![alt text](image-2.png)
3. Modules
   ![alt text](image-3.png)
   1. Cost function. The cost function c(·) is a measure of “homogeneity”
   2. Search method. The search method is the resolution procedure for the discrete optimization problems associated with Problem 1 (P1) and Problem 2 (P2).
   3. Constraint (on the number of change points). When the number of changes is unknown (P2), a constraint is added, in the form of a complexity penalty pen(·) (P2), to balance out the goodness-of-fit term V (T , y). T
## Key concepts
### Cost function
1. property of estimation
   1. Asymptotic consistency
      1. ![alt text](image-4.png)
2. evaluation
   1. AnnotationError![alt text](image-5.png)
   2. Hausdorf ![alt text](image-6.png)
   3. RandIndex ![alt text](image-7.png)
   4. F1-score ![alt text](image-8.png)
3. Cost functions
   1. parametric
      1. i.i.d. ![alt text](image-9.png)
      2. cost 2: ![alt text](image-10.png)
      3. cost 3: ![alt text](image-11.png)
      4. cost 4: ![alt text](image-12.png)
      5. cost 5: ![alt text](image-13.png)
      6. cost AR: ![alt text](image-14.png)
   2. non-parametric
      1. assume a emperical CDF
         1. ![alt text](image-15.png)
         2. MLE: ![alt text](image-16.png)
            1. cost function: ![alt text](image-17.png)
         3. kernel method: ![alt text](image-18.png)
            1. rbf: ![alt text](image-19.png)
### Search method
#### optimal detection
1. if K is known
   1. dynamic programming ![alt text](image-20.png)
2. if K is unknown
   1. dynamic programming wiht penalty PELT (pruned exact linear time) ![alt text](image-21.png)
#### Approximate detection
1. window slicing
![alt text](image-22.png)
2. binary segmentation
![alt text](image-23.png)
3. Bottom-up segmentation
![alt text](image-24.png)
#### Penalties
![alt text](image-25.png)