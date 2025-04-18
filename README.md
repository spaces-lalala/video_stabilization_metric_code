# Video Stabilization Evaluation Metrics

> **Note**: This repository is continuously being updated. If you notice any errors or have information to contribute, please feel free to contact me.

A collection of "stability_score" metrics for evaluating video stabilization algorithms, including detailed definitions from key research papers and links to public implementations.

## Public Implementations

| Publication | Year | Paper / Project Page | Code Link | Remarks |
|------------|------|-------|-----------|---------|
| TOG | 2020 | [DIFRINT: Deep Iterative Frame Interpolation for Full-Frame Video Stabilization](https://arxiv.org/pdf/1909.02641) | [GitHub (Official)](https://github.com/jinsc37/DIFRINT/blob/master/metrics.py) | Based on Bundled Camera Paths |
| ICCV | 2021 | [FuSta: Hybrid Neural Fusion for Full-frame Video Stabilization](https://alex04072000.github.io/FuSta/) | [GitHub (Official)](https://github.com/alex04072000/FuSta/blob/main/metrics.py) | Based on DIFRINT |
| WACV | 2022 | [Deep Online Fused Video Stabilization](https://zhmeishi.github.io/dvs/) | [GitHub (Official)](https://github.com/googleinterns/deep-stabilization/blob/master/dvs/metrics.py) |  |
| ICCV | 2023 | [Minimum Latency Deep Online Video Stabilization](https://arxiv.org/pdf/2212.02073) | [GitHub (Official)](https://github.com/liuzhen03/NNDVS/blob/master/metrices.py) | Based on Bundled Camera Paths |

*Remarks indicate which previous method the stability score implementation is based on.*

## Stability Score Definitions

### Bundled Camera Paths for Video Stabilization
**[Project page](http://www.liushuaicheng.org/SIGGRAPH2013/index.htm)**, TOG 2013

This work introduced a frequency-based stability metric. Their approach:
- Uses bundled camera paths to approximate true motion in the video
- Extracts translation and rotation components as 1D temporal signals
- Evaluates the energy percentage of low-frequency components (2nd to 6th) over full frequencies (excluding DC component)
- Takes the smallest measurement among translation and rotation as the final score

### MeshFlow: Minimum Latency Online Video Stabilization (2016)
**[Project page](http://www.liushuaicheng.org/eccv2016/index.html)**,  ECCV 2016

This approach modifies the Bundled Camera Paths method:
- Uses vertex profiles extracted from the stabilized video
- Analyzes each vertex profile in the frequency domain
- Takes the lowest frequencies (2nd to 6th) and calculates the energy percentage over full frequencies (excluding DC component)
- Final score is the average across all profiles

For details on other methods based on Bundled Camera Paths and MeshFlow, see [Detail.md](Detail.md).

## Notes
- The calculation of certain metrics might fail and result in NaN or values larger than 1.0 when evaluating some stabilization methods, due to lack of feature points or homography estimation failures

**Important**: The method descriptions in this repository have been condensed from the original papers and were generated with the assistance of AI LLM models. Please use with caution and refer to the original papers for complete and accurate information.