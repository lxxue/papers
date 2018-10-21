# Towards Evaluating the Robustness of Neural Networks
Nicholas Carlini David Wagner

## Summary
Introduce three attack methods that make defensive distillation useless.

### Three different distance metric:

+ L_0: tend to only change a small amount of pixel, but change it greatly
+ L_2: tend to change much more pixels compared with L1, but with smaller perturbation
+ L_infty: like L2, change a lot of pixels and with more drastic change in value compared to L_2(less drastic compared to L_0)

### Three different attack setting:

+ white box: attacker has full access to model's architecture, parameters, and gradient.
+ black box: only the output of model(Usually attack a substitute model and try to transfer the adversarial examples)

### Two different types of adversarial examples:

+ targeted: want the example to be classified as an fixed label T
    + AverageCase: Random target
    + BestCase: Easiest one
    + WorstCase: hardest one

+ untargeted: just need the output to be different from the current output

### Existing attacking methods:

1. L-BFGS-B in Intriguing... paper: optimize an objective c||x-x'|| + F_loss(x') with the constraint that x' should be in [0,1] box.
2. FGSM: x = x' - \epsilon * gradient
3. IGS: larger step size and then clip
4. JSMA: consider pixel pair pq and find "best" pair to disturb. used for l_0 distance
5. Deepfool: suppose the network is linear and find analytical solution. repeat until one is found.

### Solving under box constraint

1. Projected GD: perform poorly with advanced GD(e.g. Momentum) since clipping unexpected change the start point of next iteration
2. Internal clipping: go some flat spot where x_i is much larger than 1 so that partial derivative is 0.
3. Use tanh to project x to [0,1]