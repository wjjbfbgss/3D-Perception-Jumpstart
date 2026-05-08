


### Fundamentals of LiDAR Data and 3D Representations

Goal: to establish a strong foundation in LiDAR technology and its data formats. This is the essential first step before diving into more complex topics.

Steps:

- research the principles of LiDAR sensors and the characteristics of the 3D point clouds they generate
- investigate the primary methods for representing point clouds for machine learning, including raw point-based methods, Bird's-Eye View (BEV) projections, and voxel grids.

### Classic 3D Perception Pipelines

Goal: to understand the evolution of the field and appreciate modern methods (the traditional, non-deep-learning approaches to 3D perception).

Steps:

- investigate classic algorithms for ground segmentation (e.g., RANSAC-based plane fitting).
- explore traditional clustering methods for object instance proposals (e.g., Euclidean Clustering).
- look into the use of handcrafted feature descriptors for object classification in these classic pipelines.

### Dominant Paradigms in Modern LiDAR Object Detection

Goal: to understand current deep learning-based paradigms that dominate the field.

Step:

- research the core concepts behind the main approaches: point-based, voxel-based, and projection-based (BEV) methods.
- analyze the trade-offs between these paradigms in terms of accuracy, computational cost, and complexity.

### State-of-the-Art Models for LiDAR Object Detection

Goal: to identify and analyze the specific models that are currently leading the benchmarks.

Steps:

- consult leaderboards from datasets like nuScenes and Waymo to identify top-performing architectures.
- for each model, research its key innovations, network architecture, and performance metrics.

### LiDAR-based Segmentation

Goal: to understand the critical task of scene segmentation, which is parallel in importance to object detection.

Steps:

- research the primary segmentation tasks: semantic (labeling every point), instance (distinguishing individual objects), and panoptic (a unified combination of both).
- investigate the leading SOTA models and techniques for each of these segmentation tasks.

### Temporal and 4D Perception

Goal: to build understanding in a cutting-edge and vital area.

Steps:

- Learn: focus on understanding sequential LiDAR processing, the importance of motion consistency, and the relationship between tracking and detection.
- Study: investigate the ideas behind 4D convolution and spatiotemporal models, as well as the techniques used for instance tracking in LiDAR.

### Emerging Trends and Future Directions

Goal: to be informed of other important trends that are shaping the future of LiDAR perception.

Steps:

- research multi-modal fusion strategies that combine LiDAR with camera and radar data for more robust perception.
- investigate the growing field of self-supervised and unsupervised learning to reduce the reliance on large-scale labeled datasets.

## SOTA lidar-only models (stand Apr. 2026)

### Object Detection

1. CenterPoint: This remains an excellent choice and a very strong baseline. It is a LiDAR-only detector that has consistently shown top performance on benchmarks like nuScenes and Waymo. Its approach of detecting object centers in a Bird's-Eye-View (BEV) map is efficient and effective, making it a great starting point for your verification tests.

    GitHub Link: [https://github.com/tianweiy/CenterPoint]

2. DetZero: This model currently holds a top position on the Waymo 3D Object Detection leaderboard for LiDAR-only methods. It's an "offboard" detector, meaning it processes a long sequence of LiDAR frames (up to 200) to achieve very high accuracy by generating and refining complete object tracks. While it is highly accurate, its complexity and focus on offline, long-term processing might make it more involved for a quick test, but it represents the peak of current accuracy.

    GitHub Link: [https://github.com/PJLab-ADG/DetZero]

3. SECOND (Sparsely Embedded Convolutional Detection): This is another highly influential and efficient voxel-based LiDAR-only detector. It introduced the use of sparse convolutions to the 3D detection world, which significantly speeds up processing of the sparse voxel grids created from point clouds. It's a well-established and robust model that provides a great balance of speed and accuracy.

    Official (mmdetection3d) Link: While not a standalone repo, it's integrated into the OpenMMLab ecosystem.
    Note: For practical use, better to find it within a larger, maintained library like mmdetection3d or OpenPCDet.

### Segmentation

1. Panoptic-PHNet: This model is a top performer on the SemanticKITTI panoptic segmentation leaderboard. It uses a "clustering pseudo heatmap" to efficiently and accurately find instance centers without a separate detection step, and it does so at real-time speeds.

    GitHub Link: The paper mentions the code will be released, but a public repository under the exact name is not immediately found. However, the principles are discussed in the paper "LiDAR-Camera Panoptic Segmentation via Geometry-Consistent and Semantic-Aware Alignment", which has a repository.
    Related Repository: [https://github.com/zhangzw12319/lcps.git]

2. Eq-4D-StOP: This is the current state-of-the-art on the SemanticKITTI 4D Panoptic Segmentation leaderboard. It uses a novel rotation-equivariant network design, which means the model is built to understand that rotating an object doesn't change what it is. This approach not only improves accuracy but also reduces computational cost compared to its non-equivariant counterparts.

    GitHub Link: [https://github.com/minghanz/EQ-4D-StOP]

3. PUPS (Point Cloud Unified Panoptic Segmentation): This model also ranked 1st on the SemanticKITTI leaderboard and achieves state-of-the-art results on nuScenes. It's an end-to-end framework that unifies instance and semantic segmentation into a single "grouping" problem, getting rid of complex post-processing steps.

    GitHub Link: [https://github.com/OpenRobotLab/P3Former]