---
layout: post
title:  "Poisoning Self-supervised Learning Based Sequential Recommendations"
author: 马浩
categories: [ 时间序列 ]
image: assets/images/FEDformer.png
---

序列推荐从用户的交互历史记录中获取用户偏好，并给出推荐。模型极易受到数据稀疏性问题的影响。数据稀疏的问题可以通过SSL来解决。为了部署SSL，他们在历史用户项交互上实现数据增强，以便进行预训练。

事实上，现实世界中的推荐系统很容易受到基于恶意用户注入的拓扑攻击。SSL在计算机视觉领域容易受到中毒攻击和后门攻击，但基于SSL的推荐系统的中毒尚未进行研究。本文作者认为在基于SSL的条件下，这种安全威胁仍然严重。

推荐系统攻击有三个挑战：1）有效性：在不知道模型的具体结构和参数的情况下，如何使得攻击效果更好；2） 隐蔽性：在注入虚假用户后如何防止被推荐模型发现；3）开销：在保证效果的前提下如何尽可能降低攻击成本。

1）本文设计了一个针对基于SSL的推荐系统的中毒攻击，该系统不需要任何推荐系统访问或了解目标模型的详细信息；2）这种方法是针对基于SSL的顺序推荐系统的第一次中毒攻击。SSL为投毒攻击创造了一个新的攻击面，这种新的攻击面支持更简单的数据投毒设置、更少的开销和更隐蔽的方式；3）该方法只需要训练SSL预训练部分的代理模型，该模型被简化为二进制分类器。
![图片](assets/IMG_1.png)

PartA：Discriminator in GAN：给定现有序列集合S，生成器将根据该集合生成虚假序列
PartB：Surrogate Model of Pre-training Part ：PartB将针对SSL的攻击公式化为双层优化问题
PartC：Presence of Target Item ：当计算PartC的损失函数时，我们将序列中的每个项目的标签设置为目标项目