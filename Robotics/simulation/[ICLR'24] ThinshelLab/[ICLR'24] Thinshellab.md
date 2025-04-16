# [ICLR'24] Thin-Shell Object Manipulations With Differentiable Physics Simulations
1. Link: https://arxiv.org/abs/2404.00451
2. Arthurs and institution: Yian Wang, Juntian Zheng, Zhehuan Chen, Zhou Xian, Gu Zhang, Chao Liu, Chuang Gan from UMass and MIT-IBM

**NOTE**
1. Chuang Gan(淦创): The corresponding arthur of GENESIS, this is one of his previous jobs.
2. Zhou Xian: first arthur of GENESIS
3. 
**TL;DR**
A fully differentiable simulation platform tailored for robotic interactions with diverse thin-shell materials possessing varying material properties.  This endeavor encompasses a triad of manipulation tasks, inverse design tasks, and real-world experiments. 

## Contributions
1.  We introduce ThinShellLab, a comprehensive benchmark for robotic learning in thin-shell material manipulation. The benchmark provides a diverse collection of manipulation tasks and a standardized interface for RL and trajectory optimization algorithms.
2. A fully differentiable simulation engine supporting volumetric and thin-shell deformable objects and coupling between them. To the best of our knowledge, it is the first simulation environment capable of conducting gradient-based optimization on thin-shell object manipulation tasks.
3. We demonstrate how our differentiable simulator can help solving inverse design problem, and bridge the simulation scenes and the real-world robotics. We show the the simulator’s capability of reconstructing real-world physics scene parameters via gradient, and deploying learned skills to real robots.
## Related Work
### Differentiable Simulation
1. train neural networks predicting forward dynamics
   1. most recent: [NeurIPS'22] Jiaqi Han, ...,J.B. Tenenbaum, Chuang Gan, Learning physical dynamics with subequivariant graph neural networks
   2. drawbacks
      1. collecting a large amount of data
      2. suffers from problems on generalizability
      3. large sim-to-real gap
2.  a simulation system and integrate gradient calculation into the system
    1.  auto-diff for explicit time integration
        1.  most recent
            1.  difftaichi
            2.  
### Thin-Shell Object Manipulation
## Key points
### Comparison on key features with several simulators
![alt text](image.png)
### DaX
1. objects
   1. rope, cloth, liquid, and elasto-plastic materials
2. gradient calculation:  autodifferentiation and parallelization across multiple accelerators
3. env
   1. wrapped as OpenAI Gym API
4. State Representations
   1. MLS-MPM with particles
      1. liquid and rope
   2. mass-spring system
5. Forward tricks
   1. lazy dynamic update: only update particles of interest
   2. checkpointing method: only stores the values of a few states (i.e. checkpoints), and re-evaluates the sub-step gradients online during the back-propagation to reduce the memory consumption for long horizon problems
6. Discontinous gradient
   1. the gradient of non-contacted action is discontinous
   2. leads to a poor estimation of gradient during BP
   3. let actions always make the gripper in contact with the deformable objects
   
### Benchmark tasks
1. tasks
   1. Pour-Water
   2. Pour-soup
   3. Push-Rope
   4. Whip-Rope
   5. Fold-Cloth
   6. Fold-T-shirt
   7. Unfold-Cloth