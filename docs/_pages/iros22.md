---
permalink: /iros22
layout: page
title: "IROS\u00A02022"
usemathjax: true
---
## Learning a State Estimator for Tactile In-Hand Manipulation

This site complements our paper [**Learning a State Estimator for Tactile In-Hand Manipulation**](https://ieeexplore.ieee.org/document/9981730){:target="_blank"} by
[Lennart Röstel](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"}, [Johannes Pitz](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"}, and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"}.

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/SaBwlCRnR3k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</p>

## Abstract

We study the problem of estimating the pose of an object which is being manipulated by a multi-fingered robotic hand by only using proprioceptive feedback. To address this challenging problem, we propose a novel variant of differentiable particle filters, which combines two key extensions. First, our learned proposal distribution incorporates recent measurements in a way that mitigates weight degeneracy. Second, the particle update works on non-euclidean manifolds like Lie-groups, enabling learning-based pose estimation in 3D on SE(3). We show that the method can represent the rich and often multi-modal distributions over poses that arise in tactile state estimation. The models are trained in simulation, but by using domain randomization, we obtain state estimators that can be employed for pose estimation on a real robotic hand (equipped with joint torque sensors). Moreover, the estimator runs fast, allowing for online usage with update rates of more than 100 Hz on a single CPU core. We quantitatively evaluate our method and benchmark it against other approaches in simulation. We also show qualitative experiments on the real torque-controlled DLR-Hand II.

<button onclick="window.location.href='https://ieeexplore.ieee.org/document/9981730';">IEEE Explore</button>

Consider citing this paper as:

    @inproceedings{Roestel_2022,
       title={Learning a State Estimator for Tactile In-Hand Manipulation},
       booktitle={IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)},
       publisher={IEEE},
       author={Röstel, Lennart and Sievers, Leon and Pitz, Johannes and Bäuml, Berthold},
       year={2022},}
