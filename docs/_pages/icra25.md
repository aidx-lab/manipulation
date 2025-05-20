---
permalink: /icra25
layout: page
title: ICRA 2025
usemathjax: true
---
## Composing Dextrous Grasping and In-hand Manipulation via Scoring with a Reinforcement Learning Critic

This site complements our paper [**Composing Dextrous Grasping and In-hand Manipulation via Scoring with a Reinforcement Learning Critic**](https://arxiv.org/abs/2505.13253){:target="_blank"} by
[Lennart Röstel\*](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Dominik Winkelbauer\*](https://scholar.google.com/citations?user=kduGd8wAAAAJ), [Johannes Pitz](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"},[Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"}.

<p align="center">
<iframe width="560" height="315" src="https://www.youtube.com/embed/L4dlVvxJLJU?si=sf2NZCbvFBZ4Up6C" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</p>


## Abstract

In-hand manipulation and grasping are fundamental yet often separately addressed tasks in robotics.
 For deriving in-hand manipulation policies, reinforcement learning has recently shown great success. 
 However, the derived controllers are not yet useful in real-world scenarios because they often require a human operator to place the objects in suitable initial (grasping) states.
 Finding stable grasps that also promote the desired in-hand manipulation goal is an open problem.
 
 In this work, we propose a method for bridging this gap by leveraging the critic network of a reinforcement learning agent trained for in-hand manipulation to score and select initial grasps.
 Our experiments show that this method significantly increases the success rate of in-hand manipulation without requiring additional training.
 We also present an implementation of a full grasp manipulation pipeline on a real-world system, enabling autonomous grasping and reorientation even of unwieldy objects.

<button onclick="window.location.href='https://arxiv.org/abs/2505.13253';">arXiv preprint</button>

Consider citing this paper as:

    @inproceedings{Roestel_2025,
       title={Composing Dextrous Grasping and In-hand Manipulation via Scoring with a Reinforcement Learning Critic},
       booktitle={2025 IEEE International Conference on Robotics and Automation (ICRA)},
       publisher={IEEE},
       author={Röstel, Lennart and Winkelbauer, Dominik and Pitz, Johannes Sievers, Leon and Bäuml, Berthold},
       year={2025},
       month=may }
