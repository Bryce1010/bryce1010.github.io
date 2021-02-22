---
layout: post
title:  "(Review)Advances and Open Problems in Federated Learning"
date:   2021-02-22 17:01:03 +0800
categories: 算法_目标识别
tags: [Federated Learning, review]
---

# Advances and Open Problems in Federated Learning


![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a7391da1-31cb-4cef-bd69-812a69790cfd/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a7391da1-31cb-4cef-bd69-812a69790cfd/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210222T090439Z&X-Amz-Expires=86400&X-Amz-Signature=dfa7043fa660e49206f257de10900fbc9c72eb4b2fced348a11433c3fd849895&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

- paper: [https://arxiv.org/pdf/1912.04977.pdf](https://arxiv.org/pdf/1912.04977.pdf)

联邦学习(Federated Learning)是通过一个中心Server（比如Server提供者）作为中枢，多个Client（比如手机，组织机构等）协作配合训练一个网络模型的框架，这种框架的好处是可以去中心化，保证训练数据的独立性。和传统训练方法相比，联邦学习不需要集中收集数据，并达到数据的最小泄露风险，这样的特点可以减轻传统方法中数据和系统的隐私风险和成本。

联邦学习由McMahan et al.[289] 在2016年提出，框架系统的构成涉及了多个领域的知识，包括了密码学、数据库和机器学习等。因此联邦学习需要关心的不仅仅是机器学习中的模型问题，还要关注分布式优化，加密问题，差分隐私，公平性，压缩感知，操作系统，信息论，数据科学等方面的问题。

广义上，联邦学习可以分为两种类型：cross-device FL和cross-silo FL。cross-device FL是一种纵向的体系结构，针对不同区域的同一种数据，广泛应用在消费数字产品上。比如Google的Gboard mobile keyboard、Pixel phones和Android Message。cross-silo FL是一种横向的体系结构，针对同一区域的不同数据，广泛应用于众多领域包括金融风险预测，药物发现、电子健康数据挖掘以及智能制造。

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2e3fe5f-99c1-418b-a4c4-86107bc06c52/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/a2e3fe5f-99c1-418b-a4c4-86107bc06c52/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210222T090525Z&X-Amz-Expires=86400&X-Amz-Signature=56096594baac20b32b3b08e1500b0da79c80d676e24c7ddf59a225938326ef2c&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

            cross-silo or Horizontal

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0f5e8bde-eb1f-444c-8a14-44ccce8590de/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0f5e8bde-eb1f-444c-8a14-44ccce8590de/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210222T090617Z&X-Amz-Expires=86400&X-Amz-Signature=c9e1beb68416a087b0ec1f73a4a79ba2bb92b68f973a2ef7b3a91d8105f99588&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

Horizontal交换的是参数

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/406095ef-c37f-4463-be39-d32029d209a7/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/406095ef-c37f-4463-be39-d32029d209a7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210222T090549Z&X-Amz-Expires=86400&X-Amz-Signature=ce9d5842d7587b19ee129a8d2480dd87c0dcd6f2880a5f0b46884d6a4b7da4f1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

            cross-device or Vertical

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/eac13d3d-b898-42a2-81bb-6b61359dc0ee/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/eac13d3d-b898-42a2-81bb-6b61359dc0ee/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210222T090709Z&X-Amz-Expires=86400&X-Amz-Signature=da7ce0499e756797b0ce285bb7ccffda7da294903050a39a82ad4069576e3212&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

Vertical交换中间结果

随着联邦学习的深入研究，关于联邦学习的应用也不断产生，包括了TensorFlow Federated，Federated AI Technology Enabler，PySyft，Leaf，PaddleFL和 Clara Training Framework。

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43eac815-aca7-4842-974b-9686af46821d/Untitled.png](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/43eac815-aca7-4842-974b-9686af46821d/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAT73L2G45O3KS52Y5%2F20210222%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20210222T090731Z&X-Amz-Expires=86400&X-Amz-Signature=02e822f8993ee52b0d2485a24dda47b9a6567fa8ae04de8fa0cce7a3486e48bb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22)

联邦学习的生命周期

- Problem identification
- Client instrumentation
- Simulation prototyping
- Federated model training
- (Federated) model evaluation
- Deployment

联邦学习的训练过程

- Client Selection
- Broadcast: 选中的client下载模型
- Client computation
- Aggeration
- Model update