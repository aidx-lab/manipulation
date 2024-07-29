---
permalink: /humanoids23
layout: page
title: Humanoids23
usemathjax: true
---
## Estimator-Coupled Reinforcement Learning for Robust Purely Tactile In-Hand Manipulation
This site complements our paper [**Estimator-Coupled Reinforcement Learning for Robust Purely Tactile In-Hand Manipulation**](https://arxiv.org/abs/2311.04060){:target="_blank"} by [Lennart Röstel](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Johannes Pitz](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"}, [Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"}

<p align="center">
<iframe width="746" height="420" src="https://www.youtube.com/embed/P8jSDg5TA_E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>

## Abstract

This paper identifies and addresses the problems with naively combining (reinforcement) learning-based controllers and state estimators for robotic in-hand manipulation. Specifically, we tackle the challenging task of purely tactile, goal-conditioned, dextrous in-hand reorientation with the hand pointing downwards.
Due to the limited sensing available, many control strategies that are feasible in simulation when having full knowledge of the object's state do not allow for accurate state estimation. Hence, separately training the controller and the estimator and combining the two at test time leads to poor performance. 
We solve this problem by coupling the control policy to the state estimator already during training in simulation.
This approach leads to more robust state estimation and overall higher performance on the task while maintaining an interpretability advantage over end-to-end policy learning. 
With our GPU-accelerated implementation, learning from scratch takes a median training time of only 6.5 hours on a single, low-cost GPU.
In simulation experiments with the DLR-Hand~II and for four significantly different object shapes, we provide an in-depth analysis of the performance of our approach. 
We demonstrate the successful sim2real transfer by rotating the four objects to all 24 orientations in the $$\pi/2$$ discretization of SO(3), which has never been achieved for such a diverse set of shapes. 
Finally, our method can reorient a cube consecutively to nine goals (median), which was beyond the reach of previous methods in this challenging setting.
<!---![Sequence](../assets/imgs/humanoids23/motiv_pic.png) -->


Cite this paper as:

    @inproceedings{Roestel_2023,
       title={Estimator-Coupled Reinforcement Learning for Robust Purely Tactile In-Hand Manipulation},
       booktitle={IEEE-RAS 22nd International Conference on Humanoid Robots (Humanoids)},
       author={Röstel, Lennart and Pitz, Johannes and Sievers, Leon and Bäuml, Berthold},
       year={2023}}

---

<p align="center">
<iframe width="746" height="420" src="https://www.youtube.com/embed/rIDo_DmlDF4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>

---

## Interactive Analysis
Below are interactive visualization of rollouts of the estimator-coupled policy (EcRL) and the AdaEstim baseline.
To replay the animation please select "Open Controls" in the upper right corner. Then under "Animations" press "play".

### EcRL (robust)
<embed type="text/html" src="./assets/imgs/humanoids23/scene_22_ecrl.html" width="746" height="400">

### AdaEstim (non-robust)
<embed type="text/html" src="./assets/imgs/humanoids23/scene_22_ma.html" width="746" height="400">
For reference, this trajectory corresponds to figure 3 a) in the paper.
