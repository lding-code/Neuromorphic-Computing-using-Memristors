# Neuromorphic Computing using Memristors

## Team Members

### Haebel Varghes, Lei Ding, Shreya Nandy

My name: Lei Ding

My student ID: 3032832007

This repo hosts resources and codes for EE 595 project "Neuromorphic Computing using Memristors"

## Preliminary summary

<https://1drv.ms/w/s!AvC8SENWufoEg_IzbgfqYzRMZy6Zjw?e=y14cfb>

## Abstract

Spiking Neural Networks on neuromorphic hardware have a lot of advantages, hence it is used for efficient implementation of deep neural networks. But as we design more complex deep neural networks, we need to find better methods to reduce the storage size and the time required for computing. In this paper we are using the model compression technique to optimize our SNN. We are hence designing an algorithm-hardware co-optimization framework that will improve the hardware usage and at the same time keep the accuracy of the neural network high.   

## Proposal

<https://docs.google.com/document/d/1Sb3gQYsvauGhS4CUvpPSOWDSfVPKRJBNzcIC0ySyt54/edit?pli=1>

## Phase 1 Update

### Problem Description

The team aims to study and produce a framework that optimizes Spiking Neural Network (SNN) by utilizing model compression techniques including weight pruning and weight quantization considering the simulation of such neural network is very power hungry. In adidtion to such optimization, a major goal of such framework is the ability to transform an optimized SNN to an actual hardware based simulation using components specifically designed for different neural networks. The team believes that the optimization of SNN and ability to transform software design to hardware design within the same framework will help advance the research and development of SNN related hardwares and broaden SNN driven applications.

The team has two groups studying two aspects of the problem: software (me) and hardware (Haebel Varghes, Shreya Nandy). On the software side, the focus is on implementing and optimizing a given SNN model with model compression techniques mentioned above. Furthermore, a visualizer that helps understand the network topology is to be developed.

### Project Timeline

At the current stage, a python package for SNN simulation called Brian is being used and studied for the software part. Several experimental SNN models have been created based this package. A working SNN image classification model (GitHub: <https://github.com/Shikhargupta/Spiking-Neural-Network>) utilizing Spike-Time Dependent Plasticity (STDP) is also being studied. STDP describes behavior of certain synapse type in which the synaptic weight will increase if the post-synaptic neuron fires after the pre-synaptic neuron. Such weight will decrease for the opposite case. A working model with actual application is very important for developing model compression techniques as it provides performance measurement.

In the next phase (phase 2), the team will implement the optimization framework and start bringing the software and hardware parts together. 

### Analysis

The actual implementation of the model compression techniques is still in debate. A basic pruning technique is weight threshold on STDP learning SNN. After each unsupervised training period, the weight of each synapse is checked. If the weight does not exceed the threshold, it will be marked 0. Further training will be executed to measure the performance hit. In the end, only the most active synapses are left. The rest synspases are considered less significant and will be discarded permanently. After the synapses are pruned, weight quatization will be used to further optimize the efficiency of the network. The quantization reduces the weight precision, hence packet complexity. A balance point between efficiency and accuracy is the optimal goal of such optimization.

### Implementation

Right now, only small sample SNN models are made to study the property of such novel network (code in examples folder). A visualizer is also work in progress.

### Papers

* Ren, A., Zhang, T., Ye, S., Li, J., Xu, W., Qian, X., Lin, X. and Wang, Y., 2019, April. Admm-nn: An algorithm-hardware co-design framework of dnns using alternating direction methods of multipliers. In Proceedings of the Twenty-Fourth International Conference on Architectural Support for Programming Languages and Operating Systems (pp. 925-938).

This paper proposes a framework that optimizes deep neural network and provide algorithm-hardware co-design capability. Although the paper is about deep neural network, the essential idea can be extended to spiking neural network. In fact, this paper provides the team with a general direction of where the project could go.

* Machado, P., Cosma, G. and McGinnity, T.M., 2019, September. NatCSNN: A Convolutional Spiking Neural Network for recognition of objects extracted from natural images. In International Conference on Artificial Neural Networks (pp. 351-362). Springer, Cham.
  
This paper describes how SNN can be used for specific task like object recognition. The author constructed a 3-layer convolutional spiking neural network with STDP learning. The paper provides an insight on how supervised training on a SNN model is possible with a novel concept of teacher synapse. The teacher synapse will produce desired spiking signal based on inpout image. The weight of STDP synapses will be positively affected by the teacher synapse and thus increase the probability of firing signal to the correct output neuron.

* Ponulak, F., 2006. Supervised learning in spiking neural networks with ReSuMe method. Phd, Poznan University of Technology, 46, p.47.

This long paper discusses the realization of supervised learning in spiking neural networks in depth. As supplementary material to previous paper, this paper proved detailed theoretical and mathematical reference, which can be used to strengthen understanding on SNN learning techniques.

* Rathi, N., Panda, P. and Roy, K., 2018. STDP-based pruning of connections and weight quantization in spiking neural networks for energy-efficient recognition. IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, 38(4), pp.668-677.

This paper presents a very efficient optimization techniques for unsupervised learning in STDP SNN. Brief introduction of such optimization is discussed above. This paper prives a very inspiring and novel idea for optimizing SNN. The idea can be used as a starting point towards the target framework.

* Deng, L., Wu, Y., Hu, Y., Liang, L., Li, G., Hu, X., Ding, Y., Li, P. and Xie, Y., 2019. Comprehensive SNN Compression Using ADMM Optimization and Activity Regularization. arXiv preprint arXiv:1911.00822.

This paper proposes more compression techniques for SNN including supervised weight pruning and quantization, which is similar to what is discussed in the previous paper, spatial-temporal backprogation (STBP), alternating direction method of multipliers (ADMM), and active regulation. The model described in this paper is more complicated than the previous paper. It provides more emerging techniques that could be very helful to the project. The paper covers too many novel ideas, the team will try to implement weight pruning and quatization at first and then spend more time on those novel techniques. 

* Merolla, P.A., Arthur, J.V., Alvarez-Icaza, R., Cassidy, A.S., Sawada, J., Akopyan, F., Jackson, B.L., Imam, N., Guo, C., Nakamura, Y. and Brezzo, B., 2014. A million spiking-neuron integrated circuit with a scalable communication network and interface. Science, 345(6197), pp.668-673.

In this paper we learn about the neuromorphic architecture on which the TrueNorth simulator is based.

* Pfeiffer, M. and Pfeil, T., 2018. Deep learning with spiking neurons: opportunities and challenges. Frontiers in neuroscience, 12, p.774.

In this paper we learn about SNNs, their training methods, advantages and disadvantages.

* Ji, Y., Zhang, Y., Chen, W. and Xie, Y., 2018, March. Bridge the gap between neural networks and neuromorphic hardware with a neural network compiler. In Proceedings of the Twenty-Third International Conference on Architectural Support for Programming Languages and Operating Systems (pp. 448-460).

We understood the basic idea on how to build a Neural Network simulator.