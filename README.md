# Video Stabilization Evaluation Metrics

> **Note**: This repository is continuously being updated. If you notice any errors or have information to contribute, please feel free to contact me.

A comprehensive collection of stability score metrics for evaluating video stabilization algorithms, including detailed definitions from key research papers and links to public implementations.

## Table of Contents
- [Public Implementations](#public-implementations)
- [Stability Score Definitions](#stability-score-definitions)

## Public Implementations

| Year | Method | Publication | Paper | Code Link |
|------|--------|------------|-------|-----------|
| 2016 | MeshFlow | ECCV | [MeshFlow: Minimum Latency Online Video Stabilization](http://www.liushuaicheng.org/eccv2016/meshflow.pdf) | [GitHub (Unofficial)](https://github.com/how4rd/meshflow/blob/master/meshflowstabilizer.py) |
| 2019 | Deep Online Video Stabilization | IEEE TIP | [Deep Online Video Stabilization With Multi-Grid Warping Transformation Learning](https://ieeexplore.ieee.org/document/8554287) | [GitHub (Unofficial)](https://github.com/btxviny/StabNet/blob/main/metrics.py) |
| 2019 | DIFRINT | ICCVW/TOG | [DIFRINT: Deep Iterative Frame Interpolation for Full-Frame Video Stabilization](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9022415) | [GitHub (Official)](https://github.com/jinsc37/DIFRINT/blob/master/metrics.py) |
| 2021 | FuSta | ICCV | [FuSta: Hybrid Neural Fusion for Full-frame Video Stabilization](https://alex04072000.github.io/FuSta/) | [GitHub (Official)](https://github.com/alex04072000/FuSta/blob/main/metrics.py) |
| 2022 | Deep Online Fused | WACV | [Deep Online Fused Video Stabilization](https://zhmeishi.github.io/dvs/) | [GitHub (Official)](https://github.com/googleinterns/deep-stabilization/blob/master/dvs/metrics.py) |
| 2023 | NNDVS | ICCV | [Minimum Latency Deep Online Video Stabilization](https://github.com/liuzhen03/NNDVS) | [GitHub (Official)](https://github.com/liuzhen03/NNDVS/blob/master/metrices.py) |

## Stability Score Definitions

### Bundled Camera Paths (2013)
**Paper**: [Bundled Camera Paths for Video Stabilization](http://www.liushuaicheng.org/SIGGRAPH2013/index.htm), TOG 2013

This work introduced a frequency-based stability metric. Their approach:
- Uses bundled camera paths to approximate true motion in the video
- Extracts translation and rotation components as 1D temporal signals
- Evaluates the energy percentage of low-frequency components (2nd to 6th) over full frequencies (excluding DC component)
- Takes the smallest measurement among translation and rotation as the final score

### MeshFlow (2016)
**Paper**: [MeshFlow: Minimum Latency Online Video Stabilization](http://www.liushuaicheng.org/eccv2016/meshflow.pdf), ECCV 2016

This approach modifies the Bundled Camera Paths method:
- Uses vertex profiles extracted from the stabilized video
- Analyzes each vertex profile in the frequency domain
- Takes the lowest frequencies (2nd to 6th) and calculates the energy percentage over full frequencies (excluding DC component)
- Final score is the average across all profiles

### Deep Online Video Stabilization (2019)
**Paper**: [Deep Online Video Stabilization With Multi-Grid Warping Transformation Learning](https://ieeexplore.ieee.org/document/8554287), IEEE TIP 2019

Follows MeshFlow's approach:
- Computes spatially distributed camera paths as vertex profiles for 4×4 mesh grid vertices
- Presents vertex profiles as 1D temporal signals for frequency domain analysis
- Takes lowest frequency components over full frequencies (excluding DC component)
- Final score is the average from all profiles

### PWStableNet (2020)
**Paper**: [PWStableNet: Learning Pixel-Wise Warping Maps for Video Stabilization](https://ieeexplore.ieee.org/document/8951447), IEEE TIP 2020

Based on MeshFlow's approach:
- Segments each frame into 4×4 grids
- Uses vertex profiles between successive frames as 1D temporal signals
- Computes the ratio of lowest frequency components (2nd to 6th) over full frequencies (excluding DC component)
- Final score is the average ratio of all profiles

### DIFRINT (2019)
**Paper**: [DIFRINT: Deep Iterative Frame Interpolation for Full-Frame Video Stabilization](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9022415), ICCVW 2019

Uses the Bundled Camera Paths approach:
- Extracts translation and rotation components from camera path
- Creates two 1D profile signals
- Computes the ratio of the sum of lowest (2nd to 6th) frequency energies to total energy
- Takes the minimum as the final stability score

### Minimum Latency Deep Online Video Stabilization (2023)
**Paper**: [Minimum Latency Deep Online Video Stabilization](https://github.com/liuzhen03/NNDVS), ICCV 2023

Follows the Bundled Camera Paths approach:
- Uses frequency domain analysis on camera paths
- Measures the smoothness of stabilized videos

### Deep Online Fused Video Stabilization (2022)
**Paper**: [Deep Online Fused Video Stabilization](https://zhmeishi.github.io/dvs/), WACV 2022

This paper references multiple methods including:
- Deep iterative frame interpolation for full-frame video stabilization
- Bundled camera paths for video stabilization
- Deep online video stabilization with multi-grid warping transformation learning
- Learning video stabilization using optical flow
- PWStableNet

### FuSta (2021)
**Paper**: [FuSta: Hybrid Neural Fusion for Full-frame Video Stabilization](https://alex04072000.github.io/FuSta/), ICCV 2021

Measures the stability and smoothness of the stabilized video, with implementation derived from DIFRINT.

## Notes
- Some official implementations don't include the evaluation metrics code
- The calculation of certain metrics might fail and result in NaN or values larger than 1.0 when evaluating some stabilization methods, due to lack of feature points or homography estimation failures
- For accurate comparisons, it's recommended to only average scores from video sequences where all compared methods successfully pass the metric calculations