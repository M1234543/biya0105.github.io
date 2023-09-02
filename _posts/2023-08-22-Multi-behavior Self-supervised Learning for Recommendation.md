---
    layout: post
    title: "Multi-behavior Self-supervised Learning for Recommendation"
    author: Yunhang Yao
    categories: [推荐系统]
    image: assets/images/MBSSL.png
---

本文主要解决了两个问题

*   在多行为推荐场景中，辅助行为的交互数据虽然可以为目标行为提供良好的补充信息，但目标行为相对于辅助行为的数量仍然是稀疏的。
*   现有的SSL推荐模型将SSL任务作为辅助任务共同优化，但辅助任务的梯度和大小可能在优化过程中占据主导地位，导致优化向辅助任务靠近，偏离了推荐主目标；同时，调整多个辅助任务损失的权重是非常耗时的。

针对第一个问题，本文提出了MBSSL框架，主要包含三个模块：行为感知图神经网络，行为间自监督学习，行为内自监督学习。

行为内自监督学习通过在目标行为之间进行对比学习，放大了目标行为的监督信号，缓解了辅助行为中的噪声交互，避免学习的表征被辅助信号主导，从而失去目标行为本身的内在语义。

对于第二个问题，本文提出了混合梯度操作方法，对梯度的大小和方向进行混合操作。对于具有较小梯度大小的辅助行为梯度以及和目标行为具有较小冲突方向的辅助梯度不进行处理，防止过拟合，对于剩余情况的辅助梯度，先使用平面投影方法，将辅助行为梯度投影到目标行为的法向量，然后再利用松弛因子来控制辅助行为与目标行为梯度之间的接近程度。

[PPT](https://github.com/biya0105/biya0105.github.io/blob/main/assets/ppt/2023-08-22-Multi-behavior%20Self-supervised%20Learning%20for%20Recommendation.pptx)