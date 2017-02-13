### 我需要知道什么

1. 论文目的
2. 评价体系
3. 结构体系
4. 训练和预测过程
5. 提升结果
6. 结论 and why does it work?
7. 缺点和可以改进的地方





### Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields

affinity  接近，相似

1. Realtime 、multi-person 、pose estimate

   **data-set** : MSCOCO 2016 keypoints challenge , MPII Multi-person

   **challenge** : unknown numberof people , any position and any scale

   ​		      interactions between people *(occlusion)*

   ​		      runtime complexity is prone to growth with the num of people

2. performance : mAP

   efficiency : runtime

3. **Principle ：bottom-up manner** 

   **Mothod**：

   1) Confidence maps for part detection

   2) PAFs for part association *( PAFs , Part Affinity Fields , a set of 2D vector fileds )*

   3) Multi-Person Parsing using PAFs

   4) Joint Learing Part Detection and Association with Sequential Prediction

   **Step**:

   1）A two branch network upon CPMs to refine confidence maps and PAFs with global image and spatial contexts.

   2) use pairwise scores from PAFs and greedy algorithm to assemble body pose to th efinal pose estimate.

4. MSCOCO 2016 keypoints challenge , MPII Multi-person

   *8.8 fps* for a video with *19* people.

5. In this paper, we consider a critical component of such perception: realtime algorithms to detect the 2D pose of multiple people in images. We present an explicit nonparametric representation of the keypoints association that encodes both position and orientation of human limbs. Second, we design a CNN architecture for jointly learning parts detection and parts association. Third, an efficient parsing
   algorithm is proposed to use the part affinity fields as important bridges to associate body part detection candidates and form the full body pose of all people in the image.

6. 愿景 Machines, endowed with such perception in real-time, would be able to react to and even participate in the individual and social behavior of people.