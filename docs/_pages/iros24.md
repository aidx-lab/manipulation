---
permalink: /iros24
layout: page
title: IROS 2024
usemathjax: true
---
## Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects

This site complements our paper [**Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects**](https://arxiv.org/abs/2407.18834){:target="_blank"} by
[Johannes Pitz\*](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"}, [Lennart Röstel\*](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"}, [Darius Burschka](https://scholar.google.com/citations?hl=en&user=y-MzVoUAAAAJ){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"}.

<p align="center">
<iframe class="youtube-video" width="746" height="420" src="https://www.youtube.com/embed/aldTETxDbcU?si=mP_s1jbsa338V81j" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>

## Abstract

Reorienting diverse objects with a multi-fingered hand is a challenging task. Current methods in robotic in-hand manipulation are either object-specific or require permanent supervision of the object state from visual sensors. This is far from human capabilities and from what is needed in real-world applications. In this work, we address this gap by training shape-conditioned agents to reorient diverse objects in hand, relying purely on tactile feedback (via torque and position measurements of the fingers' joints). To achieve this, we propose a learning framework that exploits shape information in a reinforcement learning policy and a learned state estimator. We find that representing 3D shapes by vectors from a fixed set of basis points to the shape's surface, transformed by its predicted 3D pose, is especially helpful for learning dexterous in-hand manipulation. In simulation and real-world experiments, we show the reorientation of many objects with high success rates, on par with state-of-the-art results obtained with specialized single-object agents. Moreover, we show generalization to novel objects, achieving success rates of ∼90% even for non-convex shapes. 

<!-- [Open on Arxiv](https://arxiv.org/abs/2407.18834){:target="_blank"}
[button url="https://arxiv.org/abs/2407.18834"]
[Click me](https://arxiv.org/abs/2407.18834){: .btn}
<button name="button">Click me</button> -->

<button onclick="window.location.href='https://arxiv.org/abs/2407.18834';">Arxiv preprint</button>


Cite this paper as:

    @misc{Pitz2024
          title={Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects}, 
          author={Johannes Pitz and Lennart Röstel and Leon Sievers and Darius Burschka and Berthold Bäuml},
          year={2024},
          eprint={2407.18834},
          archivePrefix={arXiv},
          primaryClass={cs.RO},
          url={https://arxiv.org/abs/2407.18834}, 
    }

<!-- @inproceedings{Pitz2024,
    title={Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects},
    booktitle={2024 IEEE/RSJ International Conference on Intelligent Robots and Systems, IROS},
    author={Pitz, Johannes and Röstel, Lennart and Sievers, Leon and Burschka, Darius Bäuml, Berthold},
    year={2024}} -->

---

## Hyperparameters
Below, we provide the hyperparameters used for training the purely tactile agent.

#### EcRL Training Parameters 
See [Estimator-Coupled Reinforcement Learning for Robust Purely Tactile In-Hand Manipulation](https://arxiv.org/abs/2311.04060){:target="_blank"} for definitions

|$$\rho_0$$ | $$1.0$$
|$$\delta_{\rho}$$ | $$5\times 10^{-4}$$
|rollout length $$T$$| $$32$$
|data reusage ($$k$$) | $$4$$

#### Estimator Parameters

|learning rate | $$5\times 10^{-4}$$
|Adam $$\beta_1, \beta_2$$ | $$0.9$$, $$0.99$$
|weight decay | $$1\times 10^{-5}$$
|hidden layers $$f_{\varphi}$$| [512, 512, 512, 512]
|hidden layers $$f_{\sigma}$$| [256, 256, 256, 256]
|minibatch size | $$2^{10}$$
|latent dimensions $$n$$| $$32$$
|clip gradient by norm| $$1.0$$


#### Policy Training Parameters 
We train a policy and a value funtion using PPO with the following parameters:

|learning rate | adaptive, based on kl-divergence
|kl_threshold | 0.016
|weight decay | $$1\times 10^{-5}$$
|hidden layers | [512, 512, 256, 128]
|minibatch size | $$2^{15}$$
|$$\epsilon_{clip}$$ | $$0.2$$
|entropy coeff | $$1\times 10^{-3}$$
|GAE $$\lambda$$ | $$0.95$$
|$$\gamma$$ | $$0.99$$


#### Network details

<details><summary>Policy</summary>
<pre><code>Network(
  (a2c_network): Network(
    (actor_mlp): D2RLNet(
      (activations): ModuleList(
        (0-3): 4 x ELU(alpha=1.0)
      )
      (linears): ModuleList(
        (0): Linear(in_features=353, out_features=512, bias=True)
        (1): Linear(in_features=865, out_features=512, bias=True)
        (2): Linear(in_features=865, out_features=256, bias=True)
        (3): Linear(in_features=609, out_features=128, bias=True)
      )
    )
    (critic_mlp): D2RLNet(
      (activations): ModuleList(
        (0-3): 4 x ELU(alpha=1.0)
      )
      (linears): ModuleList(
        (0): Linear(in_features=353, out_features=512, bias=True)
        (1): Linear(in_features=865, out_features=512, bias=True)
        (2): Linear(in_features=865, out_features=256, bias=True)
        (3): Linear(in_features=609, out_features=128, bias=True)
      )
    )
    (value): Linear(in_features=128, out_features=1, bias=True)
    (mu): Linear(in_features=128, out_features=12, bias=True)
  )
)</code></pre>
<h5>Inputs</h5>
joint pos + control error: 6 * 24 <br>
goal delta rot: 6 <br>
vec bps: 4**3 * 3 <br>
object pose: 9 <br>
uncertainty: 2 <br>
<br>
</details>

<details><summary>Estimator</summary>
<pre><code>Network(
  (encoder): MLP(
    (model): Sequential(
      (0): Linear(in_features=144, out_features=512, bias=True)
      (1): ReLU()
      (2): Linear(in_features=512, out_features=512, bias=True)
      (3): ReLU()
      (4): Linear(in_features=512, out_features=512, bias=True)
      (5): ReLU()
      (6): Linear(in_features=512, out_features=512, bias=True)
      (7): ReLU()
      (8): Linear(in_features=512, out_features=32, bias=True)
    )
  )
  (transition_model): MLP(
    (model): Sequential(
      (0): Linear(in_features=265, out_features=512, bias=True)
      (1): ReLU()
      (2): Linear(in_features=512, out_features=512, bias=True)
      (3): ReLU()
      (4): Linear(in_features=512, out_features=512, bias=True)
      (5): ReLU()
      (6): Linear(in_features=512, out_features=512, bias=True)
      (7): ReLU()
      (8): Linear(in_features=512, out_features=38, bias=True)
    )
  )
  (sigma_net): MLP(
    (model): Sequential(
      (0): Linear(in_features=32, out_features=256, bias=True)
      (1): ReLU()
      (2): Linear(in_features=256, out_features=256, bias=True)
      (3): ReLU()
      (4): Linear(in_features=256, out_features=256, bias=True)
      (5): ReLU()
      (6): Linear(in_features=256, out_features=256, bias=True)
      (7): ReLU()
      (8): Linear(in_features=256, out_features=2, bias=True)
    )
  )
)</code></pre>
<h5>Encoder input</h5>
joint pos + control error: 6 * 24 <br>
<h5>Transition_model input</h5>
encoder out: 32 <br>
latent: 32 <br>
vec bps: 4**3 * 3 <br>
object pose: 9 <br>
<h5>Transition_model output</h5>
latent: 32 <br>
delta pos: 3 <br>
delta rot: 3 <br>
<h5>Sigma_net input</h5>
latent: 32 <br>
<br>
</details>
