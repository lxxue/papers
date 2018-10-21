# EXPLAINING AND HARNESSING ADVERSARIAL EXAMPLES

Ian J. Goodfellow, Jonathon Shlens & Christian Szegedy

## Argument

1. Adversarial examples come from the local linearity of neural network:

    + perturbation \neta does not grow with dimension in the sense of L_infty
    + however, perturbation of input for activation(linear combination of input image) grow with dimension in linear model w^tx
    + so for input space with high dimension, small perturbation can add up and cause undesirable results -- adversarial examples
    + for neural networks, we can use gradient to approximate equivalent linear model w^tx, where w is gradient w.r.t. input x
    + advantage: almost no overhead by applying chain rule
    + seems to bear some similarity to L1 weight decay, but actually quite different. 
    + So L1 weight decay coefficient should be much smaller than perturbation threshold epsilon

2. Random Noise has little to do with adversarial examples:

    + on expectation, the perturbation adds up to zero

3. View adversarial training as minimize worst-case error and active learning

4. No conclusion which layer is easier to perturb: no consistent experiment result

5. adversarial training applies when the model has enough capacity to resist adversarial examples.

    + if start from last hidden layer, the corresponding model doesn't satisfy the requirement for universal approximation theorem, thus not suitable for adversarial training.

6. why adversarial examples generalize: linearity

    + adversarial examples lie in more broad subspace, not a single point
    + though trained on different subsets, the learned parameters are similar because the current setting make models tend to resemble linear classifiers

7. why adversarial examples exist:

    + generative models also suffer adversarial examples
    + ensemble does not help much