# Deep Learning: The Great Decoupling

Deep Learning is undergoing a decoupling with the expansion of the 'pretrain and finetune' paradigm. The first phase involves learning general representations through pre-training. The second phase involves learning or exciting task-specific representations through fine-tuning or prompting. Different companies specialize at each stage. Pretraining is capital-intensive and dominated by AI research labs. Fine-tuning accelerates training and is increasingly carried out by companies looking to solve domain-specific problems.

This is not news to anyone involved in machine learning. The big questions are whether transfer learning is here to stay and what the implications of large pretrained models might be. In this post I extrapolate existing trends to get a sense of where we might be headed. In particular, I focus on the idea of “models as platforms” where a model can be reused for many purposes in different domains. 

Models as platforms means the fine-tuning stage is where the bulk of economic value is created. The models themselves are provided by large companies, either released openly or licensed. In the latter case, the agent that provides the pretrained model takes a cut of the downstream value created (the platform fee). Can this approach win out against an open source alternative? I consider that question and other implications of general-purpose models.

As a warmup to this discussion, I cover two analogies to the decoupling we are experiencing. The first is from the history of computing, the decoupling between hardware and software, and the second from neuroscience, the decoupling between memory and co-ordination. 

## General Purpose Computing

<img src="https://rjt1990.github.io/images/differentialanalyzer.jpeg" width=200>

Many groups experimented with early forms of computer in the 1930s. Some examples of early computers included Bush’s [Differential Analyzer](https://en.wikipedia.org/wiki/Differential_analyser), Stibitz and Williams’ [Complex Computer](https://en.wikipedia.org/wiki/George_Stibitz#Computer), the [Atansoff-Berry computer](https://en.wikipedia.org/wiki/Atanasoff%E2%80%93Berry_computer) and Aiken’s [Mark I](https://en.wikipedia.org/wiki/Harvard_Mark_I). These innovations offered marked speedups over slide rules and calculators, but they severely lacked flexibility. A new application required a new machine or a costly reconfiguration. There was no general sense of computing. Hardware and software were coupled.

Until recently, lack of generality was a criticism of deep learning models. A model may be state-of-the-art on a benchmark, but its utility may be limited outside a single task or domain. The big exception was [ImageNet pre-training](https://arxiv.org/abs/1310.1531)[^1] where pre-trained image classification models enabled deep learning to work in tasks such as object detection. But then [NLP had its ImageNet moment](https://ruder.io/nlp-imagenet/)[^2], and now as [transformers move to other ML tasks](https://paperswithcode.com/newsletter/3/), model generality and transfer learning is becoming more common.

[^1]: [DeCAF: A Deep Convolutional Activation Feature for Generic Visual Recognition - Donahue et al](https://arxiv.org/abs/1310.1531)
[^2]: [NLP's ImageNet moment has arrived - Sebastian Ruder](https://ruder.io/nlp-imagenet/)

Can we find an analogy for general-purpose models in general-purpose computing? General-purpose computing emerged from a theoretical and a practical source. Theoretically it came from [Turing machines](https://en.wikipedia.org/wiki/Universal_Turing_machine) and practically through [stored-program computers](https://en.wikipedia.org/wiki/Stored-program_computer). The enabling insight was a decoupling between hardware and software.

Turing showed computation is universal under certain conditions: all machines are fundamentally the same. Additionally the actual instructions could be on the tape itself, that is in-memory, rather than encoded elsewhere. This would enable a direct separation between computation and that which is to be computed.

In practice, the solution to flexibility and creating a general-purpose computer came from the concept of a stored-program. Instead of instructions being on a punch card, or even worse in the physical construction of the machine itself, instructions could be stored in memory then fetched, executed and returned. To change the application, you need only change the instructions rather than physical construction of the machine.

The synthesis of theory and practice occurred with the [vNM architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture): Turing machines for computation (hardware) and stored-programs for instructions (software). Computing could then be general-purpose. The same hardware could support many different types of application. And just as one could play Bach (music) on a piano or a pipe-organ (instruments), you could use the same software on different hardware.

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

$$ \int_{T}\int_{D} $D_{KL}\left(p\left(y; \theta^{0}, t, d\right) \mid\mid  p\left(y; \theta^{P}, t, d\right)\right) \delta{t}\delta{d} $$

The ML decoupling is therefore between capturing knowledge (memory) and accessing that knowledge to solve a task (co-ordination). In pretraining we want to capture as much information as we can about the world and compress it into a model. In fine-tuning or prompting we want to excite the model into revealing parts of its knowledge that are useful for the task of interest. For example, if we want a good question answering system on legal texts, we need to excite the model to obtain its legal knowledge and configure it for the QA task.

