# Practical Black-Box Attacks against Machine Learning

Nicolas Papernot, Patrick McDaniel, Ian Goodfellow, Somesh Jha, Z. Berkay Celik, Ananthram Swami

## Summary

Conditions: have access to the output label of targeted model, no access to the parameters and the training dataset.

Method:

+ train a substitute network using synthetic data
+ craft adversarial examples using substitute
+ transfer them to the targeted example

Key issues:

+ What's the suitable architecture of a substitute?
  + actually we just need to have the basic idea of what's the input(e.g. text, image) and output(e.g. class prob), and use appropriate operation for it(e.g. conv for image)
  + hyperparameters(e.g. # layers, # neurons) have relatively low impact on the success of the attack
  + But why?
+ How to generate the synthetic dataset?
  + manually find some images that might appear in the training dataset of target model 
+ Make # queries as small as possible.