# 3D-Perception-Jumpstart

Beginner-first guide for understanding how machines perceive 3D scenes from sensors (camera, LiDAR, depth).
Camera-based systems still count as 3D perception because 3D structure can be reconstructed from:
- multi-view geometry (stereo)
- motion over time (structure from motion / visual odometry)
- learned monocular depth
Unlike LiDAR, cameras do not directly measure depth for each point.

---

## 1) What is 3D perception?

3D perception is the stack of methods used to estimate **geometry**, **motion**, and **semantics** of the world.

- **Geometry**: Where are points/surfaces in 3D?
- **Motion**: How are objects or the sensor moving over time?
- **Semantics**: What are those objects (car, person, road, wall)?

Typical outputs:
- Depth maps
- Point clouds
- Camera pose / trajectory
- 3D object detections
- Semantic scene labels

---

## 2) Big-picture pipeline (illustration)

```text
Sensors (RGB / Stereo / LiDAR / IMU)
                |
                v
      Calibration + Time Sync
                |
                v
   Geometry Estimation (Depth / Triangulation)
                |
                v
 Localization & Mapping (VO / SLAM / Odometry)
                |
                v
   Scene Understanding (Detection / Segmentation)
                |
                v
      Planning / Robotics / AR / Analytics
```

When each stage is required:
- **Calibration + Time Sync**: required when fusing multiple sensors, using stereo rigs, or working with time-sequence data where alignment affects geometry.
  - Example fusion setup: camera + LiDAR + IMU
- **Geometry Estimation**: required when depth/3D structure is not directly given and must be inferred from images or reconstructed from observations.
- **Localization & Mapping**: required when the platform moves and you need consistent pose tracking, trajectory estimation, or a map over time.

---

## 3) Technical foundations to learn first

### A. Math core
- Linear algebra: vectors, matrices, transforms
- Geometry: coordinate frames, rotation matrices, quaternions
- Optimization: least squares, robust losses
- Probability: Gaussian noise, Bayesian intuition

### B. Camera model essentials

Projection from 3D camera coordinates `(X, Y, Z)` to image pixel `(u, v)`:

`u = fx * (X / Z) + cx`  
`v = fy * (Y / Z) + cy`

Where:
- `fx, fy`: focal lengths (in pixels)
- `cx, cy`: principal point
- `Z`: depth (distance along camera axis)

**Key idea:** once projection is understood, tasks like triangulation, pose estimation, and SLAM become much easier to reason about.

### C. LiDAR basics
- LiDAR returns sparse 3D points `(x, y, z)` with optional intensity.
- Advantages: metric depth directly measured.
- Trade-off: sparsity + sensor noise + occlusion.

---

## 4) How to use this repository

Use this repository as a personal learning notebook:
- Track what topic you finished each week.
- Add links to papers/videos/datasets you found useful.
- Keep a short “what I understood vs what is still unclear” section after each module.
