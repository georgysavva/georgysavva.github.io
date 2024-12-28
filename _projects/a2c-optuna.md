---
layout: page
title: Actor-Critic with Optuna
description: 
img:
importance: 2
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/diffusion_for_simulation/sfg-b4-concat-teacherforcing.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This trajectory is simulated by the model.
</div>

We explore the application of transformer-based
diffusion models for game environment generation, investigating multiple approaches for conditioning on past frames and actions: Video Generation (VG) to predict the whole video sequence
conditioned on past actions, and Single Frame
Generation (SFG) to predict a single frame conditioned on past frames and actions, with both
concatenation and cross-attention mechanisms.
Using the ViZDoom My Way Home environment as our test environment, we demonstrate that
while SFG models achieve superior performance
in teacher-forcing scenarios with PSNR values
up to 32.21, VG models show better stability in
autoregressive generation, suggesting important
tradeoffs between model architecture and performance.

[[Final Report]](assets/pdf/Diffusion_for_Simulation.pdf) [[Code]](https://github.com/georgysavva/diffusion-for-simulation)
