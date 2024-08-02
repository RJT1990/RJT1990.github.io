# Collected Thoughts: LLM Creativity, MCPE, Self-Reward, Human Latents

I had a great time talking to Nathan Lambert about my recent work. I touched upon several ideas and thought it might be useful to expand on them in more detail here.

## Benchmarking LLM Creativity as Rediscovery

**Problem:**
- How can LLMs make new discoveries that are not in the training data?

This is hard to benchmark as we have no ground truth for undiscovered things.

So here is a fun idea. We take a known breakthrough in the past and create a training corpus of data up until that timepoint. The task is then to find an inference-time method that generalises from the training dataset to "rediscover" the breakthrough.

For example, [Einstein famously published four papers in 1905](https://en.wikipedia.org/wiki/Annus_mirabilis_papers) explaining the photoelectric effect, Brownian motion, special relativity and mass-energy equivariance. 

We could imaging pre-training a model on a training corpus up until 1905, and then trying to rediscover these breakthroughs through inference compute. If we succeeded, we would have evidence that LLMs can be as creative as the most creative human. We could then use the same method for the present day and make new discoveries.

(* The downside to this instantiation is that most useful tokens were published after 1905! But we could imagine a similar setup with more recent breakthroughs)

## Monte Carlo Policy Evaluation (MCPE)

**Problem:**
- How to get dense feedback on LLM trajectories?

Nathan asked me about the benefits of [PRM](https://arxiv.org/pdf/2211.14275). I see this through the lens of an older idea which is [MCPE](http://incompleteideas.net/book/first/ebook/node51.html). Using Monte Carlo rollouts, and a reward function, we can learn to assign dense feedback at each point in a trajectory, instead of using human annotations.

MCTS is a particular instantiation of this idea. It's underappreciated how the original motivation behind MCTS was to learn a value function - given how hard it was to build hand-crafted evaluation functions for Go. But in games like Go, it is easy to evaluate if someone has won the game (the reward function). So combining Monte Carlo rollouts with a search tree and a reward function gives us the basis for obtaining dense feedback.

Variants of this idea were published recently, see [SORM](https://arxiv.org/abs/2402.10963) and [MATH-shepherd](https://arxiv.org/abs/2312.08935).

The problem for AGI is then is to find a sufficiently general reward function - since language is harder to evaluate than a game with clearly defined rules.

## Self-Reward

**Problem:**
- How to make a general reward function?

It would be great if LLMs could verify their own solutions, as this would help us make progress towards a general reward function.

Many people on Twitter state definitively that “LLMs can’t verify”. The word they are missing is “yet”. In fact, self-reward is one of the ideas that has strong potential for results as we continue to scale.

To see this, you can do a simple example.

Take a LLaMA-1 70B model and sample GSM8k train trajectories to train an ORM. The LLaMA-1 70B model will be our policy. Then train an [orm](https://arxiv.org/pdf/2211.14275) on these trajectories with different base models: LLaMA-1, LLaMA-2, LLaMA-3. Then evaluate by sampling from the policy and re-ranking with the three ORM models at various levels of pass@k.

If you plot the pass@k on a single graph, you’ll see the same policy doing much better with reward models trained on more recent base models.

This might seem obvious, but it has an interesting implication for self-reward. Note that each reward model is trained with the same set of trajectories from the policy. This means the additional knowledge about how to judge the answer is coming from knowledge gained during pre-training -> and models trained with more compute are better judges.

## Human Latents

**Problem:**
- How to make AI more aligned with human intelligence?

I cryptically touched upon what I have been thinking about in the 3 months since leaving Meta.

Language models are trained on human outputs. We do not directly observe the thought process required to produce them. This is why we have methods like scratchpads, chain of thought, quiet reasoning tokens to artificially produce the thought process that creates good output.

But this whole area is underexplored and has broader applications than just reasoning. For example, many human decisions are based on an internal value system, emotions, empathy - which we do not observe directly in text. We may learn a low-dimensional representation of these latents, but it seems that having a better grasp on them will be important for alignment.

More specifically, my bet is that future AI systems will have constraints on capability to be more “human-like”. A [recent OpenAI paper](https://openai.com/index/prover-verifier-games-improve-legibility/) framed this in terms of an interpretability/capability tradeoff, where we would be happy to trade performance for outputs to be interpretable by humans. Interpretability is one axis of human-like intelligence - but clearly there is more that we would like to capture to be more confident with living in a world with superintelligent AIs. Feeling the AGI means teaching AGI to feel...

Hoping to share more later in the year!

