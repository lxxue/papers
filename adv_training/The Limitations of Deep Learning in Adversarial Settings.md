# The Limitations of Deep Learning in Adversarial Settings

Nicolas Papernot, Patrick McDaniel, Somesh Jha, Matt Fredrikson, Z. Berkay Celik, Ananthram Swami

## Summary

Use the Jacobian of output instead of gradient of loss function as guidance for adversarial search!

So-called saliency map: use Jacobian to set the change of each pixel either with 0(where it is not wise to perturb since this pixel will hurt class t or benefit all other classes), or with distortion proportional to $\partial F_t/\partial x_{ij}$ and $\sum_{l \neq t} \partial F_l / \partial x_{ij}$.

Not so much extra computation for Jacobian(most partial derivatives have been calculated during backprop) but O($n^2$) for saliency map.

Use heuristic to select two pixels to perturb a fix value.

propose three metric:

+ hardness metric H(s,t): average distortion from class s to class t, so depends on the method of adversarial attacks
+ adversarial distance A(X,t):How hard for one example X to be classified as t, heuristic
+ Robustness of network R(F): minimal adversarial distance for this model(assume X is large enough), still not universal

