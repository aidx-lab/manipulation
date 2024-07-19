---
permalink: /iros24
layout: page
title: IROS24
usemathjax: true
---
## Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects

This site complements our paper [**Learning a Shape-Conditioned Agent for Purely Tactile In-Hand Manipulation of Various Objects**](){:target="_blank"} by
[Johannes Pitz\*](https://www.linkedin.com/in/johannes-pitz/){:target="_blank"}, [Lennart Röstel\*](https://scholar.google.com/citations?user=BPUd5h0AAAAJ&hl=en&oi=sra), [Leon Sievers](https://www.linkedin.com/in/leon-sievers/){:target="_blank"}, [Darius Burschka](https://scholar.google.com/citations?hl=en&user=y-MzVoUAAAAJ){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"} submitted to the 2024 IEEE/RSJ International Conference on Intelligent Robots and Systems.

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
|weight decay | $$1\times 10^{-5}$$
|hidden layers | [512, 512, 256, 128]
|minibatch size | $$2^{15}$$
|$$\epsilon_{clip}$$ | $$0.2$$
|entropy coeff | $$1\times 10^{-3}$$
|GAE $$\lambda$$ | $$0.95$$
|$$\gamma$$ | $$0.99$$
