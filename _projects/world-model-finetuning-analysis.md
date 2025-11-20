---
layout: page
title: World Model Finetuning Analysis
description: Do Pre-Trained and Fine-Tuned World Models Generalize?
img: assets/img/world-model-finetuning-analysis/preview.png
importance: 1
---

This work investigates the generalization capabil-
ities of two diffusion-based world models, OA-
SIS and WorldMem within the Minecraft envi-
ronment. OASIS is trained from scratch on the
diverse VPT dataset, while WorldMem is a fine-
tuned version of OASIS on a simpler, randomly
generated dataset. The models are evaluated on
three distinct datasets, VPT, WorldMem, and a
custom-designed Consistency dataset, each rep-
resenting a different distribution of the environ-
ment. Quantitative analysis using PSNR scores
and qualitative video comparisons show that both
models struggle to generalize beyond their train-
ing distributions, with fine-tuning also leading to
catastrophic forgetting of the pretrained distribu-
tion. These findings reveal the limitations of the
current world models in adapting to varied distri-
butions and suggest that combining datasets for
fine-tuning is necessary to preserve and extend
the model’s performance.

You can find the details about our findings in the [final report](/assets/pdf/World_Model_Pretrain_Finetune_Analysis.pdf).
