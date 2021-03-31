# The Great Decoupling

Deep Learning is undergoing a decoupling where models are trained in two distinct phases. The first phase involves learning general representations through pre-training. The second phase involves learning or exciting task-specific representations through fine-tuning or prompting. Different companies specialize at each stage. Pretraining is capital-intensive and dominated by AI research labs. Fine-tuning is carried out by companies looking to solve domain-specific problems. {% fn 1 %}

{{ "This is the actual footnote" | fndetail: 1 }}

This is not news to anyone involved in machine learning. The big questions are whether transfer learning is here to stay and what the implications of large pretrained models might be. In this post I extrapolate existing trends to get a sense of where we might be headed. In particular, I focus on the idea of “models as platforms” where a model can be reused for many purposes in different domains. 

Models as platforms means the fine-tuning stage is where the bulk of economic value is created. The models themselves are provided by large companies, either released openly or licensed. In the latter case, the agent that provides the pretrained model takes a cut of the downstream value created (the platform fee). Can this approach win out against an open source alternative? I consider that question and other implications of general-purpose models.

As a warmup to this discussion, I cover two analogies to the decoupling we are experiencing. The first is from the history of computing, the decoupling between hardware and software, and the second from neuroscience, the decoupling between memory and co-ordination. 

## General Purpose Computing

<img src="https://rjt1990.github.io/images/differentialanalyzer.jpeg" width=200>

Many groups experimented with early forms of computer in the 1930s. Some examples of early computers included Bush’s [Differential Analyzer](https://en.wikipedia.org/wiki/Differential_analyser), Stibitz and Williams’ [Complex Computer](https://en.wikipedia.org/wiki/George_Stibitz#Computer), the [Atansoff-Berry computer](https://en.wikipedia.org/wiki/Atanasoff%E2%80%93Berry_computer) and Aiken’s [Mark I](https://en.wikipedia.org/wiki/Harvard_Mark_I). These innovations offered marked speedups over slide rules and calculators, but they severely lacked flexibility. A new application required a new machine or a costly reconfiguration. There was no general sense of computing. Hardware and software were coupled.

Until recently, lack of generality was a criticism of deep learning models. A model may be state-of-the-art on a benchmark, but its utility may be limited outside a single task or domain. An early exception was [ImageNet pre-training](https://arxiv.org/abs/1310.1531) where image classification models could be reused for tasks like object detection, semantic segmentation and other tasks. But then [NLP had its ImageNet moment](https://ruder.io/nlp-imagenet/), and now as transformers move to other ML tasks, model generality appears to be becoming more common.

Can we find an analogy for general-purpose models in general-purpose computing? General-purpose computing emerged from a theoretical and a practical source. Theoretically it came from [Turing machines](https://en.wikipedia.org/wiki/Universal_Turing_machine) and practically through [stored-program computers](https://en.wikipedia.org/wiki/Stored-program_computer). The enabling insight was a decoupling between hardware and software.

Turing showed computation is universal under certain conditions: all machines are fundamentally the same. Additionally the actual instructions could be on the tape itself, that is in-memory, rather than encoded elsewhere. This would enable a direct separation between computation and that which is to be computed.

In practice, the solution to flexibility and creating a general-purpose computer came from the concept of a stored-program. Instead of instructions being on a punch card, or even worse in the physical construction of the machine itself, instructions could be stored in memory then fetched, executed and returned. To change the application, you need only change the instructions rather than physical construction of the machine.

The synthesis of theory and practice occurred with the [vNM architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture): Turing machines for computation (hardware) and stored-programs for instructions (software). Computing could then be general-purpose. The same hardware could support many different types of application. And just as one could play Bach (music) on a piano or a pipe-organ (instruments), you could use the same software on different hardware.

By general-purpose model, we similarly mean: a machine learning model that can solve multiple tasks in different domains. But what enables a model to be general-purpose? 

Informally, if we take a trained model, remove its task head (e.g. a fully connected layer), and replace with a new head for a task, and then finetune, the preceding layers should be useful for prediction. For example, fine-tuning an ImageNet classifier on a new image dataset should get us to a higher accuracy more quickly than a fresh, randomly initialized model. 

More formally, a pre-trained model provides side information for prediction. Specifically, for image classification, if we are predicting a class $P\left(X=k\right)$ then the value of the pre-trained weights is the mutual information relative to the class of the image, that is:

$$ I\left(X; \theta^{*}\right) = \mathbb{E}_{\theta^{*}}\left[D_{KL}\left(P\left(X\mid\theta^{*}\right)\mid\mid{P\left(X\mid\theta^{0}\right)}\right)\right] $$

where $\theta^{*}$ is the weights for the pre-trained model, $\theta^{0}$ are randomly initialized weights, and $X$ is the outcome class of the image.

Transfer learning, and information gain, is possible because of knowledge that is implicit in learned features. In the case of an image classifier, we can reuse features like edges abd corners in a new task like object detection or a new domain. In the case of a language model, learning about the structure of language can help with downstream tasks like question answering.

The ML decoupling is therefore between capturing knowledge (memory) and accessing that knowledge to solve a task (co-ordination). In pretraining we want to capture as much information as we can about the world and compress it into a model. In fine-tuning or prompting we want to excite the model into revealing parts of its knowledge that are useful for the task of interest. For example, if we want a good question answering system on legal texts, we need to excite the model to obtain its legal knowledge and configure it for the QA task.

