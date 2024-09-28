# 1. Dynamic 3D Gaussian Tracking for Graph-Based Neural Dynamics Modeling
1. Links
   1. https://arxiv.org/pdf/2406.10788
   2. https://gaussian-gbnd.github.io/
2. Authors: Mingtong Zhang, Kaifeng Zhang, Yunzhu Li (AP)
3. Affliations: Columbia University
4. TL;DR: A framework that combines a PBD model with 3DGS, enabling the training of dynamics models using unlabeled multi-view (posed) video observations.

**TODO**
1. read Dyn3DGS (Luiten, J., Kopanas, G., Leibe, B. and Ramanan, D., 2023. Dynamic 3d Gaussians: Tracking by persistent dynamic view synthesis. arXiv preprint arXiv:2308.09713.)
2. read nn-based simulator (P. Ma, P. Y. Chen, B. Deng, J. B. Tenenbaum, T. Du, C. Gan, and W. Matusik. Learning neural constitutive laws from motion observations for generalizable pde dynamics. In International Conference on Machine Learning, pages 23279–23300. PMLR, 2023.)

## Existing problem
### Dynamics Modeling of Real-World Objects
1. For those who use physics-based simulator to get (gradient free/based) physical params, they require accurate perception to transfer real to sim.
2. NN based simulators learn dynamics w/o analytical model.

## Contributions
1. A mechanism that combines gaussian seeds with particles from PBD, captures both visual and physical information about the scene
2. A real-time method to correct the particle states using visual feedback
## Key concepts
1. Dynamic 3D Gaussian Splatting with Dense Tracking
   1. Resources:
      1. original paper: https://matthias-research.github.io/pages/publications/posBasedDyn.pdf
      2. tutorial from original author: https://matthias-research.github.io/pages/publications/PBDTutorial2017-CourseNotes.pdf
      3. useful blog: https://carmencincotti.com/2022-07-11/position-based-dynamics/
   2. Algorithm
      1. ![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/5632566727.jpg)
         1. Initialize each particle with position, rotation, mass, linear and angular velocities
         2. given applied force, solve uncorrected position for each particle
         3. solve contraints (nonlinear, inequality/equality)
         4. update positions
      2. These can be parallelized
2. Gaussian splatting
   1. ![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/5521929236.jpg)
   2. The authors transformed point clouds to gaussians with a similiar approach to GaussianGrasper(RAL'24).
## Details
### Initialization
#### Gaussians
1. use tools to get object instance label and 3D-BBOX
2. filled with Gaussians(r = 4-7mm, $\Sigma=I$)
3. solving positions, colors and opacities by PBD
4. training with photometric and segmentation reconstruction loss
![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/2547599691.jpg)
1. prune gaussians with $\mathit{I}_{\alpha_i \leq 0.3}$
#### Particles
1. init. with given position
2. align them with shape constraint ![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/4848082805.jpg)
#### Refinement
1. optimize gaussians, add more gaussians
2. remove gaussians far from particles
### Online Prediction
1. use FK to get positions of particles for the robot
2. use PBD to get predicted positions of particles
### Online Correction
1. update gaussians those are only attached on objects by photometric reconstruction loss from given camera viewpoints.
2. reset the gaussian to original position
3. compute the imposed force of each particle ![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/2079622739.jpg)

