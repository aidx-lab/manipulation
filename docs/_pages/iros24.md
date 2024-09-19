---
permalink: /iros24
layout: page
title: IROS24
usemathjax: true
---
## Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects

This site complements our paper [**Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects**](https://arxiv.org/abs/2407.18834){:target="_blank"} by
[Johannes Pitz\*](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"}, [Lennart Röstel\*](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"}, [Darius Burschka](https://scholar.google.com/citations?hl=en&user=y-MzVoUAAAAJ){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"} submitted to the 2024 IEEE/RSJ International Conference on Intelligent Robots and Systems.

<iframe width="746" height="420" src="https://www.youtube.com/embed/aldTETxDbcU?si=mP_s1jbsa338V81j" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

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
