### 我需要知道什么

1. 论文目的
2. 评价体系
3. 结构体系
4. 训练和预测过程
5. 提升结果
6. 结论 and why does it work?
7. 缺点和可以改进的地方



### Online Multi-Object Tracking by Decision Making

1. Online MOT

   **challenge** : how to robustly associate noisy object detections on a new video frame with perviously tracked object. how to handle the birth/death and appearance/disappearance of targets

   **Method** : learning a policy for the MDP

   **dateset** : MOT Benchmark

   **application** : autonomous driving and robot navigation

2. multiple metrics suggested by the MOT Benchmark

3. Reinforcement learning both offline and online

   1) learning in our method is conducted offline so as to utilize supervision from ground truth trajectories

   2) learning in our method takes place while tracking objects in training sequences, so the MDP is able to make the decision based on both the current status and the history of the target

   3) training is finished when the MDP can successfully track the target

4. We have proposed a novel online multi-object tracking framework based on Markov decision processes, where the lifetime of an object is modeled with a MDP with four subspaces of states (Active, Tracked, Lost and Inactive). The state transitions in the MDP naturally handle the birth/death and appearance/disappearance of objects in tracking. A similarity function for data association is learned as part of the MDP policy with reinforcement learning. Our framework is general to be integrated with different techniques in object detection, single object tracking and data association by using them for MDP policy learning. We have tested our implementation of the tracking framework on the challenging MOT Benchmark, which outperforms the state-of-the-art methods tested on the benchmark by notable margins.7