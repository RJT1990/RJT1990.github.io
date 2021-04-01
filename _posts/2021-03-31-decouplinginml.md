# Deep Learning: The Great Decoupling

Deep Learning is undergoing a decoupling with the growth of the 'pretrain and finetune' paradigm. The first phase involves learning general representations through pre-training. The second phase involves learning or exciting task-specific representations through fine-tuning or prompting. Model and dataset scale appears to benefit pre-training, and this has led to very large models. Given budgets and incentives, different companies are effectively specializing at each stage. Pretraining is capital-intensive and dominated by AI research labs. Fine-tuning accelerates training and is increasingly carried out by companies looking to solve domain-specific problems.

This decoupling is not news to anyone involved in machine learning. However, the implications of transfer learning as a new workflow standard have not been discussed in detail. In this essay I extrapolate a few of these trends to see where we might be headed. In particular, I focus on the idea of “models as platforms” where a model can be reused for many purposes in different domains. 

Models as platforms has theoretial and practical implications. Theoretically, it raises the question whether we should aim for a goal of building *universal representations* that have maximum generality to new tasks and domains. This is a potential pathway to solving tasks within machine learning, as we can reuse general-purpose representations rather than training afresh. In practice, models as platforms means the fine-tuning stage is where the bulk of economic value is created. The models themselves are provided by large companies, either released openly or licensed. In the latter case, the agent that provides the pretrained model takes a cut of the downstream value created (the platform fee). Are we heading for a world where large companies build the general-purpose models and license them out? Or will an open source alternative win out?  

As a warmup to this discussion, I cover two analogies to the decoupling we are experiencing. The first is from the history of computing, the decoupling between hardware and software, and the second from neuroscience, the separation between memory and executive control. This should provide context as to why general-purpose models might be useful, and additionally, why the current 'pretrain and finetune' paradigm might survive or fail.

## General Purpose Computers

<br />

<p><img src="https://rjt1990.github.io/images/differentialanalyzer.jpeg" width=250></p>
<p align="center"><i>Vannevar Bush with the Differential Analyzer</i></p>

<br />

Computing was not always general-purpose. In fact, the early proto-computers in the 1930s were application-specific. Some examples include Bush’s [Differential Analyzer](https://en.wikipedia.org/wiki/Differential_analyser), Stibitz and Williams’ [Complex Computer](https://en.wikipedia.org/wiki/George_Stibitz#Computer), the [Atansoff-Berry computer](https://en.wikipedia.org/wiki/Atanasoff%E2%80%93Berry_computer) and Aiken’s [Mark I](https://en.wikipedia.org/wiki/Harvard_Mark_I). These innovations offered marked speedups over slide rules and calculators, but they severely lacked flexibility. A new application required a new machine or a costly reconfiguration. Hardware and software were coupled and there was no "general" sense of computing.

General-purpose computing emerged from a theoretical and a practical source: [Turing machines](https://en.wikipedia.org/wiki/Universal_Turing_machine) and [stored-program computers](https://en.wikipedia.org/wiki/Stored-program_computer). Turing showed computation is universal under certain conditions: all machines are fundamentally the same. Additionally the actual instructions could be on the tape itself, that is in-memory, rather than encoded elsewhere. This implied a separation between computation and that which is to be computed. While in practice, stored-program computers stored instructions in memory that could be fetched, executed and returned. To change the application, you need only change the instructions rather than physical construction of the machine or a punch card.

In both theory and practice, the key insight was a decoupling of hardware and software. The synthesis of these ideas was the [vNM architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture): Turing machines for computation (hardware) and stored-programs for instructions (software). This enabled general purpose computing, as the same hardware could support many different types of application, while software could be used on different hardware.

The advantages of general-purpose computing over application-specific computers were:

- **Accelerating innovation and reducing costs** : producers could focus on innovation for computing as a whole for a given architecture - rather than building fundamentally different hardware for each application. Standardization through the vNM architecture enabled economies of scale, plus more shared industry learnings ([Wright's Law](https://en.wikipedia.org/wiki/Experience_curve_effects)). Later on, progress could then be measured through [Moore's Law](https://en.wikipedia.org/wiki/Moore's_law).
- **Enabling specialization by decoupling software and hardware** : some producers could focus on making really good software, and others on hardware - rather than having to solve both types of problem simultaneously.
- **Reducing friction for developing new applications** : rather than building an entirely new computer for a new problem, existing computers could be repurposed for new problems through new software. Less reinventing the wheel.

As we'll see, many of the same arguments apply for the new decoupling between pretraining and finetuning large models.

## Memory and Control

<br />

<p><img src="https://rjt1990.github.io/images/fruitloop.png" width=400></p>
<p align="center"><i>Rats love Froot Loops. Image from <a href="https://www.reddit.com/r/RATS/comments/8nv1kn/eating_fruit_loops_make_freya_a_happy_rattie/">Reddit</a></i></p>

<br />

When animals solve tasks, they are presented with a context and must use that context to retrieve relevant memories that help solve the task (and yield a reward). The two key lobes of the brain that appear to be relevant for this are the frontal and medial lobes. More specifically, the [prefrontal cortex](https://en.wikipedia.org/wiki/Prefrontal_cortex) (PFC) seems to be particularly important for executive control (planning, decision making, working memory), while the [hippocampus](https://en.wikipedia.org/wiki/Hippocampus) seems to be particularly important for long-term memory.

The [rat foraging example of Eichenbaum](https://www.nature.com/articles/nn.4327)[^4] provides a nice illustration of a bidirectional relationship between the PFC and the hippocampus.

[^4]: [Bidirectional prefrontal-hippocampal interactions support context-guided memory - Eichenbaum et al](https://www.nature.com/articles/nn.4327)

Rats are given a task of finding Froot Loops in flowerpots. They have to learn in room A, cereal is hidden in a pot filled with purple plastic beads and smells sweet; and in room B, cereal is hidden in a pot with black paper shreds that smells spicy. The experimenters measured the neural activity of the prefrontal cortex and the hippocampus. Each region of the brain reacts as follows in the course of the task:

- The prefrontal cortex fires in relation to cues that signal rewards - e.g. a pot that signals it may have Froot Loops.
- The ventral hippocampus fires when the rat recognises the room it is in.
- The dorsal hippocampus fires when the rat recognises a flowerpot it has seen before.

Crucially, the sequence of firing hints at a handshake behaviour between the hippocampus and the prefrontal cortex:

- When the rat enters room A, the ventral hippocampus transmits to the prefrontal cortex and sets the context to room A.
- This context then guides retrieval from the dorsal hippocampus, which recognizes the flowerpots and sends this information back to the cortex.
- The cortex then combines the flowerpot information with the context, and infers the pot has purple beads and smells sweet.

The key takeaway is that that prefrontal cortex seems to help filter out irrelevant memories for the task at hand.

When we are finetuning or prompting a large model, we are essentially trying to retrieve goal-relevant knowledge for the task and dataset at hand. Indeed, this was the point of the observation that GPT-2 was a [unsupervised multi-task learner](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)[^5], because in a general system, we are conditioning on $p\left(output\mid{input}, task\right)$. Similarly, we can see that the PFC is essentially "conditioning" the hippocampus to retrieve the right memories for the given task in the rat foraging example.

[^5]: [Language Models are Unsupervised Multitask Learners - Radford et al](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)

Seen through this lens, the deep learning decoupling is similarly a division between memory and executive control. With finetuning or prompting, we have a task in mind, e.g. finetuning BERT for question answering on legal texts, and our goal is to retrieve relevant knowledge from the model for this task. The usefulness of the underlying language model is whether we have stored relevant task (question answering), domain (legal text) or general (language understanding) information that's useful for the downstream task. But in addition, it is whether we can conveniently access this goal-relevant knowledge through a procedure like fine-tuning (accessibility), and whether the knowledge generalizes for solving problems (generalisibility). 

## The Tyranny of Memory

A natural pathway from the idea that downstream task performance depends on memorizing the right tasks and domains, is to ensure very large models that have as much as knowledge as possible. This is the 'model scaling' direction of language model research. But more knowledge is not always useful. It is possible to memorize lots of details but be incapable of generalizing to a new situation: this is what we mean by overfitting the data. That is why compression is useful because it allows us to generalize from our experience to situations we have never experienced before.

<br />

<img src="https://rjt1990.github.io/images/scalinglaws.png">
*Model Scaling for GPT-3*[^6]

[^6]: [Language Models are Few-Shot Learners - Brown et al](https://arxiv.org/abs/2005.14165)

<br />

Empirically, we have not yet hit diminishing returns from model scaling yet.

## General Purpose Models

Until recently, lack of generality was a criticism of deep learning models. A model may be state-of-the-art on a benchmark, but its utility may be limited outside a single task or domain. The big exception was [ImageNet pre-training](https://arxiv.org/abs/1310.1531)[^1] where pre-trained image classification models enabled deep learning to work in tasks such as object detection. But then [NLP had its ImageNet moment](https://ruder.io/nlp-imagenet/)[^2], and now as [transformers move to other ML tasks](https://paperswithcode.com/newsletter/3/), model generality and transfer learning is becoming more common.

[^1]: [DeCAF: A Deep Convolutional Activation Feature for Generic Visual Recognition - Donahue et al](https://arxiv.org/abs/1310.1531)
[^2]: [NLP's ImageNet moment has arrived - Sebastian Ruder](https://ruder.io/nlp-imagenet/)

Can we find an analogy for general-purpose models in general-purpose computing? 

By general-purpose model, we similarly mean: a machine learning model that can be used to solve multiple tasks in different domains. But what enables a model to be general-purpose? 

Informally, if we take a pretrained model, replace its head (randomly initialized) and then finetune, then the preceding layers should be useful for prediction. For example, fine-tuning an ImageNet classifier on a new image dataset can potentially get us to a higher accuracy than a fresh, randomly initialized model. The value-add comes from quicker training (over random initialization) but also useful information in the weights that we couldn't obtain from training on the new dataset alone. 

Formally, a pre-trained model provides side information for prediction. Let's say we train two competing models, one that initializes with random weights $\theta^{0}$ and the other with pre-trained weights $\theta^{P}$. We ignore details of how they are trained (how many epochs, etc) - assume both have appropriate hyperparameters. After training, we obtain likelihoods $p\left(y; \theta^{0}\right)$ and $p\left(y; \theta^{P}\right)$. From this we can measure information gain from using the pre-trained model as $D_{KL}\left(p\left(y; \theta^{0}\right) \mid\mid  p\left(y; \theta^{P}\right)\right)$. In the worst case, e.g. the source dataset does not transfer well to the target dataset, the information gain is small. Where information transfers, we have information gain.

Information gain through transfer learning is possible because of feature reusability. In the case of an image classifier, we can reuse [features like edges and textures](https://distill.pub/2017/feature-visualization/) in a new task like object detection or a new dataset - i.e. where those features are still valuable. In the case of a language model, learning about the structure of language can help with downstream tasks like question answering.

<br />

<img src="https://rjt1990.github.io/images/visualization.png">
*Visualizing features in GoogLeNet from distill.pub*[^3]

<br />

[^3]: [Feature Visualization - distill.pub](https://distill.pub/2017/feature-visualization/)

Seen through the lens of information gain, a model's generality increases with its ability to have information gain across new tasks and datasets. In other words, integrating over all possible tasks and datasets, we have a measure of how general-purpose a model is:

$$ \int_{T}\int_{D} D_{KL}\left(p\left(y; \theta^{0}, t, d\right) \mid\mid  p\left(y; \theta^{P}, t, d\right)\right) \delta{t}\delta{d} $$

The ML decoupling is therefore between capturing knowledge (memory) and accessing that knowledge to solve a task (co-ordination). In pretraining we want to capture as much information as we can about the world and compress it into a model. In fine-tuning or prompting we want to excite the model into revealing parts of its knowledge that are useful for the task of interest. For example, if we want a good question answering system on legal texts, we need to excite the model to obtain its legal knowledge and configure it for the QA task.

