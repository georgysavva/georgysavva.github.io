---
layout: page
title: A2C Optuna
description: Advantage Actor-Critic with Optuna
img: assets/img/a2c_optuna/preview.jpeg
importance: 2
---

[![Code](https://img.shields.io/badge/Code-GitHub-blue?logo=github)](https://github.com/georgysavva/a2c-optuna)

## Introduction

The performance of online reinforcement algorithms such as Advantage Actor-Critic ([A2C](https://arxiv.org/abs/1602.01783)) is very sensitive to hyperparameters.
To automate and streamline the training of an optimal policy, this project utilizes [Optuna](https://optuna.org/),
a hyperparameter search framework. We successfully find the set of parameters that solve the [HalfCheetah](https://www.gymlibrary.dev/environments/mujoco/half_cheetah/) MuJoCo Gym environment.

## Method

The policy's input is the 17-dimensional continuous state of the environment.
It's trained to predict 6-dimensional action output.
The training consists of training two networks: actor and critic.
The actor learns to map states to actions, and the critic learns to predict the expected return from a given state.
We use Generalized Advantage Estimation ([GAE](https://arxiv.org/abs/1506.02438)) for advantage calculation, with normalized advantages.
Optuna uses the Bayesian optimization algorithm to search for the best set of hyperparameters. We search among these: model size, discount, learning rate, generalized advantage estimate lambda, temporal difference lambda, baseline gradient steps, and batch size.

## Results

We compare the performance of our best model trained by Optuna for the `HalfCheetah-v4` environment with the stable-baseline3 A2C policy, the only policy available online for the same environment. The sb3-a2c policy can be found [here](https://huggingface.co/sb3/a2c-HalfCheetah-v3).

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

From the video above, we can see that our agent achieves higher speed and runs in a more stable way compared to the sb3-a2c policy.

Below is the set of hyperparameter values found by Optuna to train our policy.

| Policy   | discount| learning rate | gae lambda| td lambda| baseline grad steps| batch size| normalize advantage | reward to go| num layers| layer size layers|
| -------- | ------- | -------       | -------   | -------   | -------            | ------- | -------              | -------     | -------   | -------         |
| **Ours** | 0.99    | 1.0e-3       | 1.0        | 1.0      | 50                  | 25,000 | true                   | true       | 3         | 256             |

And here is the training curve for the average episode return of our policy.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/a2c_optuna/return_figure.png" title="return figure" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Conclusion

This project demonstrates the efficacy of automated hyperparameter optimization using Optuna in enhancing the performance of reinforcement learning algorithms.
By fine-tuning key parameters of the Advantage Actor-Critic (A2C) algorithm, we achieved a 24% improvement in average return compared to the stable-baseline3 A2C policy on the HalfCheetah MuJoCo Gym environment.

Our approach leverages Bayesian optimization to systematically explore the hyperparameter space, resulting in a robust policy that outperforms the baseline both quantitatively and qualitatively, as evident from the higher stability and speed observed in trajectory rollouts.
This highlights the potential of automated hyperparameter search frameworks like Optuna to streamline the development of efficient reinforcement learning models for complex tasks.
