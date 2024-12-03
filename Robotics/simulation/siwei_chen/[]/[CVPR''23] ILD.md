# [CVPR'23] Imitation Learning as State Matching via Differentiable Physics
1. Link: https://github.com/sail-sg/ILD
2. Arthurs and institution: Siwei Chen, Xiao Ma, Zhongwen Xu from NUS and Sea AI Lab
**TL;DR**
We propose an imitation learning method that incorporates the differentiable physics simulator as a physics prior into its computational graph for policy learning.
# comments and critisim
1. how does the quality of gradient may affect policy learning process?

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