---
layout: post
title: Stacked hourglass networks
categories: [blog ]
description:
comments: true
published: true
header-img: "img/18.jpg"
tags:
     - Deep Learning
     - Pose Estimation
---

*hourglass 沙漏*

1. human pose estimation —— a key toward understanding people in image

   **input** : single man in the single RGB image

   **output** : precise location of keypoints of body

   **challenge** : occlusion *( 重叠 )* 、 deformation *( 变形 )* 、 rare poses 、 enviroment *( clothing , lighting )*

   perpose : designed a kind of ConvNets named Stacked hourglass can handle any scale of image.

2. **benchmark** : *FLIC* and *MPII Human Pose*

3. **threshold** : PDJ metric

   *Metrics In order to be able to compare with published results we will use two widely accepted evaluation metrics. Percentage of Correct Parts (PCP) measures detection rate of limbs, where a limb is considered detected if the distance between the two predicted joint locations and the true limb joint locations is at most half of the limb length. PCP was the initially preferred metric for evaluation, however it has the drawback of penalizing shorter limbs, such as lower arms, which are usually harder to detect. To address this drawback, recently detection rates of joints are being reported using a different detection criterion – a joint is considered detected if the distance between the predicted and the true joint is within a certain fraction of the torso diameter (躯干直径) . By varying this fraction, detection rates are obtained for varying degrees of localization precision. This metric alleviates the drawback of PCP since the detection criteria for all joints are based on the same distance threshold. We refer to this metric as Percent of Detected Joints (PDJ).*

4. **DeepPose** *( 2014,Toshev et al. )* : directly regress the x,y coordinates of joints use ConvNet

   **Stacked hourglass networks** : generates heatmaps

   single pipeline with skip layers

   **Hourglass** is set up as follows:

   1) **bottom-up** : Conv and max-polling layers, at each max-pooling step, branches off  **to** the lowest resolution(4x4)

   2) **top-down** : nearest neighbor unsampling ,combination of featrues accross scales

   3) **two 1X1 convo7lutions** are applied ,output is a set of heatmaps

   **Stacked** means stack hourglasses end-to-end

   **Intermediate Supervision**

5. MPII **2%** average improvment       **4-5%** improvment on difficult joints

6. *This work introduces a novel convolutional network architecture for the task of human pose estimation. Features are processed across all scales and consolidated to best capture the various spatial relationships associated with the body. We show how repeated bottom-up, top-down processing used in conjunction with intermediate supervision is critical to improving the performance of the network. We refer to the architecture as a “stacked hourglass” network based on the successive steps of pooling and upsampling that are done to produce a final set of predictions.*

7. only work in the case of single man in image



The futrue work

2D pose estimation --> human part segmentation

<p><img src="/img/blog/1.png" align="center"></p>