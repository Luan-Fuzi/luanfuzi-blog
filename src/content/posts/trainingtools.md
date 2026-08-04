---
title: "深度学习小工具"
published: 2024-05-08T23:39:24+08:00
description: "整理一些深度学习过程中用到的小工具，提升1%的工作效率并提高99%的工作满意度。"
category: legacy
tags: ["工具"]
---

整理一些深度学习过程中用到的小工具，提升1%的工作效率并提高99%的工作满意度。

## GPU状态监控

N卡自带的监控可以使用nvidia-smi指令调用，好处是驱动自带，坏处是…其实这监控没给多少有用信息。

![nvidia-smi](/imgs/posts/trainingtools/nvidia-smi.png)

使用nvtop获得更加炫酷、更加详细的监控指标。

![nvtop](/imgs/posts/trainingtools/nvtop.png)

## TensorboardX or wandb?

wandb适合团队协作、远程访问，功能强大，但我有时也懒得配。

TensorboardX做单卡少次训练也够用，如果不是特别注重细节。

### 哈哈哈3
