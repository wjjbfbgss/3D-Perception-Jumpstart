# 3D-Perception-Jumpstart

Beginner-first learning plan for understanding how machines perceive 3D scenes from sensors (camera, LiDAR, depth).

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

## 4) Suggested learning plan (8 weeks)

### Phase 1 (Weeks 1-2): Coordinate systems + projection
- Learn homogeneous transforms and frame chaining.
- Implement simple 3D-to-2D projection in Python.
- Validate with synthetic points.

### Phase 2 (Weeks 3-4): Depth + stereo
- Learn disparity-depth relationship:
  `Z = (f * B) / d`  
  where `f` = focal length, `B` = baseline, `d` = disparity.
- Build a mini stereo depth demo.

### Phase 3 (Weeks 5-6): Visual odometry / SLAM basics
- Feature extraction + matching.
- Relative pose estimation (essential matrix / PnP intuition).
- Understand drift and loop closure conceptually.

### Phase 4 (Weeks 7-8): 3D detection or segmentation
- Learn point cloud preprocessing (voxelization/downsampling).
- Train/evaluate one baseline model.
- Report precision/recall and common error cases.

---

## 5) Study checklist for beginners

- [ ] I can explain coordinate frames (world, camera, sensor).
- [ ] I can derive basic pinhole projection equations.
- [ ] I can explain the disparity-to-depth relationship.
- [ ] I can describe why odometry drifts over time.
- [ ] I can run one small 3D perception experiment end-to-end.

---

## 6) Minimal project ideas

1. **Monocular depth sanity checker**  
   Compare depth maps across indoor vs outdoor scenes and write failure analysis.

2. **Stereo reconstruction mini-lab**  
   Estimate disparity and convert to point cloud.

3. **LiDAR object clustering**  
   Segment ground plane + cluster obstacles with classical methods.

---

## 7) How to use this repository

Use this repository as a personal learning notebook:
- Track what topic you finished each week.
- Add links to papers/videos/datasets you found useful.
- Keep a short “what I understood vs what is still unclear” section after each module.
