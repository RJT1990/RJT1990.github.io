# Why Synthetic Data Works

![Feeding a Model on its Own Outputs](https://upload.wikimedia.org/wikipedia/commons/7/71/Serpiente_alquimica.jpg)

Synthetic data seems hard to grasp intuitively. How can a model trained on its own outputs improve its performance? The key idea is to introduce **side information** to transform the proposal model distribution to a more desirable distribution.

Let's assume we have access to a language model policy $\pi$ that can generate text. We can measure the performance of the model on a particular task, e.g. mathematical reasoning, as $P_{\pi}\left(X\right)$, the probability of predicting the right answer $X$.

The synthetic data question can be posed as follows:

**Can we find an improved policy $\pi^{*}$ by sampling from $P_{\pi}$ and re-training on that data?**

The answer is yes, but only if our synthetic data procedure leads to a desirable distributional shift in our model: i.e. $P_{\pi^{*}}\left(X\right) > P_{\pi}\left(X\right)$.

To achieve this distributional shift, we need to introduce side information $I$ that can allow us to use the proposal distribution $P_{\pi}\left(X\right)$ to sample from a desired distribution $P_{\pi^{*}}\left(X\right)$.

The value of the side information is the mutual information relative to the original policy. 

Write $P_{\pi}(X|I) = P_{\pi^{*}}\left(X\right)$, then:

$$ I(X; I) = \mathbb{E}_{I}\left[D_{KL}\left(P_{\pi}(X\mid{I})\mid\mid{P}{\pi}(X)\right)\right] $$

We can see that if we have no side information then the KL divergence is zero and the value is zero: this explains why some people find synthetic data unintuitive, because they assume there is no side information being introduced. In contrast, if we can use side information to filter the original distribution, then useful synthetic data is possible. 
