---
layout: page
title: Diffusion for Simulation 
description: Transformer-Based Diffusion for Game Generation
img: assets/img/diffusion_for_simulation/preview.png
importance: 1
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/diffusion_for_simulation/sfg-b4-concat-teacherforcing.gif" title="simulated trajectory" class="img-fluid rounded z-depth-1" %}
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

You can find the details about our findings in the [final report](/assets/pdf/Diffusion_for_Simulation.pdf) and see our code [here](https://github.com/georgysavva/diffusion-for-simulation).
