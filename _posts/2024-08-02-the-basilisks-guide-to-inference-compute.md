# Collected Thoughts: LLM Creativity, MCPE, Self-Reward, Human Latents

I had a great time talking to Nathan Lambert about my recent work. I touched upon several ideas and thought it might be useful to expand on them in more detail here.

## Benchmarking LLM Creativity as Rediscovery

**Problem:**
- How to make LLMs creative? 
- How can LLMs make new discoveries that are not in the training data?

This is hard to benchmark as we have no ground truth for undiscovered things.

So here is an idea. We take a known breakthrough in the past and create a training corpus of data up until that timepoint. The task is then to find an inference-time method that generalises from the training dataset to "rediscover" the breakthrough.

For example, [Einstein famously published four papers in 1905](https://en.wikipedia.org/wiki/Annus_mirabilis_papers) explaining the photoelectric effect, Brownian motion, special relativity and mass-energy equivariance. 

We could imagine collecting a training corpus up until 1905, and then trying to rediscover these breakthroughs. If we succeeded, we would have evidence that LLMs can be as creative as the most creative human. We could then try to use the same method for the present day and use it for brand new discoveries.

(* The downside to this instantiation is that most useful tokens were published online after 1905! But we could imagine doing a similar experiment with more recent breakthroughs)

## Monte Carlo Policy Evaluation (MCPE)

**Problem:**
- How to get dense feedback on LLM trajectories?

Nathan asked me about the benefits of PRM. I see this through the lens of an older idea which is [MCPE](http://incompleteideas.net/book/first/ebook/node51.html). Using Monte Carlo rollouts, and a reward function, we can learn to assign dense values at each point in a trajectory - instead of using human annotations.

MCTS is a particular instantiation of this idea. It's still underappreciated how the main motivation behind the idea was to learn a value function - given how hard it was to build human-crafted evaluation functions for Go. But it's easy to evaluate if someone has won the game (the reward function). Combined a search tree, we then have a basis for obtaining dense feedback.

Variants of this idea were published recently, see [SORM](https://arxiv.org/abs/2402.10963) and [MATH-shepherd](https://arxiv.org/abs/2312.08935).

The problem for AGI is then is to find a sufficiently general reward function.

## Self-Reward

It would be great if language models could verify their own solutions, as this would solve the generality problem mentioned above.

I see many people claiming that “LLMs can’t verify” their solutions on Twitter. The word they are missing is “yet”, and in fact, in many cases self-reward works for the current generation of models.

If you don’t believe me, an easy way to see things is as follows.

Take a LLaMA-1 model and sample GSM8k train trajectories to train an ORM. The llama-1 model will be our policy. Then train an ORM on these trajectories with different base models: llama-1, llama-2, llama-3. Then evaluate by sampling from the policy and reranking with the three ORM models at various levels of pass@k.

If you plot the pass@k on a single graph, you’ll see the same policy doing much better with reward models trained on recent base models.

Now notice: each reward model is trained with the same set of trajectories (!). This means the additional knowledge about how to judge the answer is coming from knowledge gained during pre-training.

This is very clear evidence that LLMs have latent knowledge on how to judge solutions, and more importantly, that this ability scales with the underlying strength of the model.

## Human Latents

I cryptically touched upon what I have been thinking about in the 3 months since leaving Meta.

LLMs right now are trained on human outputs. We do not directly observe the thought process (internal context) required to produce them. This is why we have methods like scratchpads, chain of thought, quiet reasoning tokens to try to artificially produce the thought process that creates good output.

I still think this whole area is very underexplored, and has much broader applications than reasoning. For example, many human decisions are based in accordance with an internal value system, emotions, empathy - which we do not observe directly in text. Having a better grasp on them will be crucial for alignment.

More specifically, my bet is that future AI systems will have constraints on capability to be more “human-like”. A recent OpenAI paper couched this in terms of an interpretability/capability tradeoff, where we would be happy to trade performance for outputs to be interpretable by humans.

Interpretability is one axis of human-like intelligence - but clearly there is more that we would like to capture to be more confident with living in a world with superintelligent AIs. Feeling the AGI means teaching AGI to feel.

Hoping to share more on what I’ve been building later in the year!

