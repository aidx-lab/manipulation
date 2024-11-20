---
permalink: /humanoids24
layout: page
title: Humanoids 2024
usemathjax: true
---
## Learning Time-Optimal and Speed-Adjustable Tactile In-Hand Manipulation

This site complements our paper [**Learning Time-Optimal and Speed-Adjustable Tactile In-Hand Manipulation**](TODO){:target="_blank"} by
[Johannes Pitz](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"}, [Lennart Röstel](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"}.


<!-- TODOOOOOO -->
<p align="center">
<iframe class="youtube-video" width="746" height="420" src="https://www.youtube.com/embed/Aj4xOSilkxQ?si=KqEdB7ExmzAE34TG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>

## Abstract

In-hand manipulation with multi-fingered hands is a challenging problem that recently became feasible with the advent of deep reinforcement learning methods. While most contributions to the task brought improvements in robustness and generalization, this paper addresses the critical performance measure of the speed at which an in-hand manipulation can be performed. We present reinforcement learning policies that can perform in-hand reorientation significantly faster than previous approaches for the complex setting of goal-conditioned reorientation in SO(3) with permanent force closure and tactile feedback only (i.e., using the hand's torque and position sensors). Moreover, we show how policies can be trained to be speed-adjustable, allowing for setting the average orientation speed of the manipulated object during deployment. To this end, we present suitable and minimalistic reinforcement learning objectives for time-optimal and speed-adjustable in-hand manipulation, as well as an analysis based on extensive experiments in simulation. We also demonstrate the zero-shot transfer of the learned policies to the real DLR-Hand II with a wide range of target speeds and the fastest dextrous in-hand manipulation without visual inputs.


Cite this paper as:

    @inproceedings{Pitz2024,
        title={Learning Time-Optimal and Speed-Adjustable Tactile In-Hand Manipulation},
        booktitle={IEEE-RAS International Conference on Humanoid Robots (Humanoids)},
        author={Pitz, Johannes and Röstel, Lennart and Sievers, Leon and Bäuml, Berthold},
        year={2024}
    }

---
    

## Hyperparameters
Below, we provide the learning hyperparameters used for training the purely tactile agent that were changed from our [previous work](iros24.md){:target="_blank"} to better work with the higher interaction frequency $$f_{\text{nn}} = 20Hz$$ and lower filter constant $$\tau = 0.2$$ reported in the paper.

#### Policy Training Parameters 

We introduce a small bounds loss on the network output based on the [rlgames PPO implementation](https://github.com/Denys88/rl_games/blob/2606effbc2ecbee93ff2cc313b25dd5b4a7f0e54/rl_games/algos_torch/a2c_continuous.py#L195). The other loss coefficients remain unchanged but are listed for reference.

|soft_bound | $$1.0$$
|bounds_loss_coef | $$0.003$$
|critic_coef | $$4.0$$
|entropy_coef | $$0.001$$

#### Reward 

|$$\lambda_{q}$$ | $$\frac{1}{24}$$

#### EcRL Training Parameters 
See [Estimator-Coupled Reinforcement Learning](https://arxiv.org/abs/2311.04060){:target="_blank"} for definitions

|$$\delta_{\rho}$$ | $$1\times 10^{-3}$$ 
