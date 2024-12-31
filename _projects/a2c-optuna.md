---
layout: page
title: A2C Optuna
description: Advantage Actor-Critic with Optuna
img: assets/img/a2c_optuna/preview.jpeg
importance: 2
---


The performance of online reinforcement algorithms such as A2C is very sensitive to hyperparameters. To automate and streamline the training of an optimal policy, this project utilizes [Optuna](https://optuna.org/), a hyperparameter search framework. We successfully find the set of parameters that solve the Mujoco Gym environments like HalfCheetah.

Optuna uses the Bayesian optimization algorithm to search for the best set of hyperparameters. We search among these: model size, discount, learning rate, generalized advantage estimate lambda, temporal difference lambda, baseline gradient steps, and batch size.

We compare the performance of our best model trained by Optuna for the `HalfCheetah-v4` environment with the stable-baseline3 A2C policy, the only policy available online for the same environment. The sb3-a2c policy can be found [here](https://huggingface.co/sb3/a2c-HalfCheetah-v3)

| Policy   | Average Return |
| -------- | ------- |
| **Ours**| 3828.84 |
| sb3-a2c  | 3096.61 |

Our model performs `24%` better than the sb3-a2c. Below are the policies' trajectory rollouts.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/a2c_optuna/policy_rollout" title="our policy rollout" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/a2c_optuna/sb3_a2c_rollout.gif" title="s3b-a2c policy rollout" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The left video is a rollout of our policy, and the right one corresponds to the sb3-a2c policy.
</div>

From the video above we can see that our agent achieves higher speed and runs in more stable way compared to the sb3-a2c policy.

We present the details our model training
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/a2c_optuna/return_figure.png" title="return figure" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

And here is the set of hyperparameter values found by Optuna to train our policy

| Policy   | discount| learning rate | gae lambda| td lambda| baseline grad steps| batch size| normalize advantage | reward to go| num layers| layer size layers|
| -------- | ------- | -------       | -------   | -------   | -------            | ------- | -------              | -------     | -------   | -------         |
| **Ours** | 0.99    | 1.0e-3       | 1.0        | 1.0      | 50                  | 25,000 | true                   | true       | 3         | 256             |

[[Code]](https://github.com/georgysavva/a2c-optuna)
