# Distillation as a Defense to Adversarial Perturbations against Deep Neural Networks

Nicolas Papernot, Patrick McDaniel, Xi Wu, Somesh Jha, and Ananthram Swami

## Summary

Distillation: a training procedure designed to transfer knowledge learn from one DNN to another DNN. In this paper, the authors try to use this method to improve DNN's own resilience to adversarial attacks. The explanation is that distillation can help reduce the amplitude of gradients(more smooth).

### Distillation

Train a network with a labeled dataset. Then use the output of this network as the label for training a second network. The advantage is that the output encodes the similarity between different classes(additional entropy). Besides, it also prevents the network from fitting too tightly to the data.

There is a parameter T called temperature which controls how sharp the output of the softmax layer is(The high temperature forces the DNN to produce probability vectors with relatively large values for each class). During training the temperature of the first and the second network must be the same and larger than 1. Then at test time the temperature will be set to 1 to give more sharp predictions.

### metric of robustness

$\rho_{adv}(F) = E_{\mu}(\Delta(X,F))$

$\Delta(X,F) = \arg\min\{||\delta X|| | F(X + \delta X) \neq F(X)\}$

It seems that this definition do not depend on the attack method. However, when evaluating it we must use one or some kinds of attack methods.

### Question

Why higher temperature leads to better defense? Ambiguity helps with attack? We may review this question after reading the attack that beat this distillation mechanism.

### The impact of distillation

the mean amplitude of adversarial graident decreases dramatically. Training for too long make it suspectible to adversarial examples.

### Pros

1. No extra layer(which can be attacked also)

### Cons

1. Not trivial usage of distillation for tasks different from classification.