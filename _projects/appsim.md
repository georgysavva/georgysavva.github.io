---
layout: page
title: AppSim
description: "AppSim: A Learned World Model for an App API"
img: assets/img/appsim/preview.png
importance: 3
---


We present AppSim, a family of learned world
models for API simulation. Building on the
model-based reinforcement learning successes
in vision-based games and text-driven environ-
ments, we consider two approaches. In the first,
we finetune a TinyLlama model on a custom
dataset of synthetic trajectories from the Ap-
pWorld engine, combining semi-random API
exploration with ChatGPT-driven user requests.
In the second, we use a powerful off-the-shelf
LLM in a zero-shot setting. Evaluating on held-
out trajectories using object-match accuracy,
BLEU, and ROUGE, we find that the general-
purpose LLMs exhibit superior performance.

You can find the details about our findings in the [final report](/assets/pdf/AppSim.pdf) and see our code [here](https://github.com/georgysavva/appsim).
