# Additional Stability Score Definitions

This document contains detailed definitions for stability score metrics based on Bundled Camera Paths and MeshFlow approaches.

## Deep Online Video Stabilization (2019)
**Paper**: [Deep Online Video Stabilization With Multi-Grid Warping Transformation Learning](https://ieeexplore.ieee.org/document/8554287), IEEE TIP 2019

Follows MeshFlow's approach:
- Computes spatially distributed camera paths as vertex profiles for 4×4 mesh grid vertices
- Presents vertex profiles as 1D temporal signals for frequency domain analysis
- Takes lowest frequency components over full frequencies (excluding DC component)
- Final score is the average from all profiles

## PWStableNet (2020)
**Paper**: [PWStableNet: Learning Pixel-Wise Warping Maps for Video Stabilization](https://ieeexplore.ieee.org/document/8951447), IEEE TIP 2020

Based on MeshFlow's approach:
- Segments each frame into 4×4 grids
- Uses vertex profiles between successive frames as 1D temporal signals
- Computes the ratio of lowest frequency components (2nd to 6th) over full frequencies (excluding DC component)
- Final score is the average ratio of all profiles

## DIFRINT (2019)
**Paper**: [DIFRINT: Deep Iterative Frame Interpolation for Full-Frame Video Stabilization](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9022415), ICCVW 2019

Uses the Bundled Camera Paths approach:
- Extracts translation and rotation components from camera path
- Creates two 1D profile signals
- Computes the ratio of the sum of lowest (2nd to 6th) frequency energies to total energy
- Takes the minimum as the final stability score

## Minimum Latency Deep Online Video Stabilization (2023)
**Paper**: [Minimum Latency Deep Online Video Stabilization](https://github.com/liuzhen03/NNDVS), ICCV 2023

Follows the Bundled Camera Paths approach:
- Uses frequency domain analysis on camera paths
- Measures the smoothness of stabilized videos

## Deep Online Fused Video Stabilization (2022)
**Paper**: [Deep Online Fused Video Stabilization](https://zhmeishi.github.io/dvs/), WACV 2022

This paper references multiple methods including:
- Deep iterative frame interpolation for full-frame video stabilization
- Bundled camera paths for video stabilization
- Deep online video stabilization with multi-grid warping transformation learning
- Learning video stabilization using optical flow
- PWStableNet

## FuSta (2021)
**Paper**: [FuSta: Hybrid Neural Fusion for Full-frame Video Stabilization](https://alex04072000.github.io/FuSta/), ICCV 2021

Measures the stability and smoothness of the stabilized video, with implementation derived from DIFRINT.

---

**Important**: The method descriptions in this document have been condensed from the original papers and were generated with the assistance of AI LLM models. Please use with caution and refer to the original papers for complete and accurate information.
