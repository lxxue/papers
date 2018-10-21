# Intriguing properties of neural networks

Christian Szegedy, Wojciech Zaremba, Ilya Sutskever, Joan Bruna, Dumitru Erhan, Ian Goodfellow, Rob Fergus

## Summary

There are two main findings of this paper:

1. Linear combination of activation also leads to seemingly interpretable features: it is the space, not the direction, that matters. NNs do not generate disentangled features at all.
    + What does this argument mean? What does linear combination of neural network represents? It looks like a next layer neuron?

2. Existence of adversarial examples.
    + We can use Lipschitz constant as a way of regularization -> lead to smoothness -> more robust in L-p meaning
    + What is adversarial examples? L_p ball seems to be an intuition and is mathematically simple. How to define more general adversarial examples like useless occlusion?
    + To conquer such problems, the authors propose to generate adversarial examples(keep a pool and update it from time to time, use L-BFGS ) and train the network with these examples. A quiet brute-force but effective way? However, this training examples really slow down and seems not a fundamental way(I guess we still can find many holes in the trained network).