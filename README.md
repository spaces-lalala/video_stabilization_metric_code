# Video Stabilization Evaluation Metrics

> **Note**: This repository is continuously being updated. If you notice any errors or have information to contribute, please feel free to contact me.

A collection of "stability_score" metrics for evaluating video stabilization algorithms, including detailed definitions from key research papers and links to public implementations.

## Public Implementations

| Publication | Year | Paper | Code Link | Remarks |
|------------|------|-------|-----------|---------|
| ICCVW/TOG | 2019 | [DIFRINT: Deep Iterative Frame Interpolation for Full-Frame Video Stabilization](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=9022415) | [GitHub (Official)](https://github.com/jinsc37/DIFRINT/blob/master/metrics.py) | Based on Bundled Camera Paths |
| ICCV | 2021 | [FuSta: Hybrid Neural Fusion for Full-frame Video Stabilization](https://alex04072000.github.io/FuSta/) | [GitHub (Official)](https://github.com/alex04072000/FuSta/blob/main/metrics.py) | Based on DIFRINT |
| WACV | 2022 | [Deep Online Fused Video Stabilization](https://zhmeishi.github.io/dvs/) | [GitHub (Official)](https://github.com/googleinterns/deep-stabilization/blob/master/dvs/metrics.py) |  |
| ICCV | 2023 | [Minimum Latency Deep Online Video Stabilization](https://github.com/liuzhen03/NNDVS) | [GitHub (Official)](https://github.com/liuzhen03/NNDVS/blob/master/metrices.py) | Based on Bundled Camera Paths |

*Remarks indicate which previous method the stability score implementation is based on. Empty cell means no specific base method is mentioned.*

## Stability Score Definitions

### Bundled Camera Paths (2013)
**Project page**: [Bundled Camera Paths for Video Stabilization](http://www.liushuaicheng.org/SIGGRAPH2013/index.htm), TOG 2013

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

For details on other methods based on Bundled Camera Paths and MeshFlow, see [Detail.md](Detail.md).

## Notes
- Some official implementations don't include the evaluation metrics code
- The calculation of certain metrics might fail and result in NaN or values larger than 1.0 when evaluating some stabilization methods, due to lack of feature points or homography estimation failures
- For accurate comparisons, it's recommended to only average scores from video sequences where all compared methods successfully pass the metric calculations