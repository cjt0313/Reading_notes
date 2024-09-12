# [CVPR'24] Driving Everywhere with Large Language Model Policy Adaptation

1. Link:
   1. paper: https://openaccess.thecvf.com/content/CVPR2024/papers/Li_Driving_Everywhere_with_Large_Language_Model_Policy_Adaptation_CVPR_2024_paper.pdf
   2. youtube: https://www.youtube.com/watch?v=fQ3HJbEkP4U
   3. bilibili(w/less informed): https://www.bilibili.com/video/BV16y411h7eG/?spm_id_from=333.999.0.0&vd_source=0340bcb393969ab1f8766419a9956fcf
   4. git(empty, 24.08): https://github.com/Boyiliee/llada

2. Arthurs: Boyi Li, ..., Marco Pavone team (Nvidia, Stanford)

3. TL;DR: A LLM-as-planner framework that use LLM to facilitate traffic-rule interpretations, capable for serving as a driver assitant or a planner-checker in the AD system. The inputs of the framework are ego state, observation description and traffic handbook, the output of is one-step high level plan.

4. [jintian] questions
   1. The idea of providing guidance to drivers is great; however, the questionare-based experiment only test the validness of LLVDA, does this function require time sensitivity? (e.g. warning the driver not turning right before he do so.) If so, how does the module address it?
## Existing problems

### Traffic Rules in AV Planning.
1. Expressing the entire traffic law is not scalable.
2. Adapting to new traffic rules is difficult.
### LLMs for Robotic Reasoning.
1.  However, the key difference is that our method focuses on policy
adaptation via LLMs rather than the wholesale replacement
of modules with LLMs.
### LLMs for Autonomous Driving.
1. Traditional perception and planning modules in AV system are generally non-adaptive, preventing AVs from generalizing to any in-the-wild domain.
2. For solving out-of-domain generalization and detection problems, majority of LLM works focus on low-level tasks.

## Contribution
![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/5408441331.jpg)
1. A training-free mechanism to assist
human drivers and adapt autonomous driving policies to
new environments by distilling leveraging the zero-shot
generalizability of LLMs.
## Details
1. together with llm planner
 ![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/5753320421.jpg)
2. questionare design
![alt text](../../../Documents/xwechat_files/cjt171333003_a4ad/temp/snapshot/1843287411.jpg)